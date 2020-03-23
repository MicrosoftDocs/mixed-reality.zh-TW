---
title: Azure 語音服務教學課程 - 3。 新增 Azure 認知服務語音翻譯元件
description: 在此課程中，您將了解如何在混合實境應用程式中實作 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d8e73e24f0522ff71b95ea1886d59893216b0597
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028323"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3.新增 Azure 認知服務語音翻譯元件

在本教學課程中，您會將語音翻譯新增至您的專案，以讓您將語音翻譯及轉譯成三種不同語言。

## <a name="objectives"></a>目標

* 了解如何整合 Azure 語音翻譯

## <a name="instructions"></a>指示

在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Lunarcom Translation Recognizer (指令碼)** 元件新增至 Lunarcom 物件，並進行以下設定：

* 將 [目標語言]  變更為您選擇的語言，例如：德文 

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> Lunarcom Translation Recognizer (指令碼) 元件不是 MRTK 的一部分。 這是本教學課程資產隨附的元件。

如果您現在進入遊戲模式，您可以先按下衛星按鈕來測試語音翻譯。 接下來，假設您的電腦有麥克風，當您說到某個項目時，您的語音會翻譯成您選擇的語言並在終端機面板上進行轉譯：

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> 應用程式必須連線到 Azure，因此請確定您的電腦/裝置已連線到網際網路。

## <a name="congratulations"></a>恭喜！

您的專案現在可以成功地將您所說的字詞轉譯成數種不同的語言。 在您的裝置上執行應用程式，以確保功能可正常運作。

[下一個教學課程：4.設定意圖和自然語言理解](mrlearning-speechSDK-ch4.md)
