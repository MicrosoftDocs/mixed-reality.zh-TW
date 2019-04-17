---
title: MR 和 Azure 312-Bot 整合
description: 完成此課程來了解如何建立及部署 bot，使用 Microsoft Bot Framework v4，並與其通訊的混合的實境應用程式中。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 電腦視景、 hololens、 沉浸式 vr microsoft bot framework v4、 web 應用程式 bot、 bot framework、 microsoft bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597078"
---
>[!NOTE]
><span data-ttu-id="95d4f-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="95d4f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="95d4f-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="95d4f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="95d4f-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="95d4f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="95d4f-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="95d4f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="95d4f-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="95d4f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="95d4f-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="95d4f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="95d4f-110">MR 和 Azure 312:Bot 整合</span><span class="sxs-lookup"><span data-stu-id="95d4f-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="95d4f-111">在此課程中，您將學習如何建立並部署使用 Microsoft Bot Framework V4 bot，並透過 Windows Mixed Reality 應用程式與其通訊。</span><span class="sxs-lookup"><span data-stu-id="95d4f-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="95d4f-112">**Microsoft Bot Framework V4**是一組 Api 可提供開發人員工具來建置可擴充且可調整的 bot 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95d4f-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="95d4f-113">如需詳細資訊，請瀏覽[Microsoft Bot Framework 頁面](https://dev.botframework.com/)或[V4 Git 存放庫](https://github.com/Microsoft/botbuilder-dotnet/wiki)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="95d4f-114">完成本課程之後，您就會建置的 Windows Mixed Reality 應用程式，可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="95d4f-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="95d4f-115">使用**點選手勢**開始接聽使用者語音 bot。</span><span class="sxs-lookup"><span data-stu-id="95d4f-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="95d4f-116">當使用者說過的項目 bot 會嘗試提供回應。</span><span class="sxs-lookup"><span data-stu-id="95d4f-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="95d4f-117">Bot 回覆文字顯示，bot，Unity 場景中靠近定位。</span><span class="sxs-lookup"><span data-stu-id="95d4f-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="95d4f-118">在您的應用程式，則您對於如何將整合結果進行設計。</span><span class="sxs-lookup"><span data-stu-id="95d4f-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="95d4f-119">本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="95d4f-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="95d4f-120">它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。</span><span class="sxs-lookup"><span data-stu-id="95d4f-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="95d4f-121">裝置支援</span><span class="sxs-lookup"><span data-stu-id="95d4f-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="95d4f-122">課程</span><span class="sxs-lookup"><span data-stu-id="95d4f-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="95d4f-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="95d4f-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="95d4f-124"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="95d4f-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="95d4f-125">MR 和 Azure 312:Bot 整合</span><span class="sxs-lookup"><span data-stu-id="95d4f-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="95d4f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="95d4f-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="95d4f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="95d4f-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="95d4f-128">雖然這堂課程主要著重於 HoloLens，您也可以套用您在此課程 Windows Mixed Reality 沈浸式 (VR) 耳機來了解。</span><span class="sxs-lookup"><span data-stu-id="95d4f-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="95d4f-129">因為沈浸式 (VR) 耳機並沒有可存取的相機，您必須連線到您的 PC 外部相機。</span><span class="sxs-lookup"><span data-stu-id="95d4f-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="95d4f-130">當您遵循本課程中，您會看到 備忘稿上用來支援沈浸式 (VR) 耳機時，您可能需要的任何變更。</span><span class="sxs-lookup"><span data-stu-id="95d4f-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95d4f-131">先決條件</span><span class="sxs-lookup"><span data-stu-id="95d4f-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="95d4f-132">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="95d4f-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="95d4f-133">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。</span><span class="sxs-lookup"><span data-stu-id="95d4f-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="95d4f-134">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。</span><span class="sxs-lookup"><span data-stu-id="95d4f-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="95d4f-135">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="95d4f-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="95d4f-136">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="95d4f-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="95d4f-137">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="95d4f-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="95d4f-138">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="95d4f-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="95d4f-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="95d4f-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="95d4f-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="95d4f-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="95d4f-141">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="95d4f-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="95d4f-142">Azure 和 Azure Bot 擷取的網際網路存取。</span><span class="sxs-lookup"><span data-stu-id="95d4f-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="95d4f-143">如需詳細資訊，[請遵循此連結](https://dev.botframework.com/)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="95d4f-144">開始之前</span><span class="sxs-lookup"><span data-stu-id="95d4f-144">Before you start</span></span>

1.  <span data-ttu-id="95d4f-145">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="95d4f-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="95d4f-146">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="95d4f-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="95d4f-147">如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="95d4f-148">它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。</span><span class="sxs-lookup"><span data-stu-id="95d4f-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="95d4f-149">校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="95d4f-150">如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="95d4f-151">第 1 章-建立機器人應用程式</span><span class="sxs-lookup"><span data-stu-id="95d4f-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="95d4f-152">第一個步驟是建立您的機器人，做為本機的 ASP.Net Core Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95d4f-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="95d4f-153">一旦您完成並測試它，將會發行至 Azure 入口網站。</span><span class="sxs-lookup"><span data-stu-id="95d4f-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="95d4f-154">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="95d4f-154">Open Visual Studio.</span></span> <span data-ttu-id="95d4f-155">建立新專案，選取**ASP NET Core Web 應用程式**做為專案類型 （您會發現它在.NET Core 的小節），並稱之為**MyBot**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="95d4f-156">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="95d4f-156">Click **OK**.</span></span>

2.  <span data-ttu-id="95d4f-157">在視窗中會出現選取**空**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="95d4f-158">也請確定目標設為**ASP NET Core 2.0**並驗證已設為**不需要驗證**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="95d4f-159">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="95d4f-159">Click **OK**.</span></span>  

    ![建立機器人應用程式](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="95d4f-161">現在將會開啟解決方案。</span><span class="sxs-lookup"><span data-stu-id="95d4f-161">The solution will now open.</span></span> <span data-ttu-id="95d4f-162">以滑鼠右鍵按一下方案**Mybot**中**方案總管**，然後按一下**管理方案的 NuGet 套件**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![建立機器人應用程式](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="95d4f-164">在 **瀏覽**索引標籤上，搜尋**Microsoft.Bot.Builder.Integration.AspNet.Core** (請確定您已**包含發行前版本**檢查)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="95d4f-165">選取的套件版本**4.0.1**，和勾選的 [專案] 方塊。</span><span class="sxs-lookup"><span data-stu-id="95d4f-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="95d4f-166">然後按一下**安裝**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-166">Then click on **Install**.</span></span> <span data-ttu-id="95d4f-167">現在您已安裝所需的程式庫**Bot Framework v4**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="95d4f-168">關閉 [NuGet] 頁面。</span><span class="sxs-lookup"><span data-stu-id="95d4f-168">Close the NuGet page.</span></span>

    ![建立機器人應用程式](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="95d4f-170">以滑鼠右鍵按一下您*專案*， **MyBot**，請在**方案總管 中**，然後按一下**新增** **|\*\*\*\*類別**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![建立機器人應用程式](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="95d4f-172">將類別命名為**MyBot** ，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![建立機器人應用程式](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="95d4f-174">重複前一個點，來建立名為另一個類別**ConversationContext**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="95d4f-175">以滑鼠右鍵按一下**wwwroot**中**方案總管**，然後按一下**新增** **|** **新項目**.</span><span class="sxs-lookup"><span data-stu-id="95d4f-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="95d4f-176">選取  **HTML 網頁**（您會發現它在 Web 子區段下）。</span><span class="sxs-lookup"><span data-stu-id="95d4f-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="95d4f-177">將檔案命名**default.html**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-177">Name the file **default.html**.</span></span> <span data-ttu-id="95d4f-178">按一下 **\[新增\]**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-178">Click **Add**.</span></span>

    ![建立機器人應用程式](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="95d4f-180">類別的清單中的物件 /**方案總管 中**看起來應該像下列映像。</span><span class="sxs-lookup"><span data-stu-id="95d4f-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![建立機器人應用程式](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="95d4f-182">按兩下**ConversationContext**類別。</span><span class="sxs-lookup"><span data-stu-id="95d4f-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="95d4f-183">這個類別是對話的負責保存用來維護內容機器人的變數。</span><span class="sxs-lookup"><span data-stu-id="95d4f-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="95d4f-184">因為，將會維護此類別的執行個體中的這些交談內容值的任何執行個體**MyBot**類別將會重新整理每個活動接收的時間。</span><span class="sxs-lookup"><span data-stu-id="95d4f-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="95d4f-185">將下列程式碼新增至類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="95d4f-186">按兩下**MyBot**類別。</span><span class="sxs-lookup"><span data-stu-id="95d4f-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="95d4f-187">這個類別會裝載任何連入的活動所呼叫，從客戶的處理常式。</span><span class="sxs-lookup"><span data-stu-id="95d4f-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="95d4f-188">此類別中，您將加入的程式碼，用來建置 bot 和客戶之間的對話。</span><span class="sxs-lookup"><span data-stu-id="95d4f-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="95d4f-189">如先前所述，此類別的執行個體被初始化每一個接收活動的時間。</span><span class="sxs-lookup"><span data-stu-id="95d4f-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="95d4f-190">將下列程式碼新增至此類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="95d4f-191">按兩下**啟動**類別。</span><span class="sxs-lookup"><span data-stu-id="95d4f-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="95d4f-192">這個類別會初始化 bot。</span><span class="sxs-lookup"><span data-stu-id="95d4f-192">This class will initialize the bot.</span></span> <span data-ttu-id="95d4f-193">將下列程式碼新增至類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="95d4f-194">開啟**程式**類別檔案，並確認它的程式碼如下所示相同：</span><span class="sxs-lookup"><span data-stu-id="95d4f-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="95d4f-195">請務必儲存您的變更，若要這樣做，請移至**檔案** > **全部儲存**，從頂端的 Visual Studio 工具列。</span><span class="sxs-lookup"><span data-stu-id="95d4f-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="95d4f-196">第 2-建立 Azure Bot 服務</span><span class="sxs-lookup"><span data-stu-id="95d4f-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="95d4f-197">既然您已針對您的 bot 建立程式碼，您必須將它發行到的執行個體*Web 應用程式 Bot*服務，在 Azure 入口網站上的。</span><span class="sxs-lookup"><span data-stu-id="95d4f-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="95d4f-198">本章將說明如何建立並設定在 Azure 上的機器人服務，然後再將您的程式碼發佈到它。</span><span class="sxs-lookup"><span data-stu-id="95d4f-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="95d4f-199">首先，登入 Azure 入口網站 (https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="95d4f-200">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="95d4f-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="95d4f-201">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="95d4f-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="95d4f-202">一旦您登入，按一下**建立資源**在左上角，，然後搜尋*Web 應用程式 bot*，然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="95d4f-204">新的頁面將提供的描述*Web 應用程式 Bot*服務。</span><span class="sxs-lookup"><span data-stu-id="95d4f-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="95d4f-205">在左下方的這個頁面上，選取**建立**按鈕，以建立與這個關聯服務。</span><span class="sxs-lookup"><span data-stu-id="95d4f-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="95d4f-207">一旦您按下**建立**:</span><span class="sxs-lookup"><span data-stu-id="95d4f-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="95d4f-208">插入您想要**名稱**此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="95d4f-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="95d4f-209">選取 **訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="95d4f-210">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="95d4f-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="95d4f-211">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="95d4f-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="95d4f-212">建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。</span><span class="sxs-lookup"><span data-stu-id="95d4f-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="95d4f-213">如果您想要深入了解 Azure 資源群組，[請遵循此連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="95d4f-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="95d4f-214">（如果您要建立新的資源群組），請判斷您的資源群組的位置。</span><span class="sxs-lookup"><span data-stu-id="95d4f-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="95d4f-215">位置，在理想情況下會在應用程式會執行所在的區域。</span><span class="sxs-lookup"><span data-stu-id="95d4f-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="95d4f-216">在特定區域中，才可以使用一些 Azure 的資產。</span><span class="sxs-lookup"><span data-stu-id="95d4f-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="95d4f-217">選取 **定價層**適合您，如果這是第一個時間來建立*Web 應用程式 Bot*服務，免費層 （名為 F0） 應該是您可以使用</span><span class="sxs-lookup"><span data-stu-id="95d4f-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="95d4f-218">**應用程式名稱**可以只保留相同*Bot 名稱*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="95d4f-219">離開*Bot 範本*作為**基本 (C#)**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="95d4f-220">*App service 方案/位置*應該已自動填入您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="95d4f-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="95d4f-221">設定**Azure 儲存體**您想要用來裝載您的機器人。</span><span class="sxs-lookup"><span data-stu-id="95d4f-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="95d4f-222">如果您還沒有，您可以在此建立。</span><span class="sxs-lookup"><span data-stu-id="95d4f-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="95d4f-223">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="95d4f-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="95d4f-224">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="95d4f-224">Click Create.</span></span>
 
        ![建立 Azure Bot 服務](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="95d4f-226">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="95d4f-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="95d4f-227">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="95d4f-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="95d4f-229">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="95d4f-229">Click on the notification to explore your new Service instance.</span></span> 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="95d4f-231">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="95d4f-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="95d4f-232">您會前往新的 Azure 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="95d4f-232">You will be taken to your new Azure Service instance.</span></span> 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="95d4f-234">此時您需要設定稱為功能**直線**以允許用戶端應用程式與此 Bot 服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="95d4f-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="95d4f-235">按一下 **通道**，然後在**新增精選的頻道**區段中，按一下**設定直接線路通道**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="95d4f-237">在此頁面中，您會發現**祕密金鑰**，可讓您的用戶端應用程式與機器人進行驗證。</span><span class="sxs-lookup"><span data-stu-id="95d4f-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="95d4f-238">按一下 **顯示**按鈕並複製的其中一個顯示的金鑰，因為您將需要這稍後會在您的專案。</span><span class="sxs-lookup"><span data-stu-id="95d4f-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="95d4f-240">第 3-將 Bot 發行至 Azure Web 應用程式 Bot 服務</span><span class="sxs-lookup"><span data-stu-id="95d4f-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="95d4f-241">現在，您的服務已準備就緒，您需要將您的 Bot 程式碼，您建置之前，您新建立的 Web 應用程式 Bot 服務的發佈。</span><span class="sxs-lookup"><span data-stu-id="95d4f-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="95d4f-242">您必須將您的 Bot 發行至 Azure 服務，每次您變更 Bot 解決方案 / c o d。</span><span class="sxs-lookup"><span data-stu-id="95d4f-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="95d4f-243">回到您先前建立的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="95d4f-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="95d4f-244">以滑鼠右鍵按一下您**MyBot**專案中，在**方案總管**，然後按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![將 Bot 發行至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="95d4f-246">在上*挑選發行目標*頁面上，按一下**App Service**，然後**選取現有**，最後按一下**建立設定檔**（您可能需要按一下旁邊的下拉式箭號*發佈*按鈕，如果這是不可見)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![將 Bot 發行至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="95d4f-248">如果您尚未登入到您的 Microsoft 帳戶，您必須在此處進行。</span><span class="sxs-lookup"><span data-stu-id="95d4f-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="95d4f-249">在上**發佈**您會發現您需要設定相同的頁面**訂用帳戶**用於*Web 應用程式 Bot*建立服務。</span><span class="sxs-lookup"><span data-stu-id="95d4f-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="95d4f-250">然後設定**檢視**作為**資源群組**，然後在下拉式清單的資料夾結構中，選取**資源群組**您先前建立。</span><span class="sxs-lookup"><span data-stu-id="95d4f-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="95d4f-251">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="95d4f-251">Click **OK**.</span></span> 

    ![將 Bot 發行至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="95d4f-253">現在，按一下**發佈**按鈕，並等候 Bot 發行 （可能需要幾分鐘的時間）。</span><span class="sxs-lookup"><span data-stu-id="95d4f-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![將 Bot 發行至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="95d4f-255">第 4 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="95d4f-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="95d4f-256">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="95d4f-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="95d4f-257">開啟*Unity*然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-257">Open *Unity* and click **New**.</span></span> 

    ![設定 Unity 專案](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="95d4f-259">您現在必須提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="95d4f-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="95d4f-260">插入**Hololens Bot**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="95d4f-261">請確定已設定的專案範本**3D**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="95d4f-262">設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="95d4f-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="95d4f-263">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-263">Then, click **Create project**.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="95d4f-265">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="95d4f-266">移至**編輯 > 偏好**，然後在新視窗中，瀏覽**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="95d4f-267">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="95d4f-268">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="95d4f-268">Close the **Preferences** window.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="95d4f-270">接下來，移至**檔案 > 組建設定**，然後選取**通用 Windows 平台**，然後按一下**切換平台**按鈕以套用您的選擇。</span><span class="sxs-lookup"><span data-stu-id="95d4f-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="95d4f-272">當您依然在**檔案 > 組建設定**並確定：</span><span class="sxs-lookup"><span data-stu-id="95d4f-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="95d4f-273">**裝置為目標**設為**Hololens**</span><span class="sxs-lookup"><span data-stu-id="95d4f-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="95d4f-274">針對擬真耳機，設定**目標裝置**要*任何裝置*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="95d4f-275">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="95d4f-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="95d4f-276">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="95d4f-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="95d4f-277">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="95d4f-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="95d4f-278">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="95d4f-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="95d4f-279">儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="95d4f-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="95d4f-280">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="95d4f-281">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="95d4f-281">A save window will appear.</span></span>
        
            ![設定 Unity 專案](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="95d4f-283">建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![設定 Unity 專案](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="95d4f-285">開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中，輸入**BotScene**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="95d4f-287">剩餘的設定，**組建設定**，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="95d4f-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="95d4f-288">中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。</span><span class="sxs-lookup"><span data-stu-id="95d4f-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![設定 Unity 專案](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="95d4f-290">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="95d4f-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="95d4f-291">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="95d4f-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="95d4f-292">**指令碼執行階段版本**應該 **（.NET 4.6 對等） 的實驗性**; 變更這項需要重新啟動的編輯器。</span><span class="sxs-lookup"><span data-stu-id="95d4f-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="95d4f-293">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="95d4f-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="95d4f-294">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="95d4f-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="95d4f-296">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="95d4f-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="95d4f-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="95d4f-297">**InternetClient**</span></span>
        - <span data-ttu-id="95d4f-298">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="95d4f-298">**Microphone**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="95d4f-300">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。</span><span class="sxs-lookup"><span data-stu-id="95d4f-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="95d4f-302">回到*Build Settings* _Unity C#_ 專案不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="95d4f-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="95d4f-303">關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="95d4f-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="95d4f-304">儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="95d4f-305">第 5 章-觀景窗設定</span><span class="sxs-lookup"><span data-stu-id="95d4f-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95d4f-306">如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[Azure MR-312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)，它匯入到您的專案，作為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 7 章](#chapter-7-–-create-the-botobjects-class)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="95d4f-307">在 *階層面板*，選取**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="95d4f-308">選取之後，您將能夠看到所有的元件**Main Camera**中*Inspector 面板*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="95d4f-309">**相機物件**必須命名為**Main Camera** （請注意拼字檢查）</span><span class="sxs-lookup"><span data-stu-id="95d4f-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="95d4f-310">Main Camera**標記**必須設為**MainCamera** （請注意拼字檢查）</span><span class="sxs-lookup"><span data-stu-id="95d4f-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="95d4f-311">請確定**轉換的位置**設定為**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="95d4f-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="95d4f-312">設定**清除旗標**要**單色**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="95d4f-313">設定**背景**相機元件以色彩**黑色，0 的 Alpha (十六進位的程式碼: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="95d4f-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![照相機設定](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="95d4f-315">第 6 章-匯入 Newtonsoft 程式庫</span><span class="sxs-lookup"><span data-stu-id="95d4f-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="95d4f-316">若要可協助您還原序列化和序列化物件接收和傳送到 Bot 服務，您需要下載**Newtonsoft**程式庫。</span><span class="sxs-lookup"><span data-stu-id="95d4f-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="95d4f-317">您會發現[相容的版本已經組織使用的正確 Unity 資料夾結構這裡](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="95d4f-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="95d4f-318">若要 Newtonsoft 程式庫匯入專案中，使用 Unity 套件所附的這堂課程。</span><span class="sxs-lookup"><span data-stu-id="95d4f-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="95d4f-319">新增 *.unitypackage*若要使用的 Unity**資產** > **匯入封裝** > **自訂封裝**功能表選項。</span><span class="sxs-lookup"><span data-stu-id="95d4f-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![匯入 Newtonsoft 程式庫](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="95d4f-321">在 **匯入 Unity 封裝**方塊會顯示。 請確認所有項目底下 （而且包括）**外掛程式**已選取。</span><span class="sxs-lookup"><span data-stu-id="95d4f-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![匯入 Newtonsoft 程式庫](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="95d4f-323">按一下 **匯入**按鈕以新增至您的專案項目。</span><span class="sxs-lookup"><span data-stu-id="95d4f-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="95d4f-324">移至**Newtonsoft**下方的資料夾**外掛程式**專案檢視，然後選取 Newtonsoft 外掛程式中。</span><span class="sxs-lookup"><span data-stu-id="95d4f-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="95d4f-325">使用選取 Newtonsoft 外掛程式，請確認**任何平台**是**取消核取**，然後確定**WSAPlayer**也是**未核取**，然後按一下**套用**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="95d4f-326">這只是要確認已正確設定檔案。</span><span class="sxs-lookup"><span data-stu-id="95d4f-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="95d4f-327">標示這些外掛程式會設定它們僅適用於在 Unity 編輯器中。</span><span class="sxs-lookup"><span data-stu-id="95d4f-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="95d4f-328">有一組不同的專案會匯出從 Unity 後要使用 WSA 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="95d4f-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="95d4f-329">接下來，您必須開啟**WSA**資料夾內**Newtonsoft**資料夾。</span><span class="sxs-lookup"><span data-stu-id="95d4f-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="95d4f-330">您會看到您剛才設定的相同檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="95d4f-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="95d4f-331">選取檔案，並在偵測器中，確定該</span><span class="sxs-lookup"><span data-stu-id="95d4f-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="95d4f-332">**任何平台**是**unchecked**</span><span class="sxs-lookup"><span data-stu-id="95d4f-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="95d4f-333">**只有** **WSAPlayer**是**檢查**</span><span class="sxs-lookup"><span data-stu-id="95d4f-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="95d4f-334">**不會處理**是**檢查**</span><span class="sxs-lookup"><span data-stu-id="95d4f-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="95d4f-335">第 7 – 建立 BotTag</span><span class="sxs-lookup"><span data-stu-id="95d4f-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="95d4f-336">建立新**標記**呼叫的物件**BotTag**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="95d4f-337">您可以選取 Main Camera 在場景中。</span><span class="sxs-lookup"><span data-stu-id="95d4f-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="95d4f-338">按一下標記下拉式功能表偵測器 面板中。</span><span class="sxs-lookup"><span data-stu-id="95d4f-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="95d4f-339">按一下 **新增標記**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-339">Click on **Add Tag**.</span></span>

    ![照相機設定](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="95d4f-341">按一下  **+** 符號。</span><span class="sxs-lookup"><span data-stu-id="95d4f-341">Click on the **+** symbol.</span></span> <span data-ttu-id="95d4f-342">指定新**標記**作為**BotTag**，*儲存*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![照相機設定](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="95d4f-344">**不這麼做**套用**BotTag**到 Main Camera。</span><span class="sxs-lookup"><span data-stu-id="95d4f-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="95d4f-345">如果您不小心這麼做，請務必變更標記回到 Main Camera *MainCamera*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="95d4f-346">第 8 章-建立 BotObjects 類別</span><span class="sxs-lookup"><span data-stu-id="95d4f-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="95d4f-347">您必須建立第一個指令碼**BotObjects**類別，這是空的類別建立，因此一系列的其他類別的物件可儲存在相同的指令碼，並在場景中其他指令碼存取。</span><span class="sxs-lookup"><span data-stu-id="95d4f-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="95d4f-348">建立這個類別是純粹的架構的選擇，這些物件可以改為裝載於稍後在本課程中，您將建立 Bot 指令碼。</span><span class="sxs-lookup"><span data-stu-id="95d4f-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="95d4f-349">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-349">To create this class:</span></span> 

1.  <span data-ttu-id="95d4f-350">以滑鼠右鍵按一下 *[專案] 面板*，然後**建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="95d4f-351">將資料夾命名**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-351">Name the folder **Scripts**.</span></span> 

    ![建立指令碼 資料夾。](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="95d4f-353">按兩下**指令碼**資料夾將它開啟。</span><span class="sxs-lookup"><span data-stu-id="95d4f-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="95d4f-354">然後在該資料夾，然後按一下滑鼠右鍵，並選取**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="95d4f-355">指令碼命名**BotObjects**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="95d4f-356">按兩下新**BotObjects**指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="95d4f-357">刪除指令碼的內容，並取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="95d4f-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="95d4f-358">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="95d4f-359">第 9 章 – 建立 GazeInput 類別</span><span class="sxs-lookup"><span data-stu-id="95d4f-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="95d4f-360">下一步要建立的類別是**GazeInput**類別。</span><span class="sxs-lookup"><span data-stu-id="95d4f-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="95d4f-361">這個類別會負責：</span><span class="sxs-lookup"><span data-stu-id="95d4f-361">This class is responsible for:</span></span>

- <span data-ttu-id="95d4f-362">建立資料指標，代表*視線*播放程式。</span><span class="sxs-lookup"><span data-stu-id="95d4f-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="95d4f-363">偵測物件叫用的視線，播放程式，並保存至偵測到的物件的參考。</span><span class="sxs-lookup"><span data-stu-id="95d4f-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="95d4f-364">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-364">To create this class:</span></span> 

1.  <span data-ttu-id="95d4f-365">移至**指令碼**您先前建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="95d4f-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="95d4f-366">在資料夾中，以滑鼠右鍵按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="95d4f-367">呼叫指令碼**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="95d4f-368">按兩下新**GazeInput**指令碼，以開啟它**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="95d4f-369">插入下面這一行的類別名稱的頂端：</span><span class="sxs-lookup"><span data-stu-id="95d4f-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="95d4f-370">然後新增下列變數內**GazeInput**類別，上述**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="95d4f-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="95d4f-371">程式碼**start （)** 應該加入方法。</span><span class="sxs-lookup"><span data-stu-id="95d4f-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="95d4f-372">在類別初始化時，這將會呼叫：</span><span class="sxs-lookup"><span data-stu-id="95d4f-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="95d4f-373">實作的方法，將會具現化，並設定視線資料指標：</span><span class="sxs-lookup"><span data-stu-id="95d4f-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="95d4f-374">實作的方法，將設定從 Main Camera Raycast 並追蹤的目前具有焦點的物件。</span><span class="sxs-lookup"><span data-stu-id="95d4f-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="95d4f-375">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="95d4f-376">第 10 章 – 建立 Bot 類別</span><span class="sxs-lookup"><span data-stu-id="95d4f-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="95d4f-377">現在會呼叫您要建立指令碼**Bot**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="95d4f-378">這是您的應用程式的核心類別，它會儲存：</span><span class="sxs-lookup"><span data-stu-id="95d4f-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="95d4f-379">您的 Web 應用程式 Bot 認證</span><span class="sxs-lookup"><span data-stu-id="95d4f-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="95d4f-380">收集使用者語音命令方法</span><span class="sxs-lookup"><span data-stu-id="95d4f-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="95d4f-381">必要起始交談的 Web 應用程式 Bot 方法</span><span class="sxs-lookup"><span data-stu-id="95d4f-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="95d4f-382">為了將訊息傳送至您的 Web 應用程式 Bot 方法</span><span class="sxs-lookup"><span data-stu-id="95d4f-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="95d4f-383">若要將訊息傳送到 Bot 服務時， **SendMessageToBot()** 協同程式將會建置的活動，這是使用者所傳送的資料 Bot Framework 可辨識的物件。</span><span class="sxs-lookup"><span data-stu-id="95d4f-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="95d4f-384">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-384">To create this class:</span></span> 

1. <span data-ttu-id="95d4f-385">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="95d4f-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="95d4f-386">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="95d4f-387">指令碼命名**Bot**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="95d4f-388">按兩下新的指令碼，以使用 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="95d4f-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="95d4f-389">更新命名空間相同，如下所示，在頂端**Bot**類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="95d4f-390">內部**Bot**類別新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="95d4f-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="95d4f-391">請確定您插入您**Bot 祕密金鑰**成**botSecret**變數。</span><span class="sxs-lookup"><span data-stu-id="95d4f-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="95d4f-392">您將已記下您**Bot 祕密金鑰**在開始本課程中，在**[第 2 章](#chapter-2---create-the-azure-bot-service)，步驟 10**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="95d4f-393">程式碼**Awake()** 並**start （)** 現在需要加入。</span><span class="sxs-lookup"><span data-stu-id="95d4f-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="95d4f-394">新增語音擷取開始及結束時，會呼叫由語音程式庫的兩個處理常式。</span><span class="sxs-lookup"><span data-stu-id="95d4f-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="95d4f-395">*DictationRecognizer*將會自動停止擷取使用者的心聲，當使用者停止讀出。</span><span class="sxs-lookup"><span data-stu-id="95d4f-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="95d4f-396">下列處理常式會收集使用者的語音輸入的結果，並呼叫協同程式負責將訊息傳送至 Web 應用程式 Bot Service。</span><span class="sxs-lookup"><span data-stu-id="95d4f-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="95d4f-397">下列的協同程式會呼叫來開始交談與機器人。</span><span class="sxs-lookup"><span data-stu-id="95d4f-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="95d4f-398">您會注意到交談呼叫完成之後，它會呼叫**SendMessageToCoroutine()** 藉由傳遞一系列會設定傳送到 Bot Service 與空的訊息活動的參數。</span><span class="sxs-lookup"><span data-stu-id="95d4f-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="95d4f-399">這是為了提示 Bot 服務，才能起始對話。</span><span class="sxs-lookup"><span data-stu-id="95d4f-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="95d4f-400">下列的協同程式會呼叫來建置要傳送到 Bot 服務的活動。</span><span class="sxs-lookup"><span data-stu-id="95d4f-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="95d4f-401">下列的協同程式會呼叫來要求傳送到 Bot 服務的活動之後的回應。</span><span class="sxs-lookup"><span data-stu-id="95d4f-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="95d4f-402">要加入至這個類別的最後一個方法，才能在場景中顯示訊息：</span><span class="sxs-lookup"><span data-stu-id="95d4f-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="95d4f-403">您可能會看到在 Unity 編輯器] 主控台的 [關於遺漏錯誤**SceneOrganiser**類別。</span><span class="sxs-lookup"><span data-stu-id="95d4f-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="95d4f-404">當您將會稍後在本教學課程中建立這個類別，請忽略此訊息中。</span><span class="sxs-lookup"><span data-stu-id="95d4f-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="95d4f-405">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="95d4f-406">第 11 章 – 建立互動類別</span><span class="sxs-lookup"><span data-stu-id="95d4f-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="95d4f-407">您即將建立的類別現在稱為**互動**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="95d4f-408">這個類別用來偵測使用者的 HoloLens 點選輸入。</span><span class="sxs-lookup"><span data-stu-id="95d4f-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="95d4f-409">如果在使用者點選時查看*Bot* Bot 以及在場景中的物件已準備好接聽語音輸入、 Bot 物件會變更色彩**紅色**並開始接聽語音輸入。</span><span class="sxs-lookup"><span data-stu-id="95d4f-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="95d4f-410">這個類別繼承自**GazeInput**類別，並因此可參考**start （)** 方法，並自該類別，表示所使用的變數**基底**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="95d4f-411">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-411">To create this class:</span></span>

1.  <span data-ttu-id="95d4f-412">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="95d4f-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="95d4f-413">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="95d4f-414">指令碼命名**互動**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="95d4f-415">按兩下新的指令碼，以使用 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="95d4f-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="95d4f-416">更新命名空間和類別繼承，如下所示，頂端的相同**互動**類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="95d4f-417">內部**互動**類別新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="95d4f-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="95d4f-418">然後新增**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="95d4f-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="95d4f-419">加入處理常式，將會在使用者執行前面 HoloLens 相機點選手勢時觸發</span><span class="sxs-lookup"><span data-stu-id="95d4f-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="95d4f-420">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="95d4f-421">第 12 章-建立 SceneOrganiser 類別</span><span class="sxs-lookup"><span data-stu-id="95d4f-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="95d4f-422">在這個實驗室中所需的最後一個類別會呼叫**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="95d4f-423">這個類別會以程式設計方式設定場景，藉由將元件和指令碼新增至 Main Camera 中，並在場景中建立適當的物件。</span><span class="sxs-lookup"><span data-stu-id="95d4f-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="95d4f-424">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="95d4f-424">To create this class:</span></span>

1.  <span data-ttu-id="95d4f-425">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="95d4f-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="95d4f-426">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="95d4f-427">指令碼命名**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="95d4f-428">按兩下新的指令碼，以使用 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="95d4f-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="95d4f-429">內部**SceneOrganiser**類別新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="95d4f-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="95d4f-430">然後新增**Awake()** 並**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="95d4f-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="95d4f-431">新增下列方法，負責在場景中建立 Bot 物件，並設定參數和元件：</span><span class="sxs-lookup"><span data-stu-id="95d4f-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="95d4f-432">新增下列方法，負責建立場景，代表來自 Bot 的回應中的 UI 物件：</span><span class="sxs-lookup"><span data-stu-id="95d4f-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="95d4f-433">請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="95d4f-434">在 Unity 編輯器中，拖曳**SceneOrganiser**到 Main Camera 從指令碼 資料夾的指令碼。</span><span class="sxs-lookup"><span data-stu-id="95d4f-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="95d4f-435">場景召集人元件現在應該會出現在 Main Camera 物件，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="95d4f-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="95d4f-437">第 13 章-建置前</span><span class="sxs-lookup"><span data-stu-id="95d4f-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="95d4f-438">若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="95d4f-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="95d4f-439">這麼做之前，請確認：</span><span class="sxs-lookup"><span data-stu-id="95d4f-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="95d4f-440">中所述的所有設定[**第 4 章**](#Chapter-4-–-Set-up-the-unity-project)都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="95d4f-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="95d4f-441">指令碼**SceneOrganiser**附加至**Main Camera**物件。</span><span class="sxs-lookup"><span data-stu-id="95d4f-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="95d4f-442">在  **Bot**類別中，請確定您已插入您**Bot 祕密金鑰**成**botSecret**變數。</span><span class="sxs-lookup"><span data-stu-id="95d4f-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="95d4f-443">第 14 章-建置和側載到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="95d4f-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="95d4f-444">此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。</span><span class="sxs-lookup"><span data-stu-id="95d4f-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="95d4f-445">瀏覽至**組建設定**，**檔案 > 組建設定...**.</span><span class="sxs-lookup"><span data-stu-id="95d4f-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="95d4f-446">從**Build Settings**  視窗中，按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-446">From the **Build Settings** window, click **Build**.</span></span>

    ![從 Unity 建置應用程式](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="95d4f-448">如果您尚未，勾選**UnityC#專案**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="95d4f-449">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="95d4f-449">Click **Build**.</span></span> <span data-ttu-id="95d4f-450">將會啟動 unity**檔案總管**視窗中，您要建立，然後選取 建置到應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="95d4f-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="95d4f-451">現在，建立該資料夾並將它命名**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="95d4f-452">然後使用**應用程式**按一下 選取資料夾**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="95d4f-453">Unity 會開始建置您的專案**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="95d4f-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="95d4f-454">一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。</span><span class="sxs-lookup"><span data-stu-id="95d4f-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="95d4f-455">章 15 – 將部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="95d4f-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="95d4f-456">若要部署 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="95d4f-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="95d4f-457">您將需要您 HoloLens IP 位址 （適用於遠端部署），並以確保您 HoloLens 處於**開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="95d4f-458">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="95d4f-458">To do this:</span></span>

    1. <span data-ttu-id="95d4f-459">儘管穿著您 HoloLens，開啟**設定**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="95d4f-460">移至**網路和網際網路 > Wi-fi > 進階選項**</span><span class="sxs-lookup"><span data-stu-id="95d4f-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="95d4f-461">附註**IPv4**位址。</span><span class="sxs-lookup"><span data-stu-id="95d4f-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="95d4f-462">接下來，瀏覽回到**設定**，然後**更新與安全性 > 適用於開發人員**</span><span class="sxs-lookup"><span data-stu-id="95d4f-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="95d4f-463">設定開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="95d4f-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="95d4f-464">瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="95d4f-465">在 **方案組態**選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="95d4f-466">在 **的方案平台**，選取**x86**，**遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="95d4f-468">移至**建置 功能表**，然後按一下**部署方案**，側載您 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95d4f-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="95d4f-469">您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="95d4f-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="95d4f-470">若要將部署到擬真耳機，設定**的方案平台**來*本機電腦*，並設定**組態**至*偵錯*，使用*x86*作為**平台**。</span><span class="sxs-lookup"><span data-stu-id="95d4f-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="95d4f-471">然後部署到本機電腦，使用**建置 功能表**，並選取*部署方案*。</span><span class="sxs-lookup"><span data-stu-id="95d4f-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="95d4f-472">第 16 章 – HoloLens 上使用應用程式</span><span class="sxs-lookup"><span data-stu-id="95d4f-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="95d4f-473">一旦您已啟動的應用程式，您會看到您面前的藍色球體 Bot。</span><span class="sxs-lookup"><span data-stu-id="95d4f-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="95d4f-474">使用**點選手勢**時您會在起始交談球體 gazing。</span><span class="sxs-lookup"><span data-stu-id="95d4f-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="95d4f-475">等候啟動交談 （發生時，UI 會顯示一則訊息）。</span><span class="sxs-lookup"><span data-stu-id="95d4f-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="95d4f-476">一旦您入門的訊息接收的 Bot 時，點選一次 Bot 讓它將會變成紅色，並開始接聽您的聲音。</span><span class="sxs-lookup"><span data-stu-id="95d4f-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="95d4f-477">當您停止交談時，您的應用程式會將您的訊息傳送到 Bot 和您會立即收到的回應，將會顯示在 UI 中。</span><span class="sxs-lookup"><span data-stu-id="95d4f-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="95d4f-478">重複程序，將多個訊息傳送至您的 Bot （您必須點選每個您想要傳送訊息的時間）。</span><span class="sxs-lookup"><span data-stu-id="95d4f-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="95d4f-479">這項交談會示範如何 Bot 可以保留資訊 （您的名稱），同時也提供已知的資訊 （例如所配備的項目）。</span><span class="sxs-lookup"><span data-stu-id="95d4f-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="95d4f-480">要求 Bot 一些問題：</span><span class="sxs-lookup"><span data-stu-id="95d4f-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="95d4f-481">您已完成的 Web 應用程式 Bot (v4) 應用程式</span><span class="sxs-lookup"><span data-stu-id="95d4f-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="95d4f-482">恭喜，您建置會利用 Azure Web 應用程式 Bot、 Microsoft Bot Framework v4 mixed 的 reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95d4f-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![最終產品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="95d4f-484">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="95d4f-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="95d4f-485">練習 1</span><span class="sxs-lookup"><span data-stu-id="95d4f-485">Exercise 1</span></span>

<span data-ttu-id="95d4f-486">在這個實驗室中的交談結構是非常基本。</span><span class="sxs-lookup"><span data-stu-id="95d4f-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="95d4f-487">您可以使用 Microsoft LUIS，自然語言了解功能賦予機器人。</span><span class="sxs-lookup"><span data-stu-id="95d4f-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="95d4f-488">練習 2</span><span class="sxs-lookup"><span data-stu-id="95d4f-488">Exercise 2</span></span>

<span data-ttu-id="95d4f-489">此範例不包含終止的交談，並重新啟動一個新。</span><span class="sxs-lookup"><span data-stu-id="95d4f-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="95d4f-490">若要讓的 Bot 功能完成，請嘗試實作交談的結束。</span><span class="sxs-lookup"><span data-stu-id="95d4f-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
