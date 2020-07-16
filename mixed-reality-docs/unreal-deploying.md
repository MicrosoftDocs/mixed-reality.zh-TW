---
title: 在 Unreal 中部署至裝置
description: 在 Unreal 至 HoloLens 2 中部署至裝置的指南
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal，Unreal Engine 4，UE4，HoloLens，HoloLens 2，mixed reality，部署至裝置，電腦，檔
appliesto:
- HoloLens 2
ms.openlocfilehash: 2d0cd67db79c1970695334d826fbbaf0f2f92ec0
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408176"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="e79dc-104">在 Unreal 中部署至裝置</span><span class="sxs-lookup"><span data-stu-id="e79dc-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="e79dc-105">概觀</span><span class="sxs-lookup"><span data-stu-id="e79dc-105">Overview</span></span>
<span data-ttu-id="e79dc-106">有兩種方式可將 Unreal 應用程式部署至 HoloLens 2：</span><span class="sxs-lookup"><span data-stu-id="e79dc-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span> 
* <span data-ttu-id="e79dc-107">直接從 Unreal 編輯器</span><span class="sxs-lookup"><span data-stu-id="e79dc-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="e79dc-108">作為透過裝置入口網站上傳的套件</span><span class="sxs-lookup"><span data-stu-id="e79dc-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="e79dc-109">這兩個選項都需要您設定 HoloLens，才能使用[裝置入口網站](using-the-windows-device-portal.md)進行開發。</span><span class="sxs-lookup"><span data-stu-id="e79dc-109">Both options require you to set up your HoloLens to use the [device portal](using-the-windows-device-portal.md) for development.</span></span> 

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="e79dc-110">從 Unreal 編輯器部署至裝置</span><span class="sxs-lookup"><span data-stu-id="e79dc-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="e79dc-111">按一下 [**啟動**] 按鈕旁邊的下拉式箭號。</span><span class="sxs-lookup"><span data-stu-id="e79dc-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="e79dc-112">一開始，HoloLens 裝置選項會呈現灰色。</span><span class="sxs-lookup"><span data-stu-id="e79dc-112">Initially, the HoloLens device option will be grayed out.</span></span>

![啟動下拉式清單選項](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="e79dc-114">開啟 [ **Device Manager**]。</span><span class="sxs-lookup"><span data-stu-id="e79dc-114">Open the **Device Manager**.</span></span> <span data-ttu-id="e79dc-115">請注意，您的 HoloLens 不會自動出現在裝置清單中。</span><span class="sxs-lookup"><span data-stu-id="e79dc-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="e79dc-116">展開 [**新增未列出的裝置**] 區段。</span><span class="sxs-lookup"><span data-stu-id="e79dc-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="e79dc-117">選取 [ **HoloLens** ] 做為您的**平臺**。</span><span class="sxs-lookup"><span data-stu-id="e79dc-117">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="e79dc-118">輸入您裝置的 IP 位址和埠資訊，並以冒號分隔作為裝置識別碼。</span><span class="sxs-lookup"><span data-stu-id="e79dc-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="e79dc-119">例如，"127.0.0.1： 10080" （透過 USB 連接時）。</span><span class="sxs-lookup"><span data-stu-id="e79dc-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="e79dc-120">使用您的裝置入口網站使用者名稱和密碼認證。</span><span class="sxs-lookup"><span data-stu-id="e79dc-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="e79dc-121">點擊 [**新增**]，然後關閉 [裝置管理員]。</span><span class="sxs-lookup"><span data-stu-id="e79dc-121">Hit **Add** and close the device manager.</span></span> 
    * <span data-ttu-id="e79dc-122">如果發生錯誤（例如位址、使用者名稱或密碼錯誤），則會將訊息列印到輸出記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e79dc-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![新增未列出的裝置](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="e79dc-124">再次按一下 [**啟動**] 按鈕旁的下拉式箭號，此時您應該會看到剛才新增的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="e79dc-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="e79dc-125">選取要建立並部署至 HoloLens 的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="e79dc-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span> 

>[!NOTE]
><span data-ttu-id="e79dc-126">建立裝置可能需要重新編譯著色器（特別是在第一次執行時）-這可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="e79dc-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="e79dc-127">請勿讓裝置進入睡眠狀態，直到應用程式執行（您可能必須磨損）。</span><span class="sxs-lookup"><span data-stu-id="e79dc-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="e79dc-128">否則，著色器編譯將會失敗！</span><span class="sxs-lookup"><span data-stu-id="e79dc-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="e79dc-129">透過裝置入口網站部署至裝置</span><span class="sxs-lookup"><span data-stu-id="e79dc-129">Deploying to device via device portal</span></span>

<span data-ttu-id="e79dc-130">您可以在消費者入門 with Unreal 教學課程系列的最後一節中，找到有關[封裝和部署應用程式](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)的詳細指示。</span><span class="sxs-lookup"><span data-stu-id="e79dc-130">You can find detailed instructions on [packaging and deploying an app](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>
