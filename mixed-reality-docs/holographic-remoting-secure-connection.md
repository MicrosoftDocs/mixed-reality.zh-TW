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
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a><span data-ttu-id="58776-104">使用全像攝影遠端建立安全連線</span><span class="sxs-lookup"><span data-stu-id="58776-104">Establishing a secure connection with Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="58776-105">本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="58776-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="58776-106">此頁面說明如何在使用全像攝影遠端時建立安全的加密連接。</span><span class="sxs-lookup"><span data-stu-id="58776-106">This page explains how to establish a secure encrypted connection when using Holographic Remoting.</span></span>

<span data-ttu-id="58776-107">透過不安全的網路（例如開啟的 WiFi 或網際網路）將內容串流處理至 HoloLens 2 時，強烈建議使用加密的連接。</span><span class="sxs-lookup"><span data-stu-id="58776-107">When streaming content to HoloLens 2 over a insecure Network such as an open WiFi or the internet it is highly recommended to use an encrypted connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="58776-108">即使在使用受信任的本機 WiFi 時，也應該考慮使用加密的連接。</span><span class="sxs-lookup"><span data-stu-id="58776-108">Even when using a trusted local WiFi using an encrypted connection should be considered.</span></span>

<span data-ttu-id="58776-109">若要能夠使用加密的連線，您必須同時執行[自訂播放機](holographic-remoting-create-player.md)和[自訂遠端應用程式](holographic-remoting-create-host.md)。</span><span class="sxs-lookup"><span data-stu-id="58776-109">To be able to use a encrypted connection you will need to implement both a [custom player](holographic-remoting-create-player.md) and a [custom remote app](holographic-remoting-create-host.md).</span></span>

<span data-ttu-id="58776-110">加密是透過使用基礎平臺的 TLS 實現來達成。</span><span class="sxs-lookup"><span data-stu-id="58776-110">The encryption is achieved by using the underlying platforms TLS implementation.</span></span>

## <a name="basics-of-an-encrypted-connection"></a><span data-ttu-id="58776-111">加密連接的基本概念</span><span class="sxs-lookup"><span data-stu-id="58776-111">Basics of an encrypted connection</span></span>

<span data-ttu-id="58776-112">下列物件必須實作為允許憑證交換。</span><span class="sxs-lookup"><span data-stu-id="58776-112">The following objects need to be implemented to allow for a certificate exchange.</span></span>

>[!TIP]
><span data-ttu-id="58776-113">使用C++/winrt 可以輕鬆地執行 WinRT 介面</span><span class="sxs-lookup"><span data-stu-id="58776-113">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="58776-114">「[使用C++/WinRT 的作者 api](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) 」章節會詳細說明這一點。</span><span class="sxs-lookup"><span data-stu-id="58776-114">The [Author APIs with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="58776-115">NuGet 套件中的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包含與安全連線相關之 API 的詳細檔。</span><span class="sxs-lookup"><span data-stu-id="58776-115">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

1) <span data-ttu-id="58776-116">需要執行 ```ICertificate``` 介面的憑證物件。</span><span class="sxs-lookup"><span data-stu-id="58776-116">A certificate object, which needs to implement the ```ICertificate``` interface.</span></span>

    * <span data-ttu-id="58776-117">透過 ```GetCertificatePfx``` 方法，傳回 pfx 憑證的二進位內容。</span><span class="sxs-lookup"><span data-stu-id="58776-117">Return the binary contents of the pfx certificate through the ```GetCertificatePfx``` method.</span></span> <span data-ttu-id="58776-118">與 .pfx 檔案的二進位內容相同。</span><span class="sxs-lookup"><span data-stu-id="58776-118">Same as the binary contents of a .pfx file.</span></span>
    * <span data-ttu-id="58776-119">透過 ```GetSubjectName```傳回憑證主體名稱。</span><span class="sxs-lookup"><span data-stu-id="58776-119">Return the certificate subject name through ```GetSubjectName```.</span></span>
    * <span data-ttu-id="58776-120">透過 ```GetPfxPassword```傳回 pfx 密碼。</span><span class="sxs-lookup"><span data-stu-id="58776-120">Return the pfx password through ```GetPfxPassword```.</span></span> <span data-ttu-id="58776-121">針對未受保護的 pfx，傳回空字串。</span><span class="sxs-lookup"><span data-stu-id="58776-121">Return an empty string for an unprotected pfx.</span></span>

2) <span data-ttu-id="58776-122">執行 ```ICertificateProvider``` 介面的憑證提供者，會在透過 ```GetCertificate``` 方法要求時提供憑證。</span><span class="sxs-lookup"><span data-stu-id="58776-122">A certificate provider implementing the ```ICertificateProvider``` interface which provides a certificate when asked through the ```GetCertificate``` method.</span></span>

