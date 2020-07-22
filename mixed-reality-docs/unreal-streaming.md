---
title: Unreal 中的串流
description: Unreal 至 HoloLens 2 的串流指南
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 串流, 電腦, 全像攝影應用程式遠端處理, 全像攝影遠端播放程式, 文件
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: d25efbcf83e45749cc4eb8b99581b71105c59c9d
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303529"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="496ab-104">Unreal 中的串流</span><span class="sxs-lookup"><span data-stu-id="496ab-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="496ab-105">概觀</span><span class="sxs-lookup"><span data-stu-id="496ab-105">Overview</span></span>
<span data-ttu-id="496ab-106">從電腦串流至 HoloLens 可提供兩大優點：</span><span class="sxs-lookup"><span data-stu-id="496ab-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="496ab-107">可讓您的混合實境應用程式利用電腦的計算能力。</span><span class="sxs-lookup"><span data-stu-id="496ab-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="496ab-108">有助於加快開發反覆運算的時間。</span><span class="sxs-lookup"><span data-stu-id="496ab-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="496ab-109">若要開始使用，您必須將[全像攝影遠端播放程式](holographic-remoting-player.md)下載到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="496ab-109">To get started, you'll need to download the [Holographic Remoting Player](holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="496ab-110">這可讓您的應用程式從下列來源直接串流至 HoloLens 上的遠端播放程式：</span><span class="sxs-lookup"><span data-stu-id="496ab-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="496ab-111">Unreal Engine 編輯器</span><span class="sxs-lookup"><span data-stu-id="496ab-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="496ab-112">已封裝的 Windows 可執行檔</span><span class="sxs-lookup"><span data-stu-id="496ab-112">A packaged Windows executable</span></span> 

<span data-ttu-id="496ab-113">進行串流時，您可以存取您在裝置上執行應用程式時可用的絕大多數 HoloLens 功能。</span><span class="sxs-lookup"><span data-stu-id="496ab-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="496ab-114">其中包括[手部關節追蹤](unreal-hand-tracking.md) (如果您是在 HoloLens 2 上)、[空間對應](unreal-spatial-mapping.md)和[空間錨點](unreal-spatial-anchors.md)，但不包括此[限制清單](holographic-remoting-troubleshooting.md)上的功能。</span><span class="sxs-lookup"><span data-stu-id="496ab-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="496ab-115">串流品質高度取決於您的 wifi 網路強度。</span><span class="sxs-lookup"><span data-stu-id="496ab-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="496ab-116">全像攝影遠端處理播放程式會自動啟用所有功能。</span><span class="sxs-lookup"><span data-stu-id="496ab-116">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="496ab-117">如果您發現某個功能需要使用者權限 (例如：眼睛追蹤)，才能透過串流方式來使用，但在裝置上執行時則不用，請檢查並確定您已在專案設定下啟用適當的功能。</span><span class="sxs-lookup"><span data-stu-id="496ab-117">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="496ab-118">裝置支援</span><span class="sxs-lookup"><span data-stu-id="496ab-118">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="496ab-119"><strong>來源</strong></span><span class="sxs-lookup"><span data-stu-id="496ab-119"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="496ab-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="496ab-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="496ab-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="496ab-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="496ab-122"><strong>沉浸式頭戴裝置</strong></span><span class="sxs-lookup"><span data-stu-id="496ab-122"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="496ab-123">Unreal 編輯器</span><span class="sxs-lookup"><span data-stu-id="496ab-123">Unreal editor</span></span></td>
        <td><span data-ttu-id="496ab-124">✔️</span><span class="sxs-lookup"><span data-stu-id="496ab-124">✔️</span></span></td>
        <td><span data-ttu-id="496ab-125">✔️</span><span class="sxs-lookup"><span data-stu-id="496ab-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="496ab-126">Windows 套件</span><span class="sxs-lookup"><span data-stu-id="496ab-126">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="496ab-127">✔️</span><span class="sxs-lookup"><span data-stu-id="496ab-127">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="496ab-128">從 Unreal 編輯器進行串流</span><span class="sxs-lookup"><span data-stu-id="496ab-128">Streaming from the Unreal editor</span></span>

<span data-ttu-id="496ab-129">身為開發人員，您會發現從 Unreal 編輯器串流至 HoloLens 裝置可在測試時提供很大的好處，也就是您不再需要等到應用程式完成建置和部署，才能試用您的更新。</span><span class="sxs-lookup"><span data-stu-id="496ab-129">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="496ab-130">您可以在「開始使用 Unreal」教學課程系列的最後一節中，找到[從 Unreal 編輯器進行串流](unreal-uxt-ch6.md#device-only-streaming)的詳細指示。</span><span class="sxs-lookup"><span data-stu-id="496ab-130">You can find detailed instructions on [streaming from the Unreal editor](unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="496ab-131">從已封裝的 Windows 可執行檔進行串流</span><span class="sxs-lookup"><span data-stu-id="496ab-131">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="496ab-132">從 Unreal 4.25.1 開始，您可以依照下列步驟，從已封裝的 Windows 可執行檔將應用程式串流至 HoloLens 2 裝置：</span><span class="sxs-lookup"><span data-stu-id="496ab-132">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="496ab-133">在 [編輯器] 功能表中，移至 [檔案] > [封裝專案] > [Windows]。</span><span class="sxs-lookup"><span data-stu-id="496ab-133">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="496ab-134">選擇要儲存套件的位置，然後按一下 [選取資料夾]。</span><span class="sxs-lookup"><span data-stu-id="496ab-134">Choose a location to save your package and click **Select Folder**.</span></span>

2. <span data-ttu-id="496ab-135">套件完成建置後，請在 HoloLens 2 上開啟 [全像攝影遠端播放程式]，並記下 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="496ab-135">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="496ab-136">將 [全像攝影遠端播放程式] 保持開啟，並使用命令列提示字元執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="496ab-136">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="496ab-137">切換至套件儲存所在的本機目錄中。</span><span class="sxs-lookup"><span data-stu-id="496ab-137">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="496ab-138">輸入下列命令：```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="496ab-138">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="496ab-139">系統應該會自動使用您專案設定中的應用程式名稱來建立 Windows 套件。</span><span class="sxs-lookup"><span data-stu-id="496ab-139">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="496ab-140">如果這些設定因某些原因而有所不同，請在命令提示字元中使用 Windows 可執行檔名稱。</span><span class="sxs-lookup"><span data-stu-id="496ab-140">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="496ab-141">按 Enter 鍵，您的應用程式即會開始串流！</span><span class="sxs-lookup"><span data-stu-id="496ab-141">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="496ab-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="496ab-142">See also</span></span>
* [<span data-ttu-id="496ab-143">全像攝影遠端處理版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="496ab-143">Holographic remoting version history</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="496ab-144">撰寫自訂全像攝影遠端播放應用程式</span><span class="sxs-lookup"><span data-stu-id="496ab-144">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="496ab-145">建立全像攝影遠端處理的連線安全</span><span class="sxs-lookup"><span data-stu-id="496ab-145">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
