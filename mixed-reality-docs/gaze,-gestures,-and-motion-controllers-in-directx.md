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
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a>視線、 手勢和在 DirectX 中的動作控制站

如果您要直接在平台上建置，您必須處理使用者-例如，使用者會透過查詢的輸入的來自[前端的視線](gaze.md)，而且使用者已選取使用[筆勢](gestures.md)或[動作控制器](motion-controllers.md)。 結合這些形式的輸入，您可以讓使用者放置[闀](hologram.md)應用程式中。 [全像攝影版的應用程式範本](creating-a-holographic-directx-project.md)，有一個簡單易用的範例。

>[!NOTE]
>目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。  概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。

## <a name="gaze-input"></a>注視輸入

若要存取使用者的[前端的視線](gaze.md)，您使用[SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx)型別。 全像攝影版的應用程式範本包含了解視線的基本程式碼。 此程式碼提供向前指，頭尾包括在內的使用者看的因此納入考量，裝置的位置和方向的向量給定[座標系統](coordinate-systems-in-directx.md)。




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

您可能會發現自問：「 但是座標系統來自何處？ 」

讓我們來回答這個問題。 在我們的 AppMain**更新**函式中，我們處理空間的輸入的事件我們 StationaryFrameOfReference 的該屬性取得相對座標系統。 您應該記得我們設定時，就建立 StationaryFrameOfReference [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)，並在開頭取得座標系統[更新](rendering-in-directx.md)。




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

請注意，繫結至某種類型的指標狀態的資料。 我們會取得此空間的輸入事件。 事件資料物件包含座標系統，因此您一律可以產生事件時的視線方向關聯至任何您所需要的空間座標系統。 事實上，您必須執行才能取得指標姿勢。

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。

## <a name="gesture-and-motion-controller-input"></a>輸入手勢和動作的控制器

Windows Mixed Reality，在同時送[筆勢](gestures.md)並[動作控制站](motion-controllers.md)位於相同空間輸入的 Api，透過處理[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)命名空間。 這可讓您輕鬆地處理常見的動作，如**選取**按下相同的方式，跨雙手及動作控制站。

