---
title: Windows Mixed Reality 和新的 Microsoft Edge
description: 準備開始進行 Windows Mixed Reality 中新的 Microsoft Edge。 包含預期的變更、要查看的更新，以及已知問題。
author: mattzmsft
ms.author: mazeller
ms.date: 01/15/2020
ms.topic: article
keywords: edge、new、沉浸式 web、microsoft edge、browser、vr
ms.openlocfilehash: 2576762786c9234377308f226036c830e01d9133
ms.sourcegitcommit: d73d9012941fa1b13eb7d2f45ccc481d6365827a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885617"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality 和新的 Microsoft Edge

[新的 Microsoft Edge 現在已可供下載](https://blogs.windows.com/windowsexperience/?p=173496)，但客戶也可以在未來數個月內以測量的推出方法，[等待它安裝到 Windows 10 的後續更新中](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)。 

透過這段新聞，**我們想要讓 Windows Mixed REALITY VR 耳機客戶知道新的 Microsoft Edge 有哪些內容，並通知您一些可改善 Windows Mixed Reality web 流覽體驗的擱置更新**。

## <a name="introducing-the-new-microsoft-edge"></a>新的 Microsoft Edge 簡介

新的 Microsoft Edge 採用桌上型電腦上[的 Chromium 開放原始碼專案](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)，為客戶建立更佳的 web 相容性，並減少所有 網頁程式開發人員的 web 片段。 它也會在啟動時支援 WebXR，這是建立 VR 耳機的沉浸式 web 體驗的新標準，用來取代 WebVR。

>[!IMPORTANT]
>當您在最新的 Windows 10 裝置上安裝 Microsoft Edge 時，將會取代您電腦上先前的（舊版）版本。

## <a name="getting-ready-for-the-new-microsoft-edge"></a>準備開始新的 Microsoft Edge

Windows Mixed Reality VR 耳機客戶若想要在混合現實首頁中使用新的 Microsoft Edge，應**升級至 Windows 10 1903 版或更新版本，以在混合現實首頁中提供 Win32 應用程式的原生支援（例如新的 Microsoft Edge）** 。 檢查 Windows Update 或[手動安裝最新版的 Windows 10](https://www.microsoft.com/en-us/software-download/windows10)。

針對混合現實首頁中最佳可能的 Microsoft Edge 體驗，我們也建議您等待**windows 10 第 1 1903 版（或更新版本）的2020-01 累積更新抵達新 Microsoft edge 的一些重要 Windows Mixed reality 優化**，這應該會在一月月底的 Windows Update 中提供。

>[!IMPORTANT]
>如果您選擇在進行這些更新之前下載新的 Microsoft Edge，在 Windows Mixed Reality 中會有一些已知的問題（您可以在下方閱讀）。

## <a name="known-issues"></a>已知問題

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Windows 10 1903 版（或更新版本）的2020-01 累積更新所解決的已知問題

- 啟動任何 Win32 應用程式（包括新的 Microsoft Edge）都會讓頭戴式裝置顯示短暫凍結。
- Microsoft Edge 磚會從 Windows Mixed Reality 的 [開始] 功能表中消失（您可以在 [傳統應用程式] 資料夾中找到它）。
- 來自先前 Microsoft Edge 的 Windows 仍然會放在混合現實首頁，但無法使用。 嘗試啟用這些 windows 會啟動桌面應用程式內的邊緣。
- 選取混合現實首頁中的超連結，就會在桌面上啟動網頁瀏覽器，而不是使用混合現實首頁。
- 雖然 WebVR 不受支援，但 WebVR 展示應用程式存在於混合現實首頁中。
- 鍵盤啟動和視覺效果的一般改良功能。

### <a name="additional-known-issues"></a>其他已知問題

-   在混合現實入口網站關閉的情況下，在 Windows Mixed Reality 中開啟的網站將會遺失，但 Microsoft Edge Windows 仍會保留在混合現實首頁中的位置。
-   未 hrtf 來自 Microsoft Edge windows 的音訊。
-   **修正360檢視器延伸模組版本 2.3.8**：在 Windows Mixed Reality 中從 YouTube 開啟360影片可能會導致影片在耳機中失真。 重新開機邊緣應以不可見的程式更新360檢視器延伸模組，以解決此問題。 您可以在網址列中輸入 `edge://system/`，然後選取 [擴充功能] 旁的**展開**按鈕，以確認您擁有的延伸模組版本。
-   在 Windows Mixed Reality 會話期間，虛擬監視器會在 [設定] 中顯示為一般實體監視器 > 系統 > 顯示。



