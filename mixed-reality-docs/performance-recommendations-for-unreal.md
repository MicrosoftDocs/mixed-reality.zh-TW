---
title: Unreal 的效能建議
description: 在 Unreal 中使用混合實境應用程式的最佳效能建議
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 效能, 最佳化, 設定, 文件
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840197"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="ca8d7-104">Unreal 的效能建議</span><span class="sxs-lookup"><span data-stu-id="ca8d7-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="ca8d7-105">本文是以[混合實境效能建議](understanding-performance-for-mixed-reality.md)中所述的討論為基礎，但著重於 Unreal Engine 環境的特定學習。</span><span class="sxs-lookup"><span data-stu-id="ca8d7-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unreal Engine environment.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="ca8d7-106">建議的 Unreal 專案設定</span><span class="sxs-lookup"><span data-stu-id="ca8d7-106">Recommended Unreal project settings</span></span>

- <span data-ttu-id="ca8d7-107">使用行動 VR 轉譯器 - 在您的專案設定中，確定您的目標平台已在 [專案 – 目標硬體] 底下設定為 [行動裝置/平板電腦]</span><span class="sxs-lookup"><span data-stu-id="ca8d7-107">Use the mobile VR renderer- in your project settings, ensure your target platform is set to "Mobile/Tablet" under "Project – Target Hardware"</span></span>
- <span data-ttu-id="ca8d7-108">停用遮蔽剔除 - 在 [引擎 – 呈現] 底下的 [剔除] 區段中，取消核取 [遮蔽剔除]</span><span class="sxs-lookup"><span data-stu-id="ca8d7-108">Disable occlusion culling- under "Engine – Rendering" in the "Culling" section, uncheck "Occlusion Culling"</span></span>
    + <span data-ttu-id="ca8d7-109">如果需要遮蔽剔除 (因為必須呈現非常詳細的場景)，建議您在 [引擎 – 呈現] 下啟用 [支援軟體遮蔽剔除]。</span><span class="sxs-lookup"><span data-stu-id="ca8d7-109">If occlusion culling is required because a very detailed scene needs to be rendered, it is recommended that "Support Software Occlusion Culling" is enabled Under "Engine – Rendering".</span></span> <span data-ttu-id="ca8d7-110">這可讓 Unreal 在 CPU 上進行遮蔽剔除，並避免 GPU 的遮蔽查詢 (此功能在 HoloLens 2 上的執行效能不佳)。</span><span class="sxs-lookup"><span data-stu-id="ca8d7-110">This allows Unreal to do occlusion culling on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
- <span data-ttu-id="ca8d7-111">在 [VR] 類別中的 [引擎 – 呈現] 底下，啟用 [實例化立體呈現 (Instanced Stereo)] 和 [行動多視角 (Mobile Multi-View)]。</span><span class="sxs-lookup"><span data-stu-id="ca8d7-111">Enable both "Instanced Stereo" and "Mobile Multi-View" under "Engine – Rendering" in the "VR" category.</span></span> <span data-ttu-id="ca8d7-112">您可能需要取消核取 [行動後置處理 (Mobile Post-Processing)]，才能夠勾選 [行動多視角]</span><span class="sxs-lookup"><span data-stu-id="ca8d7-112">You may need to uncheck "Mobile Post-Processing" in order to be able to check "Mobile Multi-View"</span></span>
