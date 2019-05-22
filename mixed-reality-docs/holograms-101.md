---
title: MR 基本概念 101-與裝置的完整專案
description: 請遵循此程式碼撰寫的逐步解說，使用 Unity、 Visual Studio 和 HoloLens，若要了解 Windows Mixed Reality 的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合實境，Windows Mixed Reality、 HoloLens、 全像圖、 academy、 教學課程
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591556"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>MR 101 基本知識：完整的專案，與裝置

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

本教學課程將逐步引導您完成的專案，建置在 Unity 中，示範核心 Windows Mixed Reality 功能，包括 HoloLens[視線](gaze.md)，[筆勢](gestures.md)，[語音輸入](voice-input.md)，[空間音效](spatial-sound.md)並[空間對應](spatial-mapping.md)。

本教學課程需要大約 1 小時才能完成。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 101 基本知識：完整的專案，與裝置</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>先決條件

* Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。
* HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>專案檔

* 下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)專案所需。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。
  * 如果您仍然需要 Unity 5.5 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。
  * 如果您仍然需要 Unity 5.4 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。
* 取消封存您的桌面或其他您輕鬆地連線到位置的檔案。 保留的資料夾名稱，作為**Origami**。

>[!NOTE]
>如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)。

## <a name="chapter-1---holo-world"></a>第 1 章-「 Holo"world

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

在本章中，我們將安裝程式，我們的第一個 Unity 專案並逐步執行組建和部署程序。

### <a name="objectives"></a>目標

* 設定全像攝影版的開發環境 Unity。
* 請全像圖。
* 請參閱您所做的雷射。

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 **開啟**。
* 輸入與位置**Origami**資料夾您先前未封存。
* 選取  **Origami**然後按一下**選取資料夾**。
* 由於**Origami**專案未包含場景，儲存新的檔案使用空的預設場景：**檔案** / **儲存為場景**。
* 命名新的場景**Origami**然後按**儲存** 按鈕。

#### <a name="setup-the-main-virtual-camera"></a>安裝程式主要的虛擬觀景窗

* 在 **階層面板**，選取**Main Camera**。
* 在  **Inspector**將其轉換位置設為**0,0,0**。
* 尋找**清除旗標**屬性，並將變更從下拉式清單中**天空盒**來**單色**。
* 按一下 **背景**欄位，以開啟色彩選擇器。
* 設定**R、 G、 B 和 A**要**0**。

#### <a name="setup-the-scene"></a>設定場景

* 在**階層面板**，按一下**建立**並**建立空**。
* 以滑鼠右鍵按一下 新**GameObject**並選取 重新命名。 重新命名以 GameObject **OrigamiCollection**。
* 從**全像投影**專案] 面板中的資料夾 （展開資產，並選取 [全像投影或按兩下 [專案] 面板中的 [全像投影] 資料夾）：
  * 拖曳**階段**置於階層是子系**OrigamiCollection**。
  * 拖曳**Sphere1**置於階層是子系**OrigamiCollection**。
  * 拖曳**Sphere2**置於階層是子系**OrigamiCollection**。
* 以滑鼠右鍵按一下**定向光線**物件中**階層面板**，然後選取**刪除**。
* 從**全像投影**資料夾中，拖曳**燈**的根目錄**階層面板**。
* 在 **階層**，選取**OrigamiCollection**。
* 在  **Inspector**，將轉換的位置設為**0，-0.5，2.0**。
* 按下**播放**預覽您全像投影的 Unity 中的按鈕。
* 您應該會看到 [預覽] 視窗中的 Origami 物件。
* 按下**播放**第二次停止 [預覽] 模式。

#### <a name="export-the-project-from-unity-to-visual-studio"></a>匯出從 Unity 專案，Visual studio

* 在 Unity 中，選取**檔案 > 組建設定**。
* 選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。
* 設定**SDK**來**通用 10**並**建置型別**至**D3D**。
* 請檢查**UnityC#專案**。
* 按一下 **加入開啟的場景**加入場景。
* 按一下 [建置] 。
* 在出現的 [檔案總管] 視窗，建立**新的資料夾**名為 「 應用程式 」。
* 只要按一下**應用程式資料夾**。
* 按下**選取資料夾**。
* Unity 完成時，會出現檔案總管 視窗。
* 開啟**應用程式**資料夾。
* （按兩下） 開放**Origami.sln**。
* 使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **X86**。
* 按一下 [裝置] 按鈕旁邊的箭號，然後選取**遠端機器**透過 Wi-fi 部署。
  * 設定**地址**的名稱或 IP 位址的您 HoloLens。 如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**詢問 Cortana 或 **「 嘿 Cortana，我的 IP 位址是什麼？ 」**
  * 如果透過 USB 連接的 HoloLens，可能會改為選取**裝置**透過 USB 進行部署。
  * 離開**驗證模式**設為**通用**。
  * 按一下 **選取**

* 按一下 **偵錯 > 啟動但不偵錯**或按**Ctrl + F5**。 如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))。

