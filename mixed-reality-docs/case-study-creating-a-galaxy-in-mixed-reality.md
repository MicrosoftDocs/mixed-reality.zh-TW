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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597018"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="6f999-105">案例研究-在混合實境中建立 galaxy</span><span class="sxs-lookup"><span data-stu-id="6f999-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="6f999-106">Microsoft HoloLens 出貨之前，我們會要求開發人員社群，何種應用程式他們想要查看建立的新裝置的資深內部團隊集。</span><span class="sxs-lookup"><span data-stu-id="6f999-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="6f999-107">超過 5000 個概念所共用，因而 24 小時制 Twitter 輪詢之後, 得獎者呼叫了解[Galaxy 總管](galaxy-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="6f999-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="6f999-108">Andy Zibits，圖案潛在客戶專案，並 Karim Luccin，小組的圖形工程師討論封面和 Milky 方式銀河系 Galaxy 總管 中的精確、 互動式表示建立的工程合作。</span><span class="sxs-lookup"><span data-stu-id="6f999-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="6f999-109">技術</span><span class="sxs-lookup"><span data-stu-id="6f999-109">The Tech</span></span>

<span data-ttu-id="6f999-110">[我們的小組](galaxy-explorer.md#meet-the-team)-向上提出的兩個設計工具、 三位開發人員、 四個演出者、 產生者和一個測試人員，有六週建置功能完整的應用程式，這可讓人了解並探索 vastness 和我們 Milky 方式 Galaxy 優點。</span><span class="sxs-lookup"><span data-stu-id="6f999-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="6f999-111">我們想要充分利用 HoloLens 能夠呈現 3D 物件，直接在您居住的空間，因此我們決定我們想要建立實際尋找 galaxy 其中人員就能夠放大關閉並查看個別的星星，分別位於它們自己滴下.</span><span class="sxs-lookup"><span data-stu-id="6f999-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="6f999-112">在開發的第一週中，我們想出了幾項目標 Milky 方式 Galaxy 我們表示法：它需要有深度、 移動及風格體積型 — 會協助您建立的銀河系形狀的星的評等的全文。</span><span class="sxs-lookup"><span data-stu-id="6f999-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="6f999-113">建立有數十億個顆星動畫的 galaxy 問題是單單只有需要更新的單一項目數目會是每個畫面格以動畫顯示使用 CPU 的 HoloLens 的太大。</span><span class="sxs-lookup"><span data-stu-id="6f999-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="6f999-114">我們的解決方案涉及複雜的混合的藝術與科學。</span><span class="sxs-lookup"><span data-stu-id="6f999-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="6f999-115">幕後</span><span class="sxs-lookup"><span data-stu-id="6f999-115">Behind the scenes</span></span>

<span data-ttu-id="6f999-116">若要允許使用者瀏覽個別的星星，我們的第一個步驟是找出多少物件，我們可能會導致一次。</span><span class="sxs-lookup"><span data-stu-id="6f999-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="6f999-117">轉譯物件</span><span class="sxs-lookup"><span data-stu-id="6f999-117">Rendering particles</span></span>

<span data-ttu-id="6f999-118">目前的 Cpu 適合處理序列工作和最多幾個平行工作一次 （視多少核心是），但 Gpu 可更有效地處理數千個平行作業。</span><span class="sxs-lookup"><span data-stu-id="6f999-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="6f999-119">不過，因為通常不會共用相同的記憶體與 CPU，CPU <> GPU 之間交換資料可以快速地成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="6f999-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="6f999-120">我們的解決方案就是要 galaxy gpu，而且完全存留在 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="6f999-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="6f999-121">我們開始數千個不同的模式中的點物件的壓力測試。</span><span class="sxs-lookup"><span data-stu-id="6f999-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="6f999-122">這讓我們能夠取得 galaxy HoloLens，若要查看成功，而哪些沒有。</span><span class="sxs-lookup"><span data-stu-id="6f999-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="6f999-123">建立星星的位置</span><span class="sxs-lookup"><span data-stu-id="6f999-123">Creating the position of the stars</span></span>

<span data-ttu-id="6f999-124">其中一個我們的小組成員已經寫C#會產生其初始位置的顆星的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f999-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="6f999-125">星星在橢圓形上，以及可以描述它們的位置 (**curveOffset**， **ellipseSize**，**提高權限**) 其中**curveOffset**是一種沿著橢圓形，星狀角度**ellipseSize**是沿著 X 橢圓形的維度和 Z 和提高權限內 galaxy 星號的適當權限提升。</span><span class="sxs-lookup"><span data-stu-id="6f999-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="6f999-126">因此，我們可以在其中建立緩衝區 ([Unity ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html))，會使用每個星號的屬性初始化，並將它傳送它會即時體驗的其餘部分在 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="6f999-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="6f999-127">若要繪製這個緩衝區，我們使用[Unity DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html)允許執行著色器 （程式碼在 GPU 上） 任意一組點而不需要代表 galaxy 實際網格：</span><span class="sxs-lookup"><span data-stu-id="6f999-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="6f999-128">**CPU:**</span><span class="sxs-lookup"><span data-stu-id="6f999-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="6f999-129">**GPU:**</span><span class="sxs-lookup"><span data-stu-id="6f999-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="6f999-130">我們開始著手使用數千個物件的未經處理循環模式。</span><span class="sxs-lookup"><span data-stu-id="6f999-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="6f999-131">這讓我們證明我們有需要我們可以管理許多物件，並執行以高效能的速度，但我們不滿意 galaxy 的整體圖形。</span><span class="sxs-lookup"><span data-stu-id="6f999-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="6f999-132">若要改善圖形，我們可以嘗試各種模式和旋轉粒子系統。</span><span class="sxs-lookup"><span data-stu-id="6f999-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="6f999-133">這些是一開始有希望，因為物件和效能的數目都維持一致，但圖形中斷 中央附近的 向下和星號已發出外表上但不實際。</span><span class="sxs-lookup"><span data-stu-id="6f999-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="6f999-134">我們需要可以讓我們來操作的時間，以及有實際上，移動的物件發出迴圈曾經接近 galaxy 的中心。</span><span class="sxs-lookup"><span data-stu-id="6f999-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![我們嘗試各種不同的模式和旋轉，這類的粒子系統。](images/galaxy-patterns-500px.png)

<span data-ttu-id="6f999-136">我們嘗試各種不同的模式和旋轉，這類的粒子系統。</span><span class="sxs-lookup"><span data-stu-id="6f999-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="6f999-137">我們的團隊未方式個函式進行一些研究，以及我們做了專為 galaxy 自訂粒子系統，使我們無法移動物件為基礎的省略符號 」[密度 wave 理論](https://en.wikipedia.org/wiki/Density_wave_theory)，"其中 theorizes 的召集令galaxy 是密度的區域的更高，但常不斷變化，例如場流量壅塞災難。</span><span class="sxs-lookup"><span data-stu-id="6f999-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="6f999-138">出現穩定且穩固，但是顆星實際進出 arms 沿著其各自的省略符號中移動。</span><span class="sxs-lookup"><span data-stu-id="6f999-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="6f999-139">在我們的系統物件永遠不會存在在 CPU 上 — 我們產生卡片，並讓整個系統是只要初始狀態再加上時間 GPU 上的所有設定它們。</span><span class="sxs-lookup"><span data-stu-id="6f999-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="6f999-140">它進展如下：</span><span class="sxs-lookup"><span data-stu-id="6f999-140">It progressed like this:</span></span>

![使用 GPU 轉譯粒子系統的進展](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="6f999-142">使用 GPU 轉譯粒子系統的進展</span><span class="sxs-lookup"><span data-stu-id="6f999-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="6f999-143">一旦足夠的省略符號，且設定為旋轉，請另開始表單"手臂 」 移動顆星的交集的位置。</span><span class="sxs-lookup"><span data-stu-id="6f999-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="6f999-144">每個橢圓形的路徑星星的間距提供一些隨機性，和每個星號都有一堆 positional 隨機性加入。</span><span class="sxs-lookup"><span data-stu-id="6f999-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="6f999-145">這會建立更自然的尋找散發的移動和 arm 星形。</span><span class="sxs-lookup"><span data-stu-id="6f999-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="6f999-146">最後，我們新增的功能為中心的距離為基礎的磁碟機色彩。</span><span class="sxs-lookup"><span data-stu-id="6f999-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="6f999-147">建立星星的影片</span><span class="sxs-lookup"><span data-stu-id="6f999-147">Creating the motion of the stars</span></span>

<span data-ttu-id="6f999-148">若要動畫顯示一般的星狀影片，我們需要新增常數的角度為每個框架，以及取得沿著其省略符號常數星形的速度移動的星星。</span><span class="sxs-lookup"><span data-stu-id="6f999-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="6f999-149">這是使用的主要原因**curveOffset**。</span><span class="sxs-lookup"><span data-stu-id="6f999-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="6f999-150">這不是技術上正確，因為星號會加快沿著長的側邊的省略符號，但認為良好的一般動作。</span><span class="sxs-lookup"><span data-stu-id="6f999-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![顆星的移動速度上長弧線，邊緣變慢。](images/ellipse-movement.jpg)

<span data-ttu-id="6f999-152">顆星的移動速度上長弧線，邊緣變慢。</span><span class="sxs-lookup"><span data-stu-id="6f999-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="6f999-153">一來，每一顆星星的完整說明由 (**curveOffset**， **ellipseSize**，**提高權限**，**年齡**) 其中**年齡**會載入場景後經過的總時間累積。</span><span class="sxs-lookup"><span data-stu-id="6f999-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="6f999-154">這可讓我們以產生數以萬計的星星，一次在應用程式開始，然後我們以動畫顯示到單一的一份沿著建立曲線的星星。</span><span class="sxs-lookup"><span data-stu-id="6f999-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="6f999-155">由於所有項目是在 GPU 上，系統可以動畫顯示到 CPU 免費平行的所有顆星。</span><span class="sxs-lookup"><span data-stu-id="6f999-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![以下是看起來像是時繪製白色四邊形。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="6f999-157">以下是看起來像是時繪製白色四邊形。</span><span class="sxs-lookup"><span data-stu-id="6f999-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="6f999-158">若要讓每四張臉部的相機，我們可以使用 幾何著色器轉換到 2D 矩形會包含我們的星狀材質的畫面上的每個星級位置。</span><span class="sxs-lookup"><span data-stu-id="6f999-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![鑽石，而不是四邊形。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="6f999-160">鑽石，而不是四邊形。</span><span class="sxs-lookup"><span data-stu-id="6f999-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="6f999-161">因為我們想要限制過度繪製 （數字的次數會處理像素） 最大的我們旋轉我們四邊形，因此它們會有較少的重疊。</span><span class="sxs-lookup"><span data-stu-id="6f999-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="6f999-162">新增雲端</span><span class="sxs-lookup"><span data-stu-id="6f999-162">Adding clouds</span></span>

<span data-ttu-id="6f999-163">有許多方式來初步了體積型與物件 — 從 marching 內磁碟區到繪製多個物件，以模擬定域機組的光線。</span><span class="sxs-lookup"><span data-stu-id="6f999-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="6f999-164">即時的光跡 marching 打算可能過於昂貴和作者，困難，因此我們先嘗試建置使用方法來轉譯遊戲中的樹系冒充系統，有許多面向觀景窗的樹狀結構的 2D 影像。</span><span class="sxs-lookup"><span data-stu-id="6f999-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="6f999-165">當我們這麼做，在遊戲中時，我們可以有紋理的呈現旋轉周圍，儲存這些映像，以及在執行階段針對每個告示板卡片相機中的樹狀結構，請選取符合檢視方向的映像。</span><span class="sxs-lookup"><span data-stu-id="6f999-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="6f999-166">全像投影的映像時，這不會正常運作。</span><span class="sxs-lookup"><span data-stu-id="6f999-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="6f999-167">左側的眼睛與正確的眼睛之間的差異讓我們必須更高的解析度，否則它只會認價，別名，或重複。</span><span class="sxs-lookup"><span data-stu-id="6f999-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="6f999-168">在我們的第二次嘗試，我們試著盡可能讓多個物件。</span><span class="sxs-lookup"><span data-stu-id="6f999-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="6f999-169">當我們火繪製物件，並再將它們新增至場景模糊它們時，已達到最佳的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="6f999-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="6f999-170">該方法的典型問題是我們無法一次繪製到幾個相關的物件和多少畫面仍維持 60 fps 它們所涵蓋的區域。</span><span class="sxs-lookup"><span data-stu-id="6f999-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="6f999-171">模糊處理產生的映像，以取得覺得此雲端已通常非常昂貴的作業。</span><span class="sxs-lookup"><span data-stu-id="6f999-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![沒有紋理，這是雲端會如下所示 2%不透明度。](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="6f999-173">沒有紋理，這是雲端會如下所示 2%不透明度。</span><span class="sxs-lookup"><span data-stu-id="6f999-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="6f999-174">正在附加的而有很多，我們會有數個四邊形彼此，重複陰影相同的像素的方式。</span><span class="sxs-lookup"><span data-stu-id="6f999-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="6f999-175">Galaxy 中心，在相同的像素都有數百個四邊形彼此的上方，並進行全螢幕時，這已有巨大的成本。</span><span class="sxs-lookup"><span data-stu-id="6f999-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="6f999-176">執行全螢幕雲端，並試著模糊化它們原本不好的概念，因此我們決定讓我們執行工作的硬體。</span><span class="sxs-lookup"><span data-stu-id="6f999-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="6f999-177">A 位元內容的第一次</span><span class="sxs-lookup"><span data-stu-id="6f999-177">A bit of context first</span></span>

<span data-ttu-id="6f999-178">在遊戲中使用的紋理時紋理大小會很少會符合我們想要使用它，在的區域，但我們可以使用不同種類的篩選，以取得要進行插補，我們想要從材質的像素的色彩的圖形卡的紋理 ([紋理篩選<c3/>)。](https://msdn.microsoft.com/library/dn642451.aspx)</span><span class="sxs-lookup"><span data-stu-id="6f999-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="6f999-179">我們感興趣的篩選[雙線性篩選](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)會計算任何使用最近鄰近項目 4 的像素的值。</span><span class="sxs-lookup"><span data-stu-id="6f999-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![原始再進行篩選](images/texture-1.png)

![篩選後的結果](images/texture-2.png)

<span data-ttu-id="6f999-182">使用這個屬性，我們看到，我們試著兩倍大的區域內繪製紋理每次它模糊了結果。</span><span class="sxs-lookup"><span data-stu-id="6f999-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="6f999-183">而不是轉譯為全螢幕，並會遺失這些寶貴的毫秒，我們可能會花其他項目，我們會轉譯為小版本的畫面。</span><span class="sxs-lookup"><span data-stu-id="6f999-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="6f999-184">然後，您也可以藉由複製此紋理及延展的 2 倍數次，我們回到全螢幕時模糊處理程序中的內容。</span><span class="sxs-lookup"><span data-stu-id="6f999-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 upscale 回到完整解析。](images/galaxy-resolutions-300px.png)

<span data-ttu-id="6f999-186">x3 upscale 回到完整解析。</span><span class="sxs-lookup"><span data-stu-id="6f999-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="6f999-187">這讓我們能夠取得與只有一小部分的原始成本的雲端組件。</span><span class="sxs-lookup"><span data-stu-id="6f999-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="6f999-188">而不是新增雲端上的完整解析度，我們只繪製 1/64th 的像素為單位，只要延展回到完整解析度的材質。</span><span class="sxs-lookup"><span data-stu-id="6f999-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![左側，upscale 1/8 至完整的解決方式，並向右，含 3 upscale 使用 2 的乘冪。](images/stars-upscaled-300px.jpg)

<span data-ttu-id="6f999-190">左側，upscale 1/8 至完整的解決方式，並向右，含 3 upscale 使用 2 的乘冪。</span><span class="sxs-lookup"><span data-stu-id="6f999-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="6f999-191">請注意，嘗試從 1/64th 完整大小的大小，一次看起來完全不同，圖形卡會仍使用 4 個像素的更大的區域加上網底且成品開始出現。</span><span class="sxs-lookup"><span data-stu-id="6f999-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="6f999-192">然後，如果我們與較小的卡片加入完整解析度顆星，我們會取得完整的 galaxy:</span><span class="sxs-lookup"><span data-stu-id="6f999-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![附近的 galaxy 轉譯使用完整解析度顆星的最終結果](images/full-galaxy-500px.png)

<span data-ttu-id="6f999-194">一旦我們走上正軌圖形時，我們會新增圖層的雲端，空出的暫存的點，與我們在 Photoshop 繪製，並新增一些額外的色彩。</span><span class="sxs-lookup"><span data-stu-id="6f999-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="6f999-195">結果就是 Milky 方式銀河系我們封面和工程小組，這兩個認為的好處和它符合我們的深度、 磁碟區和動作的目標，所有不致於造成 CPU。</span><span class="sxs-lookup"><span data-stu-id="6f999-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![以 3D 我們最終 Milky 方式 Galaxy。](images/final-galaxy-500px.jpg)

<span data-ttu-id="6f999-197">以 3D 我們最終 Milky 方式 Galaxy。</span><span class="sxs-lookup"><span data-stu-id="6f999-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="6f999-198">進一步探索</span><span class="sxs-lookup"><span data-stu-id="6f999-198">More to explore</span></span>

<span data-ttu-id="6f999-199">我們已開放原始碼的 Galaxy Explorer 應用程式的程式碼，並可在[GitHub](https://github.com/Microsoft/GalaxyExplorer)上建置的開發人員。</span><span class="sxs-lookup"><span data-stu-id="6f999-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="6f999-200">有興趣 Galaxy explorer 找出更多的開發程序嗎？</span><span class="sxs-lookup"><span data-stu-id="6f999-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="6f999-201">查看所有上我們過去專案更新[Microsoft HoloLens YouTube 頻道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)。</span><span class="sxs-lookup"><span data-stu-id="6f999-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="6f999-202">關於作者</span><span class="sxs-lookup"><span data-stu-id="6f999-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="6f999-203"><b>Karim Luccin</b>是軟體工程師和花俏的視覺效果人十分熱心。</span><span class="sxs-lookup"><span data-stu-id="6f999-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="6f999-204">他曾 Galaxy 總管圖形工程師。</span><span class="sxs-lookup"><span data-stu-id="6f999-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="6f999-205"><b>Andy Zibits</b>是封面的潛在客戶和空間熱衷 Galaxy explorer 管理 3D 模型化小組和得力的更多的物件。</span><span class="sxs-lookup"><span data-stu-id="6f999-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="6f999-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f999-206">See also</span></span>
* [<span data-ttu-id="6f999-207">在 GitHub 上的 Galaxy 總管</span><span class="sxs-lookup"><span data-stu-id="6f999-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="6f999-208">YouTube 上的 Galaxy 總管專案更新</span><span class="sxs-lookup"><span data-stu-id="6f999-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
