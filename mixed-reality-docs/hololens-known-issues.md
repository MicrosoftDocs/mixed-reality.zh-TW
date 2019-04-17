---
title: HoloLens 的已知問題
description: 這是已知的問題可能會影響 HoloLens 的開發人員的清單。
author: mattzmsft
ms.author: mazeller
ms.date: 04/1/2019
ms.topic: article
keywords: 針對進行疑難排解，已知問題，協助
ms.openlocfilehash: a92ab52c899de44f9c5c8c86ebb6f9cd8433d395
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597066"
---
# <a name="hololens-known-issues"></a>HoloLens 的已知問題

這是目前的 HoloLens 影響開發人員的已知問題清單。 在此請先檢查您會看到一個奇怪的行為。 這份清單會保持更新發現新問題或收到回報，或未來的 HoloLens 軟體更新問題的解答。

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>啟動 Microsoft Store 和 HoloLens 上的應用程式的問題

>[!IMPORTANT]
>上次更新日期：@ 10AM-解決問題的 4/2。 

嘗試啟動 Microsoft Store 和 HoloLens 上的應用程式時，可能會遇到問題。 我們已決定背景應用程式更新部署新版 framework 中的封裝特定的順序，一或多個相依的應用程式仍在執行時，會發生問題。 在此情況下，自動更新傳遞新版本的.NET 原生架構 （版本到 10.0.27413 10.0.25531） 會造成未正確更新所有執行的應用程式使用舊版的架構來執行的應用程式。  Framework update 流程如下所示:-

1.  從存放區下載並安裝新的 framework 套件
2.  使用較舊的架構的所有應用程式會 「 更新 」 使用較新版本

如果步驟 2 完成之前中斷任何不已註冊與新版架構的應用程式將無法從 [開始] 功能表啟動。  我們相信 HoloLens 上的任何應用程式可能會受到此問題。

某些使用者有回報，關閉無回應的應用程式，並啟動其他應用程式，例如意見反應中樞，3D 檢視器或相片解決此問題，-但，這無法 100%的時間。

我們根造成此問題已不造成導致不正確地處理，原生.NET framework 更新 OS 更新本身，但錯誤。 我們很高興宣布，我們已識別出修正程式，而且已發行的更新 (OS 版本 17763.380) 包含修正程式。 

若要查看是否您的裝置可能需要更新請：

1.  移至 [設定] 應用程式，並開啟 [更新與安全性]
2.  按一下 [檢查更新]
3.  如果有可用 17763.380 的更新，請更新至接收應用程式懸置狀況 bug 的修正此組建
4.  在更新到此版本的作業系統，應用程式應該運作如預期般運作。

此外，如同我們使用所有 HoloLens OS 發行版本一樣，我們有張貼 FFU 映像至 Microsoft 下載中心 https://aka.ms/hololensdownload/10.0.17763.380。 

如果您不想要取得更新，我們發行了新版本的 Microsoft Store UWP 應用程式自 3/29。 一旦您有更新的版本存放區：

1) 開啟存放區，並確認它會載入。
2) 您可以使用 Bloom 筆勢來開啟的功能表。
3) 嘗試開啟先前中斷的應用程式
3) 如果仍然無法啟動，點選 按住中斷的應用程式的圖示並選取 解除安裝。
4) Resinstall 這些來自市集的應用程式。

如果您的裝置仍然無法載入應用程式，您可以側載的版本的.NET 原生架構和執行階段透過 「 下載中心 」 這麼做：

1)  請下載[此 zip 檔案](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)從 Microsoft 下載中心取得。  解壓縮，將會產生兩個檔案。  Microsoft.NET.Native.Runtime.1.7.appx 和 Microsoft.NET.Native.Framework.1.7.appx
2)  請確認您的裝置是開發人員解除鎖定。  如果您尚未這麼做的指示之前完成[此處](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)。
3)  接著您要進入 Windows Device Portal。  我們的建議是，若要這樣做透過 USB 和您一樣的輸入 http://127.0.0.1:10080貼入瀏覽器。  
4)  一旦您有 Windows Device Portal 向上我們需要您 「 側載 」 的兩個檔案，下載。  若要這麼做，您需要往左的提要欄位，直到您取得的 「 應用程式 」 一節，然後按一下 [應用程式]。
5)  然後，您會看到一個畫面，類似於下方。  您想要前往指出 「 安裝應用程式 」 一節，並瀏覽至您解壓縮這兩個的 APPX 檔案。  您可以只執行一次，因此您選取第一個之後然後按一下 [執行] 在 [部署] 區段。  然後執行這項操作的第二個的 APPX 檔案。 
  ![若要安裝側載應用程式的 Windows Device Portal](images/20190322-DevicePortal.png)<br>
