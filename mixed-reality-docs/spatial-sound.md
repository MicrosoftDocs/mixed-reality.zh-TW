---
title: 混合現實中的音訊
description: 混合現實中的音訊可以增加使用者對 UI 互動的信心，並 immerse 使用者體驗。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空間音效，環繞音效，3d 音訊，3d 音效，空間音訊
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641110"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="03f28-104">混合現實中的音訊</span><span class="sxs-lookup"><span data-stu-id="03f28-104">Audio in Mixed Reality</span></span>
<span data-ttu-id="03f28-105">音訊是混合現實中設計和生產力的重要部分，而且可以：</span><span class="sxs-lookup"><span data-stu-id="03f28-105">Audio is an essential part of design and productivity in mixed reality, and can:</span></span>
* <span data-ttu-id="03f28-106">提升使用者對筆勢和語音互動的信心</span><span class="sxs-lookup"><span data-stu-id="03f28-106">Increase user confidence in gesture- and voice-based interactions</span></span>
* <span data-ttu-id="03f28-107">引導使用者進行後續步驟</span><span class="sxs-lookup"><span data-stu-id="03f28-107">Guide users to next steps</span></span>
* <span data-ttu-id="03f28-108">有效率地結合虛擬物件與真實世界</span><span class="sxs-lookup"><span data-stu-id="03f28-108">Effectively combine virtual objects with the real world</span></span>

<span data-ttu-id="03f28-109">混合現實耳機的低延遲標頭追蹤（包括 HoloLens）可讓您使用高品質的 HRTF 型 spatialization。</span><span class="sxs-lookup"><span data-stu-id="03f28-109">The low-latency head tracking of mixed reality headsets, including HoloLens, enables the use of high quality HRTF-based spatialization.</span></span> <span data-ttu-id="03f28-110">在您的應用程式中 Spatializing 音訊可以：</span><span class="sxs-lookup"><span data-stu-id="03f28-110">Spatializing audio in your application can:</span></span>
* <span data-ttu-id="03f28-111">呼叫視覺元素的注意力</span><span class="sxs-lookup"><span data-stu-id="03f28-111">Call attention to visual elements</span></span>
* <span data-ttu-id="03f28-112">協助使用者維護其真實世界周圍的認知</span><span class="sxs-lookup"><span data-stu-id="03f28-112">Help users maintain awareness of their real-world surroundings</span></span>

<span data-ttu-id="03f28-113">新增聲場更深入地將全息連接到混合的世界，並且可以提供有關環境和物件狀態的提示。</span><span class="sxs-lookup"><span data-stu-id="03f28-113">Adding acoustics more deeply connects holograms to the mixed world, and can provide cues about the environment and object state.</span></span>

