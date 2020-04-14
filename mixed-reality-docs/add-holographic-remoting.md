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
# <a name="add-holographic-remoting-hololens-1st-gen"></a><span data-ttu-id="5dcf3-104">新增全像攝影遠端（HoloLens （第1代））</span><span class="sxs-lookup"><span data-stu-id="5dcf3-104">Add Holographic Remoting (HoloLens (1st gen))</span></span>

>[!IMPORTANT]
><span data-ttu-id="5dcf3-105">本檔說明如何建立 HoloLens 1 的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="5dcf3-106">**HoloLens （第1代）** 的主機應用程式必須使用 NuGet **1.x.x**套件1.x 版。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="5dcf3-107">這表示針對 HoloLens 1 所撰寫的主機應用程式與 HoloLens 2 不相容，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="5dcf3-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5dcf3-108">HoloLens 2</span></span>

<span data-ttu-id="5dcf3-109">使用全像攝影遠端的 HoloLens 開發人員必須更新其應用程式，使其與 HoloLens 2 相容。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="5dcf3-110">這需要新版本的全像攝影遠端 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="5dcf3-111">如果應用程式使用的全像是在版本號碼小於2.0.0.0 的「全像攝影」 NuGet 套件嘗試連接到 HoloLens 2 上的全像「遠端播放」，連線將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-111">If an application using the Holographic Remoting NuGet package with a version number smaller than 2.0.0.0 attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>

>[!NOTE]
><span data-ttu-id="5dcf3-112">您可以在[這裡](holographic-remoting-create-host.md)找到 HoloLens 2 的特定指引。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-host.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="5dcf3-113">在您的桌上型電腦或 UWP 應用程式中新增全像的遠端功能</span><span class="sxs-lookup"><span data-stu-id="5dcf3-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="5dcf3-114">此頁面說明如何在桌上型電腦或 UWP 應用程式中新增全像攝影遠端功能。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="5dcf3-115">全像攝影遠端可讓您的應用程式以桌上型電腦或 UWP 裝置（例如 Xbox One）上裝載的全像攝影內容為 HoloLens，讓您可以存取更多的系統資源，並讓您能夠將遠端[沉浸式流覽](app-views.md)整合到現有的桌上型電腦軟體。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-115">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="5dcf3-116">遠端主機應用程式會從 HoloLens 接收輸入資料流程、在虛擬沉浸式視圖中轉譯內容，以及將內容框架串流回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-116">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="5dcf3-117">連接是使用標準 Wi-fi 建立的。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-117">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="5dcf3-118">若要使用遠端處理，您將使用 NuGet 套件將全像的遠端處理新增至桌面或 UWP 應用程式，並撰寫程式碼來處理連接並在沉浸式視圖中轉譯。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-118">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="5dcf3-119">Helper 程式庫包含在程式碼範例中，可簡化處理裝置連線的工作。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-119">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="5dcf3-120">一般遠端連線的延遲時間會降到50毫秒。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-120">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="5dcf3-121">Player 應用程式可以即時報告延遲。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-121">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="5dcf3-122">本文中的程式碼片段目前示範如何使用C++/cx， C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT，如全像攝影專案範本中所使用。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-122">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="5dcf3-123">概念相當於C++/WinRT 專案，但您必須轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-123">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="5dcf3-124">取得遠端 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="5dcf3-124">Get the remoting NuGet packages</span></span>

<span data-ttu-id="5dcf3-125">請遵循下列步驟來取得適用于全像攝影遠端的 NuGet 套件，並從您的專案新增參考：</span><span class="sxs-lookup"><span data-stu-id="5dcf3-125">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="5dcf3-126">前往 Visual Studio 中的專案。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-126">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="5dcf3-127">以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 套件 ...** ]</span><span class="sxs-lookup"><span data-stu-id="5dcf3-127">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="5dcf3-128">在出現的面板中，按一下 **[流覽]** ，然後搜尋「全像遠端處理」。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-128">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="5dcf3-129">選取 [ **Microsoft 全息**]，然後按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-129">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="5dcf3-130">如果出現 [**預覽**] 對話方塊，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-130">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="5dcf3-131">下一個出現的對話方塊是授權合約。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-131">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="5dcf3-132">按一下 [**我接受**] 以接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-132">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="5dcf3-133">建立 HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="5dcf3-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="5dcf3-134">首先，我們需要 HolographicStreamerHelpers 的實例。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-134">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="5dcf3-135">將此加入至將會處理遠端的類別。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-135">Add this to the class that will be handling remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="5dcf3-136">您也必須追蹤連接狀態。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-136">You'll also need to track connection state.</span></span> <span data-ttu-id="5dcf3-137">如果您想要轉譯預覽，則需要有材質，才能將它複製到其中。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-137">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="5dcf3-138">您也需要一些東西，像是線上狀態鎖定，還有一些儲存 HoloLens IP 位址的方法，依此類推。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-138">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="5dcf3-139">將 HolographicStreamerHelpers 初始化並聯機至 HoloLens</span><span class="sxs-lookup"><span data-stu-id="5dcf3-139">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="5dcf3-140">若要連線至 HoloLens 裝置，請建立 HolographicStreamerHelpers 的實例，並連接到目標 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-140">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="5dcf3-141">您必須設定影片畫面大小，使其符合 HoloLens 的顯示寬度和高度，因為全像攝影遠端程式庫會預期編碼器和解碼器解析度完全相符。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-141">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

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

