---
title: MR 學習 Speechsdk.quickstart 模組-語音辨識與轉譯
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 43a6f02eaf09fcf43775374fae4fbe2d0bc8c346
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68977982"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a>語音 SDK 學習模組-使用語音命令 Rocket 啟動器控制項

在這一課, 我們將使用 Azure 語音服務的意圖功能來瞭解語音的意圖。 我們會使用 [偵測到的語音] 意圖作為語音命令, 以控制 rocket 啟動器。 在此課程中, 我們將匯入 Rocket 啟動器資產, 而我們會將偵測到的意圖語音命令介面為預先定義的控制按鈕, 以控制 Rocket。 

## <a name="objectives"></a>目標

- 瞭解如何將語音意圖連接為語音命令。
- 瞭解如何使用語音意圖語音命令作為 rocket 控制輸入命令。

## <a name="instructions"></a>指示
1. 在本教學課程中, 我們將使用「BaseModule」資產, 將 rocket 啟動器與語音命令整合。 為此, 我們需要將資產匯入到專案中。 您可以使用此[連結](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2)來下載「Rocket 啟動器」資產。 

2. 若要匯入資產, 請移至資產-> 匯入套件-> 自訂套件-> 流覽至下載的檔案, 然後按一下 [匯入]。

![module4chapter5step1](images/module4chapter5step1.PNG)

3. 匯入「基本模組資產」資產之後, 流覽 [基底模組資產] 資料夾-> Prefabs-> 選取 [Rocket Launcher_Complete], 然後將它拖放到現有的場景階層中。

![module4chapter5step2](images/module4chapter5step2.PNG)

4. 現在, 我們需要將我們的「Rocket 啟動器」與我們在上一課[課程](mrlearning-speechSDK-ch4.md)中工作的LUIS 專案整合。 為此, 請展開階層中的 "Rocket Launcher_Complete" prefab, 並尋找 [LaunchRoundButton]、[ResetRoundButton] 和 [放置提示] 按鈕。

![module4chapter5step3](images/module4chapter5step3.PNG)

5. 選取 [LaunchRoundButton], 然後在 [偵測器] 面板中, 移至 [可互動], 然後在事件的 [OnClick ()] 底下, 拖放 [LunarModule] prefab。 然後, 選取 [函式] 下拉式選並選取 [LunarModule], 然後流覽至 "StartThruster ()" 函式並加以選取。

![module4chapter5step 3。0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. 選取 [ResetRoundButton], 然後在 [偵測器] 面板中, 移至 [可互動], 然後在事件的 [OnClick ()] 底下, 拖放 [LunarModule] prefab。 然後, 選取 [函式] 下拉式選並選取 [LunarModule], 然後流覽至 "resetModule ()" 函式並加以選取。

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. 選取 [放置提示], 然後在 [偵測器] 面板中, 移至 [可互動], 然後在事件的 [OnClick ()] 底下, 拖放 "LunarModule" prefab。 然後, 選取 [函式] 下拉式選並選取 [LunarModule], 然後流覽至 [TogglePlacementHints] 函式, 然後選取 [ToggleGameOBjects ()]。

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  接下來, 選取階層中的 [Lunarcom_Completed] prefab, 並流覽至 [Inspector] 中的 [Lunarcom 意圖辨識器] 腳本, 然後將 [LaunchRoundButton]、[ResetRoundButton] 和 [放置提示] 按鈕拖放到其各自的位置。

![module4chapter5step4](images/module4chapter5step4.PNG)

9. 按下 Unity 編輯器中的 [播放] 按鈕, 並按一下 [Rocket] 按鈕, 然後有些純粹是像是「推送 Rocket 啟動按鈕」、「顯示位置提示」、「按下 rest 按鈕」或任何其他與啟動、重設或提示 Rocket 啟動器的要求相關的片語。

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a>恭喜！

在本課程中, 我們已瞭解如何將 AI 驅動的語音命令連接到語音命令, 以作為輸入法。 現在, 我們的程式可以使用說話者意圖作為語音命令, 為 rocket 啟動器提供輸入。

