---
title: 在 HoloLens 上測試您的應用程式
description: 測試 HoloLens 應用程式的指引和建議
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 測試
ms.openlocfilehash: 35e8eff230cdcd719952ad2633ec610c9a9a26a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549044"
---
# <a name="testing-your-app-on-hololens"></a>在 HoloLens 上測試您的應用程式

測試 HoloLens 應用程式與測試 Windows 應用程式非常類似。 所有常見的區域都應該考慮 (功能、互通性、效能、安全性、可靠性等)。 不過, 有些區域需要特別處理或留意到電腦或電話應用程式中通常不會觀察到的詳細資料。 全像攝影應用程式必須在各種不同的環境中順利執行。 他們也必須隨時維護效能和使用者的緩和度。 本主題將詳細說明這些區域的測試指引。

## <a name="performance"></a>效能

全像攝影應用程式必須在各種不同的環境中順利執行。 他們也必須隨時維護效能和使用者的緩和度。 對於使用者使用全像攝影應用程式的經驗, 我們有一個專門的主題, 因此效能非常重要。 請確定您已閱讀並遵循[瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>在3D 中測試3D
1. **盡可能在最多不同的空間中測試您的應用程式。** 在大房間、小型室、bathrooms、廚房、臥室、辦公室等方面試試看。也請考慮使用非標準功能的房間, 例如非垂直牆、彎曲牆、非水準上限。 在房間間、樓層間進行走廊或階梯轉換時, 其效果是否良好？
2. **在不同光源條件中測試您的應用程式。** 它會適當地回應不同的環境條件, 例如光源、黑色表面、透明/反射表面 (例如, 鏡像、玻璃牆等)。
3. **在不同的動作條件中測試您的應用程式。** 放在裝置上, 並在各種動作狀態下嘗試您的案例。 它是否會適當地回應不同的移動或穩定狀態？
4. **測試應用程式在不同角度的運作方式。** 如果您有全球鎖定的全息影像, 當您的使用者執行後會發生什麼事？ 如果使用者與全像投影之間有問題, 會發生什麼事？ 如果使用者從上方或下方查看全息影像該怎麼辦？
5. **使用空間和音訊提示。** 請確定您的應用程式使用這些來防止使用者遺失。
6. **在不同層級的環境雜訊上測試您的應用程式。** 如果您已執行語音命令, 請嘗試以不同的環境雜訊層級叫用。
7. **測試您的應用程式是否已安裝並待命**。 請務必同時從「座位」和「中」位置進行測試。
8. **從不同的距離測試您的應用程式**。 UI 元素可以從最遠的地方讀取和互動嗎？ 您的應用程式對使用者的回應是否太接近您的全息影像？
9. **針對常見的應用程式行互動, 測試您的應用程式**。 所有應用程式磚和2D 通用應用程式都有一個[應用程式行](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps), 可讓您控制應用程式在混合世界中的位置。 請確定按一下 [移除] 可正常終止您的應用程式進程, 並在2D 通用應用程式的內容中支援 [上一頁] 按鈕。 當您的應用程式處於作用中狀態, 且為已暫停的應用程式圖格時, 請嘗試在[調整模式](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps)中縮放並將其移動。

### <a name="environmental-test-matrix"></a>環境測試矩陣

![適用于 HoloLens 應用程式開發的環境測試矩陣](images/environment-matrix-600px.png)

## <a name="comfort"></a>舒服
1. **剪輯平面。** 用心至[呈現全息影像](hologram-stability.md#hologram-render-distances)的位置。
2. **避免虛擬移動與實際的 head 移動不一致。** 避免以不代表使用者實際動作的方式移動相機。 如果您的應用程式需要透過場景移動使用者, 請將動作設為可預測、最小化加速, 並讓使用者控制移動。
3. **請遵循全息的品質方針。** 執行全像投影[品質指引](hologram-stability.md)的高效能應用程式較不可能導致使用者 discomfort。
4. **水準散發全像投影, 而不是垂直分佈。** 強制使用者花很長的時間來搜尋或縮小, 可能會導致在頸部中疲勞。

## <a name="input"></a>Input

### <a name="gaze-and-gestures"></a>注視和手勢

[注視](gaze.md)是 HoloLens 上的一種基本形式的輸入, 可讓使用者以「全息影像」和「環境」做為目標。 您可以根據游標位置, 以視覺方式查看注視的目標位置。 通常會將注視游標與滑鼠游標建立關聯。

[手勢](gestures.md)是您與全息影像互動的方式, 就像按一下滑鼠一樣。 在大部分的情況下, 滑鼠和觸控行為都相同, 但請務必瞭解並驗證其差異。

**當您的應用程式具有滑鼠和觸控的不同行為時進行驗證。** 這會找出不一致的問題, 並協助設計決策, 讓使用者的體驗更自然。 例如, 根據滑鼠停留觸發動作。

> [!NOTE]
> [即將推出](index.md#news-and-notes)更多 HoloLens 2 特定指引。

### <a name="custom-voice-commands"></a>自訂語音命令

[語音輸入](voice-input.md)是一種自然的互動形式。 使用者體驗可能會根據您選擇的命令以及如何加以公開而神奇或混淆。 作為規則, 您不應該使用系統語音命令, 例如 "Select" 或 "嘿 Cortana" 做為自訂命令。 以下是幾個要考慮的要點:
1. **避免使用聽起來類似的命令。** 這可能會觸發不正確的命令。
2. **盡可能選擇發音豐富的文字。** 這會減少和 (或) 避免啟用錯誤。

### <a name="peripherals"></a>周邊設備

使用者可以透過[週邊設備](hardware-accessories.md)與您的應用程式互動。 應用程式不需要採取任何特殊動作, 就能利用這項功能, 不過有幾件事值得檢查。
1. **驗證自訂互動。** 您應用程式的自訂鍵盤快速鍵等專案。
2. **驗證切換輸入類型。** 在同一個案例中, 嘗試使用多個輸入方法來完成工作, 例如語音、手勢、滑鼠和鍵盤。

## <a name="system-integration"></a>系統整合

### <a name="battery"></a>電池

在未連線電源的情況下測試您的應用程式, 以瞭解耗盡電池的速度。 您可以藉由查看電源 LED 讀數, 輕鬆瞭解電池狀態。 ![指出電池電源的 LED 狀態](images/batterypowerledindication-500px.png)

### <a name="power-state-transitions"></a>電源狀態轉換

在電源狀態之間轉換時, 驗證主要案例會如預期般運作。 例如, 應用程式是否會保持其原始位置？ 它是否會正確保存其狀態？ 它是否會繼續如預期般運作？
1. **待命/繼續。** 若要進入待命, 可以立即按下並放開 [電源] 按鈕。 裝置也會在停止活動3分鐘後自動輸入待命。 若要從待命狀態繼續, 可以立即按下並放開 [電源] 按鈕。 如果您連接電源或中斷其連線, 裝置也會繼續。
2. **關閉/重新開機。** 若要關閉, 請連續按住電源按鈕6秒。 若要重新開機, 請按下 [電源] 按鈕。

### <a name="multi-app-scenarios"></a>多應用程式案例

在應用程式之間切換時驗證核心應用程式功能, 特別是在您已執行背景工作時。 複製/貼上和 Cortana 整合在適用的情況下也值得檢查。

## <a name="telemetry"></a>遙測

使用遙測和分析來引導您。 將分析整合到您的應用程式, 可協助您從 Beta 測試人員和使用者取得應用程式的深入解析。 此資料可用來在提交至存放區之前, 以及未來的更新, 協助優化您的應用程式。 這裡有許多分析選項。 如果您不確定要從何處著手, 請參閱[App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx)。

需要考慮的問題:
1. 使用者使用空間的方式為何？
2. 應用程式如何將物件放在世界中-您可以偵測到問題嗎？
3. 它們在應用程式的不同階段花了多少時間？
4. 他們在應用程式中花費了多久的時間？
5. 使用者嘗試最常見的使用方式路徑為何？
6. 使用者是否遇到非預期的狀態及/或錯誤？

## <a name="emulator-and-simulated-input"></a>模擬器和模擬輸入

[HoloLens 模擬器](using-the-hololens-emulator.md)可讓您以各種模擬的使用者特性和空間有效率地測試您的全像攝影應用程式。 以下是有效使用模擬器來測試應用程式的一些建議:
1. **使用模擬器的虛擬聊天室來擴展您的測試。** 模擬器隨附一組虛擬聊天室, 您可以用來在更多環境中測試您的應用程式。
2. **使用模擬器從所有角度查看您的應用程式。** PageUp/PageDn 金鑰會讓您的模擬使用者變得更高或更短。
3. **使用真實的 HoloLens 來測試您的應用程式。** HoloLens 模擬器是很棒的工具, 可協助您快速逐一查看應用程式並攔截新的 bug, 但請務必先在實體 HoloLens 上進行測試, 再提交到 Windows Store。 這一點非常重要, 可確保效能和經驗在實際硬體上很棒。

## <a name="automated-testing-with-perception-simulation"></a>使用認知模擬進行自動化測試

某些應用程式開發人員可能會想要自動化其應用程式的測試。 除了簡單的單元測試之外, 您還可以使用 HoloLens 中的[認知模擬](perception-simulation.md)堆疊, 將人工和世界的輸入自動化至您的應用程式。 認知模擬 API 可以將模擬的輸入傳送至 HoloLens 模擬器或實體 HoloLens。

## <a name="windows-app-certification-kit"></a>Windows 應用程式認證套件

若要讓您的應用程式能夠在[Windows](submitting-an-app-to-the-microsoft-store.md)市集中發佈, 最好先在本機進行驗證並測試, 再提交憑證以進行認證。 如果您的應用程式以 Windows 全像裝置系列為目標, 則[Windows 應用程式認證套件](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx)只會在您的電腦上執行本機靜態分析測試。 您的 HoloLens 不會執行任何測試。

## <a name="see-also"></a>另請參閱
* [將應用程式提交到 Windows Store](submitting-an-app-to-the-microsoft-store.md)
