---
title: Unreal 中的 HoloLens 相機
description: 在 Unreal 中使用 HoloLens 攝影機的指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 相機, 第三相機, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840117"
---
# <a name="hololens-camera-in-unreal"></a>Unreal 中的 HoloLens 相機

## <a name="third-camera-mixed-reality-capture"></a>第三相機混合實境擷取

第三相機混合實境擷取 (MRC) 可以用來從 HoloLens 訪客的視角轉譯混合實境擷取，而不是從眼部紋理的視角。  這樣可以改善實際世界與 MRC 影片中全像投影之間的對應。 

若要選擇使用第三相機 MRC，請使用想要的影片維度呼叫 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera。 

![第三相機](images/unreal-camera-3rd.PNG)

然後在 HoloLens 裝置入口網站中錄製 MRC 影片。 

## <a name="pv-camera"></a>PV 相機

網路攝影機紋理也可以在遊戲的執行階段中擷取。  若要在 HoloLens 上取得網路攝影機紋理，首先請確定已在 [專案設定] > [平台] > [HoloLens] > [功能] 下的 Unreal 編輯器中勾選「網路攝影機」功能。 

選擇透過 StartCameraCapture 函式在執行階段使用網路攝影機。  使用 StopCameraCapture 函式停止擷取。 

![相機啟動停止](images/unreal-camera-startstop.PNG)

若要轉譯相機影像，請先根據專案中的材質建立動態材質執行個體。  在此情況下，會以名為 PVCamMat 的材質為基礎。  將這個項目設定為具有類型材質執行個體動態物件參考的變數。  然後設定場景中物件的材質，該場景會將相機輸出轉譯至這個新的動態材質執行個體，並啟動用來將相機影像繫結至材質的計時器。 

![相機轉譯](images/unreal-camera-render.PNG)

建立此計時器的新函式 (在這個案例中為 MaterialTimer)，並且呼叫 GetARCameraImage 以從網路攝影機取得紋理。  如果此紋理有效，請將著色器中的紋理參數設定為此影像。  否則，請重新啟動材質計時器。 

![相機紋理](images/unreal-camera-texture.PNG)

材質應該具有符合 SetTextureParameterValue (繫結至色彩項目以適當地顯示相機影像) 中名稱的參數。 

![相機紋理](images/unreal-camera-material.PNG)

## <a name="see-also"></a>另請參閱
* [定位相機](locatable-camera.md)
* [適用於開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)
