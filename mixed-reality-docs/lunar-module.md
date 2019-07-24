---
title: 月球模組
description: LunarModule 是 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。 透過此專案, 您可以瞭解如何使用兩個右手的追蹤和 Xbox controller 輸入來擴充 Hololens 的基底手勢、建立會回應表面對應和平面尋找並實行簡單功能表系統的物件。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 範例應用程式, 設計, HoloLens
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515995"
---
# <a name="lunar-module"></a>月球模組

>[!NOTE]
>本文討論我們在[混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例, 這是我們分享我們學習的相關資訊, 並提供混合現實應用程式開發的建議。 我們的設計相關文章和程式碼將會隨著我們進行新的探索而演進。

[陰曆模組](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)是 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。 透過此專案, 您可以瞭解如何使用兩個右手的追蹤和 Xbox controller 輸入來擴充 Hololens 的基底手勢、建立會回應表面對應和平面尋找並實行簡單功能表系統的物件。 所有專案的元件都可以在您自己的混合現實應用程式體驗中使用。

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>重新思考 Windows Mixed Reality 的傳統體驗

在大氣中的高, Apollo 模組的小型出貨想起會有條理地調查下面的鋸齒狀地形。 我們的 fearless 試驗點是適當的登陸區域。 下降是棘手但幸好, 這種旅程已經過了許多次 。

![來自 Atari 1979 陰曆 Lander 的原始介面](images/640px-atari-lunar-lander.png)<br>
*來自 Atari 1979 陰曆 Lander 的原始介面*

[陰曆 Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game))是 arcade 傳統, 玩家會嘗試試驗月球 Lander, 進入農曆地形的平面。 在1970年的任何人, 在 arcade 中有很多時間都花了好幾個小時, 並將其眼睛粘附到這個向量從天空出貨 plummeting。 當玩家導覽其出貨到所需的登陸區域時, 地形會調整以顯示更多詳細資料。 成功表示在水準和垂直速度的安全臨界值內登陸。 系統會根據登陸區域的大小, 針對花費在登陸和剩餘燃料的時間取得點數。

