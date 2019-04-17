---
title: 全像攝影版的遠端播放程式
description: 全像攝影版的遠端播放程式是小幫手應用程式連接到電腦的應用程式和支援全像攝影版的遠端執行功能的遊戲。 全像攝影版的遠端資料流全像攝影版內容從 PC 到您的 Microsoft HoloLens 中即時使用 Wi-fi 連線。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 遠端處理，全像攝影版的遠端處理
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597086"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="d2f14-105">全像攝影版的遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="d2f14-105">Holographic Remoting Player</span></span>

<span data-ttu-id="d2f14-106">全像攝影版的遠端播放程式是小幫手應用程式連接到電腦的應用程式和支援全像攝影版的遠端執行功能的遊戲。</span><span class="sxs-lookup"><span data-stu-id="d2f14-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="d2f14-107">全像攝影版的遠端資料流全像攝影版內容從 PC 到您的 Microsoft HoloLens 中即時使用 Wi-fi 連線。</span><span class="sxs-lookup"><span data-stu-id="d2f14-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="d2f14-108">全像攝影版的遠端播放程式只能搭配專為支援全像攝影版的遠端執行功能的 PC 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2f14-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="d2f14-109">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="d2f14-109">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="d2f14-110">連接到全像攝影版的遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="d2f14-110">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="d2f14-111">依照您的應用程式連接到全像攝影版的遠端播放程式的指示。</span><span class="sxs-lookup"><span data-stu-id="d2f14-111">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="d2f14-112">您必須輸入您可以在遠端處理播放程式的主畫面看到，如下所示的 HoloLens 裝置的 IP 位址：</span><span class="sxs-lookup"><span data-stu-id="d2f14-112">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![全像攝影版的遠端播放程式](images/holographicremotingplayer.png)

<span data-ttu-id="d2f14-114">每當您看到主畫面中，您會知道您沒有連接的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2f14-114">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="d2f14-115">請注意，全像攝影版的遠端連線**不會加密**。</span><span class="sxs-lookup"><span data-stu-id="d2f14-115">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="d2f14-116">您應該一律使用全像攝影版的遠端處理，透過您信任的安全之 Wi-fi 連線。</span><span class="sxs-lookup"><span data-stu-id="d2f14-116">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="d2f14-117">品質和效能</span><span class="sxs-lookup"><span data-stu-id="d2f14-117">Quality and Performance</span></span>

<span data-ttu-id="d2f14-118">品質和效能的經驗會有所不同三個因素：</span><span class="sxs-lookup"><span data-stu-id="d2f14-118">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="d2f14-119">**您執行全像攝影版體驗**-轉譯高解析度或高詳細內容的應用程式可能需要更快的電腦或更快的無線連線。</span><span class="sxs-lookup"><span data-stu-id="d2f14-119">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="d2f14-120">**您的電腦硬體**-您的個人電腦必須能夠執行，並編碼您全像攝影版的體驗，在每秒 60 畫面格數。</span><span class="sxs-lookup"><span data-stu-id="d2f14-120">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="d2f14-121">如圖形卡，我們通常建議 GeForce GTX 970 或 AMD Radeon R9 290 或高愈好。</span><span class="sxs-lookup"><span data-stu-id="d2f14-121">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="d2f14-122">同樣地，您的特定體驗可能需要較高或較低的卡片。</span><span class="sxs-lookup"><span data-stu-id="d2f14-122">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="d2f14-123">**您的 Wi-fi 連線**-透過 Wi-fi 串流處理您全像攝影版的體驗。</span><span class="sxs-lookup"><span data-stu-id="d2f14-123">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="d2f14-124">使用低壅塞的高速網路可提高品質。</span><span class="sxs-lookup"><span data-stu-id="d2f14-124">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="d2f14-125">使用透過乙太網路纜線連接的電腦，而不是 Wi-fi，可能也提升品質。</span><span class="sxs-lookup"><span data-stu-id="d2f14-125">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="d2f14-126">診斷</span><span class="sxs-lookup"><span data-stu-id="d2f14-126">Diagnostics</span></span>

<span data-ttu-id="d2f14-127">若要測量您連線的品質，說 **[啟用診斷]** 在全像攝影版的遠端播放程式的主畫面。</span><span class="sxs-lookup"><span data-stu-id="d2f14-127">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="d2f14-128">當診斷啟用後時，應用程式會顯示您：</span><span class="sxs-lookup"><span data-stu-id="d2f14-128">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="d2f14-129">**FPS** -呈現的畫面格的平均數目遠端處理播放程式會接收和每秒轉譯。</span><span class="sxs-lookup"><span data-stu-id="d2f14-129">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="d2f14-130">理想狀況是 60 FPS。</span><span class="sxs-lookup"><span data-stu-id="d2f14-130">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="d2f14-131">**延遲**-平均的從您的電腦移至 HoloLens 的畫面格所花費的時間量。</span><span class="sxs-lookup"><span data-stu-id="d2f14-131">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="d2f14-132">愈低愈好。</span><span class="sxs-lookup"><span data-stu-id="d2f14-132">The lower the better.</span></span> <span data-ttu-id="d2f14-133">這是多半取決於您的 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="d2f14-133">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="d2f14-134">在 主畫面中，您可以說**停用 診斷**關閉診斷。</span><span class="sxs-lookup"><span data-stu-id="d2f14-134">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="d2f14-135">電腦的系統需求</span><span class="sxs-lookup"><span data-stu-id="d2f14-135">PC System Requirements</span></span>
* <span data-ttu-id="d2f14-136">您的電腦**必須**執行 Windows 10 年度更新版。</span><span class="sxs-lookup"><span data-stu-id="d2f14-136">Your PC **must** be running the Windows 10 Anniversary Update.</span></span>
* <span data-ttu-id="d2f14-137">我們建議 GeForce GTX 970 或 AMD Radeon R9 290 或更好的圖形卡。</span><span class="sxs-lookup"><span data-stu-id="d2f14-137">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="d2f14-138">我們建議您透過乙太網路，以減少無線躍點數目的網路連接您的電腦。</span><span class="sxs-lookup"><span data-stu-id="d2f14-138">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2f14-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2f14-139">See Also</span></span>
* [<span data-ttu-id="d2f14-140">全像攝影版的遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="d2f14-140">Holographic remoting software license terms</span></span>](microsoft-holographic-remoting-software-license-terms.md)
* [<span data-ttu-id="d2f14-141">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="d2f14-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
