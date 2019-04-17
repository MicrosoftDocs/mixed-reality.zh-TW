---
title: 測試 HoloLens 上的應用程式
description: 指引和建議來測試您的 HoloLens 應用程式
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens 測試
ms.openlocfilehash: 35e8eff230cdcd719952ad2633ec610c9a9a26a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591803"
---
# <a name="testing-your-app-on-hololens"></a>測試 HoloLens 上的應用程式

測試的 HoloLens 應用程式是非常類似於測試 Windows 應用程式。 （功能、 互通性、 效能、 安全性、 可靠性等），則應該考慮所有一般的區域。 有，不過，有些區域需要特殊處理或注意通常不觀察在 PC 或 phone 應用程式的詳細資料。 全像攝影版的應用程式需要一組多樣化的環境中順暢執行。 他們也必須隨時維護效能和使用者的緩和。 本主題會詳細說明測試這些區域的指引。

## <a name="performance"></a>效能

全像攝影版的應用程式需要一組多樣化的環境中順暢執行。 他們也必須隨時維護效能和使用者的緩和。 效能是很重要的使用者經驗，使用全像攝影版的應用程式，我們有專用於它的整個主題。 請確定您閱讀並遵循[for Mixed Reality 的了解效能](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>測試以 3d 效果的 3D
1. **測試多個不同的空間中的應用程式，越好。** 在大房間、 小房間、 浴室、 這些、 房間、 辦公室等嘗試。也列入考量的房間裡，非標準的功能，例如非垂直牆壁、 曲線的牆、 非水平的上限。 它運作時聊天室之間轉換，樓層，瀏覽走廊或樓梯嗎？
2. **測試您的應用程式中不同光源狀況。** 沒有它適當回應不同環境的條件，例如光源、 黑色介面、 鏡像、 半透明的背景牆等透明/反射介面。
3. **在不同的動作條件測試您的應用程式。** 將放在裝置上，再次嘗試您的案例中的影片的各種狀態。 沒有它適當地回應不同的移動或穩定狀態？
4. **測試您的應用程式從不同角度的運作方式。** 如果您有鎖定的世界雷射，萬一您的使用者將逐步引導其背後怎麼辦？ 如果項目出現在使用者與全像圖之間發生什麼事？ 如果使用者是探討全像圖從高於或低於嗎？
5. **使用空間和音訊的提示。** 請確定您的應用程式所使用的是這些來防止使用者不知所措。
6. **測試您的應用程式環境的噪音的不同層級。** 如果您已實作語音命令，請嘗試叫用具有不同的層級的環境的雜訊。
7. **測試您的應用程式插入擴充槽和常設**。 請務必從座位和永久性位置進行測試。
8. **測試您的應用程式，從不同距離**。 UI 項目能夠閱讀並從遠處互動？ 對使用者到執行您的應用程式 react 程式全像投影嗎？
9. **測試您的應用程式，針對常見的應用程式列互動**。 所有的應用程式磚和 2D 的通用應用程式都有[應用程式列](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps)，可讓您控制如何將應用程式放置在混合的環境。 請確定按一下 移除依正常程序會終止您的應用程式處理序，且 上一頁 按鈕，都支援 2D 通用應用程式的內容中。 請嘗試調整和移動中的應用程式[調整模式](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps)在作用中狀態，和正在暫止應用程式圖格。

### <a name="environmental-test-matrix"></a>環境的測試矩陣

![HoloLens 的應用程式開發環境測試矩陣](images/environment-matrix-600px.png)

## <a name="comfort"></a>緩和
1. **裁剪平面。** 要到何處用心[全像投影會轉譯](hologram-stability.md#hologram-render-distances)。
2. **避免與實際磁頭移動不一致的虛擬移動。** 避免不代表使用者的實際移動的方式移動觀景窗。 如果您的應用程式需要移動使用者透過場景，讓影片更容易預測、 加速功能，最小化，並且讓使用者控制移動。
3. **遵循全像品質指導方針。** 高效能應用程式可實作[闀品質指南](hologram-stability.md)不太可能會導致使用者 discomfort。
4. **以水平方式而不是以垂直方式，請將散發全像投影。** 強迫使用者花長期查閱的時間，或向下可能會導致在頸部疲勞。

## <a name="input"></a>Input

### <a name="gaze-and-gestures"></a>視線和筆勢

[視線](gaze.md)是一種可讓使用者的目標是全像投影和環境的 HoloLens 上輸入的基本形式。 您可以以視覺化方式查看其中的目標您的視線根據游標位置。 您常會視線資料指標相關聯的滑鼠資料指標。

[筆勢](gestures.md)是您與全像投影，例如滑鼠點選的互動。 大多數情況下的滑鼠及觸控裝置的行為都相同，但務必要了解，並驗證它們之間的差異時。

**當您的應用程式具有不同的行為與滑鼠及觸控裝置驗證。** 這會識別不一致，並協助使用者，讓體驗更自然的設計決策。 例如，觸發基礎暫留時的動作。

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。

### <a name="custom-voice-commands"></a>自訂的語音命令

[語音輸入](voice-input.md)是自然互動的表單。 神奇或令人困惑，根據您選擇的命令，並在您公開的方式，可以是使用者體驗。 一般而言，您不應該使用系統語音命令，例如 「 Select 」 或 「 嘿 Cortana 」 作為自訂命令。 以下是一些需要考慮的事項：
1. **請避免使用發音類似的命令。** 這可能可以觸發正確的命令。
2. **選擇次序豐富的文字，可能的話。** 這將會最小化及/或避免 false 啟用。

### <a name="peripherals"></a>周邊設備

使用者可以與您的應用程式，透過互動[週邊設備](hardware-accessories.md)。 應用程式不需要採取任何特別動作來利用這項功能，不過有幾件事值得一查。
1. **驗證自訂的互動。** 一些事，像是您的應用程式的自訂鍵盤快速鍵。
2. **驗證切換輸入的類型。** 嘗試使用多個輸入的方法來完成工作，例如語音、 動作、 滑鼠及鍵盤全都放在相同的案例。

## <a name="system-integration"></a>系統整合

### <a name="battery"></a>電池

測試您的應用程式而不連接若要了解如何快速會清空電池電源來源。 其中一個能輕鬆地瞭解電池狀態，藉由查看電源 LED 讀數。 ![表示電池電力的 LED 狀態](images/batterypowerledindication-500px.png)

### <a name="power-state-transitions"></a>電源狀態轉換

如預期般的電源狀態之間轉換時，請驗證金鑰的情況下工作。 應用程式，例如保留其原始位置？ 它正確保存其狀態？ 它會繼續如預期般運作？
1. **待命/繼續。** 若要進入待命狀態，可以按下並立即釋放的電源按鈕。 也裝置會進入待命 3 分鐘的閒置時間後自動。 若要繼續從待命狀態，可以按下並立即釋放的電源按鈕。 如果您連接或電源中斷，裝置也會繼續。
2. **關機 / 重新啟動。** 若要關閉、 按住電源按鈕持續 6 秒。 若要重新啟動，請按 [電源] 按鈕。

### <a name="multi-app-scenarios"></a>多應用程式案例

驗證應用程式的核心功能切換應用程式，尤其是如果您已實作背景工作。 複製/貼上與 Cortana 整合也是值得適用。

## <a name="telemetry"></a>遙測

引導您使用遙測和分析。 將分析整合到您的應用程式，可協助您深入了解您的應用程式從您的 beta 版測試人員和使用者。 此資料可用來協助最佳化您的應用程式提交至存放區和未來的更新之前。 有許多分析選項。 如果您不確定要從何處開始，請參閱[App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx)。

要考量的問題：
1. 使用者如何使用的空間？
2. 應用程式有何放置物件世界可以偵測的問題嗎？
3. 多少時間他們花在不同階段的應用程式嗎？
4. 多少時間他們花在應用程式嗎？
5. 什麼最常見的使用狀況路徑的使用者嘗試？
6. 使用者會遇到未預期的狀態和/或錯誤嗎？

## <a name="emulator-and-simulated-input"></a>模擬器和模擬的輸入

[HoloLens 模擬器](using-the-hololens-emulator.md)是適合用來有效率地測試您全像攝影版的應用程式與各種不同的模擬的使用者的特性和空格。 以下是有效地使用模擬器來測試您的應用程式的一些建議：
1. **使用模擬器的虛擬聊天室擴充您的測試。** 模擬器隨附一組可供您在更多的環境中測試您的應用程式的虛擬聊天室。
2. **您可以使用模擬器來查看您的應用程式，從所有面向。** PageUp/PageDn 金鑰可讓您模擬的使用者，較高或較短。
3. **測試與實際的 HoloLens 的應用程式。** HoloLens 模擬器是很棒的工具，可協助您快速逐一查看應用程式並找到新的 bug，但請務必也測試實體 HoloLens 上再提交至 Windows 市集。 這很重要，以確保在實際的硬體上的絕佳的效能和經驗。

## <a name="automated-testing-with-perception-simulation"></a>自動化測試與 Perception 模擬

有些應用程式開發人員可能想要自動化測試的應用程式。 除了簡單的單元測試，您可以使用[perception 模擬](perception-simulation.md)HoloLens 來自動化您的應用程式的人為和世界輸入中的堆疊。 Perception 模擬 API 可以傳送模擬的輸入 HoloLens 模擬器或實體的 HoloLens。

## <a name="windows-app-certification-kit"></a>Windows 應用程式認證套件

若要讓您的應用程式的最佳機會[在 Windows 市集上發行](submitting-an-app-to-the-microsoft-store.md)、 驗證以及在本機測試之前您提交連接器等待認證。 如果您的應用程式目標設為 Windows.Holographic 裝置家族中， [Windows 應用程式認證套件](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx)只會在您的電腦上執行本機的靜態分析的測試。 在您的 HoloLens 上，將會不執行任何測試。

## <a name="see-also"></a>另請參閱
* [提交至 Windows 市集應用程式](submitting-an-app-to-the-microsoft-store.md)
