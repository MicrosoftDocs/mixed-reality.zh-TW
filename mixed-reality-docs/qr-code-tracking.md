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
# <a name="qr-code-tracking"></a>QR 代碼追蹤

HoloLens 2 可以在耳機周圍偵測到 QR 代碼, 並在每個程式碼的真實世界位置建立座標系統。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> QR 代碼偵測</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">請參閱附注</td>
</tr>
</table>

>[!NOTE]
>下列 NuGet 套件目前不支援桌上型電腦上的沉浸式 Windows Mixed Reality 耳機。  隨時掌握有關桌面支援的進一步更新。

## <a name="getting-the-qr-package"></a>取得 QR 套件
您可以在[這裡](https://github.com/dorreneb/mixed-reality/releases)下載適用于 QR 代碼偵測的 NuGet 套件。

此套件的未來版本將可透過公用 NuGet 套件存放庫取得。

## <a name="detecting-qr-codes"></a>偵測 QR 代碼

### <a name="adding-the-webcam-capability"></a>加入網路攝影機功能
您必須將功能`webcam`新增至您的資訊清單, 以偵測 QR 代碼。 這項功能是必要的, 因為在使用者環境中偵測到的程式碼內的資料可能包含機密資訊。

呼叫`QRCodeWatcher.RequestAccessAsync()`來要求許可權:

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

在您建立 QRCodeWatcher 物件之前, 應該先要求許可權。

當 QR 代碼偵測需要此`webcam`功能時, 會使用裝置的追蹤攝影機進行偵測。 相較于使用裝置的相片/影片 (PV) 攝影機偵測, 這可提供更廣泛的偵測 FOV, 以及更好的電池壽命。

### <a name="detecting-qr-codes-in-unity"></a>在 Unity 中偵測 QR 代碼

您可以在 Unity 中使用 QR 代碼偵測 API, 而不需依賴 MRTK 的相依性。 若要這樣做, 您必須:

1. 在 unity 專案的 [資產] 資料夾中, 使用名稱*外掛程式*建立新的資料夾。
2. 將此資料夾中的所有必要檔案複製到您剛才建立的本機「外掛程式」資料夾中。

有一個範例 Unity 應用程式會顯示 QR 代碼的全像投影方塊, 以及相關聯的資料, 例如 GUID、實體大小、時間戳記和解碼的資料。 此應用程式可以位於 https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes 。

### <a name="detecting-qr-codes-in-c"></a>偵測中的 QR 代碼C++

>[!NOTE]
>本文C++中的程式碼片段目前示範如何使用C++/cx, 而不是 C + 17 相容C++的[ C++ ](creating-a-holographic-directx-project.md)/WinRT, 如全像攝影專案範本中所使用。 概念相當於C++/WinRT 專案, 但您必須轉譯程式碼。

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>取得 QR 代碼的座標系統

每個偵測到的 QR 代碼都會公開[空間座標系統](coordinate-systems.md), 並將其與左上方的 [快速偵測] 方塊左上角的 QR 代碼結合, 如下所示。  直接使用 QR SDK 時, Z 軸會指向紙張 (未顯示)-轉換成 Unity 座標時, Z 軸會指向紙張, 而且會被留下。

QR 代碼的 SpatialCoordinateSystem 會對齊顯示。 藉由呼叫<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a>並傳入程式碼的 SpatialGraphNodeId, 即可從平臺取得此座標系統。

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

針對 QRCode 物件, 下列C++/cx 程式碼示範如何建立矩形, 並使用 QR 代碼的座標系統來放置它:

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

您可以使用實體大小來建立 QR 矩形:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

座標系統可以用來繪製 QR 代碼, 或將全息影像附加至位置:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

您的*QRCodeWatcher:: QRCodeAddedHandler*可能會看起來像這樣:

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

## <a name="best-practices-for-qr-code-detection"></a>QR 代碼偵測的最佳做法

### <a name="quiet-zones-around-qr-codes"></a>QR 代碼周圍的安靜區域

若要正確讀取, QR 代碼需要程式碼兩側的邊界。 此邊界不能包含任何列印的內容, 而且應該是四個模組 (程式碼中的單一黑色正方形) 寬。 

[QR 規格](https://www.qrcode.com/en/howto/code.html)包含有關 quiet 區域的詳細資訊。

### <a name="lighting-and-backdrop"></a>光源和背景
QR 代碼偵測品質容易受到不同的照明和背景影響。 

在具有特別明亮光源的場景中, 列印灰色背景上為黑色的程式碼。 否則, 請將黑色 QR 代碼列印在白色背景上。

如果程式碼的背景特別深, 如果您的偵測速率很低, 請嘗試黑色的灰色程式碼。 如果背景相對淺, 一般程式碼應該會正常執行。

### <a name="size-of-qr-codes"></a>QR 代碼的大小
Windows Mixed Reality 裝置無法搭配每個邊緣小於 5 cm 的 QR 代碼使用。

對於介於5到 10 cm 長度的 QR 代碼, 您必須非常接近, 才能偵測程式碼。 這也需要更長的時間來偵測此大小的代碼。 

偵測程式碼的確切時間, 不僅取決於 QR 代碼的大小, 還會超出程式碼的距離。 接近程式碼的移動將有助於彌補大小的問題。

### <a name="distance-and-angular-position-from-the-qr-code"></a>QR 代碼的距離和角度位置
追蹤攝影機只能偵測特定層級的詳細資料。 對於真正的小型程式碼-< 10cm 沿著一邊, 您必須相當接近。 針對第1版的 QR 代碼, 從10個到25個 cm 寬, 最小偵測距離範圍從0.15 計量到0.5 計量。 

大小的偵測距離會以線性方式增加。 

QR 偵測適用于一系列的角度 + = 45deg。 這是為了確保我們有適當的解決方案來偵測程式碼。

### <a name="qr-codes-with-logos"></a>具有標誌的 QR 代碼
具有標誌的 QR 代碼尚未經過測試, 目前不受支援。

### <a name="managing-qr-code-data"></a>管理 QR 代碼資料
Windows Mixed Reality 裝置會偵測驅動程式中系統層級的 QR 代碼。 當裝置重新開機時, 偵測到的 QR 代碼將會消失, 並會在下一次重新偵測為新物件。

建議您將應用程式設定為略過早于特定時間戳記的 QR 代碼。 目前, API 不支援清除 QR 代碼歷程記錄。

### <a name="qr-code-placement-in-a-space"></a>QR 代碼在空間中的位置
如需有關如何放置 QR 代碼的建議, 請參閱[HoloLens 的環境考慮](environment-considerations-for-hololens.md)。

## <a name="qr-api-reference"></a>QR API 參考

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

## <a name="see-also"></a>另請參閱
* [座標系統](coordinate-systems.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>