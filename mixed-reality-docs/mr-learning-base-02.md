---
title: 入門教學課程 - 2。 初始化您的專案並部署您的第一個應用程式
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5cac7d6f776619cbc2a0e0891b7915b656708726
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376650"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2.初始化您的專案並部署您的第一個應用程式

## <a name="overview"></a>概觀

在本教學課程中，您將了解如何建立新的 Unity 專案、將其設定為<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合實境工具組 (MRTK)</a>開發之用，以及匯入 MRTK。 您也將逐步了解如何設定、建置並從 Visual Studio 將基本 Unity 範例場景部署到 HoloLens 2 或模擬器。

## <a name="objectives"></a>目標

* 了解如何設定 Unity 以用於 HoloLens 開發
* 了解如何建置應用程式並部署至 HoloLens
* 空間對應網格、手部網格和畫面播放速率計數器體驗

## <a name="creating-the-unity-project"></a>建立 Unity 專案

啟動 **Unity Hub**，選取 [專案] 索引標籤，然後按一下 [新增] 按鈕旁的**向下箭號**：

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

在下拉式清單中，選取[必要條件](mr-learning-base-01.md#prerequisites)中所指定的 Unity **版本**：

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> 如果 Unity Hub 中無法使用特定的 Unity 版本，您可以從 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下載封存</a>起始安裝。

在 [建立新專案] 視窗中：

* 確定 [範本] 設定為 [3D]
* 輸入適當的 [專案名稱]，例如 MRTK Tutorials
* 選擇適當的 [位置] 來儲存您的專案，例如 D:\MixedRealityLearning
* 按一下 [建立] 按鈕，以建立並啟動新的 Unity 專案

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> 在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。 因此，您應該將 Unity 專案儲存在磁碟機的根目錄附近。

等候 Unity 建立專案：

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>切換建置平台

在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗：

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

在 [組建設定] 視窗中，選取 [通用 Windows 平台]，然後按一下 [切換平台] 按鈕：

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

等候 Unity 完成平台的切換：

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

當 Unity 完成平台切換之後，按一下紅色 **x** 圖示以關閉 [組建設定] 視窗：

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>匯入 TextMeshPro 基本資源

在 Unity 功能表中，選取 [視窗] >  [TextMeshPro]  >  [匯入 TMP 基本資源] 以開啟 [匯入 Unity 套件] 視窗：

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> MRTK 的 UI 元素需要 TextMeshPro 基本資源。 如果您不打算在專案中使用 MRTK 的 UI 元素，則可以略過此步驟。

## <a name="importing-the-mixed-reality-toolkit"></a>匯入混合實境工具組

下載 Unity 自訂套件：

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

在 Unity 功能表中，選取 [資產]  >  [匯入套件]  >  [自訂套件 ...] 以開啟 [匯入套件...] 視窗：

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

在 [匯入套件...] 視窗中，選取您下載的 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage**，然後按一下 [開啟] 按鈕：

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>設定 Unity 專案

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1.套用 MRTK 專案配置器設定

Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。 如果沒有，請前往 Unity 功能表，然後選取 [混合實境工具組] > [公用程式] > [設定 Unity Project]，以開啟 [配置器] 視窗：

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

在 [MRTK 專案設定程式] 視窗中，展開 [修改設定] 區段，確定已勾選所有其他選項，然後按一下 [套用] 按鈕來套用設定：

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a>2.設定其他專案設定

在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，按一下 **+** 圖示，然後選取 Windows Mixed Reality 來新增 Windows Mixed Reality SDK：

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。 如果沒有出現，請使用 Unity 功能表開啟。

在 [MRTK 專案設定] 視窗中，使用**Audio 空間定位器**下拉式清單選取 [MS HRTF 空間定位器]，然後按一下 [套用] 按鈕來套用設定：

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，然後使用**深度格式**下拉式清單選取 **16 位元深度**：

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在**套件名稱**欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> 「套件名稱」是應用程式的唯一識別碼。 您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。

> [!TIP]
> 「產品名稱」是 HoloLens 開始功能表中顯示的名稱。 若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。

## <a name="creating-and-configuring-the-scene"></a>建立和設定場景

在 Unity 功能表中，選取 [檔案] > [新增場景] 以建立新場景：

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

在 Unity 功能表中，選取 [混合實境工具組] >  [新增至場景並設定...] 來將 MRTK 新增至目前的場景：

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件後，在 [偵測器] 視窗中，驗證 **MixedRealityToolkit** 設定中的設定檔是否變更為 **DefaultMixedRealityToolkitConfigurationProfile**：

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> 通常，在開發 HoloLens 時會使用 DefaultHoloLens2ConfigurationProfile。 不過，基於本教學課程的目的，您會使用 DefaultMixedRealityToolkitConfigurationProfile，然後在下一個教學課程[設定 MRTK 工具組](mr-learning-base-03.md)中，改為使用 DefaultHoloLens2ConfigurationProfile。

在 Unity 功能表中，選取 [檔案] >  [另存新檔 ...] 以開啟 [儲存場景] 視窗：

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

在 [儲存場景] 視窗中，瀏覽至專案的 **Scenes** 資料夾，為您的場景取一個適當的名稱，例如 _GettingStarted_，然後按一下 [儲存] 按鈕以儲存場景：

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>在您的 HoloLens 2 上建置應用程式

### <a name="1-build-the-unity-project"></a>1.組建 Unity 專案

在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗。

在 [組建設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至 [組建中的場景] 清單，然後按一下 [組建] 按鈕以開啟 [組建通用 Windows 平台] 視窗：

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

在 [組建通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的組建，例如 D:\MixedRealityLearning\Builds，建立新的資料夾並指定適當的名稱，例如 GettingStarted，然後按一下 [選取資料夾] 按鈕開始組建程序：

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

等候 Unity 完成組建程序：

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.組建和部署應用程式

當建置程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。 瀏覽該資料夾，按兩下解決方案的檔案即可在 Visual Studio 中開啟該檔案：

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> 如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同 **[安裝工具](install-the-tools.md)** 文件中所述。

設定 Visual Studio 以便用於 HoloLens，請選取 [Master] 或 [Release] 設定、[ARM64] 架構，選取 [裝置] 作為目標：

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> 如果您要部署至 HoloLens (第1代)，請選取 **x86** 架構。

> [!NOTE]
> 若是 HoloLens，您通常會建立 ARM 架構。 不過，在 Visual Studio 中選取 ARM 作為建置架構時，Unity 2019.3 中的<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知問題</strong></a>會造成錯誤。 建議的解決方法是以 ARM64 建置。 如果無法這麼做，請移至**編輯 > 專案設定 > 播放程式 > 其他設定** 並停用**圖形作業**。

> [!NOTE]
> 如果您看不到 [裝置為目標] 選項，可能需要將 Visual Studio 解決方案的啟始專案從 IL2CPP 專案變更為 UWP 專案。 要這麼做，在方案總管中，以滑鼠右鍵按一下 YourProjectName (Universal Windows) 並選取 [設定為啟動專案]。

將 HoloLens 與電腦連線，然後選取 [偵錯] > [啟動但不進行偵錯]，以建置並部署至您的裝置：

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> 在組建您的裝置之前，裝置必須處於「開發人員模式」，並與開發電腦配對。 請遵循[這些指示](using-visual-studio.md)來完成這兩個步驟。

> [!TIP]
> 您也可以部署到 [HoloLens 模擬器](using-the-hololens-emulator.md) 或為側載建立[應用程式套件](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)。

使用 [啟動但不進行偵測] 會自動啟動您裝置上的應用程式，而不會附加 Visual Studio 偵錯工具。

若要在不自動啟動應用程式的情況下部署裝置，選取 [組建] > [部署解決方案]。

> [!NOTE]
>您可能會注意到應用程式中的診斷分析工具，您可以使用 **Toggle Diagnostics** 語音命令開啟或關閉此工具。 建議您在開發期間儘量讓分析工具保持可見，以了解應用程式的變更何時會對效能產生影響。 例如，HoloLens 應用程式應該[持續以 60 FPS 執行](understanding-performance-for-mixed-reality.md)。

## <a name="congratulations"></a>恭喜！

您現在已部署了第一個 HoloLens 應用程式。 當您隨處走動時，應該會看到空間對應網格涵蓋了所有 HoloLens 所感知到的表面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。 這些功能只是 MRTK 所包含的幾個基本部分。 在接下來的教學課程中，您將會在場景中新增內容，以探索 HoloLens 和 MRTK 的功能。

[下一個教學課程：3.設定 MRTK 設定檔](mr-learning-base-03.md)
