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
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="9acbe-105">2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="9acbe-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="9acbe-106">概觀</span><span class="sxs-lookup"><span data-stu-id="9acbe-106">Overview</span></span>

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
<span data-ttu-id="9acbe-107">在此第一篇教學課程中，您將了解<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合實境工具組 (MRTK)</a>提供的一些功能，然後啟動第一個適用於 HoloLens 2 的應用程式，並將其部署到裝置。</span><span class="sxs-lookup"><span data-stu-id="9acbe-107">In this first tutorial, you will learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="9acbe-108">目標</span><span class="sxs-lookup"><span data-stu-id="9acbe-108">Objectives</span></span>

* <span data-ttu-id="9acbe-109">設定 Unity 以用於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="9acbe-109">Configure Unity for HoloLens development</span></span>
* <span data-ttu-id="9acbe-110">匯入資產並設定場景</span><span class="sxs-lookup"><span data-stu-id="9acbe-110">Import assets and set up the scene</span></span>
* <span data-ttu-id="9acbe-111">空間對應網格、手部網格和畫面播放速率計數器的視覺效果</span><span class="sxs-lookup"><span data-stu-id="9acbe-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9acbe-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="9acbe-112">Prerequisites</span></span>

* <span data-ttu-id="9acbe-113">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="9acbe-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="9acbe-114">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="9acbe-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9acbe-115">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="9acbe-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="9acbe-116">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="9acbe-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="9acbe-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="9acbe-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9acbe-118">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="9acbe-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="9acbe-119">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="9acbe-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="9acbe-120">建立新的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="9acbe-120">Create new Unity project</span></span>

<span data-ttu-id="9acbe-121">啟動 **Unity Hub**，選取 [專案]  索引標籤，然後按一下 [新增]  按鈕旁的**向下箭號**：</span><span class="sxs-lookup"><span data-stu-id="9acbe-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

