---
title: Unity 中的焦點點
description: 藉由設定焦點點, 手動調整 Unity 中的全息影像穩定性
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 焦點點, 焦點平面, 穩定平面, 穩定點, reprojection, LSR, 深度緩衝區
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525466"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="8b6ae-104">Unity 中的焦點點</span><span class="sxs-lookup"><span data-stu-id="8b6ae-104">Focus point in Unity</span></span>

<span data-ttu-id="8b6ae-105">**命名空間：**  *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="8b6ae-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="8b6ae-106">**類型**：*HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="8b6ae-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="8b6ae-107">您可以將[焦點](hologram-stability.md#stabilization-plane)設定為提供 HoloLens 提示, 告訴您如何在目前顯示的全息影像上, 最佳執行穩定。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-107">The [focus point](hologram-stability.md#stabilization-plane) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="8b6ae-108">如果您想要在 Unity 中設定焦點, 則必須使用*HolographicSettings. SetFocusPointForFrame ()* 來設定每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="8b6ae-109">如果沒有為框架設定焦點, 則會使用預設的穩定平面。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="8b6ae-110">根據預設, 新的 Unity 專案會設定 [啟用深度緩衝區共用] 選項。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="8b6ae-111">使用此選項時, 在沉浸式桌面耳機上執行的 Unity 應用程式或執行 Windows 10 四月份2018更新 (RS4) 或更新版本的 HoloLens 會將您的深度緩衝區提交至 Windows, 以自動將您的「影像」穩定性優化, 而不需要您的應用程式指定焦點點:</span><span class="sxs-lookup"><span data-stu-id="8b6ae-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="8b6ae-112">在沉浸式桌面耳機上, 這會啟用以圖元為基礎的深度 reprojection。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="8b6ae-113">在執行 Windows 10 2018 年4月更新 (含) 以後版本的 HoloLens 上, 這會分析深度緩衝區, 以自動挑選最佳穩定平面。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="8b6ae-114">這兩種方法都應該提供更好的影像品質, 而不需要由您的應用程式進行明確的工作, 就能選取每個畫面</span><span class="sxs-lookup"><span data-stu-id="8b6ae-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="8b6ae-115">請注意, 如果您手動提供焦點, 這會覆寫上述的自動行為, 而且通常會減少全息影像的穩定性。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="8b6ae-116">一般而言, 當您的應用程式在尚未更新為 Windows 10 2018 年4月更新的 HoloLens 上執行時, 您應該只指定手動焦點點。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="8b6ae-117">範例</span><span class="sxs-lookup"><span data-stu-id="8b6ae-117">Example</span></span>

<span data-ttu-id="8b6ae-118">有許多方式可設定焦點, 如*SetFocusPointForFrame*靜態函式上提供的多載所建議。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="8b6ae-119">以下是簡單的範例, 可將焦點平面設定為每個框架所提供的物件:</span><span class="sxs-lookup"><span data-stu-id="8b6ae-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

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

<span data-ttu-id="8b6ae-120">請注意, 上述的簡單程式碼可能會在焦點物件最後出現在使用者後方時, 減少全息影像的穩定性。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="8b6ae-121">這就是為什麼您通常應該設定「啟用深度緩衝區共用」, 而不是手動指定焦點。</span><span class="sxs-lookup"><span data-stu-id="8b6ae-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="8b6ae-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b6ae-122">See also</span></span>
* [<span data-ttu-id="8b6ae-123">穩定平面</span><span class="sxs-lookup"><span data-stu-id="8b6ae-123">Stabilization plane</span></span>](hologram-stability.md#stabilization-plane)
