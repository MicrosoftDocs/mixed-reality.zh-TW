---
title: 使用者入門教學課程-7。 建立農曆模組範例應用程式
description: 在這一課，您將結合從先前課程中學到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 3a557be91bee9b98e750ae1546ea1c4b3103298e
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555236"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. 建立農曆模組範例應用程式
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

在本教學課程中，會將多個概念與前一課結合，以建立獨特的範例體驗。 您將瞭解如何建立元件元件應用程式，讓使用者必須使用追蹤的手來挑選元件，並嘗試組合陰曆模組。 您將使用 [pressable] 按鈕來開啟和關閉放置提示、重設體驗，以及啟動農曆模組到空間中！

在未來的教學課程中，您將繼續以這項體驗為基礎，其中包含強大的多使用者使用案例，可運用 Azure 空間錨點進行空間對齊。

## <a name="objectives"></a>目標

* 結合來自先前課程的多個概念以建立獨特體驗
* 了解如何切換物件
* 使用可點按的按鈕來觸發複雜事件
* 使用 rigidbody 物理特性和力
* 探索工具提示的使用

## <a name="lunar-module-parts-overview"></a>陰曆模組元件總覽
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

在本節中，您將建立一個簡單的部分元件挑戰，使用者的目標是要將在該資料表上散佈的五個部分放在農曆模組的正確位置。

達成此目標所需採取的主要步驟如下：

1. 將 Rocket 啟動器 prefab 新增至場景
2. 啟用所有元件的物件操作
3. 新增和設定元件元件示範（腳本）元件

> [!NOTE]
> 部分元件示範（腳本）元件不是 MRTK 的一部分。 本教學課程的資產提供此說明。

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. 將 Rocket 啟動器 prefab 新增至場景

在 [專案] 視窗中，流覽至 [**資產**] > **MRTK。GettingStarted** > **Prefabs** > **RocketLauncher**資料夾，將**RocketLauncher** prefab 拖曳到 [階層] 視窗中，將它新增至您的場景，然後將它放置在適當的位置，例如：

* 轉換位置 X = 1.5、Y =-0.4、Z = 0，使其位於 waist height 的使用者右方
* 轉換旋轉 X = 0、Y = 180、Z = 0，因此體驗的主要功能會面對使用者

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. 為所有元件啟用物件操作

在 [階層] 視窗中，找出 RocketLauncher > **LunarModuleParts**物件，並選取所有**子物件**、新增**操作處理常式（腳本）** 元件和**近端互動 Grabbable （腳本）** 元件，然後設定操作處理常式（腳本），如下所示：

