---
title: 空間的錨點
description: 最佳作法來呈現穩定全像投影中使用空間的錨點的詳細資訊。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系統、 空間座標系統、 全球規模、 全球、 小數位數、 位置、 方向、 錨點、 空間的錨點、 世界鎖定時，世界鎖定的持續性，共用
ms.openlocfilehash: eb0fae7881f1b6517da57305ef2fa3cb1ed78648
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597127"
---
# <a name="spatial-anchors"></a>空間的錨點

空間的錨點表示系統應該追蹤的一段時間的世界中很重要的一點。 每個錨點已[座標系統](coordinate-systems.md)的參考框架，以確保錨定全像投影保持精確地在放置或如有需要相對於其他的錨點，可調整的情況。  轉譯錨點的座標系統中全像圖可讓您在任何時候最精確的設定位置來進行該全像圖。 這個代價小幅度的調整一段時間至全像的位置，因為系統持續將它移回至相對於真實世界的地方。

您也可以保存，並跨應用程式工作階段和跨裝置共用空間的錨點：
* 藉由將本機空間錨點儲存到磁碟和更新版本重新的載入，您的應用程式可以理解真實世界中相同的位置，在單一的 HoloLens 裝置上的多個應用程式工作階段之間。
* 藉由使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>若要建立雲端錨點，您的應用程式可以跨多個 HoloLens、 iOS 和 Android 裝置共用空間的錨點。 擁有呈現雷射，使用相同的空間錨點的每個裝置，所有的使用者會看到全像圖會出現在真實世界中相同的位置。  這可讓您即時分享經驗。
* 您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>非同步闀持續性跨 HoloLens、 iOS 和 Android 裝置。  藉由共用持久的雲端空間錨點，多個裝置可以觀察相同的保存全像經過一段時間，即使這些裝置不存在一起在相同的時間。

