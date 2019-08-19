---
title: MR 分享 240-多個 HoloLens 裝置
description: 請遵循使用 Unity、Visual Studio 和 HoloLens 進行的編碼逐步解說, 以瞭解共用全息影像的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 共用, 網路, 學院, 教學課程
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522337"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。  因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊, 以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時, 使用這些教學課程的連結進行更新。

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR 分享 240:多個 HoloLens 裝置

在我們的世界中, 當我們在空間上移動時, 會將全像投影。 HoloLens 會藉由使用各種[座標系統](coordinate-systems.md)來追蹤物件的位置和方向, 以保持全息。 當我們在裝置之間共用這些座標系統時, 我們可以建立共用體驗, 讓我們參與共用的全像世界。

在本教學課程中, 我們將:

* 設定共用體驗的網路。
* 跨 HoloLens 裝置共用全息影像。
* 探索我們分享的全像世界中的其他人。
* 建立可讓您以其他玩家為目標並啟動炮彈的共用互動式體驗!

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 分享 240:多個 HoloLens 裝置</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

* 以網際網路存取所安裝的正確[工具](install-the-tools.md)設定的 WINDOWS 10 電腦。
* 至少有兩個[設定為開發的](using-visual-studio.md#enabling-developer-mode)HoloLens 裝置。

### <a name="project-files"></a>專案檔案

* 下載專案所需的[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。
  * 如果您仍然需要 Unity 5.5 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。
  * 如果您仍然需要 Unity 5.4 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。
* 將檔案取消封存至您的桌面或其他容易到達的位置。 將資料夾名稱保留為**SharedHolograms**。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼, 可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)取得。

## <a name="chapter-1---holo-world"></a>第1章-Hololens 世界

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

在本章中, 我們將設定第一個 Unity 專案, 並逐步執行組建和部署流程。

### <a name="objectives"></a>目標

* 設定 Unity 以開發全像攝影應用程式。
* 查看您的全息影像!

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 [**開啟**]。
* 輸入 location 作為您先前 unarchived 的**SharedHolograms**資料夾。
* 選取 [**專案名稱**], 然後按一下 [**選取資料夾**]。
* 在階層中, 以滑鼠右鍵按一下**主要相機**, 然後選取 [**刪除**]。
* 在 [ **HoloToolkit-共用-240/Prefabs/攝影機**] 資料夾中, 尋找**主要相機**prefab。
* 將**主要相機**拖放到階層中。
* 在階層中, 按一下 [**建立**] 並**建立空**的。
* 以滑鼠右鍵按一下新的**GameObject** , 然後選取 [**重新命名**]。
* 將 GameObject 重新命名為**HologramCollection**。
* 選取階層中的 [ **HologramCollection** ] 物件。
* 在偵測**器**中, 將**轉換位置**設定為:**X0, Y:-0.25, Z:2**。
* 在 [**專案] 面板**的 [**全息影像**] 資料夾中, 尋找**EnergyHub**資產。
* 將**EnergyHub**物件從 [**專案] 面板**拖放至階層 , 做為**HologramCollection 的子**系。
* 選取 [檔案] **> 另存場景**。
* 將場景命名為**SharedHolograms** , 然後按一下 [**儲存**]。
* 按下 Unity 中的 [**播放**] 按鈕, 以預覽您的全息影像。
* 按第二次 [**播放**] 以停止預覽模式。

**將專案從 Unity 匯出至 Visual Studio**
* 在 Unity 中, 選取 檔案 **> 組建設定**。
* 按一下 [新增] [**開啟場景**] 以加入場景。
* 在 [**平臺**] 清單中選取**通用 Windows 平臺**, 然後按一下 [**切換平臺**]。
* 將**SDK**設定為**通用 10**。
* 將 [**目標裝置**] 設定為**HoloLens** , 將**UWP 組建類型**設為 [ **D3D**]。
* 檢查**Unity C#專案**。
* 按一下 [建置]。
* 在出現的 [檔案瀏覽器] 視窗中, 建立名為 "App" 的**新資料夾**。
* 按一下 [**應用程式**] 資料夾。
* 按 [**選取資料夾**]。
* 當 Unity 完成時, 將會出現 [檔案瀏覽器] 視窗。
* 開啟**應用程式**資料夾。
* 開啟**SharedHolograms**以啟動 Visual Studio。
* 使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**X86**。
* 按一下 [本機電腦] 旁的下拉式箭號, 然後選取 [**遠端裝置**]。
    * 將**位址**設定為 HoloLens 的名稱或 IP 位址。 如果您不知道您的裝置 IP 位址, 請查看 [**設定] > 網路 & [網際網路] > [Advanced Options** **] 或 [你好 cortana, 我的 IP 位址是什麼？]**
    * 將 [**驗證模式]** 保持設定為 [**通用**]。
    * 按一下 [**選取**]
* 按一下 [ **Debug > 啟動但不進行調試**] 或按**Ctrl + F5**。 如果這是您第一次部署至您的裝置, 您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device-hololens)。
* 放入 HoloLens 並尋找 EnergyHub 的全息影像。

