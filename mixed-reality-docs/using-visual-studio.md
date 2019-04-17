---
title: 使用 Visual Studio 來部署和偵錯
description: 如何建置、 偵錯及部署 HoloLens 和使用 Visual Studio 的 Windows Mixed Reality 應用程式。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio、 HoloLens、 混合實境，偵錯、 部署
ms.openlocfilehash: 6bd47d7212d321791a11ff4db91c3e172c91f463
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594874"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>使用 Visual Studio 來部署和偵錯

您是否要使用 DirectX 或 Unity 開發您的混合的實境應用程式，您將使用 Visual Studio 偵錯和部署。 在本節中，您將學習：
* 如何部署應用程式到您 HoloLens 或 Windows Mixed Reality 沈浸式耳機，透過 Visual Studio。
* 如何使用 Visual Studio 內建的 HoloLens 模擬器。
* 如何偵錯混合的實境應用程式。

## <a name="prerequisites"></a>先決條件
1. 請參閱[安裝工具](install-the-tools.md)如需安裝指示。
2. 在 Visual Studio 2015 Update 1 或 Visual Studio 2017 中建立新的通用 Windows 應用程式專案。 C#C++，和 JavaScript 專案都有支援。 (或遵循指示來[Unity 中建立應用程式建置](holograms-100.md)。)

## <a name="enabling-developer-mode"></a>啟用開發人員模式

藉由啟用開始**開發人員模式**讓 Visual Studio 可以連線到它在裝置上。

