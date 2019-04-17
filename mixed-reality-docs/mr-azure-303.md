---
title: MR 和 Azure 303-自然語言理解 (LUIS)
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure Language Understanding Intelligence Service (LUIS)。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境，academy、 unity、 教學課程、 api、 language understanding intelligence service，luis，hololens 沉浸式 vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595912"
---
>[!NOTE]
><span data-ttu-id="7b2d8-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7b2d8-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7b2d8-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7b2d8-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7b2d8-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7b2d8-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="7b2d8-110">MR 和 Azure 303:自然語言理解 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="7b2d8-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="7b2d8-111">在此課程中，您將了解如何整合 Azure 認知服務，使用 Language Understanding API 的混合的實境應用程式中的 Language Understanding。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![實驗室結果](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="7b2d8-113">*Language Understanding (LUIS)* 是 Microsoft Azure 服務，例如可從使用者輸入的意義，透過擷取功能的人員可能會想，客戶推薦的能力提供應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="7b2d8-114">這是透過機器學習服務，可了解和學習輸入的資訊，並接著可以回覆詳細、 相關的資訊來達成。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="7b2d8-115">如需詳細資訊，請瀏覽[Azure Language Understanding (LUIS) 頁面](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="7b2d8-116">完成本課程之後，您必須能夠執行下列作業的混合的實境耳機沈浸式應用程式：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="7b2d8-117">擷取使用者輸入的語音，使用附加至沈浸式耳機式麥克風。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="7b2d8-118">傳送擷取的聽寫*Azure Language Understanding Intelligent Service* (*LUIS*)。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="7b2d8-119">具有 LUIS 擷取表示傳送資訊，就會分析，並嘗試判斷將進行使用者要求的目的。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="7b2d8-120">開發將包含建立的應用程式，使用者將能夠使用語音和/或視線變更大小和場景中物件的色彩。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="7b2d8-121">將未涵蓋的動作控制站使用。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="7b2d8-122">在您的應用程式，則您對於如何將整合結果進行設計。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="7b2d8-123">本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="7b2d8-124">它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="7b2d8-125">準備好訓練 LUIS 數次，其中涵蓋[第 12 章](#chapter-12--improving-your-luis-service)。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="7b2d8-126">您會更好的結果已訓練 LUIS 的更多時間。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="7b2d8-127">裝置支援</span><span class="sxs-lookup"><span data-stu-id="7b2d8-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7b2d8-128">課程</span><span class="sxs-lookup"><span data-stu-id="7b2d8-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7b2d8-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7b2d8-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7b2d8-130"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="7b2d8-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="7b2d8-131">MR 和 Azure 303:自然語言理解 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="7b2d8-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="7b2d8-132">✔️</span><span class="sxs-lookup"><span data-stu-id="7b2d8-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7b2d8-133">✔️</span><span class="sxs-lookup"><span data-stu-id="7b2d8-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="7b2d8-134">雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="7b2d8-135">當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="7b2d8-136">當使用 HoloLens，您可能會發現某些回應語音擷取期間。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7b2d8-137">先決條件</span><span class="sxs-lookup"><span data-stu-id="7b2d8-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="7b2d8-138">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="7b2d8-139">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="7b2d8-140">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊會完全符合您會發現在較新的軟體與以下所列內容.</span><span class="sxs-lookup"><span data-stu-id="7b2d8-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="7b2d8-141">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="7b2d8-142">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="7b2d8-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="7b2d8-143">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="7b2d8-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="7b2d8-144">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="7b2d8-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="7b2d8-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="7b2d8-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="7b2d8-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7b2d8-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="7b2d8-147">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="7b2d8-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="7b2d8-148">一組的耳機與內建的麥克風 （如果耳機沒有內建的麥克風和喇叭）</span><span class="sxs-lookup"><span data-stu-id="7b2d8-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="7b2d8-149">Azure 設定和 LUIS 擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="7b2d8-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="7b2d8-150">開始之前</span><span class="sxs-lookup"><span data-stu-id="7b2d8-150">Before you start</span></span>

1.  <span data-ttu-id="7b2d8-151">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="7b2d8-152">若要允許您的機器以啟用語音輸入，請移至**Windows 設定 > 隱私權 > 語音、 筆跡 & 輸入** 按鈕上按下**語音服務開啟與輸入的建議**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="7b2d8-153">本教學課程中的程式碼可讓您從錄製**預設麥克風裝置**在電腦上。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="7b2d8-154">請確定預設麥克風裝置設定為您想要用來擷取您的聲音。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="7b2d8-155">如果耳機有內建的麥克風，，請務必選擇 *「 我穿上我耳機，切換到耳機式麥克風 」* 開啟*混合實境入口網站*設定。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![設定 沈浸式耳機](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="7b2d8-157">第 1 章-設定 Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="7b2d8-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="7b2d8-158">若要使用*Language Understanding*服務在 Azure 中，您必須設定您的應用程式提供服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="7b2d8-159">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="7b2d8-160">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="7b2d8-161">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="7b2d8-162">一旦您登入，按一下**新增**在左上角，，然後搜尋*Language Understanding*，然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![建立 LUIS 資源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="7b2d8-164">單字**的新**可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="7b2d8-165">向新的頁面會提供 Language Understanding 服務的描述。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="7b2d8-166">在左下方的這個頁面上，選取**建立**按鈕，以建立此服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![LUIS 服務建立的法律注意事項](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="7b2d8-168">一旦您按一下 建立：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="7b2d8-169">插入您想要**名稱**此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="7b2d8-170">選取 **訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="7b2d8-171">選取 **定價層**適合您，如果這是第一個時間來建立*LUIS 服務*，免費層 （名為 F0） 應該是您可以使用。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="7b2d8-172">可用的配置應該是多個足夠這堂課程。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="7b2d8-173">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7b2d8-174">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="7b2d8-175">建議將常見的資源群組下 （例如例如這些課程中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="7b2d8-176">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="7b2d8-177">判斷**位置**資源群組 （如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="7b2d8-178">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="7b2d8-179">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="7b2d8-180">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="7b2d8-181">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-181">Select **Create**.</span></span>

        ![建立 LUIS 服務-使用者輸入](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="7b2d8-183">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="7b2d8-184">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![新的 Azure 通知映像](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="7b2d8-186">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-186">Click on the notification to explore your new Service instance.</span></span>

    ![成功的資源建立通知](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="7b2d8-188">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="7b2d8-189">您會前往新的 LUIS 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![存取 LUIS 金鑰](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="7b2d8-191">在本教學課程中，您的應用程式將需要對您的服務，透過使用您的服務訂用帳戶金鑰進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="7b2d8-192">從*快速入門*頁面上的您*LUIS API*服務，請瀏覽至第一個步驟中，*取得您的金鑰*，然後按一下**金鑰**（您也可以達到此目的按一下藍色超連結索引鍵，位於服務導覽功能表中，以索引鍵的圖示表示）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="7b2d8-193">這將顯示您的服務*金鑰*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="7b2d8-194">需要顯示的索引鍵，其中的複本，因為您將需要此更新版本中您的專案。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="7b2d8-195">在 *服務*頁面上，按一下*Language Understanding 入口網站*重新導向至用來建立新的服務，LUIS 應用程式內的網頁。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="7b2d8-196">第 2 章-Language Understanding 入口網站</span><span class="sxs-lookup"><span data-stu-id="7b2d8-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="7b2d8-197">這一節中，您將了解如何對 LUIS 入口網站中的 LUIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="7b2d8-198">請特別注意，設定*實體*，*意圖*，並*談話*這一章中是第一個步驟中建置您的 LUIS 服務： 您也必須重新訓練服務，許多次，因此要更精確。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="7b2d8-199">重新訓練您的服務說明[最後一章](#chapter-12--improving-your-luis-service)本課程中，因此請確定您已完成它。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="7b2d8-200">達到*Language Understanding 入口網站*，您可能需要登入，如果您還沒有，與您的 Azure 入口網站相同的認證。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS 登入頁面](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="7b2d8-202">如果這是您第一次使用 LUIS，您必須捲動到底部的 歡迎 頁面來尋找並按一下**建立 LUIS 應用程式** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![建立 LUIS 應用程式頁面](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="7b2d8-204">登入之後，按一下**我的應用程式**（如果您目前不是在該區段中）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="7b2d8-205">您可以按一下**建立新的應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-205">You can then click on **Create new app**.</span></span>

    ![LUIS-我的應用程式映像](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="7b2d8-207">提供給您的應用程式*名稱*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="7b2d8-208">如果您的應用程式應該了解不同於英語的語言，您應該變更*文化特性*到適當的語言。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="7b2d8-209">這裡您也可以加入*描述*新 LUIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-建立新的應用程式](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="7b2d8-211">一旦您按下**完成**，將會進入*建置*您新的頁面*LUIS*應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="7b2d8-212">有幾個重要的概念，若要了解以下：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="7b2d8-213">*意圖*，表示將使用者從下列查詢會呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="7b2d8-214">*意圖*可能會有一或多個*實體*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="7b2d8-215">*實體*，是描述的相關資訊之查詢的元件*意圖*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="7b2d8-216">*談話*，前提是由開發人員，該 LUIS 會使用定型本身是查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="7b2d8-217">如果這些概念不完全清除，請不要擔心，如本課程將釐其進一步在這一章中。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="7b2d8-218">您將會開始建立*實體*建置這堂課程所需。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="7b2d8-219">在頁面的左側，按一下*實體*，然後按一下**建立新的實體**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![建立新的實體](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="7b2d8-221">呼叫新的實體*色彩*，將其類型設*簡單*，然後按**完成**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![建立簡單的實體-色彩](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="7b2d8-223">重複此程序來建立三 （3） 多個簡單的實體名稱為：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="7b2d8-224">*upsize*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-224">*upsize*</span></span>
    -   <span data-ttu-id="7b2d8-225">*downsize*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-225">*downsize*</span></span>
    -   <span data-ttu-id="7b2d8-226">*target*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-226">*target*</span></span>

<span data-ttu-id="7b2d8-227">結果看起來應該類似下面的影像：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-227">The result should look like the image below:</span></span>

![建立實體的結果](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="7b2d8-229">此時您可以在其中開始建立*意圖*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="7b2d8-230">請勿刪除**無**意圖。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="7b2d8-231">在頁面的左側，按一下**意圖**，然後按一下**建立新的用途**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![建立新的對應方式](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="7b2d8-233">呼叫新*意圖* **ChangeObjectColor**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7b2d8-234">這*意圖*名稱用在稍後在本課程中的程式碼，因此為了獲得最佳結果，使用此名稱完全依照所提供。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="7b2d8-235">一旦您確認您將會導向至意圖頁面的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS-意圖頁面](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="7b2d8-237">您會注意到沒有文字方塊，要求您為 5 或以上不同的型別*發音*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="7b2d8-238">LUIS 會將所有的表達方式轉換為小寫。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="7b2d8-239">插入下列*Utterance*頂端的文字方塊中 (目前使用的文字*輸入約 5 範例...*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="7b2d8-240">)，然後按**Enter**:</span><span class="sxs-lookup"><span data-stu-id="7b2d8-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="7b2d8-241">您會注意到，新*Utterance*會出現在下方的清單。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="7b2d8-242">遵循相同的程序中，插入下列六 （6） 表達方式：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="7b2d8-243">如您所建立每個 [utterance] 中,，您必須識別為實體 LUIS 應該使用哪一個字。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="7b2d8-244">在此範例中，您需要加上標籤與所有色彩*色彩*實體，並做為目標的所有可能參考*目標*實體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="7b2d8-245">若要這樣做，請嘗試按一下的單字*圓柱*中第一個 [utterance]，然後選取*目標*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![識別 [utterance] 目標](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="7b2d8-247">現在按一下 word*紅色*中第一個 [utterance]，然後選取*色彩*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![識別 [utterance] 實體](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="7b2d8-249">此外，標籤的下一行所在*cube*應該*目標*，和*黑色*應該*色彩*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="7b2d8-250">也請注意使用的單字 *'this'*， *'it'*，並 *'這個物件'*，我們提供，因此也有可用的非特定的目標型別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="7b2d8-251">重複上述程序，直到所有談話都有標示的實體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="7b2d8-252">請參閱下列映像，如果您需要協助。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="7b2d8-253">當選取以實體形式將它們加上標籤的文字：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="7b2d8-254">如需單一字只按一下它們。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-254">For single words just click them.</span></span>
    > - <span data-ttu-id="7b2d8-255">如需兩個或多個字組，按一下的開頭和結尾的集合。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7b2d8-256">您可以使用*語彙基元檢視*切換按鈕，即可切換**實體 / 權杖檢視**！</span><span class="sxs-lookup"><span data-stu-id="7b2d8-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="7b2d8-257">結果應該會顯示下列影像中所示**實體 / 權杖檢視**:</span><span class="sxs-lookup"><span data-stu-id="7b2d8-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![權杖及實體的檢視](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="7b2d8-259">此時按下**定型**在頁面的右上方按鈕，然後等候小圓形指標，它才會變成綠色。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="7b2d8-260">這表示 LUIS 已辨識此意圖成功訓練。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![訓練 LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="7b2d8-262">為您在練習中，建立新的對應方式，稱為**ChangeObjectSize**，使用實體*目標*，*轉換*，以及*縮小*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="7b2d8-263">遵循先前的用途，相同的程序插入下列 （8） 的發音如*大小*變更：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

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

23. <span data-ttu-id="7b2d8-264">結果應該類似下面的影像中：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-264">The result should be like the one in the image below:</span></span>

    ![設定 ChangeObjectSize 語彙基元 / 實體](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="7b2d8-266">一次這兩種對應方式**ChangeObjectColor**並**ChangeObjectSize**，已建立並定型，按一下**發行**網頁頂端的按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![LUIS 服務發行](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="7b2d8-268">在 *發佈*頁面上，您將完成發佈您的 LUIS 應用程式，使它可以存取您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="7b2d8-269">設定卸除*發佈至*作為**生產**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="7b2d8-270">設定*時區*到您的時區。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="7b2d8-271">核取方塊**包含所有預測意圖分數**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="7b2d8-272">按一下 **發行至生產位置**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-272">Click on **Publish to Production Slot**.</span></span>

        ![發行設定](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="7b2d8-274">一節*資源和金鑰*:</span><span class="sxs-lookup"><span data-stu-id="7b2d8-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="7b2d8-275">選取您要為在 Azure 入口網站中的服務執行個體的區域。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="7b2d8-276">您會發現**Starter_Key**項目，會忽略它。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="7b2d8-277">按一下**Add Key** ，並插入*金鑰*您取得在 Azure 入口網站中，當您建立您的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="7b2d8-278">如果您的 Azure 和 LUIS 入口網站登入相同的使用者，您將會提供下拉式清單功能表*租用戶名稱*，*訂用帳戶名稱*，而*金鑰*您想要使用 （為您提供先前在 Azure 入口網站中，會有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="7b2d8-279">下面*端點*，製作的複本對應到索引鍵之端點的已插入，您很快就會使用它在程式碼中。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="7b2d8-280">第 3 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="7b2d8-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="7b2d8-281">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="7b2d8-282">開啟*Unity*然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-282">Open *Unity* and click **New**.</span></span> 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="7b2d8-284">您現在需要提供 Unity 專案名稱、 插入**MR_LUIS**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="7b2d8-285">請確定專案類型設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="7b2d8-286">設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="7b2d8-287">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-287">Then, click **Create project**.</span></span>

    ![提供新的 Unity 專案的詳細資料。](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="7b2d8-289">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="7b2d8-290">移至 編輯 > 喜好設定，然後在新視窗中，瀏覽**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="7b2d8-291">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="7b2d8-292">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-292">Close the **Preferences** window.</span></span>

    ![更新指令碼編輯器喜好設定。](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="7b2d8-294">接下來，移至**檔案 > 組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![建置設定 視窗中，切換至 UWP 的平台。](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="7b2d8-296">移至**檔案 > 組建設定**並確定：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="7b2d8-297">**裝置為目標**設為**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="7b2d8-298">對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="7b2d8-299">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="7b2d8-300">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="7b2d8-301">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="7b2d8-302">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="7b2d8-303">儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="7b2d8-304">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="7b2d8-305">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-305">A save window will appear.</span></span>
        
            ![按一下 新增開啟場景按鈕](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="7b2d8-307">建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的指令碼資料夾](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="7b2d8-309">開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中輸入**MR_LuisScene**，然後按**儲存**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![指定新的場景的名稱。](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="7b2d8-311">剩餘的設定，*組建設定*，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="7b2d8-312">中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟播放程式設定。](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="7b2d8-314">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="7b2d8-315">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="7b2d8-316">**指令碼執行階段版本**應該**穩定**（.NET 3.5 對等）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="7b2d8-317">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="7b2d8-318">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="7b2d8-320">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="7b2d8-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-321">**InternetClient**</span></span>
        2. <span data-ttu-id="7b2d8-322">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-322">**Microphone**</span></span>

            ![正在更新發行的設定。](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="7b2d8-324">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 R 設定。](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="7b2d8-326">回到*Build Settings* _Unity C#_ 專案不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="7b2d8-327">關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="7b2d8-328">儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="7b2d8-329">第 4 章-建立場景</span><span class="sxs-lookup"><span data-stu-id="7b2d8-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b2d8-330">如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，它匯入到您的專案做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 5 章](#chapter-5--create-the-microphonemanager-class)。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="7b2d8-331">中的空白區域上按一下滑鼠右鍵*階層面板*下方**3D 物件**，加入**平面**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![建立平面。](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="7b2d8-333">請注意，當您以滑鼠右鍵按一下*階層*再次建立更多的物件，如果您仍然有選取的最後一個物件，選取的物件會您的新物件的父系。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="7b2d8-334">在階層中的空白空間上按一下滑鼠左鍵，然後以滑鼠右鍵按一下，可以避免此選項。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="7b2d8-335">重複上述程序，將下列物件：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="7b2d8-336">*Sphere*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-336">*Sphere*</span></span>
    2. <span data-ttu-id="7b2d8-337">*Cylinder*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-337">*Cylinder*</span></span>
    3. <span data-ttu-id="7b2d8-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-338">*Cube*</span></span>
    4. <span data-ttu-id="7b2d8-339">*3D 文字*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-339">*3D Text*</span></span>

4.  <span data-ttu-id="7b2d8-340">產生的場景*階層*應該類似下面的影像中：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![場景階層安裝程式。](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="7b2d8-342">上按一下滑鼠左鍵**Main Camera**來選取它，看看*Inspector 面板*您會看到所有相機物件及其元件。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="7b2d8-343">按一下 **新增元件** 按鈕位於最底部*偵測器 面板*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![新增音訊來源](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="7b2d8-345">搜尋呼叫的元件*音效來源*，如上所示。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="7b2d8-346">此外，請確定*轉換*Main Camera 元件設定為 (0,0,0)，這可以藉由按下**齒輪**相機的旁邊的圖示*轉換*元件然後選取**重設**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="7b2d8-347">*轉換*元件再看起來應該像：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="7b2d8-348">*位置*設定為**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="7b2d8-349">*旋轉*設定為**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="7b2d8-350">針對 Microsoft HoloLens，您必須也變更下列項目，兩者皆屬於**相機**元件，這是在您**Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="7b2d8-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="7b2d8-351">**清除旗標：** 不透明色彩。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="7b2d8-352">**背景**' Black、 Alpha 0'-十六進位色彩: #00000000。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="7b2d8-353">上按一下滑鼠左鍵**平面**來選取它。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="7b2d8-354">在 [*偵測器] 面板*設定*轉換*元件使用下列值：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="7b2d8-355">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="7b2d8-356">**X**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-356">**X**</span></span> | <span data-ttu-id="7b2d8-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-357">**Y**</span></span>                  | <span data-ttu-id="7b2d8-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-358">**Z**</span></span> |
    | <span data-ttu-id="7b2d8-359">0</span><span class="sxs-lookup"><span data-stu-id="7b2d8-359">0</span></span>     | <span data-ttu-id="7b2d8-360">-1</span><span class="sxs-lookup"><span data-stu-id="7b2d8-360">-1</span></span>                     | <span data-ttu-id="7b2d8-361">0</span><span class="sxs-lookup"><span data-stu-id="7b2d8-361">0</span></span>     |


10. <span data-ttu-id="7b2d8-362">上按一下滑鼠左鍵**球體**來選取它。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="7b2d8-363">在 [*偵測器] 面板*設定*轉換*元件使用下列值：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="7b2d8-364">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="7b2d8-365">**X**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-365">**X**</span></span> | <span data-ttu-id="7b2d8-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-366">**Y**</span></span>                  | <span data-ttu-id="7b2d8-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-367">**Z**</span></span> |
    | <span data-ttu-id="7b2d8-368">2</span><span class="sxs-lookup"><span data-stu-id="7b2d8-368">2</span></span>     | <span data-ttu-id="7b2d8-369">1</span><span class="sxs-lookup"><span data-stu-id="7b2d8-369">1</span></span>                      | <span data-ttu-id="7b2d8-370">2</span><span class="sxs-lookup"><span data-stu-id="7b2d8-370">2</span></span>     |

11. <span data-ttu-id="7b2d8-371">上按一下滑鼠左鍵**圓柱**來選取它。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="7b2d8-372">在 [*偵測器] 面板*設定*轉換*元件使用下列值：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="7b2d8-373">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="7b2d8-374">**X**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-374">**X**</span></span> | <span data-ttu-id="7b2d8-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-375">**Y**</span></span>                  | <span data-ttu-id="7b2d8-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-376">**Z**</span></span> |
    | <span data-ttu-id="7b2d8-377">-2</span><span class="sxs-lookup"><span data-stu-id="7b2d8-377">-2</span></span>    | <span data-ttu-id="7b2d8-378">1</span><span class="sxs-lookup"><span data-stu-id="7b2d8-378">1</span></span>                      | <span data-ttu-id="7b2d8-379">2</span><span class="sxs-lookup"><span data-stu-id="7b2d8-379">2</span></span>     |

12. <span data-ttu-id="7b2d8-380">上按一下滑鼠左鍵**Cube**來選取它。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="7b2d8-381">在 [*偵測器] 面板*設定*轉換*元件使用下列值：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="7b2d8-382">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="7b2d8-383">轉換-*旋轉*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="7b2d8-384">**X**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-384">**X**</span></span> | <span data-ttu-id="7b2d8-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-385">**Y**</span></span>                   | <span data-ttu-id="7b2d8-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-386">**Z**</span></span> |  \| | <span data-ttu-id="7b2d8-387">**X**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-387">**X**</span></span> | <span data-ttu-id="7b2d8-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-388">**Y**</span></span>                  | <span data-ttu-id="7b2d8-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-389">**Z**</span></span> |
    | <span data-ttu-id="7b2d8-390">0</span><span class="sxs-lookup"><span data-stu-id="7b2d8-390">0</span></span>     | <span data-ttu-id="7b2d8-391">1</span><span class="sxs-lookup"><span data-stu-id="7b2d8-391">1</span></span>                       | <span data-ttu-id="7b2d8-392">4</span><span class="sxs-lookup"><span data-stu-id="7b2d8-392">4</span></span>     |  \| | <span data-ttu-id="7b2d8-393">45</span><span class="sxs-lookup"><span data-stu-id="7b2d8-393">45</span></span>    | <span data-ttu-id="7b2d8-394">45</span><span class="sxs-lookup"><span data-stu-id="7b2d8-394">45</span></span>                     | <span data-ttu-id="7b2d8-395">0</span><span class="sxs-lookup"><span data-stu-id="7b2d8-395">0</span></span>     | 

13. <span data-ttu-id="7b2d8-396">上按一下滑鼠左鍵**新的文字**物件加以選取。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="7b2d8-397">在 [*偵測器] 面板*設定*轉換*元件使用下列值：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="7b2d8-398">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="7b2d8-399">轉換-*小數位數*</span><span class="sxs-lookup"><span data-stu-id="7b2d8-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="7b2d8-400">**X**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-400">**X**</span></span> | <span data-ttu-id="7b2d8-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-401">**Y**</span></span>                  | <span data-ttu-id="7b2d8-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-402">**Z**</span></span> |  \| | <span data-ttu-id="7b2d8-403">**X**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-403">**X**</span></span> | <span data-ttu-id="7b2d8-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-404">**Y**</span></span>               | <span data-ttu-id="7b2d8-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-405">**Z**</span></span> |
    | <span data-ttu-id="7b2d8-406">-2</span><span class="sxs-lookup"><span data-stu-id="7b2d8-406">-2</span></span>    | <span data-ttu-id="7b2d8-407">6</span><span class="sxs-lookup"><span data-stu-id="7b2d8-407">6</span></span>                      | <span data-ttu-id="7b2d8-408">9</span><span class="sxs-lookup"><span data-stu-id="7b2d8-408">9</span></span>     |  \| | <span data-ttu-id="7b2d8-409">0.1</span><span class="sxs-lookup"><span data-stu-id="7b2d8-409">0.1</span></span>   | <span data-ttu-id="7b2d8-410">0.1</span><span class="sxs-lookup"><span data-stu-id="7b2d8-410">0.1</span></span>                 | <span data-ttu-id="7b2d8-411">0.1</span><span class="sxs-lookup"><span data-stu-id="7b2d8-411">0.1</span></span>   | 

14. <span data-ttu-id="7b2d8-412">變更**字型大小**中**文字 Mesh**元件加入**50**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="7b2d8-413">變更*名稱*的**文字 Mesh**物件**聽寫的文字**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![建立 3D 文字物件](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="7b2d8-415">您的階層面板結構現在看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![mesh 場景檢視中的文字](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="7b2d8-417">最終的場景看起來應該類似下面的影像：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-417">The final scene should look like the image below:</span></span>

    ![場景檢視中。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="7b2d8-419">第 5 章-建立 MicrophoneManager 類別</span><span class="sxs-lookup"><span data-stu-id="7b2d8-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="7b2d8-420">您即將建立的第一個指令碼*MicrophoneManager*類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="7b2d8-421">在此之後，您將建立*LuisManager*，則*行為*類別，最後*視線*類別 （可自由雖然將討論當您建立所有這些現在，達到每一章）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="7b2d8-422">*MicrophoneManager*類別負責：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="7b2d8-423">偵測耳機或 （無論是的預設值） 的機器附加的錄音裝置。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="7b2d8-424">擷取音訊 （語音），並將它儲存為字串使用聽寫。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="7b2d8-425">一旦已暫停的語音，提交至聽寫*LuisManager*類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="7b2d8-426">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-426">To create this class:</span></span> 

1.  <span data-ttu-id="7b2d8-427">以滑鼠右鍵按一下*專案 面板*，**建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="7b2d8-428">呼叫資料夾**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-428">Call the folder **Scripts**.</span></span> 

    ![建立指令碼 資料夾。](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="7b2d8-430">具有**指令碼**建立資料夾，按兩下，以開啟該項目。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="7b2d8-431">然後，在該資料夾中，按一下滑鼠右鍵**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="7b2d8-432">指令碼命名*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="7b2d8-433">按兩下*MicrophoneManager*來開啟它*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="7b2d8-434">檔案開頭處新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="7b2d8-435">然後新增下列變數內*MicrophoneManager*類別：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="7b2d8-436">程式碼*Awake()* 並*start （)* 方法現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="7b2d8-437">在類別初始化時，這些將會呼叫：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-437">These will be called when the class initializes:</span></span>

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
 
7.  <span data-ttu-id="7b2d8-438">現在，您需要應用程式用來啟動和停止語音擷取，並將它傳遞至方法*LuisManager*您即將建置的類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

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

8.  <span data-ttu-id="7b2d8-439">新增*聽寫處理常式*，將會叫用語音暫停時。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="7b2d8-440">這個方法會傳遞要聽寫的文字*LuisManager*類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

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
    > <span data-ttu-id="7b2d8-441">刪除*update （)* 方法，因為這個類別不會使用它。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="7b2d8-442">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7b2d8-443">此時您會注意到錯誤不會出現在*Unity 編輯器主控台面板*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="7b2d8-444">這是因為程式碼參考*LuisManager*您會建立下一步 一章中的類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="7b2d8-445">第 6 章-建立 LUISManager 類別</span><span class="sxs-lookup"><span data-stu-id="7b2d8-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="7b2d8-446">它是您建立的時候*LuisManager*類別，可讓 Azure LUIS 服務的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="7b2d8-447">這個類別的目的是要接收的語音輸入文字*MicrophoneManager*類別，並將它傳送給*Azure Language Understanding API*以便進行分析。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="7b2d8-448">這個類別會還原序列化*JSON*回應，並呼叫適當的方法*行為*觸發動作的類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="7b2d8-449">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-449">To create this class:</span></span> 

1.  <span data-ttu-id="7b2d8-450">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="7b2d8-451">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7b2d8-452">指令碼命名*LuisManager*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="7b2d8-453">按兩下要使用 Visual Studio 中開啟它的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="7b2d8-454">檔案開頭處新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="7b2d8-455">您將會開始建立三個類別**內** *LuisManager*類別 (在相同的指令碼檔案中，上述*start （)* 方法)，將會代表已還原序列化從 Azure 的 JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

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

6.  <span data-ttu-id="7b2d8-456">接下來，新增下列變數內*LuisManager*類別：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="7b2d8-457">請務必現在將放在您的 LUIS 端點 （這就會從您的 LUIS 入口網站）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="7b2d8-458">程式碼*Awake()* 方法現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="7b2d8-459">在類別初始化時，將會呼叫這個方法：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="7b2d8-460">現在，您需要的方法，此應用程式用來傳送來自聽寫*MicrophoneManager*類別，即可*LUIS*，然後接收和還原序列化回應。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="7b2d8-461">一旦決定的意圖和相關聯的實體的值，傳遞至執行個體*行為*類別觸發的動作。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

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
 
11. <span data-ttu-id="7b2d8-462">建立新的方法，稱為*AnalyseResponseElements()* ，將讀取產生*AnalysedQuery*並判斷實體。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="7b2d8-463">這些實體會決定之後，會將它們傳遞到的執行個體*行為*動作中使用的類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

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

            // Depending on the topmost recognised intent, read the entities name
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
    > <span data-ttu-id="7b2d8-464">刪除*start （)* 並*update （)* 方法，因為這個類別不會使用它們。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="7b2d8-465">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="7b2d8-466">此時您會注意到數個錯誤，不會出現在*Unity 編輯器主控台面板*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="7b2d8-467">這是因為程式碼參考*行為*您會建立下一步 一章中的類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="7b2d8-468">第 7 章-建立行為類別</span><span class="sxs-lookup"><span data-stu-id="7b2d8-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="7b2d8-469">*行為*類別將會觸發使用所提供之實體的動作*LuisManager*類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="7b2d8-470">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-470">To create this class:</span></span> 

1.  <span data-ttu-id="7b2d8-471">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="7b2d8-472">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7b2d8-473">指令碼命名*行為*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="7b2d8-474">按兩下要開啟它的指令碼*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="7b2d8-475">然後新增下列變數內*行為*類別：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="7b2d8-476">新增*Awake()* 方法程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="7b2d8-477">在類別初始化時，將會呼叫這個方法：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="7b2d8-478">下列方法會呼叫*LuisManager*類別 （您先前建立） 來判斷哪一個物件為目標的查詢，然後再觸發適當的動作。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

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
 
7.  <span data-ttu-id="7b2d8-479">新增*FindTarget()* 方法，以判斷哪些*Gameobject*做為目標的目前的意圖。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="7b2d8-480">這個方法預設目標，以便*GameObject*正在"gazed 」 如果沒有明確的目標定義實體中。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
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
    > <span data-ttu-id="7b2d8-481">刪除*start （)* 並*update （)* 方法，因為這個類別不會使用它們。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="7b2d8-482">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="7b2d8-483">第 8 – 建立視線類別</span><span class="sxs-lookup"><span data-stu-id="7b2d8-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="7b2d8-484">您必須完成此應用程式的最後一個類別是*視線*類別。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="7b2d8-485">這個類別會更新參考*GameObject*目前在使用者的視覺焦點。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="7b2d8-486">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-486">To create this Class:</span></span> 

1.  <span data-ttu-id="7b2d8-487">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="7b2d8-488">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7b2d8-489">指令碼命名*視線*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="7b2d8-490">按兩下要開啟它的指令碼*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="7b2d8-491">插入此類別的下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-491">Insert the following code for this class:</span></span>

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
 
5.  <span data-ttu-id="7b2d8-492">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="7b2d8-493">第 9 章 – 場景設定完成</span><span class="sxs-lookup"><span data-stu-id="7b2d8-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="7b2d8-494">若要完成場景的安裝程式，將您從指令碼 資料夾，以建立每個指令碼**Main Camera**物件中*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="7b2d8-495">選取  **Main Camera**並查看*Inspector 面板*您應該能夠看到您附加，每個指令碼，您會注意到每個指令碼在即將設定的參數。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![設定觀景窗參考目標。](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="7b2d8-497">若要正確地設定這些參數，請遵循下列指示：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="7b2d8-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="7b2d8-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="7b2d8-499">從*階層面板*，拖曳**聽寫的文字**物件插入**聽寫的文字**參數值 方塊中。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="7b2d8-500">*行為*，從*階層面板*:</span><span class="sxs-lookup"><span data-stu-id="7b2d8-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="7b2d8-501">拖曳**球體**物件插入*球體*參考 [目標] 方塊。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="7b2d8-502">拖曳**圓柱**成*圓柱*參考 [目標] 方塊。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="7b2d8-503">拖曳**Cube**成*Cube*參考 [目標] 方塊。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="7b2d8-504">*視線*:</span><span class="sxs-lookup"><span data-stu-id="7b2d8-504">*Gaze*:</span></span>

        - <span data-ttu-id="7b2d8-505">設定*視線最大距離*要**300** （如果它尚未）。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="7b2d8-506">結果看起來應該類似下面的影像：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-506">The result should look like the image below:</span></span>

    ![顯示相機參考目標，現在設定。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="7b2d8-508">第 10 章-測試在 Unity 編輯器中</span><span class="sxs-lookup"><span data-stu-id="7b2d8-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="7b2d8-509">場景安裝程式會正確地實作測試。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="7b2d8-510">請確定：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-510">Ensure that:</span></span>

-   <span data-ttu-id="7b2d8-511">所有指令碼會附加至**Main Camera**物件。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="7b2d8-512">中的所有欄位*Main 攝影機偵測器 面板*皆正確。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="7b2d8-513">按下**播放**按鈕*Unity Editor*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="7b2d8-514">應用程式應該附加的沈浸式耳機內執行。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="7b2d8-515">試用少數的表達方式，例如：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="7b2d8-516">如果您看到錯誤的相關變更預設音訊裝置，Unity 主控台中，場景可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="7b2d8-517">這是因為內建麥克風耳機，讓它們會處理混合的實境入口網站的方式。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="7b2d8-518">如果您看到此錯誤，只是停止場景並重新啟動它，而且項目應該都能當作預期。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="7b2d8-519">第 11 章-建置和側載 UWP 方案</span><span class="sxs-lookup"><span data-stu-id="7b2d8-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="7b2d8-520">一旦確定應用程式正在 Unity 編輯器中，您就準備好要建置和部署。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="7b2d8-521">若要建置：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-521">To Build:</span></span>

1.  <span data-ttu-id="7b2d8-522">按一下儲存目前的場景**檔案 > 儲存**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="7b2d8-523">移至**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="7b2d8-524">勾選方塊稱為**UnityC#專案**（適用於查看和 UWP 專案建立之後，偵錯您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="7b2d8-525">按一下 **加入開啟的場景**，然後按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![建置設定 視窗](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="7b2d8-527">系統會提示您選取您要建置方案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="7b2d8-528">建立*建置*資料夾和該資料夾中建立適當的名稱，您選擇的另一個資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="7b2d8-529">按一下 **選取資料夾**開始在該位置的組建。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="7b2d8-530">![建立組建資料夾](images/AzureLabs-Lab3-44.png)
    ![選取組建資料夾](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="7b2d8-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="7b2d8-531">一次 Unity 已完成的建置 （它可能需要一些時間），它應該會開啟**檔案總管**視窗在您的組建位置。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="7b2d8-532">若要部署在本機電腦上：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="7b2d8-533">在  *Visual Studio*，開啟方案檔中已建立[前一章](#chapter-10--test-in-the-unity-editor)。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="7b2d8-534">在 **的方案平台**，選取**x86**，**本機**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="7b2d8-535">在 **方案組態**選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="7b2d8-536">針對 Microsoft HoloLens，您可能會發現它更輕鬆地將此設為*遠端機器*，如此一來，您不行動網卡到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="7b2d8-537">不過，您必須也執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="7b2d8-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="7b2d8-538">了解**IP 位址**的您 HoloLens，位於*設定 > 網路和網際網路 > Wi-fi > 進階選項*; IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="7b2d8-539">請確定**開發人員模式**是**上**; 在找到*設定 > 更新與安全性 > 適用於開發人員*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![部署應用程式](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="7b2d8-541">移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="7b2d8-542">您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動 ！</span><span class="sxs-lookup"><span data-stu-id="7b2d8-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="7b2d8-543">一旦啟動，應用程式會提示您授權的存取權_麥克風_。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="7b2d8-544">使用*移動控制器*，或*語音輸入*，或有*鍵盤*按**是** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="7b2d8-545">第 12 章-改善您的 LUIS 服務</span><span class="sxs-lookup"><span data-stu-id="7b2d8-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="7b2d8-546">本章是非常重要的是，並可能需要 interated 時數次，因為它可協助改善您的 LUIS 服務的精確度： 確保您已完成這。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-546">This chapter is incredibly important, and may need to be interated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="7b2d8-547">若要改善 LUIS 所提供的了解程度，您需要擷取新的談話，並使用它們來重新訓練您的 LUIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="7b2d8-548">例如，您可能已受過訓練 LUIS，若要了解"Increase"以及 「 轉換 」，但您不希望您的應用程式，也了解 「 放大 」 之類的字？</span><span class="sxs-lookup"><span data-stu-id="7b2d8-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="7b2d8-549">一旦您已使用您的應用程式數次，你說的所有項目會收集 LUIS 和 LUIS 入口網站中使用。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="7b2d8-550">移至入口網站應用程式遵循此[連結](https://www.luis.ai/home)，和登入。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="7b2d8-551">一旦您登入您的 MS 認證，按一下您*應用程式名稱*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="7b2d8-552">按一下 **檢閱端點的發音**頁面左邊的按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![檢閱表達方式](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="7b2d8-554">您會看到一份已由您的混合實境應用程式傳送至 LUIS 的發音。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![清單中的表達方式](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="7b2d8-556">您會發現一些反白顯示*實體*。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="7b2d8-557">停留在反白顯示的每個字，您可以檢閱每個 [utterance]，並判斷哪些實體有尚未正確辨識，實體是錯誤以及哪些實體就會遺失。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="7b2d8-558">在上述範例中，它找不到，「 魚叉式 」 這個字有已反白顯示做為目標，所以必須更正錯誤，由這個字，以滑鼠暫留，然後按一下**移除標籤**。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="7b2d8-559">![檢查談話](images/AzureLabs-Lab3-49.png)
![移除標籤影像](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="7b2d8-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="7b2d8-560">如果您發現完全無誤的談話，您可以刪除它們使用**刪除**螢幕右側的按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![刪除錯誤的表達方式](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="7b2d8-562">或如果您認為 LUIS 已正確解譯 utterance，您可以使用來驗證其了解**新增對齊意圖** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![加入 對齊的意圖](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="7b2d8-564">一旦您在排序所有顯示的談話，請嘗試並重新載入頁面，以查看更多是否可用。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="7b2d8-565">它是重複的次數以改善您的應用程式了解此程序非常重要。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="7b2d8-566">**愉快 ！**</span><span class="sxs-lookup"><span data-stu-id="7b2d8-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="7b2d8-567">您已完成的整合式 LUIS 應用程式</span><span class="sxs-lookup"><span data-stu-id="7b2d8-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="7b2d8-568">恭喜，您所建立的混合的實境應用程式，運用 Azure Language Understanding Intelligence Service，以了解使用者所講的是和處理該資訊。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![實驗室結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="7b2d8-570">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="7b2d8-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7b2d8-571">練習 1</span><span class="sxs-lookup"><span data-stu-id="7b2d8-571">Exercise 1</span></span>

<span data-ttu-id="7b2d8-572">使用此應用程式時可能會注意到，是否您注視 Floor 物件，並要求以變更其色彩，它就會如此。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="7b2d8-573">您可以算出如何停止應用程式時變更 Floor 色彩嗎？</span><span class="sxs-lookup"><span data-stu-id="7b2d8-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="7b2d8-574">練習 2</span><span class="sxs-lookup"><span data-stu-id="7b2d8-574">Exercise 2</span></span>

<span data-ttu-id="7b2d8-575">請嘗試擴充 LUIS 和應用程式的功能，加入場景; 中的物件的其他功能做為範例，請在視線叫用的時間點，根據使用者所說，並且可使用現有的命令旁目前的場景物件，這些物件建立新的物件。</span><span class="sxs-lookup"><span data-stu-id="7b2d8-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
