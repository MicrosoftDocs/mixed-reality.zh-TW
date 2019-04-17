---
title: 取得 HolographicSpace
description: 說明 HolographicSpace API，而是全像攝影版的轉譯和空間輸入的核心概念。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality HolographicSpace、 CoreWindow，空間輸入、 轉譯、 交換鏈結、 全像攝影版的框架，更新迴圈、 遊戲迴圈、 參考架構、 locatability、 範例程式碼、 逐步解說
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597118"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="332c7-104">取得 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="332c7-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="332c7-105"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別是您的入口網站，進入全像攝影版的世界。</span><span class="sxs-lookup"><span data-stu-id="332c7-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="332c7-106">它控制沈浸式轉譯、 提供相機資料，並提供空間推理 Api 的存取。</span><span class="sxs-lookup"><span data-stu-id="332c7-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="332c7-107">您將建立一個用於您的 UWP 應用程式<a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a>或 Win32 應用程式的 HWND。</span><span class="sxs-lookup"><span data-stu-id="332c7-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="332c7-108">設定全像攝影版的空間</span><span class="sxs-lookup"><span data-stu-id="332c7-108">Set up the holographic space</span></span>

<span data-ttu-id="332c7-109">建立全像攝影版的空間物件是讓 Windows Mixed Reality 應用程式的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="332c7-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="332c7-110">傳統的 Windows 應用程式會轉譯為針對其應用程式檢視的 [核心] 視窗建立 Direct3D 交換鏈結。</span><span class="sxs-lookup"><span data-stu-id="332c7-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="332c7-111">在全像攝影版的 UI 中的 slate 就會顯示此交換鏈結。</span><span class="sxs-lookup"><span data-stu-id="332c7-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="332c7-112">若要讓您的應用程式檢視全像攝影版而不是 2D slate，建立一個全像攝影版的位置，讓其核心視窗，而不是交換鏈結。</span><span class="sxs-lookup"><span data-stu-id="332c7-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="332c7-113">呈現全像攝影版的畫面格所建立的這個全像攝影版的空間時，會將您的應用程式置入全螢幕呈現模式。</span><span class="sxs-lookup"><span data-stu-id="332c7-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="332c7-114">針對**UWP 應用程式**[從開始*全像攝影版的 DirectX 11 應用程式 (通用 Windows) 範本*](creating-a-holographic-directx-project.md)，在此程式碼看起來**SetWindow**在 [AppView.cpp 方法：</span><span class="sxs-lookup"><span data-stu-id="332c7-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="332c7-115">針對**Win32 應用程式**[從開始*BasicHologram* Win32 範例](creating-a-holographic-directx-project.md#creating-a-win32-project)，查看**App::CreateWindowAndHolographicSpace**的如何建立 HWND，然後將它轉換成沈浸式 HWND，藉由建立相關聯的範例<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="332c7-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="332c7-116">既然您已取得 HolographicSpace 為您的 UWP CoreWindow 或 Win32 HWND，您將使用該 HolographicSpace 來處理全像攝影版的數位相機、 建立座標系統，並執行全像攝影版的轉譯。</span><span class="sxs-lookup"><span data-stu-id="332c7-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="332c7-117">DirectX 範本中的多個位置中，會使用目前的全像攝影版空間：</span><span class="sxs-lookup"><span data-stu-id="332c7-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="332c7-118">**DeviceResources**類別需要 HolographicSpace 物件從取得一些資訊，才能建立 Direct3D 裝置。</span><span class="sxs-lookup"><span data-stu-id="332c7-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="332c7-119">這是全像攝影版顯示相關聯的 DXGI 配接器識別碼。</span><span class="sxs-lookup"><span data-stu-id="332c7-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="332c7-120"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別會使用您的應用程式 Direct3D 11 裝置來建立和管理裝置為基礎的資源，例如背景緩衝區，針對每個全像攝影版的相機。</span><span class="sxs-lookup"><span data-stu-id="332c7-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="332c7-121">如果您想要查看此函式會在幕後，您會發現在 DeviceResources.cpp。</span><span class="sxs-lookup"><span data-stu-id="332c7-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="332c7-122">此函式**DeviceResources::InitializeUsingHolographicSpace**示範濆爧髍孮配接器藉由查閱 LUID-以及如何指定慣用的介面卡時，請選擇預設介面卡。</span><span class="sxs-lookup"><span data-stu-id="332c7-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="332c7-123">應用程式的主要類別會使用從全像攝影版的空間**AppView::SetWindow**或是**App::CreateWindowAndHolographicSpace**更新和轉譯。</span><span class="sxs-lookup"><span data-stu-id="332c7-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="332c7-124">下列各節會提到函式名稱，從範本時想**AppView::SetWindow** ，假設您開始從全像攝影版的 UWP 應用程式範本，您會看到的程式碼片段將會平均套用 UWP 和 Win32 應用程式。</span><span class="sxs-lookup"><span data-stu-id="332c7-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="332c7-125">接下來，我們將探討安裝程序， **SetHolographicSpace**負責 AppMain 類別中。</span><span class="sxs-lookup"><span data-stu-id="332c7-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="332c7-126">相機的事件訂閱、 建立以及移除相機資源</span><span class="sxs-lookup"><span data-stu-id="332c7-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="332c7-127">您的應用程式全像攝影版內容會位於其全像攝影版的空間，且會透過一或多個全像攝影版相機代表不同的檢視方塊集中在場景檢視。</span><span class="sxs-lookup"><span data-stu-id="332c7-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="332c7-128">既然您有全像攝影版的空間，可以接收資料的全像攝影版的相機。</span><span class="sxs-lookup"><span data-stu-id="332c7-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="332c7-129">您的應用程式需要回應**CameraAdded**事件所建立的任何資源，專屬於該數位相機，例如您的背景緩衝區的呈現目標檢視。</span><span class="sxs-lookup"><span data-stu-id="332c7-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="332c7-130">您可以看到這段程式碼**DeviceResources::SetHolographicSpace**函式，呼叫**AppView::SetWindow**應用程式會建立任何全像攝影版的畫面格之前：</span><span class="sxs-lookup"><span data-stu-id="332c7-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="332c7-131">您的應用程式也需要回應**CameraRemoved**釋放該數位相機所建立的資源的事件。</span><span class="sxs-lookup"><span data-stu-id="332c7-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="332c7-132">從**DeviceResources::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="332c7-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="332c7-133">事件處理常式必須完成一些工作，才能保持順暢，流動的全像攝影版轉譯，以便讓您的應用程式可呈現。</span><span class="sxs-lookup"><span data-stu-id="332c7-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="332c7-134">讀取的程式碼和註解的詳細資料： 您可以尋找**OnCameraAdded**並**OnCameraRemoved**在您的主要類別，以了解如何**m_cameraResources**對應是由處理**DeviceResources**。</span><span class="sxs-lookup"><span data-stu-id="332c7-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="332c7-135">現在，我們的重點 AppMain 和安裝程式，以啟用您的應用程式，了解全像攝影版的相機。</span><span class="sxs-lookup"><span data-stu-id="332c7-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="332c7-136">這一點，請務必記下下列兩項需求：</span><span class="sxs-lookup"><span data-stu-id="332c7-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="332c7-137">針對**CameraAdded**事件處理常式，應用程式能夠以非同步方式來完成建立資源和載入新的全像攝影版相機的資產。</span><span class="sxs-lookup"><span data-stu-id="332c7-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="332c7-138">需要多個框架來完成這項工作的應用程式應該要求的延遲，並完成之後以非同步的方式; 載入的延遲[PPL 工作](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)可用來執行非同步工作。</span><span class="sxs-lookup"><span data-stu-id="332c7-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="332c7-139">您的應用程式必須確定它已準備好該觀景窗立即呈現，便會結束事件處理常式中，或在完成時的延遲。</span><span class="sxs-lookup"><span data-stu-id="332c7-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="332c7-140">結束事件處理常式，或完成延遲告知您的應用程式現在已準備好接收全像攝影版的畫面格，以包含該相機的系統。</span><span class="sxs-lookup"><span data-stu-id="332c7-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="332c7-141">當應用程式收到**CameraRemoved**事件，它必須釋放背景緩衝區與結束的項目，此函式離開右的所有參考。</span><span class="sxs-lookup"><span data-stu-id="332c7-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="332c7-142">這包括的呈現目標檢視，以及任何其他資源，可能會佔據的參考[IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)。</span><span class="sxs-lookup"><span data-stu-id="332c7-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="332c7-143">應用程式也必須確定背景緩衝區未附加做為呈現目標，如中所示**CameraResources::ReleaseResourcesForBackBuffer**。</span><span class="sxs-lookup"><span data-stu-id="332c7-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="332c7-144">為了協助速度東西，您的應用程式可以釋放背景緩衝區，然後啟動工作以非同步方式完成，才能卸除該相機的任何其他工作。</span><span class="sxs-lookup"><span data-stu-id="332c7-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="332c7-145">全像攝影版的應用程式範本包含您可以使用針對此目的的 PPL 工作。</span><span class="sxs-lookup"><span data-stu-id="332c7-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="332c7-146">如果您想要判斷當加入或移除的相機上出現的畫面格，使用**HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras)並[RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)屬性。</span><span class="sxs-lookup"><span data-stu-id="332c7-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="332c7-147">建立參考框架的全像攝影版的內容</span><span class="sxs-lookup"><span data-stu-id="332c7-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="332c7-148">您的應用程式內容必須位於[空間座標系統](coordinate-systems-in-directx.md)HolographicSpace 中呈現。</span><span class="sxs-lookup"><span data-stu-id="332c7-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="332c7-149">系統會提供兩個主要的參考框架可用來建立您全像投影座標系統。</span><span class="sxs-lookup"><span data-stu-id="332c7-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="332c7-150">有兩種類型的 Windows 全像攝影版中的參考畫面格： 參考框架附加至裝置，並會保留不動，為裝置通過的使用者環境的參考畫面格。</span><span class="sxs-lookup"><span data-stu-id="332c7-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="332c7-151">預設; 的全像攝影版的應用程式範本會使用靜態參考框架這是其中一種最簡單的方式來呈現世界鎖定全像投影。</span><span class="sxs-lookup"><span data-stu-id="332c7-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="332c7-152">靜態參考框架專為穩定的裝置目前位置附近的位置。</span><span class="sxs-lookup"><span data-stu-id="332c7-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="332c7-153">這表示，允許更裝置座標的使用者環境而言稍有漂移，因為裝置會學習更多關於其周圍的空間。</span><span class="sxs-lookup"><span data-stu-id="332c7-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="332c7-154">若要建立靜態參考座標系的兩種方式： 取得座標系統[空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，或使用預設<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。</span><span class="sxs-lookup"><span data-stu-id="332c7-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="332c7-155">如果您要建立沉浸式耳機的 Windows Mixed Reality 應用程式，建議的起始點就[空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，這也會提供沉浸式耳機穿戴期間播放程式功能相關資訊。</span><span class="sxs-lookup"><span data-stu-id="332c7-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="332c7-156">在這裡，我們示範如何使用預設<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。</span><span class="sxs-lookup"><span data-stu-id="332c7-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="332c7-157">空間定位器代表 Windows Mixed Reality 裝置，並會追蹤裝置的動作，並提供可以了解相對於其位置的座標系統。</span><span class="sxs-lookup"><span data-stu-id="332c7-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="332c7-158">從**AppMain::OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="332c7-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="332c7-159">應用程式啟動時，請建立靜態參考框架一次。</span><span class="sxs-lookup"><span data-stu-id="332c7-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="332c7-160">這是類似於定義全局座標系統中，放在裝置的位置，當應用程式啟動時的來源。</span><span class="sxs-lookup"><span data-stu-id="332c7-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="332c7-161">此參考框架不會移動與裝置。</span><span class="sxs-lookup"><span data-stu-id="332c7-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="332c7-162">從**AppMain::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="332c7-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="332c7-163">所有的參考框架是重力對齊時，表示 y 軸點 「 向上 」 的使用者環境而言。</span><span class="sxs-lookup"><span data-stu-id="332c7-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="332c7-164">因為 Windows 會使用 「 右手性 」 的座標系統，則會在與裝置面向參考畫面格建立時的"forward"方向一致 – z 軸的方向。</span><span class="sxs-lookup"><span data-stu-id="332c7-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="332c7-165">當您的應用程式需要個別全像投影的精確位置時，請使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>來錨定在個別的全像真實世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="332c7-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="332c7-166">例如，使用空間的錨點，當使用者指出要特別有趣的點。</span><span class="sxs-lookup"><span data-stu-id="332c7-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="332c7-167">不進行漂移錨點位置，但它們可以進行調整。</span><span class="sxs-lookup"><span data-stu-id="332c7-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="332c7-168">根據預設，時機調整錨點，它可以減輕其位置原位透過下一步 的數個畫面格之後更正發生。</span><span class="sxs-lookup"><span data-stu-id="332c7-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="332c7-169">根據您的應用程式中，當發生這種情況您可能要以不同方式處理調整 （例如，延後到全像超出檢視）。</span><span class="sxs-lookup"><span data-stu-id="332c7-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="332c7-170"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>屬性並<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件可讓這些自訂項目。</span><span class="sxs-lookup"><span data-stu-id="332c7-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="332c7-171">回應 locatability 變更事件</span><span class="sxs-lookup"><span data-stu-id="332c7-171">Respond to locatability changed events</span></span>

<span data-ttu-id="332c7-172">呈現世界鎖定全像投影需要能夠找出本身的世界中的裝置。</span><span class="sxs-lookup"><span data-stu-id="332c7-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="332c7-173">這可能不可能會因為環境的條件，如果是的話，使用者可能會預期追蹤中斷時間的視覺指示。</span><span class="sxs-lookup"><span data-stu-id="332c7-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="332c7-174">必須使用附加至裝置，而不是固定的世界參考框架呈現此視覺化指示。</span><span class="sxs-lookup"><span data-stu-id="332c7-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="332c7-175">您的應用程式可以要求將追蹤因任何原因中斷時收到通知。</span><span class="sxs-lookup"><span data-stu-id="332c7-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="332c7-176">註冊 LocatabilityChanged 事件，偵測何時要本身位於全球資訊變更裝置的能力。</span><span class="sxs-lookup"><span data-stu-id="332c7-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="332c7-177">從**AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="332c7-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="332c7-178">然後使用這個事件來判斷何時無法轉譯靜態世界全像投影。</span><span class="sxs-lookup"><span data-stu-id="332c7-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="332c7-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="332c7-179">See also</span></span>
* [<span data-ttu-id="332c7-180">在 DirectX 中轉譯</span><span class="sxs-lookup"><span data-stu-id="332c7-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="332c7-181">DirectX 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="332c7-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
