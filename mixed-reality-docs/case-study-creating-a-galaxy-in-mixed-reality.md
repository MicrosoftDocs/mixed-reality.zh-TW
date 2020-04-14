---
title: 案例研究-在混合現實中建立 galaxy
description: 在 Microsoft HoloLens 推出之前，我們會要求開發人員小組想要看到新裝置有經驗的內部團隊組建。 分享超過5000的想法，在24小時的 Twitter 輪詢之後，獲勝者就是所謂的「Galaxy Explorer」的想法。
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer、HoloLens、Windows Mixed Reality、分享您的想法、個案研究
ms.openlocfilehash: f13395250c8a73718408c051ab95d2ec4bf62014
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278176"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="31b54-105">案例研究-在混合現實中建立 galaxy</span><span class="sxs-lookup"><span data-stu-id="31b54-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="31b54-106">在 Microsoft HoloLens 推出之前，我們會要求開發人員小組想要看到新裝置有經驗的內部團隊組建。</span><span class="sxs-lookup"><span data-stu-id="31b54-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="31b54-107">分享超過5000的想法，在24小時的 Twitter 輪詢之後，獲勝者就是一個稱為「 [Galaxy Explorer](galaxy-explorer.md)」的概念。</span><span class="sxs-lookup"><span data-stu-id="31b54-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="31b54-108">Zibits，這是專案的 Karim Luccin，這是團隊的圖形工程師，談到在「Galaxy Explorer」中建立銀河方式的精確、互動標記法的美工和工程之間的共同作業。</span><span class="sxs-lookup"><span data-stu-id="31b54-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="31b54-109">技術</span><span class="sxs-lookup"><span data-stu-id="31b54-109">The Tech</span></span>