除了遊戲之外, 遊戲的 arcade 時代也帶來了控制項配置的持續創新。 從最簡單的4向搖桿和按鈕設定 (出現在 iconic [Pac](https://en.wikipedia.org/wiki/Pac-Man)), 到晚期90年代和 00s (例如高爾夫球模擬器和鐵路玩射擊中的) 中所見到的高度特定和複雜的配置。 在陰曆 Lander 機器中使用的輸入配置, 特別是有趣, 原因有兩個: 路緣吸引人和深度。

![Atari 的陰曆 Lander 的 arcade 主控台](images/atariconsole.png)<br>
*Atari 的陰曆 Lander arcade 主控台*

為什麼 Atari 和其他許多遊戲公司決定重新思考輸入？

最新的 flashiest 機器自然會感到十分好奇一間 arcade 的孩子。 但陰曆 Lander 提供 novel 的輸入技師修理, 可讓您從更多功能中勇敢面對考驗。

陰曆 Lander 使用兩個按鈕來旋轉向左和向右鍵, 而**天生拉杆**則可控制出貨所產生的天生量。 此杠杆可讓使用者 finesse 一般搖桿無法提供的特定層級。 這也是新式航空考核中心的萬用群組件。 Atari 希望陰曆 Lander immerse 使用者, 覺得他們其實在試驗陰曆課程模組。 這個概念稱為**觸覺深度**。

觸覺深度是感應式意見反應以執行重複動作的經驗。 在此情況下, 調整調節杆和旋轉的重複性動作 (我們的眼睛會看到, 而我們的耳聽得到) 可協助將播放程式連接到月球表面上的登陸。 這個概念可以系結至「flow」的心理概念。 使用者完全吸收在具有適當混合挑戰和報酬的工作中, 或更單純地說, 他們就是「在此區域中」。

當然, 混合現實中最明顯的深度類型是空間深度。 整個混合現實的重點是要欺騙自己, 相信這些數位物件存在於現實世界中。 我們會在我們的環境中合成全像投影, 在整個環境和經驗中, 空間可以沉浸。 這並不表示我們還是不能在我們的經驗中運用其他類型的深度, 如同 Atari 在農曆 Lander 中觸覺深度。

## <a name="designing-with-immersion"></a>使用深度設計

如何將觸覺深度套用至 Atari 傳統的已更新體積型 sequel？ 在處理輸入配置之前, 必須先處理3d 空間的遊戲結構。

![將 HoloLens 中的表面對應視覺化](images/surfacemapping.png)<br>
*視覺化 HoloLens 中的空間對應*

藉由運用使用者的環境, 我們實際上有無限的地形選項可用於登陸我們的陰曆課程模組。 若要讓遊戲與原始標題最相似, 使用者可能會在其環境中操作和放置不同問題的登陸 pad。

![飛行陰曆課程模組](images/640px-lm-hero.jpg)<br>
*飛行陰曆課程模組*

需要使用者學習輸入配置、控制出貨, 而且有一個小型目標是要尋求的。 成功的遊戲體驗具有適當的挑戰和報酬組合。 使用者應該能夠選擇一層困難, 其中最簡單的模式就是要求使用者成功地進入 HoloLens 掃描之介面上的使用者定義區域。 一旦使用者取得遊戲的「停止回應」, 他們就可以在迅速地建立時看到更多的難度。

### <a name="adding-input-for-hand-gestures"></a>新增右手手勢的輸入

HoloLens 基底輸入只有兩個手勢[, 也](gestures.md)就是 Bloom。 使用者不需要記住內容上的細微差異或特定手勢的總清單, 讓平臺的介面既多樣化又容易學習。 雖然系統可能只會公開這兩個手勢, 但 HoloLens 作為裝置能夠一次追蹤兩個手。 我們的程式碼到農曆的 Lander 是一種[沉浸式應用程式](app-model.md), 這表示我們可以擴充一組基本手勢, 以運用兩個手, 並新增我們的令人愉快觸覺表示的陰曆模組導覽。

回顧一下原始的控制項配置,**我們需要解決天生和旋轉的**問題。 要注意的是, 新內容中的旋轉會加入額外的軸 (技術上為二, 但 Y 軸對登陸而言較不重要)。 兩個不同的出貨移動自然會使自己能夠彼此對應:

![在所有三個軸上, 按住並拖曳手勢以旋轉 lander](images/module-handdrag.gif)<br>
*在所有三個軸上, 按住並拖曳手勢以旋轉 lander*

**天生**

原始 arcade 機器上的拉杆會對應至值的小數值, 而移動杆已移至出貨的天生愈高。 這裡要指出的一項重要的細微之處是, 使用者可以拿掉控制項並維護所需的值。 我們可以有效地使用點擊和拖曳行為來達到相同的結果。 天生值從零開始。 使用者點擊並拖曳以增加值。 此時, 他們可以繼續維護它。 任何點擊和拖曳手勢值的變更, 都是與原始值的差異。

**旋轉**

這會稍微複雜一點。 讓全像投影的「旋轉」按鈕變得更豐富的體驗。 沒有可運用的實體控制項, 因此行為必須來自于代表 lander 的物件或 lander 本身的操作。 我們提出了使用點按和拖曳的方法, 可讓使用者以他們想要的方向有效地「推送並提取」。 每當使用者按下並按住時, 筆勢起始的空間就會變成旋轉的原點。 從原點拖曳會轉換手轉譯的差異 (X、Y、Z), 並將其套用至 lander 旋轉值的差異。 更簡單地說, 向*左拖曳 <-> right, 向上 <-> 向下、向前 <-在空格中向後 > 會相應旋轉出貨*。

因為 HoloLens 可以追蹤兩個手, 所以可以在天生由左側控制時, 將旋轉指派給右手邊。 Finesse 是此遊戲中成功的驅動因素。 這些互動的*風格*是絕對最高的優先順序。 尤其是在觸覺深度的內容中。 有太多反應的出貨會不必要地進行操作, 而速度太慢時, 使用者必須在出貨時「推送並提取」一段滑雪的時間。

### <a name="adding-input-for-game-controllers"></a>新增遊戲控制器的輸入

雖然 HoloLens 上的手勢提供了微調控制項的 novel 方法, 但還是有一些從類比控制項取得的「true」觸覺意見反應。 連接 Xbox 遊戲控制器可讓您回頭瞭解這種 physicality, 同時利用控制杆來保留精細的控制。

有多種方式可將相對直接的控制項配置套用至 Xbox 控制器。 由於我們正嘗試盡可能接近原始 arcade 設定, 因此**天生**對應最適合 [觸發程式] 按鈕。 這些按鈕是類比控制項, 這表示它們的 [*開啟] 和 [關閉*] 狀態都很簡單, 它們實際上會回應壓力的程度。 這會提供類似的結構做為**天生杠杆**。 不同于原始遊戲和手勢, 此控制項會在使用者停止觸發程式的壓力時, 剪下出貨的天生。 它仍然會為使用者提供與原始 arcade 遊戲相同程度的 finesse。

![左側的操縱杆會對應至偏擺和變換, 右杆會對應至音調並變換](images/thumbsticksidebyside.gif)<br>
*左側的操縱杆會對應到偏擺並變換;右側的操縱杆會對應至音調並變換*

雙重 thumbsticks 自然就能控制出貨的旋轉。 可惜的是, 出貨可以旋轉3個軸, 兩個 thumbsticks 都支援兩個軸。 這種不相符的意思是一個操縱杆控制一個軸;或是 thumbsticks 的座標軸重迭。 先前的解決方案最終感覺「中斷」, 因為 thumbsticks 原本就會混合其本機 X 和 Y 值。 後者的解決方案需要進行一些測試, 以找出哪些重複的軸覺得最自然。 最後一個範例會針對左側的操縱杆使用*偏擺*和變換 (Y 和 X 軸), 並針對右側的操縱杆使用*音調*和變換 (Z 和 X 軸)。 這覺得最自然的是 , 隨著*偏擺*和*螺距*的變換也是獨立配對。 就這一點而言, 同時使用 thumbsticks 進行變換也會發生兩倍的旋轉值;讓 lander do 迴圈變得非常有趣。

這個範例應用程式會示範空間辨識和觸覺深度如何大幅改變體驗, 因為這是 Windows Mixed Reality 的可擴充輸入形式。 雖然農曆 Lander 的年齡可能接近40年, 但使用該小型的八邊形所公開的概念也會永久存留。 想像未來, 為什麼看不到過去？

## <a name="technical-details"></a>技術詳細資料

您可以在[混合現實設計實驗室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)上找到適用于農曆模組範例應用程式的腳本和 prefabs。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>UX 設計工具@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [運動控制器](motion-controllers.md)
* [筆勢](gestures.md)
* [混合實境應用程式類型](types-of-mixed-reality-apps.md)
