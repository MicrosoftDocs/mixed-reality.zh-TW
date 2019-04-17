---
title: HoloLens 進行疑難排解
description: Microsoft HoloLens 的疑難排解步驟。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 問題、 bug、 疑難排解、 修正、 協助支援，HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591133"
---
# <a name="hololens-troubleshooting"></a><span data-ttu-id="e6b90-104">HoloLens 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="e6b90-104">HoloLens Troubleshooting</span></span>

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a><span data-ttu-id="e6b90-105">我的 HoloLens 沒有回應，或將不會開機</span><span class="sxs-lookup"><span data-stu-id="e6b90-105">My HoloLens is unresponsive or won’t boot</span></span>

<span data-ttu-id="e6b90-106">如果您的 HoloLens 不開機：</span><span class="sxs-lookup"><span data-stu-id="e6b90-106">If your HoloLens won't boot:</span></span>
* <span data-ttu-id="e6b90-107">如果不淺的 Led，由 [電源] 按鈕，或只有 1 會簡短地閃爍 LED，您可能需要向您 HoloLens 收取費用。</span><span class="sxs-lookup"><span data-stu-id="e6b90-107">If the LEDs by the power button don't light up, or only 1 LED briefly blinks, you may need to charge your HoloLens.</span></span>
* <span data-ttu-id="e6b90-108">如果 Led 亮起時按下電源按鈕，但您無法看到任何項目在顯示器上，，保留 [電源] 按鈕，直到全部 5 份由 [電源] 按鈕的 Led 將關閉。</span><span class="sxs-lookup"><span data-stu-id="e6b90-108">If the LEDs light up when you press the power button but you can't see anything on the displays, hold the power button until all 5 of the LEDs by the power button turn off.</span></span>

<span data-ttu-id="e6b90-109">如果已凍結或沒有回應，則會變成您 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="e6b90-109">If your HoloLens becomes frozen or unresponsive:</span></span>
* <span data-ttu-id="e6b90-110">關閉您 HoloLens 藉由按下電源按鈕，直到全部 5 份由 [電源] 按鈕的 Led 本身，開啟或關閉 10 秒的時間如果 Led 沒有回應。</span><span class="sxs-lookup"><span data-stu-id="e6b90-110">Turn off your HoloLens by pressing the power button until all 5 of the LEDs by the power button turn themselves off, or for 10 seconds if the LEDs are unresponsive.</span></span> <span data-ttu-id="e6b90-111">按下電源按鈕開機。</span><span class="sxs-lookup"><span data-stu-id="e6b90-111">Press the power button again to boot.</span></span>

