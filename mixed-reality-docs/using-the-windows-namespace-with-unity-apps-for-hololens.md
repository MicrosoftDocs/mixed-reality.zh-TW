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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="27cf6-104">HoloLens 與 Unity 應用程式使用的 Windows 命名空間</span><span class="sxs-lookup"><span data-stu-id="27cf6-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="27cf6-105">此頁面說明如何使用 Unity 專案中的 HoloLens WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="27cf6-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="27cf6-106">有條件地包含 WinRT API 呼叫</span><span class="sxs-lookup"><span data-stu-id="27cf6-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="27cf6-107">WinRT Api 只用於在 Windows 8、 Windows 8.1 通用 Windows 平台為目標的 Unity 專案組建中任何您撰寫程式碼中 Unity 指令碼為目標的 WinRT Api 必須有條件地包含只有這些組建。</span><span class="sxs-lookup"><span data-stu-id="27cf6-107">WinRT APIs will only be used in Unity project builds that target Windows 8, Windows 8.1, or the Universal Windows Platform; any code that you write in Unity scripts that targets WinRT APIs must be conditionally included for only those builds.</span></span> <span data-ttu-id="27cf6-108">這是使用 NETFX_CORE 或 WINDOWS_UWP 前置處理器定義。</span><span class="sxs-lookup"><span data-stu-id="27cf6-108">This is done using the NETFX_CORE or WINDOWS_UWP preprocessor definitions.</span></span> <span data-ttu-id="27cf6-109">此規則適用於使用陳述式，以及其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="27cf6-109">This rule applies to using statements, as well as other code.</span></span>

<span data-ttu-id="27cf6-110">下列程式碼片段會從 Unity 手冊頁面，針對[通用 Windows 平台：中的 WinRT APIC#指令碼](http://docs.unity3d.com/Manual/windowsstore-scripts.html)。</span><span class="sxs-lookup"><span data-stu-id="27cf6-110">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="27cf6-111">在此範例中，廣告識別碼會傳回，但只能在 Windows 8.0 或更新版本的目標組建：</span><span class="sxs-lookup"><span data-stu-id="27cf6-111">In this example, an advertising ID is returned, but only on Windows 8.0 or higher target builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="27cf6-112">編輯您在 Unity 中的指令碼C#專案</span><span class="sxs-lookup"><span data-stu-id="27cf6-112">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="27cf6-113">當您按兩下 Unity editor 中的指令碼時，它會依預設啟動您的指令碼編輯器專案中。</span><span class="sxs-lookup"><span data-stu-id="27cf6-113">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="27cf6-114">WinRT Api 會出現為未知原因有二：NETFX_CORE 未定義在此環境中，且專案不會參考 Windows 執行階段。</span><span class="sxs-lookup"><span data-stu-id="27cf6-114">The WinRT APIs will appear to be unknown for two reasons: NETFX_CORE is not defined in this environment, and the project does not reference the Windows Runtime.</span></span> <span data-ttu-id="27cf6-115">如果您使用[建議使用匯出和建置設定](exporting-and-building-a-unity-visual-studio-solution.md)，並改為編輯該專案中的指令碼，它會定義 NETFX_CORE 並也包含在位置的 參考至 Windows 執行階段; 此設定，WinRT Api 會適用於 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="27cf6-115">If you use the [recommended export and built settings](exporting-and-building-a-unity-visual-studio-solution.md), and edit the scripts in that project instead, it will define NETFX_CORE and also include a reference to the Windows Runtime; with this configuration in place, WinRT APIs will be available for IntelliSense.</span></span>

<span data-ttu-id="27cf6-116">請注意，您的 UnityC#專案也可用來透過您的指令碼使用遠端偵錯在 Visual Studio 中的 F5 偵錯。</span><span class="sxs-lookup"><span data-stu-id="27cf6-116">Note that your Unity C# project can also be used to debug through your scripts using F5 remote debugging in Visual Studio.</span></span> <span data-ttu-id="27cf6-117">如果您看不見工作第一次您開啟您的 Unity 的 IntelliSenseC#專案、 關閉專案，並重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="27cf6-117">If you do not see IntelliSense working the first time that you open your Unity C# project, close the project and re-open it.</span></span> <span data-ttu-id="27cf6-118">IntelliSense 應該開始使用。</span><span class="sxs-lookup"><span data-stu-id="27cf6-118">IntelliSense should start working.</span></span>

## <a name="see-also"></a><span data-ttu-id="27cf6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27cf6-119">See also</span></span>
* [<span data-ttu-id="27cf6-120">匯出和建置 Unity Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="27cf6-120">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
