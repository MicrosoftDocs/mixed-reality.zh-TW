---
title: Unreal 的效能建議
description: 在 Unreal 中使用混合實境應用程式的最佳效能建議
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 效能, 最佳化, 設定, 文件
ms.openlocfilehash: a7972962eeb2b1480a7da38210b5ee77104f508b
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303631"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="2bf20-104">Unreal 的效能建議</span><span class="sxs-lookup"><span data-stu-id="2bf20-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="2bf20-105">概觀</span><span class="sxs-lookup"><span data-stu-id="2bf20-105">Overview</span></span>

<span data-ttu-id="2bf20-106">本文是以[混合實境效能建議](understanding-performance-for-mixed-reality.md)中所述的討論為基礎，但著重於 Unreal Engine 特有的功能。</span><span class="sxs-lookup"><span data-stu-id="2bf20-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="2bf20-107">建議您先閱讀應用程式瓶頸、分析和剖析混合實境應用程式，並進行一般效能修正，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="2bf20-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="2bf20-108">建議的 Unreal 專案設定</span><span class="sxs-lookup"><span data-stu-id="2bf20-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="2bf20-109">您可以在 [編輯] > [專案設定] 中找到下列每個設定。</span><span class="sxs-lookup"><span data-stu-id="2bf20-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="2bf20-110">使用行動 VR 轉譯器：</span><span class="sxs-lookup"><span data-stu-id="2bf20-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="2bf20-111">向下捲動至 [專案] 區段、選取 [目標硬體]，然後將目標平台設定為 [行動裝置/平板電腦]</span><span class="sxs-lookup"><span data-stu-id="2bf20-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![行動目標設定](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="2bf20-113">停用遮蔽消除：</span><span class="sxs-lookup"><span data-stu-id="2bf20-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="2bf20-114">向下捲動至 [引擎] 區段、選取 [轉譯]、展開 [消除] 區段，然後取消勾選 [遮蔽消除]。</span><span class="sxs-lookup"><span data-stu-id="2bf20-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="2bf20-115">如果您需要針對轉譯的詳細場景進行遮蔽消除，建議您在 [引擎] > [轉譯] 中啟用 [支援軟體遮蔽消除]。</span><span class="sxs-lookup"><span data-stu-id="2bf20-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="2bf20-116">這讓 Unreal 可在 CPU 上執行此工作，並避免 GPU 的遮蔽查詢 (此功能在 HoloLens 2 上的執行效能不佳)。</span><span class="sxs-lookup"><span data-stu-id="2bf20-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![停用遮蔽消除](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="2bf20-118">使用行動多重檢視：</span><span class="sxs-lookup"><span data-stu-id="2bf20-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="2bf20-119">向下捲動至 [引擎] 區段、選取 [轉譯]、展開 [VR] 區段，然後同時啟用 [執行個體化立體聲] 和 [行動多重檢視]。</span><span class="sxs-lookup"><span data-stu-id="2bf20-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="2bf20-120">應取消核取行動設備 HDR。</span><span class="sxs-lookup"><span data-stu-id="2bf20-120">Mobile HDR should be unchecked.</span></span>

![VR 轉譯設定](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="2bf20-122">將 [要轉譯的 CSM 串聯數目上限] 設定為 **1**，並將 [可移動的聚光燈/點狀光源數上限] 設定為 **0**。</span><span class="sxs-lookup"><span data-stu-id="2bf20-122">Setting the **Maximum number of CSM cascades to render** to **1** and **Max Movable Spotlights / Point Lights** to **0**.</span></span> 
