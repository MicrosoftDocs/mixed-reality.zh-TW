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
# <a name="implement-3d-app-launchers-uwp-apps"></a>實作 3D 應用程式啟動器 (UWP app)

> [!NOTE]
> 這項功能已新增為沈浸式耳機 2017 Fall Creators Update (RS3) 的一部分，並受到 HoloLens 與 Windows 10 April 2018 Update。 請確定您的應用程式大於或等於 10.0.16299 上耳機沈浸式且 10.0.17125 HoloLens 上的 Windows sdk 版本為目標。 您可以找到最新的 Windows SDK[此處](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。

[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)是使用者啟動應用程式之前的登陸位置的起點。 建立時的 UWP 應用程式的 Windows Mixed Reality，根據預設，應用程式會啟動為其應用程式標誌的 2D slate。 當 Windows Mixed Reality 開發體驗，3D 的啟動器可以選擇性地定義覆寫預設 2D launcher，可用於您的應用程式。 一般情況下，建議 3D 啟動器啟動接受使用者從家用的 Windows Mixed Reality，而應用程式啟動就緒時，預設 2D 啟動器是慣用的沉浸式應用程式。 您也可以建立[3D 的深層連結 (secondaryTile)](#3d-deep-links-secondarytiles)為 3D 的啟動器 2D 的 UWP 應用程式內的內容。

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D 應用程式啟動器建立程序

有 3 個步驟以建立 3D 應用程式啟動程式：
1. [設計和 concepting](3d-app-launcher-design-guidance.md)
2. [模型化和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 將它整合到您的應用程式 （本文）

應該使用撰寫您的應用程式的啟動程式要使用 3D 資產[撰寫指導方針的 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)以確保相容性。 在家用的 Windows Mixed Reality 時，將無法呈現無法符合此規格中撰寫的資產。

## <a name="configuring-the-3d-launcher"></a>設定 「 3D 」 啟動程式

在 Visual Studio 中建立新的專案時，它會建立一個顯示 app 名稱和標誌的簡單預設磚。 若要取代此 2D 表示包含自訂的 3D 模型會編輯應用程式資訊清單的應用程式以包含 「 MixedRealityModel"項目，為您的預設圖格定義的一部分。 若要還原為 2D 啟動器只移除 MixedRealityModel 定義資訊清單。

### <a name="xml"></a>XML

首先，尋找目前專案中的應用程式封裝資訊清單。 根據預設，資訊清單將會命名 Package.appxmanifest。 如果您使用 Visual Studio，然後以滑鼠右鍵按一下您的方案檢視器中的資訊清單並選取**檢視原始檔**開啟進行編輯的 xml。 

在資訊清單的頂端，新增 uap5 結構描述，並將它包含可忽略的命名空間：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

接下來的預設圖格，您的應用程式中指定 」 MixedRealityModel 」:

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

MixedRealityModel 元素接受檔案路徑指向您的應用程式封裝中儲存的 3D 資產。 目前只有的 3D 模型使用.glb 檔案格式傳送和對撰寫[撰寫指示的 Windows Mixed Reality 3D 資產](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)支援。 資產必須儲存在應用程式套件，目前不支援動畫。 如果 「 路徑 」 參數保留空白 Windows 會顯示 2D 的候選影片，而不是 「 3D 」 啟動程式。 **注意：** .glb 資產必須標示為 「 內容 」 中您的組建設定之前建置和執行您的應用程式。


![在方案總管中選取.glb，然後使用 [屬性] 區段中的組建設定，將其標示為 「 內容 」](images/buildsetting-content-300px.png)<br>
*在方案總管中選取.glb，然後使用 [屬性] 區段中的組建設定，將其標示為 「 內容 」*

### <a name="bounding-box"></a>週框方塊

週框方塊可用來選擇性地加入物件周圍的其他緩衝區區域。 使用中心點的範圍，這表示週框方塊的中心到每個軸與其邊緣之間的距離，以及指定的週框方塊。 週框方塊的單位可以對應至 1 個單位 = 1 公尺。 如果未提供的週框方塊然後其中一個將會自動納入物件的網狀結構。 如果提供的週框方塊小於此模型然後它會調整大小以符合網狀結構。

週框方塊屬性的支援會隨附 Windows RS4 更新屬性 MixedRealityModel 項目上。 先定義週框方塊，頂端的 應用程式資訊清單新增 uap6 結構描述並將它包含可忽略的命名空間為它們：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
接下來，在 MixedRealityModel SpatialBoundingBox 將屬性設定為定義週框方塊： 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>使用 Unity

使用 Unity 時必須建置專案，然後才可以編輯應用程式資訊清單，Visual Studio 中開啟。 

>[!NOTE]
>3D 的啟動器必須重新定義建置和部署新的 Visual Studio 方案，從 Unity 時的資訊清單中。

## <a name="3d-deep-links-secondarytiles"></a>3D 的深層連結 (secondaryTiles)

> [!NOTE]
> 這項功能已新增為沈浸式 (VR) 耳機 2017 Fall Creators Update (RS3) 的一部分，而年 4 月 2018年的一部分的 HoloLens 的更新 (RS4)。 請確定您的應用程式大於或等於在沉浸式 (VR) 耳機 10.0.16299 且 10.0.17125 HoloLens 上的 Windows sdk 版本為目標。 您可以找到最新的 Windows SDK[此處](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。

>[!IMPORTANT]
>3D 的深層連結 (secondaryTiles) 只適用於 2D 的 UWP 應用程式。 不過，您可以建立[3D 應用程式啟動器](implementing-3d-app-launchers.md)啟動獨佔家用的 Windows Mixed Reality 應用程式。

2D 應用程式可以加上放置到的應用程式的 3D 模型的功能增強的 Windows Mixed Reality [Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)2D 應用程式內的內容的深層連結，就像[2D 的次要資料庫圖格](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)Windows [開始] 功能表。 例如，您可以建立 360 ° photospheres，直接將 360 ° 的相片檢視器應用程式連結，或讓使用者放置的集合中的資產，會開啟詳細資料頁面，作者的 3D 內容。 這些是以展開 應用程式功能的 2D 與 3D 內容的幾種方式。

### <a name="creating-a-3d-secondarytile"></a>建立 3D"secondaryTile 」

您可以從您的應用程式藉由在建立時定義混合的實境模型使用 「 secondaryTiles 」 放置 3D 內容。 混合的實境模型會建立參考應用程式套件中的 3D 資產，並選擇性地定義週框方塊。 

> [!NOTE]
> 目前不支援從建立"secondaryTiles 」 內的專屬檢視。

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

週框方塊可用來新增可在物件周圍的其他緩衝區區域。 使用中心點的範圍，這表示週框方塊的中心到每個軸與其邊緣之間的距離，以及指定的週框方塊。 週框方塊的單位可以對應至 1 個單位 = 1 公尺。 如果未提供的週框方塊然後其中一個將會自動納入物件的網狀結構。 如果提供的週框方塊小於此模型然後它會調整大小以符合網狀結構。

### <a name="activation-behavior"></a>啟用行為

> [!NOTE]
> 這項功能將會支援 Windows RS4 更新。 請確定您的應用程式的目標大於或等於 10.0.17125 的 Windows sdk 版本，如果您打算使用這項功能

您可以定義來控制當使用者選取它，它的回應方式的 3D secondaryTile 的啟動行為。 這可用來將 3D 物件放在混合實境中主要的 purley 具有資訊價值或裝飾。 支援下列的啟動行為類型：
1. Default：當使用者選取 3D secondaryTile 啟用應用程式
2. None:當使用者選取會發生任何事 3D secondaryTile 和應用程式就不會啟動。

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>如何取得並更新現有的 「 secondaryTile"

開發人員可以取得一份其現有的次要磚，其中包含先前指定的屬性。 他們也可以藉由變更值，然後呼叫 UpdateAsync() 更新屬性。

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>檢查使用者位於 Windows Mixed Reality

檢視會顯示在 Windows Mixed Reality 耳機時，就只能建立 3D 的深層連結 (secondaryTiles)。 當您的檢視不顯示 Windows Mixed Reality 耳機建議依正常程序處理這就隱藏的進入點，或顯示錯誤訊息。 您可以藉由查詢中檢查這[IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)。

## <a name="tile-notifications"></a>磚通知

磚通知目前不支援傳送與 3D 資產更新。 這表示開發人員不會執行下列作業
* 推播通知
* 定期輪詢
* 已排程的通知

其他的更多有關磚功能和屬性，和它們被用於 2D 磚指[UWP 應用程式文件的圖格](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。

## <a name="see-also"></a>另請參閱

* [混合的實境模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)包含 3D 應用程式啟動程式。
* [3D 應用程式啟動程式的設計指引](3d-app-launcher-design-guidance.md)
* [建立 3D 模型，使用 Windows Mixed Reality 在家中](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [實作 3D 應用程式啟動器 （Win32 應用程式）](implementing-3d-app-launchers-win32.md)
* [瀏覽家用的 Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
