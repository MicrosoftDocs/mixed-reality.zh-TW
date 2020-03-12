---
title: 自訂全像攝影遠端資料通道
description: 自訂資料通道可以用來透過已建立的全像攝影遠端連線傳送使用者資料。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 8bfa19b7af0f3429130aabf70d9d11083bc56a52
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092300"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="c6d9e-104">自訂全像攝影遠端資料通道</span><span class="sxs-lookup"><span data-stu-id="c6d9e-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="c6d9e-105">本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="c6d9e-106">使用自訂資料通道，透過已建立的遠端連線傳送自訂資料。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c6d9e-107">自訂資料通道需要自訂的遠端應用程式和自訂播放機應用程式，因為這可讓兩個自訂應用程式之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-107">Custom data channels require a custom remote app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="c6d9e-108">您可以在全像攝影[遠端範例 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中的遠端和播放機範例中找到簡單的乒乓球範例。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-108">A simple ping-pong example can be found in the remote and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="c6d9e-109">取消批註 SampleRemoteMain 中的 ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE```，以啟用範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleRemoteMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="c6d9e-110">建立自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="c6d9e-110">Create a custom data channel</span></span>


<span data-ttu-id="c6d9e-111">若要建立自訂資料通道，需要下欄欄位：</span><span class="sxs-lookup"><span data-stu-id="c6d9e-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="c6d9e-112">成功建立連接之後，就可以從遠端端和/或播放程式端起始新的資料通道。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-112">After a connection was successfully established, the creation of new data channels can be initiated from either the remote side and/or the player side.</span></span> <span data-ttu-id="c6d9e-113">RemoteCoNtext 和 PlayerCoNtext 都提供 ```CreateDataChannel()``` 方法來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method to do this.</span></span> <span data-ttu-id="c6d9e-114">第一個參數是通道識別碼，用來識別後續作業中的資料通道。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-114">The first parameter is the channel ID which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="c6d9e-115">第二個參數是優先順序，指定此通道的資料傳輸到另一端的優先順序。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-115">The second parameter is the priority which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="c6d9e-116">通道識別碼的有效範圍為0到遠端端，包括63，而最多則為64，而不是播放程式端的127。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-116">The valid range for channel IDs is 0 up to and including 63 for the remote side and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="c6d9e-117">有效的優先順序為 ```Low```、```Medium``` 或 ```High``` （兩端）。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-117">Valid priorities are ```Low```, ```Medium``` or ```High``` (on both sides).</span></span>

<span data-ttu-id="c6d9e-118">若要起始在**遠端**端建立資料通道：</span><span class="sxs-lookup"><span data-stu-id="c6d9e-118">To initiate the creation of a data channel on the **remote** side:</span></span>
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="c6d9e-119">若要起始在**播放**端建立資料通道：</span><span class="sxs-lookup"><span data-stu-id="c6d9e-119">To initiate the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="c6d9e-120">若要建立新的自訂資料通道，只有一個側邊（遠端或玩家）需要呼叫 ```CreateDataChannel``` 方法。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-120">To create a new custom data channel, only one side (either remote or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="c6d9e-121">處理自訂資料通道事件</span><span class="sxs-lookup"><span data-stu-id="c6d9e-121">Handling custom data channel events</span></span>

<span data-ttu-id="c6d9e-122">若要建立自訂資料通道，必須處理 ```OnDataChannelCreated``` 事件（在玩家和遠端端）。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the remote side).</span></span> <span data-ttu-id="c6d9e-123">它會在使用者資料通道已由任一端建立時觸發，並提供 ```IDataChannel``` 物件，可用於透過此通道傳送和接收資料。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="c6d9e-124">若要在 ```OnDataChannelCreated``` 事件上註冊接聽程式：</span><span class="sxs-lookup"><span data-stu-id="c6d9e-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="c6d9e-125">若要在收到資料時收到通知，請向 ```OnDataChannelCreated``` 處理常式所提供之 ```IDataChannel``` 物件上的 ```OnDataReceived``` 事件註冊。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="c6d9e-126">註冊至 ```OnClosed``` 事件，以在資料通道關閉時收到通知。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a><span data-ttu-id="c6d9e-127">傳送資料</span><span class="sxs-lookup"><span data-stu-id="c6d9e-127">Sending data</span></span>

<span data-ttu-id="c6d9e-128">若要透過自訂資料通道傳送資料，請使用 ```IDataChannel::SendData()``` 方法。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="c6d9e-129">第一個參數是應該傳送之資料的 ```winrt::array_view<const uint8_t>```。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="c6d9e-130">第二個參數指定應重新傳送資料的位置，直到另一端認可接收為止。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="c6d9e-131">萬一發生網路狀況不佳的情況，相同的資料封包可能會抵達一次以上。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="c6d9e-132">接收程式碼必須能夠處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="c6d9e-133">關閉自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="c6d9e-133">Closing a custom data channel</span></span>

<span data-ttu-id="c6d9e-134">若要關閉自訂資料通道，請使用 ```IDataChannel::Close()``` 方法。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="c6d9e-135">一旦自訂資料通道關閉後，```OnClosed``` 事件就會通知雙方。</span><span class="sxs-lookup"><span data-stu-id="c6d9e-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="c6d9e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6d9e-136">See Also</span></span>
* [<span data-ttu-id="c6d9e-137">撰寫全像攝影遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="c6d9e-137">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="c6d9e-138">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="c6d9e-138">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="c6d9e-139">全像攝影遠端疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="c6d9e-139">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="c6d9e-140">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="c6d9e-140">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="c6d9e-141">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="c6d9e-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
