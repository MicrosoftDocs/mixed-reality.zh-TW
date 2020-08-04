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
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="930a2-105">2.初始化您的專案並部署您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="930a2-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="930a2-106">概觀</span><span class="sxs-lookup"><span data-stu-id="930a2-106">Overview</span></span>

<span data-ttu-id="930a2-107">在本教學課程中，您將了解如何建立新的 Unity 專案、將其設定為<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合實境工具組 (MRTK)</a>開發之用，以及匯入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="930a2-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="930a2-108">您也將逐步了解如何設定、建置並從 Visual Studio 將基本 Unity 範例場景部署到 HoloLens 2 或模擬器。</span><span class="sxs-lookup"><span data-stu-id="930a2-108">You'll also walk through configuring, building, and deploying the basic Unity sample scene from Visual Studio to your HoloLens 2 or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="930a2-109">目標</span><span class="sxs-lookup"><span data-stu-id="930a2-109">Objectives</span></span>

* <span data-ttu-id="930a2-110">了解如何設定 Unity 以用於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="930a2-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="930a2-111">了解如何建置應用程式並部署至 HoloLens</span><span class="sxs-lookup"><span data-stu-id="930a2-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="930a2-112">空間對應網格、手部網格和畫面播放速率計數器體驗</span><span class="sxs-lookup"><span data-stu-id="930a2-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="930a2-113">建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="930a2-113">Creating the Unity project</span></span>

<span data-ttu-id="930a2-114">啟動 **Unity Hub**，選取 [專案] 索引標籤，然後按一下 [新增] 按鈕旁的**向下箭號**：</span><span class="sxs-lookup"><span data-stu-id="930a2-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="930a2-116">在下拉式清單中，選取[必要條件](mr-learning-base-01.md#prerequisites)中所指定的 Unity **版本**：</span><span class="sxs-lookup"><span data-stu-id="930a2-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="930a2-118">如果 Unity Hub 中無法使用特定的 Unity 版本，您可以從 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下載封存</a>起始安裝。</span><span class="sxs-lookup"><span data-stu-id="930a2-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="930a2-119">在 [建立新專案] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="930a2-119">In the Create a new project window:</span></span>

* <span data-ttu-id="930a2-120">確定 [範本] 設定為 [3D]</span><span class="sxs-lookup"><span data-stu-id="930a2-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="930a2-121">輸入適當的 [專案名稱]，例如 MRTK Tutorials</span><span class="sxs-lookup"><span data-stu-id="930a2-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="930a2-122">選擇適當的 [位置] 來儲存您的專案，例如 D:\MixedRealityLearning</span><span class="sxs-lookup"><span data-stu-id="930a2-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="930a2-123">按一下 [建立] 按鈕，以建立並啟動新的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="930a2-123">Click the **Create** button to create and launch your new Unity project</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="930a2-125">在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="930a2-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="930a2-126">因此，您應該將 Unity 專案儲存在磁碟機的根目錄附近。</span><span class="sxs-lookup"><span data-stu-id="930a2-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="930a2-127">等候 Unity 建立專案：</span><span class="sxs-lookup"><span data-stu-id="930a2-127">Wait for Unity to create the project:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="930a2-129">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="930a2-129">Switching the build platform</span></span>

<span data-ttu-id="930a2-130">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="930a2-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="930a2-132">在 [組建設定] 視窗中，選取 [通用 Windows 平台]，然後按一下 [切換平台] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="930a2-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="930a2-134">等候 Unity 完成平台的切換：</span><span class="sxs-lookup"><span data-stu-id="930a2-134">Wait for Unity to finish switching the platform:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="930a2-136">當 Unity 完成平台切換之後，按一下紅色 **x** 圖示以關閉 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="930a2-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="930a2-138">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="930a2-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="930a2-139">在 Unity 功能表中，選取 [視窗] >  [TextMeshPro]  >  [匯入 TMP 基本資源] 以開啟 [匯入 Unity 套件] 視窗：</span><span class="sxs-lookup"><span data-stu-id="930a2-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="930a2-141">在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：</span><span class="sxs-lookup"><span data-stu-id="930a2-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="930a2-143">MRTK 的 UI 元素需要 TextMeshPro 基本資源。</span><span class="sxs-lookup"><span data-stu-id="930a2-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="930a2-144">如果您不打算在專案中使用 MRTK 的 UI 元素，則可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="930a2-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="930a2-145">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="930a2-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="930a2-146">下載 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="930a2-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="930a2-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="930a2-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

