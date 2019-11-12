---
title: 快速入門教學課程-6。 探索先進的輸入選項
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 5599fe48f62a35d1dc02ce30fb7858fd74e87685
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926539"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="46abe-105">6. 探索 advanced 輸入選項</span><span class="sxs-lookup"><span data-stu-id="46abe-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="46abe-106">在本教學課程中，會探索 HoloLens 2 的數個先進的輸入選項，包括使用語音命令、移動流覽手勢和眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="46abe-106">In this tutorial, several advanced input options for HoloLens 2 are explored, including the use of voice commands, panning gesture, and eye tracking.</span></span> 

## <a name="objectives"></a><span data-ttu-id="46abe-107">目標</span><span class="sxs-lookup"><span data-stu-id="46abe-107">Objectives</span></span>

- <span data-ttu-id="46abe-108">使用語音命令和關鍵字觸發事件</span><span class="sxs-lookup"><span data-stu-id="46abe-108">Trigger events using voice commands and keywords</span></span>
- <span data-ttu-id="46abe-109">使用追蹤的手平移材質和3D 物件</span><span class="sxs-lookup"><span data-stu-id="46abe-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
- <span data-ttu-id="46abe-110">利用 HoloLens 2 眼追蹤功能來選取物件</span><span class="sxs-lookup"><span data-stu-id="46abe-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="instructions"></a><span data-ttu-id="46abe-111">指示</span><span class="sxs-lookup"><span data-stu-id="46abe-111">Instructions</span></span>

### <a name="enabling-voice-commands"></a><span data-ttu-id="46abe-112">啟用語音命令</span><span class="sxs-lookup"><span data-stu-id="46abe-112">Enabling Voice Commands</span></span>

<span data-ttu-id="46abe-113">在本節中，會執行兩個語音命令。</span><span class="sxs-lookup"><span data-stu-id="46abe-113">In this section, two voice commands are implemented.</span></span> <span data-ttu-id="46abe-114">首先，您可以藉由說「切換診斷」來引進切換畫面播放速率診斷面板的功能。</span><span class="sxs-lookup"><span data-stu-id="46abe-114">First, the ability to toggle the frame rate diagnostics panel is introduced by saying "toggle diagnostics".</span></span> <span data-ttu-id="46abe-115">第二，會探索使用語音命令來播放音效的功能。</span><span class="sxs-lookup"><span data-stu-id="46abe-115">Second, the ability to play a sound with a voice command is explored.</span></span> <span data-ttu-id="46abe-116">負責設定語音命令的 MRTK 設定檔和設定會先進行審核。</span><span class="sxs-lookup"><span data-stu-id="46abe-116">The MRTK profiles and settings responsible for configuring voice commands is reviewed first.</span></span>

1. <span data-ttu-id="46abe-117">在 BaseScene 階層中，選取 [MixedRealityToolkit]。</span><span class="sxs-lookup"><span data-stu-id="46abe-117">In the BaseScene hierarchy, select MixedRealityToolkit.</span></span> <span data-ttu-id="46abe-118">然後，在 [偵測器] 面板中選取 [輸入]，然後按一下 DefaultMixedRealityInputSystemProfile 左邊的小型 [複製] 按鈕，以開啟 [複製設定檔] 快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="46abe-118">Then, in the Inspector panel, select Input and click the small Clone button to the left of the DefaultMixedRealityInputSystemProfile to open the Clone Profile popup.</span></span> <span data-ttu-id="46abe-119">在快顯視窗中按一下 [複製]，以建立新的設定檔 MixedRealityInputSystemProfile。</span><span class="sxs-lookup"><span data-stu-id="46abe-119">In the popup click Clone to create a new profile MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1a .png](images/mrlearning-base-ch5-1-step1a.png)

    <span data-ttu-id="46abe-121">這也會使用新建立的 MixedRealityInputSystemProfile 自動填入 MixedRealityToolkitConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="46abe-121">This will also auto-populate the MixedRealityToolkitConfigurationProfile with the newly created MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1b .png](images/mrlearning-base-ch5-1-step1b.png)