## <a name="chapter-2---interaction"></a>第2章-互動

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

在本章中, 我們將與我們的全息影像互動。 首先, 我們要新增游標來視覺化我們的[注視](gaze.md)。 然後, 我們將新增[手勢](gestures.md), 並使用我們的手將全息影像放在空間中。

### <a name="objectives"></a>目標

* 使用注視輸入來控制資料指標。
* 使用手勢輸入來與全息影像互動。

### <a name="instructions"></a>指示

**目光**
* 在 [階層]**面板**中, 選取 [ **HologramCollection** ] 物件。
* 在 [偵測**器] 面板**中, 按一下 [**加入元件**] 按鈕。
* 在功能表中, 在搜尋方塊中輸入 [**注視管理員**]。 選取搜尋結果。
* 在**HoloToolkit-Sharing-240\Prefabs\Input**資料夾中, 尋找資料**指標**資產。
* 將**游標**資產拖放到階層上。

**#**
* 在 [階層]**面板**中, 選取 [ **HologramCollection** ] 物件。
* 按一下 [**新增元件**], 然後在 [搜尋] 欄位中輸入**手勢管理員**。 選取搜尋結果。
* 在 [階層]**面板**中, 展開 [ **HologramCollection**]。
* 選取子**EnergyHub**物件。
* 在 [偵測**器] 面板**中, 按一下 [**加入元件**] 按鈕。
* 在功能表中, 于 [搜尋] 方塊中輸入「**全息影像」位置**。 選取搜尋結果。
* 選取 [檔案] **> 儲存場景**, 以儲存場景。

**部署和享用**
* 使用上一章中的指示, 建立並部署至您的 HoloLens。
* 一旦應用程式在您的 HoloLens 上啟動, 請移動您的頭部, 並留意 EnergyHub 如何遵循您的注視。
* 請注意, 當您注視全息的全像投影時, 游標會如何顯示, 而不會在全息的撥雲見日時, 會變更為點光線。
* 執行 [空中] 以放置全息影像。 在我們的專案中, 您目前只能放置全息影像一次 (重新部署以重試)。

## <a name="chapter-3---shared-coordinates"></a>第3章-共用座標

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

查看和與全息影像互動很有趣, 但讓我們繼續進行。 我們會設定我們的第一個共用體驗-每個人都可以一起查看的全息影像。

### <a name="objectives"></a>目標

* 設定共用體驗的網路。
* 建立通用參考點。
* 跨裝置共用座標系統。
* 每個人都看到相同的全息影像!

>[!NOTE]
>必須為應用程式宣告**InternetClientServer**和**PrivateNetworkClientServer**功能, 才能連接到共用伺服器。 這是針對您已在全息記錄240中完成的作業, 但請記住您自己的專案。
>1. 在 Unity 編輯器中, 流覽至 [編輯 > 專案設定 > Player], 移至播放程式設定
>2. 按一下 [Windows Store] 索引標籤
>3. 在 [發佈設定 > 功能] 區段中, 檢查**InternetClientServer**功能和**PrivateNetworkClientServer**功能

### <a name="instructions"></a>指示

* 在 [**專案] 面板**中, 流覽至 [ **HoloToolkit-Sharing-240\Prefabs\Sharing** ] 資料夾。
* 將**共用**prefab 拖放到 [階層]**面板**中。