<span data-ttu-id="930a2-148">在 Unity 功能表中，選取 [資產]  >  [匯入套件]  >  [自訂套件 ...] 以開啟 [匯入套件...] 視窗：</span><span class="sxs-lookup"><span data-stu-id="930a2-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="930a2-150">在 [匯入套件...] 視窗中，選取您下載的 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage**，然後按一下 [開啟] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="930a2-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="930a2-152">在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：</span><span class="sxs-lookup"><span data-stu-id="930a2-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="930a2-154">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="930a2-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="930a2-155">1.套用 MRTK 專案配置器設定</span><span class="sxs-lookup"><span data-stu-id="930a2-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="930a2-156">Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="930a2-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="930a2-157">如果沒有，請前往 Unity 功能表，然後選取 [混合實境工具組] > [公用程式] > [設定 Unity Project]，以開啟 [配置器] 視窗：</span><span class="sxs-lookup"><span data-stu-id="930a2-157">If it doesn't, open the Configurator window by going to the Unity menu and selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="930a2-159">在 [MRTK 專案設定程式] 視窗中，展開 [修改設定] 區段，確定已勾選所有其他選項，然後按一下 [套用] 按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="930a2-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="930a2-161">2.設定其他專案設定</span><span class="sxs-lookup"><span data-stu-id="930a2-161">2. Configure additional project settings</span></span>

<span data-ttu-id="930a2-162">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="930a2-162">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="930a2-164">在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，按一下 **+** 圖示，然後選取 Windows Mixed Reality 來新增 Windows Mixed Reality SDK：</span><span class="sxs-lookup"><span data-stu-id="930a2-164">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="930a2-166">Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="930a2-166">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="930a2-167">如果沒有出現，請使用 Unity 功能表開啟。</span><span class="sxs-lookup"><span data-stu-id="930a2-167">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="930a2-168">在 [MRTK 專案設定] 視窗中，使用**Audio 空間定位器**下拉式清單選取 [MS HRTF 空間定位器]，然後按一下 [套用] 按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="930a2-168">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="930a2-170">在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，然後使用**深度格式**下拉式清單選取 **16 位元深度**：</span><span class="sxs-lookup"><span data-stu-id="930a2-170">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="930a2-172">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在**套件名稱**欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="930a2-172">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> <span data-ttu-id="930a2-174">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="930a2-174">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="930a2-175">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="930a2-175">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="930a2-176">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="930a2-176">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="930a2-177">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="930a2-177">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="930a2-178">建立和設定場景</span><span class="sxs-lookup"><span data-stu-id="930a2-178">Creating and configuring the scene</span></span>

<span data-ttu-id="930a2-179">在 Unity 功能表中，選取 [檔案] > [新增場景] 以建立新場景：</span><span class="sxs-lookup"><span data-stu-id="930a2-179">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="930a2-181">在 Unity 功能表中，選取 [混合實境工具組] >  [新增至場景並設定...] 來將 MRTK 新增至目前的場景：</span><span class="sxs-lookup"><span data-stu-id="930a2-181">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="930a2-183">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件後，在 [偵測器] 視窗中，驗證 **MixedRealityToolkit** 設定中的設定檔是否變更為 **DefaultMixedRealityToolkitConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="930a2-183">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="930a2-185">通常，在開發 HoloLens 時會使用 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="930a2-185">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="930a2-186">不過，基於本教學課程的目的，您會使用 DefaultMixedRealityToolkitConfigurationProfile，然後在下一個教學課程[設定 MRTK 工具組](mr-learning-base-03.md)中，改為使用 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="930a2-186">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="930a2-187">在 Unity 功能表中，選取 [檔案] >  [另存新檔 ...] 以開啟 [儲存場景] 視窗：</span><span class="sxs-lookup"><span data-stu-id="930a2-187">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="930a2-189">在 [儲存場景] 視窗中，瀏覽至專案的 **Scenes** 資料夾，為您的場景取一個適當的名稱，例如 _GettingStarted_，然後按一下 [儲存] 按鈕以儲存場景：</span><span class="sxs-lookup"><span data-stu-id="930a2-189">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="930a2-191">在您的 HoloLens 2 上建置應用程式</span><span class="sxs-lookup"><span data-stu-id="930a2-191">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="930a2-192">1.組建 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="930a2-192">1. Build the Unity project</span></span>

