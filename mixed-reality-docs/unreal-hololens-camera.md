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
# <a name="hololens-camera-in-unreal"></a><span data-ttu-id="4df72-104">Unreal 中的 HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="4df72-104">HoloLens Camera in Unreal</span></span>

## <a name="third-camera-mixed-reality-capture"></a><span data-ttu-id="4df72-105">第三相機混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="4df72-105">Third Camera Mixed Reality Capture</span></span>

<span data-ttu-id="4df72-106">第三相機混合實境擷取 (MRC) 可以用來從 HoloLens 訪客的視角轉譯混合實境擷取，而不是從眼部紋理的視角。</span><span class="sxs-lookup"><span data-stu-id="4df72-106">Third camera Mixed Reality Capture (MRC) can be used to render a mixed reality capture from the perspective of the camera on the HoloLens visor, rather than the perspective of the eye textures.</span></span>  <span data-ttu-id="4df72-107">這樣可以改善實際世界與 MRC 影片中全像投影之間的對應。</span><span class="sxs-lookup"><span data-stu-id="4df72-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span> 

<span data-ttu-id="4df72-108">若要選擇使用第三相機 MRC，請使用想要的影片維度呼叫 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera。</span><span class="sxs-lookup"><span data-stu-id="4df72-108">To opt into using third camera MRC, call SetEnabledMixedRealityCamera and ResizeMixedRealityCamera with the desired video dimensions.</span></span> 

![第三相機](images/unreal-camera-3rd.PNG)

<span data-ttu-id="4df72-110">然後在 HoloLens 裝置入口網站中錄製 MRC 影片。</span><span class="sxs-lookup"><span data-stu-id="4df72-110">Then record an MRC video in the HoloLens device portal.</span></span> 

## <a name="pv-camera"></a><span data-ttu-id="4df72-111">PV 相機</span><span class="sxs-lookup"><span data-stu-id="4df72-111">PV Camera</span></span>

<span data-ttu-id="4df72-112">網路攝影機紋理也可以在遊戲的執行階段中擷取。</span><span class="sxs-lookup"><span data-stu-id="4df72-112">The webcam texture can also be retrieved in the game at runtime.</span></span>  <span data-ttu-id="4df72-113">若要在 HoloLens 上取得網路攝影機紋理，首先請確定已在 [專案設定] > [平台] > [HoloLens] > [功能] 下的 Unreal 編輯器中勾選「網路攝影機」功能。</span><span class="sxs-lookup"><span data-stu-id="4df72-113">To get the webcam texture on HoloLens, first ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> 

<span data-ttu-id="4df72-114">選擇透過 StartCameraCapture 函式在執行階段使用網路攝影機。</span><span class="sxs-lookup"><span data-stu-id="4df72-114">Opt into using the webcam at runtime with the StartCameraCapture function.</span></span>  <span data-ttu-id="4df72-115">使用 StopCameraCapture 函式停止擷取。</span><span class="sxs-lookup"><span data-stu-id="4df72-115">Stop capturing with the StopCameraCapture function.</span></span> 

![相機啟動停止](images/unreal-camera-startstop.PNG)

<span data-ttu-id="4df72-117">若要轉譯相機影像，請先根據專案中的材質建立動態材質執行個體。</span><span class="sxs-lookup"><span data-stu-id="4df72-117">To render the camera image, first create a dynamic material instance based on a material in the project.</span></span>  <span data-ttu-id="4df72-118">在此情況下，會以名為 PVCamMat 的材質為基礎。</span><span class="sxs-lookup"><span data-stu-id="4df72-118">In this case based on a material named PVCamMat.</span></span>  <span data-ttu-id="4df72-119">將這個項目設定為具有類型材質執行個體動態物件參考的變數。</span><span class="sxs-lookup"><span data-stu-id="4df72-119">Set this to a variable with type Material Instance Dynamic Object Reference.</span></span>  <span data-ttu-id="4df72-120">然後設定場景中物件的材質，該場景會將相機輸出轉譯至這個新的動態材質執行個體，並啟動用來將相機影像繫結至材質的計時器。</span><span class="sxs-lookup"><span data-stu-id="4df72-120">Then set the material of the object in the scene that will render the camera feed to this new dynamic material instance and start a timer that will be used to bind the camera image to the material.</span></span> 

![相機轉譯](images/unreal-camera-render.PNG)

<span data-ttu-id="4df72-122">建立此計時器的新函式 (在這個案例中為 MaterialTimer)，並且呼叫 GetARCameraImage 以從網路攝影機取得紋理。</span><span class="sxs-lookup"><span data-stu-id="4df72-122">Create a new function for this timer, in this case MaterialTimer, and call GetARCameraImage to get the texture from the webcam.</span></span>  <span data-ttu-id="4df72-123">如果此紋理有效，請將著色器中的紋理參數設定為此影像。</span><span class="sxs-lookup"><span data-stu-id="4df72-123">If this texture is valid, set a texture parameter in the shader to this image.</span></span>  <span data-ttu-id="4df72-124">否則，請重新啟動材質計時器。</span><span class="sxs-lookup"><span data-stu-id="4df72-124">Otherwise, start the material timer again.</span></span> 

![相機紋理](images/unreal-camera-texture.PNG)

<span data-ttu-id="4df72-126">材質應該具有符合 SetTextureParameterValue (繫結至色彩項目以適當地顯示相機影像) 中名稱的參數。</span><span class="sxs-lookup"><span data-stu-id="4df72-126">The material should have a parameter matching the name in SetTextureParameterValue bound to a color entry to properly display the camera image.</span></span> 

![相機紋理](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="4df72-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4df72-128">See also</span></span>
* [<span data-ttu-id="4df72-129">定位相機</span><span class="sxs-lookup"><span data-stu-id="4df72-129">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="4df72-130">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="4df72-130">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
