---
title: MR 和 Azure 302-電腦視覺
description: 完成這個課程來了解如何辨識提供的映像，在混合的實境應用程式中使用 Azure 的 Computer Vision 內的視覺化內容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 電腦視覺、 hololens、 沉浸式 vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591196"
---
>[!NOTE]
><span data-ttu-id="6a4bb-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="6a4bb-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="6a4bb-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="6a4bb-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="6a4bb-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="6a4bb-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="6a4bb-110">MR 和 Azure 302:電腦視覺</span><span class="sxs-lookup"><span data-stu-id="6a4bb-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="6a4bb-111">在此課程中，您將學習如何辨識提供的映像 」 中的視覺內容混合的實境應用程式中使用的 Azure 電腦視覺功能。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="6a4bb-112">辨識結果將顯示為具描述性的標籤。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="6a4bb-113">您可以使用而不需要這項服務，來定型機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="6a4bb-114">如果您的實作需要訓練機器學習模型，請參閱[MR 和 Azure 302b](mr-azure-302b.md)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![實驗室結果](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="6a4bb-116">Microsoft Computer Vision 是一份所有從雲端中使用進階的演算法，用以與映像處理和分析 （附帶傳回的資訊），提供開發人員 Api。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="6a4bb-117">開發人員上傳映像或映像的 URL，以及 Microsoft 電腦視覺 API 演算法會分析視覺化內容中，根據選擇的使用者，則可以傳回資訊，請輸入包括，識別的型別和品質的影像，偵測人臉 （傳回其座標），並加上標籤、 或分類映像。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="6a4bb-118">如需詳細資訊，請瀏覽[Azure Computer Vision API 頁面](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="6a4bb-119">完成本課程之後，您會有混合的實境 HoloLens 應用程式，可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="6a4bb-120">HoloLens 相機會使用點選手勢，來擷取映像。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="6a4bb-121">映像將會傳送至 Azure 的電腦視覺 API 服務中。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="6a4bb-122">簡單的 UI 群組放置在 Unity 場景中會列出可辨識的物件。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="6a4bb-123">在您的應用程式，則您對於如何將整合結果進行設計。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="6a4bb-124">本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="6a4bb-125">它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="6a4bb-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="6a4bb-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="6a4bb-127">課程</span><span class="sxs-lookup"><span data-stu-id="6a4bb-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="6a4bb-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6a4bb-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6a4bb-129"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="6a4bb-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="6a4bb-130">MR 和 Azure 302:電腦視覺</span><span class="sxs-lookup"><span data-stu-id="6a4bb-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="6a4bb-131">✔️</span><span class="sxs-lookup"><span data-stu-id="6a4bb-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6a4bb-132">✔️</span><span class="sxs-lookup"><span data-stu-id="6a4bb-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="6a4bb-133">雖然這堂課程主要著重於 HoloLens，您也可以套用您在此課程 Windows Mixed Reality 沈浸式 (VR) 耳機來了解。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="6a4bb-134">因為沈浸式 (VR) 耳機並沒有可存取的相機，您必須連線到您的 PC 外部相機。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="6a4bb-135">當您遵循本課程中，您會看到 備忘稿上用來支援沈浸式 (VR) 耳機時，您可能需要的任何變更。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6a4bb-136">先決條件</span><span class="sxs-lookup"><span data-stu-id="6a4bb-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="6a4bb-137">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="6a4bb-138">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="6a4bb-139">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊會完全符合您會發現在較新的軟體與以下所列內容.</span><span class="sxs-lookup"><span data-stu-id="6a4bb-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="6a4bb-140">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="6a4bb-141">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="6a4bb-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="6a4bb-142">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="6a4bb-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="6a4bb-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="6a4bb-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="6a4bb-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="6a4bb-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="6a4bb-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="6a4bb-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="6a4bb-146">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="6a4bb-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="6a4bb-147">相機連接到您的電腦 （開發沈浸式耳機）</span><span class="sxs-lookup"><span data-stu-id="6a4bb-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="6a4bb-148">Azure 的安裝程式和電腦視覺 API 擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="6a4bb-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="6a4bb-149">開始之前</span><span class="sxs-lookup"><span data-stu-id="6a4bb-149">Before you start</span></span>

