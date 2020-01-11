---
title: 器
description: MRTK Standard 著色器提供各種類型的視覺效果，可與全息影像搭配使用。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、ui、ux
ms.openlocfilehash: 8d0e01bb26347d95a80703884c4e9408653e03ed
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901452"
---
# <a name="shader"></a><span data-ttu-id="63498-104">器</span><span class="sxs-lookup"><span data-stu-id="63498-104">Shader</span></span>

![器](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="63498-106">由於全息型物件與實際環境中的實體不同，因此請務必向使用者提供視覺提示。</span><span class="sxs-lookup"><span data-stu-id="63498-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="63498-107">MRTK Standard 著色器提供各種類型的視覺效果，可與全息影像搭配使用。</span><span class="sxs-lookup"><span data-stu-id="63498-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="63498-108">MRTK 標準陰影系統利用單一、彈性的著色器，可達成類似 Unity 標準著色器的視覺效果、實行[流暢的設計系統原則](https://www.microsoft.com/design/fluent/#/)，並在混合現實裝置上保持高效能。</span><span class="sxs-lookup"><span data-stu-id="63498-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="63498-109">使用 MRTK 標準著色器的視覺效果範例</span><span class="sxs-lookup"><span data-stu-id="63498-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="63498-110">![移動](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="63498-110">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="63498-111">**近光源**</span><span class="sxs-lookup"><span data-stu-id="63498-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="63498-112">![旋轉](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="63498-112">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="63498-113">**框線亮度**</span><span class="sxs-lookup"><span data-stu-id="63498-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="63498-114">適用于 Unity 的 MRTK （混合現實工具組）中的 MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="63498-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="63498-115">MRTK-標準著色器</span><span class="sxs-lookup"><span data-stu-id="63498-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="63498-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="63498-116">See also</span></span>

* [<span data-ttu-id="63498-117">游標</span><span class="sxs-lookup"><span data-stu-id="63498-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="63498-118">手部光線</span><span class="sxs-lookup"><span data-stu-id="63498-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="63498-119">Button</span><span class="sxs-lookup"><span data-stu-id="63498-119">Button</span></span>](button.md)
* [<span data-ttu-id="63498-120">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="63498-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="63498-121">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="63498-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="63498-122">操作</span><span class="sxs-lookup"><span data-stu-id="63498-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="63498-123">手部功能表</span><span class="sxs-lookup"><span data-stu-id="63498-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="63498-124">近端功能表</span><span class="sxs-lookup"><span data-stu-id="63498-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="63498-125">物件集合</span><span class="sxs-lookup"><span data-stu-id="63498-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="63498-126">語音命令</span><span class="sxs-lookup"><span data-stu-id="63498-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="63498-127">鍵盤</span><span class="sxs-lookup"><span data-stu-id="63498-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="63498-128">工具提示</span><span class="sxs-lookup"><span data-stu-id="63498-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="63498-129">平板</span><span class="sxs-lookup"><span data-stu-id="63498-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="63498-130">滑桿</span><span class="sxs-lookup"><span data-stu-id="63498-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="63498-131">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="63498-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="63498-132">顯示進度</span><span class="sxs-lookup"><span data-stu-id="63498-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="63498-133">表面磁性</span><span class="sxs-lookup"><span data-stu-id="63498-133">Surface magnetism</span></span>](surface-magnetism.md)
