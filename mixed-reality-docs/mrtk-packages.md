---
title: MRTK 套件
description: 這篇文章描述組成 Microsoft 混合實境 Toollkit 的封裝。
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality，MRTK 元件、 封裝
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596942"
---
# <a name="mrtk-packages"></a><span data-ttu-id="2f87c-104">MRTK 套件</span><span class="sxs-lookup"><span data-stu-id="2f87c-104">MRTK packages</span></span>

<span data-ttu-id="2f87c-105">混合實境工具組 (MRTK) 是一個提供及支援的混合實境硬體平台元件化的方式來啟用跨平台混合實境應用程式開發的封裝的集合。</span><span class="sxs-lookup"><span data-stu-id="2f87c-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms in a componentized manner.</span></span>

<span data-ttu-id="2f87c-106">有三種 MRTK 套件：</span><span class="sxs-lookup"><span data-stu-id="2f87c-106">There are three categories of MRTK packages:</span></span> 

* [<span data-ttu-id="2f87c-107">Foundation</span><span class="sxs-lookup"><span data-stu-id="2f87c-107">Foundation</span></span>](#foundation-packages)
* [<span data-ttu-id="2f87c-108">延伸模組</span><span class="sxs-lookup"><span data-stu-id="2f87c-108">Extension</span></span>](#extension-packages)
* [<span data-ttu-id="2f87c-109">Experimental</span><span class="sxs-lookup"><span data-stu-id="2f87c-109">Experimental</span></span>](#experimental-packages)

## <a name="foundation-packages"></a><span data-ttu-id="2f87c-110">Foundation 套件</span><span class="sxs-lookup"><span data-stu-id="2f87c-110">Foundation Packages</span></span>

<span data-ttu-id="2f87c-111">混合實境 Toolkit Foundation 是一組可讓您運用混合實境平台的通用功能的應用程式封裝。</span><span class="sxs-lookup"><span data-stu-id="2f87c-111">The Mixed Reality Toolkit Foundation is the set of packages that enable your application to leverage common functionality across Mixed Reality Platforms.</span></span> <span data-ttu-id="2f87c-112">這些封裝是發行和從來源中的程式碼，Microsoft 支援[mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) GitHub 上的分支。</span><span class="sxs-lookup"><span data-stu-id="2f87c-112">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

![MRTK Foundation 套件](images/mrtk-foundation.jpg)

<span data-ttu-id="2f87c-114">*混合的實境 Toolkit Foundation 套件*</span><span class="sxs-lookup"><span data-stu-id="2f87c-114">*Mixed Reality Toolkit Foundation packages*</span></span>

<span data-ttu-id="2f87c-115">MRTK Foundation 所組成：</span><span class="sxs-lookup"><span data-stu-id="2f87c-115">The MRTK Foundation is comprised of:</span></span>

* [<span data-ttu-id="2f87c-116">核心封裝</span><span class="sxs-lookup"><span data-stu-id="2f87c-116">Core Package</span></span>](#core-package)
* [<span data-ttu-id="2f87c-117">平台提供者</span><span class="sxs-lookup"><span data-stu-id="2f87c-117">Platform Providers</span></span>](#platform-providers)
* [<span data-ttu-id="2f87c-118">系統服務</span><span class="sxs-lookup"><span data-stu-id="2f87c-118">System Services</span></span>](#system-services)
* [<span data-ttu-id="2f87c-119">功能資產</span><span class="sxs-lookup"><span data-stu-id="2f87c-119">Feature Assets</span></span>](#feature-assets)

<span data-ttu-id="2f87c-120">下列各節說明每個類別目錄中的封裝類型。</span><span class="sxs-lookup"><span data-stu-id="2f87c-120">The following sections describe the types of packages in each category.</span></span>

### <a name="core-package"></a><span data-ttu-id="2f87c-121">核心封裝</span><span class="sxs-lookup"><span data-stu-id="2f87c-121">Core Package</span></span>

<span data-ttu-id="2f87c-122">是核心封裝_必要_元件和 je obsazen MRTK foundation 的所有套件作為相依性。</span><span class="sxs-lookup"><span data-stu-id="2f87c-122">The core package is a _required_ component and is taken as a dependency by all MRTK foundation packages.</span></span>

<span data-ttu-id="2f87c-123">MRTK Core 套件包括：</span><span class="sxs-lookup"><span data-stu-id="2f87c-123">The MRTK Core package includes:</span></span>

* [<span data-ttu-id="2f87c-124">常見的介面、 類別和資料類型</span><span class="sxs-lookup"><span data-stu-id="2f87c-124">Common interfaces, classes and data types</span></span>](#common-interfaces-clases-and-data-types)
* [<span data-ttu-id="2f87c-125">MixedRealityToolkit 場景元件</span><span class="sxs-lookup"><span data-stu-id="2f87c-125">MixedRealityToolkit scene component</span></span>](#mixedrealitytoolkit-scene-component)
* [<span data-ttu-id="2f87c-126">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="2f87c-126">MRTK Standard Shader</span></span>](#mrtk-standard-shader)
* [<span data-ttu-id="2f87c-127">Unity 輸入提供者</span><span class="sxs-lookup"><span data-stu-id="2f87c-127">Unity Input Provider</span></span>](#unity-input-provider)
* [<span data-ttu-id="2f87c-128">套件管理</span><span class="sxs-lookup"><span data-stu-id="2f87c-128">Package Management</span></span>](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a><span data-ttu-id="2f87c-129">常見的介面、 類別和資料類型</span><span class="sxs-lookup"><span data-stu-id="2f87c-129">Common interfaces, classes and data types</span></span>

<span data-ttu-id="2f87c-130">混合實境 Toolkit 核心套件包含所有常見的介面，類別和所有其他元件所使用的資料類型的定義。</span><span class="sxs-lookup"><span data-stu-id="2f87c-130">The Mixed Reality Toolkit Core package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="2f87c-131">強烈建議應用程式，以獨佔方式透過定義的介面，以啟用跨平台的相容性的最高層級存取 MRTK 元件。</span><span class="sxs-lookup"><span data-stu-id="2f87c-131">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

#### <a name="mixedrealitytoolkit-scene-component"></a><span data-ttu-id="2f87c-132">MixedRealityToolkit 場景元件</span><span class="sxs-lookup"><span data-stu-id="2f87c-132">MixedRealityToolkit scene component</span></span>

<span data-ttu-id="2f87c-133">MixedRealityToolkit 場景元件是單一的集中式資源管理員的混合實境工具組。</span><span class="sxs-lookup"><span data-stu-id="2f87c-133">The MixedRealityToolkit scene component is the single, centralized resource manager for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="2f87c-134">此元件會載入和管理的平台和服務模組的存留時間，並提供存取其組態設定的系統資源。</span><span class="sxs-lookup"><span data-stu-id="2f87c-134">This component loads and manages the lifespan of the platform and service modules and provides resources for the systems to access their configuration settings.</span></span> 

#### <a name="mrtk-standard-shader"></a><span data-ttu-id="2f87c-135">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="2f87c-135">MRTK Standard Shader</span></span>

<span data-ttu-id="2f87c-136">MRTK 標準著色器提供的基礎，幾乎所有 MRTK 所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="2f87c-136">The MRTK Standard Shader provides the basis for virtually all of the materials provided by the MRTK.</span></span> <span data-ttu-id="2f87c-137">這個著色器是極富彈性且最佳化的各種 MRTK 支援的平台。</span><span class="sxs-lookup"><span data-stu-id="2f87c-137">This shader is extremely flexible and optimized for the variety of platforms on which MRTK is supported.</span></span> <span data-ttu-id="2f87c-138">很_高度_建議您的應用程式資料使用 MRTK 標準著色器，以獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="2f87c-138">It is _highly_ recommended that your application's materials use the MRTK standard shader for optimal performance.</span></span>

#### <a name="unity-input-provider"></a><span data-ttu-id="2f87c-139">Unity 輸入提供者</span><span class="sxs-lookup"><span data-stu-id="2f87c-139">Unity Input Provider</span></span>

<span data-ttu-id="2f87c-140">Unity 的輸入提供者提供常見遊戲控制器、 觸控式螢幕等 3D 空間滑鼠的輸入裝置的存取權。</span><span class="sxs-lookup"><span data-stu-id="2f87c-140">The Unity Input Provider provides access to common input devices such as game controllers, touch screens and a 3D spatial mouse.</span></span>

#### <a name="package-management"></a><span data-ttu-id="2f87c-141">套件管理</span><span class="sxs-lookup"><span data-stu-id="2f87c-141">Package Management</span></span>

<span data-ttu-id="2f87c-142">_即將推出_</span><span class="sxs-lookup"><span data-stu-id="2f87c-142">_Coming soon_</span></span>

<span data-ttu-id="2f87c-143">混合實境 Toolkit 核心封裝可讓您探索及管理的選擇性的 foundation、 延伸模組和實驗性 MRTK 封裝。</span><span class="sxs-lookup"><span data-stu-id="2f87c-143">The Mixed Reality Toolkit Core package provides support for discovering and managing the optional foundation, extension and experimental MRTK packages.</span></span>

### <a name="platform-providers"></a><span data-ttu-id="2f87c-144">平台提供者</span><span class="sxs-lookup"><span data-stu-id="2f87c-144">Platform Providers</span></span>

<span data-ttu-id="2f87c-145">MRTK 平台提供者套件會啟用目標混合實境硬體混合實境工具及平台功能的元件。</span><span class="sxs-lookup"><span data-stu-id="2f87c-145">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="2f87c-146">支援的平台包括：</span><span class="sxs-lookup"><span data-stu-id="2f87c-146">Supported platforms include:</span></span>

* [<span data-ttu-id="2f87c-147">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2f87c-147">Windows Mixed Reality</span></span>](#windows-mixed-reality)
* [<span data-ttu-id="2f87c-148">OpenVR</span><span class="sxs-lookup"><span data-stu-id="2f87c-148">OpenVR</span></span>](#openvr)
* [<span data-ttu-id="2f87c-149">Windows Voice</span><span class="sxs-lookup"><span data-stu-id="2f87c-149">Windows Voice</span></span>](#windows-voice)

#### <a name="windows-mixed-reality"></a><span data-ttu-id="2f87c-150">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2f87c-150">Windows Mixed Reality</span></span>

<span data-ttu-id="2f87c-151">Windows Mixed Reality 封裝提供適用於 Microsoft HoloLens 和 Windows Mixed Reality 沈浸式裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="2f87c-151">The Windows Mixed Reality package provides support for Microsoft HoloLens and Windows Mixed Reality Immersive devices.</span></span> <span data-ttu-id="2f87c-152">封裝包含完整的平台支援，包括：</span><span class="sxs-lookup"><span data-stu-id="2f87c-152">The package contains full platform support, including:</span></span>

* <span data-ttu-id="2f87c-153">為目標的視線</span><span class="sxs-lookup"><span data-stu-id="2f87c-153">Gaze targeting</span></span>
* <span data-ttu-id="2f87c-154">手勢</span><span class="sxs-lookup"><span data-stu-id="2f87c-154">Gestures</span></span>
* <span data-ttu-id="2f87c-155">Windows Mixed Reality 動作控制站</span><span class="sxs-lookup"><span data-stu-id="2f87c-155">Windows Mixed Reality Motion controllers</span></span>
* <span data-ttu-id="2f87c-156">空間對應</span><span class="sxs-lookup"><span data-stu-id="2f87c-156">Spatial Mapping</span></span>

#### <a name="openvr"></a><span data-ttu-id="2f87c-157">OpenVR</span><span class="sxs-lookup"><span data-stu-id="2f87c-157">OpenVR</span></span>

<span data-ttu-id="2f87c-158">OpenVR 套件提供的硬體和平台支援使用 OpenVR 平台的裝置。</span><span class="sxs-lookup"><span data-stu-id="2f87c-158">The OpenVR package provides hardware and platform support for devices using the OpenVR platform.</span></span>

#### <a name="windows-voice"></a><span data-ttu-id="2f87c-159">Windows 語音</span><span class="sxs-lookup"><span data-stu-id="2f87c-159">Windows Voice</span></span>

<span data-ttu-id="2f87c-160">Windows 語音套件會提供 Microsoft Windows 10 裝置上的關鍵字辨識和語音輸入功能的支援。</span><span class="sxs-lookup"><span data-stu-id="2f87c-160">The Windows Voice package provides support for keyword recognition and dictation functionality on Microsoft Windows 10 devices.</span></span>

### <a name="system-services"></a><span data-ttu-id="2f87c-161">系統服務</span><span class="sxs-lookup"><span data-stu-id="2f87c-161">System Services</span></span>

<span data-ttu-id="2f87c-162">核心平台服務提供系統服務封裝中。</span><span class="sxs-lookup"><span data-stu-id="2f87c-162">Core platform services are provided in system service packages.</span></span> <span data-ttu-id="2f87c-163">這些套件包含混合實境工具組的預設實作中定義的系統服務介面[core](#core-package)封裝。</span><span class="sxs-lookup"><span data-stu-id="2f87c-163">These packages contain the Mixed Reality Toolkit's default implementations of the system service interfaces, defined in the [core](#core-package) package.</span></span>

<span data-ttu-id="2f87c-164">MRTK foundation 包含下列的系統服務：</span><span class="sxs-lookup"><span data-stu-id="2f87c-164">The MRTK foundation includes the following system services:</span></span>

* [<span data-ttu-id="2f87c-165">界限系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-165">Boundary System</span></span>](#boundary-system)
* [<span data-ttu-id="2f87c-166">診斷系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-166">Diagnostic System</span></span>](#diagnostic-system)
* [<span data-ttu-id="2f87c-167">輸入的系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-167">Input System</span></span>](#input-system)
* [<span data-ttu-id="2f87c-168">空間感知系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-168">Spatial Awareness System</span></span>](#spatial-awareness-system)
* [<span data-ttu-id="2f87c-169">空間傳送系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-169">Teleport System</span></span>](#teleport-system)

#### <a name="boundary-system"></a><span data-ttu-id="2f87c-170">界限系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-170">Boundary System</span></span>

<span data-ttu-id="2f87c-171">MRTK 界限系統提供資料至虛擬實境 playspace。</span><span class="sxs-lookup"><span data-stu-id="2f87c-171">The MRTK Boundary System provides data about the to virtual reality playspace.</span></span> <span data-ttu-id="2f87c-172">在系統上的使用者已設定的界限，floor 平面、 矩形 playspace、 追蹤的區域中，和更多功能，可以提供系統。</span><span class="sxs-lookup"><span data-stu-id="2f87c-172">On systems for which the user has configured the boundary, the system can provide a floor plane, rectangular playspace, tracked area, and more.</span></span>

#### <a name="diagnostic-system"></a><span data-ttu-id="2f87c-173">診斷系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-173">Diagnostic System</span></span>

<span data-ttu-id="2f87c-174">MRTK 診斷系統會提供可在您的應用程式體驗的即時效能資料。</span><span class="sxs-lookup"><span data-stu-id="2f87c-174">The MRTK Diagnostic System provides real-time performance data within your application experience.</span></span> <span data-ttu-id="2f87c-175">在瀏覽，您可以檢視畫面播放速率、 處理器時間和其他關鍵效能計量，當您使用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f87c-175">At a glace, you will be able to view frame rate, processor time and other key performance metrics as you use your application.</span></span>

#### <a name="input-system"></a><span data-ttu-id="2f87c-176">輸入的系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-176">Input System</span></span>

<span data-ttu-id="2f87c-177">MRTK 輸入系統可讓應用程式存取跨平台的方式輸入指定使用者的動作，並將這些動作指派給最適當的按鈕和目標的控制站上的軸。</span><span class="sxs-lookup"><span data-stu-id="2f87c-177">The MRTK Input Systems enables applications to access input in a cross platform manner by specifying user actions and assigning those actions to the most appropriate buttons and axes on target controllers.</span></span>

#### <a name="spatial-awareness-system"></a><span data-ttu-id="2f87c-178">空間感知系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-178">Spatial Awareness System</span></span>

<span data-ttu-id="2f87c-179">MRTK 空間感知系統可從裝置，例如 Microsoft HoloLens 讓真實世界的環境資料的存取。</span><span class="sxs-lookup"><span data-stu-id="2f87c-179">The MRTK Spatial Awareness System enables access to real-world environmental data from devices such as the Microsoft HoloLens.</span></span>

#### <a name="teleport-system"></a><span data-ttu-id="2f87c-180">空間傳送系統</span><span class="sxs-lookup"><span data-stu-id="2f87c-180">Teleport System</span></span>

<span data-ttu-id="2f87c-181">MRTK 空間傳送系統提供的虛擬實境 locomotion 支援。</span><span class="sxs-lookup"><span data-stu-id="2f87c-181">The MRTK Teleport System provides virtual reality locomotion support.</span></span>

### <a name="feature-assets"></a><span data-ttu-id="2f87c-182">功能資產</span><span class="sxs-lookup"><span data-stu-id="2f87c-182">Feature Assets</span></span>

<span data-ttu-id="2f87c-183">功能資產是以 Unity 資產和指令碼的形式提供的相關功能的集合。</span><span class="sxs-lookup"><span data-stu-id="2f87c-183">Feature Assets are collections of related functionality delivered as Unity assets and scripts.</span></span> <span data-ttu-id="2f87c-184">這些功能包括：</span><span class="sxs-lookup"><span data-stu-id="2f87c-184">Some of these features include:</span></span>

* <span data-ttu-id="2f87c-185">使用者介面控制項</span><span class="sxs-lookup"><span data-stu-id="2f87c-185">User Interface Controls</span></span>
* <span data-ttu-id="2f87c-186">標準資產</span><span class="sxs-lookup"><span data-stu-id="2f87c-186">Standard Assets</span></span>
* <span data-ttu-id="2f87c-187">more</span><span class="sxs-lookup"><span data-stu-id="2f87c-187">more</span></span>

## <a name="extension-packages"></a><span data-ttu-id="2f87c-188">延伸模組套件</span><span class="sxs-lookup"><span data-stu-id="2f87c-188">Extension Packages</span></span>

<span data-ttu-id="2f87c-189">MRTK 延伸模組套件是一個 Microsoft 和社群所撰寫，擴充及增強功能的混合實境工具組封裝的集合。</span><span class="sxs-lookup"><span data-stu-id="2f87c-189">MRTK Extension packages are a collection of packages written by Microsoft and the Community that extend and enhance the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="2f87c-190">延伸模組作者將任何必要的相依性的狀態、 標示為相容於混合實境工具組封裝和提供授權和支援陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f87c-190">Extension authors will state any required dependencies, mark the package as compatible with the Mixed Reality Toolkit and provide licensing and support statements.</span></span>

<span data-ttu-id="2f87c-191">延伸模組套件可能會提供新功能和新的平台支援。</span><span class="sxs-lookup"><span data-stu-id="2f87c-191">Extension packages may provide new features and new platform support.</span></span> <span data-ttu-id="2f87c-192">經過一段時間，擴充功能，協助與核准的作者，被移轉至 MRTK Foundation，屆時它們會發行並由 Microsoft 支援。</span><span class="sxs-lookup"><span data-stu-id="2f87c-192">Over time, extensions may, with the assistance and approval of the authors, be migrated into the MRTK Foundation at which time they will be released and supported by Microsoft.</span></span>

![MRTK 延伸模組套件](images/mrtk-extensions.jpg)

<span data-ttu-id="2f87c-194">*混合的實境 Toolkit 擴充功能封裝*</span><span class="sxs-lookup"><span data-stu-id="2f87c-194">*Mixed Reality Toolkit Extension packages*</span></span>

## <a name="experimental-packages"></a><span data-ttu-id="2f87c-195">實驗性的套件</span><span class="sxs-lookup"><span data-stu-id="2f87c-195">Experimental Packages</span></span>

<span data-ttu-id="2f87c-196">實驗性的封裝提供航班原型功能、 發行前版本和令人興奮的新想法的能力。</span><span class="sxs-lookup"><span data-stu-id="2f87c-196">Experimental packages provide the ability to flight prototype features, pre-releases and exciting new ideas.</span></span> <span data-ttu-id="2f87c-197">最實驗性套件的目標是要嘗試新的項目，並量測計的客戶感興趣。</span><span class="sxs-lookup"><span data-stu-id="2f87c-197">The goal of most experimental packages is to try something new and to gauge customer interest.</span></span> <span data-ttu-id="2f87c-198">許多，原型設計和測試階段完成後，實驗性的套件雖然不是全部，會重新發行為擴充功能。</span><span class="sxs-lookup"><span data-stu-id="2f87c-198">Many, though not all, experimental packages will be re-released as extensions once the prototyping and testing phase completes.</span></span>

![MRTK 實驗性套件](images/mrtk-experimental.jpg)

<span data-ttu-id="2f87c-200">*混合的實境工具組實驗性的套件*</span><span class="sxs-lookup"><span data-stu-id="2f87c-200">*Mixed Reality Toolkit Experimental packages*</span></span>

## <a name="conclusion"></a><span data-ttu-id="2f87c-201">結論</span><span class="sxs-lookup"><span data-stu-id="2f87c-201">Conclusion</span></span>

<span data-ttu-id="2f87c-202">混合實境工具組封裝和封裝管理系統的設計可讓您火到您的經驗建置功能，而不需要不必要的元件加入至專案的簡單方法。</span><span class="sxs-lookup"><span data-stu-id="2f87c-202">The Mixed Reality Toolkit packages and package management system are designed to enable a clean and simple method for you to additively build features into your experiences without requiring unnecessary components to be included into the project.</span></span>

<span data-ttu-id="2f87c-203">經過一段時間，會新增並增強在混合實境 Toolkit 中套件管理支援。</span><span class="sxs-lookup"><span data-stu-id="2f87c-203">Over time, package management support will be added and enhanced within the Mixed Reality Toolkit.</span></span> <span data-ttu-id="2f87c-204">如果您有意見反應，或想要參與，請瀏覽[混合實境 Toolkit 專案](https://github.com/Microsoft/MixedRealityToolkit-Unity)GitHub 上。</span><span class="sxs-lookup"><span data-stu-id="2f87c-204">If you have feedback or wish to get involved, please visit the [Mixed Reality Toolkit project](https://github.com/Microsoft/MixedRealityToolkit-Unity) on GitHub.</span></span> 

## <a name="see-also"></a><span data-ttu-id="2f87c-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f87c-205">See also</span></span>

* [<span data-ttu-id="2f87c-206">MixedRealityToolkit-Unity (GitHub)</span><span class="sxs-lookup"><span data-stu-id="2f87c-206">MixedRealityToolkit-Unity (GitHub)</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

