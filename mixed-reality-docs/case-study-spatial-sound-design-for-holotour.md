---
title: 案例研究-適用于 HoloTour 的空間音效設計
description: 若要為 Microsoft HoloLens 建立真正的沉浸式3D 虛擬導覽，全景影片和全像攝影景象只是公式的一部分。
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、HoloTour、空間音效、個案研究
ms.openlocfilehash: e1da80bd647084aa4d7839c0f1b1848b46c2b1b4
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641148"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>案例研究-適用于 HoloTour 的空間音效設計

若要為 Microsoft HoloLens 建立真正的沉浸式3D 虛擬導覽，全景影片和全像攝影景象只是公式的一部分。 音訊設計工具 Jason Syltebo 將討論如何捕捉並處理音效，讓您覺得自己在 HoloTour 中的每個位置都是如此。

## <a name="the-tech"></a>技術

您在 HoloTour 中看到的美觀影像和全像攝影場景，只是建立可信 mixed reality 體驗的一部分。 雖然全息影像只會以視覺化方式出現在使用者前方，但 HoloLens 的[空間音效](spatial-sound.md)功能允許音訊來自所有方向，讓使用者有更完整的感應式體驗。

空間音效可讓我們提供音訊提示來指示使用者應輪流的方向，或讓使用者知道有更多的全息影像可在其空間內查看。 我們也可以將音效直接附加到全像投影，並持續更新全息影像與使用者之間的方向和距離，使其看起來好像是直接來自該物件。

有了 HoloTour，我們想要利用 HoloLens 的空間音效功能來建立360度的環境環境，與影片同步處理，以顯示特定位置的 sonic 重點。

## <a name="behind-the-scenes"></a>幕後

我們建立了兩個不同位置的 HoloTour 體驗：羅馬和 Machu Picchu。 為了讓這些導覽感受到絕佳且引人注目的效果，我們想要避免使用一般音效，並改為直接從我們 filming 的位置捕捉音訊。

### <a name="capturing-the-audio"></a>捕捉音訊

在我們的[案例研究中，關於捕捉 HoloTour 的視覺內容](case-study-capturing-and-creating-content-for-holotour.md)，我們談到了相機 rig 的自訂設計。 它包含14個 GoPro 攝影機，內含在3D 列印的機架中，專為特定的尺寸。 若要從這個 rig 中捕捉音訊，我們在攝影機底下新增了四個麥克風陣列，這會送到一個以基座基底為基礎的 compact 4 聲道錄影單位。 我們選擇的麥克風不僅執行良好，但有極小的使用量，因此無法遮蔽相機的觀看。

![自訂相機和麥克風 rig](images/camera-rig-microphones-300px.png)<br>
*自訂相機和麥克風 rig*

這個安裝程式會從相機的確切位置以四個方向來捕捉音效，讓我們有足夠的資訊可以使用空間音效重新建立3D 以聽覺方式全景，我們可以在稍後同步處理到360度的影片。

相機陣列音訊的挑戰之一，就是您正在 mercy 在拍攝時所記錄的內容。 即使影片捕捉良好，音效捕捉也可能會因為像是 sirens、飛機或高股，而變得很有問題。 為了確保我們擁有所需的所有元素，我們使用一系列的身歷聲和 mono 行動記錄單元，在每個位置的特定點上取得非同步環境元素。 這是很重要的，因為它可讓音效設計工具尋找清理和可用的內容，以便在後置生產中用來製作出興趣並增加進一步的方向。

任何指定的 capture day 都會產生大量的檔案。 請務必開發系統，以追蹤哪些檔案對應至特定位置或相機快照。 我們的錄影單元已設定為依日期自動命名的檔案，並採用數位，而我們會在一天結束時將這些檔案備份到外部磁片磁碟機。 最重要的是，verbally 經過音訊錄製的開頭非常重要，因為這可讓您輕鬆地識別內容，以便在檔案名中出現問題。 當影片和音訊記錄為個別媒體，而且需要在貼文期間進行同步處理時，我們也很重要。

### <a name="editing-the-audio"></a>編輯音訊

回到 studio 之後，收集方向和沉浸式以聽覺方式體驗的第一個步驟，就是複習某個位置的所有音訊捕捉，挑選最佳的接受，並找出可在整合. 然後會編輯並清除音訊。 例如，您可以使用相同的捕捉中的無訊息、環境音訊區段來取代和拼接較大的車。

