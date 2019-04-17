---
title: HoloLens 上的帳戶
description: 如何設定和管理 HoloLens 上的使用者帳戶。
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 使用者、 帳戶、 aad、 adfs、 microsoft 帳戶、 msa、 認證
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591744"
---
# <a name="accounts-on-hololens"></a>HoloLens 上的帳戶

初始 HoloLens 在安裝期間，使用者才能使用它們想要在裝置上使用的帳戶登入。 此帳戶可以是消費者 Microsoft 帳戶或企業帳戶已設定 Azure Active Directory (AAD) 或 Active Directory Federation Services (ADFS) 中。

登入此帳戶，在安裝期間建立的使用者設定檔，使用者可以用來在裝置上登入，而是針對哪些所有的應用程式會將其資料儲存。 這個相同的帳戶也提供單一登入應用程式，例如邊緣或透過 Windows 的帳戶管理員 Api 的 Skype。

此外，當登入企業或組織帳戶，在裝置上的，它可能也適用於行動裝置管理 (MDM) 原則，如果您的 IT 系統管理員所設定

每當裝置重新啟動或從待命狀態恢復時，此帳戶的認證可再次登入。 如果設定中已啟用 [強制執行明確的登入] 選項，使用者必須再次輸入其認證。 每當接收和套用 OS 更新之後重新啟動裝置，明確的登入需要。

## <a name="multi-user-support"></a>多使用者支援

>[!NOTE]
>多使用者支援需要 Commercial Suite，，，因為這是[Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise)功能。

開頭[Windows 10 April 2018 Update](release-notes-april-2018.md)，HoloLens 支援從相同的 AAD 租用戶內的多個使用者。 若要使用此選項必須設定裝置一開始使用屬於貴組織的帳戶。 接著，從相同的租用戶的其他使用者能夠登入裝置的登入畫面或依序點選 開始面板上的 使用者 圖格，以將現有的使用者登出。 

在裝置上安裝的應用程式可供所有其他使用者，但每個都會有自己的應用程式資料和喜好設定。 移除應用程式也會移除它為所有其他使用者不過。 

您可以將裝置的使用者移除裝置，以回收空間，請移至 設定 > 帳戶 > 其他人。 這也會從裝置移除所有其他使用者的應用程式資料。 

## <a name="linked-accounts"></a>連結的帳戶

在單一裝置帳戶中，使用者可以連結其他 web 為了更容易存取應用程式 （例如存放區） 內的帳戶認證或結合個人與工作資源，類似於 Windows 的桌面版本的存取權。 登入額外的帳戶，以這種方式不分隔在裝置上，例如映像所建立的使用者資料，或下載。 一旦帳戶已連線至裝置，可以將應用程式使用它與您的權限來減少需要個別登入每個應用程式。

## <a name="using-single-sign-on-within-an-app"></a>使用單一登入應用程式中

身為應用程式開發人員，您可以利用與 HoloLens 上擁有的已連線的身分識別[Windows 帳戶管理員 Api](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx)，就像您一樣的其他 Windows 裝置。 這些 Api 的某些程式碼範例可[此處](http://go.microsoft.com/fwlink/p/?LinkId=620621)。

帳戶資訊，例如要求的使用者可能會發生任何帳戶插斷同意，當應用程式會要求驗證權杖時，就必須處理雙因素驗證等。

如果您的應用程式需要特定的帳戶類型，先前尚未連結，您的應用程式可以要求系統將提示使用者將其加入。 這會觸發啟動為強制回應的子系，您的應用程式的 [帳戶設定] 窗格。 2D 應用程式，此視窗會呈現直接透過您的應用程式，以及 Unity 應用程式的中心，這將會簡短需要將使用者登出您全像攝影版的應用程式，以便可以轉譯此子視窗。 自訂命令和動作，針對此窗格會描述[此處](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx)。

## <a name="enterprise-and-other-authentication"></a>企業及其他驗證

如果您的應用程式會使用其他類型的驗證，例如 NTLM、 Basic 或 Kerberos，您可以使用[Windows 認證 UI](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx)收集、 處理及儲存使用者的認證。 收集這些認證的使用者經驗非常類似其他以雲端為導向帳戶插斷和將會顯示為您的 2D 應用程式最上層的子應用程式或簡短地暫停 Unity 應用程式中顯示 UI。

## <a name="deprecated-apis"></a>已被取代的 Api

從 Desktop 的 HoloLens 上開發的其中一項差異在於[OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx)不完全支援的 API。 雖然它會傳回權杖的主要帳戶是否在良好地位，中斷這類以上所述將不會顯示任何使用者的 UI，並將無法正確驗證帳戶。

