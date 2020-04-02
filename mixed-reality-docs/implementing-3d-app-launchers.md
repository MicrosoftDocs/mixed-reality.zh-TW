---
title: 執行3D 應用程式啟動器（UWP 應用程式）
description: 如何建立適用于 Windows Mixed Reality UWP 應用程式和遊戲的3D 應用程式啟動器和標誌（透過 Microsoft Store 散發），包括 HoloLens 和沉浸式（VR）耳機。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D，標誌，圖示，模型，啟動器，3D 啟動器，磚，即時 cube，深層連結，secondarytile，次要磚，UWP
ms.openlocfilehash: 0a2e2177ffa7e381c461a58f373c818c9c5e72c4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549384"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>執行3D 應用程式啟動器（UWP 應用程式）

> [!NOTE]
> 這項功能已新增為沉浸式耳機的2017秋季建立者更新（RS3）的一部分，且 HoloLens 支援 Windows 10 4 月2018更新。 請確定您的應用程式是以10.0.16299 的版本為目標，而不是以沉浸式頭戴式耳機和10.0.17125 在 HoloLens 上的 Windows SDK。 您可以在[這裡](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。

[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。 建立適用于 Windows Mixed Reality 的 UWP 應用程式時，根據預設，應用程式會以其應用程式的標誌，以2D 平板的形式啟動。 在開發 Windows Mixed Reality 的經驗時，可以選擇性地定義3D 啟動器以覆寫應用程式的預設2D 啟動器。 一般而言，建議使用3D 啟動器來啟動沉浸式應用程式，讓使用者離開 Windows Mixed Reality home，而當應用程式就地啟用時，偏好使用預設的2D 啟動器。 您也可以建立[3d 的深層連結（secondaryTile）](#3d-deep-links-secondarytiles) ，做為 2d UWP 應用程式中內容的3d 啟動器。

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D 應用程式啟動器建立進程

建立3D 應用程式啟動器有3個步驟：
1. [設計和 concepting](3d-app-launcher-design-guidance.md)
2. [模型化和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 將它整合到您的應用程式（本文）

要做為應用程式之啟動器使用的3D 資產，應使用[Windows Mixed Reality 撰寫指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)來確保相容性。 無法符合此撰寫規格的資產將不會在 Windows Mixed Reality 首頁中轉譯。

## <a name="configuring-the-3d-launcher"></a>設定3D 啟動程式

在 Visual Studio 中建立新的專案時，它會建立一個顯示 app 名稱和標誌的簡單預設磚。 若要以自訂3D 模型取代此2D 標記法，請編輯應用程式的應用程式資訊清單，以將 "MixedRealityModel" 元素納入為預設磚定義的一部分。 若要還原為2D 啟動器，請直接從資訊清單中移除 MixedRealityModel 定義。

### <a name="xml"></a>XML

首先，在您目前的專案中找出應用程式套件資訊清單。 根據預設，資訊清單會命名為 package.appxmanifest.xml。 如果您使用 Visual Studio，請以滑鼠右鍵按一下方案檢視器中的資訊清單，然後選取 [ **View source** ] 以開啟 xml 進行編輯。 

在資訊清單的頂端，新增 uap5 架構，並將它包含為可忽略的命名空間：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

接下來，在應用程式的預設磚中指定 "MixedRealityModel"：

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

MixedRealityModel 元素會接受指向儲存在應用程式套件中之3D 資產的檔案路徑。 目前只支援使用 glb 檔案格式所提供的3D 模型，並根據[Windows Mixed Reality 3d 資產撰寫指示](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)來撰寫。 資產必須儲存在應用程式套件中，而且目前不支援動畫。 如果 "Path" 參數保留空白，Windows 將會顯示2D 平板電腦，而不是3D 啟動程式。 **注意：** 在建立並執行您的應用程式之前，必須先將 glb 資產標記為您組建設定中的「內容」。


![在您的方案 explorer 中選取 glb，並使用 [屬性] 區段，將其標示為 [組建設定] 中的 [內容]](images/buildsetting-content-300px.png)<br>
*在 [方案瀏覽器] 中選取 glb，然後使用 [屬性] 區段，將其標示為 [內容] （在 [組建設定] 中）*

### <a name="bounding-box"></a>週框方塊

周框方塊可以用來選擇性地在物件周圍加入額外的緩衝區區域。 周框方塊是使用中心點和範圍來指定，其表示從周框方塊中央到其邊緣沿著每個軸的距離。 周框方塊的單位可以對應到1個單位 = 1 個計量。 如果未提供周框方塊，則會自動將一個方塊調整為物件的網格。 如果提供的周框方塊小於模型，則會調整大小以符合網格。

周框方塊屬性的支援將隨附于 Windows RS4 update，做為 MixedRealityModel 元素上的屬性。 若要先在應用程式資訊清單頂端定義周框方塊，請新增 uap6 架構，並將其包含為可忽略的命名空間：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
接下來，在 MixedRealityModel 上設定 SpatialBoundingBox 屬性以定義周框方塊： 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>使用 Unity

使用 Unity 時，必須在 Visual Studio 中建立和開啟專案，才能編輯應用程式資訊清單。 

>[!NOTE]
>從 Unity 建立和部署新的 Visual Studio 方案時，必須在資訊清單中重新定義3D 啟動程式。

## <a name="3d-deep-links-secondarytiles"></a>3D 深層連結（secondaryTiles）

> [!NOTE]
> 這項功能已新增為沉浸（VR）耳機的2017秋季建立者更新（RS3）的一部分，並作為 HoloLens 2018 年4月更新（RS4）的一部分。 請確定您的應用程式是以10.0.16299 的版本為目標，而不是以沉浸式（VR）耳機和 10.0.17125 on HoloLens 的 Windows SDK。 您可以在[這裡](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。

>[!IMPORTANT]
>3D 深層連結（secondaryTiles）僅適用于 2D UWP 應用程式。 不過，您可以建立[3d 應用程式啟動器](implementing-3d-app-launchers.md)，從 Windows Mixed Reality home 啟動專屬的應用程式。

藉由新增將3D 模型從您的應用程式放入[Windows Mixed reality home](navigating-the-windows-mixed-reality-home.md)做為2d 應用程式中內容的深層連結，就像 Windows [開始] 功能表上的[2d 次要磚](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)一樣，您可以增強2D 應用程式的 windows mixed reality 功能。 例如，您可以建立可直接連結至360相片檢視器應用程式的360° photospheres，或讓使用者從一組資產集合中開啟3D 內容，這些資產會開啟有關作者的詳細資料頁面。 這些只是使用3D 內容擴充2D 應用程式功能的幾種方式。

### <a name="creating-a-3d-secondarytile"></a>建立 3D "secondaryTile"

您可以在建立時定義混合現實模型，以使用 "secondaryTiles" 從應用程式中放置3D 內容。 混合現實模型的建立方式是參考應用程式套件中的3D 資產，並選擇性地定義周框方塊。 

> [!NOTE]
> 目前不支援從獨佔視圖中建立 "secondaryTiles"。

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

### <a name="bounding-box"></a>週框方塊

周框方塊可以用來在物件周圍加入額外的緩衝區區域。 周框方塊是使用中心點和範圍來指定，其表示從周框方塊中央到其邊緣沿著每個軸的距離。 周框方塊的單位可以對應到1個單位 = 1 個計量。 如果未提供周框方塊，則會自動將一個方塊調整為物件的網格。 如果提供的周框方塊小於模型，則會調整大小以符合網格。

### <a name="activation-behavior"></a>啟用行為

> [!NOTE]
> 這項功能將受到 Windows RS4 update 的支援。 如果您打算使用這項功能，請確定您的應用程式是以大於或等於10.0.17125 的 Windows SDK 版本為目標

您可以定義 3D secondaryTile 的啟用行為，以控制當使用者選取它時的回應方式。 這可以用來將3D 物件放在純粹是資訊性或裝飾的混合現實首頁中。 支援下列啟用行為類型：
1. 預設值：當使用者選取 3D secondaryTile 時，應用程式就會啟用
2. 無：當使用者選取 3D secondaryTile 時，不會發生任何事，也不會啟用應用程式。

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>取得和更新現有的 "secondaryTile"

開發人員可以取回其現有的次要磚清單，其中包括先前指定的屬性。 它們也可以藉由變更值，然後呼叫 UpdateAsync （）來更新屬性。

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>正在檢查使用者是否在 Windows Mixed Reality 中

只有當視圖在 Windows Mixed Reality 耳機中顯示時，才能建立3D 深層連結（secondaryTiles）。 當您的觀賞不在 Windows Mixed Reality 耳機中呈現時，我們建議您藉由隱藏進入點或顯示錯誤訊息，正常地處理這種情況。 您可以藉由查詢[IsCurrentViewPresentedOnHolographic （）](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)來進行檢查。

## <a name="tile-notifications"></a>磚通知

磚通知目前不支援傳送含有3D 資產的更新。 這表示開發人員將無法執行下列動作
* 推播通知
* 定期輪詢
* 排定的通知

如需其他圖格功能和屬性以及它們如何用於2D 磚的詳細資訊，請參閱[UWP 應用程式的磚檔](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。

## <a name="see-also"></a>另請參閱

* 包含3D 應用程式啟動器的[混合現實模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。
* [3D 應用程式啟動程式設計指引](3d-app-launcher-design-guidance.md)
* [建立3D 模型以用於 Windows Mixed Reality 首頁](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [執行3D 應用程式啟動器（Win32 應用程式）](implementing-3d-app-launchers-win32.md)
* [瀏覽 Windows Mixed Reality 住家](navigating-the-windows-mixed-reality-home.md)
