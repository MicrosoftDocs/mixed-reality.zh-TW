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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="8b443-104">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="8b443-104">Spatial sound in Unity</span></span>

<span data-ttu-id="8b443-105">本主題說明如何在您的 Unity 專案中使用空間音效。</span><span class="sxs-lookup"><span data-stu-id="8b443-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="8b443-106">它涵蓋了必要的外掛程式檔案, 以及可啟用空間音效的 Unity 元件和屬性。</span><span class="sxs-lookup"><span data-stu-id="8b443-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="8b443-107">啟用 Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="8b443-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="8b443-108">Unity 中的空間音效是使用音訊空間定位器外掛程式來啟用。</span><span class="sxs-lookup"><span data-stu-id="8b443-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="8b443-109">外掛程式檔案會直接結合到 Unity 中, 因此啟用空間音效就如同**編輯 > 專案設定 > 音訊**, 並將偵測器中的**空間定位器外掛程式**變更為**MS HRTF 空間定位器**一樣容易。</span><span class="sxs-lookup"><span data-stu-id="8b443-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="8b443-110">由於 Microsoft 空間定位器目前僅支援 48000Hz, 因此您也應該將系統取樣率設定為 48000, 以避免在系統輸出裝置尚未設定為48000的罕見情況下 HRTF 失敗:</span><span class="sxs-lookup"><span data-stu-id="8b443-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="8b443-111">![AudioManager 的偵測器](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="8b443-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="8b443-112">*AudioManager 的偵測器*</span><span class="sxs-lookup"><span data-stu-id="8b443-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="8b443-113">您的 Unity 專案現在已設定為使用空間音效。</span><span class="sxs-lookup"><span data-stu-id="8b443-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="8b443-114">如果您不是使用 Windows 10 電腦進行開發, 就不會在編輯器或裝置上取得空間音效 (即使您使用 Windows 10 SDK)。</span><span class="sxs-lookup"><span data-stu-id="8b443-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="8b443-115">在 Unity 中使用空間音效</span><span class="sxs-lookup"><span data-stu-id="8b443-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="8b443-116">在您的 Unity 專案中, 您可以調整音訊來源元件上的三項設定, 以使用空間音效。</span><span class="sxs-lookup"><span data-stu-id="8b443-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="8b443-117">下列步驟將設定您的音訊來源元件的空間音效。</span><span class="sxs-lookup"><span data-stu-id="8b443-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="8b443-118">在 [ 階層] 面板中, 選取具有已連接**音訊來源**的遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="8b443-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="8b443-119">在 [偵測**器**] 面板的 [**音訊來源**] 元件下</span><span class="sxs-lookup"><span data-stu-id="8b443-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="8b443-120">檢查**Spatialize**選項。</span><span class="sxs-lookup"><span data-stu-id="8b443-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="8b443-121">將**空間 Blend**設定為**3d** (數值 1)。</span><span class="sxs-lookup"><span data-stu-id="8b443-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="8b443-122">為獲得最佳結果, 請展開 [ **3D 音效設定**], 並將 [**磁片區 Rolloff** ] 設定為**自訂 Rolloff**</span><span class="sxs-lookup"><span data-stu-id="8b443-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="8b443-123">![Unity 中的偵測器面板, 顯示音訊來源](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="8b443-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="8b443-124">*Unity 中的偵測器面板, 顯示音訊來源*</span><span class="sxs-lookup"><span data-stu-id="8b443-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="8b443-125">您的音效現在實際存在於您專案的環境中!</span><span class="sxs-lookup"><span data-stu-id="8b443-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="8b443-126">強烈建議您熟悉[空間音效設計方針](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="8b443-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="8b443-127">這些指導方針可協助將您的音訊順暢地整合到您的專案, 並進一步 immerse 您的使用者, 使其成為您所建立的經驗。</span><span class="sxs-lookup"><span data-stu-id="8b443-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="8b443-128">設定空間音效設定</span><span class="sxs-lookup"><span data-stu-id="8b443-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="8b443-129">Microsoft 空間音效外掛程式會提供額外的參數, 可依每個音訊來源設定, 以允許其他音訊模擬的控制。</span><span class="sxs-lookup"><span data-stu-id="8b443-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="8b443-130">此參數是模擬空間的大小。</span><span class="sxs-lookup"><span data-stu-id="8b443-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="8b443-131">房間大小</span><span class="sxs-lookup"><span data-stu-id="8b443-131">Room Size</span></span>

<span data-ttu-id="8b443-132">空間音效模擬的房間大小。</span><span class="sxs-lookup"><span data-stu-id="8b443-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="8b443-133">房間的近似大小為;小型 (辦公室到小型會議室)、中型 (大型會議室) 和大型 (auditorium)。</span><span class="sxs-lookup"><span data-stu-id="8b443-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="8b443-134">您也可以指定 [無] 的房間大小來模擬室外環境。</span><span class="sxs-lookup"><span data-stu-id="8b443-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="8b443-135">預設的會議室大小很小。</span><span class="sxs-lookup"><span data-stu-id="8b443-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="8b443-136">範例</span><span class="sxs-lookup"><span data-stu-id="8b443-136">Example</span></span>

<span data-ttu-id="8b443-137">適用于 Unity 的 MixedRealityToolkit 提供靜態類別, 讓您可以輕鬆地設定空間音效設定。</span><span class="sxs-lookup"><span data-stu-id="8b443-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="8b443-138">這個類別可以在[MixedRealityToolkit\SpatialSound 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)中找到, 而且可以從專案中的任何腳本呼叫。</span><span class="sxs-lookup"><span data-stu-id="8b443-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="8b443-139">建議您在專案中的每個音訊來源元件上設定這些參數。</span><span class="sxs-lookup"><span data-stu-id="8b443-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="8b443-140">下列範例會示範如何選取連接音訊來源的中房間大小。</span><span class="sxs-lookup"><span data-stu-id="8b443-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="8b443-141">直接從 Unity 存取參數</span><span class="sxs-lookup"><span data-stu-id="8b443-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="8b443-142">如果您不想使用 MixedRealityToolkit 中的絕佳音訊工具, 以下是變更 HRTF 參數的方式。</span><span class="sxs-lookup"><span data-stu-id="8b443-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="8b443-143">您可以將此程式碼複製/貼上至名為*SetHRTF.cs*的腳本, 您會想要將它附加到每個 HRTF spatialize。</span><span class="sxs-lookup"><span data-stu-id="8b443-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="8b443-144">它可讓您將重要的參數變更為 HRTF。</span><span class="sxs-lookup"><span data-stu-id="8b443-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="8b443-145">混合現實工具組中的空間音效</span><span class="sxs-lookup"><span data-stu-id="8b443-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="8b443-146">HoloToolkit-Examples/SpatialSound/場景/UAudioManagerTest unity</span><span class="sxs-lookup"><span data-stu-id="8b443-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="8b443-147">下列混合現實工具組中的範例是一般的音訊效果範例, 示範如何使用音效讓您的體驗更具沉浸。</span><span class="sxs-lookup"><span data-stu-id="8b443-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="8b443-148">HoloToolkit-Examples/SpatialSound/場景/AudioLoFiTest unity</span><span class="sxs-lookup"><span data-stu-id="8b443-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="8b443-149">HoloToolkit-Examples/SpatialSound/場景/AudioOcclusionTest unity</span><span class="sxs-lookup"><span data-stu-id="8b443-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="8b443-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b443-150">See also</span></span>
* [<span data-ttu-id="8b443-151">空間音效</span><span class="sxs-lookup"><span data-stu-id="8b443-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="8b443-152">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="8b443-152">Spatial sound design</span></span>](spatial-sound-design.md)