<span data-ttu-id="5dcf3-142">裝置連接是非同步。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-142">The device connection is asynchronous.</span></span> <span data-ttu-id="5dcf3-143">您的應用程式必須提供連接、中斷連線和框架傳送事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-143">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="5dcf3-144">OnConnected 事件可以更新 UI、開始呈現等等。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-144">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="5dcf3-145">在我們的桌面程式碼範例中，我們會使用「已連線」訊息來更新視窗標題。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-145">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="5dcf3-146">OnDisconnected 事件可以處理重新連接、UI 更新等等。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-146">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="5dcf3-147">在此範例中，如果發生暫時性失敗，我們會重新連線。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-147">In this example, we reconnect if there is a transient failure.</span></span>

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

<span data-ttu-id="5dcf3-148">當遠端處理元件準備好要傳送框架時，您的應用程式會有機會在 SendFrameEvent 中建立複本。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-148">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="5dcf3-149">在這裡，我們會將畫面複製到交換鏈，讓我們可以將它顯示在預覽視窗中。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-149">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

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

### <a name="render-holographic-content"></a><span data-ttu-id="5dcf3-150">呈現全像攝影內容</span><span class="sxs-lookup"><span data-stu-id="5dcf3-150">Render holographic content</span></span>

<span data-ttu-id="5dcf3-151">若要使用遠端處理來轉譯內容，您可以在桌面或 UWP 應用程式內設定虛擬 IFrameworkView，並處理來自遠端的全息框架。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-151">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="5dcf3-152">所有的 Windows 全像攝影應用程式開發介面都是以相同的方式來使用，但其設定方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-152">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="5dcf3-153">「全像攝影空間」和「語音」元件不會自行建立，而是來自您的 HolographicRemotingHelpers 類別：</span><span class="sxs-lookup"><span data-stu-id="5dcf3-153">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="5dcf3-154">您不需要在 Run 方法內使用 update 迴圈，而是從桌面或 UWP 應用程式的主要迴圈提供滴答更新。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-154">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="5dcf3-155">這可讓您的桌面或 UWP 應用程式繼續控制訊息處理。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-155">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="5dcf3-156">全像攝影應用程式視圖的 Tick （）方法會完成更新、繪製、呈現迴圈的一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-156">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

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

<span data-ttu-id="5dcf3-157">全像攝影應用程式視圖的更新、轉譯和呈現迴圈，與在 HoloLens 上執行時完全相同，不同之處在于您可以存取桌上型電腦上的系統資源數量更大。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-157">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="5dcf3-158">您可以轉譯多個三角形、擁有更多的繪製行程、執行更多物理，以及使用 x64 進程來載入需要超過 2 GB RAM 的內容。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-158">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="5dcf3-159">中斷連線並結束遠端會話</span><span class="sxs-lookup"><span data-stu-id="5dcf3-159">Disconnect and end the remote session</span></span>

<span data-ttu-id="5dcf3-160">中斷連線-例如，當使用者按一下 UI 按鈕以中斷連接 HolographicStreamerHelpers 上的呼叫中斷連接（），然後放開物件。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-160">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

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

## <a name="get-the-remoting-player"></a><span data-ttu-id="5dcf3-161">取得遠端播放機</span><span class="sxs-lookup"><span data-stu-id="5dcf3-161">Get the remoting player</span></span>

<span data-ttu-id="5dcf3-162">Windows app store 中提供的 Windows 全像遠端處理播放程式，是遠端主機應用程式連接的端點。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-162">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="5dcf3-163">若要取得 Windows 全像遠端播放程式，請從 HoloLens 流覽 Windows app store、搜尋遠端處理，然後下載應用程式。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-163">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="5dcf3-164">「遠端播放程式」包含在螢幕上顯示統計資料的功能，在對遠端處理主機應用程式進行調試時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-164">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="5dcf3-165">記事和資源</span><span class="sxs-lookup"><span data-stu-id="5dcf3-165">Notes and resources</span></span>

<span data-ttu-id="5dcf3-166">全像攝影應用程式視圖需要一種方式，讓您的應用程式能夠使用 Direct3D 裝置，這必須用來初始化全像攝影空間。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-166">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="5dcf3-167">您的應用程式應該使用此 Direct3D 裝置來複製和顯示預覽畫面。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-167">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="5dcf3-168">程式**代碼範例：** 提供完整的全像攝影版遠端處理常式代碼範例，其中包含與使用 XAML 的桌面 Win32、UWP DirectX 和 UWP 的遠端處理和遠端處理主項目目相容的全像攝影應用程式視圖。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-168">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="5dcf3-169">若要取得它，請移至這裡：</span><span class="sxs-lookup"><span data-stu-id="5dcf3-169">To get it, go here:</span></span>
* [<span data-ttu-id="5dcf3-170">遠端處理的 Windows 全像程式碼範例</span><span class="sxs-lookup"><span data-stu-id="5dcf3-170">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="5dcf3-171">**調試注意事項：** 全像攝影遠端程式庫可能會擲回第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-171">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="5dcf3-172">根據當時作用中的 Visual Studio 例外狀況設定，這些例外狀況可能會顯示在偵錯工具會話中。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-172">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="5dcf3-173">「全像」遠端程式庫會在內部攔截這些例外狀況，而且可以忽略。</span><span class="sxs-lookup"><span data-stu-id="5dcf3-173">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
