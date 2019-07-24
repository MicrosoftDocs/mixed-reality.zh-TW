---
title: 在首頁中啟用3D 模型的放置
description: 如何從您的網站或應用程式, 將3D 模型放在 Windows Mixed Reality 首頁
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, 模型, 放置於家裡, 地點, 世界, 模型, 混合現實首頁, web, 應用程式
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829729"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>在混合現實首頁中啟用3D 模型的放置

> [!NOTE]
> 這項功能已新增為[Windows 10 2018 年4月更新](release-notes-april-2018.md)的一部分。 較舊版本的 Windows 與此功能不相容。

[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。 在某些案例中, 2D 應用程式 (例如「全息影像」應用程式) 可將3D 模型直接放置在混合現實首頁中作為裝飾, 或以完整3D 進行進一步檢查。 「*新增模型」通訊協定*可讓您將3d 模型從您的網站或應用程式直接傳送至 Windows Mixed Reality 首頁, 其將會保存, 例如[3d 應用程式啟動器](3d-app-launcher-design-guidance.md)、2d 應用程式和全息影像。 

例如, 如果您正在開發的應用程式會呈現3D 傢俱的目錄以設計空間, 您可以使用*新增模型通訊協定*, 讓使用者從類別目錄中放置這些3d 傢俱模型。 一旦放在世界中, 使用者就可以移動、調整大小和移除這些3D 模型, 就像在家中的其他全息影像一樣。 本文概述如何實行「*新增模型」通訊協定*, 讓您可以開始讓使用者從您的應用程式或 Web 使用3d 物件裝飾其世界。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>新增模型通訊協定</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>總覽

在 Windows Mixed Reality 首頁中啟用3D 模型的位置有2個步驟:
1. [確定您的3d 模型與 Windows Mixed Reality 首頁相容](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。
2. 在您的應用程式或網頁中執行「*新增模型」通訊協定*(本文)。

## <a name="implementing-the-add-model-protocol"></a>執行*新增模型通訊協定*

當您擁有[相容的3d 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)之後, 您可以從任何網頁或應用程式啟用下列 URI, 以實作為「*新增模型」通訊協定*:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

如果 URI 指向遠端資源, 則會自動下載並放在首頁。 本機資源會先複製到混合現實首頁的 [應用程式資料] 資料夾, 才會放入首頁。 我們建議您針對使用者可能執行舊版 Windows 而不支援這項功能的情況, 在可能的情況下, 將您的經驗設計成考慮。 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>從通用 Windows 平臺應用程式叫用*新增模型通訊協定*:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>從網頁叫用*新增模型通訊協定*:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>沉浸式 (VR) 耳機的考慮

* 若為沉浸式 (VR) 耳機, 則在叫用「*新增模型」通訊協定*之前, 混合現實入口網站不需要執行。 在此情況下, 「*新增模型」通訊協定*將會啟動混合現實入口網站, 並直接將物件放在您抵達混合現實首頁後的頭戴式裝置上。 
* 從已執行混合現實入口網站的桌面叫用 [*新增模型] 通訊協定*時, 請確定耳機處於「喚醒」狀態。 如果不是, 則放置將會失敗。 

## <a name="see-also"></a>另請參閱

* [建立3D 模型以用於 Windows Mixed Reality 首頁](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [瀏覽 Windows Mixed Reality 住家](navigating-the-windows-mixed-reality-home.md)
