---
title: 硬體配件
description: 說明可搭配 HoloLens 和 Windows Mixed Reality 使用的配件類型，以及如何設定它們。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 如何，配件，藍牙，bt，控制器，遊戲台，clicker，xbox
ms.openlocfilehash: 566d4217fb674057e1dc3d9791b247185bf61d32
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375695"
---
# <a name="hardware-accessories"></a>硬體配件

Windows Mixed Reality 裝置支援附屬應用程式。 您會使用藍牙將支援的配件配對到 HoloLens，而您可以使用 Bluetooth 或 USB，透過其連線的電腦將支援的配件配對到沉浸式耳機。

使用具有 HoloLens 的配件的兩個常見案例，就是用來做為 [空中] 手勢和 [虛擬鍵盤] 的替代方式。 為此，最常見的兩個配件是**HoloLens Clicker**和**藍牙鍵盤**。 Microsoft HoloLens 包含 Bluetooth 4.1 無線電，並支援[BLUETOOTH HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29)和[bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29)設定檔。

Windows Mixed Reality 沉浸式耳機需要在[注視](gaze-and-commit.md)和[語音](voice-input.md)以外的輸入配件。 支援的配件包括**鍵盤和滑鼠**、**遊戲台**和 **[動作控制器](motion-controllers.md)** 。

## <a name="pairing-bluetooth-accessories"></a>配對藍牙配件

將藍牙週邊設備與 Microsoft HoloLens 配對，類似于將 Bluetooth 周邊與 Windows 10 桌上型電腦或行動裝置配對：
1. 從 [開始] 功能表開啟 [**設定**] 應用程式
2. 前往 [**裝置**]
3. 若使用滑杆切換，請開啟藍牙無線電
4. 將您的藍牙裝置置於配對模式。 這會因裝置而異。 在大部分的藍牙裝置上，只要按住一或多個按鈕，即可完成此動作。
5. 等待裝置的名稱顯示在藍牙裝置清單中。 當它完成時，請選取裝置，然後選取 [**配對**] 按鈕。 如果您附近有許多藍牙裝置，您可能需要滾動到藍牙裝置清單底部，才能看到您嘗試配對的裝置。
6. 將具有輸入功能的藍牙週邊設備（例如：藍牙鍵盤）配對時，可能會顯示6位數或8位數的 pin。 請務必在周邊輸入該 pin，然後按 enter 鍵以完成與 Microsoft HoloLens 的配對。

## <a name="motion-controllers"></a>運動控制器

沉浸式頭戴式耳機支援 Windows Mixed Reality[運動控制器](motion-controllers.md)，但 HoloLens 則不支援。 這些控制器會使用沉浸式耳機中的感應器，在您的視圖中提供精確且快速的移動追蹤，這表示不需要在空間中的牆上安裝硬體。 每個控制器都會提供數個輸入方法。

![Windows Mixed Reality 運動控制器](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

HoloLens Clicker 是專為 HoloLens 建立的第一個週邊裝置，隨附于 HoloLens 開發版。 HoloLens Clicker 可讓使用者按一下並以最小的手上移動，以取代空中碰手勢。 這不是所有[手勢](gaze-and-commit.md#composite-gestures)的取代。 例如， [bloom](system-gesture.md#bloom)和重[設大小或移動](gaze-and-commit.md#composite-gestures)手勢使用手運動。 HoloLens clicker 是具有簡單按鈕的方向感應器裝置。 它會使用藍牙低功耗（BTLE）連接到 HoloLens。

![HoloLens Clicker](images/hololens-clicker-500px.jpg)

若要選取全像[投影，請看一下，然後](hologram.md)按一下。 這項作業的 clicker 方向並不重要。 若要滾動或移動，請按一下並按住，然後將 Clicker 向上/向下或向左/向右旋轉。 在滾動時，您只需要使用 +/-15 °手腕旋轉，就能達到最快的速度。 移動更多不會更快地滾動。

Clicker 內有兩個 Led：
* 白色 LED 指出裝置是否為配對（閃爍）或充電（實心）
* 琥珀色 LED 表示裝置的電池計量偏低（閃爍）或發生失敗（固態）

您可以預期2周或更長的定期使用（也就是在牆充電器上2-3 小時）。 當電池偏低時，如果您按下按鈕或從睡眠狀態喚醒，琥珀色 LED 會在5秒的期間內閃爍10次。 如果您的 Clicker 處於極低的電池模式，琥珀色 LED 會在5秒的期間內快速閃爍。

## <a name="bluetooth-keyboards"></a>藍牙鍵盤

以英文為標準的藍牙鍵盤可以配對並用於任何可使用全像攝影鍵盤的位置。 取得品質鍵盤會產生差異，因此建議使用[Microsoft 通用](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001)可折迭鍵盤或[Microsoft Designer 藍牙桌面](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)。

## <a name="bluetooth-gamepads"></a>藍牙遊戲台

您可以使用控制器搭配應用程式和遊戲，特別啟用遊戲台支援。 遊戲台不能用來控制 HoloLens 使用者介面。

Xbox one 隨附的 xbox 無線控制器，或銷售作為 Xbox One 的配件，其特色是 Bluetooth 連線能力，可讓它們與 HoloLens 和沉浸式耳機搭配使用。 Xbox 無線控制器[必須先更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)，才能與 HoloLens 搭配使用。

其他品牌的藍牙遊戲台可能適用于 Windows Mixed Reality 裝置，但支援會因應用程式而異。

## <a name="other-bluetooth-accessories"></a>其他藍牙配件

只要周邊支援 Bluetooth HID 或 GATT 設定檔，就能夠與 HoloLens 配對。 除了鍵盤、滑鼠和 HoloLens Clicker 以外的其他 Bluetooth HID 和 GATT 裝置，可能需要 Microsoft HoloLens 上的隨附應用程式，才能完全正常運作。

不支援的週邊設備包括：
* 不支援藍牙音訊設定檔中的週邊設備。
* Bluetooth 音訊裝置（例如喇叭和耳機）可能會在 [設定] 應用程式中顯示為可用，但不支援搭配 Microsoft HoloLens 作為音訊端點使用。
* 啟用 Bluetooth 的手機和電腦不支援配對，也無法用於檔案傳輸。

## <a name="unpairing-a-bluetooth-peripheral"></a>取消配對藍牙週邊設備
1. 從 [開始] 功能表開啟 [**設定**] 應用程式
2. 前往 [**裝置**]
3. 開啟藍牙無線電（如果已關閉）
4. 在可用的藍牙裝置清單中尋找您的裝置
5. 從清單中選取您的裝置，然後選取 [**移除**] 按鈕

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>停用 Microsoft HoloLens 上的藍牙

這會關閉藍牙無線電的 RF 元件，並停用 Microsoft HoloLens 上的所有藍牙功能。
1. 從 [開始] 功能表開啟 [**設定**] 應用程式
2. 前往 [**裝置**]
3. 將 [藍牙] 的滑杆開關移至 [關閉] 位置
