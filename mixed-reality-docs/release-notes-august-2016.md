---
title: 版本資訊-2016 年8月
description: Windows 10 年度版本的 HoloLens 版本資訊（2016年）
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，版本資訊，os，平臺，功能，商業套件
ms.openlocfilehash: dcac64524cd8d1b1f2b0a496c4dcd2ad2fc7b690
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438099"
---
# <a name="release-notes---august-2016"></a>版本資訊-2016 年8月

HoloLens 團隊正在接聽 Windows 測試人員計畫中的開發人員意見反應，以排定工作的優先順序。 請透過 @HoloLens，繼續提供意見反應中樞、[開發人員論壇](https://forums.hololens.com)和[Twitter](https://twitter.com/hololens)的[意見反應給我們](give-us-feedback.md)。 隨著 Windows 10 的年度更新，HoloLens 團隊很高興能為全像攝影體驗提供進一步的改進。 在此更新中，我們著重于主要的修正程式、改良功能，以及企業所要求並可在 Microsoft HoloLens 商業套件中取得的功能。

**最新版本：** Windows 全像2016年8月更新（**10.0.14393.0**，windows 10 年度發行版本）

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

若要[更新為目前的版本](updating-hololens.md)，請開啟 [*設定*] 應用程式，移至 [*更新 & 安全性*]，然後選取 [*檢查更新*] 按鈕。

## <a name="new-features"></a>新功能

**附加至進程的調試**程式HoloLens 現在支援附加至進程的偵錯工具。 您可以使用 Visual Studio 2015 Update 3 來連線至 HoloLens 上執行中的應用程式，並[開始對其進行調試](using-visual-studio.md#debugging-an-installed-or-running-app)。 這種方式不需要從 Visual Studio 專案進行部署。

**已更新 HoloLens 模擬器**我們也已發行 HoloLens 模擬器的更新版本。

**遊戲台支援**您現在可以將藍牙遊戲台與 HoloLens 配對！ 新發行的 Xbox 無線控制器具有藍牙功能，可用來播放您最愛的遊戲和應用程式。 您必須先套用[控制器更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)，才能將 Xbox 無線控制器與 HoloLens 連接。 Xbox 無線控制器支援[XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)和[Windows 遊戲。輸入](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx)api。 您可以透過[Windows. 遊戲輸入](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx)API 來存取其他的藍牙控制器型號。

## <a name="improvements-and-fixes"></a>改良功能與修正

我們會與其余的 Windows 10 年度更新版同步，因此除了 HoloLens 特有的修正程式之外，您也會收到 Windows update 的所有好處，以提高平臺的可靠性和效能。 您的意見反應具有高價值，且優先于版本中的修正。

我們已改善下列體驗：
* 登入體驗。
* 加入工作場所。
* 裝置電源狀態轉換的電源效率。
* 混合現實的穩定性。
* 藍牙連線能力的可靠性
* 多個應用程式案例中的全息影像持續性。

我們已修正下列問題：
* Visual Studio 分析工具和圖形偵錯工具無法連接。
* 相片 & 檔不會顯示在裝置入口網站的檔案瀏覽器中。
* 當游標放在調整模式的上方時，應用程式行就會閃爍。
* 當處於調整模式時，眼睛點游標將會變得更慢。
* 「嗨，Cortana play 音樂」並不會啟動 Groove。
* 在上一次更新之後，表示 "Go Home" 不會正確顯示 pin 面板。

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Microsoft HoloLens 商業套件簡介

Microsoft HoloLens 商業套件已準備好進行企業部署。 我們已從我們的早期企業合作夥伴新增數個高度要求的[商業功能](commercial-features.md)。

請洽詢您當地的 Microsoft 帳戶經理，以購買 Microsoft HoloLens 商用套件。

### <a name="key-commercial-features"></a>主要的商業功能 

* **Kiosk 模式。** 使用 HoloLens kiosk 模式時，您可以限制要執行哪些應用程式，以啟用示範或展示體驗。<br>
  以 kiosk 模式 ![，HoloLens 會直接啟動您選擇的應用程式。](images/201608-kioskmode-400px.png)
* **適用于 HoloLens 的行動裝置管理（MDM）。** 您的 IT 部門可以使用 Microsoft Intune 之類的解決方案同時管理多個 HoloLens 裝置。 您可以管理設定、選取要安裝的應用程式，並且設定針對您組織所需來量身訂做的安全性設定。<br>
  HoloLens 上的 ![行動裝置管理可提供跨多個裝置的企業級裝置管理。](images/201608-enterprisemanagement-400px.png)
* **商務用 Windows Update。** 對裝置進行受控制的作業系統更新，並支援長期維護分支。
* **資料安全性。** HoloLens 上已啟用 BitLocker 資料加密，以提供與任何其他 Windows 裝置相同層級的安全性保護。
* **工作存取。** 您組織中的任何人都可以透過 HoloLens 上的虛擬私人網路，從遠端連線到公司網路。 HoloLens 也可以存取需要認證的 Wi-fi 網路。
* **商務用 Microsoft Store。** 您的 IT 部門也可以設定企業私人存放區，只包含您的公司應用程式，以符合您特定的 HoloLens 使用量。 安全地將您的企業軟體散發給所選的企業使用者群組。

### <a name="development-edition-vs-commercial-suite"></a>開發版與商業套件

<table>
<tr>
<th>功能</th><th>開發版</th><th>商業套件</th>
</tr><tr>
<td>裝置加密（Bitlocker）</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>虛擬私人網路 (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk 模式</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 管理與部署</th>
</tr><tr>
<td>行動裝置管理 (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>封鎖取消註冊的能力</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>以憑證為基礎的公司 Wi-fi 存取</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store （取用者）</td><td style="text-align: center;">型</td><td style="text-align: center;">透過 MDM 篩選</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">商務商店入口網站</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 安全性和身分識別</th>
</tr><tr>
<td>使用 Azure Active Directory （AAD）登入</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>使用 Microsoft 帳戶（MSA）登入</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>具有 PIN 解除鎖定的下一代認證</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">安全開機</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 服務與支援</th>
</tr><tr>
<td>自動的系統更新</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">商務用 Windows Update</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>長期維護分支</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>先前的版本資訊
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>請參閱
* [HoloLens 的已知問題](hololens-known-issues.md)
* [商業功能](commercial-features.md)
* [安裝工具](install-the-tools.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
