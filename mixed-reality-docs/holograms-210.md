---
title: MR 輸入 210-視線
description: 遵循此程式碼逐步解說如何使用 Unity、 Visual Studio 和 HoloLens，若要了解視線概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit、 mixedrealitytoolkit-academy，教學課程，視線 unity
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993549"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

# <a name="mr-input-210-gaze"></a>MR 輸入 210:注視

[視線](gaze.md)是第一種形式的輸入，並會顯示使用者的意圖和感知。 MR 輸入 210 (也稱為專案總管) 是深入探討 Windows Mixed Reality 視線相關概念。 我們將新增內容感知到我們的資料指標和全像投影，充分利用您的應用程式知道使用者的視線有關。

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

我們必須易記太空人這裡幫助您了解視線概念。 在  [MR 基本概念 101](holograms-101.md)，我們只是後接您的視線簡單資料指標。 今天我們要移動的簡單資料指標的後續步驟：

* 我們將會讓資料指標而且我們全像投影視線注意： 同時會隨著使用者注視的位置-，或使用者所在*不*尋找。 這讓它們更能感知環境。
* 我們會將我們的資料指標和全像投影至多個內容上所設定的目標是授與使用者意見反應。 此意見反應可以音訊和視覺化。
* 我們將示範您目標的技術，可協助使用者點擊較小的目標。
* 我們將示範如何強調使用者的您具有方向性指標全像投影。
* 我們會教導您全像投影需要與使用者，因為她在您的世界中移動的技術。

>[!IMPORTANT]
>使用 Unity 及混合實境 toolkit 的推出較舊的版本記錄中的下列章節的每個內嵌的影片。 雖然的逐步指示是準確且即時的您可能會看到指令碼和對應已過期的影片中的視覺效果。 影片仍包含 posterity，和因為概念涵蓋仍然適用。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 輸入 210:注視</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

* Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。
* 基本C#程式設計的能力。
* 您應已完成[MR 基本概念 101](holograms-101.md)。
* HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>專案檔

* 下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)專案所需。 需要 Unity 2017.2 或更新版本。
* 取消封存您的桌面或其他您輕鬆地連線到位置的檔案。

>[!NOTE]
>如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)。

### <a name="errata-and-notes"></a>偵錯 errata 和附註

* 在 Visual Studio 中，Just My Code 必須是停用 （未核取） 在 工具-> 選項-> 若要在程式碼中設定中斷點的偵錯。

## <a name="chapter-1---unity-setup"></a>第 1 章-Unity 安裝

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>目標

* 最佳化 HoloLens 開發 Unity。
* 匯入資產，並設定場景。
* 檢視太空人 HoloLens。

### <a name="instructions"></a>指示

1. 啟動 Unity。
2. 選取 **新的專案**。
3. 將專案命名為**ModelExplorer**。
4. 輸入與位置**視線**資料夾您先前未封存。
5. 請確定專案已設定為**3D**。
6. 按一下 **建立專案**。

### <a name="unity-settings-for-hololens"></a>HoloLens 的 unity 設定

我們需要讓知道我們嘗試匯出的應用程式應該建立 Unity[沈浸式檢視](app-views.md)而不是 2D 檢視。 我們的做法是將做為虛擬實境裝置的 HoloLens。

1. 移至**編輯 > 專案設定 > Player**。
2. 在 [**偵測器] 面板**播放程式設定中，選取**Windows 市集**圖示。
3. 依序展開**XR 設定**群組。
4. 在 **轉譯**區段中，按一下**虛擬實境支援**核取方塊以加入新**虛擬實境 Sdk**清單。
5. 確認**Windows Mixed Reality**出現在清單中。 如果沒有，請選取**+** 按鈕在清單底部，然後選擇**Windows 全像攝影版**。

接下來，我們需要將我們指令碼的後端設定為.NET。

1. 移至**編輯 > 專案設定 > Player** （您可能仍有這在上一個步驟）。
2. 在 [**偵測器] 面板**播放程式設定中，選取**Windows 市集**圖示。
3. 在 **其他設定**組態區段中，請確定**指令碼的後端**設定為 **.NET**

最後，我們會更新我們的品質設定，以達到 HoloLens 上快速的效能。

1. 移至**編輯 > 專案設定 > 品質**。
2. 按一下向下鍵在**預設**在 Windows 市集圖示的資料列。
3. 選取 **非常低**for **Windows 市集應用程式**。

### <a name="import-project-assets"></a>匯入專案資產

1. 以滑鼠右鍵按一下**資產**中的資料夾**專案**面板。
2. 按一下 **匯入封裝 > 自訂套件**。
3. 瀏覽至您下載的專案檔案，然後按一下**ModelExplorer.unitypackage**。
4. 按一下 [開啟] 。
5. 封裝載入之後，請按一下**匯入** 按鈕。

### <a name="setup-the-scene"></a>設定場景

