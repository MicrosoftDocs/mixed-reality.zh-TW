---
title: 使用 Visual Studio 部署和調試
description: 如何使用 Visual Studio 來建立、偵測及部署 HoloLens 和 Windows Mixed Reality 的應用程式。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio, HoloLens, 混合現實, debug, 部署
ms.openlocfilehash: 36ed428d69802084c3b953ac2fdce46844dfdc88
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387732"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>使用 Visual Studio 部署和調試

無論您是否想要使用 DirectX 或 Unity 來開發混合的現實應用程式, 都將使用 Visual Studio 來進行調試和部署。 在本節中, 您將瞭解:
* 如何透過 Visual Studio 將應用程式部署到 HoloLens 或 Windows Mixed Reality 的沉浸式耳機。
* 如何使用內建的 HoloLens 模擬器來 Visual Studio。
* 如何進行混合式現實應用程式的偵錯工具。

## <a name="prerequisites"></a>必要條件
1. 如需安裝指示, 請參閱[安裝工具](install-the-tools.md)。
2. 在 Visual Studio 2015 Update 1、Visual Studio 2017 或 Visual Studio 2019 中建立新的通用 Windows 應用程式專案。 C#、 C++和 JavaScript 專案都受到支援。 (或遵循指示,[在 Unity 中建立應用程式](holograms-100.md)。)

## <a name="enabling-developer-mode"></a>啟用開發人員模式

一開始請先在您的裝置上啟用**開發人員模式**, 讓 Visual Studio 可以連接到它。

