---
title: 重設或復原您的 HoloLens
description: 基本和進階重新啟動或重設您的 HoloLens 的指示。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 作法，請重新啟動、 重設、 復原，硬重設、 軟重設、 電源循環，HoloLens，關閉
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591764"
---
# <a name="reset-or-recover-your-hololens"></a><span data-ttu-id="0d4dc-104">重設或復原您的 HoloLens</span><span class="sxs-lookup"><span data-stu-id="0d4dc-104">Reset or recover your HoloLens</span></span>

<span data-ttu-id="0d4dc-105">如果您遇到您 HoloLens，您可能想要嘗試重新啟動的問題，請重設，或甚至重新 flash 與裝置復原。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-105">If you’re experiencing problems with your HoloLens you may want to try a restart, reset, or even re-flash with device recovery.</span></span> <span data-ttu-id="0d4dc-106">本文件將引導您完成連續的建議步驟。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-106">This document will guide you through the recommended steps in succession.</span></span>

## <a name="perform-a-device-reboot"></a><span data-ttu-id="0d4dc-107">執行裝置重新開機</span><span class="sxs-lookup"><span data-stu-id="0d4dc-107">Perform a device reboot</span></span>

<span data-ttu-id="0d4dc-108">如果您的 HoloLens 發生問題，或沒有回應，則先試著透過其中一種下列方法。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-108">If your HoloLens is experiencing issues or is unresponsive, first try rebooting it via one of the below methods.</span></span>

### <a name="perform-a-safe-reboot-via-cortana"></a><span data-ttu-id="0d4dc-109">執行安全的重新開機，透過 Cortana</span><span class="sxs-lookup"><span data-stu-id="0d4dc-109">Perform a safe reboot via Cortana</span></span>

<span data-ttu-id="0d4dc-110">若要重新啟動 HoloLens 最安全的方法是透過 Cortana。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-110">The safest way to reboot the HoloLens is via Cortana.</span></span> <span data-ttu-id="0d4dc-111">這通常是絕佳的第一個步驟時遇到的問題與 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="0d4dc-111">This is generally a great first-step when experiencing an issue with HoloLens:</span></span>
1. <span data-ttu-id="0d4dc-112">將放在您的裝置</span><span class="sxs-lookup"><span data-stu-id="0d4dc-112">Put on your device</span></span>
2. <span data-ttu-id="0d4dc-113">請確定開機、 登入的使用者和裝置未在等待密碼來解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-113">Make sure it’s powered on, a user is logged in, and the device is not waiting for a password to unlock it.</span></span>
3. <span data-ttu-id="0d4dc-114">說 「 嘿 Cortana，重新啟動 」 或 「 嘿 Cortana，重新啟動。 」</span><span class="sxs-lookup"><span data-stu-id="0d4dc-114">Say “Hey Cortana, reboot” or "Hey Cortana, restart."</span></span>
4. <span data-ttu-id="0d4dc-115">當她認可她將會要求您確認。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-115">When she acknowledges she will ask you for confirmation.</span></span> <span data-ttu-id="0d4dc-116">等候另一個則用於後完成她的問題，表示她用來接聽以您要播放的音效，然後說出"Yes"。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-116">Wait a second for a sound to play after she has finished her question, indicating she is listening to you and then say “Yes.”</span></span>
5. <span data-ttu-id="0d4dc-117">裝置會立即重新開機/重新啟動。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-117">The device will now reboot/restart.</span></span>

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a><span data-ttu-id="0d4dc-118">執行 Windows Device Portal 透過安全的重新開機</span><span class="sxs-lookup"><span data-stu-id="0d4dc-118">Perform a safe reboot via Windows Device Portal</span></span>

