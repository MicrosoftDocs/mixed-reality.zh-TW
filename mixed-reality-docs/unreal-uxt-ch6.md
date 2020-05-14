---
title: 6. 封裝並部署至裝置或模擬器
description: 教學課程的第 6 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 35b18e4bb289438f94433827846e94d1014385db
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840377"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="1c9d1-104">6.封裝並部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="1c9d1-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="1c9d1-105">本節會逐步引導您完成準備應用程式以在 HoloLens 2 裝置或模擬器上執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="1c9d1-106">如果您有裝置，您可以從電腦串流至裝置，或封裝應用程式以直接在裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="1c9d1-107">如果您沒有裝置，您必須封裝應用程式，才能在模擬器上執行。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="1c9d1-108">目標</span><span class="sxs-lookup"><span data-stu-id="1c9d1-108">Objectives</span></span>

* <span data-ttu-id="1c9d1-109">[僅限裝置] 透過全像應用程式遠端處理，將您的應用程式串流至 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1c9d1-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="1c9d1-110">封裝您的應用程式並將其部署至 HoloLens 2 裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="1c9d1-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="1c9d1-111">[僅限裝置] 串流</span><span class="sxs-lookup"><span data-stu-id="1c9d1-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="1c9d1-112">從您的 HoloLens 2 上的 Microsoft Store 安裝**全像攝影遠端播放程式**並執行應用程式</span><span class="sxs-lookup"><span data-stu-id="1c9d1-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="1c9d1-113">移至 [編輯] > [專案設定]  。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="1c9d1-114">在 [全像攝影遠端處理] 區段中，勾選核取方塊以啟用遠端處理，然後重新啟動編輯器。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="1c9d1-115">輸入您裝置的 IP 位址，然後按一下 [連線]。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="1c9d1-116">連線之後，請在 UE4 編輯器中按一下 [播放] 按鈕右邊的下拉箭號，然後選取 [VR 預覽]。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="1c9d1-117">封裝和部署您的應用程式</span><span class="sxs-lookup"><span data-stu-id="1c9d1-117">Package and deploy your app</span></span> 

1.  <span data-ttu-id="1c9d1-118">移至 [編輯] > [專案設定]  。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-118">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="1c9d1-119">在 [專案] > [描述] > [關於] > [專案名稱]  底下，為您的專案命名。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-119">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="1c9d1-120">在 [專案] > [描述] > [發行者] > [公司辨別名稱]  底下，輸入 “CN={INSERT COMPANY NAME}”。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-120">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="1c9d1-121">將其中一個欄位留空會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-121">Leaving either of these fields blank will result in an error.</span></span> 

![專案設定 - 描述](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="1c9d1-123">在 [平台] > [HoloLens]  底下，根據您的目標選擇模擬及/或裝置。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-123">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="1c9d1-124">在 [封裝]  區段的 [簽署憑證]  旁，按一下 [產生新的]  按鈕，以產生新的簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-124">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="1c9d1-125">返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-125">Return to the Main window.</span></span>

![專案設定 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="1c9d1-127">移至 [檔案] > [封裝專案]  ，然後選取 [HoloLens]  。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-127">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="1c9d1-128">建立新資料夾來儲存您的封裝，然後按一下 [選取資料夾]  。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-128">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="1c9d1-129">成功封裝應用程式之後，請開啟 **Windows 裝置入口網站**，移至 [檢視] > [應用程式]  ，並尋找**部署應用程式**一節。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-129">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="1c9d1-130">按一下 [瀏覽...]  ，瀏覽至您的 **ChessApp.appxbundle** 檔案。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-130">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="1c9d1-131">按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-131">Click **Open**.</span></span> 

    * <span data-ttu-id="1c9d1-132">如果這是您第一次在裝置上安裝應用程式，請勾選 [允許我選取架構套件]  旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-132">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="1c9d1-133">在下一個對話方塊中，包含適當的 VCLibs appx 檔案 (針對裝置為 arm64、針對模擬器為 x64)。</span><span class="sxs-lookup"><span data-stu-id="1c9d1-133">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="1c9d1-134">按一下 [安裝] </span><span class="sxs-lookup"><span data-stu-id="1c9d1-134">Click **Install**</span></span>

<span data-ttu-id="1c9d1-135">恭喜您完成本教學課程！</span><span class="sxs-lookup"><span data-stu-id="1c9d1-135">Congratulations on finishing this tutorial!</span></span>  