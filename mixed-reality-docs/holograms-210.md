---
title: MR 輸入 210-注視
description: 請遵循使用 Unity、Visual Studio 和 HoloLens 進行的編碼逐步解說，以深入瞭解看看概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，學院，教學課程，注視
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434689"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。

# <a name="mr-input-210-gaze"></a>MR 輸入210：注視

[注視](gaze-and-commit.md)是第一種形式的輸入，並顯示使用者的意圖和認知。 MR Input 210 （也稱為 Project Explorer）是深入探討 Windows Mixed Reality 的注視相關概念。 我們將會對游標和全息影像新增內容感知，並充分利用您的應用程式對使用者注視的認識。

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

這裡有一個很好用的太空人，可協助您瞭解一些概念。 在[MR 基本概念 101](holograms-101.md)中，我們有一個簡單的游標，只是看著您的注視。 今天，我們要將一個步驟移到簡單的資料指標之外：

* 我們會讓游標和我們的全息影像看起來很清楚：兩者都會根據使用者的外觀，或使用者*不*在尋找的位置而變更。 這可讓他們瞭解內容。
* 我們會將意見反應新增至游標和全息影像，以提供使用者更多有關目標的內容。 此意見反應可以是音訊和視覺效果。
* 我們將示範如何以協助使用者達到較小目標的技術為目標。
* 我們將示範如何使用方向指標，將使用者的注意力繪製到您的全息影像。
* 我們會告訴您，您可以在世界各地移動您的全息和使用者。

>[!IMPORTANT]
>下列各章節所內嵌的影片，都是使用舊版 Unity 和混合現實工具組錄製的。 雖然逐步指示是正確且最新的，但您可能會在已過期的對應影片中看到腳本和視覺效果。 影片仍包含在 posterity 中，因為涵蓋的概念仍適用。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 輸入210：注視</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