接下來, 我們需要啟動共用服務。 只有**一部電腦**在共用體驗中, 才需要執行此步驟。
* 在 Unity-在頂端功能表中, 選取 [ **HoloToolkit-共用-240] 功能表**。
* 在下拉式選單中, 選取 [**啟動共用服務**] 專案。
* 核取 [**私人網路**] 選項, 然後在出現防火牆提示時, 按一下 [**允許存取**]。
* 記下 [共用服務主控台] 視窗中顯示的 IPv4 位址。 這是與執行服務的電腦相同的 IP。

遵循將加入共用體驗的**所有電腦**上的其餘指示。
* 在 [階層] 中, 選取 [**共用**] 物件。
* 在偵測**器**的**共用階段**元件上, 將**伺服器位址**從 ' localhost ' 變更為執行 SharingService 之電腦的 IPv4 位址。
* 在階層中選取 [ **HologramCollection** ] 物件。
* 在偵測**器**中, 按一下 [**加入元件**] 按鈕。
* 在搜尋方塊中, 輸入匯**入匯出錨點管理員**。 選取搜尋結果。
* 在 [**專案] 面板**中, 流覽至 [**腳本**] 資料夾。
* 按兩下 [ **HologramPlacement** ] 腳本, 在 Visual Studio 中開啟它。
* 將內容取代為下列程式碼。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* 回到 Unity, 選取 [階層]**面板**中的 [ **HologramCollection** ]。
* 在 [偵測**器] 面板**中, 按一下 [**加入元件**] 按鈕。
* 在功能表中, 于 [搜尋] 方塊中輸入 [**應用程式狀態管理員**]。 選取搜尋結果。

**部署和享用**
* 建立 HoloLens 裝置的專案。
* 指定一個要先部署的 HoloLens。 您必須等到將錨點上傳至服務, 才能放置 EnergyHub (這可能需要 ~ 30-60 秒)。 完成上傳之前, 會忽略您的點按手勢。
* 放置 EnergyHub 之後, 其位置將會上傳至服務, 然後您就可以部署到其他所有的 HoloLens 裝置。
* 當新的 HoloLens 第一次加入會話時, EnergyHub 在該裝置上的位置可能不正確。 不過, 一旦從服務下載錨點和 EnergyHub 位置, EnergyHub 應該會跳至新的共用位置。 如果這不是在 ~ 30-60 秒內發生, 請在設定錨點以收集更多的環境線索時, 逐步執行原始 HoloLens 的位置。 如果位置仍未鎖定, 請重新部署至裝置。
* 當裝置已準備就緒且正在執行應用程式時, 請尋找 EnergyHub。 您是否同意全像投影的位置, 以及文字所面向的方向為何？

## <a name="chapter-4---discovery"></a>第4章-探索

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

所有人現在都可以看到相同的全息影像! 現在讓我們看看其他人連線到我們分享的全像世界。 在本章中, 我們將在相同的共用會話中抓取所有其他 HoloLens 裝置的頭位置和旋轉。

### <a name="objectives"></a>目標

* 在我們的共用體驗中探索彼此。
* 選擇並分享玩家頭像。
* 在每個人的標題旁附加玩家頭像。

### <a name="instructions"></a>指示

* 在 [**專案] 面板**中, 流覽至 [**全息影像**] 資料夾。
* 將**PlayerAvatarStore**拖放到階層中。
* 在 [**專案] 面板**中, 流覽至 [**腳本**] 資料夾。
* 按兩下 [ **AvatarSelector** ] 腳本, 在 Visual Studio 中開啟它。
* 將內容取代為下列程式碼。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* 在階層中選取 [ **HologramCollection** ] 物件。
* 在偵測**器**中, 按一下 [**加入元件**]。
* 在搜尋方塊中, 輸入**本機播放程式管理員**。 選取搜尋結果。
* 在階層中選取 [ **HologramCollection** ] 物件。
* 在偵測**器**中, 按一下 [**加入元件**]。
* 在搜尋方塊中, 輸入**Remote Player Manager**。 選取搜尋結果。
* 在 Visual Studio 中開啟**HologramPlacement**腳本。
* 將內容取代為下列程式碼。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* 在 Visual Studio 中開啟**AppStateManager**腳本。
* 將內容取代為下列程式碼。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**部署和享用**
* 建立專案並將其部署到您的 HoloLens 裝置。
* 當您聽到 ping 音效時, 請尋找 [頭像選擇] 功能表, 然後使用 [點一下] 手勢來選取 [頭像]。
* 如果您不想要查看任何全息影像, 當 HoloLens 與服務通訊時, 游標周圍的點會變成不同的色彩: 初始化 (暗紫色)、下載錨點 (綠色)、匯入/匯出位置資料 (黃色)、上傳錨點 (藍色)。 如果您游標周圍的點是預設色彩 (淺紫色), 表示您已準備好與會話中的其他玩家互動!
* 查看連接到您的空間的其他人-將會有一位全像的機器人浮動在其肩上, 並模擬其 head 運動!

