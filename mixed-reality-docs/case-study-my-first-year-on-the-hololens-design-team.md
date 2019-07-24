---
title: 個案研究-我在 HoloLens 設計小組的第一年
description: 當我在2016年1月加入 HoloLens 設計團隊時, 從 2D flatland 到3D 世界的旅程已開始。
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 設計, 編輯, 個人
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873948"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>個案研究-我在 HoloLens 設計小組的第一年

當我在2016年1月加入 HoloLens 設計團隊時, 從 2D flatland 到3D 世界的旅程已開始。 在加入小組之前, 我在3D 設計方面的經驗非常少。 從單一步驟開始, 這就像是諺語的一趟旅程, 但在我的案例中, 第一個步驟是 leap 的:

![從2D 到3D 的飛躍](images/2D_to_3D-800px.gif)<br>
*從2D 到3D 的飛躍*

> *「我覺得我已經跳到駕駛基座, 而不知道如何推動汽車。我已害怕, 但卻非常專注。」*<br>
> : Hae 金先生

在過去一年, 我可以像我一樣快速地挑選技能和知識, 但是我還是有太多學習。 我在這裡寫了4個觀察影片教學課程, 記錄從2D 到3D 互動設計工具的轉換。 我希望我的體驗會讓其他設計人員更容易使用3D。

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>不錯的框架。 Hello 空間/diegetic UI

每當我設計海報、雜誌、網站或應用程式畫面時, 定義的框架 (通常是矩形) 就是每個問題的常數。 除非您是在 HoloLens 或其他的 VR 裝置中閱讀這篇文章, 否則您會從透過2D 畫面*的外部*, 安全地在框架內進行觀察。 內容不在您的外部。 不過, 混合現實耳機會使*框架消失*, 因此您會在內容空間中, 尋找並從內部流覽內容。

