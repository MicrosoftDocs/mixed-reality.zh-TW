---
title: 在 Unity 視線
description: 視線是指向您的應用程式會建立在混合實境中全像投影的使用者的主要方式。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 視線、 unity、 全像圖、 混合的實境
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597006"
---
# <a name="gaze-in-unity"></a>在 Unity 視線

[視線](gaze.md)是主要的方法，讓使用者為目標[全像投影](hologram.md)您的應用程式中建立[混合實境](mixed-reality.md)。

## <a name="implementing-gaze"></a>實作視線

就概念而言，[視線](gaze.md)藉由將從耳機所在位置，正面臨並判斷使用者的標頭無限遠的光線投射光線與衝突代表什麼意思。 在 Unity 中，使用者的前端的位置和方向透過 Unity 主要公開[相機](camera-in-unity.md)，特別[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)並[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)。

呼叫[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)導致[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)結構也包含資訊包括 3D 點發生衝突的衝突及其他 GameObject 視線光線衝突。

### <a name="example-implement-gaze"></a>範例：實作視線

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>最佳做法

雖然上述範例示範如何更新迴圈來尋找視線目標的單一 raycast，建議在單一物件管理而不是這麼做可能會想要在正在 gazed 物件中的任何物件的視線中這麼做。 這可讓您執行每個畫面格的一個視線 raycast 儲存處理的應用程式。

## <a name="visualizing-gaze"></a>視覺化視線

就像在桌面上，使用滑鼠指標來為目標並進行互動使用內容，您應該實作[游標](cursors.md)，代表使用者的視線。 這讓使用者的信心，在即將要進行互動。

## <a name="gaze-in-mixed-reality-toolkit"></a>視線混合的實境工具組中
當您匯入[MRTK 發行 Unity 套件](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或從專案複製[GitHub 存放庫](https://github.com/Microsoft/MixedRealityToolkit-Unity)，您要在 Unity 中尋找新的功能表 ' 混合實境 Toolkit'。 在 [設定] 功能表上，您會看到功能表 [適用於混合實境場景設定]。 當您按一下它時，它會移除預設相機，並新增基本元件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，並[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。

![MRTK 場景設定功能表](images/MRTK_Input_Menu.png)<br>
*MRTK 場景設定功能表*

![自動的場景中 MRTK 的安裝程式](images/MRTK_HowTo_Input1.png)<br>
*自動的場景中 MRTK 的安裝程式*

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a>視線混合實境工具組中的相關指令碼
混合實境工具組包含 InputManager prefab [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs)並[視線對](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs)。 底下[SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs)，您可以指派您自訂的資料指標。 在預設情況下，動畫[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)指派。

[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)並[CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)示範如何以視覺化方式檢視您的視線使用資料指標。

## <a name="see-also"></a>另請參閱
* [相機](camera-in-unity.md)
* [Gaze](gaze.md)
* [資料指標](cursors.md)
* [為目標的視線](gaze-targeting.md)
