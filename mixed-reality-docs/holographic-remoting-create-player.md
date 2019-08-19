---
title: 撰寫自訂的全像遠端播放播放機
description: 藉由建立自訂的全像遠端播放機應用程式, 您可以建立自訂應用程式, 能夠將遠端電腦上呈現的內容顯示到 HoloLens 2。 本文說明如何達成此目的。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: fdc3d3bbd72d0812377d6a70c975f2111e1a2224
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718092"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>撰寫自訂的全像遠端播放播放機應用程式

>[!IMPORTANT]
>本檔說明如何建立 HoloLens 2 的自訂播放機應用程式。 針對 HoloLens 2 撰寫的自訂播放程式與針對 HoloLens 1 撰寫的主機應用程式不相容。 這表示這兩個應用程式都必須使用NuGet 套件 2.x. x 版。

藉由建立自訂的全像遠端播放機應用程式, 您可以建立自訂應用程式, 讓它能夠在 HoloLens 2 的遠端電腦上顯示[沉浸式視圖](app-views.md)。 本文說明如何達成此目的。 此頁面上的所有程式碼和工作專案都可以在全像的[遠端範例 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。

全像攝影遠端播放程式可讓您的應用程式顯示在桌上型電腦或 UWP 裝置 (例如 Xbox one) 上[轉譯](rendering.md)的全像攝影內容, 以允許存取更多系統資源。 全像攝影的遠端播放程式應用程式會將輸入資料串流至全像攝影的遠端主機應用程式, 並以影片和音訊串流的形式接收沉浸式觀賞。 連接是使用標準 Wi-fi 建立的。 若要建立播放機應用程式, 您將使用 NuGet 套件將全像的遠端處理新增至 UWP 應用程式, 並撰寫程式碼來處理連接並顯示沉浸式視圖。 

## <a name="prerequisites"></a>先決條件

良好的起點是已以 Windows Mixed Reality API 為目標的可運作 DirectX 型 UWP 應用程式。 如需詳細資訊, 請參閱[DirectX 開發總覽](directx-development-overview.md)。 如果您沒有現有的應用程式, 而且想要從頭開始, 全像[ C++投影專案範本](creating-a-holographic-directx-project.md)是不錯的起點。

>[!IMPORTANT]
>任何使用全像攝影遠端的應用程式, 都應該撰寫成使用[多執行緒的單元](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)。 支援使用[單一執行緒的 apartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) , 但會導致在播放期間的效能和可能會間斷情形。 使用C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started)時, 多執行緒的單元是預設值。

## <a name="get-the-holographic-remoting-nuget-package"></a>取得全像攝影的遠端 NuGet 套件

若要將 NuGet 套件新增至 Visual Studio 中的專案, 必須執行下列步驟。
1. 在 Visual Studio 中開啟專案。
2. 以滑鼠右鍵按一下專案節點, 然後選取 [**管理 NuGet 套件 ...** ]
3. 在出現的面板中, 按一下 **[流覽]** , 然後搜尋「全像遠端處理」。
4. 選取 [ **Microsoft 全息**], 並確定挑選最新的 2.x 版, 然後按一下 [**安裝**]。
5. 如果出現 [**預覽**] 對話方塊, 請按一下 **[確定]** 。
6. 下一個出現的對話方塊是授權合約。 按一下 [**我接受**] 以接受授權合約。

