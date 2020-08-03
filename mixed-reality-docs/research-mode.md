---
title: HoloLens 研究模式
description: 使用 HoloLens 的 Research 模式，應用程式可以存取金鑰裝置感應器串流（深度、環境追蹤和 IR-反射率）。
author: hferrone
ms.author: v-haferr
ms.date: 07/31/2020
ms.topic: article
keywords: 研究模式，cv，rs4，電腦視覺，research，HoloLens，HoloLens 2
ms.openlocfilehash: dd49186d1218b6a6a6c9a8d5943159daad3bcefb
ms.sourcegitcommit: 36316e2658d3dfa804d798b9f4fb2f9186052144
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507692"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="a6d62-104">HoloLens 研究模式</span><span class="sxs-lookup"><span data-stu-id="a6d62-104">HoloLens Research Mode</span></span>

<span data-ttu-id="a6d62-105">Research 模式是在第1代 HoloLens 中引進，可讓您存取裝置上的主要感應器，特別是針對不適合部署的研究應用程式。</span><span class="sxs-lookup"><span data-stu-id="a6d62-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="a6d62-106">HoloLens 2 的研究模式保留 HoloLens 1 的功能，並新增額外串流的存取權：</span><span class="sxs-lookup"><span data-stu-id="a6d62-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="a6d62-107">**可見的光線環境追蹤攝影機**-系統用於 head 追蹤和地圖建築物的灰階相機。</span><span class="sxs-lookup"><span data-stu-id="a6d62-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="a6d62-108">**深度相機**–以兩種模式運作：</span><span class="sxs-lookup"><span data-stu-id="a6d62-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="a6d62-109">用於手動追蹤的 AHAT、高頻率（45 FPS）近深度檢測。</span><span class="sxs-lookup"><span data-stu-id="a6d62-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="a6d62-110">與第1版的簡短擲回模式不同的是，AHAT 提供的虛擬深度與1個計量以外的階段換行。</span><span class="sxs-lookup"><span data-stu-id="a6d62-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="a6d62-111">[空間對應](spatial-mapping.md)所使用的長時間擲回、低頻率（1-5 FPS）深度感應</span><span class="sxs-lookup"><span data-stu-id="a6d62-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>

* <span data-ttu-id="a6d62-112">**兩個版本的 IR 反射率串流**-由 HoloLens 用來計算深度。</span><span class="sxs-lookup"><span data-stu-id="a6d62-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="a6d62-113">這些映射是由紅外線所照亮，並不會受到環境可見光線的影響。</span><span class="sxs-lookup"><span data-stu-id="a6d62-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="a6d62-114">如果您使用 HoloLens 2，您也可以存取下列其他輸入：</span><span class="sxs-lookup"><span data-stu-id="a6d62-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="a6d62-115">**加速**計–系統用來判斷沿著 X、Y 和 Z 軸和引力的線性加速。</span><span class="sxs-lookup"><span data-stu-id="a6d62-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="a6d62-116">**Gyro** –由系統用來判斷旋轉。</span><span class="sxs-lookup"><span data-stu-id="a6d62-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="a6d62-117">**磁力計**–由系統用來估計絕對方向。</span><span class="sxs-lookup"><span data-stu-id="a6d62-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6d62-118">Research 模式目前為公開預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="a6d62-118">Research Mode is currently in Public Preview.</span></span> <span data-ttu-id="a6d62-119">HoloLens 2 範例、教學課程和完整 API 檔將在[ECCV 2020](https://eccv2020.eu/
 )的 Research 模式 Git 存放庫中提供。</span><span class="sxs-lookup"><span data-stu-id="a6d62-119">HoloLens 2 samples, tutorials, and full API documentation will be available at [ECCV 2020](https://eccv2020.eu/
 ) in the Research Mode Git repository.</span></span>

