---
title: 撰寫自訂的全像遠端播放播放機
description: 藉由建立自訂的全像遠端播放機應用程式, 您可以建立自訂應用程式, 能夠將遠端電腦上呈現的內容顯示到 HoloLens 2。 本文說明如何達成此目的。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: fdc3d3bbd72d0812377d6a70c975f2111e1a2224
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718092"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="62208-105">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="62208-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="62208-106">本檔說明如何建立 HoloLens 2 的自訂播放機應用程式。</span><span class="sxs-lookup"><span data-stu-id="62208-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="62208-107">針對 HoloLens 2 撰寫的自訂播放程式與針對 HoloLens 1 撰寫的主機應用程式不相容。</span><span class="sxs-lookup"><span data-stu-id="62208-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="62208-108">這表示這兩個應用程式都必須使用NuGet 套件 2.x. x 版。</span><span class="sxs-lookup"><span data-stu-id="62208-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="62208-109">藉由建立自訂的全像遠端播放機應用程式, 您可以建立自訂應用程式, 讓它能夠在 HoloLens 2 的遠端電腦上顯示[沉浸式視圖](app-views.md)。</span><span class="sxs-lookup"><span data-stu-id="62208-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="62208-110">本文說明如何達成此目的。</span><span class="sxs-lookup"><span data-stu-id="62208-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="62208-111">此頁面上的所有程式碼和工作專案都可以在全像的[遠端範例 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。</span><span class="sxs-lookup"><span data-stu-id="62208-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="62208-112">全像攝影遠端播放程式可讓您的應用程式顯示在桌上型電腦或 UWP 裝置 (例如 Xbox one) 上[轉譯](rendering.md)的全像攝影內容, 以允許存取更多系統資源。</span><span class="sxs-lookup"><span data-stu-id="62208-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="62208-113">全像攝影的遠端播放程式應用程式會將輸入資料串流至全像攝影的遠端主機應用程式, 並以影片和音訊串流的形式接收沉浸式觀賞。</span><span class="sxs-lookup"><span data-stu-id="62208-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="62208-114">連接是使用標準 Wi-fi 建立的。</span><span class="sxs-lookup"><span data-stu-id="62208-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="62208-115">若要建立播放機應用程式, 您將使用 NuGet 套件將全像的遠端處理新增至 UWP 應用程式, 並撰寫程式碼來處理連接並顯示沉浸式視圖。</span><span class="sxs-lookup"><span data-stu-id="62208-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="62208-116">先決條件</span><span class="sxs-lookup"><span data-stu-id="62208-116">Prerequisites</span></span>

