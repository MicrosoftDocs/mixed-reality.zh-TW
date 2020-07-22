---
title: 多使用者功能教學課程 - 1。 簡介
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: eff600ba6388732ab9aa200ce41494cac1dddf35
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304846"
---
# <a name="1-introduction"></a><span data-ttu-id="6d9d1-105">1.簡介</span><span class="sxs-lookup"><span data-stu-id="6d9d1-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="6d9d1-106">概觀</span><span class="sxs-lookup"><span data-stu-id="6d9d1-106">Overview</span></span>

<span data-ttu-id="6d9d1-107">歡迎使用多使用者功能教學課程！</span><span class="sxs-lookup"><span data-stu-id="6d9d1-107">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="6d9d1-108">透過本教學課程系列，您將了解使用 <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity 網路</a> (PUN) 建置多使用者體驗的基本概念。</span><span class="sxs-lookup"><span data-stu-id="6d9d1-108">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="6d9d1-109">PUN 是可讓混合實境開發人員用來建立共用體驗的眾多網路功能選項之一。</span><span class="sxs-lookup"><span data-stu-id="6d9d1-109">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="6d9d1-110">本系列的教學課程：</span><span class="sxs-lookup"><span data-stu-id="6d9d1-110">Tutorials in this series:</span></span>

* [<span data-ttu-id="6d9d1-111">設定 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="6d9d1-111">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="6d9d1-112">連線多個使用者</span><span class="sxs-lookup"><span data-stu-id="6d9d1-112">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="6d9d1-113">與多個使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="6d9d1-113">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="6d9d1-114">將 Azure Spatial Anchors 整合到共用體驗</span><span class="sxs-lookup"><span data-stu-id="6d9d1-114">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="6d9d1-115">目標</span><span class="sxs-lookup"><span data-stu-id="6d9d1-115">Objectives</span></span>

* <span data-ttu-id="6d9d1-116">了解如何建立 PUN 應用程式以及將您的 Unity 專案連線至 PUN 應用程式</span><span class="sxs-lookup"><span data-stu-id="6d9d1-116">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="6d9d1-117">了解如何在共用體驗中連線多個使用者</span><span class="sxs-lookup"><span data-stu-id="6d9d1-117">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="6d9d1-118">了解如何與其他使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="6d9d1-118">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="6d9d1-119">了解如何達到多個裝置之間的空間對齊</span><span class="sxs-lookup"><span data-stu-id="6d9d1-119">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d9d1-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="6d9d1-120">Prerequisites</span></span>

* <span data-ttu-id="6d9d1-121">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="6d9d1-121">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="6d9d1-122">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="6d9d1-122">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="6d9d1-123">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="6d9d1-123">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="6d9d1-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.3.15，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="6d9d1-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="6d9d1-125">完成[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)區段，其位於[教學課程：建立使用 Azure Spatial Anchors 的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="6d9d1-125">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="6d9d1-126">完成[使用者入門教學課程](mr-learning-base-01.md)系列或一些基本的 Unity 和 MRTK 體驗</span><span class="sxs-lookup"><span data-stu-id="6d9d1-126">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="6d9d1-127">完成 [Azure 空間錨點教學課程](mr-learning-asa-01.md)系列，或建立 Azure 空間錨點帳戶的體驗</span><span class="sxs-lookup"><span data-stu-id="6d9d1-127">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="6d9d1-128">如果想要部署至 Android 及 HoloLens</span><span class="sxs-lookup"><span data-stu-id="6d9d1-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="6d9d1-129">已啟用<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開發人員</a>和具有 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 功能</a>的 Android 裝置，可透過 USB 連接至您的 Windows 或 macOS 電腦</span><span class="sxs-lookup"><span data-stu-id="6d9d1-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="6d9d1-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.3.15，且已新增 Android 組建支援模組</span><span class="sxs-lookup"><span data-stu-id="6d9d1-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="6d9d1-131">如果想要部署至 iOS 及 HoloLens</span><span class="sxs-lookup"><span data-stu-id="6d9d1-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="6d9d1-132">已安裝最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 電腦</span><span class="sxs-lookup"><span data-stu-id="6d9d1-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="6d9d1-133"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 相容</a>的 iOS 裝置可透過 USB 連接至您的 macOS 電腦</span><span class="sxs-lookup"><span data-stu-id="6d9d1-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="6d9d1-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.3.15，且已新增 iOS 組建支援模組</span><span class="sxs-lookup"><span data-stu-id="6d9d1-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="6d9d1-135">本教學課程系列的建議混合實境工具組版本是 MRTK 2.4.0。</span><span class="sxs-lookup"><span data-stu-id="6d9d1-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="6d9d1-136">本教學課程系列的建議 Unity 版本是 Unity 2019.3.15。</span><span class="sxs-lookup"><span data-stu-id="6d9d1-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="6d9d1-137">這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求。</span><span class="sxs-lookup"><span data-stu-id="6d9d1-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="6d9d1-138">下一個教學課程：2.設定 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="6d9d1-138">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
