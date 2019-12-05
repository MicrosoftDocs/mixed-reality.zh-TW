---
title: Unity 開發概觀
description: 開始在 Unity 中建置混合實境應用程式。
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合實境, 開發, 開始使用, 新專案, 移植, 功能, 相機, 模擬, 模擬, 文件
ms.openlocfilehash: 23b3d9a3fe419911e774722a7d2db6809c2955cf
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491089"
---
# <a name="unity-development-overview"></a>Unity 開發概觀

建置[混合實境應用程式](app-views.md)的最快速路徑是透過 [Unity](https://unity.com)。 我們建議您花一些時間來探索 [Unity 教學課程](https://unity3d.com/learn/tutorials)。 如果您需要資產，Unity 具有完整的[資產存放區](https://www.assetstore.unity3d.com/)。 建立 Unity 的基本了解之後，您可以造訪[教學課程](tutorials.md)，了解使用 Unity 進行混合實境開發的細節。 請務必造訪 [Unity 混合實境論壇](https://forum.unity3d.com/forums/hololens.102/)，與在 Unity 中建置混合實境應用程式的其他人互動，並找出您所遇到問題的解決方案。

若要開始使用 Unity 建置混合實境應用程式，請先[安裝工具](install-the-tools.md)。 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>使用混合實境工具組的新 Unity 專案 

在 Unity 中開發最簡單的方式，就是使用混合實境工具組。 這個工具組可協助您自動設定專案，並提供一組混合實境功能來加速您的開發。 請查看[混合實境工具組 v2](mrtk-getting-started.md) 以深入了解並開始使用。 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>將現有的 Unity 應用程式移植到 Windows Mixed Reality

如果您有現有的 Unity 專案要移植到 Windows Mixed Reality，請遵循 [Unity 移植指南](porting-guides.md)以開始使用。

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>設定適用於 Windows Mixed Reality 的新 Unity 專案

如果您想要在未匯入混合實境工具組的情況下建立新的 Unity 專案，則您需要為 Windows Mixed Reality 手動變更一小組 Unity 設定。 這些設定分成兩個類別：每個專案和每個場景。 請參閱這裡以取得[設定適用於 Windows Mixed Reality 的新 Unity 專案](Configure-Unity-Project.md)的逐步指南

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>新增混合實境功能和輸入

當您使用專案設定 MRTK V2 或如上所述設定專案之後，標準 Unity 遊戲物件 (例如相機) 會針對**坐姿體驗**立即亮起，並且隨著使用者移動頭部自動更新相機的位置。

新增 Windows Mixed Reality 功能的支援，例如[空間階段](coordinate-systems.md#spatial-coordinate-systems)、[手勢、運動控制器](gestures-and-motion-controllers-in-unity.md)或[語音輸入](voice-input-in-unity.md)，是使用直接內建於 Unity 中的 API 來達成。 

首先，請檢閱您的應用程式可設為目標的[體驗調整](coordinate-systems.md)：
* 如果您想要建置**僅限定向**或**坐姿體驗**，您必須將 Unity 的追蹤空間類型設定為[固定](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您想要建置**站姿**或**房間規模體驗**，您必須確定 Unity 的追蹤空間類型已成功設定為 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您想要在 HoloLens 上建置**全球規模**體驗，讓使用者漫遊超過 5 公尺，您必須使用 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 元件。

混合實境應用程式的所有核心建置組塊都會以與其他 Unity API 一致的方式公開。 也可以透過混合實境工具組來取得。
* [相機](camera-in-unity.md)
* [座標系統](coordinate-systems-in-unity.md)
* [目光](gaze-in-unity.md)
* [手勢和運動控制器](gestures-and-motion-controllers-in-unity.md)
* [語音輸入](voice-input-in-unity.md)
* [持續性](persistence-in-unity.md)
* [空間音效](spatial-sound-in-unity.md)
* [空間對應](spatial-mapping-in-unity.md)

還有許多混合實境應用程式想要使用的其他重要功能，也會公開至 Unity 應用程式：
* [共用體驗](shared-experiences-in-unity.md)
* [定位相機](locatable-camera-in-unity.md)
* [對焦點](focus-point-in-unity.md)
* [追蹤遺失](tracking-loss-in-unity.md)
* [鍵盤](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>在真實或模擬裝置上執行 Unity 專案

當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是[匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)。

有了該 VS 解決方案，您就可以使用真實或模擬裝置，以三種方式的其中一種來執行應用程式：
* [部署到真實 HoloLens 或 Windows Mixed Reality 沉浸式頭戴裝置](using-visual-studio.md)
* [部署到 HoloLens 模擬器](using-the-hololens-emulator.md)
* [部署到 Windows Mixed Reality 沉浸式頭戴裝置模擬器](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 文件

除了可以在 docs.microsoft.com 上取得的本文件之外，Unity 還會隨著 Unity 編輯器一起安裝 Windows Mixed Reality 功能的文件。 Unity 提供的文件包含兩個不同的區段：
1. **Unity 指令碼參考**
    * 文件中的此區段包含 Unity 所提供 API 指令碼的詳細資料。
    * 透過 [說明 > 指令碼參考]  ，可以從 Unity 編輯器存取
2. **Unity 手冊**
    * 本手冊的設計目的是協助您了解如何從基本到進階技術來使用 Unity。
    * 透過 [說明 > 手冊]  ，可以從 Unity 編輯器存取

## <a name="see-also"></a>請參閱
* [混合實境工具組 v2](mrtk-getting-started.md)
* [MR Basics 100：開始使用 Unity](holograms-100.md)
* [Unity 的建議設定](recommended-settings-for-unity.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳作法](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 播放模式](unity-play-mode.md)
* [移植指南](porting-guides.md)
