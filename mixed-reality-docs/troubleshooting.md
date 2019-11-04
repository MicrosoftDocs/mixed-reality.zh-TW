---
title: HoloLens 疑難排解
description: Microsoft HoloLens 的疑難排解步驟。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 問題、錯誤、疑難排解、修正、說明、支援、HoloLens
ms.openlocfilehash: 855bb0cafb0d3fba0d8d97c93d9415b51bcc2fb3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438278"
---
# <a name="hololens-troubleshooting"></a>HoloLens 疑難排解

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>我的 HoloLens 沒有回應或無法開機

如果您的 HoloLens 無法開機：
* 如果 [電源] 按鈕的 Led 不亮，或只有1個 LED 短暫閃爍，您可能需要向 HoloLens 收費。
* 當您按下電源按鈕但看不到顯示器上的任何專案時，如果 Led 亮起，請按住 [電源] 按鈕，直到電源按鈕關閉為止的所有5個 Led。

如果您的 HoloLens 已凍結或沒有回應：
* 關閉您的 HoloLens，方法是按下 [電源] 按鈕的所有5個 Led，直到電源按鈕變成 [關閉]，或如果 Led 沒有回應，則為10秒。 再按一次 [電源] 按鈕以開機。

如果這些步驟無法正常執行：
* 您可以嘗試[復原您的裝置](reset-or-recover-your-hololens.md)。

## <a name="holograms-dont-look-good-or-are-moving-around"></a>全息影像外觀不佳或四處移動。

如果您的全息影像不穩定、跳動或看起來不正確，請嘗試下列其中一個修正：
* 清除您的裝置面板，並確定沒有任何阻礙感應器。
* 請確定您的房間內有足夠的光線。
* 試著流覽並查看您的環境，讓 HoloLens 可以更完整地掃描。
* 試著執行校正應用程式。 它會校正您的 HoloLens 以最適合您的眼睛。 移至 [**設定**] > [**系統** > **公用程式**]。 在 [校正] 底下，選取 [**開啟校正**]。
* 如果您在執行校正應用程式之後仍然遇到問題，請使用感應器微調應用程式來調整您的裝置感應器。 移至 [**設定**] > [**系統** > **公用程式**]。 在 [感應器微調] 底下，選取 [**開啟感應器微調**]。

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens 不會回應我的手勢。

若要確保 HoloLens 能夠看到您的手勢，請將手放在手勢框架中，這會在您的任一邊延伸幾英尺。 當 HoloLens 可以看到您的手時，游標會從點變更為環形。 深入瞭解如何使用[手勢](gaze-and-commit.md#composite-gestures)。

如果您的環境太暗，HoloLens 可能看不到您的手，因此請確定有足夠的光線。

如果您的面板具有指紋或塗抹，請使用 HoloLens 隨附的 microfiber 清潔抹布來輕輕清理您的面板。

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens 不會回應我的語音命令。

如果 Cortana 沒有回應您的語音命令，請確定 Cortana 已開啟。 在 所有應用程式 清單中，選取 Cortana > 功能表 > 筆記本 > 設定 以進行變更。 若要深入瞭解您可以說的內容，請參閱使用您的語音來控制 HoloLens。

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>我無法放置全息影像或查看我先前放置的全息影像。

如果 HoloLens 無法對應或載入您的空間，它會進入有限的模式，而且您將無法放置全息影像或看到您所放置的全息影像。 您可以嘗試以下方法：
* 請確定您的環境中有足夠的光線，讓 HoloLens 能夠看到並對應空間。
* 請確定您已連線到 Wi-fi 網路。 如果您未連線到 Wi-fi，HoloLens 就無法識別並載入已知的空間。
* 如果您需要建立新的空間，請連接到 Wi-fi，然後重新開機 HoloLens。
* 若要查看正確的空間是否作用中，或要手動載入空間，請移至 [**設定**] [**系統** > **空間**] > 。
* 如果載入正確的空間，但您仍然遇到問題，則空間可能已損毀。 若要修正此問題，請選取空間，然後選取 [移除]。 一旦移除空間之後，HoloLens 就會開始對應您的環境，並建立新的空間。

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>我的 HoloLens 經常進入有限的模式，或顯示「追蹤遺失」的訊息。

如果您的裝置通常會顯示「受限模式」或「追蹤遺失」訊息，請嘗試我的全息影像中的建議[不佳，或正四處移動](#holograms-dont-look-good-or-are-moving-around)。

## <a name="my-hololens-cant-tell-what-space-im-in"></a>我的 HoloLens 無法分辨我的空間。

如果您的 HoloLens 無法自動識別並載入您所在的空間，請確定您已連接到 Wi-fi、房間內有足夠的光線，而且對等互連尚未進行任何重大變更。 您也可以手動載入空間，或前往 [**設定**] [ > ] [**系統** > **空間**] 來管理空間。

## <a name="im-getting-a-low-disk-space-error"></a>我收到「磁碟空間不足」錯誤。

您必須執行下列一或多項作業來釋放一些儲存空間：
* 刪除一些未使用的空間。 移至 [**設定**] > [**系統** > **空間**]，選取不再需要的空間，然後選取 [**移除**]。
* 移除您所放置的部分全息影像。
* 刪除相片應用程式中的某些圖片和影片。
* 從 HoloLens 卸載一些應用程式。 在 [所有應用程式] 清單中，按住您要卸載的應用程式，然後選取 [**卸載**]。

## <a name="my-hololens-cant-create-a-new-space"></a>我的 HoloLens 無法建立新的空間。

最有可能的問題是您的儲存空間不足。 請嘗試上面的其中一個[提示](#im-getting-a-low-disk-space-error)來釋放一些磁碟空間。
