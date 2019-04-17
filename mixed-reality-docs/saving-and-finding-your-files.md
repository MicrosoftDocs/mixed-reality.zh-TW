---
title: 儲存並尋找您的檔案
description: 如何尋找、 儲存及共用 HoloLens 上的檔案。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 操作說明、 檔案選擇器、 檔案、 相片、 視訊、 圖片、 OneDrive、 儲存體、 檔案總管
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595665"
---
# <a name="saving-and-finding-your-files"></a>儲存並尋找您的檔案

檔案可以儲存和管理類似的方式，其他的 Windows 10 Desktop 和行動裝置：
* 使用檔案總管 應用程式存取本機資料夾
* 應用程式本身的儲存體
* 在特殊的已知資料夾 （例如視訊或音樂媒體櫃）
* 使用儲存體服務，其中包含應用程式和檔案選擇器 （例如 OneDrive)
* 透過 MTP （媒體傳輸通訊協定） 支援使用桌上型個人電腦連接到您透過 USB、 HoloLens

## <a name="file-explorer"></a>檔案總管

您可以使用檔案總管 應用程式來移動和刪除 HoloLens 中的檔案。

>[!NOTE]
>如果看不到任何檔案在檔案總管中的，「 最近 」 篩選條件可能是作用中 （左窗格中，反白顯示時鐘圖示）。 若要修正此問題，請選取**此裝置**文件圖示，左窗格中 （下方的時鐘圖示），或開啟功能表，然後選取**此裝置**。

## <a name="files-within-an-app"></a>應用程式中的檔案

如果應用程式儲存在您的裝置上的檔案，您可以使用該應用程式可以存取它們。

### <a name="where-are-my-photosvideos"></a>我的相片/影片哪裡？

[混合實境擷取](mixed-reality-capture.md)相片和視訊會儲存至裝置的相機相簿的資料夾。 這些可以透過存取[照片 app](see-your-photos.md#photos-app)。 您可以使用相片應用程式進行同步處理您的相片和影片到 OneDrive。 您也可以存取您的相片和影片透過混合實境擷取的畫面[Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)。

### <a name="requesting-files-from-another-app"></a>從另一個應用程式要求檔案

應用程式可以要求儲存檔案，或從另一個應用程式，透過開啟檔案[檔案選擇器](app-model.md#file-pickers)。

## <a name="known-folders"></a>已知的資料夾

HoloLens 支援多種[已知資料夾](app-model.md#known-folders)應用程式可以要求存取權限。

## <a name="files-in-a-service"></a>在服務中的檔案

若要儲存至檔案 （或存取檔案） 服務，還必須安裝與服務相關聯的應用程式。 若要將檔案儲存及存取檔案從 OneDrive，您必須安裝[OneDrive 應用程式](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)。

## <a name="mtp-media-transfer-protocol"></a>MTP （媒體傳輸通訊協定）

類似於其他行動裝置、 HoloLens 連接到您的桌面電腦，並且輕鬆傳輸開啟檔案總管 來存取您 HoloLens 的程式庫 （相片、 影片、 文件） 電腦上。

## <a name="clarifications"></a>釐清的內容

* HoloLens 不支援連接到外接式硬碟或 sd 記憶卡。
* 至於[Windows 10 April 2018 HoloLens 的更新 (RS4)](release-notes-april-2018.md)，HoloLens 包括檔案總管 中儲存和管理檔案的裝置。 加入的檔案總管 也可讓您能夠選擇您的檔案選擇器 （例如，儲存到您的裝置，或到 OneDrive 的檔案）。
