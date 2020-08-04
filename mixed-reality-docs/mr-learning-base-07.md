---
title: 入門教學課程 - 7。 與 3D 物件互動
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: f02780a1b9421b814242727ce92311d62b5e3461
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376420"
---
# <a name="7-interacting-with-3d-objects"></a>7.與 3D 物件互動

在本教學課程中，您將了解如何對 3D 物件進行遠近操作，並限制允許的操作類型。 您也將了解如何在3D 物件周圍加入週框方塊，讓您更輕鬆地控制物件操作。

## <a name="objectives"></a>目標

* 了解如何設定3D 物件，使其能夠進行互動
* 了解如何將週框方塊加入 3D 物件

## <a name="manipulating-3d-objects"></a>操作 3D 物件

在本節中，您將加入可操作所有 Rover 零件的能力，也就是您在[將物件置放在場景中](mr-learning-base-04.md)的教學課程中，於桌面上組織的所有 Rover 零件。

達成此動作所需採取的主要步驟如下：

1. 將 Object Manipulator (指令碼) 元件新增至所有零件物件
2. 將 NearInteractionGrabbable 元件新增至所有零件物件
3. 設定 Object Manipulator (指令碼) 元件

> [!NOTE]
> 若要能夠**操作物件**，該物件必須具有下列元件：
>
> * **Collider** 元件，例如 Box Collider
> * **Object Manipulator (指令碼)** 元件
>
> 若要能夠以追蹤的手部**操作**及**抓取物件**，該物件必須具有下列元件：
>
> * **Collider** 元件，例如 Box Collider
> * **Object Manipulator (指令碼)** 元件
> * **NearInteractionGrabbable** 元件

此外，您將設定 Rover Explorer，讓您可以將 Rover 零件放在 Rover 上，使其成為完整的 Rover 組件。

在 [階層] 視窗中，展開 RoverExplorer > **RoverParts** 物件，並選取其所有子 Rover 零件物件和 **RoverAssembly** 物件，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕將下列元件新增至所有選取的物件：

* **Object Manipulator (指令碼)** 元件
* **NearInteractionGrabbable** 元件
* **Part Assembly Controller (指令碼)** 元件

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> 若要選取非連續的多個物件，請按住 CTRL 鍵並使用滑鼠選取任何物件。

> [!NOTE]
> 基於本教學課程的目的，碰撞器 (Collider) 已新增至 Rover 零件。 若要深入了解碰撞器，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞器 (Collider)</a> 文件。

> [!NOTE]
> Part Assembly Controller (指令碼) 不是 MRTK 的一部分，但已包含在教學課程資產中。

在仍選取所有 Rover 零件物件和 RoverAssembly 物件的情況下，在 [偵測器] 視窗中，設定 **Object Manipulator (指令碼)** 元件，如下所示：

* 從 [兩手操作類型] 下拉式清單中，取消核取 [縮放]，只啟用 [移動] 和 [選轉]

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> 此時，您已針對所有 Rover 零件物件和 RoverAssembly 物件啟用物件操作。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK] > [SDK] > [StandardAssets] > [Audio] 資料夾，以找出音訊剪輯：

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

在 [階層] 視窗中，重新選取所有 **Rover 零件物件**，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增**音訊來源**元件，並進行以下設定：

* 將 **MRTK_Scale_Start** 音訊剪輯指派給 **AudioClip** 欄位
* 取消核取 [喚醒時播放] 核取方塊
* 將 [空間混合] 變更為 1

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

在 [階層] 視窗中，展開 RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** 物件，以顯示所有位置提示物件，選取第一個 Rover 零件 RoverParts > **Camera_Part**，然後設定 **Part Assembly Controller (指令碼)** 元件，如下所示：

* 將 **Camera_PlacementHint** 物件指派給 [要放置的位置] 欄位

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

針對其餘每個 Rover 零件物件和 RoverAssembly 物件**重複**此步驟，以設定 **Part Assembly Controller (指令碼)** 元件，如下所示：