<span data-ttu-id="0d4dc-119">如果上述無法運作，您可以嘗試重新啟動裝置，透過[Windows Device Portal](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-119">If the above doesn't work, you can try to reboot the device via [Windows Device Portal](using-the-windows-device-portal.md).</span></span> <span data-ttu-id="0d4dc-120">在右上角沒有重新開機/關機選項的裝置。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-120">In the upper right corner, there is an option to restart/shutdown the device.</span></span>

### <a name="perform-a-safe-reboot-via-the-power-button"></a><span data-ttu-id="0d4dc-121">執行 [電源] 按鈕透過安全的重新開機</span><span class="sxs-lookup"><span data-stu-id="0d4dc-121">Perform a safe reboot via the power button</span></span>

<span data-ttu-id="0d4dc-122">如果您仍無法重新啟動您的裝置，您可以嘗試發出透過 [電源] 按鈕重新開機：</span><span class="sxs-lookup"><span data-stu-id="0d4dc-122">If you still can't reboot your device, you can try to issue a reboot via the power button:</span></span>
1. <span data-ttu-id="0d4dc-123">按住電源按鈕的 5 秒</span><span class="sxs-lookup"><span data-stu-id="0d4dc-123">Press and hold the power button for 5 seconds</span></span>
   1. <span data-ttu-id="0d4dc-124">1 秒之後, 您會看到所有 5 個 Led 照亮，然後慢慢關閉由右至左</span><span class="sxs-lookup"><span data-stu-id="0d4dc-124">After 1 second, you will see all 5 LEDs illuminate, then slowly turn off from right to left</span></span>
   2. <span data-ttu-id="0d4dc-125">在 5 秒之後, 所有的 Led 將會關閉，表示已成功發出關機命令</span><span class="sxs-lookup"><span data-stu-id="0d4dc-125">After 5 seconds, all LEDs will be off, indicating the shutdown command was issued successfully</span></span>
   3. <span data-ttu-id="0d4dc-126">請注意，務必要停止所有的 Led 已關閉後立即按下按鈕</span><span class="sxs-lookup"><span data-stu-id="0d4dc-126">Note, it’s important to stop pressing the button immediately after all the LEDs have turned off</span></span>
2. <span data-ttu-id="0d4dc-127">等候 1 分鐘才能完全成功關閉。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-127">Wait 1 minute for the shutdown to cleanly succeed.</span></span> <span data-ttu-id="0d4dc-128">請注意，關閉可能仍是進行中，即使會顯示已關閉</span><span class="sxs-lookup"><span data-stu-id="0d4dc-128">Note that the shutdown may still be in progress even if the displays are off</span></span>
3. <span data-ttu-id="0d4dc-129">透過按住電源按鈕 1 秒再次在裝置上的電源</span><span class="sxs-lookup"><span data-stu-id="0d4dc-129">Power on the device again by pressing and holding the power button for 1 second</span></span>

### <a name="perform-an-unsafe-forced-reboot"></a><span data-ttu-id="0d4dc-130">執行不安全的強制重新開機</span><span class="sxs-lookup"><span data-stu-id="0d4dc-130">Perform an unsafe forced reboot</span></span>

<span data-ttu-id="0d4dc-131">如果上述方法都能夠成功地重新啟動您的裝置，您可以強制重新開機。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-131">If none of the above methods are able to successfully reboot your device, you can force a reboot.</span></span> <span data-ttu-id="0d4dc-132">請注意，這個方法相當於從 HoloLens，提取電池，因此是危險的作業，而這可能導致您的裝置處於損毀的狀態。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-132">Note that this method is equivalent to pulling the battery from the HoloLens, and as such, is a dangerous operation which may leave your device in a corrupt state.</span></span> 

>[!WARNING]
><span data-ttu-id="0d4dc-133">這是可能會造成損害的方法，且應該僅用於萬一上述的方法，沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-133">This is a potentially harmful method and should only be used in the event none of the above methods work.</span></span>

1. <span data-ttu-id="0d4dc-134">按住不放在至少 10 秒的時間的電源按鈕</span><span class="sxs-lookup"><span data-stu-id="0d4dc-134">Press and hold the power button for at least 10 seconds</span></span>
   * <span data-ttu-id="0d4dc-135">可以在按住按鈕超過 10 秒</span><span class="sxs-lookup"><span data-stu-id="0d4dc-135">It’s okay to hold the button for longer than 10 seconds</span></span>
   * <span data-ttu-id="0d4dc-136">它可以放心地忽略任何 LED 活動</span><span class="sxs-lookup"><span data-stu-id="0d4dc-136">It’s safe to ignore any LED activity</span></span>
2. <span data-ttu-id="0d4dc-137">放開按鈕，等候 2-3 秒</span><span class="sxs-lookup"><span data-stu-id="0d4dc-137">Release the button and wait 2-3 seconds</span></span>
3. <span data-ttu-id="0d4dc-138">透過按住電源按鈕 1 秒再次在裝置上的電源</span><span class="sxs-lookup"><span data-stu-id="0d4dc-138">Power on the device again by pressing and holding the power button for 1 second</span></span>

## <a name="reset-the-device-to-a-factory-clean-state"></a><span data-ttu-id="0d4dc-139">將裝置重設為原廠的初始狀態</span><span class="sxs-lookup"><span data-stu-id="0d4dc-139">Reset the device to a factory clean state</span></span>

<span data-ttu-id="0d4dc-140">如果您 HoloLens 重新開機之後仍發生問題，您可以嘗試重設為原廠的初始狀態。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-140">If your HoloLens is still experiencing issues after rebooting, you can try resetting it to a factory clean state.</span></span> <span data-ttu-id="0d4dc-141">如果您重設您的裝置，所有您個人資料、 應用程式和設定將被清除。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-141">If you reset your device, all your personal data, apps, and settings will be erased.</span></span> <span data-ttu-id="0d4dc-142">重設只會安裝最新的 Windows 全像攝影版安裝的版本，您必須重做所有的初始化步驟 (校正、 連線到 WiFi、 建立使用者帳戶、 下載應用程式等等.)。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-142">Resetting will only install the latest installed version of Windows Holographic and you will have to redo all the initialization steps (calibrate, connect to WiFi, create a user account, download apps, etc…).</span></span>
1. <span data-ttu-id="0d4dc-143">啟動**設定**應用程式]-> [**更新** -> **重設**</span><span class="sxs-lookup"><span data-stu-id="0d4dc-143">Launch the **Settings** app -> **Update** -> **Reset**</span></span>
2. <span data-ttu-id="0d4dc-144">選取 **重設裝置**選項，然後讀取 確認 對話方塊</span><span class="sxs-lookup"><span data-stu-id="0d4dc-144">Select the **Reset device** option and read the confirmation dialog</span></span>
3. <span data-ttu-id="0d4dc-145">如果您同意將裝置重設，裝置會重新啟動，並顯示一組旋轉 gears 一個進度列</span><span class="sxs-lookup"><span data-stu-id="0d4dc-145">If you agree to reset your device, the device will reboot and display a set of spinning gears with a progress bar</span></span>
4. <span data-ttu-id="0d4dc-146">等候約 30 分鐘的時間才能完成此程序</span><span class="sxs-lookup"><span data-stu-id="0d4dc-146">Wait about 30 minutes for this process to complete</span></span>
5. <span data-ttu-id="0d4dc-147">重設會完成，而且裝置會重新開機到全新體驗</span><span class="sxs-lookup"><span data-stu-id="0d4dc-147">The reset will complete and the device will reboot into the out of the box experience</span></span>

## <a name="perform-a-full-device-recovery"></a><span data-ttu-id="0d4dc-148">執行完整裝置復原</span><span class="sxs-lookup"><span data-stu-id="0d4dc-148">Perform a full device recovery</span></span>

<span data-ttu-id="0d4dc-149">如果您的裝置是執行上述選項之後,**仍然**凍結，沒有回應，或未發生更新或軟體問題可以使用 Windows Device Recovery Tool 加以復原。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-149">If, after performing the above options, your device is **still** frozen, unresponsive, or experiencing update or software problems you can recover it using the Windows Device Recovery Tool.</span></span> <span data-ttu-id="0d4dc-150">復原您的裝置是類似重設，因為它將會清除所有的使用者內容，在裝置上，包括應用程式、 遊戲、 相片、 使用者帳戶等。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-150">Recovering your device is similar to resetting it in the sense that it will erase all user content on the device, including apps, games, photos, user accounts, and more.</span></span> <span data-ttu-id="0d4dc-151">可能的話，請備份您想要保留的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-151">If possible, backup any information you want to keep.</span></span>

<span data-ttu-id="0d4dc-152">若要完全復原您的 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="0d4dc-152">To fully recover your HoloLens:</span></span>
1. <span data-ttu-id="0d4dc-153">中斷您的電腦上的所有電話和 Windows 裝置</span><span class="sxs-lookup"><span data-stu-id="0d4dc-153">Disconnect all phones and Windows devices from your PC</span></span>
2. <span data-ttu-id="0d4dc-154">安裝並啟動[Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) 在您的電腦上</span><span class="sxs-lookup"><span data-stu-id="0d4dc-154">Install and launch the [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) on your PC</span></span>
3. <span data-ttu-id="0d4dc-155">它隨附您電腦使用 micro USB 纜線連接您 HoloLens</span><span class="sxs-lookup"><span data-stu-id="0d4dc-155">Connect your HoloLens to your PC using the micro-USB cable it came with</span></span>
   * <span data-ttu-id="0d4dc-156">請注意，並非所有的 USB 纜線與眾不同之處。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-156">Note that not all USB cables are created equal.</span></span> <span data-ttu-id="0d4dc-157">即使您已使用另一個的纜線已成功，此流程會公開其中纜線可能沒那麼好的新狀態。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-157">Even if you’ve been using another cable successfully, this flow will expose new states where the cable may not perform as well.</span></span> <span data-ttu-id="0d4dc-158">您 HoloLens 隨附的一個是最佳且最並經過充分測試的選項</span><span class="sxs-lookup"><span data-stu-id="0d4dc-158">The one your HoloLens came with is the best and most well tested option</span></span>
4. <span data-ttu-id="0d4dc-159">如果此工具會自動偵測您的裝置會顯示 HoloLens 圖格。</span><span class="sxs-lookup"><span data-stu-id="0d4dc-159">If the tool automatically detects your device it will display a HoloLens tile.</span></span> <span data-ttu-id="0d4dc-160">按一下它，然後遵循指示完成程序</span><span class="sxs-lookup"><span data-stu-id="0d4dc-160">Click it and follow the instructions to complete the process</span></span>

>[!NOTE]
><span data-ttu-id="0d4dc-161">WDRT 可能復原較舊版本的 Windows 全像攝影版; 您的裝置您可能需要安裝更新之後閃爍</span><span class="sxs-lookup"><span data-stu-id="0d4dc-161">WDRT may recover your device to an older version of Windows Holographic; you may need to install updates after flashing</span></span>

<span data-ttu-id="0d4dc-162">如果無法自動偵測您的裝置，請嘗試下列工具：</span><span class="sxs-lookup"><span data-stu-id="0d4dc-162">If the tool is unable to detect your device automatically, try the following:</span></span>
1. <span data-ttu-id="0d4dc-163">重新啟動您的電腦和重試一次 （這會修正大部分的問題）</span><span class="sxs-lookup"><span data-stu-id="0d4dc-163">Reboot your PC and try again (this fixes most issues)</span></span>
2. <span data-ttu-id="0d4dc-164">按一下 [**偵測不到我的裝置] 按鈕**，選擇**Microsoft HoloLens**，並遵循螢幕上指示的其餘部分</span><span class="sxs-lookup"><span data-stu-id="0d4dc-164">Click the **My device was not detected button**, choose **Microsoft HoloLens**, and follow the rest of the instructions on the screen</span></span>
