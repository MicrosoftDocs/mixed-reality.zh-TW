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
# <a name="qr-code-tracking"></a><span data-ttu-id="4baf4-104">追蹤的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="4baf4-104">QR code tracking</span></span>

<span data-ttu-id="4baf4-105">沈浸式 (VR) 耳機的 Windows Mixed Reality 驅動程式中實作追蹤的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4baf4-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="4baf4-106">藉由啟用 QR 程式碼追蹤程式耳機驅動程式中的，耳機掃描 QR 代碼並回報給想要的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4baf4-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="4baf4-107">這項功能才可使用的[Windows 10 年 10 月 2018 Update (也稱為 RS5)](release-notes-october-2018.md)。</span><span class="sxs-lookup"><span data-stu-id="4baf4-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="4baf4-108">目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="4baf4-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="4baf4-109">概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="4baf4-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="4baf4-110">裝置支援</span><span class="sxs-lookup"><span data-stu-id="4baf4-110">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4baf4-111">功能</span><span class="sxs-lookup"><span data-stu-id="4baf4-111">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4baf4-112"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4baf4-112"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4baf4-113"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="4baf4-113"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4baf4-114">追蹤的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="4baf4-114">QR code tracking</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="4baf4-115">✔️</span><span class="sxs-lookup"><span data-stu-id="4baf4-115">✔️</span></span></td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="4baf4-116">啟用和停用 QR 程式碼耳機的追蹤</span><span class="sxs-lookup"><span data-stu-id="4baf4-116">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="4baf4-117">注意：本節僅適用於[Windows 10 年 10 月 2018 Update (也稱為 RS5)](release-notes-october-2018.md)。</span><span class="sxs-lookup"><span data-stu-id="4baf4-117">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="4baf4-118">從 19 h 1 組建及更新版本，您將不不必執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="4baf4-118">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="4baf4-119">不論您正在開發的混合的實境應用程式，將會利用追蹤的 QR 代碼，或您是客戶的其中一個應用程式，您必須以手動方式啟動追蹤耳機的驅動程式中的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4baf4-119">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="4baf4-120">若要**開啟 追蹤的 QR 代碼**的沈浸式 (VR) 耳機：</span><span class="sxs-lookup"><span data-stu-id="4baf4-120">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="4baf4-121">關閉您的電腦上的混合的實境入口網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="4baf4-121">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="4baf4-122">請拔除耳機，從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="4baf4-122">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="4baf4-123">在命令提示字元執行下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="4baf4-123">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="4baf4-124">重新連線到您的 PC 耳機。</span><span class="sxs-lookup"><span data-stu-id="4baf4-124">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="4baf4-125">若要**關閉 QR 代碼追蹤**的沈浸式 (VR) 耳機：</span><span class="sxs-lookup"><span data-stu-id="4baf4-125">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="4baf4-126">關閉您的電腦上的混合的實境入口網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="4baf4-126">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="4baf4-127">請拔除耳機，從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="4baf4-127">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="4baf4-128">在命令提示字元執行下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="4baf4-128">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="4baf4-129">重新連線到您的 PC 耳機。</span><span class="sxs-lookup"><span data-stu-id="4baf4-129">Reconnect your headset to your PC.</span></span> <span data-ttu-id="4baf4-130">這會讓任何探索到的 QR 代碼 「 非-之外的可尋獲。 」</span><span class="sxs-lookup"><span data-stu-id="4baf4-130">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="4baf4-131">列印代碼</span><span class="sxs-lookup"><span data-stu-id="4baf4-131">Printing codes</span></span>

