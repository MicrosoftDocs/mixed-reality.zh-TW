---
title: MR 和 Azure 302b-自訂視覺
description: 完成此課程來了解如何定型機器學習服務模型，然後使用定型的模型可辨識的混合的實境應用程式中的相似物件。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 自訂視覺、 hololens、 沉浸式 vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591812"
---
>[!NOTE]
><span data-ttu-id="fea5f-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="fea5f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fea5f-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="fea5f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fea5f-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="fea5f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fea5f-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="fea5f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fea5f-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="fea5f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fea5f-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="fea5f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="fea5f-110">MR 和 Azure 302b:自訂辨識</span><span class="sxs-lookup"><span data-stu-id="fea5f-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="fea5f-111">在此課程中，您將學習如何辨識提供的映像 」 中的自訂視覺內容混合的實境應用程式中使用 Azure 自訂視覺功能。</span><span class="sxs-lookup"><span data-stu-id="fea5f-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="fea5f-112">這項服務可讓您定型機器學習模型，使用物件的映像。</span><span class="sxs-lookup"><span data-stu-id="fea5f-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="fea5f-113">然後您會辨識相似的物件，使用定型的模型，由攝影機擷取的 Microsoft HoloLens 或連線到您電腦上的沈浸式 (VR) 耳機相機所提供。</span><span class="sxs-lookup"><span data-stu-id="fea5f-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![課程結果](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="fea5f-115">Azure Custom Vision 是 Microsoft 的認知服務，可讓開發人員建置自訂映像分類器。</span><span class="sxs-lookup"><span data-stu-id="fea5f-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="fea5f-116">這些分類器可以再搭配新的映像辨識，或分類，該新的映像中的物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="fea5f-117">服務提供簡單、 容易使用的線上入口網站簡化程序。</span><span class="sxs-lookup"><span data-stu-id="fea5f-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="fea5f-118">如需詳細資訊，請瀏覽[Azure Custom Vision Service 頁面](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="fea5f-119">完成本課程的詳細資訊，您必須將能夠在兩個模式下運作的混合的實境應用程式：</span><span class="sxs-lookup"><span data-stu-id="fea5f-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="fea5f-120">**分析模式**: Custom Vision Service 手動設定上傳映像、 建立標記，並訓練服務辨識不同的物件 （在此案例的滑鼠和鍵盤）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="fea5f-121">您接著會建立一個 HoloLens 的應用程式，將擷取映像使用相機，並嘗試辨識這些真實世界中的物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="fea5f-122">**定型模式**： 您會實作可讓您的應用程式在 「 定型模式 」 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fea5f-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="fea5f-123">定型模式可讓您擷取映像使用 HoloLens' 相機、 將擷取的映像上傳至服務，以及自訂視覺模型定型。</span><span class="sxs-lookup"><span data-stu-id="fea5f-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="fea5f-124">本課程將教導您如何從 Custom Vision Service 取得結果，到 Unity 為基礎的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="fea5f-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="fea5f-125">它會決定要將這些概念套用到您可能建置自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="fea5f-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="fea5f-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="fea5f-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fea5f-127">課程</span><span class="sxs-lookup"><span data-stu-id="fea5f-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fea5f-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fea5f-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fea5f-129"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="fea5f-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="fea5f-130">MR 和 Azure 302b:自訂辨識</span><span class="sxs-lookup"><span data-stu-id="fea5f-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="fea5f-131">✔️</span><span class="sxs-lookup"><span data-stu-id="fea5f-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="fea5f-132">✔️</span><span class="sxs-lookup"><span data-stu-id="fea5f-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="fea5f-133">雖然這堂課程主要著重於 HoloLens，您也可以套用您在此課程 Windows Mixed Reality 沈浸式 (VR) 耳機來了解。</span><span class="sxs-lookup"><span data-stu-id="fea5f-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="fea5f-134">因為沈浸式 (VR) 耳機並沒有可存取的相機，您必須連線到您的 PC 外部相機。</span><span class="sxs-lookup"><span data-stu-id="fea5f-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="fea5f-135">當您遵循本課程中，您會看到 備忘稿上用來支援沈浸式 (VR) 耳機時，您可能需要的任何變更。</span><span class="sxs-lookup"><span data-stu-id="fea5f-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fea5f-136">先決條件</span><span class="sxs-lookup"><span data-stu-id="fea5f-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="fea5f-137">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="fea5f-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="fea5f-138">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。</span><span class="sxs-lookup"><span data-stu-id="fea5f-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="fea5f-139">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。</span><span class="sxs-lookup"><span data-stu-id="fea5f-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="fea5f-140">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="fea5f-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="fea5f-141">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="fea5f-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="fea5f-142">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="fea5f-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fea5f-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="fea5f-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fea5f-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="fea5f-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fea5f-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fea5f-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="fea5f-146">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="fea5f-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="fea5f-147">相機連接到您的電腦 （開發沈浸式耳機）</span><span class="sxs-lookup"><span data-stu-id="fea5f-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="fea5f-148">Azure 設定及自訂視覺 API 擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="fea5f-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="fea5f-149">至少五 （5） 映像 （十 （10） 建議選項） 的一系列的每個您想要自訂視覺服務，可辨識的物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="fea5f-150">如果您想，您可以使用[這個課程 （電腦滑鼠和鍵盤） 已提供的映像](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="fea5f-151">開始之前</span><span class="sxs-lookup"><span data-stu-id="fea5f-151">Before you start</span></span>

