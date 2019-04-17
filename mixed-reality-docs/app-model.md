---
title: 應用程式模型
description: Windows Mixed Reality 使用通用 Windows 平台、 模型和現代 Windows 應用程式的環境所提供的應用程式模型。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP 應用程式模型、 生命週期、 暫停、 繼續、 圖格、 檢視、 合約
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595857"
---
# <a name="app-model"></a>應用程式模型

Windows Mixed Reality 會使用所提供的應用程式模型[通用 Windows 平台](https://docs.microsoft.com/windows/uwp/get-started/)(UWP)、 模型和現代 Windows 應用程式的環境。 UWP 應用程式模型會定義應用程式的安裝、 更新、 建立版本的方式，並安全地和完全移除。 它會管理應用程式生命週期-如何應用程式執行、 進入睡眠狀態和終止-和它們可以保留狀態的方式。 其中也涵蓋整合以及與作業系統、 檔案和其他應用程式的互動。

![2D 排列在 Windows Mixed Reality 家用早餐區域中的應用程式](images/20160112-055908-hololens-500px.jpg)<br>
*2D 檢視排列在家用的 Windows Mixed Reality 應用程式*

## <a name="app-lifecycle"></a>應用程式週期

Mixed 的 reality 應用程式的生命週期包括標準的應用程式的概念，例如位置、 啟動、 終止和移除。

### <a name="placement-is-launch"></a>放置已啟動

每個應用程式在混合實境中開頭加上應用程式圖格 (剛[Windows 次要磚](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) 中[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)。 這些應用程式圖格上放置的功能，將會開始執行應用程式。 這些應用程式磚保存並保持在放置位置的位置做像啟動器為隨時為您想要回到應用程式。

![位置會置於世界中的次要磚](images/slide1-600px.png)<br>
*位置會置於世界中的次要磚*

一旦完成放置 (除非位置已啟動[即可在應用程式](app-model.md#protocols)啟動)，應用程式開始啟動。 Windows Mixed Reality 可以一次執行為數有限的應用程式。 當您將，並啟動應用程式，其他使用中的應用程式可能暫止，讓其應用程式圖格上的應用程式的最後一個狀態的螢幕擷取畫面，只要將它放。 請參閱[Windows 10 UWP 應用程式生命週期](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle)如需有關處理繼續和其他應用程式生命週期事件。

![將圖格，應用程式會開始執行](images/slide2-500px.png)![執行中、 暫止或未執行的應用程式的狀態圖表](images/ic576232-500px.png)<br>
*左： 圖格後，應用程式會開始執行。執行中、 已擱置，或未執行的應用程式的權限： 狀態圖表。*

### <a name="remove-is-closeterminate-process"></a>移除是關閉/終止程序

當您從世界移除放置的應用程式圖格時，這會關閉基礎的處理程序。 這可以是適用於確保您的應用程式已終止或重新啟動有問題的應用程式。

### <a name="app-suspensiontermination"></a>應用程式暫停/終止

在  [Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)，使用者就可以建立多個應用程式的進入點。 他們這麼做，方法是啟動您的應用程式，從 [開始] 功能表，並置於世界的應用程式磚。 每個應用程式圖格行為會如同其他進入點，並在系統中有個別的圖格的執行個體。 查詢[SecondaryTile.FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync)將會導致**SecondaryTile**每個應用程式執行個體。

UWP 應用程式會暫停，當螢幕擷取畫面會採取的目前狀態。

![螢幕擷取畫面會顯示為已暫停的應用程式](images/slide9-800px.png)<br>
*螢幕擷取畫面會顯示為已暫停的應用程式*

從其他 Windows 10 殼層的一個主要差異是透過應用程式執行個體啟動的應用程式會收到的通知[CoreApplication.Resuming](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming)並[CoreWindow.Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated)事件。

|  狀況 |  繼續  |  已啟動 | 
|----------|----------|----------|
|  啟動應用程式，從 [開始] 功能表的新執行個體  |   |  **啟動**與新[TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  啟動應用程式，從 [開始] 功能表的第二個執行個體  |   |  **啟動**與新**TileId** | 
|  選取的執行個體不是目前作用中的應用程式  |   |  **啟動**具有**TileId**執行個體相關聯 | 
|  選取不同的應用程式，然後選取先前使用的執行個體  |  **繼續**引發  |  | 
|  選取不同的應用程式，然後選取 原本之前非使用中的執行個體  |  **繼續**引發  |  然後**Activated**具有**TileId**執行個體相關聯 | 

### <a name="extended-execution"></a>延伸的執行

有時候您的應用程式必須繼續執行在背景中的工作或播放音訊。 [背景工作](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest)HoloLens 上可用。

![應用程式可以在背景中執行](images/slide10-800px.png)<br>
*應用程式可以在背景中執行*

## <a name="app-views"></a>應用程式檢視

當您的應用程式啟動時，您可以選擇您想要何種檢視來顯示。 應用程式**CoreApplication**，一律會有一個主要[應用程式檢視](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView)以及進一步應用程式檢視，您想要建立的任何數字。 在桌面上，您可以將應用程式檢視做為視窗。 我們的混合的實境應用程式範本建立 Unity 專案的主要應用程式檢視所在[沈浸式](app-views.md)。 

您的應用程式可以建立使用技術，例如 XAML，若要使用 Windows 10 功能，例如應用程式內購買額外的 2D 應用程式檢視。 如果您的應用程式啟動為其他 Windows 10 裝置的 UWP 應用程式，您的主要檢視 2D，但您無法 「 點亮 」 在混合實境中加上額外的應用程式檢視，向體驗 volumetrically 沉浸式。 想像一下建置相片檢視器應用程式中 XAML 投影片放映按鈕切換到從應用程式的相片飛跨全球和介面的沉浸式應用程式檢視的位置。

![2D 檢視或沈浸式檢視，可以有執行中應用程式](images/slide3-800px.png)<br>
*2D 檢視或沈浸式檢視，可以有執行中應用程式*

### <a name="creating-an-immersive-view"></a>建立沉浸式檢視

混合的實境應用程式所建立的沈浸式的檢視，方法是使用[HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace)型別。

即使從桌面啟動，完全沈浸式應用程式應該一律會建立啟動時，沈浸式檢視。 沈浸式檢視一律會顯示在耳機，不論他們所建立的。 啟用的沈浸式檢視，會顯示在混合實境入口網站，並引導使用者置於其耳機。

開始在桌面的監視器上的 2D 檢視應用程式可能會建立次要的沈浸式檢視，以顯示 耳機中的內容。 這個範例是顯示在耳機的 360 度的視訊監視器上的 2D Edge 視窗。

![在沉浸式 檢視中執行的應用程式是唯一一個可見](images/slide4-800px.png)<br>
*沈浸式檢視中執行的應用程式是唯一可見*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>在家用的 Windows Mixed Reality 的 2D 檢視

沈浸式檢視以外的任何項目會轉譯為您的世界中的 2D 檢視。

應用程式可能會有在桌上型監視器和耳機的 2D 檢視。 請注意新的 2D 檢視將會置於相同的殼層，或是建立在監視器上耳機中的檢視。 它不是目前無法用於應用程式或混合實境首頁與監視器之間移動的 2D 檢視使用者。

![在 2D 檢視中執行的應用程式與其他應用程式共用混合的環境中的空間](images/slide5-800px.png)<br>
*在 2D 檢視中執行的應用程式共用空間與其他應用程式*

### <a name="placement-of-additional-app-tiles"></a>其他的應用程式磚的位置

您可以將許多具有 2D 應用程式檢視您的世界中，只要[次要磚 Api](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)。 這些 「 釘選 」 的磚會顯示為啟動顯示畫面中，使用者必須放置，然後稍後可用來啟動您的應用程式。 Windows Mixed Reality 目前不支援任何 2D 圖格的內容轉譯為動態磚。

![應用程式可以有多個位置使用次要磚](images/slide6-800px.png)<br>
*應用程式可以有多個位置使用次要磚*

### <a name="switching-views"></a>切換檢視

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>從 2D 的 [XAML] 檢視切換至沈浸式檢視

如果應用程式使用 XAML，則 XAML [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource)會控制應用程式的第一個檢視。 應用程式需要切換至沈浸式檢視，然後再啟動**CoreWindow**，以確保啟動應用程式，直接將人沉迷的體驗。

使用[CoreApplication.CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_)並[ApplicationViewSwitcher.SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_)得現用檢視表。

> [!NOTE]
>* 未指定[ApplicationViewSwitchingOptions.ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions)旗標設為**SwitchAsync**時從 [XAML] 檢視切換至 [沈浸式] 檢視中或啟動應用程式的 slate 將會移除來自世界。
>* **SwitchAsync**應該使用稱為[發送器](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher)與您想要切換至檢視相關聯。
>* 您必須**SwitchAsync**回到如果您要啟動虛擬鍵盤，或想要啟動另一個應用程式中的 [XAML] 檢視。

![應用程式可以 2D 檢視和檢視之間切換擬真](images/slide7-600px.png)![混合的環境和其他應用程式的應用程式進入的沈浸式檢視，當消失](images/slide8-600px.png)<br>
*Left： 應用程式可以 2D 檢視和沈浸式 檢視之間切換。權限： 應用程式進入的沈浸式檢視，當 Windows Mixed Reality 家庭與其他應用程式將會消失。*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>正在從沈浸式檢視切換回 XAML 檢視的鍵盤

上一步-和-來回切換檢視模式的一個常見原因 mixed 的 reality 應用程式中顯示鍵盤。 殼層才能夠顯示系統鍵盤，如果應用程式會顯示 2D 檢視。 如果應用程式需要取得文字輸入，可能會提供自訂的 [XAML] 檢視的文字輸入欄位、 切換到它，以及再切換回在輸入完成後。

在上一節中，您可以使用像是**ApplicationViewSwitcher.SwitchAsync**轉換回 XAML 檢視從您的沈浸式檢視。

## <a name="app-size"></a>將應用程式大小

2D 應用程式檢視一律會顯示在固定的虛擬 slate。 這可讓所有的 2D 檢視顯示的內容完全相同的量。 以下是一些關於您的應用程式的 2D 檢視的大小的進一步詳細資料：
* 在調整大小時，會保留長寬比，應用程式。
* 應用程式[解析度和比例因素](building-2d-apps.md#2d-app-view-resolution-and-scale-factor)不會變更透過調整大小。
* 應用程式不能查詢其世界中的實際大小。

![2D 應用程式會顯示具有固定的視窗大小](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*應用程式的 2D 檢視會顯示具有固定的視窗大小*

## <a name="app-tiles"></a>應用程式磚

[開始] 功能表使用的標準小型磚和中型磚的 pin 並**所有應用程式**在混合實境中的清單。 

![Windows Mixed Reality 的 [開始] 功能表](images/start-500px.png)<br>
*Windows Mixed Reality 的 [開始] 功能表*

## <a name="app-to-app-interactions"></a>應用程式互動的應用程式

當您建置應用程式時，您會在 Windows 10 上有可用的豐富的應用程式即可在應用程式通訊機制的存取。 許多通訊協定的新 Api 和檔案註冊完美地處理來啟用應用程式啟動和通訊的 HoloLens。 

請注意，在桌面的耳機，針對與指定的檔案副檔名相關聯的應用程式或通訊協定可能只可以出現在桌面的監視器上或在桌面的候選影片中的 Win32 應用程式。

### <a name="protocols"></a>通訊協定

HoloLens 支援即可在應用程式啟動透過[Windows.System.Launcher Api](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)。

有要啟動另一個應用程式時，請考慮一些事項：

* 當進行非強制回應啟動時，這類[LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)，使用者必須將應用程式，然後再與其互動。

* 在執行強制回應啟動時，例如透過[LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)，強制回應的應用程式會放在視窗頂端。

* Windows Mixed Reality 無法覆疊在專屬的檢視上的應用程式。 若要顯示啟動的應用程式，Windows 會將使用者帶回至世界各地的顯示應用程式。

### <a name="file-pickers"></a>檔案選擇器

同時支援 HoloLens [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker)並[FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker)合約。 不過，沒有任何應用程式已預先安裝，可滿足檔案選擇器協定。 這些應用程式-例如 OneDrive-可以從 Microsoft Store 安裝。

如果您有一個以上的檔案選擇器應用程式，安裝時，您不會看到任何含意清楚 UI 選擇哪些應用程式，以啟動;相反地，將會選擇第一個安裝的檔案選擇器。 當儲存檔案，檔名會產生包括時間戳記。 無法變更此使用者。

根據預設，下列延伸模組支援本機：

|  應用程式  |  延伸模組 | 
|----------|----------|
|  相片  |  bmp、 gif、 jpg、 png、 avi、 mov、 mp4、 wmv | 
|  Microsoft Edge  |  htm、 html、 pdf、 svg、 xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>應用程式協定與 Windows Mixed Reality 延伸模組

應用程式協定與延伸點可讓您註冊應用程式以充分利用更深入的作業系統功能，例如處理檔案延伸模組，或使用背景工作。 這是一份支援和不支援合約和 HoloLens 上的擴充點。

|  合約或延伸模組  |  支援？ | 
|----------|----------|
| [帳戶圖片提供者 （擴充）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | 不支援 | 
| [Alarm](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | 不支援 | 
| [應用程式服務](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | 支援，但不是完全正常運作 | 
| [約會提供者](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | 不支援 | 
| [[自動播放] （擴充）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | 不支援 | 
| [背景工作 （擴充）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | 部分支援 （並非所有工作觸發程序） | 
| [更新工作 （擴充）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | 支援 | 
| [快取的檔案更新程式合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | 支援 | 
| [照相機設定 （擴充）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | 不支援 | 
| [撥號通訊協定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | 不支援 | 
| [檔案啟用 （擴充）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | 支援 | 
| [檔案開啟選擇器合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | 支援 | 
| [檔案儲存選擇器合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | 支援 | 
| [鎖定畫面呼叫](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | 不支援 | 
| [媒體播放](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | 不支援 | 
| [播放至合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | 不支援 | 
| [預先安裝的組態工作](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | 不支援 | 
| [列印 3D 工作流程](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | 支援 | 
| [列印工作設定 （擴充）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | 不支援 | 
| [URI 啟用 （擴充）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | 支援 | 
| [受限制的啟動](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | 不支援 | 
| [搜尋合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | 不支援 | 
| [設定合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | 不支援 | 
| [共用合約](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | 不支援 | 
| [SSL 憑證 （副檔名）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | 支援 | 
| [Web 帳戶提供者](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | 支援 | 

## <a name="app-file-storage"></a>應用程式檔案儲存體

所有存放裝置是透過[Windows.Storage 命名空間](https://docs.microsoft.com/uwp/api/Windows.Storage)。 請參閱下列文件，如需詳細資訊。 HoloLens 不支援應用程式儲存體同步處理/漫遊。

* [檔案、資料夾和媒體櫃](https://docs.microsoft.com/windows/uwp/files/index)
* [儲存和擷取設定和其他應用程式資料](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>已知的資料夾

請參閱[KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) UWP 應用程式的完整詳細資料。

<table>
<tr>
<th> 屬性</th><th> HoloLens 上支援</th><th> 支援的沈浸式耳機</th><th> 描述</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得應用程式可擷取 資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得的相機相簿的資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得文件庫。 文件庫的目的不是一般用途。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得 音樂媒體櫃。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得物件的 3D 資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得圖片媒體櫃。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">播放清單</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得的播放清單的資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得儲存的圖片 資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得視訊媒體櫃。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">HomeGroup</a></td><td></td><td style="text-align: center;">✔️</td><td>取得 [HomeGroup] 資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>取得媒體的資料夾 (數位生活網路聯盟 (DLNA)) 伺服器裝置。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>取得錄製的通話資料夾。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>取得卸除式裝置 資料夾。</td>
</tr>
</table>

## <a name="app-package"></a>應用程式套件

與 Windows 10 不會再目標作業系統而[目標應用程式以一或多個裝置系列](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families)。 裝置系列會識別 API、系統特性以及您對於裝置系列中的裝置可以預期的行為。 它也會決定一組可以從安裝您的應用程式所在的裝置[Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)。

* 若要桌面耳機和 HoloLens 為目標，您的應用程式的目標**Windows.Universal**裝置系列。
* 若要目標只是桌上型電腦的耳機，您的應用程式的目標**Windows.Desktop**裝置系列。
* 若要目標只是 HoloLens，您的應用程式的目標**Windows.Holographic**裝置系列。

## <a name="see-also"></a>另請參閱

* [應用程式檢視](app-views.md)
* [更新混合實境的 2D UWP 應用的程式](building-2d-apps.md)
* [3D 應用程式啟動程式的設計指引](3d-app-launcher-design-guidance.md)
* [實作的 3D 應用程式啟動器](implementing-3d-app-launchers.md)
