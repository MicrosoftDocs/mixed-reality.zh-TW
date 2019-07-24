---
title: 案例研究-Lowe 廚房的課程
description: HoloLens 小組想要分享一些衍生自 Lowe 的 HoloLens 專案的最佳作法。
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe, HoloLens, 廚房, 個案研究
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522340"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>案例研究-Lowe 廚房的課程

HoloLens 小組想要分享一些衍生自 Lowe 的 HoloLens 專案的最佳作法。 以下是 Lowe 的 HoloLens 投影影片, 示範于 Satya 的 2016 Ignite 專題主題。
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Lowe 的 HoloLens 最佳做法

這兩段影片涵蓋的最佳作法是衍生自 Lowe 的 HoloLens 試驗, 這是從2016年4月起在兩個 Lowe 的商店中。 主要主題如下:
* 最大化行動裝置的效能
* 建立具有完整全像攝影畫面的 UX 方法 (第二個說話)
* 精確度對齊 (第二次交談)
* 共用的全像攝影體驗 (第二談)
* 與客戶互動 (第二談)

## <a name="video-1"></a>影片1

**最大化行動裝置的效能**HoloLens 是非網路共用裝置, 在裝置中進行所有處理。 這需要行動平臺, 而且需要類似于建立行動應用程式的思維方式。 Microsoft 建議您的 HoloLens 應用程式維護 60FPS, 為您的使用者提供美味體驗。 具有低 FPS 會導致不穩定的全息影像。

使用自訂著色器 (可在[Hololens 工具](https://github.com/Microsoft/HoloToolkit-Unity)組中免費取得), 在 HoloLens 上進行開發時, 應查看的一些最重要的事項是資產優化/減去。 另一個重要的考慮是從專案的一開始測量畫面播放速率。 視專案而定, 顯示資產的順序也可能是一個很大的參與者
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>影片2

**建立具有完整全像攝影畫面的 UX 方法**請務必瞭解在實體世界中的全息影像位置。 在 Lowe 中, 我們討論了各種不同的 UX 方法, 可協助使用者體驗清理, 同時仍然看到最大的全息影像環境。

**精確度對齊**在 Lowe 的案例中, 最重要的是將全息的全像投影至實體廚房的體驗。 我們會討論一些技術, 協助確保說服使用者實體環境已變更的經驗。

**共用**的全像攝影體驗「耦合」是使用 Lowe 體驗的主要方式。 一個人可以變更檯面, 而另一人會看到變更。 我們稱之為「共用體驗」。

**與客戶互動**Lowe 的設計人員不會使用 HoloLens, 但需要查看客戶看到的內容。 我們會示範如何在 UWP 應用程式上捕捉客戶看到的內容。
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
