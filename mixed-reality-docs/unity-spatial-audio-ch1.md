---
title: 空間音訊教學課程-1。 將空間音訊新增至您的專案
description: 將 Microsoft 空間定位器外掛程式新增至您的 Unity 專案，以存取 HoloLens 2 HRTF 硬體卸載。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教學課程，hololens2，空間音訊
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182795"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="47403-105">將空間音訊新增至您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="47403-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="47403-106">歡迎使用 HoloLens2 上適用于 Unity 的空間音訊 tutioral。</span><span class="sxs-lookup"><span data-stu-id="47403-106">Welcome to the spatial audio tutioral for Unity on HoloLens2.</span></span> <span data-ttu-id="47403-107">本教學課程的順序顯示：</span><span class="sxs-lookup"><span data-stu-id="47403-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="47403-108">如何在 Unity 中的 HoloLens 2 上使用 HRTF 卸載</span><span class="sxs-lookup"><span data-stu-id="47403-108">How to use HRTF offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="47403-109">如何在使用 HRTF 卸載時啟用回音</span><span class="sxs-lookup"><span data-stu-id="47403-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="47403-110">[Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)已完成此教學課程式列的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="47403-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="47403-111">如需 spatialize 音效時的建議事項，請參閱[空間音效設計](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)。</span><span class="sxs-lookup"><span data-stu-id="47403-111">For our recommendations on when it can be helpful to spatialize sounds, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="objectives"></a><span data-ttu-id="47403-112">目標</span><span class="sxs-lookup"><span data-stu-id="47403-112">Objectives</span></span>
<span data-ttu-id="47403-113">在第一個章節中，您將會：</span><span class="sxs-lookup"><span data-stu-id="47403-113">In this first chapter, you'll:</span></span>
* <span data-ttu-id="47403-114">建立 Unity 專案並匯入 MRTK</span><span class="sxs-lookup"><span data-stu-id="47403-114">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="47403-115">匯入 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="47403-115">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="47403-116">啟用 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="47403-116">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="47403-117">在開發人員工作站上啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="47403-117">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="47403-118">建立專案並新增 Unity 的 NuGet</span><span class="sxs-lookup"><span data-stu-id="47403-118">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="47403-119">從空白的 Unity 專案開始，然後新增並設定適用于 Unity 的 NuGet：</span><span class="sxs-lookup"><span data-stu-id="47403-119">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="47403-120">下載最新的[NuGetForUnity。 unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="47403-120">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="47403-121">在 Unity 功能表列中，按一下 **資產-> 匯入套件-> 自訂套件 ...** ，然後安裝 NuGetForUnity 套件：</span><span class="sxs-lookup"><span data-stu-id="47403-121">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![匯入自訂套件](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="47403-123">新增 Windows Mixed Reality 封裝</span><span class="sxs-lookup"><span data-stu-id="47403-123">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="47403-124">Unity 2019 和更新版本中的 Windows Mixed Reality 支援包含在選擇性的封裝中。</span><span class="sxs-lookup"><span data-stu-id="47403-124">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="47403-125">若要將它新增至您的專案，請從 Unity 功能表列開啟 [**視窗 > 封裝管理員]** ：</span><span class="sxs-lookup"><span data-stu-id="47403-125">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![封裝管理員功能表](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="47403-127">然後尋找並安裝**Windows Mixed Reality**套件：</span><span class="sxs-lookup"><span data-stu-id="47403-127">Then find and install the **Windows Mixed Reality** package:</span></span>

![套件管理員視窗](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="47403-129">安裝 MRTK 和 Microsoft 空間定位器</span><span class="sxs-lookup"><span data-stu-id="47403-129">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="47403-130">使用適用于 Unity 的 NuGet，安裝 MRTK 和 Microsoft 空間定位器外掛程式：</span><span class="sxs-lookup"><span data-stu-id="47403-130">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="47403-131">在 Unity 功能表列中，按一下 [ **nuget-> 管理 Nuget 封裝**]。</span><span class="sxs-lookup"><span data-stu-id="47403-131">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![管理 NuGet 套件](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="47403-133">在**搜尋**方塊中，輸入 "MixedReality"，並安裝 MRTK core 套件： **MixedReality。**</span><span class="sxs-lookup"><span data-stu-id="47403-133">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![MRTK NuGet 套件](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="47403-135">[MRTK NuGet 套件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html)有其他內容和詳細資料。</span><span class="sxs-lookup"><span data-stu-id="47403-135">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="47403-136">在**搜尋**方塊中，輸入 "SpatialAudio" 並安裝 microsoft 空間定位器套件： **SpatialAudio. 空間定位器 Unity**</span><span class="sxs-lookup"><span data-stu-id="47403-136">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![空間定位器外掛程式 NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="47403-138">在您的專案中設定 MRTK</span><span class="sxs-lookup"><span data-stu-id="47403-138">Set up MRTK in your project</span></span>

1. <span data-ttu-id="47403-139">前往 [檔案 **-> 組建設定**]，開啟 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="47403-139">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="47403-140">選取_通用 Windows 平臺_，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="47403-140">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="47403-141">按一下 [**組建] 視窗**中的 [**玩家設定**]，以在 [偵測**器**] 窗格中開啟**播放 [設定**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="47403-141">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="47403-142">在 [ **XR 設定**] 下，勾選 [**支援虛擬實境**] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="47403-142">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="47403-143">在 [ **XR 設定**] 下，將 [**身歷聲轉譯模式]** 變更為 [**單一傳遞實例**]。</span><span class="sxs-lookup"><span data-stu-id="47403-143">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="47403-144">在 [**發行設定**] 底下，勾選 [**功能**] 區段中的 [**空間感知**] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="47403-144">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="47403-145">在功能表列上，按一下 **混合現實工具組-> 新增至場景並設定**。</span><span class="sxs-lookup"><span data-stu-id="47403-145">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="47403-146">將 MRTK 新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="47403-146">to add MRTK to your scene.</span></span>

<span data-ttu-id="47403-147">如需其他指引，包括如何建立您的應用程式並部署至 HoloLens 2，請參閱[MR 學習基底課程模組的第1章](mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="47403-147">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="47403-148">啟用 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="47403-148">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="47403-149">啟用**Microsoft 空間定位器**外掛程式。</span><span class="sxs-lookup"><span data-stu-id="47403-149">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="47403-150">開啟 [**編輯-> 專案設定]-> [音訊**]，然後將**空間定位器外掛程式**變更為 "Microsoft 空間定位器"。</span><span class="sxs-lookup"><span data-stu-id="47403-150">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="47403-151">**專案設定**的 [**音訊**] 區段現在會如下所示：</span><span class="sxs-lookup"><span data-stu-id="47403-151">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![顯示空間定位器外掛程式的專案設定](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="47403-153">在您的工作站上啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="47403-153">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="47403-154">在桌上出版本的 Windows 上，預設會停用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="47403-154">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="47403-155">以滑鼠右鍵按一下工作列中的音量圖示來加以啟用。</span><span class="sxs-lookup"><span data-stu-id="47403-155">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="47403-156">若要取得您在 HoloLens 2 上聽到的最佳呈現方式，請選擇 [**空間音效-> 適用于耳機的 Windows Sonic**]。</span><span class="sxs-lookup"><span data-stu-id="47403-156">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![桌面空間音訊設定](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="47403-158">只有當您計畫在 Unity 編輯器中測試專案時，才需要此設定。</span><span class="sxs-lookup"><span data-stu-id="47403-158">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="47403-159">後續步驟</span><span class="sxs-lookup"><span data-stu-id="47403-159">Next steps</span></span>
<span data-ttu-id="47403-160">繼續閱讀[Unity 空間音訊第2章](unity-spatial-audio-ch2.md)，以 spatialize 按鈕互動音效。</span><span class="sxs-lookup"><span data-stu-id="47403-160">Continue on to [Unity spatial audio chapter 2](unity-spatial-audio-ch2.md) to spatialize button interaction sounds.</span></span>

