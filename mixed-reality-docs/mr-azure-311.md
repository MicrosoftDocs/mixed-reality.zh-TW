---
title: MR 和 Azure 311-Microsoft Graph
description: 完成這個課程來了解如何使用 Microsoft Graph，並連接驅動生產力，在混合的實境應用程式中的資料。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 microsoft graph、 hololens、 沉浸式 vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694530"
---
>[!NOTE]
><span data-ttu-id="23adb-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="23adb-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="23adb-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="23adb-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="23adb-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="23adb-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="23adb-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="23adb-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="23adb-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="23adb-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="23adb-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="23adb-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="23adb-110">MR 和 Azure 311-Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="23adb-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="23adb-111">在此課程中，您將了解如何使用*Microsoft Graph*登入您使用安全的驗證，在混合的實境應用程式中的 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="23adb-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="23adb-112">您接著擷取並顯示應用程式介面中的已排程的會議。</span><span class="sxs-lookup"><span data-stu-id="23adb-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="23adb-113">*Microsoft Graph*是一組設計來啟用對許多 Microsoft 服務存取的 Api。</span><span class="sxs-lookup"><span data-stu-id="23adb-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="23adb-114">Microsoft 說明 Microsoft Graph 為連線的關聯性，資源的矩陣，這表示它可讓應用程式存取各式各樣的已連線的使用者資料。</span><span class="sxs-lookup"><span data-stu-id="23adb-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="23adb-115">如需詳細資訊，請瀏覽[Microsoft Graph 頁面](https://developer.microsoft.com/graph)。</span><span class="sxs-lookup"><span data-stu-id="23adb-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="23adb-116">開發將包含建立使用者以注視，然後點選 球體，將會提示使用者安全地登入 Microsoft 帳戶的指示，應用程式。</span><span class="sxs-lookup"><span data-stu-id="23adb-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="23adb-117">一旦登入其帳戶，使用者將能夠看到一份排程一天的會議。</span><span class="sxs-lookup"><span data-stu-id="23adb-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="23adb-118">完成本課程之後，您會有混合的實境 HoloLens 應用程式，可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="23adb-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="23adb-119">點選 使用點選手勢，將會提示使用者登入 Microsoft 帳戶 （移出登入，然後再移回至應用程式的應用程式） 的物件。</span><span class="sxs-lookup"><span data-stu-id="23adb-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="23adb-120">檢視排程一天的會議的清單。</span><span class="sxs-lookup"><span data-stu-id="23adb-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="23adb-121">在您的應用程式，則您對於如何將整合結果進行設計。</span><span class="sxs-lookup"><span data-stu-id="23adb-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="23adb-122">本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="23adb-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="23adb-123">它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。</span><span class="sxs-lookup"><span data-stu-id="23adb-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="23adb-124">裝置支援</span><span class="sxs-lookup"><span data-stu-id="23adb-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="23adb-125">課程</span><span class="sxs-lookup"><span data-stu-id="23adb-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="23adb-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="23adb-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="23adb-127"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="23adb-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="23adb-128">MR 和 Azure 311:Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="23adb-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="23adb-129">✔️</span><span class="sxs-lookup"><span data-stu-id="23adb-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="23adb-130">先決條件</span><span class="sxs-lookup"><span data-stu-id="23adb-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="23adb-131">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="23adb-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="23adb-132">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。</span><span class="sxs-lookup"><span data-stu-id="23adb-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="23adb-133">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。</span><span class="sxs-lookup"><span data-stu-id="23adb-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="23adb-134">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="23adb-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="23adb-135">開發電腦</span><span class="sxs-lookup"><span data-stu-id="23adb-135">A development PC</span></span>
- [<span data-ttu-id="23adb-136">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="23adb-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="23adb-137">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="23adb-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="23adb-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="23adb-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="23adb-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="23adb-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="23adb-140">A [Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="23adb-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="23adb-141">Azure 的安裝程式和 Microsoft Graph 資料擷取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="23adb-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="23adb-142">有效**的 Microsoft 帳戶**（個人或公司/學校）</span><span class="sxs-lookup"><span data-stu-id="23adb-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="23adb-143">一些會議排定為目前日期，使用相同的 Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="23adb-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="23adb-144">開始之前</span><span class="sxs-lookup"><span data-stu-id="23adb-144">Before you start</span></span>

1.  <span data-ttu-id="23adb-145">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="23adb-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="23adb-146">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="23adb-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="23adb-147">如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="23adb-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="23adb-148">它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。</span><span class="sxs-lookup"><span data-stu-id="23adb-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="23adb-149">校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="23adb-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="23adb-150">如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="23adb-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="23adb-151">第 1 層應用程式註冊入口網站中建立您的應用程式</span><span class="sxs-lookup"><span data-stu-id="23adb-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="23adb-152">一開始，您必須建立並註冊您的應用程式**應用程式註冊入口網站**。</span><span class="sxs-lookup"><span data-stu-id="23adb-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="23adb-153">您也會在這一章中找到服務金鑰，可讓您對進行呼叫*Microsoft Graph*來存取您帳戶的內容。</span><span class="sxs-lookup"><span data-stu-id="23adb-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="23adb-154">瀏覽至[Microsoft 應用程式註冊入口網站](https://apps.dev.microsoft.com)並使用您的 Microsoft 帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="23adb-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="23adb-155">一旦您已登入，您將會重新導向至**應用程式註冊入口網站**。</span><span class="sxs-lookup"><span data-stu-id="23adb-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="23adb-156">在 **我的應用程式**區段中，按一下按鈕**新增應用程式**。</span><span class="sxs-lookup"><span data-stu-id="23adb-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="23adb-157">**應用程式註冊入口網站**可以看起來不同，取決於是否您先前用過*Microsoft Graph*。</span><span class="sxs-lookup"><span data-stu-id="23adb-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="23adb-158">以下螢幕擷取畫面顯示這些不同的版本。</span><span class="sxs-lookup"><span data-stu-id="23adb-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="23adb-159">針對您的應用程式，然後按一下 新增名稱**建立**。</span><span class="sxs-lookup"><span data-stu-id="23adb-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="23adb-160">一旦建立應用程式，您將重新導向到的應用程式的主頁面。</span><span class="sxs-lookup"><span data-stu-id="23adb-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="23adb-161">複製**應用程式識別碼**請務必記下此值為安全的地方，您將使用它很快就在您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="23adb-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="23adb-162">在 **平台**區段中，請確定**原生應用程式**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="23adb-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="23adb-163">如果*未*上按一下**新增平台**，然後選取**原生應用程式**。</span><span class="sxs-lookup"><span data-stu-id="23adb-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="23adb-164">在相同的頁面和稱為區段，向下捲動**Microsoft Graph 權限**您必須新增應用程式的其他權限。</span><span class="sxs-lookup"><span data-stu-id="23adb-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="23adb-165">按一下 **新增**旁**委派的權限**。</span><span class="sxs-lookup"><span data-stu-id="23adb-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="23adb-166">由於您希望您的應用程式存取使用者的行事曆，核取方塊稱為**Calendars.Read**然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="23adb-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="23adb-167">捲動到底部，按一下**儲存** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="23adb-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="23adb-168">會確認您的儲存，以及您可以登出**應用程式註冊入口網站**。</span><span class="sxs-lookup"><span data-stu-id="23adb-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="23adb-169">第 2 章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="23adb-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="23adb-170">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="23adb-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="23adb-171">開啟*Unity*然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="23adb-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="23adb-172">您需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="23adb-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="23adb-173">插入**MSGraphMR**。</span><span class="sxs-lookup"><span data-stu-id="23adb-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="23adb-174">請確定已設定的專案範本**3D**。</span><span class="sxs-lookup"><span data-stu-id="23adb-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="23adb-175">設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="23adb-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="23adb-176">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="23adb-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="23adb-177">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="23adb-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="23adb-178">移至**編輯** > **喜好設定**並從新的視窗，然後瀏覽至**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="23adb-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="23adb-179">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="23adb-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="23adb-180">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="23adb-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="23adb-181">移至**檔案** > **組建設定**，然後選取**通用 Windows 平台**，然後按一下**切換平台**按鈕，以套用您的選擇。</span><span class="sxs-lookup"><span data-stu-id="23adb-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="23adb-182">當您依然在**檔案** > **組建設定**，請確定：</span><span class="sxs-lookup"><span data-stu-id="23adb-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="23adb-183">**裝置為目標**設為**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="23adb-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="23adb-184">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="23adb-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="23adb-185">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="23adb-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="23adb-186">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="23adb-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="23adb-187">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="23adb-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="23adb-188">儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="23adb-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="23adb-189">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="23adb-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="23adb-190">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="23adb-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="23adb-191">這與任何未來、 場景中建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="23adb-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="23adb-192">選取 **新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="23adb-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="23adb-193">開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中輸入**MR_ComputerVisionScene**，然後按一下**儲存**.</span><span class="sxs-lookup"><span data-stu-id="23adb-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="23adb-194">請注意，您必須先儲存您的 Unity 場景中*資產*資料夾，因為它們必須是與 Unity 專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="23adb-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="23adb-195">建立場景資料夾 （和其他類似的資料夾） 是建構的 Unity 專案的典型方式。</span><span class="sxs-lookup"><span data-stu-id="23adb-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="23adb-196">剩餘的設定，*組建設定*，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="23adb-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="23adb-197">中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。</span><span class="sxs-lookup"><span data-stu-id="23adb-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="23adb-198">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="23adb-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="23adb-199">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="23adb-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="23adb-200">**指令碼** **執行階段版本**應該**實驗性**（.NET 4.6 對等），這會觸發程序需要重新啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="23adb-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="23adb-201">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="23adb-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="23adb-202">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="23adb-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="23adb-203">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="23adb-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="23adb-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="23adb-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="23adb-205">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，檢查**虛擬實境支援**，請確定**Windows Mixed RealitySDK**加入。</span><span class="sxs-lookup"><span data-stu-id="23adb-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="23adb-206">回到*Build Settings*， *UnityC#專案*不再呈現灰色，要檢查這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="23adb-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="23adb-207">關閉*組建設定*視窗。</span><span class="sxs-lookup"><span data-stu-id="23adb-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="23adb-208">儲存您的場景和專案 (**檔案** > **儲存場景檔案** > **儲存專案**)。</span><span class="sxs-lookup"><span data-stu-id="23adb-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="23adb-209">第 3 章-在 Unity 中的匯入程式庫</span><span class="sxs-lookup"><span data-stu-id="23adb-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23adb-210">如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)，它匯入到您的專案做為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 5 章](#chapter-5---create-meetingsui-class)。</span><span class="sxs-lookup"><span data-stu-id="23adb-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="23adb-211">若要使用*Microsoft Graph*您需要進行的 Unity 中使用的**Microsoft.Identity.Client** DLL。</span><span class="sxs-lookup"><span data-stu-id="23adb-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="23adb-212">您可使用 Microsoft Graph SDK，不過，它就需要加入的 NuGet 套件之後建置 Unity 專案 （亦即編輯專案建置後）。</span><span class="sxs-lookup"><span data-stu-id="23adb-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="23adb-213">會被視為直接將 Unity 匯入必要的 Dll 的工作變得更容易。</span><span class="sxs-lookup"><span data-stu-id="23adb-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="23adb-214">這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。</span><span class="sxs-lookup"><span data-stu-id="23adb-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="23adb-215">這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。</span><span class="sxs-lookup"><span data-stu-id="23adb-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="23adb-216">若要匯入*Microsoft Graph*到您自己的專案[MSGraph_LabPlugins.zip 檔案下載](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="23adb-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="23adb-217">此套件已建立版本測試過的程式庫使用。</span><span class="sxs-lookup"><span data-stu-id="23adb-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="23adb-218">如果您想要深入了解如何將自訂 Dll 新增至您的 Unity 專案[請依循下列連結](https://docs.unity3d.com/Manual/UsingDLL.html)。</span><span class="sxs-lookup"><span data-stu-id="23adb-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="23adb-219">若要匯入套件：</span><span class="sxs-lookup"><span data-stu-id="23adb-219">To import the package:</span></span>

1.  <span data-ttu-id="23adb-220">使用將 Unity 套件新增至 Unity**資產** > **匯入封裝** > **自訂封裝**功能表選項。</span><span class="sxs-lookup"><span data-stu-id="23adb-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="23adb-221">選取您剛才下載的封裝。</span><span class="sxs-lookup"><span data-stu-id="23adb-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="23adb-222">在 **匯入 Unity 封裝**方塊會顯示。 請確認所有項目底下 （而且包括）**外掛程式**已選取。</span><span class="sxs-lookup"><span data-stu-id="23adb-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="23adb-223">按一下 **匯入**按鈕以新增至您的專案項目。</span><span class="sxs-lookup"><span data-stu-id="23adb-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="23adb-224">移至**MSGraph**下的資料夾**外掛程式**中*專案] 面板*，然後選取 [外掛程式呼叫**Microsoft.Identity.Client**。</span><span class="sxs-lookup"><span data-stu-id="23adb-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="23adb-225">具有*外掛程式*選取，請確認**任何平台**未核取，則確定**WSAPlayer**也是未選取，然後按一下 **套用**.</span><span class="sxs-lookup"><span data-stu-id="23adb-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="23adb-226">這只是要確認已正確設定檔案。</span><span class="sxs-lookup"><span data-stu-id="23adb-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="23adb-227">標示這些外掛程式會設定它們僅適用於在 Unity 編輯器中。</span><span class="sxs-lookup"><span data-stu-id="23adb-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="23adb-228">有一組不同的專案會匯出從 Unity 做為通用 Windows 應用程式後要使用 WSA 資料夾中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="23adb-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="23adb-229">接下來，您必須開啟**WSA**資料夾內**MSGraph**資料夾。</span><span class="sxs-lookup"><span data-stu-id="23adb-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="23adb-230">您會看到您剛才設定的相同檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="23adb-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="23adb-231">選取檔案，然後在偵測器：</span><span class="sxs-lookup"><span data-stu-id="23adb-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="23adb-232">請確認**任何平台**是**取消核取**，且**只** **WSAPlayer**是**檢查**。</span><span class="sxs-lookup"><span data-stu-id="23adb-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="23adb-233">請確定**SDK**設為**UWP**，並**指令碼的後端**設為**Dot Net**</span><span class="sxs-lookup"><span data-stu-id="23adb-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="23adb-234">請確認**不會處理**是**檢查**。</span><span class="sxs-lookup"><span data-stu-id="23adb-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="23adb-235">按一下 **[套用]** 。</span><span class="sxs-lookup"><span data-stu-id="23adb-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="23adb-236">第 4 章-觀景窗設定</span><span class="sxs-lookup"><span data-stu-id="23adb-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="23adb-237">在這一章期間您將設定場景的 Main Camera:</span><span class="sxs-lookup"><span data-stu-id="23adb-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="23adb-238">在 *階層面板*，選取**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="23adb-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="23adb-239">選取之後，您將能夠看到所有的元件**Main Camera**中*Inspector*面板。</span><span class="sxs-lookup"><span data-stu-id="23adb-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="23adb-240">**相機物件**必須命名為**Main Camera** （請注意拼字 ！）</span><span class="sxs-lookup"><span data-stu-id="23adb-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="23adb-241">Main Camera**標記**必須設為**MainCamera** （請注意拼字 ！）</span><span class="sxs-lookup"><span data-stu-id="23adb-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="23adb-242">請確定**轉換的位置**設定為**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="23adb-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="23adb-243">設定**清除旗標**到**純色**</span><span class="sxs-lookup"><span data-stu-id="23adb-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="23adb-244">設定**背景色彩**要相機元件**黑色，0 的 Alpha** **(十六進位的程式碼: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="23adb-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="23adb-245">中的最終物件結構*階層面板*應該類似下面的影像中所示：</span><span class="sxs-lookup"><span data-stu-id="23adb-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="23adb-246">第 5 章-建立 MeetingsUI 類別</span><span class="sxs-lookup"><span data-stu-id="23adb-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="23adb-247">您必須建立第一個指令碼**MeetingsUI**，它會負責裝載，並填入 （歡迎訊息、 指示和會議詳細資料） 的應用程式的 UI。</span><span class="sxs-lookup"><span data-stu-id="23adb-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="23adb-248">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="23adb-248">To create this class:</span></span>

1.  <span data-ttu-id="23adb-249">以滑鼠右鍵按一下**資產**中的資料夾 *[專案] 面板*，然後選取**建立** > **資料夾**。</span><span class="sxs-lookup"><span data-stu-id="23adb-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="23adb-250">將資料夾命名**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="23adb-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="23adb-251">開啟**指令碼**資料夾，在該資料夾中，按一下滑鼠右鍵，**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="23adb-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="23adb-252">指令碼命名**MeetingsUI。**</span><span class="sxs-lookup"><span data-stu-id="23adb-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="23adb-253">按兩下新**MeetingsUI**指令碼，以開啟它*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="23adb-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="23adb-254">插入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="23adb-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="23adb-255">類別內插入下列變數：</span><span class="sxs-lookup"><span data-stu-id="23adb-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="23adb-256">然後取代**start （)** 方法，並新增**Awake()** 方法。</span><span class="sxs-lookup"><span data-stu-id="23adb-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="23adb-257">在類別初始化時，這些將會呼叫：</span><span class="sxs-lookup"><span data-stu-id="23adb-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="23adb-258">加入負責建立方法*會議 UI*並填入目前的會議時要求：</span><span class="sxs-lookup"><span data-stu-id="23adb-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="23adb-259">**刪除** **update （)** 方法，以及**儲存您的變更**傳回給 Unity 之前的 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="23adb-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="23adb-260">章節 6-建立圖形類別</span><span class="sxs-lookup"><span data-stu-id="23adb-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="23adb-261">下一步 以建立指令碼**Graph**指令碼。</span><span class="sxs-lookup"><span data-stu-id="23adb-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="23adb-262">此指令碼是負責驗證使用者，並擷取目前的日期，從使用者的行事曆排定的會議的呼叫。</span><span class="sxs-lookup"><span data-stu-id="23adb-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="23adb-263">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="23adb-263">To create this class:</span></span>

1.  <span data-ttu-id="23adb-264">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="23adb-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="23adb-265">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="23adb-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="23adb-266">指令碼命名**Graph**。</span><span class="sxs-lookup"><span data-stu-id="23adb-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="23adb-267">按兩下要使用 Visual Studio 中開啟它的指令碼。</span><span class="sxs-lookup"><span data-stu-id="23adb-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="23adb-268">插入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="23adb-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="23adb-269">您會注意到此指令碼中的程式碼的部分包裝著[先行編譯指示詞](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)，這是為了避免與程式庫的問題，當建置 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="23adb-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="23adb-270">刪除**start （)** 並**update （)** 方法，因為它們不會使用。</span><span class="sxs-lookup"><span data-stu-id="23adb-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="23adb-271">Outside **Graph**類別中，插入所需的還原序列化 JSON 物件，表示每日排定的會議的下列物件：</span><span class="sxs-lookup"><span data-stu-id="23adb-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="23adb-272">內部**Graph**類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="23adb-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="23adb-273">變更 **appId** 值，成為 **應用程式識別碼** 您記下在 **[第 1 章](#chapter-1---create-your-app-in-the-application-registration-portal)，步驟 4** 。</span><span class="sxs-lookup"><span data-stu-id="23adb-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="23adb-274">這個值應該是顯示在相同**應用程式註冊入口網站，** 在您的應用程式註冊頁面中。</span><span class="sxs-lookup"><span data-stu-id="23adb-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="23adb-275">內**Graph**類別中，將方法加入**SignInAsync()** 並**AquireTokenAsync()** ，，會提示使用者插入的登入認證。</span><span class="sxs-lookup"><span data-stu-id="23adb-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="23adb-276">新增下列兩種方法：</span><span class="sxs-lookup"><span data-stu-id="23adb-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="23adb-277">**BuildTodayCalendarEndpoint()** ，哪些組建會指定日期和時間範圍內，已排程的會議中擷取的 URI。</span><span class="sxs-lookup"><span data-stu-id="23adb-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="23adb-278">**ListMeetingsAsync()** ，會要求從已排程的會議*Microsoft Graph*。</span><span class="sxs-lookup"><span data-stu-id="23adb-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="23adb-279">您現在已完成**Graph**指令碼。</span><span class="sxs-lookup"><span data-stu-id="23adb-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="23adb-280">**儲存您的變更**傳回給 Unity 之前的 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="23adb-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="23adb-281">第 7-建立 GazeInput 指令碼</span><span class="sxs-lookup"><span data-stu-id="23adb-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="23adb-282">您現在會建立**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="23adb-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="23adb-283">這個類別會處理並追蹤使用者的視線，使用**Raycast**來自**Main Camera**，向前投影。</span><span class="sxs-lookup"><span data-stu-id="23adb-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="23adb-284">若要建立指令碼：</span><span class="sxs-lookup"><span data-stu-id="23adb-284">To create the script:</span></span>

