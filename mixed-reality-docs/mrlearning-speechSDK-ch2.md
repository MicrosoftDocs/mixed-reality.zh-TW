---
title: MR 學習 Speechsdk.quickstart 模組-語音辨識與轉譯
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: e8dc5da5a089079ba38a26969df6070af8bc6200
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460308"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a>2.  新增用於本機語音轉換文字翻譯的離線模式

在本教學課程中, 我們將新增離線模式, 讓您在無法連線到 Azure 服務時執行本機語音轉換文字翻譯。 我們也會*模擬*中斷連線的狀態。

1. 選取階層中的 [Lunarcom_Base] 物件, 然後按一下 [偵測器] 面板中的 [新增元件]。 搜尋並選取 [Lunarcom 離線識別]。

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. 按一下 LunarcomOfflineRecognizer 中的下拉式選單, 然後選取 [已啟用]。 這會讓專案的行為與使用者不具有連接。 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. 現在, 按下 [在 Unity 編輯器中播放] 並加以測試。 按下場景左下角的麥克風, 然後開始說話。 

> [!NOTE]
> 因為我們已離線, 所以已停用喚醒 word 功能。 當您每次想要在離線時辨識語音時, 都必須實際按一下麥克風。 

以下是您的場景可能外觀的範例。

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>恭喜！

已啟用離線模式。 現在, 當您離線時, 您仍然可以使用語音 SDK 來處理您的專案! 


[下一個教學課程:3.新增 Azure 認知服務語音翻譯元件](mrlearning-speechSDK-ch3.md)