3) <span data-ttu-id="58776-123">執行 ```ICertificateValidator``` 介面的憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="58776-123">A certificate validator implementing the ```ICertificateValidator``` interface.</span></span> <span data-ttu-id="58776-124">其工作是驗證傳入的憑證。</span><span class="sxs-lookup"><span data-stu-id="58776-124">Its task is to verify incoming certificates.</span></span>
    * <span data-ttu-id="58776-125">當基礎平臺應驗證傳入的憑證鏈時 ```false```，```PerformSystemValidation``` 方法應該會傳回 ```true```，否則會傳回。</span><span class="sxs-lookup"><span data-stu-id="58776-125">The ```PerformSystemValidation``` method should return ```true``` when the underlying platform should validate the incoming certificate chain, ```false``` otherwise.</span></span>
    * <span data-ttu-id="58776-126">```ValidateCertificate``` 由用戶端內容呼叫以要求驗證憑證。</span><span class="sxs-lookup"><span data-stu-id="58776-126">```ValidateCertificate``` is called by the client context to request validation of a certificate.</span></span> <span data-ttu-id="58776-127">這個方法會接受憑證鏈（使用第一個憑證作為主旨憑證）、與建立連線的伺服器名稱，以及是否應該強制執行撤銷檢查。</span><span class="sxs-lookup"><span data-stu-id="58776-127">This method accepts the certificate chain (with the first certificate being the subject certificate), the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="58776-128">如果已要求基礎系統的驗證，則會提供系統驗證結果。</span><span class="sxs-lookup"><span data-stu-id="58776-128">The system validation result will be provided if validation by the underlying system has been requested.</span></span> <span data-ttu-id="58776-129">若要繼續以適當的結果處理 ```CertificateValidated```，或 ```Cancel``` 取消驗證，必須在傳遞的 ```ICertificateValidationCallback```上呼叫。</span><span class="sxs-lookup"><span data-stu-id="58776-129">To continue processing either ```CertificateValidated``` with the appropriate result or ```Cancel``` to cancel validation needs to be called on the passed ```ICertificateValidationCallback```.</span></span>

<span data-ttu-id="58776-130">此外，若要允許交換安全權杖，則必須實作為下列物件。</span><span class="sxs-lookup"><span data-stu-id="58776-130">Furthermore, to allow for the exchange of a secure token the following objects need to be implemented.</span></span>

1) <span data-ttu-id="58776-131">執行 ```IAuthenticationProvider``` 介面的驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="58776-131">An authentication provider implementing the ```IAuthenticationProvider``` interface.</span></span> <span data-ttu-id="58776-132">用戶端內容會呼叫其 ```GetToken``` 方法來要求權杖以進行用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="58776-132">Its ```GetToken``` method is called by the client context to request a token for client authentication.</span></span> <span data-ttu-id="58776-133">若要繼續 ```TokenReceived``` 以提供驗證權杖，並繼續進行連線程式，或 ```Cancel``` 取消處理常式必須在傳遞的 ```IAuthenticationProviderCallback```上呼叫。</span><span class="sxs-lookup"><span data-stu-id="58776-133">To continue either ```TokenReceived``` to provide the authentication token and continue the connection process or ```Cancel``` to cancel the process needs to be called on the passed ```IAuthenticationProviderCallback```.</span></span>
2) <span data-ttu-id="58776-134">執行 ```IAuthenticationReceiver``` 介面的驗證接收器。</span><span class="sxs-lookup"><span data-stu-id="58776-134">An authentication receiver implementing the ```IAuthenticationReceiver``` interface.</span></span> <span data-ttu-id="58776-135">其工作是用來驗證傳入的權杖。</span><span class="sxs-lookup"><span data-stu-id="58776-135">Its task is to validate incoming tokens.</span></span>
    * <span data-ttu-id="58776-136">```GetRealm``` 方法應該會傳回驗證領域的名稱。</span><span class="sxs-lookup"><span data-stu-id="58776-136">The ```GetRealm``` method should return the name of the authentication realm.</span></span>
    * <span data-ttu-id="58776-137">伺服器網路內容會呼叫 ```ValidateToken``` 方法，以要求驗證用戶端驗證權杖。</span><span class="sxs-lookup"><span data-stu-id="58776-137">The ```ValidateToken``` method is called by the server network context to request validation of a client authentication token.</span></span> <span data-ttu-id="58776-138">若要繼續，請呼叫 ```ValidationCompleted``` 以指示完成驗證，或 ```Cancel``` 拒絕用戶端連接。</span><span class="sxs-lookup"><span data-stu-id="58776-138">To continue either call ```ValidationCompleted``` to signal completion of the validation or ```Cancel``` to reject the client connection..</span></span> <span data-ttu-id="58776-139">用戶端連接將會根據傳遞給 ```ValidationCompleted```的驗證結果來獲准或拒絕。</span><span class="sxs-lookup"><span data-stu-id="58776-139">The client connection will be admitted or rejected based on the validation result passed to ```ValidationCompleted```.</span></span> 

<span data-ttu-id="58776-140">一旦執行這些物件 ```ListenSecure``` 必須呼叫，而不是 ```Listen``` 和 ```ConnectSecure```，而不是分別在遠端內容和播放者內容上 ```Connect```。</span><span class="sxs-lookup"><span data-stu-id="58776-140">Once these objects are implemented ```ListenSecure``` needs to be called instead of ```Listen``` and ```ConnectSecure``` instead of ```Connect``` on the remote context and player context respectively.</span></span> <span data-ttu-id="58776-141">```ListenSecure``` 需要額外的憑證提供者和驗證接收器，而不是 ```Listen```。</span><span class="sxs-lookup"><span data-stu-id="58776-141">```ListenSecure``` requires an additional certificate provider and authentication receiver over ```Listen```.</span></span> <span data-ttu-id="58776-142">```ConnectSecure``` 需要額外的驗證提供者，以及透過 ```Connect```的憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="58776-142">```ConnectSecure``` requires an additional authentication provider and certificate validator over ```Connect```.</span></span>

## <a name="see-also"></a><span data-ttu-id="58776-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58776-143">See Also</span></span>
* [<span data-ttu-id="58776-144">撰寫全像攝影遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="58776-144">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="58776-145">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="58776-145">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="58776-146">全像攝影遠端疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="58776-146">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="58776-147">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="58776-147">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="58776-148">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="58776-148">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
