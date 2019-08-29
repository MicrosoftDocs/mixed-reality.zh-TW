---
title: 效果
description: 校準您的 IPD (interpupillary 距離) 可以改善視覺效果的品質。 HoloLens 和 Windows Mixed Reality 的沉浸式耳機都提供自訂 IPD 的方式。
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 校正, 舒適, 視覺效果, 品質, ipd
ms.openlocfilehash: e86319dadeda02f71427b87980268eaf18942c49
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122083"
---
# <a name="improve-visual-quality-and-comfort"></a><span data-ttu-id="a1cc8-105">改善視覺品質和舒適</span><span class="sxs-lookup"><span data-stu-id="a1cc8-105">Improve visual quality and comfort</span></span>
<span data-ttu-id="a1cc8-106">HoloLens、HoloLens 2 和 Windows Mixed Reality 沉浸式耳機提供不同的方式來改善視覺效果的品質。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-106">HoloLens, HoloLens 2 and Windows Mixed Reality immersive headsets offer different ways to improve the quality of the visual experience.</span></span> 

## <a name="hololens-2"></a><span data-ttu-id="a1cc8-107">Hololens 2</span><span class="sxs-lookup"><span data-stu-id="a1cc8-107">Hololens 2</span></span>

### <a name="calibration"></a><span data-ttu-id="a1cc8-108">效果</span><span class="sxs-lookup"><span data-stu-id="a1cc8-108">Calibration</span></span>

<span data-ttu-id="a1cc8-109">Hololens 2 的設計目的是為客戶提供最高品質的視覺效果影像和緩和。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-109">Hololens 2 is designed to provide the highest quality visual imagery and comfort for our customers.</span></span> <span data-ttu-id="a1cc8-110">眼睛追蹤技術是用來改善在虛擬環境中查看和互動的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-110">Eye tracking technology is used to improve the user experience of seeing and interacting with the virtual environment.</span></span>  

<span data-ttu-id="a1cc8-111">在 HoloLens 2 上, 系統會提示您在裝置設定期間校準您的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-111">On HoloLens 2, you'll be prompted to calibrate your visuals during device setup.</span></span> <span data-ttu-id="a1cc8-112">系統會要求使用者查看一組 fixation 目標。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-112">Users are asked to look at a set of fixation targets.</span></span> <span data-ttu-id="a1cc8-113">這可讓裝置調整影像的呈現方式, 以確保正確定位的全息影像、舒適的3D 觀賞體驗, 以及改良的顯示品質。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-113">This allows the device to adjust the rendering of holograms to the user to ensure accurately positioned holograms, a comfortable 3D viewing experience and improved display quality.</span></span> <span data-ttu-id="a1cc8-114">所有的調整會即時進行, 而不需要手動調整。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-114">All adjustments happen on-the-fly without the need for manual tuning.</span></span> <span data-ttu-id="a1cc8-115">藉由使用眼睛做為地標, 裝置會個別調整為每位使用者, 而且視覺效果會隨著耳機在使用中稍微移動而調整。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-115">By using the eyes as landmarks, the device is individually adjusted to every user, and visuals are tuned as the headset shifts slightly throughout use.</span></span> <span data-ttu-id="a1cc8-116">系統會在內部使用眼睛追蹤, 而開發人員則不需要採取任何動作來運用這項功能。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-116">Eye position tracking is used internally by the system and developers don’t need to do anything to leverage this capability.</span></span> <span data-ttu-id="a1cc8-117">事實上, 開發人員無法使用這項資訊。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-117">In fact, this information is not available to developers.</span></span>
<span data-ttu-id="a1cc8-118">請參閱[眼睛追蹤 api](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) , 以深入瞭解眼睛追蹤系統提供給開發人員的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-118">Please refer to the [Eye Tracking APIs](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) to learn more about the type of data the eye tracking system provides to developers.</span></span>

