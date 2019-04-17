---
title: 案例研究-在混合實境中建立 galaxy
description: Microsoft HoloLens 出貨之前，我們會要求開發人員社群，何種應用程式他們想要查看建立的新裝置的資深內部團隊集。 超過 5000 個概念所共用，因而 24 小時制 Twitter 輪詢之後, 得獎者了解稱為 「 Galaxy 總管 」。
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer、 HoloLens、 Windows Mixed Reality，分享您的想法，案例研究
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597018"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>案例研究-在混合實境中建立 galaxy

Microsoft HoloLens 出貨之前，我們會要求開發人員社群，何種應用程式他們想要查看建立的新裝置的資深內部團隊集。 超過 5000 個概念所共用，因而 24 小時制 Twitter 輪詢之後, 得獎者呼叫了解[Galaxy 總管](galaxy-explorer.md)。

Andy Zibits，圖案潛在客戶專案，並 Karim Luccin，小組的圖形工程師討論封面和 Milky 方式銀河系 Galaxy 總管 中的精確、 互動式表示建立的工程合作。

## <a name="the-tech"></a>技術

[我們的小組](galaxy-explorer.md#meet-the-team)-向上提出的兩個設計工具、 三位開發人員、 四個演出者、 產生者和一個測試人員，有六週建置功能完整的應用程式，這可讓人了解並探索 vastness 和我們 Milky 方式 Galaxy 優點。

我們想要充分利用 HoloLens 能夠呈現 3D 物件，直接在您居住的空間，因此我們決定我們想要建立實際尋找 galaxy 其中人員就能夠放大關閉並查看個別的星星，分別位於它們自己滴下.

在開發的第一週中，我們想出了幾項目標 Milky 方式 Galaxy 我們表示法：它需要有深度、 移動及風格體積型 — 會協助您建立的銀河系形狀的星的評等的全文。

建立有數十億個顆星動畫的 galaxy 問題是單單只有需要更新的單一項目數目會是每個畫面格以動畫顯示使用 CPU 的 HoloLens 的太大。 我們的解決方案涉及複雜的混合的藝術與科學。

## <a name="behind-the-scenes"></a>幕後

若要允許使用者瀏覽個別的星星，我們的第一個步驟是找出多少物件，我們可能會導致一次。

### <a name="rendering-particles"></a>轉譯物件

目前的 Cpu 適合處理序列工作和最多幾個平行工作一次 （視多少核心是），但 Gpu 可更有效地處理數千個平行作業。 不過，因為通常不會共用相同的記憶體與 CPU，CPU <> GPU 之間交換資料可以快速地成為瓶頸。 我們的解決方案就是要 galaxy gpu，而且完全存留在 GPU 上。

我們開始數千個不同的模式中的點物件的壓力測試。 這讓我們能夠取得 galaxy HoloLens，若要查看成功，而哪些沒有。

### <a name="creating-the-position-of-the-stars"></a>建立星星的位置

其中一個我們的小組成員已經寫C#會產生其初始位置的顆星的程式碼。 星星在橢圓形上，以及可以描述它們的位置 (**curveOffset**， **ellipseSize**，**提高權限**) 其中**curveOffset**是一種沿著橢圓形，星狀角度**ellipseSize**是沿著 X 橢圓形的維度和 Z 和提高權限內 galaxy 星號的適當權限提升。 因此，我們可以在其中建立緩衝區 ([Unity ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html))，會使用每個星號的屬性初始化，並將它傳送它會即時體驗的其餘部分在 GPU 上。 若要繪製這個緩衝區，我們使用[Unity DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html)允許執行著色器 （程式碼在 GPU 上） 任意一組點而不需要代表 galaxy 實際網格：

**CPU:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

我們開始著手使用數千個物件的未經處理循環模式。 這讓我們證明我們有需要我們可以管理許多物件，並執行以高效能的速度，但我們不滿意 galaxy 的整體圖形。 若要改善圖形，我們可以嘗試各種模式和旋轉粒子系統。 這些是一開始有希望，因為物件和效能的數目都維持一致，但圖形中斷 中央附近的 向下和星號已發出外表上但不實際。 我們需要可以讓我們來操作的時間，以及有實際上，移動的物件發出迴圈曾經接近 galaxy 的中心。

![我們嘗試各種不同的模式和旋轉，這類的粒子系統。](images/galaxy-patterns-500px.png)

我們嘗試各種不同的模式和旋轉，這類的粒子系統。

我們的團隊未方式個函式進行一些研究，以及我們做了專為 galaxy 自訂粒子系統，使我們無法移動物件為基礎的省略符號 」[密度 wave 理論](https://en.wikipedia.org/wiki/Density_wave_theory)，"其中 theorizes 的召集令galaxy 是密度的區域的更高，但常不斷變化，例如場流量壅塞災難。 出現穩定且穩固，但是顆星實際進出 arms 沿著其各自的省略符號中移動。 在我們的系統物件永遠不會存在在 CPU 上 — 我們產生卡片，並讓整個系統是只要初始狀態再加上時間 GPU 上的所有設定它們。 它進展如下：

![使用 GPU 轉譯粒子系統的進展](images/spiral-galaxy-arms-500px.jpg)

使用 GPU 轉譯粒子系統的進展


一旦足夠的省略符號，且設定為旋轉，請另開始表單"手臂 」 移動顆星的交集的位置。 每個橢圓形的路徑星星的間距提供一些隨機性，和每個星號都有一堆 positional 隨機性加入。 這會建立更自然的尋找散發的移動和 arm 星形。 最後，我們新增的功能為中心的距離為基礎的磁碟機色彩。

### <a name="creating-the-motion-of-the-stars"></a>建立星星的影片

若要動畫顯示一般的星狀影片，我們需要新增常數的角度為每個框架，以及取得沿著其省略符號常數星形的速度移動的星星。 這是使用的主要原因**curveOffset**。 這不是技術上正確，因為星號會加快沿著長的側邊的省略符號，但認為良好的一般動作。

![顆星的移動速度上長弧線，邊緣變慢。](images/ellipse-movement.jpg)

顆星的移動速度上長弧線，邊緣變慢。


一來，每一顆星星的完整說明由 (**curveOffset**， **ellipseSize**，**提高權限**，**年齡**) 其中**年齡**會載入場景後經過的總時間累積。




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

這可讓我們以產生數以萬計的星星，一次在應用程式開始，然後我們以動畫顯示到單一的一份沿著建立曲線的星星。 由於所有項目是在 GPU 上，系統可以動畫顯示到 CPU 免費平行的所有顆星。

![以下是看起來像是時繪製白色四邊形。](images/drawing-white-quads-300px.jpg)

以下是看起來像是時繪製白色四邊形。



若要讓每四張臉部的相機，我們可以使用 幾何著色器轉換到 2D 矩形會包含我們的星狀材質的畫面上的每個星級位置。

![鑽石，而不是四邊形。](images/drawing-white-quads-300px.jpg)

鑽石，而不是四邊形。


因為我們想要限制過度繪製 （數字的次數會處理像素） 最大的我們旋轉我們四邊形，因此它們會有較少的重疊。

### <a name="adding-clouds"></a>新增雲端

有許多方式來初步了體積型與物件 — 從 marching 內磁碟區到繪製多個物件，以模擬定域機組的光線。 即時的光跡 marching 打算可能過於昂貴和作者，困難，因此我們先嘗試建置使用方法來轉譯遊戲中的樹系冒充系統，有許多面向觀景窗的樹狀結構的 2D 影像。 當我們這麼做，在遊戲中時，我們可以有紋理的呈現旋轉周圍，儲存這些映像，以及在執行階段針對每個告示板卡片相機中的樹狀結構，請選取符合檢視方向的映像。 全像投影的映像時，這不會正常運作。 左側的眼睛與正確的眼睛之間的差異讓我們必須更高的解析度，否則它只會認價，別名，或重複。

在我們的第二次嘗試，我們試著盡可能讓多個物件。 當我們火繪製物件，並再將它們新增至場景模糊它們時，已達到最佳的視覺效果。 該方法的典型問題是我們無法一次繪製到幾個相關的物件和多少畫面仍維持 60 fps 它們所涵蓋的區域。 模糊處理產生的映像，以取得覺得此雲端已通常非常昂貴的作業。

![沒有紋理，這是雲端會如下所示 2%不透明度。](images/clouds-without-texture-300px.jpg)

沒有紋理，這是雲端會如下所示 2%不透明度。



正在附加的而有很多，我們會有數個四邊形彼此，重複陰影相同的像素的方式。 Galaxy 中心，在相同的像素都有數百個四邊形彼此的上方，並進行全螢幕時，這已有巨大的成本。

執行全螢幕雲端，並試著模糊化它們原本不好的概念，因此我們決定讓我們執行工作的硬體。

### <a name="a-bit-of-context-first"></a>A 位元內容的第一次

在遊戲中使用的紋理時紋理大小會很少會符合我們想要使用它，在的區域，但我們可以使用不同種類的篩選，以取得要進行插補，我們想要從材質的像素的色彩的圖形卡的紋理 ([紋理篩選<c3/>)。 我們感興趣的篩選[雙線性篩選](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)會計算任何使用最近鄰近項目 4 的像素的值。

![原始再進行篩選](images/texture-1.png)

![篩選後的結果](images/texture-2.png)

使用這個屬性，我們看到，我們試著兩倍大的區域內繪製紋理每次它模糊了結果。

而不是轉譯為全螢幕，並會遺失這些寶貴的毫秒，我們可能會花其他項目，我們會轉譯為小版本的畫面。 然後，您也可以藉由複製此紋理及延展的 2 倍數次，我們回到全螢幕時模糊處理程序中的內容。

![x3 upscale 回到完整解析。](images/galaxy-resolutions-300px.png)

x3 upscale 回到完整解析。



這讓我們能夠取得與只有一小部分的原始成本的雲端組件。 而不是新增雲端上的完整解析度，我們只繪製 1/64th 的像素為單位，只要延展回到完整解析度的材質。

![左側，upscale 1/8 至完整的解決方式，並向右，含 3 upscale 使用 2 的乘冪。](images/stars-upscaled-300px.jpg)

左側，upscale 1/8 至完整的解決方式，並向右，含 3 upscale 使用 2 的乘冪。


請注意，嘗試從 1/64th 完整大小的大小，一次看起來完全不同，圖形卡會仍使用 4 個像素的更大的區域加上網底且成品開始出現。

然後，如果我們與較小的卡片加入完整解析度顆星，我們會取得完整的 galaxy:

![附近的 galaxy 轉譯使用完整解析度顆星的最終結果](images/full-galaxy-500px.png)

一旦我們走上正軌圖形時，我們會新增圖層的雲端，空出的暫存的點，與我們在 Photoshop 繪製，並新增一些額外的色彩。 結果就是 Milky 方式銀河系我們封面和工程小組，這兩個認為的好處和它符合我們的深度、 磁碟區和動作的目標，所有不致於造成 CPU。

![以 3D 我們最終 Milky 方式 Galaxy。](images/final-galaxy-500px.jpg)

以 3D 我們最終 Milky 方式 Galaxy。


### <a name="more-to-explore"></a>進一步探索

我們已開放原始碼的 Galaxy Explorer 應用程式的程式碼，並可在[GitHub](https://github.com/Microsoft/GalaxyExplorer)上建置的開發人員。

有興趣 Galaxy explorer 找出更多的開發程序嗎？ 查看所有上我們過去專案更新[Microsoft HoloLens YouTube 頻道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)。

## <a name="about-the-authors"></a>關於作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b>是軟體工程師和花俏的視覺效果人十分熱心。 他曾 Galaxy 總管圖形工程師。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b>是封面的潛在客戶和空間熱衷 Galaxy explorer 管理 3D 模型化小組和得力的更多的物件。</td>
</tr>
</table>


## <a name="see-also"></a>另請參閱
* [在 GitHub 上的 Galaxy 總管](https://github.com/Microsoft/GalaxyExplorer)
* [YouTube 上的 Galaxy 總管專案更新](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
