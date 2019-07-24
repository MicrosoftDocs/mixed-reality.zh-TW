---
title: 版本資訊-5 月2016
description: Windows 全像2016年5月版的 HoloLens 版本資訊更新。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 版本資訊, os, 功能, 組建, 平臺
ms.openlocfilehash: bc4e09c36a3ab6643be1144873a624fc5ed66e37
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524554"
---
# <a name="release-notes---may-2016"></a><span data-ttu-id="9069c-104">版本資訊-5 月2016</span><span class="sxs-lookup"><span data-stu-id="9069c-104">Release notes - May 2016</span></span>

<span data-ttu-id="9069c-105">HoloLens 小組致力於提供您最新功能開發的更新, 以及透過 Windows 測試人員計畫的主要修正程式。</span><span class="sxs-lookup"><span data-stu-id="9069c-105">The HoloLens team is committed to provide you with an update on our latest feature development and major fixes through the Windows Insider Program.</span></span> <span data-ttu-id="9069c-106">感謝您所有的建議, 我們會將您的意見反應提供給您。</span><span class="sxs-lookup"><span data-stu-id="9069c-106">Thanks to all your suggestions, we take your feedback to heart.</span></span> <span data-ttu-id="9069c-107">請透過意見反應中樞、[開發人員論壇](https://forums.hololens.com) [ @HoloLens和 Twitter ](https://twitter.com/hololens), 繼續[提供意見](give-us-feedback.md)反應給我們。</span><span class="sxs-lookup"><span data-stu-id="9069c-107">Please continue to [give us feedback](give-us-feedback.md) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span>

<span data-ttu-id="9069c-108">**發行版本:** Windows 全像5月2016更新 (**10.0.14342.1016**)</span><span class="sxs-lookup"><span data-stu-id="9069c-108">**Release version:** Windows Holographic May 2016 Update (**10.0.14342.1016**)</span></span>

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

<span data-ttu-id="9069c-109">若要更新為目前的版本, 請開啟 [*設定*] 應用程式, 移至 [*更新 & 安全性*], 然後選取 [*檢查更新*] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9069c-109">To update to the current release, open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="9069c-110">新功能</span><span class="sxs-lookup"><span data-stu-id="9069c-110">New features</span></span>

* <span data-ttu-id="9069c-111">您現在可以**同時在2d 視圖中執行最多三個應用程式**。</span><span class="sxs-lookup"><span data-stu-id="9069c-111">You can now **run up to three apps in 2D view simultaneously**.</span></span> <span data-ttu-id="9069c-112">這可讓 HoloLens 中的多工使用案例無限。</span><span class="sxs-lookup"><span data-stu-id="9069c-112">This enables endless use cases for multi-tasking in HoloLens.</span></span> <span data-ttu-id="9069c-113">在探索此航班的新功能時, 讓新的意見反應中樞具有探索」的清單。</span><span class="sxs-lookup"><span data-stu-id="9069c-113">Have the new Feedback Hub with the list of Quests open while exploring the new features on this flight.</span></span>

  <span data-ttu-id="9069c-114">![HoloLens 可以同時執行三個應用程式](images/img-3625-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9069c-114">![HoloLens can run three apps at the same time](images/img-3625-400px.jpg)</span></span><br>
  <span data-ttu-id="9069c-115">同時在2D 視圖中執行最多三個應用程式</span><span class="sxs-lookup"><span data-stu-id="9069c-115">Run up to three apps in 2D view simultaneously</span></span>

* <span data-ttu-id="9069c-116">我們已新增**語音命令**:</span><span class="sxs-lookup"><span data-stu-id="9069c-116">We've added new **voice commands**:</span></span>
   * <span data-ttu-id="9069c-117">請嘗試查看全像投影, 並說「臉部我」來旋轉</span><span class="sxs-lookup"><span data-stu-id="9069c-117">Try looking at a hologram and rotate it by saying "face me"</span></span>
   * <span data-ttu-id="9069c-118">藉由說出「大」或「較小」來變更其大小</span><span class="sxs-lookup"><span data-stu-id="9069c-118">Change its size by saying "bigger" or "smaller"</span></span>
   * <span data-ttu-id="9069c-119">藉由說「嘿 Cortana, 將*應用程式名稱*移到這裡」來移動應用程式。</span><span class="sxs-lookup"><span data-stu-id="9069c-119">Move an app by saying "Hey Cortana, move *app name* here."</span></span>
* <span data-ttu-id="9069c-120">我們已**更輕鬆地在 HoloLens 上進行開發**。</span><span class="sxs-lookup"><span data-stu-id="9069c-120">We've made **developing on HoloLens easier**.</span></span> <span data-ttu-id="9069c-121">您現在可以透過[Windows 裝置入口網站](using-the-windows-device-portal.md)流覽、上傳和下載檔案。</span><span class="sxs-lookup"><span data-stu-id="9069c-121">You can now browse, upload, and download files through the [Windows Device Portal](using-the-windows-device-portal.md).</span></span> <span data-ttu-id="9069c-122">您可以存取 [檔] 資料夾、[圖片] 資料夾, 以及任何您透過 Visual Studio 側載或部署之應用程式的本機儲存體。</span><span class="sxs-lookup"><span data-stu-id="9069c-122">You can access the Documents folder, Pictures folder, and the local storage for any app you side-loaded or deployed through Visual Studio.</span></span>
* <span data-ttu-id="9069c-123">**模擬器現在支援以 Microsoft 帳戶登入**, 就像您在實際的 HoloLens 上所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="9069c-123">The **emulator now supports log-in with a Microsoft Account** just like you would on a real HoloLens.</span></span> <span data-ttu-id="9069c-124">您可以從 [其他工具] 功能表 [> >] 加以啟用。</span><span class="sxs-lookup"><span data-stu-id="9069c-124">You can enable this from the Additional Tools menu ">>".</span></span>
* <span data-ttu-id="9069c-125">**2D 應用程式現在會在觀賞全螢幕影片時隱藏應用程式行和游標**, 以避免干擾。</span><span class="sxs-lookup"><span data-stu-id="9069c-125">**2D Apps now hide the app bar and cursor when watching video full screen** to avoid distraction.</span></span> <span data-ttu-id="9069c-126">透過這種方式, 您的影片觀賞體驗在 HoloLens 上會更有樂趣。</span><span class="sxs-lookup"><span data-stu-id="9069c-126">With this, your video watching experience will be even more enjoyable on HoloLens.</span></span>
* <span data-ttu-id="9069c-127">您也可以**釘選相片, 而不需要您世界中的應用程式行**。</span><span class="sxs-lookup"><span data-stu-id="9069c-127">You can also **pin photos without the app bar** in your world .</span></span>

  <span data-ttu-id="9069c-128">![針對2D 應用程式 (例如相片), 可以隱藏應用程式行](images/img-3626-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9069c-128">![The app bar can be hidden for 2D apps like photos](images/img-3626-400px.jpg)</span></span><br>
  <span data-ttu-id="9069c-129">應用程式行可針對具有2D 視圖的應用程式隱藏, 例如相片</span><span class="sxs-lookup"><span data-stu-id="9069c-129">The app bar can be hidden for apps with a 2D view, like Photos</span></span>
  
* <span data-ttu-id="9069c-130">檔案**選擇器**的運作方式就如同您在 HoloLens 上所預期的一樣。</span><span class="sxs-lookup"><span data-stu-id="9069c-130">**File picker** works just like you expect it to on HoloLens.</span></span>
* <span data-ttu-id="9069c-131">已更新**Edge 瀏覽器**來對應與桌面和手機一致的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="9069c-131">Updated **Edge browser** to map unified user experience with desktop and phone.</span></span> <span data-ttu-id="9069c-132">我們在新視窗中啟用了多個瀏覽器實例、自訂 HoloLens 新索引標籤頁、索引標籤查看和開啟, 以及 power & 效能改進。</span><span class="sxs-lookup"><span data-stu-id="9069c-132">We enabled multiple instances of your browser, custom HoloLens new tab page, tab peek, and open in new windows, along with power & performance improvements.</span></span>
* <span data-ttu-id="9069c-133">**Groove 音樂**應用程式現在已在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="9069c-133">**Groove Music** app is now on HoloLens.</span></span> <span data-ttu-id="9069c-134">請造訪 store 進行下載, 然後在背景嘗試播放。</span><span class="sxs-lookup"><span data-stu-id="9069c-134">Visit the store to download it and try playing in the background.</span></span>
* <span data-ttu-id="9069c-135">您可以輕鬆地自訂應用程式在世界中的相片順序。</span><span class="sxs-lookup"><span data-stu-id="9069c-135">You can easily customize how apps are arranged in your world.</span></span> <span data-ttu-id="9069c-136">只要按一下並拖曳中間垂直框線中的 circle, 即可嘗試在調整模式中**旋轉您的全息影像**。</span><span class="sxs-lookup"><span data-stu-id="9069c-136">Try **rotating your holograms** in adjust mode by simply click and drag on circle in the middle vertical wireframes.</span></span> <span data-ttu-id="9069c-137">您可能會注意到, 全息影像的**邊界方塊較緊密**, 以確保最大化的互動。</span><span class="sxs-lookup"><span data-stu-id="9069c-137">You might notice holograms have **tighter fitted bounding boxes** to ensure maximized interaction.</span></span> <span data-ttu-id="9069c-138">您也可以垂直調整所有平面應用程式的大小 (相片和全息影像應用程式除外)。</span><span class="sxs-lookup"><span data-stu-id="9069c-138">You can also resize all flat apps vertically (except Photos and Hologram apps).</span></span>

  <span data-ttu-id="9069c-139">![將影像放在世界上之後, 可以旋轉全像投影](images/img-3627-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9069c-139">![Holograms can be rotated after you place them in the world](images/img-3627-400px.jpg)</span></span><br>
  <span data-ttu-id="9069c-140">將全息影像放在世界上之後旋轉</span><span class="sxs-lookup"><span data-stu-id="9069c-140">Rotate holograms after you place them in your world</span></span>

* <span data-ttu-id="9069c-141">我們在此航班中做了許多**輸入改善**。</span><span class="sxs-lookup"><span data-stu-id="9069c-141">We've made a lot of **input improvement** in this flight.</span></span> <span data-ttu-id="9069c-142">您可以將一般藍牙滑鼠連線到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="9069c-142">You can connect a regular Bluetooth mouse to HoloLens.</span></span> <span data-ttu-id="9069c-143">Clicker 已經過微調, 可讓您調整使用 clicker 移動全息影像的大小 &。</span><span class="sxs-lookup"><span data-stu-id="9069c-143">The clicker has been fine tuned to enable resizing & moving holograms with a clicker.</span></span> <span data-ttu-id="9069c-144">鍵盤的執行效果也比以往更好。</span><span class="sxs-lookup"><span data-stu-id="9069c-144">Keyboard is also running better than ever.</span></span>
* <span data-ttu-id="9069c-145">現在您只要按下音量並同時往下移動, 就可以採用**混合的現實圖片**。</span><span class="sxs-lookup"><span data-stu-id="9069c-145">Now you can take **mixed reality pictures** by simply pressing down the volume up + volume down simultaneously.</span></span> <span data-ttu-id="9069c-146">您也可以將您混合現實的相片 & 影片分享到 Facebook、Twitter 和 YouTube。</span><span class="sxs-lookup"><span data-stu-id="9069c-146">You can also share your mixed reality captured photos & videos to Facebook, Twitter and YouTube.</span></span>
* <span data-ttu-id="9069c-147">**混合現實**影片的記錄長度上限已增加到五分鐘。</span><span class="sxs-lookup"><span data-stu-id="9069c-147">The maximum recording length of **mixed reality videos** has been increased to five minutes.</span></span>
* <span data-ttu-id="9069c-148">**相片應用程式**現在會從 OneDrive 串流影片, 而不需要在播放前下載整段影片。</span><span class="sxs-lookup"><span data-stu-id="9069c-148">**Photos app** now streams videos from OneDrive instead of having to download the entire video before playback.</span></span>
* <span data-ttu-id="9069c-149">我們已改善您**的全息影像在您離開時的位置**。</span><span class="sxs-lookup"><span data-stu-id="9069c-149">We've improved how your **holograms will be right where you left them**.</span></span> <span data-ttu-id="9069c-150">您也會看到重新連線至 Wi-fi 的選項, 並在 HoloLens 無法偵測到其所在位置時再試一次。</span><span class="sxs-lookup"><span data-stu-id="9069c-150">You will also be presented the option to re-connect to Wi-Fi and try again if HoloLens cannot detect where they are.</span></span>
* <span data-ttu-id="9069c-151">鍵盤具有改良的版面配置, 可讓您使用金鑰來輸入**電子郵件地址**, 以便您只需按一下就能進入最受歡迎的電子郵件網域。</span><span class="sxs-lookup"><span data-stu-id="9069c-151">The keyboard has an **improved layout for entering email address** with keys that allow you to enter the most popular email domains with a single click.</span></span>
* <span data-ttu-id="9069c-152">在 OOBE 期間, 更快的**應用程式註冊**和**時間區域自動偵測**, 為您提供最佳的第一個使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="9069c-152">Faster **app registration** and **auto detection of time zone** during OOBE, giving you the best first user experience.</span></span>
* <span data-ttu-id="9069c-153">**儲存體感知**可讓您透過 [設定] 應用程式中的系統和應用程式, 來查看剩餘和已使用的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="9069c-153">**Storage sense** allows you to view remaining and used disk space by the system and apps in the settings app.</span></span>
* <span data-ttu-id="9069c-154">我們已將「融合式意見反應」應用程式和內部中樞納入單一應用程式**意見反應中樞**, 這是可**提供意見**反應的「前往」工具、您喜愛的功能、不需要的功能, 或有可能更好的東西。</span><span class="sxs-lookup"><span data-stu-id="9069c-154">We have converged Feedback App and Inside Hub into a single app **Feedback Hub** that will be the go-to tool for **giving us feedback**, which features you love, which features you could do without, or when something could be better.</span></span> <span data-ttu-id="9069c-155">當您加入測試人員計畫時, 您可以隨時掌握**取得最新的 insider 新聞**、**評分組建**, 以及從意見反應中樞**探索」意見**反應。</span><span class="sxs-lookup"><span data-stu-id="9069c-155">When you join the Insider Program, you can keep up on **get latest Insider news**, **rate builds** and go on **feedback quests** from Feedback Hub.</span></span>
* <span data-ttu-id="9069c-156">我們也[發佈了已更新的 HoloLens 模擬器](install-the-tools.md)組建。</span><span class="sxs-lookup"><span data-stu-id="9069c-156">We've also [published an updated HoloLens Emulator](install-the-tools.md) build.</span></span>
* <span data-ttu-id="9069c-157">您的混合現實影片現在看起來較佳, 因為它是自動的**視頻穩定**。</span><span class="sxs-lookup"><span data-stu-id="9069c-157">Your mixed reality videos now look better due to automatic **video stabilization**.</span></span>

## <a name="major-fixes"></a><span data-ttu-id="9069c-158">主要修正</span><span class="sxs-lookup"><span data-stu-id="9069c-158">Major fixes</span></span>

<span data-ttu-id="9069c-159">我們已修正空格會變慢或偵測不正確的全息圖空間問題。</span><span class="sxs-lookup"><span data-stu-id="9069c-159">We fixed issues with hologram spaces where the spaces would be slow or incorrectly detected.</span></span> <span data-ttu-id="9069c-160">我們已修正關機問題, 這可能會在關機期間繼續嘗試啟動 shell。</span><span class="sxs-lookup"><span data-stu-id="9069c-160">We fixed a shutdown issue that could continue to try launching the shell during shutdown.</span></span>

<span data-ttu-id="9069c-161">我們已修正問題</span><span class="sxs-lookup"><span data-stu-id="9069c-161">We fixed an issue</span></span>
* <span data-ttu-id="9069c-162">這會封鎖繼續 XAML 應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="9069c-162">that blocks the ability to resume a XAML application.</span></span>
* <span data-ttu-id="9069c-163">當損毀時, 會留下黑色畫面和一些不規則線條。</span><span class="sxs-lookup"><span data-stu-id="9069c-163">where a crash would leave a black screen and some jagged lines.</span></span>
* <span data-ttu-id="9069c-164">使用某些應用程式時, 滾動有時會導致不正確的方向。</span><span class="sxs-lookup"><span data-stu-id="9069c-164">scrolling would sometimes stick in the wrong direction when using some apps.</span></span>
* <span data-ttu-id="9069c-165">電源 Led 可能表示裝置仍開啟時處於關閉狀態。</span><span class="sxs-lookup"><span data-stu-id="9069c-165">the power LEDs could indicate an off state when the device was still on.</span></span>
* <span data-ttu-id="9069c-166">從待命狀態繼續後, WiFi 可能會關閉。</span><span class="sxs-lookup"><span data-stu-id="9069c-166">WiFi could get turned off after resuming from standby.</span></span>
* <span data-ttu-id="9069c-167">Xbox 身分識別提供者會提供玩家代號設定, 然後停滯在迴圈中。</span><span class="sxs-lookup"><span data-stu-id="9069c-167">the Xbox identity provider offers gamertag setup and then gets stuck in a loop.</span></span>
* <span data-ttu-id="9069c-168">在 OneDrive 檔案選擇器中選取下載的檔案時, Shell 偶爾會損毀。</span><span class="sxs-lookup"><span data-stu-id="9069c-168">the Shell occasionally crashes when selecting a downloaded file in the OneDrive File Picker.</span></span>
* <span data-ttu-id="9069c-169">按住連結, 有時會開啟一個新的已中斷索引標籤, 並開啟內容功能表。</span><span class="sxs-lookup"><span data-stu-id="9069c-169">pressing and holding on a link sometimes both opens a new, broken tab and opens a context menu.</span></span>
* <span data-ttu-id="9069c-170">其中 windows 裝置入口網站不允許從50到80的 IPD 調整</span><span class="sxs-lookup"><span data-stu-id="9069c-170">where windows device portal didn’t allow IPD adjustments from 50 to 80</span></span>

<span data-ttu-id="9069c-171">我們已修正相片的問題, 其中</span><span class="sxs-lookup"><span data-stu-id="9069c-171">We fixed issues with Photos where</span></span>
* <span data-ttu-id="9069c-172">影像偶爾會因為忽略 [EXIF 方向] 屬性而顯示 [旋轉]。</span><span class="sxs-lookup"><span data-stu-id="9069c-172">an image would occasionally display rotated due to ignoring the EXIF orientation property.</span></span>
* <span data-ttu-id="9069c-173">它可能會在已釘選的相片上啟動時損毀。</span><span class="sxs-lookup"><span data-stu-id="9069c-173">it could crash during start-up on pinned Photos.</span></span>
* <span data-ttu-id="9069c-174">影片會在暫停後重新開機, 而不是從上次暫停的位置繼續。</span><span class="sxs-lookup"><span data-stu-id="9069c-174">videos would restart after pausing instead of continuing from where last paused.</span></span>
* <span data-ttu-id="9069c-175">共用影片的重新執行可能會在播放時共用。</span><span class="sxs-lookup"><span data-stu-id="9069c-175">replay of a shared video could be prevented if it was shared while playing.</span></span>
* <span data-ttu-id="9069c-176">混合現實捕捉記錄的開頭為 0.5-1 秒的僅音訊摘要。</span><span class="sxs-lookup"><span data-stu-id="9069c-176">Mixed Reality Capture recordings would begin with 0.5-1 second of audio only feed.</span></span>
* <span data-ttu-id="9069c-177">[同步處理] 按鈕會在初始 OneDrive 同步期間消失。</span><span class="sxs-lookup"><span data-stu-id="9069c-177">the Sync button disappears during initial OneDrive sync.</span></span>

<span data-ttu-id="9069c-178">我們已修正設定的問題, 其中</span><span class="sxs-lookup"><span data-stu-id="9069c-178">We fixed issues with settings where</span></span>
* <span data-ttu-id="9069c-179">環境變更時, 需要重新整理。</span><span class="sxs-lookup"><span data-stu-id="9069c-179">a refresh was needed when the environment changes.</span></span>
* <span data-ttu-id="9069c-180">鍵盤上的 ' Enter ' 不會像在某些對話方塊中按一下 [下一步] 一樣。</span><span class="sxs-lookup"><span data-stu-id="9069c-180">'Enter' on keyboard would not behave like clicking Next in some dialogs.</span></span>
* <span data-ttu-id="9069c-181">很難得知 clicker 的配對何時失敗。</span><span class="sxs-lookup"><span data-stu-id="9069c-181">it was hard to know when the clicker failed pairing.</span></span>
* <span data-ttu-id="9069c-182">它可能會因為 WiFi 中斷連線和連線而變得沒有回應。</span><span class="sxs-lookup"><span data-stu-id="9069c-182">it could become unresponsive with WiFi disconnect and connect.</span></span>

<span data-ttu-id="9069c-183">我們已修正 Cortana 的問題, 其中</span><span class="sxs-lookup"><span data-stu-id="9069c-183">We fixed issues with Cortana where</span></span>
* <span data-ttu-id="9069c-184">它可能會停滯, 而無法顯示接聽 UI。</span><span class="sxs-lookup"><span data-stu-id="9069c-184">it could get stuck displaying the Listening UI.</span></span>
* <span data-ttu-id="9069c-185">如果您對結束應用程式的要求可能是或否, 詢問「您的 Cortana, 我可以從獨佔模式應用程式取得哪些內容」會停滯。</span><span class="sxs-lookup"><span data-stu-id="9069c-185">asking "Hey Cortana, what can I say" from an exclusive mode app would get stuck if you answered maybe rather yes/no to the request to exit the app.</span></span>
* <span data-ttu-id="9069c-186">如果您要求 Cortana 進入睡眠狀態, 然後繼續進行, Cortana 接聽 UI 就不會正確地繼續。</span><span class="sxs-lookup"><span data-stu-id="9069c-186">the Cortana listening UI doesn't resume correctly if you ask Cortana to go to sleep and then resume.</span></span>
* <span data-ttu-id="9069c-187">查詢「我連接到什麼網路？」</span><span class="sxs-lookup"><span data-stu-id="9069c-187">the queries "What network am I connected to?"</span></span> <span data-ttu-id="9069c-188">「我已連線嗎？」</span><span class="sxs-lookup"><span data-stu-id="9069c-188">and the "Am I connected?"</span></span> <span data-ttu-id="9069c-189">當第一個網路設定檔回傳而沒有連線能力時, 可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="9069c-189">could fail when the first network profile comes back with no connectivity.</span></span>
* <span data-ttu-id="9069c-190">UI 旁邊在「接聽」, 但結束應用程式時, 會立即開始執行語音辨識。</span><span class="sxs-lookup"><span data-stu-id="9069c-190">the UI froze on "Listening" but upon exiting an app would immediately began doing speech recognition again.</span></span>
* <span data-ttu-id="9069c-191">在登出 Cortana 應用程式的情況下, 您將無法重新登入, 直到重新開機為止。</span><span class="sxs-lookup"><span data-stu-id="9069c-191">where signing out of the Cortana app wouldn't let you sign back into it until a reboot.</span></span>
* <span data-ttu-id="9069c-192">當混合現實 Capture UI 為作用中時, 不會啟動它。</span><span class="sxs-lookup"><span data-stu-id="9069c-192">it would not launch when Mixed Reality Capture UI was active.</span></span>

<span data-ttu-id="9069c-193">我們已修正 Visual Studio 的問題, 其中</span><span class="sxs-lookup"><span data-stu-id="9069c-193">We fixed issues with Visual Studio where</span></span>
* <span data-ttu-id="9069c-194">背景工作的調試失敗。</span><span class="sxs-lookup"><span data-stu-id="9069c-194">background task debugging did not work.</span></span>
* <span data-ttu-id="9069c-195">圖形偵錯工具中的框架分析無法正常執行。</span><span class="sxs-lookup"><span data-stu-id="9069c-195">frame analysis in the graphics debugger did not work.</span></span>
* <span data-ttu-id="9069c-196">除非您的專案 TargetPlatformVersion 設定為 10240, 否則 HoloLens 模擬器不會出現在 Visual Studio 的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="9069c-196">the HoloLens Emulator did not appear in the drop-down list for Visual Studio unless your project's TargetPlatformVersion was set to 10240.</span></span>

## <a name="changes-from-previous-release"></a><span data-ttu-id="9069c-197">先前版本的變更</span><span class="sxs-lookup"><span data-stu-id="9069c-197">Changes from previous release</span></span>
* <span data-ttu-id="9069c-198">Cortana 命令 [您**好的 cortana], 重新開機裝置**無法運作。</span><span class="sxs-lookup"><span data-stu-id="9069c-198">The Cortana command **Hey Cortana, reboot the device** does not work.</span></span> <span data-ttu-id="9069c-199">使用者可以說**cortana、restart**或**你好的 cortana, 重新開機裝置**。</span><span class="sxs-lookup"><span data-stu-id="9069c-199">User can say **Hey Cortana, restart** or **Hey Cortana, restart the device**.</span></span>
* <span data-ttu-id="9069c-200">已從產品移除 Kiosk 模式。</span><span class="sxs-lookup"><span data-stu-id="9069c-200">Kiosk mode has been removed from the product.</span></span>

## <a name="prior-release-notes"></a><span data-ttu-id="9069c-201">先前的版本資訊</span><span class="sxs-lookup"><span data-stu-id="9069c-201">Prior release notes</span></span>
* [<span data-ttu-id="9069c-202">版本資訊 - 2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="9069c-202">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="9069c-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9069c-203">See also</span></span>
* [<span data-ttu-id="9069c-204">HoloLens 的已知問題</span><span class="sxs-lookup"><span data-stu-id="9069c-204">HoloLens known issues</span></span>](hololens-known-issues.md)
* [<span data-ttu-id="9069c-205">安裝工具</span><span class="sxs-lookup"><span data-stu-id="9069c-205">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="9069c-206">Shell</span><span class="sxs-lookup"><span data-stu-id="9069c-206">Shell</span></span>](navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="9069c-207">更新混合實境的 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="9069c-207">Updating 2D UWP apps for mixed reality</span></span>](building-2d-apps.md)
* [<span data-ttu-id="9069c-208">硬體配件</span><span class="sxs-lookup"><span data-stu-id="9069c-208">Hardware accessories</span></span>](hardware-accessories.md)
* [<span data-ttu-id="9069c-209">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="9069c-209">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="9069c-210">語音輸入</span><span class="sxs-lookup"><span data-stu-id="9069c-210">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="9069c-211">將應用程式提交到 Windows Store</span><span class="sxs-lookup"><span data-stu-id="9069c-211">Submitting an app to the Windows Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="9069c-212">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="9069c-212">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
