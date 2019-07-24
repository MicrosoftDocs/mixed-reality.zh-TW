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
# <a name="spatial-sound-in-directx"></a>DirectX 中的空間音效

使用[XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)和[xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)音訊程式庫, 將空間音效新增至以 DirectX 為基礎的 Windows Mixed Reality 應用程式。

本主題使用來自 HolographicHRTFAudioSample 的範例程式碼。

>[!NOTE]
>本文中的程式碼片段目前示範如何使用C++/cx, C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT, 如全像攝影專案範本中所使用。  概念相當於C++/WinRT 專案, 但您必須轉譯程式碼。

## <a name="overview-of-head-relative-spatial-sound"></a>前端相對空間音效的總覽

空間音效會實作為**音訊處理物件 (APO)** , 其使用**head 相關的傳送函式 (HRTF)** 篩選器來*spatialize*一般的音訊串流。

在 pch 中包含這些標頭檔以存取音訊 Api:
* XAudio2。h
* xapo。h
* hrtfapoapi。h

若要設定空間音效:
1. 呼叫[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)以初始化 HRTF 音訊的新 APO。
2. 指派[HRTF 參數](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)和[HRTF 環境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx), 以定義空間音效 APO 的聲場特性。
3. 設定 XAudio2 引擎進行 HRTF 處理。
4. 建立[IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)物件, 並呼叫[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)。

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>在 DirectX 應用程式中執行 HRTF 和空間音效

您可以使用不同的參數和環境來設定 HRTF APO, 以達到各種效果。 使用下列程式碼來探索可能性。 從這裡下載通用 Windows 平臺程式碼範例:[空間音效範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

下列檔案提供 Helper 類型:
* [AudioFileReader .cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):使用媒體基礎和[IMFSourceReader 介面](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)載入音訊檔案。
* [XAudio2Helpers .h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):執行**SetupXAudio2**函式, 以初始化 XAudio2 以進行 HRTF 處理。

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>新增全方向來源的空間音效

使用者周圍的某些全息影像會以同樣的方向發出音效。 下列程式碼示範如何初始化 APO 以發出全方向音效。 在此範例中, 我們會從 Windows 全像應用程式範本將此概念套用到旋轉的 cube。 如需完整的程式代碼清單, 請參閱[OmnidirectionalSound。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)

**視窗的空間音效引擎僅支援播放的 48k samplerate。大部分的中介軟體程式 (例如 Unity) 都會自動將音效檔轉換成所需的格式, 但如果您在音訊系統中的較低層級開始開始進行或自行製作, 這點非常重要, 請務必避免損毀或不想要的行為, 例如HRTF 系統失敗。**

首先, 我們需要初始化 APO。 在我們的全像攝影範例應用程式中, 我們選擇在**HolographicSpace**之後執行這項操作。

From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

Initialize 的執行, 從*OmnidirectionalSound*:

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

設定 APO 以進行 HRTF 之後, 您可以呼叫來源語音上的[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)來播放音訊。 在我們的範例應用程式中, 我們選擇將它放在迴圈中, 讓您可以繼續聆聽來自 cube 的音效。

From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

從*OmnidirectionalSound*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

現在, 當我們更新框架時, 我們需要更新與裝置本身相關的全息影像位置。 這是因為 HRTF 位置一律會以相對於使用者的標頭表示, 包括標頭位置和方向。

若要在 HolographicSpace 中執行此動作, 我們必須將 SpatialStationaryFrameOfReference 座標系統中的轉換矩陣, 建立到固定到裝置本身的座標系統。

From *HolographicHrtfAudioSampleMain:: Update ()* :

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

HRTF 位置會直接套用至 OmnidirectionalSound helper 類別所 APO 的音效。

From *OmnidirectionalSound:: OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

就這麼容易！ 繼續閱讀, 以深入瞭解您可以使用 HRTF 音訊和 Windows 全像攝影的功能。

### <a name="initialize-spatial-sound-for-a-directional-source"></a>初始化方向性來源的空間音效

使用者周圍的某些全息影像大部分都是以單向方式發出音效。 這個音效模式的名稱是*cardioid* , 因為它看起來像是卡通的心。 下列程式碼示範如何初始化 APO 以發出方向音效。 如需完整的程式代碼清單, 請參閱[CardioidSound。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp)

設定 APO 以進行 HRTF 之後, 請呼叫來源語音上的 [[開始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)] 來播放音訊。

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

### <a name="implement-custom-decay"></a>執行自訂衰減

您可以覆寫空間音效在距離和 (或) 完全截斷的距離之間的速率。 若要在空間音效上執行自訂衰減行為, 請填入[HrtfDistanceDecay 結構](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx), 並將它指派給[HrtfApoInit 結構](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)中的**distanceDecay**欄位, 然後再將它傳遞給[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)函數。

將下列程式碼新增至先前所示的**Initialize**方法, 以指定自訂衰減行為。 如需完整的程式代碼清單, 請參閱[CustomDecay。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)

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
