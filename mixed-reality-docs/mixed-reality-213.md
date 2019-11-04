---
title: MR 輸入213
description: 遵循此編碼教學課程，使用 Unity、Visual Studio 和沉浸式耳機來瞭解動作控制器的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、沉浸式、運動控制器、學院、教學課程
ms.openlocfilehash: e2199c3afed21f9396ed84f71093a8b2fb3bb23b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438543"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。

<br>

# <a name="mr-input-213-motion-controllers"></a>MR 輸入213：動作控制器

混合現實世界中的運動控制器會加入另一個層級的互動。 有了[動作控制器](motion-controllers.md)，我們可以透過更自然的方式直接與物件互動，類似于真實生活中的實體互動，在您的應用程式體驗中增加深度和取悅。

在 MR 輸入213中，我們將建立簡單的空間繪製體驗，以探索動作控制器的輸入事件。 使用此應用程式，使用者可以在具有各種類型之筆刷和色彩的三維空間中繪製。

## <a name="topics-covered-in-this-tutorial"></a>本教學課程涵蓋的主題

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**控制器視覺效果**|**控制器輸入事件**|**自訂控制器和 UI**|
|瞭解如何在 Unity 的遊戲模式和執行時間中呈現移動控制器模型。|瞭解不同類型的按鈕事件及其應用程式。|瞭解如何在控制器上覆迭 UI 元素，或將其完全自訂。|

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 輸入213：動作控制器</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

請參閱[此頁面](install-the-tools.md)上的沉浸式耳機安裝檢查清單。

