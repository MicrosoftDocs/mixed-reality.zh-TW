---
title: 在 Unity 中的相機
description: 如何使用 Unity 的主攝影機的 Windows Mixed Reality 開發進行全像攝影版的轉譯
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 全像攝影版的轉譯、 全像攝影版的沉浸式鶗懘、 深度緩衝區、 方向、 位置、 不透明且透明的剪輯
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591174"
---
# <a name="camera-in-unity"></a>在 Unity 中的相機

當您穿上混合的實境耳機時，它會變成您全像攝影版的世界的中心。 Unity[相機](http://docs.unity3d.com/Manual/class-Camera.html)元件會自動處理立體視覺呈現，並將您的前端的移動和旋轉時遵循您的專案具有 「 虛擬實境支援 」 與 「 Windows Mixed Reality"選取 （以裝置為[其他設定] 區段的 [Windows 市集的播放程式設定）。 這可能會列為 「 Windows 全像 」 在較舊版本的 Unity。

不過，若要完全最佳化視覺品質並[闀穩定性](hologram-stability.md)，您應該設定如下所述的觀景窗設定。

>[!NOTE]
>要套用至您的應用程式的每個場景中的相機，需要這些設定。
>
>根據預設，當您在 Unity 中，建立新的場景時它就會包含包括相機元件，但沒有正確套用下方設定階層中的 Main 相機 GameObject。

## <a name="holographic-vs-immersive-headsets"></a>沈浸式的耳機與全像攝影版

Unity 數位相機元件上的預設設定適用於傳統的 3D 應用程式需要類似天空盒的背景，因為它們沒有真實的世界。
* 在上執行時**[沈浸式耳機](immersive-headset-hardware-details.md)** 您要轉譯的使用者所見的所有項目，因此您可能會想要保留的天空盒。
* 不過，在上執行時**全像攝影版的耳機**像[HoloLens](hololens-hardware-details.md)，現實世界裡應該會出現背後的所有項目相機轉譯。 若要這樣做，請設定 相機背景透明 （的 HoloLens，為透明的黑色呈現) 而不是天空盒材質：
    1. 在 階層 面板中選取 Main Camera
    2. 在 [偵測器] 面板中，找不到相機元件，並從天空盒中變更清除旗標的下拉式清單中，為純色
    3. 選取 背景色彩選擇器，並將 RGBA 值變更為 （0，0，0，0）

您可以使用指令碼在執行階段判斷耳機藉由檢查是否為沈浸式或全像攝影版[HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)。


## <a name="positioning-the-camera"></a>定位觀景窗

它能夠更輕鬆地配置您的應用程式，如果您能想像為 （x： 使用者的開始位置0，Y:0，Z:0). 由於 Main Camera 正在追蹤使用者的標頭的移動，就可以設定使用者的開始位置設定 Main Camera 的開始位置。
1. 在 階層 面板中選取 Main Camera
2. 在 [偵測器] 面板中，找不到的轉換元件，並變更的位置 （x:0，Y:1，z:-10） 到 （x:0，Y:0，Z:0)

   ![在 Unity 中的 [偵測器] 窗格中的相機](images/maincamera-350px.png)<br>
   *在 Unity 中的 [偵測器] 窗格中的相機*

## <a name="clip-planes"></a>裁剪平面

