---
title: Unreal 中的 QR 代碼
description: 在 Unreal 中使用 QR 代碼的指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, qr 代碼
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342656"
---
# <a name="qr-codes-in-unreal"></a>Unreal 中的 QR 代碼

HoloLens 可以在世界空間中找到 QR 代碼，以在真實世界中的已知位置轉譯全像投影。  這也可以用來在相同位置中的多個裝置上轉譯全像投影，以建立共用體驗。 

若要在 HoloLens 上啟用 QR 偵測，請確定已在 [專案設定] > [平台] > [HoloLens] > [功能] 下的 Unreal 編輯器中勾選「網路攝影機」功能。  

藉由使用 StartARSession 函式來啟動 ARSession，以選擇在 Unreal 中使用 QR 代碼追蹤。 

QR 代碼會透過 Unreal 的 AR 追蹤幾何系統呈現為追蹤的影像。  若要使用這個功能，請將 AR 可追蹤通知元件新增至藍圖	動作項目： 

![QR AR 可追蹤通知](images/unreal-spatialmapping-artrackablenotify.PNG)

然後移至元件的詳細資料，並且按一下要監視事件的綠色 "+" 按鈕。  

![QR 事件](images/unreal-spatialmapping-events.PNG)

在這裡，我們訂閱了 OnUpdateTrackedImage，以在 QR 代碼的中央呈現點，並列印 QR 代碼的編碼資料。 

![QR 轉譯範例](images/unreal-qr-render.PNG)

首先將追蹤的影像轉型為 ARTrackedQRCode，以確認目前更新的影像是 QR 代碼。  然後，您可以使用 QRCode 變數來擷取編碼的資料。  您可以從 GetLocalToWorldTransform 的位置擷取 QR 代碼的左上角。  您可以使用 GetEstimateSize 來擷取維度。 

每個 QR 代碼也有唯一的 GUID 識別碼： 

![QR GUID](images/unreal-qr-guid.PNG)

## <a name="see-also"></a>另請參閱
* [QR 代碼追蹤](qr-code-tracking.md)
