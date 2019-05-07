---
title: MR 空間 230-空間對應
description: 遵循此程式碼逐步解說如何使用 Unity、 Visual Studio 和 HoloLens，若要了解空間對應概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 academy、 教學課程中，空間的對應、 介面重構，網格
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993564"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR 空間 230:空間對應

[空間對應](spatial-mapping.md)實際及虛擬世界結合所教授的環境相關全像投影。 MR 空間 230 (專案 Planetarium) 中我們將了解如何：

* 掃描您的開發電腦以 HoloLens 的環境和傳輸資料。
* 探索著色器，並了解如何使用它們以視覺化方式呈現您的空間。
* 細分成使用網格處理簡單的平面空間網狀結構。
* 除了在中學到的放置技術移[MR 基本概念 101](holograms-101.md)，並提供意見反應全像可以放置在環境中。
* 瀏覽的阻擋物的影響，因此在真實世界物件後面您全像圖時，您仍然可以看到它與超人 ！

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 空間 230:空間對應</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>先決條件

* Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。
* 基本C#程式設計的能力。
* 您應已完成[MR 基本概念 101](holograms-101.md)。
* HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>專案檔

* 下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip)專案所需。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)。
  * 如果您仍然需要 Unity 5.5 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)。
  * 如果您仍然需要 Unity 5.4 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)。
* 取消封存您的桌面或其他您輕鬆地連線到位置的檔案。

>[!NOTE]
>如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)。

### <a name="notes"></a>附註

* 在 Visual Studio 需要停用中的 [啟用 Just My Code] (*未核取*) 下工具 > 選項 > 若要在程式碼中設定中斷點的偵錯。

## <a name="unity-setup"></a>Unity 安裝

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* 開始**Unity**。
* 選取 **新增**建立新的專案。
* 將專案命名為**Planetarium**。
* 確認**3D**選取設定。
* 按一下 **建立專案**。
* 一旦 Unity 啟動時，請移至**編輯 > 專案設定 > Player**。
* 在 [ **Inspector** ] 面板中，尋找並選取綠色**Windows Store**圖示。
* 依序展開**其他設定**。
* 在 **轉譯**區段中，按一下**受支援的虛擬實境**選項。
* 確認**Windows 全像攝影版**清單中會出現**虛擬實境 Sdk**。 如果沒有，請選取**+** 按鈕在清單底部，然後選擇**Windows 全像攝影版**。
* 依序展開**發佈設定**。
* 在 **功能**區段中，請檢查下列設定：
    * InternetClientServer
    * PrivateNetworkClientServer
    * 麥克風
    * SpatialPerception
* 移至**編輯 > 專案設定 > 品質**
* 在 [ **Inspector** ] 面板中，在 Windows 市集圖示，選取黑色的向下箭頭，在 'Default' 資料列，並將變更預設設定，以**非常低**。
* 移至**資產 > 匯入封裝 > 自訂套件**。
* 瀏覽至 **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting**資料夾。
* 按一下  **Planetarium.unitypackage**。
* 按一下 [開啟] 。
* **匯入 Unity 封裝**應該會出現視窗，按一下**匯入** 按鈕。
* 等待匯入的所有資產，我們將完成此專案需要 Unity。
* 在 [**階層**] 面板中，刪除**Main Camera**。
* 在 [**專案**] 面板中， **HoloToolkit-SpatialMapping-230\Utilities\Prefabs**資料夾中，尋找**Main Camera**物件。
* 將拖放**Main Camera**至 prefab**階層**面板。
* 在 [**階層**] 面板中，刪除**定向光線**物件。
* 在 [**專案**] 面板中，**全像投影**資料夾中，找出**游標**物件。
* 拖放**游標**至 prefab**階層**。
* 在 **階層**面板中，選取**游標**物件。
* 在 [ **Inspector** ] 面板中，按一下**層**下拉式清單，然後選取**編輯圖層...**.
* 名稱**使用者層級 31**做為 「**SpatialMapping**"。
* 儲存新的場景：**檔案 > 儲存場景為...**
* 按一下 **新的資料夾**並將資料夾命名**場景**。
* 將檔案命名為"**Planetarium**"並將它儲存在**場景**資料夾。

## <a name="chapter-1---scanning"></a>第 1 章-掃描

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**目標**
* 深入了解 SurfaceObserver 和其設定影響如何體驗和效能。
* 建立聊天室掃描以收集您的聊天室的網格的體驗。

**指示**
* 在 **專案**面板**HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs**資料夾中，尋找**SpatialMapping** prefab。
* 拖放**SpatialMapping**至 prefab**階層**面板。

