---
title: MR 和 Azure 306-串流影片
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 媒體服務。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 學術, unity, 教學課程, api, 媒體服務, 串流影片, 360, 沉浸, vr
ms.openlocfilehash: e27bda2a9309f335feb0056703da492555c39fde
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896588"
---
>[!NOTE]
><span data-ttu-id="aab47-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="aab47-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="aab47-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="aab47-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="aab47-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="aab47-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="aab47-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="aab47-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="aab47-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="aab47-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="aab47-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="aab47-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="aab47-110">MR 和 Azure 306:串流影片</span><span class="sxs-lookup"><span data-stu-id="aab47-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="aab47-111">![最終產品-開始](images/AzureLabs-Lab6-00.png)
 ![最終產品-開始](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="aab47-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="aab47-112">在此課程中, 您將瞭解如何將您的 Azure 媒體服務連線到 Windows Mixed Reality VR 體驗, 以允許在沉浸式耳機上串流360度的影片播放。</span><span class="sxs-lookup"><span data-stu-id="aab47-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="aab47-113">**Azure 媒體服務**是一組服務, 可為您提供廣播品質的影片串流服務, 以在現今最熱門的行動裝置上觸及更大的觀眾。</span><span class="sxs-lookup"><span data-stu-id="aab47-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="aab47-114">如需詳細資訊, 請造訪[Azure 媒體服務頁面](https://azure.microsoft.com/services/media-services)。</span><span class="sxs-lookup"><span data-stu-id="aab47-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="aab47-115">完成此課程之後, 您將擁有一個混合現實的沉浸式耳機應用程式, 其將能夠執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="aab47-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="aab47-116">透過**Azure 媒體服務**從**Azure 儲存體**取出360度的影片。</span><span class="sxs-lookup"><span data-stu-id="aab47-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="aab47-117">顯示 Unity 場景內抓取的360度影片。</span><span class="sxs-lookup"><span data-stu-id="aab47-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="aab47-118">使用兩個不同的影片, 在兩個場景之間流覽。</span><span class="sxs-lookup"><span data-stu-id="aab47-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="aab47-119">在您的應用程式中, 您可以決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="aab47-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="aab47-120">本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。</span><span class="sxs-lookup"><span data-stu-id="aab47-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="aab47-121">您的工作是使用您從這個課程取得的知識, 來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="aab47-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="aab47-122">裝置支援</span><span class="sxs-lookup"><span data-stu-id="aab47-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="aab47-123">粗</span><span class="sxs-lookup"><span data-stu-id="aab47-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="aab47-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="aab47-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="aab47-125"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="aab47-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="aab47-126">MR 和 Azure 306:串流影片</span><span class="sxs-lookup"><span data-stu-id="aab47-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="aab47-127">✔️</span><span class="sxs-lookup"><span data-stu-id="aab47-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="aab47-128">必要條件</span><span class="sxs-lookup"><span data-stu-id="aab47-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="aab47-129">本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="aab47-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="aab47-130">也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (5 月 2018)。</span><span class="sxs-lookup"><span data-stu-id="aab47-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="aab47-131">您可以免費使用 [[安裝工具] 文章](install-the-tools.md)中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="aab47-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="aab47-132">在此課程中, 我們建議您採用下列硬體和軟體:</span><span class="sxs-lookup"><span data-stu-id="aab47-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="aab47-133">[與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦, 可用於沉浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="aab47-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="aab47-134">已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="aab47-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="aab47-135">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="aab47-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="aab47-136">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="aab47-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="aab47-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="aab47-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="aab47-138">[Windows Mixed Reality 沉浸式 (VR) 耳機](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="aab47-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="aab47-139">適用于 Azure 設定和資料抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="aab47-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="aab47-140">以檔案格式的 2 360-角度影片 (您可以[在此下載頁面](https://www.mettle.com/360vr-master-series-free-360-downloads-page)找到一些免版稅的影片)</span><span class="sxs-lookup"><span data-stu-id="aab47-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="aab47-141">開始之前</span><span class="sxs-lookup"><span data-stu-id="aab47-141">Before you start</span></span>

1.  <span data-ttu-id="aab47-142">為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。</span><span class="sxs-lookup"><span data-stu-id="aab47-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="aab47-143">設定和測試混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="aab47-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aab47-144">在此課程中, 您將**不**需要有動作控制器。</span><span class="sxs-lookup"><span data-stu-id="aab47-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="aab47-145">如果您需要支援設定「沉浸式耳機」, 請按一下[如何設定 Windows Mixed Reality 的連結](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="aab47-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="aab47-146">第1章-Azure 入口網站: 建立 Azure 儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="aab47-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="aab47-147">若要使用**Azure 儲存體服務**, 您將需要在 Azure 入口網站中建立並設定**儲存體帳戶**。</span><span class="sxs-lookup"><span data-stu-id="aab47-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="aab47-148">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="aab47-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="aab47-149">如果您還沒有 Azure 帳戶, 您將需要建立一個。</span><span class="sxs-lookup"><span data-stu-id="aab47-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="aab47-150">如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。</span><span class="sxs-lookup"><span data-stu-id="aab47-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="aab47-151">登入之後, 請按一下左側功能表中的 [**儲存體帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="aab47-153">在 [**儲存體帳戶**] 索引標籤上, 按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="aab47-155">在 [**建立儲存體帳戶**] 索引標籤中:</span><span class="sxs-lookup"><span data-stu-id="aab47-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="aab47-156">插入您帳戶的**名稱**, 請注意此欄位只接受數位和小寫字母。</span><span class="sxs-lookup"><span data-stu-id="aab47-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="aab47-157">針對 [**部署模型],** 選取 [ **Resource manager**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="aab47-158">針對 [**帳戶類型**], 選取 [**儲存體 (一般用途 v1)** ]。</span><span class="sxs-lookup"><span data-stu-id="aab47-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="aab47-159">針對 **效能**，選取 **標準\*。**</span><span class="sxs-lookup"><span data-stu-id="aab47-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="aab47-160">針對 [複寫], 請選取 **[本機-多餘儲存體 (LRS)** ]。</span><span class="sxs-lookup"><span data-stu-id="aab47-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="aab47-161">將 [**需要安全傳輸**] 保留為 [**停用**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="aab47-162">選取**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="aab47-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="aab47-163">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="aab47-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="aab47-164">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="aab47-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="aab47-165">判斷資源群組的**位置**(如果您要建立新的資源群組)。</span><span class="sxs-lookup"><span data-stu-id="aab47-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="aab47-166">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="aab47-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="aab47-167">某些 Azure 資產僅適用于特定區域。</span><span class="sxs-lookup"><span data-stu-id="aab47-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="aab47-168">您必須確認已瞭解適用于此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="aab47-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="aab47-170">按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="aab47-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="aab47-171">建立服務實例之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="aab47-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="aab47-173">此時您不需要追蹤資源, 只要移到下一章即可。</span><span class="sxs-lookup"><span data-stu-id="aab47-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="aab47-174">第2章-Azure 入口網站: 建立媒體服務</span><span class="sxs-lookup"><span data-stu-id="aab47-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="aab47-175">若要使用 Azure 媒體服務, 您必須將服務的實例設定為可供應用程式使用 (帳戶持有者必須是系統管理員)。</span><span class="sxs-lookup"><span data-stu-id="aab47-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="aab47-176">在 Azure 入口網站中, 按一下左上角的 [**建立資源**], 然後搜尋 [**媒體服務],** 按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="aab47-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="aab47-177">您想要的資源目前有粉紅色圖示;按一下此以顯示新的頁面。</span><span class="sxs-lookup"><span data-stu-id="aab47-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="aab47-179">新頁面將會提供**媒體服務**的描述。</span><span class="sxs-lookup"><span data-stu-id="aab47-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="aab47-180">在此提示的左下方, 按一下 [**建立**] 按鈕, 以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="aab47-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="aab47-182">當您按一下 [**建立**] 之後, 就會出現一個面板, 您需要提供一些有關新媒體服務的詳細資料:</span><span class="sxs-lookup"><span data-stu-id="aab47-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="aab47-183">為此服務實例插入所需的**帳戶名稱**。</span><span class="sxs-lookup"><span data-stu-id="aab47-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="aab47-184">選取**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="aab47-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="aab47-185">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="aab47-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="aab47-186">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="aab47-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="aab47-187">建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。</span><span class="sxs-lookup"><span data-stu-id="aab47-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="aab47-188">如果您想要深入瞭解 Azure 資源群組, 請遵循此[連結以瞭解如何管理 Azure 資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="aab47-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="aab47-189">判斷資源群組的**位置**(如果您要建立新的資源群組)。</span><span class="sxs-lookup"><span data-stu-id="aab47-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="aab47-190">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="aab47-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="aab47-191">某些 Azure 資產僅適用于特定區域。</span><span class="sxs-lookup"><span data-stu-id="aab47-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="aab47-192">針對 [**儲存體帳戶**] 區段, 按一下 [**請選取 ...** ] 區段, 然後按一下您在上一章中建立的**儲存體帳戶**。</span><span class="sxs-lookup"><span data-stu-id="aab47-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="aab47-193">您也必須確認您已瞭解適用于此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="aab47-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="aab47-194">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="aab47-194">Click **Create**.</span></span>

        ![Azure 入口網站](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="aab47-196">按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="aab47-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="aab47-197">建立服務實例之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="aab47-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="aab47-199">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="aab47-199">Click on the notification to explore your new Service instance.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="aab47-201">按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="aab47-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="aab47-202">在 [新增媒體服務] 頁面左側的面板中, 按一下 [**資產**] 連結, 這是大約一半的。</span><span class="sxs-lookup"><span data-stu-id="aab47-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="aab47-203">在下一個頁面上, 按一下頁面左上角的 [**上傳**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="aab47-205">按一下**資料夾**圖示以流覽您的檔案, 然後選取您想要串流處理的前360影片。</span><span class="sxs-lookup"><span data-stu-id="aab47-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="aab47-206">您可以遵循此[連結來下載範例影片](https://vimeo.com/214401712)。</span><span class="sxs-lookup"><span data-stu-id="aab47-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="aab47-208">長檔名可能會導致編碼器發生問題: 因此, 若要確保影片沒有問題, 請考慮縮短影片檔案名的長度。</span><span class="sxs-lookup"><span data-stu-id="aab47-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="aab47-209">當影片完成上傳時, 進度列會變成綠色。</span><span class="sxs-lookup"><span data-stu-id="aab47-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="aab47-211">按一下上方的文字 (**yourservicename-資產**) 以返回 [**資產**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="aab47-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="aab47-212">您會注意到已成功上傳您的影片。</span><span class="sxs-lookup"><span data-stu-id="aab47-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="aab47-213">按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="aab47-213">Click on it.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="aab47-215">您要重新導向的頁面會顯示有關您影片的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="aab47-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="aab47-216">若要能夠使用您的影片, 您必須按一下頁面左上角的 [**編碼**] 按鈕, 將其編碼。</span><span class="sxs-lookup"><span data-stu-id="aab47-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="aab47-218">右側會出現新的面板, 您可以在其中設定檔案的編碼選項。</span><span class="sxs-lookup"><span data-stu-id="aab47-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="aab47-219">設定下列屬性 (有些會預設為已設定):</span><span class="sxs-lookup"><span data-stu-id="aab47-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="aab47-220">**媒體編碼器名稱\*媒體編碼器標準**\*</span><span class="sxs-lookup"><span data-stu-id="aab47-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="aab47-221">**編碼預設*內容自動調整多重位元速率*設定**</span><span class="sxs-lookup"><span data-stu-id="aab47-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="aab47-222">\***媒體編碼器標準處理 Video1 的\*作業名稱**</span><span class="sxs-lookup"><span data-stu-id="aab47-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="aab47-223">**輸出媒體資產名稱\*Video1--已編碼媒體編碼器標準**\*</span><span class="sxs-lookup"><span data-stu-id="aab47-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Azure 入口網站](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="aab47-225">按一下 [建立] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aab47-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="aab47-226">您會發現**已加入編碼作業**的橫條, 按一下該橫條, 就會出現一個面板, 其中顯示編碼進度。</span><span class="sxs-lookup"><span data-stu-id="aab47-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-17.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="aab47-229">等候作業完成。</span><span class="sxs-lookup"><span data-stu-id="aab47-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="aab47-230">完成後, 您可以使用該面板右上方的 [X] 來關閉面板。</span><span class="sxs-lookup"><span data-stu-id="aab47-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-19.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="aab47-233">所需時間取決於影片的檔案大小。</span><span class="sxs-lookup"><span data-stu-id="aab47-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="aab47-234">此程式可能需要相當長的時間。</span><span class="sxs-lookup"><span data-stu-id="aab47-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="aab47-235">現在已建立影片的編碼版本, 您可以將其發佈, 使其可供存取。</span><span class="sxs-lookup"><span data-stu-id="aab47-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="aab47-236">若要這麼做, 請按一下藍色連結**資產**以返回 [資產] 頁面。</span><span class="sxs-lookup"><span data-stu-id="aab47-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="aab47-238">您會看到您的影片以及另一個, 這是「 **_多位元率_」資產類型**。</span><span class="sxs-lookup"><span data-stu-id="aab47-238">You will see your video along with another, which is of **Asset Type _Multi-Bitrate MP4_**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="aab47-240">您可能會注意到, 新的資產與您的初始影片是*未知*的, 而且有 ' 0 ' 個位元組的**大小**, 只要重新整理您的視窗, 即可更新。</span><span class="sxs-lookup"><span data-stu-id="aab47-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="aab47-241">按一下 [此新資產]。</span><span class="sxs-lookup"><span data-stu-id="aab47-241">Click this new asset.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="aab47-243">您會看到先前所用的面板相似, 只有這是不同的資產。</span><span class="sxs-lookup"><span data-stu-id="aab47-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="aab47-244">按一下位於頁面頂端的 [**發行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aab47-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="aab47-246">系統會提示您在資產中將 [**定位器**] (即進入點) 設定為 [檔案/s]。</span><span class="sxs-lookup"><span data-stu-id="aab47-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="aab47-247">針對您的案例, 請設定下列屬性:</span><span class="sxs-lookup"><span data-stu-id="aab47-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="aab47-248">**定位器類型** > **漸進式**。</span><span class="sxs-lookup"><span data-stu-id="aab47-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="aab47-249">系統會將您的**日期**和**時間**從目前的日期設定為未來的時間 (在此案例中為100年)。</span><span class="sxs-lookup"><span data-stu-id="aab47-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="aab47-250">保持原狀, 或將它變更為 [符合]。</span><span class="sxs-lookup"><span data-stu-id="aab47-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aab47-251">如需定位器的詳細資訊, 以及您可以選擇的內容, 請造訪[Azure 媒體服務檔](https://docs.microsoft.com/azure/media-services/media-services-concepts)。</span><span class="sxs-lookup"><span data-stu-id="aab47-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="aab47-252">在該面板的底部, 按一下 [**新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aab47-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="aab47-254">您的影片現在已發行, 可以使用其端點進行串流處理。</span><span class="sxs-lookup"><span data-stu-id="aab47-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="aab47-255">頁面的正下方是檔案區段。</span><span class="sxs-lookup"><span data-stu-id="aab47-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="aab47-256">這是影片的不同編碼版本所在的位置。</span><span class="sxs-lookup"><span data-stu-id="aab47-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="aab47-257">選取最高可能的解決方式 1 (在下圖中是1920x960 檔案), 右側的面板會出現。</span><span class="sxs-lookup"><span data-stu-id="aab47-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="aab47-258">您會在這裡找到**下載 URL**。</span><span class="sxs-lookup"><span data-stu-id="aab47-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="aab47-259">複製此**端點**, 因為您稍後會在程式碼中使用它。</span><span class="sxs-lookup"><span data-stu-id="aab47-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-26.png)    

    ![Azure 入口網站](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="aab47-262">您也可以按下 [**播放**] 按鈕來播放您的影片並加以測試。</span><span class="sxs-lookup"><span data-stu-id="aab47-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="aab47-263">您現在需要上傳將在此實驗室中使用的第二個影片。</span><span class="sxs-lookup"><span data-stu-id="aab47-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="aab47-264">遵循上述步驟, 針對第二個影片重複相同的程式。</span><span class="sxs-lookup"><span data-stu-id="aab47-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="aab47-265">請確定您也複製了第二個**端點**。</span><span class="sxs-lookup"><span data-stu-id="aab47-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="aab47-266">使用下列[連結下載第二個影片](https://vimeo.com/214402865)。</span><span class="sxs-lookup"><span data-stu-id="aab47-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="aab47-267">一旦發佈這兩個影片之後, 您就可以繼續進行下一章。</span><span class="sxs-lookup"><span data-stu-id="aab47-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="aab47-268">第3章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="aab47-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="aab47-269">以下是使用混合現實進行開發的一般設定, 因此是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="aab47-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="aab47-270">開啟**Unity** , 然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-270">Open **Unity** and click **New**.</span></span> 

    ![Azure 入口網站](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="aab47-272">您現在需要提供 Unity 專案名稱、 插入**MR\_360VideoStreaming**。</span><span class="sxs-lookup"><span data-stu-id="aab47-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="aab47-273">請確定 [專案類型] 設定為 [ **3d**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="aab47-274">將位置設定為適合您的位置 (請記住, 接近根目錄較佳)。</span><span class="sxs-lookup"><span data-stu-id="aab47-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="aab47-275">然後, 按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-275">Then, click **Create project**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="aab47-277">在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="aab47-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="aab47-278">移至 ***編輯* *喜好設定*** ，然後在新視窗中，瀏覽**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="aab47-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="aab47-279">將**外部腳本編輯器**變更為**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="aab47-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="aab47-280">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="aab47-280">Close the **Preferences** window.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="aab47-282">接下來，移至 ***檔案* *組建設定*** ，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aab47-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="aab47-283">也請確定:</span><span class="sxs-lookup"><span data-stu-id="aab47-283">Also make sure that:</span></span>

    1. <span data-ttu-id="aab47-284">[**目標裝置**] 已設定為 [**任何裝置]。**</span><span class="sxs-lookup"><span data-stu-id="aab47-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="aab47-285">[**組建類型**] 設定為 [ **D3D]。**</span><span class="sxs-lookup"><span data-stu-id="aab47-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="aab47-286">**SDK**設定為 [**最新安裝]。**</span><span class="sxs-lookup"><span data-stu-id="aab47-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="aab47-287">**Visual Studio 版本**設定為 [**最新安裝]。**</span><span class="sxs-lookup"><span data-stu-id="aab47-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="aab47-288">[**組建與執行**] 設定為 [**本機電腦]。**</span><span class="sxs-lookup"><span data-stu-id="aab47-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="aab47-289">現在請不要擔心設定**場景**, 因為您稍後會進行設定。</span><span class="sxs-lookup"><span data-stu-id="aab47-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="aab47-290">其餘的設定現在應保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="aab47-290">The remaining settings should be left as default for now.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="aab47-292">在 [**組建設定**] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測**器**所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="aab47-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="aab47-293">在此面板中, 需要驗證幾項設定:</span><span class="sxs-lookup"><span data-stu-id="aab47-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="aab47-294">在 [**其他設定**] 索引標籤中:</span><span class="sxs-lookup"><span data-stu-id="aab47-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="aab47-295">**指令碼** **執行階段版本**應該**穩定**（.NET 3.5 對等）。</span><span class="sxs-lookup"><span data-stu-id="aab47-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="aab47-296">**腳本後端**應該是 **.net。**</span><span class="sxs-lookup"><span data-stu-id="aab47-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="aab47-297">**API 相容性層級**應該是 **.net 4.6。**</span><span class="sxs-lookup"><span data-stu-id="aab47-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="aab47-299">在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]。</span><span class="sxs-lookup"><span data-stu-id="aab47-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="aab47-301">在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:</span><span class="sxs-lookup"><span data-stu-id="aab47-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="aab47-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="aab47-302">**InternetClient**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="aab47-304">進行這些變更之後, 請關閉 [**組建設定**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="aab47-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="aab47-305">儲存專案 \* 檔案 \* 儲存專案 \* \*。</span><span class="sxs-lookup"><span data-stu-id="aab47-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="aab47-306">第4章-匯入 InsideOutSphere Unity 封裝</span><span class="sxs-lookup"><span data-stu-id="aab47-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aab47-307">如果您想要略過此課程的*Unity 設定*元件, 並繼續直接進入程式碼, 您可以下載這個[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), 將它匯入到您的專案中做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html), 然後繼續進行**第5章**。</span><span class="sxs-lookup"><span data-stu-id="aab47-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="aab47-308">您仍然需要建立 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="aab47-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="aab47-309">在此課程中, 您將需要下載名為 InsideOutSphere 的 Unity 資產套件[ **。 unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="aab47-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="aab47-310">如何匯入**unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="aab47-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="aab47-311">在您前方的 Unity 儀表板中, 按一下畫面頂端功能表中的 **資產**, 然後按一下 匯**入套件 > 自訂套件**。</span><span class="sxs-lookup"><span data-stu-id="aab47-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="aab47-313">使用檔案選擇器選取**InsideOutSphere unitypackage**套件, 然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="aab47-314">系統會顯示此資產的元件清單。</span><span class="sxs-lookup"><span data-stu-id="aab47-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="aab47-315">按一下 [匯**入**] 確認匯入。</span><span class="sxs-lookup"><span data-stu-id="aab47-315">Confirm the import by clicking **Import**.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="aab47-317">完成匯入之後, 您會注意到有三個新的資料夾、**材質**、**型號**和**Prefabs**已新增至您的 [**資產**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="aab47-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="aab47-318">這種資料夾結構通常適用于 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="aab47-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="aab47-320">開啟 [**模型**] 資料夾, 您會看到**InsideOutSphere**模型已匯入。</span><span class="sxs-lookup"><span data-stu-id="aab47-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="aab47-321">在 [**材質**] 資料夾中, 您會發現 [ **InsideOutSpheres**材質] *lambert1*, 以及稱為*ButtonMaterial*的材料, 這是 GazeButton 所使用的資料, 您很快就會看到。</span><span class="sxs-lookup"><span data-stu-id="aab47-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="aab47-322">**Prefabs**資料夾包含**InsideOutSphere** prefab, 其中同時包含**InsideOutSphere** *模型*和*GazeButton*。</span><span class="sxs-lookup"><span data-stu-id="aab47-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="aab47-323">**未包含任何程式碼**, 您將會遵循此課程來撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="aab47-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="aab47-324">在階層中, 選取**主要相機**物件, 並更新下列元件:</span><span class="sxs-lookup"><span data-stu-id="aab47-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="aab47-325">**轉換**</span><span class="sxs-lookup"><span data-stu-id="aab47-325">**Transform**</span></span>

        1.  <span data-ttu-id="aab47-326">位置 = **X**:0、 **Y**:0, **Z**:0.</span><span class="sxs-lookup"><span data-stu-id="aab47-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="aab47-327">旋轉 = **X**:0、 **Y**:0, **Z**:0.</span><span class="sxs-lookup"><span data-stu-id="aab47-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="aab47-328">尺規**X**:1, **Y**:1, **Z**:1.</span><span class="sxs-lookup"><span data-stu-id="aab47-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="aab47-329">**相機**</span><span class="sxs-lookup"><span data-stu-id="aab47-329">**Camera**</span></span>

        1. <span data-ttu-id="aab47-330">**清除旗標**:單色。</span><span class="sxs-lookup"><span data-stu-id="aab47-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="aab47-331">**裁剪平面**:附近0.1, 目前:6.</span><span class="sxs-lookup"><span data-stu-id="aab47-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="aab47-333">流覽至 [ **Prefab** ] 資料夾, 然後將 [ **InsideOutSphere** ] Prefab 拖曳至 [階層] 面板。</span><span class="sxs-lookup"><span data-stu-id="aab47-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="aab47-335">按一下 [ **InsideOutSphere** ] 物件旁邊的小箭號, 以展開階層中的物件。</span><span class="sxs-lookup"><span data-stu-id="aab47-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="aab47-336">您會在其下看到一個名為**GazeButton**的**子**物件。</span><span class="sxs-lookup"><span data-stu-id="aab47-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="aab47-337">這將用來變更場景和影片。</span><span class="sxs-lookup"><span data-stu-id="aab47-337">This will be used to change scenes and thus videos.</span></span>

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="aab47-339">在 [偵測器] 視窗中, 按一下**InsideOutSphere**的 [轉換] 元件, 確定已設定下列屬性:</span><span class="sxs-lookup"><span data-stu-id="aab47-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="aab47-340">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="aab47-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="aab47-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-341">**X** 0</span></span>  |          <span data-ttu-id="aab47-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-342">**Y** 0</span></span>          |  <span data-ttu-id="aab47-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="aab47-344">轉換-旋轉</span><span class="sxs-lookup"><span data-stu-id="aab47-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="aab47-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-345">**X** 0</span></span>  |          <span data-ttu-id="aab47-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="aab47-346">**Y** -50</span></span>        |  <span data-ttu-id="aab47-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="aab47-348">轉換-調整規模</span><span class="sxs-lookup"><span data-stu-id="aab47-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="aab47-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="aab47-349">**X** 1</span></span>   |          <span data-ttu-id="aab47-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="aab47-350">**Y** 1</span></span>          |  <span data-ttu-id="aab47-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="aab47-351">**Z** 1</span></span>  |

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="aab47-353">按一下 [ **GazeButton** ] 子物件, 並設定其**轉換**, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="aab47-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="aab47-354">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="aab47-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="aab47-355">**X** 3。6</span><span class="sxs-lookup"><span data-stu-id="aab47-355">**X** 3.6</span></span>|          <span data-ttu-id="aab47-356">**Y** 1。3</span><span class="sxs-lookup"><span data-stu-id="aab47-356">**Y** 1.3</span></span>        |  <span data-ttu-id="aab47-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="aab47-358">轉換-旋轉</span><span class="sxs-lookup"><span data-stu-id="aab47-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="aab47-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-359">**X** 0</span></span>  |          <span data-ttu-id="aab47-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-360">**Y** 0</span></span>          |  <span data-ttu-id="aab47-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="aab47-362">轉換-調整規模</span><span class="sxs-lookup"><span data-stu-id="aab47-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="aab47-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="aab47-363">**X** 1</span></span>   |          <span data-ttu-id="aab47-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="aab47-364">**Y** 1</span></span>          |  <span data-ttu-id="aab47-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="aab47-365">**Z** 1</span></span>  |

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="aab47-367">第5章-建立 VideoController 類別</span><span class="sxs-lookup"><span data-stu-id="aab47-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="aab47-368">**VideoController**類別會裝載兩個將用來從 Azure 媒體服務串流內容的影片端點。</span><span class="sxs-lookup"><span data-stu-id="aab47-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="aab47-369">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="aab47-369">To create this class:</span></span>

1.  <span data-ttu-id="aab47-370">以滑鼠右鍵按一下 [**資產] 資料夾**(位於 [**專案**] 面板中), 然後按一下 [**建立 > 資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="aab47-371">將資料夾命名為**Scripts**。</span><span class="sxs-lookup"><span data-stu-id="aab47-371">Name the folder **Scripts**.</span></span>

    ![建立 VideoController 類別](images/AzureLabs-Lab6-43.png)

    ![建立 VideoController 類別](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="aab47-374">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="aab47-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="aab47-375">在資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立 >\# C 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="aab47-376">將腳本命名為**VideoController**。</span><span class="sxs-lookup"><span data-stu-id="aab47-376">Name the script **VideoController**.</span></span>

    ![建立 VideoController 類別](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="aab47-378">按兩下新的**VideoController**腳本, 以**Visual Studio 2017**開啟它。</span><span class="sxs-lookup"><span data-stu-id="aab47-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![建立 VideoController 類別](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="aab47-380">更新程式碼檔案頂端的命名空間, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="aab47-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="aab47-381">在**VideoController**類別中輸入下列變數, 以及使用**喚醒 ()** 方法:</span><span class="sxs-lookup"><span data-stu-id="aab47-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

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

7.  <span data-ttu-id="aab47-382">現在是從您的 Azure 媒體服務影片輸入端點的時機:</span><span class="sxs-lookup"><span data-stu-id="aab47-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="aab47-383">*Video1endpoint*變數中的第一個。</span><span class="sxs-lookup"><span data-stu-id="aab47-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="aab47-384">*Video2endpoint*變數中的第二個。</span><span class="sxs-lookup"><span data-stu-id="aab47-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="aab47-385">在 Unity 中使用*HTTPs*時, 有版本 2017.4.1 f1 的已知問題。</span><span class="sxs-lookup"><span data-stu-id="aab47-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="aab47-386">如果影片在播放時提供錯誤, 請嘗試改為使用 ' HTTP '。</span><span class="sxs-lookup"><span data-stu-id="aab47-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="aab47-387">接下來, 需要編輯**Start ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="aab47-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="aab47-388">每次使用者切換場景 (因而切換影片) 時, 就會觸發這個方法, 方式是查看 [注視] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aab47-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="aab47-389">在**Start ()** 方法後面, 插入**連結 playvideo ()** *IEnumerator*方法, 這將用來順暢地啟動影片 (因此不會出現任何斷斷續續)。</span><span class="sxs-lookup"><span data-stu-id="aab47-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

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

10. <span data-ttu-id="aab47-390">您在此類別中所需的最後一個方法是**ChangeScene ()** 方法, 它會用來在場景之間交換。</span><span class="sxs-lookup"><span data-stu-id="aab47-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="aab47-391">**ChangeScene ()** 方法會使用一個方便的\# C 功能, 稱為「*條件運算子*」。</span><span class="sxs-lookup"><span data-stu-id="aab47-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="aab47-392">如此一來, 就可以檢查條件, 然後根據檢查結果傳回的值, 全都在單一語句內。</span><span class="sxs-lookup"><span data-stu-id="aab47-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="aab47-393">[若要深入瞭解條件運算子](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator), 請遵循此連結。</span><span class="sxs-lookup"><span data-stu-id="aab47-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="aab47-394">請先儲存 Visual Studio 中的變更, 再返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="aab47-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="aab47-395">回到 Unity 編輯器中, 按一下 [從] {. 底線} [**腳本**] 資料夾中的 [ **VideoController** ] 類別, 然後拖曳至 [階層 ] 面板中的**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="aab47-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="aab47-396">按一下**主攝影機**並查看 [**檢查] 面板**。</span><span class="sxs-lookup"><span data-stu-id="aab47-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="aab47-397">您會發現, 在新加入的腳本元件中, 有一個欄位具有空的值。</span><span class="sxs-lookup"><span data-stu-id="aab47-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="aab47-398">這是參考欄位, 其以程式碼內的公用變數為目標。</span><span class="sxs-lookup"><span data-stu-id="aab47-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="aab47-399">將 [ **InsideOutSphere** ] 物件從 [階層]**面板**拖曳至 [**球體**] 位置, 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="aab47-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="aab47-400">![建立 VideoController 類別](images/AzureLabs-Lab6-47.png)
     ![建立 VideoController 類別](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="aab47-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="aab47-401">第6章-建立注視課程</span><span class="sxs-lookup"><span data-stu-id="aab47-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="aab47-402">此類別負責建立將從**主要相機**向前 Beprojected 的**Raycast** , 以偵測使用者正在查看的物件。</span><span class="sxs-lookup"><span data-stu-id="aab47-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="aab47-403">在此情況下, **Raycast**將需要識別使用者是否正在查看場景中的**GazeButton**物件, 並觸發行為。</span><span class="sxs-lookup"><span data-stu-id="aab47-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="aab47-404">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="aab47-404">To create this Class:</span></span>

1.  <span data-ttu-id="aab47-405">移至您先前建立的**腳本**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aab47-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="aab47-406">以滑鼠右鍵按一下**專案** 面板中，\**建立* \*C\# 指令碼\*\*。</span><span class="sxs-lookup"><span data-stu-id="aab47-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="aab47-407">將腳本命名為**注視**。</span><span class="sxs-lookup"><span data-stu-id="aab47-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="aab47-408">按兩下新的***注視***腳本, 使用**Visual Studio 2017**加以開啟。</span><span class="sxs-lookup"><span data-stu-id="aab47-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="aab47-409">請確定下列命名空間位於腳本的最上方, 並移除其他任何專案:</span><span class="sxs-lookup"><span data-stu-id="aab47-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="aab47-410">然後在**注視**類別內新增下列變數:</span><span class="sxs-lookup"><span data-stu-id="aab47-410">Then add the following variables inside the **Gaze** class:</span></span>

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

6.  <span data-ttu-id="aab47-411">現在必須加入**喚醒 ()** 和**Start ()** 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aab47-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="aab47-412">在**Update ()** 方法中新增下列程式碼, 以投影 Raycast 並偵測目標叫用:</span><span class="sxs-lookup"><span data-stu-id="aab47-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

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

8.  <span data-ttu-id="aab47-413">請先儲存 Visual Studio 中的變更, 再返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="aab47-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="aab47-414">按一下 [腳本] 資料夾中的 [**注視**] 類別, 並將其拖曳至 [階層] 面板中的主要相機物件。</span><span class="sxs-lookup"><span data-stu-id="aab47-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="aab47-415">第7章-設定兩個 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="aab47-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="aab47-416">本章的目的是要設定兩個場景, 分別裝載影片以進行串流。</span><span class="sxs-lookup"><span data-stu-id="aab47-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="aab47-417">您會複製已建立的場景, 這樣就不需要再次設定它, 但您會接著編輯新場景, 讓*GazeButton*物件位於不同的位置, 並具有不同的外觀。</span><span class="sxs-lookup"><span data-stu-id="aab47-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="aab47-418">這是為了示範如何在幕後進行變更。</span><span class="sxs-lookup"><span data-stu-id="aab47-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="aab47-419">請前往 檔案 **> 另存場景**... 來執行此動作。儲存 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="aab47-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="aab47-420">按一下 [**新增資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aab47-420">Click the **New folder** button.</span></span>

    ![第7章-設定兩個 Unity 場景](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="aab47-422">將資料夾命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="aab47-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="aab47-423">[**儲存場景**] 視窗仍會開啟。</span><span class="sxs-lookup"><span data-stu-id="aab47-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="aab47-424">開啟新建立的 [**幕後**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="aab47-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="aab47-425">在 [**檔案名:** 文字] 欄位中, 輸入**VideoScene1**, 然後按 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="aab47-426">回到 Unity, 開啟您的**幕後**資料夾, 然後以滑鼠左鍵按一下您的**VideoScene1**檔案。</span><span class="sxs-lookup"><span data-stu-id="aab47-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="aab47-427">使用您的鍵盤, 然後按下**Ctrl + D** , 將會複製該場景</span><span class="sxs-lookup"><span data-stu-id="aab47-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="aab47-428">您也可以流覽至 [**編輯 > 重複**] 來執行**重複**的命令。</span><span class="sxs-lookup"><span data-stu-id="aab47-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="aab47-429">Unity 會自動遞增場景名稱, 但仍然檢查, 以確保它符合先前插入的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aab47-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="aab47-430">您應該有**VideoScene1**和**VideoScene2**。</span><span class="sxs-lookup"><span data-stu-id="aab47-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="aab47-431">使用您的兩個場景, 移至 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="aab47-432">在 [**組建設定**] 視窗開啟的情況下, 將您的場景拖曳至 [**組建中的場景**] 區段。</span><span class="sxs-lookup"><span data-stu-id="aab47-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="aab47-434">您可以透過按住**Ctrl**鍵, 然後以滑鼠左鍵按一下每個場景, 最後再拖曳兩者, 從**幕後**資料夾中選取這兩個場景。</span><span class="sxs-lookup"><span data-stu-id="aab47-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="aab47-435">關閉 [**組建設定**] 視窗, 然後按兩下 [ **VideoScene2**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="aab47-436">當第二個場景開啟時, 按一下**InsideOutSphere**的 [ **GazeButton** ] 子物件, 並設定其轉換, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="aab47-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="aab47-437">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="aab47-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="aab47-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-438">**X** 0</span></span>  |         <span data-ttu-id="aab47-439">**Y** 1。3</span><span class="sxs-lookup"><span data-stu-id="aab47-439">**Y** 1.3</span></span>         | <span data-ttu-id="aab47-440">**Z** 3。6</span><span class="sxs-lookup"><span data-stu-id="aab47-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="aab47-441">轉換-旋轉</span><span class="sxs-lookup"><span data-stu-id="aab47-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="aab47-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-442">**X** 0</span></span>  |          <span data-ttu-id="aab47-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-443">**Y** 0</span></span>          |  <span data-ttu-id="aab47-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="aab47-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="aab47-445">轉換-調整規模</span><span class="sxs-lookup"><span data-stu-id="aab47-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="aab47-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="aab47-446">**X** 1</span></span>   |          <span data-ttu-id="aab47-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="aab47-447">**Y** 1</span></span>          |  <span data-ttu-id="aab47-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="aab47-448">**Z** 1</span></span>  |

10. <span data-ttu-id="aab47-449">在仍選取**GazeButton**子系的情況下, 查看 [**檢查**] 和 [**網格] 篩選準則**。</span><span class="sxs-lookup"><span data-stu-id="aab47-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="aab47-450">按一下 [**網格**參考] 欄位旁的小目標:</span><span class="sxs-lookup"><span data-stu-id="aab47-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="aab47-452">[**選取網格**] 快顯視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="aab47-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="aab47-453">按兩下**資產**清單中的 [ **Cube**網格]。</span><span class="sxs-lookup"><span data-stu-id="aab47-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="aab47-455">**網格篩選器**將會更新, 現在是一個**Cube**。</span><span class="sxs-lookup"><span data-stu-id="aab47-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="aab47-456">現在, 按一下 [**球體碰撞**件] 旁的**齒輪**圖示, 然後按一下 [**移除元件**], 以刪除此物件中的碰撞。</span><span class="sxs-lookup"><span data-stu-id="aab47-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="aab47-458">在仍選取**GazeButton**的情況下, 按一下偵測**器**底部的 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aab47-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="aab47-459">在 [搜尋] 欄位中，輸入**方塊**，和**方塊 Collider**會是一個選項，按一下該選項，以新增**方塊 Collider**至您**GazeButton**物件.</span><span class="sxs-lookup"><span data-stu-id="aab47-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="aab47-461">**GazeButton**現在已部分更新, 看起來會不同, 不過, 您現在會建立新的資料, 讓它看起來完全不同, 而且比第一個場景中的物件更容易辨識為不同的物件。</span><span class="sxs-lookup"><span data-stu-id="aab47-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="aab47-462">在 [**專案] 面板**中, 流覽至您的 [**材質**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="aab47-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="aab47-463">複製**ButtonMaterial**材質 (在鍵盤上按**Ctrl**  +  **D** , 或以滑鼠右鍵按一下**材質**, 然後從 [**編輯**檔案] 功能表選項選取 [**複製**])。</span><span class="sxs-lookup"><span data-stu-id="aab47-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="aab47-464">![第7章--設定兩個 unity](images/AzureLabs-Lab6-55.png)
    場景![第7章--設定兩個 unity 場景](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="aab47-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="aab47-465">選取新的**ButtonMaterial**材質 (名為**ButtonMaterial 1**), 然後在偵測**器**中, 按一下 [ **Albedo**色彩] 視窗。</span><span class="sxs-lookup"><span data-stu-id="aab47-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="aab47-466">隨即會出現一個快顯視窗, 您可以在其中選取另一個色彩 (選擇您喜歡的方式), 然後關閉快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="aab47-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="aab47-467">此材質會是它自己的實例, 與原始的不同。</span><span class="sxs-lookup"><span data-stu-id="aab47-467">The Material will be its own instance, and different to the original.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="aab47-469">將新的資料拖曳到**GazeButton**子系上, 以立即完整更新其外觀, 讓它可以輕鬆地從第一個場景按鈕來區分。</span><span class="sxs-lookup"><span data-stu-id="aab47-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="aab47-471">此時, 您可以在建立 UWP 專案之前, 先在編輯器中測試專案。</span><span class="sxs-lookup"><span data-stu-id="aab47-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="aab47-472">按下**編輯器**中的 [**播放**] 按鈕, 然後戴頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="aab47-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="aab47-474">查看兩個**GazeButton**物件, 以在第一和第二部影片之間切換。</span><span class="sxs-lookup"><span data-stu-id="aab47-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="aab47-475">第8章-建立 UWP 解決方案</span><span class="sxs-lookup"><span data-stu-id="aab47-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="aab47-476">一旦確定編輯器沒有任何錯誤, 您就可以開始建立。</span><span class="sxs-lookup"><span data-stu-id="aab47-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="aab47-477">若要建立:</span><span class="sxs-lookup"><span data-stu-id="aab47-477">To Build:</span></span>

1.  <span data-ttu-id="aab47-478">按一下 檔案 **> 儲存** 來儲存目前的場景。</span><span class="sxs-lookup"><span data-stu-id="aab47-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="aab47-479">勾選名為 [ **Unity C\# Projects** ] 的方塊 (這很重要, 因為它可讓您在組建完成後編輯類別)。</span><span class="sxs-lookup"><span data-stu-id="aab47-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="aab47-480">移至 [檔案] **> [組建設定**], 按一下 [**組建**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="aab47-481">系統會提示您選取要 buildthe 解決方案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="aab47-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="aab47-482">建立**組建**資料夾, 並在該資料夾內建立另一個資料夾, 並使用您選擇的適當名稱。</span><span class="sxs-lookup"><span data-stu-id="aab47-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="aab47-483">按一下您的新資料夾, 然後按一下 [**選取資料夾**], 選擇該資料夾, 在該位置開始組建。</span><span class="sxs-lookup"><span data-stu-id="aab47-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="aab47-484">![第8章--組建 uwp 解決方案](images/AzureLabs-Lab6-60.png)
     ![第8章--組建 uwp 解決方案](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="aab47-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="aab47-485">Unity 完成建立 (可能需要一些時間) 之後, 它會在組建的位置開啟 [檔案**瀏覽器**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="aab47-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="aab47-486">第9章-在本機電腦上部署</span><span class="sxs-lookup"><span data-stu-id="aab47-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="aab47-487">組建完成之後, [檔案**瀏覽器**] 視窗就會出現在組建的位置。</span><span class="sxs-lookup"><span data-stu-id="aab47-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="aab47-488">開啟您已命名並建立的資料夾, 然後按兩下該資料夾中的解決方案 (.sln) 檔案, 以 Visual Studio 2017 開啟您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="aab47-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="aab47-489">剩下的工作就是將您的應用程式部署到您的電腦 (或*本機電腦*)。</span><span class="sxs-lookup"><span data-stu-id="aab47-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="aab47-490">若要部署到本機電腦:</span><span class="sxs-lookup"><span data-stu-id="aab47-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="aab47-491">在**Visual Studio 2017**中, 開啟剛建立的方案檔。</span><span class="sxs-lookup"><span data-stu-id="aab47-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="aab47-492">在**解決方案平臺**中, 選取 [ **x86]、[本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="aab47-493">在 [**解決方案**設定] 中, 選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="aab47-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![第9章--在本機電腦上部署](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="aab47-495">您現在必須將任何套件還原至您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="aab47-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="aab47-496">以滑鼠右鍵按一下您的**方案**, 然後按一下 [**還原解決方案的 NuGet 套件**...]</span><span class="sxs-lookup"><span data-stu-id="aab47-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="aab47-497">這是因為 Unity 所建立的套件必須設為目標, 才能與您的本機電腦參考搭配使用。</span><span class="sxs-lookup"><span data-stu-id="aab47-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="aab47-498">移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="aab47-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="aab47-499">Visual Studio 會先建立並部署您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="aab47-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="aab47-500">您的應用程式現在應該會出現在已安裝的應用程式清單中, 並準備好啟動。</span><span class="sxs-lookup"><span data-stu-id="aab47-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![第9章--在本機電腦上部署](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="aab47-502">當您執行 Mixed Reality 應用程式時, 您會在應用程式內使用的**InsideOutSphere**模型中。</span><span class="sxs-lookup"><span data-stu-id="aab47-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="aab47-503">這個球體將是影片的串流目標位置, 提供內送影片的360度觀點 (這種觀點的 filmed)。</span><span class="sxs-lookup"><span data-stu-id="aab47-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="aab47-504">如果影片需要幾秒鐘的時間才能載入, 您的應用程式會受限於可用的網際網路速度, 因為必須提取並下載影片, 才能串流至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="aab47-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="aab47-505">當您準備好時, 請撥雲見日紅色球體來變更場景並開啟第二個影片!</span><span class="sxs-lookup"><span data-stu-id="aab47-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="aab47-506">然後您可以隨意使用第二個場景中的藍色 cube!</span><span class="sxs-lookup"><span data-stu-id="aab47-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="aab47-507">您完成的 Azure 媒體服務應用程式</span><span class="sxs-lookup"><span data-stu-id="aab47-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="aab47-508">恭喜, 您建立了一個混合現實應用程式, 利用 Azure 媒體服務串流處理360影片。</span><span class="sxs-lookup"><span data-stu-id="aab47-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![實驗室結果](images/AzureLabs-Lab6-00.png)

![實驗室結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="aab47-511">額外練習</span><span class="sxs-lookup"><span data-stu-id="aab47-511">Bonus Exercises</span></span>

<span data-ttu-id="aab47-512">**練習1**</span><span class="sxs-lookup"><span data-stu-id="aab47-512">**Exercise 1**</span></span>

<span data-ttu-id="aab47-513">在本教學課程中, 您可以完全只使用單一場景來變更影片。</span><span class="sxs-lookup"><span data-stu-id="aab47-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="aab47-514">試驗您的應用程式, 並使其進入單一場景!</span><span class="sxs-lookup"><span data-stu-id="aab47-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="aab47-515">甚至可能將另一部影片新增至混合。</span><span class="sxs-lookup"><span data-stu-id="aab47-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="aab47-516">**練習2**</span><span class="sxs-lookup"><span data-stu-id="aab47-516">**Exercise 2**</span></span>

<span data-ttu-id="aab47-517">使用 Azure 和 Unity 進行實驗, 並嘗試執行此功能, 讓應用程式根據網際網路連線的強度, 自動選取不同檔案大小的影片。</span><span class="sxs-lookup"><span data-stu-id="aab47-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


