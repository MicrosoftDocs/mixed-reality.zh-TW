---
title: MR 和 Azure 303-自然語言理解（LUIS）
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure Language Understanding 智慧服務（LUIS）。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合現實，學術，unity，教學課程，api，語言理解智慧服務，luis，hololens，沉浸，vr
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926810"
---
>[!NOTE]
><span data-ttu-id="ce0c3-104">混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ce0c3-105">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ce0c3-106">這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ce0c3-107">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ce0c3-108">未來將會有一系列新的教學課程，將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ce0c3-109">此通知會在張貼時，使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="ce0c3-110">MR 和 Azure 303：自然語言理解（LUIS）</span><span class="sxs-lookup"><span data-stu-id="ce0c3-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="ce0c3-111">在此課程中，您將瞭解如何使用 Azure 認知服務搭配 Language Understanding API，將 Language Understanding 整合到混合的現實應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![實驗室結果](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="ce0c3-113">*Language Understanding （LUIS）* 是一項 Microsoft Azure 的服務，可讓應用程式從使用者輸入中實現意義，例如，藉由以自己的單字來解壓縮個人可能想要的內容。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="ce0c3-114">這是透過機器學習來達成，這會瞭解並學習輸入資訊，然後可以使用詳細的相關資訊來回複。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="ce0c3-115">如需詳細資訊，請造訪[Azure Language Understanding （LUIS）頁面](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="ce0c3-116">完成此課程之後，您將擁有一個混合現實的沉浸式耳機應用程式，其將能夠執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="ce0c3-117">使用連接到沉浸式耳機的麥克風來捕捉使用者輸入語音。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="ce0c3-118">將已捕獲的聽寫傳送至*Azure Language Understanding 智慧型服務*（*LUIS*）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="ce0c3-119">讓 LUIS 從傳送資訊中解壓縮意義，這將會進行分析，並嘗試判斷使用者的要求意圖。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="ce0c3-120">開發會包含應用程式的建立，讓使用者能夠使用語音和/或注視來變更場景中物件的大小和色彩。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="ce0c3-121">將不會涵蓋使用動作控制器。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="ce0c3-122">在您的應用程式中，您可以決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ce0c3-123">本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="ce0c3-124">您的工作是使用您從這個課程取得的知識，來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="ce0c3-125">準備好訓練 LUIS 數次，如第[12 章](#chapter-12--improving-your-luis-service)所述。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="ce0c3-126">您會得到更好的結果，也就是 LUIS 已定型的次數。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="ce0c3-127">裝置支援</span><span class="sxs-lookup"><span data-stu-id="ce0c3-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ce0c3-128">粗</span><span class="sxs-lookup"><span data-stu-id="ce0c3-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ce0c3-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ce0c3-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ce0c3-130"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="ce0c3-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="ce0c3-131">MR 和 Azure 303：自然語言理解（LUIS）</span><span class="sxs-lookup"><span data-stu-id="ce0c3-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="ce0c3-132">✔️</span><span class="sxs-lookup"><span data-stu-id="ce0c3-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ce0c3-133">✔️</span><span class="sxs-lookup"><span data-stu-id="ce0c3-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ce0c3-134">雖然此課程主要著重于 Windows Mixed Reality 沉浸式（VR）耳機，但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ce0c3-135">隨著課程的遵循，您會看到您可能需要用來支援 HoloLens 的任何變更的附注。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ce0c3-136">使用 HoloLens 時，您可能會在語音捕獲期間發現一些回應。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce0c3-137">必要條件</span><span class="sxs-lookup"><span data-stu-id="ce0c3-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ce0c3-138">本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ce0c3-139">也請注意，本檔中的必要條件和書面指示，代表在撰寫本文時已測試和驗證的內容（5月2018）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ce0c3-140">您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體，但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容，而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ce0c3-141">在此課程中，我們建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ce0c3-142">[與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦，可用於沉浸式（VR）耳機開發</span><span class="sxs-lookup"><span data-stu-id="ce0c3-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ce0c3-143">已啟用開發人員模式的 Windows 10 秋季建立者更新（或更新版本）</span><span class="sxs-lookup"><span data-stu-id="ce0c3-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="ce0c3-144">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="ce0c3-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="ce0c3-145">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="ce0c3-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="ce0c3-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ce0c3-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="ce0c3-147">已啟用開發人員模式的[Windows Mixed Reality 沉浸（VR）耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="ce0c3-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ce0c3-148">一組具有內建麥克風的耳機（如果耳機沒有內建的 mic 和喇叭）</span><span class="sxs-lookup"><span data-stu-id="ce0c3-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="ce0c3-149">適用于 Azure 設定和 LUIS 抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="ce0c3-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ce0c3-150">開始之前</span><span class="sxs-lookup"><span data-stu-id="ce0c3-150">Before you start</span></span>

1.  <span data-ttu-id="ce0c3-151">為避免在建立此專案時發生問題，強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案（長資料夾路徑可能會在組建階段造成問題）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="ce0c3-152">若要允許您的電腦啟用聽寫，請移至**Windows 設定 > 隱私權 > 語音，筆跡 & 輸入**，然後按下 [**開啟語音服務] 按鈕並輸入建議**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="ce0c3-153">本教學課程中的程式碼可讓您從電腦上的**預設麥克風裝置**設定記錄。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="ce0c3-154">請確定預設的麥克風裝置已設定為您要用來捕捉語音的裝置。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="ce0c3-155">如果您的耳機有內建的麥克風，請確定已在*Mixed Reality 入口網站*設定中開啟 [*當我戴耳機，切換到耳機 mic]* 選項。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![設定沉浸式頭戴式裝置](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="ce0c3-157">第1章–設定 Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="ce0c3-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="ce0c3-158">若要在 Azure 中使用*Language Understanding*服務，您將需要設定服務的實例，讓應用程式可以使用。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="ce0c3-159">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ce0c3-160">如果您還沒有 Azure 帳戶，您將需要建立一個。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ce0c3-161">如果您是在課堂或實驗室的情況下進行本教學課程，請洽詢您的講師或其中一個 proctors，以協助設定您的新帳戶。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ce0c3-162">登入之後，按一下左上角的 [**新增**]，並搜尋*Language Understanding*，然後按一下**Enter 鍵**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![建立 LUIS 資源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="ce0c3-164">在較新的入口網站中，**新**的「可能」已取代為「**建立資源**」。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="ce0c3-165">右側的新頁面將會提供 Language Understanding 服務的描述。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="ce0c3-166">在此頁面的左下方，選取 [**建立**] 按鈕，以建立此服務的實例。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![LUIS 服務建立-法律注意事項](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="ce0c3-168">當您按一下 [建立] 之後：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="ce0c3-169">為此服務實例插入您想要的**名稱**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="ce0c3-170">選取**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="ce0c3-171">選取適合您的**定價層**，如果這是您第一次建立*LUIS 服務*，您應該可以使用免費層（名為 F0）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="ce0c3-172">在此課程中，免費配置應該就夠多了。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="ce0c3-173">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ce0c3-174">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ce0c3-175">建議您將與單一專案相關聯的所有 Azure 服務（例如這些課程）都保留在通用資源群組下）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="ce0c3-176">如果您想要深入瞭解 Azure 資源群組，請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="ce0c3-177">判斷資源群組的**位置**（如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ce0c3-178">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ce0c3-179">某些 Azure 資產僅適用于特定區域。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="ce0c3-180">您也必須確認您已瞭解適用于此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="ce0c3-181">選取 **\[建立\]** 。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-181">Select **Create**.</span></span>

        ![建立 LUIS 服務-使用者輸入](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="ce0c3-183">按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="ce0c3-184">建立服務實例之後，入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![新增 Azure 通知映射](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="ce0c3-186">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-186">Click on the notification to explore your new Service instance.</span></span>

    ![成功建立資源通知](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="ce0c3-188">按一下通知中的 [**移至資源**] 按鈕，探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ce0c3-189">您將會進入新的 LUIS 服務實例。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![存取 LUIS 金鑰](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="ce0c3-191">在本教學課程中，您的應用程式將需要呼叫您的服務，這會透過使用您服務的訂用帳戶金鑰來完成。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="ce0c3-192">從*LUIS API*服務的 [*快速入門*] 頁面，流覽至第一個步驟，*抓取您的金鑰*，然後按一下 [**金鑰**] （您也可以按一下位於 [服務] 導覽功能表中的藍色超連結鍵，以按鍵圖示表示）來達成此目的。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="ce0c3-193">這會顯示您的服務*金鑰*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="ce0c3-194">複製其中一個顯示的金鑰，因為您稍後會在專案中用到。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="ce0c3-195">在 [*服務*] 頁面中，按一下 [ *Language Understanding 入口網站*]，將其重新導向至您將用來在 LUIS 應用程式中建立新服務的網頁。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="ce0c3-196">第2章– Language Understanding 入口網站</span><span class="sxs-lookup"><span data-stu-id="ce0c3-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="ce0c3-197">在本節中，您將瞭解如何在 LUIS 入口網站上建立 LUIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ce0c3-198">請注意，在本章中設定*實體*、*意圖*和*語句*，只是建立 LUIS 服務的第一步：您也需要重新定型服務數次，讓它更準確。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="ce0c3-199">本課程的[最後一章](#chapter-12--improving-your-luis-service)涵蓋重新定型您的服務，因此請確定您已完成。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="ce0c3-200">到達*Language Understanding 入口網站*時，您可能需要登入（如果您尚未這麼做），其認證與您的 Azure 入口網站相同。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS 登入頁面](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="ce0c3-202">如果這是您第一次使用 LUIS，您將需要向下滾動到歡迎頁面底部，以尋找並按一下 [**建立 LUIS 應用程式**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![建立 LUIS 應用程式頁面](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="ce0c3-204">登入之後，按一下 [**我的應用程式**] （如果您目前不在該區段中）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="ce0c3-205">然後，您可以按一下 [**建立新的應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-205">You can then click on **Create new app**.</span></span>

    ![LUIS-我的應用程式影像](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="ce0c3-207">提供您的應用程式*名稱*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="ce0c3-208">如果您的應用程式應該瞭解與英文不同的語言，您應該將*文化*特性變更為適當的語言。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="ce0c3-209">您也可以在這裡新增新 LUIS 應用程式的*描述*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-建立新的應用程式](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="ce0c3-211">當您按下 [**完成**] 之後，您將會進入新*LUIS*應用程式的 [*組建*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="ce0c3-212">這裡有幾個重要的概念需要瞭解：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="ce0c3-213">*意圖*：代表將在使用者的查詢之後呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="ce0c3-214">*意圖*可能會有一或多個*實體*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="ce0c3-215">*實體*是查詢的元件，可描述與*意圖*相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="ce0c3-216">*語句*是開發人員所提供的查詢範例，LUIS 會用它來訓練自己。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="ce0c3-217">如果這些概念並非完全清楚，請別擔心，因為本課程將在本章中進一步說明。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="ce0c3-218">您將從建立此課程所需的*實體*開始。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="ce0c3-219">在頁面的左側，按一下 [*實體*]，然後按一下 [**建立新實體**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![建立新實體](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="ce0c3-221">呼叫新的實體*色彩*，將其類型設定為 [*簡單*]，然後按 [**完成**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![建立簡單的實體色彩](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="ce0c3-223">重複此程式以建立三個（3）個更簡單的實體，名為：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="ce0c3-224">*升遷*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-224">*upsize*</span></span>
    -   <span data-ttu-id="ce0c3-225">*縮減*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-225">*downsize*</span></span>
    -   <span data-ttu-id="ce0c3-226">*設定*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-226">*target*</span></span>

<span data-ttu-id="ce0c3-227">結果看起來應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-227">The result should look like the image below:</span></span>

![建立實體的結果](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="ce0c3-229">此時您可以開始建立*意圖*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="ce0c3-230">請勿刪除 [**無**] 意圖。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="ce0c3-231">在頁面的左側，按一下 [**意圖**]，然後按一下 [**建立新的意圖**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![建立新意圖](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="ce0c3-233">呼叫新的*意圖* **ChangeObjectColor**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ce0c3-234">此*意圖*名稱會在本課程稍後的程式碼中使用，因此若要獲得最佳結果，請依照所提供的方式使用此名稱。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="ce0c3-235">一旦您確認名稱，系統就會將您導向至 [意圖] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS-意圖頁面](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="ce0c3-237">您會發現有一個文字方塊要求您輸入5個或更多不同的*語句*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="ce0c3-238">LUIS 會將所有語句轉換成小寫。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="ce0c3-239">在頂端的文字方塊中插入下列*語句*（目前有*大約5個範例*的文字類型 。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="ce0c3-240">），然後按**enter**鍵：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="ce0c3-241">您會注意到新的*語句*會出現在下面的清單中。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="ce0c3-242">遵循相同的程式，插入下列六個（6）語句：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="ce0c3-243">針對您已建立的每個語句，您必須識別 LUIS 要使用哪些單字做為實體。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="ce0c3-244">在此範例中，您必須將所有色彩標記為*色彩*實體，並將目標的所有可能參考標示為*目標*實體。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="ce0c3-245">若要這麼做，請嘗試在第一個語句中按一下 [*圓柱*]，然後選取 [*目標*]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![識別語句目標](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="ce0c3-247">現在按一下第一個語句中的*紅色*文字，然後選取 [*色彩*]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![識別語句的實體](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="ce0c3-249">為下一行加上標籤，其中*cube*應該是*目標*，而*黑色*則應該是*色彩*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="ce0c3-250">也請注意，我們所提供的「 *this*」、「 *it*」和「 *this object*」這幾個字，因此也有非特定的目標型別可供使用。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="ce0c3-251">重複上述程式，直到所有語句都已標示實體為止。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="ce0c3-252">如果您需要協助，請參閱下圖。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="ce0c3-253">選取字詞以將其標示為實體時：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="ce0c3-254">針對單一字組，只要按一下即可。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-254">For single words just click them.</span></span>
    > - <span data-ttu-id="ce0c3-255">針對一組二或多個單字，按一下開頭，然後在集合結尾處。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ce0c3-256">您可以使用 [*權杖] 視圖*切換按鈕，在**實體/標記視圖**之間切換！</span><span class="sxs-lookup"><span data-stu-id="ce0c3-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="ce0c3-257">結果應如下圖所示，其中顯示 [**實體/權杖] 視圖**：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![& 實體視圖的權杖](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="ce0c3-259">此時，請按頁面右上方的 [**定型**] 按鈕，然後等候小型的圓角指標變成綠色。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="ce0c3-260">這表示已成功訓練 LUIS 以辨識此意圖。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![訓練 LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="ce0c3-262">做為您的練習，使用實體*target*、*升遷*和*縮減*，建立名為**ChangeObjectSize**的新意圖。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="ce0c3-263">遵循與上一個意圖相同的程式，插入下列八個（8）語句以進行*大小*變更：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="ce0c3-264">結果應如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-264">The result should be like the one in the image below:</span></span>

    ![設定 ChangeObjectSize token/實體](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="ce0c3-266">當意圖、 **ChangeObjectColor**和**ChangeObjectSize**都已建立並定型之後，請按一下頁面頂端的 [**發佈**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![發行 LUIS 服務](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="ce0c3-268">在 [*發佈*] 頁面上，您將會完成併發布您的 LUIS 應用程式，讓您的程式碼可以存取它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="ce0c3-269">將下拉式*發行*設定為 [**生產**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="ce0c3-270">將*時區*設定為您的時區。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="ce0c3-271">勾選 [**包含所有預測的意圖分數**] 方塊。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="ce0c3-272">按一下 [**發佈至生產**位置]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-272">Click on **Publish to Production Slot**.</span></span>

        ![發行設定](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="ce0c3-274">在 [*資源和金鑰*] 區段中：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="ce0c3-275">選取您在 Azure 入口網站中為服務實例設定的區域。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="ce0c3-276">您會注意到下列**Starter_Key**元素，請予以忽略。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="ce0c3-277">按一下 [**新增金鑰**]，並插入當您建立服務實例時，在 Azure 入口網站中取得的*金鑰*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="ce0c3-278">如果您的 Azure 和 LUIS 入口網站已登入相同的使用者，您將會在*租使用者名稱*、訂用帳戶*名稱*和您想要使用的*金鑰*（將與您先前在 Azure 入口網站中提供的名稱相同）中提供下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="ce0c3-279">在 [*端點*] 下方，建立對應至所插入金鑰的端點複本，您很快就會在程式碼中使用它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="ce0c3-280">第3章–設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="ce0c3-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="ce0c3-281">以下是使用混合現實進行開發的一般設定，因此是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ce0c3-282">開啟*Unity* ，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-282">Open *Unity* and click **New**.</span></span> 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="ce0c3-284">現在您將需要提供 Unity 專案名稱、插入**MR_LUIS**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="ce0c3-285">請確定 [專案類型] 設定為 [ **3d**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="ce0c3-286">將位置設定為適合您的**位置**（請記住，接近根目錄較佳）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ce0c3-287">然後，按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-287">Then, click **Create project**.</span></span>

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="ce0c3-289">在 Unity 開啟的情況下，值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ce0c3-290">移至 編輯 > 喜好設定，然後在新視窗中，流覽至 **外部工具**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ce0c3-291">將**外部腳本編輯器**變更為**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ce0c3-292">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-292">Close the **Preferences** window.</span></span>

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="ce0c3-294">接著，移至 [檔案] **> [組建設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至**通用 Windows 平臺**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![[組建設定] 視窗，將平臺切換至 UWP。](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="ce0c3-296">移至 [檔案] **> [組建設定**]，並確認：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="ce0c3-297">**目標裝置**已設定為**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="ce0c3-298">若為 Microsoft HoloLens，請將**目標裝置**設定為*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="ce0c3-299">**組建類型**設定為**D3D**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="ce0c3-300">**SDK**已設定為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="ce0c3-301">**Visual Studio 版本**設定為 [**最新安裝**]</span><span class="sxs-lookup"><span data-stu-id="ce0c3-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="ce0c3-302">**組建和執行**設定為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="ce0c3-303">儲存場景，並將它加入至組建。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="ce0c3-304">選取 [新增] [**開啟場景**] 來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ce0c3-305">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-305">A save window will appear.</span></span>
        
            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="ce0c3-307">為此建立新的資料夾，並在任何未來的場景中選取 [**新增資料夾**] 按鈕，以建立新的資料夾，將其命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的腳本資料夾](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="ce0c3-309">開啟新建立的 [**幕後**] 資料夾，然後在 [*檔案名*：文字] 欄位中輸入**MR_LuisScene**，然後按 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![為新場景指定名稱。](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="ce0c3-311">[*組建設定*] 中的其餘設定，現在應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="ce0c3-312">在 [*組建設定*] 視窗中，按一下 [ **Player 設定**] 按鈕，這會在偵測*器*所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟 [播放] [設定]。](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="ce0c3-314">在此面板中，需要驗證幾項設定：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="ce0c3-315">在 [**其他設定**] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="ce0c3-316">**腳本執行階段版本**應為**穩定**（.net 3.5 對等）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="ce0c3-317">**腳本後端**應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="ce0c3-318">**API 相容性層級**應該是 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="ce0c3-320">在 [**發行設定**] 索引標籤的 [**功能**] 底下，檢查：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="ce0c3-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-321">**InternetClient**</span></span>
        2. <span data-ttu-id="ce0c3-322">**十分**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-322">**Microphone**</span></span>

            ![正在更新發行設定。](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="ce0c3-324">在面板中，于 [ **XR 設定**] （在 [**發佈設定**] 下方找到）中，支援 [勾選**虛擬實境**]，並確定已新增 [ **Windows Mixed Reality SDK** ]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 設定。](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="ce0c3-326">回到*組建設定* _Unity C#_ 專案已不再呈現灰色;勾選 [] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="ce0c3-327">關閉 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="ce0c3-328">儲存場景和專案（**file > 儲存場景/檔案 > 儲存專案**）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="ce0c3-329">第4章–建立場景</span><span class="sxs-lookup"><span data-stu-id="ce0c3-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ce0c3-330">如果您想要略過此課程的*Unity 設定*元件，並繼續直接進入程式碼，您可以下載這個[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，將它匯入到您的專案中做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行[第5章](#chapter-5--create-the-microphonemanager-class)。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="ce0c3-331">以滑鼠右鍵按一下 [階層]*面板*的空白區域，然後在 [ **3d 物件**] 下加入**平面**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![建立平面。](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="ce0c3-333">請注意，當*您再次以*滑鼠右鍵按一下階層以建立更多物件時，如果您仍然選取最後一個物件，選取的物件將會是新物件的父系。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="ce0c3-334">請避免這種情況，在階層內的空白處按一下滑鼠左鍵，然後按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="ce0c3-335">重複上述程式來新增下列物件：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="ce0c3-336">*Sphere*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-336">*Sphere*</span></span>
    2. <span data-ttu-id="ce0c3-337">*柱*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-337">*Cylinder*</span></span>
    3. <span data-ttu-id="ce0c3-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-338">*Cube*</span></span>
    4. <span data-ttu-id="ce0c3-339">*3D 文字*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-339">*3D Text*</span></span>

4.  <span data-ttu-id="ce0c3-340">產生*的場景階層*應如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![場景階層設定。](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="ce0c3-342">以滑鼠左鍵按一下**主要相機**以選取它，查看 [*檢查] 面板*，您將會看到相機物件及其所有元件。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="ce0c3-343">按一下位於 [偵測*器] 面板*最下方的 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![新增音訊來源](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="ce0c3-345">搜尋稱為「*音訊來源*」的元件，如上所示。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="ce0c3-346">也請確定主要攝影機的 [*轉換*] 元件設定為（0，0，0），只要按下相機*轉換*元件旁的**齒輪**圖示，然後選取 [**重設**] 即可完成。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="ce0c3-347">接著，*轉換*元件看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="ce0c3-348">*Position*設定為**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="ce0c3-349">*旋轉*設定為**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="ce0c3-350">針對 Microsoft HoloLens，您也必須變更下列各項，這是**相機**元件的一部分，位於您的**主要攝影機**上：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="ce0c3-351">**清除旗標：** 單色。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="ce0c3-352">**背景**' 黑色，Alpha 0 ' –十六進位色彩： #00000000。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="ce0c3-353">在**平面**上按一下滑鼠左鍵加以選取。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="ce0c3-354">在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="ce0c3-355">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="ce0c3-356">**X**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-356">**X**</span></span> | <span data-ttu-id="ce0c3-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-357">**Y**</span></span>                  | <span data-ttu-id="ce0c3-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-358">**Z**</span></span> |
    | <span data-ttu-id="ce0c3-359">0</span><span class="sxs-lookup"><span data-stu-id="ce0c3-359">0</span></span>     | <span data-ttu-id="ce0c3-360">-1</span><span class="sxs-lookup"><span data-stu-id="ce0c3-360">-1</span></span>                     | <span data-ttu-id="ce0c3-361">0</span><span class="sxs-lookup"><span data-stu-id="ce0c3-361">0</span></span>     |


10. <span data-ttu-id="ce0c3-362">在**球體**上按一下滑鼠左鍵加以選取。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="ce0c3-363">在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="ce0c3-364">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="ce0c3-365">**X**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-365">**X**</span></span> | <span data-ttu-id="ce0c3-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-366">**Y**</span></span>                  | <span data-ttu-id="ce0c3-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-367">**Z**</span></span> |
    | <span data-ttu-id="ce0c3-368">2</span><span class="sxs-lookup"><span data-stu-id="ce0c3-368">2</span></span>     | <span data-ttu-id="ce0c3-369">1</span><span class="sxs-lookup"><span data-stu-id="ce0c3-369">1</span></span>                      | <span data-ttu-id="ce0c3-370">2</span><span class="sxs-lookup"><span data-stu-id="ce0c3-370">2</span></span>     |

11. <span data-ttu-id="ce0c3-371">在**圓柱**上按一下滑鼠左鍵加以選取。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="ce0c3-372">在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="ce0c3-373">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="ce0c3-374">**X**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-374">**X**</span></span> | <span data-ttu-id="ce0c3-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-375">**Y**</span></span>                  | <span data-ttu-id="ce0c3-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-376">**Z**</span></span> |
    | <span data-ttu-id="ce0c3-377">-2</span><span class="sxs-lookup"><span data-stu-id="ce0c3-377">-2</span></span>    | <span data-ttu-id="ce0c3-378">1</span><span class="sxs-lookup"><span data-stu-id="ce0c3-378">1</span></span>                      | <span data-ttu-id="ce0c3-379">2</span><span class="sxs-lookup"><span data-stu-id="ce0c3-379">2</span></span>     |

12. <span data-ttu-id="ce0c3-380">在**Cube**上按一下滑鼠左鍵加以選取。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="ce0c3-381">在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="ce0c3-382">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="ce0c3-383">轉換-*旋轉*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="ce0c3-384">**X**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-384">**X**</span></span> | <span data-ttu-id="ce0c3-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-385">**Y**</span></span>                   | <span data-ttu-id="ce0c3-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-386">**Z**</span></span> |  \| | <span data-ttu-id="ce0c3-387">**X**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-387">**X**</span></span> | <span data-ttu-id="ce0c3-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-388">**Y**</span></span>                  | <span data-ttu-id="ce0c3-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-389">**Z**</span></span> |
    | <span data-ttu-id="ce0c3-390">0</span><span class="sxs-lookup"><span data-stu-id="ce0c3-390">0</span></span>     | <span data-ttu-id="ce0c3-391">1</span><span class="sxs-lookup"><span data-stu-id="ce0c3-391">1</span></span>                       | <span data-ttu-id="ce0c3-392">4</span><span class="sxs-lookup"><span data-stu-id="ce0c3-392">4</span></span>     |  \| | <span data-ttu-id="ce0c3-393">45</span><span class="sxs-lookup"><span data-stu-id="ce0c3-393">45</span></span>    | <span data-ttu-id="ce0c3-394">45</span><span class="sxs-lookup"><span data-stu-id="ce0c3-394">45</span></span>                     | <span data-ttu-id="ce0c3-395">0</span><span class="sxs-lookup"><span data-stu-id="ce0c3-395">0</span></span>     | 

13. <span data-ttu-id="ce0c3-396">在**新的文字**物件上按一下滑鼠左鍵，加以選取。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="ce0c3-397">在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="ce0c3-398">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="ce0c3-399">轉換-*調整規模*</span><span class="sxs-lookup"><span data-stu-id="ce0c3-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="ce0c3-400">**X**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-400">**X**</span></span> | <span data-ttu-id="ce0c3-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-401">**Y**</span></span>                  | <span data-ttu-id="ce0c3-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-402">**Z**</span></span> |  \| | <span data-ttu-id="ce0c3-403">**X**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-403">**X**</span></span> | <span data-ttu-id="ce0c3-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-404">**Y**</span></span>               | <span data-ttu-id="ce0c3-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-405">**Z**</span></span> |
    | <span data-ttu-id="ce0c3-406">-2</span><span class="sxs-lookup"><span data-stu-id="ce0c3-406">-2</span></span>    | <span data-ttu-id="ce0c3-407">6</span><span class="sxs-lookup"><span data-stu-id="ce0c3-407">6</span></span>                      | <span data-ttu-id="ce0c3-408">9</span><span class="sxs-lookup"><span data-stu-id="ce0c3-408">9</span></span>     |  \| | <span data-ttu-id="ce0c3-409">0.1</span><span class="sxs-lookup"><span data-stu-id="ce0c3-409">0.1</span></span>   | <span data-ttu-id="ce0c3-410">0.1</span><span class="sxs-lookup"><span data-stu-id="ce0c3-410">0.1</span></span>                 | <span data-ttu-id="ce0c3-411">0.1</span><span class="sxs-lookup"><span data-stu-id="ce0c3-411">0.1</span></span>   | 

14. <span data-ttu-id="ce0c3-412">將 [**文字網格**] 元件中的**字型大小**變更為**50**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="ce0c3-413">將**文本網格**物件的*名稱*變更為 [**聽寫文字**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![建立3D 文字物件](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="ce0c3-415">階層式面板的結構現在看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![場景視圖中的文本網格](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="ce0c3-417">最後的場景看起來應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-417">The final scene should look like the image below:</span></span>

    ![場景視圖。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="ce0c3-419">第5章–建立 MicrophoneManager 類別</span><span class="sxs-lookup"><span data-stu-id="ce0c3-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="ce0c3-420">您即將建立的第一個腳本是*MicrophoneManager*類別。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="ce0c3-421">接下來，您將建立*LuisManager*、*行為*類別，最後是*注視*的課程（您可以隨意建立所有這些類別，不過這會在您每一章中討論）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="ce0c3-422">*MicrophoneManager*類別負責：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="ce0c3-423">偵測連接到耳機或電腦的錄製裝置（以何者為預設值）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="ce0c3-424">捕捉音訊（語音）並使用聽寫將其儲存為字串。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="ce0c3-425">聲音暫停之後，請將聽寫提交至*LuisManager*類別。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="ce0c3-426">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-426">To create this class:</span></span> 

1.  <span data-ttu-id="ce0c3-427">以滑鼠右鍵按一下 [*專案] 面板*中的 [**建立 > 資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="ce0c3-428">呼叫資料夾**腳本**。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-428">Call the folder **Scripts**.</span></span> 

    ![建立腳本資料夾。](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="ce0c3-430">建立**腳本**資料夾之後，按兩下它以開啟。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="ce0c3-431">然後，在該資料夾中，以滑鼠右鍵按一下 [**建立 > C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="ce0c3-432">將腳本命名為*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="ce0c3-433">按兩下 [ *MicrophoneManager* ]，以*Visual Studio*開啟它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="ce0c3-434">將下列命名空間新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="ce0c3-435">然後，在*MicrophoneManager*類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="ce0c3-436">現在必須加入*喚醒（）* 和*Start （）* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="ce0c3-437">當類別初始化時，將會呼叫這些：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-437">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="ce0c3-438">現在您需要應用程式用來啟動和停止語音捕捉的方法，並將它傳遞給*LuisManager*類別，您很快就會建立。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="ce0c3-439">新增語音暫停時將叫用的*聽寫處理常式*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="ce0c3-440">這個方法會將聽寫文字傳遞給*LuisManager*類別。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="ce0c3-441">刪除*Update （）* 方法，因為這個類別不會使用它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="ce0c3-442">請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ce0c3-443">此時，您會注意到 [ *Unity 編輯器] 主控台面板*中出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="ce0c3-444">這是因為程式碼會參考您將在下一章中建立的*LuisManager*類別。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="ce0c3-445">第6章–建立 LUISManager 類別</span><span class="sxs-lookup"><span data-stu-id="ce0c3-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="ce0c3-446">您現在可以建立*LuisManager*類別，這會呼叫 Azure LUIS 服務。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="ce0c3-447">此類別的目的是要從*MicrophoneManager*類別接收聽寫文字，並將其傳送至要分析的*Azure Language Understanding API* 。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="ce0c3-448">這個類別會將*JSON*回應還原序列化，並呼叫*行為*類別的適當方法來觸發動作。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="ce0c3-449">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-449">To create this class:</span></span> 

1.  <span data-ttu-id="ce0c3-450">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="ce0c3-451">在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立 > C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="ce0c3-452">將腳本命名為*LuisManager*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="ce0c3-453">按兩下腳本，以 Visual Studio 開啟它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="ce0c3-454">將下列命名空間新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="ce0c3-455">首先，您會在*LuisManager*類別**中建立三個類別（** 在相同的腳本檔案中，在*Start （）* 方法的上方），這會代表來自 Azure 的已還原序列化 JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="ce0c3-456">接下來，在*LuisManager*類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="ce0c3-457">請務必將您的 LUIS 端點放在現在（您將會從 LUIS 入口網站）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="ce0c3-458">現在必須加入*喚醒（）* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="ce0c3-459">當類別初始化時，會呼叫這個方法：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="ce0c3-460">現在您需要此應用程式使用的方法，將從*MicrophoneManager*類別收到的聽寫傳送至*LUIS*，然後接收和還原序列化回應。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="ce0c3-461">一旦決定意圖的值和相關聯的實體之後，就會將其傳遞給*行為*類別的實例，以觸發預期的動作。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="ce0c3-462">建立名為*AnalyseResponseElements （）* 的新方法，它會讀取產生的*AnalysedQuery*並判斷實體。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="ce0c3-463">一旦決定這些實體之後，它們就會傳遞給*行為*類別的實例，以便在動作中使用。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="ce0c3-464">刪除*Start （）* 和*Update （）* 方法，因為這個類別不會使用它們。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="ce0c3-465">請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="ce0c3-466">此時，您會注意到 [ *Unity 編輯器] 主控台面板*中出現數個錯誤。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="ce0c3-467">這是因為程式碼會參考您將在下一章中建立的*行為*類別。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="ce0c3-468">第7章–建立行為類別</span><span class="sxs-lookup"><span data-stu-id="ce0c3-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="ce0c3-469">*行為*類別將會使用*LuisManager*類別所提供的實體來觸發動作。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="ce0c3-470">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-470">To create this class:</span></span> 

1.  <span data-ttu-id="ce0c3-471">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="ce0c3-472">在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立 > C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="ce0c3-473">將腳本命名為*行為*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="ce0c3-474">按兩下腳本，以*Visual Studio*開啟它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="ce0c3-475">然後，在*行為*類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="ce0c3-476">新增*喚醒（）* 方法程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="ce0c3-477">當類別初始化時，會呼叫這個方法：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="ce0c3-478">下列方法是由*LuisManager*類別（您先前建立的）所呼叫，用來判斷哪個物件是查詢的目標，然後觸發適當的動作。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="ce0c3-479">加入*FindTarget （）* 方法，以判斷哪一個*Gameobject*是目前意圖的目標。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="ce0c3-480">如果實體中未定義明確目標，則此方法會將目標預設為 "gazed" 的*GameObject* 。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="ce0c3-481">刪除*Start （）* 和*Update （）* 方法，因為這個類別不會使用它們。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="ce0c3-482">請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="ce0c3-483">第8章–建立注視課程</span><span class="sxs-lookup"><span data-stu-id="ce0c3-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="ce0c3-484">完成此應用程式所需的最後一個類別是*注視*課程。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="ce0c3-485">這個類別會更新目前在使用者視覺焦點中的*GameObject*參考。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="ce0c3-486">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-486">To create this Class:</span></span> 

1.  <span data-ttu-id="ce0c3-487">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="ce0c3-488">在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立 > C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="ce0c3-489">將腳本命名為*注視*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="ce0c3-490">按兩下腳本，以*Visual Studio*開啟它。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="ce0c3-491">為此類別插入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-491">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="ce0c3-492">請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="ce0c3-493">第9章–完成場景設定</span><span class="sxs-lookup"><span data-stu-id="ce0c3-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="ce0c3-494">若要完成場景的設定，請將您在 [腳本] 資料夾中建立的每個腳本，拖曳至 [階層]*面板*中的**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="ce0c3-495">選取**主攝影機**並查看 [*檢查器] 面板*，您應該可以看到已附加的每個腳本，而且您會注意到每個尚未設定的腳本都有參數。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![設定相機參照目標。](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="ce0c3-497">若要正確設定這些參數，請遵循下列指示：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="ce0c3-498">*MicrophoneManager*：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="ce0c3-499">從 [階層]*面板*中，將 [**聽寫文字**] 物件拖曳至 [**聽寫文字**參數值] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="ce0c3-500">*行為*，從 [階層]*面板*：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="ce0c3-501">將 [**球體**] 物件拖曳至 [*球體*參考目標] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="ce0c3-502">將**圓柱**拖曳至 [*圓柱*參考目標] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="ce0c3-503">將**cube**拖曳至 [ *cube*參考目標] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="ce0c3-504">*注視*：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-504">*Gaze*:</span></span>

        - <span data-ttu-id="ce0c3-505">將 [*注視最大距離*] 設定為**300** （如果尚未這麼做）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="ce0c3-506">結果看起來應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-506">The result should look like the image below:</span></span>

    ![現在會顯示相機參考目標。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="ce0c3-508">第10章–在 Unity 編輯器中測試</span><span class="sxs-lookup"><span data-stu-id="ce0c3-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="ce0c3-509">測試場景設定是否已正確執行。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="ce0c3-510">請確定：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-510">Ensure that:</span></span>

-   <span data-ttu-id="ce0c3-511">所有腳本都會附加到**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="ce0c3-512">*主要相機偵測器面板*中的所有欄位都已正確指派。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="ce0c3-513">按下*Unity 編輯器*中的 [**播放**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="ce0c3-514">應用程式應在附加的沉浸式耳機內執行。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="ce0c3-515">嘗試幾個語句，例如：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="ce0c3-516">如果您在 Unity 主控台看到關於預設音訊裝置變更的錯誤，場景可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="ce0c3-517">這是因為混合現實入口網站處理具有耳機之內建麥克風的方式。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="ce0c3-518">如果您看到此錯誤，只要停止場景並重新啟動，就應該會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="ce0c3-519">第11章–組建和側載 UWP 解決方案</span><span class="sxs-lookup"><span data-stu-id="ce0c3-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="ce0c3-520">一旦確定應用程式是在 Unity 編輯器中運作，您就可以開始建立和部署。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="ce0c3-521">若要建立：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-521">To Build:</span></span>

1.  <span data-ttu-id="ce0c3-522">按一下 檔案 **> 儲存** 來儲存目前的場景。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="ce0c3-523">移至 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="ce0c3-524">勾選名為 [ **Unity C#專案**] 的方塊（建立 UWP 專案之後，適用于查看和偵錯工具代碼）。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="ce0c3-525">按一下 [**新增] [開啟場景**]，然後按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![組建設定視窗](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="ce0c3-527">系統會提示您選取要在其中建立解決方案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="ce0c3-528">建立*組建*資料夾，並在該資料夾內建立另一個資料夾，並使用您選擇的適當名稱。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="ce0c3-529">按一下 [**選取資料夾**]，在該位置開始組建。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="ce0c3-530">![建立組建資料夾](images/AzureLabs-Lab3-44.png)
    ![選取組建資料夾](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="ce0c3-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="ce0c3-531">Unity 完成建立（可能需要一些時間）之後，它應該會在組建的位置開啟 [檔案**瀏覽器**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="ce0c3-532">若要在本機電腦上部署：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="ce0c3-533">在*Visual Studio*中，開啟在[上一章](#chapter-10--test-in-the-unity-editor)中建立的方案檔。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="ce0c3-534">在**解決方案平臺**中，選取 [ **x86**]、[**本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="ce0c3-535">在 [**解決方案**設定] 中，選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="ce0c3-536">針對 Microsoft HoloLens，您可能會發現將此設定為 [*遠端電腦*] 比較容易，因此您不會行動網卡到電腦。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="ce0c3-537">不過，您也必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ce0c3-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="ce0c3-538">知道您的 HoloLens 的**IP 位址**，您可以在 *> Network & Internet > Wi-fi > Advanced 選項*的 [設定] 中找到它;IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="ce0c3-539">請確定**開發人員模式**已**開啟**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >* 。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![部署應用程式](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="ce0c3-541">移至 [**建立] 功能表**，然後按一下 [**部署方案**]，將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="ce0c3-542">您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好啟動！</span><span class="sxs-lookup"><span data-stu-id="ce0c3-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="ce0c3-543">啟動之後，應用程式會提示您授權存取_麥克風_。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="ce0c3-544">使用 [*動作控制器*] 或 [*語音輸入*]，或*鍵盤*按 [**是]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="ce0c3-545">第12章–改善您的 LUIS 服務</span><span class="sxs-lookup"><span data-stu-id="ce0c3-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="ce0c3-546">這一章非常重要，而且可能需要反復執行幾次，因為這有助於改善 LUIS 服務的精確度：請務必完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-546">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="ce0c3-547">若要改善 LUIS 所提供的瞭解層級，您需要捕捉新的語句，並使用它們來重新訓練您的 LUIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="ce0c3-548">例如，您可能已定型 LUIS 來瞭解「增加」和「升遷」，但您不想讓應用程式也瞭解「放大」之類的字詞嗎？</span><span class="sxs-lookup"><span data-stu-id="ce0c3-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="ce0c3-549">一旦使用您的應用程式數次，您所說的所有內容都將由 LUIS 收集，並可在 LUIS 入口網站中取得。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="ce0c3-550">遵循此[連結](https://www.luis.ai/home)移至入口網站應用程式，然後登入。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="ce0c3-551">當您使用 MS 認證登入之後，請按一下您的*應用程式名稱*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="ce0c3-552">按一下頁面左側的 [**審查端點語句**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![審查語句](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="ce0c3-554">您將會看到您的混合現實應用程式已傳送給 LUIS 的語句清單。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![語句清單](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="ce0c3-556">您會發現一些反白顯示的*實體*。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="ce0c3-557">藉由將滑鼠停留在每個反白顯示的字組上，您可以檢查每個語句，並判斷哪些實體已正確辨識、哪些實體錯誤，以及哪些實體已遺失。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="ce0c3-558">在上述範例中，發現 "魚叉式" 一字已反白顯示為目標，因此必須更正錯誤，這是藉由滑鼠游標停留在該字組上，然後按一下 [**移除標籤**] 來完成。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="ce0c3-559">![檢查語句](images/AzureLabs-Lab3-49.png)
![移除標籤影像](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="ce0c3-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="ce0c3-560">如果您發現完全錯誤的語句，可以使用畫面右側的 [**刪除**] 按鈕將它們刪除。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![刪除錯誤的語句](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="ce0c3-562">或者，如果您覺得 LUIS 已正確地解讀語句，您可以使用 [**新增至對齊的意圖**] 按鈕來驗證其理解。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![新增至對齊的意圖](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="ce0c3-564">排序所有顯示的語句之後，請嘗試並重載頁面，以查看是否有更多可用的功能。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="ce0c3-565">請務必重複此程式，以改善應用程式的瞭解。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="ce0c3-566">**玩得愉快！**</span><span class="sxs-lookup"><span data-stu-id="ce0c3-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="ce0c3-567">您完成的 LUIS 整合式應用程式</span><span class="sxs-lookup"><span data-stu-id="ce0c3-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="ce0c3-568">恭喜，您建立了一個混合現實應用程式來運用 Azure Language Understanding 智慧服務，以瞭解使用者所說的內容，並對該資訊採取行動。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![實驗室結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ce0c3-570">額外練習</span><span class="sxs-lookup"><span data-stu-id="ce0c3-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="ce0c3-571">練習1</span><span class="sxs-lookup"><span data-stu-id="ce0c3-571">Exercise 1</span></span>

<span data-ttu-id="ce0c3-572">使用此應用程式時，您可能會注意到，如果您注視 Floor 物件，並要求變更其色彩，它就會這麼做。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="ce0c3-573">您可以處理如何阻止應用程式變更樓層色彩？</span><span class="sxs-lookup"><span data-stu-id="ce0c3-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="ce0c3-574">練習2</span><span class="sxs-lookup"><span data-stu-id="ce0c3-574">Exercise 2</span></span>

<span data-ttu-id="ce0c3-575">嘗試擴充 LUIS 和應用程式功能，為場景中的物件新增額外的功能;例如，根據使用者所說的內容，在看眼點建立新的物件，然後能夠將這些物件與目前的場景物件搭配使用，以及現有的命令。</span><span class="sxs-lookup"><span data-stu-id="ce0c3-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
