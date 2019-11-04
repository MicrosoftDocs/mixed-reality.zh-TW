---
title: 案例研究-在混合現實中建立 galaxy
description: 在 Microsoft HoloLens 推出之前，我們會要求開發人員小組想要看到新裝置有經驗的內部團隊組建。 分享超過5000的想法，在24小時的 Twitter 輪詢之後，獲勝者就是所謂的「Galaxy Explorer」的想法。
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer、HoloLens、Windows Mixed Reality、分享您的想法、個案研究
ms.openlocfilehash: 696662eb92371708389f8a128dcee6a61acf1816
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436866"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>案例研究-在混合現實中建立 galaxy

在 Microsoft HoloLens 推出之前，我們會要求開發人員小組想要看到新裝置有經驗的內部團隊組建。 分享超過5000的想法，在24小時的 Twitter 輪詢之後，獲勝者就是一個稱為「 [Galaxy Explorer](galaxy-explorer.md)」的概念。

Zibits，這是專案的 Karim Luccin，這是團隊的圖形工程師，談到在「Galaxy Explorer」中建立銀河方式的精確、互動標記法的美工和工程之間的共同作業。

## <a name="the-tech"></a>技術

[我們的團隊](galaxy-explorer.md#meet-the-team)由兩個設計師組成，三名開發人員、四個演出者、生產者和一個測試人員，建立功能完整的應用程式，讓人們能夠瞭解及探索銀河方式 Galaxy 的 vastness 和美。

我們想要充分利用 HoloLens 在您的生活空間中直接轉譯3D 物件的能力，所以我們決定要建立一個逼真的外觀，讓使用者能夠放大並查看個別的星星，每個都在自己的軌跡上.

在第一周的開發過程中，我們提供了一些目標，讓我們以銀河的方式呈現 Galaxy：它必須有深度、移動和感覺體積型，這是一項可協助建立 Galaxy 圖形的完整星星。

建立具有數十億顆星的動畫 galaxy 的問題是，需要更新的大量單一元素會太大而無法讓 HoloLens 以動畫使用 CPU。 我們的解決方案牽涉到複雜的藝術與科學混合。

## <a name="behind-the-scenes"></a>幕後

為了讓人們能夠探索個別的星星，我們的第一步就是要找出一次可以轉譯多少個粒子。

### <a name="rendering-particles"></a>呈現微粒

目前的 Cpu 非常適合用來一次處理序列工作和多個平行工作（取決於它們有多少核心），但是 Gpu 在以平行方式處理數以千計的作業時更有效率。 不過，因為它們通常不會與 CPU 共用相同的記憶體，所以在 CPU < > GPU 之間交換資料可能很快就會成為瓶頸。 我們的解決方案是在 GPU 上建立一個 galaxy，而且必須完全在 GPU 上運作。

我們在各種模式中開始使用數千個點粒子的壓力測試。 如此一來，我們就可以在 HoloLens 上取得 galaxy，以查看有哪些功能和功能。

### <a name="creating-the-position-of-the-stars"></a>建立星星的位置

我們的其中一個小組成員已撰寫程式C#代碼，它會在其初始位置產生星星。 星星位於橢圓形，而且其位置可以由（**curveOffset**， **ellipseSize**，提高**許可權**）描述，其中**curveOffset**是星形沿著橢圓形的角度， **ellipseSize**是橢圓形的維度沿著 X 和 Z，並提高 galaxy 內適當的星號提升許可權。 因此，我們可以建立一個緩衝區（[Unity 的 ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)），它會使用每個星型屬性進行初始化，並在 GPU 上將它傳送給其餘的經驗。 為了繪製這個緩衝區，我們使用[Unity 的 DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) ，允許在任意一組點上執行著色器（GPU 上的程式碼），而不需要實際的網格來表示 galaxy：

**使用率**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

我們從具有數千個粒子的原始迴圈模式開始。 如此一來，我們所需的證明就是我們可以管理許多粒子，並以高效能的速度執行它，但我們並不滿意 galaxy 的整體塑造。 為了改善此圖形，我們嘗試了各種不同的模式和物件系統旋轉。 這一開始是有希望的，因為微粒和效能的數目維持一致，但圖形接近中央，而星星發出外表，這並不實際。 我們需要一個可讓我們操控時間並讓微粒實際移動的發射，這會更接近 galaxy 的中心。

![我們嘗試了各種旋轉的模式和物件系統，就像這樣。](images/galaxy-patterns-500px.png)

我們嘗試了各種旋轉的模式和物件系統，就像這樣。

我們的團隊進行了 galaxies 函式的一些研究，我們為 galaxy 建立了自訂的物件系統，讓我們可以根據「[密度波理論](https://en.wikipedia.org/wiki/Density_wave_theory)」來移動省略號上的微粒，這 theorizes 了 galaxy 的臂密度較高，但在固定的 flux 中，就像流量卡紙一樣。 它看起來穩定又穩固，但星形在沿著其各自的橢圓形移動時，實際上會移入和移出臂。 在我們的系統中，粒子永遠不會存在於 CPU 上—我們會產生卡片並在 GPU 上調整其方向，因此整個系統只是初始狀態 + 時間。 它的進展如下：

![具有 GPU 轉譯之物件的進展](images/spiral-galaxy-arms-500px.jpg)

具有 GPU 轉譯之物件的進展


加入足夠的省略號並設定為旋轉之後，galaxies 就會開始形成「臂」，其中星形的移動會融合在其中。 沿著每個橢圓形路徑的星星間距會被賦予一些隨機性，而且每顆星都會加上一點的位置隨機性。 這建立了更自然的星型移動和 arm 圖形分佈。 最後，我們新增了以中央的距離為基礎來驅動色彩的功能。

### <a name="creating-the-motion-of-the-stars"></a>建立星星的動作

若要建立一般星形動作的動畫，我們必須為每個框架新增一個常數角度，並以常數星形速度沿著橢圓形移動。 這是使用**curveOffset**的主要原因。 這在技術上並不正確，因為星星會沿著橢圓形的長邊更快速地移動，但一般動作會覺得良好。

![星星以較長的弧線更快移動，邊緣的速度較慢。](images/ellipse-movement.jpg)

星星以較長的弧線更快移動，邊緣的速度較慢。


如此一來，每顆星都是由（**curveOffset**， **ellipseSize**，提高**許可權**，**年齡**）完整描述，其中**Age**是從載入場景以來已過的總時間累計。




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

如此一來，我們就可以在應用程式開始時產生數萬顆星一次，然後沿著建立的曲線，以動畫顯示一組挑的星星。 因為所有專案都是在 GPU 上，所以系統可以將所有星形以平行方式繪製，而不會對 CPU 進行任何成本。

![以下是繪製白色四邊形時的外觀。](images/drawing-white-quads-300px.jpg)

以下是繪製白色四邊形時的外觀。



為了讓每個四顆人都成為攝影機，我們使用幾何著色器，將每個星形位置轉換成螢幕上的2D 矩形，其中將包含星形材質。

![菱形，而不是四邊形。](images/drawing-white-quads-300px.jpg)

菱形，而不是四邊形。


因為我們想要限制過度繪製（圖元的處理次數）越多越好，我們就會將四邊形旋轉，讓它們的重迭較少。

### <a name="adding-clouds"></a>新增雲端

有許多方法可讓您使用體積型感受，從磁片區內的光線 marching，到盡可能繪製最多的粒子來模擬雲端。 即時光線 marching 的成本太高且難以撰寫，所以我們先嘗試使用在遊戲中轉譯樹系的方法來建立一個冒名頂替系統，其中包含許多與相機相關的2D 影像。 當我們在遊戲中進行這項操作時，我們可以從相機呈現的材質會旋轉、儲存所有影像，並在執行時間為每個佈告欄卡片選取符合視圖方向的影像。 這在影像是全像投影時也沒有作用。 左邊眼和適當眼睛之間的差異，讓我們需要更高的解析度，或只是看起來像是平面、失真或重複。

在第二次嘗試時，我們試著盡可能多的粒子。 當我們 additively 已繪製的微粒，並將其新增到場景之前，已達到最佳視覺效果。 這種方法的典型問題，是關於我們可以在一次繪製多少個粒子，以及它們在維護60fps 時所涵蓋的畫面區域數量。 將產生的影像模糊以取得此雲端感覺，通常是相當耗費成本的作業。

![如果沒有材質，這就是雲端看起來有2% 不透明度的樣子。](images/clouds-without-texture-300px.jpg)

如果沒有材質，這就是雲端看起來有2% 不透明度的樣子。



加總並擁有許多，表示我們會在彼此上有數個四邊形，並重複著色相同的圖元。 在 galaxy 的中心，相同的圖元會在彼此上有數百個四邊形，而這在全螢幕完成時有相當大的成本。

執行全螢幕雲端並嘗試將它們模糊會是個不錯的主意，所以我們決定讓硬體為我們執行工作。

### <a name="a-bit-of-context-first"></a>第一個內容

在遊戲中使用材質時，材質大小很少會符合我們想要在其中使用的區域，但我們可以使用不同類型的紋理篩選來取得圖形配接器，以從材質圖元（[紋理篩選](https://msdn.microsoft.com/library/dn642451.aspx)）中插入我們想要的色彩。 對我們感興趣的篩選是[雙線性篩選](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)，會使用4個最接近的鄰近專案來計算任何圖元的值。

![篩選之前的原始](images/texture-1.png)

![篩選後的結果](images/texture-2.png)

使用此屬性時，我們會看到每次嘗試在區域中繪製材質兩次大時，會模糊結果。

我們不會轉譯成全螢幕，而是遺失這些珍貴的毫秒，而是會轉譯成較小的螢幕版本。 然後，藉由複製此材質並以2個因數來延展，我們會回到全螢幕，同時模糊處理常式中的內容。

![x3 升級回到完整解析度。](images/galaxy-resolutions-300px.png)

x3 升級回到完整解析度。



這讓我們只需要一小部分的原始成本，就能取得雲端元件。 我們不會在完整解析度上新增雲端，而是只繪製 1/第64次圖元，而只是將材質延展回完整解析度。

![Left，升級從 1/8 到完整解析;和 right，使用2的乘冪3升級。](images/stars-upscaled-300px.jpg)

Left，升級從 1/8 到完整解析;和 right，使用2的乘冪3升級。


請注意，嘗試從大小的 1/第64次到完整大小的外觀看起來完全不同，因為在我們的設定中，圖形配接器仍然會使用4個圖元來為較大的區域加上陰影，而成品會開始出現。

然後，如果我們以較小的卡片新增完整解析星星，我們會取得完整的 galaxy：

![使用完整解析星形的 galaxy 轉譯接近最終結果](images/full-galaxy-500px.png)

隨著圖形的追蹤，我們新增了一層雲端，並以我們在 Photoshop 中繪製的臨時點交換，並新增一些額外的色彩。 結果是銀河的，Galaxy 我們的美工和工程團隊都覺得很好用，而且它達到了深度、音量和運動的目標—全都不會造成 CPU 的負擔。

![在3D 中，我們最終的銀河方式為 Galaxy。](images/final-galaxy-500px.jpg)

在3D 中，我們最終的銀河方式為 Galaxy。


### <a name="more-to-explore"></a>深入探索

我們開啟了適用于 Galaxy Explorer 應用程式的程式碼，並將其提供給[GitHub](https://github.com/Microsoft/GalaxyExplorer) ，供開發人員建立。

有興趣尋找更多有關 [Galaxy Explorer] 開發流程的資訊嗎？ 查看[Microsoft HoloLens YouTube 頻道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)上所有過去的專案更新。

## <a name="about-the-authors"></a>關於作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b>是一種軟體工程師和別致的視覺效果愛好者。 他是適用于 Galaxy Explorer 的圖形工程師。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Zibits</b>是一位藝術的組長和空間愛好者，負責管理適用于 Galaxy Explorer 的3d 模型化小組，並無法駕馭更多的粒子。</td>
</tr>
</table>


## <a name="see-also"></a>請參閱
* [GitHub 上的 Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer)
* [YouTube 上的 Galaxy Explorer 專案更新](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
