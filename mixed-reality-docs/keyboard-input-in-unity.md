---
title: 在 Unity 中的鍵盤輸入
description: Unity 提供 TouchScreenKeyboard 類別時不沒有可用的任何實體鍵盤接受鍵盤輸入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 鍵盤輸入，unity touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597039"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="b47b3-104">在 Unity 中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="b47b3-104">Keyboard input in Unity</span></span>

<span data-ttu-id="b47b3-105">\**命名空間：\*\*\*UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="b47b3-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="b47b3-106">**類型**：*[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="b47b3-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="b47b3-107">雖然 HoloLens 支援許多形式的輸入包括藍芽鍵盤，大部分的應用程式不能假設所有使用者都有可用的實體鍵盤。</span><span class="sxs-lookup"><span data-stu-id="b47b3-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="b47b3-108">如果您的應用程式需要文字輸入，則應該提供某種形式的螢幕小鍵盤。</span><span class="sxs-lookup"><span data-stu-id="b47b3-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="b47b3-109">Unity 提供*[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 時不沒有可用的任何實體鍵盤接受鍵盤輸入的類別。</span><span class="sxs-lookup"><span data-stu-id="b47b3-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="b47b3-110">在 Unity 中的 HoloLens 系統鍵盤行為</span><span class="sxs-lookup"><span data-stu-id="b47b3-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="b47b3-111">HoloLens，在*TouchScreenKeyboard*運用系統的螢幕小鍵盤。</span><span class="sxs-lookup"><span data-stu-id="b47b3-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="b47b3-112">體積型檢視上方重疊，因此必須要建立次要 2D XAML 檢視，以顯示鍵盤，則傳回回到體積型檢視中，提交輸入之後的 Unity 無法系統的螢幕小鍵盤。</span><span class="sxs-lookup"><span data-stu-id="b47b3-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="b47b3-113">使用者流程如下所示：</span><span class="sxs-lookup"><span data-stu-id="b47b3-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="b47b3-114">使用者執行動作導致應用程式程式碼呼叫*TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="b47b3-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="b47b3-115">應用程式會負責暫停的應用程式狀態，然後再呼叫*TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="b47b3-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="b47b3-116">應用程式可能會終止之前曾經切換回到體積型檢視</span><span class="sxs-lookup"><span data-stu-id="b47b3-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="b47b3-117">Unity 會切換成 2D 的 XAML 檢視也就是世界中的 自動放置</span><span class="sxs-lookup"><span data-stu-id="b47b3-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="b47b3-118">使用者輸入文字時，使用系統鍵盤和送出或取消</span><span class="sxs-lookup"><span data-stu-id="b47b3-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="b47b3-119">Unity 會切換回體積型檢視</span><span class="sxs-lookup"><span data-stu-id="b47b3-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="b47b3-120">應用程式會負責繼續執行應用程式時*TouchScreenKeyboard*完成</span><span class="sxs-lookup"><span data-stu-id="b47b3-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="b47b3-121">已送出的文字可用於*TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="b47b3-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="b47b3-122">可用鍵盤的檢視</span><span class="sxs-lookup"><span data-stu-id="b47b3-122">Available keyboard views</span></span>

<span data-ttu-id="b47b3-123">有六個不同的鍵盤檢視：</span><span class="sxs-lookup"><span data-stu-id="b47b3-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="b47b3-124">單行文字方塊</span><span class="sxs-lookup"><span data-stu-id="b47b3-124">Single-line textbox</span></span>
* <span data-ttu-id="b47b3-125">標題的單行文字方塊</span><span class="sxs-lookup"><span data-stu-id="b47b3-125">Single-line textbox with title</span></span>
* <span data-ttu-id="b47b3-126">多行文字方塊</span><span class="sxs-lookup"><span data-stu-id="b47b3-126">Multi-line textbox</span></span>
* <span data-ttu-id="b47b3-127">標題的多行文字方塊</span><span class="sxs-lookup"><span data-stu-id="b47b3-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="b47b3-128">單行密碼方塊</span><span class="sxs-lookup"><span data-stu-id="b47b3-128">Single-line password box</span></span>
* <span data-ttu-id="b47b3-129">標題的單行密碼方塊</span><span class="sxs-lookup"><span data-stu-id="b47b3-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="b47b3-130">如何啟用系統鍵盤在 Unity 中</span><span class="sxs-lookup"><span data-stu-id="b47b3-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="b47b3-131">只有適用於 Unity 應用程式會使用 [UWP 建置類型] 設定為"XAML"匯出 HoloLens 系統鍵盤。</span><span class="sxs-lookup"><span data-stu-id="b47b3-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="b47b3-132">沒有您選擇 [UWP 建置類型] 為"XAML"透過 「 D3D 」 時所做的權衡取捨。</span><span class="sxs-lookup"><span data-stu-id="b47b3-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="b47b3-133">如果您不熟悉這些權衡取捨，您可能想要探索[解決方案的替代輸入](#alternative-keyboard-options)系統鍵盤。</span><span class="sxs-lookup"><span data-stu-id="b47b3-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="b47b3-134">開啟**檔案**功能表，然後選取**組建設定...**</span><span class="sxs-lookup"><span data-stu-id="b47b3-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="b47b3-135">確保**平台**設為**Windows 市集**，則**SDK**設定為**通用 10**，並設定**UWP 建置型別**要**XAML**。</span><span class="sxs-lookup"><span data-stu-id="b47b3-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="b47b3-136">在 **組建設定** 對話方塊中，按一下 **播放程式設定...** 按鈕</span><span class="sxs-lookup"><span data-stu-id="b47b3-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="b47b3-137">選取 [**設定適用於 Windows 市集**] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="b47b3-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="b47b3-138">依序展開**其他設定**群組</span><span class="sxs-lookup"><span data-stu-id="b47b3-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="b47b3-139">在 **轉譯**區段中，按一下**虛擬實境支援**核取方塊以加入新**虛擬實境裝置**清單</span><span class="sxs-lookup"><span data-stu-id="b47b3-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="b47b3-140">請確定**Windows 全像攝影版**會出現在清單中的虛擬實境 Sdk</span><span class="sxs-lookup"><span data-stu-id="b47b3-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="b47b3-141">如果您不與 HoloLens 裝置，將建置標示為受支援的虛擬實境中，專案會匯出為 2D XAML 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b47b3-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="b47b3-142">在您的 Unity 應用程式中使用系統鍵盤</span><span class="sxs-lookup"><span data-stu-id="b47b3-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="b47b3-143">宣告鍵盤</span><span class="sxs-lookup"><span data-stu-id="b47b3-143">Declare the keyboard</span></span>

<span data-ttu-id="b47b3-144">在類別中，宣告一個變數來存放*TouchScreenKeyboard* ，並傳回變數，以容納字串鍵盤。</span><span class="sxs-lookup"><span data-stu-id="b47b3-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="b47b3-145">叫用鍵盤</span><span class="sxs-lookup"><span data-stu-id="b47b3-145">Invoke the keyboard</span></span>

<span data-ttu-id="b47b3-146">要求的鍵盤輸入發生事件時，呼叫其中一個函式所需的輸入類型而定。</span><span class="sxs-lookup"><span data-stu-id="b47b3-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="b47b3-147">請注意，標題會 textPlaceholder 參數中指定。</span><span class="sxs-lookup"><span data-stu-id="b47b3-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

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

### <a name="retrieve-typed-contents"></a><span data-ttu-id="b47b3-148">擷取具類型的內容</span><span class="sxs-lookup"><span data-stu-id="b47b3-148">Retrieve typed contents</span></span>

<span data-ttu-id="b47b3-149">在更新迴圈中，檢查是否鍵盤接收到新的輸入並將它儲存在其他地方使用。</span><span class="sxs-lookup"><span data-stu-id="b47b3-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

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

## <a name="alternative-keyboard-options"></a><span data-ttu-id="b47b3-150">替代鍵盤選項</span><span class="sxs-lookup"><span data-stu-id="b47b3-150">Alternative keyboard options</span></span>

<span data-ttu-id="b47b3-151">我們了解切換移出的 2D 檢視的體積型檢視不是最理想的方式從使用者取得文字輸入。</span><span class="sxs-lookup"><span data-stu-id="b47b3-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="b47b3-152">目前的替代方案，運用系統鍵盤，透過 Unity 包括：</span><span class="sxs-lookup"><span data-stu-id="b47b3-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="b47b3-153">使用語音聽寫輸入 (<b>附註：</b>這通常是在字典中找不到的文字容易發生錯誤，並且不適合用於密碼項目)</span><span class="sxs-lookup"><span data-stu-id="b47b3-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="b47b3-154">在您的應用程式專屬的檢視中建立適用於使用鍵盤</span><span class="sxs-lookup"><span data-stu-id="b47b3-154">Create a keyboard that works in your applications exclusive view</span></span>
