---
title: MR 學習 ASA 模組上 HoloLens 2 Azure 空間的錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326672"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a><span data-ttu-id="b2209-104">Getting Started with Azure HoloLens 2 上的空間錨點</span><span class="sxs-lookup"><span data-stu-id="b2209-104">Getting Started with Azure Spatial Anchors on HoloLens 2</span></span>

<span data-ttu-id="b2209-105">歡迎來到 HoloLens 2 教學課程的第二個模組 ！</span><span class="sxs-lookup"><span data-stu-id="b2209-105">Welcome to the second module of the HoloLens 2 Tutorial!</span></span> <span data-ttu-id="b2209-106">開始之前，務必讓所有的[必要條件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)完成。</span><span class="sxs-lookup"><span data-stu-id="b2209-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="b2209-107">如果您尚未完成第一個[基底模組](mrlearning-base.md)，我們強烈建議您先完成該第一個。</span><span class="sxs-lookup"><span data-stu-id="b2209-107">If you have not completed the first, [base module](mrlearning-base.md) yet, we highly recommend that you complete that first.</span></span> <span data-ttu-id="b2209-108">如果您從新的 unity 專案，請依照下列中的新專案建立步驟[基底模組](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="b2209-108">If you are starting from a new unity project, follow the new project creation steps in the [base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="b2209-109">目標</span><span class="sxs-lookup"><span data-stu-id="b2209-109">Objectives</span></span>

* <span data-ttu-id="b2209-110">了解使用 Azure 空間的錨點標記 HoloLens 2 開發基礎</span><span class="sxs-lookup"><span data-stu-id="b2209-110">Learn the fundamentals of developing with Azure Spatial Anchors with the HoloLens 2</span></span>

* <span data-ttu-id="b2209-111">建立、 上傳，並下載空間的錨點</span><span class="sxs-lookup"><span data-stu-id="b2209-111">Create, Upload, and Download Spatial Anchors</span></span>

  

## <a name="instructions"></a><span data-ttu-id="b2209-112">指示</span><span class="sxs-lookup"><span data-stu-id="b2209-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="b2209-113">下載和匯入資產</span><span class="sxs-lookup"><span data-stu-id="b2209-113">Downloading and Importing Assets</span></span>
<span data-ttu-id="b2209-114">在開始之前，您必須下載並匯入下列資產：</span><span class="sxs-lookup"><span data-stu-id="b2209-114">Before beginning, you must download and import the following assets:</span></span>

