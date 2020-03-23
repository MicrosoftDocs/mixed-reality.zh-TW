---
title: Azure 語音服務教學課程 - 2。 新增本機語音轉換文字翻譯離線模式
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031606"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a>2.使用語音辨識來執行命令

在本教學課程中，您將新增使用 Azure 語音辨識執行命令的功能，這可讓您根據所定義的單字或片語進行一些動作。

## <a name="objectives"></a>目標

* 了解如何使用 Azure 語音辨識來執行命令

## <a name="instructions"></a>指示

在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Lunarcom Wake Word Recognizer (指令碼)** 元件新增至 Lunarcom 物件，並進行以下設定：

* 在 [喚醒字詞]  欄位中，入適當的片語，例如「啟動終端機 (Activate terminal)」  。
* 在 [關閉字詞]  欄位中，輸入適當的片語，例如「關閉終端機 (Dismiss terminal)」  。

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Lunarcom Wake Word Recognizer (指令碼) 元件不是 MRTK 的一部分。 這是本教學課程資產隨附的元件。

如果您現在進入遊戲模式，如先前的教學課程所示，預設會啟用終端機面板，但您現在可以藉由說出關閉字詞：**關閉終端機**，來將其停用：

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

然後藉由說出喚醒字詞：**啟動終端機**，來再次將其啟動：

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> 應用程式必須連線到 Azure，因此請確定您的電腦/裝置已連線到網際網路。

> [!TIP]
> 如果您預期無法經常連線到 Azure，您也可以遵循[啟用語音命令](mrlearning-base-ch5.md#enabling-voice-commands)指示，使用 MRTK 來實作語音命令。

## <a name="congratulations"></a>恭喜！

您已實作由 Azure 提供技術支援的語音命令。 在您的裝置上執行應用程式，以確保功能可正常運作。

在下一個教學課程中，您將了解如何使用 Azure 語音翻譯來轉譯語音。

[下一個教學課程：3.新增 Azure 認知服務語音翻譯元件](mrlearning-speechSDK-ch3.md)