<span data-ttu-id="4baf4-132">首先[規格的 QR 代碼](https://www.qrcode.com/en/howto/code.html)指出 「 QR 代碼符號區域需要的邊界或 「 無訊息區 」 周圍可使用它。</span><span class="sxs-lookup"><span data-stu-id="4baf4-132">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="4baf4-133">邊界是不會在此對話方塊列印的清除區域周圍的符號。</span><span class="sxs-lookup"><span data-stu-id="4baf4-133">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="4baf4-134">QR 代碼需要四個模組寬的邊界，在符號的所有側邊。 」</span><span class="sxs-lookup"><span data-stu-id="4baf4-134">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="4baf4-135">這需要對每一側，模組-程式碼中的單一黑色方塊的大小四倍的寬度。</span><span class="sxs-lookup"><span data-stu-id="4baf4-135">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="4baf4-136">[Spec] 頁面包含如何列印 QR 代碼，並找出特定大小的 QR 代碼所需的區域大小的建議。</span><span class="sxs-lookup"><span data-stu-id="4baf4-136">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="4baf4-137">目前 QR 程式碼偵測品質很容易變動的照明和底圖的。</span><span class="sxs-lookup"><span data-stu-id="4baf4-137">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="4baf4-138">若要避免此問題，請注意您照明和列印適當的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4baf4-138">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="4baf4-139">在已加上特別光明的光源的場景，列印黑色灰色背景上的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4baf4-139">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="4baf4-140">在低亮度場景，黑色白色運作。</span><span class="sxs-lookup"><span data-stu-id="4baf4-140">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="4baf4-141">同樣地，如果特別深的程式碼的背景，嘗試灰色的程式碼為黑色，如果您偵測率很低。</span><span class="sxs-lookup"><span data-stu-id="4baf4-141">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="4baf4-142">否則，如果淺色背景，一般的程式碼應該就夠用。</span><span class="sxs-lookup"><span data-stu-id="4baf4-142">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="4baf4-143">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="4baf4-143">QRTracking API</span></span>

<span data-ttu-id="4baf4-144">QRTracking 外掛程式會公開的 Api 可讓追蹤的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4baf4-144">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="4baf4-145">若要使用外掛程式，您必須使用下列類型從*QRCodesTrackerPlugin*命名空間。</span><span class="sxs-lookup"><span data-stu-id="4baf4-145">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="4baf4-146">實作追蹤 Unity 中的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="4baf4-146">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="4baf4-147">範例 MRTK （混合實境工具組） 中的 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="4baf4-147">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="4baf4-148">您可以找到如何使用混合實境工具組中的 QR 追蹤 API 範例[GitHub 網站](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)。</span><span class="sxs-lookup"><span data-stu-id="4baf4-148">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="4baf4-149">MRTK 已實作所需的指令碼，以 simpilify QR 追蹤使用方式。</span><span class="sxs-lookup"><span data-stu-id="4baf4-149">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="4baf4-150">所有所需的資產來開發 QR 追蹤應用程式位於 「 QRTracker"資料夾。</span><span class="sxs-lookup"><span data-stu-id="4baf4-150">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="4baf4-151">有兩個場景： 第一個是只會偵測到，以及第二個示範如何使用附加至 QR 代碼座標系統，以顯示 全像投影顯示 QR 代碼的詳細資料的範例。</span><span class="sxs-lookup"><span data-stu-id="4baf4-151">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="4baf4-152">沒有 prefab"QRScanner 」 來使用 QRCodes 加入所有必要的 scrips。</span><span class="sxs-lookup"><span data-stu-id="4baf4-152">There is a prefab "QRScanner" which added all the necessary scrips to the scenes to use QRCodes.</span></span> <span data-ttu-id="4baf4-153">指令碼 QRCodeManager 是 singileton 類別會實作 QRCode API，您可以將它新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="4baf4-153">The script QRCodeManager is a singileton class that implements the QRCode API you can add it to you scene.</span></span> <span data-ttu-id="4baf4-154">指令碼 」 AttachToQRCode 」 用來附加全像投影的 QR 代碼 coodridnate 系統，此指令碼可以新增至任何您全像投影。</span><span class="sxs-lookup"><span data-stu-id="4baf4-154">The scripts "AttachToQRCode" is used to attach holograms to the QR Code coodridnate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="4baf4-155">「 SpatialGraphCoordinateSystem"會示範如何使用 QRCode 座標系統。</span><span class="sxs-lookup"><span data-stu-id="4baf4-155">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="4baf4-156">可以使用這些指令碼，因為您的專案場景中，或您可以撰寫您自己直接使用外掛程式上面所述。</span><span class="sxs-lookup"><span data-stu-id="4baf4-156">These scripts can be used as is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="4baf4-157">實作追蹤沒有 MRTK Unity 中的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="4baf4-157">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="4baf4-158">您也可以在 Unity 中使用 QR 追蹤 API，而不需要仰賴 MRTK。</span><span class="sxs-lookup"><span data-stu-id="4baf4-158">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="4baf4-159">若要使用的 API，您必須準備您的專案，使用下列指示：</span><span class="sxs-lookup"><span data-stu-id="4baf4-159">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="4baf4-160">在您的 unity 專案名稱的 [assets] 資料夾中建立新的資料夾：「 外掛程式 」。</span><span class="sxs-lookup"><span data-stu-id="4baf4-160">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="4baf4-161">從所有必要的檔案複製[此資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)您剛才建立的本機 「 外掛程式 」 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4baf4-161">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="4baf4-162">您可以使用追蹤的指令碼中的 QR [MRTK 指令碼 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)或自行撰寫。</span><span class="sxs-lookup"><span data-stu-id="4baf4-162">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="4baf4-163">注意：這些外掛程式會僅適用於[Windows 10 年 10 月 2018 Update (也稱為 RS5)](release-notes-october-2018.md)組建。</span><span class="sxs-lookup"><span data-stu-id="4baf4-163">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="4baf4-164">下一步 的 windows 版本中，將會更新外掛程式。</span><span class="sxs-lookup"><span data-stu-id="4baf4-164">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="4baf4-165">目前外掛程式實驗，並不適用於 windows 的未來版本。</span><span class="sxs-lookup"><span data-stu-id="4baf4-165">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="4baf4-166">新的外掛程式將會發行可從下一個 windows 版本並不會回溯相容及不適用於 RS5）。</span><span class="sxs-lookup"><span data-stu-id="4baf4-166">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="4baf4-167">實作追蹤 DirectX 中的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="4baf4-167">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="4baf4-168">若要使用 QRTrackingPlugin Visual Studio 中，您必須將 QRTrackingPlugin 的參考新增至.winmd。</span><span class="sxs-lookup"><span data-stu-id="4baf4-168">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="4baf4-169">您可以找到[所需的檔案支援的平台這裡](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)。</span><span class="sxs-lookup"><span data-stu-id="4baf4-169">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="4baf4-170">取得座標系統</span><span class="sxs-lookup"><span data-stu-id="4baf4-170">Getting a coordinate system</span></span>

<span data-ttu-id="4baf4-171">我們會定義右的座標系統，配合在左上角位於左上方的快速偵測正方形的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4baf4-171">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="4baf4-172">如下所示的座標系統。</span><span class="sxs-lookup"><span data-stu-id="4baf4-172">The coordinate system is shown below.</span></span> <span data-ttu-id="4baf4-173">Z 軸指向納入文件 （未顯示），但在 Unity z 軸和慣用左手紙張用完。</span><span class="sxs-lookup"><span data-stu-id="4baf4-173">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="4baf4-174">定義 SpatialCoordinateSystem 靠所示。</span><span class="sxs-lookup"><span data-stu-id="4baf4-174">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="4baf4-175">您可以從使用 API 的平台取得此座標系統*Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*。</span><span class="sxs-lookup"><span data-stu-id="4baf4-175">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

<span data-ttu-id="4baf4-177">從 QRCode ^ 物件程式碼，下列程式碼示範如何建立矩形，並將它放在 QR 座標系統：</span><span class="sxs-lookup"><span data-stu-id="4baf4-177">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="4baf4-178">您可以使用的實體大小，以建立 QR 矩形：</span><span class="sxs-lookup"><span data-stu-id="4baf4-178">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="4baf4-179">座標系統可以用來繪製 QR 代碼，或附加全像投影至的位置中：</span><span class="sxs-lookup"><span data-stu-id="4baf4-179">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="4baf4-180">總之，您*QRCodesTrackerPlugin::QRCodeAddedHandler*可能看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="4baf4-180">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="4baf4-181">疑難排解和常見問題集</span><span class="sxs-lookup"><span data-stu-id="4baf4-181">Troubleshooting and FAQ</span></span>

<span data-ttu-id="4baf4-182">**一般疑難排解**</span><span class="sxs-lookup"><span data-stu-id="4baf4-182">**General troubleshooting**</span></span>

* <span data-ttu-id="4baf4-183">為您的電腦執行 Windows 10 年 10 月 2018年更新嗎？</span><span class="sxs-lookup"><span data-stu-id="4baf4-183">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="4baf4-184">您已設定登錄機碼？</span><span class="sxs-lookup"><span data-stu-id="4baf4-184">Have you set the reg key?</span></span> <span data-ttu-id="4baf4-185">之後重新啟動裝置嗎？</span><span class="sxs-lookup"><span data-stu-id="4baf4-185">Restarted the device afterwards?</span></span>
* <span data-ttu-id="4baf4-186">是 QR 程式碼版本支援的版本嗎？</span><span class="sxs-lookup"><span data-stu-id="4baf4-186">Is the QR code version a supported version?</span></span> <span data-ttu-id="4baf4-187">目前的 API 支援最多 QR 程式碼版本 20 個。</span><span class="sxs-lookup"><span data-stu-id="4baf4-187">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="4baf4-188">我們建議使用一般用途的第 5 版。</span><span class="sxs-lookup"><span data-stu-id="4baf4-188">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="4baf4-189">為您關閉 QR 代碼足以嗎？</span><span class="sxs-lookup"><span data-stu-id="4baf4-189">Are you close enough to the QR code?</span></span> <span data-ttu-id="4baf4-190">越接近相機 QR 代碼，可支援更高的 QR 程式碼版本的 API。</span><span class="sxs-lookup"><span data-stu-id="4baf4-190">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="4baf4-191">**我要如何關閉 QR 代碼，來偵測它是？**</span><span class="sxs-lookup"><span data-stu-id="4baf4-191">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="4baf4-192">這將取決於大小的 QR 代碼，而且也哪一個版本。</span><span class="sxs-lookup"><span data-stu-id="4baf4-192">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="4baf4-193">第 1 版 QR 代碼，範圍從 5 cm 側邊到 25 公分側邊，最小偵測距離範圍 0.15 公尺至 0.5 的計量。</span><span class="sxs-lookup"><span data-stu-id="4baf4-193">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="4baf4-194">最遠了這些可以偵測到從會從較小的 QR 代碼目標大約 0.3 公尺至愈大 1.4 計量。</span><span class="sxs-lookup"><span data-stu-id="4baf4-194">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="4baf4-195">大於的 QR 代碼，您可以評估;偵測距離大小呈線性增加。</span><span class="sxs-lookup"><span data-stu-id="4baf4-195">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="4baf4-196">我們追蹤程式不適用於具有邊的 QR 代碼小於 5 cm。</span><span class="sxs-lookup"><span data-stu-id="4baf4-196">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="4baf4-197">**請勿使用標誌工作的 QR 代碼？**</span><span class="sxs-lookup"><span data-stu-id="4baf4-197">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="4baf4-198">具有標誌的 QR 代碼尚未經過測試，以及目前不支援。</span><span class="sxs-lookup"><span data-stu-id="4baf4-198">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="4baf4-199">**如何清除 QR 代碼從我的應用程式讓它們不會保存？**</span><span class="sxs-lookup"><span data-stu-id="4baf4-199">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="4baf4-200">QR 代碼，才會保存在開機工作階段中。</span><span class="sxs-lookup"><span data-stu-id="4baf4-200">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="4baf4-201">一旦重新啟動 （或重新啟動的驅動程式），它們會進入並偵測為新物件下一次。</span><span class="sxs-lookup"><span data-stu-id="4baf4-201">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="4baf4-202">QR 程式碼歷程記錄時，會儲存在系統層級上，在驅動程式工作階段中，但您可以設定您的應用程式，如果您想要忽略超過特定的時間戳記的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4baf4-202">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="4baf4-203">目前 API 並支援清除 QR 程式碼歷程記錄，因為多個應用程式可能感興趣的資料。</span><span class="sxs-lookup"><span data-stu-id="4baf4-203">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="4baf4-204">**外掛程式 RS5 和未來的版本不相容**RS5 新版的外掛程式只適用於的 RS5，未來版本將無法運作。</span><span class="sxs-lookup"><span data-stu-id="4baf4-204">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="4baf4-205">Expermental 外掛程式將會取代為實際的外掛程式，並應該是，我們可以使用在未來的 windows 版本。</span><span class="sxs-lookup"><span data-stu-id="4baf4-205">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
