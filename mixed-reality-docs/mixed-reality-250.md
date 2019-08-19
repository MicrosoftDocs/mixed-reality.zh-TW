---
title: MR 分享 250-HoloLens 和沉浸式耳機
description: 遵循這份使用 Unity、Visual Studio、HoloLens 和 Windows Mixed Reality 耳機的編碼逐步解說, 瞭解在混合現實裝置之間共用全息影像的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 沉浸, 運動控制器, 共用, xbox 控制器, 網路, 跨裝置
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63506109"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。  因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊, 以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時, 使用這些教學課程的連結進行更新。

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR 分享 250:HoloLens 和沉浸式耳機

有了通用 Windows 平臺 (UWP) 的彈性, 您可以輕鬆地建立橫跨多個裝置的應用程式。 有了這種彈性, 我們就可以建立運用每個裝置的優勢的體驗。 本教學課程將涵蓋在 HoloLens 和 Windows Mixed Reality 沉浸式耳機上執行的基本共用體驗。 此內容原本是在華盛頓州西雅圖的 Microsoft Build 2017 會議中提供。

**在本教學課程中, 我們將:**

* 使用 UNET 設定網路。
* 跨混合現實裝置共用全息影像。
* 根據使用的混合現實裝置, 建立不同的應用程式視圖。
* 建立一個分享的體驗, 讓 HoloLens 使用者透過一些簡單的測驗, 引導沉浸式耳機使用者。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 分享 250:HoloLens 和沉浸式耳機</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

* Windows 10 電腦具有必要的[開發工具](install-the-tools.md), 並[已設定為支援 windows Mixed Reality 沉浸式頭戴式](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)裝置。
* 可與您的電腦搭配使用的 Xbox 控制器。
* 至少一部 HoloLens 裝置和一個沉浸式耳機。
* 允許 UDP 廣播進行探索的網路。

### <a name="project-files"></a>專案檔案

