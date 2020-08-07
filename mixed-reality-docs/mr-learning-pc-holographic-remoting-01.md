---
title: 電腦全像攝影遠端處理教學課程 - 1。 開始使用電腦全像攝影遠端處理
description: 完成此課程，以了解如何從電腦到 HoloLens 2 進行遠端混合實境體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/29/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4929634d70a082e835eb7bd6b5680719338a5e92
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476970"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1.開始使用電腦全像攝影遠端處理

## <a name="overview"></a>概觀

  歡迎使用 HoloLens 2 教學課程。 在這個兩部分的教學課程系列中，您將了解如何建立混合實境體驗示範，以及如何建立適用於全像攝影遠端的電腦應用程式。

   在本教學課程 ([建立混合實境體驗](mr-learning-pc-holographic-remoting-01.md)) 中，您將了解如何建立混合實境體驗。 本教學課程將示範 UI 元素、3D 模型操作、模型裁剪，以及眼球追蹤功能。

  在第二個教學課程 ([建立全像攝影遠端處理應用程式](mr-learning-pc-holographic-remoting-02.md)) 中，您將了解如何建立適用於全像攝影遠端處理的電腦應用程式。 並且隨時連線至 HoloLens 2，以提供在混合實境中視覺化 3D 內容的方法。

## <a name="objectives"></a>目標

* 匯入資產並設定場景
* 使用 UI 元素和按鈕來與全像投影互動
* 設定 3D 物件的裁剪功能
* 了解眼球追蹤的啟用工具提示

## <a name="prerequisites"></a>必要條件

* 已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦
* 基本 C# 程式設計知識
* 已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已掛接 Unity 2019.3.X，且已新增通用 Windows 平台組建支援模組

**強烈建議**先完成[使用者入門](mr-learning-base-01.md)教學課程系列或一些基本的 Unity 和 MRTK 體驗，再繼續執行。

> [!IMPORTANT]
> * 本教學課程系列的建議 Unity 版本是 Unity 2019.3.X。 這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求或建議。
> * 透過 MRTK 專案進行全像攝影遠端處理只會使用舊版 XR。 目前不支援 XR SDK。

## <a name="creating-and-preparing-the-unity-project"></a>建立和準備 Unity 專案

在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。

