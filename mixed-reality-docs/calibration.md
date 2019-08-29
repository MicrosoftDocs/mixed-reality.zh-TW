---
title: 效果
description: 校準您的 IPD (interpupillary 距離) 可以改善視覺效果的品質。 HoloLens 和 Windows Mixed Reality 的沉浸式耳機都提供自訂 IPD 的方式。
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 校正, 舒適, 視覺效果, 品質, ipd
ms.openlocfilehash: e86319dadeda02f71427b87980268eaf18942c49
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122083"
---
# <a name="improve-visual-quality-and-comfort"></a>改善視覺品質和舒適
HoloLens、HoloLens 2 和 Windows Mixed Reality 沉浸式耳機提供不同的方式來改善視覺效果的品質。 

## <a name="hololens-2"></a>Hololens 2

### <a name="calibration"></a>效果

Hololens 2 的設計目的是為客戶提供最高品質的視覺效果影像和緩和。 眼睛追蹤技術是用來改善在虛擬環境中查看和互動的使用者體驗。  

在 HoloLens 2 上, 系統會提示您在裝置設定期間校準您的視覺效果。 系統會要求使用者查看一組 fixation 目標。 這可讓裝置調整影像的呈現方式, 以確保正確定位的全息影像、舒適的3D 觀賞體驗, 以及改良的顯示品質。 所有的調整會即時進行, 而不需要手動調整。 藉由使用眼睛做為地標, 裝置會個別調整為每位使用者, 而且視覺效果會隨著耳機在使用中稍微移動而調整。 系統會在內部使用眼睛追蹤, 而開發人員則不需要採取任何動作來運用這項功能。 事實上, 開發人員無法使用這項資訊。
請參閱[眼睛追蹤 api](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) , 以深入瞭解眼睛追蹤系統提供給開發人員的資料類型。

在 Hololens 2 上, 執行校正也可以確保每一位使用者都能進行精確的眼睛追蹤。 眼球追蹤可讓應用程式即時追蹤使用者的視線方向。 這是開發人員可以利用的主要功能, 在全像攝影體驗中啟用全新的內容、人類瞭解及互動。  

校正資料會儲存在本機裝置上, 而且不會與任何帳戶資訊相關聯。 沒有任何已使用裝置而未進行校正的記錄。 這表示當使用者第一次使用裝置時, 以及選擇不進行校正或校正不成功時, 系統會提示他們進行校準。 在 [**設定** > ] [**隱私權** > **監控**] 中, 您一律可以從裝置中刪除校正資料。 

### <a name="calibration-failures"></a>校正失敗
校正應該適用于大部分的使用者, 但在某些情況下, 使用者可能無法成功校準。  
一些校正失敗的範例是因為:
- 使用者有注意力, 而且在校正體驗期間不會查看校正目標
- 已變更或有劃痕的裝置面板或裝置面板未正確定位 
- 某些類型的連絡人鏡頭和眼鏡 (彩色連絡人鏡頭, 部分 toric 連絡人鏡頭, IR 封鎖眼鏡, 一些高處方眼鏡, 太陽眼鏡等等)
- 中途或有劃痕的眼鏡
- 更明顯的構成, 某些 eyelash 擴充功能
- 眼睛和/或裝置面板遮蔽 (頭髮、一些粗眼鏡的框架)
- 眼睛生理學、特定的眼睛和 (或) 眼睛 (一些狹窄的眼睛、長 eyelashes、amblyopia、nystagmus、LASIK 或其他眼睛 surgeries 的一些案例等等)

如果校正不成功, 請嘗試下列其中一個修正: 
- 清理您的裝置面板
- 清理您的眼鏡
- 將您的裝置面板全部推送到
- 請確定沒有任何阻礙感應器或您的眼睛 (例如, 頭髮) 
- 請確定您的房間內有足夠的光線, 而且您不是在直接陽光下
- 請確定您在校正期間仔細遵循目標

如果您遵循所有方針, 而且校正仍然失敗, 您可以在 [**設定** > ] [**系統** > **校正**] 中停用校正提示:「*當新人員使用此 Hololens 時, 會自動要求執行眼睛校正*」功能。 請瞭解, 這可能會導致更糟的全息影像轉譯品質和 discomfort。

