---
title: 為 Windows Mixed Reality 設定新的 Unity 專案
description: 針對 Windows Mixed Reality 設定 Unity 專案的指示
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity，混合現實，開發，快速入門，新專案
ms.openlocfilehash: 64f7006bf212f49ab1c478d5dbb1fc1f5ab15497
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390097"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>為 Windows Mixed Reality 設定新的 Unity 專案 

## <a name="overview"></a>概觀

Windows Mixed Reality （WMR）是 Windows 10 作業系統的一部分引進的 Microsoft 平臺。 WMR 平臺可讓您建立應用程式，以在全像攝影和 VR 顯示裝置上呈現數位內容。

設定 WMR 時，您可以採用兩個路徑。 第一個選項是安裝[混合現實工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)組（MRTK） v2，這會自動設定 WMR 環境。 第二個選項是手動變更一些 Unity 設定，以使用 WMR 進行滾動。 

> [!NOTE]
> 您稍後可以隨時匯入 MRTK，因此先進行手動路由並不會有負面影響。

如果您選擇 WMR 手動設定，您需要變更的設定會分成兩個類別：每個專案和每個場景。

## <a name="per-project-settings"></a>每個專案的設定

您需要針對 WMR 變更的第一個設定是專案平臺： 
1. 選取 [檔案 **> 組建設定**...]
2. 在 [平臺] 清單中選取**通用 Windows 平臺**，然後按一下 [**切換平臺**]
3. 將**SDK**設定為**通用 10**
4. 將 [**目標裝置**] 設定為 [**任何裝置**] 以支援沉浸式耳機或切換至**HoloLens**
5. 將**組建類型**設定為**D3D**
6. 將**UWP SDK**設定為**最新安裝**

![Unity XR 設定](images/unity-uwp-settings.png)<br>
*Unity XR 設定*

正確設定平臺之後，您必須讓 Unity 知道您的應用程式應該在匯出時建立[沉浸式視圖](app-views.md)，而不是2d 視圖：
1. 從 [**組建設定 ...** ] 視窗中，開啟 [**播放者設定**]。
2. 選取 [**通用 Windows 平臺**] 索引標籤的設定，然後展開 [ **XR 設定**] 群組
3. 在 [ **XR 設定**] 區段中，勾選 [**支援虛擬實境**] 核取方塊以新增**虛擬實境裝置**清單。
4. 在 [ **XR 設定**] 群組中，確認 **[Windows Mixed Reality]** 已列為支援的裝置。 （在舊版 Unity 中，此選項可能會顯示為**Windows**全像）

![Unity UWP 設定](images/xrsettings.png)<br>
*Unity XR 設定*

### <a name="updating-the-manifest"></a>正在更新資訊清單

您的應用程式現在可以處理全像攝影轉譯和空間輸入。 不過，您的應用程式需要在其資訊清單中宣告適當的功能，才能利用特定功能。 若要尋找您的專案功能，請前往 [播放程式設定]， **> 通用 Windows 平臺 > 發佈設定] > 功能的設定**。 

建議您在 Unity 中進行資訊清單宣告，以將它們包含在您匯出的未來所有專案中。 針對混合式現實啟用常用 Unity Api 的適用功能包括：

|  功能  |  需要功能的 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver （在 HoloLens 上存取[空間對應](spatial-mapping.md)網格） &mdash; *沒有頭戴式耳機的一般空間追蹤所需的功能* | 
|  網路  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture，分別是（儲存已捕獲的內容時） | 
|  麥克風  |  VideoCapture （在捕獲音訊時）、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer （並使用 Unity Profiler） | 

### <a name="quality-settings"></a>品質設定

HoloLens 具有行動類別 GPU。 如果您的應用程式是以 HoloLens 為目標，您會想要調整應用程式中的品質設定以取得最快的效能，以確保它會維持完整的畫面播放速率：
1. 選取 [**編輯] > 專案設定 > 品質**
2. 選取 [ **Windows Store** ] 標誌底下的**下拉式清單**，然後選取 [**非常低**]。 當 [Windows Store] 資料行中的方塊和**非常低**的資料列都是綠色時，您會知道設定已正確套用。

![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)<br>
*Unity 品質設定*

## <a name="per-scene-settings"></a>每場景設定

### <a name="unity-camera-settings"></a>Unity 攝影機設定

若已核取 [**虛擬實境支援**]， [Unity 攝影機](camera-in-unity.md)元件會處理[head 追蹤和 stereoscopic](rendering.md)轉譯。 這表示您不需要將主要相機物件取代為自訂相機。

如果您的應用程式特別以 HoloLens 為目標，您需要變更一些設定，以針對裝置的透明顯示進行優化。 這些設定可讓您的全像攝影內容透過實體世界顯示：
1. **在階層中，選取****主要相機**
2. 在 [偵測**器**] 面板中，將 [轉換**位置**] 設定為**0，0，0，** 讓使用者的前端位置從 Unity world 來源開始。
3. 將 [**清除旗標**] 變更為**純色**。
4. 將**背景**色彩變更為**RGBA 0，0，0**，0。 在 HoloLens 中，黑色呈現為透明。
5. 變更**裁剪平面-接近** [HoloLens 建議](camera-in-unity.md#clip-planes)0.85 （計量）。

![Unity 攝影機設定](images/Unitycamerasettings.png)<br>
*Unity 攝影機設定*

> [!IMPORTANT]
> 如果您刪除並建立新的相機，請確定您的新相機已標記為**MainCamera**。

## <a name="see-also"></a>另請參閱
* [混合實境工具組 v2](mrtk-getting-started.md)
* [Unity 開發總覽](unity-development-overview.md)
