---
title: 案例研究-空間設計完善的 HoloTour
description: 若要建立 Microsoft HoloLens 真正擬真 3D 虛擬之旅，全景的影片和全像攝影版的場景是公式的一部分。
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，HoloTour，空間的音效、 案例研究
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596338"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>案例研究-空間設計完善的 HoloTour

若要建立 Microsoft HoloLens 真正擬真 3D 虛擬之旅，全景的影片和全像攝影版的場景是公式的一部分。 Jason Syltebo 談論如何音效的音訊設計工具已擷取，並處理，讓您覺得您實際上是在每個 HoloTour 中的位置中。

## <a name="the-tech"></a>技術

美觀的圖像和全像攝影版的場景，您會看到 HoloTour 屬於只有一個可信的混合的實境體驗。 雖然全像投影只能前面的使用者，以視覺化方式出現[空間音效](spatial-sound.md)HoloLens 的功能可讓音訊來自所有方向，這可讓使用者更完整的感應式體驗。

空間的聲音，可讓我們提供音訊提示來指出使用者應該在其中開啟，方向，或讓使用者知道有多個全像投影，請參閱其空間內。 我們可以也音效直接附加到全像圖，並持續更新的方向和全像圖是來自使用者將看起來好像聲音直接來自該物件的距離。

使用 HoloTour，我們想要利用空間建立 360 度環境環境，以顯示特定位置 sonic 反白顯示視訊與同步處理的 HoloLens 音效功能。

## <a name="behind-the-scenes"></a>幕後

我們建立兩個不同位置的 HoloTour 的體驗：羅馬，馬丘比丘。 真確且吸引人，讓覺得這些教學課程，我們想要避免使用泛型的音效，並改為擷取音訊，直接從我們已在此對話方塊 filming 的位置。

### <a name="capturing-the-audio"></a>擷取音訊

在我們[有關的 HoloTour 擷取視覺內容的案例研究](case-study-capturing-and-creating-content-for-holotour.md)，我們談到我們的數位相機設備的自訂設計。 它包含 14 GoPro 相機中 3D 列印的住宅，所包含的設計為三腳架特定維度。 若要擷取此設備的音訊功能，我們新增了下方的相機，送入坐在基底的三腳架 compact 4 通道錄製單元四麥克風陣列。 我們選擇了 麥克風的不只執行，但其中有非常小的使用量，以便不 occlude 相機的檢視。

![自訂的攝影機與麥克風 rig](images/camera-rig-microphones-300px.png)<br>
*自訂的攝影機與麥克風 rig*

此安裝程式會擷取從我們的數位相機，提供足夠的資訊來重新建立 3D 聽覺全景使用空間的聲音，我們可以稍後再同步處理到 360 度的視訊的確切位置的 4 個方向的音效。

使用數位相機陣列音訊的挑戰之一是您的項目會記錄在擷取時掌控。 即使視訊擷取很好，音效擷取可能會變得有問題，因為關閉攝影機音效，例如塞倫海妖、 飛機或高接近。 為確保我們有我們需要的所有項目中,，我們會使用一系列的立體聲和 mono 行動錄製單位來取得非同步、 環境的項目在每個位置中感興趣的特定時間點。 此擷取十分重要，因為它讓音效的設計工具能夠找出可以在後的生產環境中用來創造感興趣，並新增其他的方向性的乾淨且可使用內容。

任何給定的擷取一天會產生大量的檔案。 重要的是，開發系統來追蹤哪些檔案會對應至特定位置或相機擷取。 我們錄製單位是設定自動命名的檔案依日期和 take 編號，我們會備份這些檔案在一天結束外部磁碟機。 最起碼，口頭且音訊錄製的開頭是很重要，因為這可讓內容的簡單內容的識別設定檔名應該成為問題。 它也是很重要，讓我們以視覺化方式 slate 相機 rig 擷取，因為視訊和音訊已記錄為獨立的媒體及所需的 post 期間，同步處理。

### <a name="editing-the-audio"></a>編輯音訊

回顧 studio 之後擷取旅程中，組合的方向和沈浸式聽覺體驗的第一個步驟是檢閱所有位置，請挑選最佳的大約需要，以及識別可能更多時間套用在任何醒目提示的音訊擷取整合。 然後編輯並清除音訊。 例如，大聲汽車 horn-kimballton 長達一秒左右，並重複幾次，可以取代，並且編結的無訊息、 環境的音訊，從相同的擷取區段使用。