1.  <span data-ttu-id="fea5f-152">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="fea5f-153">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fea5f-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="fea5f-154">如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="fea5f-155">它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。</span><span class="sxs-lookup"><span data-stu-id="fea5f-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="fea5f-156">校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="fea5f-157">如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="fea5f-158">第 1 章-Custom Vision Service 入口網站</span><span class="sxs-lookup"><span data-stu-id="fea5f-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="fea5f-159">若要使用*Custom Vision Service*在 Azure 中，您必須設定您的應用程式提供服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fea5f-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="fea5f-160">首先，[瀏覽至*Custom Vision Service*主頁](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="fea5f-161">按一下 [**開始**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fea5f-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="fea5f-162">登入*Custom Vision Service*入口網站。</span><span class="sxs-lookup"><span data-stu-id="fea5f-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="fea5f-163">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="fea5f-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="fea5f-164">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="fea5f-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="fea5f-165">當您第一次登入時，您將會收到提示*服務條款*面板。</span><span class="sxs-lookup"><span data-stu-id="fea5f-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="fea5f-166">按一下核取方塊以同意條款。</span><span class="sxs-lookup"><span data-stu-id="fea5f-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="fea5f-167">然後按一下**我同意**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="fea5f-168">需要同意的條款，您將瀏覽至*專案*入口網站區段。</span><span class="sxs-lookup"><span data-stu-id="fea5f-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="fea5f-169">按一下 **新的專案**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="fea5f-170">索引標籤會出現在右手邊的畫面會提示您指定的專案部分欄位。</span><span class="sxs-lookup"><span data-stu-id="fea5f-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="fea5f-171">插入*名稱*為您的專案。</span><span class="sxs-lookup"><span data-stu-id="fea5f-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="fea5f-172">插入*描述*為您的專案 (*選擇性*)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="fea5f-173">選擇*資源群組*或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="fea5f-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="fea5f-174">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="fea5f-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fea5f-175">建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="fea5f-176">設定*專案類型*到**分類**</span><span class="sxs-lookup"><span data-stu-id="fea5f-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="fea5f-177">設定*網域*作為**一般**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="fea5f-178">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="fea5f-179">一旦您完成時，按一下**建立專案**，您將會重新導向至 Custom Vision Service，專案頁面。</span><span class="sxs-lookup"><span data-stu-id="fea5f-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="fea5f-180">第 2 章-訓練您的自訂視覺專案</span><span class="sxs-lookup"><span data-stu-id="fea5f-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="fea5f-181">一次在自訂視覺入口網站中，您的主要目標是訓練您的專案，以辨識影像中的特定物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="fea5f-182">您需要至少五 （5） 映像，但十 （10），最好使用，針對每個您想要您的應用程式，可辨識的物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="fea5f-183">[您可以使用本課程 （電腦滑鼠和鍵盤） 提供的映像](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="fea5f-184">若要訓練您的自訂視覺服務專案：</span><span class="sxs-lookup"><span data-stu-id="fea5f-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="fea5f-185">按一下  **+** 按鈕旁**標記。**</span><span class="sxs-lookup"><span data-stu-id="fea5f-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="fea5f-186">新增**名稱**您想要辨識的物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="fea5f-187">按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="fea5f-188">您會注意到您**標記**已加入 （您可能需要重新載入您的頁面才會出現）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="fea5f-189">如果未選取，請按一下與您的新標籤，核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fea5f-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="fea5f-190">按一下 **新增映像**中頁面的中心。</span><span class="sxs-lookup"><span data-stu-id="fea5f-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="fea5f-191">按一下 **瀏覽本機檔案**，並搜尋，然後選取時，您想要使用最小的所上傳的映像五 （5)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="fea5f-192">請記住所有這些映像應該包含您要訓練的物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="fea5f-193">您可以選取數個映像，一次，若要上傳。</span><span class="sxs-lookup"><span data-stu-id="fea5f-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="fea5f-194">一旦您所見的映像 索引標籤中，選取中適當的標籤**My 標記** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="fea5f-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="fea5f-195">按一下 **將檔案上傳**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-195">Click on **Upload files**.</span></span> <span data-ttu-id="fea5f-196">檔案就會開始上傳。</span><span class="sxs-lookup"><span data-stu-id="fea5f-196">The files will begin uploading.</span></span> <span data-ttu-id="fea5f-197">上傳的確認之後，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="fea5f-198">重複相同的程序來建立新**標記**名為**鍵盤**及上傳適當的相片。</span><span class="sxs-lookup"><span data-stu-id="fea5f-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="fea5f-199">請務必 **取消核取** *滑鼠* 當您建立新的標記，因此以顯示 *新增映像* 視窗。</span><span class="sxs-lookup"><span data-stu-id="fea5f-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="fea5f-200">設定兩個標記之後，按一下**定型**，並且在第一個訓練反覆項目會開始建置。</span><span class="sxs-lookup"><span data-stu-id="fea5f-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="fea5f-201">一旦建立，您會看到兩個按鈕稱為**設成預設值**並**預測 URL**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="fea5f-202">按一下 **設成預設值**第一次，然後按一下**預測 URL**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="fea5f-203">從這裡開始，提供的端點 URL 設為者為準*反覆項目*已標示為預設值。</span><span class="sxs-lookup"><span data-stu-id="fea5f-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="fea5f-204">因此，如果您稍後建立新*反覆項目*更新為預設值，您不需要變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="fea5f-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="fea5f-205">一旦您按下*預測 URL*，開啟*記事本*，然後複製並貼上**URL**和**預測金鑰**，如此一來，您可以當您需要稍後在程式碼時，請擷取它。</span><span class="sxs-lookup"><span data-stu-id="fea5f-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="fea5f-206">按一下 **齒輪**頂端螢幕的權限。</span><span class="sxs-lookup"><span data-stu-id="fea5f-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="fea5f-207">複製**訓練的索引鍵**將它貼到*記事本*，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="fea5f-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="fea5f-208">同時複製您**專案識別碼**，也將它貼至您*記事本*檔案，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="fea5f-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="fea5f-209">第 3 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="fea5f-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="fea5f-210">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="fea5f-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="fea5f-211">開啟*Unity*然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="fea5f-212">您現在必須提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="fea5f-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="fea5f-213">插入**AzureCustomVision。**</span><span class="sxs-lookup"><span data-stu-id="fea5f-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="fea5f-214">請確定已設定的專案範本**3D**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="fea5f-215">設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="fea5f-216">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="fea5f-217">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="fea5f-218">移至 **編輯* > *喜好設定** 從新的視窗中，然後瀏覽至 **外部工具** 。</span><span class="sxs-lookup"><span data-stu-id="fea5f-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="fea5f-219">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="fea5f-220">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="fea5f-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="fea5f-221">接下來，移至**檔案 > 組建設定**，然後選取**通用 Windows 平台**，然後按一下**切換平台**按鈕以套用您的選擇。</span><span class="sxs-lookup"><span data-stu-id="fea5f-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="fea5f-222">當您依然在**檔案 > 組建設定**並確定：</span><span class="sxs-lookup"><span data-stu-id="fea5f-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="fea5f-223">**裝置為目標**設為**Hololens**</span><span class="sxs-lookup"><span data-stu-id="fea5f-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="fea5f-224">針對擬真耳機，設定**目標裝置**要*任何裝置*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="fea5f-225">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="fea5f-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="fea5f-226">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="fea5f-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="fea5f-227">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="fea5f-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="fea5f-228">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="fea5f-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="fea5f-229">儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="fea5f-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="fea5f-230">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="fea5f-231">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="fea5f-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="fea5f-232">建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="fea5f-233">開啟您剛建立**場景**資料夾，然後在*檔案名稱：* 文字欄位中輸入**CustomVisionScene**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="fea5f-234">請注意，您必須先儲存您的 Unity 場景中*資產*資料夾，因為它們必須是與 Unity 專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="fea5f-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="fea5f-235">建立場景資料夾 （和其他類似的資料夾） 是建構的 Unity 專案的典型方式。</span><span class="sxs-lookup"><span data-stu-id="fea5f-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="fea5f-236">剩餘的設定，*組建設定*，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="fea5f-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="fea5f-237">中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。</span><span class="sxs-lookup"><span data-stu-id="fea5f-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="fea5f-238">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="fea5f-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="fea5f-239">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="fea5f-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="fea5f-240">**指令碼執行階段版本**應該 **（.NET 4.6 對等） 的實驗性**，這會觸發程序需要重新啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="fea5f-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="fea5f-241">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="fea5f-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="fea5f-242">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="fea5f-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="fea5f-243">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="fea5f-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="fea5f-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="fea5f-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="fea5f-245">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="fea5f-245">**Webcam**</span></span>

        3. <span data-ttu-id="fea5f-246">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="fea5f-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="fea5f-247">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。</span><span class="sxs-lookup"><span data-stu-id="fea5f-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="fea5f-248">回到*Build Settings* *Unity C\#專案*不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fea5f-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="fea5f-249">關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="fea5f-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="fea5f-250">儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="fea5f-251">第 4 章-匯入 unity Newtonsoft DLL</span><span class="sxs-lookup"><span data-stu-id="fea5f-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fea5f-252">如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)，它匯入到您的專案做為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 6 章](#chapter-6---create-the-customvisionanalyser-class)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="fea5f-253">本課程需要使用**Newtonsoft**程式庫，您可以將做為 DLL，加入您的資產。</span><span class="sxs-lookup"><span data-stu-id="fea5f-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="fea5f-254">封裝包含[可以從此連結下載此文件庫](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="fea5f-255">若要 Newtonsoft 程式庫匯入專案中，使用 Unity 套件所附的這堂課程。</span><span class="sxs-lookup"><span data-stu-id="fea5f-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="fea5f-256">新增 *.unitypackage* 若要使用的 Unity **資產* > *匯入* *封裝* > *自訂* *封裝** 功能表選項。</span><span class="sxs-lookup"><span data-stu-id="fea5f-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="fea5f-257">在 **匯入 Unity 封裝**方塊會顯示。 請確認所有項目底下 （而且包括）**外掛程式**已選取。</span><span class="sxs-lookup"><span data-stu-id="fea5f-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="fea5f-258">按一下 **匯入**按鈕以新增至您的專案項目。</span><span class="sxs-lookup"><span data-stu-id="fea5f-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="fea5f-259">移至**Newtonsoft**下方的資料夾**外掛程式**中的專案檢視，然後選取*Newtonsoft.Json 外掛程式*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="fea5f-260">與*Newtonsoft.Json 外掛程式*選取，請確認**任何平台**是**unchecked**，然後確定**WSAPlayer**也**未核取**，然後按一下**套用**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="fea5f-261">這只是要確認已正確設定檔案。</span><span class="sxs-lookup"><span data-stu-id="fea5f-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="fea5f-262">標示這些外掛程式會設定它們僅適用於在 Unity 編輯器中。</span><span class="sxs-lookup"><span data-stu-id="fea5f-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="fea5f-263">有一組不同的專案會匯出從 Unity 後要使用 WSA 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="fea5f-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="fea5f-264">接下來，您必須開啟**WSA**資料夾內**Newtonsoft**資料夾。</span><span class="sxs-lookup"><span data-stu-id="fea5f-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="fea5f-265">您會看到您剛才設定的相同檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="fea5f-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="fea5f-266">選取檔案，並在偵測器中，確定該</span><span class="sxs-lookup"><span data-stu-id="fea5f-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="fea5f-267">**任何平台**是**unchecked**</span><span class="sxs-lookup"><span data-stu-id="fea5f-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="fea5f-268">**只有** **WSAPlayer**是**檢查**</span><span class="sxs-lookup"><span data-stu-id="fea5f-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="fea5f-269">**不會處理**是**檢查**</span><span class="sxs-lookup"><span data-stu-id="fea5f-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="fea5f-270">第 5 章-觀景窗設定</span><span class="sxs-lookup"><span data-stu-id="fea5f-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="fea5f-271">在階層窗格中，選取*Main Camera*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="fea5f-272">選取之後，您將能夠看到所有的元件*Main Camera*中*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="fea5f-273">*相機*必須命名為物件**Main Camera** （請注意拼字 ！）</span><span class="sxs-lookup"><span data-stu-id="fea5f-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="fea5f-274">Main Camera**標記**必須設為**MainCamera** （請注意拼字 ！）</span><span class="sxs-lookup"><span data-stu-id="fea5f-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="fea5f-275">請確定**轉換的位置**設定為**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="fea5f-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="fea5f-276">設定**清除旗標**要**單色**（略過此的沈浸式耳機）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="fea5f-277">設定**背景**觀景窗的色彩元件至**黑色，0 的 Alpha (十六進位的程式碼: #00000000)** （略過此的沈浸式耳機）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="fea5f-278">章節 6-建立 CustomVisionAnalyser 類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="fea5f-279">此時，您已準備好開始撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="fea5f-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="fea5f-280">將開頭*CustomVisionAnalyser*類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="fea5f-281">呼叫**Custom Vision Service**中顯示的程式碼進行以下都會使用**自訂視覺 REST API**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="fea5f-282">透過使用這種情況，您會看到如何實作及使用此 api （適用於了解如何自行實作類似）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="fea5f-283">請注意，Microsoft 提供了**Custom Vision Service SDK** ，也可用來對服務進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="fea5f-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="fea5f-284">如需詳細資訊，請造訪[Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)文章。</span><span class="sxs-lookup"><span data-stu-id="fea5f-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="fea5f-285">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="fea5f-285">This class is responsible for:</span></span>

-   <span data-ttu-id="fea5f-286">正在載入最新的映像擷取成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="fea5f-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="fea5f-287">將位元組陣列傳送至您的 Azure *Custom Vision Service*執行個體進行分析。</span><span class="sxs-lookup"><span data-stu-id="fea5f-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="fea5f-288">接收回應為 JSON 字串。</span><span class="sxs-lookup"><span data-stu-id="fea5f-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="fea5f-289">還原序列化回應，並傳遞產生*預測*要*SceneOrganiser*類別，它會負責顯示回應的方式。</span><span class="sxs-lookup"><span data-stu-id="fea5f-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="fea5f-290">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="fea5f-290">To create this class:</span></span>

1.  <span data-ttu-id="fea5f-291">以滑鼠右鍵按一下*Assets 資料夾*位於 *[專案] 面板*，然後按一下**建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="fea5f-292">呼叫資料夾**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="fea5f-293">按兩下剛才建立開啟的資料夾。</span><span class="sxs-lookup"><span data-stu-id="fea5f-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="fea5f-294">在資料夾中，以滑鼠右鍵按一下，然後按一下  **Create** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fea5f-295">指令碼命名*CustomVisionAnalyser*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="fea5f-296">按兩下新*CustomVisionAnalyser*指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="fea5f-297">更新頂端的 您的檔案，以符合下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="fea5f-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="fea5f-298">在  *CustomVisionAnalyser*類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="fea5f-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="fea5f-299">請確定您插入您**預測金鑰**成**predictionKey**變數和您**預測端點**到**predictionEndpoint**變數。</span><span class="sxs-lookup"><span data-stu-id="fea5f-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="fea5f-300">您可以複製這些*記事本*稍早在本課程。</span><span class="sxs-lookup"><span data-stu-id="fea5f-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="fea5f-301">程式碼**Awake()** 現在必須初始化執行個體變數新增：</span><span class="sxs-lookup"><span data-stu-id="fea5f-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="fea5f-302">刪除方法**start （)** 並**update （)** 。</span><span class="sxs-lookup"><span data-stu-id="fea5f-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="fea5f-303">接下來，新增 協同程式 (具有靜態**GetImageAsByteArray()** 下方的方法)，這將會取得所擷取的映像的分析結果*ImageCapture*類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fea5f-304">在  **AnalyseImageCapture**協同程式，來呼叫*SceneOrganiser*您即將建立的類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="fea5f-305">因此，**保留的線條標記為註解現在**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-305">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="fea5f-306">請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="fea5f-307">第 7-建立 CustomVisionObjects 類別</span><span class="sxs-lookup"><span data-stu-id="fea5f-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="fea5f-308">您將建立的類別現在是*CustomVisionObjects*類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="fea5f-309">此指令碼包含用來序列化和還原序列化的呼叫對其他類別的物件數目*Custom Vision Service*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="fea5f-310">很重要，您需要注意 Custom Vision Service 所提供的是，做為端點的下列 JSON 結構已設定來處理[*自訂辨識預測 v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="fea5f-311">如果您有不同的版本，您可能需要更新下列結構。</span><span class="sxs-lookup"><span data-stu-id="fea5f-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="fea5f-312">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="fea5f-312">To create this class:</span></span>

1.  <span data-ttu-id="fea5f-313">以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fea5f-314">呼叫指令碼*CustomVisionObjects*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="fea5f-315">按兩下新**CustomVisionObjects**指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="fea5f-316">檔案開頭處新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="fea5f-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="fea5f-317">刪除**start （)** 並**update （)** 內的方法*CustomVisionObjects*類別; 此類別現在應為空白。</span><span class="sxs-lookup"><span data-stu-id="fea5f-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="fea5f-318">新增下列類別**外** *CustomVisionObjects*類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="fea5f-319">這些物件由*Newtonsoft*序列化和還原序列化回應資料的程式庫：</span><span class="sxs-lookup"><span data-stu-id="fea5f-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="fea5f-320">第 8-建立 VoiceRecognizer 類別</span><span class="sxs-lookup"><span data-stu-id="fea5f-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="fea5f-321">這個類別會辨識來自使用者的語音輸入。</span><span class="sxs-lookup"><span data-stu-id="fea5f-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="fea5f-322">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="fea5f-322">To create this class:</span></span>

1.  <span data-ttu-id="fea5f-323">以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fea5f-324">呼叫指令碼*VoiceRecognizer*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="fea5f-325">按兩下新**VoiceRecognizer**指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="fea5f-326">新增下列命名空間的上述*VoiceRecognizer*類別：</span><span class="sxs-lookup"><span data-stu-id="fea5f-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="fea5f-327">然後新增下列變數內*VoiceRecognizer*類別，上述*start （)* 方法：</span><span class="sxs-lookup"><span data-stu-id="fea5f-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="fea5f-328">新增**Awake()** 並**start （)** 方法，後者會設定使用者*關鍵字*建立關聯之影像標記時才能辨識：</span><span class="sxs-lookup"><span data-stu-id="fea5f-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="fea5f-329">刪除**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="fea5f-330">新增下列處理常式，每當辨識語音輸入，就會呼叫：</span><span class="sxs-lookup"><span data-stu-id="fea5f-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="fea5f-331">請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="fea5f-332">不要擔心可能會顯示有錯誤，當您將會提供進一步的類別，以修正這些程式碼。</span><span class="sxs-lookup"><span data-stu-id="fea5f-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="fea5f-333">第 9-建立 CustomVisionTrainer 類別</span><span class="sxs-lookup"><span data-stu-id="fea5f-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="fea5f-334">這個類別會鏈結一連串 web 呼叫來定型*Custom Vision Service*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="fea5f-335">每個呼叫將會說明在上面的程式碼的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fea5f-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="fea5f-336">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="fea5f-336">To create this class:</span></span>