<span data-ttu-id="a1cc8-119">在 Hololens 2 上, 執行校正也可以確保每一位使用者都能進行精確的眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-119">On Hololens 2, performing the calibration also ensures accurate eye-gaze tracking for every user.</span></span> <span data-ttu-id="a1cc8-120">眼球追蹤可讓應用程式即時追蹤使用者的視線方向。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-120">Eye tracking enables applications to track where the user is looking in real time.</span></span> <span data-ttu-id="a1cc8-121">這是開發人員可以利用的主要功能, 在全像攝影體驗中啟用全新的內容、人類瞭解及互動。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-121">This is the main capability developers can leverage to enable a whole new level of context, human understanding and interactions within the holographic experience.</span></span>  

<span data-ttu-id="a1cc8-122">校正資料會儲存在本機裝置上, 而且不會與任何帳戶資訊相關聯。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-122">The calibration data is stored locally on the device and is not associated with any account information.</span></span> <span data-ttu-id="a1cc8-123">沒有任何已使用裝置而未進行校正的記錄。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-123">There is no record of who has used the device without calibration.</span></span> <span data-ttu-id="a1cc8-124">這表示當使用者第一次使用裝置時, 以及選擇不進行校正或校正不成功時, 系統會提示他們進行校準。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-124">This means that users will get prompted to calibrate when they use the device for the first time, as well as users who opted out of calibration previously or if the calibration was unsuccessful.</span></span> <span data-ttu-id="a1cc8-125">在 [**設定** > ] [**隱私權** > **監控**] 中, 您一律可以從裝置中刪除校正資料。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-125">The calibration data can always be deleted from the device in **Settings** > **Privacy** > **Eye Tracker**.</span></span> 

### <a name="calibration-failures"></a><span data-ttu-id="a1cc8-126">校正失敗</span><span class="sxs-lookup"><span data-stu-id="a1cc8-126">Calibration failures</span></span>
<span data-ttu-id="a1cc8-127">校正應該適用于大部分的使用者, 但在某些情況下, 使用者可能無法成功校準。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-127">Calibration should work for most users, but there are cases in which the user might be unable to calibrate successfully.</span></span>  
<span data-ttu-id="a1cc8-128">一些校正失敗的範例是因為:</span><span class="sxs-lookup"><span data-stu-id="a1cc8-128">Some examples of calibration failures are due to:</span></span>
- <span data-ttu-id="a1cc8-129">使用者有注意力, 而且在校正體驗期間不會查看校正目標</span><span class="sxs-lookup"><span data-stu-id="a1cc8-129">The user got distracted and didn't look at the calibration targets during the calibration experience</span></span>
- <span data-ttu-id="a1cc8-130">已變更或有劃痕的裝置面板或裝置面板未正確定位</span><span class="sxs-lookup"><span data-stu-id="a1cc8-130">Dirty or scratched device visor or device visor not positioned properly</span></span> 
- <span data-ttu-id="a1cc8-131">某些類型的連絡人鏡頭和眼鏡 (彩色連絡人鏡頭, 部分 toric 連絡人鏡頭, IR 封鎖眼鏡, 一些高處方眼鏡, 太陽眼鏡等等)</span><span class="sxs-lookup"><span data-stu-id="a1cc8-131">Certain types of contact lenses and glasses (colored contact lenses, some toric contact lenses, IR blocking glasses, some high prescription glasses, sunglasses, etc.)</span></span>
- <span data-ttu-id="a1cc8-132">中途或有劃痕的眼鏡</span><span class="sxs-lookup"><span data-stu-id="a1cc8-132">Dirty or scratched glasses</span></span>
- <span data-ttu-id="a1cc8-133">更明顯的構成, 某些 eyelash 擴充功能</span><span class="sxs-lookup"><span data-stu-id="a1cc8-133">More pronounced makeup, some eyelash extensions</span></span>
- <span data-ttu-id="a1cc8-134">眼睛和/或裝置面板遮蔽 (頭髮、一些粗眼鏡的框架)</span><span class="sxs-lookup"><span data-stu-id="a1cc8-134">Occlusions of eye and/or device visor (hair, some thick eyeglasses frames)</span></span>
- <span data-ttu-id="a1cc8-135">眼睛生理學、特定的眼睛和 (或) 眼睛 (一些狹窄的眼睛、長 eyelashes、amblyopia、nystagmus、LASIK 或其他眼睛 surgeries 的一些案例等等)</span><span class="sxs-lookup"><span data-stu-id="a1cc8-135">Eye physiology, certain eye conditions and/or eye surgery (some narrow eyes, long eyelashes, amblyopia, nystagmus, some cases of LASIK or other eye surgeries, etc.)</span></span>