* 下載專案所需的[檔案](https://github.com/Microsoft/MixedReality250/archive/master.zip)。 將檔案解壓縮到容易記住的位置。
* 此專案需要[具有 Windows Mixed Reality 支援的建議版本 Unity](install-the-tools.md)。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼, 可以[在 GitHub 上](https://github.com/Microsoft/MixedReality250)取得。

## <a name="chapter-1---holo-world"></a>第1章-Hololens 世界

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>目標

請確定開發環境已準備好開始使用簡單的專案。

### <a name="what-we-will-build"></a>我們將建立的內容

一種應用程式, 可顯示 HoloLens 或 Windows Mixed Reality 沉浸式耳機的全息影像。

### <a name="steps"></a>步驟
* 開啟 Unity。
    * 選取 [**開啟**]。
    * 流覽至您解壓縮專案檔案的位置。
    * 按一下 [選擇資料夾]。
    * *Unity 需要一些時間才能第一次處理專案。*
* 檢查 Unity 中是否已啟用混合現實。
    * 開啟 [組建設定] 對話方塊 ([**控制項 + Shift + B** ] 或 [檔案 **> 組建設定**...])。
    * 選取**通用 Windows 平臺**, 然後按一下 [**切換平臺**]。
    * 選取 [**編輯 > 播放機設定**]。
    * 在右側的 [偵測**器**] 面板中, 展開 [ **XR 設定**]。
    * 勾選 [**支援虛擬實境**] 方塊。
    * *Windows Mixed Reality 應該是虛擬實境 SDK。*
* 建立場景。
    * 在階層中, 以滑鼠右鍵按一下**主要相機**選取 [**刪除**]。
    * 從**HoloToolkit > 輸入 > Prefabs**將**MixedRealityCameraParent**拖曳至階層。
* 將全息影像新增至場景
    * 從 [ **AppPrefabs** ] 將 [ **Skybox** ] 拖曳至**場景視圖**。
    * 從**AppPrefabs**將**經理**拖曳至階層。
    * 從 [ **AppPrefabs** ] 將 [**島**] 拖曳至階層。
* 儲存並建立
    * 儲存 ( **Control + S**或**File > 儲存場景**)
    * 因為這是新場景, 所以您必須將其命名為。 名稱並不重要, 但我們會使用 SharedMixedReality。
* 匯出至 Visual Studio
    * 開啟 [建立] 功能表 (**ctrl + Shift + B**或**File > 組建設定**)
    * 按一下 [**新增開啟的場景]。**
    * 檢查**Unity C#專案**
    * 按一下 [建置]。
    * 在出現的 [檔案瀏覽器] 視窗中, 建立名為 [**應用程式**] 的新資料夾。
    * 按一下 [**應用程式**] 資料夾。
    * 按 [**選取資料夾]。**
    * **等候組建完成**
    * 在出現的 [檔案瀏覽器] 視窗中, 流覽至 [**應用程式**] 資料夾。
    * 按兩下 [ **SharedMixedReality** ] 以啟動 Visual Studio
* 從 Visual Studio 建立
    * 使用頂端工具列將目標變更為 [**發行**] 和 [ **x86**]。
    * 按一下 [**本機電腦**] 旁的箭號, 然後選取 [要部署到 HoloLens 的**裝置**]
    * 按一下 [**裝置**] 旁的箭號, 然後選取 [**本機電腦**] 以部署混合現實耳機。
    * 按一下 [ **Debug-> 啟動但不**進行偵測] 或 [**控制 + F5** ] 來啟動應用程式。

### <a name="digging-into-the-code"></a>深入探討至程式碼

在 [專案] 面板中, 流覽至**Assets\HoloToolkit\Input\Scripts\Utilities** , 然後按兩下**MixedRealityCameraManager.cs**將其開啟。

**簡要**MixedRealityCameraManager.cs 是一個簡單的腳本, 可根據裝置調整品質層級和背景設定。 這裡的金鑰是 HolographicSettings. IsDisplayOpaque, 它可讓腳本偵測裝置是否為 HoloLens (IsDisplayOpaque 會傳回 false) 或沉浸式耳機 (IsDisplayOpaque 會傳回 true)。

### <a name="enjoy-your-progress"></a>享用您的進度

此時, 應用程式只會轉譯一個全息影像。 我們會在稍後新增與全息影像的互動。 這兩個裝置都會呈現相同的全息影像。 沉浸式耳機也會呈現藍色的天空和雲端背景。

## <a name="chapter-2---interaction"></a>第2章-互動

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>目標

示範如何處理 Windows Mixed Reality 應用程式的輸入。

### <a name="what-we-will-build"></a>我們將建立的內容

從第1章的應用程式開始, 我們將新增功能, 讓使用者能夠挑選全像投影, 並將它放在 HoloLens 的實際表面上, 或放置在沉浸式耳機的虛擬資料表上。

**輸入重新整理器:** 在 HoloLens 上, 選取筆勢是「**空中碰**」。 在沉浸式耳機上, 我們將使用 Xbox 控制器上的 [ **A** ] 按鈕。 如需輸入的詳細資訊, 請[從這裡開始](gestures.md)。

### <a name="steps"></a>步驟
* 新增輸入管理員
    * 從**HoloToolkit > 輸入 > Prefabs**將 [ **InputManager** ] 拖曳至 [階層] 做為**經理**的子系。
    * 從**HoloToolkit > 輸入 > Prefabs > 資料指標**將**游標**拖曳至階層。
* 新增空間對應
    * 從**HoloToolkit > SpatialMapping > Prefabs**將 [ **SpatialMapping** ] 拖曳至 [階層]。
* 新增虛擬 Playspace
    * 在階層中展開**MixedRealityCameraParent**選取**界限**
    * 在 [偵測**器**] 面板中, 核取 [啟用**界限**] 方塊
    * 從 [ **AppPrefabs** ] 將[ **VRRoom** ] 拖曳至 [階層]。
* 新增 WorldAnchorManager
    * 在[階層] 中, 選取 [**管理員**]。
    * 在 [偵測**器**] 中, 按一下 [**新增元件**]。
    * 輸入**世界錨點管理員**。
    * 選取 [**全球錨點管理員**] 將它加入。
* 將 TapToPlace 新增至島
    * 在[階層] 中, 展開 [**島**]。
    * 選取 [ **MixedRealityLand**]。
    * 在 [偵測**器**] 中, 按一下 [**新增元件**]。
    * 輸入點一下並加以選取。
    * 勾選 **[將父系放在點上**]。
    * 將**放置位移**設定為 **(0, 0.1, 0)** 。
* 儲存並建立成先前的

### <a name="digging-into-the-code"></a>深入探討至程式碼

**腳本 1-GamepadInput.cs**

在 [專案] 面板中, 流覽至**Assets\HoloToolkit\Input\Scripts\InputSources** , 然後按兩下**GamepadInput.cs**將其開啟。 在 [專案] 面板的相同路徑中, 也按兩下 [ **InteractionSourceInputSource.cs**]。

請注意, 這兩個腳本都有通用的基類 BaseInputSource。

BaseInputSource 會保留對 InputManager 的參考, 讓腳本能夠觸發事件。 在此情況下, InputClicked 事件是相關的。 當我們進入腳本 2, TapToPlace 時, 請務必記住這一點。 在 GamePadInput 的案例中, 我們會輪詢要按下控制器上的按鈕, 然後再引發 InputClicked 事件。 在 InteractionSourceInputSource 的案例中, 我們會引發 InputClicked 事件以回應 TappedEvent。

**腳本 2-TapToPlace.cs**

在 [專案] 面板中, 流覽至**Assets\HoloToolkit\SpatialMapping\Scripts** , 然後按兩下**TapToPlace.cs**將其開啟。

開發人員在建立全像攝影應用程式時想要執行的第一件事, 就是使用手勢輸入來移動全息影像。 因此, 我們已 endeavored 完整批註此腳本。 在本教學課程中, 有幾件事值得特別強調。

首先, 請注意, TapToPlace 會執行 IInputClickHandler。 IInputClickHandler 會公開函式, 這些函式會處理 GamePadInput.cs 或 InteractionSourceInputSource.cs 所引發的 InputClicked 事件。 當 BaseInputSource 偵測到點擊, 而具有 TapToPlace 的物件處於焦點時, 就會呼叫 OnInputClicked。 Airtapping 在 HoloLens 上或按下 Xbox 控制器上的按鈕, 將會觸發事件。

第二種是在 update 中執行程式碼, 以查看是否正在查看表面, 讓我們可以將遊戲物件放在表面上, 例如資料表。 沉浸式耳機沒有實際表面的概念, 因此代表資料表 top (隆隆 > TableThingy > Cube) 的物件已標記 SpatialMapping 實體層, 因此更新中的光線轉型會與虛擬資料表頂端衝突。

### <a name="enjoy-your-progress"></a>享用您的進度

這次您可以選取要移動的島。 在 HoloLens 上, 您可以將島移至實際表面。 在沉浸式耳機中, 您可以將島移至我們新增的虛擬資料表。

## <a name="chapter-3---sharing"></a>第3章-共用

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>目標

請確定已正確設定網路, 並詳細說明如何在裝置之間共用空間錨點。

### <a name="what-we-will-build"></a>我們將建立的內容

我們會將專案轉換成多人遊戲專案。 我們會將 UI 和邏輯新增至主機或加入會話。 HoloLens 使用者會在會話中看到彼此的雲端, 而沉浸式耳機使用者在錨點所在位置附近有雲端。 沉浸式耳機中的使用者會看到 HoloLens 使用者相對於場景的原點。 HoloLens 使用者會在同一個位置看到島的全息影像。 重點是要注意的是, 沉浸式耳機中的使用者不會在這一章的島上, 但其行為非常類似 HoloLens, 而且具有鳥瞰圖。

### <a name="steps"></a>步驟
* 移除島和 VRRoom
    * 在階層中, 以滑鼠右鍵按一下 [**島**] 選取 [**刪除**]
    * 在階層中, 以滑鼠右鍵按一下**VRRoom**選取 [**刪除**]
* 新增 Usland
    * 從 [ **AppPrefabs** ] 將[ **Usland** ] 拖曳至 [階層]。
* 從 [ **AppPrefabs** ] 將下列每一個都拖曳至 [階層]:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* 儲存並建立成先前的

### <a name="digging-into-the-code"></a>深入探討至程式碼

在 [專案] 面板中, 流覽至**Assets\AppPrefabs\Support\SharingWithUnet\Scripts** , 然後按兩下 [ **UnetAnchorManager.cs**]。 一個 HoloLens 與另一個 HoloLens 共用追蹤資訊的能力, 讓這兩個裝置都可以共用相同的空間, 接近神奇。 當有兩個以上的人可以使用相同的數位資料共同作業時, 混合現實的威力就會保持運作。

在此腳本中要指出的幾件事:

在 start 函式中, 注意**IsDisplayOpaque**的檢查。 在此情況下, 我們會假設已建立錨點。 這是因為沉浸式耳機不會公開匯入或匯出錨點的方式。 不過, 如果我們在 HoloLens 上執行, 此腳本會在裝置之間執行共用錨點。 啟動會話的裝置將會建立錨點以供匯出。 加入會話的裝置會向啟動會話的裝置要求錨點。

**導**

當使用者建立會話時, NetworkDiscoveryWithAnchors 將會呼叫 UNETAnchorManagers CreateAnchor function。 讓我們遵循 CreateAnchor flow。

我們一開始會先進行一些維護, 清除我們針對先前錨點收集的任何資料。 然後, 我們會檢查是否有要載入的快取錨點。 錨點資料通常介於5到 20 MB 之間, 因此重複使用快取的錨點可以節省我們需要透過網路傳輸的資料量。 我們稍後會看到其運作方式。 即使我們重複使用錨點, 我們還是需要在沒有錨點的新用戶端聯結時, 讓錨點資料準備就緒。

說到準備錨點資料, WorldAnchorTransferBatch 類別會公開功能來準備錨定資料, 以便傳送到其他裝置或應用程式, 以及匯入錨定資料的功能。 因為我們是在匯出路徑, 所以我們會將錨點新增至 WorldAnchorTransferBatch 並呼叫 ExportAsync 函式。 然後, ExportAsync 會在產生要匯出的資料時呼叫 WriteBuffer 回呼。 匯出所有資料之後, 就會呼叫 ExportComplete。 在 WriteBuffer 中, 我們會將資料區塊新增至我們保留以進行匯出的清單。 在 ExportComplete 中, 我們會將清單轉換成陣列。 也會設定 AnchorName 變數, 這會觸發其他裝置來要求錨點 (如果沒有的話)。

在某些情況下, 錨點不會匯出或建立幾乎不會再試一次的資料。 在這裡, 我們就再次呼叫 CreateAnchor。

匯出路徑中的最後一個函式是 AnchorFoundRemotely。 當另一個裝置找到錨點時, 該裝置將會告訴主機, 而主機將會使用它來表示錨點為「良好錨點」, 而且可以快取。

**導**

當 HoloLens 加入會話時, 它需要匯入錨點。 在 UNETAnchorManager 的 Update 函式中, 會輪詢 AnchorName。 當錨點名稱變更時, 就會開始匯入程式。 首先, 我們會嘗試從本機錨點存放區載入具有指定名稱的錨點。 如果已經有, 我們就可以使用它, 而不需要再次下載資料。 如果沒有, 則我們會呼叫 WaitForAnchor, 以起始下載。

當下載完成時, 會呼叫 NetworkTransmitter_dataReadyEvent。 這會通知更新迴圈使用下載的資料來呼叫 ImportAsync。 當匯入程式完成時, ImportAsync 會呼叫 ImportComplete。 如果匯入成功, 錨點會儲存在本機播放機存放區中。 PlayerController.cs 實際上會呼叫 AnchorFoundRemotely, 讓主機知道已建立良好的錨點。

### <a name="enjoy-your-progress"></a>享用您的進度

這次具有 HoloLens 的使用者將會使用 UI 中的 [**啟動會話**] 按鈕來主控會話。 其他使用者 (在 HoloLens 或沉浸式頭戴式裝置上) 會選取該會話, 然後在 UI 中選取 [**加入會話**] 按鈕。 如果您有多個使用 HoloLens 裝置的人員, 他們的標題將會有紅色雲端。 每個沉浸式耳機也會有一個藍色的雲端, 但是藍色的雲不會在耳機上方, 因為耳機不會嘗試尋找與 HoloLens 裝置相同的全局座標空間。

專案中的這個點是包含的共用應用程式;它不會執行太多動作, 而且可能做為基準。 在接下來的章節中, 我們將開始打造讓大家享受的體驗。 若要取得有關共用體驗設計的進一步指引, 請移至這裡。

## <a name="chapter-4---immersion-and-teleporting"></a>第4章-深度和 teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>目標

滿足每種混合現實裝置類型的體驗。

### <a name="what-we-will-build"></a>我們將建立的內容

我們將更新應用程式, 以沉浸式視圖將沉浸式耳機使用者放在島上。 HoloLens 使用者仍然會看到島的鳥瞰圖。 每種裝置類型的使用者都可以看到其他使用者出現在世界中的情況。 比方說, 沉浸式耳機使用者可以看到其他虛擬人偶在島上的其他路徑, 並在島上看到 HoloLens 使用者為巨型雲端。 如果 HoloLens 使用者正在查看島, 則沉浸式耳機使用者也會看到 HoloLens 使用者的注視光線游標。 HoloLens 使用者會在島上看到代表每個沉浸式耳機使用者的圖片。

**已更新沉浸式裝置的輸入:**
* Xbox 控制器上的左緩衝和右緩衝按鈕會旋轉玩家
* 在 Xbox 控制器上保留 Y 按鈕, 將會啟用 [[傳送](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)] 游標。 當您放開 Y 按鈕時, 如果游標具有旋轉箭號指標, 您就會傳送到游標的位置。

### <a name="steps"></a>步驟
* 將 MixedRealityTeleport 新增至 MixedRealityCameraParent
    * 在[階層] 中, 選取 [ **Usland**]。
    * 在 [偵測**器**] 中, 啟用**層級控制**。
    * 在[階層] 中, 選取 [ **MixedRealityCameraParent**]。
    * 在 [偵測**器**] 中, 按一下 [**新增元件**]。
    * 輸入**Mixed Reality 傳送**並加以選取。

### <a name="digging-into-the-code"></a>深入探討至程式碼

沉浸式耳機使用者將使用纜線行動網卡到他們的電腦上, 但我們的島大於纜線的長度。 若要補償, 我們必須能夠在使用者的動作以外獨立移動相機。 如需有關設計混合現實應用程式 (特別是自我動作和 locomotion) 的詳細資訊, 請參閱[舒適頁面](comfort.md)。

為了描述此程式, 定義兩個詞彙將會很有説明。 首先, **dolly**會是與使用者獨立移動相機的物件。 **Dolly**的子遊戲物件將會是**主要攝影機**。 主要相機會附加到使用者的標頭。

在 [專案] 面板中, 流覽至**Assets\AppPrefabs\Support\Scripts\GameLogic** , 然後按兩下 [ **MixedRealityTeleport.cs**]。

MixedRealityTeleport 有兩個作業。 首先, 它會使用「緩衝器」來處理旋轉。 在 update 函式中, 我們會輪詢 LeftBumper 和 RightBumper 上的 ' ButtonUp '。 GetButtonUp 只會在第一個畫面格上傳回 true, 而按鈕在關閉之後就會出現。 如果已引發任一按鈕, 則我們知道使用者需要旋轉。

當我們旋轉時, 我們會使用稱為「淡化控制項」的簡單腳本, 淡出並淡入。 這麼做是為了防止使用者看到可能導致 discomfort 的非自然移動。 淡入和放大效果相當簡單。 在**主攝影機**前方, 我們有黑色的四場懸掛。 當您淡出時, 會將 Alpha 值從0轉換成1。 這會逐漸導致四顆十字的黑色圖元呈現並遮蔽其背後的任何內容。 淡入後, 我們會將 Alpha 值轉換回零。

當我們計算旋轉時, 請注意, 我們會旋轉**dolly** , 但計算**主要攝影機**周圍的旋轉。 這一點很重要, 因為**主相機**遠離 0, 0, 0, 從使用者的觀點來看, dolly 的旋轉就愈不精確。 事實上, 如果您不繞著相機位置旋轉, 使用者會在**dolly**前後移動, 而不是旋轉。

MixedRealityTeleport 的第二個工作是處理移動**dolly**。 這會在 SetWorldPosition 中完成。 SetWorldPosition 會採用所需的世界位置, 也就是使用者想要 percieve 他們占的位置。 我們必須將**dolly**放在該位置, 而不是**主攝影機**的本機位置, 因為每個畫面格都會加入該位移。

第二個腳本會呼叫 SetWorldPosition。 我們來看一下該腳本。 在 [專案] 面板中, 流覽至**Assets\AppPrefabs\Support\Scripts\GameLogic** , 然後按兩下 [ **TeleportScript.cs**]。

這段腳本比 MixedRealityTeleport 稍微複雜一點。 腳本正在檢查 Xbox controller 上的 Y 按鈕是否要保持關閉狀態。 當按鈕被關閉時, 會轉譯一個傳送游標, 而腳本會將光線從使用者的注視位置轉換出來。 如果該光線與較多或較不重要的表面衝突, 則會將介面視為要傳送至的表面, 並會啟用 [傳送] 游標上的動畫。 如果光線不會與表面出現較多或較少的指標, 則會停用游標上的動畫。 當 Y 按鈕放開, 而且光線的計算點是有效的位置時, 腳本會以光線相交的位置來呼叫 SetWorldPosition。

### <a name="enjoy-your-progress"></a>享用您的進度

這次您需要尋找 friend。

同樣地, 具有 HoloLens 的使用者會主控一個會話。 其他使用者將加入此會話。 應用程式會將前三個使用者加入至島上三個路徑之一的沉浸式耳機。 歡迎您流覽本節的小島。

要注意的詳細資料:
1. 您可以在雲端中看到臉部, 協助可以沉浸使用者查看 HoloLens 使用者所尋找的方向。
2. 島上的虛擬人偶具有旋轉的 necks。 他們不會遵循使用者所做的實際事 (我們沒有這項資訊), 而是提供絕佳的體驗。
3. 如果 HoloLens 使用者正在查看島, 可以沉浸使用者可以看到其游標。
4. 代表 HoloLens 使用者轉換陰影的雲端。

## <a name="chapter-5---finale"></a>第5章-Finale

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>目標

在兩種裝置類型之間建立共同作業的互動體驗。

### <a name="what-we-will-build"></a>我們將建立的內容

以第4章為基礎, 當具有沉浸式耳機的使用者接近島上的拼圖時, HoloLens 使用者會取得工具提示, 其中包含拼圖的線索。 一旦所有的沉浸式耳機使用者都在 rocket 室的「ready pad」之後, rocket 就會啟動。

### <a name="steps"></a>步驟
* 在[階層] 中, 選取 [ **Usland**]。
* 在 [**檢查**] 的 [**層級控制**] 中, 勾選 [**啟用**共同作業]。

### <a name="digging-into-the-code"></a>深入探討至程式碼

現在讓我們來看一下 LevelControl.cs。 此腳本是遊戲邏輯的核心, 並會維護遊戲狀態。 因為這是使用 UNET 的多玩家遊戲, 所以我們需要瞭解資料流程的運作方式, 至少是為了修改本教學課程。 如需 UNET 的完整總覽, 請參閱 Unity 檔。

在 [專案] 面板中, 流覽至**Assets\AppPrefabs\Support\Scripts\GameLogic** , 然後按兩下 [ **LevelControl.cs**]。

讓我們瞭解沉浸式耳機如何表示它們已準備好開始 rocket。 在對應于島上三個路徑的布林清單中, 設定三個布林的其中一個, 即可傳達 Rocket 啟動的準備就緒。 當指派給路徑的使用者在 rocket 房間內的棕色填補上方時, 將會設定路徑的 bool。 好, 現在就來瞭解詳細資料。

我們會從 Update () 函數開始。 您會注意到有一個「功能提要」函式。 我們在開發過程中使用此功能來測試 rocket 的啟動和重設順序。 這無法在多使用者體驗中使用。 希望您在地下列資訊時, 可以讓它發揮作用。 查看是否有任何功能之後, 我們會檢查本機播放機是否已可以沉浸。 我們想要專注于我們如何找出我們的目標。 在 if (可以沉浸) 檢查內, 會呼叫 CheckGoal 隱藏在**EnableCollaboration** bool 後面。 這會對應到您在完成本章的步驟時所檢查的核取方塊。 在 EnableCollaboration 內部, 我們看到 CheckGoal () 的呼叫。

CheckGoal 會執行一些數學運算, 以查看是否有更多或更低的面板。 在我們的時候, 我們會進行 Debug。記錄「到達目標」, 然後呼叫「SendAtGoalMessage ()」。 在 SendAtGoalMessage 中, 我們會呼叫 playerController. SendAtGoal。 為了節省一些時間, 以下是程式碼:

```cs
private void CmdSendAtGoal(int GoalIndex)
       {
           levelState.SetGoalIndex(GoalIndex);
       }
```

```cs
public void SendAtGoal(int GoalIndex)
       {
           if (isLocalPlayer)
           {
               Debug.Log("sending at goal " + GoalIndex);
               CmdSendAtGoal(GoalIndex);
           }
       }
```

請注意, SendAtGoalMessage 會呼叫 CmdSendAtGoal, 它會呼叫 levelState, 而此 SetGoalIndex 會回到 LevelControl.cs。 乍看之下, 這似乎有點奇怪。 為什麼不直接呼叫 SetGoalIndex, 而不是透過 player 控制器來進行這種奇怪的路由？ 原因是我們符合資料模型 UNET 用來讓資料保持同步。若要防止作弊和抖動, UNET 會要求每個物件都有有權變更已同步處理之變數的使用者。 此外, 只有主機 (啟動會話的使用者) 可以直接變更資料。 不是主機但具有許可權的使用者, 必須將「命令」傳送到將變更變數的主機。 根據預設, 主機具有所有物件的授權, 但衍生來代表使用者的物件除外。 在我們的案例中, 此物件具有 playercontroller 腳本。 有一種方法可以要求物件的授權, 然後進行變更, 但是我們選擇利用 player 控制器具有自我授權, 並透過 player 控制器路由傳送命令。

換句話說, 當我們發現自己的目標時, 玩家必須告訴主機, 而主機會告訴其他人。

回到 LevelControl.cs 查看 SetGoalIndex。 在這裡, 我們將設定 synclist (AtGoal) 中的值。 請記住, 當我們執行這項操作時, 我們是在主機的內容中。 類似于命令, RPC 是主機可能發出的專案, 這會導致所有用戶端執行一些程式碼。 在此我們稱之為「RpcCheckAllGoals」。 每個用戶端會個別檢查是否已設定這三個 AtGoals, 如果是, 則啟動 rocket。

### <a name="enjoy-your-progress"></a>享用您的進度

在上一章中, 我們將以先前的方式開始會話。 這次當沉浸式耳機中的使用者到達其路徑上的「門」時, 就會出現只有 HoloLens 使用者可以看到的工具提示。 HoloLens 使用者會負責將此線索傳達給沉浸式耳機中的使用者。 當每個頭像在火山內的對應棕色填補之後, rocket 就會啟動到空間。 場景會在60秒後重設, 讓您可以再次執行。

## <a name="see-also"></a>另請參閱
* [MR Input 213：運動控制器](mixed-reality-213.md)
