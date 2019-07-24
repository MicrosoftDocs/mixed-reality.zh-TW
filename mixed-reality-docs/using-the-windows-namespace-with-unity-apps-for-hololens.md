---
title: 搭配適用于 HoloLens 的 Unity 應用程式使用 Windows 命名空間
description: 說明如何在適用于 HoloLens 的 Unity 專案中使用 WinRT Api。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, 逐步解說
ms.openlocfilehash: fd25548de8eeb3c8157a3f9de283dc5004ed1180
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548729"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>搭配適用于 HoloLens 的 Unity 應用程式使用 Windows 命名空間

此頁面說明如何在適用于 HoloLens 的 Unity 專案中使用 WinRT Api。

## <a name="conditionally-include-winrt-api-calls"></a>有條件地包含 WinRT API 呼叫

WinRT Api 可用於針對通用 Windows 平臺和 Xbox One 平臺所建立的 Unity 專案;在以 WinRT Api 為目標的 Unity 腳本中撰寫的任何程式碼, 都必須有條件地包含在這些組建中。 

這可以透過 Unity 中的兩個步驟來完成:
1) 在播放 [設定] 中, API 相容性層級必須設定為 [ **.net 4.6** ] 或 [ **.NET Standard 2.0** ]
    - **編輯**  **專案設定**播放的 > Api**相容性層級**至 .net 4.6 或 **.NET Standard 2.0**  >   >   > 
2) 預處理器指示詞**ENABLE_WINMD_SUPPORT**必須包裝在任何 WinRT 運用的程式碼周圍

下列程式碼片段來自[通用 Windows 平臺的 Unity 手冊頁面:腳本](http://docs.unity3d.com/Manual/windowsstore-scripts.html)中的C# WinRT API。 在此範例中, 會傳回廣告識別碼, 但僅適用于 UWP 和 Xbox One 組建:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>在 Unity C#專案中編輯您的腳本

當您按兩下 Unity 編輯器中的腳本時, 預設會在編輯器專案中啟動您的腳本。 WinRT Api 會顯示為未知, 因為 Visual Studio 專案未參考 Windows 執行階段。 此外, **ENALBE_WINMD_SUPPORT**指示詞將會是未定義的, 而且除非您將專案建立到 UWP Visual Studio 解決方案, 否則會忽略任何 *#if*包裝的程式碼。

## <a name="see-also"></a>另請參閱
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 執行階段支援 Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)