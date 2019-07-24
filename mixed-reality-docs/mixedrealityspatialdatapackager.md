---
title: 混合現實空間資料封裝程式檔
description: 使用混合現實空間資料封裝工具的檔
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe、MixedRealitySpatialDataPackager、MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942104"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="59974-104">混合現實空間資料封裝程式檔</span><span class="sxs-lookup"><span data-stu-id="59974-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="59974-105">此工具和其作業是依自己提供。</span><span class="sxs-lookup"><span data-stu-id="59974-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="59974-106">如有任何變更, 恕不另行通知, 而且可能無法與未來的 Windows 或 Windows Mixed Reality HMD 版本相容。</span><span class="sxs-lookup"><span data-stu-id="59974-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="59974-107">下載</span><span class="sxs-lookup"><span data-stu-id="59974-107">Download</span></span>
 <span data-ttu-id="59974-108">[在此下載 MixedRealitySpatialDataPackager](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="59974-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="59974-109">入門</span><span class="sxs-lookup"><span data-stu-id="59974-109">Quickstart</span></span>

<span data-ttu-id="59974-110">Mixed Reality 空間資料封裝工具會透過兩個步驟的匯出和匯入程式, 將目標應用程式的空間資料從一部電腦複製到另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="59974-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="59974-111">此工具必須以系統管理員許可權執行, 並在匯入時刪除現有的空間資料。</span><span class="sxs-lookup"><span data-stu-id="59974-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="59974-112">匯出會讓現有的空間資料保持不變。</span><span class="sxs-lookup"><span data-stu-id="59974-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="59974-113">主要需求和限制:</span><span class="sxs-lookup"><span data-stu-id="59974-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="59974-114">工具必須以系統管理員許可權執行</span><span class="sxs-lookup"><span data-stu-id="59974-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="59974-115">如果混合現實入口網站在執行此工具之後變得不穩定, 您可能必須重新開機電腦</span><span class="sxs-lookup"><span data-stu-id="59974-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="59974-116">當遇到空間資料版本不符或不相容時, 工具將不會執行</span><span class="sxs-lookup"><span data-stu-id="59974-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="59974-117">匯入時, 工具將會清除現有的空間資料</span><span class="sxs-lookup"><span data-stu-id="59974-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="59974-118">如果匯入程式失敗, 除非先前已匯出, 否則無法還原先前的資料</span><span class="sxs-lookup"><span data-stu-id="59974-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="59974-119">空間對應資料之「唯讀」模式的匯入功能品質</span><span class="sxs-lookup"><span data-stu-id="59974-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="59974-120">對應最佳作法</span><span class="sxs-lookup"><span data-stu-id="59974-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="59974-121">從 [控制台] 清除現有的對應 (設定-> 混合現實-> 環境-> 清除環境資料)</span><span class="sxs-lookup"><span data-stu-id="59974-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="59974-122">確保有足夠的光源來進行良好的追蹤, 而且如果執行鎖定的地圖模式嘗試維持相同的光源</span><span class="sxs-lookup"><span data-stu-id="59974-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="59974-123">可能的話, 您可以避免在深色、陰影區域旁邊的高光源區域, 讓光線動態範圍降低</span><span class="sxs-lookup"><span data-stu-id="59974-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="59974-124">最小化空白的 textureless 介面, 例如將各種不同的海報放在白色牆上</span><span class="sxs-lookup"><span data-stu-id="59974-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="59974-125">對應場景中沒有動態物件的空間, 例如移動人員</span><span class="sxs-lookup"><span data-stu-id="59974-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="59974-126">在匯入時鎖定對應 (可透過 Insider Preview 取得)</span><span class="sxs-lookup"><span data-stu-id="59974-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="59974-127">解除鎖定地圖並在追蹤品質降低和 (或) 環境中有變更時重新掃描環境 (物件版面配置中的光源或變更)</span><span class="sxs-lookup"><span data-stu-id="59974-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="59974-128">使用隨附腳本執行混合現實空間資料封裝工具</span><span class="sxs-lookup"><span data-stu-id="59974-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="59974-129">我們提供的 MRSpatialPackagerHelperScript 會執行地圖封裝工具。</span><span class="sxs-lookup"><span data-stu-id="59974-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="59974-130">腳本參數定義如下:</span><span class="sxs-lookup"><span data-stu-id="59974-130">The script parameters are defined below:</span></span>

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
    This functionality requires an updated driver from Insider Preview Builds with the Map Locking feature

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="59974-131">Powershell 腳本範例使用方式和輸出</span><span class="sxs-lookup"><span data-stu-id="59974-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="59974-132">.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-使用者名稱系統管理員-模式匯出-MapxPath D:\temp\-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="59974-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value succesfully set to 0

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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="59974-133">如何使用 MixedRealityPackager 匯出</span><span class="sxs-lookup"><span data-stu-id="59974-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="59974-134">將地圖服務匯出關閉裝置會產生兩個 mapx 檔案: het. mapx 和 sa. mapx。</span><span class="sxs-lookup"><span data-stu-id="59974-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="59974-135">在匯出過程中, 除了指定的應用程式和使用者建立的界限 (如果存在) 之外, 所有空間錨點都會移除。</span><span class="sxs-lookup"><span data-stu-id="59974-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="59974-136">來源套件系列名稱必須符合現有已安裝的應用程式, 否則 exe 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="59974-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="59974-137">如何使用 MixedRealityPackager 匯入</span><span class="sxs-lookup"><span data-stu-id="59974-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="59974-138">[匯入] 會刪除現有的空間資料, 並將它取代為指定目錄中的資料。</span><span class="sxs-lookup"><span data-stu-id="59974-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="59974-139">應用程式名稱輸入會指定應匯入空間錨點的目標應用程式套件名稱, 而目標使用者 SID 則指定應該具有已匯入之空間錨點存取權的使用者。</span><span class="sxs-lookup"><span data-stu-id="59974-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="59974-140">目標套件系列名稱和使用者 Sid 必須符合電腦上的現有值, 否則 exe 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="59974-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="59974-141">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="59974-141">Error Messages</span></span>
<span data-ttu-id="59974-142">此外, 下列錯誤訊息也會伴隨著 HRESULT</span><span class="sxs-lookup"><span data-stu-id="59974-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="59974-143">如果發生錯誤不正確引數</span><span class="sxs-lookup"><span data-stu-id="59974-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="59974-144">如果可執行檔不是以系統管理員模式執行</span><span class="sxs-lookup"><span data-stu-id="59974-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="59974-145">如果啟用或停用驅動程式時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="59974-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="59974-146">如果驗證空間資料庫版本時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="59974-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="59974-147">如果驗證為目標匯入/匯出應用程式提供的套件系列名稱時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="59974-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="59974-148">如果驗證使用者 SID 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="59974-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="59974-149">如果發生與目的地或來源空間資料檔相關的錯誤</span><span class="sxs-lookup"><span data-stu-id="59974-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="59974-150">如果發生與啟動和 stoping 頻譜/SharedRealitySvc 相關的錯誤</span><span class="sxs-lookup"><span data-stu-id="59974-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
