---
title: HoloLens 疑難排解
description: Microsoft HoloLens 的疑難排解步驟。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 問題、錯誤、疑難排解、修正、說明、支援、HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550888"
---
# <a name="hololens-troubleshooting"></a><span data-ttu-id="97a6b-104">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="97a6b-104">HoloLens Troubleshooting</span></span>

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a><span data-ttu-id="97a6b-105">我的 HoloLens 沒有回應或無法開機</span><span class="sxs-lookup"><span data-stu-id="97a6b-105">My HoloLens is unresponsive or won’t boot</span></span>

<span data-ttu-id="97a6b-106">如果您的 HoloLens 無法開機:</span><span class="sxs-lookup"><span data-stu-id="97a6b-106">If your HoloLens won't boot:</span></span>
* <span data-ttu-id="97a6b-107">如果 [電源] 按鈕的 Led 不亮, 或只有1個 LED 短暫閃爍, 您可能需要向 HoloLens 收費。</span><span class="sxs-lookup"><span data-stu-id="97a6b-107">If the LEDs by the power button don't light up, or only 1 LED briefly blinks, you may need to charge your HoloLens.</span></span>
* <span data-ttu-id="97a6b-108">當您按下電源按鈕但看不到顯示器上的任何專案時, 如果 Led 亮起, 請按住 [電源] 按鈕, 直到電源按鈕關閉為止的所有5個 Led。</span><span class="sxs-lookup"><span data-stu-id="97a6b-108">If the LEDs light up when you press the power button but you can't see anything on the displays, hold the power button until all 5 of the LEDs by the power button turn off.</span></span>

<span data-ttu-id="97a6b-109">如果您的 HoloLens 已凍結或沒有回應:</span><span class="sxs-lookup"><span data-stu-id="97a6b-109">If your HoloLens becomes frozen or unresponsive:</span></span>
* <span data-ttu-id="97a6b-110">關閉您的 HoloLens, 方法是按下 [電源] 按鈕的所有5個 Led, 直到電源按鈕變成 [關閉], 或如果 Led 沒有回應, 則為10秒。</span><span class="sxs-lookup"><span data-stu-id="97a6b-110">Turn off your HoloLens by pressing the power button until all 5 of the LEDs by the power button turn themselves off, or for 10 seconds if the LEDs are unresponsive.</span></span> <span data-ttu-id="97a6b-111">再按一次 [電源] 按鈕以開機。</span><span class="sxs-lookup"><span data-stu-id="97a6b-111">Press the power button again to boot.</span></span>

