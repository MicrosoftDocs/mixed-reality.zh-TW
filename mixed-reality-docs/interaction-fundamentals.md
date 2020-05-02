---
title: 本能互動
description: 瞭解貫穿整個混合實境平台的簡單、直覺式互動原理。
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 注視, 注視定向, 互動, 設計, hololens, MMR, 多樣式
ms.openlocfilehash: 6b54d6e844c1b501a0835fc3a48deb4932ba551d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "74539724"
---
# <a name="introducing-instinctual-interactions"></a>本能互動簡介

![遠距手部操作](images/04_InteractionFundamentals.png)

簡單、直覺式互動的原理貫穿整個混合實境 (MR) 平台。 我們採取了三個步驟，以確保應用程式設計人員和開發人員可為其客戶提供簡單且直覺式的互動。 

首先，我們確定我們令人讚嘆的感應器和輸入技術 (包括手部追蹤、眼球追蹤和自然語言) 結合成完美的多樣式互動模型。  
根據我們的研究，多樣式架構內的設計和開發 (而不是根據個別輸入) 是創造直覺式體驗的關鍵。

其次，我們了解許多開發人員都以多個 HoloLens 裝置為目標，例如 HoloLens 2 和 HoloLens (第 1 代) 或 HoloLens 和 VR。  
因此，我們將互動模型設計為可跨裝置運作，即使每個裝置上的輸入技術有所不同。  
例如，在採用 6DoF 控制器的 Windows 沉浸式頭戴裝置上的遠距互動以及在 HoloLens 2 上的遠距互動均使用相同的能供性和模式，因此可輕易地進行跨裝置應用程式開發，並提供自然的使用者互動體驗。 

我們承認 MR 中有數千種有效、吸引人和神奇的可能互動，但我們也發現在應用程式中刻意運用端對端的單一互動模型，是確保使用者順利擁有絕佳體驗的最佳方法。 為此，我們在此互動指引中納入了三件事：
* 特定指引，以三個主要互動模型以及每個模型所需的元件和模式為主。
* 補充指引，說明我們的平台具備的其他優勢。
* 一般指引，可針對您的開發案例協助您選取適當的互動模型。

## <a name="multimodal-interaction-models"></a>多樣式互動模型

根據我們的研究以及客戶的意見反應，我們發現有三個主要互動模型適合大部分的混合實境體驗。 在許多方面，互動模型是使用者如何完成流程的心智模型。 上述每種互動模型都已針對一套客戶需求進行最佳化，正確使用時每種都很方便、強大、實用。 

下圖是簡化的概觀。 在底下的頁面中，使用每個互動模型的詳細資訊都有連結，其中包含影像和程式碼範例。 

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
        <td><strong>適合</strong></td>
        <td><strong>硬體</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">手部和運動控制器</a></td>
        <td>3D 空間體驗，例如空間版面配置與設計、內容操作或模擬。</td>
        <td>很適用於新使用者，可搭配語音、眼球追蹤或頭部注視使用。 學習曲線很低。 手部追蹤和 6DoF 控制器之間的一致 UX。</td>
        <td>HoloLens 2<br>沉浸式頭戴裝置</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">免持式</a></td>
        <td>使用者雙手沒空 (例如在職培訓和維護) 時的情境體驗。</td>
        <td>需要學習一下。 如果無法使用手部，裝置可搭配語音和自然語言使用。</td>
        <td>HoloLens 2<br>HoloLens (第 1 代)<br>沉浸式頭戴裝置</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">目光和行動</a></td>
        <td>點選體驗，例如 3D 簡報、示範。</td>
        <td>需要 HMD 訓練，但不是在行動裝置上。 最適合用於可存取的控制器。 最適合用於 HoloLens (第 1 代)。</td>
        <td>HoloLens 2<br>HoloLens (第 1 代)<br>沉浸式頭戴裝置<br>行動 AR</td>
    </tr>
</table>
<br>

為了確保使用者互動體驗不會有任何落差，從頭到尾遵循單一模型的指引將是最佳方式。

下列各節會逐步說明選取及實作其中一個互動模型的步驟。  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>在此頁面結束前，您會了解我們對於下列各項的指引：
 
* 為您的客戶選擇互動模型
* 實作互動模型
* 互動模型之間的轉換
* 設計後續步驟


## <a name="choose-an-interaction-model-for-your-customer"></a>為您的客戶選擇互動模型

開發人員和創作者通常都已考量其客戶可使用的互動類型。 為了鼓勵以客戶為主的設計方式，我們建議您遵循下列指引來選取最適合客戶的互動模型。

### <a name="why-follow-this-guidance"></a>為什麼要遵循本指引？

* 我們的互動模型都經過客觀和主觀條件測試，例如實際和認知投入、直覺性和學習力。 
* 由於互動不同，互動模型之間的視訊/音訊能供性及物件行為也可能不同。  
* 結合多個互動模型的組件，會引起競用能供性 (例如同時手部光線和頭部注視游標) 的風險。 這可能會造成使用者的負荷和困惑。

