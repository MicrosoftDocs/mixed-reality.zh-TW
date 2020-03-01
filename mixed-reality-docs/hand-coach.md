---
title: 手動教練
description: 當系統偵測不到使用者的手協助時，所觸發的3D 手。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、手勢、沉浸式耳機、MRTK、手中的協助
ms.openlocfilehash: c5f0a0c241ff71dc93f370a5a8caa627128bfb1a
ms.sourcegitcommit: 1ec628a9107194c0a9d4073b5ca09ee816030e85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2020
ms.locfileid: "78202731"
---
# <a name="hand-coach"></a><span data-ttu-id="179f4-104">手動教練</span><span class="sxs-lookup"><span data-stu-id="179f4-104">Hand coach</span></span>

<span data-ttu-id="179f4-105">「手動操作」是一種3D 模型化的手，會在系統未偵測到使用者手時觸發。</span><span class="sxs-lookup"><span data-stu-id="179f4-105">Hand coach is 3D modeled hands that are triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="179f4-106">這會實作為「教學」元件，可在未教授手勢時協助引導使用者。</span><span class="sxs-lookup"><span data-stu-id="179f4-106">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="179f4-107">如果使用者尚未針對某個時間執行指定的手勢，則手會以延遲方式迴圈。</span><span class="sxs-lookup"><span data-stu-id="179f4-107">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="179f4-108">右手教練可用來代表按下按鈕或挑選全像投影。</span><span class="sxs-lookup"><span data-stu-id="179f4-108">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  


<span data-ttu-id="179f4-109">![範例：手動操作](images/HandCoach/MRTK_handCoach.jpg)</span><span class="sxs-lookup"><span data-stu-id="179f4-109">![Example: Hand coach](images/HandCoach/MRTK_handCoach.jpg)</span></span><br>
<span data-ttu-id="179f4-110">*MRTK 的 HandCoach 範例*</span><span class="sxs-lookup"><span data-stu-id="179f4-110">*HandCoach Example from MRTK*</span></span>

## <a name="hand-coach-provided"></a><span data-ttu-id="179f4-111">提供的手形指導</span><span class="sxs-lookup"><span data-stu-id="179f4-111">Hand coach provided</span></span>

<span data-ttu-id="179f4-112">目前的互動模型代表各種手勢控制項，例如 [滾動]、[遠選] 和 [近碰點]。</span><span class="sxs-lookup"><span data-stu-id="179f4-112">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="179f4-113">以下是<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets">MRTK</a>中所提供之現有右手手勢的完整清單：</span><span class="sxs-lookup"><span data-stu-id="179f4-113">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="179f4-114">接近的 Select](images/HandCoach/NearSelect.gif) ![範例</span><span class="sxs-lookup"><span data-stu-id="179f4-114">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="179f4-115">**接近選取使用方式的範例示範如何選取按鈕或關閉可互動物件**</span><span class="sxs-lookup"><span data-stu-id="179f4-115">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="179f4-116">![的空中點](images/HandCoach/AirTap.gif) 範例</span><span class="sxs-lookup"><span data-stu-id="179f4-116">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="179f4-117">**點一下的範例-用來示範如何選取距離最遠的物件**</span><span class="sxs-lookup"><span data-stu-id="179f4-117">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="179f4-118">![移動](images/HandCoach/Move.gif) 的範例</span><span class="sxs-lookup"><span data-stu-id="179f4-118">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="179f4-119">**在空間中移動物件的範例-用來示範如何在空間中移動全息影像**</span><span class="sxs-lookup"><span data-stu-id="179f4-119">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="179f4-120">![旋轉](images/HandCoach/Rotate.gif) 的範例</span><span class="sxs-lookup"><span data-stu-id="179f4-120">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="179f4-121">**旋轉範例-用來示範如何旋轉全息影像或物件**</span><span class="sxs-lookup"><span data-stu-id="179f4-121">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="179f4-122">![Scale](images/HandCoach/Scale.gif) 範例</span><span class="sxs-lookup"><span data-stu-id="179f4-122">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="179f4-123">**縮放的範例，用來顯示如何操作全像更大的全息影像**</span><span class="sxs-lookup"><span data-stu-id="179f4-123">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="179f4-124">![的 Palm](images/HandCoach/PalmUp.gif) 範例</span><span class="sxs-lookup"><span data-stu-id="179f4-124">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="179f4-125">**掌上-建議使用的範例，以顯示功能表**</span><span class="sxs-lookup"><span data-stu-id="179f4-125">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="179f4-126">HandFlip](images/HandCoach/HandFlip.gif) ![範例</span><span class="sxs-lookup"><span data-stu-id="179f4-126">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="179f4-127">**右手手勢範例–另一種顯示功能表的方式**</span><span class="sxs-lookup"><span data-stu-id="179f4-127">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="179f4-128">![Scroll](images/HandCoach/Scoll.gif) 的範例</span><span class="sxs-lookup"><span data-stu-id="179f4-128">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="179f4-129">**Scroll 範例-用於滾動清單或長檔**</span><span class="sxs-lookup"><span data-stu-id="179f4-129">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="179f4-130">設計概念</span><span class="sxs-lookup"><span data-stu-id="179f4-130">Design concepts</span></span>

