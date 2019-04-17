---
title: 追蹤的 QR 代碼
description: 了解如何開啟追蹤您的 Windows Mixed Reality 沈浸式 (VR) 耳機的 QR 代碼，並在 VR 應用程式中實作的功能。
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr lbe，位置為基礎的娛樂、 vr arcade arcade，沉浸式 qr，qr 代碼
ms.openlocfilehash: b0f4480496c15f811979f76143acbd456d89e249
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597131"
---
# <a name="qr-code-tracking"></a>追蹤的 QR 代碼

沈浸式 (VR) 耳機的 Windows Mixed Reality 驅動程式中實作追蹤的 QR 代碼。 藉由啟用 QR 程式碼追蹤程式耳機驅動程式中的，耳機掃描 QR 代碼並回報給想要的應用程式。 這項功能才可使用的[Windows 10 年 10 月 2018 Update (也稱為 RS5)](release-notes-october-2018.md)。

>[!NOTE]
>目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。  概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> 追蹤的 QR 代碼</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>啟用和停用 QR 程式碼耳機的追蹤
注意：本節僅適用於[Windows 10 年 10 月 2018 Update (也稱為 RS5)](release-notes-october-2018.md)。 從 19 h 1 組建及更新版本，您將不不必執行這項操作。
不論您正在開發的混合的實境應用程式，將會利用追蹤的 QR 代碼，或您是客戶的其中一個應用程式，您必須以手動方式啟動追蹤耳機的驅動程式中的 QR 代碼。

若要**開啟 追蹤的 QR 代碼**的沈浸式 (VR) 耳機：

1. 關閉您的電腦上的混合的實境入口網站應用程式。
2. 請拔除耳機，從您的電腦。
3. 在命令提示字元執行下列指令碼：<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. 重新連線到您的 PC 耳機。

若要**關閉 QR 代碼追蹤**的沈浸式 (VR) 耳機：

1. 關閉您的電腦上的混合的實境入口網站應用程式。
2. 請拔除耳機，從您的電腦。
3. 在命令提示字元執行下列指令碼：<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. 重新連線到您的 PC 耳機。 這會讓任何探索到的 QR 代碼 「 非-之外的可尋獲。 」

## <a name="printing-codes"></a>列印代碼

