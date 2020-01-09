---
title: 多使用者功能教學課程-1。 設定 Photon Unity 網路功能
description: 完成此課程，以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 57a23e34404e4bff653d74b7f6afc65adff8b19c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334336"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="9b050-105">1. 設定 Photon Unity 網路功能</span><span class="sxs-lookup"><span data-stu-id="9b050-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="9b050-106">概觀</span><span class="sxs-lookup"><span data-stu-id="9b050-106">Overview</span></span>

<span data-ttu-id="9b050-107">在本教學課程中，您將瞭解如何藉由將 Photon Unity 網路（雙關語）匯入 Unity 專案，來準備建立共用體驗。</span><span class="sxs-lookup"><span data-stu-id="9b050-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="9b050-108">Photon 是可讓混合現實開發人員建立共用體驗的幾個網路功能選項之一。</span><span class="sxs-lookup"><span data-stu-id="9b050-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="9b050-109">您將瞭解如何建立 Photon 帳戶、匯入 Photon，以及建立選用的本機伺服器</span><span class="sxs-lookup"><span data-stu-id="9b050-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="9b050-110">目標</span><span class="sxs-lookup"><span data-stu-id="9b050-110">Objectives</span></span>

* <span data-ttu-id="9b050-111">瞭解如何建立 Photon 帳戶</span><span class="sxs-lookup"><span data-stu-id="9b050-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="9b050-112">瞭解如何尋找和匯入 Photon Unity 網路功能</span><span class="sxs-lookup"><span data-stu-id="9b050-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="9b050-113">設定本機 Photon 伺服器</span><span class="sxs-lookup"><span data-stu-id="9b050-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b050-114">先決條件</span><span class="sxs-lookup"><span data-stu-id="9b050-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="9b050-115">如果您尚未完成[快速入門教學](mrlearning-base.md)課程系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="9b050-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="9b050-116">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦</span><span class="sxs-lookup"><span data-stu-id="9b050-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="9b050-117">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="9b050-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9b050-118">一些基本C#的程式設計能力</span><span class="sxs-lookup"><span data-stu-id="9b050-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="9b050-119">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="9b050-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
><span data-ttu-id="9b050-120">本教學課程系列需要<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a> ，而建議的版本是 unity 2019.1.14。</span><span class="sxs-lookup"><span data-stu-id="9b050-120">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="9b050-121">這會取代上述所連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="9b050-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="9b050-122">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="9b050-122">Setting up Photon</span></span>

1. <span data-ttu-id="9b050-123">設定[Photon](https://dashboard.photonengine.com//Account/SignUp)帳戶。</span><span class="sxs-lookup"><span data-stu-id="9b050-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="9b050-124">按一下[此連結](https://dashboard.photonengine.com//Account/SignUp)，流覽至 Photon 註冊頁面。</span><span class="sxs-lookup"><span data-stu-id="9b050-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="9b050-125">遵循註冊頁面上的指示來建立帳戶。</span><span class="sxs-lookup"><span data-stu-id="9b050-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="9b050-128">按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="9b050-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="9b050-130">從 [Photon 類型] 底下的下拉式功能表中，選取 [Photon 雙關語]。</span><span class="sxs-lookup"><span data-stu-id="9b050-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="9b050-131">然後為它命名。</span><span class="sxs-lookup"><span data-stu-id="9b050-131">Then give it a name.</span></span> <span data-ttu-id="9b050-132">在此範例中，我們將它命名為 HoloLensPhotonProject。</span><span class="sxs-lookup"><span data-stu-id="9b050-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="9b050-133">完成後，按一下 [建立] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9b050-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="9b050-135">返回您的應用程式頁面，您應該會看到類似下圖的畫面。</span><span class="sxs-lookup"><span data-stu-id="9b050-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="9b050-136">按一下 [應用程式識別碼] 並加以複製。</span><span class="sxs-lookup"><span data-stu-id="9b050-136">Click the application ID and copy it.</span></span> <span data-ttu-id="9b050-137">將它貼入您可以輕鬆存取的位置。</span><span class="sxs-lookup"><span data-stu-id="9b050-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="9b050-139">建立新的 unity 專案，並將其命名為 HLSharingProject。</span><span class="sxs-lookup"><span data-stu-id="9b050-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="9b050-140">如需如何建立新 Unity 專案的指示，請參閱[基底模組的「建立 Unity 專案」一節](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="9b050-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="9b050-141">專案載入後，按一下 [資產] [存放區] 索引標籤，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="9b050-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="9b050-142">然後，在下圖中反白顯示的搜尋方塊中，輸入雙關語，然後從搜尋結果中選取 Photon 雙關語2免費的資產。</span><span class="sxs-lookup"><span data-stu-id="9b050-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="9b050-144">按下 [下載] 和 [匯入] 按鈕，下載並匯入此資產。</span><span class="sxs-lookup"><span data-stu-id="9b050-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="9b050-146">一旦 Photon 完成匯入程式，就會出現雙關語 Wizard。</span><span class="sxs-lookup"><span data-stu-id="9b050-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="9b050-147">從步驟4取出 [應用程式識別碼] （應該位於您的剪貼簿中），將它貼到 [AppID] 方塊中，然後按下 [安裝專案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9b050-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="9b050-149">成功新增 AppID 之後，請流覽至 Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings 在 [資產] 中。</span><span class="sxs-lookup"><span data-stu-id="9b050-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="9b050-150">選取 [使用名稱伺服器] 選項，並將 [固定區域] 設定為 [US] 或您的 photon 服務區域。</span><span class="sxs-lookup"><span data-stu-id="9b050-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="9b050-152">恭喜您</span><span class="sxs-lookup"><span data-stu-id="9b050-152">Congratulations</span></span>

<span data-ttu-id="9b050-153">您已成功建立 Photon 帳戶、設定本機 Photon 伺服器，並將雙關語匯入 Unity。</span><span class="sxs-lookup"><span data-stu-id="9b050-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="9b050-154">下一個步驟是設定專案，並允許與其他使用者進行連線，讓多個使用者可以看到您的工作。</span><span class="sxs-lookup"><span data-stu-id="9b050-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="9b050-155">[下一個教學課程： 2. 讓 Unity 準備好進行開發](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="9b050-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
