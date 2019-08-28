---
title: QR 代碼追蹤
description: 瞭解如何偵測 HoloLens 2 上的 QR 代碼。
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: vr, lbe, 以位置為基礎的娛樂, vr arcade, arcade, 沉浸, qr, qr 代碼, hololens2
ms.openlocfilehash: 736ab265db2145dd784c435e525059ed3a2fcbbb
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047161"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="37324-104">QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="37324-104">QR code tracking</span></span>

<span data-ttu-id="37324-105">HoloLens 2 可以在耳機周圍偵測到 QR 代碼, 並在每個程式碼的真實世界位置建立座標系統。</span><span class="sxs-lookup"><span data-stu-id="37324-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="37324-106">裝置支援</span><span class="sxs-lookup"><span data-stu-id="37324-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="37324-107">功能</span><span class="sxs-lookup"><span data-stu-id="37324-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="37324-108"><a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></span><span class="sxs-lookup"><span data-stu-id="37324-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="37324-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="37324-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="37324-110"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="37324-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="37324-111">QR 代碼偵測</span><span class="sxs-lookup"><span data-stu-id="37324-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="37324-112">️</span><span class="sxs-lookup"><span data-stu-id="37324-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="37324-113">✔️</span><span class="sxs-lookup"><span data-stu-id="37324-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="37324-114">請參閱附注</span><span class="sxs-lookup"><span data-stu-id="37324-114">See note</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="37324-115">下列 NuGet 套件目前不支援桌上型電腦上的沉浸式 Windows Mixed Reality 耳機。</span><span class="sxs-lookup"><span data-stu-id="37324-115">Support for immersive Windows Mixed Reality headsets on desktop PCs is not currently supported with the NuGet package below.</span></span>  <span data-ttu-id="37324-116">隨時掌握有關桌面支援的進一步更新。</span><span class="sxs-lookup"><span data-stu-id="37324-116">Stay tuned for further updates on desktop support.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="37324-117">取得 QR 套件</span><span class="sxs-lookup"><span data-stu-id="37324-117">Getting the QR package</span></span>
<span data-ttu-id="37324-118">您可以在[這裡](https://github.com/dorreneb/mixed-reality/releases)下載適用于 QR 代碼偵測的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="37324-118">You can download a NuGet package for QR code detection [here](https://github.com/dorreneb/mixed-reality/releases).</span></span>

<span data-ttu-id="37324-119">此套件的未來版本將可透過公用 NuGet 套件存放庫取得。</span><span class="sxs-lookup"><span data-stu-id="37324-119">Future versions of this package will be available through the public NuGet package repository.</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="37324-120">偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="37324-120">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="37324-121">加入網路攝影機功能</span><span class="sxs-lookup"><span data-stu-id="37324-121">Adding the webcam capability</span></span>
<span data-ttu-id="37324-122">您必須將功能`webcam`新增至您的資訊清單, 以偵測 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="37324-122">You will need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="37324-123">這項功能是必要的, 因為在使用者環境中偵測到的程式碼內的資料可能包含機密資訊。</span><span class="sxs-lookup"><span data-stu-id="37324-123">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="37324-124">呼叫`QRCodeWatcher.RequestAccessAsync()`來要求許可權:</span><span class="sxs-lookup"><span data-stu-id="37324-124">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="37324-125">_C#:_</span><span class="sxs-lookup"><span data-stu-id="37324-125">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="37324-126">_C++:_</span><span class="sxs-lookup"><span data-stu-id="37324-126">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="37324-127">在您建立 QRCodeWatcher 物件之前, 應該先要求許可權。</span><span class="sxs-lookup"><span data-stu-id="37324-127">Permission should be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="37324-128">當 QR 代碼偵測需要此`webcam`功能時, 會使用裝置的追蹤攝影機進行偵測。</span><span class="sxs-lookup"><span data-stu-id="37324-128">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="37324-129">相較于使用裝置的相片/影片 (PV) 攝影機偵測, 這可提供更廣泛的偵測 FOV, 以及更好的電池壽命。</span><span class="sxs-lookup"><span data-stu-id="37324-129">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="37324-130">在 Unity 中偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="37324-130">Detecting QR codes in Unity</span></span>

<span data-ttu-id="37324-131">您可以在 Unity 中使用 QR 代碼偵測 API, 而不需依賴 MRTK 的相依性。</span><span class="sxs-lookup"><span data-stu-id="37324-131">You can use the QR code detection API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="37324-132">若要這樣做, 您必須:</span><span class="sxs-lookup"><span data-stu-id="37324-132">To do so, you must:</span></span>

1. <span data-ttu-id="37324-133">在 unity 專案的 [資產] 資料夾中, 使用名稱*外掛程式*建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="37324-133">Create a new folder in the assets folder of your unity project with the name *Plugins*.</span></span>
2. <span data-ttu-id="37324-134">將此資料夾中的所有必要檔案複製到您剛才建立的本機「外掛程式」資料夾中。</span><span class="sxs-lookup"><span data-stu-id="37324-134">Copy all the required files from this folder into the local "Plugins" folder you just created.</span></span>

<span data-ttu-id="37324-135">有一個範例 Unity 應用程式會顯示 QR 代碼的全像投影方塊, 以及相關聯的資料, 例如 GUID、實體大小、時間戳記和解碼的資料。</span><span class="sxs-lookup"><span data-stu-id="37324-135">There is a sample Unity app that displays a holographic square over QR codes, along with the associated data such as GUID, physical size, timestamp, and decoded data.</span></span> <span data-ttu-id="37324-136">此應用程式可以位於 https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes 。</span><span class="sxs-lookup"><span data-stu-id="37324-136">This app can be located at https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="37324-137">偵測中的 QR 代碼C++</span><span class="sxs-lookup"><span data-stu-id="37324-137">Detecting QR codes in C++</span></span>

>[!NOTE]
><span data-ttu-id="37324-138">本文C++中的程式碼片段目前示範如何使用C++/cx, 而不是 C + 17 相容C++的[ C++ ](creating-a-holographic-directx-project.md)/WinRT, 如全像攝影專案範本中所使用。</span><span class="sxs-lookup"><span data-stu-id="37324-138">The C++ code snippets in this article currently demonstrate the use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="37324-139">概念相當於C++/WinRT 專案, 但您必須轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="37324-139">The concepts are equivalent for a C++/WinRT project, though you need to translate the code.</span></span>

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="37324-140">取得 QR 代碼的座標系統</span><span class="sxs-lookup"><span data-stu-id="37324-140">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="37324-141">每個偵測到的 QR 代碼都會公開[空間座標系統](coordinate-systems.md), 並將其與左上方的 [快速偵測] 方塊左上角的 QR 代碼結合, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="37324-141">Each detected QR code exposes a [spatial coordinate system](coordinate-systems.md) aligned with the QR code at the top left corner of the fast detection square in the top left as seen below.</span></span>  <span data-ttu-id="37324-142">直接使用 QR SDK 時, Z 軸會指向紙張 (未顯示)-轉換成 Unity 座標時, Z 軸會指向紙張, 而且會被留下。</span><span class="sxs-lookup"><span data-stu-id="37324-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="37324-143">QR 代碼的 SpatialCoordinateSystem 會對齊顯示。</span><span class="sxs-lookup"><span data-stu-id="37324-143">A QR code's SpatialCoordinateSystem aligns shown.</span></span> <span data-ttu-id="37324-144">藉由呼叫<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a>並傳入程式碼的 SpatialGraphNodeId, 即可從平臺取得此座標系統。</span><span class="sxs-lookup"><span data-stu-id="37324-144">This coordinate system can be obtained from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

<span data-ttu-id="37324-146">針對 QRCode 物件, 下列C++/cx 程式碼示範如何建立矩形, 並使用 QR 代碼的座標系統來放置它:</span><span class="sxs-lookup"><span data-stu-id="37324-146">For a QRCode object, the following C++/CX code shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="37324-147">您可以使用實體大小來建立 QR 矩形:</span><span class="sxs-lookup"><span data-stu-id="37324-147">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="37324-148">座標系統可以用來繪製 QR 代碼, 或將全息影像附加至位置:</span><span class="sxs-lookup"><span data-stu-id="37324-148">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

<span data-ttu-id="37324-149">您的*QRCodeWatcher:: QRCodeAddedHandler*可能會看起來像這樣:</span><span class="sxs-lookup"><span data-stu-id="37324-149">Altogether, your *QRCodeWatcher::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="37324-150">QR 代碼偵測的最佳做法</span><span class="sxs-lookup"><span data-stu-id="37324-150">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="37324-151">QR 代碼周圍的安靜區域</span><span class="sxs-lookup"><span data-stu-id="37324-151">Quiet zones around QR Codes</span></span>

<span data-ttu-id="37324-152">若要正確讀取, QR 代碼需要程式碼兩側的邊界。</span><span class="sxs-lookup"><span data-stu-id="37324-152">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="37324-153">此邊界不能包含任何列印的內容, 而且應該是四個模組 (程式碼中的單一黑色正方形) 寬。</span><span class="sxs-lookup"><span data-stu-id="37324-153">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="37324-154">[QR 規格](https://www.qrcode.com/en/howto/code.html)包含有關 quiet 區域的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="37324-154">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="37324-155">光源和背景</span><span class="sxs-lookup"><span data-stu-id="37324-155">Lighting and backdrop</span></span>
<span data-ttu-id="37324-156">QR 代碼偵測品質容易受到不同的照明和背景影響。</span><span class="sxs-lookup"><span data-stu-id="37324-156">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="37324-157">在具有特別明亮光源的場景中, 列印灰色背景上為黑色的程式碼。</span><span class="sxs-lookup"><span data-stu-id="37324-157">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="37324-158">否則, 請將黑色 QR 代碼列印在白色背景上。</span><span class="sxs-lookup"><span data-stu-id="37324-158">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="37324-159">如果程式碼的背景特別深, 如果您的偵測速率很低, 請嘗試黑色的灰色程式碼。</span><span class="sxs-lookup"><span data-stu-id="37324-159">If the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="37324-160">如果背景相對淺, 一般程式碼應該會正常執行。</span><span class="sxs-lookup"><span data-stu-id="37324-160">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="37324-161">QR 代碼的大小</span><span class="sxs-lookup"><span data-stu-id="37324-161">Size of QR codes</span></span>
<span data-ttu-id="37324-162">Windows Mixed Reality 裝置無法搭配每個邊緣小於 5 cm 的 QR 代碼使用。</span><span class="sxs-lookup"><span data-stu-id="37324-162">Windows Mixed Reality devices do not work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="37324-163">對於介於5到 10 cm 長度的 QR 代碼, 您必須非常接近, 才能偵測程式碼。</span><span class="sxs-lookup"><span data-stu-id="37324-163">For QR codes between 5 and 10 cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="37324-164">這也需要更長的時間來偵測此大小的代碼。</span><span class="sxs-lookup"><span data-stu-id="37324-164">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="37324-165">偵測程式碼的確切時間, 不僅取決於 QR 代碼的大小, 還會超出程式碼的距離。</span><span class="sxs-lookup"><span data-stu-id="37324-165">The exact time to detect codes depends not only on the size of the QR codes, but how far you are away from the code.</span></span> <span data-ttu-id="37324-166">接近程式碼的移動將有助於彌補大小的問題。</span><span class="sxs-lookup"><span data-stu-id="37324-166">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="37324-167">QR 代碼的距離和角度位置</span><span class="sxs-lookup"><span data-stu-id="37324-167">Distance and angular position from the QR code</span></span>
<span data-ttu-id="37324-168">追蹤攝影機只能偵測特定層級的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="37324-168">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="37324-169">對於真正的小型程式碼-< 10cm 沿著一邊, 您必須相當接近。</span><span class="sxs-lookup"><span data-stu-id="37324-169">For really small codes - < 10cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="37324-170">針對第1版的 QR 代碼, 從10個到25個 cm 寬, 最小偵測距離範圍從0.15 計量到0.5 計量。</span><span class="sxs-lookup"><span data-stu-id="37324-170">For a version 1 QR code varying from 10 to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="37324-171">大小的偵測距離會以線性方式增加。</span><span class="sxs-lookup"><span data-stu-id="37324-171">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="37324-172">QR 偵測適用于一系列的角度 + = 45deg。</span><span class="sxs-lookup"><span data-stu-id="37324-172">QR detection works with a range of angles += 45deg.</span></span> <span data-ttu-id="37324-173">這是為了確保我們有適當的解決方案來偵測程式碼。</span><span class="sxs-lookup"><span data-stu-id="37324-173">This is to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="37324-174">具有標誌的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="37324-174">QR codes with logos</span></span>
<span data-ttu-id="37324-175">具有標誌的 QR 代碼尚未經過測試, 目前不受支援。</span><span class="sxs-lookup"><span data-stu-id="37324-175">QR codes with logos have not been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="37324-176">管理 QR 代碼資料</span><span class="sxs-lookup"><span data-stu-id="37324-176">Managing QR code data</span></span>
<span data-ttu-id="37324-177">Windows Mixed Reality 裝置會偵測驅動程式中系統層級的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="37324-177">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="37324-178">當裝置重新開機時, 偵測到的 QR 代碼將會消失, 並會在下一次重新偵測為新物件。</span><span class="sxs-lookup"><span data-stu-id="37324-178">When the device is rebooted, the detected QR codes are gone and will be re-detected as new objects next time.</span></span>

<span data-ttu-id="37324-179">建議您將應用程式設定為略過早于特定時間戳記的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="37324-179">It is recommended to configure your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="37324-180">目前, API 不支援清除 QR 代碼歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="37324-180">Currently, the API does not support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="37324-181">QR 代碼在空間中的位置</span><span class="sxs-lookup"><span data-stu-id="37324-181">QR code placement in a space</span></span>
<span data-ttu-id="37324-182">如需有關如何放置 QR 代碼的建議, 請參閱[HoloLens 的環境考慮](environment-considerations-for-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="37324-182">For recommendations on where and how to place QR codes, please refer to [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="37324-183">QR API 參考</span><span class="sxs-lookup"><span data-stu-id="37324-183">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum VersionInfo
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="37324-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37324-184">See also</span></span>
* [<span data-ttu-id="37324-185">座標系統</span><span class="sxs-lookup"><span data-stu-id="37324-185">Coordinate systems</span></span>](coordinate-systems.md)
* <span data-ttu-id="37324-186"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="37324-186"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>