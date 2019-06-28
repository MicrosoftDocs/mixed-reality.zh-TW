---
title: MR 學習 ASA 模組上 HoloLens 2 Azure 空間的錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: c120d22f955d366042bbcb9ac73eaa4f13dc20e9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415275"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a><span data-ttu-id="098e4-104">開始使用 Azure HoloLens 2 上的空間錨點</span><span class="sxs-lookup"><span data-stu-id="098e4-104">Getting started with Azure Spatial Anchors on HoloLens 2</span></span>

<span data-ttu-id="098e4-105">歡迎來到 HoloLens 2 教學課程的第二個模組。</span><span class="sxs-lookup"><span data-stu-id="098e4-105">Welcome to the second module of the HoloLens 2 Tutorial.</span></span> <span data-ttu-id="098e4-106">開始之前，務必讓所有的[必要條件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)完成。</span><span class="sxs-lookup"><span data-stu-id="098e4-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="098e4-107">如果您尚未完成第一個[基底模組](mrlearning-base.md)，建議您先完成該模組。</span><span class="sxs-lookup"><span data-stu-id="098e4-107">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="098e4-108">如果您從新的 Unity 專案，請依照下列中的新專案建立步驟[基底模組](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="098e4-108">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="098e4-109">目標</span><span class="sxs-lookup"><span data-stu-id="098e4-109">Objectives</span></span>

* <span data-ttu-id="098e4-110">了解使用 Azure 空間的錨點標記 HoloLens 2 開發基礎</span><span class="sxs-lookup"><span data-stu-id="098e4-110">Learn the fundamentals of developing with Azure Spatial Anchors with the HoloLens 2</span></span>

* <span data-ttu-id="098e4-111">建立、 上傳，並下載空間的錨點</span><span class="sxs-lookup"><span data-stu-id="098e4-111">Create, Upload, and Download Spatial Anchors</span></span>

  

