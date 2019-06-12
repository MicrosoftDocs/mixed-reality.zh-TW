---
title: 在 Unity 中的文字
description: 若要在 Unity 中顯示文字，有兩種類型的文字元件，您可以使用-UI 文字和 3D 文字網狀結構。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality，設計、 控制項、 字型、 印刷樣式、 ui、 ux
ms.openlocfilehash: 7d40db2e0571e835e28e444c7921e1a086800936
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829968"
---
# <a name="text-in-unity"></a>在 Unity 中的文字

文字可以是其中一個最重要的元件，在全像攝影版的應用程式中。 若要在 Unity 中顯示文字，有三種您可以使用文字元件 — UI 文字、 3D 文字網狀結構，和文字 Mesh Pro。 依預設 UI 文字和 3D 文字網格看起來是模糊且太大。 您需要調整幾個變數，以取得明確的高品質文字 HoloLens 中具有可管理的大小。 藉由套用縮放比例，以取得適當的維度，使用 UI 文字和 3D 文字 Mesh 的元件時，您可以達到更好的呈現品質。

![如何取得聰明又美觀的文字](images/hug-text-02-640px.png)<br>
*在 Unity 中的模糊的預設文字*

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a>使用 Unity 的 3D 文字 （Text 網狀結構） 和 UI 文字

Unity 假設所有新增至場景的新項目 1 中的大小或 100%轉換小數位數，會轉譯為大約 1 公尺 HoloLens 上的 Unity 單位。 如果字型是週框方塊 3D TextMesh 隨附的預設位置的高度大約 1 公尺。

![使用 Unity 中的字型](images/640px-hug-text-03.png)<br>
*預設 Unity 3D 文字 (Text Mesh) 佔用 1 Unity 單位為 1 公尺*

<br>
大部分的視覺化設計工具會使用點來定義真實世界中的字型大小。 有大約 2835 (2,834.645666399962) 在 1 公尺的點。 根據點系統轉換為 1 公尺和 Unity 的預設文字 Mesh 字型大小為 13，13 除以 2835年等於 0.0046 (0.004586111116 很精確) 的簡單數學運算提供良好的標準擴展開始 （部分可能會想要為 0.005 捨入）。 調整文字物件或為這些值的容器不會只允許 1 對 1 轉換字型的大小在設計程式中，但也提供一種標準，因此您可以在您的經驗來維護一致性。

![Unity 3D 文字網格不同的字型大小](images/Text_In_Unity_Measurements1.png)<br>
*調整 Unity 3D 文字和 UI 文字值*

![Unity 3D 文字網格不同的字型大小](images/hug-text-05-1000px.png)<br>
*Unity 3D 文字網格最佳化的值*

<br>
當將 UI 或畫布的基礎的文字項目新增至場景，大小差異大於仍是。 在這兩個大小的差異是大約 1000年%，這會將縮放比例 0.00046 (0.0004586111116 很精確) 基礎的 UI 文字元件或超過 0.0005 的捨入的值。

![使用不同的動態像素，每個單位值的 unity UI 文字](images/hug-text-04-1000px.png)<br>
*Unity UI 文字，以最佳化的值*

<br>

>[!NOTE]
>任何字型的預設值可能會受到該字型或字型如何匯入至 Unity 的紋理大小。 這些測試所據以執行在 Unity 中的預設新細明體字型，以及其他匯入的一種字型。

## <a name="working-with-text-mesh-pro"></a>處理文字 Mesh Pro

使用 Unity 的文字 Mesh Pro，您可以保護的文字呈現品質。 它支援不論距離使用清晰的文字外框[SDF （簽署距離欄位）](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)技巧。 使用 3D 文字網格和 UI 文字上面使用的相同計算方法，我們可以找出適當的調整值，要使用傳統的印刷樣式端點。 由於預設 3D 大小 36 Mesh Pro 文字字型顯示 2.5 Unity Unit(2.5m) 的周框，我們可以使用縮放比例值 0.005 若要使用的點數大小。 文字 Mesh Pro UI 功能表底下有週框大小的 25 Unity Unit(25m) 預設值。 這會提供超過 0.0005 的縮放比例的值。

![Unity 3D 文字網格不同的字型大小](images/Text_In_Unity_Measurements2.png)<br>
*調整 Unity 3D 文字和 UI 文字值*

## <a name="recommended-text-size"></a>建議的文字大小
您可能已經想到，我們使用電腦或平板電腦裝置 （通常在 12 – 產生 32pt) 之間的類型大小的 2 公尺的距離看變得很小。 它取決於特性的每種字型，但一般情況下檢視角度和字型高度，以利閱讀建議的最小周圍 0.35°-0.4°/12.21-13.97mm 根據我們的使用者研究工作。 它是關於 35 40pt 上面介紹的縮放因數。 

在 0.45m(45cm) 幾近互動，最小易於閱讀字型檢視角度和高度是 0.4 °-0.5 ° / 3.14 – 3.9 mm。 它是關於 9 12pt 上面介紹的縮放因數。

![不久，到目前為止的互動範圍](images/typography-distance-1000px.jpg)
*內容在附近，遠的互動範圍*

### <a name="the-minimum-legible-font-size"></a>易於閱讀的字型大小下限
| 距離 | 檢視角度 | 文字高度 | 字型大小 |
|---------|---------|---------|---------|
| 45 cm （直接操作距離） | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>舒服地易於閱讀的字型大小
| 距離 | 檢視角度 | 文字高度 | 字型大小 |
|---------|---------|---------|---------|
| 45 cm （直接操作距離） | 0.65°-0.8° | 5.1-6.3mm | 14.47-17.8pt |
| 2m | 0.6°-0.75° | 20.9-26.2mm | 59.4-74.2pt |

Segoe UI （Windows 的預設字型） 也適用於大部分的情況。 不過，在避免使用 light 或半淺色字型系列較小，因為將震動精簡型的垂直筆劃，而且它會降低易讀性。 新式的字型，具有足夠的筆劃粗細正常運作。 比方說，新細明體新細明體看起來美觀和 HoloLens 中使用規則或粗體加權非常清晰。


![檢視角度](images/Text_In_Unity_ViewingAngle.jpg)
*檢視距離、 角度和文字的高度*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>明確的文字呈現品質與正確的維度

根據這些縮放係數，我們建立了[UI 文字與 3D 文字 Mesh 的文字 prefabs](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)。 開發人員可以使用這些 prefabs，以取得明確的文字和一致的字型大小。

![明確的文字呈現品質與正確的維度](images/hug-text-06-1000px.png)<br>
*明確的文字呈現品質與正確的維度*

## <a name="shader-with-occlusion-support"></a>阻擋支援的著色器

Unity 的預設字型材質不支援會受阻擋。 因為這個緣故，您會看到的文字物件後面預設。 我們已包含簡單[著色器，支援會受阻擋](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)。 下圖顯示 （左邊） 的預設字型資料的文字和具有適當的阻擋物 （右） 的文字。

![阻擋支援的著色器](images/hug-text-07-1000px.png)<br>
*阻擋支援的著色器*


## <a name="see-also"></a>另請參閱
* [在 MRTK 文字 Prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [印刷樣式](typography.md)

 
