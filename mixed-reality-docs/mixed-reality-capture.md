---
title: 混合實境擷取
description: 使用混合的實境擷取資訊。
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: mrc，混合實境擷取、 相片、 視訊、 相機、 擷取、 使用量、 資料流、 即時串流、 示範
ms.openlocfilehash: 18a80083bd25974905874c6c2ec0de87dc7424ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596710"
---
# <a name="mixed-reality-capture"></a>混合實境擷取

HoloLens 讓使用者混合現實與數位世界的體驗。 混合的實境擷取 (MRC) 可讓您擷取相片或視訊的經驗。 這可讓您與其他人分享的體驗，讓它們能夠看到全像投影，因為您會看到它們。 這類的影片和相片會從第一個人的觀點。 針對第三位使用者的觀點而言，使用[spectator 檢視](spectator-view.md)。

分享影片之間社交圈超越混合的實境擷取的使用案例。 影片可用來指示其他人如何使用應用程式。 開發人員可以使用視訊或仍然可改善重新產生步驟及偵錯的應用程式體驗。

## <a name="live-streaming-from-hololens"></a>即時串流從 HoloLens

[Windows 10 年 10 月 2018 Update](release-notes-october-2018.md) Miracast 支援加入 HoloLens。 選取  **Connect**底部的 開始 功能表啟動 已啟用 Miracast 的裝置和配接器的選擇器 按鈕。 選取您要開始串流處理的裝置。 完成時，選取**中斷連線**底部的 [開始] 功能表的按鈕。  **連接**並**中斷連線**也會提供在 [快速動作] 功能表上。 

[Windows Device Portal](using-the-windows-device-portal.md)公開即時串流處理的選項，在開發人員模式的裝置。

## <a name="taking-mixed-reality-captures"></a>採用混合的實境擷取

![按一下底部的 [開始] 功能表的 [相機] 圖示](images/cameraiconinpins-300px.png)<br>
*按一下底部的 [開始] 功能表的 [相機] 圖示*

有多種方式來起始混合的實境擷取：
* Cortana 可以用在所有時間不論目前正在執行的應用程式。 只是說: 「 嘿 Cortana，拍照 」 或 「 嘿 Cortana，開始錄製。 」 若要停止的影片，請說 「 嘿 Cortana 停止錄製。 」
* 在 [開始] 功能表上選取**相機**或是**視訊**。 使用[空中點選](gestures.md#air-tap)開啟內建的 MRC 相機 UI。
* 在 [快速動作] 功能表上選取**相機**或**視訊**開啟內建的 MRC 相機 UI。
* 應用程式都能夠公開其自己的 UI，使用自訂的混合的實境擷取，或從[Windows 10 年 10 月 2018 Update](release-notes-october-2018.md)，[內建 MRC 相機 UI](mixed-reality-capture-for-developers.md)。
* 唯一 HoloLens: 
    * [Windows Device Portal](using-the-windows-device-portal.md)混合的實境擷取頁面，可用來取得相片、 影片、 即時資料流，並檢視擷取。
    * 按兩**音量提高**並**音量降低**按鈕，同時以拍照，不論目前正在執行的應用程式。
    * 保存**音量提高**並**音量降低**三秒，若要開始錄製視訊的按鈕。 若要停止的影片，請點選兩者**音量提高**並**音量降低**同時按鈕。
* 唯一沈浸式耳機： 
    * 使用動作控制站，保存**Windows**按鈕，然後點選**觸發程序**來拍照。 
    * 使用動作控制站，保存**Windows**按鈕，然後點選**功能表**按鈕以啟動錄製影片。 保存**Windows**按鈕，然後點選**觸發程序**若要停止錄製影片。
    
>[!NOTE]
>[Windows 10 年 10 月 2018 Update](release-notes-october-2018.md) bloom 和 [Windows] 按鈕的行為方式會變更。 更新前, bloom 筆勢或 Windows 按鈕便會停止記錄。 更新之後，bloom 筆勢 或 Windows 按鈕會開啟 開始 功能表 （或如果您是在應用程式中的 快速動作 功能表）。 在功能表中，選取**停止視訊**停止錄製。

### <a name="limitations-of-mixed-reality-capture"></a>混合的實境擷取的限制

HoloLens，在系統將會節流 30 赫茲轉譯速率。 這會建立執行應用程式不需要保留固定的預算保留，因此 MRC 一些成長空間，並也會比對的 30fps MRC 影片記錄畫面播放速率。

影片會有最大長度為五分鐘的時間。

內建的 MRC 相機 UI 只支援單一 MRC 作業一次 （拍攝照片是互斥的錄製的視訊）。

### <a name="file-formats"></a>檔案格式

混合的實境會擷取從 Cortana 語音命令，並開始 功能表工具建立的檔案格式如下：

|  類型  |  格式  |  延伸  |  解析度  |  音訊 | 
|----------|----------|----------|----------|----------|
|  Photo  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  1408x792px (HoloLens) 1920x1080px<br> （沈浸式耳機） |  N/A | 
|  視訊  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1408x792px (HoloLens) 1632x918px （沈浸式耳機） |  48 kHz 立體聲 | 

## <a name="viewing-mixed-reality-captures"></a>檢視混合的實境擷取

混合的實境擷取相片和視訊會儲存到裝置的 「 手機相簿"資料夾中。 這些可以透過存取[照片 app](see-your-photos.md#photos-app)或檔案總管。

在 PC 上連線到 HoloLens，您也可以使用[Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)或 [檔案總管] 中您的電腦 ([透過 MTP](release-notes-april-2018.md#new-features-for-hololens))。

如果您安裝[OneDrive 應用程式](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3)，您可以開啟**相機上傳，** 和 MRC 相片和視訊會同步至 OneDrive 和其他裝置使用 OneDrive。

>[!NOTE]
>從 Windows 10 April 2018 Update，相片應用程式將不會再上傳相片和視訊到 OneDrive。

## <a name="see-also"></a>另請參閱
* [Spectator 檢視](spectator-view.md)
* [之外的可尋獲相機](locatable-camera.md)
* [混合實境擷取適用於開發人員](mixed-reality-capture-for-developers.md)
* [請參閱您的相片](see-your-photos.md)
* [使用 Windows Device Portal](using-the-windows-device-portal.md)