* 取消核取 [**允許**最大操作] 核取方塊，只允許近乎互動
* 變更**兩個右手操作類型**以**移動旋轉**，以停用調整

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> 如需提醒，使用逐步指示，瞭解如何執行物件操作，您可以參考[處理3D 物件](mrlearning-base-ch4.md#manipulating-3d-objects)的指示。

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. 新增和設定元件元件示範（腳本）元件

在仍選取所有 LunarModuleParts 子物件的情況下，新增**音訊來源**元件，然後進行設定，如下所示：

* 將適當的音訊剪輯指派給**AudioClip**欄位，例如，MRKT_Scale_Start
* 取消勾選 [**在喚醒時播放**] 核取方塊，讓音訊剪輯不會在場景載入時自動播放
* 將**空間 Blend**變更為1，以啟用空間音訊

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

在仍選取所有 LunarModuleParts 子物件的情況下，新增元件元件**示範（腳本）** 元件：

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

在 [階層] 視窗中，選取 [ **RoverEnclosure** ] 物件，並設定其 [元件元件**示範（腳本）** ] 元件，如下所示：

* 在 [**要放置的物件**] 欄位中，指派物件**本身**，在此案例中為 RoverEnclosure 物件
* 在 [**要放置的位置**] 欄位中，指派對應的**PlacementHints**物件（在此案例中為 RoverEnclosure_PlacementHint 物件）
* 在 [**工具提示物件**] 欄位中，指派對應的**工具提示**，在此案例中為 RoverEnclosure_ToolTip 物件
* 在 [**音訊來源**] 欄位中，指派物件**本身**，在此案例中為 RoverEnclosure 物件

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

針對每個其他 LunarModuleParts 子物件**重複**，亦即 FuelTank、EnergyCell、DockingPortal 和 ExternalSensor。

如果您現在進入遊戲模式，並將「物件」放在靠近其對應的「位置」，您會注意到：

* 物件將會貼齊位置，並在 LunarModule 物件下成為父代，使其成為陰曆模組的一部分
* 物件上的音訊來源會在物件的位置播放指派的音訊剪輯
* 對應的工具提示物件將會隱藏

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> 如需有關如何使用編輯器內輸入模擬的提醒，您可以參考[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用編輯器內的手寫輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。

## <a name="configuring-the-lunar-module"></a>設定登月小艇

在本節中，您會將其他功能新增至 Rocket 啟動器應用程式，讓使用者可以：

* 與陰曆模組互動
* 將農曆模組啟動到空間中，並在啟動時播放音效
* 重設應用程式，讓陰曆模組和所有元件都放回其原始位置
* 隱藏放置提示，使部分元件的挑戰變得更困難。

達成此目標所需採取的主要步驟如下：

1. 啟用物件操作
2. 啟用物理
3. 新增音訊來源元件
4. 新增和設定啟動陰曆模組（腳本）元件
5. 新增和設定切換位置提示（腳本）元件

> [!NOTE]
> 啟動陰曆模組（腳本）元件和切換放置提示（腳本）元件不是 MRTK 的一部分。 這是本教學課程的資產所提供的。

### <a name="1-enable-object-manipulation"></a>1. 啟用物件操作

在 [階層] 視窗中，選取 RocketLauncher > **LunarModule**物件、新增**操作處理常式（腳本）** 元件和**近乎互動 Grabbable （腳本）** 元件，然後設定操作處理常式（腳本），如下所示：

* 取消核取 [**允許**最大操作] 核取方塊，只允許近乎互動
* 變更**兩個右手操作類型**以移動旋轉，以停用調整

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. 啟用物理

在仍選取 RocketLauncher > **LunarModule**物件的情況下，新增**Rigidbody**元件，然後進行設定，如下所示：

* 取消核取 [**使用重心**] 核取方塊，讓陰曆模組不會受到引力的影響
* 勾選 [**是運動學**] 核取方塊，讓陰曆模組一開始不會受到 physic 強制影響

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. 新增音訊來源元件

在仍選取 RocketLauncher > **LunarModule**物件的情況下，新增**音訊來源**元件，然後進行設定，如下所示：

* 將**空間 Blend**變更為1以啟用空間音訊

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. 新增和設定啟動陰曆模組（腳本）元件

在仍選取 RocketLauncher > **LunarModule**物件的情況下，新增 [**啟動陰曆模組（腳本）** ] 元件，然後進行設定，如下所示：

* 變更**天生**值，讓陰曆模組在啟動時正常運作，例如，到0.01

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. 新增和設定切換位置提示（腳本）元件

在仍選取 RocketLauncher > **LunarModule**物件的情況下，新增**切換位置提示（腳本）** 元件，然後進行設定，如下所示：

* 將 [遊戲物件陣列**大小**] 屬性設定為5
* 將每個 RocketLauncher > LunarModule > **PlacementHints**物件的**子物件**指派給遊戲物件陣列中的**元素**欄位：

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>設定 [啟動] 按鈕

在 階層 視窗中，選取 RocketLauncher > 按鈕 > **LaunchButton**物件，然後在  **Pressable 按鈕（腳本）** 元件上，建立已按下的新**按鈕（）** 事件、設定**LunarModule**物件以接收事件，並將**LaunchLunarModule**定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> 如需如何執行事件的提醒，您可以參考[手追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。

在 RocketLauncher > 按鈕 > 仍然選取 [ **LaunchButton**物件]，在 [ **Pressable] 按鈕（腳本）** 元件上，建立已**按下的新按鈕（）** 事件、設定**LunarModule**物件以接收事件、將**spatialize**定義為要觸發的動作，以及將適當的音訊剪輯指派給**音訊剪輯**欄位，例如 MRTK_Gem 的音訊剪輯：

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

在 RocketLauncher > 按鈕 > 仍然選取 [ **LaunchButton**物件]，在 [ **Pressable] 按鈕（腳本）** 元件上，建立新的**Touch End （）** 事件、設定**LunarModule**物件以接收事件，並將**LaunchLunarModule**定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

如果您現在進入遊戲模式，並按下 [啟動] 按鈕，您會聽到播放音訊剪輯，如果您將 [啟動] 按鈕按下大約一秒或更長的時間，就會看到 [陰曆] 模組啟動進入空間：

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>設定重設按鈕

在 階層 視窗中，選取 RocketLauncher > 按鈕 > **ResetButton**物件，然後在  **Pressable 按鈕（腳本）** 元件上，建立已按下的新**按鈕（）** 事件、設定**LunarModule**物件以接收事件，並將**LaunchLunarModule**定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

在 RocketLauncher > 按鈕 > 仍然選取 [ **ResetButton**物件]，在 [ **Pressable] 按鈕（腳本）** 元件上，建立已**按下的新按鈕（）** 事件、設定**RocketLauncher**物件以接收事件、將**GameObject**定義為要觸發的動作，並在 [訊息] 欄位中輸入**BroadcastMessage** ：

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> GameObject. BroadcastMessage 動作會將 ResetPlacement 訊息從 RocketLauncher 物件傳送到其所有的子物件。 具有 ResetPlacement 函式的任何子物件（定義于您加入至所有 LunarModuleParts 子物件的元件示範（Script）元件中）都會叫用 ResetPlacement 函式，該函式會重設該子物件的位置。

如果您現在進入遊戲模式，請移動部分和/或啟動農曆模組，然後按下 [重設] 按鈕，您將會看到元件和/或陰曆模組重設為其原始位置：

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>設定放置提示按鈕
<!-- TODO: Rename to 'Configuring the Hints button'-->

在 階層 視窗中，選取 RocketLauncher > 按鈕 > **HintsButton**物件，然後在  **Pressable 按鈕（腳本）** 元件上，建立已按下的新**按鈕（）** 事件、設定**LunarModule**物件以接收事件，並將**TogglePlacementHints**定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

如果您現在進入遊戲模式，您會注意到，預設會停用半透明的放置提示，但是您可以按下 [提示] 按鈕，將它們切換為開啟或關閉：

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>恭喜

您已完全設定此應用程式。 現在，您的應用程式可讓使用者完整組合陰曆模組、啟動陰曆模組、切換提示，然後將應用程式重設為重新啟動。
