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
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="96869-104">Unreal 中的 HoloLens 相片/影片相機</span><span class="sxs-lookup"><span data-stu-id="96869-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="96869-105">HoloLens 具有相片/影片 (PV) 相機，用於混合實境擷取 (MRC)，並可供應用程式用來存取真實世界的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="96869-105">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="96869-106">從適用於 MRC 的 PV 相機呈現</span><span class="sxs-lookup"><span data-stu-id="96869-106">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="96869-107">這需要 **Unreal Engine 4.25** 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="96869-107">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="96869-108">系統和自訂 MRC 錄製器，藉由結合 PV 相機與沉浸式應用程式所呈現的全像投影，建立混合實境。</span><span class="sxs-lookup"><span data-stu-id="96869-108">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="96869-109">根據預設，混合實境擷取會使用右眼的全像投影輸出。</span><span class="sxs-lookup"><span data-stu-id="96869-109">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="96869-110">如果沉浸式應用程式選擇[從 PV 相機呈現](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，則會改用此功能。</span><span class="sxs-lookup"><span data-stu-id="96869-110">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="96869-111">這樣可以改善實際世界與 MRC 影片中全像投影之間的對應。</span><span class="sxs-lookup"><span data-stu-id="96869-111">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="96869-112">若要選擇從 PV 相機呈現：</span><span class="sxs-lookup"><span data-stu-id="96869-112">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="96869-113">呼叫 **SetEnabledMixedRealityCamera** 和 **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="96869-113">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="96869-114">使用 **Size X** 和 **Size Y** 值來設定影片大小。</span><span class="sxs-lookup"><span data-stu-id="96869-114">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第三相機](images/unreal-camera-3rd.PNG)

<span data-ttu-id="96869-116">然後，Unreal 會處理來自 MRC 的要求，以從 PV 相機的視角呈現。</span><span class="sxs-lookup"><span data-stu-id="96869-116">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="96869-117">只有在觸發了[混合實境擷取](mixed-reality-capture.md)時，才會要求應用程式從相片/影片相機的視角呈現。</span><span class="sxs-lookup"><span data-stu-id="96869-117">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="96869-118">使用 PV 相機</span><span class="sxs-lookup"><span data-stu-id="96869-118">Using the PV Camera</span></span>

<span data-ttu-id="96869-119">網路攝影機紋理可以在執行階段於遊戲中擷取，但必須在編輯器的 [編輯] > [專案設定] 中啟用：</span><span class="sxs-lookup"><span data-stu-id="96869-119">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="96869-120">移至 [平台] > [HoloLens] > [功能]，並勾選 [網路攝影機]。</span><span class="sxs-lookup"><span data-stu-id="96869-120">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="96869-121">使用 **StartCameraCapture** 函式，以在執行階段使用網路攝影機，以及使用 **StopCameraCapture** 函式以停止錄製。</span><span class="sxs-lookup"><span data-stu-id="96869-121">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![相機啟動停止](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="96869-123">呈現影像</span><span class="sxs-lookup"><span data-stu-id="96869-123">Rendering an image</span></span>
<span data-ttu-id="96869-124">若要呈現相機影像：</span><span class="sxs-lookup"><span data-stu-id="96869-124">To render the camera image:</span></span>
1. <span data-ttu-id="96869-125">根據專案中的材質建立動態材質執行個體，在下列螢幕擷取畫面中將其稱為 **PVCamMat**。</span><span class="sxs-lookup"><span data-stu-id="96869-125">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="96869-126">將動態材質執行個體設定為**材質執行個體動態物件參考**變數。</span><span class="sxs-lookup"><span data-stu-id="96869-126">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="96869-127">將場景中呈現相機摘要的物件材質設定為這個新的動態材質執行個體。</span><span class="sxs-lookup"><span data-stu-id="96869-127">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="96869-128">啟動用來將相機影像繫結至材質的計時器。</span><span class="sxs-lookup"><span data-stu-id="96869-128">Start a timer that will be used to bind the camera image to the material.</span></span> 

![相機轉譯](images/unreal-camera-render.PNG)

4. <span data-ttu-id="96869-130">建立此計時器的新函式 (在這個案例中為 **MaterialTimer**)，並且呼叫 **GetARCameraImage** 以從網路攝影機取得紋理。</span><span class="sxs-lookup"><span data-stu-id="96869-130">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="96869-131">如果紋理有效，請將著色器中的紋理參數設定為影像。</span><span class="sxs-lookup"><span data-stu-id="96869-131">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="96869-132">否則，請重新啟動材質計時器。</span><span class="sxs-lookup"><span data-stu-id="96869-132">Otherwise, start the material timer again.</span></span> 

![相機紋理](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="96869-134">確定材質有一個參數符合 **SetTextureParameterValue** 中繫結至色彩項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="96869-134">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="96869-135">若非如此，就無法適當地顯示相機影像。</span><span class="sxs-lookup"><span data-stu-id="96869-135">Without this, the camera image can't be properly displayed.</span></span>

![相機紋理](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="96869-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96869-137">See also</span></span>
* [<span data-ttu-id="96869-138">定位相機</span><span class="sxs-lookup"><span data-stu-id="96869-138">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="96869-139">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="96869-139">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