<span data-ttu-id="97a6b-112">如果這些步驟無法正常執行:</span><span class="sxs-lookup"><span data-stu-id="97a6b-112">If these steps don't work:</span></span>
* <span data-ttu-id="97a6b-113">您可以嘗試[復原您的裝置](reset-or-recover-your-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="97a6b-113">You can try [recovering your device](reset-or-recover-your-hololens.md).</span></span>

## <a name="holograms-dont-look-good-or-are-moving-around"></a><span data-ttu-id="97a6b-114">全息影像外觀不佳或四處移動。</span><span class="sxs-lookup"><span data-stu-id="97a6b-114">Holograms don't look good or are moving around.</span></span>

<span data-ttu-id="97a6b-115">如果您的全息影像不穩定、跳動或看起來不正確, 請嘗試下列其中一個修正:</span><span class="sxs-lookup"><span data-stu-id="97a6b-115">If your holograms are unstable, jumpy, or don’t look right, try one of these fixes:</span></span>
* <span data-ttu-id="97a6b-116">清除您的裝置面板, 並確定沒有任何阻礙感應器。</span><span class="sxs-lookup"><span data-stu-id="97a6b-116">Clean your device visor and make sure nothing is obstructing the sensors.</span></span>
* <span data-ttu-id="97a6b-117">請確定您的房間內有足夠的光線。</span><span class="sxs-lookup"><span data-stu-id="97a6b-117">Make sure there’s enough light in your room.</span></span>
* <span data-ttu-id="97a6b-118">試著流覽並查看您的環境, 讓 HoloLens 可以更完整地掃描。</span><span class="sxs-lookup"><span data-stu-id="97a6b-118">Try walking around and looking at your surroundings so HoloLens can scan them more completely.</span></span>
* <span data-ttu-id="97a6b-119">試著執行校正應用程式。</span><span class="sxs-lookup"><span data-stu-id="97a6b-119">Try running the Calibration app.</span></span> <span data-ttu-id="97a6b-120">它會校正您的 HoloLens 以最適合您的眼睛。</span><span class="sxs-lookup"><span data-stu-id="97a6b-120">It calibrates your HoloLens to work best for your eyes.</span></span> <span data-ttu-id="97a6b-121">移至 [**設定** > ] [**系統** > **公用程式**]。</span><span class="sxs-lookup"><span data-stu-id="97a6b-121">Go to **Settings** > **System** > **Utilities**.</span></span> <span data-ttu-id="97a6b-122">在 [校正] 底下, 選取 [**開啟校正**]。</span><span class="sxs-lookup"><span data-stu-id="97a6b-122">Under Calibration, select **Open Calibration**.</span></span>
* <span data-ttu-id="97a6b-123">如果您在執行校正應用程式之後仍然遇到問題, 請使用感應器微調應用程式來調整您的裝置感應器。</span><span class="sxs-lookup"><span data-stu-id="97a6b-123">If you’re still having trouble after running the Calibration app, use the Sensor Tuning app to tune your device sensors.</span></span> <span data-ttu-id="97a6b-124">移至 [**設定** > ] [**系統** > **公用程式**]。</span><span class="sxs-lookup"><span data-stu-id="97a6b-124">Go to **Settings** > **System** > **Utilities**.</span></span> <span data-ttu-id="97a6b-125">在 [感應器微調] 底下, 選取 [**開啟感應器微調**]。</span><span class="sxs-lookup"><span data-stu-id="97a6b-125">Under Sensor tuning, select **Open Sensor Tuning**.</span></span>

## <a name="hololens-doesnt-respond-to-my-gestures"></a><span data-ttu-id="97a6b-126">HoloLens 不會回應我的手勢。</span><span class="sxs-lookup"><span data-stu-id="97a6b-126">HoloLens doesn’t respond to my gestures.</span></span>

<span data-ttu-id="97a6b-127">若要確保 HoloLens 能夠看到您的手勢, 請將手放在手勢框架中, 這會在您的任一邊延伸幾英尺。</span><span class="sxs-lookup"><span data-stu-id="97a6b-127">To make sure HoloLens can see your gestures, keep your hand in the gesture frame, which extends a couple of feet on either side of you.</span></span> <span data-ttu-id="97a6b-128">當 HoloLens 可以看到您的手時, 游標會從點變更為環形。</span><span class="sxs-lookup"><span data-stu-id="97a6b-128">When HoloLens can see your hand, the cursor will change from a dot to a ring.</span></span> <span data-ttu-id="97a6b-129">深入瞭解如何使用[手勢](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="97a6b-129">Learn more about using [gestures](gestures.md).</span></span>

<span data-ttu-id="97a6b-130">如果您的環境太暗, HoloLens 可能看不到您的手, 因此請確定有足夠的光線。</span><span class="sxs-lookup"><span data-stu-id="97a6b-130">If your environment is too dark, HoloLens might not see your hand, so make sure there’s enough light.</span></span>

<span data-ttu-id="97a6b-131">如果您的面板具有指紋或塗抹, 請使用 HoloLens 隨附的 microfiber 清潔抹布來輕輕清理您的面板。</span><span class="sxs-lookup"><span data-stu-id="97a6b-131">If your visor has fingerprints or smudge, please use the microfiber cleaning cloth that came with the HoloLens to clean your visor gently.</span></span>

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a><span data-ttu-id="97a6b-132">HoloLens 不會回應我的語音命令。</span><span class="sxs-lookup"><span data-stu-id="97a6b-132">HoloLens doesn’t respond to my voice commands.</span></span>

<span data-ttu-id="97a6b-133">如果 Cortana 沒有回應您的語音命令, 請確定 Cortana 已開啟。</span><span class="sxs-lookup"><span data-stu-id="97a6b-133">If Cortana isn’t responding to your voice commands, make sure Cortana is turned on.</span></span> <span data-ttu-id="97a6b-134">在 所有應用程式 清單中, 選取 Cortana > 功能表 > 筆記本 > 設定 以進行變更。</span><span class="sxs-lookup"><span data-stu-id="97a6b-134">On the All apps list, select Cortana > Menu > Notebook > Settings to make changes.</span></span> <span data-ttu-id="97a6b-135">若要深入瞭解您可以說的內容, 請參閱使用您的語音來控制 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="97a6b-135">To learn more about what you can say, see Use your voice to control HoloLens.</span></span>

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a><span data-ttu-id="97a6b-136">我無法放置全息影像或查看我先前放置的全息影像。</span><span class="sxs-lookup"><span data-stu-id="97a6b-136">I can’t place holograms or see holograms I previously placed.</span></span>

<span data-ttu-id="97a6b-137">如果 HoloLens 無法對應或載入您的空間, 它會進入有限的模式, 而且您將無法放置全息影像或看到您所放置的全息影像。</span><span class="sxs-lookup"><span data-stu-id="97a6b-137">If HoloLens can’t map or load your space, it will enter Limited mode and you won’t be able to place holograms or see holograms you’ve placed.</span></span> <span data-ttu-id="97a6b-138">您可以嘗試以下方法：</span><span class="sxs-lookup"><span data-stu-id="97a6b-138">Here are some things to try:</span></span>
* <span data-ttu-id="97a6b-139">請確定您的環境中有足夠的光線, 讓 HoloLens 能夠看到並對應空間。</span><span class="sxs-lookup"><span data-stu-id="97a6b-139">Make sure there’s enough light in your environment so HoloLens can see and map the space.</span></span>
* <span data-ttu-id="97a6b-140">請確定您已連線到 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="97a6b-140">Make sure you’re connected to a Wi-Fi network.</span></span> <span data-ttu-id="97a6b-141">如果您未連線到 Wi-fi, HoloLens 就無法識別並載入已知的空間。</span><span class="sxs-lookup"><span data-stu-id="97a6b-141">If you’re not connected to Wi-Fi, HoloLens can’t identify and load a known space.</span></span>
* <span data-ttu-id="97a6b-142">如果您需要建立新的空間, 請連接到 Wi-fi, 然後重新開機 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="97a6b-142">If you need to create a new space, connect to Wi-Fi, then restart your HoloLens.</span></span>
* <span data-ttu-id="97a6b-143">若要查看正確的空間是否為作用中, 或若要手動載入空間, 請移至 [**設定** > ] [**系統** > **空間**]。</span><span class="sxs-lookup"><span data-stu-id="97a6b-143">To see if the correct space is active, or to manually load a space, go to **Settings** > **System** > **Spaces**.</span></span>
* <span data-ttu-id="97a6b-144">如果載入正確的空間, 但您仍然遇到問題, 則空間可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="97a6b-144">If the correct space is loaded and you’re still having problems, the space may be corrupt.</span></span> <span data-ttu-id="97a6b-145">若要修正此問題, 請選取空間, 然後選取 [移除]。</span><span class="sxs-lookup"><span data-stu-id="97a6b-145">To fix this, select the space, then select Remove.</span></span> <span data-ttu-id="97a6b-146">一旦移除空間之後, HoloLens 就會開始對應您的環境, 並建立新的空間。</span><span class="sxs-lookup"><span data-stu-id="97a6b-146">Once the space is removed, HoloLens will start mapping your surroundings and create a new space.</span></span>

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a><span data-ttu-id="97a6b-147">我的 HoloLens 經常進入有限的模式, 或顯示「追蹤遺失」的訊息。</span><span class="sxs-lookup"><span data-stu-id="97a6b-147">My HoloLens frequently enters Limited mode or shows a “Tracking lost” message.</span></span>

<span data-ttu-id="97a6b-148">如果您的裝置通常會顯示「受限模式」或「追蹤遺失」訊息, 請嘗試我的全息影像中的建議[不佳, 或正四處移動](#holograms-dont-look-good-or-are-moving-around)。</span><span class="sxs-lookup"><span data-stu-id="97a6b-148">If your device often shows a "limited mode" or "tracking lost" message, try the suggestions from [My Holograms don't look good or are moving around](#holograms-dont-look-good-or-are-moving-around).</span></span>

## <a name="my-hololens-cant-tell-what-space-im-in"></a><span data-ttu-id="97a6b-149">我的 HoloLens 無法分辨我的空間。</span><span class="sxs-lookup"><span data-stu-id="97a6b-149">My HoloLens can’t tell what space I’m in.</span></span>

<span data-ttu-id="97a6b-150">如果您的 HoloLens 無法自動識別並載入您所在的空間, 請確定您已連接到 Wi-fi、房間內有足夠的光線, 而且對等互連尚未進行任何重大變更。</span><span class="sxs-lookup"><span data-stu-id="97a6b-150">If your HoloLens can’t automatically identify and load the space you’re in, make sure you’re connected to Wi-Fi, there’s plenty of light in the room, and there haven’t been any major changes to the surroundings.</span></span> <span data-ttu-id="97a6b-151">您也可以手動載入空間, 或前往 [**設定** > ] [**系統** > **空間**] 管理您的空間。</span><span class="sxs-lookup"><span data-stu-id="97a6b-151">You can also load a space manually or manage your spaces by going to **Settings** > **System** > **Spaces**.</span></span>

## <a name="im-getting-a-low-disk-space-error"></a><span data-ttu-id="97a6b-152">我收到「磁碟空間不足」錯誤。</span><span class="sxs-lookup"><span data-stu-id="97a6b-152">I’m getting a “low disk space” error.</span></span>

<span data-ttu-id="97a6b-153">您必須執行下列一或多項作業來釋放一些儲存空間:</span><span class="sxs-lookup"><span data-stu-id="97a6b-153">You’ll need to free up some storage space by doing one or more of the following:</span></span>
* <span data-ttu-id="97a6b-154">刪除一些未使用的空間。</span><span class="sxs-lookup"><span data-stu-id="97a6b-154">Delete some unused spaces.</span></span> <span data-ttu-id="97a6b-155">移至 [**設定** > ] [**系統** > **空間**], 選取不再需要的空間, 然後選取 [**移除**]。</span><span class="sxs-lookup"><span data-stu-id="97a6b-155">Go to **Settings** > **System** > **Spaces**, select a space you no longer need, and then select **Remove**.</span></span>
* <span data-ttu-id="97a6b-156">移除您所放置的部分全息影像。</span><span class="sxs-lookup"><span data-stu-id="97a6b-156">Remove some of the holograms you’ve placed.</span></span>
* <span data-ttu-id="97a6b-157">刪除相片應用程式中的某些圖片和影片。</span><span class="sxs-lookup"><span data-stu-id="97a6b-157">Delete some pictures and videos in the Photos app.</span></span>
* <span data-ttu-id="97a6b-158">從 HoloLens 卸載一些應用程式。</span><span class="sxs-lookup"><span data-stu-id="97a6b-158">Uninstall some apps from your HoloLens.</span></span> <span data-ttu-id="97a6b-159">在 [所有應用程式] 清單中, 按住您要卸載的應用程式, 然後選取 [**卸載**]。</span><span class="sxs-lookup"><span data-stu-id="97a6b-159">In the All apps list, tap and hold the app you want to uninstall, and then select **Uninstall**.</span></span>

## <a name="my-hololens-cant-create-a-new-space"></a><span data-ttu-id="97a6b-160">我的 HoloLens 無法建立新的空間。</span><span class="sxs-lookup"><span data-stu-id="97a6b-160">My HoloLens can’t create a new space.</span></span>

<span data-ttu-id="97a6b-161">最有可能的問題是您的儲存空間不足。</span><span class="sxs-lookup"><span data-stu-id="97a6b-161">The most likely problem is that you’re running low on storage space.</span></span> <span data-ttu-id="97a6b-162">請嘗試上面的其中一個[提示](#im-getting-a-low-disk-space-error)來釋放一些磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="97a6b-162">Try one of the [tips above](#im-getting-a-low-disk-space-error) to free up some disk space.</span></span>
