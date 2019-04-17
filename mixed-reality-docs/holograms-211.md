---
title: MR 輸入 211-筆勢
description: 請遵循此程式碼撰寫的逐步解說，使用 Unity、 Visual Studio 和 HoloLens，若要了解筆勢概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 academy、 教學課程中，軌跡
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596146"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

# <a name="mr-input-211-gesture"></a>MR 輸入 211:手勢

[筆勢](gestures.md)變成動作的使用者意圖。 處理筆勢，使用者可以互動全像投影。 在此課程中，我們將了解如何追蹤使用者的手中，回應使用者輸入，和以提供給使用者的意見反應手邊基礎狀態下和位置。

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

在  [MR 基本概念 101](holograms-101.md)，我們使用簡單的空中點選手勢互動我們全像投影。 現在，我們會超越空中點選手勢，並瀏覽至新的概念：

* 偵測何時正在追蹤使用者的手狀，並提供意見反應給使用者。
* 您可以使用 瀏覽筆勢來旋轉我們全像投影。
* 當使用者的手超出檢視時，請提供意見反應。
* 您可以使用操作事件，讓使用者移動其指針與全像投影。

在此課程中，我們再探討 Unity 專案**模型總管**，我們建置[MR 輸入 210](holograms-210.md)。 我們太空人朋友是回到協助我們探索這些新的筆勢概念。

>[!IMPORTANT]
>使用 Unity 及混合實境 toolkit 的推出較舊的版本記錄中的下列章節的每個內嵌的影片。 雖然的逐步指示是準確且即時的您可能會看到指令碼和對應已過期的影片中的視覺效果。 影片仍包含 posterity，和因為概念涵蓋仍然適用。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 輸入 211:手勢</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>先決條件

* Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。
* 基本C#程式設計的能力。
* 您應已完成[MR 基本概念 101](holograms-101.md)。
* 您應已完成[MR 輸入 210](holograms-210.md)。
* HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>專案檔

* 下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)專案所需。 需要 Unity 2017.2 或更新版本。
* 取消封存您的桌面或其他您輕鬆地連線到位置的檔案。

>[!NOTE]
>如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)。

### <a name="errata-and-notes"></a>偵錯 errata 和附註

* 若要停用 啟用 Just My Code 的需求 (*未核取*) 在 Visual Studio 的 工具-> 選項-> 偵錯以程式碼中設定中斷點。

## <a name="chapter-0---unity-setup"></a>第 0-Unity 安裝

### <a name="instructions"></a>指示

