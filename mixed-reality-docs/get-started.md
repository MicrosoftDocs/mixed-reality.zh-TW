---
title: 立即開始
description: 本指南概要說明最快的方法，以啟動並執行混合的實境開發。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 要開始，基本概念、 HoloLens、 沈浸式耳機、 ar、 vr、 unity、 visual studio、 快速入門中，如何
ms.openlocfilehash: 92fbc6eee227da571ff36401f84cf81a093062d7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594861"
---
# <a name="get-started"></a><span data-ttu-id="52b9a-104">立即開始</span><span class="sxs-lookup"><span data-stu-id="52b9a-104">Get started</span></span>

<span data-ttu-id="52b9a-105">歡迎來到混合的實境開發的世界 ！</span><span class="sxs-lookup"><span data-stu-id="52b9a-105">Welcome to the world of mixed reality development!</span></span> <span data-ttu-id="52b9a-106">如果您還不熟悉 MR，本指南會啟動您的中樞，並盡快執行。</span><span class="sxs-lookup"><span data-stu-id="52b9a-106">If you're new to MR, this guide will be your hub to get up and running as quickly as possible.</span></span> <span data-ttu-id="52b9a-107">我們將協助您讓您的電腦集更適用於開發、 準備您的裝置，並安裝將會加速 MR 開發程序的工具。</span><span class="sxs-lookup"><span data-stu-id="52b9a-107">We'll help you get your PC set up for development, get your device(s) ready, and install tools that will speed up the MR development process.</span></span> 

## <a name="intro-to-mixed-reality"></a><span data-ttu-id="52b9a-108">簡介混合實境</span><span class="sxs-lookup"><span data-stu-id="52b9a-108">Intro to mixed reality</span></span>

<span data-ttu-id="52b9a-109">您可能會有一些疑問所熟知的 「 混合實境 」，以及它與要擴增實境 (AR) 和虛擬實境 (VR)。</span><span class="sxs-lookup"><span data-stu-id="52b9a-109">You may have some questions about what we mean by "mixed reality" and how it relates to augmented reality (AR) and virtual reality (VR).</span></span> <span data-ttu-id="52b9a-110">簡單地說，混合的實境是混合，其與數位世界中，實體世界的範圍涵蓋所有項目從擴增實境，因此在真實世界中，虛擬實境，以您實際其中幾乎完全是放置數位內容由數位所取代。</span><span class="sxs-lookup"><span data-stu-id="52b9a-110">In short, mixed reality is the blending of the physical world with the digital world, so it's a spectrum that covers everything from augmented reality, where digital content is placed in the real world, to virtual reality, where your real world is almost entirely replaced by the digital.</span></span> 

<span data-ttu-id="52b9a-111">![支援 HoloLens 和沈浸式 (VR) 耳機 mixed 的 reality 應用程式的範例](images/mr-island.png)</span><span class="sxs-lookup"><span data-stu-id="52b9a-111">![Example of a mixed reality app that supports both HoloLens and immersive (VR) headsets](images/mr-island.png)</span></span><br>
<span data-ttu-id="52b9a-112">*HoloLens 和沈浸式 (VR) 耳機，可支援混合的實境應用程式*</span><span class="sxs-lookup"><span data-stu-id="52b9a-112">*Mixed reality apps can support both HoloLens and immersive (VR) headsets*</span></span>

