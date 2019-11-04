---
title: DirectX 中的本機錨點傳輸
description: 說明如何藉由傳輸空間錨點來同步處理兩部 HoloLens 裝置。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，同步處理，空間錨點，傳輸，多人遊戲，視圖，案例，逐步解說，範例程式碼，傳輸，本機錨點傳輸，錨點匯出，錨點匯入
ms.openlocfilehash: f961862c3c49872484683e264fb9c62b5d0b60ee
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437952"
---
# <a name="local-anchor-transfers-in-directx"></a>DirectX 中的本機錨點傳輸

在無法使用<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間錨點</a>的情況下，本機錨點傳輸可讓一個 hololens 裝置匯出錨點，以供第二個 hololens 裝置匯入。

>[!NOTE]
>本機錨點傳輸提供較不健全的錨點回收，而不是使用<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間錨點</a>，而且此方法不支援 IOS 和 Android 裝置。

>[!NOTE]
>本文中的程式碼片段目前示範如何使用C++/cx， C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT，如全像攝影專案範本中所使用。  概念相當於C++/WinRT 專案，但您必須轉譯程式碼。

## <a name="transferring-spatial-anchors"></a>傳輸空間錨點

您可以使用[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)，在 Windows Mixed Reality 裝置之間傳輸空間錨點。 此 API 可讓您將錨點與所需的所有支援感應器資料組合在一起，以尋找世界中的確切位置，然後在另一個裝置上匯入該配套。 當第二個裝置上的應用程式匯入該錨點之後，每個應用程式都可以使用該共用空間錨點的座標系統來轉譯全息影像，然後在實際情況下出現于相同的位置。

請注意，空間錨點無法在不同的裝置類型之間傳輸，例如，可能無法使用沉浸式耳機來定位 HoloLens 空間錨點。  轉移的錨點也與 iOS 或 Android 裝置不相容。

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>設定應用程式以使用 spatialPerception 功能

您的應用程式必須先獲得使用 spatialPerception 功能的許可權，才能使用[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)。 這是必要的，因為傳輸空間錨點牽涉到在該錨點的區域中共用收集的感應器影像，其中可能包含機密資訊。

在您應用程式的 package.appxmanifest.xml 檔案中宣告這項功能。 以下是範例：

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

這項功能來自**uap2**命名空間。 若要在資訊清單中取得這個命名空間的存取權，請將它包含在 &lt;封裝 > 元素中做為*xlmns*屬性。 以下是範例：

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**注意：** 您的應用程式必須在執行時間要求功能，才能存取 SpatialAnchor 的匯出/匯入 Api。 請參閱下列範例中的[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) 。

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>使用 SpatialAnchorTransferManager 將錨點資料匯出以進行序列化

Helper 函式包含在程式碼範例中，可匯出（序列化） [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)資料。 此匯出 API 會將索引鍵/值組集合中的所有錨點序列化，並將字串與錨點產生關聯。

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

首先，我們需要設定資料流程。 這可讓我們成為1。）使用 TryExportAnchorsAsync 將資料放在應用程式所擁有的緩衝區中，以及2。將資料從匯出的位元組緩衝區資料流程（也就是 WinRT 資料流程）讀取到我們自己的記憶體緩衝區，也就是 std：： vector&lt;位元組 >。

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

我們需要要求許可權才能存取空間資料，包括系統所匯出的錨點。

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

如果我們取得許可權並匯出錨點，我們可以讀取資料流程。 在此，我們也會示範如何建立要用來讀取資料的 DataReader 和 InputStream。

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

從資料流程讀取位元組之後，我們可以將它們儲存到我們自己的資料緩衝區，如下所示。

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>使用 SpatialAnchorTransferManager 將錨點資料匯入至系統以將其還原序列化

Helper 函式包含在程式碼範例中，用以載入先前匯出的資料。 這個還原序列化函式會提供索引鍵/值組的集合，與 SpatialAnchorStore 所提供的相同，不同之處在于我們從另一個來源（例如網路通訊端）獲得這項資料。 您可以使用應用程式內記憶體或（如果適用的話）應用程式的 SpatialAnchorStore，在離線儲存資料之前，處理和原因。

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

首先，我們需要建立資料流程物件來存取錨定資料。 我們將從緩衝區將資料寫入系統緩衝區，因此我們將建立寫入記憶體中資料流程的資料寫入元，以達成將位元組緩衝區的錨點放入系統的 SpatialAnchors 的目標。

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

同樣地，我們需要確保應用程式有權匯出空間錨點資料，其中可能包含使用者環境的私用資訊。

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

如果允許存取，我們可以將緩衝區中的位元組寫入系統資料流程。

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

如果我們成功地將位元組儲存在資料流程中，我們可以嘗試使用 SpatialAnchorTransferManager 匯入該資料。

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

如果可以匯入資料，我們會取得索引鍵/值組的地圖視圖，將字串與錨點產生關聯。 我們可以將此載入至自己的記憶體中資料收集，並使用該集合來尋找我們有興趣使用的錨點。

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

**注意：** 這是因為您可以匯入錨點，但不一定表示您可以立即使用它。 錨點可能會位於不同的房間，或完全位於另一個實體位置;在收到錨點的裝置有足夠的視覺效果資訊來建立錨點所用的環境時，就不會找出錨定，以還原相對於已知目前環境的錨點位置。 用戶端執行應該嘗試找出相對於您當地座標系統或參考框架的錨點，然後再繼續嘗試將其用於即時內容。 例如，請嘗試定期尋找相對於目前座標系統的錨點，直到開始定位錨點為止。

## <a name="special-considerations"></a>特殊考慮

