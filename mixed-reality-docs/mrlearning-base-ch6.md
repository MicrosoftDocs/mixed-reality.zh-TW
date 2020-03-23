---
title: 入門教學課程 - 7。 建立登月小艇應用程式範例
description: 在本課程中，您將會結合從先前課程中所學習到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031537"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7.建立登月小艇應用程式範例
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

在本教學課程中，我們會結合先前課程中的多個概念來建立獨特範例體驗。 您將了解如何建立元件組合應用程式，讓使用者必須使用追蹤的手部來挑選元件，並嘗試組合登月小艇。 您將會使用可點按的按鈕來將放置提示切換為開或關、重設體驗，以及將登月小艇發射到太空中！

在未來的教學課程中，您將以此體驗作為基礎持續建置，其中包括能運用 Azure Spatial Anchors 來進行空間對齊的強大多使用者使用案例。

## <a name="objectives"></a>目標

* 結合來自先前課程的多個概念以建立獨特體驗
* 了解如何切換物件
* 使用可點按的按鈕來觸發複雜事件
* 使用 rigidbody 物理特性和力
* 探索工具提示的使用

## <a name="lunar-module-parts-overview"></a>登月小艇組件概觀
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

在本節中，您將建立一個簡單的元件組合挑戰，其中使用者的目標是要將散佈在資料表上的五個元件放在登月小艇的正確位置上。

達成此動作所需採取的主要步驟如下：

1. 將火箭發射器的 Prefab 新增至場景
2. 為所有元件啟用物件操作
3. 新增和設定 Part Assembly Demo (指令碼) 元件

> [!NOTE]
> Part Assembly Demo (指令碼) 元件不是 MRTK 的一部分。 這是本教學課程資產隨附的元件。

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1.將火箭發射器的 Prefab 新增至場景

在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.GettingStarted]   > [Prefabs]   > [RocketLauncher]  資料夾，將 **RocketLauncher** Prefab 拖曳到 [階層] 視窗中以新增至場景，然後將其放在適當位置，例如：

* 變形位置 X = 1.5、Y =-0.4、Z = 0，使其位於使用者腰部高度的右方
* 變形旋轉 X = 0、Y = 180、Z = 0，使體驗的主要功能面對使用者

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2.為所有元件啟用物件操作

在 [階層] 視窗中，找出 RocketLauncher > **LunarModuleParts** 物件，然後選取所有**子物件**，並加入 **Manipulation Handler (指令碼)** 元件和 **Near Interaction Grabbable (指令碼)** 元件，然後設定 Manipulation Handler (指令碼)，如下所示：

