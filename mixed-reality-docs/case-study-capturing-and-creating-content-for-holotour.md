---
title: 案例研究-捕捉及建立 HoloTour 的內容
description: HoloTour for Microsoft HoloLens 為全球各地的 iconic 地點提供沉浸式3D 個人導覽。
author: DannyAskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour、HoloLens、Windows Mixed Reality
ms.openlocfilehash: 6c9e5f44c439310883c8b0271187a7b2263b0854
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63518190"
---
# <a name="case-study---capturing-and-creating-content-for-holotour"></a>案例研究-捕捉及建立 HoloTour 的內容

HoloTour for Microsoft HoloLens 為全球各地的 iconic 地點提供沉浸式3D 個人導覽。 身為設計人員、演出者、生產者、音訊設計師和處理此專案的開發人員, 建立知名位置的 convincingly 真正3D 呈現, 會採用獨特的創意與技術 wizardry blend。

## <a name="the-tech"></a>技術

有了 HoloTour, 我們想要讓人們能夠在自己的生活室中, 流覽一些全球最令人驚奇的目的地, 像是秘魯的[毀損 Machu Picchu](https://en.wikipedia.org/wiki/Machu_Picchu) , 或在義大利的現代化日[Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) 。 我們的團隊將其目標設為「讓您感到滿意」 HoloTour。 所需的經驗不僅僅是圖片或影片。 藉由運用 HoloLens 的獨特顯示、追蹤和音訊技術, 我們相信我們可以將您傳輸到另一個位置。 我們需要為我們流覽的每個位置, 捕獲焦點轉向、音效和3d 幾何, 然後在應用程式內重新建立。

若要這麼做, 我們需要具有方向性音訊捕獲的360數位相機 rig。 它必須以極高的解析度來捕捉, 讓素材在 HoloLens 上播放時看起來很清晰, 而且攝影機必須定位在一起, 以減少裝訂成品。 我們想要完整的球形涵蓋範圍, 而不只是在範圍內, 也不只是在您的上方和下方。 Rig 也必須是可移植的, 才能讓我們在世界各地使用。 我們評估了現成可用的選項, 並實現它們不足以實現我們的願景, 這可能是因為解決方案、成本或大小。 如果找不到符合我們需求的相機 rig, 我們就必須自行建立一個。

### <a name="building-the-rig"></a>建立 rig

第一版 (從紙箱、Velcro、管道磁帶, 以及 14 GoPro 攝影機) 是 MacGyver 會很榮幸的東西。 從低端解決方案審視到自訂製造的 rig 之後, GoPro 攝影機最終是最適合我們的選擇, 因為它們既小型又實惠, 而且具有便於使用的記憶體儲存體。 較小的外型規格特別重要, 因為它允許我們將相機放在一起, 也就是攝影機之間的距離, 而裝訂成品就越小。 我們獨特的攝影機相片順序讓我們能夠取得完整的球體涵蓋範圍,*加上*足夠的重迭, 以智慧方式對齊相機, 並在裝訂過程中順暢地使用某些成品。

利用 HoloLens 的[空間音效](spatial-sound.md)功能, 對建立 convincingly 真正的沉浸式體驗非常重要。 我們使用的四個麥克風陣列放在一張位於其上的攝影機底下, 這會以四個方向從攝影機的位置捕捉音效, 提供足夠的資訊, 在我們的幕後建立空間音效。

![我們的360數位相機 rig 已設定為在 Pantheon 外 filming。](images/camera-pantheon-200px.png)

我們的360數位相機 rig 已設定為在 Pantheon 外 filming。 


我們已藉由將自製的 rig 帶到 Rattlesnake 附近的凸緣來測試, 並在走去加加頂端捕捉景象。 結果雖比您今天在 HoloTour 中看到的還大, 但我們相信我們的 rig 設計已經夠好, 讓您覺得自己的工作就是如此。

我們已將 Velcro 和紙箱的 rig 升級為3D 列印的攝影機, 並購買 GoPro 攝影機的外部電池套件, 以簡化電池管理。 然後再進行更廣泛的測試, 往下往三藩市, 建立城市的 coast 和 iconic 黃金閘道的縮圖。 這是我們在 HoloTour 中流覽的大部分位置所使用的相機 rig。

![Machu Picchu 中的360°攝影機 rig filming。](images/camera-machu-pichu-500px.png)

Machu Picchu 中的360°攝影機 rig filming。 


## <a name="behind-the-scenes"></a>幕後

在 filming 之前, 我們需要先找出我們想要包含在虛擬導覽上的位置。 「羅馬」是我們要寄送的第一個位置, 我們想要正確地取得, 所以我們決定要事先進行 scouting 的旅程。 我們傳送了六個人 (包括演出者、設計人員和生產者) 的團隊, 讓我們親自造訪我們所考慮的網站。 旅程大約有9天–2.5 用於旅遊, filming 的其餘部分。 (針對 Machu Picchu, 我們選擇不進行 scout 行程, 事先研究並預約幾天的 filming)。

在羅馬期間, 小組會拍攝每個領域的相片, 並記下有趣的事實以及實際的考慮, 例如, 出差到每個地點的困難程度, 以及因為 crowds 或限制而導致電影的困難程度。 這聽起來可能像是假, 但這是很多工作。 早上幾天就會開始, 而且在晚上不會停機。 每晚會上傳素材, 讓小組回到西雅圖進行審查。 

![我們的「我們的 capture」是以羅馬。](images/holotour-filming-crew-rome-500px.jpg) 

我們的「我們的 capture」是以羅馬。 


Scout 行程完成後, 就會針對實際的 filming 進行最後的計畫。 這需要一份詳細的清單, 其中列出我們要在哪一天和何時進行電影。 每日海外的費用很高, 因此必須有效率地進行這些行程。 我們以羅馬方式預約了指南和處理常式, 以協助我們和在日落後的每一天完全使用。 我們需要取得最佳的素材, 才能讓您感到滿意。

### <a name="capturing-the-video"></a>正在捕獲影片

在 capture 期間執行幾個簡單的作業, 可以讓後續處理作業更容易。 例如, 每當您將多個相機中的影像結合在一起時, 最後就會有視覺成品, 因為每個相機的觀點都略有不同。 較接近的物件是相機、視圖之間的差異愈大, 而裝訂成品也會比較大。 以下是將問題視覺化的簡單方法: 將您的 thumb 放在臉部前方, 並只以一眼查看。 立即切換眼睛。 您會看到您的捲動方塊顯示為相對於背景的移動。 如果您從臉部中更遠地離開您的 thumb 並重複實驗, 您的 thumb 會變得較少。 這種明顯的移動與我們面臨的縫合問題類似:您的眼睛就像我們的攝影機一樣, 看不到完全相同的影像, 因為它們是以較小的距離隔開。

因為在 filming 時可以更輕鬆地防止最差的成品, 而不是在後置處理中修正它們, 所以我們試著讓人們和東西遠離相機, 而不需要將特寫物件拼接在一起。 維護攝影機的大型清除, 可能是我們在進行升級時所面臨的最大挑戰之一, 因此我們必須有創意才能使其正常執行。 使用本機指南是管理 crowds 的一大説明, 但我們也發現使用符號 (有時也是小型的圓錐或 bean 包) 將我們的 filming 空間標示為合理的效果, 特別是因為我們只需要在每個位置取得少量的素材。 取得良好 capture 的最佳方式, 通常是在早上的初期抵達, 大部分的人都是在這之前。

一些其他實用的 capture 技術直接來自傳統的電影實務。 例如, 我們在所有相機上都使用了色彩更正卡, 並已捕獲材質的參照相片, 以及我們稍後可能需要的物件。 

![顯示色彩校正卡的 Machu Picchu 粗略剪下。](images/rough-cut-machu-picchu-500px.png)

在進行裝訂之前, Pantheon 素材的粗略剪下。

### <a name="processing-the-video"></a>處理影片

捕捉360°內容只是第一個步驟, 需要進行許多處理, 才能將我們所捕捉到的原始攝影機素材轉換成您在 HoloTour 中看到的最終資產。 當我們回到家裡之後, 我們需要從14個不同的相機摘要中拍攝影片, 並將其轉換成具有最少成品的單一連續影片。 我們的美工小組使用數種工具來結合和波蘭文已捕捉的素材, 我們開發了管線, 盡可能將處理優化。 此素材必須拼接在一起、校正顏色, 然後再複合以移除干擾性的元素和成品, 或是新增生命與運動的補充隨身, 而且其目標是要增強這種實際的外觀。

![在進行裝訂之前, Pantheon 素材的粗略剪下。](images/rough-cut-pantheon-500px.png)

在進行裝訂之前, Pantheon 素材的粗略剪下。 


為了將影片結合在一起, 我們使用了稱為[PTGui](http://www.ptgui.com/)的工具, 並將它整合到我們的處理管線中。 在後置處理過程中, 我們會從影片中解壓縮仍然是畫面格, 並找到適合其中一個畫面格的拼接圖樣。 然後, 我們會將該模式套用至我們所撰寫的自訂外掛程式, 讓我們的影片演出者能夠直接微調和調整裝訂模式, 同時在效果後進行組合。 

![PTGui 的螢幕擷取畫面, 其中顯示拼接 Pantheon 的素材。](images/stitching-tool-pantheon-500px.png)

PTGui 的螢幕擷取畫面, 其中顯示拼接 Pantheon 的素材。 


### <a name="video-playback"></a>視訊播放

在處理完素材之後, 我們有一個流暢的影片, 但它非常龐大, 大約是8K 解析度。 解碼影片很昂貴, 而且很少電腦可以處理8K 的影片, 因此下一個挑戰是尋找在 HoloLens 上播放這部影片的方式。 我們開發了一些策略來避免進行解碼的成本, 同時讓使用者覺得看起來像是觀看整段影片。

最簡單的優化是避免解碼部分不會變更的影片。 我們撰寫了一個工具來識別每個場景中幾乎不會有任何動作的區域。 針對這些區域, 我們會顯示靜態影像, 而不是每個畫面解碼一次影片。 為了實現這一點, 我們將大量影片分成較小的區塊。

我們也確保我們解碼的每個圖元最有效率地使用。 我們使用壓縮技術來實驗, 以降低影片的大小;我們會根據要投射到的幾何多邊形來分割影片區域;我們調整了 UVs, 並根據所包含的不同多邊形有多少細節來 repacked 影片。 這項工作的結果是, 以單一8k 影片的形式啟動會變成許多區塊, 直到它們正確地重新投射到場景為止。 對於瞭解材質對應和 UV 封裝的遊戲開發人員而言, 這可能看起來很熟悉。 

![優化前的 Pantheon 完整視圖。](images/pantheon-before-optimization-500px.png) 

優化前的 Pantheon 完整視圖。 


![Pantheon 的右半部, 處理後播放的影片。](images/pantheon-process-video-playback-500px.png) 

Pantheon 的右半部, 處理後播放的影片。 


![優化和封裝後的單一影片區域範例。](images/single-video-region-after-optimization-500px.png) 

優化和封裝後的單一影片區域範例。 


我們使用的另一個技巧, 是為了避免對您未主動觀看的影片進行解碼。 在 HoloTour 中, 您只能在任何指定的時間看到整個場景的一部分。 我們只會在您的視圖範圍外 (FOV) 進行影片的解碼。 當您旋轉 head 時, 我們會開始播放現在位於 FOV 中的影片區域, 並停止播放已不在其中的地區。 大部分的人都不會注意到這種情況, 但如果您很快就會看到影片, 您就會看到一段時間開始, 在此之後, 您就會看見一個靜態影像, 然後在準備好後將它淡回影片。

為了讓此策略發揮作用, 我們開發了大量的影片播放系統。 我們已將低層級播放程式碼優化, 讓視頻切換變得非常有效率。 此外, 我們還必須以特殊方式編碼我們的影片, 讓您隨時都能快速切換到任何影片。 此播放管線已耗用大量的開發時間, 因此我們會在階段中執行。 我們從較不有效率的較簡單系統開始著手, 但允許設計人員和演出者處理經驗, 並將其緩慢地提升為更健全的播放系統, 讓我們能夠在最終的品質列中出貨。 這最後的系統具有我們在 Unity 內建立的自訂工具, 可設定場景內的影片, 並監視播放引擎。

### <a name="recreating-near-space-objects-in-3d"></a>在3D 中重新建立近空間物件

影片組成您在 HoloTour 中看到的大部分內容, 但有一些靠近您的3D 物件, 例如在 Piazza Navona 中繪製、Pantheon 外的 fountain, 或您在高空場景中所處的熱空氣氣球。 這些3D 物件很重要, 因為人類深度的認知非常接近, 但不是非常棒。 我們可以在遠處開始使用影片, 但為了讓使用者能夠四處流覽空間, 並覺得鄰近的物件需要深度。 這項技術類似于您可能會在自然歷程記錄博物館中看到的內容, 也就是在前景中以實體造景、植物和動物 specimens 的 diorama, 但是在背景中 recedes 成應變遮罩的亞光繪製。

有些物件只是我們所建立並新增至場景的3D 資產, 以增強體驗。 繪製和熱空氣氣球會落在這個類別中, 因為我們 filmed 時並不存在。 與遊戲資產類似, 它們是由我們小組的3D 演出者所建立, 並且會適當地加上紋理。 我們會將這些專案放在離您附近的幕後, 而遊戲引擎可以將它們轉譯成兩個 HoloLens 顯示, 使其顯示為3D 物件。

其他資產 (例如 Pantheon 外的 fountain) 是真正的物件, 存在於我們所要的影片中, 但若要將這些物件從影片移到 3D, 我們必須執行一些動作。

首先, 我們需要每個物件的其他資訊。 在 filming 的位置上, 我們的小組會捕捉到這些物件的許多參考素材, 讓我們有足夠的詳細影像可正確地重新建立紋理。 小組也執行了[攝影測量](https://en.wikipedia.org/wiki/Photogrammetry)掃描, 它會從數十個2d 影像中建立3d 模型, 為我們提供非常精確的物件模型。

當我們處理我們的素材時, 會從影片中移除將以3D 標記法取代的物件。 3D 資產是以攝影測量模型為基礎, 但由我們的演出者清理和簡化。 針對某些物件, 我們可以使用影片的某些部分 (例如 fountain 上的水材質), 但大部分的 fountain 現在都是3D 物件, 可讓使用者在體驗的空間有限的範圍內, 觀察深度並加以討論。 像這樣的近空間物件大幅增加了真實性的意義, 並有助於讓虛擬位置中的使用者得以接地。 

![已移除 fountain 的 Pantheon 素材。 它將會取代為3D 資產。](images/object-removal-pantheon-500px.png)

已移除 fountain 的 Pantheon 素材。 它將會取代為3D 資產。


## <a name="final-thoughts"></a>最後的想法

很明顯地, 建立此內容比我們在這裡討論的還要多。 有幾個場景, 我們想要將它們稱為「不可能的觀點」, 包括熱球形球和 gladiator 對抗 Colosseum, 這種方法更具創意。 我們將在未來的案例研究中解決這些情況。

我們希望在生產期間, 將解決方案分享給其他開發人員的挑戰, 並讓您可以使用其中一些技巧來建立您自己的 HoloLens 的沉浸式體驗。 (如果您這樣做, 請務必在[HoloLens 應用程式開發論壇](https://forums.hololens.com/)與我們分享!)

## <a name="about-the-authors"></a>關於作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b>是資深的開發人員, 他已瞭解如何在 HoloTour 上工作, 更深入瞭解相機 rig 和影片播放。</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b>是一位影片演出者, 他可以確保您的最完美地進行羅馬。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b>是一種音訊設計人員, 其可確保您可以體驗到您造訪的每個目的地的 soundscape, 即使您回到目前為止。</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b>是一個設計主管, 其研究和 scouted 位置、建立路線規劃, 以及在網站上導向的 filming。</td>
</tr>
</table>



## <a name="see-also"></a>另請參閱
* [影片：Microsoft HoloLens：HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
