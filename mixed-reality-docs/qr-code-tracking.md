---
title: QR 代碼追蹤
description: 瞭解如何開啟 Windows Mixed Reality 沉浸 (VR) 耳機的 QR 代碼追蹤, 並在您的 VR 應用程式中執行此功能。
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr, lbe, 以位置為基礎的娛樂, vr arcade, arcade, 沉浸, qr, qr 代碼
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829977"
---
# <a name="qr-code-tracking"></a>QR 代碼追蹤

QR 代碼追蹤會在適用于沉浸式 (VR) 耳機的 Windows Mixed Reality 驅動程式中執行。 藉由在耳機驅動程式中啟用 QR 代碼追蹤器, 頭戴式裝置會掃描 QR 代碼, 並回報給感興趣的應用程式。 這項功能僅適用于[Windows 10 2018 年10月更新 (也稱為 RS5)](release-notes-october-2018.md)。

>[!NOTE]
>本文中的程式碼片段目前示範如何使用C++/cx, C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT, 如全像攝影專案範本中所使用。  概念相當於C++/WinRT 專案, 但您必須轉譯程式碼。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>QR 代碼追蹤</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>啟用和停用頭戴式裝置的 QR 代碼追蹤
注意:本節僅適用于[Windows 10 2018 年10月更新 (也稱為 RS5)](release-notes-october-2018.md)。 從19h1 的組建開始, 您不需要這麼做。
無論您開發的是將利用 QR 代碼追蹤的混合現實應用程式, 或您是其中一個應用程式的客戶, 都必須在頭戴式裝置的驅動程式中手動開啟 QR 代碼追蹤。

若要開啟您的沉浸式 (VR) 耳機的**QR 代碼追蹤**:

1. 在您的電腦上關閉混合現實入口網站應用程式。
2. 從您的電腦拔下頭戴式裝置。
3. 在命令提示字元中執行下列腳本:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. 將您的耳機重新連接到您的電腦。

若要關閉沉浸式 (VR) 耳機的**QR 代碼追蹤**:

1. 在您的電腦上關閉混合現實入口網站應用程式。
2. 從您的電腦拔下頭戴式裝置。
3. 在命令提示字元中執行下列腳本:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. 將您的耳機重新連接到您的電腦。 這會使任何探索到的 QR 代碼「無法定位」。

## <a name="printing-codes"></a>列印代碼

