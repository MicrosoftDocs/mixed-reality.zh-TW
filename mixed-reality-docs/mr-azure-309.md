---
title: MR 和 Azure 309-Application insights
description: 完成此課程, 以瞭解如何使用 Azure 應用程式 Insights 服務, 收集有關混合現實應用程式中使用者行為的分析。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合現實, 學術, unity, 教學課程, api, application insights, hololens, 沉浸, vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694564"
---
>[!NOTE]
><span data-ttu-id="16cc2-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="16cc2-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="16cc2-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="16cc2-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="16cc2-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="16cc2-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="16cc2-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="16cc2-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="16cc2-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="16cc2-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="16cc2-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="16cc2-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="16cc2-110">MR 和 Azure 309:Application insights</span><span class="sxs-lookup"><span data-stu-id="16cc2-110">MR and Azure 309: Application insights</span></span>

![最終產品-開始](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="16cc2-112">在此課程中, 您將瞭解如何使用 Azure 應用程式 Insights API 來收集有關使用者行為的分析, 將 Application Insights 功能新增到混合的現實應用程式中。</span><span class="sxs-lookup"><span data-stu-id="16cc2-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="16cc2-113">Application Insights 是一種 Microsoft 服務, 可讓開發人員從其應用程式收集分析, 並從便於使用的入口網站進行管理。</span><span class="sxs-lookup"><span data-stu-id="16cc2-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="16cc2-114">分析可以從效能到您想要收集的自訂資訊。</span><span class="sxs-lookup"><span data-stu-id="16cc2-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="16cc2-115">如需詳細資訊, 請造訪[Application Insights 頁面](https://azure.microsoft.com/services/application-insights/)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="16cc2-116">完成此課程之後, 您將擁有一個混合現實的沉浸式耳機應用程式, 其將能夠執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="16cc2-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="16cc2-117">允許使用者在場景周圍進行注視和移動。</span><span class="sxs-lookup"><span data-stu-id="16cc2-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="16cc2-118">藉由使用場景中的物件, 觸發將分析傳送至*Application Insights 服務*的程式。</span><span class="sxs-lookup"><span data-stu-id="16cc2-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="16cc2-119">應用程式也會在服務上呼叫, 並在過去24小時內, 提取使用者最常完成哪些物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="16cc2-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="16cc2-120">該物件會將其色彩變更為綠色。</span><span class="sxs-lookup"><span data-stu-id="16cc2-120">That object will change its color to green.</span></span>

<span data-ttu-id="16cc2-121">本課程將告訴您如何將來自 Application Insights 服務的結果, 帶入以 Unity 為基礎的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="16cc2-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="16cc2-122">您必須將這些概念套用到您可能正在建立的自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="16cc2-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="16cc2-123">裝置支援</span><span class="sxs-lookup"><span data-stu-id="16cc2-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="16cc2-124">粗</span><span class="sxs-lookup"><span data-stu-id="16cc2-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="16cc2-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="16cc2-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="16cc2-126"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="16cc2-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="16cc2-127">MR 和 Azure 309:Application insights</span><span class="sxs-lookup"><span data-stu-id="16cc2-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="16cc2-128">✔️</span><span class="sxs-lookup"><span data-stu-id="16cc2-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="16cc2-129">✔️</span><span class="sxs-lookup"><span data-stu-id="16cc2-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="16cc2-130">雖然此課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機, 但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="16cc2-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="16cc2-131">隨著課程的遵循, 您會看到您可能需要用來支援 HoloLens 的任何變更的附注。</span><span class="sxs-lookup"><span data-stu-id="16cc2-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="16cc2-132">使用 HoloLens 時, 您可能會在語音捕獲期間發現一些回應。</span><span class="sxs-lookup"><span data-stu-id="16cc2-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16cc2-133">先決條件</span><span class="sxs-lookup"><span data-stu-id="16cc2-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="16cc2-134">本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="16cc2-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="16cc2-135">也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (2018 年7月)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="16cc2-136">您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="16cc2-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="16cc2-137">在此課程中, 我們建議您採用下列硬體和軟體:</span><span class="sxs-lookup"><span data-stu-id="16cc2-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="16cc2-138">[與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦, 可用於沉浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="16cc2-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="16cc2-139">已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="16cc2-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="16cc2-140">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="16cc2-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="16cc2-141">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="16cc2-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="16cc2-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="16cc2-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="16cc2-143">已啟用開發人員模式的[Windows Mixed Reality 沉浸 (VR) 耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="16cc2-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="16cc2-144">一組具有內建麥克風的耳機 (如果耳機沒有內建的 mic 和喇叭)</span><span class="sxs-lookup"><span data-stu-id="16cc2-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="16cc2-145">適用于 Azure 設定和 Application Insights 資料抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="16cc2-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="16cc2-146">開始之前</span><span class="sxs-lookup"><span data-stu-id="16cc2-146">Before you start</span></span>

<span data-ttu-id="16cc2-147">為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="16cc2-148">請注意, 進入*Application Insights*的資料需要一些時間, 因此請耐心等候。</span><span class="sxs-lookup"><span data-stu-id="16cc2-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="16cc2-149">如果您想要檢查服務是否已收到您的資料, 請查看第[14 章](#chapter-14---the-application-insights-service-portal), 這會示範如何流覽入口網站。</span><span class="sxs-lookup"><span data-stu-id="16cc2-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="16cc2-150">第1章-Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="16cc2-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="16cc2-151">若要使用*Application Insights*, 您將需要在 Azure 入口網站中建立和設定*Application Insights 服務*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="16cc2-152">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="16cc2-153">如果您還沒有 Azure 帳戶, 您將需要建立一個。</span><span class="sxs-lookup"><span data-stu-id="16cc2-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="16cc2-154">如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。</span><span class="sxs-lookup"><span data-stu-id="16cc2-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="16cc2-155">登入之後, 按一下左上角的 [**新增**], 並搜尋*Application Insights*, 然後按一下**Enter 鍵**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="16cc2-156">在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。</span><span class="sxs-lookup"><span data-stu-id="16cc2-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="16cc2-158">右側的新頁面將會提供*Azure 應用程式 Insights*服務的描述。</span><span class="sxs-lookup"><span data-stu-id="16cc2-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="16cc2-159">在此頁面的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="16cc2-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="16cc2-161">一旦您按下 **建立** :</span><span class="sxs-lookup"><span data-stu-id="16cc2-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="16cc2-162">為此服務實例插入您想要的**名稱**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="16cc2-163">選取 **[一般**] 作為 [**應用程式類型**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="16cc2-164">選取適當的**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="16cc2-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="16cc2-165">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="16cc2-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="16cc2-166">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="16cc2-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="16cc2-167">建議您將與單一專案相關聯的所有 Azure 服務 (例如這些課程) 都保留在通用資源群組下)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="16cc2-168">如果您想要深入瞭解 Azure 資源群組, 請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="16cc2-169">選取 [**位置**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="16cc2-170">您也必須確認您已瞭解適用于此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="16cc2-171">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-171">Select **Create**.</span></span>

        ![Azure 入口網站](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="16cc2-173">按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="16cc2-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="16cc2-174">建立服務實例之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="16cc2-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="16cc2-176">按一下 [通知] 以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="16cc2-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="16cc2-178">按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="16cc2-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="16cc2-179">您將會進入新的*Application Insights 服務*實例。</span><span class="sxs-lookup"><span data-stu-id="16cc2-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="16cc2-181">讓此網頁保持開啟且易於存取, 您通常會回到這裡查看所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="16cc2-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="16cc2-182">若要執行 Application Insights, 您必須使用三個 (3) 個特定的值:**檢測金鑰**、**應用程式識別碼**和**API 金鑰**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="16cc2-183">您會在下面看到如何從您的服務取得這些值。</span><span class="sxs-lookup"><span data-stu-id="16cc2-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="16cc2-184">請務必在空白的 [*記事本*] 頁面上記下這些值, 因為您很快就會在程式碼中使用它們。</span><span class="sxs-lookup"><span data-stu-id="16cc2-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="16cc2-185">若要尋找**檢測金鑰**, 您必須向下滾動服務函式清單, 然後按一下 [**屬性**], 顯示的索引標籤會顯示**服務金鑰**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="16cc2-187">以下是一些**屬性**, 您會發現需要按一下的**API 存取權**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="16cc2-188">右邊的面板會提供您應用程式的**應用程式識別碼**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="16cc2-190">在 [**應用程式識別碼**] 面板仍然開啟的情況下, 按一下 [**建立 api 金鑰**], 這會開啟 [*建立 api 金鑰*] 面板。</span><span class="sxs-lookup"><span data-stu-id="16cc2-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="16cc2-192">在現在開啟 [*建立 API 金鑰*] 面板中, 輸入描述, 然後**勾選三個方塊**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="16cc2-193">按一下 [**產生金鑰**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-193">Click **Generate Key**.</span></span> <span data-ttu-id="16cc2-194">將會建立並顯示您的**API 金鑰**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure 入口網站](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="16cc2-196">這是您的**服務金鑰**只會顯示的時間, 因此請務必立即建立複本。</span><span class="sxs-lookup"><span data-stu-id="16cc2-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="16cc2-197">第2章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="16cc2-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="16cc2-198">以下是使用混合現實進行開發的一般設定, 因此是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="16cc2-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="16cc2-199">開啟*Unity* , 然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-199">Open *Unity* and click **New**.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="16cc2-201">您現在必須提供 Unity 專案名稱, 並插入**MR\_Azure\_Application\_Insights**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="16cc2-202">請確定*範本*已設定為 [ **3d**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="16cc2-203">將位置設定為適合您的*位置*(請記住, 接近根目錄較佳)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="16cc2-204">然後, 按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-204">Then, click **Create project**.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="16cc2-206">在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="16cc2-207">移至 **[ \>編輯喜好**設定], 然後在新視窗中, 流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="16cc2-208">將**外部腳本編輯器**變更為**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="16cc2-209">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="16cc2-209">Close the **Preferences** window.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="16cc2-211">接下來, 移至 **\>** [檔案] [組建設定], 然後按一下 [**切換平臺**] 按鈕, 將平臺切換至通用 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="16cc2-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="16cc2-213">移至 **\>** [檔案] [組建設定], 並確認:</span><span class="sxs-lookup"><span data-stu-id="16cc2-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="16cc2-214">**目標裝置**已設定為**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="16cc2-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="16cc2-215">若為 Microsoft HoloLens, 請將**目標裝置**設定為*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="16cc2-216">**組建類型**設定為**D3D**</span><span class="sxs-lookup"><span data-stu-id="16cc2-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="16cc2-217">**SDK**已設定為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="16cc2-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="16cc2-218">**組建和執行**設定為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="16cc2-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="16cc2-219">儲存場景, 並將它加入至組建。</span><span class="sxs-lookup"><span data-stu-id="16cc2-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="16cc2-220">選取 [新增] [**開啟場景**] 來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="16cc2-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="16cc2-221">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="16cc2-221">A save window will appear.</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="16cc2-223">建立這個的新資料夾, 以及任何未來的場景, 然後按一下 [**新增資料夾**] 按鈕, 建立新的資料夾, 將它命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="16cc2-225">開啟新建立的 [**幕後**] 資料夾, 然後在 [*檔案名:* 文字] 欄位中, 輸入**ApplicationInsightsScene**, 然後按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="16cc2-227">[**組建設定**] 中的其餘設定, 現在應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="16cc2-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="16cc2-228">在 [**組建設定**] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測**器**所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="16cc2-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="16cc2-230">在此面板中, 需要驗證幾項設定:</span><span class="sxs-lookup"><span data-stu-id="16cc2-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="16cc2-231">在 [**其他設定**] 索引標籤中:</span><span class="sxs-lookup"><span data-stu-id="16cc2-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="16cc2-232">**指令碼** **執行階段版本**應該 **（.NET 4.6 對等） 的實驗性**，這會觸發程序需要重新啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="16cc2-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="16cc2-233">**腳本後端**應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="16cc2-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="16cc2-234">**API 相容性層級**應該是 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="16cc2-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="16cc2-236">在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:</span><span class="sxs-lookup"><span data-stu-id="16cc2-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="16cc2-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="16cc2-237">**InternetClient**</span></span>     

            ![設定 Unity 專案](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="16cc2-239">在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="16cc2-241">回到 [**組建設定**] **, C# Unity 專案**不再呈現灰色;勾選 [] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="16cc2-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="16cc2-242">關閉 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="16cc2-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="16cc2-243">儲存場景和專案 ([  > 檔案] [**儲存場景]/**  > [檔案] [**儲存專案**])。</span><span class="sxs-lookup"><span data-stu-id="16cc2-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="16cc2-244">第3章-匯入 Unity 封裝</span><span class="sxs-lookup"><span data-stu-id="16cc2-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16cc2-245">如果您想要略過*Unity 設定*本課程的元件, 並繼續直接進入程式碼, 您可以免費下載此[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), 將它匯入您的專案中做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="16cc2-246">這也會包含下一章中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="16cc2-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="16cc2-247">匯入之後, 請從[**第6章**](#chapter-6---create-the-applicationinsightstracker-class)繼續進行。</span><span class="sxs-lookup"><span data-stu-id="16cc2-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16cc2-248">若要在 Unity 中使用 Application Insights, 您需要匯入它的 DLL, 以及 Newtonsoft DLL。</span><span class="sxs-lookup"><span data-stu-id="16cc2-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="16cc2-249">Unity 中目前有一個已知問題, 需要在匯入後重新設定外掛程式。</span><span class="sxs-lookup"><span data-stu-id="16cc2-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="16cc2-250">解決錯誤之後, 將不再需要這些步驟 (本節中的 4-7)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="16cc2-251">若要將 Application Insights 匯入至您自己的專案, 請確定您已[下載包含外掛程式的 ' unitypackage '](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="16cc2-252">然後, 執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="16cc2-252">Then, do the following:</span></span>

1.  <span data-ttu-id="16cc2-253">使用 [ 資產 **\> ] [匯入套件\> ] [自訂套件**] 功能表選項, 將 unitypackage 新增至 Unity。</span><span class="sxs-lookup"><span data-stu-id="16cc2-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="16cc2-254">在快顯的 [匯**入 Unity 封裝**] 方塊中, 確定已選取 (和包含)**外掛程式**底下的所有專案。</span><span class="sxs-lookup"><span data-stu-id="16cc2-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="16cc2-256">按一下 [匯**入**] 按鈕, 將專案新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="16cc2-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="16cc2-257">移至 [專案] 視圖中 [**外掛程式**] 底下的 [ **Insights** ] 資料夾, 然後選取 [*僅*下列外掛程式]:</span><span class="sxs-lookup"><span data-stu-id="16cc2-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="16cc2-258">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="16cc2-258">Microsoft.ApplicationInsights</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="16cc2-260">選取此*外掛程式*之後, 請確認已**取消**核取**任何平臺**, 然後確定**WSAPlayer**也未核取, 然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="16cc2-261">這麼做只是為了確認檔案已正確設定。</span><span class="sxs-lookup"><span data-stu-id="16cc2-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="16cc2-263">標記這類外掛程式時, 會將它們設定為僅在 Unity 編輯器中使用。</span><span class="sxs-lookup"><span data-stu-id="16cc2-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="16cc2-264">在 [WSA] 資料夾中有一組不同的 Dll, 將在從 Unity 匯出專案之後使用。</span><span class="sxs-lookup"><span data-stu-id="16cc2-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="16cc2-265">接下來, 您必須在 [ **Insights** ] 資料夾內開啟 [ **WSA** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="16cc2-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="16cc2-266">您會看到您剛才設定的相同檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="16cc2-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="16cc2-267">選取此檔案, 然後在偵測器中, 確定已**取消**選取**任何平臺**, 然後確定**只**會**核**取 [ **WSAPlayer** ]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="16cc2-268">按一下 **[套用]** 。</span><span class="sxs-lookup"><span data-stu-id="16cc2-268">Click **Apply**.</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="16cc2-270">您現在必須遵循**步驟 4-6**, 而不是*Newtonsoft*外掛程式。</span><span class="sxs-lookup"><span data-stu-id="16cc2-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="16cc2-271">請參閱下列螢幕擷取畫面, 以瞭解結果看起來的樣子。</span><span class="sxs-lookup"><span data-stu-id="16cc2-271">See the below screenshot for what the outcome should look like.</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="16cc2-273">第4章-設定相機和使用者控制項</span><span class="sxs-lookup"><span data-stu-id="16cc2-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="16cc2-274">在本章中, 您將設定相機和控制項, 以允許使用者在場景中查看及移動。</span><span class="sxs-lookup"><span data-stu-id="16cc2-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="16cc2-275">以滑鼠右鍵按一下 [階層] 面板中的空白區域, 然後在 [**建立** > **空白**] 上。</span><span class="sxs-lookup"><span data-stu-id="16cc2-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="16cc2-277">將新的空白 GameObject 重新命名為**攝影機父系**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="16cc2-279">以滑鼠右鍵按一下 [階層] 面板中的空白區域, 然後在 [ **3D 物件**] 和 [**球體**] 上。</span><span class="sxs-lookup"><span data-stu-id="16cc2-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="16cc2-280">將球體重新命名為**右手**邊。</span><span class="sxs-lookup"><span data-stu-id="16cc2-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="16cc2-281">將右手邊的**轉換縮放比例**設定為**0.1、0.1、0.1**</span><span class="sxs-lookup"><span data-stu-id="16cc2-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="16cc2-283">按一下 [*球體碰撞*器] 元件中的**齒輪**, 然後**移除 [元件**], 以移除右側的**球體碰撞**器元件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="16cc2-285">在 [階層] 面板中, 將**主相機**和**右手**邊物件拖曳至**相機父**物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="16cc2-287">將**主要相機**和**右手**邊物件的**轉換位置**設定為**0, 0, 0**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-31.png)

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="16cc2-290">第5章-在 Unity 場景中設定物件</span><span class="sxs-lookup"><span data-stu-id="16cc2-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="16cc2-291">您現在會為場景建立一些基本圖案, 讓使用者可以進行互動。</span><span class="sxs-lookup"><span data-stu-id="16cc2-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="16cc2-292">以滑鼠右鍵按一下 [階層]*面板*中的空白區域, 然後在 [ **3d 物件**] 上, 選取 [**平面**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="16cc2-293">將平面**轉換位置**設定為**0,-1, 0**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="16cc2-294">將平面**轉換比例**設定為**5、1、5**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="16cc2-296">建立要與您的**平面**物件搭配使用的基本材質, 讓其他圖形更容易看到。</span><span class="sxs-lookup"><span data-stu-id="16cc2-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="16cc2-297">流覽至您的 [*專案] 面板*, 以滑鼠右鍵按一下 [**建立**], 接著按 [**資料夾**], 以建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="16cc2-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="16cc2-298">為 it**教材**命名。</span><span class="sxs-lookup"><span data-stu-id="16cc2-298">Name it **Materials**.</span></span>

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-34.png) ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="16cc2-301">開啟 [**材質**] 資料夾, 然後以滑鼠右鍵按一下 [**建立**], 然後按一下 [**材質**] 來建立新的資料。</span><span class="sxs-lookup"><span data-stu-id="16cc2-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="16cc2-302">將它命名為**藍色**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-302">Name it **Blue**.</span></span>

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-36.png) ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="16cc2-305">選取新的**藍色**材質後, 查看 [*檢查*], 然後按一下 [ **Albedo**] 矩形視窗。</span><span class="sxs-lookup"><span data-stu-id="16cc2-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="16cc2-306">選取藍色色彩 (下一張圖片是**十六進位色彩:\#3592FFFF**)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="16cc2-307">選擇之後, 請按一下 [關閉] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="16cc2-307">Click the close button once you have chosen.</span></span>

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="16cc2-309">將您的新材質從 [**材質**] 資料夾拖曳到您在新建立的**平面**上, 放在您的場景內 (或將它放置在階層內的**平面**物件上)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="16cc2-311">以滑鼠右鍵按一下 [階層]*面板*中的空白區域, 然後在 [ **3d 物件]、[膠囊**] 上。</span><span class="sxs-lookup"><span data-stu-id="16cc2-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="16cc2-312">具有**Capsule**選取，變更其**轉換** *位置*至： **-10、 1、 0**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="16cc2-313">以滑鼠右鍵按一下 [階層]*面板*中的空白區域, 然後在 [ **3d 物件]、[Cube**] 上。</span><span class="sxs-lookup"><span data-stu-id="16cc2-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="16cc2-314">具有**Cube**選取，變更其**轉換** *位置*來：**0、0、10**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="16cc2-315">以滑鼠右鍵按一下 [階層]*面板*中的空白區域, 然後在 [ **3d 物件]、[球體**] 上。</span><span class="sxs-lookup"><span data-stu-id="16cc2-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="16cc2-316">具有 **球體** 選取，變更其 **轉換** *位置* 來：**10, 0, 0**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="16cc2-318">這些*位置*值是*建議*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="16cc2-319">您可以自由地將物件的位置設定為任何您想要的, 不過, 如果物件距離與相機不太遠, 應用程式的使用者就會更容易。</span><span class="sxs-lookup"><span data-stu-id="16cc2-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="16cc2-320">當您的應用程式正在執行時, 它必須能夠識別場景內的物件, 以達到此目的, 必須加上標籤。</span><span class="sxs-lookup"><span data-stu-id="16cc2-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="16cc2-321">選取其中一個物件, 然後在 偵測*器* 面板中按一下 **新增標記 ...** , 這會將偵測*器*與 標籤 **& 圖層** 面板交換。</span><span class="sxs-lookup"><span data-stu-id="16cc2-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="16cc2-322">![在 Unity 場景](images/AzureLabs-Lab309-41.png)中設定物件![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="16cc2-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="16cc2-323">按一下 [ **+] (加號)** 符號, 然後將標記名稱輸入為**ObjectInScene**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="16cc2-325">如果您的標籤使用不同的名稱, 您必須確保這種變更也會變成*DataFromAnalytics*、 *ObjectTrigger*和*注視*、腳本之後, 以便在場景中找到並偵測您的物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="16cc2-326">建立標記之後, 您現在必須將它套用到您的所有三個物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="16cc2-327">在階層中, 按住**Shift**鍵, 然後依序按一下 **[膠囊**]、[ **Cube**] 和 [**球體**]、[物件], 然後在偵測*器*中, 按一下下拉式功能表加上**標記**, 然後按一下 [ *ObjectInScene* ]您建立的標記。</span><span class="sxs-lookup"><span data-stu-id="16cc2-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="16cc2-328">![在 Unity 場景](images/AzureLabs-Lab309-44.png)中設定物件![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="16cc2-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="16cc2-329">第6章-建立 ApplicationInsightsTracker 類別</span><span class="sxs-lookup"><span data-stu-id="16cc2-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="16cc2-330">您需要建立的第一個腳本是**ApplicationInsightsTracker**, 它會負責:</span><span class="sxs-lookup"><span data-stu-id="16cc2-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="16cc2-331">根據使用者互動建立事件以提交給 Azure 應用程式 Insights。</span><span class="sxs-lookup"><span data-stu-id="16cc2-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="16cc2-332">根據使用者互動, 建立適當的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="16cc2-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="16cc2-333">將事件提交至 Application Insights 服務實例。</span><span class="sxs-lookup"><span data-stu-id="16cc2-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="16cc2-334">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="16cc2-334">To create this class:</span></span>

1.  <span data-ttu-id="16cc2-335">在 [*專案] 面板*中按一下滑鼠右鍵, 然後按 [**建立** > **資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="16cc2-336">將資料夾命名為**Scripts**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-336">Name the folder **Scripts**.</span></span>

    ![建立 ApplicationInsightsTracker 類別](images/AzureLabs-Lab309-46.png)  ![建立 ApplicationInsightsTracker 類別](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="16cc2-339">在建立 script 資料夾之後, 按兩下以開啟。</span><span class="sxs-lookup"><span data-stu-id="16cc2-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="16cc2-340">然後, 在該資料夾中, 以滑鼠右鍵按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="16cc2-341">將腳本命名為**ApplicationInsightsTracker**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="16cc2-342">按兩下新的**ApplicationInsightsTracker**腳本, 以**Visual Studio**開啟它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="16cc2-343">更新腳本頂端的命名空間, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="16cc2-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="16cc2-344">在類別內插入下列變數:</span><span class="sxs-lookup"><span data-stu-id="16cc2-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="16cc2-345">使用 Azure 入口網站中的*服務金鑰*(如步驟9的「開始」一[章](#chapter-1---the-azure-portal)所述), 適當地設定**instrumentationKey、applicationId 和 API_Key**值。</span><span class="sxs-lookup"><span data-stu-id="16cc2-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="16cc2-346">然後, 新增**開始 ()** 和**喚醒 ()** 方法, 這會在類別初始化時呼叫:</span><span class="sxs-lookup"><span data-stu-id="16cc2-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="16cc2-347">新增負責傳送應用程式所註冊的事件和計量的方法:</span><span class="sxs-lookup"><span data-stu-id="16cc2-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="16cc2-348">請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="16cc2-349">第7章-建立注視腳本</span><span class="sxs-lookup"><span data-stu-id="16cc2-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="16cc2-350">下一個要建立的腳本是**注視**腳本。</span><span class="sxs-lookup"><span data-stu-id="16cc2-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="16cc2-351">此腳本會負責建立將從*主要相機*向前投射的*Raycast* , 以偵測使用者正在查看的物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="16cc2-352">在此情況下, *Raycast*將需要識別使用者是否查看具有**ObjectInScene**標記的物件, 然後計算使用者在該物件上*gazes*的時間長度。</span><span class="sxs-lookup"><span data-stu-id="16cc2-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="16cc2-353">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="16cc2-354">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="16cc2-355">將腳本命名為**注視**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="16cc2-356">按兩下腳本, 以 Visual Studio 開啟它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="16cc2-357">將現有的程式碼取代為下列內容:</span><span class="sxs-lookup"><span data-stu-id="16cc2-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="16cc2-358">現在必須加入**喚醒 ()** 和**Start ()** 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="16cc2-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="16cc2-359">在**注視**類別內部, 于**Update ()** 方法中新增下列程式碼, 以投影*Raycast*並偵測目標叫用:</span><span class="sxs-lookup"><span data-stu-id="16cc2-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="16cc2-360">加入**ResetFocusedObject ()** 方法, 以在使用者查看物件時, 將資料傳送至**Application Insights** 。</span><span class="sxs-lookup"><span data-stu-id="16cc2-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="16cc2-361">您現在已完成**注視**腳本。</span><span class="sxs-lookup"><span data-stu-id="16cc2-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="16cc2-362">請先儲存*Visual Studio*中的變更, 再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="16cc2-363">第8章-建立 ObjectTrigger 類別</span><span class="sxs-lookup"><span data-stu-id="16cc2-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="16cc2-364">您需要建立的下一個腳本是**ObjectTrigger**, 它會負責:</span><span class="sxs-lookup"><span data-stu-id="16cc2-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="16cc2-365">將衝突所需的元件新增至主要攝影機。</span><span class="sxs-lookup"><span data-stu-id="16cc2-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="16cc2-366">偵測相機是否接近標記為**ObjectInScene**的物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="16cc2-367">若要建立腳本:</span><span class="sxs-lookup"><span data-stu-id="16cc2-367">To create the script:</span></span>

1.  <span data-ttu-id="16cc2-368">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="16cc2-369">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="16cc2-370">將腳本命名為**ObjectTrigger**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="16cc2-371">按兩下腳本, 以 Visual Studio 開啟它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="16cc2-372">將現有的程式碼取代為下列內容:</span><span class="sxs-lookup"><span data-stu-id="16cc2-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="16cc2-373">請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="16cc2-374">第9章-建立 DataFromAnalytics 類別</span><span class="sxs-lookup"><span data-stu-id="16cc2-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="16cc2-375">現在您將需要建立**DataFromAnalytics**腳本, 其負責:</span><span class="sxs-lookup"><span data-stu-id="16cc2-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="16cc2-376">正在提取有關相機已接近哪個物件的分析資料。</span><span class="sxs-lookup"><span data-stu-id="16cc2-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="16cc2-377">使用*服務金鑰*, 以允許與您的 Azure 應用程式 Insights 服務實例進行通訊。</span><span class="sxs-lookup"><span data-stu-id="16cc2-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="16cc2-378">根據具有最高事件計數的場景排序物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="16cc2-379">將最接近物件的材質色彩變更為*綠色*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="16cc2-380">若要建立腳本:</span><span class="sxs-lookup"><span data-stu-id="16cc2-380">To create the script:</span></span>

1.  <span data-ttu-id="16cc2-381">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="16cc2-382">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="16cc2-383">將腳本命名為**DataFromAnalytics**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="16cc2-384">按兩下腳本, 以 Visual Studio 開啟它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="16cc2-385">插入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="16cc2-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="16cc2-386">在腳本中, 插入下列內容:</span><span class="sxs-lookup"><span data-stu-id="16cc2-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="16cc2-387">在**DataFromAnalytics**類別內的**Start ()** 方法後面, 新增下列名為**FetchAnalytics ()** 的方法。</span><span class="sxs-lookup"><span data-stu-id="16cc2-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="16cc2-388">這個方法會負責填入機碼值組的清單, 以及一個*GameObject*和一個預留位置事件計數編號。</span><span class="sxs-lookup"><span data-stu-id="16cc2-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="16cc2-389">然後, 它會初始化**GetWebRequest ()** 協同程式。</span><span class="sxs-lookup"><span data-stu-id="16cc2-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="16cc2-390">您也可以在這個方法中找到*Application Insights*呼叫的查詢結構, 做為*查詢 URL*端點。</span><span class="sxs-lookup"><span data-stu-id="16cc2-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="16cc2-391">在**FetchAnalytics ()** 方法的右下方, 新增名為**GetWebRequest ()** 的方法, 它會傳回*IEnumerator*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="16cc2-392">這個方法會負責要求在*Application Insights*內呼叫事件 (對應于特定*GameObject*) 的次數。</span><span class="sxs-lookup"><span data-stu-id="16cc2-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="16cc2-393">當所有傳送的查詢都傳回時, 會呼叫**DetermineWinner ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="16cc2-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="16cc2-394">下一個方法是**DetermineWinner ()** , 它會根據最高的事件計數來排序*GameObject*和*Int*配對的清單。</span><span class="sxs-lookup"><span data-stu-id="16cc2-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="16cc2-395">然後, 它會將該*GameObject*的材質色彩變更為*綠色*(以最高計數的意見反應表示)。</span><span class="sxs-lookup"><span data-stu-id="16cc2-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="16cc2-396">這會顯示含有分析結果的訊息。</span><span class="sxs-lookup"><span data-stu-id="16cc2-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="16cc2-397">新增類別結構, 其將用來還原序列化從*Application Insights*接收的 JSON 物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="16cc2-398">在**DataFromAnalytics**類別檔案的最下方, 于類別定義**之外**新增這些類別。</span><span class="sxs-lookup"><span data-stu-id="16cc2-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="16cc2-399">請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="16cc2-400">第10章-建立移動類別</span><span class="sxs-lookup"><span data-stu-id="16cc2-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="16cc2-401">**移動**腳本是您將需要建立的下一個腳本。</span><span class="sxs-lookup"><span data-stu-id="16cc2-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="16cc2-402">它負責:</span><span class="sxs-lookup"><span data-stu-id="16cc2-402">It is responsible for:</span></span>

- <span data-ttu-id="16cc2-403">根據相機正在尋找的方向移動主要攝影機。</span><span class="sxs-lookup"><span data-stu-id="16cc2-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="16cc2-404">將所有其他腳本新增至場景物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="16cc2-405">若要建立腳本:</span><span class="sxs-lookup"><span data-stu-id="16cc2-405">To create the script:</span></span>

1.  <span data-ttu-id="16cc2-406">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="16cc2-407">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="16cc2-408">為腳本的**移動**命名。</span><span class="sxs-lookup"><span data-stu-id="16cc2-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="16cc2-409">按兩下腳本, 以*Visual Studio*開啟它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="16cc2-410">將現有的程式碼取代為下列內容:</span><span class="sxs-lookup"><span data-stu-id="16cc2-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="16cc2-411">在 move 類別內的空白**Update ()** 方法*底下*, 插入下列方法, 讓使用者可以使用手形控制器來移動虛擬空間:</span><span class="sxs-lookup"><span data-stu-id="16cc2-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="16cc2-412">最後, 在**Update ()** 方法內新增方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="16cc2-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="16cc2-413">請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="16cc2-414">第11章-設定腳本參考</span><span class="sxs-lookup"><span data-stu-id="16cc2-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="16cc2-415">在本章中, 您必須將**移動**腳本放在**相機父系**上, 並設定其參考目標。</span><span class="sxs-lookup"><span data-stu-id="16cc2-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="16cc2-416">接著, 該腳本會處理將其他腳本放在需要的位置。</span><span class="sxs-lookup"><span data-stu-id="16cc2-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="16cc2-417">從 [*專案] 面板*的 [**腳本**] 資料夾中, 將 [**移動**] 腳本拖曳至 [階層]*面板*中的 [**相機] 父**物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![在 Unity 場景中設定腳本參考](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="16cc2-419">按一下 [**相機] 父系**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="16cc2-420">在 [階層]*面板*中,**將右手**物件從 [階層]*面板*拖曳至 [偵測*器] 面板*中的參考目標**控制器**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="16cc2-421">將 [**使用者速度**] 設定為 [ **5**], 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="16cc2-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![在 Unity 場景中設定腳本參考](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="16cc2-423">第12章-建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="16cc2-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="16cc2-424">此專案的 Unity 區段所需的全部內容現在已經完成, 所以可以從 Unity 建立它。</span><span class="sxs-lookup"><span data-stu-id="16cc2-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="16cc2-425">流覽至 [**組建設定**]  > ([檔案**組建設定**])。</span><span class="sxs-lookup"><span data-stu-id="16cc2-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="16cc2-426">從 [**組建設定**] 視窗中, 按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-426">From the **Build Settings** window, click **Build**.</span></span>

    ![將 Unity 專案建立至 UWP 解決方案](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="16cc2-428">[檔案**瀏覽器**] 視窗隨即出現, 提示您輸入組建的位置。</span><span class="sxs-lookup"><span data-stu-id="16cc2-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="16cc2-429">建立新的資料夾 (按一下左上角的 [**新增資料夾**]), 並將其命名為**build**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![將 Unity 專案建立至 UWP 解決方案](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="16cc2-431">開啟 [新增**組建**] 資料夾, 然後建立另一個資料夾 (使用**新資料夾**一次), 並將其命名為 **\_MR Azure\_application\_Insights**。</span><span class="sxs-lookup"><span data-stu-id="16cc2-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![將 Unity 專案建立至 UWP 解決方案](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="16cc2-433">選取 [ **MR\_Azure\_ application\_Insights** ] 資料夾, 然後按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="16cc2-434">專案需要幾分鐘的時間才能建立。</span><span class="sxs-lookup"><span data-stu-id="16cc2-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="16cc2-435">在下列*組建*中, 會出現 [檔案**瀏覽器**], 顯示新專案的位置。</span><span class="sxs-lookup"><span data-stu-id="16cc2-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="16cc2-436">第13章-將 MR_Azure_Application_Insights 應用程式部署到您的電腦</span><span class="sxs-lookup"><span data-stu-id="16cc2-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="16cc2-437">若要在您的本機電腦上部署**MR\_Azure\_Application\_Insights**應用程式:</span><span class="sxs-lookup"><span data-stu-id="16cc2-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="16cc2-438">在**Visual Studio**中開啟**MR\_ \_Azure\_Application Insights**應用程式的方案檔。</span><span class="sxs-lookup"><span data-stu-id="16cc2-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="16cc2-439">在**解決方案平臺**中, 選取 [ **x86]、[本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="16cc2-440">在 [**解決方案**設定] 中, 選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![將 Unity 專案建立至 UWP 解決方案](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="16cc2-442">移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="16cc2-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="16cc2-443">您的應用程式現在應該會出現在已安裝的應用程式清單中, 並準備好啟動。</span><span class="sxs-lookup"><span data-stu-id="16cc2-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="16cc2-444">啟動混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="16cc2-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="16cc2-445">當*Azure 深入解析服務*收集到足夠的事件資料時, 在場景前後移動, 它會將已接近綠色的物件設為最多。</span><span class="sxs-lookup"><span data-stu-id="16cc2-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="16cc2-446">雖然服務收集*事件和計量*的平均等候時間大約需要15分鐘, 但在某些情況下, 可能需要多達1小時。</span><span class="sxs-lookup"><span data-stu-id="16cc2-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="16cc2-447">第14章-Application Insights 服務入口網站</span><span class="sxs-lookup"><span data-stu-id="16cc2-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="16cc2-448">在您漫遊場景並 gazed 數個物件之後, 您就可以看到*Application Insights 服務*入口網站中收集的資料。</span><span class="sxs-lookup"><span data-stu-id="16cc2-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="16cc2-449">回到您的 Application Insights 服務入口網站。</span><span class="sxs-lookup"><span data-stu-id="16cc2-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="16cc2-450">按一下 [*計量瀏覽器*]。</span><span class="sxs-lookup"><span data-stu-id="16cc2-450">Click on *Metrics Explorer*.</span></span>

    ![查看收集的資料](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="16cc2-452">它會在包含圖形的索引標籤中開啟, 代表與您的應用程式相關的*事件和計量*。</span><span class="sxs-lookup"><span data-stu-id="16cc2-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="16cc2-453">如上所述, 資料可能需要一段時間 (最多1小時) 才會顯示在圖形中</span><span class="sxs-lookup"><span data-stu-id="16cc2-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![查看收集的資料](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="16cc2-455">按一下 [依應用程式版本的*事件總數*] 中的 [*事件*] 列, 以查看事件的詳細細目及其名稱。</span><span class="sxs-lookup"><span data-stu-id="16cc2-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![查看收集的資料](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="16cc2-457">您已完成 Application Insights 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="16cc2-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="16cc2-458">恭喜, 您建立了一個混合現實應用程式, 利用 Application Insights 服務來監視應用程式中的使用者活動。</span><span class="sxs-lookup"><span data-stu-id="16cc2-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![課程結果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="16cc2-460">額外練習</span><span class="sxs-lookup"><span data-stu-id="16cc2-460">Bonus Exercises</span></span>

<span data-ttu-id="16cc2-461">**練習1**</span><span class="sxs-lookup"><span data-stu-id="16cc2-461">**Exercise 1**</span></span>

<span data-ttu-id="16cc2-462">嘗試產生, 而不是手動建立 ObjectInScene 物件, 並在腳本內的平面上設定其座標。</span><span class="sxs-lookup"><span data-stu-id="16cc2-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="16cc2-463">如此一來, 您可以向 Azure 詢問最受歡迎的物件是什麼 (從注視或相近的結果), 並產生一個*額外*的物件。</span><span class="sxs-lookup"><span data-stu-id="16cc2-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="16cc2-464">**練習2**</span><span class="sxs-lookup"><span data-stu-id="16cc2-464">**Exercise 2**</span></span>

<span data-ttu-id="16cc2-465">依時間排序您的 Application Insights 結果, 讓您取得最相關的資料, 並在您的應用程式中執行該時間的敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="16cc2-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

