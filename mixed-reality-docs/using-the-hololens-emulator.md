---
title: 使用 HoloLens 模擬器
description: 使用 HoloLens 模擬器在沒有實體 HoloLens 的電腦上測試混合實境應用程式。
author: pbarnettms
ms.author: pbarnett
ms.date: 09/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, 模擬器
ms.openlocfilehash: 455abfabede5bc1e646bd273afa09068feb886a1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437347"
---
# <a name="using-the-hololens-emulator"></a>使用 HoloLens 模擬器

HoloLens 模擬器可讓您在沒有實體 HoloLens 的電腦上測試全像攝影應用程式。 它也包含 HoloLens 開發工具組。 模擬器會使用 Hyper-V 虛擬機器。 通常由 HoloLens 感應器讀取的人類和環境輸入，會從鍵盤、滑鼠或 Xbox 控制器來模擬。 應用程式不需要經過修改就能在模擬器上執行；應用程式不會察覺到本身並非在真實的 HoloLens 上執行。

如果您想要開發適用於桌上型電腦的 Windows Mixed Reality 沈浸式 (VR) 頭戴式裝置應用程式或遊戲，請參閱 [Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)，以模擬桌上型電腦的頭戴式裝置。


## <a name="installing-the-hololens-emulator"></a>安裝 HoloLens 模擬器
下載 HoloLens 模擬器。