1. 啟動 Unity。
2. 選取 **開啟**。
3. 瀏覽至**筆勢**資料夾您先前未封存。
4. 尋找並選取**起始**/**模型總管**資料夾。
5. 按一下 [**選取資料夾**] 按鈕。
6. 在 [**專案**] 面板中，展開**場景**資料夾。
7. 按兩下**ModelExplorer**載入在 Unity 中的場景。

### <a name="building"></a>建置

1. 在 Unity 中，選取**檔案 > 組建設定**。
2. 如果**場景/ModelExplorer**中未列出**組建中的場景**，按一下 **加入開啟的場景**加入場景。
3. 如果您要特別開發的 HoloLens，設定**目標裝置**要**HoloLens**。 否則，將它保留在**任何裝置**。
4. 確保**建置型別**設為**D3D**並**SDK**設定為**最新安裝**（這應該可以 16299 或更新版本的 SDK）。
5. 按一下 [建置] 。
6. 建立**新的資料夾**名為 「 應用程式 」。
7. 只要按一下**應用程式**資料夾。
8. 按下**選取資料夾**，Unity 將會啟動 Visual studio 中建置專案。

Unity 完成時，會出現檔案總管 視窗。

1. 開啟**應用程式**資料夾。
2. 開啟**ModelExplorer Visual Studio 解決方案**。

如果將部署到 HoloLens:

1. 使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x86**。
2. 按一下下拉式清單 [本機電腦] 按鈕旁邊的箭號，然後選取**遠端機器**。
3. 請輸入**HoloLens 裝置的 IP 位址**並將驗證模式設定為**通用 （未加密的通訊協定）**。 按一下 **選取**。 如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**。
4. 在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。 如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device-hololens)。
5. 當應用程式部署時，關閉**Fitbox**具有**選取 軌跡**。

如果將部署到擬真耳機：

1. 使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x64**。
2. 請確定部署目標設定為**本機電腦**。
3. 在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。
4. 當應用程式部署時，關閉**Fitbox**所提取的動作控制站上的觸發程序。

>[!NOTE]
>您可能會注意到一些紅色的錯誤，在 Visual Studio 的 [錯誤] 面板。 它可以安全地忽略它們。 切換至 [輸出] 面板，若要檢視實際組建進度。 在 [輸出] 面板中的錯誤會要求您修正 （最常在指令碼中發生錯誤所造成）。

## <a name="chapter-1---hand-detected-feedback"></a>第 1 章-手動偵測到的意見反應

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>目標

* 訂閱交給追蹤事件。
* 您可以使用資料指標的意見反應，正在追蹤手的形狀時，顯示使用者。

### <a name="instructions"></a>指示

* 在 [**階層**] 面板中，展開**InputManager**物件。
* 尋找並選取**GesturesInput**物件。

**InteractionInputSource.cs**指令碼會執行下列步驟：

1. 訂閱 InteractionSourceDetected 和 InteractionSourceLost 事件。
2. 設定 HandDetected 狀態。
3. 從 InteractionSourceDetected 和 InteractionSourceLost 事件取消訂閱。

接下來，我們將升級從資料指標[MR 輸入 210](holograms-210.md)成一個顯示意見反應，視使用者的動作而定。

1. 在 **階層**面板中，選取**游標**物件，並將它刪除。
2. 在 [**專案**] 面板中，搜尋**CursorWithFeedback**並將它拖曳到**階層**面板。
3. 按一下 [ **InputManager**中**階層**] 面板，然後以拖曳方式**CursorWithFeedback**物件**階層**到InputManager 的**SimpleSinglePointerSelector**的**游標**欄位中，在底部**Inspector**。
4. 按一下  **CursorWithFeedback**中**階層**。
5. 在**Inspector**  面板中，展開**游標狀態資料**上**物件的資料指標**指令碼。

**資料指標狀態資料**運作方式如下所示：

* 任何**觀察**狀態表示沒有手動偵測到並四處只尋找使用者。
* 任何**Interact**手形或控制站會偵測到的狀態表示。
* 任何**暫留**狀態表示使用者查看雷射。

### <a name="build-and-deploy"></a>建置和部署

* 在 Unity 中，使用**檔案 > 組建設定**重建應用程式。
* 開啟**應用程式**資料夾。
* 如果它尚未開啟，開啟**ModelExplorer Visual Studio 方案**。
  * （如果您已經建置/部署此專案在 Visual Studio 設定期間，然後您可以開啟 VS 執行個體並按一下 [重新載入全部] 出現提示時）。
* 在 Visual Studio 中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。
* 應用程式部署到 HoloLens 之後，關閉使用空中點選手勢 fitbox。
* 將您的手才移至 檢視和食指指向天空啟動手動追蹤。
* 移動您的手左、 右、 向上和向下。
* 觀看如何，游標會變成手上已偵測到，再從檢視遺失時。
* 如果您所在的沈浸式耳機時，您必須連接或中斷連接您的控制器。 連接的控制器一律是 「 可用 」 時，此意見反應會變得較不有趣沈浸式裝置。

## <a name="chapter-2---navigation"></a>第 2 章-瀏覽

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>目標

* 您可以使用 瀏覽軌跡事件來旋轉太空人。

### <a name="instructions"></a>指示

若要使用軌跡瀏覽我們的應用程式中，我們將編輯**GestureAction.cs**時瀏覽鍵筆勢，就會發生旋轉物件。 此外，我們將新增意見反應，來瀏覽可用時，所顯示的游標。

1. 在 [**階層**] 面板中，展開**CursorWithFeedback**。
2. 在 **全像投影**資料夾中，尋找**ScrollFeedback**資產。
3. 將拖放**ScrollFeedback**拖曳至 prefab **CursorWithFeedback**中的 GameObject**階層**。
4. 按一下  **CursorWithFeedback**。
5. 在  **Inspector**  面板中，按一下**新增元件** 按鈕。
6. 在功能表中，輸入在搜尋方塊**CursorFeedback**。 選取搜尋結果。
7. 將拖放**ScrollFeedback**物件**階層**拖曳至**捲動偵測到的遊戲物件**中的屬性**資料指標的意見反應**元件**Inspector**。
8. 在 **階層**面板中，選取**AstroMan**物件。
9. 在  **Inspector**  面板中，按一下**新增元件** 按鈕。
10. 在功能表中，輸入在搜尋方塊**手勢動作**。 選取搜尋結果。

接下來，開啟**GestureAction.cs** Visual Studio 中。 在撰寫程式碼練習 2.c，編輯指令碼，執行下列操作：

1. **旋轉 AstroMan**物件每當執行瀏覽動作時。
2. 計算**rotationFactor**來控制旋轉套用至物件的大小。
3. **旋轉物件**繞 y 軸，當使用者將其手動左邊或右邊。

完整的程式碼撰寫練習 2.c 指令碼或取代已完成的解決方案使用的程式碼中：

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

您會發現其他瀏覽事件已經會填入部分資訊。 我們將推送到此工具組的 GameObject InputSystem 的強制回應堆疊，因此使用者不需要專注在太空人一旦開始旋轉。 同樣地，我們顯示堆疊中取出 GameObject 完成筆勢。

### <a name="build-and-deploy"></a>建置和部署

1. 重建 Unity 中的應用程式，然後建置並部署從執行中的 HoloLens 的 Visual Studio。
2. 注視太空人，兩個箭號應該會出現在左邊或右邊的資料指標。 這個新的視覺效果指示太空人可以被輪替。
3. 將手放在準備好的位置 （食指指向天空） 讓 HoloLens 會開始追蹤您的手。
4. 若要輪替太空人，降低食指到縮小的位置，然後再移手左邊或右邊觸發 NavigationX 筆勢。

## <a name="chapter-3---hand-guidance"></a>第 3 章-手動指引

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>目標

* 使用**交給指引分數**協助預測時，手動追蹤將會遺失。
* 提供**意見反應游標**顯示當使用者的手接近檢視的相機的邊緣。

### <a name="instructions"></a>指示

1. 在 **階層**面板中，選取**CursorWithFeedback**物件。
2. 在  **Inspector**  面板中，按一下**新增元件** 按鈕。
3. 在功能表中，輸入在搜尋方塊**手指引**。 選取搜尋結果。
4. 在 **專案**面板**全像投影**資料夾中，尋找**HandGuidanceFeedback**資產。
5. 將拖放**HandGuidanceFeedback**拖曳至資產**手指引指標**中的屬性**Inspector**面板。

### <a name="build-and-deploy"></a>建置和部署

* 重建 Unity 中的應用程式然後建置並從 Visual Studio 體驗 HoloLens 上的應用程式部署。
* 您的手帶入檢視，並引發食指取得追蹤。
* 開始輪替與瀏覽筆勢太空人 （縮小食指和 thumb 一起）。
* 最左邊，以滑鼠右鍵，，向上和向下，請移動您的手。
* 因為您的手接近筆勢框架邊緣，應該旁出現的箭號來警告您該追蹤的手狀游標將會遺失。 箭號表示的方向，以避免遺失追蹤移動您的手。

## <a name="chapter-4---manipulation"></a>第 4 章-操作

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>目標

* 若要移動雙手太空人使用操作事件。
* 若要讓使用者知道可以使用操作時資料指標上提供意見反應。

### <a name="instructions"></a>指示

GestureManager.cs 和 AstronautManager.cs 可讓我們執行下列作業：

1. 使用語音關鍵字"**移動太空人**「 若要啟用**操作**筆勢和 「**旋轉太空人**"停用它們。
2. 切換至回應**操作筆勢辨識器**。

那就開始吧。

1. 在 [**階層**] 面板中，建立新的空 GameObject。 它命名為"**AstronautManager**"。
2. 在  **Inspector**  面板中，按一下**新增元件** 按鈕。
3. 在功能表中，輸入在搜尋方塊**太空人 Manager**。 選取搜尋結果。
4. 在  **Inspector**  面板中，按一下**新增元件** 按鈕。
5. 在功能表中，輸入在搜尋方塊**語音輸入來源**。 選取搜尋結果。

現在，我們要加入控制太空人互動狀態所需的語音命令。

1. 依序展開**關鍵字**一節**Inspector**。
2. 按一下  **+** 右邊加入新的關鍵字。
3. 類型為關鍵字**移動太空人**。 歡迎加入索引鍵的快顯，如有需要。
4. 按一下  **+** 右邊加入新的關鍵字。
5. 類型為關鍵字**旋轉太空人**。 歡迎加入索引鍵的快顯，如有需要。
6. 對應的處理常式程式碼可在**GestureAction.cs**，請在**ISpeechHandler.OnSpeechKeywordRecognized**處理常式。

![如何設定第 4 章語音輸入來源](images/holograms211-speech.png)

接下來，我們將設定資料指標上的操作意見反應。

1. 在 **專案**面板**全像投影**資料夾中，尋找**PathingFeedback**資產。
2. 將拖放**PathingFeedback**拖曳至 prefab **CursorWithFeedback**物件**階層**。
3. 在 [**階層**] 面板中，按一下**CursorWithFeedback**。
4. 將拖放**PathingFeedback**物件**階層**拖曳至**路徑偵測到的遊戲物件**中的屬性**資料指標的意見反應**元件**Inspector**。

現在我們要將程式碼加入**GestureAction.cs**以啟用下列：

1. 將程式碼加入**IManipulationHandler.OnManipulationUpdated**函式，會移動太空人時**操作**偵測到筆勢時。
2. 計算**移動向量**來判斷應該太空人移到基底的庫存位置。
3. **移動**太空人移動至新位置。

完整的程式碼撰寫練習在 4.a **GestureAction.cs**，或使用我們已完成的解決方案下方：

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

### <a name="build-and-deploy"></a>建置和部署

* 在 Unity 中重建然後建置並部署從執行中 HoloLens 的應用程式的 Visual Studio。
* 移動手 HoloLens 前方，並引發食指，以便可以追蹤。
* 透過太空人著重資料指標。
* 假設要移動與操作筆勢太空人的 ' 移動太空人 '。
* 四個箭號應否顯示資料指標來表示程式會立即回應操作事件。
* 降低食指向您捲動方塊中，並讓他們一起 pinched。
* 當您移動您的手周圍，也會跟著移動太空人 （這是操作）。
* 引發食指停止操作太空人。
* 注意：如果移動您的手之前不假設移動太空人然後瀏覽軌跡將會改用。
* 假設 '旋轉太空人' 回到座艙的狀態。

## <a name="chapter-5---model-expansion"></a>第 5 章-模型擴充

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>目標

* 展開太空人模型分成多個、 較小組件的使用者可以與互動。
* 移動使用個別的軌跡瀏覽和操作每個片段。

### <a name="instructions"></a>指示

在本節中，我們將完成下列工作：

1. 加入新的關鍵字 「**展開模型**"展開太空人模型。
2. 加入新的關鍵字 「**重設的模型**"以返回其原始形式的模型。

我們會加入語音輸入來源中的兩個的多個關鍵字，從上一章。 我們也將示範另一種方式來處理辨識的事件。

1. 按一下 上一步**AstronautManager**中**Inspector**展開**關鍵字**一節中**Inspector**。
2. 按一下  **+** 右邊加入新的關鍵字。
3. 類型為關鍵字**展開模型**。 歡迎加入索引鍵的快顯，如有需要。
4. 按一下  **+** 右邊加入新的關鍵字。
5. 類型為關鍵字**重設模型**。 歡迎加入索引鍵的快顯，如有需要。
6. 在  **Inspector**  面板中，按一下**新增元件** 按鈕。
7. 在功能表中，輸入在搜尋方塊**語音輸入處理常式**。 選取搜尋結果。
8. 請檢查**是全域的接聽程式**，因為我們希望我們著重這些命令不受限於 GameObject。
9. 按一下  **+** 按鈕，然後選取**展開模型**關鍵字下拉式清單中。
10. 按一下  **+** 下的回應，並將拖曳**AstronautManager**從**階層**到**None （物件）** 欄位。
11. 現在，按一下  **No 函式**下拉式清單中，選取**AstronautManager**，然後**ExpandModelCommand**。
12. 按一下 語音輸入處理常式**+** 按鈕，然後選取**重設的模型**關鍵字下拉式清單中。
13. 按一下  **+** 下的回應，並將拖曳**AstronautManager**從**階層**到**None （物件）** 欄位。
14. 現在，按一下  **No 函式**下拉式清單中，選取**AstronautManager**，然後**ResetModelCommand**。

![如何設定語音輸入來源和處理常式的第 5 章](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>建置和部署

* 試試看！ 建置並部署到 HoloLens 的應用程式。
* 假設**展開模型**來查看展開的太空人模型。
* 使用**瀏覽**旋轉太空人花色的各個部分。
* 假設**移動太空人**，然後使用**操作**移動太空人花色的各個部分。
* 假設**旋轉太空人**再次旋轉項目。
* 假設**重設的模型**太空人返回其原始形式。

## <a name="the-end"></a>結束

恭喜您！ 您現在已完成**MR 輸入 211:筆勢**。

* 您知道如何偵測和回應交給追蹤、 瀏覽和操作事件。
* 您了解瀏覽和操作筆勢之間的差異。
* 您知道如何變更資料指標來手動偵測到時，會遺失，手的形狀時以及當物件支援不同的互動 （瀏覽與操作） 提供視覺化回饋。
