---
title: Unity 中的鍵盤輸入
description: Unity 提供 TouchScreenKeyboard 類別，可在沒有可用的實體鍵盤時接受鍵盤輸入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 鍵盤、輸入、unity、touchscreenkeyboard
ms.openlocfilehash: f506415f9658d9723bf31b339d63fe4569100ace
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438558"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="7d14b-104">Unity 中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="7d14b-104">Keyboard input in Unity</span></span>

<span data-ttu-id="7d14b-105">**命名空間：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="7d14b-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="7d14b-106">**類型**：  *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="7d14b-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="7d14b-107">雖然 HoloLens 支援許多形式的輸入，包括藍牙鍵盤，但大部分的應用程式都無法假設所有使用者都有可用的實體鍵盤。</span><span class="sxs-lookup"><span data-stu-id="7d14b-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="7d14b-108">如果您的應用程式需要文字輸入，則應該提供某種形式的螢幕小鍵盤。</span><span class="sxs-lookup"><span data-stu-id="7d14b-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="7d14b-109">Unity 提供 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 類別，可在沒有可用的實體鍵盤時接受鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="7d14b-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="7d14b-110">在 Unity 中的 HoloLens 系統鍵盤行為</span><span class="sxs-lookup"><span data-stu-id="7d14b-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="7d14b-111">在 HoloLens 上， *TouchScreenKeyboard*會利用系統的螢幕小鍵盤。</span><span class="sxs-lookup"><span data-stu-id="7d14b-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="7d14b-112">系統的 [螢幕小鍵盤] 無法在體積型視圖上重迭，因此 Unity 必須建立次要 2D XAML 視圖來顯示鍵盤，然後在送出輸入之後回到體積型 view。</span><span class="sxs-lookup"><span data-stu-id="7d14b-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="7d14b-113">使用者流程如下所示：</span><span class="sxs-lookup"><span data-stu-id="7d14b-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="7d14b-114">使用者執行動作，導致應用程式代碼呼叫*TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="7d14b-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="7d14b-115">在呼叫*TouchScreenKeyboard*之前，應用程式會負責暫停應用程式狀態</span><span class="sxs-lookup"><span data-stu-id="7d14b-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="7d14b-116">應用程式可能會在切換回體積型視圖之前終止</span><span class="sxs-lookup"><span data-stu-id="7d14b-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="7d14b-117">Unity 切換為自動放在世界中的 2D XAML 視圖</span><span class="sxs-lookup"><span data-stu-id="7d14b-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="7d14b-118">使用者使用系統鍵盤輸入文字並提交或取消</span><span class="sxs-lookup"><span data-stu-id="7d14b-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="7d14b-119">Unity 切換回體積型視圖</span><span class="sxs-lookup"><span data-stu-id="7d14b-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="7d14b-120">當*TouchScreenKeyboard*完成時，應用程式會負責繼續應用程式狀態</span><span class="sxs-lookup"><span data-stu-id="7d14b-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="7d14b-121">提交的文字可在*TouchScreenKeyboard*中取得</span><span class="sxs-lookup"><span data-stu-id="7d14b-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="7d14b-122">可用的鍵盤流覽</span><span class="sxs-lookup"><span data-stu-id="7d14b-122">Available keyboard views</span></span>

