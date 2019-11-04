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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="d6b4e-104">Unity 中的頭注視</span><span class="sxs-lookup"><span data-stu-id="d6b4e-104">Head-gaze in Unity</span></span>

<span data-ttu-id="d6b4e-105">「[注視](gaze-and-commit.md)」是一種主要的方式，可讓使用者以應用程式在[混合現實](mixed-reality.md)中建立的[全息影像](hologram.md)為目標。</span><span class="sxs-lookup"><span data-stu-id="d6b4e-105">[Gaze](gaze-and-commit.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="d6b4e-106">實現頭部</span><span class="sxs-lookup"><span data-stu-id="d6b4e-106">Implementing head-gaze</span></span>

<span data-ttu-id="d6b4e-107">在概念[上，您](gaze-and-commit.md)可以從使用者的頭部投射一個光線，而這是指耳機的正向，並決定該光線與哪一個衝突。</span><span class="sxs-lookup"><span data-stu-id="d6b4e-107">Conceptually, [head-gaze](gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="d6b4e-108">在 Unity 中，使用者的標頭位置和方向會透過 Unity 主要[攝影機](camera-in-unity.md)公開，特別是[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[轉換. 正向](https://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[轉換。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="d6b4e-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="d6b4e-109">呼叫[RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html)會產生[RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html)結構，其中包含衝突的相關資訊，包括發生衝突的3d 點，以及另一個 GameObject 的前端注視光線衝突。</span><span class="sxs-lookup"><span data-stu-id="d6b4e-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="d6b4e-110">範例：執行 head 注視</span><span class="sxs-lookup"><span data-stu-id="d6b4e-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="d6b4e-111">最佳做法</span><span class="sxs-lookup"><span data-stu-id="d6b4e-111">Best practices</span></span>

<span data-ttu-id="d6b4e-112">雖然上述範例示範如何在更新迴圈中執行單一 raycast，以尋找使用者前端的目標，但建議您在管理 head 眼的單一物件中執行此動作，而不是在對物件傳入可能感興趣的任何物件中執行此作業。t 正在 gazed。</span><span class="sxs-lookup"><span data-stu-id="d6b4e-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="d6b4e-113">這可讓您的應用程式在每個畫面格只執行一個前端 raycast 來儲存處理。</span><span class="sxs-lookup"><span data-stu-id="d6b4e-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="d6b4e-114">視覺化頭注視</span><span class="sxs-lookup"><span data-stu-id="d6b4e-114">Visualizing head-gaze</span></span>

<span data-ttu-id="d6b4e-115">就像在桌面上使用滑鼠指標來鎖定內容並與之互動，您應該執行代表使用者前端的[游標](cursors.md)。</span><span class="sxs-lookup"><span data-stu-id="d6b4e-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="d6b4e-116">這可讓使用者在他們要與之互動的方面獲得信心。</span><span class="sxs-lookup"><span data-stu-id="d6b4e-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="d6b4e-117">混合現實工具組 v2 中的頭部注視</span><span class="sxs-lookup"><span data-stu-id="d6b4e-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="d6b4e-118">您可以從 MRTK v2 中的[輸入管理員](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)存取 head 注視。</span><span class="sxs-lookup"><span data-stu-id="d6b4e-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6b4e-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6b4e-119">See also</span></span>
* [<span data-ttu-id="d6b4e-120">相機</span><span class="sxs-lookup"><span data-stu-id="d6b4e-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="d6b4e-121">游標</span><span class="sxs-lookup"><span data-stu-id="d6b4e-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d6b4e-122">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="d6b4e-122">Head-gaze and commit</span></span>](gaze-and-commit.md)
