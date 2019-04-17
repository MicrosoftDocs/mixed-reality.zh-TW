---
title: 案例研究-減少全像攝影版的動盪一同使用穩定平面
description: 若要減少全像攝影版的動盪一同使用穩定平面
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全像投影、 穩定、 案例研究
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591124"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>案例研究-減少全像攝影版的動盪一同使用穩定平面

使用全像投影可能很難。 您可以用來移動您的空間，並查看您所有的不同角度從全像投影的事實提供您無法利用標準電腦螢幕的深度的層級。 將這些全像投影保留在原位，並尋找實際是透過 Microsoft HoloLens 硬體和智慧型全像攝影版的應用程式的設計的技術能力。

## <a name="the-tech"></a>技術

若要讓全像投影看似它們實際上與您共用的空間，其應該會轉譯正確，不使用色彩隔離。 即可達成此目的，部分內建於其中保存全像投影錨定在我們所謂的 HoloLens 硬體技術[穩定平面](hologram-stability.md#stabilization-plane)。

平面由點和定義一般，但因為我們一直都希望面對相機平面，我們只關心設定平面的點。 我們可以告訴會將焦點放入所有項目錨定的保留其處理指的 HoloLens 和穩定，但如何設定此鶗懘應用程式而異，並能夠左右您的應用程式，視內容而定。

簡單的說，全像投影運作最佳時正確地套用穩定平面，但實際上方法取決於您要建立的應用程式的類型代表什麼意思。 讓我們看看一些目前可供 HoloLens 的應用程式如何處理這個問題。

## <a name="behind-the-scenes"></a>幕後

在開發下列應用程式時，我們注意到，當我們並未使用平面，物件會 sway 時我們標頭移到，我們會看到快速的前端或全像移動色彩區隔。 開發時間範圍期間，我們已了解透過誤如何善用穩定平面及設計我們的應用程式，它無法修正的問題解決方式。

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer:靜態內容，3D 互動性

[Galaxy 總管](galaxy-explorer.md)場景中有兩個主要的項目：科學內容並遵循您的視線小型 UI 工具列的主要檢視中。 穩定邏輯中，我們會探討您目前的視線向量相交與每個畫面來判斷是否達到指定的衝突圖層上的任何項目中。 在此情況下，我們感興趣的圖層會在行星上，因此如果您的視線落在行星上，穩定平面放在該處。 如果沒有任何目標衝突層中的物件叫用時，應用程式會使用次要的 「 方案 B 」 層。 如果不要在 gazed，穩定平面會保留在相同的距離，gazing 內容時一樣。 UI 工具中省略了平面目標為我們找到附近之間跳躍點，並更減少整體的場景的穩定性。

Galaxy 總管的設計適合用於項目保持穩定，並減少色彩區隔的效果。 四處巡察和軌跡內容而非移動沿著其並行，因此使用者可以和行星這顆恆速度色彩區隔不明顯。 此外，會維護常數 60 FPS，這會導致發生色的方式。

若要自行檢查此情形，尋找檔案，在呼叫 LSRPlaneModifier.cs [Galaxy 總管程式碼，GitHub 上的](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)。

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio:「 定態 UI 焦點內容

在 HoloStudio，您會花費大部分的時間查看相同的模型正努力。 您的視線不會移動一段很長，但當您選取新的工具，或想要巡覽 UI，讓我們可以簡化平面設定邏輯。 檢視 UI 時，此平面設為您的視線貼齊至任何 UI 項目。 查看模型，平面時設定的距離，與預設的距離，寄件者與模型之間對應。

![穩定平面以視覺化方式檢視中以使用者身分 HoloStudio gazes 在 [首頁] 按鈕](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour 和 3D 檢視器：動畫和電影的靜態內容

在 HoloTour 和 3D 檢視器中，您想透過單獨動畫的物件或電影與在其上加入 3D 效果。 在這些應用程式穩定會設定為任何您目前檢視中。

HoloTour 也會防止您從您的虛擬世界太遠而 straying 方法是讓它與您一起移動，而無須停留在固定的位置。 這可確保您不想得夠小遠離其他全像投影到蔓延的穩定性問題。

![在此範例中從 HoloTour，穩定平面會設定為 Hadrian 的 Pantheon 的電影。](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid:動態內容和環境的互動

設定 RoboRaid 穩定平面是出乎意料地簡單，但還是需要進行最突然移動的應用程式。 平面專為著重於背景牆或周圍的物件，並將浮點數面前的固定距離夠遠離開時。

記住的穩定平面 RoboRaid 的設計。 Reticle，移動大部分，因為它是標頭鎖定，這會避開這使用只有紅色和藍色的最小化任何色彩的高度。 它也包含小型的位元的項目，並且降至最低由遮罩處理，含有已預期的視差效果，就會發生任何色彩頁之間的深度。 機器人不非常快速地移動，並只傳送短程距離，以固定間隔。 它們通常會維持大約 2 公尺前方，其中預設會設定穩定。

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>片段和年輕 Conker:環境互動的動態內容

作者 Asobo Studio，在  C++，片段和 Young Conker 採用不同的方式設定穩定平面。 景點 (POI) 定義於程式碼，並依據優先順序排序。 Poi 是遊戲中的內容，例如 Conker 模型 Young Conker、 功能表、 通用性 reticle，和標誌。 Poi 與使用者的視線交集和平面設為具有最高優先順序物件的中心。 如果沒有交集，平面設為預設的距離。

片段和 Young Conker 也設計中心您太遠從全像投影 straying 藉由暫停應用程式，如果您移動項目會為您的播放空間先前掃描之外。 因此，它們可讓您以提供最穩定的經驗所找到的界限內。

## <a name="do-it-yourself"></a>自行進行此作業

如果您有 HoloLens，並想要玩我所討論的概念，您可以下載測試場景，並試試看以下的練習。 它會使用 Unity 的內建 gizmo API，它應該可以協助您以視覺化方式檢視 正在設定您的飛機。 此程式碼也用來擷取在此案例研究的螢幕擷取畫面。
1. 同步處理的最新版本[MixedRealityToolkit Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)。
2. 開啟[HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity)場景。
3. 建置並設定所產生的專案。
4. 在您的裝置上執行。

### <a name="exercise-1"></a>練習 1

您會看到數個白色點周圍您在不同的方向。 之前，您會看到三個點不同的深度。 若要變更的空中點選的點平面會設定為。 針對此練習中，以及其他兩個，您的空間四處移動時 gazing 在點中。 向上和向下，請開啟您前端的左邊，右邊。 移動點使其更接近和 father。 請參閱穩定平面設為不同的目標時，他們的反應如何。

### <a name="exercise-2"></a>練習 2

直到您看到兩個移動的點，其中一個穩定的水平的路徑和一個垂直的路徑上，現在，開啟您的權限。 同樣地，空中點選來變更設平面的點。 色變小，如何通知會出現在已連線到此平面的點。 再次點選以在平面設定函式中使用點的速度。 此參數會提供有關物件的預定動作到 HoloLens 的提示。 請務必了解何時要使用此功能，您會發現一個點上使用速度時，移動點將會顯示更高的色彩區隔。 記住這設計您的應用程式時，擁有一致的流程，以移動的物件出現時，防止成品可以幫助。

### <a name="exercise-3"></a>練習 3

移至您的權限一次直到您看到新的組態的點。 在此情況下有點之間的距離和縮小和相應放大 spiraling 前面的一個點。 空中點選來變更平面中設定替代後的點和移動中的點之間的點。 請注意如何設定平面位置和速度的 spiraling 點讓每個地方出現的成品。

**祕訣**
* 簡化您的平面設定邏輯。 如您所見，您不需要複數平面設定演算法，讓人沉迷的體驗。 穩定平面是只有一個一塊拼圖。
* 可能的話，在時一律平面之間移動目標順暢。 立即切換遙遠的目標時，並以視覺化方式可能會中斷場景。
* 請考慮讓在平面設定邏輯鎖定在非常特定的目標上的選項。 如此一來，如有需要可以有鎖定物件，例如標誌 或 標題 畫面上的平面。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>軟體工程師 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [MR 基本概念 100:開始使用 Unity](holograms-100.md)
* [在 Unity 中的焦點](focus-point-in-unity.md)
* [全像穩定性](hologram-stability.md)
