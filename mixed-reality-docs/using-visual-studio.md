---
title: 使用 Visual Studio 來部署和偵錯
description: 了解如何使用 Visual Studio 來建置、偵錯及部署 HoloLens 和 Windows Mixed Reality 的應用程式。
author: pbarnettms
ms.author: pbarnett
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合實境, 偵錯, 部署
ms.openlocfilehash: fecd9db8777b6947c3ea19a02e428459c78c935b
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491188"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>使用 Visual Studio 來部署和偵錯

無論您是想要使用 DirectX 或 Unity 來開發混合實境應用程式，都將使用 Visual Studio 來進行偵錯和部署。 在本節中，您將了解如何：
* 透過 Visual Studio 將應用程式部署到 HoloLens 或 Windows Mixed Reality 沉浸式頭戴裝置。
* 使用內建至 Visual Studio 的 HoloLens 模擬器。
* 針對混合實境應用程式進行偵錯。

## <a name="prerequisites"></a>必要條件
1. 如需安裝指示，請參閱[安裝工具](install-the-tools.md)。
2. 在 Visual Studio 中建立新的通用 Windows app 專案。  對於 HoloLens (第 1 代)，使用 Visual Studio 2017 或更新版本。  對於 Hololens 2，使用 Visual Studio 2019 16.2 或更新版本。 支援 C# 和 C++。 (或者遵循指示，[在 Unity 中建立應用程式](holograms-100.md)。)

## <a name="enabling-developer-mode"></a>啟用開發人員模式

從在您的裝置上啟用**開發人員模式**開始，讓 Visual Studio 可以與它連線。

