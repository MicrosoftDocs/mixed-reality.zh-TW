---
title: 使用 Windows Mixed Reality 模擬器
description: Windows Mixed Reality 模擬器可讓您在電腦上測試混合現實應用程式, 而不需要 Windows Mixed Reality 沉浸式頭戴式裝置。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, 模擬器, 測試
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580696"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>使用 Windows Mixed Reality 模擬器

Windows Mixed Reality 模擬器可讓您在電腦上測試混合現實應用程式, 而不需要 Windows Mixed Reality 沉浸式頭戴式裝置。 從 Windows 10 建立者更新開始提供。 [模擬器與 HoloLens 模擬器](using-the-hololens-emulator.md)類似, 但模擬器不會使用虛擬機器。 在模擬器中執行的應用程式會在您的 Windows 10 desktop 使用者會話中執行, 就像是使用沉浸式耳機一樣。 在沉浸式耳機上, 感應器通常會讀取的人力和環境輸入, 會改為使用鍵盤、滑鼠或 Xbox 控制器來模擬。 應用程式不需要修改就可以在模擬器中執行, 也不知道它們不會在沉浸式頭戴式裝置上運作。

## <a name="enabling-the-windows-mixed-reality-simulator"></a>啟用 Windows Mixed Reality 模擬器

1. 從設定**啟用開發人員模式**-為開發人員 > 更新和安全性 >
2. 從桌面啟動**混合現實入口網站**
3. 如果這是您第一次啟動入口網站, 您必須完成設定體驗
   1. 按一下 [**開始**使用]
   2. 按一下 [**我同意**接受合約]
   3. 按一下 **[設定以模擬 (適用于開發人員)** ], 在不使用實體裝置的情況下繼續執行安裝程式
   4. 按一下 [**設定**] 以確認您的選擇
4. 按一下混合現實入口網站左側的 [**適用于開發人員**] 按鈕
5. 將模擬切換切換為**開啟**
   * 根據預設, 啟用模擬會安裝並啟用左方模擬的 6 DOF 控制器。  在 Windows 10 5 月2019更新之前, 安裝模擬的 6 DOF 控制器需要系統管理員許可權。  您必須接受 [使用者帳戶控制] 對話方塊 (如果有出現的話)。

您現在應該使用模擬來執行!

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>將應用程式部署到混合現實模擬器

由於模擬器會在沒有虛擬機器的本機電腦上執行, 因此您可以在進行偵錯工具時, 直接將通用 Windows 應用程式部署到**本機電腦**。

## <a name="basic-simulator-input"></a>基本模擬器輸入

控制模擬器非常類似于許多常見的3D 視頻遊戲和[HoloLens 模擬器](using-the-hololens-emulator.md)。 可用的輸入選項包括使用鍵盤、滑鼠或 Xbox 控制器。

您可以藉由將模擬使用者的動作導向沉浸式耳機來控制模擬器。 您的動作會移動模擬的使用者, 並與回應在沉浸式頭戴式裝置上的應用程式互動。
* **向前走、向後走、向左走和向右走** - 使用鍵盤上的 W、A、S 和 D 鍵或 Xbox 控制器上的左搖桿。
* **向上看、向下看、向左看和向右看** - 按一下並拖曳滑鼠、使用鍵盤上的方向鍵或 Xbox 控制器上的右搖桿。
* **動作按鈕按下控制器**-以滑鼠右鍵按一下滑鼠, 在鍵盤上按下 enter 鍵, 或使用 Xbox 控制器上的 [A] 按鈕。
* [**首頁] 按鈕按下 [控制器**]-按下鍵盤上的 Windows 鍵或 F2 鍵, 或按 Xbox 控制器上的 B 按鈕。
* **控制器移動以進行滾動**-按住 ALT 鍵, 按住滑鼠右鍵, 然後向上/向下拖曳滑鼠, 或在 Xbox 控制器中按住右觸發程式, 然後按下向下鍵並上下移動。

## <a name="tracked-controllers"></a>追蹤的控制器

混合現實模擬器可以模擬最多兩個手持的追蹤動作控制器。 使用混合現實入口網站中的切換參數來啟用它們。 每個模擬控制器都具有:
* 空間中的位置和方向
* 首頁按鈕
* 功能表按鈕
* [抓握] 按鈕
* 觸控板
* 上下
* 電池音量

## <a name="see-also"></a>另請參閱
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [Advanced Mixed Reality 模擬器輸入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Unity 中的空間對應](spatial-mapping-in-unity.md)
* [DirectX 中的空間對應](spatial-mapping-in-directx.md)
