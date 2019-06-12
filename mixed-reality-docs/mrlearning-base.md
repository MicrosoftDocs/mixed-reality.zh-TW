---
title: MR 學習基底模組簡介
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: 2fe07efe87086e9a8c06e1953fcef8544b03c80a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829880"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="3215d-104">MR 學習基底模組概觀與目標</span><span class="sxs-lookup"><span data-stu-id="3215d-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="3215d-105">裝置支援</span><span class="sxs-lookup"><span data-stu-id="3215d-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3215d-106"><strong>課程</strong></span><span class="sxs-lookup"><span data-stu-id="3215d-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="3215d-107"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="3215d-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3215d-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="3215d-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="3215d-109"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></span><span class="sxs-lookup"><span data-stu-id="3215d-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="3215d-110">❌</span><span class="sxs-lookup"><span data-stu-id="3215d-110">❌</span></span></td>
        <td><span data-ttu-id="3215d-111">✔️</span><span class="sxs-lookup"><span data-stu-id="3215d-111">✔️</span></span></td>
        <td><span data-ttu-id="3215d-112">❌</span><span class="sxs-lookup"><span data-stu-id="3215d-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="3215d-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="3215d-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3215d-114">先決條件</span><span class="sxs-lookup"><span data-stu-id="3215d-114">Prerequisites</span></span>

* <span data-ttu-id="3215d-115">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="3215d-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="3215d-116">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="3215d-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="3215d-117">基本C#程式設計的能力。</span><span class="sxs-lookup"><span data-stu-id="3215d-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="3215d-118">HoloLens 2 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="3215d-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
