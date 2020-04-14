---
title: 取得 HolographicSpace
description: 說明 HolographicSpace API，這是一種適用于全像攝影轉譯和空間輸入的核心概念。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HolographicSpace，CoreWindow，空間輸入，轉譯，交換鏈，全息框，更新迴圈，遊戲迴圈，參考框架，locatability，範例程式碼，逐步解說
ms.openlocfilehash: 76211c8a5394e2e296748253df4eac063841746c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277826"
---
# <a name="getting-a-holographicspace"></a>取得 HolographicSpace

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別是您進入全像世界的入口網站。 它會控制沉浸式轉譯、提供相機資料，並提供空間推理 Api 的存取權。 您將為 UWP 應用程式的<a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a>或 Win32 應用程式的 HWND 建立一個。

## <a name="set-up-the-holographic-space"></a>設定全像攝影空間

建立「全像攝影空間」物件是製作 Windows Mixed Reality 應用程式的第一步。 傳統的 Windows 應用程式會轉譯成針對其應用程式視圖的核心視窗所建立的 Direct3D 交換鏈。 此交換鏈會顯示在全像攝影 UI 中的一片平板電腦上。 若要讓您的應用程式觀賞全像2D 平板電腦，請為其核心視窗建立全像攝影空間，而不是交換鏈。 呈現這個全像攝影空間所建立的全息式框架，可讓您的應用程式進入全螢幕轉譯模式。

針對從全像「 [ *DirectX 11 應用程式（通用 Windows）」範本*開始](creating-a-holographic-directx-project.md)的**UWP 應用程式**，請在 AppView 的**SetWindow**方法中尋找此程式碼：

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

針對[從*BasicHologram* win32 範例開始](creating-a-holographic-directx-project.md#creating-a-win32-project)的**win32 應用程式**，請查看**app：： CreateWindowAndHolographicSpace** ，以取得如何建立 HWND，然後藉由建立相關聯的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>，將它轉換成沉浸式 HWND 的範例：
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

既然您已取得 UWP CoreWindow 或 Win32 HWND 的 HolographicSpace，就會使用該 HolographicSpace 來處理全像攝影相機、建立座標系統，以及進行全像攝影轉譯。 目前的全像攝影空間用於 DirectX 範本中的多個位置：
* **DeviceResources**類別需要從 HolographicSpace 物件取得一些資訊，才能建立 Direct3D 裝置。 這是與全像攝影顯示器相關聯的 DXGI 介面卡識別碼。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別會使用您應用程式的 Direct3D 11 裝置來建立和管理以裝置為基礎的資源，例如每個全像攝影攝影機的背面緩衝區。 如果您有興趣瞭解此函式在幕後的功能，您可以在 DeviceResources 中找到它。
* 函數**DeviceResources：： InitializeUsingHolographicSpace**示範如何藉由查閱 LUID 來取得介面卡，以及如何在未指定慣用介面卡時選擇預設介面卡。
* 應用程式的主要類別會使用**AppView：： SetWindow**或**App：： CreateWindowAndHolographicSpace**中的全像攝影空間來進行更新和呈現。

>[!NOTE]
>雖然下列各節提及的是來自範本的函式名稱，例如**AppView：： SetWindow** ，假設您是從全像攝影的 UWP 應用程式範本開始，您所看到的程式碼片段會在 UWP 和 Win32 應用程式中同樣適用。

接下來，我們將深入探討**SetHolographicSpace**在 AppMain 類別中負責處理的安裝程式。

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>訂閱攝影機事件、建立和移除相機資源

您的應用程式的全像攝影內容位於其全像攝影空間，並透過一或多個全像攝影相機來觀看，其代表場景上不同的觀點。 現在您已有全像攝影空間，可以接收全像攝影攝影機的資料。

您的應用程式必須藉由建立該相機特定的任何資源（例如，您的背景緩衝區呈現目標視圖）來回應**CameraAdded**事件。 您可以在**DeviceResources：： SetHolographicSpace**函式中看到此程式碼，該函式是由**AppView：： SetWindow**所呼叫，在應用程式建立任何全像攝影框架之前：

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

您的應用程式也必須釋放針對該攝影機所建立的資源，以回應**CameraRemoved**事件。

From **DeviceResources：： SetHolographicSpace**：

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

事件處理常式必須完成一些工作，才能讓全像攝影轉譯順暢地流動，讓您的應用程式能夠完全呈現。 如需詳細資訊，請閱讀程式碼和批註：您可以在主要類別中尋找**OnCameraAdded**和**OnCameraRemoved** ，以瞭解**DeviceResources**如何處理**m_cameraResources**對應。

現在，我們著重于 AppMain 和設定，讓您的應用程式知道全像攝影攝影機。 記住這一點之後，請務必記下下列兩個需求：

1. 針對**CameraAdded**事件處理常式，應用程式可以非同步方式工作，以完成建立資源並為新的全像攝影相機載入資產。 需要一個以上的框架來完成這項工作的應用程式應該會要求延遲，並在非同步載入後完成延遲;[PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)工作可用於執行非同步工作。 您的應用程式必須確定它已準備好在結束事件處理常式或完成延遲時立即呈現給該相機。 結束事件處理常式或完成延遲會告訴系統，您的應用程式現在已準備好接收包含該攝影機的全像攝影畫面。

2. 當應用程式收到**CameraRemoved**事件時，它必須釋放對後端緩衝區的所有參考，並立即結束函式。 這包括呈現目標視圖，以及任何其他可能持有[IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)參考的資源。 應用程式也必須確保背景緩衝區不會附加為轉譯目標，如**CameraResources：： ReleaseResourcesForBackBuffer**中所示。 為了協助加速作業，您的應用程式可以釋放後端緩衝區，然後啟動工作以非同步完成卸載該攝影機所需的任何其他工作。 全像攝影應用程式範本包含可用於此用途的 PPL 工作。

>[!NOTE]
>如果您想要判斷畫面上顯示的是新增或移除的相機，請使用**HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras)和[RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)屬性。

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>建立您的全像攝影內容的參考框架

