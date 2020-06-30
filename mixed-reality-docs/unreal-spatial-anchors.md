---
title: Unreal 中的空間錨點
description: 在 Unreal 中使用空間錨點的指南
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 空間錨點
ms.openlocfilehash: 58394f4e27aff5070d55ed5f0d62cd81ff579d1f
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720314"
---
# <a name="spatial-anchors-in-unreal"></a>Unreal 中的空間錨點

## <a name="overview"></a>概觀

空間錨點是用來在應用程式工作階段之間，在真實世界空間中儲存全像投影。  這些會透過 Unreal 呈現為 **ARPins**，並儲存在 HoloLens 的錨點存放區中，可在未來的工作階段中載入。 

## <a name="checking-the-anchor-store"></a>檢查錨定存放區

在儲存或載入錨點之前，必須先檢查錨點存放區是否準備就緒。  在錨點存放區準備就緒之前，呼叫任何 HoloLens 錨點功能將會失敗。  

![空間錨點存放區就緒](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a>儲存錨點

一旦應用程式具有需要釘選到世界的元件，就可以下列序列儲存到錨點存放區： 

![空間錨點儲存](images/unreal-spatialanchors-save.PNG)

將此細分：
1. 在已知位置繁衍動作項目。
2. 根據動作項目的類別，建立具有該位置和名稱的 **ARPin**。 
3. 將動作項目新增至 **ARPin**，並將圖釘儲存至 HoloLens 錨點存放區。  
    * 您選擇的錨點名稱必須是唯一的，在這個範例中，其為目前的時間戳記。 

4. 如果錨點成功儲存至錨點存放區，則您可以在 [系統] > [對應管理員] > [裝置上儲存的錨點檔案] 底下的 HoloLens 裝置入口網站中，檢查該錨點。 

## <a name="loading-anchors"></a>載入錨點

當應用程式啟動時，您可以使用下列藍圖來將元件還原至其錨點位置：

![空間錨點載入](images/unreal-spatialanchors-load.PNG)

將此細分：
1. 逐一查看錨點存放區中的所有錨點。 
2. 在身分識別中繁衍動作項目。
3. 從錨點存放區將該動作項目釘選到 **ARPin**。  

    * 請務必在身分識別繁衍動作項目，因為錨點會負責根據儲存位置在世界中重新放置全像投影。 此處新增的任何轉換都會將位移新增至錨點。 

也會查詢錨點識別碼，以便根據錨點的儲存名稱來繁衍不同的動作項目。 

## <a name="removing-anchors"></a>移除錨點 

當您完成錨點時，可以使用 **Remove ARPin from WMRAnchor Store** 和 **Remove All ARPins from WMRAnchor Store** 元件，清除個別錨點或整個錨點存放區。

![空間錨點移除](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> 請記住，空間錨點仍是 Beta 版，因此請務必回頭查看是否有更新的資訊和功能。

## <a name="see-also"></a>另請參閱
* [空間錨點](spatial-anchors.md)
* [座標系統](coordinate-systems.md)
