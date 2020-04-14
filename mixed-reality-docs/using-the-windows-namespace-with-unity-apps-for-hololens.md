---
title: 適用于 HoloLens 的 WinRT Api 搭配 Unity
description: 說明如何在適用于 HoloLens 的 Unity 專案中使用 WinRT Api （Windows 命名空間）。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，WinRT，windows mixed reality，API，逐步解說
ms.openlocfilehash: 80f950d7571a936e93eb08490ad83dbb34a50b3a
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277986"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>適用于 HoloLens 的 WinRT Api 搭配 Unity

此頁面說明如何在適用于 HoloLens 的 Unity 專案中使用 WinRT Api。

## <a name="mixed-reality-apis"></a>混合現實 Api

.NET Standard 2.0 相容投影中已提供 Windows SDK 的混合現實重點子集，您可以在專案中使用，而不需要預處理器指示詞。 這包括 Windows 中的大部分 Api，以及新的命名空間，並可能在未來擴充以包含其他 Api。 在編輯器中執行時，可以使用預測的 Api，這會啟用「[播放」模式](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)。 若要使用此投影，請對您的專案進行下列修改：

1) 使用[適用于 Unity 的 nuget](https://github.com/GlitchEnzo/NuGetForUnity)，新增對[MixedReality DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet 套件的參考。
2) 具有 `Microsoft.`的 `Windows` 命名空間的前置詞參考：
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) 以 `FromNativePtr`取代原生指標轉換：
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>有條件地包含 WinRT API 呼叫

或者，使用預處理器指示詞，WinRT Api 可用於針對通用 Windows 平臺和 Xbox One 平臺所建立的 Unity 專案;在以 WinRT Api 為目標的 Unity 腳本中撰寫的任何程式碼，都必須有條件地包含在這些組建中。 

這可以透過 Unity 中的兩個步驟來完成：
1) 在播放 [設定] 中，API 相容性層級必須設定為 [ **.net 4.6** ] 或 [ **.NET Standard 2.0** ]
    - **編輯** > **專案設定** > **Player** > **設定** > **Api 相容性層級**設為 **.net 4.6**或 **.NET Standard 2.0**
2) 預處理器指示詞**ENABLE_WINMD_SUPPORT**必須包裝在任何 WinRT 利用的程式碼周圍

下列程式碼片段來自 Unity 手冊頁面，適用于[腳本中C#的通用 WINDOWS 平臺： WinRT API](https://docs.unity3d.com/Manual/windowsstore-scripts.html)。 在此範例中，會傳回廣告識別碼，但僅適用于 UWP 和 Xbox One 組建：

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

當您按兩下 Unity 編輯器中的腳本時，預設會在編輯器專案中啟動您的腳本。 WinRT Api 會顯示為未知，因為 Visual Studio 專案未參考 Windows 執行階段。 此外， **ENABLE_WINMD_SUPPORT**指示詞將會是未定義的，而且除非您將專案建立到 UWP Visual Studio 解決方案，否則會忽略任何 *#if*包裝的程式碼。

## <a name="see-also"></a>另請參閱
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 執行階段支援 Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
