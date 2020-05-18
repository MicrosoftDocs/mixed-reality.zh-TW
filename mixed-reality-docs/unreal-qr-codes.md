---
title: Unreal 中的 QR 代碼
description: 在 Unreal 中使用 QR 代碼的指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, qr 代碼
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342656"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="6b004-104">Unreal 中的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="6b004-104">QR codes in Unreal</span></span>

<span data-ttu-id="6b004-105">HoloLens 可以在世界空間中找到 QR 代碼，以在真實世界中的已知位置轉譯全像投影。</span><span class="sxs-lookup"><span data-stu-id="6b004-105">HoloLens can locate QR codes in world space to render holograms at known positions in the real world.</span></span>  <span data-ttu-id="6b004-106">這也可以用來在相同位置中的多個裝置上轉譯全像投影，以建立共用體驗。</span><span class="sxs-lookup"><span data-stu-id="6b004-106">This can also be used to render holograms on multiple devices in the same location to create a shared experience.</span></span> 

<span data-ttu-id="6b004-107">若要在 HoloLens 上啟用 QR 偵測，請確定已在 [專案設定] > [平台] > [HoloLens] > [功能] 下的 Unreal 編輯器中勾選「網路攝影機」功能。</span><span class="sxs-lookup"><span data-stu-id="6b004-107">To enable QR detection on HoloLens, ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="6b004-108">藉由使用 StartARSession 函式來啟動 ARSession，以選擇在 Unreal 中使用 QR 代碼追蹤。</span><span class="sxs-lookup"><span data-stu-id="6b004-108">Opt into using QR code tracking in Unreal by starting an ARSession with the StartARSession function.</span></span> 

<span data-ttu-id="6b004-109">QR 代碼會透過 Unreal 的 AR 追蹤幾何系統呈現為追蹤的影像。</span><span class="sxs-lookup"><span data-stu-id="6b004-109">QR Codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span>  <span data-ttu-id="6b004-110">若要使用這個功能，請將 AR 可追蹤通知元件新增至藍圖	動作項目：</span><span class="sxs-lookup"><span data-stu-id="6b004-110">To use this, add an AR Trackable Notify component to a Blueprint actor:</span></span> 

![QR AR 可追蹤通知](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="6b004-112">然後移至元件的詳細資料，並且按一下要監視事件的綠色 "+" 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6b004-112">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span>  

![QR 事件](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="6b004-114">在這裡，我們訂閱了 OnUpdateTrackedImage，以在 QR 代碼的中央呈現點，並列印 QR 代碼的編碼資料。</span><span class="sxs-lookup"><span data-stu-id="6b004-114">Here, we have subscribed to OnUpdateTrackedImage to render a point in the center of a QR Code and print the QR code’s encoded data.</span></span> 

![QR 轉譯範例](images/unreal-qr-render.PNG)

<span data-ttu-id="6b004-116">首先將追蹤的影像轉型為 ARTrackedQRCode，以確認目前更新的影像是 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="6b004-116">First cast the tracked image to an ARTrackedQRCode to verify that the current updated image is a QR code.</span></span>  <span data-ttu-id="6b004-117">然後，您可以使用 QRCode 變數來擷取編碼的資料。</span><span class="sxs-lookup"><span data-stu-id="6b004-117">Then the encoded data can be retrieved with the QRCode variable.</span></span>  <span data-ttu-id="6b004-118">您可以從 GetLocalToWorldTransform 的位置擷取 QR 代碼的左上角。</span><span class="sxs-lookup"><span data-stu-id="6b004-118">The top-left of the QR code can be retrieved from the location of GetLocalToWorldTransform.</span></span>  <span data-ttu-id="6b004-119">您可以使用 GetEstimateSize 來擷取維度。</span><span class="sxs-lookup"><span data-stu-id="6b004-119">The dimensions can be retrieved with GetEstimateSize.</span></span> 

<span data-ttu-id="6b004-120">每個 QR 代碼也有唯一的 GUID 識別碼：</span><span class="sxs-lookup"><span data-stu-id="6b004-120">Every QR code also has a unique guid ID:</span></span> 

![QR GUID](images/unreal-qr-guid.PNG)

## <a name="see-also"></a><span data-ttu-id="6b004-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b004-122">See also</span></span>
* [<span data-ttu-id="6b004-123">QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="6b004-123">QR code tracking</span></span>](qr-code-tracking.md)
