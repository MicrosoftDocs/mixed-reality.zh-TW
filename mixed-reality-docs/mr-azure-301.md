---
title: MR 和 Azure 301-語言翻譯
description: 完成這個課程來了解如何實作 Azure Translator Text API，在混合的實境應用程式中。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 翻譯文字、 hololens、 沉浸式 vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596314"
---
>[!NOTE]
><span data-ttu-id="b2fbf-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b2fbf-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b2fbf-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b2fbf-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b2fbf-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b2fbf-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="b2fbf-110">MR 和 Azure 301:語言翻譯</span><span class="sxs-lookup"><span data-stu-id="b2fbf-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="b2fbf-111">在此課程中，您將學習如何將翻譯功能新增至 Translator Text API 搭配使用 Azure 認知服務的混合的實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![最終產品](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="b2fbf-113">Translator Text API 是近乎即時地適用於服務的翻譯。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="b2fbf-114">服務是以雲端為基礎，並使用 REST API 呼叫，讓應用程式可以使用的類神經機器翻譯技術翻譯成其他語言的文字。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="b2fbf-115">如需詳細資訊，請瀏覽[Azure Translator Text API 頁面](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="b2fbf-116">完成本課程的詳細資訊，您必須能夠執行下列作業的混合的實境應用程式：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="b2fbf-117">使用者會說話連接沈浸式的 (VR) 耳機式麥克風 （或內建的麥克風的 HoloLens）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="b2fbf-118">應用程式會擷取語音輸入，並將它傳送至 Azure 的 Translator Text API。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="b2fbf-119">轉譯結果會顯示 Unity 場景中的簡單 UI 群組中。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="b2fbf-120">本課程將教導您如何從轉譯程式服務取得結果到 Unity 為基礎的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="b2fbf-121">它會決定要將這些概念套用到您可能建置自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="b2fbf-122">裝置支援</span><span class="sxs-lookup"><span data-stu-id="b2fbf-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b2fbf-123">課程</span><span class="sxs-lookup"><span data-stu-id="b2fbf-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b2fbf-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b2fbf-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b2fbf-125"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="b2fbf-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b2fbf-126">MR 和 Azure 301:語言翻譯</span><span class="sxs-lookup"><span data-stu-id="b2fbf-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="b2fbf-127">✔️</span><span class="sxs-lookup"><span data-stu-id="b2fbf-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b2fbf-128">✔️</span><span class="sxs-lookup"><span data-stu-id="b2fbf-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b2fbf-129">雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="b2fbf-130">當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="b2fbf-131">當使用 HoloLens，您可能會發現某些回應語音擷取期間。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2fbf-132">先決條件</span><span class="sxs-lookup"><span data-stu-id="b2fbf-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b2fbf-133">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b2fbf-134">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="b2fbf-135">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊會完全符合您會發現在較新的軟體與以下所列內容.</span><span class="sxs-lookup"><span data-stu-id="b2fbf-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="b2fbf-136">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b2fbf-137">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="b2fbf-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b2fbf-138">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="b2fbf-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b2fbf-139">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="b2fbf-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b2fbf-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="b2fbf-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b2fbf-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b2fbf-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="b2fbf-142">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="b2fbf-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b2fbf-143">一組的耳機與內建的麥克風 （如果耳機沒有內建的麥克風和喇叭）</span><span class="sxs-lookup"><span data-stu-id="b2fbf-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="b2fbf-144">Azure 的安裝程式] 及 [翻譯擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="b2fbf-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b2fbf-145">開始之前</span><span class="sxs-lookup"><span data-stu-id="b2fbf-145">Before you start</span></span>

- <span data-ttu-id="b2fbf-146">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="b2fbf-147">本教學課程中的程式碼可讓您從預設麥克風的裝置連線到您的電腦記錄。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="b2fbf-148">請確定預設麥克風的裝置設定為您打算用來擷取您的語音裝置。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="b2fbf-149">若要允許您的電腦啟用語音輸入，請移至**設定 > 隱私權 > 語音、 筆跡 & 鍵入**，然後選取按鈕**語音服務開啟與輸入的建議**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="b2fbf-150">如果您使用麥克風並連接到的耳機 （或內建） 耳機，請確定選擇 「 我穿上我耳機，切換到耳機式麥克風 」 開啟**設定 > 混合實境 > 音訊及語音**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![混合的實境設定](images/AzureLabs-Lab1-00-5.png)

   ![設定麥克風](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="b2fbf-153">請注意，如果您正在開發的沈浸式耳機本實驗室中，您可能會遇到的音訊輸出裝置問題。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="b2fbf-154">這是 unity 的因為 unity (Unity 2018.2) 更新版本中已修正的問題。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="b2fbf-155">此問題會防止 Unity 在執行階段變更預設音訊輸出裝置。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="b2fbf-156">因應之道，請確定您已完成上述步驟，並關閉並重新開啟編輯器 中，當此問題會。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="b2fbf-157">第 1 章-Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="b2fbf-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="b2fbf-158">若要使用 Azure 轉譯程式 API，您必須設定您的應用程式提供服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="b2fbf-159">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b2fbf-160">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b2fbf-161">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="b2fbf-162">一旦您登入，按一下**新增**右上角左角並搜尋"Translator Text API。 」</span><span class="sxs-lookup"><span data-stu-id="b2fbf-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="b2fbf-163">選取 **輸入**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-163">Select **Enter**.</span></span>

    ![新的資源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="b2fbf-165">單字**的新**可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="b2fbf-166">新的頁面將提供的描述*Translator Text API*服務。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="b2fbf-167">在左下方的這個頁面上，選取**建立**按鈕，以建立與這個關聯服務。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![建立 Translator Text API 服務](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="b2fbf-169">一旦您按下**建立**:</span><span class="sxs-lookup"><span data-stu-id="b2fbf-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="b2fbf-170">插入您想要**名稱**此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="b2fbf-171">選取適當**訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="b2fbf-172">選取 **定價層**適合您，如果這是第一個時間來建立*轉譯程式文字服務*，免費層 （名為 F0） 應該是您可以使用。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="b2fbf-173">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="b2fbf-174">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b2fbf-175">建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些實驗室中） 的單一專案保留）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="b2fbf-176">如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="b2fbf-177">判斷**位置**資源群組 （如果您要建立新的資源群組）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="b2fbf-178">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="b2fbf-179">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="b2fbf-180">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="b2fbf-181">選取 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-181">Select **Create**.</span></span>

        ![選取 [建立] 按鈕。](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="b2fbf-183">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="b2fbf-184">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Azure 服務建立通知](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="b2fbf-186">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-186">Click on the notification to explore your new Service instance.</span></span> 

    ![請移至資源的快顯視窗。](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="b2fbf-188">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="b2fbf-189">您會前往新的 Translator Text API 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Translator Text API 服務頁面](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="b2fbf-191">在本教學課程中，您的應用程式將需要對您的服務，透過使用您的服務訂用帳戶金鑰進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="b2fbf-192">從*快速入門*頁面您*Translator Text*服務，瀏覽至第一個步驟中，*取得您的金鑰*，然後按一下**金鑰**（或者您可以也達到此目的按一下藍色超連結索引鍵，位於服務導覽功能表中，以索引鍵的圖示表示）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="b2fbf-193">這將顯示您的服務*金鑰*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="b2fbf-194">需要顯示的索引鍵，其中的複本，因為您將需要此更新版本中您的專案。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="b2fbf-195">第 2 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="b2fbf-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="b2fbf-196">設定並測試您的混合的實境沈浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="b2fbf-197">您不會需要移動控制器這堂課程。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="b2fbf-198">如果您需要支援的沈浸式耳機的設定，請[遵循下列步驟](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="b2fbf-199">下列已啟動的一組典型混合實境進行開發，此情況下，是良好的其他專案範本：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="b2fbf-200">開啟*Unity*然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-200">Open *Unity* and click **New**.</span></span> 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="b2fbf-202">您現在必須提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="b2fbf-203">插入**MR_Translation**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="b2fbf-204">請確定專案類型設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="b2fbf-205">設定*位置*適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b2fbf-206">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-206">Then, click **Create project**.</span></span>

    ![提供新的 Unity 專案的詳細資料。](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="b2fbf-208">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b2fbf-209">移至**編輯 > 偏好**，然後在新視窗中，瀏覽**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b2fbf-210">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b2fbf-211">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-211">Close the **Preferences** window.</span></span>

    ![更新指令碼編輯器喜好設定。](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="b2fbf-213">接下來，移至**檔案 > 組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![建置設定 視窗中，切換至 UWP 的平台。](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="b2fbf-215">移至**檔案 > 組建設定**並確定：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="b2fbf-216">**裝置為目標**設定為**任何裝置**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="b2fbf-217">對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="b2fbf-218">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="b2fbf-219">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="b2fbf-220">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="b2fbf-221">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="b2fbf-222">儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="b2fbf-223">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b2fbf-224">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-224">A save window will appear.</span></span>

            ![按一下 新增開啟場景按鈕](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="b2fbf-226">建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的指令碼資料夾](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="b2fbf-228">開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中輸入**MR_TranslationScene**，然後按**儲存**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![指定新的場景的名稱。](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="b2fbf-230">請注意，您必須先儲存您的 Unity 場景中*資產*資料夾，因為它們必須是與 Unity 專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="b2fbf-231">建立場景資料夾 （和其他類似的資料夾） 是建構的 Unity 專案的典型方式。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="b2fbf-232">剩餘的設定，*組建設定*，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="b2fbf-233">中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟播放程式設定。](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="b2fbf-235">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="b2fbf-236">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="b2fbf-237">**指令碼執行階段版本**應該**穩定**（.NET 3.5 對等）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="b2fbf-238">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="b2fbf-239">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="b2fbf-241">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="b2fbf-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-242">**InternetClient**</span></span>
        2. <span data-ttu-id="b2fbf-243">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-243">**Microphone**</span></span>

            ![正在更新發行的設定。](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="b2fbf-245">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 R 設定。](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="b2fbf-247">回到**Build Settings**， *UnityC#專案*不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="b2fbf-248">關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="b2fbf-249">儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="b2fbf-250">第 3 章-Main Camera 安裝程式</span><span class="sxs-lookup"><span data-stu-id="b2fbf-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2fbf-251">如果您想要跳過*Unity 設定*元件的課程，並直接在程式碼中繼續進行，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)，它匯入到您的專案做為[ *自訂封裝*](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 5 章](#chapter-5--create-the-results-class)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="b2fbf-252">您仍然必須建立 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="b2fbf-253">在 *階層面板*，您會發現呼叫物件**Main Camera**，這個物件代表您的 「 主要 」 觀點來看，當您 「 內部 」 您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="b2fbf-254">您面前的 Unity 儀表板中，選取**主攝影機 GameObject**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="b2fbf-255">您將會發現*偵測器 面板*（通常是到右方時，儀表板中找到） 將會顯示各種元件的*GameObject*，使用*轉換*在頂端，後面接著*相機*，和一些其他元件。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="b2fbf-256">您必須重設主攝影機的轉換，以便正確地定位。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="b2fbf-257">若要這樣做，請選取**齒輪**相機的旁邊的圖示*轉換*元件，然後選取**重設**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![重設 Main Camera 轉換。](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="b2fbf-259">*轉換*元件再看起來應該像：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="b2fbf-260">*位置*設定為**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="b2fbf-261">*旋轉*設為**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="b2fbf-262">並*擴展*設定為**1，1，1**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![轉換觀景窗的資訊](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="b2fbf-264">接下來，使用**Main Camera**選取資訊，請參閱**新增元件** 按鈕位於最底部*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="b2fbf-265">選取該按鈕，然後搜尋 (輸入*音訊來源*到 [搜尋] 欄位，或瀏覽區段) 稱為元件**音訊來源**，如下所示並加以選取 （按下 enter 上面也可以運作）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="b2fbf-266">*音效來源*元件會加入至**Main Camera**，如下所示。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![新增音訊來源元件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="b2fbf-268">針對 Microsoft HoloLens，您必須也變更下列項目，兩者皆屬於**相機**元件在您**Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="b2fbf-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="b2fbf-269">**清除旗標：** 不透明色彩。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="b2fbf-270">**背景**' Black、 Alpha 0'-十六進位色彩: #00000000。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="b2fbf-271">第 4 章-設定偵錯畫布</span><span class="sxs-lookup"><span data-stu-id="b2fbf-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="b2fbf-272">若要顯示的輸入和輸出的轉譯，必須建立基本的 UI。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="b2fbf-273">這堂課程中，您將建立畫布 UI 物件，以顯示資料的數個 'Text' 物件。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="b2fbf-274">中的空白區域上按一下滑鼠右鍵*階層面板*下方**UI**，加入**畫布**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![加入新的畫布 UI 物件。](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="b2fbf-276">與已選取的畫布物件*偵測器 面板*（在 '畫布 」 元件），變更**轉譯模式**來**世界空間**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="b2fbf-277">接下來，變更下列參數*Inspector 面板 Rect 轉換*:</span><span class="sxs-lookup"><span data-stu-id="b2fbf-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="b2fbf-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="b2fbf-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="b2fbf-279">*Width* -    500</span><span class="sxs-lookup"><span data-stu-id="b2fbf-279">*Width* -    500</span></span>
    3. <span data-ttu-id="b2fbf-280">*Height* -   300</span><span class="sxs-lookup"><span data-stu-id="b2fbf-280">*Height* -   300</span></span>
    4. <span data-ttu-id="b2fbf-281">*縮放比例* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="b2fbf-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![更新畫布的 rect 轉換。](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="b2fbf-283">以滑鼠右鍵按一下**畫布**中*階層面板*下方**UI**，並新增**面板**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="b2fbf-284">這**面板**會提供您將會顯示在場景中的文字的背景。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="b2fbf-285">以滑鼠右鍵按一下**面板**中*階層面板*下方**UI**，並新增**文字物件**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="b2fbf-286">重複相同的程序，直到您完成建立四個 UI 文字物件總計 (提示： 如果您有選取的第一個 'Text' 物件，您可以直接按下 **'Ctrl' + 有 '** 、 複製它，除非您有四個總計)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="b2fbf-287">每個**文字物件**、 選取它，並使用下表設定的參數*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="b2fbf-288">針對*Rect 轉換*元件：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="b2fbf-289">名稱</span><span class="sxs-lookup"><span data-stu-id="b2fbf-289">Name</span></span>                   | <span data-ttu-id="b2fbf-290">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="b2fbf-290">Transform - *Position*</span></span>             | <span data-ttu-id="b2fbf-291">寬度</span><span class="sxs-lookup"><span data-stu-id="b2fbf-291">Width</span></span>      | <span data-ttu-id="b2fbf-292">高度</span><span class="sxs-lookup"><span data-stu-id="b2fbf-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="b2fbf-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="b2fbf-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="b2fbf-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="b2fbf-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="b2fbf-295">300</span><span class="sxs-lookup"><span data-stu-id="b2fbf-295">300</span></span>        | <span data-ttu-id="b2fbf-296">30</span><span class="sxs-lookup"><span data-stu-id="b2fbf-296">30</span></span>        |
        | <span data-ttu-id="b2fbf-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="b2fbf-297">AzureResponseLabel</span></span>     | <span data-ttu-id="b2fbf-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="b2fbf-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="b2fbf-299">300</span><span class="sxs-lookup"><span data-stu-id="b2fbf-299">300</span></span>        | <span data-ttu-id="b2fbf-300">30</span><span class="sxs-lookup"><span data-stu-id="b2fbf-300">30</span></span>        |
        | <span data-ttu-id="b2fbf-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="b2fbf-301">DictationLabel</span></span>         | <span data-ttu-id="b2fbf-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="b2fbf-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="b2fbf-303">300</span><span class="sxs-lookup"><span data-stu-id="b2fbf-303">300</span></span>        | <span data-ttu-id="b2fbf-304">30</span><span class="sxs-lookup"><span data-stu-id="b2fbf-304">30</span></span>        |
        | <span data-ttu-id="b2fbf-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="b2fbf-305">TranslationResultLabel</span></span> | <span data-ttu-id="b2fbf-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="b2fbf-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="b2fbf-307">300</span><span class="sxs-lookup"><span data-stu-id="b2fbf-307">300</span></span>        | <span data-ttu-id="b2fbf-308">30</span><span class="sxs-lookup"><span data-stu-id="b2fbf-308">30</span></span>        |


    2. <span data-ttu-id="b2fbf-309">針對**文字 （指令碼）** 元件：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="b2fbf-310">名稱</span><span class="sxs-lookup"><span data-stu-id="b2fbf-310">Name</span></span>                   | <span data-ttu-id="b2fbf-311">文字</span><span class="sxs-lookup"><span data-stu-id="b2fbf-311">Text</span></span>               | <span data-ttu-id="b2fbf-312">字型大小</span><span class="sxs-lookup"><span data-stu-id="b2fbf-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="b2fbf-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="b2fbf-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="b2fbf-314">麥克風狀態：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-314">Microphone Status:</span></span> | <span data-ttu-id="b2fbf-315">20</span><span class="sxs-lookup"><span data-stu-id="b2fbf-315">20</span></span>           |
        | <span data-ttu-id="b2fbf-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="b2fbf-316">AzureResponseLabel</span></span>     | <span data-ttu-id="b2fbf-317">Azure 的 Web 回應</span><span class="sxs-lookup"><span data-stu-id="b2fbf-317">Azure Web Response</span></span> | <span data-ttu-id="b2fbf-318">20</span><span class="sxs-lookup"><span data-stu-id="b2fbf-318">20</span></span>           |
        | <span data-ttu-id="b2fbf-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="b2fbf-319">DictationLabel</span></span>         |   <span data-ttu-id="b2fbf-320">您剛才提到：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-320">You just said:</span></span>   | <span data-ttu-id="b2fbf-321">20</span><span class="sxs-lookup"><span data-stu-id="b2fbf-321">20</span></span>           |
        | <span data-ttu-id="b2fbf-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="b2fbf-322">TranslationResultLabel</span></span> |    <span data-ttu-id="b2fbf-323">轉譯：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-323">Translation:</span></span>    | <span data-ttu-id="b2fbf-324">20</span><span class="sxs-lookup"><span data-stu-id="b2fbf-324">20</span></span>           |

        ![輸入的 UI 標籤的對應值。](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="b2fbf-326">此外，請 字型樣式**粗體**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="b2fbf-327">這會讓文字更方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-327">This will make the text easier to read.</span></span>

        ![粗體字型。](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="b2fbf-329">每個*UI 文字物件*中建立[第 5 章](#chapter-5--create-the-results-class)，建立新*子* **UI 文字物件**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="b2fbf-330">這些子系會顯示應用程式的輸出。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-330">These children will display the output of the application.</span></span> <span data-ttu-id="b2fbf-331">建立*子系*透過以滑鼠右鍵按一下您要的父系的物件 (例如*MicrophoneStatusLabel*)，然後選取**UI** ，然後選取**文字**.</span><span class="sxs-lookup"><span data-stu-id="b2fbf-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="b2fbf-332">針對每個這些子系，請選取它，然後使用下列設定的參數偵測器 面板中的資料表。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="b2fbf-333">針對**Rect 轉換**元件：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="b2fbf-334">名稱</span><span class="sxs-lookup"><span data-stu-id="b2fbf-334">Name</span></span>                  | <span data-ttu-id="b2fbf-335">轉換-*位置*</span><span class="sxs-lookup"><span data-stu-id="b2fbf-335">Transform - *Position*</span></span> | <span data-ttu-id="b2fbf-336">寬度</span><span class="sxs-lookup"><span data-stu-id="b2fbf-336">Width</span></span>      | <span data-ttu-id="b2fbf-337">高度</span><span class="sxs-lookup"><span data-stu-id="b2fbf-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="b2fbf-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="b2fbf-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="b2fbf-339">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="b2fbf-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="b2fbf-340">300</span><span class="sxs-lookup"><span data-stu-id="b2fbf-340">300</span></span>        | <span data-ttu-id="b2fbf-341">30</span><span class="sxs-lookup"><span data-stu-id="b2fbf-341">30</span></span>        |
        | <span data-ttu-id="b2fbf-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="b2fbf-342">AzureResponseText</span></span>     | <span data-ttu-id="b2fbf-343">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="b2fbf-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="b2fbf-344">300</span><span class="sxs-lookup"><span data-stu-id="b2fbf-344">300</span></span>        | <span data-ttu-id="b2fbf-345">30</span><span class="sxs-lookup"><span data-stu-id="b2fbf-345">30</span></span>        |
        | <span data-ttu-id="b2fbf-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="b2fbf-346">DictationText</span></span>         | <span data-ttu-id="b2fbf-347">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="b2fbf-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="b2fbf-348">300</span><span class="sxs-lookup"><span data-stu-id="b2fbf-348">300</span></span>        | <span data-ttu-id="b2fbf-349">30</span><span class="sxs-lookup"><span data-stu-id="b2fbf-349">30</span></span>        |
        | <span data-ttu-id="b2fbf-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="b2fbf-350">TranslationResultText</span></span> | <span data-ttu-id="b2fbf-351">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="b2fbf-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="b2fbf-352">300</span><span class="sxs-lookup"><span data-stu-id="b2fbf-352">300</span></span>        | <span data-ttu-id="b2fbf-353">30</span><span class="sxs-lookup"><span data-stu-id="b2fbf-353">30</span></span>        |

    2. <span data-ttu-id="b2fbf-354">針對**文字 （指令碼）** 元件：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="b2fbf-355">名稱</span><span class="sxs-lookup"><span data-stu-id="b2fbf-355">Name</span></span>                  | <span data-ttu-id="b2fbf-356">文字</span><span class="sxs-lookup"><span data-stu-id="b2fbf-356">Text</span></span>          | <span data-ttu-id="b2fbf-357">字型大小</span><span class="sxs-lookup"><span data-stu-id="b2fbf-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="b2fbf-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="b2fbf-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="b2fbf-359">??</span><span class="sxs-lookup"><span data-stu-id="b2fbf-359">??</span></span>       | <span data-ttu-id="b2fbf-360">20</span><span class="sxs-lookup"><span data-stu-id="b2fbf-360">20</span></span>           |
        | <span data-ttu-id="b2fbf-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="b2fbf-361">AzureResponseText</span></span>     |      <span data-ttu-id="b2fbf-362">??</span><span class="sxs-lookup"><span data-stu-id="b2fbf-362">??</span></span>       | <span data-ttu-id="b2fbf-363">20</span><span class="sxs-lookup"><span data-stu-id="b2fbf-363">20</span></span>           |
        | <span data-ttu-id="b2fbf-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="b2fbf-364">DictationText</span></span>         |      <span data-ttu-id="b2fbf-365">??</span><span class="sxs-lookup"><span data-stu-id="b2fbf-365">??</span></span>       | <span data-ttu-id="b2fbf-366">20</span><span class="sxs-lookup"><span data-stu-id="b2fbf-366">20</span></span>           |
        | <span data-ttu-id="b2fbf-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="b2fbf-367">TranslationResultText</span></span> |      <span data-ttu-id="b2fbf-368">??</span><span class="sxs-lookup"><span data-stu-id="b2fbf-368">??</span></span>       | <span data-ttu-id="b2fbf-369">20</span><span class="sxs-lookup"><span data-stu-id="b2fbf-369">20</span></span>           |

9. <span data-ttu-id="b2fbf-370">接下來，選取每個文字元件 'centre' 對齊選項：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![文字對齊。](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="b2fbf-372">若要確保**子系 UI 文字**物件都可以輕鬆地讀取、 變更其*色彩*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="b2fbf-373">依序按一下  列上 （目前 ' 黑色'） 下的一步*色彩*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![輸入對應 UI 文字輸出的值。](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="b2fbf-375">然後，在新的很小，*色彩*視窗中，變更*十六進位色彩*來：**0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![更新為藍色的色彩。](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="b2fbf-377">以下是如何**UI**應該看起來。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="b2fbf-378">在 *階層面板*:</span><span class="sxs-lookup"><span data-stu-id="b2fbf-378">In the *Hierarchy Panel*:</span></span>

        ![在提供的結構中的階層。](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="b2fbf-380">在 *場景*並*遊戲檢視*:</span><span class="sxs-lookup"><span data-stu-id="b2fbf-380">In the *Scene* and *Game Views*:</span></span>

        ![在相同的結構中的場景和遊戲的檢視。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="b2fbf-382">第 5 章-建立結果類別</span><span class="sxs-lookup"><span data-stu-id="b2fbf-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="b2fbf-383">您必須建立第一個指令碼*結果*類別，這是負責提供方法，以查看轉譯的結果。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="b2fbf-384">類別會儲存，並會顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="b2fbf-385">從 Azure 回應結果。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-385">The response result from Azure.</span></span>
- <span data-ttu-id="b2fbf-386">麥克風狀態。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-386">The microphone status.</span></span> 
- <span data-ttu-id="b2fbf-387">聽寫 （語音文字） 的結果。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="b2fbf-388">轉譯結果。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-388">The result of the translation.</span></span>

<span data-ttu-id="b2fbf-389">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-389">To create this class:</span></span> 

1.  <span data-ttu-id="b2fbf-390">以滑鼠右鍵按一下*專案 面板*，然後**建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="b2fbf-391">將資料夾命名**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-391">Name the folder **Scripts**.</span></span> 
 
    ![建立指令碼 資料夾。](images/AzureLabs-Lab1-31.png)

    ![開啟 [指令碼] 資料夾。](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="b2fbf-394">具有**指令碼**資料夾建立，連按兩下以開啟該項目。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="b2fbf-395">然後在該資料夾，然後按一下滑鼠右鍵，並選取**建立 >** 再**C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="b2fbf-396">指令碼命名*結果*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-396">Name the script *Results*.</span></span> 

    ![建立第一個指令碼。](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="b2fbf-398">按兩下新*結果*指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="b2fbf-399">插入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="b2fbf-400">類別內插入下列變數：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-400">Inside the Class insert the following variables:</span></span>

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

6.  <span data-ttu-id="b2fbf-401">然後新增*Awake()* 類別初始化時所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="b2fbf-402">最後，新增會負責輸出至 UI 的各種結果資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

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

8.  <span data-ttu-id="b2fbf-403">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="b2fbf-404">第 6 章-建立*MicrophoneManager*類別</span><span class="sxs-lookup"><span data-stu-id="b2fbf-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="b2fbf-405">您要建立第二個類別是*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="b2fbf-406">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-406">This class is responsible for:</span></span>

- <span data-ttu-id="b2fbf-407">偵測耳機或 （無論是預設值） 的機器附加的錄音裝置。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="b2fbf-408">擷取音訊 （語音），並將它儲存為字串使用聽寫。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="b2fbf-409">一旦已暫停的語音，提交聽寫，轉譯器類別。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="b2fbf-410">裝載的方法，如有需要，可停止語音擷取。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="b2fbf-411">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-411">To create this class:</span></span> 
1.  <span data-ttu-id="b2fbf-412">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="b2fbf-413">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="b2fbf-414">指令碼命名*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="b2fbf-415">按兩下新的指令碼，以使用 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="b2fbf-416">更新命名空間相同，如下所示，在頂端*MicrophoneManager*類別：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="b2fbf-417">然後，新增下列變數內*MicrophoneManager*類別：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

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

6.  <span data-ttu-id="b2fbf-418">程式碼*Awake()* 並*start （)* 方法現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="b2fbf-419">在類別初始化時，這些將會呼叫：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-419">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="b2fbf-420">您可以*刪除* *update （)* 方法，因為這個類別不會使用它。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="b2fbf-421">現在，您需要讓應用程式用來啟動和停止語音擷取，並將它傳遞至方法*Translator*您即將建置的類別。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="b2fbf-422">下列程式碼複製並貼上下方*start （)* 方法。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

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
    > <span data-ttu-id="b2fbf-423">雖然此應用程式不會使用它， *StopCapturingAudio()* 方法也已提供在這裡，如果您想要實作的功能，以停止擷取您的應用程式中的音訊。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="b2fbf-424">您現在需要新增語音停止時將會叫用語音輸入處理常式。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="b2fbf-425">這個方法會再將要聽寫的文字*Translator*類別。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-425">This method will then pass the dictated text to the *Translator* class.</span></span>

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

10. <span data-ttu-id="b2fbf-426">請務必在 Visual Studio 中儲存您的變更，然後再回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="b2fbf-427">此時您會注意到錯誤不會出現在*Unity 編輯器 主控台*面板 ("name 'Translator' 不存在...」)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="b2fbf-428">這是因為程式碼參考*Translator*類別，您將在下一步 一章。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="b2fbf-429">第 7 章 – 對 Azure 和轉譯程式的服務呼叫</span><span class="sxs-lookup"><span data-stu-id="b2fbf-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="b2fbf-430">您需要建立的最後一個指令碼*Translator*類別。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="b2fbf-431">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-431">This class is responsible for:</span></span>

-   <span data-ttu-id="b2fbf-432">驗證應用程式與*Azure*，exchange for**驗證權杖**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="b2fbf-433">使用**驗證權杖**送出的文字 (收到*MicrophoneManager*類別) 來轉譯。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="b2fbf-434">接收轉譯的結果，並將它傳遞給*結果*類別，以在 UI 中視覺化。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="b2fbf-435">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-435">To create this Class:</span></span> 
1.  <span data-ttu-id="b2fbf-436">移至**指令碼**您先前建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="b2fbf-437">以滑鼠右鍵按一下**專案 面板**，**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="b2fbf-438">呼叫指令碼*Translator*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="b2fbf-439">按兩下新*Translator*以開啟它的指令碼**使用 Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="b2fbf-440">檔案開頭處新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="b2fbf-441">然後新增下列變數內*Translator*類別：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-441">Then add the following variables inside the *Translator* class:</span></span>

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
    > - <span data-ttu-id="b2fbf-442">插入至語言的語言**enum**只是範例。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="b2fbf-443">依需要新增更多，如果您想要的選項;[API 支援 60 語言](https://docs.microsoft.com/azure/cognitive-services/translator/languages)（包括克林貢） ！</span><span class="sxs-lookup"><span data-stu-id="b2fbf-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="b2fbf-444">沒有[涵蓋可用的語言更具互動性的頁面](https://www.microsoft.com/translator/business/languages/)，不過留意頁面才會出現在時使用的站台語言設定為 ' en-' （和 Microsoft 網站將 可能的重新導向至您的原生語言）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="b2fbf-445">您可以變更站台的語言，在下方的頁面或改變的 URL。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="b2fbf-446">**AuthorizationKey**值，在上述程式碼片段中，必須**金鑰**您訂閱時，您會收到*Azure Translator Text API*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="b2fbf-447">這已涵蓋在[第 1 章](#chapter-1--the-azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="b2fbf-448">程式碼*Awake()* 並*start （)* 方法現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="b2fbf-449">在此情況下，程式碼會呼叫*Azure*使用授權金鑰，取得*語彙基元*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

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
    > <span data-ttu-id="b2fbf-450">權杖會在 10 分鐘後過期。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="b2fbf-451">根據您的應用程式案例，您可能必須進行多次呼叫相同的協同程式。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="b2fbf-452">若要取得此語彙基元協同程式如下：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-452">The coroutine to obtain the Token is the following:</span></span>

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
    > <span data-ttu-id="b2fbf-453">如果您編輯 IEnumerator 方法的名稱**GetTokenCoroutine()** ，您需要更新*StartCoroutine*並*StopCoroutine*呼叫上述程式碼中的字串值。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="b2fbf-454">[根據 Unity 文件](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)，以停止特定*協同程式*，您需要使用的字串值的方法。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="b2fbf-455">接下來，新增的協同程式 （使用 「 支援 」 資料流的方法正下方） 以取得所收到的文字翻譯*MicrophoneManager*類別。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="b2fbf-456">此程式碼會建立將傳送至查詢字串*Azure Translator Text API*，然後使用內部的 Unity UnityWebRequest 類別的查詢字串的端點 'Get' 呼叫。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="b2fbf-457">結果是再用來設定您的結果物件中的翻譯。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="b2fbf-458">下列程式碼顯示實作：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-458">The code below shows the implementation:</span></span>

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

10. <span data-ttu-id="b2fbf-459">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="b2fbf-460">第 8 – 設定 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="b2fbf-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="b2fbf-461">傳回在 Unity 編輯器中，按一下並拖曳 *結果* 類別 *從* **指令碼** 資料夾 **Main Camera** 中的物件 *階層面板*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="b2fbf-462">按一下  **Main Camera**並查看*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="b2fbf-463">您會注意到內新增*指令碼*元件，有四個欄位為空值。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="b2fbf-464">這些是在程式碼屬性的輸出參考。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="b2fbf-465">拖曳適當**文字**物件從*階層面板*對這些四個位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![使用指定的值更新目標參考。](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="b2fbf-467">接下來，按一下並拖曳*Translator*從類別**指令碼**資料夾**Main Camera**物件*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="b2fbf-468">然後，按一下並拖曳*MicrophoneManager*從類別**指令碼**資料夾**Main Camera**物件*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="b2fbf-469">最後，按一下**Main Camera**並查看*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="b2fbf-470">您會發現，在您拖放至指令碼，有兩個的下拉式清單方塊，可讓您設定的語言。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![請確定輸入的預定的翻譯語言。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="b2fbf-472">第 9 章 – 在混合實境中的測試</span><span class="sxs-lookup"><span data-stu-id="b2fbf-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="b2fbf-473">此時，您需要測試已正確地實作場景。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="b2fbf-474">請確定：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-474">Ensure that:</span></span>

- <span data-ttu-id="b2fbf-475">中所述的所有設定[第 1 章](#chapter-1--the-azure-portal)都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="b2fbf-476">*結果*， *Translator*，並*MicrophoneManager*，指令碼會附加至**Main Camera**物件。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="b2fbf-477">您已經放置您*Azure Translator Text API*服務**金鑰**內**authorizationKey**變數*Translator*指令碼。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="b2fbf-478">中的所有欄位*Main 攝影機偵測器 面板*皆正確。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="b2fbf-479">執行您的場景時，是否正常運作您的麥克風 (如果沒有，請檢查您連接的麥克風*預設*裝置，而且您擁有[正確地設定 Windows 內](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10))。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="b2fbf-480">您可以藉由按下測試沈浸式耳機**播放**按鈕*Unity Editor*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="b2fbf-481">應用程式應該可以正常運作，透過附加的沈浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="b2fbf-482">如果您看到錯誤的相關變更預設音訊裝置，Unity 主控台中，場景可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="b2fbf-483">這是因為內建麥克風耳機，讓它們會處理混合的實境入口網站的方式。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="b2fbf-484">如果您看到此錯誤，只是停止場景並重新啟動它，而且項目應該都能當作預期。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="b2fbf-485">第 10 – 建置 UWP 方案，然後在本機電腦上的側載</span><span class="sxs-lookup"><span data-stu-id="b2fbf-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="b2fbf-486">此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="b2fbf-487">瀏覽至**組建設定**:**檔案 > 組建設定...**</span><span class="sxs-lookup"><span data-stu-id="b2fbf-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="b2fbf-488">從**Build Settings**  視窗中，按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-488">From the **Build Settings** window, click **Build**.</span></span>

    ![建置 Unity 場景。](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="b2fbf-490">如果您尚未，勾選**UnityC#專案**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="b2fbf-491">按一下 [建置]  。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-491">Click **Build**.</span></span> <span data-ttu-id="b2fbf-492">將會啟動 unity*檔案總管*視窗中，您要建立，然後選取 建置到應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b2fbf-493">現在，建立該資料夾並將它命名*應用程式*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="b2fbf-494">然後使用*應用程式*資料夾選取，請按下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="b2fbf-495">Unity 會開始建置您的專案*應用程式*資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="b2fbf-496">一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟*檔案總管*視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="b2fbf-497">第 11 章-部署您的應用程式</span><span class="sxs-lookup"><span data-stu-id="b2fbf-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="b2fbf-498">若要部署您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-498">To deploy your application:</span></span>

1.  <span data-ttu-id="b2fbf-499">瀏覽至新的 Unity 組建 (*應用程式*資料夾)，並開啟方案檔*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="b2fbf-500">在 方案組態選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="b2fbf-501">在 方案平台上，選取**x86**，**本機**。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="b2fbf-502">針對 Microsoft HoloLens，您可能會發現它更輕鬆地將此設為*遠端機器*，如此一來，您不行動網卡到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="b2fbf-503">不過，您必須也執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="b2fbf-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="b2fbf-504">了解**IP 位址**的您 HoloLens，位於*設定 > 網路和網際網路 > Wi-fi > 進階選項*; IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="b2fbf-505">請確定*開發人員模式*是**上**; 在找到*設定 > 更新與安全性 > 適用於開發人員*。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="b2fbf-507">移至**建置 功能表**，然後按一下**部署方案**側載應用程式以您的電腦。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="b2fbf-508">您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="b2fbf-509">一旦啟動，應用程式會提示您授權存取麥克風。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="b2fbf-510">請務必按一下 [**是**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="b2fbf-511">您現在已準備好開始轉譯 ！</span><span class="sxs-lookup"><span data-stu-id="b2fbf-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="b2fbf-512">您已完成的翻譯文字 API 應用程式</span><span class="sxs-lookup"><span data-stu-id="b2fbf-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="b2fbf-513">恭喜，您所建立的混合的實境應用程式，運用 Azure 翻譯文字 API，將語音翻譯的文字。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![最終的產品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b2fbf-515">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="b2fbf-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b2fbf-516">練習 1</span><span class="sxs-lookup"><span data-stu-id="b2fbf-516">Exercise 1</span></span>

<span data-ttu-id="b2fbf-517">可以您文字轉換語音將功能加入至應用程式，使傳回的文字說出？</span><span class="sxs-lookup"><span data-stu-id="b2fbf-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b2fbf-518">練習 2</span><span class="sxs-lookup"><span data-stu-id="b2fbf-518">Exercise 2</span></span>

<span data-ttu-id="b2fbf-519">讓使用者變更應用程式本身，來源和輸出的語言 （'from' 和 'to'），因此應用程式就不需要重建每次您想要變更語言。</span><span class="sxs-lookup"><span data-stu-id="b2fbf-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
