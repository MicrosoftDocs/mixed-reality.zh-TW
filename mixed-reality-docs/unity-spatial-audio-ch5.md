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
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="c2608-105">使用回音來增加空間音訊的距離</span><span class="sxs-lookup"><span data-stu-id="c2608-105">Using reverb to add distance to spatial audio</span></span>

## <a name="objectives"></a><span data-ttu-id="c2608-106">目標</span><span class="sxs-lookup"><span data-stu-id="c2608-106">Objectives</span></span>
<span data-ttu-id="c2608-107">在上一章中，我們將 spatialization 新增到音效，讓他們有意義的方向。</span><span class="sxs-lookup"><span data-stu-id="c2608-107">In previous chapters, we added spatialization to sounds to give them a sense of direction.</span></span> <span data-ttu-id="c2608-108">在這第5章中，我們會新增一個回音效果，讓聽起來能夠說是距離。</span><span class="sxs-lookup"><span data-stu-id="c2608-108">In this 5th chapter, we'll add a reverb effect to give sounds a sense of distance.</span></span> <span data-ttu-id="c2608-109">我們的目標是：</span><span class="sxs-lookup"><span data-stu-id="c2608-109">Our objectives are to:</span></span>
* <span data-ttu-id="c2608-110">藉由新增回音來改善音效來源的認知距離</span><span class="sxs-lookup"><span data-stu-id="c2608-110">Improve perceived distance of sound sources by adding reverb</span></span>
* <span data-ttu-id="c2608-111">使用收聽者與全息影像的距離，控制聲音的觀察距離</span><span class="sxs-lookup"><span data-stu-id="c2608-111">Control perceived distance of the sound using the listener's distance to the hologram</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="c2608-112">新增混音器群組和回音效果</span><span class="sxs-lookup"><span data-stu-id="c2608-112">Add a mixer group and a reverb effect</span></span>
<span data-ttu-id="c2608-113">在[第2章](unity-spatial-audio-ch2.md)中，我們新增了混音器。</span><span class="sxs-lookup"><span data-stu-id="c2608-113">In [Chapter 2](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="c2608-114">混音器包含一個預設名為**Master**的**群組**。</span><span class="sxs-lookup"><span data-stu-id="c2608-114">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="c2608-115">因為我們只想要將回音效果套用到一些音效，所以讓我們為這些音效新增第二個**群組**。</span><span class="sxs-lookup"><span data-stu-id="c2608-115">Because we'll only want to apply a reverb effect to some sounds, let's add a second **Group** for those sounds.</span></span> <span data-ttu-id="c2608-116">若要新增**群組**，請以滑鼠右鍵按一下 [**音訊混音**器] 中的**主要**群組，然後選擇 [**新增子群組**]：</span><span class="sxs-lookup"><span data-stu-id="c2608-116">To add a **Group**, right click on the **Master** group in the **Audio Mixer** and choose **Add child group**:</span></span>

![新增子群組](images/spatial-audio/add-child-group.png)

<span data-ttu-id="c2608-118">在此範例中，我們將新的群組命名為「會議室效果」。</span><span class="sxs-lookup"><span data-stu-id="c2608-118">In this example, we've named the new group "Room Effect".</span></span>

<span data-ttu-id="c2608-119">每個**群組**都有自己的一組效果。</span><span class="sxs-lookup"><span data-stu-id="c2608-119">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="c2608-120">按一下新群組上的 [新增 **...** ]，然後選擇 [SFX] [**回音**]，將 [回音] 效果新增至新群組：</span><span class="sxs-lookup"><span data-stu-id="c2608-120">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![新增 SFX 回音](images/spatial-audio/add-sfx-reverb.png)

<span data-ttu-id="c2608-122">在音訊術語中，原始的 unreverberated 音訊稱為「_乾路徑_」，而使用「回音」篩選準則篩選後的音訊稱為「未幹」的_路徑_。</span><span class="sxs-lookup"><span data-stu-id="c2608-122">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="c2608-123">這兩個路徑都會傳送至音訊輸出，而且其在此混合中的相對強度稱為「_濕/幹混合_」。</span><span class="sxs-lookup"><span data-stu-id="c2608-123">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="c2608-124">濕/幹混合強烈影響距離的意義。</span><span class="sxs-lookup"><span data-stu-id="c2608-124">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="c2608-125">SFX 的「**回音**」包含控制項，可調整效果中的濕/幹混合。</span><span class="sxs-lookup"><span data-stu-id="c2608-125">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="c2608-126">由於**Microsoft 空間定位器**外掛程式會處理試路徑，因此我們只會針對濕路徑使用**SFX 回音**。</span><span class="sxs-lookup"><span data-stu-id="c2608-126">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="c2608-127">在您的**SFX 回音**的 [偵測**器**] 窗格上：</span><span class="sxs-lookup"><span data-stu-id="c2608-127">On the **Inspector** pane of your **SFX Reverb**:</span></span>
* <span data-ttu-id="c2608-128">將 [晾乾層級] 屬性設定為最低設定（-10000 mB）</span><span class="sxs-lookup"><span data-stu-id="c2608-128">Set the Dry Level property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="c2608-129">將 [房間] 屬性設為最高設定（0 mB）</span><span class="sxs-lookup"><span data-stu-id="c2608-129">Set the Room property to the highest setting (0 mB)</span></span>

<span data-ttu-id="c2608-130">這些變更之後， **SFX 回音**的偵測**器**窗格看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="c2608-130">After these changes, the **Inspector** pane of the **SFX Reverb** will look like this:</span></span>

![SFX 回音屬性](images/spatial-audio/sfx-reverb-properties.png)

<span data-ttu-id="c2608-132">其他設定則控制模擬室的風格。</span><span class="sxs-lookup"><span data-stu-id="c2608-132">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="c2608-133">特別是，**衰減時間**與認知的房間大小有關。</span><span class="sxs-lookup"><span data-stu-id="c2608-133">In particular, **Decay Time** is related to perceived room size.</span></span> 

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="c2608-134">在播放影片時啟用回音</span><span class="sxs-lookup"><span data-stu-id="c2608-134">Enable reverb on the video playback</span></span>
<span data-ttu-id="c2608-135">有兩個步驟可以在音訊來源上啟用「回音」：</span><span class="sxs-lookup"><span data-stu-id="c2608-135">There are two steps to enable reverb on an audio source:</span></span>
* <span data-ttu-id="c2608-136">將**音訊來源**路由至適當的**群組**</span><span class="sxs-lookup"><span data-stu-id="c2608-136">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="c2608-137">設定**Microsoft 空間定位器**外掛程式，將音訊傳遞至**群組**進行處理</span><span class="sxs-lookup"><span data-stu-id="c2608-137">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="c2608-138">在下列步驟中，我們將調整腳本以控制音訊路由，並附加**Microsoft 空間定位器**外掛程式所提供的控制項腳本，將資料摘要至回音。</span><span class="sxs-lookup"><span data-stu-id="c2608-138">In the following steps, we'll adjust our script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="c2608-139">在**四**個 [偵測**器**] 窗格中，按一下 [**新增元件**]，然後新增 [**會議室效果] 傳送層級**腳本：</span><span class="sxs-lookup"><span data-stu-id="c2608-139">On the **Inspector** pane for the **Quad**, click **Add Component** and add the **Room Effect Send Level** script:</span></span>

![新增傳送層級腳本](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> <span data-ttu-id="c2608-141">除非您啟用**Microsoft 空間定位器**外掛程式的**會議室效果傳送層級**功能，否則不會將任何音訊傳送回 Unity 音訊引擎以進行效果處理。</span><span class="sxs-lookup"><span data-stu-id="c2608-141">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="c2608-142">[**會議室效果傳送層級**] 元件包含一個圖形控制項，可設定傳送給 Unity 音訊引擎以進行回音處理的音訊層級。</span><span class="sxs-lookup"><span data-stu-id="c2608-142">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="c2608-143">按一下並向下拖曳曲線，將層級設定為 [關於-30dB]：</span><span class="sxs-lookup"><span data-stu-id="c2608-143">Click and drag the curve downwards to set the level to about -30dB:</span></span>

![調整回音曲線](images/spatial-audio/adjust-reverb-curve.png)

<span data-ttu-id="c2608-145">接下來，將**SpatializeOnOff**腳本中的4個批註行取消批註。</span><span class="sxs-lookup"><span data-stu-id="c2608-145">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="c2608-146">腳本現在會如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2608-146">The script will now look like this:</span></span>
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

<span data-ttu-id="c2608-147">取消批註這些行會將兩個屬性新增至腳本的 [偵測**器**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="c2608-147">Uncommenting these lines adds two properties to the **Inspector** pane for the script.</span></span> <span data-ttu-id="c2608-148">若要設定這些，請在**四**個**Spatialize**的 [Inspector] 元件上的 [偵測**器**] 窗格上：</span><span class="sxs-lookup"><span data-stu-id="c2608-148">To set these, on the **Inspector** pane of the **Spatialize On Off** component of the **Quad**:</span></span>
* <span data-ttu-id="c2608-149">將 [**房間效果群組**] 屬性設定為新的房間效果混音器群組</span><span class="sxs-lookup"><span data-stu-id="c2608-149">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="c2608-150">將 [**主要群組**] 屬性設定為 [主要混音器] 群組</span><span class="sxs-lookup"><span data-stu-id="c2608-150">Set the **Master Group** property to the Master mixer group</span></span>

<span data-ttu-id="c2608-151">這些變更之後， **Spatialize On**屬性會如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2608-151">After these changes, the **Spatialize On Off** properties will look like this:</span></span>

![Spatialize 已關閉擴充](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a><span data-ttu-id="c2608-153">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c2608-153">Next steps</span></span>

<span data-ttu-id="c2608-154">在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2608-154">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="c2608-155">現在，當您觸及應用程式中的按鈕來啟動 spatialization 時，腳本會將影片的音訊路由傳送至房間效果群組，以新增回音。</span><span class="sxs-lookup"><span data-stu-id="c2608-155">Now, when touching the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="c2608-156">切換至身歷聲時，它會將音訊路由至主要群組，並避免新增回音。</span><span class="sxs-lookup"><span data-stu-id="c2608-156">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

<span data-ttu-id="c2608-157">您已完成適用于 Unity 的 HoloLens 2 空間音訊教學課程。</span><span class="sxs-lookup"><span data-stu-id="c2608-157">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="c2608-158">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c2608-158">Congratulations!</span></span>