1. 在階層中，刪除**Main Camera**。
2. 在  **HoloToolkit**資料夾中，開啟**輸入**資料夾，然後開啟**Prefabs**資料夾。
3. 將拖放**MixedRealityCameraParent** prefab 來自**Prefabs**資料夾**階層**。
4. 以滑鼠右鍵按一下**定向光線**階層，然後選取**刪除**。
5. 在 **全像投影**資料夾中，拖放的根目錄中的下列資產**階層**:
    * **AstroMan**
    * **號誌**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. 開始**播放模式**檢視太空人 ▶。
7. 按一下 **播放模式**▶ 一次，若要**停止**。
8. 在 **全像投影**資料夾中，尋找**Fitbox**資產並將它拖曳到的根目錄**階層**。
9. 選取  **Fitbox**中**階層**面板。
10. 拖曳**AstroMan**從集合**階層**來**闀集合**屬性中 Fitbox **Inspector**面板。

### <a name="save-the-project"></a>儲存專案

1. 儲存新的場景：**檔案 > 儲存為場景**。
2. 按一下 **新的資料夾**並將資料夾命名**場景**。
3. 將檔案命名為"**ModelExplorer**"並將它儲存在**場景**資料夾。

### <a name="build-the-project"></a>建置專案

1. 在 Unity 中，選取**檔案 > 組建設定**。
2. 按一下 **加入開啟的場景**加入場景。
3. 選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。
4. 如果您要特別開發的 HoloLens，設定**目標裝置**要**HoloLens**。 否則，將它保留在**任何裝置**。
5. 確保**建置型別**設為**D3D**並**SDK**設定為**最新安裝**（這應該可以 16299 或更新版本的 SDK）。
6. 按一下 [建置] 。
7. 建立**新的資料夾**名為 「 應用程式 」。
8. 只要按一下**應用程式**資料夾。
9. 按下**選取資料夾**。

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

## <a name="chapter-2---cursor-and-target-feedback"></a>第 2 章-資料指標和目標的意見反應

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>目標

* 資料指標的視覺化設計和行為。
* 視線為基礎的資料指標的意見反應。
* 視線型全像意見反應。

我們將努力根據部分的資料指標設計原則，也就是：

* 資料指標一律會出現。
* 不要讓取得太小或最大的資料指標。
* 避免阻礙內容。

### <a name="instructions"></a>指示

1. 在  **HoloToolkit\Input\Prefabs**資料夾中，尋找**InputManager**資產。
2. 將拖放**InputManager**拖曳至**階層**。
3. 在  **HoloToolkit\Input\Prefabs**資料夾中，尋找**游標**資產。
4. 將拖放**游標**拖曳至**階層**。
5. 選取  **InputManager**物件中**階層**。
6. 拖曳**游標**物件**階層**到 InputManager **SimpleSinglePointerSelector**的**游標**欄位中，在底部**Inspector**。

