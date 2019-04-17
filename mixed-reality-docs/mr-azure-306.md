---
title: MR 和 Azure 306-串流處理視訊
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 媒體服務。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境，academy、 unity、 教學課程、 api，媒體服務，串流處理視訊，360、 沉浸式 vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591607"
---
>[!NOTE]
><span data-ttu-id="1050a-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="1050a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1050a-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="1050a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1050a-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="1050a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1050a-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="1050a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1050a-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="1050a-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1050a-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="1050a-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="1050a-110">MR 和 Azure 306:串流處理視訊</span><span class="sxs-lookup"><span data-stu-id="1050a-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="1050a-111">![最終產品-開始](images/AzureLabs-Lab6-00.png)
![最終成品-啟動](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="1050a-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="1050a-112">在本課程中，您將學習如何連接到 Windows 混合實境的 VR 體驗，以使串流 360 度的視訊播放沈浸式耳機上的 您的 Azure 媒體服務。</span><span class="sxs-lookup"><span data-stu-id="1050a-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="1050a-113">**Azure 媒體服務**是服務的集合，可讓您廣播品質的影片串流服務可接觸到現今最熱門的行動裝置的觀眾。</span><span class="sxs-lookup"><span data-stu-id="1050a-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="1050a-114">如需詳細資訊，請瀏覽[Azure 媒體服務頁面](https://azure.microsoft.com/services/media-services)。</span><span class="sxs-lookup"><span data-stu-id="1050a-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="1050a-115">完成本課程之後，您會有的混合的實境沈浸式耳機應用程式，可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1050a-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="1050a-116">擷取來自的 360 度影片**Azure 儲存體**，透過**Azure 媒體服務**。</span><span class="sxs-lookup"><span data-stu-id="1050a-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="1050a-117">顯示 Unity 場景中擷取的 360 度影片。</span><span class="sxs-lookup"><span data-stu-id="1050a-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="1050a-118">使用兩個不同的影片的兩個場景之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="1050a-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="1050a-119">在您的應用程式，則您對於如何將整合結果進行設計。</span><span class="sxs-lookup"><span data-stu-id="1050a-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="1050a-120">本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="1050a-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="1050a-121">它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。</span><span class="sxs-lookup"><span data-stu-id="1050a-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="1050a-122">裝置支援</span><span class="sxs-lookup"><span data-stu-id="1050a-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1050a-123">課程</span><span class="sxs-lookup"><span data-stu-id="1050a-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1050a-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1050a-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1050a-125"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1050a-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1050a-126">MR 和 Azure 306:串流處理視訊</span><span class="sxs-lookup"><span data-stu-id="1050a-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="1050a-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1050a-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="1050a-128">必要條件</span><span class="sxs-lookup"><span data-stu-id="1050a-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1050a-129">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="1050a-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1050a-130">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。</span><span class="sxs-lookup"><span data-stu-id="1050a-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="1050a-131">中所示，您可以自由使用最新的軟體[安裝工具文章](install-the-tools.md)，不過它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體與以下所列.</span><span class="sxs-lookup"><span data-stu-id="1050a-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="1050a-132">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="1050a-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1050a-133">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="1050a-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1050a-134">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="1050a-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1050a-135">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1050a-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1050a-136">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="1050a-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1050a-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1050a-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="1050a-138">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="1050a-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="1050a-139">Azure 的安裝程式和資料擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="1050a-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="1050a-140">兩個 mp4 格式的 360 度影片 (您可以找到一些免費的影片[在此下載頁面](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="1050a-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1050a-141">開始之前</span><span class="sxs-lookup"><span data-stu-id="1050a-141">Before you start</span></span>

1.  <span data-ttu-id="1050a-142">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="1050a-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="1050a-143">設定並測試混合實境沈浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="1050a-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1050a-144">您將會**不**本課程所需動作的控制器。</span><span class="sxs-lookup"><span data-stu-id="1050a-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="1050a-145">如果您需要支援沈浸式耳機的設定，請按一下[連結，有關如何設定 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="1050a-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="1050a-146">第 1-Azure 入口網站： 建立 Azure 儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="1050a-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="1050a-147">若要使用**Azure 儲存體服務**，您必須建立及設定**儲存體帳戶**在 Azure 入口網站中。</span><span class="sxs-lookup"><span data-stu-id="1050a-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="1050a-148">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="1050a-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="1050a-149">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="1050a-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1050a-150">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="1050a-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1050a-151">一旦您登入，按一下**儲存體帳戶**左側功能表中。</span><span class="sxs-lookup"><span data-stu-id="1050a-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="1050a-153">在 **儲存體帳戶**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="1050a-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="1050a-155">在 [**建立儲存體帳戶**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="1050a-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="1050a-156">插入**名稱**您的帳戶，請留意這個欄位只接受數字和小寫字母。</span><span class="sxs-lookup"><span data-stu-id="1050a-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="1050a-157">針對**部署模型**選取**Resource manager**。</span><span class="sxs-lookup"><span data-stu-id="1050a-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="1050a-158">針對**帳戶種類**，選取**儲存體 (一般用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="1050a-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="1050a-159">針對**效能**，選取\**標準 *。**</span><span class="sxs-lookup"><span data-stu-id="1050a-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="1050a-160">針對**複寫**選取**本地備援儲存體 (LRS)**。</span><span class="sxs-lookup"><span data-stu-id="1050a-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="1050a-161">離開**需要安全傳輸**作為**停用**。</span><span class="sxs-lookup"><span data-stu-id="1050a-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="1050a-162">選取 **訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="1050a-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="1050a-163">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1050a-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="1050a-164">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="1050a-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="1050a-165">判斷**位置**資源群組 （如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="1050a-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="1050a-166">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="1050a-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="1050a-167">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="1050a-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="1050a-168">您必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="1050a-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="1050a-170">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="1050a-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="1050a-171">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="1050a-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="1050a-173">此時您就不必遵循資源，只需移至下一步 一章。</span><span class="sxs-lookup"><span data-stu-id="1050a-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="1050a-174">章節 2-在 Azure 入口網站： 建立媒體服務</span><span class="sxs-lookup"><span data-stu-id="1050a-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="1050a-175">若要使用 Azure 媒體服務，您必須設定可供使用 （其中帳戶持有者必須是系統管理員） 的應用程式服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1050a-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="1050a-176">在 Azure 入口網站中，按一下**建立資源**在左上角，，然後搜尋**媒體服務**按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="1050a-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="1050a-177">您想在目前的資源都有粉紅色的圖示;按一下此選項，以顯示新的頁面。</span><span class="sxs-lookup"><span data-stu-id="1050a-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="1050a-179">新的頁面將提供的描述**媒體服務**。</span><span class="sxs-lookup"><span data-stu-id="1050a-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="1050a-180">在此提示的左下方，按一下**建立**按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="1050a-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="1050a-182">一旦您按下**建立**面板會顯示您要提供您新的媒體服務相關的一些詳細資料：</span><span class="sxs-lookup"><span data-stu-id="1050a-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="1050a-183">插入您想要**帳戶名稱**此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="1050a-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="1050a-184">選取 **訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="1050a-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="1050a-185">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1050a-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1050a-186">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="1050a-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1050a-187">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="1050a-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="1050a-188">如果您想要深入了解 Azure 資源群組，請遵循此[如何管理 Azure 資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="1050a-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="1050a-189">判斷**位置**資源群組 （如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="1050a-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="1050a-190">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="1050a-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="1050a-191">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="1050a-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="1050a-192">針對**儲存體帳戶**區段中，按一下**請選取...** 區段，然後按一下**儲存體帳戶**在最後一章中所建立。</span><span class="sxs-lookup"><span data-stu-id="1050a-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="1050a-193">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="1050a-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="1050a-194">按一下 [建立] 。</span><span class="sxs-lookup"><span data-stu-id="1050a-194">Click **Create**.</span></span>

        ![Azure 入口網站](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="1050a-196">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="1050a-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="1050a-197">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="1050a-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="1050a-199">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="1050a-199">Click on the notification to explore your new Service instance.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="1050a-201">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="1050a-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="1050a-202">在 [新媒體服務] 頁面的左側面板中按一下**資產**連結，也就是關於偶數的清單。</span><span class="sxs-lookup"><span data-stu-id="1050a-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="1050a-203">在下一步 頁面上，左上角的頁面上，按一下**上傳**。</span><span class="sxs-lookup"><span data-stu-id="1050a-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="1050a-205">按一下 **資料夾**圖示以瀏覽檔案，並選取您想要串流處理的第一次 360 視訊。</span><span class="sxs-lookup"><span data-stu-id="1050a-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="1050a-206">您可以遵循此[連結以下載範例視訊](https://vimeo.com/214401712)。</span><span class="sxs-lookup"><span data-stu-id="1050a-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="1050a-208">長檔名可能會使用編碼器的時發生問題： 因此若要確保影片並沒有問題，請考慮縮短您的視訊檔案名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="1050a-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="1050a-209">完成上傳影片時，進度列會變成綠色。</span><span class="sxs-lookup"><span data-stu-id="1050a-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="1050a-211">按一下上方的文字 (**yourservicename-資產**) 以返回**資產**頁面。</span><span class="sxs-lookup"><span data-stu-id="1050a-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="1050a-212">您會發現，您的影片已成功上傳。</span><span class="sxs-lookup"><span data-stu-id="1050a-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="1050a-213">按一下它。</span><span class="sxs-lookup"><span data-stu-id="1050a-213">Click on it.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="1050a-215">將您重新導向頁面會顯示您的影片的相關詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1050a-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="1050a-216">若要能夠使用您需要進行編碼，因此，依序按一下您的影片**編碼** 按鈕，在頁面的左上方。</span><span class="sxs-lookup"><span data-stu-id="1050a-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="1050a-218">新的面板會出現在右側，其中您可以在此處設定編碼選項，為您的檔案。</span><span class="sxs-lookup"><span data-stu-id="1050a-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="1050a-219">設定下列屬性 （部分已經將預設）：</span><span class="sxs-lookup"><span data-stu-id="1050a-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="1050a-220">**媒體編碼器名稱\*媒體編碼器標準**\*</span><span class="sxs-lookup"><span data-stu-id="1050a-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="1050a-221">**編碼預設\*內容自動調整的多個位元速率 MP4**\*</span><span class="sxs-lookup"><span data-stu-id="1050a-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="1050a-222">**作業名稱\*Video1.mp4 媒體編碼器標準處理**\*</span><span class="sxs-lookup"><span data-stu-id="1050a-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="1050a-223">**輸出媒體資產名稱\*Video1.mp4-Media Encoder Standard 編碼**\*</span><span class="sxs-lookup"><span data-stu-id="1050a-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Azure 入口網站](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="1050a-225">按一下 [建立] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1050a-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="1050a-226">您會注意到具有的列**新增的編碼工作**按一下該列，面板會顯示與顯示的編碼方式進行。</span><span class="sxs-lookup"><span data-stu-id="1050a-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-17.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="1050a-229">等候作業完成。</span><span class="sxs-lookup"><span data-stu-id="1050a-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="1050a-230">完成之後，放心地關閉具有 'X' 右上方的面板的面板。</span><span class="sxs-lookup"><span data-stu-id="1050a-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-19.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="1050a-233">這會帶，時間取決於您的影片檔案大小。</span><span class="sxs-lookup"><span data-stu-id="1050a-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="1050a-234">此程序可能需要一段時間。</span><span class="sxs-lookup"><span data-stu-id="1050a-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="1050a-235">既然已建立的視訊編碼的版本，您可以發行它，使其可供存取。</span><span class="sxs-lookup"><span data-stu-id="1050a-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="1050a-236">若要這樣做，請按一下藍色的連結**資產**返回至 [資產] 頁面。</span><span class="sxs-lookup"><span data-stu-id="1050a-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="1050a-238">您會看到您的影片，以及另一個，這是 \* \* 資產類型 \* 多位元速率 MP4 \* \* \*。</span><span class="sxs-lookup"><span data-stu-id="1050a-238">You will see your video along with another, which is of \*\*Asset Type \*Multi-Bitrate MP4\*\*\*.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="1050a-240">您可能會注意到新的資產，以及您初始的影片*未知*，而且它是具有 '0' 位元組**大小**，只重新整理您的視窗來進行更新。</span><span class="sxs-lookup"><span data-stu-id="1050a-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="1050a-241">按一下這個新的資產。</span><span class="sxs-lookup"><span data-stu-id="1050a-241">Click this new asset.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="1050a-243">您會看到類似的面板，您所使用之前，您也可以只是這是不同的資產。</span><span class="sxs-lookup"><span data-stu-id="1050a-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="1050a-244">按一下 **發佈**按鈕位於頁面頂端中央。</span><span class="sxs-lookup"><span data-stu-id="1050a-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="1050a-246">若要設定將會提示您**定位器**，這是進入點，為您的資產中的檔案/秒。</span><span class="sxs-lookup"><span data-stu-id="1050a-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="1050a-247">您的案例中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="1050a-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="1050a-248">**定位器類型** > **漸進式**。</span><span class="sxs-lookup"><span data-stu-id="1050a-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="1050a-249">**日期**並**時間**會從您目前的日期，為您設定，以在未來的時間 （在此情況下的 100 年）。</span><span class="sxs-lookup"><span data-stu-id="1050a-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="1050a-250">將保留為是或將它變更為符合。</span><span class="sxs-lookup"><span data-stu-id="1050a-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1050a-251">如需有關定位器，以及您可以選擇的詳細資訊，請瀏覽[Azure 媒體服務文件](https://docs.microsoft.com/azure/media-services/media-services-concepts)。</span><span class="sxs-lookup"><span data-stu-id="1050a-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="1050a-252">在該面板下方，按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1050a-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="1050a-254">您的影片，現在已發行，並可以串流，方法是使用其端點。</span><span class="sxs-lookup"><span data-stu-id="1050a-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="1050a-255">進一步向下的頁面**檔案**一節。</span><span class="sxs-lookup"><span data-stu-id="1050a-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="1050a-256">這是影片的要編碼的不同版本，您。</span><span class="sxs-lookup"><span data-stu-id="1050a-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="1050a-257">選取其中一個最高可能解決方式 （在下圖中很 1920 x 960 檔案），則會出現在右邊面板和。</span><span class="sxs-lookup"><span data-stu-id="1050a-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="1050a-258">您會在這裡找到**下載 URL**。</span><span class="sxs-lookup"><span data-stu-id="1050a-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="1050a-259">複製這**端點**因為您將在稍後的程式碼中使用它。</span><span class="sxs-lookup"><span data-stu-id="1050a-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-26.png)    

    ![Azure 入口網站](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="1050a-262">您也可以按下**播放**按鈕來播放影片，並加以測試。</span><span class="sxs-lookup"><span data-stu-id="1050a-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="1050a-263">您現在需要在這個實驗室中，您將使用第二個影片上傳。</span><span class="sxs-lookup"><span data-stu-id="1050a-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="1050a-264">請遵循上述步驟，重複執行相同的程序，第二個影片。</span><span class="sxs-lookup"><span data-stu-id="1050a-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="1050a-265">請確定您複製第二個**端點**也。</span><span class="sxs-lookup"><span data-stu-id="1050a-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="1050a-266">使用下列[連結以下載第二個視訊](https://vimeo.com/214402865)。</span><span class="sxs-lookup"><span data-stu-id="1050a-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="1050a-267">一旦已發佈這兩個影片，您就準備好移至下一步 一章。</span><span class="sxs-lookup"><span data-stu-id="1050a-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="1050a-268">第 3 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="1050a-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="1050a-269">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="1050a-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1050a-270">開啟**Unity**然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="1050a-270">Open **Unity** and click **New**.</span></span> 

    ![Azure 入口網站](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="1050a-272">您現在需要提供 Unity 專案名稱、 插入**MR\_360VideoStreaming**。</span><span class="sxs-lookup"><span data-stu-id="1050a-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="1050a-273">請確定專案類型設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="1050a-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="1050a-274">適用於您的某處設定的位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="1050a-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1050a-275">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="1050a-275">Then, click **Create project**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="1050a-277">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設定為**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="1050a-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="1050a-278">移至***編輯\*\*喜好設定*** ，然後在新視窗中，瀏覽**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="1050a-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1050a-279">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="1050a-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1050a-280">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="1050a-280">Close the **Preferences** window.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="1050a-282">接下來，移至***檔案\*\*組建設定*** ，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1050a-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="1050a-283">此外，請確定：</span><span class="sxs-lookup"><span data-stu-id="1050a-283">Also make sure that:</span></span>

    1. <span data-ttu-id="1050a-284">**裝置為目標**設為**任何裝置。**</span><span class="sxs-lookup"><span data-stu-id="1050a-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="1050a-285">**建置型別**設為**D3D。**</span><span class="sxs-lookup"><span data-stu-id="1050a-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="1050a-286">**SDK**設為**最新安裝。**</span><span class="sxs-lookup"><span data-stu-id="1050a-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="1050a-287">**Visual Studio 版本**設為**最新安裝。**</span><span class="sxs-lookup"><span data-stu-id="1050a-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="1050a-288">**建置並執行**設為**本機電腦。**</span><span class="sxs-lookup"><span data-stu-id="1050a-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="1050a-289">不要擔心設定**場景**現在，當您將會設定這些更新版本。</span><span class="sxs-lookup"><span data-stu-id="1050a-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="1050a-290">其餘的設定應該保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="1050a-290">The remaining settings should be left as default for now.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="1050a-292">中**組建設定**視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。</span><span class="sxs-lookup"><span data-stu-id="1050a-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="1050a-293">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="1050a-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="1050a-294">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="1050a-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="1050a-295">**指令碼\*\*\*\*執行階段版本**應該**穩定**（.NET 3.5 對等）。</span><span class="sxs-lookup"><span data-stu-id="1050a-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="1050a-296">**指令碼後端**應該是 **.NET。**</span><span class="sxs-lookup"><span data-stu-id="1050a-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="1050a-297">**API 相容性層級**應該是 **.NET 4.6。**</span><span class="sxs-lookup"><span data-stu-id="1050a-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="1050a-299">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。</span><span class="sxs-lookup"><span data-stu-id="1050a-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="1050a-301">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="1050a-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="1050a-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1050a-302">**InternetClient**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="1050a-304">一旦您進行這些變更，關閉**組建設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="1050a-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="1050a-305">儲存您的專案 **檔案** 儲存專案。</span><span class="sxs-lookup"><span data-stu-id="1050a-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="1050a-306">第 4 章-匯入 InsideOutSphere Unity 封裝</span><span class="sxs-lookup"><span data-stu-id="1050a-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1050a-307">如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)，它匯入到您的專案做為[ **自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從**第 5 章**。</span><span class="sxs-lookup"><span data-stu-id="1050a-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="1050a-308">您仍然必須建立 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="1050a-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="1050a-309">本課程，您必須下載 Unity 資產套件，稱為[ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="1050a-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="1050a-310">如何匯入**unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="1050a-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="1050a-311">您面前的 Unity 儀表板中，按一下**資產**在畫面頂端的功能表，然後按一下**匯入封裝 > 自訂封裝**。</span><span class="sxs-lookup"><span data-stu-id="1050a-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="1050a-313">使用檔案選擇器選取**InsideOutSphere.unitypackage**封裝，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="1050a-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="1050a-314">為此資產的元件的清單會顯示給您。</span><span class="sxs-lookup"><span data-stu-id="1050a-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="1050a-315">確認匯入，依序按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="1050a-315">Confirm the import by clicking **Import**.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="1050a-317">完成匯入後，您會發現三個新的資料夾**材料**，**模型**，和**Prefabs**，已新增至您**資產**資料夾。</span><span class="sxs-lookup"><span data-stu-id="1050a-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="1050a-318">這種資料夾結構是典型的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="1050a-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="1050a-320">開啟**模型**資料夾，而您會看到**InsideOutSphere**已匯入模型。</span><span class="sxs-lookup"><span data-stu-id="1050a-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="1050a-321">內**材料**資料夾，您會找到**InsideOutSpheres**材料*lambert1*，以及呼叫材質*ButtonMaterial*，這由 GazeButton，您就會立即看到。</span><span class="sxs-lookup"><span data-stu-id="1050a-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="1050a-322">**Prefabs**資料夾包含**InsideOutSphere** prefab 其中同時包含**InsideOutSphere** *模型*並*GazeButton*。</span><span class="sxs-lookup"><span data-stu-id="1050a-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="1050a-323">**不包含任何程式碼**，您將會依照本課程中撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="1050a-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="1050a-324">內**階層**，選取**Main Camera**物件，並更新下列元件：</span><span class="sxs-lookup"><span data-stu-id="1050a-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="1050a-325">**轉換**</span><span class="sxs-lookup"><span data-stu-id="1050a-325">**Transform**</span></span>

        1.  <span data-ttu-id="1050a-326">位置 = **X**:0， **Y**:0， **Z**:0.</span><span class="sxs-lookup"><span data-stu-id="1050a-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="1050a-327">旋轉 = **X**:0， **Y**:0， **Z**:0.</span><span class="sxs-lookup"><span data-stu-id="1050a-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="1050a-328">縮放比例**X**:1， **Y**:1， **Z**:1.</span><span class="sxs-lookup"><span data-stu-id="1050a-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="1050a-329">**相機**</span><span class="sxs-lookup"><span data-stu-id="1050a-329">**Camera**</span></span>

        1. <span data-ttu-id="1050a-330">**清除旗標**:不透明色彩。</span><span class="sxs-lookup"><span data-stu-id="1050a-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="1050a-331">**裁剪平面**:附近：0.1，到目前為止：6.</span><span class="sxs-lookup"><span data-stu-id="1050a-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="1050a-333">瀏覽至**Prefab**資料夾，然後再拖曳**InsideOutSphere**至 prefab**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="1050a-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="1050a-335">依序展開**InsideOutSphere**物件內**階層**按一下它旁邊的小箭號。</span><span class="sxs-lookup"><span data-stu-id="1050a-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="1050a-336">您會看到**子系**下方，叫做物件**GazeButton**。</span><span class="sxs-lookup"><span data-stu-id="1050a-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="1050a-337">這會用來變更場景，因此影片。</span><span class="sxs-lookup"><span data-stu-id="1050a-337">This will be used to change scenes and thus videos.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="1050a-339">在偵測器視窗中按一下**InsideOutSphere**的轉換元件，請確定已設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="1050a-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="1050a-340">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="1050a-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1050a-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-341">**X** 0</span></span>  |          <span data-ttu-id="1050a-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-342">**Y** 0</span></span>          |  <span data-ttu-id="1050a-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="1050a-344">轉換的旋轉</span><span class="sxs-lookup"><span data-stu-id="1050a-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1050a-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-345">**X** 0</span></span>  |          <span data-ttu-id="1050a-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="1050a-346">**Y** -50</span></span>        |  <span data-ttu-id="1050a-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="1050a-348">轉換為小數位數</span><span class="sxs-lookup"><span data-stu-id="1050a-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="1050a-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="1050a-349">**X** 1</span></span>   |          <span data-ttu-id="1050a-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="1050a-350">**Y** 1</span></span>          |  <span data-ttu-id="1050a-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="1050a-351">**Z** 1</span></span>  |

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="1050a-353">按一下  **GazeButton**子物件，並設定其**轉換**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1050a-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="1050a-354">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="1050a-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1050a-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="1050a-355">**X** 3.6</span></span>|          <span data-ttu-id="1050a-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="1050a-356">**Y** 1.3</span></span>        |  <span data-ttu-id="1050a-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="1050a-358">轉換的旋轉</span><span class="sxs-lookup"><span data-stu-id="1050a-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1050a-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-359">**X** 0</span></span>  |          <span data-ttu-id="1050a-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-360">**Y** 0</span></span>          |  <span data-ttu-id="1050a-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="1050a-362">轉換為小數位數</span><span class="sxs-lookup"><span data-stu-id="1050a-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="1050a-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="1050a-363">**X** 1</span></span>   |          <span data-ttu-id="1050a-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="1050a-364">**Y** 1</span></span>          |  <span data-ttu-id="1050a-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="1050a-365">**Z** 1</span></span>  |

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="1050a-367">第 5-建立 VideoController 類別</span><span class="sxs-lookup"><span data-stu-id="1050a-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="1050a-368">**VideoController**類別裝載兩個視訊的端點，將用來串流處理從 Azure 媒體服務內容。</span><span class="sxs-lookup"><span data-stu-id="1050a-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="1050a-369">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="1050a-369">To create this class:</span></span>

1.  <span data-ttu-id="1050a-370">以滑鼠右鍵按一下**Assets 資料夾**，位於**專案**] 面板中，然後按一下 [**建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="1050a-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="1050a-371">將資料夾命名**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="1050a-371">Name the folder **Scripts**.</span></span>

    ![建立 VideoController 類別](images/AzureLabs-Lab6-43.png)

    ![建立 VideoController 類別](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="1050a-374">按兩下**指令碼**資料夾將它開啟。</span><span class="sxs-lookup"><span data-stu-id="1050a-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="1050a-375">在資料夾中，以滑鼠右鍵按一下，然後按一下 **建立 > C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="1050a-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="1050a-376">指令碼命名**VideoController**。</span><span class="sxs-lookup"><span data-stu-id="1050a-376">Name the script **VideoController**.</span></span>

    ![建立 VideoController 類別](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="1050a-378">按兩下新**VideoController**指令碼，以開啟它**Visual Studio 2017。**</span><span class="sxs-lookup"><span data-stu-id="1050a-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![建立 VideoController 類別](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="1050a-380">更新的程式碼檔案頂端的命名空間如下所示：</span><span class="sxs-lookup"><span data-stu-id="1050a-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="1050a-381">輸入中的下列變數**VideoController**類別，以及使用**Awake()** 方法：</span><span class="sxs-lookup"><span data-stu-id="1050a-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="1050a-382">現在是從您的 Azure 媒體服務影片輸入端點的時間：</span><span class="sxs-lookup"><span data-stu-id="1050a-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="1050a-383">到第一個*video1endpoint*變數。</span><span class="sxs-lookup"><span data-stu-id="1050a-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="1050a-384">到第二個*video2endpoint*變數。</span><span class="sxs-lookup"><span data-stu-id="1050a-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="1050a-385">沒有使用的已知的問題*https* Unity 中，使用版本 2017.4.1f1 內。</span><span class="sxs-lookup"><span data-stu-id="1050a-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="1050a-386">如果影片提供 play 上的錯誤，請嘗試改為使用 'http'。</span><span class="sxs-lookup"><span data-stu-id="1050a-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="1050a-387">下一步 **start （)** 方法需要進行編輯。</span><span class="sxs-lookup"><span data-stu-id="1050a-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="1050a-388">每次使用者切換場景 （因此切換視訊），藉由查看視線 按鈕，就會觸發這個方法。</span><span class="sxs-lookup"><span data-stu-id="1050a-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="1050a-389">遵循**start （)** 方法，插入**PlayVideo()** *IEnumerator*方法，將用來啟動影片，順暢地 （因此會看到不間斷）。</span><span class="sxs-lookup"><span data-stu-id="1050a-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="1050a-390">您需要為這個類別的最後一個方法**ChangeScene()** 方法，將場景之間交換使用。</span><span class="sxs-lookup"><span data-stu-id="1050a-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="1050a-391">**ChangeScene()** 方法會使用便利 C\#功能，稱為*條件運算子*。</span><span class="sxs-lookup"><span data-stu-id="1050a-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="1050a-392">這是用來進行檢查的條件，然後值根據傳回的檢查，全部都在單一陳述式內的結果。</span><span class="sxs-lookup"><span data-stu-id="1050a-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="1050a-393">請遵循這[連結以深入了解條件式運算子](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)。</span><span class="sxs-lookup"><span data-stu-id="1050a-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="1050a-394">在 Visual Studio 中儲存的變更，然後再回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="1050a-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="1050a-395">傳回在 Unity 編輯器中，按一下並拖曳**VideoController**類別 [from] {.underline}**指令碼**資料夾**Main Camera**物件**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="1050a-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="1050a-396">按一下  **Main Camera**並查看**Inspector 面板**。</span><span class="sxs-lookup"><span data-stu-id="1050a-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="1050a-397">您會注意到，在新加入的指令碼元件，具有空值的欄位。</span><span class="sxs-lookup"><span data-stu-id="1050a-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="1050a-398">這是參考欄位，其以您的程式碼內的公用變數為目標。</span><span class="sxs-lookup"><span data-stu-id="1050a-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="1050a-399">拖曳**InsideOutSphere**物件**階層面板**來**球體**位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1050a-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="1050a-400">![建立 VideoController 類別](images/AzureLabs-Lab6-47.png)
    ![建立 VideoController 類別](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="1050a-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="1050a-401">章節 6-建立視線類別</span><span class="sxs-lookup"><span data-stu-id="1050a-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="1050a-402">這個類別會負責建立**Raycast** ，將 beprojected 從轉寄**Main Camera**，來偵測使用者查看的物件。</span><span class="sxs-lookup"><span data-stu-id="1050a-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="1050a-403">在此情況下， **Raycast**就必須找出，如果使用者查看**GazeButton**場景中物件，並會觸發的行為。</span><span class="sxs-lookup"><span data-stu-id="1050a-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="1050a-404">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="1050a-404">To create this Class:</span></span>

1.  <span data-ttu-id="1050a-405">移至**指令碼**您先前建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1050a-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="1050a-406">以滑鼠右鍵按一下**專案** 面板中，**建立** C\#指令碼 \* \*。</span><span class="sxs-lookup"><span data-stu-id="1050a-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="1050a-407">指令碼命名**視線**。</span><span class="sxs-lookup"><span data-stu-id="1050a-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="1050a-408">按兩下新***視線***指令碼，以開啟它**Visual Studio 2017。**</span><span class="sxs-lookup"><span data-stu-id="1050a-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="1050a-409">請確認下列命名空間頂端的 指令碼，然後移除任何其他：</span><span class="sxs-lookup"><span data-stu-id="1050a-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="1050a-410">然後新增下列變數內**視線**類別：</span><span class="sxs-lookup"><span data-stu-id="1050a-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="1050a-411">程式碼**Awake()** 並**start （)** 方法現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="1050a-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="1050a-412">新增下列程式碼**update （)** 投射 Raycast 和偵測目標叫用的方法：</span><span class="sxs-lookup"><span data-stu-id="1050a-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="1050a-413">在 Visual Studio 中儲存的變更，然後再回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="1050a-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="1050a-414">按一下並拖曳**視線**指令碼 資料夾中的 Main Camera 物件的類別**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="1050a-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="1050a-415">第 7 章-安裝這兩個 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="1050a-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="1050a-416">本指南的用途是設定在兩個場景，每個裝載視訊資料流。</span><span class="sxs-lookup"><span data-stu-id="1050a-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="1050a-417">讓您不需要再次設定然後，您會編輯新的場景，不過，您將複製的場景，您已經建立，以便*GazeButton*物件是在不同的位置，而且有不同的外觀。</span><span class="sxs-lookup"><span data-stu-id="1050a-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="1050a-418">這是要說明如何變更場景之間。</span><span class="sxs-lookup"><span data-stu-id="1050a-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="1050a-419">這樣做的方法是前往**檔案 > 儲存的場景為...**.儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="1050a-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="1050a-420">按一下 [**新的資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1050a-420">Click the **New folder** button.</span></span>

    ![第 7 章-安裝這兩個 Unity 場景](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="1050a-422">將資料夾命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="1050a-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="1050a-423">**儲存場景**視窗仍會開啟。</span><span class="sxs-lookup"><span data-stu-id="1050a-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="1050a-424">開啟您新建**場景**資料夾。</span><span class="sxs-lookup"><span data-stu-id="1050a-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="1050a-425">在 **檔案名稱：** 文字欄位中，輸入**VideoScene1**，然後按**儲存**。</span><span class="sxs-lookup"><span data-stu-id="1050a-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="1050a-426">傳回在 Unity 中，開啟您**場景**資料夾，然後以滑鼠左鍵按一下您**VideoScene1**檔案。</span><span class="sxs-lookup"><span data-stu-id="1050a-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="1050a-427">使用鍵盤，按下**Ctrl + D**您將會複製該場景</span><span class="sxs-lookup"><span data-stu-id="1050a-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="1050a-428">**重複**也可以瀏覽至執行命令**編輯 > 重複**。</span><span class="sxs-lookup"><span data-stu-id="1050a-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="1050a-429">Unity 會自動遞增場景名稱數，但，檢查以確定它符合先前插入的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1050a-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="1050a-430">您應該**VideoScene1**並**VideoScene2**。</span><span class="sxs-lookup"><span data-stu-id="1050a-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="1050a-431">使用您的兩個場景，請移至**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="1050a-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="1050a-432">與**Build Settings**視窗中開啟，拖曳至您場景**組建中的場景**一節。</span><span class="sxs-lookup"><span data-stu-id="1050a-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="1050a-434">您可以選取這兩個您場景，從您**場景**資料夾保存透過**Ctrl**按鈕，然後用滑鼠左鍵按一下每個場景，並最後進行拖曳，讓兩者之間。</span><span class="sxs-lookup"><span data-stu-id="1050a-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="1050a-435">關閉**Build Settings**  視窗中，並按兩下**VideoScene2**。</span><span class="sxs-lookup"><span data-stu-id="1050a-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="1050a-436">開啟第二個場景，請按一下 上**GazeButton**的子物件**InsideOutSphere**，並將其轉換，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1050a-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="1050a-437">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="1050a-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1050a-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-438">**X** 0</span></span>  |         <span data-ttu-id="1050a-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="1050a-439">**Y** 1.3</span></span>         | <span data-ttu-id="1050a-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="1050a-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="1050a-441">轉換的旋轉</span><span class="sxs-lookup"><span data-stu-id="1050a-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1050a-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-442">**X** 0</span></span>  |          <span data-ttu-id="1050a-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-443">**Y** 0</span></span>          |  <span data-ttu-id="1050a-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1050a-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="1050a-445">轉換為小數位數</span><span class="sxs-lookup"><span data-stu-id="1050a-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="1050a-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="1050a-446">**X** 1</span></span>   |          <span data-ttu-id="1050a-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="1050a-447">**Y** 1</span></span>          |  <span data-ttu-id="1050a-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="1050a-448">**Z** 1</span></span>  |

10. <span data-ttu-id="1050a-449">與**GazeButton**仍已選取，尋找位於子**Inspector**並在**Mesh 的篩選器**。</span><span class="sxs-lookup"><span data-stu-id="1050a-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="1050a-450">接下來按一下小目標**Mesh**參考欄位：</span><span class="sxs-lookup"><span data-stu-id="1050a-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="1050a-452">A**選取 Mesh**快顯視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="1050a-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="1050a-453">按兩下**Cube**從清單中的網狀結構**資產**。</span><span class="sxs-lookup"><span data-stu-id="1050a-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="1050a-455">**Mesh 的篩選條件**會更新，而且現在**Cube**。</span><span class="sxs-lookup"><span data-stu-id="1050a-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="1050a-456">現在，按一下 **齒輪**旁的圖示**球體 Collider**然後按一下**移除元件**，若要從這個物件刪除 collider。</span><span class="sxs-lookup"><span data-stu-id="1050a-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="1050a-458">與**GazeButton**保持選取，按一下**新增元件**底部的按鈕**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="1050a-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="1050a-459">在 [搜尋] 欄位中，輸入**方塊**，和**方塊 Collider**會是一個選項，按一下該選項，以新增**方塊 Collider**至您**GazeButton**物件.</span><span class="sxs-lookup"><span data-stu-id="1050a-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="1050a-461">**GazeButton**是部分更新，現在看起來不同，不過，您現在將建立新**材料**，好讓它看起來完全不同，而且容易比視為不同的物件，第一個場景中的物件。</span><span class="sxs-lookup"><span data-stu-id="1050a-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="1050a-462">瀏覽至您**材料**資料夾內 **[專案] 面板**。</span><span class="sxs-lookup"><span data-stu-id="1050a-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="1050a-463">重複**ButtonMaterial**材料 (按下**Ctrl** + **D**鍵盤上按滑鼠左鍵**材料**，然後從**編輯**檔案 功能表選項中，選取**重複**)。</span><span class="sxs-lookup"><span data-stu-id="1050a-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="1050a-464">![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-55.png)
    ![章 7--設定兩個的 Unity 場景](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="1050a-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="1050a-465">選取新**ButtonMaterial**材料 (這裡稱為**ButtonMaterial 1**)，內**Inspector**，按一下  **Albedo**色彩視窗。</span><span class="sxs-lookup"><span data-stu-id="1050a-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="1050a-466">會出現快顯視窗，您可以在其中選取另一種色彩 （選擇您喜歡的色彩），然後關閉快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="1050a-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="1050a-467">資料將會有自己的執行個體，和不同原始。</span><span class="sxs-lookup"><span data-stu-id="1050a-467">The Material will be its own instance, and different to the original.</span></span>

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="1050a-469">拖曳新**材料**拖曳至**GazeButton**子系，現在它的外觀，完全更新，使其容易分辨從第一個場景按鈕。</span><span class="sxs-lookup"><span data-stu-id="1050a-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="1050a-471">此時您可以在編輯器中測試專案之前建置的 UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="1050a-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="1050a-472">按下**播放**按鈕**編輯器**和戴上耳機。</span><span class="sxs-lookup"><span data-stu-id="1050a-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="1050a-474">看看這兩個**GazeButton**切換的第一個和第二個視訊的物件。</span><span class="sxs-lookup"><span data-stu-id="1050a-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="1050a-475">第 8 章-建置 UWP 方案</span><span class="sxs-lookup"><span data-stu-id="1050a-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="1050a-476">一旦確定編輯器沒有任何錯誤，您就準備好要建置的。</span><span class="sxs-lookup"><span data-stu-id="1050a-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="1050a-477">若要建置：</span><span class="sxs-lookup"><span data-stu-id="1050a-477">To Build:</span></span>

1.  <span data-ttu-id="1050a-478">按一下儲存目前的場景**檔案 > 儲存**。</span><span class="sxs-lookup"><span data-stu-id="1050a-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="1050a-479">核取方塊稱為**Unity C\#專案**（這是重要因為這樣可讓您完成建置後編輯類別）。</span><span class="sxs-lookup"><span data-stu-id="1050a-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="1050a-480">移至**檔案 > Build Settings**，按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="1050a-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="1050a-481">系統會提示您選取要 buildthe 方案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1050a-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="1050a-482">建立**建置**資料夾和該資料夾中建立適當的名稱，您選擇的另一個資料夾。</span><span class="sxs-lookup"><span data-stu-id="1050a-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="1050a-483">按一下您的新資料夾，然後按一下**選取資料夾**，因此，若要選擇該資料夾中，若要開始在該位置的組建。</span><span class="sxs-lookup"><span data-stu-id="1050a-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="1050a-484">![第 8 章-建置的 UWP 方案](images/AzureLabs-Lab6-60.png)
    ![章 8-建置的 UWP 方案](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="1050a-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="1050a-485">一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置。</span><span class="sxs-lookup"><span data-stu-id="1050a-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="1050a-486">第 9-將本機電腦上部署</span><span class="sxs-lookup"><span data-stu-id="1050a-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="1050a-487">完成組建後，**檔案總管**視窗將會出現在您的組建的位置。</span><span class="sxs-lookup"><span data-stu-id="1050a-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="1050a-488">開啟的資料夾命名，並建置，然後按兩下該資料夾，若要使用 Visual Studio 2017 中開啟您的方案中的方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="1050a-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="1050a-489">只剩下来為應用程式部署至您的電腦 (或*本機電腦*)。</span><span class="sxs-lookup"><span data-stu-id="1050a-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="1050a-490">若要部署到本機電腦：</span><span class="sxs-lookup"><span data-stu-id="1050a-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="1050a-491">在  **Visual Studio 2017**，開啟剛建立的方案檔。</span><span class="sxs-lookup"><span data-stu-id="1050a-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="1050a-492">在 **的方案平台**，選取**x86，本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="1050a-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="1050a-493">在 **方案組態**選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="1050a-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![第 9 章-部署在本機電腦上](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="1050a-495">您現在必須將任何套件還原到您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="1050a-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="1050a-496">以滑鼠右鍵按一下您**解決方案**，然後按一下**還原方案的 NuGet 套件...**</span><span class="sxs-lookup"><span data-stu-id="1050a-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="1050a-497">這是因為 Unity 建置的套件需要為目標來使用您本機電腦的參考。</span><span class="sxs-lookup"><span data-stu-id="1050a-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="1050a-498">移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="1050a-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="1050a-499">Visual Studio 會先建置，然後再部署您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1050a-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="1050a-500">您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。</span><span class="sxs-lookup"><span data-stu-id="1050a-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![第 9 章-部署在本機電腦上](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="1050a-502">當您執行的混合實境應用程式時，您將會位於內**InsideOutSphere**用您的應用程式內的模型。</span><span class="sxs-lookup"><span data-stu-id="1050a-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="1050a-503">此球形會將串流處理視訊，提供 360 度檢視，連入的視訊 （這圖書館這種觀點來看）。</span><span class="sxs-lookup"><span data-stu-id="1050a-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="1050a-504">不會感到驚訝的影片需要幾秒鐘的時間載入的如果您的應用程式受限於可用的網際網路速度，因為視訊必須擷取並下載，因此以串流處理至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1050a-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="1050a-505">當您準備好時，變更場景，並開啟第二段影片中，在紅色球體 gazing ！</span><span class="sxs-lookup"><span data-stu-id="1050a-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="1050a-506">然後可以自由回到上一頁，使用第二個場景中的藍色的立方體 ！</span><span class="sxs-lookup"><span data-stu-id="1050a-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="1050a-507">您已完成的 Azure 媒體服務應用程式</span><span class="sxs-lookup"><span data-stu-id="1050a-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="1050a-508">恭喜，您所建立的混合的實境應用程式，利用 Azure 媒體服務來將 360 的視訊串流處理。</span><span class="sxs-lookup"><span data-stu-id="1050a-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![實驗室結果](images/AzureLabs-Lab6-00.png)

![實驗室結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1050a-511">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="1050a-511">Bonus Exercises</span></span>

<span data-ttu-id="1050a-512">**練習 1**</span><span class="sxs-lookup"><span data-stu-id="1050a-512">**Exercise 1**</span></span>

<span data-ttu-id="1050a-513">完全可以只使用單一的場景變更這個教學課程中的影片。</span><span class="sxs-lookup"><span data-stu-id="1050a-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="1050a-514">試驗您的應用程式，並使它成為單一場景 ！</span><span class="sxs-lookup"><span data-stu-id="1050a-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="1050a-515">或許甚至是另一個將影片新增至混合。</span><span class="sxs-lookup"><span data-stu-id="1050a-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="1050a-516">**練習 2**</span><span class="sxs-lookup"><span data-stu-id="1050a-516">**Exercise 2**</span></span>

<span data-ttu-id="1050a-517">體驗 Azure 和 Unity，並嘗試實作應用程式，以自動選取 使用不同的檔案大小，取決於網際網路連線的強度影片的能力。</span><span class="sxs-lookup"><span data-stu-id="1050a-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


