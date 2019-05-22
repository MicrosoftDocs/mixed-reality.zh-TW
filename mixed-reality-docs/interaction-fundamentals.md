---
title: 多樣式互動概觀
description: 多樣式互動的概觀
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境、 視線、 視線目標，就會有互動，設計、 hololens MMR，multimodal
ms.openlocfilehash: 9d0e639d7474c7e8728282acfa8d288cfeec7043
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974909"
---
# <a name="introducing-instinctual-interactions"></a>簡介 instinctual 互動

簡單、 instinctual 互動的原理是這整個 Microsoft 混合實境 (MMR) 平台上，從軟體的硬體。

這些 instinctual 互動會利用所有可用輸入的技術，包括無縫式的多樣式互動模型中的追蹤內到外、 手動追蹤、 追蹤、 眼睛和自然語言。 根據我們的研究，設計和開發 multimodals，而不是依據單一的輸入時而言至關重要 instinctive 的體驗。

所有裝置類型也自然對齊 Instinctual 互動模型。  比方說，遠互動的沈浸式耳機上自由 (DoF) 控制器 6 度和 HoloLens 2 上的遠端互動使用相同的提供、 模式和行為。  不只是此方便開發人員和設計工具，但它自然給使用者。


最後，雖然我們辨識有數千個更有效、 更吸引人，並在 MR 神奇互動，但我們發現該刻意採用的互動模型中端對端應用程式是確保使用者是否順利的最佳辦法，有絕佳的體驗。  為此，我們包含了這個互動的指導方針中的三個項目：
* 我們已建立結構周圍的三個主要的互動模型的元件和模式所需的每本指導方針
* 我們包含了其他優點，我們的平台提供的補充指引
* 我們包含了指引，幫助您選取適當的互動模型，您的案例

## <a name="multimodal-interaction-models"></a>多樣式的互動模型

根據我們的研究和與客戶合作，日期的工作，我們發現符合大部分的混合實境體驗的三種主要的互動模型。  

您可以將這些互動模型想像成心智模型中的使用者完成其流程。

每個這些互動模型是便利又強大，而且可用於其自己的權限，和所有適用於一組客戶的需求。 檢視圖表下方，而是針對案例、 範例和每個互動模型的優點。  

