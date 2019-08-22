---
title: HoloLens 的已知問題
description: 這是可能會影響 HoloLens 開發人員的已知問題清單。
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: 疑難排解, 已知問題, 協助
ms.openlocfilehash: f043164f21f20925a78b59057e14ac4607d0d3f1
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896539"
---
# <a name="hololens-known-issues"></a>HoloLens 的已知問題

這是 HoloLens 影響開發人員的目前已知問題清單。 如果您看到奇怪的行為, 請先查看這裡。 當發現或回報新問題, 或在未來的 HoloLens 軟體更新中解決問題時, 這份清單將會保持更新。

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>無法透過 Visual Studio 連線並部署至 HoloLens

>[!NOTE]
>上次更新日期:8/8 @ 5: Visual Studio 晚上11點已發行 VS 2019 16.2 版, 其中包含此問題的修正。 我們建議您更新到這個最新版本, 以避免發生此錯誤。

Visual Studio 已發行 VS 2019 16.2 版, 其中包含此問題的修正。 我們建議您更新到這個最新版本, 以避免發生此錯誤。

問題根本原因:使用 Visual Studio 2015 或舊版 Visual Studio 2017 的使用者在其 HoloLens 上部署和偵測應用程式, 然後再使用相同 HoloLens 的最新版本 Visual Studio 2017 或 Visual Studio 2019 將會受到影響。 較新版本的 Visual Studio 會部署新版的元件, 但較舊版本的檔案會保留在裝置上, 導致較新的版本失敗。  這會導致下列錯誤訊息:DEP0100:請確定目標裝置已啟用開發人員模式。 <ip>因錯誤80004005而無法取得開發人員授權。
 
**因應措施**： 

我們的團隊目前正在努力修正。 在此同時, 您可以使用下列步驟來解決問題, 並協助解除封鎖部署和調試:  
1. 開啟 Visual Studio
2. 檔案 > 新 > 專案
3. Visual C# > Windows 桌面 > 主控台應用程式 (.NET Framework)
4. 提供專案的名稱 (例如 HoloLensDeploymentFix), 並確定架構設定為至少 .NET Framework 4.5, 然後按一下 [確定]。
5. 以滑鼠右鍵按一下方案總管中的 [參考] 節點, 並新增下列參考 (按一下 [流覽] 區段, 然後按一下 [流覽 ...]按鈕):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >如果您尚未安裝 10.0.18362.0, 請使用您所擁有的最新版本。
 
6. 以滑鼠右鍵按一下方案總管中的專案, 然後選擇 [加入 >] [現有專案]。
 
7. 流覽至 C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86, 並將篩選準則變更為 "All\*Files\*(.)"
 
8. 選取 [SirepClient] 和 [SshClient], 然後按一下 [新增]。
 
9. 在方案總管中找出並選取這兩個檔案 (它們應該位於檔案清單的底部), 然後在屬性視窗中將 [複製到輸出目錄] 變更為 [永遠複製]
 
10. 在檔案的頂端, 將下列內容新增至現有的 ' using ' 語句清單: 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. 在 "static void Main (...)" 內, 新增下列程式碼:
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. 組建 > 組建解決方案
 
13. 在包含已編譯 .exe 的資料夾中開啟命令提示字元 (例如 C:\MyProjects\HoloLensDeploymentFix\bin\Debug)
 
14. 執行可執行檔, 並提供裝置的 IP 位址做為命令列引數。  (如果透過 USB 連線, 您可以使用 127.0.0.1, 否則請使用裝置的 WiFi IP 位址)。例如, "HoloLensDeploymentFix 127.0.0.1"
 
15. 一旦工具結束但沒有任何訊息 (這應該只需要幾秒鐘的時間), 您現在就可以從 Visual Studio 2017 或更新版本進行部署和偵錯工具。  不需要繼續使用此工具。

我們將在提供進一步的更新。

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>在 HoloLens 上啟動 Microsoft Store 和應用程式的問題

>[!NOTE]
>上次更新日期:4/2 @ 10 AM-已解決問題。 

