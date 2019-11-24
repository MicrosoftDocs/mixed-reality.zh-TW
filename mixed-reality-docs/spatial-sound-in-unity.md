---
title: Unity 中的空間音效
description: 播放來自 Unity 場景內特定3D 點的空間音效。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間音效、HRTF、會議室大小
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641068"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="58b95-104">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="58b95-104">Spatial Sound in Unity</span></span>

<span data-ttu-id="58b95-105">此頁面會連結至資源，協助您在 Unity mixed reality 專案中使用及設計 Microsoft HRTF 空間定位器。</span><span class="sxs-lookup"><span data-stu-id="58b95-105">This page links to resources to help you use and design with the Microsoft HRTF spatializer in your Unity mixed reality projects.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="58b95-106">啟用 spatialization</span><span class="sxs-lookup"><span data-stu-id="58b95-106">Enable spatialization</span></span>

<span data-ttu-id="58b95-107">在您專案的音訊設定中啟用**MS HRTF 空間定位器**。</span><span class="sxs-lookup"><span data-stu-id="58b95-107">Enable the **MS HRTF Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="58b95-108">如需詳細資訊，請參閱[Unity 的空間定位器檔](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)。</span><span class="sxs-lookup"><span data-stu-id="58b95-108">For more details, see [Unity's spatializer documentation](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span></span> 

<span data-ttu-id="58b95-109">將**音訊來源**附加至階層中的物件，並藉由核取 [**啟用 spatialization** ] 核取方塊並將**空間 Blend**滑杆移至 [1] 來啟用 spatialization。</span><span class="sxs-lookup"><span data-stu-id="58b95-109">Attach an **Audio Source** to an object in the hierarchy, and enable spatialization by checking the **Enable spatialization** checkbox and moving the **Spatial Blend** slider to '1'.</span></span> <span data-ttu-id="58b95-110">如需詳細資訊，請參閱[Unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)。</span><span class="sxs-lookup"><span data-stu-id="58b95-110">For more details, see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span></span> 

## <a name="design-with-spatialization"></a><span data-ttu-id="58b95-111">使用 spatialization 設計</span><span class="sxs-lookup"><span data-stu-id="58b95-111">Design with spatialization</span></span>

### <a name="distance-based-attenuation"></a><span data-ttu-id="58b95-112">以距離為基礎的衰減</span><span class="sxs-lookup"><span data-stu-id="58b95-112">Distance-based attenuation</span></span>
<span data-ttu-id="58b95-113">以 Unity 的預設距離為基礎的衰減，其最小距離為1個計量，而最大距離為500計量，而對數 rolloff 為。</span><span class="sxs-lookup"><span data-stu-id="58b95-113">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="58b95-114">這可能適用于您的案例，或者您可能會發現來源的 attenuate 速度太快或太慢。</span><span class="sxs-lookup"><span data-stu-id="58b95-114">This may work for your scenario, or you may find sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="58b95-115">如需距離衰減曲線的建議設定，請參閱[混合現實中的音效設計](spatial-sound-design.md)，並參閱[unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)，以取得在 Unity 中設定這些曲線的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="58b95-115">See [sound design in mixed reality](spatial-sound-design.md) for recommended settings for distance decay curves, and see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for information on setting these curves in Unity.</span></span>

### <a name="environment"></a><span data-ttu-id="58b95-116">環境</span><span class="sxs-lookup"><span data-stu-id="58b95-116">Environment</span></span>
<span data-ttu-id="58b95-117">**MS HRTF 空間定位器**包含一個房間回音元件，其中包含[四個回音設定](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment)和預設值「小型」。</span><span class="sxs-lookup"><span data-stu-id="58b95-117">The **MS HRTF Spatializer** includes a room reverb component with [four reverb settings](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) and a default of 'small'.</span></span> <span data-ttu-id="58b95-118">您可以藉由將下列C#腳本附加至 Unity 中具有 Hrtf 音訊來源的每個物件，以程式設計方式變更每個音訊來源的房間設定：</span><span class="sxs-lookup"><span data-stu-id="58b95-118">The room setting can be changed programmatically for each audio source by attaching the following C# script to each object in Unity that has a spatialized Audio Source:</span></span>

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="58b95-119">Unity 空間音效範例</span><span class="sxs-lookup"><span data-stu-id="58b95-119">Unity spatial sound examples</span></span>
<span data-ttu-id="58b95-120">Mixed Reality 工具組（MRTK）包含在混合現實中套用音訊效果的方式範例： [MRTK 示範](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)。</span><span class="sxs-lookup"><span data-stu-id="58b95-120">The Mixed Reality Toolkit (MRTK) includes examples of ways to apply audio effects in mixed reality: [MRTK demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span></span>

