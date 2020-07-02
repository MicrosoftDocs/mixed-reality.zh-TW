---
title: Unreal 開發概觀
description: 使用 Unreal Engine 4 的混合實境開發概觀
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 串流, 遠端, 混合實境, 開發, 開始使用, 功能, 新專案, 模擬器, 文件, 指南, 功能, 全像投影, 遊戲開發
ms.openlocfilehash: 0e3f40c7aa05a9c5f93d7eb9dc9793b6daeb8b90
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720364"
---
# <a name="unreal-development-overview"></a>Unreal 開發概觀

開始使用 <a href="https://docs.microsoft.com/en-us/windows/mixed-reality" target="_blank" title="Mixed Reality Docs"> 混合實境應用程式</a>是一項大型工作。 新的概念、平台和尖端硬體看起來可能像是障礙。 不過，如果您是 Unreal 開發人員，很幸運。 在 Unreal Engine 的最新 <a href="https://docs.unrealengine.com/en-US/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 版本資訊">版本</a>中，現在引進了 <a href="https://www.microsoft.com/en-us/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality Docs">Windows Mixed Reality</a> (VR) 和 <a href="https://www.microsoft.com/en-us/hololens/hardware" target="_blank" title="HoloLens 2 Docs">HoloLens 2</a> (AR) 的支援。 此更新包括：
* 混合實境 UX 工具外掛程式支援
* OpenXR 支援
* 從傳統型應用程式進行的應用程式遠端處理
* 更好的效能
* 混合實境擷取
* Azure Spatial Anchors 的初始支援

如果您不熟悉 Unreal 開發，請不要盲目跳入。 探索 Unreal <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">教學課程系列</a>，以快速了解並尋找 Unreal <a href="https://www.unrealengine.com/marketplace//store" target="_blank">市集</a>和混合實境<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">論壇</a>中的資產和支援。 這些資源可將您連結至今日混合實境市集中建置者和問題解決者的社群。

## <a name="mixed-reality-toolkit-for-unreal"></a>適用於 Unreal 的混合實境工具組

[適用於 Unreal 的混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unreal)是為了加速您在 Unreal 中進行開發而設計的一組元件。 每個元件都包含用於設定沉浸式體驗的外掛程式、範例和文件。 

[適用於 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)是第一個要發行的元件，目前僅在 HoloLens 2 上提供支援。 元件外掛程式包括常用 UX 功能的程式碼、藍圖和範例資產，包括：
* 輸入模擬
* 手部互動動作項目
* 可點按的按鈕元件
* 操作工具元件
* 追蹤行為元件

您可以深入了解[適用於 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal) GitHub 存放庫，以取得功能詳細資料和設定專案的相關資訊。

## <a name="additional-files"></a>其他檔案
如果這是您第一次建立或部署適用於 HoloLens 的 Unreal 應用程式，則需從 Epic Launcher [下載支援的檔案](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app)。

## <a name="tutorial"></a>教學課程

使用您的雙手建置東西，是學習新技能的最佳方法。 了解如何使用 UX 工具外掛程式，為 HoloLens 2 [建置和部署簡單的國際象棋應用程式](unreal-uxt-ch1.md)，是很好的起點。 

端對端教學課程系列提供與常見互動式 UX 元件和案例的實際操作聯繫。 您將逐步完成專案設定、新增場景的互動，以及部署至裝置或模擬器。 您只需要 Windows 10、模擬器和 Visual Studio 2019。


## <a name="performance"></a>效能

針對混合實境進行開發時，隨附依賴平台的效能檢查點。 HoloLens 2 應用程式必須以每秒 60 格執行，才能讓全像投影穩定顯示並且看起來有回應。 幸好，Unreal 提供[效能建議](performance-recommendations-for-unreal.md)，以在您的應用程式中實現此目的。

## <a name="guides-to-specific-features"></a>特定功能的指南

混合實境開發有幾個重要功能不在我們的教學課程系列討論範圍內。 參閱下列指南以取得詳細資料和實用應用程式： 
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
