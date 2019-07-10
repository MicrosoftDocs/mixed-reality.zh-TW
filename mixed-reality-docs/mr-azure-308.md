---
title: MR 和 Azure 308-跨裝置通知
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 通知中樞、 Azure Functions 和 Azure 儲存體和資料表。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 通知、 函式、 資料表、 通知中樞、 hololens、 沉浸式 vr
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694610"
---
>[!NOTE]
><span data-ttu-id="46df6-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="46df6-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="46df6-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="46df6-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="46df6-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="46df6-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="46df6-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="46df6-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="46df6-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="46df6-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="46df6-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="46df6-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="46df6-110">MR 和 Azure 308:跨裝置通知</span><span class="sxs-lookup"><span data-stu-id="46df6-110">MR and Azure 308: Cross-device notifications</span></span>

![最終產品-開始](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="46df6-112">在此課程中，您將學習如何使用 Azure 通知中樞、 Azure 資料表和 Azure Functions 的混合的實境應用程式中加入通知中樞功能。</span><span class="sxs-lookup"><span data-stu-id="46df6-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="46df6-113">**Azure 通知中樞**是 Microsoft 的服務，這可讓開發人員作為目標，並個人化推播通知傳送到任何平台，所有電源雲端內。</span><span class="sxs-lookup"><span data-stu-id="46df6-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="46df6-114">這可以有效地讓開發人員與終端使用者進行通訊，或甚至溝通各種應用程式，視案例而定。</span><span class="sxs-lookup"><span data-stu-id="46df6-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="46df6-115">如需詳細資訊，請瀏覽**Azure 通知中樞**[頁面](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)。</span><span class="sxs-lookup"><span data-stu-id="46df6-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="46df6-116">**Azure Functions**是 Microsoft 服務，可讓開發人員執行程式碼片段，'函式'，在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="46df6-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="46df6-117">這可用來將工作委派給雲端，而不是您本機的應用程式，可以有許多優點。</span><span class="sxs-lookup"><span data-stu-id="46df6-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="46df6-118">**Azure Functions**支援數種開發語言，包括 C\#，F\#、 Node.js、 Java 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="46df6-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="46df6-119">如需詳細資訊，請瀏覽**Azure Functions** [頁面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="46df6-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="46df6-120">**Azure 資料表**Microsoft 雲端服務，讓開發人員能夠在雲端中儲存結構化的非 SQL 資料，因此能夠輕鬆存取任何位置。</span><span class="sxs-lookup"><span data-stu-id="46df6-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="46df6-121">服務擁有許多無結構描述的設計，如有需要讓資料表的發展，因此非常大的彈性。</span><span class="sxs-lookup"><span data-stu-id="46df6-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="46df6-122">如需詳細資訊，請瀏覽**Azure 資料表**[頁面](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="46df6-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="46df6-123">完成本課程之後，您會有混合的實境沈浸式耳機應用程式和桌上型電腦應用程式，可以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="46df6-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="46df6-124">桌面電腦應用程式可讓使用者將物件移 2D 空間 （X，Y） 中使用滑鼠。</span><span class="sxs-lookup"><span data-stu-id="46df6-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="46df6-125">移動的 PC 應用程式內的物件將會傳送至雲端，使用 JSON，這將會以字串的格式，其中包含的物件識別碼、 類型，並轉換資訊 （X 和 Y 座標）。</span><span class="sxs-lookup"><span data-stu-id="46df6-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="46df6-126">混合的實境應用程式，具有相同的場景，傳統型應用程式，會收到來自 「 通知中樞 」 服務 （這只是已更新的桌上型電腦應用程式） 的相關物件移動的通知。</span><span class="sxs-lookup"><span data-stu-id="46df6-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="46df6-127">收到通知，其中將包含物件識別碼、 類型和轉換資訊，mixed 的 reality 應用程式會套用至它自己的場景的已接收的資訊。</span><span class="sxs-lookup"><span data-stu-id="46df6-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="46df6-128">在您的應用程式，則您對於如何將整合結果進行設計。</span><span class="sxs-lookup"><span data-stu-id="46df6-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="46df6-129">本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="46df6-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="46df6-130">它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。</span><span class="sxs-lookup"><span data-stu-id="46df6-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="46df6-131">本課程是獨立的教學課程，其中並不直接包含任何其他混合實境實驗室。</span><span class="sxs-lookup"><span data-stu-id="46df6-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="46df6-132">裝置支援</span><span class="sxs-lookup"><span data-stu-id="46df6-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="46df6-133">課程</span><span class="sxs-lookup"><span data-stu-id="46df6-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="46df6-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="46df6-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="46df6-135"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="46df6-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="46df6-136">MR 和 Azure 308:跨裝置通知</span><span class="sxs-lookup"><span data-stu-id="46df6-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="46df6-137">✔️</span><span class="sxs-lookup"><span data-stu-id="46df6-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="46df6-138">✔️</span><span class="sxs-lookup"><span data-stu-id="46df6-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="46df6-139">雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。</span><span class="sxs-lookup"><span data-stu-id="46df6-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="46df6-140">當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="46df6-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="46df6-141">當使用 HoloLens，您可能會發現某些回應語音擷取期間。</span><span class="sxs-lookup"><span data-stu-id="46df6-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46df6-142">先決條件</span><span class="sxs-lookup"><span data-stu-id="46df6-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="46df6-143">本教學課程專為具有基礎經驗的 Unity 開發人員和C#。</span><span class="sxs-lookup"><span data-stu-id="46df6-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="46df6-144">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。</span><span class="sxs-lookup"><span data-stu-id="46df6-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="46df6-145">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊會完全符合您會發現在較新的軟體與以下所列內容.</span><span class="sxs-lookup"><span data-stu-id="46df6-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="46df6-146">我們建議下列的硬體和軟體這堂課程：</span><span class="sxs-lookup"><span data-stu-id="46df6-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="46df6-147">開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發</span><span class="sxs-lookup"><span data-stu-id="46df6-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="46df6-148">Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式</span><span class="sxs-lookup"><span data-stu-id="46df6-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="46df6-149">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="46df6-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="46df6-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="46df6-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="46df6-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="46df6-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="46df6-152">A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式</span><span class="sxs-lookup"><span data-stu-id="46df6-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="46df6-153">網際網路存取 Azure 的安裝程式，並存取通知中樞</span><span class="sxs-lookup"><span data-stu-id="46df6-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="46df6-154">開始之前</span><span class="sxs-lookup"><span data-stu-id="46df6-154">Before you start</span></span>

- <span data-ttu-id="46df6-155">若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。</span><span class="sxs-lookup"><span data-stu-id="46df6-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="46df6-156">您必須是您的 Microsoft 開發人員入口網站和您的應用程式註冊入口網站的擁有者，否則您不會存取中的應用程式的權限[第 2 章](#chapter-2---retrieve-your-new-apps-credentials)。</span><span class="sxs-lookup"><span data-stu-id="46df6-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="46df6-157">第 1-Microsoft 開發人員入口網站建立應用程式</span><span class="sxs-lookup"><span data-stu-id="46df6-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="46df6-158">若要使用**Azure 通知中樞**服務，您必須建立應用程式上 Microsoft 開發人員入口網站中，因為您的應用程式必須進行註冊，使其可以傳送和接收通知。</span><span class="sxs-lookup"><span data-stu-id="46df6-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="46df6-159">登入[Microsoft 開發人員入口網站](https://developer.microsoft.com/dashboard)。</span><span class="sxs-lookup"><span data-stu-id="46df6-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="46df6-160">您必須登入您的 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="46df6-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="46df6-161">從儀表板中，按一下**建立新的應用程式**。</span><span class="sxs-lookup"><span data-stu-id="46df6-161">From the Dashboard, click **Create a new app**.</span></span>

    ![建立應用程式](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="46df6-163">會出現快顯視窗，其中您要為新的應用程式保留名稱。</span><span class="sxs-lookup"><span data-stu-id="46df6-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="46df6-164">在文字方塊中，插入適當的名稱;如果選擇的名稱可用，刻度會出現右邊的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="46df6-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="46df6-165">插入可用名稱之後，按一下**保留產品名稱**快顯視窗的左下方的按鈕。</span><span class="sxs-lookup"><span data-stu-id="46df6-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![反向名稱](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="46df6-167">現在建立應用程式時，您已準備好移至下一步 一章項目。</span><span class="sxs-lookup"><span data-stu-id="46df6-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="46df6-168">第 2-擷取新的應用程式認證</span><span class="sxs-lookup"><span data-stu-id="46df6-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="46df6-169">登入應用程式註冊入口網站中，新的應用程式會列出，而擷取的認證將用來安裝**通知中樞服務**內**Azure 入口網站**。</span><span class="sxs-lookup"><span data-stu-id="46df6-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="46df6-170">瀏覽至[應用程式註冊入口網站](http://apps.dev.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="46df6-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![應用程式註冊入口網站](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="46df6-172">您必須使用您的 Microsoft 帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="46df6-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="46df6-173">這**必須**是用在舊版的 Microsoft 帳戶[章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)，使用 Windows 市集開發人員入口網站。</span><span class="sxs-lookup"><span data-stu-id="46df6-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="46df6-174">您會發現您的應用程式**我的應用程式**一節。</span><span class="sxs-lookup"><span data-stu-id="46df6-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="46df6-175">一旦找到它，按一下它，然後您會前往新頁面，具有應用程式名稱加上**註冊**。</span><span class="sxs-lookup"><span data-stu-id="46df6-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![您新註冊的應用程式](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="46df6-177">捲動註冊頁面，尋找您**應用程式祕密**一節並**封裝 SID**應用程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="46df6-178">用於設定複製**Azure 通知中樞服務**下一步 一章中。</span><span class="sxs-lookup"><span data-stu-id="46df6-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![應用程式祕密](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="46df6-180">章節 3-設定 Azure 入口網站： 建立通知中樞 」 服務</span><span class="sxs-lookup"><span data-stu-id="46df6-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="46df6-181">使用您的應用程式的認證擷取，您需要移至 Azure 入口網站中，您將在其中建立 Azure 通知中樞服務。</span><span class="sxs-lookup"><span data-stu-id="46df6-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="46df6-182">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="46df6-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="46df6-183">如果您還沒有 Azure 帳戶，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="46df6-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="46df6-184">如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。</span><span class="sxs-lookup"><span data-stu-id="46df6-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="46df6-185">一旦您登入，按一下**新增**在左上角，，然後搜尋**通知中樞**，然後按一下***Enter***。</span><span class="sxs-lookup"><span data-stu-id="46df6-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![通知中樞的搜尋](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="46df6-187">單字***的新***可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="46df6-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="46df6-188">新的頁面將提供的描述*通知中樞*服務。</span><span class="sxs-lookup"><span data-stu-id="46df6-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="46df6-189">在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="46df6-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![建立通知中樞執行個體](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="46df6-191">一旦您按下 ***建立*** :</span><span class="sxs-lookup"><span data-stu-id="46df6-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="46df6-192">插入您想要的名稱，此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="46df6-193">提供**命名空間**您會將與此應用程式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="46df6-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="46df6-194">選取**位置。**</span><span class="sxs-lookup"><span data-stu-id="46df6-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="46df6-195">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="46df6-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="46df6-196">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="46df6-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="46df6-197">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="46df6-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="46df6-198">如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="46df6-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="46df6-199">選取適當**訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="46df6-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="46df6-200">您也必須確認您已了解這些條款和條件套用到此服務。</span><span class="sxs-lookup"><span data-stu-id="46df6-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="46df6-201">選取 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="46df6-201">Select **Create**.</span></span>

        ![填寫 服務詳細資料](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="46df6-203">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="46df6-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="46df6-204">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![通知](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="46df6-206">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="46df6-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="46df6-207">您將會被重新導向至新**通知中樞**服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![前往資源](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="46df6-209">從 概觀 頁面的中途頁面上，按一下  **Windows (WNS)。**</span><span class="sxs-lookup"><span data-stu-id="46df6-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="46df6-210">在右側面板會顯示兩個文字欄位，需要變更您**封裝 SID**並**安全性金鑰**，從您先前設定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![新建立的中樞服務](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="46df6-212">一旦您正確的欄位複製的詳細資訊，請按一下**儲存**，而且已成功更新通知中樞時，您會收到通知。</span><span class="sxs-lookup"><span data-stu-id="46df6-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![複製安全性詳細資料](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="46df6-214">章節 4-設定 Azure 入口網站： 建立表格服務</span><span class="sxs-lookup"><span data-stu-id="46df6-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="46df6-215">建立您的通知中樞 」 服務執行個體之後, 瀏覽回到您的 Azure 入口網站，您將在其中建立儲存體資源建立 Azure 資料表服務。</span><span class="sxs-lookup"><span data-stu-id="46df6-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="46df6-216">如果您尚未登入，登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="46df6-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="46df6-217">登入之後，按一下**新增**在左上角，，然後搜尋**儲存體帳戶**，然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="46df6-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="46df6-218">單字***的新***可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="46df6-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="46df6-219">選取 **儲存體帳戶-blob、 檔案、 資料表、 佇列**從清單中。</span><span class="sxs-lookup"><span data-stu-id="46df6-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![搜尋儲存體帳戶](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="46df6-221">新的頁面將提供的描述**儲存體帳戶**服務。</span><span class="sxs-lookup"><span data-stu-id="46df6-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="46df6-222">在此提示，選取的左下方**建立**按鈕，以建立此服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="46df6-224">一旦您按下**建立**，面板會顯示：</span><span class="sxs-lookup"><span data-stu-id="46df6-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="46df6-225">插入您想要**名稱**（必須是全部小寫） 此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="46df6-226">針對**部署模型**，按一下**Resource manager**。</span><span class="sxs-lookup"><span data-stu-id="46df6-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="46df6-227">針對**帳戶種類**，使用下拉式功能表，選取**儲存體 (一般用途 v1)** 。</span><span class="sxs-lookup"><span data-stu-id="46df6-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="46df6-228">選取適當**位置**。</span><span class="sxs-lookup"><span data-stu-id="46df6-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="46df6-229">針對**複寫**下拉式功能表中，選取**讀取-存取-異地備援儲存體 (RA-GRS)** 。</span><span class="sxs-lookup"><span data-stu-id="46df6-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="46df6-230">針對**效能**，按一下**標準**。</span><span class="sxs-lookup"><span data-stu-id="46df6-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="46df6-231">內**需要安全傳輸**區段中，選取**停用**。</span><span class="sxs-lookup"><span data-stu-id="46df6-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="46df6-232">從**訂用帳戶**下拉式功能表中，選取適當的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="46df6-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="46df6-233">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="46df6-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="46df6-234">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="46df6-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="46df6-235">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="46df6-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="46df6-236">如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="46df6-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="46df6-237">離開**虛擬網路**作為**停用**如果這是您的選項。</span><span class="sxs-lookup"><span data-stu-id="46df6-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="46df6-238">按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="46df6-238">Click **Create**.</span></span>

        ![填入儲存體詳細資料](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="46df6-240">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="46df6-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="46df6-241">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="46df6-242">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-242">Click on the notifications to explore your new Service instance.</span></span>

    ![新的儲存體通知](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="46df6-244">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="46df6-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="46df6-245">您將會進入您新的儲存體服務執行個體概觀 頁面。</span><span class="sxs-lookup"><span data-stu-id="46df6-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![前往資源](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="46df6-247">從 [概觀] 頁面的右手邊的側邊，按一下**資料表**。</span><span class="sxs-lookup"><span data-stu-id="46df6-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="46df6-248">在右側面板會變更以顯示**表格服務**資訊，您要在其中加入新的資料表。</span><span class="sxs-lookup"><span data-stu-id="46df6-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="46df6-249">依序按一下 **+** **表格**左上角的按鈕。</span><span class="sxs-lookup"><span data-stu-id="46df6-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![開啟資料表](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="46df6-251">新的頁面將會顯示，您要在其中輸入**資料表名稱**。</span><span class="sxs-lookup"><span data-stu-id="46df6-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="46df6-252">這是您用來在您的應用程式，在後續章節中的資料所參考的名稱。</span><span class="sxs-lookup"><span data-stu-id="46df6-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="46df6-253">插入適當的名稱，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="46df6-253">Insert an appropriate name and click **OK**.</span></span>

    ![建立新的資料表](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="46df6-255">一旦建立新的資料表，您將能夠看到它內**表格服務**頁面 （位於底部）。</span><span class="sxs-lookup"><span data-stu-id="46df6-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![建立新資料表](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="46df6-257">第 5 章-完成 Visual Studio 中的 Azure 資料表</span><span class="sxs-lookup"><span data-stu-id="46df6-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="46df6-258">既然您**表格服務**儲存體帳戶是否已設定，就可以開始將資料加入至它，將會用來儲存和擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="46df6-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="46df6-259">編輯您的資料表可透過**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="46df6-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="46df6-260">開啟**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="46df6-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="46df6-261">從功能表中，按一下**檢視** > **Cloud Explorer**。</span><span class="sxs-lookup"><span data-stu-id="46df6-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![開啟 cloud explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="46df6-263">**Cloud Explorer**會開啟為停駐項目 （耐心等候，因為載入可能會花費的時間）。</span><span class="sxs-lookup"><span data-stu-id="46df6-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="46df6-264">如果您用來建立訂用帳戶您*儲存體帳戶*不可見，請確定您已：</span><span class="sxs-lookup"><span data-stu-id="46df6-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="46df6-265">與您在 Azure 入口網站使用相同的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="46df6-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="46df6-266">從 [帳戶] 管理頁面 （您可能需要從您的帳戶設定套用篩選），選取您的訂用帳戶：</span><span class="sxs-lookup"><span data-stu-id="46df6-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![尋找訂用帳戶](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="46df6-268">Azure 雲端服務將會顯示。</span><span class="sxs-lookup"><span data-stu-id="46df6-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="46df6-269">尋找**儲存體帳戶**按一下箭號左側，展開您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="46df6-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![開啟儲存體帳戶](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="46df6-271">一旦展開時，您新建立**儲存體帳戶**應該可用。</span><span class="sxs-lookup"><span data-stu-id="46df6-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="46df6-272">按一下您的儲存體中，左邊的箭號之後，會展開，然後尋找**資料表**，按一下，以顯示旁的箭號**資料表**在最後一章中所建立。</span><span class="sxs-lookup"><span data-stu-id="46df6-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="46df6-273">按兩下您**資料表**。</span><span class="sxs-lookup"><span data-stu-id="46df6-273">Double click your **Table**.</span></span>

    ![開啟場景物件的資料表](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="46df6-275">您的資料表將會開啟您的 Visual Studio 視窗中央。</span><span class="sxs-lookup"><span data-stu-id="46df6-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="46df6-276">按一下 [資料表] 圖示，以 **+** （加上） 在其上。</span><span class="sxs-lookup"><span data-stu-id="46df6-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![加入新的資料表](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="46df6-278">接著會出現視窗提示要*新增實體*。</span><span class="sxs-lookup"><span data-stu-id="46df6-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="46df6-279">您將建立三個實體中每個都有數個屬性的總計。</span><span class="sxs-lookup"><span data-stu-id="46df6-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="46df6-280">您將會發現*PartitionKey*並*RowKey*已提供，這些資料表所用來尋找您的資料。</span><span class="sxs-lookup"><span data-stu-id="46df6-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![資料分割和資料列索引鍵](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="46df6-282">更新*值*的**PartitionKey**並**RowKey** ，如下所示 (請記住，若要這樣做為您新增時，每個資料列屬性但每次遞增 RowKey):</span><span class="sxs-lookup"><span data-stu-id="46df6-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![加入正確的值](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="46df6-284">按一下 **將屬性加入**新增額外的資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="46df6-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="46df6-285">讓您比對的第一個空白資料表下表。</span><span class="sxs-lookup"><span data-stu-id="46df6-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="46df6-286">按一下 **確定**完畢時。</span><span class="sxs-lookup"><span data-stu-id="46df6-286">Click **OK** when you are finished.</span></span>

    ![完成時，請按一下 [確定]](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="46df6-288">請確定您已變更**型別**的**X**， **Y**，以及**Z**，項目，以**Double**。</span><span class="sxs-lookup"><span data-stu-id="46df6-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="46df6-289">您會發現您的資料表現在有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="46df6-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="46df6-290">按一下 [ **+** （加號）] 圖示以新增另一個實體。</span><span class="sxs-lookup"><span data-stu-id="46df6-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![第一個資料列](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="46df6-292">建立一個額外的屬性，然後將 新實體，以符合那些如下所示的值。</span><span class="sxs-lookup"><span data-stu-id="46df6-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![新增 cube](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="46df6-294">重複最後一個步驟，以新增另一個實體。</span><span class="sxs-lookup"><span data-stu-id="46df6-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="46df6-295">設定此實體的值，如下所示。</span><span class="sxs-lookup"><span data-stu-id="46df6-295">Set the values for this entity to those shown below.</span></span>

    ![加入圓柱圖](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="46df6-297">您的資料表現在看起來應該像下面這樣。</span><span class="sxs-lookup"><span data-stu-id="46df6-297">Your table should now look like the one below.</span></span>

    ![完整的資料表](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="46df6-299">您已完成這一章。</span><span class="sxs-lookup"><span data-stu-id="46df6-299">You have completed this Chapter.</span></span> <span data-ttu-id="46df6-300">請務必儲存。</span><span class="sxs-lookup"><span data-stu-id="46df6-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="46df6-301">章節 6-建立 Azure 函式應用程式</span><span class="sxs-lookup"><span data-stu-id="46df6-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="46df6-302">建立 Azure 函數應用程式，若要更新的桌面應用程式會呼叫**表格**服務，並將傳送的通知**通知中樞**。</span><span class="sxs-lookup"><span data-stu-id="46df6-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="46df6-303">首先，您必須建立一個檔案，可讓您的 Azure 函式，將您所需的程式庫。</span><span class="sxs-lookup"><span data-stu-id="46df6-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="46df6-304">開啟**記事本**（按 Windows 鍵和型別 [記事本]）。</span><span class="sxs-lookup"><span data-stu-id="46df6-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![開啟 [記事本]](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="46df6-306">使用 「 記事本 」 開啟，在其中插入以下的 JSON 結構。</span><span class="sxs-lookup"><span data-stu-id="46df6-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="46df6-307">完成後，會將它儲存為您的桌面上**project.json**。</span><span class="sxs-lookup"><span data-stu-id="46df6-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="46df6-308">請務必確認名稱是否正確： 請確定它會**沒有.txt**副檔名。</span><span class="sxs-lookup"><span data-stu-id="46df6-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="46df6-309">如果您使用過它看起來會類似的 NuGet，此檔案會定義將使用您的函式，程式庫。</span><span class="sxs-lookup"><span data-stu-id="46df6-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

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

3.  <span data-ttu-id="46df6-310">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="46df6-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="46df6-311">一旦您登入，按一下**新增**在左上角，，然後搜尋**函式應用程式**、 按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="46df6-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![搜尋函式應用程式](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="46df6-313">單字**的新**可能已取代為**建立資源**，較新的入口網站中。</span><span class="sxs-lookup"><span data-stu-id="46df6-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="46df6-314">新的頁面將提供的描述**函式應用程式**服務。</span><span class="sxs-lookup"><span data-stu-id="46df6-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="46df6-315">在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="46df6-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![函式應用程式執行個體](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="46df6-317">一旦您按下**建立**，填入下列：</span><span class="sxs-lookup"><span data-stu-id="46df6-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="46df6-318">針對**應用程式名稱**，插入您想要的名稱，此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="46df6-319">選取 **訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="46df6-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="46df6-320">選取定價層適合您，如果這是第一次建立**函式應用程式服務**，免費層應該是您可以使用。</span><span class="sxs-lookup"><span data-stu-id="46df6-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="46df6-321">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="46df6-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="46df6-322">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="46df6-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="46df6-323">建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。</span><span class="sxs-lookup"><span data-stu-id="46df6-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="46df6-324">如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="46df6-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="46df6-325">針對**OS**，按一下 Windows，因為這是預期的平台。</span><span class="sxs-lookup"><span data-stu-id="46df6-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="46df6-326">選取 **主控方案**(使用本教學課程**取用方案**。</span><span class="sxs-lookup"><span data-stu-id="46df6-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="46df6-327">選取 **位置** **（上一個步驟中選擇您已建立的儲存體相同的位置）**</span><span class="sxs-lookup"><span data-stu-id="46df6-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="46df6-328">針對**儲存體**一節**您必須選取您在上一個步驟中建立的儲存體服務**。</span><span class="sxs-lookup"><span data-stu-id="46df6-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="46df6-329">您不需要*Application Insights*在此應用程式，因此您將它保留**關閉**。</span><span class="sxs-lookup"><span data-stu-id="46df6-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="46df6-330">按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="46df6-330">Click **Create**.</span></span>

        ![建立新的執行個體](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="46df6-332">一旦您按下**建立**您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="46df6-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="46df6-333">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新的通知](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="46df6-335">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="46df6-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="46df6-336">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="46df6-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![前往資源](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="46df6-338">按一下  **+** （加號） 旁的圖示*函式*至*新建*。</span><span class="sxs-lookup"><span data-stu-id="46df6-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![新增新的函式](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="46df6-340">在中央窗格中，**函式**建立視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="46df6-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="46df6-341">忽略的窗格中，上半部中的資訊，然後按一下**自訂函式**，位在靠近底部 （在藍色區域中，如下所示）。</span><span class="sxs-lookup"><span data-stu-id="46df6-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![自訂函式](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="46df6-343">在視窗內新的頁面會顯示各種函式類型。</span><span class="sxs-lookup"><span data-stu-id="46df6-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="46df6-344">向下捲動以檢視紫色的類型，然後按一下**HTTP PUT**項目。</span><span class="sxs-lookup"><span data-stu-id="46df6-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![http put 連結](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="46df6-346">您可能要進一步向下捲動一頁 （和此映像可能不看起來完全相同，如果您尚未執行 Azure 入口網站更新），不過，您要尋找的項目呼叫*HTTP PUT*。</span><span class="sxs-lookup"><span data-stu-id="46df6-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="46df6-347">**HTTP PUT**視窗會出現，您要設定函式 （請參閱下方的映像）。</span><span class="sxs-lookup"><span data-stu-id="46df6-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="46df6-348">針對**語言**使用下拉式功能表中，選取 C\#。</span><span class="sxs-lookup"><span data-stu-id="46df6-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="46df6-349">針對**名稱，** 輸入適當的名稱。</span><span class="sxs-lookup"><span data-stu-id="46df6-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="46df6-350">在 **驗證層級**下拉式功能表中，選取**函式**。</span><span class="sxs-lookup"><span data-stu-id="46df6-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="46df6-351">針對**資料表名稱**區段中，您需要使用您用來建立的確切名稱您**資料表**服務先前 （包括相同的字母大小寫）。</span><span class="sxs-lookup"><span data-stu-id="46df6-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="46df6-352">內**儲存體帳戶連線**區段中，使用下拉式功能表，然後從該處選取儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="46df6-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="46df6-353">如果那里，按一下**新增**與區段標題，以顯示另一個面板，應該會列出您的儲存體帳戶的超連結。</span><span class="sxs-lookup"><span data-stu-id="46df6-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![新的儲存體](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="46df6-355">按一下 **建立**而且您會收到通知，您的設定已成功更新。</span><span class="sxs-lookup"><span data-stu-id="46df6-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![建立函式](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="46df6-357">按一下後**建立**，您會被重新導向至函式編輯器。</span><span class="sxs-lookup"><span data-stu-id="46df6-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![更新函式程式碼](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="46df6-359">（取代函式中的程式碼） 的函式編輯器中插入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="46df6-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

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
    > <span data-ttu-id="46df6-360">使用內含的程式庫，在函數收到的名稱和位置的物件已移動的 Unity 場景中 (做為C#物件，稱為**UnityGameObject**)。</span><span class="sxs-lookup"><span data-stu-id="46df6-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="46df6-361">這個物件接著會用來更新物件內的參數建立的資料表中。</span><span class="sxs-lookup"><span data-stu-id="46df6-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="46df6-362">在此之後，函式可讓您建立的通知中樞服務，就會通知所有訂閱的應用程式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="46df6-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="46df6-363">中位置的程式碼，請按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="46df6-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="46df6-364">接下來，按一下 **\<** （箭頭） 圖示，在頁面的右手邊。</span><span class="sxs-lookup"><span data-stu-id="46df6-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![開啟上傳 面板](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="46df6-366">從右邊的窗格中將投影片。</span><span class="sxs-lookup"><span data-stu-id="46df6-366">A panel will slide in from the right.</span></span> <span data-ttu-id="46df6-367">在該面板中，按一下**上傳**，檔案瀏覽器將會出現。</span><span class="sxs-lookup"><span data-stu-id="46df6-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="46df6-368">瀏覽至，然後按一下 []， **project.json**中建立的檔案**記事本**之前，然後按一下 [**開啟**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="46df6-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="46df6-369">此檔案會定義您的函式會使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="46df6-369">This file defines the libraries that your function will use.</span></span>

    ![上傳 json](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="46df6-371">檔案已上傳時，它會出現在右側面板。</span><span class="sxs-lookup"><span data-stu-id="46df6-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="46df6-372">按一下將內開啟它**函式**編輯器。</span><span class="sxs-lookup"><span data-stu-id="46df6-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="46df6-373">它必須看起來**完全**下一步 的映像 （下面步驟 23） 相同。</span><span class="sxs-lookup"><span data-stu-id="46df6-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="46df6-374">然後，在左側面板下方**函式**，按一下**整合**連結。</span><span class="sxs-lookup"><span data-stu-id="46df6-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![整合函式](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="46df6-376">在下一步 頁面上，在右上角，按一下**進階的編輯器**（如下）。</span><span class="sxs-lookup"><span data-stu-id="46df6-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![開啟進階編輯器](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="46df6-378">A **function.json**檔案將會開啟在中央窗格中，必須以下列程式碼片段取代。</span><span class="sxs-lookup"><span data-stu-id="46df6-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="46df6-379">這會定義您要建置的函式和參數傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="46df6-379">This defines the function you are building and the parameters passed into the function.</span></span>

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

26. <span data-ttu-id="46df6-380">您的編輯器現在看起來應該類似下面的影像：</span><span class="sxs-lookup"><span data-stu-id="46df6-380">Your editor should now look like the image below:</span></span>

    ![回到標準編輯器](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="46df6-382">您可能會注意到您剛插入的輸入的參數可能不符合您的資料表和儲存體詳細資料，因此將需要使用您的資訊來更新。</span><span class="sxs-lookup"><span data-stu-id="46df6-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="46df6-383">**請不要這樣這裡**，如接下來指涵蓋。</span><span class="sxs-lookup"><span data-stu-id="46df6-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="46df6-384">只要按一下**標準編輯器**連結，頁面上，若要返回右上角。</span><span class="sxs-lookup"><span data-stu-id="46df6-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="46df6-385">回到**標準編輯器**，按一下**Azure 資料表儲存體 （資料表）** 下方**輸入**。</span><span class="sxs-lookup"><span data-stu-id="46df6-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![資料表輸入](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="46df6-387">請確定下列比對**您**的詳細資訊，因為它們可能會不同 （沒有下列步驟的映像）：</span><span class="sxs-lookup"><span data-stu-id="46df6-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="46df6-388">**資料表名稱**： 您在 Azure 儲存體，資料表服務內建立的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="46df6-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="46df6-389">**儲存體帳戶連接：** 按一下 **新**旁下拉式功能表中，會出現，面板會顯示視窗的右邊。</span><span class="sxs-lookup"><span data-stu-id="46df6-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![新的儲存體](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="46df6-391">選取您**儲存體帳戶**，您先前建立到主機**函式應用程式。**</span><span class="sxs-lookup"><span data-stu-id="46df6-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="46df6-392">您將會發現**儲存體帳戶**已建立連接值。</span><span class="sxs-lookup"><span data-stu-id="46df6-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="46df6-393">請務必按下**儲存**完成之後。</span><span class="sxs-lookup"><span data-stu-id="46df6-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="46df6-394">**輸入**頁面上現在應該符合下面顯示**您**資訊。</span><span class="sxs-lookup"><span data-stu-id="46df6-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![完整的輸入](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="46df6-396">接下來，按一下 **（通知） 的 Azure 通知中樞**-底下**輸出**。</span><span class="sxs-lookup"><span data-stu-id="46df6-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="46df6-397">請確認下列與進行比對**您**的詳細資訊，因為它們可能會不同 （沒有下列步驟的映像）：</span><span class="sxs-lookup"><span data-stu-id="46df6-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="46df6-398">**通知中樞名稱**： 這是名稱您**通知中樞**服務執行個體，您在先前所建立。</span><span class="sxs-lookup"><span data-stu-id="46df6-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="46df6-399">**通知中樞命名空間連線**： 按一下 **新**，旁邊的下拉式清單中的功能表會出現。</span><span class="sxs-lookup"><span data-stu-id="46df6-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![檢查輸出](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="46df6-401">**連接**快顯視窗會出現 （請參閱下圖），您要選取**命名空間**的**通知中樞**，其中您先前設定。</span><span class="sxs-lookup"><span data-stu-id="46df6-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="46df6-402">選取您**通知中樞**從中間的下拉式清單中的功能表名稱。</span><span class="sxs-lookup"><span data-stu-id="46df6-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="46df6-403">設定**原則**下拉式功能表， **DefaultFullSharedAccessSignature**。</span><span class="sxs-lookup"><span data-stu-id="46df6-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="46df6-404">按一下 [**選取**返回] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="46df6-404">Click the **Select** button to go back.</span></span>

        ![更新輸出](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="46df6-406">**輸出**頁面上現在應該符合以下，但**您**資訊改為。</span><span class="sxs-lookup"><span data-stu-id="46df6-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="46df6-407">請務必按下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="46df6-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="46df6-408">*請勿直接編輯的通知中樞名稱*(這所有應該使用**進階編輯器**，前提是您正確地遵循上述步驟。</span><span class="sxs-lookup"><span data-stu-id="46df6-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![完整的輸出](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="46df6-410">此時，您應該測試函式，以確保其正常運作。</span><span class="sxs-lookup"><span data-stu-id="46df6-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="46df6-411">請這樣做：</span><span class="sxs-lookup"><span data-stu-id="46df6-411">To do this:</span></span> 

    1. <span data-ttu-id="46df6-412">瀏覽至函式頁面一次：</span><span class="sxs-lookup"><span data-stu-id="46df6-412">Navigate to the function page once more:</span></span>

        ![完整的輸出](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="46df6-414">返回 [函式] 頁面中，按一下 [**測試**] 索引標籤上，請在頁面上，開啟最右端*測試*刀鋒視窗中：</span><span class="sxs-lookup"><span data-stu-id="46df6-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![完整的輸出](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="46df6-416">內**要求本文**文字方塊中的刀鋒視窗中，貼上下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="46df6-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

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

    4. <span data-ttu-id="46df6-417">使用就地測試程式碼中，按一下**執行**右下方，以及測試 按鈕將會執行。</span><span class="sxs-lookup"><span data-stu-id="46df6-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="46df6-418">測試的輸出記錄檔會出現在 [主控台] 區域中，您的函式程式碼下方。</span><span class="sxs-lookup"><span data-stu-id="46df6-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![完整的輸出](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="46df6-420">如果上述的測試失敗，您必須再次檢查您已遵循上述步驟，特別是在設定**整合面板**。</span><span class="sxs-lookup"><span data-stu-id="46df6-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="46df6-421">第 7 章-設定桌面 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="46df6-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46df6-422">您現在正在建立的桌面應用程式**不會**在 Unity 編輯器中工作。</span><span class="sxs-lookup"><span data-stu-id="46df6-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="46df6-423">它必須執行外部編輯器中，遵循建置的應用程式中，然後再使用 Visual Studio （或已部署的應用程式）。</span><span class="sxs-lookup"><span data-stu-id="46df6-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="46df6-424">下列使用 Unity 進行開發及混合的實境，由一組典型，此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="46df6-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="46df6-425">設定並測試您的混合的實境沈浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="46df6-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="46df6-426">您將會**不**本課程所需動作的控制器。</span><span class="sxs-lookup"><span data-stu-id="46df6-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="46df6-427">如果您需要支援沈浸式耳機的設定，請遵循此[連結，有關如何設定 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="46df6-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="46df6-428">開啟**Unity**然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="46df6-428">Open **Unity** and click **New**.</span></span>

    ![新的 unity 專案](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="46df6-430">您需要提供 Unity 專案名稱、 插入**UnityDesktopNotifHub**。</span><span class="sxs-lookup"><span data-stu-id="46df6-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="46df6-431">請確定專案類型設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="46df6-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="46df6-432">設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="46df6-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="46df6-433">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="46df6-433">Then, click **Create project**.</span></span>

    ![建立專案](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="46df6-435">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="46df6-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="46df6-436">移至**編輯** > **喜好設定**並從新的視窗，然後瀏覽至**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="46df6-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="46df6-437">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="46df6-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="46df6-438">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="46df6-438">Close the **Preferences** window.</span></span>

    ![設定外部的 VS 工具](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="46df6-440">接下來，移至**檔案** > **組建設定**，然後選取**通用 Windows 平台**，然後按一下 **切換平台**按鈕以套用您的選擇。</span><span class="sxs-lookup"><span data-stu-id="46df6-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![切換平台](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="46df6-442">當您依然在**檔案** > **組建設定**，請確定：</span><span class="sxs-lookup"><span data-stu-id="46df6-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="46df6-443">**裝置為目標**設為**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="46df6-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="46df6-444">此應用程式將會為您的桌面，因此必須**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="46df6-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="46df6-445">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="46df6-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="46df6-446">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="46df6-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="46df6-447">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="46df6-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="46df6-448">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="46df6-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="46df6-449">在這裡值得儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="46df6-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="46df6-450">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="46df6-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="46df6-451">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="46df6-451">A save window will appear.</span></span>

            ![將開啟的場景新增](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="46df6-453">建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="46df6-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新的場景資料夾](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="46df6-455">開啟您剛建立**場景**資料夾，然後在**檔案名稱：** 文字欄位中輸入**NH\_Desktop\_場景**，然後按**儲存**。</span><span class="sxs-lookup"><span data-stu-id="46df6-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![新的 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="46df6-457">剩餘的設定，**組建設定**，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="46df6-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="46df6-458">在相同的視窗中按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。</span><span class="sxs-lookup"><span data-stu-id="46df6-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="46df6-459">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="46df6-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="46df6-460">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="46df6-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="46df6-461">**指令碼執行階段版本**應該是**實驗性 （.NET 4.6 對等）**</span><span class="sxs-lookup"><span data-stu-id="46df6-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="46df6-462">**指令碼後端**應該是 **.NET**</span><span class="sxs-lookup"><span data-stu-id="46df6-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="46df6-463">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="46df6-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![4.6 的.net 版本](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="46df6-465">內**發佈設定**索引標籤之下**功能**，檢查：</span><span class="sxs-lookup"><span data-stu-id="46df6-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="46df6-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="46df6-466">**InternetClient**</span></span>

            ![刻度網際網路用戶端](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="46df6-468">回到**Build Settings** *Unity C\#專案*不再呈現灰色，這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="46df6-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="46df6-469">關閉**組建設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="46df6-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="46df6-470">儲存您的場景和專案**檔案** > **儲存場景檔案** > **儲存專案**。</span><span class="sxs-lookup"><span data-stu-id="46df6-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="46df6-471">如果您想要跳過*Unity 設定*元件 （桌面應用程式），此專案並繼續直接進入程式碼，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)，它匯入到您的專案做為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="46df6-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="46df6-472">您仍必須新增指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="46df6-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="46df6-473">第 8 章-匯入 Unity 中的 Dll</span><span class="sxs-lookup"><span data-stu-id="46df6-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="46df6-474">您將針對 Unity 使用 Azure 儲存體 （而其本身會利用.Net SDK for Azure）。</span><span class="sxs-lookup"><span data-stu-id="46df6-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="46df6-475">如需詳細資訊請遵循這[解 Unity 的 Azure 儲存體的連結](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="46df6-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="46df6-476">這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。</span><span class="sxs-lookup"><span data-stu-id="46df6-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="46df6-477">這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。</span><span class="sxs-lookup"><span data-stu-id="46df6-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="46df6-478">若要 SDK 匯入您自己的專案，請確定您已下載最新[ **.unitypackage** ](https://aka.ms/azstorage-unitysdk)從 GitHub。</span><span class="sxs-lookup"><span data-stu-id="46df6-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="46df6-479">然後，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="46df6-479">Then, do the following:</span></span>

1.  <span data-ttu-id="46df6-480">新增 **.unitypackage**若要使用的 Unity**資產\>匯入封裝\>自訂封裝**功能表選項。</span><span class="sxs-lookup"><span data-stu-id="46df6-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="46df6-481">在 **匯入 Unity 封裝**方塊，顯示，您可以選取下方的所有內容 \* \**外掛程式* \> \* 儲存 \* \* \*。</span><span class="sxs-lookup"><span data-stu-id="46df6-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="46df6-482">取消選取所有項目不需要這堂課程。</span><span class="sxs-lookup"><span data-stu-id="46df6-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![匯入封裝](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="46df6-484">按一下 ***匯入***按鈕以新增至您的專案項目。</span><span class="sxs-lookup"><span data-stu-id="46df6-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="46df6-485">移至**儲存體**下方的資料夾**外掛程式**專案中檢視，然後選取下列外掛程式*只*:</span><span class="sxs-lookup"><span data-stu-id="46df6-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="46df6-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="46df6-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="46df6-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="46df6-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="46df6-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="46df6-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="46df6-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="46df6-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="46df6-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="46df6-490">System.Spatial</span></span>

![取消選取任何平台](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="46df6-492">具有*這些特定的外掛程式*選取，**取消核取** **任何平台**並**取消核取** **WSAPlayer**然後按一下**套用**。</span><span class="sxs-lookup"><span data-stu-id="46df6-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![適用於平台的 dll](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="46df6-494">我們會將標示要僅適用於在 Unity 編輯器中的這些特定外掛程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="46df6-495">這是因為有不同版本的專案會匯出從 Unity 後要使用 WSA 資料夾中的同一個外掛程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="46df6-496">在 **儲存體**外掛程式資料夾中，只選取：</span><span class="sxs-lookup"><span data-stu-id="46df6-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="46df6-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="46df6-497">Microsoft.Data.Services.Client</span></span>

        ![dll 不會處理集合](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="46df6-499">請檢查**不處理程序**下方**平台設定**，按一下 ***套用***。</span><span class="sxs-lookup"><span data-stu-id="46df6-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![適用於任何處理](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="46df6-501">我們會標示此外掛程式不處理，因為 Unity 組件修補程式已處理此外掛程式的困難度。</span><span class="sxs-lookup"><span data-stu-id="46df6-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="46df6-502">即使它不會處理此外掛程式仍然可以運作。</span><span class="sxs-lookup"><span data-stu-id="46df6-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="46df6-503">第 9-桌面 Unity 專案中建立 TableToScene 類別</span><span class="sxs-lookup"><span data-stu-id="46df6-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="46df6-504">您現在要建立包含程式碼以執行此應用程式的指令碼。</span><span class="sxs-lookup"><span data-stu-id="46df6-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="46df6-505">您必須建立第一個指令碼**TableToScene**，它會負責：</span><span class="sxs-lookup"><span data-stu-id="46df6-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="46df6-506">讀取 Azure 資料表中的實體。</span><span class="sxs-lookup"><span data-stu-id="46df6-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="46df6-507">使用資料表資料，來判斷哪些物件來繁衍 （spawn），以及在哪些位置。</span><span class="sxs-lookup"><span data-stu-id="46df6-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="46df6-508">您必須建立第二個指令碼**CloudScene**，它會負責：</span><span class="sxs-lookup"><span data-stu-id="46df6-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="46df6-509">註冊以滑鼠左鍵按一下事件，以允許使用者拖曳物件周圍的場景。</span><span class="sxs-lookup"><span data-stu-id="46df6-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="46df6-510">序列化物件資料，從這個 Unity 場景，並將它傳送至 Azure 函式應用程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="46df6-511">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="46df6-511">To create this class:</span></span>

1.  <span data-ttu-id="46df6-512">以滑鼠右鍵按一下**Asset**  資料夾位於 專案 面板**建立** > **資料夾**。</span><span class="sxs-lookup"><span data-stu-id="46df6-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="46df6-513">將資料夾命名**指令碼**。</span><span class="sxs-lookup"><span data-stu-id="46df6-513">Name the folder **Scripts**.</span></span>

    ![建立指令碼 資料夾](images/AzureLabs-Lab8-66.png)

    ![建立指令碼資料夾 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="46df6-516">按兩下剛才建立開啟的資料夾。</span><span class="sxs-lookup"><span data-stu-id="46df6-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="46df6-517">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="46df6-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="46df6-518">指令碼命名**TableToScene**。</span><span class="sxs-lookup"><span data-stu-id="46df6-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="46df6-519">![新的 c# 指令碼](images/AzureLabs-Lab8-68.png)
    ![TableToScene 重新命名](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="46df6-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="46df6-520">按兩下要開啟 Visual Studio 2017 中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="46df6-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="46df6-521">加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="46df6-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="46df6-522">在類別中，插入下列變數：</span><span class="sxs-lookup"><span data-stu-id="46df6-522">Within the class, insert the following variables:</span></span>

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
    > <span data-ttu-id="46df6-523">Substitute **accountName**值與您 Azure 儲存體服務的名稱並**accountKey**具有金鑰的值，在 Azure 入口網站 （請參閱下圖） 中的 Azure 儲存體服務中找到的值。</span><span class="sxs-lookup"><span data-stu-id="46df6-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![擷取帳戶金鑰](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="46df6-525">現在，加入**start （)** 並**Awake()** 來初始化類別的方法。</span><span class="sxs-lookup"><span data-stu-id="46df6-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

8.  <span data-ttu-id="46df6-526">內**TableToScene**類別中，新增會從 Azure 資料表中擷取值，以及使用它們來繁衍 （spawn） 在場景中適當的基本類型的方法。</span><span class="sxs-lookup"><span data-stu-id="46df6-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

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

9.  <span data-ttu-id="46df6-527">Outside **TableToScene**類別，您需要應用程式用來序列化和還原序列化的類別定義**資料表實體**。</span><span class="sxs-lookup"><span data-stu-id="46df6-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

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

10. <span data-ttu-id="46df6-528">請務必**儲存**之前返回至 Unity Editor。</span><span class="sxs-lookup"><span data-stu-id="46df6-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="46df6-529">按一下 [ **Main Camera**從**階層**] 面板中，使其屬性會出現在**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="46df6-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="46df6-530">具有**指令碼**資料夾中開啟，選取的指令碼**TableToScene 檔案**然後拖曳到**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="46df6-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="46df6-531">結果應該如下：</span><span class="sxs-lookup"><span data-stu-id="46df6-531">The result should be as below:</span></span>

    ![將指令碼新增至主攝影機](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="46df6-533">第 10-桌面 Unity 專案中建立 CloudScene 類別</span><span class="sxs-lookup"><span data-stu-id="46df6-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="46df6-534">您必須建立第二個指令碼**CloudScene**，它會負責：</span><span class="sxs-lookup"><span data-stu-id="46df6-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="46df6-535">註冊以滑鼠左鍵按一下事件，以允許使用者拖曳物件周圍的場景。</span><span class="sxs-lookup"><span data-stu-id="46df6-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="46df6-536">序列化物件資料，從這個 Unity 場景，並將它傳送至 Azure 函式應用程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="46df6-537">若要建立第二個指令碼：</span><span class="sxs-lookup"><span data-stu-id="46df6-537">To create the second script:</span></span>

1.  <span data-ttu-id="46df6-538">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立**， **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="46df6-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="46df6-539">指令碼命名**CloudScene**</span><span class="sxs-lookup"><span data-stu-id="46df6-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="46df6-540">![新的 c# 指令碼](images/AzureLabs-Lab8-72.png)
    ![重新命名 CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="46df6-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="46df6-541">加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="46df6-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="46df6-542">插入下列變數：</span><span class="sxs-lookup"><span data-stu-id="46df6-542">Insert the following variables:</span></span>

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

4.  <span data-ttu-id="46df6-543">Substitute **azureFunctionEndpoint**與下圖所示，在 Azure 函式應用程式服務中，在 Azure 入口網站中，找到您的 Azure 函式應用程式 URL 的值：</span><span class="sxs-lookup"><span data-stu-id="46df6-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![取得函式 URL](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="46df6-545">現在，加入**start （)** 並**Awake()** 來初始化類別的方法。</span><span class="sxs-lookup"><span data-stu-id="46df6-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

6.  <span data-ttu-id="46df6-546">內**update （)** 方法，將會偵測滑鼠輸入，並拖曳，會依次移動 Gameobject 場景中的下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="46df6-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="46df6-547">如果使用者拖曳並卸除物件，它會將名稱和物件的座標傳遞至方法**UpdateCloudScene()** ，這會呼叫 Azure 函式應用程式服務，這會更新 Azure 資料表和觸發程序通知。</span><span class="sxs-lookup"><span data-stu-id="46df6-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

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

7.  <span data-ttu-id="46df6-548">現在，加入**UpdateCloudScene()** 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="46df6-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

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

8.  <span data-ttu-id="46df6-549">儲存程式碼，並返回到 Unity</span><span class="sxs-lookup"><span data-stu-id="46df6-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="46df6-550">拖曳**CloudScene**拖曳至指令碼**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="46df6-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="46df6-551">按一下 [ **Main Camera**從**階層**] 面板中，使其屬性會出現在**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="46df6-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="46df6-552">具有**指令碼**資料夾開啟，請選取**CloudScene**指令碼，並將它拖曳到**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="46df6-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="46df6-553">結果應該如下：</span><span class="sxs-lookup"><span data-stu-id="46df6-553">The result should be as below:</span></span>

        > ![拖曳主攝影機中的雲端指令碼](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="46df6-555">第 11 章-建置 UWP 桌面專案</span><span class="sxs-lookup"><span data-stu-id="46df6-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="46df6-556">此專案的 Unity 區段所需的所有項目現在已完成。</span><span class="sxs-lookup"><span data-stu-id="46df6-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="46df6-557">瀏覽至**組建設定**(**檔案** > **組建設定**)。</span><span class="sxs-lookup"><span data-stu-id="46df6-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="46df6-558">從**Build Settings**  視窗中，按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="46df6-558">From the **Build Settings** window, click **Build**.</span></span>

    ![建置專案](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="46df6-560">A**檔案總管** 將會快顯視窗，提示您輸入要組建的位置。</span><span class="sxs-lookup"><span data-stu-id="46df6-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="46df6-561">建立新的資料夾 (依序按一下**新的資料夾**左上角)，並將它命名**建置**。</span><span class="sxs-lookup"><span data-stu-id="46df6-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![組建的新資料夾](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="46df6-563">開啟新**組建**資料夾，並建立另一個資料夾 (使用**新資料夾**一次)，並將它命名**NH\_Desktop\_應用程式**。</span><span class="sxs-lookup"><span data-stu-id="46df6-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![資料夾名稱 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="46df6-565">具有**NH\_桌面\_應用程式**選取。</span><span class="sxs-lookup"><span data-stu-id="46df6-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="46df6-566">按一下 **選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="46df6-566">click **Select Folder**.</span></span> <span data-ttu-id="46df6-567">專案需要約一分鐘來建置。</span><span class="sxs-lookup"><span data-stu-id="46df6-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="46df6-568">下列組建**檔案總管**會出現顯示您的新專案的位置。</span><span class="sxs-lookup"><span data-stu-id="46df6-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="46df6-569">若要開啟它，不過，您也可以視需要建立其他 Unity 專案首先，在接下來幾個章節則不需要。</span><span class="sxs-lookup"><span data-stu-id="46df6-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="46df6-570">第 12 章-設定混合實境 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="46df6-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="46df6-571">下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。</span><span class="sxs-lookup"><span data-stu-id="46df6-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="46df6-572">開啟**Unity**然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="46df6-572">Open **Unity** and click **New**.</span></span>

    ![新的 unity 專案](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="46df6-574">您現在需要提供 Unity 專案名稱、 插入**UnityMRNotifHub**。</span><span class="sxs-lookup"><span data-stu-id="46df6-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="46df6-575">請確定專案類型設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="46df6-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="46df6-576">設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。</span><span class="sxs-lookup"><span data-stu-id="46df6-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="46df6-577">然後，按一下**建立專案**。</span><span class="sxs-lookup"><span data-stu-id="46df6-577">Then, click **Create project**.</span></span>

    ![name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="46df6-579">使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="46df6-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="46df6-580">移至**編輯** > **喜好設定**並從新的視窗，然後瀏覽至**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="46df6-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="46df6-581">變更**外部指令碼編輯器**要**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="46df6-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="46df6-582">關閉**喜好設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="46df6-582">Close the **Preferences** window.</span></span>

    ![設定 VS 外部編輯器](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="46df6-584">接下來，移至**檔案** > **組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="46df6-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![切換至 UWP 的平台](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="46df6-586">移至**檔案** > **組建設定**並確定：</span><span class="sxs-lookup"><span data-stu-id="46df6-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="46df6-587">**裝置為目標**設為**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="46df6-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="46df6-588">對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="46df6-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="46df6-589">**建置型別**設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="46df6-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="46df6-590">**SDK**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="46df6-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="46df6-591">**Visual Studio 版本**設為**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="46df6-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="46df6-592">**建置並執行**設為**本機電腦**</span><span class="sxs-lookup"><span data-stu-id="46df6-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="46df6-593">在這裡值得儲存場景，並將它新增至組建。</span><span class="sxs-lookup"><span data-stu-id="46df6-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="46df6-594">做法是選取**加入開啟的場景**。</span><span class="sxs-lookup"><span data-stu-id="46df6-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="46df6-595">儲存視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="46df6-595">A save window will appear.</span></span>

            ![將開啟的場景新增](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="46df6-597">建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="46df6-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新的場景資料夾](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="46df6-599">開啟您剛建立**場景**資料夾，然後在**檔案名稱：** 文字欄位中輸入**NH\_MR\_場景**，然後按下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="46df6-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![新的場景-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="46df6-601">剩餘的設定，**組建設定**，應保持為預設值，現在。</span><span class="sxs-lookup"><span data-stu-id="46df6-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="46df6-602">在相同的視窗中按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。</span><span class="sxs-lookup"><span data-stu-id="46df6-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![開啟 播放程式設定](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="46df6-604">在此窗格中，少數設定需要驗證：</span><span class="sxs-lookup"><span data-stu-id="46df6-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="46df6-605">在 [**其他設定**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="46df6-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="46df6-606">**指令碼執行階段版本**應該**實驗性**（.NET 4.6 對等）</span><span class="sxs-lookup"><span data-stu-id="46df6-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="46df6-607">**指令碼後端**應該是 ***.NET***</span><span class="sxs-lookup"><span data-stu-id="46df6-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="46df6-608">**API 相容性層級**應該是 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="46df6-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![api 相容性](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="46df6-610">在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入</span><span class="sxs-lookup"><span data-stu-id="46df6-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![更新 xr 設定](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="46df6-612">內**發佈設定**索引標籤之下**功能**，h:</span><span class="sxs-lookup"><span data-stu-id="46df6-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="46df6-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="46df6-613">**InternetClient**</span></span>           

            ![刻度網際網路用戶端](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="46df6-615">回到**Build Settings**， **UnityC#專案**不再呈現灰色： 這旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="46df6-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="46df6-616">完成這些變更，關閉 [建立設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="46df6-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="46df6-617">儲存您的場景和專案**檔案** > **儲存場景檔案** > **儲存專案**。</span><span class="sxs-lookup"><span data-stu-id="46df6-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="46df6-618">如果您想要跳過*Unity 設定*元件為此專案中 （混合實境應用程式），並直接在程式碼中繼續進行，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)，它匯入到您的專案，作為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="46df6-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="46df6-619">您仍必須新增指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="46df6-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="46df6-620">第 13 章-匯入的混合的實境 Unity 專案中的 Dll</span><span class="sxs-lookup"><span data-stu-id="46df6-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="46df6-621">您將使用 Azure 儲存體的 Unity 文件庫 （這適用於 Azure 中使用.Net SDK）。</span><span class="sxs-lookup"><span data-stu-id="46df6-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="46df6-622">請遵循此[如何使用 Unity 的 Azure 儲存體的連結](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="46df6-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="46df6-623">這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。</span><span class="sxs-lookup"><span data-stu-id="46df6-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="46df6-624">這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。</span><span class="sxs-lookup"><span data-stu-id="46df6-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="46df6-625">若要 SDK 匯入您自己的專案，請確定您已下載最新[.unitypackage](https://aka.ms/azstorage-unitysdk)。</span><span class="sxs-lookup"><span data-stu-id="46df6-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="46df6-626">然後，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="46df6-626">Then, do the following:</span></span>

1.  <span data-ttu-id="46df6-627">新增您從上述項目，下載到使用 Unity.unitypackage**資產** > **匯入封裝** > **自訂封裝**功能表選項.</span><span class="sxs-lookup"><span data-stu-id="46df6-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="46df6-628">在 **匯入 Unity 封裝**方塊，顯示，您可以選取下方的所有內容**外掛程式** > **儲存體**。</span><span class="sxs-lookup"><span data-stu-id="46df6-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![匯入封裝](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="46df6-630">按一下 **匯入**按鈕以新增至您的專案項目。</span><span class="sxs-lookup"><span data-stu-id="46df6-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="46df6-631">移至**儲存體**下方的資料夾**外掛程式**專案中檢視，然後選取下列外掛程式*只*:</span><span class="sxs-lookup"><span data-stu-id="46df6-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="46df6-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="46df6-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="46df6-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="46df6-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="46df6-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="46df6-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="46df6-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="46df6-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="46df6-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="46df6-636">System.Spatial</span></span>

    ![選取外掛程式](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="46df6-638">具有*這些特定的外掛程式*選取，**取消核取** **任何平台**並**取消核取** **WSAPlayer**然後按一下**套用**。</span><span class="sxs-lookup"><span data-stu-id="46df6-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![適用於平台的變更](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="46df6-640">您必須先將這些特定的外掛程式，以僅適用於在 Unity 編輯器中。</span><span class="sxs-lookup"><span data-stu-id="46df6-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="46df6-641">這是因為有不同版本的專案會匯出從 Unity 後要使用 WSA 資料夾中的同一個外掛程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="46df6-642">在 **儲存體**外掛程式資料夾中，只選取：</span><span class="sxs-lookup"><span data-stu-id="46df6-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="46df6-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="46df6-643">Microsoft.Data.Services.Client</span></span>

        ![選取 data services 用戶端](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="46df6-645">請檢查**不處理程序**下方**平台設定**，按一下 **套用**。</span><span class="sxs-lookup"><span data-stu-id="46df6-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![不會處理](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="46df6-647">您必須先將此外掛程式 」 不會處理 」 的 Unity 組件修補程式發生無法處理此外掛程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="46df6-648">即使它不處理的外掛程式仍然可以運作。</span><span class="sxs-lookup"><span data-stu-id="46df6-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="46df6-649">第 14 章-混合的實境 Unity 專案中建立 TableToScene 類別</span><span class="sxs-lookup"><span data-stu-id="46df6-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="46df6-650">**TableToScene**中所述的一個類別等同[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="46df6-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="46df6-651">在 Unity 專案遵循相同的程序所述的混合實境中建立相同的類別[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="46df6-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="46df6-652">當您完成這一章，這兩個您**Unity 專案**會有在 Main Camera 上設定這個類別。</span><span class="sxs-lookup"><span data-stu-id="46df6-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="46df6-653">第 15 章-混合實境 Unity 專案中建立 NotificationReceiver 類別</span><span class="sxs-lookup"><span data-stu-id="46df6-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="46df6-654">您必須建立第二個指令碼**NotificationReceiver**，它會負責：</span><span class="sxs-lookup"><span data-stu-id="46df6-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="46df6-655">在初始化時的通知中樞註冊的應用程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="46df6-656">接聽來自通知中樞的通知。</span><span class="sxs-lookup"><span data-stu-id="46df6-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="46df6-657">還原序列化物件資料，從接收的通知。</span><span class="sxs-lookup"><span data-stu-id="46df6-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="46df6-658">場景，根據已還原序列化資料中移動 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="46df6-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="46df6-659">若要建立**NotificationReceiver**指令碼：</span><span class="sxs-lookup"><span data-stu-id="46df6-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="46df6-660">以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立**， **C\#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="46df6-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="46df6-661">指令碼命名**NotificationReceiver**。</span><span class="sxs-lookup"><span data-stu-id="46df6-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="46df6-662">![建立新的 c# 指令碼](images/AzureLabs-Lab8-95.png)
    ![命名 NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="46df6-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="46df6-663">按兩下要開啟的指令碼。</span><span class="sxs-lookup"><span data-stu-id="46df6-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="46df6-664">加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="46df6-664">Add the following namespaces:</span></span>

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

4.  <span data-ttu-id="46df6-665">插入下列變數：</span><span class="sxs-lookup"><span data-stu-id="46df6-665">Insert the following variables:</span></span>

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

5.  <span data-ttu-id="46df6-666">Substitute **hubName**值與您通知中樞服務的名稱，並**hubListenEndpoint**值與存取原則 索引標籤中，Azure 通知中樞服務中找到的端點值Azure 入口網站 （請參閱下圖）。</span><span class="sxs-lookup"><span data-stu-id="46df6-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![插入通知中樞原則端點](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="46df6-668">現在，加入**start （)** 並**Awake()** 來初始化類別的方法。</span><span class="sxs-lookup"><span data-stu-id="46df6-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

7.  <span data-ttu-id="46df6-669">新增**WaitForNotification**方法，以允許應用程式以接收來自通知中樞程式庫的通知，而不發生衝突與主執行緒：</span><span class="sxs-lookup"><span data-stu-id="46df6-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

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

8.  <span data-ttu-id="46df6-670">下列方法**InitNotificationAsync()** ，會向通知中樞服務在初始化應用程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="46df6-671">程式碼標記為註解為 Unity 將無法建置專案。</span><span class="sxs-lookup"><span data-stu-id="46df6-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="46df6-672">當您匯入 Visual Studio 中的 Azure 傳訊的 Nuget 套件，您將會移除註解。</span><span class="sxs-lookup"><span data-stu-id="46df6-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

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

9.  <span data-ttu-id="46df6-673">下列處理常式中，**通道\_PushNotificationReceived()** ，每次接收到通知時，就會觸發。</span><span class="sxs-lookup"><span data-stu-id="46df6-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="46df6-674">它將會還原序列化該通知上方，它會於桌面應用程式中，已移動之 Azure 資料表實體，然後將對應的 GameObject MR 場景中移至相同的位置。</span><span class="sxs-lookup"><span data-stu-id="46df6-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="46df6-675">因為程式碼會參考 Azure 傳訊程式庫，您將會新增在建置使用 Nuget 套件管理員，在 Visual Studio 的 Unity 專案之後，會註解化程式碼。</span><span class="sxs-lookup"><span data-stu-id="46df6-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="46df6-676">因此，Unity 專案將無法建置，除非它標記為註解。請注意，您應該建置您的專案，然後想要傳回至 Unity，您必須**恢復註解**該程式碼。</span><span class="sxs-lookup"><span data-stu-id="46df6-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

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

10. <span data-ttu-id="46df6-677">請務必先返回至 Unity 編輯器中儲存變更。</span><span class="sxs-lookup"><span data-stu-id="46df6-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="46df6-678">按一下 [ **Main Camera**從**階層**] 面板中，使其屬性會出現在**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="46df6-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="46df6-679">具有**指令碼**資料夾開啟，請選取**NotificationReceiver**指令碼，並將它拖曳到**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="46df6-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="46df6-680">結果應該如下：</span><span class="sxs-lookup"><span data-stu-id="46df6-680">The result should be as below:</span></span>

    ![拖曳至攝影機的通知接收者指令碼](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="46df6-682">如果您正在開發這 Microsoft HoloLens，您必須更新**Main Camera**的*相機*元件，以便：</span><span class="sxs-lookup"><span data-stu-id="46df6-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="46df6-683">清除旗標：純色</span><span class="sxs-lookup"><span data-stu-id="46df6-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="46df6-684">背景：黑色</span><span class="sxs-lookup"><span data-stu-id="46df6-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="46df6-685">第 16 章-建置混合的實境專案至 UWP</span><span class="sxs-lookup"><span data-stu-id="46df6-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="46df6-686">這一章等同於建置前一個專案的程序。</span><span class="sxs-lookup"><span data-stu-id="46df6-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="46df6-687">此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。</span><span class="sxs-lookup"><span data-stu-id="46df6-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="46df6-688">瀏覽至**組建設定**(**檔案** > **組建設定**)。</span><span class="sxs-lookup"><span data-stu-id="46df6-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="46df6-689">從**Build Settings**  功能表中，確保**UnityC#專案**\* 已核 （這可讓您在建置後編輯此專案中的指令碼）。</span><span class="sxs-lookup"><span data-stu-id="46df6-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="46df6-690">這麼做之後，請按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="46df6-690">After this is done, click **Build**.</span></span>

    ![建置專案](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="46df6-692">A**檔案總管** 將會快顯視窗，提示您輸入要組建的位置。</span><span class="sxs-lookup"><span data-stu-id="46df6-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="46df6-693">建立新的資料夾 (依序按一下**新的資料夾**左上角)，並將它命名**建置**。</span><span class="sxs-lookup"><span data-stu-id="46df6-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![建立組建 資料夾](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="46df6-695">開啟新**組建**資料夾，並建立另一個資料夾 (使用**新資料夾**一次)，並將它命名**NH\_MR\_應用程式**。</span><span class="sxs-lookup"><span data-stu-id="46df6-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![建立 NH_MR_Apps 資料夾](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="46df6-697">具有**NH\_MR\_應用程式**選取。</span><span class="sxs-lookup"><span data-stu-id="46df6-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="46df6-698">按一下 **選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="46df6-698">click **Select Folder**.</span></span> <span data-ttu-id="46df6-699">專案需要約一分鐘來建置。</span><span class="sxs-lookup"><span data-stu-id="46df6-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="46df6-700">下列組建**檔案總管**視窗就會開啟新專案的位置。</span><span class="sxs-lookup"><span data-stu-id="46df6-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="46df6-701">第 17 章-加入 UnityMRNotifHub 方案的 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="46df6-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="46df6-702">請記住，一旦您將下列 NuGet 封裝 (並在下一個程式碼取消註解[章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class))，程式碼，在 Unity 專案中，重新開啟時將會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="46df6-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="46df6-703">如果您想要返回並繼續編輯在 Unity 編輯器中，您將需要發表評論該 errosome 程式碼中，，然後取消註解一次更新的版本，一旦您已回到 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="46df6-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="46df6-704">完成混合的實境組建之後，瀏覽至混合的實境專案中，您建立，並按兩下該資料夾，若要使用 Visual Studio 2017 中開啟您的方案中的方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="46df6-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="46df6-705">您現在需要新增**WindowsAzure.Messaging.managed** NuGet 套件，這是用來接收來自通知中樞通知程式庫。</span><span class="sxs-lookup"><span data-stu-id="46df6-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="46df6-706">若要匯入的 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="46df6-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="46df6-707">在 [**方案總管] 中**，以滑鼠右鍵按一下您的解決方案</span><span class="sxs-lookup"><span data-stu-id="46df6-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="46df6-708">按一下 **管理 NuGet 封裝**。</span><span class="sxs-lookup"><span data-stu-id="46df6-708">Click on **Manage NuGet Packages**.</span></span>

    ![開啟 nuget 管理員](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="46df6-710">選取 ***瀏覽***索引標籤，然後搜尋**WindowsAzure.Messaging.managed**。</span><span class="sxs-lookup"><span data-stu-id="46df6-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![尋找 windows azure 傳訊套件](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="46df6-712">選取結果 （如下所示），然後在右側視窗中，選取核取方塊旁**專案**。</span><span class="sxs-lookup"><span data-stu-id="46df6-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="46df6-713">這將會置於刻度核取方塊旁**專案**，以及旁的核取方塊**組件 CSharp**並**UnityMRNotifHub**專案。</span><span class="sxs-lookup"><span data-stu-id="46df6-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![勾選所有專案](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="46df6-715">一開始提供的版本**可能不**與此專案相容。</span><span class="sxs-lookup"><span data-stu-id="46df6-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="46df6-716">因此，按一下功能表上的下拉式清單旁**版本**，然後按一下**版本 0.1.7.9**，然後按一下**安裝**。</span><span class="sxs-lookup"><span data-stu-id="46df6-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="46df6-717">您現在已完成安裝 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="46df6-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="46df6-718">尋找您在中輸入註解的程式碼**NotificationReceiver**類別，並移除註解...</span><span class="sxs-lookup"><span data-stu-id="46df6-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="46df6-719">第 18 章-編輯 UnityMRNotifHub 應用程式、 NotificationReceiver 類別</span><span class="sxs-lookup"><span data-stu-id="46df6-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="46df6-720">下列加**NuGet 套件**，您必須*取消註解*部分中的程式碼**NotificationReceiver**類別。</span><span class="sxs-lookup"><span data-stu-id="46df6-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="46df6-721">這包括：</span><span class="sxs-lookup"><span data-stu-id="46df6-721">This includes:</span></span>

1. <span data-ttu-id="46df6-722">在頂端命名空間：</span><span class="sxs-lookup"><span data-stu-id="46df6-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="46df6-723">內的所有程式碼**InitNotificationsAsync()** 方法：</span><span class="sxs-lookup"><span data-stu-id="46df6-723">All the code within the **InitNotificationsAsync()** method:</span></span>

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
> <span data-ttu-id="46df6-724">上述程式碼中有註解： 請確定您已不會無意*取消註解*，註解 （如程式碼將不會編譯有 ！）。</span><span class="sxs-lookup"><span data-stu-id="46df6-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="46df6-725">而且，最後**Channel_PushNotificationReceived**事件：</span><span class="sxs-lookup"><span data-stu-id="46df6-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

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

<span data-ttu-id="46df6-726">使用這些取消註解，請確定您儲存，，，然後繼續進行下一步 一章。</span><span class="sxs-lookup"><span data-stu-id="46df6-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="46df6-727">將第 19 章-產生關聯的混合的實境專案，為市集應用程式</span><span class="sxs-lookup"><span data-stu-id="46df6-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="46df6-728">您現在必須將關聯**混合實境**中建立實驗室的開頭為市集應用程式的專案。</span><span class="sxs-lookup"><span data-stu-id="46df6-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="46df6-729">開啟的方案。</span><span class="sxs-lookup"><span data-stu-id="46df6-729">Open the solution.</span></span>

2.  <span data-ttu-id="46df6-730">在方案總管 窗格中，移至 UWP 應用程式專案上按一下滑鼠右鍵**存放區**，和**與市集建立關聯的應用程式...** .</span><span class="sxs-lookup"><span data-stu-id="46df6-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![開啟市集關聯](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="46df6-732">會出現一個新的視窗呼叫**產生關聯您的應用程式與 Windows 市集**。</span><span class="sxs-lookup"><span data-stu-id="46df6-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="46df6-733">按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="46df6-733">Click **Next**.</span></span>

    ![請移至下一個畫面](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="46df6-735">它會載入與您已登入的帳戶相關聯的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="46df6-736">如果您未登入您的帳戶，您可以**登入**此頁面上。</span><span class="sxs-lookup"><span data-stu-id="46df6-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="46df6-737">尋找**市集應用程式名稱**，您在本教學課程開頭所建立，並加以選取。</span><span class="sxs-lookup"><span data-stu-id="46df6-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="46df6-738">然後按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="46df6-738">Then click **Next**.</span></span>

    ![尋找並選取您的存放區名稱](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="46df6-740">按一下 **產生關聯**。</span><span class="sxs-lookup"><span data-stu-id="46df6-740">Click **Associate**.</span></span>

    ![應用程式建立關聯](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="46df6-742">您的應用程式現在已**相關聯**市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="46df6-743">這是必要的啟用通知。</span><span class="sxs-lookup"><span data-stu-id="46df6-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="46df6-744">第 20 章-部署 UnityMRNotifHub 和 UnityDesktopNotifHub 應用程式</span><span class="sxs-lookup"><span data-stu-id="46df6-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="46df6-745">這一章可能容易，因為兩名人員，結果會包含同時執行的應用程式，在 Desktop 中，您電腦上的一個執行，另一個沈浸式耳機內。</span><span class="sxs-lookup"><span data-stu-id="46df6-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="46df6-746">耳機沈浸式應用程式正在等候接收場景 （本機 Gameobject 的位置變更，） 的變更和傳統型應用程式會對其本機場景 （位置的變更） 會共用 MR 應用程式進行變更。</span><span class="sxs-lookup"><span data-stu-id="46df6-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="46df6-747">合理 MR 應用程式部署在第一次，後面傳統型應用程式，以便開始接聽的接收者。</span><span class="sxs-lookup"><span data-stu-id="46df6-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="46df6-748">若要部署**UnityMRNotifHub**本機電腦上的應用程式：</span><span class="sxs-lookup"><span data-stu-id="46df6-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="46df6-749">開啟的方案檔您**UnityMRNotifHub**中的應用程式**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="46df6-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="46df6-750">在 **的方案平台**，選取**x86，本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="46df6-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="46df6-751">在 **方案組態**選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="46df6-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![設定專案組態](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="46df6-753">移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="46df6-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="46df6-754">您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。</span><span class="sxs-lookup"><span data-stu-id="46df6-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="46df6-755">若要部署**UnityDesktopNotifHub**本機電腦上的應用程式：</span><span class="sxs-lookup"><span data-stu-id="46df6-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="46df6-756">開啟的方案檔您**UnityDesktopNotifHub**中的應用程式**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="46df6-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="46df6-757">在 **的方案平台**，選取**x86，本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="46df6-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="46df6-758">在 **方案組態**選取**偵錯**。</span><span class="sxs-lookup"><span data-stu-id="46df6-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![設定專案組態](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="46df6-760">移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="46df6-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="46df6-761">您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。</span><span class="sxs-lookup"><span data-stu-id="46df6-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="46df6-762">啟動混合的實境應用程式，後面接著的桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="46df6-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="46df6-763">這兩個執行的應用程式，請在桌面的場景 （使用左滑鼠按鈕） 中移動的物件。</span><span class="sxs-lookup"><span data-stu-id="46df6-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="46df6-764">這些位置的變更會在本機進行，序列化，且傳送至函式應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="46df6-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="46df6-765">函式應用程式服務會更新與通知中樞的資料表。</span><span class="sxs-lookup"><span data-stu-id="46df6-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="46df6-766">接收更新，通知中樞將更新的資料直接傳送到所有已註冊應用程式 （在此案例的沈浸式耳機應用程式），接著還原序列化傳入的資料，並將新的位置資料套用至本機的物件，您可以移動它們在場景中。</span><span class="sxs-lookup"><span data-stu-id="46df6-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="46df6-767">您已完成您的 Azure 通知中樞應用程式</span><span class="sxs-lookup"><span data-stu-id="46df6-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="46df6-768">恭喜，您所建立的混合的實境應用程式會利用 「 Azure 通知中樞 」 服務，並允許應用程式之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="46df6-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![最終產品-結束](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="46df6-770">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="46df6-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="46df6-771">練習 1</span><span class="sxs-lookup"><span data-stu-id="46df6-771">Exercise 1</span></span>

<span data-ttu-id="46df6-772">您可以變更 Gameobject 的色彩，並將該通知傳送給其他應用程式檢視場景怎麼運作嗎？</span><span class="sxs-lookup"><span data-stu-id="46df6-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="46df6-773">練習 2</span><span class="sxs-lookup"><span data-stu-id="46df6-773">Exercise 2</span></span>

<span data-ttu-id="46df6-774">您可以對 MR 應用程式中新增的 Gameobject 移動並傳統型應用程式中看到更新的場景嗎？</span><span class="sxs-lookup"><span data-stu-id="46df6-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