針對常設-小數位數或聊天室擴展體驗將會維持在 5 公尺直徑內的行動網卡桌面耳機，您通常只可以使用[階段參照](coordinate-systems.md#stage-frame-of-reference)而不空間的錨點，提供您單一用於轉譯的所有內容的座標系統。 不過，如果您的應用程式想要讓超過 5 公尺走廊 HoloLens 上的使用者，則可能作業系統在整個的建築物、 樓層您必須空間的錨點，以保留內容穩定。

適用於全像投影應該保持固定在世界中，一旦放錨點是空間的錨點時，它無法移動。 有更適合動態全像投影，以及使用者應標記的錨點的替代方案。 最好的方式是使用靜態參考座標系 （Unity 的全局座標為基礎） 或附加的畫面格的參考動態全像投影的位置。

## <a name="best-practices"></a>最佳作法

這些空間的錨點指導方針可協助您呈現穩定全像投影，以精確追蹤真實的世界。

### <a name="create-spatial-anchors-where-users-place-them"></a>建立使用者放置它們的空間錨點

大部分的情況下，使用者應該明確地放置空間的錨點的項目。

比方說，在 HoloLens，應用程式有交集的使用者[視線](gaze.md)與光線[空間對應](spatial-mapping.md)網狀結構，讓使用者決定雷射的位置。 當使用者點選要放置該全像圖時，建立空間的錨點交集處，並接著將全像圖放在該錨點的座標系統的原點。

本機空間錨點進行，若要建立，高效能和系統會將其內部的資料如果多個錨點可以共用其基礎的感應器資料。 通常，您應該建立新本機空間錨點的使用者明確地將，每個全像下面所述，例如全像投影的固定群組的情況除外。

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>一定會轉譯錨定在其錨定的 3 公尺全像投影

空間的錨點來穩固其錨點的原始附近的座標系統。 如果您從該原點超過約 3 公尺呈現全像投影，這些全像投影可能會遇到比例從該原點，由於推桿 arm 效果的距離明顯位置錯誤。 適用於使用者代表附近錨點，因為全像太遠從使用者，這表示較遠的全像 angular 錯誤會很小。 不過，如果使用者可走到該較遠的全像圖，然後會在他們的檢視，使遠處的錨點的原始推桿 arm 效果很明顯大。

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>群組全像應該形成固定叢集投影

如果應用程式必須要有這些維護固定的關聯性，以另一個全像投影，多個全像投影可以共用相同空間的錨點。

比方說，如果您以動畫顯示房間內的全像攝影版太陽系，最好將所有單一的錨點太陽系物件繫結在管理中心中，使其相對於其他順暢地移動。 在此情況下，它是太陽系整體而言，錨定，即使其元件部分將以動態方式移動周圍的錨點。

金鑰必須注意維護全像穩定性是遵循上述的 3 計量規則。

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>轉譯高動態全像投影使用靜態參考座標系，而不本機的空間錨點

如果您有高動態的雷射，例如出外四處空間或遵循使用者附近的牆浮動 UI 字元最好是略過本機空間錨點，並呈現這些全像投影所提供的座標系統中的直接[</c0>靜態參考座標系<spanclass="notranslate">](coordinate-systems.md#stationary-frame-of-reference)（也就是在 Unity 中，您達到此目的而 WorldAnchor 不全局座標中直接置於全像投影）。</span> 在靜態參考座標系全像投影時可能會遇到漂移使用者遠低於全像圖，但這不太可能會注意到的動態全像投影： 全像經常移動，或其影片持續保持它接近使用者其中漂移會降到最低。

動態全像投影的其中一個有趣的案例是一種錨定的座標系統到另一個以動畫顯示的物件。 比方說，您可能會有兩個 castle 化 10 公尺，在他們自己的空間錨點，每個引發在其他 castle cannonball 一個 castle。 目前 cannonball 引發時，您可以在靜態參考座標系，以便與第一個的 castle 錨定的座標系統中 cannon 一致的適當位置轉譯。 它接著可以遵循其檔案在空中 10 公尺其軌跡中靜態參考座標系。 當 cannonball 到達其他 castle 時，您可以選擇將移到第二個的 castle 錨定的座標系統，以供物理具有該 castle 固定的內文的計算。

如果您在裝置之間共用高動態的全像圖，您必須挑選做為其父代，某些雲端空間錨點，以在裝置間無法共用的 「 定態的參考框架。  不過，在此情況下，您應該確定是動態的全像圖或檢視的裝置都保留在錨點的 3 個計量半徑，以確保全像圖會出現在所有裝置上的穩定。

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>避免建立空間的錨點的方格

您可能會想要讓使用者將逐步引導，移動錨定至錨點轉換動態物件卸除規則方格空間的錨點的應用程式。 不過，這牽涉到大量管理您的應用程式，而不需要系統本身會在內部維護深入的感應器資料的好處。 在這些情況下，您通常會達到更好的結果，更不費力放置您全像投影中的靜態參考座標，如上節所述。

當預先定位雲端靜態空格周圍的空間錨點的一組，請考慮將空間的錨點放在使用者將會遇到上述，原則每金鑰全像投影的位置，而不是建立任意方格中的錨點。  這可確保您會取得這些金鑰全像投影最大的穩定性。

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>發行您不再需要的本機空間錨點

本機空間錨點作用中時，系統會排定優先順序接近該錨點的感應器資料的保留。 如果您無法再使用空間的錨點，用來存取其座標系統的停駐點。 這可讓視要移除其基礎感應器資料。

這是您已保存至空間的錨點存放區的本機錨點特別重要。 這些錨點背後的感應器資料會保留周圍永久允許您的應用程式，以尋找會錨定在未來的應用程式工作階段，這會減少追蹤其他的錨點的可用空間。 保存只有這些本機錨點，您需要再次在未來的工作階段中找到並移除它們從存放區時，它們不會再對使用者有意義。

針對雲端空間錨點，隨著您的案例需要，可以調整您的儲存體。  您可以儲存多個雲端錨點如有需要您知道您的使用者將不需要再次會錨定在尋找全像投影時，才將它們釋出。

## <a name="see-also"></a>另請參閱
* [座標系統](coordinate-systems.md)
* [在混合實境中共用體驗](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>
* [在 Unity 中的持續性](persistence-in-unity.md)
* [DirectX 中的空間錨點](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [案例研究-仔細檢查您實際上的漏洞](case-study-looking-through-holes-in-your-reality.md)