![簡單的單一指標選取器設定](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>建置和部署

1. 重建的應用程式**檔案 > 組建設定**。
2. 開啟**應用程式資料夾**。
3. 開啟**ModelExplorer Visual Studio 解決方案**。
4. 按一下 **偵錯-> 啟動但不偵錯**或按**Ctrl + F5**。
5. 觀察資料指標的繪製方式及其如何變更外觀如果雷射筆碰觸。

### <a name="instructions"></a>指示

1. 在 [**階層**] 面板中，展開**AstroMan**->**GEO_G**->**Back_Center**物件。
2. 按兩下**Interactible.cs**在 Visual Studio 中開啟它。
3. 中的行取消註解**IFocusable.OnFocusEnter()** 並**IFocusable.OnFocusExit()** 中的回呼**Interactible.cs**。 （或視線控制器指） 焦點進入和離開特定的 GameObject collider 時，這些是由混合實境工具組的 InputManager 進行呼叫。

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>我們會使用`EnableKeyword`和`DisableKeyword`上方。 為了讓使用您自己的應用程式與工具組的標準著色器中，您必須遵循[Unity 指導方針，以存取透過指令碼的教材](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。 在此情況下，我們已加入[反白顯示資料的三種變化](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)需要 （尋找反白顯示的名稱中使用的三個資料） 中的 [資源] 資料夾中。

### <a name="build-and-deploy"></a>建置和部署

1. 同樣地，建置專案，並將部署到 HoloLens。
2. 觀察視線旨在物件時，會發生什麼事並不是。

## <a name="chapter-3---targeting-techniques"></a>第 3 章-為目標的技術

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>目標

* 讓您更輕鬆地目標全像投影。
* 穩固自然前端的移動。

### <a name="instructions"></a>指示

1. 在 **階層**面板中，選取**InputManager**物件。
2. 在 [ **Inspector** ] 面板中，尋找**視線對**指令碼。 如果您想要看，請按一下以在 Visual Studio 中開啟。
    * 此指令碼會逐一查看 Raycast 資料的範例，並協助穩定的有效位數為目標的使用者的視線。
3. 在  **Inspector**，您可以編輯**儲存穩定性範例**值。 這個值表示對會逐一查看直到計算穩定的值的樣本數目。

## <a name="chapter-4---directional-indicator"></a>第 4 章-方向性指標

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>目標

* 新增資料指標以協助找出全像投影的方向性指標。

### <a name="instructions"></a>指示

我們將使用**DirectionIndicator.cs**檔案將會：

1. 如果使用者不會 gazing 在全像投影的情況下顯示方向性指標。
2. 如果使用者 gazing 在全像投影，請隱藏方向性指標。
3. 更新為指向全像投影的方向性指標。

那就開始吧。

1. 按一下**AstroMan**物件中**階層**面板並**按一下箭號**加以展開。
2. 在 **階層**面板中，選取**DirectionalIndicator**物件下**AstroMan**。
3. 在  **Inspector**  面板中，按一下**新增元件** 按鈕。
4. 在功能表中，輸入在搜尋方塊**方向指標**。 選取搜尋結果。
5. 中**階層** 面板、 拖曳和卸除**游標**物件拖曳至**游標**中的屬性**Inspector**。
6. 在 [**專案**] 面板的**全像投影**資料夾、 拖放**DirectionalIndicator**拖曳至資產**方向性指標**中的屬性**Inspector**。
7. 建置及部署應用程式。
8. 觀看方向性指標物件如何協助您找出太空人。

## <a name="chapter-5---billboarding"></a>第 5 章-告示板

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>目標

* 使用告示板，讓全像投影一律面臨朝向您。

我們將使用**Billboard.cs**檔案以保留導向，使其面向使用者隨時 GameObject。

1. 在 **階層**面板中，選取**AstroMan**物件。
2. 在  **Inspector**  面板中，按一下**新增元件** 按鈕。
3. 在功能表中，輸入在搜尋方塊**告示板**。 選取搜尋結果。
4. 在  **Inspector**設定**Pivot Axis**來**Y**。
5. 試試看！ 建置並部署為應用程式之前。
6. 請參閱如何告示板物件也會等您不論您如何變更觀點來看。
7. 刪除從指令碼**AstroMan**現在。

## <a name="chapter-6---tag-along"></a>第 6 章-Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>目標

* 您可以使用 Tag-Along，讓我們全像投影房間周圍關注我們。

當我們處理此問題，我們將會引導您藉由下列的設計限制：

* 內容應該總是一目瞭然消失。
* 內容不應方式。
* Head 鎖定的內容時感到不舒服。

這裡使用的解決方案是使用 「 tag-along"的方法。

Tag-along 物件永遠不會完整保留使用者的檢視。 您可以將 tag-along 視為物件附加至使用者的大腦拖放群組列。 當使用者移動，內容會維持內輕鬆瀏覽，而不需要完全離開滑動朝向檢視的邊緣。 當使用者 gazes 朝向 tag-along 物件時，它進入更完整檢視。

我們將使用**SimpleTagalong.cs**檔案將會：

1. 判斷 Tag-Along 物件是否相機的範圍內。
2. 如果沒有檢視範圍內的位置來 Tag-Along，部分在檢視範圍內。
3. 從使用者的預設距離，否則為位置 Tag-Along。

若要這樣做，我們首先必須變更**Interactible.cs**指令碼來呼叫**TagalongAction**。

1. 編輯**Interactible.cs**完成程式碼撰寫練習 6.a （取消註解線條 84 到 87）。

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

**InteractibleAction.cs**指令碼，搭配**Interactible.cs**執行自訂動作，當您點選 全像投影。 在此情況下，我們將使用其中一個專為 tag-along。

* 在 **指令碼**資料夾中的，按一下  **TagalongAction.cs**資產在 Visual Studio 中開啟。
* 完成程式碼撰寫練習，或將其變更如下：
  * 在頂端**階層**，在搜尋列中輸入**ChestButton_Center**和選取的結果。
  * 在  **Inspector**  面板中，按一下**新增元件** 按鈕。
  * 在功能表中，輸入在搜尋方塊**Tagalong 動作**。 選取搜尋結果。
  * 在 [**全像投影**] 資料夾尋找**Tagalong**資產。
  * 選取  **ChestButton_Center**物件中**階層**。 將拖放**TagAlong**物件**專案**面板拖曳至**Inspector**成**物件至 Tagalong**屬性。
  * 拖曳**Tagalong 動作**物件**Inspector**成**Interactible 動作**欄位**Interactible**指令碼。
* 按兩下**TagalongAction**指令碼，以在 Visual Studio 中開啟它。

![Interactible 設定](images/holograms210-interactible.png)

我們需要加入下列程式碼：

* 將功能加入 PerformAction 函式 （繼承自 InteractibleAction） TagalongAction 指令碼中。
* 告示板 gazed 基礎物件，加上 pivot axis 設 XY 散佈圖。
* 然後新增至物件的簡單 Tag-Along。

以下是我們的解決方案，從**TagalongAction.cs**:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* 試試看！ 建置及部署應用程式。
* 觀看如何的內容會遵循中心的視線點，但不是持續，而不會封鎖它。
