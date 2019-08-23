---
title: 以位置為基礎的娛樂與 Windows Mixed Reality
description: 取得 Unity 中基礎全像原生物件的存取權。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: mixed reality、vr、lbe、location
ms.openlocfilehash: e23d17ff2b07c636c98a9f19a5dd20f4dc558bf7
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69983396"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a><span data-ttu-id="bf4c3-104">以位置為基礎的娛樂與 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bf4c3-104">Location Based Entertainment with Windows Mixed Reality</span></span>

<span data-ttu-id="bf4c3-105">過去幾年來, 我們在以位置為基礎的娛樂類別中目睹了大量的成長和創新。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-105">In the last couple of years, we have witnessed an incredible amount of growth and innovation in the Location Based Entertainment category.</span></span> <span data-ttu-id="bf4c3-106">傳統地點 (例如主題公園和 theatres) 已開始為現有的乘車和安裝提供可免費體驗的沉浸式多玩家體驗。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-106">Traditional venues like theme parks and theatres have started offering immersive, multi-player experiences as complimentary experiences to existing rides and installations.</span></span> <span data-ttu-id="bf4c3-107">新的操作員和地點為 masses 帶來了獨特的多 sensorial、多玩家體驗。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-107">New operators and venues are bringing unique multi-sensorial, multi-player experiences at an attractive price to the masses.</span></span> <span data-ttu-id="bf4c3-108">所有這些體驗都會推播信封, 以瞭解混合現實的可能性。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-108">All of these experiences are pushing the envelope for what’s possible with mixed reality.</span></span>

<span data-ttu-id="bf4c3-109">本檔是在以位置為基礎的娛樂類別中開始使用 Windows Mixed Reality 的指南。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-109">This document is a guide to get started with Windows Mixed Reality in the Location Based Entertainment category.</span></span> <span data-ttu-id="bf4c3-110">下列指導方針可能會另外適用于以位置為基礎的體驗 (例如訓練、產品設計或其他使用案例)。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-110">The guidance below may additionally be applicable to location-based experiences beyond entertainment such as training, product design or other use cases.</span></span>

## <a name="engineering-faq"></a><span data-ttu-id="bf4c3-111">工程常見問題</span><span class="sxs-lookup"><span data-stu-id="bf4c3-111">Engineering FAQ</span></span>

### <a name="hardware"></a><span data-ttu-id="bf4c3-112">硬體</span><span class="sxs-lookup"><span data-stu-id="bf4c3-112">Hardware</span></span>

<span data-ttu-id="bf4c3-113">**問題解答Microsoft 及其合作夥伴可以使用哪些硬體來進行設定？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-113">**Q: What hardware is available from Microsoft and its partners that I can use in my setup?**</span></span>

<span data-ttu-id="bf4c3-114">答：Microsoft 及其 OEM 合作夥伴提供了一套吸引人的裝置組合, 視您的需求而定。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-114">A: Microsoft and its OEM partners offer a compelling portfolio of devices to choose from depending on your needs.</span></span>  

<span data-ttu-id="bf4c3-115">如果您提供給客戶的體驗需要虛擬實境耳機, 則來自 HP、Samsung 和 Acer 的下列市場頭戴式耳機非常適合。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-115">If the experiences you’re providing to your customers require virtual reality headsets, the following in-market headsets from HP, Samsung and Acer are a great fit.</span></span> <span data-ttu-id="bf4c3-116">每個耳機都有自己的差異屬性。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-116">Each headset has their own differentiated attributes.</span></span> <span data-ttu-id="bf4c3-117">下列各項的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-117">More details on each below.</span></span>