<span data-ttu-id="e6b90-112">如果這些步驟沒有作用：</span><span class="sxs-lookup"><span data-stu-id="e6b90-112">If these steps don't work:</span></span>
* <span data-ttu-id="e6b90-113">您可以嘗試[復原您的裝置](reset-or-recover-your-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="e6b90-113">You can try [recovering your device](reset-or-recover-your-hololens.md).</span></span>

## <a name="holograms-dont-look-good-or-are-moving-around"></a><span data-ttu-id="e6b90-114">全像投影的效果不好或已移動。</span><span class="sxs-lookup"><span data-stu-id="e6b90-114">Holograms don't look good or are moving around.</span></span>

<span data-ttu-id="e6b90-115">如果您全像投影不穩定、 跳動，或是看起來不正確，請嘗試這些修正程式的其中一個：</span><span class="sxs-lookup"><span data-stu-id="e6b90-115">If your holograms are unstable, jumpy, or don’t look right, try one of these fixes:</span></span>
* <span data-ttu-id="e6b90-116">清除裝置上面，並確定不會阻礙感應器。</span><span class="sxs-lookup"><span data-stu-id="e6b90-116">Clean your device visor and make sure nothing is obstructing the sensors.</span></span>
* <span data-ttu-id="e6b90-117">請確定您的聊天室中沒有足夠的光線。</span><span class="sxs-lookup"><span data-stu-id="e6b90-117">Make sure there’s enough light in your room.</span></span>
* <span data-ttu-id="e6b90-118">請嘗試四處跑，並查看鳥瞰因此 HoloLens 就能掃描它們更完整。</span><span class="sxs-lookup"><span data-stu-id="e6b90-118">Try walking around and looking at your surroundings so HoloLens can scan them more completely.</span></span>
* <span data-ttu-id="e6b90-119">請嘗試執行校正應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6b90-119">Try running the Calibration app.</span></span> <span data-ttu-id="e6b90-120">它會校準適合眼睛您 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e6b90-120">It calibrates your HoloLens to work best for your eyes.</span></span> <span data-ttu-id="e6b90-121">移至**設定** > **System** > **公用程式**。</span><span class="sxs-lookup"><span data-stu-id="e6b90-121">Go to **Settings** > **System** > **Utilities**.</span></span> <span data-ttu-id="e6b90-122">在 [校正] 中，選取**開啟校正**。</span><span class="sxs-lookup"><span data-stu-id="e6b90-122">Under Calibration, select **Open Calibration**.</span></span>
* <span data-ttu-id="e6b90-123">如果您仍然無法執行校正應用程式之後，使用感應器調整應用程式來微調您的裝置感應器。</span><span class="sxs-lookup"><span data-stu-id="e6b90-123">If you’re still having trouble after running the Calibration app, use the Sensor Tuning app to tune your device sensors.</span></span> <span data-ttu-id="e6b90-124">移至**設定** > **System** > **公用程式**。</span><span class="sxs-lookup"><span data-stu-id="e6b90-124">Go to **Settings** > **System** > **Utilities**.</span></span> <span data-ttu-id="e6b90-125">在微調感應器，選取**開啟感應器調整**。</span><span class="sxs-lookup"><span data-stu-id="e6b90-125">Under Sensor tuning, select **Open Sensor Tuning**.</span></span>

## <a name="hololens-doesnt-respond-to-my-gestures"></a><span data-ttu-id="e6b90-126">HoloLens 我筆勢不會回應。</span><span class="sxs-lookup"><span data-stu-id="e6b90-126">HoloLens doesn’t respond to my gestures.</span></span>

<span data-ttu-id="e6b90-127">若要確定 HoloLens 可以看到您的筆勢，保留您的手在軌跡框架中，以擴充您的任一邊的英呎數。</span><span class="sxs-lookup"><span data-stu-id="e6b90-127">To make sure HoloLens can see your gestures, keep your hand in the gesture frame, which extends a couple of feet on either side of you.</span></span> <span data-ttu-id="e6b90-128">當 HoloLens 可以看到您的手時，游標會變成從一個點的環形。</span><span class="sxs-lookup"><span data-stu-id="e6b90-128">When HoloLens can see your hand, the cursor will change from a dot to a ring.</span></span> <span data-ttu-id="e6b90-129">進一步了解如何[筆勢](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="e6b90-129">Learn more about using [gestures](gestures.md).</span></span>

<span data-ttu-id="e6b90-130">如果您的環境是否太深，可能不會看到您的手，因此請確定沒有足夠的光線 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e6b90-130">If your environment is too dark, HoloLens might not see your hand, so make sure there’s enough light.</span></span>

<span data-ttu-id="e6b90-131">如果您上面有指紋或模糊，請使用清除隨附輕輕清除您上面 HoloLens 的清潔 microfiber。</span><span class="sxs-lookup"><span data-stu-id="e6b90-131">If your visor has fingerprints or smudge, please use the microfiber cleaning cloth that came with the HoloLens to clean your visor gently.</span></span>

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a><span data-ttu-id="e6b90-132">HoloLens 不會回應我語音命令。</span><span class="sxs-lookup"><span data-stu-id="e6b90-132">HoloLens doesn’t respond to my voice commands.</span></span>

<span data-ttu-id="e6b90-133">如果 Cortana 沒有回應您的語音命令，請確定已開啟 Cortana。</span><span class="sxs-lookup"><span data-stu-id="e6b90-133">If Cortana isn’t responding to your voice commands, make sure Cortana is turned on.</span></span> <span data-ttu-id="e6b90-134">在所有的應用程式清單中，選取 [Cortana >] 功能表 > Notebook > 來變更設定。</span><span class="sxs-lookup"><span data-stu-id="e6b90-134">On the All apps list, select Cortana > Menu > Notebook > Settings to make changes.</span></span> <span data-ttu-id="e6b90-135">若要深入了解您可以說，請參閱使用語音來控制 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e6b90-135">To learn more about what you can say, see Use your voice to control HoloLens.</span></span>

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a><span data-ttu-id="e6b90-136">我無法將全像投影，或請參閱先前放置全像投影。</span><span class="sxs-lookup"><span data-stu-id="e6b90-136">I can’t place holograms or see holograms I previously placed.</span></span>

<span data-ttu-id="e6b90-137">如果 HoloLens 無法對應，或載入您的空間，它會進入受限制的模式，並無法將全像投影，或請參閱您放入全像投影。</span><span class="sxs-lookup"><span data-stu-id="e6b90-137">If HoloLens can’t map or load your space, it will enter Limited mode and you won’t be able to place holograms or see holograms you’ve placed.</span></span> <span data-ttu-id="e6b90-138">您可以嘗試以下方法：</span><span class="sxs-lookup"><span data-stu-id="e6b90-138">Here are some things to try:</span></span>
* <span data-ttu-id="e6b90-139">請確定有足夠光您的環境中讓 HoloLens 可以看到，並將對應的空間。</span><span class="sxs-lookup"><span data-stu-id="e6b90-139">Make sure there’s enough light in your environment so HoloLens can see and map the space.</span></span>
* <span data-ttu-id="e6b90-140">請確定您已連接到 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="e6b90-140">Make sure you’re connected to a Wi-Fi network.</span></span> <span data-ttu-id="e6b90-141">如果您未連線至 Wi-fi，HoloLens 無法識別，並載入已知的空間。</span><span class="sxs-lookup"><span data-stu-id="e6b90-141">If you’re not connected to Wi-Fi, HoloLens can’t identify and load a known space.</span></span>
* <span data-ttu-id="e6b90-142">如果您需要建立新的空間，連接到 Wi-fi，然後重新啟動您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e6b90-142">If you need to create a new space, connect to Wi-Fi, then restart your HoloLens.</span></span>
* <span data-ttu-id="e6b90-143">若要查看正確的空間是否作用中，或手動載入的空間，請前往**設定** > **System** > **空間**。</span><span class="sxs-lookup"><span data-stu-id="e6b90-143">To see if the correct space is active, or to manually load a space, go to **Settings** > **System** > **Spaces**.</span></span>
* <span data-ttu-id="e6b90-144">如果在載入正確的空間，您仍遇到問題，空間可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="e6b90-144">If the correct space is loaded and you’re still having problems, the space may be corrupt.</span></span> <span data-ttu-id="e6b90-145">若要修正此問題，選取的磁碟空間，然後選取 [移除]。</span><span class="sxs-lookup"><span data-stu-id="e6b90-145">To fix this, select the space, then select Remove.</span></span> <span data-ttu-id="e6b90-146">一旦移除空間時，會開始對應鳥瞰 HoloLens，並建立新的空間。</span><span class="sxs-lookup"><span data-stu-id="e6b90-146">Once the space is removed, HoloLens will start mapping your surroundings and create a new space.</span></span>

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a><span data-ttu-id="e6b90-147">我 HoloLens 經常會進入 Limited 模式下，或顯示 「 追蹤遺失 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="e6b90-147">My HoloLens frequently enters Limited mode or shows a “Tracking lost” message.</span></span>

<span data-ttu-id="e6b90-148">如果您的裝置通常會顯示 「 有限的模式 」 或 「 追蹤遺失 」 訊息，請嘗試從建議[My 全像投影的效果不好或已移動](#holograms-dont-look-good-or-are-moving-around)。</span><span class="sxs-lookup"><span data-stu-id="e6b90-148">If your device often shows a "limited mode" or "tracking lost" message, try the suggestions from [My Holograms don't look good or are moving around](#holograms-dont-look-good-or-are-moving-around).</span></span>

## <a name="my-hololens-cant-tell-what-space-im-in"></a><span data-ttu-id="e6b90-149">我的 HoloLens 無法分辨我所在的空間。</span><span class="sxs-lookup"><span data-stu-id="e6b90-149">My HoloLens can’t tell what space I’m in.</span></span>

<span data-ttu-id="e6b90-150">如果您的 HoloLens 無法自動識別並載入您的空間，請確定您已連線至 Wi-fi、 還有很多 light 中的空間，而且尚未恍神進行重大變更。</span><span class="sxs-lookup"><span data-stu-id="e6b90-150">If your HoloLens can’t automatically identify and load the space you’re in, make sure you’re connected to Wi-Fi, there’s plenty of light in the room, and there haven’t been any major changes to the surroundings.</span></span> <span data-ttu-id="e6b90-151">您也可以手動載入的空間，或管理您的空間，方法是前往**設定** > **System** > **空間**。</span><span class="sxs-lookup"><span data-stu-id="e6b90-151">You can also load a space manually or manage your spaces by going to **Settings** > **System** > **Spaces**.</span></span>

## <a name="im-getting-a-low-disk-space-error"></a><span data-ttu-id="e6b90-152">我收到 「 磁碟空間不足 」 錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6b90-152">I’m getting a “low disk space” error.</span></span>

<span data-ttu-id="e6b90-153">您必須釋出一些儲存空間藉由一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="e6b90-153">You’ll need to free up some storage space by doing one or more of the following:</span></span>
* <span data-ttu-id="e6b90-154">刪除一些未使用的空格。</span><span class="sxs-lookup"><span data-stu-id="e6b90-154">Delete some unused spaces.</span></span> <span data-ttu-id="e6b90-155">移至**設定** > **System** > **空間**，選取您不再需要，然後選取的空間**移除**.</span><span class="sxs-lookup"><span data-stu-id="e6b90-155">Go to **Settings** > **System** > **Spaces**, select a space you no longer need, and then select **Remove**.</span></span>
* <span data-ttu-id="e6b90-156">請移除一些放入全像投影。</span><span class="sxs-lookup"><span data-stu-id="e6b90-156">Remove some of the holograms you’ve placed.</span></span>
* <span data-ttu-id="e6b90-157">請刪除一些圖片和影片，相片應用程式中。</span><span class="sxs-lookup"><span data-stu-id="e6b90-157">Delete some pictures and videos in the Photos app.</span></span>
* <span data-ttu-id="e6b90-158">解除安裝某些應用程式，以從您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e6b90-158">Uninstall some apps from your HoloLens.</span></span> <span data-ttu-id="e6b90-159">在所有的應用程式清單中，按住您要解除安裝，然後選取 應用程式**解除安裝**。</span><span class="sxs-lookup"><span data-stu-id="e6b90-159">In the All apps list, tap and hold the app you want to uninstall, and then select **Uninstall**.</span></span>

## <a name="my-hololens-cant-create-a-new-space"></a><span data-ttu-id="e6b90-160">我的 HoloLens 無法建立新的空間。</span><span class="sxs-lookup"><span data-stu-id="e6b90-160">My HoloLens can’t create a new space.</span></span>

<span data-ttu-id="e6b90-161">最可能的問題是，您要儲存體空間不足。</span><span class="sxs-lookup"><span data-stu-id="e6b90-161">The most likely problem is that you’re running low on storage space.</span></span> <span data-ttu-id="e6b90-162">請嘗試[上述的祕訣](#im-getting-a-low-disk-space-error)以釋放一些磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="e6b90-162">Try one of the [tips above](#im-getting-a-low-disk-space-error) to free up some disk space.</span></span>
