---
title: 更新適用于混合現實的 2D UWP 應用程式
description: 本文概述如何更新您現有的2D 通用 Windows 平臺應用程式，以在 HoloLens 和 Windows Mixed Reality 沉浸式耳機上執行。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 應用程式，UWP，一般應用程式，HoloLens，沉浸式耳機，應用程式型號，上一頁按鈕，應用程式行，DPI，解析度，調整
ms.openlocfilehash: 46d2a9ca044dee977faecc84d610dc0811a4bfb7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436972"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>更新適用于混合現實的 2D UWP 應用程式

Windows Mixed Reality 可讓使用者在您的實體或數位世界中，看到像是您一樣的全息影像。 在其核心中，HoloLens 和您附加了沉浸式耳機配件的桌上型電腦都是 Windows 10 裝置;這表示您可以在存放區中執行幾乎所有的通用 Windows 平臺（UWP）應用程式，做為2D 應用程式。

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>建立適用于混合現實的 2D UWP 應用程式

將2D 應用程式帶入混合現實耳機的第一個步驟，是讓您的應用程式在桌面監視器上以標準2D 應用程式的形式執行。

### <a name="building-a-new-2d-uwp-app"></a>建立新的 2D UWP 應用程式

若要建立混合現實的新2D 應用程式，您只需要建立標準2D 通用 Windows 平臺（UWP）應用程式。 該應用程式不需要進行任何其他應用程式變更，就能在混合現實中以平板電腦的形式執行。

