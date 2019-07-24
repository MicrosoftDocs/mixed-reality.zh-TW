---
title: 開始使用
description: 本指南概述啟動和執行混合現實開發的最快方式。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 開始使用, 基本, HoloLens, 沉浸式耳機, ar, vr, unity, visual studio, 快速入門, 如何
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873964"
---
# <a name="get-started"></a><span data-ttu-id="314e4-104">開始使用</span><span class="sxs-lookup"><span data-stu-id="314e4-104">Get started</span></span>

<span data-ttu-id="314e4-105">歡迎來到混合現實開發的世界!</span><span class="sxs-lookup"><span data-stu-id="314e4-105">Welcome to the world of mixed reality development!</span></span> <span data-ttu-id="314e4-106">如果您不熟悉 MR, 本指南將會讓您的中樞儘快啟動並執行。</span><span class="sxs-lookup"><span data-stu-id="314e4-106">If you're new to MR, this guide will be your hub to get up and running as quickly as possible.</span></span> <span data-ttu-id="314e4-107">我們將協助您設定電腦以進行開發、準備好您的裝置, 以及安裝可加速 MR 開發流程的工具。</span><span class="sxs-lookup"><span data-stu-id="314e4-107">We'll help you get your PC set up for development, get your device(s) ready, and install tools that will speed up the MR development process.</span></span> 

## <a name="intro-to-mixed-reality"></a><span data-ttu-id="314e4-108">混合現實簡介</span><span class="sxs-lookup"><span data-stu-id="314e4-108">Intro to mixed reality</span></span>

<span data-ttu-id="314e4-109">您可能會有一些關於所謂「mixed reality」的問題, 以及它如何與增強的現實 (AR) 和虛擬實境 (VR) 有關。</span><span class="sxs-lookup"><span data-stu-id="314e4-109">You may have some questions about what we mean by "mixed reality" and how it relates to augmented reality (AR) and virtual reality (VR).</span></span> <span data-ttu-id="314e4-110">簡單地說, 混合現實是實體世界與數位世界的混合, 所以它是一種涵蓋所有內容的範圍, 從增強的現實中, 數位內容放在真實世界, 到虛擬實境, 而現實世界幾乎完全已由數位取代。</span><span class="sxs-lookup"><span data-stu-id="314e4-110">In short, mixed reality is the blending of the physical world with the digital world, so it's a spectrum that covers everything from augmented reality, where digital content is placed in the real world, to virtual reality, where your real world is almost entirely replaced by the digital.</span></span> 

<span data-ttu-id="314e4-111">![支援 HoloLens 和沉浸式 (VR) 耳機的混合現實應用程式範例](images/mr-island.png)</span><span class="sxs-lookup"><span data-stu-id="314e4-111">![Example of a mixed reality app that supports both HoloLens and immersive (VR) headsets](images/mr-island.png)</span></span><br>
<span data-ttu-id="314e4-112">*混合現實應用程式可以同時支援 HoloLens 和沉浸式 (VR) 耳機*</span><span class="sxs-lookup"><span data-stu-id="314e4-112">*Mixed reality apps can support both HoloLens and immersive (VR) headsets*</span></span>

