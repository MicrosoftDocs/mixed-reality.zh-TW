---
title: 儲存並尋找您的檔案
description: 如何尋找、 儲存及共用 HoloLens 上的檔案。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 操作說明、 檔案選擇器、 檔案、 相片、 視訊、 圖片、 OneDrive、 儲存體、 檔案總管
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595665"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="dc195-104">儲存並尋找您的檔案</span><span class="sxs-lookup"><span data-stu-id="dc195-104">Saving and finding your files</span></span>

<span data-ttu-id="dc195-105">檔案可以儲存和管理類似的方式，其他的 Windows 10 Desktop 和行動裝置：</span><span class="sxs-lookup"><span data-stu-id="dc195-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="dc195-106">使用檔案總管 應用程式存取本機資料夾</span><span class="sxs-lookup"><span data-stu-id="dc195-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="dc195-107">應用程式本身的儲存體</span><span class="sxs-lookup"><span data-stu-id="dc195-107">Within an app's own storage</span></span>
* <span data-ttu-id="dc195-108">在特殊的已知資料夾 （例如視訊或音樂媒體櫃）</span><span class="sxs-lookup"><span data-stu-id="dc195-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="dc195-109">使用儲存體服務，其中包含應用程式和檔案選擇器 （例如 OneDrive)</span><span class="sxs-lookup"><span data-stu-id="dc195-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="dc195-110">透過 MTP （媒體傳輸通訊協定） 支援使用桌上型個人電腦連接到您透過 USB、 HoloLens</span><span class="sxs-lookup"><span data-stu-id="dc195-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="dc195-111">檔案總管</span><span class="sxs-lookup"><span data-stu-id="dc195-111">File Explorer</span></span>

<span data-ttu-id="dc195-112">您可以使用檔案總管 應用程式來移動和刪除 HoloLens 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="dc195-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="dc195-113">如果看不到任何檔案在檔案總管中的，「 最近 」 篩選條件可能是作用中 （左窗格中，反白顯示時鐘圖示）。</span><span class="sxs-lookup"><span data-stu-id="dc195-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="dc195-114">若要修正此問題，請選取**此裝置**文件圖示，左窗格中 （下方的時鐘圖示），或開啟功能表，然後選取**此裝置**。</span><span class="sxs-lookup"><span data-stu-id="dc195-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="dc195-115">應用程式中的檔案</span><span class="sxs-lookup"><span data-stu-id="dc195-115">Files within an app</span></span>

<span data-ttu-id="dc195-116">如果應用程式儲存在您的裝置上的檔案，您可以使用該應用程式可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="dc195-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="dc195-117">我的相片/影片哪裡？</span><span class="sxs-lookup"><span data-stu-id="dc195-117">Where are my photos/videos?</span></span>

<span data-ttu-id="dc195-118">[混合實境擷取](mixed-reality-capture.md)相片和視訊會儲存至裝置的相機相簿的資料夾。</span><span class="sxs-lookup"><span data-stu-id="dc195-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="dc195-119">這些可以透過存取[照片 app](see-your-photos.md#photos-app)。</span><span class="sxs-lookup"><span data-stu-id="dc195-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="dc195-120">您可以使用相片應用程式進行同步處理您的相片和影片到 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="dc195-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="dc195-121">您也可以存取您的相片和影片透過混合實境擷取的畫面[Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)。</span><span class="sxs-lookup"><span data-stu-id="dc195-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="dc195-122">從另一個應用程式要求檔案</span><span class="sxs-lookup"><span data-stu-id="dc195-122">Requesting files from another app</span></span>

<span data-ttu-id="dc195-123">應用程式可以要求儲存檔案，或從另一個應用程式，透過開啟檔案[檔案選擇器](app-model.md#file-pickers)。</span><span class="sxs-lookup"><span data-stu-id="dc195-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="dc195-124">已知的資料夾</span><span class="sxs-lookup"><span data-stu-id="dc195-124">Known folders</span></span>

<span data-ttu-id="dc195-125">HoloLens 支援多種[已知資料夾](app-model.md#known-folders)應用程式可以要求存取權限。</span><span class="sxs-lookup"><span data-stu-id="dc195-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="dc195-126">在服務中的檔案</span><span class="sxs-lookup"><span data-stu-id="dc195-126">Files in a service</span></span>

<span data-ttu-id="dc195-127">若要儲存至檔案 （或存取檔案） 服務，還必須安裝與服務相關聯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc195-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="dc195-128">若要將檔案儲存及存取檔案從 OneDrive，您必須安裝[OneDrive 應用程式](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)。</span><span class="sxs-lookup"><span data-stu-id="dc195-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="dc195-129">MTP （媒體傳輸通訊協定）</span><span class="sxs-lookup"><span data-stu-id="dc195-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="dc195-130">類似於其他行動裝置、 HoloLens 連接到您的桌面電腦，並且輕鬆傳輸開啟檔案總管 來存取您 HoloLens 的程式庫 （相片、 影片、 文件） 電腦上。</span><span class="sxs-lookup"><span data-stu-id="dc195-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="dc195-131">釐清的內容</span><span class="sxs-lookup"><span data-stu-id="dc195-131">Clarifications</span></span>

* <span data-ttu-id="dc195-132">HoloLens 不支援連接到外接式硬碟或 sd 記憶卡。</span><span class="sxs-lookup"><span data-stu-id="dc195-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="dc195-133">至於[Windows 10 April 2018 HoloLens 的更新 (RS4)](release-notes-april-2018.md)，HoloLens 包括檔案總管 中儲存和管理檔案的裝置。</span><span class="sxs-lookup"><span data-stu-id="dc195-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="dc195-134">加入的檔案總管 也可讓您能夠選擇您的檔案選擇器 （例如，儲存到您的裝置，或到 OneDrive 的檔案）。</span><span class="sxs-lookup"><span data-stu-id="dc195-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
