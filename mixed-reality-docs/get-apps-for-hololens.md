---
title: 取得 HoloLens 的應用程式
description: 描述 HoloLens，同時透過 Microsoft Store 和側載安裝應用程式。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 側載、 側載、 側載、 市集、 uwp、 應用程式，安裝
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591129"
---
# <a name="get-apps-for-hololens"></a>取得 HoloLens 的應用程式

為 Windows 10 裝置、 HoloLens 支援許多現有的 UWP 應用程式，從應用程式市集，以及專為 HoloLens 建置新的應用程式。 上，您可能甚至想要[開發](development-overview.md)並安裝您自己的應用程式，或您的朋友 ！

## <a name="installing-apps"></a>安裝應用程式

有三種方式可在您的 HoloLens 上安裝新的應用程式。 主要方法是從 Windows 市集安裝新的應用程式。 不過，您也可以安裝自己的應用程式使用裝置入口網站或從 Visual Studio 部署。

### <a name="from-the-microsoft-store"></a>從 Microsoft Store
1. 執行[bloom](gestures.md#bloom)以開啟軌跡[開始 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。
2. 選取市集應用程式，然後點選 將此圖格放入您的世界。
3. 市集應用程式開啟後，請使用 [搜尋] 列，尋找任何所需的應用程式。
4. 選取 **取得**或是**安裝**（購買可能會需要） 的應用程式的頁面上。

### <a name="installing-an-application-package-with-the-device-portal"></a>使用裝置入口網站安裝應用程式封裝
1. 從建立連線[裝置入口網站](using-the-windows-device-portal.md)目標 HoloLens。
2. 瀏覽至**應用程式**在左側導覽中的頁面。
3. 底下**應用程式套件**瀏覽至您的應用程式相關聯的.appx 檔案。
  >[!IMPORTANT]
  >請務必參考任何相關聯的相依性和憑證檔案。

4. 按一下 **移**。

![在 Microsoft HoloLens 上的 Windows Device Portal 中安裝的應用程式表單](images/deviceportal-appmanager.jpg)<br>
使用 Windows Device Portal HoloLens 上安裝應用程式

### <a name="deploying-from-microsoft-visual-studio-2015"></a>從 Microsoft Visual Studio 2015 部署
1. 開啟您的應用程式的 Visual Studio 方案 （.sln） 檔。
2. 開啟專案的**屬性**。
3. 選取下列的組建組態：主版/x86/遠端機器。
4. 當您選取遠端電腦：
   * 請務必地址點 HoloLens 的 WiFi IP 位址。
   * 將驗證設定為通用 （未加密的通訊協定）。
5. 建置您的解決方案。
6. 按一下 **遠端機器**按鈕，將部署應用程式從開發電腦，以您 HoloLens。 如果您已經有現有的組建 HoloLens 上，選取 [是] 以重新安裝這個較新版本。<br>
  ![在 Visual Studio 中的 Microsoft HoloLens 的應用程式的遠端機器部署](images/vs2015-remotedeployment.jpg)<br>
7. 應用程式會安裝，並自動在您的 HoloLens 上啟動。
