---
title: 新增全像攝影遠端
description: 說明如何使用全像攝影遠端，透過網路將全息影像轉譯成 HoloLens。
author: mikeriches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality，全息影像，全像攝影遠端，遠端呈現，網路轉譯，HoloLens，遠端全息
ms.openlocfilehash: 2f6ade5552c993f66281d0be8a7e62c8f076deac
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277706"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a>新增全像攝影遠端（HoloLens （第1代））

>[!IMPORTANT]
>本檔說明如何建立 HoloLens 1 的主應用程式。 **HoloLens （第1代）** 的主機應用程式必須使用 NuGet **1.x.x**套件1.x 版。 這表示針對 HoloLens 1 所撰寫的主機應用程式與 HoloLens 2 不相容，反之亦然。

## <a name="hololens-2"></a>HoloLens 2

使用全像攝影遠端的 HoloLens 開發人員必須更新其應用程式，使其與 HoloLens 2 相容。 這需要新版本的全像攝影遠端 NuGet 套件。 如果應用程式使用的全像是在版本號碼小於2.0.0.0 的「全像攝影」 NuGet 套件嘗試連接到 HoloLens 2 上的全像「遠端播放」，連線將會失敗。

>[!NOTE]
>您可以在[這裡](holographic-remoting-create-host.md)找到 HoloLens 2 的特定指引。


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>在您的桌上型電腦或 UWP 應用程式中新增全像的遠端功能

此頁面說明如何在桌上型電腦或 UWP 應用程式中新增全像攝影遠端功能。

全像攝影遠端可讓您的應用程式以桌上型電腦或 UWP 裝置（例如 Xbox One）上裝載的全像攝影內容為 HoloLens，讓您可以存取更多的系統資源，並讓您能夠將遠端[沉浸式流覽](app-views.md)整合到現有的桌上型電腦軟體。 遠端主機應用程式會從 HoloLens 接收輸入資料流程、在虛擬沉浸式視圖中轉譯內容，以及將內容框架串流回 HoloLens。 連接是使用標準 Wi-fi 建立的。 若要使用遠端處理，您將使用 NuGet 套件將全像的遠端處理新增至桌面或 UWP 應用程式，並撰寫程式碼來處理連接並在沉浸式視圖中轉譯。 Helper 程式庫包含在程式碼範例中，可簡化處理裝置連線的工作。

一般遠端連線的延遲時間會降到50毫秒。 Player 應用程式可以即時報告延遲。

>[!NOTE]
>本文中的程式碼片段目前示範如何使用C++/cx， C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT，如全像攝影專案範本中所使用。  概念相當於C++/WinRT 專案，但您必須轉譯程式碼。

### <a name="get-the-remoting-nuget-packages"></a>取得遠端 NuGet 套件

請遵循下列步驟來取得適用于全像攝影遠端的 NuGet 套件，並從您的專案新增參考：
1. 前往 Visual Studio 中的專案。
2. 以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 套件 ...** ]
3. 在出現的面板中，按一下 **[流覽]** ，然後搜尋「全像遠端處理」。
4. 選取 [ **Microsoft 全息**]，然後按一下 [**安裝**]。
5. 如果出現 [**預覽**] 對話方塊，請按一下 **[確定]** 。
6. 下一個出現的對話方塊是授權合約。 按一下 [**我接受**] 以接受授權合約。

### <a name="create-the-holographicstreamerhelpers"></a>建立 HolographicStreamerHelpers

首先，我們需要 HolographicStreamerHelpers 的實例。 將此加入至將會處理遠端的類別。

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

您也必須追蹤連接狀態。 如果您想要轉譯預覽，則需要有材質，才能將它複製到其中。 您也需要一些東西，像是線上狀態鎖定，還有一些儲存 HoloLens IP 位址的方法，依此類推。