1.  <span data-ttu-id="fea5f-337">以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fea5f-338">呼叫指令碼*CustomVisionTrainer*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="fea5f-339">按兩下新*CustomVisionTrainer*指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="fea5f-340">新增下列命名空間的上述*CustomVisionTrainer*類別：</span><span class="sxs-lookup"><span data-stu-id="fea5f-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="fea5f-341">然後新增下列變數內*CustomVisionTrainer*類別，上述**start （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="fea5f-342">此處所使用的訓練 URL 中提供*自訂辨識訓練 1.2*文件，並具有的結構： https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="fea5f-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="fea5f-343">如需詳細資訊，請瀏覽[*自訂辨識訓練 API 的 v1.2 參考*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="fea5f-344">很重要，您需要記下 Custom Vision Service 提供您的訓練模式，以使用 JSON 結構的端點 (內**CustomVisionObjects**類別) 來使用已設定[ *Custom Vision 訓練 v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="fea5f-345">如果您有不同的版本，您可能需要更新*物件*結構。</span><span class="sxs-lookup"><span data-stu-id="fea5f-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="fea5f-346">請務必將您**服務金鑰**（訓練） 索引鍵值並**專案識別碼**值，其中您記下先前; 這些都是值您[收集從先前的課程 （入口網站第 2 章步驟 10 及更新版本）](#chapter-2---training-your-custom-vision-oroject)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="fea5f-347">新增下列**start （)** 並**Awake()** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="fea5f-348">這些方法上初始化呼叫，並包含呼叫，以設定 UI:</span><span class="sxs-lookup"><span data-stu-id="fea5f-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="fea5f-349">刪除**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-349">Delete the **Update()** method.</span></span> <span data-ttu-id="fea5f-350">這個類別就不需要它。</span><span class="sxs-lookup"><span data-stu-id="fea5f-350">This class will not need it.</span></span>

7.  <span data-ttu-id="fea5f-351">新增**RequestTagSelection()** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="fea5f-352">這個方法是已擷取並儲存在裝置影像時要呼叫的第一個，且現在已提交給*Custom Vision Service*、 將它定型。</span><span class="sxs-lookup"><span data-stu-id="fea5f-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="fea5f-353">這個方法會顯示，在 UI 中，一組使用者可以用來標記映像已擷取之關鍵字的訓練。</span><span class="sxs-lookup"><span data-stu-id="fea5f-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="fea5f-354">它也會提醒*VoiceRecognizer*類別，以開始接聽使用者的語音輸入。</span><span class="sxs-lookup"><span data-stu-id="fea5f-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="fea5f-355">新增**VerifyTag()** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="fea5f-356">這個方法會接收語音輸入辨識**VoiceRecognizer**類別並驗證其有效性，然後開始在定型程序。</span><span class="sxs-lookup"><span data-stu-id="fea5f-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="fea5f-357">新增**SubmitImageForTraining()** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="fea5f-358">此方法會開始 Custom Vision Service 定型程序。</span><span class="sxs-lookup"><span data-stu-id="fea5f-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="fea5f-359">第一個步驟是擷取**標記識別項**從使用者的已驗證的語音輸入相關聯的服務。</span><span class="sxs-lookup"><span data-stu-id="fea5f-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="fea5f-360">**標記識別項**會接著映像一起上傳。</span><span class="sxs-lookup"><span data-stu-id="fea5f-360">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="fea5f-361">新增**TrainCustomVisionProject()** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="fea5f-362">一旦已提交並標記映像，就會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="fea5f-363">它會建立新的反覆項目將定型與提交給服務，再加上的映像的所有先前映像剛才上傳。</span><span class="sxs-lookup"><span data-stu-id="fea5f-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="fea5f-364">完成訓練之後，這個方法會呼叫方法來設定新建立**反覆項目**作為**預設**，如此一來，您要用於分析的端點是最新定型的反覆項目。</span><span class="sxs-lookup"><span data-stu-id="fea5f-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="fea5f-365">新增**SetDefaultIteration()** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="fea5f-366">這個方法會設定為先前建立及定型反覆項目*預設*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="fea5f-367">完成時，這個方法就必須刪除現有的服務中的上一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="fea5f-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="fea5f-368">撰寫本課程的同時，沒有限制的最大十 （10） 反覆項目允許在服務中同時存在。</span><span class="sxs-lookup"><span data-stu-id="fea5f-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="fea5f-369">新增**DeletePreviousIteration()** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="fea5f-370">這個方法會尋找並刪除先前的非預設反覆項目：</span><span class="sxs-lookup"><span data-stu-id="fea5f-370">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="fea5f-371">要加入這個類別中的最後一個方法是**GetImageAsByteArray()** 方法，用於 web 呼叫，以轉換成位元組陣列所擷取的影像。</span><span class="sxs-lookup"><span data-stu-id="fea5f-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="fea5f-372">請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="fea5f-373">第 10-建立 SceneOrganiser 類別</span><span class="sxs-lookup"><span data-stu-id="fea5f-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="fea5f-374">這個類別將會：</span><span class="sxs-lookup"><span data-stu-id="fea5f-374">This class will:</span></span>

-   <span data-ttu-id="fea5f-375">建立**游標**来附加至 Main Camera 物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="fea5f-376">建立**標籤**服務能辨識的真實世界物件時，會出現的物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="fea5f-377">設定 Main Camera cvcollectioncmd 附加至適當的元件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="fea5f-378">即使處於**分析模式**、 繁衍 （spawn） 在執行階段，相對於位置的 Main Camera 中，適當的世界空間中的標籤，並顯示 Custom Vision Service 從收到的資料。</span><span class="sxs-lookup"><span data-stu-id="fea5f-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="fea5f-379">即使處於**定型模式**，繁衍 （spawn) 將會顯示在定型程序的不同階段的 UI。</span><span class="sxs-lookup"><span data-stu-id="fea5f-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="fea5f-380">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="fea5f-380">To create this class:</span></span>

1.  <span data-ttu-id="fea5f-381">以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="fea5f-382">指令碼命名*SceneOrganiser*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="fea5f-383">按兩下新*SceneOrganiser*指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="fea5f-384">您只需要一個命名空間，移除上述的其他*SceneOrganiser*類別：</span><span class="sxs-lookup"><span data-stu-id="fea5f-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="fea5f-385">然後新增下列變數內*SceneOrganiser*類別，上述**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="fea5f-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="fea5f-386">刪除**start （)** 並**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="fea5f-387">權限底下的變數中，加入**Awake()** 方法，它會初始化類別，並設定場景。</span><span class="sxs-lookup"><span data-stu-id="fea5f-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="fea5f-388">現在加入**CreateCameraCursor()** 方法來建立，並將 Main Camera 資料指標，而**CreateLabel()** 方法會建立**分析標籤**物件.</span><span class="sxs-lookup"><span data-stu-id="fea5f-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="fea5f-389">新增**SetCameraStatus()** 方法，它會處理要傳送給文字網狀結構提供觀景窗的狀態。</span><span class="sxs-lookup"><span data-stu-id="fea5f-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="fea5f-390">新增**PlaceAnalysisLabel()** 並**SetTagsToLastLabel()** 方法，它會繁衍 （spawn），顯示場景的 Custom Vision Service 中的資料。</span><span class="sxs-lookup"><span data-stu-id="fea5f-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="fea5f-391">最後，新增**CreateTrainingUI()** 方法，它會繁衍 （spawn） 的應用程式是在定型模式時，顯示定型程序的多個階段的 UI。</span><span class="sxs-lookup"><span data-stu-id="fea5f-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="fea5f-392">這個方法也將已經建立相機狀態物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-392">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="fea5f-393">請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fea5f-394">在繼續之前，開啟**CustomVisionAnalyser**類別，會在**AnalyseLastImageCaptured()** 方法*取消註解*下列幾行：</span><span class="sxs-lookup"><span data-stu-id="fea5f-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="fea5f-395">第 11-建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="fea5f-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="fea5f-396">下一步要建立的類別是*ImageCapture*類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="fea5f-397">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="fea5f-397">This class is responsible for:</span></span>