1.  <span data-ttu-id="6a4bb-150">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="6a4bb-151">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="6a4bb-152">如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="6a4bb-153">它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="6a4bb-154">校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="6a4bb-155">如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="6a4bb-156">第 1 章-Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="6a4bb-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="6a4bb-157">若要使用*Computer Vision API*服務在 Azure 中，您必須設定您的應用程式提供服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="6a4bb-158">首先，登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="6a4bb-159">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="6a4bb-160">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="6a4bb-161">一旦您登入，按一下**新增**在左上角，，然後搜尋*Computer Vision API*，然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![在 Azure 中建立新的資源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="6a4bb-163">單字**的新**可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="6a4bb-164">新的頁面將提供的描述*Computer Vision API*服務。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="6a4bb-165">在左下方的這個頁面上，選取**建立**按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![關於電腦視覺 api 服務](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="6a4bb-167">一旦您按下**建立**:</span><span class="sxs-lookup"><span data-stu-id="6a4bb-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="6a4bb-168">插入您想要**名稱**此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="6a4bb-169">選取 **訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="6a4bb-170">選取 **定價層**適合您，如果這是第一個時間來建立*Computer Vision API*服務，免費層 （名為 F0） 應該是您可以使用。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="6a4bb-171">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="6a4bb-172">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="6a4bb-173">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="6a4bb-174">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="6a4bb-175">（如果您要建立新的資源群組），請判斷您的資源群組的位置。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="6a4bb-176">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="6a4bb-177">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="6a4bb-178">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="6a4bb-179">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-179">Click Create.</span></span>

        ![服務建立資訊](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="6a4bb-181">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="6a4bb-182">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![請參閱您的新服務的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="6a4bb-184">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-184">Click on the notification to explore your new Service instance.</span></span> 

    ![選取 [移至資源] 按鈕。](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="6a4bb-186">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="6a4bb-187">您會前往新的 Computer Vision API 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![新的 Computer Vision API 服務](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="6a4bb-189">在本教學課程中，您的應用程式將需要對您的服務，透過使用您的服務訂用帳戶金鑰進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="6a4bb-190">從*快速入門*頁面上的您*Computer Vision API*服務，請瀏覽至第一個步驟中，*取得您的金鑰*，然後按一下**金鑰**(您也可以達到這按一下藍色超連結索引鍵，位於服務導覽功能表中，以索引鍵的圖示表示）。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="6a4bb-191">這將顯示您的服務*金鑰*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="6a4bb-192">需要顯示的索引鍵，其中的複本，因為您將需要此更新版本中您的專案。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="6a4bb-193">請返回*快速入門*頁面，然後從該處擷取您的端點。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="6a4bb-194">您可能會不同，依據您的地區 (這如果是，您必須對您的程式碼進行變更時，也將更新版本)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="6a4bb-195">需要此端點，供後續使用的複本：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-195">Take a copy of this endpoint for use later:</span></span>

    ![新的 Computer Vision API 服務](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="6a4bb-197">您可以檢查不同的端點為何[此處](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="6a4bb-198">第 2 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="6a4bb-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="6a4bb-199">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="6a4bb-200">開啟*Unity*然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-200">Open *Unity* and click **New**.</span></span> 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="6a4bb-202">您現在必須提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="6a4bb-203">插入**MR_ComputerVision**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="6a4bb-204">請確定專案類型設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="6a4bb-205">設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="6a4bb-206">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-206">Then, click **Create project**.</span></span>

    ![提供新的 Unity 專案的詳細資料。](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="6a4bb-208">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="6a4bb-209">移至**編輯 > 偏好**，然後在新視窗中，瀏覽**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="6a4bb-210">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="6a4bb-211">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-211">Close the **Preferences** window.</span></span>

    ![更新指令碼編輯器喜好設定。](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="6a4bb-213">接下來，移至**檔案 > 組建設定**，然後選取**通用 Windows 平台**，然後按一下**切換平台**按鈕以套用您的選擇。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![建置設定 視窗中，切換至 UWP 的平台。](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="6a4bb-215">當您依然在**檔案 > 組建設定**並確定：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="6a4bb-216">**裝置為目標**設為**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="6a4bb-217">針對擬真耳機，設定**目標裝置**要*任何裝置*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="6a4bb-218">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="6a4bb-219">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="6a4bb-220">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="6a4bb-221">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="6a4bb-222">儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="6a4bb-223">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="6a4bb-224">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-224">A save window will appear.</span></span>
        
            ![按一下 新增開啟場景按鈕](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="6a4bb-226">建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的指令碼資料夾](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="6a4bb-228">開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中輸入**MR_ComputerVisionScene**，然後按一下**儲存**.</span><span class="sxs-lookup"><span data-stu-id="6a4bb-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![指定新的場景的名稱。](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="6a4bb-230">請注意，您必須先儲存您的 Unity 場景中*資產*資料夾，因為它們必須是與 Unity 專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="6a4bb-231">建立場景資料夾 （和其他類似的資料夾） 是建構的 Unity 專案的典型方式。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="6a4bb-232">剩餘的設定，*組建設定*，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="6a4bb-233">中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟播放程式設定。](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="6a4bb-235">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="6a4bb-236">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="6a4bb-237">**指令碼執行階段版本**應該**穩定**（.NET 3.5 對等）。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="6a4bb-238">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="6a4bb-239">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="6a4bb-241">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="6a4bb-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-242">**InternetClient**</span></span>
        2. <span data-ttu-id="6a4bb-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-243">**Webcam**</span></span>

            ![正在更新發行的設定。](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="6a4bb-245">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 R 設定。](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="6a4bb-247">回到*Build Settings* _Unity C#_ 專案不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="6a4bb-248">關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="6a4bb-249">儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="6a4bb-250">第 3 章-Main Camera 安裝程式</span><span class="sxs-lookup"><span data-stu-id="6a4bb-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a4bb-251">如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)，它匯入到您的專案做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 5 章](#chapter-5--create-the-resultslabel-class)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="6a4bb-252">在 *階層面板*，選取**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="6a4bb-253">選取之後，您將能夠看到所有的元件**Main Camera**中*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="6a4bb-254">**相機物件**必須命名為**Main Camera** （請注意拼字 ！）</span><span class="sxs-lookup"><span data-stu-id="6a4bb-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="6a4bb-255">Main Camera**標記**必須設為**MainCamera** （請注意拼字 ！）</span><span class="sxs-lookup"><span data-stu-id="6a4bb-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="6a4bb-256">請確定**轉換的位置**設定為**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="6a4bb-257">設定**清除旗標**要**單色**（略過此的沈浸式耳機）。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="6a4bb-258">設定**背景**相機元件以色彩**黑色，0 的 Alpha (十六進位的程式碼: #00000000)** （略過此的沈浸式耳機）。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![更新相機元件。](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="6a4bb-260">接下來，您必須建立簡單的 「 游標 」 物件附加至**Main Camera**，這會協助您放置影像分析輸出應用程式執行時。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="6a4bb-261">這個資料指標將會決定攝影機焦點的中心點。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="6a4bb-262">若要建立資料指標：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="6a4bb-263">在 *階層面板*，以滑鼠右鍵按一下**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="6a4bb-264">底下**3D 物件**，按一下**球體**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![選取游標物件。](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="6a4bb-266">重新命名**球體**要**游標**（按兩下 游標物件或按 'F2' 的 鍵盤 按鈕選取的物件），並確定它位於做為子系**Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="6a4bb-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="6a4bb-267">在 *階層面板*上, 按一下滑鼠左鍵**游標**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="6a4bb-268">選取游標，調整中的下列變數*Inspector 面板*:</span><span class="sxs-lookup"><span data-stu-id="6a4bb-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="6a4bb-269">設定*轉換位置*到**0，0，5**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="6a4bb-270">設定*擴展*到**0.02、 0.02、 0.02**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![更新的轉換位置和小數位數。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="6a4bb-272">第 4 章-設定標籤系統</span><span class="sxs-lookup"><span data-stu-id="6a4bb-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="6a4bb-273">一旦您有與 HoloLens 的攝影機擷取映像，該映像將會傳送至您*Azure Computer Vision API*進行分析的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="6a4bb-274">該分析的結果會是一份可辨識的物件稱為**標記**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="6a4bb-275">您會使用標籤 （世界空間中 3D 文字） 格式來顯示這些標記拍攝相片的位置。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="6a4bb-276">下列步驟將示範如何設定**標籤**物件。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="6a4bb-277">以滑鼠右鍵按一下階層面板的 （位置不會影響在此時） 下的任何地方**3D 物件**，新增**3D 文字**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="6a4bb-278">命名**LabelText**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-278">Name it **LabelText**.</span></span>

    ![建立 3D 文字物件。](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="6a4bb-280">在 *階層面板*，在上按一下滑鼠左鍵**LabelText**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="6a4bb-281">具有**LabelText**選取，調整中的下列變數*Inspector 面板*:</span><span class="sxs-lookup"><span data-stu-id="6a4bb-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="6a4bb-282">設定**位置**到**0,0,0**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="6a4bb-283">設定**擴展**到**0.01、 0.01、 0.01**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="6a4bb-284">在元件**文字 Mesh**:</span><span class="sxs-lookup"><span data-stu-id="6a4bb-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="6a4bb-285">取代內的所有文字**文字**，使用 [...]</span><span class="sxs-lookup"><span data-stu-id="6a4bb-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="6a4bb-286">設定**錨點**到**Na Střed**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="6a4bb-287">設定**對齊**到**Center**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="6a4bb-288">設定**定位點大小**到**4**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="6a4bb-289">設定**字型大小**到**50**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="6a4bb-290">設定**色彩**到 **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![文字元件](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="6a4bb-292">拖曳**LabelText**從*階層面板*，到*Assets 資料夾*內中*專案面板*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="6a4bb-293">這會讓**LabelText** Prefab，因此它可以在程式碼中具現化。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![建立 prefab 的 LabelText 物件。](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="6a4bb-295">您應該刪除**LabelText**從*階層面板*，以便將不會顯示開啟場景中。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="6a4bb-296">它現在成為 prefab，您將呼叫個別的執行個體從 [資產] 資料夾，但沒有需要保留在場景中。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="6a4bb-297">中的最終物件結構*階層面板*應該類似下面的影像中所示：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![在 [階層] 面板的最終結構。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="6a4bb-299">第 5 章-建立 ResultsLabel 類別</span><span class="sxs-lookup"><span data-stu-id="6a4bb-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="6a4bb-300">您必須建立第一個指令碼*ResultsLabel*類別，它會負責下列：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="6a4bb-301">在適當的世界空間中，相對於觀景窗位置建立標籤。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="6a4bb-302">顯示從映像擺脫標記。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="6a4bb-303">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-303">To create this class:</span></span> 

1.  <span data-ttu-id="6a4bb-304">以滑鼠右鍵按一下*專案 面板*，然後**建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="6a4bb-305">將資料夾命名**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-305">Name the folder **Scripts**.</span></span> 

    ![建立指令碼 資料夾。](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="6a4bb-307">具有**指令碼**資料夾建立，連按兩下以開啟該項目。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="6a4bb-308">然後在該資料夾，然後按一下滑鼠右鍵，並選取**建立 >** 再**C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="6a4bb-309">指令碼命名*ResultsLabel*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="6a4bb-310">按兩下新*ResultsLabel*指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="6a4bb-311">類別內插入下列程式碼*ResultsLabel*類別：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="6a4bb-312">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="6a4bb-313">回到*Unity Editor*，按一下並拖曳*ResultsLabel*類別**指令碼**資料夾**Main Camera** 中的物件*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="6a4bb-314">按一下  **Main Camera**並查看*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="6a4bb-315">您會注意到，從指令碼，您剛拖曳到相機，有兩個欄位：**資料指標**並**加上標籤 Prefab**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="6a4bb-316">拖曳所呼叫的物件**游標**從*階層面板*命名的插槽**游標**，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="6a4bb-317">拖曳物件呼叫**LabelText**從*Assets 資料夾*中*專案面板*至名為位置**標籤 Prefab**，如下所示下圖。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![在 Unity 內參考為目標集。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="6a4bb-319">第 6 章-建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="6a4bb-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="6a4bb-320">下一步要建立的類別是*ImageCapture*類別。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="6a4bb-321">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-321">This class is responsible for:</span></span>

-   <span data-ttu-id="6a4bb-322">擷取映像使用 HoloLens 相機，並將其儲存在應用程式資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="6a4bb-323">擷取使用者的點選手勢。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="6a4bb-324">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-324">To create this class:</span></span> 

1.  <span data-ttu-id="6a4bb-325">移至**指令碼**您先前建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="6a4bb-326">在資料夾中，以滑鼠右鍵按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="6a4bb-327">呼叫指令碼*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="6a4bb-328">按兩下新*ImageCapture*指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="6a4bb-329">檔案開頭處新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="6a4bb-330">然後新增下列變數內*ImageCapture*類別，上述*start （)* 方法：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="6a4bb-331">**TapsCount**變數會儲存擷取自使用者的點選手勢的數目。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="6a4bb-332">這個數字是用來擷取的映像命名。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="6a4bb-333">程式碼*Awake()* 並*start （)* 方法現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="6a4bb-334">在類別初始化時，這些將會呼叫：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="6a4bb-335">實作會在點選手勢時呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="6a4bb-336">*TapHandler()* 方法遞增擷取使用者的分接器數目，並且使用目前的資料指標位置，決定在何處放置新的標籤。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="6a4bb-337">這個方法會接著呼叫*ExecuteImageCaptureAndAnalysis()* 方法開始此應用程式的核心功能。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="6a4bb-338">一旦已擷取並儲存映像，就會呼叫下列處理常式。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="6a4bb-339">如果處理程序成功時，結果會傳遞至*VisionManager* （即您尚未建立） 進行分析。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="6a4bb-340">然後新增應用程式用來啟動映像擷取程序，並儲存映像的方法。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="6a4bb-341">此時您會注意到錯誤不會出現在*Unity 編輯器主控台面板*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="6a4bb-342">這是因為程式碼參考*VisionManager*您會建立下一步 一章中的類別。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="6a4bb-343">第 7 章 – 對 Azure 和影像分析</span><span class="sxs-lookup"><span data-stu-id="6a4bb-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="6a4bb-344">您需要建立的最後一個指令碼*VisionManager*類別。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="6a4bb-345">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-345">This class is responsible for:</span></span>

-   <span data-ttu-id="6a4bb-346">正在載入最新的映像擷取成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="6a4bb-347">傳送的位元組陣列，要您*Azure Computer Vision API*進行分析的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="6a4bb-348">接收回應為 JSON 字串。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="6a4bb-349">還原序列化回應，並傳遞將產生的標記*ResultsLabel*類別。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="6a4bb-350">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-350">To create this class:</span></span>

1.  <span data-ttu-id="6a4bb-351">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="6a4bb-352">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="6a4bb-353">指令碼命名*VisionManager*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="6a4bb-354">按兩下新的指令碼，以使用 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="6a4bb-355">更新命名空間相同，如下所示，在頂端*VisionManager*類別：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="6a4bb-356">在您的指令碼頂端*內* *VisionManager*類別 (以上*start （)* 方法)，您現在必須建立兩個*類別*，將代表從 Azure 還原序列化的 JSON 回應：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="6a4bb-357">*TagData*並*AnalysedObject*類別必須能夠 *[System.Serializable]* 能夠還原序列化，使用 Unity 宣告前面加上的屬性程式庫。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="6a4bb-358">在 VisionManager 類別中，您應該加入下列變數：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="6a4bb-359">請確定您插入您**驗證金鑰**成**authorizationKey**變數。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="6a4bb-360">您將已記下您**驗證金鑰**在此課程中，開頭[第 1 章](#chapter-1--the-azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="6a4bb-361">**VisionAnalysisEndpoint**變數可能會在此範例中所指定的不同。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="6a4bb-362">**西-我們**嚴格參考為美國西部區域建立的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="6a4bb-363">更新與您[端點 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); 以下是這方面的一些範例看起來會像：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="6a4bb-364">西歐： `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="6a4bb-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="6a4bb-365">東南亞： `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="6a4bb-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="6a4bb-366">澳洲東部： `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="6a4bb-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="6a4bb-367">Awake 現在需要新增的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="6a4bb-368">接下來，新增 協同程式 （使用靜態的資料流方法下方），它會取得所擷取的映像的分析結果*ImageCapture*類別。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="6a4bb-369">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="6a4bb-370">傳回在 Unity 編輯器中，按一下並拖曳*VisionManager*並*ImageCapture*類別**指令碼**資料夾**Main Camera**物件中*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="6a4bb-371">第 8 章-建置前</span><span class="sxs-lookup"><span data-stu-id="6a4bb-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="6a4bb-372">若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="6a4bb-373">這麼做之前，請確認：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="6a4bb-374">中所述的所有設定[第 2 章](#chapter-2--set-up-the-unity-project)都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="6a4bb-375">所有指令碼會附加至**Main Camera**物件。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="6a4bb-376">中的所有欄位*Main 攝影機偵測器 面板*皆正確。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="6a4bb-377">請確定您插入您**驗證金鑰**成**authorizationKey**變數。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="6a4bb-378">請確定您也必須檢查您的端點您*VisionManager*指令碼，以及它與*您*區域 (此文件會使用*西-我們*預設)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="6a4bb-379">第 9 – 建置的 UWP 方案和側載應用程式</span><span class="sxs-lookup"><span data-stu-id="6a4bb-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="6a4bb-380">此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="6a4bb-381">瀏覽至*組建設定* - **檔案 > 組建設定...**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="6a4bb-382">從*Build Settings*  視窗中，按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-382">From the *Build Settings* window, click **Build**.</span></span>

    ![從 Unity 建置應用程式](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="6a4bb-384">如果您尚未，勾選**UnityC#專案**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="6a4bb-385">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-385">Click **Build**.</span></span> <span data-ttu-id="6a4bb-386">將會啟動 unity*檔案總管*視窗中，您要建立，然後選取 建置到應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="6a4bb-387">現在，建立該資料夾並將它命名*應用程式*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="6a4bb-388">然後使用*應用程式*資料夾選取，請按下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="6a4bb-389">Unity 會開始建置您的專案*應用程式*資料夾。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="6a4bb-390">一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟*檔案總管*視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="6a4bb-391">第 10 – 將部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="6a4bb-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="6a4bb-392">若要部署 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="6a4bb-393">您將需要您 HoloLens IP 位址 （適用於遠端部署），並以確保您 HoloLens 處於**開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="6a4bb-394">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="6a4bb-394">To do this:</span></span>

    1. <span data-ttu-id="6a4bb-395">儘管穿著您 HoloLens，開啟**設定**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="6a4bb-396">移至**網路和網際網路 > Wi-fi > 進階選項**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="6a4bb-397">附註**IPv4**位址。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="6a4bb-398">接下來，瀏覽回到**設定**，然後**更新與安全性 > 適用於開發人員**</span><span class="sxs-lookup"><span data-stu-id="6a4bb-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="6a4bb-399">設定開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="6a4bb-400">瀏覽至新的 Unity 組建 (*應用程式*資料夾)，並開啟方案檔*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="6a4bb-401">在 方案組態選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="6a4bb-402">在 方案平台上，選取**x86**，**遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="6a4bb-404">移至**建置 功能表**，然後按一下**部署方案**，側載您 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="6a4bb-405">您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="6a4bb-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="6a4bb-406">若要將部署到擬真耳機，設定**的方案平台**來*本機電腦*，並設定**組態**至*偵錯*，使用*x86*作為**平台**。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="6a4bb-407">然後部署到本機電腦，使用**建置 功能表**，並選取*部署方案*。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="6a4bb-408">您已完成的 Computer Vision API 應用程式</span><span class="sxs-lookup"><span data-stu-id="6a4bb-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="6a4bb-409">恭喜，您建置利用 Azure 的 Computer Vision API，來辨識真實世界物件，並顯示信心的功能，曾 mixed 的 reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![實驗室結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="6a4bb-411">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="6a4bb-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="6a4bb-412">練習 1</span><span class="sxs-lookup"><span data-stu-id="6a4bb-412">Exercise 1</span></span>

<span data-ttu-id="6a4bb-413">就如同您已使用*標記*參數 (內，證明*端點*用於*VisionManager*)，擴充應用程式，來偵測其他的資訊，看看您可以存取哪些其他參數[此處](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="6a4bb-414">練習 2</span><span class="sxs-lookup"><span data-stu-id="6a4bb-414">Exercise 2</span></span>

<span data-ttu-id="6a4bb-415">顯示傳回 Azure 中的資料，以更白話且容易閱讀的方式，或許隱藏的數字。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="6a4bb-416">如同 bot 可能說給使用者。</span><span class="sxs-lookup"><span data-stu-id="6a4bb-416">As though a bot might be speaking to the user.</span></span>
