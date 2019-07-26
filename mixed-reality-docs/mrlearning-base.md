---
title: MR 學習基底模組簡介
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: baf99fa313e3ab38f138078334fb1388a148d6da
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485609"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="fd2e1-104">1.總覽和目標</span><span class="sxs-lookup"><span data-stu-id="fd2e1-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="fd2e1-105">裝置支援</span><span class="sxs-lookup"><span data-stu-id="fd2e1-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fd2e1-106"><strong>粗</strong></span><span class="sxs-lookup"><span data-stu-id="fd2e1-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="fd2e1-107"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="fd2e1-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="fd2e1-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="fd2e1-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="fd2e1-109"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="fd2e1-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="fd2e1-110">❌</span><span class="sxs-lookup"><span data-stu-id="fd2e1-110">❌</span></span></td>
        <td><span data-ttu-id="fd2e1-111">✔️</span><span class="sxs-lookup"><span data-stu-id="fd2e1-111">✔️</span></span></td>
        <td><span data-ttu-id="fd2e1-112">❌</span><span class="sxs-lookup"><span data-stu-id="fd2e1-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="fd2e1-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="fd2e1-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="fd2e1-114">先決條件</span><span class="sxs-lookup"><span data-stu-id="fd2e1-114">Prerequisites</span></span>

* <span data-ttu-id="fd2e1-115">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦</span><span class="sxs-lookup"><span data-stu-id="fd2e1-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="fd2e1-116">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="fd2e1-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="fd2e1-117">一些基本C#的程式設計能力。</span><span class="sxs-lookup"><span data-stu-id="fd2e1-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="fd2e1-118">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置。</span><span class="sxs-lookup"><span data-stu-id="fd2e1-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

[<span data-ttu-id="fd2e1-119">下一課:2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="fd2e1-119">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
