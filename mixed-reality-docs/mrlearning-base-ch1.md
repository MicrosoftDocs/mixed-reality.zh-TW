---
title: 入門教學課程 - 2。 初始化您的專案和第一個應用程式
description: 完成此課程以學習在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: d3392df9bfad5938d71d3a01999be51834a98a5d
ms.sourcegitcommit: 87aca9c2b73b0e83cb70a46443dcdb08c3621005
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2020
ms.locfileid: "77373452"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化您的專案和第一個應用程式

## <a name="overview"></a>概觀

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
在此第一篇教學課程中，您將了解<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合實境工具組 (MRTK)</a>提供的一些功能，然後啟動第一個適用於 HoloLens 2 的應用程式，並將其部署到裝置。

## <a name="objectives"></a>目標

* 設定 Unity 以用於 HoloLens 開發
* 匯入資產並設定場景
* 空間對應網格、手部網格和畫面播放速率計數器的視覺效果

## <a name="prerequisites"></a>必要條件

* 已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 基本的 C# 程式設計能力
* 已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組

> [!IMPORTANT]
> 本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。 這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。

## <a name="create-new-unity-project"></a>建立新的 Unity 專案

啟動 **Unity Hub**，選取 [專案]  索引標籤，然後按一下 [新增]  按鈕旁的**向下箭號**：

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

選取上述[必要條件](#prerequisites)一節中指定的 Unity 版本：

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

在 [建立新專案] 視窗中：

* 確定 [範本]  設定為 [3D] 
* 輸入適當的 [專案名稱]  ，例如 MRTK Tutorials 
* 選擇適當的 [位置]  來儲存您的專案，例如 D:\MixedRealityLearning 
* 按一下 [建立]  按鈕，以建立並啟動新的 Unity 專案

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> 在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。 Unity 受到這些限制的影響，如果有任何檔案路徑的長度超過 255 個字元，可能無法編譯。 因此，強烈建議您盡可能將 Unity 專案儲存在接近磁碟機根目錄的位置。

等候 Unity 建立專案：

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>設定適用於 Windows Mixed Reality 的 Unity 專案

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

在本節中，您將切換組建平台、啟用虛擬實境，並啟用空間感知功能。

### <a name="1-switch-build-platform"></a>1.切換組建平台

在 Unity 功能表中，選取 [檔案]   >  [組建設定...]  來開啟 [組建設定] 視窗：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

在 [組建設定] 視窗中，選取 [通用 Windows 平台]  ，然後按一下 [切換平台]  按鈕：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

等候 Unity 完成平台的切換：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

當 Unity 完成平台切換之後，按一下紅色 **x** 圖示以關閉 [組建設定] 視窗：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a>2.啟用虛擬實境

> [!NOTE]
> 「啟用虛擬實境」也適用於混合實境和擴增實境頭戴式裝置，因為都是啟用立體視覺，也就是為每隻眼睛轉譯不同影像。

在 Unity 功能表中，選取 [編輯]   >  [專案設定...]  來開啟 [專案設定] 視窗：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

在 [專案設定] 視窗中，選取 [播放器]   >  [XR 設定]  以展開 [XR 設定]：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

在 [XR 設定] 中，選取 [支援的虛擬實境]  核取方塊以啟用虛擬實境，按一下 **+** 圖示，然後選取 [Windows Mixed Reality]  以新增 Windows Mixed Reality SDK：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

等候 Unity 完成 SDK 的新增：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

當 Unity 完成新增 SDK 之後，將 XR 設定最佳化，如下所示：

* 將 Windows Mixed Reality 的 [深度格式]  設為 [16 位元深度] 
* 勾選 Windows Mixed Reality 的 [啟用深度共用]  核取方塊
* 將 [立體聲轉譯模式\*]  設為 [單通道執行個體化] 

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> 若要深入瞭解如何將用於 Windows Mixed Reality 的 Unity 最佳化，您可以參閱 [Unity 的建議設定](recommended-settings-for-unity.md)文件。

### <a name="3-enable-spatial-perception"></a>3.啟用空間感知

> [!NOTE]
> 空間感知可讓 Windows Mixed Reality 裝置上的空間對應網格視覺化。

在 [專案設定] 視窗中，選取 [播放器]   >  [發佈設定]  以展開發佈設定：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

在 [發佈設定] 中，向下捲動至 [功能]  區段，然後勾選 [SpatialPerception]  核取方塊：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

關閉 [專案設定] 視窗。

## <a name="import-textmesh-pro-essential-resources"></a>匯入 TextMesh Pro 基本資源

> [!NOTE]
> 我們正在匯入此套件，因為混合實境工具組的 UI 元素會需要。

在 Unity 功能表中，選取 [視窗]   >  [TextMeshPro]   >  [匯入 TMP 基本資源]  ：

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

在 [匯入 Unity 套件] 視窗中，按一下 [全部]  按鈕以確保選取所有資產，然後按一下 [匯入]  按鈕來匯入資產：

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a>匯入混合實境工具組

下載 Unity 自訂套件：

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.2.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage)

