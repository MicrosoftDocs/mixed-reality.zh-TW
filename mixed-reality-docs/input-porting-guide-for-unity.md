---
title: 移植指南 Unity 的輸入
description: 了解如何處理在 Unity 中的 Windows Mixed Reality 的輸入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 輸入、 unity 移植
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595726"
---
# <a name="input-porting-guide-for-unity"></a><span data-ttu-id="ccdc6-104">移植指南 Unity 的輸入</span><span class="sxs-lookup"><span data-stu-id="ccdc6-104">Input porting guide for Unity</span></span>

<span data-ttu-id="ccdc6-105">您可以移植到 Windows 混和實境使用兩個方法之一，Unity 的一般 Input.GetButton/GetAxis Api，跨越多個平台或 Windows 特定 XR 您輸入的邏輯。WSA。輸入提供更豐富的資料，專為動作控制站和 HoloLens 實際操作的 Api。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-105">You can port your input logic to Windows Mixed Reality using one of two approaches, Unity's general Input.GetButton/GetAxis APIs that span across multiple platforms, or the Windows-specific XR.WSA.Input APIs that offer richer data specifically for motion controllers and HoloLens hands.</span></span>

## <a name="general-inputgetbuttongetaxis-apis"></a><span data-ttu-id="ccdc6-106">一般 Input.GetButton/GetAxis Api</span><span class="sxs-lookup"><span data-stu-id="ccdc6-106">General Input.GetButton/GetAxis APIs</span></span>

<span data-ttu-id="ccdc6-107">Unity 目前會使用其一般的 Input.GetButton/Input.GetAxis Api 公開的輸入[Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)並[OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-107">Unity currently uses its general Input.GetButton/Input.GetAxis APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) and [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html).</span></span> <span data-ttu-id="ccdc6-108">如果您的應用程式已經在使用這些 Api 的輸入，這是最簡單的路徑，在 Windows Mixed Reality 中支援動作控制站： 您應該只需要重新對應按鈕與軸在輸入管理員。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-108">If your apps are already using these APIs for input, this is the easiest path for supporting motion controllers in Windows Mixed Reality: you should just need to remap buttons and axes in the Input Manager.</span></span>

<span data-ttu-id="ccdc6-109">如需詳細資訊，請參閱[Unity 按鈕/軸對應表](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)並[常見的 Unity Api 概觀](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-109">For more information, see the [Unity button/axis mapping table](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) and the [overview of the common Unity APIs](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).</span></span>

## <a name="windows-specific-xrwsainput-apis"></a><span data-ttu-id="ccdc6-110">Windows-specific XR.WSA.Input APIs</span><span class="sxs-lookup"><span data-stu-id="ccdc6-110">Windows-specific XR.WSA.Input APIs</span></span>

<span data-ttu-id="ccdc6-111">如果您的應用程式已建置自訂的輸入的邏輯，每個平台，您可以選擇使用空間輸入的 Windows 特定的 Api 之下**UnityEngine.XR.WSA.Input**命名空間。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-111">If your app already builds custom input logic for each platform, you can choose to use the Windows-specific spatial input APIs under the **UnityEngine.XR.WSA.Input** namespace.</span></span> <span data-ttu-id="ccdc6-112">這可讓您存取其他資訊，例如位置精確度或的來源類型，可讓您告訴雙手及相隔的控制站上 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-112">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart on HoloLens.</span></span>

<span data-ttu-id="ccdc6-113">如需詳細資訊，請參閱 < [UnityEngine.XR.WSA.Input Api 概觀](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-113">For more information, see the [overview of the UnityEngine.XR.WSA.Input APIs](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="ccdc6-114">指標的姿勢與的底框姿勢</span><span class="sxs-lookup"><span data-stu-id="ccdc6-114">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="ccdc6-115">Windows Mixed Reality 支援各種不同的外型規格中的動作控制站，與每個控制站設計不同使用者的手狀位置和 「 轉送 」 方向該應用程式的自然之間關聯性的相對值應該使用指出呈現時控制站。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-115">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="ccdc6-116">若要更能代表這些控制站，有兩種您可以進行互動的每個來源的調查會帶來：</span><span class="sxs-lookup"><span data-stu-id="ccdc6-116">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>

* <span data-ttu-id="ccdc6-117">**底框姿勢**，表示偵測到的 HoloLens，一隻手的或翲保存動作控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-117">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="ccdc6-118">沈浸式耳機，在此姿勢最適合用來呈現**使用者的手**或是**物件保留在使用者的手**劍或槍等。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-118">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="ccdc6-119">**抓住位置**:Palm 距心自然，保留控制器時調整左邊或右邊，置中的底框的位置。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-119">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="ccdc6-120">**抓住方向的右座標軸**:當您完全開啟以形成平坦的 5 手指姿勢手時，光線，一般是您 palm （從左 palm、 從右 palm 回溯順向）</span><span class="sxs-lookup"><span data-stu-id="ccdc6-120">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="ccdc6-121">**抓住方向的順向軸**:當您關閉您的手部分 （如同保存在控制站）、"forward"tube 透過由非 thumb 手指點光線。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-121">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="ccdc6-122">**抓住方向的總軸**:隱含的權限和轉送的定義總軸。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-122">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="ccdc6-123">您可以透過任一 Unity 的跨銷售商輸入的 API 來存取的底框姿勢 (**[XR。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation**) 或透過 Windows 特定 API (**sourceState.sourcePose.TryGetPosition/Rotation**，要求的底框姿勢)。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-123">You can access the grip pose through either Unity's cross-vendor input API (**[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation**) or through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Grip pose).</span></span>
* <span data-ttu-id="ccdc6-124">**指標姿勢**，代表向前指的控制站的提示。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-124">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="ccdc6-125">此姿勢最適合用於 raycast 時**指向 UI**當您要在其中呈現控制器模型本身。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-125">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="ccdc6-126">指標姿勢目前僅透過 Windows 特定的 API (**sourceState.sourcePose.TryGetPosition/Rotation**，要求指標姿勢)。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-126">Currently, the pointer pose is available only through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Pointer pose).</span></span>

<span data-ttu-id="ccdc6-127">這些座標會表示在 Unity 的全局座標的姿勢。</span><span class="sxs-lookup"><span data-stu-id="ccdc6-127">These pose coordinates are all expressed in Unity world coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccdc6-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccdc6-128">See also</span></span>
* [<span data-ttu-id="ccdc6-129">動作控制站</span><span class="sxs-lookup"><span data-stu-id="ccdc6-129">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="ccdc6-130">筆勢和 Unity 中的動作控制站</span><span class="sxs-lookup"><span data-stu-id="ccdc6-130">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="ccdc6-131">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="ccdc6-131">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="ccdc6-132">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="ccdc6-132">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="ccdc6-133">移植指南</span><span class="sxs-lookup"><span data-stu-id="ccdc6-133">Porting guides</span></span>](porting-guides.md)
