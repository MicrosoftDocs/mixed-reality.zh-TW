---
title: 儲存和尋找檔案
description: 如何在 HoloLens 上尋找、儲存及共用檔案。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 操作說明, 檔案選擇器, 檔案, 相片, 影片, 圖片, OneDrive, 儲存, 檔案瀏覽器
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524608"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="5f917-104">儲存和尋找檔案</span><span class="sxs-lookup"><span data-stu-id="5f917-104">Saving and finding your files</span></span>

<span data-ttu-id="5f917-105">檔案可以與其他 Windows 10 桌上型電腦和行動裝置以類似的方式儲存和管理:</span><span class="sxs-lookup"><span data-stu-id="5f917-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="5f917-106">使用 File Explorer 應用程式存取本機資料夾</span><span class="sxs-lookup"><span data-stu-id="5f917-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="5f917-107">在應用程式本身的儲存體中</span><span class="sxs-lookup"><span data-stu-id="5f917-107">Within an app's own storage</span></span>
* <span data-ttu-id="5f917-108">在特殊的已知資料夾中 (例如影片或音樂媒體櫃)</span><span class="sxs-lookup"><span data-stu-id="5f917-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="5f917-109">使用包含應用程式和檔案選擇器的儲存體服務 (例如 OneDrive)</span><span class="sxs-lookup"><span data-stu-id="5f917-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="5f917-110">使用透過 USB 連線至 HoloLens 的桌上型電腦, via MTP (媒體傳輸通訊協定) 支援</span><span class="sxs-lookup"><span data-stu-id="5f917-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="5f917-111">檔案總管</span><span class="sxs-lookup"><span data-stu-id="5f917-111">File Explorer</span></span>

<span data-ttu-id="5f917-112">您可以使用檔案瀏覽器應用程式, 在 HoloLens 中移動和刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="5f917-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="5f917-113">如果您在 [檔案瀏覽器] 中看不到任何檔案, [最近] 篩選可能會處於作用中狀態 (左窗格中的時鐘圖示會反白顯示)。</span><span class="sxs-lookup"><span data-stu-id="5f917-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="5f917-114">若要修正此問題, 請選取左窗格中的 [**此裝置**檔] 圖示 (在 [時鐘] 圖示下方), 或開啟功能表並選取 [**此裝置**]。</span><span class="sxs-lookup"><span data-stu-id="5f917-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="5f917-115">應用程式內的檔案</span><span class="sxs-lookup"><span data-stu-id="5f917-115">Files within an app</span></span>

<span data-ttu-id="5f917-116">如果應用程式將檔案儲存在您的裝置上, 您可以使用該應用程式來存取它們。</span><span class="sxs-lookup"><span data-stu-id="5f917-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="5f917-117">我的相片/影片在哪裡？</span><span class="sxs-lookup"><span data-stu-id="5f917-117">Where are my photos/videos?</span></span>

<span data-ttu-id="5f917-118">[混合現實拍攝](mixed-reality-capture.md)相片和影片會儲存到裝置的相機變換資料夾。</span><span class="sxs-lookup"><span data-stu-id="5f917-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="5f917-119">這些可以透過[相片應用程式](see-your-photos.md#photos-app)來存取。</span><span class="sxs-lookup"><span data-stu-id="5f917-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="5f917-120">您可以使用相片應用程式將您的相片和影片同步到 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="5f917-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="5f917-121">您也可以透過[Windows 裝置入口網站](using-the-windows-device-portal.md#mixed-reality-capture)的 [混合現實捕捉] 頁面來存取您的相片和影片。</span><span class="sxs-lookup"><span data-stu-id="5f917-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="5f917-122">向另一個應用程式要求檔案</span><span class="sxs-lookup"><span data-stu-id="5f917-122">Requesting files from another app</span></span>

<span data-ttu-id="5f917-123">應用程式可以要求儲存檔案, 或透過[檔案選擇器](app-model.md#file-pickers)從另一個應用程式開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="5f917-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="5f917-124">已知的資料夾</span><span class="sxs-lookup"><span data-stu-id="5f917-124">Known folders</span></span>

<span data-ttu-id="5f917-125">HoloLens 支援一些應用程式可以要求許可權來存取的[已知資料夾](app-model.md#known-folders)。</span><span class="sxs-lookup"><span data-stu-id="5f917-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="5f917-126">服務中的檔案</span><span class="sxs-lookup"><span data-stu-id="5f917-126">Files in a service</span></span>

<span data-ttu-id="5f917-127">若要將檔案儲存至服務 (或從其中存取檔案), 則必須安裝與服務相關聯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5f917-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="5f917-128">若要將檔案儲存到 OneDrive 並從中存取檔案, 您必須安裝[onedrive 應用程式](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)。</span><span class="sxs-lookup"><span data-stu-id="5f917-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="5f917-129">MTP (媒體傳輸通訊協定)</span><span class="sxs-lookup"><span data-stu-id="5f917-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="5f917-130">類似于其他行動裝置, 請將 HoloLens 連線到桌上型電腦, 並在電腦上開啟檔案瀏覽器, 以存取您的 HoloLens 程式庫 (相片、影片、檔) 以方便傳輸。</span><span class="sxs-lookup"><span data-stu-id="5f917-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="5f917-131">澄清</span><span class="sxs-lookup"><span data-stu-id="5f917-131">Clarifications</span></span>

* <span data-ttu-id="5f917-132">HoloLens 不支援連接到外部硬碟或 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="5f917-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="5f917-133">從適用于[hololens 的 Windows 10 2018 年4月更新 (RS4)](release-notes-april-2018.md)起, hololens 包含用於儲存和管理裝置上檔案的檔案瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="5f917-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="5f917-134">新增檔案瀏覽器也可讓您選擇檔案選擇器 (例如, 將檔案儲存到您的裝置或 OneDrive)。</span><span class="sxs-lookup"><span data-stu-id="5f917-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
