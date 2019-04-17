---
title: Unity 開發概觀
description: 取得開始的建置混合實境應用程式，在 Unity 中。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，混合實境、 開發、 開始、 新的專案、 移植、 功能、 相機、 模擬、 模擬、 文件
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596903"
---
# <a name="unity-development-overview"></a>Unity 開發概觀

建置的最快路徑[mixed 的 reality 應用程式](app-views.md)是具有[Unity](http://aka.ms/HoloLensUnity)。 我們建議您花時間來探索[Unity 教學課程](https://unity3d.com/learn/tutorials)。 如果您需要的資產，Unity 的全方位[Asset Store](https://www.assetstore.unity3d.com/)。 一旦您已經建立基本的了解的 Unity，您可以瀏覽[混合實境 Academy](academy.md)若要了解使用 Unity 的混合的實境開發的詳細資訊。 請造訪[Unity 混合實境論壇](http://forum.unity3d.com/forums/hololens.102/)來參與社群建置 Unity 中的混合的實境應用程式的其餘部分，並尋找您可能會遇到的問題。

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>移植到 Windows 混和實境現有的 Unity 應用程式

如果您有現有的 Unity 專案，您要移植到 Windows 混和實境，遵循[Unity 移植指南](porting-guides.md)開始著手。

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a>設定新的 Unity 專案的 Windows Mixed Reality

若要開始建置使用 Unity 的混合的實境應用程式第一次[安裝工具](install-the-tools.md)。 如果您將目標 Windows Mixed Reality 沈浸式耳機，而不是 HoloLens，您將需要 Unity 的特殊版本現在。

如果您剛建立新的 Unity 專案有較少的 Unity 設定您要變更 Windows Mixed Reality，分成兩個類別： 每個專案和每個場景。

### <a name="per-project-settings"></a>每個專案設定

若要目標 Windows Mixed Reality，必須先設定您的 Unity 專案，以匯出為通用 Windows 平台應用程式：
1. 選取**檔案 > 組建設定...**
2. 選取 **通用 Windows 平台**平台清單，然後按一下**切換平台**
3. 設定**SDK**到**通用 10**
4. 設定**目標裝置**要**任何裝置**支援沈浸式耳機或切換至**HoloLens**
5. 設定**建置型別**到**D3D**
6. 設定**UWP SDK**到**最新安裝**

我們再需要讓知道我們嘗試匯出的應用程式應該建立 Unity[沈浸式檢視](app-views.md)而不是 2D 檢視。 我們的做法是啟用 「 虛擬實境支援 」:
1. 從**組建設定...** 視窗中，開啟**播放程式設定...**
2. 選取 [**通用 Windows 平台設定**] 索引標籤
3. 依序展開**XR 設定**群組
4. 在  **XR 設定**區段中，按一下**受支援的虛擬實境**核取方塊以新增**虛擬實境裝置**清單。
5. 在  **XR 設定**群組中，確認 **「 Windows Mixed Reality"** 列為支援的裝置。 （這可能會顯示為 「 Windows 全像 」 在較舊版本的 Unity）

您的應用程式現在可以進行基本全像攝影版的轉譯和空間的輸入。 若要更進一步，並利用特定功能，您的應用程式必須宣告適當的功能資訊清單中。 可以在 Unity 中進行資訊清單宣告，因此它們會包含在每個後續的專案匯入。 設定位於**Player 設定 > 適用於通用 Windows 平台的設定 > 發行設定 > 功能**。 啟用常用 Unity Api for Mixed Reality 適用的功能如下：

|  功能  |  需要功能的 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (存取權[空間的對應](spatial-mapping.md)網狀結構 HoloLens 上)&mdash;*沒有一般的耳機空間追蹤您所需的功能* | 
|  WebCam  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture 或 VideoCapture，分別 （儲存時所擷取的內容） | 
|  麥克風  |  VideoCapture （當擷取音訊）、 DictationRecognizer、 GrammarRecognizer 和 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer （以及使用 Unity Profiler） | 

**Unity 的品質設定**

![Unity 的品質設定](images/unityqualitysettings-350px.png)<br>
*Unity 的品質設定*

HoloLens 有 mobile 類別的 GPU。 如果您的應用程式的目標 HoloLens，您會想的品質設定為最快的效能微調請確定我們會保留完整的畫面播放速率：
1. 選取**編輯 > 專案設定 > 品質**
2. 選取**下拉式清單**下方**Windows 市集**標誌，然後選取**Fastest**。 您知道設定正確時套用的 Windows 市集的資料行中的方塊並**最快**資料列是綠色。

### <a name="per-scene-settings"></a>每個場景設定

**Unity 觀景窗設定**

![Unity 觀景窗設定](images/unitycamerasettings.png)<br>
*Unity 觀景窗設定*

一旦您啟用 「 虛擬實境支援 」 核取方塊[Unity 數位相機](camera-in-unity.md)元件控制代碼[前端追蹤和立體視覺呈現](rendering.md)。 就不需要將它取代自訂的數位相機，若要這樣做。

如果您的應用程式的目標 HoloLens 具體來說，有一些需要變更以最佳化裝置透明的顯示畫面，讓您的應用程式就會直接透過真實世界的設定：
1. 在 **階層**，選取**Main Camera**
2. 在**Inspector**  面板中，設定轉換**位置**來**0，0，0**讓使用者標頭的位置啟動 Unity 世界原始位置。
3. 變更**清除旗標**要**單色**。
4. 變更**背景**色彩**RGBA 0,0,0,0**。 黑色呈現為透明的 HoloLens。
5. 變更**接近裁剪平面-** 要[HoloLens 建議](camera-in-unity.md#clip-planes)0.85 （公尺）。

如果您刪除，然後建立新的相機，請確定您的相機**標籤**作為**MainCamera**。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>新增混合的實境功能和輸入

一旦您已設定您的專案，如上面所述，標準的 Unity 遊戲物件 （例如數位相機） 則受到立即的**安插擴展經驗**，與自動更新使用者的相機的位置移動透過世界其標頭。

新增 Windows Mixed Reality 功能的支援，例如[空間階段](coordinate-systems.md#spatial-coordinate-systems)，[筆勢，移動控制器](gestures-and-motion-controllers-in-unity.md)或[語音輸入](voice-input-in-unity.md)透過直接內建的 ApiUnity。

您的第一個步驟應該是檢閱[體驗標尺](coordinate-systems.md)為目標應用程式：
* 如果您想要建置**方向專用**或**插入擴充槽擴展經驗**，您將需要設定 Unity 的追蹤要空間型別[「 定態](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您想要建置**常設級別**或**聊天室擴展經驗**，您必須確保 Unity 的追蹤空間型別已成功設定為[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您想要建置**全球級別**體驗 HoloLens，讓使用者漫遊遠 5 公尺之外，您必須使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)元件。

所有的核心建置組塊，混合的實境應用程式中與其他的 Unity Api 一致的方式公開：
* [相機](camera-in-unity.md)
* [座標系統](coordinate-systems-in-unity.md)
* [Gaze](gaze-in-unity.md)
* [筆勢和動作控制站](gestures-and-motion-controllers-in-unity.md)
* [語音輸入](voice-input-in-unity.md)
* [持續性](persistence-in-unity.md)
* [空間的音效](spatial-sound-in-unity.md)
* [空間對應](spatial-mapping-in-unity.md)

有許多的混合的實境應用程式將會想使用的也會公開給 Unity 應用程式的其他重要功能：
* [共用的體驗](shared-experiences-in-unity.md)
* [之外的可尋獲相機](locatable-camera-in-unity.md)
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
* [MR 基本概念 100:開始使用 Unity](holograms-100.md)
* [Unity 的建議的設定](recommended-settings-for-unity.md)
* [Unity 的效能建議](performance-recommendations-for-unity.md)
* [匯出和建置 Unity Visual Studio 方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [HoloLens 與 Unity 應用程式使用的 Windows 命名空間](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳作法](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 遊戲模式](unity-play-mode.md)
* [移植指南](porting-guides.md)