1.  <span data-ttu-id="23adb-285">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="23adb-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="23adb-286">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="23adb-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="23adb-287">指令碼命名**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="23adb-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="23adb-288">按兩下要使用 Visual Studio 中開啟它的指令碼。</span><span class="sxs-lookup"><span data-stu-id="23adb-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="23adb-289">變更命名空間程式碼，以符合下面其中一個，以及新增 ' **\[System.Serializable\]** ' 上述標記您**GazeInput**類別，以便它可以序列化：</span><span class="sxs-lookup"><span data-stu-id="23adb-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="23adb-290">內部**GazeInput**類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="23adb-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

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

6.  <span data-ttu-id="23adb-291">新增**CreateCursor()** 方法來建立場景中的 HoloLens 資料指標，並呼叫方法，從**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="23adb-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="23adb-292">下列方法啟用視線 Raycast 和追蹤的焦點的物件。</span><span class="sxs-lookup"><span data-stu-id="23adb-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

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
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
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
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="23adb-293">**儲存您的變更**傳回給 Unity 之前的 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="23adb-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="23adb-294">第 8-建立互動類別</span><span class="sxs-lookup"><span data-stu-id="23adb-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="23adb-295">您現在必須建立**互動**指令碼，也就是負責：</span><span class="sxs-lookup"><span data-stu-id="23adb-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="23adb-296">處理**點選**互動並**相機視線**，這可讓使用者互動的記錄檔中在場景中的 「 按鈕 」。</span><span class="sxs-lookup"><span data-stu-id="23adb-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="23adb-297">建立記錄檔中的使用者互動，場景中的 「 按鈕 」 物件。</span><span class="sxs-lookup"><span data-stu-id="23adb-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="23adb-298">若要建立指令碼：</span><span class="sxs-lookup"><span data-stu-id="23adb-298">To create the script:</span></span>

