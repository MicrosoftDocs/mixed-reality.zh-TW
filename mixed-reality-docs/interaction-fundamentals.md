---
title: 多樣式互動概觀
description: 多樣式互動的概觀
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: 混合實境，視線、 視線目標，就會有互動，設計
ms.openlocfilehash: 8c578d9a67f6809df69fb132f4c46a381726596e
ms.sourcegitcommit: d6d96d552ec10cd7e6502fbbc1905432e2878325
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524343"
---
# <a name="introducing-instinctual-interactions"></a>簡介 instinctual 互動
簡單、 instinctual 互動的原理是這整個 Microsoft 混合實境平台。  我們已採取三個步驟，以確保應用程式設計師和開發人員可以提供簡單且直覺式的互動，供其客戶。 

首先，我們已確認我們令人讚嘆的感應器和輸入的技術，包括手動追蹤、 追蹤、 眼睛和自然語言，結合無縫式的多樣式互動模型。  根據我們的研究，設計和開發 multimodally-而不根據單一輸入--建立 instinctual 體驗的關鍵。

其次，我們了解許多開發人員目標多個裝置，不論其是指 HoloLens 2 和 HoloLens （第 1 代） 或 HoloLens 和 VR。  因此，我們已設計我們的互動模型，才能在裝置上 （即使輸入的技術而異，每個裝置上）。  比方說，Windows 沈浸式耳機 6DoF 控制站上的遠端互動和 HoloLens 2 這兩個最互動使用的相同的提供和模式，輕鬆跨裝置應用程式。 不只是此方便開發人員和設計工具，但它自然給使用者。 

最後，雖然我們辨識有數千個更有效、 更吸引人，並在 MR 神奇互動，但我們發現該刻意採用的互動模型中端對端應用程式是確保使用者是否順利的最佳辦法，有絕佳的體驗。  為此，我們包含了這個互動的指導方針中的三個項目：
* 我們已建立結構周圍的三個主要的互動模型的元件和模式所需的每本指導方針
* 我們包含了其他優點，我們的平台提供的補充指引
* 我們包含了指引，幫助您選取適當的互動模型，您的案例


## <a name="three-multimodal-interaction-models"></a>三個多模式的互動模型
根據我們的研究和與客戶合作，日期的工作，我們發現三個主要的互動模型符合大部分的混合實境體驗。

在許多方面的互動模型是使用者的心智模型完成其流程。  每個這些互動模型最適合客戶需求的一組，每一個是便利又強大，而且可用於自己的權限。 

下列圖表是簡化的概觀。  使用每個互動模型的詳細的資訊會在下方的頁面，即可使用影像和程式碼範例連結。  

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
        <td><strong>範例案例</strong></td>
        <td><strong>調整</strong></td>
        <td><strong>硬體</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">指針和工具</a></td>
        <td>3D 空間的體驗<br>例如空間配置和設計、 操作的內容或模擬</td>
        <td>適用於新的使用者<br>學習曲線很低<br>奠基於對的簡單 visual 提供<br>手動追蹤和 6DoF 控制站之間的一致 UX<br>如果結合語音、 眼睛追蹤或前端的視線很棒</td>
        <td>HoloLens 2<br>Windows 包含 6DoF 控制站的沈浸式</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">免持式</a></td>
        <td>其中使用者的手佔用例如作業學習，維護的情境體驗</td>
        <td>有些學習所需<br>如果無法使用指針<br>與語音和自然語言的配對</td>
        <td>HoloLens 2<br>HoloLens （第 1 代）<br> 沈浸式 Windows</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">頭部目光和行動</a></td>
        <td>點選體驗例如 3D 簡報、 示範</td>
        <td>需要訓練 HMDs 上但不是能在行動裝置<br>最適合可存取的控制站<br>最適合 HoloLens （第 1 代）</td>
        <td>HoloLens 2<br>HoloLens （第 1 代）<br> 沈浸式 Windows<br> Mobile AR</td>
    </tr>
</table>
<br>

請確定沒有任何間距或您的體驗的互動中出現漏洞的最佳方式是遵循從開始到結束的單一模型的指引。 

