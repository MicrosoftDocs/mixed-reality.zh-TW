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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="bdcfe-104">搭配適用于 HoloLens 的 Unity 應用程式使用 Windows 命名空間</span><span class="sxs-lookup"><span data-stu-id="bdcfe-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="bdcfe-105">此頁面說明如何在適用于 HoloLens 的 Unity 專案中使用 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="bdcfe-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="bdcfe-106">有條件地包含 WinRT API 呼叫</span><span class="sxs-lookup"><span data-stu-id="bdcfe-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="bdcfe-107">WinRT Api 可用於針對通用 Windows 平臺和 Xbox One 平臺所建立的 Unity 專案;在以 WinRT Api 為目標的 Unity 腳本中撰寫的任何程式碼, 都必須有條件地包含在這些組建中。</span><span class="sxs-lookup"><span data-stu-id="bdcfe-107">WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="bdcfe-108">這可以透過 Unity 中的兩個步驟來完成:</span><span class="sxs-lookup"><span data-stu-id="bdcfe-108">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="bdcfe-109">在播放 [設定] 中, API 相容性層級必須設定為 [ **.net 4.6** ] 或 [ **.NET Standard 2.0** ]</span><span class="sxs-lookup"><span data-stu-id="bdcfe-109">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="bdcfe-110">**編輯**  **專案設定**播放的 > Api**相容性層級**至 .net 4.6 或 **.NET Standard 2.0**  >   >   > </span><span class="sxs-lookup"><span data-stu-id="bdcfe-110">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="bdcfe-111">預處理器指示詞**ENABLE_WINMD_SUPPORT**必須包裝在任何 WinRT 運用的程式碼周圍</span><span class="sxs-lookup"><span data-stu-id="bdcfe-111">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="bdcfe-112">下列程式碼片段來自[通用 Windows 平臺的 Unity 手冊頁面:腳本](http://docs.unity3d.com/Manual/windowsstore-scripts.html)中的C# WinRT API。</span><span class="sxs-lookup"><span data-stu-id="bdcfe-112">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="bdcfe-113">在此範例中, 會傳回廣告識別碼, 但僅適用于 UWP 和 Xbox One 組建:</span><span class="sxs-lookup"><span data-stu-id="bdcfe-113">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="bdcfe-114">在 Unity C#專案中編輯您的腳本</span><span class="sxs-lookup"><span data-stu-id="bdcfe-114">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="bdcfe-115">當您按兩下 Unity 編輯器中的腳本時, 預設會在編輯器專案中啟動您的腳本。</span><span class="sxs-lookup"><span data-stu-id="bdcfe-115">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="bdcfe-116">WinRT Api 會顯示為未知, 因為 Visual Studio 專案未參考 Windows 執行階段。</span><span class="sxs-lookup"><span data-stu-id="bdcfe-116">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="bdcfe-117">此外, **ENALBE_WINMD_SUPPORT**指示詞將會是未定義的, 而且除非您將專案建立到 UWP Visual Studio 解決方案, 否則會忽略任何 *#if*包裝的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdcfe-117">Further, the **ENALBE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdcfe-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdcfe-118">See also</span></span>
* [<span data-ttu-id="bdcfe-119">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="bdcfe-119">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="bdcfe-120">Windows 執行階段支援 Unity</span><span class="sxs-lookup"><span data-stu-id="bdcfe-120">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)