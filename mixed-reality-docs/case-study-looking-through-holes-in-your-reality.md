---
title: 個案研究-查看您現實中的漏洞
description: 此案例研究會說明如何在 HoloLens 上執行「魔術 window」的效果，讓使用者可以在背景牆後方、樓層下，以及在其實際環境內的虛擬空缺中查看。
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、魔術 window、視差
ms.openlocfilehash: c829656c98b7c87f8b969dbbd16115f6a0bbaf27
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278146"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>個案研究-查看您現實中的漏洞

當人們思考混合現實以及他們可以如何處理 Microsoft HoloLens 時，他們通常會問到「我可以將哪些物件新增到我的房間？」之類的問題。 或是「我可以在我的空間上分層？」 我想要強調另一個您可以考慮的地方—基本上是一種神奇的技巧，也就是使用相同的技術來查詢您的實際實體物件。

## <a name="the-tech"></a>技術

如果您已無法駕馭外星人，因為它們在 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 中分解了您的牆、在 **[片段](case-study-creating-an-immersive-experience-in-fragments.md)** 中解除鎖定牆上的安全，或幸運的是要在 **[2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 中的 hangar 上查看 UNSC 無限大，那麼您已經看過我所說的內容。 根據您的想像，這個視覺技巧可以用來在您的飾面上放置暫時的洞，或在鬆散的 floorboard 下隱藏世界。

![RoboRaid 會在您的牆後方新增三維管道和其他結構，只會透過太空入侵者中斷時所建立的漏洞來顯示。](images/roboraid-640px.png)

RoboRaid 會在您的牆後方新增三維管道和其他結構，只會透過太空入侵者中斷時所建立的漏洞來顯示。

使用 HoloLens 上的其中一種獨特的全息影像，應用程式可以在您的牆後方或透過您的樓層提供內容的夢想，其方式與實際的視窗相同。 將自己往左移動，您可以看到右側有哪些內容。 深入瞭解，您可以看到更多專案。 主要的差別在於，真正的漏洞讓您能夠通過，而 floor 即時則不會讓您順向神奇全像攝影內容。 （我會在待處理專案中加入工作）。

## <a name="behind-the-scenes"></a>幕後

這個技巧是兩種效果的組合。 首先，使用「空間錨點」將全像攝影內容釘選到世界。 使用錨點讓該內容成為「世界鎖定」，表示您所要查看的不會以視覺化方式偏離其附近的實體物件，即使您移動或基礎空間對應系統更新其您房間的3D 模型。

其次，這種全像攝影內容會以視覺化方式限制在非常特定的空間，因此您只能在現實中看到整個洞。 這遮蔽是需要查看邏輯洞、視窗或閘口，以銷售訣竅的必要。 如果沒有封鎖大部分視圖的專案，密碼 Jurassic 維度的空間破解可能就會像是不良放置的恐龍。

![這不是實際的螢幕擷取畫面，而是從 MR 基本 101 underworld 密碼的說明如何查看 HoloLens。 黑色主機殼不會顯示，但您可以透過虛擬洞來查看內容。 （當您查看實際裝置時，地面似乎會消失，因為您的眼睛焦點會與其他距離一樣）。](images/origamiholecomposited-640px.png)

這不是實際的螢幕擷取畫面，而是從[MR 基本 101](holograms-101.md) underworld 密碼的說明如何查看 HoloLens。 黑色主機殼不會顯示，但您可以透過虛擬洞來查看內容。 （當您查看實際裝置時，地面似乎會消失，因為您的眼睛焦點會與其他距離一樣）。

### <a name="world-locking-holographic-content"></a>世界-鎖定全像攝影內容

在 Unity 中，使全像攝影內容保持世界鎖定狀態，就像新增 WorldAnchor 元件一樣簡單：

```
myObject.AddComponent<WorldAnchor>();
```

WorldAnchor 元件會持續調整其 GameObject 的位置和旋轉（也就是階層中該物件下的任何其他專案），使其相對於鄰近的實體物件保持穩定。 撰寫您的內容時，請以您物件的根 pivot 在此虛擬洞置中的方式建立。 （如果物件的樞紐分析表在牆中是深度的，其位置和旋轉的輕微調整會更明顯，而且洞的外觀可能不穩定）。

### <a name="occluding-everything-but-the-virtual-hole"></a>Occluding 虛擬洞以外的所有專案

有多種方式可以選擇性地封鎖您的牆中隱藏的視圖。 最簡單的方法是讓 HoloLens 使用加法顯示，這表示完全黑色的物件看起來不可見。 您可以在 Unity 中執行這項操作，而不需要進行任何特殊的著色器或材質訣竅，只要建立黑色材質，並將其指派給內容中的物件即可。 如果您不喜歡進行3D 模型化，只要使用幾個預設的四個物件，並稍微重迭它們就可以了。 這種方法有幾個缺點，但它是讓工作正常運作的最快方式，而且即使您懷疑稍後可能會想要重構，也是很好的概念證明。

上述「黑色箱」方法的一個主要缺點是，它不會有很好的相片。 雖然您的效果可能會透過 HoloLens 的顯示結果，但您所採取的任何螢幕擷取畫面都會顯示大型黑色物件，而不是剩餘的牆或樓層。 這是因為實體硬體和螢幕擷取畫面會以不同的方式來複合全息影像和現實。 讓我們繞道一下一些假的數學運算 。

*假的數學警示！這些數位和公式的目的是要說明一點，而不是任何精確的度量！*

您可以透過 HoloLens 看到的內容：

```
( Reality * darkening_amount ) + Holograms
```

您在螢幕擷取畫面和影片中看到的內容：

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

英文：您透過 HoloLens 看到的內容是簡單的事實（例如透過太陽眼鏡）和應用程式想要顯示的任何全息影像組合。 但是當您拍攝螢幕擷取畫面時，相機的影像會根據每個圖元的透明度值，與應用程式的全息片混合。

解決這個情況的方法之一，就是將「黑色方塊」材質改成隻寫入深度緩衝區，然後再以所有其他不透明的資料進行排序。 如需這種情況的範例，請查看[GitHub 上 MixedRealityToolkit 中的 WindowOcclusion。](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader) 相關行會複製到此處：

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

（請注意，「Offset 50，100」這一行是用來處理不相關的問題，因此可能有道理）。

執行類似的不可見遮蔽資料，可讓您的應用程式繪製在顯示器和混合現實螢幕擷取畫面中看起來正確的方塊。 對於額外的點數，您可以試著改善該方塊的效能，方法是執行聰明的作業來繪製較少的不可見圖元，但這實際上可以進入直搗黃龍，而且通常不是必要的。

![以下是來自 MR 基本101的秘密 underworld，因為 Unity 會進行繪製，但 [occluding] 方塊的外部部分除外。 請注意，underworld 的 pivot 位於方塊的中央，這有助於讓孔相對於您實際的樓層保持穩定。](images/underworld-occluded-640px.png)

以下是來自[MR 基本 101](holograms-101.md)的秘密 underworld，因為 Unity 會進行繪製，但 [occluding] 方塊的外部部分除外。 請注意，underworld 的 pivot 位於方塊的中央，這有助於讓孔相對於您實際的樓層保持穩定。

## <a name="do-it-yourself"></a>自行執行

有 HoloLens，想要自行嘗試效果嗎？ 最簡單的方法就是安裝免費的3D 檢視器應用程式，然後載入[我在 GitHub 上提供的 fbx](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow)檔案，以在您的房間內查看花卉模型。 在 HoloLens 上載入它，您就可以查看工作中的假像。 當您在模型前方時，您只會看到小洞，其他所有專案則不可見。 從任何其他端查看模型，它會完全消失。 使用3D 檢視器的 [移動]、[旋轉] 和 [調整] 控制項，將虛擬洞放在您可以想要產生一些想法的任何垂直表面上！

![在 Unity 編輯器中查看此模型會在 flowerpot 周圍顯示一個大型的黑色方塊。 在 HoloLens 上，此方塊會消失，使其成為魔術視窗效果的方式。](images/magicwindowflowerpotineditor.png)

在 Unity 編輯器中查看此模型會在 flowerpot 周圍顯示一個大型的黑色方塊。 在 HoloLens 上，此方塊會消失，使其成為魔術視窗效果的方式。

如果您想要建立使用這項技術的應用程式，請參閱[混合現實教學](tutorials.md)課程中的[MR 基本概念101教學](holograms-101.md)課程。 第7章結束于您的樓層中，會顯示隱藏的 underworld （如上圖所示）。 誰說過教學課程必須是乏味的？

以下是您在下一步可以採取此想法的一些概念：
* 將虛擬洞內的內容視為互動的方式。 讓您的使用者在其背景上有一些影響，實際上可以改善這項技巧可以提供的意義。
* 想辦法將物件查看到已知區域。 例如，您要如何在咖啡表中放入全像平面，並查看其底下的樓層？

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>資深軟體工程師 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [MR 基本概念101：使用裝置完成專案](holograms-101.md)
* [座標系統](coordinate-systems.md)
* [空間錨點](spatial-anchors.md)
* [空間對應](spatial-mapping.md)
