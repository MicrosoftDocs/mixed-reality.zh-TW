---
title: 6. 封裝並部署至裝置或模擬器
description: 教學課程系列的第 6 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 99c431920c72cf85fed5a0eec6fc72ddf9fb112c
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330229"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="d02b8-104">6.封裝並部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="d02b8-104">6. Packaging & deploying to device or emulator</span></span>

## <a name="overview"></a><span data-ttu-id="d02b8-105">概觀</span><span class="sxs-lookup"><span data-stu-id="d02b8-105">Overview</span></span>

<span data-ttu-id="d02b8-106">在上一個教學課程中，您已新增一個簡單按鈕，將棋子重設為其原始位置。</span><span class="sxs-lookup"><span data-stu-id="d02b8-106">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="d02b8-107">在此最後一節中，您將會準備好要在 HoloLens 2 或模擬器上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d02b8-107">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="d02b8-108">若有 HoloLens 2，您可以從電腦串流或封裝應用程式，以直接在裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="d02b8-108">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="d02b8-109">如果沒有裝置，您會封裝應用程式以在模擬器上執行。</span><span class="sxs-lookup"><span data-stu-id="d02b8-109">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="d02b8-110">本節結束時，您將會有一個可以播放的已部署混合實境應用程式，這是透過互動和 UI 完成的。</span><span class="sxs-lookup"><span data-stu-id="d02b8-110">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="d02b8-111">目標</span><span class="sxs-lookup"><span data-stu-id="d02b8-111">Objectives</span></span>

* <span data-ttu-id="d02b8-112">[僅限裝置] 利用全像應用程式遠端處理串流至 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d02b8-112">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="d02b8-113">封裝應用程式並將其部署至 HoloLens 2 裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="d02b8-113">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="d02b8-114">[僅限裝置] 串流</span><span class="sxs-lookup"><span data-stu-id="d02b8-114">[Device Only] Streaming</span></span>
<span data-ttu-id="d02b8-115">在此情況下，[全像遠端處理](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting)表示將電腦或獨立 UWP 裝置中的資料串流至 HoloLens 2，而不是切換管道。</span><span class="sxs-lookup"><span data-stu-id="d02b8-115">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) in this case means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="d02b8-116">其運作方式是遠端主機應用程式會從 HoloLens 接收輸入資料流程、在虛擬沉浸式檢視中呈現內容，以及透過 Wi-fi 將內容框架串流回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d02b8-116">The way this works is a remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="d02b8-117">串流可讓您將遠端沉浸式檢視新增至現有的桌上型電腦軟體，並可存取更多系統資源。</span><span class="sxs-lookup"><span data-stu-id="d02b8-117">Streaming allows you to add remote immersive views into existing desktop PC software and has access to more system resources.</span></span> 

<span data-ttu-id="d02b8-118">如果您是使用國際象棋應用程式前往此路由，將需要進行一些事項：</span><span class="sxs-lookup"><span data-stu-id="d02b8-118">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="d02b8-119">從您的 HoloLens 2 上的 Microsoft Store 安裝**全像攝影遠端播放程式**並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d02b8-119">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span>

