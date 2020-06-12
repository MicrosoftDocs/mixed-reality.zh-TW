---
title: Unreal 中的 HoloLens 相片/影片相機
description: 在 Unreal 中使用 HoloLens 相片/影片相機的指南
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 相機, PV 相機, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451333"
---
# <a name="hololens-photovideo-camera-in-unreal"></a>Unreal 中的 HoloLens 相片/影片相機

HoloLens 具有相片/影片 (PV) 相機，用於混合實境擷取 (MRC)，並可供應用程式用來存取真實世界的視覺效果。

## <a name="render-from-the-pv-camera-for-mrc"></a>從適用於 MRC 的 PV 相機呈現

> [!NOTE]
> 這需要 **Unreal Engine 4.25** 或更新版本。

系統和自訂 MRC 錄製器，藉由結合 PV 相機與沉浸式應用程式所呈現的全像投影，建立混合實境。

根據預設，混合實境擷取會使用右眼的全像投影輸出。 如果沉浸式應用程式選擇[從 PV 相機呈現](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，則會改用此功能。 這樣可以改善實際世界與 MRC 影片中全像投影之間的對應。

若要選擇從 PV 相機呈現：

1. 呼叫 **SetEnabledMixedRealityCamera** 和 **ResizeMixedRealityCamera**
    * 使用 **Size X** 和 **Size Y** 值來設定影片大小。

![第三相機](images/unreal-camera-3rd.PNG)

然後，Unreal 會處理來自 MRC 的要求，以從 PV 相機的視角呈現。

> [!NOTE]
> 只有在觸發了[混合實境擷取](mixed-reality-capture.md)時，才會要求應用程式從相片/影片相機的視角呈現。

## <a name="using-the-pv-camera"></a>使用 PV 相機

網路攝影機紋理可以在執行階段於遊戲中擷取，但必須在編輯器的 [編輯] > [專案設定] 中啟用：
1. 移至 [平台] > [HoloLens] > [功能]，並勾選 [網路攝影機]。
    * 使用 **StartCameraCapture** 函式，以在執行階段使用網路攝影機，以及使用 **StopCameraCapture** 函式以停止錄製。

![相機啟動停止](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>呈現影像
若要呈現相機影像：
1. 根據專案中的材質建立動態材質執行個體，在下列螢幕擷取畫面中將其稱為 **PVCamMat**。  
2. 將動態材質執行個體設定為**材質執行個體動態物件參考**變數。  
3. 將場景中呈現相機摘要的物件材質設定為這個新的動態材質執行個體。
    * 啟動用來將相機影像繫結至材質的計時器。 

![相機轉譯](images/unreal-camera-render.PNG)

4. 建立此計時器的新函式 (在這個案例中為 **MaterialTimer**)，並且呼叫 **GetARCameraImage** 以從網路攝影機取得紋理。  
5. 如果紋理有效，請將著色器中的紋理參數設定為影像。  否則，請重新啟動材質計時器。 

![相機紋理](images/unreal-camera-texture.PNG)

5. 確定材質有一個參數符合 **SetTextureParameterValue** 中繫結至色彩項目的名稱。 若非如此，就無法適當地顯示相機影像。

![相機紋理](images/unreal-camera-material.PNG)

## <a name="see-also"></a>另請參閱
* [定位相機](locatable-camera.md)
* [適用於開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)