### <a name="hololens"></a>HoloLens
1. 開啟您的 HoloLens 並將裝置戴上。
2. 做出[盛開](system-gesture.md#bloom)手勢來啟動主功能表。
3. 凝視 [設定]  磚，並做出[空中點選](gaze-and-commit.md#composite-gestures)手勢。 做出第二次的空中點選，來將 App 放置於您的環境中。 當您放置 [設定] App 之後，該 App 便會啟動。
4. 選取 [更新]  功能表項目。
5. 選取 [適用於開發人員]  功能表項目。
6. 啟用 [開發人員模式]  。 這可讓您[將應用程式從 Visual Studio](using-visual-studio.md) 部署到 HoloLens。
7. 選擇性：向下捲動並啟用**裝置入口網站**。 這也可讓您從網頁瀏覽器連線到您 HoloLens 上的 [Windows 裝置入口網站](using-the-windows-device-portal.md)。

### <a name="windows-pc"></a>Windows PC

如果您使用的是連線到電腦的 Windows Mixed Reality 頭戴式裝置，就必須在電腦上啟用**開發人員模式**。
1. 移至 [設定] 
2. 選取 [更新與安全性] 
3. 選取 [適用於開發人員] 
4. 啟用 [開發人員模式]  ，閱讀您所選設定的免責聲明，然後按一下 [是] 來接受變更。

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>透過 Wi-Fi 部署應用程式 - HoloLens (第 1 代)
1. 針對您的應用程式選取 **x86** 組建設定 ![Visual Studio 中的 x86 組建設定](images/x86setting.png)
2. 在 [部署目標] 下拉式功能表中選取 [遠端電腦]  ![Visual Studio 中的遠端電腦部署目標](images/remotemachinesetting.png)
3. 針對 C++ 和 JavaScript 專案，請移至 [專案 > 屬性 > 設定屬性 > 偵錯]  。 針對 C# 專案，會自動顯示用來設定連線的對話方塊。
  a. 在 [位址]  或 [電腦名稱]  欄位中，輸入您裝置的 IP 位址。 在 [設定 > 網路和網際網路 > 進階選項]  底下，尋找 HoloLens 的 IP 位址，或者您可以詢問 Cortana：「我的 IP 位址是什麼？」
  b. 將「驗證模式」設定為**通用 (未加密通訊協定)** ![Visual Studio 中的遠端連線對話方塊](images/remotedeploy.png)
4. 選取 [偵錯 > 開始偵錯]  以部署您的應用程式並開始偵錯![在 Visual Studio 中啟動但不進行偵錯](images/deploywithdebugging.png)
5. 當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。 遵循以下的**配對您的裝置**指示。

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>透過 Wi-Fi 部署應用程式 - HoloLens 2
1. 針對您的應用程式選取 **ARM** 或 **ARM64** 組建設定 ![Visual Studio 中的 ARM64 組建設定](images/arm64setting.png)
2. 在 [部署目標] 下拉式功能表中選取 [遠端電腦]  ![Visual Studio 中的遠端電腦部署目標](images/remotemachinesetting_arm64.png)
3. 針對 C++ 和 JavaScript 專案，請移至 [專案 > 屬性 > 設定屬性 > 偵錯]  。 針對 C# 專案，會自動顯示用來設定連線的對話方塊。
  a. 在 [位址]  或 [電腦名稱]  欄位中，輸入您裝置的 IP 位址。 在 [設定 > 網路和網際網路 > 進階選項]  底下，尋找 HoloLens 的 IP 位址，或者您可以詢問 Cortana：「我的 IP 位址是什麼？」
  b. 將「驗證模式」設定為**通用 (未加密通訊協定)** ![Visual Studio 中的遠端連線對話方塊](images/remotedeploy.png)
4. 選取 [偵錯 > 開始偵錯]  以部署您的應用程式並開始偵錯![在 Visual Studio 中啟動但不進行偵錯](images/deploywithdebugging.png)
5. 當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。 遵循以下的**配對您的裝置**指示。

如果您的 HoloLens IP 位址變更，您可以移至 [專案 > 屬性 > 設定屬性 > 偵錯]  ，以變更目標電腦的 IP 位址

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>透過 USB 部署應用程式 - HoloLens (第 1 代)
1. 針對您的應用程式選取 **x86** 組建設定 ![Visual Studio 中的 x86 組建設定](images/x86setting.png)
2. 在 [部署目標] 下拉式功能表中選取 [裝置]  ![Visual Studio 中的裝置部署](images/buildsettingsusbdeploy.png)
3. 選取 [偵錯 > 開始偵錯]  以部署您的應用程式並開始偵錯![在 Visual Studio 中啟動但不進行偵錯](images/deploywithdebugging.png)
4. 當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。 遵循以下的**配對您的裝置**指示。

## <a name="deploying-an-app-over-usb---hololens-2"></a>透過 USB 部署應用程式 - HoloLens 2
1. 針對您的應用程式選取 **ARM** 或 **ARM64** 組建設定 ![Visual Studio 中的 ARM64 組建設定](images/arm64setting.png)
2. 在 [部署目標] 下拉式功能表中選取 [裝置]  ![Visual Studio 中的裝置部署](images/buildsettingsusbdeploy_arm64.png)
3. 選取 [偵錯 > 開始偵錯]  以部署您的應用程式並開始偵錯![在 Visual Studio 中啟動但不進行偵錯](images/deploywithdebugging.png)
4. 當您第一次從電腦將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。 遵循以下的**配對您的裝置**指示。

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>將應用程式部署到您的本機電腦 - 沉浸式頭戴裝置

使用可連線到您的電腦或[混合實境模擬器](using-the-windows-mixed-reality-simulator.md)的 Windows Mixed Reality 沉浸式頭戴裝置時，請遵循這些指示。 在這些情況下，只需在本機電腦上部署並執行您的應用程式即可。
1. 為您的應用程式選取 **x86** 或 **x64** 組建設定
2. 在 [部署目標] 下拉式功能表中，選取 [本機電腦] 
3. 選取 [偵錯 > 開始偵錯]  來部署您的應用程式並開始偵錯

## <a name="pairing-your-device"></a>配對您的裝置

當您第一次從 Visual Studio 將應用程式部署到 HoloLens 時，系統會提示您輸入 PIN 碼。 在 HoloLens 上，移至 [更新 > 適用於開發人員]  ，並點選 [配對]  ，藉由啟動 [設定] 應用程式來產生 PIN。 PIN 會顯示在您的 HoloLens 上；在 Visual Studio 中輸入這個 PIN。 配對完成之後，點選 HoloLens 上的 [完成]  以關閉對話方塊。 這部電腦現在已與 HoloLens 配對，您可以自動部署應用程式。 針對後續用來將應用程式部署至 HoloLens 的每部電腦重複這些步驟。

若要將您的 HoloLens 從其配對的所有電腦解除配對，請啟動 [設定]  應用程式，移至 [更新 > 適用於開發人員]  ，然後點選 [清除]  。

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>將應用程式部署至 HoloLens (第 1 代) 模擬器
1. 請確定您已 **[安裝 HoloLens 模擬器](install-the-tools.md)** 。
2. 為您的應用程式選取 **x86** 組建設定。
![Visual Studio 中的 x86 組建設定](images/x86setting.png)
3. 選取 [部署目標] 下拉式功能表中的 [HoloLens 模擬器]  ![Visual Studio 中的模擬器目標](images/deployemulator.png)
4. 選取 [偵錯 > 開始偵錯]  以部署您的應用程式並開始偵錯![在 Visual Studio 中啟動但不進行偵錯](images/deploywithdebugging.png)

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>將應用程式部署至 HoloLens 2 模擬器
1. 請確定您已 **[安裝 HoloLens 模擬器](install-the-tools.md)** 。
2. 為您的應用程式選取 **x86** 或 **x64** 組建設定。
![Visual Studio 中的 x86 組建設定](images/x86setting.png)
3. 選取 [部署目標] 下拉式功能表中的 [HoloLens 2 模擬器]  ![Visual Studio 中的模擬器目標](images/deployemulator2.png)
4. 選取 [偵錯 > 開始偵錯]  以部署您的應用程式並開始偵錯![在 Visual Studio 中啟動但不進行偵錯](images/deploywithdebugging.png)

## <a name="graphics-debugger-for-hololens-1st-gen"></a>HoloLens (第 1 代) 的圖形偵錯工具

撰寫和最佳化全像攝影應用程式時，Visual Studio 圖形診斷工具非常有幫助。 如需完整詳細資料，請參閱 [MSDN 上的 Visual Studio 圖形診斷](https://msdn.microsoft.com/library/hh315751.aspx)。

**啟動圖形偵錯工具**
1. 遵循上述指示，以裝置或模擬器為目標
2. 移至 [偵錯 > 圖形 > 開始診斷] 
3. 第一次使用 HoloLens 執行此動作時，您可能會遇到「拒絕存取」錯誤。 將 HoloLens 重新開機讓更新的權限生效，然後再試一次。

## <a name="profiling"></a>程式碼剖析

Visual Studio 程式碼剖析工具可讓您分析應用程式的效能和資源使用。 包括將 CPU、記憶體、圖形和網路使用最佳化的工具。 如需完整詳細資料，請參閱 [MSDN 上的執行診斷工具而不進行偵錯](https://msdn.microsoft.com/library/dn957936.aspx)。

**使用 HoloLens 啟動程式碼剖析工具**
1. 遵循上述指示，以裝置或模擬器為目標
2. 移至 [偵錯 > 啟動診斷工具但不偵錯...]  。
3. 選取您想要使用的工具
4. 按一下 [開始] 
5. 第一次使用 HoloLens 執行此動作時，您可能會遇到「拒絕存取」錯誤。 將 HoloLens 重新開機讓更新的權限生效，然後再試一次。

## <a name="debugging-an-installed-or-running-app"></a>針對已安裝或執行中的應用程式進行偵錯

您可以使用 Visual Studio 針對已安裝但未從 Visual Studio 專案部署的通用 Windows app 進行偵錯。 如果您想要對已安裝的應用程式套件進行偵錯，或想要對已經在執行中的應用程式進行偵錯，這會很有用。
1. 移至 [偵錯 -> 其他偵錯目標 -> 針對已安裝的應用程式套件進行偵錯] 
2. 針對 HoloLens 選取 [遠端電腦]  目標，或針對沉浸式頭戴裝置選取 [本機電腦]  。
3. 輸入您裝置的 **IP 位址**
4. 選擇 [通用]  驗證模式
5. 此視窗會顯示執行中和非使用中的應用程式。 挑選您想要進行偵錯的應用程式。
6. 選擇要進行偵錯的程式碼類型 (受控、原生、混合)
7. 按一下 [附加]  或 [啟動] 

## <a name="see-also"></a>請參閱
* [安裝工具](install-the-tools.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [部署和偵錯通用 Windows 平台 (UWP) app](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [啟用您的裝置以進行開發](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
