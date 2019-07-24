---
title: 取得 HoloLens 的應用程式
description: 說明如何透過 Microsoft Store 和側載安裝 HoloLens 的應用程式。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 側載, 側邊載入, 側載入, 存放區, uwp, 應用程式, 安裝
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522553"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="6f0b6-104">取得 HoloLens 的應用程式</span><span class="sxs-lookup"><span data-stu-id="6f0b6-104">Get apps for HoloLens</span></span>

<span data-ttu-id="6f0b6-105">作為 Windows 10 裝置, HoloLens 支援來自 app store 的許多現有 UWP 應用程式, 以及專為 HoloLens 建立的新應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="6f0b6-106">除此之外, 您甚至可能想要[開發](development-overview.md)和安裝自己的應用程式或朋友</span><span class="sxs-lookup"><span data-stu-id="6f0b6-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="6f0b6-107">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="6f0b6-107">Installing Apps</span></span>

<span data-ttu-id="6f0b6-108">有三種方式可在您的 HoloLens 上安裝新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="6f0b6-109">主要方法是從 Windows Store 安裝新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="6f0b6-110">不過, 您也可以使用裝置入口網站或從 Visual Studio 部署來安裝自己的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="6f0b6-111">從 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="6f0b6-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="6f0b6-112">執行[bloom](gestures.md#bloom)手勢以開啟 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="6f0b6-113">選取 [Store] 應用程式, 然後按一下 [將此磚放入您的世界]。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="6f0b6-114">儲存區應用程式開啟後, 使用搜尋列尋找任何想要的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="6f0b6-115">在應用程式頁面上選取 [**取得**] 或 [**安裝**] (可能需要購買)。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="6f0b6-116">使用裝置入口網站安裝應用程式套件</span><span class="sxs-lookup"><span data-stu-id="6f0b6-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="6f0b6-117">建立從[裝置入口網站](using-the-windows-device-portal.md)到目標 HoloLens 的連線。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="6f0b6-118">流覽至左側導覽中的 [**應用程式**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="6f0b6-119">在 [**應用程式套件**] 底下, 流覽至與您的應用程式相關聯的 .appx 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="6f0b6-120">請務必參考任何相關聯的相依性和憑證檔案。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="6f0b6-121">按一下 [**移至**]。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-121">Click **Go**.</span></span>

<span data-ttu-id="6f0b6-122">![在 Microsoft HoloLens 上的 Windows 裝置入口網站中安裝應用程式表單](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="6f0b6-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="6f0b6-123">使用 Windows 裝置入口網站在 HoloLens 上安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="6f0b6-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="6f0b6-124">從 Microsoft Visual Studio 2015 部署</span><span class="sxs-lookup"><span data-stu-id="6f0b6-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="6f0b6-125">開啟應用程式的 Visual Studio 方案 (.sln 檔案)。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="6f0b6-126">開啟專案的 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="6f0b6-127">選取下列組建設定:主要/x86/遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="6f0b6-128">當您選取 [遠端電腦] 時:</span><span class="sxs-lookup"><span data-stu-id="6f0b6-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="6f0b6-129">請確定該位址指向 HoloLens 的 WiFi IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="6f0b6-130">將驗證設定為通用 (未加密的通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="6f0b6-131">建立您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-131">Build your solution.</span></span>
6. <span data-ttu-id="6f0b6-132">按一下 [**遠端電腦**] 按鈕, 將應用程式從開發電腦部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="6f0b6-133">如果您已在 HoloLens 上擁有現有的組建, 請選取 [是] 以重新安裝這個較新的版本。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="6f0b6-134">![在 Visual Studio 中將應用程式的遠端機器部署至 Microsoft HoloLens](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="6f0b6-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="6f0b6-135">應用程式將會在您的 HoloLens 上安裝並自動啟動。</span><span class="sxs-lookup"><span data-stu-id="6f0b6-135">The application will install and auto launch on your HoloLens.</span></span>
