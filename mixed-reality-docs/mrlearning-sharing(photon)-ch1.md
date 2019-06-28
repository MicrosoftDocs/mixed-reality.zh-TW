---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416119"
---
# <a name="setting-up-photon"></a><span data-ttu-id="db341-104">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="db341-104">Setting Up Photon</span></span>

<span data-ttu-id="db341-105">在這一課中，我們將了解如何做好準備，以建立共用的體驗 Photon Unity 網路功能 （自己使用這個雙關語） 匯入 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="db341-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="db341-106">Photon 是數個網路功能選項 Mixed Reality 開發人員可用來建立共用的體驗。</span><span class="sxs-lookup"><span data-stu-id="db341-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="db341-107">我們將帶領您學習建立 Photon 帳戶、 匯入 Photon，並建立選用的本機伺服器</span><span class="sxs-lookup"><span data-stu-id="db341-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="db341-108">目標：</span><span class="sxs-lookup"><span data-stu-id="db341-108">Objectives:</span></span>

* <span data-ttu-id="db341-109">了解如何建立 Photon 帳戶</span><span class="sxs-lookup"><span data-stu-id="db341-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="db341-110">了解如何尋找並匯入 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="db341-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="db341-111">設定本機的 Photon server</span><span class="sxs-lookup"><span data-stu-id="db341-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="db341-112">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="db341-112">Setting Up Photon</span></span>

1. <span data-ttu-id="db341-113">設定好[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帳戶。</span><span class="sxs-lookup"><span data-stu-id="db341-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="db341-114">按一下瀏覽至 Photon 註冊頁面[此連結](https://dashboard.photonengine.com/en-US/Account/SignUp)。</span><span class="sxs-lookup"><span data-stu-id="db341-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="db341-115">若要建立的帳戶註冊頁面上，遵循的指示。</span><span class="sxs-lookup"><span data-stu-id="db341-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="db341-118">按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="db341-118">Create an application ID by clicking the "create a new app" button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="db341-120">選取"Photon 了絕佳 」 從下拉式功能表中，在 「 photon 類型 」。</span><span class="sxs-lookup"><span data-stu-id="db341-120">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="db341-121">然後為它命名，在此範例中，我們將它命名為"HoloLensPhotonProject。 」</span><span class="sxs-lookup"><span data-stu-id="db341-121">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="db341-122">完成之後，按一下 [建立] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="db341-122">Once finished, click the "CREATE" button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="db341-124">完成後，返回您的應用程式頁面，您應該會看到類似下圖。</span><span class="sxs-lookup"><span data-stu-id="db341-124">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="db341-125">按一下 應用程式識別碼，並將它複製。</span><span class="sxs-lookup"><span data-stu-id="db341-125">Click on the app ID and copy it.</span></span> <span data-ttu-id="db341-126">貼上是您可以輕鬆存取的地方。</span><span class="sxs-lookup"><span data-stu-id="db341-126">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="db341-128">建立新的 unity 專案並將它命名為"HLSharingProject。 」</span><span class="sxs-lookup"><span data-stu-id="db341-128">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="db341-129">如需有關如何建立新的 Unity 專案的指示，請參閱[基底模組中的 < 建立 Unity 專案 > 一節](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="db341-129">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="db341-130">專案載入後，按一下 「 資產存放區 」 索引標籤，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="db341-130">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="db341-131">然後，在下圖中反白顯示搜尋方塊中輸入 「 自己 」 使用這個雙關語，然後從搜尋結果中選取 「 Photon 自己 2-使用這個雙關語可用 」 的資產。</span><span class="sxs-lookup"><span data-stu-id="db341-131">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="db341-133">下載並匯入此資產藉由按下 「 下載 」 及 「 匯入 」 按鈕。</span><span class="sxs-lookup"><span data-stu-id="db341-133">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="db341-135">匯入程序完成後 Photon，自己使用這個雙關語精靈 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="db341-135">Once Photon has completed the importing process, the Pun Wizard will appear.</span></span> <span data-ttu-id="db341-136">需要應用程式識別碼 （這應該是您的剪貼簿中） 從步驟 4 並將它貼到 [AppID] 方塊中，按下 [安裝專案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="db341-136">Take the application ID (which should be in your clipboard) from step 4 and paste it into the AppID box and press the "Setup Project" button.</span></span> 
<span data-ttu-id="db341-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="db341-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="db341-138">已成功新增 AppID 之後, 瀏覽至 [Photon]->"PhotonUnityNetworking"]-> [[資源]->"PhotonServerSettings 」 中的資產。</span><span class="sxs-lookup"><span data-stu-id="db341-138">After successfully adding the AppID, navigate to "Photon"->"PhotonUnityNetworking" -> "Resources" ->  "PhotonServerSettings" in Assets.</span></span> <span data-ttu-id="db341-139">選取 [使用名稱伺服器] 選項並設定固定的區域 「 我們 」 或您 photon 服務區域。</span><span class="sxs-lookup"><span data-stu-id="db341-139">Select "Use Name Server" option and set the fixed region to "us" or your photon service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="db341-141">恭喜！</span><span class="sxs-lookup"><span data-stu-id="db341-141">Congratulations</span></span>

<span data-ttu-id="db341-142">您已成功建立 Photon 帳戶、 設定本機 Photon 伺服器，並自己使用這個雙關語匯入 Unity。</span><span class="sxs-lookup"><span data-stu-id="db341-142">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="db341-143">下一步是要設定專案，然後允許與其他使用者的連線，這樣多個使用者可以看到您的工作。</span><span class="sxs-lookup"><span data-stu-id="db341-143">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="db341-144">[下一課：第 2 課 Sharing(Photon)](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="db341-144">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

