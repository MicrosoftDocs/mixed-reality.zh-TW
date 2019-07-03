# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="f7cf7-101">準備 Unity 進行開發</span><span class="sxs-lookup"><span data-stu-id="f7cf7-101">Getting Unity ready for development</span></span> 

<span data-ttu-id="f7cf7-102">在本教學課程中，我們了解如何準備及設定 Unity 以應用程式開發，包括匯入混合實境工具組、 設定組建設定，並準備我們的場景。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-102">In this tutorial, we learn how to prepare and configure Unity for applicaiton development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="f7cf7-103">目標：</span><span class="sxs-lookup"><span data-stu-id="f7cf7-103">Objectives:</span></span>

- <span data-ttu-id="f7cf7-104">設定 Unity 應用程式開發</span><span class="sxs-lookup"><span data-stu-id="f7cf7-104">Configure Unity for applicaiton development</span></span>

- <span data-ttu-id="f7cf7-105">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="f7cf7-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="f7cf7-106">準備您的專案場景</span><span class="sxs-lookup"><span data-stu-id="f7cf7-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="f7cf7-107">指示</span><span class="sxs-lookup"><span data-stu-id="f7cf7-107">Instructions</span></span>

1. <span data-ttu-id="f7cf7-108">下載並儲存混合實境 Toolkit unity 套件，依序按一下[這裡。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="f7cf7-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="f7cf7-109">在 Unity 中，按一下 [資產] 功能表並選取匯入封裝，然後按一下自訂套件。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="f7cf7-111">選取您從步驟 1 中所提供的連結下載 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="f7cf7-112">一旦匯入快顯視窗會出現在 Unity 中，按一下 匯入 按鈕，以開始匯入。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="f7cf7-113">匯入 MRTK 可能需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="f7cf7-115">注意:下載的封裝是在您儲存檔案的位置的本機資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="f7cf7-116">上圖未顯示您將在其中找到封裝。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="f7cf7-117">建立新的場景。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-117">Create a new scene.</span></span> <span data-ttu-id="f7cf7-118">T 可按一下檔案，然後選取新的場景 」）。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-118">Tthis can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="f7cf7-119">存 HLSharedProjectMain 場景。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="f7cf7-120">注意： 您可能會收到看起來類似下面的影像的快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="f7cf7-121">現在，請按一下 [否]。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="f7cf7-123">在混合實境工具箱項目，按一下 新增至場景，然後設定。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="f7cf7-125">完成後完成時，新的組態檔隨即出現，讓您選擇以自訂設定檔。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="f7cf7-126">按一下 複製和自訂。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-126">Click Copy and Customize.</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="f7cf7-130">向下捲動，並取消核取 啟用 Siagnostics 系統，如果您想要隱藏 diagnostics 視窗。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-130">Scroll down and uncheck Enable Siagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="f7cf7-131">我們建議您保持 [diagnostics] 視窗來監視效能，應用程式開發期間啟用和停用在生產環境或應用程式的示範期間。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-131">We recommend keeping the diagnostics window enabled during applicaiton development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="f7cf7-133">開啟的組建設定，請按 control + shift + B，或前往 檔案-> 組建設定。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="f7cf7-134">請注意，此程式目前設定在 PC、 Mac 和 Linux 的獨立平台。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="f7cf7-135">HoloLens 2 開發，會設定為通用 Windows 平台的平台。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="f7cf7-136">選取它，然後按一下 切換平台。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-136">Select it and click Switch Platform.</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="f7cf7-138">完成後，按一下 [新增開啟場景] 方塊。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="f7cf7-139">現在請移至 [偵測器] 面板中，並確定已核取核取方塊右邊的虛擬實境支援 （如圖所示）。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="f7cf7-140">也請確定在下圖所示，也檢查場景/HLSharedProjectMain 旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="f7cf7-142">在 [偵測器] 面板中的 [發佈設定] 區段中，向下捲動功能，並確保已標示下列核取方塊：</span><span class="sxs-lookup"><span data-stu-id="f7cf7-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="f7cf7-144">匯入自訂的套件稱為 SharingAssetCollection 可下載[以下。](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="f7cf7-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="f7cf7-145">在 [專案] 面板中，移至 Prefabs 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-145">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="f7cf7-146">在接下來的步驟中，您會實作少數 prefabs 場景。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-146">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="f7cf7-147">在 Prefabs 資料夾中，按一下並拖曳 prefab，DebugWindow 到階層。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-147">In the Prefabs folder, click and drag the prefab, DebugWindow into the hierarchy.</span></span> <span data-ttu-id="f7cf7-148">完成之後，儲存專案的 clckin 檔案，然後儲存或按 Control + S。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-148">Once finished, save the project by clckin File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="f7cf7-150">注意:您可能會注意到快顯視窗會顯示當您按一下 prefab，詢問您關於 TMP Essentials。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-150">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="f7cf7-151">如有需要請按一下 匯入 TMP 基本功能。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-151">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="f7cf7-152">如果這個快顯視窗出現時，您可能需要刪除您的階層 prefab 並重新將它拖曳到您的階層，以避免可能的文字相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-152">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="f7cf7-154">恭喜！</span><span class="sxs-lookup"><span data-stu-id="f7cf7-154">Congratulations</span></span>

<span data-ttu-id="f7cf7-155">您的 Unity 專案已準備好進行 Photon。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-155">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="f7cf7-156">在接下來的教學課程中，我們將建置此場景和我們針對完整的共用經驗的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="f7cf7-156">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="f7cf7-157">[下一個教學課程：連接多個使用者](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="f7cf7-157">[Next tutorial: Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

