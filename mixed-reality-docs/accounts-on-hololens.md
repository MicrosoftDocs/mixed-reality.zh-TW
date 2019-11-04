---
title: HoloLens 上的帳戶
description: 如何在 HoloLens 上設定和管理使用者帳戶。
author: tmlyon
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，使用者，帳戶，aad，adfs，microsoft 帳戶，msa，認證
ms.openlocfilehash: 5579cf53948b8bdbd4b41973dde7b8fc70a5aa31
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437091"
---
# <a name="accounts-on-hololens"></a>HoloLens 上的帳戶

在初始 HoloLens 設定期間，使用者必須使用他們想要在裝置上使用的帳戶登入。 此帳戶可以是取用者 Microsoft 帳戶或已在 Azure Active Directory （AAD）或 Active Directory 同盟服務（ADFS）中設定的企業帳戶。

在安裝期間登入此帳戶會在裝置上建立使用者設定檔，以供使用者用來登入，並針對所有應用程式儲存其資料。 這個相同的帳戶也會透過 Windows 帳戶管理員 Api，為 Edge 或 Skype 等應用程式提供單一登入。

此外，登入裝置上的企業或組織帳戶時，如果您的 IT 系統管理員設定，它也可能套用行動裝置管理（MDM）原則。

每當裝置重新開機或從待命狀態恢復時，就會使用此帳戶的認證重新登入。 如果已在 [設定] 中啟用 [強制執行明確登入] 選項，使用者就必須再次輸入其認證。 每當裝置在收到並套用 OS 更新之後重新開機時，就需要明確的登入。

## <a name="multi-user-support"></a>多使用者支援

>[!NOTE]
>多使用者支援需要商業套件，因為這是 Windows 全像[企業版的](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise)功能。

從[Windows 10 2018 年4月更新](release-notes-april-2018.md)開始，HoloLens 可支援同一個 AAD 租使用者內的多個使用者。 若要使用此設定，您必須先使用屬於貴組織的帳戶來設定裝置。 之後，來自相同租使用者的其他使用者將能夠從登入畫面登入裝置，或透過在 [開始] 面板上按使用者磚來登出現有的使用者。 

安裝在裝置上的應用程式將可供所有其他使用者使用，但每個都有自己的應用程式資料和喜好設定。 不過，移除應用程式也會將它移除給所有其他使用者。 

您可以移至 [設定] [> 帳戶] > [其他人]，從裝置移除裝置使用者以回收空間。 這也會從裝置移除所有其他使用者的應用程式資料。 

## <a name="linked-accounts"></a>連結的帳戶

在單一裝置帳戶內，使用者可以連結額外的 web 帳號憑證，以便在應用程式（例如存放區）中更容易存取，或結合個人和工作資源的存取，類似于桌上出版本的 Windows。 以這種方式登入其他帳戶並不會區分裝置上建立的使用者資料，例如影像或下載。 一旦帳戶已連線到裝置，應用程式就可以使用它與您的許可權，以減少每個應用程式的個別登入。

## <a name="using-single-sign-on-within-an-app"></a>在應用程式內使用單一登入

身為應用程式開發人員，您可以利用[Windows 帳戶管理員 api](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx)在 HoloLens 上擁有連線的身分識別，就像您在其他 windows 裝置上所做的一樣。 [這裡](https://go.microsoft.com/fwlink/p/?LinkId=620621)提供這些 api 的一些程式碼範例。

任何可能發生的帳戶中斷，例如要求帳戶資訊的使用者同意、雙因素驗證等，都必須在應用程式要求驗證權杖時處理。

如果您的應用程式需要先前尚未連結的特定帳戶類型，您的應用程式可以要求系統提示使用者加入一個。 這會觸發 [帳戶設定] 窗格以應用程式的模式子系啟動。 針對2D 應用程式，此視窗會直接呈現在您應用程式的中央，而對於 Unity 應用程式，這會將使用者短暫地移出您的全像應用程式，以便呈現這個子視窗。 [這裡](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx)會說明自訂此窗格的命令和動作。

## <a name="enterprise-and-other-authentication"></a>企業和其他驗證

如果您的應用程式會使用其他類型的驗證（例如 NTLM、Basic 或 Kerberos），您可以使用[Windows 認證 UI](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx)來收集、處理及儲存使用者的認證。 收集這些認證的使用者體驗非常類似于其他雲端驅動帳戶的插斷，並會在您的2D 應用程式頂端顯示為子應用程式，或暫時暫止 Unity 應用程式以顯示 UI。

## <a name="deprecated-apis"></a>已淘汰的 Api

從桌面開發 HoloLens 的一項差異是，不完全支援[OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API。 雖然它會在主要帳戶是良好的情況下傳回權杖，但類似上述的中斷不會顯示使用者的任何 UI，也無法正確驗證帳戶。

