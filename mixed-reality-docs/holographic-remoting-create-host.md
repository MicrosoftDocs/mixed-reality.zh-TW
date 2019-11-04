---
title: 撰寫全像的遠端主機應用程式
description: 藉由建立全像遠端主機應用程式遠端內容（在遠端電腦上轉譯），可以串流處理至 HoloLens 2。 本文說明如何達成此目的。
author: bethau
ms.author: bethau
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: e296e5847849bb87f76a7187c3f8ea36a1d681e1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434309"
---
# <a name="writing-a-holographic-remoting-host-app"></a><span data-ttu-id="4b404-105">撰寫全像的遠端主機應用程式</span><span class="sxs-lookup"><span data-stu-id="4b404-105">Writing a Holographic Remoting host app</span></span>

>[!IMPORTANT]
><span data-ttu-id="4b404-106">本檔說明如何建立 HoloLens 2 的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b404-106">This document describes the creation of a host application for HoloLens 2.</span></span> <span data-ttu-id="4b404-107">**HoloLens （第1代）** 的主機應用程式必須使用 NuGet套件1.x 版。</span><span class="sxs-lookup"><span data-stu-id="4b404-107">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="4b404-108">這表示針對 HoloLens 2 所撰寫的主機應用程式與 HoloLens 1 不相容，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="4b404-108">This implies that host applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="4b404-109">您可以在[這裡](add-holographic-remoting.md)找到 HoloLens 1 的檔。</span><span class="sxs-lookup"><span data-stu-id="4b404-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="4b404-110">藉由建立全像遠端主機應用程式，您可以將在遠端電腦上呈現的遠端內容串流至 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="4b404-110">By creating a Holographic Remoting host app remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="4b404-111">本文說明如何達成此目的。</span><span class="sxs-lookup"><span data-stu-id="4b404-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="4b404-112">此頁面上的所有程式碼和工作專案都可以在全像的[遠端範例 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。</span><span class="sxs-lookup"><span data-stu-id="4b404-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="4b404-113">全像攝影遠端功能可讓應用程式以在桌上型電腦或 UWP 裝置（例如 Xbox One）上裝載的全像 HoloLens 的內容作為目標，讓您可以存取更多系統資源，並讓您能夠將遠端[沉浸式視圖](app-views.md)整合到現有的桌上型電腦軟體。</span><span class="sxs-lookup"><span data-stu-id="4b404-113">Holographic remoting allows an app to target HoloLens 2 with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="4b404-114">遠端主機應用程式會接收來自 HoloLens 2 的輸入資料流程、轉譯虛擬沉浸式視圖中的內容，以及將內容框架串流回到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="4b404-114">A remoting host app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="4b404-115">連接是使用標準 Wi-fi 建立的。</span><span class="sxs-lookup"><span data-stu-id="4b404-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="4b404-116">全像攝影遠端會透過 NuGet 封包新增至桌面或 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b404-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="4b404-117">需要額外的程式碼來處理連接，並以沉浸式視圖呈現。</span><span class="sxs-lookup"><span data-stu-id="4b404-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="4b404-118">一般遠端連線的延遲時間會降到50毫秒。</span><span class="sxs-lookup"><span data-stu-id="4b404-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="4b404-119">Player 應用程式可以即時報告延遲。</span><span class="sxs-lookup"><span data-stu-id="4b404-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b404-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="4b404-120">Prerequisites</span></span>

<span data-ttu-id="4b404-121">良好的起點是以 Windows Mixed Reality API 為目標的可運作 DirectX 型桌面或 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b404-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="4b404-122">如需詳細資訊，請參閱[DirectX 開發總覽](directx-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4b404-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="4b404-123">全像攝影專案範本是不錯的起點。 [ C++ ](creating-a-holographic-directx-project.md)</span><span class="sxs-lookup"><span data-stu-id="4b404-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="4b404-124">任何使用全像攝影遠端的應用程式，都應該撰寫成使用[多執行緒的單元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="4b404-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="4b404-125">支援使用[單一執行緒的單元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)，但會導致在播放期間獲得最佳效能，而且可能會間斷情形。</span><span class="sxs-lookup"><span data-stu-id="4b404-125">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="4b404-126">使用C++/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started)時，多執行緒的單元是預設值。</span><span class="sxs-lookup"><span data-stu-id="4b404-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="4b404-127">取得全像攝影的遠端 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="4b404-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="4b404-128">若要將 NuGet 套件新增至 Visual Studio 中的專案，必須執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="4b404-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="4b404-129">在 Visual Studio 中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="4b404-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="4b404-130">以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 套件 ...** ]</span><span class="sxs-lookup"><span data-stu-id="4b404-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="4b404-131">在出現的面板中，按一下 **[流覽]** ，然後搜尋「全像遠端處理」。</span><span class="sxs-lookup"><span data-stu-id="4b404-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="4b404-132">選取 [ **Microsoft 全息**]，並確定**挑選最新**的2.x 版，然後按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="4b404-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="4b404-133">如果出現 [**預覽**] 對話方塊，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4b404-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="4b404-134">下一個出現的對話方塊是授權合約。</span><span class="sxs-lookup"><span data-stu-id="4b404-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="4b404-135">按一下 [**我接受**] 以接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="4b404-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="4b404-136">1\.x**版的**NuGet 套件仍然可供想要以 HoloLens 1 為目標的開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="4b404-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="4b404-137">如需詳細資訊，請參閱新增全像攝影[遠端（HoloLens （第1代））](add-holographic-remoting.md)。</span><span class="sxs-lookup"><span data-stu-id="4b404-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="4b404-138">建立遠端內容</span><span class="sxs-lookup"><span data-stu-id="4b404-138">Create the remote context</span></span>

