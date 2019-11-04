---
title: MRTK 第2版入門
description: 適用于想要利用 MRTK 的新開發人員
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality、測試、混合現實工具組、MRTK 第2版、MRTK、工具、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: 46a06b951ae9aa60259f70be3fa1e558e7ab8ab6
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438351"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="559cd-104">開始使用 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="559cd-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="559cd-105">MRTK 消費者入門指南</span><span class="sxs-lookup"><span data-stu-id="559cd-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="559cd-106">如需開始使用 MRTK V2 的詳細資訊，請參閱[MRTK 快速入門手冊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)。</span><span class="sxs-lookup"><span data-stu-id="559cd-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for detailed information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="559cd-107">什麼是混合現實工具組（MRTK）？</span><span class="sxs-lookup"><span data-stu-id="559cd-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="559cd-108">MRTK 是一項令人驚奇的開放原始碼工具組，自 HoloLens 首次發行之後就已經存在，而不是我們的開發人員社區的困難工作。</span><span class="sxs-lookup"><span data-stu-id="559cd-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="559cd-109">過去3年來，我們聽取了開發人員社區的意見反應，並已建立 MRTK v2 來考慮最大的顧慮。</span><span class="sxs-lookup"><span data-stu-id="559cd-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="559cd-110">Unity 的 MRTK v2 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="559cd-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="559cd-111">MRTK 第 2 版主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="559cd-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="559cd-112">此專案的目標是減少建立混合實境應用程式的進入障礙，以及回饋伴著我們成長的社群。</span><span class="sxs-lookup"><span data-stu-id="559cd-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 

<span data-ttu-id="559cd-113">若要深入瞭解，請參閱[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。</span><span class="sxs-lookup"><span data-stu-id="559cd-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="559cd-114">MRTK v2 的新版本</span><span class="sxs-lookup"><span data-stu-id="559cd-114">New with MRTK v2</span></span>
<span data-ttu-id="559cd-115">我們想要強調我們對這些平臺工具的承諾。</span><span class="sxs-lookup"><span data-stu-id="559cd-115">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="559cd-116">事實上，我們利用 MRTK 第2版來開發收件匣的經驗，例如安裝體驗（OOBE）和我們的混合現實學習應用程式。</span><span class="sxs-lookup"><span data-stu-id="559cd-116">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="559cd-117">您也可以預期新的 HoloLens 2 功能會先透過 MRTK 公開，因為我們認為這是在我們的平臺上進行開發的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="559cd-117">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="559cd-118">採用</span><span class="sxs-lookup"><span data-stu-id="559cd-118">Modular</span></span>
<span data-ttu-id="559cd-119">我們以模組化的方式建立了它，因此您不需要將每個工具組放在您的專案中。</span><span class="sxs-lookup"><span data-stu-id="559cd-119">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="559cd-120">這其實有幾個優點。</span><span class="sxs-lookup"><span data-stu-id="559cd-120">There are actually a few benefits to this.</span></span>  <span data-ttu-id="559cd-121">它可以讓您的專案大小變小，也更容易管理。</span><span class="sxs-lookup"><span data-stu-id="559cd-121">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="559cd-122">除此之外，因為它是使用可編寫腳本的物件所建立，而且是介面驅動的，所以您也可以取代自己所包含的元件，以支援其他服務、系統和平臺。</span><span class="sxs-lookup"><span data-stu-id="559cd-122">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="559cd-123">跨平台</span><span class="sxs-lookup"><span data-stu-id="559cd-123">Cross-platform</span></span>
<span data-ttu-id="559cd-124">說到其他平臺，它有跨平臺支援。</span><span class="sxs-lookup"><span data-stu-id="559cd-124">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="559cd-125">雖然這並不代表每個平臺都有現成的支援，但我們確保當您將組建目標切換至其他平臺時，沒有任何工具組程式碼會中斷。</span><span class="sxs-lookup"><span data-stu-id="559cd-125">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="559cd-126">模組化設計的健全性和擴充性，讓您能夠以良好的路徑來支援多個平臺，例如 ARCore、ARKit 和 OpenVR。</span><span class="sxs-lookup"><span data-stu-id="559cd-126">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="559cd-127">性能</span><span class="sxs-lookup"><span data-stu-id="559cd-127">Performant</span></span>
<span data-ttu-id="559cd-128">使用行動平臺時，我們會考慮到效能。</span><span class="sxs-lookup"><span data-stu-id="559cd-128">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="559cd-129">這是非常重要的，我們想要確保工具不會對您工作。</span><span class="sxs-lookup"><span data-stu-id="559cd-129">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="559cd-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="559cd-130">See also</span></span>
* [<span data-ttu-id="559cd-131">MRTK 入門指南</span><span class="sxs-lookup"><span data-stu-id="559cd-131">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="559cd-132">MRTK 檔首頁</span><span class="sxs-lookup"><span data-stu-id="559cd-132">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="559cd-133">安裝工具</span><span class="sxs-lookup"><span data-stu-id="559cd-133">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="559cd-134">從 HTK/MRTK 移植到 MRTK 第2版</span><span class="sxs-lookup"><span data-stu-id="559cd-134">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
