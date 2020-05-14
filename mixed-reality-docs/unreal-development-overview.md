---
title: Unreal 開發概觀
description: 使用 Unreal Engine 4 的混合實境開發概觀
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 串流, 遠端, 混合實境, 開發, 開始使用, 功能, 新專案, 模擬器, 文件, 指南, 功能, 全像投影
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851562"
---
# <a name="unreal-development-overview"></a>Unreal 開發概觀

Unreal Engine 4 現在完全支援 Windows Mixed Reality (VR) 和 HoloLens 2 (AR) 裝置的開發！ 如果您是 Unreal 開發的新手，<a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">開始使用 Unreal Engine 4</a> 是一個絕佳的探索頁面。 如果您需要資產，Unreal 具有完整的 <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>。 

在您取得 Unreal 開發的基本了解之後，請參閱下一節中的教學課程，以了解如何在 HoloLens 上建置及執行您的應用程式。 請務必造訪 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 混合實境論壇</a>，與在 Unreal 中建置混合實境應用程式的社群進行互動。 這是尋找您可能遇到問題解決方案的絕佳位置。

## <a name="tutorial"></a>教學課程

請遵循我們的端對端教學課程，以了解如何針對 HoloLens 2 [建置及部署簡單的國際象棋應用程式](unreal-uxt-ch1.md)。 本教學課程使用 UX 工具外掛程式來加速使用互動式 UX 元件 (包括按鈕和操作工具) 開發應用程式。 如需 UX 工具外掛程式的詳細資訊，請參閱下一節的 MRTK。 

## <a name="mixed-reality-toolkit-for-unreal"></a>適用於 Unreal 的混合實境工具組

[適用於 Unreal 的混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unreal)是一組元件，形式為外掛程式、範例和文件，其設計目的是加速使用 Unreal Engine 的混合實境應用程式開發。 此工具組中發行的第一個元件是[適用於 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)，這是可新增至 HoloLens 2 專案的外掛程式，為 HoloLens 2 應用程式提供 UX 功能。 您可以在各自的 GitHub 存放庫中找到混合實境工具組和適用於 Unreal 的 UX 工具的文件。 

## <a name="performance"></a>效能

HoloLens 2 應用程式必須以每秒 60 格執行，才能讓全像投影穩定顯示並且看起來有回應。 若要在您的應用程式中達到此目的，我們強烈建議您遵循我們[對 Unreal 的效能建議](performance-recommendations-for-unreal.md)。 

## <a name="guides-to-specific-features"></a>特定功能的指南

若要了解如何使用 Unreal 中的特定功能，請參閱下列指南： 
* [手勢追蹤](unreal-hand-tracking.md)
* [眼球追蹤](unreal-gaze-input.md)
* [空間對應](unreal-spatial-mapping.md)
* [空間錨點](unreal-spatial-anchors.md)
* [語音輸入](unreal-voice-input.md)
* [HoloLens 相機](unreal-hololens-camera.md)
* [QR 代碼](unreal-qr-codes.md)

## <a name="supported-features"></a>支援的功能

| HoloLens 2 功能 | 最早支援的 Unreal Engine 版本 |
| ----------- | ----------- |
| ARM64 支援 | 4.23 |
| 來自電腦的串流 | 4.23 |
| 空間對應 | 4.23 |
| 手部和關節追蹤 | 4.23 |
| 眼球追蹤 | 4.23 |
| 語音輸入 | 4.23 |
| 空間錨點 | 4.23 |
| 相機存取 | 4.23 |
| QR 代碼 | 4.23 |
| 空間音訊 | 4.23 |
| 串流的觀眾螢幕支援 | 4.24 |
| 透過串流的平面 LSR | 4.24 |
| 範例應用程式 ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 和 [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| 行動多重檢視：效能命中 60 fps | 4.25 |
| 第三相機轉譯 | 4.25 |
| 從已封裝的桌面應用程式串流 | 4.25 |
| 適用於 HoloLens 2 的 Azure Spatial Anchors 搶鮮版 (Beta) | 4.25 |
| OpenXR 支援搶鮮版 (Beta) | 4.25 |
| UX 工具支援 (0.8) | 4.25 |
| 開發人員文件和教學課程 | 4.25 |

## <a name="see-also"></a>另請參閱
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">適用於串流、部署至模擬器和裝置的 Unreal 文件</a>
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">行動裝置的 Unreal 效能指導方針</a>
