---
title: MR 和 Azure 302-電腦視覺
description: 完成本課程, 以瞭解如何在混合現實應用程式中使用 Azure 電腦視覺, 以在所提供的影像中辨識視覺內容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合現實, 學術, unity, 教學課程, api, 電腦視覺, hololens, 沉浸, vr
ms.openlocfilehash: 9cc526afdc36b8056afd61948fea5cf98015bb35
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047188"
---
>[!NOTE]
><span data-ttu-id="45d87-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="45d87-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="45d87-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="45d87-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="45d87-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="45d87-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="45d87-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="45d87-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="45d87-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="45d87-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="45d87-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="45d87-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="45d87-110">MR 和 Azure 302:電腦視覺</span><span class="sxs-lookup"><span data-stu-id="45d87-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="45d87-111">在此課程中, 您將瞭解如何使用混合現實應用程式中的 Azure 電腦視覺功能, 辨識所提供影像中的視覺內容。</span><span class="sxs-lookup"><span data-stu-id="45d87-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="45d87-112">辨識結果會顯示為描述性標記。</span><span class="sxs-lookup"><span data-stu-id="45d87-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="45d87-113">您可以使用此服務, 而不需要訓練機器學習服務模型。</span><span class="sxs-lookup"><span data-stu-id="45d87-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="45d87-114">如果您的執行需要訓練機器學習模型, 請參閱[MR 和 Azure 302b](mr-azure-302b.md)。</span><span class="sxs-lookup"><span data-stu-id="45d87-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![實驗室結果](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="45d87-116">Microsoft 電腦視覺是一組 Api, 其設計目的是要為開發人員提供影像處理和分析 (包含傳回信息), 並使用所有雲端的先進演算法。</span><span class="sxs-lookup"><span data-stu-id="45d87-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="45d87-117">開發人員上傳影像或影像 URL, 而 Microsoft 電腦視覺 API 演算法會根據選擇使用者的輸入來分析視覺內容, 然後傳回信息, 包括識別影像的類型和品質、偵測人臉 (傳回其座標)、標記或分類影像。</span><span class="sxs-lookup"><span data-stu-id="45d87-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="45d87-118">如需詳細資訊, 請造訪[Azure 電腦視覺 API 頁面](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。</span><span class="sxs-lookup"><span data-stu-id="45d87-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="45d87-119">完成此課程之後, 您將擁有一個混合現實 HoloLens 應用程式, 其將能夠執行下列作業:</span><span class="sxs-lookup"><span data-stu-id="45d87-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="45d87-120">使用點一下手勢, HoloLens 的攝影機將會捕捉影像。</span><span class="sxs-lookup"><span data-stu-id="45d87-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="45d87-121">映射將會傳送至 Azure 電腦視覺 API 服務。</span><span class="sxs-lookup"><span data-stu-id="45d87-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="45d87-122">辨識的物件將會列在位於 Unity 場景的簡單 UI 群組中。</span><span class="sxs-lookup"><span data-stu-id="45d87-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="45d87-123">在您的應用程式中, 您可以決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="45d87-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="45d87-124">本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。</span><span class="sxs-lookup"><span data-stu-id="45d87-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="45d87-125">您的工作是使用您從這個課程取得的知識, 來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="45d87-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="45d87-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="45d87-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="45d87-127">粗</span><span class="sxs-lookup"><span data-stu-id="45d87-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="45d87-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="45d87-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="45d87-129"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="45d87-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="45d87-130">MR 和 Azure 302:電腦視覺</span><span class="sxs-lookup"><span data-stu-id="45d87-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="45d87-131">✔️</span><span class="sxs-lookup"><span data-stu-id="45d87-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="45d87-132">✔️</span><span class="sxs-lookup"><span data-stu-id="45d87-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="45d87-133">雖然此課程主要著重于 HoloLens, 但您也可以將在本課程中學習到的內容套用至 Windows Mixed Reality 沉浸式 (VR) 耳機。</span><span class="sxs-lookup"><span data-stu-id="45d87-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="45d87-134">因為沉浸式 (VR) 耳機沒有可存取的相機, 所以您需要連接到電腦的外部相機。</span><span class="sxs-lookup"><span data-stu-id="45d87-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="45d87-135">隨著課程的遵循, 您將會看到支援沉浸式 (VR) 耳機時, 您可能需要採取的任何變更的附注。</span><span class="sxs-lookup"><span data-stu-id="45d87-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45d87-136">先決條件</span><span class="sxs-lookup"><span data-stu-id="45d87-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="45d87-137">本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="45d87-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="45d87-138">也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (5 月 2018)。</span><span class="sxs-lookup"><span data-stu-id="45d87-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="45d87-139">您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="45d87-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="45d87-140">在此課程中, 我們建議您採用下列硬體和軟體:</span><span class="sxs-lookup"><span data-stu-id="45d87-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="45d87-141">[與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦, 可用於沉浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="45d87-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="45d87-142">已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="45d87-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="45d87-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="45d87-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="45d87-144">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="45d87-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="45d87-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="45d87-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="45d87-146">已啟用開發人員模式的[Windows Mixed Reality 沉浸 (VR) 耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="45d87-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="45d87-147">連接到您電腦的相機 (適用于沉浸式耳機開發)</span><span class="sxs-lookup"><span data-stu-id="45d87-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="45d87-148">適用于 Azure 設定和電腦視覺 API 抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="45d87-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="45d87-149">開始之前</span><span class="sxs-lookup"><span data-stu-id="45d87-149">Before you start</span></span>

1.  <span data-ttu-id="45d87-150">為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。</span><span class="sxs-lookup"><span data-stu-id="45d87-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="45d87-151">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="45d87-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="45d87-152">如果您需要支援設定 HoloLens,[請務必造訪 hololens 安裝程式一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="45d87-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="45d87-153">開始開發新的 HoloLens 應用程式時, 最好先執行校正和感應器微調 (有時候它有助於為每個使用者執行這些工作)。</span><span class="sxs-lookup"><span data-stu-id="45d87-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="45d87-154">如需校正的說明, 請遵循此[HoloLens 校正文章的連結](calibration.md#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="45d87-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="45d87-155">如需感應器微調的說明, 請遵循此[HoloLens 感應器微調文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="45d87-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="45d87-156">第1章– Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="45d87-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="45d87-157">若要在 Azure 中使用*電腦視覺 API*服務, 您將需要設定服務的實例, 讓應用程式可以使用。</span><span class="sxs-lookup"><span data-stu-id="45d87-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="45d87-158">首先, 登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="45d87-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="45d87-159">如果您還沒有 Azure 帳戶, 您將需要建立一個。</span><span class="sxs-lookup"><span data-stu-id="45d87-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="45d87-160">如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。</span><span class="sxs-lookup"><span data-stu-id="45d87-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="45d87-161">登入之後, 按一下左上角的 [**新增**], 並搜尋*電腦視覺 API*, 然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="45d87-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![在 Azure 中建立新的資源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="45d87-163">在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。</span><span class="sxs-lookup"><span data-stu-id="45d87-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="45d87-164">新的頁面會提供*電腦視覺 API*服務的描述。</span><span class="sxs-lookup"><span data-stu-id="45d87-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="45d87-165">在此頁面的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="45d87-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![關於電腦視覺 api 服務](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="45d87-167">一旦您按下 **建立** :</span><span class="sxs-lookup"><span data-stu-id="45d87-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="45d87-168">為此服務實例插入您想要的**名稱**。</span><span class="sxs-lookup"><span data-stu-id="45d87-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="45d87-169">選取**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="45d87-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="45d87-170">選取適合您的**定價層**, 如果這是您第一次建立*電腦視覺 API*服務, 則應該可供您使用的免費層 (名為 F0)。</span><span class="sxs-lookup"><span data-stu-id="45d87-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="45d87-171">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="45d87-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="45d87-172">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="45d87-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="45d87-173">建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。</span><span class="sxs-lookup"><span data-stu-id="45d87-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="45d87-174">如果您想要深入瞭解 Azure 資源群組, 請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="45d87-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="45d87-175">判斷資源群組的位置 (如果您要建立新的資源群組)。</span><span class="sxs-lookup"><span data-stu-id="45d87-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="45d87-176">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="45d87-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="45d87-177">某些 Azure 資產僅適用于特定區域。</span><span class="sxs-lookup"><span data-stu-id="45d87-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="45d87-178">您也必須確認您已瞭解適用于此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="45d87-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="45d87-179">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="45d87-179">Click Create.</span></span>

        ![服務建立資訊](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="45d87-181">按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="45d87-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="45d87-182">建立服務實例之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="45d87-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![查看新服務的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="45d87-184">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="45d87-184">Click on the notification to explore your new Service instance.</span></span> 

    ![選取 [移至資源] 按鈕。](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="45d87-186">按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="45d87-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="45d87-187">您將會進入新的電腦視覺 API 服務實例。</span><span class="sxs-lookup"><span data-stu-id="45d87-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![您的新電腦視覺 API 服務](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="45d87-189">在本教學課程中, 您的應用程式將需要呼叫您的服務, 這會透過使用您服務的訂用帳戶金鑰來完成。</span><span class="sxs-lookup"><span data-stu-id="45d87-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="45d87-190">從您*電腦視覺 API*服務的 [*快速入門*] 頁面, 流覽至第一個步驟,*抓取您的金鑰*, 然後按一下 [**金鑰**] (您也可以按一下位於 [服務] 導覽功能表中的藍色超連結金鑰來達成此目的,以按鍵圖示表示)。</span><span class="sxs-lookup"><span data-stu-id="45d87-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="45d87-191">這會顯示您的服務*金鑰*。</span><span class="sxs-lookup"><span data-stu-id="45d87-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="45d87-192">複製其中一個顯示的金鑰, 因為您稍後會在專案中用到。</span><span class="sxs-lookup"><span data-stu-id="45d87-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="45d87-193">回到 [*快速入門*] 頁面, 然後從該處提取您的端點。</span><span class="sxs-lookup"><span data-stu-id="45d87-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="45d87-194">請注意, 您的區域可能會不同, 視您的地區而定 (如果是的話, 您稍後將需要變更程式碼)。</span><span class="sxs-lookup"><span data-stu-id="45d87-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="45d87-195">取得此端點的複本以供稍後使用:</span><span class="sxs-lookup"><span data-stu-id="45d87-195">Take a copy of this endpoint for use later:</span></span>

    ![您的新電腦視覺 API 服務](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="45d87-197">您可以在[這裡](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)檢查各種端點。</span><span class="sxs-lookup"><span data-stu-id="45d87-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="45d87-198">第2章–設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="45d87-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="45d87-199">以下是使用混合現實進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="45d87-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="45d87-200">開啟*Unity* , 然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-200">Open *Unity* and click **New**.</span></span> 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="45d87-202">現在您將需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="45d87-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="45d87-203">插入**MR_ComputerVision**。</span><span class="sxs-lookup"><span data-stu-id="45d87-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="45d87-204">請確定 [專案類型] 設定為 [ **3d**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="45d87-205">將位置設定為適合您的**位置**(請記住, 接近根目錄較佳)。</span><span class="sxs-lookup"><span data-stu-id="45d87-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="45d87-206">然後, 按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-206">Then, click **Create project**.</span></span>

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="45d87-208">在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="45d87-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="45d87-209">移至 **編輯 > 喜好**設定, 然後在新視窗中, 流覽至 **外部工具**。</span><span class="sxs-lookup"><span data-stu-id="45d87-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="45d87-210">將**外部腳本編輯器**變更為**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="45d87-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="45d87-211">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="45d87-211">Close the **Preferences** window.</span></span>

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="45d87-213">接下來, 移至 [檔案] **> [組建設定**], 並選取 [**通用 Windows 平臺**], 然後按一下 [**切換平臺**] 按鈕以套用您的選取專案。</span><span class="sxs-lookup"><span data-stu-id="45d87-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![[組建設定] 視窗, 將平臺切換至 UWP。](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="45d87-215">仍在 檔案 **> 組建設定**, 並確認:</span><span class="sxs-lookup"><span data-stu-id="45d87-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="45d87-216">**目標裝置**設定為**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="45d87-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="45d87-217">針對沉浸式耳機, 將 [**目標裝置**] 設定為 [*任何裝置*]。</span><span class="sxs-lookup"><span data-stu-id="45d87-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="45d87-218">**組建類型**設定為**D3D**</span><span class="sxs-lookup"><span data-stu-id="45d87-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="45d87-219">**SDK**已設定為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="45d87-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="45d87-220">**Visual Studio 版本**設定為 [**最新安裝**]</span><span class="sxs-lookup"><span data-stu-id="45d87-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="45d87-221">**組建和執行**設定為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="45d87-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="45d87-222">儲存場景, 並將它加入至組建。</span><span class="sxs-lookup"><span data-stu-id="45d87-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="45d87-223">選取 [新增] [**開啟場景**] 來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="45d87-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="45d87-224">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="45d87-224">A save window will appear.</span></span>
        
            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="45d87-226">為此建立新的資料夾, 並在任何未來的場景中選取 [**新增資料夾**] 按鈕, 以建立新的資料夾, 將其命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="45d87-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的腳本資料夾](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="45d87-228">開啟新建立的 [**幕後**] 資料夾, 然後在 [*檔案名*: 文字] 欄位中, 輸入**MR_ComputerVisionScene**, 然後按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![為新場景指定名稱。](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="45d87-230">請注意, 您必須將 Unity 場景儲存在 [*資產*] 資料夾中, 因為它們必須與 Unity 專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="45d87-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="45d87-231">建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。</span><span class="sxs-lookup"><span data-stu-id="45d87-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="45d87-232">[*組建設定*] 中的其餘設定, 現在應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="45d87-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="45d87-233">在 [*組建設定*] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測*器*所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="45d87-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟 [播放] [設定]。](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="45d87-235">在此面板中, 需要驗證幾項設定:</span><span class="sxs-lookup"><span data-stu-id="45d87-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="45d87-236">在 [**其他設定**] 索引標籤中:</span><span class="sxs-lookup"><span data-stu-id="45d87-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="45d87-237">**腳本執行階段版本**應為**穩定**(.net 3.5 對等)。</span><span class="sxs-lookup"><span data-stu-id="45d87-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="45d87-238">**腳本後端**應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="45d87-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="45d87-239">**API 相容性層級**應該是 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="45d87-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="45d87-241">在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:</span><span class="sxs-lookup"><span data-stu-id="45d87-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="45d87-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="45d87-242">**InternetClient**</span></span>
        2. <span data-ttu-id="45d87-243">**網路**</span><span class="sxs-lookup"><span data-stu-id="45d87-243">**Webcam**</span></span>

            ![正在更新發行設定。](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="45d87-245">在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]。</span><span class="sxs-lookup"><span data-stu-id="45d87-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 設定。](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="45d87-247">回到*組建設定* _Unity C#_ 專案已不再呈現灰色;勾選 [] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="45d87-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="45d87-248">關閉 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="45d87-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="45d87-249">儲存場景和專案 (**file > 儲存場景/檔案 > 儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="45d87-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="45d87-250">第3章–主要攝影機設定</span><span class="sxs-lookup"><span data-stu-id="45d87-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45d87-251">如果您想要略過此課程的*Unity 設定*元件, 並繼續直接進入程式碼, 您可以下載這個[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), 將它匯入到您的專案中做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html), 然後繼續進行[第5章](#chapter-5--create-the-resultslabel-class)。</span><span class="sxs-lookup"><span data-stu-id="45d87-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="45d87-252">在 [階層]*面板*中, 選取**主要相機**。</span><span class="sxs-lookup"><span data-stu-id="45d87-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="45d87-253">選取之後, 您就可以在 [偵測*器] 面板*中看到**主要攝影機**的所有元件。</span><span class="sxs-lookup"><span data-stu-id="45d87-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="45d87-254">**相機物件**必須命名為「**主攝影機**」 (請注意拼寫的!)</span><span class="sxs-lookup"><span data-stu-id="45d87-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="45d87-255">主要相機**標記**必須設定為**MainCamera** (請注意拼寫!)</span><span class="sxs-lookup"><span data-stu-id="45d87-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="45d87-256">請確定**轉換位置**設定為**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="45d87-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="45d87-257">將 [**清除旗標**] 設定為**純色**(針對沉浸式耳機忽略此標記)。</span><span class="sxs-lookup"><span data-stu-id="45d87-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="45d87-258">將相機元件的**背景**色彩設定為**黑色、Alpha 0 (十六進位碼: #00000000)** (針對沉浸式耳機則忽略此項)。</span><span class="sxs-lookup"><span data-stu-id="45d87-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![更新攝影機元件。](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="45d87-260">接下來, 您必須建立連接到**主要攝影機**的簡單「游標」物件, 這可協助您在應用程式執行時放置影像分析輸出。</span><span class="sxs-lookup"><span data-stu-id="45d87-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="45d87-261">此游標會決定相機焦點的中心點。</span><span class="sxs-lookup"><span data-stu-id="45d87-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="45d87-262">若要建立資料指標:</span><span class="sxs-lookup"><span data-stu-id="45d87-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="45d87-263">在 [階層]*面板*中, 以滑鼠右鍵按一下**主要相機**。</span><span class="sxs-lookup"><span data-stu-id="45d87-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="45d87-264">在 [ **3D 物件**] 底下, 按一下 [**球體**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![選取游標物件。](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="45d87-266">將**球體**重新命名為**Cursor** (按兩下游標物件, 或按下 [F2] 鍵盤按鈕, 並選取物件), 並確定它是位於**主攝影機**的子系。</span><span class="sxs-lookup"><span data-stu-id="45d87-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="45d87-267">在 [階層]*面板*中, 以滑鼠左鍵按一下**游標**。</span><span class="sxs-lookup"><span data-stu-id="45d87-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="45d87-268">選取游標之後, 請在 [偵測*器] 面板*中調整下列變數:</span><span class="sxs-lookup"><span data-stu-id="45d87-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="45d87-269">將*轉換位置*設定為**0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="45d87-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="45d87-270">將*縮放比例*設定為**0.02、0.02、0.02**</span><span class="sxs-lookup"><span data-stu-id="45d87-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![更新轉換位置和縮放比例。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="45d87-272">第4章–設定標籤系統</span><span class="sxs-lookup"><span data-stu-id="45d87-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="45d87-273">一旦您使用 HoloLens 的相機來捕捉映射, 該映射就會傳送至您的*Azure 電腦視覺 API*服務實例進行分析。</span><span class="sxs-lookup"><span data-stu-id="45d87-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="45d87-274">該分析的結果會是可識別的物件清單, 稱為**標記**。</span><span class="sxs-lookup"><span data-stu-id="45d87-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="45d87-275">您將使用標籤 (在世界空間中為3D 文字), 在拍攝相片的位置顯示這些標記。</span><span class="sxs-lookup"><span data-stu-id="45d87-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="45d87-276">下列步驟將示範如何設定**標籤**物件。</span><span class="sxs-lookup"><span data-stu-id="45d87-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="45d87-277">以滑鼠右鍵按一下 [階層] 面板中的任何位置 (此處的位置並不重要), 然後在 [ **3D 物件**] 下加入**3d 文字**。</span><span class="sxs-lookup"><span data-stu-id="45d87-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="45d87-278">將它命名為**LabelText**。</span><span class="sxs-lookup"><span data-stu-id="45d87-278">Name it **LabelText**.</span></span>

    ![建立3D 文字物件。](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="45d87-280">在 [階層]*面板*中, 以滑鼠左鍵按一下 [ **LabelText**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="45d87-281">選取**LabelText**之後, 請在 [偵測*器] 面板*中調整下列變數:</span><span class="sxs-lookup"><span data-stu-id="45d87-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="45d87-282">將**位置**設定為**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="45d87-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="45d87-283">將**縮放比例**設定為**0.01、0.01、0.01**</span><span class="sxs-lookup"><span data-stu-id="45d87-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="45d87-284">在元件**文本網格**中:</span><span class="sxs-lookup"><span data-stu-id="45d87-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="45d87-285">將**文字**中的所有文字取代為 "..."</span><span class="sxs-lookup"><span data-stu-id="45d87-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="45d87-286">將**錨點**設定為**中間置**</span><span class="sxs-lookup"><span data-stu-id="45d87-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="45d87-287">將**對齊**設定為 [**置**中]</span><span class="sxs-lookup"><span data-stu-id="45d87-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="45d87-288">將定位**鍵的大小**設定為**4**</span><span class="sxs-lookup"><span data-stu-id="45d87-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="45d87-289">將**字型大小**設定為**50**</span><span class="sxs-lookup"><span data-stu-id="45d87-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="45d87-290">將**色彩**設定為 **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="45d87-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![文字元件](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="45d87-292">將**LabelText**從 [階層]*面板*拖曳至 [*專案] 面板*中的 [資產]*資料夾*。</span><span class="sxs-lookup"><span data-stu-id="45d87-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="45d87-293">這會讓**LabelText**成為 Prefab, 讓它可以在程式碼中具現化。</span><span class="sxs-lookup"><span data-stu-id="45d87-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![建立 LabelText 物件的 prefab。](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="45d87-295">您應該從 [階層]*面板*中刪除**LabelText** , 使其不會顯示在開啟的場景中。</span><span class="sxs-lookup"><span data-stu-id="45d87-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="45d87-296">現在它是一個 prefab, 您會針對資產資料夾中的個別實例呼叫它, 而不需要將它保留在場景中。</span><span class="sxs-lookup"><span data-stu-id="45d87-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="45d87-297">[階層]*面板*中的最終物件結構應如下圖所示:</span><span class="sxs-lookup"><span data-stu-id="45d87-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![階層面板的最終結構。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="45d87-299">第5章–建立 ResultsLabel 類別</span><span class="sxs-lookup"><span data-stu-id="45d87-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="45d87-300">您需要建立的第一個腳本是*ResultsLabel*類別, 其負責下列各項:</span><span class="sxs-lookup"><span data-stu-id="45d87-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="45d87-301">在適當的世界空間中建立標籤 (相對於相機的位置)。</span><span class="sxs-lookup"><span data-stu-id="45d87-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="45d87-302">顯示影像擺脫中的標記。</span><span class="sxs-lookup"><span data-stu-id="45d87-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="45d87-303">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="45d87-303">To create this class:</span></span> 

1.  <span data-ttu-id="45d87-304">在 *專案 面板*中按一下滑鼠右鍵, 然後**建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="45d87-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="45d87-305">將資料夾命名為**Scripts**。</span><span class="sxs-lookup"><span data-stu-id="45d87-305">Name the folder **Scripts**.</span></span> 

    ![建立腳本資料夾。](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="45d87-307">在 [**腳本**] 資料夾建立後, 按兩下以開啟。</span><span class="sxs-lookup"><span data-stu-id="45d87-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="45d87-308">然後在該資料夾中, 以滑鼠右鍵按一下, 然後選取 [**建立] >** [  **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="45d87-309">將腳本命名為*ResultsLabel*。</span><span class="sxs-lookup"><span data-stu-id="45d87-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="45d87-310">按兩下新的*ResultsLabel*腳本, 以**Visual Studio**開啟它。</span><span class="sxs-lookup"><span data-stu-id="45d87-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="45d87-311">在類別內, 于*ResultsLabel*類別中插入下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="45d87-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

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

6.  <span data-ttu-id="45d87-312">請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="45d87-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="45d87-313">回到*Unity 編輯器*中, 按一下 [**腳本**] 資料夾中的 [ *ResultsLabel* ] 類別, 並將其拖曳至 [階層]*面板*中的**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="45d87-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="45d87-314">按一下**主攝影機**並查看 [*檢查] 面板*。</span><span class="sxs-lookup"><span data-stu-id="45d87-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="45d87-315">您會發現, 從剛拖曳至相機的腳本中, 有兩個欄位:資料**指標**和**標籤 Prefab**。</span><span class="sxs-lookup"><span data-stu-id="45d87-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="45d87-316">將名為**cursor**的物件從 [階層]*面板*拖曳到名為**cursor**的位置, 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="45d87-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="45d87-317">從 [*專案] 面板*中的 [*資產] 資料夾*, 將名為**LabelText**的物件拖曳至名為**Label Prefab**的位置, 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="45d87-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![在 Unity 中設定參考目標。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="45d87-319">第6章–建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="45d87-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="45d87-320">下一個您即將建立的類別是*ImageCapture*類別。</span><span class="sxs-lookup"><span data-stu-id="45d87-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="45d87-321">此類別負責:</span><span class="sxs-lookup"><span data-stu-id="45d87-321">This class is responsible for:</span></span>

-   <span data-ttu-id="45d87-322">使用 HoloLens 攝影機來捕獲影像, 並將其儲存在應用程式資料夾中。</span><span class="sxs-lookup"><span data-stu-id="45d87-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="45d87-323">捕捉使用者的點擊手勢。</span><span class="sxs-lookup"><span data-stu-id="45d87-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="45d87-324">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="45d87-324">To create this class:</span></span> 

1.  <span data-ttu-id="45d87-325">移至您先前建立的**腳本**資料夾。</span><span class="sxs-lookup"><span data-stu-id="45d87-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="45d87-326">以滑鼠右鍵按一下資料夾內的 [**建立C# > 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="45d87-327">呼叫腳本*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="45d87-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="45d87-328">按兩下新的*ImageCapture*腳本, 以**Visual Studio**開啟它。</span><span class="sxs-lookup"><span data-stu-id="45d87-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="45d87-329">將下列命名空間新增至檔案頂端:</span><span class="sxs-lookup"><span data-stu-id="45d87-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="45d87-330">然後, 在*ImageCapture*類別內的*Start ()* 方法上方新增下列變數:</span><span class="sxs-lookup"><span data-stu-id="45d87-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="45d87-331">**TapsCount**變數會儲存從使用者所捕獲的點擊點手勢數目。</span><span class="sxs-lookup"><span data-stu-id="45d87-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="45d87-332">這個數位會用於所捕獲的映射命名。</span><span class="sxs-lookup"><span data-stu-id="45d87-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="45d87-333">現在必須加入*喚醒 ()* 和*Start ()* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="45d87-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="45d87-334">當類別初始化時, 將會呼叫這些:</span><span class="sxs-lookup"><span data-stu-id="45d87-334">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="45d87-335">執行會在點碰手勢發生時呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="45d87-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

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
 
<span data-ttu-id="45d87-336">*TapHandler ()* 方法會遞增從使用者中捕捉到的分次次數, 並使用目前的游標位置來決定要在何處放置新的標籤。</span><span class="sxs-lookup"><span data-stu-id="45d87-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="45d87-337">然後, 這個方法會呼叫*ExecuteImageCaptureAndAnalysis ()* 方法來開始此應用程式的核心功能。</span><span class="sxs-lookup"><span data-stu-id="45d87-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="45d87-338">一旦捕獲並儲存映射之後, 就會呼叫下列處理常式。</span><span class="sxs-lookup"><span data-stu-id="45d87-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="45d87-339">如果程式成功, 結果會傳遞至*VisionManager* (您尚未建立) 進行分析。</span><span class="sxs-lookup"><span data-stu-id="45d87-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

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
 
9.  <span data-ttu-id="45d87-340">然後, 新增應用程式用來啟動映射捕獲進程並儲存映射的方法。</span><span class="sxs-lookup"><span data-stu-id="45d87-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

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
> <span data-ttu-id="45d87-341">此時, 您會注意到 [ *Unity 編輯器] 主控台面板*中出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="45d87-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="45d87-342">這是因為程式碼會參考您將在下一章中建立的*VisionManager*類別。</span><span class="sxs-lookup"><span data-stu-id="45d87-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="45d87-343">第7章–呼叫 Azure 和影像分析</span><span class="sxs-lookup"><span data-stu-id="45d87-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="45d87-344">您需要建立的最後一個腳本是*VisionManager*類別。</span><span class="sxs-lookup"><span data-stu-id="45d87-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="45d87-345">此類別負責:</span><span class="sxs-lookup"><span data-stu-id="45d87-345">This class is responsible for:</span></span>

-   <span data-ttu-id="45d87-346">載入以位元組陣列形式捕獲的最新影像。</span><span class="sxs-lookup"><span data-stu-id="45d87-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="45d87-347">將位元組陣列傳送至您的*Azure 電腦視覺 API*服務實例以進行分析。</span><span class="sxs-lookup"><span data-stu-id="45d87-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="45d87-348">以 JSON 字串的形式接收回應。</span><span class="sxs-lookup"><span data-stu-id="45d87-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="45d87-349">還原序列化回應, 並將產生的標記傳遞至*ResultsLabel*類別。</span><span class="sxs-lookup"><span data-stu-id="45d87-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="45d87-350">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="45d87-350">To create this class:</span></span>

1.  <span data-ttu-id="45d87-351">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="45d87-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="45d87-352">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立 > C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="45d87-353">將腳本命名為*VisionManager*。</span><span class="sxs-lookup"><span data-stu-id="45d87-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="45d87-354">按兩下新的腳本, 以 Visual Studio 開啟它。</span><span class="sxs-lookup"><span data-stu-id="45d87-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="45d87-355">在*VisionManager*類別的頂端, 更新命名空間, 以與下列內容相同:</span><span class="sxs-lookup"><span data-stu-id="45d87-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="45d87-356">在腳本頂端的*VisionManager*類別 (在*Start ()* 方法上方) 中, 您現在需要建立兩個*類別*, 以代表來自 Azure 的已還原序列化 JSON 回應:</span><span class="sxs-lookup"><span data-stu-id="45d87-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

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
    > <span data-ttu-id="45d87-357">*TagData*和*AnalysedObject*類別必須在宣告之前加入 *[system.object]* 屬性, 才能使用 Unity 程式庫進行還原序列化。</span><span class="sxs-lookup"><span data-stu-id="45d87-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="45d87-358">在 VisionManager 類別中, 您應該加入下列變數:</span><span class="sxs-lookup"><span data-stu-id="45d87-358">In the VisionManager class, you should add the following variables:</span></span>

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
    > <span data-ttu-id="45d87-359">請務必將您的**驗證金鑰**插入**authorizationKey**變數中。</span><span class="sxs-lookup"><span data-stu-id="45d87-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="45d87-360">您會在本課程[第1章](#chapter-1--the-azure-portal)的一開始就記下**驗證金鑰**。</span><span class="sxs-lookup"><span data-stu-id="45d87-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="45d87-361">**VisionAnalysisEndpoint**變數可能與此範例中指定的變數不同。</span><span class="sxs-lookup"><span data-stu-id="45d87-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="45d87-362">**美國西部**會嚴格地指的是針對美國西部區域所建立的服務實例。</span><span class="sxs-lookup"><span data-stu-id="45d87-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="45d87-363">請使用您的[端點 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)來更新此值;以下是一些可能如下的範例:</span><span class="sxs-lookup"><span data-stu-id="45d87-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="45d87-364">西歐:`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="45d87-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="45d87-365">東南亞:`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="45d87-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="45d87-366">澳大利亞東部:`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="45d87-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="45d87-367">現在必須加入喚醒的程式碼。</span><span class="sxs-lookup"><span data-stu-id="45d87-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="45d87-368">接下來, 新增協同程式 (使用其底下的靜態資料流程方法), 這會取得*ImageCapture*類別所捕獲影像的分析結果。</span><span class="sxs-lookup"><span data-stu-id="45d87-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

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

9.  <span data-ttu-id="45d87-369">請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="45d87-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="45d87-370">回到 Unity 編輯器中, 按一下 [**腳本**] 資料夾中的 [ *VisionManager* ] 和 [ *ImageCapture* ] 類別, 並將其拖曳至 [階層]*面板*中的**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="45d87-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="45d87-371">第8章–大樓</span><span class="sxs-lookup"><span data-stu-id="45d87-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="45d87-372">若要執行應用程式的徹底測試, 您必須將它側載到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="45d87-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="45d87-373">在您執行之前, 請確定:</span><span class="sxs-lookup"><span data-stu-id="45d87-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="45d87-374">[第2章](#chapter-2--set-up-the-unity-project)所述的所有設定都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="45d87-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="45d87-375">所有腳本都會附加到**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="45d87-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="45d87-376">*主要相機偵測器面板*中的所有欄位都已正確指派。</span><span class="sxs-lookup"><span data-stu-id="45d87-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="45d87-377">請務必將您的**驗證金鑰**插入**authorizationKey**變數中。</span><span class="sxs-lookup"><span data-stu-id="45d87-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="45d87-378">請確定您已在*VisionManager*腳本中檢查端點, 並將其對應至*您*的區域 (本檔預設使用「*美國西部*」)。</span><span class="sxs-lookup"><span data-stu-id="45d87-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="45d87-379">第9章–建立 UWP 解決方案並側載應用程式</span><span class="sxs-lookup"><span data-stu-id="45d87-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="45d87-380">此專案的 Unity 區段所需的全部內容現在已經完成, 所以可以從 Unity 建立它。</span><span class="sxs-lookup"><span data-stu-id="45d87-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="45d87-381">流覽至*組建配置* - **檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="45d87-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="45d87-382">從 [*組建設定*] 視窗中, 按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-382">From the *Build Settings* window, click **Build**.</span></span>

    ![從 Unity 建立應用程式](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="45d87-384">如果尚未這麼做, 請先勾選**Unity C#專案**。</span><span class="sxs-lookup"><span data-stu-id="45d87-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="45d87-385">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="45d87-385">Click **Build**.</span></span> <span data-ttu-id="45d87-386">Unity 將會啟動 [檔案*瀏覽器*] 視窗, 您必須在其中建立並選取要建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="45d87-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="45d87-387">立即建立該資料夾, 並將它命名為*應用程式*。</span><span class="sxs-lookup"><span data-stu-id="45d87-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="45d87-388">然後選取 [*應用程式*] 資料夾, 按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="45d87-389">Unity 會開始將您的專案建立至*應用程式*資料夾。</span><span class="sxs-lookup"><span data-stu-id="45d87-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="45d87-390">Unity 完成建立之後 (可能需要一些時間), 它會在組建的位置開啟 [檔案*瀏覽器*] 視窗 (請檢查您的工作列, 因為它不一定會出現在視窗的上方, 但會通知您加入新的視窗)。</span><span class="sxs-lookup"><span data-stu-id="45d87-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="45d87-391">第10章-部署至 HoloLens</span><span class="sxs-lookup"><span data-stu-id="45d87-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="45d87-392">若要在 HoloLens 上部署:</span><span class="sxs-lookup"><span data-stu-id="45d87-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="45d87-393">您將需要 HoloLens 的 IP 位址 (用於遠端部署), 並確保 HoloLens 處於**開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="45d87-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="45d87-394">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="45d87-394">To do this:</span></span>

    1. <span data-ttu-id="45d87-395">在戴 HoloLens 的同時, 請開啟**設定**。</span><span class="sxs-lookup"><span data-stu-id="45d87-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="45d87-396">前往**Network & Internet > wi-fi > Advanced Options**</span><span class="sxs-lookup"><span data-stu-id="45d87-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="45d87-397">記下**IPv4**位址。</span><span class="sxs-lookup"><span data-stu-id="45d87-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="45d87-398">接下來, 流覽回到 [**設定**], 然後為**開發人員更新 & 的安全性 >**</span><span class="sxs-lookup"><span data-stu-id="45d87-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="45d87-399">將開發人員模式設定為 On。</span><span class="sxs-lookup"><span data-stu-id="45d87-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="45d87-400">流覽至新的 Unity 組建 (*應用程式*資料夾), 然後使用*Visual Studio*開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="45d87-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="45d87-401">在 [解決方案設定] 中, 選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="45d87-402">在解決方案平臺中, 選取 [ **x86**]、[**遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="45d87-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![從 Visual Studio 部署解決方案。](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="45d87-404">移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="45d87-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="45d87-405">您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中, 準備好啟動!</span><span class="sxs-lookup"><span data-stu-id="45d87-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="45d87-406">若要部署到沉浸式耳機, 請將**解決方案平臺**設定為 [*本機電腦*], 然後將 [設定] 設為 [ *Debug*], 並將*x86*作為**平臺**。</span><span class="sxs-lookup"><span data-stu-id="45d87-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="45d87-407">然後, 使用 [**建立] 功能表**, 選取 [*部署解決方案*], 部署至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="45d87-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="45d87-408">您完成的電腦視覺 API 應用程式</span><span class="sxs-lookup"><span data-stu-id="45d87-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="45d87-409">恭喜您, 您建立了一個混合現實應用程式, 利用 Azure 電腦視覺 API 來辨識現實世界的物件, 並顯示已看到之內容的信心。</span><span class="sxs-lookup"><span data-stu-id="45d87-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![實驗室結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="45d87-411">額外練習</span><span class="sxs-lookup"><span data-stu-id="45d87-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="45d87-412">練習1</span><span class="sxs-lookup"><span data-stu-id="45d87-412">Exercise 1</span></span>

<span data-ttu-id="45d87-413">就如同您在*VisionManager*中使用的*端點*內所使用的*標記*參數一樣, 請擴充應用程式以偵測其他資訊;請[在此](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)查看您可以存取的其他參數。</span><span class="sxs-lookup"><span data-stu-id="45d87-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="45d87-414">練習2</span><span class="sxs-lookup"><span data-stu-id="45d87-414">Exercise 2</span></span>

<span data-ttu-id="45d87-415">以更具交談和可讀取的方式顯示傳回的 Azure 資料, 可能會隱藏數位。</span><span class="sxs-lookup"><span data-stu-id="45d87-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="45d87-416">如同 bot 可能對使用者說話。</span><span class="sxs-lookup"><span data-stu-id="45d87-416">As though a bot might be speaking to the user.</span></span>
