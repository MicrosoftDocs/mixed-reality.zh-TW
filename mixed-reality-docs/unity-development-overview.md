---
title: Unity 開發總覽
description: 開始在 Unity 中建立混合現實應用程式。
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
keywords: Unity，混合現實，開發，快速入門，新專案，移植，功能，攝影機，模擬，模擬，檔
ms.openlocfilehash: b78afb0cf6557ec9b61a029e2d557debbd0b6b46
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437380"
---
# <a name="unity-development-overview"></a>Unity 開發總覽

建立[混合現實應用程式](app-views.md)的最快速路徑是使用[Unity](https://unity.com)。 我們建議您花一些時間來探索[Unity 教學](https://unity3d.com/learn/tutorials)課程。 如果您需要資產，Unity 具有完整的[資產存放區](https://www.assetstore.unity3d.com/)。 建立 Unity 的基本瞭解之後，您可以造訪[教學](tutorials.md)課程，以瞭解使用 unity 進行混合現實開發的細節。 請務必造訪[Unity Mixed Reality 論壇](https://forum.unity3d.com/forums/hololens.102/)，以與在 unity 中建立混合現實應用程式的其餘部分互動，並找出您可能遇到之問題的解決方案。

若要開始使用 Unity 建立混合現實應用程式，請先[安裝工具](install-the-tools.md)。 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>使用混合式現實工具組的新 Unity 專案 

在 Unity 中開發最簡單的方式，就是使用混合現實工具組。 這可協助您自動設定專案，並提供一組混合現實功能來加速您的開發。 請參閱[混合現實工具組 v2](mrtk-getting-started.md)以深入瞭解並開始使用。 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>將現有的 Unity 應用程式移植到 Windows Mixed Reality

如果您有現有的 Unity 專案是要移植到 Windows Mixed Reality，請遵循[Unity 移植指南](porting-guides.md)以開始使用。

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>為 Windows Mixed Reality 設定新的 Unity 專案

如果您想要建立新的 Unity 專案，但未匯入 Mixed Reality 工具組，則您需要手動變更 Windows Mixed Reality 的一小組 Unity 設定。 這些會分成兩個類別：每個專案和每個場景。 如需為[Windows Mixed Reality 設定新 Unity 專案](Configure-Unity-Project.md)的逐步指南，請參閱這裡

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>新增混合現實功能和輸入

當您使用專案設定 MRTK V2 或設定專案（如上所述）之後，標準的 Unity 遊戲物件（例如相機）會立即亮起以進行**固定規模的體驗**，並自動將相機的位置更新為使用者會將其標頭移至世界。

新增 Windows Mixed Reality 功能的支援，例如[空間階段](coordinate-systems.md#spatial-coordinate-systems)、[筆勢、動作控制器](gestures-and-motion-controllers-in-unity.md)或[語音輸入](voice-input-in-unity.md)，是使用直接內建于 Unity 的 api 來達成。 

首先，請檢查您的 applicatioin 可設為目標的[經驗調整](coordinate-systems.md)：
* 如果您想要建立**僅限方向**或**大規模的經驗**，您必須將 Unity 的追蹤空間類型設定為 [[固定](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)]。
* 如果您想要建立**大規模**或**會議室規模的體驗**，您必須確定 Unity 的追蹤空間類型已成功設定為[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您想要在 HoloLens 上建立**全球**化體驗，讓使用者漫遊超過5計量，您必須使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)元件。

混合現實應用程式的所有核心建立區塊都會以與其他 Unity Api 一致的方式公開。 也可以透過混合式現實工具組來取得。
* [相機](camera-in-unity.md)
* [座標系統](coordinate-systems-in-unity.md)
* [目光](gaze-in-unity.md)
* [筆勢和運動控制器](gestures-and-motion-controllers-in-unity.md)
* [語音輸入](voice-input-in-unity.md)
* [暫](persistence-in-unity.md)
* [空間音效](spatial-sound-in-unity.md)
* [空間對應](spatial-mapping-in-unity.md)

還有許多混合現實應用程式會想要使用的重要功能，也會公開至 Unity 應用程式：
* [共用體驗](shared-experiences-in-unity.md)
* [定位相機](locatable-camera-in-unity.md)
* [焦點點](focus-point-in-unity.md)
* [追蹤遺失](tracking-loss-in-unity.md)
* [鍵盤](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>在真實或模擬的裝置上執行 Unity 專案

當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是[匯出並建立 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)。

有了該 VS 解決方案，您就可以使用真實或模擬裝置，以三種方式的其中一種來執行應用程式：
* [部署到真實的 HoloLens 或 Windows Mixed Reality 沉浸式頭戴式裝置](using-visual-studio.md)
* [部署至 HoloLens 模擬器](using-the-hololens-emulator.md)
* [部署到 Windows Mixed Reality 沉浸式耳機模擬器](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 檔

除了 docs.microsoft.com 上提供的這項檔之外，Unity 還會同時安裝 Windows Mixed Reality 功能的檔與 Unity Editor。 Unity 提供的檔包含兩個不同的區段：
1. **Unity 腳本參考**
    * 檔集的這一節包含 Unity 提供的腳本 API 的詳細資料。
    * 透過說明 **> 腳本參考來**存取 Unity Editor
2. **Unity 手冊**
    * 本手冊的設計目的是協助您瞭解如何使用 Unity，從基本到先進的技術。
    * 可從 Unity 編輯器透過 [說明] **> 手動來**存取

## <a name="see-also"></a>請參閱
* [混合現實工具組 v2](mrtk-getting-started.md)
* [MR 基本概念100：開始使用 Unity](holograms-100.md)
* [Unity 的建議設定](recommended-settings-for-unity.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳作法](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 播放模式](unity-play-mode.md)
* [移植指南](porting-guides.md)
