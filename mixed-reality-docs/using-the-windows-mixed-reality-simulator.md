---
title: 使用 Windows Mixed Reality 模擬器
description: Windows Mixed Reality 模擬器可讓您測試您的電腦，而不需要 Windows Mixed Reality 沈浸式耳機上的混合的實境應用程式。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows 混合現實情況下，模擬器測試
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580696"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="1c3df-104">使用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="1c3df-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="1c3df-105">Windows Mixed Reality 模擬器可讓您測試您的電腦，而不需要 Windows Mixed Reality 沈浸式耳機上的混合的實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c3df-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="1c3df-106">它是從 Windows 10 Creators Update。</span><span class="sxs-lookup"><span data-stu-id="1c3df-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="1c3df-107">模擬器是類似[HoloLens 模擬器](using-the-hololens-emulator.md)，不過模擬器不會使用虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="1c3df-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="1c3df-108">在模擬器中執行的應用程式會執行 Windows 10 桌面的使用者工作階段，就像您使用的沈浸式耳機時它們執行的動作一樣。</span><span class="sxs-lookup"><span data-stu-id="1c3df-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="1c3df-109">通常會在沉浸式耳機感應器所讀取的人力和環境輸入是改為模擬使用您的鍵盤、 滑鼠或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="1c3df-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="1c3df-110">應用程式不需要修改，才能在模擬器中執行，而且不知道它們不在沉浸式耳機上執行。</span><span class="sxs-lookup"><span data-stu-id="1c3df-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="1c3df-111">啟用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="1c3df-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="1c3df-112">**啟用開發人員模式**從 設定-> 更新與安全性-> 適用於開發人員</span><span class="sxs-lookup"><span data-stu-id="1c3df-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="1c3df-113">啟動**混合實境入口網站**從桌面</span><span class="sxs-lookup"><span data-stu-id="1c3df-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="1c3df-114">如果這是您第一次啟動入口網站，您必須經歷了安裝經驗</span><span class="sxs-lookup"><span data-stu-id="1c3df-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="1c3df-115">按一下 **開始**</span><span class="sxs-lookup"><span data-stu-id="1c3df-115">Click **Get started**</span></span>
   2. <span data-ttu-id="1c3df-116">按一下 **我同意**接受授權合約</span><span class="sxs-lookup"><span data-stu-id="1c3df-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="1c3df-117">按一下 **設定為模擬 （適用於開發人員）** 繼續執行安裝程式沒有實體裝置</span><span class="sxs-lookup"><span data-stu-id="1c3df-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="1c3df-118">按一下 **設定**來確認您的選擇</span><span class="sxs-lookup"><span data-stu-id="1c3df-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="1c3df-119">按一下 **適用於開發人員**混合實境入口網站左邊的按鈕</span><span class="sxs-lookup"><span data-stu-id="1c3df-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="1c3df-120">若要開啟模擬切換開關**上**</span><span class="sxs-lookup"><span data-stu-id="1c3df-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="1c3df-121">啟用模擬會安裝並啟用預設左模擬的 DOF 6 控制站。</span><span class="sxs-lookup"><span data-stu-id="1c3df-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="1c3df-122">之前的 Windows 10 2019 年更新，安裝模擬的 6 DOF 控制站需要系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="1c3df-122">Prior to the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="1c3df-123">如果出現的話，您必須接受 [使用者帳戶控制] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1c3df-123">You must accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="1c3df-124">您現在應該執行的模擬 ！</span><span class="sxs-lookup"><span data-stu-id="1c3df-124">You should now be running with simulation!</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="1c3df-125">將應用程式部署至混合實境模擬器</span><span class="sxs-lookup"><span data-stu-id="1c3df-125">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="1c3df-126">因為模擬器在本機電腦而不需要虛擬機器上執行，您可以只部署您的通用 Windows 應用程式**本機電腦**偵錯時。</span><span class="sxs-lookup"><span data-stu-id="1c3df-126">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="1c3df-127">基本的模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="1c3df-127">Basic simulator input</span></span>