* [已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。
* 一些基本C#的程式設計能力。
* 您應已完成[MR 基本概念 101](holograms-101.md)。
* [為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔案

* 下載專案[所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)檔案。 需要 Unity 2017.2 或更新版本。
* 將檔案取消封存至您的桌面或其他容易到達的位置。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼，可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)取得。

### <a name="errata-and-notes"></a>勘誤和注意事項

* 在 Visual Studio 中，必須停用（取消核取） [工具-> 選項] 下 > 的 [Just My Code]，才能在程式碼中叫用中斷點。

## <a name="chapter-1---unity-setup"></a>第1章-Unity 設定

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>目標

* 最佳化 Unity 以用於 HoloLens 開發。
* 匯入資產並設定場景。
* 查看 HoloLens 中的太空人。

### <a name="instructions"></a>指示

1. 啟動 Unity。
2. 選取 [**新增專案**]。
3. 將專案命名為**ModelExplorer**。
4. 輸入 [位置] 作為您先前取消封存的 [**注視**] 資料夾。
5. 確定專案已設定為 **3D**。
6. 按一下 [建立專案]。

### <a name="unity-settings-for-hololens"></a>HoloLens 的 Unity 設定

我們需要讓 Unity 知道，我們嘗試匯出的應用程式應該建立[沉浸式視圖](app-views.md)，而不是2d 視圖。 我們的作法是將 HoloLens 新增為虛擬實境裝置。

1. 移至 **編輯 > 專案設定 > Player**。
2. 在 [玩家設定] 的 [偵測**器] 面板**中，選取 [ **Windows Store** ] 圖示。
3. 展開 [ **XR 設定**] 群組。
4. **在轉譯區段中**，勾選 [**支援虛擬實境**] 核取方塊，以新增**虛擬實境 sdk**清單。
5. 確認清單中出現**Windows Mixed Reality** 。 如果沒有，請選取清單底部的 [ **+** ] 按鈕，然後選擇 [ **Windows**全像]。

接下來，我們需要將腳本後端設定為 .NET。

1. 移至 **編輯 > 專案設定 > 播放** （您在上一個步驟中可能還是會這麼做）。
2. 在 [玩家設定] 的 [偵測**器] 面板**中，選取 [ **Windows Store** ] 圖示。
3. 在 [**其他設定**] 區段中，確認 [**腳本後端**] 已設定為 [ **.net** ]

最後，我們會更新我們的品質設定，以在 HoloLens 上達到快速的效能。

1. 移至 **編輯 > 專案設定 > 品質**。
2. 在 Windows 市集中圖示底下的**預設**資料列中，按一下向下箭號。
3. 對於**Windows Store 應用程式**，請選取 [**非常低**]。

### <a name="import-project-assets"></a>匯入專案資產

1. 在 [**專案**] 面板中，以滑鼠右鍵按一下 [**資產**] 資料夾。
2. 按一下 [匯**入封裝 > 自訂套件**]。
3. 流覽至您所下載的專案檔，然後按一下 [ **ModelExplorer unitypackage**]。
4. 按一下 **\[開啟\]** 。
5. 封裝載入之後，按一下 [匯**入**] 按鈕。

### <a name="setup-the-scene"></a>設定場景

1. 在階層中，刪除**主要相機**。
2. 在**HoloToolkit**資料夾中，開啟 [**輸入**] 資料夾，然後開啟 [ **Prefabs** ] 資料夾。
3. 將**MixedRealityCameraParent** Prefab 從**Prefabs**資料夾拖**放到階層中。**
4. 以滑鼠右鍵按一下階層中的 [**方向光源**]，然後選取 [**刪除**]。
5. 在 [**全息影像**] 資料夾中，將下列資產拖放到**階層的根目錄中：**
    * **AstroMan**
    * **無**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. 啟動**播放模式**▶以觀看太空人。
7. 再次按一下 [**播放模式]** ▶**停止**。
8. 在 [**全息影像**] 資料夾中，尋找**Fitbox**資產，並將它拖曳到**階層的根目錄。**
9. **在 [階層**] 面板中選取**Fitbox** 。
10. 從階層中，將**AstroMan**集合**拖曳至 [** 偵測**器**] 面板中 Fitbox 的 [**全息影像集合**] 屬性。

### <a name="save-the-project"></a>儲存專案

1. 儲存新場景：檔案 **> 另存場景**。
2. 按一下 [**新增資料夾**]，並將資料夾命名為**場景**。
3. 將檔案命名為 "**ModelExplorer**"，並將它儲存在 [**幕後**] 資料夾中。

### <a name="build-the-project"></a>建立專案

1. 在 Unity 中，選取 [檔案] **> [組建設定**]。
2. 按一下 [新增] [**開啟場景**] 以加入場景。
3. 在 [**平臺**] 清單中選取**通用 Windows 平臺**，然後按一下 [**切換平臺**]。
4. 如果您是特別針對 HoloLens 進行開發，請將**目標裝置**設定為**hololens**。 否則，請將它保留在**任何裝置**上。
5. 確定 [**組建類型**] 設定為 [ **D3D** ]，並將 [ **sdk** ] 設定為 [**已安裝最新**版本] （應該是 SDK 16299 或更新版本）。
6. 按一下 [建置]。
7. 建立名為 "App" 的**新資料夾**。
8. 按一下 [**應用程式**] 資料夾。
9. 按 [**選取資料夾**]。

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

## <a name="chapter-2---cursor-and-target-feedback"></a>第2章-資料指標和目標意見反應

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>目標

* 游標視覺化設計和行為。
* 注視游標的意見反應。
* 以注視式的全息影像意見反應。

我們將根據一些資料指標設計原則來進行工作，也就是：

* 資料指標一律存在。
* 不要讓游標變得太小或太大。
* 避免阻礙內容。

### <a name="instructions"></a>指示

1. 在**HoloToolkit\Input\Prefabs**資料夾中，尋找**InputManager**資產。
2. 將**InputManager**拖**放到階層上。**
3. 在**HoloToolkit\Input\Prefabs**資料夾中，尋找資料**指標**資產。
4. 將**游標**拖**放到階層上。**
5. 選取階層中的 [ **InputManager** ]**物件。**
6. 將**游標**物件從階層拖曳**至 InputManager**的**SimpleSinglePointerSelector**的資料**指標**欄位（位於偵測**器**底部）。

![簡單單一指標選取器設定](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>組建和部署

1. 從 [檔案] **> 組建設定**重建應用程式。
2. 開啟**應用程式資料夾**。
3. 開啟**ModelExplorer Visual Studio 解決方案**。
4. 按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。
5. 觀察游標的繪製方式，以及它在觸及全息圖形時如何變更外觀。

### <a name="instructions"></a>指示

1. **在 [階層**] 面板中，展開 [ **AstroMan**->**GEO_G**->**Back_Center**物件]。
2. 按兩下 [ **Interactible.cs** ]，在 Visual Studio 中開啟它。
3. 取消批註**Interactible.cs**中**IFocusable. OnFocusEnter （）** 和**IFocusable OnFocusExit （）** 回呼中的行。 當焦點（由注視或控制器指向）進入並結束特定 GameObject 的碰撞器時，混合現實工具組的 InputManager 會呼叫這些方法。

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
>我們使用上述 `EnableKeyword` 和 `DisableKeyword`。 為了在您自己的應用程式中搭配使用工具組的標準著色器，您必須遵循[Unity 指導方針，透過腳本存取材質](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。 在此情況下，我們已包含 [資源] 資料夾中所需反[白顯示材質的三種](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)變化（尋找名稱中有醒目提示的三個數據）。

### <a name="build-and-deploy"></a>組建和部署

1. 如先前所述，建立專案並部署至 HoloLens。
2. 觀察當注視物件導向時所發生的情況，以及不是什麼時候。

## <a name="chapter-3---targeting-techniques"></a>第3章-目標技術

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>目標

* 讓您更輕鬆地以全息影像為目標。
* 穩定的自然 head 移動。

### <a name="instructions"></a>指示

1. **在 [階層**] 面板中，選取 [ **InputManager** ] 物件。
2. 在 [偵測**器**] 面板中，尋找**注視的穩定**器腳本。 如果您想要查看，請按一下該檔案以在 Visual Studio 中開啟。
    * 此腳本會逐一查看 Raycast 資料的樣本，並協助將使用者的注視變得穩定，以達到精確目標。
3. 在偵測**器**中，您可以編輯**儲存的穩定性範例**值。 此值表示穩定程式會逐一查看以計算穩定值的樣本數。

## <a name="chapter-4---directional-indicator"></a>第4章-方向指標

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>目標

* 在游標上新增方向指標，以協助找出全息影像。

### <a name="instructions"></a>指示

我們將使用**DirectionIndicator.cs**檔案，它會：

1. 如果未在全息影像中撥雲見日使用者，則顯示方向指標。
2. 如果在全息影像中撥雲見日使用者，則隱藏方向指標。
3. 更新方向指標以指向全息影像。

那就開始吧。

1. 按一下 **[階層] 面板中**的 [ **AstroMan** ] 物件，然後**按一下箭**號將它展開。
2. 在 [**階層**] 面板中，選取 [ **AstroMan**] 下的 [ **DirectionalIndicator** ] 物件。
3. 在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。
4. 在功能表中，于搜尋方塊**方向指標**上輸入。 選取搜尋結果。
5. **在 [階層] 面板中**，將**游標**物件拖放至偵測**器**中的**cursor**屬性。
6. 在 [**專案**] 面板的 [**全息影像**] 資料夾中，將**DirectionalIndicator**資產拖放至偵測**器**中的**方向指標**屬性。
7. 建立並部署應用程式。
8. 觀看方向指標物件如何協助您尋找太空人。

## <a name="chapter-5---billboarding"></a>第5章-Billboarding

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>目標

* 使用 billboarding 讓全像投影永遠都能朝向您的臉。

我們將使用**Billboard.cs**檔案來保留 GameObject 導向，使其隨時面向使用者。

1. **在 [階層**] 面板中，選取 [ **AstroMan** ] 物件。
2. 在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。
3. 在功能表中，于搜尋方塊中輸入**佈告欄**。 選取搜尋結果。
4. 在 [偵測**器**] 中，將 [ **Pivot 軸**] 設定為**Y**。
5. 試試看！ 如先前一樣，建立和部署應用程式。
6. 無論您如何改變觀點，都能瞭解佈告欄物件的外觀。
7. 立即從**AstroMan**刪除腳本。

## <a name="chapter-6---tag-along"></a>第6章-標記-沿著

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>目標

* 使用標籤-並讓我們的全息影像沿著我們的房間來追蹤。

當我們處理這個問題時，我們會依照下列設計條件約束來引導我們：

* 內容應該一律一目了然。
* 內容不應為該方式。
* Head 鎖定內容不舒服。

此處使用的解決方案是使用「標記為一」的方法。

標記物件永遠不會完全離開使用者的觀點。 您可以將一個標記視為一個物件，並將它與使用者的標頭連接在一起。 當使用者移動時，內容會透過滑動到視野的邊緣而不會完全離開，而保持在簡單概覽。 當使用者 gazes 到標記物件時，它會有更完整的視野。

我們將使用**SimpleTagalong.cs**檔案，它會：

1. 判斷標記沿著的物件是否在相機界限內。
2. 如果不在視圖的 [截位] 中，請將標記放在視圖的 [截維] 內。
3. 否則，請將標記與使用者的預設距離放置在一起。

若要這麼做，我們必須先變更**Interactible.cs**腳本以呼叫**TagalongAction**。

1. 完成程式碼撰寫練習 6. （取消批註行84到87）來編輯**Interactible.cs** 。

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

當您按一下全息影像時，與**Interactible.cs**配對的**InteractibleAction.cs**腳本會執行自訂動作。 在此情況下，我們會使用特別用於標記的一個。

* 在 [**腳本**] 資料夾中，按一下 [ **TagalongAction.cs**資產] 以在 Visual Studio 中開啟。
* 完成程式碼撰寫練習，或將它變更為：
  * 在階層頂端的 [搜尋] 列**中，輸入** **ChestButton_Center**並選取結果。
  * 在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。
  * 在功能表中，于 [搜尋] 方塊中輸入**Tagalong 動作**。 選取搜尋結果。
  * 在 [**全息影像**] 資料夾中，尋找**Tagalong**資產。
  * 選取階層中的 [ **ChestButton_Center** ]**物件。** 從 [**專案**] 面板中，將**TagAlong**物件拖放**到 [** **要 TagAlong 的物件**] 屬性中。
  * 將 [ **Tagalong 動作**] 物件從 [偵測**器**] 拖曳至**Interactible**腳本上的 [ **Interactible 動作**] 欄位中。
* 按兩下 [ **TagalongAction** ] 腳本，在 Visual Studio 中開啟它。

![Interactible 設定](images/holograms210-interactible.png)

我們需要新增下列內容：

* 將功能新增至 TagalongAction 腳本中的 PerformAction 函數（繼承自 InteractibleAction）。
* 將 billboarding 新增至 gazed 物件，並將 pivot 軸設定為 [XY]。
* 然後將簡單的標記新增至物件。

以下是來自**TagalongAction.cs**的解決方案：

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

* 試試看！ 建立並部署應用程式。
* 監看內容在注視點的中心，但不會持續且不會封鎖。
