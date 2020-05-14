---
title: Unreal 中的空間錨點
description: 在 Unreal 中使用空間錨點的指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 空間錨點
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840137"
---
# <a name="spatial-anchors-in-unreal"></a>Unreal 中的空間錨點

空間錨點是用來在應用程式工作階段之間，在真實世界空間中保持全像投影。  這會透過 Unreal 呈現為 ARPins，並儲存在 HoloLens 的錨點存放區中，以在未來的工作階段中載入。 

在儲存或載入錨點之前，請先檢查錨點存放區已就緒。  在錨點存放區準備就緒之前，嘗試呼叫任何 HoloLens 錨點功能將會失敗。  

![空間錨點存放區就緒](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a>儲存錨點

一旦應用程式具有需要釘選到世界的元件，就可以下列序列儲存到錨點存放區： 

![空間錨點儲存](images/unreal-spatialanchors-save.PNG)

在這裡，我們會在已知位置繁衍動作項目、使用該位置建立 ARPin 並且根據動作項目的類別命名、將動作項目新增至 ARPin，以及將釘選儲存到 HoloLens 錨點存放區。  我們選擇的錨點名稱必須是唯一的，因此在這個範例中我們會附加目前的時間戳記。  如果錨點成功儲存至錨點存放區，則可以在 [系統] > [對應管理員] > [裝置上儲存的錨點檔案] 底下的 HoloLens 裝置入口網站中，檢查該錨點。 

## <a name="load-anchors"></a>載入錨點

當應用程式啟動時，可以呼叫下列藍圖來將元件還原至其錨點位置：

![空間錨點載入](images/unreal-spatialanchors-load.PNG)

在此範例中，我們會逐一查看錨點存放區中的所有錨點、在身分識別繁衍動作項目，並將該動作項目從錨點存放區釘選到 ARPin。  請務必在身分識別繁衍動作項目，因為錨點會負責根據儲存位置在世界中重新放置全像投影，因此此處新增的任何轉換都會將位移新增至錨點。 

也會查詢錨點識別碼，以便根據錨點的儲存名稱來繁衍不同的動作項目。 

## <a name="remove-anchors"></a>移除錨點 

當完成使用錨點時，可以清除整個錨點存放區，或從錨點存放區移除個別錨點，使其不包含在未來的工作階段中： 

![空間錨點移除](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a>另請參閱
* [空間錨點](spatial-anchors.md)
* [座標系統](coordinate-systems.md)
