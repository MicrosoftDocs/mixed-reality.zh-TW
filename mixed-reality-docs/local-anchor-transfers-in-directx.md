---
title: DirectX 中的本機的錨點傳輸
description: 說明如何同步處理兩個的 HoloLens 裝置傳輸空間的錨點。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，同步處理，空間的錨點、 傳輸、 多人遊戲，檢視、 案例、 逐步解說、 範例程式碼、 傳輸、 本機的錨點傳輸，錨點匯出、 錨點匯入
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597111"
---
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="f1c03-104">DirectX 中的本機的錨點傳輸</span><span class="sxs-lookup"><span data-stu-id="f1c03-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="f1c03-105">在無法使用的情況下<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>，本機的錨點傳輸啟用一個 HoloLens 裝置匯出要匯入第二個的 HoloLens 裝置所錨點。</span><span class="sxs-lookup"><span data-stu-id="f1c03-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="f1c03-106">本機的錨點傳輸提供較不強大的錨點重新叫用比<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>，以及 iOS 和 Android 裝置不支援這種方法。</span><span class="sxs-lookup"><span data-stu-id="f1c03-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="f1c03-107">目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="f1c03-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="f1c03-108">概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="f1c03-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="f1c03-109">傳輸的空間錨點</span><span class="sxs-lookup"><span data-stu-id="f1c03-109">Transferring spatial anchors</span></span>

