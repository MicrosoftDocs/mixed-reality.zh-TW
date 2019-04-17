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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="c61c1-104">在 Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="c61c1-104">Spatial sound in Unity</span></span>

<span data-ttu-id="c61c1-105">本主題描述如何使用 Unity 專案中的空間音效。</span><span class="sxs-lookup"><span data-stu-id="c61c1-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="c61c1-106">它涵蓋了必要的外掛程式檔案，以及 Unity 元件和屬性，可讓空間音效。</span><span class="sxs-lookup"><span data-stu-id="c61c1-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="c61c1-107">讓空間在 Unity 中的音效</span><span class="sxs-lookup"><span data-stu-id="c61c1-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="c61c1-108">空間音效，在 Unity 中，會啟用使用音訊空間外掛程式。</span><span class="sxs-lookup"><span data-stu-id="c61c1-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="c61c1-109">讓啟用空間的聲音非常簡單，只要移至，外掛程式檔案會直接將 Unity 配套**編輯 > 專案設定 > 音訊**以及變更**空間外掛程式**來偵測器中**MS HRTF 空間**。</span><span class="sxs-lookup"><span data-stu-id="c61c1-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="c61c1-110">由於 Microsoft 空間只有目前支援 48000 Hz，您也應該將您系統的取樣率以防止在少數情況下，系統輸出裝置沒有已設定為 48000 HRTF 失敗 48000:</span><span class="sxs-lookup"><span data-stu-id="c61c1-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="c61c1-111">![AudioManager 的偵測器](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="c61c1-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="c61c1-112">*AudioManager 的偵測器*</span><span class="sxs-lookup"><span data-stu-id="c61c1-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="c61c1-113">您的 Unity 專案現在已設定為使用空間音效。</span><span class="sxs-lookup"><span data-stu-id="c61c1-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="c61c1-114">如果您不使用 Windows 10 電腦進行開發，您無法取得空間音效在編輯器中，也不在裝置上 （即使您使用 Windows 10 SDK）。</span><span class="sxs-lookup"><span data-stu-id="c61c1-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="c61c1-115">在 Unity 中使用空間的音效</span><span class="sxs-lookup"><span data-stu-id="c61c1-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="c61c1-116">空間音效用於您的 Unity 專案中，藉由調整音訊來源元件上的三個設定。</span><span class="sxs-lookup"><span data-stu-id="c61c1-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="c61c1-117">下列步驟將設定音訊來源元件的空間音效。</span><span class="sxs-lookup"><span data-stu-id="c61c1-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="c61c1-118">在 [**階層**] 面板中，選取具有附加的遊戲物件**音訊來源**。</span><span class="sxs-lookup"><span data-stu-id="c61c1-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="c61c1-119">在  **Inspector**  面板的 **音訊來源**元件</span><span class="sxs-lookup"><span data-stu-id="c61c1-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="c61c1-120">請檢查**Spatialize**選項。</span><span class="sxs-lookup"><span data-stu-id="c61c1-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="c61c1-121">設定**空間 Blend**要**3D** （數字值 1）。</span><span class="sxs-lookup"><span data-stu-id="c61c1-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="c61c1-122">為了獲得最佳結果，依序展開**3D 音效設定**並設定**磁碟區捲繞**來**自訂捲繞**。</span><span class="sxs-lookup"><span data-stu-id="c61c1-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="c61c1-123">![在 Unity 中顯示音訊來源的偵測器面板](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="c61c1-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="c61c1-124">*在 Unity 中顯示音訊來源的偵測器面板*</span><span class="sxs-lookup"><span data-stu-id="c61c1-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="c61c1-125">您的聲音現在實際上存在您的專案環境中 ！</span><span class="sxs-lookup"><span data-stu-id="c61c1-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="c61c1-126">強烈建議您先熟悉[空間音效設計指導方針](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="c61c1-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="c61c1-127">這些指導方針可協助您的音訊緊密整合您的專案，並進一步將您的使用者可享有到您已建立的體驗。</span><span class="sxs-lookup"><span data-stu-id="c61c1-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="c61c1-128">空間音效設定</span><span class="sxs-lookup"><span data-stu-id="c61c1-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="c61c1-129">Microsoft 空間音效外掛程式提供額外的參數，可以設定，在每個音訊來源為基礎，以允許音訊模擬的其他控制。</span><span class="sxs-lookup"><span data-stu-id="c61c1-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="c61c1-130">這個參數是房間的模擬的大小。</span><span class="sxs-lookup"><span data-stu-id="c61c1-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="c61c1-131">空間大小</span><span class="sxs-lookup"><span data-stu-id="c61c1-131">Room Size</span></span>

<span data-ttu-id="c61c1-132">模擬依據空間聲音的空間大小。</span><span class="sxs-lookup"><span data-stu-id="c61c1-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="c61c1-133">聊天室的近似大小是;(至小型會議室 office) 的小型、 中型 （大型會議空間） 和大型 (auditorium)。</span><span class="sxs-lookup"><span data-stu-id="c61c1-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="c61c1-134">您也可以指定無模擬戶外的環境的空間大小。</span><span class="sxs-lookup"><span data-stu-id="c61c1-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="c61c1-135">預設的空間大小很小。</span><span class="sxs-lookup"><span data-stu-id="c61c1-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="c61c1-136">範例</span><span class="sxs-lookup"><span data-stu-id="c61c1-136">Example</span></span>

<span data-ttu-id="c61c1-137">為 Unity MixedRealityToolkit 提供靜態類別，可讓您設定簡單空間音效設定。</span><span class="sxs-lookup"><span data-stu-id="c61c1-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="c61c1-138">這個類別可在[MixedRealityToolkit\SpatialSound 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)，而且可以從專案中的任何指令碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="c61c1-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="c61c1-139">建議每個音訊來源元件上設定這些參數，在您的專案。</span><span class="sxs-lookup"><span data-stu-id="c61c1-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="c61c1-140">下列範例會顯示附加的音訊來源選取中的空間大小。</span><span class="sxs-lookup"><span data-stu-id="c61c1-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="c61c1-141">直接存取從 Unity 的 參數</span><span class="sxs-lookup"><span data-stu-id="c61c1-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="c61c1-142">如果您不想要用於 MixedRealityToolkit 優異的音訊工具，以下是您想要如何變更 HRTF 參數。</span><span class="sxs-lookup"><span data-stu-id="c61c1-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="c61c1-143">您可以複製/貼上到指令碼中呼叫*SetHRTF.cs* ，您會想要附加至每個 HRTF AudioSource。</span><span class="sxs-lookup"><span data-stu-id="c61c1-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="c61c1-144">它可讓您將重要的參數變更為 HRTF。</span><span class="sxs-lookup"><span data-stu-id="c61c1-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="c61c1-145">混合的實境工具組中的空間音效</span><span class="sxs-lookup"><span data-stu-id="c61c1-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="c61c1-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="c61c1-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="c61c1-147">混合實境 Toolkit 中的下列範例會示範如何使用音效，讓您的經驗更沈浸式的一般音訊效果範例。</span><span class="sxs-lookup"><span data-stu-id="c61c1-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="c61c1-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span><span class="sxs-lookup"><span data-stu-id="c61c1-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="c61c1-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span><span class="sxs-lookup"><span data-stu-id="c61c1-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="c61c1-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c61c1-150">See also</span></span>
* [<span data-ttu-id="c61c1-151">空間的音效</span><span class="sxs-lookup"><span data-stu-id="c61c1-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="c61c1-152">空間完善的設計</span><span class="sxs-lookup"><span data-stu-id="c61c1-152">Spatial sound design</span></span>](spatial-sound-design.md)
