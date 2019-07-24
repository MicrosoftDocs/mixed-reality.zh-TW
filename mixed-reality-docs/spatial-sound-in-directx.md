---
title: DirectX 中的空間音效
description: 使用 XAudio2 和 xAPO 音訊程式庫, 將空間音效新增至以 DirectX 為基礎的 Windows Mixed Reality 應用程式。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed reality, 空間音效, 應用程式, XAudio2, 低層級, xAPO, 音訊庫, 逐步解說, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550438"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="9b489-104">DirectX 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="9b489-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="9b489-105">使用[XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)和[xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)音訊程式庫, 將空間音效新增至以 DirectX 為基礎的 Windows Mixed Reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9b489-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="9b489-106">本主題使用來自 HolographicHRTFAudioSample 的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="9b489-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="9b489-107">本文中的程式碼片段目前示範如何使用C++/cx, C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT, 如全像攝影專案範本中所使用。</span><span class="sxs-lookup"><span data-stu-id="9b489-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="9b489-108">概念相當於C++/WinRT 專案, 但您必須轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="9b489-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="9b489-109">前端相對空間音效的總覽</span><span class="sxs-lookup"><span data-stu-id="9b489-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="9b489-110">空間音效會實作為**音訊處理物件 (APO)** , 其使用**head 相關的傳送函式 (HRTF)** 篩選器來*spatialize*一般的音訊串流。</span><span class="sxs-lookup"><span data-stu-id="9b489-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="9b489-111">在 pch 中包含這些標頭檔以存取音訊 Api:</span><span class="sxs-lookup"><span data-stu-id="9b489-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="9b489-112">XAudio2。h</span><span class="sxs-lookup"><span data-stu-id="9b489-112">XAudio2.h</span></span>
* <span data-ttu-id="9b489-113">xapo。h</span><span class="sxs-lookup"><span data-stu-id="9b489-113">xapo.h</span></span>
* <span data-ttu-id="9b489-114">hrtfapoapi。h</span><span class="sxs-lookup"><span data-stu-id="9b489-114">hrtfapoapi.h</span></span>

