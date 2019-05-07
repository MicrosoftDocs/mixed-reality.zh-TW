---
title: 案例研究-我的第一年 HoloLens 上設計小組
description: 3D 世界時我加入 HoloLens 設計團隊在 2016 年 1 月，我從 2D flatland 的旅程。
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 HoloLens、 設計、 編輯、 個人
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873948"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>案例研究-我的第一年 HoloLens 上設計小組

3D 世界時我加入 HoloLens 設計團隊在 2016 年 1 月，我從 2D flatland 的旅程。 加入小組之前，我會在 3D 的設計有極少的體驗。 它就像中文諺語，關於從單一步驟中，但在我的案例的第一個步驟是閏年有 1000 英哩的旅程 ！

![從 2D 採取躍進 3d](images/2D_to_3D-800px.gif)<br>
*從 2D 採取躍進 3d*

> *「 我覺得好像我必須運用管權，而不需要知道如何駕馭。我已爆滿和害怕得，但非常聚焦。 」*<br>
> — Hae Jin Lee

在過去一年，我選擇技術和知識以最快速度性別，但仍有許多需要了。 在這裡，我寫了 4 個觀察值增加記錄我轉換來自 2D 到 3D 的互動設計工具的影片教學課程。 我希望我的經驗會激發採取 3D 轉換的其他設計工具。

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>失望，後會有期框架。 Hello 空間 / diegetic UI

每當我在設計海報、 雜誌、 網站或應用程式畫面，在定義的範圍內 （通常是矩形） 已針對每個問題的常數。 除非您正在閱讀這篇文章中的 HoloLens 或其他 VR 裝置，您均*想要從外部*透過安全地保護在範圍內的 2D 螢幕。 內容是您的外部。 不過，混合實境*消除框架*，因此您的內容的空間中尋找及逐步從內到外的內容。

