---
title: 多使用者功能教學課程-1。 設定 Photon Unity 網路功能
description: 完成此課程，以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: c6a2bea3d50669000e81cad7c83ae6a69b8a847f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437742"
---
#  <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="40600-105">1. 設定 Photon Unity 網路功能</span><span class="sxs-lookup"><span data-stu-id="40600-105">1. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="40600-106">在本教學課程中，您將瞭解如何藉由將 Photon Unity 網路（雙關語）匯入 Unity 專案，來準備建立共用體驗。</span><span class="sxs-lookup"><span data-stu-id="40600-106">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="40600-107">Photon 是可讓混合現實開發人員建立共用體驗的幾個網路功能選項之一。</span><span class="sxs-lookup"><span data-stu-id="40600-107">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="40600-108">您將瞭解如何建立 Photon 帳戶、匯入 Photon，以及建立選用的本機伺服器</span><span class="sxs-lookup"><span data-stu-id="40600-108">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="40600-109">目標</span><span class="sxs-lookup"><span data-stu-id="40600-109">Objectives</span></span>

* <span data-ttu-id="40600-110">瞭解如何建立 Photon 帳戶</span><span class="sxs-lookup"><span data-stu-id="40600-110">Learn how to create a Photon account</span></span>

* <span data-ttu-id="40600-111">瞭解如何尋找和匯入 Photon Unity 網路功能</span><span class="sxs-lookup"><span data-stu-id="40600-111">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="40600-112">設定本機 Photon 伺服器</span><span class="sxs-lookup"><span data-stu-id="40600-112">Set up a local Photon server</span></span>

  

## <a name="setting-up-photon"></a><span data-ttu-id="40600-113">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="40600-113">Setting up Photon</span></span>

1. <span data-ttu-id="40600-114">設定[Photon](https://dashboard.photonengine.com//Account/SignUp)帳戶。</span><span class="sxs-lookup"><span data-stu-id="40600-114">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="40600-115">按一下[此連結](https://dashboard.photonengine.com//Account/SignUp)，流覽至 Photon 註冊頁面。</span><span class="sxs-lookup"><span data-stu-id="40600-115">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="40600-116">遵循註冊頁面上的指示來建立帳戶。</span><span class="sxs-lookup"><span data-stu-id="40600-116">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="40600-119">按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="40600-119">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="40600-121">從 [Photon 類型] 底下的下拉式功能表中，選取 [Photon 雙關語]。</span><span class="sxs-lookup"><span data-stu-id="40600-121">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="40600-122">然後為它命名。</span><span class="sxs-lookup"><span data-stu-id="40600-122">Then give it a name.</span></span> <span data-ttu-id="40600-123">在此範例中，我們將它命名為 HoloLensPhotonProject。</span><span class="sxs-lookup"><span data-stu-id="40600-123">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="40600-124">完成後，按一下 [建立] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="40600-124">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="40600-126">返回您的應用程式頁面，您應該會看到類似下圖的畫面。</span><span class="sxs-lookup"><span data-stu-id="40600-126">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="40600-127">按一下 [應用程式識別碼] 並加以複製。</span><span class="sxs-lookup"><span data-stu-id="40600-127">Click the application ID and copy it.</span></span> <span data-ttu-id="40600-128">將它貼入您可以輕鬆存取的位置。</span><span class="sxs-lookup"><span data-stu-id="40600-128">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="40600-130">建立新的 unity 專案，並將其命名為 HLSharingProject。</span><span class="sxs-lookup"><span data-stu-id="40600-130">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="40600-131">如需如何建立新 Unity 專案的指示，請參閱[基底模組的「建立 Unity 專案」一節](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="40600-131">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="40600-132">專案載入後，按一下 [資產] [存放區] 索引標籤，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="40600-132">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="40600-133">然後，在下圖中反白顯示的搜尋方塊中，輸入雙關語，然後從搜尋結果中選取 Photon 雙關語2免費的資產。</span><span class="sxs-lookup"><span data-stu-id="40600-133">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="40600-135">按下 [下載] 和 [匯入] 按鈕，下載並匯入此資產。</span><span class="sxs-lookup"><span data-stu-id="40600-135">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="40600-137">一旦 Photon 完成匯入程式，就會出現雙關語 Wizard。</span><span class="sxs-lookup"><span data-stu-id="40600-137">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="40600-138">從步驟4取出 [應用程式識別碼] （應該位於您的剪貼簿中），將它貼到 [AppID] 方塊中，然後按下 [安裝專案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="40600-138">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="40600-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="40600-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="40600-140">成功新增 AppID 之後，請流覽至 Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings 在 [資產] 中。</span><span class="sxs-lookup"><span data-stu-id="40600-140">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="40600-141">選取 [使用名稱伺服器] 選項，並將 [固定區域] 設定為 [US] 或您的 photon 服務區域。</span><span class="sxs-lookup"><span data-stu-id="40600-141">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="40600-143">恭喜您</span><span class="sxs-lookup"><span data-stu-id="40600-143">Congratulations</span></span>

<span data-ttu-id="40600-144">您已成功建立 Photon 帳戶、設定本機 Photon 伺服器，並將雙關語匯入 Unity。</span><span class="sxs-lookup"><span data-stu-id="40600-144">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="40600-145">下一個步驟是設定專案，並允許與其他使用者進行連線，讓多個使用者可以看到您的工作。</span><span class="sxs-lookup"><span data-stu-id="40600-145">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="40600-146">[下一個教學課程： 2. 讓 Unity 準備好進行開發](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="40600-146">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

