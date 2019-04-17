---
title: HoloLens 參考資料模式
description: HoloLens 上使用參考資料模式，應用程式可以存取重要的裝置感應器資料流 （深度、 追蹤、 環境和 IR 反射率）。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 參考資料模式、 cv、 rs4、 電腦視覺、 參考資料、 HoloLens
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591120"
---
# <a name="hololens-research-mode"></a>HoloLens 參考資料模式

> [!NOTE]
> 這項功能已加入的一部分[Windows 10 April 2018 Update](release-notes-april-2018.md)的 HoloLens，並不適用於較早的版本。

參考資料模式是在裝置提供應用程式存取金鑰的感應器的 HoloLens 的新功能。 它們包括：
- 四個追蹤對應建築和前端的追蹤系統使用的數位相機的環境。
- 兩個版本的深度相機資料 – 一個用於高頻率 (30 FPS) 深度接近感應，常用的手中追蹤，另一個則用於低頻率 (也就是 1 FPS) 遠深度感應，目前使用空間的對應，
- IR-反射率資料流，用來計算深度，但本身的價值，因為這些映像從 HoloLens 照明標幟及合理受到環境光線 HoloLens 的兩個版本。

![參考資料模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)<br>
*混合的實境的擷取會顯示在參考資料模式中使用的八個感應器資料流的測試應用程式*

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> 參考資料模式</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a>之前使用參考資料模式

參考資料模式也稱為： 適合學術和產業研究人員嘗試在電腦視景和機器人的欄位中的新概念。  參考資料模式並不適用於將整個企業中部署或可在 Microsoft Store 應用程式。 參考資料模式可降低您的裝置的安全性，而消耗更多的電池電力，比正常作業的原因。 Microsoft 不認可任何未來的裝置上支援此模式中。 因此，我們建議您用它來開發及測試新的想法;不過，您將無法廣泛部署的應用程式，使用參考資料模式，或有任何的保證，讓它將繼續在未來的硬體上運作。

## <a name="enabling-research-mode"></a>啟用參考資料模式

參考資料模式是開發人員模式下的子模式。 您必須先啟用開發人員模式中設定應用程式 (**設定 > 更新與安全性 > 適用於開發人員**):

1. 將 「 使用開發人員功能 」 設定為**上**
2. 將 [啟用裝置入口網站] 設定為**上**

然後使用 連線到您的 HoloLens，相同的 Wi-fi 網路的網頁瀏覽器瀏覽至您 HoloLens 的 IP 位址 (一貫**設定 > 網路和網際網路 > Wi-fi > 硬體屬性**)。 這是[裝置入口網站](using-the-windows-device-portal.md)，，您會看到入口網站的 「 系統 」 一節中的 「 參考資料模式 」 的頁面：

![研究 HoloLens 裝置入口網站的 [模式] 索引的標籤](images/ResearchModeDevPortal.png)<br>
*HoloLens 裝置入口網站中的參考資料模式*

選取之後**允許感應器資料流存取**，您需要重新啟動 HoloLens。 從裝置入口網站中，在 "Power"功能表項目在頁面頂端，您可以執行這項操作。

一旦重新啟動您的裝置之後，已透過裝置入口網站中載入的應用程式應該能夠存取參考資料模式資料流。

## <a name="using-sensor-data-in-your-apps"></a>在您的應用程式中使用感應器資料

應用程式可以存取所開啟的感應器資料流資料[媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)完全相同的方式存取相片及視訊攝影機資料流中的資料流。 

HoloLens 的開發工作的所有 Api 也都可在 參考資料模式。 特別是，應用程式可以知道精確 HoloLens 所在 6DoF 空間中每個感應器畫面格擷取時間點。

顯示存取各種參考資料模式資料流的方式、 如何使用內建函式和 extrinsics，以及如何將記錄資料流的範例應用程式可用於[HoloLensForCV GitHub 存放庫](https://github.com/Microsoft/HoloLensForCV)。

## <a name="known-issues"></a>已知問題

請參閱[問題追蹤程式](https://github.com/Microsoft/HololensForCV/issues)HoloLensForCV 存放庫中。

## <a name="see-also"></a>另請參閱

* [Microsoft 媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 存放庫](https://github.com/Microsoft/HoloLensForCV)
* [使用 Windows Device Portal](using-the-windows-device-portal.md)
