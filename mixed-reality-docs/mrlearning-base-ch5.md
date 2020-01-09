---
title: 快速入門教學課程-6。 探索先進的輸入選項
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 75a14697953026474d8ca00e6473145d7b12a482
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334352"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="1079c-105">6. 探索 advanced 輸入選項</span><span class="sxs-lookup"><span data-stu-id="1079c-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="1079c-106">在本教學課程中，會探索 HoloLens 2 的數個先進的輸入選項，包括使用語音命令、移動流覽手勢和眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="1079c-106">In this tutorial, several advanced input options for HoloLens 2 are explored, including the use of voice commands, panning gesture, and eye tracking.</span></span> 

## <a name="objectives"></a><span data-ttu-id="1079c-107">目標</span><span class="sxs-lookup"><span data-stu-id="1079c-107">Objectives</span></span>

- <span data-ttu-id="1079c-108">使用語音命令和關鍵字觸發事件</span><span class="sxs-lookup"><span data-stu-id="1079c-108">Trigger events using voice commands and keywords</span></span>
- <span data-ttu-id="1079c-109">使用追蹤的手平移材質和3D 物件</span><span class="sxs-lookup"><span data-stu-id="1079c-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
- <span data-ttu-id="1079c-110">利用 HoloLens 2 眼追蹤功能來選取物件</span><span class="sxs-lookup"><span data-stu-id="1079c-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="1079c-111">啟用語音命令</span><span class="sxs-lookup"><span data-stu-id="1079c-111">Enabling Voice Commands</span></span>

<span data-ttu-id="1079c-112">在本節中，會執行兩個語音命令。</span><span class="sxs-lookup"><span data-stu-id="1079c-112">In this section, two voice commands are implemented.</span></span> <span data-ttu-id="1079c-113">首先，您可以藉由說「切換診斷」來引進切換畫面播放速率診斷面板的功能。</span><span class="sxs-lookup"><span data-stu-id="1079c-113">First, the ability to toggle the frame rate diagnostics panel is introduced by saying "toggle diagnostics".</span></span> <span data-ttu-id="1079c-114">第二，會探索使用語音命令來播放音效的功能。</span><span class="sxs-lookup"><span data-stu-id="1079c-114">Second, the ability to play a sound with a voice command is explored.</span></span> <span data-ttu-id="1079c-115">負責設定語音命令的 MRTK 設定檔和設定會先進行審核。</span><span class="sxs-lookup"><span data-stu-id="1079c-115">The MRTK profiles and settings responsible for configuring voice commands is reviewed first.</span></span>

1. <span data-ttu-id="1079c-116">在 BaseScene 階層中，選取 [MixedRealityToolkit]。</span><span class="sxs-lookup"><span data-stu-id="1079c-116">In the BaseScene hierarchy, select MixedRealityToolkit.</span></span> <span data-ttu-id="1079c-117">然後，在 [偵測器] 面板中選取 [輸入]，然後按一下 DefaultMixedRealityInputSystemProfile 左邊的小型 [複製] 按鈕，以開啟 [複製設定檔] 快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="1079c-117">Then, in the Inspector panel, select Input and click the small Clone button to the left of the DefaultMixedRealityInputSystemProfile to open the Clone Profile popup.</span></span> <span data-ttu-id="1079c-118">在快顯視窗中按一下 [複製]，以建立新的設定檔 MixedRealityInputSystemProfile。</span><span class="sxs-lookup"><span data-stu-id="1079c-118">In the popup click Clone to create a new profile MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1a .png](images/mrlearning-base-ch5-1-step1a.png)

    <span data-ttu-id="1079c-120">這也會使用新建立的 MixedRealityInputSystemProfile 自動填入 MixedRealityToolkitConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="1079c-120">This will also auto-populate the MixedRealityToolkitConfigurationProfile with the newly created MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1b .png](images/mrlearning-base-ch5-1-step1b.png)