<span data-ttu-id="930a2-193">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="930a2-193">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="930a2-194">在 [組建設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至 [組建中的場景] 清單，然後按一下 [組建] 按鈕以開啟 [組建通用 Windows 平台] 視窗：</span><span class="sxs-lookup"><span data-stu-id="930a2-194">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="930a2-196">在 [組建通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的組建，例如 D:\MixedRealityLearning\Builds，建立新的資料夾並指定適當的名稱，例如 GettingStarted，然後按一下 [選取資料夾] 按鈕開始組建程序：</span><span class="sxs-lookup"><span data-stu-id="930a2-196">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="930a2-198">等候 Unity 完成組建程序：</span><span class="sxs-lookup"><span data-stu-id="930a2-198">Wait for Unity to finish the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="930a2-200">2.組建和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="930a2-200">2. Build and deploy the application</span></span>

<span data-ttu-id="930a2-201">當建置程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。</span><span class="sxs-lookup"><span data-stu-id="930a2-201">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="930a2-202">瀏覽該資料夾，按兩下解決方案的檔案即可在 Visual Studio 中開啟該檔案：</span><span class="sxs-lookup"><span data-stu-id="930a2-202">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="930a2-204">如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同 **[安裝工具](install-the-tools.md)** 文件中所述。</span><span class="sxs-lookup"><span data-stu-id="930a2-204">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="930a2-205">設定 Visual Studio 以便用於 HoloLens，請選取 [Master] 或 [Release] 設定、[ARM64] 架構，選取 [裝置] 作為目標：</span><span class="sxs-lookup"><span data-stu-id="930a2-205">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="930a2-207">如果您要部署至 HoloLens (第1代)，請選取 **x86** 架構。</span><span class="sxs-lookup"><span data-stu-id="930a2-207">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="930a2-208">若是 HoloLens，您通常會建立 ARM 架構。</span><span class="sxs-lookup"><span data-stu-id="930a2-208">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="930a2-209">不過，在 Visual Studio 中選取 ARM 作為建置架構時，Unity 2019.3 中的<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知問題</strong></a>會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="930a2-209">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="930a2-210">建議的解決方法是以 ARM64 建置。</span><span class="sxs-lookup"><span data-stu-id="930a2-210">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="930a2-211">如果無法這麼做，請移至**編輯 > 專案設定 > 播放程式 > 其他設定** 並停用**圖形作業**。</span><span class="sxs-lookup"><span data-stu-id="930a2-211">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="930a2-212">如果您看不到 [裝置為目標] 選項，可能需要將 Visual Studio 解決方案的啟始專案從 IL2CPP 專案變更為 UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="930a2-212">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="930a2-213">要這麼做，在方案總管中，以滑鼠右鍵按一下 YourProjectName (Universal Windows) 並選取 [設定為啟動專案]。</span><span class="sxs-lookup"><span data-stu-id="930a2-213">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="930a2-214">將 HoloLens 與電腦連線，然後選取 [偵錯] > [啟動但不進行偵錯]，以建置並部署至您的裝置：</span><span class="sxs-lookup"><span data-stu-id="930a2-214">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="930a2-216">在組建您的裝置之前，裝置必須處於「開發人員模式」，並與開發電腦配對。</span><span class="sxs-lookup"><span data-stu-id="930a2-216">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="930a2-217">請遵循[這些指示](using-visual-studio.md)來完成這兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="930a2-217">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="930a2-218">您也可以部署到 [HoloLens 模擬器](using-the-hololens-emulator.md) 或為側載建立[應用程式套件](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)。</span><span class="sxs-lookup"><span data-stu-id="930a2-218">You can also deploy to the [HoloLens Emulator](using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="930a2-219">使用 [啟動但不進行偵測] 會自動啟動您裝置上的應用程式，而不會附加 Visual Studio 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="930a2-219">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="930a2-220">若要在不自動啟動應用程式的情況下部署裝置，選取 [組建] > [部署解決方案]。</span><span class="sxs-lookup"><span data-stu-id="930a2-220">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="930a2-221">您可能會注意到應用程式中的診斷分析工具，您可以使用 **Toggle Diagnostics** 語音命令開啟或關閉此工具。</span><span class="sxs-lookup"><span data-stu-id="930a2-221">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="930a2-222">建議您在開發期間儘量讓分析工具保持可見，以了解應用程式的變更何時會對效能產生影響。</span><span class="sxs-lookup"><span data-stu-id="930a2-222">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="930a2-223">例如，HoloLens 應用程式應該[持續以 60 FPS 執行](understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="930a2-223">For example, HoloLens apps should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="930a2-224">恭喜！</span><span class="sxs-lookup"><span data-stu-id="930a2-224">Congratulations</span></span>

<span data-ttu-id="930a2-225">您現在已部署了第一個 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="930a2-225">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="930a2-226">當您隨處走動時，應該會看到空間對應網格涵蓋了所有 HoloLens 所感知到的表面。</span><span class="sxs-lookup"><span data-stu-id="930a2-226">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="930a2-227">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="930a2-227">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="930a2-228">這些功能只是 MRTK 所包含的幾個基本部分。</span><span class="sxs-lookup"><span data-stu-id="930a2-228">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="930a2-229">在接下來的教學課程中，您將會在場景中新增內容，以探索 HoloLens 和 MRTK 的功能。</span><span class="sxs-lookup"><span data-stu-id="930a2-229">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

[<span data-ttu-id="930a2-230">下一個教學課程：3.設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="930a2-230">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