<span data-ttu-id="f1c03-110">您可以使用 Windows Mixed Reality 裝置之間傳輸空間的錨點[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f1c03-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="f1c03-111">此 API 可讓您在世界中，尋找該確切的位置所需所有支援的感應器資料的套件組合設定錨點，然後再匯入另一個裝置上的該配套。</span><span class="sxs-lookup"><span data-stu-id="f1c03-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="f1c03-112">第二個裝置上的應用程式已匯入後會錨定，每個應用程式可能會呈現全像投影使用共用空間錨點的座標系統中，會出現在真實世界中的相同位置。</span><span class="sxs-lookup"><span data-stu-id="f1c03-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="f1c03-113">請注意，空間的錨點不能將不同的裝置類型，例如 HoloLens 空間錨點可能無法使用的沈浸式耳機之外的可尋獲。</span><span class="sxs-lookup"><span data-stu-id="f1c03-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="f1c03-114">傳送的錨點也與不相容的 iOS 或 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="f1c03-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="f1c03-115">將您的應用程式設定為使用 spatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="f1c03-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="f1c03-116">您的應用程式必須被授與使用 spatialPerception 功能，才能使用的權限[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f1c03-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="f1c03-117">這是必要的因為傳輸空間的錨點牽涉到共用附近會錨定，其中可能含有機密資訊的收集一段時間的感應器映像。</span><span class="sxs-lookup"><span data-stu-id="f1c03-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="f1c03-118">宣告您的應用程式的 package.appxmanifest 檔案中的這項功能。</span><span class="sxs-lookup"><span data-stu-id="f1c03-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="f1c03-119">以下為範例：</span><span class="sxs-lookup"><span data-stu-id="f1c03-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="f1c03-120">功能是來自**uap2**命名空間。</span><span class="sxs-lookup"><span data-stu-id="f1c03-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="f1c03-121">若要存取此命名空間資訊清單中，將它包含*xlmns*屬性中&lt;封裝 > 項目。</span><span class="sxs-lookup"><span data-stu-id="f1c03-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="f1c03-122">以下為範例：</span><span class="sxs-lookup"><span data-stu-id="f1c03-122">Here's an example:</span></span>

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="f1c03-123">**注意：** 您的應用程式必須要求在執行階段功能，才可存取 SpatialAnchor 匯出/匯入 Api。</span><span class="sxs-lookup"><span data-stu-id="f1c03-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="f1c03-124">請參閱[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx)在下面的範例。</span><span class="sxs-lookup"><span data-stu-id="f1c03-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="f1c03-125">藉由匯出與 SpatialAnchorTransferManager 序列化錨點的資料</span><span class="sxs-lookup"><span data-stu-id="f1c03-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="f1c03-126">在匯出程式碼範例包含 helper 函式 （序列化） [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)資料。</span><span class="sxs-lookup"><span data-stu-id="f1c03-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="f1c03-127">此匯出 API 將序列化字串關聯的錨點的索引鍵 / 值組的集合中的所有錨點。</span><span class="sxs-lookup"><span data-stu-id="f1c03-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

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

<span data-ttu-id="f1c03-128">首先，我們需要設定資料流。</span><span class="sxs-lookup"><span data-stu-id="f1c03-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="f1c03-129">這可讓我們為 1。）使用 TryExportAnchorsAsync 來將資料放在緩衝區中擁有的應用程式，以及 2）。讀取-也就是 WinRT 資料流-匯出的位元組緩衝區資料流中的資料，我們自己的記憶體緩衝區中，也就是 std:: vector&lt;位元組 >。</span><span class="sxs-lookup"><span data-stu-id="f1c03-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="f1c03-130">我們需要要求權限來存取空間資料，包括匯出的系統的錨點。</span><span class="sxs-lookup"><span data-stu-id="f1c03-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

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

<span data-ttu-id="f1c03-131">如果出現權限，而且會在匯出的錨點，我們可以讀取資料流。</span><span class="sxs-lookup"><span data-stu-id="f1c03-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="f1c03-132">在這裡，我們也會示範如何建立 DataReader 和 InputStream，我們將用來讀取資料。</span><span class="sxs-lookup"><span data-stu-id="f1c03-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

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

<span data-ttu-id="f1c03-133">我們從資料流讀取位元組之後，我們就可以將它們儲存到自己的資料緩衝區就像這樣。</span><span class="sxs-lookup"><span data-stu-id="f1c03-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="f1c03-134">藉由將它匯入系統，請使用 SpatialAnchorTransferManager 還原序列化錨點的資料</span><span class="sxs-lookup"><span data-stu-id="f1c03-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="f1c03-135">在程式碼範例中，將先前匯出的資料包含 helper 函式。</span><span class="sxs-lookup"><span data-stu-id="f1c03-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="f1c03-136">此還原序列化函式會提供類似 SpatialAnchorStore 所提供的功能-的索引鍵 / 值組的集合，不過我們有這項資料從其他來源，例如網路通訊端。</span><span class="sxs-lookup"><span data-stu-id="f1c03-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="f1c03-137">您可以處理，以及有關這項資料，再將其儲存為離線，並使用應用程式內的記憶體，原因 （如果適用） 或您的應用程式 SpatialAnchorStore。</span><span class="sxs-lookup"><span data-stu-id="f1c03-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

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

<span data-ttu-id="f1c03-138">首先，我們需要建立資料流物件來存取錨點的資料。</span><span class="sxs-lookup"><span data-stu-id="f1c03-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="f1c03-139">我們將寫入的資料從我們的緩衝區系統緩衝區，因此我們將建立為了完成我們的目標的位元組緩衝區中的錨點放 SpatialAnchors 系統寫入至記憶體中的資料流資料寫入元。</span><span class="sxs-lookup"><span data-stu-id="f1c03-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="f1c03-140">同樣地，我們需要確保應用程式有匯出空間的錨點的資料，可能包括使用者的環境的私用資訊的權限。</span><span class="sxs-lookup"><span data-stu-id="f1c03-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="f1c03-141">如果允許存取時，我們可以撰寫從緩衝區的位元組系統資料流。</span><span class="sxs-lookup"><span data-stu-id="f1c03-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

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

<span data-ttu-id="f1c03-142">如果已成功儲存的位元組資料流中，我們可以嘗試使用 SpatialAnchorTransferManager 資料匯入。</span><span class="sxs-lookup"><span data-stu-id="f1c03-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

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

<span data-ttu-id="f1c03-143">如果無法匯入資料，我們會取得字串關聯的錨點的索引鍵 / 值組的地圖檢視。</span><span class="sxs-lookup"><span data-stu-id="f1c03-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="f1c03-144">我們可以載入這我們自己記憶體中的資料集合，並使用該集合，看起來我們有興趣使用的錨點。</span><span class="sxs-lookup"><span data-stu-id="f1c03-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

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

<span data-ttu-id="f1c03-145">**注意：** 您可以匯入錨點，因為不一定表示您可以使用它立即。</span><span class="sxs-lookup"><span data-stu-id="f1c03-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="f1c03-146">錨點可能位於不同的空間或另一個實體位置完全;無法之外的可尋獲錨點，直到它收到的裝置有足夠 visual 錨點中，建立要還原的錨點位置，相對於已知的目前環境的環境資訊。</span><span class="sxs-lookup"><span data-stu-id="f1c03-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="f1c03-147">用戶端實作應該嘗試先嘗試使用實況內容，在執行之前先尋找相對於您的區域座標系統中或參考框架的錨點。</span><span class="sxs-lookup"><span data-stu-id="f1c03-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="f1c03-148">例如，嘗試定期直到開始是之外的可尋獲錨點時，才找出相對於目前的座標系統的錨點。</span><span class="sxs-lookup"><span data-stu-id="f1c03-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="f1c03-149">特殊的考量</span><span class="sxs-lookup"><span data-stu-id="f1c03-149">Special Considerations</span></span>

<span data-ttu-id="f1c03-150">[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API 可讓多個[SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)匯出到相同的不透明二進位 blob。</span><span class="sxs-lookup"><span data-stu-id="f1c03-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="f1c03-151">不過，還有哪些資料將包含的 blob，取決於是否匯出單一呼叫中的單一 SpatialAnchor 或多個 SpatialAnchors 些微的差異。</span><span class="sxs-lookup"><span data-stu-id="f1c03-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="f1c03-152">單一 SpatialAnchor 的匯出</span><span class="sxs-lookup"><span data-stu-id="f1c03-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="f1c03-153">Blob 包含 pe-15 SpatialAnchor 環境的表示法，以便匯入 SpatialAnchor 在裝置上可辨識的環境。</span><span class="sxs-lookup"><span data-stu-id="f1c03-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="f1c03-154">匯入完成之後，新的 SpatialAnchor 會提供給裝置。</span><span class="sxs-lookup"><span data-stu-id="f1c03-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="f1c03-155">假設使用者最近已經錨定的區域中，將予以之外的可尋獲，而且可以轉譯附加到 SpatialAnchor 全像投影。</span><span class="sxs-lookup"><span data-stu-id="f1c03-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="f1c03-156">這些全像投影會顯示在一樣匯出 SpatialAnchor 在原始裝置的相同實體位置。</span><span class="sxs-lookup"><span data-stu-id="f1c03-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![單一 SpatialAnchor 的匯出](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="f1c03-158">多個 SpatialAnchors 的匯出</span><span class="sxs-lookup"><span data-stu-id="f1c03-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="f1c03-159">單一 SpatialAnchor 匯出，例如 blob 會包含所有指定的 SpatialAnchors pe-15 環境的表示法。</span><span class="sxs-lookup"><span data-stu-id="f1c03-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="f1c03-160">此外，blob 包含包含 SpatialAnchors，之間連線的相關資訊，如果它們位於相同的實體空間中。</span><span class="sxs-lookup"><span data-stu-id="f1c03-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="f1c03-161">這表示，如果兩個鄰近 SpatialAnchors 匯入，然後雷射附加至*第二個*SpatialAnchor 會之外的可尋獲，即使裝置只會辨識四周圍環境*第一個*SpatialAnchor，因為資料不足，無法計算兩個 SpatialAnchors 之間進行轉換，所以已包含在 blob 中。</span><span class="sxs-lookup"><span data-stu-id="f1c03-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="f1c03-162">如果兩個 SpatialAnchors 個別匯出 （兩個不同的呼叫 TryExportSpatialAnchors） 就可能不會有足夠的第一個是可以找到當第二個 SpatialAnchor 全像投影附加 blob 中包含的資料所在。</span><span class="sxs-lookup"><span data-stu-id="f1c03-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![使用單一的 TryExportAnchorsAsync 呼叫匯出多個錨點](images/multipleanchors.png) ![針對每個錨點使用個別的 TryExportAnchorsAsync 呼叫匯出的多個錨點](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="f1c03-165">範例：傳送使用 Windows::Networking::StreamSocket 的錨點資料</span><span class="sxs-lookup"><span data-stu-id="f1c03-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="f1c03-166">在這裡，我們會提供如何使用匯出的錨點的資料，藉由傳送 TCP 網路上的範例。</span><span class="sxs-lookup"><span data-stu-id="f1c03-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="f1c03-167">這是從 HolographicSpatialAnchorTransferSample。</span><span class="sxs-lookup"><span data-stu-id="f1c03-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="f1c03-168">WinRT StreamSocket 類別會使用 PPL 工作程式庫。</span><span class="sxs-lookup"><span data-stu-id="f1c03-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="f1c03-169">在網路錯誤的情況下使用重新擲回的例外狀況鏈結中下一個工作被傳回的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1c03-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="f1c03-170">包含的例外狀況的 HRESULT，指出錯誤狀態。</span><span class="sxs-lookup"><span data-stu-id="f1c03-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="f1c03-171">使用與 TCP 的 Windows::Networking::StreamSocketListener，傳送匯出的錨點的資料</span><span class="sxs-lookup"><span data-stu-id="f1c03-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="f1c03-172">建立會接聽連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="f1c03-172">Create a server instance that listens for a connection.</span></span>

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

<span data-ttu-id="f1c03-173">當收到連接時，使用用戶端通訊端連線傳送錨點的資料。</span><span class="sxs-lookup"><span data-stu-id="f1c03-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

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

<span data-ttu-id="f1c03-174">現在，我們可以開始傳送資料流，其中包含匯出的錨點的資料。</span><span class="sxs-lookup"><span data-stu-id="f1c03-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

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

<span data-ttu-id="f1c03-175">我們可以傳送資料流本身之前，我們必須先傳送標頭的封包。</span><span class="sxs-lookup"><span data-stu-id="f1c03-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="f1c03-176">此標頭的封包必須是固定的長度，而且它也必須指出的長度是錨點資料流的位元組陣列變數在此範例中，我們已傳送的任何其他標頭資料，因此我們標頭是 4 個位元組，包含 32 位元不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="f1c03-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

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

<span data-ttu-id="f1c03-177">一旦資料流的長度，以位元組為單位，傳送至用戶端之後，我們可以繼續進行將通訊端的資料流中寫入資料流本身。</span><span class="sxs-lookup"><span data-stu-id="f1c03-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="f1c03-178">這會導致傳送到用戶端的錨點的儲存區位元組。</span><span class="sxs-lookup"><span data-stu-id="f1c03-178">This will cause the anchor store bytes to get sent to the client.</span></span>

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

<span data-ttu-id="f1c03-179">如本主題稍早所述，我們必須準備好處理包含網路錯誤狀態訊息的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1c03-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="f1c03-180">未預期的錯誤，我們可以將寫入例外狀況資訊的偵錯主控台就像這樣。</span><span class="sxs-lookup"><span data-stu-id="f1c03-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="f1c03-181">這可讓我們對於我們的程式碼範例中是無法完成連線，則無法完成傳送錨點資料時，發生了什麼事的線索。</span><span class="sxs-lookup"><span data-stu-id="f1c03-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="f1c03-182">若要接收匯出的錨點的資料使用 TCP 的 Windows::Networking::StreamSocket</span><span class="sxs-lookup"><span data-stu-id="f1c03-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="f1c03-183">首先，我們必須連線到伺服器。</span><span class="sxs-lookup"><span data-stu-id="f1c03-183">First, we have to connect to the server.</span></span> <span data-ttu-id="f1c03-184">此程式碼範例示範如何建立並設定 StreamSocket，並建立可用來取得使用通訊端連線的網路資料的 DataReader。</span><span class="sxs-lookup"><span data-stu-id="f1c03-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="f1c03-185">**注意：** 如果您執行此範例程式碼，請確定您設定及啟動之前啟動用戶端的伺服器。</span><span class="sxs-lookup"><span data-stu-id="f1c03-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

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

<span data-ttu-id="f1c03-186">一旦連線，我們可以等候伺服器以傳送資料。</span><span class="sxs-lookup"><span data-stu-id="f1c03-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="f1c03-187">我們這樣做，藉由在資料流資料讀取器上呼叫 LoadAsync。</span><span class="sxs-lookup"><span data-stu-id="f1c03-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="f1c03-188">我們收到的位元組為單位的第一個設定應該一律是標頭的封包，這表示錨點資料流的位元組長度，如上一節所述。</span><span class="sxs-lookup"><span data-stu-id="f1c03-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

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

<span data-ttu-id="f1c03-189">...</span><span class="sxs-lookup"><span data-stu-id="f1c03-189">...</span></span>

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

<span data-ttu-id="f1c03-190">我們已收到的標頭的封包之後，我們會知道多少個位元組的錨點我們應該預期的資料。</span><span class="sxs-lookup"><span data-stu-id="f1c03-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="f1c03-191">我們可以繼續從資料流讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="f1c03-191">We can proceed to read those bytes from the stream.</span></span>

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

<span data-ttu-id="f1c03-192">以下是我們的程式碼來接收錨點的資料流。</span><span class="sxs-lookup"><span data-stu-id="f1c03-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="f1c03-193">同樣地，我們將首先將位元組從資料流;這項作業可能需要一些時間才能完成，如 StreamSocket 等待從網路接收的位元組數量。</span><span class="sxs-lookup"><span data-stu-id="f1c03-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="f1c03-194">載入作業完成時，我們可以讀取該位元組數。</span><span class="sxs-lookup"><span data-stu-id="f1c03-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="f1c03-195">如果我們收到的預計錨點的資料流的位元組數目，我們可以繼續並匯入的錨點資料;如果沒有，則必須有某種形式的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1c03-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="f1c03-196">比方說，這種情形的伺服器執行個體終止之前就可以完成傳送資料流，或網路前用戶端可接收的整個資料流關閉時。</span><span class="sxs-lookup"><span data-stu-id="f1c03-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

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

<span data-ttu-id="f1c03-197">同樣地，我們必須準備處理不明的網路錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1c03-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="f1c03-198">就這麼容易！</span><span class="sxs-lookup"><span data-stu-id="f1c03-198">That's it!</span></span> <span data-ttu-id="f1c03-199">現在，您應該有足夠的資訊，請嘗試尋找透過網路接收的錨點。</span><span class="sxs-lookup"><span data-stu-id="f1c03-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="f1c03-200">同樣地，請注意，用戶端必須成功找出錨點; 的空間不足，無法 visual 的追蹤資料如果立即無法運作，請嘗試四處跑一段時間。</span><span class="sxs-lookup"><span data-stu-id="f1c03-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="f1c03-201">如果仍然無法運作，讓伺服器傳送更多的錨點，和用戶端的運作方式的其中一個同意使用網路通訊。</span><span class="sxs-lookup"><span data-stu-id="f1c03-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="f1c03-202">您可以試試看下載 HolographicSpatialAnchorTransferSample、 設定您的用戶端和伺服器 Ip，並將它部署至用戶端和伺服器的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="f1c03-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1c03-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1c03-203">See also</span></span>
* [<span data-ttu-id="f1c03-204">平行模式程式庫 (PPL)</span><span class="sxs-lookup"><span data-stu-id="f1c03-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="f1c03-205">Windows.Networking.StreamSocket</span><span class="sxs-lookup"><span data-stu-id="f1c03-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="f1c03-206">Windows.Networking.StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="f1c03-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
