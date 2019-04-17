---
title: 共用 250-HoloLens 和沈浸式耳機 MR
description: 遵循此程式碼逐步解說如何使用 Unity、 Visual Studio、 HoloLens、 及 Windows Mixed Reality 耳機，若要了解共用全像投影混合的實境裝置之間的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity 沉浸式動作控制站、 共用、 xbox 控制器、 網路、 跨裝置
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591227"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR 共用 250:HoloLens 和沈浸式耳機

彈性的通用 Windows 平台 (UWP) 中，很容易就能建立跨越多個裝置的應用程式。 這種彈性，我們可以建立體驗，運用每個裝置的優點。 本教學課程將涵蓋基本的共用的經驗 HoloLens 與 Windows Mixed Reality 沈浸式耳機上執行。 原本在華盛頓州西雅圖市 Microsoft Build 2017 大會要傳遞此內容。

**在本教學課程中，我們將：**

* 安裝程式使用 UNET 的網路。
* 在混合的實境裝置之間共用全像投影。
* 建立依據正在使用混合的實境裝置的應用程式的不同檢視。
* 建立其中 HoloLens 使用者指南透過一些簡單的謎題的沈浸式耳機使用者分享的經驗。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 共用 250:HoloLens 和沈浸式耳機</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>先決條件