<span data-ttu-id="4b404-139">第一個步驟是應用程式應該建立遠端內容。</span><span class="sxs-lookup"><span data-stu-id="4b404-139">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="4b404-140">「全像」遠端處理的運作方式，是以遠端處理特定執行時間取代 Windows 中的 Windows Mixed Reality 執行時間。</span><span class="sxs-lookup"><span data-stu-id="4b404-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="4b404-141">這會在建立遠端內容期間完成。</span><span class="sxs-lookup"><span data-stu-id="4b404-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="4b404-142">因此，在建立遠端內容之前，任何 Windows Mixed Reality API 上的呼叫都會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="4b404-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="4b404-143">建議的方法是在與任何混合現實 API 互動之前，儘早建立遠端內容。</span><span class="sxs-lookup"><span data-stu-id="4b404-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="4b404-144">在使用建立或之後抓取的物件呼叫 CreateRemoteCoNtext 之前，絕不會透過任何 Windows Mixed Reality API 混合建立或取出的物件。</span><span class="sxs-lookup"><span data-stu-id="4b404-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="4b404-145">接下來，必須建立全像攝影空間。</span><span class="sxs-lookup"><span data-stu-id="4b404-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="4b404-146">不需要指定 CoreWindow。</span><span class="sxs-lookup"><span data-stu-id="4b404-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="4b404-147">沒有 CoreWindow 的桌面應用程式可以直接傳遞 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="4b404-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="4b404-148">連接到裝置</span><span class="sxs-lookup"><span data-stu-id="4b404-148">Connect to the device</span></span>

<span data-ttu-id="4b404-149">一旦主機應用程式準備好呈現內容，就可以建立與裝置的連線。</span><span class="sxs-lookup"><span data-stu-id="4b404-149">Once the host app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="4b404-150">連接可以透過兩種方式的其中一種來完成。</span><span class="sxs-lookup"><span data-stu-id="4b404-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="4b404-151">主機應用程式會連接到在裝置上執行的播放程式。</span><span class="sxs-lookup"><span data-stu-id="4b404-151">The host app connects to the player running on the device.</span></span>
2) <span data-ttu-id="4b404-152">裝置上執行的播放程式會連接到主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b404-152">The player running on the device connects to the host app.</span></span>