<span data-ttu-id="a1cc8-136">如果校正不成功, 請嘗試下列其中一個修正:</span><span class="sxs-lookup"><span data-stu-id="a1cc8-136">If calibration is unsuccessful, try one of these fixes:</span></span> 
- <span data-ttu-id="a1cc8-137">清理您的裝置面板</span><span class="sxs-lookup"><span data-stu-id="a1cc8-137">Clean your device visor</span></span>
- <span data-ttu-id="a1cc8-138">清理您的眼鏡</span><span class="sxs-lookup"><span data-stu-id="a1cc8-138">Clean your glasses</span></span>
- <span data-ttu-id="a1cc8-139">將您的裝置面板全部推送到</span><span class="sxs-lookup"><span data-stu-id="a1cc8-139">Push your device visor all the way in</span></span>
- <span data-ttu-id="a1cc8-140">請確定沒有任何阻礙感應器或您的眼睛 (例如, 頭髮)</span><span class="sxs-lookup"><span data-stu-id="a1cc8-140">Make sure nothing is obstructing the sensors or your eyes (e.g., hair)</span></span> 
- <span data-ttu-id="a1cc8-141">請確定您的房間內有足夠的光線, 而且您不是在直接陽光下</span><span class="sxs-lookup"><span data-stu-id="a1cc8-141">Make sure there is enough light in your room and that you are not under direct sunlight</span></span>
- <span data-ttu-id="a1cc8-142">請確定您在校正期間仔細遵循目標</span><span class="sxs-lookup"><span data-stu-id="a1cc8-142">Make sure you are carefully following the targets during calibration</span></span>

<span data-ttu-id="a1cc8-143">如果您遵循所有方針, 而且校正仍然失敗, 您可以在 [**設定** > ] [**系統** > **校正**] 中停用校正提示:「*當新人員使用此 Hololens 時, 會自動要求執行眼睛校正*」功能。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-143">If you followed all guidelines and the calibration is still failing, you can disable the calibration prompt in **Settings** > **System** > **Calibration**: *"When a new person uses this Hololens, automatically ask to run eye calibration"* should be turned off.</span></span> <span data-ttu-id="a1cc8-144">請瞭解, 這可能會導致更糟的全息影像轉譯品質和 discomfort。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-144">Please understand that this might result in worse hologram rendering quality and discomfort.</span></span>

