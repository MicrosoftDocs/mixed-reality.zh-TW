---
title: OpenXR
description: 使用可攜的 OpenXR API 標準組建引擎，並將其部署至 Windows Mixed Reality 和 HoloLens 2 耳機。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，Mixed Reality OpenXR 開發人員入口網站，DirectX，native，原生應用程式自訂引擎，中介軟體
ms.openlocfilehash: cf8795e6fed7db9fd0743d0902ce1585d56fa5e0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438146"
---
# <a name="openxr"></a>OpenXR

OpenXR 是一項開放的免費免權利 API 標準，來自<a href="https://www.khronos.org/" target="_blank">Khronos</a> ，可讓引擎以原生的許可權，從多個跨[混合現實](mixed-reality.md)範圍的廠商取得各種裝置。

您可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 沉浸式耳機桌面上進行開發。  如果您沒有頭戴式裝置的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

## <a name="why-openxr"></a>為什麼要 OpenXR？

有了 OpenXR，您就可以建立以全像是 HoloLens 2）為目標的引擎，將數位內容放在真實世界中，就像真正的一樣，還有沉浸式裝置（例如桌上型電腦的 Windows Mixed Reality 耳機），其會隱藏實體全球，並以數位體驗取代。  OpenXR 可讓您撰寫程式碼一次，然後在各種不同的硬體平臺上進行移植。

OpenXR API 會使用載入器，將您的應用程式直接連接到頭戴式裝置的原生平臺支援。  這可為使用者提供最大的效能和最小延遲，不論是使用 Windows Mixed Reality 耳機或任何其他耳機。

## <a name="what-is-openxr"></a>什麼是 OpenXR？

核心 OpenXR 1.0 API 提供的基本功能，可讓您建立一個引擎，讓它能夠以全像是 HoloLens 2 和沉浸式裝置（例如 Windows Mixed Reality 耳機）為目標的所有裝置：
* 系統 + 會話
* 參考空間（view、local、stage）
* 視圖設定（mono、身歷聲）
* Swapchains + 框架時間
* 組合圖層
* 輸入和 haptics
* 圖形 API + 平臺整合

若要深入瞭解 OpenXR API，請參閱 OpenXR 1.0<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">規格</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 參考</a>和<a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速參考指南</a>。  如需詳細資訊，請參閱<a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 頁面</a>。

