---
layout: LandingPage
title: 開始設計並建立原型
description: 我準備好要建立一些項目。 學習所需的基本概念以開始設計並建立原型。
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境、探索、散佈、索引、登陸頁面、設計、開發、教學課程、範例應用程式、基本概念、案例研究、資源、HoloLens 操作說明、開放原始碼專案
ms.openlocfilehash: 3efb411425d18a8f50a209b69b00bfa038d594f1
ms.sourcegitcommit: 183b6248807f600fe7d83daa13a6fe0b0f0dc846
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2019
ms.locfileid: "70148006"
---
# <a name="start-designing-and-prototyping"></a>開始設計並建立原型


![基本要素](images/text_in_unity_viewingangle.jpg)

## <a name="what-are-the-core-concepts-of-an-experience"></a>體驗有哪些核心概念？

### <a name="keep-the-user-comfortable---comfortcomfortmd"></a>[讓使用者感到舒適 - (舒適)](comfort.md)
為了確保頭戴顯示器的最大舒適度，設計人員和開發人員必須以模擬這些提示在自然世界中運行的方式來建立和呈現內容。

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frameholographic-framemd"></a>[考慮使用者如何看到世界 - (全像攝影框架)](holographic-frame.md)
使用者透過其頭戴式裝置所提供的矩形視口，來看到混合實境的世界。 在 HoloLens 上，這個矩形區域稱為全像攝影框架，可讓使用者看到其周圍真實世界中的數位內容。

<br>

### <a name="making-holographic-objects-feel-real---spatial-mappingspatial-mappingmd"></a>[讓全像攝影物件感覺真實 - (空間對應)](spatial-mapping.md)
空間對應可以讓使用者將物件放置在實際的表面上。 這有助於錨定使用者世界中的物件，並利用真實世界的深度提示。

<br>

### <a name="suggesting-the-scale-of-an-object---scalescalemd"></a>[建議物件的縮放比例 - (縮放比例)](scale.md)
以全像攝影形式呈現看似逼真內容的關鍵，就是盡可能地模擬真實世界的視覺統計資料。 這表示我們可以盡可能地將多個視覺提示加以結合，協助我們 (在真實世界中) 了解物件的位置、大小以及其構成。

<br>

### <a name="clear-and-readable-typographytypographymd"></a>[清楚易懂的印刷樣式](typography.md)
就像2D 螢幕上的印刷樣式一樣，目標是要清楚易懂。 有了混合實境的三維外觀比例，就有機會以更佳的方式來影響文字和整體使用者體驗。

<br>

### <a name="color-light-and-materialscolor-light-and-materialsmd"></a>[色彩、光線和材質](color,-light-and-materials.md)
設計混合實境的內容時，必須仔細考慮您體驗中所使用的每個視覺資產的色彩、光源和材質。


<br>

---



![互動設計因素](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>要考慮的互動設計因素


### <a name="expanding-the-design-process-for-mixed-realitycase-study-expanding-the-design-process-for-mixed-realitymd"></a>[擴充混合實境的設計程序](case-study-expanding-the-design-process-for-mixed-reality.md)
隨著 Microsoft 在 2016 年向積極的開發人員推出了 HoloLens，該團隊已與 Microsoft 內部及外部的工作室合作，以建立裝置的啟動體驗。 這些團隊藉由實踐，在混合實境設計的新領域中找到機會和挑戰。

<br>

### <a name="types-of-mixed-reality-appstypes-of-mixed-reality-appsmd"></a>[混合實境應用程式類型](types-of-mixed-reality-apps.md)
開發 Windows Mixed Reality 應用程式的優點之一，是該平台可以支援各種頻譜體驗。 從完全沉浸式虛擬環境到使用者目前環境下的輕量資訊分層，Windows Mixed Reality 提供了一組強大的工具，可將任何體驗變為現實。

<br>

### <a name="choose-an-interaction-model-for-your-customerinteraction-fundamentalsmd"></a>[為您的客戶選擇互動模型](interaction-fundamentals.md)
簡單、直覺式互動的原理貫穿整個混合實境平台。 我們採取了三個步驟，以確保應用程式設計人員和開發人員可為其客戶提供簡單且直覺式的互動。

<br>

### <a name="hands-and-motion-controllershands-and-toolsmd"></a>[手部和運動控制器](hands-and-tools.md)
就像2D 螢幕上的印刷樣式一樣，目標是要清楚易懂。 有了混合實境的三維外觀比例，就有機會以更佳的方式來影響文字和整體使用者體驗。

<br>

### <a name="voice-commandingvoice-designmd"></a>[語音命令](voice-design.md)
使用語音命令時，一般會使用注視來作為鎖定機制，無論是要作為指標 (「選取」) 還是用來對應用程式指示命令 (「看到什麼就說什麼」)。

<br>

### <a name="leveraging-the-users-eye-gazeeye-trackingmd"></a>[利用使用者的眼部注視](eye-tracking.md)
HoloLens 2 將全像攝影體驗的內容和人類理解能力帶入了新境界；它讓開發人員能夠運用使用者視線方向的相關資訊。


<br>


---

## <a name="choose-a-prototyping-option"></a>選擇原型設計選項  





:::row:::
    :::column:::
        <img alt="Unity Logo" width="70" height="70" src="images/unity_logo.png">
         <a href="https://learn.unity.com/" target="">Learn Unity</a>
        Learn how to create interactive experiences with Unity
    :::column-end:::
        :::column:::
       <img alt="MRTK Logo" width="70" height="70" src="images/MRTK_Logo_Sq_Text.png">
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="">混合實境工具組</a>透過混合實境工具組的空間互動和 UI 基本要素，您可以使用 Unity 快速進行混合實境的設計和開發
    :::column-end:::
    :::column:::
        <img alt="MRDL Logo" width="70" height="70" src="images/MRDL_Logo_Sq_Text.png">
         <a href="https://github.com/Microsoft/MRDL_Unity_PeriodicTable" target="">Mixed Reality Design Labs</a>
        Mixed Reality Design Lab's sample apps shows how to use MRTK's building blocks to create beautiful mixed reality experiences.
    :::column-end:::
    :::column:::
        <img alt="Maquette Logo" width="70" height="70" src="images/MicrosoftMaquette_logo_glow.png">
         <a href="https://www.maquette.ms/" target="">Microsoft Maquette</a>
        Design for VR. Microsoft Maquette makes spatial prototyping easy, quick, and immersive.
    :::column-end:::
:::row-end:::


<br>

---



## <a name="what-would-you-like-to-do-next"></a>接著要執行什麼作業？


:::row:::
    :::column:::
       ![了解基本概念](images/icon-lightbulb.jpg)
        ### [Understand the basics](index-hidden.md)
        Get a better understanding of what defines mixed reality and how it’s being used.
    :::column-end:::
    :::column:::
        ![Install the tools](images/icon-design.jpg)
         ### [Install the tools](install-the-tools.md)
        Use the installation checklist to get the tools you need to build applications for Microsoft HoloLens and Windows Mixed Reality.
    :::column-end:::
    :::column:::
        ![Come to an event](images/icon-calendar.jpg)
         ### [Come to an event](sf-academy-events.md)
        See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.
    :::column-end:::
    :::column:::
        ![Start developing](images/icon-developer.jpg)
         ### [Start developing](development-hidden.md)
        Choose a development path based on your skill level, work style. or platform interest.
    :::column-end:::
:::row-end:::



