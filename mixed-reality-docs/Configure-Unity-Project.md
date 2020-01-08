---
title: 為 Windows Mixed Reality 設定新的 Unity 專案
description: 在不 MRTK 的情況下設定 Unity 專案
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity，混合現實，開發，快速入門，新專案
ms.openlocfilehash: 99c72f2d9d900c8a05fb7d8b9b8de10d657fdd13
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502649"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>為 Windows Mixed Reality 設定新的 Unity 專案 

（如果您已將 MRTK v2 匯入 Unity 專案，請略過）

如果您想要建立新的 Unity 專案，但未匯入 Mixed Reality 工具組，則您需要針對 Windows Mixed Reality 手動變更的一小組 Unity 設定，分為兩個類別：每個專案和每個場景。

## <a name="per-project-settings"></a>每個專案的設定

若要以 Windows Mixed Reality 為目標，您必須先將 Unity 專案設定為匯出為通用 Windows 平臺應用程式： 
1. 選取 [檔案 **> 組建設定**...]
2. 在 [平臺] 清單中選取**通用 Windows 平臺**，然後按一下 [**切換平臺**]
3. 將**SDK**設定為**通用 10**
4. 將 [**目標裝置**] 設定為 [**任何裝置**] 以支援沉浸式耳機或切換至**HoloLens**
5. 將**組建類型**設定為**D3D**
6. 將**UWP SDK**設定為**最新安裝**

接著，您需要讓 Unity 知道您嘗試匯出的應用程式應該建立[沉浸式視圖](app-views.md)，而不是2d 視圖。 您可以藉由啟用「支援虛擬實境」來執行此動作：
1. 從 [**組建設定 ...** ] 視窗中，開啟 [**播放者設定**]。
2. 選取 [**通用 Windows 平臺**] 索引標籤的設定
3. 展開 [ **XR 設定**] 群組
4. 在 [ **XR 設定**] 區段中，勾選 [**支援虛擬實境**] 核取方塊以新增**虛擬實境裝置**清單。
5. 在 [ **XR 設定**] 群組中，確認 **[Windows Mixed Reality]** 已列為支援的裝置。 （在舊版 Unity 中，這可能會顯示為「Windows 全像」）

![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)<br>
*Unity xr 設定*

您的應用程式現在可以執行基本的全像攝影轉譯和空間輸入。 若要進一步瞭解並利用特定功能，您的應用程式必須在其資訊清單中宣告適當的功能。 資訊清單宣告可在 Unity 中進行，使其包含在每個後續的專案匯出中。 您可以在 [播放程式設定] 中找到設定， **> 通用 Windows 平臺 > 發佈設定 > 功能的設定**。 針對混合式現實啟用常用 Unity Api 的適用功能包括：

|  功能  |  需要功能的 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver （在 HoloLens 上存取[空間對應](spatial-mapping.md)網格）&mdash;*耳機的一般空間追蹤所需的功能* | 
|  網路  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture，分別是（儲存已捕獲的內容時） | 
|  麥克風  |  VideoCapture （在捕獲音訊時）、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer （並使用 Unity Profiler） | 

**Unity 品質設定**

![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)<br>
*Unity 品質設定*

HoloLens 具有行動類別 GPU。 如果您的應用程式是以 HoloLens 為目標，您會想要調整品質設定以取得最快的效能，以確保我們維持完整的畫面播放速率：
1. 選取 [**編輯] > 專案設定 > 品質**
2. 選取 [ **Windows Store** ] 標誌底下的**下拉式清單**，然後選取 [**非常低**]。 當 [Windows Store] 資料行中的方塊和**非常低**的資料列都是綠色時，您會知道設定已正確套用。

## <a name="per-scene-settings"></a>每場景設定

**Unity 攝影機設定**

![Unity 攝影機設定](images/Unitycamerasettings.png)<br>
*Unity 攝影機設定*

一旦您啟用 [支援虛擬實境] 核取方塊， [Unity 攝影機](camera-in-unity.md)元件就會處理[head 追蹤和 stereoscopic](rendering.md)轉譯。 您不需要將它取代為自訂相機來執行此動作。

如果您的應用程式特別以 HoloLens 為目標，則需要變更幾個設定，以優化裝置的透明顯示，讓您的應用程式會向實體世界顯示：
1. **在階層中，選取** **主要相機**
2. 在 [偵測**器**] 面板中，將 [轉換**位置**] 設定為**0，0，0，** 讓使用者的前端位置從 Unity world 來源開始。
3. 將 [**清除旗標**] 變更為**純色**。
4. 將**背景**色彩變更為**RGBA 0，0，0**，0。 在 HoloLens 中，黑色呈現為透明。
5. 變更**裁剪平面-接近** [HoloLens 建議](camera-in-unity.md#clip-planes)0.85 （計量）。

如果您刪除並建立新的相機，請確定您的相機已**標記**為**MainCamera**。


## <a name="see-also"></a>請參閱
* [混合實境工具組 v2](mrtk-getting-started.md)
* [Unity 開發總覽](unity-development-overview.md)