<span data-ttu-id="179f4-131">針對 Hololens2，我們設計了根據本能和自然手勢的手動互動。</span><span class="sxs-lookup"><span data-stu-id="179f4-131">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="179f4-132">我們相信大部分使用者都可以直覺化，因此不會建立專用的手勢學習。</span><span class="sxs-lookup"><span data-stu-id="179f4-132">We believe these to be intuitive to most users and thus did not create dedicated gesture learning moments.</span></span> <span data-ttu-id="179f4-133">相反地，我們建立了手勢來協助可能停滯或不熟悉與全息影像互動的使用者瞭解這些手勢。</span><span class="sxs-lookup"><span data-stu-id="179f4-133">Instead, we created the hand coach to help users who might get stuck or are unfamiliar with interacting with holograms learn about these gestures.</span></span> <span data-ttu-id="179f4-134">如果沒有學習時間，我們覺得顯示使用者如何藉由示範來執行動作，是最佳選項。</span><span class="sxs-lookup"><span data-stu-id="179f4-134">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="179f4-135">在我們的研究中，我們發現使用者能夠找出手勢，但需要一些指引。</span><span class="sxs-lookup"><span data-stu-id="179f4-135">In our studies, we found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="179f4-136">如果我們偵測到使用者沒有與某個期間的物件互動，就會觸發右手的指示來示範正確的手和手指位置。</span><span class="sxs-lookup"><span data-stu-id="179f4-136">If we detect that a user does not interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="179f4-137">基本</span><span class="sxs-lookup"><span data-stu-id="179f4-137">Intuitive</span></span>

<span data-ttu-id="179f4-138">以動畫顯示時，應該很明顯，而且 shoudn't 會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="179f4-138">When animating hands, it should be obvious and shoudn't cause any confusion.</span></span> <span data-ttu-id="179f4-139">手的動畫表示您嘗試呼叫給使用者的手勢，以瞭解其用途。</span><span class="sxs-lookup"><span data-stu-id="179f4-139">The animation of the hands is a representation of the gesture your trying to evoke to the user to understand it's purpose.</span></span> 

