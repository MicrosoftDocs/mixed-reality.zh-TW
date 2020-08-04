---
title: 入門教學課程 - 3。 設定 MRTK 設定檔
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d3381241bb1418fb0e1fb7e5d29d552a533faa32
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376640"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="85ce9-105">3.設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="85ce9-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="85ce9-106">概觀</span><span class="sxs-lookup"><span data-stu-id="85ce9-106">Overview</span></span>

<span data-ttu-id="85ce9-107">在本教學課程中，您將了解如何自訂和設定 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="85ce9-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="85ce9-108">此特定範例將示範如何藉由變更空間網格觀察器的設定，來隱藏空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="85ce9-108">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="85ce9-109">不過，您也可以遵循這些相同原則，自訂 MRTK 設定檔中的任何設定或值。</span><span class="sxs-lookup"><span data-stu-id="85ce9-109">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

## <a name="objectives"></a><span data-ttu-id="85ce9-110">目標</span><span class="sxs-lookup"><span data-stu-id="85ce9-110">Objectives</span></span>

* <span data-ttu-id="85ce9-111">了解如何自訂和設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="85ce9-111">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="85ce9-112">隱藏空間感知網格</span><span class="sxs-lookup"><span data-stu-id="85ce9-112">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="85ce9-113">變更空間感知顯示選項</span><span class="sxs-lookup"><span data-stu-id="85ce9-113">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="85ce9-114">隱藏空間感知網格所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="85ce9-114">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="85ce9-115">複製預設的組態設定檔</span><span class="sxs-lookup"><span data-stu-id="85ce9-115">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="85ce9-116">啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="85ce9-116">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="85ce9-117">複製預設的空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="85ce9-117">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="85ce9-118">複製預設的空間感知網格觀察器設定檔</span><span class="sxs-lookup"><span data-stu-id="85ce9-118">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="85ce9-119">變更空間感知網格的顯示</span><span class="sxs-lookup"><span data-stu-id="85ce9-119">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="85ce9-120">根據預設，您無法編輯 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="85ce9-120">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="85ce9-121">這些是預設的設定檔範本，您必須先加以複製，才能進行編輯。</span><span class="sxs-lookup"><span data-stu-id="85ce9-121">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="85ce9-122">其中有數個巢狀的設定檔層。</span><span class="sxs-lookup"><span data-stu-id="85ce9-122">There are several nested layers of profiles.</span></span> <span data-ttu-id="85ce9-123">因此，在設定一個或多個設定時，通常會複製及編輯數個設定檔。</span><span class="sxs-lookup"><span data-stu-id="85ce9-123">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="85ce9-124">1.複製預設的組態設定檔</span><span class="sxs-lookup"><span data-stu-id="85ce9-124">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="85ce9-125">組態設定檔是最上層的設定檔。</span><span class="sxs-lookup"><span data-stu-id="85ce9-125">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="85ce9-126">因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。</span><span class="sxs-lookup"><span data-stu-id="85ce9-126">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="85ce9-127">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，將 **MixedRealityToolkit** 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="85ce9-127">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="85ce9-129">在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂] 按鈕來開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="85ce9-129">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="85ce9-131">在 [複製設定檔] 視窗中，輸入適當的**設定檔名稱**，例如 _GettingStarted_HoloLens2ConfigurationProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultHololens2ConfigurationProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="85ce9-131">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="85ce9-133">新建立的組態設定檔現在已指派為您場景的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="85ce9-133">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="85ce9-135">在 Unity 功能表中，選取 [檔案] > [儲存]，即可儲存場景。</span><span class="sxs-lookup"><span data-stu-id="85ce9-135">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="85ce9-136">請記得在整個教學課程中儲存工作。</span><span class="sxs-lookup"><span data-stu-id="85ce9-136">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="85ce9-137">2.啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="85ce9-137">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="85ce9-138">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中選取 [空間感知] 索引標籤，然後勾選 [啟用空間感知系統] 核取方塊：</span><span class="sxs-lookup"><span data-stu-id="85ce9-138">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="85ce9-140">3.複製預設的空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="85ce9-140">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="85ce9-141">在 [空間感知] 索引標籤中，按一下 [複製] 按鈕以開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="85ce9-141">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="85ce9-143">在 [複製設定檔] 視窗中，輸入適當的**設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessSystemProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="85ce9-143">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="85ce9-145">新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="85ce9-145">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="85ce9-147">4.複製預設的空間感知網格觀察器設定檔</span><span class="sxs-lookup"><span data-stu-id="85ce9-147">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="85ce9-148">在仍選取 [空間感知] 索引標籤的情況下，展開 [Windows Mixed Reality 空間網格觀察器] 區段，然後按一下 [複製] 按鈕來開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="85ce9-148">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="85ce9-150">在 [複製設定檔] 視窗中，輸入適當的**設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="85ce9-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="85ce9-152">新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：</span><span class="sxs-lookup"><span data-stu-id="85ce9-152">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="85ce9-154">5.變更空間感知網格的顯示</span><span class="sxs-lookup"><span data-stu-id="85ce9-154">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="85ce9-155">在 [空間網格觀察器設定] 中，將 [顯示選項] 變更為 [遮蔽]，以隱藏仍在運作的空間對應網格：</span><span class="sxs-lookup"><span data-stu-id="85ce9-155">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="85ce9-157">雖然空間對應網格看不到，但仍存在且正常運作。</span><span class="sxs-lookup"><span data-stu-id="85ce9-157">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="85ce9-158">例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="85ce9-158">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="85ce9-159">您方才已了解如何修改 MRTK 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="85ce9-159">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="85ce9-160">如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。</span><span class="sxs-lookup"><span data-stu-id="85ce9-160">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="85ce9-161">由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。</span><span class="sxs-lookup"><span data-stu-id="85ce9-161">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="85ce9-162">若要深入了解 MRTK 設定檔及其架構，您可以參閱 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的 [MRTK 設定檔設定指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。</span><span class="sxs-lookup"><span data-stu-id="85ce9-162">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="85ce9-163">恭喜！</span><span class="sxs-lookup"><span data-stu-id="85ce9-163">Congratulations</span></span>

<span data-ttu-id="85ce9-164">在本教學課程中，您已了解如何複製、自訂和設定 MRTK 設定檔和設定。</span><span class="sxs-lookup"><span data-stu-id="85ce9-164">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

[<span data-ttu-id="85ce9-165">下一個教學課程：4.將物件置放在場景中</span><span class="sxs-lookup"><span data-stu-id="85ce9-165">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
