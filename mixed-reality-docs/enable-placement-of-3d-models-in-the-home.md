---
title: 啟用在家中的 3D 模型的位置
description: 如何將 3D 模型，從您的網站或應用程式放入家用的 Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D、 模型、 家中的位置、 位置、 全球、 模型、 混合的實境家用、 web、 應用程式
ms.openlocfilehash: 3a50353aae8e03c3ebb3ee9ec2f642f21836e925
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597094"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>啟用在首頁的混合實境中的 3D 模型的位置

> [!NOTE]
> 這項功能已加入的一部分[Windows 10 April 2018 Update](release-notes-april-2018.md)。 舊版 Windows 不相容於這項功能。

[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)是使用者啟動應用程式之前的登陸位置的起點。 在某些情況下，2D 應用程式 （例如全像投影的應用程式） 作為裝飾或進一步調查完整的 3D 中啟用 3D 模型直接放置到混合的實境首頁。 *新增模型通訊協定*可讓您從網站或直接將家中的 Windows Mixed Reality 應用程式傳送的 3D 模型，它會保存像是[3D 應用程式啟動器](3d-app-launcher-design-guidance.md)，2D 應用程式和全像投影。 

例如，如果您正在開發應用程式的 3D furniture 設計空間的類別目錄的該介面，您可以使用*新增模型通訊協定*可讓使用者放置這些家具 3D 模型，從類別目錄。 一旦將放在世界裡，使用者可以移動、 調整大小，和在家中移除這些就像其他全像投影的 3D 模型。 這篇文章提供實作的概觀*新增模型通訊協定*，以便您可以開始讓裝飾他們的世界，以從您的應用程式或網站的 3D 物件的使用者。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>新增模型通訊協定</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="overview"></a>總覽

有 2 個步驟，以啟用在家用的 Windows Mixed Reality 的 3D 模型的位置：
1. [請確定您的 3D 模型適用於家用的 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。
2. 實作*新增模型通訊協定*在您的應用程式或網頁 （本文）。

## <a name="implementing-the-add-model-protocol"></a>實作*新增模型通訊協定*

一旦[相容的 3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)，您可以實作*新增模型通訊協定*藉由啟用下列 URI，從任何網頁或應用程式：

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

如果 URI 指向遠端資源，然後它會自動下載並放置在首頁。 本機資源會複製到混合的實境家中的應用程式資料資料夾，再放在首頁。 我們建議您設計您的體驗情況下，使用者可能同時執行的較舊版本的 [隱藏] 按鈕，或停用它的話不支援這項功能的 Windows 帳戶。 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>叫用*新增模型通訊協定*從通用 Windows 平台應用程式：

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>叫用*新增模型通訊協定*從網頁：

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>沈浸式 (VR) 耳機的考量

* 針對擬真 (VR) 耳機，混合實境入口網站不需要執行之前叫用*新增模型通訊協定*。 在此情況下，*新增模型通訊協定*會啟動混合實境入口網站，並讓直接其中耳機正在尋找當您將看見在首頁的混合實境中的物件。 
* 當叫用*新增模型通訊協定*從桌面與已執行的混合實境入口網站中，確定 耳機是"甦醒狀態 」。 如果沒有，則放置將會失敗。 

## <a name="see-also"></a>另請參閱

* [建立 3D 模型，使用 Windows Mixed Reality 在家中](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [瀏覽家用的 Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
