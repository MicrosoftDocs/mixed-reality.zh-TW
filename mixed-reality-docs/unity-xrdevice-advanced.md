---
title: 混合的實境原生物件 Unity 中
description: 在 Unity 中取得基礎全像攝影版的原生物件的存取權。
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: unity，混合實境、 原生、 xrdevice、 spatialcoordinatesystem、 holographicframe、 holographiccamera、 ispatialcoordinatesystem、 iholographicframe、 iholographiccamera、 getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942094"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="19680-104">混合的實境原生物件 Unity 中</span><span class="sxs-lookup"><span data-stu-id="19680-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="19680-105">[取得 HolographicSpace](getting-a-holographicspace.md)是應用程式會執行，再開始接收相機資料和呈現每個混合實境的框架。</span><span class="sxs-lookup"><span data-stu-id="19680-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="19680-106">在 Unity 中，引擎會為您處理全像攝影版的物件處理的這些步驟，並更新就內部而言，其轉譯迴圈的一部分。</span><span class="sxs-lookup"><span data-stu-id="19680-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="19680-107">不過，在進階案例中您可能需要取得存取權的基礎原生的物件，例如<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>和目前<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>。</span><span class="sxs-lookup"><span data-stu-id="19680-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="19680-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a>是提供這些原生物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="19680-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="19680-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="19680-109">XRDevice</span></span> 

<span data-ttu-id="19680-110">\**命名空間：\*\*\*UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="19680-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="19680-111">\**類型：\*\*\*XRDevice*</span><span class="sxs-lookup"><span data-stu-id="19680-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="19680-112">*XRDevice*型別可讓您使用的基礎原生物件的存取權<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法。</span><span class="sxs-lookup"><span data-stu-id="19680-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="19680-113">GetNativePtr 所傳回，則不同的平台而有所不同。</span><span class="sxs-lookup"><span data-stu-id="19680-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="19680-114">通用 Windows 平台上，當 Windows Mixed Reality XR SDK 為目標，XRDevice.GetNativePtr 會傳回與下列結構的指標 (IntPtr):</span><span class="sxs-lookup"><span data-stu-id="19680-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
<span data-ttu-id="19680-115">您可以將它轉換至 HolographicFrameNativeData 使用 Marshal.PtrToStructure 方法：</span><span class="sxs-lookup"><span data-stu-id="19680-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="19680-116">\***IHolographicCameraPtr**是 IntPtr 封送處理為 UnmanagedType.ByValArray 等於 MaxNumberOfCameras 長度的陣列\*</span><span class="sxs-lookup"><span data-stu-id="19680-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="19680-117">使用 HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="19680-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="19680-118">變更原生物件透過 HolographicFrameNativeData 接收的狀態可能會造成無法預期的行為和轉譯成品，特別是當 Unity 也會理解該相同的狀態。</span><span class="sxs-lookup"><span data-stu-id="19680-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="19680-119">比方說，您不應該呼叫 HolographicFrame.UpdateCurrentPrediction，或是以該範圍內呈現的 Unity 姿勢預測將會是與姿勢 Windows 所預期，這會減少不同步[全像穩定性](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="19680-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="19680-120">轉譯或偵錯用途，在您的原生外掛程式需要存取原生介面時，您可以使用來自 HolographicFrameNativeData 資料或C#程式碼。</span><span class="sxs-lookup"><span data-stu-id="19680-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="19680-121">以下是您如何使用以取得目前的框架預測 photon 次 HolographicFrameNativeData 範例。</span><span class="sxs-lookup"><span data-stu-id="19680-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a><span data-ttu-id="19680-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19680-122">See Also</span></span>
* <span data-ttu-id="19680-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="19680-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="19680-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="19680-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="19680-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="19680-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="19680-126">DirectX 中的呈現</span><span class="sxs-lookup"><span data-stu-id="19680-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