<span data-ttu-id="a6d62-120">![研究模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="a6d62-120">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="a6d62-121">*測試應用程式的混合現實捕捉，會顯示 Research 模式中提供的八個感應器串流*</span><span class="sxs-lookup"><span data-stu-id="a6d62-121">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="a6d62-122">使用量</span><span class="sxs-lookup"><span data-stu-id="a6d62-122">Usage</span></span>

<span data-ttu-id="a6d62-123">研究模式是針對在電腦視覺和機器人領域中探索新想法的學術和產業研究人員所設計。</span><span class="sxs-lookup"><span data-stu-id="a6d62-123">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="a6d62-124">它不適用於部署在企業環境中的應用程式，或透過 Microsoft Store 或其他散發通道提供。</span><span class="sxs-lookup"><span data-stu-id="a6d62-124">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="a6d62-125">此外，Microsoft 不保證未來的硬體或作業系統更新將會支援研究模式或對等功能。</span><span class="sxs-lookup"><span data-stu-id="a6d62-125">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="a6d62-126">不過，這不應該阻止您使用它來開發和測試新的想法！</span><span class="sxs-lookup"><span data-stu-id="a6d62-126">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="a6d62-127">安全性與效能</span><span class="sxs-lookup"><span data-stu-id="a6d62-127">Security and performance</span></span>

<span data-ttu-id="a6d62-128">請注意，啟用 Research 模式比在正常情況下使用 HoloLens 2 的電池電力更高。</span><span class="sxs-lookup"><span data-stu-id="a6d62-128">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="a6d62-129">即使使用研究模式功能的應用程式不在執行中，也是如此。</span><span class="sxs-lookup"><span data-stu-id="a6d62-129">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="a6d62-130">啟用此模式也可以降低裝置的整體安全性，因為應用程式可能會誤用感應器資料。</span><span class="sxs-lookup"><span data-stu-id="a6d62-130">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="a6d62-131">您可以在[HoloLens 安全性常見問題](https://docs.microsoft.com/hololens/hololens-faq-security)中找到更多有關裝置安全性的資訊。</span><span class="sxs-lookup"><span data-stu-id="a6d62-131">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="a6d62-132">裝置支援</span><span class="sxs-lookup"><span data-stu-id="a6d62-132">Device support</span></span>
<table><span data-ttu-id="a6d62-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="a6d62-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="a6d62-134"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="a6d62-134"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a6d62-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a6d62-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="a6d62-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="a6d62-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a6d62-137">Head 追蹤攝影機</span><span class="sxs-lookup"><span data-stu-id="a6d62-137">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="a6d62-138">✔️</span><span class="sxs-lookup"><span data-stu-id="a6d62-138">✔️</span></span></td>
        <td><span data-ttu-id="a6d62-139">✔️</span><span class="sxs-lookup"><span data-stu-id="a6d62-139">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a6d62-140">深度 & IR 相機</span><span class="sxs-lookup"><span data-stu-id="a6d62-140">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="a6d62-141">✔️</span><span class="sxs-lookup"><span data-stu-id="a6d62-141">✔️</span></span></td>
        <td><span data-ttu-id="a6d62-142">✔️</span><span class="sxs-lookup"><span data-stu-id="a6d62-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a6d62-143">加速計</span><span class="sxs-lookup"><span data-stu-id="a6d62-143">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a6d62-144">✔️</span><span class="sxs-lookup"><span data-stu-id="a6d62-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a6d62-145">迴轉儀</span><span class="sxs-lookup"><span data-stu-id="a6d62-145">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a6d62-146">✔️</span><span class="sxs-lookup"><span data-stu-id="a6d62-146">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a6d62-147">磁力計</span><span class="sxs-lookup"><span data-stu-id="a6d62-147">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a6d62-148">✔️</span><span class="sxs-lookup"><span data-stu-id="a6d62-148">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="a6d62-149">啟用研究模式（HoloLens 第1代和 HoloLens 2）</span><span class="sxs-lookup"><span data-stu-id="a6d62-149">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="a6d62-150">Research 模式是「開發人員模式」的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a6d62-150">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="a6d62-151">開始之前，必須先啟用裝置的開發人員功能，才能存取 Research 模式設定：</span><span class="sxs-lookup"><span data-stu-id="a6d62-151">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="a6d62-152">開啟 [**開始] 功能表 > 設定**]，然後選取 [**更新**]。</span><span class="sxs-lookup"><span data-stu-id="a6d62-152">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="a6d62-153">**為開發人員**選取並啟用**開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="a6d62-153">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="a6d62-154">向下捲動並啟用**裝置入口網站**。</span><span class="sxs-lookup"><span data-stu-id="a6d62-154">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="a6d62-155">啟用開發人員功能之後，請[連接到裝置入口網站](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens)以啟用研究模式功能：</span><span class="sxs-lookup"><span data-stu-id="a6d62-155">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="a6d62-156">前往**裝置入口網站**中的 [**系統 > 研究模式]** 。</span><span class="sxs-lookup"><span data-stu-id="a6d62-156">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="a6d62-157">選取 [**允許存取感應器串流**]。</span><span class="sxs-lookup"><span data-stu-id="a6d62-157">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="a6d62-158">從頁面頂端的 [**電源**] 功能表項目重新開機裝置。</span><span class="sxs-lookup"><span data-stu-id="a6d62-158">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="a6d62-159">一旦您重新開機裝置，透過**裝置入口網站**載入的應用程式就可以存取研究模式串流。</span><span class="sxs-lookup"><span data-stu-id="a6d62-159">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="a6d62-160">![HoloLens 裝置入口網站的 [研究模式] 索引標籤](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="a6d62-160">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="a6d62-161">*HoloLens 裝置入口網站中的 Research 強制回應視窗*</span><span class="sxs-lookup"><span data-stu-id="a6d62-161">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6d62-162">從組建19041.1356 開始提供 HoloLens 2 的研究模式。</span><span class="sxs-lookup"><span data-stu-id="a6d62-162">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="a6d62-163">如果您需要在先前的組建中存取，請註冊我們的[Insider preview](https://docs.microsoft.com/hololens/hololens-insider)計畫。</span><span class="sxs-lookup"><span data-stu-id="a6d62-163">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="a6d62-164">在您的應用程式中使用感應器資料</span><span class="sxs-lookup"><span data-stu-id="a6d62-164">Using sensor data in your apps</span></span>

<span data-ttu-id="a6d62-165">應用程式可以使用透過[媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)存取相片和攝影機串流的相同方式來存取感應器串流資料。</span><span class="sxs-lookup"><span data-stu-id="a6d62-165">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="a6d62-166">所有適用于 HoloLens 開發的 Api 也會以 Research 模式提供。</span><span class="sxs-lookup"><span data-stu-id="a6d62-166">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="a6d62-167">特別是，應用程式會確切知道 HoloLens 在每個感應器框架捕獲時間的6DoF 空間。</span><span class="sxs-lookup"><span data-stu-id="a6d62-167">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="a6d62-168">您可以找到如何存取各種研究模式串流的範例應用程式、如何使用[內建函式和 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)，以及如何在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存放庫存放庫中記錄串流。</span><span class="sxs-lookup"><span data-stu-id="a6d62-168">You can find sample applications on how to access the various Research Mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="a6d62-169">目前，HoloLensForCV 範例不適用於 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="a6d62-169">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="support"></a><span data-ttu-id="a6d62-170">支援</span><span class="sxs-lookup"><span data-stu-id="a6d62-170">Support</span></span>

<span data-ttu-id="a6d62-171">請使用 HoloLensForCV 存放庫中的[問題追蹤](https://github.com/Microsoft/HololensForCV/issues)器來張貼意見反應，並追蹤已知的問題。</span><span class="sxs-lookup"><span data-stu-id="a6d62-171">Please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6d62-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6d62-172">See also</span></span>

* [<span data-ttu-id="a6d62-173">Microsoft 媒體基礎</span><span class="sxs-lookup"><span data-stu-id="a6d62-173">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="a6d62-174">HoloLensForCV GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="a6d62-174">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="a6d62-175">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="a6d62-175">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
