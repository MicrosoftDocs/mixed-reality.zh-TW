---
title: 混合的實境空間資料封裝程式文件
description: 使用混合實境的空間資料 Packager 的文件
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe MixedRealitySpatialDataPackager.exe MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942104"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>混合的實境空間資料封裝程式文件

>[!NOTE]
> 這項工具和其作業提供做為是。 它有變更恕不任何通知，並可能無法相容於未來的 Windows 或 Windows Mixed Reality HMD 釋放。

## <a name="download"></a>下載
 下載[MixedRealitySpatialDataPackager 這裡](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="quickstart"></a>快速入門

混合實境的空間資料 Packager 工具空間的目標應用程式會將資料複製到另一個執行兩個步驟的電腦匯出並匯入程序。 此工具必須以系統管理員權限執行，並刪除現有的空間資料匯入。 匯出可讓現有的空間資料保持不變。

索引鍵的需求和限制：

1. 工具必須以系統管理員權限執行 
2. 您可能必須重新啟動電腦，如果執行此工具之後，混合實境入口網站不穩定
3. 當發現空間資料的版本不相符或不相容時，不會執行工具
4. 工具將會清除現有的空間資料匯入
5. 除非它已經備份先前匯出先前匯入程序時無法還原資料
6. 匯入功能而定，「 唯讀 」 模式，以空間的對應資料的品質
***

## <a name="mapping-best-practices"></a>對應最佳作法

1. 清除控制項台中現有的對應 (設定]-> [Mixed Reality]-> [環境]-> [清除的環境資料)
2. 確保良好的追蹤，而且如果執行鎖定的地圖模式中嘗試維護相同的光源的足夠光源
3. 盡可能保持光源動態範圍低藉由避免高照明深色的遮蔽的區域旁邊的區域
4. 最小化 空白，例如在白色背景牆上放置各種不同的海報的 textureless 介面
5. 對應不含動態物件，例如移動人場景中的空間
6. 鎖定 （可透過 Insider Preview） 的匯入對應
7. 地圖，並追蹤品質會降低和/或 （光源或物件配置中的變更） 的環境中有變更時，將環境重新掃描
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>使用隨附的指令碼執行混合的實境空間資料封裝程式

我們提供了 MRSpatialPackagerHelperScript.ps1 執行對應 packager 工具。 


指令碼參數定義如下：

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

### <a name="powershell-script-example-usage-and-output"></a>使用方式範例 Powershell 指令碼和輸出

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>如何使用 MixedRealityPackager.exe 匯出
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

匯出裝置的對應產生 sa.mapx、 het.mapx 和兩個 mapx 檔案。 在匯出過程中所有空間的錨點會移除指定的應用程式和使用者建立的界限除外 （若有的話）。 來源的套件系列名稱必須符合現有的已安裝應用程式，或將 exe 將會失敗。

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>如何使用 MixedRealityPackager.exe 匯入
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
匯入刪除現有的空間資料，並取代指定之目錄中的資料。 應用程式名稱輸入指定應該匯入的目標應用程式，例如空間的錨點的封裝名稱和目標使用者 SID 指定應該具有存取權的匯入的空間錨點的使用者。 使用者 Sid 與目標的套件系列名稱必須符合在電腦上的現有值或 exe 將會失敗。


***
## <a name="error-messages"></a>錯誤訊息
除了下列失敗的錯誤訊息將也伴隨的 hresult

### <a name="if-there-was-an-error-invalid-arguments"></a>如果發生錯誤的引數無效
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>如果未在系統管理員模式中執行可執行檔
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>如果發生錯誤，啟用或停用驅動程式
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>如果正在驗證空間的資料庫版本時發生錯誤。
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>如果驗證目標匯入/匯出應用程式提供的套件系列名稱時發生錯誤。
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>如果驗證使用者的 SID 時發生錯誤。
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>如果發生錯誤相關的目的地或來源的空間資料檔案
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>如果已啟動及停止範圍/SharedRealitySvc 相關的錯誤
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