-   <span data-ttu-id="fea5f-398">擷取映像使用 HoloLens 相機，並將它儲存在*應用程式*資料夾。</span><span class="sxs-lookup"><span data-stu-id="fea5f-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="fea5f-399">處理來自使用者的點選手勢。</span><span class="sxs-lookup"><span data-stu-id="fea5f-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="fea5f-400">維護*Enum*值，決定是否有應用程式會以*Analysis*模式或*訓練*模式。</span><span class="sxs-lookup"><span data-stu-id="fea5f-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="fea5f-401">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="fea5f-401">To create this class:</span></span>

1.  <span data-ttu-id="fea5f-402">移至**指令碼**您先前建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="fea5f-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="fea5f-403">在資料夾中，以滑鼠右鍵按一下，然後按一下 **建立 > C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="fea5f-404">指令碼命名*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="fea5f-405">按兩下新**ImageCapture**指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="fea5f-406">以下列內容取代頂端的 檔案命名空間：</span><span class="sxs-lookup"><span data-stu-id="fea5f-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="fea5f-407">然後新增下列變數內*ImageCapture*類別，上述**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="fea5f-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="fea5f-408">程式碼**Awake()** 並**start （)** 方法現在需要新增：</span><span class="sxs-lookup"><span data-stu-id="fea5f-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="fea5f-409">實作會在點選手勢時呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="fea5f-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="fea5f-410">在  *Analysis*模式中， **TapHandler**方法會作為交換器，來啟動或停止相片擷取迴圈。</span><span class="sxs-lookup"><span data-stu-id="fea5f-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="fea5f-411">在 *訓練*模式中，它將來自相機的映像的擷取。</span><span class="sxs-lookup"><span data-stu-id="fea5f-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="fea5f-412">當資料指標為綠色時，表示相機可採取的映像。</span><span class="sxs-lookup"><span data-stu-id="fea5f-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="fea5f-413">當資料指標為紅色時，表示相機正在忙碌中。</span><span class="sxs-lookup"><span data-stu-id="fea5f-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="fea5f-414">新增應用程式用來啟動映像擷取程序，並儲存映像的方法。</span><span class="sxs-lookup"><span data-stu-id="fea5f-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="fea5f-415">新增處理常式會被呼叫時已擷取相片並時準備好進行分析。</span><span class="sxs-lookup"><span data-stu-id="fea5f-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="fea5f-416">結果會傳遞至*CustomVisionAnalyser*或*CustomVisionTrainer*根據哪一個模式上設定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fea5f-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="fea5f-417">請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="fea5f-418">現在，所有指令碼完成時，請回到在 Unity 編輯器中，然後按一下並拖曳**SceneOrganiser**從類別**指令碼**資料夾**Main Camera**物件中*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="fea5f-419">第 12 章-建置前</span><span class="sxs-lookup"><span data-stu-id="fea5f-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="fea5f-420">若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fea5f-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="fea5f-421">這麼做之前，請確認：</span><span class="sxs-lookup"><span data-stu-id="fea5f-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="fea5f-422">中所述的所有設定[第 2 章](#chapter-2---training-your-custom-vision-project)都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="fea5f-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="fea5f-423">中的所有欄位**Main Camera**，偵測器 面板中，適當地指派。</span><span class="sxs-lookup"><span data-stu-id="fea5f-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="fea5f-424">指令碼**SceneOrganiser**附加至**Main Camera**物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="fea5f-425">請確定您插入您**預測金鑰**成**predictionKey**變數。</span><span class="sxs-lookup"><span data-stu-id="fea5f-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="fea5f-426">您已插入您**預測端點**成**predictionEndpoint**變數。</span><span class="sxs-lookup"><span data-stu-id="fea5f-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="fea5f-427">您已插入您**訓練的索引鍵**成**trainingKey**的變數*CustomVisionTrainer*類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="fea5f-428">您已插入您**專案識別碼**成**projectId**的變數*CustomVisionTrainer*類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="fea5f-429">第 13 章-建置和側載您的應用程式</span><span class="sxs-lookup"><span data-stu-id="fea5f-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="fea5f-430">若要開始*建置*程序：</span><span class="sxs-lookup"><span data-stu-id="fea5f-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="fea5f-431">移至**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="fea5f-432">刻度**Unity C\#專案**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="fea5f-433">按一下 [建置]  。</span><span class="sxs-lookup"><span data-stu-id="fea5f-433">Click **Build**.</span></span> <span data-ttu-id="fea5f-434">將會啟動 unity**檔案總管**視窗中，您要建立，然後選取 建置到應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="fea5f-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="fea5f-435">現在，建立該資料夾並將它命名**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="fea5f-436">然後使用**應用程式**上按一下 選取資料夾**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="fea5f-437">Unity 會開始建置您的專案**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="fea5f-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="fea5f-438">一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="fea5f-439">若要部署 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="fea5f-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="fea5f-440">您將需要您 HoloLens IP 位址 （適用於遠端部署），並以確保您 HoloLens 處於**開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="fea5f-441">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="fea5f-441">To do this:</span></span>

    1.  <span data-ttu-id="fea5f-442">儘管穿著您 HoloLens，開啟**設定**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="fea5f-443">移至**網路和網際網路** > **Wi-fi** > **進階選項**</span><span class="sxs-lookup"><span data-stu-id="fea5f-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="fea5f-444">附註**IPv4**位址。</span><span class="sxs-lookup"><span data-stu-id="fea5f-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="fea5f-445">接下來，瀏覽回到**設定**，然後**更新與安全性** > **適用於開發人員**</span><span class="sxs-lookup"><span data-stu-id="fea5f-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="fea5f-446">設定**上的開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="fea5f-447">瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="fea5f-448">在 *方案組態*選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="fea5f-449">在 *的方案平台*，選取**x86，遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="fea5f-450">系統會提示您插入**IP 位址**的遠端裝置 (HoloLens，在此情況下，記下)。</span><span class="sxs-lookup"><span data-stu-id="fea5f-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="fea5f-451">移至**建置**功能表，然後按一下 **部署方案**側載您 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fea5f-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="fea5f-452">您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="fea5f-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="fea5f-453">若要將部署到擬真耳機，設定**的方案平台**來*本機電腦*，並設定**組態**至*偵錯*，使用*x86*作為**平台**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="fea5f-454">然後部署到本機電腦，使用**建置**功能表項目，選取*部署方案*。</span><span class="sxs-lookup"><span data-stu-id="fea5f-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="fea5f-455">若要使用應用程式：</span><span class="sxs-lookup"><span data-stu-id="fea5f-455">To use the application:</span></span>