1.  <span data-ttu-id="23adb-299">按兩下**指令碼**資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="23adb-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="23adb-300">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="23adb-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="23adb-301">指令碼命名**互動**。</span><span class="sxs-lookup"><span data-stu-id="23adb-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="23adb-302">按兩下要使用 Visual Studio 中開啟它的指令碼。</span><span class="sxs-lookup"><span data-stu-id="23adb-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="23adb-303">插入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="23adb-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="23adb-304">變更的繼承**互動**從類別*MonoBehaviour*來**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="23adb-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="23adb-305">~~公用類別互動：MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="23adb-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="23adb-306">內部**互動**類別插入下列變數：</span><span class="sxs-lookup"><span data-stu-id="23adb-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="23adb-307">取代**啟動**方法; 請注意，它會覆寫方法，它會呼叫的 'base' 視線類別方法。</span><span class="sxs-lookup"><span data-stu-id="23adb-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="23adb-308">**Start （)** 類別初始化時，輸入辨識向註冊，並建立登入將會呼叫 *按鈕* 場景中：</span><span class="sxs-lookup"><span data-stu-id="23adb-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="23adb-309">新增 **CreateSignInButton()** 方法，它會具現化的登入 *按鈕* 場景中並設定其屬性：</span><span class="sxs-lookup"><span data-stu-id="23adb-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="23adb-310">新增**GestureRecognizer_Tapped()** 方法，這是回應*點選*使用者事件。</span><span class="sxs-lookup"><span data-stu-id="23adb-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="23adb-311">**刪除** **update （)** 方法，然後**儲存您的變更**傳回給 Unity 之前的 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="23adb-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="23adb-312">第 9 章-設定指令碼參考</span><span class="sxs-lookup"><span data-stu-id="23adb-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="23adb-313">您必須將放在本章**互動**拖曳至指令碼**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="23adb-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="23adb-314">該指令碼會接著處理放置其他指令碼能所需的位置。</span><span class="sxs-lookup"><span data-stu-id="23adb-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="23adb-315">從**指令碼**資料夾中的 *[專案] 面板*，將指令碼**互動**至**Main Camera**物件，請參閱下圖。</span><span class="sxs-lookup"><span data-stu-id="23adb-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="23adb-316">第 10 章-設定標記</span><span class="sxs-lookup"><span data-stu-id="23adb-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="23adb-317">處理視線的程式碼，將使用的標記**SignInButton**若要識別哪些物件使用者將互動登入*Microsoft Graph*。</span><span class="sxs-lookup"><span data-stu-id="23adb-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="23adb-318">若要建立的標記：</span><span class="sxs-lookup"><span data-stu-id="23adb-318">To create the Tag:</span></span>

