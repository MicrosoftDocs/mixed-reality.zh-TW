---
title: 3D 應用程式啟動器設計指引
description: 3D 應用程式啟動器是使用者 mixed reality 房屋中的「實體」物件, 他們可以選擇用來啟動應用程式。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 設計, 3D 應用程式啟動器, 沉浸式耳機, 即時 cube
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63517789"
---
# <a name="3d-app-launcher-design-guidance"></a>3D 應用程式啟動器設計指引

當您放在 Windows Mixed Reality 沉浸式 (VR) 頭戴式裝置上時, 您會進入 Windows Mixed Reality 首頁, 並以山脈和水括住的 cliff 做為房屋 (雖然您可以[選擇其他環境, 甚至是建立自己的環境](add-custom-home-environments.md))。 在此家中的空間內, 使用者可以自由地排列及組織其所需的3D 物件和應用程式。 **3d 應用程式啟動器**是使用者 mixed reality 房屋中的「實體」物件, 他們可以選擇用來啟動應用程式。

![實例Floaty 鳥3D 應用程式啟動器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Floaty 鳥3D 應用程式啟動器範例 (虛構應用程式)*

## <a name="3d-app-launcher-creation-process"></a>3D 應用程式啟動器建立進程

建立3D 應用程式啟動器有3個步驟:
1. 設計和 concepting (本文)
2. [模型化和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 將它整合到您的應用程式中:
    * [UWP 應用程式](implementing-3d-app-launchers.md)
    * [Win32 應用程式](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>設計概念

### <a name="fantastic-yet-familiar"></a>非常熟悉的絕佳

您的應用程式啟動器所在的 Windows Mixed Reality 環境是常見的部分 fantastical/sci。 最佳的啟動器會遵循此世界的規則。 請考慮如何從您的應用程式中採取熟悉、具代表性的物件, 但會將一些實際的現實規則折。 會產生魔術。

### <a name="intuitive"></a>基本

當您查看應用程式啟動器時, 其目的是要啟動您的應用程式, 應該很明顯, 而且不會造成任何混淆。 例如, 請確定您的啟動器是您應用程式的相當明顯的代表, 而不會與 Cliff 房屋中的一段 décor 混淆。 您的應用程式啟動器應邀請人員進行觸控/選取。

![實例最新附注3D 應用程式啟動器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*最新附注3D 應用程式啟動器範例 (虛構應用程式)*

### <a name="home-scale"></a>首頁規模

3D 應用程式啟動器會存留在 Cliff 房屋中, 而其預設大小應該與空間中的其他「實體」物件有意義。 如果您將啟動器放在旁邊 (例如, 房屋工廠或某些傢俱), 它應該會在家裡, 以大小為依據。 最好的起點是查看它看起來是30個立方的角度, 但請記住, 使用者可以視需要相應增加或減少。

### <a name="own-able"></a>擁有能力

應用程式啟動器應該會像是使用者在其空間中可能很高興的物件。 它們幾乎都是在這些專案的周圍, 因此啟動器應該會像是使用者認為有足夠的東西來尋求和保持鄰近。

![實例Astro 扭曲3D 應用程式啟動器](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Astro 扭曲3D 應用程式啟動器範例 (虛構應用程式)*

### <a name="recognizable"></a>辨識

您的3D 應用程式啟動器應該會立即將「您的應用程式品牌」表示為看到它的人員。 如果您的應用程式中有星號字元或特別可識別的物件, 我們建議您將其當做設計的一個重要部分使用。 在混合現實世界中, 物件對使用者的興趣會比僅限標誌更有趣。 可辨識的物件可快速且清楚地傳達品牌。

### <a name="volumetric"></a>體積型

您的應用程式所需的不僅僅是將您的標誌放在平面上, 並一天呼叫它。 您的啟動器應該會像是使用者空間中令人興奮的3D 實體物件。 理想的方法是假設您的應用程式在 Macy 的感恩節日行列中會有一個氣球。 問自己, 究竟是什麼人會碰到街道的問題呢？ 所有的觀賞角度看起來很棒嗎？


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>良好3D 模型的秘訣

### <a name="best-practices"></a>最佳作法
* 在規劃應用程式啟動器的維度時, 大約會針對 30cm cube 進行排除。 因此, 1:1:1 的大小比例。
* 模型必須低於10000個多邊形。 [深入瞭解三角形計數和詳細資料層級 (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 盡可能在沉浸式耳機上測試。
* 盡可能將詳細資料組建到模型的幾何中–不依賴材質以取得詳細資料。
* 建立「水緊密」封閉的幾何。 沒有任何在中模型化的漏洞。
* 在您的物件中使用自然材質。 想像一下在現實世界裡製作它。
* 請確定您的模型會以不同的距離和大小來妥善閱讀。
* 當您的模型準備就緒時, 請閱讀[匯出資產指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。

![材質中包含細微詳細資料的模型](images/20171013-143334-mixedreality-640px.jpg)<br>
*材質中包含細微詳細資料的模型*

### <a name="what-to-avoid"></a>應避免的事項
* 請勿使用高對比的詳細資料或小型、忙碌的模式和紋理。
* 不要使用精簡型幾何–它不會在某個距離運作良好, 而且別名會不正確。
* 不要讓模型的部分延伸太多超過1:1:1 的大小比例。 它會建立調整問題。

![避免高對比的小型忙碌模式](images/20171013-143603-mixedreality-640px.jpg)<br>
*避免高對比、小型、忙碌模式*

## <a name="how-to-handle-type"></a>如何處理類型

### <a name="best-practices"></a>最佳作法
* 我們建議您的類型包含應用程式啟動器 (或更多) 的1/3。 「類型」 (Type) 主要是讓人們知道您的啟動器實際上是啟動器, 因此如果非常重要, 就很好用。
* 避免讓類型變寬–請嘗試將它保留在應用程式啟動器核心維度的範圍內 (更多或更少)。
* 一般類型可以工作, 但請注意, 在某些環境中可能難以從特定角度進行觀看。 您可以考慮將它放在其背後的實心物件或背景, 以協助解決此情況。
* 將維度加入至您的類型會在3D 中感覺良好。 網底: 類型的兩側不同, 較暗的色彩有助於閱讀。


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


**輸入可使用的色彩**
* 白皮書
* 黑色
* 明亮的半形色彩

![輸入可使用的色彩。](images/20171016-112111-mixedreality-640px.jpg)<br>
*輸入可使用的色彩*

### <a name="what-to-avoid"></a>應避免的事項

**輸入造成問題的色彩**
* 中間色調
* 灰色
* 過度飽和色彩或 desaturated 色彩

![輸入造成問題的色彩。](images/20171016-112246-mixedreality-640px.jpg)<br>
*輸入造成問題的色彩*

## <a name="lighting"></a>光源

應用程式啟動器的光源來自 Cliff 房屋環境。 請務必在房屋的幾個地方測試您的啟動程式, 使其在光線和陰影中都看起來很好。 好消息是, 如果您已依照本檔中的其他設計指引進行, 則您的啟動器應該會針對 Cliff 房屋中的大部分光源提供良好的圖形。

測試啟動程式如何在環境中查看各種光線的好地方, 就是 Studio、媒體聊天室、Patio 內外的任何位置 (具有草地的具體區域)。 另一個良好的測試是將它放在半淺色和半陰影, 看看它的外觀。

![請確定您的啟動器在光線和陰影中都看起來良好。](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*請確定您的啟動器在光線和陰影中都看起來良好*

## <a name="texturing"></a>繪製

### <a name="authoring-your-textures"></a>撰寫您的紋理

3D 應用程式啟動器的結束格式會是 glb 檔案, 這是使用 .PBR (實際轉譯) 管線所建立的。 這可能是一種棘手的程式, 如果您還沒這麼做, 現在是採用技術演出者的好時機。 如果您是美麗 DIY-er, 請花時間[研究並學習 .pbr 術語](http://wiki.polycount.com/wiki/PBR), 而在您開始之前, 將會協助您避免常見的錯誤。 

![實例全新便箋應用程式](images/pbr-freshnote1-640px-500px.png)<br>
*最新附注3D 應用程式啟動器範例 (虛構應用程式)*

**建議的 authoring tool**

我們建議使用 Allegorithmic 的[物質刷](https://www.allegorithmic.com/products/substance-painter)來撰寫您的最終檔案。 如果您不熟悉在「物質刷」中撰寫「.PBR 著色器」, 以下是一個[教學](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)課程。

(或者, 如果您比較熟悉其中一個, 則[Coat](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)或[Marmoset Toolbag](https://www.marmoset.co/toolbag/)也適用)。

### <a name="best-practices"></a>最佳作法

* 如果您的應用程式啟動器物件是針對 .PBR 所撰寫, 則將它轉換為 Cliff 房屋環境應該相當簡單。
* 我們的著色器預期是金屬/粗糙度工作流程– Unreal 的 .PBR 著色器是一個靠近的傳真。
* 匯出材質時, 請記住[建議的材質大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)。
* 請務必建立即時光源的物件, 這表示:
    * 避免內建陰影-或繪製陰影
    * 避免在材質中內建光源
    * 使用其中一個 .PBR 材質撰寫套件來取得為著色器產生的正確對應

## <a name="see-also"></a>另請參閱

* [建立要在混合現實首頁中使用的3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [實作 3D 應用程式啟動器 (UWP 應用程式)](implementing-3d-app-launchers.md)
* [實作 3D 應用程式啟動器 (Win32 應用程式)](implementing-3d-app-launchers-win32.md)
