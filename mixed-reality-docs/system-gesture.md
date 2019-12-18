---
title: 系統手勢
description: 系統手勢以呼叫 [開始] 功能表。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現實、手勢、互動、設計
ms.openlocfilehash: 9cfee1104cb9b8135dae51bea73850062fadd25c
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181998"
---
# <a name="system-gesture"></a><span data-ttu-id="c2987-104">系統手勢</span><span class="sxs-lookup"><span data-stu-id="c2987-104">System gesture</span></span>

<span data-ttu-id="c2987-105">系統手勢是用來叫用 [開始] 功能表的手勢。</span><span class="sxs-lookup"><span data-stu-id="c2987-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="c2987-106">這相當於按下鍵盤上的 Windows 鍵、Xbox 控制器上的 Xbox 按鈕，或沉浸式耳機運動控制器上的 Windows 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c2987-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="c2987-107">請務必瞭解在每個混合現實裝置上保留給系統的筆勢，以避免在設計互動時發生衝突。</span><span class="sxs-lookup"><span data-stu-id="c2987-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="c2987-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c2987-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c2987-109"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="c2987-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c2987-110"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c2987-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c2987-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c2987-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="c2987-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="c2987-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c2987-113">盛開</span><span class="sxs-lookup"><span data-stu-id="c2987-113">Bloom</span></span></td>
        <td><span data-ttu-id="c2987-114">✔️</span><span class="sxs-lookup"><span data-stu-id="c2987-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="c2987-115">手腕按鈕</span><span class="sxs-lookup"><span data-stu-id="c2987-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c2987-116">✔️</span><span class="sxs-lookup"><span data-stu-id="c2987-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="c2987-117">眼睛和上長的捏</span><span class="sxs-lookup"><span data-stu-id="c2987-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c2987-118">✔️</span><span class="sxs-lookup"><span data-stu-id="c2987-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="c2987-119">盛開</span><span class="sxs-lookup"><span data-stu-id="c2987-119">Bloom</span></span>
<span data-ttu-id="c2987-120">為了在 HoloLens （第1代）中顯示 [開始] 功能表，我們設計了 "Bloom"，這是模擬花卉櫻花的符號手勢。</span><span class="sxs-lookup"><span data-stu-id="c2987-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="c2987-121">它是 surefooted 互動、易於執行和快速召回的獨特之處。</span><span class="sxs-lookup"><span data-stu-id="c2987-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="c2987-122">若要在 HoloLens （第1代）上進行 bloom 手勢，請將您的手掌放在一起，並將您的手合在一起，然後藉由散佈手指來開手。</span><span class="sxs-lookup"><span data-stu-id="c2987-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="c2987-123">![Bloom 關閉](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="c2987-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="c2987-124">**步驟1：將您的手上緊密結合**</span><span class="sxs-lookup"><span data-stu-id="c2987-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2987-125">![Bloom 開啟](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="c2987-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="c2987-126">**步驟2：使用輕鬆散佈的 Palm**</span><span class="sxs-lookup"><span data-stu-id="c2987-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="c2987-127">開始手勢</span><span class="sxs-lookup"><span data-stu-id="c2987-127">Start gesture</span></span>
<span data-ttu-id="c2987-128">在 HoloLens 2 中，我們以虛擬手腕按鈕取代了 Bloom 手勢，讓您不需要額外的教學就能進行更本能的互動。</span><span class="sxs-lookup"><span data-stu-id="c2987-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="c2987-129">藉由向使用者顯示手腕上的按鈕，他們可以直覺地連接，並將其與其他人一起按。</span><span class="sxs-lookup"><span data-stu-id="c2987-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="c2987-130">![手腕按鈕就緒](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="c2987-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="c2987-131">**步驟1： Palm 以顯示手腕按鈕**</span><span class="sxs-lookup"><span data-stu-id="c2987-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2987-132">![手腕按鈕按](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="c2987-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="c2987-133">**步驟2：按 [手腕] 按鈕**</span><span class="sxs-lookup"><span data-stu-id="c2987-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a><span data-ttu-id="c2987-134">一次開始手勢</span><span class="sxs-lookup"><span data-stu-id="c2987-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2987-135">若要讓單向開始手勢正常執行：</span><span class="sxs-lookup"><span data-stu-id="c2987-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="c2987-136">您必須更新至2019年11月更新（組建18363.1039）或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c2987-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="c2987-137">您的眼睛必須在裝置上校正，讓眼追蹤能夠正確運作。</span><span class="sxs-lookup"><span data-stu-id="c2987-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="c2987-138">當您查看 [開始] 圖示時，如果看不到軌道點，則裝置上不會校正您的眼睛。</span><span class="sxs-lookup"><span data-stu-id="c2987-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="c2987-139">您也可以只使用一手勢來執行開始手勢。</span><span class="sxs-lookup"><span data-stu-id="c2987-139">You can also perform the Start gesture with only one hand.</span></span> <span data-ttu-id="c2987-140">若要這麼做，請將您的 palm 放在您的手中，並查看您內部手腕上的**開始圖示**。</span><span class="sxs-lookup"><span data-stu-id="c2987-140">To do this, hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="c2987-141">將**您的眼放在圖示上，同時**將您的 thumb 和索引手指放在一起。</span><span class="sxs-lookup"><span data-stu-id="c2987-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="c2987-142">![手腕按鈕就緒](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="c2987-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="c2987-143">**步驟1： Palm 以顯示手腕按鈕**</span><span class="sxs-lookup"><span data-stu-id="c2987-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2987-144">![手腕按鈕縮小](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="c2987-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="c2987-145">**步驟2：留意按鈕然後縮小**</span><span class="sxs-lookup"><span data-stu-id="c2987-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="c2987-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="c2987-146">See also</span></span>

* [<span data-ttu-id="c2987-147">本能互動</span><span class="sxs-lookup"><span data-stu-id="c2987-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="c2987-148">眼睛目光</span><span class="sxs-lookup"><span data-stu-id="c2987-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="c2987-149">語音輸入</span><span class="sxs-lookup"><span data-stu-id="c2987-149">Voice input</span></span>](voice-input.md)
