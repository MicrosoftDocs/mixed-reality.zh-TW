---
title: 在 Unity 中的文字
description: 若要在 Unity 中顯示文字，有兩種類型的文字元件，您可以使用-UI 文字和 3D 文字網狀結構。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計、 控制項、 字型、 印刷樣式、 ui、 ux
ms.openlocfilehash: 02f282ab80a44190d21d2dadefeb7a624c862d04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596362"
---
# <a name="text-in-unity"></a>在 Unity 中的文字

文字可以是其中一個最重要的元件，在全像攝影版的應用程式中。 若要在 Unity 中顯示文字，有兩種類型的文字元件，您可以使用-UI 文字和 3D 文字網狀結構。 依預設它們看起來是模糊且太大。 您需要調整幾個變數，以取得明確的高品質文字 HoloLens 中具有可管理的大小。 藉由套用縮放比例，以取得適當的維度，使用 UI 文字和 3D 文字 Mesh 的元件時，您可以達到更好的呈現品質。

![如何取得聰明又美觀的文字](images/hug-text-02-640px.png)<br>
*在 Unity 中的模糊的預設文字*

## <a name="working-with-fonts-in-unity"></a>使用 Unity 中的字型

Unity 假設所有新增至場景的新項目 1 中的大小或 100%轉換小數位數，會轉譯為大約 1 公尺 HoloLens 上的 Unity 單位。 如果字型是週框方塊 3D TextMesh 隨附的預設位置的高度大約 1 公尺。

![使用 Unity 中的字型](images/640px-hug-text-03.png)<br>
*預設 Unity 文字佔用 1 Unity 單位為 1 公尺*

<br>
大部分的視覺化設計工具會使用點來定義真實世界中的字型大小。 有大約 2835 (2,834.645666399962) 在 1 公尺的點。 根據點系統轉換為 1 公尺和 Unity 的預設文字 Mesh 字型大小為 13，13 除以 2835年等於 0.0046 (0.004586111116 很精確) 的簡單數學運算提供良好的標準擴展開始 （部分可能會想要為 0.005 捨入）。 調整文字物件或為這些值的容器不會只允許 1 對 1 轉換字型的大小在設計程式中，但也提供一種標準，讓您可以維護整個應用程式或遊戲的一致性。

![Unity 3D 文字網格不同的字型大小](images/hug-text-05-1000px.png)<br>
*Unity 3D 文字網格最佳化的值*

<br>
當將 UI 或畫布的基礎的文字項目新增至場景，大小差異大於仍是。 在這兩個大小的差異是大約 1000年%，這會將縮放比例 0.00046 (0.0004586111116 很精確) 基礎的 UI 文字元件或超過 0.0005 的捨入的值。

![使用不同的動態像素，每個單位值的 unity UI 文字](images/hug-text-04-1000px.png)<br>
*Unity UI 文字，以最佳化的值*

<br>

>[!NOTE]
>任何字型的預設值可能會受到該字型或字型如何匯入至 Unity 的紋理大小。 這些測試所據以執行在 Unity 中的預設新細明體字型，以及其他匯入的一種字型。

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>明確的文字呈現品質與正確的維度

根據這些縮放係數，我們建立了[兩個 prefabs-UI 文字和 3D 文字 Mesh](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)。 開發人員可以使用這些 prefabs，以取得明確的文字和一致的字型大小。

![明確的文字呈現品質與正確的維度](images/hug-text-06-1000px.png)<br>
*明確的文字呈現品質與正確的維度*

## <a name="shader-with-occlusion-support"></a>阻擋支援的著色器

Unity 的預設字型材質不支援會受阻擋。 因為這個緣故，您會看到的文字物件後面預設。 我們已包含簡單[著色器，支援會受阻擋](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders)。 下圖顯示 （左邊） 的預設字型資料的文字和具有適當的阻擋物 （右） 的文字。

![阻擋支援的著色器](images/hug-text-07-1000px.png)<br>
*阻擋支援的著色器*

## <a name="recommended-type-size"></a>建議的類型大小

您可能已經想到，我們使用電腦或平板電腦裝置 （通常在 12 – 產生 32pt) 之間的類型大小的 2 公尺的距離看變得很小。 這取決於每個字型的特性，但在一般情況下建議最小的類型大小，以利閱讀筆劃振動不在於 30pt，根據上面介紹的縮放比例。 如果您的應用程式應該使用更接近的距離，就可以使用較小的類型大小。 字型選擇功能，Segoe UI （Windows 的預設字型） 非常適合大部分情況。 不過，請避免使用 light 或半淺色字型 42pt 之下的類型大小，因為將震動精簡型的垂直筆劃，而且它會降低易讀性。 新式的字型，具有足夠的筆劃粗細正常運作。 比方說，新細明體新細明體看起來美觀和 HoloLens 中使用規則或粗體加權非常清晰。

![建議的類型大小](images/hug-text-08-1000px.png)<br>
*型別 ramp 範例*

## <a name="see-also"></a>另請參閱
* [在 MixedRealityToolkit 文字 Prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [Prefab 的範例文字版面配置和場景](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [Typography](typography.md)

 
