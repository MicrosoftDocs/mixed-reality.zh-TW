---
title: MR 和 Azure 301-語言翻譯
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure 翻譯工具文字 API。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合現實，學術，unity，教學課程，api，翻譯工具文字，hololens，沉浸，vr
ms.openlocfilehash: 012eb5522c866e9e0f1caf5e4024305af07e298c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438523"
---
>[!NOTE]
><span data-ttu-id="0cd46-104">混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="0cd46-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0cd46-105">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="0cd46-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0cd46-106">這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="0cd46-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0cd46-107">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="0cd46-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0cd46-108">未來將會有一系列新的教學課程，將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="0cd46-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0cd46-109">此通知會在張貼時，使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="0cd46-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="0cd46-110">MR 和 Azure 301：語言翻譯</span><span class="sxs-lookup"><span data-stu-id="0cd46-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="0cd46-111">在此課程中，您將瞭解如何使用 Azure 認知服務搭配翻譯工具文字 API，將翻譯功能新增至混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cd46-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![最終產品](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="0cd46-113">翻譯工具文字 API 是一項轉譯服務，以近乎即時的方式運作。</span><span class="sxs-lookup"><span data-stu-id="0cd46-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="0cd46-114">此服務是以雲端為基礎，而使用 REST API 呼叫，應用程式可以使用類神經機器翻譯技術，將文字翻譯成另一種語言。</span><span class="sxs-lookup"><span data-stu-id="0cd46-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="0cd46-115">如需詳細資訊，請造訪[Azure 翻譯工具文字 API 頁面](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。</span><span class="sxs-lookup"><span data-stu-id="0cd46-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="0cd46-116">完成本課程之後，您將會有一個混合現實應用程式，可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0cd46-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="0cd46-117">使用者會說話連接到沉浸式（VR）耳機（或 HoloLens 的內建麥克風）的麥克風。</span><span class="sxs-lookup"><span data-stu-id="0cd46-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="0cd46-118">應用程式將會捕捉聽寫，並將其傳送至 Azure 翻譯工具文字 API。</span><span class="sxs-lookup"><span data-stu-id="0cd46-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="0cd46-119">轉譯結果會顯示在 Unity 場景的簡單 UI 群組中。</span><span class="sxs-lookup"><span data-stu-id="0cd46-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="0cd46-120">本課程將告訴您如何將 Translator 服務的結果放入 Unity 型範例應用程式中。</span><span class="sxs-lookup"><span data-stu-id="0cd46-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="0cd46-121">您必須將這些概念套用到您可能正在建立的自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cd46-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="0cd46-122">裝置支援</span><span class="sxs-lookup"><span data-stu-id="0cd46-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0cd46-123">粗</span><span class="sxs-lookup"><span data-stu-id="0cd46-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0cd46-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0cd46-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0cd46-125"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="0cd46-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0cd46-126">MR 和 Azure 301：語言翻譯</span><span class="sxs-lookup"><span data-stu-id="0cd46-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="0cd46-127">✔️</span><span class="sxs-lookup"><span data-stu-id="0cd46-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0cd46-128">✔️</span><span class="sxs-lookup"><span data-stu-id="0cd46-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="0cd46-129">雖然此課程主要著重于 Windows Mixed Reality 沉浸式（VR）耳機，但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0cd46-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="0cd46-130">隨著課程的遵循，您會看到您可能需要用來支援 HoloLens 的任何變更的附注。</span><span class="sxs-lookup"><span data-stu-id="0cd46-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="0cd46-131">使用 HoloLens 時，您可能會在語音捕獲期間發現一些回應。</span><span class="sxs-lookup"><span data-stu-id="0cd46-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0cd46-132">必要條件</span><span class="sxs-lookup"><span data-stu-id="0cd46-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0cd46-133">本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="0cd46-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0cd46-134">也請注意，本檔中的必要條件和書面指示，代表在撰寫本文時已測試和驗證的內容（5月2018）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="0cd46-135">您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體，但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容，而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="0cd46-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="0cd46-136">在此課程中，我們建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="0cd46-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0cd46-137">[與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦，可用於沉浸式（VR）耳機開發</span><span class="sxs-lookup"><span data-stu-id="0cd46-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="0cd46-138">已啟用開發人員模式的 Windows 10 秋季建立者更新（或更新版本）</span><span class="sxs-lookup"><span data-stu-id="0cd46-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0cd46-139">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="0cd46-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0cd46-140">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="0cd46-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0cd46-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0cd46-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="0cd46-142">已啟用開發人員模式的[Windows Mixed Reality 沉浸（VR）耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="0cd46-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="0cd46-143">一組具有內建麥克風的耳機（如果耳機沒有內建的 mic 和喇叭）</span><span class="sxs-lookup"><span data-stu-id="0cd46-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="0cd46-144">Azure 設定和翻譯抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="0cd46-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="0cd46-145">開始之前</span><span class="sxs-lookup"><span data-stu-id="0cd46-145">Before you start</span></span>

- <span data-ttu-id="0cd46-146">為避免在建立此專案時發生問題，強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案（長資料夾路徑可能會在組建階段造成問題）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="0cd46-147">本教學課程中的程式碼可讓您從連接到電腦的預設麥克風裝置錄製。</span><span class="sxs-lookup"><span data-stu-id="0cd46-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="0cd46-148">請確定預設的麥克風裝置已設定為您打算用來捕捉語音的裝置。</span><span class="sxs-lookup"><span data-stu-id="0cd46-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="0cd46-149">若要允許您的電腦啟用聽寫，請移至 [**設定] > [隱私權 > 語音]、** [筆跡] & 輸入，然後選取 [**開啟語音服務] 和 [輸入建議**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0cd46-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="0cd46-150">如果您使用連接到（或內建于）耳機的麥克風和耳機，請確定已在 設定 中開啟 當我戴耳機、切換到耳機 mic 選項， **> Mixed reality > 音訊和語音**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Mixed reality 設定](images/AzureLabs-Lab1-00-5.png)

   ![麥克風設定](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="0cd46-153">請注意，如果您是針對此實驗室的沉浸式耳機進行開發，您可能會遇到音訊輸出裝置問題。</span><span class="sxs-lookup"><span data-stu-id="0cd46-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="0cd46-154">這是因為 Unity 的問題（在較新版本的 Unity （Unity 2018.2）中已修正）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="0cd46-155">此問題會防止 Unity 在執行時間變更預設音訊輸出裝置。</span><span class="sxs-lookup"><span data-stu-id="0cd46-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="0cd46-156">因應措施是，確定您已完成上述步驟，然後關閉並重新開啟編輯器（當此問題呈現其本身時）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="0cd46-157">第1章– Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="0cd46-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="0cd46-158">若要使用 Azure Translator API，您必須設定服務的實例，讓應用程式可以使用。</span><span class="sxs-lookup"><span data-stu-id="0cd46-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="0cd46-159">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="0cd46-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0cd46-160">如果您還沒有 Azure 帳戶，您將需要建立一個。</span><span class="sxs-lookup"><span data-stu-id="0cd46-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0cd46-161">如果您是在課堂或實驗室的情況下進行本教學課程，請洽詢您的講師或其中一個 proctors，以協助設定您的新帳戶。</span><span class="sxs-lookup"><span data-stu-id="0cd46-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="0cd46-162">登入之後，按一下左上角的 [**新增**]，並搜尋「翻譯工具文字 API」。</span><span class="sxs-lookup"><span data-stu-id="0cd46-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="0cd46-163">選取**Enter 鍵**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-163">Select **Enter**.</span></span>

    ![新增資源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="0cd46-165">在較新的入口網站中，**新**的「可能」已取代為「**建立資源**」。</span><span class="sxs-lookup"><span data-stu-id="0cd46-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="0cd46-166">新的頁面會提供*翻譯工具文字 API*服務的描述。</span><span class="sxs-lookup"><span data-stu-id="0cd46-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="0cd46-167">在此頁面的左下方，選取 [**建立**] 按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="0cd46-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![建立翻譯工具文字 API 服務](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="0cd46-169">當您按一下 [**建立**] 之後：</span><span class="sxs-lookup"><span data-stu-id="0cd46-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="0cd46-170">為此服務實例插入您想要的**名稱**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="0cd46-171">選取適當的**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="0cd46-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="0cd46-172">選取適合您的**定價層**，如果這是您第一次建立*翻譯工具文字服務*，則應該可以使用免費層（名為 F0）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="0cd46-173">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="0cd46-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0cd46-174">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="0cd46-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0cd46-175">建議您將與單一專案相關聯的所有 Azure 服務（例如這些實驗室）都保留在通用資源群組底下）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="0cd46-176">如果您想要深入瞭解 Azure 資源群組，請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="0cd46-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="0cd46-177">判斷資源群組的**位置**（如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="0cd46-178">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="0cd46-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="0cd46-179">某些 Azure 資產僅適用于特定區域。</span><span class="sxs-lookup"><span data-stu-id="0cd46-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="0cd46-180">您也必須確認您已瞭解適用于此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="0cd46-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="0cd46-181">選取 **\[建立\]** 。</span><span class="sxs-lookup"><span data-stu-id="0cd46-181">Select **Create**.</span></span>

        ![選取 [建立] 按鈕。](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="0cd46-183">按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="0cd46-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="0cd46-184">建立服務實例之後，入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="0cd46-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Azure 服務建立通知](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="0cd46-186">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="0cd46-186">Click on the notification to explore your new Service instance.</span></span> 

    ![移至 [資源] 快顯視窗。](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="0cd46-188">按一下通知中的 [**移至資源**] 按鈕，探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="0cd46-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="0cd46-189">您將會進入新的翻譯工具文字 API 服務實例。</span><span class="sxs-lookup"><span data-stu-id="0cd46-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![翻譯工具文字 API 服務頁面](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="0cd46-191">在本教學課程中，您的應用程式將需要呼叫您的服務，這會透過使用您服務的訂用帳戶金鑰來完成。</span><span class="sxs-lookup"><span data-stu-id="0cd46-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="0cd46-192">從*翻譯工具文字*服務的 [*快速入門*] 頁面中，流覽至第一個步驟，*抓取您的金鑰*，然後按一下 [**金鑰**] （您也可以按一下位於 [服務] 導覽功能表中的藍色超連結鍵來達成此目的，以按鍵圖示表示）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="0cd46-193">這會顯示您的服務*金鑰*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="0cd46-194">複製其中一個顯示的金鑰，因為您稍後會在專案中用到。</span><span class="sxs-lookup"><span data-stu-id="0cd46-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="0cd46-195">第2章–設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="0cd46-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="0cd46-196">設定和測試混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="0cd46-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="0cd46-197">在此課程中，您將不需要有動作控制器。</span><span class="sxs-lookup"><span data-stu-id="0cd46-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="0cd46-198">如果您需要支援設定沉浸式耳機，請[遵循下列步驟](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="0cd46-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="0cd46-199">以下是使用混合現實進行開發的一般設定，因此，這是適用于其他專案的絕佳範本：</span><span class="sxs-lookup"><span data-stu-id="0cd46-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="0cd46-200">開啟*Unity* ，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-200">Open *Unity* and click **New**.</span></span> 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="0cd46-202">現在您將需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="0cd46-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="0cd46-203">插入**MR_Translation**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="0cd46-204">請確定 [專案類型] 設定為 [ **3d**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="0cd46-205">將位置設定為適合您的*位置*（請記住，接近根目錄較佳）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0cd46-206">然後，按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-206">Then, click **Create project**.</span></span>

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="0cd46-208">在 Unity 開啟的情況下，值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0cd46-209">移至 **編輯 > 喜好**設定，然後在新視窗中，流覽至 **外部工具**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0cd46-210">將**外部腳本編輯器**變更為**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="0cd46-211">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="0cd46-211">Close the **Preferences** window.</span></span>

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="0cd46-213">接著，移至 [檔案] **> [組建設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至**通用 Windows 平臺**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![[組建設定] 視窗，將平臺切換至 UWP。](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="0cd46-215">移至 [檔案] **> [組建設定**]，並確認：</span><span class="sxs-lookup"><span data-stu-id="0cd46-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="0cd46-216">[**目標裝置**] 已設定為 [**任何裝置**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="0cd46-217">若為 Microsoft HoloLens，請將**目標裝置**設定為*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="0cd46-218">**組建類型**設定為**D3D**</span><span class="sxs-lookup"><span data-stu-id="0cd46-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="0cd46-219">**SDK**已設定為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="0cd46-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="0cd46-220">**Visual Studio 版本**設定為 [**最新安裝**]</span><span class="sxs-lookup"><span data-stu-id="0cd46-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="0cd46-221">**組建和執行**設定為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="0cd46-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="0cd46-222">儲存場景，並將它加入至組建。</span><span class="sxs-lookup"><span data-stu-id="0cd46-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="0cd46-223">選取 [新增] [**開啟場景**] 來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="0cd46-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="0cd46-224">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0cd46-224">A save window will appear.</span></span>

            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="0cd46-226">為此建立新的資料夾，並在任何未來的場景中選取 [**新增資料夾**] 按鈕，以建立新的資料夾，將其命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的腳本資料夾](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="0cd46-228">開啟新建立的 [**幕後**] 資料夾，然後在 [*檔案名*：文字] 欄位中輸入**MR_TranslationScene**，然後按 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![為新場景指定名稱。](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="0cd46-230">請注意，您必須將 Unity 場景儲存在 [*資產*] 資料夾中，因為它們必須與 Unity 專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="0cd46-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="0cd46-231">建立幕後資料夾（和其他類似的資料夾）是結構化 Unity 專案的典型方式。</span><span class="sxs-lookup"><span data-stu-id="0cd46-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="0cd46-232">[*組建設定*] 中的其餘設定，現在應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="0cd46-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="0cd46-233">在 [*組建設定*] 視窗中，按一下 [ **Player 設定**] 按鈕，這會在偵測*器*所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="0cd46-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟 [播放] [設定]。](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="0cd46-235">在此面板中，需要驗證幾項設定：</span><span class="sxs-lookup"><span data-stu-id="0cd46-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="0cd46-236">在 [**其他設定**] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="0cd46-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="0cd46-237">**腳本執行階段版本**應為**穩定**（.net 3.5 對等）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="0cd46-238">**腳本後端**應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="0cd46-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="0cd46-239">**API 相容性層級**應該是 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="0cd46-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="0cd46-241">在 [**發行設定**] 索引標籤的 [**功能**] 底下，檢查：</span><span class="sxs-lookup"><span data-stu-id="0cd46-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="0cd46-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="0cd46-242">**InternetClient**</span></span>
        2. <span data-ttu-id="0cd46-243">**十分**</span><span class="sxs-lookup"><span data-stu-id="0cd46-243">**Microphone**</span></span>

            ![正在更新發行設定。](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="0cd46-245">在面板中，于 [ **XR 設定**] （在 [**發佈設定**] 下方找到）中，支援 [勾選**虛擬實境**]，並確定已新增 [ **Windows Mixed Reality SDK** ]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 設定。](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="0cd46-247">回到 [**組建設定**] *， C# Unity 專案*不再呈現灰色;勾選 [] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0cd46-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="0cd46-248">關閉 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="0cd46-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="0cd46-249">儲存場景和專案（**file > 儲存場景/檔案 > 儲存專案**）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="0cd46-250">第3章–主要攝影機設定</span><span class="sxs-lookup"><span data-stu-id="0cd46-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0cd46-251">如果您想要略過此課程的*Unity 設定*元件，並繼續直接進入程式碼，您可以[下載這個 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)，將它匯入到您的專案中做為[*自訂套件*](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行[第5章](#chapter-5--create-the-results-class)。</span><span class="sxs-lookup"><span data-stu-id="0cd46-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="0cd46-252">您仍然需要建立 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="0cd46-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="0cd46-253">在 [階層]*面板*中，您會找到稱為「**主要攝影機**」的物件，此物件代表您在應用程式內「內部」時的「前端」觀點。</span><span class="sxs-lookup"><span data-stu-id="0cd46-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="0cd46-254">在您前方的 Unity 儀表板中，選取**主要相機 GameObject**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="0cd46-255">您會注意到，[*檢查面板*] （通常是在儀表板中找到）會顯示該*GameObject*的各種元件，並在頂端使用 [*轉換*]，然後按 [*相機*] 和一些其他元件。</span><span class="sxs-lookup"><span data-stu-id="0cd46-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="0cd46-256">您將需要重設主要攝影機的轉換，使其正確定位。</span><span class="sxs-lookup"><span data-stu-id="0cd46-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="0cd46-257">若要這樣做，請選取相機*轉換*元件旁的**齒輪**圖示，然後選取 [**重設**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![重設主要相機轉換。](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="0cd46-259">接著，*轉換*元件看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="0cd46-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="0cd46-260">*位置*設定為**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="0cd46-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="0cd46-261">*旋轉*設定為**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="0cd46-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="0cd46-262">和*Scale*設定為**1，1，1**</span><span class="sxs-lookup"><span data-stu-id="0cd46-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![相機的轉換資訊](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="0cd46-264">接下來，選取**主要相機**物件，請參閱位於 [偵測*器] 面板*最下方的 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0cd46-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="0cd46-265">選取該按鈕，並搜尋（在搜尋欄位中輸入*音訊來源*或流覽區段），以取得名為 [**音訊來源**] 的元件（如下所示），然後選取它（在其上按 enter 鍵也適用）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="0cd46-266">*音訊來源*元件將會新增至**主要攝影機**，如下所示。</span><span class="sxs-lookup"><span data-stu-id="0cd46-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![新增音訊來源元件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="0cd46-268">針對 Microsoft HoloLens，您也必須變更下列各項，這是您**主要攝影機**上**相機**元件的一部分：</span><span class="sxs-lookup"><span data-stu-id="0cd46-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="0cd46-269">**清除旗標：** 單色。</span><span class="sxs-lookup"><span data-stu-id="0cd46-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="0cd46-270">**背景**' 黑色，Alpha 0 ' –十六進位色彩： #00000000。</span><span class="sxs-lookup"><span data-stu-id="0cd46-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="0cd46-271">第4章–設定偵錯工具畫布</span><span class="sxs-lookup"><span data-stu-id="0cd46-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="0cd46-272">若要顯示翻譯的輸入和輸出，必須建立基本 UI。</span><span class="sxs-lookup"><span data-stu-id="0cd46-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="0cd46-273">在此課程中，您將建立畫布 UI 物件，其中包含數個「文字」物件來顯示資料。</span><span class="sxs-lookup"><span data-stu-id="0cd46-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="0cd46-274">以滑鼠右鍵按一下 [階層]*面板*的空白區域，然後在 [ **UI**] 下加入**畫布**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![加入新的畫布 UI 物件。](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="0cd46-276">選取畫布物件後，在 [偵測*器] 面板*中（在 [畫布] 元件中），將 [轉譯**模式]** 變更為 [**世界空間**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="0cd46-277">接下來，變更偵測*器面板矩形轉換*中的下列參數：</span><span class="sxs-lookup"><span data-stu-id="0cd46-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="0cd46-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="0cd46-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="0cd46-279">*寬度*-500</span><span class="sxs-lookup"><span data-stu-id="0cd46-279">*Width* -    500</span></span>
    3. <span data-ttu-id="0cd46-280">*高度*-300</span><span class="sxs-lookup"><span data-stu-id="0cd46-280">*Height* -   300</span></span>
    4. <span data-ttu-id="0cd46-281">*縮放* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="0cd46-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![更新畫布的矩形轉換。](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="0cd46-283">以滑鼠右鍵按一下 [階層]*面板*中的**畫布**，在 [ **UI**] 底下，然後加入**面板**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="0cd46-284">此**面板**會提供您將在場景中顯示之文字的背景。</span><span class="sxs-lookup"><span data-stu-id="0cd46-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="0cd46-285">以滑鼠右鍵按一下 [階層]*面板*中的**面板**，在 [ **UI**] 底下，然後新增 [**文字] 物件**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="0cd46-286">重複相同的程式，直到您建立了四個 UI 文字物件總計（提示：如果您選取了第一個 ' Text ' 物件，只要按 **' Ctrl ' + d '** ，即可複製它，直到總共有四個）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="0cd46-287">針對每個**文字物件**，請選取它，並使用下表來設定 [偵測*器] 面板*中的參數。</span><span class="sxs-lookup"><span data-stu-id="0cd46-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="0cd46-288">針對*矩形轉換*元件：</span><span class="sxs-lookup"><span data-stu-id="0cd46-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="0cd46-289">名稱</span><span class="sxs-lookup"><span data-stu-id="0cd46-289">Name</span></span>                   | <span data-ttu-id="0cd46-290">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="0cd46-290">Transform - *Position*</span></span>             | <span data-ttu-id="0cd46-291">寬度</span><span class="sxs-lookup"><span data-stu-id="0cd46-291">Width</span></span>      | <span data-ttu-id="0cd46-292">高寬比</span><span class="sxs-lookup"><span data-stu-id="0cd46-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="0cd46-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="0cd46-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="0cd46-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="0cd46-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="0cd46-295">300</span><span class="sxs-lookup"><span data-stu-id="0cd46-295">300</span></span>        | <span data-ttu-id="0cd46-296">30</span><span class="sxs-lookup"><span data-stu-id="0cd46-296">30</span></span>        |
        | <span data-ttu-id="0cd46-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="0cd46-297">AzureResponseLabel</span></span>     | <span data-ttu-id="0cd46-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="0cd46-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="0cd46-299">300</span><span class="sxs-lookup"><span data-stu-id="0cd46-299">300</span></span>        | <span data-ttu-id="0cd46-300">30</span><span class="sxs-lookup"><span data-stu-id="0cd46-300">30</span></span>        |
        | <span data-ttu-id="0cd46-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="0cd46-301">DictationLabel</span></span>         | <span data-ttu-id="0cd46-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="0cd46-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="0cd46-303">300</span><span class="sxs-lookup"><span data-stu-id="0cd46-303">300</span></span>        | <span data-ttu-id="0cd46-304">30</span><span class="sxs-lookup"><span data-stu-id="0cd46-304">30</span></span>        |
        | <span data-ttu-id="0cd46-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="0cd46-305">TranslationResultLabel</span></span> | <span data-ttu-id="0cd46-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="0cd46-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="0cd46-307">300</span><span class="sxs-lookup"><span data-stu-id="0cd46-307">300</span></span>        | <span data-ttu-id="0cd46-308">30</span><span class="sxs-lookup"><span data-stu-id="0cd46-308">30</span></span>        |


    2. <span data-ttu-id="0cd46-309">針對**文字（腳本）** 元件：</span><span class="sxs-lookup"><span data-stu-id="0cd46-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="0cd46-310">名稱</span><span class="sxs-lookup"><span data-stu-id="0cd46-310">Name</span></span>                   | <span data-ttu-id="0cd46-311">文字</span><span class="sxs-lookup"><span data-stu-id="0cd46-311">Text</span></span>               | <span data-ttu-id="0cd46-312">字型大小</span><span class="sxs-lookup"><span data-stu-id="0cd46-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="0cd46-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="0cd46-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="0cd46-314">麥克風狀態：</span><span class="sxs-lookup"><span data-stu-id="0cd46-314">Microphone Status:</span></span> | <span data-ttu-id="0cd46-315">20</span><span class="sxs-lookup"><span data-stu-id="0cd46-315">20</span></span>           |
        | <span data-ttu-id="0cd46-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="0cd46-316">AzureResponseLabel</span></span>     | <span data-ttu-id="0cd46-317">Azure Web 回應</span><span class="sxs-lookup"><span data-stu-id="0cd46-317">Azure Web Response</span></span> | <span data-ttu-id="0cd46-318">20</span><span class="sxs-lookup"><span data-stu-id="0cd46-318">20</span></span>           |
        | <span data-ttu-id="0cd46-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="0cd46-319">DictationLabel</span></span>         |   <span data-ttu-id="0cd46-320">您剛剛說過：</span><span class="sxs-lookup"><span data-stu-id="0cd46-320">You just said:</span></span>   | <span data-ttu-id="0cd46-321">20</span><span class="sxs-lookup"><span data-stu-id="0cd46-321">20</span></span>           |
        | <span data-ttu-id="0cd46-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="0cd46-322">TranslationResultLabel</span></span> |    <span data-ttu-id="0cd46-323">機器翻譯</span><span class="sxs-lookup"><span data-stu-id="0cd46-323">Translation:</span></span>    | <span data-ttu-id="0cd46-324">20</span><span class="sxs-lookup"><span data-stu-id="0cd46-324">20</span></span>           |

        ![輸入 UI 標籤的對應值。](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="0cd46-326">此外，請將字型樣式設為**粗體**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="0cd46-327">這會讓文字更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="0cd46-327">This will make the text easier to read.</span></span>

        ![粗體字型。](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="0cd46-329">針對[第5章](#chapter-5--create-the-results-class)所建立的每個*UI 文字物件*，建立新的*子* **ui 文字物件**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="0cd46-330">這些子系會顯示應用程式的輸出。</span><span class="sxs-lookup"><span data-stu-id="0cd46-330">These children will display the output of the application.</span></span> <span data-ttu-id="0cd46-331">以滑鼠右鍵按一下您想要的父系來建立*子*物件（例如*MicrophoneStatusLabel*），然後選取 [ **UI** ]，再選取 [**文字**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="0cd46-332">針對上述每個子系，請選取它，並使用下表來設定 [偵測器] 面板中的參數。</span><span class="sxs-lookup"><span data-stu-id="0cd46-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="0cd46-333">針對**矩形轉換**元件：</span><span class="sxs-lookup"><span data-stu-id="0cd46-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="0cd46-334">名稱</span><span class="sxs-lookup"><span data-stu-id="0cd46-334">Name</span></span>                  | <span data-ttu-id="0cd46-335">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="0cd46-335">Transform - *Position*</span></span> | <span data-ttu-id="0cd46-336">寬度</span><span class="sxs-lookup"><span data-stu-id="0cd46-336">Width</span></span>      | <span data-ttu-id="0cd46-337">高寬比</span><span class="sxs-lookup"><span data-stu-id="0cd46-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="0cd46-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="0cd46-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="0cd46-339">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="0cd46-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="0cd46-340">300</span><span class="sxs-lookup"><span data-stu-id="0cd46-340">300</span></span>        | <span data-ttu-id="0cd46-341">30</span><span class="sxs-lookup"><span data-stu-id="0cd46-341">30</span></span>        |
        | <span data-ttu-id="0cd46-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="0cd46-342">AzureResponseText</span></span>     | <span data-ttu-id="0cd46-343">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="0cd46-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="0cd46-344">300</span><span class="sxs-lookup"><span data-stu-id="0cd46-344">300</span></span>        | <span data-ttu-id="0cd46-345">30</span><span class="sxs-lookup"><span data-stu-id="0cd46-345">30</span></span>        |
        | <span data-ttu-id="0cd46-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="0cd46-346">DictationText</span></span>         | <span data-ttu-id="0cd46-347">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="0cd46-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="0cd46-348">300</span><span class="sxs-lookup"><span data-stu-id="0cd46-348">300</span></span>        | <span data-ttu-id="0cd46-349">30</span><span class="sxs-lookup"><span data-stu-id="0cd46-349">30</span></span>        |
        | <span data-ttu-id="0cd46-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="0cd46-350">TranslationResultText</span></span> | <span data-ttu-id="0cd46-351">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="0cd46-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="0cd46-352">300</span><span class="sxs-lookup"><span data-stu-id="0cd46-352">300</span></span>        | <span data-ttu-id="0cd46-353">30</span><span class="sxs-lookup"><span data-stu-id="0cd46-353">30</span></span>        |

    2. <span data-ttu-id="0cd46-354">針對**文字（腳本）** 元件：</span><span class="sxs-lookup"><span data-stu-id="0cd46-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="0cd46-355">名稱</span><span class="sxs-lookup"><span data-stu-id="0cd46-355">Name</span></span>                  | <span data-ttu-id="0cd46-356">文字</span><span class="sxs-lookup"><span data-stu-id="0cd46-356">Text</span></span>          | <span data-ttu-id="0cd46-357">字型大小</span><span class="sxs-lookup"><span data-stu-id="0cd46-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="0cd46-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="0cd46-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="0cd46-359">??</span><span class="sxs-lookup"><span data-stu-id="0cd46-359">??</span></span>       | <span data-ttu-id="0cd46-360">20</span><span class="sxs-lookup"><span data-stu-id="0cd46-360">20</span></span>           |
        | <span data-ttu-id="0cd46-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="0cd46-361">AzureResponseText</span></span>     |      <span data-ttu-id="0cd46-362">??</span><span class="sxs-lookup"><span data-stu-id="0cd46-362">??</span></span>       | <span data-ttu-id="0cd46-363">20</span><span class="sxs-lookup"><span data-stu-id="0cd46-363">20</span></span>           |
        | <span data-ttu-id="0cd46-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="0cd46-364">DictationText</span></span>         |      <span data-ttu-id="0cd46-365">??</span><span class="sxs-lookup"><span data-stu-id="0cd46-365">??</span></span>       | <span data-ttu-id="0cd46-366">20</span><span class="sxs-lookup"><span data-stu-id="0cd46-366">20</span></span>           |
        | <span data-ttu-id="0cd46-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="0cd46-367">TranslationResultText</span></span> |      <span data-ttu-id="0cd46-368">??</span><span class="sxs-lookup"><span data-stu-id="0cd46-368">??</span></span>       | <span data-ttu-id="0cd46-369">20</span><span class="sxs-lookup"><span data-stu-id="0cd46-369">20</span></span>           |

9. <span data-ttu-id="0cd46-370">接下來，為每個文字元件選取 [中心] 對齊選項：</span><span class="sxs-lookup"><span data-stu-id="0cd46-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![對齊文字。](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="0cd46-372">若要確保**子 UI 文字**物件可輕鬆讀取，請變更其*色彩*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="0cd46-373">若要這麼做，請按一下 [*色彩*] 旁邊的橫條（目前為「黑色」）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![輸入 UI 文字輸出的對應值。](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="0cd46-375">然後，在 [新增]、[小]、[*色彩*] 視窗中，將*十六進位色彩*變更為： **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="0cd46-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![將色彩更新為藍色。](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="0cd46-377">以下是**UI**的外觀。</span><span class="sxs-lookup"><span data-stu-id="0cd46-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="0cd46-378">在 [階層]*面板*中：</span><span class="sxs-lookup"><span data-stu-id="0cd46-378">In the *Hierarchy Panel*:</span></span>

        ![在提供的結構中具有階層。](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="0cd46-380">在*場景*和*遊戲視圖*中：</span><span class="sxs-lookup"><span data-stu-id="0cd46-380">In the *Scene* and *Game Views*:</span></span>

        ![將場景和遊戲視圖放在相同的結構中。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="0cd46-382">第5章–建立結果類別</span><span class="sxs-lookup"><span data-stu-id="0cd46-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="0cd46-383">您需要建立的第一個腳本是*結果*類別，其負責提供查看轉譯結果的方式。</span><span class="sxs-lookup"><span data-stu-id="0cd46-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="0cd46-384">類別會儲存並顯示下列內容：</span><span class="sxs-lookup"><span data-stu-id="0cd46-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="0cd46-385">來自 Azure 的回應結果。</span><span class="sxs-lookup"><span data-stu-id="0cd46-385">The response result from Azure.</span></span>
- <span data-ttu-id="0cd46-386">麥克風狀態。</span><span class="sxs-lookup"><span data-stu-id="0cd46-386">The microphone status.</span></span> 
- <span data-ttu-id="0cd46-387">聽寫的結果（語音到文字）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="0cd46-388">轉譯的結果。</span><span class="sxs-lookup"><span data-stu-id="0cd46-388">The result of the translation.</span></span>

<span data-ttu-id="0cd46-389">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="0cd46-389">To create this class:</span></span> 

1.  <span data-ttu-id="0cd46-390">在 *專案 面板*中按一下滑鼠右鍵，然後**建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="0cd46-391">將資料夾命名為**Scripts**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-391">Name the folder **Scripts**.</span></span> 
 
    ![建立腳本資料夾。](images/AzureLabs-Lab1-31.png)

    ![開啟 [腳本] 資料夾。](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="0cd46-394">在 [**腳本**] 資料夾建立後，按兩下以開啟。</span><span class="sxs-lookup"><span data-stu-id="0cd46-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="0cd46-395">然後在該資料夾中，以滑鼠右鍵按一下，然後選取 [**建立] >** [  **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="0cd46-396">將腳本命名為*結果*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-396">Name the script *Results*.</span></span> 

    ![建立第一個腳本。](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="0cd46-398">按兩下新的*結果*腳本，以**Visual Studio**開啟它。</span><span class="sxs-lookup"><span data-stu-id="0cd46-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="0cd46-399">插入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="0cd46-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="0cd46-400">在類別內插入下列變數：</span><span class="sxs-lookup"><span data-stu-id="0cd46-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="0cd46-401">然後，新增*喚醒（）* 方法，這會在類別初始化時被呼叫。</span><span class="sxs-lookup"><span data-stu-id="0cd46-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="0cd46-402">最後，新增負責將各種結果資訊輸出到 UI 的方法。</span><span class="sxs-lookup"><span data-stu-id="0cd46-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="0cd46-403">請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="0cd46-404">第6章–建立*MicrophoneManager*類別</span><span class="sxs-lookup"><span data-stu-id="0cd46-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="0cd46-405">您即將建立的第二個類別是*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="0cd46-406">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="0cd46-406">This class is responsible for:</span></span>

- <span data-ttu-id="0cd46-407">偵測連接到耳機或電腦的錄製裝置（以何者為預設值）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="0cd46-408">捕捉音訊（語音）並使用聽寫將其儲存為字串。</span><span class="sxs-lookup"><span data-stu-id="0cd46-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="0cd46-409">聲音暫停之後，請將聽寫提交至 Translator 類別。</span><span class="sxs-lookup"><span data-stu-id="0cd46-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="0cd46-410">裝載可以在需要時停止語音捕捉的方法。</span><span class="sxs-lookup"><span data-stu-id="0cd46-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="0cd46-411">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="0cd46-411">To create this class:</span></span> 
1.  <span data-ttu-id="0cd46-412">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="0cd46-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="0cd46-413">在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立 > C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="0cd46-414">將腳本命名為*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="0cd46-415">按兩下新的腳本，以 Visual Studio 開啟它。</span><span class="sxs-lookup"><span data-stu-id="0cd46-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="0cd46-416">在*MicrophoneManager*類別的頂端，更新命名空間，以與下列內容相同：</span><span class="sxs-lookup"><span data-stu-id="0cd46-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="0cd46-417">然後，在*MicrophoneManager*類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="0cd46-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="0cd46-418">現在必須加入*喚醒（）* 和*Start （）* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0cd46-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="0cd46-419">當類別初始化時，將會呼叫這些：</span><span class="sxs-lookup"><span data-stu-id="0cd46-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="0cd46-420">您可以*刪除* *Update （）* 方法，因為這個類別不會使用它。</span><span class="sxs-lookup"><span data-stu-id="0cd46-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="0cd46-421">現在您需要應用程式用來啟動和停止語音捕獲的方法，並將它傳遞給*Translator*類別，您很快就會建立。</span><span class="sxs-lookup"><span data-stu-id="0cd46-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="0cd46-422">複製下列程式碼，並將它貼入*Start （）* 方法底下。</span><span class="sxs-lookup"><span data-stu-id="0cd46-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="0cd46-423">雖然此應用程式不會使用它，但在這裡也會提供*StopCapturingAudio （）* 方法，您應該要在應用程式中執行停止捕獲音訊的功能。</span><span class="sxs-lookup"><span data-stu-id="0cd46-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="0cd46-424">您現在需要新增聽寫處理常式，當聲音停止時，就會叫用它。</span><span class="sxs-lookup"><span data-stu-id="0cd46-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="0cd46-425">然後，這個方法會將聽寫的文字傳遞給*Translator*類別。</span><span class="sxs-lookup"><span data-stu-id="0cd46-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="0cd46-426">請務必先將您的變更儲存在 Visual Studio 中，然後再返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="0cd46-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="0cd46-427">此時，您會注意到 [ *Unity 編輯器] 主控台*面板中出現錯誤（「名稱 ' Translator ' 不存在 ...」）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="0cd46-428">這是因為程式碼會參考*Translator*類別，您將在下一章中建立。</span><span class="sxs-lookup"><span data-stu-id="0cd46-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="0cd46-429">第7章–呼叫 Azure 和 translator 服務</span><span class="sxs-lookup"><span data-stu-id="0cd46-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="0cd46-430">您需要建立的最後一個腳本是*Translator*類別。</span><span class="sxs-lookup"><span data-stu-id="0cd46-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="0cd46-431">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="0cd46-431">This class is responsible for:</span></span>

-   <span data-ttu-id="0cd46-432">在 exchange 中使用*Azure*驗證應用程式，以取得**驗證權杖**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="0cd46-433">使用**驗證權杖**來提交要轉譯的文字（從*MicrophoneManager*類別收到）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="0cd46-434">接收轉譯的結果，並將它傳遞給要在 UI 中視覺化的*結果*類別。</span><span class="sxs-lookup"><span data-stu-id="0cd46-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="0cd46-435">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="0cd46-435">To create this Class:</span></span> 
1.  <span data-ttu-id="0cd46-436">移至您先前建立的**腳本**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cd46-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="0cd46-437">以滑鼠右鍵按一下 [**專案] 面板**中的 [**建立 > C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="0cd46-438">呼叫腳本*Translator*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="0cd46-439">按兩下新的*翻譯工具*腳本，以**Visual Studio**開啟它。</span><span class="sxs-lookup"><span data-stu-id="0cd46-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="0cd46-440">將下列命名空間新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="0cd46-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="0cd46-441">然後在*Translator*類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="0cd46-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="0cd46-442">插入至 [語言]**列舉**的語言只是範例。</span><span class="sxs-lookup"><span data-stu-id="0cd46-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="0cd46-443">如有需要，您可以隨意加入更多;[API 支援超過60的語言](https://docs.microsoft.com/azure/cognitive-services/translator/languages)（包括克林貢）！</span><span class="sxs-lookup"><span data-stu-id="0cd46-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="0cd46-444">有[更多互動式頁面涵蓋可用的語言](https://www.microsoft.com/translator/business/languages/)，不過請注意，只有當網站語言設定為 ' ' （而 Microsoft 網站可能會重新導向至您的原生語言）時，頁面才會運作。</span><span class="sxs-lookup"><span data-stu-id="0cd46-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to '' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="0cd46-445">您可以變更頁面底部的網站語言，或變更 URL。</span><span class="sxs-lookup"><span data-stu-id="0cd46-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="0cd46-446">上述程式碼片段中的**authorizationKey**值必須是您訂閱*Azure 翻譯工具文字 API*時所收到的**金鑰**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="0cd46-447">[第1章](#chapter-1--the-azure-portal)已涵蓋這項功能。</span><span class="sxs-lookup"><span data-stu-id="0cd46-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="0cd46-448">現在必須加入*喚醒（）* 和*Start （）* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0cd46-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="0cd46-449">在此情況下，程式碼會使用授權金鑰來呼叫*Azure* ，以取得*權杖*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="0cd46-450">權杖將在10分鐘後到期。</span><span class="sxs-lookup"><span data-stu-id="0cd46-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="0cd46-451">視您應用程式的案例而定，您可能必須多次進行相同的協同程式呼叫。</span><span class="sxs-lookup"><span data-stu-id="0cd46-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="0cd46-452">取得權杖的協同程式如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cd46-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="0cd46-453">如果您編輯 IEnumerator 方法**GetTokenCoroutine （）** 的名稱，則必須更新上述程式碼中的*StartCoroutine*和*StopCoroutine*呼叫字串值。</span><span class="sxs-lookup"><span data-stu-id="0cd46-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="0cd46-454">[根據 Unity 檔](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)，若要停止特定的*協同程式*，您必須使用字串值方法。</span><span class="sxs-lookup"><span data-stu-id="0cd46-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="0cd46-455">接下來，新增協同程式（其底下有「支援」資料流程方法），以取得*MicrophoneManager*類別所收到文字的轉譯。</span><span class="sxs-lookup"><span data-stu-id="0cd46-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="0cd46-456">此程式碼會建立要傳送至*Azure 翻譯工具文字 API*的查詢字串，然後使用內部 Unity UnityWebRequest 類別，對具有查詢字串的端點進行「Get」呼叫。</span><span class="sxs-lookup"><span data-stu-id="0cd46-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="0cd46-457">然後，結果會用來設定結果物件中的轉譯。</span><span class="sxs-lookup"><span data-stu-id="0cd46-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="0cd46-458">下列程式碼顯示執行的方式：</span><span class="sxs-lookup"><span data-stu-id="0cd46-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="0cd46-459">請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="0cd46-460">第8章–設定 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="0cd46-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="0cd46-461">回到 Unity 編輯器中，按一下 [**腳本**] 資料夾中的 [*結果* *] 類別，* 並將其拖曳至 [階層]*面板*中的**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="0cd46-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="0cd46-462">按一下**主攝影機**並查看 [*檢查] 面板*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="0cd46-463">您會發現，在新加入的*腳本*元件中，有四個欄位具有空白值。</span><span class="sxs-lookup"><span data-stu-id="0cd46-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="0cd46-464">這些是程式碼中屬性的輸出參考。</span><span class="sxs-lookup"><span data-stu-id="0cd46-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="0cd46-465">將適當的**文字**物件從 [階層]*面板*拖曳到這四個位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="0cd46-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![以指定的值更新目標參考。](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="0cd46-467">接著，按一下 [**腳本**] 資料夾中的*Translator*類別，並將其拖曳至 [階層]*面板*中的**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="0cd46-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="0cd46-468">然後，按一下 [**腳本**] 資料夾中的 [ *MicrophoneManager* ] 類別，並將其拖曳至 [階層]*面板*中的**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="0cd46-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="0cd46-469">最後，按一下**主攝影機**並查看 [*檢查器] 面板*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="0cd46-470">您會注意到在您拖曳的腳本中有兩個下拉式方塊，可讓您設定語言。</span><span class="sxs-lookup"><span data-stu-id="0cd46-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![請確定預定的翻譯語言為輸入。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="0cd46-472">第9章–混合現實中的測試</span><span class="sxs-lookup"><span data-stu-id="0cd46-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="0cd46-473">此時，您必須測試場景是否已正確執行。</span><span class="sxs-lookup"><span data-stu-id="0cd46-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="0cd46-474">請確定：</span><span class="sxs-lookup"><span data-stu-id="0cd46-474">Ensure that:</span></span>

- <span data-ttu-id="0cd46-475">[第1章](#chapter-1--the-azure-portal)所提及的所有設定都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="0cd46-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="0cd46-476">*結果*、 *Translator*和*MicrophoneManager*，腳本會附加至**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="0cd46-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="0cd46-477">您已將*Azure 翻譯工具文字 API*服務**金鑰**放在*Translator*腳本內的**authorizationKey**變數中。</span><span class="sxs-lookup"><span data-stu-id="0cd46-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="0cd46-478">*主要相機偵測器面板*中的所有欄位都已正確指派。</span><span class="sxs-lookup"><span data-stu-id="0cd46-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="0cd46-479">當您執行場景時，您的麥克風會運作（如果不是，請檢查您連接的麥克風是否為*預設*裝置，而且您已在[Windows 中正確設定](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="0cd46-480">您可以按下*Unity 編輯器*中的 [**播放**] 按鈕，測試沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="0cd46-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="0cd46-481">應用程式應透過附加的沉浸式耳機運作。</span><span class="sxs-lookup"><span data-stu-id="0cd46-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="0cd46-482">如果您在 Unity 主控台看到關於預設音訊裝置變更的錯誤，場景可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="0cd46-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="0cd46-483">這是因為混合現實入口網站處理具有耳機之內建麥克風的方式。</span><span class="sxs-lookup"><span data-stu-id="0cd46-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="0cd46-484">如果您看到此錯誤，只要停止場景並重新啟動，就應該會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="0cd46-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="0cd46-485">第10章–在本機電腦上建立 UWP 解決方案和側載</span><span class="sxs-lookup"><span data-stu-id="0cd46-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="0cd46-486">此專案的 Unity 區段所需的全部內容現在已經完成，所以可以從 Unity 建立它。</span><span class="sxs-lookup"><span data-stu-id="0cd46-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="0cd46-487">流覽至**組建設定**：檔案 **> 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="0cd46-488">從 [**組建設定**] 視窗中，按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-488">From the **Build Settings** window, click **Build**.</span></span>

    ![建立 Unity 場景。](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="0cd46-490">如果尚未這麼做，請先勾選**Unity C#專案**。</span><span class="sxs-lookup"><span data-stu-id="0cd46-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="0cd46-491">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-491">Click **Build**.</span></span> <span data-ttu-id="0cd46-492">Unity 將會啟動 [檔案*瀏覽器*] 視窗，您必須在其中建立並選取要建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cd46-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="0cd46-493">立即建立該資料夾，並將它命名為*應用程式*。</span><span class="sxs-lookup"><span data-stu-id="0cd46-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="0cd46-494">然後選取 [*應用程式*] 資料夾，按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="0cd46-495">Unity 會開始將您的專案建立至*應用程式*資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cd46-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="0cd46-496">Unity 完成建立之後（可能需要一些時間），它會在組建的位置開啟 [檔案*瀏覽器*] 視窗（請檢查您的工作列，因為它不一定會出現在視窗的上方，但會通知您加入新的視窗）。</span><span class="sxs-lookup"><span data-stu-id="0cd46-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="0cd46-497">第11章–部署您的應用程式</span><span class="sxs-lookup"><span data-stu-id="0cd46-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="0cd46-498">若要部署您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="0cd46-498">To deploy your application:</span></span>

1.  <span data-ttu-id="0cd46-499">流覽至新的 Unity 組建（*應用程式*資料夾），然後使用*Visual Studio*開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="0cd46-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="0cd46-500">在 [解決方案設定] 中，選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="0cd46-501">在解決方案平臺中，選取 [ **x86**]、[**本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="0cd46-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="0cd46-502">針對 Microsoft HoloLens，您可能會發現將此設定為 [*遠端電腦*] 比較容易，因此您不會行動網卡到電腦。</span><span class="sxs-lookup"><span data-stu-id="0cd46-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="0cd46-503">不過，您也必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0cd46-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="0cd46-504">知道您的 HoloLens 的**IP 位址**，您可以在 *> Network & Internet > Wi-fi > Advanced 選項*的 [設定] 中找到它;IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="0cd46-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="0cd46-505">請確定*開發人員模式*已**開啟**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >* 。</span><span class="sxs-lookup"><span data-stu-id="0cd46-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![從 Visual Studio 部署解決方案。](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="0cd46-507">移至 [**建立] 功能表**，然後按一下 [**部署方案**]，將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="0cd46-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="0cd46-508">您的應用程式現在應該會出現在已安裝的應用程式清單中，並準備好啟動。</span><span class="sxs-lookup"><span data-stu-id="0cd46-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="0cd46-509">啟動之後，應用程式會提示您授權存取麥克風。</span><span class="sxs-lookup"><span data-stu-id="0cd46-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="0cd46-510">請務必按一下 [**是]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0cd46-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="0cd46-511">您現在已經準備好開始翻譯了！</span><span class="sxs-lookup"><span data-stu-id="0cd46-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="0cd46-512">您完成的翻譯文字 API 應用程式</span><span class="sxs-lookup"><span data-stu-id="0cd46-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="0cd46-513">恭喜，您建立了一個混合現實應用程式，利用 Azure 翻譯文字 API 將語音轉換成翻譯的文字。</span><span class="sxs-lookup"><span data-stu-id="0cd46-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![最終產品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="0cd46-515">額外練習</span><span class="sxs-lookup"><span data-stu-id="0cd46-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="0cd46-516">練習1</span><span class="sxs-lookup"><span data-stu-id="0cd46-516">Exercise 1</span></span>

<span data-ttu-id="0cd46-517">您是否可以將文字轉換語音功能新增至應用程式，以說出傳回的文字？</span><span class="sxs-lookup"><span data-stu-id="0cd46-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="0cd46-518">練習2</span><span class="sxs-lookup"><span data-stu-id="0cd46-518">Exercise 2</span></span>

<span data-ttu-id="0cd46-519">讓使用者可以在應用程式本身內變更來源和輸出語言（「從」和「到」），因此每次您想要變更語言時，都不需要重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cd46-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
