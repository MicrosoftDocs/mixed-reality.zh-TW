---
title: 入門教學課程 - 9。 使用語音命令
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0b9771d9569d100a354af96a34cd20ef2a3d7c4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376590"
---
# <a name="9-using-speech-commands"></a>9.使用語音命令

## <a name="overview"></a>概觀

在本教學課程中，您將了解如何建立語音命令，以及如何全域性地控制這些命令。 您也將了解如何控制局部語音命令，該命令會要求使用者看著控制語音命令的物件。

## <a name="objectives"></a>目標

* 了解如何建立語音命令
* 了解如何全域性和局部性地控制語音命令

## <a name="ensuring-the-microphone-capability-is-enabled"></a>確定已啟用麥克風功能

在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用麥克風功能] 呈現灰色：

![mr-learning-base](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> 當您在本教學課程系列開頭設定 Unity 時，「麥克風」功能應該在[套用 MRTK 專案設定程式設定](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings)指示期間啟用。 不過如果未啟用，請務必立即啟用。

## <a name="creating-speech-commands"></a>建立語音命令

在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，選取 [MixedRealityToolkit] > [輸入] 索引標籤，並採取下列步驟：

* 展開 [語音] 區段
* 複製 **DefaultMixedRealitySpeechCommandsProfile** 並為其指定適當的名稱，例如 _GettingStarted_MixedRealitySpeechCommandsProfile_
* 確認 [啟動行為] 已設定為 [自動啟動]

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> 如需有關如何複製 MRTK 設定檔的提示，您可以參閱[設定 MRTK 設定檔](mr-learning-base-03.md)的指示。

在 [語音] > [語音命令] 區段中，按四次 [+ 新增語音命令] 按鈕，將四個新的語音命令新增至現有語音命令的清單中，然後在 [關鍵字] 欄位中輸入下列片語：

* 啟用指標
* 啟用點選放置
* 啟用週框方塊
* 停用週框方塊

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> 如果您的電腦沒有麥克風，您可以將 KeyCode 指派給語音命令，讓您在按下對應的按鍵時觸發語音命令。

## <a name="controlling-speech-commands"></a>控制語音命令

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK] > [SDK] > [功能] > [UX] > [Prefabs] > [ToolTip] 資料夾找出工具提示 Prefab：

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-1.png)

在 [階層] 視窗中，以滑鼠右鍵按一下空的位置，然後選取 [建立空物件]，將空的物件新增至您的場景。

將物件命名為 **SpeechInputHandler_Global**，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增 **SpeechInputHandler** 元件並進行下列設定：

* **取消核取** [需要對焦] 核取方塊，如此使用者就不需要看著具有 SpeechInputHandler 元件的物件來觸發語音命令
* 從 [專案] 視窗中，將 **SpeechConfirmation Tooltip** Prefab 指派給 [語音確認工具提示 Prefab] 欄位，以在辨識到語音命令時顯示此 Prefab

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-2.png)

在 SpeechInputHandler 元件上，按三次小型 **+** 圖示，以新增三個關鍵字元素：

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-3.png)

展開 **元素 0** 並進行下列設定：

* 在 [關鍵字] 欄位中輸入**啟用指標**，以參考您在上一節中建立的啟用指標語音命令。
* 按一下小型 **+** 圖示，以新增事件
* 從 [階層] 視窗中，將 [指標] 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [GameObject] > [SetActive (bool)]，以將此函式設定為觸發事件時所要執行的動作
* 核取引數核取方塊，讓其呈現**已核取**狀態

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-4.png)

展開 **元素 1** 並進行下列設定：

* 在 [關鍵字] 欄位中輸入**啟用週邊方塊**，以參考您在上一節中建立的啟用週邊方塊命令。
* 按一下小型 **+** 圖示，以新增事件
* 從 [階層] 視窗中，將 [RoverExplorer] 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [BoundingBox] >  [bool enabled] 以在觸發事件時更新此屬性值
* 核取引數核取方塊，讓其呈現**已核取**狀態
* 按一下小型 **+** 圖示，以新增另一個事件
* 從 [階層] 視窗中，將 [RoverExplorer] 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool enabled] 以在觸發事件時更新此屬性值
* 核取引數核取方塊，讓其呈現**已核取**狀態

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-5.png)

展開 **元素 2** 並進行下列設定：

* 在 [關鍵字] 欄位中輸入**停用週邊方塊**，以參考您在上一節中建立的停用週邊方塊命令
* 按一下小型 **+** 圖示，以新增事件
* 從 [階層] 視窗中，將 [RoverExplorer] 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [BoundingBox] >  [bool enabled] 以在觸發事件時更新此屬性值
* 確認**未核取**引數核取方塊
* 按一下小型 **+** 圖示，以新增另一個事件
* 從 [階層] 視窗中，將 [RoverExplorer] 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool enabled] 以在觸發事件時更新此屬性值
* 確認**未核取**引數核取方塊

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-6.png)

在 [階層] 視窗中選取 [RoverExplorer] > **RoverAssembly** 物件，然後在 [偵測器] 視窗中使用 [新增元件] 按鈕來新增 **SpeechInputHandler** 元件，並進行以下設定：

* 確認**已核取** [需要對焦] 核取方塊，如此使用者就必須看著具有 SpeechInputHandler 元件的物件 (也就是 RoverAssembly) 來觸發語音命令
* 從 [專案] 視窗中，將 **SpeechConfirmation Tooltip** Prefab 指派給 [語音確認工具提示 Prefab] 欄位，以在辨識到語音命令時顯示此 Prefab

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-7.png)

在 SpeechInputHandler 元件上，按一下小型 **+** 圖示以新增關鍵字元素，然後展開新建立的元素，並進行下列設定：

* 在 [關鍵字] 欄位中輸入**啟用點選放置**，以參考您在上一節中建立的點選放置命令
* 按一下小型 **+** 圖示，以新增事件
* 從 [階層] 視窗中，將物件本身 (也就是相同的 **RoverAssembly** 物件) 指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [TapToPlace] > [bool enabled] 以在觸發事件時更新此屬性值
* 核取引數核取方塊，讓其呈現**已核取**狀態

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何建立語音命令，以及如何全域性地控制這些命令。 您也已了解如何控制局部語音命令，該命令會要求使用者看著控制語音命令的物件。

這同時也會結束[入門教學課程](mr-learning-base-01.md)系列。 透過這些教學課程，您已成功地使用 MRTK 從頭開始建立完整的混合實境體驗。

在接下來的兩個教學課程系列：[Azure Spatial Anchors 教學課程](mr-learning-asa-01.md)和[多使用者功能教學課程](mr-learning-sharing-01.md)中，您會先了解如何將 Azure Spatial Anchors 整合到您的專案中，以在現實世界中錨定您建立的 Rover Explorer 體驗。 然後，您將了解如何在專案中新增多使用者功能，以即時分享使用者和物件的動作。
