---
title: 版本資訊-2016 5 月
description: HoloLens 版本資訊適用於 Windows Holographic 可能 2016年更新。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 版本資訊、 作業系統、 功能、 組建、 平台
ms.openlocfilehash: bc4e09c36a3ab6643be1144873a624fc5ed66e37
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596452"
---
# <a name="release-notes---may-2016"></a><span data-ttu-id="d56ef-104">版本資訊-2016 5 月</span><span class="sxs-lookup"><span data-stu-id="d56ef-104">Release notes - May 2016</span></span>

<span data-ttu-id="d56ef-105">HoloLens 小組致力於提供您在我們的最新的功能開發及重大修正程式，透過 Windows Insider 計劃的更新。</span><span class="sxs-lookup"><span data-stu-id="d56ef-105">The HoloLens team is committed to provide you with an update on our latest feature development and major fixes through the Windows Insider Program.</span></span> <span data-ttu-id="d56ef-106">感謝您所有的建議，我們需要您的意見反應核心。</span><span class="sxs-lookup"><span data-stu-id="d56ef-106">Thanks to all your suggestions, we take your feedback to heart.</span></span> <span data-ttu-id="d56ef-107">請繼續[提供意見反應](give-us-feedback.md)意見反應中樞，透過[開發人員論壇](https://forums.hololens.com)並[透過 Twitter @HoloLens ](https://twitter.com/hololens)。</span><span class="sxs-lookup"><span data-stu-id="d56ef-107">Please continue to [give us feedback](give-us-feedback.md) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span>

<span data-ttu-id="d56ef-108">**發行版本：** Windows 全像攝影版 2016 年更新 (**10.0.14342.1016**)</span><span class="sxs-lookup"><span data-stu-id="d56ef-108">**Release version:** Windows Holographic May 2016 Update (**10.0.14342.1016**)</span></span>

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

<span data-ttu-id="d56ef-109">若要更新目前的版本中，開啟*設定*應用程式，移至*更新與安全性*，然後選取*檢查更新* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d56ef-109">To update to the current release, open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="d56ef-110">新功能</span><span class="sxs-lookup"><span data-stu-id="d56ef-110">New features</span></span>

* <span data-ttu-id="d56ef-111">您現在可以**2D 檢視中執行最多三個應用程式時，也將同時**。</span><span class="sxs-lookup"><span data-stu-id="d56ef-111">You can now **run up to three apps in 2D view simultaneously**.</span></span> <span data-ttu-id="d56ef-112">這可讓多工在 HoloLens 永無止盡的使用案例。</span><span class="sxs-lookup"><span data-stu-id="d56ef-112">This enables endless use cases for multi-tasking in HoloLens.</span></span> <span data-ttu-id="d56ef-113">有新的意見反應中樞習開啟時探索此航班的新功能的清單。</span><span class="sxs-lookup"><span data-stu-id="d56ef-113">Have the new Feedback Hub with the list of Quests open while exploring the new features on this flight.</span></span>

  <span data-ttu-id="d56ef-114">![HoloLens 可以同時執行三個應用程式](images/img-3625-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d56ef-114">![HoloLens can run three apps at the same time](images/img-3625-400px.jpg)</span></span><br>
  <span data-ttu-id="d56ef-115">在 2D 檢視中同時執行最多三個應用程式</span><span class="sxs-lookup"><span data-stu-id="d56ef-115">Run up to three apps in 2D view simultaneously</span></span>

* <span data-ttu-id="d56ef-116">我們已新增**語音命令**:</span><span class="sxs-lookup"><span data-stu-id="d56ef-116">We've added new **voice commands**:</span></span>
   * <span data-ttu-id="d56ef-117">嘗試查看雷射和旋轉所說 「 我遇到 「</span><span class="sxs-lookup"><span data-stu-id="d56ef-117">Try looking at a hologram and rotate it by saying "face me"</span></span>
   * <span data-ttu-id="d56ef-118">說出 「 更大 」 或 「 小 」 變更其大小</span><span class="sxs-lookup"><span data-stu-id="d56ef-118">Change its size by saying "bigger" or "smaller"</span></span>
   * <span data-ttu-id="d56ef-119">移動應用程式，指出 「 嘿 Cortana 移動*應用程式名稱*這裡。 」</span><span class="sxs-lookup"><span data-stu-id="d56ef-119">Move an app by saying "Hey Cortana, move *app name* here."</span></span>
* <span data-ttu-id="d56ef-120">我們已**HoloLens 更容易開發**。</span><span class="sxs-lookup"><span data-stu-id="d56ef-120">We've made **developing on HoloLens easier**.</span></span> <span data-ttu-id="d56ef-121">現在可以瀏覽、 上傳，並透過下載檔案[Windows Device Portal](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="d56ef-121">You can now browse, upload, and download files through the [Windows Device Portal](using-the-windows-device-portal.md).</span></span> <span data-ttu-id="d56ef-122">您可以透過 Visual Studio 來存取文件 資料夾、 圖片 資料夾和您側載或部署任何應用程式的本機儲存體。</span><span class="sxs-lookup"><span data-stu-id="d56ef-122">You can access the Documents folder, Pictures folder, and the local storage for any app you side-loaded or deployed through Visual Studio.</span></span>
* <span data-ttu-id="d56ef-123">**模擬器現在支援使用登入 Microsoft 帳戶**就像真正的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d56ef-123">The **emulator now supports log-in with a Microsoft Account** just like you would on a real HoloLens.</span></span> <span data-ttu-id="d56ef-124">您可以從 [其他工具] 功能表啟用 「 >>"。</span><span class="sxs-lookup"><span data-stu-id="d56ef-124">You can enable this from the Additional Tools menu ">>".</span></span>
* <span data-ttu-id="d56ef-125">**2D 應用程式現在會隱藏的應用程式列和資料指標時觀賞影片的全螢幕**以避免干擾。</span><span class="sxs-lookup"><span data-stu-id="d56ef-125">**2D Apps now hide the app bar and cursor when watching video full screen** to avoid distraction.</span></span> <span data-ttu-id="d56ef-126">以此方式，您的視訊看體驗將會更愉悅 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="d56ef-126">With this, your video watching experience will be even more enjoyable on HoloLens.</span></span>
* <span data-ttu-id="d56ef-127">您也可以**釘選相片，而不需要應用程式列**在您的世界。</span><span class="sxs-lookup"><span data-stu-id="d56ef-127">You can also **pin photos without the app bar** in your world .</span></span>

  <span data-ttu-id="d56ef-128">![應用程式列中可以隱藏等相片的 2D 應用程式](images/img-3626-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d56ef-128">![The app bar can be hidden for 2D apps like photos](images/img-3626-400px.jpg)</span></span><br>
  <span data-ttu-id="d56ef-129">應用程式列中可以隱藏的 2D 檢視，例如相片的應用程式</span><span class="sxs-lookup"><span data-stu-id="d56ef-129">The app bar can be hidden for apps with a 2D view, like Photos</span></span>
  
* <span data-ttu-id="d56ef-130">**檔案選擇器**運作方式就像 HoloLens 上的預期。</span><span class="sxs-lookup"><span data-stu-id="d56ef-130">**File picker** works just like you expect it to on HoloLens.</span></span>
* <span data-ttu-id="d56ef-131">更新**Edge 瀏覽器**對應與桌面和電話的統一的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="d56ef-131">Updated **Edge browser** to map unified user experience with desktop and phone.</span></span> <span data-ttu-id="d56ef-132">我們已啟用瀏覽器、 自訂 HoloLens 新索引標籤頁面、 索引標籤上查看和開啟新的 windows，以及電源及效能改進中的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="d56ef-132">We enabled multiple instances of your browser, custom HoloLens new tab page, tab peek, and open in new windows, along with power & performance improvements.</span></span>
* <span data-ttu-id="d56ef-133">**Groove 音樂**HoloLens 上就有應用程式。</span><span class="sxs-lookup"><span data-stu-id="d56ef-133">**Groove Music** app is now on HoloLens.</span></span> <span data-ttu-id="d56ef-134">請瀏覽要下載，並嘗試在背景播放的存放區。</span><span class="sxs-lookup"><span data-stu-id="d56ef-134">Visit the store to download it and try playing in the background.</span></span>
* <span data-ttu-id="d56ef-135">您可以輕鬆地自訂應用程式在您的世界中的排列方式。</span><span class="sxs-lookup"><span data-stu-id="d56ef-135">You can easily customize how apps are arranged in your world.</span></span> <span data-ttu-id="d56ef-136">請嘗試**旋轉您全像投影**中調整模式，只要按一下並拖曳上在中間的垂直框線的圓形。</span><span class="sxs-lookup"><span data-stu-id="d56ef-136">Try **rotating your holograms** in adjust mode by simply click and drag on circle in the middle vertical wireframes.</span></span> <span data-ttu-id="d56ef-137">您可能會注意到有全像投影**緊密度適合的週框方塊**以確保最大化的互動。</span><span class="sxs-lookup"><span data-stu-id="d56ef-137">You might notice holograms have **tighter fitted bounding boxes** to ensure maximized interaction.</span></span> <span data-ttu-id="d56ef-138">您也可以垂直調整所有一般的應用程式 (除非相片和全像應用程式)。</span><span class="sxs-lookup"><span data-stu-id="d56ef-138">You can also resize all flat apps vertically (except Photos and Hologram apps).</span></span>

  <span data-ttu-id="d56ef-139">![之後您將它們放在世界中，就可以旋轉全像投影](images/img-3627-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d56ef-139">![Holograms can be rotated after you place them in the world](images/img-3627-400px.jpg)</span></span><br>
  <span data-ttu-id="d56ef-140">旋轉全像投影之後將它們放在您的世界</span><span class="sxs-lookup"><span data-stu-id="d56ef-140">Rotate holograms after you place them in your world</span></span>

* <span data-ttu-id="d56ef-141">我們已進行大量**輸入改進**在此處理過程中。</span><span class="sxs-lookup"><span data-stu-id="d56ef-141">We've made a lot of **input improvement** in this flight.</span></span> <span data-ttu-id="d56ef-142">您可以連接標準的藍芽滑鼠到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d56ef-142">You can connect a regular Bluetooth mouse to HoloLens.</span></span> <span data-ttu-id="d56ef-143">Clicker 已順利微調，以啟用調整大小和移動與 clicker 全像投影。</span><span class="sxs-lookup"><span data-stu-id="d56ef-143">The clicker has been fine tuned to enable resizing & moving holograms with a clicker.</span></span> <span data-ttu-id="d56ef-144">鍵盤也執行比以往更容易。</span><span class="sxs-lookup"><span data-stu-id="d56ef-144">Keyboard is also running better than ever.</span></span>
* <span data-ttu-id="d56ef-145">現在您可以採取**混合實境圖片**直接按下音量提高 + 向下的磁碟區同時。</span><span class="sxs-lookup"><span data-stu-id="d56ef-145">Now you can take **mixed reality pictures** by simply pressing down the volume up + volume down simultaneously.</span></span> <span data-ttu-id="d56ef-146">您也可以共用您的混合的實境擷取相片和影片以 Facebook、 Twitter 及 YouTube。</span><span class="sxs-lookup"><span data-stu-id="d56ef-146">You can also share your mixed reality captured photos & videos to Facebook, Twitter and YouTube.</span></span>
* <span data-ttu-id="d56ef-147">最大記錄長度**混合實境影片**已增加至五分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="d56ef-147">The maximum recording length of **mixed reality videos** has been increased to five minutes.</span></span>
* <span data-ttu-id="d56ef-148">**相片應用程式**現在可從 OneDrive 的影片串流處理而不需要下載整個視訊播放之前。</span><span class="sxs-lookup"><span data-stu-id="d56ef-148">**Photos app** now streams videos from OneDrive instead of having to download the entire video before playback.</span></span>
* <span data-ttu-id="d56ef-149">我們已改善如何您**全像投影會正確在您停止的地方**。</span><span class="sxs-lookup"><span data-stu-id="d56ef-149">We've improved how your **holograms will be right where you left them**.</span></span> <span data-ttu-id="d56ef-150">您也會看到選項以重新連線至 Wi-fi 並再試一次如果 HoloLens 偵測不到它們的位置。</span><span class="sxs-lookup"><span data-stu-id="d56ef-150">You will also be presented the option to re-connect to Wi-Fi and try again if HoloLens cannot detect where they are.</span></span>
* <span data-ttu-id="d56ef-151">具有鍵盤**經過改良的配置，用於輸入電子郵件地址**具有單一網域按一下按鍵，可讓您輸入的最受歡迎的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="d56ef-151">The keyboard has an **improved layout for entering email address** with keys that allow you to enter the most popular email domains with a single click.</span></span>
* <span data-ttu-id="d56ef-152">更快**應用程式註冊**並**自動偵測的時區**在 OOBE 期間提供您最佳的第一位使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="d56ef-152">Faster **app registration** and **auto detection of time zone** during OOBE, giving you the best first user experience.</span></span>
* <span data-ttu-id="d56ef-153">**儲存空間感知器**可讓您在 [設定] 應用程式中檢視系統和應用程式的其餘和使用磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="d56ef-153">**Storage sense** allows you to view remaining and used disk space by the system and apps in the settings app.</span></span>
* <span data-ttu-id="d56ef-154">我們都有交集的意見反應應用程式和內部 Hub 到單一應用程式**意見反應中樞**，它就會前往工具**給予我們意見反應**，哪些功能您喜歡，您可以執行不含，或當哪些功能項目可能是更好。</span><span class="sxs-lookup"><span data-stu-id="d56ef-154">We have converged Feedback App and Inside Hub into a single app **Feedback Hub** that will be the go-to tool for **giving us feedback**, which features you love, which features you could do without, or when something could be better.</span></span> <span data-ttu-id="d56ef-155">當您加入 Insider 計劃時，您可以保留**取得最新的測試人員消息**，**評比組建**，並在 上移**意見反應點數**從意見反應中樞。</span><span class="sxs-lookup"><span data-stu-id="d56ef-155">When you join the Insider Program, you can keep up on **get latest Insider news**, **rate builds** and go on **feedback quests** from Feedback Hub.</span></span>
* <span data-ttu-id="d56ef-156">我們也[發行更新的 HoloLens 模擬器](install-the-tools.md)建置。</span><span class="sxs-lookup"><span data-stu-id="d56ef-156">We've also [published an updated HoloLens Emulator](install-the-tools.md) build.</span></span>
* <span data-ttu-id="d56ef-157">您的混合的實境影片現在看起來更因為自動**視訊穩定**。</span><span class="sxs-lookup"><span data-stu-id="d56ef-157">Your mixed reality videos now look better due to automatic **video stabilization**.</span></span>

## <a name="major-fixes"></a><span data-ttu-id="d56ef-158">主要的修正</span><span class="sxs-lookup"><span data-stu-id="d56ef-158">Major fixes</span></span>

<span data-ttu-id="d56ef-159">我們已修正問題，其中的空格會變慢或不正確地偵測到全像空格。</span><span class="sxs-lookup"><span data-stu-id="d56ef-159">We fixed issues with hologram spaces where the spaces would be slow or incorrectly detected.</span></span> <span data-ttu-id="d56ef-160">我們已修正可能會持續嘗試啟動殼層在關機時關機問題。</span><span class="sxs-lookup"><span data-stu-id="d56ef-160">We fixed a shutdown issue that could continue to try launching the shell during shutdown.</span></span>

<span data-ttu-id="d56ef-161">我們已修正的問題</span><span class="sxs-lookup"><span data-stu-id="d56ef-161">We fixed an issue</span></span>
* <span data-ttu-id="d56ef-162">封鎖繼續執行 XAML 應用程式的能力。</span><span class="sxs-lookup"><span data-stu-id="d56ef-162">that blocks the ability to resume a XAML application.</span></span>
* <span data-ttu-id="d56ef-163">其中損毀會讓全黑的螢幕，以及一些不規則線條。</span><span class="sxs-lookup"><span data-stu-id="d56ef-163">where a crash would leave a black screen and some jagged lines.</span></span>
* <span data-ttu-id="d56ef-164">捲動會有時情景方向錯誤時使用某些應用程式。</span><span class="sxs-lookup"><span data-stu-id="d56ef-164">scrolling would sometimes stick in the wrong direction when using some apps.</span></span>
* <span data-ttu-id="d56ef-165">電源 led 燈號可能表示為關閉狀態仍開啟裝置時。</span><span class="sxs-lookup"><span data-stu-id="d56ef-165">the power LEDs could indicate an off state when the device was still on.</span></span>
* <span data-ttu-id="d56ef-166">無法取得 WiFi 已關閉之後繼續從待命狀態。</span><span class="sxs-lookup"><span data-stu-id="d56ef-166">WiFi could get turned off after resuming from standby.</span></span>
* <span data-ttu-id="d56ef-167">Xbox 身分識別提供者提供的玩家代號設定，然後取得卡在迴圈中。</span><span class="sxs-lookup"><span data-stu-id="d56ef-167">the Xbox identity provider offers gamertag setup and then gets stuck in a loop.</span></span>
* <span data-ttu-id="d56ef-168">OneDrive 檔案選擇器中選取已下載的檔案時，偶爾會損毀殼層。</span><span class="sxs-lookup"><span data-stu-id="d56ef-168">the Shell occasionally crashes when selecting a downloaded file in the OneDrive File Picker.</span></span>
* <span data-ttu-id="d56ef-169">按住連結有時同時開啟新的、 中斷 索引標籤，並開啟內容功能表。</span><span class="sxs-lookup"><span data-stu-id="d56ef-169">pressing and holding on a link sometimes both opens a new, broken tab and opens a context menu.</span></span>
* <span data-ttu-id="d56ef-170">其中，windows 裝置入口網站並不允許從 50 80 IPD 調整</span><span class="sxs-lookup"><span data-stu-id="d56ef-170">where windows device portal didn’t allow IPD adjustments from 50 to 80</span></span>

<span data-ttu-id="d56ef-171">我們已修正問題的相片，</span><span class="sxs-lookup"><span data-stu-id="d56ef-171">We fixed issues with Photos where</span></span>
* <span data-ttu-id="d56ef-172">偶而會顯示映像，因為忽略 EXIF orientation 屬性旋轉。</span><span class="sxs-lookup"><span data-stu-id="d56ef-172">an image would occasionally display rotated due to ignoring the EXIF orientation property.</span></span>
* <span data-ttu-id="d56ef-173">它可能會對已釘選的相片的啟動期間損毀。</span><span class="sxs-lookup"><span data-stu-id="d56ef-173">it could crash during start-up on pinned Photos.</span></span>
* <span data-ttu-id="d56ef-174">影片會重新啟動，而不會在上次暫停，從繼續在暫停之後。</span><span class="sxs-lookup"><span data-stu-id="d56ef-174">videos would restart after pausing instead of continuing from where last paused.</span></span>
* <span data-ttu-id="d56ef-175">如果共用播放時，無法防止共用視訊的重新執行。</span><span class="sxs-lookup"><span data-stu-id="d56ef-175">replay of a shared video could be prevented if it was shared while playing.</span></span>
* <span data-ttu-id="d56ef-176">混合的實境擷取的記錄會以 0.5-1 為開頭的音訊只有摘要的第二個。</span><span class="sxs-lookup"><span data-stu-id="d56ef-176">Mixed Reality Capture recordings would begin with 0.5-1 second of audio only feed.</span></span>
* <span data-ttu-id="d56ef-177">同步處理 按鈕就會消失，初始的 OneDrive 同步處理期間。</span><span class="sxs-lookup"><span data-stu-id="d56ef-177">the Sync button disappears during initial OneDrive sync.</span></span>

<span data-ttu-id="d56ef-178">我們已修正設定問題，</span><span class="sxs-lookup"><span data-stu-id="d56ef-178">We fixed issues with settings where</span></span>
* <span data-ttu-id="d56ef-179">需要重新整理的環境變更時。</span><span class="sxs-lookup"><span data-stu-id="d56ef-179">a refresh was needed when the environment changes.</span></span>
* <span data-ttu-id="d56ef-180">「 輸入 」 鍵盤會無法運作，例如某些對話方塊中按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d56ef-180">'Enter' on keyboard would not behave like clicking Next in some dialogs.</span></span>
* <span data-ttu-id="d56ef-181">很難了解當 clicker 無法配對。</span><span class="sxs-lookup"><span data-stu-id="d56ef-181">it was hard to know when the clicker failed pairing.</span></span>
* <span data-ttu-id="d56ef-182">它可能會變成沒有回應，使用 WiFi 中斷連線並連線。</span><span class="sxs-lookup"><span data-stu-id="d56ef-182">it could become unresponsive with WiFi disconnect and connect.</span></span>

<span data-ttu-id="d56ef-183">我們已修正與 Cortana 的問題，</span><span class="sxs-lookup"><span data-stu-id="d56ef-183">We fixed issues with Cortana where</span></span>
* <span data-ttu-id="d56ef-184">它可能會卡顯示接聽 UI。</span><span class="sxs-lookup"><span data-stu-id="d56ef-184">it could get stuck displaying the Listening UI.</span></span>
* <span data-ttu-id="d56ef-185">詢問 「 嘿 Cortana，我可以說什麼 」 以獨佔模式從應用程式會停滯如果您回答而或許是/否来結束應用程式的要求。</span><span class="sxs-lookup"><span data-stu-id="d56ef-185">asking "Hey Cortana, what can I say" from an exclusive mode app would get stuck if you answered maybe rather yes/no to the request to exit the app.</span></span>
* <span data-ttu-id="d56ef-186">如果您詢問 Cortana 移至睡眠狀態，然後繼續時，不正確地繼續接聽 UI 的 Cortana。</span><span class="sxs-lookup"><span data-stu-id="d56ef-186">the Cortana listening UI doesn't resume correctly if you ask Cortana to go to sleep and then resume.</span></span>
* <span data-ttu-id="d56ef-187">查詢 「 網路為何我連線到？ 」</span><span class="sxs-lookup"><span data-stu-id="d56ef-187">the queries "What network am I connected to?"</span></span> <span data-ttu-id="d56ef-188">和"Am 我連線嗎？ 」</span><span class="sxs-lookup"><span data-stu-id="d56ef-188">and the "Am I connected?"</span></span> <span data-ttu-id="d56ef-189">第一個網路設定檔傳回時沒有連線，可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="d56ef-189">could fail when the first network profile comes back with no connectivity.</span></span>
* <span data-ttu-id="d56ef-190">UI 凍結上 「 接聽 」，但在結束應用程式時就立即開始不斷執行語音辨識。</span><span class="sxs-lookup"><span data-stu-id="d56ef-190">the UI froze on "Listening" but upon exiting an app would immediately began doing speech recognition again.</span></span>
* <span data-ttu-id="d56ef-191">其中登出 Cortana 應用程式就可讓您登回它直到重新開機。</span><span class="sxs-lookup"><span data-stu-id="d56ef-191">where signing out of the Cortana app wouldn't let you sign back into it until a reboot.</span></span>
* <span data-ttu-id="d56ef-192">它不會啟動時作用中混合實境擷取 UI。</span><span class="sxs-lookup"><span data-stu-id="d56ef-192">it would not launch when Mixed Reality Capture UI was active.</span></span>

<span data-ttu-id="d56ef-193">我們已修正使用 Visual Studio 的問題，</span><span class="sxs-lookup"><span data-stu-id="d56ef-193">We fixed issues with Visual Studio where</span></span>
* <span data-ttu-id="d56ef-194">背景工作偵錯無法運作。</span><span class="sxs-lookup"><span data-stu-id="d56ef-194">background task debugging did not work.</span></span>
* <span data-ttu-id="d56ef-195">圖形偵錯工具中的畫面格分析無法運作。</span><span class="sxs-lookup"><span data-stu-id="d56ef-195">frame analysis in the graphics debugger did not work.</span></span>
* <span data-ttu-id="d56ef-196">HoloLens 模擬器未出現在下拉式清單中適用於 Visual Studio 除非您的專案 TargetPlatformVersion 已設為 10240。</span><span class="sxs-lookup"><span data-stu-id="d56ef-196">the HoloLens Emulator did not appear in the drop-down list for Visual Studio unless your project's TargetPlatformVersion was set to 10240.</span></span>

## <a name="changes-from-previous-release"></a><span data-ttu-id="d56ef-197">從舊版的變更</span><span class="sxs-lookup"><span data-stu-id="d56ef-197">Changes from previous release</span></span>
* <span data-ttu-id="d56ef-198">Cortana 命令**嘿 Cortana，重新啟動裝置**無法運作。</span><span class="sxs-lookup"><span data-stu-id="d56ef-198">The Cortana command **Hey Cortana, reboot the device** does not work.</span></span> <span data-ttu-id="d56ef-199">使用者可以說**嘿 Cortana，重新啟動**或是**嘿 Cortana，重新啟動裝置**。</span><span class="sxs-lookup"><span data-stu-id="d56ef-199">User can say **Hey Cortana, restart** or **Hey Cortana, restart the device**.</span></span>
* <span data-ttu-id="d56ef-200">Kiosk 模式已從產品中移除。</span><span class="sxs-lookup"><span data-stu-id="d56ef-200">Kiosk mode has been removed from the product.</span></span>

## <a name="prior-release-notes"></a><span data-ttu-id="d56ef-201">先前的版本資訊</span><span class="sxs-lookup"><span data-stu-id="d56ef-201">Prior release notes</span></span>
* [<span data-ttu-id="d56ef-202">版本資訊-2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="d56ef-202">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="d56ef-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d56ef-203">See also</span></span>
* [<span data-ttu-id="d56ef-204">HoloLens 的已知問題</span><span class="sxs-lookup"><span data-stu-id="d56ef-204">HoloLens known issues</span></span>](hololens-known-issues.md)
* [<span data-ttu-id="d56ef-205">安裝工具</span><span class="sxs-lookup"><span data-stu-id="d56ef-205">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="d56ef-206">Shell</span><span class="sxs-lookup"><span data-stu-id="d56ef-206">Shell</span></span>](navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="d56ef-207">更新混合實境的 2D UWP 應用的程式</span><span class="sxs-lookup"><span data-stu-id="d56ef-207">Updating 2D UWP apps for mixed reality</span></span>](building-2d-apps.md)
* [<span data-ttu-id="d56ef-208">硬體附屬應用程式</span><span class="sxs-lookup"><span data-stu-id="d56ef-208">Hardware accessories</span></span>](hardware-accessories.md)
* [<span data-ttu-id="d56ef-209">混合的實境擷取</span><span class="sxs-lookup"><span data-stu-id="d56ef-209">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="d56ef-210">語音輸入</span><span class="sxs-lookup"><span data-stu-id="d56ef-210">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="d56ef-211">提交至 Windows 市集應用程式</span><span class="sxs-lookup"><span data-stu-id="d56ef-211">Submitting an app to the Windows Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="d56ef-212">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="d56ef-212">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
