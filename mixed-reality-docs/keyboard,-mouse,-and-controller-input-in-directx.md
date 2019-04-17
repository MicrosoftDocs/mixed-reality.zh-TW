---
title: 鍵盤、 滑鼠及 DirectX 中的控制站輸入
description: 說明如何建立會使用鍵盤、 滑鼠及遊戲控制器的 Windows Mixed Reality 應用程式。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 鍵盤、 滑鼠、 遊戲控制器、 xbox 控制器、 HoloLens、 桌面、 逐步解說、 範例程式碼
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597119"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>鍵盤、 滑鼠及 DirectX 中的控制站輸入

鍵盤、 滑鼠及遊戲控制器都可以很有用的形式的 Windows Mixed Reality 裝置的輸入。 藍芽鍵盤和滑鼠都支援 HoloLens，用於偵錯您的應用程式，或是做為替代形式的輸入。 Windows Mixed Reality 也支援連接至 Pc-其中滑鼠、 鍵盤及遊戲控制器一直以來的範數的沈浸式耳機。

若要使用鍵盤輸入上 HoloLens，對您的裝置到藍芽鍵盤或透過 Windows Device Portal 虛擬輸入。 若要使用鍵盤輸入穿著 Windows Mixed Reality 沈浸式耳機時，將輸入的焦點指派給混合實境，藉由將放在裝置上，或使用 Windows 鍵 + Y 鍵盤組合。 請記住供 HoloLens 的應用程式必須提供的功能，而不需要這些連接的裝置。

>[!NOTE]
>目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。  概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。

## <a name="subscribe-for-corewindow-input-events"></a>Corewindow，否則輸入事件訂閱

### <a name="keyboard-input"></a>鍵盤輸入

在 Windows 全像攝影版的應用程式範本中，我們包含了鍵盤輸入，就像任何其他的 UWP 應用程式的事件處理常式。 您的應用程式會使用鍵盤輸入的資料相同的方式，在 Windows Mixed Reality。

從 AppView.cpp:

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

### <a name="virtual-keyboard-input"></a>虛擬的鍵盤輸入
沉浸式桌面耳機，您也可以支援虛擬鍵盤，呈現 Windows 透過沉浸式檢視。 若要支援此功能，您的應用程式可以實作**CoreTextEditContext**。 這可讓 Windows 了解您的應用程式轉譯文字方塊的狀態，以便虛擬鍵盤可以正確地參與那里的文字。

如需有關如何實作 CoreTextEditContext 支援的詳細資訊，請參閱[CoreTextEditContext 範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。

### <a name="mouse-input"></a>滑鼠輸入

您也可以使用滑鼠輸入，再透過 UWP CoreWindow 輸入的事件處理常式。 以下是如何修改 Windows 全像攝影版的應用程式範本，以支援在相同的方式為已按下動作的滑鼠點按。 之後進行這個修改之後，按一下滑鼠時頭戴耳機沈浸式裝置將會重新調整 cube。

請注意，UWP 應用程式也可以取得滑鼠的未經處理的 xy 圖資料使用[MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API。

開始先宣告新的處理常式 OnPointerPressed AppView.h 中：

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

在 AppView.cpp，請先 SetWindow 中加入此程式碼：

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

然後在檔案底部將 OnPointerPressed 此定義：

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

我們剛才加入的事件處理常式是傳遞至範本的主要類別。 讓我們修改主要的類別，以支援這個傳遞。 這個公用方法，將宣告加入至標頭檔：

```
// Handle mouse input.
       void OnPointerPressed();
```

您將需要此私用成員變數，以及：

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

最後，我們將更新新的邏輯，以支援滑鼠點按的主要類別。 將此事件處理常式來開始。 請務必更新的類別名稱：

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

現在，在更新方法中，將現有的邏輯，以取得與這個指標姿勢：

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

重新編譯並重新部署。 您應該注意到，按一下滑鼠將會現在重新調整 cube 中您的沈浸式耳機-或 HoloLens 與附加的藍芽滑鼠。

### <a name="game-controller-support"></a>遊戲控制器支援

遊戲控制器可以有趣且允許使用者便利的方式來控制 Windows Mixed Reality 沉浸式體驗。

將遊戲控制器的支援新增至 Windows 全像攝影版的應用程式範本，第一個步驟是將下列的私用成員宣告新增至您的主要檔案的標頭類別：

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

初始化遊樂器事件，與任何遊戲台目前連接，您的主要類別的建構函式：

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

這些事件處理常式加入您的主要類別。 請務必更新的類別名稱：

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

最後，更新輸入的邏輯，以識別變更控制器狀態。 在這裡，我們會使用相同的 m_pointerPressed 變數加入滑鼠事件前一節所述。 將下列加入更新方法之前它會檢查用 SpatialPointerPose 的,：

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

別忘了取消註冊事件時清除 主要類別：

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

重新編譯，並重新部署。 您現在可以附加，或配對，遊戲控制器和使用它來重新定位的旋轉立方體。

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>鍵盤和滑鼠輸入的重要方針

有一些主要的差異，在這段程式碼如何使用 Microsoft HoloLens – 也就是主要是依賴自然的使用者輸入 – 與 Windows Mixed Reality 啟用的電腦上可用的裝置上。
* 您不能依賴鍵盤或滑鼠輸入必須存在。 所有功能，您的應用程式必須使用視線、 手勢和語音輸入。
* 當附加藍芽鍵盤時，很有幫助啟用您的應用程式可能會要求的任何文字的鍵盤輸入。 這可以是很好的補充資訊，如語音輸入，例如。
* 談到設計您的應用程式時，不要依賴 （舉例來說） WASD 和滑鼠會尋求您的遊戲中的控制項。 HoloLens 專為引導房間周圍的使用者。 在此情況下，使用者控制相機直接。 推動觀景窗移動/外觀的控制項與房間周圍的介面不會提供相同的體驗。
* 鍵盤輸入可以控制您的應用程式或遊戲引擎，偵錯的層面，特別是當使用者將不需要使用鍵盤的絕佳方式。 因為您還可使用與 corewindow，否則事件 Api 串聯起都相同。 在此案例中，您可能會選擇實作設定您的應用程式，將鍵盤事件路由傳送至 「 偵錯僅輸入 」 的模式在您偵錯工作階段期間的方法。
* 藍牙控制器正常運作。

## <a name="see-also"></a>另請參閱
* [硬體附屬應用程式](hardware-accessories.md)
