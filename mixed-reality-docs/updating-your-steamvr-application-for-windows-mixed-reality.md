---
title: 更新適用于 Windows Mixed Reality 的 SteamVR 應用程式
description: 將您的 SteamVR 應用程式更新為使用 Windows Mixed Reality 耳機最大化相容性的最佳作法。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, 相容性
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548673"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a><span data-ttu-id="45676-104">更新適用于 Windows Mixed Reality 的 SteamVR 應用程式</span><span class="sxs-lookup"><span data-stu-id="45676-104">Updating your SteamVR application for Windows Mixed Reality</span></span>

<span data-ttu-id="45676-105">我們鼓勵開發人員測試並優化其 SteamVR 體驗, 以在 Windows Mixed Reality 耳機上執行。</span><span class="sxs-lookup"><span data-stu-id="45676-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="45676-106">本檔涵蓋開發人員可以進行的一般改良功能, 以確保他們的體驗在 Windows Mixed Reality 上的執行效果良好。</span><span class="sxs-lookup"><span data-stu-id="45676-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="45676-107">初始設定指示</span><span class="sxs-lookup"><span data-stu-id="45676-107">Initial setup instructions</span></span>

<span data-ttu-id="45676-108">若要開始在 Windows Mixed Reality 上測試您的遊戲或應用程式, 請務必先遵循我們的[快速入門手冊。](http://aka.ms/WindowsMixedRealitySteamVR)</span><span class="sxs-lookup"><span data-stu-id="45676-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](http://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="45676-109">控制器模型</span><span class="sxs-lookup"><span data-stu-id="45676-109">Controller Models</span></span>
1. <span data-ttu-id="45676-110">如果您的應用程式會呈現控制器模型:</span><span class="sxs-lookup"><span data-stu-id="45676-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="45676-111">使用[Windows Mixed Reality 運動控制器模型](motion-controllers.md#rendering-the-motion-controller-model)</span><span class="sxs-lookup"><span data-stu-id="45676-111">Use the [Windows Mixed Reality motion controller models](motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="45676-112">使用 IVRRenderModel:: GetComponentState 取得元件部分的本機轉換 (例如</span><span class="sxs-lookup"><span data-stu-id="45676-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="45676-113">指標姿勢)</span><span class="sxs-lookup"><span data-stu-id="45676-113">Pointer pose)</span></span>
2. <span data-ttu-id="45676-114">具有慣用手概念的經驗應該會從輸入 Api 取得提示, 以區別控制器[(Unity 範例)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="45676-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="45676-115">控制項</span><span class="sxs-lookup"><span data-stu-id="45676-115">Controls</span></span>

<span data-ttu-id="45676-116">設計或調整控制項版面配置時, 請記住下列保留的命令集:</span><span class="sxs-lookup"><span data-stu-id="45676-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="45676-117">按一下**左側和右側類比操縱杆**會保留給 [串流**儀表板**]。</span><span class="sxs-lookup"><span data-stu-id="45676-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard**.</span></span>
2. <span data-ttu-id="45676-118">**Windows 按鈕**一律會讓使用者回到 Windows Mixed Reality 首頁。</span><span class="sxs-lookup"><span data-stu-id="45676-118">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="45676-119">可能的話, 預設為以 thumb teleportation 為依據, 以符合[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation 行為</span><span class="sxs-lookup"><span data-stu-id="45676-119">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="45676-120">工具提示和 UI</span><span class="sxs-lookup"><span data-stu-id="45676-120">Tooltips and UI</span></span>

<span data-ttu-id="45676-121">許多 VR 遊戲會利用動作控制器的工具提示和重迭, 讓使用者學習其遊戲或應用程式最重要的命令。</span><span class="sxs-lookup"><span data-stu-id="45676-121">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="45676-122">針對 Windows Mixed reality 調整您的應用程式時, 我們建議您查看這部分的體驗, 以確保工具提示會對應到 Windows 控制器模型。</span><span class="sxs-lookup"><span data-stu-id="45676-122">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="45676-123">此外, 如果您的體驗中顯示控制器影像的任何時間點, 請務必使用 Windows Mixed Reality 動作控制器來提供更新的映射。</span><span class="sxs-lookup"><span data-stu-id="45676-123">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="45676-124">Haptics</span><span class="sxs-lookup"><span data-stu-id="45676-124">Haptics</span></span>

<span data-ttu-id="45676-125">從[windows 10 2018 年4月更新](release-notes-april-2018.md)開始, 現在支援 Haptics Windows Mixed Reality 的 SteamVR 體驗。</span><span class="sxs-lookup"><span data-stu-id="45676-125">Beginning with the [Windows 10 April 2018 Update](release-notes-april-2018.md), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="45676-126">如果您的 SteamVR 應用程式或遊戲已包含對 haptics 的支援, 則[Windows Mixed Reality 動作控制器](motion-controllers.md)現在應該可以正常執行 (不需要額外的工作)。</span><span class="sxs-lookup"><span data-stu-id="45676-126">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](motion-controllers.md).</span></span>

<span data-ttu-id="45676-127">Windows Mixed Reality 運動控制器會使用標準的 haptics 馬達, 而不是在其他 SteamVR 運動控制器中找到的線性傳動器, 這可能會導致略有不同的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="45676-127">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="45676-128">因此, 我們建議使用 Windows Mixed Reality 動作控制器來測試和調整您的 haptics 設計。</span><span class="sxs-lookup"><span data-stu-id="45676-128">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="45676-129">例如, 在 Windows Mixed Reality 動作控制器上, 有時短 haptic 脈衝 (5-10 毫秒) 較不明顯。</span><span class="sxs-lookup"><span data-stu-id="45676-129">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="45676-130">若要產生更明顯的脈衝, 請嘗試傳送較長的「按一下」 (40-70ms), 讓馬達在被告知關閉電源之前, 有更多時間來加速。</span><span class="sxs-lookup"><span data-stu-id="45676-130">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="45676-131">從 Windows Mixed Reality 開始功能表啟動 SteamVR 應用程式</span><span class="sxs-lookup"><span data-stu-id="45676-131">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="45676-132">針對透過串流散發的 VR 經驗, 我們已[更新 SteamVR Beta 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新的[Windows 測試人員](https://insider.windows.com)RS5 航班, 讓 SteamVR 標題現在會顯示在 [所有應用程式] 的 Windows Mixed Reality [開始] 功能表中自動列出。</span><span class="sxs-lookup"><span data-stu-id="45676-132">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="45676-133">安裝這些軟體版本後, 您的客戶現在就可以直接從 Windows Mixed Reality 首頁啟動 SteamVR 的標題, 而不需要移除其耳機。</span><span class="sxs-lookup"><span data-stu-id="45676-133">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="45676-134">Windows Mixed Reality 標誌</span><span class="sxs-lookup"><span data-stu-id="45676-134">Windows Mixed Reality logo</span></span>

<span data-ttu-id="45676-135">若要顯示您標題的 Windows Mixed Reality 支援, 請移至應用程式登陸頁面上的 [編輯存放區頁面] 連結, 按一下 [基本資訊] 索引標籤, 然後向下流覽至 [虛擬實境]。</span><span class="sxs-lookup"><span data-stu-id="45676-135">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="45676-136">取消核取 [隱藏 Windows Mixed Reality], 然後再發佈至存放區。</span><span class="sxs-lookup"><span data-stu-id="45676-136">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="45676-137">Bug 和意見反應</span><span class="sxs-lookup"><span data-stu-id="45676-137">Bugs and feedback</span></span>

<span data-ttu-id="45676-138">改善 Windows Mixed Reality SteamVR 體驗時, 您的意見反應非常寶貴。</span><span class="sxs-lookup"><span data-stu-id="45676-138">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="45676-139">請透過[Windows 意見反應中樞](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)提交所有意見反應和 bug。</span><span class="sxs-lookup"><span data-stu-id="45676-139">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="45676-140">以下是一些[如何讓您的 SteamVR 意見](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)反應盡可能發揮效用的秘訣。</span><span class="sxs-lookup"><span data-stu-id="45676-140">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="45676-141">如果您有想要分享的問題或意見, 也可以在我們的串流[論壇](http://steamcommunity.com/app/719950/discussions/)上聯繫我們。</span><span class="sxs-lookup"><span data-stu-id="45676-141">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="45676-142">常見問題和疑難排解</span><span class="sxs-lookup"><span data-stu-id="45676-142">FAQs and troubleshooting</span></span>

<span data-ttu-id="45676-143">如果您在設定或播放體驗時遇到一般問題, 請[查看最新的疑難排解步驟](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。</span><span class="sxs-lookup"><span data-stu-id="45676-143">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="45676-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45676-144">See also</span></span>
* [<span data-ttu-id="45676-145">安裝工具</span><span class="sxs-lookup"><span data-stu-id="45676-145">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="45676-146">耳機和動作控制器驅動程式歷程記錄</span><span class="sxs-lookup"><span data-stu-id="45676-146">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="45676-147">Windows Mixed Reality 最低電腦硬體相容性指導方針</span><span class="sxs-lookup"><span data-stu-id="45676-147">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
