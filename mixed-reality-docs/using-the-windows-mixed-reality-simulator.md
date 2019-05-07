---
title: 使用 Windows Mixed Reality 模擬器
description: Windows Mixed Reality 模擬器可讓您測試您的電腦，而不需要 Windows Mixed Reality 沈浸式耳機上的混合的實境應用程式。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows 混合現實情況下，模擬器測試
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580696"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>使用 Windows Mixed Reality 模擬器

Windows Mixed Reality 模擬器可讓您測試您的電腦，而不需要 Windows Mixed Reality 沈浸式耳機上的混合的實境應用程式。 它是從 Windows 10 Creators Update。 模擬器是類似[HoloLens 模擬器](using-the-hololens-emulator.md)，不過模擬器不會使用虛擬機器。 在模擬器中執行的應用程式會執行 Windows 10 桌面的使用者工作階段，就像您使用的沈浸式耳機時它們執行的動作一樣。 通常會在沉浸式耳機感應器所讀取的人力和環境輸入是改為模擬使用您的鍵盤、 滑鼠或 Xbox 控制器。 應用程式不需要修改，才能在模擬器中執行，而且不知道它們不在沉浸式耳機上執行。

## <a name="enabling-the-windows-mixed-reality-simulator"></a>啟用 Windows Mixed Reality 模擬器

1. **啟用開發人員模式**從 設定-> 更新與安全性-> 適用於開發人員
2. 啟動**混合實境入口網站**從桌面
3. 如果這是您第一次啟動入口網站，您必須經歷了安裝經驗
   1. 按一下 **開始**
   2. 按一下 **我同意**接受授權合約
   3. 按一下 **設定為模擬 （適用於開發人員）** 繼續執行安裝程式沒有實體裝置
   4. 按一下 **設定**來確認您的選擇
4. 按一下 **適用於開發人員**混合實境入口網站左邊的按鈕
5. 若要開啟模擬切換開關**上**
   * 啟用模擬會安裝並啟用預設左模擬的 DOF 6 控制站。  之前的 Windows 10 2019 年更新，安裝模擬的 6 DOF 控制站需要系統管理員權限。  如果出現的話，您必須接受 [使用者帳戶控制] 對話方塊。

您現在應該執行的模擬 ！

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>將應用程式部署至混合實境模擬器

因為模擬器在本機電腦而不需要虛擬機器上執行，您可以只部署您的通用 Windows 應用程式**本機電腦**偵錯時。

## <a name="basic-simulator-input"></a>基本的模擬器輸入

控制模擬器是非常類似於許多常見的 3D 視訊遊戲並[HoloLens 模擬器](using-the-hololens-emulator.md)。 有可用的輸入的選項使用鍵盤、 滑鼠或 Xbox 控制器。

您可以將導向穿著沈浸式耳機的模擬使用者動作控制模擬器。 您的動作移動模擬的使用者，而且會導致回應的沉浸式耳機上的應用程式的互動。
* **上一步，向前保留，並以滑鼠右鍵**-使用 W、 A、 S 和 D 鍵盤或 Xbox 控制器上的左搖桿上的索引鍵。
* **查閱，向下、 左、 並以滑鼠右鍵**-按一下並拖曳滑鼠，使用方向鍵在鍵盤或 Xbox 控制器上正確的隨身碟上。
* **控制站上按下的動作按鈕**-按一下滑鼠右鍵，在鍵盤上按 Enter 鍵或使用 Xbox 控制器上的按鈕。
* **首頁控制器上的按下按鈕**-在鍵盤上按 Windows 鍵或 F2 鍵或按下 B 上的 Xbox 控制器。
* **控制站移動捲動**-按住 Alt 鍵，請按住滑鼠按鈕，並拖曳滑鼠，增加 / 減少，或 Xbox 控制器中按住正確的觸發程序和一個按鈕並向上和向下移動右隨身碟。

## <a name="tracked-controllers"></a>追蹤控制站

混合實境模擬器可以模擬最多兩個掌上型追蹤的動作控制站。 讓他們在混合實境入口網站中使用的切換開關。 每個模擬的控制站有：
* 位置和空間中的方向
* 首頁按鈕
* 功能表按鈕
* 調整底框的按鈕
* 觸控板
* 搖桿
* 電池電量

## <a name="see-also"></a>另請參閱
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [進階混合的實境模擬器輸入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Unity 中的空間對應](spatial-mapping-in-unity.md)
* [DirectX 中的空間對應](spatial-mapping-in-directx.md)