以下是如何針對每個互動模型將能供性和行為最佳化的一些範例。 我們常會看到新使用者有類似的問題，例如「如何得知系統是否能運作」  、「如何得知我可以做什麼」  、「如何得知它是否了解我剛做了什麼？」 

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
        <td><strong>如何得知它是否能運作？</strong></td>
        <td><strong>如何得知我可以做什麼？</strong></td>
        <td><strong>如何得知我剛做了什麼？</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">手部和運動控制器</a></td>
        <td>我看到手狀網格、指尖能供性或手部/控制器光線。</td>
        <td>我看到當我的手部靠近物件時會出現可握住的把手或週框方塊。</td>
        <td>我會在握住和放開時聽到聽得見的音調並看到動畫。</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">頭部目光和行動</a></td>
        <td>我在視野中央看到一個游標。</td>
        <td>游標會在其掃過某些物件時變更狀態。</td>
        <td>當我採取動作時，我會看到/聽到看得見和聽得見的確認。</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">免持式 (頭部注視並佇留)</a></td>
        <td>我在視野中央看到一個游標。</td>
        <td>當我佇留在可互動的物件上時，我會看到進度列指示器。</td>
        <td>當我採取動作時，我會看到/聽到看得見和聽得見的確認。</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">免持式 (語音命令)</a></td>
        <td>我看到接聽指示器以及可顯示系統所聽內容的字幕。</td>
        <td>我取得語音提示。 當我說：「我可以說什麼？」 我看到回饋。</td>
        <td>當我發出命令時，我會看到/聽到看得見和聽得見的確認，或在必要時取得去除混淆 UX。</a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a>以下是我們發現有助於小組選取互動模型的問題：
 
1.  Q:我的使用者想要觸控全像投影和執行精準全像攝影操作嗎？<br><br>
答：若是如此，請查看「雙手和運動控制器」互動模型，以進行精準定向和操作。
 
2.  Q:我的使用者需要為了實際操作而騰出雙手嗎？<br><br>
答：若是如此，請查看免持式互動模型，此模型可透過注視和語音型互動提供絕佳的免持式體驗。
 
3.  Q:我的使用者是否有時間了解我的 MR 應用程式互動，或者他們需要最低學習曲線的互動？<br><br>
答：針對最低學習曲線和最直覺的互動，我們建議使用「雙手和運動控制器」模型，只要使用者能夠使用其雙手進行互動即可。
 
4.  Q:我的使用者是否要使用運動控制器來指向及操作？<br><br>
答：「雙手和運動控制器」模型包含優質運動控制器體驗的所有指引。
 
5.  Q:我的使用者是否使用協助工具控制器或通用藍牙控制器，例如 Clicker？<br><br>
答：我們建議使用所有非追蹤式控制器都適用的「頭部注視並認可」模型。 其設計訴求是可讓使用者使用簡單的「定向和行動」經歷整個體驗。 
 
6.  Q:相對於瀏覽 UI 控制項的密集版面配置，我的使用者只是經由「點選」來進行體驗 (例如在類似 3D 投影片的環境中) 嗎？<br><br>
答：如果使用者不需要控制大量 UI，則「頭部注視並認可」會提供學得會的選項，使用者就不必擔心如何定向。 
 
7.  Q:我的使用者是否同時使用 HoloLens (第 1 代) 和 HoloLens 2/Windows Mixed Reality 沉浸式頭戴裝置 (VR)？<br><br>
答：由於「頭部注視並認可」是 HoloLens (第 1 代) 適用的互動模型，我們建議支援 HoloLens (第 1 代) 的創作者將「頭部注視並認可」用於使用者在 HoloLens (第 1 代) 頭戴式裝置上所將體驗的任何功能或模式。 如需取得多代 HoloLens 絕佳體驗的詳細資訊，請參閱底下有關「轉換互動模型」  的一節。
 
8.  Q:對於經常移動 (涵蓋大型空間或在空間之間移動) 的使用者，與傾向在單一空間工作的使用者而言，有何差別？<br><br>
答：任何互動模型都適用於這些使用者。  

> [!NOTE]
> [即將推出](news.md)應用程式設計專屬的詳細指引。


## <a name="transitioning-interaction-models"></a>轉換互動模型
在某些使用案例中，可能需要使用多個互動模型。 例如，您應用程式的「建立流程」使用「雙手和運動控制器」  互動模型，但您想要讓現場技術人員使用免持式模式。
如果您的體驗的確需要多種互動模型，請您留意，有許多終端使用者可能會在轉換模型時遇到困難，尤其是不熟悉混合實境的使用者。

> [!Note]
> 我們會繼續撰寫更多適用於開發人員和設計人員的指引，讓他們了解使用多個 MR 互動模型的方式、時機和原因。
 

## <a name="see-also"></a>另請參閱
* [舒適度](comfort.md)
* [眼動式互動](eye-gaze-interaction.md)
* [HoloLens 2 的眼球追蹤](eye-tracking.md)
* [目光和行動](gaze-and-commit.md)
* [目光和停駐](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [運動控制器](motion-controllers.md)
* [空間對應](spatial-mapping.md)
* [空間音效設計](spatial-sound-design.md)
* [語音輸入](voice-input.md)


