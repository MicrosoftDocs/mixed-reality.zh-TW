---
title: Azure 空間錨點教學課程-1。 開始使用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: ac345ecafee3a09e3b5ad58344310234e60354a1
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926873"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="f008d-105">1. 開始使用 Azure 空間錨點</span><span class="sxs-lookup"><span data-stu-id="f008d-105">1. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="f008d-106">歡迎使用 HoloLens 2 教學課程的第二個模組。</span><span class="sxs-lookup"><span data-stu-id="f008d-106">Welcome to the second module of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="f008d-107">開始使用之前，請確定所有[必要條件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)都已完成。</span><span class="sxs-lookup"><span data-stu-id="f008d-107">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="f008d-108">如果您尚未完成第一個[基本模組](mrlearning-base.md)，建議您先完成該課程模組。</span><span class="sxs-lookup"><span data-stu-id="f008d-108">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="f008d-109">如果您從新的 Unity 專案開始，請遵循[基底模組](mrlearning-base.md)中的新專案建立步驟。</span><span class="sxs-lookup"><span data-stu-id="f008d-109">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="f008d-110">目標</span><span class="sxs-lookup"><span data-stu-id="f008d-110">Objectives</span></span>

* <span data-ttu-id="f008d-111">瞭解使用 HoloLens 2 搭配 Azure 空間錨點進行開發的基本概念</span><span class="sxs-lookup"><span data-stu-id="f008d-111">Learn the fundamentals of developing with Azure Spatial Anchors with HoloLens 2</span></span>

* <span data-ttu-id="f008d-112">建立、上傳及下載空間錨點</span><span class="sxs-lookup"><span data-stu-id="f008d-112">Create, upload, and download spatial anchors</span></span>

## <a name="instructions"></a><span data-ttu-id="f008d-113">指示</span><span class="sxs-lookup"><span data-stu-id="f008d-113">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="f008d-114">下載和匯入資產</span><span class="sxs-lookup"><span data-stu-id="f008d-114">Downloading and importing assets</span></span>
<span data-ttu-id="f008d-115">開始之前，請先下載並匯入下列資產：</span><span class="sxs-lookup"><span data-stu-id="f008d-115">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="f008d-116">Azure 空間錨點 v 1.1。0</span><span class="sxs-lookup"><span data-stu-id="f008d-116">Azure Spatial Anchors v1.1.0</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[<span data-ttu-id="f008d-117">MR 基底模組資產套件1.2 版</span><span class="sxs-lookup"><span data-stu-id="f008d-117">MR Base module Asset Pack v1.2</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/1.2/BaseModuleAssets-1.2.unitypackage)

[<span data-ttu-id="f008d-118">ASA 模組資產套件 v 1.3。1</span><span class="sxs-lookup"><span data-stu-id="f008d-118">ASA module Asset Pack v1.3.1</span></span>](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage)

