---
title: 入門教學課程 - 3。 建立使用者介面並設定混合實境工具組
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376135"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="3eec2-105">3.建立使用者介面並設定混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="3eec2-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="3eec2-106">在上一個教學課程中，您已藉由啟動 HoloLens 2 的第一個應用程式來了解混合實境工具組 (MRTK) 所必須提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="3eec2-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="3eec2-107">在此教學課程中，您將了解如何建立和組織按鈕及 UI 文字面板，並且會使用預設互動方式 (觸控) 來與每個按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="3eec2-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="3eec2-108">此外，您還會探索如何新增簡單的動作和效果，例如變更物件的大小、音效和色彩。</span><span class="sxs-lookup"><span data-stu-id="3eec2-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="3eec2-109">此課程模組將會從關閉[空間對應](spatial-mapping.md)的網格視覺效果開始，介紹有關修改 MRTK 設定檔的基本概念。</span><span class="sxs-lookup"><span data-stu-id="3eec2-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="3eec2-110">目標</span><span class="sxs-lookup"><span data-stu-id="3eec2-110">Objectives</span></span>

* <span data-ttu-id="3eec2-111">自訂和設定混合實境工具組設定檔</span><span class="sxs-lookup"><span data-stu-id="3eec2-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="3eec2-112">使用 UI 元素和按鈕來與全像投影互動</span><span class="sxs-lookup"><span data-stu-id="3eec2-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="3eec2-113">基本的「手部追蹤」輸入和互動</span><span class="sxs-lookup"><span data-stu-id="3eec2-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="3eec2-114">如何設定混合實境工具組設定檔 (變更空間感知顯示選項)</span><span class="sxs-lookup"><span data-stu-id="3eec2-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="3eec2-115">在本節中，您將了解如何自訂和設定預設的 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="3eec2-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="3eec2-116">此特定範例將示範如何藉由變更空間網格觀察器的設定，來隱藏空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="3eec2-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="3eec2-117">不過，您也可以遵循這些相同原則，自訂 MRTK 設定檔中的任何設定或值。</span><span class="sxs-lookup"><span data-stu-id="3eec2-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="3eec2-118">隱藏空間感知網格所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="3eec2-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="3eec2-119">複製預設的組態設定檔</span><span class="sxs-lookup"><span data-stu-id="3eec2-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="3eec2-120">啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="3eec2-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="3eec2-121">複製預設的空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="3eec2-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="3eec2-122">複製預設的空間感知網格觀察器設定檔</span><span class="sxs-lookup"><span data-stu-id="3eec2-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="3eec2-123">變更空間感知網格的顯示</span><span class="sxs-lookup"><span data-stu-id="3eec2-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="3eec2-124">根據預設，您無法編輯 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="3eec2-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="3eec2-125">這些是預設的設定檔範本，您必須先加以複製，才能進行編輯。</span><span class="sxs-lookup"><span data-stu-id="3eec2-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="3eec2-126">其中有數個巢狀的設定檔層。</span><span class="sxs-lookup"><span data-stu-id="3eec2-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="3eec2-127">因此，在設定一個或多個設定時，通常會複製及編輯數個設定檔。</span><span class="sxs-lookup"><span data-stu-id="3eec2-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="3eec2-128">1.複製預設的組態設定檔</span><span class="sxs-lookup"><span data-stu-id="3eec2-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="3eec2-129">組態設定檔是最上層的設定檔。</span><span class="sxs-lookup"><span data-stu-id="3eec2-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="3eec2-130">因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。</span><span class="sxs-lookup"><span data-stu-id="3eec2-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="3eec2-131">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件之後，於 [偵測器] 視窗中，將混合實境工具組的**組態設定檔**變更為 **DefaultHoloLens2ConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="3eec2-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="3eec2-133">在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂]  按鈕來開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="3eec2-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="3eec2-135">在 [複製設定檔] 視窗中，按一下 [複製]  按鈕來建立 **DefaultHololens2ConfigurationProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="3eec2-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="3eec2-137">新建立的組態設定檔現在已指派為您場景的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="3eec2-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="3eec2-139">在 Unity 功能表中，選取 [檔案]   > [儲存]  ，即可儲存場景。</span><span class="sxs-lookup"><span data-stu-id="3eec2-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="3eec2-140">請記得在整個教學課程中儲存工作。</span><span class="sxs-lookup"><span data-stu-id="3eec2-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="3eec2-141">2.啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="3eec2-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="3eec2-142">在 [階層] 視窗中仍選取 **MixedRealityToolkit** 物件的情況下，於 [偵測器] 視窗中選取 [空間感知]  索引標籤，然後勾選 [啟用空間感知系統]  核取方塊：</span><span class="sxs-lookup"><span data-stu-id="3eec2-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="3eec2-144">3.複製預設的空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="3eec2-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="3eec2-145">在 [空間感知]  索引標籤中，按一下 [複製]  按鈕以開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="3eec2-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="3eec2-147">在 [複製設定檔] 視窗中，按一下 [複製]  按鈕以建立 **DefaultMixedRealitySpatialAwarenessSystemProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="3eec2-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="3eec2-149">新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="3eec2-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="3eec2-151">4.複製預設的空間感知網格觀察器設定檔</span><span class="sxs-lookup"><span data-stu-id="3eec2-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="3eec2-152">在仍選取 [空間感知]  索引標籤的情況下，展開 [Windows Mixed Reality 空間網格觀察器]  區段，然後按一下 [複製]  按鈕來開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="3eec2-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="3eec2-154">在 [複製設定檔] 視窗中，按一下 [複製]  按鈕來建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="3eec2-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="3eec2-156">新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：</span><span class="sxs-lookup"><span data-stu-id="3eec2-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="3eec2-158">5.變更空間感知網格的顯示</span><span class="sxs-lookup"><span data-stu-id="3eec2-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="3eec2-159">在 [空間網格觀察器設定]  中，將 [顯示選項]  變更為 [遮蔽]  ，以隱藏仍在運作的空間對應網格：</span><span class="sxs-lookup"><span data-stu-id="3eec2-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="3eec2-161">雖然空間對應網格看不到，但仍存在且正常運作。</span><span class="sxs-lookup"><span data-stu-id="3eec2-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="3eec2-162">例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="3eec2-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="3eec2-163">您方才已了解如何修改 MRTK 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="3eec2-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="3eec2-164">如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。</span><span class="sxs-lookup"><span data-stu-id="3eec2-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="3eec2-165">由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。</span><span class="sxs-lookup"><span data-stu-id="3eec2-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="3eec2-166">若要深入了解 MRTK 設定檔及其架構，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[混合實境工具組設定檔設定指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。</span><span class="sxs-lookup"><span data-stu-id="3eec2-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="3eec2-167">手部追蹤手勢和可互動的按鈕</span><span class="sxs-lookup"><span data-stu-id="3eec2-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="3eec2-168">在本節中，您將了解如何使用手動追蹤來按下按鈕並觸發事件，讓您可以在按下按鈕時引發動作。</span><span class="sxs-lookup"><span data-stu-id="3eec2-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="3eec2-169">此特定範例將示範如何在按下按鈕時變更立方體的顏色，並在放開按鈕時變回原本顏色。</span><span class="sxs-lookup"><span data-stu-id="3eec2-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="3eec2-170">不過，您可以遵循這些相同原則來建立其他事件。</span><span class="sxs-lookup"><span data-stu-id="3eec2-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="3eec2-171">變更立方體顏色所需的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="3eec2-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="3eec2-172">將可點按的按鈕 Prefab 新增至場景</span><span class="sxs-lookup"><span data-stu-id="3eec2-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="3eec2-173">在場景中新增立方體</span><span class="sxs-lookup"><span data-stu-id="3eec2-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="3eec2-174">設定 InteractableOnPressReceiver 事件種類</span><span class="sxs-lookup"><span data-stu-id="3eec2-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="3eec2-175">設定立方體來接收「按下」事件</span><span class="sxs-lookup"><span data-stu-id="3eec2-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="3eec2-176">定義「按下」事件要觸發的動作</span><span class="sxs-lookup"><span data-stu-id="3eec2-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="3eec2-177">設定立方體以接收「放開」事件</span><span class="sxs-lookup"><span data-stu-id="3eec2-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="3eec2-178">定義「放開」事件要觸發的動作</span><span class="sxs-lookup"><span data-stu-id="3eec2-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="3eec2-179">使用編輯器內模擬來測試按鈕</span><span class="sxs-lookup"><span data-stu-id="3eec2-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="3eec2-180">1.將可點按的按鈕 Prefab 新增至場景</span><span class="sxs-lookup"><span data-stu-id="3eec2-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="3eec2-181"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> 是預先設定且儲存為 Unity 資產的 GameObject，可以在整個專案中重複使用。</span><span class="sxs-lookup"><span data-stu-id="3eec2-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="3eec2-182">在**專案視窗**中搜尋 **PressableButtonHoloLens2**，以找出您將在此範例中使用的 Prefab：</span><span class="sxs-lookup"><span data-stu-id="3eec2-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="3eec2-184">在**搜尋**結果中選取 **PressableButtonHoloLens2** Prefab，然後將其**拖曳**到 [階層]  視窗中來新增到場景中：</span><span class="sxs-lookup"><span data-stu-id="3eec2-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="3eec2-186">若要顯示下圖所示的場景，請按兩下 [階層] 視窗中的 PressableButtonHoloLens2 物件，使其成為焦點，然後使用位於場景視窗右上角的<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">場景 Gizmo</a>，將檢視角度調整為以 Z 軸為前方。</span><span class="sxs-lookup"><span data-stu-id="3eec2-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="3eec2-187">在仍選取 **PressableButtonHoloLens2** 物件的情況下，在 [偵測器]  視窗中：</span><span class="sxs-lookup"><span data-stu-id="3eec2-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="3eec2-188">變更其變形**位置**，使其位於位於相機前方 (也就是其原本位置)，例如，x = 0、y = 0 和 z = 0.5</span><span class="sxs-lookup"><span data-stu-id="3eec2-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="3eec2-190">一般情況下，Unity 中的 1 個位置單位會大致等於真實世界的 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="3eec2-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="3eec2-191">但有例外狀況，例如，當物件是所縮放物件的子系時。</span><span class="sxs-lookup"><span data-stu-id="3eec2-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="3eec2-192">2.在場景中新增立方體</span><span class="sxs-lookup"><span data-stu-id="3eec2-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="3eec2-193">以滑鼠右鍵按一下 [階層] 視窗內的空白位置，然後選取 [3D 物件]   > [立方體]  ，將立方體新增至您的場景：</span><span class="sxs-lookup"><span data-stu-id="3eec2-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="3eec2-195">在仍選取**立方體**物件的情況下，在 [偵測器]  視窗中：</span><span class="sxs-lookup"><span data-stu-id="3eec2-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="3eec2-196">變更其變形**位置**，使其位於可點按的按鈕附近，但不與之重疊，例如 x = 0、y = 0.04 和 z = 0.5</span><span class="sxs-lookup"><span data-stu-id="3eec2-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="3eec2-197">將其變形**縮放**變更為適當大小，例如 x = 0.02、y = 0.02 和 z = 0.02</span><span class="sxs-lookup"><span data-stu-id="3eec2-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="3eec2-199">3.設定 InteractableOnPressReceiver 事件種類</span><span class="sxs-lookup"><span data-stu-id="3eec2-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="3eec2-200">在 [階層] 視窗中選取 **PressableButtonHoloLens2** 物件，然後在 [偵測器]  視窗的**三條線功能表**中選取 [摺疊所有元件]  ，以取得此物件上所有元件的概觀：</span><span class="sxs-lookup"><span data-stu-id="3eec2-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="3eec2-202">展開 [Interactable (指令碼)]  元件，然後找出並展開 [事件]   > [接收者]  區段：</span><span class="sxs-lookup"><span data-stu-id="3eec2-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="3eec2-204">按一下 [新增事件]  按鈕，以建立事件接收器類型為 **InteractableOnPressReceiver** 的新事件接收器：</span><span class="sxs-lookup"><span data-stu-id="3eec2-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="3eec2-206">名為 InteractableOnPressReceiver 的事件接收器類別可讓按鈕在追蹤的手部按下按鈕時，回應按下的事件。</span><span class="sxs-lookup"><span data-stu-id="3eec2-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="3eec2-207">針對新建立的事件接收器，將**互動篩選**變更為**近處或遠處**：</span><span class="sxs-lookup"><span data-stu-id="3eec2-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="3eec2-209">4.設定立方體來接收「按下」事件</span><span class="sxs-lookup"><span data-stu-id="3eec2-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="3eec2-210">在 [階層] 視窗中，**按一下並拖曳**立方體  至 **On Press ()** 事件的 [事件屬性]  物件欄位中，將立方體指派為 On Press () 事件的接收者：</span><span class="sxs-lookup"><span data-stu-id="3eec2-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="3eec2-212">5.定義「按下」事件要觸發的動作</span><span class="sxs-lookup"><span data-stu-id="3eec2-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="3eec2-213">按一下動作下拉式清單 (目前指派內容為**無函式**)，然後選取 [MeshRenderer]   > [材質內容]  ，將立方體的材質屬性設定為在觸發 On Press () 事件時變更：</span><span class="sxs-lookup"><span data-stu-id="3eec2-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="3eec2-215">按一下材質欄位旁的**圓型**小圖示 (目前已填入 [無 (材質)])  ，以開啟選取材質視窗：</span><span class="sxs-lookup"><span data-stu-id="3eec2-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="3eec2-217">在 [選取材質] 視窗中，**搜尋** **MRTK_Standard** 並選取適當的材質，例如 **MRTK_Standard_Cyan**，如此一來，當您按下按鈕時，立方體的顏色會變更為青綠色：</span><span class="sxs-lookup"><span data-stu-id="3eec2-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="3eec2-219">6.設定立方體以接收「放開」事件</span><span class="sxs-lookup"><span data-stu-id="3eec2-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="3eec2-220">針對「放開」事件**重複**步驟 4，即可將**立方體**指派為 **On Release ()** 事件的接收者。</span><span class="sxs-lookup"><span data-stu-id="3eec2-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="3eec2-221">7.定義「放開」事件要觸發的動作</span><span class="sxs-lookup"><span data-stu-id="3eec2-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="3eec2-222">針對「放開」事件**重複**步驟 5，但選擇 [MRTK_Standard_LightGray]  材質，讓立方體的顏色在放開按鈕時回到其原本的淺灰色：</span><span class="sxs-lookup"><span data-stu-id="3eec2-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="3eec2-224">8.使用編輯器內模擬來測試按鈕</span><span class="sxs-lookup"><span data-stu-id="3eec2-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="3eec2-225">按下 [開始遊戲]  按鈕進入遊戲模式，並使用編輯器內的輸入模擬來測試新設定的按鈕。</span><span class="sxs-lookup"><span data-stu-id="3eec2-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="3eec2-226">未按下按鈕 (空格鍵 + 向後轉動滑鼠滾輪)：</span><span class="sxs-lookup"><span data-stu-id="3eec2-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="3eec2-228">已按下按鈕 (空格鍵 + 向前轉動滑鼠滾輪)：</span><span class="sxs-lookup"><span data-stu-id="3eec2-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="3eec2-230">若要了解如何使用編輯器內的輸入模擬，您可以參考 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用編輯器內的手動輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。</span><span class="sxs-lookup"><span data-stu-id="3eec2-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="3eec2-231">使用 MRTK 的方格物件集合來建立按鈕面板</span><span class="sxs-lookup"><span data-stu-id="3eec2-231">Creating a panel of buttons using MRTK's Grid Object Collection</span></span>