呈現內容太關閉，使用者可以是只要不在混合實境中的。 您可以調整[近乎並遠裁剪平面](hologram-stability.md#hologram-render-distances)相機元件上。
1. 在 階層 面板中選取 Main Camera
2. 在 [偵測器] 面板中，尋找相機元件裁剪平面並將變更幾近文字方塊從 0.3.85。 呈現更接近內容可能會導致使用者 discomfort，應該予以避免每次[呈現距離指導方針](hologram-stability.md#hologram-render-distances)。

## <a name="multiple-cameras"></a>多個相機

當場景中有多個相機的元件時，Unity 知道哪些攝影機使用立體視覺呈現，並藉由檢查哪些 GameObject 前端追蹤具有 MainCamera 標記。

## <a name="recentering-a-seated-experience"></a>Recentering 安置的體驗

如果您正在建置[安插擴展經驗](coordinate-systems.md)，您可以藉由呼叫的使用者的目前位置前端 recenter Unity 的全局原點**[XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。

## <a name="reprojection-modes"></a>Reprojection 模式

HoloLens 和沈浸式耳機將 reproject 您的應用程式呈現，以便調整使用者的實際標頭位置的任何 misprediction 時 photons 所發出的每個畫面格。

預設值：

* **沈浸式耳機**會執行位置 reprojection，調整您的位置和方向，misprediction 全像投影，如果應用程式提供深度緩衝區的指定範圍內。  如果未提供深度緩衝區，系統將只會修正 mispredictions 方向。
* **全像攝影版的耳機**像 HoloLens 會執行位置 reprojection 是否與否，應用程式會提供其深度緩衝區。  轉譯通常就是疏鬆具有穩定的背景提供真實世界，位置 reprojection 是一定要有 HoloLens 上的深度緩衝區。

如果您知道您要建置[僅限方向的經驗](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)嚴格的主體鎖定內容 （例如 360 度的視訊內容），您可以明確設定 reprojection režim fullgeneration 方向只是藉由設定[HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)要[HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)。

## <a name="sharing-your-depth-buffers-with-windows"></a>與 Windows 共用您的深度緩衝區

共用您的應用程式深度緩衝區，以每個畫面格會提供您的應用程式的兩個提升其中一個全像穩定性，耳機的型別為基礎的 Windows 您要轉譯為：
* **沈浸式耳機**可以執行位置 reprojection，提供深度緩衝區時，調整您的位置和方向的 misprediction 全像投影。
* **全像攝影版的耳機**像會自動選取 HoloLens[專注點](focus-point-in-unity.md)提供深度緩衝區時，最佳化全像穩定性沿著相交最內容的平面。

若要設定您的 Unity 應用程式會提供給 Windows 的深度緩衝區是否：
1. 移至**編輯** > **專案設定** > **Player** > **通用 Windows 平台 索引標籤**  >  **XR 設定**。
2. 依序展開**Windows Mixed Reality SDK**項目。
3. 選取或取消選取**啟用深度緩衝區共用**核取方塊。  這將會檢查所建立，因為這項功能新增至 Unity，以及將會取消選取的新專案中預設會針對較舊的專案已升級的預設值。

為 Windows 提供的深度緩衝區可以改善視覺品質，只要 Windows 可以精確地對應深度緩衝區中的正規化每個像素深度值回距離，以公尺為單位，使用您已設定在 Unity 中主攝影機遠近平面。  如果您轉譯通過控點深度值以一般方式，通常應該就可以在這裡，雖然半透明呈現傳遞，以寫入至深度緩衝區時透過現有的顯示色彩像素造成混淆 reprojection。  如果您知道轉譯階段會讓您最終的深度像素為單位的許多有不正確的深度值，您可能會以取得更佳的視覺品質，藉由取消選取 [啟用深度緩衝區共用]。

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a>混合的實境工具組的自動場景安裝程式
當您匯入[MRTK 發行 Unity 套件](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或從專案複製[GitHub 存放庫](https://github.com/Microsoft/MixedRealityToolkit-Unity)，您要在 Unity 中尋找新的功能表 ' 混合實境 Toolkit'。 在 [設定] 功能表上，您會看到功能表 [適用於混合實境場景設定]。 當您按一下它時，它會移除預設相機，並新增基本元件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，並[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。

![MRTK 場景設定功能表](images/MRTK_Input_Menu.png)<br>
*MRTK 場景設定功能表*

![自動的場景中 MRTK 的安裝程式](images/MRTK_HowTo_Input1.png)<br>
*自動的場景中 MRTK 的安裝程式*

## <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefab
您可以手動新增這些從 [專案] 面板。 您可以找到 prefabs 這些元件。 當您搜尋**MixedRealityCamera**，您將能夠看到兩個不同的數位相機 prefabs。 差別在於**MixedRealityCamera**才相機 prefab 而**MixedRealityCameraParent**包含沈浸式耳機，例如屏障，動作的其他元件控制器和，界限。

![在 MRTK 相機 prefabs](images/MRTK_HowTo_Input2.png)<br>
*在 MRTK 相機 prefabs*

**MixedRealtyCamera**支援 HoloLens 和沈浸式耳機。 它會偵測到的裝置類型，並最佳化清除旗標和天空盒等屬性。 以下您可以找到一些有用的屬性，您可以自訂游標，移動控制器模型，例如自訂和樓層。

![屬性的動作控制站中，資料指標和樓層](images/MRTK_HowTo_Input3.png)<br>
*屬性的動作控制站中，資料指標和樓層*

## <a name="see-also"></a>另請參閱
* [全像穩定性](hologram-stability.md)
* [MixedRealityToolkit Main Camera.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