6)  此時我們相信您的應用程式應該啟動重新運作，而且，您也可以取得存放區。
7)  在某些情況下，就需要執行啟動之前將會啟動受影響的應用程式的 3D 檢視器應用程式的額外步驟。 

我們已經看過的程序以解決此項目，這個問題，並期待繼續使用我們的社群建立成功的混合實境體驗，我們非常感謝您耐心等候。

## <a name="connecting-to-wifi"></a>連線到 WiFi

OOBE 和設定，在沒有認證逾時為 2 分鐘。 使用者名稱/密碼，就必須在 2 分鐘否則將會自動清除 [使用者名稱] 欄位內輸入。

我們建議使用藍芽鍵盤輸入長密碼。

## <a name="device-update"></a>裝置更新
* 在新的更新後, 的 30 秒殼層可能會消失一次。 請執行**bloom**繼續您的工作階段的筆勢。

## <a name="visual-studio"></a>Visual Studio
* 請參閱[安裝工具](install-the-tools.md)建議用於 HoloLens 的開發的 Visual Studio 的最新版本。
* 在部署您的 HoloLens 從 Visual Studio 應用程式時，您可能會看到錯誤：**要求的作業無法對具有對應的使用者 區段開啟的檔案。(發生例外狀況於 HRESULT:0x800704C8)**。 如果發生這種情況，再試一次您的部署通常會成功。

## <a name="emulator"></a>模擬器
* 在 Microsoft Store 中的並非所有應用程式都與模擬器相容的。 比方說，Young Conker 和片段不是在模擬器上播放。
* 您無法在模擬器中使用電腦的網路攝影機。
* Windows Device Portal 的即時預覽功能不適用於模擬器。 此外，您還是可以擷取混合實境視訊和影像。

## <a name="unity"></a>Unity
* 請參閱[安裝工具](install-the-tools.md)Unity 建議用於 HoloLens 的開發的最新版本。
* 使用 Unity HoloLens Technical Preview 的已知的問題所述[HoloLens Unity 論壇](http://forum.unity3d.com/threads/known-issues.394627/)。

## <a name="windows-device-portal"></a>Windows Device Portal
* 混合實境擷取的即時預覽功能可能會出現幾秒鐘的延遲。
* 在虛擬輸入 頁面上，虛擬的筆勢 區段下的手勢和捲軸控制項沒有正常運作。 使用它們，會有任何作用。 虛擬鍵盤，在相同頁面上的正常運作。
* 啟用開發人員模式，在設定後，可能需要幾秒鐘的時間才能啟用切換到開啟裝置入口網站。

## <a name="api"></a>API
* 如果應用程式設定[專注點](focus-point-in-unity.md)背後使用者或以 camera.forward 一般，全像投影不會出現在混合實境擷取相片或視訊。 直到修正這個錯誤是 Windows，如果應用程式正在設定[專注點](focus-point-in-unity.md)應該確保平面一般設定相反的相機順向 (例如一般 =-camera.forward)。

## <a name="xbox-wireless-controller"></a>Xbox 無線控制器
* Xbox 無線控制器 S 必須更新，才能搭配 HoloLens。 確保您[最新狀態](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)之前嘗試配對您的控制器與 HoloLens。
* 如果您重新啟動您的 HoloLens Xbox 無線控制器連線時，控制器會不會自動重新連線到 HoloLens。 指南按鈕燈光會顯示閃爍緩時變直到控制器電源關閉之後 3 分鐘。 若要重新連線您的控制器，立即透過保留 [節目表] 按鈕，直到燈號會關閉控制站關閉電源。 當再次開啟電源您的控制器時，它會重新連線到 HoloLens。
* 如果您的 HoloLens 進入待命，Xbox 無線控制器連線時，控制站上的任何輸入會喚醒 HoloLens。 您可以關閉您的控制站，當您完成來防止使用它。