<span data-ttu-id="bf4c3-118">HP 回音:[詳細資料](https://hp.com/go/Reverbpro)</span><span class="sxs-lookup"><span data-stu-id="bf4c3-118">HP Reverb: [Details](https://hp.com/go/Reverbpro)</span></span>

<span data-ttu-id="bf4c3-119">Samsung 電影對白 +:[詳細資料](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span><span class="sxs-lookup"><span data-stu-id="bf4c3-119">Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span></span>

<span data-ttu-id="bf4c3-120">Acer[詳細資料](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span><span class="sxs-lookup"><span data-stu-id="bf4c3-120">Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span></span>

<span data-ttu-id="bf4c3-121">如果您的位置專門從事需要使用「觀看」耳機的混合或擴充現實體驗, 您可以購買 Microsoft HoloLens 2 (現已開放訂購單)。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-121">If your location specializes in mixed or augmented reality experiences requiring the use of a see-through headset, you can procure the Microsoft HoloLens 2 (now open for pre-order interest).</span></span>  

<span data-ttu-id="bf4c3-122">HoloLens 2:[預先訂購的利息](https://www.microsoft.com/en-us/hololens/buy)</span><span class="sxs-lookup"><span data-stu-id="bf4c3-122">HoloLens 2: [Pre-order interest](https://www.microsoft.com/en-us/hololens/buy)</span></span>

<span data-ttu-id="bf4c3-123">如果您要試驗需要先進的電腦視覺、語音和本文追蹤的經驗, 您可能會發現 Azure Kinect DK 符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-123">If you’re experimenting with experiences that require advanced computer vision, speech and body tracking, you may find the Azure Kinect DK a fit for your needs.</span></span>  

<span data-ttu-id="bf4c3-124">Azure Kinect:[詳細資料](https://azure.microsoft.com/en-us/services/kinect-dk/)</span><span class="sxs-lookup"><span data-stu-id="bf4c3-124">Azure Kinect: [Details](https://azure.microsoft.com/en-us/services/kinect-dk/)</span></span>

<span data-ttu-id="bf4c3-125">**問題解答我可以使用哪些死忠電腦群組合來執行電腦行動網卡的 VR 體驗？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-125">**Q: What is the portfolio of backpack PCs I can use to run my PC-tethered VR experiences?**</span></span>

<span data-ttu-id="bf4c3-126">針對電腦行動網卡的 VR 體驗, 我們的 Oem 提供了絕佳的死忠電腦選擇, 專為該需求而打造。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-126">For PC-tethered VR experiences, our OEMs offer an incredible selection of backpack PCs built exactly for that need.</span></span>

<span data-ttu-id="bf4c3-127">HP 剛剛啟動了其 HP VR 死忠 G2, 這是世界上最強大的穿戴式電腦–已針對免費漫遊體驗優化, 現在提供了 30% 以上的 RTX 2080 GPU 功能。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-127">HP just launched their HP VR backpack G2, the world’s most powerful wearable PC – optimized for free-roam experiences, now with 30% more power with an RTX 2080 GPU inside.</span></span> [<span data-ttu-id="bf4c3-128">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bf4c3-128">Details</span></span>](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a><span data-ttu-id="bf4c3-129">安裝程式</span><span class="sxs-lookup"><span data-stu-id="bf4c3-129">Setup</span></span>

<span data-ttu-id="bf4c3-130">**問題解答如何更輕鬆地設定設定和自訂 LBE 的混合現實入口網站？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-130">**Q: How can I more easily configure setup and customize the Mixed Reality Portal for LBE?**</span></span>

>[!NOTE]
><span data-ttu-id="bf4c3-131">這項功能需要 version 2000.19061.1011.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-131">This feature requires version 2000.19061.1011.0 or greater.</span></span>  

<span data-ttu-id="bf4c3-132">您可能會發現您需要更多的混合現實入口網站自訂, 而不是通常透過應用程式來將應用程式部署到 kiosk 或自訂體驗。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-132">You may find that you need more customization of Mixed Reality Portal than is normally available through the app for deploying apps to kiosks or customized experiences.</span></span> <span data-ttu-id="bf4c3-133">混合現實入口網站的最新7月更新支援數個可透過設定檔執行下列動作的先進設定:</span><span class="sxs-lookup"><span data-stu-id="bf4c3-133">The latest July update of Mixed Reality Portal supports several advanced settings that can be via a configuration file to do the following:</span></span>  

<span data-ttu-id="bf4c3-134">允許失敗的系統檢查–安裝程式通常會先檢查電腦是否與 Windows Mixed Reality 相容, 再完成安裝程式。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-134">Allow failed system checks – normally the setup process checks the PC for compatibility with Windows Mixed Reality before completing setup.</span></span> <span data-ttu-id="bf4c3-135">若略過這種情況, 可能會在嘗試執行 Windows Mixed Reality 時發生問題 (如果有相容性問題)。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-135">Bypassing this may cause issues when trying to run Windows Mixed Reality if there are compatibility issues.</span></span>  

<span data-ttu-id="bf4c3-136">略過裝置附屬應用程式– DCA 提供由製造商提供的耳機特定設定步驟, 並可讓您更新耳機的固件。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-136">Skip Device Companion App – the DCA provides headset-specific setup steps provided by the manufacturer and allows for updating the headset’s firmware.</span></span>  

<span data-ttu-id="bf4c3-137">略過房間設定–不會收到提示以建立房間界限, 您可以直接進入位於站上/待命模式的頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-137">Skip room setup – instead of being prompted to create a room boundary, you can proceed directly into the headset in Seated/Standing mode.</span></span>  

<span data-ttu-id="bf4c3-138">略過從存放區安裝應用程式-一般安裝程式會安裝數個存放區應用程式, 包括3D 檢視器和 Edge 360 檢視器附加元件。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-138">Skip installing apps from the Store - normal setup installs several Store apps including 3D Viewer and the Edge 360 Viewer add-on.</span></span> <span data-ttu-id="bf4c3-139">這會略過這些應用程式的安裝, 但您可能會遺失裝置功能。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-139">This will skip the install of these apps, but you may be missing device functionality.</span></span>  

<span data-ttu-id="bf4c3-140">以全螢幕顯示預覽–混合式現實入口網站會預設為在使用耳機時, 于桌上型電腦上以全螢幕顯示耳機預覽。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-140">Show preview in full screen – Mixed Reality Portal will default to showing the headset preview in full-screen on the desktop PC while the headset is in use.</span></span>  

<span data-ttu-id="bf4c3-141">隱藏新的您的面板-這會防止新的 [在您啟動混合現實入口網站時] 面板擴充。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-141">Hide New for you side panel – this prevent the New for you panel from being expanded on launch of Mixed Reality Portal.</span></span>  

#### <a name="how-to-configure"></a><span data-ttu-id="bf4c3-142">如何設定:</span><span class="sxs-lookup"><span data-stu-id="bf4c3-142">How to configure:</span></span>  

<span data-ttu-id="bf4c3-143">若要設定其中任何一項設定, 您必須在此目錄下建立名為_UserConfig_的檔案: _$env:\\ LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState_</span><span class="sxs-lookup"><span data-stu-id="bf4c3-143">To set any of these configurations, you need to create a file called _UserConfig.json_ under this directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="bf4c3-144">對於大部分使用者來說, 這看起來像是 _\<C:\Users\\ username > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState_</span><span class="sxs-lookup"><span data-stu-id="bf4c3-144">For most users this will look like _C:\Users\<username>\AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="bf4c3-145">JSON 檔案應該有下列內容, 並針對您想要啟用的上述任何設定設定「true」:</span><span class="sxs-lookup"><span data-stu-id="bf4c3-145">The JSON file should have the below contents with “true” set for any of the above settings you want enabled:</span></span>  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
<span data-ttu-id="bf4c3-146">**問題解答有關于設定 playspace 的指引嗎？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-146">**Q: Is there any guidance on configuring the playspace?**</span></span>

<span data-ttu-id="bf4c3-147">答：設定 playspace 應如同使用取用者安裝經驗一樣。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-147">A: Configuring a playspace should be done as you would with a consumer setup experience.</span></span> <span data-ttu-id="bf4c3-148">房間設定程式也可讓您定義房間界限。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-148">The Room Setup process will also let you define your room boundaries.</span></span> <span data-ttu-id="bf4c3-149">您可以在[這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)閱讀更多有關設定房間界限的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-149">More details on configuring room boundaries can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="bf4c3-150">如上述檔中所述, 最大合理單一座標 playspace 是大約5mx5m。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-150">As discussed in the above document the maximum reasonable single coordinate playspace is around 5mx5m.</span></span> <span data-ttu-id="bf4c3-151">如果您想要有更大的區域, 您可以利用 Windows 全像 API 堆疊中的空間錨點功能。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-151">If you want to have a larger area you can make use of the Spatial Anchors capability in the Windows Holographic API stack.</span></span> <span data-ttu-id="bf4c3-152">使用此 API 將需要在您所產生的體驗中進行自訂工程。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-152">Using this API will require custom engineering in the experiences you are producing.</span></span>  

<span data-ttu-id="bf4c3-153">如需如何針對不同空間大小優化內容的詳細資訊, 請參閱[這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-153">More details on how to optimize your content for different space sizes can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems).</span></span>
 

<span data-ttu-id="bf4c3-154">**問題解答我的空間太大, 當我嘗試設定界限的經驗時, 就會發生錯誤。若要設定我的大型免費漫遊體驗, 我該怎麼做？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-154">**Q: My space is too large and I’m running into errors when I try to set up a Standing experience with boundaries. What should I do to setup my large free-roam experience work?**</span></span>

<span data-ttu-id="bf4c3-155">答：若要設定比 ~ 18x18ft 更大的空間, 您將無法使用系統所提供的界限體驗。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-155">A: To setup a larger space than ~18x18ft you won’t be able to use the boundary experience provided by the system.</span></span>  <span data-ttu-id="bf4c3-156">界限系統依賴單一固定座標「錨點」, 而當使用者太遠離開中央階段錨點時, 可能會變得不穩定。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-156">The boundary systems relies on leveraging a single fixed coordinate “anchor”, which can become unstable when a user is too far from the center stage anchor.</span></span> 

<span data-ttu-id="bf4c3-157">相反地, 您可以設定「固定」模式, 這不會顯示界限或設定階段界限或 playspace。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-157">Instead, you can setup “seated” mode, which will not display the boundary or configure a stage bounds or playspace.</span></span>  <span data-ttu-id="bf4c3-158">然後, 您必須在應用程式內設定多個空間錨點, 以參考實體界限區域。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-158">Then, you’ll need to configure multiple spatial anchors within the app to reference physical boundary areas.</span></span> 

<span data-ttu-id="bf4c3-159">應用程式開發人員負責顯示必要的保護措施, 讓使用者不會與實體的周圍環境衝突。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-159">The application developer is responsible to display necessary safeguards so that users don’t collide with physical surroundings.</span></span>  <span data-ttu-id="bf4c3-160">這些可能是經驗或自訂遊戲界限視覺效果中的數位牆。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-160">These could be digital walls within the experience or a customized game boundary visual.</span></span> 

<span data-ttu-id="bf4c3-161">您可以在[這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)找到使用 WMR 設定房間界限的指引。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-161">Guidance on setting up the room boundary with WMR can be found [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="bf4c3-162">**問題解答Playspace 的來源在哪裡？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-162">**Q: Where is the origin of the playspace?**</span></span>

<span data-ttu-id="bf4c3-163">答：Playspace 的來源是由房間設定經驗決定, 特別是在安裝期間按下中間按鈕時的 HMD 位置。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-163">A: The origin of the playspace is determined by the Room Setup experience, more specifically the HMD position when the Center button is pressed during setup.</span></span> 

### <a name="multi-player-setup"></a><span data-ttu-id="bf4c3-164">多玩家設定</span><span class="sxs-lookup"><span data-stu-id="bf4c3-164">MULTI-PLAYER SETUP</span></span>

<span data-ttu-id="bf4c3-165">**問題解答我要在我的場所部署多玩家體驗。Windows Mixed Reality 是否支援這種情況？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-165">**Q: I’m deploying a multi-player experience in at my venue. Is that supported on Windows Mixed Reality?**</span></span>

<span data-ttu-id="bf4c3-166">答：Mixed Reality 空間資料封裝工具是一種搶鮮版 (Beta) 功能, 可讓您將空間資料從一部電腦移植到另一部電腦, 以在相同的空間中將多個玩家當地語系化。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-166">A: The Mixed Reality Spatial Data Packager tool is a beta feature that allows localizing multiple players in the same space by enabling porting of the spatial data from one PC to another.</span></span> <span data-ttu-id="bf4c3-167">您可以在[這裡](mixedrealityspatialdatapackager.md)存取工具並深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-167">You can access the tool and learn more about it [here](mixedrealityspatialdatapackager.md).</span></span>

### <a name="tracking"></a><span data-ttu-id="bf4c3-168">修訂</span><span class="sxs-lookup"><span data-stu-id="bf4c3-168">TRACKING</span></span>

<span data-ttu-id="bf4c3-169">Q:Windows Mixed Reality 耳機中的追蹤技術如何運作？</span><span class="sxs-lookup"><span data-stu-id="bf4c3-169">Q: How does the tracking technology in the Windows Mixed Reality headsets work?</span></span>  

<span data-ttu-id="bf4c3-170">Mixed Reality 與 HoloLens 共用相同的追蹤技術。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-170">Mixed Reality shares the same tracking technology as the HoloLens.</span></span> <span data-ttu-id="bf4c3-171">若要深入瞭解內部追蹤系統, 請參閱[這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system)的檔。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-171">To learn more about the inside-out tracking system, check out the documentation [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system).</span></span>

<span data-ttu-id="bf4c3-172">如需更高層級空間對應系統運作方式的說明, 請參閱[這裡](spatial-mapping-design.md)的說明。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-172">For a description of how the higher-level spatial mapping system works you can read our description [here](spatial-mapping-design.md).</span></span>

<span data-ttu-id="bf4c3-173">**問題解答取得可靠的追蹤磁片區是否有任何最佳作法？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-173">**Q: Are there any best practices for getting a reliable tracking volume?**</span></span>

<span data-ttu-id="bf4c3-174">若要最佳設定追蹤成功的環境, 您可以閱讀這[篇文章](environment-considerations-for-hololens.md)中的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-174">To best configure the environment for tracking success, you can read best practices in this [post](environment-considerations-for-hololens.md).</span></span>

<span data-ttu-id="bf4c3-175">**問題解答在倉儲級別的空間或優化中追蹤是否有任何特定的細節需要考慮？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-175">**Q: Are there any specific nuances with tracking in warehouse-scale spaces or optimizations to consider?**</span></span>

<span data-ttu-id="bf4c3-176">答：下列作法可協助取得更可靠的追蹤磁片區:</span><span class="sxs-lookup"><span data-stu-id="bf4c3-176">A: The following practices can help with getting a more reliable tracking volume:</span></span>  

<span data-ttu-id="bf4c3-177">在房間中提供多個位置重迭的各種功能, 可協助追蹤系統取得穩固的鎖定。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-177">Providing a variety of features in the room that overlap at multiple positions will help the tracking system get a solid lock.</span></span> <span data-ttu-id="bf4c3-178">請考慮隨機繪製 splatters 和影線, 而不是使用實線輪廓樣式線條。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-178">Think of random paint splatters and hatching rather than using solid contour style lines.</span></span> 

<span data-ttu-id="bf4c3-179">盡可能減少您區域中的動態光源範圍。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-179">Minimize the dynamic range of lighting in your area where possible.</span></span> <span data-ttu-id="bf4c3-180">混合現實 Hmd 上的追蹤攝影機不是 HDR, 而且具有 AGC (自動取得) 和 AEC (自動曝光) 來處理不同光源。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-180">The tracking cameras on our Mixed Reality HMDs are not HDR and have AGC (auto gain) and AEC (auto exposure) going in order to deal with different lighting.</span></span> <span data-ttu-id="bf4c3-181">視表面光線、模式和對比的分佈而定, AGC 或 AEC 可能會結束您的所有白或黑室, 而這可能會使您的功能相對「色彩」而沖蝕。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-181">Depending on the distribution of surface light, patterns and contrast, either AGC or AEC may conclude you’re in a pretty much all white or black room which can wash out your features that may be in the opposite “color”.</span></span> <span data-ttu-id="bf4c3-182">如果您嘗試將內部圖片放在具有亮日光背後的外部視窗前方, 並調整曝光, 讓您可以查看外的詳細資料, 則內部的所有內容都是 underexposed 和黑色。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-182">If you are trying to take an interior picture in front of an exterior window with bright daylight behind and you adjust exposure so you can see detail outside, then everything on the interior is underexposed and black.</span></span> <span data-ttu-id="bf4c3-183">或者, 如果設定為 [內部], 則外部的所有專案現在都會 overexposed, 而且全部都是白色。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-183">Or if set for inside, then everything outside is now overexposed and all white.</span></span>  

<span data-ttu-id="bf4c3-184">如果追蹤攝影機有時可能會原因的房間 (甚至是額外負荷) 中的聚光燈, 這可能會使追蹤攝影機的 AEC/AGC 混淆。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-184">Spotlights in a room (even overhead) that are in view if tracking cameras can sometimes be culprits which confuse the AEC/AGC of the tracking cameras.</span></span> <span data-ttu-id="bf4c3-185">平面/散射光源有助於。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-185">Flat/diffused lighting helps.</span></span>  

### <a name="mixed-reality-cloud-services-and-azure"></a><span data-ttu-id="bf4c3-186">混合現實雲端服務和 AZURE</span><span class="sxs-lookup"><span data-stu-id="bf4c3-186">MIXED REALITY CLOUD SERVICES AND AZURE</span></span> 

<span data-ttu-id="bf4c3-187">**問題解答Microsoft Azure 可以如何協助我的企業規模？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-187">**Q: How can Microsoft Azure help my business scale?**</span></span>

<span data-ttu-id="bf4c3-188">答：以 Azure 為基礎的現場和遠端系統管理可協助您的企業成為資料驅動、降低營運成本, 並在現有和新的位置調整部署規模。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-188">A: Azure based onsite and remote management can help your business be data-driven, reduce operational costs and scale deployment across existing and new locations.</span></span> <span data-ttu-id="bf4c3-189">Azure 雲端服務 (例如 Azure 儲存體、Azure Functions、App Service、Azure 網路和 IOT 中樞) 可協助下列使用案例:</span><span class="sxs-lookup"><span data-stu-id="bf4c3-189">Azure cloud services such as Azure Storage, Azure Functions, App Service, Azure Networking and IOT Hub can help with the following use cases:</span></span>  

<span data-ttu-id="bf4c3-190">遠端裝置部署 & 管理</span><span class="sxs-lookup"><span data-stu-id="bf4c3-190">Remote Device Deployment & Management</span></span> 

<span data-ttu-id="bf4c3-191">即時現場分析</span><span class="sxs-lookup"><span data-stu-id="bf4c3-191">Real Time Onsite Analytics</span></span> 

<span data-ttu-id="bf4c3-192">智慧型的適應性 LBE 遊戲</span><span class="sxs-lookup"><span data-stu-id="bf4c3-192">Intelligent Adaptable LBE Gameplay</span></span> 

<span data-ttu-id="bf4c3-193">LBE 內容串流和部署</span><span class="sxs-lookup"><span data-stu-id="bf4c3-193">LBE Content Streaming and Deployment</span></span> 

<span data-ttu-id="bf4c3-194">LBE Player 喜好設定熱度圖</span><span class="sxs-lookup"><span data-stu-id="bf4c3-194">LBE Player Preference Heatmap</span></span> 

<span data-ttu-id="bf4c3-195">LBE 保留與預約系統</span><span class="sxs-lookup"><span data-stu-id="bf4c3-195">LBE Reservation and Booking System</span></span> 

<span data-ttu-id="bf4c3-196">**問題解答我正在開發空間 MMOG, 以部署大量的空間。協助我管理內容和物件持續性的任何服務？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-196">**Q: I’m developing a spatial MMOG to deploy over a massive footprint. Any services that help me manage my content and object persistence?**</span></span>

<span data-ttu-id="bf4c3-197">答：Azure 空間錨點是全新的混合現實服務, 可在 HoloLens、iOS 和 Android 裝置上啟用多使用者、空間感知的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-197">A: Azure Spatial Anchors is a new Mixed Reality service that enables multi-user, spatially aware mixed reality experiences across HoloLens, iOS and Android devices.</span></span> <span data-ttu-id="bf4c3-198">您可以在[這裡](https://azure.microsoft.com/en-us/services/spatial-anchors/)深入瞭解 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-198">You can learn more about Azure Spatial Anchors [here](https://azure.microsoft.com/en-us/services/spatial-anchors/).</span></span>

<span data-ttu-id="bf4c3-199">**問題解答.我們的場地專門從事多玩家體驗, 而我想要專注于內容和前端開發的開發時間。是否有可協助我啟動或卸載後端開發的供應專案？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-199">**Q. Our venue specializes in multi-player experiences and I’d like to focus our development time on content and front-end development. Are there offerings that can help me bootstrap or offload backend development?**</span></span>

<span data-ttu-id="bf4c3-200">答：Azure PlayFab 是適用于即時遊戲的完整後端平臺。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-200">A: Azure PlayFab is a complete backend platform for live games.</span></span> <span data-ttu-id="bf4c3-201">您可以在[這裡](https://playfab.com/)深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-201">You can learn more about it [here](https://playfab.com/).</span></span>

### <a name="misc"></a><span data-ttu-id="bf4c3-202">其他</span><span class="sxs-lookup"><span data-stu-id="bf4c3-202">Misc</span></span>

<span data-ttu-id="bf4c3-203">**問題解答我使用 SteamVR 來部署我的經驗。Windows Mixed Reality 與 SteamVR 搭配使用嗎？**</span><span class="sxs-lookup"><span data-stu-id="bf4c3-203">**Q: I use SteamVR to deploy my experiences. Does Windows Mixed Reality work with SteamVR?**</span></span>

<span data-ttu-id="bf4c3-204">答：適用于 SteamVR 的 windows Mixed Reality 可讓使用者在 Windows Mixed Reality 沉浸式耳機上執行 SteamVR 體驗。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-204">A: Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="bf4c3-205">[在這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)深入瞭解 STEAMVR with WMR。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-205">Learn more about SteamVR with WMR [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span></span>

### <a name="support-and-community"></a><span data-ttu-id="bf4c3-206">支援和社區</span><span class="sxs-lookup"><span data-stu-id="bf4c3-206">Support and community</span></span>  

<span data-ttu-id="bf4c3-207">以下是一些實用的資源, 可與我們小組的主題專家互動、取得疑難排解支援, 以及貢獻更廣泛的混合現實開發人員。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-207">Below are a few helpful resources to engage with subject matter experts on our team, get troubleshooting support, and contribute to the broader mixed reality dev community.</span></span>  

<span data-ttu-id="bf4c3-208">如果您遇到任何公開發行的功能問題, 請使用意見反應中樞提出錯誤。如需相關指引, 請參閱此[頁面](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback)。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-208">If you run into issues with any publicly released features, please file a bug using Feedback Hub.For guidance, please refer to this [page](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span>

<span data-ttu-id="bf4c3-209">如需 WMR 的其他疑難排解協助, 請[提出支援要求](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782)以與我們的客戶支援小組聯繫。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-209">For additional troubleshooting help with WMR please get in touch with our customer support team by filing a [support request](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).</span></span>

<span data-ttu-id="bf4c3-210">加入我們的 HoloDevelopers 時差頻道, 與開發人員共同作業, 與小組的主題專家合作: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span><span class="sxs-lookup"><span data-stu-id="bf4c3-210">Join our HoloDevelopers Slack channel to engage with the developers working on mixed reality and subject matter experts from the team: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span></span>

<span data-ttu-id="bf4c3-211">Twitter遵循我們的混合現實開發人員關係小組, 取得新聞、活動和更新@MxdRealityDev</span><span class="sxs-lookup"><span data-stu-id="bf4c3-211">Twitter: Follow our Mixed Reality Developer Relations team for news, events and updates @MxdRealityDev</span></span> 

<span data-ttu-id="bf4c3-212">如果您的工作時間是在三藩市或前後, 則 Microsoft Reactor 一律會發生一些問題。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-212">If you happen to be in or around San Francisco, there’s always something going on at the Microsoft Reactor.</span></span> <span data-ttu-id="bf4c3-213">您可以在[這裡](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco)看到我們的事件行事曆。</span><span class="sxs-lookup"><span data-stu-id="bf4c3-213">You can see our calendar of events [here](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco).</span></span>