**建置和部署 （第 1 部分）**
* 在 Unity 中，選取**檔案 > 組建設定**。
* 按一下 **加入開啟的場景**若要加入**Planetarium**場景方向，以建置。
* 選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。
* 設定**SDK**要**通用 10**並**UWP 建置型別**來**D3D**。
* 請檢查**UnityC#專案**。
* 按一下 [建置] 。
* 建立**新的資料夾**名為 「 應用程式 」。
* 只要按一下**應用程式**資料夾。
* 按下**選取資料夾** 按鈕。
* 當完成 Unity 建置時，會出現檔案總管 視窗。
* 按兩下**應用程式**資料夾將它開啟。
* 按兩下**Planetarium.sln**載入 Visual Studio 中的專案。
* 在 Visual Studio 中，請變更設定以使用頂端的工具列**發行**。
* 變更平台**x86**。
* 按一下右邊的 本機電腦上，' 的下拉式箭號，然後選取**遠端機器**。
* 請輸入[裝置的 IP 位址](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) 欄位中的位址和驗證模式變更為**通用 （未加密的通訊協定）**。
* 按一下 **偵錯-> 啟動但不偵錯**或按**Ctrl + F5**。
* 監看式**輸出**面板在 Visual Studio 中建置和部署狀態。
* 一旦您的應用程式已部署，逐步房間周圍。 您會看到黑白的線框網格所涵蓋的周圍介面。
* 掃描您恍神。 請務必查看牆壁、 上限和樓層。

**建置和部署 （第 2 部分）**

現在讓我們來探索如何設定對應的空間可能會影響效能。
* 在 Unity 中，選取**視窗中 > Profiler**。
* 按一下 **新增 Profiler > GPU**。
* 按一下 **作用中的 Profiler > <Enter IP>** 。
* 請輸入**IP 位址**的您 HoloLens。
* 按一下 **[連接]**。
* 觀察 GPU 來轉譯畫面格所花費的毫秒的數。
* 停止從裝置上執行應用程式。
* 返回 Visual Studio，然後開啟**SpatialMappingObserver.cs**。 您會發現它 HoloToolkit\SpatialMapping 專案資料夾中的組件 CSharp (通用 Windows)。
* 尋找**Awake()** 函式，並新增下列程式碼行：**TrianglesPerCubicMeter = 1200;**
* 重新部署專案，以您的裝置，然後**重新連線的程式碼剖析工具**。 觀察到的變更要呈現的畫面格的毫秒數。
* 停止從裝置上執行應用程式。

**儲存並在 Unity 中載入**

最後，讓我們儲存我們的房間網狀結構，並將其載入至 Unity。
* 返回 Visual Studio，並移除**TrianglesPerCubicMeter**您在中新增的一行**Awake()** 函式在上一節。
* 專案重新部署至您的裝置。 我們現在應該執行含**500**三角形每三次方的計量。
* 開啟瀏覽器並瀏覽至您 HoloLens IPAddress 報名參加**Windows Device Portal**。
* 選取  **3D 檢視**左方面板中的選項。
* 底下**介面重構**選取**更新** 按鈕。
* 觀看您已掃描您 HoloLens 的區域會出現在顯示視窗。
* 若要儲存您的房間掃描，請按**儲存** 按鈕。
* 開啟您**下載**資料夾，找出儲存的空間模型**SRMesh.obj**。
* 複製**SRMesh.obj**要**資產**Unity 專案的資料夾。
* 在 Unity 中，選取**SpatialMapping**物件中**階層**面板。
* 找出**物件介面觀察者 （指令碼）** 元件。
* 按一下右側的圓形**聊天室模型**屬性。
* 尋找並選取**SRMesh**物件，並接著關閉視窗。
* 確認**聊天室模型**中的屬性**Inspector**面板現在已設定為**SRMesh**。
* 按下**播放**輸入 Unity 的 [預覽] 模式的按鈕。
* SpatialMapping 元件將從儲存的空間模型載入網格，讓您可以在 Unity 中使用它們。
* 若要切換**場景**檢視來查看所有聊天室模型顯示框線著色器。
* 按下**播放** 按鈕以結束 預覽 模式。

**注意：** 您在 Unity 中，輸入 [預覽] 模式下一次它預設會載入已儲存的房間網狀結構的。

## <a name="chapter-2---visualization"></a>第 2 章-視覺效果

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**目標**
* 了解著色器的基本概念。
* 以視覺化方式檢視您恍神。

**指示**
* 在 Unity**階層**面板中，選取**SpatialMapping**物件。
* 在 [ **Inspector** ] 面板中，尋找**空間對應 Manager （指令碼）** 元件。
* 按一下右側的圓形**表面材質**屬性。
* 尋找並選取**BlueLinesOnWalls** material 和關閉視窗。
* 在 **專案**面板**著色器**資料夾中，按兩下**BlueLinesOnWalls**以開啟 Visual Studio 中的 著色器。
* 這是簡單的像素 （頂點來分割） 著色器，將完成下列工作：
    1. 將頂點位置轉換為全局空間中。
    2. 檢查 頂點的標準來判斷是否垂直的像素。
    3. 設定轉譯的像素的色彩。

