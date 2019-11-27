---
title: 什麼是混合實境？
description: 本文會定義混合的事實，並示範簡單的 AR 和 VR 裝置，以及 Windows Mixed Reality 裝置（例如 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式耳機），並配合混合現實頻譜。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality，全像，ar，vr，mr，xr，增強的現實，虛擬實境，說明
ms.openlocfilehash: 65588902565ee0c5a1710f823311ccdecc23230e
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539564"
---
# <a name="what-is-mixed-reality"></a>什麼是混合實境？

![在 HoloLens 2 上實際操作點和認可](images/02_MixedRealitySlashMixedReality.png)

混合實境是實體環境與數位世界混合的結果。 混合的實境是人類、電腦和環境互動的全新演進，並且解放了以前僅限於我們想像的可能性。 這是藉由電腦視覺、圖形處理能力、顯示器技術和輸入系統的進展而達成的。 「*混合現實*」一詞原本是由 Paul Milgram 和 Fumio Kishino 「[混合現實視覺效果的分類法](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)」所引進的1994論文。 其論文引進了*virtuality continuum*的概念，並著重于如何套用分類法的分類。 從那時起，混合現實的應用程式會超出顯示範圍。 它也包含環境輸入、空間音效和位置。

![混合的現實頻譜](images/MixedRealitySpectrum-worlds.jpg)<br>
*混合現實是將實體世界與數位世界相結合的結果。*

<br>

---

## <a name="environmental-input-and-perception"></a>環境輸入和認知

過去幾年來，人類與電腦輸入之間的關聯性已經過充分的探索。 它甚至已經過廣泛研究的專業領域，稱為*人類電腦互動*或 HCI。 人類輸入會透過各種不同的方式進行，包括鍵盤、滑鼠、觸控、筆墨、語音，甚至是 Kinect 的框架追蹤。

