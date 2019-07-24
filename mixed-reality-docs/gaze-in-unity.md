---
title: Unity 中的注視
description: 「注視」是一種主要的方式, 可讓使用者以應用程式在混合現實中建立的全息影像為目標。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 目光, unity, 全息影像, 混合現實
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453715"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="e1b39-104">Unity 中的頭注視</span><span class="sxs-lookup"><span data-stu-id="e1b39-104">Head gaze in Unity</span></span>

<span data-ttu-id="e1b39-105">「[注視](gaze.md)」是一種主要的方式, 可讓使用者以應用程式在[混合現實](mixed-reality.md)中建立的[全息影像](hologram.md)為目標。</span><span class="sxs-lookup"><span data-stu-id="e1b39-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="e1b39-106">執行頭部注視</span><span class="sxs-lookup"><span data-stu-id="e1b39-106">Implementing head gaze</span></span>

<span data-ttu-id="e1b39-107">在概念上,[注視](gaze.md)是由從使用者的頭部投射一個光線來實行, 而耳機的方向是朝向正向, 並決定該光線的衝突。</span><span class="sxs-lookup"><span data-stu-id="e1b39-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="e1b39-108">在 Unity 中, 使用者的標頭位置和方向會透過 Unity 主要[攝影機](camera-in-unity.md)公開, 特別是[UnityEngine](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[轉換. 正向](http://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[轉換。位置](http://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="e1b39-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="e1b39-109">呼叫[RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)會產生[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)結構, 其中包含衝突的相關資訊, 包括發生衝突的3d 點, 以及另一個 GameObject 注視光線衝突的位置。</span><span class="sxs-lookup"><span data-stu-id="e1b39-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="e1b39-110">範例：執行頭部注視</span><span class="sxs-lookup"><span data-stu-id="e1b39-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="e1b39-111">最佳做法</span><span class="sxs-lookup"><span data-stu-id="e1b39-111">Best Practices</span></span>

<span data-ttu-id="e1b39-112">雖然上述範例示範如何在更新迴圈中執行單一 raycast 以尋找注視目標, 但建議您在管理注視的單一物件中執行此動作, 而不是在對 gazed 物件有興趣的任何物件中執行此作業。</span><span class="sxs-lookup"><span data-stu-id="e1b39-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="e1b39-113">這可讓您的應用程式在每個畫面格只執行一個注視 raycast 來儲存處理。</span><span class="sxs-lookup"><span data-stu-id="e1b39-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="e1b39-114">視覺化注視</span><span class="sxs-lookup"><span data-stu-id="e1b39-114">Visualizing Gaze</span></span>

<span data-ttu-id="e1b39-115">就像在桌面上使用滑鼠指標來鎖定內容並與其互動, 您應該執行代表使用者注視的[游標](cursors.md)。</span><span class="sxs-lookup"><span data-stu-id="e1b39-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="e1b39-116">這可讓使用者在他們要與之互動的方面獲得信心。</span><span class="sxs-lookup"><span data-stu-id="e1b39-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="e1b39-117">混合現實工具組 v2 中的注視</span><span class="sxs-lookup"><span data-stu-id="e1b39-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="e1b39-118">您可以從 MRTK v2 中的[輸入管理員](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)存取注視。</span><span class="sxs-lookup"><span data-stu-id="e1b39-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1b39-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1b39-119">See also</span></span>
* [<span data-ttu-id="e1b39-120">相機</span><span class="sxs-lookup"><span data-stu-id="e1b39-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="e1b39-121">注視輸入</span><span class="sxs-lookup"><span data-stu-id="e1b39-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="e1b39-122">游標</span><span class="sxs-lookup"><span data-stu-id="e1b39-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e1b39-123">目光目標</span><span class="sxs-lookup"><span data-stu-id="e1b39-123">Gaze targeting</span></span>](gaze-targeting.md)
