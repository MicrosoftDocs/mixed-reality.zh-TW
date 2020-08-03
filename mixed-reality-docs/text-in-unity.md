---
title: Unity 中的文字
description: 若要在 Unity 中顯示文字，您可以使用兩種類型的文字元件： UI 文字和3D 文字網格。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality，設計，控制項，字型，印刷樣式，ui，ux
ms.openlocfilehash: 63f0992a4623cf91c1b9c62c4ebf30de12529515
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476940"
---
# <a name="text-in-unity"></a>Unity 中的文字

文字是全像攝影應用程式中最重要的元件之一。 若要在 Unity 中顯示文字，有三種類型的文字元件可供您使用： UI 文字、3D 文本網格和文本網格專業人員。 根據預設，UI 文字和3D 文本網格會呈現模糊且太大。 您需要調整一些變數，以取得在 HoloLens 中具有可管理大小的清晰、高品質文字。 藉由在使用 UI 文字和3D 文本網格元件時，套用縮放比例來取得適當的維度，您可以達到更佳的轉譯品質。

![如何取得清晰且美觀的文字](images/hug-text-02-640px.png)<br>
*Unity 中的模糊預設文字*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>使用 Unity 的3D 文字（文本網格）和 UI 文字

Unity 假設所有新增至場景的新專案都是大小的1個 Unity 單位，或100% 的轉換小數值，這在 HoloLens 上轉譯為約1個計量。 在字型的案例中，3D TextMesh 的周框方塊預設會出現在最高1計量的高度。

![在 Unity 中使用字型](images/640px-hug-text-03.png)<br>
*Default Unity 3D Text （文本網格）佔用1個 Unity 單位，也就是1個計量*

<br>
大部分的視覺效果設計工具會使用點來定義真實世界中的字型大小。 1計量中大約有2835（2，834.645666399962）點。 根據 [將系統轉換成1個計量] 和 [Unity 的預設文本網格字型大小] 為13，[13] 的簡單數學運算除以2835等於0.0046 （0.004586111116 是精確的），這可提供良好的標準調整來開始使用（有些可能會想要舍入0.005）。 將文字物件或容器調整為這些值，不只允許在設計程式中轉換1:1 的字型大小，同時也提供標準，讓您可以在整個體驗中維持一致性。

![具有不同字型大小的 Unity 3D 文本網格](images/Text_In_Unity_Measurements1.png)<br>
*調整 Unity 3D 文字和 UI 文字的值*

<br>

![具有不同字型大小的 Unity 3D 文本網格](images/hug-text-05-1000px.png)<br>
*具有優化值的 Unity 3D 文本網格*

<br>
將 UI 或畫布型文字專案新增至場景時，[大小] 差異仍然會大於。 這兩種大小的差異大約是1000%，這會將以 UI 為基礎之文字元件的縮放比例，帶入0.00046 （0.0004586111116 是精確的）或四捨五入值的0.0005。

![具有每個單位值不同動態圖元的 Unity UI 文字](images/hug-text-04-1000px.png)<br>
*具有優化值的 Unity UI 文字*

<br>

>[!NOTE]
>任何字型的預設值可能會受到該字型的材質大小，或字型匯入 Unity 的方式所影響。 這些測試是根據 Unity 中的預設 Arial 字型，以及另一個已匯入的字型來執行。

## <a name="working-with-text-mesh-pro"></a>使用文本網格 Pro

使用 Unity 的文本網格 Pro，您可以保護文字轉譯品質。 不論使用 [[帶正負號距離] 欄位（.sdf）](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)技術的距離為何，它都支援簡潔的文字外框。 針對3D 文字網格和 UI 文字，使用我們先前使用的相同計算方法，我們可以尋找適當的縮放值以搭配傳統的印刷點使用。 由於預設的3D 文字網格 Pro 字型（大小為36）的周框大小為 2.5 Unity 單位（2.5 m），因此我們可以使用調整值0.005 來取得點大小。 UI 功能表底下的文本網格 Pro 具有25個 Unity 單位（25m）的預設周框大小。 這可為我們提供0.0005 的調整值。

![具有不同字型大小的 Unity 3D 文本網格](images/Text_In_Unity_Measurements2.png)<br>
*調整 Unity 3D 文字和 UI 文字的值*

## <a name="recommended-text-size"></a>建議的文字大小
如您所見，我們在 PC 或 tablet 裝置上使用的大小（通常介於12–32pt 填補之間）看起來相當小，距離2計量。 這取決於每個字型的特性，但一般來說，建議的最小觀賞角度和可讀性的字型高度是以我們的使用者研究研究為基礎的0.35 °-0.4 °/12.21-13.97mm。 大約 35-40pt，並有上述的縮放因數。 

若要在 0.45 m （45cm）附近互動，最小的可感知字型的視圖角度和高度是0.4 °-0.5 °/3.14 – 3.9 mm。 其大約為 9-12pt，並具有上述的縮放比例。

![近距離和遠處的互動範圍 ](images/typography-distance-1000px.jpg)
 *內容*

### <a name="the-minimum-legible-font-size"></a>最小的清晰字型大小
| 距離 | 視角 | 文字高度 | 字型大小 |
|---------|---------|---------|---------|
| 45cm （直接操作距離） | 0.4 °-0.5 ° | 3.14 –3.9 毫米 | 8.9 – 11.13 pt |
| 2m | 0.35 °-0.4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>舒適的字型大小
| 距離 | 視角 | 文字高度 | 字型大小 |
|---------|---------|---------|---------|
| 45cm （直接操作距離） | 0.65 °-0.8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2m | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |

Segoe UI （Windows 的預設字型）在大多數情況下都很好用。 不過，請避免使用大小較小的淡或半透明字型系列，因為精簡的垂直筆劃將會震動，且會降低可讀性。 具有足夠筆觸粗細的新式字型運作良好。 例如，Helvetica 和 Arial 的外觀美觀，在 HoloLens 中具有一般或粗權數。


![查看角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *視圖距離、角度和文字高度*

## <a name="text-with-mixed-reality-toolkit-v2"></a>混合現實工具組 v2 的文字

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>具有適當維度的銳利文字轉譯品質

根據這些縮放因素，我們建立[了具有 UI 文字和3D 文字網格的文字 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)。 開發人員可以使用這些 prefabs 來取得清晰的文字和一致的字型大小。

![具有適當維度的銳利文字轉譯品質](images/hug-text-06-1000px.png)<br>
*具有適當維度的銳利文字轉譯品質*

### <a name="shader-with-occlusion-support"></a>具有遮蔽支援的著色器

Unity 的預設字型材質不支援遮蔽。 因此，根據預設，您會看到物件後面的文字。 我們已包含[支援遮蔽的簡單著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MRTK/Core/StandardAssets/Shaders/Text3DShader.shader)。 下圖顯示具有預設字型材質（左）的文字，以及具有適當遮蔽的文字（right）。

![具有遮蔽支援的著色器](images/hug-text-07-1000px.png)<br>
*具有遮蔽支援的著色器*


## <a name="see-also"></a>請參閱
* [MRTK 中的文字 Prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [印刷樣式](typography.md)

 