為了加快速度設計和開發，我們包含了詳細的資訊和連結的影像和程式碼範例在我們的每個模型的涵蓋範圍內。

但首先，下列各節會逐步選取及實作其中一個互動模型。  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>結束此頁面時，您會先了解我們的指引：
 
* 選擇您的客戶互動模型
* 使用互動模型的指導方針
* 互動模型之間轉換
* 設計後續步驟

## <a name="choosing-an-interaction-model-for-your-customer"></a>選擇您的客戶互動模型

最有可能，開發人員與創作者已經有一些概念記住它們想要為其使用者的互動體驗的種類。
若要鼓勵客戶為主的方法，來設計，我們建議您遵循下列指導方針來選取適合您的客戶互動模型。

### <a name="why-follow-this-guidance"></a>為什麼要遵循本指導方針？

* 我們的互動模型測試的目標和實體和認知投入時間、 intuitiveness，等 learnability 主觀的準則。 
* 因為互動不同，提供視覺與音訊及物件行為可能也不同之間的互動模型。  
* 結合多個互動模型的組件建立競爭提供，例如同時手動光線和視線資料指標，會拖垮而造成使用者混淆的風險。

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
        <td>視線游標會變更透過某些物件時的狀態。</td>
        <td>我看到/聽到視覺和聽覺確認，當我採取的動作。</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">免持聽筒 （視線和詳述）</a></td>
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
 
1.  Q:我的使用者要觸控全像投影和執行精確度全像攝影版操作嗎？
答：如果是的話，請查看雙手及工具互動模型的精確度為目標和操作與實際操作或動作控制站。
 
2.  Q:我的使用者需要保留其免費的實際工作的實際操作嗎？
答：如果是的話，看看免持聽筒互動模型，以提供絕佳免持聽筒經驗，透過視線和語音為基礎的互動。
 
3.  Q:我的使用者擁有以了解我的混合的實境應用程式互動的時間或者它們需要與最低的學習曲線的互動可能？
答：只要使用者就能夠使用其實際操作的互動，我們會建議最低的學習曲線和最直覺的互動，雙手及工具的模型。
 
4.  Q:我的使用者是否指向和操作使用動作控制站？
答：雙手及工具的模型包含移動控制站更優質的體驗的所有指引。
 
5.  Q:我的使用者使用的協助工具控制站或通用的藍牙控制器，例如 clicker 嗎？
答：我們建議所有的非追蹤控制站的 Head 視線和認可模型。  它設計成可讓使用者周遊使用簡單的 「 目標和認可 」 技師的整個體驗。 
 
6.  Q:我的使用者只介紹體驗 「 按一下 」 （例如在 3d 類似投影片的環境中），相對於瀏覽密集的 UI 控制項的版面配置嗎？
答：如果使用者不需要控制 UI 的很多，Head 視線和認可會提供準備的選項，使用者就不必擔心如何為目標。 
 
7.  Q:我的使用者使用這兩個 HoloLens （第 1 代） 和 HoloLens 2 / Windows 沉浸式 （VR 耳機） 的 a:因為 Head 視線和認可 HoloLens 互動模型 （第 1 代），我們建議最好讓支援 HoloLens 的建立者 （第 1 代） 使用 Head 視線和認可的任何功能或使用者可能會遇到 HoloLens 的模式 （第 1 代） 耳機。  請參閱下一節上*轉換互動模型*如需詳細資訊，讓多個 HoloLens 層代的絕佳體驗。
 
8.  Q:功能的相關使用者是一般行動裝置 （涵蓋大型空間或空間之間移動），與使用者要在單一的空間中運作？  
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
* [直接操作](direct-manipulation.md)
* [指向和行動](point-and-commit.md)
* [目光目標](gaze-targeting.md)
* [筆勢](gestures.md)
* [語音設計](voice-design.md)
* [運動控制器](motion-controllers.md)
* [空間音效設計](spatial-sound-design.md)
* [空間對應設計](spatial-mapping-design.md)
* [舒適度](comfort.md)
