---
title: 空間音訊教學課程-3。 從影片 Spatializing 音訊
description: 將影片資產匯入到您的 Unity 專案，並從影片 spatialize 音訊。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教學課程，hololens2，空間音訊
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182745"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="44892-105">從影片 Spatializing 音訊</span><span class="sxs-lookup"><span data-stu-id="44892-105">Spatializing audio from a video</span></span>
<span data-ttu-id="44892-106">在 HoloLens 2 Unity 教學課程的空間音訊模組的第3章中，您將會：</span><span class="sxs-lookup"><span data-stu-id="44892-106">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="44892-107">匯入影片並新增影片播放</span><span class="sxs-lookup"><span data-stu-id="44892-107">Import a video and add a Video Player</span></span>
* <span data-ttu-id="44892-108">在 quadrangle 上播放影片</span><span class="sxs-lookup"><span data-stu-id="44892-108">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="44892-109">將音訊從影片路由傳送至 quadrangle，並 spatialize 音訊</span><span class="sxs-lookup"><span data-stu-id="44892-109">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="44892-110">匯入影片並新增影片播放</span><span class="sxs-lookup"><span data-stu-id="44892-110">Import a video and add a Video Player</span></span>

<span data-ttu-id="44892-111">將影片檔案拖曳至 Unity 專案的 [**專案**] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="44892-111">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="44892-112">您可以使用空間音訊範例專案中的[這段影片](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true)。</span><span class="sxs-lookup"><span data-stu-id="44892-112">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![具有影片的資產資料夾](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="44892-114">調整影片剪輯上的品質設定可確保在 HoloLens 2 上順暢播放。</span><span class="sxs-lookup"><span data-stu-id="44892-114">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="44892-115">按一下 [**專案**] 窗格中的影片檔案。</span><span class="sxs-lookup"><span data-stu-id="44892-115">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="44892-116">然後在影片檔案的 [偵測**器**] 窗格中，覆寫 Windows Store 應用程式的設定，以及：</span><span class="sxs-lookup"><span data-stu-id="44892-116">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="44892-117">啟用**轉碼**</span><span class="sxs-lookup"><span data-stu-id="44892-117">Enable **Transcode**</span></span>
* <span data-ttu-id="44892-118">將**編解碼器**設定為 H264</span><span class="sxs-lookup"><span data-stu-id="44892-118">Set **Codec** to H264</span></span>
* <span data-ttu-id="44892-119">將**位元速率模式**設定為低</span><span class="sxs-lookup"><span data-stu-id="44892-119">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="44892-120">將**空間品質**設定為中等空間品質</span><span class="sxs-lookup"><span data-stu-id="44892-120">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="44892-121">這些調整之後，影片檔案的 [偵測**器**] 窗格看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="44892-121">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![影片屬性窗格](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="44892-123">接下來，以滑鼠右鍵**按一下 [階層**] 窗格，然後選擇 [**影片-> 影片播放程式** **]，** 將**影片播放機**物件新增至階層：</span><span class="sxs-lookup"><span data-stu-id="44892-123">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![階層中的影片播放](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="44892-125">播放影片至 quadrangle</span><span class="sxs-lookup"><span data-stu-id="44892-125">Play video onto a quadrangle</span></span>
<span data-ttu-id="44892-126">**影片播放機**物件需要一個紋理的遊戲物件來呈現影片。</span><span class="sxs-lookup"><span data-stu-id="44892-126">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="44892-127">首先，以滑鼠右鍵按一下 [**階層] 窗格**，然後選擇 [ **3d 物件-> 四**：]，將 [**四**] 新增**至您的**階層。</span><span class="sxs-lookup"><span data-stu-id="44892-127">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![將四個新增至階層](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="44892-129">為確保當應用程式啟動時，**四**個會出現在使用者前方，請將**四**個的 [**位置**] 屬性設為（0，0，2），並將 [**小**數位數] 屬性設定為（1.28、0.72、1）。</span><span class="sxs-lookup"><span data-stu-id="44892-129">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="44892-130">這些變更之後，**四**個 [偵測**器**] 窗格上的 [**轉換**] 元件將會如下所示：</span><span class="sxs-lookup"><span data-stu-id="44892-130">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四轉換](images/spatial-audio/quad-transform.png)

<span data-ttu-id="44892-132">若要使用影片將**四**種材質紋理，請建立新的**呈現材質**。</span><span class="sxs-lookup"><span data-stu-id="44892-132">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="44892-133">在 [**專案**] 窗格中，以滑鼠右鍵按一下並選擇 [**建立-> 呈現材質**]：</span><span class="sxs-lookup"><span data-stu-id="44892-133">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![建立呈現材質](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="44892-135">在轉譯**材質**的 [偵測**器**] 窗格中，設定 [**大小**] 屬性，以符合影片的1280x720 原生解析度。</span><span class="sxs-lookup"><span data-stu-id="44892-135">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="44892-136">然後，若要確保在 HoloLens 2 上呈現良好的效能，請將**深度緩衝區**屬性設定為**至少16位深度**。</span><span class="sxs-lookup"><span data-stu-id="44892-136">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="44892-137">在這些設定之後，轉譯**材質**的 [偵測**器**] 窗格看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="44892-137">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![轉譯材質屬性](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="44892-139">接下來，使用新的轉譯**材質**做為**四**種的紋理：</span><span class="sxs-lookup"><span data-stu-id="44892-139">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="44892-140">將轉譯**材質**從 [**專案**] 窗格拖曳至階層**中的 [** **四**個]</span><span class="sxs-lookup"><span data-stu-id="44892-140">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="44892-141">若要確保 HoloLens 2 的效能良好，請在**四**個 [偵測**器**] 窗格中，選取 [**混合現實工具組標準著色器**]。</span><span class="sxs-lookup"><span data-stu-id="44892-141">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="44892-142">使用這些設定，**四**個 [偵測**器**] 窗格上的 [**材質**] 元件會如下所示：</span><span class="sxs-lookup"><span data-stu-id="44892-142">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四紋理屬性](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="44892-144">若要設定新的**影片播放**程式並**呈現材質**來播放您的影片剪輯，請開啟**影片播放**程式的 [偵測**器**] 窗格，並：</span><span class="sxs-lookup"><span data-stu-id="44892-144">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="44892-145">將**影片剪輯**屬性設定為您的影片檔案</span><span class="sxs-lookup"><span data-stu-id="44892-145">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="44892-146">勾選 [**迴圈**] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="44892-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="44892-147">將**目標材質**設定為新的呈現材質</span><span class="sxs-lookup"><span data-stu-id="44892-147">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="44892-148">**影片播放**程式的 [偵測**器**] 窗格現在看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="44892-148">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![影片播放者屬性](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="44892-150">Spatialize 影片中的音訊</span><span class="sxs-lookup"><span data-stu-id="44892-150">Spatialize the audio from the video</span></span>
<span data-ttu-id="44892-151">在**四**個的 [偵測**器**] 窗格中，建立**音訊來源**，以從影片路由傳送音訊：</span><span class="sxs-lookup"><span data-stu-id="44892-151">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="44892-152">按一下窗格底部的 [**新增元件**]</span><span class="sxs-lookup"><span data-stu-id="44892-152">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="44892-153">新增**音訊來源**</span><span class="sxs-lookup"><span data-stu-id="44892-153">Add an **Audio Source**</span></span>

<span data-ttu-id="44892-154">然後，在**音訊來源**上：</span><span class="sxs-lookup"><span data-stu-id="44892-154">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="44892-155">將**輸出**設定為混音器</span><span class="sxs-lookup"><span data-stu-id="44892-155">Set **Output** to your mixer</span></span>
* <span data-ttu-id="44892-156">勾選 [ **Spatialize** ] 方塊</span><span class="sxs-lookup"><span data-stu-id="44892-156">Check the **Spatialize** box</span></span>
* <span data-ttu-id="44892-157">將**空間 Blend**滑杆移至1（3d）</span><span class="sxs-lookup"><span data-stu-id="44892-157">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="44892-158">這些變更之後，**四**個 [偵測**器**] 窗格上的 [**音訊來源**] 元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="44892-158">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四音訊來源偵測器](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="44892-160">若要設定**影片播放**程式將其音訊傳送至**四**個**音訊來源**，請開啟**影片播放機**的 [偵測**器**] 窗格，然後：</span><span class="sxs-lookup"><span data-stu-id="44892-160">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="44892-161">將**音訊輸出模式**設定為「音訊來源」</span><span class="sxs-lookup"><span data-stu-id="44892-161">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="44892-162">將 [**音訊來源**] 屬性設定為您的四個</span><span class="sxs-lookup"><span data-stu-id="44892-162">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="44892-163">這些變更之後，**影片播放**程式的 [偵測**器**] 窗格看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="44892-163">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![影片播放組設定音訊來源](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="44892-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="44892-165">Next steps</span></span>
<span data-ttu-id="44892-166">在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="44892-166">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="44892-167">您會看到並聆聽影片，而影片中的音訊將會 hrtf。</span><span class="sxs-lookup"><span data-stu-id="44892-167">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

<span data-ttu-id="44892-168">繼續進行[第4章](unity-spatial-audio-ch4.md)，以在執行時間使用按鈕來啟用和停用 spatialization。</span><span class="sxs-lookup"><span data-stu-id="44892-168">Continue to [Chapter 4](unity-spatial-audio-ch4.md) to use the button to enable and disable spatialization at run time.</span></span>

