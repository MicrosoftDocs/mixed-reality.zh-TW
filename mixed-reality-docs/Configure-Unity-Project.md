---
title: 為 Windows Mixed Reality 設定新的 Unity 專案
description: 設定無 MRTK 的 Unity 專案
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity，混合實境，開發、 開始，新的專案
ms.openlocfilehash: 4ee81eca25109da428d7b3addf59e102ddc5c5cf
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993543"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>為 Windows Mixed Reality 設定新的 Unity 專案 

（如果您已經為您的 Unity 專案匯入 MRTK v2 略過）

如果您想要建立新的 Unity 專案，但不匯入混合實境工具組，有較少的 Unity 設定，您必須手動變更 Windows Mixed Reality，分成兩個類別： 每個專案和每個場景。

## <a name="per-project-settings"></a>每個專案設定

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
2. 選取 **下拉式清單**下方**Windows 市集**標誌，然後選取**非常低**。 您知道設定正確時套用的 Windows 市集的資料行中的方塊並**非常低**資料列是綠色。

## <a name="per-scene-settings"></a>每個場景設定

**Unity 觀景窗設定**

![Unity 觀景窗設定](images/Unitycamerasettings.png)<br>
*Unity 觀景窗設定*

一旦您啟用 「 虛擬實境支援 」 核取方塊[Unity 數位相機](camera-in-unity.md)元件控制代碼[前端追蹤和立體視覺呈現](rendering.md)。 就不需要將它取代自訂的數位相機，若要這樣做。

如果您的應用程式的目標 HoloLens 具體來說，有一些需要變更以最佳化裝置透明的顯示畫面，讓您的應用程式就會直接透過真實世界的設定：
1. 在 **階層**，選取**Main Camera**
2. 在**Inspector**  面板中，設定轉換**位置**來**0，0，0**讓使用者標頭的位置啟動 Unity 世界原始位置。
3. 變更**清除旗標**要**單色**。
4. 變更**背景**色彩**RGBA 0,0,0,0**。 黑色呈現為透明的 HoloLens。
5. 變更**接近裁剪平面-** 要[HoloLens 建議](camera-in-unity.md#clip-planes)0.85 （公尺）。

如果您刪除，然後建立新的相機，請確定您的相機**標籤**作為**MainCamera**。


## <a name="see-also"></a>另請參閱
* [混合實境 Toolkit v2](mrtk-getting-started.md)
* [Unity 開發概觀](unity-development-overview.md)
