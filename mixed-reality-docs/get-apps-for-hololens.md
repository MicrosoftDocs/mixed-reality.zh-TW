---
title: 取得 HoloLens 的應用程式
description: 說明如何透過 Microsoft Store 和側載安裝 HoloLens 的應用程式。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 側載, 側邊載入, 側載入, 存放區, uwp, 應用程式, 安裝
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522553"
---
# <a name="get-apps-for-hololens"></a>取得 HoloLens 的應用程式

作為 Windows 10 裝置, HoloLens 支援來自 app store 的許多現有 UWP 應用程式, 以及專為 HoloLens 建立的新應用程式。 除此之外, 您甚至可能想要[開發](development-overview.md)和安裝自己的應用程式或朋友

## <a name="installing-apps"></a>安裝應用程式

有三種方式可在您的 HoloLens 上安裝新的應用程式。 主要方法是從 Windows Store 安裝新的應用程式。 不過, 您也可以使用裝置入口網站或從 Visual Studio 部署來安裝自己的應用程式。

### <a name="from-the-microsoft-store"></a>從 Microsoft Store
1. 執行[bloom](gestures.md#bloom)手勢以開啟 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。
2. 選取 [Store] 應用程式, 然後按一下 [將此磚放入您的世界]。
3. 儲存區應用程式開啟後, 使用搜尋列尋找任何想要的應用程式。
4. 在應用程式頁面上選取 [**取得**] 或 [**安裝**] (可能需要購買)。

### <a name="installing-an-application-package-with-the-device-portal"></a>使用裝置入口網站安裝應用程式套件
1. 建立從[裝置入口網站](using-the-windows-device-portal.md)到目標 HoloLens 的連線。
2. 流覽至左側導覽中的 [**應用程式**] 頁面。
3. 在 [**應用程式套件**] 底下, 流覽至與您的應用程式相關聯的 .appx 檔案。
  >[!IMPORTANT]
  >請務必參考任何相關聯的相依性和憑證檔案。

4. 按一下 [**移至**]。

![在 Microsoft HoloLens 上的 Windows 裝置入口網站中安裝應用程式表單](images/deviceportal-appmanager.jpg)<br>
使用 Windows 裝置入口網站在 HoloLens 上安裝應用程式

### <a name="deploying-from-microsoft-visual-studio-2015"></a>從 Microsoft Visual Studio 2015 部署
1. 開啟應用程式的 Visual Studio 方案 (.sln 檔案)。
2. 開啟專案的 [**屬性**]。
3. 選取下列組建設定:主要/x86/遠端電腦。
4. 當您選取 [遠端電腦] 時:
   * 請確定該位址指向 HoloLens 的 WiFi IP 位址。
   * 將驗證設定為通用 (未加密的通訊協定)。
5. 建立您的解決方案。
6. 按一下 [**遠端電腦**] 按鈕, 將應用程式從開發電腦部署到 HoloLens。 如果您已在 HoloLens 上擁有現有的組建, 請選取 [是] 以重新安裝這個較新的版本。<br>
  ![在 Visual Studio 中將應用程式的遠端機器部署至 Microsoft HoloLens](images/vs2015-remotedeployment.jpg)<br>
7. 應用程式將會在您的 HoloLens 上安裝並自動啟動。
