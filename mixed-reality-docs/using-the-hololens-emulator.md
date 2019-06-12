---
title: 使用 HoloLens 模擬器
description: HoloLens 模擬器可讓您在沒有實體 HoloLens 的電腦上測試混合實境應用程式。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, 模擬器
ms.openlocfilehash: 0dfca73e6c8e1809e1bea3df6ca344b3de0698d5
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730914"
---
# <a name="using-the-hololens-emulator"></a>使用 HoloLens 模擬器

HoloLens 模擬器可讓您在沒有實體 HoloLens 的電腦上測試全像攝影應用程式，且隨附 HoloLens 開發工具組。 模擬器會使用 Hyper-V 虛擬機器。 通常會由 HoloLens 上的感應器讀取的人類和環境輸入，改為使用鍵盤、滑鼠或 Xbox 控制器來模擬。 應用程式不需要經過修改就能在模擬器上執行，而且也不知道其並非在真實的 HoloLens 上執行。

如果您想要開發適用於桌上型電腦的 Windows Mixed Reality 沈浸式 (VR) 頭戴式裝置應用程式或遊戲，請參閱 [Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)，其可讓您改為模擬桌上型電腦頭的戴式裝置。


## <a name="installing-the-hololens-emulator"></a>安裝 HoloLens 模擬器
下載 HoloLens 模擬器和全像攝影專案範本。

