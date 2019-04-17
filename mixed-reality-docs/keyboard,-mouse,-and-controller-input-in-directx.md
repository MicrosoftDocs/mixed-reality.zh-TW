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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="9ef6d-104">鍵盤、 滑鼠及 DirectX 中的控制站輸入</span><span class="sxs-lookup"><span data-stu-id="9ef6d-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="9ef6d-105">鍵盤、 滑鼠及遊戲控制器都可以很有用的形式的 Windows Mixed Reality 裝置的輸入。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="9ef6d-106">藍芽鍵盤和滑鼠都支援 HoloLens，用於偵錯您的應用程式，或是做為替代形式的輸入。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="9ef6d-107">Windows Mixed Reality 也支援連接至 Pc-其中滑鼠、 鍵盤及遊戲控制器一直以來的範數的沈浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="9ef6d-108">若要使用鍵盤輸入上 HoloLens，對您的裝置到藍芽鍵盤或透過 Windows Device Portal 虛擬輸入。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="9ef6d-109">若要使用鍵盤輸入穿著 Windows Mixed Reality 沈浸式耳機時，將輸入的焦點指派給混合實境，藉由將放在裝置上，或使用 Windows 鍵 + Y 鍵盤組合。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="9ef6d-110">請記住供 HoloLens 的應用程式必須提供的功能，而不需要這些連接的裝置。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="9ef6d-111">目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="9ef6d-112">概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="9ef6d-113">Corewindow，否則輸入事件訂閱</span><span class="sxs-lookup"><span data-stu-id="9ef6d-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="9ef6d-114">鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="9ef6d-114">Keyboard input</span></span>

