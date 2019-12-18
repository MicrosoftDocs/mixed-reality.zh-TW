---
title: 空間音訊教學課程-2。 Spatializing 按鈕互動音效
description: 將按鈕新增至您的專案，並 spatialize 按鈕互動音效。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教學課程，hololens2，空間音訊
ms.openlocfilehash: bd70e3bc88ee39b2c6257089ac3a2b93dfae0ad1
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182775"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="ab5c9-105">Spatializing 按鈕互動音效</span><span class="sxs-lookup"><span data-stu-id="ab5c9-105">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="ab5c9-106">目標</span><span class="sxs-lookup"><span data-stu-id="ab5c9-106">Objectives</span></span>
<span data-ttu-id="ab5c9-107">在 HoloLens 2 教學課程的空間音訊模組的第二個章節中，您將會：</span><span class="sxs-lookup"><span data-stu-id="ab5c9-107">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="ab5c9-108">新增按鈕</span><span class="sxs-lookup"><span data-stu-id="ab5c9-108">Add a button</span></span>
* <span data-ttu-id="ab5c9-109">Spatialize 按鈕按一下聲音</span><span class="sxs-lookup"><span data-stu-id="ab5c9-109">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="ab5c9-110">新增按鈕</span><span class="sxs-lookup"><span data-stu-id="ab5c9-110">Add a button</span></span>
<span data-ttu-id="ab5c9-111">在 [**專案**] 窗格中，選取 [**資產**]，然後在搜尋列中輸入 "PressableButtonHoloLens2"：</span><span class="sxs-lookup"><span data-stu-id="ab5c9-111">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![資產中的按鈕 prefab](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="ab5c9-113">按鈕 prefab 是以藍色圖示表示的專案，而不是白色圖示。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-113">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="ab5c9-114">將名為**PressableButtonHoloLens2**的 prefab 拖曳到 [**階層] 窗格**中。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-114">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="ab5c9-115">在新按鈕的 [偵測**器**] 窗格中，將 [**位置**] 屬性設為（0，-0.4，2），使其在應用程式啟動時顯示在使用者的前方。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-115">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="ab5c9-116">按鈕的 [**轉換**] 元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="ab5c9-116">The **Transform** component of the button will look like this:</span></span>

![按鈕轉換](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="ab5c9-118">Spatialize 按鈕意見反應</span><span class="sxs-lookup"><span data-stu-id="ab5c9-118">Spatialize button feedback</span></span>
<span data-ttu-id="ab5c9-119">在此步驟中，您將 spatialize 按鈕的音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-119">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="ab5c9-120">如需相關的設計建議，請參閱[空間音效設計](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-120">For related design suggestions, see [spatial sound design](spatial-sound-design.md).</span></span> 

<span data-ttu-id="ab5c9-121">[**音訊混音**器] 窗格可讓您定義目的地（稱為**混音器群組**），以從**音訊來源**元件播放音訊。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-121">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="ab5c9-122">使用**視窗 > 音訊 > 音訊混音**器，從功能表列開啟 [**音訊混音**器] 窗格</span><span class="sxs-lookup"><span data-stu-id="ab5c9-122">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="ab5c9-123">按一下 [ **Mixers**] 旁的 [+] 來建立**混音**器。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-123">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="ab5c9-124">新的混音器會包含名為**Master**的預設**群組**。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-124">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="ab5c9-125">您的 [**混音**器] 窗格現在看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="ab5c9-125">Your **Mixer** pane will now look like this:</span></span>

![具有第一個混音器的混音器面板](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="ab5c9-127">在[第5章](unity-spatial-audio-ch5.md)啟用了「回音」之前，混音器的音量計量並不會顯示透過 Microsoft 空間定位器播放之音效的活動</span><span class="sxs-lookup"><span data-stu-id="ab5c9-127">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="ab5c9-128">按一下 [**階層] 窗格中的** **PressableButtonHoloLens2** 。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-128">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="ab5c9-129">在 [偵測**器**] 窗格中：</span><span class="sxs-lookup"><span data-stu-id="ab5c9-129">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="ab5c9-130">尋找**音訊來源**元件</span><span class="sxs-lookup"><span data-stu-id="ab5c9-130">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="ab5c9-131">針對 [**輸出**] 屬性，按一下選取器並選擇您的混合器</span><span class="sxs-lookup"><span data-stu-id="ab5c9-131">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="ab5c9-132">核取 [ **Spatialize** ] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="ab5c9-132">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="ab5c9-133">將**空間 Blend**滑杆移至3d （1）。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="ab5c9-134">在2019之前的 Unity 版本中，[Spatialize] 核取方塊位於**音訊來源**的 [偵測**器**] 窗格底部。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-134">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="ab5c9-135">這些變更之後，您**PressableButtonHoloLens2**的**音訊來源**元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="ab5c9-135">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![按鈕音訊來源](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="ab5c9-137">如果您在未核取  **Spatialize**  核取方塊的情況下，將 **空間 Blend**  移至 1 （3D），Unity 將會使用其移動空間定位器，而不是  **Microsoft 空間定位器**</span><span class="sxs-lookup"><span data-stu-id="ab5c9-137">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="ab5c9-138">調整音量曲線</span><span class="sxs-lookup"><span data-stu-id="ab5c9-138">Adjust the Volume curve</span></span>
<span data-ttu-id="ab5c9-139">根據預設，Unity 會在從接聽程式變得更遠的同時，attenuate hrtf 的聲音。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-139">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="ab5c9-140">當此衰減套用到互動意見反應音效時，介面可能會變得更難以使用。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-140">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="ab5c9-141">若要停用此衰減，請調整**音量**曲線。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-141">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="ab5c9-142">在**PressableButtonHoloLens2**的 [偵測**器**] 窗格的 [**音訊來源**] 元件中，有一個稱為 [ **3d 音效設定**] 的區段。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-142">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="ab5c9-143">在該區段中：</span><span class="sxs-lookup"><span data-stu-id="ab5c9-143">In that section:</span></span>
1. <span data-ttu-id="ab5c9-144">將**磁片區 Rolloff**屬性設定為線性</span><span class="sxs-lookup"><span data-stu-id="ab5c9-144">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="ab5c9-145">將**音量**曲線上的端點（紅色曲線）從 y 軸上的 ' 0 ' 拖曳到 ' 1 '</span><span class="sxs-lookup"><span data-stu-id="ab5c9-145">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="ab5c9-146">若要將**音量**曲線的形狀調整為平面，請將白色曲線圖形控制項平行拖曳至 X 軸</span><span class="sxs-lookup"><span data-stu-id="ab5c9-146">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="ab5c9-147">這些變更之後， **PressableButtonHoloLens2**之 [**音訊來源**] 屬性的 [ **3d 音效設定**] 區段會如下所示：</span><span class="sxs-lookup"><span data-stu-id="ab5c9-147">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![按鈕3D 音效設定](images/spatial-audio/button-3d-sound-settings.png)

## <a name="next-steps"></a><span data-ttu-id="ab5c9-149">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ab5c9-149">Next steps</span></span>

<span data-ttu-id="ab5c9-150">在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-150">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="ab5c9-151">在應用程式中，您可以碰觸按鈕並聽到 [hrtf] 按鈕互動音效。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-151">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="ab5c9-152">在 Unity 編輯器中測試時，請按空格鍵並使用滾輪進行滾動，以啟用 [手動模擬]。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-152">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="ab5c9-153">如需詳細資訊，請參閱[MRTK 檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-153">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

<span data-ttu-id="ab5c9-154">繼續進行[第3章](unity-spatial-audio-ch3.md)，將影片新增至您的應用程式，並從影片 spatialize 音訊。</span><span class="sxs-lookup"><span data-stu-id="ab5c9-154">Continue to [Chapter 3](unity-spatial-audio-ch3.md) to add a video to your app, and spatialize the audio from the video.</span></span>

