---
title: 快速入門教學課程-3。 建立使用者介面和設定混合現實工具組
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: f1d042150d1c81940e672b174c6c02ac71e05883
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554872"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="b69ba-105">3. 建立使用者介面和設定混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="b69ba-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="b69ba-106">在上一個教學課程中，您已瞭解混合現實工具組（MRTK）透過啟動第一個 HoloLens 的應用程式所提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="b69ba-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="b69ba-107">在本教學課程中，您將學習如何建立和組織按鈕以及 UI 文字面板，並使用預設互動（觸控）與每個按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="b69ba-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="b69ba-108">此外，您還會探索如何新增簡單的動作和效果，例如變更物件的大小、音效和色彩。</span><span class="sxs-lookup"><span data-stu-id="b69ba-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="b69ba-109">本課程模組將介紹有關修改 MRTK 設定檔的基本概念，從關閉[空間對應](spatial-mapping.md)網格視覺效果開始。</span><span class="sxs-lookup"><span data-stu-id="b69ba-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="b69ba-110">目標</span><span class="sxs-lookup"><span data-stu-id="b69ba-110">Objectives</span></span>

* <span data-ttu-id="b69ba-111">自訂和設定混合實境工具組設定檔</span><span class="sxs-lookup"><span data-stu-id="b69ba-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="b69ba-112">使用 UI 元素和按鈕與全息影像互動</span><span class="sxs-lookup"><span data-stu-id="b69ba-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="b69ba-113">基本的「手部追蹤」輸入和互動</span><span class="sxs-lookup"><span data-stu-id="b69ba-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="b69ba-114">如何設定混合現實工具組設定檔（變更空間感知顯示選項）</span><span class="sxs-lookup"><span data-stu-id="b69ba-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="b69ba-115">在本節中，您將瞭解如何自訂和設定預設的 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b69ba-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="b69ba-116">此特定範例將示範如何藉由變更空間網格觀察者的設定，來隱藏空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="b69ba-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="b69ba-117">不過，您可以遵循這些相同的原則，自訂 MRTK 設定檔中的任何設定或值。</span><span class="sxs-lookup"><span data-stu-id="b69ba-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="b69ba-118">隱藏空間感知網格所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="b69ba-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="b69ba-119">複製預設設定設定檔</span><span class="sxs-lookup"><span data-stu-id="b69ba-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="b69ba-120">啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="b69ba-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="b69ba-121">複製預設空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="b69ba-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="b69ba-122">複製預設空間感知網格觀察者設定檔</span><span class="sxs-lookup"><span data-stu-id="b69ba-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="b69ba-123">變更空間感知網格的可見度</span><span class="sxs-lookup"><span data-stu-id="b69ba-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="b69ba-124">根據預設，您無法編輯 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b69ba-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="b69ba-125">這些是預設設定檔範本，您必須先加以複製，才能進行編輯。</span><span class="sxs-lookup"><span data-stu-id="b69ba-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="b69ba-126">有數個嵌套的設定檔層。</span><span class="sxs-lookup"><span data-stu-id="b69ba-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="b69ba-127">因此，在設定一或多個設定時，通常會複製並編輯數個設定檔。</span><span class="sxs-lookup"><span data-stu-id="b69ba-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="b69ba-128">1. 複製預設設定設定檔</span><span class="sxs-lookup"><span data-stu-id="b69ba-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="b69ba-129">設定設定檔是最上層的設定檔。</span><span class="sxs-lookup"><span data-stu-id="b69ba-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="b69ba-130">因此，若要能夠編輯任何其他設定檔，您必須先複製設定設定檔。</span><span class="sxs-lookup"><span data-stu-id="b69ba-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="b69ba-131">在 [階層] 視窗中選取**MixedRealityToolkit**物件之後，在 [偵測器] 視窗中，將 [混合現實工具組]**設定檔**變更為**DefaultHoloLens2ConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="b69ba-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="b69ba-133">在仍選取**MixedRealityToolkit**物件的情況下，在 [偵測器] 視窗中，按一下 [**複製 & 自訂**] 按鈕以開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="b69ba-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="b69ba-135">在 [複製設定檔] 視窗中，按一下 [**複製**] 按鈕，以建立**DefaultHololens2ConfigurationProfile**的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="b69ba-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="b69ba-137">新建立的設定檔現在已指派為您場景的設定檔：</span><span class="sxs-lookup"><span data-stu-id="b69ba-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="b69ba-139">在 Unity 功能表中 **，選取** 檔案 > **儲存** 以儲存場景。</span><span class="sxs-lookup"><span data-stu-id="b69ba-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="b69ba-140">請記得在整個教學課程中儲存工作。</span><span class="sxs-lookup"><span data-stu-id="b69ba-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="b69ba-141">2. 啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="b69ba-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="b69ba-142">在 [階層] 視窗中仍然選取**MixedRealityToolkit**物件，在 [偵測器] 視窗中，選取 [**空間感知**] 索引標籤，然後核取 [**啟用空間感知系統**] 核取方塊：</span><span class="sxs-lookup"><span data-stu-id="b69ba-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="b69ba-144">3. 複製預設空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="b69ba-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="b69ba-145">在 [**空間感知**] 索引標籤中，按一下 [**複製**] 按鈕以開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="b69ba-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="b69ba-147">在 [複製設定檔] 視窗中，按一下 [**複製**] 按鈕，以建立**DefaultMixedRealitySpatialAwarenessSystemProfile**的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="b69ba-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="b69ba-149">新建立的空間感知系統設定檔現在會自動指派給您的設定設定檔：</span><span class="sxs-lookup"><span data-stu-id="b69ba-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="b69ba-151">4. 複製預設空間感知網格觀察者設定檔</span><span class="sxs-lookup"><span data-stu-id="b69ba-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="b69ba-152">在仍選取 [**空間感知**] 索引標籤的情況下，展開 [ **Windows Mixed Reality 空間網格觀察**者] 區段，然後按一下 [**複製**] 按鈕以開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="b69ba-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="b69ba-154">在 [複製設定檔] 視窗中，按一下 [**複製**] 按鈕，以建立**DefaultMixedRealitySpatialAwarenessMeshObserverProfile**的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="b69ba-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="b69ba-156">新建立的空間感知網格觀察者設定檔現在會自動指派給您的空間感知系統設定檔：</span><span class="sxs-lookup"><span data-stu-id="b69ba-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="b69ba-158">5. 變更空間感知網格的可見度</span><span class="sxs-lookup"><span data-stu-id="b69ba-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="b69ba-159">在 [**空間網格觀察**者] 設定中，將 [**顯示] 選項**變更為 [**遮蔽**]，讓空間對應網格在正常運作時不可見：</span><span class="sxs-lookup"><span data-stu-id="b69ba-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="b69ba-161">雖然空間對應網格看不到，但仍存在且正常運作。</span><span class="sxs-lookup"><span data-stu-id="b69ba-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="b69ba-162">例如，空間對應網格背後的任何全息影像（例如，實體牆後方的全息圖）將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="b69ba-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="b69ba-163">您方才已了解如何修改 MRTK 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="b69ba-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="b69ba-164">如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。</span><span class="sxs-lookup"><span data-stu-id="b69ba-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="b69ba-165">由於預設設定檔無法編輯，因此如果您想要還原為預設設定，則一律會將它們當做參考。</span><span class="sxs-lookup"><span data-stu-id="b69ba-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="b69ba-166">若要深入瞭解 MRTK 設定檔及其架構，您可以造訪[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[混合現實工具組設定檔設定指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。</span><span class="sxs-lookup"><span data-stu-id="b69ba-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="b69ba-167">手形追蹤筆勢和可互動按鈕</span><span class="sxs-lookup"><span data-stu-id="b69ba-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="b69ba-168">在本節中，您將瞭解如何使用「手動追蹤」來按下按鈕並觸發事件，以在按下按鈕時引發動作。</span><span class="sxs-lookup"><span data-stu-id="b69ba-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="b69ba-169">此特定範例將示範如何在按下按鈕時變更 cube 的色彩，並在放開按鈕時，將它變更回原始色彩。</span><span class="sxs-lookup"><span data-stu-id="b69ba-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="b69ba-170">不過，您可以遵循這些相同的原則來建立其他事件。</span><span class="sxs-lookup"><span data-stu-id="b69ba-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="b69ba-171">您需要變更 cube 色彩的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="b69ba-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="b69ba-172">將 pressable 按鈕 prefab 新增至場景</span><span class="sxs-lookup"><span data-stu-id="b69ba-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="b69ba-173">將 cube 新增至場景</span><span class="sxs-lookup"><span data-stu-id="b69ba-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="b69ba-174">設定 InteractableOnPressReceiver 事件種類</span><span class="sxs-lookup"><span data-stu-id="b69ba-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="b69ba-175">設定 cube 以在按下事件時接收</span><span class="sxs-lookup"><span data-stu-id="b69ba-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="b69ba-176">定義要在按下事件時觸發的動作</span><span class="sxs-lookup"><span data-stu-id="b69ba-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="b69ba-177">設定 cube 以接收發行前事件</span><span class="sxs-lookup"><span data-stu-id="b69ba-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="b69ba-178">定義要由「發行」事件觸發的動作</span><span class="sxs-lookup"><span data-stu-id="b69ba-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="b69ba-179">使用編輯器內模擬來測試按鈕</span><span class="sxs-lookup"><span data-stu-id="b69ba-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="b69ba-180">1. 將 pressable 按鈕 prefab 新增至場景</span><span class="sxs-lookup"><span data-stu-id="b69ba-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="b69ba-181"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a>是預先設定的 GameObject，儲存為 Unity 資產，並可在整個專案中重複使用。</span><span class="sxs-lookup"><span data-stu-id="b69ba-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="b69ba-182">在 [**專案] 視窗**中，搜尋**PressableButtonHoloLens2**以找出您將在此範例中使用的 prefab：</span><span class="sxs-lookup"><span data-stu-id="b69ba-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="b69ba-184">在**搜尋**結果中，選取 [ **PressableButtonHoloLens2** ] prefab，並**將它拖曳** **至 [階層] 視窗，將**它新增至您的場景：</span><span class="sxs-lookup"><span data-stu-id="b69ba-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="b69ba-186">若要顯示您的場景（如下圖所示），請按兩下 [階層] 視窗中的 [PressableButtonHoloLens2] 物件，使其成為焦點，然後使用場景<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Gizmo</a>（位於場景視窗的右上角），將視角調整為沿著正向 Z 軸。</span><span class="sxs-lookup"><span data-stu-id="b69ba-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="b69ba-187">在仍選取**PressableButtonHoloLens2**物件的情況下，在 [偵測**器**] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="b69ba-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="b69ba-188">變更其 [轉換**位置**]，使其定位於位於來源的相機前方，例如 x = 0、y = 0 和 z = 0。5</span><span class="sxs-lookup"><span data-stu-id="b69ba-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="b69ba-190">一般而言，Unity 中的1個位置單位大致等同于實體世界中的1個計量。</span><span class="sxs-lookup"><span data-stu-id="b69ba-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="b69ba-191">不過，這有一些例外狀況，例如，當物件是縮放物件的子系時。</span><span class="sxs-lookup"><span data-stu-id="b69ba-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="b69ba-192">2. 將 cube 新增至場景</span><span class="sxs-lookup"><span data-stu-id="b69ba-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="b69ba-193">以滑鼠右鍵按一下 [階層] 視窗內的空白位置，然後選取 [ **3D 物件** > **Cube** ]，將 cube 新增至您的場景：</span><span class="sxs-lookup"><span data-stu-id="b69ba-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="b69ba-195">在仍選取**Cube**物件的情況下，在 [偵測**器**] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="b69ba-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="b69ba-196">變更其轉換**位置**，使其位於 [pressable] 按鈕附近，但不會與它重迭，例如 x = 0、y = 0.04 和 z = 0。5</span><span class="sxs-lookup"><span data-stu-id="b69ba-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="b69ba-197">將其轉換**調整**為適當的大小，例如 x = 0.02、y = 0.02 和 z = 0.02</span><span class="sxs-lookup"><span data-stu-id="b69ba-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="b69ba-199">3. 設定 InteractableOnPressReceiver 事件種類</span><span class="sxs-lookup"><span data-stu-id="b69ba-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="b69ba-200">在 [階層] 視窗中，選取**PressableButtonHoloLens2**物件，然後在 [ **Inspector** ] 視窗的 [**漢堡] 功能表**中，選取 [折迭**所有元件**] 以取得此物件上所有元件的總覽：</span><span class="sxs-lookup"><span data-stu-id="b69ba-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="b69ba-202">展開 [**可互動（腳本）** ] 元件，然後找出並展開 [**事件** > **接收者**] 區段：</span><span class="sxs-lookup"><span data-stu-id="b69ba-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="b69ba-204">按一下 [**新增事件**] 按鈕，以建立事件接收器類型**InteractableOnPressReceiver**的新事件接收器：</span><span class="sxs-lookup"><span data-stu-id="b69ba-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="b69ba-206">名為 InteractableOnPressReceiver 的事件接收器型別，可讓按鈕在追蹤的手按下按鈕時，回應按下的事件。</span><span class="sxs-lookup"><span data-stu-id="b69ba-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="b69ba-207">針對新建立的事件接收器，將 [**互動] 篩選**變更為 [**接近] 或 [遠**]：</span><span class="sxs-lookup"><span data-stu-id="b69ba-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="b69ba-209">4. 設定 cube 以在按下事件時接收</span><span class="sxs-lookup"><span data-stu-id="b69ba-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="b69ba-210">從 [階層] 視窗中，**按一下並將** **cube**拖曳至 [**按下（）** ] 事件的 [**事件**內容] 物件欄位中，將 cube 指派為按下（）事件的接收者：</span><span class="sxs-lookup"><span data-stu-id="b69ba-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="b69ba-212">5. 定義要在按下事件時觸發的動作</span><span class="sxs-lookup"><span data-stu-id="b69ba-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="b69ba-213">按一下 [動作] 下拉式清單（目前**未指派任何**函式），然後選取 [ **MeshRenderer** > **材質材質**]，將 Cube 的材質屬性設定為在觸發 On 按（）事件時變更：</span><span class="sxs-lookup"><span data-stu-id="b69ba-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="b69ba-215">按一下 [材質] 欄位旁的小**圓圈**圖示，目前已填入 [**無（材質）** ]，以開啟 [選取材質] 視窗：</span><span class="sxs-lookup"><span data-stu-id="b69ba-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="b69ba-217">在 [選取材質] 視窗中，**搜尋** **MRTK_Standard**並選取適當的資料，例如， **MRTK_Standard_Cyan**因此當按下按鈕時，Cube 的色彩會變更為青色：</span><span class="sxs-lookup"><span data-stu-id="b69ba-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="b69ba-219">6. 設定 cube 以接收發行前事件</span><span class="sxs-lookup"><span data-stu-id="b69ba-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="b69ba-220">**重複**「發行時」事件的步驟4，將**Cube**指派為「 **on 發行」（）** 事件的接收者。</span><span class="sxs-lookup"><span data-stu-id="b69ba-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="b69ba-221">7. 定義要由「發行」事件觸發的動作</span><span class="sxs-lookup"><span data-stu-id="b69ba-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="b69ba-222">**重複**[On Release] 事件的步驟5，但選擇 [ **MRTK_Standard_LightGray** ] 材質，讓 Cube 的色彩在放開按鈕時回到其原始的淺灰色色彩：</span><span class="sxs-lookup"><span data-stu-id="b69ba-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="b69ba-224">8. 使用編輯器內模擬來測試按鈕</span><span class="sxs-lookup"><span data-stu-id="b69ba-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="b69ba-225">按下 [**播放**] 按鈕進入遊戲模式，並使用編輯器內的輸入模擬來測試新設定的按鈕。</span><span class="sxs-lookup"><span data-stu-id="b69ba-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="b69ba-226">未按下按鈕（空格鍵 + 滑鼠滾輪向後回溯）：</span><span class="sxs-lookup"><span data-stu-id="b69ba-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="b69ba-228">已按下按鈕（空格鍵 + 滑鼠滾輪向前滾動）：</span><span class="sxs-lookup"><span data-stu-id="b69ba-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="b69ba-230">若要瞭解如何使用編輯器內的輸入模擬，您可以參考[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用編輯器中的手寫輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。</span><span class="sxs-lookup"><span data-stu-id="b69ba-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="b69ba-231">使用 MRTK 的方格物件集合來建立按鈕面板</span><span class="sxs-lookup"><span data-stu-id="b69ba-231">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="b69ba-232">在本節中，您將學習如何使用 MRTK 的 Grid 物件集合工具，自動將多個按鈕對齊整齊的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b69ba-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s Grid Object Collection tool.</span></span>

