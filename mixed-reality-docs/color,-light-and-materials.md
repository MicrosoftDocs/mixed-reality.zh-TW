---
title: 色彩、光線和材質
description: 設計混合現實的內容時, 必須仔細考慮您的體驗中所使用的每個視覺資產的色彩、光源和材質。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 設計, 色彩, 光線, 材質
ms.openlocfilehash: bef0c8b63c109baa536e4192ce94919eb888faf2
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896512"
---
# <a name="color-light-and-materials"></a>色彩、光線和材質

設計混合現實的內容時, 必須仔細考慮您的體驗中所使用的每個視覺資產的色彩、光源和材質。 這些決策可用於美觀用途, 例如使用光線和材質來設定沉浸式環境的色調, 以及功能的用途, 例如使用驚人的色彩來警示使用者即將採取的動作。 每個決策都必須針對經驗目標裝置的機會和限制進行權衡。

以下是在沉浸式和全像耳機上轉譯資產的特定指導方針。 其中有許多是與其他技術領域緊密相關, 而且有一份相關主題清單可以在本文結尾的 [[另請參閱](color,-light-and-materials.md#see-also)] 一節中找到。

## <a name="rendering-on-immersive-vs-holographic-devices"></a>在沉浸式與全像攝影裝置上呈現

與全像攝影耳機中轉譯的內容相比, 以沉浸式耳機轉譯的內容會以視覺化方式呈現。 雖然沉浸式耳機通常會以2D 螢幕上的預期來轉譯內容, 但 HoloLens 這類的全像攝影耳機會使用色彩順序, 請參閱以 RGB 顯示呈現全息影像。

總是花時間在全像耳機中測試您的全像攝影體驗。 內容的外觀 (即使是專為全像攝影裝置所建立), 在次要監視器、快照和 spectator view 中的顯示方式會有所不同。 別忘了使用裝置的經驗、測試全息影像的光線, 以及從所有邊 (以及從上方和下方) 觀察內容的呈現方式。 請務必在裝置上的亮度設定範圍進行測試, 因為不太可能所有的使用者都會共用假設的預設值, 以及一組不同的光源條件。

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>在全像攝影裝置上呈現的基本概念
* 全像攝影**裝置具有 [加法] 顯示器**–從真實世界將光線新增到光線來建立全像投影, 白色會顯示為明亮, 而黑色則會透明。
* **色彩影響會因使用者的環境而異**–使用者的房間內有許多不同的光源狀況。 建立具有適當對比層級的內容, 以利清楚地協助。
* **避免動態光源**–全像全像攝影的全像攝影, 最有效率。 使用 advanced、dynamic 光源可能會超過行動裝置的功能。 需要動態光源時, 建議使用[混合現實工具組標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)。 

## <a name="designing-with-color"></a>使用色彩進行設計

由於加總顯示的本質, 某些色彩在全像攝影顯示器上可能會有所不同。 有些色彩會在光源環境中彈出, 有些則會顯示為較不影響力。 酷炫色彩通常會 recede 到背景, 而暖色彩會跳至前景。 當您探索體驗的色彩時, 請考慮下列因素:
* **色域**-HoloLens 從「寬範圍」的色彩中獲益, 概念上類似于 Adobe RGB。 因此, 某些色彩可能會在裝置中呈現不同的品質和標記法。
* **Gamma** -呈現影像的亮度和對比會因沉浸式和全像攝影裝置而異。 這些裝置的差異通常會顯示色彩和陰影的深色區域、更多或較不明亮。
* **色彩分隔**-也稱為 "color 並劃分" 或 "color fringing", 當使用者以眼睛追蹤物件時, 移動全息影像 (包括游標) 最常發生的色彩區分。
* **色彩一致性**-通常會將全像投影轉譯成明亮, 使其維持色彩一致性 (不論背景為何)。 大型區域可能會變得 blotchy。 避免出現明亮、純色的大型區域。
* **呈現淺色**-白色外觀非常明亮, 應謹慎使用。 在大部分情況下, 請考慮使用與 R 235 G 235 B 235 有關的白色值。 較大的區域可能會造成使用者 discomfort。

**呈現深色色彩**

由於加總顯示的本質, 暗色調會顯示為透明。 實心的黑色物件與真實世界的外觀並無不同。 請參閱下方的 Alpha 色板。 若要讓「黑色」的外觀嘗試使用非常深的灰階 RGB 值, 例如16、16、16。

![一般與寬色色域](images/640px-widegamut.png)<br>
*一般與寬色色域*

## <a name="technical-considerations"></a>技術考慮
* **別名**-明智失真、不規則或「樓梯步驟」, 其中全息圖形幾何的邊緣會符合真實世界。 使用具有高細節的材質可以 aggravate 此效果。 材質應該對應並啟用篩選。 請考慮將全息影像的邊緣漸淡, 或加入在物件周圍建立黑色邊緣框線的材質。 盡可能避免精簡型幾何。
* **Alpha**色板-您必須針對未轉譯全息影像的任何零件, 清除您的 Alpha 色板以完全透明。 當您從裝置或使用 Spectator View 取得影像/影片時, 將 Alpha 未定義的會導致視覺效果構件。
* **材質軟化**-由於光線是全像投影顯示器的加法, 因此最好避免較大的明亮色彩, 因為它們通常不會產生想要的視覺效果。

## <a name="storytelling-with-light-and-color"></a>以光線和色彩故事行銷

光線和色彩可協助讓您的全息影像在使用者的環境中以更自然的方式呈現, 以及提供使用者的指引和協助。 對於全像攝影的體驗, 請在探索光源和色彩時考慮下列因素:
* **Vignetting** -加深材質的「vignette」效果有助於將使用者的注意力放在視圖欄位的中央。 此效果會從使用者的注視向量中, 以一些半徑來去除全息的全像投影資料。 請注意, 當使用者的視圖從傾斜或 glancing 角度進行全息時, 這也是有效的。
* **強調**-透過對比色彩、亮度和光源, 將注意力吸引物件或互動點。 如需故事行銷中光源方法的詳細資訊, 請參閱[圖元 Cinematography-電腦圖形的光源方法](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)。

![使用色彩來顯示故事行銷元素的強調, 此處顯示于片段的場景中。](images/640px-fragments.jpg)<br>
*使用色彩來顯示故事行銷元素的強調, 此處顯示于[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)的場景中。*

## <a name="see-also"></a>另請參閱
* [色彩分隔](hologram-stability.md#color-separation)
* [全息](hologram.md)
* [Microsoft 設計語言-色彩](https://www.microsoft.com/design/color)
* [通用 Windows 平臺色彩](https://docs.microsoft.com/windows/uwp/style/color)