<span data-ttu-id="3eec2-232">在本節中，您會了解如何使用 MRTK 的方格物件集合工具，讓多個按鈕自動排列成整齊的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="3eec2-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK's Grid Object Collection tool.</span></span>

<span data-ttu-id="3eec2-233">此特定範例將示範如何建立有五個按鈕水平對齊的面板。</span><span class="sxs-lookup"><span data-stu-id="3eec2-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="3eec2-234">不過，您也可以遵循這些相同原則來建立其他版面配置。</span><span class="sxs-lookup"><span data-stu-id="3eec2-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="3eec2-235">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="3eec2-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="3eec2-236">使按鈕物件歸屬於父物件</span><span class="sxs-lookup"><span data-stu-id="3eec2-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="3eec2-237">新增和設定 Grid Object Collection (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="3eec2-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="3eec2-238">使用編輯器內的模擬來測試按鈕</span><span class="sxs-lookup"><span data-stu-id="3eec2-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="3eec2-239">1.使按鈕物件歸屬於父物件</span><span class="sxs-lookup"><span data-stu-id="3eec2-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="3eec2-240">以滑鼠右鍵按一下 [階層] 視窗內的空白位置，然後選取 [建立空白物件]  ：</span><span class="sxs-lookup"><span data-stu-id="3eec2-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="3eec2-242">以滑鼠右鍵按一下新建立的物件，選取 [重新命名]  並為其指定適當的名稱，例如 **ButtonCollection**：</span><span class="sxs-lookup"><span data-stu-id="3eec2-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="3eec2-244">選取 **PressableButtonHoloLens2** 物件，然後將其**拖曳**到 **ButtonCollection** 物件的上方，使其成為 ButtonCollection 物件的子系：</span><span class="sxs-lookup"><span data-stu-id="3eec2-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="3eec2-246">以滑鼠右鍵按一下 **PressableButtonHoloLens2** 物件，然後選取 [複製]  來建立其複本：</span><span class="sxs-lookup"><span data-stu-id="3eec2-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="3eec2-248">再**重複**此步驟四次，直到總共有五個 PressableButtonHoloLens2 物件為止。</span><span class="sxs-lookup"><span data-stu-id="3eec2-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="3eec2-249">2.新增和設定 Grid Object Collection (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="3eec2-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="3eec2-250">在 [階層] 視窗中選取 ButtonCollection 物件之後，在 [偵測器] 視窗中按一下 [新增元件]  按鈕，然後搜尋並選取 [Grid Object Collection]  以將 Grid Object Collection (指令碼) 元件新增至 ButtonCollection 物件：</span><span class="sxs-lookup"><span data-stu-id="3eec2-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="3eec2-252">設定 Grid Object Collection (指令碼)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3eec2-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="3eec2-253">將 [資料列數目]  變更為 1，使所有按鈕對齊一個單一資料列</span><span class="sxs-lookup"><span data-stu-id="3eec2-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="3eec2-254">將 [儲存格寬度]  變更為 0.05，以拉開資料列內的按鈕距離</span><span class="sxs-lookup"><span data-stu-id="3eec2-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="3eec2-255">然後按一下 [更新集合]  按鈕以套用新的設定：</span><span class="sxs-lookup"><span data-stu-id="3eec2-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="3eec2-257">您剛才套用的設定變更代表為了將按鈕放在單一資料列中所需的最小變更。</span><span class="sxs-lookup"><span data-stu-id="3eec2-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="3eec2-258">不過，在未來的專案中，根據一些因素 (例如，父物件和子物件的方向)，您可能需要調整其他設定 (例如，方向類型)。</span><span class="sxs-lookup"><span data-stu-id="3eec2-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="3eec2-259">若要深入了解 MRTK 的 Grid Object Collection，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[物件集合指令碼](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)指南。</span><span class="sxs-lookup"><span data-stu-id="3eec2-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="3eec2-260">在 [階層] 視窗中仍然選取 ButtonCollection 物件時，在 [偵測器] 視窗中變更 ButtonCollection 物件的變形**位置**，使其子按鈕物件位在相機前方 (也就是原本的位置)，例如 x = 0、y = 0 和 z = 0.5：</span><span class="sxs-lookup"><span data-stu-id="3eec2-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="3eec2-262">當您第一次將 PressableButtonHoloLens2 Prefab 新增至上述[手部追蹤手勢和可互動的按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)區段中的場景時，您會將其放在相機前方。</span><span class="sxs-lookup"><span data-stu-id="3eec2-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="3eec2-263">不過，由於方格物件集合會控制其直屬子物件的位置，因此 PressableButtonHoloLens2 子物件的 Z 位置會因為方格物件集合的「與父系的距離」值預設為 0，而重設為0。</span><span class="sxs-lookup"><span data-stu-id="3eec2-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="3eec2-264">這就是為什麼我們會將父 ButtonCollection 物件的位置向前移動，而不是設定「與父系的距離」值來向前移動 PressableButtonHoloLens2 子物件，同時也是為了保持父/子位置關聯性的結構。</span><span class="sxs-lookup"><span data-stu-id="3eec2-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="3eec2-265">3.使用編輯器內的模擬來測試按鈕</span><span class="sxs-lookup"><span data-stu-id="3eec2-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="3eec2-266">按下 [開始遊戲] 按鈕進入遊戲模式，並使用編輯器內的輸入模擬來測試新建立按鈕面板中的每個按鈕：</span><span class="sxs-lookup"><span data-stu-id="3eec2-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="3eec2-268">目前，當您按下五個按鈕的其中一個時，立方體顏色會變更為青綠色。</span><span class="sxs-lookup"><span data-stu-id="3eec2-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="3eec2-269">若要讓體驗更加有趣，請使用您剛學到的內容來設定每個按鈕，將立方體變更為不同的顏色。</span><span class="sxs-lookup"><span data-stu-id="3eec2-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="3eec2-270">在場景中新增文字</span><span class="sxs-lookup"><span data-stu-id="3eec2-270">Adding text into your scene</span></span>

<span data-ttu-id="3eec2-271">在本節中，您將了解如何使用 Unity 的 TextMesh Pro (您已在上一個教學課程的[匯入 TextMesh Pro 基本資源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)一節中有所準備)，將文字新增至您的混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="3eec2-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="3eec2-272">在此特定範例中，您會在上一節建立的按鈕集合底下新增一個簡單標籤。</span><span class="sxs-lookup"><span data-stu-id="3eec2-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="3eec2-273">以滑鼠右鍵按一下 ButtonCollection 物件，然後選取 [3D 物件]   > [文字 - TextMeshPro]  ，將 TextMeshPro 物件建立為 ButtonCollection 物件的子系：</span><span class="sxs-lookup"><span data-stu-id="3eec2-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="3eec2-275">在新建立的 TextMeshPro 物件(名為 Text (TMP)) 仍為選取狀態時，在 [偵測器] 視窗中變更其位置和大小，讓標籤整齊地放在按鈕集合底下，例如：</span><span class="sxs-lookup"><span data-stu-id="3eec2-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="3eec2-276">將矩形變形**Y 位置**變更為 -0.0425</span><span class="sxs-lookup"><span data-stu-id="3eec2-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="3eec2-277">將矩形變形**寬度**變更為 0.24</span><span class="sxs-lookup"><span data-stu-id="3eec2-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="3eec2-278">將矩形變形**高度**變更為 0.024</span><span class="sxs-lookup"><span data-stu-id="3eec2-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="3eec2-279">然後更新文字以反映標籤的用途，並選擇字型屬性，讓文字適合放入標籤，例如：</span><span class="sxs-lookup"><span data-stu-id="3eec2-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="3eec2-280">將 Text Mesh Pro (指令碼) 的**文字**變更為按鈕集合</span><span class="sxs-lookup"><span data-stu-id="3eec2-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="3eec2-281">將 Text Mesh Pro (指令碼) 的**字型樣式**變更為粗體</span><span class="sxs-lookup"><span data-stu-id="3eec2-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="3eec2-282">將 Text Mesh Pro (指令碼) 的**字型大小**變更為 0.2</span><span class="sxs-lookup"><span data-stu-id="3eec2-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="3eec2-283">將 Text Mesh Pro (指令碼) 的**對齊**變更為置中和中間</span><span class="sxs-lookup"><span data-stu-id="3eec2-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="3eec2-285">恭喜！</span><span class="sxs-lookup"><span data-stu-id="3eec2-285">Congratulations</span></span>

<span data-ttu-id="3eec2-286">在本教學課程中，您已了解如何複製、自訂和設定 MRTK 設定檔的設定。</span><span class="sxs-lookup"><span data-stu-id="3eec2-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="3eec2-287">您也已經了解如何在 HoloLens 2 上使用追蹤的手部來與按鈕互動以觸發事件。</span><span class="sxs-lookup"><span data-stu-id="3eec2-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="3eec2-288">最後，您已了解如何使用 MRTK 的方格物件集合元件和 Unity 的 Text Mesh Pro 來建立簡單的 UI 介面。</span><span class="sxs-lookup"><span data-stu-id="3eec2-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="3eec2-289">下一個教學課程：4.放置動態內容並使用解算器</span><span class="sxs-lookup"><span data-stu-id="3eec2-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