<span data-ttu-id="b69ba-233">此特定範例將示範如何建立一個水準對齊五個按鈕的面板。</span><span class="sxs-lookup"><span data-stu-id="b69ba-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="b69ba-234">不過，您可以遵循這些相同的原則來建立其他版面配置。</span><span class="sxs-lookup"><span data-stu-id="b69ba-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="b69ba-235">達成此目標所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="b69ba-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="b69ba-236">父系按鈕物件至父物件</span><span class="sxs-lookup"><span data-stu-id="b69ba-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="b69ba-237">加入和設定 Grid 物件集合（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="b69ba-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="b69ba-238">使用編輯器內模擬來測試按鈕</span><span class="sxs-lookup"><span data-stu-id="b69ba-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="b69ba-239">1. 將按鈕物件父系到父物件</span><span class="sxs-lookup"><span data-stu-id="b69ba-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="b69ba-240">以滑鼠右鍵按一下 [階層] 視窗內的空白位置，然後選取 [**建立空**的]：</span><span class="sxs-lookup"><span data-stu-id="b69ba-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="b69ba-242">以滑鼠右鍵按一下新建立的物件，並選取 [**重新命名**]，然後指定適當的名稱，例如**ButtonCollection**：</span><span class="sxs-lookup"><span data-stu-id="b69ba-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="b69ba-244">選取**PressableButtonHoloLens2**物件，並**將它拖曳**至**ButtonCollection**物件的上方，使其成為 ButtonCollection 物件的子系：</span><span class="sxs-lookup"><span data-stu-id="b69ba-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="b69ba-246">在**PressableButtonHoloLens2**物件上按一下滑鼠右鍵，然後選取 [**複製**]，以建立其複本：</span><span class="sxs-lookup"><span data-stu-id="b69ba-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="b69ba-248">**重複**此步驟四次，直到總共有五個 PressableButtonHoloLens2 物件為止。</span><span class="sxs-lookup"><span data-stu-id="b69ba-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="b69ba-249">2. 加入及設定 Grid 物件集合（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="b69ba-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="b69ba-250">在 [階層] 視窗中選取 ButtonCollection 物件之後，在 [偵測器] 視窗中，按一下 [**加入元件**] 按鈕，然後搜尋並選取 [**方格物件集合**]，將 Grid 物件集合（腳本）元件加入至 ButtonCollection 物件：</span><span class="sxs-lookup"><span data-stu-id="b69ba-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="b69ba-252">設定 Grid 物件集合（腳本），如下所示：</span><span class="sxs-lookup"><span data-stu-id="b69ba-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="b69ba-253">將 [Num] 資料**列**變更為 [1]，讓所有按鈕對齊一個單一資料列</span><span class="sxs-lookup"><span data-stu-id="b69ba-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="b69ba-254">將資料**格寬度**變更為0.05，以將資料列內的按鈕變成空白</span><span class="sxs-lookup"><span data-stu-id="b69ba-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="b69ba-255">然後按一下 [**更新集合**] 按鈕以套用新的設定：</span><span class="sxs-lookup"><span data-stu-id="b69ba-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="b69ba-257">您剛才套用的設定變更代表達到將按鈕放在單一資料列的目標所需的最小變更。</span><span class="sxs-lookup"><span data-stu-id="b69ba-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="b69ba-258">不過，在未來的專案中，視因素（例如，父系和子物件的方向）而定，您可能需要調整其他設定（例如，方向類型）。</span><span class="sxs-lookup"><span data-stu-id="b69ba-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="b69ba-259">若要深入瞭解 MRTK 的方格物件集合，您可以造訪[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[物件集合腳本](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)指南。</span><span class="sxs-lookup"><span data-stu-id="b69ba-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="b69ba-260">在 [階層] 視窗中仍然選取 ButtonCollection 物件時，在 [偵測器] 視窗中，變更 ButtonCollection 物件的轉換**位置**，讓其子按鈕物件位於相機前方，例如 x = 0、y = 0 和 z = 0.5：</span><span class="sxs-lookup"><span data-stu-id="b69ba-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="b69ba-262">當您第一次將 PressableButtonHoloLens2 prefab 新增至上方的 [[右手追蹤筆勢] 和 [可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)] 區段中的場景時，您會將它放在相機前方。</span><span class="sxs-lookup"><span data-stu-id="b69ba-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="b69ba-263">不過，由於 Grid 物件集合會控制其直屬子物件的位置，因此根據格線物件集合的預設距離0的父代值，PressableButtonHoloLens2 子物件的 Z 位置已重設為0。</span><span class="sxs-lookup"><span data-stu-id="b69ba-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="b69ba-264">這是為了讓父/子位置的關聯性保持組織，這就是為什麼我們會將父 ButtonCollection 物件的位置向前移動，而不是設定從父系值到向前移動 PressableButtonHoloLens2 子物件的距離。</span><span class="sxs-lookup"><span data-stu-id="b69ba-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="b69ba-265">3. 使用編輯器內模擬來測試按鈕</span><span class="sxs-lookup"><span data-stu-id="b69ba-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="b69ba-266">按下 [播放] 按鈕進入遊戲模式，並使用編輯器內的輸入模擬來測試新建立的按鈕面板中的每個按鈕：</span><span class="sxs-lookup"><span data-stu-id="b69ba-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="b69ba-268">目前，當您按五個按鈕的任一個時，cube 色彩會變更為青色。</span><span class="sxs-lookup"><span data-stu-id="b69ba-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="b69ba-269">若要讓體驗更加有趣，請使用您剛學習的內容，設定每個按鈕將 cube 變更為不同的色彩。</span><span class="sxs-lookup"><span data-stu-id="b69ba-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="b69ba-270">將文字新增至您的場景</span><span class="sxs-lookup"><span data-stu-id="b69ba-270">Adding text into your scene</span></span>

<span data-ttu-id="b69ba-271">在本節中，您將瞭解如何使用 Unity 的 TextMesh Pro （您在上一個教學課程的匯[入 TextMesh Pro 基本資源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)一節中所準備），將文字新增至您的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="b69ba-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="b69ba-272">在此特定範例中，您會在上一節中建立的按鈕集合底下新增一個簡單標籤。</span><span class="sxs-lookup"><span data-stu-id="b69ba-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="b69ba-273">以滑鼠右鍵按一下 [ButtonCollection] 物件，然後選取 [ **3D 物件**] > [ **TextMeshPro** ]，將 TextMeshPro 物件建立為 ButtonCollection 物件的子系：</span><span class="sxs-lookup"><span data-stu-id="b69ba-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="b69ba-275">當新建立的 TextMeshPro 物件（名為 Text （TMP））仍為選取狀態時，在 [偵測器] 視窗中，變更其位置和大小，讓標籤整齊地放在按鈕集合底下，例如：</span><span class="sxs-lookup"><span data-stu-id="b69ba-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="b69ba-276">將矩形轉換**Pos Y**變更為-0.0425</span><span class="sxs-lookup"><span data-stu-id="b69ba-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="b69ba-277">將 [矩形轉換**寬度**] 變更為0.24</span><span class="sxs-lookup"><span data-stu-id="b69ba-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="b69ba-278">將矩形轉換**高度**變更為0.024</span><span class="sxs-lookup"><span data-stu-id="b69ba-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="b69ba-279">然後更新文字以反映標籤的用途，並選擇 [字型屬性]，讓文字元合標籤，例如：</span><span class="sxs-lookup"><span data-stu-id="b69ba-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="b69ba-280">將文本網格 Pro （腳本）**文字**變更為按鈕集合</span><span class="sxs-lookup"><span data-stu-id="b69ba-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="b69ba-281">將文本網格 Pro （腳本）**字型樣式**變更為粗體</span><span class="sxs-lookup"><span data-stu-id="b69ba-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="b69ba-282">將文本網格 Pro （腳本）**字型大小**變更為0。2</span><span class="sxs-lookup"><span data-stu-id="b69ba-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="b69ba-283">將文本網格 Pro （腳本）**對齊**變更為置中和中間</span><span class="sxs-lookup"><span data-stu-id="b69ba-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="b69ba-285">恭喜</span><span class="sxs-lookup"><span data-stu-id="b69ba-285">Congratulations</span></span>

<span data-ttu-id="b69ba-286">在本教學課程中，您已瞭解如何複製、自訂和設定 MRTK 設定檔設定。</span><span class="sxs-lookup"><span data-stu-id="b69ba-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="b69ba-287">您也已瞭解如何與按鈕互動，以使用 HoloLens 2 上的追蹤來觸發事件。</span><span class="sxs-lookup"><span data-stu-id="b69ba-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="b69ba-288">最後，您已瞭解如何使用 MRTK 的 Grid 物件集合元件和 Unity 的文本網格 Pro 來建立簡單的 UI 介面。</span><span class="sxs-lookup"><span data-stu-id="b69ba-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="b69ba-289">下一個教學課程： 4. 放置動態內容並使用解析器</span><span class="sxs-lookup"><span data-stu-id="b69ba-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
