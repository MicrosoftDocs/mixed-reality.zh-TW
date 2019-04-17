---
title: 在 Unity 中的空間音效
description: 播放音效的空間，來自於特定的 3D 點，您的 Unity 場景中。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，空間的聲音，HRTF，空間大小
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591121"
---
# <a name="spatial-sound-in-unity"></a>在 Unity 中的空間音效

本主題描述如何使用 Unity 專案中的空間音效。 它涵蓋了必要的外掛程式檔案，以及 Unity 元件和屬性，可讓空間音效。

## <a name="enabling-spatial-sound-in-unity"></a>讓空間在 Unity 中的音效

空間音效，在 Unity 中，會啟用使用音訊空間外掛程式。 讓啟用空間的聲音非常簡單，只要移至，外掛程式檔案會直接將 Unity 配套**編輯 > 專案設定 > 音訊**以及變更**空間外掛程式**來偵測器中**MS HRTF 空間**。 由於 Microsoft 空間只有目前支援 48000 Hz，您也應該將您系統的取樣率以防止在少數情況下，系統輸出裝置沒有已設定為 48000 HRTF 失敗 48000:

![AudioManager 的偵測器](images/audio-250px.png)<br>
*AudioManager 的偵測器*

您的 Unity 專案現在已設定為使用空間音效。

>[!NOTE]
>如果您不使用 Windows 10 電腦進行開發，您無法取得空間音效在編輯器中，也不在裝置上 （即使您使用 Windows 10 SDK）。

## <a name="using-spatial-sound-in-unity"></a>在 Unity 中使用空間的音效

空間音效用於您的 Unity 專案中，藉由調整音訊來源元件上的三個設定。 下列步驟將設定音訊來源元件的空間音效。
* 在 [**階層**] 面板中，選取具有附加的遊戲物件**音訊來源**。
* 在  **Inspector**  面板的 **音訊來源**元件
    * 請檢查**Spatialize**選項。
    * 設定**空間 Blend**要**3D** （數字值 1）。
    * 為了獲得最佳結果，依序展開**3D 音效設定**並設定**磁碟區捲繞**來**自訂捲繞**。

![在 Unity 中顯示音訊來源的偵測器面板](images/audiosource.png)<br>
*在 Unity 中顯示音訊來源的偵測器面板*

您的聲音現在實際上存在您的專案環境中 ！

強烈建議您先熟悉[空間音效設計指導方針](spatial-sound-design.md)。 這些指導方針可協助您的音訊緊密整合您的專案，並進一步將您的使用者可享有到您已建立的體驗。

## <a name="setting-spatial-sound-settings"></a>空間音效設定

Microsoft 空間音效外掛程式提供額外的參數，可以設定，在每個音訊來源為基礎，以允許音訊模擬的其他控制。 這個參數是房間的模擬的大小。

### <a name="room-size"></a>空間大小

模擬依據空間聲音的空間大小。 聊天室的近似大小是;(至小型會議室 office) 的小型、 中型 （大型會議空間） 和大型 (auditorium)。 您也可以指定無模擬戶外的環境的空間大小。 預設的空間大小很小。

### <a name="example"></a>範例

為 Unity MixedRealityToolkit 提供靜態類別，可讓您設定簡單空間音效設定。 這個類別可在[MixedRealityToolkit\SpatialSound 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)，而且可以從專案中的任何指令碼呼叫。 建議每個音訊來源元件上設定這些參數，在您的專案。 下列範例會顯示附加的音訊來源選取中的空間大小。

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>直接存取從 Unity 的 參數

如果您不想要用於 MixedRealityToolkit 優異的音訊工具，以下是您想要如何變更 HRTF 參數。 您可以複製/貼上到指令碼中呼叫*SetHRTF.cs* ，您會想要附加至每個 HRTF AudioSource。 它可讓您將重要的參數變更為 HRTF。

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>混合的實境工具組中的空間音效
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

混合實境 Toolkit 中的下列範例會示範如何使用音效，讓您的經驗更沈浸式的一般音訊效果範例。
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>另請參閱
* [空間的音效](spatial-sound.md)
* [空間完善的設計](spatial-sound-design.md)
