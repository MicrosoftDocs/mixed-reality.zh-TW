---
title: MR 基本概念 101E-使用模擬器完成專案
description: 遵循使用 Unity、Visual Studio 和 HoloLens 模擬器的編碼逐步解說，學習全像攝影應用程式的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現實、Windows Mixed Reality、HoloLens、全息裡、學院、教學課程、模擬器
ms.openlocfilehash: b1d8e1f3f272051bdd6f69ab88c3aef4f86f13ef
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434711"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a>MR 基本概念101E：使用模擬器完成專案

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

本教學課程將逐步引導您完成以 Unity 為基礎的完整專案，其中示範 HoloLens 上的核心 Windows Mixed Reality 功能，包括[注視](gaze-and-commit.md)、[手勢](gaze-and-commit.md#composite-gestures)、[語音輸入](voice-input.md)、[空間音效](spatial-sound.md)和[空間對應](spatial-mapping.md). 本教學課程需要大約1小時才能完成。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 基本概念101E：使用模擬器完成專案</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

* [已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。

### <a name="project-files"></a>專案檔案

* 下載專案[所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)檔案。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 支援，請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。
  * 如果您仍然需要 Unity 5.5 支援，請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。
  * 如果您仍然需要 Unity 5.4 支援，請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。
* 將檔案取消封存至您的桌面或其他容易到達的位置。 將資料夾名稱保留為 [**折紙**]。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼，可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)取得。

## <a name="chapter-1---holo-world"></a>第1章-「Hololens」世界

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

在本章中，我們將設定第一個 Unity 專案，並逐步執行組建和部署流程。

### <a name="objectives"></a>目標

* 設定 Unity 以進行全像攝影開發。
* 建立全息影像。
* 查看您製作的全息影像。

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 [**開啟**]。
* 輸入 [位置] 做為您先前未封存的 [**折紙**] 資料夾。
* 選取 [**折紙**]，然後按一下 [**選取資料夾**]。
* 儲存新**場景：檔案** / **另存場景**。
* 將場景命名為「**折紙**」，然後按 [**儲存**] 按鈕。

#### <a name="setup-the-main-camera"></a>設定主要攝影機

* 在 [階層]**面板**中，選取 [**主要相機**]。
* 在偵測**器**中，將其轉換位置設為**0，0，0**。
* 尋找 [**清除旗標**] 屬性，並將下拉式清單從 [ **Skybox** ] 變更為 [**單色**]。
* 按一下 [**背景**] 欄位，以開啟色彩選擇器。
* 將**R、G、B 和 A**設定為**0**。

#### <a name="setup-the-scene"></a>設定場景

* 在 [階層]**面板**中，按一下 [**建立**] 並**建立空**的。
* 以滑鼠右鍵按一下新的**GameObject** ，然後選取 [重新命名]。 將 GameObject 重新命名為**OrigamiCollection**。
* 從 [**專案] 面板**中的 [**全息影像**] 資料夾：
  * 將**階段**拖曳到階層中，成為**OrigamiCollection**的子系。
  * 將**Sphere1**拖曳到階層中，成為**OrigamiCollection**的子系。
  * 將**Sphere2**拖曳到階層中，成為**OrigamiCollection**的子系。
* 以滑鼠右鍵按一下 [階層]**面板**中的 [**方向光源**] 物件，然後選取 [**刪除**]。
* 從 [**全息影像**] 資料夾，將 [**燈光**] 拖曳至 [階層]**面板**的根目錄。
* 在階層**中，選取**[ **OrigamiCollection**]。
* 在偵測**器**中，將轉換位置設定為**0，-0.5，2.0**。
* 按下 Unity 中的 [**播放**] 按鈕，以預覽您的全息影像。
* 您應該會在預覽視窗中看到 [折紙] 物件。
* 按第二次 [**播放**] 以停止預覽模式。

#### <a name="export-the-project-from-unity-to-visual-studio"></a>將專案從 Unity 匯出至 Visual Studio

* 在 Unity 中，選取 檔案 **> 組建設定**。
* 在 [**平臺**] 清單中選取 [ **Windows 儲存區**]，然後按一下 [**切換平臺**]。
* 將 [ **SDK** ] 設定為 [**通用 10** ]，將 [**組建類型**] 設為**D3D**
* 檢查**Unity C#專案**。
* 按一下 [新增] [**開啟場景**] 以加入場景。
* 按一下 [**玩家設定**]。
* 在 [偵測器] 面板中，選取 [ **Windows Store] 標誌**。 然後選取 [**發行設定**]。
* 在 [**功能**] 區段中，選取 [**麥克風**] 和 [ **SpatialPerception** ] 功能。
* 回到 [組建設定] 視窗，按一下 [**建立**]。
* 建立名為 "App" 的**新資料夾**。
* 按一下 [**應用程式] 資料夾**。
* 按 [**選取資料夾**]。
* 當 Unity 完成時，將會出現 [檔案瀏覽器] 視窗。
* 開啟**應用程式**資料夾。
* 開啟 [**日式 Visual Studio] 解決方案**。
* 使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**X86**。
  * 按一下 [裝置] 按鈕旁邊的箭號，然後選取 [ **HoloLens 模擬器**]。
  * 按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。
  * 經過一段時間之後，模擬器就會以折紙專案開始。 第一次啟動[模擬器](using-the-hololens-emulator.md)時，啟動模擬器可能需要15分鐘的時間。 啟動之後，請勿將它關閉。

## <a name="chapter-2---gaze"></a>第2章-注視

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

在本章中，我們將引進三種與您的全息影像互動的第一種方式：[注視](gaze-and-commit.md)。

### <a name="objectives"></a>目標

* 使用世界鎖定的游標來視覺化您的注視。

### <a name="instructions"></a>指示

* 回到您的 Unity 專案，並關閉 [組建設定] 視窗（如果仍處於開啟狀態）。
* 在 [**專案] 面板**中選取 [**全息影像**] 資料夾。
* 將**游標**物件拖曳至根層級的 [階層]**面板**。
* 按兩下**游標**物件以深入瞭解它。
* 以滑鼠右鍵按一下 [專案] 面板中的 [**腳本**] 資料夾。
* 按一下 [**建立**] 子功能表。
* 選取 **C# [腳本**]。
* 將腳本命名為**WorldCursor**。 注意：名稱會區分大小寫。 您不需要新增 .cs 副檔名。
* 在 [階層]**面板**中選取**游標**物件。
* 將**WorldCursor**腳本拖放到 [偵測**器] 面板**中。
* 按兩下 [ **WorldCursor** ] 腳本，在 Visual Studio 中開啟它。
* 將此程式碼複製並貼到**WorldCursor.cs**中，並**全部儲存**。

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

            // Move thecursor to the point where the raycast hit.
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

* 從 [檔案] **> 組建設定**重建應用程式。
* 回到先前用來部署至模擬器的 Visual Studio 方案。
* 出現提示時，選取 [全部重載]。
* 按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。
* 使用 Xbox 控制器來尋找場景。 請注意游標如何與物件的形狀互動。

## <a name="chapter-3---gestures"></a>第3章-手勢

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

在本章中，我們將新增[手勢](gaze-and-commit.md#composite-gestures)的支援。 當使用者選取紙球體時，我們會使用 Unity 的物理引擎來開啟重心，讓球體變得更容易。

### <a name="objectives"></a>目標

* 使用選取手勢控制您的全息影像。

### <a name="instructions"></a>指示

我們將從建立腳本開始，而不會偵測到選取手勢。

* 在 [**腳本**] 資料夾中，建立名為**GazeGestureManager**的腳本。
* 將**GazeGestureManager**腳本拖曳至階層中的**OrigamiCollection**物件。
* 在 Visual Studio 中開啟**GazeGestureManager**腳本，並新增下列程式碼：

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
    void Start()
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

* 在 Scripts 資料夾中建立另一個腳本，這次名為**SphereCommands**。
* 在 [階層] 視圖中展開 [ **OrigamiCollection** ] 物件。
* 將**SphereCommands**腳本拖曳至 [階層] 面板中的**Sphere1**物件。
* 將**SphereCommands**腳本拖曳至 [階層] 面板中的**Sphere2**物件。
* 在 Visual Studio 中開啟腳本進行編輯，並將預設程式碼取代為：

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

* 匯出、建立應用程式，並將其部署至 HoloLens 模擬器。
* 查看場景，並將中心放在其中一個球體。
* 按下 Xbox 控制器上的**一個**按鈕，或按空格鍵以模擬選取手勢。

## <a name="chapter-4---voice"></a>第4章-語音

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

在本章中，我們將新增兩個[語音命令](voice-input.md)的支援：「重設世界」以將捨棄的球面傳回其原始位置，而「卸載球體」則讓球體落在外。

### <a name="objectives"></a>目標

* 新增一律在背景中接聽的語音命令。
* 建立可回應語音命令的全息影像。

### <a name="instructions"></a>指示

* 在 [**腳本**] 資料夾中，建立名為**SpeechManager**的腳本。
* 將**SpeechManager**腳本拖曳至階層中的**OrigamiCollection**物件
* 在 Visual Studio 中開啟**SpeechManager**腳本。
* 將此程式碼複製並貼到**SpeechManager.cs**中，並**全部儲存**：

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

* 在 Visual Studio 中開啟**SphereCommands**腳本。
* 更新腳本以進行讀取，如下所示：

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

* 匯出、建立應用程式，並將其部署至 HoloLens 模擬器。
* 模擬器會支援您電腦的麥克風並回應您的聲音：調整視圖，使游標位於球體的其中一個，並說出「卸載球體」。
* 請說「**重設世界**」，使其回到其初始位置。

## <a name="chapter-5---spatial-sound"></a>第5章-空間音效

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

在本章中，我們會將音樂新增至應用程式，然後觸發對特定動作的音效效果。 我們會使用[空間音效](spatial-sound.md)，在3d 空間中提供特定位置的聲音。

### <a name="objectives"></a>目標

* 聆聽您世界中的全息影像。

### <a name="instructions"></a>指示

* 在 Unity 中，從頂端功能表中選取 [**編輯] > 專案設定 > 音訊**
* 尋找**空間定位器外掛程式**設定，然後選取 [ **MS HRTF 空間定位器**]。
* 從 [**全息影像**] 資料夾，將 [**環境**] 物件拖曳至 [階層] 面板中的 [ **OrigamiCollection** ] 物件。
* 選取 [ **OrigamiCollection** ]，然後尋找 [**音訊來源**] 元件。 變更這些屬性：
  * 檢查**Spatialize**屬性。
  * 勾選 [**在喚醒時播放**]。
  * 將 [**空間 Blend** ] 變更為 [ **3d** ]，方法是將滑杆向右拖曳。
  * 檢查 [**迴圈**] 屬性。
  * 展開 [ **3D 音效設定**]，然後針對 [ **Doppler 層級**] 輸入**0.1** 。
  * 將 [**磁片區 Rolloff** ] 設定為 [**對數 Rolloff**]。
  * 將 [**最大距離**] 設定為**20**。
* 在 [**腳本**] 資料夾中，建立名為**SphereSounds**的腳本。
* 將 [ **SphereSounds** ] 拖曳至階層中的**Sphere1**和**Sphere2**物件。
* 在 Visual Studio 中開啟**SphereSounds** ，更新下列程式碼並**全部儲存**。

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

* 儲存腳本，並返回 Unity。
* 匯出、建立應用程式，並將其部署至 HoloLens 模擬器。
* 戴耳機以獲得完整的效果，並從階段中更靠近或更深入地收聽音效變更。

## <a name="chapter-6---spatial-mapping"></a>第6章-空間對應

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

現在我們要使用[空間對應](spatial-mapping.md)，將遊戲面板放在真實世界中的實際物件上。

### <a name="objectives"></a>目標

* 將您的真實世界帶入虛擬世界。
* 將您的全息影像放在對您最重要的地方。

### <a name="instructions"></a>指示

* 按一下 [專案] 面板中的 [**全息影像**] 資料夾。
* 將**空間對應**資產拖曳至**階層的根目錄。**
* 按一下階層中的 [**空間對應**] 物件。
* 在 [偵測**器] 面板**中，變更下列屬性：
  * 勾選 [**繪製視覺網格**] 方塊。
  * 找出 [**繪製材質**]，然後按一下右側的圓形。 在頂端的搜尋欄位中輸入「**線框**」。 按一下結果，然後關閉視窗。
* 匯出、建立應用程式，並將其部署至 HoloLens 模擬器。
* 當應用程式執行時，系統會以線框呈現先前掃描的實際生活空間網格。
* 觀賞輪流球體如何落在舞臺上，以及在地面上！

現在，我們將示範如何將 OrigamiCollection 移到新的位置：

* 在 [**腳本**] 資料夾中，建立名為**TapToPlaceParent**的腳本。
* 在階層**中，展開**[ **OrigamiCollection** ]，然後選取 [**階段**] 物件。
* 將**TapToPlaceParent**腳本拖曳至階段物件。
* 在 Visual Studio 中開啟**TapToPlaceParent**腳本，並將它更新為下列內容：

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

* 匯出、建立及部署應用程式。
* 現在您應該可以使用選取手勢（**a**或空格鍵）然後移至新位置，然後再次使用 [選取] 手勢，將遊戲放在特定位置。

## <a name="the-end"></a>結束

這就是本教學課程的結尾！

您已瞭解：

* 如何在 Unity 中建立全像攝影應用程式。
* 如何使用 [注視]、[手勢]、[聲音]、[音效] 和 [空間對應]。
* 如何使用 Visual Studio 建立及部署應用程式。

您現在已準備好開始建立自己的全像攝影應用程式！

## <a name="see-also"></a>請參閱

* [MR 基本概念101：使用裝置完成專案](holograms-101.md)
* [目光](gaze-and-commit.md)
* [頭部目光和行動](gaze-and-commit.md)
* [語音輸入](voice-input.md)
* [空間音效](spatial-sound.md)
* [空間對應](spatial-mapping.md)