2.  <span data-ttu-id="d02b8-120">移至 [編輯] > [專案設定]，然後勾選 [全像攝影遠端處理] 區段中的 [啟用遠端處理]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-120">Go to **Edit > Project Settings** and check **enable remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="d02b8-121">重新啟動編輯器、[尋找您裝置的 IP 位址](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi) 並將其輸入，然後按一下 [連線]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-121">Restart the editor, [find your device's IP address](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi) and enter it, then click **Connect**.</span></span>

<span data-ttu-id="d02b8-122">連線之後，請按一下 [播放] 按鈕右邊的下拉箭號，然後選取 [VR 預覽]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-122">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="d02b8-123">這會在 [VR 預覽] 視窗中執行應用程式，進而串流至 HoloLens 頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="d02b8-123">This will run the app in the VR Preview Window, which is streamed to the HoloLens headset.</span></span> 

## <a name="packaging-and-deploying-the-app"></a><span data-ttu-id="d02b8-124">封裝和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="d02b8-124">Packaging and deploying the app</span></span> 

>[!NOTE]
><span data-ttu-id="d02b8-125">如果這是您第一次為適用於 HoloLens 的 Unreal 應用程式進行封裝，則需從 Epic Launcher 下載支援的檔案。</span><span class="sxs-lookup"><span data-stu-id="d02b8-125">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> 
>- <span data-ttu-id="d02b8-126">移至 Epic Games Launcher 中的 [程式庫] 索引標籤、選取 [啟動] 旁邊的下拉箭號，然後按一下 [選項]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-126">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span> 
>- <span data-ttu-id="d02b8-127">在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-127">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="d02b8-128">![專案設定 - 描述](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="d02b8-128">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="d02b8-129">移至 [編輯] > [專案設定]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-129">Go to **Edit > Project Settings**.</span></span> 
    * <span data-ttu-id="d02b8-130">在 [專案] > [描述] > [關於] > [專案名稱] 底下，新增專案名稱。</span><span class="sxs-lookup"><span data-stu-id="d02b8-130">Add a project name under **Project > Description > About > Project Name**.</span></span> 
    * <span data-ttu-id="d02b8-131">在 [專案] > [描述] > [發行者] > [公司辨別名稱] 底下，新增 **CN={INSERT COMPANY NAME}** 。</span><span class="sxs-lookup"><span data-stu-id="d02b8-131">Add **CN={INSERT COMPANY NAME}** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d02b8-132">將其中一個欄位留空會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="d02b8-132">Leaving either of these fields blank will result in an error.</span></span> 

![專案設定 - 描述](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="d02b8-134">在 [平台] > [HoloLens] 底下，啟用 [針對 HoloLens 模擬進行建置] 和/或 [針對 HoloLens 裝置進行建置]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-134">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="d02b8-135">按一下 [封裝] (在 [簽署憑證] 旁邊) 區段中的 [產生新項目]，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="d02b8-135">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**), then return to the Main window.</span></span>

![專案設定 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="d02b8-137">移至 [檔案] > [封裝專案]，然後選取 [HoloLens]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-137">Go to **File > Package Project** and select **HoloLens**.</span></span> 
    * <span data-ttu-id="d02b8-138">建立新資料夾來儲存您的封裝，然後按一下 [選取資料夾]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-138">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="d02b8-139">一旦封裝了應用程式後，請開啟 [Windows 裝置入口網站](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)移至 [檢視] > [應用程式]，然後尋找 [部署應用程式] 區段。</span><span class="sxs-lookup"><span data-stu-id="d02b8-139">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="d02b8-140">按一下 [瀏覽 ...]、移至您的 **ChessApp.appxbundle** 檔案，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="d02b8-140">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span> 

    * <span data-ttu-id="d02b8-141">如果這是您第一次在裝置上安裝應用程式，請勾選 [允許我選取架構套件] 旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="d02b8-141">Check the box next to **Allow me to select framework packages** if this is the first time you're installing the app on your device.</span></span> 
    * <span data-ttu-id="d02b8-142">在下一個對話方塊中，包含適當的 **VCLibs** 和 **appx** 檔案 (若為裝置則為 arm64，若為模擬器則為 x64)。</span><span class="sxs-lookup"><span data-stu-id="d02b8-142">In the next dialogue, include the appropriate **VCLibs** and **appx** files (arm64 for device, x64 for emulator).</span></span> <span data-ttu-id="d02b8-143">您可以在儲存套件的資料夾內 **HoloLens** 底下找到這些檔案。</span><span class="sxs-lookup"><span data-stu-id="d02b8-143">You can find these under **HoloLens** inside the folder where you saved your package.</span></span>

7.  <span data-ttu-id="d02b8-144">按一下 [安裝]</span><span class="sxs-lookup"><span data-stu-id="d02b8-144">Click **Install**</span></span>
    * <span data-ttu-id="d02b8-145">您現在可以移至 [所有應用程式]，然後點選新安裝的應用程式來執行，也可以直接從 **Windows 裝置入口網站**啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="d02b8-145">You can now go to **All Apps** and tap the the newly installed app to run it, or you can start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="d02b8-146">恭喜！</span><span class="sxs-lookup"><span data-stu-id="d02b8-146">Congratulations!</span></span> <span data-ttu-id="d02b8-147">您已完成是 HoloLens 混合實境應用程式，並可以開始進行。</span><span class="sxs-lookup"><span data-stu-id="d02b8-147">You're HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="d02b8-148">不過，這不是盡頭。</span><span class="sxs-lookup"><span data-stu-id="d02b8-148">However, this isn't the end of the road.</span></span> <span data-ttu-id="d02b8-149">MRTK 有許多獨立功能，您可以將其新增至專案，包括空間對應、注視和語音輸入，甚至是 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="d02b8-149">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="d02b8-150">如需這些功能的詳細資訊，請參閱 [Unreal 開發概觀](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)。</span><span class="sxs-lookup"><span data-stu-id="d02b8-150">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>