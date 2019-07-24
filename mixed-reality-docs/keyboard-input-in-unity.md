---
title: Unity 中的鍵盤輸入
description: Unity 提供 TouchScreenKeyboard 類別, 可在沒有可用的實體鍵盤時接受鍵盤輸入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 鍵盤、輸入、unity、touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515734"
---
# <a name="keyboard-input-in-unity"></a>Unity 中的鍵盤輸入

**命名空間：**  *UnityEngine*<br>
 **類型**： *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

雖然 HoloLens 支援許多形式的輸入, 包括藍牙鍵盤, 但大部分的應用程式都無法假設所有使用者都有可用的實體鍵盤。 如果您的應用程式需要文字輸入, 則應該提供某種形式的螢幕小鍵盤。

Unity 提供 *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 時不沒有可用的任何實體鍵盤接受鍵盤輸入的類別。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>在 Unity 中的 HoloLens 系統鍵盤行為

在 HoloLens 上, *TouchScreenKeyboard*會利用系統的螢幕小鍵盤。 系統的 [螢幕小鍵盤] 無法在體積型視圖上重迭, 因此 Unity 必須建立次要 2D XAML 視圖來顯示鍵盤, 然後在送出輸入之後回到體積型 view。 使用者流程如下所示:
1. 使用者執行動作, 導致應用程式代碼呼叫*TouchScreenKeyboard*
    * 在呼叫*TouchScreenKeyboard*之前, 應用程式會負責暫停應用程式狀態
    * 應用程式可能會在切換回體積型視圖之前終止
2. Unity 切換為自動放在世界中的 2D XAML 視圖
3. 使用者使用系統鍵盤輸入文字並提交或取消
4. Unity 切換回體積型視圖
    * 當*TouchScreenKeyboard*完成時, 應用程式會負責繼續應用程式狀態
5. 提交的文字可在*TouchScreenKeyboard*中取得

### <a name="available-keyboard-views"></a>可用的鍵盤流覽

有六種不同的鍵盤視圖可供使用:
* 單行文字方塊
* 含標題的單行文字方塊
* 多行文字方塊
* 具有標題的多行文字方塊
* 單行密碼方塊
* 具有標題的單行密碼方塊

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>如何在 Unity 中啟用系統鍵盤

HoloLens 系統鍵盤僅適用于以「UWP 組建類型」設定為「XAML」的 Unity 應用程式。 當您選擇「XAML」做為「UWP 組建類型」而不是「D3D」時, 會產生取捨。 如果您不熟悉這些取捨, 您可能會想要探索系統鍵盤的[替代輸入解決方案](#alternative-keyboard-options)。
1. 開啟 [ 檔案] 功能表, 然後選取 [**組建設定**]。
2. 確定**平臺**已設定為 [ **Windows Store**], **SDK**設定為 [**通用 10**], 並將**UWP 組建類型**設定為 [ **XAML**]。
3. 在 [**組建設定**] 對話方塊中, 按一下 [ **Player 設定 ...** ] 按鈕
4. 選取 [ **Windows Store 的設定**] 索引標籤
5. 展開 [**其他設定**] 群組
6. 在轉譯區段中, 勾選 [**支援虛擬實境**] 核取方塊, 以新增**虛擬實境裝置**清單
7. 確保**Windows**全像顯示在虛擬實境 sdk 清單中

>[!NOTE]
>如果您未將此組建標示為 HoloLens 裝置所支援的虛擬實境, 專案將會匯出為 2D XAML 應用程式。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>在 Unity 應用程式中使用系統鍵盤

### <a name="declare-the-keyboard"></a>宣告鍵盤

在類別中, 宣告用來儲存*TouchScreenKeyboard*的變數, 以及用來保存鍵盤所傳回之字串的變數。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>叫用鍵盤

當要求鍵盤輸入時發生事件時, 請根據所需的輸入類型呼叫其中一個函式。 請注意, 標題是在 textPlaceholder 參數中指定。

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

### <a name="retrieve-typed-contents"></a>取出具類型的內容

在更新迴圈中, 檢查鍵盤是否收到新的輸入, 並加以儲存以供其他地方使用。

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

我們瞭解, 將體積型視圖切換到2D 視圖並不是取得使用者文字輸入的理想方式。

透過 Unity 運用系統鍵盤的目前替代方案包括:
* 使用語音聽寫進行輸入 (<b>注意:</b>這通常容易發生在字典中找不到的單字, 且不適合用于密碼輸入)
* 建立可在應用程式獨佔視圖中運作的鍵盤
