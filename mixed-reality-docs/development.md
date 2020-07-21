---
layout: LandingPage
title: 了解工具和架構
description: HoloLens 和沉浸式頭戴裝置的混合實境開發人員文件。
author: grbury
ms.author: grbury
ms.date: 04/27/2020
ms.topic: overview
ms.localizationpriority: high
keywords: 混合實境, 開發, 開發, HoloLens, unity, unreal, directx
ms.openlocfilehash: 3c874e45e555ec6defa611bd5404abbb18e6612e
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447854"
---
# <a name="learn-the-tools-and-architecture"></a>了解工具和架構

![抽象 3D 球體](images/07_Development.png)

## <a name="expand-your-design-process"></a>[展開您的設計程序](case-study-expanding-the-design-process-for-mixed-reality.md)

隨著 Microsoft 在 2016 年向積極的開發人員推出了 HoloLens，該團隊已與 Microsoft 內部及外部的工作室合作，以建立裝置的啟動體驗。 這些團隊藉由實踐，在混合實境設計的新領域中找到機會和挑戰。 [閱讀更多內容](case-study-expanding-the-design-process-for-mixed-reality.md)


<br>

---


## <a name="what-technology-path-are-you-interested-in"></a>您對哪像技術主題感興趣？ 


:::row:::   
    :::column:::    
       [![Unity](images/unity_logo.png)](development.md#unity)<br>
        **[Unity](development.md#unity)**<br>   
        使用 Unity 建置跨平台、功能完整的混合實境應用程式。
    :::column-end:::    
    :::column:::    
        [![Unreal](images/Unreal_logo.png)](development.md#unreal)<br>
        **[Unreal](development.md#unreal)**<br> 
        在 Unreal Engine 中，透過生產環境就緒的支援來建立美觀的混合實境體驗。 
    :::column-end:::
    :::column:::    
        [![JavaScript](images/web-logo.png)](development.md#javascript)<br>
        **[JavaScript](development.md#javascript)**<br>
        JavaScript 和 WebXR 裝置 API 是一個開放的規格，可讓您在任何平台的瀏覽器中體驗混合實境。    
    :::column-end:::        
    :::column:::    
        [![Native](images/VisualStudio-small_logo.png)](development.md#native)<br>
        **[Native](development.md#native)**<br> 
        直接編寫 Windows Mixed Reality API 程式碼以建立混合實境應用程式。 
    :::column-end:::    
:::row-end:::

<br>

---

## <a name="unity"></a>Unity


### <a name="unity-development-overview"></a>[Unity 開發概觀](unity-development-overview.md)
我們建議您花一些時間來探索 Unity 教學課程。 如果您需要資產，Unity 具有完整的資產存放區。 

<br>

### <a name="microsofts-mixed-reality-toolkit-mrtk-for-unity"></a>[適用於 Unity 的 Microsoft 混合實境工具組 (MRTK)](mrtk-getting-started.md)
Unity 的 MRTK v2 是混合實境應用程式的開放原始碼跨平台開發套件。 MRTK 第 2 版主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。

<br>

### <a name="open-source-sample-apps-and-step-by-step-tutorials"></a>[開放原始碼範例應用程式和逐步教學課程](tutorials.md)
HoloLens 2 教學課程的設計目的是協助開發人員了解開發混合實境應用程式的技術和最佳做法。 這些教學課程是以混合實境工具組 2.0 (MRTK 2.0) 為基礎。

<br>

### <a name="hand-interaction-examples-scene-mrtk-for-unity"></a>[Unity 的手部互動範例場景 (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#open-and-run-the-handinteractionexamples-scene-in-editor)
HandInteractionExamples.unity 的範例場景包含各種類型的互動和 UI 控制項，其強調以關節連接的手部輸入。
>[!NOTE]
>需要安裝 MRTK Foundation 和範例 Unity 套件。

### <a name="eye-tracking-examples-mrtk-for-unity"></a>[Unity 的眼球追蹤範例 (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_ExamplesOverview.html)
本頁面說明如何以我們提供的 MRTK 眼球追蹤範例為本，快速開始使用眼球追蹤。
>[!NOTE]
>需要安裝 MRTK Foundation 和範例 Unity 套件。

<br>

---

## <a name="unreal"></a>Unreal

### <a name="unreal-development-overview"></a>[Unreal 開發概觀](unreal-development-overview.md)
瞭解如何使用 Unreal 建立混合實境應用程式。

<br>

### <a name="microsofts-mixed-reality-toolkit-mrtk-for-unreal"></a>[適用於 Unreal 的 Microsoft 混合實境工具組 (MRTK)](https://github.com/microsoft/MixedRealityToolkit-Unreal)
適用於 Unreal 的混合實境工具組 (MRTK-Unreal) 是一組元件，形式為外掛程式、範例和文件，其設計目的是加速使用 Unreal Engine 的混合實境應用程式開發。

<br>

### <a name="open-source-sample-apps-and-a-step-by-step-tutorial"></a>[開放原始碼範例應用程式和逐步教學課程](unreal-uxt-ch1.md)
在 Unreal 中開始使用混合實境開發的教學課程，會逐步引導開發人員完成使用[適用於 Unreal 的 UX 工具 v0.8](https://github.com/microsoft/MixedReality-UXTools-Unreal) 來建立 HoloLens 2 應用程式的端對端程序。

<br>

---

## <a name="javascript"></a>JavaScript   

### <a name="javascript-development-overview"></a>[JavaScript 開發概觀](javascript-development-overview.md)   
了解如何使用任何平台的 JavaScript 建立混合實境應用程式。

<br>

---

## <a name="native"></a>原生


### <a name="native-development-overview"></a>[原生開發概觀](directx-development-overview.md)
最快速的路徑是建立原生的混合實境應用程式。

<br>

### <a name="directx-uwp-app-templates-for-mixed-reality"></a>[適用於混合實境的 DirectX UWP 應用程式範本](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)
使用 DirectX 開始撰寫混合實境應用程式所需的所有基本知識。

<br>

---


## <a name="what-would-you-like-to-do-next"></a>接著要執行什麼作業？


:::row:::
    :::column:::
       [![了解基本概念](images/icon-lightbulb.png)](get-started-with-mr.md#understand-the-basics)<br>
        **[了解基本概念](get-started-with-mr.md#understand-the-basics)**<br>
        進一步瞭解混合實境的定義以及其使用方式。
    :::column-end:::
    :::column:::
        [![成為建立者](images/icon-design.jpg)](design.md)<br>
         **[成為建立者](design.md)**<br>
        學習所需的基本概念以開始設計並建立原型。
    :::column-end:::
    :::column:::
        [![安裝工具](images/icon-developer.jpg)](install-the-tools.md)<br>
         **[安裝工具](install-the-tools.md)**<br>
        使用安裝檢查清單來取得建置 HoloLens 和混合實境應用程式所需的工具。
    :::column-end:::
    :::column:::
        [![參加活動](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[參加活動](sf-academy-events.md)**<br>
        參觀硬體並取得實際操作教學課程，製作您的第一個 HoloLens 2 應用程式。
    :::column-end:::
:::row-end:::


<br>

<br>