### <a name="hololens"></a>HoloLens
1. 開啟 HoloLens 並放在裝置上。
2. 做出[盛開](gestures.md#bloom)手勢來啟動主功能表。
3. 注視 [**設定**] 圖格, 然後執行 [[空中](gestures.md#air-tap)] 手勢。 做出第二次的空中點選，來將 App 放置於您的環境中。 當您放置 [設定] App 之後，該 App 便會啟動。
4. 選取 [更新]  功能表項目。
5. 選取 [適用於開發人員]  功能表項目。
6. 啟用 [開發人員模式]  。 這可讓您將[應用程式從 Visual Studio 部署](using-visual-studio.md)到 HoloLens。
7. 選擇性：向下滾動, 同時啟用 [**裝置入口網站**]。 這也可讓您從網頁瀏覽器連接到 HoloLens 上的[Windows 裝置入口網站](using-the-windows-device-portal.md)。

### <a name="windows-pc"></a>Windows 電腦

如果您使用的是連線到電腦的 Windows Mixed Reality 耳機, 則必須在電腦上啟用**開發人員模式**。
1. 前往 [**設定**]
2. 選取**更新與安全性**
3. **為開發人員**選擇
4. 啟用**開發人員模式**, 閱讀您所選設定的免責聲明, 然後按一下 [是] 以接受變更。

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>透過 Wi-fi-HoloLens 部署應用程式 (第1代)
1. 在 Visual Studio中, 為您的應用![程式 x86 組建設定選取 x86 組建設定](images/x86setting.png)
2. 在  [部署目標] 下拉式功能表![中選取 [遠端電腦], Visual Studio 中的 [遠端電腦部署目標]](images/remotemachinesetting.png)
3. 針對C++和 JavaScript 專案, 移至 **專案 > 屬性 > 設定屬性 > 調試**程式。 針對C#專案, 對話方塊會自動快顯以設定您的連接。
  a. 在 [**位址**] 或 [**電腦名稱稱**] 欄位中, 輸入您裝置的 IP 位址。 在 [設定] 底下的 [ **> 網路 & 網際網路] > [Advanced Options**] 底下尋找您 HOLOLENS 的 ip 位址, 或者您可以詢問 Cortana 「我的 IP 位址是什麼？」
  b. 將 [驗證模式 Visual Studio] 設定為 **[通用 (未加密的通訊協定)** ![] [遠端連線] 對話方塊](images/remotedeploy.png)
4. 選取 [ **Debug > 開始進行調試**程式] 以部署您![的應用程式, 並開始在不進行任何偵測的 Visual Studio](images/deploynodebugging.png)
5. 當您第一次從電腦將應用程式部署到 HoloLens 時, 系統會提示您輸入 PIN 碼。 遵循下列**配對您的裝置**指示。

如果您的 HoloLens IP 位址變更, 您可以前往 [**專案] >** [內容] > [設定] [屬性], 以變更目的電腦的 ip 位址 >

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>透過 USB 部署應用程式-HoloLens (第1代)
1. 在 Visual Studio中, 為您的應用![程式 x86 組建設定選取 x86 組建設定](images/x86setting.png)
2. 在  [部署目標] 下拉式功能表![中, 選取 [裝置部署] 中的 [裝置] Visual Studio](images/buildsettingsusbdeploy.png)
3. 選取 [ **Debug > 開始進行調試**程式] 以部署您![的應用程式, 並開始在不進行任何偵測的 Visual Studio](images/deploynodebugging.png)
4. 當您第一次從電腦將應用程式部署到 HoloLens 時, 系統會提示您輸入 PIN 碼。 遵循下列**配對您的裝置**指示。

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>將應用程式部署到您的本機電腦-沉浸式耳機

使用可連接到您的電腦或[混合現實](using-the-windows-mixed-reality-simulator.md)模擬器的 Windows Mixed Reality 沉浸式耳機時, 請遵循這些指示。 在這些情況下, 只需在本機電腦上部署並執行您的應用程式即可。
1. 為您的應用程式選取**x86**或**x64**組建設定
2. 在 [部署目標] 下拉式功能表中選取 [**本機電腦**]
3. 選取 [ **Debug > 開始進行調試**程式] 以部署您的應用程式並開始進行偵錯工具

## <a name="pairing-your-device---hololens-1st-gen"></a>配對您的裝置-HoloLens (第1代)

當您第一次將應用程式從 Visual Studio 部署至 HoloLens 時, 系統會提示您輸入 PIN 碼。 在 HoloLens 上, 啟動 [設定] 應用程式以產生 PIN, 移至**開發人員的更新 >** , 然後按一下 [**配對**]。 您的 HoloLens 會顯示 PIN;在 Visual Studio 中輸入此 PIN。 配對完成後, 請在您的 HoloLens 上按 [**完成**] 以關閉對話方塊。 這部電腦現在已與 HoloLens 配對, 而且您將能夠自動部署應用程式。 針對每個用來將應用程式部署至 HoloLens 的後續電腦重複這些步驟。

若要將您的 HoloLens 從其配對的所有電腦解除配對, 請啟動 [**設定**] 應用程式, 移至**開發人員的 [更新 >** ], 然後按一下 [**清除**]。

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>將應用程式部署至 HoloLens (第1代) 模擬器
1. 請確定您已 **[安裝 HoloLens 模擬器](install-the-tools.md)** 。
2. 選取應用程式的**x86**組建設定。
![Visual Studio 中的 x86 組建設定](images/x86setting.png)
3. 在 [部署目標] 下拉式功能表![中選取 [ **HoloLens 模擬器**], Visual Studio 中的 [模擬器目標]](images/deployemulator.png)
4. 選取 [ **Debug > 開始進行調試**程式] 以部署您![的應用程式, 並開始在不進行任何偵測的 Visual Studio](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>圖形偵錯工具

撰寫和優化全像攝影應用程式時, Visual Studio 圖形診斷工具非常有説明。 如需完整詳細資料, 請參閱[MSDN 上的 Visual Studio 圖形診斷](https://msdn.microsoft.com/library/hh315751.aspx)。

**啟動圖形偵錯工具**
1. 遵循上面的指示, 以裝置或模擬器為目標
2. 移至**Debug > 圖形 > 開始診斷**
3. 第一次使用 HoloLens 執行此動作時, 您可能會收到「拒絕存取」錯誤。 重新開機 HoloLens 以允許更新的許可權生效, 然後再試一次。

## <a name="profiling"></a>探測

Visual Studio 分析工具可讓您分析應用程式的效能和資源使用。 這包括將 CPU、記憶體、圖形和網路使用優化的工具。 如需完整詳細資料, 請參閱[在 MSDN 上執行診斷工具而不進行調試](https://msdn.microsoft.com/library/dn957936.aspx)程式。

**使用 HoloLens 啟動分析工具**
1. 遵循上面的指示, 以裝置或模擬器為目標
2. 移至**Debug > 開始診斷工具而不進行任何調試 ...**
3. 選取您想要使用的工具
4. 按一下 [**開始**]
5. 第一次使用 HoloLens 執行此動作時, 您可能會收到「拒絕存取」錯誤。 重新開機 HoloLens 以允許更新的許可權生效, 然後再試一次。

## <a name="debugging-an-installed-or-running-app"></a>偵測已安裝或執行中的應用程式

您可以使用 Visual Studio 來進行已安裝的通用 Windows 應用程式, 而不需要從 Visual Studio 專案進行部署。 如果您想要對已安裝的應用程式套件進行偵錯工具, 或想要對已經在執行的應用程式進行偵測, 這會很有用。
1. 移至**debug-> 其他的 Debug 目標-> Debug 已安裝的應用程式套件**
2. 針對適用于沉浸式耳機的 HoloLens 或**本機電腦**選取**遠端電腦**目標。
3. 輸入您裝置的**IP 位址**
4. 選擇**通用**驗證模式
5. 此視窗會顯示執行中和非使用中的應用程式。 挑選您想要進行 debug 的一個。
6. 選擇要進行 debug 錯的程式碼類型 (Managed、原生、混合)
7. 按一下 [**附加**] 或 [**啟動**]

## <a name="see-also"></a>另請參閱
* [安裝工具](install-the-tools.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [部署和調試通用 Windows 平臺 (UWP) 應用程式](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [啟用您的裝置以進行開發](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
