---
title: 開始使用 MRTK 第 2 版
description: 適用於新的開發人員感興趣利用 MRTK
author: grbury
ms.author: grbury
ms.date: 02/22/19
ms.topic: article
keywords: Windows Mixed Reality，測試、 MRTK，第 2 版 MRTK、 工具、 SDK、 HoloLens、 HoloLens 2
ms.openlocfilehash: 44e5fe0fd4384af68922eda4bcb0594d39a1c1b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591824"
---
# <a name="getting-started-with-mrtk-version-2"></a><span data-ttu-id="4272d-104">開始使用 MRTK 第 2 版</span><span class="sxs-lookup"><span data-stu-id="4272d-104">Getting started with MRTK version 2</span></span>

<span data-ttu-id="4272d-105">MRTK 是令人讚嘆的開放原始碼工具組，因為 HoloLens 首次發行，而且不會很今天不會導致我們開發人員社群的困難的工作已存在。</span><span class="sxs-lookup"><span data-stu-id="4272d-105">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="4272d-106">過去 3 年來，我們已聽到了我們的開發人員社群的意見反應，並建置 MRTK 第 2 版的最大考量列入考量。</span><span class="sxs-lookup"><span data-stu-id="4272d-106">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK version 2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="4272d-107">使用 Unity MRTK 第 2 版是開放原始碼跨平台開發套件混合的實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="4272d-107">The MRTK version 2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="4272d-108">MRTK 第 2 版被要加速開發以 Microsoft HoloLens，Windows Mixed Reality 沈浸式 (VR) 耳機和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4272d-108">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="4272d-109">專案被針對至項目，以建立混合的實境應用程式以及貢獻回饋給社群隨著我們越來越減少屏障。</span><span class="sxs-lookup"><span data-stu-id="4272d-109">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="4272d-110">請參閱<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK 第 2 版 wiki</a>開始，並了解更多。</span><span class="sxs-lookup"><span data-stu-id="4272d-110">See the <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK version 2 wiki</a> to get started and learn more.</span></span>

## <a name="new-with-mrtk-version-2"></a><span data-ttu-id="4272d-111">新 MRTK 第 2 版</span><span class="sxs-lookup"><span data-stu-id="4272d-111">New with MRTK version 2</span></span>
<span data-ttu-id="4272d-112">我們想要強調致力於這些平台工具。</span><span class="sxs-lookup"><span data-stu-id="4272d-112">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="4272d-113">事實上，我們運用 MRTK 第 2 版來開發我們的收件匣體驗，例如安裝體驗 (OOBE) 及混合實境學習應用程式。</span><span class="sxs-lookup"><span data-stu-id="4272d-113">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="4272d-114">您也可以預期看到新的 HoloLens 2 功能，因為我們認為它可以在我們的平台上進行開發的最佳方式，先透過 MRTK。</span><span class="sxs-lookup"><span data-stu-id="4272d-114">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="4272d-115">模組化</span><span class="sxs-lookup"><span data-stu-id="4272d-115">Modular</span></span>
<span data-ttu-id="4272d-116">我們已建置模組化的方式，使您不需要納入您的專案中的每個位元工具組。</span><span class="sxs-lookup"><span data-stu-id="4272d-116">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="4272d-117">有幾個優點實際上這個。</span><span class="sxs-lookup"><span data-stu-id="4272d-117">There are actually a few benefits to this.</span></span>  <span data-ttu-id="4272d-118">它會保留您專案的大小比較小，以及可讓您更容易管理。</span><span class="sxs-lookup"><span data-stu-id="4272d-118">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="4272d-119">除此之外，，因為它由可編寫指令碼物件所建立，並且遵守介面，它也是讓您將會包含以您自己的資源，以支援其他服務、 系統與平台的元件。</span><span class="sxs-lookup"><span data-stu-id="4272d-119">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="4272d-120">跨平台</span><span class="sxs-lookup"><span data-stu-id="4272d-120">Cross-platform</span></span>
<span data-ttu-id="4272d-121">它說到其他平台，提供跨平台支援。</span><span class="sxs-lookup"><span data-stu-id="4272d-121">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="4272d-122">這並不表示每個單一平台支援現成的雖然我們已經確定當您切換到其他平台的建置目標，工具組程式碼都將會中斷。</span><span class="sxs-lookup"><span data-stu-id="4272d-122">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="4272d-123">強固性和擴充性的模組化設計設定您要能夠支援多種平台，例如 ARCore、 ARKit，以及 OpenVR 良好的路徑上。</span><span class="sxs-lookup"><span data-stu-id="4272d-123">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="4272d-124">高效能</span><span class="sxs-lookup"><span data-stu-id="4272d-124">Performant</span></span>
<span data-ttu-id="4272d-125">使用行動裝置平台，我們就以建構效能考量。</span><span class="sxs-lookup"><span data-stu-id="4272d-125">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="4272d-126">這是非常重要的是，和我們想要確保，不會針對您的工具。</span><span class="sxs-lookup"><span data-stu-id="4272d-126">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="4272d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4272d-127">See also</span></span>
* [<span data-ttu-id="4272d-128">安裝工具</span><span class="sxs-lookup"><span data-stu-id="4272d-128">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="4272d-129">從 HTK/MRTK 移植到 MRTK 第 2 版</span><span class="sxs-lookup"><span data-stu-id="4272d-129">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