<span data-ttu-id="314e4-113">我們建立了 Windows Mixed Reality 做為單一開發平臺和一組可涵蓋 MR 頻譜的工具, 我們目前支援兩種涵蓋相同頻譜的裝置類型:[Microsoft HoloLens](https://www.microsoft.com/hololens)、全球第一部獨立的全像耳機, 以及[Windows Mixed Reality 的沉浸式耳機和運動控制器](https://www.microsoft.com/windows/windows-mixed-reality), 這些都是連接到電腦以提供強大的虛擬實境體驗。</span><span class="sxs-lookup"><span data-stu-id="314e4-113">We created Windows Mixed Reality as a single development platform and set of tools that can cover the MR spectrum, and we currently support two device types that cover the same spectrum: [Microsoft HoloLens](https://www.microsoft.com/hololens), the world's first self-contained holographic headset, and [Windows Mixed Reality immersive headsets and motion controllers](https://www.microsoft.com/windows/windows-mixed-reality), which connect to a PC for powerful virtual reality experiences.</span></span> <span data-ttu-id="314e4-114">您可以查看我們的 [mixed reality？](如果您有興趣, 請參閱文章以取得更完整的答案。</span><span class="sxs-lookup"><span data-stu-id="314e4-114">You can check out our What is [mixed reality?]( article for a more thorough answer if you're interested.</span></span>

## <a name="choose-your-development-path"></a><span data-ttu-id="314e4-115">選擇您的開發路徑</span><span class="sxs-lookup"><span data-stu-id="314e4-115">Choose your development path</span></span>

<span data-ttu-id="314e4-116">開發混合現實應用程式最簡單的方式是使用[Unity](https://unity3d.com), 這是一種功能強大且常用的中介軟體工具, 通常用於遊戲開發。</span><span class="sxs-lookup"><span data-stu-id="314e4-116">The easiest way to develop a mixed reality app is using [Unity](https://unity3d.com), a powerful and popular middleware tool often used for game development.</span></span> <span data-ttu-id="314e4-117">如果您想要使用自訂引擎, 也可以[針對 DirectX 建立](directx-development-overview.md), 但大部分的 MR 開發人員會針對其遊戲和應用程式使用 Unity。</span><span class="sxs-lookup"><span data-stu-id="314e4-117">If you want to use a custom engine, you can also [build against DirectX](directx-development-overview.md), but most MR developers use Unity for their games and apps.</span></span> <span data-ttu-id="314e4-118">有了 Unity, 您就能夠建立以 HoloLens、沉浸式 (VR) 耳機或兩者為目標的混合現實應用程式!</span><span class="sxs-lookup"><span data-stu-id="314e4-118">With Unity you'll be able to create a mixed reality app that targets HoloLens, immersive (VR) headsets, or both!</span></span>

## <a name="prepare-your-pc-and-devices-for-development"></a><span data-ttu-id="314e4-119">準備您的電腦和裝置以進行開發</span><span class="sxs-lookup"><span data-stu-id="314e4-119">Prepare your PC and devices for development</span></span>

<span data-ttu-id="314e4-120">無論您是否正在建立以 HoloLens、沉浸式 (VR) 耳機為目標的混合現實應用程式, 您都將使用一組常用的工具和 Api。</span><span class="sxs-lookup"><span data-stu-id="314e4-120">Whether you're building a mixed reality app that targets HoloLens, immersive (VR) headsets, or both, you'll be using a common set of tools and APIs.</span></span> <span data-ttu-id="314e4-121">您也會想要確定您的電腦功能強大, 可用於您要進行的開發。</span><span class="sxs-lookup"><span data-stu-id="314e4-121">You'll also want to make sure your PC is powerful enough for the development you'll be doing.</span></span> 

>[!NOTE]
><span data-ttu-id="314e4-122">您可以在開發電腦規格、每個軟體工具的支援版本, 以及每個[安裝工具](install-the-tools.md)一文中的相關設定或設定注意事項中找到我們的建議。</span><span class="sxs-lookup"><span data-stu-id="314e4-122">You can find our recommendations on development PC specs, supported versions of each software tool, and relevant settings or configuration notes for each in the [Install the tools](install-the-tools.md) article.</span></span> <span data-ttu-id="314e4-123">請先參閱該文章, 再安裝下列工具。</span><span class="sxs-lookup"><span data-stu-id="314e4-123">Please review that article before installing the tools below.</span></span>

<span data-ttu-id="314e4-124">要安裝的工具:</span><span class="sxs-lookup"><span data-stu-id="314e4-124">Tools to install:</span></span>
* [<span data-ttu-id="314e4-125">Unity</span><span class="sxs-lookup"><span data-stu-id="314e4-125">Unity</span></span>](https://store.unity.com/download)
* [<span data-ttu-id="314e4-126">Visual Studio (含 Windows 10 SDK)</span><span class="sxs-lookup"><span data-stu-id="314e4-126">Visual Studio (with Windows 10 SDK)</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="314e4-127">Unity 的混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="314e4-127">Mixed Reality Toolkit for Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

<span data-ttu-id="314e4-128">您也會想要[讓目標裝置進入開發人員模式, 並設定 Visual Studio 將應用程式部署到目標裝置](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="314e4-128">You'll also want to [put your target device into Developer mode and configure Visual Studio for deploying apps to the target device](using-visual-studio.md).</span></span>

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="314e4-129">Unity 混合現實工具組的相關注意事項</span><span class="sxs-lookup"><span data-stu-id="314e4-129">A note about the Mixed Reality Toolkit for Unity</span></span>

![適用于 Unity 的 MRTK](images/mrtkandunity.png)<br>

<span data-ttu-id="314e4-131">***YOYO 請充實這項功能, 告訴每個人為什麼 MRTK-UNITY 非常令人驚奇, 而且它裡面的所有酷炫東西:)***</span><span class="sxs-lookup"><span data-stu-id="314e4-131">***YOYO PLEASE FLESH THIS OUT AND TELL EVERYONE WHY MRTK-UNITY IS SO AMAZING AND ALL THE COOL THINGS IT HAS INSIDE :)***</span></span>

<span data-ttu-id="314e4-132">Mixed Reality 工具組是腳本和元件的集合, 目的是要加速以 Microsoft HoloLens 和 Windows Mixed Reality 耳機為目標的應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="314e4-132">The Mixed Reality Toolkit is a collection of scripts and components intended to accelerate development of applications targeting Microsoft HoloLens and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="314e4-133">此專案的目標是減少建立混合實境應用程式的進入障礙，以及回饋伴著我們成長的社群。</span><span class="sxs-lookup"><span data-stu-id="314e4-133">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span>

## <a name="start-your-first-mr-project"></a><span data-ttu-id="314e4-134">開始您的第一個 MR 專案</span><span class="sxs-lookup"><span data-stu-id="314e4-134">Start your first MR project</span></span>

<span data-ttu-id="314e4-135">既然您的電腦和裝置已設定完成, 您就可以開始在 Unity 中建立第一個混合現實專案。</span><span class="sxs-lookup"><span data-stu-id="314e4-135">Now that your PC and device(s) are set up, you're ready to create your first mixed reality project in Unity.</span></span> <span data-ttu-id="314e4-136">遵循我們的第一位 mr 學術課程[, mr 基本概念 100:開始使用 Unity](holograms-100.md), 最後您將會在混合現實頭戴式裝置上啟動並執行 cube。</span><span class="sxs-lookup"><span data-stu-id="314e4-136">Follow along with our first MR academy course, [MR Basics 100: Getting started with Unity](holograms-100.md), and by the end you'll have a cube up and running in a mixed reality headset.</span></span>

<span data-ttu-id="314e4-137">![混合現實 Unity 專案中 cube 的螢幕擷取畫面](images/mr-cube.PNG)</span><span class="sxs-lookup"><span data-stu-id="314e4-137">![Screenshot of a cube in a mixed reality Unity project](images/mr-cube.PNG)</span></span><br>
<span data-ttu-id="314e4-138">*您在 Unity 中的第一個混合現實專案-hello world!*</span><span class="sxs-lookup"><span data-stu-id="314e4-138">*Your first mixed reality project in Unity - hello world!*</span></span>

## <a name="learn-more-and-get-help"></a><span data-ttu-id="314e4-139">深入瞭解並取得協助</span><span class="sxs-lookup"><span data-stu-id="314e4-139">Learn more and get help</span></span>

<span data-ttu-id="314e4-140">既然您已成功建立第一個 MR 專案, 您可能會有更多的需求。</span><span class="sxs-lookup"><span data-stu-id="314e4-140">Now that you've successfully created your first MR project, you're probably hungry for more!</span></span> <span data-ttu-id="314e4-141">以下是一些應協助的資源:</span><span class="sxs-lookup"><span data-stu-id="314e4-141">Here are some resources that should help:</span></span>
* <span data-ttu-id="314e4-142">[Mixed reality 開發人員檔](mixed-reality.md)-您已經在這裡, 但還有更多的資訊可以查看, 包括技術檔、設計指引、範例專案, 以及案例研究。</span><span class="sxs-lookup"><span data-stu-id="314e4-142">[Mixed reality developer documentation](mixed-reality.md) - you're already here, but there's so much more to check out, including technical documentation, design guidance, sample projects, and case studies.</span></span>
* <span data-ttu-id="314e4-143">[混合的現實教學](tutorials.md)課程-遵循涵蓋所有內容的教學課程, 包括設定專案、執行核心 MR 建築組塊、將 Azure 雲端服務整合到您的 MR 應用程式。</span><span class="sxs-lookup"><span data-stu-id="314e4-143">[Mixed reality tutorials](tutorials.md) - follow along with tutorials covering everything from setting up projects, to implementing core MR building blocks, to integrating Azure cloud services into your MR app.</span></span>
* <span data-ttu-id="314e4-144">[瞭解 unity](https://unity3d.com/learn) -unity 的網站提供教學課程、專案, 以及每個學習階段之建立者的即時訓練課程。</span><span class="sxs-lookup"><span data-stu-id="314e4-144">[Learn Unity](https://unity3d.com/learn) - Unity's website offers tutorials, projects, and live training sessions for creators at every stage of learning.</span></span>

<span data-ttu-id="314e4-145">您也可以從這些絕佳的社區資源取得協助:</span><span class="sxs-lookup"><span data-stu-id="314e4-145">You can also get help from these great community resources:</span></span>
* <span data-ttu-id="314e4-146">[Mixed reality 開發人員論壇](https://forums.hololens.com/)-適用于混合現實開發人員的官方論壇, 可詢問和回答問題, 以及直接閱讀 MICROSOFT 的 MR 開發新聞。</span><span class="sxs-lookup"><span data-stu-id="314e4-146">[Mixed reality developer forums](https://forums.hololens.com/) - the official forum for mixed reality developers to ask and answer questions, as well as read MR development news straight from Microsoft.</span></span>
* <span data-ttu-id="314e4-147">[HoloDevelopers 時差頻道](https://holodevelopersslack.azurewebsites.net/)-最健全且資源的外部混合現實特定開發人員通道;這裡的開發人員十分熟悉, 而且很有説明。</span><span class="sxs-lookup"><span data-stu-id="314e4-147">[HoloDevelopers Slack channel](https://holodevelopersslack.azurewebsites.net/) - the most robust and resourceful external mixed reality-specific developer channel; the devs here are knowledgeable and helpful.</span></span>
* <span data-ttu-id="314e4-148">[Unity 論壇](https://forum.unity3d.com/)-unity 的官方論壇。</span><span class="sxs-lookup"><span data-stu-id="314e4-148">[Unity forums](https://forum.unity3d.com/) - Unity's official forums.</span></span>