### <a name="launching-the-calibration-app-from-settings"></a><span data-ttu-id="a1cc8-145">從設定啟動校正應用程式</span><span class="sxs-lookup"><span data-stu-id="a1cc8-145">Launching the calibration app from Settings</span></span>
1. <span data-ttu-id="a1cc8-146">移至 HoloLens 2 上的 [設定] 頁面</span><span class="sxs-lookup"><span data-stu-id="a1cc8-146">Go to the Settings page on your HoloLens 2</span></span>
    * <span data-ttu-id="a1cc8-147">使用 [*開始手勢]* 以顯示 [開始][功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-147">Use the *"Start Gesture"* to bring up the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span> <span data-ttu-id="a1cc8-148">或者, 您也可以直接說 *「移至開始」* 。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-148">Alternatively, you can also simply say *"go to start"*.</span></span>
    * <span data-ttu-id="a1cc8-149">如果**設定**未釘選到 [啟動], 請選取 [**所有應用程式**] 以查看所有應用程式</span><span class="sxs-lookup"><span data-stu-id="a1cc8-149">If **Settings** isn't pinned to Start, select **All Apps** to view all apps</span></span>
    * <span data-ttu-id="a1cc8-150">啟動**設定**</span><span class="sxs-lookup"><span data-stu-id="a1cc8-150">Launch **Settings**</span></span>
2. <span data-ttu-id="a1cc8-151">流覽至 [**系統** > **校正** > ] [**眼睛校正**], 然後選取 [**執行眼校正**]</span><span class="sxs-lookup"><span data-stu-id="a1cc8-151">Navigate to **System** > **Calibration** > **Eye Calibration** and select **Run eye calibration**</span></span>


### <a name="calibration-when-sharing-a-devicesession"></a><span data-ttu-id="a1cc8-152">共用裝置/會話時的校正</span><span class="sxs-lookup"><span data-stu-id="a1cc8-152">Calibration when sharing a device/session</span></span>
<span data-ttu-id="a1cc8-153">Hololens 2 可以在人員之間共用, 而不需要每個人完成裝置設定體驗。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-153">Hololens 2 can be shared between people without the need for each person to go through the device setup experience.</span></span>
<span data-ttu-id="a1cc8-154">如果使用者是裝置的新手, 則 Hololens 2 會在裝置放在前端時, 提示使用者校準視覺效果。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-154">Hololens 2 will prompt the user to calibrate visuals when the device is put on the head if the user is new to the device.</span></span> <span data-ttu-id="a1cc8-155">如果使用者先前已校正裝置上的視覺效果, 則會順暢地調整顯示品質, 並在使用者將裝置放在前端時, 取得舒適的觀賞體驗。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-155">If the user has previously calibrated visuals on the device, the display will be seamlessly adjusted for quality and a comfortable viewing experience when the user puts the device on the head.</span></span> 


## <a name="hololens-v1"></a><span data-ttu-id="a1cc8-156">HoloLens (v1)</span><span class="sxs-lookup"><span data-stu-id="a1cc8-156">HoloLens (v1)</span></span>
<span data-ttu-id="a1cc8-157">校準您的 IPD (interpupillary 距離) 可以改善視覺效果的品質。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-157">Calibrating your IPD (interpupillary distance) can improve the quality of your visuals.</span></span>

### <a name="during-setup"></a><span data-ttu-id="a1cc8-158">在安裝期間</span><span class="sxs-lookup"><span data-stu-id="a1cc8-158">During setup</span></span>

![第二步的 IPD 手指對齊畫面](images/ipd-finger-alignment-300px.jpg)<br>

<span data-ttu-id="a1cc8-160">*第二步的 IPD 手指對齊畫面*</span><span class="sxs-lookup"><span data-stu-id="a1cc8-160">*IPD finger-alignment screen at second step*</span></span>

<span data-ttu-id="a1cc8-161">在 HoloLens 上, 系統會提示您在安裝期間校準您的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-161">On HoloLens, you'll be prompted to calibrate your visuals during setup.</span></span> <span data-ttu-id="a1cc8-162">這可讓裝置根據使用者的[interpupillary 距離](https://en.wikipedia.org/wiki/Interpupillary_distance)(IPD) 調整全息顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-162">This allows the device to adjust hologram display according to the user's [interpupillary distance](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span></span> <span data-ttu-id="a1cc8-163">使用不正確的 IPD, 全息影像可能會顯示不穩定或不正確的距離。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-163">With an incorrect IPD, holograms may appear unstable or at an incorrect distance.</span></span>

<span data-ttu-id="a1cc8-164">在 Cortana 引進之後, 第一個設定步驟是校正。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-164">After Cortana introduces herself, the first setup step is calibration.</span></span> <span data-ttu-id="a1cc8-165">建議您在此設定階段完成校正步驟, 但可以略過, 直到 Cortana 提示您說「略過」繼續進行。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-165">It's recommended that you complete the calibration step during this setup phase, but it can be skipped by waiting until Cortana prompts you to say "Skip" to move on.</span></span>

<span data-ttu-id="a1cc8-166">系統會要求使用者將其手指與一系列六個目標密切配合。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-166">Users are asked to align their finger with a series of six targets per eye.</span></span> <span data-ttu-id="a1cc8-167">在此過程中, HoloLens 會為使用者設定正確的 IPD。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-167">Through this process, HoloLens sets the correct IPD for the user.</span></span> <span data-ttu-id="a1cc8-168">如果需要更新或調整新使用者的校正, 可以使用校正應用程式在安裝程式之外執行。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-168">If the calibration needs to be updated or adjusted for a new user, it can be run outside of setup using the Calibration app.</span></span>

### <a name="calibration-app"></a><span data-ttu-id="a1cc8-169">校正應用程式</span><span class="sxs-lookup"><span data-stu-id="a1cc8-169">Calibration app</span></span>

<span data-ttu-id="a1cc8-170">透過校正應用程式可以隨時執行校正。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-170">Calibration can be performed any time through the Calibration app.</span></span> <span data-ttu-id="a1cc8-171">根據預設, 會安裝校正應用程式, 並可從 [開始] 功能表或透過 [設定] 應用程式存取。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-171">The Calibration app is installed by default and may be accessed from the Start menu, or through the Settings app.</span></span> <span data-ttu-id="a1cc8-172">如果您想要改善視覺效果的品質, 或為新使用者校準視覺效果, 建議使用校正。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-172">Calibration is recommended if you'd like to improve the quality of your visuals or calibrate visuals for a new user.</span></span>

<span data-ttu-id="a1cc8-173">**從開始啟動應用程式**</span><span class="sxs-lookup"><span data-stu-id="a1cc8-173">**Launching the app from Start**</span></span>
1. <span data-ttu-id="a1cc8-174">使用[bloom](gestures.md#bloom)來取得 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-174">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="a1cc8-175">選取 **+** 以查看所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-175">Select **+** to view all apps.</span></span>
3. <span data-ttu-id="a1cc8-176">啟動**校正**。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-176">Launch **Calibration**.</span></span>

![從 shell 存取校正應用程式](images/calibration-shell.png)

![在啟動後顯示為即時 Cube 的校正應用程式](images/calibration-livecube-200px.png)

<span data-ttu-id="a1cc8-179">**從設定啟動應用程式**</span><span class="sxs-lookup"><span data-stu-id="a1cc8-179">**Launching the app from Settings**</span></span>
1. <span data-ttu-id="a1cc8-180">使用[bloom](gestures.md#bloom)來取得 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-180">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="a1cc8-181">如果 **+** **設定**未釘選到 [啟動], 請選取此值來查看所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-181">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="a1cc8-182">啟動**設定**。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-182">Launch **Settings**.</span></span>
4. <span data-ttu-id="a1cc8-183">流覽至 [**系統** > **公用程式**], 然後選取 [**開啟校正**]。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-183">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

![從設定應用程式啟動校正應用程式](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a><span data-ttu-id="a1cc8-185">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="a1cc8-185">Immersive headsets</span></span>

<span data-ttu-id="a1cc8-186">若要變更頭戴式裝置內的 IPD, 請開啟 [設定] 應用程式, 並流覽至 [**混合現實** > **頭戴式**裝置] 顯示並移動滑杆控制項。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-186">To change IPD within your headset, open the Settings app and navigate to **Mixed reality** > **Headset display** and move the slider control.</span></span> <span data-ttu-id="a1cc8-187">您會在頭戴式裝置上即時看到變更。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-187">You’ll see the changes in real time in your headset.</span></span> <span data-ttu-id="a1cc8-188">如果您知道 IPD, 也許是從造訪 optometrist, 您也可以直接輸入它。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-188">If you know your IPD, maybe from a visit to the optometrist, you can enter it directly as well.</span></span>

<span data-ttu-id="a1cc8-189">您也可以前往電腦上的 [**設定** > ] [**混合現實** > **頭戴式**裝置] 顯示來調整此設定。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-189">You can also adjust this setting by going to **Settings** > **Mixed reality** > **Headset display** on your PC.</span></span>

<span data-ttu-id="a1cc8-190">如果您的耳機不支援 IPD 自訂, 則會停用此設定。</span><span class="sxs-lookup"><span data-stu-id="a1cc8-190">If your headset does not support IPD customization, this setting will be disabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1cc8-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1cc8-191">See also</span></span>
* [<span data-ttu-id="a1cc8-192">HoloLens 的環境考量</span><span class="sxs-lookup"><span data-stu-id="a1cc8-192">Environment considerations for HoloLens</span></span>](environment-considerations-for-hololens.md)
