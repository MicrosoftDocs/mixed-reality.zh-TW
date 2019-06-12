---
title: 新增全像攝影版的遠端處理
description: 說明如何使用全像攝影版的遠端處理，透過網路呈現 HoloLens 全像投影。
author: MikeRiches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality，全像投影、 全像攝影版的遠端執行功能、 遠端轉譯、 轉譯、 HoloLens、 遠端全像投影的網路
ms.openlocfilehash: 8d645f634ff0fc820893f5554fd602aa3a2f38e3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829617"
---
# <a name="add-holographic-remoting"></a>新增全像攝影版的遠端處理

## <a name="hololens-2"></a>HoloLens 2

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。

使用全像攝影版的遠端處理的 HoloLens 開發人員必須更新他們的應用程式，使其與 HoloLens 2 相容。  這將需要全像攝影版的遠端處理 NuGet 封裝尚未公開可用的新版本。  如果連接到全像攝影版 HoloLens 2 上的遠端播放程式嘗試使用 HoloLens NuGet 套件的應用程式，連接將會失敗。  HoloLens 2 NuGet 套件可供使用之後，請觀看此頁面的更新。

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>將全像攝影版的遠端執行功能新增至您的桌面或 UWP 應用程式

此頁面說明如何新增全像攝影版的遠端桌面或 UWP 應用程式。

全像攝影版的遠端處理可讓您的應用程式以裝載桌上型 PC 或 Xbox One，允許更多系統資源的存取，並讓您可以整合遠端例如 UWP 裝置上的全像攝影版內容設為目標的 HoloLens[沈浸式檢視](app-views.md)至現有的桌面電腦軟體。 遠端主機應用程式收到 HoloLens 的輸入的資料流、 呈現內容，在虛擬的沈浸式檢視中，及資料流的內容框架返回 HoloLens。 連線是使用標準的 Wi-fi。 若要使用遠端執行功能，您會將全像攝影版的遠端執行功能新增至您的桌面或 UWP 應用程式，使用 NuGet 套件，並撰寫程式碼來處理連接，並在沉浸式檢視中轉譯。 協助程式庫會包含在程式碼範例，可簡化處理裝置連線的工作。

必須為 50 毫秒的延遲低的典型的遠端連線。 播放器應用程式可以報告在即時的延遲。

>[!NOTE]
>目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。  概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。

### <a name="get-the-remoting-nuget-packages"></a>取得遠端處理 NuGet 套件

請遵循下列步驟，針對全像攝影版的遠端執行功能，讓 NuGet 套件，並從您的專案中加入的參考：
1. 請移至您在 Visual Studio 中的專案。
2. 以滑鼠右鍵按一下專案節點，然後選取**管理 NuGet 套件...**
3. 在出現的窗格中，按一下**瀏覽**，然後搜尋 「 全像攝影版的遠端執行功能 >。
4. 選取  **Microsoft.Holographic.Remoting**然後按一下**安裝**。
5. 如果**Preview**  對話方塊出現時，按一下**確定**。
6. 下一個出現的對話方塊是 「 授權合約 」。 按一下 **我接受**接受授權合約。

### <a name="create-the-holographicstreamerhelpers"></a>建立 HolographicStreamerHelpers

首先，我們需要 HolographicStreamerHelpers 的執行個體。 加入這將會處理遠端服務的類別。

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

您也必須追蹤連線狀態。 如果您想要呈現的預覽，您需要有要將它複製到的材質。 您也需要一些像是連線狀態鎖定，而儲存 HoloLens，IP 位址的某種方式等等。

```
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>初始化 HolographicStreamerHelpers 並連接到 HoloLens

若要連接到 HoloLens 裝置，建立 HolographicStreamerHelpers 的執行個體並連線至目標 IP 位址。 您必須設定視訊畫面格大小以符合 HoloLens 顯示寬度和高度，因為全像攝影版的遠端處理程式庫預期編碼器和解碼器完全相符的解決方法。

```
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

裝置連線是非同步的。 您的應用程式必須提供事件處理常式的連接，中斷連線，及框架傳送事件。

OnConnected 事件可以更新 UI，開始轉譯，等等。 在桌面程式碼範例中，我們會更新視窗標題的 「 連線 」 的訊息。

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected 事件可以處理重新連線、 UI 更新等等。 在此範例中，我們重新連接發生暫時性失敗時。

```
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

Remoting 元件準備好要傳送在範圍內時，您的應用程式提供一份在 SendFrameEvent 的機會。 在這裡，我們將複製的框架到交換鏈結，讓我們可以將它顯示在預覽視窗中。

```
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>呈現全像攝影版的內容

要呈現的內容使用遠端執行功能，您設定您的桌面或 UWP 應用程式中的虛擬 IFrameworkView 並處理全像攝影版的畫面格，從遠端處理。 所有的 Windows 全像攝影版 api 都是的使用相同的方式，此檢視中，但是它的設定方式稍有不同。

而不用建立他們自己的全像攝影版的空間和語音元件來自 HolographicRemotingHelpers 類別：

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

而不是使用執行方法內更新迴圈，您可以提供從桌面或 UWP 應用程式的主迴圈的刻度更新。 這可讓您的桌面或保留在訊息處理的控制項中的 UWP 應用程式。

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

全像攝影版的應用程式檢視的 Tick() 方法完成一次更新、 繪製時，出現迴圈的反覆運算。

```
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

全像攝影版的應用程式檢視更新、 轉譯，並出現迴圈是完全相同，即 HoloLens-上執行時不同之處在於您在桌面的電腦上有更大的系統資源的存取。 您可以呈現多更多的三角形，有多個繪圖的階段，詳細物理條件，並使用 x64 處理序載入需要的內容超過 2 GB 的 RAM。

### <a name="disconnect-and-end-the-remote-session"></a>中斷連線，然後結束遠端工作階段

若要中斷連線-例如，當使用者按一下 中斷連接-U 按鈕呼叫 Disconnect() 上 HolographicStreamerHelpers，並再釋放物件。

```
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>取得遠端處理播放程式

Windows 全像攝影版的遠端播放程式會為端點連線至遠端主機應用程式，提供 Windows 應用程式存放區中。 若要取得 Windows 全像攝影版的遠端播放程式，請從您的 HoloLens 搜尋針對遠端執行功能，瀏覽 Windows app store 並下載應用程式。 遠端處理播放程式會包含偵錯遠端裝載應用程式時很有用的功能，畫面上，顯示統計資料。

## <a name="notes-and-resources"></a>資訊與資源

全像攝影版的應用程式檢視必須有辦法提供您的應用程式與 Direct3D 裝置，必須用來初始化全像攝影版的空間。 您的應用程式應該使用 Direct3D 裝置複製，並顯示在預覽畫面格。

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**程式碼範例：** 完整的全像攝影版的遠端程式碼範例已使用，其中包含適用於遠端處理與遠端桌面的 Win32、 UWP DirectX 和 XAML 使用 UWP 的主應用程式專案的全像攝影版的應用程式檢視。 若要取得它，請前往：
* [針對遠端執行功能的 Windows 全像攝影版的程式碼範例](https://github.com/Microsoft/HoloLensCompanionKit/)

**偵錯的附註：** 全像攝影版的遠端處理程式庫可能會擲回第一個可能發生例外狀況。 這些例外狀況可能會出現在偵錯工作階段，根據當時是作用中的 Visual Studio 的例外狀況設定。 這些例外狀況會在內部攔截到全像攝影版的遠端處理程式庫，您可以忽略。
