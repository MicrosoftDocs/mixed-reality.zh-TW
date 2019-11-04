---
title: 執行3D 應用程式啟動器（UWP 應用程式）
description: 如何建立適用于 Windows Mixed Reality UWP 應用程式和遊戲的3D 應用程式啟動器和標誌（透過 Microsoft Store 散發），包括 HoloLens 和沉浸式（VR）耳機。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D，標誌，圖示，模型，啟動器，3D 啟動器，磚，即時 cube，深層連結，secondarytile，次要磚，UWP
ms.openlocfilehash: be47b590e4fd1a847ac47d9cfbcbe824c544dd59
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438012"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="992f2-104">執行3D 應用程式啟動器（UWP 應用程式）</span><span class="sxs-lookup"><span data-stu-id="992f2-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="992f2-105">這項功能已新增為沉浸式耳機的2017秋季建立者更新（RS3）的一部分，且 HoloLens 支援 Windows 10 4 月2018更新。</span><span class="sxs-lookup"><span data-stu-id="992f2-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="992f2-106">請確定您的應用程式是以10.0.16299 的版本為目標，而不是以沉浸式頭戴式耳機和10.0.17125 在 HoloLens 上的 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="992f2-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="992f2-107">您可以在[這裡](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="992f2-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="992f2-108">[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。</span><span class="sxs-lookup"><span data-stu-id="992f2-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="992f2-109">建立適用于 Windows Mixed Reality 的 UWP 應用程式時，根據預設，應用程式會以其應用程式的標誌，以2D 平板的形式啟動。</span><span class="sxs-lookup"><span data-stu-id="992f2-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="992f2-110">在開發 Windows Mixed Reality 的經驗時，可以選擇性地定義3D 啟動器以覆寫應用程式的預設2D 啟動器。</span><span class="sxs-lookup"><span data-stu-id="992f2-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="992f2-111">一般而言，建議使用3D 啟動器來啟動沉浸式應用程式，讓使用者離開 Windows Mixed Reality home，而當應用程式就地啟用時，偏好使用預設的2D 啟動器。</span><span class="sxs-lookup"><span data-stu-id="992f2-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="992f2-112">您也可以建立[3d 的深層連結（secondaryTile）](#3d-deep-links-secondarytiles) ，做為 2d UWP 應用程式中內容的3d 啟動器。</span><span class="sxs-lookup"><span data-stu-id="992f2-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="992f2-113">3D 應用程式啟動器建立進程</span><span class="sxs-lookup"><span data-stu-id="992f2-113">3D app launcher creation process</span></span>

<span data-ttu-id="992f2-114">建立3D 應用程式啟動器有3個步驟：</span><span class="sxs-lookup"><span data-stu-id="992f2-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="992f2-115">設計和 concepting</span><span class="sxs-lookup"><span data-stu-id="992f2-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="992f2-116">模型化和匯出</span><span class="sxs-lookup"><span data-stu-id="992f2-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="992f2-117">將它整合到您的應用程式（本文）</span><span class="sxs-lookup"><span data-stu-id="992f2-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="992f2-118">要做為應用程式之啟動器使用的3D 資產，應使用[Windows Mixed Reality 撰寫指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)來確保相容性。</span><span class="sxs-lookup"><span data-stu-id="992f2-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="992f2-119">無法符合此撰寫規格的資產將不會在 Windows Mixed Reality 首頁中轉譯。</span><span class="sxs-lookup"><span data-stu-id="992f2-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="992f2-120">設定3D 啟動程式</span><span class="sxs-lookup"><span data-stu-id="992f2-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="992f2-121">在 Visual Studio 中建立新的專案時，它會建立一個顯示 app 名稱和標誌的簡單預設磚。</span><span class="sxs-lookup"><span data-stu-id="992f2-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="992f2-122">若要以自訂3D 模型取代此2D 標記法，請編輯應用程式的應用程式資訊清單，以將 "MixedRealityModel" 元素納入為預設磚定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="992f2-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="992f2-123">若要還原為2D 啟動器，請直接從資訊清單中移除 MixedRealityModel 定義。</span><span class="sxs-lookup"><span data-stu-id="992f2-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="992f2-124">XML</span><span class="sxs-lookup"><span data-stu-id="992f2-124">XML</span></span>

<span data-ttu-id="992f2-125">首先，在您目前的專案中找出應用程式套件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="992f2-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="992f2-126">根據預設，資訊清單會命名為 package.appxmanifest.xml。</span><span class="sxs-lookup"><span data-stu-id="992f2-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="992f2-127">如果您使用 Visual Studio，請以滑鼠右鍵按一下方案檢視器中的資訊清單，然後選取 [ **View source** ] 以開啟 xml 進行編輯。</span><span class="sxs-lookup"><span data-stu-id="992f2-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="992f2-128">在資訊清單的頂端，新增 uap5 架構，並將它包含為可忽略的命名空間：</span><span class="sxs-lookup"><span data-stu-id="992f2-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="992f2-129">接下來，在應用程式的預設磚中指定 "MixedRealityModel"：</span><span class="sxs-lookup"><span data-stu-id="992f2-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="992f2-130">MixedRealityModel 元素會接受指向儲存在應用程式套件中之3D 資產的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="992f2-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="992f2-131">目前只支援使用 glb 檔案格式所提供的3D 模型，並根據[Windows Mixed Reality 3d 資產撰寫指示](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)來撰寫。</span><span class="sxs-lookup"><span data-stu-id="992f2-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="992f2-132">資產必須儲存在應用程式套件中，而且目前不支援動畫。</span><span class="sxs-lookup"><span data-stu-id="992f2-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="992f2-133">如果 "Path" 參數保留空白，Windows 將會顯示2D 平板電腦，而不是3D 啟動程式。</span><span class="sxs-lookup"><span data-stu-id="992f2-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="992f2-134">**注意：** 在建立並執行您的應用程式之前，必須先將 glb 資產標記為您組建設定中的「內容」。</span><span class="sxs-lookup"><span data-stu-id="992f2-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="992f2-135">![在您的方案 explorer 中選取 glb，並使用 [屬性] 區段，將其標示為 [組建設定] 中的 [內容]](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="992f2-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="992f2-136">*在 [方案瀏覽器] 中選取 glb，然後使用 [屬性] 區段，將其標示為 [內容] （在 [組建設定] 中）*</span><span class="sxs-lookup"><span data-stu-id="992f2-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="992f2-137">週框方塊</span><span class="sxs-lookup"><span data-stu-id="992f2-137">Bounding box</span></span>

<span data-ttu-id="992f2-138">周框方塊可以用來選擇性地在物件周圍加入額外的緩衝區區域。</span><span class="sxs-lookup"><span data-stu-id="992f2-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="992f2-139">周框方塊是使用中心點和範圍來指定，其表示從周框方塊中央到其邊緣沿著每個軸的距離。</span><span class="sxs-lookup"><span data-stu-id="992f2-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="992f2-140">周框方塊的單位可以對應到1個單位 = 1 個計量。</span><span class="sxs-lookup"><span data-stu-id="992f2-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="992f2-141">如果未提供周框方塊，則會自動將一個方塊調整為物件的網格。</span><span class="sxs-lookup"><span data-stu-id="992f2-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="992f2-142">如果提供的周框方塊小於模型，則會調整大小以符合網格。</span><span class="sxs-lookup"><span data-stu-id="992f2-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="992f2-143">周框方塊屬性的支援將隨附于 Windows RS4 update，做為 MixedRealityModel 元素上的屬性。</span><span class="sxs-lookup"><span data-stu-id="992f2-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="992f2-144">若要先在應用程式資訊清單頂端定義周框方塊，請新增 uap6 架構，並將其包含為可忽略的命名空間：</span><span class="sxs-lookup"><span data-stu-id="992f2-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="https://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="992f2-145">接下來，在 MixedRealityModel 上設定 SpatialBoundingBox 屬性以定義周框方塊：</span><span class="sxs-lookup"><span data-stu-id="992f2-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="992f2-146">使用 Unity</span><span class="sxs-lookup"><span data-stu-id="992f2-146">Using Unity</span></span>

<span data-ttu-id="992f2-147">使用 Unity 時，必須在 Visual Studio 中建立和開啟專案，才能編輯應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="992f2-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="992f2-148">從 Unity 建立和部署新的 Visual Studio 方案時，必須在資訊清單中重新定義3D 啟動程式。</span><span class="sxs-lookup"><span data-stu-id="992f2-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="992f2-149">3D 深層連結（secondaryTiles）</span><span class="sxs-lookup"><span data-stu-id="992f2-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="992f2-150">這項功能已新增為沉浸（VR）耳機的2017秋季建立者更新（RS3）的一部分，並作為 HoloLens 2018 年4月更新（RS4）的一部分。</span><span class="sxs-lookup"><span data-stu-id="992f2-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="992f2-151">請確定您的應用程式是以10.0.16299 的版本為目標，而不是以沉浸式（VR）耳機和 10.0.17125 on HoloLens 的 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="992f2-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="992f2-152">您可以在[這裡](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="992f2-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="992f2-153">3D 深層連結（secondaryTiles）僅適用于 2D UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="992f2-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="992f2-154">不過，您可以建立[3d 應用程式啟動器](implementing-3d-app-launchers.md)，從 Windows Mixed Reality home 啟動專屬的應用程式。</span><span class="sxs-lookup"><span data-stu-id="992f2-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="992f2-155">藉由新增將3D 模型從您的應用程式放入[Windows Mixed reality 首頁](navigating-the-windows-mixed-reality-home.md)，做為2d 應用程式中內容的深層連結，就像 windows Start 上的[2d 次要磚](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)一樣，您可以增強2D 應用程式的 windows mixed reality 功能下拉式功能表.</span><span class="sxs-lookup"><span data-stu-id="992f2-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="992f2-156">例如，您可以建立可直接連結至360相片檢視器應用程式的360° photospheres，或讓使用者從一組資產集合中開啟3D 內容，這些資產會開啟有關作者的詳細資料頁面。</span><span class="sxs-lookup"><span data-stu-id="992f2-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="992f2-157">這些只是使用3D 內容擴充2D 應用程式功能的幾種方式。</span><span class="sxs-lookup"><span data-stu-id="992f2-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="992f2-158">建立 3D "secondaryTile"</span><span class="sxs-lookup"><span data-stu-id="992f2-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="992f2-159">您可以在建立時定義混合現實模型，以使用 "secondaryTiles" 從應用程式中放置3D 內容。</span><span class="sxs-lookup"><span data-stu-id="992f2-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="992f2-160">混合現實模型的建立方式是參考應用程式套件中的3D 資產，並選擇性地定義周框方塊。</span><span class="sxs-lookup"><span data-stu-id="992f2-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="992f2-161">目前不支援從獨佔視圖中建立 "secondaryTiles"。</span><span class="sxs-lookup"><span data-stu-id="992f2-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="992f2-162">週框方塊</span><span class="sxs-lookup"><span data-stu-id="992f2-162">Bounding box</span></span>

<span data-ttu-id="992f2-163">周框方塊可以用來在物件周圍加入額外的緩衝區區域。</span><span class="sxs-lookup"><span data-stu-id="992f2-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="992f2-164">周框方塊是使用中心點和範圍來指定，其表示從周框方塊中央到其邊緣沿著每個軸的距離。</span><span class="sxs-lookup"><span data-stu-id="992f2-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="992f2-165">周框方塊的單位可以對應到1個單位 = 1 個計量。</span><span class="sxs-lookup"><span data-stu-id="992f2-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="992f2-166">如果未提供周框方塊，則會自動將一個方塊調整為物件的網格。</span><span class="sxs-lookup"><span data-stu-id="992f2-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="992f2-167">如果提供的周框方塊小於模型，則會調整大小以符合網格。</span><span class="sxs-lookup"><span data-stu-id="992f2-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="992f2-168">啟用行為</span><span class="sxs-lookup"><span data-stu-id="992f2-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="992f2-169">這項功能將受到 Windows RS4 update 的支援。</span><span class="sxs-lookup"><span data-stu-id="992f2-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="992f2-170">如果您打算使用這項功能，請確定您的應用程式是以大於或等於10.0.17125 的 Windows SDK 版本為目標</span><span class="sxs-lookup"><span data-stu-id="992f2-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="992f2-171">您可以定義 3D secondaryTile 的啟用行為，以控制當使用者選取它時的回應方式。</span><span class="sxs-lookup"><span data-stu-id="992f2-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="992f2-172">這可以用來將3D 物件放在 purley 資訊性或裝飾的混合現實首頁中。</span><span class="sxs-lookup"><span data-stu-id="992f2-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="992f2-173">支援下列啟用行為類型：</span><span class="sxs-lookup"><span data-stu-id="992f2-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="992f2-174">預設值：當使用者選取 3D secondaryTile 時，應用程式就會啟用</span><span class="sxs-lookup"><span data-stu-id="992f2-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="992f2-175">無：當使用者選取 3D secondaryTile 時，不會發生任何事，也不會啟用應用程式。</span><span class="sxs-lookup"><span data-stu-id="992f2-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="992f2-176">取得和更新現有的 "secondaryTile"</span><span class="sxs-lookup"><span data-stu-id="992f2-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="992f2-177">開發人員可以取回其現有的次要磚清單，其中包括先前指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="992f2-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="992f2-178">它們也可以藉由變更值，然後呼叫 UpdateAsync （）來更新屬性。</span><span class="sxs-lookup"><span data-stu-id="992f2-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="992f2-179">正在檢查使用者是否在 Windows Mixed Reality 中</span><span class="sxs-lookup"><span data-stu-id="992f2-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="992f2-180">只有當視圖在 Windows Mixed Reality 耳機中顯示時，才能建立3D 深層連結（secondaryTiles）。</span><span class="sxs-lookup"><span data-stu-id="992f2-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="992f2-181">當您的觀賞不在 Windows Mixed Reality 耳機中呈現時，我們建議您藉由隱藏進入點或顯示錯誤訊息，正常地處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="992f2-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="992f2-182">您可以藉由查詢[IsCurrentViewPresentedOnHolographic （）](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)來進行檢查。</span><span class="sxs-lookup"><span data-stu-id="992f2-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="992f2-183">磚通知</span><span class="sxs-lookup"><span data-stu-id="992f2-183">Tile notifications</span></span>

<span data-ttu-id="992f2-184">磚通知目前不支援傳送含有3D 資產的更新。</span><span class="sxs-lookup"><span data-stu-id="992f2-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="992f2-185">這表示開發人員將無法執行下列動作</span><span class="sxs-lookup"><span data-stu-id="992f2-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="992f2-186">推播通知</span><span class="sxs-lookup"><span data-stu-id="992f2-186">Push Notifications</span></span>
* <span data-ttu-id="992f2-187">定期輪詢</span><span class="sxs-lookup"><span data-stu-id="992f2-187">Periodic Polling</span></span>
* <span data-ttu-id="992f2-188">排定的通知</span><span class="sxs-lookup"><span data-stu-id="992f2-188">Scheduled Notifications</span></span>

<span data-ttu-id="992f2-189">如需其他圖格功能和屬性以及它們如何用於2D 磚的詳細資訊，請參閱[UWP 應用程式的磚檔](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。</span><span class="sxs-lookup"><span data-stu-id="992f2-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="992f2-190">請參閱</span><span class="sxs-lookup"><span data-stu-id="992f2-190">See also</span></span>

* <span data-ttu-id="992f2-191">包含3D 應用程式啟動器的[混合現實模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。</span><span class="sxs-lookup"><span data-stu-id="992f2-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="992f2-192">3D 應用程式啟動程式設計指引</span><span class="sxs-lookup"><span data-stu-id="992f2-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="992f2-193">建立3D 模型以用於 Windows Mixed Reality 首頁</span><span class="sxs-lookup"><span data-stu-id="992f2-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="992f2-194">執行3D 應用程式啟動器（Win32 應用程式）</span><span class="sxs-lookup"><span data-stu-id="992f2-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="992f2-195">瀏覽 Windows Mixed Reality 住家</span><span class="sxs-lookup"><span data-stu-id="992f2-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
