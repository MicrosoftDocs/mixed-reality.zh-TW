---
title: 版本資訊-2016 年 8 月
description: HoloLens Windows 10 年度版 (2016 年秋季) 的版本資訊
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 版本資訊、 作業系統、 平台、 功能、 commercial suite，
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596356"
---
# <a name="release-notes---august-2016"></a>版本資訊-2016 年 8 月

HoloLens 小組歡迎提供意見，從開發人員在 Windows Insider 計劃，來排定工作的優先順序。 請繼續[提供意見反應](give-us-feedback.md)意見反應中樞，透過[開發人員論壇](https://forums.hololens.com)並[透過 Twitter @HoloLens ](https://twitter.com/hololens)。 為 Windows 10 年度更新版，HoloLens 小組很高興能提供的環節進一步提升至全像攝影版的體驗。 在此更新中，我們會著重於主要修正、 改進及要求的企業，而且可在 Microsoft HoloLens Commercial Suite 簡介的功能。

**最新版本：** Windows 全像攝影版的年 8 月 2016年更新 (**10.0.14393.0**，Windows 10 年度版)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

若要[目前的版本更新](updating-hololens.md)，開啟*設定*應用程式，移至*更新與安全性*，然後選取*檢查更新*按鈕。

## <a name="new-features"></a>新功能

**附加至處理序偵錯**HoloLens 現在支援附加-至-處理序偵錯。 您可以使用 Visual Studio 2015 Update 3 連線到 HoloLens 上執行的應用程式和[開始偵錯](using-visual-studio.md#debugging-an-installed-or-running-app)。 這適用於不需要從 Visual Studio 專案進行部署。

**更新 HoloLens 模擬器**我們也發行了 HoloLens 模擬器的更新的版本。

**遊戲台支援**現在可以配對，並使用藍芽舵 HoloLens 與 ！ 新發行的 Xbox 無線控制器 S 藍芽功能的功能，而且可用來播放您最愛的遊戲台啟用遊戲和應用程式。 A[控制器更新](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)則必須先在 Xbox 無線控制器 S 交流 HoloLens 套用。 Xbox 無線控制器 S 受到[XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)並[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) Api。 可透過存取其他模型的藍牙控制器[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API。

## <a name="improvements-and-fixes"></a>改進功能與修正

我們是與其餘的 Windows 10 年度更新版，同步的因此除了 Hololens 特定修正程式，您也收到所有優點從 Windows update，以提高平台的可靠性和效能。 您的意見反應是高值及針對修正版本中設定優先順序。

我們已改進下列體驗：
* 登入體驗。
* 加入工作地點。
* 裝置的電源狀態轉換的電源效率。
* 使用混合實境擷取的穩定性。
* 藍牙連線的可靠性
* 在多個應用程式案例的全像持續性。

我們已修正下列問題：
* Visual Studio 分析工具和圖形偵錯工具無法連線。
* 相片和文件不會出現在檔案總管 中，在裝置入口網站中。
* 當游標置於上方調整模式中，可以閃爍應用程式列中。
* 在 [調整] 模式中，眼睛視線點游標會變更為 4 箭號游標一段時間更慢。
* 「 嘿 Cortana 播放音樂 」 不會啟動 Groove。
* 上一個更新之後，"Home 移"說不會顯示 pin 面板正確。

## <a name="introducing-microsoft-hololens-commercial-suite"></a>簡介 Microsoft HoloLens 商業套件

Microsoft HoloLens Commercial Suite，可供企業部署。 我們已新增數個高要求[商業功能](commercial-features.md)從我們早期的商業夥伴。

請連絡當地的 Microsoft 客戶經理，購買 Microsoft HoloLens Commercial Suite。

### <a name="key-commercial-features"></a>重要的商業功能 

* **Kiosk 模式。** HoloLens kiosk 模式中，您可以限制哪些應用程式來執行以啟用示範或展示的體驗。<br>
  ![使用 kiosk 模式時，直接在您選擇的應用程式會啟動 HoloLens。](images/201608-kioskmode-400px.png)
* **HoloLens 的行動裝置管理 (MDM)。** 您的 IT 部門可以管理多個的 HoloLens 裝置同時使用 Microsoft Intune 等的解決方案。 您可以管理設定、選取要安裝的應用程式，並且設定針對您組織所需來量身訂做的安全性設定。<br>
  ![HoloLens 上的行動裝置管理提供企業級裝置管理跨多個裝置。](images/201608-enterprisemanagement-400px.png)
* **Windows Update for Business。** 控制裝置和長期維護分支的支援的作業系統更新。
* **資料安全性。** HoloLens 上已啟用 BitLocker 資料加密，以提供相同等級的任何其他 Windows 裝置的安全性保護。
* **公司存取。** 您的組織中的任何人可以遠端連線到公司網路時透過 HoloLens 上的虛擬私人網路。 HoloLens 也可以存取需要認證的 Wi-fi 網路。
* **Microsoft Store for Business。** 您的 IT 部門也可以設定企業的私用存放區，其中包含只供特定的 HoloLens 使用貴公司的應用程式。 安全地散發您的企業軟體，為選取的企業使用者的群組。

### <a name="development-edition-vs-commercial-suite"></a>Development Edition 和。Commercial Suite，

<table>
<tr>
<th>功能</th><th>Development 版</th><th>Commercial Suite，</th>
</tr><tr>
<td>裝置加密 (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>虛擬私人網路 (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk 模式</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 管理和部署</th>
</tr><tr>
<td>行動裝置管理 (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>封鎖取消註冊的能力</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>憑證為基礎的公司 Wi-fi 存取</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store （消費者）</td><td style="text-align: center;">取用者</td><td style="text-align: center;">透過 MDM 進行篩選</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">企業市集入口網站</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 安全性和身分識別</th>
</tr><tr>
<td>使用 Azure Active Directory (AAD) 的登入</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>使用 Microsoft 帳戶 (MSA) 登入</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>下一步 的產生認證，使用 PIN 解除鎖定</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">安全開機</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 服務與支援</th>
</tr><tr>
<td>自動系統更新到達</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>長期維護分支</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>先前的版本資訊
* [版本資訊-2016 5 月](release-notes-may-2016.md)
* [版本資訊-2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [HoloLens 的已知問題](hololens-known-issues.md)
* [商業功能](commercial-features.md)
* [安裝工具](install-the-tools.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