我在概念上已經瞭解這一點, 但是在一開始, 我犯了一個錯誤, 就是將2D 思考轉移到3D 空間。 這顯然無法正常運作, 因為3D 空間有自己獨特的屬性, 例如視圖變更 (根據使用者的前端移動) 和[不同的使用者緩和需求](https://www.youtube.com/watch?v=-606oZKLa_s/)(根據裝置的屬性, 以及使用它們的人)。 例如, 在 2D UI 設計空間中, 鎖定螢幕角落的 UI 元素是非常常見的模式, 但此抬頭顯示器 (Head 顯示) 樣式 UI 在 MR/VR 體驗中並不自然。它會阻礙使用者深度到空間, 並導致使用者 discomfort。 就像是在您的眼鏡上有一個令人討厭的灰塵, 那就是您要定生死來擺脫的。 在一段時間之後, 我瞭解到在3D 空間中放置內容變得更自然, 並新增主體鎖定行為, 讓內容以相對固定距離來追蹤使用者。

![主體-已鎖定](images/bodylockedtagalong.gif)<br>
*主體-已鎖定*

<br>

![世界-鎖定](images/worldlocked.gif)<br>
*世界-鎖定*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>分段絕佳的 Diegetic UI 範例

[Asobo Studio](http://www.asobostudio.com/)針對 HoloLens 所開發的第一人犯罪 Thriller 是[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8), 它會示範絕佳的 Diegetic UI。 在此遊戲中, 使用者會成為一個主要字元, 這是一種嘗試解決神秘問題的偵探。 在使用者的實體聊天室中解決此神秘 get 試想的 pivotal 線索, 通常會在虛構物件中內嵌, 而非其本身。 此 diegetic UI 比主體鎖定的 UI 更容易探索, 因此 Asobo 小組應變使用許多提示, 包括虛擬字元的注視方向、音效、光線和指南 (例如, 箭號指向線索的位置), 以吸引使用者的注意力。

![片段-Diegetic UI 範例](images/fragments-game-example-1.jpg)<br>
*片段-Diegetic UI 範例*

### <a name="observations-about-diegetic-ui"></a>Diegetic UI 的相關觀察

空間 UI (主體鎖定和全球鎖定) 和 diegetic UI 都有自己的優點和缺點。 我鼓勵設計人員嘗試盡可能多的 MR/VR 應用程式, 並為各種 UI 定位方法開發自己的瞭解和 sensibility。

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Skeuomorphism 和神奇互動的傳回

Skeuomorphism, 模仿真實世界物件圖形的數位介面, 在設計產業中的過去5–7年就已經「uncool」了。 當 Apple 終於提供了 iOS 7 的一般設計方式時, Skeuomorphism 最後就好像是介面設計方法。 但是, 新的 medium、MR/VR 耳機抵達市場, 而且似乎再次傳回 Skeuomorphism。 : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>作業模擬器:Skeuomorphic VR 設計的範例

[作業](http://jobsimulatorgame.com/)模擬器是[Owlchemy Labs](https://owlchemylabs.com/)所開發的比較古怪遊戲, 是 skeuomorphic VR 設計最受歡迎的其中一個範例。 在此遊戲中, 播放機會傳輸到未來, 機器人會將人取代為人, 並造訪博物館, 以體驗在四個不同工作中的其中一項執行常見的工作:Auto 技師修理、Gourmet Chef、Store 職員或 Office Worker。

Skeuomorphism 的優點很清楚。 此遊戲中熟悉的環境和物件可協助新的 VR 使用者更舒適, 並呈現在虛擬空間中。 它也會將熟悉的知識和行為與物件及其對應的實體反應產生關聯, 讓他們感到滿意。 比方說, 若要飲料咖啡, 人們只需要走一杯咖啡機器、按下按鈕、抓住杯把手, 然後把它朝向嘴, 就像在現實世界裡一樣。

![作業模擬器](images/job-simulator.gif)<br>
*作業模擬器*

因為 MR/VR 仍然是開發媒體, 所以必須使用某種程度的 skeuomorphism 來解釋 MR/VR 技術, 並將其引進給世界各地的大型物件。 此外, 使用 skeuomorphism 或實際標記法對於特定類型的應用程式 (例如, 外科或飛行模擬) 可能很有説明。 由於這些應用程式的目標是要開發和精簡可直接套用到真實世界的特定技能, 因此模擬的範圍愈接近真實世界, 知識的轉移就愈多。

請記住, skeuomorphism 只是一種方法。 MR/VR 世界的潛能遠遠大於此, 而設計人員應該努力建立神奇的超自然互動, 這是在 MR/VR 世界中唯一可行的新 affordances。 一開始, 請考慮將神奇的動力新增至一般物件, 讓使用者能夠滿足其基本需求, 包括 teleportation 和 omniscience。

![Doraemon 的神奇門 (左) 和 Ruby slippers (right)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon 的神奇門 (左) 和 ruby slippers (right)*

### <a name="observations-about-skeuomorphism-in-vr"></a>VR 中的 skeuomorphism 觀察

從 Doraemon 的「隨處門」中, 將盎司的 Wizard 中的「Ruby Slippers」「Maurader 的地圖」放在 Harry 哈利波特中, 這是在熱門神奇中具有為數眾多電源小說的一般物件範例。 這些神奇物件可協助我們將真實世界和絕佳的連線視覺化, 這兩者之間的關係。 請記住, 在設計神奇或 surreal 物件時, 必須在功能與娛樂之間取得平衡。 請注意, 只是為了 novelty 而建立純粹神奇的誘惑。

## <a name="understanding-different-input-methods"></a>瞭解不同的輸入法

當我針對2D 媒體設計時, 必須專注于觸控、滑鼠和鍵盤互動以進行輸入。 在 MR/VR 設計空間中, 我們的主體會變成介面, 而使用者可以使用更廣泛的輸入方法, 包括語音、注視、手勢、 [6 dof 控制器](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)和手套, 以提供更直覺且與虛擬物件的直接連接。

![HoloLens 中的可用輸入](images/inputs.jpg)<br>
*HoloLens 中的可用輸入*

> *「一切都適用于其他專案, 而且最糟的東西。」*<br>
> \- [Bill Buxton](https://www.billbuxton.com/)

例如, 在 HMD 裝置上使用「裸機」和「相機」感應器的手勢輸入, 可以讓使用者離開控制器或戴 sweaty 手套, 但經常使用會導致實體疲勞 (a. k gorilla arm)。 此外, 使用者也必須將他們的手放在視線內;如果相機看不到手中, 就無法使用手。

語音輸入非常適合用於遍歷複雜的工作, 因為它可讓使用者使用一個命令來剪下嵌套功能表 (例如「顯示 Laika studio 所製作的電影」), 並在結合其他樣式 (例如, 「臉部」命令將使用者正在尋找使用者的全息影像。 不過, 語音輸入可能不適用於雜訊環境, 也可能不適合非常無訊息的空間。

除了手勢和語音以外, 已保留的追蹤控制器 (例如, Oculus go touch、Vive 等) 是非常常用的輸入法, 因為它們很容易使用、精確、運用人員的[proprioception](https://en.wikipedia.org/wiki/Proprioception), 以及提供被動的 haptic 提示。不過, 這些好處的代價是無法進行實際操作, 也不能使用完整的手指追蹤。

![Senso (Left) 和 Manus VR (Right)](images/senso-and-manus-vr.jpg)<br>
*Senso (Left) 和 Manus VR (Right)*

除了控制器的熱門, 手套也會因為 MR/VR 波而再次獲得動力。 最新的大腦/主意輸入已開始將 EEG 或 EMG 感應器整合到耳機 (例如[MINDMAZE VR](http://www.mindmaze.com/)), 以取得虛擬環境介面的吸引力。

### <a name="observations-about-input-methods"></a>關於輸入法的觀察

這些只是 MR/VR 市場中可用輸入裝置的範例。 他們會繼續持續增加, 直到產業成熟並同意最佳做法為止。 在那之前, 設計人員應該留意新的輸入裝置, 並在其特定專案的特定輸入方法中妥善精通。 設計人員需要在限制範圍內尋找創意的解決方案, 同時也扮演裝置的優勢。

## <a name="sketch-the-scene-and-test-in-the-headset"></a>在耳機中繪製場景並進行測試

當我在2D 中工作時, 大部分的內容都是直接草繪。 不過, 在混合現實空間不足的情況下。 我必須草擬整個場景, 才能更想像使用者和虛擬物件之間的關聯性。 為了協助我的空間考慮, 我開始在[電影院 4d](https://www.maxon.net/en/products/cinema-4d/overview/)中草擬場景, 有時會在[Maya](http://www.autodesk.com/products/maya/overview/)中建立用於原型的簡單資產。 我在加入 HoloLens 團隊之前從未用過這兩種程式, 我仍然是新手, 但使用這些3D 程式絕對可以協助我熟悉新的術語, 例如[著色器](https://en.wikipedia.org/wiki/Shader)和[IK (反向運動)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)。

**「無論我在3D 中畫出場景的緊密程度為何, 耳機的實際體驗幾乎都不會與草圖相同。這就是為什麼要測試目標耳機中的場景是很重要的。」— Hae 金**

針對 HoloLens 原型, 我試著從[混合現實教學](tutorials.md)課程開始著手的所有教學課程。 接著, 我開始使用 Microsoft 為開發人員提供的[HoloToolkit](https://github.com/Microsoft/HoloToolkit-Unity/) , 加速開發全像攝影應用程式。 當我停滯了一些東西時, 我將我的問題張貼到[HoloLens 問題 & 解答論壇](https://forums.hololens.com/categories/questions-and-answers/)。

在取得 HoloLens 原型的基本瞭解之後, 我想要自行讓其他非半截原型。 所以我製作了一段影片教學課程, 教您如何使用 HoloLens 開發簡單的 projectile。 我會簡短說明基本概念, 因此即使您在 HoloLens 開發方面沒有任何經驗, 您還是應該能夠遵循。

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*我為非程式設計人員提供了這個簡單的教學課程, 像我一樣。*

針對 VR 原型設計, 我在[Vr Dev School](http://learn.vrdev.school/)取得了課程, 也在 Lynda.com 上[建立了3d 內容以供虛擬實境](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/)之用。 VR Dev school 提供我更深入的編碼知識, 而 Lynda 課程為我提供了建立 VR 資產的簡短簡介。

## <a name="take-the-leap"></a>採用 leap

一年前, 我認為這一切都有點龐大。 現在我可以告訴您, 這是 100% 值得付出的努力。 MR/VR 仍然非常年輕, 而且有很多有趣的可能等待實現。 我覺得靈感和幸運能夠在設計未來的一小部分玩。 我希望您會在旅程圖中加入我的3D 空間!

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae 金先生</b><br>UX 設計工具@Microsoft</td>
</tr>
</table>

 
