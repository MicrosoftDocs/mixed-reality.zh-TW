---
title: MR 和 Azure 310-物件偵測
description: 完成此課程以瞭解如何將機器學習模型定型, 然後使用定型的模型, 從混合現實應用程式中辨識出類似物件及其在現實世界中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 自訂視覺, 物件偵測, 混合現實, 學術, unity, 教學課程, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544414"
---
>[!NOTE]
><span data-ttu-id="be3a9-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="be3a9-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="be3a9-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="be3a9-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="be3a9-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="be3a9-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="be3a9-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="be3a9-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="be3a9-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="be3a9-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="be3a9-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="be3a9-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="be3a9-110">Mr 和 Azure 310:物件偵測</span><span class="sxs-lookup"><span data-stu-id="be3a9-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="be3a9-111">在此課程中, 您將瞭解如何使用混合現實應用程式中的 Azure 自訂視覺「物件偵測」功能, 辨識所提供影像中的自訂視覺內容及其空間位置。</span><span class="sxs-lookup"><span data-stu-id="be3a9-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="be3a9-112">此服務可讓您使用物件影像來定型機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="be3a9-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="be3a9-113">接著, 您將使用定型的模型來辨識類似物件, 並在現實世界中取得其位置, 如 Microsoft HoloLens 的相機捕捉或相機連線到電腦的沉浸式 (VR) 耳機所提供。</span><span class="sxs-lookup"><span data-stu-id="be3a9-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![課程結果](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="be3a9-115">**Azure 自訂視覺, 物件偵測**是一種 Microsoft 服務, 可讓開發人員建立自訂影像分類器。</span><span class="sxs-lookup"><span data-stu-id="be3a9-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="be3a9-116">這些分類器可以再搭配新的映像來偵測該新的映像 」 中的物件，藉由提供 **方塊界限** 的映像本身。</span><span class="sxs-lookup"><span data-stu-id="be3a9-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="be3a9-117">此服務提供簡單、便於使用的線上入口網站, 以簡化此程式。</span><span class="sxs-lookup"><span data-stu-id="be3a9-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="be3a9-118">如需詳細資訊, 請造訪下列連結:</span><span class="sxs-lookup"><span data-stu-id="be3a9-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="be3a9-119">Azure 自訂視覺頁面</span><span class="sxs-lookup"><span data-stu-id="be3a9-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="be3a9-120">限制和配額</span><span class="sxs-lookup"><span data-stu-id="be3a9-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="be3a9-121">完成本課程之後, 您將會有一個混合現實應用程式, 可以執行下列作業:</span><span class="sxs-lookup"><span data-stu-id="be3a9-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="be3a9-122">使用者將能夠使用 Azure 自訂視覺服務、物件偵測來進行訓練的物件。</span><span class="sxs-lookup"><span data-stu-id="be3a9-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="be3a9-123">使用者將使用點按手勢來捕獲其所查看內容的影像。</span><span class="sxs-lookup"><span data-stu-id="be3a9-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="be3a9-124">應用程式會將映射傳送至 Azure 自訂視覺服務。</span><span class="sxs-lookup"><span data-stu-id="be3a9-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="be3a9-125">將會有服務的回復, 其會將辨識結果顯示為世界空間的文字。</span><span class="sxs-lookup"><span data-stu-id="be3a9-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="be3a9-126">這會透過使用 Microsoft HoloLens 的空間追蹤來完成, 以瞭解辨識物件的世界位置, 然後使用與影像中偵測到的內容相關聯的標籤來提供標籤文字。</span><span class="sxs-lookup"><span data-stu-id="be3a9-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="be3a9-127">本課程也會說明如何手動上傳影像、建立標記和訓練服務, 藉由在您提交的影像內設定*界限*方塊來辨識不同的物件 (在提供的範例中為杯)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="be3a9-128">建立和使用應用程式之後, 開發人員應該流覽回到 Azure 自訂視覺服務, 並找出服務所做的預測, 並判斷其是否正確 (透過標記服務遺漏的任何專案, 以及調整周*框方塊*)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="be3a9-129">服務接著可以重新定型, 這樣會增加識別真實世界物件的可能性。</span><span class="sxs-lookup"><span data-stu-id="be3a9-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="be3a9-130">本課程將告訴您如何從 Azure 自訂視覺服務 (物件偵測) 取得結果, 使其成為以 Unity 為基礎的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="be3a9-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="be3a9-131">您必須將這些概念套用到您可能正在建立的自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="be3a9-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="be3a9-132">裝置支援</span><span class="sxs-lookup"><span data-stu-id="be3a9-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="be3a9-133">粗</span><span class="sxs-lookup"><span data-stu-id="be3a9-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="be3a9-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="be3a9-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="be3a9-135"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="be3a9-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="be3a9-136">MR 和 Azure 310:物件偵測</span><span class="sxs-lookup"><span data-stu-id="be3a9-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="be3a9-137">✔️</span><span class="sxs-lookup"><span data-stu-id="be3a9-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="be3a9-138">先決條件</span><span class="sxs-lookup"><span data-stu-id="be3a9-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="be3a9-139">本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="be3a9-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="be3a9-140">也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (2018 年7月)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="be3a9-141">您可以免費使用 [[安裝工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)] 文章中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="be3a9-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="be3a9-142">在此課程中, 我們建議您採用下列硬體和軟體:</span><span class="sxs-lookup"><span data-stu-id="be3a9-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="be3a9-143">開發電腦</span><span class="sxs-lookup"><span data-stu-id="be3a9-143">A development PC</span></span>
- [<span data-ttu-id="be3a9-144">已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="be3a9-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="be3a9-145">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="be3a9-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="be3a9-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="be3a9-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="be3a9-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="be3a9-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="be3a9-148">已啟用開發人員模式的[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)</span><span class="sxs-lookup"><span data-stu-id="be3a9-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="be3a9-149">Azure 設定和自訂視覺服務的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="be3a9-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="be3a9-150">您想要自訂視覺辨識的每個物件都需要一系列至少 15 (15) 個影像)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="be3a9-151">如有需要, 您可以使用本課程中已提供的影像,[一系列的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="be3a9-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="be3a9-152">開始之前</span><span class="sxs-lookup"><span data-stu-id="be3a9-152">Before you start</span></span>

1.  <span data-ttu-id="be3a9-153">為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="be3a9-154">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="be3a9-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="be3a9-155">如果您需要支援設定 HoloLens,[請務必造訪 hololens 安裝程式一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="be3a9-156">開始開發新的 HoloLens 應用程式時, 最好先執行校正和感應器微調 (有時候它有助於為每個使用者執行這些工作)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="be3a9-157">如需校正的說明, 請遵循此[HoloLens 校正文章的連結](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="be3a9-158">如需感應器微調的說明, 請遵循此[HoloLens 感應器微調文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="be3a9-159">第1章-自訂視覺入口網站</span><span class="sxs-lookup"><span data-stu-id="be3a9-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="be3a9-160">若要使用**Azure 自訂視覺服務**, 您必須將其實例設定為可供您的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="be3a9-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="be3a9-161">流覽[至 [**自訂視覺服務**] 主頁面](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="be3a9-162">按一下 [**消費者入門**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="be3a9-163">登入自訂視覺入口網站。</span><span class="sxs-lookup"><span data-stu-id="be3a9-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="be3a9-164">如果您還沒有 Azure 帳戶, 您將需要建立一個。</span><span class="sxs-lookup"><span data-stu-id="be3a9-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="be3a9-165">如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。</span><span class="sxs-lookup"><span data-stu-id="be3a9-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="be3a9-166">當您第一次登入之後, 系統會提示您使用 [*服務條款*] 面板。</span><span class="sxs-lookup"><span data-stu-id="be3a9-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="be3a9-167">按一下核取方塊以*同意條款*。</span><span class="sxs-lookup"><span data-stu-id="be3a9-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="be3a9-168">然後按一下 [**我同意**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="be3a9-169">當您同意這些條款時, 您現在會在 [*我的專案*] 區段中。</span><span class="sxs-lookup"><span data-stu-id="be3a9-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="be3a9-170">按一下 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="be3a9-171">右側會出現一個索引標籤, 它會提示您指定專案的某些欄位。</span><span class="sxs-lookup"><span data-stu-id="be3a9-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="be3a9-172">插入專案的名稱</span><span class="sxs-lookup"><span data-stu-id="be3a9-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="be3a9-173">插入專案的描述 (**選擇性**)</span><span class="sxs-lookup"><span data-stu-id="be3a9-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="be3a9-174">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="be3a9-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="be3a9-175">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="be3a9-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="be3a9-176">建議您將與單一專案相關聯的所有 Azure 服務 (例如這些課程) 都保留在通用資源群組下)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="be3a9-177">如果您想要[深入瞭解 Azure 資源群組, 請流覽至相關聯的](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)檔</span><span class="sxs-lookup"><span data-stu-id="be3a9-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="be3a9-178">將**專案類型**設定為 [**物件偵測 (預覽)** ]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="be3a9-179">完成後, 按一下 [**建立專案**], 系統會將您重新導向至 [自訂視覺服務專案] 頁面。</span><span class="sxs-lookup"><span data-stu-id="be3a9-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="be3a9-180">第2章-訓練您的自訂視覺專案</span><span class="sxs-lookup"><span data-stu-id="be3a9-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="be3a9-181">在自訂視覺入口網站中, 您的主要目標是要將您的專案定型, 以辨識影像中的特定物件。</span><span class="sxs-lookup"><span data-stu-id="be3a9-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="be3a9-182">針對您希望應用程式辨識的每個物件, 您至少需要15個 (15) 個影像。</span><span class="sxs-lookup"><span data-stu-id="be3a9-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="be3a9-183">您可以使用本課程所提供的影像 ([一系列的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="be3a9-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="be3a9-184">若要將您的自訂視覺專案定型:</span><span class="sxs-lookup"><span data-stu-id="be3a9-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="be3a9-185">按一下 [ **+** **標記**] 旁的按鈕。</span><span class="sxs-lookup"><span data-stu-id="be3a9-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="be3a9-186">新增將用來建立影像關聯的標記**名稱**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="be3a9-187">在此範例中, 我們會使用 cup 的影像來進行辨識, 因此, 請將標記命名為「**杯**」。</span><span class="sxs-lookup"><span data-stu-id="be3a9-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="be3a9-188">完成後, 按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="be3a9-189">您會注意到您已新增標籤 (您可能需要重載頁面, 才會出現此**標記**)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="be3a9-190">按一下頁面中央的 [**新增影像**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="be3a9-191">按一下 **[流覽本機檔案]** , 然後流覽至您想要上傳給一個物件的影像, 其最小值為 15 (15)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="be3a9-192">您可以一次選取數個影像, 以進行上傳。</span><span class="sxs-lookup"><span data-stu-id="be3a9-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="be3a9-193">選取您想要用來定型專案的所有影像之後, 請按 **[上傳**檔案]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="be3a9-194">檔案將會開始上傳。</span><span class="sxs-lookup"><span data-stu-id="be3a9-194">The files will begin uploading.</span></span> <span data-ttu-id="be3a9-195">確認上傳之後, 請按一下 [**完成**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="be3a9-196">此時, 您的影像已上傳, 但未加上標籤。</span><span class="sxs-lookup"><span data-stu-id="be3a9-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="be3a9-197">若要標記影像, 請使用您的滑鼠。</span><span class="sxs-lookup"><span data-stu-id="be3a9-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="be3a9-198">當您將滑鼠停留在影像上時, 選取專案反白顯示會自動在物件周圍繪製選取專案。</span><span class="sxs-lookup"><span data-stu-id="be3a9-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="be3a9-199">如果不正確, 您可以自行繪製。</span><span class="sxs-lookup"><span data-stu-id="be3a9-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="be3a9-200">這是藉由按住滑鼠左鍵, 並將選取區域拖曳至包含物件的方式來完成。</span><span class="sxs-lookup"><span data-stu-id="be3a9-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="be3a9-201">在影像中選取您的物件之後, 就會出現一個小提示, 詢問您是否要*新增區域標記*。</span><span class="sxs-lookup"><span data-stu-id="be3a9-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="be3a9-202">選取您先前建立的標籤 (在上述範例中為「杯」), 或者, 如果您要新增更多標籤, 請在中輸入該標記, 然後按一下 [ **+] (加號)** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="be3a9-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="be3a9-203">若要標記下一個影像, 您可以按一下分頁右邊的箭號, 或關閉 [標記] 分頁 (按一下分頁右上角的**X** ), 然後按下一個影像。</span><span class="sxs-lookup"><span data-stu-id="be3a9-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="be3a9-204">當您準備好下一個映射之後, 請重複相同的程式。</span><span class="sxs-lookup"><span data-stu-id="be3a9-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="be3a9-205">針對您上傳的所有影像執行此動作, 直到全部標記完畢為止。</span><span class="sxs-lookup"><span data-stu-id="be3a9-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="be3a9-206">您可以選取相同影像中的數個物件, 如下圖所示:</span><span class="sxs-lookup"><span data-stu-id="be3a9-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="be3a9-207">標記全部之後, 請按一下畫面左側的已**標記**按鈕, 以顯示已標記的影像。</span><span class="sxs-lookup"><span data-stu-id="be3a9-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="be3a9-208">您現在已準備好訓練您的服務。</span><span class="sxs-lookup"><span data-stu-id="be3a9-208">You are now ready to train your Service.</span></span> <span data-ttu-id="be3a9-209">按一下 [**定型**] 按鈕, 就會開始進行第一個定型反復專案。</span><span class="sxs-lookup"><span data-stu-id="be3a9-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="be3a9-210">建立之後, 您就可以看到兩個名為 [設為**預設**] 和 [**預測 URL**] 的按鈕。</span><span class="sxs-lookup"><span data-stu-id="be3a9-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="be3a9-211">按一下 [**設為預設值**], 然後按一下 [**預測 URL**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="be3a9-212">從這個提供的端點會設定為任何已標示為預設的*反復*專案。</span><span class="sxs-lookup"><span data-stu-id="be3a9-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="be3a9-213">因此, 如果您稍後進行新的*反復*專案, 並將其更新為預設值, 則不需要變更您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="be3a9-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="be3a9-214">當您按一下 [**預測 URL**] 之後, 請開啟 [*記事本*], 然後複製並貼上**URL** (也稱為您的**預測端點**) 和**服務預測金鑰**, 以便您稍後在程式碼中需要時加以取出。</span><span class="sxs-lookup"><span data-stu-id="be3a9-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="be3a9-215">第3章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="be3a9-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="be3a9-216">以下是使用混合現實進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="be3a9-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="be3a9-217">開啟**Unity** , 然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="be3a9-218">現在您將需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="be3a9-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="be3a9-219">插入**CustomVisionObjDetection**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="be3a9-220">請確定 [專案類型] 設定為 [ **3d**], 並將 [位置] 設定為適合您的**位置**(請記住, 接近根目錄較佳)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="be3a9-221">然後, 按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="be3a9-222">在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="be3a9-223">移至 **編輯* > *喜好設定** 從新的視窗中，然後瀏覽至 **外部工具** 。</span><span class="sxs-lookup"><span data-stu-id="be3a9-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="be3a9-224">將**外部腳本編輯器**變更為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="be3a9-225">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="be3a9-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="be3a9-226">接下來, 移至 [檔案] **> [組建設定**], 並將**平臺**切換至 [*通用 Windows 平臺*], 然後按一下 [**切換平臺**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="be3a9-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="be3a9-227">在相同的 [**組建設定**] 視窗中, 確定已設定下列各項:</span><span class="sxs-lookup"><span data-stu-id="be3a9-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="be3a9-228">**目標裝置**設定為**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="be3a9-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="be3a9-229">**組建類型**設定為**D3D**</span><span class="sxs-lookup"><span data-stu-id="be3a9-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="be3a9-230">**SDK**已設定為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="be3a9-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="be3a9-231">**Visual Studio 版本**設定為 [**最新安裝**]</span><span class="sxs-lookup"><span data-stu-id="be3a9-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="be3a9-232">**組建和執行**設定為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="be3a9-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="be3a9-233">[**組建設定**] 中的其餘設定, 現在應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="be3a9-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="be3a9-234">在相同的 [**組建設定**] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測**器**所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="be3a9-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="be3a9-235">在此面板中, 需要驗證幾項設定:</span><span class="sxs-lookup"><span data-stu-id="be3a9-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="be3a9-236">在 [**其他設定**] 索引標籤中:</span><span class="sxs-lookup"><span data-stu-id="be3a9-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="be3a9-237">**腳本執行階段版本**應該是**實驗**性 (.net 4.6 對等用法), 這將會觸發重新開機編輯器的需求。</span><span class="sxs-lookup"><span data-stu-id="be3a9-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="be3a9-238">**腳本後端**應該是 **.net**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="be3a9-239">**API 相容性層級**應該是 **.net 4.6**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="be3a9-240">在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:</span><span class="sxs-lookup"><span data-stu-id="be3a9-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="be3a9-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="be3a9-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="be3a9-242">**網路**</span><span class="sxs-lookup"><span data-stu-id="be3a9-242">**Webcam**</span></span>

        3. <span data-ttu-id="be3a9-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="be3a9-243">**SpatialPerception**</span></span>

            <span data-ttu-id="be3a9-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="be3a9-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="be3a9-245">在面板的正下方, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到)、[**支援的虛擬實境**], 然後確定已新增 [ **Windows Mixed Reality SDK** ]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="be3a9-246">回到 [**組建設定**], *Unity\# C 專案*不再呈現灰色: 勾選 [this] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="be3a9-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="be3a9-247">關閉 [**組建設定**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="be3a9-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="be3a9-248">在**編輯器**中, 按一下 [**編輯** > **專案設定** > ] [**圖形**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="be3a9-249">在 [**偵測器] 面板** *圖形設定*將會開啟。</span><span class="sxs-lookup"><span data-stu-id="be3a9-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="be3a9-250">向下滾動直到看到名為 [**永遠包含著色**器] 的陣列。</span><span class="sxs-lookup"><span data-stu-id="be3a9-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="be3a9-251">藉由將**大小**變數增加一個來新增位置 (在此範例中, 它是 8, 所以我們將它設為 9)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="be3a9-252">陣列的最後一個位置會出現新的位置, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="be3a9-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="be3a9-253">在插槽中, 按一下插槽旁的小型目標圓形, 以開啟著色器清單。</span><span class="sxs-lookup"><span data-stu-id="be3a9-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="be3a9-254">尋找**舊版著色器/透明/擴散**著色器, 然後按兩下它。</span><span class="sxs-lookup"><span data-stu-id="be3a9-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="be3a9-255">第4章-匯入 CustomVisionObjDetection Unity 封裝</span><span class="sxs-lookup"><span data-stu-id="be3a9-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="be3a9-256">在此課程中, 您會提供名為**unitypackage**的 Unity 資產套件。</span><span class="sxs-lookup"><span data-stu-id="be3a9-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="be3a9-257">首先Unity 支援的任何物件 (包括整個場景) 都可以封裝成**unitypackage**檔案, 並在其他專案中匯出/匯入。</span><span class="sxs-lookup"><span data-stu-id="be3a9-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="be3a9-258">這是在不同**Unity 專案**之間移動資產最安全且最有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="be3a9-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="be3a9-259">您可以在[這裡找到您需要下載的 Azure-MR-310 套件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="be3a9-260">在您前方的 Unity 儀表板中, 按一下畫面頂端功能表中的 **資產**, 然後按一下 匯**入套件 > 自訂套件**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="be3a9-261">使用檔案選擇器選取**unitypackage**套件, 然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="be3a9-262">系統會顯示此資產的元件清單。</span><span class="sxs-lookup"><span data-stu-id="be3a9-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="be3a9-263">按一下 [匯**入**] 按鈕以確認匯入。</span><span class="sxs-lookup"><span data-stu-id="be3a9-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="be3a9-264">完成匯入之後, 您會發現套件中的資料夾現在已新增至您的 [**資產**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="be3a9-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="be3a9-265">這種資料夾結構通常適用于 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="be3a9-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="be3a9-266">[**材質**] 資料夾包含**注視游標**所使用的材質。</span><span class="sxs-lookup"><span data-stu-id="be3a9-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="be3a9-267">[**外掛程式**] 資料夾包含程式碼用來還原序列化服務 web 回應的 Newtonsoft DLL。</span><span class="sxs-lookup"><span data-stu-id="be3a9-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="be3a9-268">資料夾和子資料夾中所包含的兩個 (2) 不同版本是必要的, 以便讓 Unity 編輯器和 UWP 組建都能使用並建立程式庫。</span><span class="sxs-lookup"><span data-stu-id="be3a9-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="be3a9-269">**Prefabs**資料夾包含場景中包含的 Prefabs。</span><span class="sxs-lookup"><span data-stu-id="be3a9-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="be3a9-270">這些是:</span><span class="sxs-lookup"><span data-stu-id="be3a9-270">Those are:</span></span>

        1.  <span data-ttu-id="be3a9-271">**GazeCursor**, 這是應用程式中使用的資料指標。</span><span class="sxs-lookup"><span data-stu-id="be3a9-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="be3a9-272">會與 SpatialMapping prefab 搭配使用, 以放在實體物件頂端的場景中。</span><span class="sxs-lookup"><span data-stu-id="be3a9-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="be3a9-273">**標籤**, 這是在必要時, 用來在場景中顯示物件標記的 UI 物件。</span><span class="sxs-lookup"><span data-stu-id="be3a9-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="be3a9-274">**SpatialMapping**, 這是可讓應用程式使用 Microsoft HoloLens 的空間追蹤來建立虛擬對應的物件。</span><span class="sxs-lookup"><span data-stu-id="be3a9-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="be3a9-275">**幕後**資料夾, 其中目前包含此課程的預先建立場景。</span><span class="sxs-lookup"><span data-stu-id="be3a9-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="be3a9-276">開啟 [**幕後**] 資料夾, 在 [**專案] 面板**中按兩下 [ **ObjDetectionScene**], 以載入您將用於本課程的場景。</span><span class="sxs-lookup"><span data-stu-id="be3a9-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="be3a9-277">**未包含任何程式碼**, 您將會遵循此課程來撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="be3a9-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="be3a9-278">第5章-建立 CustomVisionAnalyser 類別。</span><span class="sxs-lookup"><span data-stu-id="be3a9-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="be3a9-279">此時, 您已準備好撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="be3a9-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="be3a9-280">您將會從**CustomVisionAnalyser**類別開始。</span><span class="sxs-lookup"><span data-stu-id="be3a9-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="be3a9-281">**自訂視覺服務**的呼叫是在如下所示的程式碼中, 使用**自訂視覺 REST API**來進行。</span><span class="sxs-lookup"><span data-stu-id="be3a9-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="be3a9-282">藉由使用此功能, 您將瞭解如何執行並利用此 API (適用于瞭解如何執行與您自己類似的專案)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="be3a9-283">請注意, Microsoft 提供的**自訂視覺 SDK**也可以用來對服務進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="be3a9-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="be3a9-284">如需詳細資訊, 請造訪[自訂視覺 SDK 文章](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="be3a9-285">此類別負責:</span><span class="sxs-lookup"><span data-stu-id="be3a9-285">This class is responsible for:</span></span>

- <span data-ttu-id="be3a9-286">載入以位元組陣列形式捕獲的最新影像。</span><span class="sxs-lookup"><span data-stu-id="be3a9-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="be3a9-287">將位元組陣列傳送至您的 Azure**自訂視覺服務**實例以進行分析。</span><span class="sxs-lookup"><span data-stu-id="be3a9-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="be3a9-288">以 JSON 字串的形式接收回應。</span><span class="sxs-lookup"><span data-stu-id="be3a9-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="be3a9-289">還原序列化回應, 並將產生的**預測**傳遞至**SceneOrganiser**類別, 這會負責顯示回應的方式。</span><span class="sxs-lookup"><span data-stu-id="be3a9-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="be3a9-290">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="be3a9-290">To create this class:</span></span>

1.  <span data-ttu-id="be3a9-291">以滑鼠右鍵按一下 [**資產] 資料夾**(位於 [**專案] 面板**中), 然後按一下 [**建立** > **資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="be3a9-292">呼叫資料夾**腳本**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="be3a9-293">按兩下新建立的資料夾, 將它開啟。</span><span class="sxs-lookup"><span data-stu-id="be3a9-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="be3a9-294">在資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="be3a9-295">將腳本命名為**CustomVisionAnalyser。**</span><span class="sxs-lookup"><span data-stu-id="be3a9-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="be3a9-296">按兩下新的**CustomVisionAnalyser**腳本, 以 Visual Studio 開啟它 **。**</span><span class="sxs-lookup"><span data-stu-id="be3a9-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="be3a9-297">請確定您在檔案頂端參考了下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="be3a9-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="be3a9-298">在**CustomVisionAnalyser**類別中, 新增下列變數:</span><span class="sxs-lookup"><span data-stu-id="be3a9-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

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
    > <span data-ttu-id="be3a9-299">請務必將您的**服務預測金鑰**插入至**predictionKey**變數, 並將**預測端點**插入**predictionEndpoint**變數中。</span><span class="sxs-lookup"><span data-stu-id="be3a9-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="be3a9-300">您稍[早在步驟14的第2章中](#chapter-2---training-your-custom-vision-project)將這些複製到「記事本」。</span><span class="sxs-lookup"><span data-stu-id="be3a9-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="be3a9-301">現在必須加入**喚醒 ()** 的程式碼, 以初始化執行個體變數:</span><span class="sxs-lookup"><span data-stu-id="be3a9-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="be3a9-302">新增協同程式 (使用其底下的靜態**GetImageAsByteArray ()** 方法), 它會取得由**ImageCapture**類別所捕獲的影像分析結果。</span><span class="sxs-lookup"><span data-stu-id="be3a9-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="be3a9-303">在**AnalyseImageCapture**協同程式中, 會呼叫您尚未建立的**SceneOrganiser**類別。</span><span class="sxs-lookup"><span data-stu-id="be3a9-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="be3a9-304">因此, 請**將這些行暫時**加上批註。</span><span class="sxs-lookup"><span data-stu-id="be3a9-304">Therefore, **leave those lines commented for now**.</span></span>

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

9. <span data-ttu-id="be3a9-305">刪除**Start ()** 和**Update ()** 方法, 因為它們將不會使用。</span><span class="sxs-lookup"><span data-stu-id="be3a9-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="be3a9-306">請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be3a9-307">如先前所述, 請不要擔心可能出現錯誤的程式碼, 因為您很快就會提供進一步的類別, 這將會修正這些問題。</span><span class="sxs-lookup"><span data-stu-id="be3a9-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="be3a9-308">第6章-建立 CustomVisionObjects 類別</span><span class="sxs-lookup"><span data-stu-id="be3a9-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="be3a9-309">現在您將建立的類別是**CustomVisionObjects**類別。</span><span class="sxs-lookup"><span data-stu-id="be3a9-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="be3a9-310">此腳本包含許多物件, 可供其他類別用來序列化和還原序列化對自訂視覺服務所做的呼叫。</span><span class="sxs-lookup"><span data-stu-id="be3a9-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="be3a9-311">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="be3a9-311">To create this class:</span></span>

1.  <span data-ttu-id="be3a9-312">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="be3a9-313">呼叫腳本**CustomVisionObjects。**</span><span class="sxs-lookup"><span data-stu-id="be3a9-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="be3a9-314">按兩下新的**CustomVisionObjects**腳本, 以 Visual Studio 開啟它 **。**</span><span class="sxs-lookup"><span data-stu-id="be3a9-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="be3a9-315">請確定您在檔案頂端參考了下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="be3a9-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="be3a9-316">刪除**CustomVisionObjects**類別內的**Start ()** 和**Update ()** 方法, 這個類別現在應該是空的。</span><span class="sxs-lookup"><span data-stu-id="be3a9-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="be3a9-317">請務必仔細遵循下一個指示。</span><span class="sxs-lookup"><span data-stu-id="be3a9-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="be3a9-318">如果您將新的類別宣告放在**CustomVisionObjects**類別中, 您會在第[10 章](#chapter-10---create-the-imagecapture-class)取得編譯錯誤, 指出找不到**AnalysisRootObject**和**BoundingBox** 。</span><span class="sxs-lookup"><span data-stu-id="be3a9-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="be3a9-319">將下列類別新增至**CustomVisionObjects**類別*之外*。</span><span class="sxs-lookup"><span data-stu-id="be3a9-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="be3a9-320">**Newtonsoft**程式庫會使用這些物件來序列化和還原序列化回應資料:</span><span class="sxs-lookup"><span data-stu-id="be3a9-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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

6.  <span data-ttu-id="be3a9-321">請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="be3a9-322">第7章-建立 SpatialMapping 類別</span><span class="sxs-lookup"><span data-stu-id="be3a9-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="be3a9-323">這個類別會在場景中設定**空間對應碰撞**, 讓能夠偵測虛擬物件與實際物件之間的衝突。</span><span class="sxs-lookup"><span data-stu-id="be3a9-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="be3a9-324">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="be3a9-324">To create this class:</span></span>

1.  <span data-ttu-id="be3a9-325">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="be3a9-326">呼叫腳本**SpatialMapping。**</span><span class="sxs-lookup"><span data-stu-id="be3a9-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="be3a9-327">按兩下新的**SpatialMapping**腳本, 以 Visual Studio 開啟它 **。**</span><span class="sxs-lookup"><span data-stu-id="be3a9-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="be3a9-328">請確定您已在**SpatialMapping**類別上方參考下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="be3a9-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="be3a9-329">然後, 在**SpatialMapping**類別內的**Start ()** 方法上方, 新增下列變數:</span><span class="sxs-lookup"><span data-stu-id="be3a9-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="be3a9-330">新增**喚醒 ()** 和**Start ()** :</span><span class="sxs-lookup"><span data-stu-id="be3a9-330">Add the **Awake()** and **Start()**:</span></span>

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

6.  <span data-ttu-id="be3a9-331">刪除**Update ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="be3a9-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="be3a9-332">請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="be3a9-333">第8章-建立 GazeCursor 類別</span><span class="sxs-lookup"><span data-stu-id="be3a9-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="be3a9-334">這個類別會負責使用上一章所建立的**SpatialMappingCollider**, 在實際空間中設定正確位置的資料指標。</span><span class="sxs-lookup"><span data-stu-id="be3a9-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="be3a9-335">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="be3a9-335">To create this class:</span></span>

1.  <span data-ttu-id="be3a9-336">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="be3a9-337">呼叫腳本**GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="be3a9-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="be3a9-338">按兩下新的**GazeCursor**腳本, 以 Visual Studio 開啟它 **。**</span><span class="sxs-lookup"><span data-stu-id="be3a9-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="be3a9-339">請確定您已在**GazeCursor**類別上方參考下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="be3a9-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="be3a9-340">然後, 在**GazeCursor**類別內的**Start ()** 方法上方加入下列變數。</span><span class="sxs-lookup"><span data-stu-id="be3a9-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="be3a9-341">使用下列程式碼更新**Start ()** 方法:</span><span class="sxs-lookup"><span data-stu-id="be3a9-341">Update the **Start()** method with the following code:</span></span>

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

6.  <span data-ttu-id="be3a9-342">使用下列程式碼更新**update ()** 方法:</span><span class="sxs-lookup"><span data-stu-id="be3a9-342">Update the **Update()** method with the following code:</span></span>

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
    > <span data-ttu-id="be3a9-343">請不要擔心找不到**SceneOrganiser**類別的錯誤, 您將在下一章中建立它。</span><span class="sxs-lookup"><span data-stu-id="be3a9-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="be3a9-344">請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="be3a9-345">第9章-建立 SceneOrganiser 類別</span><span class="sxs-lookup"><span data-stu-id="be3a9-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="be3a9-346">此類別將會:</span><span class="sxs-lookup"><span data-stu-id="be3a9-346">This class will:</span></span>

-   <span data-ttu-id="be3a9-347">藉由附加適當的元件來設定*主要攝影機*。</span><span class="sxs-lookup"><span data-stu-id="be3a9-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="be3a9-348">當偵測到物件時, 它會負責計算其在真實世界中的位置, 並將**標記標籤**放在其附近, 並加上適當的**標記名稱**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="be3a9-349">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="be3a9-349">To create this class:</span></span>

1.  <span data-ttu-id="be3a9-350">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="be3a9-351">將腳本命名為**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="be3a9-352">按兩下新的**SceneOrganiser**腳本, 以 Visual Studio 開啟它 **。**</span><span class="sxs-lookup"><span data-stu-id="be3a9-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="be3a9-353">請確定您已在**SceneOrganiser**類別上方參考下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="be3a9-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="be3a9-354">然後, 在**SceneOrganiser**類別內的**Start ()** 方法上方新增下列變數:</span><span class="sxs-lookup"><span data-stu-id="be3a9-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="be3a9-355">刪除**Start ()** 和**Update ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="be3a9-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="be3a9-356">在變數底下, 新增**喚醒 ()** 方法, 這會初始化類別並設定場景。</span><span class="sxs-lookup"><span data-stu-id="be3a9-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="be3a9-357">新增**PlaceAnalysisLabel ()** 方法, 它會將場景中的標籤具現*化*(此時使用者不會看到此點)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="be3a9-358">它也會放入影像所在的四個 (也不可見), 並與真實世界重迭。</span><span class="sxs-lookup"><span data-stu-id="be3a9-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="be3a9-359">這很重要, 因為在分析之後, 從服務中取出的方塊座標會重新追蹤到這個四個, 判斷物件在真實世界中的大約位置。</span><span class="sxs-lookup"><span data-stu-id="be3a9-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

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

8.  <span data-ttu-id="be3a9-360">新增**FinaliseLabel ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="be3a9-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="be3a9-361">它負責:</span><span class="sxs-lookup"><span data-stu-id="be3a9-361">It is responsible for:</span></span>

    *   <span data-ttu-id="be3a9-362">使用具有最高信賴度的預測*標記*來設定*標籤*文字。</span><span class="sxs-lookup"><span data-stu-id="be3a9-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="be3a9-363">在四個物件上呼叫周*框*方塊的計算, 其位於先前的位置, 並將標籤放置在場景中。</span><span class="sxs-lookup"><span data-stu-id="be3a9-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="be3a9-364">針對周*框*方塊使用 Raycast 來調整標籤深度, 這應該會與真實世界中的物件發生衝突。</span><span class="sxs-lookup"><span data-stu-id="be3a9-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="be3a9-365">重設 capture 進程, 讓使用者能夠捕獲另一個映射。</span><span class="sxs-lookup"><span data-stu-id="be3a9-365">Resetting the capture process to allow the user to capture another image.</span></span>

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

9.  <span data-ttu-id="be3a9-366">加入**CalculateBoundingBoxPosition ()** 方法, 它會裝載一些必要的計算, 以轉譯從服務中取出的周*框*方塊座標, 並在四個按比例重新建立它們。</span><span class="sxs-lookup"><span data-stu-id="be3a9-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

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

10. <span data-ttu-id="be3a9-367">請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="be3a9-368">在繼續之前, 請開啟**CustomVisionAnalyser**類別, 然後在**AnalyseLastImageCaptured ()** 方法內,*取消*批註下列幾行:</span><span class="sxs-lookup"><span data-stu-id="be3a9-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
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
> <span data-ttu-id="be3a9-369">不擔心**ImageCapture**類別「找不到」訊息, 您將在下一章中建立它。</span><span class="sxs-lookup"><span data-stu-id="be3a9-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="be3a9-370">第10章-建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="be3a9-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="be3a9-371">下一個您即將建立的類別是**ImageCapture**類別。</span><span class="sxs-lookup"><span data-stu-id="be3a9-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="be3a9-372">此類別負責:</span><span class="sxs-lookup"><span data-stu-id="be3a9-372">This class is responsible for:</span></span>

*   <span data-ttu-id="be3a9-373">使用 HoloLens 攝影機來捕獲影像, 並將其儲存在*應用程式*資料夾中。</span><span class="sxs-lookup"><span data-stu-id="be3a9-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="be3a9-374">處理使用者的*點擊*手勢。</span><span class="sxs-lookup"><span data-stu-id="be3a9-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="be3a9-375">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="be3a9-375">To create this class:</span></span>

1.  <span data-ttu-id="be3a9-376">移至您先前建立的**腳本**資料夾。</span><span class="sxs-lookup"><span data-stu-id="be3a9-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="be3a9-377">在資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="be3a9-378">將腳本命名為**ImageCapture**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="be3a9-379">按兩下新的**ImageCapture**腳本, 以 Visual Studio 開啟它 **。**</span><span class="sxs-lookup"><span data-stu-id="be3a9-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="be3a9-380">將檔案頂端的命名空間取代為下列內容:</span><span class="sxs-lookup"><span data-stu-id="be3a9-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="be3a9-381">然後, 在**ImageCapture**類別內的**Start ()** 方法上方新增下列變數:</span><span class="sxs-lookup"><span data-stu-id="be3a9-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="be3a9-382">現在必須加入**喚醒 ()** 和**Start ()** 方法的程式碼:</span><span class="sxs-lookup"><span data-stu-id="be3a9-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="be3a9-383">執行會在點碰手勢發生時呼叫的處理常式:</span><span class="sxs-lookup"><span data-stu-id="be3a9-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

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
    > <span data-ttu-id="be3a9-384">當游標呈**綠色**時, 表示相機可以取得影像。</span><span class="sxs-lookup"><span data-stu-id="be3a9-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="be3a9-385">當游標為**紅色**時, 表示相機忙碌中。</span><span class="sxs-lookup"><span data-stu-id="be3a9-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="be3a9-386">新增應用程式用來啟動映射捕獲進程並儲存映射的方法:</span><span class="sxs-lookup"><span data-stu-id="be3a9-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

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

9.  <span data-ttu-id="be3a9-387">新增將在拍攝相片時呼叫的處理常式, 以及準備進行分析的時間。</span><span class="sxs-lookup"><span data-stu-id="be3a9-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="be3a9-388">然後, 結果會傳遞至**CustomVisionAnalyser**進行分析。</span><span class="sxs-lookup"><span data-stu-id="be3a9-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

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

10. <span data-ttu-id="be3a9-389">請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="be3a9-390">第11章-在場景中設定腳本</span><span class="sxs-lookup"><span data-stu-id="be3a9-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="be3a9-391">既然您已撰寫此專案所需的所有程式碼, 就可以開始設定場景中的腳本, 以及在 prefabs 上, 讓它們正常運作。</span><span class="sxs-lookup"><span data-stu-id="be3a9-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="be3a9-392">在**Unity 編輯器**中的 [階層]**面板**中, 選取**主攝影機**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="be3a9-393">在 [偵測**器] 面板**中, 選取**主相機**後, 按一下 [**新增元件**], 然後搜尋 [ **SceneOrganiser**腳本], 再按兩下, 將其加入。</span><span class="sxs-lookup"><span data-stu-id="be3a9-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="be3a9-394">在 [**專案] 面板**中, 開啟 [ **Prefabs] 資料夾**, 將**標籤**prefab 拖曳至您剛才新增到*主要相機*的**SceneOrganiser**腳本中的*標籤*空白參照目標輸入區域, 如下所示:下圖:</span><span class="sxs-lookup"><span data-stu-id="be3a9-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="be3a9-395">在 [階層]**面板**中, 選取**主要攝影機**的 [ **GazeCursor** ] 子系。</span><span class="sxs-lookup"><span data-stu-id="be3a9-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="be3a9-396">在 [偵測**器] 面板**中, 選取 [ **GazeCursor** ], 按一下 [**新增元件**], 然後搜尋 [ **GazeCursor**腳本], 再按兩下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="be3a9-397">同樣地, 在 [階層]**面板**中, 選取**主要攝影機**的**SpatialMapping**子系。</span><span class="sxs-lookup"><span data-stu-id="be3a9-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="be3a9-398">在 [偵測**器] 面板**中, 選取 [ **SpatialMapping** ], 按一下 [**新增元件**], 然後搜尋 [ **SpatialMapping**腳本], 再按兩下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="be3a9-399">您未設定的其餘腳本, 將會由**SceneOrganiser**腳本中的程式碼在執行時間中新增。</span><span class="sxs-lookup"><span data-stu-id="be3a9-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="be3a9-400">第12章-建立前</span><span class="sxs-lookup"><span data-stu-id="be3a9-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="be3a9-401">若要執行應用程式的徹底測試, 您必須將它側載到您的 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="be3a9-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="be3a9-402">在您執行之前, 請確定:</span><span class="sxs-lookup"><span data-stu-id="be3a9-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="be3a9-403">[第3章](#chapter-3---set-up-the-unity-project)所述的所有設定都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="be3a9-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="be3a9-404">腳本**SceneOrganiser**會附加到**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="be3a9-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="be3a9-405">腳本**GazeCursor**會附加至**GazeCursor**物件。</span><span class="sxs-lookup"><span data-stu-id="be3a9-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="be3a9-406">腳本**SpatialMapping**會附加至**SpatialMapping**物件。</span><span class="sxs-lookup"><span data-stu-id="be3a9-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="be3a9-407">在第[5 章](#chapter-5---create-the-customvisionanalyser-class), 步驟 6:</span><span class="sxs-lookup"><span data-stu-id="be3a9-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="be3a9-408">請務必將您的**服務預測金鑰**插入**predictionKey**變數中。</span><span class="sxs-lookup"><span data-stu-id="be3a9-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="be3a9-409">您已將**預測端點**插入至**predictionEndpoint**類別。</span><span class="sxs-lookup"><span data-stu-id="be3a9-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="be3a9-410">第13章-建立 UWP 解決方案並側載您的應用程式</span><span class="sxs-lookup"><span data-stu-id="be3a9-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="be3a9-411">您現在已準備好將應用程式建立為 UWP 解決方案, 讓您能夠將其部署至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="be3a9-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="be3a9-412">若要開始建立程式:</span><span class="sxs-lookup"><span data-stu-id="be3a9-412">To begin the build process:</span></span>

1.  <span data-ttu-id="be3a9-413">移至 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="be3a9-414">Tick **Unity C\#專案**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="be3a9-415">按一下 [**新增開啟的場景**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="be3a9-416">這會將目前開啟的場景新增至組建。</span><span class="sxs-lookup"><span data-stu-id="be3a9-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="be3a9-417">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="be3a9-417">Click **Build**.</span></span> <span data-ttu-id="be3a9-418">Unity 將會啟動 [檔案*瀏覽器*] 視窗, 您必須在其中建立並選取要建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="be3a9-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="be3a9-419">立即建立該資料夾, 並將它命名為**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="be3a9-420">然後選取 [**應用程式**] 資料夾, 按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="be3a9-421">Unity 會開始將您的專案建立至**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="be3a9-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="be3a9-422">Unity 完成建立之後 (可能需要一些時間), 它會在組建的位置開啟 [檔案**瀏覽器**] 視窗 (請檢查您的工作列, 因為它不一定會出現在視窗的上方, 但會通知您加入新的視窗)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="be3a9-423">若要部署至 Microsoft HoloLens, 您將需要該裝置的 IP 位址 (用於遠端部署), 並確保它也已設定**開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="be3a9-424">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="be3a9-424">To do this:</span></span>

    1.  <span data-ttu-id="be3a9-425">在戴 HoloLens 的同時, 請開啟**設定**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="be3a9-426">前往**Network & Internet**  >  **wi-fi**  >  **Advanced Options**</span><span class="sxs-lookup"><span data-stu-id="be3a9-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="be3a9-427">記下**IPv4**位址。</span><span class="sxs-lookup"><span data-stu-id="be3a9-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="be3a9-428">接下來, 流覽回到 [**設定**], 然後為**開發人員** **更新 & 安全性** > </span><span class="sxs-lookup"><span data-stu-id="be3a9-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="be3a9-429">設定**開發人員模式** *上*。</span><span class="sxs-lookup"><span data-stu-id="be3a9-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="be3a9-430">流覽至新的 Unity 組建 (**應用程式**資料夾), 然後使用**Visual Studio**開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="be3a9-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="be3a9-431">在 [解決方案設定] 中, 選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="be3a9-432">在解決方案平臺中, 選取 [ **x86]、[遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="be3a9-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="be3a9-433">系統會提示您插入遠端裝置的**IP 位址**(在此案例中, 這是您記下的 Microsoft HoloLens)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="be3a9-434">移至 [**建立**] 功能表, 然後按一下 [**部署方案**], 將應用程式側載至您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="be3a9-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="be3a9-435">您的應用程式現在應該會出現在 Microsoft HoloLens 上已安裝的應用程式清單中, 好讓您可以啟動!</span><span class="sxs-lookup"><span data-stu-id="be3a9-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="be3a9-436">若要使用應用程式:</span><span class="sxs-lookup"><span data-stu-id="be3a9-436">To use the application:</span></span>

* <span data-ttu-id="be3a9-437">查看物件, 您已使用**Azure 自訂視覺服務、物件偵測**來進行定型, 並使用點按**手勢**。</span><span class="sxs-lookup"><span data-stu-id="be3a9-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="be3a9-438">如果成功偵測到物件, 就會出現具有標記名稱的世界空間*標籤文字*。</span><span class="sxs-lookup"><span data-stu-id="be3a9-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be3a9-439">每次您捕捉相片並將它傳送至服務時, 您可以返回 [服務] 頁面, 並以新建立的映射重新定型服務。</span><span class="sxs-lookup"><span data-stu-id="be3a9-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="be3a9-440">一開始, 您可能也必須更正周*框方塊*, 使其更正確, 並重新定型服務。</span><span class="sxs-lookup"><span data-stu-id="be3a9-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="be3a9-441">當 Microsoft HoloLens 感應器和/或 Unity 中的 SpatialTrackingComponent 無法放置適當的 colliders (相對於真實世界物件) 時, 放置的標籤文字可能不會出現在物件附近。</span><span class="sxs-lookup"><span data-stu-id="be3a9-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="be3a9-442">如果是這種情況, 請嘗試在不同的表面上使用應用程式。</span><span class="sxs-lookup"><span data-stu-id="be3a9-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="be3a9-443">您的自訂視覺, 物件偵測應用程式</span><span class="sxs-lookup"><span data-stu-id="be3a9-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="be3a9-444">恭喜您, 您建立了一個混合現實應用程式, 利用 Azure 自訂視覺的物件偵測 API, 它可以辨識影像中的物件, 然後在3D 空間中提供該物件的近似位置。</span><span class="sxs-lookup"><span data-stu-id="be3a9-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="be3a9-445">額外練習</span><span class="sxs-lookup"><span data-stu-id="be3a9-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="be3a9-446">練習1</span><span class="sxs-lookup"><span data-stu-id="be3a9-446">Exercise 1</span></span>

<span data-ttu-id="be3a9-447">將加入至文字標籤時, 請使用半透明的 cube, 將實際物件包裝在3D 周*框*方塊中。</span><span class="sxs-lookup"><span data-stu-id="be3a9-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="be3a9-448">練習2</span><span class="sxs-lookup"><span data-stu-id="be3a9-448">Exercise 2</span></span>

<span data-ttu-id="be3a9-449">訓練您的自訂視覺服務, 以辨識更多物件。</span><span class="sxs-lookup"><span data-stu-id="be3a9-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="be3a9-450">練習3</span><span class="sxs-lookup"><span data-stu-id="be3a9-450">Exercise 3</span></span>

<span data-ttu-id="be3a9-451">在辨識物件時播放音效。</span><span class="sxs-lookup"><span data-stu-id="be3a9-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="be3a9-452">練習4</span><span class="sxs-lookup"><span data-stu-id="be3a9-452">Exercise 4</span></span>

<span data-ttu-id="be3a9-453">使用 API, 以應用程式所分析的相同影像重新訓練您的服務, 以便讓服務更精確 (同時進行預測和定型)。</span><span class="sxs-lookup"><span data-stu-id="be3a9-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
