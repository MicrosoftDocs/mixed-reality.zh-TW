---
title: MR 共用 240-多個的 HoloLens 裝置
description: 遵循此程式碼逐步解說如何使用 Unity、 Visual Studio 和 HoloLens，若要了解共用全像投影的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 共用、 網路、 academy、 教學課程
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594886"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR 共用 240:多個的 HoloLens 裝置

全像投影會就地剩餘的空間中的相關移，以提供我們的世界中的目前狀態。 HoloLens 就地保留全像投影，使用不同[座標系統](coordinate-systems.md)来追蹤的位置和方向的物件。 當我們共用這些裝置之間的座標系統時，我們可以建立可讓我們參與共用的全像攝影版世界分享的經驗。

在本教學課程中，我們將：

* 設定網路，以分享經驗。
* 跨 HoloLens 裝置共用全像投影。
* 探索我們共用全像攝影版的世界中的其他人員。
* 建立共用的互動式體驗，您可以在此目標的其他玩家-並啟動在它們的砲彈 ！

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 共用 240:多個的 HoloLens 裝置</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>先決條件

* Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)具有網際網路存取。
* 兩個以上的 HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>專案檔

* 下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)專案所需。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。
  * 如果您仍然需要 Unity 5.5 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。
  * 如果您仍然需要 Unity 5.4 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。
* 取消封存您的桌面或其他您輕鬆地連線到位置的檔案。 保留的資料夾名稱，作為**SharedHolograms**。

>[!NOTE]
>如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)。

## <a name="chapter-1---holo-world"></a>第 1 章-Holo 世界

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

在本章中，我們將安裝程式，我們的第一個 Unity 專案並逐步執行組建和部署程序。

### <a name="objectives"></a>目標

* 安裝 Unity 開發全像攝影版的應用程式。
* 請參閱您全像 ！

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 **開啟**。
* 輸入與位置**SharedHolograms**先前未封存的資料夾。
* 選取 **專案名稱**然後按一下**選取資料夾**。
* 在 **階層**，以滑鼠右鍵按一下**Main Camera** ，然後選取**刪除**。
* 在  **HoloToolkit 共用-240/Prefabs/攝影**資料夾中，尋找**Main Camera** prefab。
* 將拖放**Main Camera**成**階層**。
* 在**階層**，按一下**建立**並**建立空**。
* 以滑鼠右鍵按一下 新**GameObject** ，然後選取**重新命名**。
* 重新命名以 GameObject **HologramCollection**。
* 選取  **HologramCollection**物件中**階層**。
* 在  **Inspector**設定**將位置轉換**來：**X:0，Y:-0.25，Z:2**.
* 在 **全像投影**資料夾中的**專案 面板**，尋找**EnergyHub**資產。
* 將拖放**EnergyHub**物件 **[專案] 面板**來**階層**為**子系 HologramCollection**。
* 選取**檔案 > 儲存場景為...**
* 命名場景**SharedHolograms**然後按一下**儲存**。
* 按下**播放**預覽您全像投影的 Unity 中的按鈕。
* 按下**播放**第二次停止 [預覽] 模式。

**匯出從 Unity 專案，Visual studio**
* 在 Unity 中，選取**檔案 > 組建設定**。
* 按一下 **加入開啟的場景**加入場景。
* 選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。
* 設定**SDK**要**通用 10**。
* 設定**目標裝置**要**HoloLens**並**UWP 建置型別**至**D3D**。
* 請檢查**UnityC#專案**。
* 按一下 [建置] 。
* 在出現的 [檔案總管] 視窗，建立**新的資料夾**名為 「 應用程式 」。
* 只要按一下**應用程式**資料夾。
* 按下**選取資料夾**。
* Unity 完成時，會出現檔案總管 視窗。
* 開啟**應用程式**資料夾。
* 開啟**SharedHolograms.sln**即可啟動 Visual Studio。
* 使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **X86**。
* 按一下下拉式清單旁的箭號本機電腦，然後選取**遠端裝置**。
    * 設定**地址**的名稱或 IP 位址的您 HoloLens。 如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**詢問 Cortana 或 **「 嘿 Cortana，我的 IP 位址是什麼？ 」**
    * 離開**驗證模式**設為**通用**。
    * 按一下 **選取**
