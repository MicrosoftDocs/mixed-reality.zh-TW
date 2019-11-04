---
title: Unity 中的注視
description: 「注視」是一種主要的方式，可讓使用者以應用程式在混合現實中建立的全息影像為目標。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛眼，眼鏡，unity，全息影像，混合現實
ms.openlocfilehash: 8222a5199cc1ea35429f21e7490e1eff49fcd1bc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435301"
---
# <a name="head-gaze-in-unity"></a>Unity 中的頭注視

「[注視](gaze-and-commit.md)」是一種主要的方式，可讓使用者以應用程式在[混合現實](mixed-reality.md)中建立的[全息影像](hologram.md)為目標。


## <a name="implementing-head-gaze"></a>實現頭部

在概念[上，您](gaze-and-commit.md)可以從使用者的頭部投射一個光線，而這是指耳機的正向，並決定該光線與哪一個衝突。 在 Unity 中，使用者的標頭位置和方向會透過 Unity 主要[攝影機](camera-in-unity.md)公開，特別是[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[轉換. 正向](https://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[轉換。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。

呼叫[RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html)會產生[RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html)結構，其中包含衝突的相關資訊，包括發生衝突的3d 點，以及另一個 GameObject 的前端注視光線衝突。

### <a name="example-implement-head-gaze"></a>範例：執行 head 注視

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

雖然上述範例示範如何在更新迴圈中執行單一 raycast，以尋找使用者前端的目標，但建議您在管理 head 眼的單一物件中執行此動作，而不是在對物件傳入可能感興趣的任何物件中執行此作業。t 正在 gazed。 這可讓您的應用程式在每個畫面格只執行一個前端 raycast 來儲存處理。

## <a name="visualizing-head-gaze"></a>視覺化頭注視

就像在桌面上使用滑鼠指標來鎖定內容並與之互動，您應該執行代表使用者前端的[游標](cursors.md)。 這可讓使用者在他們要與之互動的方面獲得信心。

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>混合現實工具組 v2 中的頭部注視
您可以從 MRTK v2 中的[輸入管理員](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)存取 head 注視。

## <a name="see-also"></a>請參閱
* [相機](camera-in-unity.md)
* [游標](cursors.md)
* [頭部目光和行動](gaze-and-commit.md)
