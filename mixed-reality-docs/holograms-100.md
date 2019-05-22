---
title: MR 基本概念 100-開始使用 Unity
description: 了解如何建立第一個基本的混合的實境"hello world"應用程式。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合實境，Windows Mixed Reality、 HoloLens、 沉浸式 vr mr、 開始著手，全像圖、 academy、 教學課程
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993615"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>MR 基本概念 100:開始使用 Unity

本教學課程將逐步引導您建立使用 Unity 建置基本的混合的實境應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 基本概念 100:開始使用 Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>先決條件

* Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。

## <a name="chapter-1---create-a-new-project"></a>第 1-建立新的專案

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

若要建置使用 Unity 應用程式，必須先建立專案。 此專案會組織成幾個資料夾，其中最重要的是您資產的資料夾。 這是保存您從數位內容創作工具，例如 Maya、 最大杜比劇院效果 4d 或您使用 Visual Studio 或您慣用的程式碼編輯器，建立的所有程式碼的 Photoshop 匯入的所有資產的資料夾和任意數目的內容檔案，Unity 會建立為您撰寫場景動畫和其他編輯器中的 Unity 資產類型。

若要建置及部署 UWP 應用程式，Unity 可以匯出為 Visual Studio 方案將會包含所有必要的資產和程式碼檔案的專案。

1. 啟動 Unity
2. 選取**新**
3. 輸入專案名稱 （例如：「 MixedRealityIntroduction")
4. 輸入要儲存專案的位置
5. 請確定**3D**切換已選取
6. 選取**建立專案**

恭喜，您會以您的混合的實境自訂立即開始的所有安裝程式。

## <a name="chapter-2---setup-the-camera"></a>第 2 章-安裝相機

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity Main Camera 處理追蹤的前端和立體視覺呈現。 有一些變更，可讓 Main Camera 與混合實境中使用它。
1. 選取 檔案 > 新的場景

首先，能夠更輕鬆地配置您的應用程式，如果您能想像為使用者的開始位置 (**X**:0， **Y**:0， **Z**:0). 由於 Main Camera 正在追蹤使用者的標頭的移動，就可以設定使用者的開始位置設定 Main Camera 的開始位置。
1. 選取  **Main Camera**中**階層**面板
2. 在 [ **Inspector** ] 面板中，尋找**轉換**元件，並變更**位置**從 (**X**:0， **Y**:1、&lt **Z**:-10) 到 (**X**:0， **Y**:0， **Z**:0)

第二的預設相機背景需要加以考量。

**HoloLens 的應用程式**，現實世界裡應該會出現背後的所有項目觀景窗會呈現不天空盒材質。
1. 與**Main Camera**中選取，您仍然**階層** 面板中，尋找**相機**元件**Inspector**面板，並變更**清除旗標**下拉式清單中，從**天空盒**來**單色**。
2. 選取 **背景**色彩選擇器和變更**RGBA**值 （0，0，0，0）

**混合的實境應用程式目標為沈浸式耳機**，我們可以使用 Unity 所提供的預設天空盒材質。
1. 與**Main Camera**中選取，您仍然**階層** 面板中，尋找**相機**元件**Inspector**面板，並保留**清除旗標**下拉式清單來**天空盒**。

第三，讓我們考慮接近裁剪平面 Unity 中的，並防止物件呈現太靠近使用者的眼睛使用者接近物件或物件方法的使用者。

