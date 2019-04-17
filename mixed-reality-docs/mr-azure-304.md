---
title: MR 和 Azure 304-臉部辨識
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境，academy、 unity、 教學課程中，api，臉部辨識、 hololens、 沉浸式 vr
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596464"
---
>[!NOTE]
><span data-ttu-id="db0bd-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="db0bd-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="db0bd-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="db0bd-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="db0bd-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="db0bd-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="db0bd-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="db0bd-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="db0bd-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="db0bd-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="db0bd-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="db0bd-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="db0bd-110">MR 和 Azure 304:臉部辨識</span><span class="sxs-lookup"><span data-stu-id="db0bd-110">MR and Azure 304: Face recognition</span></span>

![完成本課程的結果](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="db0bd-112">在本課程中您會了解如何將臉部辨識功能加入至混合的實境應用程式中，使用 Azure 認知服務，Microsoft 臉部 api。</span><span class="sxs-lookup"><span data-stu-id="db0bd-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="db0bd-113">*Azure 的人臉識別 API*是 Microsoft 服務，開發人員提供最先進的臉部演算法，全都在雲端。</span><span class="sxs-lookup"><span data-stu-id="db0bd-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="db0bd-114">*人臉識別 API*有兩個主要功能： 臉部屬性，以偵測和臉部辨識。</span><span class="sxs-lookup"><span data-stu-id="db0bd-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="db0bd-115">這可讓開發人員只要設定一組群組的表面，並接著，將傳送查詢映像服務更新版本中，以判斷其表面的所屬。</span><span class="sxs-lookup"><span data-stu-id="db0bd-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="db0bd-116">如需詳細資訊，請瀏覽[Azure 臉部辨識頁面](https://azure.microsoft.com/services/cognitive-services/face/)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="db0bd-117">完成本課程之後，您會有混合的實境 HoloLens 應用程式，可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="db0bd-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="db0bd-118">使用**點選手勢**起始擷取的映像使用內建的 HoloLens 相機。</span><span class="sxs-lookup"><span data-stu-id="db0bd-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="db0bd-119">傳送至擷取的映像*Azure 人臉識別 API*服務。</span><span class="sxs-lookup"><span data-stu-id="db0bd-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="db0bd-120">接收的結果*人臉識別 API*演算法。</span><span class="sxs-lookup"><span data-stu-id="db0bd-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="db0bd-121">使用簡單的使用者介面，以顯示相符的人員名稱。</span><span class="sxs-lookup"><span data-stu-id="db0bd-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="db0bd-122">這將教導您如何將結果從臉部 API 服務進入您的 Unity 為基礎的混合的實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="db0bd-123">在您的應用程式，則您對於如何將整合結果進行設計。</span><span class="sxs-lookup"><span data-stu-id="db0bd-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="db0bd-124">本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="db0bd-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="db0bd-125">它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。</span><span class="sxs-lookup"><span data-stu-id="db0bd-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="db0bd-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="db0bd-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="db0bd-127">課程</span><span class="sxs-lookup"><span data-stu-id="db0bd-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="db0bd-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="db0bd-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="db0bd-129"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="db0bd-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="db0bd-130">MR 和 Azure 304:臉部辨識</span><span class="sxs-lookup"><span data-stu-id="db0bd-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="db0bd-131">✔️</span><span class="sxs-lookup"><span data-stu-id="db0bd-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="db0bd-132">✔️</span><span class="sxs-lookup"><span data-stu-id="db0bd-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="db0bd-133">雖然這堂課程主要著重於 HoloLens，您也可以套用您在此課程 Windows Mixed Reality 沈浸式 (VR) 耳機來了解。</span><span class="sxs-lookup"><span data-stu-id="db0bd-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="db0bd-134">因為沈浸式 (VR) 耳機並沒有可存取的相機，您必須連線到您的 PC 外部相機。</span><span class="sxs-lookup"><span data-stu-id="db0bd-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="db0bd-135">當您遵循本課程中，您會看到 備忘稿上用來支援沈浸式 (VR) 耳機時，您可能需要的任何變更。</span><span class="sxs-lookup"><span data-stu-id="db0bd-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="db0bd-136">先決條件</span><span class="sxs-lookup"><span data-stu-id="db0bd-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="db0bd-137">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="db0bd-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="db0bd-138">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="db0bd-139">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊會完全符合您會發現在較新的軟體與以下所列內容.</span><span class="sxs-lookup"><span data-stu-id="db0bd-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="db0bd-140">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="db0bd-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="db0bd-141">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="db0bd-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="db0bd-142">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="db0bd-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="db0bd-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="db0bd-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="db0bd-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="db0bd-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="db0bd-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="db0bd-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="db0bd-146">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="db0bd-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="db0bd-147">相機連接到您的電腦 （開發沈浸式耳機）</span><span class="sxs-lookup"><span data-stu-id="db0bd-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="db0bd-148">Azure 設定和人臉識別 API 擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="db0bd-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="db0bd-149">開始之前</span><span class="sxs-lookup"><span data-stu-id="db0bd-149">Before you start</span></span>

1.  <span data-ttu-id="db0bd-150">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="db0bd-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="db0bd-151">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="db0bd-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="db0bd-152">如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="db0bd-153">它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。</span><span class="sxs-lookup"><span data-stu-id="db0bd-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="db0bd-154">校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="db0bd-155">如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="db0bd-156">第 1 章-Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="db0bd-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="db0bd-157">若要使用*人臉識別 API*服務在 Azure 中，您必須設定您的應用程式提供服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="db0bd-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="db0bd-158">首先，登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="db0bd-159">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="db0bd-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="db0bd-160">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="db0bd-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="db0bd-161">一旦您登入，按一下**新增**在左上角，，然後搜尋*人臉識別 API*、 按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![搜尋臉部 api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="db0bd-163">單字**的新**可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="db0bd-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="db0bd-164">新的頁面將提供的描述*人臉識別 API*服務。</span><span class="sxs-lookup"><span data-stu-id="db0bd-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="db0bd-165">在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="db0bd-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![臉部 api 資訊](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="db0bd-167">一旦您按下**建立**:</span><span class="sxs-lookup"><span data-stu-id="db0bd-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="db0bd-168">插入您想要的名稱，此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="db0bd-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="db0bd-169">選取訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="db0bd-169">Select a subscription.</span></span>

    3. <span data-ttu-id="db0bd-170">選取定價層適合您，如果這是第一次建立*臉部 API 服務*，免費層 （名為 F0） 應該是您可以使用。</span><span class="sxs-lookup"><span data-stu-id="db0bd-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="db0bd-171">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="db0bd-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="db0bd-172">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="db0bd-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="db0bd-173">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="db0bd-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="db0bd-174">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="db0bd-175">UWP 應用程式**人員 Maker**，供您更新版本中，需要使用 「 美國西部 」 位置。</span><span class="sxs-lookup"><span data-stu-id="db0bd-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="db0bd-176">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="db0bd-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="db0bd-177">選取\**建立 *。**</span><span class="sxs-lookup"><span data-stu-id="db0bd-177">Select **Create\*.**</span></span>

        ![建立臉部 api 服務](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="db0bd-179">一旦您按下\*\*建立 \*\*\* 您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="db0bd-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="db0bd-180">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="db0bd-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![服務建立通知](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="db0bd-182">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="db0bd-182">Click on the notifications to explore your new Service instance.</span></span>

    ![請移至資源通知](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="db0bd-184">當您準備好時，按一下**移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="db0bd-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![存取臉部 api 金鑰](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="db0bd-186">在本教學課程中，您的應用程式必須對您的服務，透過使用您的服務訂用帳戶 'key' 進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="db0bd-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="db0bd-187">從*快速入門*頁面上的您*人臉識別 API*服務，第一個點是數字 1，為*取得您的金鑰。*</span><span class="sxs-lookup"><span data-stu-id="db0bd-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="db0bd-188">在上*服務*頁面上，選取任一個藍色**金鑰**超連結 （如果在快速入門 頁面上），或**金鑰**服務瀏覽功能表中的連結 (左邊，以表示 '索引鍵 ' 圖示)，以顯示您的金鑰。</span><span class="sxs-lookup"><span data-stu-id="db0bd-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="db0bd-189">請記下的其中一個索引鍵，並保護它，因為您稍後需要它。</span><span class="sxs-lookup"><span data-stu-id="db0bd-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="db0bd-190">第 2 章-使用 ' 人員 Maker' UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="db0bd-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="db0bd-191">請務必下載預先建置的 UWP 應用程式呼叫[人員 Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="db0bd-192">此應用程式不是最終產品，如本課程中，只可協助您建立 Azure 項目，其更新版本的專案將會依賴工具。</span><span class="sxs-lookup"><span data-stu-id="db0bd-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="db0bd-193">**人員 Maker**可讓您建立 Azure 的項目，也就是與人員和群組的人員相關聯。</span><span class="sxs-lookup"><span data-stu-id="db0bd-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="db0bd-194">應用程式會將所需的資訊，然後稍後可由 FaceAPI，辨別您新增的人們的臉部格式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="db0bd-195">[重要]**人員 Maker**會使用一些基本節流，協助確保不會超過每分鐘的服務呼叫數目**免費訂用帳戶層**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="db0bd-196">在頂端的綠色文字會變更為紅色，並進行節流; 時，更新為 「 作用中 」如果發生這種情況，只需等待應用程式 （它會等到它接下來可以繼續存取臉部服務，一次使用時，更新為 「 中-作用中 」）。</span><span class="sxs-lookup"><span data-stu-id="db0bd-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="db0bd-197">此應用程式會使用*Microsoft.ProjectOxford.Face*程式庫，可讓您能夠完整使用人臉識別 API。</span><span class="sxs-lookup"><span data-stu-id="db0bd-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="db0bd-198">此程式庫是以 NuGet 套件的形式免費提供。</span><span class="sxs-lookup"><span data-stu-id="db0bd-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="db0bd-199">如需詳細資訊，以及類似，Api[請務必瀏覽 API 參考文章](https://docs.microsoft.com/azure/cognitive-services/face/apireference)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="db0bd-200">這些是所需的步驟，說明如何達成上述目標，是進一步文件。</span><span class="sxs-lookup"><span data-stu-id="db0bd-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="db0bd-201">**人員 Maker**應用程式可讓您：</span><span class="sxs-lookup"><span data-stu-id="db0bd-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="db0bd-202">建立*人員群組*、 有哪些群組包含的數個您想要與它相關聯的人員。</span><span class="sxs-lookup"><span data-stu-id="db0bd-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="db0bd-203">使用您的 Azure 帳戶中，您可以裝載多個人員群組。</span><span class="sxs-lookup"><span data-stu-id="db0bd-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="db0bd-204">建立*人員*，這是使用者群組的成員。</span><span class="sxs-lookup"><span data-stu-id="db0bd-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="db0bd-205">每個人都有一些*臉部*與其相關聯的映像。</span><span class="sxs-lookup"><span data-stu-id="db0bd-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="db0bd-206">指派*面臨映像*來*人員*，以允許您的 Azure 臉部 API 服務，以辨識*人員*由相對應*臉部*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="db0bd-207">*定型*您*Azure 臉部 API 服務*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="db0bd-208">留意，因此若要定型此應用程式可以辨識的人員，您必須十 （10） 特寫相片的每個人，您想要新增到您的人員群組。</span><span class="sxs-lookup"><span data-stu-id="db0bd-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="db0bd-209">Windows 10 Cam 應用程式可協助您將這些。</span><span class="sxs-lookup"><span data-stu-id="db0bd-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="db0bd-210">您必須確定每張相片已清除 （避免模糊、 遮蔽，或正在牽扯太廣，從主體），在 jpg 或 png 檔案格式中的相片，正在不大的映像檔案大小**4MB**，並不小於**1KB**.</span><span class="sxs-lookup"><span data-stu-id="db0bd-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="db0bd-211">如果您要遵循本教學課程，請勿用於您自己的臉部訓練，當您將 HoloLens 時，您無法看您自己。</span><span class="sxs-lookup"><span data-stu-id="db0bd-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="db0bd-212">使用表面的同事或人員的學生。</span><span class="sxs-lookup"><span data-stu-id="db0bd-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="db0bd-213">執行**人員 Maker**:</span><span class="sxs-lookup"><span data-stu-id="db0bd-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="db0bd-214">開啟**PersonMaker**資料夾，然後按兩下*PersonMaker 解決方案*以開啟它*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="db0bd-215">一次*PersonMaker 解決方案*開啟，請確定：</span><span class="sxs-lookup"><span data-stu-id="db0bd-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="db0bd-216">*方案組態*設為**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="db0bd-217">*的方案平台*設定為**x86**</span><span class="sxs-lookup"><span data-stu-id="db0bd-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="db0bd-218">*目標平台*是**本機**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="db0bd-219">您也可能需要*還原 NuGet 套件*(以滑鼠右鍵按一下*解決方案*，然後選取**還原 NuGet 套件**)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="db0bd-220">按一下 *本機電腦*和應用程式會啟動。</span><span class="sxs-lookup"><span data-stu-id="db0bd-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="db0bd-221">請注意，在較小的螢幕上，所有內容可能都無法看見，但您可以進一步向下捲動一進行檢視。</span><span class="sxs-lookup"><span data-stu-id="db0bd-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![人員 maker 使用者介面](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="db0bd-223">插入您**Azure 驗證金鑰**，您應該有的從您*人臉識別 API*服務在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="db0bd-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="db0bd-224">插入：</span><span class="sxs-lookup"><span data-stu-id="db0bd-224">Insert:</span></span>

    1. <span data-ttu-id="db0bd-225">*識別碼*您想要指派給*人員群組*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="db0bd-226">識別碼必須是小寫、 不含空格。</span><span class="sxs-lookup"><span data-stu-id="db0bd-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="db0bd-227">為 Unity 專案中，稍後將需要它，請記下此識別碼。</span><span class="sxs-lookup"><span data-stu-id="db0bd-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="db0bd-228">*名稱*您想要指派給*人員群組*（可以有空格）。</span><span class="sxs-lookup"><span data-stu-id="db0bd-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="db0bd-229">按下**建立的人員群組** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="db0bd-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="db0bd-230">確認訊息應該會出現下方的按鈕。</span><span class="sxs-lookup"><span data-stu-id="db0bd-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="db0bd-231">如果您有 「 拒絕存取 」 錯誤，請檢查您要為您的 Azure 服務的位置。</span><span class="sxs-lookup"><span data-stu-id="db0bd-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="db0bd-232">如上所述，此應用程式被針對 「 美國西部 」。</span><span class="sxs-lookup"><span data-stu-id="db0bd-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db0bd-233">您會注意到，您也可以按一下**提取已知群組**按鈕： 這是為了使用，而不是建立一個新的群組，且想如果您已經建立的人員。</span><span class="sxs-lookup"><span data-stu-id="db0bd-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="db0bd-234">請注意，如果您按一下*建立使用者群組*與已知的群組，這也會擷取群組。</span><span class="sxs-lookup"><span data-stu-id="db0bd-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="db0bd-235">插入*名稱*的*人員*您想要建立。</span><span class="sxs-lookup"><span data-stu-id="db0bd-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="db0bd-236">按一下 [**建立人員**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="db0bd-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="db0bd-237">確認訊息應該會出現下方的按鈕。</span><span class="sxs-lookup"><span data-stu-id="db0bd-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="db0bd-238">如果您想要刪除個人您先前已經建立，您可以寫入文字方塊並按名稱**刪除的人員**</span><span class="sxs-lookup"><span data-stu-id="db0bd-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="db0bd-239">請確定您知道您想要新增到群組之人員的相片十 （10） 的位置。</span><span class="sxs-lookup"><span data-stu-id="db0bd-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="db0bd-240">按下**建立及開啟資料夾**的人員相關聯的資料夾中開啟 Windows 檔案總管。</span><span class="sxs-lookup"><span data-stu-id="db0bd-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="db0bd-241">新增十 （10） 映像的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="db0bd-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="db0bd-242">它們必須有*JPG*或是*PNG*檔案格式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="db0bd-243">按一下 **提交至 Azure**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="db0bd-244">計數器會顯示提交，後面的訊息，完成時的狀態。</span><span class="sxs-lookup"><span data-stu-id="db0bd-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="db0bd-245">計數器已完成，並在顯示確認訊息後按一下 **定型**來定型您的服務。</span><span class="sxs-lookup"><span data-stu-id="db0bd-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="db0bd-246">程序完成後，您已準備好移至 Unity。</span><span class="sxs-lookup"><span data-stu-id="db0bd-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="db0bd-247">第 3 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="db0bd-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="db0bd-248">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="db0bd-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="db0bd-249">開啟*Unity*然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-249">Open *Unity* and click **New**.</span></span> 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="db0bd-251">您現在必須提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="db0bd-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="db0bd-252">插入**MR_FaceRecognition**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="db0bd-253">請確定專案類型設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="db0bd-254">設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="db0bd-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="db0bd-255">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-255">Then, click **Create project**.</span></span>

    ![提供新的 Unity 專案的詳細資料。](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="db0bd-257">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="db0bd-258">移至**編輯 > 偏好**，然後在新視窗中，瀏覽**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="db0bd-259">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="db0bd-260">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="db0bd-260">Close the **Preferences** window.</span></span>

    ![更新指令碼編輯器喜好設定。](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="db0bd-262">接下來，移至**檔案 > 組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="db0bd-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![建置設定 視窗中，切換至 UWP 的平台。](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="db0bd-264">移至**檔案 > 組建設定**並確定：</span><span class="sxs-lookup"><span data-stu-id="db0bd-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="db0bd-265">**裝置為目標**設為**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="db0bd-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="db0bd-266">針對擬真耳機，設定**目標裝置**要*任何裝置*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="db0bd-267">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="db0bd-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="db0bd-268">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="db0bd-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="db0bd-269">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="db0bd-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="db0bd-270">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="db0bd-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="db0bd-271">儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="db0bd-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="db0bd-272">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="db0bd-273">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="db0bd-273">A save window will appear.</span></span>

            ![按一下 新增開啟場景按鈕](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="db0bd-275">選取 **新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的指令碼資料夾](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="db0bd-277">開啟您剛建立**場景**資料夾，然後在**檔名**： 文字欄位中輸入**FaceRecScene**，然後按**儲存**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![指定新的場景的名稱。](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="db0bd-279">剩餘的設定，*組建設定*，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="db0bd-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="db0bd-280">中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。</span><span class="sxs-lookup"><span data-stu-id="db0bd-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟播放程式設定。](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="db0bd-282">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="db0bd-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="db0bd-283">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="db0bd-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="db0bd-284">**指令碼\*\*\*\*執行階段版本**應該**實驗性**（.NET 4.6 對等）。</span><span class="sxs-lookup"><span data-stu-id="db0bd-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="db0bd-285">變更這將會觸發需要重新啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="db0bd-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="db0bd-286">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="db0bd-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="db0bd-287">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="db0bd-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="db0bd-289">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="db0bd-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="db0bd-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="db0bd-290">**InternetClient**</span></span>
        - <span data-ttu-id="db0bd-291">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="db0bd-291">**Webcam**</span></span>

            ![正在更新發行的設定。](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="db0bd-293">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。</span><span class="sxs-lookup"><span data-stu-id="db0bd-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 R 設定。](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="db0bd-295">回到*Build Settings*， **UnityC#專案**不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db0bd-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="db0bd-296">關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="db0bd-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="db0bd-297">儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="db0bd-298">第 4 章-Main Camera 安裝程式</span><span class="sxs-lookup"><span data-stu-id="db0bd-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db0bd-299">如果您想要跳過*Unity 設定*元件的課程，並直接在程式碼中繼續進行，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)，然後匯入您的專案做為[自訂封裝](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="db0bd-300">請注意，此套件也包含匯入*Newtonsoft DLL*、 在涵蓋[第 5 章](#chapter-5--import-the-newtonsoft.json-library)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoft.json-library).</span></span> <span data-ttu-id="db0bd-301">與這個匯入，您可以繼續從[第 6 章](#chapter-6-create-the-faceanalysis-class)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-301">With this imported, you can continue from [Chapter 6](#chapter-6-create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="db0bd-302">在 [*階層*] 面板中，選取**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="db0bd-303">選取之後，您將能夠看到所有的元件**Main Camera**中*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="db0bd-304">**相機物件**必須命名為**Main Camera** （請注意拼字 ！）</span><span class="sxs-lookup"><span data-stu-id="db0bd-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="db0bd-305">Main Camera**標記**必須設為**MainCamera** （請注意拼字 ！）</span><span class="sxs-lookup"><span data-stu-id="db0bd-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="db0bd-306">請確定**轉換的位置**設定為**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="db0bd-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="db0bd-307">設定**清除旗標**到**純色**</span><span class="sxs-lookup"><span data-stu-id="db0bd-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="db0bd-308">設定**背景**相機元件以色彩**黑色，0 的 Alpha (十六進位的程式碼: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="db0bd-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![設定觀景窗元件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="db0bd-310">第 5 章-匯入 Newtonsoft.Json 程式庫</span><span class="sxs-lookup"><span data-stu-id="db0bd-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db0bd-311">如果您匯入 '.unitypackage'[最後一章](#chapter-4--main-camera-setup)，您可以略過這一章。</span><span class="sxs-lookup"><span data-stu-id="db0bd-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4--main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="db0bd-312">若要可協助您還原序列化和序列化物件接收和傳送到 Bot 服務，您需要下載*Newtonsoft.Json*程式庫。</span><span class="sxs-lookup"><span data-stu-id="db0bd-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="db0bd-313">您會找到相容的版本已經使用正確的 Unity 資料夾結構，在此組織[Unity 封裝檔案](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="db0bd-314">若要匯入程式庫：</span><span class="sxs-lookup"><span data-stu-id="db0bd-314">To import the library:</span></span>

1.  <span data-ttu-id="db0bd-315">下載 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="db0bd-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="db0bd-316">按一下 **資產**，**匯入套件**，**自訂套件**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![匯入 Newtonsoft.Json 程式庫](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="db0bd-318">尋找您已下載，Unity 套件，並按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="db0bd-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="db0bd-319">請確定已勾選的封裝的所有元件，然後按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![匯入 Newtonsoft.Json 程式庫](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="db0bd-321">章節 6-建立 FaceAnalysis 類別</span><span class="sxs-lookup"><span data-stu-id="db0bd-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="db0bd-322">FaceAnalysis 類別的目的是要裝載與您的 Azure 臉部辨識服務進行通訊所需的方法。</span><span class="sxs-lookup"><span data-stu-id="db0bd-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="db0bd-323">在傳送服務擷取映像之後, 它會分析它和識別人臉內，並判斷是否任何屬於已知的個人。</span><span class="sxs-lookup"><span data-stu-id="db0bd-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="db0bd-324">如果找到已知的人員，則這個類別會顯示其名稱，作為在場景中的 UI 文字。</span><span class="sxs-lookup"><span data-stu-id="db0bd-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="db0bd-325">若要建立*FaceAnalysis*類別：</span><span class="sxs-lookup"><span data-stu-id="db0bd-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="db0bd-326">以滑鼠右鍵按一下*Assets 資料夾*位於 [專案] 面板，然後按一下**建立** > **資料夾**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="db0bd-327">呼叫資料夾**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-327">Call the folder **Scripts**.</span></span> 

    ![建立 FaceAnalysis 類別。](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="db0bd-329">按兩下剛才建立開啟的資料夾。</span><span class="sxs-lookup"><span data-stu-id="db0bd-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="db0bd-330">在資料夾中，以滑鼠右鍵按一下，然後按一下**Create**  >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="db0bd-331">呼叫指令碼*FaceAnalysis*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="db0bd-332">按兩下新*FaceAnalysis*指令碼，以使用 Visual Studio 2017 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="db0bd-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="db0bd-333">輸入下列的命名空間上述*FaceAnalysis*類別：</span><span class="sxs-lookup"><span data-stu-id="db0bd-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="db0bd-334">您現在需要新增所有用於 deserialising 的物件。</span><span class="sxs-lookup"><span data-stu-id="db0bd-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="db0bd-335">這些物件必須加入**外**的*FaceAnalysis* （下方下大括號中） 的指令碼。</span><span class="sxs-lookup"><span data-stu-id="db0bd-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="db0bd-336">*Start （)* 並*update （)* 方法不會使用，因此現在刪除它們。</span><span class="sxs-lookup"><span data-stu-id="db0bd-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="db0bd-337">內部*FaceAnalysis*類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="db0bd-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="db0bd-338">取代**金鑰**並**personGroupId**您的服務金鑰與您先前建立的群組識別碼。</span><span class="sxs-lookup"><span data-stu-id="db0bd-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="db0bd-339">新增*Awake()* 方法，initialises 類別，新增*ImageCapture* Main Camera 類別並呼叫標籤建立方法：</span><span class="sxs-lookup"><span data-stu-id="db0bd-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="db0bd-340">新增*CreateLabel()* 方法會建立*標籤*物件，以顯示分析結果：</span><span class="sxs-lookup"><span data-stu-id="db0bd-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="db0bd-341">新增*DetectFacesFromImage()* 並*GetImageAsByteArray()* 方法。</span><span class="sxs-lookup"><span data-stu-id="db0bd-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="db0bd-342">前者會要求已送出的映像，在偵測任何可能的臉部，而後者是為了將擷取的映像轉換成位元組陣列臉部辨識服務︰</span><span class="sxs-lookup"><span data-stu-id="db0bd-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="db0bd-343">新增*IdentifyFaces()* 方法，會要求*臉部辨識服務*來識別任何已知的臉部偵測到先前已送出的映像中。</span><span class="sxs-lookup"><span data-stu-id="db0bd-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="db0bd-344">要求會傳回識別碼所識別的人員，但不是名稱為：</span><span class="sxs-lookup"><span data-stu-id="db0bd-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="db0bd-345">新增*GetPerson()* 方法。</span><span class="sxs-lookup"><span data-stu-id="db0bd-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="db0bd-346">藉由提供者識別碼，此方法，然後要求*臉部辨識服務*来傳回的已識別的人員名稱：</span><span class="sxs-lookup"><span data-stu-id="db0bd-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="db0bd-347">請記得**儲存**之前返回至 Unity 編輯器中的變更。</span><span class="sxs-lookup"><span data-stu-id="db0bd-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="db0bd-348">在 Unity 編輯器中，從 專案 面板中的指令碼 資料夾拖曳 FaceAnalysis 指令碼中的 Main Camera 物件*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="db0bd-349">新的指令碼元件會因此新增到 Main Camera。</span><span class="sxs-lookup"><span data-stu-id="db0bd-349">The new script component will be so added to the Main Camera.</span></span> 

![將放置到主攝影機 FaceAnalysis](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="db0bd-351">第 7-建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="db0bd-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="db0bd-352">目的*ImageCapture*類別來裝載與通訊所需的方法是您*Azure 臉部辨識服務*分析的映像，您將會擷取時，用來識別在其中的臉部和判斷它是否屬於所知的人士。</span><span class="sxs-lookup"><span data-stu-id="db0bd-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="db0bd-353">如果找到已知的人員，則這個類別會顯示其名稱，作為在場景中的 UI 文字。</span><span class="sxs-lookup"><span data-stu-id="db0bd-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="db0bd-354">若要建立*ImageCapture*類別：</span><span class="sxs-lookup"><span data-stu-id="db0bd-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="db0bd-355">以滑鼠右鍵按一下**指令碼**資料夾，您先前已建立，然後按一下**建立**，  **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="db0bd-356">呼叫指令碼*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="db0bd-357">按兩下新*ImageCapture*指令碼，以使用 Visual Studio 2017 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="db0bd-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="db0bd-358">輸入上面 ImageCapture 類別的下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="db0bd-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="db0bd-359">內部*ImageCapture*類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="db0bd-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="db0bd-360">新增*Awake()* 並*start （)* 初始化類別，並允許以擷取使用者的筆勢 HoloLens 所需的方法：</span><span class="sxs-lookup"><span data-stu-id="db0bd-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="db0bd-361">新增*TapHandler()* 使用者執行時呼叫*點選*筆勢：</span><span class="sxs-lookup"><span data-stu-id="db0bd-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="db0bd-362">新增*ExecuteImageCaptureAndAnalysis()* 方法，就會開始的映像擷取程序：</span><span class="sxs-lookup"><span data-stu-id="db0bd-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="db0bd-363">新增相片擷取程序完成時，會呼叫處理常式：</span><span class="sxs-lookup"><span data-stu-id="db0bd-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="db0bd-364">請記得**儲存**之前返回至 Unity 編輯器中的變更。</span><span class="sxs-lookup"><span data-stu-id="db0bd-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="db0bd-365">第 8 章-建置方案</span><span class="sxs-lookup"><span data-stu-id="db0bd-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="db0bd-366">若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="db0bd-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="db0bd-367">這麼做之前，請確認：</span><span class="sxs-lookup"><span data-stu-id="db0bd-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="db0bd-368">第 3 章中所述的所有設定都正確都設定。</span><span class="sxs-lookup"><span data-stu-id="db0bd-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="db0bd-369">指令碼*FaceAnalysis*會附加至 Main Camera 物件。</span><span class="sxs-lookup"><span data-stu-id="db0bd-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="db0bd-370">這兩個**驗證金鑰**並**群組識別碼**都已設定內*FaceAnalysis*指令碼。</span><span class="sxs-lookup"><span data-stu-id="db0bd-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="db0bd-371">這提供您準備好要建置方案。</span><span class="sxs-lookup"><span data-stu-id="db0bd-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="db0bd-372">一旦已建置方案，您就可以部署您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="db0bd-373">若要開始建置程序：</span><span class="sxs-lookup"><span data-stu-id="db0bd-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="db0bd-374">按一下檔案，儲存，以儲存目前場景。</span><span class="sxs-lookup"><span data-stu-id="db0bd-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="db0bd-375">移至檔案，建置設定]，按一下 [加入開啟的場景。</span><span class="sxs-lookup"><span data-stu-id="db0bd-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="db0bd-376">請務必建立刻度 UnityC#專案。</span><span class="sxs-lookup"><span data-stu-id="db0bd-376">Make sure to tick Unity C# Projects.</span></span>

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="db0bd-378">按下建置。</span><span class="sxs-lookup"><span data-stu-id="db0bd-378">Press Build.</span></span> <span data-ttu-id="db0bd-379">在這種方式，Unity 會啟動 檔案總管 視窗中，您要建立，然後選取 建置到應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="db0bd-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="db0bd-380">現在，在 Unity 專案中，建立該資料夾，並呼叫應用程式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="db0bd-381">選取的應用程式資料夾，然後按選取資料夾。</span><span class="sxs-lookup"><span data-stu-id="db0bd-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="db0bd-382">Unity 會開始建置您的專案中，應用程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="db0bd-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="db0bd-383">一次 Unity 已完成 （可能需要一些時間） 的建置，它將會開啟檔案總管 視窗中，您的組建位置。</span><span class="sxs-lookup"><span data-stu-id="db0bd-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="db0bd-385">開啟您的應用程式的資料夾，然後再開啟新的專案方案 （如上所示，MR_FaceRecognition.sln）。</span><span class="sxs-lookup"><span data-stu-id="db0bd-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="db0bd-386">第 9 章-部署應用程式</span><span class="sxs-lookup"><span data-stu-id="db0bd-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="db0bd-387">若要部署 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="db0bd-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="db0bd-388">您將需要您 HoloLens IP 位址 （適用於遠端部署），並以確保您 HoloLens 處於**開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="db0bd-389">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="db0bd-389">To do this:</span></span>

    1. <span data-ttu-id="db0bd-390">儘管穿著您 HoloLens，開啟**設定**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="db0bd-391">移至**網路和網際網路 > Wi-fi > 進階選項**</span><span class="sxs-lookup"><span data-stu-id="db0bd-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="db0bd-392">附註**IPv4**位址。</span><span class="sxs-lookup"><span data-stu-id="db0bd-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="db0bd-393">接下來，瀏覽回到**設定**，然後**更新與安全性 > 適用於開發人員**</span><span class="sxs-lookup"><span data-stu-id="db0bd-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="db0bd-394">設定開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="db0bd-395">瀏覽至新的 Unity 組建 (*應用程式*資料夾)，並開啟方案檔*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="db0bd-396">在 方案組態選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="db0bd-397">在 方案平台上，選取**x86**，**遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="db0bd-399">移至**建置 功能表**，然後按一下**部署方案**，側載您 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="db0bd-400">您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="db0bd-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="db0bd-401">若要將部署到擬真耳機，設定**的方案平台**來*本機電腦*，並設定**組態**至*偵錯*，使用*x86*作為**平台**。</span><span class="sxs-lookup"><span data-stu-id="db0bd-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="db0bd-402">然後部署到本機電腦，使用**建置 功能表**，並選取*部署方案*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="db0bd-403">第 10 章-使用應用程式</span><span class="sxs-lookup"><span data-stu-id="db0bd-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="db0bd-404">頭戴 HoloLens，啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="db0bd-405">查看您已註冊的人員*人臉識別 API*。</span><span class="sxs-lookup"><span data-stu-id="db0bd-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="db0bd-406">請確認︰</span><span class="sxs-lookup"><span data-stu-id="db0bd-406">Make sure that:</span></span>

    -  <span data-ttu-id="db0bd-407">此人臉部不太遙遠，清楚地顯示</span><span class="sxs-lookup"><span data-stu-id="db0bd-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="db0bd-408">環境光源不太深</span><span class="sxs-lookup"><span data-stu-id="db0bd-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="db0bd-409">您可以使用點選手勢來擷取連絡人的圖片。</span><span class="sxs-lookup"><span data-stu-id="db0bd-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="db0bd-410">等候傳送分析要求和接收回應應用程式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="db0bd-411">如果已成功辨識的人員，該人員的名稱會顯示為 UI 文字中。</span><span class="sxs-lookup"><span data-stu-id="db0bd-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="db0bd-412">您可以重複使用點選手勢每隔幾秒鐘的擷取程序。</span><span class="sxs-lookup"><span data-stu-id="db0bd-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="db0bd-413">完成的 Azure 臉部 API 應用程式</span><span class="sxs-lookup"><span data-stu-id="db0bd-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="db0bd-414">恭喜，您可以建置利用 Azure 臉部辨識服務來偵測映像 」 中的臉部，並識別任何已知的人臉 mixed 的 reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![完成本課程的結果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="db0bd-416">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="db0bd-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="db0bd-417">練習 1</span><span class="sxs-lookup"><span data-stu-id="db0bd-417">Exercise 1</span></span>

<span data-ttu-id="db0bd-418">**Azure 人臉識別 API**強大，足以偵測單一映像中的最多 64 的臉孔。</span><span class="sxs-lookup"><span data-stu-id="db0bd-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="db0bd-419">擴充應用程式，使它無法辨識兩個或三個的表面，在很多人之間。</span><span class="sxs-lookup"><span data-stu-id="db0bd-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="db0bd-420">練習 2</span><span class="sxs-lookup"><span data-stu-id="db0bd-420">Exercise 2</span></span>

<span data-ttu-id="db0bd-421">**Azure 人臉識別 API**時，也可以提供回的所有類型的屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="db0bd-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="db0bd-422">將這整合到應用程式。</span><span class="sxs-lookup"><span data-stu-id="db0bd-422">Integrate this into the application.</span></span> <span data-ttu-id="db0bd-423">這可能是更有趣的是，結合[表情 API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)。</span><span class="sxs-lookup"><span data-stu-id="db0bd-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
