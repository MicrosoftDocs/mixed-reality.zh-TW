---
title: 使用 Windows Mixed Reality 模擬器
description: Windows Mixed Reality 模擬器可讓您在電腦上測試混合現實應用程式，而不需要 Windows Mixed Reality 沉浸式頭戴式裝置。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality，模擬器，測試
ms.openlocfilehash: 686cac4e9ab4b3354767e22cd87d37ffbb508dea
ms.sourcegitcommit: 37816514b8fe20669c487774b86e80ec08edcadf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "81003294"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="00e21-104">使用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="00e21-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="00e21-105">Windows Mixed Reality 模擬器可讓您在電腦上測試混合現實應用程式，而不需要 Windows Mixed Reality 沉浸式頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="00e21-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="00e21-106">從 Windows 10 建立者更新開始提供。</span><span class="sxs-lookup"><span data-stu-id="00e21-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="00e21-107">[模擬器與 HoloLens 模擬器](using-the-hololens-emulator.md)類似，但模擬器不會使用虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="00e21-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="00e21-108">在模擬器中執行的應用程式會在您的 Windows 10 desktop 使用者會話中執行，就像是使用沉浸式耳機一樣。</span><span class="sxs-lookup"><span data-stu-id="00e21-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="00e21-109">在沉浸式耳機上，感應器通常會讀取的人力和環境輸入，會改為使用鍵盤、滑鼠或 Xbox 控制器來模擬。</span><span class="sxs-lookup"><span data-stu-id="00e21-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="00e21-110">應用程式不需要修改就可以在模擬器中執行，也不知道它們不會在沉浸式頭戴式裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="00e21-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="00e21-111">啟用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="00e21-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="00e21-112">從設定**啟用開發人員模式**-為開發人員 > 更新和安全性 ></span><span class="sxs-lookup"><span data-stu-id="00e21-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="00e21-113">從桌面啟動**混合現實入口網站**</span><span class="sxs-lookup"><span data-stu-id="00e21-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="00e21-114">如果這是您第一次啟動入口網站，您必須完成設定體驗</span><span class="sxs-lookup"><span data-stu-id="00e21-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="00e21-115">按一下 [**開始**使用]</span><span class="sxs-lookup"><span data-stu-id="00e21-115">Click **Get started**</span></span>
   2. <span data-ttu-id="00e21-116">按一下 [**我同意**接受合約]</span><span class="sxs-lookup"><span data-stu-id="00e21-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="00e21-117">按一下 **[設定以模擬（適用于開發人員）** ]，在不使用實體裝置的情況下繼續執行安裝程式</span><span class="sxs-lookup"><span data-stu-id="00e21-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="00e21-118">按一下 [**設定**] 以確認您的選擇</span><span class="sxs-lookup"><span data-stu-id="00e21-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="00e21-119">按一下混合現實入口網站左側的 [**適用于開發人員**] 按鈕</span><span class="sxs-lookup"><span data-stu-id="00e21-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="00e21-120">將模擬切換切換為**開啟**</span><span class="sxs-lookup"><span data-stu-id="00e21-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="00e21-121">根據預設，啟用模擬會安裝並啟用左方模擬的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="00e21-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="00e21-122">在 Windows 10 5 月2019更新之前，安裝模擬的 6 DOF 控制器需要系統管理員許可權。</span><span class="sxs-lookup"><span data-stu-id="00e21-122">Prior to the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="00e21-123">您必須接受 [使用者帳戶控制] 對話方塊（如果有出現的話）。</span><span class="sxs-lookup"><span data-stu-id="00e21-123">You must accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="00e21-124">您現在應該使用模擬來執行！</span><span class="sxs-lookup"><span data-stu-id="00e21-124">You should now be running with simulation!</span></span>

<span data-ttu-id="00e21-125">如果您想要停用 [設定] 中的 [開發人員模式]，您應該先在混合現實入口網站的 [**適用于開發人員**] 區段中，將模擬切換切換為**關閉**。</span><span class="sxs-lookup"><span data-stu-id="00e21-125">If you want to disable Developer mode in Settings, you should first turn the Simulation toggle switch to **Off** in the **For developers** section of the Mixed Reality Portal.</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="00e21-126">將應用程式部署到混合現實模擬器</span><span class="sxs-lookup"><span data-stu-id="00e21-126">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="00e21-127">由於模擬器會在沒有虛擬機器的本機電腦上執行，因此您可以在進行偵錯工具時，直接將通用 Windows 應用程式部署到**本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="00e21-127">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="00e21-128">基本模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="00e21-128">Basic simulator input</span></span>

