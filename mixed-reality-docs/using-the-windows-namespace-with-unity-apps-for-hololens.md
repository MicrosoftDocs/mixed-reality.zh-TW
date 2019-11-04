---
title: 適用于 HoloLens 的 WinRT Api 搭配 Unity
description: 說明如何在適用于 HoloLens 的 Unity 專案中使用 WinRT Api （Windows 命名空間）。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，WinRT，windows mixed reality，API，逐步解說
ms.openlocfilehash: 73764d191813f6dcae750e74ce3181af987c9e0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437240"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="fa8f0-104">適用于 HoloLens 的 WinRT Api 搭配 Unity</span><span class="sxs-lookup"><span data-stu-id="fa8f0-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="fa8f0-105">此頁面說明如何在適用于 HoloLens 的 Unity 專案中使用 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="fa8f0-106">混合現實 Api</span><span class="sxs-lookup"><span data-stu-id="fa8f0-106">Mixed Reality APIs</span></span>

<span data-ttu-id="fa8f0-107">.NET Standard 2.0 相容投影中已提供 Windows SDK 的混合現實重點子集，您可以在專案中使用，而不需要預處理器指示詞。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="fa8f0-108">這包括 Windows 中的大部分 Api，以及新的命名空間，並可能在未來擴充以包含其他 Api。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-108">This includes most APIs in the Windows.Perception and Windows.UI.Input.Spatial namespaces, and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="fa8f0-109">在編輯器中執行時，可以使用預測的 Api，這會啟用「[播放」模式](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-109">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="fa8f0-110">若要使用此投影，請對您的專案進行下列修改：</span><span class="sxs-lookup"><span data-stu-id="fa8f0-110">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="fa8f0-111">使用[適用于 Unity 的 nuget](https://github.com/GlitchEnzo/NuGetForUnity)，新增對[MixedReality DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-111">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="fa8f0-112">具有 `Microsoft.`的 `Windows` 命名空間的前置詞參考：</span><span class="sxs-lookup"><span data-stu-id="fa8f0-112">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="fa8f0-113">以 `FromNativePtr`取代原生指標轉換：</span><span class="sxs-lookup"><span data-stu-id="fa8f0-113">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="fa8f0-114">有條件地包含 WinRT API 呼叫</span><span class="sxs-lookup"><span data-stu-id="fa8f0-114">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="fa8f0-115">或者，使用預處理器指示詞，WinRT Api 可用於針對通用 Windows 平臺和 Xbox One 平臺所建立的 Unity 專案;在以 WinRT Api 為目標的 Unity 腳本中撰寫的任何程式碼，都必須有條件地包含在這些組建中。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-115">Alternatively, WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="fa8f0-116">這可以透過 Unity 中的兩個步驟來完成：</span><span class="sxs-lookup"><span data-stu-id="fa8f0-116">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="fa8f0-117">在播放 [設定] 中，API 相容性層級必須設定為 [ **.net 4.6** ] 或 [ **.NET Standard 2.0** ]</span><span class="sxs-lookup"><span data-stu-id="fa8f0-117">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="fa8f0-118">**編輯** > **專案設定** > **Player** > **設定** > **Api 相容性層級**設為 **.net 4.6**或 **.NET Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="fa8f0-118">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="fa8f0-119">預處理器指示詞**ENABLE_WINMD_SUPPORT**必須包裝在任何 WinRT 利用的程式碼周圍</span><span class="sxs-lookup"><span data-stu-id="fa8f0-119">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="fa8f0-120">下列程式碼片段來自 Unity 手冊頁面，適用于[腳本中C#的通用 WINDOWS 平臺： WinRT API](https://docs.unity3d.com/Manual/windowsstore-scripts.html)。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-120">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="fa8f0-121">在此範例中，會傳回廣告識別碼，但僅適用于 UWP 和 Xbox One 組建：</span><span class="sxs-lookup"><span data-stu-id="fa8f0-121">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="fa8f0-122">在 Unity C#專案中編輯您的腳本</span><span class="sxs-lookup"><span data-stu-id="fa8f0-122">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="fa8f0-123">當您按兩下 Unity 編輯器中的腳本時，預設會在編輯器專案中啟動您的腳本。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-123">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="fa8f0-124">WinRT Api 會顯示為未知，因為 Visual Studio 專案未參考 Windows 執行階段。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-124">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="fa8f0-125">此外， **ENABLE_WINMD_SUPPORT**指示詞將會是未定義的，而且除非您將專案建立到 UWP Visual Studio 解決方案，否則會忽略任何 *#if*包裝的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fa8f0-125">Further, the **ENABLE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa8f0-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa8f0-126">See also</span></span>
* [<span data-ttu-id="fa8f0-127">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="fa8f0-127">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="fa8f0-128">Windows 執行階段支援 Unity</span><span class="sxs-lookup"><span data-stu-id="fa8f0-128">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
