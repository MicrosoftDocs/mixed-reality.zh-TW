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
# <a name="add-holographic-remoting"></a><span data-ttu-id="4f03a-104">新增全像攝影版的遠端處理</span><span class="sxs-lookup"><span data-stu-id="4f03a-104">Add holographic remoting</span></span>

## <a name="hololens-2"></a><span data-ttu-id="4f03a-105">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4f03a-105">HoloLens 2</span></span>

> [!NOTE]
> <span data-ttu-id="4f03a-106">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="4f03a-106">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="4f03a-107">使用全像攝影版的遠端處理的 HoloLens 開發人員必須更新他們的應用程式，使其與 HoloLens 2 相容。</span><span class="sxs-lookup"><span data-stu-id="4f03a-107">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span>  <span data-ttu-id="4f03a-108">這將需要全像攝影版的遠端處理 NuGet 封裝尚未公開可用的新版本。</span><span class="sxs-lookup"><span data-stu-id="4f03a-108">This will require a new version of the Holographic Remoting NuGet package that is not publicly available yet.</span></span>  <span data-ttu-id="4f03a-109">如果連接到全像攝影版 HoloLens 2 上的遠端播放程式嘗試使用 HoloLens NuGet 套件的應用程式，連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="4f03a-109">If an application using the HoloLens NuGet package attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>  <span data-ttu-id="4f03a-110">HoloLens 2 NuGet 套件可供使用之後，請觀看此頁面的更新。</span><span class="sxs-lookup"><span data-stu-id="4f03a-110">Watch this page for updates once the HoloLens 2 NuGet package is available.</span></span>

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="4f03a-111">將全像攝影版的遠端執行功能新增至您的桌面或 UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="4f03a-111">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="4f03a-112">此頁面說明如何新增全像攝影版的遠端桌面或 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f03a-112">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="4f03a-113">全像攝影版的遠端處理可讓您的應用程式以裝載桌上型 PC 或 Xbox One，允許更多系統資源的存取，並讓您可以整合遠端例如 UWP 裝置上的全像攝影版內容設為目標的 HoloLens[沈浸式檢視](app-views.md)至現有的桌面電腦軟體。</span><span class="sxs-lookup"><span data-stu-id="4f03a-113">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="4f03a-114">遠端主機應用程式收到 HoloLens 的輸入的資料流、 呈現內容，在虛擬的沈浸式檢視中，及資料流的內容框架返回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="4f03a-114">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="4f03a-115">連線是使用標準的 Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="4f03a-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="4f03a-116">若要使用遠端執行功能，您會將全像攝影版的遠端執行功能新增至您的桌面或 UWP 應用程式，使用 NuGet 套件，並撰寫程式碼來處理連接，並在沉浸式檢視中轉譯。</span><span class="sxs-lookup"><span data-stu-id="4f03a-116">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="4f03a-117">協助程式庫會包含在程式碼範例，可簡化處理裝置連線的工作。</span><span class="sxs-lookup"><span data-stu-id="4f03a-117">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="4f03a-118">必須為 50 毫秒的延遲低的典型的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="4f03a-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="4f03a-119">播放器應用程式可以報告在即時的延遲。</span><span class="sxs-lookup"><span data-stu-id="4f03a-119">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="4f03a-120">目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="4f03a-120">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="4f03a-121">概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f03a-121">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="4f03a-122">取得遠端處理 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="4f03a-122">Get the remoting NuGet packages</span></span>

