---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 957813d24de95aad52c26b4bd0f0996a60d01358
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327340"
---
# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="e836a-104">**準備 Unity 進行開發**</span><span class="sxs-lookup"><span data-stu-id="e836a-104">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="e836a-105">在這一課中，我們將了解如何準備及設定 Unity 以應用程式開發，包括匯入混合實境工具組、 設定組建設定，並準備我們的場景。</span><span class="sxs-lookup"><span data-stu-id="e836a-105">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="e836a-106">目標：</span><span class="sxs-lookup"><span data-stu-id="e836a-106">Objectives:</span></span>

- <span data-ttu-id="e836a-107">設定 Unity 以應用程式開發</span><span class="sxs-lookup"><span data-stu-id="e836a-107">Configure Unity for app development</span></span>

- <span data-ttu-id="e836a-108">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="e836a-108">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="e836a-109">準備您的專案場景</span><span class="sxs-lookup"><span data-stu-id="e836a-109">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="e836a-110">指示</span><span class="sxs-lookup"><span data-stu-id="e836a-110">Instructions</span></span>

1. <span data-ttu-id="e836a-111">下載並儲存混合實境 Toolkit unity 套件，依序按一下[這裡。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="e836a-111">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span></span>
2. <span data-ttu-id="e836a-112">在 Unity 中，按一下 資產 功能表並選取 匯入封裝，然後按一下 「 自訂套件。 」</span><span class="sxs-lookup"><span data-stu-id="e836a-112">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="e836a-114">選取您從步驟 1 中所提供的連結下載 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="e836a-114">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="e836a-115">一旦匯入快顯視窗會出現在 Unity 中，按一下 匯入 按鈕，以開始匯入。</span><span class="sxs-lookup"><span data-stu-id="e836a-115">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="e836a-116">匯入 MRTK 可能需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="e836a-116">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="e836a-118">注意:下載的封裝會在您的本機資料夾儲存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="e836a-118">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="e836a-119">上圖未顯示您將在其中找到封裝。</span><span class="sxs-lookup"><span data-stu-id="e836a-119">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="e836a-120">建立新的場景 （做法是按一下 [檔案] 並選取 「 新場景 」）。</span><span class="sxs-lookup"><span data-stu-id="e836a-120">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="e836a-121">將場景儲存為"HLSharedProjectMain。 」</span><span class="sxs-lookup"><span data-stu-id="e836a-121">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="e836a-122">注意： 您可能會收到看起來類似下面的影像的快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="e836a-122">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="e836a-123">現在，只要按一下 [否]。</span><span class="sxs-lookup"><span data-stu-id="e836a-123">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="e836a-125">在 「 混合實境工具組 」 中，按一下 "新增至場景，並設定 」。</span><span class="sxs-lookup"><span data-stu-id="e836a-125">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="e836a-127">完成後完成時，新的組態檔會出現，讓您選擇以自訂設定檔。</span><span class="sxs-lookup"><span data-stu-id="e836a-127">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="e836a-128">按一下 複製和自訂 」。</span><span class="sxs-lookup"><span data-stu-id="e836a-128">Click "copy and customize."</span></span>

![Module3Chapter2step6im](images/module3chapter2step6im.PNG)

7. <span data-ttu-id="e836a-130">向下捲動，並取消核取 [啟用診斷系統] 是否您想要隱藏 [diagnostics] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e836a-130">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="e836a-131">我們建議您保持 [diagnostics] 視窗來監視效能，應用程式開發期間啟用和停用在生產環境或應用程式的示範期間。</span><span class="sxs-lookup"><span data-stu-id="e836a-131">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span>

![Module3Chapter2step7im](images/module3chapter2step7im.PNG)

8. <span data-ttu-id="e836a-133">開啟 組建設定，請按 control + shift + B 或前往 檔案 > 建置設定。</span><span class="sxs-lookup"><span data-stu-id="e836a-133">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="e836a-134">請注意，此程式目前設定下的 「 個人電腦、 Mac 和 Linux 的獨立 」 平台。</span><span class="sxs-lookup"><span data-stu-id="e836a-134">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="e836a-135">HoloLens 2 程式開發中，將 平台為 「 通用 Windows 平台。 」</span><span class="sxs-lookup"><span data-stu-id="e836a-135">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="e836a-136">選取它，然後按一下 「 交換器平台。 」</span><span class="sxs-lookup"><span data-stu-id="e836a-136">Select it and click "switch platform."</span></span>

   ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

   9. <span data-ttu-id="e836a-138">完成後，按一下 加入 開啟的場景。 方塊</span><span class="sxs-lookup"><span data-stu-id="e836a-138">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="e836a-139">現在請移至 [偵測器] 面板，並確定核取方塊右邊的 「 支援的虛擬實境"（如下圖所示） 會檢查。</span><span class="sxs-lookup"><span data-stu-id="e836a-139">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="e836a-140">也確定也勾選 「 場景/HLSharedProjectMain 」 旁的核取方塊，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e836a-140">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>

   ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

   10. <span data-ttu-id="e836a-142">在 [發行設定] 下一節中偵測器窗格中向下捲動到 「 功能 」，並確定下列核取方塊會標示：</span><span class="sxs-lookup"><span data-stu-id="e836a-142">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>
    - <span data-ttu-id="e836a-143">網際網路用戶端</span><span class="sxs-lookup"><span data-stu-id="e836a-143">internet client</span></span>
       
       - <span data-ttu-id="e836a-144">網際網路用戶端伺服器</span><span class="sxs-lookup"><span data-stu-id="e836a-144">internet client server</span></span>
       
       - <span data-ttu-id="e836a-145">私人網路用戶端伺服器</span><span class="sxs-lookup"><span data-stu-id="e836a-145">private network client server</span></span>
   
       - <span data-ttu-id="e836a-146">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="e836a-146">camera/webcam</span></span>

       - <span data-ttu-id="e836a-147">麥克風</span><span class="sxs-lookup"><span data-stu-id="e836a-147">microphone</span></span>
   
   11. <span data-ttu-id="e836a-148">匯入自訂以下稱為 「 第 2 課 」 可以在下載的封裝。</span><span class="sxs-lookup"><span data-stu-id="e836a-148">Import the custom package called "Lesson2" which can be downloaded here.</span></span> <span data-ttu-id="e836a-149">TODO:提供連結資產套件。</span><span class="sxs-lookup"><span data-stu-id="e836a-149">TODO: Provide link to asset pack.</span></span>
   
   ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)
   
   12. <span data-ttu-id="e836a-151">現在，在 [專案] 面板中，移至 「 prefabs"資料夾，因為在接下來的步驟中您會實作少數 prefabs 場景。</span><span class="sxs-lookup"><span data-stu-id="e836a-151">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="e836a-152">在 「 prefabs"資料夾中，按一下並拖曳 prefab，"DebugWindow 」 到階層。</span><span class="sxs-lookup"><span data-stu-id="e836a-152">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="e836a-153">完成之後，儲存專案 （按一下檔案，然後儲存，或按 control + S）</span><span class="sxs-lookup"><span data-stu-id="e836a-153">Once finished, save the project (click file, then save, or press control+S)</span></span>
   
       ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)
   
   > <span data-ttu-id="e836a-155">注意:您可能會注意到快顯視窗會顯示當您按一下 prefab，詢問您關於 TMP Essentials。</span><span class="sxs-lookup"><span data-stu-id="e836a-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="e836a-156">將需要，請按一下 [匯入 TMP Essentials]。</span><span class="sxs-lookup"><span data-stu-id="e836a-156">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="e836a-157">如果這個快顯視窗出現時，您可能需要刪除您的階層 prefab 並重新將它拖曳到您的階層，以避免可能的文字相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="e836a-157">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="e836a-159">恭喜！</span><span class="sxs-lookup"><span data-stu-id="e836a-159">Congratulations</span></span>

<span data-ttu-id="e836a-160">您的 Unity 專案已準備好進行 Photon ！</span><span class="sxs-lookup"><span data-stu-id="e836a-160">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="e836a-161">在接下來的課程中，我們將建置此場景和我們針對完整的共用經驗的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="e836a-161">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="e836a-162">[下一課：第 3 課 Sharing(Photon)](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="e836a-162">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>