<span data-ttu-id="03f28-114">如需使用音訊進行設計的詳細範例，請參閱[音效設計](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="03f28-114">For more detailed examples of design using audio, see [sound design](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="03f28-115">裝置支援</span><span class="sxs-lookup"><span data-stu-id="03f28-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="03f28-116"><strong>特徵</strong></span><span class="sxs-lookup"><span data-stu-id="03f28-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="03f28-117"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="03f28-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="03f28-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="03f28-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="03f28-119"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="03f28-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="03f28-120">Spatialization</span><span class="sxs-lookup"><span data-stu-id="03f28-120">Spatialization</span></span></td>
        <td><span data-ttu-id="03f28-121">✔️</span><span class="sxs-lookup"><span data-stu-id="03f28-121">✔️</span></span></td>
        <td><span data-ttu-id="03f28-122">✔️</span><span class="sxs-lookup"><span data-stu-id="03f28-122">✔️</span></span></td>
        <td><span data-ttu-id="03f28-123">✔️</span><span class="sxs-lookup"><span data-stu-id="03f28-123">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="03f28-124">Spatialization 硬體加速</span><span class="sxs-lookup"><span data-stu-id="03f28-124">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="03f28-125">✔️</span><span class="sxs-lookup"><span data-stu-id="03f28-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a><span data-ttu-id="03f28-126">在混合現實中使用音效</span><span class="sxs-lookup"><span data-stu-id="03f28-126">Using sounds in mixed reality</span></span>
<span data-ttu-id="03f28-127">[使用混合現實中](spatial-sound-design.md)的音效，可能需要與觸控和鍵盤和滑鼠應用程式不同的方法。</span><span class="sxs-lookup"><span data-stu-id="03f28-127">[Using sounds in mixed reality](spatial-sound-design.md) can require a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="03f28-128">關鍵的設計決策包括要 spatialize 哪些聲音，以及要 sonify 哪些互動。</span><span class="sxs-lookup"><span data-stu-id="03f28-128">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="03f28-129">這些決策可能會對使用者的信心、生產力和學習曲線造成很大的影響。</span><span class="sxs-lookup"><span data-stu-id="03f28-129">These decisions can have a strong effect on user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="03f28-130">案例研究</span><span class="sxs-lookup"><span data-stu-id="03f28-130">Case studies</span></span>
<span data-ttu-id="03f28-131">HoloTour 幾乎會讓使用者在世界各地旅遊和歷程記錄網站。</span><span class="sxs-lookup"><span data-stu-id="03f28-131">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="03f28-132">下列案例研究描述 HoloTour 的音效設計： HoloTour 的[音效設計](case-study-spatial-sound-design-for-holotour.md)。</span><span class="sxs-lookup"><span data-stu-id="03f28-132">The following case study describes the sound design for HoloTour: [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md).</span></span> <span data-ttu-id="03f28-133">用來捕捉主旨空間的特殊麥克風和轉譯設定。</span><span class="sxs-lookup"><span data-stu-id="03f28-133">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="03f28-134">RoboRaid 是 HoloLens 的高能源射擊。</span><span class="sxs-lookup"><span data-stu-id="03f28-134">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="03f28-135">下列案例研究描述的設計選擇，是為了確保已使用空間音訊來發揮最大效果： [RoboRaid 的音效設計](case-study-using-spatial-sound-in-roboraid.md)。</span><span class="sxs-lookup"><span data-stu-id="03f28-135">The following case study describes the design choices made to ensure spatial audio was used to fullest dramatic effect: [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span></span>

## <a name="spatialization"></a><span data-ttu-id="03f28-136">Spatialization</span><span class="sxs-lookup"><span data-stu-id="03f28-136">Spatialization</span></span>
<span data-ttu-id="03f28-137">Spatialization 是空間音訊的方向元件。</span><span class="sxs-lookup"><span data-stu-id="03f28-137">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="03f28-138">使用7.1 家用劇院設定時，spatialization 就像是在音量喇叭間移動一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="03f28-138">When using a 7.1 home theater setup, spatialization is as simple as panning between loud speakers.</span></span> <span data-ttu-id="03f28-139">但是，在混合式現實中，使用以 HRTF 為基礎的技術，是很重要的。</span><span class="sxs-lookup"><span data-stu-id="03f28-139">But with headphones in mixed reality it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="03f28-140">Windows 提供以 HRTF 為基礎的 spatialization，而這種支援是 HoloLens 2 上的硬體加速。</span><span class="sxs-lookup"><span data-stu-id="03f28-140">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="03f28-141">我應該 spatialize 嗎？</span><span class="sxs-lookup"><span data-stu-id="03f28-141">Should I spatialize?</span></span>
<span data-ttu-id="03f28-142">混合現實應用程式中的許多音效都受益于 spatialization，這會從接聽程式的頭部取得音效，並將其放在世界各地。</span><span class="sxs-lookup"><span data-stu-id="03f28-142">Many sounds in mixed reality applications benefit from spatialization, which takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="03f28-143">如需在應用程式中最有效使用 spatialization 的建議，請參閱[空間音效設計](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="03f28-143">Refer to [Spatial Sound Design](spatial-sound-design.md) for suggestions on the most effective uses of spatialization in your application.</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="03f28-144">空間定位器個人化</span><span class="sxs-lookup"><span data-stu-id="03f28-144">Spatializer personalization</span></span>
<span data-ttu-id="03f28-145">Hrtf 會操控各個頻率範圍內的各種層級和階段差異。</span><span class="sxs-lookup"><span data-stu-id="03f28-145">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="03f28-146">它們是根據實體模型以及人類 head、torso 和耳（pinnae）的度量。</span><span class="sxs-lookup"><span data-stu-id="03f28-146">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="03f28-147">我們的大腦會回應這些差異，以提供音效的方向。</span><span class="sxs-lookup"><span data-stu-id="03f28-147">Our brains respond to these differences to give rise to a perception of direction in sound.</span></span> 

<span data-ttu-id="03f28-148">每個人都有獨特的 ear 圖形、標題大小和耳位置，因此最佳的 Hrtf 是符合您的選擇。</span><span class="sxs-lookup"><span data-stu-id="03f28-148">Every individual has a unique ear shape, head size, and ear position, so the best HRTFs are those that conform to you.</span></span> <span data-ttu-id="03f28-149">HoloLens 會使用您從頭戴式裝置顯示的 pupilary 距離（IPD）來增加 spatialization 的精確度，以調整您的前端大小 Hrtf。</span><span class="sxs-lookup"><span data-stu-id="03f28-149">HoloLens increases spatialization accuracy by using your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="03f28-150">空間定位器平臺支援</span><span class="sxs-lookup"><span data-stu-id="03f28-150">Spatializer platform support</span></span>
<span data-ttu-id="03f28-151">Windows 透過[ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 hrtf。</span><span class="sxs-lookup"><span data-stu-id="03f28-151">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="03f28-152">此 API 會向應用程式公開 HoloLens 2 HRTF 硬體加速。</span><span class="sxs-lookup"><span data-stu-id="03f28-152">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="03f28-153">空間定位器中介軟體支援</span><span class="sxs-lookup"><span data-stu-id="03f28-153">Spatializer middleware support</span></span>
<span data-ttu-id="03f28-154">Windows ' Hrtf 的支援適用于一些協力廠商音訊引擎：</span><span class="sxs-lookup"><span data-stu-id="03f28-154">Support for Windows' HRTFs is available for some 3rd-party audio engines:</span></span>
* <span data-ttu-id="03f28-155">[Unity 音訊引擎](spatial-sound-in-unity.md)外掛程式會呼叫 HRTF XAPO</span><span class="sxs-lookup"><span data-stu-id="03f28-155">A [Unity audio engine](spatial-sound-in-unity.md) plugin calls the HRTF XAPO</span></span>
* <span data-ttu-id="03f28-156">[Wwise 音訊引擎外掛程式](https://www.audiokinetic.com/products/plug-ins/msspatial/)會呼叫 ISpatialAudioClient API</span><span class="sxs-lookup"><span data-stu-id="03f28-156">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/) calls the ISpatialAudioClient API</span></span>

## <a name="acoustics"></a><span data-ttu-id="03f28-157">運轉</span><span class="sxs-lookup"><span data-stu-id="03f28-157">Acoustics</span></span>
<span data-ttu-id="03f28-158">空間音訊可能會超過方向。</span><span class="sxs-lookup"><span data-stu-id="03f28-158">Spatial audio can be about more than direction.</span></span> <span data-ttu-id="03f28-159">其他維度（包括遮蔽、障礙物、回音、portalling 和來源模型）統稱為「聲場」。</span><span class="sxs-lookup"><span data-stu-id="03f28-159">Other dimensions, including occlusion, obstruction, reverb, portalling, and source modelling, are collectively referred to as 'acoustics'.</span></span> <span data-ttu-id="03f28-160">如果沒有聲場，hrtf 聽起來就沒有觀察距離。</span><span class="sxs-lookup"><span data-stu-id="03f28-160">Without acoustics, spatialized sounds lack a perceived distance.</span></span>

<span data-ttu-id="03f28-161">聲場處理的範圍可以從簡單到非常複雜。</span><span class="sxs-lookup"><span data-stu-id="03f28-161">Acoustics treatment can range from simple to very complex.</span></span> <span data-ttu-id="03f28-162">藉由使用任何音訊引擎所支援的簡單回音，您可以將 hrtf 推播到接聽程式周圍的環境中。</span><span class="sxs-lookup"><span data-stu-id="03f28-162">By using a simple reverb, such as that supported by any audio engine, you can push spatialized sounds out into the environment surrounding the listener.</span></span> <span data-ttu-id="03f28-163">聲場系統（如[聲場專案](https://aka.ms/acoustics)）提供更豐富且更吸引人的聲場處理。</span><span class="sxs-lookup"><span data-stu-id="03f28-163">Richer and more compelling acoustics treatment is available from acoustics systems such as [Project Acoustics](https://aka.ms/acoustics).</span></span> <span data-ttu-id="03f28-164">聲場專案可以在音效上建立牆、門和其他場景幾何的效果模型，這是在開發期間已知相關場景幾何的案例的有效選項。</span><span class="sxs-lookup"><span data-stu-id="03f28-164">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound, and is an effective option for cases where the relevant scene geometry is known at development time.</span></span>

