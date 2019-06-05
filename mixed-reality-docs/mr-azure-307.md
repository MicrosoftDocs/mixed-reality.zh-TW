---
title: MR 和 Azure 307-機器學習服務
description: 完成這個課程來了解如何實作 Azure Machine Learning Studio 內的混合的實境應用程式。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 機器學習服務，ml、 機器學習 studio、 hololens、 沈浸式、 vr
ms.openlocfilehash: 93263817df0fd809a09b32c1b34a636eab7026a1
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516044"
---
>[!NOTE]
><span data-ttu-id="f8ff1-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f8ff1-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f8ff1-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f8ff1-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f8ff1-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f8ff1-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="f8ff1-110">MR 和 Azure 307:機器學習</span><span class="sxs-lookup"><span data-stu-id="f8ff1-110">MR and Azure 307: Machine learning</span></span>

![最終產品-開始](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="f8ff1-112">在此課程中，您將學習如何將 Machine Learning (ML) 功能新增至混合的實境應用程式使用 Azure Machine Learning Studio。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="f8ff1-113">*Azure Machine Learning Studio*是 Microsoft 服務，開發人員提供了大量的機器學習服務演算法，可協助進行資料輸入、 輸出、 準備及視覺效果。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="f8ff1-114">從這些元件，就能夠開發預測性分析實驗，逐一查看，並使用它來定型模型。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="f8ff1-115">下列訓練，您可以讓您的模型運作內 Azure 雲端中，以便它可以再評分新資料。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="f8ff1-116">如需詳細資訊，請瀏覽[Azure Machine Learning Studio 頁面](https://azure.microsoft.com/en-au/services/machine-learning-studio/)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="f8ff1-117">完成本課程，您將的混合的實境沈浸式耳機應用程式，且將會學到如何執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="f8ff1-118">提供的銷售資料的資料表*Azure Machine Learning Studio*入口網站，並設計演算法來預測未來銷售的受歡迎的項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="f8ff1-119">建立**Unity 專案**，它可以接收和解譯 ML 服務的預測資料。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="f8ff1-120">中以視覺化方式顯示 predication 資料**Unity 專案**，透過提供的最受歡迎的銷售項目，放到書架上。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="f8ff1-121">在您的應用程式，則您對於如何將整合結果進行設計。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="f8ff1-122">本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="f8ff1-123">它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="f8ff1-124">本課程是獨立的教學課程，其中並不直接包含任何其他混合實境實驗室。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="f8ff1-125">裝置支援</span><span class="sxs-lookup"><span data-stu-id="f8ff1-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f8ff1-126">課程</span><span class="sxs-lookup"><span data-stu-id="f8ff1-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f8ff1-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f8ff1-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f8ff1-128"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="f8ff1-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f8ff1-129">MR 和 Azure 307:機器學習</span><span class="sxs-lookup"><span data-stu-id="f8ff1-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="f8ff1-130">✔️</span><span class="sxs-lookup"><span data-stu-id="f8ff1-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f8ff1-131">✔️</span><span class="sxs-lookup"><span data-stu-id="f8ff1-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="f8ff1-132">雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="f8ff1-133">當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="f8ff1-134">當使用 HoloLens，您可能會發現某些回應語音擷取期間。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f8ff1-135">先決條件</span><span class="sxs-lookup"><span data-stu-id="f8ff1-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f8ff1-136">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f8ff1-137">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="f8ff1-138">中所示，您可以自由使用最新的軟體[安裝工具文章](install-the-tools.md)，不過它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體與以下所列.</span><span class="sxs-lookup"><span data-stu-id="f8ff1-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="f8ff1-139">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f8ff1-140">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="f8ff1-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="f8ff1-141">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="f8ff1-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f8ff1-142">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="f8ff1-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f8ff1-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="f8ff1-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f8ff1-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f8ff1-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="f8ff1-145">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="f8ff1-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f8ff1-146">針對 Azure 設定和 ML 資料擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="f8ff1-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f8ff1-147">開始之前</span><span class="sxs-lookup"><span data-stu-id="f8ff1-147">Before you start</span></span>

<span data-ttu-id="f8ff1-148">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="f8ff1-149">第 1 章-Azure 儲存體帳戶設定</span><span class="sxs-lookup"><span data-stu-id="f8ff1-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="f8ff1-150">若要使用 Azure 轉譯程式 API，您必須設定您的應用程式提供服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="f8ff1-151">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f8ff1-152">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="f8ff1-153">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="f8ff1-154">一旦您登入，按一下**儲存體帳戶**左側功能表中。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="f8ff1-156">單字**的新**可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="f8ff1-157">在 **儲存體帳戶**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="f8ff1-159">在 **建立儲存體帳戶**面板：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="f8ff1-160">插入**名稱**您的帳戶，請留意這個欄位只接受數字和小寫字母。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="f8ff1-161">針對**部署模型**選取**Resource manager**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="f8ff1-162">針對**帳戶種類**，選取**儲存體 (一般用途 v1)** 。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="f8ff1-163">針對**效能**，選取**標準**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="f8ff1-164">針對**複寫**選取**讀取-存取-異地備援儲存體 (RA-GRS)** 。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="f8ff1-165">離開**需要安全傳輸**作為**停用**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="f8ff1-166">選取 **訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="f8ff1-167">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f8ff1-168">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f8ff1-169">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="f8ff1-170">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="f8ff1-171">判斷**位置**資源群組 （如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f8ff1-172">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f8ff1-173">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="f8ff1-174">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="f8ff1-176">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="f8ff1-177">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="f8ff1-179">第 2 章-Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="f8ff1-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="f8ff1-180">若要使用*Azure Machine Learning*，您必須設定機器學習服務可供您的應用程式的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="f8ff1-181">在 Azure 入口網站中，按一下**新增**在左上角，，然後搜尋**Machine Learning Studio 工作區**、 按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="f8ff1-183">新的頁面將提供的描述**Machine Learning Studio 工作區**服務。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="f8ff1-184">在此提示的左下方，按一下**建立**按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="f8ff1-185">一旦您按下**Create**，面板會顯示您要提供一些關於您的新詳細資料**Machine Learning Studio 服務**:</span><span class="sxs-lookup"><span data-stu-id="f8ff1-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="f8ff1-186">插入您想要**工作區名稱**此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="f8ff1-187">選取 **訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="f8ff1-188">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f8ff1-189">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f8ff1-190">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="f8ff1-191">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="f8ff1-192">判斷**位置**資源群組 （如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f8ff1-193">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f8ff1-194">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="f8ff1-195">您應該使用相同的資源群組，您用來建立 Azure 儲存體上一章。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="f8ff1-196">針對**儲存體帳戶**區段中，按一下**使用現有**，然後按一下下拉式功能表中，並從該處，按一下**儲存體帳戶**在最後一章中所建立。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="f8ff1-197">選取適當**工作區定價層**為您從下拉式功能表中。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="f8ff1-198">內**Web 服務方案**區段中，按一下**建立** **新**再插入的文字欄位中的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="f8ff1-199">從**Web 服務方案定價層**區段中，選取您選擇的價格層。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="f8ff1-200">開發，測試呼叫階層**研發/測試標準**應該是您可以免費使用。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="f8ff1-201">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="f8ff1-202">按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="f8ff1-204">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="f8ff1-205">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="f8ff1-207">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="f8ff1-209">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="f8ff1-210">在下方顯示的網頁**其他連結**區段中，按一下**啟動 Machine Learning Studio**，這會將導向您的瀏覽器**Machine Learning Studio**入口網站。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="f8ff1-212">使用**登入** 按鈕，在右上方，或是在中心，登入您的 Machine Learning Studio 中。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="f8ff1-214">第 3 章-Machine Learning Studio:資料集的安裝程式</span><span class="sxs-lookup"><span data-stu-id="f8ff1-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="f8ff1-215">其中一種機器學習服務演算法運作方式是藉由分析現有的資料，並嘗試預測未來結果根據現有的資料集。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="f8ff1-216">這通常表示，多現有的資料有，較佳的演算法會在預測未來結果。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="f8ff1-217">範例資料表會提供給您，這堂課程中，呼叫[ProductsTableCSV 而且可以在這裡下載](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8ff1-218">上述的.zip 檔案同時包含**ProductsTableCSV**並 **.unitypackage**，您將需要在[第 6 章](#chapter-6---importing-the-mlproducts-unity-package)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="f8ff1-219">此套件也會提供內該章節，但不同的 csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="f8ff1-220">此範例資料集包含每小時的每一天的 2017 年的銷售量最高的物件記錄。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio:資料集的安裝程式](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="f8ff1-222">例如，在 2017 年第 1 天，下午 1 點 （小時 13），最暢銷的項目已 salt 披頭四與。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="f8ff1-223">此範例資料表包含 9998 的項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="f8ff1-224">返回**Machine Learning Studio**入口網站中，並新增為此資料表**Dataset**您 ml。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="f8ff1-225">依序按一下 **+ 新增**在畫面的左下角的按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio:資料集的安裝程式](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="f8ff1-227">區段會出現從底部，且內左側的瀏覽窗格中。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="f8ff1-228">按一下 **資料集**，則，右邊**從本機檔案**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio:資料集的安裝程式](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="f8ff1-230">上傳新**資料集**依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="f8ff1-231">會出現 [上傳] 視窗中，您可以在其中**瀏覽**硬碟的新資料集。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio:資料集的安裝程式](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="f8ff1-233">一旦選取，並重新上傳 視窗中，保留未核取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="f8ff1-234">在下方的文字欄位中輸入**ProductsTableCSV.csv**做為資料集的名稱 （但應該會自動加入）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="f8ff1-235">使用下拉式功能表**型別**，選取**一般 CSV 檔案 (.csv) 的標頭**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="f8ff1-236">按下的刻度在右下方的 [上傳] 視窗中，而您**資料集**即將上傳。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="f8ff1-237">第 4 章-Machine Learning Studio:實驗</span><span class="sxs-lookup"><span data-stu-id="f8ff1-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="f8ff1-238">您可以建立您的機器學習系統之前，您必須建置實驗，以驗證您的理論上，您的資料。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="f8ff1-239">結果，您會知道您是否需要更多資料，或是否有可能出現的結果和資料之間沒有相互關聯。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="f8ff1-240">若要啟動建立實驗：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="f8ff1-241">請再按一下 **+ 新增**左下角的頁面，按鈕，然後按一下**實驗** > **空白實驗**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="f8ff1-243">空白實驗，將會顯示新的頁面：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="f8ff1-244">從左側面板中，展開 **儲存的資料集* > *我的資料集** 拖曳**ProductsTableCSV**入**實驗畫布**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-244">From the panel on the left expand **Saved Datasets* > *My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="f8ff1-246">在左側窗格中，依序展開**Data Transformation** > **取樣和分割**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="f8ff1-247">然後將拖曳**資料分割**項目中加入**實驗畫布**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="f8ff1-248">分割資料的項目會將資料集分成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="f8ff1-249">您將用於定型機器學習演算法使用一個組件。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="f8ff1-250">第二個部分會用於評估產生演算法的精確度。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="f8ff1-252">在右窗格中 （同時在畫布上的項目已選取分割資料），請編輯**的第一個輸出資料集中的資料列比例**要**0.7**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="f8ff1-253">這會將資料分成兩個部分，第一個部分會 70%的資料，而第二個部分會剩餘的 30%。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="f8ff1-254">若要確保資料會隨機分割，請確定**Randomized split**核取方塊保持核取狀態。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="f8ff1-256">拖曳連接自的基底**ProductsTableCSV**分割資料的項目頂端，在畫布上的項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="f8ff1-257">這會連接的項目，並傳送**ProductsTableCSV**資料集輸出至輸入的資料分割 （資料）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="f8ff1-259">在 **實驗**左側面板中，展開 \**Machine Learning* > \* 訓練 \* \*。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-259">In the **Experiments** panel on the left side, expand \**Machine Learning* > \*Train\*\*.</span></span> <span data-ttu-id="f8ff1-260">拖曳**定型模型**中的項目縮小到實驗畫布。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="f8ff1-261">畫布看起來應該與相同如下。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="f8ff1-263">從***左下方***的**分割資料**項目拖曳至某個連線**右上方**的**定型模型**項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="f8ff1-264">第一個 70%分割資料集將用於定型的模型定型演算法。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="f8ff1-266">選取 **定型模型**畫布，在和中的項目**屬性**面板 （在您的瀏覽器視窗的右手邊） 按一下 **啟動資料行選取器** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="f8ff1-267">在文字方塊中輸入**產品**，然後按**Enter**，*產品*將做為資料行來訓練預測。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="f8ff1-268">在此之後，按一下**刻度**以關閉 [選取] 對話方塊右下角。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="f8ff1-270">您要定型**多級羅吉斯迴歸**演算法來預測銷售最**產品**根據日期和日期的小時。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="f8ff1-271">超出本文件提供 Azure Machine Learning studio 中，不過，不同演算法的詳細說明的範圍是您可以深入了解從[機器學習服務演算法小祕技](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="f8ff1-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="f8ff1-272">從 實驗 項目面板的 在左側，展開 \* \**Machine Learning* > *初始化模型*> \* 分類 \* \* \*，然後拖曳**多級羅吉斯迴歸**至實驗畫布的項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-272">From the experiment items panel on the left, expand \*\**Machine Learning* > *Initialize Model* > \*Classification\*\*\*, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="f8ff1-273">輸出中，連接到從底部**多級羅吉斯迴歸**的左上方輸入**定型模型**項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="f8ff1-275">在清單中的實驗項目，在左側面板中，展開 \**Machine Learning* > \* 分數 \* \*，然後將拖曳**評分模型**至畫布的項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-275">In list of experiment items in the panel on the left, expand \**Machine Learning* > \*Score\*\*, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="f8ff1-276">輸出中，連接到從底部**定型模型**的左上方輸入**評分模型**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="f8ff1-277">從右下方輸出連接到**資料分割**，到右上方的輸入 \**評分模型*項目\*。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model* item*.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="f8ff1-279">在這份**實驗**在左側面板中的項目會展開 \* \**Machine Learning* > \* 評估 \* \* \*，然後拖曳**評估模型**拖曳到畫布上的項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-279">In the list of **Experiment** items in the panel on the left, expand \*\**Machine Learning* > \*Evaluate\*\*\*, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="f8ff1-280">從輸出連接到**評分模型**的左上方輸入**評估模型**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="f8ff1-282">您已建立您的第一個機器學習服務實驗。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="f8ff1-283">您現在可以儲存並執行實驗。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-283">You can now save and run the experiment.</span></span> <span data-ttu-id="f8ff1-284">在頁面底部功能表中，按一下**儲存**按鈕以儲存您的實驗，然後按一下**執行**開始實驗。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="f8ff1-286">您所見**狀態**中右上方畫布的實驗。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="f8ff1-287">等候一些時間才能完成實驗。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="f8ff1-288">如果您有大型 （實際） 資料集很可能實驗可能需要執行的小時。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="f8ff1-290">以滑鼠右鍵按一下**評估模型**項目畫布中，並從內容功能表動態顯示滑鼠透過**評估結果**，然後選取**視覺化**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="f8ff1-292">將顯示預測的結果與實際的結果會顯示評估結果。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="f8ff1-293">這會使用原始資料集已分割更早版本，來評估模型的 30%。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="f8ff1-294">您可以看到結果不是太棒了，在理想情況下您會具有最高數量中每個資料列是資料行中的反白顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="f8ff1-296">關閉**結果**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-296">Close the **Results**.</span></span>

24. <span data-ttu-id="f8ff1-297">若要使用您新定型的機器學習服務模型，您需要將它公開為**Web 服務**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="f8ff1-298">若要這樣做，請按一下**設定 Web 服務** 功能表項目在頁面底部的功能表，然後按一下**預測性 Web 服務**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="f8ff1-300">將建立新的索引標籤，並合併以建立新的 web 服務的定型模型。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="f8ff1-301">在頁面底部的功能表中按一下**儲存**，然後按一下**執行**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="f8ff1-302">您會看到更新的實驗畫布右上角的狀態。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="f8ff1-304">一旦執行，完成**部署 Web 服務**按鈕將會出現在頁面底部。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="f8ff1-305">您已準備好部署 web 服務。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="f8ff1-306">按一下 **部署 Web 服務**（傳統） 在頁面底部的功能表中。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="f8ff1-308">您的瀏覽器可能會提示以允許快顯視窗，您應該**允許**，不過您可能需要按下**部署 Web 服務**同樣地，如果未顯示 [部署] 頁面。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="f8ff1-309">建立實驗之後您將會重新導向至**儀表板**頁面，您必須將您**API 金鑰**顯示。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="f8ff1-310">將它複製到 [記事本] 中，目前為止，您將很快在程式碼中需要它。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="f8ff1-311">一旦您已記下您的 API 金鑰，按一下**要求/回應**按鈕**預設端點**區段下方的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="f8ff1-313">如果您在此頁面中按一下測試，您可以輸入的輸入的資料，並檢視輸出。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="f8ff1-314">請輸入**天**並**小時**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="f8ff1-315">離開**產品**空白的項目。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="f8ff1-316">然後按一下**確認** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="f8ff1-317">在頁面底部的輸出會顯示 JSON 表示正在選擇每項產品的可能性。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="f8ff1-318">新的 web 網頁將會開啟，顯示的指示和 Machine Learning Studio 所需的要求結構相關的一些範例。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="f8ff1-319">複製**要求 URI**顯示在此頁面中，到您的 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="f8ff1-321">現在您已建置機器學習系統，可提供銷售產品最有可能根據購買歷程記錄資料，就是相互關聯的日期和年份的日期時間。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="f8ff1-322">若要呼叫 web 服務，您需要 URL 的服務端點和服務的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="f8ff1-323">按一下 **取用**索引標籤上，從上方的功能表。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="f8ff1-324">**耗用量**資訊頁面會顯示您必須從您的程式碼中呼叫 web 服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="f8ff1-325">需要一份**主索引鍵**並**要求-回應**URL。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="f8ff1-326">您必須在下一步 一章中。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="f8ff1-327">第 5 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="f8ff1-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="f8ff1-328">設定並測試混合實境沈浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="f8ff1-329">您將會**不**本課程所需動作的控制器。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="f8ff1-330">如果您需要支援沈浸式耳機的設定，請按一下[此處](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="f8ff1-331">開啟**Unity**並建立新的 Unity 專案，稱為**MR\_。**</span><span class="sxs-lookup"><span data-stu-id="f8ff1-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="f8ff1-332">請確定專案類型設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="f8ff1-333">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f8ff1-334">移至 ***編輯* > *喜好設定*** 從新的視窗中，然後瀏覽至 **外部工具** 。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-334">Go to ***Edit* > *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f8ff1-335">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f8ff1-336">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="f8ff1-337">接下來，移至 ***檔案* > *組建設定*** 切換平台**通用 Windows 平台**，按一下***切換平台*** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-337">Next, go to ***File* > *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="f8ff1-338">此外，請確定：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="f8ff1-339">**裝置為目標**設定為**任何裝置**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="f8ff1-340">對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="f8ff1-341">**建置型別**設定為**D3D**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="f8ff1-342">**SDK**設定為**最新安裝**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="f8ff1-343">**Visual Studio 版本**設定為**最新安裝**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="f8ff1-344">**建置並執行**設定為**本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="f8ff1-345">不要擔心設定**場景**立即，因為這些會在稍後提供。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="f8ff1-346">其餘的設定應該保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-346">The remaining settings should be left as default for now.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="f8ff1-348">中**組建設定**視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="f8ff1-349">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="f8ff1-350">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="f8ff1-351">**指令碼** **執行階段版本**應該**實驗性**（.NET 4.6 對等）</span><span class="sxs-lookup"><span data-stu-id="f8ff1-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="f8ff1-352">**指令碼後端**應該是 ***.NET***</span><span class="sxs-lookup"><span data-stu-id="f8ff1-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="f8ff1-353">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="f8ff1-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="f8ff1-355">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="f8ff1-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f8ff1-356">**InternetClient**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="f8ff1-358">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入</span><span class="sxs-lookup"><span data-stu-id="f8ff1-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="f8ff1-360">回到**Build Settings** *Unity C#* 專案不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="f8ff1-361">關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="f8ff1-362">儲存您的專案 (**檔案 > 儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="f8ff1-363">第 6 章-匯入 MLProducts Unity 封裝</span><span class="sxs-lookup"><span data-stu-id="f8ff1-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="f8ff1-364">這堂課程中，您必須下載 Unity 資產套件，稱為[ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="f8ff1-365">此套件都有完整的場景，請使用中的所有物件也預先建置，因此您可以專注於取得它所有的工作。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="f8ff1-366">**ShelfKeeper**提供指令碼，不過只會保留用於場景的安裝程式結構的公用變數。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="f8ff1-367">您必須執行所有其他區段。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="f8ff1-368">若要匯入此套件：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-368">To import this package:</span></span>

1.  <span data-ttu-id="f8ff1-369">您面前的 Unity 儀表板中，按一下**資產**在畫面頂端的功能表，然後按一下**匯入封裝]、 [自訂封裝**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="f8ff1-371">使用檔案選擇器選取**Azure-MR-307.unitypackage**封裝，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="f8ff1-372">為此資產的元件的清單會顯示給您。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="f8ff1-373">確認匯入，依序按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-373">Confirm the import by clicking **Import**.</span></span>

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="f8ff1-375">完成匯入後，您會注意到一些新的資料夾會出現在您的 Unity **[專案] 面板**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="f8ff1-376">這些都是場景的 3D 模型和屬於預先製作，您要處理的個別資料。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="f8ff1-377">在本課程中，您將撰寫大部分的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-377">You will write the majority of the code in this course.</span></span>

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="f8ff1-379">內**專案 面板**資料夾中，按一下**場景**資料夾，按兩下 在場景 (稱為**MR_MachineLearningScene**)。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="f8ff1-380">場景會開啟 （請參閱下圖）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-380">The scene will open (see image below).</span></span> <span data-ttu-id="f8ff1-381">如果紅色菱形遺漏，只要按一下**Gizmo**頂端的按鈕，方**遊戲面板**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="f8ff1-383">第 7 章-檢查 Unity 中的 Dll</span><span class="sxs-lookup"><span data-stu-id="f8ff1-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="f8ff1-384">若要利用 JSON 文件庫 （用於序列化和還原序列化） 使用，已與您所引進的封裝實作 Newtonsoft DLL。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="f8ff1-385">程式庫應該有正確的設定，雖然很值得一查 （特別是當使用無效的程式碼有問題）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="f8ff1-386">方法如下：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-386">To do so:</span></span>

-  <span data-ttu-id="f8ff1-387">以滑鼠左鍵按一下 Plugins 資料夾內 Newtonsoft 歸檔，並查看**Inspector 面板**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="f8ff1-388">請確定**任何平台**已勾選。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="f8ff1-389">移至**UWP 索引標籤**也可確保**不會處理**已勾選。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![匯入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="f8ff1-391">第 8-建立 ShelfKeeper 類別</span><span class="sxs-lookup"><span data-stu-id="f8ff1-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="f8ff1-392">**ShelfKeeper**類別裝載控制項的 UI 和產品在場景中繁衍的方法。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="f8ff1-393">匯入套件的一部分，您將會提供這個類別，但已完成。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="f8ff1-394">現在正是時候以完成該類別：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="f8ff1-395">按兩下**ShelfKeeper**指令碼，在**指令碼**資料夾，將它以開啟**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="f8ff1-396">取代現有的指令碼使用下列程式碼，可設定的時間和日期，並已顯示產品的方法中的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="f8ff1-397">請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="f8ff1-398">傳回在 Unity 編輯器中，確認**ShelfKeeper**類別看起來像下面：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="f8ff1-400">如果您的指令碼並沒有參考目標 (亦即 *(Mesh 的文字) 的日期*)，只需將拖曳對應的物件，從**階層面板**，目標欄位。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="f8ff1-401">請參閱以下的說明，如有需要：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="f8ff1-402">開啟**繁衍點**陣列內**ShelfKeeper**元件指令碼中的用滑鼠左鍵按一下它。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="f8ff1-403">子區段會出現稱為**大小**，表示陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="f8ff1-404">型別**3**旁邊的文字方塊**大小**然後按**Enter**，和下方，將會建立三個位置。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="f8ff1-405">內**階層**展開**時間顯示**（藉由它旁邊的箭號上按一下滑鼠左鍵） 的物件。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="f8ff1-406">接下來，按一下***Main Camera***內在**階層**，以便**Inspector**顯示其資訊。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="f8ff1-407">選取 **主攝影機**中**階層面板**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="f8ff1-408">拖曳**日期**並**時間**物件**階層面板**來**日期的文字**和**階段文字**位置內**Inspector**的**Main Camera**中**ShelfKeeper**元件。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="f8ff1-409">拖曳**繁衍點**從**階層面板**(下方*貨架*物件) 至**3** **元素**參考下的目標**繁衍點**陣列，如圖所示。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="f8ff1-411">第 9-建立 ProductPrediction 類別</span><span class="sxs-lookup"><span data-stu-id="f8ff1-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="f8ff1-412">下一步要建立的類別是**ProductPrediction**類別。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="f8ff1-413">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-413">This class is responsible for:</span></span>

-   <span data-ttu-id="f8ff1-414">查詢**Machine Learning 服務**執行個體，提供目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="f8ff1-415">可用的資料還原序列化 JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="f8ff1-416">解譯的資料，擷取 3 個建議的產品。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="f8ff1-417">呼叫**ShelfKeeper**類別方法來顯示場景中的資料。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="f8ff1-418">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-418">To create this class:</span></span>

1.  <span data-ttu-id="f8ff1-419">移至**指令碼**資料夾，請在 **[專案] 面板**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="f8ff1-420">在資料夾中，以滑鼠右鍵按一下**Create** > **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-420">Right-click inside the folder, **Create** > **C\# Script**.</span></span> <span data-ttu-id="f8ff1-421">呼叫指令碼**ProductPrediction**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="f8ff1-422">按兩下新**ProductPrediction**指令碼，以開啟它**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="f8ff1-423">如果**偵測到檔案修改**對話方塊顯示，按一下 \***重新載入解決方案**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="f8ff1-424">ProductPrediction 類別頂端新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="f8ff1-425">內部**ProductPrediction**類別插入下列兩個物件是由數個巢狀類別所組成。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="f8ff1-426">這些類別用來序列化和還原序列化的 Machine Learning 服務的 JSON。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="f8ff1-427">（如此 JSON 的相關程式碼的指令碼，以下的所有其他程式碼，來移底部），然後加入先前的程式碼上方的下列變數：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="f8ff1-428">請確定插入**主索引鍵**並**要求-回應端點**，從 Machine Learning 入口網站，為的變數。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="f8ff1-429">以下影像顯示其中您所花的金鑰和端點。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="f8ff1-432">插入此程式碼內**start （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="f8ff1-433">**Start （)** 類別初始化時，會呼叫方法：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="f8ff1-434">以下是從 Windows 收集的日期和時間，並將它轉換成機器學習服務實驗可用來比較儲存在資料表中的資料格式的方法。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="f8ff1-435">您可以**刪除** **update （)** 方法，因為這個類別不會使用它。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="f8ff1-436">新增下列方法將目前的日期和時間的機器學習服務端點進行通訊，並接收 JSON 格式的回應。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="f8ff1-437">新增下列方法，也就是負責還原序列化 JSON 回應，以及通訊的還原序列化結果**ShelfKeeper**類別。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="f8ff1-438">此結果會在目前的日期和時間大部分的銷售預測三個項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="f8ff1-439">插入下列程式碼**ProductPrediction**類別前, 一個方法如下。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="f8ff1-440">儲存**Visual Studio**返回並**Unity**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="f8ff1-441">拖曳**ProductPrediction**類別的指令碼從**指令碼**資料夾中，拖曳至**Main Camera**物件。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="f8ff1-442">儲存您的場景和專案**檔案** >  ***儲存場景* / *檔案***  >  **儲存專案**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-442">Save your scene and project **File** > ***Save Scene* / *File*** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="f8ff1-443">第 10 章-建置 UWP 方案</span><span class="sxs-lookup"><span data-stu-id="f8ff1-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="f8ff1-444">現在正是時候建置您的專案做為 UWP 方案，讓它可以當做獨立應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="f8ff1-445">若要建置：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-445">To Build:</span></span>

1.  <span data-ttu-id="f8ff1-446">按一下儲存目前的場景**檔案** **儲存場景**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-446">Save the current scene by clicking on **File** **Save Scenes**.</span></span>

2.  <span data-ttu-id="f8ff1-447">移至**檔案** **組建設定**</span><span class="sxs-lookup"><span data-stu-id="f8ff1-447">Go to **File** **Build Settings**</span></span>

3.  <span data-ttu-id="f8ff1-448">核取方塊稱為**Unity C\#專案**（這是重要因為這樣可讓您完成建置後編輯類別）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-448">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="f8ff1-449">按一下 **將開啟的場景新增**，</span><span class="sxs-lookup"><span data-stu-id="f8ff1-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="f8ff1-450">按一下 [建置]  。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-450">Click **Build**.</span></span>

    ![建置 UWP 方案](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="f8ff1-452">系統會提示您選取您要建置方案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="f8ff1-453">建立**建置**資料夾和該資料夾中建立適當的名稱，您選擇的另一個資料夾。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="f8ff1-454">按一下您的新資料夾，然後按一下**選取資料夾**，若要開始在該位置的組建。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![建置 UWP 方案](images/AzureLabs-Lab7-55.png)

    ![建置 UWP 方案](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="f8ff1-457">一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="f8ff1-458">第 11-部署應用程式</span><span class="sxs-lookup"><span data-stu-id="f8ff1-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="f8ff1-459">若要部署您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-459">To deploy your application:</span></span>

1.  <span data-ttu-id="f8ff1-460">瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="f8ff1-461">使用 Visual Studio 中開啟，您需要還原 NuGet 套件，您可以透過 MachineLearningLab_Build 方案時，從 方案總管中 （右邊的 Visual Studio 找到），以滑鼠右鍵按一下，然後按一下 還原 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![新增 NuGet 封裝](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="f8ff1-463">在 方案組態選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="f8ff1-464">在 方案平台上，選取**x86**，**本機**。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="f8ff1-465">針對 Microsoft HoloLens，您可能會發現它更輕鬆地將此設為*遠端機器*，如此一來，您不行動網卡到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="f8ff1-466">不過，您必須也執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f8ff1-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="f8ff1-467">了解**IP 位址**的您 HoloLens，位於*設定 > 網路和網際網路 > Wi-fi > 進階選項*; IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="f8ff1-468">請確定**開發人員模式**是**上**; 在找到*設定 > 更新與安全性 > 適用於開發人員*。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![新增 NuGet 封裝](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="f8ff1-470">移至**建置 功能表**，然後按一下**部署方案**側載應用程式以您的電腦。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="f8ff1-471">您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="f8ff1-472">當您執行的混合實境應用程式時，您會看到已設定您的 Unity 場景，請在工作台，而且將從初始化時，擷取您在 Azure 中設定的資料。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="f8ff1-473">資料會在應用程式內進行還原序列化，並將視覺化工作台上的三種模型提供的最上層的三個結果，您目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="f8ff1-474">您已完成的機器學習服務應用程式</span><span class="sxs-lookup"><span data-stu-id="f8ff1-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="f8ff1-475">恭喜，您建置利用 Azure Machine Learning 來進行資料預測，並顯示在場景的混合的實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![新增 NuGet 封裝](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="f8ff1-477">練習</span><span class="sxs-lookup"><span data-stu-id="f8ff1-477">Exercise</span></span>

<span data-ttu-id="f8ff1-478">**練習 1**</span><span class="sxs-lookup"><span data-stu-id="f8ff1-478">**Exercise 1**</span></span>

<span data-ttu-id="f8ff1-479">體驗您的應用程式的排序次序，並具有這項資料可能會有用也出現在上架，下方的三個預測。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="f8ff1-480">**練習 2**</span><span class="sxs-lookup"><span data-stu-id="f8ff1-480">**Exercise 2**</span></span>

<span data-ttu-id="f8ff1-481">使用**Azure 資料表**填入新資料表天氣資訊，並建立新的實驗使用的資料。</span><span class="sxs-lookup"><span data-stu-id="f8ff1-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
