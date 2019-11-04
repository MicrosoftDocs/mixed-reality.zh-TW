---
title: MR 空間 220-空間音效
description: 遵循此編碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解空間音效概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，學院，教學課程，空間音效
ms.openlocfilehash: a3fc054927d73cf9ac21f831caa4ec23875977bd
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434730"
---
>[!NOTE]
><span data-ttu-id="eebb2-104">混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="eebb2-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="eebb2-105">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="eebb2-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="eebb2-106">這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="eebb2-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="eebb2-107">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="eebb2-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="eebb2-108">HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。</span><span class="sxs-lookup"><span data-stu-id="eebb2-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="eebb2-109">MR 空間220：空間音效</span><span class="sxs-lookup"><span data-stu-id="eebb2-109">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="eebb2-110">[空間音效](spatial-sound.md)breathes 的生活進入全息的狀態，並提供給我們世界各地。</span><span class="sxs-lookup"><span data-stu-id="eebb2-110">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="eebb2-111">全像投影都是由光線和音效所組成，如果您似乎失去了全息影像，空間音效可以協助您找到它們。</span><span class="sxs-lookup"><span data-stu-id="eebb2-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="eebb2-112">空間音效與您在廣播上聽到的一般音效不一樣，它是位於3D 空間中的音效。</span><span class="sxs-lookup"><span data-stu-id="eebb2-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="eebb2-113">有了空間音效，您就可以讓像是像是您一樣的全像投影，或甚至是您的頭部！</span><span class="sxs-lookup"><span data-stu-id="eebb2-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="eebb2-114">在此課程中，您將會：</span><span class="sxs-lookup"><span data-stu-id="eebb2-114">In this course, you will:</span></span>

* <span data-ttu-id="eebb2-115">設定您的開發環境以使用 Microsoft 空間音效。</span><span class="sxs-lookup"><span data-stu-id="eebb2-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="eebb2-116">使用空間音效來增強互動。</span><span class="sxs-lookup"><span data-stu-id="eebb2-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="eebb2-117">將空間音效與[空間對應](spatial-mapping.md)搭配使用。</span><span class="sxs-lookup"><span data-stu-id="eebb2-117">Use Spatial Sound in conjunction with [Spatial Mapping](spatial-mapping.md).</span></span>
* <span data-ttu-id="eebb2-118">瞭解音效設計和混合最佳作法。</span><span class="sxs-lookup"><span data-stu-id="eebb2-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="eebb2-119">使用音效來增強特殊效果，並將使用者帶入混合現實世界。</span><span class="sxs-lookup"><span data-stu-id="eebb2-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="eebb2-120">裝置支援</span><span class="sxs-lookup"><span data-stu-id="eebb2-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="eebb2-121">粗</span><span class="sxs-lookup"><span data-stu-id="eebb2-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="eebb2-122"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="eebb2-122"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="eebb2-123"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="eebb2-123"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="eebb2-124">MR 空間220：空間音效</span><span class="sxs-lookup"><span data-stu-id="eebb2-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="eebb2-125">✔️</span><span class="sxs-lookup"><span data-stu-id="eebb2-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="eebb2-126">✔️</span><span class="sxs-lookup"><span data-stu-id="eebb2-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="eebb2-127">開始之前</span><span class="sxs-lookup"><span data-stu-id="eebb2-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="eebb2-128">必要條件</span><span class="sxs-lookup"><span data-stu-id="eebb2-128">Prerequisites</span></span>

* <span data-ttu-id="eebb2-129">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="eebb2-129">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="eebb2-130">一些基本C#的程式設計能力。</span><span class="sxs-lookup"><span data-stu-id="eebb2-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="eebb2-131">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="eebb2-131">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="eebb2-132">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="eebb2-132">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="eebb2-133">專案檔案</span><span class="sxs-lookup"><span data-stu-id="eebb2-133">Project files</span></span>

* <span data-ttu-id="eebb2-134">下載專案[所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)檔案。</span><span class="sxs-lookup"><span data-stu-id="eebb2-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="eebb2-135"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="eebb2-135"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="eebb2-136">如果您仍然需要 Unity 5.6 支援，請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="eebb2-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="eebb2-137">此版本可能不再是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="eebb2-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="eebb2-138">如果您仍然需要 Unity 5.5 支援，請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="eebb2-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="eebb2-139"> 此版本可能不再是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="eebb2-139"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="eebb2-140">如果您仍然需要 Unity 5.4 支援，請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="eebb2-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="eebb2-141"> 此版本可能不再是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="eebb2-141"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="eebb2-142">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="eebb2-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="eebb2-143">如果您想要在下載之前查看原始程式碼，可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)取得。</span><span class="sxs-lookup"><span data-stu-id="eebb2-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="eebb2-144">勘誤和注意事項</span><span class="sxs-lookup"><span data-stu-id="eebb2-144">Errata and Notes</span></span>

* <span data-ttu-id="eebb2-145">必須在 Visual Studio 下的 [工具]-[> 選項]-[> 的偵錯工具] 中停用（*取消*核取） [啟用 Just My Code]，才能在程式碼中叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="eebb2-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="eebb2-146">第1章-Unity 設定</span><span class="sxs-lookup"><span data-stu-id="eebb2-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="eebb2-147">目標</span><span class="sxs-lookup"><span data-stu-id="eebb2-147">Objectives</span></span>

* <span data-ttu-id="eebb2-148">將 Unity 的音效設定變更為使用 Microsoft 空間音效。</span><span class="sxs-lookup"><span data-stu-id="eebb2-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="eebb2-149">將3D 音效新增至 Unity 中的物件。</span><span class="sxs-lookup"><span data-stu-id="eebb2-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="eebb2-150">指示</span><span class="sxs-lookup"><span data-stu-id="eebb2-150">Instructions</span></span>