* 取消核取 [允許遠端操作]  核取方塊，僅限進行近處互動
* 將**兩手操作類型**變更為「移動旋轉」  ，以停用縮放功能

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> 如需了解如何實作物件操作的提示 (包含逐步指示)，您可以參考 [操作 3D 物件](mrlearning-base-ch4.md#manipulating-3d-objects)的指示。

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3.新增和設定 Part Assembly Demo (指令碼) 元件

在仍選取所有 LunarModuleParts 子物件的情況下，新增 **Audio Source** 元件，然後進行設定，如下所示：

* 將適當的音訊片段指派給 [AudioClip]  欄位，例如 MRKT_Scale_Start
* 取消核取 [喚醒時播放]  核取方塊，讓音訊片段不會在場景載入時自動播放
* 將**空間混合**變更為 1，以啟用空間音訊

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

在仍選取所有 LunarModuleParts 子物件的情況下，新增 **Part Assembly Demo (指令碼)** 元件：

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

在 [階層] 視窗中，選取 **RoverEnclosure** 物件，並設定其 **Part Assembly Demo (指令碼)** 元件，如下所示：

* 針對 [要放置的物件]  欄位，請指派物件**本身**，在此案例中為 RoverEnclosure 物件
* 針對 [要放置的位置]  欄位，請指派對應的 **PlacementHints** 物件，在此案例中為 RoverEnclosure_PlacementHint 物件
* 針對 [工具提示物件]  欄位，請指派對應的 **ToolTip**，在此案例中為 RoverEnclosure_ToolTip 物件
* 針對 [音訊來源]  欄位，請指派物件**本身**，在此案例中為 RoverEnclosure 物件

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

針對其他每個 LunarModuleParts 子物件 (例如 FuelTank、EnergyCell、DockingPortal 和 ExternalSensor)，**重複**這些步驟。

如果您現在進入遊戲模式，並將「要放置的物件」移到靠近其對應的「位置」，您會注意到：

* 物件將會貼齊位置，並在 LunarModule 物件下成為子系，使其成為登月小艇的一部分
* 物件上的音訊來源會在物件位置上播放指派的音訊片段
* 對應的工具提示物件將會隱藏

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> 如需如何使用編輯器內的輸入模擬的提示，您可以參考 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用編輯器內的手動輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。

## <a name="configuring-the-lunar-module"></a>設定登月小艇

在本節中，您會將其他功能新增至火箭發射器應用程式，讓使用者可以：

* 與登月小艇互動
* 將登月小艇發射到太空中，並在發射時播放音效
* 重設應用程式，讓登月小艇和所有元件都放回其原本位置
* 隱藏放置提示，使元件組合的挑戰變得更困難。

達成此動作所需採取的主要步驟如下：

1. 啟用物件操作
2. 啟用物理特性
3. 新增音訊來源元件
4. 新增和設定啟動 Launch Lunar Module (指令碼) 元件
5. 新增和設定 Toggle Placement Hints (指令碼) 元件

> [!NOTE]
> Launch Lunar Module (指令碼) 元件和 Toggle Placement Hints (指令碼) 元件不是 MRTK 的一部分。 這些是本教學課程資產隨附的元件。

### <a name="1-enable-object-manipulation"></a>1.啟用物件操作

在 [階層] 視窗中，選取 RocketLauncher > **LunarModule** 物件，新增 **Manipulation Handler (指令碼)** 元件和 **Near Interaction Grabbable (指令碼)** 元件，然後設定 Manipulation Handler (指令碼)，如下所示：

* 取消核取 [允許遠端操作]  核取方塊，僅限進行近處互動
* 將**兩手操作類型**變更為「移動旋轉」，以停用縮放功能

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2.啟用物理特性

在仍選取 RocketLauncher  > **LunarModule** 物件的情況下，新增 **Rigidbody** 元件，然後依照下列方式進行設定：

* 取消核取 [使用引力]  核取方塊，讓登月小艇不會受到引力的影響
* 核取 [使用運動學]  核取方塊，讓登月小艇一開始不會受到物理力的影響

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3.新增音訊來源元件

在仍選取 RocketLauncher > **LunarModule** 物件的情況下，新增 **Audio Source** 元件，然後進行設定，如下所示：

* 將**空間混合**變更為 1，以啟用空間音訊

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4.新增和設定啟動 Launch Lunar Module (指令碼) 元件

在仍選取 RocketLauncher > **LunarModule** 物件的情況下，新增 **Launch Lunar Module (指令碼)** 元件，然後依照下列方式進行設定：

* 變更 [推力]  的值，讓登月小艇在發射時緩緩飛起，例如，變更為 0.01

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5.新增和設定 Toggle Placement Hints (指令碼) 元件

在仍選取 RocketLauncher > **LunarModule** 物件的情況下，新增 **Toggle Placement Hints (指令碼)** 元件，然後依照下列方式進行設定：

* 將遊戲物件陣列的**大小**屬性設定為 5
* 將每個 RocketLauncher > LunarModule > **PlacementHints** 物件的**子物件**指派至遊戲物件陣列中的 [元素]  欄位：

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>設定發射按鈕

在 [階層] 視窗中，選取 RocketLauncher > Buttons > **LaunchButton** 物件，然後在 **Pressable Button (指令碼)** 元件上，建立新的 **Button Pressed ()** 事件、設定 **LunarModule** 物件以接收事件，並將 **LaunchLunarModule.StartThruster** 定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> 如需有關如何實作事件的提示，您可以參閱[手部追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。

在仍選取 RocketLauncher > Buttons > **LaunchButton** 物件的情況下，於 **Pressable Button (指令碼)** 元件上建立新的 **Button Pressed ()** 事件、設定 **LunarModule** 物件以接收事件、將 **AudioSource.PlayOneShot** 定義為要觸發的動作，然後對 [音訊片段]  欄位指派合適的音訊片段，例如 MRTK_Gem 音訊片段：

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

在仍選取 RocketLauncher > Buttons > **LaunchButton**物件的情況下，於 **Pressable Button (指令碼)** 元件上建立新的 **Touch End ()** 事件、設定 **LunarModule** 物件以接收事件，並將 **LaunchLunarModule.StopThruster** 定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

如果您現在進入遊戲模式，並按下 [發射] 按鈕，您會聽到播放的音訊片段，如果您將 [發射] 按鈕按下大約一秒或更長的時間，就會看到登月小艇發射到太空中：

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>設定重設按鈕

在 [階層] 視窗中，選取 RocketLauncher > Buttons > **ResetButton** 物件，然後在 **Pressable Button (指令碼)** 元件上，建立新的 **Button Pressed ()** 事件、設定 **LunarModule** 物件以接收事件，並將 **LaunchLunarModule.ResetModule** 定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

在仍選取 RocketLauncher > Buttons > **ResetButton** 物件的情況下，於 **Pressable Button (指令碼)** 元件上建立新的 **Button Pressed ()** 事件、設定 **RocketLauncher** 以接收事件、將 **GameObject.BroadcastMessage** 定義為要觸發的動作，然後在訊息欄位中輸入 **ResetPlacement**：

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> GameObject.BroadcastMessage 動作會將 ResetPlacement 訊息從 RocketLauncher 物件傳送到其所有子物件。 在您新增至所有 LunarModuleParts 子物件的 Part Assembly Demo (指令碼) 元件中，已定義為具有 ResetPlacement 函式的任何子物件都可叫用 ResetPlacement 函式來重設該子物件的位置。

如果您現在進入遊戲模式，移動部分元件和/或發射登月小艇，然後按下 [重設] 按鈕，您將會看到元件和/或登月小艇重設至其原本位置：

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>設定放置提示按鈕
<!-- TODO: Rename to 'Configuring the Hints button'-->

在 [階層] 視窗中，選取 RocketLauncher > Buttons > **HintsButton** 物件，然後在 **Pressable Button (指令碼)** 元件上，建立新的 **Button Pressed ()** 事件、設定 **LunarModule** 物件以接收事件，並將 **TogglePlacementHints.ToggleGameObjects** 定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

如果您現在進入遊戲模式，您會注意到，半透明的放置提示已預設為停用，但是您可以按下 [提示] 按鈕，將其切換為開啟或關閉：

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>恭喜！

您已完整地設定好這個應用程式。 現在，您的應用程式可讓使用者完整組合登月小艇、發射登月小艇、切換提示，然後將應用程式重設以重新開始。
