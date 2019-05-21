---
title: MR 輸入 213
description: 遵循此程式碼撰寫的教學課程使用 Unity、 Visual Studio 和沈浸式耳機，若要了解動作控制器的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity 沉浸式動作控制站、 academy、 教學課程
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596966"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-input-213-motion-controllers"></a>MR 輸入 213:動作控制站

混合的現實世界中的動作控制站加入互動性的另一個層級。 具有[動作控制器](motion-controllers.md)，我們可以直接將其與物件互動以更自然的方式類似於我們在現實生活中的實體互動中增加訓練活動，並在您的應用程式體驗會非常喜歡這樣。

在 MR 輸入 213，我們將探討動作控制器的輸入的事件，藉由建立簡單的空間繪製體驗。 與此應用程式，使用者可以在 3d 空間中，使用各種類型的筆刷和色彩繪製。

## <a name="topics-covered-in-this-tutorial"></a>在本教學課程所涵蓋的主題

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**控制器的視覺效果**|**控制站的輸入的事件**|**自訂的控制器和 UI**|
|了解如何呈現在 Unity 的遊戲模式和執行階段的動作控制器模型。|了解不同類型的餂鈕瓿咘和他們的應用程式。|了解如何覆疊在控制器上的 UI 項目，或完全加以自訂。|

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 輸入 213:動作控制站</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>先決條件

請參閱安裝檢查清單的沈浸式耳機[本頁](install-the-tools.md)。

