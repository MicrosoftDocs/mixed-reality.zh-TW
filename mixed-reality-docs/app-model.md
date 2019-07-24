---
title: 應用程式模型
description: Windows Mixed Reality 會使用通用 Windows 平臺所提供的應用程式模型, 這是適用于新式 Windows 應用程式的模型和環境。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, 應用程式模型, 生命週期, 暫停, 繼續, 磚, 視圖, 合約
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63517264"
---
# <a name="app-model"></a>應用程式模型

Windows Mixed Reality 會使用[通用 Windows 平臺](https://docs.microsoft.com/windows/uwp/get-started/)(UWP) 提供的應用程式模型, 這是適用于新式 Windows 應用程式的模型和環境。 UWP 應用程式模型會定義如何安全且完全移除應用程式的安裝、更新、設定版本和。 它會控管應用程式生命週期-應用程式如何執行、睡眠和終止, 以及如何保留狀態。 其中也涵蓋與作業系統、檔案和其他應用程式的整合與互動。

![在早餐區域的 Windows Mixed Reality 首頁中排列的2D 應用程式](images/20160112-055908-hololens-500px.jpg)<br>
*具有2D 視圖的應用程式在 Windows Mixed Reality 首頁中排列*

## <a name="app-lifecycle"></a>應用程式週期

混合現實應用程式的生命週期牽涉到標準應用程式概念, 例如放置、啟動、終止和移除。

### <a name="placement-is-launch"></a>放置已啟動

每個應用程式都是以混合現實的方式啟動, 只要將應用程式磚 ( [windows 次要磚](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) 放在[windows mixed reality 首頁](navigating-the-windows-mixed-reality-home.md)即可。 這些應用程式磚在放置時, 會開始執行應用程式。 這些應用程式磚會保存並保留在放置的位置, 其作用就像是您想要回到應用程式時的啟動器。

![放置會將次要磚放在世界中](images/slide1-600px.png)<br>
*放置會將次要磚放在世界中*

一旦放置完成 (除非[應用程式啟動到應用程式](app-model.md#protocols)啟動的位置), 應用程式就會開始啟動。 Windows Mixed Reality 一次只能執行有限數量的應用程式。 當您放置並啟動應用程式時, 其他作用中的應用程式可能會暫停, 並在您放置應用程式時, 在應用程式磚上留下應用程式最後狀態的螢幕擷取畫面。 如需處理繼續和其他應用程式生命週期事件的詳細資訊, 請參閱[Windows 10 UWP 應用程式生命](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle)週期。

![放置磚之後, 應用程式會開始](images/slide2-500px.png) ![執行中的應用程式狀態圖](images/ic576232-500px.png)<br>
*左方: 放置磚之後, 應用程式會開始執行。Right: 應用程式執行中、已暫止或未執行的狀態圖表。*

### <a name="remove-is-closeterminate-process"></a>移除關閉/終止進程

當您從世界中移除已放置的應用程式磚時, 這會關閉基礎進程。 這有助於確保您的應用程式終止或重新開機有問題的應用程式。

### <a name="app-suspensiontermination"></a>應用程式暫停/終止

在[Windows Mixed Reality 首頁](navigating-the-windows-mixed-reality-home.md)中, 使用者可以為應用程式建立多個進入點。 若要這麼做, 請從 [開始] 功能表啟動您的應用程式, 並將應用程式磚放在世界中。 每個應用程式磚的行為都是不同的進入點, 並在系統中具有個別的磚實例。 針對每個應用程式實例, [FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync)的查詢將會產生**SecondaryTile** 。

當 UWP 應用程式暫停時, 會取得目前狀態的螢幕擷取畫面。

![已暫停的應用程式會顯示幕幕快照](images/slide9-800px.png)<br>
*已暫停的應用程式會顯示幕幕快照*

與其他 Windows 10 shell 的一個主要差異, 在於應用程式如何透過 CoreApplication 來通知應用程式實例啟用。正在[繼續](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming)和[CoreWindow 已啟用](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated)的事件。

|  狀況 |  繼續  |  已啟動 | 
|----------|----------|----------|
|  從 [開始] 功能表啟動應用程式的新實例  |   |  以新的[TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) **啟用** | 
|  從 [開始] 功能表啟動應用程式的第二個實例  |   |  以新的**TileId** **啟用** | 
|  選取目前不在使用中的應用程式實例  |   |  以與實例相關聯的**TileId** **啟用** | 
|  選取不同的應用程式, 然後選取先前使用中的實例  |  **繼續**引發  |  | 
|  選取不同的應用程式, 然後選取先前非使用中的實例  |  **繼續**引發  |  然後使用與實例相關聯的**TileId**來**啟用** | 

### <a name="extended-execution"></a>擴充執行

有時候, 您的應用程式需要在背景中繼續執行工作或播放音訊。 [背景](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest)工作可在 HoloLens 上取得。

![應用程式可以在背景中執行](images/slide10-800px.png)<br>
*應用程式可以在背景中執行*

## <a name="app-views"></a>應用程式檢視

當您的應用程式啟動時, 您可以選擇您想要顯示的檢視類型。 針對應用程式的**CoreApplication**, 一律會有一個主要的[應用程式視圖](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView), 以及您想要建立的任意數目的應用程式。 在桌面上, 您可以將應用程式視圖視為視窗。 我們的混合現實應用程式範本會建立一個 Unity 專案, 其中主要應用程式是[沉浸式](app-views.md)的。 

您的應用程式可以使用 XAML 之類的技術來建立其他2D 應用程式視圖, 以使用 Windows 10 的功能, 例如應用程式內購買。 如果您的應用程式是以適用于其他 Windows 10 裝置的 UWP 應用程式啟動, 主要視圖會是 2D, 但您可以新增額外的應用程式視圖來顯示 volumetrically 體驗, 以「在混合現實中」進行「亮」。 想像一下在 XAML 中建立相片檢視器應用程式, 其中的投影片按鈕切換到沉浸式應用程式視圖, 從世界各地的應用程式 flew 相片。

![執行中的應用程式可以有2D 視圖或沉浸式視圖](images/slide3-800px.png)<br>
*執行中的應用程式可以有2D 視圖或沉浸式視圖*

### <a name="creating-an-immersive-view"></a>建立沉浸式視圖

混合現實應用程式是建立沉浸式視圖的人, 這是使用[HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace)類型來達成的。

純粹是沉浸式的應用程式應該一律在啟動時建立沉浸式視圖, 即使是從桌面上啟動也一樣。 沉浸式視圖一律會顯示在耳機中, 不論其建立位置為何。 啟用沉浸式視圖會顯示混合現實入口網站, 並引導使用者放在其頭戴式裝置上。

在桌面監視器上以2D 視圖開始的應用程式, 可能會建立次要的沉浸式視圖, 以在頭戴式裝置上顯示內容。 其中一個範例是監視器上的2D 邊緣視窗, 在耳機中顯示360度的影片。

![在沉浸式視圖中執行的應用程式是唯一可見的](images/slide4-800px.png)<br>
*在沉浸式視圖中執行的應用程式是唯一可見的*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 首頁中的2D 視圖

沉浸式視圖以外的任何專案都會轉譯為您世界中的2D 視圖。

應用程式在桌上型電腦監視器和頭戴式裝置上可能會有 2D views。 請注意, 新的2D 視圖會放在與建立它的視圖相同的 shell 中, 不論是在監視器或頭戴式裝置上。 應用程式或使用者目前無法在混合現實首頁和監視器之間移動2D 視圖。

![在2D 視圖中執行的應用程式會與其他應用程式共用混合世界中的空間](images/slide5-800px.png)<br>
*在2D 視圖中執行的應用程式會與其他應用程式共用空間*

### <a name="placement-of-additional-app-tiles"></a>其他應用程式磚的位置

您可以視需要使用[次要磚 api](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles), 將多個應用程式與2d 視圖放在世界各地。 這些「釘選」圖格會顯示為使用者必須放置的啟動顯示畫面, 之後可以用來啟動您的應用程式。 Windows Mixed Reality 目前不支援將任何2D 磚內容轉譯為動態磚。

![應用程式可以使用次要磚來進行多個放置](images/slide6-800px.png)<br>
*應用程式可以使用次要磚來進行多個放置*

### <a name="switching-views"></a>切換視圖

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>從 2D XAML 視圖切換至沉浸式視圖

如果應用程式使用 XAML, 則 XAML [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource)會控制應用程式的第一個視圖。 應用程式必須在啟用**CoreWindow**之前切換至沉浸式視圖, 以確保應用程式能直接啟動到沉浸式體驗。

使用[CoreApplication. CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_)和[ApplicationViewSwitcher](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) , 使其成為使用中的視圖。

> [!NOTE]
>* 從 XAML 視圖切換至沉浸式視圖時, 請勿指定**SwitchAsync**的[ApplicationViewSwitchingOptions ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions)旗標, 或是啟動應用程式的平板電腦將會從世界各地移除。
>* **SwitchAsync**應該使用與您要切換的視圖相關聯的[發送器](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher)來呼叫。
>* 如果您需要啟動虛擬鍵盤或想要啟用另一個應用程式, 您必須**SwitchAsync**回到 XAML 視圖。

![當應用程式進入沉浸式視圖、混合](images/slide7-600px.png)世界和其他應用程式消失時, 應用程式可以在2d 視圖和沉浸式視圖![之間切換](images/slide8-600px.png)<br>
*Left: 應用程式可以在2D 視圖和沉浸式視圖之間切換。Right: 當應用程式進入沉浸式流覽時, Windows Mixed Reality 首頁和其他應用程式會消失。*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>從沉浸式視圖切換回鍵盤 XAML 視圖

在 views 之間來回切換的其中一個常見原因是在混合現實應用程式中顯示鍵盤。 只有當應用程式顯示2D 視圖時, shell 才能夠顯示系統鍵盤。 如果應用程式需要取得文字輸入, 它可能會提供具有文字輸入欄位的自訂 XAML 視圖, 並切換到它, 然後在輸入完成後切換回來。

如上一節所示, 您可以使用**ApplicationViewSwitcher**從您的沉浸式視圖轉換回 XAML 視圖。

## <a name="app-size"></a>應用程式大小

2D 應用程式視圖一律會出現在固定的虛擬平板電腦中。 如此一來, 所有2D 視圖都會顯示完全相同的內容數量。 以下是應用程式2D 視圖大小的一些進一步詳細資料:
* 應用程式的外觀比例會在調整大小時保留。
* 應用程式[解析和縮放比例](building-2d-apps.md#2d-app-view-resolution-and-scale-factor)不會因調整大小而變更。
* 應用程式無法查詢其在世界中的實際大小。

![2D 應用程式會以固定的視窗大小顯示](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*具有2D 視圖的應用程式會以固定視窗大小顯示*

## <a name="app-tiles"></a>應用程式磚

[開始] 功能表使用 [標準] 小磚和 [中] 磚的 [圖釘] 和 [**所有應用程式**] 清單 (混合現實)。 

![Windows Mixed Reality 的 [開始] 功能表](images/start-500px.png)<br>
*Windows Mixed Reality 的 [開始] 功能表*

## <a name="app-to-app-interactions"></a>應用程式與應用程式互動

當您建立應用程式時, 您可以存取 Windows 10 上可用的應用程式通訊機制的豐富應用程式。 許多新的通訊協定 Api 和檔案註冊在 HoloLens 上都能順利運作, 以啟用應用程式的啟動和通訊。 

請注意, 針對桌面耳機, 與指定的副檔名或通訊協定相關聯的應用程式, 可能是只能出現在桌面監視器或桌面平板電腦上的 Win32 應用程式。

### <a name="protocols"></a>通訊協定

HoloLens 支援透過[Windows 啟動器 api](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)啟動應用程式。

當您啟動另一個應用程式時, 需要考慮下列事項:

* 執行非強制回應啟動時 (例如[LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)), 使用者必須先放置應用程式, 才能與它互動。

* 當執行強制回應啟動時 (例如透過[LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)), 強制回應應用程式會放在視窗頂端。

* Windows Mixed Reality 無法將應用程式與獨佔視圖重迭。 為了顯示已啟動的應用程式, Windows 會讓使用者回到世界, 以顯示應用程式。

### <a name="file-pickers"></a>檔案選擇器

HoloLens 同時支援[FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker)和[FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker)合約。 不過, 並沒有預先安裝的應用程式可滿足檔案選擇器合約。 例如, 您可以從 Microsoft Store 安裝這些應用程式-OneDrive。

如果您已安裝多個檔案選擇器應用程式, 您將不會看到任何去除去除的 UI, 以選擇要啟動的應用程式;相反地, 會選擇第一個安裝的檔案選擇器。 儲存檔案時, 會產生包含時間戳記的檔案名。 這無法由使用者變更。

根據預設, 本機支援下列延伸模組:

|  App  |  延伸模組 | 
|----------|----------|
|  相片  |  bmp、gif、jpg、png、avi、mov、.wmv、wmv | 
|  Microsoft Edge  |  htm、html、pdf、svg、xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>應用程式合約和 Windows Mixed Reality 延伸模組

應用程式合約和擴充點可讓您註冊應用程式, 以利用更深入的作業系統功能, 例如處理副檔名或使用背景工作。 這是 HoloLens 上支援和不支援的合約和擴充點的清單。

|  合約或分機  |  支援? | 
|----------|----------|
| [帳戶圖片提供者 (延伸模組)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | 不支援 | 
| [報警](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | 不支援 | 
| [App service](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | 支援但未完全正常運作 | 
| [約會提供者](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | 不支援 | 
| [自動播放 (延伸)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | 不支援 | 
| [背景工作 (延伸模組)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | 部分支援 (並非所有觸發程式都能正常執行) | 
| [更新工作 (延伸模組)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | 支援 | 
| [快取檔案更新程式合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | 支援 | 
| [相機設定 (延伸模組)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | 不支援 | 
| [撥號通訊協定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | 不支援 | 
| [檔案啟用 (副檔名)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | 支援 | 
| [檔案開啟選擇器合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | 支援 | 
| [檔案儲存選擇器合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | 支援 | 
| [鎖定畫面呼叫](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | 不支援 | 
| [媒體播放](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | 不支援 | 
| [播放至合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | 不支援 | 
| [預先安裝的設定工作](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | 不支援 | 
| [列印3D 工作流程](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | 支援 | 
| [列印工作設定 (延伸)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | 不支援 | 
| [URI 啟用 (延伸模組)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | 支援 | 
| [限制啟動](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | 不支援 | 
| [搜尋合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | 不支援 | 
| [設定合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | 不支援 | 
| [共用合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | 不支援 | 
| [SSL/憑證 (延伸模組)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | 支援 | 
| [Web 帳戶提供者](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | 支援 | 

## <a name="app-file-storage"></a>應用程式檔儲存體

所有存放裝置都是透過[Windows. storage 命名空間](https://docs.microsoft.com/uwp/api/Windows.Storage)。 如需詳細資訊, 請參閱下列檔。 HoloLens 不支援應用程式儲存體同步處理/漫遊。

* [檔案、資料夾和媒體櫃](https://docs.microsoft.com/windows/uwp/files/index)
* [儲存及擷取設定和其他應用程式資料](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>已知的資料夾

如需 UWP 應用程式的完整詳細資料, 請參閱[knownfolders.h 檔案](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders)。

<table>
<tr>
<th> 屬性</th><th> 支援 HoloLens</th><th> 沉浸式耳機支援</th><th> 描述</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得應用程式的 [捕捉] 資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得相機翻轉資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得文件庫。 文件庫並非供一般用途使用。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得音樂媒體櫃。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得物件3D 資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得圖片媒體櫃。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">清單</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得播放清單資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得 [已儲存的圖片] 資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得影片媒體櫃。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">家庭</a></td><td></td><td style="text-align: center;">✔️</td><td>取得 [家庭] 資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>取得媒體伺服器 (數位生活網路聯盟 (DLNA)) 裝置的資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>取得錄製的呼叫資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>取得「卸載式裝置」資料夾。</td>
</tr>
</table>

## <a name="app-package"></a>應用程式套件

在 Windows 10 中, 您不再以作業系統為目標, 而是將[應用程式的目標設為一或多個裝置系列](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families)。 裝置系列會識別 API、系統特性以及您對於裝置系列中的裝置可以預期的行為。 它也會決定您的應用程式可以從[Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)安裝的裝置集合。

* 若要以桌上型耳機和 HoloLens 作為目標, 請將您的應用程式目標設為**Windows 通用**裝置系列。
* 若只要以桌面耳機作為目標, 請將您的應用程式目標設為**Windows 桌面**裝置系列。
* 若只要以 HoloLens 作為目標, 請將您的應用程式設為**Windows**全像攝影裝置系列。

## <a name="see-also"></a>另請參閱

* [應用程式檢視](app-views.md)
* [更新混合實境的 2D UWP 應用程式](building-2d-apps.md)
* [3D 應用程式啟動程式設計指引](3d-app-launcher-design-guidance.md)
* [執行3D 應用程式啟動器](implementing-3d-app-launchers.md)