當您嘗試在 HoloLens 上啟動 Microsoft Store 和應用程式時, 可能會遇到問題。 我們已判定當背景應用程式更新在特定序列中部署較新版本的 framework 套件, 而其中一或多個相依應用程式仍在執行時, 就會發生此問題。 在此情況下, 自動應用程式更新已提供新版的 .NET Native Framework (10.0.25531 到 10.0.27413), 導致執行的應用程式無法針對所有使用舊版 Framework 的執行中應用程式進行正確更新。  架構更新的流程如下所示:

1.  新的架構套件會從存放區下載並安裝
2.  所有使用舊版架構的應用程式都會「更新」, 以使用較新的版本

如果步驟2在完成前中斷, 則未註冊新架構的任何應用程式都將無法從 [開始] 功能表啟動。  我們相信 HoloLens 上的任何應用程式可能會受到此問題的影響。

有些使用者已回報關閉無回應應用程式並啟動其他應用程式 (例如意見反應中樞、3D 檢視器或相片) 可解決問題; 不過, 這不會在 100% 的時間內生效。

根本原因是此問題不會造成更新本身, 但是作業系統中導致 .NET Native framework 更新的錯誤處理不正確。 我們很高興宣佈, 我們已識別出修正程式, 並已發行包含修正程式的更新 (OS 版本 17763.380)。 

若要查看您的裝置是否可以進行更新, 請:

1.  移至 [設定] 應用程式, 並開啟 [更新 & 安全性]
2.  按一下 [檢查更新]
3.  如果有17763.380 的更新可用, 請更新為此組建, 以接收應用程式停止回應 bug 的修正
4.  更新為此版本的 OS 時, 應用程式應該會如預期般運作。

此外, 在每次 HoloLens 作業系統版本中, 我們已將 FFU 映射張貼到 Microsoft 下載中心, 網址 https://aka.ms/hololensdownload/10.0.17763.380 為。 

如果您不想要進行更新, 我們已發行新版本的 Microsoft Store UWP 應用程式, 3/29。 當您擁有更新版本的存放區之後:

1) 開啟存放區, 並確認它已載入。
2) 使用 Bloom 手勢來開啟功能表。
3) 嘗試開啟先前中斷的應用程式
3) 如果仍然無法啟動, 請按住中斷應用程式的圖示, 然後選取 [卸載]。
4) 從存放區 Resinstall 這些應用程式。

如果您的裝置仍然無法載入應用程式, 您可以執行下列動作, 透過下載中心側載某個版本的 .NET Native Framework 和執行時間:

1)  請從 Microsoft 下載中心下載[此 zip](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)檔案。  解壓縮會產生兩個檔案。  NET.TCP 和 net.tcp. .appx........。
2)  請確認您的裝置已針對開發人員解除鎖定。  如果您還沒有這麼做, 請在[這裡](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)進行操作。
3)  接著, 您會想要進入 Windows 裝置入口網站。  我們的建議是透過 USB 來執行這項操作, 您可以在 http://127.0.0.1:10080 瀏覽器中輸入來執行這項操作。  
4)  當您完成 Windows 裝置入口網站後, 我們需要您「側載入」您所下載的兩個檔案。  若要這麼做, 您必須往下移至 [應用程式] 區段, 然後按一下 [應用程式]。
5)  然後您會看到類似下面的畫面。  您想要移至顯示「安裝應用程式」的區段, 然後流覽至您解壓縮這兩個 APPX 檔案的位置。  您一次只能執行一個, 因此在您選取第一個, 然後按一下 [部署] 區段下的 [移至]。  然後為第二個 APPX 檔案執行此動作。 
  ![安裝側載應用程式的 Windows 裝置入口網站](images/20190322-DevicePortal.png)<br>
6)  此時, 我們認為您的應用程式應該會再次開始運作, 而且您也可以取得存放區。
7)  在某些情況下, 必須先執行額外的步驟來啟動3D 檢視器應用程式, 受影響的應用程式才會啟動。 

