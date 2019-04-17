---
title: HoloLens 參考資料模式
description: HoloLens 上使用參考資料模式，應用程式可以存取重要的裝置感應器資料流 （深度、 追蹤、 環境和 IR 反射率）。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 參考資料模式、 cv、 rs4、 電腦視覺、 參考資料、 HoloLens
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591120"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="9c936-104">HoloLens 參考資料模式</span><span class="sxs-lookup"><span data-stu-id="9c936-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="9c936-105">這項功能已加入的一部分[Windows 10 April 2018 Update](release-notes-april-2018.md)的 HoloLens，並不適用於較早的版本。</span><span class="sxs-lookup"><span data-stu-id="9c936-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="9c936-106">參考資料模式是在裝置提供應用程式存取金鑰的感應器的 HoloLens 的新功能。</span><span class="sxs-lookup"><span data-stu-id="9c936-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="9c936-107">它們包括：</span><span class="sxs-lookup"><span data-stu-id="9c936-107">These include:</span></span>
- <span data-ttu-id="9c936-108">四個追蹤對應建築和前端的追蹤系統使用的數位相機的環境。</span><span class="sxs-lookup"><span data-stu-id="9c936-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="9c936-109">兩個版本的深度相機資料 – 一個用於高頻率 (30 FPS) 深度接近感應，常用的手中追蹤，另一個則用於低頻率 (也就是 1 FPS) 遠深度感應，目前使用空間的對應，</span><span class="sxs-lookup"><span data-stu-id="9c936-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="9c936-110">IR-反射率資料流，用來計算深度，但本身的價值，因為這些映像從 HoloLens 照明標幟及合理受到環境光線 HoloLens 的兩個版本。</span><span class="sxs-lookup"><span data-stu-id="9c936-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="9c936-111">![參考資料模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c936-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="9c936-112">*混合的實境的擷取會顯示在參考資料模式中使用的八個感應器資料流的測試應用程式*</span><span class="sxs-lookup"><span data-stu-id="9c936-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="9c936-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="9c936-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9c936-114">功能</span><span class="sxs-lookup"><span data-stu-id="9c936-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="9c936-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9c936-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9c936-116"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="9c936-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="9c936-117">參考資料模式</span><span class="sxs-lookup"><span data-stu-id="9c936-117">Research mode</span></span></td><td style="text-align: center;"> <span data-ttu-id="9c936-118">✔️</span><span class="sxs-lookup"><span data-stu-id="9c936-118">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="9c936-119">之前使用參考資料模式</span><span class="sxs-lookup"><span data-stu-id="9c936-119">Before using Research mode</span></span>

<span data-ttu-id="9c936-120">參考資料模式也稱為： 適合學術和產業研究人員嘗試在電腦視景和機器人的欄位中的新概念。</span><span class="sxs-lookup"><span data-stu-id="9c936-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="9c936-121">參考資料模式並不適用於將整個企業中部署或可在 Microsoft Store 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c936-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="9c936-122">參考資料模式可降低您的裝置的安全性，而消耗更多的電池電力，比正常作業的原因。</span><span class="sxs-lookup"><span data-stu-id="9c936-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="9c936-123">Microsoft 不認可任何未來的裝置上支援此模式中。</span><span class="sxs-lookup"><span data-stu-id="9c936-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="9c936-124">因此，我們建議您用它來開發及測試新的想法;不過，您將無法廣泛部署的應用程式，使用參考資料模式，或有任何的保證，讓它將繼續在未來的硬體上運作。</span><span class="sxs-lookup"><span data-stu-id="9c936-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="9c936-125">啟用參考資料模式</span><span class="sxs-lookup"><span data-stu-id="9c936-125">Enabling Research mode</span></span>

<span data-ttu-id="9c936-126">參考資料模式是開發人員模式下的子模式。</span><span class="sxs-lookup"><span data-stu-id="9c936-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="9c936-127">您必須先啟用開發人員模式中設定應用程式 (**設定 > 更新與安全性 > 適用於開發人員**):</span><span class="sxs-lookup"><span data-stu-id="9c936-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="9c936-128">將 「 使用開發人員功能 」 設定為**上**</span><span class="sxs-lookup"><span data-stu-id="9c936-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="9c936-129">將 [啟用裝置入口網站] 設定為**上**</span><span class="sxs-lookup"><span data-stu-id="9c936-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="9c936-130">然後使用 連線到您的 HoloLens，相同的 Wi-fi 網路的網頁瀏覽器瀏覽至您 HoloLens 的 IP 位址 (一貫**設定 > 網路和網際網路 > Wi-fi > 硬體屬性**)。</span><span class="sxs-lookup"><span data-stu-id="9c936-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="9c936-131">這是[裝置入口網站](using-the-windows-device-portal.md)，，您會看到入口網站的 「 系統 」 一節中的 「 參考資料模式 」 的頁面：</span><span class="sxs-lookup"><span data-stu-id="9c936-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="9c936-132">![研究 HoloLens 裝置入口網站的 [模式] 索引的標籤](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="9c936-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="9c936-133">*HoloLens 裝置入口網站中的參考資料模式*</span><span class="sxs-lookup"><span data-stu-id="9c936-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="9c936-134">選取之後**允許感應器資料流存取**，您需要重新啟動 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="9c936-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="9c936-135">從裝置入口網站中，在 "Power"功能表項目在頁面頂端，您可以執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="9c936-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="9c936-136">一旦重新啟動您的裝置之後，已透過裝置入口網站中載入的應用程式應該能夠存取參考資料模式資料流。</span><span class="sxs-lookup"><span data-stu-id="9c936-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="9c936-137">在您的應用程式中使用感應器資料</span><span class="sxs-lookup"><span data-stu-id="9c936-137">Using sensor data in your apps</span></span>

<span data-ttu-id="9c936-138">應用程式可以存取所開啟的感應器資料流資料[媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)完全相同的方式存取相片及視訊攝影機資料流中的資料流。</span><span class="sxs-lookup"><span data-stu-id="9c936-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="9c936-139">HoloLens 的開發工作的所有 Api 也都可在 參考資料模式。</span><span class="sxs-lookup"><span data-stu-id="9c936-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="9c936-140">特別是，應用程式可以知道精確 HoloLens 所在 6DoF 空間中每個感應器畫面格擷取時間點。</span><span class="sxs-lookup"><span data-stu-id="9c936-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="9c936-141">顯示存取各種參考資料模式資料流的方式、 如何使用內建函式和 extrinsics，以及如何將記錄資料流的範例應用程式可用於[HoloLensForCV GitHub 存放庫](https://github.com/Microsoft/HoloLensForCV)。</span><span class="sxs-lookup"><span data-stu-id="9c936-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="9c936-142">已知問題</span><span class="sxs-lookup"><span data-stu-id="9c936-142">Known issues</span></span>

<span data-ttu-id="9c936-143">請參閱[問題追蹤程式](https://github.com/Microsoft/HololensForCV/issues)HoloLensForCV 存放庫中。</span><span class="sxs-lookup"><span data-stu-id="9c936-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c936-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c936-144">See also</span></span>

* [<span data-ttu-id="9c936-145">Microsoft 媒體基礎</span><span class="sxs-lookup"><span data-stu-id="9c936-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="9c936-146">HoloLensForCV GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="9c936-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="9c936-147">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="9c936-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
