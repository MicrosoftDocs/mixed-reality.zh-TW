---
title: Azure 語音服務教學課程-3。 新增 Azure 認知服務語音翻譯元件
description: 在此課程中，您將瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143232"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. 新增 Azure 認知服務語音翻譯元件

在本教學課程中，您將瞭解專案的 Azure 認知服務語音翻譯元件，以及如何轉譯成三種不同的語言。

## <a name="instructions"></a>指示

1. 選取階層中的 [Lunarcom_Base] 物件，然後按一下 [偵測器] 面板中的 [新增元件]。 搜尋並選取 [Lunarcom 轉譯辨識器]。

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    停用離線模式模擬器。

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >在繼續之前，請先確定已停用離線模式模擬器（如上圖所示），再測試語音 SDK 轉譯程式。 您必須連線到網際網路，才能轉譯。

2. 按一下 Lunarcom 轉譯辨識器中的下拉式選單，然後選取您想要翻譯成的語言。

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. 執行應用程式並按一下附屬按鈕來測試翻譯工具，然後開始說話。 再按一次 [衛星] 按鈕，以停止辨識。 以下是場景外觀的範例。 請隨意變更 [目的語言] 下拉式清單下的語言（請參閱上方的影像），以探索其他語言的翻譯。

    以下是場景看起來應該像這樣的範例：

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>恭喜！

您的專案現在可以成功地將您所說的單字轉譯成數種不同的語言。 歡迎您試著使用這些語言，並測試翻譯的正確性。

[下一個教學課程： 4. 設定意圖和自然語言理解](mrlearning-speechSDK-ch4.md)
