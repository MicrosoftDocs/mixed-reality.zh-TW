---
title: MR 和 Azure 308-跨裝置通知
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 通知中樞、Azure Functions 和 Azure 儲存體和資料表。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合現實, 學術, unity, 教學課程, api, 通知, 函數, 資料表, 通知中樞, hololens, 沉浸, vr
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694610"
---
>[!NOTE]
><span data-ttu-id="fb367-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="fb367-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fb367-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="fb367-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fb367-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="fb367-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fb367-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="fb367-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fb367-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="fb367-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fb367-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="fb367-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="fb367-110">MR 和 Azure 308:跨裝置通知</span><span class="sxs-lookup"><span data-stu-id="fb367-110">MR and Azure 308: Cross-device notifications</span></span>

![最終產品-開始](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="fb367-112">在此課程中, 您將瞭解如何使用 Azure 通知中樞、Azure 資料表和 Azure Functions, 將通知中樞功能新增至混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="fb367-113">**Azure 通知中樞**是一種 Microsoft 服務, 可讓開發人員將目標和個人化推播通知傳送至任何平臺, 並在雲端中提供所有功能。</span><span class="sxs-lookup"><span data-stu-id="fb367-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="fb367-114">這可有效地讓開發人員與使用者進行通訊, 或甚至在各種應用程式之間進行通訊, 視案例而定。</span><span class="sxs-lookup"><span data-stu-id="fb367-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="fb367-115">如需詳細資訊, 請造訪**Azure 通知中樞**[頁面](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)。</span><span class="sxs-lookup"><span data-stu-id="fb367-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="fb367-116">**Azure Functions**是一項 Microsoft 服務, 可讓開發人員在 Azure 中執行一小段程式碼, 即「函式」。</span><span class="sxs-lookup"><span data-stu-id="fb367-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="fb367-117">這可讓您將工作委派給雲端, 而不是您的本機應用程式, 這可能有許多好處。</span><span class="sxs-lookup"><span data-stu-id="fb367-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="fb367-118">**Azure Functions**支援數種開發語言, 包括\#C、\#F、node.js、JAVA 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="fb367-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="fb367-119">如需詳細資訊, 請造訪**Azure Functions** [頁面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="fb367-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="fb367-120">**Azure 資料表**是一項 Microsoft 雲端服務, 可讓開發人員在雲端中儲存結構化的非 SQL 資料, 讓您可以輕鬆地在任何地方存取。</span><span class="sxs-lookup"><span data-stu-id="fb367-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="fb367-121">此服務具有無架構設計, 可讓您視需要進行資料表演進, 因此非常有彈性。</span><span class="sxs-lookup"><span data-stu-id="fb367-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="fb367-122">如需詳細資訊, 請造訪**Azure 資料表**[頁面](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="fb367-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="fb367-123">完成此課程之後, 您將擁有一個混合現實的沉浸式耳機應用程式, 以及一個桌上型電腦應用程式, 其將能夠執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="fb367-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="fb367-124">桌上型電腦應用程式可讓使用者使用滑鼠來移動2D 空間 (X 和 Y) 中的物件。</span><span class="sxs-lookup"><span data-stu-id="fb367-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="fb367-125">電腦應用程式中的物件移動會使用 JSON 傳送至雲端, 其格式為字串, 其中包含物件識別碼、類型和轉換資訊 (X 和 Y 座標)。</span><span class="sxs-lookup"><span data-stu-id="fb367-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="fb367-126">混合現實應用程式 (其具有與桌面應用程式相同的場景) 將會從通知中樞服務 (剛由桌上型電腦應用程式更新) 接收有關物件移動的通知。</span><span class="sxs-lookup"><span data-stu-id="fb367-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="fb367-127">收到包含物件識別碼、類型和轉換資訊的通知時, mixed reality 應用程式會將接收的資訊套用到自己的場景。</span><span class="sxs-lookup"><span data-stu-id="fb367-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="fb367-128">在您的應用程式中, 您可以決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="fb367-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="fb367-129">本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。</span><span class="sxs-lookup"><span data-stu-id="fb367-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="fb367-130">您的工作是使用您從這個課程取得的知識, 來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="fb367-131">本課程是獨立的教學課程, 不直接牽涉到其他任何混合現實實驗室。</span><span class="sxs-lookup"><span data-stu-id="fb367-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="fb367-132">裝置支援</span><span class="sxs-lookup"><span data-stu-id="fb367-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fb367-133">粗</span><span class="sxs-lookup"><span data-stu-id="fb367-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fb367-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fb367-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fb367-135"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="fb367-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="fb367-136">MR 和 Azure 308:跨裝置通知</span><span class="sxs-lookup"><span data-stu-id="fb367-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="fb367-137">✔️</span><span class="sxs-lookup"><span data-stu-id="fb367-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="fb367-138">✔️</span><span class="sxs-lookup"><span data-stu-id="fb367-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="fb367-139">雖然此課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機, 但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fb367-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="fb367-140">隨著課程的遵循, 您會看到您可能需要用來支援 HoloLens 的任何變更的附注。</span><span class="sxs-lookup"><span data-stu-id="fb367-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="fb367-141">使用 HoloLens 時, 您可能會在語音捕獲期間發現一些回應。</span><span class="sxs-lookup"><span data-stu-id="fb367-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fb367-142">先決條件</span><span class="sxs-lookup"><span data-stu-id="fb367-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="fb367-143">本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="fb367-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="fb367-144">也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (5 月 2018)。</span><span class="sxs-lookup"><span data-stu-id="fb367-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="fb367-145">您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="fb367-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="fb367-146">在此課程中, 我們建議您採用下列硬體和軟體:</span><span class="sxs-lookup"><span data-stu-id="fb367-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="fb367-147">[與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦, 可用於沉浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="fb367-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="fb367-148">已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)</span><span class="sxs-lookup"><span data-stu-id="fb367-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fb367-149">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="fb367-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fb367-150">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="fb367-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fb367-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fb367-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="fb367-152">已啟用開發人員模式的[Windows Mixed Reality 沉浸 (VR) 耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="fb367-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="fb367-153">適用于 Azure 設定和存取通知中樞的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="fb367-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="fb367-154">開始之前</span><span class="sxs-lookup"><span data-stu-id="fb367-154">Before you start</span></span>

- <span data-ttu-id="fb367-155">為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。</span><span class="sxs-lookup"><span data-stu-id="fb367-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="fb367-156">您必須是 Microsoft 開發人員入口網站和應用程式註冊入口網站的擁有者, 否則您將不會擁有存取[第2章](#chapter-2---retrieve-your-new-apps-credentials)中應用程式的許可權。</span><span class="sxs-lookup"><span data-stu-id="fb367-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="fb367-157">第1章-在 Microsoft 開發人員入口網站上建立應用程式</span><span class="sxs-lookup"><span data-stu-id="fb367-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="fb367-158">若要使用**Azure 通知中樞**服務, 您將需要在 Microsoft 開發人員入口網站上建立應用程式, 因為您的應用程式需要註冊, 才能傳送和接收通知。</span><span class="sxs-lookup"><span data-stu-id="fb367-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="fb367-159">登入[Microsoft 開發人員入口網站](https://developer.microsoft.com/dashboard)。</span><span class="sxs-lookup"><span data-stu-id="fb367-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="fb367-160">您必須登入您的 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb367-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="fb367-161">在儀表板中, 按一下 [**建立新的應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-161">From the Dashboard, click **Create a new app**.</span></span>

    ![建立應用程式](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="fb367-163">隨即會出現一個快顯視窗, 您需要為新的應用程式保留名稱。</span><span class="sxs-lookup"><span data-stu-id="fb367-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="fb367-164">在文字方塊中, 插入適當的名稱;如果選擇的名稱可用, 則會在文字方塊的右邊顯示刻度。</span><span class="sxs-lookup"><span data-stu-id="fb367-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="fb367-165">插入可用名稱之後, 請按一下快顯視窗左下方的 [**保留產品名稱**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fb367-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![反向名稱](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="fb367-167">現在已建立應用程式, 您已準備好移至下一章。</span><span class="sxs-lookup"><span data-stu-id="fb367-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="fb367-168">第2章-取得新的應用程式認證</span><span class="sxs-lookup"><span data-stu-id="fb367-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="fb367-169">登入應用程式註冊入口網站, 其中會列出您的新應用程式, 並抓取將用來在**Azure 入口網站**中設定**通知中樞服務**的認證。</span><span class="sxs-lookup"><span data-stu-id="fb367-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="fb367-170">流覽至[應用程式註冊入口網站](http://apps.dev.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="fb367-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![應用程式註冊入口網站](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="fb367-172">您必須使用您的 Microsoft 帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="fb367-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="fb367-173">這**必須**是您在上一[章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)中使用的 Microsoft 帳戶, 以及 Windows Store 開發人員入口網站。</span><span class="sxs-lookup"><span data-stu-id="fb367-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="fb367-174">您會在 [**我的應用程式**] 區段下找到您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="fb367-175">找到之後, 請按一下它, 您將會進入新的頁面, 其中包含應用程式名稱加上**註冊**。</span><span class="sxs-lookup"><span data-stu-id="fb367-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![您剛註冊的應用程式](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="fb367-177">向下流覽註冊頁面, 以尋找**應用程式**的 [秘密] 區段和 [**套件 SID** ]。</span><span class="sxs-lookup"><span data-stu-id="fb367-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="fb367-178">在下一章中, 複製兩者以用於設定**Azure 通知中樞服務**。</span><span class="sxs-lookup"><span data-stu-id="fb367-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![應用程式秘密](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="fb367-180">第3章-設定 Azure 入口網站: 建立通知中樞服務</span><span class="sxs-lookup"><span data-stu-id="fb367-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="fb367-181">取得您的應用程式認證之後, 您必須移至 Azure 入口網站, 您將在其中建立 Azure 通知中樞服務。</span><span class="sxs-lookup"><span data-stu-id="fb367-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="fb367-182">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="fb367-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="fb367-183">如果您還沒有 Azure 帳戶, 您將需要建立一個。</span><span class="sxs-lookup"><span data-stu-id="fb367-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="fb367-184">如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb367-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="fb367-185">登入之後, 按一下左上角的 [**新增**], 並搜尋 [**通知中樞**], 然後按一下***Enter 鍵***。</span><span class="sxs-lookup"><span data-stu-id="fb367-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![搜尋通知中樞](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="fb367-187">在較新的入口網站中,***新***的「可能」已取代為「**建立資源**」。</span><span class="sxs-lookup"><span data-stu-id="fb367-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="fb367-188">[新增] 頁面將會提供*通知中樞*服務的描述。</span><span class="sxs-lookup"><span data-stu-id="fb367-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="fb367-189">在此提示的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="fb367-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![建立通知中樞實例](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="fb367-191">一旦您按下 ***建立*** :</span><span class="sxs-lookup"><span data-stu-id="fb367-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="fb367-192">為此服務實例插入您想要的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb367-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="fb367-193">提供可讓您與此應用程式建立關聯的**命名空間**。</span><span class="sxs-lookup"><span data-stu-id="fb367-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="fb367-194">選取 [**位置]。**</span><span class="sxs-lookup"><span data-stu-id="fb367-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="fb367-195">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="fb367-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="fb367-196">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="fb367-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fb367-197">建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。</span><span class="sxs-lookup"><span data-stu-id="fb367-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="fb367-198">如果您想要深入瞭解 Azure 資源群組, 請遵循此[連結以瞭解如何管理資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="fb367-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="fb367-199">選取適當的**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb367-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="fb367-200">您也必須確認您已瞭解適用于此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="fb367-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="fb367-201">選取 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="fb367-201">Select **Create**.</span></span>

        ![填寫服務詳細資料](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="fb367-203">按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="fb367-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="fb367-204">建立服務實例之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="fb367-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![通知](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="fb367-206">按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="fb367-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="fb367-207">您將會進入新的**通知中樞**服務實例。</span><span class="sxs-lookup"><span data-stu-id="fb367-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![前往資源](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="fb367-209">從 [總覽] 頁面中, 按一下頁面的正下方, 然後按一下 [ **Windows (WNS)]。**</span><span class="sxs-lookup"><span data-stu-id="fb367-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="fb367-210">右邊的面板將會變更, 以顯示兩個文字欄位, 其中需要您先前設定的應用程式中的**套件 SID**和**安全性金鑰**。</span><span class="sxs-lookup"><span data-stu-id="fb367-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![新建立的中樞服務](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="fb367-212">將詳細資料複製到正確的欄位之後, 按一下 [**儲存**], 您就會在通知中樞已成功更新時收到通知。</span><span class="sxs-lookup"><span data-stu-id="fb367-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![複製安全性詳細資料](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="fb367-214">第4章-設定 Azure 入口網站: 建立資料表服務</span><span class="sxs-lookup"><span data-stu-id="fb367-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="fb367-215">建立通知中樞服務實例之後, 流覽回到您的 Azure 入口網站, 您將藉由建立儲存體資源來建立 Azure 資料表服務。</span><span class="sxs-lookup"><span data-stu-id="fb367-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="fb367-216">如果尚未登入, 請登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="fb367-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="fb367-217">登入之後, 按一下左上角的 [**新增**], 並搜尋 [**儲存體帳戶**], 然後按一下**Enter 鍵**。</span><span class="sxs-lookup"><span data-stu-id="fb367-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="fb367-218">在較新的入口網站中,***新***的「可能」已取代為「**建立資源**」。</span><span class="sxs-lookup"><span data-stu-id="fb367-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="fb367-219">從清單中選取 [**儲存體帳戶-blob、檔案、資料表、佇列**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![搜尋儲存體帳戶](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="fb367-221">新的頁面會提供**儲存體帳戶**服務的描述。</span><span class="sxs-lookup"><span data-stu-id="fb367-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="fb367-222">在此提示的左下方, 選取 [**建立**] 按鈕, 以建立此服務的實例。</span><span class="sxs-lookup"><span data-stu-id="fb367-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="fb367-224">當您按一下 [**建立**] 之後, 就會出現一個面板:</span><span class="sxs-lookup"><span data-stu-id="fb367-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="fb367-225">為此服務實例插入您想要的**名稱**(必須全部小寫)。</span><span class="sxs-lookup"><span data-stu-id="fb367-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="fb367-226">針對 [**部署模型**], 按一下 [ **Resource manager**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="fb367-227">針對 [**帳戶種類**], 使用下拉式功能表, 選取 [**儲存體 (一般用途 v1)** ]。</span><span class="sxs-lookup"><span data-stu-id="fb367-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="fb367-228">選取適當的**位置**。</span><span class="sxs-lookup"><span data-stu-id="fb367-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="fb367-229">針對 [複寫] 下拉式功能表, 選取 [**讀取權限-異地-多餘儲存體 (RA-GRS)** ]。</span><span class="sxs-lookup"><span data-stu-id="fb367-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="fb367-230">針對 [**效能**], 請按一下 [**標準**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="fb367-231">在 [**需要安全傳輸**] 區段中, 選取 [**停用**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="fb367-232">從 [**訂**用帳戶] 下拉式功能表中, 選取適當的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb367-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="fb367-233">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="fb367-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="fb367-234">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="fb367-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fb367-235">建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。</span><span class="sxs-lookup"><span data-stu-id="fb367-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="fb367-236">如果您想要深入瞭解 Azure 資源群組, 請遵循此[連結以瞭解如何管理資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="fb367-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="fb367-237">如果這是您的選項, 請將 [**虛擬網路**] 保留為 [**停用**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="fb367-238">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="fb367-238">Click **Create**.</span></span>

        ![填入儲存體詳細資料](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="fb367-240">按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="fb367-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="fb367-241">建立服務實例之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="fb367-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="fb367-242">按一下 [通知] 以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="fb367-242">Click on the notifications to explore your new Service instance.</span></span>

    ![新的儲存體通知](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="fb367-244">按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="fb367-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="fb367-245">您將會進入新的儲存體服務實例的 [總覽] 頁面。</span><span class="sxs-lookup"><span data-stu-id="fb367-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![前往資源](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="fb367-247">從 [總覽] 頁面, 按一下右側的 [**資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="fb367-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="fb367-248">右側面板會變更, 以顯示**表格服務**資訊, 您需要在其中新增新的資料表。</span><span class="sxs-lookup"><span data-stu-id="fb367-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="fb367-249">若要這麼做, **+** 請按一下左上角的 [**資料表**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fb367-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![開啟資料表](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="fb367-251">將會顯示新的頁面, 您必須在其中輸入**資料表名稱**。</span><span class="sxs-lookup"><span data-stu-id="fb367-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="fb367-252">這是您在後續章節中用來參考應用程式中資料的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb367-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="fb367-253">插入適當的名稱, 然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="fb367-253">Insert an appropriate name and click **OK**.</span></span>

    ![建立新資料表](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="fb367-255">建立新的資料表之後, 您就可以在 [**表格服務**] 頁面 (底部) 中看到它。</span><span class="sxs-lookup"><span data-stu-id="fb367-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![已建立新資料表](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="fb367-257">第5章-在 Visual Studio 中完成 Azure 資料表</span><span class="sxs-lookup"><span data-stu-id="fb367-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="fb367-258">既然已設定您的**表格服務**儲存體帳戶, 就可以在其中加入資料, 這將用來儲存和抓取資訊。</span><span class="sxs-lookup"><span data-stu-id="fb367-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="fb367-259">您可以透過**Visual Studio**來編輯您的資料表。</span><span class="sxs-lookup"><span data-stu-id="fb367-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="fb367-260">開啟**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fb367-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="fb367-261">從功能表中, 按一下 [ **View**  >  **Cloud Explorer**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![開啟 cloud explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="fb367-263">**Cloud Explorer**將會開啟為停駐的專案 (請耐心等候, 因為載入可能需要一些時間)。</span><span class="sxs-lookup"><span data-stu-id="fb367-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="fb367-264">如果看不到您用來建立*儲存體帳戶*的訂用帳戶, 請確定您有:</span><span class="sxs-lookup"><span data-stu-id="fb367-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="fb367-265">登入與您用於 Azure 入口網站的帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="fb367-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="fb367-266">從 [帳戶管理] 頁面選取您的訂用帳戶 (您可能需要從您的帳戶設定套用篩選):</span><span class="sxs-lookup"><span data-stu-id="fb367-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![尋找訂用帳戶](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="fb367-268">將會顯示您的 Azure 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="fb367-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="fb367-269">尋找 [**儲存體帳戶**], 然後按一下該左側的箭號以展開您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb367-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![開啟儲存體帳戶](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="fb367-271">擴充之後, 應該就可以使用新建立的**儲存體帳戶**。</span><span class="sxs-lookup"><span data-stu-id="fb367-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="fb367-272">按一下儲存體左邊的箭號, 然後展開 [尋找**資料表**], 再按一下該按鈕旁邊的箭號, 以顯示您在上一章中建立的**資料表**。</span><span class="sxs-lookup"><span data-stu-id="fb367-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="fb367-273">按兩下您的**資料表**。</span><span class="sxs-lookup"><span data-stu-id="fb367-273">Double click your **Table**.</span></span>

    ![開啟場景物件資料表](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="fb367-275">您的資料表將會在 Visual Studio 視窗的中央開啟。</span><span class="sxs-lookup"><span data-stu-id="fb367-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="fb367-276">按一下 [資料表] 圖示，以 **+** （加上） 在其上。</span><span class="sxs-lookup"><span data-stu-id="fb367-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![加入新的資料表](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="fb367-278">隨即會出現一個視窗, 提示您*加入實體*。</span><span class="sxs-lookup"><span data-stu-id="fb367-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="fb367-279">您將會建立總共三個實體, 每個都有數個屬性。</span><span class="sxs-lookup"><span data-stu-id="fb367-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="fb367-280">您會發現*PartitionKey*和*RowKey*已提供, 因為資料表會使用這些來尋找您的資料。</span><span class="sxs-lookup"><span data-stu-id="fb367-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![資料分割和資料列索引鍵](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="fb367-282">更新**PartitionKey**和**RowKey**的*值*, 如下所示 (請務必針對您新增的每個資料列屬性執行此動作, 但每次都要增加 RowKey):</span><span class="sxs-lookup"><span data-stu-id="fb367-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![新增正確的值](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="fb367-284">按一下 [**新增屬性**], 以新增額外的資料列。</span><span class="sxs-lookup"><span data-stu-id="fb367-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="fb367-285">讓您的第一個空白資料表符合下表。</span><span class="sxs-lookup"><span data-stu-id="fb367-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="fb367-286">完成後, 請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="fb367-286">Click **OK** when you are finished.</span></span>

    ![完成時按一下 [確定]](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="fb367-288">請確定您已將**X**、 **Y**和**Z**等專案的**類型**變更為**Double**。</span><span class="sxs-lookup"><span data-stu-id="fb367-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="fb367-289">您會注意到您的資料表現在有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="fb367-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="fb367-290">再次按一下 **+** (加號) 圖示, 以新增另一個實體。</span><span class="sxs-lookup"><span data-stu-id="fb367-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![第一個資料列](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="fb367-292">建立其他屬性, 然後設定新實體的值以符合如下所示的值。</span><span class="sxs-lookup"><span data-stu-id="fb367-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![新增 cube](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="fb367-294">重複最後一個步驟, 以加入另一個實體。</span><span class="sxs-lookup"><span data-stu-id="fb367-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="fb367-295">將此實體的值設定如下所示。</span><span class="sxs-lookup"><span data-stu-id="fb367-295">Set the values for this entity to those shown below.</span></span>

    ![新增圓柱](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="fb367-297">您的資料表現在看起來應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="fb367-297">Your table should now look like the one below.</span></span>

    ![資料表完成](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="fb367-299">您已完成這一章。</span><span class="sxs-lookup"><span data-stu-id="fb367-299">You have completed this Chapter.</span></span> <span data-ttu-id="fb367-300">請務必儲存。</span><span class="sxs-lookup"><span data-stu-id="fb367-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="fb367-301">第6章-建立 Azure 函數應用程式</span><span class="sxs-lookup"><span data-stu-id="fb367-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="fb367-302">建立 Azure 函數應用程式, 桌面應用程式將會呼叫它來更新**表格**服務, 並透過**通知中樞**傳送通知。</span><span class="sxs-lookup"><span data-stu-id="fb367-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="fb367-303">首先, 您必須建立可讓您的 Azure 函式載入所需程式庫的檔案。</span><span class="sxs-lookup"><span data-stu-id="fb367-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="fb367-304">開啟 [**記事本**] (按 Windows 鍵, 然後輸入 [記事本])。</span><span class="sxs-lookup"><span data-stu-id="fb367-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![開啟 [記事本]](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="fb367-306">在 [記事本] 開啟的情況下, 將下面的 JSON 結構插入其中。</span><span class="sxs-lookup"><span data-stu-id="fb367-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="fb367-307">完成之後, 請將它儲存在您的桌上型電腦上做為**專案 json**。</span><span class="sxs-lookup"><span data-stu-id="fb367-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="fb367-308">請務必正確地命名: 請確定它的副檔名**不是 .txt** 。</span><span class="sxs-lookup"><span data-stu-id="fb367-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="fb367-309">此檔案會定義您的函式將使用的程式庫, 如果您已經使用 NuGet, 它看起來會很熟悉。</span><span class="sxs-lookup"><span data-stu-id="fb367-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="fb367-310">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="fb367-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="fb367-311">登入之後, 按一下左上角的 [**新增**], 然後搜尋**函數應用程式**, 按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="fb367-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![搜尋函數應用程式](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="fb367-313">在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。</span><span class="sxs-lookup"><span data-stu-id="fb367-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="fb367-314">[新增] 頁面將會提供**函數應用程式**服務的描述。</span><span class="sxs-lookup"><span data-stu-id="fb367-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="fb367-315">在此提示的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="fb367-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![函數應用程式實例](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="fb367-317">當您按一下 [**建立**] 之後, 請填寫下列內容:</span><span class="sxs-lookup"><span data-stu-id="fb367-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="fb367-318">針對 [**應用程式名稱**], 插入您想要的此服務實例名稱。</span><span class="sxs-lookup"><span data-stu-id="fb367-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="fb367-319">選取**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb367-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="fb367-320">選取適合您的定價層, 如果這是您第一次建立**函數應用程式服務**, 免費層應可供您使用。</span><span class="sxs-lookup"><span data-stu-id="fb367-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="fb367-321">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="fb367-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="fb367-322">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="fb367-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fb367-323">建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。</span><span class="sxs-lookup"><span data-stu-id="fb367-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="fb367-324">如果您想要深入瞭解 Azure 資源群組, 請遵循此[連結以瞭解如何管理資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="fb367-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="fb367-325">針對 [**作業系統**], 按一下 [Windows], 因為這是所需的平臺。</span><span class="sxs-lookup"><span data-stu-id="fb367-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="fb367-326">選取**主控方案**(本教學課程使用的是取用**方案**)。</span><span class="sxs-lookup"><span data-stu-id="fb367-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="fb367-327">選取**位置** **(選擇與您在上一個步驟中建立的儲存體相同的位置)**</span><span class="sxs-lookup"><span data-stu-id="fb367-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="fb367-328">針對 [**儲存體**] 區段,**您必須選取您在上一個步驟中建立的儲存體服務**。</span><span class="sxs-lookup"><span data-stu-id="fb367-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="fb367-329">您不需要在此應用程式中*Application Insights* , 因此請隨意保留。</span><span class="sxs-lookup"><span data-stu-id="fb367-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="fb367-330">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="fb367-330">Click **Create**.</span></span>

        ![建立新的實例](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="fb367-332">按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="fb367-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="fb367-333">建立服務實例之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="fb367-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新通知](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="fb367-335">按一下 [通知] 以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="fb367-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="fb367-336">按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="fb367-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![前往資源](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="fb367-338">按一下 [ **+** 函式] 旁邊的 (加號) 圖示, 以*建立新*的。</span><span class="sxs-lookup"><span data-stu-id="fb367-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![加入新函數](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="fb367-340">在中央面板中, 將會出現 [**函數**建立] 視窗。</span><span class="sxs-lookup"><span data-stu-id="fb367-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="fb367-341">忽略面板上半部的資訊, 然後按一下位於底部附近的 [**自訂**函式] (在藍色區域中, 如下所示)。</span><span class="sxs-lookup"><span data-stu-id="fb367-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![自訂函數](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="fb367-343">視窗內的新頁面將會顯示各種功能類型。</span><span class="sxs-lookup"><span data-stu-id="fb367-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="fb367-344">向下滾動以查看紫色類型, 然後按一下 [ **HTTP PUT**元素]。</span><span class="sxs-lookup"><span data-stu-id="fb367-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![HTTP put 連結](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="fb367-346">您可能必須進一步向下滾動頁面 (如果已進行 Azure 入口網站更新, 此影像可能看起來不完全相同), 不過, 您正在尋找名為*HTTP PUT*的元素。</span><span class="sxs-lookup"><span data-stu-id="fb367-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="fb367-347">[ **HTTP PUT** ] 視窗隨即出現, 您必須在其中設定函式 (請參閱下方的影像)。</span><span class="sxs-lookup"><span data-stu-id="fb367-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="fb367-348">針對 [**語言],** 使用下拉式功能表, 選取 [\#C]。</span><span class="sxs-lookup"><span data-stu-id="fb367-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="fb367-349">針對 [**名稱],** 輸入適當的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb367-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="fb367-350">在 [**驗證層級**] 下拉式功能表中  , 選取 [函式]。</span><span class="sxs-lookup"><span data-stu-id="fb367-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="fb367-351">在 [**資料表名稱**] 區段中, 您必須使用先前用來建立**資料表**服務的確切名稱 (包括相同的字母大小寫)。</span><span class="sxs-lookup"><span data-stu-id="fb367-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="fb367-352">在 [**儲存體帳戶連接**] 區段中, 使用下拉式功能表, 然後從該處選取您的儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb367-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="fb367-353">如果沒有出現, 請按一下 [**新增**] 超連結和區段標題, 以顯示另一個面板, 其中列出您的儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb367-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![新增存放裝置](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="fb367-355">按一下 [**建立**], 您就會收到通知, 指出您的設定已成功更新。</span><span class="sxs-lookup"><span data-stu-id="fb367-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![create 函式](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="fb367-357">按一下 [**建立**] 之後, 系統會將您重新導向至 [函數編輯器]。</span><span class="sxs-lookup"><span data-stu-id="fb367-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![更新函式程式碼](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="fb367-359">將下列程式碼插入函數編輯器中 (取代函式中的程式碼):</span><span class="sxs-lookup"><span data-stu-id="fb367-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="fb367-360">函式會使用包含的程式庫, 接收在 Unity 場景中移動之物件的名稱和位置 (稱為**UnityGameObject**的C#物件)。</span><span class="sxs-lookup"><span data-stu-id="fb367-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="fb367-361">然後, 這個物件會用來更新所建立之資料表內的物件參數。</span><span class="sxs-lookup"><span data-stu-id="fb367-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="fb367-362">在此之後, 函式會呼叫已建立的通知中樞服務, 這會通知所有已訂閱的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="fb367-363">備妥程式碼後, 按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="fb367-364">接下來，按一下 **\<** （箭頭） 圖示，在頁面的右手邊。</span><span class="sxs-lookup"><span data-stu-id="fb367-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![開啟上傳面板](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="fb367-366">面板會從右邊滑入。</span><span class="sxs-lookup"><span data-stu-id="fb367-366">A panel will slide in from the right.</span></span> <span data-ttu-id="fb367-367">在該面板中, 按一下 **[上傳**], 檔案瀏覽器隨即出現。</span><span class="sxs-lookup"><span data-stu-id="fb367-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="fb367-368">流覽至, 然後按一下 [您先前在**記事本**中建立的**專案. json**檔案], 再按一下 [**開啟**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fb367-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="fb367-369">此檔案會定義您的函式將使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="fb367-369">This file defines the libraries that your function will use.</span></span>

    ![上傳 json](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="fb367-371">檔案上傳之後, 它就會出現在右邊的面板中。</span><span class="sxs-lookup"><span data-stu-id="fb367-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="fb367-372">按一下它會在**函數**編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="fb367-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="fb367-373">它的外觀必須和下一個影像**完全**相同 (在步驟23底下)。</span><span class="sxs-lookup"><span data-stu-id="fb367-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="fb367-374">然後, 在左側面板中, 按一下 [函  式] 底下的 [**整合**] 連結。</span><span class="sxs-lookup"><span data-stu-id="fb367-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![整合函式](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="fb367-376">在下一個頁面上, 按一下右上角的 [ **Advanced editor** ] (如下所示)。</span><span class="sxs-lookup"><span data-stu-id="fb367-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![開啟進階編輯器](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="fb367-378">將會在中央面板中開啟函式**json**檔案, 此檔案必須以下列程式碼片段取代。</span><span class="sxs-lookup"><span data-stu-id="fb367-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="fb367-379">這會定義您要建立的函式, 以及傳遞至函式的參數。</span><span class="sxs-lookup"><span data-stu-id="fb367-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="fb367-380">您的編輯器現在看起來應該如下圖所示:</span><span class="sxs-lookup"><span data-stu-id="fb367-380">Your editor should now look like the image below:</span></span>

    ![回到標準編輯器](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="fb367-382">您可能會注意到剛才插入的輸入參數可能不符合您的資料表和儲存體詳細資料, 因此需要以您的資訊進行更新。</span><span class="sxs-lookup"><span data-stu-id="fb367-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="fb367-383">請不要在**這裡執行此**動作, 如下所述。</span><span class="sxs-lookup"><span data-stu-id="fb367-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="fb367-384">只要按一下頁面右上角的 [**標準編輯器**] 連結, 即可返回。</span><span class="sxs-lookup"><span data-stu-id="fb367-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="fb367-385">回到**標準編輯器**中, 按一下 [**輸入**] 底下的 **[Azure 表格儲存體 (資料表)** ]。</span><span class="sxs-lookup"><span data-stu-id="fb367-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![資料表輸入](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="fb367-387">請確定**您**的資訊符合下列各項, 因為它們可能不同 (以下步驟中有映射):</span><span class="sxs-lookup"><span data-stu-id="fb367-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="fb367-388">**資料表名稱**: 您在 Azure 儲存體資料表服務內建立的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="fb367-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="fb367-389">**儲存體帳戶連線:** 按一下 [**新增**], 這會出現在下拉式功能表旁邊, 而面板會出現在視窗的右側。</span><span class="sxs-lookup"><span data-stu-id="fb367-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![新增存放裝置](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="fb367-391">選取您先前建立用來裝載**函數應用程式**的**儲存體帳戶**。</span><span class="sxs-lookup"><span data-stu-id="fb367-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="fb367-392">您會發現已建立**儲存體帳戶**連接值。</span><span class="sxs-lookup"><span data-stu-id="fb367-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="fb367-393">完成後, 請務必按 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="fb367-394">[**輸入**] 頁面現在應符合下列內容, 其中顯示**您**的資訊。</span><span class="sxs-lookup"><span data-stu-id="fb367-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![輸入完成](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="fb367-396">接下來, 在 [**輸出**] 下按一下 [ **Azure 通知中樞 (通知)** ]。</span><span class="sxs-lookup"><span data-stu-id="fb367-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="fb367-397">請確定下列各項已符合**您**的資訊, 因為它們可能不同 (以下步驟中有一個影像):</span><span class="sxs-lookup"><span data-stu-id="fb367-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="fb367-398">**通知中樞名稱**: 這是您先前建立的**通知中樞**服務實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb367-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="fb367-399">**通知中樞命名空間**連線: 按一下 [**新增**], 這會出現在下拉式功能表旁。</span><span class="sxs-lookup"><span data-stu-id="fb367-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![檢查輸出](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="fb367-401">[連線] 快顯視窗隨即出現 (請參閱下圖), 您必須在此選取您先前設定的**通知中樞** **命名空間**。</span><span class="sxs-lookup"><span data-stu-id="fb367-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="fb367-402">從中間下拉式功能表中選取您的**通知中樞**名稱。</span><span class="sxs-lookup"><span data-stu-id="fb367-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="fb367-403">將**原則**下拉式功能表設定為**DefaultFullSharedAccessSignature**。</span><span class="sxs-lookup"><span data-stu-id="fb367-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="fb367-404">按一下 [**選取**] 按鈕以返回。</span><span class="sxs-lookup"><span data-stu-id="fb367-404">Click the **Select** button to go back.</span></span>

        ![輸出更新](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="fb367-406">[**輸出**] 頁面現在應符合下列內容, 但會改為使用**您**的資訊。</span><span class="sxs-lookup"><span data-stu-id="fb367-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="fb367-407">請務必按 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="fb367-408">*請勿直接編輯通知中樞名稱*(這一切都應該使用**進階編輯器**完成, 前提是您已正確地遵循先前的步驟。</span><span class="sxs-lookup"><span data-stu-id="fb367-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![輸出完成](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="fb367-410">此時, 您應該測試函式, 以確保其運作正常。</span><span class="sxs-lookup"><span data-stu-id="fb367-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="fb367-411">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="fb367-411">To do this:</span></span> 

    1. <span data-ttu-id="fb367-412">再次流覽至 [函式] 頁面:</span><span class="sxs-lookup"><span data-stu-id="fb367-412">Navigate to the function page once more:</span></span>

        ![輸出完成](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="fb367-414">回到 [函數] 頁面, 按一下頁面最右邊的 [**測試**] 索引標籤, 以開啟 [*測試*] 分頁:</span><span class="sxs-lookup"><span data-stu-id="fb367-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![輸出完成](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="fb367-416">在分頁的 [**要求**本文] 文字方塊中, 貼上下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="fb367-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="fb367-417">測試程式碼準備就緒後, 按一下右下方的 [**執行**] 按鈕, 測試將會執行。</span><span class="sxs-lookup"><span data-stu-id="fb367-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="fb367-418">測試的輸出記錄將會出現在您的函式程式碼下方的主控台區域中。</span><span class="sxs-lookup"><span data-stu-id="fb367-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![輸出完成](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="fb367-420">如果上述測試失敗, 您必須再次檢查您已遵循上述步驟, 特別是 [**整合] 面板**中的設定。</span><span class="sxs-lookup"><span data-stu-id="fb367-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="fb367-421">第7章-設定桌面 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="fb367-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb367-422">您現在建立的桌面應用程式**將無法**在 Unity 編輯器中使用。</span><span class="sxs-lookup"><span data-stu-id="fb367-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="fb367-423">您必須使用 Visual Studio (或已部署的應用程式), 在應用程式建立後, 于編輯器之外執行。</span><span class="sxs-lookup"><span data-stu-id="fb367-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="fb367-424">以下是使用 Unity 和 mixed reality 進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="fb367-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="fb367-425">設定和測試混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="fb367-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="fb367-426">在此課程中, 您將**不**需要有動作控制器。</span><span class="sxs-lookup"><span data-stu-id="fb367-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="fb367-427">如果您需要支援設定沉浸式耳機, 請遵循此[連結以瞭解如何設定 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="fb367-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="fb367-428">開啟**Unity** , 然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-428">Open **Unity** and click **New**.</span></span>

    ![新增 unity 專案](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="fb367-430">您需要提供 Unity 專案名稱, 並插入**UnityDesktopNotifHub**。</span><span class="sxs-lookup"><span data-stu-id="fb367-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="fb367-431">請確定 [專案類型] 設定為 [ **3d**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="fb367-432">將位置設定為適合您的**位置**(請記住, 接近根目錄較佳)。</span><span class="sxs-lookup"><span data-stu-id="fb367-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="fb367-433">然後, 按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-433">Then, click **Create project**.</span></span>

    ![建立專案](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="fb367-435">在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fb367-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="fb367-436">移至 [**編輯** > **喜好**設定], 然後在新視窗中, 流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="fb367-437">將**外部腳本編輯器**變更為**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="fb367-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="fb367-438">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="fb367-438">Close the **Preferences** window.</span></span>

    ![設定外部 VS 工具](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="fb367-440">接下來, 移   > 至 [檔案] [**組建設定**] 並選取 [**通用 Windows 平臺**], 然後按一下 [**切換平臺**] 按鈕以套用您的選取專案。</span><span class="sxs-lookup"><span data-stu-id="fb367-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![交換器平臺](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="fb367-442">仍在 [  > 檔案**組建] 設定**中, 請確定:</span><span class="sxs-lookup"><span data-stu-id="fb367-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="fb367-443">**目標裝置**已設定為**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="fb367-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="fb367-444">此應用程式將適用于您的桌面, 因此必須是**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="fb367-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="fb367-445">**組建類型**設定為**D3D**</span><span class="sxs-lookup"><span data-stu-id="fb367-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="fb367-446">**SDK**已設定為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="fb367-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="fb367-447">**Visual Studio 版本**設定為 [**最新安裝**]</span><span class="sxs-lookup"><span data-stu-id="fb367-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="fb367-448">**組建和執行**設定為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="fb367-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="fb367-449">在這裡, 很值得儲存場景, 並將它加入組建。</span><span class="sxs-lookup"><span data-stu-id="fb367-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="fb367-450">選取 [新增] [**開啟場景**] 來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="fb367-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="fb367-451">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="fb367-451">A save window will appear.</span></span>

            ![新增開啟的場景](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="fb367-453">為此建立新的資料夾, 並在任何未來的場景中選取 [**新增資料夾**] 按鈕, 以建立新的資料夾, 將其命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="fb367-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新增背景資料夾](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="fb367-455">開啟新建立的 [**幕後**] 資料夾, 然後在 [**檔案名:** 文字] 欄位中, 輸入**NH\_Desktop\_場景**, 然後按 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![新增 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="fb367-457">[**組建設定**] 中的其餘設定, 現在應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="fb367-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="fb367-458">在相同的視窗中, 按一下 [**玩家設定**] 按鈕, 這會在偵測**器**所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="fb367-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="fb367-459">在此面板中, 需要驗證幾項設定:</span><span class="sxs-lookup"><span data-stu-id="fb367-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="fb367-460">在 [**其他設定**] 索引標籤中:</span><span class="sxs-lookup"><span data-stu-id="fb367-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="fb367-461">**腳本執行階段版本**應該是**實驗性 (.Net 4.6 對等用法)**</span><span class="sxs-lookup"><span data-stu-id="fb367-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="fb367-462">**腳本後端**應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="fb367-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="fb367-463">**API 相容性層級**應該是 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="fb367-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![4.6 net 版本](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="fb367-465">在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:</span><span class="sxs-lookup"><span data-stu-id="fb367-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="fb367-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="fb367-466">**InternetClient**</span></span>

            ![勾選網際網路用戶端](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="fb367-468">回到**組建設定**: *Unity C\#專案*不再呈現灰色; 勾選此旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fb367-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="fb367-469">關閉 [**組建設定**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="fb367-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="fb367-470">儲存場景和專案**檔** > **儲存場景/**  > 檔案**儲存專案**。</span><span class="sxs-lookup"><span data-stu-id="fb367-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fb367-471">如果您想要略過此專案的*Unity 設定*元件 (傳統型應用程式), 並直接繼續執行程式碼, 您可以[下載這個 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), 將它匯入您的專案中做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html), 然後從[一章繼續9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="fb367-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="fb367-472">您仍然需要新增腳本元件。</span><span class="sxs-lookup"><span data-stu-id="fb367-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="fb367-473">第8章-匯入 Unity 中的 Dll</span><span class="sxs-lookup"><span data-stu-id="fb367-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="fb367-474">您將使用適用于 Unity 的 Azure 儲存體 (其本身會利用 .Net SDK for Azure)。</span><span class="sxs-lookup"><span data-stu-id="fb367-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="fb367-475">如需詳細資訊, 請遵循此[關於 Unity Azure 儲存體的連結](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="fb367-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="fb367-476">Unity 中目前有一個已知問題, 需要在匯入後重新設定外掛程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="fb367-477">解決錯誤之後, 將不再需要這些步驟 (本節中的 4-7)。</span><span class="sxs-lookup"><span data-stu-id="fb367-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="fb367-478">若要將 SDK 匯入您自己的專案, 請確定您已從 GitHub 下載最新的[**unitypackage。** ](https://aka.ms/azstorage-unitysdk)</span><span class="sxs-lookup"><span data-stu-id="fb367-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="fb367-479">然後, 執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="fb367-479">Then, do the following:</span></span>

1.  <span data-ttu-id="fb367-480">使用 [資產 **\> ] [匯入套件\> ] [自訂套件**] 功能表選項, 將 unitypackage 新增至 Unity。</span><span class="sxs-lookup"><span data-stu-id="fb367-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="fb367-481">在彈出的 [匯**入 Unity 封裝**] 方塊中, 您可以選取 \* \**外掛程式* \> \* 儲存體 \* \* \* 底下的所有專案。</span><span class="sxs-lookup"><span data-stu-id="fb367-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="fb367-482">取消核取其他所有專案, 因為這個課程並不需要。</span><span class="sxs-lookup"><span data-stu-id="fb367-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![匯入至封裝](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="fb367-484">按一下 [匯***入***] 按鈕, 將專案新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="fb367-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="fb367-485">移至 [專案] 視圖中 [**外掛程式**] 底下的 [**儲存體**] 資料夾, 然後選取 [*僅*下列外掛程式]:</span><span class="sxs-lookup"><span data-stu-id="fb367-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="fb367-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="fb367-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="fb367-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="fb367-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="fb367-488">Windowsazure.storage 儲存體</span><span class="sxs-lookup"><span data-stu-id="fb367-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="fb367-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="fb367-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="fb367-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="fb367-490">System.Spatial</span></span>

![取消核取任何平臺](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="fb367-492">選取*這些特定外掛程式*後,**取消**核取**任何平臺**並**取消**核  取 [ **WSAPlayer** ], 然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="fb367-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![套用平臺 dll](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="fb367-494">我們會將這些特定外掛程式標示為僅在 Unity 編輯器中使用。</span><span class="sxs-lookup"><span data-stu-id="fb367-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="fb367-495">這是因為在從 Unity 匯出專案之後, 將會使用 [WSA] 資料夾中相同外掛程式的不同版本。</span><span class="sxs-lookup"><span data-stu-id="fb367-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="fb367-496">在 [**儲存體**外掛程式] 資料夾中, 只選取:</span><span class="sxs-lookup"><span data-stu-id="fb367-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="fb367-497">Microsoft. Data. 用戶端</span><span class="sxs-lookup"><span data-stu-id="fb367-497">Microsoft.Data.Services.Client</span></span>

        ![dll 的 set 不處理](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="fb367-499">勾選 [**平臺設定**] 底下的 [**不處理**] 方塊, 然後按一下 [套用]。 </span><span class="sxs-lookup"><span data-stu-id="fb367-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![不套用任何處理](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="fb367-501">因為 Unity assembly patcher 在處理此外掛程式時遇到困難, 所以我們將此外掛程式標示為「不處理」。</span><span class="sxs-lookup"><span data-stu-id="fb367-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="fb367-502">外掛程式仍然可以正常執行, 即使尚未處理也一樣。</span><span class="sxs-lookup"><span data-stu-id="fb367-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="fb367-503">第9章-在 Desktop Unity 專案中建立 TableToScene 類別</span><span class="sxs-lookup"><span data-stu-id="fb367-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="fb367-504">您現在需要建立包含程式碼的腳本, 以執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="fb367-505">您需要建立的第一個腳本是**TableToScene**, 它會負責:</span><span class="sxs-lookup"><span data-stu-id="fb367-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="fb367-506">讀取 Azure 資料表中的實體。</span><span class="sxs-lookup"><span data-stu-id="fb367-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="fb367-507">使用資料表資料, 判斷要產生的物件, 以及在哪個位置。</span><span class="sxs-lookup"><span data-stu-id="fb367-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="fb367-508">您需要建立的第二個腳本是**CloudScene**, 它會負責:</span><span class="sxs-lookup"><span data-stu-id="fb367-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="fb367-509">註冊滑鼠左鍵的事件, 讓使用者可以在場景周圍拖曳物件。</span><span class="sxs-lookup"><span data-stu-id="fb367-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="fb367-510">從這個 Unity 場景序列化物件資料, 並將其傳送至 Azure 函數應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="fb367-511">若要建立此類別:</span><span class="sxs-lookup"><span data-stu-id="fb367-511">To create this class:</span></span>

1.  <span data-ttu-id="fb367-512">以滑鼠右鍵按一下位於 [專案] 面板中的 [**資產**] 資料夾、[**建立** > **資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="fb367-513">將資料夾命名為**Scripts**。</span><span class="sxs-lookup"><span data-stu-id="fb367-513">Name the folder **Scripts**.</span></span>

    ![建立腳本資料夾](images/AzureLabs-Lab8-66.png)

    ![建立腳本資料夾2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="fb367-516">按兩下剛才建立的資料夾, 將它開啟。</span><span class="sxs-lookup"><span data-stu-id="fb367-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="fb367-517">在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="fb367-518">將腳本命名為**TableToScene**。</span><span class="sxs-lookup"><span data-stu-id="fb367-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="fb367-519">![新的 c](images/AzureLabs-Lab8-68.png)
    # 腳本![TableToScene 重新命名](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="fb367-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="fb367-520">按兩下腳本以在 Visual Studio 2017 中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="fb367-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="fb367-521">新增下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="fb367-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="fb367-522">在類別內, 插入下列變數:</span><span class="sxs-lookup"><span data-stu-id="fb367-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="fb367-523">在 Azure 入口網站中, 將**accountName**值替換為您的 Azure 儲存體服務名稱, 並將**accountKey**值取代為 Azure 儲存體服務中找到的金鑰值 (請參閱下圖)。</span><span class="sxs-lookup"><span data-stu-id="fb367-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![提取帳戶金鑰](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="fb367-525">現在新增**Start ()** 和**喚醒 ()** 方法, 以初始化類別。</span><span class="sxs-lookup"><span data-stu-id="fb367-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="fb367-526">在**TableToScene**類別中, 新增將從 Azure 資料表中抓取值的方法, 並使用它們在場景中產生適當的基本專案。</span><span class="sxs-lookup"><span data-stu-id="fb367-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="fb367-527">在**TableToScene**類別之外, 您必須定義應用程式用來序列化和還原序列化**資料表實體**的類別。</span><span class="sxs-lookup"><span data-stu-id="fb367-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="fb367-528">在回到 Unity 編輯器之前, 請務必先**儲存**。</span><span class="sxs-lookup"><span data-stu-id="fb367-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="fb367-529">按一下 [階層] 面板中  的**主要攝影機**, 使其屬性顯示在偵測**器**中。</span><span class="sxs-lookup"><span data-stu-id="fb367-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="fb367-530">在 [**腳本**] 資料夾開啟的情況下, 選取腳本**TableToScene**檔案, 並將它拖曳到**主要相機**上。</span><span class="sxs-lookup"><span data-stu-id="fb367-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="fb367-531">結果應如下所示:</span><span class="sxs-lookup"><span data-stu-id="fb367-531">The result should be as below:</span></span>

    ![將腳本新增至主要相機](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="fb367-533">第10章-在 Desktop Unity 專案中建立 CloudScene 類別</span><span class="sxs-lookup"><span data-stu-id="fb367-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="fb367-534">您需要建立的第二個腳本是**CloudScene**, 它會負責:</span><span class="sxs-lookup"><span data-stu-id="fb367-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="fb367-535">註冊滑鼠左鍵的事件, 讓使用者可以在場景周圍拖曳物件。</span><span class="sxs-lookup"><span data-stu-id="fb367-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="fb367-536">從這個 Unity 場景序列化物件資料, 並將其傳送至 Azure 函數應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="fb367-537">若要建立第二個腳本:</span><span class="sxs-lookup"><span data-stu-id="fb367-537">To create the second script:</span></span>

1.  <span data-ttu-id="fb367-538">以滑鼠右鍵按一下 [**腳本**] 資料夾內部, 然後按一下 [**建立**]、[ **C\#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="fb367-539">將腳本命名為**CloudScene**</span><span class="sxs-lookup"><span data-stu-id="fb367-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="fb367-540">![新的 c](images/AzureLabs-Lab8-72.png)
    # 腳本![重新命名 CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="fb367-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="fb367-541">新增下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="fb367-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="fb367-542">插入下列變數:</span><span class="sxs-lookup"><span data-stu-id="fb367-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="fb367-543">在 azure 入口網站中, 以 Azure 函數應用程式服務中找到的 Azure 函數應用程式 URL 取代**azureFunctionEndpoint**值, 如下圖所示:</span><span class="sxs-lookup"><span data-stu-id="fb367-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![取得函式 URL](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="fb367-545">現在新增**Start ()** 和**喚醒 ()** 方法, 以初始化類別。</span><span class="sxs-lookup"><span data-stu-id="fb367-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="fb367-546">在**Update ()** 方法中, 加入下列程式碼以偵測滑鼠輸入並拖曳, 這將會在場景中輪流移動 gameobject。</span><span class="sxs-lookup"><span data-stu-id="fb367-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="fb367-547">如果使用者已拖放物件, 它會將物件的名稱和座標傳遞給**UpdateCloudScene ()** 方法, 這會呼叫 azure 函數應用程式服務, 這會更新 azure 資料表並觸發通知。</span><span class="sxs-lookup"><span data-stu-id="fb367-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="fb367-548">現在, 新增**UpdateCloudScene ()** 方法, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="fb367-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="fb367-549">儲存程式碼並返回 Unity</span><span class="sxs-lookup"><span data-stu-id="fb367-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="fb367-550">將**CloudScene**腳本拖曳到**主要相機**上。</span><span class="sxs-lookup"><span data-stu-id="fb367-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="fb367-551">按一下 [階層] 面板中  的**主要攝影機**, 使其屬性顯示在偵測**器**中。</span><span class="sxs-lookup"><span data-stu-id="fb367-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="fb367-552">在 [**腳本**] 資料夾開啟的情況下, 選取**CloudScene**腳本, 並將它拖曳到**主要相機**上。</span><span class="sxs-lookup"><span data-stu-id="fb367-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="fb367-553">結果應如下所示:</span><span class="sxs-lookup"><span data-stu-id="fb367-553">The result should be as below:</span></span>

        > ![將雲端腳本拖曳到主要相機上](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="fb367-555">第11章-建立 UWP 的桌面專案</span><span class="sxs-lookup"><span data-stu-id="fb367-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="fb367-556">此專案的 Unity 區段所需的全部內容, 現在已完成。</span><span class="sxs-lookup"><span data-stu-id="fb367-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="fb367-557">流覽至 [**組建設定**] ([    > 檔案**組建設定**])。</span><span class="sxs-lookup"><span data-stu-id="fb367-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="fb367-558">從 [**組建設定**] 視窗中, 按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-558">From the **Build Settings** window, click **Build**.</span></span>

    ![組建專案](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="fb367-560">[檔案**瀏覽器**] 視窗隨即彈出, 提示您輸入要建立的位置。</span><span class="sxs-lookup"><span data-stu-id="fb367-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="fb367-561">建立新的資料夾 (按一下左上角的 [**新增資料夾**]), 並將其命名為**build**。</span><span class="sxs-lookup"><span data-stu-id="fb367-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![組建的新資料夾](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="fb367-563">開啟 [新增**組建**] 資料夾, 然後建立另一個資料夾 (使用 [**新增資料夾**] 一次), 並將它命名為 **\_NH Desktop\_App**。</span><span class="sxs-lookup"><span data-stu-id="fb367-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![資料夾名稱 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="fb367-565">已選取**NH\_Desktop\_應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fb367-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="fb367-566">按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-566">click **Select Folder**.</span></span> <span data-ttu-id="fb367-567">專案需要幾分鐘的時間才能建立。</span><span class="sxs-lookup"><span data-stu-id="fb367-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="fb367-568">在下列組建中, 會出現 [檔案**瀏覽器**], 顯示新專案的位置。</span><span class="sxs-lookup"><span data-stu-id="fb367-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="fb367-569">不過, 如果您需要先建立其他 Unity 專案, 請在接下來的幾個章節中, 不需要開啟它。</span><span class="sxs-lookup"><span data-stu-id="fb367-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="fb367-570">第12章-設定混合現實 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="fb367-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="fb367-571">以下是使用混合現實進行開發的一般設定, 因此是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="fb367-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="fb367-572">開啟**Unity** , 然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-572">Open **Unity** and click **New**.</span></span>

    ![新增 unity 專案](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="fb367-574">您現在必須提供 Unity 專案名稱, 並插入**UnityMRNotifHub**。</span><span class="sxs-lookup"><span data-stu-id="fb367-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="fb367-575">請確定 [專案類型] 設定為 [ **3d**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="fb367-576">將位置設定為適合您的**位置**(請記住, 接近根目錄較佳)。</span><span class="sxs-lookup"><span data-stu-id="fb367-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="fb367-577">然後, 按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-577">Then, click **Create project**.</span></span>

    ![名稱 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="fb367-579">在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fb367-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="fb367-580">移至 [**編輯** > **喜好**設定], 然後在新視窗中, 流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="fb367-581">將**外部腳本編輯器**變更為**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="fb367-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="fb367-582">關閉 [**喜好**設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="fb367-582">Close the **Preferences** window.</span></span>

    ![將外部編輯器設為 VS](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="fb367-584">接下來, 移   > 至 [檔案] [**組建設定**], 然後按一下 [**切換平臺**] 按鈕, 將平臺切換至**通用 Windows 平臺**。</span><span class="sxs-lookup"><span data-stu-id="fb367-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![將平臺切換至 UWP](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="fb367-586">移至   > [檔案] [**組建設定**], 並確認:</span><span class="sxs-lookup"><span data-stu-id="fb367-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="fb367-587">**目標裝置**已設定為**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="fb367-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="fb367-588">若為 Microsoft HoloLens, 請將**目標裝置**設定為*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="fb367-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="fb367-589">**組建類型**設定為**D3D**</span><span class="sxs-lookup"><span data-stu-id="fb367-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="fb367-590">**SDK**已設定為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="fb367-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="fb367-591">**Visual Studio 版本**設定為 [**最新安裝**]</span><span class="sxs-lookup"><span data-stu-id="fb367-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="fb367-592">**組建和執行**設定為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="fb367-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="fb367-593">在這裡, 很值得儲存場景, 並將它加入組建。</span><span class="sxs-lookup"><span data-stu-id="fb367-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="fb367-594">選取 [新增] [**開啟場景**] 來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="fb367-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="fb367-595">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="fb367-595">A save window will appear.</span></span>

            ![新增開啟的場景](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="fb367-597">為此建立新的資料夾, 並在任何未來的場景中選取 [**新增資料夾**] 按鈕, 以建立新的資料夾, 將其命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="fb367-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新增背景資料夾](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="fb367-599">開啟新建立的 [**幕後**] 資料夾, 然後在 [**檔案名:** 文字] 欄位中, 輸入**NH\_MR\_場景**, 然後按 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![新場景-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="fb367-601">[**組建設定**] 中的其餘設定, 現在應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="fb367-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="fb367-602">在相同的視窗中, 按一下 [**玩家設定**] 按鈕, 這會在偵測**器**所在的空間中開啟相關的面板。</span><span class="sxs-lookup"><span data-stu-id="fb367-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![開啟播放 [設定]](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="fb367-604">在此面板中, 需要驗證幾項設定:</span><span class="sxs-lookup"><span data-stu-id="fb367-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="fb367-605">在 [**其他設定**] 索引標籤中:</span><span class="sxs-lookup"><span data-stu-id="fb367-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="fb367-606">**腳本執行階段版本**應該是**實驗**性 (.net 4.6 對等用法)</span><span class="sxs-lookup"><span data-stu-id="fb367-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="fb367-607">**腳本後端**應該是 ***.net***</span><span class="sxs-lookup"><span data-stu-id="fb367-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="fb367-608">**API 相容性層級**應該是 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="fb367-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![api 相容性](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="fb367-610">在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]</span><span class="sxs-lookup"><span data-stu-id="fb367-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![更新 xr 設定](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="fb367-612">在 [**發行設定**] 索引標籤的 [**功能**] 底下, 會執行:</span><span class="sxs-lookup"><span data-stu-id="fb367-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="fb367-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="fb367-613">**InternetClient**</span></span>           

            ![勾選網際網路用戶端](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="fb367-615">回到 [**組建設定**] **, C# Unity 專案**已不再呈現灰色: 勾選 [this] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fb367-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="fb367-616">完成這些變更後, 請關閉 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="fb367-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="fb367-617">儲存場景和專案**檔** > **儲存場景/**  > 檔案**儲存專案**。</span><span class="sxs-lookup"><span data-stu-id="fb367-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fb367-618">如果您想要略過*Unity 設定*此專案的元件 (混合現實應用程式), 並直接繼續程式碼, 您可以[下載這個 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), 將它匯入您的專案中做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html), 然後繼續進行[第14章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="fb367-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="fb367-619">您仍然需要新增腳本元件。</span><span class="sxs-lookup"><span data-stu-id="fb367-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="fb367-620">第13章-匯入 Mixed Reality Unity 專案中的 Dll</span><span class="sxs-lookup"><span data-stu-id="fb367-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="fb367-621">您將使用適用于 Unity 程式庫的 Azure 儲存體 (使用適用于 Azure 的 .Net SDK)。</span><span class="sxs-lookup"><span data-stu-id="fb367-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="fb367-622">請遵循此[連結, 以瞭解如何搭配使用 Azure 儲存體與 Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="fb367-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="fb367-623">Unity 中目前有一個已知問題, 需要在匯入後重新設定外掛程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="fb367-624">解決錯誤之後, 將不再需要這些步驟 (本節中的 4-7)。</span><span class="sxs-lookup"><span data-stu-id="fb367-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="fb367-625">若要將 SDK 匯入您自己的專案, 請確定您已下載最新的[unitypackage](https://aka.ms/azstorage-unitysdk)。</span><span class="sxs-lookup"><span data-stu-id="fb367-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="fb367-626">然後, 執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="fb367-626">Then, do the following:</span></span>

1.  <span data-ttu-id="fb367-627">使用 [**資產** > ] [匯**入套件** > ] [**自訂套件**] 功能表選項, 將您從上述下載的 unitypackage 新增至 Unity。</span><span class="sxs-lookup"><span data-stu-id="fb367-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="fb367-628">在彈出的 [匯**入 Unity 封裝**] 方塊中, 您可以選取 [**外掛程式** > ] [**儲存體**] 底下的所有專案。</span><span class="sxs-lookup"><span data-stu-id="fb367-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![匯入套件](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="fb367-630">按一下 [匯**入**] 按鈕, 將專案新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="fb367-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="fb367-631">移至 [專案] 視圖中 [**外掛程式**] 底下的 [**儲存體**] 資料夾, 然後選取 [*僅*下列外掛程式]:</span><span class="sxs-lookup"><span data-stu-id="fb367-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="fb367-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="fb367-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="fb367-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="fb367-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="fb367-634">Windowsazure.storage 儲存體</span><span class="sxs-lookup"><span data-stu-id="fb367-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="fb367-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="fb367-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="fb367-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="fb367-636">System.Spatial</span></span>

    ![選取外掛程式](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="fb367-638">選取*這些特定外掛程式*後,**取消**核取**任何平臺**並**取消**核  取 [ **WSAPlayer** ], 然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="fb367-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![套用平臺變更](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="fb367-640">您要將這些特定外掛程式標示為僅在 Unity 編輯器中使用。</span><span class="sxs-lookup"><span data-stu-id="fb367-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="fb367-641">這是因為在從 Unity 匯出專案之後, 將會使用 [WSA] 資料夾中相同外掛程式的不同版本。</span><span class="sxs-lookup"><span data-stu-id="fb367-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="fb367-642">在 [**儲存體**外掛程式] 資料夾中, 只選取:</span><span class="sxs-lookup"><span data-stu-id="fb367-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="fb367-643">Microsoft. Data. 用戶端</span><span class="sxs-lookup"><span data-stu-id="fb367-643">Microsoft.Data.Services.Client</span></span>

        ![選取資料服務用戶端](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="fb367-645">勾選 [**平臺設定**] 底下的 [**不處理**] 方塊, 然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="fb367-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![不要處理](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="fb367-647">您正在將此外掛程式標示為「不要處理」, 因為 Unity assembly patcher 在處理此外掛程式時發生困難。</span><span class="sxs-lookup"><span data-stu-id="fb367-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="fb367-648">外掛程式仍然可以正常執行, 即使尚未處理也一樣。</span><span class="sxs-lookup"><span data-stu-id="fb367-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="fb367-649">第14章-在 mixed reality Unity 專案中建立 TableToScene 類別</span><span class="sxs-lookup"><span data-stu-id="fb367-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="fb367-650">**TableToScene**類別與第[9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)所述的相同。</span><span class="sxs-lookup"><span data-stu-id="fb367-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="fb367-651">遵循第[9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)所述的相同程式, 在 Mixed Reality Unity 專案中建立相同的類別。</span><span class="sxs-lookup"><span data-stu-id="fb367-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="fb367-652">當您完成這一章之後, 這兩個**Unity 專案**都會在主攝影機上設定此類別。</span><span class="sxs-lookup"><span data-stu-id="fb367-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="fb367-653">第15章-在 Mixed Reality Unity 專案中建立 NotificationReceiver 類別</span><span class="sxs-lookup"><span data-stu-id="fb367-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="fb367-654">您需要建立的第二個腳本是**NotificationReceiver**, 它會負責:</span><span class="sxs-lookup"><span data-stu-id="fb367-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="fb367-655">在初始化時向通知中樞註冊應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="fb367-656">正在接聽來自通知中樞的通知。</span><span class="sxs-lookup"><span data-stu-id="fb367-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="fb367-657">從收到的通知還原序列化物件資料。</span><span class="sxs-lookup"><span data-stu-id="fb367-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="fb367-658">根據還原序列化的資料, 移動場景中的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="fb367-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="fb367-659">若要建立**NotificationReceiver**腳本:</span><span class="sxs-lookup"><span data-stu-id="fb367-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="fb367-660">以滑鼠右鍵按一下 [**腳本**] 資料夾內部, 然後按一下 [**建立**]、[ **C\#腳本**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="fb367-661">將腳本命名為**NotificationReceiver**。</span><span class="sxs-lookup"><span data-stu-id="fb367-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="fb367-662">![建立新的 c](images/AzureLabs-Lab8-95.png)
    # 腳本![名稱 NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="fb367-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="fb367-663">按兩下腳本加以開啟。</span><span class="sxs-lookup"><span data-stu-id="fb367-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="fb367-664">新增下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="fb367-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="fb367-665">插入下列變數:</span><span class="sxs-lookup"><span data-stu-id="fb367-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="fb367-666">將**hubName**值替換為您的通知中樞服務名稱, 並以 Azure 入口網站中 [存取原則] 索引標籤中的 [Azure 通知中樞服務] 中找到的端點值來取代**hubListenEndpoint**值 (請參閱下圖)。</span><span class="sxs-lookup"><span data-stu-id="fb367-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![插入通知中樞原則端點](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="fb367-668">現在新增**Start ()** 和**喚醒 ()** 方法, 以初始化類別。</span><span class="sxs-lookup"><span data-stu-id="fb367-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="fb367-669">新增**WaitForNotification**方法, 以允許應用程式接收來自通知中樞程式庫的通知, 而不衝突與主執行緒:</span><span class="sxs-lookup"><span data-stu-id="fb367-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="fb367-670">下列方法 ( **InitNotificationAsync ())** 會在初始化時向通知中樞服務註冊應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="fb367-671">程式碼已標記為批註, 因為 Unity 將無法建立專案。</span><span class="sxs-lookup"><span data-stu-id="fb367-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="fb367-672">當您在 Visual Studio 中匯入 Azure 訊息 Nuget 套件時, 將會移除批註。</span><span class="sxs-lookup"><span data-stu-id="fb367-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="fb367-673">每次收到通知時, 將會觸發下列處理常式**Channel\_PushNotificationReceived ()** 。</span><span class="sxs-lookup"><span data-stu-id="fb367-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="fb367-674">它會將通知還原序列化, 這會是已移至桌面應用程式的 Azure 資料表實體, 然後將 MR 場景中對應的 GameObject 移到相同的位置。</span><span class="sxs-lookup"><span data-stu-id="fb367-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="fb367-675">程式碼會標記為批註, 因為程式碼會參考 Azure 訊息程式庫, 而您將在 Visual Studio 中使用 Nuget 套件管理員建立 Unity 專案之後, 將會加入此程式庫。</span><span class="sxs-lookup"><span data-stu-id="fb367-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="fb367-676">因此, 除非已標記為批註, 否則 Unity 專案將無法建立。請注意, 如果您要建立專案, 然後想要回到 Unity, 就必須**重新批註**該程式碼。</span><span class="sxs-lookup"><span data-stu-id="fb367-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="fb367-677">請記得儲存您的變更, 然後再回到 Unity 編輯器。</span><span class="sxs-lookup"><span data-stu-id="fb367-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="fb367-678">按一下 [階層] 面板中  的**主要攝影機**, 使其屬性顯示在偵測**器**中。</span><span class="sxs-lookup"><span data-stu-id="fb367-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="fb367-679">在 [**腳本**] 資料夾開啟的情況下, 選取**NotificationReceiver**腳本, 並將它拖曳到**主要相機**上。</span><span class="sxs-lookup"><span data-stu-id="fb367-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="fb367-680">結果應如下所示:</span><span class="sxs-lookup"><span data-stu-id="fb367-680">The result should be as below:</span></span>

    ![將通知接收器腳本拖曳至相機](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="fb367-682">如果您是針對 Microsoft HoloLens 進行開發, 就必須更新**主要相機**的*相機*元件, 這樣才能:</span><span class="sxs-lookup"><span data-stu-id="fb367-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="fb367-683">清除旗標:單色</span><span class="sxs-lookup"><span data-stu-id="fb367-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="fb367-684">背景：黑色</span><span class="sxs-lookup"><span data-stu-id="fb367-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="fb367-685">第16章-建立 UWP 的混合現實專案</span><span class="sxs-lookup"><span data-stu-id="fb367-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="fb367-686">這一章與前一個專案的組建程式相同。</span><span class="sxs-lookup"><span data-stu-id="fb367-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="fb367-687">此專案的 Unity 區段所需的全部內容現在已經完成, 所以可以從 Unity 建立它。</span><span class="sxs-lookup"><span data-stu-id="fb367-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="fb367-688">流覽至 [**組建設定**] ([  > 檔案**組建設定**])。</span><span class="sxs-lookup"><span data-stu-id="fb367-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="fb367-689">從 [**組建設定**] 功能表中, 確定 [ **Unity C#專案**] 已核取 (這可讓您在組建之後編輯此專案中的腳本)。</span><span class="sxs-lookup"><span data-stu-id="fb367-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="fb367-690">完成後, 按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-690">After this is done, click **Build**.</span></span>

    ![組建專案](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="fb367-692">[檔案**瀏覽器**] 視窗隨即彈出, 提示您輸入要建立的位置。</span><span class="sxs-lookup"><span data-stu-id="fb367-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="fb367-693">建立新的資料夾 (按一下左上角的 [**新增資料夾**]), 並將其命名為**build**。</span><span class="sxs-lookup"><span data-stu-id="fb367-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![建立組建資料夾](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="fb367-695">開啟 [新增**組建**] 資料夾, 然後建立另一個資料夾 (使用 [**新增資料夾**] 一次), 並將它命名為 **\_NH MR\_應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fb367-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![建立 NH_MR_Apps 資料夾](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="fb367-697">已選取**NH\_MR\_應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fb367-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="fb367-698">按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-698">click **Select Folder**.</span></span> <span data-ttu-id="fb367-699">專案需要幾分鐘的時間才能建立。</span><span class="sxs-lookup"><span data-stu-id="fb367-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="fb367-700">在組建之後, 會在新專案的位置開啟 [檔案**瀏覽器**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="fb367-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="fb367-701">第17章-將 NuGet 套件新增至 UnityMRNotifHub 解決方案</span><span class="sxs-lookup"><span data-stu-id="fb367-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="fb367-702">請記住, 當您新增下列 NuGet 套件 (並取消下一[章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)中的程式碼) 後, 程式碼在 Unity 專案中重新開啟時, 將會出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="fb367-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="fb367-703">如果您想要返回並繼續在 Unity 編輯器中編輯, 您將需要批註該 errosome 程式碼, 稍後當您回到 Visual Studio 之後, 就會再次取消批註。</span><span class="sxs-lookup"><span data-stu-id="fb367-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="fb367-704">完成混合現實組建之後, 流覽至您所建立的混合現實專案, 然後按兩下該資料夾中的方案 (.sln) 檔案, 以使用 Visual Studio 2017 來開啟您的方案。</span><span class="sxs-lookup"><span data-stu-id="fb367-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="fb367-705">您現在將需要新增**windowsazure.storage 管理**的 NuGet 套件;這是用來接收來自通知中樞之通知的程式庫。</span><span class="sxs-lookup"><span data-stu-id="fb367-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="fb367-706">若要匯入 NuGet 套件:</span><span class="sxs-lookup"><span data-stu-id="fb367-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="fb367-707">在 **方案總管**中, 以滑鼠右鍵按一下您的方案</span><span class="sxs-lookup"><span data-stu-id="fb367-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="fb367-708">按一下 [**管理 NuGet 套件**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-708">Click on **Manage NuGet Packages**.</span></span>

    ![開啟 nuget 管理員](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="fb367-710">選取 [***流覽***] 索引標籤, 並搜尋**windowsazure.storage**。</span><span class="sxs-lookup"><span data-stu-id="fb367-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![尋找 windows azure 訊息封裝](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="fb367-712">選取結果 (如下所示), 然後在右邊的視窗中, 選取 [**專案**] 旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fb367-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="fb367-713">這會在 [**專案**] 旁的核取方塊中加上勾號, 以及 [**元件-CSharp**和**UnityMRNotifHub** ] 專案旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fb367-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![勾選所有專案](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="fb367-715">一開始提供的版本可能與此專案**不**相容。</span><span class="sxs-lookup"><span data-stu-id="fb367-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="fb367-716">因此, 請按一下 [**版本**] 旁的下拉式功能表, 然後按一下 [**版本 0.1.7.9**], 再按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="fb367-717">您現在已完成安裝 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="fb367-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="fb367-718">尋找您在**NotificationReceiver**類別中所輸入的批註程式碼, 並移除留言。</span><span class="sxs-lookup"><span data-stu-id="fb367-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="fb367-719">第18章-編輯 UnityMRNotifHub 應用程式, NotificationReceiver 類別</span><span class="sxs-lookup"><span data-stu-id="fb367-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="fb367-720">新增**NuGet 套件**之後, 您必須將**NotificationReceiver**類別內的部分程式碼*取消*批註。</span><span class="sxs-lookup"><span data-stu-id="fb367-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="fb367-721">這包括：</span><span class="sxs-lookup"><span data-stu-id="fb367-721">This includes:</span></span>

1. <span data-ttu-id="fb367-722">位於頂端的命名空間:</span><span class="sxs-lookup"><span data-stu-id="fb367-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="fb367-723">**InitNotificationsAsync ()** 方法內的所有程式碼:</span><span class="sxs-lookup"><span data-stu-id="fb367-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="fb367-724">上述程式碼在其中有批註: 請確定您不會意外地*取消批註*該批註 (如果您有!, 程式碼不會進行編譯)。</span><span class="sxs-lookup"><span data-stu-id="fb367-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="fb367-725">最後, **Channel_PushNotificationReceived**事件如下:</span><span class="sxs-lookup"><span data-stu-id="fb367-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="fb367-726">使用這些取消批註, 請確定您儲存, 然後繼續進行下一章。</span><span class="sxs-lookup"><span data-stu-id="fb367-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="fb367-727">第19章-將 mixed reality 專案與 Store 應用程式建立關聯</span><span class="sxs-lookup"><span data-stu-id="fb367-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="fb367-728">您現在需要將**mixed reality**專案與您在實驗室開始時所建立的 Store 應用程式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="fb367-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="fb367-729">開啟方案。</span><span class="sxs-lookup"><span data-stu-id="fb367-729">Open the solution.</span></span>

2.  <span data-ttu-id="fb367-730">在 [方案總管] 面板中, 以滑鼠右鍵按一下 UWP 應用程式專案、[移至] [**儲存**], 然後**將 [應用程式與存放區建立關聯**...]。</span><span class="sxs-lookup"><span data-stu-id="fb367-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![開啟存放區關聯](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="fb367-732">隨即會出現一個新視窗 **, 稱為將您的應用程式與 Windows Store 建立關聯**。</span><span class="sxs-lookup"><span data-stu-id="fb367-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="fb367-733">按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="fb367-733">Click **Next**.</span></span>

    ![移至下一個畫面](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="fb367-735">它會載入與您已登入之帳戶相關聯的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="fb367-736">如果您未登入您的帳戶, 您可以在此頁面上**登入**。</span><span class="sxs-lookup"><span data-stu-id="fb367-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="fb367-737">尋找您在本教學課程開始時所建立的**商店應用程式名稱**, 並加以選取。</span><span class="sxs-lookup"><span data-stu-id="fb367-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="fb367-738">然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="fb367-738">Then click **Next**.</span></span>

    ![尋找並選取您的商店名稱](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="fb367-740">按一下 [**關聯**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-740">Click **Associate**.</span></span>

    ![關聯應用程式](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="fb367-742">您的應用程式現在已與 Store 應用程式**相關聯**。</span><span class="sxs-lookup"><span data-stu-id="fb367-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="fb367-743">這是啟用通知的必要動作。</span><span class="sxs-lookup"><span data-stu-id="fb367-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="fb367-744">第20章-部署 UnityMRNotifHub 和 UnityDesktopNotifHub 應用程式</span><span class="sxs-lookup"><span data-stu-id="fb367-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="fb367-745">這一章可能會讓兩個人變得更容易, 因為這會包含兩個執行中的應用程式、一個在電腦桌面上執行, 另一個在您的沉浸式頭戴式裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="fb367-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="fb367-746">沉浸式耳機應用程式正在等候接收場景的變更 (本機 Gameobject 的位置變更), 而桌面應用程式將會對其本機場景 (位置變更) 進行變更, 這將會與 MR 應用程式共用。</span><span class="sxs-lookup"><span data-stu-id="fb367-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="fb367-747">先部署 MR 應用程式, 接著使用桌面應用程式, 讓接收者可以開始接聽, 是合理的做法。</span><span class="sxs-lookup"><span data-stu-id="fb367-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="fb367-748">若要在本機電腦上部署**UnityMRNotifHub**應用程式:</span><span class="sxs-lookup"><span data-stu-id="fb367-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="fb367-749">在**Visual Studio 2017**中開啟**UnityMRNotifHub**應用程式的方案檔。</span><span class="sxs-lookup"><span data-stu-id="fb367-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="fb367-750">在**解決方案平臺**中, 選取 [ **x86]、[本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="fb367-751">在 [**解決方案**設定] 中, 選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![設定專案設定](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="fb367-753">移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="fb367-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="fb367-754">您的應用程式現在應該會出現在已安裝的應用程式清單中, 並準備好啟動。</span><span class="sxs-lookup"><span data-stu-id="fb367-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="fb367-755">若要在本機電腦上部署**UnityDesktopNotifHub**應用程式:</span><span class="sxs-lookup"><span data-stu-id="fb367-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="fb367-756">在**Visual Studio 2017**中開啟**UnityDesktopNotifHub**應用程式的方案檔。</span><span class="sxs-lookup"><span data-stu-id="fb367-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="fb367-757">在**解決方案平臺**中, 選取 [ **x86]、[本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="fb367-758">在 [**解決方案**設定] 中, 選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="fb367-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![設定專案設定](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="fb367-760">移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="fb367-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="fb367-761">您的應用程式現在應該會出現在已安裝的應用程式清單中, 並準備好啟動。</span><span class="sxs-lookup"><span data-stu-id="fb367-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="fb367-762">啟動混合現實應用程式, 後面接著桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb367-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="fb367-763">在兩個應用程式執行的情況下, 在桌面場景中移動物件 (使用滑鼠左鍵)。</span><span class="sxs-lookup"><span data-stu-id="fb367-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="fb367-764">這些位置變更將會在本機進行序列化, 並傳送至函數應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="fb367-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="fb367-765">函數應用程式服務接著會更新資料表以及通知中樞。</span><span class="sxs-lookup"><span data-stu-id="fb367-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="fb367-766">收到更新之後, 通知中樞會將更新的資料直接傳送給所有已註冊的應用程式 (在此案例中為沉浸式耳機應用程式), 然後將傳入的資料還原序列化, 並將新的位置資料套用至本機物件。在場景中移動它們。</span><span class="sxs-lookup"><span data-stu-id="fb367-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="fb367-767">您已完成 Azure 通知中樞應用程式</span><span class="sxs-lookup"><span data-stu-id="fb367-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="fb367-768">恭喜, 您建立了一個混合現實應用程式來利用 Azure 通知中樞服務, 並允許應用程式之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="fb367-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![最終產品結束](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="fb367-770">額外練習</span><span class="sxs-lookup"><span data-stu-id="fb367-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="fb367-771">練習1</span><span class="sxs-lookup"><span data-stu-id="fb367-771">Exercise 1</span></span>

<span data-ttu-id="fb367-772">您是否可以處理如何變更 Gameobject 的色彩, 並將該通知傳送給其他應用程式, 以查看場景？</span><span class="sxs-lookup"><span data-stu-id="fb367-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="fb367-773">練習2</span><span class="sxs-lookup"><span data-stu-id="fb367-773">Exercise 2</span></span>

<span data-ttu-id="fb367-774">您可以新增 Gameobject 至 MR 應用程式的移動, 並查看桌面應用程式中更新的場景嗎？</span><span class="sxs-lookup"><span data-stu-id="fb367-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
