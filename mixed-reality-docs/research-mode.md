---
title: HoloLens 研究模式
description: 使用 HoloLens 的 Research 模式, 應用程式可以存取金鑰裝置感應器串流 (深度、環境追蹤和 IR-反射率)。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 研究模式, cv, rs4, 電腦視覺, research, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829927"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="cfa8b-104">HoloLens 研究模式</span><span class="sxs-lookup"><span data-stu-id="cfa8b-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="cfa8b-105">這項功能已新增為 HoloLens 的[Windows 10 2018 年4月更新](release-notes-april-2018.md)的一部分, 且在舊版中無法使用。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="cfa8b-106">Research 模式是 HoloLens 的新功能, 可讓應用程式存取裝置上的重要感應器。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="cfa8b-107">它們包括：</span><span class="sxs-lookup"><span data-stu-id="cfa8b-107">These include:</span></span>
- <span data-ttu-id="cfa8b-108">系統使用的四個環境追蹤攝影機, 用於地圖建立和標題追蹤。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="cfa8b-109">兩個版本的深度相機資料–一個用於高頻率 (30 FPS) 近深度檢測, 通常用於手動追蹤, 另一個用於較低頻率 (1 FPS) 的深度感應, 目前用於空間對應,</span><span class="sxs-lookup"><span data-stu-id="cfa8b-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="cfa8b-110">有兩個版本的 IR 反射率串流, 由 HoloLens 用來計算深度, 但有價值, 因為這些影像會從 HoloLens 照亮, 而且會受到環境光線的適當影響。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="cfa8b-111">![研究模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="cfa8b-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="cfa8b-112">*測試應用程式的混合現實捕捉, 會顯示 Research 模式中提供的八個感應器串流*</span><span class="sxs-lookup"><span data-stu-id="cfa8b-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="cfa8b-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="cfa8b-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="cfa8b-114"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="cfa8b-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="cfa8b-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="cfa8b-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="cfa8b-116"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="cfa8b-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="cfa8b-117">研究模式</span><span class="sxs-lookup"><span data-stu-id="cfa8b-117">Research mode</span></span></td>
        <td><span data-ttu-id="cfa8b-118">✔️</span><span class="sxs-lookup"><span data-stu-id="cfa8b-118">✔️</span></span></td>
        <td><span data-ttu-id="cfa8b-119">❌</span><span class="sxs-lookup"><span data-stu-id="cfa8b-119">❌</span></span></td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="cfa8b-120">使用研究模式之前</span><span class="sxs-lookup"><span data-stu-id="cfa8b-120">Before using Research mode</span></span>

<span data-ttu-id="cfa8b-121">研究模式的命名良好: 它適用于學術和產業研究人員在電腦視覺和機器人領域中嘗試新構想。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-121">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="cfa8b-122">研究模式不適用於將在企業中部署或可在 Microsoft Store 中使用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-122">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="cfa8b-123">這是因為研究模式會降低裝置的安全性, 而且耗用的電池電力遠高於正常作業。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-123">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="cfa8b-124">Microsoft 不會承諾在任何未來的裝置上支援此模式。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-124">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="cfa8b-125">因此, 我們建議您使用它來開發和測試新的想法;不過, 您將無法廣泛部署使用研究模式的應用程式, 也無法保證它會繼續在未來的硬體上工作。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-125">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="cfa8b-126">啟用研究模式</span><span class="sxs-lookup"><span data-stu-id="cfa8b-126">Enabling Research mode</span></span>

<span data-ttu-id="cfa8b-127">Research 模式是開發人員模式的子模式。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-127">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="cfa8b-128">您必須先在 設定 應用程式中啟用開發人員模式 (**設定 > 適用于開發人員的 更新 & 安全性 >** ):</span><span class="sxs-lookup"><span data-stu-id="cfa8b-128">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="cfa8b-129">將 [使用開發人員功能] 設定為 [**開啟**]</span><span class="sxs-lookup"><span data-stu-id="cfa8b-129">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="cfa8b-130">將 [啟用裝置入口網站] 設定為 [**開啟**]</span><span class="sxs-lookup"><span data-stu-id="cfa8b-130">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="cfa8b-131">然後使用連線到與 HoloLens 相同之 Wi-fi 網路的網頁瀏覽器, 流覽至 HoloLens 的 IP 位址 (透過 [**設定] > [網路 &] [網際網路] > [wi-fi > 硬體**內容]) 來取得。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-131">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="cfa8b-132">這是[裝置入口網站](using-the-windows-device-portal.md), 您會在入口網站的 [系統] 區段中找到 [研究模式] 頁面:</span><span class="sxs-lookup"><span data-stu-id="cfa8b-132">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="cfa8b-133">![HoloLens 裝置入口網站的 [研究模式] 索引標籤](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="cfa8b-133">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="cfa8b-134">*HoloLens 裝置入口網站中的研究模式*</span><span class="sxs-lookup"><span data-stu-id="cfa8b-134">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="cfa8b-135">選取 [**允許存取感應器串流**] 之後, 您將需要重新開機 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-135">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="cfa8b-136">您可以從裝置入口網站, 在頁面頂端的 [電源] 功能表項目底下執行此動作。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-136">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="cfa8b-137">一旦您的裝置重新開機, 透過裝置入口網站載入的應用程式應該能夠存取研究模式串流。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-137">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="cfa8b-138">在您的應用程式中使用感應器資料</span><span class="sxs-lookup"><span data-stu-id="cfa8b-138">Using sensor data in your apps</span></span>

<span data-ttu-id="cfa8b-139">應用程式可以藉由以存取相片/視頻相機串流的相同方式, 開啟[媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)串流來存取感應器串流資料。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-139">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="cfa8b-140">在研究模式下也可以使用適用于 HoloLens 開發的所有 Api。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-140">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="cfa8b-141">特別是, 應用程式可以確切知道 HoloLens 在每個感應器框架捕獲時間的6DoF 空間。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-141">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="cfa8b-142">範例應用程式會顯示如何存取各種研究模式串流、如何使用內建函式和 extrinsics, 以及如何記錄串流, 可在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存放庫中取得。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-142">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="cfa8b-143">已知問題</span><span class="sxs-lookup"><span data-stu-id="cfa8b-143">Known issues</span></span>

<span data-ttu-id="cfa8b-144">請參閱 HoloLensForCV 存放庫中的[問題追蹤](https://github.com/Microsoft/HololensForCV/issues)器。</span><span class="sxs-lookup"><span data-stu-id="cfa8b-144">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfa8b-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfa8b-145">See also</span></span>

* [<span data-ttu-id="cfa8b-146">Microsoft 媒體基礎</span><span class="sxs-lookup"><span data-stu-id="cfa8b-146">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="cfa8b-147">HoloLensForCV GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="cfa8b-147">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="cfa8b-148">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="cfa8b-148">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