<span data-ttu-id="52b9a-113">我們建立 Windows Mixed Reality 做為單一的開發平台和 MR 範圍，就可以涵蓋的工具組，而且我們目前支援兩種裝置類型，其中涵蓋相同的範圍：[Microsoft HoloLens](https://www.microsoft.com/hololens)，全世界第一個獨立全像攝影版耳機，並[Windows Mixed Reality 沈浸式耳機和動作控制器](https://www.microsoft.com/windows/windows-mixed-reality)，連線至電腦上以功能強大的虛擬實境體驗。</span><span class="sxs-lookup"><span data-stu-id="52b9a-113">We created Windows Mixed Reality as a single development platform and set of tools that can cover the MR spectrum, and we currently support two device types that cover the same spectrum: [Microsoft HoloLens](https://www.microsoft.com/hololens), the world's first self-contained holographic headset, and [Windows Mixed Reality immersive headsets and motion controllers](https://www.microsoft.com/windows/windows-mixed-reality), which connect to a PC for powerful virtual reality experiences.</span></span> <span data-ttu-id="52b9a-114">您可以看看我們什麼 [混合實境？]（如果您想要更全面的回答的文章。</span><span class="sxs-lookup"><span data-stu-id="52b9a-114">You can check out our What is [mixed reality?]( article for a more thorough answer if you're interested.</span></span>

## <a name="choose-your-development-path"></a><span data-ttu-id="52b9a-115">選擇您開發的路徑</span><span class="sxs-lookup"><span data-stu-id="52b9a-115">Choose your development path</span></span>

<span data-ttu-id="52b9a-116">開發混合的實境應用程式的最簡單方式使用[Unity](https://unity3d.com)，通常用來開發遊戲的強大且受歡迎的中介軟體工具。</span><span class="sxs-lookup"><span data-stu-id="52b9a-116">The easiest way to develop a mixed reality app is using [Unity](https://unity3d.com), a powerful and popular middleware tool often used for game development.</span></span> <span data-ttu-id="52b9a-117">如果您想要使用自訂的引擎，您也可以[針對 DirectX 建置](directx-development-overview.md)，但大部分 MR 開發人員使用 Unity 進行其遊戲和應用程式。</span><span class="sxs-lookup"><span data-stu-id="52b9a-117">If you want to use a custom engine, you can also [build against DirectX](directx-development-overview.md), but most MR developers use Unity for their games and apps.</span></span> <span data-ttu-id="52b9a-118">使用 Unity，您將可以建立目標 HoloLens、 沈浸式 (VR) 耳機，或兩者的混合的實境應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="52b9a-118">With Unity you'll be able to create a mixed reality app that targets HoloLens, immersive (VR) headsets, or both!</span></span>

## <a name="prepare-your-pc-and-devices-for-development"></a><span data-ttu-id="52b9a-119">準備您的電腦和裝置進行開發</span><span class="sxs-lookup"><span data-stu-id="52b9a-119">Prepare your PC and devices for development</span></span>

<span data-ttu-id="52b9a-120">不論您要建置以 HoloLens、 沈浸式 (VR) 耳機，或兩者為目標的混合的實境應用程式，您將使用一組常用的工具和 Api。</span><span class="sxs-lookup"><span data-stu-id="52b9a-120">Whether you're building a mixed reality app that targets HoloLens, immersive (VR) headsets, or both, you'll be using a common set of tools and APIs.</span></span> <span data-ttu-id="52b9a-121">您也會想要確定您的電腦是強大的開發時要執行。</span><span class="sxs-lookup"><span data-stu-id="52b9a-121">You'll also want to make sure your PC is powerful enough for the development you'll be doing.</span></span> 

>[!NOTE]
><span data-ttu-id="52b9a-122">您可以找到我們在開發電腦上的建議規格，支援的版本，每個軟體工具，以及相關設定附註中的 for each[安裝工具](install-the-tools.md)文章。</span><span class="sxs-lookup"><span data-stu-id="52b9a-122">You can find our recommendations on development PC specs, supported versions of each software tool, and relevant settings or configuration notes for each in the [Install the tools](install-the-tools.md) article.</span></span> <span data-ttu-id="52b9a-123">請安裝下列工具之前，檢閱該文章。</span><span class="sxs-lookup"><span data-stu-id="52b9a-123">Please review that article before installing the tools below.</span></span>

<span data-ttu-id="52b9a-124">若要安裝的工具：</span><span class="sxs-lookup"><span data-stu-id="52b9a-124">Tools to install:</span></span>
* [<span data-ttu-id="52b9a-125">Unity</span><span class="sxs-lookup"><span data-stu-id="52b9a-125">Unity</span></span>](https://store.unity.com/download)
* [<span data-ttu-id="52b9a-126">Visual Studio (使用 Windows 10 SDK)</span><span class="sxs-lookup"><span data-stu-id="52b9a-126">Visual Studio (with Windows 10 SDK)</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="52b9a-127">混合的實境適用於 Unity 的工具組</span><span class="sxs-lookup"><span data-stu-id="52b9a-127">Mixed Reality Toolkit for Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

<span data-ttu-id="52b9a-128">您也會想要[將您的目標裝置放入開發人員模式和設定 Visual Studio 的應用程式部署到目標裝置](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="52b9a-128">You'll also want to [put your target device into Developer mode and configure Visual Studio for deploying apps to the target device](using-visual-studio.md).</span></span>

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="52b9a-129">有關用於 Unity 的混合實境工具組的注意事項</span><span class="sxs-lookup"><span data-stu-id="52b9a-129">A note about the Mixed Reality Toolkit for Unity</span></span>

![MRTK for Unity](images/mrtkandunity.png)<br>

<span data-ttu-id="52b9a-131">***YOYO 請細節時，並告訴大家，為什麼 MRTK UNITY 是因此令人讚嘆且所有酷炫的內容有內:)***</span><span class="sxs-lookup"><span data-stu-id="52b9a-131">***YOYO PLEASE FLESH THIS OUT AND TELL EVERYONE WHY MRTK-UNITY IS SO AMAZING AND ALL THE COOL THINGS IT HAS INSIDE :)***</span></span>

<span data-ttu-id="52b9a-132">混合實境工具組是指令碼的集合，而且元件能加速開發以 Microsoft HoloLens 與 Windows Mixed Reality 耳機為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="52b9a-132">The Mixed Reality Toolkit is a collection of scripts and components intended to accelerate development of applications targeting Microsoft HoloLens and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="52b9a-133">專案被針對至項目，以建立混合的實境應用程式以及貢獻回饋給社群隨著我們越來越減少屏障。</span><span class="sxs-lookup"><span data-stu-id="52b9a-133">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span>

## <a name="start-your-first-mr-project"></a><span data-ttu-id="52b9a-134">啟動您的第一個 MR 專案</span><span class="sxs-lookup"><span data-stu-id="52b9a-134">Start your first MR project</span></span>

<span data-ttu-id="52b9a-135">現在，您的電腦和裝置設定，您即可建立在 Unity 中的第一個混合的實境專案。</span><span class="sxs-lookup"><span data-stu-id="52b9a-135">Now that your PC and device(s) are set up, you're ready to create your first mixed reality project in Unity.</span></span> <span data-ttu-id="52b9a-136">遵循我們第一個 MR academy 課程[MR 基本概念 100:開始使用 Unity](holograms-100.md)，結束時，您將會擁有啟動並執行混合的實境耳機的 cube。</span><span class="sxs-lookup"><span data-stu-id="52b9a-136">Follow along with our first MR academy course, [MR Basics 100: Getting started with Unity](holograms-100.md), and by the end you'll have a cube up and running in a mixed reality headset.</span></span>

<span data-ttu-id="52b9a-137">![混合的實境 Unity 專案中之 cube 的螢幕擷取畫面](images/mr-cube.PNG)</span><span class="sxs-lookup"><span data-stu-id="52b9a-137">![Screenshot of a cube in a mixed reality Unity project](images/mr-cube.PNG)</span></span><br>
<span data-ttu-id="52b9a-138">*第一個混合的實境專案中 Unity-hello world ！*</span><span class="sxs-lookup"><span data-stu-id="52b9a-138">*Your first mixed reality project in Unity - hello world!*</span></span>

## <a name="learn-more-and-get-help"></a><span data-ttu-id="52b9a-139">進一步了解，並取得協助</span><span class="sxs-lookup"><span data-stu-id="52b9a-139">Learn more and get help</span></span>

<span data-ttu-id="52b9a-140">既然您已成功建立第一個 MR 專案，您可能飢餓了 ！</span><span class="sxs-lookup"><span data-stu-id="52b9a-140">Now that you've successfully created your first MR project, you're probably hungry for more!</span></span> <span data-ttu-id="52b9a-141">以下是一些應該可以幫助的資源：</span><span class="sxs-lookup"><span data-stu-id="52b9a-141">Here are some resources that should help:</span></span>
* <span data-ttu-id="52b9a-142">[混合實境開發人員文件](mixed-reality.md)-您已經在這裡，但還有更多檢查，包括技術文件、 設計指引、 範例專案，以及案例研究。</span><span class="sxs-lookup"><span data-stu-id="52b9a-142">[Mixed reality developer documentation](mixed-reality.md) - you're already here, but there's so much more to check out, including technical documentation, design guidance, sample projects, and case studies.</span></span>
* <span data-ttu-id="52b9a-143">[混合的實境 academy](academy.md) -依照本教學課程涵蓋範圍從專案中，實作核心 MR 建置組塊所設定，來整合 Azure 雲端服務到 MR 應用程式。</span><span class="sxs-lookup"><span data-stu-id="52b9a-143">[Mixed reality academy](academy.md) - follow along with tutorials covering everything from setting up projects, to implementing core MR building blocks, to integrating Azure cloud services into your MR app.</span></span>
* <span data-ttu-id="52b9a-144">[了解 Unity](https://unity3d.com/learn) -Unity 的網站提供的教學課程、 專案和現場直播訓練工作階段建立者的每個階段的學習。</span><span class="sxs-lookup"><span data-stu-id="52b9a-144">[Learn Unity](https://unity3d.com/learn) - Unity's website offers tutorials, projects, and live training sessions for creators at every stage of learning.</span></span>

<span data-ttu-id="52b9a-145">您也可以從這些絕佳的社群資源取得說明：</span><span class="sxs-lookup"><span data-stu-id="52b9a-145">You can also get help from these great community resources:</span></span>
* <span data-ttu-id="52b9a-146">[混合實境開發人員論壇](https://forums.hololens.com/)-混合的實境開發人員，可以詢問和回答問題，以及讀取 MR 開發人員新聞，直接從 Microsoft 的官方論壇。</span><span class="sxs-lookup"><span data-stu-id="52b9a-146">[Mixed reality developer forums](https://forums.hololens.com/) - the official forum for mixed reality developers to ask and answer questions, as well as read MR development news straight from Microsoft.</span></span>
* <span data-ttu-id="52b9a-147">[HoloDevelopers Slack 通道](https://holodevelopersslack.azurewebsites.net/)-最強大且豐富的外部混合實境特有的開發人員通道; 這裡的開發人員都了解並有幫助。</span><span class="sxs-lookup"><span data-stu-id="52b9a-147">[HoloDevelopers Slack channel](https://holodevelopersslack.azurewebsites.net/) - the most robust and resourceful external mixed reality-specific developer channel; the devs here are knowledgeable and helpful.</span></span>
* <span data-ttu-id="52b9a-148">[Unity 論壇](https://forum.unity3d.com/)-Unity 的官方論壇。</span><span class="sxs-lookup"><span data-stu-id="52b9a-148">[Unity forums](https://forum.unity3d.com/) - Unity's official forums.</span></span>
