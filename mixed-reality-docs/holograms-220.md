---
title: MR 空間 220-空間音效
description: 遵循此編碼逐步解說, 使用 Unity、Visual Studio 和 HoloLens 來瞭解空間音效概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 學院, 教學課程, 空間音效
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526974"
---
>[!NOTE]
><span data-ttu-id="67abe-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="67abe-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="67abe-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="67abe-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="67abe-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="67abe-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="67abe-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="67abe-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="67abe-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="67abe-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="67abe-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="67abe-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="67abe-110">MR 空間 220:空間音效</span><span class="sxs-lookup"><span data-stu-id="67abe-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="67abe-111">[空間音效](spatial-sound.md)breathes 的生活進入全息的狀態, 並提供給我們世界各地。</span><span class="sxs-lookup"><span data-stu-id="67abe-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="67abe-112">全像投影都是由光線和音效所組成, 如果您似乎失去了全息影像, 空間音效可以協助您找到它們。</span><span class="sxs-lookup"><span data-stu-id="67abe-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="67abe-113">空間音效與您在廣播上聽到的一般音效不一樣, 它是位於3D 空間中的音效。</span><span class="sxs-lookup"><span data-stu-id="67abe-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="67abe-114">有了空間音效, 您就可以讓像是像是您一樣的全像投影, 或甚至是您的頭部!</span><span class="sxs-lookup"><span data-stu-id="67abe-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="67abe-115">在此課程中, 您將會:</span><span class="sxs-lookup"><span data-stu-id="67abe-115">In this course, you will:</span></span>

* <span data-ttu-id="67abe-116">設定您的開發環境以使用 Microsoft 空間音效。</span><span class="sxs-lookup"><span data-stu-id="67abe-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="67abe-117">使用空間音效來增強互動。</span><span class="sxs-lookup"><span data-stu-id="67abe-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="67abe-118">將空間音效與空間對應搭配使用。</span><span class="sxs-lookup"><span data-stu-id="67abe-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="67abe-119">瞭解音效設計和混合最佳作法。</span><span class="sxs-lookup"><span data-stu-id="67abe-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="67abe-120">使用音效來增強特殊效果, 並將使用者帶入混合現實世界。</span><span class="sxs-lookup"><span data-stu-id="67abe-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="67abe-121">裝置支援</span><span class="sxs-lookup"><span data-stu-id="67abe-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="67abe-122">粗</span><span class="sxs-lookup"><span data-stu-id="67abe-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="67abe-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="67abe-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="67abe-124"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="67abe-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="67abe-125">MR 空間 220:空間音效</span><span class="sxs-lookup"><span data-stu-id="67abe-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="67abe-126">✔️</span><span class="sxs-lookup"><span data-stu-id="67abe-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="67abe-127">✔️</span><span class="sxs-lookup"><span data-stu-id="67abe-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="67abe-128">開始之前</span><span class="sxs-lookup"><span data-stu-id="67abe-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="67abe-129">必要條件</span><span class="sxs-lookup"><span data-stu-id="67abe-129">Prerequisites</span></span>

* <span data-ttu-id="67abe-130">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="67abe-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="67abe-131">一些基本C#的程式設計能力。</span><span class="sxs-lookup"><span data-stu-id="67abe-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="67abe-132">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="67abe-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="67abe-133">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="67abe-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="67abe-134">專案檔案</span><span class="sxs-lookup"><span data-stu-id="67abe-134">Project files</span></span>

* <span data-ttu-id="67abe-135">下載專案所需的[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)。</span><span class="sxs-lookup"><span data-stu-id="67abe-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="67abe-136"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="67abe-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="67abe-137">如果您仍然需要 Unity 5.6 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="67abe-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="67abe-138">此版本可能不再是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="67abe-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="67abe-139">如果您仍然需要 Unity 5.5 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="67abe-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="67abe-140"> 此版本可能不再是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="67abe-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="67abe-141">如果您仍然需要 Unity 5.4 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="67abe-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="67abe-142"> 此版本可能不再是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="67abe-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="67abe-143">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="67abe-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="67abe-144">如果您想要在下載之前查看原始程式碼, 可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)取得。</span><span class="sxs-lookup"><span data-stu-id="67abe-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="67abe-145">勘誤和注意事項</span><span class="sxs-lookup"><span data-stu-id="67abe-145">Errata and Notes</span></span>

* <span data-ttu-id="67abe-146">必須在 Visual Studio 下的 [工具]-[> 選項]-[> 的偵錯工具] 中停用 (*取消*核取) [啟用 Just My Code], 才能在程式碼中叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="67abe-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="67abe-147">第1章-Unity 設定</span><span class="sxs-lookup"><span data-stu-id="67abe-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="67abe-148">目標</span><span class="sxs-lookup"><span data-stu-id="67abe-148">Objectives</span></span>

* <span data-ttu-id="67abe-149">將 Unity 的音效設定變更為使用 Microsoft 空間音效。</span><span class="sxs-lookup"><span data-stu-id="67abe-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="67abe-150">將3D 音效新增至 Unity 中的物件。</span><span class="sxs-lookup"><span data-stu-id="67abe-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="67abe-151">指示</span><span class="sxs-lookup"><span data-stu-id="67abe-151">Instructions</span></span>