在 Unity 功能表中，選取 [資產]   >  [匯入套件]   >  [自訂套件 ...]  以開啟 [匯入套件...] 視窗：

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

在 [匯入套件...] 視窗中，選取您下載的 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage**，然後按一下 [開啟]  按鈕：

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

在 [匯入 Unity 套件] 視窗中，按一下 [全部]  按鈕以確保選取所有資產，然後按一下 [匯入]  按鈕來匯入資產：

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a>設定用於混合實境工具組的 Unity 專案

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

匯入套件之後，應該會出現 [MRTK 專案設定程式] 視窗。 如果沒有，請在 Unity 功能表中選取 [混合現實工具組]   >  [公用程式]   >  [設定 Unity 專案]  加以開啟。

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

在 [MRTK 專案設定程式] 視窗中，展開 [修改設定]  區段，取消勾選<u></u> [啟用適用於 Unity 的 MSBuild]  核取方塊，確定已勾選所有其他選項，然後按一下 [套用]  按鈕來套用設定：

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> 適用於 Unity 的 MSBuild 可能不支援您將使用的所有 SDK，且在啟用之後，可能會很難停用。 因此，強烈建議您不要啟用適用於 Unity 的 MSBuild。

## <a name="configure-the-mixed-reality-toolkit"></a>設定混合實境工具組
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

在 Unity 功能表中，選取 [混合實境工具組]   >  [新增至場景並設定...]  來將混合實境工具組新增至目前的場景：

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

在 [階層] 視窗中選取 MixedRealityToolkit 物件之後，在 [偵測器] 視窗中，將 [混合實境工具組] 設定中的設定檔變更為 **DefaultHoloLens2ConfigurationProfile**：

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

在 Unity 功能表中，選取 [檔案]   >  [另存新檔 ...]  以開啟 [儲存場景] 視窗：

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

在 [儲存場景] 視窗中，瀏覽至專案的 **Scenes** 資料夾，為您的場景取一個適當的名稱，例如 Getting Started  ，然後按一下 [儲存]  按鈕儲存場景：

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a>對您的裝置建置應用程式

### <a name="1-build-the-unity-project"></a>1.組建 Unity 專案

在 Unity 功能表中，選取 [檔案]   >  [組建設定...]  來開啟 [組建設定] 視窗。

在 [組建設定] 視窗中，按一下 [新增開啟的場景]  按鈕，將您目前的場景新增至 [組建中的場景]  清單，然後按一下 [組建]  按鈕以開啟 [組建通用 Windows 平台] 視窗：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

在 [組建通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的組建，例如 D:\MixedRealityLearning\Builds  ，建立新的資料夾並指定適當的名稱，例如 GettingStarted  ，然後按一下 [選取資料夾]  按鈕開始組建程序：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

等候 Unity 完成組建程序：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.組建和部署應用程式

當組建程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。 瀏覽該資料夾，按兩下解決方案的檔案即可在 Visual Studio 中開啟該檔案：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> 如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同[安裝工具](install-the-tools.md)文件中所指定。

設定 Visual Studio 以便用於 HoloLens 2，請選取 [Master]  或 [Release]  設定、[ARM]  架構，選取 [裝置]  作為目標：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

將 HoloLens 2 連線到您的電腦。

> [!IMPORTANT]
> 在組建您的裝置之前，裝置必須處於「開發人員模式」，並與開發電腦配對。 請遵循[這些指示](using-visual-studio.md)來完成這兩個步驟。

最後一個步驟是選取 [偵錯]   >  [啟動但不偵錯]  ，來對您的裝置進行建置和部署：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

雖然這些指示假設您會部署到 HoloLens 2 裝置，但是您也可以部署到 [HoloLens 2 模擬器](using-the-hololens-emulator.md)或是建立[用於側載的應用程式套件](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)。

選取 [啟動但不偵錯] 會讓裝置上的應用程式在組建成功時立即啟動，但 Visual Studio 中不會連接偵錯工具，也不會出現資訊。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。

若要在不自動啟動應用程式的情況下對您的裝置進行部署，您可以選取 [組建] > [部署解決方案]。

## <a name="congratulations"></a>恭喜！

<!-- TODO: Consider cleanup and adding in app screenshots -->
您現在已部署第一個 HoloLens 2 應用程式。 當您隨處走動時，您應該會看到空間對應網格涵蓋了所有 HoloLens 2 所感知到的介面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。 這些只是混合實境工具組的幾個現成基本項目。 在之後的教學課程中，您將開始在場景中加入更多內容和互動項目，讓您可以完整地探索 HoloLens 2 及混合實境工具組的功能。

> [!NOTE]
> 您可能會注意到應用程式中的診斷分析工具，可以使用 **Toogle Diagnostics** 語音命令來切換其可見度。 不過，通常會建議您在開發期間讓診斷分析工具保持隨時可見，以了解變更應用程式可能會影響效能的時機，例如 HoloLens 2 應用程式應[持續在 60 FPS 執行](understanding-performance-for-mixed-reality.md)。

[下一個教學課程：3.建立使用者介面並設定混合實境工具組](mrlearning-base-ch2.md)
