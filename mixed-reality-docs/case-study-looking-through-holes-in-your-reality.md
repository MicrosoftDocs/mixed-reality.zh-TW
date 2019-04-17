---
title: 案例研究-仔細檢查您實際上的漏洞
description: 此案例研究將說明如何實作 HoloLens，讓使用者看到背後牆、 樓層、 下，並在其實際環境中的虛擬網站上的 「 magic 視窗 」 效果。
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens magic 的視窗中，視差
ms.openlocfilehash: 0c0828a6ebbefdcff7f0a66f48469007c5c532df
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592112"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>案例研究-仔細檢查您實際上的漏洞

當人們考慮混合的實境，以及他們可以如何使用 Microsoft HoloLens 時，它們通常是堅持問題像是 「 哪些物件新增至我的房間 」？ 或者 「 什麼可以我在我的空間上嗎？ 」 我想要反白顯示您可以考慮的另一個區域 — 基本上是一個神奇的技巧，來查詢或透過真實的實體物件都使用相同的技術。

## <a name="the-tech"></a>技術

如果您已得力外星人，因為它們可能會中斷在您壁 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**，解除鎖定在安全的背景牆**[片段](case-study-creating-an-immersive-experience-in-fragments.md)**，或已幸運若要查看在 UNSC 無限大機庫 **[E3 2015 Halo 5 體驗](https://www.youtube.com/watch?v=QDw5QjDtFy8)**，則您已了解正是我要討論。 根據您的想像力，此 visual 的技巧可以用在您泥中放入暫存的漏洞，或隱藏在鬆散的 floorboard 的世界。

![RoboRaid 加入三維的管道和後置您的背景牆，只能透過建立為 invaders 突破的漏洞來顯示其他結構。](images/roboraid-640px.png)

RoboRaid 加入三維的管道和後置您的背景牆，只能透過建立為 invaders 突破的漏洞來顯示其他結構。

您可以使用其中一個這些唯一全像投影 HoloLens 上，應用程式可以提供深度的內容，您的背景牆後方，或透過您 floor 方式相同，但實際上會透過實際的視窗。 自行保留，移動，您可以看到任何位於右邊。 越來越接近，以及您可以看到更多的所有項目。 主要差異是，實際的漏洞可讓您透過，而您 floor stubbornly 不會讓您透過爬該神奇的全像攝影版內容。 （我會將工作加入待處理項目）。

## <a name="behind-the-scenes"></a>幕後

這個訣竅是兩個效果的組合。 首先，全像攝影版的內容已釘選到全球使用 「 空間錨點 」。 若要讓該內容 「 世界鎖定 」 使用錨點表示，您要尋找在不以視覺化方式漂移離開實體的物件附近，即使在您移動或基礎的空間的對應系統更新您的聊天室其 3D 模型。

其次，該全像攝影版的內容會以視覺化方式限制非常特定的空間，讓您可以只看到透過漏洞，您實際上。 該阻擋是為了需要仔細檢查邏輯漏洞、 視窗或門口，銷售的技巧。 沒有什麼東西可以封鎖大部分的檢視，裂縫祕密的侏維度空間中，可能只是看起來像不當放置的恐龍。

![這不是實際的螢幕擷取畫面，但舉例說明如何在 HoloLens 從 MR 基本概念 101 祕密地底世界的樣子。 黑色的機箱未顯示，但您可以看到透過虛擬的洞裡的內容。 （透過實際的裝置時，最低限度值似乎因為眼睛的重點放在進一步的距離，如果找不到甚至更會消失。）](images/origamiholecomposited-640px.png)

這不是實際的螢幕擷取畫面，而圖如何從祕密地底世界[MR 基本概念 101](holograms-101.md) HoloLens 上看起來。 黑色的機箱未顯示，但您可以看到透過虛擬的洞裡的內容。 （透過實際的裝置時，最低限度值似乎因為眼睛的重點放在進一步的距離，如果找不到甚至更會消失。）

### <a name="world-locking-holographic-content"></a>世界鎖定全像攝影版的內容

在 Unity 中，造成保持世界鎖定全像攝影版的內容是簡單，只要新增 WorldAnchor 元件：

```
myObject.AddComponent<WorldAnchor>();
```

WorldAnchor 元件將會調整的位置和輪替其 GameObject （和任何其他在該階層中的物件項目） 保持穩定，相對於實體物件附近。 當製作您的內容，則會建立物件的 [根] 樞紐，在這個虛擬漏洞置中對齊的方式。 （牆上的深度，物件的樞紐分析時，其位置和旋轉的稍微調整會更明顯，而且漏洞不可能看起來非常穩定）。

### <a name="occluding-everything-but-the-virtual-hole"></a>Occluding 以外的虛擬的漏洞

有各種不同的方式，選擇性地封鎖項目是隱藏在您的背景牆檢視。 最簡單的一個利用 HoloLens 使用加法類的顯示，這表示全黑的物件會顯示不可見的事實。 您可以在 Unity 中而不進行任何特殊的著色器或材質的訣竅，只要建立黑色的資料，並將它指派給您的內容中的物件。 如果您不想要執行 3D 模型，只要使用少數幾個四組數字的預設物件，並稍微重疊它們。 有一些缺點，這種作法是最快的方法來取得完全運作，但取得低精確度的使用概念證明很棒，，即使您懷疑您可能想要稍後再加以重構。

上述的 「 黑箱 」 方法的一大缺點是不好拍攝。 效果看起來的 HoloLens 顯示透過完美的您採取任何螢幕擷取畫面會顯示黑色的大型物件，而非剩下的塗鴉牆或樓層。 原因是，但實際上與實體硬體和螢幕擷取畫面複合全像投影以不同的方式。 讓我們到一些假的數學繞道一下...

*假的數學警示 ！這些數字和公式是為了說明的點，不為任何類型的精確的公制 ！*

您看到透過 HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

您看到螢幕擷取畫面和影片中：

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

以英文：您透過 HoloLens 所看到的內容是簡單的組合變暗的事實 （如同透過太陽眼鏡） 和任何應用程式想要顯示全像投影。 但當您的螢幕擷取畫面，相機的映像會與應用程式的全像投影的每一像素透明度值根據混合。

若要解決這個問題的一個方式是變更，只寫入深度緩衝區，並與所有其他不透明資料排序的 「 黑箱作業 」 資料。 如這個範例，請參閱[MixedRealityToolkit 在 GitHub 上的 WindowOcclusion.shader 檔案](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)。 這裡複製相關的行：

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(請注意 「 位移 50，100"一行是應付不相關的問題，因此它可能有道理，省略。)

實作不可見的阻擋物材料，可讓您繪製的方塊，看起來是正確和混合實境螢幕擷取畫面中顯示的應用程式。 變本加厲，您可以試著改善效能的進一步延伸該方塊 clever 凡事繪製更少看不見的像素，但可以講一下檢討，通常不是必要。

![以下是從 MR 基本概念 101 祕密地底世界，因為 Unity 繪製它，除了 occluding 方塊的外部組件。 請注意，底世界的樞紐中央的方塊中，可協助保留漏洞相對於實際的 floor，盡可能穩定。](images/underworld-occluded-640px.png)

以下是從祕密地底世界[MR 基本概念 101](holograms-101.md)如 Unity 繪製它，除了 occluding 方塊的外部組件。 請注意，底世界的樞紐中央的方塊中，可協助保留漏洞相對於實際的 floor，盡可能穩定。

## <a name="do-it-yourself"></a>自行進行此作業

有 HoloLens 和想要自行試用效果？ 您可以執行 （不需要撰寫程式碼） 的最簡單件事是要安裝免費的 3D 檢視器應用程式，然後載入[我提供了在 GitHub 的下載 the.fbx 檔案](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow)檢視花卉 pot 模型，在您的房間。 HoloLens，將其載入，您可以看到工作的假象。 當您準備模型之前時，您只能看到到小的漏洞，其他所有項目不會察覺。 查看模型，從任何另一端，它完全消失。 使用移動、 旋轉和調整控制項的 3D 檢視器來放置虛擬洞，針對任何垂直的介面，您可以將產生一些想法 ！

![在 Unity 編輯器中檢視此模型會顯示圍繞 flowerpot 大型黑色方塊。 HoloLens，在方塊就會消失，讓 magic 視窗效果的方法。](images/magicwindowflowerpotineditor.png)

在 Unity 編輯器中檢視此模型會顯示圍繞 flowerpot 大型黑色方塊。 HoloLens，在方塊就會消失，讓 magic 視窗效果的方法。

如果您想要建置使用這項技術的應用程式，請參閱[MR 基本概念 101 教學課程](holograms-101.md)中[混合實境 Academy](academy.md)。 第 7 章結尾中會顯示隱藏的底世界 （如上面圖所示） 您 floor 遽增。 誰說教學課程必須無聊？

以下是一些概念的您可以採取這個想法下一步:
* 將可讓內容內的虛擬的洞裡互動式方法。 讓使用者有一些影響超過其牆真的能夠改進難怪這個技巧可提供的意義。
* 將方法可以查看透過回到已知的區域物件。 比方說，可以將全像攝影版的洞裡放在您的咖啡資料表及檢視的方式下的您 floor 嗎？

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>資深軟體工程師 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [MR 101 基本知識：完整的專案，與裝置](holograms-101.md)
* [座標系統](coordinate-systems.md)
* [空間的錨點](spatial-anchors.md)
* [空間對應](spatial-mapping.md)
