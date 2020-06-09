---
title: Unreal 中的注視輸入
description: 設定 HoloLens 和 Unreal 引擎的注視輸入教學課程
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，HoloLens 2，眼睛追蹤，注視輸入，head 裝載的顯示器，Unreal 引擎
ms.openlocfilehash: 0bc8b83a2e840b066eb5e30665584e1c68f7b021
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84551804"
---
# <a name="gaze-input"></a><span data-ttu-id="ad9af-104">注視輸入</span><span class="sxs-lookup"><span data-stu-id="ad9af-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="ad9af-105">概觀</span><span class="sxs-lookup"><span data-stu-id="ad9af-105">Overview</span></span>

<span data-ttu-id="ad9af-106">[Windows Mixed Reality 外掛程式](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)並未提供任何內建的監看式輸入功能，但 HoloLens 2 確實支援眼追蹤。</span><span class="sxs-lookup"><span data-stu-id="ad9af-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="ad9af-107">實際的追蹤功能是由 Unreal 的前端**裝載的顯示**和**眼睛追蹤**api 所提供，包括：</span><span class="sxs-lookup"><span data-stu-id="ad9af-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="ad9af-108">裝置資訊</span><span class="sxs-lookup"><span data-stu-id="ad9af-108">Device information</span></span>
- <span data-ttu-id="ad9af-109">追蹤感應器</span><span class="sxs-lookup"><span data-stu-id="ad9af-109">Tracking sensors</span></span>
- <span data-ttu-id="ad9af-110">方向和位置</span><span class="sxs-lookup"><span data-stu-id="ad9af-110">Orientation and position</span></span>
- <span data-ttu-id="ad9af-111">裁剪窗格</span><span class="sxs-lookup"><span data-stu-id="ad9af-111">Clipping panes</span></span>
- <span data-ttu-id="ad9af-112">注視資料和追蹤資訊</span><span class="sxs-lookup"><span data-stu-id="ad9af-112">Gaze data and tracking information</span></span>

<span data-ttu-id="ad9af-113">您可以在 Unreal 的前端[裝載的顯示](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html)和[眼睛追蹤](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html)檔中找到完整的功能清單。</span><span class="sxs-lookup"><span data-stu-id="ad9af-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="ad9af-114">除了 Unreal Api 之外，也請查看 HoloLens 2 的[眼睛互動](eye-gaze-interaction.md)相關檔，並閱讀[hololens 2 眼追蹤](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)的運作方式。</span><span class="sxs-lookup"><span data-stu-id="ad9af-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad9af-115">只有 HoloLens 2 才支援眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="ad9af-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="ad9af-116">啟用眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="ad9af-116">Enabling eye tracking</span></span>
<span data-ttu-id="ad9af-117">您必須先在 HoloLens 專案設定中啟用注視輸入，才能使用任何 Unreal 的 Api。</span><span class="sxs-lookup"><span data-stu-id="ad9af-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="ad9af-118">當應用程式啟動時，您會看到如下列螢幕擷取畫面所示的同意提示。</span><span class="sxs-lookup"><span data-stu-id="ad9af-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="ad9af-119">選取 **[是]** 以設定許可權，並取得注視輸入的存取權。</span><span class="sxs-lookup"><span data-stu-id="ad9af-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="ad9af-120">如果您需要隨時變更此設定，可以在 [**設定**] 應用程式中找到。</span><span class="sxs-lookup"><span data-stu-id="ad9af-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![目視輸入許可權](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="ad9af-122">Unreal 中的 HoloLens 眼追蹤只有兩個眼睛的單一注視光線，而不是 stereoscopic 追蹤所需的兩張光線，這是不支援的。</span><span class="sxs-lookup"><span data-stu-id="ad9af-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="ad9af-123">這就是您開始在 Unreal 中新增注視輸入至 HoloLens 2 應用程式所需的所有設定。</span><span class="sxs-lookup"><span data-stu-id="ad9af-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="ad9af-124">您可以在下列連結中找到關於注視輸入的詳細資訊，以及它如何影響混合現實中的使用者。</span><span class="sxs-lookup"><span data-stu-id="ad9af-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="ad9af-125">建立您的互動體驗時，請務必考慮這些資訊。</span><span class="sxs-lookup"><span data-stu-id="ad9af-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad9af-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad9af-126">See also</span></span>
* [<span data-ttu-id="ad9af-127">校正</span><span class="sxs-lookup"><span data-stu-id="ad9af-127">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="ad9af-128">舒適度</span><span class="sxs-lookup"><span data-stu-id="ad9af-128">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="ad9af-129">目光和行動</span><span class="sxs-lookup"><span data-stu-id="ad9af-129">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ad9af-130">語音輸入</span><span class="sxs-lookup"><span data-stu-id="ad9af-130">Voice input</span></span>](voice-design.md)
