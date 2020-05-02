---
title: 什麼是混合實境？
description: 本文定義混合實境，並示範混合實境頻譜搭配簡單的 AR 和 VR 裝置以及 Windows Mixed Reality 裝置 (例如 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式頭戴裝置)。
author: brandonbray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: 混合實境, 全像攝影, ar, vr, mr, xr, 擴增實境, 虛擬實境, 說明
ms.localizationpriority: high
ms.openlocfilehash: 7b0dcbdb88f880d4c1632fae874ba6a610f023fb
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "81278046"
---
# <a name="what-is-mixed-reality"></a>什麼是混合實境？

![在 HoloLens 2 上手部指向和行動](images/02_MixedRealitySlashMixedReality.png)

混合實境是實體環境與數位世界混合的結果。 混合的實境是人類、電腦和環境互動的全新演進，並且解放了以前僅限於我們想像的可能性。 這是藉由提升電腦視覺、圖形處理能力、顯示器技術和輸入系統所達成。 「混合實境」  一詞最初是由 Paul Milgram 和 Fumio Kishino 在 1994 年的論文《[混合實境視覺顯示器分類法 (A Taxonomy of Mixed Reality Visual Displays)](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)》中提出。 他們的論文提出 *Virtuality Continuum* 的概念，並著重於分類法分類套用至顯示器的方式。 從那時起，混合實境便不只應用於顯示器。 還包含環境輸入、空間音效和位置。

![混合實境頻譜](images/mixedrealityspectrum-worlds.png)<br>
*影像：混合實境是實體環境與數位世界混合的結果。*

<br>

---

## <a name="environmental-input-and-perception"></a>環境輸入和認知

過去數十年來，已充分探索人類與電腦輸入之間的關聯性。 甚至還有一個廣為研究的專業領域，稱為「人機互動」  或 HCI。 人類輸入會透過各種不同的方式進行，包括鍵盤、滑鼠、觸控、筆跡、語音，甚至是 Kinect 的框架追蹤。

