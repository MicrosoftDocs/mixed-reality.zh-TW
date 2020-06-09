---
title: HoloLens 研究模式
description: 使用 HoloLens 的 Research 模式，應用程式可以存取金鑰裝置感應器串流（深度、環境追蹤和 IR-反射率）。
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: 研究模式，cv，rs4，電腦視覺，research，HoloLens，HoloLens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533100"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="badba-104">HoloLens 研究模式</span><span class="sxs-lookup"><span data-stu-id="badba-104">HoloLens Research mode</span></span>

## <a name="overview"></a><span data-ttu-id="badba-105">概觀</span><span class="sxs-lookup"><span data-stu-id="badba-105">Overview</span></span>

<span data-ttu-id="badba-106">Research 模式是在第1代 HoloLens 中引進，可讓您存取裝置上的主要感應器，特別是針對不適合部署的研究應用程式。</span><span class="sxs-lookup"><span data-stu-id="badba-106">Research mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="badba-107">您現在可以從下列輸入收集資料：</span><span class="sxs-lookup"><span data-stu-id="badba-107">You can now gather data from the following inputs:</span></span>

* <span data-ttu-id="badba-108">**可見的光線環境追蹤攝影機**-供系統用來進行頭追蹤和地圖建築物。</span><span class="sxs-lookup"><span data-stu-id="badba-108">**Visible Light Environment Tracking Cameras** - Used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="badba-109">**深度相機**–以兩種模式運作：</span><span class="sxs-lookup"><span data-stu-id="badba-109">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="badba-110">短期擲回、高頻率（30 FPS）用於[手動追蹤](interaction-fundamentals.md)的近深度檢測</span><span class="sxs-lookup"><span data-stu-id="badba-110">Short-throw, high-frequency (30 FPS) near-depth sensing used for [Hand Tracking](interaction-fundamentals.md)</span></span>
    + <span data-ttu-id="badba-111">[空間對應](spatial-mapping.md)所使用的長時間擲回、低頻率（1-5 FPS）深度感應</span><span class="sxs-lookup"><span data-stu-id="badba-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>
* <span data-ttu-id="badba-112">**兩個版本的 IR 反射率串流**-由 HoloLens 用來計算深度。</span><span class="sxs-lookup"><span data-stu-id="badba-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="badba-113">這些映射是由紅外線所照亮，並不會受到環境可見光線的影響。</span><span class="sxs-lookup"><span data-stu-id="badba-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="badba-114">如果您使用 HoloLens 2，您也可以存取下列輸入：</span><span class="sxs-lookup"><span data-stu-id="badba-114">If you're using a HoloLens 2 you will also be able to access the following inputs:</span></span>

* <span data-ttu-id="badba-115">**加速**計–系統用來判斷沿著 X、Y 和 Z 軸和引力的線性加速。</span><span class="sxs-lookup"><span data-stu-id="badba-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="badba-116">**Gyro** –由系統用來判斷旋轉。</span><span class="sxs-lookup"><span data-stu-id="badba-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="badba-117">**磁力計**–由系統用來估計絕對方向。</span><span class="sxs-lookup"><span data-stu-id="badba-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