若要開始建立 2D UWP 應用程式，請參閱[建立您的第一個應用程式一](https://docs.microsoft.com/windows/uwp/get-started/your-first-app)文。

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>將現有的2D 存放區應用程式帶入 UWP

如果您在存放區中已經有 2D Windows 應用程式，您必須先確定它是以 Windows 10 通用 Windows 平臺（UWP）為目標。 以下是您目前的商店應用程式可能會遇到的所有潛在起點：
<br>

|  起始點  |  AppX 資訊清單平臺目標  |  如何讓此通用？ | 
|----------|----------|----------|
|  Windows Phone （Silverlight）  |  Silverlight 應用程式資訊清單 |  [遷移至 WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 通用  |  8.1 AppX 資訊清單，不包含平臺目標  |  [將您的應用程式遷移至通用 Windows 平臺](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8  |  8個不包含平臺目標的 AppX 資訊清單  |  [將您的應用程式遷移至通用 Windows 平臺](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows Store 8.1 通用  |  8.1 AppX 資訊清單，不包含平臺目標  |  [將您的應用程式遷移至通用 Windows 平臺](https://msdn.microsoft.com/library/mt148501.aspx) | 

如果您目前已將 2D Unity 應用程式建立為 Win32 應用程式（「電腦、Mac & Linux 獨立」組建目標），您可以改為將 Unity 切換為 "通用 Windows 平臺" 組建目標，以混合現實的目標。

我們將討論您可以使用[下面](#publish-and-maintain-your-universal-app)的 Windows 全像攝影裝置系列，將您的應用程式明確地限制在 HoloLens 上的方式。

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>在 Windows Mixed Reality 沉浸式耳機中執行2D 應用程式

如果您已將2D 應用程式部署到您正在開發的桌上型電腦，並在您的監視器上嘗試它，您就已經準備好在沉浸式桌面耳機中試用！

只要移至混合現實耳機內的 [開始] 功能表，即可從該處啟動應用程式。 桌面 shell 和全像攝影介面皆共用相同的 UWP 應用程式集，因此當您從 Visual Studio 部署之後，應用程式應該已經存在。

## <a name="targeting-both-immersive-headsets-and-hololens"></a>以沉浸式耳機和 HoloLens 為目標

恭喜！ 您的應用程式現在正在使用 Windows 10 通用 Windows 平臺（UWP）。

您的應用程式現在能夠在現今的 Windows 裝置上執行，例如桌上型電腦、行動裝置、Xbox、Windows Mixed Reality 沉浸式耳機和 HoloLens，以及未來的 Windows 裝置。 不過，若要實際以這些裝置為目標，您必須確定應用程式的目標為 Windows 通用裝置系列。

### <a name="change-your-device-family-to-windowsuniversal"></a>將您的裝置系列變更為 Windows. 通用

現在，讓我們跳到您的 AppX 資訊清單，以確保您的 Windows 10 UWP 應用程式可以在 HoloLens 上執行：
* 使用**Visual Studio**開啟應用程式的方案檔，然後流覽至應用程式套件資訊清單
* 以滑鼠右鍵按一下方案中的**package.appxmanifest.xml**檔案，然後移至 [**查看程式碼**]<br>
  方案總管中的 ![package.appxmanifest.xml](images/openappxmanifest-500px.png)<br>
* 確定您的目標平臺是 [相依性] 區段中的 [通用]
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* 另!

如果您未在開發環境中使用 Visual Studio，您可以在您選擇的文字編輯器中開啟**package.appxmanifest.xml** ，以確保您的目標是**Windows. 通用** *y*。

### <a name="run-in-the-hololens-emulator"></a>在 HoloLens 模擬器中執行

現在，您的 UWP 應用程式以 "Windows. 通用" 為目標，讓我們建立您的應用程式，並在[HoloLens 模擬器](using-the-hololens-emulator.md)中執行。
* 請確定您已[安裝 HoloLens 模擬器](install-the-tools.md)。
* 在 Visual Studio 中，選取您應用程式的**x86**組建設定

  ![Visual Studio 中的 x86 組建設定](images/x86setting.png)<br>
* 在 [部署目標] 下拉式功能表中選取 [ **HoloLens 模擬器**]

  ![部署目標清單中的 HoloLens 模擬器](images/deployemulator-500px.png)<br>
* 選取 [ **Debug > 開始進行調試**程式] 以部署您的應用程式並開始進行偵錯工具。
* 模擬器會啟動並執行您的應用程式。
* 使用鍵盤、滑鼠和/或 Xbox controller，將您的應用程式放在世界中以啟動它。

  ![已載入 UWP 範例的 HoloLens 模擬器](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>後續步驟

此時，可能會發生下列其中一種情況：
1. 您的應用程式會在放置於模擬器之後，顯示其啟動狀態並開始執行！ 絕佳!
2. 或者，在您看到2D 全息式的載入動畫之後，載入將會停止，而您只會在其啟動顯示畫面中看到您的應用程式。 這表示發生錯誤，而且會進行更多調查，以瞭解如何讓您的應用程式在混合現實中運作。

若要取得可能導致 UWP 應用程式無法在 HoloLens 上啟動的原因，您必須進行 debug。

### <a name="running-your-uwp-app-in-the-debugger"></a>在偵錯工具中執行 UWP 應用程式

這些步驟將逐步引導您使用 Visual Studio 偵錯工具來偵測 UWP 應用程式。
* 如果您尚未這麼做，請在 Visual Studio 中開啟您的方案。 將目標變更為**HoloLens 模擬器**和組建設定為**x86**。
* 選取 [ **Debug > 開始進行調試**程式] 以部署您的應用程式並開始進行偵錯工具。
* 使用您的滑鼠、鍵盤或 Xbox 控制器將應用程式放在世界各地。
* Visual Studio 現在應該會在應用程式程式碼中的某處中斷。
  - 如果您的應用程式不會因為發生未處理的錯誤而立即損毀或中斷偵錯工具，請執行應用程式核心功能的測試階段，以確定所有專案都在執行中且正常運作。 您可能會看到如下圖所示的錯誤（正在處理的內部例外狀況）。 為確保您不會錯過會影響應用程式體驗的內部錯誤，請執行自動化測試和單元測試，以確定所有專案都會如預期般運作。

![已載入具有 UWP 範例的 HoloLens 模擬器，顯示系統例外狀況](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>更新您的 UI

現在，您的 UWP 應用程式是以2D 全息式的耳機和/或 HoloLens 的形式執行，接下來我們要確定它看起來美觀。 以下是一些要考慮的事項：
* Windows Mixed Reality 會以固定解析度和 DPI （等同于853x480 有效圖元）來執行所有2D 應用程式。 請考慮您的設計是否需要調整規模，並回顧下面的設計指引，以改善 HoloLens 和沉浸式耳機的體驗。
* Windows Mixed Reality 不[支援](app-model.md)2d 動態磚。 如果您的核心功能顯示動態磚上的資訊，請考慮將該資訊移回您的應用程式，或探索[3d 應用程式啟動器](3d-app-launcher-design-guidance.md)。

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D 應用程式視圖解析度和縮放比例

![從回應式設計](images/scale-500px.png)

Windows 10 會將所有視覺化設計從真實的螢幕圖元移到**有效的圖元**。 這表示，開發人員會遵循 Windows 10 人力介面指導方針來設計其 UI 以取得有效的圖元，而 Windows 調整可確保這些有效圖元的大小適合跨裝置、解析度、DPI 等的可用性。如需深入瞭解和此[組建簡報](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)，請參閱[MSDN 上的這篇絕佳的閱讀](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)。

即使是將應用程式放在世界各地的獨特功能，也建議使用類似電視的視圖距離，以產生最佳的可讀性，並與注視/手勢互動。 因此，混合現實家中的虛擬平板電腦會顯示您的一般 UWP 視圖，網址為：

**1280x720，150% DPI** （853x480 有效圖元）

此解決方案有幾個優點：
* 這種有效的圖元版面配置與平板電腦或小型桌面的資訊密度相同。
* 它會比對在 Xbox One 上執行之 UWP 應用程式的固定 DPI 和有效圖元，讓裝置之間的順暢體驗。
* 在世界各地應用程式的營運距離範圍內調整時，此大小看起來很好。

### <a name="2d-app-view-interface-design-best-practices"></a>2D 應用程式視圖介面設計最佳做法

**對**
* 遵循[Windows 10 人力介面指導方針（HIG）](https://dev.windows.com/design)以取得樣式、字型大小和按鈕大小。 HoloLens 會執行工作，以確保您的應用程式會有相容的應用程式模式、可讀取的文字大小，以及適當的點擊目標大小。
* 請確定您的 UI 遵循最佳做法，讓[回應式設計](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)在 HoloLen 的獨特解析度和 DPI 上的外觀最佳。
* 使用 Windows 的「淺色」色彩主題建議。

**不要：**
* 在混合的現實中，變更您的 UI 太大，以確保使用者在耳機中有熟悉的體驗。

### <a name="understand-the-app-model"></a>瞭解應用程式模型

混合式現實的[應用程式模型](app-model.md)是設計用來使用混合現實首頁，其中許多應用程式都在一起運作。 請將此視為桌上型電腦的混合現實，您可以在其中一次執行許多2D 應用程式。 這對應用程式的生命週期、磚和其他主要功能有一些影響。

### <a name="app-bar-and-back-button"></a>[應用程式行] 和 [上一頁] 按鈕

2D 視圖會使用其內容上方的應用程式行裝飾。 應用程式行有兩個應用程式專屬個人化的點：

**標題：** 顯示與應用程式實例相關聯之磚的*displayname*

**上一頁按鈕：** 當按下時，會引發 *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 事件。 [上一頁] 按鈕可見度是由 *[SystemNavigationManager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* 所控制。

![2D 應用程式視圖中的應用程式行 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*2D 應用程式視圖中的應用程式行 UI*

### <a name="test-your-2d-apps-design"></a>測試您的2D 應用程式設計

請務必測試您的應用程式，以確定文字可供讀取、按鈕為目標設為，且整體應用程式看起來是正確的。 您可以在桌面耳機、HoloLens、模擬器或將解析度設定為 1280x720 % 的觸控裝置上進行[測試](testing-your-app-on-hololens.md)。

## <a name="new-input-possibilities"></a>新的輸入可能性

HoloLens 使用先進的深度感應器來查看世界並查看使用者。 這可啟用先進的手勢，例如[bloom](system-gesture.md#bloom)和[空中碰](gaze-and-commit.md#composite-gestures)。 強大的麥克風也可以提供[語音體驗](voice-input.md)。

使用桌面耳機時，使用者可以使用動作控制器來指向應用程式並採取動作。 他們也可以使用遊戲台，以物件與其注視的目標。

Windows 會負責 UWP 應用程式的所有這項複雜性，將您的[注視](gaze-and-commit.md)、手勢、語音和動作控制器輸入，轉譯為會抽象化輸入機制的[指標事件](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)。 例如，使用者可能已在動作控制器上使用手或拉出選取觸發程式，但2D 應用程式不需要知道輸入來自何處-它們只會看到2D 觸控按，如同在觸控式螢幕上一樣。

以下是將 UWP 應用程式帶入 HoloLens 時，您應該瞭解的高階概念/案例：
* [看一下](gaze-and-commit.md)暫留事件, 這可能會非預期地觸發功能表、flyouts 或其他使用者介面元素, 只要撥雲見日應用程式就能快顯。
* 注視並不像滑鼠輸入一樣精確。 針對 HoloLens 使用適當大小的叫用目標，類似于觸控式行動裝置應用程式。 接近應用程式邊緣的小型元素尤其難以與互動。
* 使用者必須將輸入模式切換成從滾動拖曳至兩個手指移動。 如果您的應用程式是針對觸控輸入而設計，請考慮確保不會在兩個手指移動後鎖定任何主要功能。 若是如此，請考慮具有替代的輸入機制，例如可以起始兩個手指移動的按鈕。 例如，地圖應用程式可以使用兩個手指移動來縮放，但有一個加號、減號和旋轉按鈕，可透過按一下來模擬相同的縮放互動。

[語音輸入](voice-input.md)是混合現實體驗的重要部分。 我們已在使用耳機時，啟用 Windows 10 中的所有語音 Api。

## <a name="publish-and-maintain-your-universal-app"></a>發行和維護您的通用應用程式

當您的應用程式啟動並執行之後，請封裝您的應用程式，將[它提交至 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)。

## <a name="see-also"></a>另請參閱
* [應用程式模型](app-model.md)
* [頭部目光和行動](gaze-and-commit.md)
* [運動控制器](motion-controllers.md)
* [語音輸入](voice-input.md)
* [將應用程式提交到 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
