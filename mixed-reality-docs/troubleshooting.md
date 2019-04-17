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
# <a name="hololens-troubleshooting"></a>HoloLens 進行疑難排解

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>我的 HoloLens 沒有回應，或將不會開機

如果您的 HoloLens 不開機：
* 如果不淺的 Led，由 [電源] 按鈕，或只有 1 會簡短地閃爍 LED，您可能需要向您 HoloLens 收取費用。
* 如果 Led 亮起時按下電源按鈕，但您無法看到任何項目在顯示器上，，保留 [電源] 按鈕，直到全部 5 份由 [電源] 按鈕的 Led 將關閉。

如果已凍結或沒有回應，則會變成您 HoloLens:
* 關閉您 HoloLens 藉由按下電源按鈕，直到全部 5 份由 [電源] 按鈕的 Led 本身，開啟或關閉 10 秒的時間如果 Led 沒有回應。 按下電源按鈕開機。

如果這些步驟沒有作用：
* 您可以嘗試[復原您的裝置](reset-or-recover-your-hololens.md)。

## <a name="holograms-dont-look-good-or-are-moving-around"></a>全像投影的效果不好或已移動。

如果您全像投影不穩定、 跳動，或是看起來不正確，請嘗試這些修正程式的其中一個：
* 清除裝置上面，並確定不會阻礙感應器。
* 請確定您的聊天室中沒有足夠的光線。
* 請嘗試四處跑，並查看鳥瞰因此 HoloLens 就能掃描它們更完整。
* 請嘗試執行校正應用程式。 它會校準適合眼睛您 HoloLens。 移至**設定** > **System** > **公用程式**。 在 [校正] 中，選取**開啟校正**。
* 如果您仍然無法執行校正應用程式之後，使用感應器調整應用程式來微調您的裝置感應器。 移至**設定** > **System** > **公用程式**。 在微調感應器，選取**開啟感應器調整**。

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens 我筆勢不會回應。

若要確定 HoloLens 可以看到您的筆勢，保留您的手在軌跡框架中，以擴充您的任一邊的英呎數。 當 HoloLens 可以看到您的手時，游標會變成從一個點的環形。 進一步了解如何[筆勢](gestures.md)。

如果您的環境是否太深，可能不會看到您的手，因此請確定沒有足夠的光線 HoloLens。

如果您上面有指紋或模糊，請使用清除隨附輕輕清除您上面 HoloLens 的清潔 microfiber。

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens 不會回應我語音命令。

如果 Cortana 沒有回應您的語音命令，請確定已開啟 Cortana。 在所有的應用程式清單中，選取 [Cortana >] 功能表 > Notebook > 來變更設定。 若要深入了解您可以說，請參閱使用語音來控制 HoloLens。

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>我無法將全像投影，或請參閱先前放置全像投影。

如果 HoloLens 無法對應，或載入您的空間，它會進入受限制的模式，並無法將全像投影，或請參閱您放入全像投影。 您可以嘗試以下方法：
* 請確定有足夠光您的環境中讓 HoloLens 可以看到，並將對應的空間。
* 請確定您已連接到 Wi-fi 網路。 如果您未連線至 Wi-fi，HoloLens 無法識別，並載入已知的空間。
* 如果您需要建立新的空間，連接到 Wi-fi，然後重新啟動您的 HoloLens。
* 若要查看正確的空間是否作用中，或手動載入的空間，請前往**設定** > **System** > **空間**。
* 如果在載入正確的空間，您仍遇到問題，空間可能已損毀。 若要修正此問題，選取的磁碟空間，然後選取 [移除]。 一旦移除空間時，會開始對應鳥瞰 HoloLens，並建立新的空間。

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>我 HoloLens 經常會進入 Limited 模式下，或顯示 「 追蹤遺失 」 訊息。

如果您的裝置通常會顯示 「 有限的模式 」 或 「 追蹤遺失 」 訊息，請嘗試從建議[My 全像投影的效果不好或已移動](#holograms-dont-look-good-or-are-moving-around)。

## <a name="my-hololens-cant-tell-what-space-im-in"></a>我的 HoloLens 無法分辨我所在的空間。

如果您的 HoloLens 無法自動識別並載入您的空間，請確定您已連線至 Wi-fi、 還有很多 light 中的空間，而且尚未恍神進行重大變更。 您也可以手動載入的空間，或管理您的空間，方法是前往**設定** > **System** > **空間**。

## <a name="im-getting-a-low-disk-space-error"></a>我收到 「 磁碟空間不足 」 錯誤。

您必須釋出一些儲存空間藉由一或多個項目：
* 刪除一些未使用的空格。 移至**設定** > **System** > **空間**，選取您不再需要，然後選取的空間**移除**.
* 請移除一些放入全像投影。
* 請刪除一些圖片和影片，相片應用程式中。
* 解除安裝某些應用程式，以從您的 HoloLens。 在所有的應用程式清單中，按住您要解除安裝，然後選取 應用程式**解除安裝**。

## <a name="my-hololens-cant-create-a-new-space"></a>我的 HoloLens 無法建立新的空間。

最可能的問題是，您要儲存體空間不足。 請嘗試[上述的祕訣](#im-getting-a-low-disk-space-error)以釋放一些磁碟空間。