<span data-ttu-id="badba-118">![研究模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="badba-118">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="badba-119">*測試應用程式的混合現實捕捉，會顯示 Research 模式中提供的八個感應器串流*</span><span class="sxs-lookup"><span data-stu-id="badba-119">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

> [!NOTE]
> <span data-ttu-id="badba-120">Research 模式功能已新增為 HoloLens 的[Windows 10 2018 年4月更新](release-notes-april-2018.md)的一部分，且在舊版中無法使用。</span><span class="sxs-lookup"><span data-stu-id="badba-120">The Research Mode feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

## <a name="usage"></a><span data-ttu-id="badba-121">使用方式</span><span class="sxs-lookup"><span data-stu-id="badba-121">Usage</span></span>

<span data-ttu-id="badba-122">研究模式是針對在電腦視覺和機器人領域中探索新想法的學術和產業研究人員所設計。</span><span class="sxs-lookup"><span data-stu-id="badba-122">Research mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="badba-123">它不適用於部署在企業環境中的應用程式，或透過 Microsoft Store 或其他散發通道提供。</span><span class="sxs-lookup"><span data-stu-id="badba-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="badba-124">此外，Microsoft 不保證未來的硬體或作業系統更新將會支援研究模式或對等功能。</span><span class="sxs-lookup"><span data-stu-id="badba-124">Additionally, Microsoft doesn't provide assurances that research mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="badba-125">不過，這不應該阻止您使用它來開發和測試新的想法！</span><span class="sxs-lookup"><span data-stu-id="badba-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="badba-126">安全性與效能</span><span class="sxs-lookup"><span data-stu-id="badba-126">Security and performance</span></span>

<span data-ttu-id="badba-127">請注意，啟用 research 模式比在正常情況下使用 HoloLens 2 的電池電力更高。</span><span class="sxs-lookup"><span data-stu-id="badba-127">Be aware that enabling research mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="badba-128">即使使用研究模式功能的應用程式不在執行中，也是如此。</span><span class="sxs-lookup"><span data-stu-id="badba-128">This is true even if the application using the research mode features is not running.</span></span>  <span data-ttu-id="badba-129">啟用此模式也可以降低裝置的整體安全性，因為應用程式可能會誤用感應器資料。</span><span class="sxs-lookup"><span data-stu-id="badba-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="badba-130">您可以在[HoloLens 安全性常見問題](https://docs.microsoft.com/hololens/hololens-faq-security)中找到更多有關裝置安全性的資訊。</span><span class="sxs-lookup"><span data-stu-id="badba-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  


## <a name="device-support"></a><span data-ttu-id="badba-131">裝置支援</span><span class="sxs-lookup"><span data-stu-id="badba-131">Device support</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><span data-ttu-id="badba-132"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="badba-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="badba-133"><a href="hololens-hardware-details.md"><strong>HoloLens 第1代</strong></a></span><span class="sxs-lookup"><span data-stu-id="badba-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td><span data-ttu-id="badba-134">Head 追蹤攝影機</span><span class="sxs-lookup"><span data-stu-id="badba-134">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="badba-135">✔️</span><span class="sxs-lookup"><span data-stu-id="badba-135">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="badba-136">深度 & IR 相機</span><span class="sxs-lookup"><span data-stu-id="badba-136">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="badba-137">✔️</span><span class="sxs-lookup"><span data-stu-id="badba-137">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="badba-138">加速計</span><span class="sxs-lookup"><span data-stu-id="badba-138">Accelerometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="badba-139">迴轉儀</span><span class="sxs-lookup"><span data-stu-id="badba-139">Gyroscope</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="badba-140">磁力計</span><span class="sxs-lookup"><span data-stu-id="badba-140">Magnetometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="badba-141">HoloLens 2 的 Research 模式支援預計會在2020年7月提供公開預覽，並將包含上述所有功能。</span><span class="sxs-lookup"><span data-stu-id="badba-141">Research Mode support for HoloLens 2 is expected to be available in public preview in July 2020 and will include all the features listed above.</span></span> <span data-ttu-id="badba-142">請回來查看以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="badba-142">Please check back for more information.</span></span> 

## <a name="enabling-research-mode"></a><span data-ttu-id="badba-143">啟用研究模式</span><span class="sxs-lookup"><span data-stu-id="badba-143">Enabling Research mode</span></span>

<span data-ttu-id="badba-144">Research 模式是「開發人員模式」的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="badba-144">Research mode is an extension of Developer Mode.</span></span> <span data-ttu-id="badba-145">開始之前，必須先啟用裝置的開發人員功能，才能存取 research 模式設定：</span><span class="sxs-lookup"><span data-stu-id="badba-145">Before starting, the developer features of the device need to be enabled to access the research mode settings:</span></span> 

* <span data-ttu-id="badba-146">開啟 [**開始] 功能表 > 設定**]，然後選取 [**更新**]。</span><span class="sxs-lookup"><span data-stu-id="badba-146">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="badba-147">**為開發人員**選取並啟用**開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="badba-147">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="badba-148">向下滾動並啟用 [**裝置入口網站**]。</span><span class="sxs-lookup"><span data-stu-id="badba-148">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="badba-149">啟用開發人員功能之後，請[連接到裝置入口網站](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens)以啟用研究模式功能。</span><span class="sxs-lookup"><span data-stu-id="badba-149">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the research mode features.</span></span>