<span data-ttu-id="179f4-140">例如，如果您希望使用者按下按鈕，就會觸發按下按鈕的手。</span><span class="sxs-lookup"><span data-stu-id="179f4-140">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="179f4-141">![範例：靠近點一下的手勢](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="179f4-141">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="179f4-142">*示範近乎點擊 Gem 的手勢*</span><span class="sxs-lookup"><span data-stu-id="179f4-142">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="179f4-143">右手小</span><span class="sxs-lookup"><span data-stu-id="179f4-143">Hand scale</span></span>

<span data-ttu-id="179f4-144">我們使用 UI 功能表測試了各種不同的大小，並覺得如果手中真的要調整大小，就會有 menacing 的感受，但如果太小，則很難查看並瞭解手勢。</span><span class="sxs-lookup"><span data-stu-id="179f4-144">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling but if they were too small then it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="179f4-145">**聲音和手**</span><span class="sxs-lookup"><span data-stu-id="179f4-145">**Voice over and hands**</span></span>

<span data-ttu-id="179f4-146">不預期使用者可以透過 voice 接聽一組指示，並透過手動指示觀看不同的指示。</span><span class="sxs-lookup"><span data-stu-id="179f4-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="179f4-147">排序您的指示，協助使用者專注于競爭，以減少感應式多載。</span><span class="sxs-lookup"><span data-stu-id="179f4-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="179f4-148">我可以建立自己的嗎？</span><span class="sxs-lookup"><span data-stu-id="179f4-148">Can I create my own?</span></span>

<span data-ttu-id="179f4-149">是的！</span><span class="sxs-lookup"><span data-stu-id="179f4-149">Yes!</span></span> <span data-ttu-id="179f4-150">我們鼓勵您為遊戲建立自己獨特的手勢，並向您貢獻給此社區！</span><span class="sxs-lookup"><span data-stu-id="179f4-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="179f4-151">我們提供了 Rigged 手的 Maya 檔案，可用於您的應用程式，您可以從這裡下載：<a href="files/HandCoach_MRTK.zip">下載 HandCoach_MRTK .zip</a></span><span class="sxs-lookup"><span data-stu-id="179f4-151">We have provided a Maya file of a Rigged hand that can be used for your app which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip</a></span></span>

<span data-ttu-id="179f4-152">Maya](images/HandCoach/MayaSelect_Gif.gif) 的動畫 ![範例</span><span class="sxs-lookup"><span data-stu-id="179f4-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="179f4-153">*Maya 中的動畫手勢刺探的範例*</span><span class="sxs-lookup"><span data-stu-id="179f4-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="179f4-154">**建議的 authoring tool**</span><span class="sxs-lookup"><span data-stu-id="179f4-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="179f4-155">在3D 演出者之間，許多選擇使用[Autodesk 的 Maya，其本身能夠使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)來轉換資產的建立方式。</span><span class="sxs-lookup"><span data-stu-id="179f4-155">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="179f4-156">提供的實習檔案是 Maya 二進位檔案，因此建議使用 Maya 來建立動畫並匯出手。</span><span class="sxs-lookup"><span data-stu-id="179f4-156">The hands file provided is a Maya Binary File, so it is recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="179f4-157">如果您想要使用另一個3D 程式，以下是<b>。FBX</b>：<a href="files/HandCoachMRTK_FBX.zip">下載 HandCoachMRTK_FBX .zip</a> ，以建立您自己的控制器設定。</span><span class="sxs-lookup"><span data-stu-id="179f4-157">If you prefer to use another 3D program, here is a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">           Download HandCoachMRTK_FBX.zip</a> to create your own controller setup.</span></span> 

<span data-ttu-id="179f4-158">如果使用提供的可下載 maya 手檔案，建議您將 unity 中的手向下延展至0.6。</span><span class="sxs-lookup"><span data-stu-id="179f4-158">If using the downloadable maya Hand File provided, it is suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="179f4-159">![範例： Maya 中的手動教練 rig](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="179f4-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="179f4-160">*Rigged 手*</span><span class="sxs-lookup"><span data-stu-id="179f4-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="179f4-161">技術規格</span><span class="sxs-lookup"><span data-stu-id="179f4-161">Technical Specs</span></span>

*   <span data-ttu-id="179f4-162">有兩個檔案是以 Maya Ascii 格式提供</span><span class="sxs-lookup"><span data-stu-id="179f4-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="179f4-163">右方和左側提供 Maya 二進位格式</span><span class="sxs-lookup"><span data-stu-id="179f4-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="179f4-164">將您的 Maya 檔案設定為 24 FPS</span><span class="sxs-lookup"><span data-stu-id="179f4-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="179f4-165">在檔案中，有左右的右手邊，可用於兩個右手式或單一右手手勢。</span><span class="sxs-lookup"><span data-stu-id="179f4-165">Within the file, there is a left and right hand which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="179f4-166">預設只會顯示右手邊。</span><span class="sxs-lookup"><span data-stu-id="179f4-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="179f4-167">建議在開頭和結尾保留大約10個畫面的緩衝區以淡化</span><span class="sxs-lookup"><span data-stu-id="179f4-167">It is suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="179f4-168">如果以指定的目標建立物件的動畫，其最佳作法是以動畫顯示預設方塊或 Null。</span><span class="sxs-lookup"><span data-stu-id="179f4-168">If animating a object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="179f4-169">如果手以動畫顯示實體物件（例如方塊），其最佳做法是不要在 Maya 中建立轉譯的動畫，而是在 Unity 或程式碼中等待以動畫顯示。</span><span class="sxs-lookup"><span data-stu-id="179f4-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="179f4-170">可見的動畫應為1.5 秒，才能傳達有意義的資訊</span><span class="sxs-lookup"><span data-stu-id="179f4-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="179f4-171">當您感到滿意動畫時：</span><span class="sxs-lookup"><span data-stu-id="179f4-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="179f4-172">選取所有接點並製作主要畫面格</span><span class="sxs-lookup"><span data-stu-id="179f4-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="179f4-173">刪除控制器，選取接點和網格並匯出為 FBX</span><span class="sxs-lookup"><span data-stu-id="179f4-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="179f4-174">如果有多個動畫，您可以使用 Maya 的內建遊戲匯出工具： https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="179f4-174">If there are Multiple Animations, you can use Maya’s built in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="179f4-175">從 Maya 匯出</span><span class="sxs-lookup"><span data-stu-id="179f4-175">Exporting from Maya</span></span>

<span data-ttu-id="179f4-176">在您滿意動畫之後</span><span class="sxs-lookup"><span data-stu-id="179f4-176">After you are satisfied with your animation</span></span>
* <span data-ttu-id="179f4-177">選取所有接點：選取 > 階層</span><span class="sxs-lookup"><span data-stu-id="179f4-177">Select all joints: Select > Hierarchy</span></span>

     ![範例：功能表位置](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="179f4-179">製作動畫：切換至動畫 > 鍵 > 製作動畫</span><span class="sxs-lookup"><span data-stu-id="179f4-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![範例：功能表位置](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="179f4-181">刪除控制器 Rig： Outliner > MainR_Grp 或 MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="179f4-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![範例：功能表位置](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="179f4-183">匯出為 FBX：選取 .JNT + 網格：檔案 > 匯出選取專案（選項框） > 匯出選取專案</span><span class="sxs-lookup"><span data-stu-id="179f4-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![範例：功能表位置](images/HandCoach/OptionBox.png)<br>

     ![範例：功能表位置](images/HandCoach/SelectionExport.png)<br>

     ![範例：功能表位置](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="179f4-187">當匯出為 FBX 並帶入 Unity 時，請將其向下調整為0.6。</span><span class="sxs-lookup"><span data-stu-id="179f4-187">When exporting as a FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="179f4-188">我們發現這是顯示手的完美平衡。</span><span class="sxs-lookup"><span data-stu-id="179f4-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="179f4-189">![範例： Unity 設定](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="179f4-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="179f4-190">*在 MRTK 中找到 HandCoach_R prefab 的 Unity 設定*</span><span class="sxs-lookup"><span data-stu-id="179f4-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="179f4-191">實作為 Unity 專案的實際執行</span><span class="sxs-lookup"><span data-stu-id="179f4-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="179f4-192">最佳作法</span><span class="sxs-lookup"><span data-stu-id="179f4-192">Best practices</span></span>
*    <span data-ttu-id="179f4-193">建議您將 unity 中的手擴充至0。6</span><span class="sxs-lookup"><span data-stu-id="179f4-193">It is suggested to scale down the hands in unity to 0.6</span></span>
*   <span data-ttu-id="179f4-194">應播放兩次手，如果未完成，則會持續迴圈直到手勢完成為止。</span><span class="sxs-lookup"><span data-stu-id="179f4-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="179f4-195">應該將手迴圈兩次，以確保使用者有時間註冊並查看手勢。</span><span class="sxs-lookup"><span data-stu-id="179f4-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="179f4-196">手應該在迴圈之間淡入和移出。</span><span class="sxs-lookup"><span data-stu-id="179f4-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="179f4-197">如果 HL2 攝影機看得到使用者的手，但是使用者不會執行所需的互動，則手會在10秒後出現。</span><span class="sxs-lookup"><span data-stu-id="179f4-197">If user’s hands are visible by HL2 cameras but users are not doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="179f4-198">如果 HL2 攝影機看不到使用者的手，則手會在5秒後出現。</span><span class="sxs-lookup"><span data-stu-id="179f4-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="179f4-199">如果動畫中間的 HL2 攝影機會以明顯的方式追蹤使用者的手，動畫將會完成並淡出。</span><span class="sxs-lookup"><span data-stu-id="179f4-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="179f4-200">如果您要包含 voice，建議您將它對應到手的手勢。</span><span class="sxs-lookup"><span data-stu-id="179f4-200">If you are including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="179f4-201">如果您至少已教授過一次，只會在偵測到使用者停滯時，才重複手勢。</span><span class="sxs-lookup"><span data-stu-id="179f4-201">If you have taught the hands at least once, only repeat the gesture if its detected that the user is stuck.</span></span>
*   <span data-ttu-id="179f4-202">如果特定手指/手位置非常重要，請確保使用者可以清楚地在動畫中看到這些細節。</span><span class="sxs-lookup"><span data-stu-id="179f4-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="179f4-203">試著 angling 手，讓最重要的部分清楚可見。</span><span class="sxs-lookup"><span data-stu-id="179f4-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="179f4-204">如果您注意到手上的失真，您需要移至 Unity 的品質設定，以增加骨骼的數量。</span><span class="sxs-lookup"><span data-stu-id="179f4-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the amount of bones.</span></span> 
 <span data-ttu-id="179f4-205">前往 Unity 的編輯 > 專案設定 > 品質 > 其他 > Blend 權數。</span><span class="sxs-lookup"><span data-stu-id="179f4-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="179f4-206">請確定已選取 [4 個骨骼]，以查看平滑接點。</span><span class="sxs-lookup"><span data-stu-id="179f4-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![範例：功能表位置](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a><span data-ttu-id="179f4-208">應避免的事項</span><span class="sxs-lookup"><span data-stu-id="179f4-208">What to avoid</span></span>
* <span data-ttu-id="179f4-209">調整太大的手</span><span class="sxs-lookup"><span data-stu-id="179f4-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="179f4-210">將手放在靠近使用者的附近</span><span class="sxs-lookup"><span data-stu-id="179f4-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="179f4-211">手上應該只教授一次。</span><span class="sxs-lookup"><span data-stu-id="179f4-211">Hands should only be taught once.</span></span> <span data-ttu-id="179f4-212">透過教學可能會造成混淆和 messiness</span><span class="sxs-lookup"><span data-stu-id="179f4-212">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="179f4-213">將它帶入 Unity，請在這裡下載最新的 MRTK： https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="179f4-213">Bringing it into Unity, please download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="179f4-214">材質： Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="179f4-214">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="179f4-215">腳本：請參閱<a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">MRTK 手勢指導</a>的 MRTK 指導方針</span><span class="sxs-lookup"><span data-stu-id="179f4-215">Scripts: Refer to MRTK guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="179f4-216">每個專案的設定</span><span class="sxs-lookup"><span data-stu-id="179f4-216">Per- project setting</span></span>
        *   <span data-ttu-id="179f4-217">場景設定為 UWP：指示可在適用于 Windows Mixed Reality 的[Configure Unity 專案](Configure-Unity-Project.md)中找到</span><span class="sxs-lookup"><span data-stu-id="179f4-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="179f4-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="179f4-218">See also</span></span>
* [<span data-ttu-id="179f4-219">互動-基本概念</span><span class="sxs-lookup"><span data-stu-id="179f4-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="179f4-220">資產建立流程</span><span class="sxs-lookup"><span data-stu-id="179f4-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="179f4-221">筆勢</span><span class="sxs-lookup"><span data-stu-id="179f4-221">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="179f4-222">安裝工具</span><span class="sxs-lookup"><span data-stu-id="179f4-222">Install the Tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="179f4-223">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="179f4-223">Configure Unity Project</span></span>](Configure-Unity-Project.md)
* [<span data-ttu-id="179f4-224">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="179f4-224">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="179f4-225">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="179f4-225">MRTK 101</span></span>](mrtk-101.md)