<span data-ttu-id="4f03a-123">請遵循下列步驟，針對全像攝影版的遠端執行功能，讓 NuGet 套件，並從您的專案中加入的參考：</span><span class="sxs-lookup"><span data-stu-id="4f03a-123">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="4f03a-124">請移至您在 Visual Studio 中的專案。</span><span class="sxs-lookup"><span data-stu-id="4f03a-124">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="4f03a-125">以滑鼠右鍵按一下專案節點，然後選取**管理 NuGet 套件...**</span><span class="sxs-lookup"><span data-stu-id="4f03a-125">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="4f03a-126">在出現的窗格中，按一下**瀏覽**，然後搜尋 「 全像攝影版的遠端執行功能 >。</span><span class="sxs-lookup"><span data-stu-id="4f03a-126">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="4f03a-127">選取  **Microsoft.Holographic.Remoting**然後按一下**安裝**。</span><span class="sxs-lookup"><span data-stu-id="4f03a-127">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="4f03a-128">如果**Preview**  對話方塊出現時，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4f03a-128">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="4f03a-129">下一個出現的對話方塊是 「 授權合約 」。</span><span class="sxs-lookup"><span data-stu-id="4f03a-129">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="4f03a-130">按一下 **我接受**接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="4f03a-130">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="4f03a-131">建立 HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="4f03a-131">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="4f03a-132">首先，我們需要 HolographicStreamerHelpers 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f03a-132">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="4f03a-133">加入這將會處理遠端服務的類別。</span><span class="sxs-lookup"><span data-stu-id="4f03a-133">Add this to the class that will be handling remoting.</span></span>

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="4f03a-134">您也必須追蹤連線狀態。</span><span class="sxs-lookup"><span data-stu-id="4f03a-134">You'll also need to track connection state.</span></span> <span data-ttu-id="4f03a-135">如果您想要呈現的預覽，您需要有要將它複製到的材質。</span><span class="sxs-lookup"><span data-stu-id="4f03a-135">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="4f03a-136">您也需要一些像是連線狀態鎖定，而儲存 HoloLens，IP 位址的某種方式等等。</span><span class="sxs-lookup"><span data-stu-id="4f03a-136">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="4f03a-137">初始化 HolographicStreamerHelpers 並連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="4f03a-137">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="4f03a-138">若要連接到 HoloLens 裝置，建立 HolographicStreamerHelpers 的執行個體並連線至目標 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="4f03a-138">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="4f03a-139">您必須設定視訊畫面格大小以符合 HoloLens 顯示寬度和高度，因為全像攝影版的遠端處理程式庫預期編碼器和解碼器完全相符的解決方法。</span><span class="sxs-lookup"><span data-stu-id="4f03a-139">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

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

<span data-ttu-id="4f03a-140">裝置連線是非同步的。</span><span class="sxs-lookup"><span data-stu-id="4f03a-140">The device connection is asynchronous.</span></span> <span data-ttu-id="4f03a-141">您的應用程式必須提供事件處理常式的連接，中斷連線，及框架傳送事件。</span><span class="sxs-lookup"><span data-stu-id="4f03a-141">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="4f03a-142">OnConnected 事件可以更新 UI，開始轉譯，等等。</span><span class="sxs-lookup"><span data-stu-id="4f03a-142">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="4f03a-143">在桌面程式碼範例中，我們會更新視窗標題的 「 連線 」 的訊息。</span><span class="sxs-lookup"><span data-stu-id="4f03a-143">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="4f03a-144">OnDisconnected 事件可以處理重新連線、 UI 更新等等。</span><span class="sxs-lookup"><span data-stu-id="4f03a-144">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="4f03a-145">在此範例中，我們重新連接發生暫時性失敗時。</span><span class="sxs-lookup"><span data-stu-id="4f03a-145">In this example, we reconnect if there is a transient failure.</span></span>

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

<span data-ttu-id="4f03a-146">Remoting 元件準備好要傳送在範圍內時，您的應用程式提供一份在 SendFrameEvent 的機會。</span><span class="sxs-lookup"><span data-stu-id="4f03a-146">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="4f03a-147">在這裡，我們將複製的框架到交換鏈結，讓我們可以將它顯示在預覽視窗中。</span><span class="sxs-lookup"><span data-stu-id="4f03a-147">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

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

### <a name="render-holographic-content"></a><span data-ttu-id="4f03a-148">呈現全像攝影版的內容</span><span class="sxs-lookup"><span data-stu-id="4f03a-148">Render holographic content</span></span>

<span data-ttu-id="4f03a-149">要呈現的內容使用遠端執行功能，您設定您的桌面或 UWP 應用程式中的虛擬 IFrameworkView 並處理全像攝影版的畫面格，從遠端處理。</span><span class="sxs-lookup"><span data-stu-id="4f03a-149">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="4f03a-150">所有的 Windows 全像攝影版 api 都是的使用相同的方式，此檢視中，但是它的設定方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="4f03a-150">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="4f03a-151">而不用建立他們自己的全像攝影版的空間和語音元件來自 HolographicRemotingHelpers 類別：</span><span class="sxs-lookup"><span data-stu-id="4f03a-151">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="4f03a-152">而不是使用執行方法內更新迴圈，您可以提供從桌面或 UWP 應用程式的主迴圈的刻度更新。</span><span class="sxs-lookup"><span data-stu-id="4f03a-152">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="4f03a-153">這可讓您的桌面或保留在訊息處理的控制項中的 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f03a-153">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="4f03a-154">全像攝影版的應用程式檢視的 Tick() 方法完成一次更新、 繪製時，出現迴圈的反覆運算。</span><span class="sxs-lookup"><span data-stu-id="4f03a-154">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

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