[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API 允許將多個[SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)匯出到同一個不透明的二進位 blob。 不過，blob 所包含的資料會有些許差異，端視單一呼叫中是否匯出單一 SpatialAnchor 或多個 SpatialAnchors 而定。

### <a name="export-of-a-single-spatialanchor"></a>匯出單一 SpatialAnchor

Blob 會在 SpatialAnchor 區域中包含環境的標記法，以便在匯入 SpatialAnchor 的裝置上辨識環境。 匯入完成之後，裝置將會提供新的 SpatialAnchor。 假設使用者最近曾在錨點附近，則可以將它放在可呈現的位置，並將其連接到 SpatialAnchor。 這些全息影像會顯示在匯出 SpatialAnchor 的原始裝置上的相同實體位置。

![匯出單一 SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>匯出多個 SpatialAnchors

如同匯出單一 SpatialAnchor，blob 會在所有指定 SpatialAnchors 的鄰近範圍中包含環境的標記法。 此外，blob 會包含包含的 SpatialAnchors 之間的連線相關資訊（如果它們位於相同的實體空間）。 這表示如果匯入兩個鄰近的 SpatialAnchors，則即使裝置只會辨識*第一個*SpatialAnchor 周圍的環境，也會找出附加到*第二*個 SpatialAnchor 的全息影像，因為有足夠的資料可供兩個 SpatialAnchors 之間的計算轉換已包含在 blob 中。 如果這兩個 SpatialAnchors 是個別匯出的（兩個 TryExportSpatialAnchors 呼叫），則 blob 中可能不會包含足夠的資料，以供連接到第二個 SpatialAnchor 的全息影像在第一個位置找到。

![使用單一 TryExportAnchorsAsync 呼叫匯出多個錨點](images/multipleanchors.png) ![針對每個錨點使用個別的 TryExportAnchorsAsync 呼叫匯出多個錨點](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>範例：使用 Windows：：網路：： StreamSocket 傳送錨點資料

在這裡，我們會提供範例，說明如何藉由在 TCP 網路上傳送來使用匯出的錨點資料。 這是來自 HolographicSpatialAnchorTransferSample。

WinRT StreamSocket 類別會使用 PPL 工作程式庫。 發生網路錯誤時，會使用重新擲回的例外狀況，將錯誤傳回給鏈中的下一個工作。 例外狀況包含 HRESULT，表示錯誤狀態。

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>使用 Windows：：網路：： StreamSocketListener 搭配 TCP 來傳送匯出的錨點資料

建立接聽連接的伺服器實例。

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

當收到連接時，請使用用戶端通訊端連接來傳送錨點資料。

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

現在，我們可以開始傳送包含匯出錨點資料的資料流程。

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

我們必須先傳送標頭封包，才可以傳送資料流程本身。 此標頭封包的長度必須是固定的，而且也必須指出錨點資料流程的變數陣列長度（以位元組為單位）。在此範例中，我們沒有其他要傳送的標頭資料，因此我們的標頭長度為4個位元組，且包含32位不帶正負號的整數。

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

資料流程長度（以位元組為單位）傳送至用戶端之後，我們就可以繼續將資料流程本身寫入通訊端資料流程。 這會導致將錨點存放區位元組傳送給用戶端。

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

如本主題稍早所述，我們必須準備好處理包含網路錯誤狀態訊息的例外狀況。 對於不預期的錯誤，我們可以將例外狀況資訊寫入至偵錯工具主控台，如下所示。 如果我們的程式碼範例無法完成連接，或如果無法完成傳送錨點資料，這將會提供線索給我們。

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>使用 Windows：：網路：： StreamSocket 搭配 TCP 來接收匯出的錨點資料

首先，我們必須連接到伺服器。 此程式碼範例示範如何建立和設定 StreamSocket，並建立一個 DataReader，讓您用來取得使用通訊端連接的網路資料。

**注意：** 如果您執行此範例程式碼，請確定您已設定並啟動伺服器，然後再啟動用戶端。

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

連接完成後，我們就可以等候伺服器傳送資料。 我們藉由在資料流程資料讀取器上呼叫 LoadAsync 來完成此動作。

我們收到的第一組位元組應該一律是標頭封包，以指出上一節中所述的錨點資料流程位元組長度。

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

...

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

在我們收到標頭封包之後，我們知道應該會有多少個位元組的錨點資料。 我們可以繼續從資料流程讀取這些位元組。

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

以下是用來接收錨點資料流程的程式碼。 同樣地，我們會先從資料流程載入位元組;這項作業可能需要一些時間才能完成，因為 StreamSocket 會等待收到來自網路的位元組數量。

當載入作業完成時，我們可以讀取該位元組數目。 如果我們收到預期錨點資料流程的位元組數目，我們可以繼續匯入錨定資料;如果不是，則必須有某種類型的錯誤。 例如，當伺服器實例在完成傳送資料流程之前就終止，或在用戶端接收整個資料流程之前，網路也會關閉之前，就可能發生這種情況。

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

同樣地，我們必須準備好處理未知的網路錯誤。

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

這樣就完成了！ 現在，您應該要有足夠的資訊，以嘗試尋找透過網路接收的錨點。 同樣地，請注意，用戶端必須有足夠的視覺化追蹤資料，空間才能成功找出錨點;如果無法立即使用，請嘗試一段時間。 如果仍然無法運作，請讓伺服器傳送更多錨點，並使用網路通訊來同意適用于用戶端的訊息。 您可以下載 HolographicSpatialAnchorTransferSample、設定您的用戶端和伺服器 Ip，並將其部署至用戶端和伺服器 HoloLens 裝置，以試做。

## <a name="see-also"></a>請參閱
* [平行模式程式庫（PPL）](https://msdn.microsoft.com/library/dd492418.aspx)
* [StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
