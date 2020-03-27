---
title: 入門教學課程 - 1。 概觀和目標
description: 此課程可讓您了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36c12d82759b8ac2ba24aa9af37a096e0faf5fb5
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082052"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="26479-105">1.概觀和目標</span><span class="sxs-lookup"><span data-stu-id="26479-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="26479-106">裝置支援</span><span class="sxs-lookup"><span data-stu-id="26479-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="26479-107"><strong>課程</strong></span><span class="sxs-lookup"><span data-stu-id="26479-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="26479-108"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="26479-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="26479-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="26479-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="26479-110"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="26479-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="26479-111">✔️</span><span class="sxs-lookup"><span data-stu-id="26479-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="26479-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="26479-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="26479-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="26479-113">Prerequisites</span></span>

* <span data-ttu-id="26479-114">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="26479-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="26479-115">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="26479-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="26479-116">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="26479-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="26479-117">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="26479-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="26479-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="26479-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26479-119">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="26479-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="26479-120">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="26479-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="26479-121">下一課：2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="26479-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
