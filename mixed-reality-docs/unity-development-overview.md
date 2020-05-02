---
title: Unity 開發概觀
description: 開始在 Unity 中建置混合實境應用程式。
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合實境, 開發, 開始使用, 新專案, 移植, 功能, 相機, 模擬, 模擬, 文件
ms.openlocfilehash: e0fe775f5fe891416145d91e52a5a801e049c568
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "81433414"
---
# <a name="unity-development-overview"></a><span data-ttu-id="f48d6-104">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="f48d6-104">Unity development overview</span></span>

<span data-ttu-id="f48d6-105">建置[混合實境應用程式](app-views.md)的最快速路徑是透過 [Unity](https://unity.com)。</span><span class="sxs-lookup"><span data-stu-id="f48d6-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](https://unity.com).</span></span> <span data-ttu-id="f48d6-106">我們建議您花一些時間來探索 [Unity 教學課程](https://unity3d.com/learn/tutorials)。</span><span class="sxs-lookup"><span data-stu-id="f48d6-106">We recommend that you take time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="f48d6-107">如果您需要資產，Unity 具有完整的[資產存放區](https://www.assetstore.unity3d.com/)。</span><span class="sxs-lookup"><span data-stu-id="f48d6-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="f48d6-108">建立 Unity 的基本了解之後，您可以造訪[教學課程](tutorials.md)，了解使用 Unity 進行混合實境開發的細節。</span><span class="sxs-lookup"><span data-stu-id="f48d6-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="f48d6-109">請務必造訪 [Unity 混合實境論壇](https://forum.unity3d.com/forums/hololens.102/)，與在 Unity 中建置混合實境應用程式的其他人互動，並找出您所遇到問題的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f48d6-109">Be sure to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>

<span data-ttu-id="f48d6-110">若要開始使用 Unity 建置混合實境應用程式，請先[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f48d6-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> 

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="f48d6-111">使用混合實境工具組的新 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="f48d6-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="f48d6-112">在 Unity 中開發最簡單的方式，就是使用混合實境工具組。</span><span class="sxs-lookup"><span data-stu-id="f48d6-112">The easiest way to develop in Unity is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="f48d6-113">這個工具組可協助您自動設定專案，並提供一組混合實境功能來加速您的開發。</span><span class="sxs-lookup"><span data-stu-id="f48d6-113">This will help you setup with the project automatically, and provide a set of mixed reality features to accelerate your development.</span></span> <span data-ttu-id="f48d6-114">請查看[混合實境工具組 v2](mrtk-getting-started.md) 以深入了解並開始使用。</span><span class="sxs-lookup"><span data-stu-id="f48d6-114">Please check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="f48d6-115">將現有的 Unity 應用程式移植到 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f48d6-115">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="f48d6-116">如果您有現有的 Unity 專案要移植到 Windows Mixed Reality，請遵循 [Unity 移植指南](porting-guides.md)以開始使用。</span><span class="sxs-lookup"><span data-stu-id="f48d6-116">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="f48d6-117">設定適用於 Windows Mixed Reality 的新 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="f48d6-117">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="f48d6-118">如果您想要在未匯入混合實境工具組的情況下建立新的 Unity 專案，則您需要為 Windows Mixed Reality 手動變更一小組 Unity 設定。</span><span class="sxs-lookup"><span data-stu-id="f48d6-118">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="f48d6-119">這些設定分成兩個類別：每個專案和每個場景。</span><span class="sxs-lookup"><span data-stu-id="f48d6-119">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="f48d6-120">請參閱這裡以取得[設定適用於 Windows Mixed Reality 的新 Unity 專案](Configure-Unity-Project.md)的逐步指南</span><span class="sxs-lookup"><span data-stu-id="f48d6-120">See here for a step by step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="f48d6-121">新增混合實境功能和輸入</span><span class="sxs-lookup"><span data-stu-id="f48d6-121">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="f48d6-122">當您使用專案設定 MRTK V2 或如上所述設定專案之後，標準 Unity 遊戲物件 (例如相機) 會針對**坐姿體驗**立即亮起，並且隨著使用者移動頭部自動更新相機的位置。</span><span class="sxs-lookup"><span data-stu-id="f48d6-122">Once you've setup MRTK V2 with your project or configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="f48d6-123">新增 Windows Mixed Reality 功能的支援，例如[空間階段](coordinate-systems.md#spatial-coordinate-systems)、[手勢、運動控制器](gestures-and-motion-controllers-in-unity.md)或[語音輸入](voice-input-in-unity.md)，是使用直接內建於 Unity 中的 API 來達成。</span><span class="sxs-lookup"><span data-stu-id="f48d6-123">Adding support for Windows Mixed Reality features, such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="f48d6-124">首先，請檢閱您的應用程式可設為目標的[體驗調整](coordinate-systems.md)：</span><span class="sxs-lookup"><span data-stu-id="f48d6-124">First, review the [experience scales](coordinate-systems.md) that your application can target:</span></span>
* <span data-ttu-id="f48d6-125">如果您想要建置**僅限定向**或**坐姿體驗**，您必須將 Unity 的追蹤空間類型設定為[固定](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="f48d6-125">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="f48d6-126">如果您想要建置**站姿**或**房間規模體驗**，您必須確定 Unity 的追蹤空間類型已成功設定為 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="f48d6-126">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="f48d6-127">如果您想要在 HoloLens 上建置**全球規模**體驗，讓使用者漫遊超過 5 公尺，您必須使用 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 元件。</span><span class="sxs-lookup"><span data-stu-id="f48d6-127">If you're looking to build a **world-scale** experience on HoloLens that lets users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="f48d6-128">混合實境應用程式的所有核心建置組塊都會以與其他 Unity API 一致的方式公開。</span><span class="sxs-lookup"><span data-stu-id="f48d6-128">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="f48d6-129">也可以透過混合實境工具組來取得。</span><span class="sxs-lookup"><span data-stu-id="f48d6-129">They are also available through the Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="f48d6-130">相機</span><span class="sxs-lookup"><span data-stu-id="f48d6-130">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="f48d6-131">座標系統</span><span class="sxs-lookup"><span data-stu-id="f48d6-131">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="f48d6-132">目光</span><span class="sxs-lookup"><span data-stu-id="f48d6-132">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="f48d6-133">手勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="f48d6-133">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="f48d6-134">語音輸入</span><span class="sxs-lookup"><span data-stu-id="f48d6-134">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="f48d6-135">持續性</span><span class="sxs-lookup"><span data-stu-id="f48d6-135">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="f48d6-136">空間音效</span><span class="sxs-lookup"><span data-stu-id="f48d6-136">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="f48d6-137">空間對應</span><span class="sxs-lookup"><span data-stu-id="f48d6-137">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="f48d6-138">還有許多混合實境應用程式想要使用的其他重要功能，也會公開至 Unity 應用程式：</span><span class="sxs-lookup"><span data-stu-id="f48d6-138">There are other key features that many mixed reality applications will want to use that are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="f48d6-139">共用體驗</span><span class="sxs-lookup"><span data-stu-id="f48d6-139">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="f48d6-140">定位相機</span><span class="sxs-lookup"><span data-stu-id="f48d6-140">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="f48d6-141">對焦點</span><span class="sxs-lookup"><span data-stu-id="f48d6-141">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="f48d6-142">追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="f48d6-142">Tracking loss</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="f48d6-143">鍵盤</span><span class="sxs-lookup"><span data-stu-id="f48d6-143">Keyboard</span></span>](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="f48d6-144">在真實或模擬裝置上執行 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="f48d6-144">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="f48d6-145">當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是[匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="f48d6-145">Once you've got your holographic Unity project ready for testing, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="f48d6-146">有了該 VS 解決方案，您就可以使用真實或模擬裝置，以三種方式的其中一種來執行應用程式：</span><span class="sxs-lookup"><span data-stu-id="f48d6-146">With that VS solution in hand, you can then run your application in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="f48d6-147">部署到真實 HoloLens 或 Windows Mixed Reality 沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="f48d6-147">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="f48d6-148">部署到 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="f48d6-148">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="f48d6-149">部署到 Windows Mixed Reality 沉浸式頭戴裝置模擬器</span><span class="sxs-lookup"><span data-stu-id="f48d6-149">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="f48d6-150">Unity 文件</span><span class="sxs-lookup"><span data-stu-id="f48d6-150">Unity documentation</span></span>

<span data-ttu-id="f48d6-151">除了可以在 docs.microsoft.com 上取得的本文件之外，Unity 還會隨著 Unity 編輯器一起安裝 Windows Mixed Reality 功能的文件。</span><span class="sxs-lookup"><span data-stu-id="f48d6-151">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="f48d6-152">Unity 提供的文件包含兩個不同的區段：</span><span class="sxs-lookup"><span data-stu-id="f48d6-152">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="f48d6-153">**Unity 指令碼參考**</span><span class="sxs-lookup"><span data-stu-id="f48d6-153">**Unity scripting reference**</span></span>
    * <span data-ttu-id="f48d6-154">文件中的此區段包含 Unity 所提供 API 指令碼的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f48d6-154">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="f48d6-155">透過 [說明 > 指令碼參考]  ，可以從 Unity 編輯器存取</span><span class="sxs-lookup"><span data-stu-id="f48d6-155">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="f48d6-156">**Unity 手冊**</span><span class="sxs-lookup"><span data-stu-id="f48d6-156">**Unity manual**</span></span>
    * <span data-ttu-id="f48d6-157">本手冊的設計目的是協助您了解如何從基本到進階技術來使用 Unity。</span><span class="sxs-lookup"><span data-stu-id="f48d6-157">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="f48d6-158">透過 [說明 > 手冊]  ，可以從 Unity 編輯器存取</span><span class="sxs-lookup"><span data-stu-id="f48d6-158">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="f48d6-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f48d6-159">See also</span></span>
* [<span data-ttu-id="f48d6-160">混合實境工具組 v2</span><span class="sxs-lookup"><span data-stu-id="f48d6-160">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="f48d6-161">MR Basics 100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="f48d6-161">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="f48d6-162">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="f48d6-162">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="f48d6-163">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="f48d6-163">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="f48d6-164">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="f48d6-164">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="f48d6-165">搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式</span><span class="sxs-lookup"><span data-stu-id="f48d6-165">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="f48d6-166">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="f48d6-166">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="f48d6-167">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="f48d6-167">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="f48d6-168">移植指南</span><span class="sxs-lookup"><span data-stu-id="f48d6-168">Porting guides</span></span>](porting-guides.md)
