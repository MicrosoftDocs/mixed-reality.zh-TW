---
title: 連線至 Wi-fi HoloLens 上
description: 如何使用 HoloLens 無線網際網路連線以及如何找出裝置的 IP 位址的指示。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens、 wifi、 無線網路、 網際網路、 ip、 ip 位址
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670120"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="85ad4-104">連線至 Wi-fi HoloLens 上</span><span class="sxs-lookup"><span data-stu-id="85ad4-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="85ad4-105">HoloLens 包含 802.11ac-2 的 Wi-fi 電台的能力，2x。</span><span class="sxs-lookup"><span data-stu-id="85ad4-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="85ad4-106">連線到 Wi-fi 網路的 HoloLens 是類似於 Windows 10 Desktop 或行動裝置版裝置連接到 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="85ad4-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![HoloLens Wi-fi 設定](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="85ad4-108">連線到 Wi-fi 網路上 HoloLens</span><span class="sxs-lookup"><span data-stu-id="85ad4-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="85ad4-109">[Bloom](gestures.md#bloom)要**啟動**功能表。</span><span class="sxs-lookup"><span data-stu-id="85ad4-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="85ad4-110">選取 **設定**應用程式從開始，或從**所有應用程式**右邊的 開始 功能表上的清單。</span><span class="sxs-lookup"><span data-stu-id="85ad4-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="85ad4-111">**設定**應用程式將會自動放置您面前。</span><span class="sxs-lookup"><span data-stu-id="85ad4-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="85ad4-112">選取 **網路和網際網路**。</span><span class="sxs-lookup"><span data-stu-id="85ad4-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="85ad4-113">確定已開啟 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="85ad4-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="85ad4-114">從清單中選取 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="85ad4-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="85ad4-115">（如有需要），請輸入中的 Wi-fi 網路密碼。</span><span class="sxs-lookup"><span data-stu-id="85ad4-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="85ad4-116">停用 HoloLens 上的 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="85ad4-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="85ad4-117">使用 HoloLens 上的 設定 應用程式</span><span class="sxs-lookup"><span data-stu-id="85ad4-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="85ad4-118">[Bloom](gestures.md#bloom)要**啟動**功能表。</span><span class="sxs-lookup"><span data-stu-id="85ad4-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="85ad4-119">選取 **設定**應用程式從開始，或從**所有應用程式**右邊的 開始 功能表上的清單。</span><span class="sxs-lookup"><span data-stu-id="85ad4-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="85ad4-120">**設定**應用程式將會自動放置您面前。</span><span class="sxs-lookup"><span data-stu-id="85ad4-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="85ad4-121">選取 **網路和網際網路**。</span><span class="sxs-lookup"><span data-stu-id="85ad4-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="85ad4-122">選取 [Wi-fi] 滑桿切換，將它移到 「 關閉 」 位置。</span><span class="sxs-lookup"><span data-stu-id="85ad4-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="85ad4-123">這會關閉 Wi-fi 無線通訊的 RF 元件，並停用 HoloLens 上的所有 Wi-fi 功能。</span><span class="sxs-lookup"><span data-stu-id="85ad4-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="85ad4-124">HoloLens 將無法自動載入您[空格](environment-considerations-for-hololens.md#WiFi fingerprint considerations)Wi-fi 選項已停用。</span><span class="sxs-lookup"><span data-stu-id="85ad4-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="85ad4-125">移動滑桿切換到開啟的 Wi-fi 選項和還原 Microsoft HoloLens 上的 Wi-fi 功能的 「 開啟 」 位置。</span><span class="sxs-lookup"><span data-stu-id="85ad4-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="85ad4-126">選取的 Wi-fi 選項狀態 (「 On 」 的 「 關閉 」) 會在重新啟動期間保存。</span><span class="sxs-lookup"><span data-stu-id="85ad4-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="85ad4-127">如何確認您連接到 Wi-fi 網路</span><span class="sxs-lookup"><span data-stu-id="85ad4-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="85ad4-128">[Bloom](gestures.md#bloom)即可啟動**啟動**功能表。</span><span class="sxs-lookup"><span data-stu-id="85ad4-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="85ad4-129">看看右上方的 Wi-fi 狀態的 開始 功能表。</span><span class="sxs-lookup"><span data-stu-id="85ad4-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="85ad4-130">會顯示狀態的 Wi-fi 和連線的網路 SSID。</span><span class="sxs-lookup"><span data-stu-id="85ad4-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="85ad4-131">識別您 HoloLens Wi-fi 網路上 IP 位址</span><span class="sxs-lookup"><span data-stu-id="85ad4-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="85ad4-132">使用 [設定] 應用程式</span><span class="sxs-lookup"><span data-stu-id="85ad4-132">Using the Settings app</span></span>

1. <span data-ttu-id="85ad4-133">[Bloom](gestures.md#bloom)要**啟動**功能表。</span><span class="sxs-lookup"><span data-stu-id="85ad4-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="85ad4-134">選取 **設定**應用程式從開始，或從**所有應用程式**右邊的 開始 功能表上的清單。</span><span class="sxs-lookup"><span data-stu-id="85ad4-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="85ad4-135">**設定**應用程式將會自動放置您面前。</span><span class="sxs-lookup"><span data-stu-id="85ad4-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="85ad4-136">選取 **網路和網際網路**。</span><span class="sxs-lookup"><span data-stu-id="85ad4-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="85ad4-137">向下捲動至下方清單中可用的 Wi-fi 網路，然後選取**硬體屬性**。</span><span class="sxs-lookup"><span data-stu-id="85ad4-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![在 Wi-fi 設定的硬體屬性](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="85ad4-139">將旁邊顯示的 IP 位址**IPv4 位址**。</span><span class="sxs-lookup"><span data-stu-id="85ad4-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="85ad4-140">使用 Cortana</span><span class="sxs-lookup"><span data-stu-id="85ad4-140">Using Cortana</span></span>

<span data-ttu-id="85ad4-141">說出 「*嘿 Cortana，我的 IP 位址是什麼？*"</span><span class="sxs-lookup"><span data-stu-id="85ad4-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="85ad4-142">和 Cortana 將會顯示和讀取您的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="85ad4-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="85ad4-143">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="85ad4-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="85ad4-144">開啟[裝置入口網站](using-the-windows-device-portal.md#networking)網頁瀏覽器，在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="85ad4-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="85ad4-145">瀏覽至**網路**一節。</span><span class="sxs-lookup"><span data-stu-id="85ad4-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="85ad4-146">您的 IP 位址和其他網路資訊會在該處顯示。</span><span class="sxs-lookup"><span data-stu-id="85ad4-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="85ad4-147">這個方法允許為簡單的複製和貼上的開發電腦上的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="85ad4-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
