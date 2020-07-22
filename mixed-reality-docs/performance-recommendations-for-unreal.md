---
title: Unreal 的效能建議
description: 在 Unreal 中使用混合實境應用程式的最佳效能建議
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 效能, 最佳化, 設定, 文件
ms.openlocfilehash: a7972962eeb2b1480a7da38210b5ee77104f508b
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303631"
---
# <a name="performance-recommendations-for-unreal"></a>Unreal 的效能建議

## <a name="overview"></a>概觀

本文是以[混合實境效能建議](understanding-performance-for-mixed-reality.md)中所述的討論為基礎，但著重於 Unreal Engine 特有的功能。 建議您先閱讀應用程式瓶頸、分析和剖析混合實境應用程式，並進行一般效能修正，再繼續進行。

## <a name="recommended-unreal-project-settings"></a>建議的 Unreal 專案設定
您可以在 [編輯] > [專案設定] 中找到下列每個設定。

1. 使用行動 VR 轉譯器：
    * 向下捲動至 [專案] 區段、選取 [目標硬體]，然後將目標平台設定為 [行動裝置/平板電腦]

![行動目標設定](images/unreal/performance-recommendations-img-01.png)

2. 停用遮蔽消除：
    * 向下捲動至 [引擎] 區段、選取 [轉譯]、展開 [消除] 區段，然後取消勾選 [遮蔽消除]。
        + 如果您需要針對轉譯的詳細場景進行遮蔽消除，建議您在 [引擎] > [轉譯] 中啟用 [支援軟體遮蔽消除]。 這讓 Unreal 可在 CPU 上執行此工作，並避免 GPU 的遮蔽查詢 (此功能在 HoloLens 2 上的執行效能不佳)。

![停用遮蔽消除](images/unreal/performance-recommendations-img-02.png)

3. 使用行動多重檢視：
    * 向下捲動至 [引擎] 區段、選取 [轉譯]、展開 [VR] 區段，然後同時啟用 [執行個體化立體聲] 和 [行動多重檢視]。 應取消核取行動設備 HDR。

![VR 轉譯設定](images/unreal/performance-recommendations-img-03.png)

4. 將 [要轉譯的 CSM 串聯數目上限] 設定為 **1**，並將 [可移動的聚光燈/點狀光源數上限] 設定為 **0**。 