首先最重要的是, [qr 代碼的規格](https://www.qrcode.com/en/howto/code.html)指出「qr 代碼符號區域需要使用邊界或「無訊息區域」。 邊界是符號周圍的清楚區域, 其中不會列印任何內容。 QR 代碼需要在符號的兩邊有四個全模組的寬邊界。」 這在每一端都必須有一個寬度, 也就是模組大小的四倍-程式碼中的單一黑色正方形。 [規格] 頁面包含如何列印 QR 代碼的建議, 並找出建立特定大小的 QR 代碼所需的區域。

目前, QR 代碼偵測品質很容易受到不同的照明和背景影響。 若要對抗此情況, 請記下您的照明, 並列印適當的程式碼。 在具有特別明亮光源的場景中, 列印灰色背景上為黑色的程式碼。 在低光線場景下, 黑色 on 白色作用。 同樣地, 如果程式碼的背景特別深, 如果您的偵測速率很低, 請嘗試黑色的灰色程式碼。 否則, 如果背景較淡, 一般程式碼應該會正常執行。

## <a name="qrtracking-api"></a>QRTracking API

QRTracking 外掛程式會公開適用于 QR 代碼追蹤的 Api。 若要使用外掛程式, 您必須使用*QRCodesTrackerPlugin*命名空間中的下列類型。

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a>在 Unity 中執行 QR 代碼追蹤

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>MRTK 中的範例 Unity 場景 (混合現實工具組)

您可以在混合現實工具組[GitHub 網站](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)中找到如何使用 QR 追蹤 API 的範例。

MRTK 已實作為 simpilify QR 追蹤使用方式所需的腳本。 開發 QR 追蹤應用程式所需的所有資產都位於 "QRTracker" 資料夾中。 有兩個場景: 第一個範例只會在偵測到 QR 代碼時顯示其詳細資料, 而第二個則示範如何使用附加至 QR 代碼的座標系統來顯示全息影像。
有一個 prefab 的「QRScanner」, 它會將所有必要的腳本新增至幕後, 以使用 QRCodes。 腳本 QRCodeManager 是單一類別, 可執行 QRCode API。 這必須新增至您的場景。 「AttachToQRCode」腳本是用來將全息影像附加到 QR 代碼座標系統, 此腳本可以新增至任何全息影像。 「SpatialGraphCoordinateSystem」會顯示如何使用 QRCode 座標系統。 這些腳本可以在您的專案場景中以相同的方式使用, 或者您可以直接使用此外掛程式來撰寫您自己的程式碼, 如上所述。

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>在 Unity 中以不 MRTK 的方式來執行 QR 代碼追蹤

您也可以在 Unity 中使用 QR 追蹤 API, 而不需依賴 MRTK 的相依性。 若要使用 API, 您必須使用下列指示來準備您的專案:

1. 在 unity 專案的 [資產] 資料夾中, 使用下列名稱建立新的資料夾:「外掛程式」。
2. 將[此資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)中的所有必要檔案複製到您剛才建立的本機「外掛程式」資料夾中。
3. 您可以使用 [ [MRTK 腳本] 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)中的 QR 追蹤腳本, 或自行撰寫。
注意:這些外掛程式僅適用于[Windows 10 2018 年10月更新 (也稱為 RS5)](release-notes-october-2018.md)組建。 外掛程式將會在下一個 windows 版本中更新。 目前的外掛程式是實驗性的, 在未來的 windows 版本中將無法使用。 新的外掛程式將會發佈, 可從下一個 windows 版本中使用, 而且不會回溯相容, 也無法搭配 RS5 使用。

## <a name="implementing-qr-code-tracking-in-directx"></a>在 DirectX 中執行 QR 代碼追蹤

若要在 Visual Studio 中使用 QRTrackingPlugin, 您必須將 QRTrackingPlugin 的參考加入至 winmd。 您可以在[這裡找到支援的平臺所需](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)的檔案。

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a>取得座標系統

我們會定義右座標系統, 並將其與左上角 [快速偵測] 方塊左上方的 QR 代碼對齊。 座標系統如下所示。 Z 軸指向紙張 (未顯示), 但是在 Unity 中, Z 軸不在紙張中, 而是左手頁。

定義的 SpatialCoordinateSystem 會依照所示對齊。 您可以使用 API *Windows::P erception:: 空間::P 審查:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*, 從平臺取得此座標系統。

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

在 QRCode ^ Code 物件中, 下列程式碼會示範如何建立矩形, 並將它放在 QR 座標系統中:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

您可以使用實體大小來建立 QR 矩形:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

座標系統可以用來繪製 QR 代碼, 或將全息影像附加至位置:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

您的*QRCodesTrackerPlugin:: QRCodeAddedHandler*可能會看起來像這樣:

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
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

## <a name="troubleshooting-and-faq"></a>疑難排解和常見問題

**一般疑難排解**

* 您的電腦是否正在執行 Windows 10 2018 年10月更新？
* 您是否已設定 reg 金鑰？ 之後重新開機裝置嗎？
* QR 代碼版本是否為支援的版本？ 目前的 API 最多支援 QR 代碼版本20。 我們建議使用第5版來進行一般使用。 
* 您夠接近 QR 代碼嗎？ 相機愈接近 QR 代碼, API 可支援的 QR 代碼版本愈高。  

**我需要什麼時間才能偵測到 QR 代碼？**

這將取決於 QR 代碼的大小, 以及它的版本。 針對第1版的 QR 代碼, 從 5 cm 端到 25 cm 端, 最小偵測距離的範圍是從0.15 計量到0.5 計量。 從大約0.3 計量中, 可以偵測到最遠的, 以較大的 QR 代碼目標為1.4 計量。 對於大於此值的 QR 代碼, 您可以進行評估;大小的偵測距離會以線性方式增加。 我們的追蹤程式無法處理具有小於 5 cm 的 QR 代碼。

**具有標誌的 QR 代碼是否有效？**

具有標誌的 QR 代碼尚未經過測試, 目前不受支援。

**如何? 從我的應用程式中清除 QR 代碼, 使其不會保存？**

* QR 代碼只會保存在開機會話中。 一旦您重新開機 (或重新開機驅動程式), 它們就會消失, 並在下次偵測為新物件。
* QR 代碼歷程記錄會儲存在驅動程式會話的系統層級, 但是您可以設定應用程式, 略過超過特定時間戳記的 QR 代碼 (如有需要)。 目前, API 支援清除 QR 代碼歷程記錄, 因為多個應用程式可能會對資料感興趣。

**RS5 和未來版本的外掛程式不會相容**RS5 版本的外掛程式僅適用于 RS5, 且在未來版本中將無法運作。 Expermental 外掛程式會以 real 外掛程式取代, 而且應該是我們可以在未來版本的 windows 中使用的外掛程式。
