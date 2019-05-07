---
title: Unity 開發概觀
description: 取得開始的建置混合實境應用程式，在 Unity 中。
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity，混合實境、 開發、 開始、 新的專案、 移植、 功能、 相機、 模擬、 模擬、 文件
ms.openlocfilehash: 2cdcd5e997ab7e3f6d340377464e453a8e7c025c
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64874007"
---
# <a name="unity-development-overview"></a><span data-ttu-id="5d298-104">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="5d298-104">Unity development overview</span></span>

<span data-ttu-id="5d298-105">建置的最快路徑[mixed 的 reality 應用程式](app-views.md)是具有[Unity](http://aka.ms/HoloLensUnity)。</span><span class="sxs-lookup"><span data-stu-id="5d298-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](http://aka.ms/HoloLensUnity).</span></span> <span data-ttu-id="5d298-106">我們建議您花時間來探索[Unity 教學課程](https://unity3d.com/learn/tutorials)。</span><span class="sxs-lookup"><span data-stu-id="5d298-106">We recommend you take the time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="5d298-107">如果您需要的資產，Unity 的全方位[Asset Store](https://www.assetstore.unity3d.com/)。</span><span class="sxs-lookup"><span data-stu-id="5d298-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="5d298-108">一旦您已經建立基本的了解的 Unity，您可以瀏覽[教學課程](tutorials.md)若要了解使用 Unity 的混合的實境開發的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5d298-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="5d298-109">請造訪[Unity 混合實境論壇](http://forum.unity3d.com/forums/hololens.102/)來參與社群建置 Unity 中的混合的實境應用程式的其餘部分，並尋找您可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="5d298-109">Be sure to visit the [Unity Mixed Reality forums](http://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>


<span data-ttu-id="5d298-110">若要開始建置使用 Unity 的混合的實境應用程式第一次[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5d298-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="5d298-111">新的 Unity 專案的混合的實境工具組</span><span class="sxs-lookup"><span data-stu-id="5d298-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="5d298-112">在 Unity 所開發的最簡單方式是混合實境工具組的協助。</span><span class="sxs-lookup"><span data-stu-id="5d298-112">The easiest way to develop in Unity is with the help of Mixed Reality Toolkit.</span></span> <span data-ttu-id="5d298-113">它會自動執行，協助您設定專案，並提供一組，加速開發您的混合實境功能。</span><span class="sxs-lookup"><span data-stu-id="5d298-113">It will help you setup with project automatically, and provide a set of Mixed Reality features to accelerate your development.</span></span> <span data-ttu-id="5d298-114">請查看[混合實境 Toolkit v2](mrtk-getting-started.md)來進一步了解並開始使用。</span><span class="sxs-lookup"><span data-stu-id="5d298-114">Please check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="5d298-115">移植到 Windows 混和實境現有的 Unity 應用程式</span><span class="sxs-lookup"><span data-stu-id="5d298-115">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="5d298-116">如果您有現有的 Unity 專案，您要移植到 Windows 混和實境，遵循[Unity 移植指南](porting-guides.md)開始著手。</span><span class="sxs-lookup"><span data-stu-id="5d298-116">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="5d298-117">設定新的 Unity 專案的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5d298-117">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="5d298-118">如果您想要建立新的 Unity 專案，但不匯入混合實境工具組，有較少的 Unity 設定，您必須手動變更 Windows Mixed Reality，分成兩個類別： 每個專案和每個場景。</span><span class="sxs-lookup"><span data-stu-id="5d298-118">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="5d298-119">請參閱以下的逐步解說指南[設定新 Unity 專案的 Windows Mixed Reality](Configure-Unity-Project.md)</span><span class="sxs-lookup"><span data-stu-id="5d298-119">See here for step by step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="5d298-120">新增混合的實境功能和輸入</span><span class="sxs-lookup"><span data-stu-id="5d298-120">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="5d298-121">一旦您已安裝 MRTK V2 與您的專案，或如上面所述，設定您的專案時，標準的 Unity 遊戲物件 （例如數位相機） 則受到立即的**安插擴展經驗**，具有相機的位置更新自動為使用者通過其標頭的世界。</span><span class="sxs-lookup"><span data-stu-id="5d298-121">Once you've setup MRTK V2 with your project, or configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="5d298-122">新增 Windows Mixed Reality 功能的支援，例如[空間階段](coordinate-systems.md#spatial-coordinate-systems)，[筆勢，移動控制器](gestures-and-motion-controllers-in-unity.md)或[語音輸入](voice-input-in-unity.md)透過直接內建的 ApiUnity。</span><span class="sxs-lookup"><span data-stu-id="5d298-122">Adding support for Windows Mixed Reality features such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="5d298-123">您的第一個步驟應該是檢閱[體驗標尺](coordinate-systems.md)為目標應用程式：</span><span class="sxs-lookup"><span data-stu-id="5d298-123">Your first step should be to review the [experience scales](coordinate-systems.md) that your app can target:</span></span>
* <span data-ttu-id="5d298-124">如果您想要建置**方向專用**或**插入擴充槽擴展經驗**，您將需要設定 Unity 的追蹤要空間型別[「 定態](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="5d298-124">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="5d298-125">如果您想要建置**常設級別**或**聊天室擴展經驗**，您必須確保 Unity 的追蹤空間型別已成功設定為[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="5d298-125">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="5d298-126">如果您想要建置**全球級別**體驗 HoloLens，讓使用者漫遊遠 5 公尺之外，您必須使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)元件。</span><span class="sxs-lookup"><span data-stu-id="5d298-126">If you're looking to build a **world-scale** experience on HoloLens, letting users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="5d298-127">所有的核心建置組塊，混合的實境應用程式會公開在與其他的 Unity Api 一致的方式。</span><span class="sxs-lookup"><span data-stu-id="5d298-127">All of the core building blocks for mixed reality apps are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="5d298-128">它們也可透過混合實境工具組。</span><span class="sxs-lookup"><span data-stu-id="5d298-128">They are also available through Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="5d298-129">相機</span><span class="sxs-lookup"><span data-stu-id="5d298-129">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="5d298-130">座標系統</span><span class="sxs-lookup"><span data-stu-id="5d298-130">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="5d298-131">目光</span><span class="sxs-lookup"><span data-stu-id="5d298-131">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="5d298-132">筆勢和動作控制站</span><span class="sxs-lookup"><span data-stu-id="5d298-132">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="5d298-133">語音輸入</span><span class="sxs-lookup"><span data-stu-id="5d298-133">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="5d298-134">持續性</span><span class="sxs-lookup"><span data-stu-id="5d298-134">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="5d298-135">空間音效</span><span class="sxs-lookup"><span data-stu-id="5d298-135">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="5d298-136">空間對應</span><span class="sxs-lookup"><span data-stu-id="5d298-136">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="5d298-137">有許多的混合的實境應用程式將會想使用的也會公開給 Unity 應用程式的其他重要功能：</span><span class="sxs-lookup"><span data-stu-id="5d298-137">There are other key features that many mixed reality apps will want to use, which are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="5d298-138">共用的體驗</span><span class="sxs-lookup"><span data-stu-id="5d298-138">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="5d298-139">定位相機</span><span class="sxs-lookup"><span data-stu-id="5d298-139">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="5d298-140">焦點</span><span class="sxs-lookup"><span data-stu-id="5d298-140">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="5d298-141">追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="5d298-141">Tracking loss</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="5d298-142">鍵盤</span><span class="sxs-lookup"><span data-stu-id="5d298-142">Keyboard</span></span>](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="5d298-143">真實或模擬裝置上執行您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="5d298-143">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="5d298-144">您有全像攝影版的 Unity 專案準備好測試，您下一步是要[匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="5d298-144">Once you've got your holographic Unity project ready to test out, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="5d298-145">之後，在 VS 方案，您可以再執行您的應用程式其中一種方式，使用真實或模擬的裝置：</span><span class="sxs-lookup"><span data-stu-id="5d298-145">With that VS solution in hand, you can then run your app in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="5d298-146">將部署到實際的 HoloLens 或 Windows Mixed Reality 沈浸式耳機</span><span class="sxs-lookup"><span data-stu-id="5d298-146">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="5d298-147">部署至 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="5d298-147">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="5d298-148">將部署到 Windows Mixed Reality 沈浸式耳機模擬器</span><span class="sxs-lookup"><span data-stu-id="5d298-148">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="5d298-149">Unity 文件</span><span class="sxs-lookup"><span data-stu-id="5d298-149">Unity documentation</span></span>

<span data-ttu-id="5d298-150">除了本文件中可以使用 Windows 開發人員中心上，Unity 會安裝 Windows Mixed Reality 功能與 Unity Editor 中的文件。</span><span class="sxs-lookup"><span data-stu-id="5d298-150">In addition to this documentation available on the Windows Dev Center, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="5d298-151">Unity 提供文件包含兩個不同的區段：</span><span class="sxs-lookup"><span data-stu-id="5d298-151">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="5d298-152">**Unity 指令碼參考**</span><span class="sxs-lookup"><span data-stu-id="5d298-152">**Unity scripting reference**</span></span>
    * <span data-ttu-id="5d298-153">本節的文件包含 Unity 所提供的指令碼 api 的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5d298-153">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="5d298-154">可透過從 Unity 編輯器**協助 > 指令碼參考**</span><span class="sxs-lookup"><span data-stu-id="5d298-154">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="5d298-155">**Unity manual**</span><span class="sxs-lookup"><span data-stu-id="5d298-155">**Unity manual**</span></span>
    * <span data-ttu-id="5d298-156">本手冊可協助您了解如何使用 Unity 中，從基本到進階技術。</span><span class="sxs-lookup"><span data-stu-id="5d298-156">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="5d298-157">可透過從 Unity 編輯器**協助 > 手動**</span><span class="sxs-lookup"><span data-stu-id="5d298-157">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="5d298-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d298-158">See also</span></span>
* [<span data-ttu-id="5d298-159">混合實境 Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="5d298-159">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="5d298-160">MR Basics 100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="5d298-160">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="5d298-161">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="5d298-161">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="5d298-162">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="5d298-162">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="5d298-163">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="5d298-163">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="5d298-164">搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式</span><span class="sxs-lookup"><span data-stu-id="5d298-164">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="5d298-165">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="5d298-165">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="5d298-166">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="5d298-166">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="5d298-167">移植指南</span><span class="sxs-lookup"><span data-stu-id="5d298-167">Porting guides</span></span>](porting-guides.md)
