---
title: Unity 遊戲模式
description: 使用 Unity 編輯器中的播放模式，而不需要部署應用程式中預覽您的裝置上的變更。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 遠端、 全像攝影版的遠端處理、 全像攝影版的遠端播放程式
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591183"
---
# <a name="unity-play-mode"></a><span data-ttu-id="ad9e2-104">Unity 遊戲模式</span><span class="sxs-lookup"><span data-stu-id="ad9e2-104">Unity Play Mode</span></span>

<span data-ttu-id="ad9e2-105">在 Unity 專案上工作的快速方法是使用 「 播放模式 」。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="ad9e2-106">這會執行您的應用程式在本機在 Unity 編輯器在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="ad9e2-107">Unity 提供快速的方式，來預覽您的內容，在實際的 HoloLens 裝置上使用全像攝影版的遠端執行功能。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="ad9e2-108">使用全像攝影版的遠端執行功能的 unity 遊戲模式</span><span class="sxs-lookup"><span data-stu-id="ad9e2-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="ad9e2-109">使用全像攝影版的遠端執行功能，您可以在您的電腦上執行 Unity editor 中體驗 HoloLens，您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="ad9e2-110">視線、 手勢、 語音和空間的對應輸入會傳送您 HoloLens 從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="ad9e2-111">呈現的畫面，接著會傳送回到您 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="ad9e2-112">這是適合用來快速偵錯應用程式，而不需要建置和部署完整的專案。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="ad9e2-113">在您的 HoloLens 上移至**Microsoft Store**並安裝**[全像攝影版的遠端播放程式](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="ad9e2-114">在您的 HoloLens 上啟動**全像攝影版的遠端播放程式**應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="ad9e2-115">在 Unity 中，移至\*\* 視窗**功能表，然後選取**全像攝影版的模擬\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="ad9e2-116">設定**模擬模式**要**裝置的遠端**。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="ad9e2-117">針對**遠端機器**，輸入您的 HoloLens 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="ad9e2-118">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-118">Click **Connect**.</span></span> <span data-ttu-id="ad9e2-119">您應該會看到**連線狀態**變更為**Connected**看到變成 HoloLens 在空白畫面。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="ad9e2-120">按一下 **播放**按鈕以啟動播放模式，並體驗您的 HoloLens 上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="ad9e2-121">全像攝影版的遠端處理需要快速的 PC 和 Wi-fi 連線。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="ad9e2-122">請參閱[全像攝影版的遠端播放程式](holographic-remoting-player.md)的完整詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="ad9e2-123">為了獲得最佳結果，確定您的應用程式正確地設定[專注點](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="ad9e2-124">這有助於全像攝影版的遠端執行功能最能適應您的場景方向，以您的無線連線的延遲。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad9e2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad9e2-125">See Also</span></span>
* [<span data-ttu-id="ad9e2-126">全像攝影版的遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="ad9e2-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
