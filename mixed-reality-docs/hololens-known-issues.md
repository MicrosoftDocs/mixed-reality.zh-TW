---
title: HoloLens 的已知問題
description: 這是已知的問題可能會影響 HoloLens 的開發人員的清單。
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: 針對進行疑難排解，已知問題，協助
ms.openlocfilehash: 1ef9e9f411e16d2f604930f3146ede1d03d7c0f6
ms.sourcegitcommit: c36b8c8573f51afa79504c4a17084e4f55d2f664
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67789484"
---
# <a name="hololens-known-issues"></a>HoloLens 的已知問題

這是目前的 HoloLens 影響開發人員的已知問題清單。 在此請先檢查您會看到一個奇怪的行為。 這份清單會保持更新發現新問題或收到回報，或未來的 HoloLens 軟體更新問題的解答。

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>無法連接，然後部署至透過 Visual Studio 的 HoloLens

>[!NOTE]
>上次更新日期：7/8 下午 7:25-@ 小組已識別的根本原因和目前正努力修正。 因應措施如下所示。 

我們可以找出此問題的根本原因。 然後使用相同的 HoloLens 後續使用最新版的 Visual Studio 2017 或 Visual Studio 2019 和 Visual Studio 2015 或 Visual Studio 2017 的早期版本來部署和偵錯其 HoloLens 上的應用程式的使用者會受到影響。 

由較新版本的 Visual Studio 部署新版的元件，但造成失敗的較新版本的裝置上剩餘檔案從舊的版本。  這會導致下列錯誤訊息：DEP0100:請確定目標裝置已啟用開發人員模式。 無法取得開發人員授權上<ip>因為錯誤 80004005。
 
**因應措施**： 

我們的小組目前正努力修正程式。 在此同時，您可以使用下列步驟來解決此問題，並協助解除部署和偵錯：  
1. 開啟 Visual Studio
2. 檔案-> 新增-> 專案
3. 視覺化C#]-> [Windows 桌面]-> [主控台應用程式 (.NET Framework)
4. 提供專案名稱 (例如 HoloLensDeploymentFix)，並確定至少架構設定為.NET Framework 4.5，然後按一下 [確定]。
5. 以滑鼠右鍵按一下方案總管 中的 參考 節點，並新增下列參考 （按一下 瀏覽 區段中，然後按一下 瀏覽...按鈕）：
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >如果您沒有安裝 10.0.18362.0，使用您所擁有的最新版本。
 
6. 以滑鼠右鍵按一下方案總管] 中的專案，然後選擇 [新增]-> [現有項目。
 
7. 瀏覽至 C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86 並變更篩選，以"的所有檔案 (\*。\*) 」
 
8. 選取 SirepClient.dll 和 SshClient.dll，然後按一下 [新增]。
 
9. 找出並選取方案總管 （它們應該是檔案的清單底部） 中的這兩個檔案並將"複製到輸出目錄 中 屬性 視窗變更為 一律複製
 
10. 在檔案頂端，加入現有的 'using' 陳述式清單中的下列： 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. 在 「 靜態 void Main(...)"，新增下列程式碼：
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. 組建]-> [建置方案
 
13. 開啟命令提示字元包含已編譯的.exe (例如 C:\MyProjects\HoloLensDeploymentFix\bin\Debug) 的資料夾
 
14. 執行可執行檔，並提供裝置的 IP 位址，做為命令列引數。  （如果透過 USB 連接，您可以使用 127.0.0.1，否則請使用裝置的 WiFi IP 位址。）例如，"HoloLensDeploymentFix 127.0.0.1"
 
15. 一旦此工具已結束但沒有任何訊息 （這應該只需要幾秒鐘的時間），您現在將能夠部署和偵錯從 Visual Studio 2017 或更新版本。  不需要繼續的使用此工具。

我們將進一步提供可用的更新。

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>啟動 Microsoft Store 和 HoloLens 上的應用程式的問題

>[!NOTE]
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

此外，如同我們使用所有 HoloLens OS 發行版本一樣，我們有張貼 FFU 映像至 Microsoft 下載中心 https://aka.ms/hololensdownload/10.0.17763.380 。 

如果您不想要取得更新，我們發行了新版本的 Microsoft Store UWP 應用程式自 3/29。 一旦您有更新的版本存放區：

1) 開啟存放區，並確認它會載入。
2) 您可以使用 Bloom 筆勢來開啟的功能表。
3) 嘗試開啟先前中斷的應用程式
3) 如果仍然無法啟動，點選 按住中斷的應用程式的圖示並選取 解除安裝。
4) Resinstall 這些來自市集的應用程式。

如果您的裝置仍然無法載入應用程式，您可以側載的版本的.NET 原生架構和執行階段透過 「 下載中心 」 這麼做：

1)  請下載[此 zip 檔案](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)從 Microsoft 下載中心取得。  解壓縮，將會產生兩個檔案。  Microsoft.NET.Native.Runtime.1.7.appx 和 Microsoft.NET.Native.Framework.1.7.appx
2)  請確認您的裝置是開發人員解除鎖定。  如果您尚未這麼做的指示之前完成[此處](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)。
3)  接著您要進入 Windows Device Portal。  我們的建議是，若要這樣做透過 USB 和您一樣的輸入 http://127.0.0.1:10080 貼入瀏覽器。  
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
* 在部署您的 HoloLens 從 Visual Studio 應用程式時，您可能會看到錯誤：**要求的作業無法對具有對應的使用者 區段開啟的檔案。(發生例外狀況於 HRESULT:0x800704C8)** 。 如果發生這種情況，再試一次您的部署通常會成功。

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