* 使用 Windows 10 電腦[必要的開發工具](install-the-tools.md)並[設定為支援 Windows Mixed Reality 沈浸式耳機](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。
* 適用於您的 PC Xbox 控制器。
* 至少一個 HoloLens 裝置和一個沈浸式耳機。
* 這樣可探索的 UDP 廣播網路。

### <a name="project-files"></a>專案檔

* 下載[檔案](https://github.com/Microsoft/MixedReality250/archive/master.zip)專案所需。 將檔案解壓縮至好記的位置。
* 此專案需要[Unity 的 Windows Mixed Reality 支援與建議的版本](install-the-tools.md)。

>[!NOTE]
>如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/MixedReality250)。

## <a name="chapter-1---holo-world"></a>第 1 章-Holo 世界

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>目標

請確定開發環境已準備好開始使用簡單的專案。

### <a name="what-we-will-build"></a>我們將建置的項目

應用程式，以顯示雷射 HoloLens 或 Windows Mixed Reality 沈浸式耳機。

### <a name="steps"></a>步驟
* 開啟 Unity。
    * 選取 **開啟**。
    * 瀏覽至您解壓縮專案檔。
    * 按一下 [選擇資料夾]。
    * *它會花上一點的第一次處理專案的 Unity 時。*
* 在 Unity 中，會啟用混合實境的檢查。
    * 開啟 [組建設定] 對話方塊 (**控制 + Shift + B**或**檔案 > 組建設定...**).
    * 選取 **通用 Windows 平台**然後按一下**切換平台**。
    * 選取 **編輯 > 播放程式設定**。
    * 在 [ **Inspector**在右手邊] 面板中，展開**XR 設定**。
    * 請檢查**受支援的虛擬實境** 方塊中。
    * *Windows Mixed Reality 應該是虛擬實境 SDK。*
* 建立場景。
    * 在 **階層**以滑鼠右鍵按一下**Main Camera**選取**刪除**。
    * 從**HoloToolkit > 輸入 > Prefabs**拖曳**MixedRealityCameraParent**來**階層**。
* 新增至場景的全像投影
    * 從**AppPrefabs**拖曳**天空盒**來**場景檢視**。
    * 從**AppPrefabs**拖曳**經理**來**階層**。
    * 從**AppPrefabs**拖曳**島**來**階層**。
* 儲存並建置
    * 儲存 (任一**Control + S**或是**檔案 > 儲存場景**)
    * 由於這是新場景，您必須為它命名。 名稱並不重要，但我們會使用 SharedMixedReality。
* 匯出至 Visual Studio
    * 開啟 [建置] 功能表 (**控制 + Shift + B**或是**檔案 > 組建設定**)
    * 按一下 **加入開啟的場景。**
    * 請檢查**UnityC#專案**
    * 按一下 [建置] 。
    * 在出現檔案總管 視窗，建立名為的新資料夾**應用程式**。
    * 只要按一下**應用程式**資料夾。
    * 按下**選取資料夾。**
    * **等待建置完成**
    * 在出現的 [檔案總管] 視窗，瀏覽到**應用程式**資料夾。
    * 按兩下**SharedMixedReality.sln**即可啟動 Visual Studio
* 從 Visual Studio 建置
    * 使用頂端的工具列來變更目標，以便**Release**並**x86**。
    * 按一下箭號旁**本機電腦**，然後選取**裝置**將部署到 HoloLens
    * 按一下箭號旁**裝置**，然後選取**本機**来部署的混合的實境耳機。
    * 按一下 **偵錯-> 啟動但不偵錯**或是**控制 + F5**啟動應用程式。

### <a name="digging-into-the-code"></a>深入探討程式碼

在 [專案] 面板中，瀏覽至**Assets\HoloToolkit\Input\Scripts\Utilities** ，然後按兩下**MixedRealityCameraManager.cs**加以開啟。

**概觀：** MixedRealityCameraManager.cs 是簡單的指令碼會根據裝置的品質等級和背景設定進行調整。 這是索引鍵，以下是 HolographicSettings.IsDisplayOpaque，可讓指令碼來偵測裝置是否為 HoloLens （IsDisplayOpaque 傳回 false） 或沈浸式用耳機 （IsDisplayOpaque 傳回，則為 true）。

### <a name="enjoy-your-progress"></a>享受您的進度

此時應用程式將只會呈現全像圖。 我們將在稍後將互動加入全像圖。 這兩個裝置會呈現全像而相同。 沈浸式耳機中還會顯示藍色的天空和雲端背景。

## <a name="chapter-2---interaction"></a>第 2 章-互動

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>目標

示範如何處理 Windows Mixed Reality 應用程式的輸入。

### <a name="what-we-will-build"></a>我們將建置的項目

基礎第 1 章應用程式，我們會新增功能，可讓使用者挑選全像圖，並將它放一份虛擬資料表中的沈浸式耳機或 HoloLens 的真實世界平面上。

**輸入的重新整理程式：** 選取的動作是 HoloLens 上**空中點選**。 在沉浸式耳機，我們將使用**A** Xbox 控制器上的按鈕。 如需有關輸入[從這裡開始](gestures.md)。

### <a name="steps"></a>步驟
* 新增輸入管理員
    * 從**HoloToolkit > 輸入 > Prefabs**拖曳**InputManager**來**階層**為子系**管理員**。
    * 從**HoloToolkit > 輸入 > Prefabs > 資料指標**拖曳**游標**來**階層**。
* 新增空間對應
    * 從**HoloToolkit > SpatialMapping > Prefabs**拖曳**SpatialMapping**來**階層**。
* 新增虛擬 Playspace
    * 在 **階層**展開**MixedRealityCameraParent**選取**界限**
    * 在  **Inspector**面板核取此方塊可啟用**界限**
    * 從**AppPrefabs**拖曳**VRRoom**來**階層**。
* 新增 WorldAnchorManager
    * 在 **階層**，選取**管理員**。
    * 在  **Inspector**，按一下**新增元件**。
    * 型別**世界錨點 Manager**。
    * 選取 **世界錨點 Manager**將它加入。
* 新增 TapToPlace 島
    * 在 **階層**，展開**島**。
    * 選取  **MixedRealityLand**。
    * 在  **Inspector**，按一下**新增元件**。
    * 型別**點選到另一個地方**並加以選取。
    * 請檢查**父置於點選**。
    * 設定**放置位移**要 **（0、 0.1，0）**。
* 儲存並建置和以前一樣

### <a name="digging-into-the-code"></a>深入探討程式碼

**Script 1 - GamepadInput.cs**

在 [專案] 面板中，巡覽至**Assets\HoloToolkit\Input\Scripts\InputSources** ，然後按兩下**GamepadInput.cs**加以開啟。 從 [專案] 面板中相同的路徑，也按兩下**InteractionSourceInputSource.cs**。

請注意，這兩個指令碼常見的基底類別，稱為 BaseInputSource。

BaseInputSource 會保留 InputManager，讓觸發程序事件的指令碼的參考。 在此情況下，InputClicked 事件無關。 這會是一定要記住，當我們要編寫指令碼 2 TapToPlace 時。 如果 GamePadInput，是我們輪詢被按下控制器上的按鈕，然後我們引發 InputClicked 事件。 在 InteractionSourceInputSource，我們會引發以回應 TappedEvent InputClicked 事件。

**指令碼 2-TapToPlace.cs**

在 [專案] 面板中，巡覽至**Assets\HoloToolkit\SpatialMapping\Scripts** ，然後按兩下**TapToPlace.cs**加以開啟。

許多開發人員想要實作建立全像攝影版的應用程式時第一件事將全像投影移筆勢輸入。 因此，我們已 endeavored 徹底註解此指令碼。 幾件事是值得的本教學課程中反白顯示。

首先，請注意 TapToPlace 實作 IInputClickHandler。 IInputClickHandler 公開處理 GamePadInput.cs 或 InteractionSourceInputSource.cs 引發 InputClicked 事件的函式。 OnInputClicked 時 BaseInputSource 偵測到按一下 TapToPlace 物件處於焦點時呼叫。 是空中點選上 HoloLens 或 Xbox 控制器上按下的按鈕會觸發此事件。

第二個是會執行的程式碼，請參閱是否介面正在進行調查讓我們可以將遊戲物件放在介面上，例如資料表的更新中。 沈浸式耳機沒有概念，以實際的介面，因此表示資料表頂端的物件 (Vroom > TableThingy > Cube) 已標有 SpatialMapping 物理圖層，因此光線轉換更新中將使用虛擬資料表的最上層相衝突。

### <a name="enjoy-your-progress"></a>享受您的進度

此時您可以選取，將它移島。 HoloLens 您可以將島移到實際的介面。 在沉浸式耳機中，您可以移動島我們新增的虛擬資料表。

## <a name="chapter-3---sharing"></a>第 3 章-共用

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>目標

確定已正確設定網路，並詳細說明如何空間的錨點會在裝置之間共用。

### <a name="what-we-will-build"></a>我們將建置的項目

我們會將我們的專案轉換成多人遊戲的專案。 我們會將 UI 和邏輯新增至主機或聯結的工作階段。 HoloLens 使用者會在其標頭中，透過與雲端工作階段中彼此看到和沈浸式耳機使用者有接近錨點所在的雲端。 沈浸式耳機中的使用者會看到 HoloLens 使用者相對於場景的原點。 HoloLens 使用者會看到相同的位置島的全像圖。 它是關鍵請注意，沈浸式耳機中的使用者將無法島上在本章中，但將的運作方式非常類似 HoloLens，與島俯瞰檢視。

### <a name="steps"></a>步驟
* 移除島及 VRRoom
    * 在 **階層**上按一下滑鼠右鍵**島**選取**刪除**
    * 在 **階層**上按一下滑鼠右鍵**VRRoom**選取**刪除**
* 新增 Usland
    * 從**AppPrefabs**拖曳**Usland**來**階層**。
* 從**AppPrefabs**拖曳到下列每個**階層**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* 儲存並建置和以前一樣

### <a name="digging-into-the-code"></a>深入探討程式碼

在 [專案] 面板中，瀏覽至**Assets\AppPrefabs\Support\SharingWithUnet\Scripts** ，然後按兩下**UnetAnchorManager.cs**。 將追蹤資訊分享另一個 HoloLens，使得這兩個裝置都可以共用相同的空間的一個 HoloLens 讓即將神奇。 混合實境的強大功能會保持運作，當兩個或更多人可以使用相同的數位資料共同作業。

指出此指令碼中的幾件事：

在開始函式，請注意檢查**IsDisplayOpaque**。 在此情況下，我們會假裝會建立錨點。 這是因為沈浸式耳機不會公開匯入或匯出的錨點的方式。 如果我們 HoloLens 上執行，不過，此指令碼會實作在裝置之間共用的錨點。 啟動工作階段的裝置將會建立匯出的錨點。 裝置加入工作階段時，會要求從裝置啟動工作階段的錨點。

**匯出：**

當使用者建立工作階段時，NetworkDiscoveryWithAnchors 會呼叫 UNETAnchorManagers CreateAnchor 函式。 讓我們遵循 CreateAnchor 流程。

我們先進行一些內部管理工作，我們可能會收集前一個錨點的任何資料清除。 然後我們會檢查是否有快取的錨點，來載入。 錨點的資料通常會介於 5 到 20 MB，以便重複使用快取的錨點儲存我們需要透過網路傳送的資料量。 我們會看到其運作方式稍待片刻。 即使我們要重複使用錨點，我們需要取得備妥資料以防新用戶端所加入的沒有錨點錨點。

說到備妥錨點的資料，則 WorldAnchorTransferBatch 類別會公開以準備錨點的資料傳送至另一個裝置或應用程式和功能的錨點的資料匯入的功能。 因為我們在匯出路徑上，我們會將我們的錨點加入至 WorldAnchorTransferBatch，並呼叫 ExportAsync 函式。 ExportAsync 會接著呼叫 WriteBuffer 回呼，它會產生匯出的資料。 已匯出的所有資料時，就會呼叫 ExportComplete。 在 WriteBuffer 我們加入資料的區塊的清單，我們會保留用於匯出。 ExportComplete 中我們將清單轉換為陣列。 AnchorName 也設定變數，這將會觸發其他裝置來要求錨點，不需要它。

在某些情況下，不會匯出錨點，或將建立這麼少的資料，我們會再試一次。 這裡我們只需要呼叫 CreateAnchor 一次。

在匯出路徑的最後一個函式是 AnchorFoundRemotely。 當其他裝置找到錨點時，該裝置將會通知主機和主機將會使用它做為錨點是 「 良好錨點 」 的訊號，並可以快取。

**匯入：**

當 HoloLens 加入工作階段時，它需要匯入錨點。 在 UNETAnchorManager 的更新函式，AnchorName 輪詢一次。 當錨定名稱變更時，便會開始匯入程序。 首先，我們會試著從本機的錨點存放區載入具有指定名稱的錨點。 如果我們還沒有它，我們可以使用它，而不需要再次下載資料。 如果我們沒有它，然後我們會呼叫 WaitForAnchor 這會起始下載。

當下載完成時，會呼叫 NetworkTransmitter_dataReadyEvent。 這會指示使用下載的資料呼叫 ImportAsync Update 迴圈。 ImportAsync 匯入程序完成時，會呼叫 ImportComplete。 如果匯入成功時，錨點會儲存在本機的播放程式存放區中。 PlayerController.cs 實際上是 AnchorFoundRemotely 的呼叫，讓主機知道確實已建立好的錨點。

### <a name="enjoy-your-progress"></a>享受您的進度

這次的使用者與 HoloLens 將主控工作階段，使用**啟動工作階段**在 UI 中的按鈕。 其他使用者，同時在 HoloLens 或沈浸式耳機，將選取的工作階段，然後選取**收聽廣播**在 UI 中的按鈕。 如果您有多人與 HoloLens 裝置時，他們將會對它們的頭來紅色的雲端。 也會針對每個沈浸式耳機，藍色定域機組，但藍色的雲端不會高於耳機，耳機未嘗試尋找為 HoloLens 裝置相同的全局座標空間。

此專案中的點是自主的共用應用程式中;它不會執行很多，無法做為基準。 在下一個章節中，我們將開始建置可享受的人的體驗。 若要取得進一步分享的經驗設計指導方針，請前往這裡。

## <a name="chapter-4---immersion-and-teleporting"></a>第 4 章-Immersion 和 teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>目標

在供應給其他每一種混合的實境裝置的使用經驗。

### <a name="what-we-will-build"></a>我們將建置的項目

我們將更新的沈浸式檢視島上放置沈浸式耳機使用者應用程式。 HoloLens 使用者仍然可以島的鳥瞰檢視。 濆婞剢謅世界，每種裝置類型的使用者可以看到其他使用者。 比方說，沈浸式耳機使用者可以看到其他的虛擬人偶島上的其他路徑上，也高於島的巨大雲端查看 HoloLens 使用者。 如果 HoloLens 使用者查看島，沈浸式耳機使用者也會看到 資料指標的 HoloLens 使用者的視線光線。 HoloLens 使用者會看到顯示圖片，來代表每個沈浸式耳機使用者島上。

**沈浸式裝置的更新的輸入：**
* Xbox 控制器上的左動和權限動按鈕旋轉播放程式
* 保留在 Xbox 控制器上的 [Y] 按鈕可讓[傳送](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)資料指標。 如果資料指標有旋轉箭號指示器，當您放開 [Y] 按鈕時，您將會 teleported 資料指標的位置。

### <a name="steps"></a>步驟
* 加入 MixedRealityCameraParent MixedRealityTeleport
    * 在 **階層**，選取**Usland**。
    * 在  **Inspector**，讓**層級控制**。
    * 在 **階層**，選取**MixedRealityCameraParent**。
    * 在  **Inspector**，按一下**新增元件**。
    * 型別**混合實境傳送**並加以選取。

### <a name="digging-into-the-code"></a>深入探討程式碼

將行動網卡沈浸式耳機使用者，其電腦透過纜線，但我們島大於纜線過長。 為了彌補，我們需要能夠移動觀景窗獨立於使用者的動作。 請參閱[緩和頁面](comfort.md)如需有關設計混合的實境應用程式 （特別是本身的影片和 locomotion）。

為了說明此程序很適合用來定義兩個詞彙。 首先， **dolly**會是從使用者的個別移動觀景窗的物件。 子系遊戲物件**dolly**會**主攝影機**。 主攝影機會附加至使用者的大腦。

在 [專案] 面板中，瀏覽至**Assets\AppPrefabs\Support\Scripts\GameLogic** ，然後按兩下**MixedRealityTeleport.cs**。

MixedRealityTeleport 有兩項作業。 首先，它會處理使用轉場廣告旋轉的動畫。 更新函式中我們輪詢 'ButtonUp' LeftBumper 和 RightBumper 上。 GetButtonUp 只會傳回 true 按鈕已啟動，處於已關閉之後的第一個畫面上。 如果任一個按鈕引發，我們便知道使用者要旋轉。

我們旋轉時我們執行淡及淡入使用稱為 'fade 控制項' 的簡單指令碼。 我們這樣做可以防止使用者看到這可能導致 discomfort 非自然移動。 淡入和登出效果都相當簡單。 我們有黑色四組數字前面溢出**主攝影機**。 當淡出轉換從 0 到 1 的 alpha 值。 逐漸，這會使用於轉譯並遮蔽其後的任何項目四黑色像素。 當漸淡入轉換的 alpha 值設回零。

當我們計算旋轉時，請注意，我們要輪替我們**dolly**但計算繞著旋轉**主攝影機**。 這相當重要，因為較遠**主攝影機**不 0,0,0，較不精確 dolly 旋轉會變成從使用者的觀點來看。 事實上，如果您不會旋轉觀景窗位置周圍，則使用者將會在弧線周圍移動**dolly**而不是旋轉。

MixedRealityTeleport 的第二個工作是處理移動**dolly**。 這是 SetWorldPosition。 SetWorldPosition 會採用所需的世界空間位置，而使用者想要它們所佔的 percieve 的所在位置。 我們需要把我們**dolly**該位置的本機位置減去**主攝影機**、 為每個畫面格會新增該位移。

第二個指令碼會呼叫 SetWorldPosition。 讓我們看看該指令碼。 在 [專案] 面板中，瀏覽至**Assets\AppPrefabs\Support\Scripts\GameLogic** ，然後按兩下**TeleportScript.cs**。

此指令碼會比 MixedRealityTeleport 稍微複雜的。 Xbox 控制器中 [Y] 按鈕，往下保留正在檢查指令碼。 持有按鈕的游標會變成向下傳送，指令碼會從使用者的視線位置無限遠的光線。 如果該光線衝突是增加或減少的介面與向上，介面會被視為良好的介面，以傳送到，並傳送資料指標上的動畫將會啟用。 如果光線不衝突的介面，增加或減少指向資料指標的動畫將會停用。 [Y] 按鈕已釋放時之射線的導出的點是有效的位置，則指令碼會呼叫 SetWorldPosition 與光線相交的位置。

### <a name="enjoy-your-progress"></a>享受您的進度

此時您必須尋找朋友。

同樣地，使用者與 HoloLens 將主控工作階段。 其他使用者將會加入此工作階段。 應用程式會將前三個使用者加入從沈浸式耳機島上三個路徑的其中一個上。 請盡情探索這一節島。

要注意的詳細資料：
1. 您可以看到在雲端中的臉部幫助 immersed 的使用者，請參閱 HoloLens 使用者正在尋找的方向。
2. 島上的虛擬人偶有 necks 旋轉。 它們不會依照使用者正在做什麼是真正的領域 （我們不需要該資訊），但它對所做的好用的體驗。
3. 如果 HoloLens 使用者會看到島，immersed 的使用者可以看到其資料指標。
4. 代表 HoloLens 使用者的雲端轉換陰影。

## <a name="chapter-5---finale"></a>第 5 章-二

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>目標

建立兩個裝置類型之間的共同作業的互動式體驗。

### <a name="what-we-will-build"></a>我們將建置的項目

基礎第 4 章沈浸式的耳機與使用者靠近謎題島上時，HoloLens 使用者會收到與拼圖線索的工具提示。 一旦所有的沈浸式耳機使用者取得超過其謎題，然後在 「 準備板 」 到 rocket 房間內，將會啟動 rocket。

### <a name="steps"></a>步驟
* 在 **階層**，選取**Usland**。
* 在  **Inspector**，請在**層級控制**，檢查**啟用共同作業**。

### <a name="digging-into-the-code"></a>深入探討程式碼

現在讓我們看看 LevelControl.cs。 此指令碼是遊戲邏輯的核心，並維護遊戲的狀態。 由於這是多人遊戲使用 UNET 我們需要了解資料的流程，也至少夠修改本教學課程。 UNET 的更完整概觀，請參閱 Unity 文件。

在 [專案] 面板中，瀏覽至**Assets\AppPrefabs\Support\Scripts\GameLogic** ，然後按兩下**LevelControl.cs**。

讓我們了解如何沈浸式耳機表示它們是火箭上市作準備。 Rocket 啟動整備通訊的其中三個布林設定清單中的對應至三個路徑島上的布林。 將使用者指派給路徑位於 rocket 房間內的棕色板上方時，設定路徑的 bool。 好，現在來詳細資料。

我們將開始的 update （） 函式。 您會發現沒有 'cheat' 函式。 我們使用這在開發過程中將測試 rocket 啟動和重設序列。 它將無法在多使用者體驗中運作。 希望您內化下列資訊的時間就能夠立即確認其運作。 我們檢查一下，請參閱我們應該使用密技之後，我們會檢查以查看 是否沉浸本機的播放程式。 我們想要專注於我們如何找到我們在目標。 在 if （沉浸） 檢查，沒有呼叫背後隱藏的 CheckGoal **EnableCollaboration** bool。 這會對應至您在完成本章節的步驟時，核取此核取方塊。 EnableCollaboration 內，我們會看到 CheckGoal() 呼叫。

CheckGoal 會執行一些數學運算來查看我們是否增加或減少板上的位置。 當我們，我們 Debug.Log"Arrived 在目標 」，接著再呼叫 'SendAtGoalMessage()'。 在 SendAtGoalMessage，我們會呼叫 playerController.SendAtGoal。 若要節省一些時間，以下的程式碼：

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

請注意 SendAtGoalMessage 呼叫 CmdSendAtGoal，哪一個呼叫 levelState.SetGoalIndex，也就是在 LevelControl.cs。 乍看之下可能有點奇怪。 為什麼不只是呼叫 SetGoalIndex 而不是這奇怪經過 「 玩家 」 控制器？ 原因是我們符合 UNET 使用，讓資料保持同步的資料模型。若要避免作弊和過度置換，UNET 會需要每個物件都具有變更的同步處理的變數的權限的使用者。 此外，只有主機 （啟動工作階段的使用者） 可以直接變更資料。 不是主應用程式，但具有權限，使用者需要 「 command 」 將會變更變數的主機。 根據預設主機會高於繁衍來代表使用者的物件除外的所有物件的授權單位。 在本例中此物件會具有 playercontroller 指令碼。 沒有方法可要求之物件的授權單位，然後再進行變更，但我們選擇利用 「 玩家 」 控制器具有本身的授權單位和路由命令透過 「 玩家 」 控制器的事實。

換言之，當我們發現自己在我們的目標時，播放程式需要向主應用程式，而主應用程式會告訴其他人。

在 LevelControl.cs SetGoalIndex 看。 這裡我們 synclist (AtGoal) 中設定的值。 請記住我們是主應用程式的內容中，當我們執行這項操作。 類似的命令，RPC 是主應用程式可以發出，使所有用戶端執行一些程式碼。 這裡我們呼叫 'RpcCheckAllGoals'。 每個用戶端會個別檢查以查看所有的三個 AtGoals 所設定，和如果是這樣，啟動 rocket。

### <a name="enjoy-your-progress"></a>享受您的進度

在上一章中建置，我們將開始為之前的工作階段。 這次在沉浸式耳機 get 扇 「 小門 」 在其路徑中，以使用者為工具提示會顯示只有 HoloLens 的使用者可以看到。 HoloLens 使用者負責傳達此線索沈浸式耳機中的使用者。 Rocket 會啟動空間之後每個虛擬人偶有分層式火山內其對應的棕色板上。 場景會重設在 60 秒之後，因此您可以再次執行。

## <a name="see-also"></a>另請參閱
* [MR 輸入 213:動作控制站](mixed-reality-213.md)