* 針對 **Generator_Part**，將 **Generator_PlacementHint** 物件指派給 [要放置的位置] 欄位
* 針對 **Lights_Part**，將 **Lights_PlacementHint** 物件指派給 [要放置的位置] 欄位
* 針對 **UHFAntenna_Part**，將 **UHFAntenna_PlacementHint** 物件指派給 [要放置的位置] 欄位
* 針對 **Spectrometer_Part**，將 **Spectrometer_PlacementHint** 物件指派給 [要放置的位置] 欄位
* 針對 **RoverAssembly**，將物件本身 (也就是相同的 **RoverAssembly** 物件) 指派給 [要放置的位置] 欄位

在 [階層] 視窗中，選取 [RoverExplorer] > [按鈕] > [重設] 按鈕物件，然後在 [偵測器] 視窗中，設定可互動的 **OnClick ()** 事件，如下所示：

* 將 **RoverAssembly** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [PartAssemblyController] > [ResetPlacement ()]，以將此函式設定為觸發事件時所要執行的動作

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

如果您現在進入遊戲模式，您可以使用近或遠的互動來將 Rover 零件放在 Rover 上。 零件會在接近對應的放置提示時，貼齊位置並成為 Rover 的一部分。 若要重設放置位置，您可以按下 [重設] 按鈕：

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

若要深入了解 Object Manipulator (物件操作工具) 元件及其相關聯的屬性，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的 [Object Manipulator (物件操作工具)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) 指南。

## <a name="adding-bounding-boxes"></a>新增週框方塊

周框方塊藉由提供可用於縮放和旋轉的控點，讓您能夠更輕鬆且更直覺地以單手操作可遠近互動的物件。

在此範例中，您會將週框方塊新增至 RoverExplorer 物件，以便您在整個體驗中可以輕鬆地移動、旋轉和縮放。 此外，您將設定「功能表」，讓您可以開啟和關閉週框方塊。

在 [階層] 視窗中，選取 **RoverExplorer** 物件，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增下列元件：

* **BoundingBox** 元件
* **Object Manipulator (指令碼)** 元件

然後**取消核取**這兩個元件旁的核取方塊，使其預設為**停用**：

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> 週框方塊視覺效果會在執行階段中建立，因此在您進入遊戲模式之前看不到該效果。

> [!NOTE]
> BoundingBox 元件將會在執行階段尚自動新增 NearInteractionGrabbable 元件。 因此，我們不需要新增此元件，就能以追蹤的手部抓取框起來的物件。

在 [階層] 視窗中，展開功能表 > **ButtonCollection** 物件以顯示四個按鈕，並將第三個按鈕重新命名為 **BoundingBox_Enable**，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件，如下所示：

* 將 [主要標籤文字] 變更為 [啟用]
* 將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [BoundingBox] >  [bool Enabled] 以在觸發事件時更新此屬性值
* 確認**已核取**引數核取方塊
* 按一下小型 **+** 圖示，以新增另一個事件
* 將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool Enabled] 以在觸發事件時更新此屬性值
* 確認**已核取**引數核取方塊
* 將**圖示**保留為 [具有週框的立方體] 圖示

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

將第四個 (也就是最後一個) 按鈕重新命名為 **BoundingBox_Disable**，然後在 [偵測器] 視窗中，設定 **Button Config Helper (Script)** 元件，如下所示：

* 將 [主要標籤文字] 變更為 [停用]
* 將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [BoundingBox] >  [bool Enabled] 以在觸發事件時更新此屬性值
* 確認**未核取**引數核取方塊
* 按一下小型 **+** 圖示，以新增另一個事件
* 將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool Enabled] 以在觸發事件時更新此屬性值
* 確認**未核取**引數核取方塊
* 將**圖示**變更為 [具有週框的立方體] 圖示

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

如果您現在進入遊戲模式，並按一下 [啟用] 按鈕來啟用週框方塊，您就可以使用近或遠的互動來移動、旋轉和縮放週框方塊，然後使用 [停用] 按鈕再次停用週框方塊：

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

若要深入了解 Bounding Box 元件和其相關聯的屬性，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[周框方塊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)指南。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何啟用 3D 物件的遠近操作，以及如何限制允許的操作類型。 您也了解如何在 3D 物件周圍加入週框方塊，讓您更輕鬆地控制物件操作。

[下一個教學課程：8.使用眼球追蹤](mr-learning-base-08.md)
