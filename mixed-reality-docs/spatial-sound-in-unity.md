---
title: Unity 中的空間音效
description: 從 Unity 場景內的特定3D 點播放空間音效。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間音效、HRTF、會議室大小
ms.openlocfilehash: af3f1486c3e931ad93d7b8960d822653ec740c12
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082036"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="56f73-104">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="56f73-104">Spatial sound in Unity</span></span>

<span data-ttu-id="56f73-105">此頁面會連結到 Unity 中的空間音效資源。</span><span class="sxs-lookup"><span data-stu-id="56f73-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="56f73-106">空間定位器選項</span><span class="sxs-lookup"><span data-stu-id="56f73-106">Spatializer options</span></span>
<span data-ttu-id="56f73-107">混合現實應用程式的空間定位器選項包括：</span><span class="sxs-lookup"><span data-stu-id="56f73-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="56f73-108">*MS HRTF 空間定位器*。</span><span class="sxs-lookup"><span data-stu-id="56f73-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="56f73-109">Unity 提供此做為*Windows Mixed Reality*選用套件的一部分。</span><span class="sxs-lookup"><span data-stu-id="56f73-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="56f73-110">這會在較高成本的「單一來源」架構中，于 CPU 上執行。</span><span class="sxs-lookup"><span data-stu-id="56f73-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="56f73-111">這是針對與原始 HoloLens 應用程式的回溯相容性而提供的。</span><span class="sxs-lookup"><span data-stu-id="56f73-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="56f73-112">*Microsoft 空間定位器*。</span><span class="sxs-lookup"><span data-stu-id="56f73-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="56f73-113">這可從[Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)取得。</span><span class="sxs-lookup"><span data-stu-id="56f73-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="56f73-114">這會使用較低成本的「多來源」架構。</span><span class="sxs-lookup"><span data-stu-id="56f73-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="56f73-115">在 HoloLens 2 上，這會卸載至硬體加速器。</span><span class="sxs-lookup"><span data-stu-id="56f73-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="56f73-116">針對新的應用程式，我們建議*Microsoft 空間定位器*。</span><span class="sxs-lookup"><span data-stu-id="56f73-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="56f73-117">啟用 spatialization</span><span class="sxs-lookup"><span data-stu-id="56f73-117">Enable spatialization</span></span>

<span data-ttu-id="56f73-118">使用[適用于 Unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)來安裝_SpatialAudio 空間定位器 unity_ ，並在專案的音訊設定中選擇 [ **microsoft 空間定位器**]。</span><span class="sxs-lookup"><span data-stu-id="56f73-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="56f73-119">然後：</span><span class="sxs-lookup"><span data-stu-id="56f73-119">Then:</span></span>
* <span data-ttu-id="56f73-120">將**音訊來源**連結至階層中的物件</span><span class="sxs-lookup"><span data-stu-id="56f73-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="56f73-121">核取 [**啟用 spatialization** ] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="56f73-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="56f73-122">將**空間 Blend**滑杆移至 ' 1 '</span><span class="sxs-lookup"><span data-stu-id="56f73-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="56f73-123">請確定您的開發人員工作站上已啟用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="56f73-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="56f73-124">以滑鼠右鍵按一下工作列中的磁片區圖示，並確定 [空間音效] 設定為 [關閉] 以外的專案，即可加以啟用。</span><span class="sxs-lookup"><span data-stu-id="56f73-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="56f73-125">若要取得您在 HoloLens 2 上聽到的最佳呈現方式，請選擇 [ **Windows Sonic For 耳機**]。</span><span class="sxs-lookup"><span data-stu-id="56f73-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones**.</span></span>

>[!NOTE]
><span data-ttu-id="56f73-126">如果您在 Unity 中收到錯誤，指出無法載入外掛程式 SpatialAudio，因為遺漏了其中一個相依性，請檢查您的電腦上是否已安裝最新版的[Microsoft Visual C++ ](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="56f73-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="56f73-127">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="56f73-127">For more details, see:</span></span>
* [<span data-ttu-id="56f73-128">Microsoft 空間定位器 GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="56f73-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="56f73-129">Microsoft 的空間定位器教學課程</span><span class="sxs-lookup"><span data-stu-id="56f73-129">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="56f73-130">Unity 的音訊來原始檔案</span><span class="sxs-lookup"><span data-stu-id="56f73-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="56f73-131">Unity 的空間定位器檔</span><span class="sxs-lookup"><span data-stu-id="56f73-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="56f73-132">以距離為基礎的衰減</span><span class="sxs-lookup"><span data-stu-id="56f73-132">Distance-based attenuation</span></span>
<span data-ttu-id="56f73-133">以 Unity 的預設距離為基礎的衰減，其最小距離為1個計量，而最大距離為500計量，而對數 rolloff 為。</span><span class="sxs-lookup"><span data-stu-id="56f73-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="56f73-134">這些設定可能適用于您的案例，或者您可能會發現來源的 attenuate 速度太快或太慢。</span><span class="sxs-lookup"><span data-stu-id="56f73-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="56f73-135">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="56f73-135">For more details, see:</span></span>
* <span data-ttu-id="56f73-136">針對建議的設定，[在混合現實中的音效設計](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="56f73-136">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="56f73-137">[Unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)，以取得有關設定這些曲線的指示。</span><span class="sxs-lookup"><span data-stu-id="56f73-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="56f73-138">殘響</span><span class="sxs-lookup"><span data-stu-id="56f73-138">Reverb</span></span>
<span data-ttu-id="56f73-139">根據預設， _Microsoft 空間定位器_會停用空間定位器後的效果。</span><span class="sxs-lookup"><span data-stu-id="56f73-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="56f73-140">若要啟用 hrtf 來源的回音和其他效果：</span><span class="sxs-lookup"><span data-stu-id="56f73-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="56f73-141">將**房間效果傳送層級**元件附加到每個來源</span><span class="sxs-lookup"><span data-stu-id="56f73-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="56f73-142">調整每個來源的傳送層級曲線，以控制送回給圖形以進行效果處理的音訊增益</span><span class="sxs-lookup"><span data-stu-id="56f73-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="56f73-143">如需詳細資訊，請參閱[空間定位器教學課程的第5章](unity-spatial-audio-ch5.md)。</span><span class="sxs-lookup"><span data-stu-id="56f73-143">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="56f73-144">Unity 空間音效範例</span><span class="sxs-lookup"><span data-stu-id="56f73-144">Unity spatial sound examples</span></span>
<span data-ttu-id="56f73-145">如需 Unity 中的空間音效範例，請參閱：</span><span class="sxs-lookup"><span data-stu-id="56f73-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="56f73-146">MRTK 示範</span><span class="sxs-lookup"><span data-stu-id="56f73-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="56f73-147">[Microsoft 空間定位器範例專案](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="56f73-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="56f73-148">後續步驟</span><span class="sxs-lookup"><span data-stu-id="56f73-148">Next steps</span></span>
* [<span data-ttu-id="56f73-149">混合現實中的音效設計</span><span class="sxs-lookup"><span data-stu-id="56f73-149">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="56f73-150">Microsoft 的空間定位器教學課程</span><span class="sxs-lookup"><span data-stu-id="56f73-150">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