<span data-ttu-id="31b54-110">[我們的團隊](galaxy-explorer.md#meet-the-team)由兩個設計師組成，三名開發人員、四個演出者、生產者和一個測試人員，建立功能完整的應用程式，讓人們能夠瞭解及探索銀河方式 Galaxy 的 vastness 和美。</span><span class="sxs-lookup"><span data-stu-id="31b54-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="31b54-111">我們想要充分利用 HoloLens 在您的生活空間中直接轉譯3D 物件的能力，所以我們決定要建立一個逼真的外觀，讓使用者能夠放大並查看個別的星星，每個都在自己的軌跡上。</span><span class="sxs-lookup"><span data-stu-id="31b54-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="31b54-112">在第一周的開發過程中，我們提供了一些目標，讓我們以銀河的方式呈現 Galaxy：它必須有深度、移動和感覺體積型，這是一項可協助建立 Galaxy 圖形的完整星星。</span><span class="sxs-lookup"><span data-stu-id="31b54-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="31b54-113">建立具有數十億顆星的動畫 galaxy 的問題是，需要更新的大量單一元素會太大而無法讓 HoloLens 以動畫使用 CPU。</span><span class="sxs-lookup"><span data-stu-id="31b54-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="31b54-114">我們的解決方案牽涉到複雜的藝術與科學混合。</span><span class="sxs-lookup"><span data-stu-id="31b54-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="31b54-115">幕後</span><span class="sxs-lookup"><span data-stu-id="31b54-115">Behind the scenes</span></span>

<span data-ttu-id="31b54-116">為了讓人們能夠探索個別的星星，我們的第一步就是要找出一次可以轉譯多少個粒子。</span><span class="sxs-lookup"><span data-stu-id="31b54-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="31b54-117">呈現微粒</span><span class="sxs-lookup"><span data-stu-id="31b54-117">Rendering particles</span></span>

<span data-ttu-id="31b54-118">目前的 Cpu 非常適合用來一次處理序列工作和多個平行工作（取決於它們有多少核心），但是 Gpu 在以平行方式處理數以千計的作業時更有效率。</span><span class="sxs-lookup"><span data-stu-id="31b54-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="31b54-119">不過，因為它們通常不會與 CPU 共用相同的記憶體，所以在 CPU < > GPU 之間交換資料可能很快就會成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="31b54-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="31b54-120">我們的解決方案是在 GPU 上建立一個 galaxy，而且必須完全在 GPU 上運作。</span><span class="sxs-lookup"><span data-stu-id="31b54-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="31b54-121">我們在各種模式中開始使用數千個點粒子的壓力測試。</span><span class="sxs-lookup"><span data-stu-id="31b54-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="31b54-122">如此一來，我們就可以在 HoloLens 上取得 galaxy，以查看有哪些功能和功能。</span><span class="sxs-lookup"><span data-stu-id="31b54-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="31b54-123">建立星星的位置</span><span class="sxs-lookup"><span data-stu-id="31b54-123">Creating the position of the stars</span></span>

<span data-ttu-id="31b54-124">我們的其中一個小組成員已撰寫程式C#代碼，它會在其初始位置產生星星。</span><span class="sxs-lookup"><span data-stu-id="31b54-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="31b54-125">星星位於橢圓形上，而且其位置可以由（**curveOffset**， **ellipseSize**，提高**許可權**）來描述，其中**curveOffset**是星形沿著橢圓形的角度， **ellipseSize**是沿著 X 和 Z 的橢圓形維度，而提高 galaxy 內適當的許可權提升。</span><span class="sxs-lookup"><span data-stu-id="31b54-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="31b54-126">因此，我們可以建立一個緩衝區（[Unity 的 ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)），它會使用每個星型屬性進行初始化，並在 GPU 上將它傳送給其餘的經驗。</span><span class="sxs-lookup"><span data-stu-id="31b54-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="31b54-127">為了繪製這個緩衝區，我們使用[Unity 的 DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) ，允許在任意一組點上執行著色器（GPU 上的程式碼），而不需要實際的網格來表示 galaxy：</span><span class="sxs-lookup"><span data-stu-id="31b54-127">To draw this buffer, we use [Unity’s DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="31b54-128">**使用率**</span><span class="sxs-lookup"><span data-stu-id="31b54-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="31b54-129">**GPU**</span><span class="sxs-lookup"><span data-stu-id="31b54-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="31b54-130">我們從具有數千個粒子的原始迴圈模式開始。</span><span class="sxs-lookup"><span data-stu-id="31b54-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="31b54-131">如此一來，我們所需的證明就是我們可以管理許多粒子，並以高效能的速度執行它，但我們並不滿意 galaxy 的整體塑造。</span><span class="sxs-lookup"><span data-stu-id="31b54-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="31b54-132">為了改善此圖形，我們嘗試了各種不同的模式和物件系統旋轉。</span><span class="sxs-lookup"><span data-stu-id="31b54-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="31b54-133">這一開始是有希望的，因為微粒和效能的數目維持一致，但圖形接近中央，而星星發出外表，這並不實際。</span><span class="sxs-lookup"><span data-stu-id="31b54-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="31b54-134">我們需要一個可讓我們操控時間並讓微粒實際移動的發射，這會更接近 galaxy 的中心。</span><span class="sxs-lookup"><span data-stu-id="31b54-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![我們嘗試了各種旋轉的模式和物件系統，就像這樣。](images/galaxy-patterns-500px.png)

<span data-ttu-id="31b54-136">我們嘗試了各種旋轉的模式和物件系統，就像這樣。</span><span class="sxs-lookup"><span data-stu-id="31b54-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="31b54-137">我們的團隊進行了 galaxies 函式的一些研究，我們為 galaxy 建立了自訂的物件系統，讓我們可以根據「[密度 wave 理論](https://en.wikipedia.org/wiki/Density_wave_theory)」來移動省略號上的微粒，這會 theorizes galaxy 的臂是密度較高的區域，而在固定的 flux 中，像是交通不足。</span><span class="sxs-lookup"><span data-stu-id="31b54-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="31b54-138">它看起來穩定又穩固，但星形在沿著其各自的橢圓形移動時，實際上會移入和移出臂。</span><span class="sxs-lookup"><span data-stu-id="31b54-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="31b54-139">在我們的系統中，粒子永遠不會存在於 CPU 上—我們會產生卡片並在 GPU 上調整其方向，因此整個系統只是初始狀態 + 時間。</span><span class="sxs-lookup"><span data-stu-id="31b54-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="31b54-140">它的進展如下：</span><span class="sxs-lookup"><span data-stu-id="31b54-140">It progressed like this:</span></span>

![具有 GPU 轉譯之物件的進展](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="31b54-142">具有 GPU 轉譯之物件的進展</span><span class="sxs-lookup"><span data-stu-id="31b54-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="31b54-143">加入足夠的省略號並設定為旋轉之後，galaxies 就會開始形成「臂」，其中星形的移動會融合在其中。</span><span class="sxs-lookup"><span data-stu-id="31b54-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="31b54-144">沿著每個橢圓形路徑的星星間距會被賦予一些隨機性，而且每顆星都會加上一點的位置隨機性。</span><span class="sxs-lookup"><span data-stu-id="31b54-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="31b54-145">這建立了更自然的星型移動和 arm 圖形分佈。</span><span class="sxs-lookup"><span data-stu-id="31b54-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="31b54-146">最後，我們新增了以中央的距離為基礎來驅動色彩的功能。</span><span class="sxs-lookup"><span data-stu-id="31b54-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="31b54-147">建立星星的動作</span><span class="sxs-lookup"><span data-stu-id="31b54-147">Creating the motion of the stars</span></span>

<span data-ttu-id="31b54-148">若要建立一般星形動作的動畫，我們必須為每個框架新增一個常數角度，並以常數星形速度沿著橢圓形移動。</span><span class="sxs-lookup"><span data-stu-id="31b54-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="31b54-149">這是使用**curveOffset**的主要原因。</span><span class="sxs-lookup"><span data-stu-id="31b54-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="31b54-150">這在技術上並不正確，因為星星會沿著橢圓形的長邊更快速地移動，但一般動作會覺得良好。</span><span class="sxs-lookup"><span data-stu-id="31b54-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![星星以較長的弧線更快移動，邊緣的速度較慢。](images/ellipse-movement.jpg)

<span data-ttu-id="31b54-152">星星以較長的弧線更快移動，邊緣的速度較慢。</span><span class="sxs-lookup"><span data-stu-id="31b54-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="31b54-153">如此一來，每顆星都是由（**curveOffset**， **ellipseSize**，提高**許可權**，**年齡**）完整描述，其中**Age**是從載入場景以來已過的總時間累計。</span><span class="sxs-lookup"><span data-stu-id="31b54-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="31b54-154">如此一來，我們就可以在應用程式開始時產生數萬顆星一次，然後沿著建立的曲線，以動畫顯示一組挑的星星。</span><span class="sxs-lookup"><span data-stu-id="31b54-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="31b54-155">因為所有專案都是在 GPU 上，所以系統可以將所有星形以平行方式繪製，而不會對 CPU 進行任何成本。</span><span class="sxs-lookup"><span data-stu-id="31b54-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![以下是繪製白色四邊形時的外觀。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="31b54-157">以下是繪製白色四邊形時的外觀。</span><span class="sxs-lookup"><span data-stu-id="31b54-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="31b54-158">為了讓每個四顆人都成為攝影機，我們使用幾何著色器，將每個星形位置轉換成螢幕上的2D 矩形，其中將包含星形材質。</span><span class="sxs-lookup"><span data-stu-id="31b54-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![菱形，而不是四邊形。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="31b54-160">菱形，而不是四邊形。</span><span class="sxs-lookup"><span data-stu-id="31b54-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="31b54-161">因為我們想要限制過度繪製（圖元的處理次數）越多越好，我們就會將四邊形旋轉，讓它們的重迭較少。</span><span class="sxs-lookup"><span data-stu-id="31b54-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="31b54-162">新增雲端</span><span class="sxs-lookup"><span data-stu-id="31b54-162">Adding clouds</span></span>

<span data-ttu-id="31b54-163">有許多方法可讓您使用體積型感受，從磁片區內的光線 marching，到盡可能繪製最多的粒子來模擬雲端。</span><span class="sxs-lookup"><span data-stu-id="31b54-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="31b54-164">即時光線 marching 的成本太高且難以撰寫，所以我們先嘗試使用在遊戲中轉譯樹系的方法來建立一個冒名頂替系統，其中包含許多與相機相關的2D 影像。</span><span class="sxs-lookup"><span data-stu-id="31b54-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="31b54-165">當我們在遊戲中進行這項操作時，我們可以從相機呈現的材質會旋轉、儲存所有影像，並在執行時間為每個佈告欄卡片選取符合視圖方向的影像。</span><span class="sxs-lookup"><span data-stu-id="31b54-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="31b54-166">這在影像是全像投影時也沒有作用。</span><span class="sxs-lookup"><span data-stu-id="31b54-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="31b54-167">左邊眼和適當眼睛之間的差異，讓我們需要更高的解析度，或只是看起來像是平面、失真或重複。</span><span class="sxs-lookup"><span data-stu-id="31b54-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="31b54-168">在第二次嘗試時，我們試著盡可能多的粒子。</span><span class="sxs-lookup"><span data-stu-id="31b54-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="31b54-169">當我們 additively 已繪製的微粒，並將其新增到場景之前，已達到最佳視覺效果。</span><span class="sxs-lookup"><span data-stu-id="31b54-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="31b54-170">這種方法的典型問題，是關於我們可以在一次繪製多少個粒子，以及它們在維護60fps 時所涵蓋的畫面區域數量。</span><span class="sxs-lookup"><span data-stu-id="31b54-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="31b54-171">將產生的影像模糊以取得此雲端感覺，通常是相當耗費成本的作業。</span><span class="sxs-lookup"><span data-stu-id="31b54-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![如果沒有材質，這就是雲端看起來有2% 不透明度的樣子。](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="31b54-173">如果沒有材質，這就是雲端看起來有2% 不透明度的樣子。</span><span class="sxs-lookup"><span data-stu-id="31b54-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="31b54-174">加總並擁有許多，表示我們會在彼此上有數個四邊形，並重複著色相同的圖元。</span><span class="sxs-lookup"><span data-stu-id="31b54-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="31b54-175">在 galaxy 的中心，相同的圖元會在彼此上有數百個四邊形，而這在全螢幕完成時有相當大的成本。</span><span class="sxs-lookup"><span data-stu-id="31b54-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="31b54-176">執行全螢幕雲端並嘗試將它們模糊會是個不錯的主意，所以我們決定讓硬體為我們執行工作。</span><span class="sxs-lookup"><span data-stu-id="31b54-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="31b54-177">第一個內容</span><span class="sxs-lookup"><span data-stu-id="31b54-177">A bit of context first</span></span>

<span data-ttu-id="31b54-178">在遊戲中使用材質時，材質大小很少會符合我們想要在其中使用的區域，但我們可以使用不同類型的紋理篩選來取得圖形配接器，以從材質圖元（[紋理篩選](https://msdn.microsoft.com/library/dn642451.aspx)）中插入我們想要的色彩。</span><span class="sxs-lookup"><span data-stu-id="31b54-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="31b54-179">對我們感興趣的篩選是[雙線性篩選](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)，會使用4個最接近的鄰近專案來計算任何圖元的值。</span><span class="sxs-lookup"><span data-stu-id="31b54-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![篩選之前的原始](images/texture-1.png)

![篩選後的結果](images/texture-2.png)

<span data-ttu-id="31b54-182">使用此屬性時，我們會看到每次嘗試在區域中繪製材質兩次大時，會模糊結果。</span><span class="sxs-lookup"><span data-stu-id="31b54-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="31b54-183">我們不會轉譯成全螢幕，而是遺失這些珍貴的毫秒，而是會轉譯成較小的螢幕版本。</span><span class="sxs-lookup"><span data-stu-id="31b54-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="31b54-184">然後，藉由複製此材質並以2個因數來延展，我們會回到全螢幕，同時模糊處理常式中的內容。</span><span class="sxs-lookup"><span data-stu-id="31b54-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 升級回到完整解析度。](images/galaxy-resolutions-300px.png)

<span data-ttu-id="31b54-186">x3 升級回到完整解析度。</span><span class="sxs-lookup"><span data-stu-id="31b54-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="31b54-187">這讓我們只需要一小部分的原始成本，就能取得雲端元件。</span><span class="sxs-lookup"><span data-stu-id="31b54-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="31b54-188">我們不會在完整解析度上新增雲端，而是只繪製 1/第64次圖元，而只是將材質延展回完整解析度。</span><span class="sxs-lookup"><span data-stu-id="31b54-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Left，升級從 1/8 到完整解析;和 right，使用2的乘冪3升級。](images/stars-upscaled-300px.jpg)

<span data-ttu-id="31b54-190">Left，升級從 1/8 到完整解析;和 right，使用2的乘冪3升級。</span><span class="sxs-lookup"><span data-stu-id="31b54-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="31b54-191">請注意，嘗試從大小的 1/第64次到完整大小的外觀看起來完全不同，因為在我們的設定中，圖形配接器仍然會使用4個圖元來為較大的區域加上陰影，而成品會開始出現。</span><span class="sxs-lookup"><span data-stu-id="31b54-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="31b54-192">然後，如果我們以較小的卡片新增完整解析星星，我們會取得完整的 galaxy：</span><span class="sxs-lookup"><span data-stu-id="31b54-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![使用完整解析星形的 galaxy 轉譯接近最終結果](images/full-galaxy-500px.png)

<span data-ttu-id="31b54-194">隨著圖形的追蹤，我們新增了一層雲端，並以我們在 Photoshop 中繪製的臨時點交換，並新增一些額外的色彩。</span><span class="sxs-lookup"><span data-stu-id="31b54-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="31b54-195">結果是銀河的，Galaxy 我們的美工和工程團隊都覺得很好用，而且它達到了深度、音量和運動的目標—全都不會造成 CPU 的負擔。</span><span class="sxs-lookup"><span data-stu-id="31b54-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![在3D 中，我們最終的銀河方式為 Galaxy。](images/final-galaxy-500px.jpg)

<span data-ttu-id="31b54-197">在3D 中，我們最終的銀河方式為 Galaxy。</span><span class="sxs-lookup"><span data-stu-id="31b54-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="31b54-198">深入探索</span><span class="sxs-lookup"><span data-stu-id="31b54-198">More to explore</span></span>

<span data-ttu-id="31b54-199">我們開啟了適用于 Galaxy Explorer 應用程式的程式碼，並將其提供給[GitHub](https://github.com/Microsoft/GalaxyExplorer) ，供開發人員建立。</span><span class="sxs-lookup"><span data-stu-id="31b54-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="31b54-200">有興趣尋找更多有關 [Galaxy Explorer] 開發流程的資訊嗎？</span><span class="sxs-lookup"><span data-stu-id="31b54-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="31b54-201">查看[Microsoft HoloLens YouTube 頻道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)上所有過去的專案更新。</span><span class="sxs-lookup"><span data-stu-id="31b54-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="31b54-202">關於作者</span><span class="sxs-lookup"><span data-stu-id="31b54-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="31b54-203"><b>Karim Luccin</b>是一種軟體工程師和別致的視覺效果愛好者。</span><span class="sxs-lookup"><span data-stu-id="31b54-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="31b54-204">他是適用于 Galaxy Explorer 的圖形工程師。</span><span class="sxs-lookup"><span data-stu-id="31b54-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="31b54-205"><b>Zibits</b>是一位藝術的組長和空間愛好者，負責管理適用于 Galaxy Explorer 的3d 模型化小組，並無法駕馭更多的粒子。</span><span class="sxs-lookup"><span data-stu-id="31b54-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="31b54-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31b54-206">See also</span></span>
* [<span data-ttu-id="31b54-207">GitHub 上的 Galaxy Explorer</span><span class="sxs-lookup"><span data-stu-id="31b54-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="31b54-208">YouTube 上的 Galaxy Explorer 專案更新</span><span class="sxs-lookup"><span data-stu-id="31b54-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
