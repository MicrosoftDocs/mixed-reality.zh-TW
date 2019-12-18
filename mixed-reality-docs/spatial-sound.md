---
title: 混合現實中的音訊
description: 混合現實中的音訊可以增加使用者對 UI 互動的信心，並 immerse 使用者體驗。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空間音效，環繞音效，3d 音訊，3d 音效，空間音訊
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181978"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="8f2e5-104">混合現實中的音訊</span><span class="sxs-lookup"><span data-stu-id="8f2e5-104">Audio in mixed reality</span></span>
<span data-ttu-id="8f2e5-105">音訊是混合現實中設計和生產力的重要部分。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="8f2e5-106">音效可以：</span><span class="sxs-lookup"><span data-stu-id="8f2e5-106">Sound can:</span></span>
* <span data-ttu-id="8f2e5-107">增加手勢和語音互動的使用者信賴度。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="8f2e5-108">引導使用者進行後續步驟。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-108">Guide users to next steps.</span></span>
* <span data-ttu-id="8f2e5-109">有效率地結合虛擬物件與真實世界。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="8f2e5-110">混合現實耳機的低延遲標頭追蹤（包括 HoloLens）支援高品質的 HRTF 型 spatialization。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="8f2e5-111">您可以在應用程式中 spatialize 音訊，以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8f2e5-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="8f2e5-112">請注意視覺元素。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="8f2e5-113">協助使用者維護其真實世界周圍的認知。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="8f2e5-114">聲場更深入地將全息影像連線到混合現實世界。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="8f2e5-115">它會提供有關環境和物件狀態的提示。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="8f2e5-116">請參閱[使用音訊的設計詳細範例](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="8f2e5-117">裝置支援</span><span class="sxs-lookup"><span data-stu-id="8f2e5-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8f2e5-118"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="8f2e5-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="8f2e5-119"><a href="hololens-hardware-details.md"><strong>HoloLens （第一代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="8f2e5-119"><a href="hololens-hardware-details.md"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8f2e5-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8f2e5-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="8f2e5-121"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="8f2e5-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8f2e5-122">Spatialization</span><span class="sxs-lookup"><span data-stu-id="8f2e5-122">Spatialization</span></span></td>
        <td><span data-ttu-id="8f2e5-123">✔️</span><span class="sxs-lookup"><span data-stu-id="8f2e5-123">✔️</span></span></td>
        <td><span data-ttu-id="8f2e5-124">✔️</span><span class="sxs-lookup"><span data-stu-id="8f2e5-124">✔️</span></span></td>
        <td><span data-ttu-id="8f2e5-125">✔️</span><span class="sxs-lookup"><span data-stu-id="8f2e5-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8f2e5-126">Spatialization 硬體加速</span><span class="sxs-lookup"><span data-stu-id="8f2e5-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="8f2e5-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8f2e5-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="8f2e5-128">在混合現實中使用音效</span><span class="sxs-lookup"><span data-stu-id="8f2e5-128">Use of sounds in mixed reality</span></span>
<span data-ttu-id="8f2e5-129">[在混合現實中使用](spatial-sound-design.md)音效，需要的方法與觸控和鍵盤和滑鼠應用程式不同。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="8f2e5-130">關鍵的設計決策包括要 spatialize 哪些聲音，以及要 sonify 哪些互動。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="8f2e5-131">這些決策會強烈影響使用者信賴度、生產力和學習曲線。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="8f2e5-132">案例研究</span><span class="sxs-lookup"><span data-stu-id="8f2e5-132">Case studies</span></span>
<span data-ttu-id="8f2e5-133">HoloTour 幾乎會讓使用者在世界各地旅遊和歷程記錄網站。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="8f2e5-134">請參閱 HoloTour 案例研究的[音效設計](case-study-spatial-sound-design-for-holotour.md)。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="8f2e5-135">用來捕捉主旨空間的特殊麥克風和轉譯設定。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="8f2e5-136">RoboRaid 是 HoloLens 的高能源射擊。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="8f2e5-137">RoboRaid 案例研究的[音效設計](case-study-using-spatial-sound-in-roboraid.md)描述了用來確保空間音訊最大效果的設計選擇。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="8f2e5-138">Spatialization</span><span class="sxs-lookup"><span data-stu-id="8f2e5-138">Spatialization</span></span>
<span data-ttu-id="8f2e5-139">Spatialization 是空間音訊的方向元件。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="8f2e5-140">若為7.1 的家庭劇院設定，spatialization 就像在 loudspeakers 之間移動一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="8f2e5-141">但對於混合式現實中的耳機，請務必使用 HRTF 型技術，以取得精確度和舒適度。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="8f2e5-142">Windows 提供以 HRTF 為基礎的 spatialization，而這種支援是 HoloLens 2 上的硬體加速。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="8f2e5-143">我應該 spatialize 嗎？</span><span class="sxs-lookup"><span data-stu-id="8f2e5-143">Should I spatialize?</span></span>
<span data-ttu-id="8f2e5-144">Spatialization 可以改善混合現實應用程式中的許多音效。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="8f2e5-145">Spatialization 會從接聽程式的標頭中取出聲音，並將其放在世界各地。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="8f2e5-146">如需在應用程式中有效使用 spatialization 的建議，請參閱[空間音效設計](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="8f2e5-147">空間定位器個人化</span><span class="sxs-lookup"><span data-stu-id="8f2e5-147">Spatializer personalization</span></span>
<span data-ttu-id="8f2e5-148">Hrtf 會操控各個頻率範圍內的各種層級和階段差異。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="8f2e5-149">它們是根據實體模型以及人類 head、torso 和耳（pinnae）的度量。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="8f2e5-150">我們的大腦會回應這些差異，以提供音效中的預期方向。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="8f2e5-151">每個人都有獨特的 ear 圖形、標題大小和耳位置。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="8f2e5-152">因此，最佳的 Hrtf 會符合您的規定。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="8f2e5-153">為了增加 spatialization 的精確度，HoloLens 會使用耳機顯示器的 pupilary 間距離（IPD）來調整您的前端大小 Hrtf。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="8f2e5-154">空間定位器平臺支援</span><span class="sxs-lookup"><span data-stu-id="8f2e5-154">Spatializer platform support</span></span>
<span data-ttu-id="8f2e5-155">Windows 透過[ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 hrtf。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="8f2e5-156">此 API 會向應用程式公開 HoloLens 2 HRTF 硬體加速。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="8f2e5-157">空間定位器中介軟體支援</span><span class="sxs-lookup"><span data-stu-id="8f2e5-157">Spatializer middleware support</span></span>
<span data-ttu-id="8f2e5-158">Windows ' Hrtf 的支援適用于下列協力廠商音訊引擎。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="8f2e5-159">[Unity 音訊引擎外掛程式](spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="8f2e5-159">A [Unity audio engine plugin](spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="8f2e5-160">[Wwise 音訊引擎外掛程式](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span><span class="sxs-lookup"><span data-stu-id="8f2e5-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="8f2e5-161">運轉</span><span class="sxs-lookup"><span data-stu-id="8f2e5-161">Acoustics</span></span>
<span data-ttu-id="8f2e5-162">空間音訊大約是方向。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="8f2e5-163">其他維度則包括遮蔽、障礙物、回音、portalling 和來源模型。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-163">Other dimensions include occlusion, obstruction, reverb, portalling, and source modeling.</span></span> <span data-ttu-id="8f2e5-164">這些維度*統稱為聲場。*</span><span class="sxs-lookup"><span data-stu-id="8f2e5-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="8f2e5-165">如果沒有聲場，hrtf 音效就不會察覺距離。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="8f2e5-166">聲場的治療範圍從簡單到非常複雜。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-166">Acoustics treatments range from simple to very complex.</span></span> <span data-ttu-id="8f2e5-167">您可以使用任何音訊引擎支援的簡單回音，將 hrtf 的聲音推送至接聽程式的環境。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-167">You can use a simple reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="8f2e5-168">聲場系統（例如[聲場專案](https://aka.ms/acoustics)）可提供更豐富且更吸引人的聲場處理。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-168">Acoustics systems such as [Project Acoustics](https://aka.ms/acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="8f2e5-169">聲場專案可以在音效上建立牆、門和其他場景幾何的效果模型。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="8f2e5-170">在開發階段已知相關場景幾何的案例中，這是有效的選項。</span><span class="sxs-lookup"><span data-stu-id="8f2e5-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8f2e5-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8f2e5-171">Next steps</span></span>
- [<span data-ttu-id="8f2e5-172">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="8f2e5-172">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
- [<span data-ttu-id="8f2e5-173">如何在混合現實應用程式中使用音效</span><span class="sxs-lookup"><span data-stu-id="8f2e5-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)
