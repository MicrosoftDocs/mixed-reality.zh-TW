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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="14128-104">在 Unity 中的標頭視線</span><span class="sxs-lookup"><span data-stu-id="14128-104">Head gaze in Unity</span></span>

<span data-ttu-id="14128-105">[視線](gaze.md)是主要的方法，讓使用者為目標[全像投影](hologram.md)您的應用程式中建立[混合實境](mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="14128-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="14128-106">實作的前端視線</span><span class="sxs-lookup"><span data-stu-id="14128-106">Implementing head gaze</span></span>

<span data-ttu-id="14128-107">就概念而言，[視線](gaze.md)藉由將從耳機所在位置，正面臨並判斷使用者的標頭無限遠的光線投射光線與衝突代表什麼意思。</span><span class="sxs-lookup"><span data-stu-id="14128-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="14128-108">在 Unity 中，使用者的前端的位置和方向透過 Unity 主要公開[相機](camera-in-unity.md)，特別[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)並[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="14128-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="14128-109">呼叫[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)導致[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)結構也包含資訊包括 3D 點發生衝突的衝突及其他 GameObject 視線光線衝突。</span><span class="sxs-lookup"><span data-stu-id="14128-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="14128-110">範例：實作前端視線</span><span class="sxs-lookup"><span data-stu-id="14128-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="14128-111">最佳做法</span><span class="sxs-lookup"><span data-stu-id="14128-111">Best Practices</span></span>

<span data-ttu-id="14128-112">雖然上述範例示範如何更新迴圈來尋找視線目標的單一 raycast，建議在單一物件管理而不是這麼做可能會想要在正在 gazed 物件中的任何物件的視線中這麼做。</span><span class="sxs-lookup"><span data-stu-id="14128-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="14128-113">這可讓您執行每個畫面格的一個視線 raycast 儲存處理的應用程式。</span><span class="sxs-lookup"><span data-stu-id="14128-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="14128-114">視覺化視線</span><span class="sxs-lookup"><span data-stu-id="14128-114">Visualizing Gaze</span></span>

<span data-ttu-id="14128-115">就像在桌面上，使用滑鼠指標來為目標並進行互動使用內容，您應該實作[游標](cursors.md)，代表使用者的視線。</span><span class="sxs-lookup"><span data-stu-id="14128-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="14128-116">這讓使用者的信心，在即將要進行互動。</span><span class="sxs-lookup"><span data-stu-id="14128-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="14128-117">在混合實境中視線 Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="14128-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="14128-118">您可以存取從視線[輸入管理員](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)MRTK v2 中。</span><span class="sxs-lookup"><span data-stu-id="14128-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="14128-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14128-119">See also</span></span>
* [<span data-ttu-id="14128-120">相機</span><span class="sxs-lookup"><span data-stu-id="14128-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="14128-121">視線輸入</span><span class="sxs-lookup"><span data-stu-id="14128-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="14128-122">游標</span><span class="sxs-lookup"><span data-stu-id="14128-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="14128-123">目光目標</span><span class="sxs-lookup"><span data-stu-id="14128-123">Gaze targeting</span></span>](gaze-targeting.md)