我們非常感謝您的耐心等候, 因為我們已完成解決此問題的流程, 我們期待繼續與我們的社區合作, 以建立成功的混合現實體驗。

## <a name="connecting-to-wifi"></a>連接到 WiFi

在 OOBE & 設定期間, 有2分鐘的認證超時。 使用者名稱/密碼必須在2分鐘內輸入, 否則 [使用者名稱] 欄位將會自動清除。

我們建議使用藍牙鍵盤來輸入長密碼。

>[!NOTE]
> 如果在 OOBE 期間選取了錯誤的網路, 裝置就必須完全重設。 您可以在這裡找到指示[。](https://docs.microsoft.com/en-us/windows/mixed-reality/reset-or-recover-your-hololens#perform-a-full-device-recovery) 

## <a name="device-update"></a>裝置更新
* 在新的更新之後30秒, shell 可能會消失一次。 請執行**bloom**手勢來繼續您的會話。

## <a name="visual-studio"></a>Visual Studio
* 如需適用于 HoloLens 開發的最新版本 Visual Studio, 請參閱[安裝工具](install-the-tools.md)。
* 將應用程式從 Visual Studio 部署至 HoloLens 時, 您可能會看到下列錯誤:**無法在開啟使用者對應區段的檔案上執行要求的作業。(發生例外狀況於 HRESULT:0x800704C8)** 。 如果發生這種情況, 請再試一次, 您的部署通常會成功。

## <a name="emulator"></a>模擬器
* 並非 Microsoft Store 中的所有應用程式都與模擬器相容。 例如, 在模擬器上無法播放年輕 Conker 和片段。
* 您無法在模擬器中使用電腦網路攝影機。
* Windows 裝置入口網站的 [即時預覽] 功能無法與模擬器搭配使用。 您仍然可以捕捉混合現實影片和影像。

## <a name="unity"></a>Unity
* 如需 HoloLens 開發的最新版本建議, 請參閱[安裝工具](install-the-tools.md)。
* Unity HoloLens Technical Preview 的已知問題記載于[HoloLens Unity 論壇](http://forum.unity3d.com/threads/known-issues.394627/)。

## <a name="windows-device-portal"></a>Windows Device Portal
* 混合現實 capture 中的即時預覽功能可能會出現數秒的延遲。
* 在 [虛擬輸入] 頁面上, [虛擬手勢] 區段下的筆勢和 Scroll 控制項無法正常運作。 使用它們將不會有任何作用。 相同頁面上的虛擬鍵盤運作正常。
* 啟用 [設定] 中的 [開發人員模式] 之後, 可能需要幾秒鐘的時間, 才能開啟啟用裝置入口網站的交換器。

## <a name="api"></a>API
* 如果應用程式將使用者背後的[焦點點](focus-point-in-unity.md)設定為, 或將其設為一般相機。轉寄, 則全像投影不會出現在混合現實的 Capture 相片或影片中。 在 Windows 中修正此錯誤之前, 如果應用程式主動設定[焦點](focus-point-in-unity.md), 則應該確保平面的垂直方向是設定為與相機向前 (例如, normal =-攝影機)。

## <a name="xbox-wireless-controller"></a>Xbox 無線控制器
* Xbox 無線控制器必須先更新, 才能與 HoloLens 搭配使用。 請確定您是[最](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)新的, 再嘗試將控制器與 HoloLens 配對。
* 如果您在 Xbox 無線控制器連線時重新開機 HoloLens, 控制器將不會自動重新連接至 HoloLens。 在3分鐘後控制器電源關閉後, 此指南按鈕 light 會慢慢閃爍。 若要立即重新連線您的控制器, 請按住 [節目表] 按鈕以關閉控制器電源, 直到燈關閉為止。 當您再次開啟控制器電源時, 它會重新連線至 HoloLens。
* 如果您的 HoloLens 在 Xbox 無線控制器連線時進入待命, 控制器上的任何輸入都會喚醒 HoloLens。 您可以在使用完控制器後關閉它, 藉此避免發生這種情況。
