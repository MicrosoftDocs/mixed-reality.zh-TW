---
title: Azure 語音服務教學課程-2。 新增用於本機語音轉換文字翻譯的離線模式
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 5382a1cce38e8607042c21b8dd3157d1da2fa72e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437560"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2. 新增本機語音轉換文字翻譯的離線模式

在本教學課程中，我們將新增離線模式，讓您在無法連線到 Azure 服務時執行本機語音轉換文字翻譯。 我們也會*模擬*中斷連線的狀態。

## <a name="instructions"></a>指示

1. 選取階層中的 [Lunarcom_Base] 物件。
2. 按一下 [偵測器] 面板中的 [新增元件]。 搜尋並選取 [Lunarcom 離線識別]。

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. 按一下 LunarcomOfflineRecognizer 中的下拉式選單，然後選取 [已啟用]。 這會讓專案的行為與使用者不具有連接。 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. 按下 [在 Unity 編輯器中播放] 並加以測試。 按下場景左下角的麥克風並開始說話。 

> [!NOTE]
> 因為我們已離線，所以已停用喚醒 word 功能。 每次您想要在離線時辨識語音時，都必須實際按一下麥克風。 

以下是您的場景可能外觀的範例。

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>恭喜您

已啟用離線模式。 現在，當您離線時，您仍然可以使用語音 SDK 來處理您的專案！ 


[下一個教學課程： 3. 新增 Azure 認知服務語音翻譯元件](mrlearning-speechSDK-ch3.md)