2. <span data-ttu-id="1079c-122">在輸入系統設定檔中，有各種不同的設定。</span><span class="sxs-lookup"><span data-stu-id="1079c-122">In the input system profile, there are a variety of settings.</span></span> <span data-ttu-id="1079c-123">針對語音命令，請展開 [語音] 區段，並遵循與上一個步驟相同的程式來複製 DefaultMixedRealitySpeechCommandsProfile，並將它取代為您自己的可編輯複本。</span><span class="sxs-lookup"><span data-stu-id="1079c-123">For voice commands, expand the Speech section and follow the same process as in the previous step to clone the DefaultMixedRealitySpeechCommandsProfile and replace it with your own editable copy.</span></span>

    ![mrlearning-base-ch5-1-step2 .png](images/mrlearning-base-ch5-1-step2.png)

    <span data-ttu-id="1079c-125">在語音命令設定檔中，您會注意到一系列的設定。</span><span class="sxs-lookup"><span data-stu-id="1079c-125">In the speech command profile, you’ll notice a range of settings.</span></span> <span data-ttu-id="1079c-126">如需這些設定的完整說明，請參閱[MRTK 語音檔](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。</span><span class="sxs-lookup"><span data-stu-id="1079c-126">For a full description of these settings, refer to the [MRTK speech documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>).</span></span>

    <span data-ttu-id="1079c-127">根據預設，一般行為是自動啟動。</span><span class="sxs-lookup"><span data-stu-id="1079c-127">By default, the general behavior is auto-start.</span></span> <span data-ttu-id="1079c-128">如有需要，您可以將此變更為手動啟動。</span><span class="sxs-lookup"><span data-stu-id="1079c-128">This can be changed to manual-start, if desired.</span></span> <span data-ttu-id="1079c-129">但在此範例中，請將它保持在自動啟動。</span><span class="sxs-lookup"><span data-stu-id="1079c-129">But for this example, keep it on auto-start.</span></span> <span data-ttu-id="1079c-130">MRTK 隨附數個預設語音命令，例如功能表、切換診斷和切換 profiler。</span><span class="sxs-lookup"><span data-stu-id="1079c-130">The MRTK comes with several default voice commands, such as menu, toggle diagnostics and toggle profiler.</span></span> <span data-ttu-id="1079c-131">我們將使用關鍵字「切換診斷」，以開啟和關閉診斷的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="1079c-131">We will use the keyword “toggle diagnostics,” in order to turn on and off the diagnostics framerate counter.</span></span> <span data-ttu-id="1079c-132">我們還將在下列步驟中加入新的語音命令。</span><span class="sxs-lookup"><span data-stu-id="1079c-132">We will also add a new voice command in the steps below.</span></span>

3. <span data-ttu-id="1079c-133">加入新的語音命令。</span><span class="sxs-lookup"><span data-stu-id="1079c-133">Add a new voice command.</span></span> <span data-ttu-id="1079c-134">若要這樣做，請按一下 [+ 新增語音命令] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1079c-134">To do this, click the + Add a New Speech Command button.</span></span> <span data-ttu-id="1079c-135">您會看到出現在現有語音命令清單下方的新行。</span><span class="sxs-lookup"><span data-stu-id="1079c-135">You'll see a new line that appears below the list of existing voice commands.</span></span> <span data-ttu-id="1079c-136">輸入您想要使用的語音命令。</span><span class="sxs-lookup"><span data-stu-id="1079c-136">Type the voice command you want to use.</span></span> <span data-ttu-id="1079c-137">在此範例中，使用「播放音樂」命令。</span><span class="sxs-lookup"><span data-stu-id="1079c-137">In this example, use the command “play music".</span></span>

    ![mrlearning-base-ch5-1-step3 .png](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    ><span data-ttu-id="1079c-139">您也可以為語音命令設定按鍵代碼。</span><span class="sxs-lookup"><span data-stu-id="1079c-139">You can also set a keycode for speech commands.</span></span> <span data-ttu-id="1079c-140">這可讓語音命令在按下鍵盤按鍵時觸發事件。</span><span class="sxs-lookup"><span data-stu-id="1079c-140">This allows for voice commands to trigger events upon the press of a keyboard key.</span></span>

4. <span data-ttu-id="1079c-141">新增回應語音命令的功能。</span><span class="sxs-lookup"><span data-stu-id="1079c-141">Add the ability to respond to voice commands.</span></span> <span data-ttu-id="1079c-142">在 BaseScene 階層中選取任何未附加任何其他輸入腳本的物件，例如 MixedRealityPlayspace 遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="1079c-142">Select any object in the BaseScene hierarchy that does not have any other input scripts attached to it, for example, the MixedRealityPlayspace game object.</span></span> <span data-ttu-id="1079c-143">在 [偵測器] 面板中，按一下 [新增元件]，搜尋 "speech"，然後選取語音輸入處理常式腳本。</span><span class="sxs-lookup"><span data-stu-id="1079c-143">In the Inspector panel, click Add Component, search for "speech", and select the Speech Input Handler script.</span></span>

    ![mrlearning-base-ch5-1-step4 .png](images/mrlearning-base-ch5-1-step4.png)

    <span data-ttu-id="1079c-145">根據預設，您會看到兩個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1079c-145">By default, you will see two checkboxes.</span></span> <span data-ttu-id="1079c-146">其中一個是 [需要焦點] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1079c-146">One is the Is Focus Required checkbox.</span></span> <span data-ttu-id="1079c-147">因此，只要您是以光線眼、列印頭、控制器眼或手注視的方式來指向物件，就會觸發語音命令。</span><span class="sxs-lookup"><span data-stu-id="1079c-147">So, as long as you are pointing at the object with a ray-eye-gaze, head-gaze, controller-gaze, or hand-gaze, the voice command will be triggered.</span></span> <span data-ttu-id="1079c-148">取消核取此核取方塊，讓使用者不需要查看物件即可使用語音命令。</span><span class="sxs-lookup"><span data-stu-id="1079c-148">Uncheck this checkbox so that the user does not have to look at the object to use the voice command.</span></span>

5. <span data-ttu-id="1079c-149">新增回應語音命令的功能。</span><span class="sxs-lookup"><span data-stu-id="1079c-149">Add the ability to respond to a voice command.</span></span> <span data-ttu-id="1079c-150">若要這麼做，請按一下語音輸入處理常式中的 [+] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1079c-150">To do this, click the + button that’s in the Speech Input Handler.</span></span>

    ![mrlearning-base-ch5-1-step5 .png](images/mrlearning-base-ch5-1-step5.png)

6. <span data-ttu-id="1079c-152">在 [關鍵字] 旁，您會看到一個下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="1079c-152">Next to Keyword, you'll see a dropdown menu.</span></span> <span data-ttu-id="1079c-153">選取 [切換診斷]，如此一來，每當使用者說出「切換診斷」片語時，它就會觸發動作。</span><span class="sxs-lookup"><span data-stu-id="1079c-153">Select Toggle Diagnostics so that whenever the user says the phrase “toggle diagnostics”, it triggers an action.</span></span> <span data-ttu-id="1079c-154">請注意，您可能需要按下旁邊的箭號來展開元素0。</span><span class="sxs-lookup"><span data-stu-id="1079c-154">Note that you might need to expand Element 0 by pressing the arrow next to it.</span></span>

    ![mrlearning-base-ch5-1-step6 .png](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    ><span data-ttu-id="1079c-156">系統會根據您在步驟3中編輯的設定檔，填入這些關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1079c-156">These keywords are populated, based on the profile you edited in the step 3.</span></span>

7. <span data-ttu-id="1079c-157">新增診斷系統 Voice 控制項腳本，以切換開啟和關閉的畫面播放速率計數器診斷。</span><span class="sxs-lookup"><span data-stu-id="1079c-157">Add the Diagnostics System Voice Controls script to toggle the framerate counter diagnostic on and off.</span></span> <span data-ttu-id="1079c-158">若要這麼做，請按 [新增元件]，搜尋 [診斷] [系統] [語音控制腳本]，然後從功能表中加以新增。</span><span class="sxs-lookup"><span data-stu-id="1079c-158">To do this, press Add Component, search for Diagnostics System Voice Controls script and add it from the menu.</span></span> <span data-ttu-id="1079c-159">此指令碼可以新增至任何物件，但為了簡單起見，我們將其新增至與語音輸入處理常式相同的物件中。</span><span class="sxs-lookup"><span data-stu-id="1079c-159">This script can be added to any object, but for simplicity, we will add it to the same object as the speech input handler.</span></span>

    ![mrlearning-base-ch5-1-step7 .png](images/mrlearning-base-ch5-1-step7.png)

8. <span data-ttu-id="1079c-161">在語音輸入處理常式中加入新的回應。</span><span class="sxs-lookup"><span data-stu-id="1079c-161">Add a new response in the speech input handler.</span></span> <span data-ttu-id="1079c-162">若要這麼做，請按一下 [+] 圖示，將新的回應新增至回應清單。</span><span class="sxs-lookup"><span data-stu-id="1079c-162">To do this, click the "+" icon to add a new response to the response list.</span></span>

    ![mrlearning-base-ch5-1-step8 .png](images/mrlearning-base-ch5-1-step8.png)

9. <span data-ttu-id="1079c-164">將具有「診斷系統聲音控制」腳本的物件拖曳至您剛才在上一個步驟中建立的新回應。</span><span class="sxs-lookup"><span data-stu-id="1079c-164">Drag the object that has the Diagnostics System Voice Controls script to the new response you just created in the previous step.</span></span>

    ![mrlearning-base-ch5-1-step9 .png](images/mrlearning-base-ch5-1-step9.png)

10. <span data-ttu-id="1079c-166">按一下 [函式] 下拉式清單（此處未顯示函式）、[診斷系統聲音控制]，然後選取將診斷切換為開啟和關閉的 ToggleDiagnostics （）函數。</span><span class="sxs-lookup"><span data-stu-id="1079c-166">Click the function dropdown (where it says No Function), then Diagnostics System Voice Controls, and select the ToggleDiagnostics () function which toggles your diagnostics on and off.</span></span>

    ![mrlearning-base-ch5-1-step10 .png](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > <span data-ttu-id="1079c-168">在建立您的裝置之前，您必須啟用 mic 設定。</span><span class="sxs-lookup"><span data-stu-id="1079c-168">Before building to your device, you need to enable mic settings.</span></span> <span data-ttu-id="1079c-169">若要這樣做，請按一下 [檔案] 並移至 [組建設定]、[播放程式設定]，並確定已設定麥克風功能。</span><span class="sxs-lookup"><span data-stu-id="1079c-169">To do this, click File and go to Build Settings, Player Settings and ensure that the microphone capability is set.</span></span>

    <span data-ttu-id="1079c-170">接下來，使用顆 octa 物件新增播放音訊檔案的功能。</span><span class="sxs-lookup"><span data-stu-id="1079c-170">Next, add the ability to play an audio file from voice command using the Octa object.</span></span> <span data-ttu-id="1079c-171">回想一下[第4課](mrlearning-base-ch4.md)，已新增播放音訊剪輯以觸及顆 octa 物件的能力。</span><span class="sxs-lookup"><span data-stu-id="1079c-171">Recall from [lesson 4](mrlearning-base-ch4.md) that the ability to play an audio clip from touching the Octa object was added.</span></span> <span data-ttu-id="1079c-172">我們將針對我們的音樂語音命令使用相同的音訊來源。</span><span class="sxs-lookup"><span data-stu-id="1079c-172">We will leverage this same audio source for our music voice command.</span></span>

11. <span data-ttu-id="1079c-173">選取 [BaseScene] 階層中的 [顆 octa] 物件。</span><span class="sxs-lookup"><span data-stu-id="1079c-173">Select the Octa object in the BaseScene hierarchy.</span></span>

12. <span data-ttu-id="1079c-174">新增另一個語音輸入處理常式（重複步驟4和5），但使用顆 octa 物件。</span><span class="sxs-lookup"><span data-stu-id="1079c-174">Add another speech input handler (repeat Steps 4 and 5), but with the octa object.</span></span>

13. <span data-ttu-id="1079c-175">請新增 [播放音樂語音] 命令，而不是從步驟6新增 [切換診斷語音] 命令，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1079c-175">Instead of adding the Toggle Diagnostics voice command from step 6, add the Play Music voice command as shown in the image below.</span></span>

    ![mrlearning-base-ch5-1-step13 .png](images/mrlearning-base-ch5-1-step13.png)

14. <span data-ttu-id="1079c-177">如同步驟8和9，加入新的回應，並將顆 octa 物件（包含診斷系統 Voice 控制項腳本的物件）拖曳至空白回應位置。</span><span class="sxs-lookup"><span data-stu-id="1079c-177">As with Steps 8 and 9, add a new response and drag the Octa object, the object that has the Diagnostics System Voice Controls script on it, to the empty response slot.</span></span>

15. <span data-ttu-id="1079c-178">選取顯示 [沒有函數] 的下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="1079c-178">Select the dropdown menu that says No Function.</span></span> <span data-ttu-id="1079c-179">然後選取 [音訊來源]，後面接著 [PlayOneShot （AudioClip）]。</span><span class="sxs-lookup"><span data-stu-id="1079c-179">Then select Audio Source, followed by PlayOneShot (AudioClip).</span></span>

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. <span data-ttu-id="1079c-181">在此範例中，我們將使用[第4課](mrlearning-base-ch4.md)的相同音訊剪輯。</span><span class="sxs-lookup"><span data-stu-id="1079c-181">For this example, we are going to use the same audio clip from [Lesson 4](mrlearning-base-ch4.md).</span></span> <span data-ttu-id="1079c-182">移至您的 [專案] 面板，搜尋 "MRTK_Gem" 音訊剪輯，並將它拖曳到音訊來源位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1079c-182">Go into your Project panel, search for “MRTK_Gem” audio clip and drag it into the audio source slot as shown in the image below.</span></span> <span data-ttu-id="1079c-183">現在，您的應用程式會回應語音命令「切換診斷」，以切換 [畫面播放速率計數器] 面板並播放音樂來播放 MRTK_Gem 的歌曲。</span><span class="sxs-lookup"><span data-stu-id="1079c-183">Now your application will respond to the voice commands “toggle diagnostics” to toggle the Frame Rate Counter panel and Play Music to play the MRTK_Gem song.</span></span>

    ![Lesson5 Chapter1.txt Step16im](images/Lesson5_chapter1_step16im.PNG)

## <a name="the-pan-gesture"></a><span data-ttu-id="1079c-185">平移手勢</span><span class="sxs-lookup"><span data-stu-id="1079c-185">The Pan Gesture</span></span>

<span data-ttu-id="1079c-186">在本節中，您將瞭解如何使用平移手勢。</span><span class="sxs-lookup"><span data-stu-id="1079c-186">In this section, you will learn how to use the pan gesture.</span></span> <span data-ttu-id="1079c-187">這適用于使用手指或手來滾動內容的捲軸。</span><span class="sxs-lookup"><span data-stu-id="1079c-187">This is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="1079c-188">您也可以使用平移手勢來旋轉物件、迴圈流覽3D 物件的集合，甚至是滾動 2D UI。</span><span class="sxs-lookup"><span data-stu-id="1079c-188">You can also use the pan gesture to rotate objects, cycle through a collection of 3D objects, or even to scroll a 2D UI.</span></span>

1. <span data-ttu-id="1079c-189">建立四邊形。</span><span class="sxs-lookup"><span data-stu-id="1079c-189">Create a quad.</span></span> <span data-ttu-id="1079c-190">在 BaseScene 階層中，以滑鼠右鍵按一下 [3D 物件]，然後選取 [四]。</span><span class="sxs-lookup"><span data-stu-id="1079c-190">In your BaseScene hierarchy, right-click, select "3D Object" followed by Quad.</span></span>

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. <span data-ttu-id="1079c-192">適當地重新置放四個。</span><span class="sxs-lookup"><span data-stu-id="1079c-192">Reposition the quad, as appropriate.</span></span> <span data-ttu-id="1079c-193">在我們的範例中，我們將 x = 0、y = 0 和 z = 1.5 遠離相機，以取得 HoloLens 2 的舒適位置。</span><span class="sxs-lookup"><span data-stu-id="1079c-193">For our example, we set the x = 0, the y = 0 and the z = 1.5 away from the camera for a comfortable position from HoloLens 2.</span></span>

    >[!NOTE]
    ><span data-ttu-id="1079c-194">如果四個區塊或位於先前課程中的任何內容前方，請務必將其移動，使其不會封鎖任何其他物件。</span><span class="sxs-lookup"><span data-stu-id="1079c-194">If the quad blocks or is in front of any content from the previous lessons, be sure to move it so that it doesn’t block any of the other objects.</span></span>

3. <span data-ttu-id="1079c-195">將材質套用至四邊形。</span><span class="sxs-lookup"><span data-stu-id="1079c-195">Apply a material to the quad.</span></span> <span data-ttu-id="1079c-196">這份材料將是我們將透過移動流覽手勢來進行的動作。</span><span class="sxs-lookup"><span data-stu-id="1079c-196">This material will be what we will be scrolling through with the pan gesture.</span></span>

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. <span data-ttu-id="1079c-198">在 [專案] 面板的 [搜尋] 方塊中，輸入「pan 內容」。</span><span class="sxs-lookup"><span data-stu-id="1079c-198">In your Projects panel, type “pan content” in the Search box.</span></span> <span data-ttu-id="1079c-199">將該材料拖曳到場景中的四個。</span><span class="sxs-lookup"><span data-stu-id="1079c-199">Drag that material onto the quad in your scene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="1079c-200">PanContent 材料不是 MRTK 的一部分，而是包含在上一課匯入的 BaseModuleAssets 資產中。</span><span class="sxs-lookup"><span data-stu-id="1079c-200">The PanContent material is not part of MRTK but included with the BaseModuleAssets asset imported in the previous lesson.</span></span>

    <span data-ttu-id="1079c-201">若要使用平移手勢，您需要在物件上使用碰撞器。</span><span class="sxs-lookup"><span data-stu-id="1079c-201">To use the pan gesture, you will need a collider on your object.</span></span> <span data-ttu-id="1079c-202">您可能會看到四邊形已經有一個網格碰撞器。</span><span class="sxs-lookup"><span data-stu-id="1079c-202">You may see the quad already has a mesh collider.</span></span> <span data-ttu-id="1079c-203">然而，網格碰撞器並不理想，因為它非常薄並且難以選取。</span><span class="sxs-lookup"><span data-stu-id="1079c-203">However, the mesh collider is not ideal, because it is extremely thin and difficult to select.</span></span> <span data-ttu-id="1079c-204">我們建議用方塊碰撞器取代網格碰撞器。</span><span class="sxs-lookup"><span data-stu-id="1079c-204">We suggest replacing the mesh collider with a box collider.</span></span>

5. <span data-ttu-id="1079c-205">以滑鼠右鍵按一下 [偵測器] 面板上 [四個] 的網格碰撞。</span><span class="sxs-lookup"><span data-stu-id="1079c-205">Right-click the mesh collider that’s on the quad from the Inspector panel.</span></span> <span data-ttu-id="1079c-206">然後按一下 [移除元件] 將它移除。</span><span class="sxs-lookup"><span data-stu-id="1079c-206">Then remove it by clicking Remove Component.</span></span>

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. <span data-ttu-id="1079c-208">現在，按一下 [新增元件] 並搜尋「方塊碰撞器」，以新增方塊碰撞器。</span><span class="sxs-lookup"><span data-stu-id="1079c-208">Now add the box collider by clicking Add Component and searching “box collider”.</span></span> <span data-ttu-id="1079c-209">預設新增的方塊碰撞，仍然太精簡，因此請按一下 [編輯碰撞] 按鈕進行編輯。</span><span class="sxs-lookup"><span data-stu-id="1079c-209">The default added box collider is still too thin, so click the Edit Collider button to edit.</span></span> <span data-ttu-id="1079c-210">按下它時，可以使用 x、y 和 z 值或場景編輯器中的元素調整大小。</span><span class="sxs-lookup"><span data-stu-id="1079c-210">When it’s pressed in, you can adjust the size using the x, y and z values or the elements in the scene editor.</span></span> <span data-ttu-id="1079c-211">針對我們的範例，我們希望將方塊碰撞器延伸到四邊形後面。</span><span class="sxs-lookup"><span data-stu-id="1079c-211">For our example, we want to extend the box collider a little behind the quad.</span></span> <span data-ttu-id="1079c-212">在場景編輯器中，從後面向外拖曳方塊碰撞器 (請參閱下圖)。</span><span class="sxs-lookup"><span data-stu-id="1079c-212">In the scene editor, drag the box collider from the back, outwards (see the image below).</span></span> <span data-ttu-id="1079c-213">這可讓使用者不只使用手指，而是要滾動的全手勢。</span><span class="sxs-lookup"><span data-stu-id="1079c-213">This lets the user not only use their finger, but their entire hand to scroll.</span></span>

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. <span data-ttu-id="1079c-215">使其具互動性。</span><span class="sxs-lookup"><span data-stu-id="1079c-215">Make it interactive.</span></span> <span data-ttu-id="1079c-216">因為我們想要直接與四個程式互動，所以我們想要使用我們在第4課用來從顆 octa 物件播放音樂的近距離互動 Touchable 元件。</span><span class="sxs-lookup"><span data-stu-id="1079c-216">Since we want to interact with the quad directly, we want to use the Near Interaction Touchable component that we used this in Lesson 4 for playing music from the Octa object.</span></span> <span data-ttu-id="1079c-217">按一下 [新增元件]，搜尋「接近互動 touchable」並加以選取，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1079c-217">Click Add Component, search for “near interaction touchable” and select it as shown in the images below.</span></span>

    ![mrlearning-base-ch5-2-step7a .png](images/mrlearning-base-ch5-2-step7a.png)

    <span data-ttu-id="1079c-219">如果您看到關於界限和/或中心不符合 BoxCollider 大小和/或中心的黃色警告，請按一下 [修正範圍] 和/或 [修正中心] 按鈕，以更新中間和界限值。</span><span class="sxs-lookup"><span data-stu-id="1079c-219">If you see a yellow warning about bounds and/or center not matching the BoxCollider's size and/or center, click the Fix Bounds and/or Fix Center buttons to update the center and bounds values.</span></span>

    ![mrlearning-base-ch5-2-step7b .png](images/mrlearning-base-ch5-2-step7b.png)

8. <span data-ttu-id="1079c-221">新增可辨識平移手勢的功能。</span><span class="sxs-lookup"><span data-stu-id="1079c-221">Add the ability to recognize the pan gesture.</span></span> <span data-ttu-id="1079c-222">按一下 [新增元件]，在 [搜尋] 欄位中輸入「手互動」，然後新增「手互動」的「流覽縮放腳本」元件。</span><span class="sxs-lookup"><span data-stu-id="1079c-222">Click Add Component, type “hand interaction” in the search field and add the Hand Interaction Pan Zoom script component.</span></span>

    ![mrlearning-base-ch5-2-step8a .png](images/mrlearning-base-ch5-2-step8a.png)

    <span data-ttu-id="1079c-224">如此一來，您就有一個啟用 pan 的四個。</span><span class="sxs-lookup"><span data-stu-id="1079c-224">And with that, you have a pan-enabled quad.</span></span>

    <span data-ttu-id="1079c-225">如您所見，「手互動」的「流覽縮放腳本」元件具有各種設定，做為選擇性的練習，您可以自由地玩。</span><span class="sxs-lookup"><span data-stu-id="1079c-225">As you can see, the Hand Interaction Pan Zoom script component has various settings, as an optional exercise, feel free to play around with them.</span></span>

    ![mrlearning-base-ch5-2-step8b .png](images/mrlearning-base-ch5-2-step8b.png)

9. <span data-ttu-id="1079c-227">接下來，我們將學習如何平移 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="1079c-227">Next, we will learn how to pan 3D objects.</span></span>

    <span data-ttu-id="1079c-228">在階層中，以滑鼠右鍵按一下 [四個物件]，以開啟關聯式快顯功能表，然後選取 [ **3D 物件** > **Cube** ]，將 cube 加入場景中。</span><span class="sxs-lookup"><span data-stu-id="1079c-228">In the Hierarchy, right-click the Quad object, to open the contextual popup menu, then select **3D Object** > **Cube** to add a cube to your scene.</span></span>

    <span data-ttu-id="1079c-229">請確定 Cube 的**位置**設定為_0，0，0，_ 使其整齊地放在四個內。</span><span class="sxs-lookup"><span data-stu-id="1079c-229">Ensure the Cube's **Position** is set to  _0, 0, 0_ so it's positioned neatly within the Quad.</span></span> <span data-ttu-id="1079c-230">將 Cube 相應縮小至_0.1、0.1、0.1_的**規模**。</span><span class="sxs-lookup"><span data-stu-id="1079c-230">Scale the Cube down to a **Scale** of _0.1, 0.1, 0.1_.</span></span>

    ![mrlearning-base-ch5-2-step9 .png](images/mrlearning-base-ch5-2-step9.png)

    <span data-ttu-id="1079c-232">將 Cube 複製三次，方法是以滑鼠右鍵按一下 Cube，開啟關聯式快顯功能表，然後選取 [**複製**]。</span><span class="sxs-lookup"><span data-stu-id="1079c-232">Duplicate the Cube three times by right-clicking the Cube, to open the contextual popup menu, and selecting **Duplicate**.</span></span>

    <span data-ttu-id="1079c-233">將 cube 平均隔開。</span><span class="sxs-lookup"><span data-stu-id="1079c-233">Space the cubes out evenly.</span></span> <span data-ttu-id="1079c-234">您的場景看起來應該如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1079c-234">Your scene should look similar to the image below.</span></span>

10. <span data-ttu-id="1079c-235">按住 CTRL 鍵，同時選取 [階層] 面板中的每個**Cube**物件，以將 MoveWithPan 腳本新增至所有 cube。</span><span class="sxs-lookup"><span data-stu-id="1079c-235">Add the MoveWithPan script to all the cubes by holding down the CTRL key while selecting each **Cube** object in the Hierarchy panel.</span></span> <span data-ttu-id="1079c-236">在 [偵測器] 面板中，按一下 [加入元件]，然後搜尋並選取 [**使用平移腳本移動**]，將它新增至所有 cube。</span><span class="sxs-lookup"><span data-stu-id="1079c-236">In the Inspector panel, click Add Component, and search for and select the **Move With Pan** script to add it to all the cubes.</span></span>

    ![mrlearning-base-ch5-2-step10a .png](images/mrlearning-base-ch5-2-step10a.png)

    >[!NOTE]
    ><span data-ttu-id="1079c-238">MoveWithPan 腳本不是 MRTK 的一部分，而是包含在上一課匯入的 BaseModuleAssets 資產中。</span><span class="sxs-lookup"><span data-stu-id="1079c-238">The MoveWithPan script is not part of MRTK but included with the BaseModuleAssets asset imported in the previous lesson.</span></span>

    <span data-ttu-id="1079c-239">在仍選取 cube 的情況下，將**四**個物件從 [階層] 面板拖曳至 [**移動流覽**腳本] 元件的 [**平移輸入來源**] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="1079c-239">With the cubes still selected, drag the **Quad** object from the Hierarchy panel into the **Pan Input Source** field of the **Move With Pan** script component.</span></span>

    ![mrlearning-base-ch5-2-step10b .png](images/mrlearning-base-ch5-2-step10b.png)

    <span data-ttu-id="1079c-241">現在，cube 會隨著您的移動流覽手勢移動。</span><span class="sxs-lookup"><span data-stu-id="1079c-241">Now, the cubes will move with your pan gesture.</span></span>

    >[!TIP]
    ><span data-ttu-id="1079c-242">每個 cube 上的 MoveWithPan 實例會接聽四個物件上的 HandInteractionPanZoom 實例所傳送的 PanUpdated 事件，我們已新增至每個 cube 上的 [移動流覽輸入來源] 欄位，並據以更新個別 cube 物件的位置。</span><span class="sxs-lookup"><span data-stu-id="1079c-242">The MoveWithPan instance on each cube listens for the PanUpdated event sent from the HandInteractionPanZoom instance on the Quad object, that we added to the Pan Input Source field on each of the cubes, and updates the respective cube object's position accordingly.</span></span>

    <span data-ttu-id="1079c-243">在仍選取 cube 的情況下，將它們沿著 Z 軸向後移動，讓每個 cube 的網格都在**四**個方塊的**碰撞**器內，方法是將其**位置 Z**值變更為_0.7_。</span><span class="sxs-lookup"><span data-stu-id="1079c-243">With the cubes still selected, move them forward along their Z axis so each cube's mesh is inside the **Quad**'s **Box Collider** by changing their **Position Z** values to _0.7_.</span></span>

    ![mrlearning-base-ch5-2-step10c .png](images/mrlearning-base-ch5-2-step10c.png)

    <span data-ttu-id="1079c-245">現在，如果您在 [偵測器] 面板中取消核取，以停用**四**個**網格**轉譯器元件，您將會有一個不可見的四個，您可以在其中流覽3d 物件清單。</span><span class="sxs-lookup"><span data-stu-id="1079c-245">Now, if you disable the **Quad**'s **Mesh Renderer** component by un-checking it in the Inspector panel, you will have an invisible quad where you can pan through a list of 3D objects.</span></span>

    ![mrlearning-base-ch5-2-step10d .png](images/mrlearning-base-ch5-2-step10d.png)

## <a name="eye-tracking"></a><span data-ttu-id="1079c-247">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="1079c-247">Eye Tracking</span></span>

<span data-ttu-id="1079c-248">在本節中，我們將探討如何在我們的示範中啟用眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="1079c-248">In this section, we will explore how to enable eye tracking in our demo.</span></span> <span data-ttu-id="1079c-249">當您的眼睛 gazed 時，我們會慢慢旋轉3D 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="1079c-249">We will slowly spin our 3D menu items when they are being gazed upon with your eye gaze.</span></span> <span data-ttu-id="1079c-250">當選取注視項目時，我們也會觸發有趣的效果。</span><span class="sxs-lookup"><span data-stu-id="1079c-250">We will also trigger a fun effect when the gazed-upon item is selected.</span></span>

1. <span data-ttu-id="1079c-251">請確定已正確設定 MRTK 設定檔以進行眼追蹤。</span><span class="sxs-lookup"><span data-stu-id="1079c-251">Ensure the MRTK profiles are properly configured for eye tracking.</span></span> <span data-ttu-id="1079c-252">若要這麼做，請移至[MRTK 指示中的開始使用眼睛追蹤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)，並查看[設定眼追蹤逐步](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step)執行一節中的步驟，確認是否已正確設定眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="1079c-252">To do this, go to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions and verify that eye tracking is properly configured by reviewing the steps in the [Setting up eye tracking step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) section.</span></span> <span data-ttu-id="1079c-253">完成檔中剩餘的步驟。</span><span class="sxs-lookup"><span data-stu-id="1079c-253">Complete any remaining steps in the documentation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="1079c-254">如果您使用 DefaultHoloLens2InputSystemProfile （如[設定混合現實工具](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit)組課程中所述）來複製您的自訂 MRTK 設定設定檔，則依預設會在 unity 專案中啟用監看追蹤，但您仍然必須設定 unity 編輯器的眼睛追蹤模擬，並設定 Visual Studio 以允許組建的眼追蹤。</span><span class="sxs-lookup"><span data-stu-id="1079c-254">If you used the DefaultHoloLens2InputSystemProfile, as instructed in the [Configure the Mixed Reality Toolkit](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) lesson, to clone your custom MRTK configuration profile, eye tracking is enabled by default in the Unity project but you will still have to set up eye tracking simulation for the Unity editor and configure Visual Studio to allow eye tracking for the build.</span></span>

    <span data-ttu-id="1079c-255">上述連結提供下列事項的簡短指示：</span><span class="sxs-lookup"><span data-stu-id="1079c-255">The link above provides brief instructions for:</span></span>

    - <span data-ttu-id="1079c-256">建立要在 MRTK 設定檔中使用的 Windows Mixed Reality 眼注視 Data Provider</span><span class="sxs-lookup"><span data-stu-id="1079c-256">Creating the Windows Mixed Reality Eye Gaze Data Provider for use in the MRTK profile</span></span>
    - <span data-ttu-id="1079c-257">在連接至相機的注視提供者中啟用眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="1079c-257">Enabling eye tracking in the Gaze Provider attached to the camera</span></span>
    - <span data-ttu-id="1079c-258">在 Unity 編輯器中設定眼睛追蹤模擬</span><span class="sxs-lookup"><span data-stu-id="1079c-258">Setting up an eye tracking simulation in the Unity editor</span></span>
    - <span data-ttu-id="1079c-259">編輯 Visual Studio 解決方案的功能，以允許在建置的應用程式中進行眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="1079c-259">Editing the Visual Studio solution's capabilities to allow eye tracking in the built application</span></span>

2. <span data-ttu-id="1079c-260">將眼球追蹤目標元件新增至目標物件。</span><span class="sxs-lookup"><span data-stu-id="1079c-260">Add the Eye Tracking Target component to target objects.</span></span> <span data-ttu-id="1079c-261">若要讓物件回應眼睛眼事件，我們必須在每個想要使用眼睛互動的物件上新增 EyeTrackingTarget 元件。</span><span class="sxs-lookup"><span data-stu-id="1079c-261">To allow an object to respond to eye gaze events, we'll need to add the EyeTrackingTarget component on each object that we want to interact with by using eye gaze.</span></span> <span data-ttu-id="1079c-262">將此元件新增至作為方格集合一部分之九個 3D 物件中的每一個。</span><span class="sxs-lookup"><span data-stu-id="1079c-262">Add this component to each of the nine 3D objects that are part of the grid collection.</span></span>

    >[!TIP]
    ><span data-ttu-id="1079c-263">您可以使用 Shift 和/或 CRTL 鍵選取階層中的多個專案，然後大量新增 EyeTrackingTarget 元件。</span><span class="sxs-lookup"><span data-stu-id="1079c-263">You can use the Shift and/or CRTL keys to select multiple items in the Hierarchy and then bulk-add the EyeTrackingTarget component.</span></span>

    ![Lesson5 Chapter3 步驟2](images/Lesson5Chapter3Step2.JPG)

3. <span data-ttu-id="1079c-265">接下來，我們會新增 EyeTrackingTutorialDemo 腳本來進行一些令人興奮的互動。</span><span class="sxs-lookup"><span data-stu-id="1079c-265">Next, we will add the EyeTrackingTutorialDemo script for some exciting interactions.</span></span> <span data-ttu-id="1079c-266">針對方格集合中的每個3D 物件，藉由在 [加入元件] 功能表中搜尋元件來新增 EyeTrackingTutorialDemo 腳本。</span><span class="sxs-lookup"><span data-stu-id="1079c-266">For each 3D object in the grid collection, add the EyeTrackingTutorialDemo script by searching for the component in the Add Component menu.</span></span>

    ![Lesson5 Chapter3 步驟3](images/Lesson5Chapter3Step3.JPG)

    >[!NOTE]
    ><span data-ttu-id="1079c-268">EyeTrackingTutorialDemo 腳本資料不是 MRTK 的一部分，而是包含在上一課匯入的 BaseModuleAssets 資產中。</span><span class="sxs-lookup"><span data-stu-id="1079c-268">The EyeTrackingTutorialDemo script material is not part of MRTK but included with the BaseModuleAssets asset imported in the previous lesson.</span></span>

4. <span data-ttu-id="1079c-269">在注視目標時旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="1079c-269">Spin the object while looking at the target.</span></span> <span data-ttu-id="1079c-270">我們想要設定我們的3D 物件，以在我們查看時旋轉。</span><span class="sxs-lookup"><span data-stu-id="1079c-270">We want to configure our 3D objects to spin while we are looking at them.</span></span> <span data-ttu-id="1079c-271">若要這麼做，請在查看 EyeTrackingTarget 元件的 Target （）區段時，在中插入新的欄位，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1079c-271">To do this, insert a new field in the While Looking At Target() section of the EyeTrackingTarget component, as shown in the image below.</span></span>

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    <span data-ttu-id="1079c-273">在新建立的欄位中，將目前的遊戲物件新增至空白欄位，然後選取 [EyeTrackingTutorialDemo > RotateTarget （）]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1079c-273">In the newly-created field, add the current Game Object to the empty field, and select EyeTrackingTutorialDemo>RotateTarget(), as shown in the image below.</span></span> <span data-ttu-id="1079c-274">現在，3D 物件被設定為在透過眼球追蹤注視時旋轉。</span><span class="sxs-lookup"><span data-stu-id="1079c-274">Now the 3D object is configured to spin when it is being gazed upon with eye tracking.</span></span>

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. <span data-ttu-id="1079c-276">加入「中斷目標」的功能，這是以點按方式選取，或說出「select」時所 gazed 的。</span><span class="sxs-lookup"><span data-stu-id="1079c-276">Add in the ability to “blip target” that is being gazed at upon select by air-tap or saying “select”.</span></span> <span data-ttu-id="1079c-277">與步驟4類似，我們想要藉由將 EyeTrackingTutorialDemo 指派給 EyeTrackingTarget 元件的遊戲物件的 Select （）欄位來觸發 > BlipTarget （），如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1079c-277">Similar to Step 4, we want to trigger EyeTrackingTutorialDemo>BlipTarget() by assigning it to the game object’s Select() field of the EyeTrackingTarget component, as shown in the figure below.</span></span> <span data-ttu-id="1079c-278">現在設定完成後，每當您觸發選取動作（例如，按下點或語音命令「選取」）時，就會注意到遊戲物件有些許中斷。</span><span class="sxs-lookup"><span data-stu-id="1079c-278">With this now configured, you will notice a slight blip in the game object whenever you trigger a select action, such as air-tap or the voice command “select”.</span></span>

    ![Lesson5 Chapter3 步驟5](images/Lesson5Chapter3Step5.JPG)

6. <span data-ttu-id="1079c-280">在建置 HoloLens 2 之前，請確定已正確設定眼球追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="1079c-280">Ensure eye tracking capabilities are properly configured before building to HoloLens 2.</span></span> <span data-ttu-id="1079c-281">在撰寫本文時，Unity 尚未能夠設定眼追蹤功能的注視輸入。</span><span class="sxs-lookup"><span data-stu-id="1079c-281">As of this writing, Unity does not yet have the ability to set the gaze input for eye tracking capabilities.</span></span> <span data-ttu-id="1079c-282">需要設定這項功能，眼睛追蹤才能在 HoloLens 2 中工作。</span><span class="sxs-lookup"><span data-stu-id="1079c-282">Setting this capability is required for eye tracking to work in HoloLens 2.</span></span> <span data-ttu-id="1079c-283">請遵循在[HoloLens 2 上測試 Unity 應用程式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)的指示，以啟用注視輸入功能。</span><span class="sxs-lookup"><span data-stu-id="1079c-283">Follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions to enable the gaze input capability.</span></span>

## <a name="congratulations"></a><span data-ttu-id="1079c-284">恭喜您</span><span class="sxs-lookup"><span data-stu-id="1079c-284">Congratulations</span></span>

<span data-ttu-id="1079c-285">您已成功將基本眼追蹤功能新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1079c-285">You’ve successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="1079c-286">這些動作只是眼球追蹤功能無限可能性的開端。</span><span class="sxs-lookup"><span data-stu-id="1079c-286">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="1079c-287">本章也會在第5課結束，我們已瞭解先進的輸入功能，例如語音命令、移動流覽手勢和眼追蹤。</span><span class="sxs-lookup"><span data-stu-id="1079c-287">This chapter also concludes Lesson 5, where we learned about advanced input functionality, such as voice commands, panning gestures, and eye tracking.</span></span>

[<span data-ttu-id="1079c-288">下一課： 7. 建立農曆模組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="1079c-288">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
