---
layout: LandingPage
title: 開始設計並建立原型
description: 如果您已準備好要建立一些東西，請學習所需的基本概念以開始設計並建立原型。
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 探索, 散佈, 索引, 登陸頁面, 設計, 開發, 教學課程, 範例應用程式, 基本概念, 案例研究, 資源, HoloLens 操作說明, 開放原始碼專案, 核心概念, 互動
ms.openlocfilehash: 9ef408e1551e9f6c52a6c5fcf7df3123cc099c8c
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "75334090"
---
# <a name="start-designing-and-prototyping"></a>開始設計並建立原型


![混合實境設計抽象](images/03_Design.png)

## <a name="expand-your-design-process"></a>[展開您的設計程序](case-study-expanding-the-design-process-for-mixed-reality.md)

隨著 Microsoft 在 2016 年向積極的開發人員推出了 HoloLens，該團隊已與 Microsoft 內部及外部的工作室合作，以建立裝置的啟動體驗。 這些團隊藉由實踐，在混合實境設計的新領域中找到機會和挑戰。 [閱讀更多內容](case-study-expanding-the-design-process-for-mixed-reality.md)

<br>

---

## <a name="what-are-the-core-concepts-of-an-experience"></a>體驗有哪些核心概念？

### <a name="keep-the-user-comfortable---comfort"></a>[讓使用者感到舒適 - (舒適)](comfort.md)
為了確保頭戴顯示器的最大舒適度，設計人員和開發人員必須以模擬這些提示在自然世界中運行的方式來建立和呈現內容。

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frame"></a>[考慮使用者如何看到世界 - (全像攝影框架)](holographic-frame.md)
使用者透過其頭戴式裝置所提供的矩形視口，來看到混合實境的世界。 在 HoloLens 上，這個矩形區域稱為全像攝影框架，可讓使用者看到其周圍真實世界中的數位內容。

<br>

### <a name="types-of-mixed-reality-apps"></a>[混合實境應用程式類型](types-of-mixed-reality-apps.md)
開發混合實境應用程式的優點之一，是平台可以支援各種不同的體驗。 從完全沉浸式虛擬環境到使用者目前環境下的輕量資訊分層，混合實境提供了一組強大的工具，可將任何體驗變為現實。

<br>

### <a name="keeping-holograms-in-place---coordinate-systems"></a>[就地保留全像投影 (座標系統)](coordinate-systems.md)
混合實境應用程式的核心是將全像投影放在您的世界中，讓它看起來聽起來像是真正的物件。 這牽涉到將那些全像投影精準地放在世界各地對使用者有意義的地方，不論是他們所在的實際空間或您所建立的虛擬領域。

<br>

### <a name="making-holographic-objects-feel-real---spatial-mapping"></a>[讓全像攝影物件感覺真實 - (空間對應)](spatial-mapping.md)
空間對應可以讓使用者將物件放置在實際的表面上。 這有助於錨定使用者世界中的物件，並利用真實世界的深度提示。

<br>


---

<br>

![互動設計因素](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>要考慮的互動設計因素


### <a name="choose-an-interaction-model-for-your-customer"></a>[為您的客戶選擇互動模型](interaction-fundamentals.md)
簡單、直覺式互動的原理貫穿整個混合實境平台。 我們採取了三個步驟，以確保應用程式設計人員和開發人員可為其客戶提供簡單且直覺式的互動。

<br>

### <a name="hands-and-motion-controllers"></a>[手部和運動控制器](hands-and-tools.md)
使用者可以直接使用單手或雙手來觸控和操作全像投影，就像對真實世界中的物件所做的一樣。 或者，您可以透過運動控制器，藉由提供跨越大範圍距離的精確互動，來擴充使用者的身體能力。

<br>

### <a name="directly-commanding-objects-with-voice-input"></a>[使用語音輸入直接命令物件](voice-input.md)
語音是 HoloLens 輸入的其中一種主要形式。 它可讓您直接命令全像投影，而不需要使用手勢。 語音輸入是溝通意圖的一種自然方式。

<br>

### <a name="leveraging-the-users-eye-gaze"></a>[利用使用者的眼部注視](eye-tracking.md)
HoloLens 2 將全像攝影體驗的內容和人類理解能力帶入了新境界；它讓開發人員能夠運用使用者視線方向的相關資訊。

<br>

### <a name="color-light-and-materials"></a>[色彩、光線和材質](color,-light-and-materials.md)
設計混合實境的內容時，必須仔細考慮您體驗中所使用的每個視覺資產的色彩、光源和材質。

<br>

### <a name="suggesting-the-scale-of-an-object"></a>[建議物件的縮放比例](scale.md)
以全像攝影形式呈現看似逼真內容的關鍵，就是盡可能地模擬真實世界的視覺特性。 這表示我們可以盡可能地將多個視覺提示加以結合，協助我們 (在真實世界中) 了解物件的位置、大小以及其構成。

<br>

### <a name="clear-and-readable-typography"></a>[清楚易懂的印刷樣式](typography.md)
就像2D 螢幕上的印刷樣式一樣，目標是要清楚易懂。 有了混合實境的三維外觀比例，就有機會以更佳的方式來影響文字和整體使用者體驗。

<br>

### <a name="ux-elements-for-the-mixed-reality"></a>[混合實境的 UX 元素](app-patterns-landingpage.md)
了解混合實境中空間互動和 UI 的建置元素。
<br>


---

## <a name="choose-a-prototyping-option"></a>選擇原型設計選項  

:::row:::   
    :::column:::    
       [![學習 Unity](images/Final_unity_logo.png)](https://learn.unity.com/)<br>
        **[學習 Unity](https://learn.unity.com/)**<br>
        瞭解如何使用 Unity 建立互動式體驗。 邊做邊學，從開始到完成。
    :::column-end:::    
    :::column:::    
        [![混合實境工具組 (MRTK)](images/Final_mrtk-small_logo.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[混合實境工具組 (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        透過混合實境工具組的空間互動和 UI 基本要素，您可以使用 Unity 快速進行混合實境的設計和開發。   
    :::column-end:::
    :::column:::    
        [![混合實境設計實驗室](images/Final_mrdl_logo.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[混合實境設計實驗室](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        取得範例應用程式，示範如何使用 MRTK 的建置元素來建立美觀的混合實境體驗。
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/Final_maquette_logo.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        為 VR 而設計。 Microsoft Maquette 讓空間原型設計變得簡單、快速、身歷其境。 
    :::column-end:::    
:::row-end:::

<br>

---



## <a name="what-would-you-like-to-do-next"></a>接著要執行什麼作業？

:::row:::
    :::column:::
       [![了解基本概念](images/icon-lightbulb.png)](index.md#understand-the-basics)<br>
        **[了解基本概念](index.md#understand-the-basics)**<br>
        進一步瞭解混合實境的定義以及其使用方式。
    :::column-end:::
    :::column:::
        [![參加活動](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[參加活動](sf-academy-events.md)**<br>
        參觀硬體並取得實際操作教學課程，製作您的第一個 HoloLens 2 應用程式。
    :::column-end:::
    :::column:::
        [![安裝工具](images/icon-design.jpg)](install-the-tools.md)<br>
         **[安裝工具](install-the-tools.md)**<br>
        使用安裝檢查清單來取得建置 HoloLens 和混合實境應用程式所需的工具。
    :::column-end:::
    :::column:::
        [![開始進行開發](images/icon-developer.jpg)](development.md)<br>
        **[開始進行開發](development.md)**<br>
        根據您的技能層級、工作風格或感興趣的平台，選擇開發路徑。
    :::column-end:::
:::row-end:::


<br>

<br>