<span data-ttu-id="badba-150">在*HoloLens 第1代*上：</span><span class="sxs-lookup"><span data-stu-id="badba-150">On *HoloLens 1st Gen*:</span></span>

* <span data-ttu-id="badba-151">前往**裝置入口網站**中的 [**系統 > 研究模式]** 。</span><span class="sxs-lookup"><span data-stu-id="badba-151">Go to **System > Research mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="badba-152">選取 [**允許存取感應器串流**]。</span><span class="sxs-lookup"><span data-stu-id="badba-152">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="badba-153">從頁面頂端的 [**電源**] 功能表項目重新開機裝置。</span><span class="sxs-lookup"><span data-stu-id="badba-153">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="badba-154">一旦您重新開機裝置，透過**裝置入口網站**載入的應用程式就可以存取研究模式串流。</span><span class="sxs-lookup"><span data-stu-id="badba-154">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research mode streams.</span></span>

<span data-ttu-id="badba-155">![HoloLens 裝置入口網站的 [研究模式] 索引標籤](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="badba-155">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="badba-156">*HoloLens 裝置入口網站中的 Research 強制回應視窗*</span><span class="sxs-lookup"><span data-stu-id="badba-156">*Research mode window in the HoloLens Device Portal*</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="badba-157">在您的應用程式中使用感應器資料</span><span class="sxs-lookup"><span data-stu-id="badba-157">Using sensor data in your apps</span></span>

<span data-ttu-id="badba-158">*HoloLens 第1代*</span><span class="sxs-lookup"><span data-stu-id="badba-158">*HoloLens 1st Gen*</span></span>

<span data-ttu-id="badba-159">應用程式可以使用透過[媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)存取相片和攝影機串流的相同方式來存取感應器串流資料。</span><span class="sxs-lookup"><span data-stu-id="badba-159">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="badba-160">所有適用于 HoloLens 開發的 Api 也會以 Research 模式提供。</span><span class="sxs-lookup"><span data-stu-id="badba-160">All APIs that work for HoloLens development are also available in Research mode.</span></span> <span data-ttu-id="badba-161">特別是，應用程式會確切知道 HoloLens 在每個感應器框架捕獲時間的6DoF 空間。</span><span class="sxs-lookup"><span data-stu-id="badba-161">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="badba-162">您可以找到如何存取各種研究模式串流的範例應用程式、如何使用[內建函式和 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)，以及如何在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存放庫存放庫中記錄串流。</span><span class="sxs-lookup"><span data-stu-id="badba-162">You can find sample applications on how to access the various Research mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="badba-163">目前，HoloLensForCV 範例不適用於 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="badba-163">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="known-issues"></a><span data-ttu-id="badba-164">已知問題</span><span class="sxs-lookup"><span data-stu-id="badba-164">Known issues</span></span>

<span data-ttu-id="badba-165">您可以使用 HoloLensForCV 存放庫中的[問題追蹤](https://github.com/Microsoft/HololensForCV/issues)程式來遵循已知問題。</span><span class="sxs-lookup"><span data-stu-id="badba-165">You can use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to follow known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="badba-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="badba-166">See also</span></span>

* [<span data-ttu-id="badba-167">Microsoft 媒體基礎</span><span class="sxs-lookup"><span data-stu-id="badba-167">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="badba-168">HoloLensForCV GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="badba-168">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="badba-169">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="badba-169">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
