---
title: Unity 中的空間音效
description: 播放來自 Unity 場景內特定3D 點的空間音效。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間音效、HRTF、會議室大小
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549094"
---
# <a name="spatial-sound-in-unity"></a>Unity 中的空間音效

本主題說明如何在您的 Unity 專案中使用空間音效。 它涵蓋了必要的外掛程式檔案, 以及可啟用空間音效的 Unity 元件和屬性。

## <a name="enabling-spatial-sound-in-unity"></a>啟用 Unity 中的空間音效

Unity 中的空間音效是使用音訊空間定位器外掛程式來啟用。 外掛程式檔案會直接結合到 Unity 中, 因此啟用空間音效就如同**編輯 > 專案設定 > 音訊**, 並將偵測器中的**空間定位器外掛程式**變更為**MS HRTF 空間定位器**一樣容易。 由於 Microsoft 空間定位器目前僅支援 48000Hz, 因此您也應該將系統取樣率設定為 48000, 以避免在系統輸出裝置尚未設定為48000的罕見情況下 HRTF 失敗:

![AudioManager 的偵測器](images/audio-250px.png)<br>
*AudioManager 的偵測器*

您的 Unity 專案現在已設定為使用空間音效。

>[!NOTE]
>如果您不是使用 Windows 10 電腦進行開發, 就不會在編輯器或裝置上取得空間音效 (即使您使用 Windows 10 SDK)。

## <a name="using-spatial-sound-in-unity"></a>在 Unity 中使用空間音效

在您的 Unity 專案中, 您可以調整音訊來源元件上的三項設定, 以使用空間音效。 下列步驟將設定您的音訊來源元件的空間音效。
* 在 [ 階層] 面板中, 選取具有已連接**音訊來源**的遊戲物件。
* 在 [偵測**器**] 面板的 [**音訊來源**] 元件下
    * 檢查**Spatialize**選項。
    * 將**空間 Blend**設定為**3d** (數值 1)。
    * 為獲得最佳結果, 請展開 [ **3D 音效設定**], 並將 [**磁片區 Rolloff** ] 設定為**自訂 Rolloff**

![Unity 中的偵測器面板, 顯示音訊來源](images/audiosource.png)<br>
*Unity 中的偵測器面板, 顯示音訊來源*

您的音效現在實際存在於您專案的環境中!

強烈建議您熟悉[空間音效設計方針](spatial-sound-design.md)。 這些指導方針可協助將您的音訊順暢地整合到您的專案, 並進一步 immerse 您的使用者, 使其成為您所建立的經驗。

## <a name="setting-spatial-sound-settings"></a>設定空間音效設定

Microsoft 空間音效外掛程式會提供額外的參數, 可依每個音訊來源設定, 以允許其他音訊模擬的控制。 此參數是模擬空間的大小。

### <a name="room-size"></a>房間大小

空間音效模擬的房間大小。 房間的近似大小為;小型 (辦公室到小型會議室)、中型 (大型會議室) 和大型 (auditorium)。 您也可以指定 [無] 的房間大小來模擬室外環境。 預設的會議室大小很小。

### <a name="example"></a>範例

適用于 Unity 的 MixedRealityToolkit 提供靜態類別, 讓您可以輕鬆地設定空間音效設定。 這個類別可以在[MixedRealityToolkit\SpatialSound 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)中找到, 而且可以從專案中的任何腳本呼叫。 建議您在專案中的每個音訊來源元件上設定這些參數。 下列範例會示範如何選取連接音訊來源的中房間大小。

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>直接從 Unity 存取參數

如果您不想使用 MixedRealityToolkit 中的絕佳音訊工具, 以下是變更 HRTF 參數的方式。 您可以將此程式碼複製/貼上至名為*SetHRTF.cs*的腳本, 您會想要將它附加到每個 HRTF spatialize。 它可讓您將重要的參數變更為 HRTF。

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>混合現實工具組中的空間音效
- [HoloToolkit-Examples/SpatialSound/場景/UAudioManagerTest unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

下列混合現實工具組中的範例是一般的音訊效果範例, 示範如何使用音效讓您的體驗更具沉浸。
- [HoloToolkit-Examples/SpatialSound/場景/AudioLoFiTest unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/場景/AudioOcclusionTest unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>另請參閱
* [空間音效](spatial-sound.md)
* [空間音效設計](spatial-sound-design.md)
