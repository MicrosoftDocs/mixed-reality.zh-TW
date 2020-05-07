---
title: 場景理解
description: 適用于 HoloLens 的場景理解功能簡介
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 場景理解，空間對應，Windows Mixed Reality，Unity
ms.openlocfilehash: 615da20df95f4a435216457e8b9f16bb7d7d069b
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604959"
---
# <a name="scene-understanding"></a>場景理解

場景理解為混合現實開發人員提供結構化的高階環境標記法，其設計目的是為了讓環保感知應用程式的開發更加直覺。 場景理解是藉由結合現有混合現實執行時間的強大功能來達成，例如，高度精確的結構[空間對應](spatial-mapping.md)和新的 AI 驅動執行時間。 藉由結合這些技術，場景理解會產生類似于您在 Unity 或 ARKit/ARCore 等架構中使用之3D 環境的標記法。 場景理解進入點從場景觀察者開始，您的應用程式會呼叫它來計算新場景。 目前，此技術能夠產生3個相異但相關的物件類別：簡化的防水環境網格，可推斷平面室結構，而不會雜亂、放置我們呼叫四邊形的平面區域，以及與我們呈現的四邊形/防水資料對齊的[空間對應](spatial-mapping.md)網格的快照。

![空間對應網格，標示平面表面，防水網格](images/SUScenarios.png)

本檔的目的是要提供案例總覽，並澄清場景瞭解和空間對應共用的關聯性。

## <a name="developing-with-scene-understanding"></a>使用場景理解進行開發

本文僅適用于介紹場景的瞭解執行時間和概念。 如果您要尋找有關如何使用場景理解進行開發的檔，您可能會對下列各項感興趣：

[場景理解 SDK 總覽](scene-understanding-SDK.md)

您可以從範例 GitHub 網站下載場景瞭解範例應用程式：

