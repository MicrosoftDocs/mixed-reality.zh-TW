---
title: 什麼被混合實境？
description: 本文定義混合的實境，並示範簡單的 AR 及 VR 裝置，以及 Windows Mixed Reality 裝置，例如 Microsoft HoloLens 和 Windows Mixed Reality 沈浸式耳機，以及混合的實境頻譜位於其中。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: 混合的實境，全像攝影版、 ar、 vr、 mr、 xr、 擴增的實境、 虛擬實境、 說明
ms.openlocfilehash: 3f6000b3d700d7c13f1efa13a81561464f8fdad1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597010"
---
# <a name="what-is-mixed-reality"></a>什麼被混合實境？

混合的實境是混合現實與數位世界的結果。 混合的實境是下一代演進，人類看得、 電腦和環境的互動，並解除鎖定，之前只有我們 imaginations 的可能性。 它可大幅提升，在電腦視覺、 圖形化的處理能力、 顯示技術和輸入的系統。 詞彙*混合實境*由 Paul Milgram 和 Fumio Kishino 原本引入 1994年 （英文） 中"[分類的混合實境視覺顯示](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)。 」 其紙張導入的概念*virtuality 連續體*並著重於套用至的分類法分類的顯示方式。 從那時起的混合實境應用程式會顯示更多，但也包含環境的輸入、 空間的聲音，以及位置。

## <a name="environmental-input-and-perception"></a>環境的輸入和感覺

![Venn 圖表，顯示電腦、 人類和環境之間的互動](images/mixed-reality-venn-diagram-300px.png)<br> 

過去幾個數十年來輸入電腦的輸入之間的關聯性已也探索了。 甚至還有稱為廣泛研究專業領域*人工電腦互動*或 HCI。 輸入會透過各種方式，包括鍵盤、 滑鼠、 touch、 筆墨、 語音及甚至 Kinect 骨架追蹤。

在感應器與處理方面的改進，讓上升的電腦輸入新的區域從環境。 電腦和環境之間的互動是有效的環境了解，或是*perception*。 因此稱為顯示環境的資訊的 Windows 中的 API 名稱[perception Api](https://docs.microsoft.com/uwp/api/Windows.Perception)。 環境的輸入擷取之類的世界中的個人位置 (例如[前端追蹤](coordinate-systems.md))，介面和界限 (例如[空間對應](spatial-mapping.md)和[空間了解](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md))，環境光源、 環境的音效、 物件辨識和位置。

現在，處理所有的三個 – 電腦的組合，人性化的輸入和環境的輸入-設定來建立，則為 true 的混合的實境體驗的機會。 透過真實世界的移動可以轉譯為數位世界中移動。 在真實世界的界限可能會影響應用程式體驗，例如遊戲，數位世界中。 不需要環境的輸入經驗無法 blend 之間的實體與數位現實情況。

## <a name="the-mixed-reality-spectrum"></a>混合的實境範圍

混合的實境是真實世界的數位世界混用，因為這些兩個的現實情況會定義稱為 virtuality 連續體的範圍極座標圖的結尾。 為了簡單起見，我們將它作為*混合的實境頻譜*。 在左手邊我們人類的我們存在的實體現實。 然後在右手邊有相對應的數位現實。

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

現今市場上大部分的行動電話都有一些不到環境了解功能。 因此，它們提供的體驗不能混用實體與數位現況之間。 重疊的真實世界的視訊資料流上的圖形體驗*擴增實境*，和 occlude 呈現的數位體驗您的檢視體驗*虛擬實境*。 如您所見，這兩項極端之間啟用體驗已*混合實境*:
* 從開始真實世界中，放置在數位的物件，例如雷射，如同它是真的有。
* 開頭為真實世界中，另一個人的數位表示 – avatar – 顯示它們已在其中釐離開資訊時的位置。 換句話說，體驗表示非同步的共同作業在不同時間點的時間。
* 從開始數位世界，實體界限從真實世界中，例如牆壁和 furniture，就會出現數位內體驗，可協助使用者避免實體的物件。

![混合的實境範圍](images/mixed-reality-spectrum-550px.png)

最擴增的實境和虛擬實境供應項目可立即代表這個範圍非常小的一部分。 是，不過，較大的混合的實境範圍子集。 Windows 10 使用納入考量，廣泛所建置，並允許透明混色的人員、 位置及物品與真實世界的數位表示法。

![混合的實境範圍中的裝置類型](images/mixed-reality-spectrum-device-types-550px.png)

有兩種類型的裝置可提供 Windows Mixed Reality 體驗：
1. **全像攝影版的裝置。** 這些特性會放置在真實世界的數位內容，就好像真的有裝置的能力。
2. **沈浸式裝置。** 這些被以建立 「 目前 」 – 隱藏實體世界，並以數位體驗取代了解裝置的能力。

<table>
<tr>
<th width="20%"> 特性</th><th width="40%"> 全像攝影版的裝置</th><th width="40%"> 沈浸式裝置</th>
</tr><tr>
<td> 範例裝置</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows 混合實境 Development 版<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> 顯示器</td><td> <i>透明顯示。</i> 可讓使用者看到同時頭戴耳機的實體環境。</td><td> <i>不透明的顯示。</i> 實體環境，同時頭戴耳機的區塊。</td>
</tr><tr>
<td> 移動</td><td> 完整的六個--的-自由度的資料移動、 旋轉和平移。</td><td> 完整的六個--的-自由度的資料移動、 旋轉和平移。</td>
</tr>
</table>

請注意，裝置是否連線到或行動網卡 （透過 USB 纜線或 Wi-fi） 不同的電腦或獨立的 (untethered) 會反映裝置是全像攝影版或沈浸式。 當然，無法行動網卡或 untethered 改善行動的潛在客戶對更好的經驗與全像攝影版和沈浸式裝置的功能。

## <a name="devices-and-experiences"></a>裝置和體驗

技術演進是已啟用混合的實境體驗的內容。 沒有任何裝置目前可跨整個範圍中，執行體驗不過，Windows 10 提供通用的混合的實境平台為裝置製造商和開發人員。 裝置現在可以支援特定範圍內的混合的實境範圍，並經過一段時間，新的裝置應該展開該範圍內。 在未來，全像攝影版的裝置會變成更沈浸式，而且沈浸式裝置會變成更全像攝影版。

![裝置上混合的實境範圍配置的位置](images/mixed-reality-spectrum-device-placement-550px.png)

通常，最好考慮何種體驗的應用程式或遊戲的開發人員想要建立。 特定點或範圍上的組件，通常會以目標的體驗。 然後，開發人員應該考慮他們想要為目標的裝置的功能。 比方說，真實世界所依賴的體驗將會執行最佳 HoloLens 上。
* **往左 （靠近實體實際上）。** 使用者仍然會在其實體環境中存在，且永遠不會認為它們已離開該環境。
* **在中間的 （完全混合實境） 中。** 這些經驗完全混合現實世界裡，數位世界。 看過的電影的檢視器[Jumanji](https://en.wikipedia.org/wiki/Jumanji)可以協調的房子劇本發生的所在的實體結構混合對叢林環境的方式。
* **針對 （靠近數位實境） 的權限。** 使用者體驗完全數位的環境，並會注意到在其周圍的實體環境中可能發生的狀況。


## <a name="see-also"></a>另請參閱
* [API 參考：Windows.Perception](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [API 參考：Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [API 參考：Windows.Perception.Spatial.Surfaces](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
