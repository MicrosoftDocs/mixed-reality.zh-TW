---
title: 空間音效
description: 在混合現實應用程式中使用空間音效, 可以讓您 convincingly 將音效放在3D 空間中。
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 空間音效, 環繞音效, 3d 音訊, 3d 音效, 空間音訊
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829925"
---
# <a name="spatial-sound"></a><span data-ttu-id="ffdfa-104">空間音效</span><span class="sxs-lookup"><span data-stu-id="ffdfa-104">Spatial sound</span></span>

<span data-ttu-id="ffdfa-105">當物件不在我們的視線時, 我們可以透過音效來觀察目前的狀況。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-105">When objects are out of our line of sight, one of the ways that we can perceive what's going on around us is through sound.</span></span> <span data-ttu-id="ffdfa-106">在 Windows Mixed Reality 中, 音訊引擎會使用方向、距離和環境模擬來模擬3D 音效, 以提供混合現實體驗的以聽覺方式元件。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-106">In Windows Mixed Reality, the audio engine provides the aural component of the mixed-reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="ffdfa-107">在應用程式中使用空間音效, 可以讓開發人員 convincingly 在使用者周圍, 以3維空間 (球體) 來放置聲音。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-107">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="ffdfa-108">這些聽起來好像是來自實際的實體物件, 或是使用者周圍的混合現實全息。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-108">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="ffdfa-109">由於[全息影像](hologram.md)是物件的光線, 有時也是音效, 因此音效元件可協助基礎的全像投影, 使其更可信, 並建立更有沉浸的體驗。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-109">Given that [holograms](hologram.md) are objects made of light and sometimes sound, the sound component helps ground holograms making them more believable and creating a more immersive experience.</span></span>

<span data-ttu-id="ffdfa-110">雖然全息影像只會以視覺化方式出現在使用者的眼睛指向何處, 但您應用程式的音效可能來自所有方向;上方、下方、後面、到側邊等等。您可以使用這項功能, 對可能目前不在使用者觀點中的物件繪製注意力。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-110">Although holograms can only appear visually where the user's gaze is pointing, your app's sound can come from all directions; above, below, behind, to the side, etc. You can use this feature to draw attention to an object that might not currently be in the user's view.</span></span> <span data-ttu-id="ffdfa-111">使用者可以察覺從混合現實世界中的來源 mouseleave 的音效。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-111">A user can perceive sounds to be emanating from a source in the mixed-reality world.</span></span> <span data-ttu-id="ffdfa-112">例如, 當使用者接近物件, 或物件接近其時, 磁片區就會增加。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-112">For example, as the user gets closer to an object or the object gets closer to them, the volume increases.</span></span> <span data-ttu-id="ffdfa-113">同樣地, 當物件在使用者之間移動時, 或相反的, 空間音效會提供聲音直接來自物件的假像。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-113">Similarly, as objects move around a user, or vice versa, spatial sounds give the illusion that sounds are coming directly from the object.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

## <a name="device-support"></a><span data-ttu-id="ffdfa-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="ffdfa-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ffdfa-115"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="ffdfa-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="ffdfa-116"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="ffdfa-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="ffdfa-117"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="ffdfa-117"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="ffdfa-118"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="ffdfa-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ffdfa-119">空間音效</span><span class="sxs-lookup"><span data-stu-id="ffdfa-119">Spatial sound</span></span></td>
        <td><span data-ttu-id="ffdfa-120">✔️</span><span class="sxs-lookup"><span data-stu-id="ffdfa-120">✔️</span></span></td>
        <td><span data-ttu-id="ffdfa-121">✔️</span><span class="sxs-lookup"><span data-stu-id="ffdfa-121">✔️</span></span></td>
        <td><span data-ttu-id="ffdfa-122">✔️ (含耳機)</span><span class="sxs-lookup"><span data-stu-id="ffdfa-122">✔️ (with headphones)</span></span></td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a><span data-ttu-id="ffdfa-123">模擬聲音的認知位置和距離</span><span class="sxs-lookup"><span data-stu-id="ffdfa-123">Simulating the perceived location and distance of sounds</span></span>