* 按一下 **偵錯 > 啟動但不偵錯**或按**Ctrl + F5**。 如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device-hololens)。
* 將放在您的 HoloLens 上，並尋找 EnergyHub 全像圖。

## <a name="chapter-2---interaction"></a>第 2 章-互動

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

在本章中，我們將與我們全像投影互動。 首先，我們將新增的資料指標，以視覺化方式檢視我們[視線](gaze.md)。 然後，我們將新增[筆勢](gestures.md)和空間中放置我們全像投影中使用我們的游標。

### <a name="objectives"></a>目標

* 使用視線輸入來控制資料指標。
* 使用輸入至全像投影與互動的筆勢。

### <a name="instructions"></a>指示

**Gaze**
* 在 **階層面板**選取**HologramCollection**物件。
* 在 [**偵測器] 面板**按一下 [**新增元件**] 按鈕。
* 在功能表中，輸入在搜尋方塊**視線 Manager**。 選取搜尋結果。
* 在  **HoloToolkit 共用 240\Prefabs\Input**資料夾中，尋找**游標**資產。
* 將拖放**游標**拖曳至資產**階層**。

**筆勢**
* 在 **階層面板**選取**HologramCollection**物件。
* 按一下 [**新增元件**並輸入**筆勢管理員**搜尋] 欄位中。 選取搜尋結果。
* 在 **階層面板**，展開**HologramCollection**。
* 選取子系**EnergyHub**物件。
* 在 [**偵測器] 面板**按一下 [**新增元件**] 按鈕。
* 在功能表中，輸入在搜尋方塊**全像放置**。 選取搜尋結果。
* 選取 來儲存場景**檔案 > 儲存場景**。

**部署並享有**
* 建置並部署到您的 HoloLens，使用來自上一個章節的指示。
* 一旦您 HoloLens 上啟動應用程式，移動您的標頭，並注意 EnergyHub 如何遵循您的視線。
* 請注意如何資料指標時您視線闀，時，會出現，而且如果不在全像 gazing 會變更為點光線。
* 執行將全像空中點選。 在我們的專案中，此時您可以只將全像一次 （重新部署到再試一次）。

## <a name="chapter-3---shared-coordinates"></a>第 3 章-共用座標

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

這是查看並與其互動全像投影，更有趣，但讓我們進一步。 我們會設定我們第一個共用體驗-雷射，每個人都可以看到在一起。

### <a name="objectives"></a>目標

* 設定網路，以分享經驗。
* 建立一般的參考點。
* 跨裝置共用座標系統。
* 每個人看到相同的全像 ！

>[!NOTE]
>**InternetClientServer**並**PrivateNetworkClientServer**必須連接到共用的伺服器應用程式的宣告功能。 這是針對您已在全像投影 240 但謹記在心，為您自己的專案。
>1. 瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定
>2. 按一下 [Windows Store] 索引標籤
>3. 在 「 發行的設定 > 功能 」 區段中，檢查**InternetClientServer**功能並**PrivateNetworkClientServer**功能

### <a name="instructions"></a>指示

* 在  **專案 面板**瀏覽至**HoloToolkit 共用 240\Prefabs\Sharing**資料夾。
* 將拖放**Sharing**至 prefab**階層面板**。

接下來，我們需要啟動共用服務。 只有**一部電腦**是共用體驗需要執行此步驟。
* 在 Unity-中最上方現有的功能表中，選取**HoloToolkit 共用 240 功能表**。
* 選取 **啟動共用服務**下拉式清單中的項目。
* 請檢查**私用網路**選項，然後按一下**允許存取**防火牆提示出現時。
* 請記下的共用服務主控台視窗中顯示的 IPv4 位址。 這是與機器服務執行相同的 IP。