* <span data-ttu-id="67abe-152">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="67abe-152">Start Unity.</span></span>
* <span data-ttu-id="67abe-153">選取 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-153">Select **Open**.</span></span>
* <span data-ttu-id="67abe-154">流覽至您的桌面, 並尋找您先前取消封存的資料夾。</span><span class="sxs-lookup"><span data-stu-id="67abe-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="67abe-155">按一下 [ **Starting\Decibel** ] 資料夾, 然後按 [**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="67abe-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="67abe-156">等候專案載入 Unity。</span><span class="sxs-lookup"><span data-stu-id="67abe-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="67abe-157">在 [ **專案**] 面板中, 開啟**Scenes\Decibel.unity**。</span><span class="sxs-lookup"><span data-stu-id="67abe-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="67abe-158">在 [階層] 面板中, 展開 [ **HologramCollection** ], 然後選取 [ **P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="67abe-159">在偵測器中, 展開 [ **spatialize** ], 並注意 [沒有**Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="67abe-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="67abe-160">根據預設, Unity 不會載入空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="67abe-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="67abe-161">下列步驟將會啟用專案中的空間音效。</span><span class="sxs-lookup"><span data-stu-id="67abe-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="67abe-162">在 Unity 的頂端功能表中, 移至 **編輯 > 專案設定 > 音訊**。</span><span class="sxs-lookup"><span data-stu-id="67abe-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="67abe-163">尋找 [**空間定位器外掛程式**] 下拉式清單, 然後選取 [ **MS HRTF 空間定位器**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="67abe-164">在 [階層] 面板中, 選取 [ **HologramCollection > P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="67abe-165">在 [偵測**器**] 面板中, 尋找 [**音訊來源**] 元件。</span><span class="sxs-lookup"><span data-stu-id="67abe-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="67abe-166">核取 [ **Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="67abe-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="67abe-167">將**空間 Blend**滑杆拖曳到**3d**, 或在編輯方塊中輸入**1** 。</span><span class="sxs-lookup"><span data-stu-id="67abe-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="67abe-168">我們現在會在 Unity 中建立專案, 並在 Visual Studio 中設定方案。</span><span class="sxs-lookup"><span data-stu-id="67abe-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="67abe-169">在 Unity 中, 選取 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="67abe-170">按一下 [新增] [**開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="67abe-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="67abe-171">在 [**平臺**] 清單中選取**通用 Windows 平臺**, 然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="67abe-172">如果您是特別針對 HoloLens 進行開發, 請將**目標裝置**設定為**hololens**。</span><span class="sxs-lookup"><span data-stu-id="67abe-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="67abe-173">否則, 請將它保留在**任何裝置**上。</span><span class="sxs-lookup"><span data-stu-id="67abe-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="67abe-174">確定 [**組建類型**] 設定為 [ **D3D** ], 並將 [ **sdk** ] 設定為 [**已安裝最新**版本] (應該是 SDK 16299 或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="67abe-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="67abe-175">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="67abe-175">Click **Build**.</span></span>
7. <span data-ttu-id="67abe-176">建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="67abe-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="67abe-177">按一下 [**應用程式**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="67abe-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="67abe-178">按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-178">Press **Select Folder**.</span></span>

<span data-ttu-id="67abe-179">當 Unity 完成時, 將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="67abe-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="67abe-180">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="67abe-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="67abe-181">開啟 [**分貝] Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="67abe-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="67abe-182">如果部署至 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="67abe-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="67abe-183">使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**x86**。</span><span class="sxs-lookup"><span data-stu-id="67abe-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="67abe-184">按一下 [本機電腦] 按鈕旁的下拉式箭號, 然後選取 [**遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="67abe-185">輸入**您的 HoloLens 裝置 IP 位址**, 並將驗證模式設定為 **[通用 (未加密的通訊協定)** ]。</span><span class="sxs-lookup"><span data-stu-id="67abe-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="67abe-186">按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="67abe-186">Click **Select**.</span></span> <span data-ttu-id="67abe-187">如果您不知道您的裝置 IP 位址, 請查看 [設定] [ **> Network & Internet] > [Advanced Options**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="67abe-188">在頂端功能表列中, 按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="67abe-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="67abe-189">如果這是您第一次部署至您的裝置, 您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device---hololens-1st-gen)。</span><span class="sxs-lookup"><span data-stu-id="67abe-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="67abe-190">如果部署到沉浸式耳機:</span><span class="sxs-lookup"><span data-stu-id="67abe-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="67abe-191">使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**x64**。</span><span class="sxs-lookup"><span data-stu-id="67abe-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="67abe-192">請確定 [部署目標] 設定為 [**本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="67abe-193">在頂端功能表列中, 按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="67abe-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="67abe-194">第2章-空間音效和互動</span><span class="sxs-lookup"><span data-stu-id="67abe-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="67abe-195">目標</span><span class="sxs-lookup"><span data-stu-id="67abe-195">Objectives</span></span>

* <span data-ttu-id="67abe-196">使用音效增強全息影像的真實感。</span><span class="sxs-lookup"><span data-stu-id="67abe-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="67abe-197">使用音效引導使用者的注視。</span><span class="sxs-lookup"><span data-stu-id="67abe-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="67abe-198">使用音效提供手勢意見反應。</span><span class="sxs-lookup"><span data-stu-id="67abe-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="67abe-199">第1部分-增強真實性</span><span class="sxs-lookup"><span data-stu-id="67abe-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="67abe-200">重要概念</span><span class="sxs-lookup"><span data-stu-id="67abe-200">Key Concepts</span></span>

* <span data-ttu-id="67abe-201">Spatialize 的全息影像音效。</span><span class="sxs-lookup"><span data-stu-id="67abe-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="67abe-202">音效來源應該放在全息影像上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="67abe-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="67abe-203">音效的適當位置將取決於全息影像。</span><span class="sxs-lookup"><span data-stu-id="67abe-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="67abe-204">例如, 如果全像是人類的全息圖, 則音效來源應該位於嘴附近, 而不是腳。</span><span class="sxs-lookup"><span data-stu-id="67abe-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="67abe-205">指示</span><span class="sxs-lookup"><span data-stu-id="67abe-205">Instructions</span></span>

<span data-ttu-id="67abe-206">下列指示會將 hrtf 音效附加至全息影像。</span><span class="sxs-lookup"><span data-stu-id="67abe-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="67abe-207">在 [階層] 面板中, 展開 [ **HologramCollection** ], 然後選取 [ **P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="67abe-208">在 [偵測**器**] 面板的 [ **spatialize**] 中, 按一下 [ **AudioClip** ] 旁邊的圓形, 然後從快顯視窗中選取 [ **PolyHover** ]。</span><span class="sxs-lookup"><span data-stu-id="67abe-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="67abe-209">按一下 [**輸出**] 旁的圓形, 然後從快顯視窗中選取 [ **SoundEffects** ]。</span><span class="sxs-lookup"><span data-stu-id="67abe-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="67abe-210">Project 分貝會使用 Unity **AudioMixer**元件, 為音效群組啟用調整聲音層級。</span><span class="sxs-lookup"><span data-stu-id="67abe-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="67abe-211">藉由以這種方式將聲音分組, 可以調整整體磁片區, 同時維持每個音效的相對量。</span><span class="sxs-lookup"><span data-stu-id="67abe-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="67abe-212">在**spatialize**中, 展開 [ **3d 音效設定**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="67abe-213">將 [ **Doppler 層級**] 設定為**0**。</span><span class="sxs-lookup"><span data-stu-id="67abe-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="67abe-214">將 Doppler 層級設定為零會停用移動 (全像是全息或使用者) 所造成的音調變更。</span><span class="sxs-lookup"><span data-stu-id="67abe-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="67abe-215">Doppler 的典型範例是快速移動的汽車。</span><span class="sxs-lookup"><span data-stu-id="67abe-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="67abe-216">隨著汽車接近固定的接聽程式, 引擎的音調也會上升。</span><span class="sxs-lookup"><span data-stu-id="67abe-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="67abe-217">當它通過接聽程式時, 音調就會減少與距離。</span><span class="sxs-lookup"><span data-stu-id="67abe-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="67abe-218">第2部分-引導使用者的注視</span><span class="sxs-lookup"><span data-stu-id="67abe-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="67abe-219">重要概念</span><span class="sxs-lookup"><span data-stu-id="67abe-219">Key Concepts</span></span>

* <span data-ttu-id="67abe-220">使用音效來留意重要的全息影像。</span><span class="sxs-lookup"><span data-stu-id="67abe-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="67abe-221">此耳可協助引導眼睛的外觀。</span><span class="sxs-lookup"><span data-stu-id="67abe-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="67abe-222">大腦有一些學習的預期。</span><span class="sxs-lookup"><span data-stu-id="67abe-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="67abe-223">學習預期的一個範例是, 鳥瞰通常在人類的正上方。</span><span class="sxs-lookup"><span data-stu-id="67abe-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="67abe-224">如果使用者聽到鳥瞰聲, 其初始反應就是查閱。</span><span class="sxs-lookup"><span data-stu-id="67abe-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="67abe-225">將鳥瞰圖放在使用者下方, 會導致他們以正確的音效方向呈現, 但無法根據預期的查詢來尋找全息。</span><span class="sxs-lookup"><span data-stu-id="67abe-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="67abe-226">指示</span><span class="sxs-lookup"><span data-stu-id="67abe-226">Instructions</span></span>

<span data-ttu-id="67abe-227">下列指示可讓 P0LY 隱藏在您的後方, 讓您可以使用音效來尋找全息的全像投影。</span><span class="sxs-lookup"><span data-stu-id="67abe-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="67abe-228">在 [階層] 面板中, 選取 [**管理員**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="67abe-229">在 [偵測**器**] 面板中, 尋找 [**語音輸入處理常式**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="67abe-230">在 [**語音輸入處理常式**] 中, 展開 [**移至隱藏**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="67abe-231">將**No Function**變更為**PolyActions. GoHide**。</span><span class="sxs-lookup"><span data-stu-id="67abe-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![關鍵字移至隱藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="67abe-233">第3部分-手勢意見反應</span><span class="sxs-lookup"><span data-stu-id="67abe-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="67abe-234">重要概念</span><span class="sxs-lookup"><span data-stu-id="67abe-234">Key Concepts</span></span>

* <span data-ttu-id="67abe-235">為使用者提供使用音效的正面手勢確認</span><span class="sxs-lookup"><span data-stu-id="67abe-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="67abe-236">不要讓使用者過於塞滿的音效</span><span class="sxs-lookup"><span data-stu-id="67abe-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="67abe-237">微妙音效的效果最佳-不要失色經驗</span><span class="sxs-lookup"><span data-stu-id="67abe-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="67abe-238">指示</span><span class="sxs-lookup"><span data-stu-id="67abe-238">Instructions</span></span>

* <span data-ttu-id="67abe-239">在 [階層] 面板中, 展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="67abe-240">展開 [ **EnergyHub** ], 然後選取 [**基底**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="67abe-241">在 [偵測**器**] 面板中, 按一下 [**加入元件**], 然後加入**手勢音效處理常式**。</span><span class="sxs-lookup"><span data-stu-id="67abe-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="67abe-242">在 [**手勢音效處理常式**] 中, 按一下 [**導覽已啟動的剪輯**] 和 [**導覽已更新剪輯**] 旁的圓形, 然後從這兩者的快顯視窗選取 [ **RotateClick** ]。</span><span class="sxs-lookup"><span data-stu-id="67abe-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="67abe-243">按兩下 [GestureSoundHandler] 以載入 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="67abe-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="67abe-244">手勢音效處理常式會執行下列工作:</span><span class="sxs-lookup"><span data-stu-id="67abe-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="67abe-245">建立和設定**spatialize**。</span><span class="sxs-lookup"><span data-stu-id="67abe-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="67abe-246">將**spatialize**放在適當**GameObject**的位置。</span><span class="sxs-lookup"><span data-stu-id="67abe-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="67abe-247">播放與手勢相關聯的**AudioClip** 。</span><span class="sxs-lookup"><span data-stu-id="67abe-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="67abe-248">組建和部署</span><span class="sxs-lookup"><span data-stu-id="67abe-248">Build and Deploy</span></span>

1. <span data-ttu-id="67abe-249">在 Unity 中, 選取 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="67abe-250">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="67abe-250">Click **Build**.</span></span>
3. <span data-ttu-id="67abe-251">按一下 [**應用程式**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="67abe-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="67abe-252">按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-252">Press **Select Folder**.</span></span>

<span data-ttu-id="67abe-253">檢查工具列是否顯示 [發行]、[x86] 或 [x64], 以及 [遠端裝置]。</span><span class="sxs-lookup"><span data-stu-id="67abe-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="67abe-254">如果不是, 這就是 Visual Studio 的程式碼實例。</span><span class="sxs-lookup"><span data-stu-id="67abe-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="67abe-255">您可能需要從應用程式資料夾重新開啟解決方案。</span><span class="sxs-lookup"><span data-stu-id="67abe-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="67abe-256">如果出現提示, 請重載專案檔案。</span><span class="sxs-lookup"><span data-stu-id="67abe-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="67abe-257">同樣地, 從 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="67abe-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="67abe-258">部署應用程式之後:</span><span class="sxs-lookup"><span data-stu-id="67abe-258">After the application is deployed:</span></span>

* <span data-ttu-id="67abe-259">觀察當您在 P0LY 四處移動時, 音效如何改變。</span><span class="sxs-lookup"><span data-stu-id="67abe-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="67abe-260">說「 *Go Hide* 」, 讓 P0LY 移到您背後的位置。</span><span class="sxs-lookup"><span data-stu-id="67abe-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="67abe-261">依音效尋找。</span><span class="sxs-lookup"><span data-stu-id="67abe-261">Find it by the sound.</span></span>
* <span data-ttu-id="67abe-262">看著能源中樞的基礎。</span><span class="sxs-lookup"><span data-stu-id="67abe-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="67abe-263">請按住滑鼠左鍵並向左或向右拖曳以旋轉全像投影, 並注意按一下音效如何確認手勢。</span><span class="sxs-lookup"><span data-stu-id="67abe-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="67abe-264">注意:有一個文字面板會與您一起標記。</span><span class="sxs-lookup"><span data-stu-id="67abe-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="67abe-265">這會包含可供您在本課程中使用的語音命令。</span><span class="sxs-lookup"><span data-stu-id="67abe-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="67abe-266">第3章-空間音效和空間對應</span><span class="sxs-lookup"><span data-stu-id="67abe-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="67abe-267">目標</span><span class="sxs-lookup"><span data-stu-id="67abe-267">Objectives</span></span>

* <span data-ttu-id="67abe-268">使用音效確認全息影像與真實世界之間的互動。</span><span class="sxs-lookup"><span data-stu-id="67abe-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="67abe-269">使用實體世界遮蔽音效。</span><span class="sxs-lookup"><span data-stu-id="67abe-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="67abe-270">第1部分-實體世界互動</span><span class="sxs-lookup"><span data-stu-id="67abe-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="67abe-271">重要概念</span><span class="sxs-lookup"><span data-stu-id="67abe-271">Key Concepts</span></span>

* <span data-ttu-id="67abe-272">當遇到表面或另一個物件時, 實體物件通常會發出音效。</span><span class="sxs-lookup"><span data-stu-id="67abe-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="67abe-273">音效在體驗中應該是適當的內容。</span><span class="sxs-lookup"><span data-stu-id="67abe-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="67abe-274">例如, 在資料表上設定杯時, 應該會比在金屬片上卸載科羅拉多, 讓音效更為安靜。</span><span class="sxs-lookup"><span data-stu-id="67abe-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="67abe-275">指示</span><span class="sxs-lookup"><span data-stu-id="67abe-275">Instructions</span></span>

* <span data-ttu-id="67abe-276">在 [階層] 面板中, 展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="67abe-277">展開 [ **EnergyHub**], 選取 [**基底**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="67abe-278">在 [偵測**器**] 面板中, 按一下 [**新增元件**], 然後新增 **[使用音效和動作來放置**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="67abe-279">**使用音效和動作來放置**:</span><span class="sxs-lookup"><span data-stu-id="67abe-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="67abe-280">勾選 **[將父系放在點上**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="67abe-281">將**放置音效**設定為 [**放置**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="67abe-282">將**Pickup 音效**設定為**取貨**。</span><span class="sxs-lookup"><span data-stu-id="67abe-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="67abe-283">**在 [取貨動作**] 和 [**放置] 動作上**, 按右下方的 [+]。</span><span class="sxs-lookup"><span data-stu-id="67abe-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="67abe-284">將 [EnergyHub] 從場景拖曳至 [**無] (物件)** 欄位。</span><span class="sxs-lookup"><span data-stu-id="67abe-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="67abe-285">在 [**收取取貨動作**] 下, 按一下 [ **No Function**  ->  **EnergyHubBase**  ->  **ResetAnimation**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="67abe-286">在 [**放置動作**] 底下,  -> 按一下 [無函式**EnergyHubBase**  ->  **OnSelect**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![利用音效和動作來放置](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="67abe-288">第2部分-音效遮蔽</span><span class="sxs-lookup"><span data-stu-id="67abe-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="67abe-289">重要概念</span><span class="sxs-lookup"><span data-stu-id="67abe-289">Key Concepts</span></span>

* <span data-ttu-id="67abe-290">音效 (如 light) 可以 pixels occluded。</span><span class="sxs-lookup"><span data-stu-id="67abe-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="67abe-291">典型的範例是音樂會廳。</span><span class="sxs-lookup"><span data-stu-id="67abe-291">A classic example is a concert hall.</span></span> <span data-ttu-id="67abe-292">當接聽程式離開大廳外, 而門已關閉時, 音樂會 muffled。</span><span class="sxs-lookup"><span data-stu-id="67abe-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="67abe-293">一般來說, 磁片區也會減少。</span><span class="sxs-lookup"><span data-stu-id="67abe-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="67abe-294">當門開啟時, 會在實際音量聽到音效的完整範圍。</span><span class="sxs-lookup"><span data-stu-id="67abe-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="67abe-295">高頻率的音效通常會吸收超過低頻率。</span><span class="sxs-lookup"><span data-stu-id="67abe-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="67abe-296">指示</span><span class="sxs-lookup"><span data-stu-id="67abe-296">Instructions</span></span>

* <span data-ttu-id="67abe-297">在 [階層] 面板中, 展開 [ **HologramCollection** ], 然後選取 [ **P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="67abe-298">在 [偵測**器**] 面板中, 按一下 [**新增元件**] 並新增**音訊發射器**。</span><span class="sxs-lookup"><span data-stu-id="67abe-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="67abe-299">音訊發射器類別提供下列功能:</span><span class="sxs-lookup"><span data-stu-id="67abe-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="67abe-300">還原**spatialize**磁片區的任何變更。</span><span class="sxs-lookup"><span data-stu-id="67abe-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="67abe-301">以附加**AudioEmitter**的**GameObject**方向, 從使用者的位置執行**RaycastNonAlloc** 。</span><span class="sxs-lookup"><span data-stu-id="67abe-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="67abe-302">RaycastNonAlloc 方法是用來做為效能優化, 以限制配置以及傳回的結果數目。</span><span class="sxs-lookup"><span data-stu-id="67abe-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="67abe-303">針對每個遇到的**IAudioInfluencer** , 會呼叫**ApplyEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="67abe-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="67abe-304">對於不再遇到的每個先前**IAudioInfluencer** , 請呼叫**RemoveEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="67abe-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="67abe-305">請注意, AudioEmitter 會更新人力時間規模, 而不是每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="67abe-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="67abe-306">這樣做的原因是, 人們通常無法快速地進行更新, 而需要比每個季或半秒的頻率更高。</span><span class="sxs-lookup"><span data-stu-id="67abe-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="67abe-307">從一個位置快速傳送到另一個位置的全息影像, 可能會破壞夢想。</span><span class="sxs-lookup"><span data-stu-id="67abe-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="67abe-308">在 [階層] 面板中, 展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="67abe-309">展開 [ **EnergyHub** ], 然後選取 [ **BlobOutside**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="67abe-310">在 [偵測**器**] 面板中, 按一下 [**新增元件**] 並新增**音訊 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="67abe-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="67abe-311">在 [**音訊 Occluder**] 中, 將 [**截止頻率**] 設定為**1500**。</span><span class="sxs-lookup"><span data-stu-id="67abe-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="67abe-312">此設定會將 Spatialize 頻率限制為 1500 Hz 和以下。</span><span class="sxs-lookup"><span data-stu-id="67abe-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="67abe-313">將**磁片區傳遞**至**0.9**。</span><span class="sxs-lookup"><span data-stu-id="67abe-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="67abe-314">此設定會將 Spatialize 的數量減少到其目前層級的 90%。</span><span class="sxs-lookup"><span data-stu-id="67abe-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="67abe-315">音訊 Occluder 會將 IAudioInfluencer 實作為:</span><span class="sxs-lookup"><span data-stu-id="67abe-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="67abe-316">使用附加至**spatialize**受控購買**AudioEmitter**的**AudioLowPassFilter**來套用遮蔽效果。</span><span class="sxs-lookup"><span data-stu-id="67abe-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="67abe-317">將磁片區衰減套用至 Spatialize。</span><span class="sxs-lookup"><span data-stu-id="67abe-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="67abe-318">藉由設定中性的截止頻率並停用篩選來停用效果。</span><span class="sxs-lookup"><span data-stu-id="67abe-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="67abe-319">用為中性的頻率是 22 kHz (22000 Hz)。</span><span class="sxs-lookup"><span data-stu-id="67abe-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="67abe-320">選擇此頻率的原因, 是因為它高於人耳可聽到的名義最大頻率, 所以不會對音效造成明顯影響。</span><span class="sxs-lookup"><span data-stu-id="67abe-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="67abe-321">在 [階層] 面板中, 選取 [ **SpatialMapping**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="67abe-322">在 [偵測**器**] 面板中, 按一下 [**新增元件**] 並新增**音訊 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="67abe-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="67abe-323">在 [**音訊 Occluder**] 中, 將 [**截止頻率**] 設定為**750**。</span><span class="sxs-lookup"><span data-stu-id="67abe-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="67abe-324">當使用者和**AudioEmitter**之間的路徑中有多個阻隔器時, 會將最低頻率套用至篩選準則。</span><span class="sxs-lookup"><span data-stu-id="67abe-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="67abe-325">將**磁片區傳遞**至**0.75**。</span><span class="sxs-lookup"><span data-stu-id="67abe-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="67abe-326">當使用者和**AudioEmitter**之間的路徑中有多個阻隔器時, 就會套用 additively 的磁片區。</span><span class="sxs-lookup"><span data-stu-id="67abe-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="67abe-327">在 [階層] 面板中, 選取 [**管理員**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="67abe-328">在 [偵測**器**] 面板中, 展開 [**語音輸入處理常式**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="67abe-329">在 [**語音輸入處理常式**] 中, 展開 [**繼續收費**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="67abe-330">將**No Function**變更為**PolyActions. GoCharge**。</span><span class="sxs-lookup"><span data-stu-id="67abe-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![關鍵字繼續收費](images/gocharge.png)

* <span data-ttu-id="67abe-332">依序展開 [前往**這裡**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="67abe-333">將**No Function**變更為**PolyActions. 撰寫復活**。</span><span class="sxs-lookup"><span data-stu-id="67abe-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![關鍵字過來這裡](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="67abe-335">組建和部署</span><span class="sxs-lookup"><span data-stu-id="67abe-335">Build and Deploy</span></span>

* <span data-ttu-id="67abe-336">如先前一樣, 在 Unity 中建立專案, 並在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="67abe-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="67abe-337">部署應用程式之後:</span><span class="sxs-lookup"><span data-stu-id="67abe-337">After the application is deployed:</span></span>

* <span data-ttu-id="67abe-338">說「*繼續收費*」, 讓 P0LY 進入能源中樞。</span><span class="sxs-lookup"><span data-stu-id="67abe-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="67abe-339">請注意音效中的變更。</span><span class="sxs-lookup"><span data-stu-id="67abe-339">Note the change in the sound.</span></span> <span data-ttu-id="67abe-340">它應該聽起來 muffled, 而且有點安靜。</span><span class="sxs-lookup"><span data-stu-id="67abe-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="67abe-341">如果您可以在您和能源中樞之間定位自己的牆或其他物件, 您應該會注意到因為真實世界遮蔽, 而 muffling 的音效。</span><span class="sxs-lookup"><span data-stu-id="67abe-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="67abe-342">說「*在這裡*」, 讓 P0LY 離開能源中樞, 並將其本身放在您的前方。</span><span class="sxs-lookup"><span data-stu-id="67abe-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="67abe-343">請注意, P0LY 結束能源中樞後, 就會移除音效遮蔽。</span><span class="sxs-lookup"><span data-stu-id="67abe-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="67abe-344">如果您仍然聽到遮蔽, P0LY 可能會受到真實世界的 pixels occluded。</span><span class="sxs-lookup"><span data-stu-id="67abe-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="67abe-345">請嘗試移動以確保您有清楚的 P0LY。</span><span class="sxs-lookup"><span data-stu-id="67abe-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="67abe-346">第3部分-會議室模型</span><span class="sxs-lookup"><span data-stu-id="67abe-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="67abe-347">重要概念</span><span class="sxs-lookup"><span data-stu-id="67abe-347">Key Concepts</span></span>

* <span data-ttu-id="67abe-348">空間的大小會提供 subliminal 的佇列, 以做出音效當地語系化。</span><span class="sxs-lookup"><span data-stu-id="67abe-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="67abe-349">會議室模型是依**spatialize**設定。</span><span class="sxs-lookup"><span data-stu-id="67abe-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="67abe-350">[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供設定房間模型的程式碼。</span><span class="sxs-lookup"><span data-stu-id="67abe-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="67abe-351">針對混合現實體驗, 請選取最適合真實世界空間的房間模型。</span><span class="sxs-lookup"><span data-stu-id="67abe-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="67abe-352">如果您要建立虛擬實境案例, 請選取最適合虛擬環境的房間模型。</span><span class="sxs-lookup"><span data-stu-id="67abe-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="67abe-353">第4章-音效設計</span><span class="sxs-lookup"><span data-stu-id="67abe-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="67abe-354">目標</span><span class="sxs-lookup"><span data-stu-id="67abe-354">Objectives</span></span>

* <span data-ttu-id="67abe-355">瞭解有效音效設計的考慮。</span><span class="sxs-lookup"><span data-stu-id="67abe-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="67abe-356">瞭解混合技術和指導方針。</span><span class="sxs-lookup"><span data-stu-id="67abe-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="67abe-357">第1部分-音效和體驗設計</span><span class="sxs-lookup"><span data-stu-id="67abe-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="67abe-358">本節討論主要音效和體驗設計考慮和指導方針。</span><span class="sxs-lookup"><span data-stu-id="67abe-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="67abe-359">標準化所有聲音</span><span class="sxs-lookup"><span data-stu-id="67abe-359">Normalize all sounds</span></span>

<span data-ttu-id="67abe-360">如此一來, 就不需要特殊的案常式序代碼來調整每個音效的音量層級, 這可能相當耗時, 而且會限制輕鬆更新音效檔的能力。</span><span class="sxs-lookup"><span data-stu-id="67abe-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="67abe-361">非網路共用體驗的設計</span><span class="sxs-lookup"><span data-stu-id="67abe-361">Design for an untethered experience</span></span>

<span data-ttu-id="67abe-362">HoloLens 是完全獨立的非網路共用全像攝影電腦。</span><span class="sxs-lookup"><span data-stu-id="67abe-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="67abe-363">您的使用者可以和將會在移動時使用您的體驗。</span><span class="sxs-lookup"><span data-stu-id="67abe-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="67abe-364">請務必四處流覽來測試您的音訊混合。</span><span class="sxs-lookup"><span data-stu-id="67abe-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="67abe-365">從您的全息影像上的邏輯位置發出音效</span><span class="sxs-lookup"><span data-stu-id="67abe-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="67abe-366">在真實世界中, 狗不會從結尾處吠, 而且人類的語音也不會來自其腳。</span><span class="sxs-lookup"><span data-stu-id="67abe-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="67abe-367">避免在您的全息影像未預期的部分發出聲音。</span><span class="sxs-lookup"><span data-stu-id="67abe-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="67abe-368">對於小型的全息影像, 從幾何中心開始音效是合理的。</span><span class="sxs-lookup"><span data-stu-id="67abe-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="67abe-369">熟悉的音效是最能當地語系化的</span><span class="sxs-lookup"><span data-stu-id="67abe-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="67abe-370">人類語音和音樂很容易當地語系化。</span><span class="sxs-lookup"><span data-stu-id="67abe-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="67abe-371">如果有人撥打您的名字, 您就能夠非常準確地判斷語音的方向和距離。</span><span class="sxs-lookup"><span data-stu-id="67abe-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="67abe-372">簡言之, 不熟悉的音效很難當地語系化。</span><span class="sxs-lookup"><span data-stu-id="67abe-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="67abe-373">使用者期望的 cognizant</span><span class="sxs-lookup"><span data-stu-id="67abe-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="67abe-374">生命體驗在我們識別音效位置的功能中扮演了部分。</span><span class="sxs-lookup"><span data-stu-id="67abe-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="67abe-375">這就是為什麼人類語音特別容易當地語系化的原因之一。</span><span class="sxs-lookup"><span data-stu-id="67abe-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="67abe-376">請務必留意您的使用者在放置音效時所學到的預期。</span><span class="sxs-lookup"><span data-stu-id="67abe-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="67abe-377">比方說, 當有人聽到一則一般會查詢的「鳥」歌曲時, 因為鳥傾向于觀察線上 (飛行或在樹狀結構中)。</span><span class="sxs-lookup"><span data-stu-id="67abe-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="67abe-378">使用者不常以正確的音效方向開啟, 而是在找不到任何一種垂直方向, 並在無法找到全息的情況下感到困惑或挫折。</span><span class="sxs-lookup"><span data-stu-id="67abe-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="67abe-379">避免隱藏的發射器</span><span class="sxs-lookup"><span data-stu-id="67abe-379">Avoid hidden emitters</span></span>

<span data-ttu-id="67abe-380">在真實世界中, 如果聽到音效, 我們通常可以識別發出音效的物件。</span><span class="sxs-lookup"><span data-stu-id="67abe-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="67abe-381">這也應該在您的經驗中成立。</span><span class="sxs-lookup"><span data-stu-id="67abe-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="67abe-382">這可能非常令人不安, 讓使用者聽到音效, 知道聲音源自何處, 而無法看到物件。</span><span class="sxs-lookup"><span data-stu-id="67abe-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="67abe-383">此指導方針有一些例外狀況。</span><span class="sxs-lookup"><span data-stu-id="67abe-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="67abe-384">例如, 欄位中的環境音效 (例如 crickets) 不需要是可見的。</span><span class="sxs-lookup"><span data-stu-id="67abe-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="67abe-385">生活經驗讓我們熟悉這些音效的來源, 而不需要看到它。</span><span class="sxs-lookup"><span data-stu-id="67abe-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="67abe-386">第2部分-音效混合</span><span class="sxs-lookup"><span data-stu-id="67abe-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="67abe-387">將您的混合目標設為 HoloLens 上的 70% 磁片區</span><span class="sxs-lookup"><span data-stu-id="67abe-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="67abe-388">混合現實體驗允許在真實世界中看到全息影像。</span><span class="sxs-lookup"><span data-stu-id="67abe-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="67abe-389">他們也應該能夠聽到真實世界的聲音。</span><span class="sxs-lookup"><span data-stu-id="67abe-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="67abe-390">70% 的磁片區目標可讓使用者在世界各地聆聽他們, 並附上您的體驗。</span><span class="sxs-lookup"><span data-stu-id="67abe-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="67abe-391">100% 磁片區上的 HoloLens 應下拉式清單外部聲音</span><span class="sxs-lookup"><span data-stu-id="67abe-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="67abe-392">磁片區層級 100% 類似于虛擬實境體驗。</span><span class="sxs-lookup"><span data-stu-id="67abe-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="67abe-393">使用者會以視覺化方式傳輸到不同的世界。</span><span class="sxs-lookup"><span data-stu-id="67abe-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="67abe-394">同樣的情況也應該保留 true 語音。</span><span class="sxs-lookup"><span data-stu-id="67abe-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="67abe-395">使用 Unity AudioMixer 來調整音效的類別</span><span class="sxs-lookup"><span data-stu-id="67abe-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="67abe-396">設計混合時, 建立音效類別並能夠以一個單位來增加或減少其音量, 通常會很有説明。</span><span class="sxs-lookup"><span data-stu-id="67abe-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="67abe-397">這會保留每個音效的相對層級, 同時讓整體混合的快速且輕鬆地進行變更。</span><span class="sxs-lookup"><span data-stu-id="67abe-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="67abe-398">常見的類別包括:聲音效果、環境、語音轉移和背景音樂。</span><span class="sxs-lookup"><span data-stu-id="67abe-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="67abe-399">根據使用者的注視來混合聲音</span><span class="sxs-lookup"><span data-stu-id="67abe-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="67abe-400">根據使用者的所在位置 (或不是) 來變更您的體驗, 通常會很有用。</span><span class="sxs-lookup"><span data-stu-id="67abe-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="67abe-401">這項技術的其中一個常見用途是減少全像攝影畫面外的全息影像音量, 讓使用者更容易專注于他們前面的資訊。</span><span class="sxs-lookup"><span data-stu-id="67abe-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="67abe-402">另一種用途是增加音效的音量, 將使用者的注意力吸引到重要的事件。</span><span class="sxs-lookup"><span data-stu-id="67abe-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="67abe-403">打造您的混合</span><span class="sxs-lookup"><span data-stu-id="67abe-403">Building your mix</span></span>

<span data-ttu-id="67abe-404">建立混合時, 建議您從體驗的背景音訊開始, 並根據重要性新增圖層。</span><span class="sxs-lookup"><span data-stu-id="67abe-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="67abe-405">通常, 這會導致每個圖層都比先前的還要大。</span><span class="sxs-lookup"><span data-stu-id="67abe-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="67abe-406">將您的混合想像為反向漏斗圖, 其底部最重要的 (通常是 quietest 音效), 建議您將混合結構與下圖類似。</span><span class="sxs-lookup"><span data-stu-id="67abe-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![音效混合結構](images/soundlevels.png)

<span data-ttu-id="67abe-408">語音轉移是一種有趣的案例。</span><span class="sxs-lookup"><span data-stu-id="67abe-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="67abe-409">根據您所建立的經驗, 您可能會想要有身歷聲 (非當地語系化) 音效或 spatialize 語音轉移。</span><span class="sxs-lookup"><span data-stu-id="67abe-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="67abe-410">兩個 Microsoft 發佈的體驗說明每個案例的絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="67abe-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="67abe-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)使用身歷聲聲音。</span><span class="sxs-lookup"><span data-stu-id="67abe-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="67abe-412">當朗讀程式描述要查看的位置時, 音效會一致, 而且不會因使用者的位置而有所不同。</span><span class="sxs-lookup"><span data-stu-id="67abe-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="67abe-413">這可讓 [朗讀程式] 描述場景, 而不需要離開環境的 hrtf 音效。</span><span class="sxs-lookup"><span data-stu-id="67abe-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="67abe-414">[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)會以偵探的形式利用 hrtf 的聲音。</span><span class="sxs-lookup"><span data-stu-id="67abe-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="67abe-415">此偵探的語音是用來協助讓使用者注意到重要的線索, 就好像實際的人在聊天室一樣。</span><span class="sxs-lookup"><span data-stu-id="67abe-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="67abe-416">這可讓您更瞭解深度解決神秘的經驗。</span><span class="sxs-lookup"><span data-stu-id="67abe-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="67abe-417">第3部分-效能</span><span class="sxs-lookup"><span data-stu-id="67abe-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="67abe-418">CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="67abe-418">CPU usage</span></span>

<span data-ttu-id="67abe-419">使用空間音效時, 10-12 發射器會耗用大約 12% 的 CPU。</span><span class="sxs-lookup"><span data-stu-id="67abe-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="67abe-420">串流長音訊檔案</span><span class="sxs-lookup"><span data-stu-id="67abe-420">Stream long audio files</span></span>

<span data-ttu-id="67abe-421">音訊資料可能很大, 尤其是常見的取樣率 (44.1 和 48 kHz)。</span><span class="sxs-lookup"><span data-stu-id="67abe-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="67abe-422">一般的規則是, 應串流處理長度超過 5-10 秒的音訊檔案, 以減少應用程式記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="67abe-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="67abe-423">在 Unity 中, 您可以在檔案的匯入設定中, 標示要串流處理的音訊檔案。</span><span class="sxs-lookup"><span data-stu-id="67abe-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![音訊匯入設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="67abe-425">第5章-特殊效果</span><span class="sxs-lookup"><span data-stu-id="67abe-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="67abe-426">目標</span><span class="sxs-lookup"><span data-stu-id="67abe-426">Objectives</span></span>

* <span data-ttu-id="67abe-427">將深度新增至「魔術視窗」。</span><span class="sxs-lookup"><span data-stu-id="67abe-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="67abe-428">將使用者帶到虛擬世界。</span><span class="sxs-lookup"><span data-stu-id="67abe-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="67abe-429">魔術視窗</span><span class="sxs-lookup"><span data-stu-id="67abe-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="67abe-430">重要概念</span><span class="sxs-lookup"><span data-stu-id="67abe-430">Key Concepts</span></span>

* <span data-ttu-id="67abe-431">在隱藏的世界中建立視圖, 視覺上具吸引力。</span><span class="sxs-lookup"><span data-stu-id="67abe-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="67abe-432">當全息影像或使用者接近隱藏世界時, 新增音訊效果, 以增強真實性。</span><span class="sxs-lookup"><span data-stu-id="67abe-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="67abe-433">指示</span><span class="sxs-lookup"><span data-stu-id="67abe-433">Instructions</span></span>

* <span data-ttu-id="67abe-434">在 [階層] 面板中, 展開 [ **HologramCollection** ], 然後選取 [ **Underworld**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="67abe-435">展開 [ **Underworld** ], 然後選取 [ **VoiceSource**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="67abe-436">在 [偵測**器**] 面板中, 按一下 [**新增元件**] 並新增 [**使用者聲音效果**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="67abe-437">**Spatialize**元件將會新增至**VoiceSource**。</span><span class="sxs-lookup"><span data-stu-id="67abe-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="67abe-438">在**spatialize**中, 將 [**輸出**] 設定為 **[UserVoice (混音器)** ]。</span><span class="sxs-lookup"><span data-stu-id="67abe-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="67abe-439">核取 [ **Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="67abe-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="67abe-440">將**空間 Blend**滑杆拖曳到**3d**, 或在編輯方塊中輸入**1** 。</span><span class="sxs-lookup"><span data-stu-id="67abe-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="67abe-441">展開 [ **3D 音效設定**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="67abe-442">將 [ **Doppler 層級**] 設定為**0**。</span><span class="sxs-lookup"><span data-stu-id="67abe-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="67abe-443">在 [**使用者聲音效果**] 中, 將**父物件**從場景設定為**Underworld** 。</span><span class="sxs-lookup"><span data-stu-id="67abe-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="67abe-444">將 [**最大距離**] 設定為**1**。</span><span class="sxs-lookup"><span data-stu-id="67abe-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="67abe-445">設定 [**最大距離**] 可讓使用者在啟用效果之前, 先關閉使用者必須前往父物件的**聲音效果**。</span><span class="sxs-lookup"><span data-stu-id="67abe-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="67abe-446">在 [**使用者語音效果**] 中, 展開 [**一首哀歌參數**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="67abe-447">將**深度**設定為**0.1**。</span><span class="sxs-lookup"><span data-stu-id="67abe-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="67abe-448">設定**一下1個磁片**區, 再按2個**音量**, 然後將**3 個磁片**區帶到**0.8**。</span><span class="sxs-lookup"><span data-stu-id="67abe-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="67abe-449">將 [**原始音效磁片**區] 設定為**0.5**。</span><span class="sxs-lookup"><span data-stu-id="67abe-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="67abe-450">先前的設定會設定 Unity **AudioChorusFilter**的參數, 用來將豐富的語音新增至使用者的聲音。</span><span class="sxs-lookup"><span data-stu-id="67abe-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="67abe-451">在 [**使用者語音效果**] 中, 展開 [ **Echo 參數**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="67abe-452">將**延遲**設定為**300**</span><span class="sxs-lookup"><span data-stu-id="67abe-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="67abe-453">將 [**衰減比例**] 設定為**0.2**。</span><span class="sxs-lookup"><span data-stu-id="67abe-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="67abe-454">將 [**原始音效音量**] 設定為**0**。</span><span class="sxs-lookup"><span data-stu-id="67abe-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="67abe-455">先前的設定會設定用來讓使用者的語音回應的 Unity **AudioEchoFilter**參數。</span><span class="sxs-lookup"><span data-stu-id="67abe-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="67abe-456">使用者聲音效果腳本會負責:</span><span class="sxs-lookup"><span data-stu-id="67abe-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="67abe-457">測量使用者與附加腳本的**GameObject**之間的距離。</span><span class="sxs-lookup"><span data-stu-id="67abe-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="67abe-458">判斷使用者是否面臨**GameObject**。</span><span class="sxs-lookup"><span data-stu-id="67abe-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="67abe-459">無論距離為何, 使用者都必須面對 GameObject, 才會啟用效果。</span><span class="sxs-lookup"><span data-stu-id="67abe-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="67abe-460">對**spatialize**套用和設定**AudioChorusFilter**和**AudioEchoFilter** 。</span><span class="sxs-lookup"><span data-stu-id="67abe-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="67abe-461">停用篩選來停用效果。</span><span class="sxs-lookup"><span data-stu-id="67abe-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="67abe-462">使用者語音效果使用 Mic 串流選取器元件 (來自[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)) 來選取高品質的語音串流, 並將其路由傳送到 Unity 的音訊系統。</span><span class="sxs-lookup"><span data-stu-id="67abe-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="67abe-463">在 [階層] 面板中, 選取 [**管理員**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="67abe-464">在 [偵測**器**] 面板中, 展開 [**語音輸入處理常式**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="67abe-465">在 [**語音輸入處理常式**] 中, 展開 [**顯示 Underworld**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="67abe-466">將**No Function**變更為**UnderworldBase. OnEnable**。</span><span class="sxs-lookup"><span data-stu-id="67abe-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![關鍵字顯示 Underworld](images/showunderworld.png)

* <span data-ttu-id="67abe-468">展開 [**隱藏 Underworld**]。</span><span class="sxs-lookup"><span data-stu-id="67abe-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="67abe-469">將**No Function**變更為**UnderworldBase. OnDisable**。</span><span class="sxs-lookup"><span data-stu-id="67abe-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![關鍵字隱藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="67abe-471">組建和部署</span><span class="sxs-lookup"><span data-stu-id="67abe-471">Build and Deploy</span></span>

* <span data-ttu-id="67abe-472">如先前一樣, 在 Unity 中建立專案, 並在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="67abe-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="67abe-473">部署應用程式之後:</span><span class="sxs-lookup"><span data-stu-id="67abe-473">After the application is deployed:</span></span>

* <span data-ttu-id="67abe-474">臉部表面 (牆、樓層、桌子), 並說出「 *Show Underworld*」。</span><span class="sxs-lookup"><span data-stu-id="67abe-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="67abe-475">將會顯示 underworld, 並隱藏所有其他的全息影像。</span><span class="sxs-lookup"><span data-stu-id="67abe-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="67abe-476">如果您看不到 underworld, 請確定您面臨的是真實世界的表面。</span><span class="sxs-lookup"><span data-stu-id="67abe-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="67abe-477">一種 underworld 的全像投影, 並開始談。</span><span class="sxs-lookup"><span data-stu-id="67abe-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="67abe-478">音訊效果現已套用至您的語音!</span><span class="sxs-lookup"><span data-stu-id="67abe-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="67abe-479">關閉 underworld, 並留意效果不再套用的方式。</span><span class="sxs-lookup"><span data-stu-id="67abe-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="67abe-480">說「*隱藏 Underworld* 」以隱藏 Underworld。</span><span class="sxs-lookup"><span data-stu-id="67abe-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="67abe-481">Underworld 將會隱藏, 而先前隱藏的全息影像將會重新出現。</span><span class="sxs-lookup"><span data-stu-id="67abe-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="67abe-482">結束</span><span class="sxs-lookup"><span data-stu-id="67abe-482">The End</span></span>

<span data-ttu-id="67abe-483">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="67abe-483">Congratulations!</span></span> <span data-ttu-id="67abe-484">您現在已完成**MR 空間 220:空間音效**。</span><span class="sxs-lookup"><span data-stu-id="67abe-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="67abe-485">收聽世界, 讓您的經驗實現音效!</span><span class="sxs-lookup"><span data-stu-id="67abe-485">Listen to the world and bring your experiences to life with sound!</span></span>
