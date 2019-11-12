---
title: 混合現實空間資料封裝程式檔
description: 使用混合現實空間資料封裝工具的檔
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe、MixedRealitySpatialDataPackager、MixedRealitySpatialDataPackager
ms.openlocfilehash: 331fa6dc752c64eeaa5bc2e9d1dd6b2c15049a27
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926753"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>混合現實空間資料封裝程式檔

>[!NOTE]
> 此工具和其作業是依自己提供。 如有任何變更，恕不另行通知，而且可能無法與未來的 Windows 或 Windows Mixed Reality HMD 版本相容。

## <a name="download"></a>您剛才購買的產品旁的 [下載]
 [在此下載 MixedRealitySpatialDataPackager](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>特徵</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>混合現實空間資料封裝工具</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>入門

Mixed Reality 空間資料封裝工具會透過兩個步驟的匯出和匯入程式，將目標應用程式的空間資料從一部電腦複製到另一部電腦。 此工具必須以系統管理員許可權執行，並在匯入時刪除現有的空間資料。 匯出會讓現有的空間資料保持不變。

主要需求和限制：

1. 工具必須以系統管理員許可權執行 
2. 如果混合現實入口網站在執行此工具之後變得不穩定，您可能必須重新開機電腦
3. 當遇到空間資料版本不符或不相容時，工具將不會執行
4. 匯入時，工具將會清除現有的空間資料
5. 如果匯入程式失敗，除非先前已匯出，否則無法還原先前的資料
6. 空間對應資料之「唯讀」模式的匯入功能品質
***

## <a name="mapping-best-practices"></a>對應最佳作法

1. 從 [控制台] 清除現有的對應（設定-> 混合現實-> 環境-> 清除環境資料）
2. 確保有足夠的光源來進行良好的追蹤，而且如果執行鎖定的地圖模式嘗試維持相同的光源
3. 可能的話，您可以避免在深色、陰影區域旁邊的高光源區域，讓光線動態範圍降低
4. 最小化空白的 textureless 介面，例如將各種不同的海報放在白色牆上
5. 對應場景中沒有動態物件的空間，例如移動人員
6. 在匯入時鎖定對應（可透過 Insider Preview 取得）
7. 解除鎖定對應，並在追蹤品質降低和（或）環境中有變更（光源或物件版面配置中的變更）時重新掃描環境
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>使用隨附腳本執行混合現實空間資料封裝工具

我們提供的 MRSpatialPackagerHelperScript 會執行地圖封裝工具。 


腳本參數定義如下：

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

### <a name="powershell-script-example-usage-and-output"></a>Powershell 腳本範例使用方式和輸出

.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-使用者名稱系統管理員-模式匯出-MapxPath D:\temp\-LockMap 0
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>如何使用 MixedRealityPackager 匯出
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

將地圖服務匯出關閉裝置會產生兩個 mapx 檔案： het. mapx 和 sa. mapx。 在匯出過程中，除了指定的應用程式和使用者建立的界限（如果存在）之外，所有空間錨點都會移除。 來源套件系列名稱必須符合現有已安裝的應用程式，否則 exe 將會失敗。

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>如何使用 MixedRealityPackager 匯入
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
[匯入] 會刪除現有的空間資料，並將它取代為指定目錄中的資料。 應用程式名稱輸入會指定應匯入空間錨點的目標應用程式套件名稱，而目標使用者 SID 則指定應該具有已匯入之空間錨點存取權的使用者。 目標套件系列名稱和使用者 Sid 必須符合電腦上的現有值，否則 exe 將會失敗。


***
## <a name="error-messages"></a>錯誤訊息
此外，下列錯誤訊息也會伴隨著 HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>如果發生錯誤不正確引數
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>如果可執行檔不是以系統管理員模式執行
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>如果啟用或停用驅動程式時發生錯誤
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>如果驗證空間資料庫版本時發生錯誤
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>如果驗證為目標匯入/匯出應用程式提供的套件系列名稱時發生錯誤
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>如果驗證使用者 SID 時發生錯誤
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>如果發生與目的地或來源空間資料檔相關的錯誤
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>如果發生與啟動和停止頻譜/SharedRealitySvc 相關的錯誤
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