在感應器和處理方面的提升，逐漸使環境中的電腦輸入形成新的區域。 電腦與環境之間的互動是有效的環境理解或「感知」  。 因此，Windows 中顯示環境資訊的 API 名稱即稱為「[認知 API」](https://docs.microsoft.com/uwp/api/Windows.Perception)。 環境輸入會擷取諸多事物，像是使用者所處的位置 (例如[人頭追蹤](coordinate-systems.md))、表面和邊界 (例如[空間對應](spatial-mapping.md)和[場景理解](scene-understanding.md))、環境光源、環境音效、物件辨識和位置。

<br>

![顯示電腦、人類與環境之間互動的卞氏圖表](images/mixed-reality-venn-diagram-300px.png)<br> 
*影像：電腦、人類與環境之間的互動。*

<br>

現在，**電腦處理、人類輸入和環境輸入**這三個的組合，樹立了建立真正混合實境體驗的機會。 實體世界中的移動可以轉譯成數位世界中的移動。 實體世界的界限可能會影響數位世界中的應用程式體驗，例如遊戲進行。 如果沒有環境輸入，體驗就無法混合實體與數位實境。<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>混合實境頻譜

因為混合實境會混合實體和數位世界，這兩個實境就定義了頻譜的兩極，稱為 Virtuality Continuum。 為了簡單起見，我們將此稱為「混合實境頻譜」  。 在左側，是實體實境，也就是我們人類所在之處；在右側，則是對應的數位實境。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>擴增與虛擬實境

現今市場上大部分的行動電話幾乎都沒有環境理解功能。 因此，他們所提供的體驗無法混合實體和數位實境。 在實體世界的影片串流上重疊圖形的體驗即為「擴增實境」  。 遮蔽您的檢視來呈現數位體驗的體驗即為「虛擬實境」  。 如您所見，在這兩個極端之間的體驗，即為「混合實境」  ：
* 從實體世界開始，放置數位物件 (例如全像投影)，如同真實存在一般。
* 從實體世界開始，另一個人的數位表示法 -- [頭像] -- 顯示他們在留言時所處的位置。 換句話說，即為不同時間點表示非同步共同作業的體驗。
* 從數位世界開始，實體世界 (例如牆和傢俱) 的實體界限會以數位方式出現在體驗中，以協助使用者避免實體物件。


<br>

![混合實境頻譜](images/mixedrealityspectrum.png)<br>
*影像：混合實境頻譜*

<br>

現今提供的大部分擴增實境和虛擬實境產品，都代表此頻譜的一小部分。 不過，它們也是較大混合實境頻譜的子集。 Windows 10 以整個頻譜為基礎，並可將數位方式呈現的人員、環境和事物與真實世界混合。




## <a name="devices-and-experiences"></a>裝置和體驗


有兩種主要的裝置類型可提供 Windows Mixed Reality 體驗：
1. **全像攝影裝置。** 這些特性是由裝置將數位內容放在真實世界中的功能來表示，如同真實存在一般。
2. **沉浸式裝置。** 這些特性是由裝置建立「目前狀態」的功能來表示 -- 隱藏實體世界，並以數位體驗取代。

<table>
<tr>
<th width="30%"> 特性</th><th width="35%"> 全像攝影裝置</th><th width="35%"> 沉浸式裝置</th>
</tr><tr>
<td><strong>範例裝置</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>顯示器</strong></td><td> 透明顯示器。 讓使用者在穿戴頭戴式裝置時可看到實體環境。</td><td> 不透明顯示器。 在穿戴頭戴式裝置時封鎖實體環境。</td>
</tr><tr>
<td><strong>移動</strong></td><td> 完整的六度自由移動，包括旋轉和轉譯。</td><td> 完整的六度自由移動，包括旋轉和轉譯。</td>
</tr>
</table>



請注意，無論裝置是連線到其他電腦或以行動網卡連線到其他電腦 (透過 USB 纜線或 Wi-Fi) 或是獨立的 (未連線)，都不會反映裝置是否為全像攝影還是沉浸式。 當然，增加行動性的功能會帶來更好的體驗，且全像攝影和沉浸式裝置都可能是以行動網卡連線或是未連線的。


技術提升是已啟用混合實境體驗的功能。 目前沒有任何裝置可在整個頻譜中執行體驗。 不過，Windows 10 同時為裝置製造商和開發人員提供通用的混合實境平台。 現今的裝置可以支援混合實境頻譜內的特定範圍。 經過一段時間後，新的裝置將會擴充該範圍。 在未來，全像攝影裝置會變得更沉浸式，而沉浸式裝置會變得更全像攝影。

<br>

![混合實境頻譜中的裝置類型](images/Final_WhatIsMixedReality07.png)<br>
*影像：裝置在混合實境頻譜上的位置*

通常，最好能考量應用程式或遊戲開發人員想要建立的經驗類型。 這些體驗通常會以頻譜上的特定點或部分作為目標。 然後，開發人員應該考慮他們想要作為目標的裝置功能。 例如，仰賴實體世界的體驗在 HoloLens 上的效果最佳。
* **向左 (接近實體實境)。** 使用者仍然存在於其實體環境中，且永遠不會相信他們已離開該環境。
* **中間 (完全混合實境)。** 這些體驗混合了真實世界與數位世界。 看過[野蠻遊戲](https://en.wikipedia.org/wiki/Jumanji)這部電影的觀看者，可以調整故事中所出現房屋的實體結構與叢林環境的混合方式。
* **向右 (接近數位實境)。** 使用者會遇到完全數位的環境，且不會察覺周遭實體環境中發生的情況。


## <a name="see-also"></a>另請參閱

* [什麼是全像投影？](hologram.md)
* [了解混合實境的基本概念](index.md#understand-the-basics)
* [開始建立並建立原型](design.md)
* [了解工具和架構](development.md)

