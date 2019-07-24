---
title: 全像攝影遠端播放
description: 全像攝影遠端播放程式是一種隨附的應用程式, 可連接到支援全像攝影遠端的電腦應用程式和遊戲。 全像攝影遠端處理會使用 Wi-fi 連線, 即時將全像個人電腦的內容串流至您的 Microsoft HoloLens。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813716"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="c796a-105">全像攝影遠端播放</span><span class="sxs-lookup"><span data-stu-id="c796a-105">Holographic Remoting Player</span></span>

<span data-ttu-id="c796a-106">全像攝影遠端播放程式是一種隨附的應用程式, 可連接到支援全像攝影遠端的電腦應用程式和遊戲。</span><span class="sxs-lookup"><span data-stu-id="c796a-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="c796a-107">全像攝影遠端處理會使用 Wi-fi 連線, 即時將全像個人電腦的內容串流至您的 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c796a-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="c796a-108">全像攝影遠端播放程式只能用於專為支援全像攝影遠端功能而設計的電腦應用程式。</span><span class="sxs-lookup"><span data-stu-id="c796a-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

<span data-ttu-id="c796a-109">全像是 HoloLens 和 HoloLens 2 都提供全像攝影遠端播放程式。</span><span class="sxs-lookup"><span data-stu-id="c796a-109">The Holographic Remoting Player is available for both HoloLens and HoloLens 2.</span></span>  <span data-ttu-id="c796a-110">使用 HoloLens 支援全像攝影遠端功能的電腦應用程式必須更新, 以支援使用 HoloLens 2 的全像 Remtoing。</span><span class="sxs-lookup"><span data-stu-id="c796a-110">PC apps that supported Holographic Remoting with HoloLens need to be updated to support Holographic Remtoing with HoloLens 2.</span></span>  <span data-ttu-id="c796a-111">如果您對支援的版本有任何疑問, 請洽詢您的應用程式提供者。</span><span class="sxs-lookup"><span data-stu-id="c796a-111">Please contact your app provider if you have questions about which versions are supported.</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="c796a-112">連接到全像攝影遠端播放播放機</span><span class="sxs-lookup"><span data-stu-id="c796a-112">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="c796a-113">遵循您應用程式的指示, 連接到全像攝影的遠端播放播放機。</span><span class="sxs-lookup"><span data-stu-id="c796a-113">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="c796a-114">您將需要輸入 HoloLens 裝置的 IP 位址, 您可以在遠端播放程式的主畫面上看到它, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="c796a-114">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![全像攝影遠端播放](images/holographicremotingplayer.png)

<span data-ttu-id="c796a-116">當您看到主畫面時, 您會知道您沒有連線的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c796a-116">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="c796a-117">請注意, 全像攝影遠端連線**不會加密**。</span><span class="sxs-lookup"><span data-stu-id="c796a-117">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="c796a-118">您應該一律在您信任的安全 Wi-fi 連線上使用全像攝影遠端。</span><span class="sxs-lookup"><span data-stu-id="c796a-118">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="c796a-119">品質和效能</span><span class="sxs-lookup"><span data-stu-id="c796a-119">Quality and Performance</span></span>

<span data-ttu-id="c796a-120">您的體驗品質和效能會因三個因素而有所不同:</span><span class="sxs-lookup"><span data-stu-id="c796a-120">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="c796a-121">**您**正在執行的全像攝影體驗-呈現高解析度或高度詳細內容的應用程式, 可能需要更快速的電腦或更快的無線連線。</span><span class="sxs-lookup"><span data-stu-id="c796a-121">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="c796a-122">**您**的電腦硬體-您的電腦必須能夠在每秒60畫面上執行及編碼您的全像體驗。</span><span class="sxs-lookup"><span data-stu-id="c796a-122">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="c796a-123">針對圖形配接器, 我們通常建議使用 GeForce GTX 970 或 AMD Radeon R9 290 或更高的品質。</span><span class="sxs-lookup"><span data-stu-id="c796a-123">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="c796a-124">同樣地, 您的特定體驗可能需要較高或較低的卡片。</span><span class="sxs-lookup"><span data-stu-id="c796a-124">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="c796a-125">**您的 wi-fi**連線-您的全像攝影體驗會透過 wi-fi 進行串流處理。</span><span class="sxs-lookup"><span data-stu-id="c796a-125">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="c796a-126">使用具有低擁塞的快速網路, 將品質最大化。</span><span class="sxs-lookup"><span data-stu-id="c796a-126">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="c796a-127">使用透過 Ethernet 纜線 (而非 Wi-fi) 連線的電腦, 也可以改善品質。</span><span class="sxs-lookup"><span data-stu-id="c796a-127">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="c796a-128">診斷</span><span class="sxs-lookup"><span data-stu-id="c796a-128">Diagnostics</span></span>

<span data-ttu-id="c796a-129">若要測量連線的品質, 請在全像攝影遠端播放程式的主畫面上說「**啟用診斷**」。</span><span class="sxs-lookup"><span data-stu-id="c796a-129">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="c796a-130">啟用診斷時, 應用程式會顯示:</span><span class="sxs-lookup"><span data-stu-id="c796a-130">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="c796a-131">**FPS** -遠端播放者每秒接收和轉譯的轉譯框架平均數目。</span><span class="sxs-lookup"><span data-stu-id="c796a-131">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="c796a-132">理想的情況是 60 FPS。</span><span class="sxs-lookup"><span data-stu-id="c796a-132">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="c796a-133">**延遲**-框架從您的電腦移至 HoloLens 所需的平均時間量。</span><span class="sxs-lookup"><span data-stu-id="c796a-133">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="c796a-134">越低越好。</span><span class="sxs-lookup"><span data-stu-id="c796a-134">The lower the better.</span></span> <span data-ttu-id="c796a-135">這主要取決於您的 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="c796a-135">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="c796a-136">在主畫面上, 您可以說「**停用診斷**」來關閉診斷。</span><span class="sxs-lookup"><span data-stu-id="c796a-136">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="c796a-137">電腦系統需求</span><span class="sxs-lookup"><span data-stu-id="c796a-137">PC System Requirements</span></span>
* <span data-ttu-id="c796a-138">您的電腦**必須**執行 Windows 10 年度更新版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c796a-138">Your PC **must** be running the Windows 10 Anniversary Update or newer.</span></span>
* <span data-ttu-id="c796a-139">我們建議使用 GeForce GTX 970 或 AMD Radeon R9 290 或更好的圖形配接器。</span><span class="sxs-lookup"><span data-stu-id="c796a-139">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="c796a-140">我們建議您透過 ethernet 將電腦連線到您的網路, 以減少無線躍點的數目。</span><span class="sxs-lookup"><span data-stu-id="c796a-140">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="c796a-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c796a-141">See Also</span></span>
* [<span data-ttu-id="c796a-142">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="c796a-142">Holographic remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="c796a-143">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="c796a-143">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
