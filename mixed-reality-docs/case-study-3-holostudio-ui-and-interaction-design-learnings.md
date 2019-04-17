---
title: 案例研究-3 HoloStudio UI 和互動設計所獲得的經驗
description: HoloStudio UI 和互動的設計做法
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: 混合實境的 HoloLens，HoloStudio，Windows
ms.openlocfilehash: 217c489fed3c0588dae1c2753db6ba15da3522c8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596014"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>案例研究-3 HoloStudio UI 和互動設計所獲得的經驗

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) HoloLens 是其中一個第一的 Microsoft 應用程式。 因為這個緣故，我們必須建立新的 3D UI 的最佳作法和互動的設計。 我們透過大量使用者測試、 建立原型和試驗和錯誤。

我們知道，並非所有人擁有的資源任由他們支配，若要執行這種類型的參考資料，因此我們不得不我們資深全像攝影版設計工具中，Marcus Ghaly 共用三件事我們了解有關 HoloLens 的應用程式的 UI 和互動設計 HoloStudio 開發期間。

## <a name="watch-the-video"></a>觀看影片

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>問題 #1:使用者不想要其建立四處移動

我們原本被設計在 HoloStudio workbench 為矩形，更像您會發現真實世界中。 問題在於，人的體驗，告知他們要坐在桌或讓它們未移動 workbench，在電腦前工作，並探索從所有側邊的 3D 建立時，仍保持存留期。

![矩形 HoloStudio 在 workbench 的設計 dissuaded 四處移動，並看到其從所有側邊建立的使用者。](images/rectangular-workbench-500px.jpg)

我們必須讓 workbench 捨入，因此，沒有任何 「 面對 」，或清除您原本就能進行的深入解析。 當我們測試時，突然人啟動四處移動，並自行探索其建立。

![循環的 workbench 設計建議從頭到尾參與繞其建立的使用者。](images/circular-workbench-500px.jpg)

**我們了解**

請務必考慮什麼是使用者習慣。 利用他們的實體空間是很棒的功能，HoloLens 和您無法與其他裝置。

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>問題 #2:強制回應對話方塊有時候是從全像攝影版的框架

有時候，您的使用者可能會尋找不同方向從項目需要注意應用程式中。 在 PC 上，您可以只快顯啟動一個對話方塊，，但如果您這樣做，在某個人的臉部在 3D 的環境中，它可以覺得對話方塊取得它們的方式。 您需要它們來讀取訊息，但其直覺是將嘗試取得開。 這個反應很棒，如果您在玩遊戲時，但在工具中，針對工作所設計，是不盡理想。

在嘗試幾個不同的項目之後, 我們最後決定使用 「 相信有一天泡泡 」 系統對於我們的對話，並加入 tendrils 使用者可遵循在我們的應用程式中需要注意的地方。 我們也強化了 tendrils 脈衝，其中隱含的方向，讓使用者知道的位置。

![「 認為泡泡 」 系統包含閃爍 tendrils 提供方向，導致使用者已在應用程式所需注意感。](images/thought-bubble-500px.jpg)

**我們了解**

它是很難在 3D，警告使用者他們需要注意的事項。 這類使用注意董事會[空間音效](spatial-sound.md)、 亮色調光線，或思考反昇，可能會導致使用者能所需的位置。

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>問題 3:有時候 UI 都可以使用其他全像投影遭到封鎖

有些的時候，當使用者想要互動的全像和其相關聯的 UI 控制項，但會從檢視中封鎖，因為另一個全像前面。 雖然我們開發 HoloStudio，我們會用來參加這個方案的試驗和錯誤。

![如果它與穿著 HoloLens 的使用者之間的另一個全像雷射相關聯的 UI 控制項可能會被封鎖。](images/ui-blocked-500px.jpg)

我們試著將 UI 控制項更接近移至使用者，讓它無法取得受到封鎖，但發現那其實不知道如何讓使用者查看時同時查看很遠的地方是全像已接近您的控制項。 如果，不過，我們已接近全像前面控制項移至使用者，他們覺得自己已卸離應該會影響全像圖。

最後，我們會最後會建立映像的 UI 控制項，並將其放置在相同的距離使用者為其相關聯，全像圖讓它們都覺得連線。 這可讓使用者與控制項互動，即使它已遮蔽。

![解決方案： 我們建立 UI 控制項，同時允許與控制項互動，並使它可以連線到它已影響全像映像。](images/ghosting-ui-500px.jpg)

**我們了解**

使用者必須要能夠輕鬆地存取 UI 控制項，即使它們已被封鎖，因此請找出方法，以確保使用者可以完成其身處何處其全像投影真實世界中的工作。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Sr.全像攝影版的設計工具 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [互動的基本概念](interaction-fundamentals.md)

 
