---
title: 使用全像攝影遠端建立安全連線
description: 此頁面說明如何在使用全像攝影遠端時建立安全的加密連接。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278226"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>使用全像攝影遠端建立安全連線

>[!IMPORTANT]
>本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。

此頁面說明如何在使用全像攝影遠端時建立安全的加密連接。

透過不安全的網路（例如開啟的 WiFi 或網際網路）將內容串流處理至 HoloLens 2 時，強烈建議使用加密的連接。

>[!IMPORTANT]
>即使在使用受信任的本機 WiFi 時，也應該考慮使用加密的連接。

若要能夠使用加密的連線，您必須同時執行[自訂播放機](holographic-remoting-create-player.md)和[自訂遠端應用程式](holographic-remoting-create-host.md)。

加密是透過使用基礎平臺的 TLS 實現來達成。

## <a name="basics-of-an-encrypted-connection"></a>加密連接的基本概念

下列物件必須實作為允許憑證交換。

>[!TIP]
>使用C++/winrt 可以輕鬆地執行 WinRT 介面 「[使用C++/WinRT 的作者 api](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) 」章節會詳細說明這一點。

>[!IMPORTANT]
>NuGet 套件中的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包含與安全連線相關之 API 的詳細檔。

1) 需要執行 ```ICertificate``` 介面的憑證物件。

    * 透過 ```GetCertificatePfx``` 方法，傳回 pfx 憑證的二進位內容。 與 .pfx 檔案的二進位內容相同。
    * 透過 ```GetSubjectName```傳回憑證主體名稱。
    * 透過 ```GetPfxPassword```傳回 pfx 密碼。 針對未受保護的 pfx，傳回空字串。

2) 執行 ```ICertificateProvider``` 介面的憑證提供者，會在透過 ```GetCertificate``` 方法要求時提供憑證。

3) 執行 ```ICertificateValidator``` 介面的憑證驗證程式。 其工作是驗證傳入的憑證。
    * 當基礎平臺應驗證傳入的憑證鏈時 ```false```，```PerformSystemValidation``` 方法應該會傳回 ```true```，否則會傳回。
    * ```ValidateCertificate``` 由用戶端內容呼叫以要求驗證憑證。 這個方法會接受憑證鏈（使用第一個憑證作為主旨憑證）、與建立連線的伺服器名稱，以及是否應該強制執行撤銷檢查。 如果已要求基礎系統的驗證，則會提供系統驗證結果。 若要繼續以適當的結果處理 ```CertificateValidated```，或 ```Cancel``` 取消驗證，必須在傳遞的 ```ICertificateValidationCallback```上呼叫。

此外，若要允許交換安全權杖，則必須實作為下列物件。

1) 執行 ```IAuthenticationProvider``` 介面的驗證提供者。 用戶端內容會呼叫其 ```GetToken``` 方法來要求權杖以進行用戶端驗證。 若要繼續 ```TokenReceived``` 以提供驗證權杖，並繼續進行連線程式，或 ```Cancel``` 取消處理常式必須在傳遞的 ```IAuthenticationProviderCallback```上呼叫。
2) 執行 ```IAuthenticationReceiver``` 介面的驗證接收器。 其工作是用來驗證傳入的權杖。
    * ```GetRealm``` 方法應該會傳回驗證領域的名稱。
    * 伺服器網路內容會呼叫 ```ValidateToken``` 方法，以要求驗證用戶端驗證權杖。 若要繼續，請呼叫 ```ValidationCompleted``` 以指示完成驗證，或 ```Cancel``` 拒絕用戶端連接。 用戶端連接將會根據傳遞給 ```ValidationCompleted```的驗證結果來獲准或拒絕。 

一旦執行這些物件 ```ListenSecure``` 必須呼叫，而不是 ```Listen``` 和 ```ConnectSecure```，而不是分別在遠端內容和播放者內容上 ```Connect```。 ```ListenSecure``` 需要額外的憑證提供者和驗證接收器，而不是 ```Listen```。 ```ConnectSecure``` 需要額外的驗證提供者，以及透過 ```Connect```的憑證驗證程式。

## <a name="see-also"></a>另請參閱
* [撰寫全像攝影遠端應用程式](holographic-remoting-create-host.md)
* [撰寫自訂的全像遠端播放播放機應用程式](holographic-remoting-create-player.md)
* [全像攝影遠端疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