一旦建立了位置的影片編輯之後，音效設計工具就可以同步處理對應的音訊。 此時，我們同時使用了「攝影機 rig」和「行動裝置捕獲」來決定哪些元素（或兩者的組合）可以用來建立沉浸式的音訊場景。 我們發現很有用的技巧，就是將所有的音效元素新增到音訊編輯器，並建立快速的線性模擬，以試驗不同的混合想法。 這讓我們在建立實際的 HoloTour 場景時，提供了更好的格式想法。

### <a name="assembling-the-scene"></a>組合場景

建立3D 環境場景的第一個步驟是建立一般背景環境迴圈音效的平臺，以支援場景中的其他功能和互動式音效元素。 在這麼做的情況下，我們採用了一套全方位的方法，讓您瞭解特定場景的特定需求和設計準則所決定的各種不同的實技術。 有些場景可能會使用已同步處理的相機捕捉來編制索引，而有些則可能需要更策劃的方法，使用更分開的音效、互動式元素和音樂，以及在 HoloTour 中有更 cinematic 的時間。

當使用相機捕捉音訊編制索引時，我們會將空間啟用音效的環境音訊發射器對應至相機方向的方向座標，讓 [上相機] 視圖從「上」麥克風播放音訊，同樣地適用于其他關鍵指示。 這些發射器是世界上鎖定的，這表示使用者可以自由地將其與這些發射器相關聯，而音效也會隨之變更，有效地將站在該位置的音效模型化。 收聽 Piazza Navona 或 Pantheon，以取得使用良好混合相機捕捉音訊的場景範例。

有一種不同的方法，就是玩迴圈身歷聲環境，並將其放在場景中，以在磁片區、音調和觸發頻率等方面隨機播放一條音效。 這會以增強的方向來建立環境。 例如，在 Aguas Calientes 中，您可以聆聽全景的每個象限如何具有特定的發射器，以刻意反白顯示地理位置的特定區域，但共同合作以建立整體的沉浸式環境。

## <a name="tips-and-tricks"></a>秘訣和訣竅

當您將音訊用於場景時，還有一些額外的方法可用來進一步強調方向性和深度，並充分利用 HoloLens 的空間音效功能。 我們在下一次嘗試 HoloTour 時，會提供一些清單。
* **尋找目標**：只有當您查看全像攝影框架的特定物件或區域時，才會觸發這些聲音。 例如，在羅馬的 Piazza Navona 中尋找街道端咖啡館的方向，將會稍微觸發忙碌餐廳的聲音。
* **當地願景**： HoloTour 的旅程包含特定的節拍，其中您的導覽指南（透過全息影像輔助）將深入探索主題。 比方說，做為 Pantheon 的外觀，以顯示 oculus go，從 Pantheon 內的3D 發射器 reverberating 的音訊，鼓勵使用者流覽內部模型。
* **增強的方向**性：在許多場景中，我們以各種不同的方式來放置音效，以加入到方向。 例如，在 Pantheon 場景中，fountain 的音效會放在靠近使用者的個別發射器，讓他們可以在播放空間前後看到「sonic 視差」。 在秘魯的 Salinas de Maras 場景中，部分小串流的個別觀點是放在不同的發射器中，以建立更沉浸的環境環境，讓使用者在該位置周圍擁有真正的音效。
* **曲線發射器**：這個特殊的空間音效發射器會在3d 空間中移動，相對於其所附加物件的視覺位置。 其中一個範例是 Machu Picchu 中的訓練，我們使用曲線發射器來提供不同的方向和移動意義。
* **音樂和 SFX**： HoloTour 的某些層面，代表更具風格或 cinematic 的方法，會使用音樂和音效效果來提高情緒的影響。 在羅馬導覽結束的 gladiator 中，whooshes 或 stingers 等特殊效果是用來協助強化標籤在幕後出現的效果。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>音訊設計工具 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>請參閱
* [空間音效](spatial-sound.md)
* [空間音效設計](spatial-sound-design.md)
* [Unity 中的空間音效](spatial-sound-in-unity.md)
* [影片： Microsoft HoloLens： HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