版本： 
* [HoloLens 2 模擬器和全像攝影專案範本](https://go.microsoft.com/fwlink/?linkid=2087187)。
* [HoloLens 模擬器 (第 1 代) 和全像攝影專案範本](https://go.microsoft.com/fwlink/?linkid=2065980)。

您可以在 [HoloLens 模擬器封存](hololens-emulator-archive.md)頁面上找到 HoloLens 模擬器的舊版組建。

### <a name="hololens-emulator-system-requirements"></a>HoloLens 模擬器的系統需求

HoloLens 模擬器會使用 Hyper-V 與 RemoteFx (第 1 代模擬器) 或 GPU-PV (HoloLens 2 模擬器) 來提供硬體加速圖形。 若要使用模擬器，請確定您的電腦符合下列硬體需求：
* 64 位元 Windows 10 專業版、企業版或教育版 
    >[!NOTE]
    >Windows 10 家用版不支援 Hyper-V 或 HoloLens 模擬器。  
    >HoloLens 2 模擬器需要 Windows 10 2018 年 10 月更新或更新版本。
* 64 位元 CPU
* 4 核心 CPU (或有多個 CPU，且總共有 4 個核心)
* 8 GB RAM 或更多
* BIOS 必須[支援並啟用](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx)下列功能：
   * 硬體協助虛擬化
   * 第二層位址轉譯 (SLAT)
   * 硬體型資料執行防止 (DEP)。
* GPU 需求
   * DirectX 11.0 或更新版本
   * WDDM 1.2 圖形驅動程式或更新版本 (第 1 代)
   * WDDM 2.5 圖形驅動程式 (HoloLens 2 模擬器)
   * 模擬器可與不支援的 GPU 搭配運作，但速度會明顯變慢

如果您的系統符合上述需求，**請確定該系統上已啟用「Hyper-V」功能**，方法是透過 [控制台] -> [程式] -> [程式和功能] -> [開啟或關閉 Windows 功能] -> 確定「Hyper-V」已選取以便能成功安裝模擬器。

## <a name="deploying-apps-to-the-hololens-emulator"></a>將應用程式部署至 HoloLens 模擬器

1. 在 Visual Studio 中載入您的應用程式解決方案。
    >[!NOTE]
    >在使用 Unity 時，請從 Unity 建置專案，然後如往常般將建置好的解決方案載入至 Visual Studio。
2. 若為 HoloLens 模擬器 (第 1 代)，請確定平台已設定為 **x86**。 若為 HoloLens 2 模擬器，請確定平台已設定為 **x86** 或 **x64**。
3. 選取想要的 **HoloLens 模擬器**版本作為要偵錯的目標裝置。
4. 移至 [偵錯] > [開始偵錯]  或按 **F5** 啟動模擬器，然後部署要偵錯的應用程式。

模擬器首次啟動時，可能需要一分鐘以上的時間才能啟動。 建議您在偵錯工作階段期間讓模擬器保持開啟，以便能夠快速地將應用程式部署到執行中的模擬器。

## <a name="basic-emulator-input"></a>基本的模擬器輸入

控制模擬器的方式和許多常見的 3D 電玩遊戲非常類似。 可用的輸入選項包括使用鍵盤、滑鼠或 Xbox 控制器。 您可以藉由指揮穿戴 HoloLens 的模擬使用者做一些動作來控制模擬器。 您的動作會在模擬使用者周圍移動，且在模擬器中執行的應用程式會像在實際裝置中操作一樣地做出回應。

HoloLens (第 1 代) 上的游標會跟著頭部的移動和旋轉。  在 HoloLens 2 模擬器中，游標則會跟著手部的移動和方向。

* **向前走、向後走、向左走和向右走** - 使用鍵盤上的 W、A、S 和 D 鍵或 Xbox 控制器上的左搖桿。
* **向上看、向下看、向左看和向右看** - 按一下並拖曳滑鼠、使用鍵盤上的方向鍵或 Xbox 控制器上的右搖桿。
* **空中點選手勢** - 按一下滑鼠右鍵、按鍵盤上的 Enter 鍵或使用 Xbox 控制器上的 A 鈕。
* **綻開/系統手勢** - 按鍵盤上的 Windows 鍵或 F2 鍵，或按 Xbox 控制器上的 B 鈕。
* **移動手部來捲動** - 按住 Alt 鍵、按住滑鼠右鍵，然後將滑鼠往上/往下拖曳，或在 Xbox 控制器中，按下 RT 鍵和 A 鈕並將右搖桿往上和往下移動。
* **手部移動和方向** (僅限 HoloLens 2 模擬器) - 按住 Alt 鍵並將滑鼠往上/往下/往左/往右拖曳來移動手部，或使用方向鍵和 Q/E 來旋轉及傾斜手部。  若為 Xbox 控制器，則按住 LB 鍵或 RB 鍵並使用左搖桿來將手部往左/往右/往前/往後移動、使用右搖桿來旋轉手部，以及 Dpad 上的向上/向下來提高或降低手部。

## <a name="anatomy-of-the-hololens-2-emulator"></a>HoloLens 2 模擬器的結構 

### <a name="main-window"></a>主視窗

![HoloLens 2 模擬器的主視窗](images/emulator2-900px.png)

### <a name="toolbar"></a>工具列

在主視窗右邊，您會找到模擬器工具列。 工具列包含下列按鈕：
* ![關閉圖示](images/emulator-close.png) **關閉**：關閉模擬器。
* ![最小化圖示](images/emulator-minimize.png) **最小化**：將模擬器視窗最小化。
* ![Simulation_icon](images/emulator-simulation-panel.png) **模擬控制台**：顯示或隱藏用來設定和控制[模擬器輸入](#basic-emulator-input)的[模擬控制台](#simulation-control-panel)。
* ![全螢幕圖示](images/emulator-fit.png) **全螢幕**：讓模擬器變成全螢幕大小。
* ![縮放圖示](images/emulator-zoom.png) **縮放**：讓模擬器放大和縮小。
* ![説明圖示](images/emulator-help.png)**説明**：開啟模擬器的說明。
* ![開啟裝置入口網站圖示](images/emulator-deviceportal.png) **開啟裝置入口網站**：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。
* ![工具圖示](images/emulator-tools.png) **工具**：開啟 [其他工具]  窗格。

### <a name="simulation-control-panel"></a>模擬控制台

模擬控制台可讓您檢視模擬的人類與輸入裝置目前的位置和方向。  其也可讓您設定模擬輸入 (例如，顯示或隱藏單手或雙手) 以及用於控制模擬輸入的裝置 (例如，電腦的鍵盤、滑鼠和遊戲台)。

![模擬控制台](images/emulator-simulation-control-panel.png)

* 若要隱藏或顯示模擬控制台，請按一下工具列按鈕或按鍵盤上的 F7 鍵。
* 將滑鼠停留在控制項或欄位上以顯示工具提示，其內含適用的鍵盤、滑鼠和遊戲台控制項。
* 若要顯示或隱藏手部，請切換左手或右手底下的適當開關。
* 若要控制手部，請使用鍵盤上左邊或右邊的 Alt 鍵，或使用遊戲台上的 LB 鍵或 RB 鍵。
* 若要將所有輸入引導至單手或雙手，請按一下切換開關底下的圖釘按鈕。  對於手部來說，這相當於按住 Alt 鍵。
* 若要控制眼睛注視方向，請按一下 [眼睛] 區段中的圖釘。  在鍵盤上，這相當於按住 [Y] 鍵。
* 若要載入空間記錄，請按一下 [記錄] 區段中的 [載入] 按鈕。  如需詳細資訊，請參閱[模擬空間](#simulated-rooms)。
* 若要調整所模擬人類或模擬輸入裝置為回應鍵盤、滑鼠或遊戲台的輸入所做移動或旋轉的速度，請按一下 [輸入設定] 旁的齒輪圖示，然後調整滑桿。
* 根據預設，鍵盤輸入會控制所模擬的人類和模擬輸入。  若要讓電腦的鍵盤輸入傳送至 HoloLens，請取消核取 [使用鍵盤來模擬]。  F4 是這項設定的快速鍵。
* 如果模擬控制台已顯示，則按 F8 鍵可將鍵盤焦點移至該控制台。
* 若要從模擬器視窗卸除模擬控制台，請按一下控制台底部的按鈕，或在鍵盤上按 F9 鍵。  關閉視窗或再次按 F9 鍵會讓視窗返回模擬器。
* 您可以用個別應用程式的形式來啟動模擬控制台，這可讓您藉由從 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\ 執行 PerceptionSimulationInput.exe，來控制並連線至 HoloLens 2 模擬器、HoloLens 2 裝置或 Windows Mixed Reality 模擬。

### <a name="account-tab"></a>[帳戶] 索引標籤

[帳戶] 索引標籤可讓您將模擬器設定為使用 Microsoft 帳戶來登入。 這適用於會要求使用者使用帳戶來登入的測試 API。  若要切換這個選項，您必須先徹底關閉再重新啟動 HoloLens 模擬器，設定才會生效。  如果此選項啟用，後續在啟動模擬器時，系統就會要求您登入，就和使用者在首次啟動 HoloLens 時會進行的程序一樣。  若要使用電腦的鍵盤快速輸入認證，請先關閉模擬控制台中的 [使用鍵盤來模擬]，或按鍵盤上的 F4 來將鍵盤設定切換為開啟或關閉。

### <a name="optional-settings-tab"></a>[選擇性設定] 索引標籤

[選擇性設定] 索引標籤會顯示用來啟用或停用硬體加速圖形的控制項。  依預設，如果電腦的圖形卡驅動程式有支援硬體加速圖形，便會加以使用。  如果圖形卡的驅動程式不支援 GPU-PV，系統就不會顯示此選項。

### <a name="diagnostics-tab"></a>[診斷] 索引標籤

[診斷] 索引標籤會顯示模擬器的 IP 位址 (以 Windows 裝置入口網站連結的形式) 以及虛擬 GPU 的狀態。


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>HoloLens (第 1 代) 模擬器的結構

### <a name="main-window"></a>主視窗

當模擬器啟動時，您會看到一個顯示了 HoloLens OS 的視窗。

![HoloLens 模擬器的主視窗](images/emulator-890px.png)

### <a name="toolbar"></a>工具列

在主視窗右邊，您會找到模擬器工具列。 工具列包含下列按鈕：
* ![關閉圖示](images/emulator-close.png) **關閉**：關閉模擬器。
* ![最小化圖示](images/emulator-minimize.png) **最小化**：將模擬器視窗最小化。
* ![人類輸入圖示](images/emulator-control.png) **人類輸入**：滑鼠和鍵盤可用來模擬人類對[模擬器的輸入](#basic-emulator-input)。
* ![鍵盤和滑鼠輸入圖示](images/emulator-input.png) **鍵盤和滑鼠輸入**：鍵盤和滑鼠輸入會直接以鍵盤和滑鼠事件的形式傳遞到 HoloLens OS，彷彿您是與藍牙鍵盤和滑鼠連線。
* ![全螢幕圖示](images/emulator-fit.png) **全螢幕**：讓模擬器變成全螢幕大小。
* ![縮放圖示](images/emulator-zoom.png) **縮放**：讓模擬器放大和縮小。
* ![説明圖示](images/emulator-help.png)**説明**：開啟模擬器的說明。
* ![開啟裝置入口網站圖示](images/emulator-deviceportal.png) **開啟裝置入口網站**：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。
* ![工具圖示](images/emulator-tools.png) **工具**：開啟 [其他工具]  窗格。

### <a name="simulation-tab"></a>[模擬] 索引標籤

[其他工具]  窗格中的預設索引標籤是 [模擬]  索引標籤。

![HoloLens 模擬器的 [其他工具] 窗格](images/emulator-simulation-500px.png)

[模擬] 索引標籤會顯示用來在模擬器中驅動 HoloLens OS 的模擬感應器目前是什麼狀態。 將滑鼠停留在 [模擬] 索引標籤中的任何值上，便會提供描述如何控制該值的工具提示。

### <a name="room-tab"></a>[空間] 索引標籤

模擬器會以來自所模擬「空間」的空間對應網格形式，模擬世界輸入。 此索引標籤可讓您挑選所要載入的空間，而非載入預設空間。

![HoloLens 模擬器的 [空間] 索引標籤](images/emulator-room-500px.png)

如需詳細資訊，請參閱[模擬空間](#simulated-rooms)。

### <a name="account-tab"></a>[帳戶] 索引標籤

[帳戶] 索引標籤可讓您將模擬器設定為使用 Microsoft 帳戶來登入。 這適用於會要求使用者使用帳戶來登入的測試 API。 在此頁面上核取該方塊後，後續在啟動模擬器時，系統就會要求您登入，就和使用者在首次啟動 HoloLens 時會進行的程序一樣。

## <a name="simulated-rooms"></a>模擬空間

模擬空間可用於在多個環境測試應用程式。 模擬器會隨附數個空間，一旦您安裝模擬，就會在 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(版本)\Plugins\Rooms 中發現這些空間。 這些空間全都是使用 HoloLens 在真實環境中擷取下來的：
* **DefaultRoom.xef** - 小型客廳，配備有電視、咖啡桌與兩個沙發。 會在您啟動模擬器時依預設載入。
* **Bedroom1.xef** - 小型臥室，配備有書桌。
* **Bedroom2.xef** - 一間臥室，配備有大號雙人床、梳妝台、床頭櫃和衣帽間。
* **GreatRoom.xef** - 大型開放空間，有客廳、餐桌和廚房。
* **LivingRoom.xef** - 客廳，配備有壁爐、沙發、扶手椅和擺了一個花瓶的咖啡桌。

您也可以在 HoloLens (第 1 代) 上使用 [Windows 裝置入口網站](using-the-windows-device-portal.md)的 [模擬] 頁面，來記錄自己的空間以便在模擬器中使用。

在模擬器中，您只會看到您所呈現的全像投影，而不會看到全像投影背後的模擬空間。 相較之下，在真正的 HoloLens 中，您會看到兩者混合在一起。 如果您想要在 HoloLens 模擬器中看到模擬空間，就必須更新應用程式以呈現場景中的空間對應網格。

## <a name="troubleshooting"></a>疑難排解

您可能會在安裝模擬器時看到錯誤，內容指出您需要「Visual Studio 2015 Update 1 和 UWP 工具 1.2 版」  。 此錯誤有三個可能的原因：
* 您的 Visual Studio 版本不夠新 (Visual Studio 2019、Visual Studio 2017 或 Visual Studio 2015 Update 1 或更新版本)。 若要修正此問題，請安裝最新版的 Visual Studio。
* 您的 Visual Studio 版本夠新，但未安裝通用 Windows 平台 (UWP) 工具。 這是 Visual Studio 的選用功能。

在非專業版/企業版/教育版 SKU 的 Windows 上安裝模擬器時，或如果您尚未啟用 Hyper-V 功能，則可能也會看到錯誤。
* 如需整組需求，請閱讀上面的[系統需求](#hololens-emulator-system-requirements)一節。
* 也請確定您的系統上已啟用 Hyper-V 功能。

如果安裝順利完成，HoloLens 模擬器卻未成為部署和偵錯選項，請確認下列設定：
* Visual Studio 專案設定已設定為 x86 (HoloLens 第 1 代) 或 x86 或 x64 (HoloLens 2 模擬器)。
* 如果使用 Visual Studio 2019，專案設定中的平台工具組已設定為 v142。

如果安裝順利完成，但 Visual Studio 在嘗試啟動 HoloLens 模擬器時顯示錯誤，請嘗試下列動作：
* 以系統管理員身分執行 Visual Studio
* 如果您只安裝過 Visual Studio 2019，請確認 HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots 上的登錄值 "KitsRoot10" 指向 32 位元的 Program Files 資料夾 (例如 "C:\Program Files (x86)\Windows Kits\10")。  如果沒有，請解除安裝 HoloLens 模擬器、將登錄值變更為 32 位元的 Program Files 資料夾，再重新安裝 HoloLens 模擬器。  Visual Studio 2019 16.0.3 已解決此問題。

如果模擬器在啟動時顯示「位元組編碼無效」錯誤對話方塊：
* 請刪除 %localappdata%\Microsoft\XDE\HCS 中的所有檔案，然後再試一次。

如果 Visual Studio 中的偵錯目標清單是空的 (例如，只有 [開始] 選項)，而且您已遵循上述所有疑難排解步驟來操作過：
* 請刪除 %localappdata%\Microsoft\VisualStudio\\<*installation id*>\CoreCon 中的 'ConfigurationCache' 資料夾，然後再試一次。

如果系統在模擬器啟動時停止回應，請停用模擬器圖形的硬體加速。
* 在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 建立名為 "DisableGPU" 的登錄 DWORD 值，並將其值設定為 1。

## <a name="see-also"></a>請參閱
* [進階 HoloLens 模擬器和混合實境模擬器輸入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens 模擬器軟體的歷程記錄](hololens-emulator-archive.md)
* [Unity 中的空間對應](spatial-mapping-in-unity.md)
* [DirectX 中的空間對應](spatial-mapping-in-directx.md)