* 本教學課程需要[Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>專案檔案

* [下載](https://github.com/Microsoft/MixedReality213/archive/master.zip)專案所需的檔案，並將檔案解壓縮到桌面。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼，可以[在 GitHub 上](https://github.com/Microsoft/MixedReality213)取得。

## <a name="unity-setup"></a>Unity 設定

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>目標

* 將 Unity 優化以進行 Windows Mixed Reality 開發
* 設定混合現實攝影機
* 設定環境

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 [**開啟**]。
* 流覽至您的桌面，並尋找您先前 unarchived 的**MixedReality213 主**資料夾。
* 按一下 [選擇資料夾]。
* 一旦 Unity 完成載入專案檔之後，您就可以看到 Unity 編輯器。
* 在 Unity 中，選取 [檔案] **> [組建設定**]。

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* 選取 [**平臺**] 清單中的 [**通用 Windows 平臺**]，然後按一下 [**切換平臺**] 按鈕。
* 將目標裝置設定為**任何裝置**
* 將組建類型設定為**D3D**
* 將 SDK 設定為**最新安裝**
* 檢查**Unity C#專案**
    * 這可讓您修改 Visual Studio 專案中的指令檔，而不需要重建 Unity 專案。
* 按一下 [**玩家設定**]。
* 在 [偵測**器**] 面板中，向下流覽至底部
* 在 [XR 設定] 中，檢查**支援的虛擬實境**
* 在 [虛擬實境 Sdk] 底下，選取 [ **Windows Mixed Reality** ]

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* 關閉 [**組建設定**] 視窗。

### <a name="project-structure"></a>專案結構

本教學課程使用 **[混合的現實工具組-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 。 您可以在[此頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)上找到版本。

![ProjectStructure](images/mr213-projectstructure-650px.png)

**您參考的已完成場景**

* 您會在 [**場景**] 資料夾下找到兩個已完成的 Unity 場景。
    * **MixedReality213**：具有單一筆刷的已完成場景
    * **MixedReality213Advanced**：已完成的場景，適用于具有多筆刷的先進設計

**教學課程的新場景設定**

* 在 Unity 中，按一下 [檔案] **> 新場景**
* 刪除**主要相機**和**方向光線**
* 從 [**專案] 面板**中，搜尋下列 prefabs，並將其拖曳至 [階層 **] 面板：**
    * 資產/HoloToolkit/輸入/Prefabs/**MixedRealityCamera**
    * 資產/AppPrefabs/**環境**

    ![相機和環境](images/mr213-cameraenvironment-300px.jpg)

* 混合現實工具組中有兩個相機 prefabs：
    * **MixedRealityCamera. prefab**：僅限相機
    * **MixedRealityCameraParent. prefab**：攝影機 + Teleportation + 界限
    * 在本教學課程中，我們將使用**MixedRealityCamera**而不 teleportation 功能。 因此，我們新增了簡單的**環境**prefab，其中包含基本的樓層，讓使用者感覺更接地。
    * 若要深入瞭解具有**MixedRealityCameraParent**的 teleportation，請參閱[Advanced design-teleportation 和 locomotion](#advanced-design---teleportation-and-locomotion)

**Skybox 設定**

* 按一下 [**視窗] > 光源 > 設定**
* 按一下 [ **Skybox 材質] 欄位**右側的圓形
* 輸入 ' 灰階 ' 並選取**SkyboxGray** （資產/AppPrefabs/支援/材質/SkyboxGray）

    ![設定 skybox](images/mr123-skyboxsetting-400px.jpg)

* 檢查**Skybox**選項以查看指派的灰色漸層 Skybox

    ![切換 skybox 選項](images/mr213-skyboxcheck-400px.jpg)

* 具有 [MixedRealityCamera]、[環境] 和 [灰色] skybox 的場景看起來會像這樣。

    ![MixedReality213 環境](images/mr213-environment-600px.jpg)

* 按一下 [檔案] **> 另存場景**
* 以任何名稱**將場景儲存**在幕後資料夾下

## <a name="chapter-1---controller-visualization"></a>第1章-控制器視覺效果

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>目標

* 瞭解如何在 Unity 的遊戲模式和執行時間中轉譯運動控制器模型。

Windows Mixed Reality 提供控制控制器視覺效果的動畫控制器模型。 您可以針對應用程式中的控制器視覺效果採取幾種方法：

* 預設-在不修改的情況下使用預設控制器
* 混合式使用預設控制器，但自訂其部分元素或覆迭 UI 元件
* 取代-針對控制器使用您自己的自訂3D 模型

在本章中，我們將瞭解這些控制器自訂的範例。

### <a name="instructions"></a>指示

* 在 [**專案**] 面板的 [搜尋] 方塊中，輸入**MotionControllers** 。 您也可以在 [資產]/[HoloToolkit]/[輸入/Prefabs/] 下找到它。
* 將 [ **MotionControllers** prefab] 拖曳至 [階層 **] 面板。**
* 按一下 [階層 **] 面板中的 [** **MotionControllers** ] prefab。

**MotionControllers prefab**

**MotionControllers** Prefab 具有**MotionControllerVisualizer**腳本，可提供替代控制器模型的位置。 如果您指派自己的自訂3D 模型，例如手或寶劍，並勾選 [一律使用替代的左/右模型]，則會看到它們，而不是預設模型。 我們將在第4章使用此位置，以筆刷取代控制器模型。

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**螢幕**

* 在 [偵測**器**] 面板中，按兩下 [ **MotionControllerVisualizer**腳本] 以查看 Visual Studio 中的程式碼

**MotionControllerVisualizer 腳本**

**MotionControllerVisualizer**和**MotionControllerInfo**類別提供存取 & 修改預設控制器模型的方法。 **MotionControllerVisualizer**訂閱 Unity 的**InteractionSourceDetected**事件，並在找到時自動具現化控制器模型。

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

控制器模型是根據[glTF 規格](https://github.com/KhronosGroup/glTF)來傳遞。 這種格式的建立是為了提供通用格式，同時改善傳輸和解除包裝3D 資產的處理常式。 在此情況下，我們需要在執行時間抓取和載入控制器模型，因為我們想要讓使用者的體驗盡可能順暢，而且不保證使用者可能會使用哪個版本的動作控制器。 這個課程透過混合現實工具組，使用 Khronos 群組的[UnityGLTF 專案](https://github.com/KhronosGroup/UnityGLTF)版本。

一旦傳遞了控制器，腳本就可以使用**MotionControllerInfo**來尋找特定控制器元素的轉換，讓它們可以正確地定位。

在後面的章節中，我們將學習如何使用這些腳本將 UI 元素附加至控制器。

*在某些腳本中，您會發現含有 #if 的程式碼區塊 **！UNITY_EDITOR**或**UNITY_WSA**。只有當您部署到 Windows 時，這些程式碼區塊才會在 UWP 執行時間上執行。這是因為 Unity editor 和 UWP 應用程式執行時間所使用的一組 Api 不同。*

* **儲存**場景，然後按一下 [**播放**] 按鈕。

您將能夠在耳機中看到含有運動控制器的場景。 您可以查看按鈕點擊、操縱杆移動和觸控板觸控反白顯示的詳細動畫。

![MR213_Controller 視覺效果預設](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>第2章-將 UI 元素附加至控制器

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>目標

* 瞭解動作控制器的元素
* 瞭解如何將物件附加至控制器的特定部分

在本章中，您將瞭解如何將使用者介面專案新增至控制器，讓使用者隨時都能輕鬆地存取和操作。 您也將瞭解如何使用觸控板輸入來新增簡單的色彩選擇器 UI。

### <a name="instructions"></a>指示

* 在 [**專案**] 面板中，搜尋**MotionControllerInfo**腳本。
* 在搜尋結果中，按兩下 [ **MotionControllerInfo**腳本] 以查看 Visual Studio 中的程式碼。

**MotionControllerInfo 腳本**

第一個步驟是選擇您要讓 UI 附加到哪個控制器的元素。 這些元素是在**MotionControllerInfo.cs**的**ControllerElementEnum**中定義。

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **起始**
* **功能表**
* **領會**
* **上下**
* **請**
* **觸控板**
* **指標姿勢**–此元素表示控制器指向正向方向的提示。

**螢幕**

* 在 [**專案**] 面板中，搜尋**AttachToController**腳本。
* 在搜尋結果中，按兩下 [ **AttachToController**腳本] 以查看 Visual Studio 中的程式碼。

**AttachToController 腳本**

**AttachToController**腳本提供簡單的方法，將任何物件附加至指定的控制器慣用手和元素。

在**AttachElementToController （）** 中，

* 使用**MotionControllerInfo. 慣用手**檢查慣用手
* 使用**MotionControllerInfo. TryGetElement （）** 取得控制器的特定元素
* 從控制器模型中抓取專案的轉換之後，父系物件下的物件，並將物件的本機位置 & 旋轉為零。

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

使用**AttachToController**腳本最簡單的方式是從它繼承，如同我們在 ColorPickerWheel 的情況下所做的一樣 **。** 只要覆寫**OnAttachToController**和**OnDetatchFromController**函式，即可在偵測到或中斷連接控制器時執行您的設定/細目。

**螢幕**

* 在 [**專案**] 面板的 [搜尋] 方塊中，輸入**ColorPickerWheel**。 您也可以在 [資產/AppPrefabs/] 下找到它。
* 將 [ **ColorPickerWheel** prefab] 拖曳**至 [階層**] 面板。
* 按一下 [階層 **] 面板中的 [** **ColorPickerWheel** ] prefab。
* 在 [偵測**器**] 面板中，按兩下 [ **ColorPickerWheel**腳本] 以查看 Visual Studio 中的程式碼。

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel 腳本**

由於**ColorPickerWheel**會繼承**AttachToController**，因此它會在 [偵測**器**] 面板中顯示**慣用手**和**元素**。 我們會將 UI 附加至左側控制器上的觸控板元素。

![ColorPickerWheel 腳本](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel**會覆寫**OnAttachToController**和**OnDetatchFromController** ，以訂閱輸入事件，將在下一章使用觸控板輸入進行色彩選取。

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **儲存**場景，然後按一下 [**播放**] 按鈕。

**將物件附加至控制器的替代方法**

我們建議您的腳本繼承自**AttachToController**並覆寫**OnAttachToController**。 不過，這可能不一定可行。 另一個替代方式是使用它做為獨立元件。 當您想要將現有的 prefab 附加至控制器，但未重構腳本時，這會很有用。 在執行任何安裝程式之前，請先讓您的類別等待 IsAttached 設定為 true。 最簡單的方法是使用「開始」的協同程式。

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>第3章-使用觸控板輸入

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>目標

* 瞭解如何取得觸控板輸入資料事件
* 瞭解如何針對您的應用程式體驗使用觸控板軸位置資訊

### <a name="instructions"></a>指示

* **在 [階層**] 面板中，按一下 [ **ColorPickerWheel** ]
* 在 偵測**器** 面板的  **Animatior** 底下，按兩下  **ColorPickerWheelController**
* 您將能夠看到開啟的 [ **Animator** ] 索引標籤

**使用 Unity 的動畫控制器顯示/隱藏 UI**

為了顯示和隱藏具有動畫的**ColorPickerWheel** UI，我們使用[Unity 的動畫系統](https://docs.unity3d.com/Manual/AnimationOverview.html)。 將**ColorPickerWheel**的**Visible**屬性設定為 true 或 False 觸發程式會**顯示**和**隱藏**動畫觸發程式。 [**顯示**] 和 [**隱藏**] 參數定義于**ColorPickerWheelController**動畫控制器中。

![Unity 動畫控制器](images/mr123-animationcontroller-550px.jpg)

**螢幕**

* **在 [階層**] 面板中，選取 [ **ColorPickerWheel** prefab]
* 在 [偵測**器**] 面板中，按兩下 [ **ColorPickerWheel**腳本] 以查看 Visual Studio 中的程式碼

**ColorPickerWheel 腳本**

**ColorPickerWheel**會訂閱 Unity 的**InteractionSourceUpdated**事件，以接聽觸控板事件。

在**InteractionSourceUpdated （）** 中，腳本會先檢查以確定它：

* 實際上是一種觸控板事件（obj. state。**touchpadTouched**）
* 源自于左側控制器（.obj **）。慣用手**）

如果兩者皆為 true，則為觸控板位置（obj. state。**touchpadPosition**）指派給**selectorPosition**。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

在**Update （）** 中，根據**visible**屬性，它會觸發在色彩選擇器的 animator 元件中顯示和隱藏動畫觸發程式

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

在**Update （）** 中， **selectorPosition**是用來將光線轉換成色輪的網格碰撞器，這會傳回 UV 位置。 接著可以使用這個位置來尋找色輪材質的圖元座標和色彩值。 此值可透過**SelectedColor**屬性存取其他腳本。

![色彩選擇器滾輪 Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>第4章-覆寫控制器模型

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>目標

* 瞭解如何使用自訂3D 模型覆寫控制器模型。

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>指示

* 按一下 **[階層**] 面板中的 [ **MotionControllers** ]。
* 按一下 [**替代右控制器**] 欄位右側的圓形。
* 輸入 **' BrushController**'，然後從結果中選取 prefab。 您可以在 [資產]/[AppPrefabs]/[**BrushController**] 下找到它。
* 勾選 [**一律使用替代的右模型**]

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**[階層] 面板中**不需要包含**BrushController** prefab。 不過，若要簽出其子元件：

* 在 [**專案**] 面板中輸入**BrushController** ，並將 [ **BrushController** prefab] 拖曳至 [階層 **] 面板。**

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

您會在**BrushController**中找到**Tip**元件。 我們將使用其轉換來啟動/停止繪製線條。

* 從 [階層 **] 面板中**刪除**BrushController** 。
* **儲存**場景，然後按一下 [**播放**] 按鈕。 您將能夠看到筆刷模型已取代右手邊的運動控制器。

## <a name="chapter-5---painting-with-select-input"></a>第5章-使用選取輸入進行繪製

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>目標

* 瞭解如何使用 [選取] 按鈕事件來啟動和停止線條繪圖

### <a name="instructions"></a>指示

* 在 [**專案**] 面板中搜尋**BrushController** prefab。
* 在 [偵測**器**] 面板中，按兩下 [ **BrushController**腳本] 以查看中的程式碼 Visual Studio

**BrushController 腳本**

**BrushController**會訂閱 InteractionManager 的**InteractionSourcePressed**和**InteractionSourceReleased**事件。 觸發**InteractionSourcePressed**事件時，筆刷的**Draw**屬性會設定為 true;觸發**InteractionSourceReleased**事件時，筆刷的**Draw**屬性會設定為 false。

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

當**Draw**設定為 true 時，筆刷會在具現化的 Unity **LineRenderer**中產生點。 這個 prefab 的參考會保留在筆刷的 [**筆劃 prefab** ] 欄位中。

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

若要從色彩選擇器滾輪 UI 使用目前選取的色彩， **BrushController**必須要有**ColorPickerWheel**物件的參考。 由於**BrushController** prefab 會在執行時間具現化為取代控制器，因此必須在執行時間設定場景中物件的任何參考。 在此情況下，我們會使用**GameObject FindObjectOfType**來尋找**ColorPickerWheel**：

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **儲存**場景，然後按一下 [**播放**] 按鈕。 您可以使用右側控制器上的 [選取] 按鈕繪製線條並繪製。

## <a name="chapter-6---object-spawning-with-select-input"></a>第6章-具有選取輸入的物件產生

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>目標

* 瞭解如何使用 [選取] 和 [抓住] 按鈕輸入事件
* 瞭解如何具現化物件

### <a name="instructions"></a>指示

* 在 [**專案**] 面板的 [搜尋] 方塊中，輸入**ObjectSpawner** 。 您也可以在 [資產]/[AppPrefabs/] 下找到它。
* 將 [ **ObjectSpawner** prefab] 拖曳至 [階層 **] 面板。**
* 按一下 **[階層**] 面板中的 [ **ObjectSpawner** ]。
* **ObjectSpawner**有一個名為**Color Source**的欄位。
* 從 [階層 **] 面板中**，將**ColorPickerWheel**參考拖曳到此欄位中。

    ![物件 Spawner 偵測器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* 按一下 [階層 **] 面板中的 [** **ObjectSpawner** ] prefab。
* 在 [偵測**器**] 面板中，按兩下 [ **ObjectSpawner**腳本] 以查看 Visual Studio 中的程式碼。

**ObjectSpawner 腳本**

**ObjectSpawner**會將基本網格（cube、球體、圓柱）的複本具現化到空間中。 偵測到**InteractionSourcePressed**時，它會檢查慣用手，如果是**InteractionSourcePressType**或**InteractionSourcePressType，請選取**[事件]。

對於**抓住**事件，它會遞增目前網格類型的索引（球體、cube、圓柱）

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

針對**Select**事件，在**SpawnObject （）** 中，會具現化新的物件，並將其取消父代併發行至世界。

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner**會使用**ColorPickerWheel**來設定顯示物件材質的色彩。 系統會將此材質的實例提供給產生的物件，使其保留其色彩。

* **儲存**場景，然後按一下 [**播放**] 按鈕。

您將能夠使用 [抓住] 按鈕來變更物件，並使用 [選取] 按鈕來產生物件。

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>建立應用程式並將其部署至混合現實入口網站

* 在 Unity 中，選取 [檔案] **> [組建設定**]。
* 按一下 [新增] [**開啟場景**]，將目前場景新增至**組建中的場景**。
* 按一下 [建置]。
* 建立名為 "App" 的**新資料夾**。
* 按一下 [**應用程式**] 資料夾。
* 按一下 [選擇資料夾]。
* 當 Unity 完成時，將會出現 [檔案瀏覽器] 視窗。
* 開啟**應用程式**資料夾。
* 按兩下 [ **YourSceneName** Visual Studio 方案檔]。
* 使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**X64**。
* 按一下 [裝置] 按鈕旁邊的下拉式箭號，然後選取 [**本機電腦**]。
* 按一下功能表中的 [ **Debug-> 啟動但不進行調試**]，或按**Ctrl + F5**。

現在，應用程式已建立並安裝在混合現實入口網站中。 您可以透過混合式現實入口網站中的 [開始] 功能表重新開機它。

## <a name="advanced-design---brush-tools-with-radial-layout"></a>使用放射狀配置的先進設計-筆刷工具

![MixedReality213 主要](images/mr213-main-600px.jpg)

在本章中，您將瞭解如何使用自訂筆刷工具集合來取代預設的動作控制器模型。 如需參考，您可以在 [**場景**] 資料夾下找到已完成的場景**MixedReality213Advanced** 。

### <a name="instructions"></a>指示

* 在 [**專案**] 面板的 [搜尋] 方塊中，輸入**BrushSelector** 。 您也可以在 [資產]/[AppPrefabs/] 下找到它。
* 將 [ **BrushSelector** prefab] 拖曳至 [階層 **] 面板。**
* 針對 [組織]，建立名為**筆刷**的空白 GameObject
* 將下列 prefabs 從 [**專案**] 面板拖曳至**筆刷**
    * 資產/AppPrefabs/**BrushFat**
    * 資產/AppPrefabs/**BrushThin**
    * 資產/AppPrefabs/**橡皮擦**
    * 資產/AppPrefabs/**MarkerFat**
    * 資產/AppPrefabs/**MarkerThin**
    * 資產/AppPrefabs/**鉛筆**

    ![筆刷](images/mixedreality213-brushes-250px.png)

* 按一下 **[階層**] 面板中的 [ **MotionControllers** prefab]。
* 在 [偵測**器**] 面板中，取消核取 [在**動作控制器視覺化**效果上**一律使用替代右模型**]
* **在 [階層**] 面板中，按一下 [ **BrushSelector** ]
* **BrushSelector**有一個名為**ColorPicker**的欄位
* 從 [階層] 面板中，將 [ **ColorPickerWheel** ] 拖曳至 [偵測**器** **] 面板中**的 [ **ColorPicker** ] 欄位。

    ![將 ColorPickerWheel 指派給筆刷選取器](images/mr213-brushselector-500px.jpg)

* **在 [階層**] 面板的 [ **BrushSelector** prefab] 底下，選取 [ **Menu** ] 物件。
* 在 [偵測**器**] 面板的 [ **LineObjectCollection** ] 元件底下，開啟 [**物件**陣列] 下拉式清單。 您會看到6個空的插槽。
* 從 [階層 **] 面板中**，將 [**筆刷**] GameObject 下的每個 prefabs 父項，以任何順序拖曳到這些位置。 （請確定您是從場景拖曳 prefabs，而不是專案資料夾中的 prefabs）。

![筆刷選取器](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefab**

由於**BrushSelector**會繼承**AttachToController**，因此它會在 [偵測**器**] 面板中顯示**慣用手**和**元素**選項。 我們選取了 [**右**] 並**指向 [姿勢**]，將筆刷工具附加至右側控制器，並具有正向方向。

**BrushSelector**會使用兩個公用程式：

* **橢圓形**：用來沿著橢圓形圖形來產生空間中的點。
* **LineObjectCollection**：使用任何線條類別所產生的點（例如橢圓形）來散發物件。 這就是我們用來沿著橢圓形圖形來放置筆刷的內容。

結合這些公用程式時，可以用來建立星形功能表。

**LineObjectCollection 腳本**

**LineObjectCollection**具有在其行中散佈之物件的大小、位置和旋轉控制項。 這適用于建立星形功能表，例如筆刷選取器。 若要建立筆刷的外觀，以在其接近置中選取的位置時，從任何範圍相應增加， **ObjectScale**曲線會尖峰在中間，並在邊緣 tapers。

**BrushSelector 腳本**

在**BrushSelector**的案例中，我們選擇使用程式動畫。 首先， **LineObjectCollection**腳本會在橢圓形中散發筆刷模型。 然後，每個筆刷會負責根據選取專案，依據其**DisplayMode**值來維護其在使用者手中的位置。 我們選擇了程式方法，因為當使用者選取筆刷時，會中斷筆刷位置轉換的機率偏高。 Mecanim 動畫可以正常地處理中斷，但是比簡單的 Lerp 作業來得複雜。

**BrushSelector**會使用兩者的組合。 當偵測到觸控板輸入時，筆刷選項會變成可見，並沿著星形功能表向上擴充。 在超時時間（表示使用者已進行選擇）之後，筆刷選項會再次相應減少，只保留選取的筆刷。

**視覺化觸控板輸入**

即使在已完全取代控制器模型的情況下，在原始模型輸入上顯示輸入會很有説明。 這有助於讓使用者在現實中採取動作。 針對**BrushSelector** ，我們選擇在收到輸入時，讓觸控板短暫顯示。 這是藉由從控制器抓取觸控板專案來完成，並以自訂資料取代其材質，然後根據上次收到觸控板輸入的時間，將漸層套用至該材質的色彩。

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**使用觸控板輸入的筆刷工具選取**

當筆刷選取器偵測到觸控板的已按下輸入時，它會檢查輸入的位置，以判斷它是在左邊或右邊。

**使用 selectPressedAmount 的筆觸粗細**

而不是**InteractionSourcePressType** ，而是在**InteractionSourcePressed （）** 中選取事件，您可以透過**selectPressedAmount**取得按下數量的類比值。 此值可在**InteractionSourceUpdated （）** 中取得。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**橡皮擦腳本**

**橡皮擦**是一種特殊類型的筆刷，會覆寫基底**筆刷**的**DrawOverTime （）** 函數。 當 Draw 為 true 時，橡皮擦會檢查其提示是否與任何現有的筆刷筆劃相交。 如果存在，則會將它們新增至要縮減和刪除的佇列。

## <a name="advanced-design---teleportation-and-locomotion"></a>Advanced design-Teleportation 和 locomotion

如果您想要允許使用者使用操縱杆透過 teleportation 來移動場景，請使用**MixedRealityCameraParent**而不是**MixedRealityCamera**。 您也需要新增**InputManager**和**DefaultCusor**。 由於**MixedRealityCameraParent**已經將**MotionControllers**和**界限**包含為子元件，因此您應該移除現有的**MotionControllers**和**環境**prefab。

### <a name="instructions"></a>指示

* **在 [階層**] 面板中，刪除**MixedRealityCamera**、**環境**和**MotionControllers**
* 從 [**專案] 面板**中，搜尋下列 prefabs，並將其拖曳至 [階層 **] 面板：**
    * 資產/AppPrefabs/輸入/Prefabs/**MixedRealityCameraParent**
    * 資產/AppPrefabs/輸入/Prefabs/**InputManager**
    * 資產/AppPrefabs/輸入/Prefabs/資料指標/**DefaultCursor**

    ![混合現實攝影機父系](images/mr213-cameraparent-300px.png)

* **在 [階層**] 面板中，按一下 [**輸入管理員**]
* 在 [偵測**器**] 面板中，向下流覽至**簡單的單一指標選取器**區段
* 從 [**階層**] 面板中，將 [ **DefaultCursor** ] 拖曳至 [**游標**] 欄位

    ![指派 DefaultCursor](images/mr213-defaultcursor-500px.png)

* **儲存**場景，然後按一下 [**播放**] 按鈕。 您將能夠使用操縱杆來向左/向右旋轉或傳送。

## <a name="the-end"></a>結束

這就是本教學課程的結尾！ 您已瞭解：

* 如何在 Unity 的遊戲模式和執行時間中使用動作控制器模型。
* 如何使用不同類型的按鈕事件及其應用程式。
* 如何在控制器上覆迭 UI 元素或完全自訂。

您現在已準備好開始建立您自己的使用動作控制器的沉浸式體驗！

## <a name="completed-scenes"></a>完成場景

* 在 Unity 的 [**專案**] 面板中，按一下 [**幕後**] 資料夾。
* 您會發現兩個 Unity sceens **MixedReality213**和**MixedReality213Advanced**。
    * **MixedReality213**：具有單一筆刷的已完成場景
    * **MixedReality213Advanced**：具有多重筆刷的已完成場景，並具有選取按鈕的按量範例

## <a name="see-also"></a>請參閱

* [MR 輸入213專案檔案](https://github.com/Microsoft/MixedReality213)
* [混合現實工具組-運動控制器測試場景](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [混合現實工具組-抓取機制](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [運動控制器開發指導方針](motion-controllers.md)