```cpp
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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>將 HolographicStreamerHelpers 初始化並聯機至 HoloLens

若要連線至 HoloLens 裝置，請建立 HolographicStreamerHelpers 的實例，並連接到目標 IP 位址。 您必須設定影片畫面大小，使其符合 HoloLens 的顯示寬度和高度，因為全像攝影遠端程式庫會預期編碼器和解碼器解析度完全相符。

```cpp
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

裝置連接是非同步。 您的應用程式必須提供連接、中斷連線和框架傳送事件的事件處理常式。

OnConnected 事件可以更新 UI、開始呈現等等。 在我們的桌面程式碼範例中，我們會使用「已連線」訊息來更新視窗標題。

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected 事件可以處理重新連接、UI 更新等等。 在此範例中，如果發生暫時性失敗，我們會重新連線。

```cpp
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

當遠端處理元件準備好要傳送框架時，您的應用程式會有機會在 SendFrameEvent 中建立複本。 在這裡，我們會將畫面複製到交換鏈，讓我們可以將它顯示在預覽視窗中。

```cpp
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

### <a name="render-holographic-content"></a>呈現全像攝影內容

若要使用遠端處理來轉譯內容，您可以在桌面或 UWP 應用程式內設定虛擬 IFrameworkView，並處理來自遠端的全息框架。 所有的 Windows 全像攝影應用程式開發介面都是以相同的方式來使用，但其設定方式稍有不同。

「全像攝影空間」和「語音」元件不會自行建立，而是來自您的 HolographicRemotingHelpers 類別：

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

您不需要在 Run 方法內使用 update 迴圈，而是從桌面或 UWP 應用程式的主要迴圈提供滴答更新。 這可讓您的桌面或 UWP 應用程式繼續控制訊息處理。

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

全像攝影應用程式視圖的 Tick （）方法會完成更新、繪製、呈現迴圈的一個反復專案。

```cpp
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

全像攝影應用程式視圖的更新、轉譯和呈現迴圈，與在 HoloLens 上執行時完全相同，不同之處在于您可以存取桌上型電腦上的系統資源數量更大。 您可以轉譯多個三角形、擁有更多的繪製行程、執行更多物理，以及使用 x64 進程來載入需要超過 2 GB RAM 的內容。

### <a name="disconnect-and-end-the-remote-session"></a>中斷連線並結束遠端會話

中斷連線-例如，當使用者按一下 UI 按鈕以中斷連接 HolographicStreamerHelpers 上的呼叫中斷連接（），然後放開物件。

```cpp
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

## <a name="get-the-remoting-player"></a>取得遠端播放機

Windows app store 中提供的 Windows 全像遠端處理播放程式，是遠端主機應用程式連接的端點。 若要取得 Windows 全像遠端播放程式，請從 HoloLens 流覽 Windows app store、搜尋遠端處理，然後下載應用程式。 「遠端播放程式」包含在螢幕上顯示統計資料的功能，在對遠端處理主機應用程式進行調試時，這會很有用。

## <a name="notes-and-resources"></a>記事和資源

全像攝影應用程式視圖需要一種方式，讓您的應用程式能夠使用 Direct3D 裝置，這必須用來初始化全像攝影空間。 您的應用程式應該使用此 Direct3D 裝置來複製和顯示預覽畫面。

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

程式**代碼範例：** 提供完整的全像攝影版遠端處理常式代碼範例，其中包含與使用 XAML 的桌面 Win32、UWP DirectX 和 UWP 的遠端處理和遠端處理主項目目相容的全像攝影應用程式視圖。 若要取得它，請移至這裡：
* [遠端處理的 Windows 全像程式碼範例](https://github.com/Microsoft/HoloLensCompanionKit/)

**調試注意事項：** 全像攝影遠端程式庫可能會擲回第一個可能發生的例外狀況。 根據當時作用中的 Visual Studio 例外狀況設定，這些例外狀況可能會顯示在偵錯工具會話中。 「全像」遠端程式庫會在內部攔截這些例外狀況，而且可以忽略。
