---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523295"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="23403-104">設定 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="23403-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="23403-105">在本教學課程中，我們了解如何做好準備，以建立共用的體驗 Photon Unity 網路功能 （自己使用這個雙關語） 匯入 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="23403-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="23403-106">Photon 是數個網路功能選項 Mixed Reality 開發人員可用來建立共用的體驗。</span><span class="sxs-lookup"><span data-stu-id="23403-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="23403-107">我們將帶領您學習建立 Photon 帳戶、 匯入 Photon，並建立選用的本機伺服器</span><span class="sxs-lookup"><span data-stu-id="23403-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="23403-108">目標：</span><span class="sxs-lookup"><span data-stu-id="23403-108">Objectives:</span></span>

* <span data-ttu-id="23403-109">了解如何建立 Photon 帳戶</span><span class="sxs-lookup"><span data-stu-id="23403-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="23403-110">了解如何尋找並匯入 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="23403-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="23403-111">設定本機的 Photon server</span><span class="sxs-lookup"><span data-stu-id="23403-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="23403-112">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="23403-112">Setting up Photon</span></span>

1. <span data-ttu-id="23403-113">設定好[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帳戶。</span><span class="sxs-lookup"><span data-stu-id="23403-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="23403-114">按一下瀏覽至 Photon 註冊頁面[此連結](https://dashboard.photonengine.com/en-US/Account/SignUp)。</span><span class="sxs-lookup"><span data-stu-id="23403-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="23403-115">若要建立的帳戶註冊頁面上，遵循的指示。</span><span class="sxs-lookup"><span data-stu-id="23403-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="23403-118">依序按一下 [建立新的應用程式] 按鈕建立的應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="23403-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="23403-120">從 Photon 類型下的下拉式功能表中選取 Photon 自己使用這個雙關語。</span><span class="sxs-lookup"><span data-stu-id="23403-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="23403-121">然後為它的名稱。</span><span class="sxs-lookup"><span data-stu-id="23403-121">Then give it a name.</span></span> <span data-ttu-id="23403-122">在此範例中，我們命名為它 HoloLensPhotonProject。</span><span class="sxs-lookup"><span data-stu-id="23403-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="23403-123">完成之後，按一下 [建立] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="23403-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="23403-125">完成後，返回您的應用程式頁面，您應該會看到類似下圖。</span><span class="sxs-lookup"><span data-stu-id="23403-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="23403-126">按一下應用程式識別碼，並將它複製。</span><span class="sxs-lookup"><span data-stu-id="23403-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="23403-127">貼上是您可以輕鬆存取的地方。</span><span class="sxs-lookup"><span data-stu-id="23403-127">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="23403-129">建立新的 unity 專案並將它命名為 HLSharingProject。</span><span class="sxs-lookup"><span data-stu-id="23403-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="23403-130">如需有關如何建立新的 Unity 專案的指示，請參閱[基底模組中的 < 建立 Unity 專案 > 一節](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="23403-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="23403-131">專案載入後，按一下 [資產存放區] 索引標籤中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="23403-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="23403-132">然後，在下圖中反白顯示搜尋方塊中輸入自己使用這個雙關語，並選取 Photon 自己使用這個雙關語 2-例如 FRE"資產，從搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="23403-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FRE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="23403-134">下載並匯入此資產藉由按下 [下載和匯入] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="23403-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="23403-136">匯入程序完成後 Photon，自己使用這個雙關語精靈 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="23403-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="23403-137">需要應用程式識別碼 （這應該是您的剪貼簿中） 從步驟 4 中，並將它貼到 AppID 方塊中，然後按 安裝專案按鈕。</span><span class="sxs-lookup"><span data-stu-id="23403-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="23403-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="23403-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="23403-139">已成功新增 AppID 之後, 瀏覽至 Photon PhotonUnityNetworking]-> []-> [資源]-> [PhotonServerSettings 在資產中的。</span><span class="sxs-lookup"><span data-stu-id="23403-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="23403-140">選取 [使用名稱伺服器] 選項中，並設定我們的固定的區域或 yourPphoton 服務區域。</span><span class="sxs-lookup"><span data-stu-id="23403-140">Select the Use Name Server option, and set the fixed region to US or yourPphoton service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="23403-142">恭喜！</span><span class="sxs-lookup"><span data-stu-id="23403-142">Congratulations</span></span>

<span data-ttu-id="23403-143">您已成功建立 Photon 帳戶、 設定本機 Photon 伺服器，並自己使用這個雙關語匯入 Unity。</span><span class="sxs-lookup"><span data-stu-id="23403-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="23403-144">下一步是要設定專案，然後允許與其他使用者的連線，這樣多個使用者可以看到您的工作。</span><span class="sxs-lookup"><span data-stu-id="23403-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="23403-145">[下一個教學課程：準備 Unity 進行開發](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="23403-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

