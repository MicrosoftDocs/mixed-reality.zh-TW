---
title: 空間錨點
description: 使用空間錨點轉譯穩定全像投影的最佳做法。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系統、空間座標系統、全球規模、全球、規模、位置、方向、錨點、空間錨點、已全球鎖定、正進行全球鎖定、持續性、共用
ms.openlocfilehash: 27b1dcd86c7edba176ca54840bdd27550736a16d
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387735"
---
# <a name="spatial-anchors"></a>空間錨點

空間錨點代表世界中系統持續追蹤一段時間的重要點。 每個錨點都有一個會視需要調整 (相對於其他錨點或參考架構) 的[座標系統](coordinate-systems.md) ，以確保錨定的全像投影能維持準確定位。  在錨點的座標系統中轉譯全像投影，可以在任何指定的時間為您提供最準確的全像投影定位。 這是因為系統持續將其移回相對於真實世界的位置, 而將一段時間內的小型調整成本降低。

您也可以跨應用程式會話和跨裝置保存和共用空間錨點:
* 藉由將本機空間錨點儲存至磁片並于稍後將其載入, 您的應用程式可以在單一 HoloLens 上的多個應用程式會話之間計算相同的位置。
* 藉由使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>來建立雲端錨點, 您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置之間共用空間錨點。 藉由讓每個裝置使用相同的空間錨點來轉譯全像投影, 使用者會看到全像是在真實世界中的同一個位置出現了全息影像。 這可提供即時共用體驗。
* 您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。 藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。

