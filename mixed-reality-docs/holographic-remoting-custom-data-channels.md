---
title: 自訂全像攝影遠端資料通道
description: 自訂資料通道可以用來透過已建立的全像攝影遠端連線傳送使用者資料。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 9f7f20023d496412b331606e03d0c5110bb4864f
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718082"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="ae1d5-104">自訂全像攝影遠端資料通道</span><span class="sxs-lookup"><span data-stu-id="ae1d5-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="ae1d5-105">本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="ae1d5-106">使用自訂資料通道, 透過已建立的遠端連線傳送自訂資料。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="ae1d5-107">自訂資料通道需要自訂的主機應用程式和自訂播放機應用程式, 因為它允許兩個自訂應用程式之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-107">Custom data channels require a custom host app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="ae1d5-108">您可以在全像「全像」[遠端範例 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)內的主機和播放機範例中找到簡單的乒乓球範例。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-108">A simple ping-pong example can be found in the host and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="ae1d5-109">在```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` SampleHostMain/SamplePlayerMain 檔案內取消批註, 以啟用範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleHostMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


# <a name="create-a-custom-data-channel"></a><span data-ttu-id="ae1d5-110">建立自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="ae1d5-110">Create a custom data channel</span></span>


<span data-ttu-id="ae1d5-111">若要建立自訂資料通道, 需要下欄欄位:</span><span class="sxs-lookup"><span data-stu-id="ae1d5-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="ae1d5-112">成功建立連接之後, 就可以從主機端和 (或) 播放程式端起始新的資料通道建立。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-112">After a connection was successfully established, the creation of new data channels can be initiated from either the host side and/or the player side.</span></span> <span data-ttu-id="ae1d5-113">RemoteCoNtext 和 PlayerCoNtext 都提供```CreateDataChannel()```方法來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method to do this.</span></span> <span data-ttu-id="ae1d5-114">第一個參數是通道識別碼, 用來識別 susequent 作業中的資料通道。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-114">The first parameter is the channel ID which is used to identify the data channel in susequent operations.</span></span> <span data-ttu-id="ae1d5-115">第二個參數是優先順序, 指定此通道的資料傳輸到另一端的優先順序。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-115">The second paramter is the priority which specifies the priority with which data of this channel is transfered to the other side.</span></span> <span data-ttu-id="ae1d5-116">通道識別碼的有效範圍為0到 (含), 最多為主機端 63, 包括玩家端的127和64。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-116">The valid range for channel IDs is 0 up to and including 63 for the host side and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="ae1d5-117">有效的優先順序```Low```為```Medium``` 、 ```High```或 (兩端)。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-117">Valid priorities are ```Low```, ```Medium``` or ```High``` (on both sides).</span></span>

<span data-ttu-id="ae1d5-118">若要起始在**主機**端建立資料通道:</span><span class="sxs-lookup"><span data-stu-id="ae1d5-118">To initiate the creation of a data channel on the **host** side:</span></span>
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="ae1d5-119">若要起始在**播放**端建立資料通道:</span><span class="sxs-lookup"><span data-stu-id="ae1d5-119">To initiate the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="ae1d5-120">若要建立新的自訂資料通道, 只有一個側邊 (主機或玩家) 需要呼叫```CreateDataChannel```方法。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-120">To create a new custom data channel, only one side (either host or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="ae1d5-121">處理自訂資料通道事件</span><span class="sxs-lookup"><span data-stu-id="ae1d5-121">Handling custom data channel events</span></span>

<span data-ttu-id="ae1d5-122">若要建立自訂資料通道, ```OnDataChannelCreated```必須處理事件 (在 player 和主機端上)。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the host side).</span></span> <span data-ttu-id="ae1d5-123">它會在使用者資料通道已由任一端建立時觸發, 並提供```IDataChannel```物件, 可用來透過此通道傳送和接收資料。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="ae1d5-124">若要在```OnDataChannelCreated```事件上註冊接聽程式:</span><span class="sxs-lookup"><span data-stu-id="ae1d5-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="ae1d5-125">若要在收到資料時收到通知, 請在```OnDataReceived``` ```OnDataChannelCreated```處理常式所```IDataChannel```提供的物件上註冊事件。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="ae1d5-126">註冊至```OnClosed```事件, 以在資料通道關閉時收到通知。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

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

## <a name="sending-data"></a><span data-ttu-id="ae1d5-127">傳送資料</span><span class="sxs-lookup"><span data-stu-id="ae1d5-127">Sending data</span></span>

<span data-ttu-id="ae1d5-128">若要透過自訂資料通道傳送資料, 請```IDataChannel::SendData()```使用方法。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="ae1d5-129">第一個參數是```winrt::array_view<const uint8_t>```應傳送之資料的。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-129">The first paramter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="ae1d5-130">第二個參數指定指出應重新傳送資料, 直到另一端認可接收為止。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-130">The second parameter specifies wheter the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="ae1d5-131">萬一發生網路狀況不佳的情況, 相同的資料封包可能會抵達一次以上。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="ae1d5-132">接收程式碼必須能夠處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="ae1d5-133">關閉自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="ae1d5-133">Closing a custom data channel</span></span>

<span data-ttu-id="ae1d5-134">若要關閉自訂資料通道, 請```IDataChannel::Close()```使用方法。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="ae1d5-135">一旦自訂資料通道關閉後```OnClosed``` , 事件就會通知雙方。</span><span class="sxs-lookup"><span data-stu-id="ae1d5-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="ae1d5-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae1d5-136">See Also</span></span>
* [<span data-ttu-id="ae1d5-137">撰寫全像的遠端主機應用程式</span><span class="sxs-lookup"><span data-stu-id="ae1d5-137">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="ae1d5-138">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="ae1d5-138">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="ae1d5-139">全像攝影遠端疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="ae1d5-139">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="ae1d5-140">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="ae1d5-140">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="ae1d5-141">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="ae1d5-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)