一旦建立位置的視訊編輯音效的設計工具可以同步處理對應的音訊。 此時，我們已與相機 rig 擷取並決定哪些項目或兩者的組合，可建置沉浸式的音訊場景的行動裝置擷取。 我們發現有用的技巧是將音效的項目新增至音訊編輯器和建置快速線性模擬 （mock) ups 來實驗不同組合的想法。 這讓我們更正確的概念來建置實際的 HoloTour 場景時。

### <a name="assembling-the-scene"></a>組合場景

建置環境的 3D 場景的第一個步驟是建立的一般背景環境迴圈音效，將會支援其他功能和互動音效的項目在場景中的平台。 在此情況下，我們針對不同的實作取決於特定的需求和設計準則的任何特定的場景的技術有全面的方法。 而有些則可能需要更策劃的方法更分開使用音效、 互動項目和音樂及聲音效果放在 HoloTour 劇院般的時間，使用同步處理的相機擷取某些場景可能編製索引。

當使用相機擷取音訊編製索引，我們放置空間音效啟用環境音訊 fixit 發出器對應至相機方向的方向性座標，使得北部相機檢視播放北部麥克風的音訊，同樣地對於其他基數的方向。 這些 fixit 發出器是以全球鎖定，這表示使用者可以自由地開啟相對於這些 fixit 發出器其標頭和聲音會相應地變更有效地模型化時，接手該位置的聲音。 如需使用相機擷取音訊良好混合的場景的範例，以接聽 Piazza Navona 或 Pantheon。

不同的方法涉及使用空間的聲音 fixit 發出器周圍場景的播放音量、 音高及觸發程序的頻率就會隨機選擇的一次性音效播放迴圈的立體聲環境搭配使用。 這會建立環境的方向性增強的意義。 在 Aguas Calientes，比方說，您可以接聽每個象限的全景有刻意反白顯示特定區域的地理位置，但搭配運作以建立整體沈浸式環境的特定 fixit 發出器。

## <a name="tips-and-tricks"></a>祕訣和訣竅

當您要放入一起音訊的場景，有一些其他方法可用來進一步反白顯示 方向性和訓練活動，充分運用 HoloLens 聲音的空間功能。 我們提供了一些下方的清單，接聽這些嘗試 HoloTour 在下一次。
* **尋找目標**:這些是觸發程序僅當您查看特定物件或全像攝影版的畫面格的區域的音效。 比方說，尋找在羅馬的 Piazza Navona street 端咖啡廳的方向，將會稍微觸發忙碌的餐廳的音效。
* **本機願景**:旅程雖然 HoloTour 包含導覽的引導其中，特定 beats 由全像投影，輔助將探索深入的主題。 比方說，以顯示 oculus 打倒 Pantheon 的外觀，reverberating 音訊放如 3D 的 fixit 發出器，從內部的 Pantheon 鼓勵使用者瀏覽內部模型。
* **增強的方向**:在許多場景，我們可以放音效將方向性的各種方式。 在 Pantheon 場景，比方說的流水音效已放置個別的 fixit 發出器，讓他們無法取得 'sonic 視差' 感，因為他們逐步周圍的 play 空間可能不足以使用者接近。 秘魯的 Salinas de Maras 場景中的個別觀點來看一些小小的資料流放作為個別的 fixit 發出器來建置環境更沈浸式環境，周圍的使用者具有該位置的真確的音效。
* **曲線 fixit 發出器**:此特殊的空間音效發射器移動相對於所連結之物件的視覺位置的 3D 空間中。 這個範例是馬丘比丘，其中我們來曲線 fixit 發出器給不同的方向和移動中的訓練。
* **音樂和 SFX**:某些層面 HoloTour 表示更樣式化或場景的方式使用音樂和音效來加強情感的影響。 作戰 gladiator 羅馬教學課程結尾處，例如 whooshes 或 stingers 特殊效果用以協助加強標籤不會出現在場景的效果。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>音訊的設計工具 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [空間的音效](spatial-sound.md)
* [空間完善的設計](spatial-sound-design.md)
* [在 Unity 中的空間音效](spatial-sound-in-unity.md)
* [MR Spatial 220](holograms-220.md)
* [影片：Microsoft HoloLens：HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
