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
# <a name="system-gesture"></a>系統手勢

系統手勢是用來叫用 [開始] 功能表的手勢。 這相當於按下鍵盤上的 Windows 鍵、Xbox 控制器上的 Xbox 按鈕，或沉浸式耳機運動控制器上的 Windows 按鈕。 請務必瞭解在每個混合現實裝置上保留給系統的筆勢，以避免在設計互動時發生衝突。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>盛開</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>手腕按鈕</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>眼睛和上長的捏</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>盛開
為了在 HoloLens （第1代）中顯示 [開始] 功能表，我們設計了 "Bloom"，這是模擬花卉櫻花的符號手勢。 它是 surefooted 互動、易於執行和快速召回的獨特之處。 若要在 HoloLens （第1代）上進行 bloom 手勢，請將您的手掌放在一起，並將您的手合在一起，然後藉由散佈手指來開手。

:::row:::
    :::column:::
        ![Bloom 關閉](images/bloom-close.png)<br>
        **步驟1：將您的手上緊密結合**<br>
    :::column-end:::
    :::column:::
        ![Bloom 開啟](images/bloom-open.png)<br>
        **步驟2：使用輕鬆散佈的 Palm**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>開始手勢
在 HoloLens 2 中，我們以虛擬手腕按鈕取代了 Bloom 手勢，讓您不需要額外的教學就能進行更本能的互動。 藉由向使用者顯示手腕上的按鈕，他們可以直覺地連接，並將其與其他人一起按。

:::row:::
    :::column:::
        ![手腕按鈕就緒](images/wrist-button-ready.png)<br>
        **步驟1： Palm 以顯示手腕按鈕**<br>
    :::column-end:::
    :::column:::
        ![手腕按鈕按](images/wrist-button-press.png)<br>
        **步驟2：按 [手腕] 按鈕**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a>一次開始手勢

> [!IMPORTANT]
> 若要讓單向開始手勢正常執行：
>
> 1. 您必須更新至2019年11月更新（組建18363.1039）或更新版本。
> 1. 您的眼睛必須在裝置上校正，讓眼追蹤能夠正確運作。 當您查看 [開始] 圖示時，如果看不到軌道點，則裝置上不會校正您的眼睛。

您也可以只使用一手勢來執行開始手勢。 若要這麼做，請將您的 palm 放在您的手中，並查看您內部手腕上的**開始圖示**。 將**您的眼放在圖示上，同時**將您的 thumb 和索引手指放在一起。<br>
:::row:::
    :::column:::
        ![手腕按鈕就緒](images/wrist-button-ready.png)<br>
        **步驟1： Palm 以顯示手腕按鈕**<br>
    :::column-end:::
    :::column:::
        ![手腕按鈕縮小](images/wrist-button-pinch.png)<br>
        **步驟2：留意按鈕然後縮小**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>請參閱

* [本能互動](interaction-fundamentals.md)
* [眼睛目光](eye-tracking.md)
* [語音輸入](voice-input.md)
