---
title: 物件集合
description: 「物件集合」是一種版面配置控制項，可協助您以預先定義的3d 圖形設定物件陣列。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，控制項，設計
ms.openlocfilehash: 8f3629c6d9465383efc901ed784a3719cd6fdfb2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438184"
---
# <a name="object-collection"></a><span data-ttu-id="66db3-104">物件集合</span><span class="sxs-lookup"><span data-stu-id="66db3-104">Object collection</span></span>

![在 Elements 應用程式的定期資料表中使用的物件集合](images/640px-objectcollection-hero-640px.jpg)<br>


<span data-ttu-id="66db3-106">「物件集合」是一種版面配置控制項，可協助您以預先定義的3d 圖形設定物件陣列。</span><span class="sxs-lookup"><span data-stu-id="66db3-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="66db3-107">它支援各種表面樣式-**平面、圓柱、球面**和**放射狀**。</span><span class="sxs-lookup"><span data-stu-id="66db3-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="66db3-108">您可以調整物件的半徑和大小，以及它們之間的空間。</span><span class="sxs-lookup"><span data-stu-id="66db3-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="66db3-109">物件集合支援來自 Unity 的任何物件-2D 和3D。</span><span class="sxs-lookup"><span data-stu-id="66db3-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="66db3-110">在 **[混合的現實工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** 組中，我們建立了 Unity 腳本和範例，可協助您建立物件集合。</span><span class="sxs-lookup"><span data-stu-id="66db3-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="66db3-111">物件集合範例</span><span class="sxs-lookup"><span data-stu-id="66db3-111">Object collection examples</span></span>

<span data-ttu-id="66db3-112">[元素的定期資料表](periodic-table-of-the-elements.md)是範例應用程式，可示範物件集合的運作方式。</span><span class="sxs-lookup"><span data-stu-id="66db3-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="66db3-113">它會使用物件集合來配置不同圖形中的3D 化學元素方塊。</span><span class="sxs-lookup"><span data-stu-id="66db3-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="66db3-114">專案應用程式的定期資料表中所顯示 ![物件集合範例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="66db3-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="66db3-115">*元素範例應用程式的定期資料表中所顯示的物件集合範例*</span><span class="sxs-lookup"><span data-stu-id="66db3-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="66db3-116">3D 物件</span><span class="sxs-lookup"><span data-stu-id="66db3-116">3D objects</span></span>

<span data-ttu-id="66db3-117">您可以使用物件集合來配置已匯入的3D 物件。</span><span class="sxs-lookup"><span data-stu-id="66db3-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="66db3-118">下列範例顯示一些3D 椅子物件的平面和圓柱版面配置。</span><span class="sxs-lookup"><span data-stu-id="66db3-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="66db3-119">![3D 物件的平面和圓柱版面配置範例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="66db3-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="66db3-120">*3D 物件的平面和圓柱版面配置範例*</span><span class="sxs-lookup"><span data-stu-id="66db3-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="66db3-121">2D 物件</span><span class="sxs-lookup"><span data-stu-id="66db3-121">2D objects</span></span>

<span data-ttu-id="66db3-122">您也可以使用2D 影像搭配物件集合。</span><span class="sxs-lookup"><span data-stu-id="66db3-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="66db3-123">下列範例會示範如何在方格中顯示2D 影像。</span><span class="sxs-lookup"><span data-stu-id="66db3-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![包含物件集合之2D 影像的範例](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="66db3-125">![具有物件集合之2D 影像的範例](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="66db3-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="66db3-126">*搭配2D 影像使用物件集合的範例*</span><span class="sxs-lookup"><span data-stu-id="66db3-126">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="66db3-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="66db3-127">See also</span></span>
* [<span data-ttu-id="66db3-128">GitHub 上混合現實工具組中物件集合的腳本和 prefabs</span><span class="sxs-lookup"><span data-stu-id="66db3-128">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="66db3-129">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="66db3-129">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="66db3-130">周框方塊</span><span class="sxs-lookup"><span data-stu-id="66db3-130">Bounding Box</span></span>](app-bar-and-bounding-box.md)