<span data-ttu-id="00e21-129">控制模擬器非常類似于許多常見的3D 視頻遊戲和[HoloLens 模擬器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="00e21-129">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="00e21-130">可用的輸入選項包括使用鍵盤、滑鼠或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="00e21-130">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="00e21-131">您可以藉由將模擬使用者的動作導向沉浸式耳機來控制模擬器。</span><span class="sxs-lookup"><span data-stu-id="00e21-131">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="00e21-132">您的動作會移動模擬的使用者，並與回應在沉浸式頭戴式裝置上的應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="00e21-132">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="00e21-133">**向前走、向後走、向左走和向右走** - 使用鍵盤上的 W、A、S 和 D 鍵或 Xbox 控制器上的左搖桿。</span><span class="sxs-lookup"><span data-stu-id="00e21-133">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="00e21-134">**向上看、向下看、向左看和向右看** - 按一下並拖曳滑鼠、使用鍵盤上的方向鍵或 Xbox 控制器上的右搖桿。</span><span class="sxs-lookup"><span data-stu-id="00e21-134">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="00e21-135">**動作按鈕按下控制器**-以滑鼠右鍵按一下滑鼠，在鍵盤上按下 enter 鍵，或使用 Xbox 控制器上的 [A] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="00e21-135">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="00e21-136">[**首頁] 按鈕按下 [控制器**]-按下鍵盤上的 Windows 鍵或 F2 鍵，或按 Xbox 控制器上的 B 按鈕。</span><span class="sxs-lookup"><span data-stu-id="00e21-136">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="00e21-137">**控制器移動以進行滾動**-按住 ALT 鍵，按住滑鼠右鍵，然後向上/向下拖曳滑鼠，或在 Xbox 控制器中按住右觸發程式，然後按下向下鍵並上下移動。</span><span class="sxs-lookup"><span data-stu-id="00e21-137">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="00e21-138">追蹤的控制器</span><span class="sxs-lookup"><span data-stu-id="00e21-138">Tracked controllers</span></span>

<span data-ttu-id="00e21-139">混合現實模擬器可以模擬最多兩個手持的追蹤動作控制器。</span><span class="sxs-lookup"><span data-stu-id="00e21-139">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="00e21-140">使用混合現實入口網站中的切換參數來啟用它們。</span><span class="sxs-lookup"><span data-stu-id="00e21-140">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="00e21-141">每個模擬控制器都具有：</span><span class="sxs-lookup"><span data-stu-id="00e21-141">Each simulated controller has:</span></span>
* <span data-ttu-id="00e21-142">空間中的位置和方向</span><span class="sxs-lookup"><span data-stu-id="00e21-142">Position and orientation in space</span></span>
* <span data-ttu-id="00e21-143">首頁按鈕</span><span class="sxs-lookup"><span data-stu-id="00e21-143">Home button</span></span>
* <span data-ttu-id="00e21-144">功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="00e21-144">Menu button</span></span>
* <span data-ttu-id="00e21-145">[抓握] 按鈕</span><span class="sxs-lookup"><span data-stu-id="00e21-145">Grip button</span></span>
* <span data-ttu-id="00e21-146">觸控板</span><span class="sxs-lookup"><span data-stu-id="00e21-146">Touchpad</span></span>
* <span data-ttu-id="00e21-147">上下</span><span class="sxs-lookup"><span data-stu-id="00e21-147">Thumbstick</span></span>
* <span data-ttu-id="00e21-148">電池音量</span><span class="sxs-lookup"><span data-stu-id="00e21-148">Battery level</span></span>

## <a name="see-also"></a><span data-ttu-id="00e21-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00e21-149">See also</span></span>
* [<span data-ttu-id="00e21-150">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="00e21-150">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="00e21-151">Advanced Mixed Reality 模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="00e21-151">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="00e21-152">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="00e21-152">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="00e21-153">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="00e21-153">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
