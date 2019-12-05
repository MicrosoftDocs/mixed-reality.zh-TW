---
title: DirectX 中的鍵盤、滑鼠和控制器輸入
description: 說明如何為使用鍵盤、滑鼠和遊戲控制器的 Windows Mixed Reality 建立應用程式。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，鍵盤，滑鼠，遊戲控制器，xbox controller，HoloLens，桌面，逐步解說，範例程式碼
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835094"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>DirectX 中的鍵盤、滑鼠和控制器輸入

鍵盤、滑鼠和遊戲控制器對於 Windows Mixed Reality 裝置而言，都是很有用的輸入形式。 HoloLens 支援藍牙鍵盤和滑鼠，可用於對您的應用程式進行偵測，或做為替代形式的輸入。 Windows Mixed Reality 也支援連接到電腦的沉浸式耳機，其中滑鼠、鍵盤和遊戲控制器的過去都是標準。

若要在 HoloLens 上使用鍵盤輸入，請將藍牙鍵盤與您的裝置配對，或透過 Windows 裝置入口網站使用虛擬輸入。 若要在戴上 Windows Mixed Reality 沉浸式耳機時使用鍵盤輸入，請將輸入焦點放在裝置上，或使用 Windows 鍵 + Y 鍵盤組合，將其指派給混合式。 請記住，適用于 HoloLens 的應用程式必須提供未連接這些裝置的功能。

>[!NOTE]
>本文中的程式碼片段目前示範如何使用C++/cx， C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT，如全像攝影專案範本中所使用。  概念相當於C++/WinRT 專案，但您必須轉譯程式碼。

## <a name="subscribe-for-corewindow-input-events"></a>訂閱 CoreWindow 輸入事件

### <a name="keyboard-input"></a>鍵盤輸入

在 Windows 全像攝影應用程式範本中，我們包含鍵盤輸入的事件處理常式，就像任何其他 UWP 應用程式一樣。 您的應用程式使用鍵盤輸入資料的方式，與 Windows Mixed Reality 相同。

從 AppView：

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>虛擬鍵盤輸入
對於沉浸式桌面耳機，您也可以透過沉浸式視圖支援 Windows 所呈現的虛擬鍵盤。 為了支援這種情況，您的應用程式可以執行**CoreTextEditCoNtext**。 這可讓 Windows 瞭解您自己的應用程式轉譯文字方塊的狀態，讓虛擬鍵盤能夠正確地參與該處的文字。

如需有關如何執行 CoreTextEditCoNtext 支援的詳細資訊，請參閱[CoreTextEditCoNtext 範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。

### <a name="mouse-input"></a>滑鼠輸入

您也可以透過 UWP CoreWindow 輸入事件處理常式，再次使用滑鼠輸入。 以下說明如何修改 Windows 全像投影應用程式範本，以支援滑鼠點按動作，就像按下手勢一樣。 進行此修改之後，在戴上沉浸式耳機裝置時按一下滑鼠，會重新調整 cube 的位置。

請注意，UWP 應用程式也可以使用[MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API 取得滑鼠的原始 XY 資料。

一開始先在 AppView 中宣告新的 OnPointerPressed 處理常式：

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

在 AppView 中，將下列程式碼新增至 SetWindow：

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

然後將 OnPointerPressed 的這個定義放在檔案的底部：

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

我們剛才加入的事件處理常式是範本主要類別的傳遞。 讓我們修改主要類別以支援此傳遞。 將這個公用方法宣告加入標頭檔中：

```
// Handle mouse input.
       void OnPointerPressed();
```

您也需要此私用成員變數，如下所示：

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

最後，我們將使用新的邏輯來更新主要類別，以支援滑鼠點擊。 從加入此事件處理常式開始。 請務必更新類別名稱：

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

現在，在 Update 方法中，將用來取得指標的現有邏輯取代為：

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

重新編譯和重新部署。 您應該會注意到按一下滑鼠後，就會將 cube 重新放置在您的沉浸式耳機-或 HoloLens 中，並連接藍牙滑鼠。

### <a name="game-controller-support"></a>遊戲控制器支援

遊戲控制器是一種有趣且方便的方式，可讓使用者控制沉浸式 Windows Mixed Reality 體驗。

將遊戲控制器的支援新增至 Windows 全像攝影應用程式範本的第一個步驟，是將下列私用成員宣告新增至主要檔案的標頭類別：

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

在您的主要類別的函式中，初始化遊戲程式事件，以及目前附加的任何遊戲台：

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

將這些事件處理常式新增至您的主要類別。 請務必更新類別名稱：

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

最後，更新輸入邏輯以辨識控制器狀態中的變更。 在這裡，我們使用上一節中所討論的相同 m_pointerPressed 變數來加入滑鼠事件。 將此檔案新增至 Update 方法，就在其檢查 SpatialPointerPose 之前：

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

清除主要類別時，別忘了取消註冊事件：

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

重新編譯，然後重新部署。 您現在可以連接或配對遊戲控制器，並用它來重新調整旋轉 cube 的位置。

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>鍵盤和滑鼠輸入的重要指導方針

此程式碼在 Microsoft HoloLens 上的使用方式有一些主要差異–這是主要依賴自然使用者輸入的裝置–與 Windows Mixed Reality 啟用的電腦上所提供的相同。
* 您不能依賴鍵盤或滑鼠輸入來呈現。 您所有的應用程式功能都必須使用「注視」、「手勢」和「語音輸入」。
* 連接 Bluetooth 鍵盤時，針對您的應用程式可能會要求的任何文字啟用鍵盤輸入可能會很有説明。 例如，這可能是聽寫的絕佳補充。
* 在設計您的應用程式時，請不要依賴您遊戲的 WASD 和滑鼠外觀控制項（例如）。 HoloLens 的設計目的是要讓使用者在房間附近。 在此情況下，使用者會直接控制相機。 使用移動/外觀控制來驅動房間相機的介面，將不會提供相同的體驗。
* 鍵盤輸入是控制應用程式或遊戲引擎之調試層面的絕佳方式，尤其是因為使用者不需要使用鍵盤。 連接的方式與使用 CoreWindow 事件 Api 時相同。 在此案例中，您可以選擇執行方法，將您的應用程式設定為在您的 debug 會話期間將鍵盤事件路由至「僅限偵錯工具輸入」模式。
* Bluetooth 控制器也會運作。

## <a name="see-also"></a>請參閱
* [硬體配件](hardware-accessories.md)
