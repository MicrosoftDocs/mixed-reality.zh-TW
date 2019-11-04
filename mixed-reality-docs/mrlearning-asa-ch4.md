---
title: MR Learning ASA 模組 Azure 空間錨點 on HoloLens 2
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 141aa90f2bf5d90527a0fe1e6a812c1ce56bd0eb
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437798"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="56dcc-104">Photon （如果發生錯誤，請更正）</span><span class="sxs-lookup"><span data-stu-id="56dcc-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="56dcc-105">在這一課，</span><span class="sxs-lookup"><span data-stu-id="56dcc-105">In this lesson,</span></span> 

<span data-ttu-id="56dcc-106">目標</span><span class="sxs-lookup"><span data-stu-id="56dcc-106">Objectives:</span></span>

* <span data-ttu-id="56dcc-107">瞭解如何 _____________________________________________</span><span class="sxs-lookup"><span data-stu-id="56dcc-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="56dcc-108">瞭解如何 _________________________________________________</span><span class="sxs-lookup"><span data-stu-id="56dcc-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="56dcc-109">指示</span><span class="sxs-lookup"><span data-stu-id="56dcc-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="56dcc-110">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="56dcc-110">Setting Up Photon</span></span>

1. <span data-ttu-id="56dcc-111">設定[Photon](https://dashboard.photonengine.com//Account/SignUp)帳戶。</span><span class="sxs-lookup"><span data-stu-id="56dcc-111">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="56dcc-112">這麼做是由輸入您的電子郵件，以及進行一些驗證步驟所組成。</span><span class="sxs-lookup"><span data-stu-id="56dcc-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="56dcc-114">註冊之後，請按一下 [Sdk]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="56dcc-115">一旦您在該頁面上，請按一下 [伺服器]，並確定它顯示「自我裝載」。</span><span class="sxs-lookup"><span data-stu-id="56dcc-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="56dcc-116">然後向下滾動並按一下 [伺服器]，如下圖中的第二個影像所示。</span><span class="sxs-lookup"><span data-stu-id="56dcc-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="56dcc-119">這會使文字方塊出現標記為「大聲朗讀」。</span><span class="sxs-lookup"><span data-stu-id="56dcc-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="56dcc-120">請繼續閱讀。</span><span class="sxs-lookup"><span data-stu-id="56dcc-120">Go ahead and read it.</span></span> <span data-ttu-id="56dcc-121">完成後，按一下 [downloadSDK] 旁邊的連結以下載。</span><span class="sxs-lookup"><span data-stu-id="56dcc-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="56dcc-123">完成下載後，請按兩下資料夾。</span><span class="sxs-lookup"><span data-stu-id="56dcc-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="56dcc-124">當您的檔案瀏覽器開啟並顯示 SDK 資料夾之後，請複製 [SDK] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="56dcc-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="56dcc-125">您的下一個步驟是進入 windows C：磁片磁碟機，並建立名為 ' server ' 的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="56dcc-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="56dcc-127">現在開啟資料夾，並貼上您稍早複製的 SDK 資料夾。</span><span class="sxs-lookup"><span data-stu-id="56dcc-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="56dcc-129">完成後，開啟 [SDK] 資料夾並移至 [部署]，然後按一下 [bin_Win64]，然後按兩下 [photon 控制項]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="56dcc-131">注意：如果您有任何有關 IP 位址或任何其他類似問題的問題，您可以在工具列中找到大部分的資訊（如下圖所示）。</span><span class="sxs-lookup"><span data-stu-id="56dcc-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="56dcc-133">現在已設定並起始伺服器，請回到 Photon 網站，然後按一下設定檔圖示（下圖中的方塊），再選取 [您的應用程式]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="56dcc-135">按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="56dcc-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="56dcc-137">從 [Photon 類型] 底下的下拉式功能表中選取 [Photon 執行]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="56dcc-138">然後為它命名（您會記住的東西）。</span><span class="sxs-lookup"><span data-stu-id="56dcc-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="56dcc-139">在此範例中，我們將它命名為 "HoloLensPhotonProject"。</span><span class="sxs-lookup"><span data-stu-id="56dcc-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="56dcc-140">完成後，按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="56dcc-142">完成後，請返回您的應用程式頁面，您應該會看到類似下圖的內容。</span><span class="sxs-lookup"><span data-stu-id="56dcc-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="56dcc-143">按一下 [應用程式識別碼] 並加以複製。</span><span class="sxs-lookup"><span data-stu-id="56dcc-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="56dcc-144">貼入您可以輕鬆存取的位置。</span><span class="sxs-lookup"><span data-stu-id="56dcc-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="56dcc-146">建立新的 unity 專案。</span><span class="sxs-lookup"><span data-stu-id="56dcc-146">Create a new unity project.</span></span> <span data-ttu-id="56dcc-147">開啟 Unity 中樞，然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="56dcc-148">將它命名為 "HLSharingProject"。</span><span class="sxs-lookup"><span data-stu-id="56dcc-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="56dcc-149">然後按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-149">Then click create.</span></span> 

   > <span data-ttu-id="56dcc-150">注意：根據電腦的速度而定，最多可能需要2分鐘的時間才能載入。</span><span class="sxs-lookup"><span data-stu-id="56dcc-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="56dcc-152">注意：藉由變更 [位置] 選項，選擇在電腦中儲存專案的位置。</span><span class="sxs-lookup"><span data-stu-id="56dcc-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="56dcc-153">將它儲存到您將記得且容易存取的位置。</span><span class="sxs-lookup"><span data-stu-id="56dcc-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="56dcc-154">專案載入後，按一下 [資產] 存放區。</span><span class="sxs-lookup"><span data-stu-id="56dcc-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="56dcc-155">然後，在下圖所示的搜尋方塊中，輸入 "雙關語"，然後選取 [Photon 雙關語-2 FREE] 資產。</span><span class="sxs-lookup"><span data-stu-id="56dcc-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="56dcc-157">下載並匯入！</span><span class="sxs-lookup"><span data-stu-id="56dcc-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="56dcc-159">**設定 Unity 專案**</span><span class="sxs-lookup"><span data-stu-id="56dcc-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="56dcc-160">按一下這裡，下載在 Unity 中設定 Photon 所需的新資產[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="56dcc-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="56dcc-161">在 Unity 中，按一下 [資產] 功能表並選取 [匯入資產]，然後按一下 [自訂資產]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="56dcc-163">從步驟1所提供的連結中，選取您剛才下載的 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="56dcc-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="56dcc-164">一旦 [匯入] 按鈕出現在 Unity 中，請按一下它。</span><span class="sxs-lookup"><span data-stu-id="56dcc-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="56dcc-166">注意：您將套件下載到的任何位置都將是您找到它的地方。</span><span class="sxs-lookup"><span data-stu-id="56dcc-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="56dcc-167">上圖不會說明您會在何處找到封裝。</span><span class="sxs-lookup"><span data-stu-id="56dcc-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="56dcc-168">建立新的場景（這可以使用 control/command + N 來完成，或按一下 [檔案]，然後選取 [新增場景]）。</span><span class="sxs-lookup"><span data-stu-id="56dcc-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="56dcc-169">將場景儲存為 "HLSharedProjectMain"。</span><span class="sxs-lookup"><span data-stu-id="56dcc-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="56dcc-170">注意：您可能會收到類似下圖的快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="56dcc-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="56dcc-171">現在，只要按一下 [否] 即可。</span><span class="sxs-lookup"><span data-stu-id="56dcc-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="56dcc-173">在 [混合式現實工具組] 底下，按一下 [新增至場景並設定]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="56dcc-175">完成之後，就會出現新的設定檔案，讓您選擇自訂設定檔。</span><span class="sxs-lookup"><span data-stu-id="56dcc-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="56dcc-176">按一下 [複製並自訂]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="56dcc-178">向下並取消選取 [啟用診斷系統]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="56dcc-179">這可讓您更輕鬆地設定此專案。</span><span class="sxs-lookup"><span data-stu-id="56dcc-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="56dcc-181">開啟 [組建設定] （ctrl + shift + B）。</span><span class="sxs-lookup"><span data-stu-id="56dcc-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="56dcc-182">請注意，程式目前是在「電腦、Mac 和 Linux 獨立」平臺下設定。</span><span class="sxs-lookup"><span data-stu-id="56dcc-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="56dcc-183">針對此專案，請將平臺設定為「通用 windows 平臺」。</span><span class="sxs-lookup"><span data-stu-id="56dcc-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="56dcc-184">選取它，然後按一下 [切換平臺]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="56dcc-186">完成後，請按一下顯示「新增開啟場景」的方塊。</span><span class="sxs-lookup"><span data-stu-id="56dcc-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="56dcc-187">現在，請移至 [偵測器] 面板，並確定已核取 [支援的虛擬實境] 右邊的核取方塊（如下圖所示）。</span><span class="sxs-lookup"><span data-stu-id="56dcc-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="56dcc-189">注意：也請確定已核取 [場景/HLSharedProjectMain] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="56dcc-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="56dcc-190">在 [偵測器] 面板中的 [發行設定] 底下，向下滾動到 [功能]，並確定只會標示下列核取方塊：</span><span class="sxs-lookup"><span data-stu-id="56dcc-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="56dcc-191">網際網路用戶端</span><span class="sxs-lookup"><span data-stu-id="56dcc-191">internet client</span></span>
- <span data-ttu-id="56dcc-192">網際網路用戶端伺服器</span><span class="sxs-lookup"><span data-stu-id="56dcc-192">internet client server</span></span>
- <span data-ttu-id="56dcc-193">私人網路用戶端伺服器</span><span class="sxs-lookup"><span data-stu-id="56dcc-193">private network client server</span></span>
- <span data-ttu-id="56dcc-194">相機/網路攝影機</span><span class="sxs-lookup"><span data-stu-id="56dcc-194">camera/webcam</span></span>
- <span data-ttu-id="56dcc-195">麥克風</span><span class="sxs-lookup"><span data-stu-id="56dcc-195">microphone</span></span>

21. <span data-ttu-id="56dcc-196">就像步驟12一樣，下一個步驟是匯入另一個名為 "第2課" 的自訂套件，您可以在這裡下載 [這裡]。[第2課. unitypackage link 這裡]匯入該套件。</span><span class="sxs-lookup"><span data-stu-id="56dcc-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="56dcc-198">現在，在 [專案] 面板中，移至 "prefabs" 資料夾，因為在接下來的幾個步驟中，您將會在場景中執行幾個 prefabs。</span><span class="sxs-lookup"><span data-stu-id="56dcc-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="56dcc-199">在 "prefabs" 資料夾中，按一下 prefab，將 "DebugWindow" 拖曳至階層中。</span><span class="sxs-lookup"><span data-stu-id="56dcc-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="56dcc-200">完成後，儲存專案（依序按一下 [檔案]、[儲存] 或 [控制 + S]）</span><span class="sxs-lookup"><span data-stu-id="56dcc-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="56dcc-202">注意：您可能會注意到當您按一下 prefab 時會出現快顯視窗，詢問您有關 TMP Essentials。</span><span class="sxs-lookup"><span data-stu-id="56dcc-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="56dcc-203">如有需要，請按一下 [匯入 TMP Essentials]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="56dcc-205">**連接多個使用者**</span><span class="sxs-lookup"><span data-stu-id="56dcc-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="56dcc-206">就像步驟22，在 [專案] 面板的 [prefabs] 資料夾中，下一個步驟是將 "NetworkLobby" prefab 拖放到階層中。</span><span class="sxs-lookup"><span data-stu-id="56dcc-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="56dcc-208">當您開啟父 prefab "NetworkLobby" 時，您應該會看到子 prefab "NetworkRoom"。</span><span class="sxs-lookup"><span data-stu-id="56dcc-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="56dcc-209">選取此選項後，進入 [檢查] 面板，然後按一下 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="56dcc-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="56dcc-210">搜尋 "PhotonView" 並新增元件。</span><span class="sxs-lookup"><span data-stu-id="56dcc-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="56dcc-212">在階層中建立新的空白遊戲物件（以滑鼠右鍵按一下階層中，然後選取 [空的]）。</span><span class="sxs-lookup"><span data-stu-id="56dcc-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="56dcc-213">請確定定位設定為 x = 0、y = 0、z = 0，並將物件命名為 "PhotonUser"。</span><span class="sxs-lookup"><span data-stu-id="56dcc-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="56dcc-215">恭喜您</span><span class="sxs-lookup"><span data-stu-id="56dcc-215">Congratulations</span></span>



