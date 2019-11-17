---
title: 物件集合
description: 「物件集合」是一種版面配置控制項，可協助您以預先定義的3d 圖形設定物件陣列。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，控制項，設計
ms.openlocfilehash: 9a111fcbe4c49972cc5ef22fb647f89544188af5
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143151"
---
# <a name="object-collection"></a><span data-ttu-id="36bfb-104">物件集合</span><span class="sxs-lookup"><span data-stu-id="36bfb-104">Object collection</span></span>

![在 Elements 應用程式的定期資料表中使用的物件集合](images/UX/UX_Hero_ObjectCollection.jpg)<br>


<span data-ttu-id="36bfb-106">「物件集合」是一種版面配置控制項，可協助您以預先定義的3d 圖形設定物件陣列。</span><span class="sxs-lookup"><span data-stu-id="36bfb-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="36bfb-107">它支援各種表面樣式-**平面、圓柱、球面**和**放射狀**。</span><span class="sxs-lookup"><span data-stu-id="36bfb-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="36bfb-108">您可以調整物件的半徑和大小，以及它們之間的空間。</span><span class="sxs-lookup"><span data-stu-id="36bfb-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="36bfb-109">物件集合支援來自 Unity 的任何物件-2D 和3D。</span><span class="sxs-lookup"><span data-stu-id="36bfb-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="36bfb-110">在 **[混合的現實工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** 組中，我們建立了 Unity 腳本和範例，可協助您建立物件集合。</span><span class="sxs-lookup"><span data-stu-id="36bfb-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="36bfb-111">物件集合範例</span><span class="sxs-lookup"><span data-stu-id="36bfb-111">Object collection examples</span></span>

<span data-ttu-id="36bfb-112">[元素的定期資料表](periodic-table-of-the-elements.md)是範例應用程式，可示範物件集合的運作方式。</span><span class="sxs-lookup"><span data-stu-id="36bfb-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="36bfb-113">它會使用物件集合來配置不同圖形中的3D 化學元素方塊。</span><span class="sxs-lookup"><span data-stu-id="36bfb-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="36bfb-114">專案應用程式的定期資料表中所顯示 ![物件集合範例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="36bfb-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="36bfb-115">*元素範例應用程式的定期資料表中所顯示的物件集合範例*</span><span class="sxs-lookup"><span data-stu-id="36bfb-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="36bfb-116">3D 物件</span><span class="sxs-lookup"><span data-stu-id="36bfb-116">3D objects</span></span>

<span data-ttu-id="36bfb-117">您可以使用物件集合來配置已匯入的3D 物件。</span><span class="sxs-lookup"><span data-stu-id="36bfb-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="36bfb-118">下列範例顯示一些3D 椅子物件的平面和圓柱版面配置。</span><span class="sxs-lookup"><span data-stu-id="36bfb-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="36bfb-119">![3D 物件的平面和圓柱版面配置範例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="36bfb-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="36bfb-120">*3D 物件的平面和圓柱版面配置範例*</span><span class="sxs-lookup"><span data-stu-id="36bfb-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="36bfb-121">2D 物件</span><span class="sxs-lookup"><span data-stu-id="36bfb-121">2D objects</span></span>

<span data-ttu-id="36bfb-122">您也可以使用2D 影像搭配物件集合。</span><span class="sxs-lookup"><span data-stu-id="36bfb-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="36bfb-123">下列範例會示範如何在方格中顯示2D 影像。</span><span class="sxs-lookup"><span data-stu-id="36bfb-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![包含物件集合之2D 影像的範例](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="36bfb-125">![具有物件集合之2D 影像的範例](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="36bfb-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="36bfb-126">*搭配2D 影像使用物件集合的範例*</span><span class="sxs-lookup"><span data-stu-id="36bfb-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="36bfb-127">適用于 Unity 的 MRTK （混合現實工具組）中的物件集合</span><span class="sxs-lookup"><span data-stu-id="36bfb-127">Object collection in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="36bfb-128">MRTK-物件集合</span><span class="sxs-lookup"><span data-stu-id="36bfb-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="36bfb-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="36bfb-129">See also</span></span>

* [<span data-ttu-id="36bfb-130">游標</span><span class="sxs-lookup"><span data-stu-id="36bfb-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="36bfb-131">手型光線</span><span class="sxs-lookup"><span data-stu-id="36bfb-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="36bfb-132">Button</span><span class="sxs-lookup"><span data-stu-id="36bfb-132">Button</span></span>](button.md)
* [<span data-ttu-id="36bfb-133">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="36bfb-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="36bfb-134">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="36bfb-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="36bfb-135">處理</span><span class="sxs-lookup"><span data-stu-id="36bfb-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="36bfb-136">手部功能表</span><span class="sxs-lookup"><span data-stu-id="36bfb-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="36bfb-137">近端功能表</span><span class="sxs-lookup"><span data-stu-id="36bfb-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="36bfb-138">物件集合</span><span class="sxs-lookup"><span data-stu-id="36bfb-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="36bfb-139">語音命令</span><span class="sxs-lookup"><span data-stu-id="36bfb-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="36bfb-140">鍵盤</span><span class="sxs-lookup"><span data-stu-id="36bfb-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="36bfb-141">並用</span><span class="sxs-lookup"><span data-stu-id="36bfb-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="36bfb-142">石板</span><span class="sxs-lookup"><span data-stu-id="36bfb-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="36bfb-143">滑桿</span><span class="sxs-lookup"><span data-stu-id="36bfb-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="36bfb-144">器</span><span class="sxs-lookup"><span data-stu-id="36bfb-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="36bfb-145">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="36bfb-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="36bfb-146">顯示進度</span><span class="sxs-lookup"><span data-stu-id="36bfb-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="36bfb-147">表面磁性</span><span class="sxs-lookup"><span data-stu-id="36bfb-147">Surface magnetism</span></span>](surface-magnetism.md)
