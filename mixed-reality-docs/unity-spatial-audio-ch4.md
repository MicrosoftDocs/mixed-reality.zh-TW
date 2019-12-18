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
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="faf31-105">在執行時間啟用和停用 spatialization</span><span class="sxs-lookup"><span data-stu-id="faf31-105">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="faf31-106">目標</span><span class="sxs-lookup"><span data-stu-id="faf31-106">Objectives</span></span>
<span data-ttu-id="faf31-107">在這第4章中，您將會：</span><span class="sxs-lookup"><span data-stu-id="faf31-107">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="faf31-108">新增腳本以控制遊戲物件上的 spatialization</span><span class="sxs-lookup"><span data-stu-id="faf31-108">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="faf31-109">從按鈕動作驅動 spatialization 控制項腳本</span><span class="sxs-lookup"><span data-stu-id="faf31-109">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="faf31-110">新增 spatialization 控制項腳本</span><span class="sxs-lookup"><span data-stu-id="faf31-110">Add spatialization control script</span></span>
<span data-ttu-id="faf31-111">以滑鼠右鍵按一下 [**專案**] 窗格，然後選擇C# [**建立 > C#腳本**] 來建立新的腳本。</span><span class="sxs-lookup"><span data-stu-id="faf31-111">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="faf31-112">將腳本命名為 "SpatializeOnOff"。</span><span class="sxs-lookup"><span data-stu-id="faf31-112">Name your script "SpatializeOnOff".</span></span>

![建立腳本](images/spatial-audio/create-script.png)

<span data-ttu-id="faf31-114">按兩下 [**專案**] 窗格中的腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="faf31-114">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="faf31-115">將預設腳本內容取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="faf31-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="faf31-116">腳本的幾行會加上批註。[第5章](unity-spatial-audio-ch5.md)將會取消批註這些行。</span><span class="sxs-lookup"><span data-stu-id="faf31-116">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="faf31-117">若要啟用或停用 spatialization，腳本只會調整**spatialBlend**屬性，並啟用**spatialization**屬性。</span><span class="sxs-lookup"><span data-stu-id="faf31-117">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="faf31-118">在此模式中，Unity 仍然會套用**磁片**區曲線。</span><span class="sxs-lookup"><span data-stu-id="faf31-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="faf31-119">否則，如果使用者從來源的遠處停用 spatialization，他們會聽到音量突然增加。</span><span class="sxs-lookup"><span data-stu-id="faf31-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="faf31-120">如果您想要完全停用 spatialization，請修改腳本，同時調整**SourceObject**變數的**spatialization**布林值屬性。</span><span class="sxs-lookup"><span data-stu-id="faf31-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="faf31-121">附加您的腳本，並從按鈕進行驅動</span><span class="sxs-lookup"><span data-stu-id="faf31-121">Attach your script and drive it from the button</span></span>
<span data-ttu-id="faf31-122">在**四**個 [偵測**器**] 窗格中，按一下 [**新增元件**]，並新增**Spatialize On** script：</span><span class="sxs-lookup"><span data-stu-id="faf31-122">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![將腳本新增至四個](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="faf31-124">在下列**四**種**Spatialize 的 Off**元件上：</span><span class="sxs-lookup"><span data-stu-id="faf31-124">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="faf31-125">**在階層**中尋找**PressableButtonHoloLens2-> IconAndText-> TextMeshPro**子物件</span><span class="sxs-lookup"><span data-stu-id="faf31-125">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subobject in the **Hierarchy**</span></span>
2. <span data-ttu-id="faf31-126">將 [ **TextMeshPro** suboject] 拖曳至 [ **Spatialize On** ] 元件的 [ **ButtonTextObject** ] 欄位</span><span class="sxs-lookup"><span data-stu-id="faf31-126">Drag the **TextMeshPro** suboject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="faf31-127">在這些變更之後，**四**個**Spatialize 的 Off**元件會如下所示：</span><span class="sxs-lookup"><span data-stu-id="faf31-127">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Spatialize on basic](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="faf31-129">若要設定按鈕以在放開按鈕時呼叫**Spatialize On**腳本，請開啟**PressableButtonHoloLens2**物件的 [偵測**器**] 窗格，尋找**可互動**元件，然後：</span><span class="sxs-lookup"><span data-stu-id="faf31-129">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="faf31-130">尋找**事件**子區段的**OnClick （）** 區域</span><span class="sxs-lookup"><span data-stu-id="faf31-130">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="faf31-131">將 [ **4** ] 從階層**拖曳至目標**物件位置。</span><span class="sxs-lookup"><span data-stu-id="faf31-131">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="faf31-132">從 [動作] 下拉式方塊中選取 [ **SpatializeOnOff SwapSpatialization** ]。</span><span class="sxs-lookup"><span data-stu-id="faf31-132">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="faf31-133">這些變更之後，**可互動**元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="faf31-133">After these changes, the **Interactable** component will look like this:</span></span>

![按鈕動作設定](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="faf31-135">後續步驟</span><span class="sxs-lookup"><span data-stu-id="faf31-135">Next steps</span></span>
<span data-ttu-id="faf31-136">在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="faf31-136">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="faf31-137">在應用程式中，您現在可以觸碰按鈕來啟用和停用影片上的 spatialization。</span><span class="sxs-lookup"><span data-stu-id="faf31-137">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="faf31-138">在 Unity 編輯器中測試時，請按空格鍵並使用滾輪進行滾動，以啟用 [手動模擬]。</span><span class="sxs-lookup"><span data-stu-id="faf31-138">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

<span data-ttu-id="faf31-139">繼續前往[第5章](unity-spatial-audio-ch5.md)，以使用回音來新增察覺到音效來源的距離。</span><span class="sxs-lookup"><span data-stu-id="faf31-139">Continue on to [Chapter 5](unity-spatial-audio-ch5.md) to add perceived distance to sound sources using reverb.</span></span>

