---
title: 開始使用 MRTK 第 2 版
description: 適用於想要利用 MRTK 的新開發人員
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 測試, 混合實境工具組, MRTK 第 2 版, MRTK, 工具, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: fc9638f405604bed7c7531ace0977a88509e91b5
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491098"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="f4e66-104">開始使用 MRTK 第 2 版</span><span class="sxs-lookup"><span data-stu-id="f4e66-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="f4e66-105">MRTK 入門指南</span><span class="sxs-lookup"><span data-stu-id="f4e66-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="f4e66-106">如需開始使用 MRTK V2 的詳細資訊，請參閱 [MRTK 入門指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)。</span><span class="sxs-lookup"><span data-stu-id="f4e66-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for detailed information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="f4e66-107">混合實境工具組 (MRTK) 是什麼？</span><span class="sxs-lookup"><span data-stu-id="f4e66-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="f4e66-108">MRTK 是一項令人驚奇的開放原始碼工具組，自 HoloLens 首次發行之後就已經存在，沒有我們開發人員社群的努力，就不會達到今天的境界。</span><span class="sxs-lookup"><span data-stu-id="f4e66-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="f4e66-109">過去 3 年來，我們聽取了開發人員社群的意見反應，將最主要的考量納入，建置了 MRTK v2。</span><span class="sxs-lookup"><span data-stu-id="f4e66-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="f4e66-110">Unity 的 MRTK v2 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="f4e66-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="f4e66-111">MRTK 第 2 版主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4e66-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="f4e66-112">此專案的目標是減少建立混合實境應用程式的進入障礙，以及回饋伴著我們成長的社群。</span><span class="sxs-lookup"><span data-stu-id="f4e66-112">The project is aimed at reducing barriers to entry, to create mixed reality applications and contribute back to the community as we all grow.</span></span> 

<span data-ttu-id="f4e66-113">若要深入了解，請參閱 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。</span><span class="sxs-lookup"><span data-stu-id="f4e66-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="f4e66-114">MRTK v2 的新功能</span><span class="sxs-lookup"><span data-stu-id="f4e66-114">New with MRTK v2</span></span>
<span data-ttu-id="f4e66-115">我們想要強調我們對這些平台工具的承諾。</span><span class="sxs-lookup"><span data-stu-id="f4e66-115">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="f4e66-116">事實上，我們利用 MRTK 第 2 版來開發收件匣體驗，例如安裝體驗 (OOBE) 和我們的混合實境學習應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4e66-116">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="f4e66-117">您也可以預期新的 HoloLens 2 功能會先透過 MRTK 公開，因為我們認為這是在我們的平台上進行開發的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="f4e66-117">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="f4e66-118">模組化</span><span class="sxs-lookup"><span data-stu-id="f4e66-118">Modular</span></span>
<span data-ttu-id="f4e66-119">我們以模組化的方式建置，因此不需要個別將工具組的部分納入您的專案中。</span><span class="sxs-lookup"><span data-stu-id="f4e66-119">We have built it in a modular way, so there's no need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="f4e66-120">這其實有幾個優點。</span><span class="sxs-lookup"><span data-stu-id="f4e66-120">There are actually a few benefits to this.</span></span>  <span data-ttu-id="f4e66-121">它會讓您的專案大小變小，讓您更容易管理。</span><span class="sxs-lookup"><span data-stu-id="f4e66-121">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="f4e66-122">此外，由於它是以可編寫指令碼的物件建置，而且是介面驅動的，因此您也可以用自己的物件取代其中所包含的元件，以支援其他服務、系統和平台。</span><span class="sxs-lookup"><span data-stu-id="f4e66-122">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="f4e66-123">跨平台</span><span class="sxs-lookup"><span data-stu-id="f4e66-123">Cross-platform</span></span>
<span data-ttu-id="f4e66-124">說到其他平台，它有跨平台支援。</span><span class="sxs-lookup"><span data-stu-id="f4e66-124">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="f4e66-125">雖然這並不代表每個平台都有現成的支援，但是我們確定當您將建置目標切換至其他平台時，不會有任何工具組程式碼中斷。</span><span class="sxs-lookup"><span data-stu-id="f4e66-125">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="f4e66-126">模組化設計的健全性和擴充性，為您提供平坦的道路，讓您可以支援多個平台，例如 ARCore、ARKit 和 OpenVR。</span><span class="sxs-lookup"><span data-stu-id="f4e66-126">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="f4e66-127">效能</span><span class="sxs-lookup"><span data-stu-id="f4e66-127">Performant</span></span>
<span data-ttu-id="f4e66-128">使用行動平台時，我們會考慮到效能。</span><span class="sxs-lookup"><span data-stu-id="f4e66-128">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="f4e66-129">這是非常重要的，我們想要確保工具不會與您作對。</span><span class="sxs-lookup"><span data-stu-id="f4e66-129">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4e66-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4e66-130">See also</span></span>
* [<span data-ttu-id="f4e66-131">MRTK 入門指南</span><span class="sxs-lookup"><span data-stu-id="f4e66-131">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="f4e66-132">MRTK 文件集首頁</span><span class="sxs-lookup"><span data-stu-id="f4e66-132">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="f4e66-133">安裝工具</span><span class="sxs-lookup"><span data-stu-id="f4e66-133">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="f4e66-134">從 HTK/MRTK 移植到 MRTK 第 2 版</span><span class="sxs-lookup"><span data-stu-id="f4e66-134">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
