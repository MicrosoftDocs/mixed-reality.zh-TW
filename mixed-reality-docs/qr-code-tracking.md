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
# <a name="qr-code-tracking"></a><span data-ttu-id="4edd6-104">QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="4edd6-104">QR code tracking</span></span>

<span data-ttu-id="4edd6-105">QR 代碼追蹤會在適用于沉浸式 (VR) 耳機的 Windows Mixed Reality 驅動程式中執行。</span><span class="sxs-lookup"><span data-stu-id="4edd6-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="4edd6-106">藉由在耳機驅動程式中啟用 QR 代碼追蹤器, 頭戴式裝置會掃描 QR 代碼, 並回報給感興趣的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4edd6-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="4edd6-107">這項功能僅適用于[Windows 10 2018 年10月更新 (也稱為 RS5)](release-notes-october-2018.md)。</span><span class="sxs-lookup"><span data-stu-id="4edd6-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="4edd6-108">本文中的程式碼片段目前示範如何使用C++/cx, C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT, 如全像攝影專案範本中所使用。</span><span class="sxs-lookup"><span data-stu-id="4edd6-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="4edd6-109">概念相當於C++/WinRT 專案, 但您必須轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="4edd6-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="4edd6-110">裝置支援</span><span class="sxs-lookup"><span data-stu-id="4edd6-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4edd6-111"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="4edd6-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="4edd6-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4edd6-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4edd6-113"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="4edd6-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4edd6-114">QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="4edd6-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="4edd6-115">❌</span><span class="sxs-lookup"><span data-stu-id="4edd6-115">❌</span></span></td>
        <td><span data-ttu-id="4edd6-116">✔️</span><span class="sxs-lookup"><span data-stu-id="4edd6-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="4edd6-117">啟用和停用頭戴式裝置的 QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="4edd6-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="4edd6-118">注意:本節僅適用于[Windows 10 2018 年10月更新 (也稱為 RS5)](release-notes-october-2018.md)。</span><span class="sxs-lookup"><span data-stu-id="4edd6-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="4edd6-119">從19h1 的組建開始, 您不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="4edd6-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="4edd6-120">無論您開發的是將利用 QR 代碼追蹤的混合現實應用程式, 或您是其中一個應用程式的客戶, 都必須在頭戴式裝置的驅動程式中手動開啟 QR 代碼追蹤。</span><span class="sxs-lookup"><span data-stu-id="4edd6-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="4edd6-121">若要開啟您的沉浸式 (VR) 耳機的**QR 代碼追蹤**:</span><span class="sxs-lookup"><span data-stu-id="4edd6-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="4edd6-122">在您的電腦上關閉混合現實入口網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="4edd6-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="4edd6-123">從您的電腦拔下頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="4edd6-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="4edd6-124">在命令提示字元中執行下列腳本:</span><span class="sxs-lookup"><span data-stu-id="4edd6-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="4edd6-125">將您的耳機重新連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="4edd6-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="4edd6-126">若要關閉沉浸式 (VR) 耳機的**QR 代碼追蹤**:</span><span class="sxs-lookup"><span data-stu-id="4edd6-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="4edd6-127">在您的電腦上關閉混合現實入口網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="4edd6-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="4edd6-128">從您的電腦拔下頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="4edd6-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="4edd6-129">在命令提示字元中執行下列腳本:</span><span class="sxs-lookup"><span data-stu-id="4edd6-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="4edd6-130">將您的耳機重新連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="4edd6-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="4edd6-131">這會使任何探索到的 QR 代碼「無法定位」。</span><span class="sxs-lookup"><span data-stu-id="4edd6-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="4edd6-132">列印代碼</span><span class="sxs-lookup"><span data-stu-id="4edd6-132">Printing codes</span></span>