## <a name="chapter-5---placement"></a>第5章-放置

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

在本章中, 我們會將錨點放在真實世界的表面上。 我們會使用共用座標, 將該錨點置於連線到共用體驗的每個人之間的中間點。

### <a name="objectives"></a>目標

* 根據玩家的頭部位置, 將全息影像放在空間地圖上。

### <a name="instructions"></a>指示

* 在 [**專案] 面板**中, 流覽至 [**全息影像**] 資料夾。
* 將**CustomSpatialMapping** prefab 拖放到階層上。
* 在 [**專案] 面板**中, 流覽至 [**腳本**] 資料夾。
* 按兩下 [ **AppStateManager** ] 腳本, 在 Visual Studio 中開啟它。
* 將內容取代為下列程式碼。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* 在 [**專案] 面板**中, 流覽至 [**腳本**] 資料夾。
* 按兩下 [ **HologramPlacement** ] 腳本, 在 Visual Studio 中開啟它。
* 將內容取代為下列程式碼。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**部署和享用**
* 建立專案並將其部署到您的 HoloLens 裝置。
* 當應用程式準備好時, 請將它放在圓形中, 並注意 EnergyHub 如何出現在每個人的中心。
* 請點一下以放置 EnergyHub。
* 請嘗試語音命令「重設目標」來挑選 EnergyHub 備份, 並以群組方式一起運作, 以將全息影像移至新位置。

## <a name="chapter-6---real-world-physics"></a>第6章-真實世界的物理

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

在本章中, 我們將新增可從真實世界表面跳動的全息影像。 觀賞您和朋友所啟動的專案, 填滿您的空間!

### <a name="objectives"></a>目標

* 啟動會從真實世界表面跳動的炮彈。
* 共用炮彈, 讓其他玩家可以看到它們。

### <a name="instructions"></a>指示

* 在階層中選取 [ **HologramCollection** ] 物件。
* 在偵測**器**中, 按一下 [**加入元件**]。
* 在搜尋方塊中, 輸入**Projectile 啟動器**。 選取搜尋結果。

**部署和享用**
* 建立並部署至您的 HoloLens 裝置。
* 當應用程式在所有裝置上執行時, 請按下來在真實世界表面啟動 projectile。
* 瞭解當您的 projectile 與其他玩家的圖片衝突時, 會發生什麼事!

## <a name="chapter-7---grand-finale"></a>第7章-總計 Finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

在本章中, 我們將發現只能透過共同作業探索的入口網站。

### <a name="objectives"></a>目標

* 共同作業以在錨點上啟動足夠的炮彈, 以發現秘密入口網站!

### <a name="instructions"></a>指示

* 在 [**專案] 面板**中, 流覽至 [**全息影像**] 資料夾。
* 將**Underworld**資產拖放為 HologramCollection 的**子**系。
* 選取**HologramCollection**後, 按一下偵測**器**中的 [**新增元件**] 按鈕。
* 在功能表的 [搜尋] 方塊中, 輸入**ExplodeTarget**。 選取搜尋結果。
* 選取**HologramCollection**之後, 從階層中, 將**EnergyHub**物件拖曳至偵測**器**中的**目標**欄位。
* 選取**HologramCollection**之後, 從階層中, 將**Underworld**物件拖曳至偵測**器**中的 [ **Underworld** ] 欄位。

**部署和享用**
* 建立並部署至您的 HoloLens 裝置。
* 當應用程式啟動時, 共同合作以在 EnergyHub 啟動炮彈。
* 當 underworld 出現時, 請在 underworld 機器人上啟動炮彈 (按下機器人三次以增加樂趣)。
