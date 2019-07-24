---
title: 連接到 HoloLens 上的 Wi-fi
description: 如何使用 HoloLens 連線至無線網際網路的指示, 以及如何識別裝置的 IP 位址。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, 無線, 網際網路, ip, ip 位址
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670120"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="aaffb-104">連接到 HoloLens 上的 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="aaffb-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="aaffb-105">HoloLens 包含具備802.11 電源功能、2x2 的 Wi-fi 無線電。</span><span class="sxs-lookup"><span data-stu-id="aaffb-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="aaffb-106">將 HoloLens 連接到 Wi-fi 網路, 類似于將 Windows 10 桌上型電腦或行動裝置連線到 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="aaffb-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![HoloLens Wi-fi 設定](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="aaffb-108">在 HoloLens 上連接到 Wi-fi 網路</span><span class="sxs-lookup"><span data-stu-id="aaffb-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="aaffb-109">[Bloom](gestures.md#bloom)至 [**開始**] 功能表。</span><span class="sxs-lookup"><span data-stu-id="aaffb-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="aaffb-110">從 [開始] 功能表右邊的 [**所有應用程式**] 清單中, 選取 [**設定**] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="aaffb-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="aaffb-111">[**設定**] 應用程式會自動放在您的前方。</span><span class="sxs-lookup"><span data-stu-id="aaffb-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="aaffb-112">選取 [**網路 & 網際網路**]。</span><span class="sxs-lookup"><span data-stu-id="aaffb-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="aaffb-113">確定已開啟 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="aaffb-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="aaffb-114">從清單中選取 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="aaffb-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="aaffb-115">輸入 Wi-fi 網路密碼 (如有需要)。</span><span class="sxs-lookup"><span data-stu-id="aaffb-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="aaffb-116">停用 HoloLens 上的 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="aaffb-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="aaffb-117">在 HoloLens 上使用設定應用程式</span><span class="sxs-lookup"><span data-stu-id="aaffb-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="aaffb-118">[Bloom](gestures.md#bloom)至 [**開始**] 功能表。</span><span class="sxs-lookup"><span data-stu-id="aaffb-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="aaffb-119">從 [開始] 功能表右邊的 [**所有應用程式**] 清單中, 選取 [**設定**] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="aaffb-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="aaffb-120">[**設定**] 應用程式會自動放在您的前方。</span><span class="sxs-lookup"><span data-stu-id="aaffb-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="aaffb-121">選取 [**網路 & 網際網路**]。</span><span class="sxs-lookup"><span data-stu-id="aaffb-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="aaffb-122">選取 [Wi-fi 滑杆] 開關, 將其移至 [關閉] 位置。</span><span class="sxs-lookup"><span data-stu-id="aaffb-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="aaffb-123">這會關閉 Wi-fi 無線電的 RF 元件, 並停用 HoloLens 上的所有 Wi-fi 功能。</span><span class="sxs-lookup"><span data-stu-id="aaffb-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="aaffb-124">當停用 Wi-fi 無線電時, HoloLens 將無法自動載入您的[空間](environment-considerations-for-hololens.md#WiFi fingerprint considerations)。</span><span class="sxs-lookup"><span data-stu-id="aaffb-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="aaffb-125">將滑杆切換至 [開啟] 位置, 以開啟 Wi-fi 無線電並在 Microsoft HoloLens 上還原 Wi-fi 功能。</span><span class="sxs-lookup"><span data-stu-id="aaffb-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="aaffb-126">選取的 Wi-fi 無線電狀態 (「開啟」) 將會在重新開機時保存。</span><span class="sxs-lookup"><span data-stu-id="aaffb-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="aaffb-127">如何確認您已連線到 Wi-fi 網路</span><span class="sxs-lookup"><span data-stu-id="aaffb-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="aaffb-128">[Bloom](gestures.md#bloom)以顯示 [**開始**] 功能表。</span><span class="sxs-lookup"><span data-stu-id="aaffb-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="aaffb-129">查看 [開始] 功能表左上方的 [Wi-fi 狀態]。</span><span class="sxs-lookup"><span data-stu-id="aaffb-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="aaffb-130">隨即會顯示 Wi-fi 的狀態和連線網路的 SSID。</span><span class="sxs-lookup"><span data-stu-id="aaffb-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="aaffb-131">識別您的 HoloLens 在 Wi-fi 網路上的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="aaffb-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="aaffb-132">使用設定應用程式</span><span class="sxs-lookup"><span data-stu-id="aaffb-132">Using the Settings app</span></span>

1. <span data-ttu-id="aaffb-133">[Bloom](gestures.md#bloom)至 [**開始**] 功能表。</span><span class="sxs-lookup"><span data-stu-id="aaffb-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="aaffb-134">從 [開始] 功能表右邊的 [**所有應用程式**] 清單中, 選取 [**設定**] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="aaffb-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="aaffb-135">[**設定**] 應用程式會自動放在您的前方。</span><span class="sxs-lookup"><span data-stu-id="aaffb-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="aaffb-136">選取 [**網路 & 網際網路**]。</span><span class="sxs-lookup"><span data-stu-id="aaffb-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="aaffb-137">在 [可用的 Wi-fi 網路] 清單下方向下流覽, 然後選取 [**硬體**內容]。</span><span class="sxs-lookup"><span data-stu-id="aaffb-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Wi-fi 設定中的硬體屬性](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="aaffb-139">IP 位址會顯示在 [ **IPv4 位址**] 旁。</span><span class="sxs-lookup"><span data-stu-id="aaffb-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="aaffb-140">使用 Cortana</span><span class="sxs-lookup"><span data-stu-id="aaffb-140">Using Cortana</span></span>

<span data-ttu-id="aaffb-141">說「*嗨, Cortana, 我的 IP 位址是什麼？* 」</span><span class="sxs-lookup"><span data-stu-id="aaffb-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="aaffb-142">而 Cortana 會顯示並讀取您的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="aaffb-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="aaffb-143">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="aaffb-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="aaffb-144">在您電腦上的網頁瀏覽器中開啟[裝置入口網站](using-the-windows-device-portal.md#networking)。</span><span class="sxs-lookup"><span data-stu-id="aaffb-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="aaffb-145">流覽至 [**網路**] 區段。</span><span class="sxs-lookup"><span data-stu-id="aaffb-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="aaffb-146">您的 IP 位址和其他網路資訊將會顯示在該處。</span><span class="sxs-lookup"><span data-stu-id="aaffb-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="aaffb-147">這個方法可讓您輕鬆地在開發電腦上複製和貼上 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="aaffb-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
