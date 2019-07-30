---
title: 混合實境擷取
description: 使用混合現實 capture 的資訊。
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: mrc, 混合現實 capture, 相片, 影片, 攝影機, capture, 使用, 串流, livestream, 示範
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694503"
---
# <a name="mixed-reality-capture"></a>混合實境擷取

HoloLens 為使用者提供了將真實世界與數位世界混合的經驗。 混合現實 capture (MRC) 可讓您以相片或影片的形式來捕捉該體驗。 這可讓您與其他人分享經驗, 方法是允許他們看到您看到的全息影像。 這類影片和相片是從第一人的觀點來看。 如需第三人的觀點, 請使用[spectator view](spectator-view.md)。

混合現實的使用案例不會在社交圈間分享影片。 您可以使用影片來指示其他人如何使用應用程式。 開發人員可以使用影片或靜止圖像來改善重現步驟和 debug 應用程式體驗。

## <a name="live-streaming-from-hololens"></a>HoloLens 的即時串流

[Windows 10 2018 年10月更新](release-notes-october-2018.md)將 Miracast 支援新增至 HoloLens。 選取 [開始] 功能表底部的 [連線 **]** 按鈕, 以顯示支援 Miracast 的裝置和介面卡的選擇器。 選取您要開始串流處理的裝置。 完成時, 請選取 [開始] 功能表底部的 [**中斷連線]** 按鈕。  [快速動作] 功能表也提供 [連線] 和 **[中斷連線]** 。

[Windows 裝置入口網站](using-the-windows-device-portal.md)和[Microsoft HoloLens 隨附應用程式](https://www.microsoft.com/store/productId/9NBLGGH4QWNX)會針對處於開發人員模式的裝置公開即時串流選項。

[Dynamics 365 遠端協助](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist)支援從 HoloLens 即時串流至遠端位置中的員工。

## <a name="taking-mixed-reality-captures"></a>接受混合的事實捕獲

![按一下 [開始] 功能表底部的相機圖示](images/cameraiconinpins-300px.png)<br>
*按一下 [開始] 功能表底部的相機圖示*

有多種方式可以起始混合現實 capture:
* 無論目前正在執行哪一個應用程式, 都可以隨時使用 Cortana。 比方說, 「嗨, Cortana, 拍一張圖片」或「嘿 Cortana, 開始錄製。」 若要停止影片, 請說: 「嘿 Cortana, 停止錄製」。
* 在 [開始] 功能表上, 選取 [**相機**] 或 [**影片**]。 使用 [點一下] 開啟內建的[[](gestures.md#air-tap) MRC 相機] UI。
* 在 [快速動作] 功能表上, 選取 [**相機**] 或 [**影片**] 以開啟內建的 MRC 攝影機 UI。
* 應用程式可以使用自訂或, 從[Windows 10 2018 年10月更新](release-notes-october-2018.md)的[內建 MRC 攝影機 ui](mixed-reality-capture-for-developers.md), 公開自己的混合現實 capture 的 UI。
* HoloLens 獨有: 
    * [Windows 裝置入口網站](using-the-windows-device-portal.md)有一個混合現實的 [capture] 頁面, 可用來拍攝相片、影片、即時串流和觀看捕捉。
    * 不論目前正在執行哪一個應用程式, 都可以同時按 [**音量**] 和 [**音量**] 按鈕來進行圖片。
    * 按住 [**音量**] 和 [**音量降低**] 按鈕三秒, 開始錄製影片。 若要停止影片, 請同時按一下 [**音量**] 和 [**音量向下**] 按鈕。
* 沉浸式耳機的獨特之處: 
    * 使用「動作控制器」, 按住 [ **Windows** ] 按鈕, 然後再按下**觸發**程式來拍照。 
    * 使用 [移動控制器], 按住 [ **Windows** ] 按鈕, 然後按下**功能表**按鈕以開始錄製影片。 按住 [ **Windows** ] 按鈕, 然後按一下**觸發**程式以停止錄製影片。
    
>[!NOTE]
>[Windows 10 2018 年10月更新](release-notes-october-2018.md)會變更 [bloom] 和 [Windows] 按鈕的行為。 在更新之前, [bloom 手勢] 或 [Windows] 按鈕會停止錄製。 更新之後, [bloom 手勢] 或 [Windows] 按鈕會開啟 [開始] 功能表 (如果您是在應用程式中, 則是 [快速動作] 功能表)。 在功能表中, 選取 [**停止影片**] 以停止錄製。

### <a name="limitations-of-mixed-reality-capture"></a>混合現實 capture 的限制

在 HoloLens 上, 系統會將轉譯速率調節為30Hz。 這會建立一些可供 MRC 執行的空間, 因此應用程式不需要保留固定的預算, 而且也會符合 (最多) 30fps 的 MRC 影片記錄的畫面播放速率。

影片的最大長度為5分鐘。

內建的「MRC 攝影機」 UI 一次只支援單一的 MRC 作業 (拍攝圖片與錄製影片互斥)。

### <a name="file-formats"></a>檔案格式

來自 Cortana 語音命令和 [開始] 功能表工具的混合現實捕獲會以下列格式建立檔案:

|  Type  |  格式  |  延伸  |  解析度  |  音訊 | 
|----------|----------|----------|----------|----------|
|  Photo  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920x1080px<br> (沉浸式耳機) |  N/A | 
|  視訊  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920x1080px<br> at 30fps (HoloLens 2)<br> 1216x684px at 24fps (HoloLens)<br> 1632x918px at 30fps (沉浸式耳機) |  48kHz 身歷聲 | 

>[!NOTE]
>如果相片/攝影機已由另一個應用程式、即時串流或系統資源不足, 則相片和影片的解析度可能會較小。

### <a name="video-stabilization"></a>影片穩定

預設:
* 透過 Miracast 進行即時串流時, 會套用零延遲的影片穩定。
* 長時間延遲的影片穩定適用于使用內建的 MRC 相機 UI、Cortana 語音命令和 Windows 裝置入口網站所捕捉到的影片。

## <a name="viewing-mixed-reality-captures"></a>觀賞混合的現實捕獲

Mixed reality capture 相片和影片會儲存到裝置的「相機變換」資料夾中。 您可以透過[相片應用程式](see-your-photos.md#photos-app)或檔案瀏覽器來存取這些檔案。

在連接到 HoloLens 的電腦上, 您也可以使用[Windows 裝置入口網站](using-the-windows-device-portal.md#mixed-reality-capture)或電腦的檔案瀏覽器 (透過[MTP](release-notes-april-2018.md#new-features-for-hololens))。

如果您安裝[onedrive 應用程式](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), 您可以開啟**相機上傳,** 而您的 MRC 相片和影片將會與 onedrive 和使用 onedrive 的其他裝置同步。

>[!NOTE]
>從 Windows 10 2018 年4月更新起, 相片應用程式將不再將您的相片和影片上傳到 OneDrive。

## <a name="see-also"></a>另請參閱
* [觀眾檢視](spectator-view.md)
* [定位相機](locatable-camera.md)
* [適用於開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)
* [查看您的相片](see-your-photos.md)
* [使用 Windows 裝置入口網站](using-the-windows-device-portal.md)