### <a name="launching-the-calibration-app-from-settings"></a>從設定啟動校正應用程式
1. 移至 HoloLens 2 上的 [設定] 頁面
    * 使用 [*開始手勢]* 以顯示 [開始][功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。 或者, 您也可以直接說 *「移至開始」* 。
    * 如果**設定**未釘選到 [啟動], 請選取 [**所有應用程式**] 以查看所有應用程式
    * 啟動**設定**
2. 流覽至 [**系統** > **校正** > ] [**眼睛校正**], 然後選取 [**執行眼校正**]


### <a name="calibration-when-sharing-a-devicesession"></a>共用裝置/會話時的校正
Hololens 2 可以在人員之間共用, 而不需要每個人完成裝置設定體驗。
如果使用者是裝置的新手, 則 Hololens 2 會在裝置放在前端時, 提示使用者校準視覺效果。 如果使用者先前已校正裝置上的視覺效果, 則會順暢地調整顯示品質, 並在使用者將裝置放在前端時, 取得舒適的觀賞體驗。 


## <a name="hololens-v1"></a>HoloLens (v1)
校準您的 IPD (interpupillary 距離) 可以改善視覺效果的品質。

### <a name="during-setup"></a>在安裝期間

![第二步的 IPD 手指對齊畫面](images/ipd-finger-alignment-300px.jpg)<br>

*第二步的 IPD 手指對齊畫面*

在 HoloLens 上, 系統會提示您在安裝期間校準您的視覺效果。 這可讓裝置根據使用者的[interpupillary 距離](https://en.wikipedia.org/wiki/Interpupillary_distance)(IPD) 調整全息顯示畫面。 使用不正確的 IPD, 全息影像可能會顯示不穩定或不正確的距離。

在 Cortana 引進之後, 第一個設定步驟是校正。 建議您在此設定階段完成校正步驟, 但可以略過, 直到 Cortana 提示您說「略過」繼續進行。

系統會要求使用者將其手指與一系列六個目標密切配合。 在此過程中, HoloLens 會為使用者設定正確的 IPD。 如果需要更新或調整新使用者的校正, 可以使用校正應用程式在安裝程式之外執行。

### <a name="calibration-app"></a>校正應用程式

透過校正應用程式可以隨時執行校正。 根據預設, 會安裝校正應用程式, 並可從 [開始] 功能表或透過 [設定] 應用程式存取。 如果您想要改善視覺效果的品質, 或為新使用者校準視覺效果, 建議使用校正。

**從開始啟動應用程式**
1. 使用[bloom](gestures.md#bloom)來取得 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。
2. 選取 **+** 以查看所有應用程式。
3. 啟動**校正**。

![從 shell 存取校正應用程式](images/calibration-shell.png)

![在啟動後顯示為即時 Cube 的校正應用程式](images/calibration-livecube-200px.png)

**從設定啟動應用程式**
1. 使用[bloom](gestures.md#bloom)來取得 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。
2. 如果 **+** **設定**未釘選到 [啟動], 請選取此值來查看所有應用程式。
3. 啟動**設定**。
4. 流覽至 [**系統** > **公用程式**], 然後選取 [**開啟校正**]。

![從設定應用程式啟動校正應用程式](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a>沉浸式頭戴裝置

若要變更頭戴式裝置內的 IPD, 請開啟 [設定] 應用程式, 並流覽至 [**混合現實** > **頭戴式**裝置] 顯示並移動滑杆控制項。 您會在頭戴式裝置上即時看到變更。 如果您知道 IPD, 也許是從造訪 optometrist, 您也可以直接輸入它。

您也可以前往電腦上的 [**設定** > ] [**混合現實** > **頭戴式**裝置] 顯示來調整此設定。

如果您的耳機不支援 IPD 自訂, 則會停用此設定。

## <a name="see-also"></a>另請參閱
* [HoloLens 的環境考量](environment-considerations-for-hololens.md)
