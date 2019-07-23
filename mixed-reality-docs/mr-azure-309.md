---
title: MR 和 Azure 309-Application insights
description: 完成此課程來了解如何收集有關使用者行為，在混合的實境應用程式中，使用 Azure Application Insights 服務的分析。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 application insights、 hololens、 沉浸式 vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694564"
---
>[!NOTE]
><span data-ttu-id="ffbab-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="ffbab-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ffbab-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="ffbab-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ffbab-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="ffbab-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ffbab-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="ffbab-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ffbab-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="ffbab-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ffbab-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="ffbab-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="ffbab-110">MR 和 Azure 309:Application insights</span><span class="sxs-lookup"><span data-stu-id="ffbab-110">MR and Azure 309: Application insights</span></span>

![最終產品-開始](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="ffbab-112">在此課程中，您將了解如何將 Application Insights 功能新增至混合的實境應用程式，來收集有關使用者行為分析中使用 Azure Application Insights API。</span><span class="sxs-lookup"><span data-stu-id="ffbab-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="ffbab-113">Application Insights 是 Microsoft 服務，讓開發人員從其應用程式收集分析，並從方便使用入口網站進行管理。</span><span class="sxs-lookup"><span data-stu-id="ffbab-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="ffbab-114">分析可以是任何您想要收集的自訂資訊的效能。</span><span class="sxs-lookup"><span data-stu-id="ffbab-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="ffbab-115">如需詳細資訊，請瀏覽[Application Insights 頁面](https://azure.microsoft.com/services/application-insights/)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="ffbab-116">完成本課程之後，您必須能夠執行下列作業的混合的實境耳機沈浸式應用程式：</span><span class="sxs-lookup"><span data-stu-id="ffbab-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="ffbab-117">允許使用者視線和場景中四處移動。</span><span class="sxs-lookup"><span data-stu-id="ffbab-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="ffbab-118">觸發程序的分析，以傳送*Application Insights 服務*、 透過視線和場景中物件的鄰近性使用。</span><span class="sxs-lookup"><span data-stu-id="ffbab-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="ffbab-119">應用程式也會在服務中，擷取關於哪個物件已經過已由使用者最接近過去 24 小時內的資訊時呼叫。</span><span class="sxs-lookup"><span data-stu-id="ffbab-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="ffbab-120">該物件會將其色彩會變成綠色。</span><span class="sxs-lookup"><span data-stu-id="ffbab-120">That object will change its color to green.</span></span>

<span data-ttu-id="ffbab-121">本課程將教導您如何從 Application Insights 服務中，取得結果，到 Unity 為基礎的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffbab-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="ffbab-122">它會決定要將這些概念套用到您可能建置自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffbab-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="ffbab-123">裝置支援</span><span class="sxs-lookup"><span data-stu-id="ffbab-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ffbab-124">課程</span><span class="sxs-lookup"><span data-stu-id="ffbab-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ffbab-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ffbab-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ffbab-126"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="ffbab-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ffbab-127">MR 和 Azure 309:Application insights</span><span class="sxs-lookup"><span data-stu-id="ffbab-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="ffbab-128">✔️</span><span class="sxs-lookup"><span data-stu-id="ffbab-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ffbab-129">✔️</span><span class="sxs-lookup"><span data-stu-id="ffbab-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ffbab-130">雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。</span><span class="sxs-lookup"><span data-stu-id="ffbab-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ffbab-131">當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ffbab-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ffbab-132">當使用 HoloLens，您可能會發現某些回應語音擷取期間。</span><span class="sxs-lookup"><span data-stu-id="ffbab-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ffbab-133">先決條件</span><span class="sxs-lookup"><span data-stu-id="ffbab-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ffbab-134">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="ffbab-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ffbab-135">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。</span><span class="sxs-lookup"><span data-stu-id="ffbab-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="ffbab-136">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。</span><span class="sxs-lookup"><span data-stu-id="ffbab-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="ffbab-137">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="ffbab-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ffbab-138">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="ffbab-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ffbab-139">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="ffbab-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ffbab-140">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="ffbab-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ffbab-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="ffbab-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ffbab-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ffbab-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ffbab-143">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="ffbab-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ffbab-144">一組的耳機與內建的麥克風 （如果耳機並沒有內建的麥克風和喇叭）</span><span class="sxs-lookup"><span data-stu-id="ffbab-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="ffbab-145">針對 Azure 設定和 Application Insights 資料擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="ffbab-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ffbab-146">開始之前</span><span class="sxs-lookup"><span data-stu-id="ffbab-146">Before you start</span></span>

<span data-ttu-id="ffbab-147">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="ffbab-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="ffbab-148">請注意，資料流向*Application Insights*需要時間，因此請耐心等候。</span><span class="sxs-lookup"><span data-stu-id="ffbab-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="ffbab-149">如果您想要檢查如果此服務已收到您的資料，請參閱[第 14 章](#chapter-14---the-application-insights-service-portal)，這會告訴您如何瀏覽至入口網站。</span><span class="sxs-lookup"><span data-stu-id="ffbab-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="ffbab-150">第 1 章-Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="ffbab-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="ffbab-151">若要使用*Application Insights*，您必須建立及設定*Application Insights 服務*在 Azure 入口網站中。</span><span class="sxs-lookup"><span data-stu-id="ffbab-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="ffbab-152">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ffbab-153">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="ffbab-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ffbab-154">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="ffbab-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ffbab-155">一旦您登入，按一下**新增**在左上角，，然後搜尋*Application Insights*，然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ffbab-156">單字**的新**可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="ffbab-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="ffbab-158">向新的頁面將提供的描述*Azure Application Insights*服務。</span><span class="sxs-lookup"><span data-stu-id="ffbab-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="ffbab-159">在左下方的這個頁面上，選取**建立**按鈕，以建立與這個關聯服務。</span><span class="sxs-lookup"><span data-stu-id="ffbab-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="ffbab-161">一旦您按下 **建立** :</span><span class="sxs-lookup"><span data-stu-id="ffbab-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="ffbab-162">插入您想要**名稱**此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ffbab-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="ffbab-163">作為**應用程式類型**，選取**一般**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="ffbab-164">選取適當**訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="ffbab-165">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="ffbab-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ffbab-166">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="ffbab-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ffbab-167">建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。</span><span class="sxs-lookup"><span data-stu-id="ffbab-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="ffbab-168">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="ffbab-169">選取 **位置**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="ffbab-170">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="ffbab-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="ffbab-171">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="ffbab-171">Select **Create**.</span></span>

        ![Azure 入口網站](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="ffbab-173">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="ffbab-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="ffbab-174">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ffbab-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="ffbab-176">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ffbab-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="ffbab-178">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="ffbab-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ffbab-179">您將會被重新導向至新*Application Insights 服務*執行個體。</span><span class="sxs-lookup"><span data-stu-id="ffbab-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="ffbab-181">保持開啟這個 web 網頁，並很容易地存取，您會返回此處通常若要查看所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="ffbab-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ffbab-182">若要實作 Application Insights，您必須使用三 （3） 特定值：**檢測金鑰**，**應用程式識別碼**，以及**API 金鑰**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="ffbab-183">以下您將了解如何從您的服務中擷取這些值。</span><span class="sxs-lookup"><span data-stu-id="ffbab-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="ffbab-184">請務必記下這些值在空白*記事本*頁面上，因為您即將使用這些程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ffbab-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="ffbab-185">若要尋找**檢測金鑰**，您必須向下捲動服務功能的清單，然後按一下 **屬性**，顯示  索引標籤會顯示**服務金鑰**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="ffbab-187">以下有點**屬性**，您會發現**API 存取**，您需要按一下。</span><span class="sxs-lookup"><span data-stu-id="ffbab-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="ffbab-188">右側面板會提供**應用程式識別碼**應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffbab-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="ffbab-190">具有**應用程式識別碼**面板仍開啟時，按一下**建立 API 金鑰**，這會開啟*建立的 API 金鑰*面板。</span><span class="sxs-lookup"><span data-stu-id="ffbab-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="ffbab-192">現在開放內*建立的 API 金鑰* 面板中，輸入描述，以及**勾選三個方塊**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="ffbab-193">按一下 **產生金鑰**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-193">Click **Generate Key**.</span></span> <span data-ttu-id="ffbab-194">您**API 金鑰**會建立並顯示。</span><span class="sxs-lookup"><span data-stu-id="ffbab-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure 入口網站](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="ffbab-196">這是唯一的時候您**服務金鑰**隨即出現，因此請確定您現在建立一份。</span><span class="sxs-lookup"><span data-stu-id="ffbab-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="ffbab-197">第 2 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="ffbab-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="ffbab-198">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="ffbab-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ffbab-199">開啟*Unity*然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-199">Open *Unity* and click **New**.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="ffbab-201">您現在需要提供 Unity 專案名稱、 插入**MR\_Azure\_應用程式\_Insights**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="ffbab-202">請確定*樣板*設為**3D**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="ffbab-203">設定*位置*適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="ffbab-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ffbab-204">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-204">Then, click **Create project**.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="ffbab-206">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ffbab-207">移至**編輯\>喜好設定**，然後在新視窗中，瀏覽**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ffbab-208">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ffbab-209">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="ffbab-209">Close the **Preferences** window.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="ffbab-211">接下來，移至**檔案\>組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ffbab-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="ffbab-213">移至**檔案\>組建設定**並確定：</span><span class="sxs-lookup"><span data-stu-id="ffbab-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="ffbab-214">**裝置為目標**設為**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="ffbab-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="ffbab-215">對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="ffbab-216">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="ffbab-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="ffbab-217">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="ffbab-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="ffbab-218">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="ffbab-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="ffbab-219">儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="ffbab-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="ffbab-220">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ffbab-221">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="ffbab-221">A save window will appear.</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="ffbab-223">為此範例和任何未來的場景，請建立新的資料夾，然後按一下 **新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="ffbab-225">開啟您剛建立**場景**資料夾，然後在*檔案名稱：* 文字欄位中輸入**ApplicationInsightsScene**，然後按一下 **儲存**.</span><span class="sxs-lookup"><span data-stu-id="ffbab-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="ffbab-227">剩餘的設定，**組建設定**，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="ffbab-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="ffbab-228">中**組建設定**視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。</span><span class="sxs-lookup"><span data-stu-id="ffbab-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="ffbab-230">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="ffbab-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ffbab-231">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="ffbab-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ffbab-232">**指令碼** **執行階段版本**應該 **（.NET 4.6 對等） 的實驗性**，這會觸發程序需要重新啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="ffbab-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="ffbab-233">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="ffbab-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="ffbab-234">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="ffbab-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="ffbab-236">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="ffbab-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="ffbab-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ffbab-237">**InternetClient**</span></span>     

            ![設定 Unity 專案](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="ffbab-239">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed RealitySDK**加入。</span><span class="sxs-lookup"><span data-stu-id="ffbab-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="ffbab-241">回到**Build Settings**， **UnityC#專案**不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ffbab-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="ffbab-242">關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ffbab-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="ffbab-243">儲存您的場景和專案 (**檔案** > **儲存場景檔案** > **儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="ffbab-244">第 3 章-匯入 Unity 封裝</span><span class="sxs-lookup"><span data-stu-id="ffbab-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ffbab-245">如果您想要跳過*Unity 設定*元件，這些課程，並繼續直接進入程式碼，請自由下載此[Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)，它匯入到您的專案做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="ffbab-246">這也會包含從下一章中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="ffbab-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="ffbab-247">匯入之後，從繼續[**第 6 章**](#chapter-6---create-the-applicationinsightstracker-class)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ffbab-248">若要使用 Application Insights 在 Unity 內，您要匯入 DLL，以及 Newtonsoft DLL。</span><span class="sxs-lookup"><span data-stu-id="ffbab-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="ffbab-249">這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。</span><span class="sxs-lookup"><span data-stu-id="ffbab-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="ffbab-250">這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。</span><span class="sxs-lookup"><span data-stu-id="ffbab-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="ffbab-251">若要匯入到您自己專案的 Application Insights，請確定您已[下載 '.unitypackage'，其中包含外掛程式](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="ffbab-252">然後，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ffbab-252">Then, do the following:</span></span>

1.  <span data-ttu-id="ffbab-253">新增 **.unitypackage**若要使用的 Unity**資產\>匯入封裝\>自訂封裝**功能表選項。</span><span class="sxs-lookup"><span data-stu-id="ffbab-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="ffbab-254">在 **匯入 Unity 封裝**方塊會顯示。 請確認所有項目底下 （而且包括）**外掛程式**已選取。</span><span class="sxs-lookup"><span data-stu-id="ffbab-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="ffbab-256">按一下 **匯入**按鈕，將項目新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ffbab-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="ffbab-257">移至**Insights**下方的資料夾**外掛程式**專案中檢視，然後選取下列外掛程式*只*:</span><span class="sxs-lookup"><span data-stu-id="ffbab-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="ffbab-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="ffbab-258">Microsoft.ApplicationInsights</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="ffbab-260">與這個*外掛程式*選取，請確認**任何平台**是**unchecked**，然後確定**WSAPlayer**也**unchecked**，然後按一下**套用**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="ffbab-261">執行此動作只是要確認已正確設定檔案。</span><span class="sxs-lookup"><span data-stu-id="ffbab-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="ffbab-263">將標示這類的外掛程式，會設定它們僅適用於在 Unity 編輯器中。</span><span class="sxs-lookup"><span data-stu-id="ffbab-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="ffbab-264">有一組不同的專案會匯出從 Unity 後要使用 WSA 資料夾中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="ffbab-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="ffbab-265">接下來，您必須開啟**WSA**資料夾內**Insights**資料夾。</span><span class="sxs-lookup"><span data-stu-id="ffbab-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="ffbab-266">您會看到您剛才設定的相同檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="ffbab-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="ffbab-267">選取此檔案，並在偵測器中，確定該**任何平台**是**unchecked**，然後確定**只** **WSAPlayer**是**檢查**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="ffbab-268">按一下 **[套用]** 。</span><span class="sxs-lookup"><span data-stu-id="ffbab-268">Click **Apply**.</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="ffbab-270">您現在必須遵循**步驟 4-6**，但*Newtonsoft*外掛程式改。</span><span class="sxs-lookup"><span data-stu-id="ffbab-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="ffbab-271">請參閱以下螢幕擷取畫面的結果應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="ffbab-271">See the below screenshot for what the outcome should look like.</span></span>

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="ffbab-273">第 4 章-設定攝影機和使用者控制項</span><span class="sxs-lookup"><span data-stu-id="ffbab-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="ffbab-274">在這一章將設定觀景窗和控制項，以允許使用者查看，並在場景中移動。</span><span class="sxs-lookup"><span data-stu-id="ffbab-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="ffbab-275">以滑鼠右鍵按一下空白區域，在階層窗格中，然後**Create** > **空**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="ffbab-277">重新命名以新的空 GameObject**相機父**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="ffbab-279">以滑鼠右鍵按一下空白區域，在階層窗格中，然後**3D 物件**，然後在**球體**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="ffbab-280">重新命名球體**右手邊**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="ffbab-281">設定**轉換擴展**到右下的**0.1、 0.1、 0.1**</span><span class="sxs-lookup"><span data-stu-id="ffbab-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="ffbab-283">移除**球體 Collider**元件從按一下右手邊**齒輪**中*球體 Collider*元件，然後**移除元件**.</span><span class="sxs-lookup"><span data-stu-id="ffbab-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="ffbab-285">在 [階層] 面板拖曳**Main Camera**而**右手邊**物件上**相機父**物件。</span><span class="sxs-lookup"><span data-stu-id="ffbab-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="ffbab-287">設定**轉換的位置**兩個**Main Camera**並**右手邊**物件**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-31.png)

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="ffbab-290">第 5 章-設定 Unity 場景中的物件</span><span class="sxs-lookup"><span data-stu-id="ffbab-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="ffbab-291">您現在將建立一些基本的圖形的場景，使用者可以與之互動。</span><span class="sxs-lookup"><span data-stu-id="ffbab-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="ffbab-292">在中的空白區域按一下滑鼠右鍵*階層面板*，然後在**3D 物件**，然後選取**平面**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="ffbab-293">設定平面**轉換位置**要**0，-1，0**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="ffbab-294">設定平面**轉換擴展**要**5、 1、 5**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="ffbab-296">建立基本材質以搭配您**平面**物件，使您更輕鬆地查看其他圖形。</span><span class="sxs-lookup"><span data-stu-id="ffbab-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="ffbab-297">瀏覽至您 *[專案] 面板*，按一下滑鼠右鍵，然後**建立**，後面接著**資料夾**，以建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ffbab-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="ffbab-298">命名**材料**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-298">Name it **Materials**.</span></span>

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-34.png) ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="ffbab-301">開啟**材料**資料夾，然後按一下滑鼠右鍵，按一下**建立**，然後**材料**，以建立新的資料。</span><span class="sxs-lookup"><span data-stu-id="ffbab-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="ffbab-302">命名**藍色**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-302">Name it **Blue**.</span></span>

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-36.png) ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="ffbab-305">與新**藍色**，查看在選取的資料*Inspector*，按一下 [矩形] 視窗一起**Albedo**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="ffbab-306">選取藍色的色彩 (下一張圖片是**十六進位色彩：\#3592FFFF**)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="ffbab-307">選擇之後，請按一下 [關閉] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ffbab-307">Click the close button once you have chosen.</span></span>

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="ffbab-309">拖曳您新的內容，從**材料**拖曳至您新建立的資料夾**平面**，場景中 (或將其放在**平面**物件內*階層*)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="ffbab-311">在中的空白區域按一下滑鼠右鍵*階層面板*，然後在**3D 物件、 Capsule**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="ffbab-312">具有**Capsule**選取，變更其**轉換** *位置*至： **-10、 1、 0**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="ffbab-313">在中的空白區域按一下滑鼠右鍵*階層面板*，然後在**3D 物件、 Cube**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="ffbab-314">具有**Cube**選取，變更其**轉換** *位置*來：**0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="ffbab-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="ffbab-315">在中的空白區域按一下滑鼠右鍵*階層面板*，然後在**3D 物件、 球體**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="ffbab-316">具有 **球體** 選取，變更其 **轉換** *位置* 來：**10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="ffbab-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="ffbab-318">這些*位置*的值為*建議*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="ffbab-319">您可以自由設定到任何您想要的物件的位置，如果物件的距離太遠從相機是應用程式的使用者更容易。</span><span class="sxs-lookup"><span data-stu-id="ffbab-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="ffbab-320">當您的應用程式執行時，它必須能夠識別中的場景，為了達成此目的的物件，它們需要來加以標記。</span><span class="sxs-lookup"><span data-stu-id="ffbab-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="ffbab-321">選取其中一個物件，並在*Inspector* ] 面板中，按一下 [**新增標記...** ，這將會交換*Inspector*具有**標記 & 層**面板。</span><span class="sxs-lookup"><span data-stu-id="ffbab-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="ffbab-322">![設定 Unity 場景中的物件](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="ffbab-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="ffbab-323">按一下  **+ （加號）** 符號，然後輸入標記名稱為**ObjectInScene**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="ffbab-325">如果您使用不同的名稱，您的標記，您必須確保這項變更也為了*DataFromAnalytics*， *ObjectTrigger*，並*視線*，更新版本中，指令碼，讓您物件是找不到，而且偵測到，場景中。</span><span class="sxs-lookup"><span data-stu-id="ffbab-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="ffbab-326">建立的標記，您現在需要將它套用到所有三個物件。</span><span class="sxs-lookup"><span data-stu-id="ffbab-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="ffbab-327">從*階層*，保留**Shift**鍵，然後按一下  **Capsule**， **Cube**，以及**球體**，物件，然後在*Inspector*，按一下下拉式功能表中的，一起**標記**，然後按一下*ObjectInScene*標記您所建立。</span><span class="sxs-lookup"><span data-stu-id="ffbab-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="ffbab-328">![設定 Unity 場景中的物件](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="ffbab-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="ffbab-329">章節 6-建立 ApplicationInsightsTracker 類別</span><span class="sxs-lookup"><span data-stu-id="ffbab-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="ffbab-330">您必須建立第一個指令碼**ApplicationInsightsTracker**，它會負責：</span><span class="sxs-lookup"><span data-stu-id="ffbab-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="ffbab-331">建立根據使用者互動，以提交至 Azure Application Insights 的事件。</span><span class="sxs-lookup"><span data-stu-id="ffbab-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="ffbab-332">建立適當的事件名稱，根據使用者互動。</span><span class="sxs-lookup"><span data-stu-id="ffbab-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="ffbab-333">正在提交事件與 Application Insights 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="ffbab-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="ffbab-334">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ffbab-334">To create this class:</span></span>

1.  <span data-ttu-id="ffbab-335">以滑鼠右鍵按一下*專案 面板*，然後**建立** > **資料夾**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="ffbab-336">將資料夾命名**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-336">Name the folder **Scripts**.</span></span>

    ![建立 ApplicationInsightsTracker 類別](images/AzureLabs-Lab309-46.png)  ![建立 ApplicationInsightsTracker 類別](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="ffbab-339">具有**指令碼**建立資料夾，按兩下，以開啟。</span><span class="sxs-lookup"><span data-stu-id="ffbab-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="ffbab-340">然後，在該資料夾中，按一下滑鼠右鍵**Create**  >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="ffbab-341">指令碼命名**ApplicationInsightsTracker**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="ffbab-342">按兩下新**ApplicationInsightsTracker**指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="ffbab-343">更新命名空間頂端的 指令碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ffbab-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="ffbab-344">類別內插入下列變數：</span><span class="sxs-lookup"><span data-stu-id="ffbab-344">Inside the class insert the following variables:</span></span>

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
    > <span data-ttu-id="ffbab-345">設定**instrumentationKey，applicationId 和 API_Key**值適當地使用*服務金鑰*從 Azure 入口網站中所述[第 1 章](#chapter-1---the-azure-portal)，步驟 9及更新版本。</span><span class="sxs-lookup"><span data-stu-id="ffbab-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="ffbab-346">然後新增**start （)** 並**Awake()** 類別初始化時呼叫的方法：</span><span class="sxs-lookup"><span data-stu-id="ffbab-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="ffbab-347">新增方法負責傳送的事件與註冊您的應用程式的計量：</span><span class="sxs-lookup"><span data-stu-id="ffbab-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

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

8.  <span data-ttu-id="ffbab-348">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="ffbab-349">第 7-建立視線指令碼</span><span class="sxs-lookup"><span data-stu-id="ffbab-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="ffbab-350">下一步 以建立指令碼**視線**指令碼。</span><span class="sxs-lookup"><span data-stu-id="ffbab-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="ffbab-351">此指令碼會負責建立*Raycast* ，從將轉寄投影*Main Camera*，來偵測使用者查看的物件。</span><span class="sxs-lookup"><span data-stu-id="ffbab-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="ffbab-352">在此情況下， *Raycast*需要識別使用者查看的物件是否**ObjectInScene**標記，並計算多久使用者*gazes*在該物件。</span><span class="sxs-lookup"><span data-stu-id="ffbab-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="ffbab-353">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="ffbab-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ffbab-354">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ffbab-355">指令碼命名**視線**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="ffbab-356">按兩下要使用 Visual Studio 中開啟它的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ffbab-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="ffbab-357">以下列取代現有的程式碼：</span><span class="sxs-lookup"><span data-stu-id="ffbab-357">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="ffbab-358">程式碼**Awake()** 並**start （)** 方法現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="ffbab-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

6.  <span data-ttu-id="ffbab-359">內部**視線**類別中，新增下列程式碼**update （)** 方法，以專案*Raycast*並偵測目標叫用：</span><span class="sxs-lookup"><span data-stu-id="ffbab-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

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

7.  <span data-ttu-id="ffbab-360">新增**ResetFocusedObject()** 方法，將資料傳送至**Application Insights**當使用者已檢閱過的物件。</span><span class="sxs-lookup"><span data-stu-id="ffbab-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

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

8.  <span data-ttu-id="ffbab-361">您現在已完成**視線**指令碼。</span><span class="sxs-lookup"><span data-stu-id="ffbab-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="ffbab-362">您將變更儲存在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="ffbab-363">第 8-建立 ObjectTrigger 類別</span><span class="sxs-lookup"><span data-stu-id="ffbab-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="ffbab-364">您必須建立下一個指令碼是**ObjectTrigger**，它會負責：</span><span class="sxs-lookup"><span data-stu-id="ffbab-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="ffbab-365">新增到 Main Camera 的衝突所需的元件。</span><span class="sxs-lookup"><span data-stu-id="ffbab-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="ffbab-366">偵測相機是否標記為物件附近**ObjectInScene**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="ffbab-367">若要建立指令碼：</span><span class="sxs-lookup"><span data-stu-id="ffbab-367">To create the script:</span></span>

1.  <span data-ttu-id="ffbab-368">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="ffbab-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ffbab-369">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ffbab-370">指令碼命名**ObjectTrigger**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="ffbab-371">按兩下要使用 Visual Studio 中開啟它的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ffbab-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="ffbab-372">以下列取代現有的程式碼：</span><span class="sxs-lookup"><span data-stu-id="ffbab-372">Replace the existing code with the following:</span></span>

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

4.  <span data-ttu-id="ffbab-373">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="ffbab-374">第 9-建立 DataFromAnalytics 類別</span><span class="sxs-lookup"><span data-stu-id="ffbab-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="ffbab-375">您現在必須建立**DataFromAnalytics**指令碼，也就是負責：</span><span class="sxs-lookup"><span data-stu-id="ffbab-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="ffbab-376">正在擷取哪些物件已著手一同由相機最多的分析資料。</span><span class="sxs-lookup"><span data-stu-id="ffbab-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="ffbab-377">使用*服務金鑰*，可讓您的 Azure Application Insights 服務執行個體的通訊。</span><span class="sxs-lookup"><span data-stu-id="ffbab-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="ffbab-378">排序場景中的物件，根據具有最高的事件計數。</span><span class="sxs-lookup"><span data-stu-id="ffbab-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="ffbab-379">為變更材質的色彩，最 approached 物件的*綠色*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="ffbab-380">若要建立指令碼：</span><span class="sxs-lookup"><span data-stu-id="ffbab-380">To create the script:</span></span>

1.  <span data-ttu-id="ffbab-381">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="ffbab-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ffbab-382">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ffbab-383">指令碼命名**DataFromAnalytics**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="ffbab-384">按兩下要使用 Visual Studio 中開啟它的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ffbab-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="ffbab-385">插入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="ffbab-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="ffbab-386">在指令碼中，插入下列各項：</span><span class="sxs-lookup"><span data-stu-id="ffbab-386">Inside the script, insert the following:</span></span>

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

6.  <span data-ttu-id="ffbab-387">內**DataFromAnalytics**類別中，以滑鼠右鍵後**start （)** 方法，新增下列方法呼叫**FetchAnalytics()** 。</span><span class="sxs-lookup"><span data-stu-id="ffbab-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="ffbab-388">這個方法會負責的機碼值組清單已填入*GameObject*和預留位置事件計數數目。</span><span class="sxs-lookup"><span data-stu-id="ffbab-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="ffbab-389">然後初始化**GetWebRequest()** 協同程式。</span><span class="sxs-lookup"><span data-stu-id="ffbab-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="ffbab-390">若要呼叫的查詢結構*Application Insights*可以找到這個方法內同時，如同*查詢 URL*端點。</span><span class="sxs-lookup"><span data-stu-id="ffbab-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

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

7.  <span data-ttu-id="ffbab-391">正下方**FetchAnalytics()** 方法，新增一個方法，叫做**GetWebRequest()** ，就會傳回*IEnumerator*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="ffbab-392">這個方法會負責要求事件，且具有特定對應的次數*GameObject*，已呼叫內*Application Insights*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="ffbab-393">傳回所有已傳送的查詢，當**DetermineWinner()** 呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="ffbab-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

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

8.  <span data-ttu-id="ffbab-394">下一個方法是**DetermineWinner()** ，其排序的清單*GameObject*並*Int*組，根據最高的事件計數。</span><span class="sxs-lookup"><span data-stu-id="ffbab-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="ffbab-395">然後，會變更的材質的色彩*GameObject*要*綠色*（做為其具有最高計數的意見反應）。</span><span class="sxs-lookup"><span data-stu-id="ffbab-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="ffbab-396">這會顯示分析結果的訊息。</span><span class="sxs-lookup"><span data-stu-id="ffbab-396">This displays a message with the analytics results.</span></span>

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

9.  <span data-ttu-id="ffbab-397">新增將用於還原序列化 JSON 物件，從接收的類別結構*Application Insights*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="ffbab-398">在最下面加入這些類別您**DataFromAnalytics**類別檔案**外部**類別定義。</span><span class="sxs-lookup"><span data-stu-id="ffbab-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

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

10. <span data-ttu-id="ffbab-399">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="ffbab-400">第 10-建立移動類別</span><span class="sxs-lookup"><span data-stu-id="ffbab-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="ffbab-401">**移動**指令碼是您必須建立下一個指令碼。</span><span class="sxs-lookup"><span data-stu-id="ffbab-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="ffbab-402">它會負責：</span><span class="sxs-lookup"><span data-stu-id="ffbab-402">It is responsible for:</span></span>

- <span data-ttu-id="ffbab-403">移動觀景窗的方向根據 Main Camera 會正面朝向。</span><span class="sxs-lookup"><span data-stu-id="ffbab-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="ffbab-404">加入場景物件中的所有其他指令碼。</span><span class="sxs-lookup"><span data-stu-id="ffbab-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="ffbab-405">若要建立指令碼：</span><span class="sxs-lookup"><span data-stu-id="ffbab-405">To create the script:</span></span>

1.  <span data-ttu-id="ffbab-406">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="ffbab-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="ffbab-407">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ffbab-408">指令碼命名**移動**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="ffbab-409">按兩下要開啟它的指令碼*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="ffbab-410">以下列取代現有的程式碼：</span><span class="sxs-lookup"><span data-stu-id="ffbab-410">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="ffbab-411">內**移動**類別*以下*空白**update （)** 方法中，插入下列方法，可讓使用者使用手動控制站虛擬空間中移動：</span><span class="sxs-lookup"><span data-stu-id="ffbab-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

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

6.  <span data-ttu-id="ffbab-412">最後將加入在方法呼叫內**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="ffbab-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="ffbab-413">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="ffbab-414">第 11 章-設定指令碼參考</span><span class="sxs-lookup"><span data-stu-id="ffbab-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="ffbab-415">在本章中，您必須將放**移動**拖曳至指令碼**相機父**並設定其參考的目標。</span><span class="sxs-lookup"><span data-stu-id="ffbab-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="ffbab-416">該指令碼會接著處理放置其他指令碼能所需的位置。</span><span class="sxs-lookup"><span data-stu-id="ffbab-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="ffbab-417">從**指令碼**中的資料夾 *[專案] 面板*，拖曳**移動**指令碼來**相機父**中找到的物件*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![設定 Unity 場景中的指令碼參考](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="ffbab-419">按一下 **相機父**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="ffbab-420">在*階層面板*，拖曳**右手邊**物件*階層面板*至參考的目標，**控制器**中*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="ffbab-421">設定**使用者速度**要**5**，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ffbab-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![設定 Unity 場景中的指令碼參考](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="ffbab-423">第 12 章-建置 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="ffbab-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="ffbab-424">此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。</span><span class="sxs-lookup"><span data-stu-id="ffbab-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="ffbab-425">瀏覽至**組建設定**，(**檔案** > **組建設定**)。</span><span class="sxs-lookup"><span data-stu-id="ffbab-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="ffbab-426">從**Build Settings**  視窗中，按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-426">From the **Build Settings** window, click **Build**.</span></span>

    ![建置 Unity 專案至 UWP 方案](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="ffbab-428">A**檔案總管**視窗將會快顯視窗，提示您輸入組建的位置。</span><span class="sxs-lookup"><span data-stu-id="ffbab-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="ffbab-429">建立新的資料夾 (依序按一下**新的資料夾**左上角)，並將它命名**建置**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![建置 Unity 專案至 UWP 方案](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="ffbab-431">開啟新**組建**資料夾，並建立另一個資料夾 (使用**新資料夾**一次)，並將它命名**MR\_Azure\_應用程式\_Insights**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![建置 Unity 專案至 UWP 方案](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="ffbab-433">具有**MR\_Azure\_應用程式\_Insights**按一下 選取資料夾**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="ffbab-434">專案需要約一分鐘來建置。</span><span class="sxs-lookup"><span data-stu-id="ffbab-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="ffbab-435">遵循*建置*，**檔案總管**會出現顯示您的新專案的位置。</span><span class="sxs-lookup"><span data-stu-id="ffbab-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="ffbab-436">第 13 章-MR_Azure_Application_Insights 應用程式部署到您的電腦</span><span class="sxs-lookup"><span data-stu-id="ffbab-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="ffbab-437">若要部署**MR\_Azure\_應用程式\_Insights**本機電腦上的應用程式：</span><span class="sxs-lookup"><span data-stu-id="ffbab-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="ffbab-438">開啟的方案檔您**MR\_Azure\_應用程式\_Insights**中的應用程式**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="ffbab-439">在 **的方案平台**，選取**x86，本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="ffbab-440">在 **方案組態**選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="ffbab-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![建置 Unity 專案至 UWP 方案](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="ffbab-442">移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="ffbab-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="ffbab-443">您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。</span><span class="sxs-lookup"><span data-stu-id="ffbab-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="ffbab-444">啟動混合的實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffbab-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="ffbab-445">接近物件，並查看它們，場景中四處移動時*Azure Insight 服務*已收集足夠的事件資料，它將會設定已著手最多為綠色的物件。</span><span class="sxs-lookup"><span data-stu-id="ffbab-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="ffbab-446">雖然的平均等候時間*事件和度量*收集由服務需要大約 15 分鐘，在某些情況下可能需要最多 1 小時。</span><span class="sxs-lookup"><span data-stu-id="ffbab-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="ffbab-447">第 14 章-Application Insights 服務入口網站</span><span class="sxs-lookup"><span data-stu-id="ffbab-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="ffbab-448">當您將會漫遊周圍場景，而且 gazed 數個物件在您所見中收集的資料*Application Insights 服務*入口網站。</span><span class="sxs-lookup"><span data-stu-id="ffbab-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="ffbab-449">回到您的 Application Insights 服務入口網站。</span><span class="sxs-lookup"><span data-stu-id="ffbab-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="ffbab-450">按一下 *計量瀏覽器*。</span><span class="sxs-lookup"><span data-stu-id="ffbab-450">Click on *Metrics Explorer*.</span></span>

    ![查看所收集的資料](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="ffbab-452">它會包含代表圖形 索引標籤中開啟*事件和度量*應用程式相關。</span><span class="sxs-lookup"><span data-stu-id="ffbab-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="ffbab-453">如上所述，可能需要一些時間 （最多 1 小時），資料才會顯示在圖形</span><span class="sxs-lookup"><span data-stu-id="ffbab-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![查看所收集的資料](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="ffbab-455">按一下 *事件列*中*的事件總數*應用程式版本，若要查看的事件其名稱的詳細的細目。</span><span class="sxs-lookup"><span data-stu-id="ffbab-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![查看所收集的資料](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="ffbab-457">您已完成您的 Application Insights 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="ffbab-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="ffbab-458">恭喜，您所建立的混合的實境應用程式，利用 Application Insights 服務，來監視應用程式內的使用者的活動。</span><span class="sxs-lookup"><span data-stu-id="ffbab-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![課程結果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ffbab-460">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="ffbab-460">Bonus Exercises</span></span>

<span data-ttu-id="ffbab-461">**練習 1**</span><span class="sxs-lookup"><span data-stu-id="ffbab-461">**Exercise 1**</span></span>

<span data-ttu-id="ffbab-462">嘗試產生，而不是以手動方式建立 ObjectInScene 物件，並在指令碼內的平面上設定其座標。</span><span class="sxs-lookup"><span data-stu-id="ffbab-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="ffbab-463">如此一來，您可以要求 Azure 的最受歡迎的哪些物件已 （無論是從視線或相近的結果） 和繁衍*額外*其中一個物件。</span><span class="sxs-lookup"><span data-stu-id="ffbab-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="ffbab-464">**練習 2**</span><span class="sxs-lookup"><span data-stu-id="ffbab-464">**Exercise 2**</span></span>

<span data-ttu-id="ffbab-465">讓您取得最相關的資料，並在您的應用程式中實作該時間敏感的資料，則您可以依照時間，您的 Application Insights 結果。</span><span class="sxs-lookup"><span data-stu-id="ffbab-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

