---
title: 更新混合實境的 2D UWP 應用的程式
description: 本文章概述更新您現有 2D 通用 Windows 平台應用程式上執行 HoloLens 與 Windows Mixed Reality 沈浸式耳機。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 應用程式，UWP，一般應用程式、 HoloLens、 沈浸式耳機，應用程式模型後按鈕、 應用程式列、 dpi、 解析，小數位數
ms.openlocfilehash: f9792a7e5fd9729bf9f5f632c699c74c58c10ddf
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414226"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>更新混合實境的 2D UWP 應用的程式

Windows Mixed Reality 可讓使用者查看全像投影，如同它們是右周圍，在您的實體或數位世界。 基本上，HoloLens 和附加沈浸式耳機附屬應用程式，可在桌面電腦是 Windows 10 裝置;這表示您能夠為 2D 應用程式存放區中執行幾乎所有的通用 Windows 平台 (UWP) 應用程式。

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>建立混合實境的 2D UWP 應用程式

2D 應用程式帶入混合的實境耳機的第一個步驟是取得您以標準 2D 應用程式在桌面的監視器上執行的應用程式。

### <a name="building-a-new-2d-uwp-app"></a>建立新的 2D UWP 應用程式

若要建立新的混合實境 2D 應用程式，您只需建置標準的 2D 通用 Windows 平台 (UWP) 應用程式。 接著再執行在混合實境中的 靜態圖像為該應用程式需要任何其他應用程式變更不。