若要以 HoloLens 2 的完整功能集為目標，您也會使用跨廠商和廠商專屬的 OpenXR 延伸模組，以啟用 OpenXR 1.0 核心以外的其他功能，像是明確的手勢追蹤、眼睛追蹤、空間對應和空間錨點。  請參閱下面的[藍圖一](openxr.md#roadmap)節，以取得今年稍後所提供之延伸模組的詳細資訊。

請注意，OpenXR 本身不是混合的現實引擎。  相反地，OpenXR 可以讓 Unity 和 Unreal 之類的引擎撰寫可攜的程式碼一次，之後就可以存取使用者全像攝影或沉浸式裝置的原生平臺功能，而不論該平臺的哪個廠商。

## <a name="getting-started-with-openxr-for-hololens-2"></a>適用于 HoloLens 2 的 OpenXR 入門

若要開始開發 HoloLens 2 的 OpenXR 應用程式：

1. 設定 HoloLens 2 或遵循指示來[安裝 hololens 2 模擬器](using-the-hololens-emulator.md)。
1. 從裝置或模擬器內啟動 Store 應用程式，並確定已更新所有應用程式。  這可確保 HoloLens 上的 OpenXR 執行時間已更新為 OpenXR 1.0。  如果使用模擬器，您會想要參閱[模擬器輸入指示](using-the-hololens-emulator.md#basic-emulator-input)，以協助您在模擬器內使用 Store 應用程式。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>開始使用 OpenXR for Windows Mixed Reality 耳機

若要開始開發沉浸式 Windows Mixed Reality 耳機的 OpenXR 應用程式：

1. 請確定您執行的是 Windows 10 5 月2019更新（1903），這是 Windows Mixed Reality 終端使用者執行 OpenXR 應用程式的最低需求。  如果您是在舊版的 Windows 10 上，您可以使用<a href="https://www.microsoft.com//software-download/windows10" target="_blank">Windows 10 更新</a>小幫手升級至2019版的更新。  如果您無法更新您的電腦，您也可以[使用 Windows 10 2018 年10月更新（1809）來開發 OpenXR 應用程式](openxr.md#developing-on-windows-10-october-2018-update)，不過您可能會遇到較低的效能或其他問題。
2. 設定 Windows Mixed Reality 耳機，或遵循指示[啟用 Windows Mixed reality](using-the-windows-mixed-reality-simulator.md)模擬器。  設定 Windows Mixed Reality 之後，混合現實入口網站會自動安裝 Windows Mixed Reality OpenXR 執行時間。  然後，Microsoft Store 會讓執行時間保持在最新狀態。
3. 從 [開始] 功能表啟動混合現實入口網站，然後按一下 [...]，讓 Windows Mixed Reality OpenXR 執行時間變成作用中功能表左下方選取 [設定 OpenXR]。<br>
![在混合現實入口網站中設定 OpenXR](images/mixed-reality-portal-set-up-openxr.png)

如果您需要讓 Windows Mixed Reality OpenXR 執行時間再次生效，請重複步驟3。

> [!NOTE]
> Windows Mixed Reality OpenXR 執行時間很快就會針對所有 Windows Mixed Reality 使用者自動設定。

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>取得 Mixed Reality OpenXR 開發人員入口網站

若要試用 Windows Mixed Reality OpenXR 執行時間，您可以安裝<a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">[Mixed Reality OpenXR 開發人員入口網站] 應用程式</a>。  此應用程式提供的示範場景會演練 OpenXR 的各種功能，以及提供作用中執行時間和目前耳機的重要資訊的 [系統狀態] 頁面。

![Mixed Reality OpenXR 開發人員入口網站應用程式](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>建立範例 OpenXR 應用程式

<a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>專案示範一個簡單的 OpenXR 範例，其中包含兩個 Visual Studio 專案檔，一個用於 Win32 桌面應用程式，另一個用於 UWP HoloLens 2 應用程式。  因為解決方案包含 HoloLens UWP 專案，所以您需要安裝在 Visual Studio 中的[通用 Windows 平臺開發工作負載](install-the-tools.md#installation-checklist)，才能完全開啟它。

請注意，雖然 Win32 和 UWP 專案檔因封裝和部署的差異而不同，但每個專案內的應用程式代碼都是100% 的相同！

## <a name="roadmap"></a>藍圖

OpenXR 規格定義了擴充機制，可讓執行時間實施者公開超出<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Base OpenXR 1.0 規格</a>中所定義之[核心功能](openxr.md#what-is-openxr)的其他功能。

有三種 OpenXR 擴充功能：
* **廠商擴充功能（例如 MSFT）：** 啟用硬體或軟體功能中的每一廠商創新。  任何執行時間廠商隨時都可以引進和運送廠商延伸模組。
* **EXT 擴充功能：** 多家公司所定義和實行的跨廠商擴充功能。  有興趣的公司群組可以隨時引進 EXT 延伸模組。
* **KHR 延伸模組：** 正式 Khronos 延伸模組已核准為核心規格版本的一部分。  KHR 延伸模組是由與核心規格本身相同的授權所涵蓋。

一年年底，Windows Mixed Reality OpenXR 執行時間將支援一組 MSFT 和 EXT 延伸模組，將一組完整的 HoloLens 2 功能帶入 OpenXR 應用程式：
* [未系結的參考空間（全球規模的體驗）](coordinate-systems.md#building-a-world-scale-experience)
* [空間錨點 + 儲存體](spatial-anchors.md)
* [手形文字清晰度 + 手上網格](hands-and-tools.md)
* [眼睛目光](eye-tracking.md)
* [次要視圖設定（混合現實捕捉）](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [空間對應](spatial-mapping.md)
* 與 Windows SDK Api 交互操作

雖然其中一些延伸模組可能會以廠商專屬的 MSFT 延伸模組開頭，但 Microsoft 和其他 OpenXR 執行時間廠商會共同合作，為許多功能領域設計跨廠商的 EXT 或 KHR 延伸模組。  這可讓您針對這些功能所撰寫的程式碼在執行時間廠商之間具有可攜性，就像使用核心規格一樣。

## <a name="troubleshooting"></a>[疑難排解]

以下是 Windows Mixed Reality OpenXR 執行時間的一些疑難排解秘訣。  如果您有任何關於<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>的其他問題，請造訪<a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 論壇</a>或<a href="https://khr.io/slack" target="_blank">#openxr 頻道的時差</a>。

### <a name="developing-on-windows-10-october-2018-update"></a>在 Windows 10 2018 年10月更新上進行開發

如果您無法將[開發電腦升級至5月2019更新](https://www.microsoft.com//software-download/windows10)，您可以再依照下列步驟，設定 Windows 10 2018 年10月更新（1809）電腦以進行開發：

1. 請遵循上述步驟，在您的桌上型電腦上開始使用 OpenXR。
1. 若要將 Windows Mixed Reality OpenXR 執行時間設定為系統的 active OpenXR 執行時間，請安裝[Windows Mixed Reality OpenXR 開發人員相容性套件](https://aka.ms/openxr-compat)。

> [!NOTE]
> 雖然 Windows 10 2018 年10月更新（1809）可在開發 OpenXR 應用程式時使用，但 Windows 10 可能會 2019 Update （1903）是讓一般使用者使用 OpenXR 與 Windows Mixed Reality 的最低需求。  您在2018年10月更新上執行 OpenXR 應用程式時，可能會遇到較低的效能或其他問題。  強烈建議您將開發電腦升級至 Windows 10 5 月2019更新（1903）。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 應用程式未啟動 Windows Mixed Reality

如果您的 OpenXR 應用程式在執行時未啟動 Windows Mixed Reality，則 Windows Mixed Reality OpenXR 執行時間可能不會設定為作用中的執行時間。  請務必遵循上述指示，以[開始使用適用于 Windows Mixed Reality 耳機的 OpenXR](#getting-started-with-openxr-for-windows-mixed-reality-headsets) ，讓執行時間變成作用中。

您也可以執行[Mixed Reality OpenXR 開發人員入口網站](#getting-the-mixed-reality-openxr-developer-portal)，以取得有關系統上的 Windows Mixed Reality OpenXR 執行時間狀態的其他疑難排解協助。

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>混合現實入口網站未顯示 [設定 OpenXR] 功能表項目

請確定您至少執行 Windows 10 2018 年10月更新（1809）。  如果您是在舊版的 Windows 10 上，您可以使用[Windows 10 更新](https://www.microsoft.com//software-download/windows10)小幫手升級至5月2019更新（1903）。

如果您有較舊版本的混合現實入口網站應用程式，則可能無法使用 [設定 OpenXR] 功能表項目。  檢查是否有[混合現實入口網站應用程式更新](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)，以確保您擁有最新版本。

請注意，如果 Windows Mixed Reality OpenXR 執行時間已安裝且作用中，就不會顯示 [設定 OpenXR] 功能表項目。  您可以安裝[Mixed Reality OpenXR 開發人員入口網站](#getting-the-mixed-reality-openxr-developer-portal)，以判斷系統上 OpenXR 執行時間的目前狀態。

## <a name="see-also"></a>請參閱

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR 的詳細資訊</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 參考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速參考指南</a>
