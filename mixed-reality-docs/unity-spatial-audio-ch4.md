---
title: 空間音訊教學課程-4。 在執行時間啟用和停用空間音訊
description: 使用按鈕，在執行時間啟用和停用音訊 spatialization。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教學課程，hololens2，空間音訊
ms.openlocfilehash: 3fc9b56dc58d4c19f229d92f4562f04cbca0e7a6
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182865"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a>在執行時間啟用和停用 spatialization

## <a name="objectives"></a>目標
在這第4章中，您將會：
* 新增腳本以控制遊戲物件上的 spatialization
* 從按鈕動作驅動 spatialization 控制項腳本

## <a name="add-spatialization-control-script"></a>新增 spatialization 控制項腳本
以滑鼠右鍵按一下 [**專案**] 窗格，然後選擇C# [**建立 > C#腳本**] 來建立新的腳本。 將腳本命名為 "SpatializeOnOff"。

![建立腳本](images/spatial-audio/create-script.png)

按兩下 [**專案**] 窗格中的腳本，在 Visual Studio 中開啟它。 將預設腳本內容取代為下列內容：

> [!NOTE]
> 腳本的幾行會加上批註。[第5章](unity-spatial-audio-ch5.md)將會取消批註這些行。

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> 若要啟用或停用 spatialization，腳本只會調整**spatialBlend**屬性，並啟用**spatialization**屬性。 在此模式中，Unity 仍然會套用**磁片**區曲線。 否則，如果使用者從來源的遠處停用 spatialization，他們會聽到音量突然增加。 <br> <br>
> 如果您想要完全停用 spatialization，請修改腳本，同時調整**SourceObject**變數的**spatialization**布林值屬性。

## <a name="attach-your-script-and-drive-it-from-the-button"></a>附加您的腳本，並從按鈕進行驅動
在**四**個 [偵測**器**] 窗格中，按一下 [**新增元件**]，並新增**Spatialize On** script：

![將腳本新增至四個](images/spatial-audio/add-script-to-quad.png)

在下列**四**種**Spatialize 的 Off**元件上：
1. **在階層**中尋找**PressableButtonHoloLens2-> IconAndText-> TextMeshPro**子物件
2. 將 [ **TextMeshPro** suboject] 拖曳至 [ **Spatialize On** ] 元件的 [ **ButtonTextObject** ] 欄位

在這些變更之後，**四**個**Spatialize 的 Off**元件會如下所示：

![Spatialize on basic](images/spatial-audio/spatialize-on-off-basic.png)

若要設定按鈕以在放開按鈕時呼叫**Spatialize On**腳本，請開啟**PressableButtonHoloLens2**物件的 [偵測**器**] 窗格，尋找**可互動**元件，然後：
1. 尋找**事件**子區段的**OnClick （）** 區域
2. 將 [ **4** ] 從階層**拖曳至目標**物件位置。
3. 從 [動作] 下拉式方塊中選取 [ **SpatializeOnOff SwapSpatialization** ]。

這些變更之後，**可互動**元件看起來會像這樣：

![按鈕動作設定](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a>後續步驟
在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。 在應用程式中，您現在可以觸碰按鈕來啟用和停用影片上的 spatialization。 在 Unity 編輯器中測試時，請按空格鍵並使用滾輪進行滾動，以啟用 [手動模擬]。 

繼續前往[第5章](unity-spatial-audio-ch5.md)，以使用回音來新增察覺到音效來源的距離。