**建置和部署**
* 傳回至 Unity 並按下**播放**進入預覽模式。
* 藍線將會呈現所有垂直的表面的房間網狀結構 （這會自動載入已儲存掃描資料）。
* 若要切換**場景**調整檢視的空間，並查看整個房間網狀結構 Unity 中顯示的方式 索引標籤。
* 在 [**專案**] 面板中，尋找**材料**資料夾，然後選取**BlueLinesOnWalls**材料。
* 修改某些屬性，請參閱如何在 Unity 編輯器中顯示變更。
    * 在 [ **Inspector** ] 面板中，調整**LineScale**讓出現較粗或越窄資料行的值。
    * 在 [ **Inspector** ] 面板中，調整**LinesPerMeter**變更多少行出現在每個背景牆上的值。
* 按一下 **播放**，結束 預覽 模式。
* 建置和部署到 HoloLens 並觀察著色器呈現實際的介面上的顯示方式。

Unity 直接挑明解的預覽資料，但它一律是個不錯的主意，在裝置中的簽出轉譯。

## <a name="chapter-3---processing"></a>第 3 章-處理

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**目標**
* 了解技術來處理您的應用程式中使用的空間的對應資料。
* 分析空間對應的資料，來尋找飛機，並移除三角形。
* 使用全像放置平面。

**指示**
* 在 Unity**專案** 面板中，**全像投影**資料夾中，尋找**SpatialProcessing**物件。
* 拖放**SpatialProcessing**物件插入**階層**面板。

SpatialProcessing prefab 包含元件處理空間的對應資料。 **SurfaceMeshesToPlanes.cs**會尋找並產生空間的對應資料為基礎的平面。 我們將使用我們的應用程式中的平面，來代表牆壁、 樓層及上限。 也包含此 prefab **RemoveSurfaceVertices.cs**這可以移除空間對應網狀結構中的頂點。 這可以用來建立的網狀結構中的漏洞，或移除多餘的三角形，不再需要 （因為可以改用平面）。
* 在 Unity**專案** 面板中，**全像投影**資料夾中，尋找**SpaceCollection**物件。
* 將拖放**SpaceCollection**物件插入**階層**面板。
* 在 **階層**面板中，選取**SpatialProcessing**物件。
* 在 [ **Inspector** ] 面板中，尋找**播放 （指令碼） 的空間 Manager**元件。
* 按兩下**PlaySpaceManager.cs**在 Visual Studio 中開啟它。

PlaySpaceManager.cs 包含特定應用程式的程式碼。 我們會將功能加入此指令碼，以啟用下列行為：
1. 停止收集資料空間的對應之後我們超過掃描的時間限制 （10 秒）。
2. 處理序空間的對應資料：
    1. 您可以使用 SurfaceMeshesToPlanes 建立平面 （牆壁、 樓層、 上限等） 的簡單世界的表示法。
    2. 您可以使用 RemoveSurfaceVertices 移除介面平面界限內的三角形。
3. 在世界裡產生的全像投影集合，並將它們放在接近使用者的背景牆和樓層平面上。

完成中 PlaySpaceManager.cs，標示的程式碼撰寫練習，或從下方取代已完成解決方案的指令碼：

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**建置和部署**
* 在之前部署到 HoloLens 上，按下**播放**Unity 輸入播放模式中的按鈕。
* 聊天室網格會從檔案載入之後，請等候 10 秒前開始空間對應 mesh 上的處理。
* 處理序完成時，飛機會出現代表樓層、 牆壁、 ceiling、 等等。
* 在所有的平面會被發現，您應該會看到太陽系，會出現在接近觀景窗的樓層的資料表。
* 兩個海報應該會出現在接近觀景窗的背景牆上太。 切換至**場景**索引標籤上，如果看不到它們**遊戲**模式。
* 按下**播放** 按鈕以結束遊戲模式。
* 建置並部署至 HoloLens，像往常一樣。
* 等候掃描，以及處理空間的對應資料，才能完成。
* 一旦您看到平面，試著找出您的世界中的太陽系和海報。

## <a name="chapter-4---placement"></a>第 4 章-位置

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**目標**
* 決定是否全像圖都會百分之百符合介面上。
* 雷射可以或不符合在介面上時，請提供意見給使用者。

**指示**
* 在 Unity**階層**面板中，選取**SpatialProcessing**物件。
* 在 [ **Inspector** ] 面板中，尋找**介面網狀結構至平面 （指令碼）** 元件。
* 變更**繪製平面**屬性設**Nothing**清除選取項目。
* 變更**繪製平面**屬性設**牆**，如此一來，只有牆平面將會呈現。
* 在 [**專案**] 面板中，**指令碼**資料夾中，按兩下**Placeable.cs**在 Visual Studio 中開啟它。

