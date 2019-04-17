---
title: 商業功能
description: Microsoft HoloLens Commercial Suite，包含可簡化管理 HoloLens 裝置的企業功能。
author: xerxesb85
ms.author: xerxesb
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 商業、 功能、 mdm、 行動裝置管理、 資訊站模式
ms.openlocfilehash: 5fd5c56983fb3e94376fac08c6e96510bccc0002
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597082"
---
# <a name="commercial-features"></a>商業功能

Microsoft HoloLens Commercial Suite，包含可簡化管理 HoloLens 裝置的企業功能。 商業功能隨附於 Windows 作業系統中，但它們會啟用授權。 在幾乎所有的情況下，授權會啟用 Microsoft 裝置管理組織中註冊的 HoloLens 時。 請連絡當地的 Microsoft 客戶經理，購買 Microsoft HoloLens Commercial Suite。

&nbsp;

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

## <a name="key-commercial-features"></a>重要的商業功能

* **Kiosk 模式。** HoloLens kiosk 模式中，您可以限制哪些應用程式來執行以啟用示範或展示的體驗。

  ![使用 kiosk 模式時，直接在您選擇的應用程式會啟動 HoloLens。](images/201608-kioskmode-400px.png)

* **HoloLens 的行動裝置管理 (MDM)。** 您的 IT 部門可以管理多個的 HoloLens 裝置同時使用 Microsoft Intune 等的解決方案。 您可以管理設定、選取要安裝的應用程式，並且設定針對您組織所需來量身訂做的安全性設定。

  ![HoloLens 上的行動裝置管理提供企業級裝置管理跨多個裝置。](images/201608-enterprisemanagement-400px.png)
  
* **Windows Update for Business。** 控制裝置和長期維護分支的支援的作業系統更新。
* **資料安全性。** HoloLens 上已啟用 BitLocker 資料加密，以提供相同等級的任何其他 Windows 裝置的安全性保護。
* **公司存取。** 您的組織中的任何人可以遠端連線到公司網路時透過 HoloLens 上的虛擬私人網路。 HoloLens 也可以存取需要認證的 Wi-fi 網路。
* **Microsoft Store for Business。** 您的 IT 部門也可以設定企業的私用存放區，其中包含只供特定的 HoloLens 使用貴公司的應用程式。 安全地散發您的企業軟體，為選取的企業使用者的群組。

## <a name="development-edition-vs-commercial-suite"></a>Development Edition 和。Commercial Suite，

<table>
<tr>
<th>功能</th><th>HoloLens Development 版</th><th>HoloLens 商業套件</th><th>HoloLens 2</th>
</tr><tr>
<td>裝置加密 (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>虛擬私人網路 (VPN)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk 模式</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 管理和部署</th>
</tr><tr>
<td>行動裝置管理 (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>封鎖取消註冊的能力</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>憑證為基礎的公司 Wi-fi 存取</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store （消費者）</td><td style="text-align: center;">取用者</td><td style="text-align: center;">透過 MDM 進行篩選</td><td style="text-align: center;">透過 MDM 進行篩選</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">企業市集入口網站</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 安全性和身分識別</th>
</tr><tr>
<td>使用 Azure Active Directory (AAD) 的登入</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>使用 Microsoft 帳戶 (MSA) 登入</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>下一步 的產生認證，使用 PIN 解除鎖定</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">安全開機</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 服務與支援</th>
</tr><tr>
<td>自動系統更新到達</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>長期維護分支</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>



## <a name="enabling-commercial-features"></a>啟用商業功能

商業功能，例如 Microsoft Store for Business，kiosk 模式及企業 Wi-fi 存取是由組織的設定 IT 系統管理員。[HoloLens Windows IT 中心](https://technet.microsoft.com/itpro/hololens/index)提供裝置註冊和安裝應用程式從 Microsoft Store for Business 中的逐步指示。

## <a name="see-also"></a>另請參閱
* [IT 專業人員指南 HoloLens](https://technet.microsoft.com/itpro/hololens/index)
* [Kiosk 模式](using-the-windows-device-portal.md#kiosk-mode)
* [在 Windows 全像攝影版企業支援的 Csp](https://msdn.microsoft.com/library/windows/hardware/dn920025(v=vs.85).aspx#HoloLens)
* [Microsoft Store 商務及企業營運應用程式](https://blogs.technet.microsoft.com/sbucci/2016/04/13/windows-store-for-business-and-line-of-business-applications/)
* [使用特定業務應用程式](https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps)