您的應用程式內容必須位於[空間座標系統](coordinate-systems-in-directx.md)中，才能在 HolographicSpace 中呈現。 系統提供兩個主要的參考框架，您可以用來建立您的全息影像的座標系統。

Windows 全像攝影中有兩種參考框架：附加至裝置的參考框架，以及裝置在使用者環境中移動時仍維持固定的參考框架。 全像攝影應用程式範本預設會使用固定的參考框架;這是轉譯世界鎖定的全像投影的其中一個最簡單的方式。

固定的參考框架是設計用來在裝置的目前位置附近穩定位置。 這表示當裝置深入瞭解其周圍的空間時，與裝置之間的座標可能會與使用者的環境略有些許漂移。 有兩種方式可建立固定的參考框架：從[空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)取得座標系統，或使用預設<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。 如果您要建立沉浸式耳機的 Windows Mixed Reality 應用程式，建議的起點是[空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，這也會提供播放程式所磨損之沉浸式耳機功能的相關資訊。 在這裡，我們會示範如何使用預設<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。

空間定位器代表 Windows Mixed Reality 裝置，並追蹤裝置的動作，並提供可瞭解其位置相關的座標系統。

From **AppMain：： OnHolographicDisplayIsAvailableChanged**：

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

在應用程式啟動時，建立固定的參考框架一次。 這類似于定義全球座標系統，並在應用程式啟動時將原點放在裝置的位置。 此參考框架不會與裝置一起移動。

From **AppMain：： SetHolographicSpace**：

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

所有參考框架都會對齊，這表示 y 軸會指向使用者的環境。 由於 Windows 使用「右手式」座標系統，因此– Z 軸的方向與裝置在建立參考框架時所面臨的「正向」方向一致。

>[!NOTE]
>當您的應用程式需要精確地放置個別的全息影像時，請使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>將個別的全息影像錨定到真實世界中的位置。 例如，當使用者指出特別感的點時，請使用空間錨點。 錨點位置不會漂移，但可以調整。 根據預設，調整錨點時，會在更正發生後，將其位置簡化到接下來的幾個畫面。 視您的應用程式而定，當發生這種情況時，您可能會想要以不同的方式處理調整（例如，將其延後，直到全息全像看出來）。 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>屬性和<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件會啟用這些自訂。

## <a name="respond-to-locatability-changed-events"></a>回應 locatability 變更的事件

呈現世界鎖定的全像投影需要裝置能夠在世界各地尋找自己。 這可能不一定會因為環境條件而發生，因此，使用者可能會預期追蹤中斷的視覺指示。 此視覺指示必須使用附加至裝置的參考框架來轉譯，而不是從「固定」到「世界」。

您的應用程式可以要求在追蹤因任何原因而中斷時收到通知。 註冊 LocatabilityChanged 事件，以偵測裝置在世界中尋找自身的能力變更。 From **AppMain：： SetHolographicSpace：**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

然後使用此事件來判斷全息影像何時無法以靜止的方式呈現給世界。

## <a name="see-also"></a>另請參閱
* [DirectX 中的呈現](rendering-in-directx.md)
* [DirectX 中的座標系統](coordinate-systems-in-directx.md)