<span data-ttu-id="7d14b-123">有六種不同的鍵盤視圖可供使用：</span><span class="sxs-lookup"><span data-stu-id="7d14b-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="7d14b-124">單行文字方塊</span><span class="sxs-lookup"><span data-stu-id="7d14b-124">Single-line textbox</span></span>
* <span data-ttu-id="7d14b-125">含標題的單行文字方塊</span><span class="sxs-lookup"><span data-stu-id="7d14b-125">Single-line textbox with title</span></span>
* <span data-ttu-id="7d14b-126">多行文字方塊</span><span class="sxs-lookup"><span data-stu-id="7d14b-126">Multi-line textbox</span></span>
* <span data-ttu-id="7d14b-127">具有標題的多行文字方塊</span><span class="sxs-lookup"><span data-stu-id="7d14b-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="7d14b-128">單行密碼方塊</span><span class="sxs-lookup"><span data-stu-id="7d14b-128">Single-line password box</span></span>
* <span data-ttu-id="7d14b-129">具有標題的單行密碼方塊</span><span class="sxs-lookup"><span data-stu-id="7d14b-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="7d14b-130">如何在 Unity 中啟用系統鍵盤</span><span class="sxs-lookup"><span data-stu-id="7d14b-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="7d14b-131">HoloLens 系統鍵盤僅適用于以「UWP 組建類型」設定為「XAML」的 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d14b-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="7d14b-132">當您選擇「XAML」做為「UWP 組建類型」而不是「D3D」時，會產生取捨。</span><span class="sxs-lookup"><span data-stu-id="7d14b-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="7d14b-133">如果您不熟悉這些取捨，您可能會想要探索系統鍵盤的[替代輸入解決方案](#alternative-keyboard-options)。</span><span class="sxs-lookup"><span data-stu-id="7d14b-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="7d14b-134">開啟 [**檔案] 功能表，然後**選取 [**組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="7d14b-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="7d14b-135">確定**平臺**已設定為 [ **Windows Store**]， **SDK**設定為 [**通用 10**]，並將**UWP 組建類型**設定為 [ **XAML**]。</span><span class="sxs-lookup"><span data-stu-id="7d14b-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="7d14b-136">在 [**組建設定**] 對話方塊中，按一下 [ **Player 設定 ...** ] 按鈕</span><span class="sxs-lookup"><span data-stu-id="7d14b-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="7d14b-137">選取 [ **Windows Store 的設定**] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="7d14b-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="7d14b-138">展開 [**其他設定**] 群組</span><span class="sxs-lookup"><span data-stu-id="7d14b-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="7d14b-139">**在轉譯區段中**，勾選 [**支援虛擬實境**] 核取方塊，以新增**虛擬實境裝置**清單</span><span class="sxs-lookup"><span data-stu-id="7d14b-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="7d14b-140">確保**Windows**全像顯示在虛擬實境 sdk 清單中</span><span class="sxs-lookup"><span data-stu-id="7d14b-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="7d14b-141">如果您未將此組建標示為 HoloLens 裝置所支援的虛擬實境，專案將會匯出為 2D XAML 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d14b-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="7d14b-142">在 Unity 應用程式中使用系統鍵盤</span><span class="sxs-lookup"><span data-stu-id="7d14b-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="7d14b-143">宣告鍵盤</span><span class="sxs-lookup"><span data-stu-id="7d14b-143">Declare the keyboard</span></span>

<span data-ttu-id="7d14b-144">在類別中，宣告用來儲存*TouchScreenKeyboard*的變數，以及用來保存鍵盤所傳回之字串的變數。</span><span class="sxs-lookup"><span data-stu-id="7d14b-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="7d14b-145">叫用鍵盤</span><span class="sxs-lookup"><span data-stu-id="7d14b-145">Invoke the keyboard</span></span>

<span data-ttu-id="7d14b-146">當要求鍵盤輸入時發生事件時，請根據所需的輸入類型呼叫其中一個函式。</span><span class="sxs-lookup"><span data-stu-id="7d14b-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="7d14b-147">請注意，標題是在 textPlaceholder 參數中指定。</span><span class="sxs-lookup"><span data-stu-id="7d14b-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="7d14b-148">取出具類型的內容</span><span class="sxs-lookup"><span data-stu-id="7d14b-148">Retrieve typed contents</span></span>

<span data-ttu-id="7d14b-149">在更新迴圈中，檢查鍵盤是否收到新的輸入，並加以儲存以供其他地方使用。</span><span class="sxs-lookup"><span data-stu-id="7d14b-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="7d14b-150">替代鍵盤選項</span><span class="sxs-lookup"><span data-stu-id="7d14b-150">Alternative keyboard options</span></span>

<span data-ttu-id="7d14b-151">我們瞭解，將體積型視圖切換到2D 視圖並不是取得使用者文字輸入的理想方式。</span><span class="sxs-lookup"><span data-stu-id="7d14b-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="7d14b-152">透過 Unity 運用系統鍵盤的目前替代方案包括：</span><span class="sxs-lookup"><span data-stu-id="7d14b-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="7d14b-153">使用語音聽寫進行輸入（<b>注意：</b>這通常容易發生在字典中找不到的單字，且不適合用于密碼輸入）</span><span class="sxs-lookup"><span data-stu-id="7d14b-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="7d14b-154">建立可在應用程式獨佔視圖中運作的鍵盤</span><span class="sxs-lookup"><span data-stu-id="7d14b-154">Create a keyboard that works in your applications exclusive view</span></span>