<span data-ttu-id="ffdfa-124">藉由分析音效如何達到我們的耳, 我們的大腦會決定物件發出音效的距離和方向。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-124">By analyzing how sound reaches both our ears, our brain determines the distance and direction of the object emitting the sound.</span></span> <span data-ttu-id="ffdfa-125">HRTF (或標頭相關的傳送函式) 會藉由建立 spectral 回應的模型來模擬這項互動, 以說明耳如何從空間的角度來接收音效。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-125">An HRTF (or Head Related Transfer Function) simulates this interaction by modeling the spectral response that characterizes how an ear receives sound from a point in space.</span></span> <span data-ttu-id="ffdfa-126">空間音效引擎使用個人化的 Hrtf 來擴展混合現實體驗, 並模擬來自各種方向和距離的聲音。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-126">The spatial audio engine uses personalized HRTFs to expand the mixed reality experience, and simulate sounds that are coming from various directions and distances.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

<span data-ttu-id="ffdfa-127">左或右音訊 (azimuth) 提示源自于每個耳的音效抵達時間差異。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-127">Left or right audio (azimuth) cues originate from differences in the time sound arrives at each ear.</span></span> <span data-ttu-id="ffdfa-128">向上和向下提示來自外部耳圖形 (pinnae) 所產生的 spectral 變更。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-128">Up and down cues originate from spectral changes produced by the outer ear shape (pinnae).</span></span> <span data-ttu-id="ffdfa-129">藉由指定音訊的來源, 系統可以模擬在不同時間到達我們的耳的音效體驗。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-129">By designating where audio is coming from, the system can simulate the experience of sound arriving at different times to our ears.</span></span> <span data-ttu-id="ffdfa-130">請注意, 在 HoloLens 上, 當 azimuth spatialization 是個人化時, 提高許可權的模擬是以一組平均的 anthropometrics 為基礎。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-130">Note that on HoloLens, while azimuth spatialization is personalized, the simulation of elevation is based on an average set of anthropometrics.</span></span> <span data-ttu-id="ffdfa-131">因此, 提高許可權精確度可能會比 azimuth 精確度更不精確。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-131">Thus, elevation accuracy may be less accurate than azimuth accuracy.</span></span>

<span data-ttu-id="ffdfa-132">音效的特性也會根據其存在的環境而變更。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-132">The characteristics of sounds also change based on the environment in which they exist.</span></span> <span data-ttu-id="ffdfa-133">比方說, cave 中的 shouting 會讓您的聲音從牆、地面和上限中退出, 並建立 echo 效果。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-133">For instance, shouting in a cave will cause your voice to bounce off the walls, floors, and ceilings, creating an echo effect.</span></span> <span data-ttu-id="ffdfa-134">空間音效的房間模型設定會重現這些反射, 以將聲音放在特定的音訊環境中。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-134">The room model setting of spatial sound reproduces these reflections to place sounds in a particular audio environment.</span></span> <span data-ttu-id="ffdfa-135">您可以使用這項設定來比對使用者在該空間中模擬音效的實際位置, 以建立更多沉浸的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-135">You can use this setting to match the user's actual location for simulation of sounds in that space to create a more immersive audio experience.</span></span>

## <a name="integrating-spatial-sound"></a><span data-ttu-id="ffdfa-136">整合空間音效</span><span class="sxs-lookup"><span data-stu-id="ffdfa-136">Integrating spatial sound</span></span>

