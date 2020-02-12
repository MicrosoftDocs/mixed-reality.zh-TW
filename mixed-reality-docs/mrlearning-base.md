---
title: 快速入門教學課程-1。 總覽和目標
description: 本課程說明如何在混合現實應用程式中執行 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: dbae7545edb6515b5cf148fbbfb6652595d2fc0d
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129259"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="9fa23-105">1. 總覽和目標</span><span class="sxs-lookup"><span data-stu-id="9fa23-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="9fa23-106">裝置支援</span><span class="sxs-lookup"><span data-stu-id="9fa23-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9fa23-107"><strong>粗</strong></span><span class="sxs-lookup"><span data-stu-id="9fa23-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="9fa23-108"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="9fa23-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="9fa23-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="9fa23-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="9fa23-110"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9fa23-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="9fa23-111">✔️</span><span class="sxs-lookup"><span data-stu-id="9fa23-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9fa23-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="9fa23-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9fa23-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="9fa23-113">Prerequisites</span></span>

* <span data-ttu-id="9fa23-114">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦</span><span class="sxs-lookup"><span data-stu-id="9fa23-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="9fa23-115">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="9fa23-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9fa23-116">一些基本C#的程式設計能力</span><span class="sxs-lookup"><span data-stu-id="9fa23-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="9fa23-117">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="9fa23-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="9fa23-118">已安裝 Unity 2019.2. X 的<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中樞</a>，並已新增通用 Windows 平臺組建支援模組</span><span class="sxs-lookup"><span data-stu-id="9fa23-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9fa23-119">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="9fa23-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="9fa23-120">這會取代上述所連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="9fa23-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="9fa23-121">下一課： 2. 初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="9fa23-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