若要開始建置 2D 的 UWP 應用程式，請參閱[建立第一個應用程式](https://docs.microsoft.com/windows/uwp/get-started/your-first-app)文章。

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>將現有的 2D 市集應用程式帶到 UWP

如果您已經有 2D 的 Windows 應用程式存放區中，您必須先確定它設為目標 Windows 10 通用 Windows 平台 (UWP)。 以下是所有可能起始點您可能與您的市集應用程式立即：
<br>

|  起點  |  AppX 資訊清單平台目標  |  若要使此通用如何？ | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight 應用程式資訊清單 |  [將移轉到 WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 通用  |  8.1 AppX 資訊清單不包含平台目標  |  [將您的應用程式移轉至通用 Windows 平台](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 市集 8  |  8 AppX 資訊清單不包含平台目標  |  [將您的應用程式移轉至通用 Windows 平台](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 市集 8.1 通用  |  8.1 AppX 資訊清單不包含平台目標  |  [將您的應用程式移轉至通用 Windows 平台](https://msdn.microsoft.com/library/mt148501.aspx) | 

如果您有立即建置 Win32 應用程式 （"PC、 Mac 和 Linux 單機版 」 組建目標） 為 2D Unity 應用程式時，您可以針對混合的實境，改為切換到 「 通用 Windows 平台 」 建置目標的 Unity。

我們將討論方式，您可以限制您的應用程式是專為使用 Windows.Holographic 裝置家族的 HoloLens[以下](#publish-and-maintain-your-universal-app)。

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>執行 Windows Mixed Reality 沈浸式耳機 2D 應用程式

如果您正在開發並試用您的監視器上桌上型電腦部署了 2D 應用程式之後，您已經準備好要試試看在沉浸式桌面耳機 ！

只要移至混合的實境耳機內的 [開始] 功能表，然後啟動應用程式，從該處。 桌面殼層和全像攝影版的殼層都共用相同一組的 UWP 應用程式，並因此應用程式應該會出現，一旦您從 Visual Studio 部署。

## <a name="targeting-both-immersive-headsets-and-hololens"></a>為目標的沈浸式耳機和 HoloLens

恭喜您！ 您的應用程式正在使用 Windows 10 通用 Windows 平台 (UWP)。

現在能在現今的 Windows 裝置，例如桌面、 行動、 Windows Mixed Reality 沈浸式耳機的 Xbox 和 HoloLens，以及為未來的 Windows 裝置上執行您的應用程式。 不過，若要實際目標的所有這些裝置，您必須確保您的應用程式的目標 Windows.Universal 裝置系列。

### <a name="change-your-device-family-to-windowsuniversal"></a>將您的裝置系列變更為 Windows.Universal

現在讓我們跳到您的 AppX 資訊清單，以確保您的 Windows 10 UWP 應用程式可以執行 HoloLens 上：
* 開啟您的應用程式使用的方案檔**Visual Studio**並瀏覽至應用程式封裝資訊清單
* 以滑鼠右鍵按一下**Package.appxmanifest**檔案中您的解決方案，並移至**檢視程式碼**<br>
  ![在 [方案總管] 中的 package.appxmanifest](images/openappxmanifest-500px.png)<br>
* 請確定您的目標平台 Windows.Universal 相依性一節
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* 儲存 ！

如果您不使用 Visual Studio 開發環境，您可以開啟**AppXManifest.xml**在您的選擇，以確保您設為目標的文字編輯器**Windows.Universal** *TargetDeviceFamily*。

### <a name="run-in-the-hololens-emulator"></a>HoloLens 模擬器中執行

現在，您的 UWP 應用程式目標設為"Windows.Universal"，讓我們來建置您的應用程式，並在執行[HoloLens 模擬器](using-the-hololens-emulator.md)。
* 請確定您已[安裝 HoloLens 模擬器](install-the-tools.md)。
* 在 Visual Studio 中，選取**x86**建置您的應用程式的組態

  ![x86 建置在 Visual Studio 中的組態](images/x86setting.png)<br>
* 選取  **HoloLens 模擬器**部署目標下拉式選單中

  ![部署目標清單中的 HoloLens 模擬器](images/deployemulator-500px.png)<br>
* 選取 **偵錯 > 啟動偵錯**來部署您的應用程式，並開始偵錯。
* 模擬器會啟動，並執行您的應用程式。
* 使用鍵盤、 滑鼠及/或 Xbox 控制器，會將您應用程式世界各地的啟動它。

  ![HoloLens 模擬器載入 UWP 範例](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>後續步驟

此時，會發生下列其中一種：
1. 您的應用程式會顯示其開頭顯示畫面，並啟動之後它會放在模擬器中執行 ！ 好極了 ！
2. 或者，您會看到如 2D 全像載入的動畫後，載入將會停止，而且您將只會看到您的應用程式在其啟動顯示畫面。 這表示發生錯誤，而且需要更多的調查，以了解如何在混合實境中實現您的應用程式。

若要取得的功能可能會導致您的 UWP 應用程式底部不 HoloLens 上啟動，您必須偵錯。

### <a name="running-your-uwp-app-in-the-debugger"></a>在 偵錯工具中執行您的 UWP 應用程式

這些步驟將引導您使用 Visual Studio 偵錯工具的 UWP 應用程式進行偵錯。
* 如果您尚未這麼做，請在 Visual Studio 中開啟的方案。 變更目標，以便**HoloLens 模擬器**和 組建組態設為**x86**。
* 選取 **偵錯 > 啟動偵錯**來部署您的應用程式，並開始偵錯。
* 使用您的滑鼠、 鍵盤或 Xbox 控制器世界中的應用程式的地方。
* Visual Studio 現在應該在應用程式程式碼中某處中斷。
  - 如果您的應用程式不會立即損毀，或偵錯工具中斷，因為發生未處理的錯誤，然後瀏覽您的應用程式，以確定一切都運作和功能的核心功能測試。 您可能會看到錯誤，例如圖 （內部例外狀況處理）。 若要確保您千萬別錯過影響您的應用程式體驗的內部錯誤，執行您的自動化的測試和單元測試，藉此確定一切如預期般運作。

![HoloLens 模擬器載入 UWP 範例顯示系統例外狀況](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>更新您的 UI

現在，您的 UWP 應用程式沈浸式耳機和/或為 2D 雷射 HoloLens 上執行，接下來我們要確定它看起來美觀。 以下是一些考量事項：
* Windows Mixed Reality 會在固定的解析度和 DPI，等同於執行所有的 2D 應用程式以 853 x 480 有效的像素。 請考慮您的設計是否需要以這個規模調整，並檢閱設計指導方針，以改善您 HoloLens 和沈浸式耳機的體驗。
* Windows Mixed Reality[不支援](app-model.md)2D 的動態磚。 如果您的核心功能顯示之動態磚的相關資訊，請考慮將該資訊移回至應用程式，或瀏覽[3D 應用程式啟動器](3d-app-launcher-design-guidance.md)。

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D 應用程式檢視解析度和比例因素

![從 回應式設計](images/scale-500px.png)

Windows 10 從實際螢幕像素為單位來移動所有視覺效果的設計**有效的像素**。 這表示，開發人員設計的 Windows 10 人性化介面指導方針的有效的像素為單位，其 UI 和 Windows 調整這些有效的像素是正確的大小可確保裝置、 裝置解析度、 DPI、 使用性等等。請參閱此[MSDN 上的絕佳讀取](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)若要了解更多，以及這[組建簡報](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)。

即使有獨特的功能的應用程式放在您的世界裡，在一連串的距離，以產生最佳的可讀性和視線/手勢互動建議電視類似檢視的距離。 因此，混合實境在家中的虛擬 slate 將會顯示您在一般的 UWP 檢視：

**1280 x 720，150 %dpi** （853 x 480 有效的像素）

這個解決方案有下列優點：
* 此配置命名為有效的像素會有相關的平板電腦或小型的桌面為相同的資訊密度。
* 它符合固定的 DPI 和 Xbox One 上，啟用順暢的體驗，在裝置上執行的 UWP 應用程式的有效像素。
* 此大小看起來沒問題，當我們的營運的世界中的應用程式的距離範圍擴及相應的。

### <a name="2d-app-view-interface-design-best-practices"></a>2D 應用程式檢視介面設計最佳作法

**執行動作：**
* 請遵循[Windows 10 人性化介面指導方針 (HIG)](https://dev.windows.com/design)樣式、 字型大小和按鈕大小。 HoloLens 會執行工作，以確保您的應用程式會有相容的應用程式模式，可讀取的文字大小，以及適當的叫用的目標調整大小。
* 確保您的 UI 遵循的最佳作法[回應式設計](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)尋找最佳 HoloLen 的唯一的解析度和 DPI。
* 從 Windows 使用的"light"色彩佈景主題的建議。

**沒有此項目：**
* 在混合實境，以確保使用者擁有流入和流出耳機熟悉的體驗也大幅變更您的 UI。

### <a name="understand-the-app-model"></a>了解應用程式模型

[應用程式模型](app-model.md)的混合的實境旨在使用混合實境首頁，許多應用程式一起存放的位置。 把這個想成在桌面對混合的實境等項目在您執行許多的 2D 應用程式一次。 這會影響應用程式生命週期、 圖格和其他重要的功能，您的應用程式。

### <a name="app-bar-and-back-button"></a>應用程式列和上一步按鈕

2D 檢視會附有應用程式列中，其內容上方。 應用程式列中有兩個點的應用程式專屬的個人化：

**標題︰** 會顯示*displayname*應用程式執行個體相關聯的圖格

**上一頁按鈕：** 引發 *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 時按下的事件。 上一步 按鈕的可見性會受到 *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* 。

![應用程式列在 2D 應用程式檢視中的 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*應用程式列在 2D 應用程式檢視中的 UI*

### <a name="test-your-2d-apps-design"></a>測試 2D 應用程式的設計

請務必測試您的應用程式，請確定所讀取的文字、 按鈕會將目標設為，而且將整體應用程式看起來正確無誤。 您可以[測試](testing-your-app-on-hololens.md)桌面耳機、 HoloLens、 模擬器，或觸控裝置解析度設定為 1280 x 720 @150%。

## <a name="new-input-possibilities"></a>新輸入的可能性

HoloLens 使用進階的深度感應器看到世界與使用者。 這可讓進階等手勢[bloom](gestures.md#bloom)並[空中點選](gestures.md#air-tap)。 功能強大的麥克風也可讓[語音體驗](voice-input.md)。

桌面耳機，使用者可以使用動作控制站來指向應用程式，並採取行動。 他們也可以使用遊戲台，以其視線物件為目標。

Windows 會負責針對 UWP 應用程式，此複雜度完全轉譯您[視線](gaze.md)，筆勢，語音和動作的輸入控制器[指標事件](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)，抽離輸入的機制。 例如，使用者可能已完成其手空中點選或提取動作控制站上的 選取的觸發程序但 2D 應用程式不需要知道其中輸入來自-他們只看到 2D 觸控按下時，如同觸控螢幕上的功能。

以下是高階概念/案例 HoloLens 將您的 UWP 應用程式時，您應該瞭解的輸入：
* [視線](gaze.md)變成暫留時的事件，非預期地觸發功能表、 延伸顯示或只要 gazing 您應用程式周圍彈出其他使用者介面項目。
* 視線不精確度可達滑鼠輸入。 使用適當地調整大小的 HoloLens，類似且方便觸控的行動裝置應用程式，叫用的目標。 應用程式的邊緣附近的小項目會特別難互動。
* 使用者必須切換向下捲動到拖曳兩個手指移動瀏覽至從輸入的模式。 如果您的應用程式專為具備觸控輸入，請考慮確保任何重大的功能已被鎖定，後面兩個手指移動瀏覽。 如果是的話，請考慮讓替代的輸入的機制，例如可以初始化兩個手指移動瀏覽 按鈕。 比方說，對應應用程式可以使用兩個手指移動瀏覽顯示比例，但可以加號，減號，而且旋轉來模擬相同縮放互動單一按下滑鼠按鈕。

[語音輸入](voice-input.md)是混合的實境體驗不可或缺的一部分。 我們已啟用所有的語音使用耳機時加強 Cortana 的 Windows 10 中的 Api。

## <a name="publish-and-maintain-your-universal-app"></a>發行及維護您的通用應用程式

您的應用程式啟動並執行之後，封裝您的應用程式[將它提交至 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)。

## <a name="see-also"></a>另請參閱
* [應用程式模型](app-model.md)
* [目光](gaze.md)
* [筆勢](gestures.md)
* [運動控制器](motion-controllers.md)
* [語音輸入](voice-input.md)
* [將應用程式提交到 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
