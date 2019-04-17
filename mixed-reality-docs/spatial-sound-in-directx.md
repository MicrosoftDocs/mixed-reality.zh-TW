---
title: DirectX 中的空間音效
description: 加入使用 XAudio2 和 xAPO 音訊程式庫，根據 DirectX 的 Windows Mixed Reality 應用程式空間的聲音。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows 混合實境，空間的聲音，應用程式，XAudio2，最低層級，xAPO、 音效的程式庫、 逐步解說中，DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597142"
---
# <a name="spatial-sound-in-directx"></a>DirectX 中的空間音效

加入以使用 DirectX 的 Windows Mixed Reality 應用程式空間的聲音[XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)並[xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)音訊程式庫。

本主題使用 HolographicHRTFAudioSample 範例程式碼。

>[!NOTE]
>目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。  概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。

## <a name="overview-of-head-relative-spatial-sound"></a>標頭相對空間音效的概觀

空間的聲音會實作成**音效處理物件 (APO)** 使用**標頭相關的傳送函式 (HRTF)** 篩選*spatialize*一般的音訊資料流。

若要存取 Api 的音訊的 pch.h 中包括這些標頭檔：
* XAudio2.h
* xapo.h
* hrtfapoapi.h

若要設定空間音效：
1. 呼叫[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)來初始化新的 APO HRTF 音訊。
2. 指派[HRTF 參數](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)並[HRTF 環境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx)定義空間的聲音 APO 柔和式特性。
3. 設定 XAudio2 引擎進行 HRTF 處理。
4. 建立[IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)物件，然後呼叫[開始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)。

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>在 DirectX 應用程式中實作 HRTF 和空間的音效

您可以藉由使用不同的參數和環境設定 HRTF APO 達成各種不同的效果。 您可以使用下列程式碼來探索各種可能性。 從這裡下載通用 Windows 平台程式碼範例：[Spatial 音效的範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

協助程式類型可在這些檔案中：
* [AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):使用媒體基礎載入音訊檔和[IMFSourceReader 介面](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)。
* [XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):Implements **SetupXAudio2**函式來初始化 XAudio2 HRTF 處理。

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>新增空間聲音 omnidirectional 來源

某些使用者的周圍環境中全像投影發出音效同樣往所有方向。 下列程式碼示範如何初始化 APO 發出 omnidirectional 音效。 在此範例中，我們套用於這個概念的旋轉立方體從 Windows 全像攝影版的應用程式範本。 如需完整的程式碼清單，請參閱[OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)。

**視窗的空間音效引擎只支援 48 k samplerate 播放。大部分的中介軟體程式，例如 Unity 會自動將音效檔轉換成所需的格式，但如果您啟動較低層級中音訊的系統，或進行您自己試幾次，這是一定要記住來防止損毀或不想要的行為，例如HRTF 系統失敗。**

首先，我們需要初始化 APO。 在我們全像攝影版的範例應用程式中，我們選擇這樣做，一旦**HolographicSpace**。

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

實作的初始化，從*OmnidirectionalSound.cpp*:

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

APO 已針對 HRTF 之後，您呼叫[啟動](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)上播放音訊來源語音。 在我們的範例應用程式，我們選擇將它放在迴圈中，以便您可以繼續聽到的聲音，來自該 cube。

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

從*OmnidirectionalSound.cpp*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

現在，每當我們更新畫面格時，我們需要更新全像的位置，相對於裝置本身。 這是因為 HRTF 位置一律以相對於使用者的大腦，包括前端的位置和方向。

若要在 HolographicSpace 這樣做，我們需要建構從我們 SpatialStationaryFrameOfReference 座標系統轉換矩陣，以固定為裝置本身的座標系統。

從*HolographicHrtfAudioSampleMain::Update()*:

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

HRTF 位置會直接套用至音效 APO OmnidirectionalSound 協助程式類別。

從*OmnidirectionalSound::OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

就這麼容易！ 繼續閱讀以深入了解您可以使用 HRTF 音訊 」 和 「 Windows 全像攝影版執行。

### <a name="initialize-spatial-sound-for-a-directional-source"></a>初始化方向性的來源空間音效

某些使用者的周圍環境中全像投影發出音效大部分是以單一方向。 此音效的模式稱為*cardioid*因為它看起來像卡通核心。 下列程式碼會示範如何初始化發出方向性 APO 音效。 如需完整的程式碼清單，請參閱[CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) 。

APO 已針對 HRTF 之後，請呼叫[啟動](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)上播放音訊來源語音。

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

### <a name="implement-custom-decay"></a>實作自訂的衰退

您可以覆寫的空間音效的減少距離和/或哪些距離它突然停止完全的速率。 若要實作自訂衰減行為上的空間的音效，填入[HrtfDistanceDecay 結構](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx)將其指派給**distanceDecay**欄位中[HrtfApoInit 結構](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)再傳遞給[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)函式。

將下列程式碼加入**初始化**先前所示，若要指定自訂的 decay 行為的方法。 如需完整的程式碼清單，請參閱[CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)。

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
