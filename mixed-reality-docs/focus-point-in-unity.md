---
title: 在 Unity 中的焦點
description: 以手動方式設定焦點調整在 Unity 的全像穩定性
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 焦點、 焦點平面、 穩定平面、 穩定點、 reprojection、 LSR、 深度緩衝區
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597038"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="bf282-104">在 Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="bf282-104">Focus point in Unity</span></span>

<span data-ttu-id="bf282-105">\**命名空間：\*\*\*UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="bf282-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="bf282-106">**類型**：*HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="bf282-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="bf282-107">[專注點](hologram-stability.md#stabilization-plane)可以設為提供 HoloLens 有關如何以最適合目前在全像投影執行穩定的提示所顯示。</span><span class="sxs-lookup"><span data-stu-id="bf282-107">The [focus point](hologram-stability.md#stabilization-plane) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="bf282-108">如果您想要將焦點設定在 Unity 中，它必須設定使用每框架*HolographicSettings.SetFocusPointForFrame()*。</span><span class="sxs-lookup"><span data-stu-id="bf282-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="bf282-109">如果未設定焦點的框架，將會使用預設穩定平面。</span><span class="sxs-lookup"><span data-stu-id="bf282-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="bf282-110">根據預設，新的 Unity 專案已設定的 [啟用深度緩衝區共用] 選項。</span><span class="sxs-lookup"><span data-stu-id="bf282-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="bf282-111">使用此選項，在沉浸式桌面耳機或執行 Windows 的 HoloLens 上執行的 Unity 應用程式 10 April 2018 Update (RS4) 或更新版本會送出您的深度緩衝區，以自動將最佳化全像穩定性，而您的應用程式指定的 Windows焦點：</span><span class="sxs-lookup"><span data-stu-id="bf282-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="bf282-112">在沉浸式桌面耳機，這可讓每一像素深度型 reprojection。</span><span class="sxs-lookup"><span data-stu-id="bf282-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="bf282-113">HoloLens 上執行 Windows 10 April 2018 Update 或更新版本中，這將會分析自動挑選最佳的穩定平面深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bf282-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="bf282-114">兩種方法應該提供更好的影像品質，而不需要明確的工作由您的應用程式，以選取婧鎏鶗懘每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="bf282-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="bf282-115">請注意，如果您以手動方式提供婧鎏鶗懘，將會覆寫自動上面所述的行為，通常會減少闀穩定性。</span><span class="sxs-lookup"><span data-stu-id="bf282-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="bf282-116">一般而言，您才應該指定手動鶗懘尚未更新至 Windows HoloLens 上執行您的應用程式時 10 April 2018 Update。</span><span class="sxs-lookup"><span data-stu-id="bf282-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="bf282-117">範例</span><span class="sxs-lookup"><span data-stu-id="bf282-117">Example</span></span>

<span data-ttu-id="bf282-118">有許多方法可設定焦點，所提供的多載建議*SetFocusPointForFrame*靜態函式。</span><span class="sxs-lookup"><span data-stu-id="bf282-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="bf282-119">下列是將焦點平面設定所提供的物件為每個畫面的簡單範例：</span><span class="sxs-lookup"><span data-stu-id="bf282-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="bf282-120">請注意，上述的簡單程式碼可能會得到減少闀穩定性，如果具有焦點的物件最後背後的使用者。</span><span class="sxs-lookup"><span data-stu-id="bf282-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="bf282-121">這就是為什麼一般來說，您應該設定 「 啟用深度緩衝區共用 」 而不是以手動方式指定婧鎏鶗懘。</span><span class="sxs-lookup"><span data-stu-id="bf282-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="bf282-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf282-122">See also</span></span>
* [<span data-ttu-id="bf282-123">穩定平面</span><span class="sxs-lookup"><span data-stu-id="bf282-123">Stabilization plane</span></span>](hologram-stability.md#stabilization-plane)
