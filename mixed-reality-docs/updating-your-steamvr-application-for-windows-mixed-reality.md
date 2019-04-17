---
title: 更新 Windows Mixed Reality 的應用程式 SteamVR
description: 更新 SteamVR 應用程式來充分發揮 Windows Mixed Reality 耳機與相容性的最佳做法。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR，相容性
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591189"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a><span data-ttu-id="38fe5-104">更新 Windows Mixed Reality 的應用程式 SteamVR</span><span class="sxs-lookup"><span data-stu-id="38fe5-104">Updating your SteamVR application for Windows Mixed Reality</span></span>

<span data-ttu-id="38fe5-105">我們鼓勵開發人員測試和最佳化 Windows Mixed Reality 耳機上執行其 SteamVR 體驗。</span><span class="sxs-lookup"><span data-stu-id="38fe5-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="38fe5-106">這份文件涵蓋了一般開發人員可以對確保他們的體驗 Windows Mixed reality 執行絕佳的增強功能。</span><span class="sxs-lookup"><span data-stu-id="38fe5-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="38fe5-107">初始安裝指示</span><span class="sxs-lookup"><span data-stu-id="38fe5-107">Initial setup instructions</span></span>

<span data-ttu-id="38fe5-108">若要開始測試您的遊戲或應用程式上 Windows Mixed Reality 確定到第一個遵循我們[入門指南。](http://aka.ms/WindowsMixedRealitySteamVR)</span><span class="sxs-lookup"><span data-stu-id="38fe5-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](http://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="38fe5-109">控制器模型</span><span class="sxs-lookup"><span data-stu-id="38fe5-109">Controller Models</span></span>
1. <span data-ttu-id="38fe5-110">如果您的應用程式呈現控制器模型：</span><span class="sxs-lookup"><span data-stu-id="38fe5-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="38fe5-111">使用[Windows Mixed Reality 動作控制器模型](motion-controllers.md#rendering-the-motion-controller-model)</span><span class="sxs-lookup"><span data-stu-id="38fe5-111">Use the [Windows Mixed Reality motion controller models](motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="38fe5-112">若要取得本機使用 IVRRenderModel::GetComponentState 將轉換為元件組件 （例如。</span><span class="sxs-lookup"><span data-stu-id="38fe5-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="38fe5-113">指標姿勢）</span><span class="sxs-lookup"><span data-stu-id="38fe5-113">Pointer pose)</span></span>
2. <span data-ttu-id="38fe5-114">體驗有法線慣用手的概念，應從輸入 Api 來區分控制器取得提示[（Unity 範例）](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="38fe5-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="38fe5-115">控制項</span><span class="sxs-lookup"><span data-stu-id="38fe5-115">Controls</span></span>

<span data-ttu-id="38fe5-116">在設計或調整您的控制項配置請記住下列保留的命令組：</span><span class="sxs-lookup"><span data-stu-id="38fe5-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="38fe5-117">按一下向下**左邊和右邊類比搖桿**保留供**Steam 儀表板**。</span><span class="sxs-lookup"><span data-stu-id="38fe5-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard**.</span></span>
2. <span data-ttu-id="38fe5-118">**Windows 按鈕**一律會傳回使用者家用的 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="38fe5-118">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="38fe5-119">可能的話，thumb 隨身碟的預設基礎來比對的屏障[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)屏障行為</span><span class="sxs-lookup"><span data-stu-id="38fe5-119">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="38fe5-120">工具提示和 UI</span><span class="sxs-lookup"><span data-stu-id="38fe5-120">Tooltips and UI</span></span>

<span data-ttu-id="38fe5-121">許多的 VR 遊戲善用動作控制器的工具提示並教導使用者他們的遊戲或應用程式的最重要命令的覆疊。</span><span class="sxs-lookup"><span data-stu-id="38fe5-121">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="38fe5-122">微調您的應用程式的 Windows Mixed reality 時建議您檢閱您的體驗，並確定將對應至 Windows 控制器模型的工具提示的這個部分。</span><span class="sxs-lookup"><span data-stu-id="38fe5-122">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="38fe5-123">另外有您的經驗顯示控制站的映像的位置中的任何點請務必提供更新的映像使用 Windows Mixed Reality 動作控制站。</span><span class="sxs-lookup"><span data-stu-id="38fe5-123">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="38fe5-124">Haptics</span><span class="sxs-lookup"><span data-stu-id="38fe5-124">Haptics</span></span>

<span data-ttu-id="38fe5-125">開頭[Windows 10 April 2018 Update](release-notes-april-2018.md)，haptics 現在支援以 SteamVR 體驗 Windows Mixed reality。</span><span class="sxs-lookup"><span data-stu-id="38fe5-125">Beginning with the [Windows 10 April 2018 Update](release-notes-april-2018.md), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="38fe5-126">如果 SteamVR 應用程式或遊戲已經包含 haptics 的支援，其應該正常運作 （進行任何其他的工作） 與[Windows Mixed Reality 動作控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="38fe5-126">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](motion-controllers.md).</span></span>

<span data-ttu-id="38fe5-127">Windows Mixed Reality 動作控制站會使用標準 haptics 馬達，而不是線性的傳動器，在某些其他 SteamVR 動作控制站，而可能會導致稍微不同高於預期的使用者體驗中找到。</span><span class="sxs-lookup"><span data-stu-id="38fe5-127">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="38fe5-128">因此，我們建議測試及調整您的 haptics 設計，含有 Windows Mixed Reality 動作控制站。</span><span class="sxs-lookup"><span data-stu-id="38fe5-128">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="38fe5-129">比方說，有時簡短 haptic 跳動 （5-10 毫秒） 是 Windows Mixed Reality 動作控制站上較不明顯。</span><span class="sxs-lookup"><span data-stu-id="38fe5-129">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="38fe5-130">若要產生更明顯的 pulse，試驗傳送長 「 按一下 」 (40 70ms) 來提供馬達的更多時間才能啟動之前被告知電源一次。</span><span class="sxs-lookup"><span data-stu-id="38fe5-130">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="38fe5-131">從 Windows Mixed Reality 開始 功能表啟動 SteamVR 應用程式</span><span class="sxs-lookup"><span data-stu-id="38fe5-131">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="38fe5-132">透過資料流所散發的 VR 體驗，我們已[SteamVR beta 版更新 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新[Windows 測試人員](https://insider.windows.com)RS5 航班以便 SteamVR 標題會出現在混合實境 [開始] 功能表中 [所有應用程式 」 會自動列出。</span><span class="sxs-lookup"><span data-stu-id="38fe5-132">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="38fe5-133">與安裝這些軟體版本，您的客戶現在可以啟動 SteamVR 項目直接從家用的 Windows Mixed Reality 內而不需移除其耳機。</span><span class="sxs-lookup"><span data-stu-id="38fe5-133">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="38fe5-134">Windows Mixed Reality 標誌</span><span class="sxs-lookup"><span data-stu-id="38fe5-134">Windows Mixed Reality logo</span></span>

<span data-ttu-id="38fe5-135">若要顯示標題的 Windows Mixed Reality 支援，請前往 「 編輯存放區頁面 」 連結，應用程式登陸頁面上，按一下 [基本資訊] 索引標籤上，捲動到 「 虛擬實境。 」</span><span class="sxs-lookup"><span data-stu-id="38fe5-135">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="38fe5-136">取消核取 「 隱藏 Windows Mixed Reality"，然後發佈到市集。</span><span class="sxs-lookup"><span data-stu-id="38fe5-136">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="38fe5-137">Bug 和意見反應</span><span class="sxs-lookup"><span data-stu-id="38fe5-137">Bugs and feedback</span></span>

<span data-ttu-id="38fe5-138">改善 Windows Mixed Reality SteamVR 體驗時，您的意見非常寶貴。</span><span class="sxs-lookup"><span data-stu-id="38fe5-138">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="38fe5-139">請提交的所有意見反應和透過 bug [Windows 意見反應中樞](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)。</span><span class="sxs-lookup"><span data-stu-id="38fe5-139">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="38fe5-140">以下是一些[如何讓您 SteamVR 的意見反應盡可能為有用的秘訣](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)。</span><span class="sxs-lookup"><span data-stu-id="38fe5-140">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="38fe5-141">如果您有問題或意見，若要共用，您也可以連線到我們在我們[Steam 論壇](http://steamcommunity.com/app/719950/discussions/)。</span><span class="sxs-lookup"><span data-stu-id="38fe5-141">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="38fe5-142">常見問題和疑難排解</span><span class="sxs-lookup"><span data-stu-id="38fe5-142">FAQs and troubleshooting</span></span>

<span data-ttu-id="38fe5-143">如果您執行一般的問題，設定或播放您的經驗[查看最新疑難排解步驟](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。</span><span class="sxs-lookup"><span data-stu-id="38fe5-143">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="38fe5-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38fe5-144">See also</span></span>
* [<span data-ttu-id="38fe5-145">安裝工具</span><span class="sxs-lookup"><span data-stu-id="38fe5-145">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="38fe5-146">耳機式和移動控制器的驅動程式記錄</span><span class="sxs-lookup"><span data-stu-id="38fe5-146">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="38fe5-147">Windows Mixed Reality 最小電腦的硬體相容性指導方針</span><span class="sxs-lookup"><span data-stu-id="38fe5-147">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
