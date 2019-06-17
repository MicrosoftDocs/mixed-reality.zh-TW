---
title: MR 學習基底模組簡介
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: d4220527a7de8e596f2825fd9d199d536510b972
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148630"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="b0edb-104">MR 學習基底模組概觀與目標</span><span class="sxs-lookup"><span data-stu-id="b0edb-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="b0edb-105">裝置支援</span><span class="sxs-lookup"><span data-stu-id="b0edb-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b0edb-106"><strong>課程</strong></span><span class="sxs-lookup"><span data-stu-id="b0edb-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="b0edb-107"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b0edb-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b0edb-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="b0edb-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="b0edb-109"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b0edb-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="b0edb-110">❌</span><span class="sxs-lookup"><span data-stu-id="b0edb-110">❌</span></span></td>
        <td><span data-ttu-id="b0edb-111">✔️</span><span class="sxs-lookup"><span data-stu-id="b0edb-111">✔️</span></span></td>
        <td><span data-ttu-id="b0edb-112">❌</span><span class="sxs-lookup"><span data-stu-id="b0edb-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="b0edb-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="b0edb-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b0edb-114">先決條件</span><span class="sxs-lookup"><span data-stu-id="b0edb-114">Prerequisites</span></span>

* <span data-ttu-id="b0edb-115">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="b0edb-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="b0edb-116">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="b0edb-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="b0edb-117">基本C#程式設計的能力。</span><span class="sxs-lookup"><span data-stu-id="b0edb-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="b0edb-118">HoloLens 2 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="b0edb-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
