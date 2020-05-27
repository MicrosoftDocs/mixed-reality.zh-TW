---
title: 撰寫全像攝影遠端應用程式
description: 藉由建立全像遠端的遠端應用程式遠端內容（在遠端電腦上轉譯），可以串流處理至 HoloLens 2。 本文說明如何達成此目的。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 53f370dc32b4fe56eb610b6e5687022e0908f7a8
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866858"
---
# <a name="writing-a-holographic-remoting-remote-app"></a>撰寫全像攝影遠端應用程式

>[!IMPORTANT]
>本檔說明如何建立 HoloLens 2 的遠端應用程式。 **HoloLens （第1代）** 的遠端應用程式必須使用 NuGet **1.x.x**套件1.x 版。 這表示針對 HoloLens 2 所撰寫的遠端應用程式與 HoloLens 1 不相容，反之亦然。 您可以在[這裡](add-holographic-remoting.md)找到 HoloLens 1 的檔。

藉由建立全像遠端的遠端應用程式，在遠端電腦上呈現的遠端內容可以串流至 HoloLens 2。 本文說明如何達成此目的。 此頁面上的所有程式碼和工作專案都可以在全像的[遠端範例 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。

全像攝影遠端可讓應用程式以在桌上型電腦或 UWP 裝置（例如 Xbox One）上轉譯的全像 HoloLens 的內容作為目標，讓您可以存取更多的系統資源，並讓您能夠將遠端[沉浸式流覽](app-views.md)整合到現有的桌上型電腦軟體。 遠端應用程式會接收來自 HoloLens 2 的輸入資料流程、轉譯虛擬沉浸式視圖中的內容，以及將內容框架串流回 HoloLens 2。 連接是使用標準 Wi-fi 建立的。 全像攝影遠端會透過 NuGet 封包新增至桌面或 UWP 應用程式。 需要額外的程式碼來處理連接，並以沉浸式視圖呈現。

一般遠端連線的延遲時間會降到50毫秒。 Player 應用程式可以即時報告延遲。

## <a name="prerequisites"></a>Prerequisites

良好的起點是以 Windows Mixed Reality API 為目標的可運作 DirectX 型桌面或 UWP 應用程式。 如需詳細資訊，請參閱[DirectX 開發總覽](directx-development-overview.md)。 [C + + 全息版專案範本](creating-a-holographic-directx-project.md)是很好的起點。

>[!IMPORTANT]
>任何使用全像攝影遠端的應用程式，都應該撰寫成使用[多執行緒的單元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。 支援使用[單一執行緒的單元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)，但會導致在播放期間獲得最佳效能，而且可能會間斷情形。 使用 c + +/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started)時，多執行緒的單元是預設值。



## <a name="get-the-holographic-remoting-nuget-package"></a>取得全像攝影的遠端 NuGet 套件

若要將 NuGet 套件新增至 Visual Studio 中的專案，必須執行下列步驟。
1. 在 Visual Studio 中開啟專案。
2. 以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 套件 ...** ]
3. 在出現的面板中，按一下 **[流覽]** ，然後搜尋「全像遠端處理」。
4. 選取 [ **Microsoft 全息**]，並確定**挑選最新**的2.x 版，然後按一下 [**安裝**]。
5. 如果出現 [**預覽**] 對話方塊，請按一下 **[確定]**。
6. 下一個出現的對話方塊是授權合約。 按一下 [**我接受**] 以接受授權合約。

>[!NOTE]
>1.x**版的**NuGet 套件仍然可供想要以 HoloLens 1 為目標的開發人員使用。 如需詳細資訊，請參閱新增全像攝影[遠端（HoloLens （第1代））](add-holographic-remoting.md)。

## <a name="create-the-remote-context"></a>建立遠端內容

第一個步驟是應用程式應該建立遠端內容。

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>「全像」遠端處理的運作方式，是以遠端處理特定執行時間取代 Windows 中的 Windows Mixed Reality 執行時間。 這會在建立遠端內容期間完成。 因此，在建立遠端內容之前，任何 Windows Mixed Reality API 上的呼叫都會導致非預期的行為。 建議的方法是在與任何混合現實 API 互動之前，儘早建立遠端內容。 在使用建立或之後抓取的物件呼叫 CreateRemoteCoNtext 之前，絕不會透過任何 Windows Mixed Reality API 混合建立或取出的物件。

接下來，必須建立全像攝影空間。 不需要指定 CoreWindow。 沒有 CoreWindow 的桌面應用程式可以直接傳遞 ```nullptr``` 。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>連接到裝置

一旦遠端應用程式準備好呈現內容，就可以建立與裝置的連線。

連接可以透過兩種方式的其中一種來完成。
1) 遠端應用程式會連線到裝置上執行的玩家。
2) 裝置上執行的播放程式會連線到遠端應用程式。

