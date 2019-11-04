---
title: MR 輸入 211-手勢
description: 遵循此編碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解手勢概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學院、教學課程、手勢
ms.openlocfilehash: d7a92e4b2f196d6d8b0ba0fe3ccb2aed87479ac1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434693"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。

# <a name="mr-input-211-gesture"></a>MR 輸入211：手勢

[手勢](gaze-and-commit.md#composite-gestures)會將使用者意圖變成動作。 透過手勢，使用者可以與全息影像互動。 在本課程中，我們將學習如何追蹤使用者的手、回應使用者輸入，並根據手中的狀態和位置提供意見反應給使用者。

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

在[MR 基本 101](holograms-101.md)中，我們使用了簡單的點按手勢來與我們的全息影像互動。 現在，我們將超越空中操作手勢，並探索新的概念來：

* 偵測使用者的手追蹤，並提供意見反應給使用者。
* 使用導覽手勢來旋轉我們的全息影像。
* 當使用者想要離開時，請提供意見反應。
* 使用操作事件可讓使用者以自己的手移動全息影像。

在此課程中，我們將會回顧 Unity 專案**模型瀏覽器**，我們在[MR 輸入 210](holograms-210.md)中建立了這項功能。 我們的太空人 friend 會回頭協助我們探索這些新的手勢概念。

>[!IMPORTANT]
>下列各章節所內嵌的影片，都是使用舊版 Unity 和混合現實工具組錄製的。 雖然逐步指示是正確且最新的，但您可能會在已過期的對應影片中看到腳本和視覺效果。 影片仍包含在 posterity 中，因為涵蓋的概念仍適用。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 輸入211：手勢</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

* [已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。
* 一些基本C#的程式設計能力。
* 您應已完成[MR 基本概念 101](holograms-101.md)。
* 您應已完成[MR 輸入 210](holograms-210.md)。
* [為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔案

* 下載專案[所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)檔案。 需要 Unity 2017.2 或更新版本。
* 將檔案取消封存至您的桌面或其他容易到達的位置。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼，可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)取得。

### <a name="errata-and-notes"></a>勘誤和注意事項

* 必須在 Visual Studio 下的 [工具]-[> 選項]-[> 的偵錯工具] 中停用（*取消*核取） [啟用 Just My Code]，才能在程式碼中叫用中斷點。

## <a name="chapter-0---unity-setup"></a>第0章-Unity 設定

### <a name="instructions"></a>指示

1. 啟動 Unity。
2. 選取 [**開啟**]。
3. 流覽至您先前取消封存的**手勢**資料夾。
4. 尋找並選取 [**開始**/**模型瀏覽器**] 資料夾。
5. 按一下 [**選取資料夾**] 按鈕。
6. 在 [**專案**] 面板中，展開 [**幕後**] 資料夾。
7. 按兩下 [ **ModelExplorer**場景]，將其載入 Unity。

### <a name="building"></a>建置

1. 在 Unity 中，選取 [檔案] **> [組建設定**]。
2. 如果 [**場景/ModelExplorer** ] 未在 [組建] 的**場景**中列出，請按一下 [**新增開啟場景**] 以加入場景。
3. 如果您是特別針對 HoloLens 進行開發，請將**目標裝置**設定為**hololens**。 否則，請將它保留在**任何裝置**上。
4. 確定 [**組建類型**] 設定為 [ **D3D** ]，並將 [ **sdk** ] 設定為 [**已安裝最新**版本] （應該是 SDK 16299 或更新版本）。
5. 按一下 [建置]。
6. 建立名為 "App" 的**新資料夾**。
7. 按一下 [**應用程式**] 資料夾。
8. 按下 [**選取資料夾**]，Unity 就會開始建立 Visual Studio 的專案。

當 Unity 完成時，將會出現 [檔案瀏覽器] 視窗。

1. 開啟**應用程式**資料夾。
2. 開啟**ModelExplorer Visual Studio 解決方案**。

如果部署至 HoloLens：

1. 使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x86**。
2. 按一下 [本機電腦] 按鈕旁的下拉式箭號，然後選取 [**遠端電腦**]。
3. 輸入**您的 HoloLens 裝置 IP 位址**，並將驗證模式設定為 **[通用（未加密的通訊協定）** ]。 按一下 [**選取**]。 如果您不知道您的裝置 IP 位址，請查看 [設定] [ **> Network & Internet] > [Advanced Options**]。
4. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。 如果這是您第一次部署至您的裝置，您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device)。
5. 應用程式部署完成後，請使用**select 手勢**來關閉**Fitbox** 。

如果部署到沉浸式耳機：

1. 使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x64**。
2. 請確定 [部署目標] 設定為 [**本機電腦**]。
3. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。
4. 應用程式部署完成後，請藉由在動作控制器上提取觸發程式來關閉**Fitbox** 。

>[!NOTE]
>在 [Visual Studio 錯誤] 面板中，您可能會注意到一些紅色錯誤。 可以放心地忽略它們。 切換至 [輸出] 面板以查看實際的組建進度。 [輸出] 面板中的錯誤會要求您進行修正（最常見的原因是腳本錯誤）。

## <a name="chapter-1---hand-detected-feedback"></a>第1章-一手偵測到的意見反應

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>目標

* 訂閱手寫追蹤事件。
* 使用游標意見反應，在追蹤手時顯示使用者。

>[!NOTE]
>在 HoloLens 2 上，只要看到手（而不只是指手指的狀態）時，就會引發實習偵測。

### <a name="instructions"></a>指示

* **在 [階層**] 面板中，展開 [ **InputManager** ] 物件。
* 尋找並選取**GesturesInput**物件。

**InteractionInputSource.cs**腳本會執行下列步驟：

1. 訂閱 InteractionSourceDetected 和 InteractionSourceLost 事件。
2. 設定 HandDetected 狀態。
3. 從 InteractionSourceDetected 和 InteractionSourceLost 事件取消訂閱。

接下來，我們會將我們的資料指標從[MR 輸入 210](holograms-210.md)升級為根據使用者的動作顯示意見反應的資料指標。

1. **在 [階層] 面板中**，選取**游標**物件，並將它刪除。
2. 在 [**專案**] 面板中，搜尋**CursorWithFeedback** ，**並將它拖曳至 [階層**] 面板。
3. 按一下 [階層 **] 面板中的 [** **InputManager** ]，然後將**CursorWithFeedback**物件從階層**拖曳至 InputManager**的**SimpleSinglePointerSelector**的 [**游標**] 欄位（位於底部）偵測**器**。
4. 按一下階層**中的 [** **CursorWithFeedback** ]。
5. 在 [偵測**器**] 面板中，展開**物件游標**腳本上的 [**游標狀態資料**]。

**游標狀態資料**的運作方式如下所示：

* 任何**觀察**狀態表示不會偵測到任何手，而且使用者只需要尋找。
* 任何**互動**狀態表示偵測到手或控制器。
* 任何**停留**狀態表示使用者正在查看全像投影。

### <a name="build-and-deploy"></a>組建和部署

* 在 Unity 中，使用檔案 **> 組建設定**來重建應用程式。
* 開啟**應用程式**資料夾。
* 如果尚未開啟，請開啟**ModelExplorer Visual Studio 解決方案**。
  * （如果您已經在安裝期間于 Visual Studio 內建立/部署此專案，則可以開啟 VS 的實例，然後在出現提示時按一下 [全部重載]）。
* 在 Visual Studio 中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。
* 將應用程式部署至 HoloLens 之後，請使用 [點一下] 手勢來關閉 fitbox。
* 將您的手移到視野中，並將您的索引指向天空以開始追蹤。
* 向左、向右、向上和向下移動。
* 在偵測到您的手時，觀看游標變更的方式，然後從 view 中消失。
* 如果您使用的是沉浸式耳機，就必須連接並中斷控制器的連線。 此意見反應在沉浸式裝置上會變得較不有趣，因為連線的控制器一律會「可用」。

## <a name="chapter-2---navigation"></a>第2章-流覽

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>目標

* 使用導覽手勢事件來旋轉太空人。

### <a name="instructions"></a>指示

若要在我們的應用程式中使用導覽手勢，我們將在導覽手勢發生時，編輯**GestureAction.cs**以旋轉物件。 此外，我們還會將意見反應新增至游標，以便在導覽可供使用時顯示。

1. **在 [階層**] 面板中，展開 [ **CursorWithFeedback**]。
2. 在 [**全息影像**] 資料夾中，尋找**ScrollFeedback**資產。
3. 將**ScrollFeedback** prefab 拖放到階層中的**CursorWithFeedback** **GameObject。**
4. 按一下 [ **CursorWithFeedback**]。
5. 在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。
6. 在功能表的 [搜尋] 方塊中，輸入**CursorFeedback**。 選取搜尋結果。
7. 從階層中，將**ScrollFeedback** **物件拖放至偵測** **器**中**游標意見**反應元件的 [ **Scroll 偵測到的遊戲物件**] 屬性。
8. **在 [階層**] 面板中，選取 [ **AstroMan** ] 物件。
9. 在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。
10. 在功能表中，于 [搜尋] 方塊中輸入**手勢動作**。 選取搜尋結果。

接下來，在 Visual Studio 中開啟**GestureAction.cs** 。 在編碼練習 2. c 中，編輯腳本以執行下列動作：

1. 每當執行導覽手勢時 **，旋轉 AstroMan**物件。
2. 計算**rotationFactor**以控制套用至物件的旋轉量。
3. 當使用者向左或向右移動時，旋轉 y 軸的**物件**。

在腳本中完成程式碼編寫練習 2. c，或以下列已完成的解決方案取代程式碼：

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

您會發現其他導覽事件已填入一些資訊。 我們會將 GameObject 推送至工具組的 InputSystem's 強制堆疊，讓使用者不需要在開始旋轉之後，將焦點保持在太空人上。 同樣地，在手勢完成後，我們會將 GameObject 從堆疊中彈出。

### <a name="build-and-deploy"></a>組建和部署

1. 在 Unity 中重建應用程式，然後從 Visual Studio 建立及部署，以在 HoloLens 中執行。
2. 看一下太空人，游標的任一邊應該會出現兩個箭號。 這個新的視覺效果表示太空人可以旋轉。
3. 將您的手放在就緒的位置（食指指向天空），讓 HoloLens 能夠開始追蹤您的手。
4. 若要旋轉太空人，請將您的索引指向縮小位置，然後向左或向右移動以觸發 NavigationX 手勢。

## <a name="chapter-3---hand-guidance"></a>第3章-右手指引

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>目標

* 使用**手動指引分數**來協助預測何時會遺失手動追蹤。
* 提供**游標的意見**反應，以顯示使用者何時接近相機的觀看邊緣。

### <a name="instructions"></a>指示

1. **在 [階層**] 面板中，選取 [ **CursorWithFeedback** ] 物件。
2. 在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。
3. 在功能表中，于搜尋方塊中輸入**指引**。 選取搜尋結果。
4. 在 [**專案**面板] [**全息影像**] 資料夾中，尋找**HandGuidanceFeedback**資產。
5. 將**HandGuidanceFeedback**資產拖放至 [偵測**器**] 面板中的 [**右手指引指標**] 屬性。

### <a name="build-and-deploy"></a>組建和部署

* 在 Unity 中重建應用程式，然後從 Visual Studio 建立及部署，以在 HoloLens 上體驗應用程式。
* 帶入您的手中，並提起您的索引手指以進行追蹤。
* 使用導覽手勢開始旋轉太空人（將您的索引手指和 thumb 一起縮小）。
* 將您的手往左、靠右、向上和向下移動。
* 當您的手接近手勢框架的邊緣時，游標旁邊應該會出現箭號，以警告您將會遺失追蹤。 箭號表示要移動手的方向，以避免追蹤遺失。

## <a name="chapter-4---manipulation"></a>第4章-操作

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>目標

* 使用操作事件以您的手移動太空人。
* 提供游標的意見反應，讓使用者知道何時可以使用操作。

### <a name="instructions"></a>指示

GestureManager.cs 和 AstronautManager.cs 可讓我們執行下列動作：

1. 使用語音關鍵字 "**Move 太空人**" 啟用**操作**手勢，並將 [**旋轉太空人**] 停用。
2. 切換為回應**操作手勢辨識器**。

那就開始吧。

1. **在 [階層**] 面板中，建立新的空白 GameObject。 將它命名為 "**AstronautManager**"。
2. 在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。
3. 在功能表的 [**太空人管理員**] 搜尋方塊中輸入。 選取搜尋結果。
4. 在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。
5. 在功能表中，于 [**語音輸入來源**] 搜尋方塊中輸入。 選取搜尋結果。

我們現在會新增控制太空人互動狀態所需的語音命令。

1. 展開偵測**器**中的 [**關鍵字**] 區段。
2. 按一下右手邊的  **+** ，以加入新的關鍵字。
3. 輸入關鍵字做為**移動太空人**。 如有需要，您可以隨意新增金鑰快捷方式。
4. 按一下右手邊的  **+** ，以加入新的關鍵字。
5. 輸入關鍵字作為 [**旋轉太空人**]。 如有需要，您可以隨意新增金鑰快捷方式。
6. 對應的處理常式程式碼可以在**GestureAction.cs**中的**ISpeechHandler. OnSpeechKeywordRecognized**處理常式中找到。

![如何設定第4章的語音輸入來源](images/holograms211-speech.png)

接下來，我們會在資料指標上設定操作意見反應。

1. 在 [**專案**面板] [**全息影像**] 資料夾中，尋找**PathingFeedback**資產。
2. 將**PathingFeedback** prefab 拖放到階層中的**CursorWithFeedback**物件上 **。**
3. **在 [階層**] 面板中，按一下 [ **CursorWithFeedback**]。
4. 從階層中，將**PathingFeedback** **物件拖放至偵測** **器**的資料**指標意見**反應元件中的 [偵測到的內容]**遊戲物件**屬性。

現在，我們需要將程式碼新增至**GestureAction.cs** ，以啟用下列各項：

1. 將程式碼新增至**IManipulationHandler. OnManipulationUpdated**函式，此函式會在偵測到**操作**手勢時移動太空人。
2. 計算**移動向量**，以根據手上的位置判斷太空人的移動位置。
3. **將太空人移**至新位置。

完成程式碼撰寫練習 4. 中的**GestureAction.cs**，或使用下列已完成的解決方案：

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>組建和部署

* 在 Unity 中重建，然後從 Visual Studio 建立及部署，以在 HoloLens 中執行應用程式。
* 將您的手移到 HoloLens 前方，並引發您的索引手指，讓它可以進行追蹤。
* 將游標放在太空人上。
* 說「移動太空人」，以操作手勢移動太空人。
* 游標周圍應會出現四個箭號，表示程式會立即回應操作事件。
* 將您的索引向下移到您的經驗，並將其 pinched 在一起。
* 當您四處移動時，太空人也會移動（這是操作）。
* 請提高您的索引手指，以停止操作太空人。
* 注意：如果您在移動手前不要說「移動太空人」，則會改為使用導覽手勢。
* 說「旋轉太空人」回到 rotatable 狀態。

## <a name="chapter-5---model-expansion"></a>第5章-模型展開

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>目標

* 將太空人模型展開成多個較小的片段，讓使用者可以與之互動。
* 使用導覽和操作手勢來個別移動每個部分。

### <a name="instructions"></a>指示

在本節中，我們將完成下列工作：

1. 加入新的關鍵字「**展開模型**」以展開太空人模型。
2. 加入新的關鍵字「**重設模型**」，將模型傳回原始格式。

我們會藉由在上一章中新增兩個關鍵字到語音輸入來源來完成此動作。 我們也將示範另一種處理辨識事件的方式。

1. 在偵測器**中按一下**[上一頁]，然後展開 [**檢查**] 中的 [**關鍵字**] 區段。
2. 按一下右手邊的  **+** ，以加入新的關鍵字。
3. 輸入關鍵字作為 [**展開模型**]。 如有需要，您可以隨意新增金鑰快捷方式。
4. 按一下右手邊的  **+** ，以加入新的關鍵字。
5. 輸入關鍵字作為 [**重設模型**]。 如有需要，您可以隨意新增金鑰快捷方式。
6. 在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。
7. 在功能表中，于 [**語音輸入處理常式**] 搜尋方塊中輸入。 選取搜尋結果。
8. 檢查**是全域接聽程式**，因為我們想要讓這些命令都能正常執行，而不受我們所關注的 GameObject。
9. 按一下 [ **+** ] 按鈕，然後從 [關鍵字] 下拉式清單中選取 [**展開模型**]。
10. 按一下 [回應] 底下的 [ **+** ]，然後將**AstronautManager**從階層**拖曳至 [** 無] **（物件）** 欄位。
11. 現在，按一下 [**沒有**函式] 下拉式清單，選取 [ **AstronautManager**]，然後選取 [ **ExpandModelCommand**]。
12. 按一下語音輸入處理常式的 **+**  按鈕，然後從 關鍵字 下拉式清單中選取 **重設模型**。
13. 按一下 [回應] 底下的 [ **+** ]，然後將**AstronautManager**從階層**拖曳至 [** 無] **（物件）** 欄位。
14. 現在，按一下 [**沒有**函式] 下拉式清單，選取 [ **AstronautManager**]，然後選取 [ **ResetModelCommand**]。

![如何設定第5章的語音輸入來源和處理常式](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>組建和部署

* 試試看！ 建立應用程式並將其部署至 HoloLens。
* 假設**展開模型**以查看展開的太空人模型。
* 使用 [**導覽**] 來旋轉太空人花色的個別部分。
* 假設**Move 太空人**，然後使用**操作**來移動太空人花色的個別部分。
* 假設 [**旋轉太空人**] 再次旋轉各部分。
* 假設 [**重設模型**] 會將太空人回到其原始表單。

## <a name="the-end"></a>結束

恭喜！ 您現在已完成**MR 輸入211：手勢**。

* 您知道如何偵測和回應手動追蹤、導覽和操作事件。
* 您瞭解導覽和動作筆勢之間的差異。
* 您知道如何變更游標，以便在偵測到手時、即將遺失時，以及物件支援不同互動（導覽與操作）時，提供視覺效果的意見反應。