<span data-ttu-id="4b404-153">若要建立從主機應用程式到 HoloLens 2 的連線，請在指定主機名稱和埠的遠端內容上呼叫 ```Connect``` 方法。</span><span class="sxs-lookup"><span data-stu-id="4b404-153">To establish a connection from the host app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="4b404-154">全像攝影遠端播放程式所使用的埠是**8265**。</span><span class="sxs-lookup"><span data-stu-id="4b404-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="4b404-155">如同任何C++/WinRT API ```Connect``` 可能會擲回需要處理的 WinRT：： hresult_error。</span><span class="sxs-lookup"><span data-stu-id="4b404-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="4b404-156">若要避免使用[ C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/)語言投射，可以包含位於全像攝影遠端 NuGet 封裝內的檔案 ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h```。</span><span class="sxs-lookup"><span data-stu-id="4b404-156">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="4b404-157">它包含基礎 COM 介面的宣告。</span><span class="sxs-lookup"><span data-stu-id="4b404-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="4b404-158">不過，建議C++使用/WinRT。</span><span class="sxs-lookup"><span data-stu-id="4b404-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="4b404-159">接聽主機應用程式上的連入連線，可以藉由呼叫 ```Listen``` 方法來完成。</span><span class="sxs-lookup"><span data-stu-id="4b404-159">Listening for incoming connections on the host app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="4b404-160">在此呼叫期間，可以指定交握埠和傳輸埠。</span><span class="sxs-lookup"><span data-stu-id="4b404-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="4b404-161">交握埠會用於初始交握。</span><span class="sxs-lookup"><span data-stu-id="4b404-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="4b404-162">然後，資料會透過傳輸埠傳送。</span><span class="sxs-lookup"><span data-stu-id="4b404-162">The data is then send over the transport port.</span></span> <span data-ttu-id="4b404-163">預設會使用**8265**和**8266** 。</span><span class="sxs-lookup"><span data-stu-id="4b404-163">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="4b404-164">NuGet 套件中的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包含「全像」遠端處理所公開之 API 的詳細檔。</span><span class="sxs-lookup"><span data-stu-id="4b404-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="4b404-165">處理遠端特定事件</span><span class="sxs-lookup"><span data-stu-id="4b404-165">Handling Remoting specific events</span></span>

<span data-ttu-id="4b404-166">遠端內容會公開三個重要的事件，以監視連接的狀態。</span><span class="sxs-lookup"><span data-stu-id="4b404-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="4b404-167">OnConnected：已成功建立與裝置的連線時觸發。</span><span class="sxs-lookup"><span data-stu-id="4b404-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="4b404-168">OnDisconnected：在已建立的連接已關閉或無法建立連接時觸發。</span><span class="sxs-lookup"><span data-stu-id="4b404-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="4b404-169">OnListening：接聽連入連線時，會啟動。</span><span class="sxs-lookup"><span data-stu-id="4b404-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="4b404-170">此外，您還可以使用遠端內容上的 ```ConnectionState``` 屬性來查詢連接狀態。</span><span class="sxs-lookup"><span data-stu-id="4b404-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="4b404-171">處理語音事件</span><span class="sxs-lookup"><span data-stu-id="4b404-171">Handling speech events</span></span>

<span data-ttu-id="4b404-172">使用遠端語音介面，可以向 HoloLens 2 註冊語音觸發程式，並讓它們遠端處理到主應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b404-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the host application.</span></span>

<span data-ttu-id="4b404-173">需要此額外成員才能追蹤遠端語音的狀態。</span><span class="sxs-lookup"><span data-stu-id="4b404-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="4b404-174">首先，必須抓取遠端語音介面。</span><span class="sxs-lookup"><span data-stu-id="4b404-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="4b404-175">您可以使用非同步 helper 方法，初始化遠端語音。</span><span class="sxs-lookup"><span data-stu-id="4b404-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="4b404-176">這應該會以非同步方式完成，因為初始化可能需要相當長的時間。</span><span class="sxs-lookup"><span data-stu-id="4b404-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="4b404-177">[使用/WinRT 的C++並行和非同步作業](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency)說明如何使用C++/winrt 撰寫非同步功能</span><span class="sxs-lookup"><span data-stu-id="4b404-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleHostMain> sampleHostMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleHostMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleHostMain = sampleHostMainWeak.lock())
            {
                sampleHostMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="4b404-178">有兩種方式可以指定要辨識的片語。</span><span class="sxs-lookup"><span data-stu-id="4b404-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="4b404-179">語音文法 xml 檔案中的規格。</span><span class="sxs-lookup"><span data-stu-id="4b404-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="4b404-180">如需詳細資訊，請參閱[如何建立基本 XML 文法](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14))。</span><span class="sxs-lookup"><span data-stu-id="4b404-180">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="4b404-181">藉由在字典向量內傳遞它們來指定 ```ApplyParameters```。</span><span class="sxs-lookup"><span data-stu-id="4b404-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="4b404-182">在 OnRecognizedSpeech 回呼內，可以處理的語音事件如下：</span><span class="sxs-lookup"><span data-stu-id="4b404-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

```cpp
void SampleHostMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="4b404-183">在本機預覽串流內容</span><span class="sxs-lookup"><span data-stu-id="4b404-183">Preview streamed content locally</span></span>

<span data-ttu-id="4b404-184">若要在傳送至裝置的主機應用程式中顯示相同的內容，可以使用遠端內容的 ```OnSendFrame``` 事件。</span><span class="sxs-lookup"><span data-stu-id="4b404-184">To display the same content in the host app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="4b404-185">每次全像攝影遠端程式庫將目前的框架傳送到遠端裝置時，就會觸發 ```OnSendFrame``` 事件。</span><span class="sxs-lookup"><span data-stu-id="4b404-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="4b404-186">這是接受內容並將它 array.blit 到桌面或 UWP 視窗的理想時機。</span><span class="sxs-lookup"><span data-stu-id="4b404-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="optional-custom-data-channels"></a><span data-ttu-id="4b404-187">選擇性：自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="4b404-187">Optional: Custom data channels</span></span>

<span data-ttu-id="4b404-188">自訂資料通道可以用來透過已建立的遠端連線傳送使用者資料。</span><span class="sxs-lookup"><span data-stu-id="4b404-188">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="4b404-189">如需詳細資訊，請參閱[自訂資料通道](holographic-remoting-custom-data-channels.md)。</span><span class="sxs-lookup"><span data-stu-id="4b404-189">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b404-190">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b404-190">See Also</span></span>
* [<span data-ttu-id="4b404-191">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="4b404-191">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="4b404-192">自訂全像攝影遠端資料通道</span><span class="sxs-lookup"><span data-stu-id="4b404-192">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="4b404-193">使用全像攝影遠端建立安全連線</span><span class="sxs-lookup"><span data-stu-id="4b404-193">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="4b404-194">全像攝影遠端疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="4b404-194">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="4b404-195">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="4b404-195">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="4b404-196">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="4b404-196">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
