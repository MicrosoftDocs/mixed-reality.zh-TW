---
title: 使用全像攝影遠端建立安全連線
description: 此頁面說明如何在使用全像攝影遠端時建立安全的加密連接。
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 5bc039d7a1e500f577c4a30d2d082b718a45a8b4
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718072"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>使用全像攝影遠端建立安全連線

>[!IMPORTANT]
>本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。

此頁面說明如何在使用全像攝影遠端時建立安全的加密連接。

透過不安全的網路 (例如開啟的 WiFi 或網際網路) 將內容串流處理至 HoloLens 2 時, 強烈建議使用加密的連接。

>[!IMPORTANT]
>即使在使用受信任的本機 WiFi 時, 也應該考慮使用加密的連接。

若要能夠使用加密的連線, 您必須同時執行[自訂播放機](holographic-remoting-create-player.md)和[自訂主機應用程式](holographic-remoting-create-host.md)。

加密是透過使用基礎平臺的 TLS 實現來達成。

## <a name="basics-of-an-encrypted-connection"></a>加密連接的基本概念

下列物件必須實作為允許憑證交換。

>[!TIP]
>使用C++/winrt 可以輕鬆地執行 WinRT 介面 「[使用C++/WinRT 的作者 api](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/author-apis) 」章節會詳細說明這一點。

>[!IMPORTANT]
>NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```套件內的包含與安全連線相關之 API 的詳細檔。

1) 需要執行```ICertificate```介面的憑證物件。

    * 透過```GetCertificatePfx```方法傳回 pfx 憑證的二進位內容。 與 .pfx 檔案的二進位內容相同。
    * 透過```GetSubjectName```傳回憑證主體名稱。
    * 透過```GetPfxPassword```傳回 pfx 密碼。 針對未受保護的 pfx, 傳回空字串。

2) 執行```ICertificateProvider```介面的憑證提供者, 會在```GetCertificate```透過方法要求時提供憑證。

3) 執行```ICertificateValidator```介面的憑證驗證程式。 其工作是驗證傳入的憑證。
    * 當基礎平臺應驗證傳入的憑證鏈時, ```false``` 方法應該會傳回,否則會傳回。```PerformSystemValidation``` ```true```
    * ```ValidateCertificate```用戶端內容會呼叫以要求驗證憑證。 這個方法會接受憑證鏈 (使用第一個憑證作為主旨憑證)、與建立連線的伺服器名稱, 以及是否應該強制執行撤銷檢查。 如果已要求基礎系統的驗證, 則會提供系統驗證結果。 若要繼續處理```CertificateValidated``` , 請使用適當的```Cancel```結果, 或取消必須在傳遞```ICertificateValidationCallback```的上呼叫的驗證。

此外, 若要允許交換安全權杖, 則必須實作為下列物件。

1) 執行```IAuthenticationProvider```介面的驗證提供者。 客戶```GetToken```端內容會呼叫其方法來要求用戶端驗證的權杖。 若要繼續```TokenReceived```提供驗證權杖並繼續連線程式, 或```Cancel```取消處理常式必須在傳遞```IAuthenticationProviderCallback```的上呼叫。
2) 執行```IAuthenticationReceiver```介面的驗證接收器。 其工作是用來驗證傳入的權杖。
    * ```GetRealm```方法應該會傳回驗證領域的名稱。
    * ```ValidateToken```方法是由伺服器網路內容呼叫, 以要求驗證用戶端驗證權杖。 若要繼續呼叫```ValidationCompleted```以完成驗證, 或```Cancel```拒絕用戶端連接。 用戶端連接將會根據傳遞至```ValidationCompleted```的驗證結果而被承認或拒絕。 

一旦實作為這些物件```ListenSecure``` , 就必須呼叫```Listen``` , 而不```ConnectSecure```是, ```Connect```而不是在遠端內容和播放者內容上。 ```ListenSecure```需要額外的憑證提供者和驗證接收器```Listen```。 ```ConnectSecure```需要額外的驗證提供者和憑證驗證```Connect```程式。

## <a name="see-also"></a>另請參閱
* [撰寫全像的遠端主機應用程式](holographic-remoting-create-host.md)
* [撰寫自訂的全像遠端播放播放機應用程式](holographic-remoting-create-player.md)
* [全像攝影遠端疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)