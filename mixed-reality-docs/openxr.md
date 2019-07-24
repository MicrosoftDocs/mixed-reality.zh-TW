---
title: OpenXR
description: 試用具有混合現實 OpenXR 開發人員預覽的臨時 OpenXR 0.90 API。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Mixed Reality OpenXR 開發人員預覽
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039175"
---
# <a name="openxr"></a>OpenXR

OpenXR 是一項開放的免費專利標準, 來自[Khronos](https://www.khronos.org/) , 可提供各種不同裝置的原生存取權, 而這些廠商橫跨[混合現實頻譜](mixed-reality.md)。

有了 OpenXR, 您就可以建立以全像是 HoloLens 2) 為目標的應用程式, 將數位內容放在真實世界中, 就像真正的一樣, 還有沉浸式裝置 (例如桌上型電腦的 Windows Mixed Reality 耳機), 其會隱藏實體世界, 並以數位體驗取代。  OpenXR 可讓您撰寫程式碼一次, 然後在各種不同的硬體平臺上進行移植。

OpenXR standard 目前處於暫時性階段, 併發行初始 OpenXR 0.90 規格以提供意見反應。  如需 OpenXR 的詳細資訊, 包括暫時性[0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)和[標頭](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)的存取權, 請參閱[Khronos OpenXR 頁面](https://www.khronos.org/openxr/)。 

您可以使用 Mixed Reality OpenXR Developer Preview, 在 HoloLens 2 或桌上型電腦上試用臨時的 OpenXR 0.90 API。  此早期執行時間可讓以 OpenXR 0.90 API 為目標的應用程式, 以桌上型電腦上的 HoloLens 2 或 Windows Mixed Reality 沉浸式耳機為目標。

如果您沒有頭戴式裝置的存取權, 您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>設定適用于 HoloLens 2 的 Mixed Reality OpenXR 開發人員預覽

若要開始使用 HoloLens 上的 Mixed Reality OpenXR 開發人員預覽 2:

1. 設定 HoloLens 2 或遵循指示來[安裝 hololens 2 模擬器](using-the-hololens-emulator.md)。
1. 從裝置或模擬器內啟動 Store 應用程式, 並確定已更新所有應用程式。  這會安裝混合現實 OpenXR 開發人員預覽, 以便與該裝置上的應用程式搭配使用。  如果使用模擬器, 您會想要參閱[模擬器輸入指示](using-the-hololens-emulator.md#basic-emulator-input), 以協助您在模擬器內使用 Store 應用程式。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>設定適用于沉浸式桌面耳機的混合現實 OpenXR 開發人員預覽

若要開始在桌上型電腦上使用 Mixed Reality OpenXR 開發人員預覽:

1. 請確定您執行的是 Windows 10 2018 年10月更新 (1809) 或 Windows 10 可能會2019更新 (1903)。  如果您是在舊版的 Windows 10 上, 您可以使用[Windows 10 更新](https://www.microsoft.com/en-us/software-download/windows10)小幫手升級至2019版的更新。
1. 設定 Windows Mixed Reality 耳機, 或遵循指示[啟用 Windows Mixed reality](using-the-windows-mixed-reality-simulator.md)模擬器。
1. 安裝[Mixed Reality OpenXR 開發人員預覽應用程式](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。  此應用程式可讓您設定 Windows 10 2018 年10月更新 (1809) 或更新版本上的預覽 OpenXR 執行時間。  安裝此應用程式之後, Windows Store 會讓執行時間保持在最新狀態。
1. 從 [開始] 功能表執行 Mixed Reality OpenXR 開發人員預覽應用程式, 並遵循指示將執行時間設為使用中。  很快地, 此應用程式可讓您探索其他 OpenXR 的 debug 資訊。

![Mixed Reality OpenXR 開發人員預覽應用程式](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Windows 10 2018 年10月更新的支援

如果您執行的是 Windows 10 5 月2019更新 (1903) 並遵循上述步驟, 您應該已準備好使用 Mixed Reality OpenXR 開發人員預覽!

如果您還未準備好將[桌上型電腦升級至5月2019更新](https://www.microsoft.com/en-us/software-download/windows10), 您可以執行下列一個步驟, 以繼續進行 Windows 10 2018 年10月更新 (1809):

1. 請遵循上述步驟來安裝混合現實 OpenXR 開發人員預覽版。
1. 若要將 Mixed Reality OpenXR Developer Preview 設定為系統的 active OpenXR 執行時間, 請安裝[Mixed Reality OpenXR Developer Preview 相容性套件](https://aka.ms/openxr-compat)。

## <a name="building-a-sample-openxr-app"></a>建立範例 OpenXR 應用程式

[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp)專案示範一個簡單的 OpenXR 範例, 其中包含兩個 Visual Studio 專案檔, 一個用於 Win32 桌面應用程式, 另一個用於 UWP HoloLens 2 應用程式。  因為解決方案包含 HoloLens UWP 專案, 所以您需要安裝在 Visual Studio 中的[通用 Windows 平臺開發工作負載](install-the-tools.md#installation-checklist), 才能完全開啟它。

請注意, 雖然 Win32 和 UWP 專案檔因封裝和部署的差異而不同, 但每個專案內的應用程式代碼都是 100% 的相同!

## <a name="feedback"></a>意見反應

若要提供有關[OpenXR 暫時性0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)的意見反應, 請造訪[Khronos OpenXR 論壇](https://community.khronos.org/c/openxr)、[時差 #openxr 頻道](https://khr.io/slack)和[規格問題追蹤](https://github.com/KhronosGroup/OpenXR-Docs/issues)器。

## <a name="troubleshooting"></a>疑難排解

以下是混合現實 OpenXR 開發人員預覽的一些疑難排解秘訣。  如果您遇到任何其他問題, 請造訪[Khronos OpenXR 論壇](https://community.khronos.org/c/openxr)或[#openxr 頻道的時差](https://khr.io/slack)。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 應用程式未啟動 Windows Mixed Reality

如果您的 OpenXR 應用程式在執行時沒有啟動 Windows Mixed Reality, 混合現實 OpenXR 開發人員預覽可能不會設定為作用中的執行時間。  請務必執行 Mixed Reality OpenXR 開發人員預覽應用程式, 並遵循指示使執行時間生效。

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>無法安裝 Mixed Reality OpenXR 開發人員預覽應用程式 

請確定您至少執行 Windows 10 2018 年10月更新 (1809)。  如果您是在舊版的 Windows 10 上, 您可以使用[Windows 10 更新](https://www.microsoft.com/en-us/software-download/windows10)小幫手升級至5月2019更新 (1903)。

如果混合現實 OpenXR 開發人員預覽應用程式上的 [安裝] 按鈕在 Windows 10 2018 年10月更新中沒有任何內容, 表示您的系統可能已快取應用程式的過時系統需求。  您可以從命令提示`wsreset.exe`字元執行命令, 以清除快取。

## <a name="see-also"></a>另請參閱

* [OpenXR 的詳細資訊](https://www.khronos.org/openxr/)
* [OpenXR 臨時0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR 臨時 0.90 API 參考](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR 臨時0.90 標頭](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [OpenXR 臨時0.90 快速參考指南](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