若要建立從遠端應用程式到 HoloLens 2 的連接，請 ```Connect``` 在指定主機名稱和埠的遠端內容上呼叫方法。 全像攝影遠端播放程式所使用的埠是**8265**。

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>如同任何 c + +/WinRT API， ```Connect``` 可能會擲回需要處理的 WinRT：： hresult_error。

>[!TIP]
>若要避免使用[c + +/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/)語言投射， ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` 可以包含位於全像的遠端 NuGet 封裝內的檔案。 它包含基礎 COM 介面的宣告。 不過，建議使用 c + +/WinRT。

藉由呼叫方法，即可接聽遠端應用程式上的連入連線 ```Listen``` 。 在此呼叫期間，可以指定交握埠和傳輸埠。 交握埠會用於初始交握。 然後，資料會透過傳輸埠傳送。 預設會使用**8265**和**8266** 。

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>NuGet 套件內的包含適用于全像「全像」 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 遠端處理所公開之 API 的詳細檔。

## <a name="handling-remoting-specific-events"></a>處理遠端特定事件

遠端內容會公開三個重要的事件，以監視連接的狀態。
1) OnConnected：已成功建立與裝置的連線時觸發。
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected：在已建立的連接已關閉或無法建立連接時觸發。
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) OnListening：接聽連入連線時，會啟動。
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

此外，您還可以使用遠端內容上的屬性來查詢連接狀態 ```ConnectionState``` 。
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>處理語音事件

使用遠端語音介面，可以向 HoloLens 2 註冊語音觸發程式，並讓它們遠端處理至遠端應用程式。

需要此額外成員才能追蹤遠端語音的狀態。

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

首先，必須抓取遠端語音介面。

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

您可以使用非同步 helper 方法，初始化遠端語音。 這應該會以非同步方式完成，因為初始化可能需要相當長的時間。 [使用 c + + 的並行和非同步作業/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency)說明如何使用 c + +/winrt 撰寫非同步函式

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

有兩種方式可以指定要辨識的片語。
1) 語音文法 xml 檔案中的規格。 如需詳細資訊，請參閱[如何建立基本 XML 文法](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14))。
2) 藉由將字典向量內傳遞至來指定 ```ApplyParameters``` 。

在 OnRecognizedSpeech 回呼內，可以處理的語音事件如下：

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>在本機預覽串流內容

若要在傳送至裝置的遠端應用程式中顯示相同的內容， ```OnSendFrame``` 可以使用遠端內容的事件。 每次全像攝影 ```OnSendFrame``` 遠端程式庫將目前的框架傳送到遠端裝置時，就會觸發此事件。 這是接受內容並將它 array.blit 到桌面或 UWP 視窗的理想時機。

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a>深度 Reprojection

從版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)開始，全像攝影遠端支援[深度 Reprojection](hologram-stability.md#reprojection)。 除了色彩緩衝區之外，這還需要將深度緩衝區從遠端應用程式串流至 HoloLens 2。 根據預設，深度緩衝區資料流程已啟用並設定為使用色彩緩衝區的一半解析度。 這可以變更如下：

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

請注意，如果不應該使用預設值， ```ConfigureDepthVideoStream``` 就必須在建立與 HoloLens 2 的連線之前呼叫。 最好的地方是在您建立遠端內容之後。 DepthBufferStreamResolution 的可能值為：

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* Disabled （已新增版本[2.1.3](holographic-remoting-version-history.md#v2.1.3) ，如果未使用，則不會建立其他深度影片串流）

請記住，使用完整解析深度緩衝區也會影響頻寬需求，而且必須在您提供的最大頻寬值中列入考慮 ```CreateRemoteContext``` 。

在設定解決方案的旁邊，您也必須透過 HolographicCameraRenderingParameters 來認可深度緩衝區。 [CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

若要確認深度 reprojection 是否 correclty 在 HoloLens 2 上運作，您可以透過裝置入口網站啟用深度視覺化。 如需詳細資訊，請參閱[確認深度已正確設定](hologram-stability.md#verifying-depth-is-set-correctly)。

## <a name="optional-custom-data-channels"></a>選擇性：自訂資料通道

自訂資料通道可以用來透過已建立的遠端連線傳送使用者資料。 如需詳細資訊，請參閱[自訂資料通道](holographic-remoting-custom-data-channels.md)。

## <a name="see-also"></a>另請參閱
* [撰寫自訂的全像遠端播放播放機應用程式](holographic-remoting-create-player.md)
* [自訂全像攝影遠端資料通道](holographic-remoting-custom-data-channels.md)
* [使用全像攝影遠端建立安全連線](holographic-remoting-secure-connection.md)
* [全像攝影遠端疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
