---
title: MR 和 Azure 311-Microsoft Graph
description: 完成此課程, 以瞭解如何運用 Microsoft Graph, 並連接到在混合現實應用程式中驅動生產力的資料。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 學術, unity, 教學課程, api, microsoft graph, hololens, 沉浸, vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694530"
---
>[!NOTE]
><span data-ttu-id="e4f0f-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e4f0f-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e4f0f-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e4f0f-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e4f0f-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e4f0f-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="e4f0f-110">MR 和 Azure 311-Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="e4f0f-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="e4f0f-111">在此課程中, 您將瞭解如何使用*Microsoft Graph* , 以在混合現實應用程式中使用安全驗證來登入您的 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="e4f0f-112">接著, 您將會在應用程式介面中抓取和顯示已排程的會議。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="e4f0f-113">*Microsoft Graph*是一組 api, 其設計目的是要讓您能夠存取許多 Microsoft 服務。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="e4f0f-114">Microsoft 將 Microsoft Graph 描述為以關聯性連線的資源矩陣, 這表示它允許應用程式存取各種已連線的使用者資料。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="e4f0f-115">如需詳細資訊, 請造訪[Microsoft Graph 頁面](https://developer.microsoft.com/graph)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="e4f0f-116">開發過程中將會建立應用程式, 其中會指示使用者注視並按一下球體, 這會提示使用者安全地登入 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="e4f0f-117">登入其帳戶之後, 使用者就能夠看到一天排定的會議清單。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="e4f0f-118">完成此課程之後, 您將擁有一個混合現實 HoloLens 應用程式, 其將能夠執行下列作業:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="e4f0f-119">使用 [點按手勢], 並按一下物件, 這會提示使用者登入 Microsoft 帳戶 (移出應用程式以登入, 然後再次回到應用程式)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="e4f0f-120">查看每天排定的會議清單。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="e4f0f-121">在您的應用程式中, 您可以決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="e4f0f-122">本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="e4f0f-123">您的工作是使用您從這個課程取得的知識, 來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="e4f0f-124">裝置支援</span><span class="sxs-lookup"><span data-stu-id="e4f0f-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e4f0f-125">粗</span><span class="sxs-lookup"><span data-stu-id="e4f0f-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e4f0f-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e4f0f-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e4f0f-127"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="e4f0f-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e4f0f-128">MR 和 Azure 311:Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="e4f0f-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="e4f0f-129">✔️</span><span class="sxs-lookup"><span data-stu-id="e4f0f-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="e4f0f-130">必要條件</span><span class="sxs-lookup"><span data-stu-id="e4f0f-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="e4f0f-131">本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="e4f0f-132">也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (2018 年7月)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="e4f0f-133">您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="e4f0f-134">在此課程中, 我們建議您採用下列硬體和軟體:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="e4f0f-135">開發電腦</span><span class="sxs-lookup"><span data-stu-id="e4f0f-135">A development PC</span></span>
- [<span data-ttu-id="e4f0f-136">已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="e4f0f-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e4f0f-137">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="e4f0f-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e4f0f-138">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="e4f0f-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e4f0f-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e4f0f-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="e4f0f-140">已啟用開發人員模式的[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="e4f0f-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="e4f0f-141">適用于 Azure 設定和 Microsoft Graph 資料抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="e4f0f-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="e4f0f-142">有效的**Microsoft 帳戶**(個人或公司/學校)</span><span class="sxs-lookup"><span data-stu-id="e4f0f-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="e4f0f-143">使用相同的 Microsoft 帳戶排定當天的幾個會議</span><span class="sxs-lookup"><span data-stu-id="e4f0f-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="e4f0f-144">開始之前</span><span class="sxs-lookup"><span data-stu-id="e4f0f-144">Before you start</span></span>

1.  <span data-ttu-id="e4f0f-145">為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="e4f0f-146">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="e4f0f-147">如果您需要支援設定 HoloLens,[請務必造訪 hololens 安裝程式一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="e4f0f-148">開始開發新的 HoloLens 應用程式時, 最好先執行校正和感應器微調 (有時候它有助於為每個使用者執行這些工作)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="e4f0f-149">如需校正的說明, 請遵循此[HoloLens 校正文章的連結](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="e4f0f-150">如需感應器微調的說明, 請遵循此[HoloLens 感應器微調文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="e4f0f-151">第1章-在應用程式註冊入口網站中建立您的應用程式</span><span class="sxs-lookup"><span data-stu-id="e4f0f-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="e4f0f-152">一開始, 您必須在**應用程式註冊入口網站**中建立並註冊您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="e4f0f-153">在本章中, 您也會找到可讓您呼叫*Microsoft Graph*以存取帳戶內容的服務金鑰。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="e4f0f-154">流覽至[Microsoft 應用程式註冊入口網站](https://apps.dev.microsoft.com), 並使用您的 Microsoft 帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="e4f0f-155">登入之後, 系統會將您重新導向至**應用程式註冊入口網站**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="e4f0f-156">在 [**我的應用程式**] 區段中, 按一下 [**新增應用程式**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="e4f0f-157">**應用程式註冊入口網站**看起來可能會不同, 取決於您先前是否使用過*Microsoft Graph*。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="e4f0f-158">下列螢幕擷取畫面顯示這些不同的版本。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="e4f0f-159">新增應用程式的名稱, 然後按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="e4f0f-160">建立應用程式之後, 系統會將您重新導向至應用程式的主頁面。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="e4f0f-161">複製 [**應用程式識別碼**], 並確定在安全的地方記下此值, 您很快就會在程式碼中使用它。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="e4f0f-162">在 [**平臺**] 區段中, 確認已顯示 [**原生應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="e4f0f-163">如果*沒有*, 請按一下 [**新增平臺**], 然後選取 [**原生應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="e4f0f-164">在同一個頁面中, 或在稱為**Microsoft Graph 許可權**的區段中向下滾動, 您必須為應用程式新增額外的許可權。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="e4f0f-165">按一下 [**委派的許可權**] 旁的 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="e4f0f-166">因為您想要讓應用程式存取使用者的行事曆, 請核取 [行事曆] 方塊 **。閱讀**, 然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="e4f0f-167">向下流覽至底部, 然後按一下 [**儲存**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="e4f0f-168">將會確認您的儲存, 並可從**應用程式註冊入口網站**登出。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="e4f0f-169">第2章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="e4f0f-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="e4f0f-170">以下是使用混合現實進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="e4f0f-171">開啟*Unity* , 然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="e4f0f-172">您必須提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="e4f0f-173">插入**MSGraphMR**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="e4f0f-174">請確定專案範本已設定為 [ **3d**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="e4f0f-175">將位置設定為適合您的**位置**(請記住, 接近根目錄較佳)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="e4f0f-176">然後, 按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="e4f0f-177">在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="e4f0f-178">移至 [**編輯** > **喜好**設定], 然後在新視窗中, 流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="e4f0f-179">將**外部腳本編輯器**變更為**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="e4f0f-180">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="e4f0f-181">移至  > [檔案] [**組建設定**] 並選取 [**通用 Windows 平臺**], 然後按一下 [**切換平臺**] 按鈕以套用您的選取專案。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="e4f0f-182">仍在 [   > 檔案**組建] 設定**中, 請確定:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="e4f0f-183">**目標裝置**設定為**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="e4f0f-184">**組建類型**設定為**D3D**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="e4f0f-185">**SDK**已設定為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="e4f0f-186">**Visual Studio 版本**設定為 [**最新安裝**]</span><span class="sxs-lookup"><span data-stu-id="e4f0f-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="e4f0f-187">**組建和執行**設定為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="e4f0f-188">儲存場景, 並將它加入至組建。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="e4f0f-189">選取 [新增] [**開啟場景**] 來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="e4f0f-190">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="e4f0f-191">為此和任何未來的場景建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="e4f0f-192">選取 [**新增資料夾**] 按鈕, 若要建立新的資料夾, 請將其命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="e4f0f-193">開啟新建立的 [**幕後**] 資料夾, 然後在 [*檔案名*: 文字] 欄位中, 輸入**MR_ComputerVisionScene**, 然後按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="e4f0f-194">請注意, 您必須將 Unity 場景儲存在 [*資產*] 資料夾中, 因為它們必須與 Unity 專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="e4f0f-195">建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="e4f0f-196">[*組建設定*] 中的其餘設定, 現在應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="e4f0f-197">在 [*組建設定*] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測*器*所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="e4f0f-198">在此面板中, 需要驗證幾項設定:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="e4f0f-199">在 [**其他設定**] 索引標籤中:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="e4f0f-200">**指令碼** **執行階段版本**應該**實驗性**（.NET 4.6 對等），這會觸發程序需要重新啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="e4f0f-201">**腳本後端**應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="e4f0f-202">**API 相容性層級**應該是 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="e4f0f-203">在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="e4f0f-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="e4f0f-205">在面板的正下方, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到) 中, 勾選 [**支援的虛擬實境**], 並確定已新增**Windows Mixed Reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="e4f0f-206">回到 [*組建設定*] *, C# Unity 專案*不再呈現灰色;核取 [此] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="e4f0f-207">關閉 [*組建設定*] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="e4f0f-208">儲存場景和專案 ([  > 檔案] [**儲存場景]/**  > [檔案] [**儲存專案**])。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="e4f0f-209">第3章-Unity 中的匯入程式庫</span><span class="sxs-lookup"><span data-stu-id="e4f0f-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4f0f-210">如果您想要略過此課程的*Unity 設定*元件, 並直接繼續執行程式碼, 您可以免費下載此[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), 將其匯入至您的專案做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html), 然後繼續進行[第5章](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="e4f0f-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="e4f0f-211">若要在 Unity 中使用*Microsoft Graph* , 您必須利用**Microsoft. Identity. Client** DLL。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="e4f0f-212">您可以使用 Microsoft Graph SDK, 不過, 在您建立 Unity 專案之後 (也就是編輯專案後置), 它將需要新增 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="e4f0f-213">將所需的 Dll 直接匯入 Unity, 會將它視為較簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="e4f0f-214">Unity 中目前有一個已知問題, 需要在匯入後重新設定外掛程式。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="e4f0f-215">解決錯誤之後, 將不再需要這些步驟 (本節中的 4-7)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="e4f0f-216">若要將*Microsoft Graph*匯入至您自己的專案, 請[下載 MSGraph_LabPlugins。](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="e4f0f-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="e4f0f-217">已使用已測試過的程式庫版本來建立此套件。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="e4f0f-218">如果您想要深入瞭解如何將自訂 Dll 新增至 Unity 專案, 請[遵循此連結](https://docs.unity3d.com/Manual/UsingDLL.html)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="e4f0f-219">若要匯入封裝:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-219">To import the package:</span></span>

1.  <span data-ttu-id="e4f0f-220">使用 [**資產** > ] [匯**入套件** > ] [**自訂套件**] 功能表選項, 將 unity 封裝加入 unity。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="e4f0f-221">選取您剛才下載的套件。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="e4f0f-222">在快顯的 [匯**入 Unity 封裝**] 方塊中, 確定已選取 (和包含)**外掛程式**底下的所有專案。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="e4f0f-223">按一下 [匯**入**] 按鈕, 將專案新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="e4f0f-224">移至 [*專案] 面板*中 [**外掛程式**] 底下的 [ **MSGraph** ] 資料夾, 然後選取名為 [ **Microsoft 身分識別用戶端**] 的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="e4f0f-225">選取此*外掛程式*之後, 請確認已取消核取**任何平臺**, 然後確定**WSAPlayer**也未核取, 然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="e4f0f-226">這只是為了確認檔案已正確設定。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="e4f0f-227">標記這些外掛程式會將它們設定為僅在 Unity 編輯器中使用。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="e4f0f-228">[WSA] 資料夾中有一組不同的 Dll, 會在專案從 Unity 匯出為通用 Windows 應用程式之後使用。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="e4f0f-229">接下來, 您需要在**MSGraph**資料夾中開啟 [ **WSA** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="e4f0f-230">您會看到您剛才設定的相同檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="e4f0f-231">選取檔案, 然後在 偵測器:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="e4f0f-232">請確定未**選取** **任何平臺**, 而且**只**會**核**取 [ **WSAPlayer** ]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="e4f0f-233">確定**SDK**已設定為**UWP**, 而且**腳本後端**已設定為**點 Net**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="e4f0f-234">確定**已核**取 [**不處理**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="e4f0f-235">按一下 **[套用]** 。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="e4f0f-236">第4章-數位相機設定</span><span class="sxs-lookup"><span data-stu-id="e4f0f-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="e4f0f-237">在本章中, 您將設定場景的主要攝影機:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="e4f0f-238">在 [階層]*面板*中, 選取**主要相機**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="e4f0f-239">選取之後, 您就可以在 [偵測*器*] 面板中看到**主要攝影機**的所有元件。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="e4f0f-240">**相機物件**必須命名為「**主攝影機**」 (請注意拼寫的!)</span><span class="sxs-lookup"><span data-stu-id="e4f0f-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="e4f0f-241">主要相機**標記**必須設定為**MainCamera** (請注意拼寫!)</span><span class="sxs-lookup"><span data-stu-id="e4f0f-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="e4f0f-242">請確定**轉換位置**設定為**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="e4f0f-243">將**清除旗標**設定為**純色**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="e4f0f-244">將相機元件的**背景色彩**設定為**黑色, Alpha 0** **(十六進位碼: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="e4f0f-245">[階層]*面板*中的最終物件結構應如下圖所示:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="e4f0f-246">第5章-建立 MeetingsUI 類別</span><span class="sxs-lookup"><span data-stu-id="e4f0f-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="e4f0f-247">您需要建立的第一個腳本是**MeetingsUI**, 它負責裝載和填入應用程式的 UI (歡迎訊息、指示和會議詳細資料)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="e4f0f-248">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-248">To create this class:</span></span>

1.  <span data-ttu-id="e4f0f-249">以滑鼠右鍵按一下 [*專案] 面板*中的 [**資產**] 資料夾, 然後選取 [**建立** > **資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="e4f0f-250">將資料夾命名為**Scripts**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="e4f0f-251">開啟 [**腳本**] 資料夾, 然後在該資料夾中, 以滑鼠右鍵按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="e4f0f-252">將腳本命名為**MeetingsUI。**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="e4f0f-253">按兩下新的**MeetingsUI**腳本, 以*Visual Studio*開啟它。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="e4f0f-254">插入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="e4f0f-255">在類別內插入下列變數:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-255">Inside the class insert the following variables:</span></span>

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

6.  <span data-ttu-id="e4f0f-256">然後取代**Start ()** 方法, 並加入一個**喚醒 ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="e4f0f-257">當類別初始化時, 將會呼叫這些:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-257">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="e4f0f-258">新增負責建立*會議 UI*的方法, 並在要求時, 將目前的會議填入其中:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

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

8. <span data-ttu-id="e4f0f-259">**刪除** **Update ()** 方法, 並**將您的變更儲存**在 Visual Studio 中, 然後再返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="e4f0f-260">第6章-建立圖形類別</span><span class="sxs-lookup"><span data-stu-id="e4f0f-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="e4f0f-261">下一個要建立的腳本是**圖形**腳本。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="e4f0f-262">此腳本會負責進行呼叫以驗證使用者, 並從使用者的行事曆抓取當天的排程會議。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="e4f0f-263">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-263">To create this class:</span></span>

1.  <span data-ttu-id="e4f0f-264">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e4f0f-265">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e4f0f-266">將腳本命名為**Graph**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="e4f0f-267">按兩下腳本, 以 Visual Studio 開啟它。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="e4f0f-268">插入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-268">Insert the following namespaces:</span></span>

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
    > <span data-ttu-id="e4f0f-269">您會發現, 此腳本中的部分程式碼會包裝在預先[編譯](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)指示詞周圍, 這是為了避免在建立 Visual Studio 解決方案時程式庫發生問題。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="e4f0f-270">刪除**Start ()** 和**Update ()** 方法, 因為它們將不會使用。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="e4f0f-271">在**Graph**類別外, 插入下列物件, 這是將代表每日排程會議的 JSON 物件還原序列化所需的物件:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

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

7.  <span data-ttu-id="e4f0f-272">在**Graph**類別內, 新增下列變數:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-272">Inside the **Graph** class, add the following variables:</span></span>

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
    > <span data-ttu-id="e4f0f-273">變更 **appId** 值，成為 **應用程式識別碼** 您記下在 **[第 1 章](#chapter-1---create-your-app-in-the-application-registration-portal)，步驟 4** 。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="e4f0f-274">這個值應該與應用程式註冊**入口網站**中的應用程式註冊頁面中所顯示的值相同。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="e4f0f-275">在**Graph**類別中, 加入**SignInAsync ()** 和**AquireTokenAsync ()** 方法, 這會提示使用者插入登入認證。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

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

9.  <span data-ttu-id="e4f0f-276">新增下列兩個方法:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="e4f0f-277">**BuildTodayCalendarEndpoint ()** , 它會建立 URI, 指定要在其中抓取排程會議的日期和時間範圍。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="e4f0f-278">**ListMeetingsAsync ()** , 它會向*Microsoft Graph*要求已排定的會議。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

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

10. <span data-ttu-id="e4f0f-279">您現在已完成**圖形**腳本。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="e4f0f-280">請先儲存 Visual Studio 中的**變更**, 再返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="e4f0f-281">第7章-建立 GazeInput 腳本</span><span class="sxs-lookup"><span data-stu-id="e4f0f-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="e4f0f-282">您現在會建立**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="e4f0f-283">此類別會處理並追蹤使用者的注視, 並使用來自**主要攝影機**的**Raycast** , 並向前投射。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="e4f0f-284">若要建立腳本:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-284">To create the script:</span></span>

1.  <span data-ttu-id="e4f0f-285">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e4f0f-286">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e4f0f-287">將腳本命名為**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="e4f0f-288">按兩下腳本, 以 Visual Studio 開啟它。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="e4f0f-289">變更命名空間程式碼, 使其符合下列各項, 並在您的**GazeInput**類別上方加入 ' **\[ \]system.object**' 標記, 以便將它序列化:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="e4f0f-290">在**GazeInput**類別中, 新增下列變數:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-290">Inside the **GazeInput** class, add the following variables:</span></span>

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

6.  <span data-ttu-id="e4f0f-291">新增**CreateCursor ()** 方法來建立場景中的 HoloLens 游標, 並從**Start ()** 方法呼叫方法:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

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

7.  <span data-ttu-id="e4f0f-292">下列方法可啟用注視 Raycast, 並持續追蹤焦點物件。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

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

8.  <span data-ttu-id="e4f0f-293">請先儲存 Visual Studio 中的**變更**, 再返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="e4f0f-294">第8章-建立互動類別</span><span class="sxs-lookup"><span data-stu-id="e4f0f-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="e4f0f-295">您現在必須建立**互動**腳本, 其負責:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="e4f0f-296">處理點一下互動和**攝影機注視**, 讓使用者能夠與場景中的「按鈕」的記錄互動。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="e4f0f-297">在場景中建立登入「按鈕」物件, 讓使用者與之互動。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="e4f0f-298">若要建立腳本:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-298">To create the script:</span></span>

1.  <span data-ttu-id="e4f0f-299">按兩下 [**腳本**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e4f0f-300">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e4f0f-301">將腳本命名為**互動**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="e4f0f-302">按兩下腳本, 以 Visual Studio 開啟它。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="e4f0f-303">插入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="e4f0f-304">將**互動**類別的繼承從*MonoBehaviour*變更為**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="e4f0f-305">~~公用類別互動:MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="e4f0f-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="e4f0f-306">在**互動**類別內, 插入下列變數:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="e4f0f-307">取代**Start**方法。請注意, 它是一個覆寫方法, 它會呼叫「基底」注視類別方法。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="e4f0f-308">**Start （)** 類別初始化時，輸入辨識向註冊，並建立登入將會呼叫 *按鈕* 場景中：</span><span class="sxs-lookup"><span data-stu-id="e4f0f-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

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

8.  <span data-ttu-id="e4f0f-309">新增 **CreateSignInButton()** 方法，它會具現化的登入 *按鈕* 場景中並設定其屬性：</span><span class="sxs-lookup"><span data-stu-id="e4f0f-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

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

9.  <span data-ttu-id="e4f0f-310">加入**GestureRecognizer_Tapped ()** 方法, 它會回應*攻分*點使用者事件。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

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

10. <span data-ttu-id="e4f0f-311">**刪除** **Update ()** 方法, 然後**將您的變更儲存**在 Visual Studio 中, 然後再返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="e4f0f-312">第9章-設定腳本參考</span><span class="sxs-lookup"><span data-stu-id="e4f0f-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="e4f0f-313">在本章中, 您必須將**互動**腳本放到**主要相機**上。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="e4f0f-314">接著, 該腳本會處理將其他腳本放在需要的位置。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="e4f0f-315">從 [*專案] 面板*的 [**腳本**] 資料夾中, 將腳本**互動**拖曳到**主要相機**物件, 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="e4f0f-316">第10章-設定標記</span><span class="sxs-lookup"><span data-stu-id="e4f0f-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="e4f0f-317">處理注視的程式碼會使用標記**SignInButton**來識別使用者將與其互動以登入*Microsoft Graph*的物件。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="e4f0f-318">若要建立標記:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-318">To create the Tag:</span></span>

1.  <span data-ttu-id="e4f0f-319">在 Unity 編輯器中, 按一下 [階層]*面板*中的**主要攝影機**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="e4f0f-320">在 [偵測*器] 面板*中, 按一下 [ **MainCamera** ]*標記*以開啟下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="e4f0f-321">按一下 [**新增標記 ...** ]</span><span class="sxs-lookup"><span data-stu-id="e4f0f-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="e4f0f-322">按一下 [ **+** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="e4f0f-323">將標記名稱撰寫為**SignInButton** , 然後按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="e4f0f-324">第11章-將 Unity 專案建立至 UWP</span><span class="sxs-lookup"><span data-stu-id="e4f0f-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="e4f0f-325">此專案的 Unity 區段所需的全部內容現在已經完成, 所以可以從 Unity 建立它。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="e4f0f-326">瀏覽至 *組建設定* (**檔案*>*建置設定**)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="e4f0f-327">如果還沒這麼做, 請對 **\# Unity C 專案**進行滴答。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="e4f0f-328">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-328">Click **Build**.</span></span> <span data-ttu-id="e4f0f-329">Unity 將會啟動 [檔案**瀏覽器**] 視窗, 您必須在其中建立並選取要建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="e4f0f-330">立即建立該資料夾, 並將它命名為**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="e4f0f-331">然後選取 [**應用程式**] 資料夾, 按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="e4f0f-332">Unity 會開始將您的專案建立至**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="e4f0f-333">Unity 完成建立之後 (可能需要一些時間), 它會在組建的位置開啟 [檔案**瀏覽器**] 視窗 (請檢查您的工作列, 因為它不一定會出現在視窗的上方, 但會通知您加入新的視窗)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="e4f0f-334">第12章-部署至 HoloLens</span><span class="sxs-lookup"><span data-stu-id="e4f0f-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="e4f0f-335">若要在 HoloLens 上部署:</span><span class="sxs-lookup"><span data-stu-id="e4f0f-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="e4f0f-336">您將需要 HoloLens 的 IP 位址 (用於遠端部署), 並確保 HoloLens 處於**開發人員模式。**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="e4f0f-337">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="e4f0f-337">To do this:</span></span>

    1.  <span data-ttu-id="e4f0f-338">在戴 HoloLens 的同時, 請開啟**設定**。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="e4f0f-339">前往**Network & Internet**  >  **wi-fi**  >  **Advanced Options**</span><span class="sxs-lookup"><span data-stu-id="e4f0f-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="e4f0f-340">記下**IPv4**位址。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="e4f0f-341">接下來, 流覽回到 [**設定**], 然後為**開發人員** **更新 & 安全性** > </span><span class="sxs-lookup"><span data-stu-id="e4f0f-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="e4f0f-342">將**開發人員模式**設定為 On。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="e4f0f-343">流覽至新的 Unity 組建 (**應用程式**資料夾), 然後使用**Visual Studio**開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="e4f0f-344">在 [**解決方案**設定] 中, 選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="e4f0f-345">在**解決方案平臺**中, 選取 [ **x86]、[遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="e4f0f-346">系統會提示您插入遠端裝置的**IP 位址**(在此案例中, 這是您記下的 HoloLens)。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="e4f0f-347">移至 [**建立**] 功能表, 然後按一下 [**部署方案**], 將應用程式側載至您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="e4f0f-348">您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中, 準備好啟動!</span><span class="sxs-lookup"><span data-stu-id="e4f0f-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="e4f0f-349">您的 Microsoft Graph HoloLens 應用程式</span><span class="sxs-lookup"><span data-stu-id="e4f0f-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="e4f0f-350">恭喜, 您建立了一個混合現實應用程式, 利用 Microsoft Graph 來讀取和顯示使用者行事歷數據。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="e4f0f-351">額外練習</span><span class="sxs-lookup"><span data-stu-id="e4f0f-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="e4f0f-352">練習1</span><span class="sxs-lookup"><span data-stu-id="e4f0f-352">Exercise 1</span></span>

<span data-ttu-id="e4f0f-353">使用 Microsoft Graph 顯示使用者的其他相關資訊</span><span class="sxs-lookup"><span data-stu-id="e4f0f-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="e4f0f-354">使用者電子郵件/電話號碼/設定檔圖片</span><span class="sxs-lookup"><span data-stu-id="e4f0f-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="e4f0f-355">練習1</span><span class="sxs-lookup"><span data-stu-id="e4f0f-355">Exercise 1</span></span>

<span data-ttu-id="e4f0f-356">執行語音控制以流覽 Microsoft Graph UI。</span><span class="sxs-lookup"><span data-stu-id="e4f0f-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
