---
title: 物件集合
description: 物件的集合是可協助您配置的預先定義的 3d 圖形中的物件陣列的版面配置控制項。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，控制項設計
ms.openlocfilehash: 88ab0359d5083d43d5d6312ef1185f67ca0caa7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597090"
---
# <a name="object-collection"></a><span data-ttu-id="0a3da-104">物件集合</span><span class="sxs-lookup"><span data-stu-id="0a3da-104">Object collection</span></span>

<span data-ttu-id="0a3da-105">物件的集合是可協助您配置的預先定義的 3d 圖形中的物件陣列的版面配置控制項。</span><span class="sxs-lookup"><span data-stu-id="0a3da-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="0a3da-106">它支援四個不同的介面樣式-**平面、 圓柱，球體**並**散佈**。</span><span class="sxs-lookup"><span data-stu-id="0a3da-106">It supports four different surface styles - **plane, cylinder, sphere** and **scatter**.</span></span> <span data-ttu-id="0a3da-107">您可以調整的 radius 和大小的物件以及它們之間的空間。</span><span class="sxs-lookup"><span data-stu-id="0a3da-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="0a3da-108">物件的集合支援 Unity-2D 和 3D 中的任何物件。</span><span class="sxs-lookup"><span data-stu-id="0a3da-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="0a3da-109">在  **[混合實境 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**，我們已經建立 Unity 指令碼和[範例場景](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity)幫助您建立的物件集合。</span><span class="sxs-lookup"><span data-stu-id="0a3da-109">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, we have created Unity script and [example scene](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) that will help you create an object collection.</span></span>

<span data-ttu-id="0a3da-110">![定期表格的項目應用程式中使用的物件集合](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a3da-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="0a3da-111">*定期表格的項目範例應用程式中使用的物件集合*</span><span class="sxs-lookup"><span data-stu-id="0a3da-111">*Object collection used in the Periodic Table of the Elements sample app*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="0a3da-112">物件集合範例</span><span class="sxs-lookup"><span data-stu-id="0a3da-112">Object collection examples</span></span>

<span data-ttu-id="0a3da-113">[項目的周期資料表](periodic-table-of-the-elements.md)示範物件集合的運作方式的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="0a3da-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="0a3da-114">它會使用物件集合中不同的圖案的 3D 的化學項目方塊版面配置。</span><span class="sxs-lookup"><span data-stu-id="0a3da-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="0a3da-115">![顯示項目的應用程式的定期資料表中的物件集合範例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a3da-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="0a3da-116">*項目範例應用程式定期表所示的物件集合範例*</span><span class="sxs-lookup"><span data-stu-id="0a3da-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="0a3da-117">3D 物件</span><span class="sxs-lookup"><span data-stu-id="0a3da-117">3D objects</span></span>

<span data-ttu-id="0a3da-118">若要匯入 3D 物件的版面配置設定，您可以使用物件集合。</span><span class="sxs-lookup"><span data-stu-id="0a3da-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="0a3da-119">下列範例會示範平面和某些 3D 的椅子物件的磁柱版面配置。</span><span class="sxs-lookup"><span data-stu-id="0a3da-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="0a3da-120">![平面與圓柱的版面配置的 3D 物件的範例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a3da-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="0a3da-121">*平面與圓柱的版面配置的 3D 物件的範例*</span><span class="sxs-lookup"><span data-stu-id="0a3da-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="0a3da-122">2D 物件</span><span class="sxs-lookup"><span data-stu-id="0a3da-122">2D objects</span></span>

<span data-ttu-id="0a3da-123">您也可以使用的 2D 影像與物件集合。</span><span class="sxs-lookup"><span data-stu-id="0a3da-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="0a3da-124">下列範例會示範如何 2D 映像可以顯示在方格中。</span><span class="sxs-lookup"><span data-stu-id="0a3da-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![物件集合的 2D 影像的範例](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="0a3da-126">![物件集合的 2D 影像的範例](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a3da-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="0a3da-127">*物件集合的 2D 影像的範例*</span><span class="sxs-lookup"><span data-stu-id="0a3da-127">*Examples of 2D images with object collection*</span></span>

## <a name="see-also"></a><span data-ttu-id="0a3da-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a3da-128">See also</span></span>
* [<span data-ttu-id="0a3da-129">指令碼和 GitHub 上的混合實境工具組中的物件集合的 prefabs</span><span class="sxs-lookup"><span data-stu-id="0a3da-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)
* [<span data-ttu-id="0a3da-130">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="0a3da-130">Interactable object</span></span>](interactable-object.md)
