---
title: 多使用者功能教學課程 - 2。 準備 Unity 以進行開發
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031234"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="af93e-105">2.準備 Unity 以進行開發</span><span class="sxs-lookup"><span data-stu-id="af93e-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="af93e-106">在本教學課程中，您將了解如何準備和設定 Unity 來開發應用程式，包括匯入混合實境工具組、設定組建設定，以及準備您的場景。</span><span class="sxs-lookup"><span data-stu-id="af93e-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="af93e-107">目標</span><span class="sxs-lookup"><span data-stu-id="af93e-107">Objectives</span></span>

* <span data-ttu-id="af93e-108">設定 Unity 以用於應用程式開發</span><span class="sxs-lookup"><span data-stu-id="af93e-108">Configure Unity for application development</span></span>
* <span data-ttu-id="af93e-109">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="af93e-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="af93e-110">準備您的專案場景</span><span class="sxs-lookup"><span data-stu-id="af93e-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="af93e-111">指示</span><span class="sxs-lookup"><span data-stu-id="af93e-111">Instructions</span></span>

1. <span data-ttu-id="af93e-112">按一下[這裡](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)，下載並儲存混合實境工具組的基礎 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="af93e-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="af93e-113">在 Unity 中，按一下 [資產] 功能表並選取 [匯入套件]，然後按一下 [自訂套件]。</span><span class="sxs-lookup"><span data-stu-id="af93e-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="af93e-115">從步驟 1 所提供的連結中，選取您剛才下載的 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="af93e-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="af93e-116">當 Unity 中出現匯入快顯視窗時，按一下 [匯入] 按鈕以開始匯入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="af93e-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="af93e-117">這可能需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="af93e-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="af93e-119">下載的套件會位在您的本機資料夾中，也就是您儲存該檔案的地方。</span><span class="sxs-lookup"><span data-stu-id="af93e-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="af93e-120">上圖不會說明您套件的所在位置。</span><span class="sxs-lookup"><span data-stu-id="af93e-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="af93e-121">匯入套件之後，應該會出現 [MRTK 專案設定程式] 視窗。</span><span class="sxs-lookup"><span data-stu-id="af93e-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="af93e-122">如果沒有，請在 Unity 功能表中選取 [混合現實工具組] > [公用程式] > [設定 Unity 專案] 加以開啟。</span><span class="sxs-lookup"><span data-stu-id="af93e-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="af93e-123">在 [MRTK 專案設定程式] 視窗中，展開 [修改設定] 區段，取消勾選 [啟用適用於 Unity 的 MSBuild] 核取方塊，確定已勾選所有其他選項，然後按一下 [套用] 按鈕來套用設定。</span><span class="sxs-lookup"><span data-stu-id="af93e-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="af93e-125">適用於 Unity 的 MSBuild 可能不支援您將使用的所有 SDK，且在啟用之後，可能會很難停用。</span><span class="sxs-lookup"><span data-stu-id="af93e-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="af93e-126">因此，強烈建議您不要啟用適用於 Unity 的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="af93e-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="af93e-127">建立新場景。</span><span class="sxs-lookup"><span data-stu-id="af93e-127">Create a new scene.</span></span> <span data-ttu-id="af93e-128">這可以藉由按一下 [檔案] 並選取 [新增場景] 來完成。</span><span class="sxs-lookup"><span data-stu-id="af93e-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="af93e-129">將其儲存為 HLSharedProjectMain。</span><span class="sxs-lookup"><span data-stu-id="af93e-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="af93e-130">在 [混合時竟工具組] 底下，按一下 [新增至場景並設定]。</span><span class="sxs-lookup"><span data-stu-id="af93e-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="af93e-132">完成後，請從階層中選取 [混合現實工具組 (MRTK)]。</span><span class="sxs-lookup"><span data-stu-id="af93e-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="af93e-133">在 [偵測器] 面板中，將 MRTK 組態設定檔變更為 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="af93e-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="af93e-135">從階層中選取 [混合實境工具組 (MRTK)]。</span><span class="sxs-lookup"><span data-stu-id="af93e-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="af93e-136">在偵測器面板中尋找 [混合實境工具組指令碼]，然後按 [複製與自訂] 按鈕，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="af93e-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="af93e-137">此時會出現一個快顯示窗，在快顯功能表中選取 [複製] 選項。</span><span class="sxs-lookup"><span data-stu-id="af93e-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="af93e-140">如果您想要隱藏診斷視窗，請向下捲動並取消核取 [啟用診斷系統]。</span><span class="sxs-lookup"><span data-stu-id="af93e-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="af93e-141">建議您在應用程式開發期間讓診斷視窗保持啟用狀態，以監視效能，然後在生產環境或應用程式示範期間將其停用。</span><span class="sxs-lookup"><span data-stu-id="af93e-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="af93e-143">按 ctrl + shift + B，或移至 [檔案] -> [組建設定]，以開啟組建設定。</span><span class="sxs-lookup"><span data-stu-id="af93e-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="af93e-144">請注意，程式目前可在 PC、Mac 和 Linux 獨立平台下設定。</span><span class="sxs-lookup"><span data-stu-id="af93e-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="af93e-145">若是進行 HoloLens 2 開發，請將平台設定為通用 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="af93e-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="af93e-146">選取該項目，然後按一下 [切換平台]。</span><span class="sxs-lookup"><span data-stu-id="af93e-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="af93e-148">完成後，按一下名為 [新增開啟場景] 的方塊。</span><span class="sxs-lookup"><span data-stu-id="af93e-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="af93e-149">現在，移至偵測器面板，並確定已核取 [支援的虛擬實境] 右邊的核取方塊 (如下圖所示)。</span><span class="sxs-lookup"><span data-stu-id="af93e-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="af93e-150">此外，也請確定 [場景/HLSharedProjectMain] 旁的核取方塊也已核取，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="af93e-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="af93e-152">在 [偵測器] 面板的 [發佈設定] 區段下，向下捲動至 [功能]，並確定已核取下列核取方塊：</span><span class="sxs-lookup"><span data-stu-id="af93e-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="af93e-154">匯入列出的自訂套件：</span><span class="sxs-lookup"><span data-stu-id="af93e-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="af93e-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (2.1.1 版)</span><span class="sxs-lookup"><span data-stu-id="af93e-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="af93e-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="af93e-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="af93e-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="af93e-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="af93e-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="af93e-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="af93e-159">如需有關如何為 Azure Spatial Anchors 設定 Unity 專案的提示，您可以參閱[開始使用 Azure Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) 教學課程，這是 [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) 教學課程系列的一部分。</span><span class="sxs-lookup"><span data-stu-id="af93e-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="af93e-160">在 [專案] 面板中，移至 [Prefabs] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="af93e-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="af93e-161">在下列步驟中，您將會在場景中實作幾個 Prefab。</span><span class="sxs-lookup"><span data-stu-id="af93e-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="af93e-162">在 [Prefabs] 資料夾中，按一下 [Debug Window] Prefab 並將其拖曳至階層中。</span><span class="sxs-lookup"><span data-stu-id="af93e-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="af93e-163">完成後，依序按一下 [檔案] 和 [儲存] 或按 Ctrl + S 來儲存專案。</span><span class="sxs-lookup"><span data-stu-id="af93e-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="af93e-165">您可能會注意到當您按一下 Prefab 時，會出現快顯視窗來詢問您有關 TMP Essentials 的資訊。</span><span class="sxs-lookup"><span data-stu-id="af93e-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="af93e-166">請視需要按一下 [匯入 TMP Essentials]。</span><span class="sxs-lookup"><span data-stu-id="af93e-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="af93e-167">如果出現此快顯視窗，表示您可能需要從階層中刪除 Prefab，然後將其重新拖曳到您的階層中，以避免潛在的文字相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="af93e-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="af93e-169">恭喜！</span><span class="sxs-lookup"><span data-stu-id="af93e-169">Congratulations</span></span>

<span data-ttu-id="af93e-170">您的 Unity 專案現在已準備好用於 Photon。</span><span class="sxs-lookup"><span data-stu-id="af93e-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="af93e-171">在接下來的教學課程中，我們將以這個場景和 Unity 專案為基礎來建立完整的共用體驗。</span><span class="sxs-lookup"><span data-stu-id="af93e-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="af93e-172">[下一個教學課程：3.連線多個使用者](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="af93e-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