<span data-ttu-id="62208-117">良好的起點是已以 Windows Mixed Reality API 為目標的可運作 DirectX 型 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="62208-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="62208-118">如需詳細資訊, 請參閱[DirectX 開發總覽](directx-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="62208-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="62208-119">如果您沒有現有的應用程式, 而且想要從頭開始, 全像[ C++投影專案範本](creating-a-holographic-directx-project.md)是不錯的起點。</span><span class="sxs-lookup"><span data-stu-id="62208-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="62208-120">任何使用全像攝影遠端的應用程式, 都應該撰寫成使用[多執行緒的單元](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="62208-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="62208-121">支援使用[單一執行緒的 apartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) , 但會導致在播放期間的效能和可能會間斷情形。</span><span class="sxs-lookup"><span data-stu-id="62208-121">The use of a [single-threaded appartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="62208-122">使用C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started)時, 多執行緒的單元是預設值。</span><span class="sxs-lookup"><span data-stu-id="62208-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="62208-123">取得全像攝影的遠端 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="62208-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="62208-124">若要將 NuGet 套件新增至 Visual Studio 中的專案, 必須執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="62208-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="62208-125">在 Visual Studio 中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="62208-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="62208-126">以滑鼠右鍵按一下專案節點, 然後選取 [**管理 NuGet 套件 ...** ]</span><span class="sxs-lookup"><span data-stu-id="62208-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="62208-127">在出現的面板中, 按一下 **[流覽]** , 然後搜尋「全像遠端處理」。</span><span class="sxs-lookup"><span data-stu-id="62208-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="62208-128">選取 [ **Microsoft 全息**], 並確定挑選最新的 2.x 版, 然後按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="62208-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="62208-129">如果出現 [**預覽**] 對話方塊, 請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="62208-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="62208-130">下一個出現的對話方塊是授權合約。</span><span class="sxs-lookup"><span data-stu-id="62208-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="62208-131">按一下 [**我接受**] 以接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="62208-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="62208-132">NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```套件內的包含適用于全像「全像」遠端處理所公開之 API 的詳細檔。</span><span class="sxs-lookup"><span data-stu-id="62208-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="62208-133">修改應用程式的 package.appxmanifest.xml</span><span class="sxs-lookup"><span data-stu-id="62208-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="62208-134">若要讓應用程式知道 NuGet 套件所新增的 AppRemoting, 您必須在專案上執行下列步驟:</span><span class="sxs-lookup"><span data-stu-id="62208-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="62208-135">在 方案總管以滑鼠右鍵按一下**package.appxmanifest.xml**檔案, 然後選取 **開啟方式**...。</span><span class="sxs-lookup"><span data-stu-id="62208-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="62208-136">選取 [ **XML (文字) 編輯器**], 然後按一下 [確定]</span><span class="sxs-lookup"><span data-stu-id="62208-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="62208-137">將下列幾行新增至檔案並儲存</span><span class="sxs-lookup"><span data-stu-id="62208-137">Add the following lines to the file and save</span></span>
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a><span data-ttu-id="62208-138">建立播放者內容</span><span class="sxs-lookup"><span data-stu-id="62208-138">Create the player context</span></span>

<span data-ttu-id="62208-139">第一個步驟是應用程式應該建立播放機內容。</span><span class="sxs-lookup"><span data-stu-id="62208-139">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="62208-140">「全像」遠端處理的運作方式, 是以遠端處理特定執行時間取代 Windows 中的 Windows Mixed Reality 執行時間。</span><span class="sxs-lookup"><span data-stu-id="62208-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="62208-141">這會在建立播放者內容期間完成。</span><span class="sxs-lookup"><span data-stu-id="62208-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="62208-142">因此, 在建立播放程式內容之前, 任何 Windows Mixed Reality API 上的呼叫可能會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="62208-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="62208-143">建議的方法是在與任何混合現實 API 互動之前, 儘早建立播放者內容。</span><span class="sxs-lookup"><span data-stu-id="62208-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="62208-144">在```PlayerContext::Create()```使用建立或之後抓取的物件呼叫之前, 絕不會透過任何 Windows Mixed Reality API 混合建立或抓取的物件。</span><span class="sxs-lookup"><span data-stu-id="62208-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="62208-145">接下來, 您可以藉由呼叫[HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)來建立 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="62208-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="62208-146">連接到主機</span><span class="sxs-lookup"><span data-stu-id="62208-146">Connect to the host</span></span>

<span data-ttu-id="62208-147">一旦播放機應用程式準備好呈現內容, 就可以建立與主機的連接。</span><span class="sxs-lookup"><span data-stu-id="62208-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="62208-148">您可以透過下列其中一種以下方式來建立連接:</span><span class="sxs-lookup"><span data-stu-id="62208-148">The connection can be established in one of the follwing ways:</span></span>
1) <span data-ttu-id="62208-149">在 HoloLens 2 上執行的播放機應用程式會連接到主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="62208-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="62208-150">主機應用程式會連線到在 HoloLens 2 上執行的 player 應用程式。</span><span class="sxs-lookup"><span data-stu-id="62208-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="62208-151">若要從 player 應用程式連線到主機, 請```Connect```在指定主機名稱和埠的 player 內容上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="62208-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="62208-152">預設通訊埠為**8265**。</span><span class="sxs-lookup"><span data-stu-id="62208-152">The default port is **8265**.</span></span>

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
><span data-ttu-id="62208-153">如同任何C++/WinRT API ```Connect``` , 可能會擲回需要處理的 WinRT:: hresult_error。</span><span class="sxs-lookup"><span data-stu-id="62208-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="62208-154">接聽 player 應用程式上的連入連線可以藉由呼叫```Listen```方法來完成。</span><span class="sxs-lookup"><span data-stu-id="62208-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="62208-155">在此呼叫期間, 可以指定交握埠和傳輸埠。</span><span class="sxs-lookup"><span data-stu-id="62208-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="62208-156">交握埠會用於初始交握。</span><span class="sxs-lookup"><span data-stu-id="62208-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="62208-157">然後, 資料會透過傳輸埠傳送。</span><span class="sxs-lookup"><span data-stu-id="62208-157">The data is then send over the transport port.</span></span> <span data-ttu-id="62208-158">預設會使用埠號碼**8265**和**8266** 。</span><span class="sxs-lookup"><span data-stu-id="62208-158">By default port number **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a><span data-ttu-id="62208-159">處理連接相關的事件</span><span class="sxs-lookup"><span data-stu-id="62208-159">Handling connection related events</span></span>

<span data-ttu-id="62208-160">會```PlayerContext```公開三個事件來監視連接的狀態。</span><span class="sxs-lookup"><span data-stu-id="62208-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="62208-161">OnConnected:已成功建立與主機的連接時觸發。</span><span class="sxs-lookup"><span data-stu-id="62208-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="62208-162">OnDisconnected:在已建立的連接終止或無法建立連接時觸發。</span><span class="sxs-lookup"><span data-stu-id="62208-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
><span data-ttu-id="62208-163">可能```ConnectionFailureReason```的```Microsoft.Holographic.AppRemoting.idl```值記錄在[檔案](#idl)中。</span><span class="sxs-lookup"><span data-stu-id="62208-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="62208-164">OnListening:接聽連入連線時, 會啟動。</span><span class="sxs-lookup"><span data-stu-id="62208-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="62208-165">此外, 您還可以使用播放機內容上```ConnectionState```的屬性來查詢連接狀態。</span><span class="sxs-lookup"><span data-stu-id="62208-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="62208-166">顯示遠端呈現的框架</span><span class="sxs-lookup"><span data-stu-id="62208-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="62208-167">若要顯示遠端呈現的內容, ```PlayerContext::BlitRemoteFrame()```請在呈現[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)時呼叫。</span><span class="sxs-lookup"><span data-stu-id="62208-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="62208-168">```BlitRemoteFrame()```需要將目前 HolographicFrame 的背景緩衝區系結為轉譯目標。</span><span class="sxs-lookup"><span data-stu-id="62208-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="62208-169">您可以透過[Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)屬性, 從[HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)接收後端緩衝區。</span><span class="sxs-lookup"><span data-stu-id="62208-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="62208-170">呼叫時, ```BlitRemoteFrame()```會將最新收到的框架從主應用程式複製到 HolographicFrame 的 BackBuffer。</span><span class="sxs-lookup"><span data-stu-id="62208-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="62208-171">此外, 如果遠端應用程式在呈現遠端框架期間已指定焦點, 則會設定焦點集合。</span><span class="sxs-lookup"><span data-stu-id="62208-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="62208-172">```PlayerContext::BlitRemoteFrame()```可能會覆寫目前框架的焦點。</span><span class="sxs-lookup"><span data-stu-id="62208-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="62208-173">若要指定回溯焦點點, 請先```PlayerContext::BlitRemoteFrame()```呼叫[HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 。</span><span class="sxs-lookup"><span data-stu-id="62208-173">To specifiy a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="62208-174">若要 overrwrite 遠端焦點點, 請在之後```PlayerContext::BlitRemoteFrame()```呼叫[HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 。</span><span class="sxs-lookup"><span data-stu-id="62208-174">To overrwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="62208-175">成功時, ```BlitRemoteFrame()``` ```BlitResult::Success_Color```會傳回。</span><span class="sxs-lookup"><span data-stu-id="62208-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="62208-176">否則, 它會傳回失敗原因:</span><span class="sxs-lookup"><span data-stu-id="62208-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="62208-177">```BlitResult::Failed_NoRemoteFrameAvailable```:失敗, 因為沒有可用的遠端框架。</span><span class="sxs-lookup"><span data-stu-id="62208-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="62208-178">```BlitResult::Failed_NoCamera```:失敗, 因為沒有任何相機存在。</span><span class="sxs-lookup"><span data-stu-id="62208-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="62208-179">選擇性：取得最後一個遠端框架的相關統計資料</span><span class="sxs-lookup"><span data-stu-id="62208-179">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="62208-180">若要診斷效能或網路問題, 可以```PlayerContext::LastFrameStatistics```透過屬性來抓取最後一個遠端框架的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="62208-180">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="62208-181">在呼叫[HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)期間, 會更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="62208-181">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="62208-182">如需詳細資訊, 請```PlayerFrameStatistics```參閱檔案```Microsoft.Holographic.AppRemoting.idl```中的[檔](#idl)。</span><span class="sxs-lookup"><span data-stu-id="62208-182">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="62208-183">選擇性：自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="62208-183">Optional: Custom data channels</span></span>

<span data-ttu-id="62208-184">自訂資料通道可以用來透過已建立的遠端連線傳送使用者資料。</span><span class="sxs-lookup"><span data-stu-id="62208-184">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="62208-185">如需詳細資訊, 請參閱[自訂資料通道](holographic-remoting-custom-data-channels.md)。</span><span class="sxs-lookup"><span data-stu-id="62208-185">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="62208-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62208-186">See Also</span></span>
* [<span data-ttu-id="62208-187">撰寫全像的遠端主機應用程式</span><span class="sxs-lookup"><span data-stu-id="62208-187">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="62208-188">自訂全像攝影遠端資料通道</span><span class="sxs-lookup"><span data-stu-id="62208-188">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="62208-189">使用全像攝影遠端建立安全連線</span><span class="sxs-lookup"><span data-stu-id="62208-189">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="62208-190">全像攝影遠端疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="62208-190">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="62208-191">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="62208-191">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="62208-192">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="62208-192">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)