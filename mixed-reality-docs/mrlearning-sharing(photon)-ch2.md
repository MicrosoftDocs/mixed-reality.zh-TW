---
title: 多使用者功能教學課程-2。 讓 Unity 準備好進行開發
description: 完成此課程，以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 6abf4fa8fc87afc7007d6f7c76becfbd88ed7a12
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901509"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="c8ab4-105">2. 讓 Unity 準備好進行開發</span><span class="sxs-lookup"><span data-stu-id="c8ab4-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="c8ab4-106">在本教學課程中，您將瞭解如何為應用程式開發準備和設定 Unity，包括匯入混合現實工具組、設定組建設定，以及準備您的場景。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="c8ab4-107">目標</span><span class="sxs-lookup"><span data-stu-id="c8ab4-107">Objectives</span></span>

* <span data-ttu-id="c8ab4-108">設定 Unity 以進行應用程式開發</span><span class="sxs-lookup"><span data-stu-id="c8ab4-108">Configure Unity for application development</span></span>
* <span data-ttu-id="c8ab4-109">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="c8ab4-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="c8ab4-110">準備您的專案場景</span><span class="sxs-lookup"><span data-stu-id="c8ab4-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="c8ab4-111">指示</span><span class="sxs-lookup"><span data-stu-id="c8ab4-111">Instructions</span></span>

1. <span data-ttu-id="c8ab4-112">按一下這裡，下載並儲存 Mixed Reality 工具組 Foundation unity 封裝[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="c8ab4-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="c8ab4-113">在 Unity 中，按一下 [資產] 功能表並選取 [匯入套件]，然後按一下 [自訂套件]。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="c8ab4-115">從步驟1所提供的連結中，選取您剛才下載的 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="c8ab4-116">在 Unity 中出現 [匯入] 快顯視窗後，按一下 [匯入] 按鈕以開始匯入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="c8ab4-117">這可能需要數分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="c8ab4-119">下載的套件位於您的本機資料夾中，您已在其中儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="c8ab4-120">上圖不會說明您會在何處找到封裝。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="c8ab4-121">建立新場景。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-121">Create a new scene.</span></span> <span data-ttu-id="c8ab4-122">這可以藉由按一下 [檔案] 並選取 [新增場景] 來完成。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="c8ab4-123">將它儲存為 HLSharedProjectMain。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-123">Save it as HLSharedProjectMain.</span></span>

    <span data-ttu-id="c8ab4-124">您可能會收到類似下圖的快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-124">You may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="c8ab4-125">現在，請按一下 [否]。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-125">For now, click No.</span></span>
    <span data-ttu-id="c8ab4-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span><span class="sxs-lookup"><span data-stu-id="c8ab4-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span></span>

5. <span data-ttu-id="c8ab4-127">在 [混合式現實工具組] 底下，按一下 [新增至場景] 並設定。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="c8ab4-129">完成之後，就會出現新的設定檔案，讓您選擇自訂設定檔。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="c8ab4-131">從階層中選取 [混合現實工具組（MRTK）]。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="c8ab4-132">在 [偵測器] 面板中，尋找 Mixed Reality 工具組腳本，然後按下圖所示的 [複製 & 自訂] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="c8ab4-133">這會出現一個 pop，然後在快顯功能表中選取 [複製] 選項。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="c8ab4-136">如果您想要隱藏 [診斷] 視窗，請向下選取並取消核取 [啟用診斷系統]。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="c8ab4-137">建議您在應用程式開發期間讓診斷視窗保持啟用狀態，以監視效能，然後在生產或應用程式示範期間將它停用。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="c8ab4-139">按 ctrl + shift + B，或移至 [檔案-> 組建設定]，以開啟組建設定。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="c8ab4-140">請注意，程式目前是在電腦、Mac 和 Linux 獨立平臺下設定。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="c8ab4-141">若是 HoloLens 2 開發，請將平臺設定為通用 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="c8ab4-142">選取該檔案，然後按一下 [切換平臺]。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-142">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="c8ab4-144">完成後，按一下名為 [新增] [開啟場景] 的方塊。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="c8ab4-145">現在，移至 [偵測器] 面板，並確定已核取 [支援的虛擬實境] 右邊的核取方塊（如下圖所示）。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="c8ab4-146">此外，也請確定 [場景/HLSharedProjectMain] 旁的核取方塊也已核取，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="c8ab4-148">在 [偵測器] 面板的 [發行設定] 區段下，向下流覽至 [功能]，並確定已將下列核取方塊標記為：</span><span class="sxs-lookup"><span data-stu-id="c8ab4-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="c8ab4-150">匯入列出的自訂套件：</span><span class="sxs-lookup"><span data-stu-id="c8ab4-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="c8ab4-151">a.</span><span class="sxs-lookup"><span data-stu-id="c8ab4-151">a.</span></span> <span data-ttu-id="c8ab4-152">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) （版本2.0.0）</span><span class="sxs-lookup"><span data-stu-id="c8ab4-152">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>

    <span data-ttu-id="c8ab4-153">b。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-153">b.</span></span> [<span data-ttu-id="c8ab4-154">MRTK.HoloLens2 GettingStarted. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="c8ab4-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)

    <span data-ttu-id="c8ab4-155">c.</span><span class="sxs-lookup"><span data-stu-id="c8ab4-155">c.</span></span> [<span data-ttu-id="c8ab4-156">MRTK.HoloLens2 AzureSpatialAnchors. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="c8ab4-156">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

    <span data-ttu-id="c8ab4-157">d.</span><span class="sxs-lookup"><span data-stu-id="c8ab4-157">d.</span></span> [<span data-ttu-id="c8ab4-158">MRTK.HoloLens2 MultiUserCapabilities. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="c8ab4-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="c8ab4-159">如需有關如何為 Azure 空間錨點設定 Unity 專案的提醒，您可以參閱[azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)空間錨點教學課程系列的「[開始使用 Azure 空間錨點](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)」教學課程。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. <span data-ttu-id="c8ab4-161">在 [專案] 面板中，移至 [Prefabs] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-161">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="c8ab4-162">在下列步驟中，您將會在場景中執行幾個 prefabs。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-162">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="c8ab4-163">在 [Prefabs] 資料夾中，按一下 [prefab]、[Debug] 視窗並拖曳至階層中。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-163">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="c8ab4-164">完成後，依序按一下 [檔案] 和 [儲存] 或按 Ctrl + S 來儲存專案。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-164">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="c8ab4-166">您可能會注意到當您按一下 prefab 時，快顯視窗會詢問您有關 TMP Essentials 的資訊。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-166">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="c8ab4-167">視需要按一下 [匯入 TMP Essentials]。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-167">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="c8ab4-168">如果出現這個快顯視窗，您可能需要從階層中刪除 prefab，然後將它重新拖曳到您的階層中，以避免潛在的文字相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-168">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="c8ab4-170">恭喜您</span><span class="sxs-lookup"><span data-stu-id="c8ab4-170">Congratulations</span></span>

<span data-ttu-id="c8ab4-171">您的 Unity 專案現在已準備好進行 Photon。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-171">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="c8ab4-172">在接下來的教學課程中，我們將以這個場景和 Unity 專案為完整的共用體驗來建立。</span><span class="sxs-lookup"><span data-stu-id="c8ab4-172">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="c8ab4-173">[下一個教學課程： 3. 連接多個使用者](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="c8ab4-173">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
