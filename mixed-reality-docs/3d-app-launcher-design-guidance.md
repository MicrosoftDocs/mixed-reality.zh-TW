---
title: 3D 應用程式啟動程式的設計指引
description: 3D 應用程式啟動程式是一個 「 實體 」 的物件，他們可以選取的啟動應用程式的使用者的混合的實境房子。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計、 3D 應用程式啟動程式、 沈浸式耳機、 即時的 cube
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591328"
---
# <a name="3d-app-launcher-design-guidance"></a>3D 應用程式啟動程式的設計指引

當您將在 Windows Mixed Reality 沈浸式 (VR) 耳機時，您可以輸入家中的 Windows Mixed Reality 視覺化為房屋下懸崖住山脈與水 (雖然您可以[選擇其他環境，甚至建立您自己](add-custom-home-environments.md)). 這個空間內首頁，使用者可以自由排列及組織的 3D 物件和他們很關心它們想要的任何方式的應用程式。 A **3D 應用程式啟動器**是在使用者的 「 實體 」 物件的混合實境房子，他們可以選取的啟動應用程式。

![範例：浮動 Bird 3D 應用程式啟動器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*浮動 Bird 3D 應用程式啟動器範例 （虛構應用程式）*

## <a name="3d-app-launcher-creation-process"></a>3D 應用程式啟動器建立程序

有 3 個步驟以建立 3D 應用程式啟動程式：
1. 設計和 concepting （本文）
2. [模型化和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 請將它整合到您的應用程式：
    * [UWP 應用程式](implementing-3d-app-launchers.md)
    * [Win32 應用程式](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>設計概念

### <a name="fantastic-yet-familiar"></a>超棒的但熟悉

您的應用程式啟動程式存在於 Windows Mixed Reality 環境是部分陌生，部分成冊/sci-fi。 最佳的啟動器會遵循這個世界的規則。 將如何從您的應用程式，採用熟悉的代表性物件，但東改西改的一些實際的現實的規則。 將會產生魔術。

### <a name="intuitive"></a>直覺式

當您查看您的應用程式啟動程式時，其用途-啟動您的應用程式-應該很明顯，而且不應該造成任何混淆。 比方說，是確定您的啟動程式是您的應用程式，它將不會混淆 decor Cliff 屋裡的一項明顯夠代表。 您的應用程式啟動程式應該邀請人觸控/選取它。

![範例：全新的附註 3D 應用程式啟動器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*全新的附註 3D 應用程式啟動器範例 （虛構應用程式）*

### <a name="home-scale"></a>主要刻度

3D 應用程式啟動器 live Cliff 屋裡，其預設大小應該意義與其他 「 實體 」 物件空間中。 如果您將您的啟動器，說，一家工廠或某些 furniture，應該會覺得在家裡、 size-wise。 若要查看其外觀在 30 三次方公分為單位，但請記住，使用者可以相應增加或相應減少是否他們想，是不錯的起點。

### <a name="own-able"></a>可擁有的

應用程式啟動程式應該感覺個人會也很高興在其空間中的物件。 他們將能幾乎周圍本身與這些項目，讓啟動器應該覺得喜歡使用者思考是想要找出並保留附近。

![範例：Astro Warp 3D 應用程式啟動器](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Astro Warp 3D 應用程式啟動器範例 （虛構應用程式）*

### <a name="recognizable"></a>可辨識

您的 3D 應用程式啟動程式應該立即 express 人看到 」 您的應用程式的品牌 」。 如果您有星號字元或特別識別的物件在您的應用程式中，我們建議使用其做為您的設計的很大一部份。 在混合的實境世界中，物件會比只單獨商標的使用者從連往更有意思。 可辨識物件通訊的品牌，快速且清楚地。

### <a name="volumetric"></a>體積型

您的應用程式值得使用更不只是一般的平面上放置您的標誌和呼叫一天。 您的啟動程式應該感覺上是令人興奮、 3D、 實體的物件，在使用者的空間中。 是不錯的方法是假設您的應用程式即將要 Macy 感恩節天行列中有一個球形文字說明。 問問自己，什麼會真的讚嘆的人員為其來源巷口？ 項目看起來很棒從頭到尾檢視？


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


## <a name="tips-for-good-3d-models"></a>良好的 3D 模型的秘訣

### <a name="best-practices"></a>最佳作法
* 在規劃您的應用程式啟動器的維度，限定大約 30 cm cube。 因此，1:1:1 大小比率。
* 模型必須是 10000 的多邊形。 [深入了解三角形計數和層級的詳細資料 (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 在盡可能沈浸式耳機上進行測試。
* 建置到您的模型幾何詳細資料，盡可能 – 不要依賴紋理的詳細資料。
* 建置"water 緊密 」 關閉幾何。 未設定模型中沒有安全漏洞。
* 使用自然的資料物件中。 想像一下製作真實世界中。
* 請確定您的模型讀取也在不同距離和大小。
* 準備好您的模型時，讀取[匯出資產指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。

![微妙的細節，材質中的模型](images/20171013-143334-mixedreality-640px.jpg)<br>
*微妙的細節，材質中的模型*

### <a name="what-to-avoid"></a>要避免的事項
* 請勿使用高對比詳細資料或小型的忙線中的模式和紋理。
* 請勿使用精簡型的幾何 – 不運作也在距離，並將別名格式錯誤。
* 不要讓擴充您的模型部分太多超過 1:1:1 大小比率。 它會建立縮放問題。

![避免高對比 」、 「 小忙線中的模式](images/20171013-143603-mixedreality-640px.jpg)<br>
*避免高對比、 小型、 忙碌中的模式*

## <a name="how-to-handle-type"></a>如何控制代碼類型

### <a name="best-practices"></a>最佳作法
* 我們建議您的型別包含大約 1/3 的應用程式啟動器 （或以上）。 類型為重點，讓人們可以您啟動器的是，事實上，啟動器，因此如果是很重大很不錯的主意。
* 避免進行非常廣泛的型別，請盡量保持它的應用程式啟動器的範圍內 core 維度 （增加或減少）。
* 一般型別可以運作，但請注意，它很難檢視從某些角度和在某些環境中。 您可以考慮將它置於實體物件或其可協助完成這背後的背景。
* 新增維度，以便您的型別覺得不錯 3D 中。 陰影的類型不同，較深的色彩可以降低了可讀性。


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


**工作的類型色彩**
* 白皮書
* 黑色
* 亮半飽和的色彩

![工作的類型色彩。](images/20171016-112111-mixedreality-640px.jpg)<br>
*工作的類型色彩*

### <a name="what-to-avoid"></a>要避免的事項

**造成麻煩的類型色彩**
* Mid 撥號音
* 灰色
* 過度飽和的色彩或已去色的色彩

![輸入造成麻煩的色彩。](images/20171016-112246-mixedreality-640px.jpg)<br>
*造成麻煩的類型色彩*

## <a name="lighting"></a>光源

您的應用程式啟動器的光源來自 Cliff 房屋環境。 請務必測試您的啟動程式在整個房子的幾個地方，讓它看起來沒問題中光線和陰影。 好消息是，如果您照著本文件中的其他設計指導方針，您的啟動程式應該相當良好 Cliff 屋裡大多數的光源。

若要測試您程式啟動器中環境中的各種燈的外觀良好是 Studio 媒體的空間，和上一步 」 高台 （使用草坪具體的區域） 上任何位置外。 另一個很好的測試，就是將它放在一半的光線和一半的陰影，並看看它的外觀。

![請確定您的啟動程式看起來不錯中光線和陰影。](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*請確定您的啟動程式看起來不錯中光線和陰影*

## <a name="texturing"></a>材質

### <a name="authoring-your-textures"></a>撰寫您的紋理

您的 3D 應用程式啟動器的結束格式會.glb 檔案，會使用 PBR （實際基礎轉譯） 管線。 這可以是複雜的程序-現在是採用技術的演出者，如果您還沒有這麼做的好時機。 如果您是勇敢 DIY-呃，花時間[研究，了解 PBR 術語](http://wiki.polycount.com/wiki/PBR)事情實際上在您開始前，將可協助您避免常見的錯誤。 

![範例：全新的注意應用程式](images/pbr-freshnote1-640px-500px.png)<br>
*全新的附註 3D 應用程式啟動器範例 （虛構應用程式）*

**建議撰寫工具**

我們建議您使用[物質複製](https://www.allegorithmic.com/products/substance-painter)由 Allegorithmic 來撰寫您的最後一個檔案。 如果您不熟悉撰寫在物質複製，這裡的 PBR 著色器[教學課程](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)。

(或者[3D Coat](https://3dcoat.com/home/)， [Quixel Suite 2](https://quixel.se/suite2/)，或[Marmoset Toolbag](https://www.marmoset.co/toolbag/)只有當您更熟悉其中一種，也可以運作。)

### <a name="best-practices"></a>最佳作法

* 如果您的應用程式啟動程式物件所撰寫的 PBR，它應該是將它轉換為 Cliff 房屋環境很簡單。
* 我們的著色器所預期的 Metal/粗糙度工作流程 – Unreal PBR 著色器是關閉的傳真。
* 當匯出您的紋理保持[建議的紋理大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)記住。
* 務必先建置您即時的光線的物件，這表示：
    * 避免烤的 shadows – 或繪製的陰影
    * 避免烤的光源的紋理中
    * 使用其中一種撰寫套件 PBR 資料以取得正確的對應產生我們的著色器

## <a name="see-also"></a>另請參閱

* [在首頁的混合實境中建立使用 3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [實作 3D 應用程式啟動器 (UWP app)](implementing-3d-app-launchers.md)
* [實作 3D 應用程式啟動器 （Win32 應用程式）](implementing-3d-app-launchers-win32.md)