### <a name="hololens"></a>HoloLens
1. 開啟您的 HoloLens，並放在裝置上。
2. 做出[盛開](gestures.md#bloom)手勢來啟動主功能表。
3. 注視**設定**圖格，並執行[空中點選](gestures.md#air-tap)筆勢。 做出第二次的空中點選，來將 App 放置於您的環境中。 當您放置 [設定] App 之後，該 App 便會啟動。
4. 選取 [更新] 功能表項目。
5. 選取 [適用於開發人員] 功能表項目。
6. 啟用 [開發人員模式]。 這可讓您[從 Visual Studio 部署應用程式](using-visual-studio.md)到您的 HoloLens。
7. 選擇性：向下捲動，也可讓**裝置入口網站**。 這也可讓您連接到[Windows Device Portal](using-the-windows-device-portal.md)上您從網頁瀏覽器的 HoloLens。

### <a name="windows-pc"></a>Windows 電腦

如果您正在使用 Windows Mixed Reality 耳機，連線到您的電腦，您必須啟用**開發人員模式**在電腦上。
1. 移至**設定**
2. 選取**更新與安全性**
3. 選取**適用於開發人員**
4. 啟用**開發人員模式**，設定您選擇，請閱讀免責聲明，然後按一下 [是] 以接受變更。

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>部署 wi-fi-HoloLens 的應用程式 （第 1 代）
1. 選取  **x86**建置應用程式的組態![x86 建置在 Visual Studio 中的組態](images/x86setting.png)
2. 選取 **遠端電腦**部署目標下拉式選單中![Visual Studio 中的遠端電腦部署目標](images/remotemachinesetting.png)
3. 針對C++和 JavaScript 專案，請前往**專案 > 屬性 > 組態屬性 > 偵錯**。 針對C#專案，對話方塊會自動快顯，若要設定您的連線。
  a. 輸入您的裝置中的 IP 位址**地址**或是**電腦名稱**欄位。 在您 HoloLens 上找到的 IP 位址**設定 > 網路和網際網路 > 進階選項**，或者您可以要求 Cortana 「 我的 IP 位址為何？ 」
  b. 若要設定驗證模式**通用 （未加密的通訊協定）**![Visual Studio 中的 [遠端連線] 對話方塊](images/remotedeploy.png)
4. 選取 **偵錯 > 啟動偵錯**來部署您的應用程式，並開始偵錯![啟動但不偵錯在 Visual Studio 中](images/deploynodebugging.png)
5. 第一次您將應用程式部署到您 HoloLens 上從您的電腦，您將會提示輸入 PIN。 請遵循**配對您的裝置**下列指示。

HoloLens IP 位址變更，您還可以變更目標電腦的 IP 位址，方法是前往**專案 > 屬性 > 組態屬性 > 偵錯**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>透過 USB-HoloLens 部署應用程式 （第 1 代）
1. 選取  **x86**建置應用程式的組態![x86 建置在 Visual Studio 中的組態](images/x86setting.png)
2. 選取 **裝置**部署目標下拉式選單中![Visual Studio 中的裝置部署](images/buildsettingsusbdeploy.png)
3. 選取 **偵錯 > 啟動偵錯**來部署您的應用程式，並開始偵錯![啟動但不偵錯在 Visual Studio 中](images/deploynodebugging.png)
4. 第一次您將應用程式部署到您 HoloLens 上從您的電腦，您將會提示輸入 PIN。 請遵循**配對您的裝置**下列指示。

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>將應用程式部署到本機電腦-沈浸式耳機

使用 Windows Mixed Reality 沈浸式耳機，連接到您的電腦時，請遵循下列指示或[混合實境模擬器](using-the-windows-mixed-reality-simulator.md)。 在這些情況下，只要部署，並在本機電腦上執行您的應用程式。
1. 選取  **x86**或是**x64**建置您的應用程式的組態
2. 選取 **本機電腦**部署目標下拉式選單中
3. 選取 **偵錯 > 啟動偵錯**來部署您的應用程式，並開始偵錯

## <a name="pairing-your-device---hololens-1st-gen"></a>配對您的裝置-HoloLens （第 1 代）

首次部署應用程式從 Visual Studio 以您的 HoloLens，您會提示輸入 PIN。 HoloLens，在產生的 pin 碼來啟動設定 應用程式，請前往**更新 > 適用於開發人員**並點選**配對**。 Pin 碼將會顯示在您的 HoloLens;在 Visual Studio 中，輸入此 pin 碼。 完成配對之後，請點選**完成**以關閉對話方塊，您 HoloLens 上。 這部電腦現在搭配 HoloLens，您將能夠自動部署應用程式。 針對用來將應用程式部署到您的 HoloLens 的每個後續電腦中重複這些步驟。

若要取消對您所有的電腦，它搭配，HoloLens 啟動**設定**應用程式，移至**更新 > 適用於開發人員**並點選**清除**。

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>將應用程式部署到 HoloLens （第 1 代） 模擬器
1. 請確定您已**[安裝 HoloLens 模擬器](install-the-tools.md)**。
2. 選取  **x86**建置您的應用程式的組態。
![x86 建置在 Visual Studio 中的組態](images/x86setting.png)
3. 選取  **HoloLens 模擬器**部署目標下拉式選單中![Visual Studio 中的模擬器目標](images/deployemulator.png)
4. 選取 **偵錯 > 啟動偵錯**來部署您的應用程式，並開始偵錯![啟動但不偵錯在 Visual Studio 中](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>圖形偵錯工具

Visual Studio 圖形診斷工具會撰寫並最佳化全像攝影版的應用程式時非常有用。 請參閱[MSDN 上的 Visual Studio 圖形診斷](https://msdn.microsoft.com/library/hh315751.aspx)的完整詳細資料。

**若要開始圖形偵錯工具**
1. 請遵循上述指示，以在裝置或模擬器為目標
2. 移至**偵錯 > 圖形 > 啟動診斷**
3. 第一次您執行這項操作與 HoloLens，您可能會收到 「 拒絕存取 」 錯誤。 重新啟動您的 HoloLens 讓更新生效，並再試一次的權限。

## <a name="profiling"></a>程式碼剖析

Visual Studio 程式碼剖析工具可讓您分析您的應用程式效能與資源使用。 這包括最佳化 CPU、 記憶體、 圖形，以及網路使用的工具。 請參閱[執行診斷工具但不偵錯 MSDN 上](https://msdn.microsoft.com/library/dn957936.aspx)的完整詳細資料。

**若要開始 HoloLens 的程式碼剖析工具**
1. 請遵循上述指示，以在裝置或模擬器為目標
2. 移至**偵錯 > 啟動診斷工具但不偵錯...**
3. 選取您想要使用的工具
4. 按一下 **開始**
5. 第一次您執行這項操作與 HoloLens，您可能會收到 「 拒絕存取 」 錯誤。 重新啟動您的 HoloLens 讓更新生效，並再試一次的權限。

## <a name="debugging-an-installed-or-running-app"></a>偵錯已安裝或執行應用程式

您可以使用 Visual Studio 偵錯而不需從 Visual Studio 專案部署已安裝的通用 Windows 應用程式。 如果您想要偵錯已安裝的應用程式套件，或如果您想要偵錯已執行的應用程式，這非常有用。
1. 移至**偵錯]-> [其他偵錯目標]-> [偵錯已安裝的應用程式套件**
2. 選取 **遠端電腦**HoloLens 的目標或**本機**的沈浸式耳機。
3. 輸入您的裝置**IP 位址**
4. 選擇**通用**驗證模式
5. 視窗會顯示執行與非作用中的應用程式。 挑選您想要偵錯。
6. 選擇 偵錯 （Managed、 原生、 混合式） 的程式碼的類型
7. 按一下 **附加**或**開始**

## <a name="see-also"></a>另請參閱
* [安裝工具](install-the-tools.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [部署和偵錯通用 Windows 平台 (UWP) 應用程式](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [啟用您的裝置進行開發](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
