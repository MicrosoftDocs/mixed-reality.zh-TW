---
title: MR 和 Azure 305-函式和儲存體
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 儲存體和函式。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 函式、 儲存體、 hololens、 vr 沈浸式，
ms.openlocfilehash: 5f3d0c6990249bc32e4c0f55c72dd884c4c2214e
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694551"
---
>[!NOTE]
><span data-ttu-id="6f58a-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="6f58a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="6f58a-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="6f58a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="6f58a-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="6f58a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="6f58a-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="6f58a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="6f58a-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="6f58a-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="6f58a-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="6f58a-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="6f58a-110">MR 和 Azure 305:函式和儲存體</span><span class="sxs-lookup"><span data-stu-id="6f58a-110">MR and Azure 305: Functions and storage</span></span>

![最終產品-開始](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="6f58a-112">在此課程中，您將學習如何建立和使用 Azure Functions 及儲存與 Azure 儲存體資源，在混合的實境應用程式中的資料。</span><span class="sxs-lookup"><span data-stu-id="6f58a-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="6f58a-113">*Azure Functions*是 Microsoft 服務，可讓開發人員執行程式碼片段，'函式'，在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="6f58a-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="6f58a-114">這可用來將工作委派給雲端，而不是您本機的應用程式，可以有許多優點。</span><span class="sxs-lookup"><span data-stu-id="6f58a-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="6f58a-115">*Azure Functions*支援數種開發語言，包括 C\#，F\#、 Node.js、 Java 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="6f58a-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="6f58a-116">如需詳細資訊，請瀏覽[Azure Functions 文件](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="6f58a-117">*Azure 儲存體*是 Microsoft 雲端服務，可讓開發人員可以使用儲存資料，它會是高度可用、 安全、 持久、 可擴充和備援的保險。</span><span class="sxs-lookup"><span data-stu-id="6f58a-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="6f58a-118">這表示 Microsoft 會為您處理所有的維護，以及關鍵的問題。</span><span class="sxs-lookup"><span data-stu-id="6f58a-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="6f58a-119">如需詳細資訊，請瀏覽[Azure 儲存體文章](https://docs.microsoft.com/azure/storage/common/storage-introduction)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="6f58a-120">完成本課程之後，您必須能夠執行下列作業的混合的實境耳機沈浸式應用程式：</span><span class="sxs-lookup"><span data-stu-id="6f58a-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="6f58a-121">允許使用者視線周圍的場景。</span><span class="sxs-lookup"><span data-stu-id="6f58a-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="6f58a-122">觸發程序繁衍 (sprawning) 物件時使用者 gazes 在 3D 'button'。</span><span class="sxs-lookup"><span data-stu-id="6f58a-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="6f58a-123">繁衍 （spawn） 的物件將會選擇 Azure 函式。</span><span class="sxs-lookup"><span data-stu-id="6f58a-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="6f58a-124">因為每個物件會繁衍，應用程式將會儲存中的物件型別*Azure 檔案*，位於*Azure 儲存體*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="6f58a-125">在第二次， *Azure 檔案*會擷取此項目，與用來重新執行先前的執行個體的應用程式的繁衍動作的資料。</span><span class="sxs-lookup"><span data-stu-id="6f58a-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="6f58a-126">在您的應用程式，則您對於如何將整合結果進行設計。</span><span class="sxs-lookup"><span data-stu-id="6f58a-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="6f58a-127">本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="6f58a-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="6f58a-128">它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。</span><span class="sxs-lookup"><span data-stu-id="6f58a-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="6f58a-129">裝置支援</span><span class="sxs-lookup"><span data-stu-id="6f58a-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="6f58a-130">課程</span><span class="sxs-lookup"><span data-stu-id="6f58a-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="6f58a-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6f58a-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6f58a-132"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="6f58a-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="6f58a-133">MR 和 Azure 305:函式和儲存體</span><span class="sxs-lookup"><span data-stu-id="6f58a-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="6f58a-134">✔️</span><span class="sxs-lookup"><span data-stu-id="6f58a-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6f58a-135">✔️</span><span class="sxs-lookup"><span data-stu-id="6f58a-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="6f58a-136">雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。</span><span class="sxs-lookup"><span data-stu-id="6f58a-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="6f58a-137">當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6f58a-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f58a-138">先決條件</span><span class="sxs-lookup"><span data-stu-id="6f58a-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="6f58a-139">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="6f58a-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="6f58a-140">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="6f58a-141">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊會完全符合您會發現在較新的軟體與以下所列內容.</span><span class="sxs-lookup"><span data-stu-id="6f58a-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="6f58a-142">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="6f58a-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="6f58a-143">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="6f58a-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="6f58a-144">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="6f58a-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="6f58a-145">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="6f58a-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="6f58a-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="6f58a-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="6f58a-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="6f58a-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="6f58a-148">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="6f58a-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="6f58a-149">建立 Azure 資源的 Azure 帳戶的訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="6f58a-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="6f58a-150">Azure 的安裝程式和資料擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="6f58a-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="6f58a-151">開始之前</span><span class="sxs-lookup"><span data-stu-id="6f58a-151">Before you start</span></span>

<span data-ttu-id="6f58a-152">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="6f58a-153">第 1 章-Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="6f58a-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="6f58a-154">若要使用**Azure 儲存體服務**，您必須建立及設定**儲存體帳戶**在 Azure 入口網站中。</span><span class="sxs-lookup"><span data-stu-id="6f58a-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="6f58a-155">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="6f58a-156">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="6f58a-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="6f58a-157">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="6f58a-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="6f58a-158">一旦您登入，按一下**新增**在左上角，，然後搜尋*儲存體帳戶*，然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![azure 儲存體搜尋](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="6f58a-160">單字**的新**可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="6f58a-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="6f58a-161">新的頁面將提供的描述*Azure 儲存體帳戶*服務。</span><span class="sxs-lookup"><span data-stu-id="6f58a-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="6f58a-162">在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="6f58a-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![建立服務](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="6f58a-164">一旦您按下 **建立** :</span><span class="sxs-lookup"><span data-stu-id="6f58a-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="6f58a-165">插入*名稱*您的帳戶，請留意這個欄位只接受數字和小寫字母。</span><span class="sxs-lookup"><span data-stu-id="6f58a-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="6f58a-166">針對*部署模型*，選取**Resource manager**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="6f58a-167">針對*帳戶種類*，選取**儲存體 (一般用途 v1)** 。</span><span class="sxs-lookup"><span data-stu-id="6f58a-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="6f58a-168">判斷*位置*資源群組 （如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="6f58a-169">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="6f58a-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="6f58a-170">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="6f58a-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="6f58a-171">針對*複寫*選取**讀取-存取-異地備援儲存體 (RA-GRS)** 。</span><span class="sxs-lookup"><span data-stu-id="6f58a-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="6f58a-172">針對*效能*，選取**標準**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="6f58a-173">離開*需要安全傳輸*作為**停用**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="6f58a-174">選取 *訂用帳戶*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="6f58a-175">選擇*資源群組*或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="6f58a-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="6f58a-176">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="6f58a-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="6f58a-177">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="6f58a-178">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="6f58a-179">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="6f58a-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="6f58a-180">選取 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="6f58a-180">Select **Create**.</span></span>

        ![輸入的服務資訊](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="6f58a-182">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="6f58a-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="6f58a-183">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f58a-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![在 azure 入口網站中的新通知](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="6f58a-185">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f58a-185">Click on the notifications to explore your new Service instance.</span></span>

    ![前往資源](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="6f58a-187">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f58a-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="6f58a-188">您將會被重新導向至新*儲存體帳戶*服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f58a-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![存取金鑰](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="6f58a-190">按一下 *存取金鑰*，以顯示此雲端服務的端點。</span><span class="sxs-lookup"><span data-stu-id="6f58a-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="6f58a-191">使用 *記事本*或類似檔案，以供稍後使用其中一個金鑰複本。</span><span class="sxs-lookup"><span data-stu-id="6f58a-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="6f58a-192">另請注意*連接字串*值，因為您將會用於*所需的 AzureServices*類別，您將在稍後建立。</span><span class="sxs-lookup"><span data-stu-id="6f58a-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![複製連接字串](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="6f58a-194">第 2 章-設定 Azure 函式</span><span class="sxs-lookup"><span data-stu-id="6f58a-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="6f58a-195">現在您將撰寫**Azure** **函式**的 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="6f58a-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="6f58a-196">您可以使用**Azure Function**執行幾乎任何項目，也就與傳統的函式在程式碼中，差異在於，此函式可以存取任何應用程式具有存取您的 Azure 帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="6f58a-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="6f58a-197">若要建立 Azure 函式：</span><span class="sxs-lookup"><span data-stu-id="6f58a-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="6f58a-198">從您*Azure 入口網站*，按一下**新增**在左上角，，並搜尋*函式應用程式*，然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![建立函數應用程式](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="6f58a-200">單字**的新**可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="6f58a-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="6f58a-201">新的頁面將提供的描述*Azure 函數應用程式*服務。</span><span class="sxs-lookup"><span data-stu-id="6f58a-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="6f58a-202">在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="6f58a-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![函式應用程式資訊](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="6f58a-204">一旦您按下 **建立** :</span><span class="sxs-lookup"><span data-stu-id="6f58a-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="6f58a-205">提供*應用程式名稱*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-205">Provide an *App name*.</span></span> <span data-ttu-id="6f58a-206">字母和數字此處只能使用 （允許上限或下限的大小寫）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="6f58a-207">選取您偏好*訂用帳戶*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="6f58a-208">選擇*資源群組*或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="6f58a-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="6f58a-209">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="6f58a-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="6f58a-210">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="6f58a-211">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="6f58a-212">針對此練習中，選取*Windows*為所選**OS**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="6f58a-213">選取 *耗用量計劃*for**主控方案**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="6f58a-214">判斷*位置*資源群組 （如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="6f58a-215">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="6f58a-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="6f58a-216">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="6f58a-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="6f58a-217">為了達到最佳效能，選取 儲存體帳戶相同的區域。</span><span class="sxs-lookup"><span data-stu-id="6f58a-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="6f58a-218">針對*儲存體*，選取**使用現有**，然後使用下拉式功能表中，尋找您先前建立的儲存體。</span><span class="sxs-lookup"><span data-stu-id="6f58a-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="6f58a-219">離開*Application Insights*關閉這項練習。</span><span class="sxs-lookup"><span data-stu-id="6f58a-219">Leave *Application Insights* off for this exercise.</span></span>

        ![輸入函式應用程式詳細資料](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="6f58a-221">按一下 [建立]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f58a-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="6f58a-222">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="6f58a-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="6f58a-223">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f58a-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新的 azure 入口網站通知](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="6f58a-225">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f58a-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![移至資源函式應用程式](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="6f58a-227">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f58a-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="6f58a-228">您將會被重新導向至新*函式應用程式*服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f58a-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="6f58a-229">在上*函式應用程式*儀表板，將滑鼠移*函式*，在左側面板中找到，然後按一下 **+ （加號）** 符號。</span><span class="sxs-lookup"><span data-stu-id="6f58a-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![建立新的函式](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="6f58a-231">在下一步 頁面上，確定**Webhook + API**已選取，至於*選擇的語言，* 選取**CSharp**，因為這是本教學課程中所使用的語言。</span><span class="sxs-lookup"><span data-stu-id="6f58a-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="6f58a-232">最後，按一下**建立此函式** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f58a-232">Lastly, click the **Create this function** button.</span></span>

    ![選取 web hook csharp](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="6f58a-234">您應該會進入程式碼頁面 (run.csx)，如果沒有，按一下左側面板中的 [函數] 清單中新建立的函式。</span><span class="sxs-lookup"><span data-stu-id="6f58a-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![開啟新的函式](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="6f58a-236">將下列程式碼複製到您的函式中。</span><span class="sxs-lookup"><span data-stu-id="6f58a-236">Copy the following code into your function.</span></span> <span data-ttu-id="6f58a-237">此函式只會傳回隨機整數，介於 0 和 2 時呼叫。</span><span class="sxs-lookup"><span data-stu-id="6f58a-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="6f58a-238">請勿擔心現有的程式碼，歡迎您貼上至頂端。</span><span class="sxs-lookup"><span data-stu-id="6f58a-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="6f58a-239">選取 \[儲存\]  。</span><span class="sxs-lookup"><span data-stu-id="6f58a-239">Select **Save**.</span></span>

14. <span data-ttu-id="6f58a-240">結果看起來應該像下列映像。</span><span class="sxs-lookup"><span data-stu-id="6f58a-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="6f58a-241">按一下 **取得函式 URL**並記*端點*顯示。</span><span class="sxs-lookup"><span data-stu-id="6f58a-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="6f58a-242">您必須將它插入*所需的 AzureServices*稍後在本課程中，您將建立的類別。</span><span class="sxs-lookup"><span data-stu-id="6f58a-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![取得函式端點](images/AzureLabs-Lab5-16.png)

    ![取得函式端點](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="6f58a-245">第 3 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="6f58a-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="6f58a-246">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="6f58a-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="6f58a-247">設定並測試您的混合的實境沈浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="6f58a-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="6f58a-248">您將會**不**本課程所需動作的控制器。</span><span class="sxs-lookup"><span data-stu-id="6f58a-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="6f58a-249">如果您需要支援沈浸式耳機的設定，請[瀏覽設定發行項的混合的實境](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="6f58a-250">開啟 Unity，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-250">Open Unity and click **New**.</span></span>

    ![建立新的 unity 專案](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="6f58a-252">您現在必須提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="6f58a-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="6f58a-253">插入**MR_Azure_Functions**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="6f58a-254">請確定專案類型設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="6f58a-255">設定*位置*適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="6f58a-256">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-256">Then, click **Create project**.</span></span>

    ![指定新的 unity 專案的名稱](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="6f58a-258">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="6f58a-259">移至**編輯** > **喜好設定**並從新的視窗，然後瀏覽至**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="6f58a-260">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="6f58a-261">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="6f58a-261">Close the **Preferences** window.</span></span>

    ![設定 visual studio，為指令碼編輯器](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="6f58a-263">接下來，移至**檔案** > **組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f58a-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![切換至 uwp 的平台](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="6f58a-265">移至**檔案** > **組建設定**並確定：</span><span class="sxs-lookup"><span data-stu-id="6f58a-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="6f58a-266">**裝置為目標**設定為**任何裝置**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="6f58a-267">對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="6f58a-268">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="6f58a-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="6f58a-269">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="6f58a-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="6f58a-270">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="6f58a-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="6f58a-271">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="6f58a-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="6f58a-272">儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="6f58a-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="6f58a-273">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="6f58a-274">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="6f58a-274">A save window will appear.</span></span>

            ![將開啟的場景新增](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="6f58a-276">建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立場景資料夾](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="6f58a-278">開啟您剛建立**場景**資料夾，然後在**檔案名稱：** 文字欄位中輸入**FunctionsScene**，然後按**儲存**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![儲存函式場景](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="6f58a-280">剩餘的設定，**組建設定**，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="6f58a-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![儲存函式場景](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="6f58a-282">中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。</span><span class="sxs-lookup"><span data-stu-id="6f58a-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![偵測器中的播放程式設定](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="6f58a-284">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="6f58a-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="6f58a-285">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="6f58a-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="6f58a-286">**指令碼執行階段版本**應該**實驗性**（.NET 4.6 對等），這會觸發程序需要重新啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="6f58a-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="6f58a-287">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="6f58a-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="6f58a-288">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="6f58a-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="6f58a-289">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="6f58a-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="6f58a-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="6f58a-290">**InternetClient**</span></span>

            ![設定功能](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="6f58a-292">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed RealitySDK**加入。</span><span class="sxs-lookup"><span data-stu-id="6f58a-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![設定 XR 設定](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="6f58a-294">回到*Build Settings* *UnityC#專案*不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6f58a-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![刻度 c# 專案](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="6f58a-296">關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="6f58a-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="6f58a-297">儲存您的場景和專案 (**檔案** > **儲存場景檔案** > **儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-297">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="6f58a-298">第 4 章-安裝主攝影機</span><span class="sxs-lookup"><span data-stu-id="6f58a-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f58a-299">如果您想要跳過*Unity 設定*元件的課程，並直接在程式碼中繼續進行，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)，然後匯入您的專案做為[自訂封裝](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="6f58a-300">這也會包含從下一章中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="6f58a-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="6f58a-301">匯入之後，從繼續[第 7 章](#chapter-7---create-the-azureservices-class)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="6f58a-302">在 *階層面板*，您會發現呼叫物件**Main Camera**，這個物件代表您的 「 主要 」 觀點來看，當您 「 內部 」 您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f58a-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="6f58a-303">您面前的 Unity 儀表板中，選取**主攝影機 GameObject**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="6f58a-304">您將會發現*偵測器 面板*（通常是到右方時，儀表板中找到） 將會顯示各種元件的*GameObject*，使用*轉換*在頂端，後面接著*相機*，和一些其他元件。</span><span class="sxs-lookup"><span data-stu-id="6f58a-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="6f58a-305">您必須重設主攝影機的轉換，以便正確地定位。</span><span class="sxs-lookup"><span data-stu-id="6f58a-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="6f58a-306">若要這樣做，請選取**齒輪**相機的旁邊的圖示*轉換*元件，然後選取**重設**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![重設轉換](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="6f58a-308">然後更新**轉換**元件如下：</span><span class="sxs-lookup"><span data-stu-id="6f58a-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="6f58a-309">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="6f58a-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="6f58a-310">**X**</span><span class="sxs-lookup"><span data-stu-id="6f58a-310">**X**</span></span>   | <span data-ttu-id="6f58a-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="6f58a-311">**Y**</span></span>                     | <span data-ttu-id="6f58a-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="6f58a-312">**Z**</span></span> |
    | <span data-ttu-id="6f58a-313">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-313">0</span></span>       | <span data-ttu-id="6f58a-314">1</span><span class="sxs-lookup"><span data-stu-id="6f58a-314">1</span></span>                         | <span data-ttu-id="6f58a-315">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-315">0</span></span>     |    

    |       | <span data-ttu-id="6f58a-316">轉換的旋轉</span><span class="sxs-lookup"><span data-stu-id="6f58a-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="6f58a-317">**X**</span><span class="sxs-lookup"><span data-stu-id="6f58a-317">**X**</span></span> | <span data-ttu-id="6f58a-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="6f58a-318">**Y**</span></span>                | <span data-ttu-id="6f58a-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="6f58a-319">**Z**</span></span> |
    | <span data-ttu-id="6f58a-320">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-320">0</span></span>     | <span data-ttu-id="6f58a-321">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-321">0</span></span>                    | <span data-ttu-id="6f58a-322">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-322">0</span></span>     |

    |       | <span data-ttu-id="6f58a-323">轉換為小數位數</span><span class="sxs-lookup"><span data-stu-id="6f58a-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="6f58a-324">**X**</span><span class="sxs-lookup"><span data-stu-id="6f58a-324">**X**</span></span> | <span data-ttu-id="6f58a-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="6f58a-325">**Y**</span></span>             | <span data-ttu-id="6f58a-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="6f58a-326">**Z**</span></span> |
    | <span data-ttu-id="6f58a-327">1</span><span class="sxs-lookup"><span data-stu-id="6f58a-327">1</span></span>     | <span data-ttu-id="6f58a-328">1</span><span class="sxs-lookup"><span data-stu-id="6f58a-328">1</span></span>                 | <span data-ttu-id="6f58a-329">1</span><span class="sxs-lookup"><span data-stu-id="6f58a-329">1</span></span>     |

    ![設定觀景窗轉換](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="6f58a-331">第 5 章-設定 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="6f58a-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="6f58a-332">中的空白區域上按一下滑鼠右鍵*階層面板*下方**3D 物件**，加入**平面**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![建立新的平面](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="6f58a-334">具有**平面**物件選取、 變更中的下列參數*Inspector 面板*:</span><span class="sxs-lookup"><span data-stu-id="6f58a-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="6f58a-335">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="6f58a-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="6f58a-336">**X**</span><span class="sxs-lookup"><span data-stu-id="6f58a-336">**X**</span></span> | <span data-ttu-id="6f58a-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="6f58a-337">**Y**</span></span>                | <span data-ttu-id="6f58a-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="6f58a-338">**Z**</span></span> |
    | <span data-ttu-id="6f58a-339">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-339">0</span></span>     | <span data-ttu-id="6f58a-340">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-340">0</span></span>                    | <span data-ttu-id="6f58a-341">4</span><span class="sxs-lookup"><span data-stu-id="6f58a-341">4</span></span>     |

    |       | <span data-ttu-id="6f58a-342">轉換為小數位數</span><span class="sxs-lookup"><span data-stu-id="6f58a-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="6f58a-343">**X**</span><span class="sxs-lookup"><span data-stu-id="6f58a-343">**X**</span></span> | <span data-ttu-id="6f58a-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="6f58a-344">**Y**</span></span>             | <span data-ttu-id="6f58a-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="6f58a-345">**Z**</span></span> |
    | <span data-ttu-id="6f58a-346">10</span><span class="sxs-lookup"><span data-stu-id="6f58a-346">10</span></span>    | <span data-ttu-id="6f58a-347">1</span><span class="sxs-lookup"><span data-stu-id="6f58a-347">1</span></span>                 | <span data-ttu-id="6f58a-348">10</span><span class="sxs-lookup"><span data-stu-id="6f58a-348">10</span></span>    |

    ![設定平面位置和比例](images/AzureLabs-Lab5-32.png)

    ![平面的場景檢視](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="6f58a-351">中的空白區域上按一下滑鼠右鍵*階層面板*下方**3D 物件**，加入**Cube**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="6f58a-352">重新命名 Cube **GazeButton** （與所選取的 Cube，請按 'F2'）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="6f58a-353">變更中的下列參數*Inspector 面板*:</span><span class="sxs-lookup"><span data-stu-id="6f58a-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="6f58a-354">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="6f58a-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="6f58a-355">**X**</span><span class="sxs-lookup"><span data-stu-id="6f58a-355">**X**</span></span> | <span data-ttu-id="6f58a-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="6f58a-356">**Y**</span></span>                | <span data-ttu-id="6f58a-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="6f58a-357">**Z**</span></span> |
        | <span data-ttu-id="6f58a-358">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-358">0</span></span>     | <span data-ttu-id="6f58a-359">3</span><span class="sxs-lookup"><span data-stu-id="6f58a-359">3</span></span>                    | <span data-ttu-id="6f58a-360">5</span><span class="sxs-lookup"><span data-stu-id="6f58a-360">5</span></span>     |


        ![設定視線按鈕轉換](images/AzureLabs-Lab5-34.png)

        ![視線按鈕場景檢視](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="6f58a-363">按一下 **標記**下拉式按鈕，然後按一下 **新增標記**以開啟*標記和圖層 窗格*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![加入新的標記](images/AzureLabs-Lab5-36.png)

        ![選取加號](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="6f58a-366">選取 [ **+ （加號）** ] 按鈕，然後在*新的標記名稱*欄位中，輸入**GazeButton**，然後按**儲存**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![名稱的新標記](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="6f58a-368">按一下 [ **GazeButton**物件中*階層面板*，然後在*偵測器] 面板*，指派新建立**GazeButton**標記。</span><span class="sxs-lookup"><span data-stu-id="6f58a-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![將新的標籤指定視線按鈕](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="6f58a-370">以滑鼠右鍵按一下**GazeButton**物件，在*階層面板*，並新增**空 GameObject** (這將會新增為*子*物件）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="6f58a-371">選取新的物件，然後將它重新命名**ShapeSpawnPoint**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="6f58a-372">變更中的下列參數*Inspector 面板*:</span><span class="sxs-lookup"><span data-stu-id="6f58a-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="6f58a-373">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="6f58a-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="6f58a-374">**X**</span><span class="sxs-lookup"><span data-stu-id="6f58a-374">**X**</span></span> |<span data-ttu-id="6f58a-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="6f58a-375">**Y**</span></span>                 | <span data-ttu-id="6f58a-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="6f58a-376">**Z**</span></span> |
        | <span data-ttu-id="6f58a-377">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-377">0</span></span>     | <span data-ttu-id="6f58a-378">-1</span><span class="sxs-lookup"><span data-stu-id="6f58a-378">-1</span></span>                   | <span data-ttu-id="6f58a-379">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-379">0</span></span>     |

        ![更新圖案繁衍點轉換](images/AzureLabs-Lab5-40.png)

        ![圖形繁衍點場景檢視](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="6f58a-382">接下來，您會建立**3D 文字**来提供意見反應對 Azure 服務之狀態物件。</span><span class="sxs-lookup"><span data-stu-id="6f58a-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="6f58a-383">以滑鼠右鍵按一下**GazeButton**階層中面板 一次，並新增**3D 物件** > **3D 文字**物件當做*子*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child*.</span></span>

    ![建立新的 3D 文字物件](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="6f58a-385">重新命名**3D 文字**物件**AzureStatusText**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="6f58a-386">變更**AzureStatusText**物件轉換，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f58a-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="6f58a-387">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="6f58a-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="6f58a-388">**X**</span><span class="sxs-lookup"><span data-stu-id="6f58a-388">**X**</span></span> | <span data-ttu-id="6f58a-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="6f58a-389">**Y**</span></span>                | <span data-ttu-id="6f58a-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="6f58a-390">**Z**</span></span> |
    | <span data-ttu-id="6f58a-391">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-391">0</span></span>     | <span data-ttu-id="6f58a-392">0</span><span class="sxs-lookup"><span data-stu-id="6f58a-392">0</span></span>                    | <span data-ttu-id="6f58a-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="6f58a-393">-0.6</span></span>  |

    |       | <span data-ttu-id="6f58a-394">轉換為小數位數</span><span class="sxs-lookup"><span data-stu-id="6f58a-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="6f58a-395">**X**</span><span class="sxs-lookup"><span data-stu-id="6f58a-395">**X**</span></span> | <span data-ttu-id="6f58a-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="6f58a-396">**Y**</span></span>             | <span data-ttu-id="6f58a-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="6f58a-397">**Z**</span></span> |
    | <span data-ttu-id="6f58a-398">0.1</span><span class="sxs-lookup"><span data-stu-id="6f58a-398">0.1</span></span>   | <span data-ttu-id="6f58a-399">0.1</span><span class="sxs-lookup"><span data-stu-id="6f58a-399">0.1</span></span>               | <span data-ttu-id="6f58a-400">0.1</span><span class="sxs-lookup"><span data-stu-id="6f58a-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="6f58a-401">請勿擔心，如果它似乎是關閉中心，因為這將會修正當下方文字 Mesh 更新元件。</span><span class="sxs-lookup"><span data-stu-id="6f58a-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="6f58a-402">變更**文字 Mesh**來比對的元件如下：</span><span class="sxs-lookup"><span data-stu-id="6f58a-402">Change the **Text Mesh** component to match the below:</span></span>

    ![設定文字網狀結構元件](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="6f58a-404">選取的色彩是十六進位色彩：**000000FF**，但是請放心選擇自己，只要確定它是可讀取。</span><span class="sxs-lookup"><span data-stu-id="6f58a-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="6f58a-405">您的階層面板結構現在看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="6f58a-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![mesh 場景檢視中的文字](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="6f58a-407">場景現在看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="6f58a-407">Your scene should now look like this:</span></span>

    ![mesh 場景檢視中的文字](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="6f58a-409">第 6 章-匯入 Unity 的 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="6f58a-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="6f58a-410">您將針對 Unity 使用 Azure 儲存體 （而其本身會利用.Net SDK for Azure）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="6f58a-411">您可以深入了解這在[Unity 文件的 Azure 儲存體](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="6f58a-412">這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。</span><span class="sxs-lookup"><span data-stu-id="6f58a-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="6f58a-413">這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。</span><span class="sxs-lookup"><span data-stu-id="6f58a-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="6f58a-414">若要 SDK 匯入您自己的專案，請確定您已下載最新[從 GitHub '.unitypackage](https://aka.ms/azstorage-unitysdk)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="6f58a-415">然後，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="6f58a-415">Then, do the following:</span></span>

1.  <span data-ttu-id="6f58a-416">新增 **.unitypackage** unity 所使用的檔案**資產** > **匯入封裝** > **自訂封裝**功能表選項。</span><span class="sxs-lookup"><span data-stu-id="6f58a-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="6f58a-417">在 **匯入 Unity 封裝**方塊，顯示，您可以選取下方的所有內容**外掛程式** > **儲存體**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span> <span data-ttu-id="6f58a-418">取消選取所有項目不需要這堂課程。</span><span class="sxs-lookup"><span data-stu-id="6f58a-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![匯入封裝](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="6f58a-420">按一下 **匯入**按鈕以新增至您的專案項目。</span><span class="sxs-lookup"><span data-stu-id="6f58a-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="6f58a-421">移至*儲存體*下方的資料夾*外掛程式*，接著在專案檢視 中，選取下列外掛程式*只*:</span><span class="sxs-lookup"><span data-stu-id="6f58a-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="6f58a-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="6f58a-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="6f58a-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="6f58a-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="6f58a-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="6f58a-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="6f58a-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="6f58a-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="6f58a-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="6f58a-426">System.Spatial</span></span>

        ![取消選取任何平台](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="6f58a-428">具有*這些特定的外掛程式*選取，**取消核取\*\**任何平台*並**取消核取\*\* *WSAPlayer*然後按一下**套用**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![適用於平台的 dll](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="6f58a-430">我們會將標示要僅適用於在 Unity 編輯器中的這些特定外掛程式。</span><span class="sxs-lookup"><span data-stu-id="6f58a-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="6f58a-431">這是因為有不同版本的專案會匯出從 Unity 後要使用 WSA 資料夾中的同一個外掛程式。</span><span class="sxs-lookup"><span data-stu-id="6f58a-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="6f58a-432">在 *儲存體*外掛程式資料夾中，只選取：</span><span class="sxs-lookup"><span data-stu-id="6f58a-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="6f58a-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="6f58a-433">Microsoft.Data.Services.Client</span></span>

        ![dll 不會處理集合](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="6f58a-435">請檢查**不處理程序**下方*平台設定*，按一下 **套用**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![適用於任何處理](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="6f58a-437">我們會將標示此外掛程式 」 不會處理 」 的 Unity 組件修補程式發生無法處理此外掛程式。</span><span class="sxs-lookup"><span data-stu-id="6f58a-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="6f58a-438">即使它不會處理此外掛程式仍然可以運作。</span><span class="sxs-lookup"><span data-stu-id="6f58a-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="6f58a-439">第 7-建立所需的 AzureServices 類別</span><span class="sxs-lookup"><span data-stu-id="6f58a-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="6f58a-440">您即將建立的第一個類別是*所需的 AzureServices*類別。</span><span class="sxs-lookup"><span data-stu-id="6f58a-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="6f58a-441">*所需的 AzureServices*類別會負責：</span><span class="sxs-lookup"><span data-stu-id="6f58a-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="6f58a-442">儲存 Azure 帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="6f58a-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="6f58a-443">呼叫您的 Azure 應用程式函式。</span><span class="sxs-lookup"><span data-stu-id="6f58a-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="6f58a-444">上傳和下載資料檔案，您的 Azure 雲端儲存體中。</span><span class="sxs-lookup"><span data-stu-id="6f58a-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="6f58a-445">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="6f58a-445">To create this Class:</span></span>

1.  <span data-ttu-id="6f58a-446">以滑鼠右鍵按一下*Asset*資料夾，位於 [專案] 面板**建立** > **資料夾**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="6f58a-447">將資料夾命名**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-447">Name the folder **Scripts**.</span></span>

    ![建立新資料夾](images/AzureLabs-Lab5-50.png)

    ![呼叫資料夾-指令碼](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="6f58a-450">按兩下剛才建立開啟的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f58a-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="6f58a-451">在資料夾中，以滑鼠右鍵按一下**Create**  >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-451">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="6f58a-452">呼叫指令碼*所需的 AzureServices*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="6f58a-453">按兩下新*所需的 AzureServices*類別，以開啟它*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="6f58a-454">將下列命名空間加入至頂端*所需的 AzureServices*:</span><span class="sxs-lookup"><span data-stu-id="6f58a-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="6f58a-455">加入下列 Inspector 欄位內*所需的 AzureServices*類別：</span><span class="sxs-lookup"><span data-stu-id="6f58a-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="6f58a-456">然後新增下列成員變數內*所需的 AzureServices*類別：</span><span class="sxs-lookup"><span data-stu-id="6f58a-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="6f58a-457">請確定您取代*端點*並*連接字串*在 Azure 入口網站中找到的值與您的 Azure 儲存體、 值</span><span class="sxs-lookup"><span data-stu-id="6f58a-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="6f58a-458">程式碼*Awake()* 並*start （)* 方法現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="6f58a-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="6f58a-459">在類別初始化時，就會呼叫這些方法：</span><span class="sxs-lookup"><span data-stu-id="6f58a-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="6f58a-460">我們將會填入的程式碼*CallAzureFunctionForNextShape()* 中[未來一章](#chapter-10---completing-the-azureservices-class)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="6f58a-461">刪除*update （)* 方法，因為這個類別不會使用它。</span><span class="sxs-lookup"><span data-stu-id="6f58a-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="6f58a-462">在 Visual Studio 中，儲存您的變更，然後返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="6f58a-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="6f58a-463">按一下並拖曳*所需的 AzureServices*指令碼 資料夾中的 Main Camera 物件的類別*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="6f58a-464">選取 Main Camera，接著要抓取**AzureStatusText**從下方的子物件**GazeButton**物件，並放在**AzureStatusText**參考目標欄位中，以*Inspector*，以提供參考*所需的 AzureServices*指令碼。</span><span class="sxs-lookup"><span data-stu-id="6f58a-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![指派 azure 狀態文字參考目標](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="6f58a-466">第 8-建立 ShapeFactory 類別</span><span class="sxs-lookup"><span data-stu-id="6f58a-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="6f58a-467">若要建立下, 一步 的指令碼*ShapeFactory*類別。</span><span class="sxs-lookup"><span data-stu-id="6f58a-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="6f58a-468">此類別的角色是要求時，建立新的圖形，並保留歷程記錄中建立的圖案*圖形歷程記錄清單*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="6f58a-469">每次建立圖形時，*圖形歷程記錄清單*中更新*AzureService*類別，並且會儲存您*Azure 儲存體*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="6f58a-470">應用程式啟動時，如果儲存的檔案位於您*Azure 儲存體*，則*圖形的歷程記錄清單*擷取和重新執行，使用**3D 文字**物件，提供產生的圖形是否從儲存體，或新的。</span><span class="sxs-lookup"><span data-stu-id="6f58a-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="6f58a-471">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="6f58a-471">To create this class:</span></span>

1.  <span data-ttu-id="6f58a-472">移至**指令碼**您先前建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f58a-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="6f58a-473">在資料夾中，以滑鼠右鍵按一下**Create**  >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-473">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="6f58a-474">呼叫指令碼*ShapeFactory*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="6f58a-475">按兩下新*ShapeFactory*指令碼，以開啟它*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="6f58a-476">請確定*ShapeFactory*類別包含下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="6f58a-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="6f58a-477">新增至如下所示的變數*ShapeFactory*類別，並取代*start （)* 並*Awake()* 與下列函式：</span><span class="sxs-lookup"><span data-stu-id="6f58a-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="6f58a-478">*CreateShape()* 方法會產生基本的圖形，根據所提供*整數*參數。</span><span class="sxs-lookup"><span data-stu-id="6f58a-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="6f58a-479">布林值參數是用來指定目前建立的圖形是從儲存體，或是新。</span><span class="sxs-lookup"><span data-stu-id="6f58a-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="6f58a-480">將下列程式碼，在您*ShapeFactory*類別，先前的方法如下：</span><span class="sxs-lookup"><span data-stu-id="6f58a-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="6f58a-481">請務必在 Visual Studio 中儲存您的變更，然後再回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="6f58a-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="6f58a-482">傳回在 Unity 編輯器中，按一下並拖曳*ShapeFactory*從類別**指令碼**資料夾**Main Camera**物件*階層面板*.</span><span class="sxs-lookup"><span data-stu-id="6f58a-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="6f58a-483">您會發現與選取的 Main Camera *ShapeFactory*遺漏指令碼元件*繁衍點*參考。</span><span class="sxs-lookup"><span data-stu-id="6f58a-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="6f58a-484">若要修正此問題，拖曳**ShapeSpawnPoint**物件*階層面板*來**繁衍點**參考目標。</span><span class="sxs-lookup"><span data-stu-id="6f58a-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![集合圖形 factory 參考目標](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="6f58a-486">第 9-建立視線類別</span><span class="sxs-lookup"><span data-stu-id="6f58a-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="6f58a-487">您需要建立的最後一個指令碼*視線*類別。</span><span class="sxs-lookup"><span data-stu-id="6f58a-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="6f58a-488">這個類別會負責建立**Raycast** ，從主攝影機，來偵測使用者查看哪些物件會向前投影。</span><span class="sxs-lookup"><span data-stu-id="6f58a-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="6f58a-489">在此情況下，進而識別是否有使用者查看需要 Raycast **GazeButton**場景中物件，並會觸發的行為。</span><span class="sxs-lookup"><span data-stu-id="6f58a-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="6f58a-490">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="6f58a-490">To create this Class:</span></span>

1.  <span data-ttu-id="6f58a-491">移至**指令碼**您先前建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f58a-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="6f58a-492">在 [專案] 面板中，以滑鼠右鍵按一下**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-492">Right-click in the Project Panel, **Create** > **C# Script**.</span></span> <span data-ttu-id="6f58a-493">呼叫指令碼*視線*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="6f58a-494">按兩下新*視線*指令碼，以開啟它*Visual Studio。*</span><span class="sxs-lookup"><span data-stu-id="6f58a-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="6f58a-495">請確定下列命名空間包含在指令碼的頂端：</span><span class="sxs-lookup"><span data-stu-id="6f58a-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="6f58a-496">然後新增下列變數內*視線*類別：</span><span class="sxs-lookup"><span data-stu-id="6f58a-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="6f58a-497">這些變數的一些能夠在中編輯*編輯器*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="6f58a-498">程式碼*Awake()* 並*start （)* 方法現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="6f58a-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="6f58a-499">新增下列程式碼會建立一個資料指標物件開頭的情況下，連同*update （)* 方法，將會執行 Raycast 方法，以及切換 GazeEnabled 布林值的位置：</span><span class="sxs-lookup"><span data-stu-id="6f58a-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="6f58a-500">接下來新增*UpdateRaycast()* 方法，它將專案 Raycast 並偵測叫用的目標。</span><span class="sxs-lookup"><span data-stu-id="6f58a-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="6f58a-501">最後，新增*ResetFocusedObject()* 方法，它會切換 GazeButton 物件目前的色彩，表示它要建立新的形狀與否。</span><span class="sxs-lookup"><span data-stu-id="6f58a-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="6f58a-502">在 Visual Studio 中儲存的變更，然後再回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="6f58a-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="6f58a-503">按一下並拖曳*視線*類別的指令碼資料夾**Main Camera**物件*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="6f58a-504">第 10 章-完成所需的 AzureServices 類別</span><span class="sxs-lookup"><span data-stu-id="6f58a-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="6f58a-505">與其他指令碼中的地方，它現在便能夠*完整* *所需的 AzureServices*類別。</span><span class="sxs-lookup"><span data-stu-id="6f58a-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="6f58a-506">這會透過來達成：</span><span class="sxs-lookup"><span data-stu-id="6f58a-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="6f58a-507">新增名為的新方法*CreateCloudIdentityAsync()* ，若要設定驗證所需的變數來與 Azure 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="6f58a-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="6f58a-508">這個方法也會檢查先前儲存的檔案，包含 [圖形] 清單中存在。</span><span class="sxs-lookup"><span data-stu-id="6f58a-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="6f58a-509">**如果找到的檔案**，它會停用使用者*視線*，和形狀建立圖形，根據觸發程序，因為儲存在**Azure 儲存體檔案**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="6f58a-510">使用者可以確認這一點，作為**文字 Mesh**會提供顯示 'Storage' 或 'New'，根據圖形原點。</span><span class="sxs-lookup"><span data-stu-id="6f58a-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="6f58a-511">**如果不找到任何檔案**，它會讓*視線*，讓使用者能夠查看時，建立圖形**GazeButton**場景中的物件。</span><span class="sxs-lookup"><span data-stu-id="6f58a-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="6f58a-512">下一步 的程式碼片段是從*start （)* 方法，其中的呼叫將會對*CreateCloudIdentityAsync()* 方法。</span><span class="sxs-lookup"><span data-stu-id="6f58a-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="6f58a-513">歡迎您目前透過複製*start （)* 方法，與下面：</span><span class="sxs-lookup"><span data-stu-id="6f58a-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="6f58a-514">方法的程式碼中填滿*CallAzureFunctionForNextShape()* 。</span><span class="sxs-lookup"><span data-stu-id="6f58a-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="6f58a-515">您將使用先前建立*Azure 函數應用程式*要求形狀索引。</span><span class="sxs-lookup"><span data-stu-id="6f58a-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="6f58a-516">一旦收到新的形狀時，這個方法會將傳送圖形，以*ShapeFactory*場景中建立新的形狀的類別。</span><span class="sxs-lookup"><span data-stu-id="6f58a-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="6f58a-517">若要完成本文中使用下列程式碼*CallAzureFunctionForNextShape()* 。</span><span class="sxs-lookup"><span data-stu-id="6f58a-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="6f58a-518">新增方法以建立字串，串連的整數儲存圖形的歷程記錄清單，並將它儲存在您*Azure 儲存體檔案*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="6f58a-519">新增方法以擷取儲存在檔案位於您*Azure 儲存體檔案*並*還原序列化*到清單。</span><span class="sxs-lookup"><span data-stu-id="6f58a-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="6f58a-520">完成此程序之後，此方法會重新啟用視線，讓使用者可以將多個圖形新增至場景。</span><span class="sxs-lookup"><span data-stu-id="6f58a-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="6f58a-521">在 Visual Studio 中儲存的變更，然後再回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="6f58a-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="6f58a-522">第 11 章-建置 UWP 方案</span><span class="sxs-lookup"><span data-stu-id="6f58a-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="6f58a-523">若要開始建置程序：</span><span class="sxs-lookup"><span data-stu-id="6f58a-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="6f58a-524">移至**檔案** > **組建設定**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-524">Go to **File** > **Build Settings**.</span></span>

    ![建置應用程式](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="6f58a-526">按一下 [建置]  。</span><span class="sxs-lookup"><span data-stu-id="6f58a-526">Click **Build**.</span></span> <span data-ttu-id="6f58a-527">將會啟動 unity*檔案總管*視窗中，您要建立，然後選取 建置到應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f58a-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="6f58a-528">現在，建立該資料夾並將它命名*應用程式*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="6f58a-529">然後使用*應用程式*資料夾選取，請按下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="6f58a-530">Unity 會開始建置您的專案*應用程式*資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f58a-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="6f58a-531">一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟*檔案總管*視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="6f58a-532">第 12 章-部署應用程式</span><span class="sxs-lookup"><span data-stu-id="6f58a-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="6f58a-533">若要部署您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="6f58a-533">To deploy your application:</span></span>

1.  <span data-ttu-id="6f58a-534">瀏覽至*應用程式*中所建立的資料夾[最後一章](#chapter-11---build-the-uwp-solution)。</span><span class="sxs-lookup"><span data-stu-id="6f58a-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="6f58a-535">您會看到您的應用程式名稱，與 '.sln' 擴充功能，您應該連按兩下檔案，因此以內開啟它*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="6f58a-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="6f58a-536">在 **的方案平台**，選取**x86，本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="6f58a-537">在 **方案組態**選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="6f58a-538">針對 Microsoft HoloLens，您可能會發現它更輕鬆地將此設為*遠端機器*，如此一來，您不行動網卡到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="6f58a-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="6f58a-539">不過，您必須也執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="6f58a-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="6f58a-540">了解**IP 位址**的您 HoloLens，位於**設定** > **網路和網際網路** >  **Wi-fi** > **進階選項**; IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="6f58a-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options**; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="6f58a-541">請確定**開發人員模式**是**上**; 在找到**設定** > **更新與安全性** >  **適用於開發人員**。</span><span class="sxs-lookup"><span data-stu-id="6f58a-541">Ensure **Developer Mode** is **On**; found in **Settings** > **Update & Security** > **For developers**.</span></span>

    ![部署解決方案](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="6f58a-543">移至**建置**功能表，然後按一下 **部署方案**側載應用程式到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="6f58a-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="6f58a-544">您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動並測試 ！</span><span class="sxs-lookup"><span data-stu-id="6f58a-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="6f58a-545">您已完成 Azure Functions 和儲存體應用程式</span><span class="sxs-lookup"><span data-stu-id="6f58a-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="6f58a-546">恭喜，您所建立的混合的實境應用程式，運用 Azure Functions 和 Azure 儲存體服務。</span><span class="sxs-lookup"><span data-stu-id="6f58a-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="6f58a-547">您的應用程式將能夠依據儲存的資料，並提供該資料為基礎的動作。</span><span class="sxs-lookup"><span data-stu-id="6f58a-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![最終產品-結束](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="6f58a-549">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="6f58a-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="6f58a-550">練習 1</span><span class="sxs-lookup"><span data-stu-id="6f58a-550">Exercise 1</span></span>

<span data-ttu-id="6f58a-551">建立第二個繁衍，點和記錄點已建立物件，從繁衍 （spawn）。</span><span class="sxs-lookup"><span data-stu-id="6f58a-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="6f58a-552">當您載入資料檔案時，重新執行正在繁衍從原先建立的位置的圖形。</span><span class="sxs-lookup"><span data-stu-id="6f58a-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="6f58a-553">練習 2</span><span class="sxs-lookup"><span data-stu-id="6f58a-553">Exercise 2</span></span>

<span data-ttu-id="6f58a-554">建立應用程式，而不必重新開啟它每次重新啟動的方式。</span><span class="sxs-lookup"><span data-stu-id="6f58a-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="6f58a-555">**正在載入場景**是很好的位置，以啟動。</span><span class="sxs-lookup"><span data-stu-id="6f58a-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="6f58a-556">之後，若要清除的預存的清單中的方式來建立*Azure 儲存體*，如此一來，它可以輕鬆地重設您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f58a-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