>[!IMPORTANT]
><a name="idl"></a>NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```套件內的包含適用于全像「全像」遠端處理所公開之 API 的詳細檔。

## <a name="modify-the-packageappxmanifest-of-the-application"></a>修改應用程式的 package.appxmanifest.xml

若要讓應用程式知道 NuGet 套件所新增的 AppRemoting, 您必須在專案上執行下列步驟:

1. 在 方案總管以滑鼠右鍵按一下**package.appxmanifest.xml**檔案, 然後選取 **開啟方式**...。
2. 選取 [ **XML (文字) 編輯器**], 然後按一下 [確定]
3. 將下列幾行新增至檔案並儲存
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>建立播放者內容

第一個步驟是應用程式應該建立播放機內容。

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>「全像」遠端處理的運作方式, 是以遠端處理特定執行時間取代 Windows 中的 Windows Mixed Reality 執行時間。 這會在建立播放者內容期間完成。 因此, 在建立播放程式內容之前, 任何 Windows Mixed Reality API 上的呼叫可能會導致非預期的行為。 建議的方法是在與任何混合現實 API 互動之前, 儘早建立播放者內容。 在```PlayerContext::Create()```使用建立或之後抓取的物件呼叫之前, 絕不會透過任何 Windows Mixed Reality API 混合建立或抓取的物件。

接下來, 您可以藉由呼叫[HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)來建立 HolographicSpace。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a>連接到主機

一旦播放機應用程式準備好呈現內容, 就可以建立與主機的連接。

您可以透過下列其中一種以下方式來建立連接:
1) 在 HoloLens 2 上執行的播放機應用程式會連接到主機應用程式。
2) 主機應用程式會連線到在 HoloLens 2 上執行的 player 應用程式。

若要從 player 應用程式連線到主機, 請```Connect```在指定主機名稱和埠的 player 內容上呼叫方法。 預設通訊埠為**8265**。

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>如同任何C++/WinRT API ```Connect``` , 可能會擲回需要處理的 WinRT:: hresult_error。

接聽 player 應用程式上的連入連線可以藉由呼叫```Listen```方法來完成。 在此呼叫期間, 可以指定交握埠和傳輸埠。 交握埠會用於初始交握。 然後, 資料會透過傳輸埠傳送。 預設會使用埠號碼**8265**和**8266** 。

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>處理連接相關的事件

會```PlayerContext```公開三個事件來監視連接的狀態。
1) OnConnected:已成功建立與主機的連接時觸發。
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected:在已建立的連接終止或無法建立連接時觸發。
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>可能```ConnectionFailureReason```的```Microsoft.Holographic.AppRemoting.idl```值記錄在[檔案](#idl)中。

3) OnListening:接聽連入連線時, 會啟動。
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

此外, 您還可以使用播放機內容上```ConnectionState```的屬性來查詢連接狀態。
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>顯示遠端呈現的框架

若要顯示遠端呈現的內容, ```PlayerContext::BlitRemoteFrame()```請在呈現[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)時呼叫。 

```BlitRemoteFrame()```需要將目前 HolographicFrame 的背景緩衝區系結為轉譯目標。 您可以透過[Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)屬性, 從[HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)接收後端緩衝區。

呼叫時, ```BlitRemoteFrame()```會將最新收到的框架從主應用程式複製到 HolographicFrame 的 BackBuffer。 此外, 如果遠端應用程式在呈現遠端框架期間已指定焦點, 則會設定焦點集合。

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame()```可能會覆寫目前框架的焦點。 
>- 若要指定回溯焦點點, 請先```PlayerContext::BlitRemoteFrame()```呼叫[HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 。 
>- 若要 overrwrite 遠端焦點點, 請在之後```PlayerContext::BlitRemoteFrame()```呼叫[HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 。

成功時, ```BlitRemoteFrame()``` ```BlitResult::Success_Color```會傳回。 否則, 它會傳回失敗原因:
- ```BlitResult::Failed_NoRemoteFrameAvailable```:失敗, 因為沒有可用的遠端框架。
- ```BlitResult::Failed_NoCamera```:失敗, 因為沒有任何相機存在。

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>選擇性：取得最後一個遠端框架的相關統計資料

若要診斷效能或網路問題, 可以```PlayerContext::LastFrameStatistics```透過屬性來抓取最後一個遠端框架的相關統計資料。 在呼叫[HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)期間, 會更新統計資料。

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

如需詳細資訊, 請```PlayerFrameStatistics```參閱檔案```Microsoft.Holographic.AppRemoting.idl```中的[檔](#idl)。

## <a name="optional-custom-data-channels"></a>選擇性：自訂資料通道

自訂資料通道可以用來透過已建立的遠端連線傳送使用者資料。 如需詳細資訊, 請參閱[自訂資料通道](holographic-remoting-custom-data-channels.md)。

## <a name="see-also"></a>另請參閱
* [撰寫全像的遠端主機應用程式](holographic-remoting-create-host.md)
* [自訂全像攝影遠端資料通道](holographic-remoting-custom-data-channels.md)
* [使用全像攝影遠端建立安全連線](holographic-remoting-secure-connection.md)
* [全像攝影遠端疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)