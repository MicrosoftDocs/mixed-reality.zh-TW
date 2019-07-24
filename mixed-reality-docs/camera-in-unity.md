---
title: Unity 中的相機
description: 如何使用 Unity 的主要攝影機進行 Windows Mixed Reality 開發以進行全像轉譯
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、全像攝影、全像投影、沉浸式、焦點、深度緩衝區、僅限方向、位置、不透明、透明、裁剪
ms.openlocfilehash: 3a9846242dd1709bcaf927d8ffae33862e96ecc8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522387"
---
# <a name="camera-in-unity"></a>Unity 中的相機

當您磨損混合現實耳機時, 它會成為您的全像攝影世界的中心。 Unity[攝影機](http://docs.unity3d.com/Manual/class-Camera.html)元件會自動處理 stereoscopic 轉譯, 並在您的專案已選取 [Windows Mixed reality] 做為裝置 (在其他設定中) 時, 遵循您的 head 移動和旋轉區段中的 [Windows Store Player 設定])。 在舊版 Unity 中, 這可能會列為「Windows 全像」。

不過, 若要完全優化視覺品質和全息圖形的[穩定性](hologram-stability.md), 您應該設定以下所述的相機設定。

>[!NOTE]
>這些設定必須套用至您應用程式的每個場景中的相機。
>
>根據預設, 當您在 Unity 中建立新場景時, 它會在階層中包含主要相機 GameObject, 其中包含相機元件, 但未正確套用下列設定。

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a>使用混合現實工具組 v2 進行自動場景和相機設定。 

遵循[逐步](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)指南, 將混合現實工具組 v2 新增至您的 Unity 專案, 它會自動設定您的專案。

您也可以使用下一節中的指南, 手動設定專案, 而不 MRTK。 

## <a name="holographic-vs-immersive-headsets"></a>全像沉浸式耳機

Unity 攝影機元件上的預設設定適用于傳統3D 應用程式, 需要 skybox 的背景, 因為它們沒有真實世界。
* 在 **[沉浸式耳機](immersive-headset-hardware-details.md)** 上執行時, 您會轉譯使用者看到的所有內容, 因此您可能會想要保留 skybox。
* 不過, 在[HoloLens](hololens-hardware-details.md)這類全像的**耳機**上執行時, 真實世界應該會出現在相機呈現的所有內容背後。 若要這麼做, 請將相機背景設定為透明 (在 HoloLens 中, 黑色呈現為透明), 而不是 Skybox 材質:
    1. 在 [階層] 面板中選取主要相機
    2. 在 [偵測器] 面板中, 尋找相機元件, 並將 [清除旗標] 下拉式清單從 Skybox 變更為純色
    3. 選取背景色彩選擇器, 並將 RGBA 值變更為 (0, 0, 0, 0)

您可以使用腳本, 在執行時間判斷耳機是否為沉浸式或全像攝影, 方法是檢查[HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)。


## <a name="positioning-the-camera"></a>定位相機

如果您將使用者的開始位置想像為 (X:, 則可以更輕鬆地配置您的應用程式)。0、Y:0, Z:0)。 由於主要攝影機是追蹤使用者頭部的移動, 因此可以藉由設定主要攝影機的開始位置來設定使用者的開始位置。
1. 在 [階層] 面板中選取主要相機
2. 在 偵測器 面板中, 尋找 轉換 元件, 並將位置從 (X:0、Y:1, Z:-10) 至 (X:0、Y:0, Z:0

   ![Unity 中的 [偵測器] 窗格中的相機](images/maincamera-350px.png)<br>
   *Unity 中的 [偵測器] 窗格中的相機*

## <a name="clip-planes"></a>剪輯平面

太接近使用者的轉譯內容可能會令人混淆。 您可以調整相機元件上的[近距離剪輯平面](hologram-stability.md#hologram-render-distances)。
1. 在 [階層] 面板中選取主要相機
2. 在 [偵測器] 面板中, 尋找相機元件裁剪平面, 並將近端 textbox 從0.3 變更為85。 呈現更接近的內容可能會導致使用者 discomfort, 而且應該根據轉譯[距離方針](hologram-stability.md#hologram-render-distances)來避免。

## <a name="multiple-cameras"></a>多個相機

當場景中有多個相機元件時, Unity 會藉由檢查哪個 GameObject 具有 MainCamera 標籤, 來知道要使用哪一個相機來 stereoscopic 轉譯和 head 追蹤。

## <a name="recentering-a-seated-experience"></a>Recentering 上一位經驗

如果您要建立[大規模的經驗](coordinate-systems.md), 您可以呼叫 XR, 在使用者目前的前端位置 recenter Unity 的世界原點 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。

## <a name="reprojection-modes"></a>Reprojection 模式

HoloLens 和沉浸式耳機都會 reproject 應用程式轉譯的每個畫面格, 以便在發出光子時, 針對使用者的實際標頭位置 misprediction 進行調整。

預設:

* 如果應用程式提供特定框架的深度緩衝區, 則**沉浸式耳機**會執行位置 reprojection、調整您的全像位置和方向 misprediction 的全息影像。  如果未提供深度緩衝區, 系統只會在方向更正 mispredictions。
* 如 HoloLens 這類全像的**耳機**將會執行位置 reprojection, 不論應用程式是否提供其深度緩衝區。  在 HoloLens 上可能沒有深度緩衝區, 因為轉譯通常是以真實世界提供的穩定背景來進行稀疏。

如果您知道您要使用嚴格的主體鎖定內容來建立[僅限方向的體驗](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)(例如, 360 度的影片內容), 您可以將 reprojection 模式明確設定為僅透過設定[的方向。HolographicSettings. ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) To [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)。

## <a name="sharing-your-depth-buffers-with-windows"></a>與 Windows 共用深度緩衝區

將應用程式的深度緩衝區與 Windows 共用, 每個畫面格都會根據您要轉譯的頭戴式裝置類型, 為您的應用程式提供兩種影像的其中一種提升:
* 當提供深度緩衝區時,**沉浸式耳機**可以執行位置 reprojection, 調整您的全像位置和方向 misprediction 的全息影像。
* 在提供深度緩衝區時, 像是 HoloLens 這類全像攝影的**耳機**會自動選取[焦點](focus-point-in-unity.md), 並在與大部分內容相交的平面上優化全息影像的穩定性。

若要設定您的 Unity 應用程式是否會提供深度緩衝區給 Windows:
1. 移至 **[編輯** > **專案設定** > ] [**播放** > **通用 Windows 平臺]**  > 索引標籤**XR 設定**。
2. 展開 [ **Windows Mixed REALITY SDK** ] 專案。
3. 勾選或取消核取 [**啟用深度緩衝區共用**] 核取方塊。  預設會在建立的新專案中核取此功能, 因為這項功能已新增至 Unity, 而且預設會針對已升級的舊版專案取消選取。

只要 Windows 能夠精確地將深度緩衝區中正規化的每圖元深度值對應到量表中的距離, 並使用您在主攝影機上的 Unity 中所設定的近和遠平面, 就能為 Windows 提供深度緩衝區來改善視覺品質。  如果您的轉譯行程以一般方式處理深度值, 您通常應該會在這裡正常運作, 但在顯示到現有的色彩圖元時, 寫入深度緩衝區的半透明轉譯傳遞可能會使 reprojection 混淆。  如果您知道您的轉譯行程會讓許多最後深度的圖元變得不正確, 您可能會取消核取 [啟用深度緩衝區共用], 以取得更佳的視覺品質。


## <a name="see-also"></a>另請參閱
* [全像投影穩定性](hologram-stability.md)
* [MixedRealityToolkit 主要攝影機 prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
