---
title: 互動的基本概念
description: 如我們所建置的體驗，跨 HoloLens （第 1 代）、 HoloLens 2 和沈浸式耳機，我們已經開始寫下可共用，我們發現的一些事項。
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合實境，互動，設計
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591128"
---
# <a name="interaction-fundamentals"></a>互動的基本概念

如我們所建置的體驗，跨 HoloLens 和沈浸式耳機，我們已經開始寫下可共用，我們發現的一些事項。 想像這是基本的建置組塊，混合的實境互動設計。

## <a name="device-support"></a>裝置支援

以下是套用至已發佈的互動設計文件的裝置類型或類型的外框。
<br>

<table>

<th>
<tr>

<td style="width:150px;"><strong>輸入</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
</tr>
</th>
 
<tr>
<td> <a href="gestures.md">相互連貫的指針</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td></td>

</tr><tr>
<td> <a href="gaze-targeting.md">眼睛目標</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;"></td>
</tr><tr>
<td> <a href="gaze-targeting.md">為目標的視線</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gestures.md">筆勢</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-design.md">語音設計</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> 遊戲台</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
<tr>
<td> <a href="motion-controllers.md">動作控制站</a></td><td></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>

</tr>
<th>
<tr>
<td style="width:150px;"><strong>認知和空間的功能</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
</tr>
</th>
<tr>

<td> <a href="spatial-sound-design.md">空間完善的設計</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping-design.md">空間對應設計</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="hologram.md">全像投影</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a>使用者是觀景窗

![使用者是觀景窗](images/useriscamera-640px.jpg)

一定會想要針對使用者的觀點來看設計有關他們的實際及虛擬世界中移動。

**若要詢問的一些問題**
* 是使用者坐、 reclining、 固定，而且或步行時使用您的體驗嗎？
* 您的內容如何調整到不同位置？
* 可以 使用者會調整它嗎？
* 使用者會輕鬆自如地使用您的應用程式嗎？

**最佳作法**
* 使用者是數位相機，它們控制移動。 讓這些磁碟機。
* 如果您需要以虛擬方式傳輸使用者時，很容易受 vestibular discomfort 相關問題。
* 使用較短的動畫
* 建立動畫的來源清單/左/右或淡入，而不是 Z
* 時間變慢
* 允許使用者會看到在背景中 world

**要避免的事項**
* 不要搖動相機或刻意將其鎖定以 3DOF 只方向 (未轉譯），它可以讓使用者感到不安。
* 任何突然的移動。 如果您需要將內容，或使用者，將它移緩慢且順暢地進行到它們的最大的緩和。 即將在它們的大型功能表會因應使用者。
* 不能加快速度，或開啟使用者的相機。 使用者是區分加速 （angular 和 translational）。

## <a name="leverage-the-users-perspective"></a>利用使用者的觀點來看

使用者會看到沈浸式和全像攝影版的裝置上混合實境，透過顯示的世界。 HoloLens，在此顯示稱為[全像攝影版的框架](holographic-frame.md)。

2D 開發，經常存取的內容和設定可能放個角落的畫面，使其更容易存取。 不過，在全像攝影版的應用程式，可能會不想存取的使用者檢視的邊角中的內容。 在此情況下，全像攝影版的畫面格的中心是內容的主要位置。

使用者可能需要指引以協助找出重要的事件或超過其立即檢視的物件。 您可以使用箭號、 淺線索、 字元磁頭移動，思考泡泡、 指標、 空間音效以及語音提示，可協助引導您的應用程式中的重要內容的使用者。

建議您將未鎖定內容至使用者的緩和的畫面。 如果您需要保留內容檢視中，將它放在世界各地，讓內容 「 tag-along"，例如 [開始] 功能表。 取得使用者的觀點來看以及提取的內容會覺得在環境中更自然。

![[開始] 功能表會到達框架邊緣時，所遵循的使用者檢視](images/tagalong-1000px.jpg)<br>
*[開始] 功能表會到達框架邊緣時，所遵循的使用者檢視*

在 HoloLens，因為沒有取得切掉符合全像攝影版的範圍內時，覺得真正全像投影。 使用者會移動才能看到雷射範圍內的界限。 上 HoloLens，是簡化的使用者檢視，而且可以專注於主要動作上將使用者介面。 沈浸式耳機，務必維護永續性虛擬世界內裝置的視野的假象。

## <a name="user-comfort"></a>使用者

若要確保最大[緩和](comfort.md)上掛接標頭的顯示，是很重要的設計人員和開發人員建立，並以模擬人類如何解譯 3D 圖形和物件的相對位置，自然的方式呈現內容世界。 實體的觀點而言，也很重要的設計不需要的頸部或手臂 fatiguing 動作的內容。

不論開發 HoloLens 或沈浸式耳機，務必轉譯這兩個眼睛的視覺效果。 轉譯平視顯示窗眼裡一個只可以讓介面難了解，以及造成使用者的注意和大腦 uneasiness。

## <a name="share-your-experience"></a>分享您的體驗

使用[混合實境擷取](mixed-reality-capture.md)，使用者可以擷取相片或視訊的使用者體驗，在任何時間。 請考慮您可能要鼓勵快照集或視訊的應用程式中的體驗。

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a>運用基本家用的 Windows Mixed Reality UI 項目

就像 Windows PC 體驗啟動與桌面時，Windows Mixed Reality，開始於首頁。 [Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)運用我們對中炫耀都能夠了解，並瀏覽 3D 的地方。 HoloLens，您的首頁是您的實體空間。 沈浸式耳機，與您的首頁會是虛擬的位置。

您的首頁也是，您將使用 [開始] 功能表開啟，並將應用程式和內容。 您可以混合的實境內容中填入您的首頁和 multitask 同時使用多個應用程式。 您放置在您家中的項目留在那裡，即使您重新啟動您的裝置。

## <a name="see-also"></a>另請參閱
* [為目標的視線](gaze-targeting.md)
* [筆勢](gestures.md)
* [語音設計](voice-design.md)
* [動作控制站](motion-controllers.md)
* [空間完善的設計](spatial-sound-design.md)
* [空間對應設計](spatial-mapping-design.md)
* [Comfort](comfort.md)
* [瀏覽家用的 Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
