---
title: MR 基本概念 100-開始使用 Unity
description: 瞭解如何建立您的第一個基本混合現實 "hello world" 應用程式。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現實，Windows Mixed Reality，HoloLens，沉浸，vr，mr，開始使用，全息影像，學院，教學課程
ms.openlocfilehash: 0600383b3cca3f580f014597217afc6ae78836dd
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375595"
---
>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>MR 基本概念100：開始使用 Unity

本教學課程將逐步引導您建立以 Unity 建立的基本混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 基本概念100：開始使用 Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>必要條件

* [已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。

## <a name="chapter-1---create-a-new-project"></a>第1章-建立新專案

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

若要使用 Unity 來建立應用程式，您必須先建立專案。 此專案會組織成幾個資料夾，其中最重要的是您的資產資料夾。 這是保存您從數位內容建立工具（例如 Maya、最大影院4D 或 Photoshop）匯入之所有資產的資料夾，您使用 Visual Studio 或慣用的程式碼編輯器建立的所有程式碼，以及 Unity 在撰寫場景時所建立的任何內容檔案數目、動畫，以及編輯器中的其他 Unity 資產類型。

若要建立和部署 UWP 應用程式，Unity 可以將專案匯出為 Visual Studio 方案，其中包含所有必要的資產和程式碼檔案。

1. 啟動 Unity
2. 選取 [**新增**]
3. 輸入專案名稱（例如 "MixedRealityIntroduction"）
4. 輸入儲存專案的位置
5. 確定已選取**3d**切換
6. 選取 [**建立專案**]

恭喜，您可以立即開始進行混合現實的自訂。

## <a name="chapter-2---setup-the-camera"></a>第2章-設定相機

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity 主要攝影機會處理 head 追蹤和 stereoscopic 轉譯。 主要相機有幾個變更可用於混合現實。

1. 選取檔案 > 新場景

首先，如果您認為使用者的開始位置是（**X**：0， **Y**：0， **Z**：0），則可以更輕鬆地配置應用程式。 由於主要攝影機是追蹤使用者頭部的移動，因此可以藉由設定主要攝影機的開始位置來設定使用者的開始位置。

1. **在 [階層**] 面板中選取**主要相機**
2. 在 [偵測**器**] 面板中，尋找 [**轉換**] 元件，並將**位置**從（**x**：0， **y**：1， **z**：-10）變更為（**x**：0， **y**：0， **Z**：0）

第二，預設的相機背景需要一些思考。

若是**HoloLens 應用程式**，真實世界應該會出現在相機呈現的所有內容後方，而不是 Skybox 材質。

1. 在 [階層] 面板中仍然選取**主要相機**後，**在 [偵測** **器**] 面板中尋找**相機**元件，並將 [**清除旗標**] 下拉式清單從**Skybox**變更為**純色**。
2. 選取**背景**色彩選擇器，並將**RGBA**值變更為（0，0，0，0）

**對於以沉浸式耳機為目標的混合現實應用程式**，我們可以使用 Unity 提供的預設 Skybox 材質。

1. **在 [階層] 面板中**，仍然選取**主要相機**，請在 [偵測**器**] 面板中尋找**相機**元件，並將 [**清除旗標**] 下拉式清單保留為**Skybox**。

第三，讓我們考慮 Unity 中附近的裁剪平面，防止物件在使用者接近物件或物件接近使用者的情況下，呈現太接近使用者的眼睛。

若是**hololens 應用程式**，接近的裁剪平面可以設定為[hololens 建議](camera-in-unity.md#clip-planes)的0.85 計量。

1. **在 [階層] 面板中**仍然選取**主要相機**時，請在 [偵測**器**] 面板中尋找**相機**元件，並將 [**接近剪切平面**] 欄位從預設**0.3**變更為 [HoloLens 建議**0.85**]。

**對於以沉浸式耳機為目標的混合現實應用程式**，我們可以使用 Unity 提供的預設設定。

1. **在 [階層] 面板中**仍然選取**主要相機**時，請在 [偵測**器**] 面板中尋找**相機**元件，並將 [**近端剪切平面**] 欄位保留為預設值**0.3**。

最後，讓我們來儲存我們目前的進度。 若要儲存場景變更，請選取 檔案 **> 另存場景**，將場景命名為**Main**，然後選取 **儲存**。

## <a name="chapter-3---setup-the-project-settings"></a>第3章-設定專案設定

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

在本章中，我們將設定一些 Unity 專案設定，以協助我們以 Windows 全像開發 SDK 為目標。 我們也會為應用程式設定一些品質設定。 最後，我們會確保組建目標設定為 Windows Store。

### <a name="unity-performance-and-quality-settings"></a>Unity 效能和品質設定

**HoloLens 的 Unity 品質設定**

![HoloLens 的 Unity 品質設定](images/qualitysettings.png)

因為在 HoloLens 上維持高畫面播放速率相當重要，所以我們想要調整品質設定以取得最快的效能。 如需更詳細的效能資訊，請[查看 Unity 的效能建議](performance-recommendations-for-unity.md)。

1. 選取 [**編輯] > 專案設定 > 品質**
2. 選取 [ **Windows Store** ] 標誌底下的**下拉式清單**，然後選取 [**非常低**]。 當 [Windows Store] 資料行中的方塊和**非常低**的資料列都是綠色時，您會知道設定已正確套用。

**針對以 pixels occluded 為目標的混合現實應用程式**，您可以將品質設定保留為預設值。

### <a name="target-windows-10-sdk"></a>以 Windows 10 SDK 為目標

**以 Windows 全像的 SDK 為目標**

![以 Windows 全像的 SDK 為目標](images/xrsettings.png)

我們需要讓 Unity 知道，我們嘗試匯出的應用程式應該建立[沉浸式視圖](app-views.md)，而不是2d 視圖。 我們的作法是在以 Windows 10 SDK 為目標的 Unity 上啟用虛擬實境支援。

1. 移至 **編輯 > 專案設定 > Player**。
2. 在 [玩家設定] 的 [偵測**器] 面板**中，選取 [ **Windows Store** ] 圖示。
3. 展開 [ **XR 設定**] 群組。
4. **在轉譯區段中**，勾選 [**支援虛擬實境**] 核取方塊，以新增**虛擬實境 sdk**清單。
5. 確認清單中出現**Windows Mixed Reality** 。 如果沒有，請選取清單底部的 [ **+** ] 按鈕，然後選擇 [ **Windows Mixed Reality**]。

>[!NOTE]
>如果您看不到 [ **Windows store** ] 圖示，請再次檢查以確定您在安裝之前已選取 [windows Store .Net 腳本後端]。 如果不是，您可能需要使用正確的 Windows 安裝來重新安裝 Unity。

**確認 .NET 設定**

![確認 .NET 設定](images/configoptions-375px.png)

1. 移至 **編輯 > 專案設定 > 播放** （您在上一個步驟中可能還是會這麼做）。
2. 在 [玩家設定] 的 [偵測**器] 面板**中，選取 [ **Windows Store** ] 圖示。
3. 在 [**其他設定**] 區段中，確認 [**腳本後端**] 已設定為 [ **.net** ]

取得套用所有專案設定的絕佳作業。 接下來，讓我們新增全息影像！

## <a name="chapter-4---create-a-cube"></a>第4章-建立 cube

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

在 Unity 專案中建立 cube，就像在 Unity 中建立任何其他物件一樣。 將 cube 放在使用者的前方很容易，因為 Unity 的座標系統會對應到真實世界-其中 Unity 中的一個計量是真實世界中的一個計量。

1. **在 [階層] 面板的**左上角，選取 [**建立**] 下拉式清單，然後選擇 [ **3d 物件 > Cube**]。
2. 在 [階層 **] 面板中**選取新建立的**Cube**
3. 在偵測**器**中，尋找 [**轉換**] 元件，並將 [**位置**] 變更為（**X**：0， **Y**：0， **Z**：2）。 *這會將 cube 2 計量置於使用者開始位置的前方。*
4. 在 [**轉換**] 元件中，將 [**旋轉**] 變更為（**x**：45， **Y**：45， **Z**：45），並將 [**調整**為] （**x**：0.25， **Y**：0.25， **z**：0.25）。 *這會將 cube 調整為0.25 計量。*
5. 若要儲存場景變更，請選取 檔案 **> 儲存場景**。

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>第5章-從 Unity 編輯器進行裝置驗證

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

既然我們已經建立 cube，就可以開始快速檢查裝置。 您可以直接從 Unity 編輯器中執行此動作。

### <a name="initial-setup"></a>初始設定

1. 在開發電腦的 Unity 中，開啟 [檔案] **> [組建設定**] 視窗。
2. 將**平臺**變更為**通用 Windows 平臺**，然後按一下 [**切換平臺**]

### <a name="for-hololens-use-unity-remoting"></a>若是 HoloLens，請使用 Unity Remoting

1. 在您的 HoloLens 上，安裝並執行可從 Windows 市集中取得的全像攝影[遠端播放](holographic-remoting-player.md)程式。 在裝置上啟動應用程式，它會進入等候狀態，並顯示裝置的 IP 位址。 記下 IP。
2. 開啟**Window > XR >** 全像的模擬。
3. 將**模擬模式**從 [**無**] 變更為 [**遠端] 至 [裝置**]。
4. 在 [**遠端電腦**] 中，輸入您先前記下的 HOLOLENS 的 IP 位址。
5. 按一下 [連接]。
6. 確定 [**連接狀態**] 變更為 [綠色**已連接**]。
7. 現在您可以按一下 Unity 編輯器中的 [**播放**]。

您現在將能夠在 [裝置] 和編輯器中看到 cube。 就像在編輯器中執行應用程式一樣，您可以暫停、檢查物件和進行 debug，因為這基本上是發生的情況，但是會在主機電腦與裝置之間的網路上來回傳輸影片、音訊和裝置輸入。

### <a name="for-other-mixed-reality-supported-headsets"></a>適用于其他混合現實支援的耳機

1. 使用 USB 纜線和 HDMI 或顯示器埠纜線，將耳機連接到您的開發電腦。
2. 啟動**混合現實入口網站**，並確定您已完成第一次執行體驗。
3. 從 Unity，您現在可以按下 [播放] 按鈕。

您現在可以在混合現實頭戴式耳機和編輯器中看到 cube 呈現。

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>第6章-從 Visual Studio 建立及部署至裝置

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

我們現在已準備好編譯專案，以 Visual Studio 並部署至目標裝置。

### <a name="export-to-the-visual-studio-solution"></a>匯出至 Visual Studio 解決方案

1.  開啟 檔案 **> 組建設定** 視窗。
2.  按一下 [新增] [**開啟場景**] 以加入場景。
3.  將**平臺**變更為**通用 Windows 平臺**，然後按一下 [**切換平臺**]。
4.  在**Windows Store**設定中， **SDK**為**通用 10**。
5.  針對 [目標裝置]，保留 [**任何裝置**以進行 pixels occluded] 或 [切換至**HoloLens**]。
6.  **UWP 組建類型**應該是**D3D**。
7.  **UWP SDK**可以保持在**最新的安裝**位置。
8.  檢查 [調試] 底下的**Unity C#專案**。
9.  按一下 [建置]。
10. 在 [檔案瀏覽器] 中，按一下 [**新增資料夾**]，並將資料夾命名為「**應用程式**」。
11. 選取**應用程式**資料夾後，按一下 [**選取資料夾**] 按鈕。
12. Unity 完成建立時，將會出現 Windows 檔案瀏覽器視窗。
13. 在檔案瀏覽器中開啟**應用程式**資料夾。
14. 開啟產生的 Visual Studio 方案（在此範例中為 MixedRealityIntroduction）

### <a name="compile-the-visual-studio-solution"></a>編譯 Visual Studio 解決方案

最後，我們將編譯匯出的 Visual Studio 解決方案、部署它，然後在裝置上試試看。

1. 使用 Visual Studio 中的頂端工具列，將目標從 [**調試**] 變更為 [**發行**]，將 [從**ARM** ] 變更為**X86**。

部署至裝置與模擬器的指示不同。 遵循符合您設定的指示。

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>透過 Wi-fi 部署到混合現實裝置

1. 按一下 [**本機電腦**] 按鈕旁的箭號，然後將部署目標變更為 [**遠端電腦**]。
2. 輸入您 mixed reality 裝置的 IP 位址，並將其他裝置的 HoloLens 和**Windows**的**驗證模式**變更為通用（未加密的通訊協定）。
3. 按一下 [ **Debug > 啟動但不進行調試**]。

若是**HoloLens**，如果這是您第一次部署至您的裝置，您將需要[使用 Visual Studio](using-visual-studio.md)配對。

### <a name="deploy-to-mixed-reality-device-over-usb"></a>透過 USB 部署到混合現實裝置

請確定您的裝置已透過 USB 纜線插入。

1. 若是**HoloLens**，請按一下 [**本機電腦**] 按鈕旁的箭號，然後將部署目標變更為 [**裝置**]。
2. **針對連接到您電腦的 pixels occluded 裝置**，請將設定保留在 [本機電腦]。 請確定您有執行中的**混合現實入口網站**。
3. 按一下 [ **Debug > 啟動但不進行調試**]。

### <a name="deploy-to-emulator"></a>部署至模擬器

1. 按一下 [**裝置**] 按鈕旁邊的箭號，然後從下拉式選選取 [ **HoloLens 模擬器**]。
2. 按一下 [ **Debug > 啟動但不進行調試**]。

### <a name="try-out-your-app"></a>試用您的應用程式

現在您已部署您的應用程式，請嘗試在 cube 前後移動，並觀察它是否留在您的前方。

## <a name="see-also"></a>另請參閱

* [Unity 開發概觀](unity-development-overview.md)
* [使用 Unity 和 Visual Studio 的最佳作法](best-practices-for-working-with-unity-and-visual-studio.md)
* [MR 基本101](holograms-101.md)
* [MR 基本概念101E](holograms-101e.md)
