---
title: MR 學習 ASA 模組上 HoloLens 2 Azure 空間的錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326821"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="473d1-104">Photon （更正我如果我是錯誤）</span><span class="sxs-lookup"><span data-stu-id="473d1-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="473d1-105">在這一課中，</span><span class="sxs-lookup"><span data-stu-id="473d1-105">In this lesson,</span></span> 

<span data-ttu-id="473d1-106">目標：</span><span class="sxs-lookup"><span data-stu-id="473d1-106">Objectives:</span></span>

* <span data-ttu-id="473d1-107">了解如何 ___</span><span class="sxs-lookup"><span data-stu-id="473d1-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="473d1-108">了解如何 ___</span><span class="sxs-lookup"><span data-stu-id="473d1-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="473d1-109">指示</span><span class="sxs-lookup"><span data-stu-id="473d1-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="473d1-110">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="473d1-110">Setting Up Photon</span></span>

1. <span data-ttu-id="473d1-111">設定好[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帳戶。</span><span class="sxs-lookup"><span data-stu-id="473d1-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="473d1-112">執行此動作將會包含輸入您的電子郵件，並透過一些驗證步驟。</span><span class="sxs-lookup"><span data-stu-id="473d1-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="473d1-114">一旦您已註冊，請按一下 Sdk。</span><span class="sxs-lookup"><span data-stu-id="473d1-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="473d1-115">當您在該頁面上，按一下在 [伺服器]，並確定它說 「 自我裝載。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="473d1-116">然後向下捲動，然後按一下 [伺服器] 下方的第二個影像所示。</span><span class="sxs-lookup"><span data-stu-id="473d1-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="473d1-119">這會造成文字方塊中，會加上標籤，顯示 「 讀我 」。</span><span class="sxs-lookup"><span data-stu-id="473d1-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="473d1-120">請繼續並讀取它。</span><span class="sxs-lookup"><span data-stu-id="473d1-120">Go ahead and read it.</span></span> <span data-ttu-id="473d1-121">一旦完成，請按一下 「 downloadSDK 」，若要下載它旁邊的連結。</span><span class="sxs-lookup"><span data-stu-id="473d1-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="473d1-123">完成下載之後，按兩下 資料夾。</span><span class="sxs-lookup"><span data-stu-id="473d1-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="473d1-124">檔案總管開啟後揭露 SDK 資料夾，請將複製的 SDK 資料夾。</span><span class="sxs-lookup"><span data-stu-id="473d1-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="473d1-125">下一步是進入 windows c： 磁碟機，並建立新資料夾，稱為 「 伺服器 」。</span><span class="sxs-lookup"><span data-stu-id="473d1-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="473d1-127">現在開啟資料夾，並貼上您之前複製的 SDK 資料夾。</span><span class="sxs-lookup"><span data-stu-id="473d1-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="473d1-129">完成之後，開啟 [SDK] 資料夾，並移至 「 部署 」 的再"bin_Win64 」，然後按兩下 「 photon 控制項 」。</span><span class="sxs-lookup"><span data-stu-id="473d1-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="473d1-131">注意:如果您有任何疑問的 IP 位址或任何其他類似的問題，您可以找到大部分的資訊，在工具列中 （如圖所示） 即可。</span><span class="sxs-lookup"><span data-stu-id="473d1-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="473d1-133">現在，伺服器已設定，並起始，返回 Photon 網站 （在下圖中進行 boxed 處理） 的設定檔圖示上按一下，並選取 「 您的應用程式。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="473d1-135">按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="473d1-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="473d1-137">從 「 photon 類型 」。 下的下拉式功能表中選取 Photon 執行</span><span class="sxs-lookup"><span data-stu-id="473d1-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="473d1-138">然後為它的名稱 （項目就會記住）。</span><span class="sxs-lookup"><span data-stu-id="473d1-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="473d1-139">在此範例中，我們將它命名為"HoloLensPhotonProject。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="473d1-140">完成後，按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="473d1-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="473d1-142">完成後，返回您的應用程式頁面，您應該會看到類似下圖。</span><span class="sxs-lookup"><span data-stu-id="473d1-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="473d1-143">按一下 應用程式識別碼，並將它複製。</span><span class="sxs-lookup"><span data-stu-id="473d1-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="473d1-144">貼上是您可以輕鬆存取的地方。</span><span class="sxs-lookup"><span data-stu-id="473d1-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="473d1-146">建立新的 unity 專案。</span><span class="sxs-lookup"><span data-stu-id="473d1-146">Create a new unity project.</span></span> <span data-ttu-id="473d1-147">開啟 Unity 中樞，然後按一下 「 new 」。</span><span class="sxs-lookup"><span data-stu-id="473d1-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="473d1-148">它命名為"HLSharingProject。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="473d1-149">然後按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="473d1-149">Then click create.</span></span> 

   > <span data-ttu-id="473d1-150">注意：這可能需要 2 分鐘的時間載入，根據您的電腦速度。</span><span class="sxs-lookup"><span data-stu-id="473d1-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="473d1-152">注意： 挑選一個位置來儲存您的專案中您的電腦，藉由變更 「 位置 」 選項。</span><span class="sxs-lookup"><span data-stu-id="473d1-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="473d1-153">請將它儲存到您將會記住，並能輕鬆存取的位置。</span><span class="sxs-lookup"><span data-stu-id="473d1-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="473d1-154">專案載入後，按一下 「 資產存放區 」。</span><span class="sxs-lookup"><span data-stu-id="473d1-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="473d1-155">然後，在搜尋方塊中顯示在下圖中，輸入 「 自己 」 使用這個雙關語，然後選取 「 Photon 自己使用這個雙關語 2 免費 」 的資產。</span><span class="sxs-lookup"><span data-stu-id="473d1-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="473d1-157">下載並匯入 ！</span><span class="sxs-lookup"><span data-stu-id="473d1-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="473d1-159">**設定 Unity 專案**</span><span class="sxs-lookup"><span data-stu-id="473d1-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="473d1-160">下載新設定 Photon Unity 中，依序按一下所需的資產[這裡。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="473d1-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="473d1-161">在 Unity 中，按一下 資產 功能表並選取 「 匯入資產 」 然後按一下 「 自訂資產。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="473d1-163">選取您從步驟 1 中所提供的連結下載 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="473d1-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="473d1-164">一旦匯入 按鈕會出現在 Unity 中，按一下它。</span><span class="sxs-lookup"><span data-stu-id="473d1-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="473d1-166">注意： 下載套件的任一處，將會在您找到。</span><span class="sxs-lookup"><span data-stu-id="473d1-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="473d1-167">上圖未顯示您將在其中找到封裝。</span><span class="sxs-lookup"><span data-stu-id="473d1-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="473d1-168">建立新的場景 (這可以是使用控制項 / 命令 + N，或按一下 [檔案]，然後選取 「 新的場景。")。</span><span class="sxs-lookup"><span data-stu-id="473d1-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="473d1-169">將場景儲存為"HLSharedProjectMain。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="473d1-170">注意： 您可能會收到看起來類似下面的影像的快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="473d1-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="473d1-171">現在，只要按一下 [否。]</span><span class="sxs-lookup"><span data-stu-id="473d1-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="473d1-173">在 「 混合實境工具組 」 中，按一下 "新增至場景，並設定 」。</span><span class="sxs-lookup"><span data-stu-id="473d1-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="473d1-175">完成後完成時，新的組態檔會出現，讓您選擇以自訂設定檔。</span><span class="sxs-lookup"><span data-stu-id="473d1-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="473d1-176">按一下 複製和自訂 」。</span><span class="sxs-lookup"><span data-stu-id="473d1-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="473d1-178">向下捲動，並取消核取 [啟用診斷系統]。</span><span class="sxs-lookup"><span data-stu-id="473d1-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="473d1-179">這會讓您更輕鬆地設定此專案。</span><span class="sxs-lookup"><span data-stu-id="473d1-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="473d1-181">開啟 組建設定 （控制 + shift + B）。</span><span class="sxs-lookup"><span data-stu-id="473d1-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="473d1-182">請注意，此程式目前設定下的 「 個人電腦、 Mac 和 Linux 的獨立 」 平台。</span><span class="sxs-lookup"><span data-stu-id="473d1-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="473d1-183">此專案中，將 平台為 「 通用 windows 平台。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="473d1-184">選取它，然後按一下 「 交換器平台。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="473d1-186">完成後，按一下 加入 開啟的場景。 方塊</span><span class="sxs-lookup"><span data-stu-id="473d1-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="473d1-187">現在請移至 [偵測器] 面板，並確定核取方塊右邊的 「 支援的虛擬實境"（如下圖所示） 會檢查。</span><span class="sxs-lookup"><span data-stu-id="473d1-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="473d1-189">注意：也請確定 「 場景/HLSharedProjectMain 」 旁的核取方塊也會核取。</span><span class="sxs-lookup"><span data-stu-id="473d1-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="473d1-190">底下的 「 發佈設定 」 偵測器 面板中捲動到 「 功能 」，並確定下列核取方塊會標示：</span><span class="sxs-lookup"><span data-stu-id="473d1-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="473d1-191">網際網路用戶端</span><span class="sxs-lookup"><span data-stu-id="473d1-191">internet client</span></span>
- <span data-ttu-id="473d1-192">網際網路用戶端伺服器</span><span class="sxs-lookup"><span data-stu-id="473d1-192">internet client server</span></span>
- <span data-ttu-id="473d1-193">私人網路用戶端伺服器</span><span class="sxs-lookup"><span data-stu-id="473d1-193">private network client server</span></span>
- <span data-ttu-id="473d1-194">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="473d1-194">camera/webcam</span></span>
- <span data-ttu-id="473d1-195">麥克風</span><span class="sxs-lookup"><span data-stu-id="473d1-195">microphone</span></span>

21. <span data-ttu-id="473d1-196">如同步驟 12 中下, 一個步驟是匯入另一個稱為 「 第 2 課 」 可以在 [這裡]。 下載的自訂套件[lesson2.unitypackage 連結置於此處]匯入該套件。</span><span class="sxs-lookup"><span data-stu-id="473d1-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="473d1-198">現在，在 [專案] 面板中，移至 「 prefabs"資料夾，因為在接下來的步驟中您會實作少數 prefabs 場景。</span><span class="sxs-lookup"><span data-stu-id="473d1-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="473d1-199">在 「 prefabs"資料夾中，按一下並拖曳 prefab，"DebugWindow 」 到階層。</span><span class="sxs-lookup"><span data-stu-id="473d1-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="473d1-200">完成之後，儲存專案 (按一下檔案，然後儲存檔案，或 control + S)</span><span class="sxs-lookup"><span data-stu-id="473d1-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="473d1-202">注意：您可能會注意到快顯視窗會顯示當您按一下 prefab，詢問您關於 TMP Essentials。</span><span class="sxs-lookup"><span data-stu-id="473d1-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="473d1-203">將需要，請按一下 [匯入 TMP Essentials]。</span><span class="sxs-lookup"><span data-stu-id="473d1-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="473d1-205">**連接多個使用者**</span><span class="sxs-lookup"><span data-stu-id="473d1-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="473d1-206">如步驟 22，在 [專案] 面板中，「 prefabs"資料夾中的下一個步驟是拖放 「 NetworkLobby"prefab 至階層。</span><span class="sxs-lookup"><span data-stu-id="473d1-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="473d1-208">當您開啟父 prefab，而"NetworkLobby 」，您應該會看到子系 prefab，「 NetworkRoom。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="473d1-209">有了它選取，進入 [偵測器] 面板，並按一下 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="473d1-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="473d1-210">搜尋 「 PhotonView"，並將元件加入。</span><span class="sxs-lookup"><span data-stu-id="473d1-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="473d1-212">階層 （以滑鼠右鍵按一下 階層 和 選取 「 空白 」） 中建立新的空白遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="473d1-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="473d1-213">請確定位置設定為 x = 0，y = 0，z = 0，並命名物件，也就是 「 PhotonUser。 」</span><span class="sxs-lookup"><span data-stu-id="473d1-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="473d1-215">恭喜！</span><span class="sxs-lookup"><span data-stu-id="473d1-215">Congratulations</span></span>



