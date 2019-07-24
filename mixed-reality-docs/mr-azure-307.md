---
title: MR 和 Azure 307-機器學習服務
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure Machine Learning Studio。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合現實, 學術, unity, 教學課程, api, 機器學習, ml, machine learning studio, hololens, 沉浸, vr
ms.openlocfilehash: 89d9758dedb6a2389644dda887bfadf5b28f6dd2
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694548"
---
>[!NOTE]
><span data-ttu-id="5f222-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="5f222-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5f222-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="5f222-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5f222-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="5f222-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5f222-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="5f222-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5f222-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="5f222-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5f222-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="5f222-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="5f222-110">MR 和 Azure 307:機器學習</span><span class="sxs-lookup"><span data-stu-id="5f222-110">MR and Azure 307: Machine learning</span></span>

![最終產品-開始](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="5f222-112">在此課程中, 您將瞭解如何使用 Azure Machine Learning Studio, 將 Machine Learning (ML) 功能新增至混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="5f222-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="5f222-113">*Azure Machine Learning Studio*是一項 Microsoft 服務, 可為開發人員提供大量的機器學習服務演算法, 這有助於資料輸入、輸出、準備和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="5f222-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="5f222-114">在這些元件中, 您可以開發預測性分析實驗、逐一查看, 並使用它來定型您的模型。</span><span class="sxs-lookup"><span data-stu-id="5f222-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="5f222-115">依照訓練, 您可以讓模型在 Azure 雲端中運作, 讓它可以對新資料進行評分。</span><span class="sxs-lookup"><span data-stu-id="5f222-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="5f222-116">如需詳細資訊, 請造訪[Azure Machine Learning Studio 頁面](https://azure.microsoft.com/en-au/services/machine-learning-studio/)。</span><span class="sxs-lookup"><span data-stu-id="5f222-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="5f222-117">完成此課程之後, 您將擁有一個混合現實的沉浸式耳機應用程式, 並將學習如何執行下列作業:</span><span class="sxs-lookup"><span data-stu-id="5f222-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="5f222-118">將銷售資料的資料表提供給*Azure Machine Learning Studio*入口網站, 並設計演算法來預測熱門專案的未來銷售。</span><span class="sxs-lookup"><span data-stu-id="5f222-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="5f222-119">建立**Unity 專案**, 它可以接收並解讀來自 ML 服務的預測資料。</span><span class="sxs-lookup"><span data-stu-id="5f222-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="5f222-120">透過在貨位上提供最受歡迎的銷售專案, 以視覺化方式在**Unity 專案**中顯示 predication 資料。</span><span class="sxs-lookup"><span data-stu-id="5f222-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="5f222-121">在您的應用程式中, 您可以決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="5f222-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="5f222-122">本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。</span><span class="sxs-lookup"><span data-stu-id="5f222-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="5f222-123">您的工作是使用您從這個課程取得的知識, 來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="5f222-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="5f222-124">本課程是獨立的教學課程, 不直接牽涉到其他任何混合現實實驗室。</span><span class="sxs-lookup"><span data-stu-id="5f222-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="5f222-125">裝置支援</span><span class="sxs-lookup"><span data-stu-id="5f222-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5f222-126">粗</span><span class="sxs-lookup"><span data-stu-id="5f222-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5f222-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5f222-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5f222-128"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="5f222-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="5f222-129">MR 和 Azure 307:機器學習</span><span class="sxs-lookup"><span data-stu-id="5f222-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="5f222-130">✔️</span><span class="sxs-lookup"><span data-stu-id="5f222-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="5f222-131">✔️</span><span class="sxs-lookup"><span data-stu-id="5f222-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="5f222-132">雖然此課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機, 但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5f222-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="5f222-133">隨著課程的遵循, 您會看到您可能需要用來支援 HoloLens 的任何變更的附注。</span><span class="sxs-lookup"><span data-stu-id="5f222-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="5f222-134">使用 HoloLens 時, 您可能會在語音捕獲期間發現一些回應。</span><span class="sxs-lookup"><span data-stu-id="5f222-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f222-135">必要條件</span><span class="sxs-lookup"><span data-stu-id="5f222-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="5f222-136">本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="5f222-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="5f222-137">也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (5 月 2018)。</span><span class="sxs-lookup"><span data-stu-id="5f222-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="5f222-138">您可以免費使用 [[安裝工具] 文章](install-the-tools.md)中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f222-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="5f222-139">在此課程中, 我們建議您採用下列硬體和軟體:</span><span class="sxs-lookup"><span data-stu-id="5f222-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="5f222-140">[與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦, 可用於沉浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="5f222-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="5f222-141">已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="5f222-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5f222-142">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="5f222-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5f222-143">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="5f222-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5f222-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5f222-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="5f222-145">已啟用開發人員模式的[Windows Mixed Reality 沉浸 (VR) 耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="5f222-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="5f222-146">適用于 Azure 設定和 ML 資料抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="5f222-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="5f222-147">開始之前</span><span class="sxs-lookup"><span data-stu-id="5f222-147">Before you start</span></span>

<span data-ttu-id="5f222-148">為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。</span><span class="sxs-lookup"><span data-stu-id="5f222-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="5f222-149">第1章-Azure 儲存體帳戶設定</span><span class="sxs-lookup"><span data-stu-id="5f222-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="5f222-150">若要使用 Azure Translator API, 您必須設定服務的實例, 讓應用程式可以使用。</span><span class="sxs-lookup"><span data-stu-id="5f222-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="5f222-151">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="5f222-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="5f222-152">如果您還沒有 Azure 帳戶, 您將需要建立一個。</span><span class="sxs-lookup"><span data-stu-id="5f222-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="5f222-153">如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。</span><span class="sxs-lookup"><span data-stu-id="5f222-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="5f222-154">登入之後, 請按一下左側功能表中的 [**儲存體帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="5f222-156">在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。</span><span class="sxs-lookup"><span data-stu-id="5f222-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="5f222-157">在 [**儲存體帳戶**] 索引標籤上, 按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="5f222-159">在 [**建立儲存體帳戶**] 面板中:</span><span class="sxs-lookup"><span data-stu-id="5f222-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="5f222-160">插入您帳戶的**名稱**, 請注意此欄位只接受數位和小寫字母。</span><span class="sxs-lookup"><span data-stu-id="5f222-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="5f222-161">針對 [**部署模型],** 選取 [ **Resource manager**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="5f222-162">針對 [**帳戶類型**], 選取 [**儲存體 (一般用途 v1)** ]。</span><span class="sxs-lookup"><span data-stu-id="5f222-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="5f222-163">針對 [**效能**], 選取 [**標準**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="5f222-164">針對 [複寫], 選取 **[讀取權限-異地-多餘儲存體 (RA-GRS)** ]。</span><span class="sxs-lookup"><span data-stu-id="5f222-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="5f222-165">將 [**需要安全傳輸**] 保留為 [**停用**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="5f222-166">選取**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="5f222-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="5f222-167">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="5f222-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5f222-168">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="5f222-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5f222-169">建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。</span><span class="sxs-lookup"><span data-stu-id="5f222-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="5f222-170">如果您想要深入瞭解 Azure 資源群組, 請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="5f222-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="5f222-171">判斷資源群組的**位置**(如果您要建立新的資源群組)。</span><span class="sxs-lookup"><span data-stu-id="5f222-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="5f222-172">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="5f222-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="5f222-173">某些 Azure 資產僅適用于特定區域。</span><span class="sxs-lookup"><span data-stu-id="5f222-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="5f222-174">您也必須確認您已瞭解適用于此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="5f222-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="5f222-176">按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="5f222-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="5f222-177">建立服務實例之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="5f222-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="5f222-179">第2章-Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="5f222-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="5f222-180">若要使用*Azure Machine Learning*, 您必須設定 Machine Learning 服務的實例, 讓應用程式可以使用。</span><span class="sxs-lookup"><span data-stu-id="5f222-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="5f222-181">在 Azure 入口網站中, 按一下左上角的 [**新增**], 然後搜尋**Machine Learning Studio 工作區**, 按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="5f222-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="5f222-183">[新增] 頁面將會提供**Machine Learning Studio 工作區**服務的描述。</span><span class="sxs-lookup"><span data-stu-id="5f222-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="5f222-184">在此提示的左下方, 按一下 [**建立**] 按鈕, 以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="5f222-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="5f222-185">當您按一下 [**建立**] 之後, 就會出現一個面板, 您必須在其中提供有關新**Machine Learning Studio 服務**的一些詳細資料:</span><span class="sxs-lookup"><span data-stu-id="5f222-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="5f222-186">為此服務實例插入所需的**工作區名稱**。</span><span class="sxs-lookup"><span data-stu-id="5f222-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="5f222-187">選取**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="5f222-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="5f222-188">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="5f222-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5f222-189">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="5f222-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5f222-190">建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。</span><span class="sxs-lookup"><span data-stu-id="5f222-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="5f222-191">如果您想要深入瞭解 Azure 資源群組, 請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="5f222-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="5f222-192">判斷資源群組的**位置**(如果您要建立新的資源群組)。</span><span class="sxs-lookup"><span data-stu-id="5f222-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="5f222-193">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="5f222-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="5f222-194">某些 Azure 資產僅適用于特定區域。</span><span class="sxs-lookup"><span data-stu-id="5f222-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="5f222-195">您應該使用您在上一章中用來建立 Azure 儲存體的相同資源群組。</span><span class="sxs-lookup"><span data-stu-id="5f222-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="5f222-196">在 [**儲存體帳戶**] 區段中, 按一下 [**使用現有**的], 然後按一下下拉式功能表, 然後按一下您在上一章中建立的**儲存體帳戶**。</span><span class="sxs-lookup"><span data-stu-id="5f222-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="5f222-197">從下拉式功能表中, 為您選取適當的**工作區定價層**。</span><span class="sxs-lookup"><span data-stu-id="5f222-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="5f222-198">內**Web 服務方案**區段中，按一下**建立** **新**再插入的文字欄位中的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f222-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="5f222-199">從 [ **Web 服務方案定價層**] 區段中, 選取您選擇的 [定價層]。</span><span class="sxs-lookup"><span data-stu-id="5f222-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="5f222-200">名為**DEVTEST Standard**的開發測試層應免費提供給您。</span><span class="sxs-lookup"><span data-stu-id="5f222-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="5f222-201">您也必須確認您已瞭解適用于此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="5f222-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="5f222-202">按一下 [建立] 。</span><span class="sxs-lookup"><span data-stu-id="5f222-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="5f222-204">按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="5f222-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="5f222-205">建立服務實例之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="5f222-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="5f222-207">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="5f222-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="5f222-209">按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="5f222-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="5f222-210">在顯示的頁面中, 按一下 [**其他連結**] 區段下的 [**啟動 Machine Learning Studio**], 這會將您的瀏覽器導向**Machine Learning Studio**入口網站。</span><span class="sxs-lookup"><span data-stu-id="5f222-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="5f222-212">使用位於右上方或中央的 [登**入**] 按鈕, 登入您的 Machine Learning Studio。</span><span class="sxs-lookup"><span data-stu-id="5f222-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="5f222-214">第3章-Machine Learning Studio:資料集設定</span><span class="sxs-lookup"><span data-stu-id="5f222-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="5f222-215">Machine Learning 演算法的工作方式之一是分析現有的資料, 然後根據現有的資料集嘗試預測未來的結果。</span><span class="sxs-lookup"><span data-stu-id="5f222-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="5f222-216">這通常表示您擁有的資料愈多, 演算法將在預測未來結果時愈好。</span><span class="sxs-lookup"><span data-stu-id="5f222-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="5f222-217">範例資料表會提供給您, 在此課程中稱為[ProductsTableCSV, 而且可以在這裡下載](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。</span><span class="sxs-lookup"><span data-stu-id="5f222-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f222-218">上述 .zip 檔案包含**ProductsTableCSV**和**unitypackage**, 您將在[第6章](#chapter-6---importing-the-mlproducts-unity-package)中需要此檔案。</span><span class="sxs-lookup"><span data-stu-id="5f222-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="5f222-219">這一章也提供此套件, 但與 csv 檔案分開。</span><span class="sxs-lookup"><span data-stu-id="5f222-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="5f222-220">此範例資料集包含每一年2017之每小時的最佳銷售物件記錄。</span><span class="sxs-lookup"><span data-stu-id="5f222-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio:資料集設定](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="5f222-222">例如, 在2017的第1天, 下午 (小時 13), 最佳銷售專案是 salt 和辣椒。</span><span class="sxs-lookup"><span data-stu-id="5f222-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="5f222-223">這個範例資料表包含9998專案。</span><span class="sxs-lookup"><span data-stu-id="5f222-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="5f222-224">返回**Machine Learning Studio**入口網站, 並將此資料表新增為 ML 的**資料集**。</span><span class="sxs-lookup"><span data-stu-id="5f222-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="5f222-225">若要這麼做, 請按一下畫面左下角的 [ **+ 新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5f222-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio:資料集設定](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="5f222-227">區段會從底部出現, 並在左側有導覽面板。</span><span class="sxs-lookup"><span data-stu-id="5f222-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="5f222-228">**從 [本機**檔案], 按一下 [**資料集**], 然後從 [] 右邊。</span><span class="sxs-lookup"><span data-stu-id="5f222-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio:資料集設定](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="5f222-230">依照下列步驟來上傳新的**資料集**:</span><span class="sxs-lookup"><span data-stu-id="5f222-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="5f222-231">[上傳] 視窗隨即出現, 您可以在其中**流覽**硬碟以尋找新的資料集。</span><span class="sxs-lookup"><span data-stu-id="5f222-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio:資料集設定](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="5f222-233">選取之後, 返回 [上傳] 視窗, 將核取方塊保留為 [未核取]。</span><span class="sxs-lookup"><span data-stu-id="5f222-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="5f222-234">在下面的文字欄位中, 輸入**ProductsTableCSV**做為資料集的名稱 (但應該自動加入)。</span><span class="sxs-lookup"><span data-stu-id="5f222-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="5f222-235">使用 [**類型**] 的下拉式功能表, 選取**具有標頭 (.Csv) 的一般 CSV**檔案。</span><span class="sxs-lookup"><span data-stu-id="5f222-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="5f222-236">按下 [上傳] 視窗右下方的 [滴答], 將會上傳您的**資料集**。</span><span class="sxs-lookup"><span data-stu-id="5f222-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="5f222-237">第4章-Machine Learning Studio:實驗</span><span class="sxs-lookup"><span data-stu-id="5f222-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="5f222-238">建立機器學習系統之前, 您必須先建立實驗, 以驗證您對資料的理論。</span><span class="sxs-lookup"><span data-stu-id="5f222-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="5f222-239">有了結果, 您就會知道您是否需要更多資料, 或者資料與可能的結果之間沒有相互關聯。</span><span class="sxs-lookup"><span data-stu-id="5f222-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="5f222-240">若要開始建立實驗:</span><span class="sxs-lookup"><span data-stu-id="5f222-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="5f222-241">再次按一下頁面左下方的 [ **+ 新增**] 按鈕, 然後按一下 [**實驗** > ] [**空白實驗**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="5f222-243">新的頁面會顯示空白實驗:</span><span class="sxs-lookup"><span data-stu-id="5f222-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="5f222-244">從左側面板中, 展開 [**已儲存的資料集** > ] [**我的資料集**], 然後將**ProductsTableCSV**拖曳到**實驗畫布**上。</span><span class="sxs-lookup"><span data-stu-id="5f222-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="5f222-246">在左側面板中, 展開 [**資料轉換** > **範例] 和 [分割**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="5f222-247">然後將 [**分割資料**] 專案拖曳至**實驗畫布**。</span><span class="sxs-lookup"><span data-stu-id="5f222-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="5f222-248">分割資料項目會將資料集分割成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="5f222-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="5f222-249">您將用來訓練機器學習服務演算法的其中一個部分。</span><span class="sxs-lookup"><span data-stu-id="5f222-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="5f222-250">第二個部分將用來評估產生之演算法的精確度。</span><span class="sxs-lookup"><span data-stu-id="5f222-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="5f222-252">在右面板中 (當選取畫布上的 [分割資料項目] 時), 將**第一個輸出資料集中的資料列分數**編輯為**0.7**。</span><span class="sxs-lookup"><span data-stu-id="5f222-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="5f222-253">這會將資料分割成兩個部分, 第一個部分將是 70% 的資料, 而第二個部分將是剩餘的 30%。</span><span class="sxs-lookup"><span data-stu-id="5f222-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="5f222-254">若要確保資料會隨機分割, 請確定 [**隨機分割**] 核取方塊保持核取狀態。</span><span class="sxs-lookup"><span data-stu-id="5f222-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="5f222-256">將畫布上 [ **ProductsTableCSV** ] 專案基底的連接拖曳至 [分割] 資料項目的頂端。</span><span class="sxs-lookup"><span data-stu-id="5f222-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="5f222-257">這會連接專案, 並將**ProductsTableCSV**資料集輸出 (資料) 傳送至分割資料輸入。</span><span class="sxs-lookup"><span data-stu-id="5f222-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="5f222-259">在左側的 [**實驗**] 面板中, 展開 [ **Machine Learning**  > **訓練**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="5f222-260">將**訓練模型**專案向外拖曳至實驗畫布。</span><span class="sxs-lookup"><span data-stu-id="5f222-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="5f222-261">您的畫布看起來應該與下面相同。</span><span class="sxs-lookup"><span data-stu-id="5f222-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="5f222-263">從 [**分割資料項目**] 的***左下方***, 將 [連接] 拖曳至 [**定型模型**] 專案的**右上**角。</span><span class="sxs-lookup"><span data-stu-id="5f222-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="5f222-264">定型模型會使用從資料集分割的第一個 70% 來定型演算法。</span><span class="sxs-lookup"><span data-stu-id="5f222-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="5f222-266">選取畫布上的 [**定型模型**] 專案, 然後在 [**屬性**] 面板 (位於瀏覽器視窗右側) 中, 按一下 [**啟動資料行選取器**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5f222-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="5f222-267">在文字方塊中輸入**product** , 然後按**enter**鍵, *product*將會設定為數據行來定型預測。</span><span class="sxs-lookup"><span data-stu-id="5f222-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="5f222-268">在此之後, 按一下右下角的**滴答**, 關閉選取對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5f222-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="5f222-270">您將訓練**多元羅吉斯回歸**演算法, 根據一天中的一小時和日期來預測最銷售的**產品**。</span><span class="sxs-lookup"><span data-stu-id="5f222-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="5f222-271">這不在本檔的討論範圍內, 以說明 Azure Machine Learning studio 所提供之不同演算法的詳細資料, 但您可以從[Machine Learning 演算法](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)功能提要中深入瞭解</span><span class="sxs-lookup"><span data-stu-id="5f222-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="5f222-272">從左側的 [實驗專案] 面板中, 展開 [ **Machine Learning**  > **初始化模型** > **分類**], 然後將 [**多元羅吉斯回歸**] 專案拖曳至實驗畫布。</span><span class="sxs-lookup"><span data-stu-id="5f222-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="5f222-273">將輸出從**多元羅吉斯回歸**的底部, 連接到**訓練模型**專案的左上角輸入。</span><span class="sxs-lookup"><span data-stu-id="5f222-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="5f222-275">在左側面板中的實驗專案清單中, 展開 [ **Machine Learning**  > **分數**], 然後將 [**評分模型**] 專案拖曳到畫布上。</span><span class="sxs-lookup"><span data-stu-id="5f222-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="5f222-276">將輸出從**訓練模型**的底部, 連接到**評分模型**的左上角輸入。</span><span class="sxs-lookup"><span data-stu-id="5f222-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="5f222-277">將 [**分割資料**] 的右下方輸出連接到 [**評分模型**] 專案的右上方輸入。</span><span class="sxs-lookup"><span data-stu-id="5f222-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="5f222-279">在左側面板中的**實驗**專案清單中, 展開 [ **Machine Learning**  > **評估**], 然後將 [**評估模型**] 專案拖曳至畫布上。</span><span class="sxs-lookup"><span data-stu-id="5f222-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="5f222-280">將**評分模型**的輸出連接到**評估模型**的左上角輸入。</span><span class="sxs-lookup"><span data-stu-id="5f222-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="5f222-282">您已經建立您的第一個 Machine Learning 實驗。</span><span class="sxs-lookup"><span data-stu-id="5f222-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="5f222-283">您現在可以儲存並執行實驗。</span><span class="sxs-lookup"><span data-stu-id="5f222-283">You can now save and run the experiment.</span></span> <span data-ttu-id="5f222-284">在頁面底部的功能表中, 按一下 [**儲存**] 按鈕以儲存您的實驗, 然後按一下 [**執行**] 以啟動實驗。</span><span class="sxs-lookup"><span data-stu-id="5f222-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="5f222-286">您可以在畫布右上角查看實驗的**狀態**。</span><span class="sxs-lookup"><span data-stu-id="5f222-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="5f222-287">請稍候片刻, 讓實驗完成。</span><span class="sxs-lookup"><span data-stu-id="5f222-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="5f222-288">如果您有大型 (實際) 的資料集, 可能是實驗需要數小時才會執行。</span><span class="sxs-lookup"><span data-stu-id="5f222-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="5f222-290">以滑鼠右鍵按一下畫布中的 [**評估模型**] 專案, 然後從內容功能表中, 將滑鼠停留在 [**評估結果**] 上, 然後選取 [**視覺化**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="5f222-292">將會顯示評估結果, 顯示預測的結果與實際結果。</span><span class="sxs-lookup"><span data-stu-id="5f222-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="5f222-293">這會使用先前分割的原始資料集 30% 來評估模型。</span><span class="sxs-lookup"><span data-stu-id="5f222-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="5f222-294">您可以看到結果並不大, 在理想的情況下, 每個資料列中的最大數目就是資料行中反白顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="5f222-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="5f222-296">關閉**結果**。</span><span class="sxs-lookup"><span data-stu-id="5f222-296">Close the **Results**.</span></span>

24. <span data-ttu-id="5f222-297">若要使用您剛定型的 Machine Learning 模型, 您必須將它公開為**Web 服務**。</span><span class="sxs-lookup"><span data-stu-id="5f222-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="5f222-298">若要這樣做, 請在頁面底部的功能表中按一下 [**設定 Web 服務**] 功能表項目, 然後按一下 [預測性**Web 服務**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="5f222-300">將建立新的索引標籤, 併合並定型模型來建立新的 web 服務。</span><span class="sxs-lookup"><span data-stu-id="5f222-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="5f222-301">在頁面底部的功能表中, 按一下 [**儲存**], 然後按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="5f222-302">您會在實驗畫布右上角看到更新的狀態。</span><span class="sxs-lookup"><span data-stu-id="5f222-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="5f222-304">完成執行後, [**部署 Web 服務**] 按鈕將會出現在頁面底部。</span><span class="sxs-lookup"><span data-stu-id="5f222-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="5f222-305">您已準備好部署 web 服務。</span><span class="sxs-lookup"><span data-stu-id="5f222-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="5f222-306">在頁面底部的功能表中, 按一下 [**部署 Web 服務**(傳統)]。</span><span class="sxs-lookup"><span data-stu-id="5f222-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="5f222-308">您的瀏覽器可能會提示您允許快顯視窗, 這是您應該**允許**的, 但如果 [部署] 頁面未顯示, 您可能需要再次按下 [**部署 Web 服務**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="5f222-309">建立實驗之後, 您會被重新導向至**儀表板**頁面, 其中會顯示您的**API 金鑰**。</span><span class="sxs-lookup"><span data-stu-id="5f222-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="5f222-310">將它複製到「記事本」, 很快就會在您的程式碼中需要它。</span><span class="sxs-lookup"><span data-stu-id="5f222-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="5f222-311">記下 API 金鑰之後, 請按一下金鑰底下 [**預設端點**] 區段中的 [**要求/回應**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5f222-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="5f222-313">如果您按一下此頁面中的 [測試], 您將能夠輸入輸入資料並查看輸出。</span><span class="sxs-lookup"><span data-stu-id="5f222-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="5f222-314">輸入 [**日**] 和 [**小時**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="5f222-315">將 [**產品**] 專案保留空白。</span><span class="sxs-lookup"><span data-stu-id="5f222-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="5f222-316">然後按一下 [**確認**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5f222-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="5f222-317">頁面底部的輸出會顯示 JSON, 代表每個產品的可能性。</span><span class="sxs-lookup"><span data-stu-id="5f222-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="5f222-318">隨即會開啟新的網頁, 並顯示有關 Machine Learning Studio 所需之要求結構的指示和一些範例。</span><span class="sxs-lookup"><span data-stu-id="5f222-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="5f222-319">將此頁面中顯示的**要求 URI**複製到您的 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="5f222-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="5f222-321">您現在已建立機器學習系統, 以根據歷程記錄購買資料, 提供最有可能的產品銷售, 並與一年中的一天和一天的時間產生關聯。</span><span class="sxs-lookup"><span data-stu-id="5f222-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="5f222-322">若要呼叫 web 服務, 您將需要服務端點的 URL 和服務的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="5f222-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="5f222-323">按一下頂端功能表中的 [取用] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5f222-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="5f222-324">[**耗用量**資訊] 頁面將會顯示您從程式碼呼叫 web 服務時所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="5f222-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="5f222-325">請複製**主要金鑰**和**要求-回應**URL。</span><span class="sxs-lookup"><span data-stu-id="5f222-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="5f222-326">您將在下一章中需要這些功能。</span><span class="sxs-lookup"><span data-stu-id="5f222-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="5f222-327">第5章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="5f222-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="5f222-328">設定和測試混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="5f222-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="5f222-329">在此課程中, 您將**不**需要有動作控制器。</span><span class="sxs-lookup"><span data-stu-id="5f222-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="5f222-330">如果您需要支援設定沉浸式頭戴式裝置, 請按一下[這裡](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="5f222-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="5f222-331">開啟**Unity** , 並建立名為**MR\_MachineLearning**的新 unity 專案。</span><span class="sxs-lookup"><span data-stu-id="5f222-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="5f222-332">請確定 [專案類型] 設定為 [ **3d**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="5f222-333">在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="5f222-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="5f222-334">移至 [**編輯** > **喜好**設定], 然後在新視窗中, 流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="5f222-335">將**外部腳本編輯器**變更為**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="5f222-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="5f222-336">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5f222-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="5f222-337">接下來, 移  > 至 [檔案] [**組建設定**], 然後按一下 [***切換平臺***] 按鈕, 將平臺切換至**通用 Windows 平臺**。</span><span class="sxs-lookup"><span data-stu-id="5f222-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="5f222-338">也請確定:</span><span class="sxs-lookup"><span data-stu-id="5f222-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="5f222-339">[**目標裝置**] 已設定為 [**任何裝置**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="5f222-340">若為 Microsoft HoloLens, 請將**目標裝置**設定為*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="5f222-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="5f222-341">[**組建類型**] 設定為 [ **D3D**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="5f222-342">**SDK**設定為 [**最新安裝**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="5f222-343">**Visual Studio 版本**設定為 [**最新安裝**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="5f222-344">[**組建與執行**] 設定為 [**本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="5f222-345">請不要擔心立即設定**場景**, 因為稍後會提供這些資訊。</span><span class="sxs-lookup"><span data-stu-id="5f222-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="5f222-346">其餘的設定現在應保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="5f222-346">The remaining settings should be left as default for now.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="5f222-348">在 [**組建設定**] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測**器**所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="5f222-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="5f222-349">在此面板中, 需要驗證幾項設定:</span><span class="sxs-lookup"><span data-stu-id="5f222-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="5f222-350">在 [**其他設定**] 索引標籤中:</span><span class="sxs-lookup"><span data-stu-id="5f222-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="5f222-351">**腳本** **執行階段版本**應該是**實驗**性 (.net 4.6 對等用法)</span><span class="sxs-lookup"><span data-stu-id="5f222-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="5f222-352">**腳本後端**應該是 ***.net***</span><span class="sxs-lookup"><span data-stu-id="5f222-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="5f222-353">**API 相容性層級**應該是 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="5f222-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="5f222-355">在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:</span><span class="sxs-lookup"><span data-stu-id="5f222-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="5f222-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="5f222-356">**InternetClient**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="5f222-358">在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]</span><span class="sxs-lookup"><span data-stu-id="5f222-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="5f222-360">回到**組建設定** *Unity C#* 專案已不再呈現灰色;勾選 [] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5f222-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="5f222-361">關閉 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5f222-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="5f222-362">儲存您的專案 (檔案 **> 儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="5f222-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="5f222-363">第6章-匯入 MLProducts Unity 封裝</span><span class="sxs-lookup"><span data-stu-id="5f222-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="5f222-364">在此課程中, 您將需要下載名為[**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)的 Unity 資產套件。</span><span class="sxs-lookup"><span data-stu-id="5f222-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="5f222-365">此套件隨附于場景, 所有物件都在該預先建立中, 因此您可以專注于讓它運作。</span><span class="sxs-lookup"><span data-stu-id="5f222-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="5f222-366">由於場景安裝結構的目的, 我們會提供**ShelfKeeper**腳本, 但只會保存公用變數。</span><span class="sxs-lookup"><span data-stu-id="5f222-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="5f222-367">您將需要執行所有其他區段。</span><span class="sxs-lookup"><span data-stu-id="5f222-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="5f222-368">若要匯入此封裝:</span><span class="sxs-lookup"><span data-stu-id="5f222-368">To import this package:</span></span>

1.  <span data-ttu-id="5f222-369">在您前方的 Unity 儀表板中, 按一下畫面頂端功能表中的 [**資產**], 然後按一下 [匯**入套件]、[自訂套件**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="5f222-371">使用檔案選擇器選取**unitypackage**套件, 然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="5f222-372">系統會顯示此資產的元件清單。</span><span class="sxs-lookup"><span data-stu-id="5f222-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="5f222-373">按一下 [匯**入**] 確認匯入。</span><span class="sxs-lookup"><span data-stu-id="5f222-373">Confirm the import by clicking **Import**.</span></span>

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="5f222-375">完成匯入之後, 您會發現 Unity**專案面板**中出現一些新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5f222-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="5f222-376">這些是3D 模型, 也是您將使用之預先製作場景中的個別材質。</span><span class="sxs-lookup"><span data-stu-id="5f222-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="5f222-377">在此課程中, 您將會撰寫大部分的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f222-377">You will write the majority of the code in this course.</span></span>

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="5f222-379">在 [**專案面板**] 資料夾中, 按一下 [**場景**] 資料夾, 然後按兩下內的場景 (稱為**MR_MachineLearningScene**)。</span><span class="sxs-lookup"><span data-stu-id="5f222-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="5f222-380">場景隨即開啟 (請參閱下圖)。</span><span class="sxs-lookup"><span data-stu-id="5f222-380">The scene will open (see image below).</span></span> <span data-ttu-id="5f222-381">如果缺少紅色菱形, 只要按一下**遊戲面板**右上方的 [ **Gizmos** ] 按鈕即可。</span><span class="sxs-lookup"><span data-stu-id="5f222-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="5f222-383">第7章-檢查 Unity 中的 Dll</span><span class="sxs-lookup"><span data-stu-id="5f222-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="5f222-384">若要利用 JSON 程式庫 (用於序列化和還原序列化), 已使用您帶入的封裝來執行 Newtonsoft DLL。</span><span class="sxs-lookup"><span data-stu-id="5f222-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="5f222-385">程式庫應具有正確的設定, 但值得檢查 (尤其是如果您有程式碼無法運作的問題)。</span><span class="sxs-lookup"><span data-stu-id="5f222-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="5f222-386">方法如下：</span><span class="sxs-lookup"><span data-stu-id="5f222-386">To do so:</span></span>

-  <span data-ttu-id="5f222-387">以滑鼠左鍵按一下 [外掛程式] 資料夾內的 Newtonsoft 檔案, 然後查看 [**檢查] 面板**。</span><span class="sxs-lookup"><span data-stu-id="5f222-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="5f222-388">請確定已核取**任何平臺**。</span><span class="sxs-lookup"><span data-stu-id="5f222-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="5f222-389">移至 [ **UWP]** 索引標籤, 並確定 [**不核取處理**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![匯入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="5f222-391">第8章-建立 ShelfKeeper 類別</span><span class="sxs-lookup"><span data-stu-id="5f222-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="5f222-392">**ShelfKeeper**類別裝載的方法, 可控制在場景中衍生的 UI 和產品。</span><span class="sxs-lookup"><span data-stu-id="5f222-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="5f222-393">在匯入的套件中, 您將會獲得這個類別, 但它不完整。</span><span class="sxs-lookup"><span data-stu-id="5f222-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="5f222-394">現在是完成該類別的時機:</span><span class="sxs-lookup"><span data-stu-id="5f222-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="5f222-395">按兩下 [**腳本**] 資料夾中的**ShelfKeeper**腳本, 以**Visual Studio 2017**開啟它。</span><span class="sxs-lookup"><span data-stu-id="5f222-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="5f222-396">將腳本中現有的所有程式碼取代為下列程式碼, 這會設定時間和日期, 並具有可顯示產品的方法。</span><span class="sxs-lookup"><span data-stu-id="5f222-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

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

3.  <span data-ttu-id="5f222-397">請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。</span><span class="sxs-lookup"><span data-stu-id="5f222-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="5f222-398">回到 Unity 編輯器, 檢查**ShelfKeeper**類別看起來如下所示:</span><span class="sxs-lookup"><span data-stu-id="5f222-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="5f222-400">如果您的腳本沒有參考目標 (也就是*日期 (文本網格)* ), 只需從 [階層]**面板**將對應的物件拖曳至目標欄位。</span><span class="sxs-lookup"><span data-stu-id="5f222-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="5f222-401">如需說明, 請參閱以下內容:</span><span class="sxs-lookup"><span data-stu-id="5f222-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="5f222-402">在**ShelfKeeper**元件腳本中, 以滑鼠左鍵按一下產生**點**陣列, 以開啟它。</span><span class="sxs-lookup"><span data-stu-id="5f222-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="5f222-403">子區段會顯示稱為「**大小**」, 表示陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="5f222-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="5f222-404">在 [**大小**] 旁的文字方塊中輸入**3** , 然後按**enter**鍵, 下方會建立三個位置。</span><span class="sxs-lookup"><span data-stu-id="5f222-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="5f222-405">在階層中展開 [**時間顯示**] 物件 (以滑鼠左鍵按一下其旁邊的箭號)。</span><span class="sxs-lookup"><span data-stu-id="5f222-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="5f222-406">接著, 按一下階層內的***主要攝影機***, 讓偵測**器**顯示其資訊。</span><span class="sxs-lookup"><span data-stu-id="5f222-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="5f222-407">在 [階層]**面板**中選取**主要相機**。</span><span class="sxs-lookup"><span data-stu-id="5f222-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="5f222-408">從 [階層]**面板**中, 將 [**日期**] 和 [**時間**] 物件拖曳至**ShelfKeeper**元件中**主要攝影機**的偵測**器**內的**日期文字**和**時間文字**位置。</span><span class="sxs-lookup"><span data-stu-id="5f222-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="5f222-409">將 [階層]**面板**中的 [產生**點**] (在 [*貨位*] 物件下方) 拖曳至 [**衍生點**] 陣列底下的**3**個專案參考目標, 如影像中所示。</span><span class="sxs-lookup"><span data-stu-id="5f222-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="5f222-411">第9章-建立 ProductPrediction 類別</span><span class="sxs-lookup"><span data-stu-id="5f222-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="5f222-412">下一個您即將建立的類別是**ProductPrediction**類別。</span><span class="sxs-lookup"><span data-stu-id="5f222-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="5f222-413">此類別負責:</span><span class="sxs-lookup"><span data-stu-id="5f222-413">This class is responsible for:</span></span>

-   <span data-ttu-id="5f222-414">查詢**Machine Learning 的服務**實例, 並提供目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="5f222-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="5f222-415">將 JSON 回應還原序列化為可用的資料。</span><span class="sxs-lookup"><span data-stu-id="5f222-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="5f222-416">解讀資料, 並抓取3個建議的產品。</span><span class="sxs-lookup"><span data-stu-id="5f222-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="5f222-417">呼叫**ShelfKeeper**類別方法, 以顯示場景中的資料。</span><span class="sxs-lookup"><span data-stu-id="5f222-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="5f222-418">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="5f222-418">To create this class:</span></span>

1.  <span data-ttu-id="5f222-419">移至 [**專案] 面板**中的 [**腳本**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5f222-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="5f222-420">以滑鼠右鍵按一下資料夾內的 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="5f222-421">呼叫腳本**ProductPrediction**。</span><span class="sxs-lookup"><span data-stu-id="5f222-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="5f222-422">按兩下新的**ProductPrediction**腳本, 以**Visual Studio 2017**開啟它。</span><span class="sxs-lookup"><span data-stu-id="5f222-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="5f222-423">如果出現 [偵測**到檔案修改**] 對話方塊, 請按一下 [**重載解決方案**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="5f222-424">將下列命名空間新增至 ProductPrediction 類別的頂端:</span><span class="sxs-lookup"><span data-stu-id="5f222-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

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

6.  <span data-ttu-id="5f222-425">在**ProductPrediction**類別中, 插入下列兩個由多個嵌套類別所組成的物件。</span><span class="sxs-lookup"><span data-stu-id="5f222-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="5f222-426">這些類別是用來序列化和還原序列化 Machine Learning 服務的 JSON。</span><span class="sxs-lookup"><span data-stu-id="5f222-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

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

7.  <span data-ttu-id="5f222-427">然後, 在先前的程式碼上方加入下列變數 (如此一來, JSON 相關程式碼就會在腳本的底部、所有其他程式碼之下, 以及從外):</span><span class="sxs-lookup"><span data-stu-id="5f222-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

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
    > <span data-ttu-id="5f222-428">請務必將 [**主要金鑰**] 和 [**要求-回應] 端點**從 Machine Learning 入口網站插入此處的變數。</span><span class="sxs-lookup"><span data-stu-id="5f222-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="5f222-429">下列影像顯示您從何處取得金鑰和端點。</span><span class="sxs-lookup"><span data-stu-id="5f222-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="5f222-432">將此程式碼插入**Start ()** 方法中。</span><span class="sxs-lookup"><span data-stu-id="5f222-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="5f222-433">當類別初始化時, 會呼叫**Start ()** 方法:</span><span class="sxs-lookup"><span data-stu-id="5f222-433">The **Start()** method is called when the class initializes:</span></span>

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

9.  <span data-ttu-id="5f222-434">以下是從 Windows 收集日期和時間的方法, 並將它轉換成 Machine Learning 實驗可用來與資料表中所儲存資料進行比較的格式。</span><span class="sxs-lookup"><span data-stu-id="5f222-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

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

10. <span data-ttu-id="5f222-435">您可以**刪除** **Update ()** 方法, 因為這個類別不會使用它。</span><span class="sxs-lookup"><span data-stu-id="5f222-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="5f222-436">新增下列方法, 這會將目前的日期和時間傳達給 Machine Learning 端點, 並以 JSON 格式接收回應。</span><span class="sxs-lookup"><span data-stu-id="5f222-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

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

12. <span data-ttu-id="5f222-437">新增下列方法, 這會負責將 JSON 回應還原序列化, 以及將還原序列化的結果與**ShelfKeeper**類別通訊。</span><span class="sxs-lookup"><span data-stu-id="5f222-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="5f222-438">此結果會是預測為目前日期和時間銷售最大的三個專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f222-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="5f222-439">將下列程式碼插入**ProductPrediction**類別的先前方法底下。</span><span class="sxs-lookup"><span data-stu-id="5f222-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

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

13. <span data-ttu-id="5f222-440">儲存**Visual Studio**並返回**Unity**。</span><span class="sxs-lookup"><span data-stu-id="5f222-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="5f222-441">將 [ **ProductPrediction**類別] 腳本從 [**腳本**] 資料夾拖曳到**主要相機**物件上。</span><span class="sxs-lookup"><span data-stu-id="5f222-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="5f222-442">儲存場景和專案**檔** > **儲存場景/**  > 檔案**儲存專案**。</span><span class="sxs-lookup"><span data-stu-id="5f222-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="5f222-443">第10章-建立 UWP 解決方案</span><span class="sxs-lookup"><span data-stu-id="5f222-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="5f222-444">現在可以將您的專案建立成 UWP 解決方案, 使其可以獨立應用程式的形式執行。</span><span class="sxs-lookup"><span data-stu-id="5f222-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="5f222-445">若要建立:</span><span class="sxs-lookup"><span data-stu-id="5f222-445">To Build:</span></span>

1.  <span data-ttu-id="5f222-446">按一下 > [檔案] [**儲存場景**] 以儲存目前的場景。</span><span class="sxs-lookup"><span data-stu-id="5f222-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="5f222-447">移至  > 檔案**組建設定**</span><span class="sxs-lookup"><span data-stu-id="5f222-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="5f222-448">選取名為 [ **Unity C#專案**] 的方塊 (這很重要, 因為它可讓您在組建完成後編輯類別)。</span><span class="sxs-lookup"><span data-stu-id="5f222-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="5f222-449">按一下 [**新增開啟的場景**],</span><span class="sxs-lookup"><span data-stu-id="5f222-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="5f222-450">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="5f222-450">Click **Build**.</span></span>

    ![建立 UWP 解決方案](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="5f222-452">系統會提示您選取要在其中建立解決方案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5f222-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="5f222-453">建立**組建**資料夾, 並在該資料夾內建立另一個資料夾, 並使用您選擇的適當名稱。</span><span class="sxs-lookup"><span data-stu-id="5f222-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="5f222-454">按一下您的新資料夾, 然後按一下 [**選取資料夾**], 在該位置開始組建。</span><span class="sxs-lookup"><span data-stu-id="5f222-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![建立 UWP 解決方案](images/AzureLabs-Lab7-55.png)

    ![建立 UWP 解決方案](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="5f222-457">Unity 完成建立之後 (可能需要一些時間), 它會在組建的位置開啟 [檔案**瀏覽器**] 視窗 (請檢查您的工作列, 因為它不一定會出現在視窗的上方, 但會通知您加入新的視窗)。</span><span class="sxs-lookup"><span data-stu-id="5f222-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="5f222-458">第11章-部署您的應用程式</span><span class="sxs-lookup"><span data-stu-id="5f222-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="5f222-459">若要部署您的應用程式:</span><span class="sxs-lookup"><span data-stu-id="5f222-459">To deploy your application:</span></span>

1.  <span data-ttu-id="5f222-460">流覽至新的 Unity 組建 (**應用程式**資料夾), 然後使用**Visual Studio**開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="5f222-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="5f222-461">在 Visual Studio 開啟的情況下, 您需要還原 NuGet 套件, 您可以在 MachineLearningLab_Build 解決方案上按一下滑鼠右鍵, 從 [方案總管] (位於 [Visual Studio] 右邊), 然後按一下 [還原 NuGet 套件] 來完成:</span><span class="sxs-lookup"><span data-stu-id="5f222-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![新增 NuGet 封裝](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="5f222-463">在 [解決方案設定] 中, 選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="5f222-464">在解決方案平臺中, 選取 [ **x86**]、[**本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="5f222-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="5f222-465">針對 Microsoft HoloLens, 您可能會發現將此設定為 [*遠端電腦*] 比較容易, 因此您不會行動網卡到電腦。</span><span class="sxs-lookup"><span data-stu-id="5f222-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="5f222-466">不過, 您也必須執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="5f222-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="5f222-467">知道您的 HoloLens 的**IP 位址**, 您可以在 *> Network & Internet > Wi-fi > Advanced 選項*的 [設定] 中找到它;IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="5f222-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="5f222-468">請確定**開發人員模式**已**開啟**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >* 。</span><span class="sxs-lookup"><span data-stu-id="5f222-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![新增 NuGet 封裝](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="5f222-470">移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="5f222-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="5f222-471">您的應用程式現在應該會出現在已安裝的應用程式清單中, 並準備好啟動。</span><span class="sxs-lookup"><span data-stu-id="5f222-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="5f222-472">當您執行 Mixed Reality 應用程式時, 您會看到在 Unity 場景中設定的工作臺, 而從初始化開始, 將會提取您在 Azure 中設定的資料。</span><span class="sxs-lookup"><span data-stu-id="5f222-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="5f222-473">資料將會在您的應用程式中還原序列化, 而目前日期和時間的三個最上層結果將以視覺化方式提供, 做為工作臺上的三個模型。</span><span class="sxs-lookup"><span data-stu-id="5f222-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="5f222-474">您完成的 Machine Learning 應用程式</span><span class="sxs-lookup"><span data-stu-id="5f222-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="5f222-475">恭喜, 您建立了一個混合現實應用程式, 利用 Azure Machine Learning 來進行資料預測, 並將它顯示在您的場景上。</span><span class="sxs-lookup"><span data-stu-id="5f222-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![新增 NuGet 封裝](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="5f222-477">練習</span><span class="sxs-lookup"><span data-stu-id="5f222-477">Exercise</span></span>

<span data-ttu-id="5f222-478">**練習1**</span><span class="sxs-lookup"><span data-stu-id="5f222-478">**Exercise 1**</span></span>

<span data-ttu-id="5f222-479">請試驗您應用程式的排序次序, 並將三個底部的預測顯示在貨架上, 因為這項資料可能也會很有用。</span><span class="sxs-lookup"><span data-stu-id="5f222-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="5f222-480">**練習2**</span><span class="sxs-lookup"><span data-stu-id="5f222-480">**Exercise 2**</span></span>

<span data-ttu-id="5f222-481">使用**Azure 資料表**會在新資料表中填入氣象資訊, 並使用該資料建立新的實驗。</span><span class="sxs-lookup"><span data-stu-id="5f222-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