針對行動網卡桌面耳機的大規模或室內延展體驗, 會維持在5計量的直徑範圍內, 您可以通常使用[參考的階段框架](coordinate-systems.md#stage-frame-of-reference), 而不是空間錨點, 這會提供您要在其中執行的單一座標系統。呈現所有內容。 不過, 如果您的應用程式想要讓使用者在 HoloLens 中穿梭超過5計量, 可能會在大樓的整個樓層中運作, 您將需要空間錨點以保持內容穩定。

雖然空間錨點對於在真實世界中應保持固定的全像投影非常有用，但是一旦將錨點放至定位，就無法移動它。 錨點有一些替代方式, 適用于與使用者一起標記的動態全息影像。 最好使用靜止的參考架構 (Unity 的世界座標基礎) 或附加的參考架構來定位動態全像投影。

## <a name="best-practices"></a>最佳作法

這些空間錨點指南將協助您轉譯穩定、且能準確追蹤現實世界的全像投影。

### <a name="create-spatial-anchors-where-users-place-them"></a>建立使用者放置的空間錨點

一般而言, 使用者是明確放置空間錨點的使用者。

例如, 在 HoloLens 上, 應用程式可以將使用者的[注視](gaze.md)光線與[空間對應](spatial-mapping.md)網格相交, 讓使用者決定要放置全息的位置。 當使用者按下以放置該全息影像時, 請在交集點建立空間錨點, 然後將全息影像放在錨點座標系統的原點。

本機空間錨點既容易又高效能, 可以建立。 如果多個錨點可以共用其基礎感應器資料, 系統會合並其內部資料。 您通常應該為使用者明確放置的每個全息影像建立新的本機空間錨點, 但以下所述的情況除外, 例如固定的全息影像群組。

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>一律轉譯位於錨點 3 公尺範圍內的錨定全像投影

空間錨點可穩固錨點原始位置附近的座標系統。 如果您從該原點轉譯超過3計量的全息影像, 這些全息影像可能會遇到明顯的位置錯誤, 與從該來源與原點的距離相比, 這是因為杠杆臂的效果。 這適用于使用者在錨點附近的情況, 因為全息影像與使用者的距離並不相同。 換句話說, 遠處的全息影像的角度錯誤將會很小。 不過, 如果使用者逐步解說該最遠的全像投影, 它就會變大, 讓遠方錨定來源的拉杆臂效果非常明顯。

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>應形成固定叢集的群組全像投影

如果應用程式預期這些全息影像彼此維持固定的關聯性, 多個全息影像就可以共用相同的空間錨點。

例如, 如果您要在房間內建立全像攝影的日光系統動畫, 最好將所有的日光系統物件系結到中央的單一錨點, 讓它們彼此順暢地移動。 在這個情況下，即使各個元件部分會圍繞錨點動態移動，整個太陽系也會維持錨定狀態。

維護全像影像穩定性的重要注意事項是遵循上述的3計量規則。

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>使用靜止的參考架構而不是本機空間錨點來轉譯高動態全像投影

如果您有高動態的全像投影, 例如沿著靠近使用者附近的房間或浮動 UI 的字元, 則最好略過本機空間錨點, 並直接在所提供[的座標系統中轉譯那些全息影像固定的參考框架](coordinate-systems.md#stationary-frame-of-reference)。 我的 Unity 是將全息影像直接放在全局座標中, 而不需要 WorldAnchor, 藉此達到這個目的。 在靜止的參考框架中的全息影像, 可能會在使用者距離全息影像時遇到漂移。 但對於動態的全息影像而言, 這不太可能很明顯: 可能是因為全息影像經常移動, 或其動作會持續靠近使用者, 讓漂移降至最低。

動態全像投影的一個有趣的例子是一個物件從某個錨定座標系統移動至另一個座標系統的動畫。 例如, 您可能會有兩個 castles 的10計量, 每個都在自己的空間錨點上, 其中有一個 castle 引發另一個 castle 的 cannonball。 在 cannonball 引發時, 您可以在固定的參考框架中的適當位置轉譯它, 以便與第一個 castle 的錨定座標系統中的 cannon 一致。 然後它可以在靜止的參考架構中追蹤砲彈在空中飛行 10 公尺的軌跡。 當 cannonball 到達另一個 castle 時, 您可以選擇將它移到第二個 castle 的錨定座標系統, 以允許使用該 castle 的固定主體進行物理計算。

如果您要跨裝置共用高度動態的全息影像, 您必須挑選一些雲端空間錨點作為其父系, 因為無法在裝置之間共用固定的參考框架。  不過, 在此情況下, 您應該確保動態的全息影像或裝置的流覽會保留在錨點的3計量半徑內, 以確保所有裝置上的全像投影顯示穩定。

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>避免建立空間錨點的網格

當使用者四處移動時, 您可能會想要讓應用程式卸載一般的空間錨點方格, 將動態物件從錨點轉換至錨點。 不過, 這牽涉到許多應用程式的管理, 而不會有系統本身在內部維護的深層感應器資料的好處。 在這些情況下, 您通常會將您的全息影像放在固定的參考框架中, 以較少的方式獲得更好的結果, 如上述一節中所述。
將一組雲端空間錨點放在靜態空間的前面時, 請考慮將空間錨點放置在使用者根據上述原則所遇到的按鍵的位置, 而不是建立任意的錨點格線。 這可確保您能夠讓那些關鍵的全像投影獲得最高的穩定性。

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>釋出您不再需要的本機空間錨點

當本機空間錨點處於作用中狀態時, 系統會優先保留該錨點附近的感應器資料。 如果您無法再使用空間錨點，請停止存取其座標系統。 如此一來, 就可以視需要移除其基礎感應器資料。

對於您已保存至空間錨點存放區的本機錨點來說，這一點特別重要。 這些錨點背後的感應器資料將會永久保留, 以允許您的應用程式在未來的會話中尋找該錨點, 進而減少追蹤其他錨點的可用空間。 只保存您需要在未來會話中再次尋找的本機錨點, 並在不再對使用者有意義時, 將它們從存放區中移除。

對於雲端空間錨點，您的儲存體可以依照案例需要調整規模。 您可以視需要儲存多個雲端錨點, 只有在您知道您的使用者不需要再次尋找該錨點的全息影像時, 才會釋出它們。

## <a name="see-also"></a>另請參閱
* [座標系統](coordinate-systems.md)
* [混合實境中的共用體驗](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Unity 中的持續性](persistence-in-unity.md)
* [DirectX 中的空間錨點](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [案例研究 - 在實境中的的透視技術](case-study-looking-through-holes-in-your-reality.md)