<span data-ttu-id="1c3df-128">控制模擬器是非常類似於許多常見的 3D 視訊遊戲並[HoloLens 模擬器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="1c3df-128">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="1c3df-129">有可用的輸入的選項使用鍵盤、 滑鼠或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="1c3df-129">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="1c3df-130">您可以將導向穿著沈浸式耳機的模擬使用者動作控制模擬器。</span><span class="sxs-lookup"><span data-stu-id="1c3df-130">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="1c3df-131">您的動作移動模擬的使用者，而且會導致回應的沉浸式耳機上的應用程式的互動。</span><span class="sxs-lookup"><span data-stu-id="1c3df-131">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="1c3df-132">**上一步，向前保留，並以滑鼠右鍵**-使用 W、 A、 S 和 D 鍵盤或 Xbox 控制器上的左搖桿上的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1c3df-132">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="1c3df-133">**查閱，向下、 左、 並以滑鼠右鍵**-按一下並拖曳滑鼠，使用方向鍵在鍵盤或 Xbox 控制器上正確的隨身碟上。</span><span class="sxs-lookup"><span data-stu-id="1c3df-133">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="1c3df-134">**控制站上按下的動作按鈕**-按一下滑鼠右鍵，在鍵盤上按 Enter 鍵或使用 Xbox 控制器上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="1c3df-134">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="1c3df-135">**首頁控制器上的按下按鈕**-在鍵盤上按 Windows 鍵或 F2 鍵或按下 B 上的 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="1c3df-135">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="1c3df-136">**控制站移動捲動**-按住 Alt 鍵，請按住滑鼠按鈕，並拖曳滑鼠，增加 / 減少，或 Xbox 控制器中按住正確的觸發程序和一個按鈕並向上和向下移動右隨身碟。</span><span class="sxs-lookup"><span data-stu-id="1c3df-136">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="1c3df-137">追蹤控制站</span><span class="sxs-lookup"><span data-stu-id="1c3df-137">Tracked controllers</span></span>

<span data-ttu-id="1c3df-138">混合實境模擬器可以模擬最多兩個掌上型追蹤的動作控制站。</span><span class="sxs-lookup"><span data-stu-id="1c3df-138">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="1c3df-139">讓他們在混合實境入口網站中使用的切換開關。</span><span class="sxs-lookup"><span data-stu-id="1c3df-139">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="1c3df-140">每個模擬的控制站有：</span><span class="sxs-lookup"><span data-stu-id="1c3df-140">Each simulated controller has:</span></span>
* <span data-ttu-id="1c3df-141">位置和空間中的方向</span><span class="sxs-lookup"><span data-stu-id="1c3df-141">Position and orientation in space</span></span>
* <span data-ttu-id="1c3df-142">首頁按鈕</span><span class="sxs-lookup"><span data-stu-id="1c3df-142">Home button</span></span>
* <span data-ttu-id="1c3df-143">功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="1c3df-143">Menu button</span></span>
* <span data-ttu-id="1c3df-144">調整底框的按鈕</span><span class="sxs-lookup"><span data-stu-id="1c3df-144">Grip button</span></span>
* <span data-ttu-id="1c3df-145">觸控板</span><span class="sxs-lookup"><span data-stu-id="1c3df-145">Touchpad</span></span>
* <span data-ttu-id="1c3df-146">搖桿</span><span class="sxs-lookup"><span data-stu-id="1c3df-146">Thumbstick</span></span>
* <span data-ttu-id="1c3df-147">電池電量</span><span class="sxs-lookup"><span data-stu-id="1c3df-147">Battery level</span></span>

## <a name="see-also"></a><span data-ttu-id="1c3df-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c3df-148">See also</span></span>
* [<span data-ttu-id="1c3df-149">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="1c3df-149">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="1c3df-150">進階混合的實境模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="1c3df-150">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="1c3df-151">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="1c3df-151">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="1c3df-152">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="1c3df-152">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
