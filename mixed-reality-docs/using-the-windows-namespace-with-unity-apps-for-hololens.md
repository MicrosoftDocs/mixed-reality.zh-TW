---
title: HoloLens 與 Unity 應用程式使用的 Windows 命名空間
description: 說明如何使用 Unity 專案中的 HoloLens WinRT Api。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity WinRT，windows 混合的實境，API，逐步解說
ms.openlocfilehash: ed65b5995d74c54057a49b878c1206d0f06394ca
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591760"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>HoloLens 與 Unity 應用程式使用的 Windows 命名空間

此頁面說明如何使用 Unity 專案中的 HoloLens WinRT Api。

## <a name="conditionally-include-winrt-api-calls"></a>有條件地包含 WinRT API 呼叫

WinRT Api 只用於在 Windows 8、 Windows 8.1 通用 Windows 平台為目標的 Unity 專案組建中任何您撰寫程式碼中 Unity 指令碼為目標的 WinRT Api 必須有條件地包含只有這些組建。 這是使用 NETFX_CORE 或 WINDOWS_UWP 前置處理器定義。 此規則適用於使用陳述式，以及其他程式碼。

下列程式碼片段會從 Unity 手冊頁面，針對[通用 Windows 平台：中的 WinRT APIC#指令碼](http://docs.unity3d.com/Manual/windowsstore-scripts.html)。 在此範例中，廣告識別碼會傳回，但只能在 Windows 8.0 或更新版本的目標組建：

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if NETFX_CORE
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>編輯您在 Unity 中的指令碼C#專案

當您按兩下 Unity editor 中的指令碼時，它會依預設啟動您的指令碼編輯器專案中。 WinRT Api 會出現為未知原因有二：NETFX_CORE 未定義在此環境中，且專案不會參考 Windows 執行階段。 如果您使用[建議使用匯出和建置設定](exporting-and-building-a-unity-visual-studio-solution.md)，並改為編輯該專案中的指令碼，它會定義 NETFX_CORE 並也包含在位置的 參考至 Windows 執行階段; 此設定，WinRT Api 會適用於 IntelliSense。

請注意，您的 UnityC#專案也可用來透過您的指令碼使用遠端偵錯在 Visual Studio 中的 F5 偵錯。 如果您看不見工作第一次您開啟您的 Unity 的 IntelliSenseC#專案、 關閉專案，並重新開啟它。 IntelliSense 應該開始使用。

## <a name="see-also"></a>另請參閱
* [匯出和建置 Unity Visual Studio 方案](exporting-and-building-a-unity-visual-studio-solution.md)