**HoloLens 的應用程式**，可以將設定為接近裁剪平面[HoloLens 建議](camera-in-unity.md#clip-planes)0.85 的計量。
1. 與**Main Camera**中選取，您仍然**階層**] 面板中，尋找**相機**元件**Inspector**面板，並變更**接近裁剪平面**欄位從 [預設**0.3**來建議 HoloLens **0.85**。

**混合的實境應用程式目標為沈浸式耳機**，我們可以使用 Unity 所提供的預設設定。
1. 與**Main Camera**中選取，您仍然**階層** 面板中，尋找**相機**元件**Inspector**面板，並保留**接近裁剪平面**欄位設為預設值**0.3**。

最後，讓我們儲存我們進行到目前為止。 若要儲存的場景變更，請選取**檔案 > 存場景**，場景命名為**Main**，然後選取**儲存**。

## <a name="chapter-3---setup-the-project-settings"></a>第 3 章-安裝程式的專案設定

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

在本章中，我們會設定一些幫助我們的 Unity 專案設定目標 Windows 全像攝影版 SDK 進行開發。 我們也將我們的應用程式中設定某些品質設定。 最後，我們會確保我們建置目標會設定為 Windows 市集。

### <a name="unity-performance-and-quality-settings"></a>Unity 的效能和品質的設定

**HoloLens 的 unity 品質設定**

![HoloLens 的 unity 品質設定](images/qualitysettings.png) 

維護高的畫面播放速率 HoloLens 上是很重要，因為我們想要微調的最快效能的品質設定。 如需詳細效能資訊，請[Unity 的效能建議](performance-recommendations-for-unity.md)。
1. 選取**編輯 > 專案設定 > 品質**
2. 選取 **下拉式清單**下方**Windows 市集**標誌，然後選取**非常低**。 您知道設定正確時套用的 Windows 市集的資料行中的方塊並**非常低**資料列是綠色。

**混合的實境應用程式，以阻擋顯示目標**，您可以將品質設定保留為其預設值。

### <a name="target-windows-10-sdk"></a>目標 Windows 10 SDK

**目標 Windows 全像攝影版 SDK**

![目標 Windows 全像攝影版 SDK](images/xrsettings.png) 

我們需要讓知道我們嘗試匯出的應用程式應該建立 Unity[沈浸式檢視](app-views.md)而不是 2D 檢視。 我們可以啟用在 Unity 上的虛擬實境支援 Windows 10 SDK 為目標。
1. 移至**編輯 > 專案設定 > Player**。
2. 在 [**偵測器] 面板**播放程式設定中，選取**Windows 市集**圖示。
3. 依序展開**XR 設定**群組。
4. 在 **轉譯**區段中，按一下**虛擬實境支援**核取方塊以加入新**虛擬實境 Sdk**清單。
5. 確認**Windows Mixed Reality**出現在清單中。 如果沒有，請選取 **+** 按鈕在清單底部，然後選擇**Windows Mixed Reality**。

>[!NOTE]
>如果您看不見**Windows 市集**圖示，並再次檢查以確定您選取 Windows 市集.NET 指令碼後端之前安裝。 如果沒有，您可能需要重新安裝正確的 Windows 安裝 Unity。

**確認.NET 組態**

![確認.NET 組態](images/configoptions-375px.png)

1. 移至**編輯 > 專案設定 > Player** （您可能仍有這在上一個步驟）。
2. 在 [**偵測器] 面板**播放程式設定中，選取**Windows 市集**圖示。
3. 在 **其他設定**組態區段中，請確定**指令碼的後端**設定為 **.NET**

取得套用的所有專案設定得好極了。 接下來，讓我們新增雷射 ！

## <a name="chapter-4---create-a-cube"></a>第 4 層建立 cube

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

建立 Unity 專案中的 cube 就如同在 Unity 中建立任何其他物件。 將放在使用者之前 cube 很容易，因為 Unity 的座標系統對應至真實世界-其中 Unity 中的一個計量是真實的世界中大約一個計量。
1. 中的左上角**階層**面板中，選取**建立**下拉式清單中，然後選擇  **3D 物件 > Cube**。
2. 選取 新建**Cube**中**階層**面板
3. 在  **Inspector**尋找**轉換**元件，並變更**位置**來 (**X**:0， **Y**:0， **Z**:2). *這會將 cube 2 公尺之前使用者的起始位置。*
4. 在 **轉換**元件，變更**旋轉**到 (**X**:45 **Y**:45 **Z**:45），並變更**擴展**到 (**X**:0.25， **Y**:0.25， **Z**:0.25). *這會調整至 0.25 計量 cube。*
5. 若要儲存的場景變更，請選取**檔案 > 儲存場景**。

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>第 5-確認裝置上，從 Unity 編輯器

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

既然我們已建立 cube，就可以進行裝置中的快速檢查。 您可以直接從 Unity 編輯器中。

### <a name="initial-setup"></a>初始設定
1. 在開發電腦，在 Unity 中，開啟**檔案 > 組建設定**視窗。
2. 變更**平台**要**通用 Windows 平台**按一下**切換平台**

### <a name="for-hololens-use-unity-remoting"></a>HoloLens 使用 Unity 遠端處理
1. 在您的 HoloLens 上安裝，並執行[全像攝影版的遠端播放程式](holographic-remoting-player.md)，可從 Windows 市集。 啟動裝置上的應用程式，它會進入等候狀態，並顯示裝置的 IP 位址。 請記下 IP。
2. 開啟**視窗中 > XR > 全像攝影版的模擬**。
3. 變更**模擬模式**從**無**來**遠端裝置**。
4. 在 **遠端機器**，輸入您稍早所述的 HoloLens 的 IP 位址。
5. 按一下 **[連接]**。
6. 請確定**連線狀態**變更為綠色**Connected**。
7. 您現在可以按一下現在**播放**在 Unity 編輯器中。

您現在可以看到 cube 中的裝置，並在編輯器中。 您可以暫停、 檢查物件，及偵錯就像您會在編輯器中，執行應用程式，因為這基本上是發生的事情，但與視訊、 音訊及裝置輸入在主機電腦和裝置之間的網路來回傳輸。

### <a name="for-other-mixed-reality-supported-headsets"></a>其他混合實境支援耳機

1. 連接到開發電腦使用 USB 纜線和 HDMI 的耳機或顯示的連接埠的纜線。
2. 啟動**混合實境入口網站**，並確定您已完成初次執行的體驗。
3. 從 Unity，您現在可以按 [播放] 按鈕。

您現在可以看到 cube 呈現在混合的實境耳機，並在編輯器中。

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>章節 6-建置，並從 Visual Studio 部署至裝置

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

我們現在已準備好我們的專案，Visual studio 編譯及部署到我們的目標裝置。

### <a name="export-to-the-visual-studio-solution"></a>匯出至 Visual Studio 方案
1.  開啟**檔案 > 組建設定**視窗。
2.  按一下 **加入開啟的場景**加入場景。
3.  變更**平台**要**通用 Windows 平台**然後按一下**切換平台**。
4.  在  **Windows 市集**設定可確保， **SDK**會**通用 10**。
5.  針對目標裝置，留給**任何裝置**occluded 顯示或切換至**HoloLens**。
6.  **UWP 建置型別**應該**D3D**。
7.  **UWP SDK**可能會停留在**最新安裝**。
8.  請檢查**UnityC#專案**偵錯。
9.  按一下 [建置] 。
10. 在 [檔案總管] 中，按一下**新的資料夾**並將資料夾命名 **「 應用程式 」**。
11. 具有**應用程式**按一下 [選取資料夾**選取資料夾**] 按鈕。
12. 當完成 Unity 建置，就會顯示 Windows 檔案總管 視窗。
13. 開啟**應用程式**檔案總管 中的資料夾。
14. 開啟產生的 Visual Studio 方案 (在此範例中的 MixedRealityIntroduction.sln)

### <a name="compile-the-visual-studio-solution"></a>編譯的 Visual Studio 方案

最後，我們將會編譯匯出的 Visual Studio 方案，加以部署，並試用看看在裝置上。
1. 在 Visual Studio 中，使用頂端的工具列來變更目標從**偵錯**要**版本**進出**ARM**來**X86**。

指示不同部署至模擬器與裝置。 請遵循符合您的安裝程式的指示。

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>將部署至混合的實境裝置透過 Wi-fi
1. 按一下箭號旁**本機電腦**按鈕，並變更部署目標，以便**遠端機器**。
2. 輸入您的混合的實境裝置的 IP 位址，然後變更**驗證模式**為通用 （未加密的通訊協定） 的 HoloLens 和**Windows**針對其他裝置。
3. 按一下 **偵錯 > 啟動但不偵錯**。

**針對 HoloLens**，如果這是您第一次部署到您的裝置，您需要配對[使用 Visual Studio](using-visual-studio.md)。

### <a name="deploy-to-mixed-reality-device-over-usb"></a>透過 USB 將部署至混合的實境裝置

請確定您的裝置透過 USB 纜線已插入。
1. **HoloLens**，按一下箭號旁**本機電腦**按鈕，並變更部署目標，以便**裝置**。
2. **針對連接到您的電腦的阻擋裝置**，保留到本機電腦的設定。 請確定您已**混合實境入口網站**執行。
3. 按一下 **偵錯 > 啟動但不偵錯**。

### <a name="deploy-to-emulator"></a>部署至模擬器
1. 按一下箭號旁**裝置** 按鈕，並從下拉式清單中，選取**HoloLens 模擬器**。
2. 按一下 **偵錯 > 啟動但不偵錯**。

### <a name="try-out-your-app"></a>試用您的應用程式

現在，部署您的應用程式時，嘗試移動所有 cube，並觀察它會保持在您面前的世界。

## <a name="see-also"></a>另請參閱
* [Unity 開發概觀](unity-development-overview.md)
* [使用 Unity 和 Visual Studio 的最佳作法](best-practices-for-working-with-unity-and-visual-studio.md)
* [101 MR 基本知識](holograms-101.md)
* [MR 基本概念 101E](holograms-101e.md)
