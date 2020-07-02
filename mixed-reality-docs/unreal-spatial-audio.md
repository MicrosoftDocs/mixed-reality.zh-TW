---
title: Unreal 中的空間音訊
description: 概述 Unreal Engine 的空間音訊外掛程式。
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 串流, 遠端, 混合實境, 開發, 開始使用, 功能, 新專案, 模擬器, 文件, 指南, 功能, 全像投影, 遊戲開發
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446789"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="5909a-104">Unreal 中的空間音訊</span><span class="sxs-lookup"><span data-stu-id="5909a-104">Spatial Audio in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="5909a-105">概觀</span><span class="sxs-lookup"><span data-stu-id="5909a-105">Overview</span></span>

<span data-ttu-id="5909a-106">不同於視覺，人類可聽到來自周遭 360 度的聲音。</span><span class="sxs-lookup"><span data-stu-id="5909a-106">Unlike vision, humans hear in 360 degree surround sound.</span></span> <span data-ttu-id="5909a-107">空間音效會模擬人類聽覺的運作方式，提供識別真實世界中的發聲位置所需的提示。</span><span class="sxs-lookup"><span data-stu-id="5909a-107">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="5909a-108">在混合實境應用程式中新增空間音效後，將可加強使用者體驗的沉浸程度。</span><span class="sxs-lookup"><span data-stu-id="5909a-108">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your users experience.</span></span>  

<span data-ttu-id="5909a-109">高品質的空間音效處理是很複雜的，因此，HoloLens 2 隨附了專用硬體來處理這些音效物件。</span><span class="sxs-lookup"><span data-stu-id="5909a-109">High quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="5909a-110">您必須先在 Unreal 專案中安裝 **MicrosoftSpatialSound** 外掛程式，才可存取此硬體處理支援。</span><span class="sxs-lookup"><span data-stu-id="5909a-110">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="5909a-111">本文將逐步引導您完成該外掛程式的安裝和設定，並為您深入介紹在 Unreal Engine 中使用空間音效所需的資源。</span><span class="sxs-lookup"><span data-stu-id="5909a-111">This article will walk you through the installation and configuration of that plugin and point you towards more in-depth resources for using spatial sound in the Unreal engine.</span></span> 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="5909a-112">安裝 Microsoft 空間音效外掛程式</span><span class="sxs-lookup"><span data-stu-id="5909a-112">Installing the Microsoft Spatial Sound plugin</span></span> 

<span data-ttu-id="5909a-113">將空間音效新增至專案的第一個步驟，是安裝 Microsoft 空間音效外掛程式；您可以透過下列方式找到此外掛程式：</span><span class="sxs-lookup"><span data-stu-id="5909a-113">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span> 

1. <span data-ttu-id="5909a-114">按一下 [編輯] > [外掛程式]，並在搜尋方塊中搜尋 **MicrosoftSpatialSound**。</span><span class="sxs-lookup"><span data-stu-id="5909a-114">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span> 
2. <span data-ttu-id="5909a-115">選取 **MicrosoftSpatialSound** 外掛程式中的 [已啟用] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5909a-115">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span> 
3. <span data-ttu-id="5909a-116">在 [外掛程式] 頁面中選取 [立即重新啟動]，將 Unreal 編輯器重新啟動。</span><span class="sxs-lookup"><span data-stu-id="5909a-116">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span> 