* 本教學課程需要[Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>專案檔

* [將檔案下載](https://github.com/Microsoft/MixedReality213/archive/master.zip)需要專案，然後將檔案解壓縮至桌面。

>[!NOTE]
>如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/MixedReality213)。

## <a name="unity-setup"></a>Unity 安裝

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>目標

* 最佳化 Unity for Windows Mixed Reality 開發
* 設定混合的實境相機
* 設定環境

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 **開啟**。
* 瀏覽至您的桌面及尋找**MixedReality213 master**先前未封存的資料夾。
* 按一下 [選擇資料夾]。
* Unity 完成載入專案檔案之後, 您將能夠看到 Unity 編輯器。
* 在 Unity 中，選取**檔案 > 組建設定**。

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* 選取 [**通用 Windows 平台**中**平台**清單，然後按一下**切換平台**] 按鈕。
* 若要設定目標裝置**任何裝置**
* 設定組建類型為**D3D**
* 若要設定 SDK**最新安裝**
* 請檢查**UnityC#專案**
    * 這可讓您修改 Visual Studio 專案中的指令碼檔案，而不需重建 Unity 專案。
* 按一下  **Player 設定**。
* 在 [ **Inspector** ] 面板中，捲動到底部
* 在 XR 設定中，檢查**虛擬實境支援**
* 在 虛擬實境 Sdk 中，選取**Windows Mixed Reality**

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* 關閉**組建設定**視窗。

### <a name="project-structure"></a>專案結構

本教學課程會使用 **[混合實境工具組-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 。 您可以找到這些發行版本[本頁](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)。

![ProjectStructure](images/mr213-projectstructure-650px.png)

**已完成的場景，供您參考**
* 您會發現兩個已完成下的 Unity 場景**場景**資料夾。
    * **MixedReality213**:已完成的場景，使用單一的筆刷
    * **MixedReality213Advanced**:完成進階的設計，含有多個筆刷的場景

**新的場景設定本教學課程**
* 在 Unity 中，按一下 **檔案 > 新的場景**
* 刪除**主攝影機**和**定向光線**
* 從 **[專案] 面板**，搜尋並拖曳到下列 prefabs**階層**面板：
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/**Environment**

![相機和環境](images/mr213-cameraenvironment-300px.jpg)
* 有兩個混合實境工具組中的相機 prefabs:
    * **MixedRealityCamera.prefab**:只有相機
    * **MixedRealityCameraParent.prefab**:相機屏障 + 界限
    * 在本教學課程中，我們將使用**MixedRealityCamera**沒有空間傳送功能。 因為這個緣故，我們加入簡單**環境**prefab 其中包含讓使用者覺得腳踏實地的基本樓層。
    * 若要深入了解與屏障**MixedRealityCameraParent**，請參閱[進階設計-屏障和 locomotion](#advanced-design---teleportation-and-locomotion)

**天空盒安裝程式**
* 按一下 **視窗 > 光源 > 設定**
* 按一下右側的圓形**天空盒資料欄位**
* 輸入 'gray'，然後選取  **SkyboxGray**

(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

![設定天空盒](images/mr123-skyboxsetting-400px.jpg)
* 請檢查**天空盒**選項，以查看指派灰色的漸層停駐天空盒

![切換天空盒選項](images/mr213-skyboxcheck-400px.jpg)
* 使用 MixedRealityCamera、 環境和灰色的天空盒場景會如下所示。

![MixedReality213 環境](images/mr213-environment-600px.jpg)
* 按一下 **檔案 > 儲存為場景**
* **儲存**場景的任何名稱的資料夾下場景

## <a name="chapter-1---controller-visualization"></a>第 1 章-控制站的視覺效果

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>目標

* 了解如何在 Unity 的遊戲模式，並在執行階段，控制器模型呈現動作。

Windows Mixed Reality 提供動畫的控制器模型，以控制站的視覺效果。 有數種方法，您可以在您的應用程式採取控制器視覺效果：
* 預設值-使用預設的控制站，而不需修改
* 混合式-使用預設的控制站，但自訂一些其項目或重疊 UI 元件
* 取代為使用您自己自訂的控制站的 3D 模型

在本章中，我們將了解這些控制器自訂的範例。

### <a name="instructions"></a>指示

* 在 [**專案**] 面板中，鍵入**MotionControllers**在搜尋方塊中。 您也可以尋找其下的資產/HoloToolkit/輸入/Prefabs /。
* 拖曳**MotionControllers**至 prefab**階層**面板。
* 按一下  **MotionControllers** prefab 中**階層**面板。

**MotionControllers prefab**

**MotionControllers** prefab 已經**MotionControllerVisualizer**指令碼，其會提供替代的控制器模型中的位置。 如果您指派您自己自訂的 3D 模型，例如手形或拉鋸，並檢查 「 一律使用替代左/右模型 」，您會看到它們，而不是預設模型。 我們將使用第 4 章中的這個位置來取代控制器模型使用筆刷。

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**指示**
* 在 [ **Inspector** ] 面板中，按兩下**MotionControllerVisualizer**若要查看 Visual Studio 中的程式碼的指令碼

**MotionControllerVisualizer script**

**MotionControllerVisualizer**並**MotionControllerInfo**類別提供方法來存取及修改的預設控制器模型。 **MotionControllerVisualizer**訂閱 Unity **InteractionSourceDetected**事件和自動會具現化控制器模型時找到它們。

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

根據傳遞的控制器模型[glTF 規格](https://github.com/KhronosGroup/glTF)。 已建立這種格式提供常見的格式，同時改善傳輸和解壓縮 3D 資產背後的程序。 在此情況下，我們要擷取及載入控制器模型，在執行階段，我們想要讓使用者的體驗盡可能順暢地，而且它具有不保證動作控制器的哪一個版本的使用者可能會使用。 本課程中的，混合實境工具組，透過使用 Khronos 群組的版本[UnityGLTF 專案](https://github.com/KhronosGroup/UnityGLTF)。

一旦已傳遞控制站，可以使用指令碼**MotionControllerInfo**來尋找特定控制器的項目轉換，讓它們可以正確地定位本身。

在稍後的章節中，我們將了解如何使用這些指令碼來將 UI 項目連結的控制站。

*某些指令碼，在中，您會發現使用的程式碼區塊 **#if ！UNITY_EDITOR**或是**UNITY_WSA**。只在 UWP 執行階段上的事件，是當您將部署到 Windows 執行的這些程式碼區塊。這是因為不同的一組 Unity editor 和 UWP 應用程式執行階段所使用的 Api。*
* **儲存**場景，然後按一下**播放** 按鈕。

您會看到在場景中耳機的移動控制站。 您可以看到詳細的動畫按鈕按下滑鼠、 搖桿移動和觸控板觸控反白顯示。

![MR213_Controller 視覺效果預設](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>第 2 章-附加到控制器的 UI 項目

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>目標

* 深入了解動作控制器的項目
* 了解如何將物件附加到特定的組件的控制站

在本章中，您將學習如何將使用者介面項目新增至控制器的使用者可以輕鬆地存取和操作，是在任何時間。 您也將學習如何將新增簡單的色彩選擇器 UI 使用觸控輸入。

### <a name="instructions"></a>指示

* 在 [**專案**] 面板中，搜尋**MotionControllerInfo**指令碼。
* 在搜尋結果中，按兩下**MotionControllerInfo**若要查看 Visual Studio 中的程式碼的指令碼。

**MotionControllerInfo script**

第一個步驟是選擇您想要附加至 UI 的控制站的哪個項目。 這些項目會定義於**ControllerElementEnum**中**MotionControllerInfo.cs**。

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* **首頁**
* **功能表**
* **Grasp**
* **搖桿**
* **Select**
* **觸控板**
* **指標的姿勢**– 此項目代表指正向方向的控制站的提示。

**指示**
* 在 [**專案**] 面板中，搜尋**AttachToController**指令碼。
* 在搜尋結果中，按兩下**AttachToController**若要查看 Visual Studio 中的程式碼的指令碼。

**AttachToController 指令碼**

**AttachToController**指令碼提供簡單的方式，將任何物件附加至指定的控制器法線慣用手和項目。

In **AttachElementToController()**,
* 檢查使用的法線慣用手的**MotionControllerInfo.Handedness**
* 取得控制器使用的特定項目**MotionControllerInfo.TryGetElement()**
* 擷取的項目之後從控制器模型，而父系下它的物件轉換，並將物件的本機位置和旋轉設為零。

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

若要使用最簡單的方式**AttachToController**指令碼是從它繼承，如我們所做的情況**ColorPickerWheel。** 只是覆寫**OnAttachToController**並**OnDetatchFromController**函式來執行您的設定 / 細目時偵測到 / 中斷連接的控制器。

**指示**
* 在 [**專案**] 面板中，在 [搜尋] 方塊中輸入**ColorPickerWheel**。 您也可以尋找其下的資產/AppPrefabs /。
* 拖曳**ColorPickerWheel**至 prefab**階層**面板。
* 按一下  **ColorPickerWheel** prefab 中**階層**面板。
* 在 [ **Inspector** ] 面板中，按兩下**ColorPickerWheel**若要查看 Visual Studio 中的程式碼的指令碼。

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel 指令碼**

由於**ColorPickerWheel**繼承**AttachToController**，它會顯示**法線慣用手**並**項目**中**Inspector**面板。 我們將會將附加 UI 至左的控制站上的觸控板項目。

![ColorPickerWheel 指令碼](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel**會覆寫**OnAttachToController**並**OnDetatchFromController**訂閱將會用於下一步 一章中使用的色彩選取範圍之輸入事件觸控輸入。

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
* **儲存**場景，然後按一下**播放** 按鈕。

**另一個方法來將物件附加至控制器**

我們建議您的指令碼繼承自**AttachToController** ，並覆寫**OnAttachToController**。 不過，這不一定可行。 替代方法使用它作為獨立元件。 當您想要將現有的 prefab 連結到控制器，而不需要重構您的指令碼時，這非常有用。 只需要等候 IsAttached 設為您的類別之前執行任何設定，則為 true。 若要這樣做最簡單的方式是使用協同程式的 'Start'。

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>第 3 章-使用觸控輸入

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>目標

* 了解如何取得觸控輸入的資料事件
* 了解如何使用觸控板座標軸位置資訊，針對您的應用程式體驗

### <a name="instructions"></a>指示

* 在 **階層** 面板中，按一下  **ColorPickerWheel**
* 在  **Inspector**  面板的  **Animatior**，按兩下  **ColorPickerWheelController**
* 您將能夠看到**動畫**開啟索引標籤

**顯示/隱藏 UI 與 Unity 的動畫控制器**

若要顯示和隱藏**ColorPickerWheel** UI 中的動畫，我們會使用[Unity 的動畫系統](https://docs.unity3d.com/Manual/AnimationOverview.html)。 設定**ColorPickerWheel**的**Visible**屬性設為 true 或 false 的觸發程序**顯示**並**隱藏**動畫觸發程序。 **顯示**並**隱藏**中所定義的參數**ColorPickerWheelController**動畫控制器。

![Unity 動畫控制器](images/mr123-animationcontroller-550px.jpg)

**指示**
* 在 **階層**面板中，選取**ColorPickerWheel** prefab
* 在 [ **Inspector** ] 面板中，按兩下**ColorPickerWheel**若要查看 Visual Studio 中的程式碼的指令碼

**ColorPickerWheel 指令碼**

**ColorPickerWheel**訂閱 Unity **InteractionSourceUpdated**接聽觸控事件的事件。

在  **InteractionSourceUpdated()**，指令碼會先檢查以確保它：
* 是實際的觸控事件 (obj.state。**touchpadTouched**)
* 來自左方的控制站 (obj.state.source。**法線慣用手的**)

如果兩者都是 true，觸控板的位置 (obj.state。**touchpadPosition**) 指派給**selectorPosition**。

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

在  **update （)**，這取決於**可見**屬性，就會觸發色彩選擇器的動畫元件中顯示和隱藏動畫觸發程序

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

在  **update （)**， **selectorPosition**用來轉換無限遠的光線色彩轉輪網狀結構 collider 傳回 UV 位置。 這個位置可用來尋找像素座標和色彩的色彩轉輪材質的值。 這個值是透過其他指令碼必須能夠**SelectedColor**屬性。

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

## <a name="chapter-4---overriding-controller-model"></a>第 4 章-覆寫控制器模型

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>目標

* 了解如何覆寫控制器模型，以自訂的 3D 模型。

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>指示

* 按一下  **MotionControllers**中**階層**面板。
* 按一下右側的圓形**替代的右方控制器**欄位。
* 在中輸入 **' BrushController**'，然後從結果選取 prefab。 您可以找到它資產/AppPrefabs/**BrushController**。
* 檢查**一律使用替代的正確模型**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**BrushController** prefab 沒有要納入**階層**面板。 不過，若要查看它的子元件：
* 在 [**專案**] 面板中，輸入**BrushController**拖**BrushController**至 prefab**階層**面板。

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

您會發現**祕訣**元件**BrushController**。 我們將使用其轉型，以啟動/停止繪製線條。
* 刪除**BrushController**從**階層**面板。
* **儲存**場景，然後按一下**播放** 按鈕。 您將能夠看到筆刷模型取代右移動控制器。

## <a name="chapter-5---painting-with-select-input"></a>第 5 章-使用選取的輸入繪製

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>目標

* 了解如何使用 [選取] 按鈕的事件來啟動和停止為線條繪圖

### <a name="instructions"></a>指示

* 搜尋**BrushController** prefab 中**專案**面板。
* 在 [ **Inspector** ] 面板中，按兩下**BrushController**若要查看 Visual Studio 中的程式碼的指令碼

**BrushController 指令碼**

**BrushController**訂閱 InteractionManager **InteractionSourcePressed**並**InteractionSourceReleased**事件。 當**InteractionSourcePressed**觸發事件時，筆刷**繪製**屬性設定為 true，當**InteractionSourceReleased**觸發事件時，筆刷的**繪製**屬性設定為 false。

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

雖然**繪製**設為 true，筆刷會產生點中具現化的 Unity **LineRenderer**。 此 prefab 的參考會保留在的筆刷**筆劃 Prefab**欄位。

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

若要使用目前選取的色彩，色彩選擇器滾輪 UI 中，從**BrushController**必須有參考**ColorPickerWheel**物件。 因為**BrushController** prefab 在做為取代控制站的執行階段具現化，場景中物件的任何參考必須在執行階段進行設定。 在此案例中，我們使用**GameObject.FindObjectOfType**找出**ColorPickerWheel**:

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
* **儲存**場景，然後按一下**播放** 按鈕。 您可以繪製線條和繪製右手邊的控制站上使用 [選取] 按鈕。

## <a name="chapter-6---object-spawning-with-select-input"></a>輸入一章 6-繁衍與選取的物件

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>目標

* 了解如何使用 Select 和理解餂鈕瓿咘輸入
* 了解如何具現化物件

### <a name="instructions"></a>指示

* 在 [**專案**] 面板中，鍵入**ObjectSpawner**在搜尋方塊中。 您也可以尋找其下的資產/AppPrefabs /
* 拖曳**ObjectSpawner**至 prefab**階層**面板。
* 按一下  **ObjectSpawner**中**階層**面板。
* **ObjectSpawner**具有名為欄位**色彩來源**。
* 從**階層** 面板中，拖曳**ColorPickerWheel**到這個欄位的參考。

![物件 Spawner 偵測器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* 按一下  **ObjectSpawner** prefab 中**階層**面板。
* 在 [ **Inspector** ] 面板中，按兩下**ObjectSpawner**若要查看 Visual Studio 中的程式碼的指令碼。

**ObjectSpawner 指令碼**

**ObjectSpawner**會具現化的空間的基本網格 （cube、 球體、 圓柱） 的複本。 當**InteractionSourcePressed**它會檢查法線慣用手的而且如果偵測到**InteractionSourcePressType.Grasp**或是**InteractionSourcePressType.Select**事件。

針對**抓住**事件，就會自動遞增的索引型別的目前網格 （sphere、 cube、 圓柱）

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

針對**選取 **事件，請在**SpawnObject()**，新的物件會具現化、 非父代和發行到全球。

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

**ObjectSpawner**會使用**ColorPickerWheel**設定顯示物件的材質的色彩。 繁衍 （spawn） 的物件會獲得這份資料的執行個體，因此它們會保留其色彩。
* **儲存**場景，然後按一下**播放** 按鈕。

您將能夠變更掌握按鈕的物件，然後繁衍 （spawn） 使用 [選取] 按鈕的物件。

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>建置並部署至混合實境入口網站的 應用程式
* 在 Unity 中，選取**檔案 > 組建設定**。
* 按一下 **加入開啟的場景**以新增至目前場景**組建中的場景**。
* 按一下 [建置] 。
* 建立**新的資料夾**名為 「 應用程式 」。
* 只要按一下**應用程式**資料夾。
* 按一下 [選擇資料夾]。
* Unity 完成時，會出現檔案總管 視窗。
* 開啟**應用程式**資料夾。
* 按兩下**YourSceneName.sln** Visual Studio 方案檔。
* 使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **X64**。
* 按一下 [裝置] 按鈕旁邊的下拉式箭號，然後選取**本機電腦**。
* 按一下 **偵錯-> 啟動但不偵錯**中的功能表或按**Ctrl + F5**。

現在應用程式是內建，並安裝在混合實境入口網站。 您可以重新啟動透過在混合實境入口網站中的 [開始] 功能表。

## <a name="advanced-design---brush-tools-with-radial-layout"></a>進階的程式設計-使用放射狀版面配置的筆刷工具

![MixedReality213 Main](images/mr213-main-600px.jpg)

在本章中，您將學習如何使用自訂的筆刷工具集合取代預設動作的控制器模型。 供您參考，您可以找到完整的場景**MixedReality213Advanced**下方**場景**資料夾。

### <a name="instructions"></a>指示

* 在 [**專案**] 面板中，鍵入**BrushSelector**在搜尋方塊中。 您也可以尋找其下的資產/AppPrefabs /
* 拖曳**BrushSelector**至 prefab**階層**面板。
* 為組織建立空白 GameObject 呼叫**筆刷**
* 下列從 prefabs 拖曳**專案** 面板到**筆刷**
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Assets/AppPrefabs/**Eraser**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Assets/AppPrefabs/**Pencil**

![筆刷](images/mixedreality213-brushes-250px.png)
* 按一下  **MotionControllers** prefab 中**階層**面板。
* 在 [ **Inspector** ] 面板中，取消核取**一律使用替代權限模型**上**動作控制器的視覺化檢視**
* 在 **階層** 面板中，按一下  **BrushSelector**
* **BrushSelector**具有名為欄位**ColorPicker**
* 從**階層** 面板中，拖曳**ColorPickerWheel**成**ColorPicker**欄位中**Inspector**面板。

![指派至筆刷選取器 ColorPickerWheel](images/mr213-brushselector-500px.jpg)
* 在 **階層** 面板的  **BrushSelector** prefab，選取**功能表**物件。
* 在  **Inspector**  面板的  **LineObjectCollection**元件，開啟**物件**陣列下拉式清單。 您會看到空的插槽 6。
* 從**階層** 面板中，拖曳每個父代下 prefabs**筆刷**GameObject 到這些位置依任何順序。 （請確定您從場景，而不在專案資料夾 prefabs 拖曳 prefabs。）

![筆刷選取器](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefab**

由於**BrushSelector**繼承**AttachToController**，它會顯示**法線慣用手**並**項目**中的選項**Inspector**面板。 我們選取 **權限**並**指向會造成**來將筆刷工具附加至有正向方向的右手邊控制器。

**BrushSelector**會利用兩個公用程式：
* **橢圓形**： 用來產生點沿著橢圓形圖案的空間中。
* **LineObjectCollection**： 會使用任何列類別 （例如橢圓形） 所產生的點物件。 這是什麼我們將使用放置我們沿著 [橢圓形] 圖形的筆刷。

結合時，這些公用程式可用來建立星形功能表。

**LineObjectCollection 指令碼**

**LineObjectCollection**具有適用於大小、 位置和旋轉物件沿著其列分散的控制。 這是適合用來建立類似的筆刷選取器的放射狀功能表。 若要建立外觀的筆刷可從 nothing 在接近選取置中位置，如**ObjectScale**邊緣的曲線要求尖峰期的置中與 tapers 已關閉。

**BrushSelector 指令碼**

若是**BrushSelector**，我們選擇使用程序的動畫。 首先，筆刷模型發佈的方式，藉由將橢圓形**LineObjectCollection**指令碼。 然後，每個筆刷是負責維護其根據使用者的手中的位置及其**DisplayMode**變更取決於選擇的值。 我們選擇程序性的方法，因為高中斷在使用者選取筆刷的筆刷位置轉換的機率。 Mecanim 動畫可以依正常程序，處理中斷，但它通常會比簡單的 Lerp 作業更複雜。

**BrushSelector**使用兩者的組合。 偵測到觸控輸入時，筆刷選項就會顯示出來，並沿著放射狀功能表相應增加。 逾時期限 （表示使用者已選取項目） 之後的筆刷選項擴展向下同樣地，離開只有選取的筆刷。

**視覺化觸控輸入**

即使是在其中已完全取代控制器模型的情況下，很有幫助顯示原始的模型輸入中的 輸入。 這有助於在現實中以讓使用者的動作。 針對**BrushSelector**我們選擇要觸控板短暫顯示在收到輸入。 這樣做，請從控制器，其內容取代為自訂的資料，擷取觸控板項目，然後將漸層套用至該材質的色彩，根據過去的時間觸控板收到輸入時。

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

**觸控輸入的筆刷工具選取範圍**

當筆刷選取器偵測到觸控的已按下的輸入時，它會檢查以判斷它是向左或向右輸入的位置。

**使用 selectPressedAmount 筆劃粗細**

而不是**InteractionSourcePressType.Select**中的事件**InteractionSourcePressed()**，您可以取得已按下量透過類比值**selectPressedAmount**. 此值可以在擷取**InteractionSourceUpdated()**。

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

**橡皮擦指令碼**

**橡皮擦**是一種特殊的覆寫基底的筆刷**筆刷**的**DrawOverTime()** 函式。 繪製，則為 true 時，橡皮擦會檢查其提示是否與任何現有的筆刷筆劃。 若是如此，它們是新增至佇列，以關閉壓縮，而且刪除。

## <a name="advanced-design---teleportation-and-locomotion"></a>進階的設計-屏障和 locomotion

如果您想要允許使用者與使用搖桿的屏障中移動場景，請使用**MixedRealityCameraParent**而不是**MixedRealityCamera**。 您也需要新增**InputManager**並**DefaultCusor**。 由於**MixedRealityCameraParent**已經包含**MotionControllers**並**界限**做為子元件，您應該移除現有**MotionControllers**並**環境**prefab。

### <a name="instructions"></a>指示

* 在 [**階層**] 面板中，刪除**MixedRealityCamera**，**環境**並**MotionControllers**
* 從 **[專案] 面板**，搜尋並拖曳到下列 prefabs**階層**面板：
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

![混合的實境相機父代](images/mr213-cameraparent-300px.png)
* 在 **階層** 面板中，按一下 **輸入管理員**
* 在 [ **Inspector** ] 面板中，向下捲動至**簡單的單一指標選取器**區段
* 從**階層** 面板中，拖曳**DefaultCursor**成**游標**欄位

![指派 DefaultCursor](images/mr213-defaultcursor-500px.png)
* **儲存**場景，然後按一下**播放** 按鈕。 您可以使用搖桿來旋轉左/右或傳送。

## <a name="the-end"></a>結束

而且，本教學課程結束 ！ 您已了解：
* 如何使用 Unity 的遊戲模式和執行階段中的動作控制器模型。
* 如何使用不同類型的餂鈕瓿咘和他們的應用程式。
* 如何覆疊在控制器上的 UI 項目，或完全加以自訂。

您現在已準備好開始使用影片控制站中建立您自己的沉浸式體驗 ！

## <a name="completed-scenes"></a>已完成的場景

* 在 Unity**專案**] 面板中的，按一下 [**場景**資料夾。
* 您會發現兩個 Unity sceens **MixedReality213**並**MixedReality213Advanced**。
    * **MixedReality213**:已完成的場景，使用單一的筆刷
    * **MixedReality213Advanced**:已完成的場景中填入多個筆刷選取按鈕的按下量範例

## <a name="see-also"></a>另請參閱

* [MR 輸入 213 專案檔](https://github.com/Microsoft/MixedReality213)
* [混合的實境工具組-動作控制器測試場景](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [混合的實境工具組-抓取機制](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [動作控制器的開發指導方針](motion-controllers.md)