**Placeable**指令碼已附加至平面尋找完成之後所建立的海報和投影。 我們只需要為一些程式碼，取消註解，此指令碼將會達到下列目的：
1. 決定是否全像圖都會百分之百符合由中央和四個角落的週框的 cube raycasting 介面上。
2. 請檢查以判斷是否順利清除坐全像圖的一般介面。
3. 轉譯時放顯示實際大小闀週框 olap cube。
4. 投射陰影下/背後全像圖來顯示它放置在 floor/塗鴉牆上。
5. 如果全像不能放在介面中或綠色，如果可以請為紅色，轉譯的陰影。
6. 重新導向以配合其同質性介面的型別 （垂直或水平） 全像圖。
7. 順暢全像置於選取的介面，以避免跳躍或貼齊行為。

在下面的程式碼撰寫練習中的所有程式碼取消註解，或使用內已完成的解決方案**Placeable.cs**:

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**建置和部署**
* 同樣地，建置專案，並將部署到 HoloLens。
* 等候掃描，以及處理空間的對應資料，才能完成。
* 當您看到太陽系時，注視下的 [投影] 方塊，並執行選取的動作並四處移動。 選取 [投影] 方塊時，請週框的 cube 會顯示該投影的周圍。
* 將您注視聊天室中的不同位置的標頭。 [投影] 方塊應遵循您的視線。 當陰影投射方塊下方會變成紅色時，您無法將全像圖放在該介面上。 當陰影投射方塊下方會變成綠色時，您可以將全像藉由執行另一個選取的筆勢。
* 尋找並選取其中一個全像攝影版的海報上將它移至新位置。 請注意，您無法將海報放上下限或上限，而且它會保持正確導向每個背景牆當您移動。

## <a name="chapter-5---occlusion"></a>第 5 章-阻擋

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**目標**
* 決定是否全像圖會阻擋空間對應網狀結構。
* 套用不同的阻擋物技術以達成一個有趣效果。

**指示**

首先，我們將允許 occlude 其他全像投影，而不需要 occluding 真實世界空間的對應網格：
* 在 **階層**面板中，選取**SpatialProcessing**物件。
* 在 [ **Inspector** ] 面板中，尋找**播放 （指令碼） 的空間 Manager**元件。
* 按一下右側的圓形**次要材料**屬性。
* 尋找並選取**阻擋**material 和關閉視窗。

接下來，我們會將地球，特殊的行為，使其具有藍色醒目提示，它會變成阻擋其他全像 （例如，sun)，或空間的對應網狀結構時：
* 在 [**專案**] 面板的**全像投影**資料夾中，展開**SolarSystem**物件。
* 按一下 **地球**。
* 在 [ **Inspector** ] 面板中，尋找地球的資料 （底部元件）。
* 在 **著色器下拉式清單**，變更著色器**自訂 > OcclusionRim**。 每當另一個物件阻擋，這會造成地球周圍的藍色醒目提示。

最後，我們會讓我們太陽系中行星 x 光視覺效果。 我們將需要編輯**PlanetOcclusion.cs** （Scripts\SolarSystem 資料夾中找到） 才能達成以下目標：
1. 決定是否要將全球 occluded SpatialMapping 層 （聊天室網格和平面）。
2. 顯示全球的線框表示法，每當 SpatialMapping 層阻擋。
3. 全球的線框表示法時隱藏 SpatialMapping 層不會封鎖它。

請依照下列程式碼撰寫練習在 PlanetOcclusion.cs，或使用下列解決方法：

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**建置和部署**
* 建置並如往常般部署 HoloLens，應用程式。
* 等候掃描和空間的對應資料，以完成處理 （您應該會看到出現在牆上的藍線）。
* 尋找和選取太陽系的 [投影] 方塊，然後將方塊旁邊的塗鴉牆或背後的計數器。
* 您可以檢視對等互連的海報，或是投影方塊介面背後的隱藏基本的阻擋物。
* 尋找地球，應該會有藍色醒目提示效果時它會在另一個全像圖或介面。
* 觀看行星移動在牆上或在聊天室中的其他介面。 現在，您會有 x 光，可以看到其框線基本架構 ！

## <a name="the-end"></a>結束

恭喜您！ 您現在已完成**MR 空間 230:空間對應**。
* 您知道如何將掃描您的環境和負載空間的對應資料到 Unity。
* 您了解著色器，以及如何使用資料，以重新在世界各地以視覺化方式檢視基本的概念。
* 您已了解新的處理技巧，來尋找平面移除網狀結構中的三角形。
* 您無法移動，並將全像投影放不二人選的表面。
* 您發生不同的阻擋物技術，已經超人威力 ！
