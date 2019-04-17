---
title: OpenXR
description: 試試看暫時 OpenXR 0.90 API 與混合實境 OpenXR 開發人員預覽版本。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 混合的實境 OpenXR 開發人員預覽
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596355"
---
# <a name="openxr"></a>OpenXR

OpenXR 為從開放免費標準[Khronos](https://www.khronos.org/)跨越的許多廠商的各種裝置提供原生形式存取[混合的實境頻譜](mixed-reality.md)。

OpenXR，您可以建置全像攝影版裝置 （例如 HoloLens 2) 放置在真實世界的數位內容，就好像沒什麼，以及 （例如桌上型電腦的 Windows Mixed Reality 耳機） 隱藏的沈浸式裝置為目標的應用程式真實世界，並取代為數位體驗。  OpenXR 可讓您撰寫程式碼完成之後再可攜式跨各種不同的硬體平台。

OpenXR 標準處於目前佈建階段中，但針對意見反應所發行的初始 OpenXR 0.90 規格。  如需有關 OpenXR，包括存取權[暫時 0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)並[標頭](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)，請參閱[Khronos OpenXR 頁面](https://www.khronos.org/openxr/)。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a>設定混合實境 OpenXR 開發人員預覽

您可以試試看今天使用混合實境 OpenXR 開發人員預覽的暫時 OpenXR 0.90 API。  這個早期的執行階段可讓目標在桌面上目標 Windows Mixed Reality 沈浸式耳機 OpenXR 0.90 API 的應用程式。  如果您沒有存取權耳機，您可以改為使用 Windows Mixed Reality 模擬器。

若要開始使用混合實境 OpenXR 開發人員預覽版本：

1. 確定您至少執行 Windows 10 年 10 月 2018年的更新。  如果您是在舊版的 Windows 10 上，您可以升級至 10 月 2018年更新[Windows 10 更新小幫手](https://www.microsoft.com/en-us/software-download/windows10)。  如果您覺得探險，您可以安裝[Windows 10 Insider Preview 組建](https://insider.windows.com)。
1. 設定 Windows Mixed Reality 耳機或遵循指示來[啟用 Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)。
1. 安裝[混合的實境 OpenXR 開發人員預覽的應用程式](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。  此應用程式可讓您使用 preview OpenXR 執行階段上設定 Windows 10 年 10 月 2018年更新或更新版本。  安裝此應用程式之後, Windows 存放區會保留的執行階段最新狀態。
1. 從 [開始] 功能表執行混合實境 OpenXR 開發人員預覽應用程式，並遵循指示來啟用執行階段。  不久之後，此應用程式可讓您探索其他 OpenXR 偵錯資訊。

![混合的實境 OpenXR 開發人員預覽的應用程式](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a>支援 Windows 10 年 10 月 2018年更新

若要開始使用混合實境 OpenXR 開發人員預覽在 Windows 10 年 10 月 2018年更新 （Windows 目前版本），您必須遵循幾個步驟：

1. 請遵循上述步驟，以安裝混合實境 OpenXR 開發人員預覽。
1. 若要設定混合實境 OpenXR 開發人員預覽使用中 OpenXR 執行階段，您的系統，安裝[混合實境 OpenXR Developer Preview 相容性套件](https://aka.ms/openxr-compat)。

## <a name="building-a-test-openxr-app"></a>建置測試 OpenXR 應用程式

[Hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR 測試應用程式示範如何使用 API 的各種組件。  您可以遵循這些[組建指示](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md)，這會建置測試應用程式和 OpenXR 標頭本身。

## <a name="feedback"></a>意見反應

若要提供意見反應[OpenXR 暫時 0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)，請瀏覽[Khronos OpenXR 論壇](https://community.khronos.org/c/openxr)， [#openxr Slack 通道](https://khr.io/slack)而[規格問題追蹤程式](https://github.com/KhronosGroup/OpenXR-Docs/issues)。

## <a name="troubleshooting"></a>疑難排解

以下是一些疑難排解的秘訣，混合實境 OpenXR 開發人員預覽版本。  如果您遇到任何其他問題，請瀏覽[Khronos OpenXR 論壇](https://community.khronos.org/c/openxr)或是[#openxr Slack 通道](https://khr.io/slack)。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>無法啟動 Windows Mixed Reality OpenXR 應用程式

如果 OpenXR 應用程式無法啟動程式 Windows Mixed Reality，在執行時，混合實境 OpenXR 開發人員預覽可能不設定為使用中的執行階段。  請務必先執行混合實境 OpenXR 開發人員預覽應用程式，並遵循指示來啟用執行階段。

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>混合的實境 OpenXR 開發人員預覽應用程式無法安裝 

確定您至少執行 Windows 10 年 10 月 2018年的更新。  如果您是在舊版的 Windows 10 上，您可以升級至 10 月 2018年更新[Windows 10 更新小幫手](https://www.microsoft.com/en-us/software-download/windows10)。

如果混合實境 OpenXR 開發人員預覽應用程式上的 [安裝] 按鈕不會在 Windows 上執行任何動作 10 年 10 月 2018年更新，您的系統可能已快取應用程式的過時的系統需求。  您可以執行命令`wsreset.exe`清除快取的命令提示字元。

## <a name="see-also"></a>另請參閱

* [更多有關 OpenXR](https://www.khronos.org/openxr/)
* [OpenXR 暫時 0.90 規格](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR 暫時 0.90 API 參考](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR 暫時 0.90 標頭](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