為此，請先遵循[初始化您的專案和第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：

1. [建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」

1. [切換組建平台](mr-learning-base-02.md#configuring-the-unity-project)

1. [匯入 TextMeshPro 基本資源](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [匯入混合實境工具組](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [設定 Unity 專案](mr-learning-base-02.md#configuring-the-unity-project)

1. [建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如「電腦全像攝影遠端處理」

然後遵循[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)指示，將場景的 MRTK 設定檔變更為 **DefaultHoloLens2ConfigurationProfile**。 將空間感知網格的顯示選項變更為**遮蔽**。

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並**匯入** [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage)。

>[!TIP]
> 如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 的指示。

匯入教學課程資產之後，您的 [專案] 視窗看起來應該會像這樣：

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a>設定和準備場景

在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.PCHolograhicRemoting] > [Prefabs] 資料夾。 按住 CTRL 鍵時，按一下下列六個 prefabs。

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* 指示
* ModelParent
* 平台

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

將這些模型從 [Prefabs] 資料夾拖放到 [階層] 視窗中。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

若要將焦點放在場景中的物件上，您可以按兩下 **ModelParent** 物件，然後再次將場景稍微縮小：

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> 如果您發現場景中的大圖示 (例如大型邊框的 'T' 圖示) 會造成干擾，您可以藉由<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切換 Gizmo</a> 到關閉位置來將其隱藏。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>設定按鈕以操作場景

在本節中，您會將指令碼新增至場景中，以建立會示範模型切換和裁剪功能基本概念的按鈕事件。

### <a name="1-configuring-the-interactable-script-component"></a>1.設定 Interactable (指令碼) 元件

在 [階層] 視窗中，展開 **ButtonParent** 物件，然後選取 **NextButton**。 在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，然後按一下 **OnClick ()+ 事件底下的**  圖示。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

在 [階層] 視窗中保持選取 **NextButton** 物件，按一下 **ButtonParent** 物件並將其從 [階層] 視窗拖曳至您剛才所新增事件的空白 [無 (物件)] 欄位，讓 ButtonParent 物件可以從此按鈕接聽按下按鈕的事件：

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

按一下相同事件的 [沒有函式] 下拉式清單。 然後選取 [ViewButtonControl]  >  [NextModel ()]，將 [NextModel ()] 函式設定為從這個按鈕引發按下按鈕事件時所觸發的動作：

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2.設定其餘按鈕

針對其餘的每個按鈕，完成上述程序，將函式指派給 **OnClick ()** 事件：

* 針對 PreviousButton 物件，指派 **ViewButtonContro**l > **PreviousModel ()** 函式。

* 針對 ClippingButton，選取 **ToggleButton**  >  **ToggleClipping ()** 函式。

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3.設定 View Button Control (指令碼) 和 Toggle Button (指令碼) 元件

現在您的按鈕已設定為示範模型切換和裁剪功能。 現在可以將 3D 模型和裁剪物件新增至指令碼。

我們提供六種不同的 3D 模型作為示範，請展開 ***ModelParentobject*** 以公開這些 3D 模型。

在 [階層] 視窗中保持選取 ButtonParent 物件，在 [偵測器] 視窗中，找出 **View Button Control (指令碼)** 元件，然後展開 **Models** 變數。

在 [大小] 欄位中，輸入您想要在場景中擁有的 3D 模型數目。 在此案例中，此值會是 6。 會建立欄位以新增新的 3D 模型。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

將 ModelParent 物件的每個子物件拖放到這些欄位。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

從 [階層] 視窗中，將 **ClippingObjects** 物件拖放至 **Toggle Button (指令碼)** 元件的 [裁剪物件] 欄位。
>[!NOTE]
>只停留在按鈕父物件。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

在 [階層] 視窗中，選取 [ClippingObjects] prefab，並在 [偵測器] 視窗中啟用以開啟裁剪物件。

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>設定裁剪物件以啟用裁剪功能

在本節中，您會將 MarsCuriosityRover 物件的子物件轉譯器新增至個別的裁剪物件，以示範 MarsCuriosityRover 模型的裁剪。

在 [階層] 視窗中，展開 **ClippingObjects** 物件，以公開您將在此專案中使用的三個不同裁剪物件。

若要設定 **ClippingSphere** 物件，請按一下該物件，然後在 [偵測器] 視窗中，找出 **Clipping Sphere (指令碼)** 元件。 在 [大小] 欄位中輸入您需要為 3D 模型新增的轉譯器數目。 在此案例中，請為 MarsCuriosityRover 子物件新增 10 個。 會建立欄位以新增轉譯器，並將 MarsCuriosityRover 物件的子模型物件拖放到這些欄位。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

遵循相同的程序，並將 MarsCuriosityRover 的子物件轉譯器新增至 **ClippingBox** 和 **ClippingPlane** 物件。

在本教學課程中，只會使用 MarsCuriosityRover 模型來示範裁剪功能。 這些模型會將裁剪功能新增至更多模型、增加轉譯器的大小，以及新增其個別的網格轉譯器。

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>設定眼球追蹤以醒目提示工具提示

在本節中，您將探索如何在專案中啟用眼球追蹤。 例如，您將會實作功能以在查看 MarsCuriosityRover 組件時醒目提示附加至其中的工具提示，並且在您移開視線時將其隱藏。

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1.識別目標物件和相關聯的工具提示

在 [階層] 視窗中，選取 [ModelParent] 物件。 展開 [MarsCuriosity] -> [Rover]，以尋找 MarsCuriosityRover 的五個主要組件：**POI-Camera**、**POI-Wheels**、**POI-Antena**、**POI-Spectrometer**、**POI-RUHF Antenna**。

* 觀察與 [階層] 視窗中 MarsCuriosityRover 組件相關聯的五個對應工具提示物件。
* 當您查看 MarsCuriosityRover 組件時，將會設定這些物件以醒目提示體驗。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2.在發生 Looking At Target () 和 On Look Away () 事件時實作

在 [階層] 視窗中，選取 [POI-Camera] 物件。 在 [偵測器] 視窗中，找出 **Eye Tracking Target (指令碼)** 元件，並且設定 **While Looking At Target ()** 和 **On Look Away ()** 事件，如下所示：

* 對 [無 (物件)] 欄位，指派 **POI-Camera ToolTip** 物件
* 從 **While Looking At Target ()** 事件的 [沒有函式] 下拉式清單中，選取 [GameObject]  >  [SetActive (bool)]。 選取其底下的**核取方塊**，將工具提示醒目提示為當您查看目標物件時所觸發的動作。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* 遵循相同的程序，然後按一下 **On Look Away ()** 事件接聽程式的 [沒有函式] 下拉式清單。 然後選取 [GameObject]  >  [SetActive (bool)]，並將 [核取方塊] 保留空白以隱藏工具提示，作為當您將視線移開目標物件時所觸發的動作。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

遵循相同的程序，並且將個別的工具提示物件指派給其相同的 **MarsCuriosityRover** 組件 **While Looking At Target ()** 和 **On Look Away ()** 事件。

若要啟用眼球追蹤，請遵循這些[指導方針](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations)。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何建立混合實境體驗，以示範 UI 元素、3D 模型操作、模型裁剪和眼球追蹤功能。 本教學課程提供您 NextButton 和 PreviousButton，可讓您探索 3D 模型檢視器體驗。 ClippingObjectButton 讓您開啟裁剪物件和體驗裁剪功能。 本教學課程也提供您一個眼球追蹤元素，讓您在體驗中醒目提示工具提示。

在下一課中，您將學習如何為電腦建立全像攝影遠端處理應用程式，以在任何時間點連線 HoloLens 2，提供一種在混合實境中將 3D 內容視覺化的方式。

[下一課：2.建立全像攝影遠端處理應用程式](mr-learning-pc-holographic-remoting-02.md)
