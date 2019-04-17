---
title: 取得 HoloLens 的應用程式
description: 描述 HoloLens，同時透過 Microsoft Store 和側載安裝應用程式。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 側載、 側載、 側載、 市集、 uwp、 應用程式，安裝
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591129"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="1add5-104">取得 HoloLens 的應用程式</span><span class="sxs-lookup"><span data-stu-id="1add5-104">Get apps for HoloLens</span></span>

<span data-ttu-id="1add5-105">為 Windows 10 裝置、 HoloLens 支援許多現有的 UWP 應用程式，從應用程式市集，以及專為 HoloLens 建置新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1add5-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="1add5-106">上，您可能甚至想要[開發](development-overview.md)並安裝您自己的應用程式，或您的朋友 ！</span><span class="sxs-lookup"><span data-stu-id="1add5-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="1add5-107">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="1add5-107">Installing Apps</span></span>

<span data-ttu-id="1add5-108">有三種方式可在您的 HoloLens 上安裝新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1add5-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="1add5-109">主要方法是從 Windows 市集安裝新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1add5-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="1add5-110">不過，您也可以安裝自己的應用程式使用裝置入口網站或從 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="1add5-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="1add5-111">從 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="1add5-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="1add5-112">執行[bloom](gestures.md#bloom)以開啟軌跡[開始 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="1add5-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="1add5-113">選取市集應用程式，然後點選 將此圖格放入您的世界。</span><span class="sxs-lookup"><span data-stu-id="1add5-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="1add5-114">市集應用程式開啟後，請使用 [搜尋] 列，尋找任何所需的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1add5-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="1add5-115">選取 **取得**或是**安裝**（購買可能會需要） 的應用程式的頁面上。</span><span class="sxs-lookup"><span data-stu-id="1add5-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="1add5-116">使用裝置入口網站安裝應用程式封裝</span><span class="sxs-lookup"><span data-stu-id="1add5-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="1add5-117">從建立連線[裝置入口網站](using-the-windows-device-portal.md)目標 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="1add5-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="1add5-118">瀏覽至**應用程式**在左側導覽中的頁面。</span><span class="sxs-lookup"><span data-stu-id="1add5-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="1add5-119">底下**應用程式套件**瀏覽至您的應用程式相關聯的.appx 檔案。</span><span class="sxs-lookup"><span data-stu-id="1add5-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="1add5-120">請務必參考任何相關聯的相依性和憑證檔案。</span><span class="sxs-lookup"><span data-stu-id="1add5-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="1add5-121">按一下 **移**。</span><span class="sxs-lookup"><span data-stu-id="1add5-121">Click **Go**.</span></span>

<span data-ttu-id="1add5-122">![在 Microsoft HoloLens 上的 Windows Device Portal 中安裝的應用程式表單](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="1add5-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="1add5-123">使用 Windows Device Portal HoloLens 上安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="1add5-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="1add5-124">從 Microsoft Visual Studio 2015 部署</span><span class="sxs-lookup"><span data-stu-id="1add5-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="1add5-125">開啟您的應用程式的 Visual Studio 方案 （.sln） 檔。</span><span class="sxs-lookup"><span data-stu-id="1add5-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="1add5-126">開啟專案的**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1add5-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="1add5-127">選取下列的組建組態：主版/x86/遠端機器。</span><span class="sxs-lookup"><span data-stu-id="1add5-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="1add5-128">當您選取遠端電腦：</span><span class="sxs-lookup"><span data-stu-id="1add5-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="1add5-129">請務必地址點 HoloLens 的 WiFi IP 位址。</span><span class="sxs-lookup"><span data-stu-id="1add5-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="1add5-130">將驗證設定為通用 （未加密的通訊協定）。</span><span class="sxs-lookup"><span data-stu-id="1add5-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="1add5-131">建置您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="1add5-131">Build your solution.</span></span>
6. <span data-ttu-id="1add5-132">按一下 **遠端機器**按鈕，將部署應用程式從開發電腦，以您 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="1add5-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="1add5-133">如果您已經有現有的組建 HoloLens 上，選取 [是] 以重新安裝這個較新版本。</span><span class="sxs-lookup"><span data-stu-id="1add5-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="1add5-134">![在 Visual Studio 中的 Microsoft HoloLens 的應用程式的遠端機器部署](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="1add5-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="1add5-135">應用程式會安裝，並自動在您的 HoloLens 上啟動。</span><span class="sxs-lookup"><span data-stu-id="1add5-135">The application will install and auto launch on your HoloLens.</span></span>
