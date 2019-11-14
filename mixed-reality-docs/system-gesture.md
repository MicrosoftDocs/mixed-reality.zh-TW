---
title: 系統手勢
description: 系統手勢以呼叫 [開始] 功能表。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現實、手勢、互動、設計
ms.openlocfilehash: 417811fff9d98e459dc0047d46ea065acfced4ef
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064234"
---
# <a name="system-gesture"></a><span data-ttu-id="92875-104">系統手勢</span><span class="sxs-lookup"><span data-stu-id="92875-104">System gesture</span></span>

<span data-ttu-id="92875-105">系統手勢是用來叫用 [開始] 功能表的手勢。</span><span class="sxs-lookup"><span data-stu-id="92875-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="92875-106">這相當於按下鍵盤上的 Windows 鍵、Xbox 控制器上的 Xbox 按鈕，或沉浸式耳機運動控制器上的 Windows 按鈕。</span><span class="sxs-lookup"><span data-stu-id="92875-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="92875-107">請務必瞭解在每個混合現實裝置上保留給系統的筆勢，以避免在設計互動時發生衝突。</span><span class="sxs-lookup"><span data-stu-id="92875-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="92875-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="92875-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="92875-109"><strong>特徵</strong></span><span class="sxs-lookup"><span data-stu-id="92875-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="92875-110"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="92875-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="92875-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="92875-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="92875-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="92875-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="92875-113">Bloom</span><span class="sxs-lookup"><span data-stu-id="92875-113">Bloom</span></span></td>
        <td><span data-ttu-id="92875-114">✔️</span><span class="sxs-lookup"><span data-stu-id="92875-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="92875-115">手腕按鈕</span><span class="sxs-lookup"><span data-stu-id="92875-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="92875-116">✔️</span><span class="sxs-lookup"><span data-stu-id="92875-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="92875-117">眼睛和上長的捏</span><span class="sxs-lookup"><span data-stu-id="92875-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="92875-118">✔️</span><span class="sxs-lookup"><span data-stu-id="92875-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="92875-119">Bloom</span><span class="sxs-lookup"><span data-stu-id="92875-119">Bloom</span></span>
<span data-ttu-id="92875-120">為了在 HoloLens （第1代）中顯示 [開始] 功能表，我們設計了 "Bloom"，這是模擬花卉櫻花的符號手勢。</span><span class="sxs-lookup"><span data-stu-id="92875-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="92875-121">它是 surefooted 互動、易於執行和快速召回的獨特之處。</span><span class="sxs-lookup"><span data-stu-id="92875-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="92875-122">若要在 HoloLens （第1代）上進行 bloom 手勢，請將您的手掌放在一起，並將您的手合在一起，然後藉由散佈手指來開手。</span><span class="sxs-lookup"><span data-stu-id="92875-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="92875-123">![Bloom 關閉](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="92875-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="92875-124">**步驟1：將您的手上緊密結合**</span><span class="sxs-lookup"><span data-stu-id="92875-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92875-125">![Bloom 開啟](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="92875-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="92875-126">**步驟2：使用輕鬆散佈的 Palm**</span><span class="sxs-lookup"><span data-stu-id="92875-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="92875-127">手腕按鈕</span><span class="sxs-lookup"><span data-stu-id="92875-127">Wrist button</span></span>
<span data-ttu-id="92875-128">在 HoloLens 2 中，我們以虛擬手腕按鈕取代了 Bloom 手勢，讓您不需要額外的教學就能進行更本能的互動。</span><span class="sxs-lookup"><span data-stu-id="92875-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="92875-129">藉由向使用者顯示手腕上的按鈕，他們可以直覺地連接，並將其與其他人一起按。</span><span class="sxs-lookup"><span data-stu-id="92875-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="92875-130">![手腕按鈕就緒](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="92875-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="92875-131">**步驟1： Palm 以顯示手腕按鈕**</span><span class="sxs-lookup"><span data-stu-id="92875-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92875-132">![手腕按鈕按](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="92875-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="92875-133">**步驟2：按 [手腕] 按鈕**</span><span class="sxs-lookup"><span data-stu-id="92875-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="92875-134">眼睛與托上</span><span class="sxs-lookup"><span data-stu-id="92875-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="92875-135">我們也在 HoloLens 2 中設計了一種可輕鬆存取的解決方案。</span><span class="sxs-lookup"><span data-stu-id="92875-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="92875-136">此手勢會要求使用者眼一下手腕按鈕，然後使用相同的手勢，使用其拇指和食指來執行 palm 的縮小。</span><span class="sxs-lookup"><span data-stu-id="92875-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="92875-137">![手腕按鈕就緒](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="92875-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="92875-138">**步驟1： Palm 以顯示手腕按鈕**</span><span class="sxs-lookup"><span data-stu-id="92875-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92875-139">![手腕按鈕縮小](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="92875-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="92875-140">**步驟2：留意按鈕然後縮小**</span><span class="sxs-lookup"><span data-stu-id="92875-140">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="92875-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="92875-141">See also</span></span>

* [<span data-ttu-id="92875-142">本能互動</span><span class="sxs-lookup"><span data-stu-id="92875-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="92875-143">眼睛目光</span><span class="sxs-lookup"><span data-stu-id="92875-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="92875-144">語音輸入</span><span class="sxs-lookup"><span data-stu-id="92875-144">Voice input</span></span>](voice-input.md)
