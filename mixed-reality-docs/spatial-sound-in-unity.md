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
# <a name="spatial-sound-in-unity"></a>Unity 中的空間音效

此頁面會連結至資源，協助您在 Unity mixed reality 專案中使用及設計 Microsoft HRTF 空間定位器。

## <a name="enable-spatialization"></a>啟用 spatialization

在您專案的音訊設定中啟用**MS HRTF 空間定位器**。 如需詳細資訊，請參閱[Unity 的空間定位器檔](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)。 

將**音訊來源**附加至階層中的物件，並藉由核取 [**啟用 spatialization** ] 核取方塊並將**空間 Blend**滑杆移至 [1] 來啟用 spatialization。 如需詳細資訊，請參閱[Unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)。 

## <a name="design-with-spatialization"></a>使用 spatialization 設計

### <a name="distance-based-attenuation"></a>以距離為基礎的衰減
以 Unity 的預設距離為基礎的衰減，其最小距離為1個計量，而最大距離為500計量，而對數 rolloff 為。 這可能適用于您的案例，或者您可能會發現來源的 attenuate 速度太快或太慢。 如需距離衰減曲線的建議設定，請參閱[混合現實中的音效設計](spatial-sound-design.md)，並參閱[unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)，以取得在 Unity 中設定這些曲線的相關資訊。

### <a name="environment"></a>環境
**MS HRTF 空間定位器**包含一個房間回音元件，其中包含[四個回音設定](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment)和預設值「小型」。 您可以藉由將下列C#腳本附加至 Unity 中具有 Hrtf 音訊來源的每個物件，以程式設計方式變更每個音訊來源的房間設定：

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

## <a name="unity-spatial-sound-examples"></a>Unity 空間音效範例
Mixed Reality 工具組（MRTK）包含在混合現實中套用音訊效果的方式範例： [MRTK 示範](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)。