依照其餘指示**所有電腦**，將會加入分享的經驗。
* 在 **階層**，選取**共用**物件。
* 在**Inspector**上**共用階段**元件，變更**伺服器位址**從 'localhost' 為執行 SharingService.exe 之電腦的 IPv4 位址。
* 在 **階層**選取**HologramCollection**物件。
* 在  **Inspector**按一下 **新增元件** 按鈕。
* 在 [搜尋] 方塊中，輸入**匯入匯出的錨點 Manager**。 選取搜尋結果。
* 在  **專案 面板**瀏覽至**指令碼**資料夾。
* 按兩下**HologramPlacement**指令碼，以在 Visual Studio 中開啟它。
* 下列程式碼取代內容。

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

* 傳回在 Unity 中，選取**HologramCollection**中**階層面板**。
* 在 [**偵測器] 面板**按一下 [**新增元件**] 按鈕。
* 在功能表中，輸入在搜尋方塊**應用程式的狀態管理員**。 選取搜尋結果。

**部署並享有**
* 建置您的 HoloLens 裝置專案。
* 將指定為第一個部署一個 HoloLens。 您必須等待才能下 EnergyHub 上傳至服務的錨點 (這可能需要 30-60 秒)。 上傳完成後，直到您點選手勢都會被忽略。
* 已置放 EnergyHub 之後，它的位置將會上傳至服務，並接著便可部署到所有其他的 HoloLens 裝置。
* 當新的 HoloLens 第一次加入工作階段時，可能不在該裝置上正確 EnergyHub 的位置。 不過，已從服務下載的錨點和 EnergyHub 位置，如 EnergyHub 應該移至新的共用位置。 如果這不會在 30 至 60 秒，逐步引導到原始的 HoloLens 的設定來收集多個環境線索的錨點時。 如果位置仍不會鎖定，重新部署至裝置。
* 當裝置時，隨時，並執行應用程式，尋找 EnergyHub。 大家都同意在全像的位置可以和文字面向的方向？

## <a name="chapter-4---discovery"></a>第 4 章-探索

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

現在，每個人都可以看到相同的全像 ！ 現在我們來看看其他連線至共用全像攝影版世界的每個人。 在本章中，我們就會把相同的共用工作階段中的所有其他的 HoloLens 裝置旋轉與前端的位置。

### <a name="objectives"></a>目標

* 在我們的共用經驗來發現彼此。
* 選擇，以及共用播放程式顯示圖片。
* 將播放程式顯示圖片，每個人的標頭旁邊的連結。

### <a name="instructions"></a>指示

* 在  **專案 面板**瀏覽至**全像投影**資料夾。
* 將拖放**PlayerAvatarStore**成**階層**。
* 在  **專案 面板**瀏覽至**指令碼**資料夾。
* 按兩下**AvatarSelector**指令碼，以在 Visual Studio 中開啟它。
* 下列程式碼取代內容。

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

* 在 **階層**選取**HologramCollection**物件。
* 在  **Inspector**按一下 **新增元件**。
* 在 [搜尋] 方塊中，輸入**本機播放程式管理員**。 選取搜尋結果。
* 在 **階層**選取**HologramCollection**物件。
* 在  **Inspector**按一下 **新增元件**。
* 在 [搜尋] 方塊中，輸入**遠端播放程式管理員**。 選取搜尋結果。
* 開啟**HologramPlacement** Visual Studio 中的指令碼。
* 下列程式碼取代內容。

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

* 開啟**AppStateManager** Visual Studio 中的指令碼。
* 下列程式碼取代內容。

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

