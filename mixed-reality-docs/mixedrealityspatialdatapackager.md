---
title: 混合現實空間資料封裝程式檔
description: 使用混合現實空間資料封裝工具的檔
author: alfred-msft
ms.author: yuripek
ms.date: 05/16/2019
ms.topic: article
keywords: lbe、MixedRealitySpatialDataPackager、MixedRealitySpatialDataPackager
ms.openlocfilehash: 3beb8f9168bfb6fd921d6d5c1eb6d250c70a714d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539682"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="42201-104">混合現實空間資料封裝程式檔</span><span class="sxs-lookup"><span data-stu-id="42201-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="42201-105">此工具和其作業是依自己提供。</span><span class="sxs-lookup"><span data-stu-id="42201-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="42201-106">如有任何變更，恕不另行通知，而且可能無法與未來的 Windows 或 Windows Mixed Reality HMD 版本相容。</span><span class="sxs-lookup"><span data-stu-id="42201-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="42201-107">您剛才購買的產品旁的 [下載]</span><span class="sxs-lookup"><span data-stu-id="42201-107">Download</span></span>
 <span data-ttu-id="42201-108">[在此下載 MixedRealitySpatialDataPackager](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="42201-108">Download [MixedRealitySpatialDataPackager here](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="device-support"></a><span data-ttu-id="42201-109">裝置支援</span><span class="sxs-lookup"><span data-stu-id="42201-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="42201-110"><strong>特徵</strong></span><span class="sxs-lookup"><span data-stu-id="42201-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="42201-111"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="42201-111"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="42201-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="42201-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="42201-113"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="42201-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="42201-114">混合現實空間資料封裝工具</span><span class="sxs-lookup"><span data-stu-id="42201-114">Mixed Reality Spatial Data Packager</span></span></td>
        <td>❌</td>
        <td>❌</td>
        <td><span data-ttu-id="42201-115">✔️</span><span class="sxs-lookup"><span data-stu-id="42201-115">✔️</span></span></td>
    </tr>
</table>

## <a name="quickstart"></a><span data-ttu-id="42201-116">入門</span><span class="sxs-lookup"><span data-stu-id="42201-116">Quickstart</span></span>

<span data-ttu-id="42201-117">Mixed Reality 空間資料封裝工具會透過兩個步驟的匯出和匯入程式，將目標應用程式的空間資料從一部電腦複製到另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="42201-117">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="42201-118">此工具必須以系統管理員許可權執行，並在匯入時刪除現有的空間資料。</span><span class="sxs-lookup"><span data-stu-id="42201-118">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="42201-119">匯出會讓現有的空間資料保持不變。</span><span class="sxs-lookup"><span data-stu-id="42201-119">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="42201-120">主要需求和限制：</span><span class="sxs-lookup"><span data-stu-id="42201-120">Key requirements and limitations:</span></span>

1. <span data-ttu-id="42201-121">工具必須以系統管理員許可權執行</span><span class="sxs-lookup"><span data-stu-id="42201-121">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="42201-122">如果混合現實入口網站在執行此工具之後變得不穩定，您可能必須重新開機電腦</span><span class="sxs-lookup"><span data-stu-id="42201-122">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="42201-123">當遇到空間資料版本不符或不相容時，工具將不會執行</span><span class="sxs-lookup"><span data-stu-id="42201-123">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="42201-124">匯入時，工具將會清除現有的空間資料</span><span class="sxs-lookup"><span data-stu-id="42201-124">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="42201-125">如果匯入程式失敗，除非先前已匯出，否則無法還原先前的資料</span><span class="sxs-lookup"><span data-stu-id="42201-125">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="42201-126">空間對應資料之「唯讀」模式的匯入功能品質</span><span class="sxs-lookup"><span data-stu-id="42201-126">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="42201-127">對應最佳作法</span><span class="sxs-lookup"><span data-stu-id="42201-127">Mapping Best Practices</span></span>

1. <span data-ttu-id="42201-128">從 [控制台] 清除現有的對應（設定-> 混合現實-> 環境-> 清除環境資料）</span><span class="sxs-lookup"><span data-stu-id="42201-128">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="42201-129">確保有足夠的光源來進行良好的追蹤，而且如果執行鎖定的地圖模式嘗試維持相同的光源</span><span class="sxs-lookup"><span data-stu-id="42201-129">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="42201-130">可能的話，您可以避免在深色、陰影區域旁邊的高光源區域，讓光線動態範圍降低</span><span class="sxs-lookup"><span data-stu-id="42201-130">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="42201-131">最小化空白的 textureless 介面，例如將各種不同的海報放在白色牆上</span><span class="sxs-lookup"><span data-stu-id="42201-131">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="42201-132">對應場景中沒有動態物件的空間，例如移動人員</span><span class="sxs-lookup"><span data-stu-id="42201-132">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="42201-133">在匯入時鎖定對應（可透過 Insider Preview 取得）</span><span class="sxs-lookup"><span data-stu-id="42201-133">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="42201-134">解除鎖定對應，並在追蹤品質降低和（或）環境中有變更（光源或物件版面配置中的變更）時重新掃描環境</span><span class="sxs-lookup"><span data-stu-id="42201-134">Unlock the map and rescan the environment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="42201-135">使用隨附腳本執行混合現實空間資料封裝工具</span><span class="sxs-lookup"><span data-stu-id="42201-135">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="42201-136">我們提供的 MRSpatialPackagerHelperScript 會執行地圖封裝工具。</span><span class="sxs-lookup"><span data-stu-id="42201-136">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="42201-137">腳本參數定義如下：</span><span class="sxs-lookup"><span data-stu-id="42201-137">The script parameters are defined below:</span></span>

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="42201-138">Powershell 腳本範例使用方式和輸出</span><span class="sxs-lookup"><span data-stu-id="42201-138">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="42201-139">.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-使用者名稱系統管理員-模式匯出-MapxPath D:\temp\-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="42201-139">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="42201-140">如何使用 MixedRealityPackager 匯出</span><span class="sxs-lookup"><span data-stu-id="42201-140">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="42201-141">將地圖服務匯出關閉裝置會產生兩個 mapx 檔案： het. mapx 和 sa. mapx。</span><span class="sxs-lookup"><span data-stu-id="42201-141">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="42201-142">在匯出過程中，除了指定的應用程式和使用者建立的界限（如果存在）之外，所有空間錨點都會移除。</span><span class="sxs-lookup"><span data-stu-id="42201-142">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="42201-143">來源套件系列名稱必須符合現有已安裝的應用程式，否則 exe 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="42201-143">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="42201-144">如何使用 MixedRealityPackager 匯入</span><span class="sxs-lookup"><span data-stu-id="42201-144">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="42201-145">[匯入] 會刪除現有的空間資料，並將它取代為指定目錄中的資料。</span><span class="sxs-lookup"><span data-stu-id="42201-145">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="42201-146">應用程式名稱輸入會指定應匯入空間錨點的目標應用程式套件名稱，而目標使用者 SID 則指定應該具有已匯入之空間錨點存取權的使用者。</span><span class="sxs-lookup"><span data-stu-id="42201-146">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="42201-147">目標套件系列名稱和使用者 Sid 必須符合電腦上的現有值，否則 exe 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="42201-147">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="42201-148">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="42201-148">Error Messages</span></span>
<span data-ttu-id="42201-149">此外，下列錯誤訊息也會伴隨著 HRESULT</span><span class="sxs-lookup"><span data-stu-id="42201-149">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="42201-150">如果發生錯誤不正確引數</span><span class="sxs-lookup"><span data-stu-id="42201-150">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="42201-151">如果可執行檔不是以系統管理員模式執行</span><span class="sxs-lookup"><span data-stu-id="42201-151">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="42201-152">如果啟用或停用驅動程式時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="42201-152">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="42201-153">如果驗證空間資料庫版本時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="42201-153">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="42201-154">如果驗證為目標匯入/匯出應用程式提供的套件系列名稱時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="42201-154">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="42201-155">如果驗證使用者 SID 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="42201-155">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="42201-156">如果發生與目的地或來源空間資料檔相關的錯誤</span><span class="sxs-lookup"><span data-stu-id="42201-156">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a><span data-ttu-id="42201-157">如果發生與啟動和停止頻譜/SharedRealitySvc 相關的錯誤</span><span class="sxs-lookup"><span data-stu-id="42201-157">If there was an error related to starting and stopping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
