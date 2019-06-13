---
title: MR 和 Azure 310-物體偵測
description: 完成此課程來了解如何定型機器學習服務模型，然後使用定型的模型來識別相似的物件，並在混合的實境應用程式中從真實世界中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 中，自訂的視覺物件偵測、 混合實境、 academy、 unity、 教學課程、 api、 hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591148"
---
>[!NOTE]
><span data-ttu-id="05895-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="05895-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="05895-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="05895-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="05895-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="05895-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="05895-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="05895-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="05895-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="05895-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="05895-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="05895-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="05895-110">Mr 和 Azure 310:物件偵測</span><span class="sxs-lookup"><span data-stu-id="05895-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="05895-111">在此課程中，您將了解如何識別自訂的視覺內容，並提供的映像中，其空間位置使用 Azure Custom Vision 混合的實境應用程式中的 「 物件偵測 」 功能。</span><span class="sxs-lookup"><span data-stu-id="05895-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="05895-112">這項服務可讓您定型機器學習模型，使用物件的映像。</span><span class="sxs-lookup"><span data-stu-id="05895-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="05895-113">然後將定型的模型識別相似的物件，然後大約在真實世界中，其位置所提供的 Microsoft HoloLens 相機擷取或相機連接到電腦的沈浸式 (VR) 耳機。</span><span class="sxs-lookup"><span data-stu-id="05895-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![課程結果](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="05895-115">**Azure Custom Vision、 物體偵測**是一項 Microsoft 服務可讓開發人員建置自訂映像分類器。</span><span class="sxs-lookup"><span data-stu-id="05895-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="05895-116">這些分類器可以再搭配新的映像來偵測該新的映像 」 中的物件，藉由提供 **方塊界限** 的映像本身。</span><span class="sxs-lookup"><span data-stu-id="05895-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="05895-117">服務提供簡單、 容易使用的線上的入口網站，來簡化此程序。</span><span class="sxs-lookup"><span data-stu-id="05895-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="05895-118">如需詳細資訊，請瀏覽下列連結：</span><span class="sxs-lookup"><span data-stu-id="05895-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="05895-119">Azure 的自訂視覺頁面</span><span class="sxs-lookup"><span data-stu-id="05895-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="05895-120">限制和配額</span><span class="sxs-lookup"><span data-stu-id="05895-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="05895-121">完成本課程的詳細資訊，您必須能夠執行下列作業的混合的實境應用程式：</span><span class="sxs-lookup"><span data-stu-id="05895-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="05895-122">使用者將能夠*視線*的物件，它們必須使用 Azure Custom Vision Service，物件偵測來進行定型。</span><span class="sxs-lookup"><span data-stu-id="05895-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="05895-123">使用者會使用*點選*擷取的東西在映像的筆勢。</span><span class="sxs-lookup"><span data-stu-id="05895-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="05895-124">應用程式會將影像傳送到 Azure Custom Vision Service。</span><span class="sxs-lookup"><span data-stu-id="05895-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="05895-125">將會有的服務也會以全局空間文字顯示結果的辨識的回覆。</span><span class="sxs-lookup"><span data-stu-id="05895-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="05895-126">這會透過使用 Microsoft HoloLens 的空間追蹤，了解世界空間位置的可辨識的物件，然後使用這種方式來完成*標記*與項目中偵測到映像，為相關聯提供的標籤文字。</span><span class="sxs-lookup"><span data-stu-id="05895-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="05895-127">本課程也將涵蓋手動上傳的映像，建立標記，並訓練辨識不同的服務物件 （在提供的範例中，一杯），藉由設定*邊界方塊*您提交映像中。</span><span class="sxs-lookup"><span data-stu-id="05895-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="05895-128">下列建立和使用應用程式中，開發人員應瀏覽回 Azure Custom Vision Service，並識別服務時，所做的預測，並判斷是否它們是正確或不 (透過標記的任何項目服務遺漏，以及調整*週框方塊*)。</span><span class="sxs-lookup"><span data-stu-id="05895-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="05895-129">服務可以再進行重新定型，這會增加它辨識真實世界物件的可能性。</span><span class="sxs-lookup"><span data-stu-id="05895-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="05895-130">本課程將教導您如何從 Azure Custom Vision Service，物件偵測的結果取得到 Unity 為基礎的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="05895-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="05895-131">它會決定要將這些概念套用到您可能建置自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="05895-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="05895-132">裝置支援</span><span class="sxs-lookup"><span data-stu-id="05895-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="05895-133">課程</span><span class="sxs-lookup"><span data-stu-id="05895-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="05895-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="05895-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="05895-135"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="05895-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="05895-136">MR 和 Azure 310:物件偵測</span><span class="sxs-lookup"><span data-stu-id="05895-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="05895-137">✔️</span><span class="sxs-lookup"><span data-stu-id="05895-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="05895-138">先決條件</span><span class="sxs-lookup"><span data-stu-id="05895-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="05895-139">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="05895-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="05895-140">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。</span><span class="sxs-lookup"><span data-stu-id="05895-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="05895-141">中所示，您可以自由使用最新的軟體[安裝工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。</span><span class="sxs-lookup"><span data-stu-id="05895-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="05895-142">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="05895-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="05895-143">開發電腦</span><span class="sxs-lookup"><span data-stu-id="05895-143">A development PC</span></span>
- [<span data-ttu-id="05895-144">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="05895-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="05895-145">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="05895-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="05895-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="05895-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="05895-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="05895-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="05895-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="05895-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="05895-149">Azure 設定及自訂視覺服務擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="05895-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="05895-150">一系列的最少 15 （15） 映像所需的） 每個物件，您想要自訂視覺辨識。</span><span class="sxs-lookup"><span data-stu-id="05895-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="05895-151">如果您想，您可以使用本課程中，已提供的映像[一連串的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="05895-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="05895-152">開始之前</span><span class="sxs-lookup"><span data-stu-id="05895-152">Before you start</span></span>

1.  <span data-ttu-id="05895-153">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="05895-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="05895-154">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="05895-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="05895-155">如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="05895-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="05895-156">它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。</span><span class="sxs-lookup"><span data-stu-id="05895-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="05895-157">校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="05895-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="05895-158">如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="05895-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="05895-159">第 1 章-Custom Vision 入口網站</span><span class="sxs-lookup"><span data-stu-id="05895-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="05895-160">若要使用**Azure Custom Vision Service**，您必須設定它可讓您的應用程式使用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="05895-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="05895-161">瀏覽[要**Custom Vision Service**主頁](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。</span><span class="sxs-lookup"><span data-stu-id="05895-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="05895-162">按一下 **開始使用**。</span><span class="sxs-lookup"><span data-stu-id="05895-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="05895-163">登入自訂視覺入口網站。</span><span class="sxs-lookup"><span data-stu-id="05895-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="05895-164">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="05895-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="05895-165">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="05895-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="05895-166">當您第一次登入時，您將會收到提示*服務條款*面板。</span><span class="sxs-lookup"><span data-stu-id="05895-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="05895-167">按一下核取方塊*同意條款*。</span><span class="sxs-lookup"><span data-stu-id="05895-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="05895-168">然後按一下**我同意**。</span><span class="sxs-lookup"><span data-stu-id="05895-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="05895-169">需要同意的條款，現在您已*我的專案*一節。</span><span class="sxs-lookup"><span data-stu-id="05895-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="05895-170">按一下 **新的專案**。</span><span class="sxs-lookup"><span data-stu-id="05895-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="05895-171">索引標籤會出現在右手邊的畫面會提示您指定的專案部分欄位。</span><span class="sxs-lookup"><span data-stu-id="05895-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="05895-172">插入您的專案名稱</span><span class="sxs-lookup"><span data-stu-id="05895-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="05895-173">插入您專案的描述 (**選擇性**)</span><span class="sxs-lookup"><span data-stu-id="05895-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="05895-174">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="05895-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="05895-175">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="05895-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="05895-176">建議將常見的資源群組下 （例如例如這些課程中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="05895-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="05895-177">如果您想要[深入了解 Azure 資源群組中，瀏覽至相關聯的文件](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="05895-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="05895-178">設定**專案類型**作為**物體偵測 （預覽）** 。</span><span class="sxs-lookup"><span data-stu-id="05895-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="05895-179">一旦您完成時，按一下**建立專案**，您就會重新導向至 Custom Vision Service 專案頁面。</span><span class="sxs-lookup"><span data-stu-id="05895-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="05895-180">第 2 章-訓練您的自訂視覺專案</span><span class="sxs-lookup"><span data-stu-id="05895-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="05895-181">一次在自訂視覺入口網站中，您的主要目標是訓練您的專案，以辨識影像中的特定物件。</span><span class="sxs-lookup"><span data-stu-id="05895-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="05895-182">對於每個您想要您的應用程式，可辨識的物件，您就會需要至少 15 個映像。</span><span class="sxs-lookup"><span data-stu-id="05895-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="05895-183">您可以使用本課程提供的映像 ([一連串的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="05895-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="05895-184">若要訓練您的自訂視覺專案：</span><span class="sxs-lookup"><span data-stu-id="05895-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="05895-185">按一下  **+** 按鈕旁**標記**。</span><span class="sxs-lookup"><span data-stu-id="05895-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="05895-186">新增**名稱**將用來將您的映像，以建立關聯的標記。</span><span class="sxs-lookup"><span data-stu-id="05895-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="05895-187">在此範例中我們用來辨識，因此已為此，命名標記映像的 cup **Cup**。</span><span class="sxs-lookup"><span data-stu-id="05895-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="05895-188">按一下 **儲存**一次完成。</span><span class="sxs-lookup"><span data-stu-id="05895-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="05895-189">您會注意到您**標記**已加入 （您可能需要重新載入您的頁面才會出現）。</span><span class="sxs-lookup"><span data-stu-id="05895-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="05895-190">按一下 **將影像加入**中頁面的中心。</span><span class="sxs-lookup"><span data-stu-id="05895-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="05895-191">按一下 **瀏覽本機檔案**，並瀏覽至您想要一個物件，並將最小值是 15 (15) 上傳的映像。</span><span class="sxs-lookup"><span data-stu-id="05895-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="05895-192">您可以選取數個映像，一次，若要上傳。</span><span class="sxs-lookup"><span data-stu-id="05895-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="05895-193">按下**將檔案上傳**一旦您選取的所有映像您想要定型的專案。</span><span class="sxs-lookup"><span data-stu-id="05895-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="05895-194">檔案就會開始上傳。</span><span class="sxs-lookup"><span data-stu-id="05895-194">The files will begin uploading.</span></span> <span data-ttu-id="05895-195">上傳的確認之後，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="05895-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="05895-196">此時您的映像上傳，但未標記。</span><span class="sxs-lookup"><span data-stu-id="05895-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="05895-197">若要標記您的映像，請使用滑鼠。</span><span class="sxs-lookup"><span data-stu-id="05895-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="05895-198">當您暫留在您的映像的選取項目反白顯示都能協助您藉由自動繪製您的物件周圍的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="05895-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="05895-199">如果您不正確，您可以繪製您自己。</span><span class="sxs-lookup"><span data-stu-id="05895-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="05895-200">這被透過滑鼠不放，以滑鼠左鍵按一下和拖曳選取範圍區域，以包含您的物件。</span><span class="sxs-lookup"><span data-stu-id="05895-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="05895-201">下列映像中物件的選取項目，小型的提示字元會要求您提供*新增 Region 標記*。</span><span class="sxs-lookup"><span data-stu-id="05895-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="05895-202">選取您先前建立的標記 ('Cup'，在上述範例中)，或如果您要新增更多標籤，輸入，然後按一下 **+ （加號）**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="05895-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="05895-203">若要標記下一步 的映像，您可以按一下刀鋒視窗中，右邊的箭號，或關閉 標記 刀鋒視窗 (依序按一下**X**刀鋒視窗的右上角)，然後按一下 下一步 的影像。</span><span class="sxs-lookup"><span data-stu-id="05895-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="05895-204">下一步 的映像準備好之後，重複執行相同的程序。</span><span class="sxs-lookup"><span data-stu-id="05895-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="05895-205">您已上傳，直到被所有標記的所有映像執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="05895-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="05895-206">您可以選取數個物件相同的映像，類似下面的影像中：</span><span class="sxs-lookup"><span data-stu-id="05895-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="05895-207">一旦您已標記它們全部，按一下**標記**按鈕，在左邊的畫面中，以顯示已加上標記的映像。</span><span class="sxs-lookup"><span data-stu-id="05895-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="05895-208">您現在已準備好定型您的服務。</span><span class="sxs-lookup"><span data-stu-id="05895-208">You are now ready to train your Service.</span></span> <span data-ttu-id="05895-209">按一下 **定型**按鈕，然後在第一個訓練反覆項目就會開始。</span><span class="sxs-lookup"><span data-stu-id="05895-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="05895-210">一旦建立，您會看到兩個按鈕稱為**設成預設值**並**預測 URL**。</span><span class="sxs-lookup"><span data-stu-id="05895-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="05895-211">按一下 **設成預設值**第一次，然後按一下**預測 URL**。</span><span class="sxs-lookup"><span data-stu-id="05895-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="05895-212">提供從這裡開始，將端點設為者為準*反覆項目*已標示為預設值。</span><span class="sxs-lookup"><span data-stu-id="05895-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="05895-213">因此，如果您稍後建立新*反覆項目*更新為預設值，您不需要變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="05895-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="05895-214">一旦您按下**預測 URL**，開啟*記事本*，然後複製並貼上**URL** (也稱為您**預測端點**)而**服務的預測金鑰**，如此一來，您可以稍後在程式碼中需要時擷取它。</span><span class="sxs-lookup"><span data-stu-id="05895-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="05895-215">第 3 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="05895-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="05895-216">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="05895-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="05895-217">開啟**Unity**然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="05895-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="05895-218">您現在必須提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="05895-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="05895-219">插入**CustomVisionObjDetection**。</span><span class="sxs-lookup"><span data-stu-id="05895-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="05895-220">請確定專案類型設定為**3D**，並將**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="05895-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="05895-221">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="05895-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="05895-222">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="05895-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="05895-223">移至 **編輯* > *喜好設定** 從新的視窗中，然後瀏覽至 **外部工具** 。</span><span class="sxs-lookup"><span data-stu-id="05895-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="05895-224">變更**外部指令碼編輯器**要**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="05895-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="05895-225">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="05895-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="05895-226">接下來，移至**檔案 > 組建設定**，並切換**平台**來*通用 Windows 平台*，然後按一下**切換平台**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="05895-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="05895-227">在同一個**組建設定** 視窗中，請確定下列設定：</span><span class="sxs-lookup"><span data-stu-id="05895-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="05895-228">**裝置為目標**設為**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="05895-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="05895-229">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="05895-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="05895-230">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="05895-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="05895-231">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="05895-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="05895-232">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="05895-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="05895-233">剩餘的設定，**組建設定**，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="05895-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="05895-234">在同一個**組建設定**視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。</span><span class="sxs-lookup"><span data-stu-id="05895-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="05895-235">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="05895-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="05895-236">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="05895-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="05895-237">**指令碼執行階段版本**應該**實驗性**（.NET 4.6 對等），這會觸發程序需要重新啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="05895-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="05895-238">**指令碼後端**應該 **.NET**。</span><span class="sxs-lookup"><span data-stu-id="05895-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="05895-239">**API 相容性層級**應該 **.NET 4.6**。</span><span class="sxs-lookup"><span data-stu-id="05895-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="05895-240">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="05895-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="05895-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="05895-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="05895-242">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="05895-242">**Webcam**</span></span>

        3. <span data-ttu-id="05895-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="05895-243">**SpatialPerception**</span></span>

            <span data-ttu-id="05895-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="05895-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="05895-245">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，然後確定**Windows 混合但實際上 SDK**加入。</span><span class="sxs-lookup"><span data-stu-id="05895-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="05895-246">回到**Build Settings**， *Unity C\#專案*不再呈現灰色： 這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="05895-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="05895-247">關閉**組建設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="05895-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="05895-248">在 **編輯器**，按一下**編輯** > **專案設定** > **圖形**。</span><span class="sxs-lookup"><span data-stu-id="05895-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="05895-249">在 [**偵測器] 面板** *圖形設定*將會開啟。</span><span class="sxs-lookup"><span data-stu-id="05895-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="05895-250">向下捲動，直到您看到稱為陣列**一律包含著色器**。</span><span class="sxs-lookup"><span data-stu-id="05895-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="05895-251">新增位置透過增加**大小**其中一個變數 (在此範例中，所以 8 我們 9)。</span><span class="sxs-lookup"><span data-stu-id="05895-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="05895-252">新的位置會顯示，在陣列中的最後一個位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="05895-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="05895-253">在位置中，按一下的位置，以開啟一份著色器旁邊的小目標圓形。</span><span class="sxs-lookup"><span data-stu-id="05895-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="05895-254">尋求**Diffuse/著色器/Transparent 舊版**著色器，然後按兩下它。</span><span class="sxs-lookup"><span data-stu-id="05895-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="05895-255">第 4 章-匯入 CustomVisionObjDetection Unity 封裝</span><span class="sxs-lookup"><span data-stu-id="05895-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="05895-256">本課程為您提供 Unity 資產套件，稱為**Azure-MR-310.unitypackage**。</span><span class="sxs-lookup"><span data-stu-id="05895-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="05895-257">[提示]支援的 Unity，包含整個場景，任何物件可以封裝到 **.unitypackage**檔案，並匯出 / 匯入在其他專案中。</span><span class="sxs-lookup"><span data-stu-id="05895-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="05895-258">這是將資產移之間不同最安全的且最有效率的方式**Unity 專案**。</span><span class="sxs-lookup"><span data-stu-id="05895-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="05895-259">您可以找到[您必須下載此處的 Azure-MR-310 封裝](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="05895-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="05895-260">您面前的 Unity 儀表板中，按一下**資產**在畫面頂端的功能表，然後按一下**匯入封裝 > 自訂封裝**。</span><span class="sxs-lookup"><span data-stu-id="05895-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="05895-261">使用檔案選擇器選取**Azure-MR-310.unitypackage**封裝，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="05895-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="05895-262">為此資產的元件的清單會顯示給您。</span><span class="sxs-lookup"><span data-stu-id="05895-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="05895-263">確認匯入，依序按一下**匯入** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="05895-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="05895-264">完成匯入後，您會發現現在有已從封裝的資料夾新增至您**資產**資料夾。</span><span class="sxs-lookup"><span data-stu-id="05895-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="05895-265">這種資料夾結構是典型的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="05895-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="05895-266">**材料**資料夾包含所使用的材料**視線游標**。</span><span class="sxs-lookup"><span data-stu-id="05895-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="05895-267">**外掛程式**資料夾包含用來還原序列化服務的 web 回應的程式碼 Newtonsoft DLL。</span><span class="sxs-lookup"><span data-stu-id="05895-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="05895-268">兩個 （2） 不同的版本中所包含的資料夾，以及子資料夾中，會允許要使用與 Unity Editor 和 UWP 建置所建置的程式庫所需。</span><span class="sxs-lookup"><span data-stu-id="05895-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="05895-269">**Prefabs**資料夾包含在場景中包含 prefabs。</span><span class="sxs-lookup"><span data-stu-id="05895-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="05895-270">這些是：</span><span class="sxs-lookup"><span data-stu-id="05895-270">Those are:</span></span>

        1.  <span data-ttu-id="05895-271">**GazeCursor**，應用程式中使用的游標。</span><span class="sxs-lookup"><span data-stu-id="05895-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="05895-272">將 SpatialMapping prefab，若要能夠放在實體物件上場景中一起運作。</span><span class="sxs-lookup"><span data-stu-id="05895-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="05895-273">**標籤**，它是用來顯示物件標記中的場景時所需的 UI 物件。</span><span class="sxs-lookup"><span data-stu-id="05895-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="05895-274">**SpatialMapping**，這是讓應用程式使用的物件建立一個虛擬的對應，使用 Microsoft HoloLens 的空間追蹤。</span><span class="sxs-lookup"><span data-stu-id="05895-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="05895-275">**場景**所在的資料夾目前這堂課程預先建置的場景。</span><span class="sxs-lookup"><span data-stu-id="05895-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="05895-276">開啟**場景**資料夾，請在 **[專案] 面板**，然後按兩下**ObjDetectionScene**、 載入場景，您將用於本課程。</span><span class="sxs-lookup"><span data-stu-id="05895-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="05895-277">**不包含任何程式碼**，您將會依照本課程中撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="05895-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="05895-278">第 5-建立 CustomVisionAnalyser 類別。</span><span class="sxs-lookup"><span data-stu-id="05895-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="05895-279">此時，您已準備好開始撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="05895-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="05895-280">將開頭**CustomVisionAnalyser**類別。</span><span class="sxs-lookup"><span data-stu-id="05895-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="05895-281">若要呼叫**Custom Vision Service**，如下所示的程式碼中，使用**自訂視覺 REST API**。</span><span class="sxs-lookup"><span data-stu-id="05895-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="05895-282">透過使用這種情況，您會看到如何實作及使用此 api （適用於了解如何自行實作類似）。</span><span class="sxs-lookup"><span data-stu-id="05895-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="05895-283">請注意，Microsoft 提供了**自訂視覺 SDK** ，也可用來對服務進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="05895-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="05895-284">如需詳細資訊，請造訪[自訂視覺 SDK 文件](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。</span><span class="sxs-lookup"><span data-stu-id="05895-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="05895-285">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="05895-285">This class is responsible for:</span></span>

- <span data-ttu-id="05895-286">正在載入最新的映像擷取成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="05895-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="05895-287">將位元組陣列傳送至您的 Azure **Custom Vision Service**執行個體進行分析。</span><span class="sxs-lookup"><span data-stu-id="05895-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="05895-288">接收回應為 JSON 字串。</span><span class="sxs-lookup"><span data-stu-id="05895-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="05895-289">還原序列化回應，並傳遞產生**預測**要**SceneOrganiser**類別，它會負責顯示回應的方式。</span><span class="sxs-lookup"><span data-stu-id="05895-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="05895-290">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="05895-290">To create this class:</span></span>

1.  <span data-ttu-id="05895-291">以滑鼠右鍵按一下**Assets 資料夾**，位於 **[專案] 面板**，然後按一下**建立** > **資料夾**。</span><span class="sxs-lookup"><span data-stu-id="05895-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="05895-292">呼叫資料夾**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="05895-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="05895-293">按兩下新建立的資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="05895-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="05895-294">在資料夾中，以滑鼠右鍵按一下，然後按一下  **Create** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="05895-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="05895-295">指令碼命名**CustomVisionAnalyser。**</span><span class="sxs-lookup"><span data-stu-id="05895-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="05895-296">按兩下新**CustomVisionAnalyser**指令碼，以開啟它**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="05895-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="05895-297">請確定您有下列命名空間參考在檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="05895-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="05895-298">在  **CustomVisionAnalyser**類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="05895-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="05895-299">請確定您插入您**服務的預測金鑰**成**predictionKey**變數和您**預測端點**到**predictionEndpoint**變數。</span><span class="sxs-lookup"><span data-stu-id="05895-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="05895-300">您可以複製這些[記事本更早版本，在第 2 章步驟 14](#chapter-2---training-your-custom-vision-project)。</span><span class="sxs-lookup"><span data-stu-id="05895-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="05895-301">程式碼**Awake()** 現在必須初始化執行個體變數新增：</span><span class="sxs-lookup"><span data-stu-id="05895-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="05895-302">新增協同程式 (具有靜態**GetImageAsByteArray()** 下方的方法)，這將會取得映像，所擷取的分析結果**ImageCapture**類別。</span><span class="sxs-lookup"><span data-stu-id="05895-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="05895-303">在  **AnalyseImageCapture**協同程式，來呼叫**SceneOrganiser**您即將建立的類別。</span><span class="sxs-lookup"><span data-stu-id="05895-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="05895-304">因此，**保留的線條標記為註解現在**。</span><span class="sxs-lookup"><span data-stu-id="05895-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. <span data-ttu-id="05895-305">刪除**start （)** 並**update （)** 方法，因為它們不會使用。</span><span class="sxs-lookup"><span data-stu-id="05895-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="05895-306">請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="05895-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05895-307">如先前所述，不必擔心可能會顯示有錯誤，將會進一步提供類別，以修正這些程式碼。</span><span class="sxs-lookup"><span data-stu-id="05895-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="05895-308">章節 6-建立 CustomVisionObjects 類別</span><span class="sxs-lookup"><span data-stu-id="05895-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="05895-309">您將建立的類別現在是**CustomVisionObjects**類別。</span><span class="sxs-lookup"><span data-stu-id="05895-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="05895-310">此指令碼包含用來序列化和還原序列化 Custom Vision Service 進行的呼叫其他類別的物件數目。</span><span class="sxs-lookup"><span data-stu-id="05895-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="05895-311">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="05895-311">To create this class:</span></span>

1.  <span data-ttu-id="05895-312">以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="05895-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="05895-313">呼叫指令碼**CustomVisionObjects。**</span><span class="sxs-lookup"><span data-stu-id="05895-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="05895-314">按兩下新**CustomVisionObjects**指令碼，以開啟它**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="05895-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="05895-315">請確定您有下列命名空間參考在檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="05895-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="05895-316">刪除**start （)** 並**update （)** 內的方法**CustomVisionObjects**類別，這個類別現在應空白。</span><span class="sxs-lookup"><span data-stu-id="05895-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="05895-317">請務必仔細遵循下一步 的指示。</span><span class="sxs-lookup"><span data-stu-id="05895-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="05895-318">如果您將新的類別宣告內**CustomVisionObjects**類別，會產生編譯錯誤，[章 10](#chapter-10---create-the-imagecapture-class)，， **AnalysisRootObject**和**BoundingBox**找不到。</span><span class="sxs-lookup"><span data-stu-id="05895-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="05895-319">新增下列類別*外* **CustomVisionObjects**類別。</span><span class="sxs-lookup"><span data-stu-id="05895-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="05895-320">這些物件由**Newtonsoft**序列化和還原序列化回應資料的程式庫：</span><span class="sxs-lookup"><span data-stu-id="05895-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="05895-321">請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="05895-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="05895-322">第 7-建立 SpatialMapping 類別</span><span class="sxs-lookup"><span data-stu-id="05895-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="05895-323">此類別會設定**空間的對應 Collider**因此若要能夠偵測到虛擬與實際的物件間的衝突，場景中。</span><span class="sxs-lookup"><span data-stu-id="05895-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="05895-324">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="05895-324">To create this class:</span></span>

1.  <span data-ttu-id="05895-325">以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="05895-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="05895-326">呼叫指令碼**SpatialMapping。**</span><span class="sxs-lookup"><span data-stu-id="05895-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="05895-327">按兩下新**SpatialMapping**指令碼，以開啟它**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="05895-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="05895-328">請確定您具有下列命名空間上面提及**SpatialMapping**類別：</span><span class="sxs-lookup"><span data-stu-id="05895-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="05895-329">然後，新增下列變數內**SpatialMapping**類別，上述**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="05895-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="05895-330">新增**Awake()** 並**start**:</span><span class="sxs-lookup"><span data-stu-id="05895-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="05895-331">刪除**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="05895-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="05895-332">請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="05895-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="05895-333">第 8-建立 GazeCursor 類別</span><span class="sxs-lookup"><span data-stu-id="05895-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="05895-334">這個類別會負責設定資料指標，在正確的位置，在實際的空間中，藉由使用**SpatialMappingCollider**、 上一章中建立。</span><span class="sxs-lookup"><span data-stu-id="05895-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="05895-335">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="05895-335">To create this class:</span></span>

1.  <span data-ttu-id="05895-336">以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="05895-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="05895-337">呼叫指令碼**GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="05895-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="05895-338">按兩下新**GazeCursor**指令碼，以開啟它**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="05895-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="05895-339">請確定您具有下列命名空間，上面提及**GazeCursor**類別：</span><span class="sxs-lookup"><span data-stu-id="05895-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="05895-340">然後新增下列變數內**GazeCursor**類別，上述**start （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="05895-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="05895-341">更新**start （)** 為下列程式碼的方法：</span><span class="sxs-lookup"><span data-stu-id="05895-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="05895-342">更新**update （)** 為下列程式碼的方法：</span><span class="sxs-lookup"><span data-stu-id="05895-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="05895-343">不必擔心的錯誤**SceneOrganiser**類別找不到，您將在下一步 一章。</span><span class="sxs-lookup"><span data-stu-id="05895-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="05895-344">請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="05895-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="05895-345">第 9-建立 SceneOrganiser 類別</span><span class="sxs-lookup"><span data-stu-id="05895-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="05895-346">這個類別將會：</span><span class="sxs-lookup"><span data-stu-id="05895-346">This class will:</span></span>

-   <span data-ttu-id="05895-347">設定好*Main Camera*將 cvcollectioncmd 附加至適當的元件。</span><span class="sxs-lookup"><span data-stu-id="05895-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="05895-348">偵測到物件時，它會負責計算其位置與真實世界中的位置**標記標籤**附近以適當**標記名稱**。</span><span class="sxs-lookup"><span data-stu-id="05895-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="05895-349">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="05895-349">To create this class:</span></span>

1.  <span data-ttu-id="05895-350">以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="05895-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="05895-351">指令碼命名**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="05895-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="05895-352">按兩下新**SceneOrganiser**指令碼，以開啟它**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="05895-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="05895-353">請確定您具有下列命名空間上面提及**SceneOrganiser**類別：</span><span class="sxs-lookup"><span data-stu-id="05895-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="05895-354">然後新增下列變數內**SceneOrganiser**類別，上述**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="05895-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="05895-355">刪除**start （)** 並**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="05895-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="05895-356">底下的變數中，加入**Awake()** 方法，它會初始化類別，並設定場景。</span><span class="sxs-lookup"><span data-stu-id="05895-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="05895-357">新增**PlaceAnalysisLabel()** 方法，將*具現化*場景 （這現在是看不到使用者項目） 中的標籤。</span><span class="sxs-lookup"><span data-stu-id="05895-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="05895-358">它也會四組數字 （也不可見） 映像放，而與真實世界重疊。</span><span class="sxs-lookup"><span data-stu-id="05895-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="05895-359">這很重要，因為方塊座標會從服務擷取之後分析會回溯追蹤到這個四判斷真實世界中物件的概略位置。</span><span class="sxs-lookup"><span data-stu-id="05895-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="05895-360">新增**FinaliseLabel()** 方法。</span><span class="sxs-lookup"><span data-stu-id="05895-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="05895-361">它會負責：</span><span class="sxs-lookup"><span data-stu-id="05895-361">It is responsible for:</span></span>

    *   <span data-ttu-id="05895-362">設定*標籤*文字*標記*具有最高信賴度預測。</span><span class="sxs-lookup"><span data-stu-id="05895-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="05895-363">呼叫的計算*週框方塊*在四個物件，過去，定位和放置在場景中的標籤。</span><span class="sxs-lookup"><span data-stu-id="05895-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="05895-364">使用針對 Raycast 調整標籤深度*週框方塊*，這應該會對真實世界中的物件發生衝突。</span><span class="sxs-lookup"><span data-stu-id="05895-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="05895-365">正在重設以允許使用者擷取另一個映像擷取程序。</span><span class="sxs-lookup"><span data-stu-id="05895-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="05895-366">新增**CalculateBoundingBoxPosition()** 方法，它會裝載數目進行轉譯所需的計算*週框方塊*座標從服務擷取和重新建立它們按比例上四組數字。</span><span class="sxs-lookup"><span data-stu-id="05895-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="05895-367">請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="05895-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="05895-368">在繼續之前，開啟**CustomVisionAnalyser**類別，會在**AnalyseLastImageCaptured()** 方法*取消註解*下列幾行：</span><span class="sxs-lookup"><span data-stu-id="05895-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="05895-369">不要擔心**ImageCapture**類別 '無法找到' 的訊息中，您將在下一步 一章。</span><span class="sxs-lookup"><span data-stu-id="05895-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="05895-370">第 10-建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="05895-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="05895-371">下一步要建立的類別是**ImageCapture**類別。</span><span class="sxs-lookup"><span data-stu-id="05895-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="05895-372">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="05895-372">This class is responsible for:</span></span>

*   <span data-ttu-id="05895-373">擷取映像使用 HoloLens 相機，並將它儲存在*應用程式*資料夾。</span><span class="sxs-lookup"><span data-stu-id="05895-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="05895-374">處理*點選*使用者筆勢。</span><span class="sxs-lookup"><span data-stu-id="05895-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="05895-375">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="05895-375">To create this class:</span></span>

1.  <span data-ttu-id="05895-376">移至**指令碼**您先前建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="05895-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="05895-377">在資料夾中，以滑鼠右鍵按一下，然後按一下  **Create** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="05895-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="05895-378">指令碼命名**ImageCapture**。</span><span class="sxs-lookup"><span data-stu-id="05895-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="05895-379">按兩下新**ImageCapture**指令碼，以開啟它**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="05895-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="05895-380">以下列內容取代頂端的 檔案命名空間：</span><span class="sxs-lookup"><span data-stu-id="05895-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="05895-381">然後新增下列變數內**ImageCapture**類別，上述**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="05895-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="05895-382">程式碼**Awake()** 並**start （)** 方法現在需要新增：</span><span class="sxs-lookup"><span data-stu-id="05895-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="05895-383">實作會在點選手勢時呼叫的處理常式：</span><span class="sxs-lookup"><span data-stu-id="05895-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="05895-384">當游標位於**綠色**，它表示相機可採取的映像。</span><span class="sxs-lookup"><span data-stu-id="05895-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="05895-385">當游標位於**紅色**，這表示相機正在忙碌中。</span><span class="sxs-lookup"><span data-stu-id="05895-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="05895-386">新增應用程式用來啟動映像擷取程序，並儲存映像的方法：</span><span class="sxs-lookup"><span data-stu-id="05895-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  <span data-ttu-id="05895-387">新增處理常式會被呼叫時已擷取相片並時準備好進行分析。</span><span class="sxs-lookup"><span data-stu-id="05895-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="05895-388">結果會傳遞至**CustomVisionAnalyser**進行分析。</span><span class="sxs-lookup"><span data-stu-id="05895-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="05895-389">請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="05895-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="05895-390">第 11 章-設定在場景中的指令碼</span><span class="sxs-lookup"><span data-stu-id="05895-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="05895-391">既然您已撰寫所有必要為此專案的程式碼，就可以設定在場景，與在 prefabs，才能正確運作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="05895-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="05895-392">內**Unity Editor**，請在**階層面板**，選取**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="05895-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="05895-393">在 [**偵測器] 面板**，與**Main Camera**選取，按一下**新增元件**，然後搜尋**SceneOrganiser**指令碼和連按兩下，以將它加入。</span><span class="sxs-lookup"><span data-stu-id="05895-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="05895-394">在 [**專案] 面板**，開啟**Prefabs 資料夾**，拖曳**標籤**prefab 到*標籤*空白參考目標中輸入區域中，**SceneOrganiser**您剛剛加到的指令碼*Main Camera*，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="05895-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="05895-395">在 **階層面板**，選取**GazeCursor**的子系**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="05895-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="05895-396">在 [**偵測器] 面板**，與**GazeCursor**選取，按一下**新增元件**，然後搜尋**GazeCursor**指令碼和連按兩下，以將它加入。</span><span class="sxs-lookup"><span data-stu-id="05895-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="05895-397">同樣地，在**階層面板**，選取**SpatialMapping**的子系**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="05895-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="05895-398">在 [**偵測器] 面板**，與**SpatialMapping**選取，按一下**新增元件**，然後搜尋**SpatialMapping**指令碼然後連按兩下，以將它加入。</span><span class="sxs-lookup"><span data-stu-id="05895-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="05895-399">其餘的您的指令碼尚未設定將加入程式碼所**SceneOrganiser**指令碼，在執行階段。</span><span class="sxs-lookup"><span data-stu-id="05895-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="05895-400">第 12 章-建置前</span><span class="sxs-lookup"><span data-stu-id="05895-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="05895-401">若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="05895-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="05895-402">這麼做之前，請確認：</span><span class="sxs-lookup"><span data-stu-id="05895-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="05895-403">中所述的所有設定[第 3 章](#chapter-3---set-up-the-unity-project)都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="05895-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="05895-404">指令碼**SceneOrganiser**附加至**Main Camera**物件。</span><span class="sxs-lookup"><span data-stu-id="05895-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="05895-405">指令碼**GazeCursor**附加至**GazeCursor**物件。</span><span class="sxs-lookup"><span data-stu-id="05895-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="05895-406">指令碼**SpatialMapping**附加至**SpatialMapping**物件。</span><span class="sxs-lookup"><span data-stu-id="05895-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="05895-407">在 [第 5 章](#chapter-5---create-the-customvisionanalyser-class)，步驟 6:</span><span class="sxs-lookup"><span data-stu-id="05895-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="05895-408">請確定您插入您**預測的服務金鑰**成**predictionKey**變數。</span><span class="sxs-lookup"><span data-stu-id="05895-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="05895-409">您已插入您**預測端點**成**predictionEndpoint**類別。</span><span class="sxs-lookup"><span data-stu-id="05895-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="05895-410">第 13-建置的 UWP 方案和側載您的應用程式</span><span class="sxs-lookup"><span data-stu-id="05895-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="05895-411">您現在就來建置您的應用程式做為您將能夠部署到 Microsoft HoloLens 的 UWP 方案。</span><span class="sxs-lookup"><span data-stu-id="05895-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="05895-412">若要開始建置程序：</span><span class="sxs-lookup"><span data-stu-id="05895-412">To begin the build process:</span></span>

1.  <span data-ttu-id="05895-413">移至**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="05895-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="05895-414">刻度**Unity C\#專案**。</span><span class="sxs-lookup"><span data-stu-id="05895-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="05895-415">按一下 **將開啟的場景新增**。</span><span class="sxs-lookup"><span data-stu-id="05895-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="05895-416">這會將目前開啟的場景新增至組建。</span><span class="sxs-lookup"><span data-stu-id="05895-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="05895-417">按一下 [建置]  。</span><span class="sxs-lookup"><span data-stu-id="05895-417">Click **Build**.</span></span> <span data-ttu-id="05895-418">將會啟動 unity*檔案總管*視窗中，您要建立，然後選取 建置到應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="05895-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="05895-419">現在，建立該資料夾並將它命名**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="05895-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="05895-420">然後使用**應用程式**按一下 選取資料夾**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="05895-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="05895-421">Unity 會開始建置您的專案**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="05895-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="05895-422">一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。</span><span class="sxs-lookup"><span data-stu-id="05895-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="05895-423">若要部署到 Microsoft HoloLens，您會需要該裝置的 IP 位址 （適用於遠端部署），並確認也已**開發人員模式**設定。</span><span class="sxs-lookup"><span data-stu-id="05895-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="05895-424">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="05895-424">To do this:</span></span>

    1.  <span data-ttu-id="05895-425">儘管穿著您 HoloLens，開啟**設定**。</span><span class="sxs-lookup"><span data-stu-id="05895-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="05895-426">移至**網路和網際網路** > **Wi-fi** > **進階選項**</span><span class="sxs-lookup"><span data-stu-id="05895-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="05895-427">附註**IPv4**位址。</span><span class="sxs-lookup"><span data-stu-id="05895-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="05895-428">接下來，瀏覽回到**設定**，然後**更新與安全性** > **適用於開發人員**</span><span class="sxs-lookup"><span data-stu-id="05895-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="05895-429">設定**開發人員模式** *上*。</span><span class="sxs-lookup"><span data-stu-id="05895-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="05895-430">瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="05895-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="05895-431">在 方案組態選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="05895-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="05895-432">在 方案平台上，選取**x86，遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="05895-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="05895-433">系統會提示您插入**IP 位址**的遠端裝置上 (Microsoft HoloLens，在此情況下，記下)。</span><span class="sxs-lookup"><span data-stu-id="05895-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="05895-434">移至**建置**功能表，然後按一下 **部署方案**側載您 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="05895-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="05895-435">您的應用程式現在應該會出現在清單中，在您的 Microsoft HoloLens，即可啟動已安裝的應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="05895-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="05895-436">若要使用應用程式：</span><span class="sxs-lookup"><span data-stu-id="05895-436">To use the application:</span></span>

* <span data-ttu-id="05895-437">查看的物件，您培訓與您**Azure Custom Vision Service、 物體偵測**，並使用**點選手勢**。</span><span class="sxs-lookup"><span data-stu-id="05895-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="05895-438">如果物件已成功偵測到，全局空間*標籤文字*標記名稱會出現。</span><span class="sxs-lookup"><span data-stu-id="05895-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05895-439">每次您擷取相片，並將它傳送至服務，您可以返回 [服務] 頁面，並重新定型新擷取的映像的服務。</span><span class="sxs-lookup"><span data-stu-id="05895-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="05895-440">在開始時，可能會也必須更正*週框方塊*得更為準確地重新訓練的服務。</span><span class="sxs-lookup"><span data-stu-id="05895-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="05895-441">當 Microsoft HoloLens 感應器和/或在 Unity SpatialTrackingComponent 無法放置適當的 colliders，相對於真實世界物件放置標籤文字可能不會顯示接近的物件。</span><span class="sxs-lookup"><span data-stu-id="05895-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="05895-442">嘗試使用不同的介面上的應用程式，如果這種情況。</span><span class="sxs-lookup"><span data-stu-id="05895-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="05895-443">您自訂的願景，物件偵測應用程式</span><span class="sxs-lookup"><span data-stu-id="05895-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="05895-444">恭喜，您所建立的混合的實境應用程式，運用 Azure 自訂視覺物件偵測 API，而可以辨識的物件，從映像，然後提供該物件在 3D 空間中的約略位置。</span><span class="sxs-lookup"><span data-stu-id="05895-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="05895-445">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="05895-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="05895-446">練習 1</span><span class="sxs-lookup"><span data-stu-id="05895-446">Exercise 1</span></span>

<span data-ttu-id="05895-447">加入文字標籤，來包裝的實際物件的 3D 中使用半透明效果 cube*週框方塊*。</span><span class="sxs-lookup"><span data-stu-id="05895-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="05895-448">練習 2</span><span class="sxs-lookup"><span data-stu-id="05895-448">Exercise 2</span></span>

<span data-ttu-id="05895-449">訓練您的自訂視覺服務辨識更多的物件。</span><span class="sxs-lookup"><span data-stu-id="05895-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="05895-450">練習 3</span><span class="sxs-lookup"><span data-stu-id="05895-450">Exercise 3</span></span>

<span data-ttu-id="05895-451">當辨識項物件時，請播放的音效。</span><span class="sxs-lookup"><span data-stu-id="05895-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="05895-452">練習 4</span><span class="sxs-lookup"><span data-stu-id="05895-452">Exercise 4</span></span>

<span data-ttu-id="05895-453">使用 API，來重新訓練您的服務，與正在分析您的應用程式相同的映像，因此若要讓服務更精確 （執行預測和同時訓練）。</span><span class="sxs-lookup"><span data-stu-id="05895-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
