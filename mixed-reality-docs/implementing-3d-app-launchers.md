---
title: 實作 3D 應用程式啟動器 (UWP app)
description: 如何建立 3D 應用程式啟動器和標誌 Windows Mixed Reality UWP 應用程式和遊戲 （透過 Microsoft Store 散發）、 HoloLens 和沈浸式 (VR) 耳機。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、 標誌、 圖示、 模型、 啟動器、 3D 的啟動器、 圖格、 即時的 cube、 深層連結、 secondarytile、 次要磚，UWP
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597027"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="504d4-104">實作 3D 應用程式啟動器 (UWP app)</span><span class="sxs-lookup"><span data-stu-id="504d4-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="504d4-105">這項功能已新增為沈浸式耳機 2017 Fall Creators Update (RS3) 的一部分，並受到 HoloLens 與 Windows 10 April 2018 Update。</span><span class="sxs-lookup"><span data-stu-id="504d4-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="504d4-106">請確定您的應用程式大於或等於 10.0.16299 上耳機沈浸式且 10.0.17125 HoloLens 上的 Windows sdk 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="504d4-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="504d4-107">您可以找到最新的 Windows SDK[此處](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="504d4-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="504d4-108">[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)是使用者啟動應用程式之前的登陸位置的起點。</span><span class="sxs-lookup"><span data-stu-id="504d4-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="504d4-109">建立時的 UWP 應用程式的 Windows Mixed Reality，根據預設，應用程式會啟動為其應用程式標誌的 2D slate。</span><span class="sxs-lookup"><span data-stu-id="504d4-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="504d4-110">當 Windows Mixed Reality 開發體驗，3D 的啟動器可以選擇性地定義覆寫預設 2D launcher，可用於您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="504d4-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="504d4-111">一般情況下，建議 3D 啟動器啟動接受使用者從家用的 Windows Mixed Reality，而應用程式啟動就緒時，預設 2D 啟動器是慣用的沉浸式應用程式。</span><span class="sxs-lookup"><span data-stu-id="504d4-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="504d4-112">您也可以建立[3D 的深層連結 (secondaryTile)](#3d-deep-links-secondarytiles)為 3D 的啟動器 2D 的 UWP 應用程式內的內容。</span><span class="sxs-lookup"><span data-stu-id="504d4-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="504d4-113">3D 應用程式啟動器建立程序</span><span class="sxs-lookup"><span data-stu-id="504d4-113">3D app launcher creation process</span></span>

<span data-ttu-id="504d4-114">有 3 個步驟以建立 3D 應用程式啟動程式：</span><span class="sxs-lookup"><span data-stu-id="504d4-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="504d4-115">設計和 concepting</span><span class="sxs-lookup"><span data-stu-id="504d4-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="504d4-116">模型化和匯出</span><span class="sxs-lookup"><span data-stu-id="504d4-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="504d4-117">將它整合到您的應用程式 （本文）</span><span class="sxs-lookup"><span data-stu-id="504d4-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="504d4-118">應該使用撰寫您的應用程式的啟動程式要使用 3D 資產[撰寫指導方針的 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)以確保相容性。</span><span class="sxs-lookup"><span data-stu-id="504d4-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="504d4-119">在家用的 Windows Mixed Reality 時，將無法呈現無法符合此規格中撰寫的資產。</span><span class="sxs-lookup"><span data-stu-id="504d4-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="504d4-120">設定 「 3D 」 啟動程式</span><span class="sxs-lookup"><span data-stu-id="504d4-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="504d4-121">在 Visual Studio 中建立新的專案時，它會建立一個顯示 app 名稱和標誌的簡單預設磚。</span><span class="sxs-lookup"><span data-stu-id="504d4-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="504d4-122">若要取代此 2D 表示包含自訂的 3D 模型會編輯應用程式資訊清單的應用程式以包含 「 MixedRealityModel"項目，為您的預設圖格定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="504d4-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="504d4-123">若要還原為 2D 啟動器只移除 MixedRealityModel 定義資訊清單。</span><span class="sxs-lookup"><span data-stu-id="504d4-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="504d4-124">XML</span><span class="sxs-lookup"><span data-stu-id="504d4-124">XML</span></span>

<span data-ttu-id="504d4-125">首先，尋找目前專案中的應用程式封裝資訊清單。</span><span class="sxs-lookup"><span data-stu-id="504d4-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="504d4-126">根據預設，資訊清單將會命名 Package.appxmanifest。</span><span class="sxs-lookup"><span data-stu-id="504d4-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="504d4-127">如果您使用 Visual Studio，然後以滑鼠右鍵按一下您的方案檢視器中的資訊清單並選取**檢視原始檔**開啟進行編輯的 xml。</span><span class="sxs-lookup"><span data-stu-id="504d4-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="504d4-128">在資訊清單的頂端，新增 uap5 結構描述，並將它包含可忽略的命名空間：</span><span class="sxs-lookup"><span data-stu-id="504d4-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="504d4-129">接下來的預設圖格，您的應用程式中指定 」 MixedRealityModel 」:</span><span class="sxs-lookup"><span data-stu-id="504d4-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

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

<span data-ttu-id="504d4-130">MixedRealityModel 元素接受檔案路徑指向您的應用程式封裝中儲存的 3D 資產。</span><span class="sxs-lookup"><span data-stu-id="504d4-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="504d4-131">目前只有的 3D 模型使用.glb 檔案格式傳送和對撰寫[撰寫指示的 Windows Mixed Reality 3D 資產](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)支援。</span><span class="sxs-lookup"><span data-stu-id="504d4-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="504d4-132">資產必須儲存在應用程式套件，目前不支援動畫。</span><span class="sxs-lookup"><span data-stu-id="504d4-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="504d4-133">如果 「 路徑 」 參數保留空白 Windows 會顯示 2D 的候選影片，而不是 「 3D 」 啟動程式。</span><span class="sxs-lookup"><span data-stu-id="504d4-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="504d4-134">**注意：** .glb 資產必須標示為 「 內容 」 中您的組建設定之前建置和執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="504d4-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="504d4-135">![在方案總管中選取.glb，然後使用 [屬性] 區段中的組建設定，將其標示為 「 內容 」](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="504d4-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="504d4-136">*在方案總管中選取.glb，然後使用 [屬性] 區段中的組建設定，將其標示為 「 內容 」*</span><span class="sxs-lookup"><span data-stu-id="504d4-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="504d4-137">週框方塊</span><span class="sxs-lookup"><span data-stu-id="504d4-137">Bounding box</span></span>

<span data-ttu-id="504d4-138">週框方塊可用來選擇性地加入物件周圍的其他緩衝區區域。</span><span class="sxs-lookup"><span data-stu-id="504d4-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="504d4-139">使用中心點的範圍，這表示週框方塊的中心到每個軸與其邊緣之間的距離，以及指定的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="504d4-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="504d4-140">週框方塊的單位可以對應至 1 個單位 = 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="504d4-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="504d4-141">如果未提供的週框方塊然後其中一個將會自動納入物件的網狀結構。</span><span class="sxs-lookup"><span data-stu-id="504d4-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="504d4-142">如果提供的週框方塊小於此模型然後它會調整大小以符合網狀結構。</span><span class="sxs-lookup"><span data-stu-id="504d4-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="504d4-143">週框方塊屬性的支援會隨附 Windows RS4 更新屬性 MixedRealityModel 項目上。</span><span class="sxs-lookup"><span data-stu-id="504d4-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="504d4-144">先定義週框方塊，頂端的 應用程式資訊清單新增 uap6 結構描述並將它包含可忽略的命名空間為它們：</span><span class="sxs-lookup"><span data-stu-id="504d4-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="504d4-145">接下來，在 MixedRealityModel SpatialBoundingBox 將屬性設定為定義週框方塊：</span><span class="sxs-lookup"><span data-stu-id="504d4-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="504d4-146">使用 Unity</span><span class="sxs-lookup"><span data-stu-id="504d4-146">Using Unity</span></span>

<span data-ttu-id="504d4-147">使用 Unity 時必須建置專案，然後才可以編輯應用程式資訊清單，Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="504d4-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="504d4-148">3D 的啟動器必須重新定義建置和部署新的 Visual Studio 方案，從 Unity 時的資訊清單中。</span><span class="sxs-lookup"><span data-stu-id="504d4-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="504d4-149">3D 的深層連結 (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="504d4-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="504d4-150">這項功能已新增為沈浸式 (VR) 耳機 2017 Fall Creators Update (RS3) 的一部分，而年 4 月 2018年的一部分的 HoloLens 的更新 (RS4)。</span><span class="sxs-lookup"><span data-stu-id="504d4-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="504d4-151">請確定您的應用程式大於或等於在沉浸式 (VR) 耳機 10.0.16299 且 10.0.17125 HoloLens 上的 Windows sdk 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="504d4-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="504d4-152">您可以找到最新的 Windows SDK[此處](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="504d4-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="504d4-153">3D 的深層連結 (secondaryTiles) 只適用於 2D 的 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="504d4-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="504d4-154">不過，您可以建立[3D 應用程式啟動器](implementing-3d-app-launchers.md)啟動獨佔家用的 Windows Mixed Reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="504d4-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="504d4-155">2D 應用程式可以加上放置到的應用程式的 3D 模型的功能增強的 Windows Mixed Reality [Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)2D 應用程式內的內容的深層連結，就像[2D 的次要資料庫圖格](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)Windows [開始] 功能表。</span><span class="sxs-lookup"><span data-stu-id="504d4-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="504d4-156">例如，您可以建立 360 ° photospheres，直接將 360 ° 的相片檢視器應用程式連結，或讓使用者放置的集合中的資產，會開啟詳細資料頁面，作者的 3D 內容。</span><span class="sxs-lookup"><span data-stu-id="504d4-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="504d4-157">這些是以展開 應用程式功能的 2D 與 3D 內容的幾種方式。</span><span class="sxs-lookup"><span data-stu-id="504d4-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="504d4-158">建立 3D"secondaryTile 」</span><span class="sxs-lookup"><span data-stu-id="504d4-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="504d4-159">您可以從您的應用程式藉由在建立時定義混合的實境模型使用 「 secondaryTiles 」 放置 3D 內容。</span><span class="sxs-lookup"><span data-stu-id="504d4-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="504d4-160">混合的實境模型會建立參考應用程式套件中的 3D 資產，並選擇性地定義週框方塊。</span><span class="sxs-lookup"><span data-stu-id="504d4-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="504d4-161">目前不支援從建立"secondaryTiles 」 內的專屬檢視。</span><span class="sxs-lookup"><span data-stu-id="504d4-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

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

### <a name="bounding-box"></a><span data-ttu-id="504d4-162">週框方塊</span><span class="sxs-lookup"><span data-stu-id="504d4-162">Bounding box</span></span>

<span data-ttu-id="504d4-163">週框方塊可用來新增可在物件周圍的其他緩衝區區域。</span><span class="sxs-lookup"><span data-stu-id="504d4-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="504d4-164">使用中心點的範圍，這表示週框方塊的中心到每個軸與其邊緣之間的距離，以及指定的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="504d4-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="504d4-165">週框方塊的單位可以對應至 1 個單位 = 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="504d4-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="504d4-166">如果未提供的週框方塊然後其中一個將會自動納入物件的網狀結構。</span><span class="sxs-lookup"><span data-stu-id="504d4-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="504d4-167">如果提供的週框方塊小於此模型然後它會調整大小以符合網狀結構。</span><span class="sxs-lookup"><span data-stu-id="504d4-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="504d4-168">啟用行為</span><span class="sxs-lookup"><span data-stu-id="504d4-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="504d4-169">這項功能將會支援 Windows RS4 更新。</span><span class="sxs-lookup"><span data-stu-id="504d4-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="504d4-170">請確定您的應用程式的目標大於或等於 10.0.17125 的 Windows sdk 版本，如果您打算使用這項功能</span><span class="sxs-lookup"><span data-stu-id="504d4-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="504d4-171">您可以定義來控制當使用者選取它，它的回應方式的 3D secondaryTile 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="504d4-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="504d4-172">這可用來將 3D 物件放在混合實境中主要的 purley 具有資訊價值或裝飾。</span><span class="sxs-lookup"><span data-stu-id="504d4-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="504d4-173">支援下列的啟動行為類型：</span><span class="sxs-lookup"><span data-stu-id="504d4-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="504d4-174">Default：當使用者選取 3D secondaryTile 啟用應用程式</span><span class="sxs-lookup"><span data-stu-id="504d4-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="504d4-175">None:當使用者選取會發生任何事 3D secondaryTile 和應用程式就不會啟動。</span><span class="sxs-lookup"><span data-stu-id="504d4-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="504d4-176">如何取得並更新現有的 「 secondaryTile"</span><span class="sxs-lookup"><span data-stu-id="504d4-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="504d4-177">開發人員可以取得一份其現有的次要磚，其中包含先前指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="504d4-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="504d4-178">他們也可以藉由變更值，然後呼叫 UpdateAsync() 更新屬性。</span><span class="sxs-lookup"><span data-stu-id="504d4-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="504d4-179">檢查使用者位於 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="504d4-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="504d4-180">檢視會顯示在 Windows Mixed Reality 耳機時，就只能建立 3D 的深層連結 (secondaryTiles)。</span><span class="sxs-lookup"><span data-stu-id="504d4-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="504d4-181">當您的檢視不顯示 Windows Mixed Reality 耳機建議依正常程序處理這就隱藏的進入點，或顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="504d4-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="504d4-182">您可以藉由查詢中檢查這[IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)。</span><span class="sxs-lookup"><span data-stu-id="504d4-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="504d4-183">磚通知</span><span class="sxs-lookup"><span data-stu-id="504d4-183">Tile notifications</span></span>

<span data-ttu-id="504d4-184">磚通知目前不支援傳送與 3D 資產更新。</span><span class="sxs-lookup"><span data-stu-id="504d4-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="504d4-185">這表示開發人員不會執行下列作業</span><span class="sxs-lookup"><span data-stu-id="504d4-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="504d4-186">推播通知</span><span class="sxs-lookup"><span data-stu-id="504d4-186">Push Notifications</span></span>
* <span data-ttu-id="504d4-187">定期輪詢</span><span class="sxs-lookup"><span data-stu-id="504d4-187">Periodic Polling</span></span>
* <span data-ttu-id="504d4-188">已排程的通知</span><span class="sxs-lookup"><span data-stu-id="504d4-188">Scheduled Notifications</span></span>

<span data-ttu-id="504d4-189">其他的更多有關磚功能和屬性，和它們被用於 2D 磚指[UWP 應用程式文件的圖格](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。</span><span class="sxs-lookup"><span data-stu-id="504d4-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="504d4-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="504d4-190">See also</span></span>

* <span data-ttu-id="504d4-191">[混合的實境模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)包含 3D 應用程式啟動程式。</span><span class="sxs-lookup"><span data-stu-id="504d4-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="504d4-192">3D 應用程式啟動程式的設計指引</span><span class="sxs-lookup"><span data-stu-id="504d4-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="504d4-193">建立 3D 模型，使用 Windows Mixed Reality 在家中</span><span class="sxs-lookup"><span data-stu-id="504d4-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="504d4-194">實作 3D 應用程式啟動器 （Win32 應用程式）</span><span class="sxs-lookup"><span data-stu-id="504d4-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="504d4-195">瀏覽家用的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="504d4-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