有兩種處理筆勢或移動控制站在混合實境中時，您可以針對的 API 層級：
* [互動](gestures.md#the-two-core-gestures-of-hololens)([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx)， [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx)並[SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx))，存取使用[SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)
* [複合筆勢](gestures.md#composite-gestures)([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx)，按住不放，操作，瀏覽)，存取使用[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a>選取/功能表/掌握/觸控板/搖桿互動：SpatialInteractionManager

若要跨雙手及 Windows Mixed Reality 中的輸入的裝置，偵測到低層級的動作、 版本和更新，您從啟動[SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)。 動作控制器已偵測到輸入或 SpatialInteractionManager 發生事件時，通知應用程式時手的形狀。

有三種金鑰 SpatialInteractionSource，分別由不同的 SpatialInteractionSourceKind 值：
* **手狀**表示偵測到使用者的手。 手狀來源是僅適用於 HoloLens。
* **控制器**代表配對的移動控制站。 動作控制站可以提供的各種功能，例如：選取觸發程序 」、 「 功能表按鈕 」、 「 掌握按鈕 」、 「 跳動和 「 搖桿。
* **語音**代表使用者的語音讀出系統偵測到的關鍵字。 這將會插入選取的按下並放開每當使用者講的是 [選取]。

若要偵測按下任何這些互動的來源，您可以處理中 SpatialInputHandler.cpp SpatialInteractionManager SourcePressed 事件：


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

這個已按下的事件會以非同步方式傳送至您的應用程式。 您的應用程式或遊戲引擎可能會想要執行一些處理立即或您可能想要在您處理常式的輸入事件資料排入佇列。

此範本包括 helper 類別，可協助您開始使用。 此範本 forgoes 為了簡單起見，設計的任何處理。 會追蹤的協助程式類別，是否有一個或多個**Pressed**自從上次發生的事件**更新**呼叫。 從 SpatialInputHandler.cpp:




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

如果，則會傳回[SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)最新的輸入事件，在下一步 的更新。 從 SpatialInputHandler.cpp:




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

請注意，上述程式碼會將所有按下相同的方式，是否在使用者執行主要**選取**按也非次要**功能表**或**抓住**按下。 **選取**按是一種指針、 控制器和語音，觸發透過執行此動作控制器會執行其主要的觸發程序/按鈕按下的空中點選，手動的動作或使用者的受支援的互動的主要形式語音說出"Select"。 選取的動作表示使用者来啟用它們的目標全像。

按下哪種推斷發生，我們將修改 SpatialInteractionManager::SourceUpdated 事件處理常式。 我們的程式碼會偵測掌握按下 （如果適用的話），並使用它們來調整此 cube 的位置。 如果找不到掌握，我們將改為使用選取的動作。

下列的私用成員宣告加入 SpatialInputHandler.h: 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

Open SpatialInputHandler.cpp. 新增下列事件註冊建構函式： 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

這是事件處理常式程式碼。 如果輸入的來源發生掌握下, 一個更新迴圈將會儲存指標姿勢。 否則，它會檢查選取的按改為。 從 SpatialInputHandler.cpp:




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

請務必先取消註冊事件處理常式，解構函式中。 從 SpatialInputHandler.cpp:


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

重新編譯，並重新部署。 您的專案範本現在應該能夠辨識掌握互動，即可重新定位的旋轉立方體。

SpatialInteractionSource API 支援各種不同功能的控制站。 在上述範例中，我們檢查查看掌握是否支援然後再嘗試使用它。 SpatialInteractionSource 支援下列選用功能超越一般**選取**按下：
* **功能表按鈕：** 檢查支援，藉由檢查 IsMenuSupported 屬性。 支援時，檢查[SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)屬性，以找出是否有 [功能表] 按鈕已按下。
* **掌握按鈕：** 檢查支援，藉由檢查 IsGraspSupported 屬性。 支援時，檢查[SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)屬性，查明是否已啟動掌握。

控制站，SpatialInteractionSource 有一個控制器屬性與其他功能。
* **HasThumbstick:** 如果為 true，則控制器會有搖桿。 檢查[ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties)屬性取得搖桿 SpatialInteractionSourceState x 和 y 值 （ThumbstickX 和 ThumbstickY），以及其已按下的狀態 (IsThumbstickPressed)。
* **HasTouchpad:** 如果為 true，則控制器會有觸控板。 檢查取得觸控板 SpatialInteractionSourceState ControllerProperties 屬性 x 和 y 值 （TouchpadX 和 TouchpadY），並知道在使用者觸碰板 (IsTouchpadTouched)，以及它們會按下 （觸控板IsTouchpadPressed)。
* **SimpleHapticsController:** 控制器 SimpleHapticsController API 可讓您檢查控制器，haptics 功能，也可讓您控制 haptic 意見反應。

請注意，觸控板和搖桿從-1 為兩個座標軸的 1 （從下至上的情況下，以及從左到右） 的範圍。 類比的觸發程序存取使用 SpatialInteractionSourceState::SelectPressedValue; 屬性，此範圍會有 0 到 1 的範圍。 值為 1 IsSelectPressed 設為 true，而且所使用的相互關聯任何其他值相互關聯與 IsSelectPressed 等於 false。

請注意，在手的形狀和控制站使用 SpatialInteractionSourceState::Properties::TryGetLocation 會提供使用者的游標位置-這是表示控制器的指標光線指標姿勢有所區別。 如果您想要的項目繪製 hand 位置，使用 TryGetLocation。 如果您想要 raycast 提示中的控制器，請從上 SpatialPointerPose TryGetInteractionSourcePose 中取得指標的光跡。

您也可以使用上 SpatialInteractionManager，例如 SourceDetected 和 SourceLost，其他事件，以回應時手進入或離開裝置的檢視或它們移入或移出好的位置 （食指引發 palm 轉寄），或當動作開啟和關閉或配對/未成對的控制站。

### <a name="grip-pose-vs-pointing-pose"></a>指標的姿勢與的底框姿勢

Windows Mixed Reality 支援各種不同的外型規格中的動作控制站，與每個控制站設計不同使用者的手狀位置和 「 轉送 」 方向該應用程式的自然之間關聯性的相對值應該使用指出呈現時控制站。

若要更能代表這些控制站，有兩種您可以進行互動的每個來源的調查會帶來：
* **底框姿勢**，表示偵測到的 HoloLens，一隻手的或翲保存動作控制器的位置。
    * 沈浸式耳機，在此姿勢最適合用來呈現**使用者的手**或是**物件保留在使用者的手**劍或槍等。
    * **抓住位置**:Palm 距心自然，保留控制器時調整左邊或右邊，置中的底框的位置。
    * **抓住方向的右座標軸**:當您完全開啟以形成平坦的 5 手指姿勢手時，光線，一般是您 palm （從左 palm、 從右 palm 回溯順向）
    * **抓住方向的順向軸**:當您關閉您的手部分 （如同保存在控制站）、"forward"tube 透過由非 thumb 手指點光線。
    * **抓住方向的總軸**:隱含的權限和轉送的定義總軸。
    * 您可以透過調整底框姿勢[SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).
* **指標姿勢**，代表向前指的控制站的提示。
    * 此姿勢最適合用於 raycast 時**指向 UI**當您要在其中呈現控制器模型本身。
    * 您可以存取透過指標姿勢[SpatialInteractionSourceState.Properties.TryGetLocation(...)。SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或[SpatialInteractionSourceState.TryGetPointerPose(...)。TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)。

### <a name="composite-gestures-spatialgesturerecognizer"></a>複合筆勢：SpatialGestureRecognizer

A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)解譯使用其前端的視線哪一個使用者目標的介面的空間軌跡事件，從實際操作、 移動控制器和"Select"語音命令的使用者互動。

空間軌跡是輸入的索引鍵形式的 Windows Mixed Reality 應用程式。 藉由路由至全像 SpatialGestureRecognizer 從 SpatialInteractionManager 互動，應用程式可以偵測點選、 保留、 操作及瀏覽事件一致地跨指針、 語音和空間的輸入的裝置，而不需要處理按下並手動釋放。

SpatialGestureRecognizer 執行只有最少去除混淆您要求的筆勢集合之間。 比方說，如果您要求只點選時，使用者可能按住他們的手指，只要他們喜歡和點選，還是會發生。 如果您要求同時點選並按住不放，約一秒鐘的按住他們的手指，軌跡會將升級至保留後點選將不再發生。

若要使用 SpatialGestureRecognizer，處理 SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)事件，並抓取 SpatialPointerPose 那里公開。 使用使用者的前端的視線光線，從這個姿勢與全像投影交集和介面網狀結構中使用者的周圍環境，以判斷使用者準備進行互動。 然後，路由 SpatialInteraction 傳送目標全像 SpatialGestureRecognizer 的事件引數中使用其[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)方法。 這會啟動解譯根據該互動[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings)該辨識器上設定，或在建立時- [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)。

HoloLens 上, 互動和筆勢應該通常衍生其目標從使用者的前端的視線，而不是嘗試轉譯，或直接互動的游標位置。 一旦啟動互動，相對的左手邊的動作可用來控制鍵筆勢，如同操作或瀏覽軌跡。

## <a name="see-also"></a>另請參閱
* [Gaze](gaze.md)
* [筆勢](gestures.md)
* [動作控制站](motion-controllers.md)