[<span data-ttu-id="b2209-115">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="b2209-115">Azure Spatial Anchors</span></span>](https://github.com/azure/azure-spatial-anchors-samples/releases)

[<span data-ttu-id="b2209-116">MR 基底模組資產套件</span><span class="sxs-lookup"><span data-stu-id="b2209-116">MR Base module Asset Pack</span></span>](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[<span data-ttu-id="b2209-117">ASA 模組資產套件</span><span class="sxs-lookup"><span data-stu-id="b2209-117">ASA module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[<span data-ttu-id="b2209-118">混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="b2209-118">Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> <span data-ttu-id="b2209-119">注意： 請參閱步驟 5 中的特定指示匯入 Azure 空間的錨點，步驟 6 的特定指示需 MR 基底模組資產套件和步驟 3 到 4 的特殊指示混合實境工具組。</span><span class="sxs-lookup"><span data-stu-id="b2209-119">Note: see step 5 for specific instructions on how to import the Azure Spatial Anchors, step 6 for specific instructions on the MR Base module Asset Pack, and steps 3-4 for specific instructions on the Mixed Reality Toolkit.</span></span>

1. <span data-ttu-id="b2209-120">在專案中建立新的場景。</span><span class="sxs-lookup"><span data-stu-id="b2209-120">create a new scene in your project.</span></span> <span data-ttu-id="b2209-121">以滑鼠右鍵按一下您的場景資料夾，按一下 [建立]，然後場景。</span><span class="sxs-lookup"><span data-stu-id="b2209-121">Right click your scene folder, click "create," then scene.</span></span> <span data-ttu-id="b2209-122">命名新的場景"ASALearningmodule。 」</span><span class="sxs-lookup"><span data-stu-id="b2209-122">Name the new scene "ASALearningmodule."</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="b2209-124">按兩下 「 ASALearningmodule"以查看一些預先定義的項目出現以及新的場景。</span><span class="sxs-lookup"><span data-stu-id="b2209-124">Double click "ASALearningmodule" to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="b2209-125">設定適用於混合的實境開發場景。</span><span class="sxs-lookup"><span data-stu-id="b2209-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="b2209-127">注意:您會看到快顯視窗，指出: 「 您必須選擇檔案的混合實境工具組 」。</span><span class="sxs-lookup"><span data-stu-id="b2209-127">Note: You will see a pop-up that says, "you must choose a file for the Mixed Reality Toolkit."</span></span> <span data-ttu-id="b2209-128">按一下 [確定] 會帶您前往步驟 4。</span><span class="sxs-lookup"><span data-stu-id="b2209-128">Clicking "ok" will bring you to step 4.</span></span>

4. <span data-ttu-id="b2209-129">當選擇混合實境工具組的檔案，選取，"DefaultMixedRealityToolkitConfigurationProfile。 」</span><span class="sxs-lookup"><span data-stu-id="b2209-129">When choosing a file for the Mixed Reality Toolkit, select, "DefaultMixedRealityToolkitConfigurationProfile."</span></span>

   > <span data-ttu-id="b2209-130">注意:如果您有自己的組態設定檔自由，改為使用。</span><span class="sxs-lookup"><span data-stu-id="b2209-130">Note: If you have your own configuration profile feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="b2209-132">混合實境現在設定場景。</span><span class="sxs-lookup"><span data-stu-id="b2209-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="b2209-133">請確定您將場景 （使用其中一個控制項執行此作業 / 命令 + S 鍵，或按一下檔案，然後按一下 儲存）。</span><span class="sxs-lookup"><span data-stu-id="b2209-133">Make sure you save your scene (do this with either control/command+S, or click on file, then click on save).</span></span> 

5. <span data-ttu-id="b2209-134">匯入[Azure 空間的錨點](https://github.com/azure/azure-spatial-anchors-samples/releases)。</span><span class="sxs-lookup"><span data-stu-id="b2209-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="b2209-135">若要使用空間的錨點，您必須匯入此資產。</span><span class="sxs-lookup"><span data-stu-id="b2209-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="b2209-136">因此，按一下上方的連結，並以滑鼠右鍵按一下 「 AzureSpatialAnchors.unitypackage。 」</span><span class="sxs-lookup"><span data-stu-id="b2209-136">So, click on the link above and right click on "AzureSpatialAnchors.unitypackage."</span></span> <span data-ttu-id="b2209-137">按一下 另存目標為"，並將它儲存到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="b2209-137">Click on "save target as" and save it to your computer.</span></span> 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   <span data-ttu-id="b2209-139">然後，儲存之後，移至 unity，按一下 「 資產 」 移至 [匯入封裝]，然後按一下 [自訂的套件...]會開啟您電腦的檔案。</span><span class="sxs-lookup"><span data-stu-id="b2209-139">Then, after it's saved, go back into unity, click "assets," go down to "import package," then click "custom package..." Your computer files will open up.</span></span> <span data-ttu-id="b2209-140">一次在執行，尋找您儲存 Azure 空間的錨點的套件並加以選取。</span><span class="sxs-lookup"><span data-stu-id="b2209-140">Once they do, find where you saved the Azure Spatial Anchors package and select it.</span></span> <span data-ttu-id="b2209-141">然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="b2209-141">Then click "open."</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   <span data-ttu-id="b2209-143">現在會快顯功能表提供的工具和設定，要求您要匯入的項目清單。</span><span class="sxs-lookup"><span data-stu-id="b2209-143">Now there will be a popup giving a list of tools and settings, asking you what to import.</span></span> <span data-ttu-id="b2209-144">選取 ***所有***可用的選項，然後按一下 「 匯入。 」</span><span class="sxs-lookup"><span data-stu-id="b2209-144">Select ***all*** of the options available, then click "import."</span></span>

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > <span data-ttu-id="b2209-146">注意： 需要幾分鐘的時間匯入 」，因此請耐心等候。</span><span class="sxs-lookup"><span data-stu-id="b2209-146">note: it will take a few minutes to import, so please be patient.</span></span> 

   6. <span data-ttu-id="b2209-147">匯入[MR 基底模組資產套件](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)下一步。</span><span class="sxs-lookup"><span data-stu-id="b2209-147">Import [MR Base module Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) next.</span></span> <span data-ttu-id="b2209-148">如同步驟 5 中，按一下上方的連結，然後以滑鼠右鍵按一下 「 BasemoduleAssetsV1 1.unitypackage 」 並按一下 另存目標為"，並將它儲存到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="b2209-148">Much like step 5, click the link above, then right click "BasemoduleAssetsV1 1.unitypackage" and click "save target as" and save it to your computer.</span></span>

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > <span data-ttu-id="b2209-150">秘訣：儲存所有這些資產的相同資料夾中，使其更輕鬆地尋找及存取。</span><span class="sxs-lookup"><span data-stu-id="b2209-150">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="b2209-151">美觀且妥善管理，則會保留所有項目 ！</span><span class="sxs-lookup"><span data-stu-id="b2209-151">It will keep everything nice and organized!</span></span>

   <span data-ttu-id="b2209-152">步驟 5，請移至 unity，在按一下時，如同 「 資產 」，停留在 [匯入封裝]，然後按一下 [自訂的套件...]您電腦的檔案應該會再次出現，因此請移至您儲存此基本模組資產套件並加以選取。</span><span class="sxs-lookup"><span data-stu-id="b2209-152">Just like step 5, go back in to unity, click "assets," hover over "import package" then click "custom package..." Your computer files should appear again, so go to where you stored the Base module Asset Pack and select it.</span></span> <span data-ttu-id="b2209-153">然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="b2209-153">Then click "open."</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > <span data-ttu-id="b2209-155">注意： 可能會稍後在此模組所需的多個資產。</span><span class="sxs-lookup"><span data-stu-id="b2209-155">Note: there may be more assets needed later in this module.</span></span> <span data-ttu-id="b2209-156">請遵循下列步驟來匯入從這裡開始所述的任何資產。</span><span class="sxs-lookup"><span data-stu-id="b2209-156">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="b2209-157">匯入 ASA 模組組件使用相同的方法為匯入前的套件。</span><span class="sxs-lookup"><span data-stu-id="b2209-157">Import the ASA module Pack using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="b2209-158">設定場景</span><span class="sxs-lookup"><span data-stu-id="b2209-158">Configuring your scene</span></span>

<span data-ttu-id="b2209-159">在本節中，我們將新增 prefabs 和指令碼到場景方向，以建立一系列的示範基本概念的本機的錨點和 Azure 空間的錨點的行為方式的應用程式中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="b2209-159">In this section, we will be adding prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

7. <span data-ttu-id="b2209-160">在 專案 索引標籤底下的 「 資產 」 資料夾中，按一下 「 ASAmoduleAssets。 」</span><span class="sxs-lookup"><span data-stu-id="b2209-160">In the "project" tab, underneath the "assets" folder, click on "ASAmoduleAssets."</span></span> <span data-ttu-id="b2209-161">一次選取的是您會看到 2 prefabs"ButtonParent"和"ParentAnchor。 」</span><span class="sxs-lookup"><span data-stu-id="b2209-161">Once selected you will see 2 prefabs, "ButtonParent" and "ParentAnchor."</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. <span data-ttu-id="b2209-163">將這兩個 prefabs 拖曳到場景。</span><span class="sxs-lookup"><span data-stu-id="b2209-163">Drag both of the prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. <span data-ttu-id="b2209-165">按兩下父錨點，以選取它。</span><span class="sxs-lookup"><span data-stu-id="b2209-165">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="b2209-166">您可能需要調整您的檢視，若要查看整個場景，因此視需要調整您的場景。</span><span class="sxs-lookup"><span data-stu-id="b2209-166">You may need to adjust your view to see the entire scene, so adjust your scene as needed.</span></span>

    <span data-ttu-id="b2209-167">熟悉 ParentAnchor prefab。</span><span class="sxs-lookup"><span data-stu-id="b2209-167">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="b2209-168">目前，名為"ParentAnchor 」 遊戲物件是彩色的 cube 中，供示範之用。</span><span class="sxs-lookup"><span data-stu-id="b2209-168">Currently, the game object named "ParentAnchor" is a colored cube, for demonstration purposes.</span></span> <span data-ttu-id="b2209-169">最後，我們將會隱藏的 cube，並將我們的內容放 ParentAnchor 的子系。</span><span class="sxs-lookup"><span data-stu-id="b2209-169">Eventually, we will hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="b2209-170">此 prefab 包含 AzureSpatialAnchorsDemoWrapper.cs 隨附的指令碼 （ASA SDK） 和 ParentAnchor 物件 ASAmoduleScript.cs 指令碼 （包含此模組的一部分）。</span><span class="sxs-lookup"><span data-stu-id="b2209-170">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK) and the ASAmoduleScript.cs script (included as part of this module) to the ParentAnchor object.</span></span> 

10. <span data-ttu-id="b2209-171">設定按鈕。</span><span class="sxs-lookup"><span data-stu-id="b2209-171">Configure Buttons.</span></span> <span data-ttu-id="b2209-172">下 ParentAnchor prefab 中，您會發現許多加上標籤的按鈕。</span><span class="sxs-lookup"><span data-stu-id="b2209-172">Under the ParentAnchor prefab, you will notice several labeled buttons.</span></span> <span data-ttu-id="b2209-173">這些按鈕會從 MRTK PressableButton prefabs 建立。</span><span class="sxs-lookup"><span data-stu-id="b2209-173">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="b2209-174">深入了解如何建立從 Pressable 按鈕[基底模組](mrlearning-base-ch2.md)。</span><span class="sxs-lookup"><span data-stu-id="b2209-174">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="b2209-175">針對每個按鈕，新增當使用者按下或選取下列清單根據按鈕就會觸發的事件。</span><span class="sxs-lookup"><span data-stu-id="b2209-175">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="b2209-176">名為"StartAzureSession 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b2209-176">For the Button named "StartAzureSession", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="b2209-177">ParentAnchor 物件拖曳至空白的欄位，並將指派 StartAzureSession() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="b2209-177">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="b2209-181">名為"StopAzureSession 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b2209-181">For the Button named "StopAzureSession", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="b2209-182">ParentAnchor 物件拖曳至空白的欄位，並將指派 StopAzureSession() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="b2209-182">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="b2209-183">名為"CreateAnchor 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b2209-183">For the Button named "CreateAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="b2209-184">ParentAnchor 物件拖曳至空白的欄位，並將指派 CreateAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="b2209-184">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="b2209-185">名為"開始尋找的錨點 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b2209-185">For the Button named "Start Looking For Anchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="b2209-186">ParentAnchor 物件拖曳至空白的欄位，並將指派 FindAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="b2209-186">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="b2209-187">名為"DeleteAzureAnchor 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b2209-187">For the Button named "DeleteAzureAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="b2209-188">ParentAnchor 物件拖曳至空白的欄位，並將指派 DeleteAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="b2209-188">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="b2209-189">名為 「 刪除本機錨點 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b2209-189">For the Button named "Delete Local Anchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="b2209-190">ParentAnchor 物件拖曳至空白的欄位，並將指派 RemoveLocalAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="b2209-190">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="b2209-191">建置，並示範基底的應用程式</span><span class="sxs-lookup"><span data-stu-id="b2209-191">Build and Demonstrate Base Application</span></span>

<span data-ttu-id="b2209-192">現在，場景設定來示範 Azure 空間的錨點的基本概念，我們會建置及示範 Azure 空間的錨點的基本行為。</span><span class="sxs-lookup"><span data-stu-id="b2209-192">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="b2209-193">如果您已關閉前面幾節中的 [建置設定] 視窗，請移至 [檔案] > [建置設定] 來重新開啟 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b2209-193">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="b2209-194">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="b2209-194">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="b2209-195">藉由按一下 [加入開啟場景] 按鈕，來確定您想要嘗試的場景有在 [建置中的場景] 清單中。</span><span class="sxs-lookup"><span data-stu-id="b2209-195">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="b2209-196">按下 [建置] 按鈕，開始建置程序。</span><span class="sxs-lookup"><span data-stu-id="b2209-196">Press the Build button to begin the build process.</span></span>
    <span data-ttu-id="b2209-197">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="b2209-197">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="b2209-198">為您的應用程式建立並命名新資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2209-198">Create and name a new folder for your application.</span></span> <span data-ttu-id="b2209-199">在下圖中，已建立名為 “App” 的資料夾來包含應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2209-199">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="b2209-200">按一下 [選取資料夾]，即可開始對新建立的資料夾進行建置。</span><span class="sxs-lookup"><span data-stu-id="b2209-200">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="b2209-201">建置完成之後，您可以關閉 Unity 中的 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b2209-201">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 
    <span data-ttu-id="b2209-202">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="b2209-202">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="b2209-203">注意：如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。</span><span class="sxs-lookup"><span data-stu-id="b2209-203">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="b2209-204">如果您看到錯誤，例如「錯誤：CS0246 = 找不到"XX"的輸入或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？) 」，則您可能需要安裝[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="b2209-204">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="b2209-205">在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="b2209-205">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="b2209-206">按兩下 “MixedRealityBase.sln” 解決方案 (或是相對應名稱，如果您為專案使用替代名稱的話)，以在 Visual Studio 中開啟解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="b2209-206">Double click on the “MixedRealityBase.sln” solution (or the corresponding name, if you used an alternative name for your project) to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="b2209-207">注意:請務必開啟新建立的資料夾 (如果您遵循先前步驟中的命名慣例，此資料夾為 "App" 資料夾)，因為該資料夾外會有名稱類似的 .sln 檔案，不應與建置資料夾中的 .sln 檔案混淆。</span><span class="sxs-lookup"><span data-stu-id="b2209-207">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > <span data-ttu-id="b2209-209">注意:如果 visual studio 會要求安裝新的元件，請花一些時間來確保所有必要的元件會安裝在為特定[[安裝工具] 頁面](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="b2209-209">Note: If visual studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="b2209-210">使用 USB 纜線，將 HoloLens 2 插入您的電腦。</span><span class="sxs-lookup"><span data-stu-id="b2209-210">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="b2209-211">雖然這些課程指示假設您要部署測試與 HoloLens 2 裝置，您也可以選擇將部署到[HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[側載應用程式套件](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="b2209-211">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="b2209-212">對您的裝置進行建置之前，請確定裝置處於開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="b2209-212">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="b2209-213">如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。</span><span class="sxs-lookup"><span data-stu-id="b2209-213">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="b2209-214">若要啟用開發人員模式，或與 Visual Studio 配對，請遵循[這些指示](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="b2209-214">Please follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="b2209-215">若要設定 Visual Studio 來對 HoloLens 2 進行建置，請選取 [發行] 組態和 [ARM] 架構。</span><span class="sxs-lookup"><span data-stu-id="b2209-215">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>
    <span data-ttu-id="b2209-216">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="b2209-216">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
    
9. <span data-ttu-id="b2209-217">最後一個步驟是建置到您的裝置，選取 偵錯 > 啟動但不偵錯。</span><span class="sxs-lookup"><span data-stu-id="b2209-217">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="b2209-218">選取 [啟動但不偵錯] 會讓裝置上的應用程式在建置成功時立即啟動，但 Visual Studio 中不會出現偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="b2209-218">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="b2209-219">這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。</span><span class="sxs-lookup"><span data-stu-id="b2209-219">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="b2209-220">您也可以選取 [建置] > [部署解決方案]，在不自動啟動應用程式的情況下，對您的裝置進行部署。</span><span class="sxs-lookup"><span data-stu-id="b2209-220">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
    <span data-ttu-id="b2209-221">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="b2209-221">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
    
10. <span data-ttu-id="b2209-222">當您的裝置上執行應用程式時，請遵循螢幕上的指示。</span><span class="sxs-lookup"><span data-stu-id="b2209-222">When the application is running on your device, please follow the on-screen instructions.</span></span> <span data-ttu-id="b2209-223">請按下列步驟對應的場景按鈕。</span><span class="sxs-lookup"><span data-stu-id="b2209-223">Please press the scene buttons corresponding to the Steps below.</span></span>
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="b2209-225">啟動 Azure 空間的錨點的工作階段。</span><span class="sxs-lookup"><span data-stu-id="b2209-225">Start the Azure spatial anchors session.</span></span>
    
    2. <span data-ttu-id="b2209-226">移到不同位置的 cube。</span><span class="sxs-lookup"><span data-stu-id="b2209-226">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="b2209-227">儲存 Azure 空間的錨點，在 cube 的位置。</span><span class="sxs-lookup"><span data-stu-id="b2209-227">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="b2209-228">停止 Azure 空間的錨點的工作階段。</span><span class="sxs-lookup"><span data-stu-id="b2209-228">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="b2209-229">移除本機 cube，就可以讓使用者移動 cube 上的錨點。</span><span class="sxs-lookup"><span data-stu-id="b2209-229">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    6. <span data-ttu-id="b2209-230">移動其他地方的 cube。</span><span class="sxs-lookup"><span data-stu-id="b2209-230">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="b2209-231">啟動 Azure 空間的錨點的工作階段。</span><span class="sxs-lookup"><span data-stu-id="b2209-231">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="b2209-232">尋找 Azure 空間的錨點。</span><span class="sxs-lookup"><span data-stu-id="b2209-232">Find Azure spatial anchors.</span></span>
    <span data-ttu-id="b2209-233">（cube 應該返回到原始位置，現在您將它放在建立錨點時）。</span><span class="sxs-lookup"><span data-stu-id="b2209-233">(now cube should go back to the original place you put it when you created the anchor).</span></span>
    9. <span data-ttu-id="b2209-234">刪除 Azure 空間的錨點。</span><span class="sxs-lookup"><span data-stu-id="b2209-234">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="b2209-235">停止 Azure 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b2209-235">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="b2209-236">錨定的體驗</span><span class="sxs-lookup"><span data-stu-id="b2209-236">Anchoring an experience</span></span>

<span data-ttu-id="b2209-237">在先前章節中，您已了解 Azure 空間的錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="b2209-237">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="b2209-238">我們使用 cube 來表示，並且將視覺化父代遊戲物件，具有附加的錨點。</span><span class="sxs-lookup"><span data-stu-id="b2209-238">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="b2209-239">在本節中，您 wiill 了解如何將其放 ParentAnchor 物件的子系的錨點整個的體驗。</span><span class="sxs-lookup"><span data-stu-id="b2209-239">In this section, you wiill learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="b2209-240">此範例中，我們將使用農曆模組組件示範應用程式期間所建立[第 6 課的基本模組](mrlearning-base-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="b2209-240">For this example, we will use the Lunar module Assembly demo app that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="b2209-241">搜尋農曆模組組件完整 prefab，並將它拖曳到您的階層做為子系的 AnchorParent gameobject，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b2209-241">Search for the Lunar module Assembly Complete prefab and drag it into your heirarchy as a child of the AnchorParent gameobject, as shown in the image below.</span></span>

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="b2209-243">定位的方式，仍會公開 cube，模組組件的體驗，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b2209-243">Position the module assembly experience in such a way that the cube is still exposed, as shown in the image below.</span></span> <span data-ttu-id="b2209-244">在應用程式，使用者可能會重新定位整個體驗，藉由移動 cube。</span><span class="sxs-lookup"><span data-stu-id="b2209-244">In the application, users may reposition the entire experience by moving the cube.</span></span> 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > <span data-ttu-id="b2209-246">注意:有各種不同的重新定位體驗，包括使用按鈕來切換週框方塊括住的經驗，使用 （例如，在此步驟中所用的 cube)，重新調整物件的位置和旋轉的 gizmo 使用的使用者體驗流程等等。</span><span class="sxs-lookup"><span data-stu-id="b2209-246">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b2209-247">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b2209-247">Congratulations</span></span>
<span data-ttu-id="b2209-248">在這一課，您已了解 Azure 空間的錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="b2209-248">In this Lesson, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="b2209-249">本課程中提供了幾個按鈕，可讓您探索各種不同的步驟，才能啟動和停止 Azure 工作階段，並建立、 上傳及下載 azure 的錨點，單一裝置上。</span><span class="sxs-lookup"><span data-stu-id="b2209-249">This Lesson provided you with several buttons allowing you to explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="b2209-250">在下一課中，我們將學習如何將 Azure 的錨點識別碼儲存至擷取，您 HoloLens 2，即使重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2209-250">In the next Lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="b2209-251">在系列中，您將也了解如何達成空間的對齊方式、 多個裝置之間傳輸錨點識別碼和最終了解多使用者共用工作階段 （即將推出的共用模組一部分）。</span><span class="sxs-lookup"><span data-stu-id="b2209-251">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and eventually learn about multi-user shared sessions (forthcoming as part of sharing module.)</span></span>

[<span data-ttu-id="b2209-252">下一課：ASA Lesson 2</span><span class="sxs-lookup"><span data-stu-id="b2209-252">Next Lesson: ASA Lesson 2</span></span>](mrlearning-asa-ch2.md)