> [!NOTE]
> <span data-ttu-id="5909a-117">若您尚未依照 Unreal 教學課程系列的 **[初始化您的專案](unreal-uxt-ch2.md)** 一節中的指示，安裝 **Microsoft Windows Mixed Reality** 和 **HoloLens** 外掛程式，您必須加以安裝。</span><span class="sxs-lookup"><span data-stu-id="5909a-117">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Unreal 空間音訊外掛程式](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="5909a-119">編輯器重新啟動後，您的專案即設定完成。</span><span class="sxs-lookup"><span data-stu-id="5909a-119">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="5909a-120">設定 HoloLens 2 平台的空間化外掛程式</span><span class="sxs-lookup"><span data-stu-id="5909a-120">Setting the spatialization plugin for HoloLens 2 platform</span></span>
<span data-ttu-id="5909a-121">空間化外掛程式的設定須就個別平台來執行。</span><span class="sxs-lookup"><span data-stu-id="5909a-121">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="5909a-122">您可以啟用適用於 HoloLens 2 的 Microsoft 空間音效外掛程式，方法是：</span><span class="sxs-lookup"><span data-stu-id="5909a-122">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="5909a-123">選取 [編輯] > [專案設定] 並捲動至 [平台]，然後按一下 [HoloLens]。</span><span class="sxs-lookup"><span data-stu-id="5909a-123">Selecting **Edit > Project Settings**, scrolling to **Platforms** and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="5909a-124">展開 [音訊] 屬性，並將 [空間化外掛程式] 欄位設定為 [Microsoft 空間音效]。</span><span class="sxs-lookup"><span data-stu-id="5909a-124">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![適用於 HoloLens 平台的空間化外掛程式](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="5909a-126">如果您要在桌上型電腦的 Unreal 編輯器中預覽您的應用程式，您必須對 **Windows** 平台重複上述步驟：</span><span class="sxs-lookup"><span data-stu-id="5909a-126">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![適用於 Windows 平台的空間化外掛程式](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="5909a-128">在工作站上啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="5909a-128">Enabling spatial audio on your workstation</span></span>
<span data-ttu-id="5909a-129">Windows 桌面版依預設會停用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="5909a-129">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="5909a-130">您可以透過下列方式加以啟用：</span><span class="sxs-lookup"><span data-stu-id="5909a-130">You can enable it by:</span></span>
* <span data-ttu-id="5909a-131">以滑鼠右鍵按一下工作列中的 [磁碟區] 圖示。</span><span class="sxs-lookup"><span data-stu-id="5909a-131">Right-clicking on the **volume** icon in the task bar.</span></span> 
    + <span data-ttu-id="5909a-132">選擇 [空間音效] -> [Windows Sonic 耳機版]，以便在 HoloLens 2 上聽到最佳呈現的音效。</span><span class="sxs-lookup"><span data-stu-id="5909a-132">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![空間化外掛程式](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="5909a-134">只有您要在 Unreal 編輯器中測試您的專案時，才需要進行此設定。</span><span class="sxs-lookup"><span data-stu-id="5909a-134">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="5909a-135">建立衰減物件</span><span class="sxs-lookup"><span data-stu-id="5909a-135">Creating Attenuation objects</span></span>
<span data-ttu-id="5909a-136">在您安裝並設定必要的外掛程式後：</span><span class="sxs-lookup"><span data-stu-id="5909a-136">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="5909a-137">在 [放置動作項目] 視窗中搜尋 [環境音效] 動作項目，並將其拖曳至 [場景] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="5909a-137">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![新增環境音效動作項目](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="5909a-139">讓 [環境音效] 動作項目成為場景中視覺元素的子系。</span><span class="sxs-lookup"><span data-stu-id="5909a-139">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span> 
    * <span data-ttu-id="5909a-140">環境音效動作項目依預設不會有任何視覺呈現，因此您只會聽到其在場景中的所在位置傳來的聲音。</span><span class="sxs-lookup"><span data-stu-id="5909a-140">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="5909a-141">將其附加至視覺元素，您就可看到該動作項目，並像任何其他資產一樣加以移動。</span><span class="sxs-lookup"><span data-stu-id="5909a-141">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="5909a-142">以滑鼠右鍵按一下 [內容瀏覽器]，然後選取 [建立進階資產] -> [音效] -> [音效衰減]：</span><span class="sxs-lookup"><span data-stu-id="5909a-142">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![建立音效衰減資產](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="5909a-144">以滑鼠右鍵按一下 [內容瀏覽器] 視窗中的 [音效衰減] 資產，然後選取 [編輯] 選項以顯示 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5909a-144">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="5909a-145">將 [空間化方法] 切換為 [雙聲道]。</span><span class="sxs-lookup"><span data-stu-id="5909a-145">Switch the **Spatialization Method** to **Binaural**.</span></span>

![設定空間化方法](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="5909a-147">選取 [環境音效] 動作項目，並向下捲動至 [詳細資料] 面板中的 [衰減] 區段。</span><span class="sxs-lookup"><span data-stu-id="5909a-147">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span> 
    * <span data-ttu-id="5909a-148">將 [衰減設定] 屬性設定為您所建立的 [音效衰減] 資產。</span><span class="sxs-lookup"><span data-stu-id="5909a-148">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![設定衰減設定](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="5909a-150">藉由更新環境音效動作項目的 [音效] 屬性以指定所要使用的 SoundAsset 檔案，藉以設定要附加至環境音效動作項目的 [音效資產]。</span><span class="sxs-lookup"><span data-stu-id="5909a-150">Set the **Sound Asset** you want to attach to the Ambient Sound actor by updating the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![設定音效資產](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> <span data-ttu-id="5909a-152">SoundAsset 檔案必須是單聲道，才能使用 Microsoft 空間音效外掛程式進行空間化。</span><span class="sxs-lookup"><span data-stu-id="5909a-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="5909a-153">您可以將滑鼠游標移至 [內容瀏覽器] 視窗中的資產上方，以尋找音效檔案屬性，如下列螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="5909a-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![新的音效衰減資產](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="5909a-155">一切都設定完成後，就可以使用 HoloLens 2 上的專用硬體卸載支援將環境音效空間化。</span><span class="sxs-lookup"><span data-stu-id="5909a-155">Once all of this is configured the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="5909a-156">設定空間化的物件</span><span class="sxs-lookup"><span data-stu-id="5909a-156">Configuring objects for spatialization</span></span>
<span data-ttu-id="5909a-157">使用空間音訊時，表示您將負責管理音效在虛擬環境中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="5909a-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="5909a-158">您主要的工作重心，是要建立在使用者靠近時發出較大聲響、並在使用者遠離時較小聲的音效物件。</span><span class="sxs-lookup"><span data-stu-id="5909a-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="5909a-159">這就是所謂的音效衰減，聽起來會像是音效物件置於固定之處。</span><span class="sxs-lookup"><span data-stu-id="5909a-159">This is referred to as sound attenuation, making sounds appear as if they are positioned in a fixed spot.</span></span>

<span data-ttu-id="5909a-160">所有衰減物件都附有下列可修改的設定：</span><span class="sxs-lookup"><span data-stu-id="5909a-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="5909a-161">距離</span><span class="sxs-lookup"><span data-stu-id="5909a-161">Distance</span></span>
* <span data-ttu-id="5909a-162">空間化</span><span class="sxs-lookup"><span data-stu-id="5909a-162">Spatialization</span></span>
* <span data-ttu-id="5909a-163">空氣吸收</span><span class="sxs-lookup"><span data-stu-id="5909a-163">Air Absorption</span></span>
* <span data-ttu-id="5909a-164">聽覺焦點</span><span class="sxs-lookup"><span data-stu-id="5909a-164">Listener Focus</span></span>
* <span data-ttu-id="5909a-165">殘響傳送</span><span class="sxs-lookup"><span data-stu-id="5909a-165">Reverb Send</span></span>
* <span data-ttu-id="5909a-166">遮蔽</span><span class="sxs-lookup"><span data-stu-id="5909a-166">Occlusion</span></span>

<span data-ttu-id="5909a-167">[Unreal 中的音效衰減](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html)提供每個主題的詳細資料和實作細節。</span><span class="sxs-lookup"><span data-stu-id="5909a-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>


## <a name="see-also"></a><span data-ttu-id="5909a-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5909a-168">See also</span></span>
* [<span data-ttu-id="5909a-169">空間音效</span><span class="sxs-lookup"><span data-stu-id="5909a-169">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="5909a-170">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="5909a-170">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="5909a-171">MR Spatial 220：空間音效</span><span class="sxs-lookup"><span data-stu-id="5909a-171">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)