2. <span data-ttu-id="46abe-123">在輸入系統設定檔中，有各種不同的設定。</span><span class="sxs-lookup"><span data-stu-id="46abe-123">In the input system profile, there are a variety of settings.</span></span> <span data-ttu-id="46abe-124">針對語音命令，請展開 [語音] 區段，並遵循與上一個步驟相同的程式來複製 DefaultMixedRealitySpeechCommandsProfile，並將它取代為您自己的可編輯複本。</span><span class="sxs-lookup"><span data-stu-id="46abe-124">For voice commands, expand the Speech section and follow the same process as in the previous step to clone the DefaultMixedRealitySpeechCommandsProfile and replace it with your own editable copy.</span></span>

    ![mrlearning-base-ch5-1-step2 .png](images/mrlearning-base-ch5-1-step2.png)

    <span data-ttu-id="46abe-126">在語音命令設定檔中，您會注意到一系列的設定。</span><span class="sxs-lookup"><span data-stu-id="46abe-126">In the speech command profile, you’ll notice a range of settings.</span></span> <span data-ttu-id="46abe-127">如需這些設定的完整說明，請參閱[MRTK 語音檔](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。</span><span class="sxs-lookup"><span data-stu-id="46abe-127">For a full description of these settings, refer to the [MRTK speech documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>).</span></span>

    <span data-ttu-id="46abe-128">根據預設，一般行為是自動啟動。</span><span class="sxs-lookup"><span data-stu-id="46abe-128">By default, the general behavior is auto-start.</span></span> <span data-ttu-id="46abe-129">如有需要，您可以將此變更為手動啟動。</span><span class="sxs-lookup"><span data-stu-id="46abe-129">This can be changed to manual-start, if desired.</span></span> <span data-ttu-id="46abe-130">但在此範例中，請將它保持在自動啟動。</span><span class="sxs-lookup"><span data-stu-id="46abe-130">But for this example, keep it on auto-start.</span></span> <span data-ttu-id="46abe-131">MRTK 隨附數個預設語音命令，例如功能表、切換診斷和切換 profiler。</span><span class="sxs-lookup"><span data-stu-id="46abe-131">The MRTK comes with several default voice commands, such as menu, toggle diagnostics and toggle profiler.</span></span> <span data-ttu-id="46abe-132">我們將使用關鍵字「切換診斷」，以開啟和關閉診斷的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="46abe-132">We will use the keyword “toggle diagnostics,” in order to turn on and off the diagnostics framerate counter.</span></span> <span data-ttu-id="46abe-133">我們還將在下列步驟中加入新的語音命令。</span><span class="sxs-lookup"><span data-stu-id="46abe-133">We will also add a new voice command in the steps below.</span></span>

3. <span data-ttu-id="46abe-134">加入新的語音命令。</span><span class="sxs-lookup"><span data-stu-id="46abe-134">Add a new voice command.</span></span> <span data-ttu-id="46abe-135">若要這樣做，請按一下 [+ 新增語音命令] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="46abe-135">To do this, click the + Add a New Speech Command button.</span></span> <span data-ttu-id="46abe-136">您會看到出現在現有語音命令清單下方的新行。</span><span class="sxs-lookup"><span data-stu-id="46abe-136">You'll see a new line that appears below the list of existing voice commands.</span></span> <span data-ttu-id="46abe-137">輸入您想要使用的語音命令。</span><span class="sxs-lookup"><span data-stu-id="46abe-137">Type the voice command you want to use.</span></span> <span data-ttu-id="46abe-138">在此範例中，使用「播放音樂」命令。</span><span class="sxs-lookup"><span data-stu-id="46abe-138">In this example, use the command “play music".</span></span>

    ![mrlearning-base-ch5-1-step3 .png](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    ><span data-ttu-id="46abe-140">您也可以為語音命令設定按鍵代碼。</span><span class="sxs-lookup"><span data-stu-id="46abe-140">You can also set a keycode for speech commands.</span></span> <span data-ttu-id="46abe-141">這可讓語音命令在按下鍵盤按鍵時觸發事件。</span><span class="sxs-lookup"><span data-stu-id="46abe-141">This allows for voice commands to trigger events upon the press of a keyboard key.</span></span>

4. <span data-ttu-id="46abe-142">新增回應語音命令的功能。</span><span class="sxs-lookup"><span data-stu-id="46abe-142">Add the ability to respond to voice commands.</span></span> <span data-ttu-id="46abe-143">在 BaseScene 階層中選取任何未附加任何其他輸入腳本的物件，例如 MixedRealityPlayspace 遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="46abe-143">Select any object in the BaseScene hierarchy that does not have any other input scripts attached to it, for example, the MixedRealityPlayspace game object.</span></span> <span data-ttu-id="46abe-144">在 [偵測器] 面板中，按一下 [新增元件]，搜尋 "speech"，然後選取語音輸入處理常式腳本。</span><span class="sxs-lookup"><span data-stu-id="46abe-144">In the Inspector panel, click Add Component, search for "speech", and select the Speech Input Handler script.</span></span>

    ![mrlearning-base-ch5-1-step4 .png](images/mrlearning-base-ch5-1-step4.png)

    <span data-ttu-id="46abe-146">根據預設，您會看到兩個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="46abe-146">By default, you will see two checkboxes.</span></span> <span data-ttu-id="46abe-147">其中一個是 [需要焦點] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="46abe-147">One is the Is Focus Required checkbox.</span></span> <span data-ttu-id="46abe-148">因此，只要您是以光線眼、列印頭、控制器眼或手注視的方式來指向物件，就會觸發語音命令。</span><span class="sxs-lookup"><span data-stu-id="46abe-148">So, as long as you are pointing at the object with a ray-eye-gaze, head-gaze, controller-gaze, or hand-gaze, the voice command will be triggered.</span></span> <span data-ttu-id="46abe-149">取消核取此核取方塊，讓使用者不需要查看物件即可使用語音命令。</span><span class="sxs-lookup"><span data-stu-id="46abe-149">Uncheck this checkbox so that the user does not have to look at the object to use the voice command.</span></span>

5. <span data-ttu-id="46abe-150">新增回應語音命令的功能。</span><span class="sxs-lookup"><span data-stu-id="46abe-150">Add the ability to respond to a voice command.</span></span> <span data-ttu-id="46abe-151">若要這麼做，請按一下語音輸入處理常式中的 [+] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="46abe-151">To do this, click the + button that’s in the Speech Input Handler.</span></span>

    ![mrlearning-base-ch5-1-step5 .png](images/mrlearning-base-ch5-1-step5.png)

6. <span data-ttu-id="46abe-153">在 [關鍵字] 旁，您會看到一個下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="46abe-153">Next to Keyword, you'll see a dropdown menu.</span></span> <span data-ttu-id="46abe-154">選取 [切換診斷]，如此一來，每當使用者說出「切換診斷」片語時，它就會觸發動作。</span><span class="sxs-lookup"><span data-stu-id="46abe-154">Select Toggle Diagnostics so that whenever the user says the phrase “toggle diagnostics”, it triggers an action.</span></span> <span data-ttu-id="46abe-155">請注意，您可能需要按下旁邊的箭號來展開元素0。</span><span class="sxs-lookup"><span data-stu-id="46abe-155">Note that you might need to expand Element 0 by pressing the arrow next to it.</span></span>

    ![mrlearning-base-ch5-1-step6 .png](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    ><span data-ttu-id="46abe-157">系統會根據您在步驟3中編輯的設定檔，填入這些關鍵字。</span><span class="sxs-lookup"><span data-stu-id="46abe-157">These keywords are populated, based on the profile you edited in the step 3.</span></span>

7. <span data-ttu-id="46abe-158">新增診斷系統 Voice 控制項腳本，以切換開啟和關閉的畫面播放速率計數器診斷。</span><span class="sxs-lookup"><span data-stu-id="46abe-158">Add the Diagnostics System Voice Controls script to toggle the framerate counter diagnostic on and off.</span></span> <span data-ttu-id="46abe-159">若要這麼做，請按 [新增元件]，搜尋 [診斷] [系統] [語音控制腳本]，然後從功能表中加以新增。</span><span class="sxs-lookup"><span data-stu-id="46abe-159">To do this, press Add Component, search for Diagnostics System Voice Controls script and add it from the menu.</span></span> <span data-ttu-id="46abe-160">此指令碼可以新增至任何物件，但為了簡單起見，我們將其新增至與語音輸入處理常式相同的物件中。</span><span class="sxs-lookup"><span data-stu-id="46abe-160">This script can be added to any object, but for simplicity, we will add it to the same object as the speech input handler.</span></span>

    ![mrlearning-base-ch5-1-step7 .png](images/mrlearning-base-ch5-1-step7.png)

8. <span data-ttu-id="46abe-162">在語音輸入處理常式中加入新的回應。</span><span class="sxs-lookup"><span data-stu-id="46abe-162">Add a new response in the speech input handler.</span></span> <span data-ttu-id="46abe-163">若要這麼做，請按一下 [+] 圖示，將新的回應新增至回應清單。</span><span class="sxs-lookup"><span data-stu-id="46abe-163">To do this, click the "+" icon to add a new response to the response list.</span></span>

    ![mrlearning-base-ch5-1-step8 .png](images/mrlearning-base-ch5-1-step8.png)

9. <span data-ttu-id="46abe-165">將具有「診斷系統聲音控制」腳本的物件拖曳至您剛才在上一個步驟中建立的新回應。</span><span class="sxs-lookup"><span data-stu-id="46abe-165">Drag the object that has the Diagnostics System Voice Controls script to the new response you just created in the previous step.</span></span>

    ![mrlearning-base-ch5-1-step9 .png](images/mrlearning-base-ch5-1-step9.png)

10. <span data-ttu-id="46abe-167">按一下 [函式] 下拉式清單（此處未顯示函式）、[診斷系統聲音控制]，然後選取將診斷切換為開啟和關閉的 ToggleDiagnostics （）函數。</span><span class="sxs-lookup"><span data-stu-id="46abe-167">Click the function dropdown (where it says No Function), then Diagnostics System Voice Controls, and select the ToggleDiagnostics () function which toggles your diagnostics on and off.</span></span>

    ![mrlearning-base-ch5-1-step10 .png](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > <span data-ttu-id="46abe-169">在建立您的裝置之前，您必須啟用 mic 設定。</span><span class="sxs-lookup"><span data-stu-id="46abe-169">Before building to your device, you need to enable mic settings.</span></span> <span data-ttu-id="46abe-170">若要這樣做，請按一下 [檔案] 並移至 [組建設定]、[播放程式設定]，並確定已設定麥克風功能。</span><span class="sxs-lookup"><span data-stu-id="46abe-170">To do this, click File and go to Build Settings, Player Settings and ensure that the microphone capability is set.</span></span>

    <span data-ttu-id="46abe-171">接下來，使用顆 octa 物件新增播放音訊檔案的功能。</span><span class="sxs-lookup"><span data-stu-id="46abe-171">Next, add the ability to play an audio file from voice command using the Octa object.</span></span> <span data-ttu-id="46abe-172">回想一下[第4課](mrlearning-base-ch4.md)，已新增播放音訊剪輯以觸及顆 octa 物件的能力。</span><span class="sxs-lookup"><span data-stu-id="46abe-172">Recall from [lesson 4](mrlearning-base-ch4.md) that the ability to play an audio clip from touching the Octa object was added.</span></span> <span data-ttu-id="46abe-173">我們將針對我們的音樂語音命令使用相同的音訊來源。</span><span class="sxs-lookup"><span data-stu-id="46abe-173">We will leverage this same audio source for our music voice command.</span></span>

11. <span data-ttu-id="46abe-174">選取 [BaseScene] 階層中的 [顆 octa] 物件。</span><span class="sxs-lookup"><span data-stu-id="46abe-174">Select the Octa object in the BaseScene hierarchy.</span></span>

12. <span data-ttu-id="46abe-175">新增另一個語音輸入處理常式（重複步驟4和5），但使用顆 octa 物件。</span><span class="sxs-lookup"><span data-stu-id="46abe-175">Add another speech input handler (repeat Steps 4 and 5), but with the octa object.</span></span>

13. <span data-ttu-id="46abe-176">請新增 [播放音樂語音] 命令，而不是從步驟6新增 [切換診斷語音] 命令，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="46abe-176">Instead of adding the Toggle Diagnostics voice command from step 6, add the Play Music voice command as shown in the image below.</span></span>

    ![mrlearning-base-ch5-1-step13 .png](images/mrlearning-base-ch5-1-step13.png)

14. <span data-ttu-id="46abe-178">如同步驟8和9，加入新的回應，並將顆 octa 物件（包含診斷系統 Voice 控制項腳本的物件）拖曳至空白回應位置。</span><span class="sxs-lookup"><span data-stu-id="46abe-178">As with Steps 8 and 9, add a new response and drag the Octa object, the object that has the Diagnostics System Voice Controls script on it, to the empty response slot.</span></span>

15. <span data-ttu-id="46abe-179">選取顯示 [沒有函數] 的下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="46abe-179">Select the dropdown menu that says No Function.</span></span> <span data-ttu-id="46abe-180">然後選取 [音訊來源]，後面接著 [PlayOneShot （AudioClip）]。</span><span class="sxs-lookup"><span data-stu-id="46abe-180">Then select Audio Source, followed by PlayOneShot (AudioClip).</span></span>

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. <span data-ttu-id="46abe-182">在此範例中，我們將使用[第4課](mrlearning-base-ch4.md)的相同音訊剪輯。</span><span class="sxs-lookup"><span data-stu-id="46abe-182">For this example, we are going to use the same audio clip from [Lesson 4](mrlearning-base-ch4.md).</span></span> <span data-ttu-id="46abe-183">移至您的 [專案] 面板，搜尋 "MRTK_Gem" 音訊剪輯，並將它拖曳到音訊來源位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="46abe-183">Go into your Project panel, search for “MRTK_Gem” audio clip and drag it into the audio source slot as shown in the image below.</span></span> <span data-ttu-id="46abe-184">現在，您的應用程式會回應語音命令「切換診斷」，以切換 [畫面播放速率計數器] 面板並播放音樂來播放 MRTK_Gem 的歌曲。</span><span class="sxs-lookup"><span data-stu-id="46abe-184">Now your application will respond to the voice commands “toggle diagnostics” to toggle the Frame Rate Counter panel and Play Music to play the MRTK_Gem song.</span></span>

    ![Lesson5 Chapter1.txt Step16im](images/Lesson5_chapter1_step16im.PNG)

### <a name="the-pan-gesture"></a><span data-ttu-id="46abe-186">平移手勢</span><span class="sxs-lookup"><span data-stu-id="46abe-186">The Pan Gesture</span></span>

<span data-ttu-id="46abe-187">在本節中，您將瞭解如何使用平移手勢。</span><span class="sxs-lookup"><span data-stu-id="46abe-187">In this section, you will learn how to use the pan gesture.</span></span> <span data-ttu-id="46abe-188">這適用于使用手指或手來滾動內容的捲軸。</span><span class="sxs-lookup"><span data-stu-id="46abe-188">This is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="46abe-189">您也可以使用平移手勢來旋轉物件、迴圈流覽3D 物件的集合，甚至是滾動 2D UI。</span><span class="sxs-lookup"><span data-stu-id="46abe-189">You can also use the pan gesture to rotate objects, cycle through a collection of 3D objects, or even to scroll a 2D UI.</span></span> <!--TMP You will also learn how to use the pan gesture to warp a texture, and how to move a collection of 3D objects.-->

1. <span data-ttu-id="46abe-190">建立四邊形。</span><span class="sxs-lookup"><span data-stu-id="46abe-190">Create a quad.</span></span> <span data-ttu-id="46abe-191">在 BaseScene 階層中，以滑鼠右鍵按一下 [3D 物件]，然後選取 [四]。</span><span class="sxs-lookup"><span data-stu-id="46abe-191">In your BaseScene hierarchy, right-click, select "3D Object" followed by Quad.</span></span>

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. <span data-ttu-id="46abe-193">適當地重新置放四個。</span><span class="sxs-lookup"><span data-stu-id="46abe-193">Reposition the quad, as appropriate.</span></span> <span data-ttu-id="46abe-194">在我們的範例中，我們將 x = 0、y = 0 和 z = 1.5 遠離相機，以取得 HoloLens 2 的舒適位置。</span><span class="sxs-lookup"><span data-stu-id="46abe-194">For our example, we set the x = 0, the y = 0 and the z = 1.5 away from the camera for a comfortable position from HoloLens 2.</span></span>

    >[!NOTE]
    ><span data-ttu-id="46abe-195">如果四個區塊或位於先前課程中的任何內容前方，請務必將其移動，使其不會封鎖任何其他物件。</span><span class="sxs-lookup"><span data-stu-id="46abe-195">If the quad blocks or is in front of any content from the previous lessons, be sure to move it so that it doesn’t block any of the other objects.</span></span>

3. <span data-ttu-id="46abe-196">將材質套用至四邊形。</span><span class="sxs-lookup"><span data-stu-id="46abe-196">Apply a material to the quad.</span></span> <span data-ttu-id="46abe-197">這份材料將是我們將透過移動流覽手勢來進行的動作。</span><span class="sxs-lookup"><span data-stu-id="46abe-197">This material will be what we will be scrolling through with the pan gesture.</span></span>

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. <span data-ttu-id="46abe-199">在 [專案] 面板的 [搜尋] 方塊中，輸入「pan 內容」。</span><span class="sxs-lookup"><span data-stu-id="46abe-199">In your Projects panel, type “pan content” in the Search box.</span></span> <span data-ttu-id="46abe-200">將該材料拖曳到場景中的四個。</span><span class="sxs-lookup"><span data-stu-id="46abe-200">Drag that material onto the quad in your scene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="46abe-201">MRTK 中不包含 Pan 內容材料，而是在先前課程中匯入此模組的資產套件中的資產。</span><span class="sxs-lookup"><span data-stu-id="46abe-201">The Pan Content material is not included in the MRTK, but an asset in this module's asset package as imported in previous lessons.</span></span>

    >[!NOTE]
    ><span data-ttu-id="46abe-202">當您新增平移內容時，看起來可能會很延伸。</span><span class="sxs-lookup"><span data-stu-id="46abe-202">When you add the pan content, it may look stretched.</span></span> <span data-ttu-id="46abe-203">您可以藉由調整四邊形大小的 x、y 和 z 值來解決此問題，直到您對它的外觀感到滿意為止。</span><span class="sxs-lookup"><span data-stu-id="46abe-203">You can fix this by adjusting the values x, y and z values of the size of the quad until you are satisfied with the way it looks.</span></span>

    <span data-ttu-id="46abe-204">若要使用平移手勢，您需要在物件上使用碰撞器。</span><span class="sxs-lookup"><span data-stu-id="46abe-204">To use the pan gesture, you will need a collider on your object.</span></span> <span data-ttu-id="46abe-205">您可能會看到四邊形已經有一個網格碰撞器。</span><span class="sxs-lookup"><span data-stu-id="46abe-205">You may see the quad already has a mesh collider.</span></span> <span data-ttu-id="46abe-206">然而，網格碰撞器並不理想，因為它非常薄並且難以選取。</span><span class="sxs-lookup"><span data-stu-id="46abe-206">However, the mesh collider is not ideal, because it is extremely thin and difficult to select.</span></span> <span data-ttu-id="46abe-207">我們建議用方塊碰撞器取代網格碰撞器。</span><span class="sxs-lookup"><span data-stu-id="46abe-207">We suggest replacing the mesh collider with a box collider.</span></span>

5. <span data-ttu-id="46abe-208">以滑鼠右鍵按一下 [偵測器] 面板上 [四個] 的網格碰撞。</span><span class="sxs-lookup"><span data-stu-id="46abe-208">Right-click the mesh collider that’s on the quad from the Inspector panel.</span></span> <span data-ttu-id="46abe-209">然後按一下 [移除元件] 將它移除。</span><span class="sxs-lookup"><span data-stu-id="46abe-209">Then remove it by clicking Remove Component.</span></span>

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. <span data-ttu-id="46abe-211">現在，按一下 [新增元件] 並搜尋「方塊碰撞器」，以新增方塊碰撞器。</span><span class="sxs-lookup"><span data-stu-id="46abe-211">Now add the box collider by clicking Add Component and searching “box collider”.</span></span> <span data-ttu-id="46abe-212">預設新增的方塊碰撞，仍然太精簡，因此請按一下 [編輯碰撞] 按鈕進行編輯。</span><span class="sxs-lookup"><span data-stu-id="46abe-212">The default added box collider is still too thin, so click the Edit Collider button to edit.</span></span> <span data-ttu-id="46abe-213">按下它時，可以使用 x、y 和 z 值或場景編輯器中的元素調整大小。</span><span class="sxs-lookup"><span data-stu-id="46abe-213">When it’s pressed in, you can adjust the size using the x, y and z values or the elements in the scene editor.</span></span> <span data-ttu-id="46abe-214">針對我們的範例，我們希望將方塊碰撞器延伸到四邊形後面。</span><span class="sxs-lookup"><span data-stu-id="46abe-214">For our example, we want to extend the box collider a little behind the quad.</span></span> <span data-ttu-id="46abe-215">在場景編輯器中，從後面向外拖曳方塊碰撞器 (請參閱下圖)。</span><span class="sxs-lookup"><span data-stu-id="46abe-215">In the scene editor, drag the box collider from the back, outwards (see the image below).</span></span> <span data-ttu-id="46abe-216">這可讓使用者不只使用手指，而是要滾動的全手勢。</span><span class="sxs-lookup"><span data-stu-id="46abe-216">This lets the user not only use their finger, but their entire hand to scroll.</span></span>

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. <span data-ttu-id="46abe-218">使其具互動性。</span><span class="sxs-lookup"><span data-stu-id="46abe-218">Make it interactive.</span></span> <span data-ttu-id="46abe-219">因為我們想要直接與四個程式互動，所以我們想要使用我們在第4課用來從顆 octa 物件播放音樂的近距離互動 Touchable 元件。</span><span class="sxs-lookup"><span data-stu-id="46abe-219">Since we want to interact with the quad directly, we want to use the Near Interaction Touchable component that we used this in Lesson 4 for playing music from the Octa object.</span></span> <span data-ttu-id="46abe-220">按一下 [新增元件]，搜尋「接近互動 touchable」並加以選取，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="46abe-220">Click Add Component, search for “near interaction touchable” and select it as shown in the images below.</span></span>

    ![mrlearning-base-ch5-2-step7a .png](images/mrlearning-base-ch5-2-step7a.png)

    <span data-ttu-id="46abe-222">如果您看到關於界限和/或中心不符合 BoxCollider 大小和/或中心的黃色警告，請按一下 [修正範圍] 和/或 [修正中心] 按鈕，以更新中間和界限值。</span><span class="sxs-lookup"><span data-stu-id="46abe-222">If you see a yellow warning about bounds and/or center not matching the BoxCollider's size and/or center, click the Fix Bounds and/or Fix Center buttons to update the center and bounds values.</span></span>

    ![mrlearning-base-ch5-2-step7b .png](images/mrlearning-base-ch5-2-step7b.png)

8. <span data-ttu-id="46abe-224">新增可辨識平移手勢的功能。</span><span class="sxs-lookup"><span data-stu-id="46abe-224">Add the ability to recognize the pan gesture.</span></span> <span data-ttu-id="46abe-225">按一下 [新增元件]，在 [搜尋] 欄位中輸入「手互動」，然後新增「手互動」的「流覽縮放腳本」元件。</span><span class="sxs-lookup"><span data-stu-id="46abe-225">Click Add Component, type “hand interaction” in the search field and add the Hand Interaction Pan Zoom script component.</span></span>

    ![mrlearning-base-ch5-2-step8a .png](images/mrlearning-base-ch5-2-step8a.png)

    <span data-ttu-id="46abe-227">如此一來，您就有一個啟用 pan 的四個。</span><span class="sxs-lookup"><span data-stu-id="46abe-227">And with that, you have a pan-enabled quad.</span></span>

    <span data-ttu-id="46abe-228">如您所見，「手互動」的「移動流覽縮放」元件有各種設定，做為選擇性的練習，您可以自由地玩。</span><span class="sxs-lookup"><span data-stu-id="46abe-228">As you can see, the Hand Interaction Pan Zoom component has various setting, as an optional exercise, feel free to play around with them.</span></span>

    ![mrlearning-base-ch5-2-step8b .png](images/mrlearning-base-ch5-2-step8b.png)

<!--TMP
   Next, we will learn how to pan 3D objects. 

10. Right-click the quad object, select 3D object and click Cube. Scale the cube so that it’s roughly x = 0.1, y = 0.1 and z = 0.1. Copy that cube three times by right-clicking the cube and pressing duplicate, or by pressing control/command D. Space them out evenly. Your scene should look similar to the image below.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)

11. Select the quad again and under the hand interaction pan script, set the pan actions to each of the cubes. Under Pan Event Receivers, we want to specify the number of objects receiving the event. Since there are four cubes, type “4” and press Enter. Four empty fields should appear.

![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)

12. Drag each of the cubes into each of the empty element slots.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Add the Move with Pan script to all of the cubes by pressing and holding control/command and select each object. From the Inspector panel, click Add Component and search for “move with pan.” Click the script and it is added to each cube. Now the 3D objects will move with your pan gesture. If you remove the mesh render on your quad, you should now have an invisible quad where you can pan through a list of 3D objects.
-->

### <a name="eye-tracking"></a><span data-ttu-id="46abe-230">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="46abe-230">Eye Tracking</span></span>

<span data-ttu-id="46abe-231">在本節中，我們將探討如何在我們的示範中啟用眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="46abe-231">In this section, we will explore how to enable eye tracking in our demo.</span></span> <span data-ttu-id="46abe-232">當您的眼睛 gazed 時，我們會慢慢旋轉3D 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="46abe-232">We will slowly spin our 3D menu items when they are being gazed upon with your eye gaze.</span></span> <span data-ttu-id="46abe-233">當選取注視項目時，我們也會觸發有趣的效果。</span><span class="sxs-lookup"><span data-stu-id="46abe-233">We will also trigger a fun effect when the gazed-upon item is selected.</span></span>

1. <span data-ttu-id="46abe-234">請確定已正確設定 MRTK 設定檔以進行眼追蹤。</span><span class="sxs-lookup"><span data-stu-id="46abe-234">Ensure the MRTK profiles are properly configured for eye tracking.</span></span> <span data-ttu-id="46abe-235">若要這麼做，請移至[MRTK 指示中的開始使用眼睛追蹤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)，並查看[設定眼追蹤逐步](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step)執行一節中的步驟，確認是否已正確設定眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="46abe-235">To do this, go to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions and verify that eye tracking is properly configured by reviewing the steps in the [Setting up eye tracking step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) section.</span></span> <span data-ttu-id="46abe-236">完成檔中剩餘的步驟。</span><span class="sxs-lookup"><span data-stu-id="46abe-236">Complete any remaining steps in the documentation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="46abe-237">如果您使用 DefaultHoloLens2InputSystemProfile （如[設定混合現實工具](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit)組課程中所述）來複製您的自訂 MRTK 設定設定檔，則依預設會在 unity 專案中啟用監看追蹤，但您仍然必須設定 unity 編輯器的眼睛追蹤模擬，並設定 Visual Studio 以允許組建的眼追蹤。</span><span class="sxs-lookup"><span data-stu-id="46abe-237">If you used the DefaultHoloLens2InputSystemProfile, as instructed in the [Configure the Mixed Reality Toolkit](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) lesson, to clone your custom MRTK configuration profile, eye tracking is enabled by default in the Unity project but you will still have to set up eye tracking simulation for the Unity editor and configure Visual Studio to allow eye tracking for the build.</span></span>

    <span data-ttu-id="46abe-238">上述連結提供下列事項的簡短指示：</span><span class="sxs-lookup"><span data-stu-id="46abe-238">The link above provides brief instructions for:</span></span>

    - <span data-ttu-id="46abe-239">建立要在 MRTK 設定檔中使用的 Windows Mixed Reality 眼注視 Data Provider</span><span class="sxs-lookup"><span data-stu-id="46abe-239">Creating the Windows Mixed Reality Eye Gaze Data Provider for use in the MRTK profile</span></span>
    - <span data-ttu-id="46abe-240">在連接至相機的注視提供者中啟用眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="46abe-240">Enabling eye tracking in the Gaze Provider attached to the camera</span></span>
    - <span data-ttu-id="46abe-241">在 Unity 編輯器中設定眼睛追蹤模擬</span><span class="sxs-lookup"><span data-stu-id="46abe-241">Setting up an eye tracking simulation in the Unity editor</span></span>
    - <span data-ttu-id="46abe-242">編輯 Visual Studio 解決方案的功能，以允許在建置的應用程式中進行眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="46abe-242">Editing the Visual Studio solution's capabilities to allow eye tracking in the built application</span></span>

2. <span data-ttu-id="46abe-243">將眼球追蹤目標元件新增至目標物件。</span><span class="sxs-lookup"><span data-stu-id="46abe-243">Add the Eye Tracking Target component to target objects.</span></span> <span data-ttu-id="46abe-244">若要讓物件回應眼睛眼事件，我們必須在每個想要使用眼睛互動的物件上新增 EyeTrackingTarget 元件。</span><span class="sxs-lookup"><span data-stu-id="46abe-244">To allow an object to respond to eye gaze events, we'll need to add the EyeTrackingTarget component on each object that we want to interact with by using eye gaze.</span></span> <span data-ttu-id="46abe-245">將此元件新增至作為方格集合一部分之九個 3D 物件中的每一個。</span><span class="sxs-lookup"><span data-stu-id="46abe-245">Add this component to each of the nine 3D objects that are part of the grid collection.</span></span>

    >[!TIP]
    ><span data-ttu-id="46abe-246">您可以使用 shift 和/或 ctrl 鍵選取場景階層中的多個專案，然後大量加入 EyeTrackingTarget 元件。</span><span class="sxs-lookup"><span data-stu-id="46abe-246">You can use the shift and/or ctrl keys to select multiple items in the scene hierarchy and then bulk-add the EyeTrackingTarget component.</span></span>

    ![Lesson5 Chapter3 步驟2](images/Lesson5Chapter3Step2.JPG)

3. <span data-ttu-id="46abe-248">接下來，我們會新增 EyeTrackingTutorialDemo 腳本來進行一些令人興奮的互動。</span><span class="sxs-lookup"><span data-stu-id="46abe-248">Next, we will add the EyeTrackingTutorialDemo script for some exciting interactions.</span></span> <span data-ttu-id="46abe-249">EyeTrackingTutorialDemo 腳本包含在本教學課程系列存放庫中。</span><span class="sxs-lookup"><span data-stu-id="46abe-249">The EyeTrackingTutorialDemo script is included as part of this tutorial series repository.</span></span> <span data-ttu-id="46abe-250">預設不包含混合現實工具組。</span><span class="sxs-lookup"><span data-stu-id="46abe-250">It is not included by default with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="46abe-251">針對方格集合中的每個3D 物件，藉由在 [加入元件] 功能表中搜尋元件來新增 EyeTrackingTutorialDemo 腳本。</span><span class="sxs-lookup"><span data-stu-id="46abe-251">For each 3D object in the grid collection, add the EyeTrackingTutorialDemo script by searching for the component in the Add Component menu.</span></span>

   ![Lesson5 Chapter3 步驟3](images/Lesson5Chapter3Step3.JPG)

4. <span data-ttu-id="46abe-253">在注視目標時旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="46abe-253">Spin the object while looking at the target.</span></span> <span data-ttu-id="46abe-254">我們想要設定我們的3D 物件，以在我們查看時旋轉。</span><span class="sxs-lookup"><span data-stu-id="46abe-254">We want to configure our 3D objects to spin while we are looking at them.</span></span> <span data-ttu-id="46abe-255">若要這麼做，請在查看 EyeTrackingTarget 元件的 Target （）區段時，在中插入新的欄位，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="46abe-255">To do this, insert a new field in the While Looking At Target() section of the EyeTrackingTarget component, as shown in the image below.</span></span>

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    <span data-ttu-id="46abe-257">在新建立的欄位中，將目前的遊戲物件新增至空白欄位，然後選取 [EyeTrackingTutorialDemo > RotateTarget （）]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="46abe-257">In the newly-created field, add the current Game Object to the empty field, and select EyeTrackingTutorialDemo>RotateTarget(), as shown in the image below.</span></span> <span data-ttu-id="46abe-258">現在，3D 物件被設定為在透過眼球追蹤注視時旋轉。</span><span class="sxs-lookup"><span data-stu-id="46abe-258">Now the 3D object is configured to spin when it is being gazed upon with eye tracking.</span></span>

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. <span data-ttu-id="46abe-260">加入「中斷目標」的功能，這是以點按方式選取，或說出「select」時所 gazed 的。</span><span class="sxs-lookup"><span data-stu-id="46abe-260">Add in the ability to “blip target” that is being gazed at upon select by air-tap or saying “select”.</span></span> <span data-ttu-id="46abe-261">與步驟4類似，我們想要藉由將 EyeTrackingTutorialDemo 指派給 EyeTrackingTarget 元件的遊戲物件的 Select （）欄位來觸發 > BlipTarget （），如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="46abe-261">Similar to Step 4, we want to trigger EyeTrackingTutorialDemo>BlipTarget() by assigning it to the game object’s Select() field of the EyeTrackingTarget component, as shown in the figure below.</span></span> <span data-ttu-id="46abe-262">現在設定完成後，每當您觸發選取動作（例如，按下點或語音命令「選取」）時，就會注意到遊戲物件有些許中斷。</span><span class="sxs-lookup"><span data-stu-id="46abe-262">With this now configured, you will notice a slight blip in the game object whenever you trigger a select action, such as air-tap or the voice command “select”.</span></span>

    ![Lesson5 Chapter3 步驟5](images/Lesson5Chapter3Step5.JPG)

6. <span data-ttu-id="46abe-264">在建置 HoloLens 2 之前，請確定已正確設定眼球追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="46abe-264">Ensure eye tracking capabilities are properly configured before building to HoloLens 2.</span></span> <span data-ttu-id="46abe-265">在撰寫本文時，Unity 尚未能夠設定眼追蹤功能的注視輸入。</span><span class="sxs-lookup"><span data-stu-id="46abe-265">As of this writing, Unity does not yet have the ability to set the gaze input for eye tracking capabilities.</span></span> <span data-ttu-id="46abe-266">需要設定這項功能，眼睛追蹤才能在 HoloLens 2 中工作。</span><span class="sxs-lookup"><span data-stu-id="46abe-266">Setting this capability is required for eye tracking to work in HoloLens 2.</span></span> <span data-ttu-id="46abe-267">請遵循在[HoloLens 2 上測試 Unity 應用程式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)的指示，以啟用注視輸入功能。</span><span class="sxs-lookup"><span data-stu-id="46abe-267">Follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions to enable the gaze input capability.</span></span>

## <a name="congratulations"></a><span data-ttu-id="46abe-268">恭喜！</span><span class="sxs-lookup"><span data-stu-id="46abe-268">Congratulations</span></span>

<span data-ttu-id="46abe-269">您已成功將基本眼追蹤功能新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="46abe-269">You’ve successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="46abe-270">這些動作只是眼球追蹤功能無限可能性的開端。</span><span class="sxs-lookup"><span data-stu-id="46abe-270">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="46abe-271">本章也會在第5課結束，我們已瞭解先進的輸入功能，例如語音命令、移動流覽手勢和眼追蹤。</span><span class="sxs-lookup"><span data-stu-id="46abe-271">This chapter also concludes Lesson 5, where we learned about advanced input functionality, such as voice commands, panning gestures, and eye tracking.</span></span>

[<span data-ttu-id="46abe-272">下一課： 7. 建立農曆模組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="46abe-272">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