[<span data-ttu-id="f008d-119">Mixed Reality 工具組基礎封裝2.1。0</span><span class="sxs-lookup"><span data-stu-id="f008d-119">Mixed Reality Toolkit  Foundation Package 2.1.0</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. <span data-ttu-id="f008d-120">在您的專案中建立新的場景。</span><span class="sxs-lookup"><span data-stu-id="f008d-120">Create a new scene in your project.</span></span> <span data-ttu-id="f008d-121">以滑鼠右鍵按一下場景資料夾，然後依序按一下 [建立]、[場景]。</span><span class="sxs-lookup"><span data-stu-id="f008d-121">Right click your Scene folder, click Create, then Scene.</span></span> <span data-ttu-id="f008d-122">將新場景命名為 "ASALearningModule"。</span><span class="sxs-lookup"><span data-stu-id="f008d-122">Name the new scene as "ASALearningModule".</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="f008d-124">按兩下 [ASALearningmodule] 場景，查看一些預先定義的專案與新場景一起出現。</span><span class="sxs-lookup"><span data-stu-id="f008d-124">Double click "ASALearningmodule" scene to see some pre-defined items to appear along with the new scene.</span></span> 
3. <span data-ttu-id="f008d-125">設定混合現實開發的場景。</span><span class="sxs-lookup"><span data-stu-id="f008d-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="f008d-127">注意：您可能會看到一個快顯對話方塊，可供您選取[混合現實工具組的設定檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。</span><span class="sxs-lookup"><span data-stu-id="f008d-127">Note: You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="f008d-128">按兩下名為*DefaultHoloLens2ConfigurationProfile*的設定檔。</span><span class="sxs-lookup"><span data-stu-id="f008d-128">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

4. <span data-ttu-id="f008d-129">為 MRTK 選擇檔案時，請選取 [DefaultMixedRealityToolkitConfigurationProfile]。</span><span class="sxs-lookup"><span data-stu-id="f008d-129">When choosing a file for the MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.</span></span>

> <span data-ttu-id="f008d-130">注意：如果您有自己的設定設定檔，則可以隨意使用。</span><span class="sxs-lookup"><span data-stu-id="f008d-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="f008d-132">現在場景已設定為混合現實。</span><span class="sxs-lookup"><span data-stu-id="f008d-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="f008d-133">請確定您儲存場景（以 control/command + S 執行此動作，或按一下 [檔案]，然後按一下 [儲存]）。</span><span class="sxs-lookup"><span data-stu-id="f008d-133">Make sure you save your scene (do this with either control/command+S or click on file, then click on Save).</span></span> 

5. <span data-ttu-id="f008d-134">匯入在步驟1中下載的[Azure 空間錨點 v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity package。</span><span class="sxs-lookup"><span data-stu-id="f008d-134">Import the [Azure Spatial Anchors v1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity package, that we downloaded in step 1.</span></span> <span data-ttu-id="f008d-135">為此，按一下 [資產]，然後向下移至 [匯入套件]。</span><span class="sxs-lookup"><span data-stu-id="f008d-135">For that, click Assets, go down to Import Package.</span></span> <span data-ttu-id="f008d-136">然後按一下 [自訂套件 ...]您的電腦檔案將會開啟。</span><span class="sxs-lookup"><span data-stu-id="f008d-136">Then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="f008d-137">當他們這麼做時，請尋找您儲存 Azure 空間錨點套件的位置，並加以選取。</span><span class="sxs-lookup"><span data-stu-id="f008d-137">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="f008d-138">然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="f008d-138">Then click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

<span data-ttu-id="f008d-140">快顯視窗隨即出現，並提供工具和設定的清單，並詢問您要匯入的內容。</span><span class="sxs-lookup"><span data-stu-id="f008d-140">A pop-up appears, providing a list of tools and settings, and asking you what to import.</span></span> <span data-ttu-id="f008d-141">選取***所有***可用的選項，然後按一下 [匯入]。</span><span class="sxs-lookup"><span data-stu-id="f008d-141">Select ***all*** of the options available, then click Import.</span></span>

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> <span data-ttu-id="f008d-143">注意：請耐心等候，匯入需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="f008d-143">Note: Be patient, it will take a few minutes to import.</span></span> 

6. <span data-ttu-id="f008d-144">匯入[MR 基底模組資產套件](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2)下一步。</span><span class="sxs-lookup"><span data-stu-id="f008d-144">Import [MR Base module Asset Pack](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) next.</span></span> <span data-ttu-id="f008d-145">與步驟5非常類似，請回到 Unity，按一下 [資產]，然後將滑鼠停留在 [匯入套件] 上方。</span><span class="sxs-lookup"><span data-stu-id="f008d-145">Much like Step 5, go back in to Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="f008d-146">按一下 [自訂套件 ...]您的電腦檔案將會再次出現。</span><span class="sxs-lookup"><span data-stu-id="f008d-146">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="f008d-147">移至您儲存基本模組資產套件的位置。</span><span class="sxs-lookup"><span data-stu-id="f008d-147">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="f008d-148">然後選取它。</span><span class="sxs-lookup"><span data-stu-id="f008d-148">and select it.</span></span> <span data-ttu-id="f008d-149">按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="f008d-149">Click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> <span data-ttu-id="f008d-151">注意：此課程模組稍後可能需要更多資產。</span><span class="sxs-lookup"><span data-stu-id="f008d-151">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="f008d-152">請遵循下列步驟來匯入此處所提及的任何資產。</span><span class="sxs-lookup"><span data-stu-id="f008d-152">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="f008d-153">匯入[ASA 模組套件 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage) ，使用與匯入其他先前封裝相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="f008d-153">Import the [ASA module pack 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage) using the same steps as importing the other previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="f008d-154">設定場景</span><span class="sxs-lookup"><span data-stu-id="f008d-154">Configuring your scene</span></span>

<span data-ttu-id="f008d-155">在本節中，我們將在場景中新增 prefabs 和腳本，以建立一系列的按鈕，以示範本機錨點和 Azure 空間錨點在應用程式中的行為。</span><span class="sxs-lookup"><span data-stu-id="f008d-155">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

8. <span data-ttu-id="f008d-156">在 [專案] 索引標籤的 [資產] 資料夾底下，按一下 [ASAmoduleAssets]。</span><span class="sxs-lookup"><span data-stu-id="f008d-156">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="f008d-157">選取之後，您會看到兩個 prefabs： ButtonParent 和 ParentAnchor。</span><span class="sxs-lookup"><span data-stu-id="f008d-157">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. <span data-ttu-id="f008d-159">將這兩個 prefabs 拖曳到場景中。</span><span class="sxs-lookup"><span data-stu-id="f008d-159">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

<span data-ttu-id="f008d-161">注意：將 ButtonParent 新增至場景後，會出現快顯視窗，要求您匯入 TMP 資產。</span><span class="sxs-lookup"><span data-stu-id="f008d-161">Note: After adding the ButtonParent into the scene, a popup will appear asking you to import TMP assets.</span></span> <span data-ttu-id="f008d-162">匯入 "TMP Essentials"。</span><span class="sxs-lookup"><span data-stu-id="f008d-162">Import the "TMP Essentials".</span></span> <span data-ttu-id="f008d-163">之後，如果您在場景中看到任何大字型文字，請刪除 ButtonParent 物件，然後再次從 ASAmoduleAssets 資料夾新增。</span><span class="sxs-lookup"><span data-stu-id="f008d-163">After this, If you see any large font text in the scene, delete the ButtonParent object and add it again from the ASAmoduleAssets folder.</span></span>

<span data-ttu-id="f008d-164">注意：如果您想要檢查 HoloLens 中的 debug 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f008d-164">Note: If you want to check the debug logs in the HoloLens.</span></span> <span data-ttu-id="f008d-165">您可以將 DebugWindow prefab 從 ASAModuleAssets 資料夾拖放到場景中。</span><span class="sxs-lookup"><span data-stu-id="f008d-165">You can drag and drop the DebugWindow prefab from ASAModuleAssets folder into the scene.</span></span> <span data-ttu-id="f008d-166">在 [DebugWindow 偵測器] 面板中附加 DebugWindowMessaging 腳本，並啟用 [啟用 Debug Window] 選項。</span><span class="sxs-lookup"><span data-stu-id="f008d-166">Attach the DebugWindowMessaging script in the DebugWindow inspector panel and enable the Debug Window Enabled option.</span></span> <span data-ttu-id="f008d-167">之後，將 DebugWindow prefab 拖放到 DebugText 空的欄位中。</span><span class="sxs-lookup"><span data-stu-id="f008d-167">After that, drag  and drop the DebugWindow prefab into DebugText empty field.</span></span> <span data-ttu-id="f008d-168">您也可以隨時調整 DebugWindow 位置。</span><span class="sxs-lookup"><span data-stu-id="f008d-168">You can also adjust the DebugWindow position wherever appropriate for you.</span></span>

10. <span data-ttu-id="f008d-169">若要放大場景，請按兩下階層中的父錨點，並調整您的視圖，以視需要查看整個場景。</span><span class="sxs-lookup"><span data-stu-id="f008d-169">In order to zoom in to the scene, double click on the parent anchor in the hierarchy and adjust your view to see the entire scene as needed.</span></span> <span data-ttu-id="f008d-170">目前，ParentAnchor 是僅供示範用途使用的彩色 cube。</span><span class="sxs-lookup"><span data-stu-id="f008d-170">Currently, ParentAnchor is a colored cube used for only demonstration purpose.</span></span> <span data-ttu-id="f008d-171">最後，我們將隱藏 cube，並將內容放在 ParentAnchor 的子系中。</span><span class="sxs-lookup"><span data-stu-id="f008d-171">Eventually, we will hide the cube and place our content as a child of the ParentAnchor.</span></span> 

11. <span data-ttu-id="f008d-172">現在讓我們設定用來操作場景的按鈕。</span><span class="sxs-lookup"><span data-stu-id="f008d-172">Now lets configure the buttons for operating the scene.</span></span> <span data-ttu-id="f008d-173">為此，請展開 [ButtonParent] prefab，並注意數個加上標籤的按鈕。</span><span class="sxs-lookup"><span data-stu-id="f008d-173">For that, expand the ButtonParent prefab, and notice several labeled buttons.</span></span> <span data-ttu-id="f008d-174">這些按鈕是從 MRTK 的 PressableButton prefabs 所建立。</span><span class="sxs-lookup"><span data-stu-id="f008d-174">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="f008d-175">深入瞭解如何從[基底模組](mrlearning-base-ch2.md)建立 PressableButton。</span><span class="sxs-lookup"><span data-stu-id="f008d-175">Learn more about how to create PressableButton from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="f008d-176">為了讓這些按鈕運作，我們必須新增事件，當使用者按下或選取個別按鈕時，就會觸發此事件。</span><span class="sxs-lookup"><span data-stu-id="f008d-176">For these buttons to operate, we need to add an event which will be triggered when the user presses or selects the individual buttons.</span></span> 

- <span data-ttu-id="f008d-177">針對名為 StartAzureSession 的按鈕，在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。</span><span class="sxs-lookup"><span data-stu-id="f008d-177">For the Button named, StartAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f008d-178">將 ParentAnchor 物件拖曳至空白欄位，並從 ParentAnchor 物件的 ASAmoduleScript 元件指派 StartAzureSession （）方法，如下列螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="f008d-178">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component as shown in the below screenshot.</span></span>
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="f008d-182">針對按鈕名稱 StopAzureSession，請在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。</span><span class="sxs-lookup"><span data-stu-id="f008d-182">For the Button name, StopAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f008d-183">將 ParentAnchor 物件拖曳至空白欄位，然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 StopAzureSession （）方法。</span><span class="sxs-lookup"><span data-stu-id="f008d-183">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="f008d-184">針對名為 CreateAnchor 的按鈕，在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。</span><span class="sxs-lookup"><span data-stu-id="f008d-184">For the Button named, CreateAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f008d-185">將 ParentAnchor 物件拖曳至空白欄位，然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 CreateAzureAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="f008d-185">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>  <span data-ttu-id="f008d-186">**之後，再次將 ParentAnchor 拖曳到下一個空白的「遊戲物件」欄位。**</span><span class="sxs-lookup"><span data-stu-id="f008d-186">**After this, drag the ParentAnchor again into the next empty "Game Object" field.**</span></span>

- <span data-ttu-id="f008d-187">針對名為的按鈕，開始尋找錨點，在按鈕下按下 [事件觸發程式]，以及 [On Click] 事件觸發程式來建立新事件。</span><span class="sxs-lookup"><span data-stu-id="f008d-187">For the Button named, Start Looking For Anchor, create a new event under the Button Press" event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f008d-188">將 ParentAnchor 物件拖曳至空白欄位，然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 FindAzureAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="f008d-188">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="f008d-189">針對名為 DeleteAzureAnchor 的按鈕，在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。</span><span class="sxs-lookup"><span data-stu-id="f008d-189">For the Button named, DeleteAzureAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f008d-190">將 ParentAnchor 物件拖曳至空白欄位，然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 DeleteAzureAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="f008d-190">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>  

- <span data-ttu-id="f008d-191">針對名為的按鈕，刪除本機錨點，在按下按鈕的事件觸發程式和 On Click 事件觸發程式底下建立新事件。</span><span class="sxs-lookup"><span data-stu-id="f008d-191">For the Button named, Delete Local Anchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f008d-192">將 ParentAnchor 物件拖曳至空白欄位，然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 RemoveLocalAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="f008d-192">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span> <span data-ttu-id="f008d-193">**之後，請將 ParentAnchor 物件再次拖曳到下一個空白的「遊戲物件」欄位。**</span><span class="sxs-lookup"><span data-stu-id="f008d-193">**After this, drag the ParentAnchor object again into the next empty "Game Object" field.**</span></span>

12. <span data-ttu-id="f008d-194">若要設定 Azure 空間錨點，請移至 [資產] 資料夾中的 AzureSpatialAnchorsPlugin 資料夾，然後流覽至 [範例-> 資源-> AzureSpatialAnchorsDemoConfig 檔案]。</span><span class="sxs-lookup"><span data-stu-id="f008d-194">To set up Azure spatial anchors, go to AzureSpatialAnchorsPlugin folder in assets folder and then navigate to Examples -> Resources->AzureSpatialAnchorsDemoConfig file.</span></span> <span data-ttu-id="f008d-195">在 [偵測器] 面板中，新增稍早建立的 Azure 帳戶識別碼和帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="f008d-195">In the inspector panel add the Azure Account ID and Account Key created earlier.</span></span> <span data-ttu-id="f008d-196">如果您尚未建立或沒有這些專案，請遵循[必要條件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)。</span><span class="sxs-lookup"><span data-stu-id="f008d-196">If you haven't created or don't have the them, please follow the [Prerequisites](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span></span> 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="f008d-198">建立並示範基本應用程式</span><span class="sxs-lookup"><span data-stu-id="f008d-198">Build and demonstrate Base Application</span></span>

<span data-ttu-id="f008d-199">既然您的場景已設定為示範 Azure 空間錨點的基本概念，我們將會建立並示範 Azure 空間錨點的基本行為。</span><span class="sxs-lookup"><span data-stu-id="f008d-199">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="f008d-200">前往 [檔案] > [組建設定]，再次開啟 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f008d-200">Open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="f008d-201">![mrlearning-asa-ch1-3-步驟 1](images/mrlearning-asa-ch1-3-step1.jpg)</span><span class="sxs-lookup"><span data-stu-id="f008d-201">![mrlearning-asa-ch1-3-step1](images/mrlearning-asa-ch1-3-step1.jpg)</span></span>
2. <span data-ttu-id="f008d-202">按一下 [新增開啟的場景] 按鈕，確定您想要嘗試的場景是在 [組建中的場景] 清單中。</span><span class="sxs-lookup"><span data-stu-id="f008d-202">Ensure the scene you want to try is in the Scenes in build list by clicking on the Add Open Scenes button.</span></span>
3. <span data-ttu-id="f008d-203">確認平臺已設定為 [通用 Windows 平臺]。</span><span class="sxs-lookup"><span data-stu-id="f008d-203">Verify the Platform is set to Universal Windows Platform.</span></span> <span data-ttu-id="f008d-204">如果沒有，請將它設定為相同的。</span><span class="sxs-lookup"><span data-stu-id="f008d-204">If not, please set it to the same.</span></span>
4. <span data-ttu-id="f008d-205">按 [Player 設定] 按鈕，然後移至 [發佈設定]。</span><span class="sxs-lookup"><span data-stu-id="f008d-205">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="f008d-206">在 [功能] 底下，啟用：網際網路、網際網路用戶端伺服器、私人網路用戶端伺服器、卸除式存放裝置、網路攝影機、麥克風和空間感知。</span><span class="sxs-lookup"><span data-stu-id="f008d-206">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Removable Storage, Webcam, Microphone and Spatial Perception.</span></span>
5. <span data-ttu-id="f008d-207">在相同的播放人員設定中，移至 [XR 設定]，然後選取支援的虛擬實境。</span><span class="sxs-lookup"><span data-stu-id="f008d-207">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>
6. <span data-ttu-id="f008d-208">按下 [建置] 按鈕，開始建置程序。</span><span class="sxs-lookup"><span data-stu-id="f008d-208">Press the Build button to begin the build process.</span></span>
   <span data-ttu-id="f008d-209">![mrlearning-asa-ch1-3-步驟 6](images/mrlearning-asa-ch1-3-step6.jpg)</span><span class="sxs-lookup"><span data-stu-id="f008d-209">![mrlearning-asa-ch1-3-step6](images/mrlearning-asa-ch1-3-step6.jpg)</span></span>
7. <span data-ttu-id="f008d-210">為您的應用程式建立並命名新資料夾。</span><span class="sxs-lookup"><span data-stu-id="f008d-210">Create and name a new folder for your application.</span></span> <span data-ttu-id="f008d-211">在下圖中，已建立名為 App 的資料夾來包含應用程式。</span><span class="sxs-lookup"><span data-stu-id="f008d-211">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="f008d-212">按一下 [選取資料夾]，開始建立新建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f008d-212">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="f008d-213">組建完成之後，您可以在 Unity 中關閉 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f008d-213">After the build has completed, you may close the Build Setting" window in Unity.</span></span>

    ![mrlearning-asa-ch1-3-step7](images/mrlearning-asa-ch1-3-step7.jpg)

    > <span data-ttu-id="f008d-215">注意：如果組建失敗，請嘗試重新建立或重新開機 Unity，然後重新建立。</span><span class="sxs-lookup"><span data-stu-id="f008d-215">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="f008d-216">如果您看到錯誤，例如「錯誤： CS0246 = 類型或命名空間名稱 "XX" 找不到（您是否遺漏 using 指示詞或元件參考？）。</span><span class="sxs-lookup"><span data-stu-id="f008d-216">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="f008d-217">您可能需要安裝[Windows 10 SDK （10.0.18362.0）](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="f008d-217">You might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span> 


8. <span data-ttu-id="f008d-218">即使在成功組建之後，您可能會收到一些錯誤，如下所示，但如果組建成功，您可以忽略它們，並繼續進行後續步驟。</span><span class="sxs-lookup"><span data-stu-id="f008d-218">Even after a successful build you might get some errors as shown below but if the build is successful you can ignore them and proceed with next steps.</span></span>

    ![mrlearning-asa-ch1-3-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. <span data-ttu-id="f008d-220">在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="f008d-220">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="f008d-221">按兩下 "MixedRealityBase" 方案或對應的名稱。</span><span class="sxs-lookup"><span data-stu-id="f008d-221">Double click on the“MixedRealityBase.sln" solution or the corresponding name.</span></span> <span data-ttu-id="f008d-222">如果您使用專案的替代名稱，在 Visual Studio 中開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="f008d-222">if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

    > <span data-ttu-id="f008d-223">注意：請務必開啟新建立的資料夾（也就是應用程式資料夾，如果遵循先前步驟中的命名慣例，因為該資料夾以外的名稱類似 .sln 檔案不會與組建資料夾內的 .sln 檔案混淆）。</span><span class="sxs-lookup"><span data-stu-id="f008d-223">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps because there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span>

    ![mrlearning-asa-ch1-3-step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > <span data-ttu-id="f008d-225">注意：如果 Visual Studio 要求安裝新元件，請花點時間確定所有必要條件元件都已安裝為[[安裝工具] 頁面](install-the-tools.md)中的特定</span><span class="sxs-lookup"><span data-stu-id="f008d-225">Note: If Visual Studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span>


9. <span data-ttu-id="f008d-226">使用 USB 纜線，將 HoloLens 2 插入您的電腦。</span><span class="sxs-lookup"><span data-stu-id="f008d-226">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="f008d-227">雖然這些課程指示假設您將使用 HoloLens 2 裝置部署測試，但您也可以選擇部署至[hololens 2 模擬器](using-the-hololens-emulator.md)，或選擇建立用於側[載的應用程式套件](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="f008d-227">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

10. <span data-ttu-id="f008d-228">對您的裝置進行建置之前，請確定裝置處於開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="f008d-228">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="f008d-229">如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。</span><span class="sxs-lookup"><span data-stu-id="f008d-229">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="f008d-230">如果您需要啟用開發人員模式或與 Visual Studio 配對，請遵循[這些指示](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="f008d-230">Follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

11. <span data-ttu-id="f008d-231">藉由選取發行設定和 ARM 架構，設定用來建立 HoloLens 2 的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f008d-231">Configure Visual Studio for building to your HoloLens 2 by selecting the Release configuration as well as the ARM architecture.</span></span>

    ![mrlearning-asa-ch1-3-step11](images/mrlearning-asa-ch1-3-step11.jpg)


12. <span data-ttu-id="f008d-233">最後一個步驟是選取 [Debug] > [啟動但不進行偵錯工具] 來建立裝置。</span><span class="sxs-lookup"><span data-stu-id="f008d-233">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="f008d-234">選取 [啟動但不進行偵錯工具]，會在成功組建時立即在裝置上啟動，而不會出現在 Visual Studio 中的偵測資訊。</span><span class="sxs-lookup"><span data-stu-id="f008d-234">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="f008d-235">這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。</span><span class="sxs-lookup"><span data-stu-id="f008d-235">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="f008d-236">您也可以選取 [組建 > 部署解決方案]，以部署至您的裝置，而不會自動啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="f008d-236">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

    ![mrlearning-asa-ch1-3-step12](images/mrlearning-asa-ch1-3-step12.jpg)

><span data-ttu-id="f008d-238">注意： Azure 空間錨點會使用網際網路來儲存和載入錨定資料，因此請先確定您的裝置已連線到網際網路，然後再測試 ASA 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f008d-238">Note: The Azure spatial anchors uses the internet to save and load the anchor data so make sure your device is connected to internet before testing the ASA app.</span></span>

13. <span data-ttu-id="f008d-239">請依照指示進行。</span><span class="sxs-lookup"><span data-stu-id="f008d-239">Follow the instructions.</span></span> 
    <span data-ttu-id="f008d-240">當應用程式在您的裝置上執行時，請遵循畫面上的指示。</span><span class="sxs-lookup"><span data-stu-id="f008d-240">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="f008d-241">按下與下列步驟對應的場景按鈕。</span><span class="sxs-lookup"><span data-stu-id="f008d-241">Press the Scene buttons corresponding to the Steps below.</span></span> <span data-ttu-id="f008d-242">如果您已如先前步驟所述新增 [偵錯工具] 視窗，您可以看到個別按鈕按下的意見反應，以及與 Azure 空間錨點相關之個別作業的進度。</span><span class="sxs-lookup"><span data-stu-id="f008d-242">If you added the debug window as mentioned in the previous steps you can see the feedback for individual button press and the progress of individual operations related to Azure spatial anchors.</span></span>

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="f008d-244">啟動空間錨點會話。</span><span class="sxs-lookup"><span data-stu-id="f008d-244">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="f008d-245">將 cube 移至不同的位置。</span><span class="sxs-lookup"><span data-stu-id="f008d-245">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="f008d-246">將 Azure 空間錨點儲存在 cube 的位置。</span><span class="sxs-lookup"><span data-stu-id="f008d-246">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="f008d-247">停止 Azure 空間錨點會話。</span><span class="sxs-lookup"><span data-stu-id="f008d-247">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="f008d-248">移除 cube 上的本機錨點，讓使用者可以移動 cube。</span><span class="sxs-lookup"><span data-stu-id="f008d-248">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    
    6. <span data-ttu-id="f008d-249">將 cube 移到其他地方。</span><span class="sxs-lookup"><span data-stu-id="f008d-249">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="f008d-250">啟動 Azure 空間錨點會話。</span><span class="sxs-lookup"><span data-stu-id="f008d-250">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="f008d-251">尋找 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="f008d-251">Find Azure Spatial Anchors.</span></span> 
    <span data-ttu-id="f008d-252">當您建立錨點時，應該回到原先放置的位置。</span><span class="sxs-lookup"><span data-stu-id="f008d-252">You should go back to the original place you put it when you created the anchor.</span></span>
    
    9. <span data-ttu-id="f008d-253">刪除 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="f008d-253">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="f008d-254">停止 Azure 會話。</span><span class="sxs-lookup"><span data-stu-id="f008d-254">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="f008d-255">錨定體驗</span><span class="sxs-lookup"><span data-stu-id="f008d-255">Anchoring an experience</span></span>

<span data-ttu-id="f008d-256">在前面幾節中，您已瞭解 Azure 空間錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="f008d-256">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="f008d-257">我們已使用 cube 來呈現父遊戲物件，並將其視覺化為連結的錨點。</span><span class="sxs-lookup"><span data-stu-id="f008d-257">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="f008d-258">在本節中，您將瞭解如何藉由將它放在 ParentAnchor 物件的子系，來錨定整個體驗。</span><span class="sxs-lookup"><span data-stu-id="f008d-258">In this section, you learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="f008d-259">在此範例中，我們會使用在[基底模組第6課](mrlearning-base-ch6.md)期間所建立的陰曆模組元件示範應用程式。</span><span class="sxs-lookup"><span data-stu-id="f008d-259">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="f008d-260">搜尋 "Rocket 啟動器 Complete" prefab，並將它拖曳至您的階層中，做為物件的子系，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f008d-260">Search for the "Rocket Launcher Complete" prefab, and drag it into your hierarchy as a child of the object as shown in the image below.</span></span>

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="f008d-262">定位模組元件體驗，讓 cube 仍然公開，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f008d-262">Position the module assembly experience so that the cube is still exposed as shown in the image below.</span></span> <span data-ttu-id="f008d-263">在應用程式中，使用者可以藉由移動 cube 來重新放置整個體驗。</span><span class="sxs-lookup"><span data-stu-id="f008d-263">In the application, users may reposition the entire experience by moving the cube.</span></span> 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> <span data-ttu-id="f008d-265">注意：有各種不同的使用者體驗流程可用於重新置放體驗，包括使用按鈕來切換環繞體驗的周框方塊、使用重新置放的物件（例如在此步驟中使用的 cube）、使用位置和旋轉gizmos，還有更多。</span><span class="sxs-lookup"><span data-stu-id="f008d-265">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f008d-266">恭喜！</span><span class="sxs-lookup"><span data-stu-id="f008d-266">Congratulations</span></span>
<span data-ttu-id="f008d-267">在本教學課程中，您已瞭解 Azure 空間錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="f008d-267">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="f008d-268">這一課提供了數個按鈕，可讓您探索啟動和停止 Azure 會話，以及在單一裝置上建立、上傳和下載 azure 錨點所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="f008d-268">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="f008d-269">在下一課中，我們將瞭解如何將 Azure 錨點識別碼儲存至 HoloLens 2 進行抓取，即使在應用程式重新開機之後也一樣。</span><span class="sxs-lookup"><span data-stu-id="f008d-269">In the next lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="f008d-270">在此系列中，您也將瞭解如何在多個裝置之間傳輸錨點識別碼，以達成空間對齊，並瞭解多使用者共用會話，即將推出做為共用教學課程的一部分。</span><span class="sxs-lookup"><span data-stu-id="f008d-270">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and learn about multi-user shared sessions, forthcoming as part of Sharing tutorial.</span></span>

[<span data-ttu-id="f008d-271">下一課： 2. 儲存、正在抓取和共用 Azure 空間錨點</span><span class="sxs-lookup"><span data-stu-id="f008d-271">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