## <a name="instructions"></a><span data-ttu-id="098e4-112">指示</span><span class="sxs-lookup"><span data-stu-id="098e4-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="098e4-113">下載和匯入資產</span><span class="sxs-lookup"><span data-stu-id="098e4-113">Downloading and importing assets</span></span>
<span data-ttu-id="098e4-114">在開始之前，請下載並匯入下列資產：</span><span class="sxs-lookup"><span data-stu-id="098e4-114">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="098e4-115">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="098e4-115">Azure Spatial Anchors</span></span>](https://github.com/azure/azure-spatial-anchors-samples/releases)

[<span data-ttu-id="098e4-116">MR 基底模組資產套件</span><span class="sxs-lookup"><span data-stu-id="098e4-116">MR Base module Asset Pack</span></span>](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[<span data-ttu-id="098e4-117">ASA 模組資產套件</span><span class="sxs-lookup"><span data-stu-id="098e4-117">ASA module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[<span data-ttu-id="098e4-118">混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="098e4-118">Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> <span data-ttu-id="098e4-119">注意:如需有關如何匯入 Azure 空間的錨點，如需 MR 基底模組資產套件特定指示的步驟 6 和步驟 3 到 4 的特殊指示上混合實境工具組 (MRKT) 中的特定指示，請參閱步驟 5。</span><span class="sxs-lookup"><span data-stu-id="098e4-119">Note: See Step 5 for specific instructions on how to import Azure Spatial Anchors, Step 6 for specific instructions on the MR Base module Asset Pack, and steps 3 through 4 for specific instructions on the Mixed Reality Toolkit (MRKT).</span></span>

1. <span data-ttu-id="098e4-120">在專案中建立新的場景。</span><span class="sxs-lookup"><span data-stu-id="098e4-120">Create a new scene in your project.</span></span> <span data-ttu-id="098e4-121">以滑鼠右鍵按一下您的場景資料夾，按一下 [建立]，然後場景。</span><span class="sxs-lookup"><span data-stu-id="098e4-121">Right click your Scene folder, click "Create," then Scene.</span></span> <span data-ttu-id="098e4-122">命名新的場景 ASALearningmodule。</span><span class="sxs-lookup"><span data-stu-id="098e4-122">Name the new scene ASALearningmodule.</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="098e4-124">按兩下 ASALearningmodule 查看一些預先定義的項目，以及新的場景會出現。</span><span class="sxs-lookup"><span data-stu-id="098e4-124">Double click ASALearningmodule to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="098e4-125">設定適用於混合的實境開發場景。</span><span class="sxs-lookup"><span data-stu-id="098e4-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="098e4-127">注意:您會看到快顯視窗，指出: 「 您必須選擇檔案的混合實境工具組 」。</span><span class="sxs-lookup"><span data-stu-id="098e4-127">Note: You will see a pop-up that says, "You must choose a file for the Mixed Reality Toolkit."</span></span> <span data-ttu-id="098e4-128">按一下 [確定] 將帶您前往步驟 4。</span><span class="sxs-lookup"><span data-stu-id="098e4-128">Clicking Ok brings you to Step 4.</span></span>

4. <span data-ttu-id="098e4-129">當選擇 MRTK 檔案，選取，DefaultMixedRealityToolkitConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="098e4-129">When choosing a file for the MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.</span></span>

   > <span data-ttu-id="098e4-130">注意:如果您有自己的組態設定檔，請放心，改為使用。</span><span class="sxs-lookup"><span data-stu-id="098e4-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="098e4-132">混合實境現在設定場景。</span><span class="sxs-lookup"><span data-stu-id="098e4-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="098e4-133">請確定您將場景 (使用其中一個控制項執行此作業 / 命令 + S 或按一下檔案，然後按一下 於儲存)。</span><span class="sxs-lookup"><span data-stu-id="098e4-133">Make sure you save your scene (do this with either control/command+S or click on file, then click on Save).</span></span> 

5. <span data-ttu-id="098e4-134">匯入[Azure 空間的錨點](https://github.com/azure/azure-spatial-anchors-samples/releases)。</span><span class="sxs-lookup"><span data-stu-id="098e4-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="098e4-135">若要使用空間的錨點，您必須匯入此資產。</span><span class="sxs-lookup"><span data-stu-id="098e4-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="098e4-136">按一下上方的連結，然後 AzureSpatialAnchors.unitypackage 上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="098e4-136">Click on the link above and right click on AzureSpatialAnchors.unitypackage.</span></span> <span data-ttu-id="098e4-137">按一下 另存目標為，並將它儲存到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="098e4-137">Click on Save Target As and save it to your computer.</span></span> 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   <span data-ttu-id="098e4-139">儲存之後，請移回 Unity，按一下 資產，往下移到匯入封裝。</span><span class="sxs-lookup"><span data-stu-id="098e4-139">After it's saved, go back into Unity, click Assets, go down to Import Package.</span></span> <span data-ttu-id="098e4-140">然後按一下 自訂封裝...會開啟您電腦的檔案。</span><span class="sxs-lookup"><span data-stu-id="098e4-140">Then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="098e4-141">當它們執行，尋找您儲存 Azure 空間的錨點的封裝，並加以選取。</span><span class="sxs-lookup"><span data-stu-id="098e4-141">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="098e4-142">然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="098e4-142">Then click Open.</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   <span data-ttu-id="098e4-144">快顯視窗出現時，providingg 的工具和設定，以及詢問您要匯入的項目清單。</span><span class="sxs-lookup"><span data-stu-id="098e4-144">A pop-up appears, providingg a list of tools and settings, and asking you what to import.</span></span> <span data-ttu-id="098e4-145">選取 ***所有***可用的選項，然後按一下 匯入。</span><span class="sxs-lookup"><span data-stu-id="098e4-145">Select ***all*** of the options available, then click Import.</span></span>

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > <span data-ttu-id="098e4-147">注意:請耐心等候，需要幾分鐘的時間匯入。</span><span class="sxs-lookup"><span data-stu-id="098e4-147">Note: Be patient, it will take a few minutes to import.</span></span> 

   6. <span data-ttu-id="098e4-148">匯入[MR 基底模組資產套件](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)下一步。</span><span class="sxs-lookup"><span data-stu-id="098e4-148">Import [MR Base module Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) next.</span></span> <span data-ttu-id="098e4-149">很多類似步驟 5 中，按一下上方的連結。</span><span class="sxs-lookup"><span data-stu-id="098e4-149">Much like Step 5, click the link above.</span></span> <span data-ttu-id="098e4-150">然後以滑鼠右鍵按一下 BasemoduleAssetsV1 1.unitypackag，按一下 另存目標，並將它儲存到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="098e4-150">Then right click BasemoduleAssetsV1 1.unitypackag, and click Save Target As, and save it to your computer.</span></span>

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > <span data-ttu-id="098e4-152">秘訣：儲存所有這些資產的相同資料夾中，使其更輕鬆地尋找及存取。</span><span class="sxs-lookup"><span data-stu-id="098e4-152">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="098e4-153">它會保留所有項目好用且妥善管理。</span><span class="sxs-lookup"><span data-stu-id="098e4-153">It keeps everything nice and organized.</span></span>

   <span data-ttu-id="098e4-154">如同步驟 5 中，請回到 Unity、 按一下 資產，並停留在匯入封裝。</span><span class="sxs-lookup"><span data-stu-id="098e4-154">Just like Step 5, go back in to Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="098e4-155">按一下 自訂封裝...您電腦的檔案將會再次出現。</span><span class="sxs-lookup"><span data-stu-id="098e4-155">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="098e4-156">請移至您儲存此基本模組資產套件。</span><span class="sxs-lookup"><span data-stu-id="098e4-156">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="098e4-157">然後選取它。</span><span class="sxs-lookup"><span data-stu-id="098e4-157">and select it.</span></span> <span data-ttu-id="098e4-158">按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="098e4-158">Click Open.</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > <span data-ttu-id="098e4-160">注意:可能有多個稍後在此模組所需的資產。</span><span class="sxs-lookup"><span data-stu-id="098e4-160">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="098e4-161">請遵循下列步驟來匯入從這裡開始所述的任何資產。</span><span class="sxs-lookup"><span data-stu-id="098e4-161">Follow these steps to import any assets mentioned from this point on.</span></span> 
                                                                                                                                                                                                                    
7. <span data-ttu-id="098e4-162">匯入 ASA 模組通知使用相同的方法為匯入前的套件。</span><span class="sxs-lookup"><span data-stu-id="098e4-162">Import the ASA module ack using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="098e4-163">設定場景</span><span class="sxs-lookup"><span data-stu-id="098e4-163">Configuring your scene</span></span>

<span data-ttu-id="098e4-164">在本節中，我們會將 prefabs 和指令碼新增到場景方向，以建立一系列的示範基本概念的本機的錨點和 Azure 空間的錨點的行為方式的應用程式中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="098e4-164">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

7. <span data-ttu-id="098e4-165">在 [專案] 索引標籤的 [Assets] 資料夾底下按一下 ASAmoduleAssets。</span><span class="sxs-lookup"><span data-stu-id="098e4-165">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="098e4-166">選取之後，您會看到兩個 prefabs:ButtonParent 和 ParentAnchor。</span><span class="sxs-lookup"><span data-stu-id="098e4-166">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. <span data-ttu-id="098e4-168">將這兩個 prefabs 拖曳到場景中。</span><span class="sxs-lookup"><span data-stu-id="098e4-168">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. <span data-ttu-id="098e4-170">按兩下父錨點，以選取它。</span><span class="sxs-lookup"><span data-stu-id="098e4-170">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="098e4-171">您可能需要調整您的檢視，以查看整個場景。</span><span class="sxs-lookup"><span data-stu-id="098e4-171">You might need to adjust your view to see the entire scene.</span></span> <span data-ttu-id="098e4-172">視需要調整您的場景。</span><span class="sxs-lookup"><span data-stu-id="098e4-172">Adjust your scene as needed.</span></span>

    <span data-ttu-id="098e4-173">熟悉 ParentAnchor prefab。</span><span class="sxs-lookup"><span data-stu-id="098e4-173">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="098e4-174">目前的遊戲物件名稱，ParentAnchor，是供示範之用的彩色的 cube。</span><span class="sxs-lookup"><span data-stu-id="098e4-174">Currently, the game object named, ParentAnchor, is a colored cube for demonstration purposes.</span></span> <span data-ttu-id="098e4-175">最後，我們 '，將隱藏的 cube，並將我們的內容放 ParentAnchor 的子系。</span><span class="sxs-lookup"><span data-stu-id="098e4-175">Eventually, we',ll hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="098e4-176">此 prefab 包括 AzureSpatialAnchorsDemoWrapper.cs 隨附的指令碼 （ASA SDK），以及 ASAmoduleScript.cs 指令碼，包含這個模組 ParentAnchor 物件的一部分。</span><span class="sxs-lookup"><span data-stu-id="098e4-176">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK), and the ASAmoduleScript.cs script, included as part of this module to the ParentAnchor object.</span></span> 

10. <span data-ttu-id="098e4-177">設定按鈕。</span><span class="sxs-lookup"><span data-stu-id="098e4-177">Configure buttons.</span></span> <span data-ttu-id="098e4-178">下 ParentAnchor prefab 中，請注意幾個按鈕，加上標籤。</span><span class="sxs-lookup"><span data-stu-id="098e4-178">Under the ParentAnchor prefab, notice several labeled buttons.</span></span> <span data-ttu-id="098e4-179">這些按鈕會從 MRTK PressableButton prefabs 建立。</span><span class="sxs-lookup"><span data-stu-id="098e4-179">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="098e4-180">深入了解如何建立從 Pressable 按鈕[基底模組](mrlearning-base-ch2.md)。</span><span class="sxs-lookup"><span data-stu-id="098e4-180">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="098e4-181">針對每個按鈕，新增當使用者按下或選取下列清單根據按鈕就會觸發的事件。</span><span class="sxs-lookup"><span data-stu-id="098e4-181">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="098e4-182">名為 StartAzureSession，按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="098e4-182">For the Button named, StartAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="098e4-183">ParentAnchor 物件拖曳至空白的欄位，並將指派 StartAzureSession() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="098e4-183">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="098e4-187">按鈕名稱，StopAzureSession，建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="098e4-187">For the Button name, StopAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="098e4-188">ParentAnchor 物件拖曳至空白的欄位，並將指派 StopAzureSession() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="098e4-188">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="098e4-189">名為 CreateAnchor，按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="098e4-189">For the Button named, CreateAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="098e4-190">ParentAnchor 物件拖曳至空白的欄位，並將指派 CreateAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="098e4-190">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="098e4-191">名為開始尋找的錨點，按鈕建立新的事件，在按鈕按下 」 事件觸發程序，以及在按一下 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="098e4-191">For the Button named, Start Looking For Anchor, create a new event under the Button Presse" event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="098e4-192">ParentAnchor 物件拖曳至空白的欄位，並將指派 FindAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="098e4-192">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="098e4-193">名為 DeleteAzureAnchor，按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="098e4-193">For the Button named, DeleteAzureAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="098e4-194">ParentAnchor 物件拖曳至空白的欄位，並將指派 DeleteAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="098e4-194">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="098e4-195">命名為，刪除本機錨點按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="098e4-195">For the Button named, Delete Local Anchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="098e4-196">ParentAnchor 物件拖曳至空白的欄位，並將指派 RemoveLocalAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="098e4-196">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="098e4-197">建置，並示範基底應用程式</span><span class="sxs-lookup"><span data-stu-id="098e4-197">Build and demonstrate Base Application</span></span>

<span data-ttu-id="098e4-198">現在，場景設定來示範 Azure 空間的錨點的基本概念，我們會建置及示範 Azure 空間的錨點的基本行為。</span><span class="sxs-lookup"><span data-stu-id="098e4-198">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="098e4-199">如果您已關閉前面幾節中的 [建置設定] 視窗，請移至 [檔案] > [建置設定] 來重新開啟 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="098e4-199">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="098e4-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="098e4-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="098e4-201">請確定您想要嘗試在的場景中組建清單中的場景是藉由按一下加入開啟的場景按鈕。</span><span class="sxs-lookup"><span data-stu-id="098e4-201">Ensure the scene you want to try is in the Scenes in Build list by clicking on the Add Open Scenes button.</span></span>

3. <span data-ttu-id="098e4-202">按下 [建置] 按鈕，開始建置程序。</span><span class="sxs-lookup"><span data-stu-id="098e4-202">Press the Build button to begin the build process.</span></span>
    <span data-ttu-id="098e4-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="098e4-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="098e4-204">為您的應用程式建立並命名新資料夾。</span><span class="sxs-lookup"><span data-stu-id="098e4-204">Create and name a new folder for your application.</span></span> <span data-ttu-id="098e4-205">下圖中的應用程式命名的資料夾已建立包含應用程式。</span><span class="sxs-lookup"><span data-stu-id="098e4-205">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="098e4-206">按一下 選取的資料夾，以開始建置新建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="098e4-206">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="098e4-207">在 Unity 中建置完成之後，您也可以關閉 建立設定 」 視窗。</span><span class="sxs-lookup"><span data-stu-id="098e4-207">After the build has completed, you may close the Build Setting" window in Unity.</span></span> 
    <span data-ttu-id="098e4-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="098e4-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="098e4-209">注意：如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。</span><span class="sxs-lookup"><span data-stu-id="098e4-209">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="098e4-210">如果您看到錯誤，例如「錯誤：CS0246 = 找不到"XX"的輸入或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？)。</span><span class="sxs-lookup"><span data-stu-id="098e4-210">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="098e4-211">您可能需要安裝[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="098e4-211">You might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="098e4-212">在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="098e4-212">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="098e4-213">按兩下 the"MixedRealityBase.sln 方案或對應的名稱。</span><span class="sxs-lookup"><span data-stu-id="098e4-213">Double click on the“MixedRealityBase.sln solution or the corresponding name.</span></span> <span data-ttu-id="098e4-214">如果您使用的替代名稱，為您的專案在 Visual Studio 中開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="098e4-214">if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="098e4-215">注意:請務必開啟新建立的資料夾 （亦即，應用程式資料夾，如果先前的步驟中遵循的命名慣例，因為會有該並不會混淆組建資料夾內的.sln 檔案的資料夾以外的名稱類似的.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="098e4-215">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps because there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > <span data-ttu-id="098e4-217">注意:如果 Visual Studio 會要求安裝新的元件，請花一些時間來確保所有必要的元件會安裝在為特定[[安裝工具] 頁面](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="098e4-217">Note: If Visual Studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="098e4-218">使用 USB 纜線，將 HoloLens 2 插入您的電腦。</span><span class="sxs-lookup"><span data-stu-id="098e4-218">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="098e4-219">雖然這些課程指示假設您要部署測試與 HoloLens 2 裝置，您也可以選擇將部署到[HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[側載應用程式套件](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="098e4-219">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="098e4-220">對您的裝置進行建置之前，請確定裝置處於開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="098e4-220">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="098e4-221">如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。</span><span class="sxs-lookup"><span data-stu-id="098e4-221">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="098e4-222">請遵循[這些指示](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)若要啟用開發人員模式，或與 Visual Studio 配對。</span><span class="sxs-lookup"><span data-stu-id="098e4-222">Follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="098e4-223">選取發行組態，而且"RM"架構，用於建置以 HoloLens 2 設定 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="098e4-223">Configure Visual Studio for building to your HoloLens 2 by selecting the Release configuration and the “RM” architecture.</span></span>
    <span data-ttu-id="098e4-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="098e4-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
   
9. <span data-ttu-id="098e4-225">最後一個步驟是建置到您的裝置，選取 偵錯 > 啟動但不偵錯。</span><span class="sxs-lookup"><span data-stu-id="098e4-225">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="098e4-226">選取 啟動但不偵錯會立即開始在您的裝置時不會出現在 Visual Studio 成功組建 ithout 偵錯資訊的應用程式。</span><span class="sxs-lookup"><span data-stu-id="098e4-226">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build ithout Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="098e4-227">這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。</span><span class="sxs-lookup"><span data-stu-id="098e4-227">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="098e4-228">您也可以選取組建 > 部署的方案，而不需要自動啟動應用程式部署到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="098e4-228">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
    <span data-ttu-id="098e4-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="098e4-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
    
<span data-ttu-id="098e4-230">10.遵循的指示。</span><span class="sxs-lookup"><span data-stu-id="098e4-230">10.Follow the instructions.</span></span> <span data-ttu-id="098e4-231">當您的裝置上執行應用程式時，請遵循螢幕上的指示。</span><span class="sxs-lookup"><span data-stu-id="098e4-231">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="098e4-232">按 場景按鈕對應至下列步驟。</span><span class="sxs-lookup"><span data-stu-id="098e4-232">Press the Scene buttons corresponding to the Steps below.</span></span>
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="098e4-233">啟動空間的錨點的工作階段。</span><span class="sxs-lookup"><span data-stu-id="098e4-233">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="098e4-234">移到不同位置的 cube。</span><span class="sxs-lookup"><span data-stu-id="098e4-234">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="098e4-235">儲存 Azure 空間的錨點，在 cube 的位置。</span><span class="sxs-lookup"><span data-stu-id="098e4-235">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="098e4-236">停止 Azure 空間的錨點的工作階段。</span><span class="sxs-lookup"><span data-stu-id="098e4-236">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="098e4-237">移除本機 cube，就可以讓使用者移動 cube 上的錨點。</span><span class="sxs-lookup"><span data-stu-id="098e4-237">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    6. <span data-ttu-id="098e4-238">移動其他地方的 cube。</span><span class="sxs-lookup"><span data-stu-id="098e4-238">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="098e4-239">啟動 Azure 空間的錨點的工作階段。</span><span class="sxs-lookup"><span data-stu-id="098e4-239">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="098e4-240">尋找 Azure 空間的 aachors。</span><span class="sxs-lookup"><span data-stu-id="098e4-240">Find Azure Spatial aachors.</span></span> 
    
    <span data-ttu-id="098e4-241">您應該移回至原始位置您的電子將它放在建立錨點時）。</span><span class="sxs-lookup"><span data-stu-id="098e4-241">e You should go back to the original place you put it when you created the anchor).</span></span>
    9. <span data-ttu-id="098e4-242">刪除 Azure 空間的錨點。</span><span class="sxs-lookup"><span data-stu-id="098e4-242">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="098e4-243">停止 Azure 工作階段。</span><span class="sxs-lookup"><span data-stu-id="098e4-243">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="098e4-244">錨定的體驗</span><span class="sxs-lookup"><span data-stu-id="098e4-244">Anchoring an experience</span></span>

<span data-ttu-id="098e4-245">在先前章節中，您已了解 Azure 空間的錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="098e4-245">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="098e4-246">我們使用 cube 來表示，並且將視覺化父代遊戲物件，具有附加的錨點。</span><span class="sxs-lookup"><span data-stu-id="098e4-246">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="098e4-247">在本節中，您會學習如何將其放 ParentAnchor 物件的子系的錨點整個的體驗。</span><span class="sxs-lookup"><span data-stu-id="098e4-247">In this section, you learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="098e4-248">此範例中，我們使用農曆模組時所建立的組件示範應用程式[第 6 課的基本模組](mrlearning-base-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="098e4-248">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="098e4-249">搜尋完成農曆模組組件的 prefab，並將它拖曳到您的階層做為子系的 AnchorParent gameobject 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="098e4-249">Search for the Lunar Module Assembly Complete prefab, and drag it into your heirarchy as a child of the AnchorParent gameobject as shown in the image below.</span></span>

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="098e4-251">位置模組組件體驗，讓 cube 仍會暴露在下圖所示。</span><span class="sxs-lookup"><span data-stu-id="098e4-251">Position the module assembly experience so that the cube is still exposed as shown in the image below.</span></span> <span data-ttu-id="098e4-252">在應用程式，使用者可能會重新定位整個體驗，藉由移動 cube。</span><span class="sxs-lookup"><span data-stu-id="098e4-252">In the application, users may reposition the entire experience by moving the cube.</span></span> 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > <span data-ttu-id="098e4-254">注意:有各種不同的重新定位體驗，包括使用按鈕來切換週框方塊括住的經驗，使用 （例如，在此步驟中所用的 cube)，重新調整物件的位置和旋轉的 gizmo 使用的使用者體驗流程等等。</span><span class="sxs-lookup"><span data-stu-id="098e4-254">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="098e4-255">恭喜！</span><span class="sxs-lookup"><span data-stu-id="098e4-255">Congratulations</span></span>
<span data-ttu-id="098e4-256">在這一課，您已了解 Azure 空間的錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="098e4-256">In this lesson, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="098e4-257">此 esson 提供您幾個按鈕，可讓您瀏覽啟動及停止 Azure 工作階段，以及建立、 上傳，以及下載 azure 的錨點，單一裝置上所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="098e4-257">This esson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="098e4-258">在下一課中，我們將學習如何將 Azure 的錨點識別碼儲存至擷取，您 HoloLens 2，即使重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="098e4-258">In the next lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="098e4-259">在系列中，您也將學習如何達成空間的對齊方式，並了解多使用者共用工作階段 （即將推出的共用模組一部分）。 多個裝置之間傳輸錨點識別碼</span><span class="sxs-lookup"><span data-stu-id="098e4-259">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and learn about multi-user shared sessions (forthcoming as part of sharing module.)</span></span>

[<span data-ttu-id="098e4-260">下一課：ASA Lesson 2</span><span class="sxs-lookup"><span data-stu-id="098e4-260">Next Lesson: ASA Lesson 2</span></span>](mrlearning-asa-ch2.md)

