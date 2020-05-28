---
title: 版本資訊-5 月2020
description: 適用于 Windows 10 5 月2020更新的 windows Mixed Reality 版本資訊（也稱為2004）。
author: tmlyon
ms.author: tmlyon
ms.date: 05/27/2020
ms.topic: article
keywords: 版本資訊，版本，windows 10，組建，20H1，os，5月2020日，2004
ms.openlocfilehash: ec92259662109001c02cf631eb6b9948d61ba9de
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84124135"
---
# <a name="release-notes---may-2020"></a>版本資訊-5 月2020

**Windows 10 2020 版更新（v2004）** 包含 Windows mixed REALITY （VR）耳機的新功能，例如在混合現實首頁中啟動 Win32 應用程式的能力。 HoloLens （第1代）是長期服務（LTS），每個月都會發行服務更新。

若要更新電腦上 Windows Mixed Reality 沉浸（VR）耳機的最新版本，請開啟 [**設定**] 應用程式，移至 [**更新 & 安全性**]，然後選取 [**檢查更新**] 按鈕。 在 Windows 10 電腦上，您也可以使用[windows media 建立工具](https://www.microsoft.com/software-download/windows10)，手動安裝**Windows 10 5 月2020更新**。

**最新的桌上出版本**： Windows 10 v2004 （10.0.19041.264）

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沉浸式耳機的更新

### <a name="introducing-the-new-microsoft-edge"></a>新的 Microsoft Edge 簡介
如[先前所宣佈](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge)，我們已使用 Windows Mixed Reality 中新的 Microsoft Edge 瀏覽器進行更新，以提供更佳的支援。 新的 Microsoft Edge 採用 Chromium 開放原始碼專案，為客戶建立更佳的 web 相容性，並減少所有 網頁程式開發人員的 web 片段。 它也支援 WebXR，這是建立 VR 耳機的沉浸式 web 體驗的新標準，用來取代 WebVR。

### <a name="improved-settings-for-wmr"></a>改良的 WMR 設定
感謝您的意見反應，我們已新增並澄清頭戴式裝置顯示頁面上的設定：

* **我家裡的視覺品質**-變更這些設定只會影響混合現實的家庭環境（Cliff 房子和 Skyloft）：

* **調整混合現實首頁中的詳細資料層級和效果品質**-這會變更我們在家裡使用的部分轉譯。 特別的是，當您將此設定從低變更為高時，不同材質的視覺品質（木材、具體等）將會調整。

* **變更應用程式視窗解析度**-根據預設，在家裡啟動的大部分2d 視窗都是以720p 解析度啟動。 雖然您可以手動 & 垂直調整它們的大小，但您也可以選擇讓它們全都以1080p 啟動。 先前這個選項在 [視覺品質] 下是以高（搶鮮版）選項的形式提供。 我們已適當地將它分割成另一個設定。

* **體驗選項**-這些選項會調整混合現實體驗，以降低硬體可能會難以趕上不受限制 90 fps 的系統負載。 您可以選擇明確啟用或停用這些額外的設定，或選擇 [讓 Windows 決定]，然後讓啟發學習法繼續決定何時要切換這些功能。

* **解決**方式-如果您有高解析度的頭戴式裝置，像是 HP 回音，我們支援以原生解析度執行，或基於效能考慮以較低的解析度來執行。 先前的耳機（例如 Samsung 電影對白和電影對白 +）只支援單一解析度，因此您將無法在那些耳機上變更此設定。

* **畫面播放速率**-您現在可以手動設定頭戴式裝置顯示器的畫面播放速率，或繼續讓 Windows 使用其啟發學習法來判斷 60 hz 或 90 Hz 是否更適當。

* **校正**-如同之前一樣，如果您的耳機支援，您可以調整 IPD （interpupillary 距離）。

* **輸入切換**-將輸入焦點切換（Win + Y）行為切換為自動（根據目前狀態感應器的意見反應）或手動。

### <a name="new-cortana-app"></a>新增 Cortana 應用程式
Windows 的這項更新包含最新版的 Cortana 應用程式，目前僅限英文版，不再支援特定的混合現實特定命令，例如「拍照」和「觀看影片」。 您仍然可以使用新的 Cortana 來啟動應用程式，而且它也支援以生產力為焦點的新命令，例如「我的下一個會議何時？」 或是「傳送一封電子郵件給 <name> 我的最近執行中」。

#### <a name="please-help-us-improve"></a>請協助我們改進！
我們持續探討改善相容性。  如果您發現您最愛的傳統 Win32 應用程式在 Windows Mixed Reality 中的行為不正確，請透過我們的[意見反應中樞](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)提交意見反應。

## <a name="prior-release-notes"></a>先前的版本資訊

* [版本資訊-5 月2019](release-notes-may-2019.md)
* [版本資訊 - 2018 年 10 月](release-notes-october-2018.md)
* [版本資訊-2018 年4月](release-notes-april-2018.md)
* [版本資訊 - 2017 年 10 月](release-notes-october-2017.md)
* [版本資訊 - 2016 年 8 月](release-notes-august-2016.md)
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [沉浸式耳機支援（外部連結）](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 支援（外部連結）](https://support.microsoft.com/products/hololens)
* [安裝工具](install-the-tools.md)
* [提供意見反應給我們](give-us-feedback.md)
