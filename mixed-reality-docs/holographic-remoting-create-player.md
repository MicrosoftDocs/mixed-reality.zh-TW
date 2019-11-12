---
title: 撰寫自訂的全像遠端播放播放機
description: 藉由建立自訂的全像遠端播放機應用程式，您可以建立自訂應用程式，能夠將遠端電腦上呈現的內容顯示到 HoloLens 2。 本文說明如何達成此目的。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 1f8a0cbe0f6da88c0c5e5a695737d8694020635c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926659"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="c488c-105">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="c488c-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="c488c-106">本檔說明如何建立 HoloLens 2 的自訂播放機應用程式。</span><span class="sxs-lookup"><span data-stu-id="c488c-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="c488c-107">針對 HoloLens 2 撰寫的自訂播放程式與針對 HoloLens 1 撰寫的主機應用程式不相容。</span><span class="sxs-lookup"><span data-stu-id="c488c-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="c488c-108">這表示這兩個應用程式都必須使用 NuGet 套件**2.x. x 版。**</span><span class="sxs-lookup"><span data-stu-id="c488c-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="c488c-109">藉由建立自訂的全像遠端播放機應用程式，您可以建立自訂應用程式，讓它能夠在 HoloLens 2 的遠端電腦上顯示[沉浸式視圖](app-views.md)。</span><span class="sxs-lookup"><span data-stu-id="c488c-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="c488c-110">本文說明如何達成此目的。</span><span class="sxs-lookup"><span data-stu-id="c488c-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="c488c-111">此頁面上的所有程式碼和工作專案都可以在全像的[遠端範例 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。</span><span class="sxs-lookup"><span data-stu-id="c488c-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="c488c-112">全像攝影遠端播放程式可讓您的應用程式顯示在桌上型電腦或 UWP 裝置（例如 Xbox One）上[轉譯的全像攝影內容，](rendering.md)以允許存取更多系統資源。</span><span class="sxs-lookup"><span data-stu-id="c488c-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="c488c-113">全像攝影的遠端播放程式應用程式會將輸入資料串流至全像攝影的遠端主機應用程式，並以影片和音訊串流的形式接收沉浸式觀賞。</span><span class="sxs-lookup"><span data-stu-id="c488c-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="c488c-114">連接是使用標準 Wi-fi 建立的。</span><span class="sxs-lookup"><span data-stu-id="c488c-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="c488c-115">若要建立播放機應用程式，您將使用 NuGet 套件將全像的遠端處理新增至 UWP 應用程式，並撰寫程式碼來處理連接並顯示沉浸式視圖。</span><span class="sxs-lookup"><span data-stu-id="c488c-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="c488c-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="c488c-116">Prerequisites</span></span>

