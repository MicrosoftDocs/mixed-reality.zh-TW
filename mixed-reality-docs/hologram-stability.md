---
title: 全像投影穩定性
description: HoloLens 會自動穩定的全像投影，但是開發人員可以採取一些步驟進一步改善全息影像的穩定性。
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: 全息影像、穩定性、hololens
appliesto:
- HoloLens
ms.openlocfilehash: 4a489c923138808e3afb545097c314f354b5ad2a
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408206"
---
# <a name="hologram-stability"></a>全像投影穩定性

## <a name="overview"></a>概觀

為了達到穩定的全息影像，HoloLens 具有內建的映射穩定管線。 穩定管線會在背景中自動運作，因此您不需要採取任何額外的步驟來啟用它。 不過，您應該執行改善全像全像的技術，並避免會降低穩定性的案例。

## <a name="hologram-quality-terminology"></a>全息全像品質術語

全像投影的品質是良好的環境和良好應用程式開發的結果。 在 HoloLens 可以追蹤周圍的環境中，每秒執行的應用程式會以固定的60框架為單位，確保全息全像投影和相符的座標系統同步。從使用者的觀點來看，想要成為固定的全息影像不會相對於環境進行移動。

下列術語可協助您找出環境的問題、不一致或較低的轉譯速率，或其他任何專案。
* **精確.** 當全像世界各地的全息物住在現實世界中時，應該保持其相對於周圍環境的位置，並獨立于使用者動作或小型和稀疏環境的變更。 如果之後的全息影像出現在非預期的位置，就會是*正確*的問題。 如果兩個不同的房間看起來完全相同，可能就會發生這種情況。
* **抖動.** 使用者會觀察到高頻率的全息影像抖動，這可能會在追蹤環境降低時發生。 針對使用者，解決方案正在執行[感應器微調](sensor-tuning.md)。
* **Judder.** 低轉譯頻率會導致不平均的運動和影像的兩倍。 在具有動作的全息影像中，Judder 特別明顯。 開發人員必須維持[常數 60 FPS](hologram-stability.md#frame-rate)。
* **便.** 使用者會看到像是全像一開始放置的全息影像。 當從[空間錨點](spatial-anchors.md)放置全息影像時，會發生漂移，特別是在未完全對應的環境部分。 建立接近空間錨點的全息影像，會降低漂移的可能性。
* **Jumpiness.** 當全息的「pop」或「跳躍」時，偶爾會從其位置消失。 當追蹤調整全息影像以符合對您環境的更新瞭解時，可能會發生 Jumpiness。
* **泳道.** 當您的全息顯示與使用者的動作相對應的 [sway] 時。 當應用程式未完全實[reprojection](hologram-stability.md#reprojection)，而且未針對目前的使用者[校準](calibration.md)HoloLens 時，就會發生泳道。 使用者可以重新執行[校正](calibration.md)應用程式來修正問題。 開發人員可以更新穩定平面，以進一步增強穩定性。
* **色彩分隔。** HoloLens 中的顯示為色彩順序顯示，其會將紅色-綠色-藍綠-綠色的色頻閃爍為 60 Hz （個別色彩欄位會顯示在 240 Hz）。 每當使用者以眼睛來追蹤移動的全息影像時，該全像投影的開頭和尾端邊緣會以其構成色彩分隔，產生彩虹效果。 分隔程度取決於全息影像的速度。 在某些罕見案例中，當您在查看固定的全息光碟時，快速移動一個，也可能導致彩虹的效果，稱為「*[色彩分隔](hologram-stability.md#color-separation)*」。

## <a name="frame-rate"></a>畫面播放速率

畫面播放速率是全息影像穩定性的第一個要件。 若要讓全息影像在世界中顯示為穩定，呈現給使用者的每個影像都必須在正確的位置繪製全像投影。 每秒會顯示 HoloLens 重新整理240次，並針對每個新呈現的影像顯示四個不同的色彩欄位，導致使用者體驗 60 FPS （每秒畫面格）。 為了盡可能提供最佳體驗，應用程式開發人員必須維護 60 FPS，這會轉譯為每16毫秒一致地將新的映射提供給作業系統。

**60 FPS**若要繪製全息影像，使其看起來像是真實世界，HoloLens 必須從使用者的位置呈現影像。 由於影像轉譯需要一些時間，因此 HoloLens 會預測使用者的前端在顯示畫面中顯示時的位置。 不過，這種預測演算法是近似值。 HoloLens 具有硬體，可調整轉譯的影像，以考慮預測的標頭位置與實際的頭部位置之間的差異。 調整會使使用者所看到的影像看起來像是從正確的位置轉譯，而全息影像的外觀也很穩定。 映射更新最適用于小型變更，而且無法完整修正轉譯影像中的某些專案，例如視差。

藉由在 60 FPS 轉譯，您會做三件事來協助進行穩定的全息：
1. 將轉譯影像和使用者看到的影像之間的整體延遲降到最低。 在具有遊戲的引擎和在密集建置中執行的轉譯執行緒中，于30FPS 執行的會增加33.3 毫秒的額外延遲。 減少延遲會減少預測錯誤，並增加全息影像的穩定性。
2. 讓每個影像達到使用者的眼睛，都具有一致的延遲量。 如果您以 30 fps 轉譯，顯示器仍會以 60 FPS 顯示影像，這表示相同的影像將會在資料列中顯示兩次。 第二個16.6 框架的延遲比第一個框架還多，而且必須更正較明顯的錯誤量。 這種錯誤程度不一致，可能會導致不必要的 60 Hz judder。
3. 減少出現顫抖，它的特色是不平均的運動和雙重影像。 更快的全像投影動作和更低的轉譯率與更明顯的顫抖相關聯。 努力隨時維護 60 FPS 將有助於避免指定的移動全息影像 judder。

**畫面播放速率一致性**畫面播放速率一致性與每秒高框架的重要性相同。 對於任何內容豐富的應用程式，偶爾捨棄的畫面是不可避免的，而且 HoloLens 會實行一些複雜的演算法來復原偶爾的問題。 不過，如果使用者以較低的畫面播放速率一致地執行，經常變動的畫面播放速率就會更明顯。 例如，應用程式會順暢呈現五個畫面格（這五個畫面的持續時間為 60 FPS），然後在接下來的10個畫面中卸載每個其他畫面格（這10個畫面的持續時間為 30 FPS），會比以 30 FPS 一致呈現的應用程式更不穩定。

在相關的注意事項中，作業系統會在[混合現實 capture](mixed-reality-capture.md)執行時，將應用程式調節為 30 FPS。

**效能分析**有不同類型的工具可用來對應用程式畫面播放速率進行基準測試，例如：
* GPUView
* Visual Studio 圖形偵錯工具
* 內建于3D 引擎（例如 Unity）中的分析工具

## <a name="hologram-render-distances"></a>全息影像轉譯距離

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

當 fixates 並著重于物件時，人類視覺效果系統會整合多個與距離相關的信號。
* [住宿](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)-個人眼的重點。
* [聚合](https://en.wikipedia.org/wiki/Convergence_(eye))-在物件上向內或向外移動兩個眼睛。
* [Binocular 視覺](https://en.wikipedia.org/wiki/Stereopsis)-在與您的 fixation 點不同的物件距離之間 Disparities 的左右影像。
* 陰影、相對角度大小和其他 monocular （單一眼）提示。

聚合和住宿的獨特之處在于，其視網膜的相關提示，與眼睛如何改變以在不同距離感知物件有關。 在自然觀賞中，融合和住宿是連結的。 當眼睛接近時（例如，您的鼻子）時，眼睛會交叉並配合接近點。 當眼睛為無限大時，眼睛就會變得平行，眼睛則會與無限大配合。 

戴 HoloLens 的使用者一律會容納 2.0 m，以維護清楚的影像，因為 HoloLens 顯示器的固定位置是與使用者相距接近 2.0 m 的光學距離。 應用程式開發人員可以在各種深度放置內容和全息影像，以控制使用者的眼睛。 當使用者配合並融合到不同的距離時，兩個提示之間的自然連結會中斷，這可能會導致視覺 discomfort 或疲勞，特別是當衝突的程度很大時。 

將交集內容保持在最接近 2.0 m 的情況下（也就是，在有許多深度將感興趣的區域放在接近 2.0 m 的情況下），可以避免或將 Discomfort 從 vergence-便利。 當內容不能放在 2.0 m 附近時，當使用者在不同距離之間來回看時，從 vergence-住宿衝突 discomfort 是最大的。 換句話說，要查看一段時間內遠離您的全像投影 50 cm，可以更輕鬆地查看持續 50 cm 的全像位置。

將內容放在 2.0 m 也很有利，因為這兩個顯示器的設計是要在此距離完全重迭。 對於放在此平面外的影像，當它們移出全像攝影框架的側邊時，它們會從一個顯示畫面顯示，同時仍可在另一個顯示器上看到。 這個 binocular rivalry 可能會干擾 holorgam 的深度感知。

**放置距離使用者的全像投影最佳距離**

![放置距離使用者的全像投影最佳距離](images/distanceguiderendering-750px.png)

**剪輯平面**為獲得最大的緩和度，建議您在 85 cm 裁剪轉譯距離，並從 1 m 開始以淡出內容。 在全像投影和使用者都是固定的應用程式中，可以像 50 cm 一樣輕鬆地觀看全息影像。在這些情況下，應用程式應該將剪輯平面放在不到 30 cm 的位置，而且應該從剪切平面開始至少 10 cm。 每當內容接近 85 cm 時，請務必確保使用者不會經常從全息影像移近或更遠，或不常從使用者處移到更接近或更遠的影像，因為這些情況最可能會造成 discomfort 的 vergence-住宿衝突。 內容的設計目的是要將互動的需求降到最低，而不是從使用者到 85 cm，但當內容必須轉譯成接近 85 cm 時，開發人員最好的經驗法則是設計案例，讓使用者和/或全息影像在超過25% 的時間內不會有更深入的移動。

**最佳做法**當全息影像不能放在 2 m，而且無法避免聚合與住宿之間的衝突時，全像投影位置的最佳區域是介於 1.25 m 到 5 m 之間。 在每個案例中，設計人員都應該結構內容，以鼓勵使用者離開 1 + m 的互動（例如，調整內容大小和預設放置參數）。

## <a name="reprojection"></a>Reprojection
HoloLens 會執行複雜的硬體輔助全像攝影穩定技術，稱為 reprojection。 當場景繪製動畫，而使用者移動其 head 時，Reprojection 會考慮移動和變更觀點（CameraPose）。  應用程式必須採取特定動作，才能充分利用 reprojection。


Reprojection 有四種主要類型
* **深度 Reprojection：** 以最少的應用程式工作量來產生最佳的結果。  轉譯之場景的所有部分都是根據與使用者的距離而獨立穩定的。  有些呈現成品可能會在深度變更較清晰時顯示。  此選項僅適用于 HoloLens 2 和沉浸式耳機。
* **平面 Reprojection：** 允許應用程式精確控制穩定。  平面是由應用程式所設定，而該平面上的所有專案將會是場景中最穩定的部分。  其中的全息全像是從平面開始，它的穩定程度較低。  此選項適用于所有 Windows MR 平臺。
* **自動平面 Reprojection：** 系統會使用深度緩衝區中的資訊來設定穩定平面。  此選項適用于 HoloLens 第1代和 HoloLens 2。
* **無：** 如果應用程式不會執行任何操作，則會在使用者的前端眼中，使用平面 Reprojection 以2個計量固定的穩定平面，通常會產生 substandard 的結果。

應用程式必須採取特定動作來啟用不同類型的 reprojection
* **深度 Reprojection：** 應用程式會針對每個呈現的框架，將其深度緩衝區提交至系統。  在 Unity 上，會使用 [ **XR 外掛程式管理**] 下 [ **Windows Mixed Reality 設定**] 窗格中的 [**共用深度緩衝區**] 選項來完成深度 Reprojection。  DirectX 應用程式會呼叫 CommitDirect3D11DepthBuffer。  應用程式不應呼叫 SetFocusPoint。
* **平面 Reprojection：** 在每個畫面上，應用程式會告訴系統要穩定的平面位置。  Unity 應用程式會呼叫 SetFocusPointForFrame，而且應該停用**共用深度緩衝**。  DirectX 應用程式會呼叫 SetFocusPoint，而不應呼叫 CommitDirect3D11DepthBuffer。
* **自動平面 Reprojection：** 若要啟用，應用程式必須將其深度緩衝區提交至系統，就像深度 Reprojection 一樣。  在 HoloLens 2 上，應用程式接著必須使用0點 SetFocusPoint，每個框架都有0。  若為 HoloLens 層代1，應用程式不應呼叫 SetFocusPoint。

### <a name="choosing-reprojection-technique"></a>選擇 Reprojection 技術

穩定類型 |    沉浸式耳機 |    HoloLens 第1代 | HoloLens 2
--- | --- | --- | ---
深度 Reprojection |    建議 |   N/A |   建議<br/><br/>Unity 應用程式必須使用 Unity 2018.4.12 或更新版本，或 Unity 2019.3 或更新版本。 否則，請使用自動平面 Reprojection。
自動平面 Reprojection | N/A |   建議的預設值 |   如果深度 Reprojection 未提供最佳結果，則建議使用此選項<br/><br/>建議 unity 應用程式使用 Unity 2018.4.12 或更新版本，或 Unity 2019.3 或更新版本。  先前的 Unity 版本將會使用稍微降級的 reprojection 結果。
平面 Reprojection |   不建議 |   如果自動平面未提供最佳結果，則建議使用此選項 | 如果深度選項都不提供所需的結果，請使用    

### <a name="verifying-depth-is-set-correctly"></a>確認已正確設定深度
            
當 reprojection 方法使用深度緩衝區時，請務必確認深度緩衝區的內容代表應用程式的呈現場景。  許多因素可能會造成問題。 例如，如果有第二個相機用來呈現使用者介面重迭，就可能會覆寫實際視圖中的所有深度資訊。  透明物件通常不會設定深度。  某些文字轉譯預設不會設定深度。  當深度與轉譯的全息影像不相符時，呈現中會出現問題。
            
HoloLens 2 有一個視覺化效果，可顯示深度為且未設定的位置，您可以從裝置入口網站啟用此功能。  在 [ **Views**  >  **全息影像穩定性**] 索引標籤上，選取 [**在耳機中顯示深度視覺效果**] 核取方塊。  已正確設定深度的區域將會是藍色。  沒有深度設定的轉譯專案會以紅色標示，而且需要修正。  

> [!NOTE]
> 深度的視覺效果將不會顯示在混合現實 Capture 中。  只有透過裝置才能看到它。
            
某些 GPU 視圖工具會允許深度緩衝區的視覺效果。  應用程式開發人員可以使用這些工具，以確保正確設定的深度。  請參閱應用程式工具的檔。

### <a name="using-planar-reprojection"></a>使用平面 Reprojection
> [!NOTE]
> 針對桌面沉浸式耳機，設定穩定平面通常會有生產力，因為它提供的視覺效果品質比將應用程式的深度緩衝區提供給系統來啟用以圖元為基礎的深度 reprojection 更低。 除非在 HoloLens 上執行，否則您通常應該避免設定穩定平面。

![3D 物件的穩定平面](images/stab-plane-500px.jpg)

裝置會自動嘗試選擇此平面，但應用程式應該藉由選取場景中的焦點點來協助。 在 HoloLens 上執行的 Unity 應用程式應該根據您的場景選擇最佳焦點，並將它傳遞到[SetFocusPoint （）](focus-point-in-unity.md)。 預設的旋轉 cube 範本中包含設定 DirectX 中焦點點的範例。

當您在連接到桌上型電腦的沉浸式耳機上執行應用程式時，Unity 會將您的深度緩衝區提交至 Windows 以啟用每個圖元的 reprojection，如此一來，應用程式就能提供更佳的影像品質，而不需要明確運作。 當您的應用程式在 HoloLens 上執行時，您應該只提供焦點，否則會覆寫每個圖元的 reprojection。


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

重點放在主要取決於全息影像的外觀。 應用程式有參考的注視向量，而應用程式設計師知道他們想要讓使用者觀察哪些內容。

開發人員可以對穩定的全像投影執行的最重要的事，就是在 60 FPS 呈現。 低於 60 FPS 會大幅降低全像全像穩定平面優化。

**最佳做法**沒有任何通用的方式可設定穩定平面，而且它是應用程式特定的。 我們的主要建議是實驗並查看最適合您案例的方式。 不過，請儘量將穩定平面的內容對齊，因為這個平面上的所有內容都是完美穩定的。

例如：
* 如果您只有平面內容（讀取應用程式、影片播放應用程式），請將穩定平面與具有內容的平面對齊。
* 如果有三個世界鎖定的小球體，請讓穩定平面「剪下」，但目前在使用者觀點中的所有球中心。
* 如果您的場景有非常不同深度的內容，則偏好進一步的物件。
* 請務必調整每個畫面格的穩定點，使其與使用者正在查看的全息影像一致

**要避免的事項**穩定平面是達到穩定全息的絕佳工具，但如果誤用，可能會導致嚴重的映射不穩定。
* 不要「引發並忘」。 最後，您可以使用使用者背後的穩定平面，或連接到不在使用者觀點中的物件。 確保穩定平面的法線設定為相對的相機向前（例如，-攝影機. forward）
* 不要在極端之間來回地快速變更穩定平面
* 不要讓穩定平面設定為固定距離/方向
* 不要讓穩定平面剪下使用者
* 請勿在桌上型電腦（而不是 HoloLens）上執行時設定焦點，而是依賴每個圖元的深度 reprojection。

## <a name="color-separation"></a>色彩分隔 

由於 HoloLens 顯示的本質，有時可以察覺稱為「色彩分隔」的成品。 它會以影像分隔成個別的基本色彩-紅色、綠色和藍色。 顯示白色物件時，可以特別看到成品，因為它們有大量的紅色、綠色和藍色。 當使用者以視覺化方式追蹤在全像全像全像全像攝影的畫面格上移動的全像投影時，最明顯的是。 另一種構件可以資訊清單的方式是物件的扭曲/變形。 如果物件具有高對比和/或純粹色彩，例如紅色、綠色、藍色，則會將色彩分隔視為物件不同部分的變形。

**例如，當使用者將其標頭旋轉至一邊時，標頭鎖定白色圓形游標的色彩分隔可能會類似：**

![例如，當使用者將其標頭旋轉至一邊時，標頭鎖定的白色圓形游標的色彩分隔外觀。](images/colorseparationofroundwhitecursor-300px.png)

雖然很難完全避免色彩分隔，但有幾種方法可以減輕它的問題。

**可以在下列情況看到色彩分隔：**
* 快速移動的物件，包括標頭鎖定的物件（例如[游標](cursors.md)）。
* 遠低於[穩定平面](hologram-stability.md#reprojection)的物件。

**若要 attenuate 色彩分隔的效果：**
* 讓物件延後使用者的注視。 它看起來應該像是有一些慣性，並且附加至注視「的彈簧」上。 這種方法會使游標變慢（減少分隔距離），並將它放在使用者可能的注視點後方。 只要它很快就會發生，當使用者停止切換時，就會感覺到自然。
* 如果您想要移動全息影像，請嘗試將其移動速度維持在每秒5度以下，如果您預期使用者會跟隨其眼睛。
* 針對資料指標使用*light*而不是*geometry* 。 附加至注視的虛擬照明來源會被視為互動式指標，但不會造成色彩分隔。
* 調整穩定平面，使其符合使用者撥雲見日的全息影像。
* 將物件設為紅色、綠色或藍色。
* 切換至模糊版本的內容。 例如，您可以將圓形白色游標變更為動作方向中稍微模糊的線條導向。

如先前所示，在 60 FPS 和設定穩定平面的情況下，是最重要的全像影像穩定性技術。 如果面對明顯的色彩分隔，請先確定畫面播放速率符合預期。

## <a name="see-also"></a>請參閱
* [瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)
* [色彩、光線和材質](color,-light-and-materials.md)
* [本能互動](interaction-fundamentals.md)
* [MRTK 全息影像穩定](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html)
