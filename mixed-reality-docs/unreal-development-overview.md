---
title: Unreal 開發概觀
description: 開始在 Unreal 中建置混合實境應用程式。
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, 串流, 遠端, 混合實境, 開發, 開始使用, 新專案, 模擬器, 文件
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491177"
---
# <a name="unreal-development-overview"></a><span data-ttu-id="589f7-104">Unreal 開發概觀</span><span class="sxs-lookup"><span data-stu-id="589f7-104">Unreal development overview</span></span>

<span data-ttu-id="589f7-105">Unreal Engine 4 的混合實境支援現在是搶鮮版！</span><span class="sxs-lookup"><span data-stu-id="589f7-105">Mixed reality support for Unreal Engine 4 is now in beta!</span></span> <span data-ttu-id="589f7-106">如果您是 Unreal 開發的新手，<a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">開始使用 Unreal Engine 4</a> 是一個絕佳的探索頁面。</span><span class="sxs-lookup"><span data-stu-id="589f7-106">If you're new to Unreal development, <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Getting Started with Unreal Engine 4</a> is a great page to explore.</span></span> <span data-ttu-id="589f7-107">如果您需要資產，Unreal 具有完整的 <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>。</span><span class="sxs-lookup"><span data-stu-id="589f7-107">If you need assets, Unreal has a comprehensive <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>.</span></span> 

<span data-ttu-id="589f7-108">在您具備 Unreal Engine 4 的基本了解之後，您可以造訪 Unreal Engine 文件網站上的 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens 開發</a>頁面，以了解如何在 HoloLens 上建置及執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="589f7-108">Once you've built a basic understanding of Unreal Engine 4, you can visit the <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens Development</a> page on the Unreal Engine documentation site to learn how to build and run your apps on HoloLens.</span></span> <span data-ttu-id="589f7-109">請務必造訪 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 混合實境論壇</a>，與在 Unreal 中建置混合實境應用程式的社群進行互動。</span><span class="sxs-lookup"><span data-stu-id="589f7-109">Be sure to visit the <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality forums</a> to engage with the community who build mixed reality apps in Unreal.</span></span> <span data-ttu-id="589f7-110">這是尋找您可能遇到問題解決方案的絕佳位置。</span><span class="sxs-lookup"><span data-stu-id="589f7-110">It's a great place to find solutions to problems you might run into.</span></span>

## <a name="installing-the-prerequisites"></a><span data-ttu-id="589f7-111">安裝必要條件</span><span class="sxs-lookup"><span data-stu-id="589f7-111">Installing the prerequisites</span></span>

<span data-ttu-id="589f7-112">若要開始在 Unreal 中建置 HoloLens 2 應用程式，您需要 [HoloLens 2 模擬器](using-the-hololens-emulator.md)或 HoloLens 頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="589f7-112">To get started with building a HoloLens 2 app in Unreal, you'll need the [HoloLens 2 Emulator](using-the-hololens-emulator.md) or a HoloLens headset.</span></span> <span data-ttu-id="589f7-113">您也需要安裝最新版本的 Visual Studio，其中包含<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">適用於 Unreal 的 HoloLens 2 必要條件</a>中列出的工作負載和元件。</span><span class="sxs-lookup"><span data-stu-id="589f7-113">You'll also need to install the latest version of Visual Studio with the workloads and components listed in <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">HoloLens 2 Prerequisites for Unreal</a>.</span></span>

## <a name="building-and-running-your-unreal-app"></a><span data-ttu-id="589f7-114">建置並執行您的 Unreal 應用程式</span><span class="sxs-lookup"><span data-stu-id="589f7-114">Building and running your Unreal app</span></span>

<span data-ttu-id="589f7-115">首先，<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">封裝您的 HoloLens 2 應用程式</a>。</span><span class="sxs-lookup"><span data-stu-id="589f7-115">First, <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">package your app for HoloLens 2</a>.</span></span> <span data-ttu-id="589f7-116">接下來，選擇您想要部署套件的位置：</span><span class="sxs-lookup"><span data-stu-id="589f7-116">Next, choose where you want to deploy your package:</span></span>
* <span data-ttu-id="589f7-117"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">部署至 HoloLens 2 模擬器</a></span><span class="sxs-lookup"><span data-stu-id="589f7-117"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">Deploy to the HoloLens 2 Emulator</a></span></span>
* <span data-ttu-id="589f7-118"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">部署至 HoloLens 2 頭戴式裝置</a></span><span class="sxs-lookup"><span data-stu-id="589f7-118"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">Deploy to a HoloLens 2 Headset</a></span></span>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a><span data-ttu-id="589f7-119">透過全像攝影遠端處理播放器將您的應用程式串流至頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="589f7-119">Streaming your app to a headset via the Holographic Remoting Player</span></span>

<span data-ttu-id="589f7-120">將您的應用程式從桌面串流至 HoloLens 頭戴式裝置上的全像攝影遠端處理播放器應用程式有兩個主要優點：</span><span class="sxs-lookup"><span data-stu-id="589f7-120">Streaming your app from your desktop to the Holographic Remoting Player app on a HoloLens headset has two main advantages:</span></span> 
* <span data-ttu-id="589f7-121">加速開發，讓您不需要在每次進行變更時重新封裝及上傳您的應用程式</span><span class="sxs-lookup"><span data-stu-id="589f7-121">Speeds up development, so there's no need to repackage and upload your app each time you make a change</span></span>
* <span data-ttu-id="589f7-122">利用桌面的功能，讓您可以轉譯成桌面 GPU 所允許的多個多邊形，而不受頭戴式裝置上可用電腦的限制</span><span class="sxs-lookup"><span data-stu-id="589f7-122">Leverages the power of your desktop, so you can render as many polygons as your desktop GPU allows, without being limited by the computer available on the headset</span></span>

<span data-ttu-id="589f7-123">若要開始使用串流，請參閱 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 串流快速入門</a>[]()。</span><span class="sxs-lookup"><span data-stu-id="589f7-123">To get started with streaming, check out the <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 Streaming Quick Start</a>[]().</span></span>

## <a name="see-also"></a><span data-ttu-id="589f7-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="589f7-124">See also</span></span>
* <span data-ttu-id="589f7-125"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">行動裝置的 Unreal 效能指導方針</a></span><span class="sxs-lookup"><span data-stu-id="589f7-125"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a></span></span>