**部署並享有**
* 建置，並將專案部署到您的 HoloLens 裝置。
* 當您聽到聲音，ping、 虛擬人偶選取功能表中找到並選取 顯示圖片使用空中點選手勢。
* 如果您不想透過任何全像投影，游標周圍輕點將會開啟不同的色彩時您 HoloLens 正在與服務通訊： 初始化 （深紫色）、 下載錨點 （綠色），匯入/匯出位置資料 （黃色），正在上傳 （藍色） 的錨點。 如果游標周圍輕點的預設色彩 （淺紫），接著您就可以與其他玩家互動工作階段中 ！
* 看看其他人連線到您的空間-將會有全像攝影版的機器人浮動高於其 shoulder 和模擬其前端動作 ！

## <a name="chapter-5---placement"></a>第 5 章-位置

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

在本章中，我們要能夠放在真實世界的表面上的錨點。 將會錨定在中間點之間每個人都連接到分享經驗中，我們將使用共用的座標。

### <a name="objectives"></a>目標

* 全像投影置於空間的對應，根據玩家的前端的位置。

### <a name="instructions"></a>指示

* 在  **專案 面板**瀏覽至**全像投影**資料夾。
* 將拖放**CustomSpatialMapping**拖曳至 prefab**階層**。
* 在  **專案 面板**瀏覽至**指令碼**資料夾。
* 按兩下**AppStateManager**指令碼，以在 Visual Studio 中開啟它。
* 下列程式碼取代內容。

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

* 在  **專案 面板**瀏覽至**指令碼**資料夾。
* 按兩下**HologramPlacement**指令碼，以在 Visual Studio 中開啟它。
* 下列程式碼取代內容。

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

**部署並享有**
* 建置，並將專案部署到您的 HoloLens 裝置。
* 應用程式準備就緒時，就能在圓形中，並注意 EnergyHub 中央的每個人的顯示方式。
* 點選要放置 EnergyHub。
* 嘗試移動到新位置的全像語音命令回挑選 EnergyHub 並合作，為群組的 [重設目標]。

## <a name="chapter-6---real-world-physics"></a>第 6 章-實境物理

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

在本章中，我們將新增全像投影，彈開真實世界的介面。 觀看您啟動由您和您的朋友的專案會填滿的空間 ！

### <a name="objectives"></a>目標

* 啟動投擲彈開真實世界的介面。
* 共用投擲，讓其他玩家可以看到它們。

### <a name="instructions"></a>指示

* 在 **階層**選取**HologramCollection**物件。
* 在  **Inspector**按一下 **新增元件**。
* 在 [搜尋] 方塊中，輸入**彈藥啟動器**。 選取搜尋結果。

**部署並享有**
* 建置並部署到您的 HoloLens 裝置。
* 當所有裝置上執行應用程式時，執行以啟動在真實世界表面的彈藥空中點選。
* 請參閱您的彈藥衝突與其他播放器的顯示圖片時，會發生什麼事 ！

## <a name="chapter-7---grand-finale"></a>第 7 章-總計二

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

在本章中，我們會找出只與共同作業探索到的入口網站。

### <a name="objectives"></a>目標

* 若要啟動的錨點，以發掘出有用祕密的入口網站在足夠投擲一起運作 ！

### <a name="instructions"></a>指示

* 在  **專案 面板**瀏覽至**全像投影**資料夾。
* 將拖放**底世界**資產做**HologramCollection 的子系**。
* 具有**HologramCollection**選取，按一下**新增元件**按鈕**Inspector**。
* 在功能表中，輸入在搜尋方塊**ExplodeTarget**。 選取搜尋結果。
* 具有**HologramCollection**已選取，從**階層**拖曳**EnergyHub**物件**目標**欄位**Inspector**。
* 與**HologramCollection**已選取，從**階層**拖曳**底世界**物件**底世界**欄位**Inspector**。

**部署並享有**
* 建置並部署到您的 HoloLens 裝置。
* 當應用程式已啟動時，一起共同作業以啟動在 EnergyHub 投擲。
* 底世界出現時，請啟動砲彈在底世界機器人 （按三次，額外的有趣的機器人）。