**型號** | **[指針和工具](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)** | **[免持聽筒](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)** | **[視線並認可](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**
|--------- | --------------| ------------| ---------|
**範例案例** | 3D 空間的體驗，例如空間版面配置與設計，內容操作或模擬 | 其中使用者的手都被佔用，例如工作學習，維護的情境體驗| 點選體驗，例如 3D 簡報、 示範
**調整** | 適用於新的使用者，結合的 wit 語音眼睛追蹤或前端的視線。 學習曲線很低。 手動追蹤和 6 DoF 控制器之間的一致 UX。 | 學習所需的部分。 如果實際操作是無法使用的組，與語音和自然語言 | 需要訓練 HMDs 上但不是能在行動裝置。 最適合可存取的控制器最適合 HoloLens （第 1 代） |
**硬體** | HoloLens 2 沈浸式耳機 | HoloLens 2 HoloLens （第 1 代） 沈浸式耳機 | HoloLens 2 沈浸式耳機 | HoloLens 2 HoloLens （第 1 代） 沈浸式耳機 Mobile AR |

以下圖例和從我們的 Unity MRTK 範例內容的連結以及頁面上，是順暢地一起使用所有可用的輸入，在每個互動模型的詳細的資訊。


## <a name="choose-an-interaction-model-for-your-customer"></a>選擇您的客戶互動模型


最有可能，開發人員與創作者也已經有一些概念記住它們想要將使用者的互動體驗的種類。
若要鼓勵客戶為主的方法，來設計，我們建議您遵循下列指導方針來選取適合您的客戶互動模型。

### <a name="why-follow-this-guidance"></a>為什麼要遵循本指導方針？

* 我們的互動模型測試的目標和實體和認知投入時間、 intuitiveness，等 learnability 主觀的準則。 
* 因為互動不同，提供視覺與音訊及物件行為可能也不同之間的互動模型。  
* 結合多個互動模型的組件建立競爭提供，例如同時手動光線和 head 視線資料指標，會拖垮而造成使用者混淆的風險。

以下是如何提供和行為最適合用於每個互動模型的一些範例。  我們通常會看到新的使用者為類似的問題，例如 「 如何知道系統運作，如何知道我可以做什麼，和如何知道是否瞭解我剛才那樣？ 」

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>型號</strong></td>
        <td><strong>如何知道它是否運作？</strong></td>
        <td><strong>如何知道我可以做什麼？</strong></td>
        <td><strong>如何得知我只是做什麼？</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">指針和工具</a></td>
        <td>我看到 mesh 手的形狀，我看到寫寫看功能可見性或手動 / 控制器光線。</td>
        <td>我看到 grabbable 的控制代碼或我的手附近時，會顯示週框方塊。</td>
        <td>我聽到可發出聲音的音調看動畫上擷取和釋放。</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">頭部目光和行動</a></td>
        <td>我看到我的檢視的中央資料指標。</td>
        <td>Head 視線游標會變更透過某些物件時的狀態。</td>
        <td>我看到/聽到視覺和聽覺確認，當我採取的動作。</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">免持聽筒 （Head 視線和詳述）</a></td>
        <td>我看到我的檢視的中央資料指標。</td>
        <td>我會探討可互動的物件時，我就會看到進度列指示器。</td>
        <td>我看到/聽到視覺和聽覺確認，當我採取的動作。</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">免持聽筒 （語音命令）</a></td>
        <td>我看到接聽的指標，並顯示系統聽過的標題。</td>
        <td>取得語音提示與提示。  我說 「 我可以說什麼？ 」 我看到的意見反應。</td>
        <td>我看到/聽到視覺和聽覺確認我所發出的命令，或取得去除混淆時所需的 UX。</a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a>以下是問題，我們發現說明小組選取互動模型：
 
1.  Q:我的使用者要觸控全像投影和執行精確度全像攝影版操作嗎？<br><br>
答：如果是的話，請查看雙手及工具互動模型的精確度為目標和操作與實際操作或動作控制站。
 
2.  Q:我的使用者需要保留其免費的實際工作的實際操作嗎？<br><br>
答：如果是的話，看看免持聽筒互動模型，以提供絕佳免持聽筒經驗，透過視線和語音為基礎的互動。
 
3.  Q:我的使用者擁有以了解我的混合的實境應用程式互動的時間或者它們需要與最低的學習曲線的互動可能？<br><br>
答：只要使用者就能夠使用其實際操作的互動，我們會建議最低的學習曲線和最直覺的互動，雙手及工具的模型。
 
4.  Q:我的使用者是否指向和操作使用動作控制站？<br><br>
答：雙手及工具的模型包含移動控制站更優質的體驗的所有指引。
 
5.  Q:我的使用者使用的協助工具控制站或通用的藍牙控制器，例如 clicker 嗎？<br><br>
答：我們建議所有的非追蹤控制站的 Head 視線和認可模型。  它設計成可讓使用者周遊使用簡單的 「 目標和認可 」 技師的整個體驗。 
 
6.  Q:我的使用者只介紹體驗 「 按一下 」 （例如在 3d 類似投影片的環境中），相對於瀏覽密集的 UI 控制項的版面配置嗎？<br><br>
答：如果使用者不需要控制 UI 的很多，Head 視線和認可會提供準備的選項，使用者就不必擔心如何為目標。 
 
7.  Q:我的使用者使用這兩個 HoloLens （第 1 代） 和 HoloLens 2 / Windows 沉浸式 （VR 耳機）<br><br>
答：因為 Head 視線和認可 HoloLens 互動模型 （第 1 代），我們建議最好讓支援 HoloLens 的建立者 （第 1 代） 使用 Head 視線和認可的任何功能或使用者可能會遇到 HoloLens 的模式 （第 1 代） 耳機。  請參閱下一節上*轉換互動模型*如需詳細資訊，讓多個 HoloLens 層代的絕佳體驗。
 
8.  Q:功能的相關使用者是一般行動裝置 （涵蓋大型空間或空間之間移動），與使用者要在單一的空間中運作？<br><br>
答：任何互動模型將適用於這些使用者。  

> [!NOTE]
> 特定應用程式的設計的詳細指引[即將推出](index.md#news-and-notes)。


## <a name="transition-interaction-models"></a>轉換互動模型
也有一些情況下，您的使用案例可能需要使用一個以上的互動模型。  比方說，您的應用程式 「 建立流程 」 會利用雙手及工具互動模型，但您想要的現場技術人員運用免持聽筒的模式。  

如果您的經驗並需要多種互動模型，我們發現許多終端使用者可能會遇到困難，從一種模型之間，尤其是不熟悉 MR 終端使用者的轉換。

> [!Note]
> 為了協助指南的設計人員和開發人員很難在 MR 的選擇，我們正努力使用多種互動模型的詳細指引。
 

## <a name="see-also"></a>另請參閱
* [頭部目光和行動](gaze-and-commit.md)
* [頭部目光和停駐](gaze-and-dwell.md)
* [手部直接操作](direct-manipulation.md)
* [手部指向和行動](point-and-commit.md)
* [筆勢](gestures.md)
* [語音命令](voice-design.md)
* [運動控制器](motion-controllers.md)
* [空間音效設計](spatial-sound-design.md)
* [空間對應設計](spatial-mapping-design.md)
* [舒適度](comfort.md)