1.  <span data-ttu-id="23adb-319">在 Unity 編輯器中按一下**Main Camera**中*階層面板*。</span><span class="sxs-lookup"><span data-stu-id="23adb-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="23adb-320">在 [*偵測器] 面板*上按一下**MainCamera** *標記*開啟下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="23adb-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="23adb-321">按一下**新增標記...**</span><span class="sxs-lookup"><span data-stu-id="23adb-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="23adb-322">按一下 [ **+** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="23adb-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="23adb-323">寫入的標記名稱，作為**SignInButton**並按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="23adb-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="23adb-324">第 11 章-建置 Unity 專案至 UWP</span><span class="sxs-lookup"><span data-stu-id="23adb-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="23adb-325">此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。</span><span class="sxs-lookup"><span data-stu-id="23adb-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="23adb-326">瀏覽至 *組建設定* (**檔案*>*建置設定**)。</span><span class="sxs-lookup"><span data-stu-id="23adb-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="23adb-327">如果您尚未，勾選**Unity C\#專案**。</span><span class="sxs-lookup"><span data-stu-id="23adb-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="23adb-328">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="23adb-328">Click **Build**.</span></span> <span data-ttu-id="23adb-329">將會啟動 unity**檔案總管**視窗中，您要建立，然後選取 建置到應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="23adb-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="23adb-330">現在，建立該資料夾並將它命名**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="23adb-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="23adb-331">然後使用**應用程式**按一下 選取資料夾**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="23adb-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="23adb-332">Unity 會開始建置您的專案**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="23adb-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="23adb-333">一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。</span><span class="sxs-lookup"><span data-stu-id="23adb-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="23adb-334">第 12-部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="23adb-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="23adb-335">若要部署 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="23adb-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="23adb-336">您將需要您 HoloLens IP 位址 （適用於遠端部署），並以確保您 HoloLens 處於**開發人員模式。**</span><span class="sxs-lookup"><span data-stu-id="23adb-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="23adb-337">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="23adb-337">To do this:</span></span>

    1.  <span data-ttu-id="23adb-338">儘管穿著您 HoloLens，開啟**設定**。</span><span class="sxs-lookup"><span data-stu-id="23adb-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="23adb-339">移至**網路和網際網路** > **Wi-fi** > **進階選項**</span><span class="sxs-lookup"><span data-stu-id="23adb-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="23adb-340">附註**IPv4**位址。</span><span class="sxs-lookup"><span data-stu-id="23adb-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="23adb-341">接下來，瀏覽回到**設定**，然後**更新與安全性** > **適用於開發人員**</span><span class="sxs-lookup"><span data-stu-id="23adb-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="23adb-342">設定**上的開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="23adb-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="23adb-343">瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="23adb-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="23adb-344">在 **方案組態**選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="23adb-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="23adb-345">在 **的方案平台**，選取**x86，遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="23adb-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="23adb-346">系統會提示您插入**IP 位址**的遠端裝置 (HoloLens，在此情況下，記下)。</span><span class="sxs-lookup"><span data-stu-id="23adb-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="23adb-347">移至**建置**功能表，然後按一下 **部署方案**側載您 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="23adb-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="23adb-348">您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="23adb-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="23adb-349">您的 Microsoft Graph HoloLens 應用程式</span><span class="sxs-lookup"><span data-stu-id="23adb-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="23adb-350">恭喜，您所建立的混合的實境應用程式，利用 Microsoft Graph，來讀取和顯示使用者的行事曆資料。</span><span class="sxs-lookup"><span data-stu-id="23adb-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="23adb-351">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="23adb-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="23adb-352">練習 1</span><span class="sxs-lookup"><span data-stu-id="23adb-352">Exercise 1</span></span>

<span data-ttu-id="23adb-353">使用 Microsoft Graph，以顯示使用者的其他資訊</span><span class="sxs-lookup"><span data-stu-id="23adb-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="23adb-354">使用者電子郵件 / 電話號碼] / [設定檔圖片</span><span class="sxs-lookup"><span data-stu-id="23adb-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="23adb-355">練習 1</span><span class="sxs-lookup"><span data-stu-id="23adb-355">Exercise 1</span></span>

<span data-ttu-id="23adb-356">實作語音控制瀏覽 Microsoft 的圖形使用者介面。</span><span class="sxs-lookup"><span data-stu-id="23adb-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