[場景理解範例](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

如果您沒有裝置，而且想要存取範例場景來嘗試進行場景瞭解，範例資產資料夾中會有場景：

[場景瞭解範例場景](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

如果您要尋找如何開發以進行場景瞭解的特定詳細資料，或是場景理解如何運作的詳細資料，以及如何為其進行開發，請參閱[場景瞭解 SDK 總覽](scene-understanding-SDK.md)檔。


### <a name="sample"></a>範例


## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第1代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>場景理解</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>常見使用案例

![一般空間對應使用案例的圖例：位置、遮蔽、物理和流覽](images/sm-concepts-1000px.png)<br>
*常見的空間對應使用案例：位置、遮蔽、物理和導覽。*

<br>

環境感知應用程式的許多核心案例（放置、遮蔽、物理等等）都可透過空間對應和場景理解來定址，而本節將強調這些差異。 「場景理解」和「空間對應」之間的主要差異，是針對結構和簡易性的最大精確度和延遲進行取捨。 如果您的應用程式需要只有您想要存取的最低延遲可能和網格三角形，請直接使用空間對應。 如果您要執行較高層級的處理，您可以考慮改用「場景理解模型」，因為它應該提供您功能的超集合。 另請注意，由於場景理解會提供空間對應網格的快照集作為其表示方式的一部分，因此您一律可以存取最完整且正確的空間對應資料。

下列各節會重新流覽新場景理解 SDK 內容中的核心空間對應案例。

### <a name="placement"></a>放置

場景理解提供專為簡化放置案例而設計的新結構。 場景可以計算名為 SceneQuads 的基本型別，其中描述可以放置全息影像的平面表面。 SceneQuads 特別設計于放置和描述2D 介面，並提供 API 以放置在介面上。 先前，使用三角形網格來執行放置時，必須掃描所有的四個區域，並執行洞填滿/後置處理，以識別出適合物件放置的位置。 這不一定是四邊形的必要，因為場景理解執行時間能夠推斷出四個未掃描的區域，而使四個不屬於介面的區域失效。

:::row:::
    :::column:::
       ![已停用推斷的 SceneQuads，可捕捉掃描區域的放置區域。](images/SUQuads.png)<br>
       **影像 #1** -已停用推斷的 SceneQuads，可捕捉掃描區域的放置區域。
    :::column-end:::
        :::column:::
       ![已啟用推斷的四邊形，放置不再限於掃描的區域。](images/SUWatertight.png)<br>
        **影像 #2** -已啟用推斷的四邊形，放置不再限於掃描的區域。
    :::column-end:::
:::row-end:::

<br>


如果您的應用程式想要在您環境的固定結構上放置2D 或3D 全息，最好是從[空間對應](spatial-mapping.md)網格中計算這項資訊，以便於放置 SceneQuads 的簡單性和便利性。 如需本主題的詳細資訊，請參閱[場景瞭解 SDK 參考](scene-understanding-SDK.md)

**注意**對於相依于空間對應網格的舊版放置程式碼，可以藉由設定 EnableWorldMesh 設定來計算空間對應網格和 SceneQuads。 如果場景理解 API 無法滿足您應用程式的延遲需求，我們建議您繼續使用[空間對應 API](spatial-mapping.md#placement)。

### <a name="occlusion"></a>遮蔽

[空間對應遮蔽](spatial-mapping.md#occlusion)仍然是捕捉環境即時狀態的最不潛在方式。 雖然這可能有助於在高度動態的場景中提供遮蔽，但您可能會想要考慮針對遮蔽的場景理解，原因有好幾個。 如果您使用場景理解所產生的空間對應網格，您可以從空間對應要求不會儲存在本機快取中的資料，因此不會從認知 Api 提供給您。 使用遮蔽與防水網格的空間對應將會提供額外的價值，特別是完成未掃描的聊天室結構。

如果您的需求可容忍場景理解的延遲增加，應用程式開發人員應該考慮使用場景理解防水網格，而空間對應網格則與平面表示一致。 這會提供「兩種世界的最佳」案例，其中簡化的防水遮蔽會使用更精細的 nonplanar 幾何，以提供最實際的遮蔽地圖。

### <a name="physics"></a>物理

場景理解會產生使用語義分解空間的防水網格，特別是為了解決空間對應網格所強加的許多物理限制。 防水結構可確保物理光線轉換一律會被叫用，而語義分解則允許針對室內導覽較簡單的 nav 網格產生。 如[遮蔽](#occlusion)一節中所述，使用 EnableSceneObjectMeshes 和 EnableWorldMesh 建立場景，將會產生最實際的完整網格。 環境網格的 [防水] 屬性會防止點擊的測試無法到達介面，而網格資料會確保物理與場景中的所有物件互動，而不只是與房間結構互動。

### <a name="navigation"></a>導覽

依語義類別分解的平面網格是理想的導覽和路徑規劃結構，可簡化[空間對應導覽](spatial-mapping.md#navigation)總覽中所述的許多問題。 在場景中計算的 SceneMesh 物件已由表面類型取消群組，確保 nav 層代僅限於可以導覽的表面。 由於 floor 結構的簡單性，3d 引擎（例如 Unity）中的動態 nav 網格產生會根據即時需求而達到。

產生精確的導覽網格目前仍需要後置處理，也就是應用程式仍然必須在樓層上進行阻隔器，以確保導覽不會通過雜亂/資料表等等 .。。完成此動作最精確的方式是，在使用 EnableWorldMesh 旗標來計算場景時，針對所提供的世界網格資料進行投影。

### <a name="visualization"></a>視覺效果

雖然[空間對應視覺效果](spatial-mapping.md#visualization)可以用於環境的即時意見反應，但在許多情況下，平面和防水物件的簡單性可提供更高的效能或視覺品質。 如果投影在四邊形或平面防水網格所提供的平面表面上，使用空間對應所描述的陰影投射和接地技術可能會更滿意。 特別是在環境/案例中，因為場景將會推斷，而完整的預先掃描並不是最理想的情況，而完成的環境和平面假設會將成品降到最低。

此外，空間對應所傳回的表面總數會受到內部空間快取的限制，而場景理解的空間對應網格版本則能夠存取未快取的空間對應資料。 因此，場景理解較適合用來針對視覺效果或進一步的網格處理來捕獲較大空間的網格標記法（例如，大於單一房間）。 以 EnableWorldMesh 傳回的世界網格會在整個中具有一致的詳細資料層級，如果轉譯為線框，這可能會產生更令人滿意的視覺效果。

### <a name="see-also"></a>另請參閱

* [場景理解 SDK](scene-understanding-SDK.md)
* [空間對應](spatial-mapping.md)