<span data-ttu-id="9b489-115">若要設定空間音效:</span><span class="sxs-lookup"><span data-stu-id="9b489-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="9b489-116">呼叫[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)以初始化 HRTF 音訊的新 APO。</span><span class="sxs-lookup"><span data-stu-id="9b489-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="9b489-117">指派[HRTF 參數](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)和[HRTF 環境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx), 以定義空間音效 APO 的聲場特性。</span><span class="sxs-lookup"><span data-stu-id="9b489-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="9b489-118">設定 XAudio2 引擎進行 HRTF 處理。</span><span class="sxs-lookup"><span data-stu-id="9b489-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="9b489-119">建立[IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)物件, 並呼叫[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9b489-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="9b489-120">在 DirectX 應用程式中執行 HRTF 和空間音效</span><span class="sxs-lookup"><span data-stu-id="9b489-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="9b489-121">您可以使用不同的參數和環境來設定 HRTF APO, 以達到各種效果。</span><span class="sxs-lookup"><span data-stu-id="9b489-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="9b489-122">使用下列程式碼來探索可能性。</span><span class="sxs-lookup"><span data-stu-id="9b489-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="9b489-123">從這裡下載通用 Windows 平臺程式碼範例:[空間音效範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="9b489-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="9b489-124">下列檔案提供 Helper 類型:</span><span class="sxs-lookup"><span data-stu-id="9b489-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="9b489-125">[AudioFileReader .cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):使用媒體基礎和[IMFSourceReader 介面](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)載入音訊檔案。</span><span class="sxs-lookup"><span data-stu-id="9b489-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="9b489-126">[XAudio2Helpers .h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):執行**SetupXAudio2**函式, 以初始化 XAudio2 以進行 HRTF 處理。</span><span class="sxs-lookup"><span data-stu-id="9b489-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="9b489-127">新增全方向來源的空間音效</span><span class="sxs-lookup"><span data-stu-id="9b489-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="9b489-128">使用者周圍的某些全息影像會以同樣的方向發出音效。</span><span class="sxs-lookup"><span data-stu-id="9b489-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="9b489-129">下列程式碼示範如何初始化 APO 以發出全方向音效。</span><span class="sxs-lookup"><span data-stu-id="9b489-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="9b489-130">在此範例中, 我們會從 Windows 全像應用程式範本將此概念套用到旋轉的 cube。</span><span class="sxs-lookup"><span data-stu-id="9b489-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="9b489-131">如需完整的程式代碼清單, 請參閱[OmnidirectionalSound。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)</span><span class="sxs-lookup"><span data-stu-id="9b489-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="9b489-132">**視窗的空間音效引擎僅支援播放的 48k samplerate。大部分的中介軟體程式 (例如 Unity) 都會自動將音效檔轉換成所需的格式, 但如果您在音訊系統中的較低層級開始開始進行或自行製作, 這點非常重要, 請務必避免損毀或不想要的行為, 例如HRTF 系統失敗。**</span><span class="sxs-lookup"><span data-stu-id="9b489-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="9b489-133">首先, 我們需要初始化 APO。</span><span class="sxs-lookup"><span data-stu-id="9b489-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="9b489-134">在我們的全像攝影範例應用程式中, 我們選擇在**HolographicSpace**之後執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="9b489-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="9b489-135">From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="9b489-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="9b489-136">Initialize 的執行, 從*OmnidirectionalSound*:</span><span class="sxs-lookup"><span data-stu-id="9b489-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

```
// Initializes an APO that emits sound equally in all directions.
HRESULT OmnidirectionalSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        // Passing in nullptr as the first arg for HrtfApoInit initializes the APO with defaults of
        // omnidirectional sound with natural distance decay behavior.
        // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( nullptr, &xapo );
    }

    if ( SUCCEEDED( hr ) )
    {
        // _hrtfParams is of type ComPtr<IXAPOHrtfParameters>.
        hr = xapo.As( &_hrtfParams );
    }

    // Set the default environment.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice.
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;

        // _sourceVoice is of type IXAudio2SourceVoice*.
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

<span data-ttu-id="9b489-137">設定 APO 以進行 HRTF 之後, 您可以呼叫來源語音上的[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)來播放音訊。</span><span class="sxs-lookup"><span data-stu-id="9b489-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="9b489-138">在我們的範例應用程式中, 我們選擇將它放在迴圈中, 讓您可以繼續聆聽來自 cube 的音效。</span><span class="sxs-lookup"><span data-stu-id="9b489-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="9b489-139">From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="9b489-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="9b489-140">從*OmnidirectionalSound*:</span><span class="sxs-lookup"><span data-stu-id="9b489-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="9b489-141">現在, 當我們更新框架時, 我們需要更新與裝置本身相關的全息影像位置。</span><span class="sxs-lookup"><span data-stu-id="9b489-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="9b489-142">這是因為 HRTF 位置一律會以相對於使用者的標頭表示, 包括標頭位置和方向。</span><span class="sxs-lookup"><span data-stu-id="9b489-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="9b489-143">若要在 HolographicSpace 中執行此動作, 我們必須將 SpatialStationaryFrameOfReference 座標系統中的轉換矩陣, 建立到固定到裝置本身的座標系統。</span><span class="sxs-lookup"><span data-stu-id="9b489-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="9b489-144">From *HolographicHrtfAudioSampleMain:: Update ()* :</span><span class="sxs-lookup"><span data-stu-id="9b489-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

```
m_spinningCubeRenderer->Update(m_timer);

SpatialPointerPose^ currentPose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
if (currentPose != nullptr)
{
    // Use a coordinate system built from a pointer pose.
    SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
    if (pose != nullptr)
    {
        float3 headPosition = pose->Head->Position;
        float3 headUp = pose->Head->UpDirection;
        float3 headDirection = pose->Head->ForwardDirection;

        // To construct a rotation matrix, we need three vectors that are mutually orthogonal.
        // The first vector is the gaze vector.
        float3 negativeZAxis = normalize(headDirection);

        // The second vector should end up pointing away from the horizontal plane of the device.
        // We first guess by using the head "up" direction.
        float3 positiveYAxisGuess = normalize(headUp);

        // The third vector completes the set by being orthogonal to the other two.
        float3 positiveXAxis = normalize(cross(negativeZAxis, positiveYAxisGuess));

        // Now, we can correct our "up" vector guess by redetermining orthogonality.
        float3 positiveYAxis = normalize(cross(negativeZAxis, positiveXAxis));

        // The rotation matrix is formed as a standard basis rotation.
        float4x4 rotationTransform =
            {
            positiveXAxis.x, positiveYAxis.x, negativeZAxis.x, 0.f,
            positiveXAxis.y, positiveYAxis.y, negativeZAxis.y, 0.f,
            positiveXAxis.z, positiveYAxis.z, negativeZAxis.z, 0.f,
            0.f, 0.f, 0.f, 1.f,
            };

        // The translate transform can be constructed using the Windows::Foundation::Numerics API.
        float4x4 translationTransform = make_float4x4_translation(-headPosition);

        // Now, we have a basis transform from our spatial coordinate system to a device-relative
        // coordinate system.
        float4x4 coordinateSystemTransform = translationTransform * rotationTransform;

        // Reinterpret the cube position in the device's coordinate system.
        float3 cubeRelativeToHead = transform(m_spinningCubeRenderer->GetPosition(), coordinateSystemTransform);

        // Note that at (0, 0, 0) exactly, the HRTF audio will simply pass through audio. We can use a minimal offset
        // to simulate a zero distance when the hologram position vector is exactly at the device origin in order to
        // allow HRTF to continue functioning in this edge case.
        float distanceFromHologramToHead = length(cubeRelativeToHead);
        static const float distanceMin = 0.00001f;
        if (distanceFromHologramToHead < distanceMin)
        {
            cubeRelativeToHead = float3(0.f, distanceMin, 0.f);
        }

        // Position the spatial sound source on the hologram.
        m_omnidirectionalSound.OnUpdate(cubeRelativeToHead);

        // For debugging, it can be interesting to observe the distance in the debugger.
        /*
        std::wstring distanceString = L"Distance from hologram to head: ";
        distanceString += std::to_wstring(distanceFromHologramToHead);
        distanceString += L"\n";
        OutputDebugStringW(distanceString.c_str());
        */
    }
}
```

<span data-ttu-id="9b489-145">HRTF 位置會直接套用至 OmnidirectionalSound helper 類別所 APO 的音效。</span><span class="sxs-lookup"><span data-stu-id="9b489-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="9b489-146">From *OmnidirectionalSound:: OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="9b489-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="9b489-147">就這麼容易！</span><span class="sxs-lookup"><span data-stu-id="9b489-147">That's it!</span></span> <span data-ttu-id="9b489-148">繼續閱讀, 以深入瞭解您可以使用 HRTF 音訊和 Windows 全像攝影的功能。</span><span class="sxs-lookup"><span data-stu-id="9b489-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="9b489-149">初始化方向性來源的空間音效</span><span class="sxs-lookup"><span data-stu-id="9b489-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="9b489-150">使用者周圍的某些全息影像大部分都是以單向方式發出音效。</span><span class="sxs-lookup"><span data-stu-id="9b489-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="9b489-151">這個音效模式的名稱是*cardioid* , 因為它看起來像是卡通的心。</span><span class="sxs-lookup"><span data-stu-id="9b489-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="9b489-152">下列程式碼示範如何初始化 APO 以發出方向音效。</span><span class="sxs-lookup"><span data-stu-id="9b489-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="9b489-153">如需完整的程式代碼清單, 請參閱[CardioidSound。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp)</span><span class="sxs-lookup"><span data-stu-id="9b489-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="9b489-154">設定 APO 以進行 HRTF 之後, 請呼叫來源語音上的 [[開始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)] 來播放音訊。</span><span class="sxs-lookup"><span data-stu-id="9b489-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

```
// Initializes an APO that emits directional sound.
HRESULT CardioidSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );
    if ( SUCCEEDED( hr ) )
    {
        // Initialize with "Scaling" fully directional and "Order" with broad radiation pattern.
        // As the order goes higher, the cardioid directivity region becomes narrower.
        // Any direct path signal outside of the directivity region will be attenuated based on the scaling factor.
        // For example, if scaling is set to 1 (fully directional) the direct path signal outside of the directivity
        // region will be fully attenuated and only the reflections from the environment will be audible.
        hr = ConfigureApo( 1.0f, 4.0f );
    }
    return hr;
}

