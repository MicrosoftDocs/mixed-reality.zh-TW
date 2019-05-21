---
title: 硬體附屬應用程式
description: 描述可搭配 HoloLens 與 Windows Mixed Reality，以及如何設定它們的附屬應用程式的類型。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 操作說明、 附屬應用程式、 藍芽、 bt、 控制器、 遊戲台、 clicker、 xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596979"
---
# <a name="hardware-accessories"></a>硬體附屬應用程式

Windows Mixed Reality 裝置支援 附屬應用程式。 您會將 支援的附屬應用程式時您可以使用藍芽或 USB 組支援附屬應用程式可透過它所連接的 PC 沈浸式耳機使用藍芽、 HoloLens。

使用 HoloLens 的附屬應用程式的兩個常見案例是取代空中點選手勢和虛擬的鍵盤。 這麼做，是兩個最常見的附屬應用程式**HoloLens Clicker**並**藍芽鍵盤**。 Microsoft HoloLens 藍芽 4.1 選項以及支援[藍芽 HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29)並[藍芽 GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29)設定檔。

Windows Mixed Reality 沈浸式耳機需要附屬應用程式之外的輸入[視線](gaze.md)並[語音](voice-input.md)。 支援的附屬應用程式包括 **鍵盤和滑鼠** ， **遊戲台** ， 並 **[動作控制站](motion-controllers.md)** 。

## <a name="pairing-bluetooth-accessories"></a>配對的藍牙配件

配對藍芽週邊設備與 Microsoft HoloLens 大致配對藍芽週邊設備與 Windows 10 電腦或行動裝置：
1. 從 [開始] 功能表中，開啟**設定**應用程式
2. 移至**裝置**
3. 使用滑桿切換關閉時開啟藍芽無線電
4. 將您的藍芽裝置放在配對的模式。 這個變動裝置。 在大多數的藍芽裝置上，這是完成按住一個或多個按鈕。
5. 等候才會出現在清單中的藍芽裝置的裝置名稱。 當它未選取裝置然後選取**配對** 按鈕。 如果您有許多您附近的藍牙裝置可能需要捲動到底部的 藍芽裝置清單，以查看您嘗試配對的裝置。
6. 如果配對的藍牙周邊設備與輸入功能 (例如：藍芽鍵盤） 可能會顯示 6 位數或 8 位數的 pin。 請務必在週邊設備上輸入 pin，然後按 enter 完成搭配 Microsoft HoloLens。

## <a name="motion-controllers"></a>動作控制站

Windows Mixed Reality[動作控制器](motion-controllers.md)受到沈浸式耳機，但不是 HoloLens。 這些控制站提供精確且回應迅速的沈浸式耳機，這表示不需要安裝在您的空間牆上的硬體中使用的感應器，在欄位的檢視中移動的追蹤。 每個控制站提供數種方法的輸入。

![Windows Mixed Reality 動作控制站](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

HoloLens Clicker 是專為 HoloLens 建置第一個周邊裝置，並隨附 HoloLens Development Edition。 HoloLens Clicker 可讓使用者按一下，並使用最少的手動動作捲動空中點選手勢來取代。 它不會取代所有[筆勢](gestures.md)。 比方說， [bloom](gestures.md#bloom)並[調整大小或移動](gestures.md#composite-gestures)筆勢使用手動動作。 HoloLens clicker 是方向感應器裝置使用簡單的按鈕。 它會連線到使用藍牙低能源 (BTLE) HoloLens。

![HoloLens Clicker](images/hololens-clicker-500px.jpg)

若要選取[全像](hologram.md)，注視，，然後按一下。 Clicker 的方向沒有影響這項作業。 若要捲動或移動瀏覽，按一下並按住，然後將旋轉 Clicker 向上/向下或左/右。 捲動時，您將達到儘量減少為 + /-15 ° 手腕旋轉的速度最快使用。 移動多個將不會捲動任何更快。

有兩顆 Led 將 Clicker 內：
* 白色的 LED 指出裝置是否配對 （閃爍） 或收費 （實線）
* 琥珀色 LED 指出裝置 （閃爍） 的電力偏低，或是發生失敗 （實線）

您可以預期 2 週或多個一般用途，充滿的電源 （亦即，在牆充電器的 2 到 3 小時）。 當電池變少時，琥珀色 LED 將會閃爍 10 次某段 5 秒，如果您按下按鈕，或喚醒從睡眠狀態。 琥珀色 LED 將會更快速地閃爍 5 秒的期間如果您 Clicker 為極低的電池模式。

## <a name="bluetooth-keyboards"></a>藍芽鍵盤

英文 Qwerty 藍芽鍵盤可以配對，您可以使用全像攝影版的鍵盤的任何地方使用。 取得品質鍵盤發出差異，因此，建議[Microsoft 通用的可摺疊 Keyboard](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001)或[Microsoft 設計工具的藍芽 Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)。

## <a name="bluetooth-gamepads"></a>藍芽舵

您可以使用一個控制站與應用程式和遊戲，特別是讓遊戲台支援。 舵無法用以控制 HoloLens 使用者介面。

隨附於 Xbox 一個 S 或銷售附屬應用程式針對 Xbox 一個 S 功能藍牙連線能力，讓它們能夠搭配 HoloLens 和沈浸式耳機的 Xbox 無線控制站。 Xbox 無線控制器[必須更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)搭配 HoloLens 之前。

其他品牌的藍芽舵可能使用 Windows Mixed Reality 裝置，但支援會因應用程式。

## <a name="other-bluetooth-accessories"></a>其他藍牙配件

只要週邊設備都支援藍芽 HID 或 GATT 設定檔，它都能夠與 HoloLens 配對。 除了鍵盤、 滑鼠及 HoloLens Clicker 其他藍芽 HID 和 GATT 的裝置可能需要在 Microsoft HoloLens 上完全恢復運作的隨附應用程式。

不支援的週邊設備包括：
* 不支援藍芽音訊設定檔中的週邊設備。
* 藍芽的音訊裝置，例如喇叭及耳機可能會出現在 [設定] 應用程式中，為可用，但不是支援搭配 Microsoft HoloLens 的音訊的端點。
* 藍芽啟用的手機和電腦不支援配對並用於檔案傳輸。

## <a name="unpairing-a-bluetooth-peripheral"></a>配對的藍牙周邊
1. 從 [開始] 功能表中，開啟**設定**應用程式
2. 移至**裝置**
3. 開啟藍芽無線電，如果它已關閉
4. 可用的藍芽裝置清單中尋找您的裝置
5. 從清單中選取您的裝置，然後選取**移除**按鈕

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>停用 Microsoft HoloLens 上的藍牙

這會關閉 藍芽無線電 RF 元件，並停用 Microsoft HoloLens 上的所有藍芽功能。
1. 從 [開始] 功能表中，開啟**設定**應用程式
2. 移至**裝置**
3. 將滑動軸參數移動到 「 關閉 」 位置藍芽