<span data-ttu-id="c488c-117">良好的起點是已以 Windows Mixed Reality API 為目標的可運作 DirectX 型 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c488c-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="c488c-118">如需詳細資訊，請參閱[DirectX 開發總覽](directx-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c488c-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="c488c-119">如果您沒有現有的應用程式，而且想要從頭開始，全像[ C++投影專案範本](creating-a-holographic-directx-project.md)是不錯的起點。</span><span class="sxs-lookup"><span data-stu-id="c488c-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c488c-120">任何使用全像攝影遠端的應用程式，都應該撰寫成使用[多執行緒的單元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="c488c-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="c488c-121">支援使用[單一執行緒的 apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) ，但會導致在播放期間的效能和可能會間斷情形。</span><span class="sxs-lookup"><span data-stu-id="c488c-121">The use of a [single-threaded appartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="c488c-122">使用C++/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started)時，多執行緒的單元是預設值。</span><span class="sxs-lookup"><span data-stu-id="c488c-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="c488c-123">取得全像攝影的遠端 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="c488c-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="c488c-124">若要將 NuGet 套件新增至 Visual Studio 中的專案，必須執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="c488c-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="c488c-125">在 Visual Studio 中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="c488c-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="c488c-126">以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 套件 ...** ]</span><span class="sxs-lookup"><span data-stu-id="c488c-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="c488c-127">在出現的面板中，按一下 **[流覽]** ，然後搜尋「全像遠端處理」。</span><span class="sxs-lookup"><span data-stu-id="c488c-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="c488c-128">選取 [ **Microsoft 全息**]，並確定**挑選最新**的2.x 版，然後按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="c488c-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="c488c-129">如果出現 [**預覽**] 對話方塊，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="c488c-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="c488c-130">下一個出現的對話方塊是授權合約。</span><span class="sxs-lookup"><span data-stu-id="c488c-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="c488c-131">按一下 [**我接受**] 以接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="c488c-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="c488c-132">NuGet 套件中的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包含「全像」遠端處理所公開之 API 的詳細檔。</span><span class="sxs-lookup"><span data-stu-id="c488c-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="c488c-133">修改應用程式的 package.appxmanifest.xml</span><span class="sxs-lookup"><span data-stu-id="c488c-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="c488c-134">若要讓應用程式知道 NuGet 套件所新增的 AppRemoting，您必須在專案上執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c488c-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="c488c-135">在 方案總管以滑鼠右鍵按一下**package.appxmanifest.xml**檔案，然後選取 **開啟方式**...。</span><span class="sxs-lookup"><span data-stu-id="c488c-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="c488c-136">選取 [ **XML （文字）編輯器**]，然後按一下 [確定]</span><span class="sxs-lookup"><span data-stu-id="c488c-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="c488c-137">將下列幾行新增至檔案並儲存</span><span class="sxs-lookup"><span data-stu-id="c488c-137">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="c488c-138">建立播放者內容</span><span class="sxs-lookup"><span data-stu-id="c488c-138">Create the player context</span></span>

<span data-ttu-id="c488c-139">第一個步驟是應用程式應該建立播放機內容。</span><span class="sxs-lookup"><span data-stu-id="c488c-139">As a first step the application should create a player context.</span></span>

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
><span data-ttu-id="c488c-140">「全像」遠端處理的運作方式，是以遠端處理特定執行時間取代 Windows 中的 Windows Mixed Reality 執行時間。</span><span class="sxs-lookup"><span data-stu-id="c488c-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="c488c-141">這會在建立播放者內容期間完成。</span><span class="sxs-lookup"><span data-stu-id="c488c-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="c488c-142">因此，在建立播放程式內容之前，任何 Windows Mixed Reality API 上的呼叫可能會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="c488c-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="c488c-143">建議的方法是在與任何混合現實 API 互動之前，儘早建立播放者內容。</span><span class="sxs-lookup"><span data-stu-id="c488c-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="c488c-144">在使用建立或之後取得的物件呼叫 ```PlayerContext::Create()``` 之前，絕對不要透過任何 Windows Mixed Reality API 混合建立或取出的物件。</span><span class="sxs-lookup"><span data-stu-id="c488c-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="c488c-145">接下來，您可以藉由呼叫[HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)來建立 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="c488c-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="c488c-146">連接到主機</span><span class="sxs-lookup"><span data-stu-id="c488c-146">Connect to the host</span></span>

<span data-ttu-id="c488c-147">一旦播放機應用程式準備好呈現內容，就可以建立與主機的連接。</span><span class="sxs-lookup"><span data-stu-id="c488c-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="c488c-148">您可以透過下列其中一種方式來建立連接：</span><span class="sxs-lookup"><span data-stu-id="c488c-148">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="c488c-149">在 HoloLens 2 上執行的播放機應用程式會連接到主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="c488c-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="c488c-150">主機應用程式會連線到在 HoloLens 2 上執行的 player 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c488c-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="c488c-151">若要從 player 應用程式連線到主機，請在指定主機名稱和埠的 player 內容上呼叫 ```Connect``` 方法。</span><span class="sxs-lookup"><span data-stu-id="c488c-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="c488c-152">預設通訊埠為**8265**。</span><span class="sxs-lookup"><span data-stu-id="c488c-152">The default port is **8265**.</span></span>

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
><span data-ttu-id="c488c-153">如同任何C++/WinRT API ```Connect``` 可能會擲回需要處理的 WinRT：： hresult_error。</span><span class="sxs-lookup"><span data-stu-id="c488c-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="c488c-154">接聽 player 應用程式上的連入連線可以藉由呼叫 ```Listen``` 方法來完成。</span><span class="sxs-lookup"><span data-stu-id="c488c-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="c488c-155">在此呼叫期間，可以指定交握埠和傳輸埠。</span><span class="sxs-lookup"><span data-stu-id="c488c-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="c488c-156">交握埠會用於初始交握。</span><span class="sxs-lookup"><span data-stu-id="c488c-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="c488c-157">然後，資料會透過傳輸埠傳送。</span><span class="sxs-lookup"><span data-stu-id="c488c-157">The data is then send over the transport port.</span></span> <span data-ttu-id="c488c-158">預設會使用埠號碼**8265**和**8266** 。</span><span class="sxs-lookup"><span data-stu-id="c488c-158">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="c488c-159">處理連接相關的事件</span><span class="sxs-lookup"><span data-stu-id="c488c-159">Handling connection related events</span></span>

<span data-ttu-id="c488c-160">```PlayerContext``` 會公開三個事件來監視連線的狀態。</span><span class="sxs-lookup"><span data-stu-id="c488c-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="c488c-161">OnConnected：已成功建立與主機的連接時觸發。</span><span class="sxs-lookup"><span data-stu-id="c488c-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="c488c-162">OnDisconnected：如果已建立的連接已終止或無法建立連接，就會觸發。</span><span class="sxs-lookup"><span data-stu-id="c488c-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
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
><span data-ttu-id="c488c-163">可能的 ```ConnectionFailureReason``` 值記載[于 ```Microsoft.Holographic.AppRemoting.idl``` 檔案](#idl)中。</span><span class="sxs-lookup"><span data-stu-id="c488c-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="c488c-164">OnListening：接聽連入連線時，會啟動。</span><span class="sxs-lookup"><span data-stu-id="c488c-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="c488c-165">此外，您還可以使用播放機內容上的 ```ConnectionState``` 屬性來查詢連接狀態。</span><span class="sxs-lookup"><span data-stu-id="c488c-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="c488c-166">顯示遠端呈現的框架</span><span class="sxs-lookup"><span data-stu-id="c488c-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="c488c-167">若要顯示遠端呈現的內容，請在呈現[HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)時呼叫 ```PlayerContext::BlitRemoteFrame()```。</span><span class="sxs-lookup"><span data-stu-id="c488c-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="c488c-168">```BlitRemoteFrame()``` 需要將目前 HolographicFrame 的背景緩衝區系結為轉譯目標。</span><span class="sxs-lookup"><span data-stu-id="c488c-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="c488c-169">您可以透過[Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)屬性，從[HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)接收後端緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c488c-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="c488c-170">當呼叫時，```BlitRemoteFrame()``` 會將最新收到的框架從主應用程式複製到 HolographicFrame 的 BackBuffer。</span><span class="sxs-lookup"><span data-stu-id="c488c-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="c488c-171">此外，如果遠端應用程式在呈現遠端框架期間已指定焦點，則會設定焦點集合。</span><span class="sxs-lookup"><span data-stu-id="c488c-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="c488c-172">```PlayerContext::BlitRemoteFrame()``` 可能會覆寫目前框架的焦點。</span><span class="sxs-lookup"><span data-stu-id="c488c-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="c488c-173">若要指定回溯焦點點，請先呼叫[HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ，再 ```PlayerContext::BlitRemoteFrame()```。</span><span class="sxs-lookup"><span data-stu-id="c488c-173">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="c488c-174">若要覆寫遠端焦點，請在 ```PlayerContext::BlitRemoteFrame()```之後呼叫[HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 。</span><span class="sxs-lookup"><span data-stu-id="c488c-174">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="c488c-175">成功時，```BlitRemoteFrame()``` 會傳回 ```BlitResult::Success_Color```。</span><span class="sxs-lookup"><span data-stu-id="c488c-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="c488c-176">否則，它會傳回失敗原因：</span><span class="sxs-lookup"><span data-stu-id="c488c-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="c488c-177">```BlitResult::Failed_NoRemoteFrameAvailable```：失敗，因為沒有可用的遠端框架。</span><span class="sxs-lookup"><span data-stu-id="c488c-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="c488c-178">```BlitResult::Failed_NoCamera```：失敗，因為沒有任何相機存在。</span><span class="sxs-lookup"><span data-stu-id="c488c-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="c488c-179">```BlitResult::Failed_RemoteFrameTooOld```：失敗，因為遠端框架太舊（請參閱 PlayerCoNtext：： BlitRemoteFrameTimeout 屬性）。</span><span class="sxs-lookup"><span data-stu-id="c488c-179">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

## <span data-ttu-id="c488c-180">選擇性：設定 BlitRemoteFrameTimeout<a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="c488c-180">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="c488c-181">從版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援 ```PlayerContext::BlitRemoteFrameTimeout```。</span><span class="sxs-lookup"><span data-stu-id="c488c-181">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="c488c-182">如果沒有收到新的遠端框架，```PlayerContext::BlitRemoteFrameTimeout``` 屬性會指定遠端框架重複使用的時間量。</span><span class="sxs-lookup"><span data-stu-id="c488c-182">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="c488c-183">常見的使用案例是啟用 [BlitRemoteFrame 超時]，以在一段時間內未收到任何新畫面格時，顯示空白螢幕。</span><span class="sxs-lookup"><span data-stu-id="c488c-183">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="c488c-184">啟用時，```BlitRemoteFrame``` 方法的傳回型別也可以用來切換至本機呈現的回溯內容。</span><span class="sxs-lookup"><span data-stu-id="c488c-184">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="c488c-185">若要啟用超時，請將屬性值設定為等於或大於100毫秒的持續時間。</span><span class="sxs-lookup"><span data-stu-id="c488c-185">To enable the timeout, set the property value to a duration equal or greater than 100ms.</span></span> <span data-ttu-id="c488c-186">若要停用超時，請將屬性設定為零持續時間。</span><span class="sxs-lookup"><span data-stu-id="c488c-186">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="c488c-187">如果已啟用超時，而且沒有針對設定的持續時間接收到遠端畫面格，則 BlitRemoteFrame 將會失敗並傳回 ```Failed_RemoteFrameTooOld```，直到收到新的遠端畫面格為止。</span><span class="sxs-lookup"><span data-stu-id="c488c-187">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="c488c-188">選擇性：取得最後一個遠端框架的相關統計資料</span><span class="sxs-lookup"><span data-stu-id="c488c-188">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="c488c-189">若要診斷效能或網路問題，可以透過 ```PlayerContext::LastFrameStatistics``` 屬性來抓取最後一個遠端框架的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="c488c-189">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="c488c-190">在呼叫[HolographicFrame：:P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)期間，會更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="c488c-190">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="c488c-191">如需詳細資訊，請參閱 ```Microsoft.Holographic.AppRemoting.idl``` 檔案中的 ```PlayerFrameStatistics```[檔](#idl)。</span><span class="sxs-lookup"><span data-stu-id="c488c-191">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="c488c-192">選擇性：自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="c488c-192">Optional: Custom data channels</span></span>

<span data-ttu-id="c488c-193">自訂資料通道可以用來透過已建立的遠端連線傳送使用者資料。</span><span class="sxs-lookup"><span data-stu-id="c488c-193">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="c488c-194">如需詳細資訊，請參閱[自訂資料通道](holographic-remoting-custom-data-channels.md)。</span><span class="sxs-lookup"><span data-stu-id="c488c-194">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="c488c-195">請參閱</span><span class="sxs-lookup"><span data-stu-id="c488c-195">See Also</span></span>
* [<span data-ttu-id="c488c-196">撰寫全像的遠端主機應用程式</span><span class="sxs-lookup"><span data-stu-id="c488c-196">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="c488c-197">自訂全像攝影遠端資料通道</span><span class="sxs-lookup"><span data-stu-id="c488c-197">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="c488c-198">使用全像攝影遠端建立安全連線</span><span class="sxs-lookup"><span data-stu-id="c488c-198">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="c488c-199">全像攝影遠端疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="c488c-199">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="c488c-200">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="c488c-200">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="c488c-201">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="c488c-201">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