我了解這在概念上，但一開始我犯了直接傳送到 3D 空間的 2D 思考。 顯然沒有正常運作，因為 3D 空間有它自己唯一的內容，例如檢視變更 （根據使用者的磁頭移動） 和[不同的需求，為使用者緩和](https://www.youtube.com/watch?v=-606oZKLa_s/)（根據裝置和人類使用的屬性它們）。 比方說，2D 的 UI 設計空間中鎖定到螢幕的角落的 UI 項目是很常見的模式，但此抬頭顯示器 （Head 增加顯示器） 樣式 UI 不覺得自然 MR/VR 體驗;它會防礙到空間的使用者訓練活動，並會導致使用者 discomfort。 就像在您已迫不及待想要去除您眼鏡惱人的灰塵物件。 經過一段時間，我已了解您感覺更自然放置在 3D 空間中的內容，並新增可讓內容遵循相對固定的距離的使用者主體鎖定行為。

![Body-locked](images/bodylockedtagalong.gif)<br>
*Body-locked*

<br>

![World-locked](images/worldlocked.gif)<br>
*World-locked*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>片段：舉例來說，Diegetic 的絶佳 UI

[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)，所開發的第一人稱 crime thriller [Asobo Studio](http://www.asobostudio.com/) HoloLens 示範更好的 Diegetic UI。 在這個遊戲中，使用者會成為主要的字元，嘗試解決是個謎偵測。 Pivotal 的線索來解決此神秘取得使用者的實體空間中執行，並內嵌在虛構的物件，而不是現有靠自己會經常。 此 diegetic UI 通常會比主體鎖定的 UI，不易搜尋，因此 Asobo 小組巧妙地使用很多提示，包括虛擬字元視線方向、 音效、 光線及輔助線 （例如箭號指向線索的位置） 來擷取使用者的注意力。

![片段-Diegetic UI 範例](images/fragments-game-example-1.jpg)<br>
*片段-Diegetic UI 範例*

### <a name="observations-about-diegetic-ui"></a>關於 diegetic UI 的觀察值

空間 （兩者主體鎖定和世界鎖定） 的 UI 和 diegetic UI 有自己的優點和缺點。 建議盡可能的情況下，試用數量 MR/VR 應用程式和開發自己的了解和 sensibility 定位方法的各種 ui 設計工具。

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>傳回的 skeuomorphism 和神奇的互動

Skeuomorphism，數位介面，以模擬真實世界物件的形狀已"uncool 「 過去 5 – 7 年來，在設計產業。 當 Apple 最後會提供在 iOS 7 中的一般程式設計的方式時，似乎 Skeuomorphism 是最後無作用為介面的設計方法。 但是，新的媒體，MR/VR 耳機已抵達市場並似乎 Skeuomorphism 傳回一次。 : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>作業模擬器：Skeuomorphic VR 設計的範例

[作業模擬器](http://jobsimulatorgame.com/)，由古怪的遊戲開發[Owlchemy 實驗室](https://owlchemylabs.com/)是其中一個最常見的範例，skeuomorphic VR 設計。 在這個遊戲中，玩家會傳輸未來其中機器人取代人類，並讓使用者瀏覽博物館體驗它看似執行單調的工作，其中四個不同的作業：自動技師，美食 Chef、 存放區 Clerk 或辦公室工作。

Skeuomorphism 的優點是清除。 熟悉的環境和這個遊戲中的物件可協助新 VR 使用者感受更舒適且存在虛擬空間中。 它也可讓他們覺得他們所熟悉的知識和行為關聯物件和其對應的實體反應可以控制。 比方說，要喝杯咖啡，人員只需要引導咖啡、 按下按鈕、 抓取的 cup 控點和傾斜針對其說話一樣會在真實世界中。

![作業模擬器](images/job-simulator.gif)<br>
*作業模擬器*

因為 MR/VR 仍在開發的媒體中，使用 skeuomorphism 程度是為您揭開 MR/VR 技術，以及將它連接到全球觀眾所需。 此外，使用 skeuomorphism 或實際的表示法會有益處的應用程式，例如手術或飛行模擬的特定類型。 由於這些應用程式的目標是要發展及精進可直接套用在真實世界中的特定技術，越接近模擬是以真實世界中，越轉移知識。

請記住該 skeuomorphism 是只有一個方法。 MR/VR 世界的潛力就遠大於，以及設計工具應該致力於建立神奇的超自然互動 — MR/VR 世界中是唯一可能的新提供。 為開始，請考慮在一般的物件，讓使用者能夠滿足其需求基本項目的加入 powers 神奇 — 包括屏障和神。

![（左） Doraemon 的神奇的媒體櫃門和 Ruby slippers(right)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*（左） Doraemon 的神奇的媒體櫃門和 ruby slippers(right)*

### <a name="observations-about-skeuomorphism-in-vr"></a>關於在 VR skeuomorphism 的觀察值

從 「 隨處機門"Doraemon，仙蹤哈利波特居然中的"Maurader 的對應 」 中的"Ruby Slippers 」 中的神奇的強大的一般物件範例有很多熱門故事中。 這些神奇的物件可協助我們以視覺化方式檢視真實世界與超棒，什麼是之間可能之間的連線。 請記住在設計神奇或 surreal 功能和娛樂之間取得平衡需要其中一個物件。 請注意建立純粹只是為了新奇的起見神奇的誘惑。

## <a name="understanding-different-input-methods"></a>了解不同的輸入的方法

當我針對 2D 中型而設計的時我將焦點放在觸控、 滑鼠及鍵盤輸入的互動。 在 MR/VR 設計空間中，我們的內文會變成介面和使用者就能夠使用更廣泛的選取範圍的輸入法： 包括語音、 視線、 手勢[6 dof 控制器](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)，和手套承受更直覺式且直接的連線使用虛擬物件。

![HoloLens 上可用的輸入](images/inputs.jpg)<br>
*HoloLens 上可用的輸入*

> *「 所有項目是什麼項目，最佳與最差的其他項目 」。*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

比方說，HMD 裝置上使用裸機手動與數位相機感應器輸入筆勢會釋出使用者手動從持有控制站或穿著 sweaty 手套，但經常使用可能會導致實體疲勞 (又稱為 gorilla arm)。 此外，使用者必須保留內的視野，其指針如果相機看不到指針，就無法使用指針。

語音輸入很適合周遊複雜的工作，因為它可讓使用者能夠透過單一命令的巢狀功能表剪下 (例如，"Show me 電影所 Laika studio。")，也非常符合經濟效益時加上其他的強制回應性 (例如，"面臨我 」 命令將全像使用者查看朝向使用者）。 不過，語音輸入不可能有很多雜訊的環境中正常運作，或可能不適當的非常寧靜的空間中。

除了筆勢和語音，掌上型追蹤控制站 （例如，Oculus 觸控，Vive 等） 是非常熱門的輸入的法，因為它們是容易使用、 正確運用人民[proprioception](https://en.wikipedia.org/wiki/Proprioception)，並提供 haptic 被動的提示。不過，這些優點會犧牲無法裸機手並使用完整的手指追蹤。

![Senso （左） 和 Manus VR(Right)](images/senso-and-manus-vr.jpg)<br>
*Senso （左） 和 Manus VR （右）*

雖然不受歡迎做為控制站，手套也日漸獲得注意再次感謝 MR/VR wave 的趨勢。 最近，腦/心輸入已開始能夠吸引目光為適用於虛擬環境的介面，藉由整合耳機 EEG 或 EMG 感應器 (例如[MindMaze VR](http://www.mindmaze.com/))。

### <a name="observations-about-input-methods"></a>輸入方法的相關的觀察值

這些是只輸入裝置的可用 MR/VR 的市場中的範例。 它們會繼續不斷增加，直到業界成熟且同意根據最佳作法。 在那之前，應該隨時留意新的輸入裝置的設計工具，並將其是很熟悉針對其特定專案的特定輸入方法中。 設計工具需要具創意的解決方案，以裝置的優點也播放時的限制內的查詢。

## <a name="sketch-the-scene-and-test-in-the-headset"></a>草圖場景，並在耳機中測試

我曾在 2D 中，我大部分勾勒出內容。 不過，在混合的實境沒有足夠的空間。 我必須勾勒出整個場景方向，以進一步假設使用者和虛擬物件之間的關聯性。 為了幫助我空間的想法，我開始草擬場景[杜比劇院效果 4d](https://www.maxon.net/en/products/cinema-4d/overview/)有時候會建立簡單資產中建立原型並[Maya](http://www.autodesk.com/products/maya/overview/)。 我有之前從未使用過其中任何一個程式加入 HoloLens 團隊和我仍然是新手，但使用這些 3D 程式明確地幫助我熟悉新的術語，例如[著色器](https://en.wikipedia.org/wiki/Shader)和[IK （反向運動）](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)。

**「 無論程度我勾勒出 3d 場景，耳機在實際的經驗是幾乎不會草圖相同。所以請務必測試在場景中目標耳機。 」 — Hae Jin Lee**

我試著 HoloLens 原型設計、 在的所有教學課程[混合實境教學課程](tutorials.md)啟動。 然後我開始玩[HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) Microsoft 提供給開發人員加速開發的全像攝影版的應用程式。 當我遇到問題的結果時，我把問題張貼至[HoloLens 問題與解答論壇](https://forums.hololens.com/categories/questions-and-answers/)。

之後取得的 HoloLens 原型設計的基本了解，我想要讓其他非位程式設計師在自己的原型。 所以我有所教導如何開發使用 HoloLens 簡單彈藥影片教學課程。 我簡要說明基本概念，因此甚至如果您曾經零 HoloLens 開發中，您應該能夠跟著做。

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*我做這個簡單的教學課程適用於非程式設計人員等自己。*

我花了 VR 原型設計、 參加課程[VR 開發學校](http://learn.vrdev.school/)也花了[3D 的內容建立的虛擬實境](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/)在 Lynda.com。 VR 開發學校提供我更多撰寫程式碼的深度知識中以及 Lynda 課程提供我 VR 建立資產的不錯簡短介紹。

## <a name="take-the-leap"></a>需要大幅改進

一年前，我覺得這一切都已不知所措。 現在我可以告訴您它是值得花時間的 100%。 MR/VR 仍然是非常年輕的媒體，並有很多有趣的可能性，等候實現。 我覺得啟發而幸運能夠播放設計未來的一小部分。 我希望您會將我一起踏上到 3D 空間的旅程 ！

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>UX 設計工具 @Microsoft</td>
</tr>
</table>

 