HRESULT CardioidSound::ConfigureApo( float scaling, float order )
{
    // Cardioid directivity configuration:
    // Directivity is specified at xAPO instance initialization and can't be changed per frame.
    // To change directivity, stop audio processing and reinitialize another APO instance with the new directivity.
    HrtfDirectivityCardioid cardioid;
    cardioid.directivity.type = HrtfDirectivityType::Cardioid;
    cardioid.directivity.scaling = scaling;
    cardioid.order = order;

    // APO intialization
    HrtfApoInit apoInit;
    apoInit.directivity = &cardioid.directivity;
    apoInit.distanceDecay = nullptr; // nullptr specifies natural distance decay behavior (simulates real world)

    // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
    ComPtr<IXAPO> xapo;
    auto hr = CreateHrtfApo( &apoInit, &xapo );

    if ( SUCCEEDED( hr ) )
    {
        hr = xapo.As( &_hrtfParams );
    }

    // Set the initial environment.
    // Environment settings configure the "distance cues" used to compute the early and late reverberations.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( _HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

### <a name="implement-custom-decay"></a><span data-ttu-id="9b489-155">執行自訂衰減</span><span class="sxs-lookup"><span data-stu-id="9b489-155">Implement custom decay</span></span>

<span data-ttu-id="9b489-156">您可以覆寫空間音效在距離和 (或) 完全截斷的距離之間的速率。</span><span class="sxs-lookup"><span data-stu-id="9b489-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="9b489-157">若要在空間音效上執行自訂衰減行為, 請填入[HrtfDistanceDecay 結構](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx), 並將它指派給[HrtfApoInit 結構](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)中的**distanceDecay**欄位, 然後再將它傳遞給[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)函數。</span><span class="sxs-lookup"><span data-stu-id="9b489-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="9b489-158">將下列程式碼新增至先前所示的**Initialize**方法, 以指定自訂衰減行為。</span><span class="sxs-lookup"><span data-stu-id="9b489-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="9b489-159">如需完整的程式代碼清單, 請參閱[CustomDecay。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)</span><span class="sxs-lookup"><span data-stu-id="9b489-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

```
HRESULT CustomDecaySound::Initialize( LPCWSTR filename )
{
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        HrtfDistanceDecay customDecay;
        customDecay.type = HrtfDistanceDecayType::CustomDecay;               // Custom decay behavior, we'll pass in the gain value on every frame.
        customDecay.maxGain = 0;                                             // 0dB max gain
        customDecay.minGain = -96.0f;                                        // -96dB min gain
        customDecay.unityGainDistance = HRTF_DEFAULT_UNITY_GAIN_DISTANCE;    // Default unity gain distance
        customDecay.cutoffDistance = HRTF_DEFAULT_CUTOFF_DISTANCE;           // Default cutoff distance

        // Setting the directivity to nullptr specifies omnidirectional sound.
        HrtfApoInit init;
        init.directivity = nullptr;
        init.distanceDecay = &customDecay;

        // CreateHrtfApo will fail with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( &init, &xapo );
    }
...
}
```