<span data-ttu-id="4edd6-133">首先最重要的是, [qr 代碼的規格](https://www.qrcode.com/en/howto/code.html)指出「qr 代碼符號區域需要使用邊界或「無訊息區域」。</span><span class="sxs-lookup"><span data-stu-id="4edd6-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="4edd6-134">邊界是符號周圍的清楚區域, 其中不會列印任何內容。</span><span class="sxs-lookup"><span data-stu-id="4edd6-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="4edd6-135">QR 代碼需要在符號的兩邊有四個全模組的寬邊界。」</span><span class="sxs-lookup"><span data-stu-id="4edd6-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="4edd6-136">這在每一端都必須有一個寬度, 也就是模組大小的四倍-程式碼中的單一黑色正方形。</span><span class="sxs-lookup"><span data-stu-id="4edd6-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="4edd6-137">[規格] 頁面包含如何列印 QR 代碼的建議, 並找出建立特定大小的 QR 代碼所需的區域。</span><span class="sxs-lookup"><span data-stu-id="4edd6-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="4edd6-138">目前, QR 代碼偵測品質很容易受到不同的照明和背景影響。</span><span class="sxs-lookup"><span data-stu-id="4edd6-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="4edd6-139">若要對抗此情況, 請記下您的照明, 並列印適當的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4edd6-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="4edd6-140">在具有特別明亮光源的場景中, 列印灰色背景上為黑色的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4edd6-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="4edd6-141">在低光線場景下, 黑色 on 白色作用。</span><span class="sxs-lookup"><span data-stu-id="4edd6-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="4edd6-142">同樣地, 如果程式碼的背景特別深, 如果您的偵測速率很低, 請嘗試黑色的灰色程式碼。</span><span class="sxs-lookup"><span data-stu-id="4edd6-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="4edd6-143">否則, 如果背景較淡, 一般程式碼應該會正常執行。</span><span class="sxs-lookup"><span data-stu-id="4edd6-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="4edd6-144">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="4edd6-144">QRTracking API</span></span>

<span data-ttu-id="4edd6-145">QRTracking 外掛程式會公開適用于 QR 代碼追蹤的 Api。</span><span class="sxs-lookup"><span data-stu-id="4edd6-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="4edd6-146">若要使用外掛程式, 您必須使用*QRCodesTrackerPlugin*命名空間中的下列類型。</span><span class="sxs-lookup"><span data-stu-id="4edd6-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="4edd6-147">在 Unity 中執行 QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="4edd6-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="4edd6-148">MRTK 中的範例 Unity 場景 (混合現實工具組)</span><span class="sxs-lookup"><span data-stu-id="4edd6-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="4edd6-149">您可以在混合現實工具組[GitHub 網站](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)中找到如何使用 QR 追蹤 API 的範例。</span><span class="sxs-lookup"><span data-stu-id="4edd6-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="4edd6-150">MRTK 已實作為 simpilify QR 追蹤使用方式所需的腳本。</span><span class="sxs-lookup"><span data-stu-id="4edd6-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="4edd6-151">開發 QR 追蹤應用程式所需的所有資產都位於 "QRTracker" 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4edd6-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="4edd6-152">有兩個場景: 第一個範例只會在偵測到 QR 代碼時顯示其詳細資料, 而第二個則示範如何使用附加至 QR 代碼的座標系統來顯示全息影像。</span><span class="sxs-lookup"><span data-stu-id="4edd6-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="4edd6-153">有一個 prefab 的「QRScanner」, 它會將所有必要的腳本新增至幕後, 以使用 QRCodes。</span><span class="sxs-lookup"><span data-stu-id="4edd6-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="4edd6-154">腳本 QRCodeManager 是單一類別, 可執行 QRCode API。</span><span class="sxs-lookup"><span data-stu-id="4edd6-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="4edd6-155">這必須新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="4edd6-155">This needs to be added to your scene.</span></span> <span data-ttu-id="4edd6-156">「AttachToQRCode」腳本是用來將全息影像附加到 QR 代碼座標系統, 此腳本可以新增至任何全息影像。</span><span class="sxs-lookup"><span data-stu-id="4edd6-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="4edd6-157">「SpatialGraphCoordinateSystem」會顯示如何使用 QRCode 座標系統。</span><span class="sxs-lookup"><span data-stu-id="4edd6-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="4edd6-158">這些腳本可以在您的專案場景中以相同的方式使用, 或者您可以直接使用此外掛程式來撰寫您自己的程式碼, 如上所述。</span><span class="sxs-lookup"><span data-stu-id="4edd6-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="4edd6-159">在 Unity 中以不 MRTK 的方式來執行 QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="4edd6-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="4edd6-160">您也可以在 Unity 中使用 QR 追蹤 API, 而不需依賴 MRTK 的相依性。</span><span class="sxs-lookup"><span data-stu-id="4edd6-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="4edd6-161">若要使用 API, 您必須使用下列指示來準備您的專案:</span><span class="sxs-lookup"><span data-stu-id="4edd6-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="4edd6-162">在 unity 專案的 [資產] 資料夾中, 使用下列名稱建立新的資料夾:「外掛程式」。</span><span class="sxs-lookup"><span data-stu-id="4edd6-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="4edd6-163">將[此資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)中的所有必要檔案複製到您剛才建立的本機「外掛程式」資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4edd6-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="4edd6-164">您可以使用 [ [MRTK 腳本] 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)中的 QR 追蹤腳本, 或自行撰寫。</span><span class="sxs-lookup"><span data-stu-id="4edd6-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="4edd6-165">注意:這些外掛程式僅適用于[Windows 10 2018 年10月更新 (也稱為 RS5)](release-notes-october-2018.md)組建。</span><span class="sxs-lookup"><span data-stu-id="4edd6-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="4edd6-166">外掛程式將會在下一個 windows 版本中更新。</span><span class="sxs-lookup"><span data-stu-id="4edd6-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="4edd6-167">目前的外掛程式是實驗性的, 在未來的 windows 版本中將無法使用。</span><span class="sxs-lookup"><span data-stu-id="4edd6-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="4edd6-168">新的外掛程式將會發佈, 可從下一個 windows 版本中使用, 而且不會回溯相容, 也無法搭配 RS5 使用。</span><span class="sxs-lookup"><span data-stu-id="4edd6-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="4edd6-169">在 DirectX 中執行 QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="4edd6-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="4edd6-170">若要在 Visual Studio 中使用 QRTrackingPlugin, 您必須將 QRTrackingPlugin 的參考加入至 winmd。</span><span class="sxs-lookup"><span data-stu-id="4edd6-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="4edd6-171">您可以在[這裡找到支援的平臺所需](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)的檔案。</span><span class="sxs-lookup"><span data-stu-id="4edd6-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="4edd6-172">取得座標系統</span><span class="sxs-lookup"><span data-stu-id="4edd6-172">Getting a coordinate system</span></span>

<span data-ttu-id="4edd6-173">我們會定義右座標系統, 並將其與左上角 [快速偵測] 方塊左上方的 QR 代碼對齊。</span><span class="sxs-lookup"><span data-stu-id="4edd6-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="4edd6-174">座標系統如下所示。</span><span class="sxs-lookup"><span data-stu-id="4edd6-174">The coordinate system is shown below.</span></span> <span data-ttu-id="4edd6-175">Z 軸指向紙張 (未顯示), 但是在 Unity 中, Z 軸不在紙張中, 而是左手頁。</span><span class="sxs-lookup"><span data-stu-id="4edd6-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="4edd6-176">定義的 SpatialCoordinateSystem 會依照所示對齊。</span><span class="sxs-lookup"><span data-stu-id="4edd6-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="4edd6-177">您可以使用 API *Windows::P erception:: 空間::P 審查:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*, 從平臺取得此座標系統。</span><span class="sxs-lookup"><span data-stu-id="4edd6-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

<span data-ttu-id="4edd6-179">在 QRCode ^ Code 物件中, 下列程式碼會示範如何建立矩形, 並將它放在 QR 座標系統中:</span><span class="sxs-lookup"><span data-stu-id="4edd6-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="4edd6-180">您可以使用實體大小來建立 QR 矩形:</span><span class="sxs-lookup"><span data-stu-id="4edd6-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="4edd6-181">座標系統可以用來繪製 QR 代碼, 或將全息影像附加至位置:</span><span class="sxs-lookup"><span data-stu-id="4edd6-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="4edd6-182">您的*QRCodesTrackerPlugin:: QRCodeAddedHandler*可能會看起來像這樣:</span><span class="sxs-lookup"><span data-stu-id="4edd6-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="4edd6-183">疑難排解和常見問題</span><span class="sxs-lookup"><span data-stu-id="4edd6-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="4edd6-184">**一般疑難排解**</span><span class="sxs-lookup"><span data-stu-id="4edd6-184">**General troubleshooting**</span></span>

* <span data-ttu-id="4edd6-185">您的電腦是否正在執行 Windows 10 2018 年10月更新？</span><span class="sxs-lookup"><span data-stu-id="4edd6-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="4edd6-186">您是否已設定 reg 金鑰？</span><span class="sxs-lookup"><span data-stu-id="4edd6-186">Have you set the reg key?</span></span> <span data-ttu-id="4edd6-187">之後重新開機裝置嗎？</span><span class="sxs-lookup"><span data-stu-id="4edd6-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="4edd6-188">QR 代碼版本是否為支援的版本？</span><span class="sxs-lookup"><span data-stu-id="4edd6-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="4edd6-189">目前的 API 最多支援 QR 代碼版本20。</span><span class="sxs-lookup"><span data-stu-id="4edd6-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="4edd6-190">我們建議使用第5版來進行一般使用。</span><span class="sxs-lookup"><span data-stu-id="4edd6-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="4edd6-191">您夠接近 QR 代碼嗎？</span><span class="sxs-lookup"><span data-stu-id="4edd6-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="4edd6-192">相機愈接近 QR 代碼, API 可支援的 QR 代碼版本愈高。</span><span class="sxs-lookup"><span data-stu-id="4edd6-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="4edd6-193">**我需要什麼時間才能偵測到 QR 代碼？**</span><span class="sxs-lookup"><span data-stu-id="4edd6-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="4edd6-194">這將取決於 QR 代碼的大小, 以及它的版本。</span><span class="sxs-lookup"><span data-stu-id="4edd6-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="4edd6-195">針對第1版的 QR 代碼, 從 5 cm 端到 25 cm 端, 最小偵測距離的範圍是從0.15 計量到0.5 計量。</span><span class="sxs-lookup"><span data-stu-id="4edd6-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="4edd6-196">從大約0.3 計量中, 可以偵測到最遠的, 以較大的 QR 代碼目標為1.4 計量。</span><span class="sxs-lookup"><span data-stu-id="4edd6-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="4edd6-197">對於大於此值的 QR 代碼, 您可以進行評估;大小的偵測距離會以線性方式增加。</span><span class="sxs-lookup"><span data-stu-id="4edd6-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="4edd6-198">我們的追蹤程式無法處理具有小於 5 cm 的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4edd6-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="4edd6-199">**具有標誌的 QR 代碼是否有效？**</span><span class="sxs-lookup"><span data-stu-id="4edd6-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="4edd6-200">具有標誌的 QR 代碼尚未經過測試, 目前不受支援。</span><span class="sxs-lookup"><span data-stu-id="4edd6-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="4edd6-201">**如何? 從我的應用程式中清除 QR 代碼, 使其不會保存？**</span><span class="sxs-lookup"><span data-stu-id="4edd6-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="4edd6-202">QR 代碼只會保存在開機會話中。</span><span class="sxs-lookup"><span data-stu-id="4edd6-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="4edd6-203">一旦您重新開機 (或重新開機驅動程式), 它們就會消失, 並在下次偵測為新物件。</span><span class="sxs-lookup"><span data-stu-id="4edd6-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="4edd6-204">QR 代碼歷程記錄會儲存在驅動程式會話的系統層級, 但是您可以設定應用程式, 略過超過特定時間戳記的 QR 代碼 (如有需要)。</span><span class="sxs-lookup"><span data-stu-id="4edd6-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="4edd6-205">目前, API 支援清除 QR 代碼歷程記錄, 因為多個應用程式可能會對資料感興趣。</span><span class="sxs-lookup"><span data-stu-id="4edd6-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="4edd6-206">**RS5 和未來版本的外掛程式不會相容**RS5 版本的外掛程式僅適用于 RS5, 且在未來版本中將無法運作。</span><span class="sxs-lookup"><span data-stu-id="4edd6-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="4edd6-207">Expermental 外掛程式會以 real 外掛程式取代, 而且應該是我們可以在未來版本的 windows 中使用的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="4edd6-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