* Origami 專案將立即建置、 部署到您的 HoloLens，然後再執行。
* 將放在您的 HoloLens 上，若要查看您新全像投影看一下。

## <a name="chapter-2---gaze"></a>第 2 章-視線

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

在本章中，我們即將引入互動的三種方法的第一個與您全像投影-[視線](gaze.md)。

### <a name="objectives"></a>目標

* 以視覺化方式檢視您的視線使用全球鎖定的資料指標。

### <a name="instructions"></a>指示

* 返回您的 Unity 專案，並關閉 [建立設定] 視窗，它是否仍保持開啟。
* 選取 **全像投影**中的資料夾**專案 面板**。
* 拖曳**游標**物件插入**階層面板**根層級。
* 按兩下**游標**才會仔細看看它的物件。
* 以滑鼠右鍵按一下**指令碼**專案 面板中的資料夾。
* 按一下 **建立**子功能表。
* 選取   **C#指令碼**。
* 指令碼命名**WorldCursor**。 注意：此名稱區分大小寫。 您不需要將.cs 副檔名。
* 選取 **游標**物件中**階層面板**。
* 將拖放**WorldCursor**編寫成指令碼**Inspector 面板**。
* 按兩下**WorldCursor**指令碼，以在 Visual Studio 中開啟它。
* 複製並貼上此程式碼**WorldCursor.cs**並**全部儲存**。

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* 重建的應用程式**檔案 > 組建設定**。
* 返回先前用來部署到您的 HoloLens 的 Visual Studio 方案。
* 選取 [重新載入全部] 出現提示時。
* 按一下 **偵錯-> 啟動但不偵錯**或按**Ctrl + F5**。
* 現在看一下場景，並注意資料指標的形狀之物件的互動方式。

## <a name="chapter-3---gestures"></a>第 3 章-筆勢

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

在本章中，我們將新增的支援[筆勢](gestures.md)。 當使用者選取的紙張球體時，我們要藉由開啟重力使用 Unity 的物理條件引擎落球體。

### <a name="objectives"></a>目標

* 控制您全像投影與選取的筆勢。

### <a name="instructions"></a>指示

我們一開始是建立指令碼，然後可以偵測到選取的筆勢。

* 在 **指令碼**資料夾中，建立名為指令碼**GazeGestureManager**。
* 拖曳**GazeGestureManager**拖曳至指令碼**OrigamiCollection**階層中的物件。
* 開啟**GazeGestureManager**指令碼在 Visual Studio 中，並新增下列程式碼：

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* 建立另一個指令碼，在 [指令碼] 資料夾中，這次是名為**SphereCommands**。
* 依序展開**OrigamiCollection**階層檢視中的物件。
* 拖曳**SphereCommands**拖曳至指令碼**Sphere1**在階層窗格中的物件。
* 拖曳**SphereCommands**拖曳至指令碼**Sphere2**在階層窗格中的物件。
* 在 Visual Studio 中開啟指令碼進行編輯，並以此取代預設的程式碼：

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* 匯出、 建置和部署到您的 HoloLens 的應用程式。
* 看看其中一個所置放的球體。
* 執行選取的動作，並觀看球體放入以下的介面。

## <a name="chapter-4---voice"></a>第 4 章-語音

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

在本章中，我們將新增兩個支援[語音命令](voice-input.md):「 重設的 world 」 到其原始位置，傳回已卸除的球體看起來，並捨棄球體 進行切換的球體。

### <a name="objectives"></a>目標

* 在背景中新增 alwayson 接聽的語音命令。
* 建立回應語音命令全像圖。

### <a name="instructions"></a>指示

* 在 **指令碼**資料夾中，建立名為指令碼**SpeechManager**。
* 拖曳**SpeechManager**拖曳至指令碼**OrigamiCollection**階層中的物件
* 開啟**SpeechManager** Visual Studio 中的指令碼。
* 複製並貼上此程式碼**SpeechManager.cs**並**全部儲存**:

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* 開啟**SphereCommands** Visual Studio 中的指令碼。
* 更新指令碼來讀取，如下所示：

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* 匯出、 建置和部署到您的 HoloLens 的應用程式。
* 看看其中一個球體看起來，並說"**卸除的球體**"。
* 說出 「**重設的世界**「 若要將它們回復到其初始位置。

## <a name="chapter-5---spatial-sound"></a>第 5 章-空間的音效

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

在本章中，我們會將音樂新增至應用程式，並接著觸發特定動作的音效。 我們將使用[空間音效](spatial-sound.md)讓音效在 3D 空間中的特定位置。

### <a name="objectives"></a>目標

* 聽聽您的世界中全像投影。

### <a name="instructions"></a>指示