<span data-ttu-id="fea5f-456">若要切換之間的應用程式功能*訓練*模式並*預測*模式，您需要更新**AppMode**變數，位於**Awake()** 方法將會位於*ImageCapture*類別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="fea5f-457">或</span><span class="sxs-lookup"><span data-stu-id="fea5f-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="fea5f-458">在 *訓練*模式︰</span><span class="sxs-lookup"><span data-stu-id="fea5f-458">In *Training* mode:</span></span>

- <span data-ttu-id="fea5f-459">看看**滑鼠**或是**鍵盤**並用**點選手勢**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="fea5f-460">接下來，文字會出現要求您提供的標記。</span><span class="sxs-lookup"><span data-stu-id="fea5f-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="fea5f-461">顯示**滑鼠**或是**鍵盤**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="fea5f-462">在 *預測*模式︰</span><span class="sxs-lookup"><span data-stu-id="fea5f-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="fea5f-463">查看物件，並使用**點選手勢**。</span><span class="sxs-lookup"><span data-stu-id="fea5f-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="fea5f-464">文字會出現提供具有最高的機率 （這標準化） 偵測到的物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="fea5f-465">第 14-評估，並改善您的自訂視覺模型</span><span class="sxs-lookup"><span data-stu-id="fea5f-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="fea5f-466">若要讓您的服務更精確，您必須繼續用於預測模型定型。</span><span class="sxs-lookup"><span data-stu-id="fea5f-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="fea5f-467">這透過使用新的應用程式同時使用達成*訓練*並*預測*模式，後者需要您造訪入口網站中，也就是在這一章中涵蓋的項目。</span><span class="sxs-lookup"><span data-stu-id="fea5f-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="fea5f-468">要準備多次重新瀏覽您的入口網站，以持續改善您的模型。</span><span class="sxs-lookup"><span data-stu-id="fea5f-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="fea5f-469">同樣地，前往您的 Azure 自訂視覺入口網站，然後當您在專案中，選取*預測*（從頂端中央的頁面） 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="fea5f-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="fea5f-470">您會看到您的應用程式正在執行的同時傳送到您的服務的所有映像。</span><span class="sxs-lookup"><span data-stu-id="fea5f-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="fea5f-471">如果您停留映像時，它們會將您提供該映像所做的預測：</span><span class="sxs-lookup"><span data-stu-id="fea5f-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="fea5f-472">選取您的映像，以開啟它的其中一個。</span><span class="sxs-lookup"><span data-stu-id="fea5f-472">Select one of your images to open it.</span></span> <span data-ttu-id="fea5f-473">一旦開啟，您會看到右邊，該映像所做的預測。</span><span class="sxs-lookup"><span data-stu-id="fea5f-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="fea5f-474">如果您預測正確的而您想要將此映像新增至您的服務定型模型，請按一下*My 標記*輸入方塊，然後選取您想要建立關聯的標記。</span><span class="sxs-lookup"><span data-stu-id="fea5f-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="fea5f-475">當您完成時，請按一下*儲存並關閉*按鈕右下方，並繼續執行下一個映像。</span><span class="sxs-lookup"><span data-stu-id="fea5f-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="fea5f-476">一旦您回到映像的方格中，您會注意到您已新增標記 （並儲存），映像將會移除。</span><span class="sxs-lookup"><span data-stu-id="fea5f-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="fea5f-477">如果您發現您認為不需要您標記的項目，其中任何映像，您可以刪除它們，按一下該映像 （可以執行這項操作的數個映像） 上的刻度，然後按一下*刪除*方格頁面右上角。</span><span class="sxs-lookup"><span data-stu-id="fea5f-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="fea5f-478">接下來，快顯功能表，您可以按一下其中一個*Yes，delete*或*No*，以確認刪除，或取消，分別。</span><span class="sxs-lookup"><span data-stu-id="fea5f-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="fea5f-479">當您準備好繼續進行，請按一下綠色*定型*右上角的按鈕。</span><span class="sxs-lookup"><span data-stu-id="fea5f-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="fea5f-480">這些映像您現在有提供 （這就變得更精確），都會加以定型您的服務模型。</span><span class="sxs-lookup"><span data-stu-id="fea5f-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="fea5f-481">訓練完成之後，請務必按一下 *設成預設值*同樣地，按鈕，讓您*預測 URL*會繼續使用服務的最新的反覆項目。</span><span class="sxs-lookup"><span data-stu-id="fea5f-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="fea5f-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="fea5f-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="fea5f-483">您已完成的自訂視覺 API 應用程式</span><span class="sxs-lookup"><span data-stu-id="fea5f-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="fea5f-484">恭喜，您建置利用 Azure 自訂視覺 API，以辨識真實世界物件、 訓練服務模型，並顯示信心的功能，曾 mixed 的 reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fea5f-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="fea5f-485">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="fea5f-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="fea5f-486">練習 1</span><span class="sxs-lookup"><span data-stu-id="fea5f-486">Exercise 1</span></span>

<span data-ttu-id="fea5f-487">訓練您**Custom Vision Service**辨識更多的物件。</span><span class="sxs-lookup"><span data-stu-id="fea5f-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="fea5f-488">練習 2</span><span class="sxs-lookup"><span data-stu-id="fea5f-488">Exercise 2</span></span>

<span data-ttu-id="fea5f-489">展開您已了解的方法，完成下列練習：</span><span class="sxs-lookup"><span data-stu-id="fea5f-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="fea5f-490">當辨識項物件時，請播放的音效。</span><span class="sxs-lookup"><span data-stu-id="fea5f-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="fea5f-491">練習 3</span><span class="sxs-lookup"><span data-stu-id="fea5f-491">Exercise 3</span></span>

<span data-ttu-id="fea5f-492">使用 API，來重新訓練您的服務，與正在分析您的應用程式相同的映像，因此若要讓服務更精確 （執行預測和同時訓練）。</span><span class="sxs-lookup"><span data-stu-id="fea5f-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
