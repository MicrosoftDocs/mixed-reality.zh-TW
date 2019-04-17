---
title: 視線、 手勢和在 DirectX 中的動作控制站
description: 結合輸入的來自視線、 手勢和移動控制站，您可以讓使用者將雷射放在您的應用程式。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 視線、 手勢、 動作控制站、 directx、 輸入、 全像投影
ms.openlocfilehash: 7cee3d3d7fbcd903eae0376e205034b9cc4ead3b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597122"
---
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a><span data-ttu-id="7c0c3-104">視線、 手勢和在 DirectX 中的動作控制站</span><span class="sxs-lookup"><span data-stu-id="7c0c3-104">Gaze, gestures, and motion controllers in DirectX</span></span>

<span data-ttu-id="7c0c3-105">如果您要直接在平台上建置，您必須處理使用者-例如，使用者會透過查詢的輸入的來自[前端的視線](gaze.md)，而且使用者已選取使用[筆勢](gestures.md)或[動作控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-105">If you're going to build directly on top of the platform, you will have to handle input coming from the user - such as where the user is looking via [head gaze](gaze.md) and what the user has selected with [gestures](gestures.md) or [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="7c0c3-106">結合這些形式的輸入，您可以讓使用者放置[闀](hologram.md)應用程式中。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-106">Combining these forms of input, you can enable a user to place a [hologram](hologram.md) in your app.</span></span> <span data-ttu-id="7c0c3-107">[全像攝影版的應用程式範本](creating-a-holographic-directx-project.md)，有一個簡單易用的範例。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-107">The [holographic app template](creating-a-holographic-directx-project.md) has an easy to use example.</span></span>

>[!NOTE]
><span data-ttu-id="7c0c3-108">目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="7c0c3-109">概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="gaze-input"></a><span data-ttu-id="7c0c3-110">注視輸入</span><span class="sxs-lookup"><span data-stu-id="7c0c3-110">Gaze input</span></span>

<span data-ttu-id="7c0c3-111">若要存取使用者的[前端的視線](gaze.md)，您使用[SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx)型別。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-111">To access the user's [head gaze](gaze.md), you use the [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) type.</span></span> <span data-ttu-id="7c0c3-112">全像攝影版的應用程式範本包含了解視線的基本程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-112">The holographic app template includes basic code for understanding gaze.</span></span> <span data-ttu-id="7c0c3-113">此程式碼提供向前指，頭尾包括在內的使用者看的因此納入考量，裝置的位置和方向的向量給定[座標系統](coordinate-systems-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-113">This code provides a vector pointing forward from between the user's eyes, taking into account the device's position and orientation in a given [coordinate system](coordinate-systems-in-directx.md).</span></span>




```cpp
void SpinningCubeRenderer::PositionHologram(SpatialPointerPose^ pointerPose)
{
    if (pointerPose != nullptr)
    {
        // Get the gaze direction relative to the given coordinate system.
        const float3 headPosition    = pointerPose->Head->Position;
        const float3 headDirection   = pointerPose->Head->ForwardDirection;
    
        // The hologram is positioned two meters along the user's gaze direction.
        static const float distanceFromUser = 2.0f; // meters
        const float3 gazeAtTwoMeters        = headPosition + (distanceFromUser * headDirection);
    
        // This will be used as the translation component of the hologram's
        // model transform.
        SetPosition(gazeAtTwoMeters);
    }
}
```

<span data-ttu-id="7c0c3-114">您可能會發現自問：「 但是座標系統來自何處？ 」</span><span class="sxs-lookup"><span data-stu-id="7c0c3-114">You may find yourself asking: "But where does the coordinate system come from?"</span></span>

<span data-ttu-id="7c0c3-115">讓我們來回答這個問題。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-115">Let's answer that question.</span></span> <span data-ttu-id="7c0c3-116">在我們的 AppMain**更新**函式中，我們處理空間的輸入的事件我們 StationaryFrameOfReference 的該屬性取得相對座標系統。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-116">In our AppMain's **Update** function, we processed a spatial input event by acquiring it relative to the coordinate system for our StationaryFrameOfReference.</span></span> <span data-ttu-id="7c0c3-117">您應該記得我們設定時，就建立 StationaryFrameOfReference [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)，並在開頭取得座標系統[更新](rendering-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-117">Recall that the StationaryFrameOfReference was created when we set up the [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), and the coordinate system was acquired at the start of [Update](rendering-in-directx.md).</span></span>




```cpp
// Check for new input state since the last frame.
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
if (pointerState != nullptr)
{
    // When a Pressed gesture is detected, the sample hologram will be repositioned
    // two meters in front of the user.
    m_spinningCubeRenderer->PositionHologram(
        pointerState->TryGetPointerPose(currentCoordinateSystem)
        );
}
```

<span data-ttu-id="7c0c3-118">請注意，繫結至某種類型的指標狀態的資料。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-118">Note that the data is tied to a pointer state of some kind.</span></span> <span data-ttu-id="7c0c3-119">我們會取得此空間的輸入事件。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-119">We get this from a spatial input event.</span></span> <span data-ttu-id="7c0c3-120">事件資料物件包含座標系統，因此您一律可以產生事件時的視線方向關聯至任何您所需要的空間座標系統。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-120">The event data object includes a coordinate system, so that you can always relate the gaze direction at the time of the event to whatever spatial coordinate system you need.</span></span> <span data-ttu-id="7c0c3-121">事實上，您必須執行才能取得指標姿勢。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-121">In fact, you must do so in order to get the pointer pose.</span></span>

> [!NOTE]
> <span data-ttu-id="7c0c3-122">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-122">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gesture-and-motion-controller-input"></a><span data-ttu-id="7c0c3-123">輸入手勢和動作的控制器</span><span class="sxs-lookup"><span data-stu-id="7c0c3-123">Gesture and motion controller input</span></span>

<span data-ttu-id="7c0c3-124">Windows Mixed Reality，在同時送[筆勢](gestures.md)並[動作控制站](motion-controllers.md)位於相同空間輸入的 Api，透過處理[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-124">In Windows Mixed Reality, both hand [gestures](gestures.md) and [motion controllers](motion-controllers.md) are handled through the same spatial input APIs, found in the [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span></span> <span data-ttu-id="7c0c3-125">這可讓您輕鬆地處理常見的動作，如**選取**按下相同的方式，跨雙手及動作控制站。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-125">This enables you to easily handle common actions like **Select** presses the same way across both hands and motion controllers.</span></span>

<span data-ttu-id="7c0c3-126">有兩種處理筆勢或移動控制站在混合實境中時，您可以針對的 API 層級：</span><span class="sxs-lookup"><span data-stu-id="7c0c3-126">There are two levels of API you can target when handling gestures or motion controllers in mixed reality:</span></span>
* <span data-ttu-id="7c0c3-127">[互動](gestures.md#the-two-core-gestures-of-hololens)([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx)， [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx)並[SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx))，存取使用[SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span><span class="sxs-lookup"><span data-stu-id="7c0c3-127">[Interactions](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) and [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), accessed using a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span></span>
* <span data-ttu-id="7c0c3-128">[複合筆勢](gestures.md#composite-gestures)([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx)，按住不放，操作，瀏覽)，存取使用[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span><span class="sxs-lookup"><span data-stu-id="7c0c3-128">[Composite gestures](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), Hold, Manipulation, Navigation), accessed using a [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span></span>

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a><span data-ttu-id="7c0c3-129">選取/功能表/掌握/觸控板/搖桿互動：SpatialInteractionManager</span><span class="sxs-lookup"><span data-stu-id="7c0c3-129">Select/Menu/Grasp/Touchpad/Thumbstick interactions: SpatialInteractionManager</span></span>

<span data-ttu-id="7c0c3-130">若要跨雙手及 Windows Mixed Reality 中的輸入的裝置，偵測到低層級的動作、 版本和更新，您從啟動[SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-130">To detect low-level presses, releases and updates across hands and input devices in Windows Mixed Reality, you start from a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span></span> <span data-ttu-id="7c0c3-131">動作控制器已偵測到輸入或 SpatialInteractionManager 發生事件時，通知應用程式時手的形狀。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-131">The SpatialInteractionManager has an event that informs the app when a hand or motion controller has detected input.</span></span>

<span data-ttu-id="7c0c3-132">有三種金鑰 SpatialInteractionSource，分別由不同的 SpatialInteractionSourceKind 值：</span><span class="sxs-lookup"><span data-stu-id="7c0c3-132">There are three key kinds of SpatialInteractionSource, each represented by a different SpatialInteractionSourceKind value:</span></span>
* <span data-ttu-id="7c0c3-133">**手狀**表示偵測到使用者的手。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-133">**Hand** represents a user's detected hand.</span></span> <span data-ttu-id="7c0c3-134">手狀來源是僅適用於 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-134">Hand sources are available only on HoloLens.</span></span>
* <span data-ttu-id="7c0c3-135">**控制器**代表配對的移動控制站。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-135">**Controller** represents a paired motion controller.</span></span> <span data-ttu-id="7c0c3-136">動作控制站可以提供的各種功能，例如：選取觸發程序 」、 「 功能表按鈕 」、 「 掌握按鈕 」、 「 跳動和 「 搖桿。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-136">Motion controllers can offer a variety of capabilities, for example: Select triggers, Menu buttons, Grasp buttons, touchpads and thumbsticks.</span></span>
* <span data-ttu-id="7c0c3-137">**語音**代表使用者的語音讀出系統偵測到的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-137">**Voice** represents the user's voice speaking system-detected keywords.</span></span> <span data-ttu-id="7c0c3-138">這將會插入選取的按下並放開每當使用者講的是 [選取]。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-138">This will inject a Select press and release whenever the user says "Select".</span></span>

<span data-ttu-id="7c0c3-139">若要偵測按下任何這些互動的來源，您可以處理中 SpatialInputHandler.cpp SpatialInteractionManager SourcePressed 事件：</span><span class="sxs-lookup"><span data-stu-id="7c0c3-139">To detect presses across any of these interaction sources, you can handle the SourcePressed event on SpatialInteractionManager in SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

<span data-ttu-id="7c0c3-140">這個已按下的事件會以非同步方式傳送至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-140">This pressed event is sent to your app asynchronously.</span></span> <span data-ttu-id="7c0c3-141">您的應用程式或遊戲引擎可能會想要執行一些處理立即或您可能想要在您處理常式的輸入事件資料排入佇列。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-141">Your app or game engine may want to perform some processing right away or you may want to queue up the event data in your input processing routine.</span></span>

<span data-ttu-id="7c0c3-142">此範本包括 helper 類別，可協助您開始使用。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-142">The template includes a helper class to get you started.</span></span> <span data-ttu-id="7c0c3-143">此範本 forgoes 為了簡單起見，設計的任何處理。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-143">This template forgoes any processing for simplicity of design.</span></span> <span data-ttu-id="7c0c3-144">會追蹤的協助程式類別，是否有一個或多個**Pressed**自從上次發生的事件**更新**呼叫。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-144">The helper class keeps track of whether one or more **Pressed** events occurred since the last **Update** call.</span></span> <span data-ttu-id="7c0c3-145">從 SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="7c0c3-145">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourcePressed(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    m_sourceState = args->State;
    
    //
    // TODO: In your app or game engine, rewrite this method to queue
    //       input events in your input class or event handler.
    //
}
```

<span data-ttu-id="7c0c3-146">如果，則會傳回[SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)最新的輸入事件，在下一步 的更新。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-146">If so, it returns the [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) for the most recent input event during the next Update.</span></span> <span data-ttu-id="7c0c3-147">從 SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="7c0c3-147">From SpatialInputHandler.cpp:</span></span>




```cpp
// Checks if the user performed an input gesture since the last call to this method.
// Allows the main update loop to check for asynchronous changes to the user
// input state.
SpatialInteractionSourceState^ SpatialInputHandler::CheckForInput()
{
    SpatialInteractionSourceState^ sourceState = m_sourceState;
    m_sourceState = nullptr;
    return sourceState;
}
```

<span data-ttu-id="7c0c3-148">請注意，上述程式碼會將所有按下相同的方式，是否在使用者執行主要**選取**按也非次要**功能表**或**抓住**按下。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-148">Note that the code above will treat all presses the same way, whether the user is performing a primary **Select** press or a secondary **Menu** or **Grasp** press.</span></span> <span data-ttu-id="7c0c3-149">**選取**按是一種指針、 控制器和語音，觸發透過執行此動作控制器會執行其主要的觸發程序/按鈕按下的空中點選，手動的動作或使用者的受支援的互動的主要形式語音說出"Select"。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-149">The **Select** press is a primary form of interaction supported across hands, motion controllers and voice, triggered either by a hand performing an air-tap, a motion controller with its primary trigger/button pressed, or the user's voice saying "Select".</span></span> <span data-ttu-id="7c0c3-150">選取的動作表示使用者来啟用它們的目標全像。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-150">Select presses represent the user's intention to activate the hologram they are targeting.</span></span>

<span data-ttu-id="7c0c3-151">按下哪種推斷發生，我們將修改 SpatialInteractionManager::SourceUpdated 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-151">To reason about which kind of press is occurring, we will modify the SpatialInteractionManager::SourceUpdated event handler.</span></span> <span data-ttu-id="7c0c3-152">我們的程式碼會偵測掌握按下 （如果適用的話），並使用它們來調整此 cube 的位置。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-152">Our code will detect Grasp presses (where available) and use them to reposition the cube.</span></span> <span data-ttu-id="7c0c3-153">如果找不到掌握，我們將改為使用選取的動作。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-153">If Grasp is not available, we will use Select presses instead.</span></span>

<span data-ttu-id="7c0c3-154">下列的私用成員宣告加入 SpatialInputHandler.h:</span><span class="sxs-lookup"><span data-stu-id="7c0c3-154">Add the following private member declarations to SpatialInputHandler.h:</span></span> 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

<span data-ttu-id="7c0c3-155">Open SpatialInputHandler.cpp.</span><span class="sxs-lookup"><span data-stu-id="7c0c3-155">Open SpatialInputHandler.cpp.</span></span> <span data-ttu-id="7c0c3-156">新增下列事件註冊建構函式：</span><span class="sxs-lookup"><span data-stu-id="7c0c3-156">Add the following event registration to the constructor:</span></span> 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

<span data-ttu-id="7c0c3-157">這是事件處理常式程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-157">This is the event handler code.</span></span> <span data-ttu-id="7c0c3-158">如果輸入的來源發生掌握下, 一個更新迴圈將會儲存指標姿勢。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-158">If the input source is experiencing a Grasp, the pointer pose will be stored for the next update loop.</span></span> <span data-ttu-id="7c0c3-159">否則，它會檢查選取的按改為。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-159">Otherwise, it will check for a Select press instead.</span></span> <span data-ttu-id="7c0c3-160">從 SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="7c0c3-160">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourceUpdated(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    if (args->State->Source->IsGraspSupported)
    {
        if (args->State->IsGrasped)
        {
            m_sourceState = args->State;
        }
    }
    else
    {
        if (args->State->IsSelectPressed)
        {
            m_sourceState = args->State;
        }
    }
}
```

<span data-ttu-id="7c0c3-161">請務必先取消註冊事件處理常式，解構函式中。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-161">Make sure to unregister the event handler in the destructor.</span></span> <span data-ttu-id="7c0c3-162">從 SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="7c0c3-162">From SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

<span data-ttu-id="7c0c3-163">重新編譯，並重新部署。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-163">Recompile, and then redeploy.</span></span> <span data-ttu-id="7c0c3-164">您的專案範本現在應該能夠辨識掌握互動，即可重新定位的旋轉立方體。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-164">Your template project should now be able to recognize Grasp interactions to reposition the spinning cube.</span></span>

<span data-ttu-id="7c0c3-165">SpatialInteractionSource API 支援各種不同功能的控制站。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-165">The SpatialInteractionSource API supports controllers with a wide range of capabilities.</span></span> <span data-ttu-id="7c0c3-166">在上述範例中，我們檢查查看掌握是否支援然後再嘗試使用它。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-166">In the example shown above, we check to see if Grasp is supported before trying to use it.</span></span> <span data-ttu-id="7c0c3-167">SpatialInteractionSource 支援下列選用功能超越一般**選取**按下：</span><span class="sxs-lookup"><span data-stu-id="7c0c3-167">The SpatialInteractionSource supports the following optional features beyond the common **Select** press:</span></span>
* <span data-ttu-id="7c0c3-168">**功能表按鈕：** 檢查支援，藉由檢查 IsMenuSupported 屬性。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-168">**Menu button:** Check support by inspecting the IsMenuSupported property.</span></span> <span data-ttu-id="7c0c3-169">支援時，檢查[SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)屬性，以找出是否有 [功能表] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-169">When supported, check the [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if the menu button is pressed.</span></span>
* <span data-ttu-id="7c0c3-170">**掌握按鈕：** 檢查支援，藉由檢查 IsGraspSupported 屬性。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-170">**Grasp button:** Check support by inspecting the IsGraspSupported property.</span></span> <span data-ttu-id="7c0c3-171">支援時，檢查[SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)屬性，查明是否已啟動掌握。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-171">When supported, check the [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if grasp is activated.</span></span>

<span data-ttu-id="7c0c3-172">控制站，SpatialInteractionSource 有一個控制器屬性與其他功能。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-172">For controllers, the SpatialInteractionSource has a Controller property with additional capabilities.</span></span>
* <span data-ttu-id="7c0c3-173">**HasThumbstick:** 如果為 true，則控制器會有搖桿。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-173">**HasThumbstick:** If true, the controller has a thumbstick.</span></span> <span data-ttu-id="7c0c3-174">檢查[ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties)屬性取得搖桿 SpatialInteractionSourceState x 和 y 值 （ThumbstickX 和 ThumbstickY），以及其已按下的狀態 (IsThumbstickPressed)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-174">Inspect the [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) property of the SpatialInteractionSourceState to acquire the thumbstick x and y values (ThumbstickX and ThumbstickY), as well as its pressed state (IsThumbstickPressed).</span></span>
* <span data-ttu-id="7c0c3-175">**HasTouchpad:** 如果為 true，則控制器會有觸控板。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-175">**HasTouchpad:** If true, the controller has a touchpad.</span></span> <span data-ttu-id="7c0c3-176">檢查取得觸控板 SpatialInteractionSourceState ControllerProperties 屬性 x 和 y 值 （TouchpadX 和 TouchpadY），並知道在使用者觸碰板 (IsTouchpadTouched)，以及它們會按下 （觸控板IsTouchpadPressed)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-176">Inspect the ControllerProperties property of the SpatialInteractionSourceState to acquire the touchpad x and y values (TouchpadX and TouchpadY), and to know if the user is touching the pad (IsTouchpadTouched) and if they are pressing the touchpad down (IsTouchpadPressed).</span></span>
* <span data-ttu-id="7c0c3-177">**SimpleHapticsController:** 控制器 SimpleHapticsController API 可讓您檢查控制器，haptics 功能，也可讓您控制 haptic 意見反應。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-177">**SimpleHapticsController:** The SimpleHapticsController API for the controller allows you to inspect the haptics capabilities of the controller, and it also allows you to control haptic feedback.</span></span>

<span data-ttu-id="7c0c3-178">請注意，觸控板和搖桿從-1 為兩個座標軸的 1 （從下至上的情況下，以及從左到右） 的範圍。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-178">Note that the range for touchpad and thumbstick from -1 to 1 for both axes (from bottom to top, and from left to right).</span></span> <span data-ttu-id="7c0c3-179">類比的觸發程序存取使用 SpatialInteractionSourceState::SelectPressedValue; 屬性，此範圍會有 0 到 1 的範圍。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-179">The range for the analog trigger, which is accessed using the SpatialInteractionSourceState::SelectPressedValue property, has a range of 0 to 1.</span></span> <span data-ttu-id="7c0c3-180">值為 1 IsSelectPressed 設為 true，而且所使用的相互關聯任何其他值相互關聯與 IsSelectPressed 等於 false。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-180">A value of 1 correlates with IsSelectPressed being equal to true; any other value correlates with IsSelectPressed being equal to false.</span></span>

<span data-ttu-id="7c0c3-181">請注意，在手的形狀和控制站使用 SpatialInteractionSourceState::Properties::TryGetLocation 會提供使用者的游標位置-這是表示控制器的指標光線指標姿勢有所區別。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-181">Note that for both a hand and a controller, using SpatialInteractionSourceState::Properties::TryGetLocation will provide the user's hand position - this is distinct from the pointer pose representing the controller's pointing ray.</span></span> <span data-ttu-id="7c0c3-182">如果您想要的項目繪製 hand 位置，使用 TryGetLocation。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-182">If you want to draw something at the hand location, use TryGetLocation.</span></span> <span data-ttu-id="7c0c3-183">如果您想要 raycast 提示中的控制器，請從上 SpatialPointerPose TryGetInteractionSourcePose 中取得指標的光跡。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-183">If you want to raycast from the tip of the controller, get the pointing ray from TryGetInteractionSourcePose on the SpatialPointerPose.</span></span>

<span data-ttu-id="7c0c3-184">您也可以使用上 SpatialInteractionManager，例如 SourceDetected 和 SourceLost，其他事件，以回應時手進入或離開裝置的檢視或它們移入或移出好的位置 （食指引發 palm 轉寄），或當動作開啟和關閉或配對/未成對的控制站。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-184">You can also use the other events on SpatialInteractionManager, such as SourceDetected and SourceLost, to react when hands enter or leave the device's view or when they move in or out of the ready position (index finger raised with palm forward), or when motion controllers are turned on/off or are paired/unpaired.</span></span>

### <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="7c0c3-185">指標的姿勢與的底框姿勢</span><span class="sxs-lookup"><span data-stu-id="7c0c3-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="7c0c3-186">Windows Mixed Reality 支援各種不同的外型規格中的動作控制站，與每個控制站設計不同使用者的手狀位置和 「 轉送 」 方向該應用程式的自然之間關聯性的相對值應該使用指出呈現時控制站。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="7c0c3-187">若要更能代表這些控制站，有兩種您可以進行互動的每個來源的調查會帶來：</span><span class="sxs-lookup"><span data-stu-id="7c0c3-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>
* <span data-ttu-id="7c0c3-188">**底框姿勢**，表示偵測到的 HoloLens，一隻手的或翲保存動作控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-188">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="7c0c3-189">沈浸式耳機，在此姿勢最適合用來呈現**使用者的手**或是**物件保留在使用者的手**劍或槍等。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-189">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="7c0c3-190">**抓住位置**:Palm 距心自然，保留控制器時調整左邊或右邊，置中的底框的位置。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-190">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="7c0c3-191">**抓住方向的右座標軸**:當您完全開啟以形成平坦的 5 手指姿勢手時，光線，一般是您 palm （從左 palm、 從右 palm 回溯順向）</span><span class="sxs-lookup"><span data-stu-id="7c0c3-191">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="7c0c3-192">**抓住方向的順向軸**:當您關閉您的手部分 （如同保存在控制站）、"forward"tube 透過由非 thumb 手指點光線。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-192">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="7c0c3-193">**抓住方向的總軸**:隱含的權限和轉送的定義總軸。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-193">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="7c0c3-194">您可以透過調整底框姿勢[SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span><span class="sxs-lookup"><span data-stu-id="7c0c3-194">You can access the grip pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span></span>
* <span data-ttu-id="7c0c3-195">**指標姿勢**，代表向前指的控制站的提示。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-195">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="7c0c3-196">此姿勢最適合用於 raycast 時**指向 UI**當您要在其中呈現控制器模型本身。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-196">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="7c0c3-197">您可以存取透過指標姿勢[SpatialInteractionSourceState.Properties.TryGetLocation(...)。SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或[SpatialInteractionSourceState.TryGetPointerPose(...)。TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-197">You can access the pointer pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...).SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) or [SpatialInteractionSourceState.TryGetPointerPose(...).TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span></span>

### <a name="composite-gestures-spatialgesturerecognizer"></a><span data-ttu-id="7c0c3-198">複合筆勢：SpatialGestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="7c0c3-198">Composite gestures: SpatialGestureRecognizer</span></span>

<span data-ttu-id="7c0c3-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)解譯使用其前端的視線哪一個使用者目標的介面的空間軌跡事件，從實際操作、 移動控制器和"Select"語音命令的使用者互動。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interprets user interactions from hands, motion controllers, and the "Select" voice command to surface spatial gesture events, which users target using their head gaze.</span></span>

<span data-ttu-id="7c0c3-200">空間軌跡是輸入的索引鍵形式的 Windows Mixed Reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-200">Spatial gestures are a key form of input for Windows Mixed Reality apps.</span></span> <span data-ttu-id="7c0c3-201">藉由路由至全像 SpatialGestureRecognizer 從 SpatialInteractionManager 互動，應用程式可以偵測點選、 保留、 操作及瀏覽事件一致地跨指針、 語音和空間的輸入的裝置，而不需要處理按下並手動釋放。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-201">By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.</span></span>

<span data-ttu-id="7c0c3-202">SpatialGestureRecognizer 執行只有最少去除混淆您要求的筆勢集合之間。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-202">SpatialGestureRecognizer performs only the minimal disambiguation between the set of gestures that you request.</span></span> <span data-ttu-id="7c0c3-203">比方說，如果您要求只點選時，使用者可能按住他們的手指，只要他們喜歡和點選，還是會發生。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-203">For example, if you request just Tap, the user may hold their finger down as long as they like and a Tap will still occur.</span></span> <span data-ttu-id="7c0c3-204">如果您要求同時點選並按住不放，約一秒鐘的按住他們的手指，軌跡會將升級至保留後點選將不再發生。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-204">If you request both Tap and Hold, after about a second of holding down their finger, the gesture will promote to a Hold and a Tap will no longer occur.</span></span>

<span data-ttu-id="7c0c3-205">若要使用 SpatialGestureRecognizer，處理 SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)事件，並抓取 SpatialPointerPose 那里公開。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-205">To use SpatialGestureRecognizer, handle the SpatialInteractionManager's [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) event and grab the SpatialPointerPose exposed there.</span></span> <span data-ttu-id="7c0c3-206">使用使用者的前端的視線光線，從這個姿勢與全像投影交集和介面網狀結構中使用者的周圍環境，以判斷使用者準備進行互動。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-206">Use the user's head gaze ray from this pose to intersect with the holograms and surface meshes in the user's surroundings, in order to determine what the user is intending to interact with.</span></span> <span data-ttu-id="7c0c3-207">然後，路由 SpatialInteraction 傳送目標全像 SpatialGestureRecognizer 的事件引數中使用其[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)方法。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-207">Then, route the SpatialInteraction in the event arguments to the target hologram's SpatialGestureRecognizer, using its [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) method.</span></span> <span data-ttu-id="7c0c3-208">這會啟動解譯根據該互動[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings)該辨識器上設定，或在建立時- [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-208">This starts interpreting that interaction according to the [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) set on that recognizer at creation time - or by [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span></span>

<span data-ttu-id="7c0c3-209">HoloLens 上, 互動和筆勢應該通常衍生其目標從使用者的前端的視線，而不是嘗試轉譯，或直接互動的游標位置。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-209">On HoloLens, interactions and gestures should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="7c0c3-210">一旦啟動互動，相對的左手邊的動作可用來控制鍵筆勢，如同操作或瀏覽軌跡。</span><span class="sxs-lookup"><span data-stu-id="7c0c3-210">Once an interaction has started, relative motions of the hand may be used to control the gesture, as with the Manipulation or Navigation gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c0c3-211">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c0c3-211">See also</span></span>
* [<span data-ttu-id="7c0c3-212">Gaze</span><span class="sxs-lookup"><span data-stu-id="7c0c3-212">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="7c0c3-213">筆勢</span><span class="sxs-lookup"><span data-stu-id="7c0c3-213">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="7c0c3-214">動作控制站</span><span class="sxs-lookup"><span data-stu-id="7c0c3-214">Motion controllers</span></span>](motion-controllers.md)
