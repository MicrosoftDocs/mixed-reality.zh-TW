---
title: 農曆模組
description: LunarModule 是 Microsoft 的混合實境設計實驗室開放原始碼的範例應用程式。 與此專案中，您可以了解如何擴充 Hololens 的基底的筆勢，雙手追蹤和 Xbox 控制器輸入建立會反射式到 surface 對應和平面尋找的物件，實作簡單的功能表系統。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: 混合實境，範例應用程式，設計、 HoloLens 的 Windows
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595545"
---
# <a name="lunar-module"></a>農曆模組

>[!NOTE]
>這篇文章討論探勘的範例，我們已在中建立[混合實境設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)，我們分享我們所獲得的經驗相關的位置和建議混合實境應用程式開發。 當我們新的探索，就會持續改進我們的設計相關的文章和程式碼。

[農曆模組](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)是來自 Microsoft 的混合實境設計實驗室的開放原始碼的範例應用程式。 與此專案中，您可以了解如何擴充 Hololens 的基底的筆勢，雙手追蹤和 Xbox 控制器輸入建立會反射式到 surface 對應和平面尋找的物件，實作簡單的功能表系統。 所有專案的元件可供您自己的混合的實境應用程式體驗。

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>重新思考傳統體驗，如 Windows Mixed Reality

大氣中的高增加，讓我們依稀想起 Apollo 模組小船有條理地調查下方的鋸齒狀的地形。 我們並肩作戰試驗 spots 適合的登陸區域。 深度是棘手但幸好這趟旅程發生之前多次...

![從 Atari 的 1979年陰曆 Lander 原始介面](images/640px-atari-lunar-lander.png)<br>
*從 Atari 的 1979年陰曆 Lander 原始介面*

[以陰曆 Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game))是 arcade 傳統播放程式嘗試試驗 moon lander 到陰曆地形一般位置。 在 1970 年代出生的任何人都很有可能已在 arcade 花時間，黏附 plummeting 天上這個向量出貨至其眼睛。 播放程式就會瀏覽到所需的登陸區域其出貨地形會調整以顯示以漸進方式更多詳細資料。 成功表示登陸的水平和垂直速度的安全臨界值內。 點數登陸和剩餘的油量、 與根據登陸區域大小的倍數花費的時間。

