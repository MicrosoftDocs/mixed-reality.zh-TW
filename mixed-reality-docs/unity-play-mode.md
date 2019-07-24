---
title: Unity 播放模式
description: 在 Unity 編輯器中使用 [播放] 模式, 即可在不部署應用程式的情況下, 預覽裝置上的變更。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 遠端, 全像攝影遠端, 全像攝影遠端播放
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548725"
---
# <a name="unity-play-mode"></a><span data-ttu-id="76a08-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="76a08-104">Unity Play Mode</span></span>

<span data-ttu-id="76a08-105">處理 Unity 專案的快速方式是使用「播放模式」。</span><span class="sxs-lookup"><span data-stu-id="76a08-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="76a08-106">這會在您的電腦上, 于 Unity 編輯器中本機執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="76a08-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="76a08-107">Unity 使用全像攝影遠端來提供快速的方式, 以在真實的 HoloLens 裝置上預覽內容。</span><span class="sxs-lookup"><span data-stu-id="76a08-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="76a08-108">使用全像攝影遠端的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="76a08-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="76a08-109">使用全像攝影遠端功能時, 您可以在 HoloLens 上體驗應用程式, 而在電腦上的 Unity 編輯器中執行。</span><span class="sxs-lookup"><span data-stu-id="76a08-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="76a08-110">「注視」、「手勢」、「語音」和「空間對應」輸入都會從您的 HoloLens 傳送到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="76a08-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="76a08-111">轉譯後的框架會傳送回您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="76a08-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="76a08-112">這是在無需建立和部署完整專案的情況下, 快速地對應用程式進行錯用的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="76a08-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="76a08-113">在您的 HoloLens 上移至 **Microsoft Store** 並安裝 **[全像攝影版的遠端播放程式](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="76a08-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="76a08-114">在您的 HoloLens 上, 啟動全像攝影版的**遠端播放機**應用程式。</span><span class="sxs-lookup"><span data-stu-id="76a08-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="76a08-115">在 Unity 中，移至 **視窗** 功能表，然後選取 **全像攝影版的模擬** 。</span><span class="sxs-lookup"><span data-stu-id="76a08-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="76a08-116">將**模擬模式**設定為 [**遠端至裝置**]。</span><span class="sxs-lookup"><span data-stu-id="76a08-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="76a08-117">針對 [**遠端電腦**], 輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="76a08-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="76a08-118">按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="76a08-118">Click **Connect**.</span></span> <span data-ttu-id="76a08-119">您應該會看到 [連線**狀態**] 變更為 [**已連接**], 並在 HoloLens 中看到畫面變成空白。</span><span class="sxs-lookup"><span data-stu-id="76a08-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="76a08-120">按一下 [**播放**] 按鈕以啟動播放模式, 並在 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="76a08-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="76a08-121">全像攝影遠端處理需要快速的電腦和 Wi-fi 連線。</span><span class="sxs-lookup"><span data-stu-id="76a08-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="76a08-122">如需完整詳細資料, 請參閱全像攝影[遠端播放](holographic-remoting-player.md)程式。</span><span class="sxs-lookup"><span data-stu-id="76a08-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="76a08-123">為獲得最佳結果, 請確定您的應用程式已正確設定[焦點點](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="76a08-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="76a08-124">這可協助全像攝影的遠端處理, 以最符合您的無線連線延遲來調整您的場景。</span><span class="sxs-lookup"><span data-stu-id="76a08-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="76a08-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76a08-125">See Also</span></span>
* [<span data-ttu-id="76a08-126">全像攝影遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="76a08-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
