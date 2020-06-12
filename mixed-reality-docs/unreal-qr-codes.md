---
title: Unreal 中的 QR 代碼
description: 在 Unreal 中使用 QR 代碼的指南
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, qr 代碼
ms.openlocfilehash: 90a51227ae455389168fb3262e83f34b64a7bfb5
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428746"
---
# <a name="qr-codes-in-unreal"></a>Unreal 中的 QR 代碼

## <a name="overview"></a>概觀

HoloLens 2 可以使用網路攝影機查看世界空間中的 QR 代碼，這會在每個代碼的真實世界位置中使用座標系統將其呈現為全息投影。  除了單一 QR 代碼外，HoloLens 2 還可以在相同位置的多個裝置上呈現全像投影，以建立共用體驗。 確定您遵循將 QR 代碼新增至應用程式的最佳作法：

- 寧靜區域
- 光源和底圖
- 大小、距離和角度位置

將 QR 代碼放在您的應用程式時，請特別注意[環境考量](environment-considerations-for-hololens.md)。 您可以在其中每一個主題上找到詳細資訊，以及在主要 [QR 代碼追蹤](qr-code-tracking.md)文件中找到如何下載所需 NuGet 套件的指示。 

## <a name="enabling-qr-detection"></a>啟用 QR 偵測
因為 HoloLens 2 需要使用網路攝影機來查看 QR 代碼，所以您必須在專案設定中將其啟用：
- 開啟 [編輯] > [專案設定]捲動至 [平台] 區段，然後按一下 [HoloLens]。
    + 展開 [功能] 區段，並勾選 [網路攝影機]。  

您也必須[新增 ARSessionConfig 資產](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)，來加入 QR 代碼追蹤。

## <a name="setting-up-a-tracked-image"></a>設定追蹤的影像

QR 代碼會透過 Unreal 的 AR 追蹤幾何系統呈現為追蹤的影像。 若要讓此作業運作，您必須：
1. 建立藍圖並新增 **ARTrackableNotify** 元件。

![QR AR 可追蹤通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. 選取 [ARTrackableNotify]，然後展開 [詳細資料] 面板中的 [事件] 區段。 

![QR 事件](images/unreal-spatialmapping-events.PNG)

3. 按一下 [On Add Tracked Geometry] 旁邊的 **+** ，將節點新增至事件圖形。
    - 您可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 元件 API 中找到完整的事件清單。 

![QR 轉譯範例](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a>使用追蹤的影像
下圖中的事件圖形會顯示用來在 QR 代碼中心呈現點的 **OnUpdateTrackedImage** 事件，並印出其資料。 

![QR 轉譯範例](images/unreal-qr-render.PNG)

以下是後續動作：
1. 首先，追蹤的影像會強制轉型為 **ARTrackedQRCode**，以檢查目前更新的影像是否為 QR 代碼。  
2. 編碼的資料是從 **QRCode** 變數中擷取的。 您可以從 **GetLocalToWorldTransform** 的位置，以及具有 **GetEstimateSize** 的維度，到達 QR 代碼的左上角。 

您也可以在程式碼中[取得 QR 代碼的座標系統](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)。

## <a name="finding-the-unique-id"></a>尋找唯一識別碼
每個 QR 代碼都有唯一的 guid 識別碼，您可以透過下列方式找到該識別碼：
- 拖放 **As ARTracked QRCode** 釘選並搜尋 [取得唯一識別碼]。

![QR GUID](images/unreal-qr-guid.PNG)

QR 代碼在幕後還有很多工作要做，因此這不是盡頭。 請務必查看下列連結，以取得有關幕後內容的詳細資訊。

## <a name="see-also"></a>另請參閱
* [空間對應](spatial-mapping.md)
* [全像投影](hologram.md)
* [座標系統](coordinate-systems.md)