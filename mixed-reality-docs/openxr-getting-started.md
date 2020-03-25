---
title: 開始使用 OpenXR
description: 開始使用 Windows Mixed Reality 和 HoloLens 2 耳機上的可移植 OpenXR API 標準。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，windows Mixed Reality OpenXR 開發人員入口網站，DirectX，原生，原生應用程式，自訂引擎，中介軟體，開始使用，101，預覽延伸模組
ms.openlocfilehash: 7a210ce25d1e7c22710f1029aca2ca7f55a8b71c
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163332"
---
# <a name="getting-started-with-openxr"></a>開始使用 OpenXR

您可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 沉浸式耳機桌面上進行開發。  如果您沒有頭戴式裝置的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

## <a name="getting-started-with-openxr-for-hololens-2"></a>適用于 HoloLens 2 的 OpenXR 入門

若要開始開發 HoloLens 2 的 OpenXR 應用程式：

1. 設定 HoloLens 2 或遵循指示來[安裝最新版本的 hololens 2 模擬器](using-the-hololens-emulator.md)。  如果您的裝置最近已更新其 OS，或者您使用的是最新的模擬器映射，您應該已準備好 OpenXR 1.0。
1. 若要確定您已具備所有[延伸](openxr.md#roadmap)模組的最新 OpenXR 執行時間，請從裝置或模擬器內啟動 Store 應用程式，開啟右上方的功能表，按一下 [**下載和更新**]，然後按一下 [**取得更新**]。  這可確保 HoloLens 上的 OpenXR 執行時間是最新的。  請注意，如果您使用模擬器，模擬器映射會在您每次啟動時重設，因此最好的辦法就是確定您擁有[最新版的 HoloLens 2 模擬器映射](using-the-hololens-emulator.md)。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>開始使用 OpenXR for Windows Mixed Reality 耳機

若要開始開發沉浸式 Windows Mixed Reality 耳機的 OpenXR 應用程式：

1. 請確定您至少執行 Windows 10 5 月2019更新（1903），這是 Windows Mixed Reality 終端使用者執行 OpenXR 應用程式的最低需求。  如果您是在舊版的 Windows 10 上，您可以使用<a href="https://www.microsoft.com/software-download/windows10" target="_blank">windows 10 更新</a>小幫手進行升級。
2. 設定 Windows Mixed Reality 耳機，或遵循指示[啟用 Windows Mixed reality](using-the-windows-mixed-reality-simulator.md)模擬器。  當您設定 Windows Mixed Reality 時，混合現實入口網站會自動安裝 Windows Mixed Reality OpenXR 執行時間。  然後，Microsoft Store 會讓執行時間保持在最新狀態。
3. 從 [開始] 功能表啟動混合現實入口網站，然後按一下 [...]，讓 Windows Mixed Reality OpenXR 執行時間變成作用中功能表左下方選取 [設定 OpenXR]。<br>
![在混合現實入口網站中設定 OpenXR](images/mixed-reality-portal-set-up-openxr.png)

如果您需要讓 Windows Mixed Reality OpenXR 執行時間再次生效，請重複步驟3。

> [!NOTE]
> Windows Mixed Reality OpenXR 執行時間很快就會自動為所有 Windows Mixed Reality 使用者進行作用。

## <a name="getting-the-windows-mixed-reality-openxr-developer-portal"></a>取得 Windows Mixed Reality OpenXR 開發人員入口網站

若要試用 Windows Mixed Reality OpenXR 執行時間，您可以安裝<a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">Mixed Reality OpenXR 開發人員入口網站應用程式</a>。  此應用程式提供的示範場景會演練 OpenXR 的各種功能，以及提供作用中執行時間和目前耳機的重要資訊的 [系統狀態] 頁面。

如果使用模擬器，安裝混合現實 OpenXR 開發人員入口網站的最簡單方式是使用[Windows 裝置入口網站](using-the-windows-device-portal.md)，方法是流覽至 [OpenXR] 頁面，然後按一下 [開發人員功能] 底下的 [安裝] 按鈕。 （這也適用于實體 HoloLens 2 裝置）

![Mixed Reality OpenXR 開發人員入口網站應用程式](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>建立範例 OpenXR 應用程式

如果您還沒有 OpenXR 開發所需的工具，請務必加以[安裝](install-the-tools.md)。

<a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>專案示範一個簡單的 OpenXR 範例，其中包含兩個 Visual Studio 專案檔，一個用於 Win32 桌面應用程式，另一個用於 UWP HoloLens 2 應用程式。  因為解決方案包含 HoloLens UWP 專案，所以您需要安裝在 Visual Studio 中的[通用 Windows 平臺開發工作負載](install-the-tools.md#installation-checklist)，才能完全開啟它。

請注意，雖然 Win32 和 UWP 專案檔因封裝和部署的差異而不同，但每個專案內的應用程式代碼都是100% 的相同！

建立 OpenXR 的 Win32 桌面之後。EXE，不論是 Windows Mixed Reality 耳機或任何其他耳機，您都可以在任何支援 OpenXR 的 desktop VR 平臺上搭配使用 VR 頭戴式裝置。

建立 OpenXR UWP 應用程式套件之後，您可以將[該套件部署](using-visual-studio.md)到 hololens 2 裝置或 Hololens 2 模擬器。

## <a name="integrate-the-openxr-loader-into-a-project"></a>將 OpenXR 載入器整合到專案中

若要開始在現有的專案中使用 OpenXR，您將包含 OpenXR 載入器。  載入器會在裝置上探索作用中的 OpenXR 執行時間，並提供其所執行核心函式和擴充功能的存取權。

您可以從 Visual Studio 專案[參考官方的 OpenXR NuGet 套件](#reference-official-openxr-nuget-package)，或從 Khronos GitHub 存放庫中[包含官方的 OpenXR 載入器來源](#include-official-openxr-loader-source)。  任一種方法都可讓您存取 OpenXR 1.0 核心功能，加上發佈的 `KHR`、`EXT` 和 `MSFT` 延伸模組。

如果您有興趣試驗 `MSFT_preview` 延伸模組，您可以從混合現實 GitHub 存放庫[複製預覽版 OpenXR 標頭](#using-preview-extensions)。

### <a name="reference-official-openxr-nuget-package"></a>參考官方 OpenXR NuGet 套件

<a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR 載入**器 NuGet 封裝</a>是參考預先建立 OpenXR 載入器的最簡單方式。Visual Studio C++解決方案中的 DLL。  這可讓您存取 OpenXR 1.0 核心功能，加上發佈的 `KHR`、`EXT` 和 `MSFT` 延伸模組。

若要將 OpenXR 的 NuGet 套件參考新增至您的C++ Visual Studio 解決方案：
1. 在**方案總管**中，以滑鼠右鍵按一下要使用 OpenXR 的專案，然後選取 [**管理 NuGet 套件 ...** ]。
1. 切換至 [**流覽**] 索引標籤，並搜尋**OpenXR**。
1. 選取**OpenXR 載入**器套件，然後按一下右邊詳細資料窗格中的 [安裝]。
1. 按一下 [確定] 以接受專案的變更。
1. 將 `#include <openxr/openxr.h>` 新增至來源檔案，以開始使用 OpenXR API。

若要查看作用中的 OpenXR API 範例，請參閱<a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>範例應用程式。

### <a name="include-official-openxr-loader-source"></a>包含官方 OpenXR 載入器來源

如果您想要自行建立載入器，例如避免額外的載入器。DLL，您可以將官方的 Khronos OpenXR 載入器來源提取到您的專案中。  這可讓您存取 OpenXR 1.0 核心功能，加上發佈的 `KHR`、`EXT` 和 `MSFT` 延伸模組。

若要從這裡開始，請遵循<a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">GitHub 上的 Khronos OpenXR-SDK</a>存放庫中的指示。  專案設定為以 CMake 建立-如果您使用 MSBuild，則需要將程式碼複製到您自己的專案。

## <a name="using-preview-extensions"></a>使用預覽擴充功能

[延伸模組藍圖](openxr.md#roadmap)中所列的 `MSFT_preview` 延伸模組是預覽的實驗廠商延伸模組，以收集意見反應。  這些擴充功能僅適用于開發人員裝置，並會在真正的延伸模組隨附時移除。

如果您有興趣試用可用的 `MSFT_preview` 延伸模組，請執行下列步驟來更新您的專案：
1. 遵循上述其中一種方法，將 OpenXR 載入器整合到您的專案中。
1. 以<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">GitHub 上的 Mixed Reality OpenXR</a>存放庫中的預覽標頭取代您專案中的標準 OpenXR 標頭。

然後在目標 HoloLens 2 或桌上型電腦上啟用預覽延伸模組：
  1. 在目標裝置上啟用 Windows 裝置入口網站：
     * 如果您的目標裝置是 HoloLens 2 裝置，請遵循目標裝置上的[這些指示](using-the-windows-device-portal.md)。  請注意，這需要實體頭戴式裝置，因為 HoloLens 2 模擬器中的已知問題會讓下一個步驟中的 UI 無法出現在模擬器中。
     * 如果您的目標裝置是連接沉浸式耳機外設的桌上型電腦，請在目標桌上型電腦上<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop#set-up-device-portal-on-windows-desktop" target="_blank">遵循這些指示</a>。
  1. 流覽至左窗格中的 [ **OpenXR** ] 索引標籤，並啟用 [**使用最新的預覽 OpenXR 運行**時間]。  這會啟用您裝置上的預覽執行時間，其已啟用預覽延伸模組。

如需這些預覽延伸模組的檔，以及如何使用它們的範例，請參閱<a href="https://github.com/Microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">Mixed Reality OpenXR</a>存放庫。

## <a name="troubleshooting"></a>疑難排解

如果您在使用 OpenXR 開發時遇到問題，請查看我們的[疑難排解秘訣](openxr-troubleshooting.md)。