<span data-ttu-id="9ef6d-115">在 Windows 全像攝影版的應用程式範本中，我們包含了鍵盤輸入，就像任何其他的 UWP 應用程式的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="9ef6d-116">您的應用程式會使用鍵盤輸入的資料相同的方式，在 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="9ef6d-117">從 AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="9ef6d-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="9ef6d-118">虛擬的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="9ef6d-118">Virtual keyboard input</span></span>
<span data-ttu-id="9ef6d-119">沉浸式桌面耳機，您也可以支援虛擬鍵盤，呈現 Windows 透過沉浸式檢視。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="9ef6d-120">若要支援此功能，您的應用程式可以實作**CoreTextEditContext**。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="9ef6d-121">這可讓 Windows 了解您的應用程式轉譯文字方塊的狀態，以便虛擬鍵盤可以正確地參與那里的文字。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="9ef6d-122">如需有關如何實作 CoreTextEditContext 支援的詳細資訊，請參閱[CoreTextEditContext 範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="9ef6d-123">滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="9ef6d-123">Mouse Input</span></span>

<span data-ttu-id="9ef6d-124">您也可以使用滑鼠輸入，再透過 UWP CoreWindow 輸入的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="9ef6d-125">以下是如何修改 Windows 全像攝影版的應用程式範本，以支援在相同的方式為已按下動作的滑鼠點按。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="9ef6d-126">之後進行這個修改之後，按一下滑鼠時頭戴耳機沈浸式裝置將會重新調整 cube。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="9ef6d-127">請注意，UWP 應用程式也可以取得滑鼠的未經處理的 xy 圖資料使用[MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="9ef6d-128">開始先宣告新的處理常式 OnPointerPressed AppView.h 中：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="9ef6d-129">在 AppView.cpp，請先 SetWindow 中加入此程式碼：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="9ef6d-130">然後在檔案底部將 OnPointerPressed 此定義：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="9ef6d-131">我們剛才加入的事件處理常式是傳遞至範本的主要類別。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="9ef6d-132">讓我們修改主要的類別，以支援這個傳遞。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="9ef6d-133">這個公用方法，將宣告加入至標頭檔：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="9ef6d-134">您將需要此私用成員變數，以及：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="9ef6d-135">最後，我們將更新新的邏輯，以支援滑鼠點按的主要類別。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="9ef6d-136">將此事件處理常式來開始。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-136">Start by adding this event handler.</span></span> <span data-ttu-id="9ef6d-137">請務必更新的類別名稱：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="9ef6d-138">現在，在更新方法中，將現有的邏輯，以取得與這個指標姿勢：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="9ef6d-139">重新編譯並重新部署。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-139">Recompile and redeploy.</span></span> <span data-ttu-id="9ef6d-140">您應該注意到，按一下滑鼠將會現在重新調整 cube 中您的沈浸式耳機-或 HoloLens 與附加的藍芽滑鼠。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="9ef6d-141">遊戲控制器支援</span><span class="sxs-lookup"><span data-stu-id="9ef6d-141">Game controller support</span></span>

<span data-ttu-id="9ef6d-142">遊戲控制器可以有趣且允許使用者便利的方式來控制 Windows Mixed Reality 沉浸式體驗。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="9ef6d-143">將遊戲控制器的支援新增至 Windows 全像攝影版的應用程式範本，第一個步驟是將下列的私用成員宣告新增至您的主要檔案的標頭類別：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="9ef6d-144">初始化遊樂器事件，與任何遊戲台目前連接，您的主要類別的建構函式：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="9ef6d-145">這些事件處理常式加入您的主要類別。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="9ef6d-146">請務必更新的類別名稱：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="9ef6d-147">最後，更新輸入的邏輯，以識別變更控制器狀態。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="9ef6d-148">在這裡，我們會使用相同的 m_pointerPressed 變數加入滑鼠事件前一節所述。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="9ef6d-149">將下列加入更新方法之前它會檢查用 SpatialPointerPose 的,：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="9ef6d-150">別忘了取消註冊事件時清除 主要類別：</span><span class="sxs-lookup"><span data-stu-id="9ef6d-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="9ef6d-151">重新編譯，並重新部署。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-151">Recompile, and redeploy.</span></span> <span data-ttu-id="9ef6d-152">您現在可以附加，或配對，遊戲控制器和使用它來重新定位的旋轉立方體。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="9ef6d-153">鍵盤和滑鼠輸入的重要方針</span><span class="sxs-lookup"><span data-stu-id="9ef6d-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="9ef6d-154">有一些主要的差異，在這段程式碼如何使用 Microsoft HoloLens – 也就是主要是依賴自然的使用者輸入 – 與 Windows Mixed Reality 啟用的電腦上可用的裝置上。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="9ef6d-155">您不能依賴鍵盤或滑鼠輸入必須存在。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="9ef6d-156">所有功能，您的應用程式必須使用視線、 手勢和語音輸入。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="9ef6d-157">當附加藍芽鍵盤時，很有幫助啟用您的應用程式可能會要求的任何文字的鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="9ef6d-158">這可以是很好的補充資訊，如語音輸入，例如。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="9ef6d-159">談到設計您的應用程式時，不要依賴 （舉例來說） WASD 和滑鼠會尋求您的遊戲中的控制項。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="9ef6d-160">HoloLens 專為引導房間周圍的使用者。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="9ef6d-161">在此情況下，使用者控制相機直接。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="9ef6d-162">推動觀景窗移動/外觀的控制項與房間周圍的介面不會提供相同的體驗。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="9ef6d-163">鍵盤輸入可以控制您的應用程式或遊戲引擎，偵錯的層面，特別是當使用者將不需要使用鍵盤的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="9ef6d-164">因為您還可使用與 corewindow，否則事件 Api 串聯起都相同。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="9ef6d-165">在此案例中，您可能會選擇實作設定您的應用程式，將鍵盤事件路由傳送至 「 偵錯僅輸入 」 的模式在您偵錯工作階段期間的方法。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="9ef6d-166">藍牙控制器正常運作。</span><span class="sxs-lookup"><span data-stu-id="9ef6d-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ef6d-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ef6d-167">See also</span></span>
* [<span data-ttu-id="9ef6d-168">硬體附屬應用程式</span><span class="sxs-lookup"><span data-stu-id="9ef6d-168">Hardware accessories</span></span>](hardware-accessories.md)