在感應器和處理方面的改進，是從環境逐漸增加到電腦輸入的新區域。 電腦與環境之間的互動是有效的環境理解或*認知*。 因此，Windows 中顯示環境資訊的 API 名稱稱為「[認知 api](https://docs.microsoft.com/uwp/api/Windows.Perception)」。 環境輸入會在世界中（例如， [head 追蹤](coordinate-systems.md)）、表面和邊界（例如[空間對應](spatial-mapping.md)和[場景理解](scene-understanding.md)）、環境光源、環境音效、物件辨識等專案中，捕捉到人員的位置。和位置。

<br>



:::row:::
    :::column:::
        現在，所有三種**電腦處理、人類輸入和環境輸入**的組合，都能為您創造出真正的混合現實體驗。 透過實體世界的移動可以轉譯成數位世界中的移動。 實體世界的界限可能會影響數位世界中的應用程式體驗，例如遊戲播放。 如果沒有環境輸入，體驗就無法在實體和數位現實之間混合。<br>
        <br>
        *影像：電腦、人類和環境之間的互動。*
    :::column-end:::
        :::column:::
       ![顯示電腦、人類和環境之間互動的卞氏圖表](images/mixed-reality-venn-diagram-300px.png)<br> 
    :::column-end:::
:::row-end:::

<br>

---


## <a name="the-mixed-reality-spectrum"></a>混合現實頻譜

因為混合現實會混合實體和數位世界，所以這兩個現實會定義一系列稱為 virtuality continuum 的極座標。 為了簡單起見，我們將此稱為「*混合現實」頻譜*。 在左側，我們有實際的現實，也就是我們的存在;在右手邊，我們有對應的數位現實。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>增強與虛擬實境的比較

現今市場上大部分的行動電話幾乎都沒有環境理解功能。 因此，他們所提供的體驗無法在實體和數位現實之間混合。 在實體世界的影片串流上重迭圖形的體驗，會有更豐富的*現實*。 遮蔽您的觀點來呈現數位體驗的經驗，就是*虛擬實境*。 如您所見，在這兩個極端之間啟用的經驗，是*混合現實*的：
* 從實體世界開始，將數位物件（例如全息的影像）放在真正的處。
* 從實體世界開始，另一個人的數位標記法--[頭像]--顯示離開便箋時的位置。 換句話說，在不同時間點表示非同步共同作業的經驗。
* 從數位世界開始，實體世界（例如牆和傢俱）的實體界限會以數位方式出現在體驗中，以協助使用者避免實體物件。


<br>

![混合的現實頻譜](images/MixedRealitySpectrum.jpg)<br>
*混合現實頻譜*

<br>

現今提供的大部分增強的現實和虛擬實境產品，都代表此頻譜的一小部分。 不過，它們也是較大混合現實頻譜的子集。 Windows 10 以整個頻譜為基礎，並可讓人、地點和事物的數位代表與真實世界混合。




## <a name="devices-and-experiences"></a>裝置和體驗


有兩種主要的裝置類型可提供 Windows Mixed Reality 體驗：
1. **全像攝影裝置。** 這些特性是由裝置將數位內容放在真實世界中的功能來表示，就像真正的一樣。
2. **沉浸式裝置。** 這些特性是由裝置建立「目前狀態」的能力所組成--隱藏實體世界，並以數位體驗取代。

<table>
<tr>
<th width="20%"> 特性</th><th width="40%"> 全像攝影裝置</th><th width="40%"> 沉浸式裝置</th>
</tr><tr>
<td> 範例裝置</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows Mixed Reality 開發版<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> 顯示器</td><td> <i>查看顯示。</i> 可讓使用者在戴頭戴式裝置時查看實體環境。</td><td> <i>不透明的顯示。</i> 在戴頭戴式裝置時封鎖實體環境。</td>
</tr><tr>
<td> 引起</td><td> 完整的六度自由移動，包括旋轉和轉譯。</td><td> 完整的六度自由移動，包括旋轉和轉譯。</td>
</tr>
</table>

請注意，無論裝置是連線到其他電腦或行動網卡到另一部電腦（透過 USB 纜線或 Wi-fi）或是獨立的（非網路共用），都不會反映裝置是否為全像攝影或沉浸式。 當然，改善行動性的功能會導致更好的體驗，而且全像攝影和沉浸式裝置都可能是行動網卡或非網路共用。


技術進步是已啟用混合現實體驗的功能。 目前沒有任何可在整個頻譜中執行體驗的裝置。 不過，Windows 10 為裝置製造商和開發人員提供通用的混合現實平臺。 現今的裝置可以支援混合現實頻譜內的特定範圍。 經過一段時間後，新的裝置將會擴充該範圍。 未來，全像攝影的裝置會變得更沉浸，而沉浸式裝置會變得更好。

<br>

混合現實頻譜中的 ![裝置類型](images/MixedRealitySpectrum-devices.jpg)<br>
*其中的裝置存在於混合現實頻譜上*

通常，最好考慮應用程式或遊戲開發人員想要建立哪種類型的經驗。 這些體驗通常會以特定點或元件為目標。 然後，開發人員應該考慮他們想要作為目標的裝置功能。 比方說，依賴實體世界的經驗在 HoloLens 上的效果最佳。
* **朝左邊（接近實體現實）。** 使用者仍然存在於其實體環境中，而且永遠不會相信他們已離開該環境。
* **中間（完全混合的事實）。** 這些體驗 blend 了真實世界與數位世界。 看過電影[Jumanji](https://en.wikipedia.org/wiki/Jumanji)的觀看者，可以協調出故事所在的房屋實體結構與蛙鳴環境的混合方式。
* **向右（接近數位現實）。** 使用者會遇到完全數位的環境，而且不會察覺實體環境中發生的情況。


## <a name="see-also"></a>請參閱

* [什麼是全像投影？](hologram.md)
* [瞭解混合現實的基本概念](index.md#understand-the-basics)
* [開始建立和原型設計](design.md)
* [了解工具和架構](development.md)