版本： 
* [HoloLens 2 模擬器 (2019 年 10 月更新)](https://go.microsoft.com/fwlink/?linkid=2106649)。
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
* BIOS 必須[支援並啟用](https://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx)下列功能：
   * 硬體協助虛擬化
   * 第二層位址轉譯 (SLAT)
   * 硬體型資料執行防止 (DEP)
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

模擬器首次啟動時，可能需要一分鐘以上的時間才能啟動。 建議您在偵錯工作階段期間讓模擬器保持開啟，以便能夠快速地將應用程式部署到模擬器。

## <a name="basic-emulator-input"></a>基本的模擬器輸入

控制模擬器的方式和許多常見的 3D 電玩遊戲非常類似。 可用的輸入選項包括使用鍵盤、滑鼠或 Xbox 控制器。 您可以藉由指揮穿戴 HoloLens 的模擬使用者做一些動作來控制模擬器。 您的動作會使模擬的使用者在環境中移動。 在模擬器中執行的應用程式會像在實際裝置中操作一樣做出回應。

HoloLens (第 1 代) 上的游標會跟著頭部的移動和旋轉。 在 HoloLens 2 模擬器中，游標則會跟著手部的移動和方向。

* **向前走、向後走、向左走和向右走** - 使用鍵盤上的 W、A、S 和 D 鍵或 Xbox 控制器上的左搖桿。
* **向上看、向下看、向左看和向右看** - 按一下並拖曳滑鼠、使用鍵盤上的方向鍵或 Xbox 控制器上的右搖桿。
* **空中點選手勢** - 按一下滑鼠右鍵、按鍵盤上的 Enter 鍵或使用 Xbox 控制器上的 A 鈕。
* **綻開/系統手勢** - 按鍵盤上的 Windows 鍵或 F2 鍵，或按 Xbox 控制器上的 B 鈕。
* **移動手部來捲動** - 同時按住 Alt 鍵和滑鼠右鍵，然後將滑鼠往上或往下拖曳，或在 Xbox 控制器中，按下 RT 鍵和 A 鈕並將右搖桿往上和往下移動。
* **手部移動和方向** (僅限 HoloLens 2 模擬器) - 按住 Alt 鍵並將滑鼠往上、往下、往左或往右拖曳來移動手部，或使用方向鍵和 Q 或 E 來旋轉及傾斜手部。 若為 Xbox 控制器，則按住 LB 鍵或 RB 鍵並使用左搖桿將手部往左、往右、往前和往後移動、使用右搖桿來旋轉手部，以及 Dpad 上的向上或向下來提高或降低手部。

## <a name="anatomy-of-the-hololens-2-emulator"></a>HoloLens 2 模擬器的結構 

### <a name="main-window"></a>主視窗

![HoloLens 2 模擬器的主視窗](images/emulator2-900px.png)

### <a name="toolbar"></a>工具列

在主視窗右邊，找出模擬器工具列。 工具列包含下列按鈕：
* ![關閉圖示](images/emulator-close.png) **關閉**：關閉模擬器。
* ![最小化圖示](images/emulator-minimize.png) **最小化**：將模擬器視窗最小化。
* ![Simulation_icon](images/emulator-simulation-panel.png) **模擬控制台**：顯示或隱藏用來設定和控制[模擬器輸入](#basic-emulator-input)的[模擬控制台](#simulation-control-panel)。
* ![全螢幕圖示](images/emulator-fit.png) **全螢幕**：讓模擬器變成全螢幕大小。
* ![縮放圖示](images/emulator-zoom.png) **縮放**：讓模擬器放大和縮小。
* ![説明圖示](images/emulator-help.png)**説明**：開啟模擬器的說明。
* ![開啟裝置入口網站圖示](images/emulator-deviceportal.png) **開啟裝置入口網站**：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。
* ![工具圖示](images/emulator-tools.png) **工具**：開啟 [其他工具]  窗格。

### <a name="simulation-control-panel"></a>模擬控制台

模擬控制台可讓您檢視模擬的人類與輸入裝置目前的位置和方向。 它也可讓您設定模擬輸入 (例如，顯示或隱藏單手或雙手) 以及用來控制模擬輸入的裝置 (例如，電腦的鍵盤、滑鼠和遊戲台)。

![模擬控制台](images/emulator-simulation-control-panel.png)

* 若要隱藏或顯示模擬控制台，請按一下工具列按鈕或按鍵盤上的 F7 鍵。
* 將滑鼠停留在控制項或欄位上以顯示工具提示，其中包含適用的鍵盤、滑鼠和遊戲台控制項。
* 若要顯示或隱藏手部，請切換左手或右手底下的適當開關。
* 若要控制手部，請使用鍵盤上左邊或右邊的 Alt 鍵，或使用遊戲台上的 LB 鍵或 RB 鍵。
* 若要將所有輸入引導至單手或雙手，請按一下切換開關底下的圖釘按鈕。 對於手部來說，這相當於按住 Alt 鍵。
* 若要控制眼睛注視方向，請按一下 [眼睛] 區段中的圖釘。 在鍵盤上，這相當於按住 Y 鍵。
* 若要載入空間記錄，請按一下 [記錄] 區段中的 [載入] 按鈕。 如需詳細資訊，請參閱[模擬空間](#simulated-rooms)。
* 若要調整模擬的人類或輸入裝置為回應鍵盤、滑鼠或遊戲台的輸入所做移動或旋轉的速度，請按一下 [輸入設定] 旁的齒輪圖示，然後調整滑桿。
* 根據預設，鍵盤輸入會控制所模擬的人類和模擬輸入。 若要讓電腦的鍵盤輸入傳送至 HoloLens，請取消核取 [使用鍵盤來模擬]。 F4 是這項設定的快速鍵。
* 如果模擬控制台已顯示，則按 F8 鍵可將鍵盤焦點移至該控制台。
* 若要從模擬器視窗卸除模擬控制台，請按一下控制台底部的按鈕，或在鍵盤上按 F9 鍵。  關閉視窗或再次按 F9 鍵會讓視窗返回模擬器。
* 您可以用個別應用程式的形式來啟動模擬控制台，這可讓您藉由從 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\ 執行 PerceptionSimulationInput.exe，來控制並連線至 HoloLens 2 模擬器、HoloLens 2 裝置或 Windows Mixed Reality 模擬。

### <a name="account-tab"></a>帳戶索引標籤

[帳戶] 索引標籤可讓您將模擬器設定為使用 Microsoft 帳戶來登入。 這適用於會要求使用者使用帳戶進行登入的測試 API。 若要切換這個選項，您必須先完全關閉再重新啟動 HoloLens 模擬器，設定才會生效。 如果此選項啟用，後續在啟動模擬器時，系統就會要求您登入，就和使用者在首次啟動 HoloLens 時進行的程序一樣。 若要使用電腦的鍵盤輸入認證，請先關閉模擬控制台的 [使用鍵盤來模擬]，或按鍵盤上的 F4 將鍵盤設定切換為開啟或關閉。

### <a name="optional-settings-tab"></a>選擇性設定索引標籤

[選擇性設定] 索引標籤會顯示用來啟用或停用硬體加速圖形的控制項。 依預設，如果電腦的圖形卡驅動程式支援硬體加速圖形，便會加以使用。 如果圖形卡的驅動程式不支援 GPU-PV，系統就不會顯示此選項。

### <a name="diagnostics-tab"></a>診斷索引標籤

[診斷] 索引標籤會顯示模擬器的 IP 位址 (以 Windows 裝置入口網站連結的形式) 以及虛擬 GPU 的狀態。

### <a name="network-tab"></a>網路索引標籤

[網路] 索引標籤會顯示模擬器的網路介面卡詳細資料，以及主機電腦的網路介面卡詳細資料。 請注意，若是使用 HoloLens 2 模擬器，只有在 Windows 10 2019 更新或更新版本上執行模擬器時，才會出現此索引標籤。

### <a name="nat-configuration-tab"></a>NAT 設定索引標籤

只有在 Windows 10 2019 更新或更新版本上執行模擬器時，才會出現此索引標籤。

模擬器會使用您電腦的網路連線，並位於 NAT 後方。  此索引標籤可讓您將主機電腦的連接埠對應到模擬器，讓遠端裝置能夠連線到在模擬器中執行的應用程式和服務。

例如，如果您想要從遠端電腦存取模擬器上的裝置入口網站：

1. 按兩下資料表中的可用列，可新增內部連接埠 80 (裝置入口網站接聽的埠)。  針對其他應用程式，請輸入該應用程式接聽的埠號碼。
2. 選擇任何可用的內部連接埠。  在此範例中，我們將使用埠 8080 做為外部連接埠。
3. 選取通訊協定。  預設值是 TCP。  因為裝置入口網站使用 TCP，所以我們會保留預設值。
4. 按一下 [套用變更] 以啟用對應。  [狀態] 將從 [擱置] 變更為 [啟動]。
5. 在遠端電腦上，開啟瀏覽器並瀏覽至 (IP-of-the-PC-running-the-emulator):8080。  裝置入口網站介面隨即出現。  請注意，您用於遠端電腦的 IP 位址必須是執行模擬器之電腦的 IP 位址，而不是模擬器本身。  您可以透過各種方式來擷取 IP，例如電腦上 [網路 & 網際網路] 類別目錄中的 [設定] 應用程式、在命令提示字元使用 'ipconfig'、或是從 [模擬器工具] 對話方塊的 [網路] 索引標籤中尋找 [桌面介面卡] 來取得。

另請注意，如果您新增裝置入口網站的連接埠對應，您可以使用模擬器安裝中包含的「感知模擬控制」工具來從遠端控制模擬器，或是透過連線到主機電腦的 IP 位址和裝置入口網站外部連接埠 (例如上述範例中的8080) 來使用感知模擬 API，以從遠端控制模擬器。  使用「感知模擬控制」來遠端連線並控制模擬器時，只要指定電腦的 IP 位址和設定的連接埠。  不要包括 'https://'。

預設是沒有連接埠對應。  您設定的任何對應都會在 HoloLens 2 模擬器的啟動期間持續，而且當模擬器完全開機時將會自動啟用。

使用 [匯出] 按鈕將您的對應儲存至檔案。  然後，您可以與其他可使用 [匯入] 按鈕自動設定相同對應的小組成員共用此檔案。

![HoloLens 模擬器的 NAT 設定索引標籤](images/emulator-natconfig-500px.png)

### <a name="updates-tab"></a>更新索引標籤

只有在 Windows 10 2019 更新或更新版本上執行模擬器時，才會出現此索引標籤。

模擬器會在啟動時檢查是否有新的版本。  如果有新版本，模擬器將會顯示提示，指出您擁有的版本以及可用的版本，並詢問您是否要更新。  如果您選取 [是]，便會下載新版本的安裝程式。

[更新] 索引標籤可讓您控制模擬器是否檢查新版本，您只需在此索引標籤上切換 [自動檢查更新] 核取方塊。從 2019 年 9 月更新開始，也可讓您查看和下載其他可用的模擬器版本。  所有目前執行版本以外的版本皆會提供下載連結。  按一下此連結將會下載該版本的安裝程式。

![HoloLens 模擬器的更新索引標籤](images/emulator-updates-500px.png)


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>HoloLens (第 1 代) 模擬器的結構

### <a name="main-window"></a>主視窗

當模擬器啟動時，您將會看到顯示 HoloLens OS 的視窗。

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

![HoloLens 模擬器的其他工具窗格](images/emulator-simulation-500px.png)

[模擬] 索引標籤會顯示用來在模擬器中驅動 HoloLens OS 的模擬感應器目前是什麼狀態。 將滑鼠停留在 [模擬] 索引標籤中的任何值上方，會提供描述如何控制該值的工具提示。

### <a name="room-tab"></a>[空間] 索引標籤

模擬器會以來自所模擬空間的空間對應網格形式，模擬世界輸入。 此索引標籤可讓您挑選所要載入的空間，而非載入預設空間。

![HoloLens 模擬器的 [空間] 索引標籤](images/emulator-room-500px.png)

如需詳細資訊，請參閱[模擬空間](#simulated-rooms)。

### <a name="account-tab"></a>帳戶索引標籤

[帳戶] 索引標籤可讓您將模擬器設定為使用 Microsoft 帳戶來登入。 這適用於會要求使用者使用帳戶來登入的測試 API。 在此頁面上核取該方塊後，後續在啟動模擬器時，系統就會要求您登入，就和使用者在首次啟動 HoloLens 時會進行的程序一樣。

## <a name="simulated-rooms"></a>模擬空間

模擬空間可供您在多個環境中測試應用程式。 模擬器會隨附數個空間。 一旦您安裝模擬，就會在 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(版本)\Plugins\Rooms 中發現這些空間。 這些空間全都是使用 HoloLens 在真實環境中擷取下來的：
* **DefaultRoom.xef** - 小型客廳，配備有電視、咖啡桌與兩個沙發。 會在您啟動模擬器時依預設載入。
* **Bedroom1.xef** - 小型臥室，配備有書桌。
* **Bedroom2.xef** - 一間臥室，配備有大號雙人床、梳妝台、床頭櫃和衣帽間。
* **GreatRoom.xef** - 大型開放空間，有客廳、餐桌和廚房。
* **LivingRoom.xef** - 客廳，配備有壁爐、沙發、扶手椅和擺了一個花瓶的咖啡桌。

您也可以在 HoloLens (第 1 代) 上使用 [Windows 裝置入口網站](using-the-windows-device-portal.md)的 [模擬] 頁面，來記錄自己的空間以便在模擬器中使用。

在模擬器中，您只會看到您所呈現的全像投影。 您不會看到全像投影背後的模擬空間。 相較之下，在實際的 HoloLens 中，您會看到兩者混合在一起。 如果您想要在 HoloLens 模擬器中看到模擬空間，就必須更新應用程式以呈現場景中的空間對應網格。

## <a name="troubleshooting"></a>疑難排解

您可能會在安裝模擬器時看到錯誤訊息，內容指出您需要「Visual Studio 2015 Update 1 和 UWP 工具 1.2 版」  。 此錯誤有三個可能的原因：
* 您的 Visual Studio 版本不夠新 (Visual Studio 2019、Visual Studio 2017 或 Visual Studio 2015 Update 1 或更新版本)。 若要修正此問題，請安裝最新版的 Visual Studio。
* 您有最新版的 Visual Studio，但未安裝通用 Windows 平台 (UWP) 工具。 這是 Visual Studio 的選用功能。

在非專業版/企業版/教育版 SKU 的 Windows 上安裝模擬器時，或如果您尚未啟用 Hyper-V 功能，則可能也會看到錯誤。
* 如需整組需求，請閱讀上面的[系統需求](#hololens-emulator-system-requirements)一節。
* 也請確定您的系統上已啟用 Hyper-V 功能。

如果安裝順利完成，HoloLens 模擬器卻未成為部署和偵錯選項，請確認下列設定：
* Visual Studio 專案設定已設定為 x86 (HoloLens 第 1 代)、x86 或 x64 (HoloLens 2 模擬器)。
* 如果使用 Visual Studio 2019，專案設定中的平台工具組已設定為 v142。

如果安裝順利完成，但 Visual Studio 在嘗試啟動 HoloLens 模擬器時顯示錯誤，請嘗試下列動作：
* 以系統管理員身分執行 Visual Studio
* 如果您只安裝過 Visual Studio 2019，請確認 HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots 上的登錄值 "KitsRoot10" 指向 32 位元的 Program Files 資料夾 (例如 "C:\Program Files (x86)\Windows Kits\10")。  如果沒有，請解除安裝 HoloLens 模擬器、將登錄值變更為 32 位元的 Program Files 資料夾，再重新安裝 HoloLens 模擬器。  Visual Studio 2019 16.0.3 已解決此問題。

如果模擬器在啟動時顯示「位元組編碼無效」錯誤對話方塊：
* 請刪除 %localappdata%\Microsoft\XDE\HCS 中的所有檔案，然後再試一次。

如果 Visual Studio 中的偵錯目標清單是空的 (例如，只有 [開始] 選項)，而且您已遵循上述所有疑難排解步驟進行操作：
* 請刪除 %localappdata%\Microsoft\VisualStudio\\<*installation id*>\CoreCon 中的 ConfigurationCache 資料夾，然後再試一次。

如果系統在模擬器啟動時停止回應，請停用模擬器圖形的硬體加速。
* 在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 建立名為 "DisableGPU" 的登錄 DWORD 值，並將其值設定為 1。

## <a name="see-also"></a>請參閱
* [進階 HoloLens 模擬器和混合實境模擬器輸入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens 模擬器軟體的歷程記錄](hololens-emulator-archive.md)
* [Unity 中的空間對應](spatial-mapping-in-unity.md)
* [DirectX 中的空間對應](spatial-mapping-in-directx.md)
