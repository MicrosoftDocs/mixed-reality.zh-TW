---
title: 使用 HoloLens 模擬器
description: HoloLens 模擬器可讓您測試您的電腦，而不需要實體 HoloLens 上的混合的實境應用程式。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、 模擬器
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596685"
---
# <a name="using-the-hololens-emulator"></a>使用 HoloLens 模擬器

HoloLens 模擬器可讓您測試您的電腦，而不需要實體 HoloLens 上全像攝影版的應用程式，並隨附 HoloLens 的開發工具組。 模擬器會使用 HYPER-V 虛擬機器。 通常會由 HoloLens 上感應器的人力和環境輸入是改為模擬使用您的鍵盤、 滑鼠或 Xbox 控制器。 應用程式不需要修改，才能在模擬器上執行，而且不知道它們不真正的 HoloLens 上執行。

如果您想要開發適用於桌面的電腦的 Windows Mixed Reality 沈浸式 (VR) 耳機應用程式或遊戲，請參閱[Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)，這可讓您改為模擬桌面耳機。

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。

## <a name="installing-the-hololens-emulator"></a>安裝 HoloLens 模擬器

下載[HoloLens （第 1 代） 模擬器] 和 [全像攝影版的專案範本](https://go.microsoft.com/fwlink/?linkid=2065980)。

您可以找到舊版組建的 HoloLens 模擬器[HoloLens 模擬器封存](hololens-emulator-archive.md)頁面。

### <a name="hololens-emulator-system-requirements"></a>HoloLens 模擬器系統需求

HoloLens 模擬器以 HYPER-V 為基礎，並使用 RemoteFx 的硬體加速的圖形。 若要使用模擬器，請確定您的電腦符合下列硬體需求：
* 64 位元 Windows 10 Pro、 Enterprise 或教育版 
    >[!NOTE]
    >Windows 10 家用版不支援 HYPER-V 或 HoloLens 模擬器
* 64 位元 CPU
* CPU 4 個核心 （或多個 Cpu，總共有 4 個核心）
* 8 GB 的 RAM 或以上
* 在 BIOS 中必須是下列功能[支援，並啟用](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * 硬體協助虛擬化
   * 第二層位址轉譯 (SLAT)
   * 硬體型資料執行防止 (DEP)。
* GPU 需求 （模擬器可能會使用不支援的 GPU，但將會明顯變慢）
   * DirectX 11.0 或更新版本
   * WDDM 1.2 驅動程式或更新版本

如果您的系統符合上述需求，**請確定您的系統上，已啟用 「 HYPER-V 」 功能**透過 控制台-> 程式-> 程式和功能-> 上的 開啟 Windows 功能，或關閉-> 確認「 HYPER-V 」 已選取的模擬器安裝才能成功。

### <a name="installation-troubleshooting"></a>安裝疑難排解

安裝模擬器，您需要時，您可能會看到錯誤 *「 Visual Studio 2015 Update 1 及 UWP 工具 1.2 版 「*。 有三個可能的原因，此錯誤：
* 您沒有 Visual Studio （Visual Studio 2017 或 Visual Studio 2015 Update 1 或更新版本） 不夠新版本。 若要修正此問題，安裝最新版的 Visual Studio。
* 您擁有的版本不夠新，Visual Studio 中，但您不需要安裝的通用 Windows 平台 (UWP) 工具。 這是適用於 Visual Studio 的選用功能。

您可能也會看到安裝模擬器上非-PRO/Enterprise/教育 SKU 的 Windows 錯誤，或如果您沒有 HYPER-V 功能啟用。
* 請閱讀[系統需求](#hololens-emulator-system-requirements)的一組完整的需求一節。
* 請也確保您的系統上，已啟用 HYPER-V 功能。

## <a name="deploying-apps-to-the-hololens-emulator"></a>應用程式部署到 HoloLens 模擬器

1. 載入您的應用程式解決方案，在 Visual Studio 2015。
    >[!NOTE]
    >當使用 Unity 時，從 Unity 建置您的專案，然後如往常般將建置的方案載入至 Visual Studio。
2. 請確定在平台設定為**x86**。
3. 選取  **HoloLens 模擬器**作為偵錯的目標裝置。
4. 移至**偵錯 > 啟動偵錯**或按**F5**啟動模擬器和部署您的應用程式進行偵錯。

模擬器可能需要一分鐘或更多以第一次啟動時開機。 我們建議您保持模擬器開啟偵錯工作階段期間讓您可以快速地將應用程式部署到執行中的模擬器。

## <a name="basic-emulator-input"></a>基本的模擬器輸入

控制模擬器是非常類似於許多常見的 3D 視訊遊戲。 有可用的輸入的選項使用鍵盤、 滑鼠或 Xbox 控制器。 您可以將導向穿著 HoloLens 的模擬使用者動作控制模擬器。 您的動作移動周圍的模擬的使用者並在模擬器中執行的應用程式回應在實際裝置上所顯示的一樣。
* **上一步，向前保留，並以滑鼠右鍵**-使用 W、 A、 S 和 D 鍵盤或 Xbox 控制器上的左搖桿上的索引鍵。
* **查閱，向下、 左、 並以滑鼠右鍵**-按一下並拖曳滑鼠，使用方向鍵在鍵盤或 Xbox 控制器上正確的隨身碟上。
* **空中點選手勢**-按一下滑鼠右鍵，在鍵盤上按 Enter 鍵或使用 Xbox 控制器上的按鈕。
* **百花齊放筆勢**-在鍵盤上按 Windows 鍵或 F2 鍵或按下 B 上的 Xbox 控制器。
* **另一方面移動捲動**-按住 Alt 鍵，請按住滑鼠按鈕，並拖曳滑鼠，增加 / 減少，或 Xbox 控制器中按住正確的觸發程序和一個按鈕並向上和向下移動右隨身碟。

## <a name="anatomy-of-the-hololens-emulator"></a>HoloLens 模擬器的結構

### <a name="main-window"></a>主視窗

當模擬器啟動時，您會看到一個可顯示 HoloLens OS 視窗。

![HoloLens 模擬器主視窗](images/emulator-890px.png)

### <a name="toolbar"></a>工具列

在主視窗的右邊，您會發現模擬器工具列。 工具列包含下列按鈕：
* ![關閉圖示](images/emulator-close.png)**關閉**:關閉模擬器。
* ![最小化 圖示](images/emulator-minimize.png)**最小化**:最小化 [模擬器] 視窗。
* ![人性化的輸入的圖示](images/emulator-control.png)**人力輸入**:滑鼠和鍵盤用來模擬人類[輸入至模擬器](#basic-emulator-input)。
* ![鍵盤和滑鼠輸入的圖示](images/emulator-input.png)**鍵盤和滑鼠輸入**:鍵盤和滑鼠輸入會直接傳遞到 HoloLens 作業系統做為鍵盤和滑鼠事件連線藍芽鍵盤和滑鼠。
* ![全螢幕圖示](images/emulator-fit.png)**全螢幕**:符合的模擬器畫面。
* ![顯示比例 圖示](images/emulator-zoom.png)**縮放**:放大及縮小，請讓模擬器。
* ![説明圖示](images/emulator-help.png)**協助**:開啟模擬器的說明。
* ![開啟裝置入口網站 圖示](images/emulator-deviceportal.png)**開啟裝置入口網站**:開啟 Windows Device Portal HoloLens os 在模擬器中。
* ![工具圖示](images/emulator-tools.png)**工具**:開啟**其他工具**窗格。

### <a name="simulation-tab"></a>模擬 索引標籤

中的 預設 索引標籤**額外的工具** 窗格是**模擬** 索引標籤。

![HoloLens 模擬器 [其他工具] 窗格](images/emulator-simulation-500px.png)

[模擬] 索引標籤會顯示模擬的感應器用來驅動 HoloLens OS 在模擬器中的目前狀態。 將滑鼠停留在 [模擬] 索引標籤中的任何值，將會提供工具提示描述如何控制該值。

### <a name="room-tab"></a>空間索引標籤

模擬器會模擬世界空間對應網狀結構與模擬"聊天室"形式的輸入。 此索引標籤可讓您挑選的空間可載入而不是預設的空間。

![HoloLens 模擬器 '聊天室' 索引標籤](images/emulator-room-500px.png)

模擬的聊天室可用於在多個環境中測試您的應用程式。 數個房間隨附於模擬器，一旦您安裝模擬時，您會發現這些 %programfiles(x86) %\Program 檔案 (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms 中。 所有這些聊天室使用 HoloLens 的實際環境中所擷取的：
* **DefaultRoom.xef** -電視、 咖啡桌，與兩個 sofas 小型起居室的絨布。 當您啟動模擬器時，請載入預設。
* **Bedroom1.xef** -小型臥室與支援人員。
* **Bedroom2.xef** -臥室皇后大小平台、 與衣櫃、 nightstands，walk-in 衣櫥。
* **GreatRoom.xef** -客廳、 餐桌，與廚房的大型的開放空間絕佳空間。
* **LivingRoom.xef** -起居室的絨布壁爐、 沙發、 armchairs，以及具有花瓶的咖啡資料表。

您也可以記錄使用的模擬頁面在模擬器中使用您自己聊天室[Windows Device Portal](using-the-windows-device-portal.md)您 HoloLens 上。

在模擬器中，您只會看到全像投影您轉譯，並將不會看到全像投影背後模擬的空間。 這是相較於真正的 HoloLens，您看到兩者混合在一起。 如果您想要看到模擬的聊天室 HoloLens 模擬器中，您必須更新您的應用程式，以轉譯場景中的空間對應網格。

### <a name="account-tab"></a>[帳戶] 索引標籤

[帳戶] 索引標籤可讓您將模擬器設定為使用 Microsoft 帳戶登入。 這是適用於測試 API 的要求使用者登入的帳戶。 之後核取方塊，在此頁面上後續啟動模擬器將會要求您登入，就像使用者一樣第一次啟動 HoloLens。

## <a name="see-also"></a>另請參閱
* [進階的 HoloLens 模擬器] 和 [混合實境模擬器輸入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens 模擬器軟體歷程記錄](hololens-emulator-archive.md)
* [在 Unity 中的空間對應](spatial-mapping-in-unity.md)
* [DirectX 中的空間對應](spatial-mapping-in-directx.md)
