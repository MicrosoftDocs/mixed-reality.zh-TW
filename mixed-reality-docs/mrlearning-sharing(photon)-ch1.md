---
title: 多使用者功能教學課程 - 1。 設定 Photon Unity 網路
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031335"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="0be2e-105">1.設定 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="0be2e-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="0be2e-106">概觀</span><span class="sxs-lookup"><span data-stu-id="0be2e-106">Overview</span></span>

<span data-ttu-id="0be2e-107">在本教學課程中，您將了解如何藉由將 Photon Unity 網路 (PUN) 匯入 Unity 專案，來準備建立共用體驗。</span><span class="sxs-lookup"><span data-stu-id="0be2e-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="0be2e-108">Photon 是可讓混合實境開發人員用來建立共用體驗的眾多網路功能選項之一。</span><span class="sxs-lookup"><span data-stu-id="0be2e-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="0be2e-109">您將了解如何建立 Photon 帳戶、匯入 Photon，以及建立選用的本機伺服器</span><span class="sxs-lookup"><span data-stu-id="0be2e-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="0be2e-110">目標</span><span class="sxs-lookup"><span data-stu-id="0be2e-110">Objectives</span></span>

* <span data-ttu-id="0be2e-111">了解如何建立 Photon 帳戶</span><span class="sxs-lookup"><span data-stu-id="0be2e-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="0be2e-112">了解如何尋找和匯入 Photon Unity 網路功能</span><span class="sxs-lookup"><span data-stu-id="0be2e-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="0be2e-113">設定本機 Photon 伺服器</span><span class="sxs-lookup"><span data-stu-id="0be2e-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0be2e-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="0be2e-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="0be2e-115">如果您尚未完成[入門教學課程](mrlearning-base.md)及 [Azure Spatial Anchors 入門教學課程](mrlearning-asa-ch1.md)的教學課程系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="0be2e-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="0be2e-116">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="0be2e-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="0be2e-117">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="0be2e-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="0be2e-118">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="0be2e-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="0be2e-119">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="0be2e-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="0be2e-120">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="0be2e-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="0be2e-121">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="0be2e-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="0be2e-122">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="0be2e-122">Setting up Photon</span></span>

1. <span data-ttu-id="0be2e-123">設定 [Photon](https://dashboard.photonengine.com//Account/SignUp) 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0be2e-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="0be2e-124">按一下[此連結](https://dashboard.photonengine.com//Account/SignUp)來瀏覽至 Photon 註冊頁面。</span><span class="sxs-lookup"><span data-stu-id="0be2e-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="0be2e-125">遵循註冊頁面上的指示來建立帳戶。</span><span class="sxs-lookup"><span data-stu-id="0be2e-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="0be2e-128">按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="0be2e-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="0be2e-130">從 [Photon 類型] 底下的下拉式功能表中，選取 [Photon PUN]。</span><span class="sxs-lookup"><span data-stu-id="0be2e-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="0be2e-131">然後為其命名。</span><span class="sxs-lookup"><span data-stu-id="0be2e-131">Then give it a name.</span></span> <span data-ttu-id="0be2e-132">在此範例中，我們將其命名為 HoloLensPhotonProject。</span><span class="sxs-lookup"><span data-stu-id="0be2e-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="0be2e-133">完成後，按一下 [建立] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0be2e-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="0be2e-135">返回您的應用程式頁面，您應該會看到類似下圖的畫面。</span><span class="sxs-lookup"><span data-stu-id="0be2e-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="0be2e-136">按一下應用程式識別碼並加以複製。</span><span class="sxs-lookup"><span data-stu-id="0be2e-136">Click the application ID and copy it.</span></span> <span data-ttu-id="0be2e-137">將其貼入您可以輕鬆存取的位置。</span><span class="sxs-lookup"><span data-stu-id="0be2e-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="0be2e-139">建立新的 Unity 專案，並將其命名為 HLSharingProject。</span><span class="sxs-lookup"><span data-stu-id="0be2e-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="0be2e-140">如需如何建立新 Unity 專案的指示，請參閱[基礎課程模組的＜建立 Unity 專案＞一節](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="0be2e-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="0be2e-141">專案載入後，按一下 [資產存放區] 索引標籤，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="0be2e-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="0be2e-142">然後，在下圖中醒目顯示的搜尋方塊中輸入 PUN，然後從搜尋結果中選取 [Photon PUN 2 - 免費] 資產。</span><span class="sxs-lookup"><span data-stu-id="0be2e-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="0be2e-144">按下 [下載] 和 [匯入] 按鈕來下載並匯入此資產。</span><span class="sxs-lookup"><span data-stu-id="0be2e-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="0be2e-146">一旦 Photon 完成匯入程序後，Pun 精靈會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0be2e-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="0be2e-147">取出步驟 4 中取得的應用程式識別碼 (應該位於您的剪貼簿中)，將其貼到 [AppID] 方塊中，然後按下 [安裝專案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0be2e-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="0be2e-149">成功新增 AppID 之後，請在 [資產] 中瀏覽至 [Photon] -> [PhotonUnityNetworking] -> [資源] -> [PhotonServerSettings]。</span><span class="sxs-lookup"><span data-stu-id="0be2e-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="0be2e-150">選取 [使用名稱伺服器] 選項，並將固定區域設定為 [美國] 或您的 Photon 服務區域。</span><span class="sxs-lookup"><span data-stu-id="0be2e-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="0be2e-152">恭喜！</span><span class="sxs-lookup"><span data-stu-id="0be2e-152">Congratulations</span></span>

<span data-ttu-id="0be2e-153">您已成功建立 Photon 帳戶、設定本機 Photon 伺服器，並將 PUN 匯入 Unity。</span><span class="sxs-lookup"><span data-stu-id="0be2e-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="0be2e-154">下一個步驟是設定專案，並允許與其他使用者進行連線，讓多個使用者可以看到您的工作。</span><span class="sxs-lookup"><span data-stu-id="0be2e-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="0be2e-155">[下一個教學課程：2.準備 Unity 以進行開發](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="0be2e-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