<span data-ttu-id="ffdfa-137">因為混合現實的一般原則是要在使用者的實體世界或虛擬環境中接地[全息影像](hologram.md), 所以大部分來自全息的聲音都應該 hrtf。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-137">Because the general principle of mixed reality is to ground [holograms](hologram.md) in the user's physical world or virtual environment, most sounds from holograms should be spatialized.</span></span> <span data-ttu-id="ffdfa-138">在 HoloLens 上, 有自然的 CPU 和記憶體預算考慮, 但是您可以在該處使用10-12 空間音效, 同時使用低於 ~ 12% 的 CPU (70 約四個核心的其中一個)。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-138">On HoloLens, there are naturally CPU and memory budget considerations, but you can use 10-12 spatial sound voices there while using less than ~12% of the CPU (~70% of one of the four cores).</span></span> <span data-ttu-id="ffdfa-139">適用于空間音效語音的建議用法包括:</span><span class="sxs-lookup"><span data-stu-id="ffdfa-139">Recommended use for spatial sound voices include:</span></span>
* <span data-ttu-id="ffdfa-140">注視混合 (反白顯示物件, 特別是在外)。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-140">Gaze Mixing (highlighting objects, particularly when out of view).</span></span> <span data-ttu-id="ffdfa-141">當全息影像需要使用者注意時, 請在該全息影像上播放音效 (例如, 有虛擬狗吠)。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-141">When a hologram needs a user's attention, play a sound on that hologram (e.g. have a virtual dog bark).</span></span> <span data-ttu-id="ffdfa-142">這可協助使用者在未觀賞時尋找全息影像。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-142">This helps the user to find the hologram when it is not in view.</span></span>
* <span data-ttu-id="ffdfa-143">音訊 Haptics (適用于 touchless 互動的被動音訊)。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-143">Audio Haptics (reactive audio for touchless interactions).</span></span> <span data-ttu-id="ffdfa-144">例如, 當使用者的手或運動控制器進入並結束手勢畫面時, 播放音效。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-144">For example, play a sound when the user's hand or motion controller enters and exits the gesture frame.</span></span> <span data-ttu-id="ffdfa-145">或在使用者選取全息影像時播放音效。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-145">Or play a sound when the user selects a hologram.</span></span>
* <span data-ttu-id="ffdfa-146">深度 (使用者周圍的環境音效)。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-146">Immersion (ambient sounds surrounding the user).</span></span>

<span data-ttu-id="ffdfa-147">也請務必注意, 在混合標準身歷聲音效與空間音效時, 可以有效地建立實際的環境, 身歷聲音效應該相對無意義, 以留出空間音效的細微部分, 例如反射 (距離提示), 在雜訊的環境中可能很容易聽到。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-147">It is also important to note that while blending standard stereo sounds with spatial sound can be effective in creating realistic environments, the stereo sounds should be relatively quiet to leave room for the subtle aspects of spatial sound, such as reflections (distance cues) that can be difficult to hear in a noisy environment.</span></span>

<span data-ttu-id="ffdfa-148">Windows 的空間音效引擎僅支援播放的48k 取樣率。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-148">Windows' spatial sound engine only supports a 48k sample rate for playback.</span></span> <span data-ttu-id="ffdfa-149">大部分中介軟體 (例如 Unity) 都會自動將音效檔轉換成支援的格式, 但當您直接使用 Windows 音訊 Api 時, 請將內容格式與效果所支援的格式進行比對。</span><span class="sxs-lookup"><span data-stu-id="ffdfa-149">Most middleware, such as Unity, will automatically convert sound files into the supported format, but when using Windows Audio APIs directly please match the format of the content to the format supported by the effect.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffdfa-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffdfa-150">See also</span></span>
* [<span data-ttu-id="ffdfa-151">MR 空間220</span><span class="sxs-lookup"><span data-stu-id="ffdfa-151">MR Spatial 220</span></span>](holograms-220.md)
* [<span data-ttu-id="ffdfa-152">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="ffdfa-152">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="ffdfa-153">DirectX 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="ffdfa-153">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="ffdfa-154">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="ffdfa-154">Spatial sound design</span></span>](spatial-sound-design.md)
