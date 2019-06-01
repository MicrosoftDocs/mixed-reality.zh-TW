---
title: 在 Unity 視線
description: 視線是指向您的應用程式會建立在混合實境中全像投影的使用者的主要方式。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 視線、 unity、 全像圖、 混合的實境
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453715"
---
# <a name="head-gaze-in-unity"></a>在 Unity 中的標頭視線

[視線](gaze.md)是主要的方法，讓使用者為目標[全像投影](hologram.md)您的應用程式中建立[混合實境](mixed-reality.md)。


## <a name="implementing-head-gaze"></a>實作的前端視線

就概念而言，[視線](gaze.md)藉由將從耳機所在位置，正面臨並判斷使用者的標頭無限遠的光線投射光線與衝突代表什麼意思。 在 Unity 中，使用者的前端的位置和方向透過 Unity 主要公開[相機](camera-in-unity.md)，特別[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)並[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)。

呼叫[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)導致[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)結構也包含資訊包括 3D 點發生衝突的衝突及其他 GameObject 視線光線衝突。

### <a name="example-implement-head-gaze"></a>範例：實作前端視線

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

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>在混合實境中視線 Toolkit v2
您可以存取從視線[輸入管理員](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)MRTK v2 中。

## <a name="see-also"></a>另請參閱
* [相機](camera-in-unity.md)
* [視線輸入](gaze.md)
* [游標](cursors.md)
* [目光目標](gaze-targeting.md)
