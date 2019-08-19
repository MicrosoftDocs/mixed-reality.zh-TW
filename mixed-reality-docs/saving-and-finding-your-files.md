---
title: 儲存和尋找檔案
description: 如何在 HoloLens 上尋找、儲存及共用檔案。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 操作說明, 檔案選擇器, 檔案, 相片, 影片, 圖片, OneDrive, 儲存, 檔案瀏覽器
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524608"
---
# <a name="saving-and-finding-your-files"></a>儲存和尋找檔案

檔案可以與其他 Windows 10 桌上型電腦和行動裝置以類似的方式儲存和管理:
* 使用 File Explorer 應用程式存取本機資料夾
* 在應用程式本身的儲存體中
* 在特殊的已知資料夾中 (例如影片或音樂媒體櫃)
* 使用包含應用程式和檔案選擇器的儲存體服務 (例如 OneDrive)
* 使用透過 USB 連線至 HoloLens 的桌上型電腦, via MTP (媒體傳輸通訊協定) 支援

## <a name="file-explorer"></a>檔案總管

您可以使用檔案瀏覽器應用程式, 在 HoloLens 中移動和刪除檔案。

>[!NOTE]
>如果您在 [檔案瀏覽器] 中看不到任何檔案, [最近] 篩選可能會處於作用中狀態 (左窗格中的時鐘圖示會反白顯示)。 若要修正此問題, 請選取左窗格中的 [**此裝置**檔] 圖示 (在 [時鐘] 圖示下方), 或開啟功能表並選取 [**此裝置**]。

## <a name="files-within-an-app"></a>應用程式內的檔案

如果應用程式將檔案儲存在您的裝置上, 您可以使用該應用程式來存取它們。

### <a name="where-are-my-photosvideos"></a>我的相片/影片在哪裡？

[混合現實拍攝](mixed-reality-capture.md)相片和影片會儲存到裝置的相機變換資料夾。 這些可以透過[相片應用程式](see-your-photos.md#photos-app)來存取。 您可以使用相片應用程式將您的相片和影片同步到 OneDrive。 您也可以透過[Windows 裝置入口網站](using-the-windows-device-portal.md#mixed-reality-capture)的 [混合現實捕捉] 頁面來存取您的相片和影片。

### <a name="requesting-files-from-another-app"></a>向另一個應用程式要求檔案

應用程式可以要求儲存檔案, 或透過[檔案選擇器](app-model.md#file-pickers)從另一個應用程式開啟檔案。

## <a name="known-folders"></a>已知的資料夾

HoloLens 支援一些應用程式可以要求許可權來存取的[已知資料夾](app-model.md#known-folders)。

## <a name="files-in-a-service"></a>服務中的檔案

若要將檔案儲存至服務 (或從其中存取檔案), 則必須安裝與服務相關聯的應用程式。 若要將檔案儲存到 OneDrive 並從中存取檔案, 您必須安裝[onedrive 應用程式](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)。

## <a name="mtp-media-transfer-protocol"></a>MTP (媒體傳輸通訊協定)

類似于其他行動裝置, 請將 HoloLens 連線到桌上型電腦, 並在電腦上開啟檔案瀏覽器, 以存取您的 HoloLens 程式庫 (相片、影片、檔) 以方便傳輸。

## <a name="clarifications"></a>澄清

* HoloLens 不支援連接到外部硬碟或 SD 卡。
* 從適用于[hololens 的 Windows 10 2018 年4月更新 (RS4)](release-notes-april-2018.md)起, hololens 包含用於儲存和管理裝置上檔案的檔案瀏覽器。 新增檔案瀏覽器也可讓您選擇檔案選擇器 (例如, 將檔案儲存到您的裝置或 OneDrive)。