<span data-ttu-id="4f03a-155">全像攝影版的應用程式檢視更新、 轉譯，並出現迴圈是完全相同，即 HoloLens-上執行時不同之處在於您在桌面的電腦上有更大的系統資源的存取。</span><span class="sxs-lookup"><span data-stu-id="4f03a-155">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="4f03a-156">您可以呈現多更多的三角形，有多個繪圖的階段，詳細物理條件，並使用 x64 處理序載入需要的內容超過 2 GB 的 RAM。</span><span class="sxs-lookup"><span data-stu-id="4f03a-156">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="4f03a-157">中斷連線，然後結束遠端工作階段</span><span class="sxs-lookup"><span data-stu-id="4f03a-157">Disconnect and end the remote session</span></span>

<span data-ttu-id="4f03a-158">若要中斷連線-例如，當使用者按一下 中斷連接-U 按鈕呼叫 Disconnect() 上 HolographicStreamerHelpers，並再釋放物件。</span><span class="sxs-lookup"><span data-stu-id="4f03a-158">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

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

## <a name="get-the-remoting-player"></a><span data-ttu-id="4f03a-159">取得遠端處理播放程式</span><span class="sxs-lookup"><span data-stu-id="4f03a-159">Get the remoting player</span></span>

<span data-ttu-id="4f03a-160">Windows 全像攝影版的遠端播放程式會為端點連線至遠端主機應用程式，提供 Windows 應用程式存放區中。</span><span class="sxs-lookup"><span data-stu-id="4f03a-160">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="4f03a-161">若要取得 Windows 全像攝影版的遠端播放程式，請從您的 HoloLens 搜尋針對遠端執行功能，瀏覽 Windows app store 並下載應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f03a-161">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="4f03a-162">遠端處理播放程式會包含偵錯遠端裝載應用程式時很有用的功能，畫面上，顯示統計資料。</span><span class="sxs-lookup"><span data-stu-id="4f03a-162">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="4f03a-163">資訊與資源</span><span class="sxs-lookup"><span data-stu-id="4f03a-163">Notes and resources</span></span>

<span data-ttu-id="4f03a-164">全像攝影版的應用程式檢視必須有辦法提供您的應用程式與 Direct3D 裝置，必須用來初始化全像攝影版的空間。</span><span class="sxs-lookup"><span data-stu-id="4f03a-164">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="4f03a-165">您的應用程式應該使用 Direct3D 裝置複製，並顯示在預覽畫面格。</span><span class="sxs-lookup"><span data-stu-id="4f03a-165">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="4f03a-166">**程式碼範例：** 完整的全像攝影版的遠端程式碼範例已使用，其中包含適用於遠端處理與遠端桌面的 Win32、 UWP DirectX 和 XAML 使用 UWP 的主應用程式專案的全像攝影版的應用程式檢視。</span><span class="sxs-lookup"><span data-stu-id="4f03a-166">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="4f03a-167">若要取得它，請前往：</span><span class="sxs-lookup"><span data-stu-id="4f03a-167">To get it, go here:</span></span>
* [<span data-ttu-id="4f03a-168">針對遠端執行功能的 Windows 全像攝影版的程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4f03a-168">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="4f03a-169">**偵錯的附註：** 全像攝影版的遠端處理程式庫可能會擲回第一個可能發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f03a-169">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="4f03a-170">這些例外狀況可能會出現在偵錯工作階段，根據當時是作用中的 Visual Studio 的例外狀況設定。</span><span class="sxs-lookup"><span data-stu-id="4f03a-170">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="4f03a-171">這些例外狀況會在內部攔截到全像攝影版的遠端處理程式庫，您可以忽略。</span><span class="sxs-lookup"><span data-stu-id="4f03a-171">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