* <span data-ttu-id="eebb2-151">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="eebb2-151">Start Unity.</span></span>
* <span data-ttu-id="eebb2-152">選取 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-152">Select **Open**.</span></span>
* <span data-ttu-id="eebb2-153">流覽至您的桌面，並尋找您先前取消封存的資料夾。</span><span class="sxs-lookup"><span data-stu-id="eebb2-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="eebb2-154">按一下 [ **Starting\Decibel** ] 資料夾，然後按 [**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eebb2-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="eebb2-155">等候專案載入 Unity。</span><span class="sxs-lookup"><span data-stu-id="eebb2-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="eebb2-156">在 [ **專案**] 面板中，開啟**Scenes\Decibel.unity**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="eebb2-157">**在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="eebb2-158">在偵測器中，展開 [ **spatialize** ]，並注意 [沒有**Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="eebb2-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="eebb2-159">根據預設，Unity 不會載入空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="eebb2-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="eebb2-160">下列步驟將會啟用專案中的空間音效。</span><span class="sxs-lookup"><span data-stu-id="eebb2-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="eebb2-161">在 Unity 的頂端功能表中，移至 **編輯 > 專案設定 > 音訊**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="eebb2-162">尋找 [**空間定位器外掛程式**] 下拉式清單，然後選取 [ **MS HRTF 空間定位器**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="eebb2-163">**在 [階層**] 面板中，選取 [ **HologramCollection > P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="eebb2-164">在 [偵測**器**] 面板中，尋找 [**音訊來源**] 元件。</span><span class="sxs-lookup"><span data-stu-id="eebb2-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="eebb2-165">核取 [ **Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="eebb2-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="eebb2-166">將**空間 Blend**滑杆拖曳到**3d**，或在編輯方塊中輸入**1** 。</span><span class="sxs-lookup"><span data-stu-id="eebb2-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="eebb2-167">我們現在會在 Unity 中建立專案，並在 Visual Studio 中設定方案。</span><span class="sxs-lookup"><span data-stu-id="eebb2-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="eebb2-168">在 Unity 中，選取 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="eebb2-169">按一下 [新增] [**開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="eebb2-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="eebb2-170">在 [**平臺**] 清單中選取**通用 Windows 平臺**，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="eebb2-171">如果您是特別針對 HoloLens 進行開發，請將**目標裝置**設定為**hololens**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="eebb2-172">否則，請將它保留在**任何裝置**上。</span><span class="sxs-lookup"><span data-stu-id="eebb2-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="eebb2-173">確定 [**組建類型**] 設定為 [ **D3D** ]，並將 [ **sdk** ] 設定為 [**已安裝最新**版本] （應該是 SDK 16299 或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="eebb2-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="eebb2-174">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-174">Click **Build**.</span></span>
7. <span data-ttu-id="eebb2-175">建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="eebb2-176">按一下 [**應用程式**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="eebb2-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="eebb2-177">按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-177">Press **Select Folder**.</span></span>

<span data-ttu-id="eebb2-178">當 Unity 完成時，將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="eebb2-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="eebb2-179">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="eebb2-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="eebb2-180">開啟 [**分貝] Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="eebb2-181">如果部署至 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="eebb2-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="eebb2-182">使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x86**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="eebb2-183">按一下 [本機電腦] 按鈕旁的下拉式箭號，然後選取 [**遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="eebb2-184">輸入**您的 HoloLens 裝置 IP 位址**，並將驗證模式設定為 **[通用（未加密的通訊協定）** ]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="eebb2-185">按一下 [**選取**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-185">Click **Select**.</span></span> <span data-ttu-id="eebb2-186">如果您不知道您的裝置 IP 位址，請查看 [設定] [ **> Network & Internet] > [Advanced Options**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="eebb2-187">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="eebb2-188">如果這是您第一次部署至您的裝置，您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="eebb2-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="eebb2-189">如果部署到沉浸式耳機：</span><span class="sxs-lookup"><span data-stu-id="eebb2-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="eebb2-190">使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x64**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="eebb2-191">請確定 [部署目標] 設定為 [**本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="eebb2-192">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="eebb2-193">第2章-空間音效和互動</span><span class="sxs-lookup"><span data-stu-id="eebb2-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="eebb2-194">目標</span><span class="sxs-lookup"><span data-stu-id="eebb2-194">Objectives</span></span>

* <span data-ttu-id="eebb2-195">使用音效增強全息影像的真實感。</span><span class="sxs-lookup"><span data-stu-id="eebb2-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="eebb2-196">使用音效引導使用者的注視。</span><span class="sxs-lookup"><span data-stu-id="eebb2-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="eebb2-197">使用音效提供手勢意見反應。</span><span class="sxs-lookup"><span data-stu-id="eebb2-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="eebb2-198">第1部分-增強真實性</span><span class="sxs-lookup"><span data-stu-id="eebb2-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="eebb2-199">重要概念</span><span class="sxs-lookup"><span data-stu-id="eebb2-199">Key Concepts</span></span>

* <span data-ttu-id="eebb2-200">Spatialize 的全息影像音效。</span><span class="sxs-lookup"><span data-stu-id="eebb2-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="eebb2-201">音效來源應該放在全息影像上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="eebb2-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="eebb2-202">音效的適當位置將取決於全息影像。</span><span class="sxs-lookup"><span data-stu-id="eebb2-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="eebb2-203">例如，如果全像是人類的全息圖，則音效來源應該位於嘴附近，而不是腳。</span><span class="sxs-lookup"><span data-stu-id="eebb2-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="eebb2-204">指示</span><span class="sxs-lookup"><span data-stu-id="eebb2-204">Instructions</span></span>

<span data-ttu-id="eebb2-205">下列指示會將 hrtf 音效附加至全息影像。</span><span class="sxs-lookup"><span data-stu-id="eebb2-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="eebb2-206">**在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="eebb2-207">在 [偵測**器**] 面板的 [ **spatialize**] 中，按一下 [ **AudioClip** ] 旁邊的圓形，然後從快顯視窗中選取 [ **PolyHover** ]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="eebb2-208">按一下 [**輸出**] 旁的圓形，然後從快顯視窗中選取 [ **SoundEffects** ]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="eebb2-209">Project 分貝會使用 Unity **AudioMixer**元件，為音效群組啟用調整聲音層級。</span><span class="sxs-lookup"><span data-stu-id="eebb2-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="eebb2-210">藉由以這種方式將聲音分組，可以調整整體磁片區，同時維持每個音效的相對量。</span><span class="sxs-lookup"><span data-stu-id="eebb2-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="eebb2-211">在**spatialize**中，展開 [ **3d 音效設定**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="eebb2-212">將 [ **Doppler 層級**] 設定為**0**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="eebb2-213">將 Doppler 層級設定為零會停用移動（全像是全息或使用者）所造成的音調變更。</span><span class="sxs-lookup"><span data-stu-id="eebb2-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="eebb2-214">Doppler 的典型範例是快速移動的汽車。</span><span class="sxs-lookup"><span data-stu-id="eebb2-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="eebb2-215">隨著汽車接近固定的接聽程式，引擎的音調也會上升。</span><span class="sxs-lookup"><span data-stu-id="eebb2-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="eebb2-216">當它通過接聽程式時，音調就會減少與距離。</span><span class="sxs-lookup"><span data-stu-id="eebb2-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="eebb2-217">第2部分-引導使用者的注視</span><span class="sxs-lookup"><span data-stu-id="eebb2-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="eebb2-218">重要概念</span><span class="sxs-lookup"><span data-stu-id="eebb2-218">Key Concepts</span></span>

* <span data-ttu-id="eebb2-219">使用音效來留意重要的全息影像。</span><span class="sxs-lookup"><span data-stu-id="eebb2-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="eebb2-220">此耳可協助引導眼睛的外觀。</span><span class="sxs-lookup"><span data-stu-id="eebb2-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="eebb2-221">大腦有一些學習的預期。</span><span class="sxs-lookup"><span data-stu-id="eebb2-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="eebb2-222">學習預期的一個範例是，鳥瞰通常在人類的正上方。</span><span class="sxs-lookup"><span data-stu-id="eebb2-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="eebb2-223">如果使用者聽到鳥瞰聲，其初始反應就是查閱。</span><span class="sxs-lookup"><span data-stu-id="eebb2-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="eebb2-224">將鳥瞰圖放在使用者下方，會導致他們以正確的音效方向呈現，但無法根據預期的查詢來尋找全息。</span><span class="sxs-lookup"><span data-stu-id="eebb2-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="eebb2-225">指示</span><span class="sxs-lookup"><span data-stu-id="eebb2-225">Instructions</span></span>

<span data-ttu-id="eebb2-226">下列指示可讓 P0LY 隱藏在您的後方，讓您可以使用音效來尋找全息的全像投影。</span><span class="sxs-lookup"><span data-stu-id="eebb2-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="eebb2-227">**在 [階層**] 面板中，選取 [**管理員**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="eebb2-228">在 [偵測**器**] 面板中，尋找 [**語音輸入處理常式**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="eebb2-229">在 [**語音輸入處理常式**] 中，展開 [**移至隱藏**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="eebb2-230">將**No Function**變更為**PolyActions. GoHide**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![關鍵字：移至隱藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="eebb2-232">第3部分-手勢意見反應</span><span class="sxs-lookup"><span data-stu-id="eebb2-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="eebb2-233">重要概念</span><span class="sxs-lookup"><span data-stu-id="eebb2-233">Key Concepts</span></span>

* <span data-ttu-id="eebb2-234">為使用者提供使用音效的正面手勢確認</span><span class="sxs-lookup"><span data-stu-id="eebb2-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="eebb2-235">不要讓使用者過於塞滿的音效</span><span class="sxs-lookup"><span data-stu-id="eebb2-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="eebb2-236">微妙音效的效果最佳-不要失色經驗</span><span class="sxs-lookup"><span data-stu-id="eebb2-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="eebb2-237">指示</span><span class="sxs-lookup"><span data-stu-id="eebb2-237">Instructions</span></span>

* <span data-ttu-id="eebb2-238">**在 [階層**] 面板中，展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="eebb2-239">展開 [ **EnergyHub** ]，然後選取 [**基底**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="eebb2-240">在 [偵測**器**] 面板中，按一下 [**加入元件**]，然後加入**手勢音效處理常式**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="eebb2-241">在 [**手勢音效處理常式**] 中，按一下 [**導覽已啟動的剪輯**] 和 [**導覽已更新剪輯**] 旁的圓形，然後從這兩者的快顯視窗選取 [ **RotateClick** ]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="eebb2-242">按兩下 [GestureSoundHandler] 以載入 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="eebb2-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="eebb2-243">手勢音效處理常式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="eebb2-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="eebb2-244">建立和設定**spatialize**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="eebb2-245">將**spatialize**放在適當**GameObject**的位置。</span><span class="sxs-lookup"><span data-stu-id="eebb2-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="eebb2-246">播放與手勢相關聯的**AudioClip** 。</span><span class="sxs-lookup"><span data-stu-id="eebb2-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="eebb2-247">組建和部署</span><span class="sxs-lookup"><span data-stu-id="eebb2-247">Build and Deploy</span></span>

1. <span data-ttu-id="eebb2-248">在 Unity 中，選取 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="eebb2-249">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-249">Click **Build**.</span></span>
3. <span data-ttu-id="eebb2-250">按一下 [**應用程式**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="eebb2-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="eebb2-251">按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-251">Press **Select Folder**.</span></span>

<span data-ttu-id="eebb2-252">檢查工具列是否顯示 [發行]、[x86] 或 [x64]，以及 [遠端裝置]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="eebb2-253">如果不是，這就是 Visual Studio 的程式碼實例。</span><span class="sxs-lookup"><span data-stu-id="eebb2-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="eebb2-254">您可能需要從應用程式資料夾重新開啟解決方案。</span><span class="sxs-lookup"><span data-stu-id="eebb2-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="eebb2-255">如果出現提示，請重載專案檔案。</span><span class="sxs-lookup"><span data-stu-id="eebb2-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="eebb2-256">同樣地，從 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="eebb2-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="eebb2-257">部署應用程式之後：</span><span class="sxs-lookup"><span data-stu-id="eebb2-257">After the application is deployed:</span></span>

* <span data-ttu-id="eebb2-258">觀察當您在 P0LY 四處移動時，音效如何改變。</span><span class="sxs-lookup"><span data-stu-id="eebb2-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="eebb2-259">說「 *Go Hide* 」，讓 P0LY 移到您背後的位置。</span><span class="sxs-lookup"><span data-stu-id="eebb2-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="eebb2-260">依音效尋找。</span><span class="sxs-lookup"><span data-stu-id="eebb2-260">Find it by the sound.</span></span>
* <span data-ttu-id="eebb2-261">看著能源中樞的基礎。</span><span class="sxs-lookup"><span data-stu-id="eebb2-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="eebb2-262">請按住滑鼠左鍵並向左或向右拖曳以旋轉全像投影，並注意按一下音效如何確認手勢。</span><span class="sxs-lookup"><span data-stu-id="eebb2-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="eebb2-263">注意：有一個會與您一起標記的文字面板。</span><span class="sxs-lookup"><span data-stu-id="eebb2-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="eebb2-264">這會包含可供您在本課程中使用的語音命令。</span><span class="sxs-lookup"><span data-stu-id="eebb2-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="eebb2-265">第3章-空間音效和空間對應</span><span class="sxs-lookup"><span data-stu-id="eebb2-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="eebb2-266">目標</span><span class="sxs-lookup"><span data-stu-id="eebb2-266">Objectives</span></span>

* <span data-ttu-id="eebb2-267">使用音效確認全息影像與真實世界之間的互動。</span><span class="sxs-lookup"><span data-stu-id="eebb2-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="eebb2-268">使用實體世界遮蔽音效。</span><span class="sxs-lookup"><span data-stu-id="eebb2-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="eebb2-269">第1部分-實體世界互動</span><span class="sxs-lookup"><span data-stu-id="eebb2-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="eebb2-270">重要概念</span><span class="sxs-lookup"><span data-stu-id="eebb2-270">Key Concepts</span></span>

* <span data-ttu-id="eebb2-271">當遇到表面或另一個物件時，實體物件通常會發出音效。</span><span class="sxs-lookup"><span data-stu-id="eebb2-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="eebb2-272">音效在體驗中應該是適當的內容。</span><span class="sxs-lookup"><span data-stu-id="eebb2-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="eebb2-273">例如，在資料表上設定杯時，應該會比在金屬片上卸載科羅拉多，讓音效更為安靜。</span><span class="sxs-lookup"><span data-stu-id="eebb2-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="eebb2-274">指示</span><span class="sxs-lookup"><span data-stu-id="eebb2-274">Instructions</span></span>

* <span data-ttu-id="eebb2-275">**在 [階層**] 面板中，展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="eebb2-276">展開 [ **EnergyHub**]，選取 [**基底**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="eebb2-277">在 [偵測**器**] 面板中，按一下 [**新增元件**]，然後新增 **[使用音效和動作來放置**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="eebb2-278">**使用音效和動作來放置**：</span><span class="sxs-lookup"><span data-stu-id="eebb2-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="eebb2-279">勾選 **[將父系放在點上**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="eebb2-280">將**放置音效**設定為 [**放置**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="eebb2-281">將**Pickup 音效**設定為**取貨**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="eebb2-282">**在 [取貨動作**] 和 [**放置] 動作上**，按右下方的 [+]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="eebb2-283">將 [EnergyHub] 從場景拖曳至 [**無] （物件）** 欄位。</span><span class="sxs-lookup"><span data-stu-id="eebb2-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="eebb2-284">在 [**收取取貨動作**] 下，按一下 [ **No Function** -> **EnergyHubBase** -> **ResetAnimation**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="eebb2-285">在 **放置動作** 底下，按一下 **沒有**函式 -> **EnergyHubBase** -> **OnSelect**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![利用音效和動作來放置](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="eebb2-287">第2部分-音效遮蔽</span><span class="sxs-lookup"><span data-stu-id="eebb2-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="eebb2-288">重要概念</span><span class="sxs-lookup"><span data-stu-id="eebb2-288">Key Concepts</span></span>

* <span data-ttu-id="eebb2-289">音效（如 light）可以 pixels occluded。</span><span class="sxs-lookup"><span data-stu-id="eebb2-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="eebb2-290">典型的範例是音樂會廳。</span><span class="sxs-lookup"><span data-stu-id="eebb2-290">A classic example is a concert hall.</span></span> <span data-ttu-id="eebb2-291">當接聽程式離開大廳外，而門已關閉時，音樂會 muffled。</span><span class="sxs-lookup"><span data-stu-id="eebb2-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="eebb2-292">一般來說，磁片區也會減少。</span><span class="sxs-lookup"><span data-stu-id="eebb2-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="eebb2-293">當門開啟時，會在實際音量聽到音效的完整範圍。</span><span class="sxs-lookup"><span data-stu-id="eebb2-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="eebb2-294">高頻率的音效通常會吸收超過低頻率。</span><span class="sxs-lookup"><span data-stu-id="eebb2-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="eebb2-295">指示</span><span class="sxs-lookup"><span data-stu-id="eebb2-295">Instructions</span></span>

* <span data-ttu-id="eebb2-296">**在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="eebb2-297">在 [偵測**器**] 面板中，按一下 [**新增元件**] 並新增**音訊發射器**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="eebb2-298">音訊發射器類別提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="eebb2-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="eebb2-299">還原**spatialize**磁片區的任何變更。</span><span class="sxs-lookup"><span data-stu-id="eebb2-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="eebb2-300">以附加**AudioEmitter**的**GameObject**方向，從使用者的位置執行**RaycastNonAlloc** 。</span><span class="sxs-lookup"><span data-stu-id="eebb2-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="eebb2-301">RaycastNonAlloc 方法是用來做為效能優化，以限制配置以及傳回的結果數目。</span><span class="sxs-lookup"><span data-stu-id="eebb2-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="eebb2-302">針對每個遇到的**IAudioInfluencer** ，會呼叫**ApplyEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="eebb2-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="eebb2-303">對於不再遇到的每個先前**IAudioInfluencer** ，請呼叫**RemoveEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="eebb2-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="eebb2-304">請注意，AudioEmitter 會更新人力時間規模，而不是每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="eebb2-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="eebb2-305">這樣做的原因是，人們通常無法快速地進行更新，而需要比每個季或半秒的頻率更高。</span><span class="sxs-lookup"><span data-stu-id="eebb2-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="eebb2-306">從一個位置快速傳送到另一個位置的全息影像，可能會破壞夢想。</span><span class="sxs-lookup"><span data-stu-id="eebb2-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="eebb2-307">**在 [階層**] 面板中，展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="eebb2-308">展開 [ **EnergyHub** ]，然後選取 [ **BlobOutside**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="eebb2-309">在 [偵測**器**] 面板中，按一下 [**新增元件**] 並新增**音訊 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="eebb2-310">在 [**音訊 Occluder**] 中，將 [**截止頻率**] 設定為**1500**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="eebb2-311">此設定會將 Spatialize 頻率限制為 1500 Hz 和以下。</span><span class="sxs-lookup"><span data-stu-id="eebb2-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="eebb2-312">將**磁片區傳遞**至**0.9**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="eebb2-313">此設定會將 Spatialize 的數量減少到其目前層級的90%。</span><span class="sxs-lookup"><span data-stu-id="eebb2-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="eebb2-314">音訊 Occluder 會將 IAudioInfluencer 實作為：</span><span class="sxs-lookup"><span data-stu-id="eebb2-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="eebb2-315">使用附加至**spatialize**受控購買**AudioEmitter**的**AudioLowPassFilter**來套用遮蔽效果。</span><span class="sxs-lookup"><span data-stu-id="eebb2-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="eebb2-316">將磁片區衰減套用至 Spatialize。</span><span class="sxs-lookup"><span data-stu-id="eebb2-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="eebb2-317">藉由設定中性的截止頻率並停用篩選來停用效果。</span><span class="sxs-lookup"><span data-stu-id="eebb2-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="eebb2-318">用為中性的頻率是 22 kHz （22000 Hz）。</span><span class="sxs-lookup"><span data-stu-id="eebb2-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="eebb2-319">選擇此頻率的原因，是因為它高於人耳可聽到的名義最大頻率，所以不會對音效造成明顯影響。</span><span class="sxs-lookup"><span data-stu-id="eebb2-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="eebb2-320">**在 [階層**] 面板中，選取 [ **SpatialMapping**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="eebb2-321">在 [偵測**器**] 面板中，按一下 [**新增元件**] 並新增**音訊 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="eebb2-322">在 [**音訊 Occluder**] 中，將 [**截止頻率**] 設定為**750**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="eebb2-323">當使用者和**AudioEmitter**之間的路徑中有多個阻隔器時，會將最低頻率套用至篩選準則。</span><span class="sxs-lookup"><span data-stu-id="eebb2-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="eebb2-324">將**磁片區傳遞**至**0.75**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="eebb2-325">當使用者和**AudioEmitter**之間的路徑中有多個阻隔器時，就會套用 additively 的磁片區。</span><span class="sxs-lookup"><span data-stu-id="eebb2-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="eebb2-326">**在 [階層**] 面板中，選取 [**管理員**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="eebb2-327">在 [偵測**器**] 面板中，展開 [**語音輸入處理常式**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="eebb2-328">在 [**語音輸入處理常式**] 中，展開 [**繼續收費**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="eebb2-329">將**No Function**變更為**PolyActions. GoCharge**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![關鍵字： Go 費用](images/gocharge.png)

* <span data-ttu-id="eebb2-331">依序展開 [前往**這裡**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="eebb2-332">將**No Function**變更為**PolyActions. 撰寫復活**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![關鍵字：在這裡](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="eebb2-334">組建和部署</span><span class="sxs-lookup"><span data-stu-id="eebb2-334">Build and Deploy</span></span>

* <span data-ttu-id="eebb2-335">如先前一樣，在 Unity 中建立專案，並在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="eebb2-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="eebb2-336">部署應用程式之後：</span><span class="sxs-lookup"><span data-stu-id="eebb2-336">After the application is deployed:</span></span>

* <span data-ttu-id="eebb2-337">說「*繼續收費*」，讓 P0LY 進入能源中樞。</span><span class="sxs-lookup"><span data-stu-id="eebb2-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="eebb2-338">請注意音效中的變更。</span><span class="sxs-lookup"><span data-stu-id="eebb2-338">Note the change in the sound.</span></span> <span data-ttu-id="eebb2-339">它應該聽起來 muffled，而且有點安靜。</span><span class="sxs-lookup"><span data-stu-id="eebb2-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="eebb2-340">如果您可以在您和能源中樞之間定位自己的牆或其他物件，您應該會注意到因為真實世界遮蔽，而 muffling 的音效。</span><span class="sxs-lookup"><span data-stu-id="eebb2-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="eebb2-341">說「*在這裡*」，讓 P0LY 離開能源中樞，並將其本身放在您的前方。</span><span class="sxs-lookup"><span data-stu-id="eebb2-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="eebb2-342">請注意，P0LY 結束能源中樞後，就會移除音效遮蔽。</span><span class="sxs-lookup"><span data-stu-id="eebb2-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="eebb2-343">如果您仍然聽到遮蔽，P0LY 可能會受到真實世界的 pixels occluded。</span><span class="sxs-lookup"><span data-stu-id="eebb2-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="eebb2-344">請嘗試移動以確保您有清楚的 P0LY。</span><span class="sxs-lookup"><span data-stu-id="eebb2-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="eebb2-345">第3部分-會議室模型</span><span class="sxs-lookup"><span data-stu-id="eebb2-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="eebb2-346">重要概念</span><span class="sxs-lookup"><span data-stu-id="eebb2-346">Key Concepts</span></span>

* <span data-ttu-id="eebb2-347">空間的大小會提供 subliminal 的佇列，以做出音效當地語系化。</span><span class="sxs-lookup"><span data-stu-id="eebb2-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="eebb2-348">會議室模型是依**spatialize**設定。</span><span class="sxs-lookup"><span data-stu-id="eebb2-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="eebb2-349">[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供設定房間模型的程式碼。</span><span class="sxs-lookup"><span data-stu-id="eebb2-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="eebb2-350">針對混合現實體驗，請選取最適合真實世界空間的房間模型。</span><span class="sxs-lookup"><span data-stu-id="eebb2-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="eebb2-351">如果您要建立虛擬實境案例，請選取最適合虛擬環境的房間模型。</span><span class="sxs-lookup"><span data-stu-id="eebb2-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="eebb2-352">第4章-音效設計</span><span class="sxs-lookup"><span data-stu-id="eebb2-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="eebb2-353">目標</span><span class="sxs-lookup"><span data-stu-id="eebb2-353">Objectives</span></span>

* <span data-ttu-id="eebb2-354">瞭解有效音效設計的考慮。</span><span class="sxs-lookup"><span data-stu-id="eebb2-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="eebb2-355">瞭解混合技術和指導方針。</span><span class="sxs-lookup"><span data-stu-id="eebb2-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="eebb2-356">第1部分-音效和體驗設計</span><span class="sxs-lookup"><span data-stu-id="eebb2-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="eebb2-357">本節討論主要音效和體驗設計考慮和指導方針。</span><span class="sxs-lookup"><span data-stu-id="eebb2-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="eebb2-358">標準化所有聲音</span><span class="sxs-lookup"><span data-stu-id="eebb2-358">Normalize all sounds</span></span>

<span data-ttu-id="eebb2-359">如此一來，就不需要特殊的案常式序代碼來調整每個音效的音量層級，這可能相當耗時，而且會限制輕鬆更新音效檔的能力。</span><span class="sxs-lookup"><span data-stu-id="eebb2-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="eebb2-360">非網路共用體驗的設計</span><span class="sxs-lookup"><span data-stu-id="eebb2-360">Design for an untethered experience</span></span>

<span data-ttu-id="eebb2-361">HoloLens 是完全獨立的非網路共用全像攝影電腦。</span><span class="sxs-lookup"><span data-stu-id="eebb2-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="eebb2-362">您的使用者可以和將會在移動時使用您的體驗。</span><span class="sxs-lookup"><span data-stu-id="eebb2-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="eebb2-363">請務必四處流覽來測試您的音訊混合。</span><span class="sxs-lookup"><span data-stu-id="eebb2-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="eebb2-364">從您的全息影像上的邏輯位置發出音效</span><span class="sxs-lookup"><span data-stu-id="eebb2-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="eebb2-365">在真實世界中，狗不會從結尾處吠，而且人類的語音也不會來自其腳。</span><span class="sxs-lookup"><span data-stu-id="eebb2-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="eebb2-366">避免在您的全息影像未預期的部分發出聲音。</span><span class="sxs-lookup"><span data-stu-id="eebb2-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="eebb2-367">對於小型的全息影像，從幾何中心開始音效是合理的。</span><span class="sxs-lookup"><span data-stu-id="eebb2-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="eebb2-368">熟悉的音效是最能當地語系化的</span><span class="sxs-lookup"><span data-stu-id="eebb2-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="eebb2-369">人類語音和音樂很容易當地語系化。</span><span class="sxs-lookup"><span data-stu-id="eebb2-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="eebb2-370">如果有人撥打您的名字，您就能夠非常準確地判斷語音的方向和距離。</span><span class="sxs-lookup"><span data-stu-id="eebb2-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="eebb2-371">簡言之，不熟悉的音效很難當地語系化。</span><span class="sxs-lookup"><span data-stu-id="eebb2-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="eebb2-372">使用者期望的 cognizant</span><span class="sxs-lookup"><span data-stu-id="eebb2-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="eebb2-373">生命體驗在我們識別音效位置的功能中扮演了部分。</span><span class="sxs-lookup"><span data-stu-id="eebb2-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="eebb2-374">這就是為什麼人類語音特別容易當地語系化的原因之一。</span><span class="sxs-lookup"><span data-stu-id="eebb2-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="eebb2-375">請務必留意您的使用者在放置音效時所學到的預期。</span><span class="sxs-lookup"><span data-stu-id="eebb2-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="eebb2-376">比方說，當有人聽到一則一般會查詢的「鳥」歌曲時，因為鳥傾向于觀察線上（飛行或在樹狀結構中）。</span><span class="sxs-lookup"><span data-stu-id="eebb2-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="eebb2-377">使用者不常以正確的音效方向開啟，而是在找不到任何一種垂直方向，並在無法找到全息的情況下感到困惑或挫折。</span><span class="sxs-lookup"><span data-stu-id="eebb2-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="eebb2-378">避免隱藏的發射器</span><span class="sxs-lookup"><span data-stu-id="eebb2-378">Avoid hidden emitters</span></span>

<span data-ttu-id="eebb2-379">在真實世界中，如果聽到音效，我們通常可以識別發出音效的物件。</span><span class="sxs-lookup"><span data-stu-id="eebb2-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="eebb2-380">這也應該在您的經驗中成立。</span><span class="sxs-lookup"><span data-stu-id="eebb2-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="eebb2-381">這可能非常令人不安，讓使用者聽到音效，知道聲音源自何處，而無法看到物件。</span><span class="sxs-lookup"><span data-stu-id="eebb2-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="eebb2-382">此指導方針有一些例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eebb2-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="eebb2-383">例如，欄位中的環境音效（例如 crickets）不需要是可見的。</span><span class="sxs-lookup"><span data-stu-id="eebb2-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="eebb2-384">生活經驗讓我們熟悉這些音效的來源，而不需要看到它。</span><span class="sxs-lookup"><span data-stu-id="eebb2-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="eebb2-385">第2部分-音效混合</span><span class="sxs-lookup"><span data-stu-id="eebb2-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="eebb2-386">將您的混合目標設為 HoloLens 上的70% 磁片區</span><span class="sxs-lookup"><span data-stu-id="eebb2-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="eebb2-387">混合現實體驗允許在真實世界中看到全息影像。</span><span class="sxs-lookup"><span data-stu-id="eebb2-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="eebb2-388">他們也應該能夠聽到真實世界的聲音。</span><span class="sxs-lookup"><span data-stu-id="eebb2-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="eebb2-389">70% 的磁片區目標可讓使用者在世界各地聆聽他們，並附上您的體驗。</span><span class="sxs-lookup"><span data-stu-id="eebb2-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="eebb2-390">100% 磁片區上的 HoloLens 應下拉式清單外部聲音</span><span class="sxs-lookup"><span data-stu-id="eebb2-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="eebb2-391">磁片區層級100% 類似于虛擬實境體驗。</span><span class="sxs-lookup"><span data-stu-id="eebb2-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="eebb2-392">使用者會以視覺化方式傳輸到不同的世界。</span><span class="sxs-lookup"><span data-stu-id="eebb2-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="eebb2-393">同樣的情況也應該保留 true 語音。</span><span class="sxs-lookup"><span data-stu-id="eebb2-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="eebb2-394">使用 Unity AudioMixer 來調整音效的類別</span><span class="sxs-lookup"><span data-stu-id="eebb2-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="eebb2-395">設計混合時，建立音效類別並能夠以一個單位來增加或減少其音量，通常會很有説明。</span><span class="sxs-lookup"><span data-stu-id="eebb2-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="eebb2-396">這會保留每個音效的相對層級，同時讓整體混合的快速且輕鬆地進行變更。</span><span class="sxs-lookup"><span data-stu-id="eebb2-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="eebb2-397">常見的類別包括：聲音效果、環境、語音轉移和背景音樂。</span><span class="sxs-lookup"><span data-stu-id="eebb2-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="eebb2-398">根據使用者的注視來混合聲音</span><span class="sxs-lookup"><span data-stu-id="eebb2-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="eebb2-399">根據使用者的所在位置（或不是）來變更您的體驗，通常會很有用。</span><span class="sxs-lookup"><span data-stu-id="eebb2-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="eebb2-400">這項技術的其中一個常見用途是減少全像攝影畫面外的全息影像音量，讓使用者更容易專注于他們前面的資訊。</span><span class="sxs-lookup"><span data-stu-id="eebb2-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="eebb2-401">另一種用途是增加音效的音量，將使用者的注意力吸引到重要的事件。</span><span class="sxs-lookup"><span data-stu-id="eebb2-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="eebb2-402">打造您的混合</span><span class="sxs-lookup"><span data-stu-id="eebb2-402">Building your mix</span></span>

<span data-ttu-id="eebb2-403">建立混合時，建議您從體驗的背景音訊開始，並根據重要性新增圖層。</span><span class="sxs-lookup"><span data-stu-id="eebb2-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="eebb2-404">通常，這會導致每個圖層都比先前的還要大。</span><span class="sxs-lookup"><span data-stu-id="eebb2-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="eebb2-405">將您的混合想像為反向漏斗圖，其底部最重要的（通常是 quietest 音效），建議您將混合結構與下圖類似。</span><span class="sxs-lookup"><span data-stu-id="eebb2-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![音效混合結構](images/soundlevels.png)

<span data-ttu-id="eebb2-407">語音轉移是一種有趣的案例。</span><span class="sxs-lookup"><span data-stu-id="eebb2-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="eebb2-408">根據您所建立的經驗，您可能會想要有身歷聲（非當地語系化）音效或 spatialize 語音轉移。</span><span class="sxs-lookup"><span data-stu-id="eebb2-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="eebb2-409">兩個 Microsoft 發佈的體驗說明每個案例的絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="eebb2-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="eebb2-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87)使用身歷聲聲音。</span><span class="sxs-lookup"><span data-stu-id="eebb2-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="eebb2-411">當朗讀程式描述要查看的位置時，音效會一致，而且不會因使用者的位置而有所不同。</span><span class="sxs-lookup"><span data-stu-id="eebb2-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="eebb2-412">這可讓 [朗讀程式] 描述場景，而不需要離開環境的 hrtf 音效。</span><span class="sxs-lookup"><span data-stu-id="eebb2-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="eebb2-413">[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)會以偵探的形式利用 hrtf 的聲音。</span><span class="sxs-lookup"><span data-stu-id="eebb2-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="eebb2-414">此偵探的語音是用來協助讓使用者注意到重要的線索，就好像實際的人在聊天室一樣。</span><span class="sxs-lookup"><span data-stu-id="eebb2-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="eebb2-415">這可讓您更瞭解深度解決神秘的經驗。</span><span class="sxs-lookup"><span data-stu-id="eebb2-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="eebb2-416">第3部分-效能</span><span class="sxs-lookup"><span data-stu-id="eebb2-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="eebb2-417">CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="eebb2-417">CPU usage</span></span>

<span data-ttu-id="eebb2-418">使用空間音效時，10-12 發射器會耗用大約12% 的 CPU。</span><span class="sxs-lookup"><span data-stu-id="eebb2-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="eebb2-419">串流長音訊檔案</span><span class="sxs-lookup"><span data-stu-id="eebb2-419">Stream long audio files</span></span>

<span data-ttu-id="eebb2-420">音訊資料可能很大，尤其是常見的取樣率（44.1 和 48 kHz）。</span><span class="sxs-lookup"><span data-stu-id="eebb2-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="eebb2-421">一般的規則是，應串流處理長度超過 5-10 秒的音訊檔案，以減少應用程式記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="eebb2-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="eebb2-422">在 Unity 中，您可以在檔案的匯入設定中，標示要串流處理的音訊檔案。</span><span class="sxs-lookup"><span data-stu-id="eebb2-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![音訊匯入設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="eebb2-424">第5章-特殊效果</span><span class="sxs-lookup"><span data-stu-id="eebb2-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="eebb2-425">目標</span><span class="sxs-lookup"><span data-stu-id="eebb2-425">Objectives</span></span>

* <span data-ttu-id="eebb2-426">將深度新增至「魔術視窗」。</span><span class="sxs-lookup"><span data-stu-id="eebb2-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="eebb2-427">將使用者帶到虛擬世界。</span><span class="sxs-lookup"><span data-stu-id="eebb2-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="eebb2-428">魔術視窗</span><span class="sxs-lookup"><span data-stu-id="eebb2-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="eebb2-429">重要概念</span><span class="sxs-lookup"><span data-stu-id="eebb2-429">Key Concepts</span></span>

* <span data-ttu-id="eebb2-430">在隱藏的世界中建立視圖，視覺上具吸引力。</span><span class="sxs-lookup"><span data-stu-id="eebb2-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="eebb2-431">當全息影像或使用者接近隱藏世界時，新增音訊效果，以增強真實性。</span><span class="sxs-lookup"><span data-stu-id="eebb2-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="eebb2-432">指示</span><span class="sxs-lookup"><span data-stu-id="eebb2-432">Instructions</span></span>

* <span data-ttu-id="eebb2-433">**在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **Underworld**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="eebb2-434">展開 [ **Underworld** ]，然後選取 [ **VoiceSource**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="eebb2-435">在 [偵測**器**] 面板中，按一下 [**新增元件**] 並新增 [**使用者聲音效果**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="eebb2-436">**Spatialize**元件將會新增至**VoiceSource**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="eebb2-437">在**spatialize**中，將 [**輸出**] 設定為 **[UserVoice （混音器）** ]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="eebb2-438">核取 [ **Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="eebb2-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="eebb2-439">將**空間 Blend**滑杆拖曳到**3d**，或在編輯方塊中輸入**1** 。</span><span class="sxs-lookup"><span data-stu-id="eebb2-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="eebb2-440">展開 [ **3D 音效設定**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="eebb2-441">將 [ **Doppler 層級**] 設定為**0**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="eebb2-442">在 [**使用者聲音效果**] 中，將**父物件**從場景設定為**Underworld** 。</span><span class="sxs-lookup"><span data-stu-id="eebb2-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="eebb2-443">將 [**最大距離**] 設定為**1**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="eebb2-444">設定 [**最大距離**] 可讓使用者在啟用效果之前，先關閉使用者必須前往父物件的**聲音效果**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="eebb2-445">在 [**使用者語音效果**] 中，展開 [**一首哀歌參數**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="eebb2-446">將**深度**設定為**0.1**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="eebb2-447">設定**一下1個磁片**區，再按2個**音量**，然後將**3 個磁片**區帶到**0.8**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="eebb2-448">將 [**原始音效磁片**區] 設定為**0.5**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="eebb2-449">先前的設定會設定 Unity **AudioChorusFilter**的參數，用來將豐富的語音新增至使用者的聲音。</span><span class="sxs-lookup"><span data-stu-id="eebb2-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="eebb2-450">在 [**使用者語音效果**] 中，展開 [ **Echo 參數**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="eebb2-451">將**延遲**設定為**300**</span><span class="sxs-lookup"><span data-stu-id="eebb2-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="eebb2-452">將 [**衰減比例**] 設定為**0.2**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="eebb2-453">將 [**原始音效音量**] 設定為**0**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="eebb2-454">先前的設定會設定用來讓使用者的語音回應的 Unity **AudioEchoFilter**參數。</span><span class="sxs-lookup"><span data-stu-id="eebb2-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="eebb2-455">使用者聲音效果腳本會負責：</span><span class="sxs-lookup"><span data-stu-id="eebb2-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="eebb2-456">測量使用者與附加腳本的**GameObject**之間的距離。</span><span class="sxs-lookup"><span data-stu-id="eebb2-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="eebb2-457">判斷使用者是否面臨**GameObject**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="eebb2-458">無論距離為何，使用者都必須面對 GameObject，才會啟用效果。</span><span class="sxs-lookup"><span data-stu-id="eebb2-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="eebb2-459">對**spatialize**套用和設定**AudioChorusFilter**和**AudioEchoFilter** 。</span><span class="sxs-lookup"><span data-stu-id="eebb2-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="eebb2-460">停用篩選來停用效果。</span><span class="sxs-lookup"><span data-stu-id="eebb2-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="eebb2-461">使用者語音效果使用 Mic 串流選取器元件（來自[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)）來選取高品質的語音串流，並將其路由傳送到 Unity 的音訊系統。</span><span class="sxs-lookup"><span data-stu-id="eebb2-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="eebb2-462">**在 [階層**] 面板中，選取 [**管理員**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="eebb2-463">在 [偵測**器**] 面板中，展開 [**語音輸入處理常式**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="eebb2-464">在 [**語音輸入處理常式**] 中，展開 [**顯示 Underworld**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="eebb2-465">將**No Function**變更為**UnderworldBase. OnEnable**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![關鍵字：顯示 Underworld](images/showunderworld.png)

* <span data-ttu-id="eebb2-467">展開 [**隱藏 Underworld**]。</span><span class="sxs-lookup"><span data-stu-id="eebb2-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="eebb2-468">將**No Function**變更為**UnderworldBase. OnDisable**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![關鍵字：隱藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="eebb2-470">組建和部署</span><span class="sxs-lookup"><span data-stu-id="eebb2-470">Build and Deploy</span></span>

* <span data-ttu-id="eebb2-471">如先前一樣，在 Unity 中建立專案，並在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="eebb2-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="eebb2-472">部署應用程式之後：</span><span class="sxs-lookup"><span data-stu-id="eebb2-472">After the application is deployed:</span></span>

* <span data-ttu-id="eebb2-473">臉部表面（牆、樓層、桌子），並說出「 *Show Underworld*」。</span><span class="sxs-lookup"><span data-stu-id="eebb2-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="eebb2-474">將會顯示 underworld，並隱藏所有其他的全息影像。</span><span class="sxs-lookup"><span data-stu-id="eebb2-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="eebb2-475">如果您看不到 underworld，請確定您面臨的是真實世界的表面。</span><span class="sxs-lookup"><span data-stu-id="eebb2-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="eebb2-476">一種 underworld 的全像投影，並開始談。</span><span class="sxs-lookup"><span data-stu-id="eebb2-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="eebb2-477">音訊效果現已套用至您的語音！</span><span class="sxs-lookup"><span data-stu-id="eebb2-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="eebb2-478">關閉 underworld，並留意效果不再套用的方式。</span><span class="sxs-lookup"><span data-stu-id="eebb2-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="eebb2-479">說「*隱藏 Underworld* 」以隱藏 Underworld。</span><span class="sxs-lookup"><span data-stu-id="eebb2-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="eebb2-480">Underworld 將會隱藏，而先前隱藏的全息影像將會重新出現。</span><span class="sxs-lookup"><span data-stu-id="eebb2-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="eebb2-481">結束</span><span class="sxs-lookup"><span data-stu-id="eebb2-481">The End</span></span>

<span data-ttu-id="eebb2-482">恭喜！</span><span class="sxs-lookup"><span data-stu-id="eebb2-482">Congratulations!</span></span> <span data-ttu-id="eebb2-483">您現在已完成**MR 空間220：空間音效**。</span><span class="sxs-lookup"><span data-stu-id="eebb2-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="eebb2-484">收聽世界，讓您的經驗實現音效！</span><span class="sxs-lookup"><span data-stu-id="eebb2-484">Listen to the world and bring your experiences to life with sound!</span></span>
