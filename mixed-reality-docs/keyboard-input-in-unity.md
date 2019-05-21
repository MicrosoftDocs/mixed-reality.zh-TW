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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597039"
---
# <a name="keyboard-input-in-unity"></a>在 Unity 中的鍵盤輸入

**命名空間：**  *UnityEngine*<br>
 **類型**：*[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

雖然 HoloLens 支援許多形式的輸入包括藍芽鍵盤，大部分的應用程式不能假設所有使用者都有可用的實體鍵盤。 如果您的應用程式需要文字輸入，則應該提供某種形式的螢幕小鍵盤。

Unity 提供 *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 時不沒有可用的任何實體鍵盤接受鍵盤輸入的類別。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>在 Unity 中的 HoloLens 系統鍵盤行為

HoloLens，在*TouchScreenKeyboard*運用系統的螢幕小鍵盤。 體積型檢視上方重疊，因此必須要建立次要 2D XAML 檢視，以顯示鍵盤，則傳回回到體積型檢視中，提交輸入之後的 Unity 無法系統的螢幕小鍵盤。 使用者流程如下所示：
1. 使用者執行動作導致應用程式程式碼呼叫*TouchScreenKeyboard*
    * 應用程式會負責暫停的應用程式狀態，然後再呼叫*TouchScreenKeyboard*
    * 應用程式可能會終止之前曾經切換回到體積型檢視
2. Unity 會切換成 2D 的 XAML 檢視也就是世界中的 自動放置
3. 使用者輸入文字時，使用系統鍵盤和送出或取消
4. Unity 會切換回體積型檢視
    * 應用程式會負責繼續執行應用程式時*TouchScreenKeyboard*完成
5. 已送出的文字可用於*TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>可用鍵盤的檢視

有六個不同的鍵盤檢視：
* 單行文字方塊
* 標題的單行文字方塊
* 多行文字方塊
* 標題的多行文字方塊
* 單行密碼方塊
* 標題的單行密碼方塊

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>如何啟用系統鍵盤在 Unity 中

只有適用於 Unity 應用程式會使用 [UWP 建置類型] 設定為"XAML"匯出 HoloLens 系統鍵盤。 沒有您選擇 [UWP 建置類型] 為"XAML"透過 「 D3D 」 時所做的權衡取捨。 如果您不熟悉這些權衡取捨，您可能想要探索[解決方案的替代輸入](#alternative-keyboard-options)系統鍵盤。
1. 開啟**檔案**功能表，然後選取**組建設定...**
2. 確保**平台**設為**Windows 市集**，則**SDK**設定為**通用 10**，並設定**UWP 建置型別**要**XAML**。
3. 在 **組建設定** 對話方塊中，按一下 **播放程式設定...** 按鈕
4. 選取 [**設定適用於 Windows 市集**] 索引標籤
5. 依序展開**其他設定**群組
6. 在 **轉譯**區段中，按一下**虛擬實境支援**核取方塊以加入新**虛擬實境裝置**清單
7. 請確定**Windows 全像攝影版**會出現在清單中的虛擬實境 Sdk

>[!NOTE]
>如果您不與 HoloLens 裝置，將建置標示為受支援的虛擬實境中，專案會匯出為 2D XAML 應用程式。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>在您的 Unity 應用程式中使用系統鍵盤

### <a name="declare-the-keyboard"></a>宣告鍵盤

在類別中，宣告一個變數來存放*TouchScreenKeyboard* ，並傳回變數，以容納字串鍵盤。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>叫用鍵盤

要求的鍵盤輸入發生事件時，呼叫其中一個函式所需的輸入類型而定。 請注意，標題會 textPlaceholder 參數中指定。

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

### <a name="retrieve-typed-contents"></a>擷取具類型的內容

在更新迴圈中，檢查是否鍵盤接收到新的輸入並將它儲存在其他地方使用。

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

## <a name="alternative-keyboard-options"></a>替代鍵盤選項

我們了解切換移出的 2D 檢視的體積型檢視不是最理想的方式從使用者取得文字輸入。

目前的替代方案，運用系統鍵盤，透過 Unity 包括：
* 使用語音聽寫輸入 (<b>附註：</b>這通常是在字典中找不到的文字容易發生錯誤，並且不適合用於密碼項目)
* 在您的應用程式專屬的檢視中建立適用於使用鍵盤