<span data-ttu-id="9acbe-123">選取上述[必要條件](#prerequisites)一節中指定的 Unity 版本：</span><span class="sxs-lookup"><span data-stu-id="9acbe-123">Select the Unity version specified in the [Prerequisites](#prerequisites) section above:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

<span data-ttu-id="9acbe-125">在 [建立新專案] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="9acbe-125">In the Create a new project window:</span></span>

* <span data-ttu-id="9acbe-126">確定 [範本]  設定為 [3D] </span><span class="sxs-lookup"><span data-stu-id="9acbe-126">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="9acbe-127">輸入適當的 [專案名稱]  ，例如 MRTK Tutorials </span><span class="sxs-lookup"><span data-stu-id="9acbe-127">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="9acbe-128">選擇適當的 [位置]  來儲存您的專案，例如 D:\MixedRealityLearning </span><span class="sxs-lookup"><span data-stu-id="9acbe-128">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="9acbe-129">按一下 [建立]  按鈕，以建立並啟動新的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="9acbe-129">Click the **Create** button to create and launch your new Unity project</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="9acbe-131">在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="9acbe-131">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="9acbe-132">Unity 受到這些限制的影響，如果有任何檔案路徑的長度超過 255 個字元，可能無法編譯。</span><span class="sxs-lookup"><span data-stu-id="9acbe-132">Unity is affected by these limits and may fail to compile if any file path is longer than 255 characters.</span></span> <span data-ttu-id="9acbe-133">因此，強烈建議您盡可能將 Unity 專案儲存在接近磁碟機根目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="9acbe-133">Consequently, it is strongly recommended to store your Unity project as close to the root of the drive as possible.</span></span>

<span data-ttu-id="9acbe-134">等候 Unity 建立專案：</span><span class="sxs-lookup"><span data-stu-id="9acbe-134">Wait for Unity to create the project:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="9acbe-136">設定適用於 Windows Mixed Reality 的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="9acbe-136">Configure the Unity project for Windows Mixed Reality</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="9acbe-137">在本節中，您將切換組建平台、啟用虛擬實境，並啟用空間感知功能。</span><span class="sxs-lookup"><span data-stu-id="9acbe-137">In this section, you will switch build platform, enable virtual reality, and enable spatial perception.</span></span>

### <a name="1-switch-build-platform"></a><span data-ttu-id="9acbe-138">1.切換組建平台</span><span class="sxs-lookup"><span data-stu-id="9acbe-138">1. Switch build platform</span></span>

<span data-ttu-id="9acbe-139">在 Unity 功能表中，選取 [檔案]   >  [組建設定...]  來開啟 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9acbe-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

<span data-ttu-id="9acbe-141">在 [組建設定] 視窗中，選取 [通用 Windows 平台]  ，然後按一下 [切換平台]  按鈕：</span><span class="sxs-lookup"><span data-stu-id="9acbe-141">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

<span data-ttu-id="9acbe-143">等候 Unity 完成平台的切換：</span><span class="sxs-lookup"><span data-stu-id="9acbe-143">Wait for Unity to finish switching the platform:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

<span data-ttu-id="9acbe-145">當 Unity 完成平台切換之後，按一下紅色 **x** 圖示以關閉 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9acbe-145">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a><span data-ttu-id="9acbe-147">2.啟用虛擬實境</span><span class="sxs-lookup"><span data-stu-id="9acbe-147">2. Enable virtual reality</span></span>

> [!NOTE]
> <span data-ttu-id="9acbe-148">「啟用虛擬實境」也適用於混合實境和擴增實境頭戴式裝置，因為都是啟用立體視覺，也就是為每隻眼睛轉譯不同影像。</span><span class="sxs-lookup"><span data-stu-id="9acbe-148">Enabling virtual reality also applies to mixed reality and augmented reality headsets because it refers to enabling stereoscopic vision, i.e. rendering different images for each eye.</span></span>

<span data-ttu-id="9acbe-149">在 Unity 功能表中，選取 [編輯]   >  [專案設定...]  來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9acbe-149">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

<span data-ttu-id="9acbe-151">在 [專案設定] 視窗中，選取 [播放器]   >  [XR 設定]  以展開 [XR 設定]：</span><span class="sxs-lookup"><span data-stu-id="9acbe-151">In the Project Settings window, select **Player** > **XR Settings** to expand the XR Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

<span data-ttu-id="9acbe-153">在 [XR 設定] 中，選取 [支援的虛擬實境]  核取方塊以啟用虛擬實境，按一下 **+** 圖示，然後選取 [Windows Mixed Reality]  以新增 Windows Mixed Reality SDK：</span><span class="sxs-lookup"><span data-stu-id="9acbe-153">In the XR Settings, check the **Virtual Reality Supported** checkbox to enable virtual reality, then click the **+** icon and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

<span data-ttu-id="9acbe-155">等候 Unity 完成 SDK 的新增：</span><span class="sxs-lookup"><span data-stu-id="9acbe-155">Wait for Unity to finish adding the SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

<span data-ttu-id="9acbe-157">當 Unity 完成新增 SDK 之後，將 XR 設定最佳化，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9acbe-157">When Unity has finished adding the SDK, optimize the XR Settings as follows:</span></span>

* <span data-ttu-id="9acbe-158">將 Windows Mixed Reality 的 [深度格式]  設為 [16 位元深度] </span><span class="sxs-lookup"><span data-stu-id="9acbe-158">Set Windows Mixed Reality **Depth Format** to **16-bit depth**</span></span>
* <span data-ttu-id="9acbe-159">勾選 Windows Mixed Reality 的 [啟用深度共用]  核取方塊</span><span class="sxs-lookup"><span data-stu-id="9acbe-159">Check the Windows Mixed Reality **Enable Depth Sharing** checkbox</span></span>
* <span data-ttu-id="9acbe-160">將 [立體聲轉譯模式\*]  設為 [單通道執行個體化] </span><span class="sxs-lookup"><span data-stu-id="9acbe-160">Set Stereo **Rendering Mode\*** to **Single Pass Instanced**</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> <span data-ttu-id="9acbe-162">若要深入瞭解如何將用於 Windows Mixed Reality 的 Unity 最佳化，您可以參閱 [Unity 的建議設定](recommended-settings-for-unity.md)文件。</span><span class="sxs-lookup"><span data-stu-id="9acbe-162">To learn more about optimizing Unity for Windows Mixed Reality, you can refer to the [Recommended settings for Unity](recommended-settings-for-unity.md) documentation.</span></span>

### <a name="3-enable-spatial-perception"></a><span data-ttu-id="9acbe-163">3.啟用空間感知</span><span class="sxs-lookup"><span data-stu-id="9acbe-163">3. Enable spatial perception</span></span>

> [!NOTE]
> <span data-ttu-id="9acbe-164">空間感知可讓 Windows Mixed Reality 裝置上的空間對應網格視覺化。</span><span class="sxs-lookup"><span data-stu-id="9acbe-164">Spatial perception allows visualization of the spatial mapping mesh on Windows Mixed Reality devices.</span></span>

<span data-ttu-id="9acbe-165">在 [專案設定] 視窗中，選取 [播放器]   >  [發佈設定]  以展開發佈設定：</span><span class="sxs-lookup"><span data-stu-id="9acbe-165">In the Project Settings window, select **Player** > **Publishing Settings** to expand the Publishing Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

<span data-ttu-id="9acbe-167">在 [發佈設定] 中，向下捲動至 [功能]  區段，然後勾選 [SpatialPerception]  核取方塊：</span><span class="sxs-lookup"><span data-stu-id="9acbe-167">In the Publishing Settings, scroll down to the **Capabilities** section and check the **SpatialPerception** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

<span data-ttu-id="9acbe-169">關閉 [專案設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="9acbe-169">Close the Project Settings window.</span></span>

## <a name="import-textmesh-pro-essential-resources"></a><span data-ttu-id="9acbe-170">匯入 TextMesh Pro 基本資源</span><span class="sxs-lookup"><span data-stu-id="9acbe-170">Import TextMesh Pro Essential Resources</span></span>

> [!NOTE]
> <span data-ttu-id="9acbe-171">我們正在匯入此套件，因為混合實境工具組的 UI 元素會需要。</span><span class="sxs-lookup"><span data-stu-id="9acbe-171">We are importing this package because it is required by Mixed Reality Toolkit's UI elements.</span></span>

<span data-ttu-id="9acbe-172">在 Unity 功能表中，選取 [視窗]   >  [TextMeshPro]   >  [匯入 TMP 基本資源]  ：</span><span class="sxs-lookup"><span data-stu-id="9acbe-172">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

<span data-ttu-id="9acbe-174">在 [匯入 Unity 套件] 視窗中，按一下 [全部]  按鈕以確保選取所有資產，然後按一下 [匯入]  按鈕來匯入資產：</span><span class="sxs-lookup"><span data-stu-id="9acbe-174">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="9acbe-176">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="9acbe-176">Import the Mixed Reality Toolkit</span></span>

<span data-ttu-id="9acbe-177">下載 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="9acbe-177">Download the Unity custom package:</span></span>

* [<span data-ttu-id="9acbe-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9acbe-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.2.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage)

<span data-ttu-id="9acbe-179">在 Unity 功能表中，選取 [資產]   >  [匯入套件]   >  [自訂套件 ...]  以開啟 [匯入套件...] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9acbe-179">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

<span data-ttu-id="9acbe-181">在 [匯入套件...] 視窗中，選取您下載的 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage**，然後按一下 [開啟]  按鈕：</span><span class="sxs-lookup"><span data-stu-id="9acbe-181">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

<span data-ttu-id="9acbe-183">在 [匯入 Unity 套件] 視窗中，按一下 [全部]  按鈕以確保選取所有資產，然後按一下 [匯入]  按鈕來匯入資產：</span><span class="sxs-lookup"><span data-stu-id="9acbe-183">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a><span data-ttu-id="9acbe-185">設定用於混合實境工具組的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="9acbe-185">Configure the Unity project for the Mixed Reality Toolkit</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="9acbe-186">匯入套件之後，應該會出現 [MRTK 專案設定程式] 視窗。</span><span class="sxs-lookup"><span data-stu-id="9acbe-186">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="9acbe-187">如果沒有，請在 Unity 功能表中選取 [混合現實工具組]   >  [公用程式]   >  [設定 Unity 專案]  加以開啟。</span><span class="sxs-lookup"><span data-stu-id="9acbe-187">If it does not, open it by selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** in the Unity menu.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

<span data-ttu-id="9acbe-189">在 [MRTK 專案設定程式] 視窗中，展開 [修改設定]  區段，取消勾選<u></u> [啟用適用於 Unity 的 MSBuild]  核取方塊，確定已勾選所有其他選項，然後按一下 [套用]  按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="9acbe-189">In the MRTK Project Configurator window, expand the **Modify Configurations** section, <u>uncheck</u> the **Enable MSBuild for Unity** checkbox, ensure all other options are checked, and click the **Apply** button to apply the settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="9acbe-191">適用於 Unity 的 MSBuild 可能不支援您將使用的所有 SDK，且在啟用之後，可能會很難停用。</span><span class="sxs-lookup"><span data-stu-id="9acbe-191">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="9acbe-192">因此，強烈建議您不要啟用適用於 Unity 的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="9acbe-192">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="9acbe-193">設定混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="9acbe-193">Configure the Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

<span data-ttu-id="9acbe-194">在 Unity 功能表中，選取 [混合實境工具組]   >  [新增至場景並設定...]  來將混合實境工具組新增至目前的場景：</span><span class="sxs-lookup"><span data-stu-id="9acbe-194">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the Mixed Reality Toolkit to your current scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

<span data-ttu-id="9acbe-196">在 [階層] 視窗中選取 MixedRealityToolkit 物件之後，在 [偵測器] 視窗中，將 [混合實境工具組] 設定中的設定檔變更為 **DefaultHoloLens2ConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="9acbe-196">With the MixedRealityToolkit object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit configuration profile to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

<span data-ttu-id="9acbe-198">在 Unity 功能表中，選取 [檔案]   >  [另存新檔 ...]  以開啟 [儲存場景] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9acbe-198">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

<span data-ttu-id="9acbe-200">在 [儲存場景] 視窗中，瀏覽至專案的 **Scenes** 資料夾，為您的場景取一個適當的名稱，例如 Getting Started  ，然後按一下 [儲存]  按鈕儲存場景：</span><span class="sxs-lookup"><span data-stu-id="9acbe-200">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _Getting Started_, and click the **Save** button to save the scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="9acbe-202">對您的裝置建置應用程式</span><span class="sxs-lookup"><span data-stu-id="9acbe-202">Build your application to your device</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="9acbe-203">1.組建 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="9acbe-203">1. Build the Unity project</span></span>

<span data-ttu-id="9acbe-204">在 Unity 功能表中，選取 [檔案]   >  [組建設定...]  來開啟 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="9acbe-204">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="9acbe-205">在 [組建設定] 視窗中，按一下 [新增開啟的場景]  按鈕，將您目前的場景新增至 [組建中的場景]  清單，然後按一下 [組建]  按鈕以開啟 [組建通用 Windows 平台] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9acbe-205">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

<span data-ttu-id="9acbe-207">在 [組建通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的組建，例如 D:\MixedRealityLearning\Builds  ，建立新的資料夾並指定適當的名稱，例如 GettingStarted  ，然後按一下 [選取資料夾]  按鈕開始組建程序：</span><span class="sxs-lookup"><span data-stu-id="9acbe-207">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

<span data-ttu-id="9acbe-209">等候 Unity 完成組建程序：</span><span class="sxs-lookup"><span data-stu-id="9acbe-209">Wait for Unity to finish the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="9acbe-211">2.組建和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="9acbe-211">2. Build and deploy the application</span></span>

<span data-ttu-id="9acbe-212">當組建程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。</span><span class="sxs-lookup"><span data-stu-id="9acbe-212">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="9acbe-213">瀏覽該資料夾，按兩下解決方案的檔案即可在 Visual Studio 中開啟該檔案：</span><span class="sxs-lookup"><span data-stu-id="9acbe-213">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> <span data-ttu-id="9acbe-215">如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同[安裝工具](install-the-tools.md)文件中所指定。</span><span class="sxs-lookup"><span data-stu-id="9acbe-215">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the [Install the Tools](install-the-tools.md) documentation.</span></span>

<span data-ttu-id="9acbe-216">設定 Visual Studio 以便用於 HoloLens 2，請選取 [Master]  或 [Release]  設定、[ARM]  架構，選取 [裝置]  作為目標：</span><span class="sxs-lookup"><span data-stu-id="9acbe-216">Configure Visual Studio for HoloLens 2 by selecting the **Master** or **Release** configuration, the **ARM** architecture, and **Device** as target:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

<span data-ttu-id="9acbe-218">將 HoloLens 2 連線到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="9acbe-218">Connect your HoloLens 2 to your computer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9acbe-219">在組建您的裝置之前，裝置必須處於「開發人員模式」，並與開發電腦配對。</span><span class="sxs-lookup"><span data-stu-id="9acbe-219">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="9acbe-220">請遵循[這些指示](using-visual-studio.md)來完成這兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="9acbe-220">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

<span data-ttu-id="9acbe-221">最後一個步驟是選取 [偵錯]   >  [啟動但不偵錯]  ，來對您的裝置進行建置和部署：</span><span class="sxs-lookup"><span data-stu-id="9acbe-221">The final step is to build and deploy to your device by selecting **Debug** > **Start Without Debugging**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

<span data-ttu-id="9acbe-223">雖然這些指示假設您會部署到 HoloLens 2 裝置，但是您也可以部署到 [HoloLens 2 模擬器](using-the-hololens-emulator.md)或是建立[用於側載的應用程式套件](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)。</span><span class="sxs-lookup"><span data-stu-id="9acbe-223">While these instructions assume you will be deploying to a HoloLens 2 device, you can also deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span></span>

<span data-ttu-id="9acbe-224">選取 [啟動但不偵錯] 會讓裝置上的應用程式在組建成功時立即啟動，但 Visual Studio 中不會連接偵錯工具，也不會出現資訊。</span><span class="sxs-lookup"><span data-stu-id="9acbe-224">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="9acbe-225">這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。</span><span class="sxs-lookup"><span data-stu-id="9acbe-225">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

<span data-ttu-id="9acbe-226">若要在不自動啟動應用程式的情況下對您的裝置進行部署，您可以選取 [組建] > [部署解決方案]。</span><span class="sxs-lookup"><span data-stu-id="9acbe-226">To deploy to your device without having the application start automatically, you can select Build > Deploy Solution.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9acbe-227">恭喜！</span><span class="sxs-lookup"><span data-stu-id="9acbe-227">Congratulations</span></span>

<!-- TODO: Consider cleanup and adding in app screenshots -->
<span data-ttu-id="9acbe-228">您現在已部署第一個 HoloLens 2 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9acbe-228">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="9acbe-229">當您隨處走動時，您應該會看到空間對應網格涵蓋了所有 HoloLens 2 所感知到的介面。</span><span class="sxs-lookup"><span data-stu-id="9acbe-229">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="9acbe-230">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="9acbe-230">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="9acbe-231">這些只是混合實境工具組的幾個現成基本項目。</span><span class="sxs-lookup"><span data-stu-id="9acbe-231">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="9acbe-232">在之後的教學課程中，您將開始在場景中加入更多內容和互動項目，讓您可以完整地探索 HoloLens 2 及混合實境工具組的功能。</span><span class="sxs-lookup"><span data-stu-id="9acbe-232">In the tutorials to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="9acbe-233">您可能會注意到應用程式中的診斷分析工具，可以使用 **Toogle Diagnostics** 語音命令來切換其可見度。</span><span class="sxs-lookup"><span data-stu-id="9acbe-233">In the app, you may notice the Diagnostics profiler, you can toggle it's visibility using the speech command **Toogle Diagnostics**.</span></span> <span data-ttu-id="9acbe-234">不過，通常會建議您在開發期間讓診斷分析工具保持隨時可見，以了解變更應用程式可能會影響效能的時機，例如 HoloLens 2 應用程式應[持續在 60 FPS 執行](understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="9acbe-234">However, it is generally recommended to keep the profiler visible at all times during development to understand when changes to the app may have impacted performance, for example, HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="9acbe-235">下一個教學課程：3.建立使用者介面並設定混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="9acbe-235">Next Tutorial: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
