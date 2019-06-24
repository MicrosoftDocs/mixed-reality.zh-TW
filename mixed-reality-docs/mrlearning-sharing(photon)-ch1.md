---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328077"
---
# <a name="setting-up-photon"></a><span data-ttu-id="acd95-104">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="acd95-104">Setting Up Photon</span></span>

<span data-ttu-id="acd95-105">在這一課中，我們將了解如何做好準備，以建立共用的體驗 Photon Unity 網路功能 （自己使用這個雙關語） 匯入 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="acd95-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="acd95-106">Photon 是數個網路功能選項 Mixed Reality 開發人員可用來建立共用的體驗。</span><span class="sxs-lookup"><span data-stu-id="acd95-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="acd95-107">我們將帶領您學習建立 Photon 帳戶、 匯入 Photon，並建立選用的本機伺服器</span><span class="sxs-lookup"><span data-stu-id="acd95-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="acd95-108">目標：</span><span class="sxs-lookup"><span data-stu-id="acd95-108">Objectives:</span></span>

* <span data-ttu-id="acd95-109">了解如何建立 Photon 帳戶</span><span class="sxs-lookup"><span data-stu-id="acd95-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="acd95-110">了解如何尋找並匯入 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="acd95-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="acd95-111">設定本機的 Photon server</span><span class="sxs-lookup"><span data-stu-id="acd95-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="acd95-112">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="acd95-112">Setting Up Photon</span></span>

1. <span data-ttu-id="acd95-113">設定好[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帳戶。</span><span class="sxs-lookup"><span data-stu-id="acd95-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="acd95-114">按一下瀏覽至 Photon 註冊頁面[此連結](https://dashboard.photonengine.com/en-US/Account/SignUp)。</span><span class="sxs-lookup"><span data-stu-id="acd95-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="acd95-115">若要建立的帳戶註冊頁面上，遵循的指示。</span><span class="sxs-lookup"><span data-stu-id="acd95-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. <span data-ttu-id="acd95-117">一旦您已註冊，請按一下 Sdk。</span><span class="sxs-lookup"><span data-stu-id="acd95-117">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="acd95-118">當您在該頁面上，按一下在 [伺服器]，並確定它說 「 自我裝載。 」</span><span class="sxs-lookup"><span data-stu-id="acd95-118">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="acd95-119">然後向下捲動，然後按一下 [伺服器] 下方的第二個影像所示。</span><span class="sxs-lookup"><span data-stu-id="acd95-119">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. <span data-ttu-id="acd95-122">這會造成文字方塊中，會加上標籤，顯示 「 讀我 」。</span><span class="sxs-lookup"><span data-stu-id="acd95-122">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="acd95-123">請繼續並讀取它。</span><span class="sxs-lookup"><span data-stu-id="acd95-123">Go ahead and read it.</span></span> <span data-ttu-id="acd95-124">一旦完成，請按一下 「 downloadSDK 」，若要下載它旁邊的連結。</span><span class="sxs-lookup"><span data-stu-id="acd95-124">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. <span data-ttu-id="acd95-126">完成下載之後，按兩下 資料夾。</span><span class="sxs-lookup"><span data-stu-id="acd95-126">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="acd95-127">檔案總管開啟後揭露 SDK 資料夾，請將複製的 SDK 資料夾。</span><span class="sxs-lookup"><span data-stu-id="acd95-127">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="acd95-128">下一步是進入 windows c： 磁碟機，並建立新資料夾，稱為 「 伺服器 」。</span><span class="sxs-lookup"><span data-stu-id="acd95-128">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - <span data-ttu-id="acd95-130">現在開啟資料夾，並貼上您之前複製的 SDK 資料夾。</span><span class="sxs-lookup"><span data-stu-id="acd95-130">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. <span data-ttu-id="acd95-132">完成之後，開啟 [SDK] 資料夾，並移至 「 部署 」 的再"bin_Win64 」，然後按兩下 「 photon 控制項 」。</span><span class="sxs-lookup"><span data-stu-id="acd95-132">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> <span data-ttu-id="acd95-134">注意:如果您有任何疑問的 IP 位址或任何其他類似的問題，您可以找到大部分的資訊，在工具列中 （如圖所示） 即可。</span><span class="sxs-lookup"><span data-stu-id="acd95-134">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. <span data-ttu-id="acd95-136">現在，伺服器已設定，並起始，回到 Photon 網站，並確定您仍登入 （或重新登入，如果您不。）按一下設定檔圖示 （右上角的下面的影像中進行 boxed 處理），然後選取 「 您的應用程式。 」</span><span class="sxs-lookup"><span data-stu-id="acd95-136">Now that the server is set up and initiated, go back to the Photon website and ensure that you are still signed in (or sign back in, if you are not.) Click on the profile icon (boxed in the top right corner of the image below) and select "your applications."</span></span>
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. <span data-ttu-id="acd95-138">按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="acd95-138">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - <span data-ttu-id="acd95-140">選取"Photon 了絕佳 」 從下拉式功能表中，在 「 photon 類型 」。</span><span class="sxs-lookup"><span data-stu-id="acd95-140">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="acd95-141">然後為它命名，在此範例中，我們將它命名為"HoloLensPhotonProject。 」</span><span class="sxs-lookup"><span data-stu-id="acd95-141">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="acd95-142">完成之後，按一下 [建立] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="acd95-142">Once finished, click the "CREATE" button.</span></span>

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. <span data-ttu-id="acd95-144">完成後，返回您的應用程式頁面，您應該會看到類似下圖。</span><span class="sxs-lookup"><span data-stu-id="acd95-144">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="acd95-145">按一下 應用程式識別碼，並將它複製。</span><span class="sxs-lookup"><span data-stu-id="acd95-145">Click on the app ID and copy it.</span></span> <span data-ttu-id="acd95-146">貼上是您可以輕鬆存取的地方。</span><span class="sxs-lookup"><span data-stu-id="acd95-146">Paste is somewhere you can easily access.</span></span>  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. <span data-ttu-id="acd95-148">建立新的 unity 專案並將它命名為"HLSharingProject。 」</span><span class="sxs-lookup"><span data-stu-id="acd95-148">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="acd95-149">如需有關如何建立新的 Unity 專案的指示，請參閱[基底模組中的 < 建立 Unity 專案 > 一節](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="acd95-149">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 


10. <span data-ttu-id="acd95-150">專案載入後，按一下 「 資產存放區 」 索引標籤，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="acd95-150">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="acd95-151">然後，在下圖中反白顯示搜尋方塊中輸入 「 自己 」 使用這個雙關語，然後從搜尋結果中選取 「 Photon 自己使用這個雙關語 2 免費 」 的資產。</span><span class="sxs-lookup"><span data-stu-id="acd95-151">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset from the search results.</span></span> 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. <span data-ttu-id="acd95-153">下載並匯入此資產藉由按下 「 下載 」 及 「 匯入 」 按鈕。</span><span class="sxs-lookup"><span data-stu-id="acd95-153">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="acd95-155">恭喜！</span><span class="sxs-lookup"><span data-stu-id="acd95-155">Congratulations</span></span>

<span data-ttu-id="acd95-156">您已成功建立 Photon 帳戶、 設定本機 Photon 伺服器，並自己使用這個雙關語匯入 Unity。</span><span class="sxs-lookup"><span data-stu-id="acd95-156">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="acd95-157">下一步是要設定專案，然後允許與其他使用者的連線，這樣多個使用者可以看到您的工作。</span><span class="sxs-lookup"><span data-stu-id="acd95-157">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="acd95-158">[下一課：第 2 課 Sharing(Photon)](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="acd95-158">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