* 在頂端功能表中的 Unity 選取**編輯 > 專案設定 > 音訊**
* 在右側 [偵測器] 面板中，尋找**空間外掛程式**設定，然後選取**MS HRTF 空間**。
* 從**全像投影**資料夾，在 [專案] 面板中，拖曳**環境**物件拖曳至**OrigamiCollection**在階層窗格中的物件。
* 選取  **OrigamiCollection**並尋找**音訊來源**元件在偵測器窗格中。 變更這些屬性：
  * 請檢查**Spatialize**屬性。
  * 請檢查**甦醒狀態上播放**。
  * 變更**空間 Blend**要**3D**拖曳到最右邊的滑桿。 值應該將從 0 變更為 1 時移動滑桿。
  * 請檢查**迴圈**屬性。
  * 依序展開**3D 音效設定**，並輸入**0.1** for **Doppler 層級**。
  * 設定**磁碟區捲繞**要**對數捲繞**。
  * 設定**最大距離**要**20**。
* 在 **指令碼**資料夾中，建立名為指令碼**SphereSounds**。
* 將拖放**SphereSounds**要**Sphere1**並**Sphere2**階層中的物件。
* 開啟**SphereSounds**在 Visual Studio 中，更新下列程式碼並**全部儲存**。

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* 儲存指令碼，並返回到 Unity。
* 匯出、 建置和部署到您的 HoloLens 的應用程式。
* 放大及更階段，然後開啟要並存至聽到任何聲音變更。

## <a name="chapter-6---spatial-mapping"></a>第 6 章-空間對應

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

現在我們將使用[空間對應](spatial-mapping.md)放置在真實世界的真實物件上的遊戲面板。

### <a name="objectives"></a>目標

* 虛擬世界中帶入您真實的世界。
* 將您全像投影，在您最感興趣。

### <a name="instructions"></a>指示

* 在 Unity 中，按一下**全像投影**專案 面板中的資料夾。
* 拖曳**空間的對應**資產的根目錄**階層**。
* 按一下 **空間對應**階層中的物件。
* 在  **Inspector 面板**，變更下列屬性：
  * 請檢查**繪製視覺網狀結構** 方塊中。
  * 找出**繪製的材質**按一下右側的圓形。 類型"**線框**」 到頂端的 [搜尋] 欄位。 按一下結果，然後關閉視窗。 當您這樣做時，繪製資料的值應該設定製作。
* 匯出、 建置和部署到您的 HoloLens 的應用程式。
* 當應用程式執行時，框線網狀結構將覆疊您真實的世界。
* 觀看如何輪流球體會切換關閉階段，並送至最低限度值 ！

現在要教您如何將 OrigamiCollection 移至新的位置：

* 在 **指令碼**資料夾中，建立名為指令碼**TapToPlaceParent**。
* 在 **階層**，展開**OrigamiCollection** ，然後選取**階段**物件。
* 拖曳**TapToPlaceParent**階段物件的指令碼。
* 開啟**TapToPlaceParent**指令碼在 Visual Studio 中，並將它有下列更新：

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* 匯出、 建置和部署應用程式。
* 現在您現在應該可以加在遊戲中的特定位置 gazing 一下，使用選取的筆勢然後移至新的位置，並再次使用選取的筆勢。

## <a name="chapter-7---holographic-fun"></a>第 7 章-全像攝影版的樂趣

### <a name="objectives"></a>目標

* 顯示 全像攝影版的地底世界的入口。

### <a name="instructions"></a>指示

現在要教您如何找出全像攝影版的地底世界：

* 從**全像投影**專案 面板中的資料夾：
  * 拖曳**底世界**置於階層是子系**OrigamiCollection**。
* 在 **指令碼**資料夾中，建立名為指令碼**HitTarget**。
* 在 **階層**，展開**OrigamiCollection**。
* 依序展開**階段**物件，並選取**目標**物件 （藍色風扇）。
* 拖曳**HitTarget**拖曳至指令碼**目標**物件。
* 開啟**HitTarget**指令碼在 Visual Studio 中，並將它有下列更新：

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* 在 Unity 中，選取**目標**物件。
* 兩個公用屬性現在會顯示在**叫用目標**元件以及我們的場景中的參考物件的需求：
  * 拖曳**底世界**從**階層**面板**底世界**屬性**叫用目標**元件。
  * 拖曳**階段**從**階層**面板**隱藏物件**屬性**叫用目標**元件。
* 匯出、 建置和部署應用程式。
* 將 Origami 集合放在最低限度值，並接著使用選取的動作進行卸除的球體。
* 當球體叫用目標 （藍色風扇） 時，則會發生遽增。 集合將會隱藏，並會出現一個洞地底世界。

## <a name="the-end"></a>結束

而且，本教學課程結束 ！

您已了解：

* 如何建立在 Unity 的全像攝影版的應用程式。
* 如何使用視線、 手勢、 語音、 聲音、 和空間的對應。
* 如何建置和部署使用 Visual Studio 的應用程式。

您現在已準備好要開始建立您自己全像攝影版的體驗 ！

## <a name="see-also"></a>另請參閱

* [MR 基本概念 101E:模擬器使用完整的專案](holograms-101e.md)
* [Gaze](gaze.md)
* [筆勢](gestures.md)
* [語音輸入](voice-input.md)
* [空間的音效](spatial-sound.md)
* [空間對應](spatial-mapping.md)