首先[規格的 QR 代碼](https://www.qrcode.com/en/howto/code.html)指出 「 QR 代碼符號區域需要的邊界或 「 無訊息區 」 周圍可使用它。 邊界是不會在此對話方塊列印的清除區域周圍的符號。 QR 代碼需要四個模組寬的邊界，在符號的所有側邊。 」 這需要對每一側，模組-程式碼中的單一黑色方塊的大小四倍的寬度。 [Spec] 頁面包含如何列印 QR 代碼，並找出特定大小的 QR 代碼所需的區域大小的建議。

目前 QR 程式碼偵測品質很容易變動的照明和底圖的。 若要避免此問題，請注意您照明和列印適當的程式碼。 在已加上特別光明的光源的場景，列印黑色灰色背景上的程式碼。 在低亮度場景，黑色白色運作。 同樣地，如果特別深的程式碼的背景，嘗試灰色的程式碼為黑色，如果您偵測率很低。 否則，如果淺色背景，一般的程式碼應該就夠用。

## <a name="qrtracking-api"></a>QRTracking API

QRTracking 外掛程式會公開的 Api 可讓追蹤的 QR 代碼。 若要使用外掛程式，您必須使用下列類型從*QRCodesTrackerPlugin*命名空間。

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

## <a name="implementing-qr-code-tracking-in-unity"></a>實作追蹤 Unity 中的 QR 代碼

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>範例 MRTK （混合實境工具組） 中的 Unity 場景

您可以找到如何使用混合實境工具組中的 QR 追蹤 API 範例[GitHub 網站](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)。

MRTK 已實作所需的指令碼，以 simpilify QR 追蹤使用方式。 所有所需的資產來開發 QR 追蹤應用程式位於 「 QRTracker"資料夾。 有兩個場景： 第一個是只會偵測到，以及第二個示範如何使用附加至 QR 代碼座標系統，以顯示 全像投影顯示 QR 代碼的詳細資料的範例。
沒有 prefab"QRScanner 」 來使用 QRCodes 加入所有必要的 scrips。 指令碼 QRCodeManager 是 singileton 類別會實作 QRCode API，您可以將它新增至您的場景。 指令碼 」 AttachToQRCode 」 用來附加全像投影的 QR 代碼 coodridnate 系統，此指令碼可以新增至任何您全像投影。 「 SpatialGraphCoordinateSystem"會示範如何使用 QRCode 座標系統。 可以使用這些指令碼，因為您的專案場景中，或您可以撰寫您自己直接使用外掛程式上面所述。

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>實作追蹤沒有 MRTK Unity 中的 QR 代碼

您也可以在 Unity 中使用 QR 追蹤 API，而不需要仰賴 MRTK。 若要使用的 API，您必須準備您的專案，使用下列指示：

1. 在您的 unity 專案名稱的 [assets] 資料夾中建立新的資料夾：「 外掛程式 」。
2. 從所有必要的檔案複製[此資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)您剛才建立的本機 「 外掛程式 」 資料夾。
3. 您可以使用追蹤的指令碼中的 QR [MRTK 指令碼 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)或自行撰寫。
注意：這些外掛程式會僅適用於[Windows 10 年 10 月 2018 Update (也稱為 RS5)](release-notes-october-2018.md)組建。 下一步 的 windows 版本中，將會更新外掛程式。 目前外掛程式實驗，並不適用於 windows 的未來版本。 新的外掛程式將會發行可從下一個 windows 版本並不會回溯相容及不適用於 RS5）。

## <a name="implementing-qr-code-tracking-in-directx"></a>實作追蹤 DirectX 中的 QR 代碼

若要使用 QRTrackingPlugin Visual Studio 中，您必須將 QRTrackingPlugin 的參考新增至.winmd。 您可以找到[所需的檔案支援的平台這裡](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)。

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

我們會定義右的座標系統，配合在左上角位於左上方的快速偵測正方形的 QR 代碼。 如下所示的座標系統。 Z 軸指向納入文件 （未顯示），但在 Unity z 軸和慣用左手紙張用完。

定義 SpatialCoordinateSystem 靠所示。 您可以從使用 API 的平台取得此座標系統*Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*。

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

從 QRCode ^ 物件程式碼，下列程式碼示範如何建立矩形，並將它放在 QR 座標系統：

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

您可以使用的實體大小，以建立 QR 矩形：

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

座標系統可以用來繪製 QR 代碼，或附加全像投影至的位置中：

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

總之，您*QRCodesTrackerPlugin::QRCodeAddedHandler*可能看起來像這樣：

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

## <a name="troubleshooting-and-faq"></a>疑難排解和常見問題集

**一般疑難排解**

* 為您的電腦執行 Windows 10 年 10 月 2018年更新嗎？
* 您已設定登錄機碼？ 之後重新啟動裝置嗎？
* 是 QR 程式碼版本支援的版本嗎？ 目前的 API 支援最多 QR 程式碼版本 20 個。 我們建議使用一般用途的第 5 版。 
* 為您關閉 QR 代碼足以嗎？ 越接近相機 QR 代碼，可支援更高的 QR 程式碼版本的 API。  

**我要如何關閉 QR 代碼，來偵測它是？**

這將取決於大小的 QR 代碼，而且也哪一個版本。 第 1 版 QR 代碼，範圍從 5 cm 側邊到 25 公分側邊，最小偵測距離範圍 0.15 公尺至 0.5 的計量。 最遠了這些可以偵測到從會從較小的 QR 代碼目標大約 0.3 公尺至愈大 1.4 計量。 大於的 QR 代碼，您可以評估;偵測距離大小呈線性增加。 我們追蹤程式不適用於具有邊的 QR 代碼小於 5 cm。

**請勿使用標誌工作的 QR 代碼？**

具有標誌的 QR 代碼尚未經過測試，以及目前不支援。

**如何清除 QR 代碼從我的應用程式讓它們不會保存？**

* QR 代碼，才會保存在開機工作階段中。 一旦重新啟動 （或重新啟動的驅動程式），它們會進入並偵測為新物件下一次。
* QR 程式碼歷程記錄時，會儲存在系統層級上，在驅動程式工作階段中，但您可以設定您的應用程式，如果您想要忽略超過特定的時間戳記的 QR 代碼。 目前 API 並支援清除 QR 程式碼歷程記錄，因為多個應用程式可能感興趣的資料。

**外掛程式 RS5 和未來的版本不相容**RS5 新版的外掛程式只適用於的 RS5，未來版本將無法運作。 Expermental 外掛程式將會取代為實際的外掛程式，並應該是，我們可以使用在未來的 windows 版本。
