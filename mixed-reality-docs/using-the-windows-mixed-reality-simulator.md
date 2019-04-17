---
title: 使用 Windows Mixed Reality 模擬器
description: Windows Mixed Reality 模擬器可讓您測試您的電腦，而不需要 Windows Mixed Reality 沈浸式耳機上的混合的實境應用程式。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows 混合現實情況下，模擬器測試
ms.openlocfilehash: 782cab85f163edd2afc4251210b7596c73dcc8b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596337"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="31d82-104">使用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="31d82-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="31d82-105">Windows Mixed Reality 模擬器可讓您測試您的電腦，而不需要 Windows Mixed Reality 沈浸式耳機上的混合的實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="31d82-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="31d82-106">它是從 Windows 10 Creators Update。</span><span class="sxs-lookup"><span data-stu-id="31d82-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="31d82-107">模擬器是類似[HoloLens 模擬器](using-the-hololens-emulator.md)，不過模擬器不會使用虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="31d82-107">The simulator is similar to the [HoloLens emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="31d82-108">在模擬器中執行的應用程式會執行 Windows 10 桌面的使用者工作階段，就像您使用的沈浸式耳機時它們執行的動作一樣。</span><span class="sxs-lookup"><span data-stu-id="31d82-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="31d82-109">通常會在沉浸式耳機感應器所讀取的人力和環境輸入是改為模擬使用您的鍵盤、 滑鼠或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="31d82-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="31d82-110">應用程式不需要修改，才能在模擬器中執行，而且不知道它們不在沉浸式耳機上執行。</span><span class="sxs-lookup"><span data-stu-id="31d82-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="31d82-111">啟用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="31d82-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="31d82-112">**啟用開發人員模式**從 設定-> 更新與安全性-> 適用於開發人員</span><span class="sxs-lookup"><span data-stu-id="31d82-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="31d82-113">啟動**混合實境入口網站**從桌面</span><span class="sxs-lookup"><span data-stu-id="31d82-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="31d82-114">如果這是您第一次啟動入口網站，您必須經歷了安裝經驗</span><span class="sxs-lookup"><span data-stu-id="31d82-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="31d82-115">按一下 **開始**</span><span class="sxs-lookup"><span data-stu-id="31d82-115">Click **Get started**</span></span>
   2. <span data-ttu-id="31d82-116">按一下 **我同意**接受授權合約</span><span class="sxs-lookup"><span data-stu-id="31d82-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="31d82-117">按一下 **設定為模擬 （適用於開發人員）** 繼續執行安裝程式沒有實體裝置</span><span class="sxs-lookup"><span data-stu-id="31d82-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="31d82-118">按一下 **設定**來確認您的選擇</span><span class="sxs-lookup"><span data-stu-id="31d82-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="31d82-119">按一下 **適用於開發人員**混合實境入口網站左邊的按鈕</span><span class="sxs-lookup"><span data-stu-id="31d82-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="31d82-120">若要開啟模擬切換開關**上**</span><span class="sxs-lookup"><span data-stu-id="31d82-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="31d82-121">這需要系統管理員權限，而且您必須接受使用者帳戶控制 對話方塊出現</span><span class="sxs-lookup"><span data-stu-id="31d82-121">This requires admin permissions and you must accept the User Account Control dialog that appears</span></span>

<span data-ttu-id="31d82-122">您現在應該執行的模擬 ！</span><span class="sxs-lookup"><span data-stu-id="31d82-122">You should now be running with simulation!</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="31d82-123">將應用程式部署至混合實境模擬器</span><span class="sxs-lookup"><span data-stu-id="31d82-123">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="31d82-124">因為模擬器在本機電腦而不需要虛擬機器上執行，您可以只部署您的通用 Windows 應用程式**本機電腦**偵錯時。</span><span class="sxs-lookup"><span data-stu-id="31d82-124">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="31d82-125">基本的模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="31d82-125">Basic simulator input</span></span>

<span data-ttu-id="31d82-126">控制模擬器是非常類似於許多常見的 3D 視訊遊戲並[HoloLens 模擬器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="31d82-126">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="31d82-127">有可用的輸入的選項使用鍵盤、 滑鼠或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="31d82-127">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="31d82-128">您可以將導向穿著沈浸式耳機的模擬使用者動作控制模擬器。</span><span class="sxs-lookup"><span data-stu-id="31d82-128">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="31d82-129">您的動作移動模擬的使用者，而且會導致回應的沉浸式耳機上的應用程式的互動。</span><span class="sxs-lookup"><span data-stu-id="31d82-129">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="31d82-130">**上一步，向前保留，並以滑鼠右鍵**-使用 W、 A、 S 和 D 鍵盤或 Xbox 控制器上的左搖桿上的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="31d82-130">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="31d82-131">**查閱，向下、 左、 並以滑鼠右鍵**-按一下並拖曳滑鼠，使用方向鍵在鍵盤或 Xbox 控制器上正確的隨身碟上。</span><span class="sxs-lookup"><span data-stu-id="31d82-131">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="31d82-132">**控制站上按下的動作按鈕**-按一下滑鼠右鍵，在鍵盤上按 Enter 鍵或使用 Xbox 控制器上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="31d82-132">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="31d82-133">**首頁控制器上的按下按鈕**-在鍵盤上按 Windows 鍵或 F2 鍵或按下 B 上的 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="31d82-133">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="31d82-134">**控制站移動捲動**-按住 Alt 鍵，請按住滑鼠按鈕，並拖曳滑鼠，增加 / 減少，或 Xbox 控制器中按住正確的觸發程序和一個按鈕並向上和向下移動右隨身碟。</span><span class="sxs-lookup"><span data-stu-id="31d82-134">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="31d82-135">追蹤控制站</span><span class="sxs-lookup"><span data-stu-id="31d82-135">Tracked controllers</span></span>

<span data-ttu-id="31d82-136">混合實境模擬器可以模擬最多兩個掌上型追蹤的動作控制站。</span><span class="sxs-lookup"><span data-stu-id="31d82-136">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="31d82-137">讓他們在混合實境入口網站中使用的切換開關。</span><span class="sxs-lookup"><span data-stu-id="31d82-137">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="31d82-138">每個模擬的控制站有：</span><span class="sxs-lookup"><span data-stu-id="31d82-138">Each simulated controller has:</span></span>
* <span data-ttu-id="31d82-139">在空間中的位置</span><span class="sxs-lookup"><span data-stu-id="31d82-139">Position in space</span></span>
* <span data-ttu-id="31d82-140">首頁按鈕</span><span class="sxs-lookup"><span data-stu-id="31d82-140">Home button</span></span>
* <span data-ttu-id="31d82-141">功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="31d82-141">Menu button</span></span>
* <span data-ttu-id="31d82-142">調整底框的按鈕</span><span class="sxs-lookup"><span data-stu-id="31d82-142">Grip button</span></span>
* <span data-ttu-id="31d82-143">觸控板</span><span class="sxs-lookup"><span data-stu-id="31d82-143">Touchpad</span></span>

## <a name="see-also"></a><span data-ttu-id="31d82-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31d82-144">See also</span></span>
* [<span data-ttu-id="31d82-145">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="31d82-145">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="31d82-146">進階混合的實境模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="31d82-146">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="31d82-147">在 Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="31d82-147">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="31d82-148">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="31d82-148">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
