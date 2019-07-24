---
title: 案例研究-3 HoloStudio UI 和互動設計學習
description: HoloStudio UI 和互動設計學習
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、HoloStudio、Windows Mixed Reality
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974822"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>案例研究-3 HoloStudio UI 和互動設計學習

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8)是 HoloLens 的第一個 Microsoft 應用程式。 因此, 我們必須為 3D UI 和互動設計建立新的最佳作法。 我們透過許多使用者測試、原型設計和試用版和錯誤來完成這項工作。

我們知道不是每個人都有資源可以處置這種類型的研究, 因此我們有了我們的 Marcus Ghaly, 分享在開發 HoloStudio 有關 HoloLens 應用程式的 UI 和互動設計期間所學到的三件事。

## <a name="watch-the-video"></a>觀看影片

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>問題 #1:人們不想要四處移動

我們原先在 HoloStudio 中將工作臺設計成一個矩形, 就像您在現實世界中找到的一樣。 問題是, 人們有經驗的存留期, 告訴他們仍在電腦坐在桌上, 或是在電腦前方工作, 因此他們不會在工作臺上移動, 同時探索他們的3D 建立。

![在 HoloStudio 中, 工作臺的矩形設計會 dissuaded 使用者, 從所有邊四處移動並查看其建立。](images/rectangular-workbench-500px.jpg)

我們有深入解析可讓工作臺變圓, 因此不會有任何「前端」或明確的位置。 當我們測試過這種情況時, 突然有人開始四處流覽自己的建立工作。

![「迴圈工作臺」設計鼓勵使用者在其建立過程中進行一步。](images/circular-workbench-500px.jpg)

**我們學到的內容**

請務必考慮使用者的熟悉之處。 利用其實體空間是 HoloLens 的絕佳功能, 也是您無法使用其他裝置執行的作業。

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>問題 #2:強制回應對話方塊有時不在全像攝影畫面上

有時候, 您的使用者可能會與需要在您的應用程式中注意的地方進行不同的方向。 在電腦上, 您可以只顯示一個對話方塊, 但如果您在某個人的3D 環境中執行此動作, 就會覺得對話會以他們的方式進入。 您需要它們來讀取訊息, 但其直覺是嘗試離開它。 如果您想要玩遊戲, 但是在專為工作而設計的工具中, 這項反應就很好用, 這不是理想的選擇。

嘗試幾個不同的東西之後, 我們終於針對對話使用「思考過的反升」系統, 並新增使用者可以遵循的 tendrils, 讓應用程式需要他們注意。 我們也將 tendrils 的脈衝, 這暗示了方向性, 讓使用者知道要前往何處。

![「思考的反升」系統包含可提供方向的 tendrils, 可讓使用者在應用程式中需要注意的地方。](images/thought-bubble-500px.jpg)

**我們學到的內容**

3D 會更難提醒使用者他們需要注意的事項。 使用像是[空間音效](spatial-sound.md)、光線或考慮氣泡等的注意總監, 可以引導使用者到達他們需要的位置。

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>問題 #3:有時 UI 可能會被其他全息影像封鎖

有時候, 使用者想要與全息和其相關聯的 UI 控制項互動, 但是因為有其他的全息影像, 所以它們會被封鎖而無法觀看。 在開發 HoloStudio 時, 我們使用了試用版和錯誤, 來解決這個問題。

![如果它與使用者戴 HoloLens 之間有另一個全息圖, 則與全息影像建立關聯的 UI 控制項可能會遭到封鎖。](images/ui-blocked-500px.jpg)

我們嘗試將 UI 控制項移到靠近使用者的位置, 因此無法被封鎖, 但發現它不適合讓使用者查看您附近的控制項, 同時又可以同時查看距離最遠的全息影像。 不過, 如果我們將控制項移到最接近的全息圖前方, 他們就會覺得它已從應該影響的全息影像卸離。

最後, 我們會使 UI 控制項變得更好, 並將其與與該使用者相關聯的全像位置相同, 使其與您的影像相同。 這可讓使用者與控制項互動, 即使它已被遮蔽也一樣。

![解決方案: 我們會將 UI 控制項加上准, 這兩者都允許與控制項互動, 並讓它覺得連接到它所影響的全息影像。](images/ghosting-ui-500px.jpg)

**我們學到的內容**

使用者必須能夠輕鬆地存取 UI 控制項, 即使已被封鎖也一樣, 因此請找出方法, 以確保使用者可以完成其工作, 而不論其在現實世界中的位置。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Sr-iov 設計工具@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [本能互動](interaction-fundamentals.md)

 
