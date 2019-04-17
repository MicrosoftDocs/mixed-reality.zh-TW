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
# <a name="gaze-in-unity"></a><span data-ttu-id="98a8c-104">在 Unity 視線</span><span class="sxs-lookup"><span data-stu-id="98a8c-104">Gaze in Unity</span></span>

<span data-ttu-id="98a8c-105">[視線](gaze.md)是主要的方法，讓使用者為目標[全像投影](hologram.md)您的應用程式中建立[混合實境](mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="98a8c-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [mixed reality](mixed-reality.md).</span></span>

## <a name="implementing-gaze"></a><span data-ttu-id="98a8c-106">實作視線</span><span class="sxs-lookup"><span data-stu-id="98a8c-106">Implementing Gaze</span></span>

<span data-ttu-id="98a8c-107">就概念而言，[視線](gaze.md)藉由將從耳機所在位置，正面臨並判斷使用者的標頭無限遠的光線投射光線與衝突代表什麼意思。</span><span class="sxs-lookup"><span data-stu-id="98a8c-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="98a8c-108">在 Unity 中，使用者的前端的位置和方向透過 Unity 主要公開[相機](camera-in-unity.md)，特別[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)並[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="98a8c-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="98a8c-109">呼叫[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)導致[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)結構也包含資訊包括 3D 點發生衝突的衝突及其他 GameObject 視線光線衝突。</span><span class="sxs-lookup"><span data-stu-id="98a8c-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-gaze"></a><span data-ttu-id="98a8c-110">範例：實作視線</span><span class="sxs-lookup"><span data-stu-id="98a8c-110">Example: Implement Gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="98a8c-111">最佳做法</span><span class="sxs-lookup"><span data-stu-id="98a8c-111">Best Practices</span></span>

<span data-ttu-id="98a8c-112">雖然上述範例示範如何更新迴圈來尋找視線目標的單一 raycast，建議在單一物件管理而不是這麼做可能會想要在正在 gazed 物件中的任何物件的視線中這麼做。</span><span class="sxs-lookup"><span data-stu-id="98a8c-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="98a8c-113">這可讓您執行每個畫面格的一個視線 raycast 儲存處理的應用程式。</span><span class="sxs-lookup"><span data-stu-id="98a8c-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="98a8c-114">視覺化視線</span><span class="sxs-lookup"><span data-stu-id="98a8c-114">Visualizing Gaze</span></span>

<span data-ttu-id="98a8c-115">就像在桌面上，使用滑鼠指標來為目標並進行互動使用內容，您應該實作[游標](cursors.md)，代表使用者的視線。</span><span class="sxs-lookup"><span data-stu-id="98a8c-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="98a8c-116">這讓使用者的信心，在即將要進行互動。</span><span class="sxs-lookup"><span data-stu-id="98a8c-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit"></a><span data-ttu-id="98a8c-117">視線混合的實境工具組中</span><span class="sxs-lookup"><span data-stu-id="98a8c-117">Gaze in Mixed Reality Toolkit</span></span>
<span data-ttu-id="98a8c-118">當您匯入[MRTK 發行 Unity 套件](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或從專案複製[GitHub 存放庫](https://github.com/Microsoft/MixedRealityToolkit-Unity)，您要在 Unity 中尋找新的功能表 ' 混合實境 Toolkit'。</span><span class="sxs-lookup"><span data-stu-id="98a8c-118">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="98a8c-119">在 [設定] 功能表上，您會看到功能表 [適用於混合實境場景設定]。</span><span class="sxs-lookup"><span data-stu-id="98a8c-119">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="98a8c-120">當您按一下它時，它會移除預設相機，並新增基本元件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，並[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。</span><span class="sxs-lookup"><span data-stu-id="98a8c-120">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="98a8c-121">![MRTK 場景設定功能表](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="98a8c-121">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="98a8c-122">*MRTK 場景設定功能表*</span><span class="sxs-lookup"><span data-stu-id="98a8c-122">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="98a8c-123">![自動的場景中 MRTK 的安裝程式](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="98a8c-123">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="98a8c-124">*自動的場景中 MRTK 的安裝程式*</span><span class="sxs-lookup"><span data-stu-id="98a8c-124">*Automatic scene setup in MRTK*</span></span>

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a><span data-ttu-id="98a8c-125">視線混合實境工具組中的相關指令碼</span><span class="sxs-lookup"><span data-stu-id="98a8c-125">Gaze related scripts in Mixed Reality Toolkit</span></span>
<span data-ttu-id="98a8c-126">混合實境工具組包含 InputManager prefab [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs)並[視線對](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs)。</span><span class="sxs-lookup"><span data-stu-id="98a8c-126">Mixed Reality Toolkit's InputManager prefab includes [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) and [Gaze Stabilizer](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span></span> <span data-ttu-id="98a8c-127">底下[SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs)，您可以指派您自訂的資料指標。</span><span class="sxs-lookup"><span data-stu-id="98a8c-127">Under [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), you can assign your custom Cursor.</span></span> <span data-ttu-id="98a8c-128">在預設情況下，動畫[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)指派。</span><span class="sxs-lookup"><span data-stu-id="98a8c-128">In default, animated [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) is assigned.</span></span>

<span data-ttu-id="98a8c-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)並[CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)示範如何以視覺化方式檢視您的視線使用資料指標。</span><span class="sxs-lookup"><span data-stu-id="98a8c-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) and [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) shows you how to visualize your Gaze using Cursors.</span></span>

## <a name="see-also"></a><span data-ttu-id="98a8c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98a8c-130">See also</span></span>
* [<span data-ttu-id="98a8c-131">相機</span><span class="sxs-lookup"><span data-stu-id="98a8c-131">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="98a8c-132">Gaze</span><span class="sxs-lookup"><span data-stu-id="98a8c-132">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="98a8c-133">資料指標</span><span class="sxs-lookup"><span data-stu-id="98a8c-133">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="98a8c-134">為目標的視線</span><span class="sxs-lookup"><span data-stu-id="98a8c-134">Gaze targeting</span></span>](gaze-targeting.md)
