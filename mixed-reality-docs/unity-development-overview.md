---
title: Unity 開發概觀
description: 取得開始的建置混合實境應用程式，在 Unity 中。
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity，混合實境、 開發、 開始、 新的專案、 移植、 功能、 相機、 模擬、 模擬、 文件
ms.openlocfilehash: 2cdcd5e997ab7e3f6d340377464e453a8e7c025c
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64874007"
---
# <a name="unity-development-overview"></a>Unity 開發概觀

建置的最快路徑[mixed 的 reality 應用程式](app-views.md)是具有[Unity](http://aka.ms/HoloLensUnity)。 我們建議您花時間來探索[Unity 教學課程](https://unity3d.com/learn/tutorials)。 如果您需要的資產，Unity 的全方位[Asset Store](https://www.assetstore.unity3d.com/)。 一旦您已經建立基本的了解的 Unity，您可以瀏覽[教學課程](tutorials.md)若要了解使用 Unity 的混合的實境開發的詳細資訊。 請造訪[Unity 混合實境論壇](http://forum.unity3d.com/forums/hololens.102/)來參與社群建置 Unity 中的混合的實境應用程式的其餘部分，並尋找您可能會遇到的問題。


若要開始建置使用 Unity 的混合的實境應用程式第一次[安裝工具](install-the-tools.md)。 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>新的 Unity 專案的混合的實境工具組 

在 Unity 所開發的最簡單方式是混合實境工具組的協助。 它會自動執行，協助您設定專案，並提供一組，加速開發您的混合實境功能。 請查看[混合實境 Toolkit v2](mrtk-getting-started.md)來進一步了解並開始使用。 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>移植到 Windows 混和實境現有的 Unity 應用程式

如果您有現有的 Unity 專案，您要移植到 Windows 混和實境，遵循[Unity 移植指南](porting-guides.md)開始著手。

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>設定新的 Unity 專案的 Windows Mixed Reality

如果您想要建立新的 Unity 專案，但不匯入混合實境工具組，有較少的 Unity 設定，您必須手動變更 Windows Mixed Reality，分成兩個類別： 每個專案和每個場景。 請參閱以下的逐步解說指南[設定新 Unity 專案的 Windows Mixed Reality](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>新增混合的實境功能和輸入

一旦您已安裝 MRTK V2 與您的專案，或如上面所述，設定您的專案時，標準的 Unity 遊戲物件 （例如數位相機） 則受到立即的**安插擴展經驗**，具有相機的位置更新自動為使用者通過其標頭的世界。

新增 Windows Mixed Reality 功能的支援，例如[空間階段](coordinate-systems.md#spatial-coordinate-systems)，[筆勢，移動控制器](gestures-and-motion-controllers-in-unity.md)或[語音輸入](voice-input-in-unity.md)透過直接內建的 ApiUnity。 

您的第一個步驟應該是檢閱[體驗標尺](coordinate-systems.md)為目標應用程式：
* 如果您想要建置**方向專用**或**插入擴充槽擴展經驗**，您將需要設定 Unity 的追蹤要空間型別[「 定態](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您想要建置**常設級別**或**聊天室擴展經驗**，您必須確保 Unity 的追蹤空間型別已成功設定為[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您想要建置**全球級別**體驗 HoloLens，讓使用者漫遊遠 5 公尺之外，您必須使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)元件。

所有的核心建置組塊，混合的實境應用程式會公開在與其他的 Unity Api 一致的方式。 它們也可透過混合實境工具組。
* [相機](camera-in-unity.md)
* [座標系統](coordinate-systems-in-unity.md)
* [目光](gaze-in-unity.md)
* [筆勢和動作控制站](gestures-and-motion-controllers-in-unity.md)
* [語音輸入](voice-input-in-unity.md)
* [持續性](persistence-in-unity.md)
* [空間音效](spatial-sound-in-unity.md)
* [空間對應](spatial-mapping-in-unity.md)

有許多的混合的實境應用程式將會想使用的也會公開給 Unity 應用程式的其他重要功能：
* [共用的體驗](shared-experiences-in-unity.md)
* [定位相機](locatable-camera-in-unity.md)
* [焦點](focus-point-in-unity.md)
* [追蹤遺失](tracking-loss-in-unity.md)
* [鍵盤](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>真實或模擬裝置上執行您的 Unity 專案

您有全像攝影版的 Unity 專案準備好測試，您下一步是要[匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)。

之後，在 VS 方案，您可以再執行您的應用程式其中一種方式，使用真實或模擬的裝置：
* [將部署到實際的 HoloLens 或 Windows Mixed Reality 沈浸式耳機](using-visual-studio.md)
* [部署至 HoloLens 模擬器](using-the-hololens-emulator.md)
* [將部署到 Windows Mixed Reality 沈浸式耳機模擬器](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 文件

除了本文件中可以使用 Windows 開發人員中心上，Unity 會安裝 Windows Mixed Reality 功能與 Unity Editor 中的文件。 Unity 提供文件包含兩個不同的區段：
1. **Unity 指令碼參考**
    * 本節的文件包含 Unity 所提供的指令碼 api 的詳細資料。
    * 可透過從 Unity 編輯器**協助 > 指令碼參考**
2. **Unity manual**
    * 本手冊可協助您了解如何使用 Unity 中，從基本到進階技術。
    * 可透過從 Unity 編輯器**協助 > 手動**

## <a name="see-also"></a>另請參閱
* [混合實境 Toolkit v2](mrtk-getting-started.md)
* [MR Basics 100：開始使用 Unity](holograms-100.md)
* [Unity 的建議設定](recommended-settings-for-unity.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳作法](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 播放模式](unity-play-mode.md)
* [移植指南](porting-guides.md)