遊戲，除了 arcade 紀元的遊戲帶不斷創新的控制項配置。 從最簡單的 4 向搖桿和按鈕組態 (圖示所示[Pac Man](https://en.wikipedia.org/wiki/Pac-Man)) 到 90 年代後期和 00 秒 （例如，在 golf 模擬器和滑軌射擊） 所示的高度特定且最複雜的配置。 以陰曆 Lander 機器中使用的輸入的配置是特別有趣，原因有兩個： 邊欄訴求與訓練活動。

![Atari 的陰曆 Lander 的 arcade 主控台](images/atariconsole.png)<br>
*Atari 的陰曆 Lander arcade 主控台*

為何 Atari 和許多其他遊戲公司決定重新思考輸入？

逐步解說 arcade 的孩子自然會像樣的最新、 flashiest 機器。 但陰曆 Lander 功能建立這項鷄 novel 輸入的 mechanic。

以陰曆 Lander 用於兩個按鈕旋轉太空船左邊和右邊和**推力桿**來控制的主要目的是產生出貨數量。 這個推桿可讓使用者採取一些手段規則搖桿無法提供特定層級。 它也是剛好是現代化的航空 cockpits 通用元件。 Atari 想要它們實際上試驗農曆模組感覺中的使用者將可享有陰曆 Lander。 這個概念稱為**tactile immersion**。

Tactile 深度是執行重複動作的感應式意見反應的體驗。 在此情況下，調整節流推桿和旋轉，請參閱我們的眼睛並耳朵聽的重複動作可協助連接播放程式的登陸的出貨的表面上的動作。 這個概念可以繫結心理概念的 「 流程 」。 在使用者是完全吸收中有正確的挑戰，並獎勵，混用的工作，或更簡單來說，它們是 「 在區域。 」

在論證上，在混合實境中的訓練活動的最重要的型別是空間訓練活動。 混合實境的重點是企圖欺騙自己以為這些數位物件存在於現實世界裡。 我們正在由全像投影合成在我們的周圍環境，在空間上沉浸在整個環境和體驗。 這並不表示我們無法仍採用其他類型的訓練活動在我們的經驗如同 Atari 一樣在陰曆 Lander tactile 訓練活動。

## <a name="designing-with-immersion"></a>設計與訓練活動

我們可能會以更新過的體積型的後方，以傳統 Atari 如何套用 tactile 深度呢？ 先解決輸入的配置，必須處理 3 維空間的遊戲建構。

![視覺化 HoloLens 中的介面對應](images/surfacemapping.png)<br>
*HoloLens 中以視覺化方式檢視空間的對應*

利用使用者的周圍環境，我們實際上會有無限的地形選項登陸我們農曆模組。 若要讓遊戲最類似原始的標題，使用者可能無法操作，然後放在其環境中的各種困難的登陸填補。

![要飛往農曆模組](images/640px-lm-hero.jpg)<br>
*要飛往農曆模組*

需要使用者了解輸入的配置、 控制出貨，並有小型的目標，以便登入是許多要求。 成功的遊戲體驗功能的挑戰，並獎勵，混用權限。 使用者應該能夠選擇難度等級，最簡單的模式只要求已成功抵達介面上的 使用者定義的區域中使用者掃描的 HoloLens。 一旦使用者取得的遊戲，他們接著可以迅速，困難度增加。

### <a name="adding-input-for-hand-gestures"></a>新增輸入手勢

HoloLens 基底的輸入已只有兩個筆勢-[空中點選和 Bloom](gestures.md)。 使用者不需要記住內容相關的細節或特定的筆勢的洗衣清單具彈性且易於了解，讓平台的介面。 時，系統可能只會公開這些兩種筆勢，為裝置的 HoloLens 可以追蹤兩個實際操作一次。 是我們的程式碼，以陰曆 Lander[沉浸式應用程式](app-model.md)這表示我們有能力以擴充的筆勢來運用兩指針，並新增我們自己令人愉快 tactile 農曆模組導覽讓基底的集合。

在原始的控制項配置，莫忘初衷**我們需要解決的主要目的是與旋轉**。 需要注意的是新的內容中的旋轉加入其他座標軸 (技術上兩個，但 Y 軸會登陸較不重要)。 兩個不同的出貨移動本身就對應至每一個指針：

![點選並拖曳 lander 上所有的三個軸的旋轉手勢](images/module-handdrag.gif)<br>
*點選並拖曳 lander 上所有的三個軸的旋轉手勢*

**主要目的是**

原始 arcade 機器上的推桿對應的值為小數位數，高槓桿已移動的更多的主要目的是已套用至 出貨。 這裡指出重要細微差別是，使用者可以採取其移交控制項，並維持所需的值。 我們實際上可以使用點選和拖曳的方式來達到相同的結果。 主要目的是值從零開始。 使用者點選並拖曳以增加值。 此時，他們可以讓移至進行維護。 點選並拖曳筆勢值的任何變更會從原始值的差異。

**旋轉**

這是有點棘手。 有全像攝影版"旋轉"的按鈕來點選讓可怕的體驗。 沒有實體控制項來運用，因此操作或處理 lander 本身的物件，代表 lander，都必須來自行為。 我們想出了使用點選並拖曳這讓使用者能夠有效地 「 推送和提取 」 方法方向在他們想要面對。 每當使用者點選，而且會保存，起始筆勢所在的空間中的點會變成旋轉的原點。 從來源將手的翻譯 （X，Y，Z） 的差異，並套用至 lander 旋轉值的差異。 或者形式更簡單*空間中的上一步拖曳左側 <>-權限，註冊 <>-向下]、 [下一頁 <>-據以旋轉太空船*。

因為 HoloLens 可以追蹤兩個實際操作，旋轉可以指派給右手邊時主要目的是受到左邊。 採取一些手段是驅動因素在這個遊戲中的成功。 *覺得*這些互動的是絕對的最高優先順序。 尤其是在 tactile 訓練活動的內容。 回應速度太快出貨不必要地難以可以操縱，雖然速度太慢的其中一個會要求使用者要 「 推送和提取 」 在太空船姿長的時間量。

### <a name="adding-input-for-game-controllers"></a>正在加入輸入遊戲控制器

HoloLens 上的手勢提供嶄新的細微的控制方法，但仍 'true' tactile 的意見反應，您從類比控制項取得缺乏。 連接 Xbox 遊戲控制器可讓這種情況下的 physicality 找回同時還能利用控制項隨身碟，保留細微的控制。

有多種方式來套用相對較簡單的控制項配置至 Xbox 控制器。 因為我們想要保持盡可能的情況下，設定原始 arcade 靠近**推力**最佳對應至觸發程序 按鈕。 這些按鈕是類比的控制項，這表示它們有多個簡單*開啟和關閉*所述，它們實際回應放在其上的壓力程度。 這會提供類似的建構，當做**推力桿**。 不同於原始遊戲和手動動作，此控制項將剪下 ship 的主要目的是之後使用者就會停止將壓力放在觸發程序。 它仍可讓使用者相同程度的採取一些手段原始 arcade 遊戲一樣。

![左搖桿會對應至偏航和回復，右搖桿會對應到講述並回復](images/thumbsticksidebyside.gif)<br>
*左搖桿會對應至偏航和回復;右搖桿會對應至推銷和復原*

雙重搖桿本身來控制的出貨旋轉。 不幸的是，有 3 個座標軸上的出貨可以旋轉和這兩個支援的兩個軸的兩個搖桿。 這種不符合表示任一一搖桿控制項一個軸;或搖桿座標軸的重疊。 第一種解決方案最終會覺得 「 已中斷 」，因為搖桿原本就是 blend 當地 X 和 Y 值。 第二種解決方案需要某些測試以查明哪些多餘的軸覺得最自然。 最後一個範例會使用*偏航*並*向前復原*（Y 軸和 X 軸） 的左搖桿，和*音調*和*彙*（Z 軸和 X 軸） 提供的權限搖桿。 這認為一樣最自然*回復*似乎也與獨立配對*偏航*和*字幅*。 附帶一提，使用的兩個搖桿*向前復原*也會發生循環值中; 的兩倍就有 do 迴圈 lander 很有趣。

此範例應用程式示範如何空間辨識和 tactile 訓練活動可能會大幅改變感謝 Windows Mixed Reality 的可延伸的輸入形式的體驗。 雖然陰曆 Lander 可能即將在時代的 40 年，概念以公開與 legs 小八邊形-將 live 下去。 當想像在未來，為何不會看到過去？

## <a name="technical-details"></a>技術詳細資料

您可以找到指令碼和 prefabs 農曆模組的範例應用程式上[混合實境設計 Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison-wesley Linville</b><br>UX 設計工具 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [動作控制站](motion-controllers.md)
* [筆勢](gestures.md)
* [混合的實境應用程式類型](types-of-mixed-reality-apps.md)
