---
title: 空間音訊教學課程-5。 使用回音來增加空間音訊的距離
description: 新增 [回音] 效果，以增強距離空間音訊的距離變化意義。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教學課程，hololens2，空間音訊
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182735"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a>使用回音來增加空間音訊的距離

## <a name="objectives"></a>目標
在上一章中，我們將 spatialization 新增到音效，讓他們有意義的方向。 在這第5章中，我們會新增一個回音效果，讓聽起來能夠說是距離。 我們的目標是：
* 藉由新增回音來改善音效來源的認知距離
* 使用收聽者與全息影像的距離，控制聲音的觀察距離

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>新增混音器群組和回音效果
在[第2章](unity-spatial-audio-ch2.md)中，我們新增了混音器。 混音器包含一個預設名為**Master**的**群組**。 因為我們只想要將回音效果套用到一些音效，所以讓我們為這些音效新增第二個**群組**。 若要新增**群組**，請以滑鼠右鍵按一下 [**音訊混音**器] 中的**主要**群組，然後選擇 [**新增子群組**]：

![新增子群組](images/spatial-audio/add-child-group.png)

在此範例中，我們將新的群組命名為「會議室效果」。

每個**群組**都有自己的一組效果。 按一下新群組上的 [新增 **...** ]，然後選擇 [SFX] [**回音**]，將 [回音] 效果新增至新群組：

![新增 SFX 回音](images/spatial-audio/add-sfx-reverb.png)

在音訊術語中，原始的 unreverberated 音訊稱為「_乾路徑_」，而使用「回音」篩選準則篩選後的音訊稱為「未幹」的_路徑_。 這兩個路徑都會傳送至音訊輸出，而且其在此混合中的相對強度稱為「_濕/幹混合_」。 濕/幹混合強烈影響距離的意義。

SFX 的「**回音**」包含控制項，可調整效果中的濕/幹混合。 由於**Microsoft 空間定位器**外掛程式會處理試路徑，因此我們只會針對濕路徑使用**SFX 回音**。 在您的**SFX 回音**的 [偵測**器**] 窗格上：
* 將 [晾乾層級] 屬性設定為最低設定（-10000 mB）
* 將 [房間] 屬性設為最高設定（0 mB）

這些變更之後， **SFX 回音**的偵測**器**窗格看起來會像這樣：

![SFX 回音屬性](images/spatial-audio/sfx-reverb-properties.png)

其他設定則控制模擬室的風格。 特別是，**衰減時間**與認知的房間大小有關。 

## <a name="enable-reverb-on-the-video-playback"></a>在播放影片時啟用回音
有兩個步驟可以在音訊來源上啟用「回音」：
* 將**音訊來源**路由至適當的**群組**
* 設定**Microsoft 空間定位器**外掛程式，將音訊傳遞至**群組**進行處理

在下列步驟中，我們將調整腳本以控制音訊路由，並附加**Microsoft 空間定位器**外掛程式所提供的控制項腳本，將資料摘要至回音。

在**四**個 [偵測**器**] 窗格中，按一下 [**新增元件**]，然後新增 [**會議室效果] 傳送層級**腳本：

![新增傳送層級腳本](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> 除非您啟用**Microsoft 空間定位器**外掛程式的**會議室效果傳送層級**功能，否則不會將任何音訊傳送回 Unity 音訊引擎以進行效果處理。

[**會議室效果傳送層級**] 元件包含一個圖形控制項，可設定傳送給 Unity 音訊引擎以進行回音處理的音訊層級。 按一下並向下拖曳曲線，將層級設定為 [關於-30dB]：

![調整回音曲線](images/spatial-audio/adjust-reverb-curve.png)

接下來，將**SpatializeOnOff**腳本中的4個批註行取消批註。 腳本現在會如下所示：
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

取消批註這些行會將兩個屬性新增至腳本的 [偵測**器**] 窗格。 若要設定這些，請在**四**個**Spatialize**的 [Inspector] 元件上的 [偵測**器**] 窗格上：
* 將 [**房間效果群組**] 屬性設定為新的房間效果混音器群組
* 將 [**主要群組**] 屬性設定為 [主要混音器] 群組

這些變更之後， **Spatialize On**屬性會如下所示：

![Spatialize 已關閉擴充](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a>後續步驟

在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。 現在，當您觸及應用程式中的按鈕來啟動 spatialization 時，腳本會將影片的音訊路由傳送至房間效果群組，以新增回音。 切換至身歷聲時，它會將音訊路由至主要群組，並避免新增回音。

您已完成適用于 Unity 的 HoloLens 2 空間音訊教學課程。 恭喜！


