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
# <a name="getting-a-holographicspace"></a>取得 HolographicSpace

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別是您的入口網站，進入全像攝影版的世界。 它控制沈浸式轉譯、 提供相機資料，並提供空間推理 Api 的存取。 您將建立一個用於您的 UWP 應用程式<a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a>或 Win32 應用程式的 HWND。

## <a name="set-up-the-holographic-space"></a>設定全像攝影版的空間

建立全像攝影版的空間物件是讓 Windows Mixed Reality 應用程式的第一個步驟。 傳統的 Windows 應用程式會轉譯為針對其應用程式檢視的 [核心] 視窗建立 Direct3D 交換鏈結。 在全像攝影版的 UI 中的 slate 就會顯示此交換鏈結。 若要讓您的應用程式檢視全像攝影版而不是 2D slate，建立一個全像攝影版的位置，讓其核心視窗，而不是交換鏈結。 呈現全像攝影版的畫面格所建立的這個全像攝影版的空間時，會將您的應用程式置入全螢幕呈現模式。

針對**UWP 應用程式**[從開始*全像攝影版的 DirectX 11 應用程式 (通用 Windows) 範本*](creating-a-holographic-directx-project.md)，在此程式碼看起來**SetWindow**在 [AppView.cpp 方法：

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

針對**Win32 應用程式**[從開始*BasicHologram* Win32 範例](creating-a-holographic-directx-project.md#creating-a-win32-project)，查看**App::CreateWindowAndHolographicSpace**的如何建立 HWND，然後將它轉換成沈浸式 HWND，藉由建立相關聯的範例<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:
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

既然您已取得 HolographicSpace 為您的 UWP CoreWindow 或 Win32 HWND，您將使用該 HolographicSpace 來處理全像攝影版的數位相機、 建立座標系統，並執行全像攝影版的轉譯。 DirectX 範本中的多個位置中，會使用目前的全像攝影版空間：
* **DeviceResources**類別需要 HolographicSpace 物件從取得一些資訊，才能建立 Direct3D 裝置。 這是全像攝影版顯示相關聯的 DXGI 配接器識別碼。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別會使用您的應用程式 Direct3D 11 裝置來建立和管理裝置為基礎的資源，例如背景緩衝區，針對每個全像攝影版的相機。 如果您想要查看此函式會在幕後，您會發現在 DeviceResources.cpp。
* 此函式**DeviceResources::InitializeUsingHolographicSpace**示範濆爧髍孮配接器藉由查閱 LUID-以及如何指定慣用的介面卡時，請選擇預設介面卡。
* 應用程式的主要類別會使用從全像攝影版的空間**AppView::SetWindow**或是**App::CreateWindowAndHolographicSpace**更新和轉譯。

>[!NOTE]
>下列各節會提到函式名稱，從範本時想**AppView::SetWindow** ，假設您開始從全像攝影版的 UWP 應用程式範本，您會看到的程式碼片段將會平均套用 UWP 和 Win32 應用程式。

接下來，我們將探討安裝程序， **SetHolographicSpace**負責 AppMain 類別中。

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>相機的事件訂閱、 建立以及移除相機資源

您的應用程式全像攝影版內容會位於其全像攝影版的空間，且會透過一或多個全像攝影版相機代表不同的檢視方塊集中在場景檢視。 既然您有全像攝影版的空間，可以接收資料的全像攝影版的相機。

您的應用程式需要回應**CameraAdded**事件所建立的任何資源，專屬於該數位相機，例如您的背景緩衝區的呈現目標檢視。 您可以看到這段程式碼**DeviceResources::SetHolographicSpace**函式，呼叫**AppView::SetWindow**應用程式會建立任何全像攝影版的畫面格之前：

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

您的應用程式也需要回應**CameraRemoved**釋放該數位相機所建立的資源的事件。

從**DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

事件處理常式必須完成一些工作，才能保持順暢，流動的全像攝影版轉譯，以便讓您的應用程式可呈現。 讀取的程式碼和註解的詳細資料： 您可以尋找**OnCameraAdded**並**OnCameraRemoved**在您的主要類別，以了解如何**m_cameraResources**對應是由處理**DeviceResources**。

現在，我們的重點 AppMain 和安裝程式，以啟用您的應用程式，了解全像攝影版的相機。 這一點，請務必記下下列兩項需求：

1. 針對**CameraAdded**事件處理常式，應用程式能夠以非同步方式來完成建立資源和載入新的全像攝影版相機的資產。 需要多個框架來完成這項工作的應用程式應該要求的延遲，並完成之後以非同步的方式; 載入的延遲[PPL 工作](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)可用來執行非同步工作。 您的應用程式必須確定它已準備好該觀景窗立即呈現，便會結束事件處理常式中，或在完成時的延遲。 結束事件處理常式，或完成延遲告知您的應用程式現在已準備好接收全像攝影版的畫面格，以包含該相機的系統。

2. 當應用程式收到**CameraRemoved**事件，它必須釋放背景緩衝區與結束的項目，此函式離開右的所有參考。 這包括的呈現目標檢視，以及任何其他資源，可能會佔據的參考[IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)。 應用程式也必須確定背景緩衝區未附加做為呈現目標，如中所示**CameraResources::ReleaseResourcesForBackBuffer**。 為了協助速度東西，您的應用程式可以釋放背景緩衝區，然後啟動工作以非同步方式完成，才能卸除該相機的任何其他工作。 全像攝影版的應用程式範本包含您可以使用針對此目的的 PPL 工作。

>[!NOTE]
>如果您想要判斷當加入或移除的相機上出現的畫面格，使用**HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras)並[RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)屬性。

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>建立參考框架的全像攝影版的內容

您的應用程式內容必須位於[空間座標系統](coordinate-systems-in-directx.md)HolographicSpace 中呈現。 系統會提供兩個主要的參考框架可用來建立您全像投影座標系統。

有兩種類型的 Windows 全像攝影版中的參考畫面格： 參考框架附加至裝置，並會保留不動，為裝置通過的使用者環境的參考畫面格。 預設; 的全像攝影版的應用程式範本會使用靜態參考框架這是其中一種最簡單的方式來呈現世界鎖定全像投影。

靜態參考框架專為穩定的裝置目前位置附近的位置。 這表示，允許更裝置座標的使用者環境而言稍有漂移，因為裝置會學習更多關於其周圍的空間。 若要建立靜態參考座標系的兩種方式： 取得座標系統[空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，或使用預設<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。 如果您要建立沉浸式耳機的 Windows Mixed Reality 應用程式，建議的起始點就[空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，這也會提供沉浸式耳機穿戴期間播放程式功能相關資訊。 在這裡，我們示範如何使用預設<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。

空間定位器代表 Windows Mixed Reality 裝置，並會追蹤裝置的動作，並提供可以了解相對於其位置的座標系統。

從**AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

應用程式啟動時，請建立靜態參考框架一次。 這是類似於定義全局座標系統中，放在裝置的位置，當應用程式啟動時的來源。 此參考框架不會移動與裝置。

從**AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

所有的參考框架是重力對齊時，表示 y 軸點 「 向上 」 的使用者環境而言。 因為 Windows 會使用 「 右手性 」 的座標系統，則會在與裝置面向參考畫面格建立時的"forward"方向一致 – z 軸的方向。

>[!NOTE]
>當您的應用程式需要個別全像投影的精確位置時，請使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>來錨定在個別的全像真實世界中的位置。 例如，使用空間的錨點，當使用者指出要特別有趣的點。 不進行漂移錨點位置，但它們可以進行調整。 根據預設，時機調整錨點，它可以減輕其位置原位透過下一步 的數個畫面格之後更正發生。 根據您的應用程式中，當發生這種情況您可能要以不同方式處理調整 （例如，延後到全像超出檢視）。 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>屬性並<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件可讓這些自訂項目。

## <a name="respond-to-locatability-changed-events"></a>回應 locatability 變更事件

呈現世界鎖定全像投影需要能夠找出本身的世界中的裝置。 這可能不可能會因為環境的條件，如果是的話，使用者可能會預期追蹤中斷時間的視覺指示。 必須使用附加至裝置，而不是固定的世界參考框架呈現此視覺化指示。

您的應用程式可以要求將追蹤因任何原因中斷時收到通知。 註冊 LocatabilityChanged 事件，偵測何時要本身位於全球資訊變更裝置的能力。 從**AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

然後使用這個事件來判斷何時無法轉譯靜態世界全像投影。

## <a name="see-also"></a>另請參閱
* [在 DirectX 中轉譯](rendering-in-directx.md)
* [DirectX 中的座標系統](coordinate-systems-in-directx.md)
