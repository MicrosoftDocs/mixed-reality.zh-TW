---
title: 個案研究-使用穩定平面來減少全像晃動
description: 使用穩定平面來減少全像晃動
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 全息影像, 穩定, 案例研究
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526277"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>個案研究-使用穩定平面來減少全像晃動

使用全息影像可能會很棘手。 您可以四處移動空間, 並從所有不同的角度查看您的全像投影, 提供您無法使用一般電腦螢幕來取得的深度層級。 Microsoft HoloLens 硬體和智慧型設計全像攝影應用程式都有一項技術方面的功能, 也就是將這些全息影像放在原處, 並找出實際的情況。

## <a name="the-tech"></a>技術

為了讓全息影像看起來像是實際與您分享空間, 它們應該正確轉譯, 而不需要色彩分隔。 這是由 HoloLens 硬體內建的技術所實現, 可讓全息影像錨定到我們所謂的[穩定平面](hologram-stability.md#stabilization-plane)。

平面是由某個點和一般所定義, 但由於我們一定會讓平面面對相機, 因此我們其實只關心設定平面的點。 我們可以告訴 HoloLens 將重點放在處理, 以將所有內容保持錨定並穩定, 但如何設定此焦點是應用程式特定的, 並且可以根據內容來建立或中斷您的應用程式。

簡單來說, 在適當套用穩定平面的情況下, 全像投影的效果最好, 但實際的意義取決於您所建立的應用程式類型。 讓我們看看目前可用於 HoloLens 的應用程式如何解決此問題。

## <a name="behind-the-scenes"></a>幕後

開發下列應用程式時, 我們注意到當我們未使用平面時, 物件會在我們的前端移動時顯示, 而我們會看到使用快速 head 或全像投影移動的色彩分隔。 在開發時間範圍內, 我們已瞭解試用版和錯誤如何讓穩定平面的最佳使用, 以及如何設計應用程式來解決無法修正的問題。

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>[Galaxy Explorer]:固定內容, 3D 互動性

[ [Galaxy Explorer](galaxy-explorer.md) ] 在場景中有兩個主要元素:著天體內容的主要觀點, 以及您注視之後的小型 UI 工具列。 針對穩定邏輯, 我們會查看在每個畫面格中, 您目前的注視向量與如何相交, 以判斷它是否會在指定的衝突層上達到任何專案。 在此情況下, 我們感興趣的圖層是行星, 因此, 如果您的注視落在地球上, 則會將穩定平面放在該處。 如果未叫用目標碰撞層中的任何物件, 應用程式會使用次要「計畫 B」層。 如果未在 gazed 任何內容, 穩定平面會保持與撥雲見日內容時相同的距離。 UI 工具會以平面目標的形式離開, 因為我們發現近到遠之間的跳躍會降低整體場景的穩定性。

[Galaxy Explorer] 的設計很適合讓專案穩定, 並減少色彩分隔的效果。 建議使用者四處流覽並軌道內容, 而不是從側邊移動, 而行星的軌道速度足以讓色彩分隔不明顯。 此外, 會維護常數 60 FPS, 這會很長的方式防止發生色彩分隔。

若要自行檢查, 請在[GitHub 上的 Galaxy Explorer 程式碼](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)中尋找名為 LSRPlaneModifier.cs 的檔案。

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio:具有 UI 焦點的固定內容

在 HoloStudio 中, 您大部分的時間都是在查看您所使用的相同模型。 當您選取新的工具或想要流覽 UI 時, 您的注視不會移動大量, 因此我們可以讓平面設定邏輯保持簡單。 查看 UI 時, 會將平面設定為您注視貼齊的任何 UI 元素。 查看模型時, 平面是一個設定距離, 其對應于您與模型之間的預設距離。

![在 HoloStudio 中視覺化的穩定平面, 做為 [首頁] 按鈕上的使用者 gazes](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour 和3D 檢視器:使用動畫與電影的固定內容

在 HoloTour 和3D 檢視器中, 您會看到單獨的動畫物件或電影, 並在上面加上3D 效果。 這些應用程式中的穩定會設定為您目前正在觀看的任何內容。

HoloTour 也可以讓您與您的虛擬世界 straying 太遠, 而不是在固定的位置保持。 這可確保您無法從其他的全息影像中取得足夠的空間, 以便在中蔓延。

![在此來自 HoloTour 的範例中, 穩定平面會設定為 Hadrian Pantheon 的這部電影。](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid:動態內容和環境互動

儘管應用程式需要最多突然的移動, 但是在 RoboRaid 中設定穩定平面非常簡單。 平面的目的是要靠近牆或周圍物件, 而且當您的距離夠遠時, 就會在您的前方固定地浮動。

RoboRaid 的設計是以穩定平面為考慮。 Reticle, 它最多會在它的前端之後移動, 而只使用紅色和藍色來規避這種情況, 可將任何顏色的色彩降至最低。 其中也包含幾個部分之間的深度, 並以已預期的視差效果, 將可能會發生的任何色彩出血降至最低。 機器人不會非常快速地移動, 而且只會以固定的間隔傳送短距離。 它們通常會在您前方停留2個計量, 其中預設會設定穩定。

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>片段和年輕 Conker:具有環境互動的動態內容

片段和年輕 Conker 是C++由中的 Asobo Studio 所撰寫, 採用不同的方法來設定穩定平面。 感興趣的點 (POI) 會在程式碼中定義, 並以優先順序排序。 Poi 是遊戲內的內容, 例如年輕人 Conker、功能表、意圖 reticle 和標誌中的 Conker 模型。 Poi 是與使用者的注視相交, 而平面則設定為具有最高優先順序的物件中心。 如果沒有交集, 則會將平面設定為預設距離。

如果您移至先前掃描的播放空間以外的地方, 片段和年輕 Conker 也會藉由暫停應用程式, 從您的 straying 中進行太遠的設計。 因此, 它們會將您保留在所發現的界限內, 以提供最穩定的體驗。

## <a name="do-it-yourself"></a>自行執行

如果您有 HoloLens, 而且想要解決我所討論的概念, 您可以下載測試場景, 並嘗試下列練習。 它會使用 Unity 的內建 gizmo API, 並可協助您以視覺化方式呈現您的平面設定位置。 這段程式碼也用來捕捉此案例研究中的螢幕擷取畫面。
1. 同步最新版本的[MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)。
2. 開啟[HoloToolkit-Examples/Utilities/場景/StabilizationPlaneSetting](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity)場景。
3. 建立並設定產生的專案。
4. 在您的裝置上執行。

### <a name="exercise-1"></a>練習1

您會在不同的方向看到幾個以虛線括住的點。 在您的前方, 您會在不同的深度看到三個點。 按一下以變更平面設定的點。 針對此練習, 和其他兩個, 在撥雲見日時, 請在您的空間前後移動。 將您的標頭向左、靠右、向上和向下。 從點往上移到和父親的距離。 瞭解當穩定平面設定為不同目標時, 它們的反應。

### <a name="exercise-2"></a>練習2

現在, 請切換至您的右方, 直到您看到兩個移動點, 一個水準路徑不穩定, 另一個在垂直路徑上。 同樣地, 按一下以變更平面設定的點。 請注意, 在連接到平面的點上, 色彩分隔會如何減少。 再次在平面設定函式中, 再次使用點的速度。 此參數會提供有關物件預定動作的 HoloLens 提示。 請務必知道何時使用此資訊, 因為您會注意到, 當您在某個點上使用速度時, 另一個移動點會顯示較大的色彩分隔。 在設計您的應用程式時, 請記住這一點, 讓您的物件動作具有一致的流程, 有助於防止成品出現。

### <a name="exercise-3"></a>練習3

在您看到新設定的點之前, 請先切換到您的權力。 在此情況下, 距離中有個點, 而其中一個點的前方和相應放大。 按一下以變更平面設定的點, 替換背面的點和動作中的點。 請注意, 設定平面位置和螺旋式的速度會使成品出現在所有位置。

**各種**
* 讓您的平面設定邏輯保持簡單。 如您所見, 您不需要複雜的平面設定演算法, 就能獲得沉浸式體驗。 穩定平面只是一小段謎題。
* 可能的話, 請一律在目標之間順暢地移動平面。 立即切換較遠的目標可能會以視覺化方式中斷場景。
* 請考慮在您的平面設定邏輯中有一個選項, 以鎖定非常特定的目標。 如此一來, 您就可以視需要在物件上鎖定平面, 例如標誌或標題畫面。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>軟體工程師@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [MR Basics 100：開始使用 Unity](holograms-100.md)
* [Unity 中的焦點](focus-point-in-unity.md)
* [全像投影穩定性](hologram-stability.md)
