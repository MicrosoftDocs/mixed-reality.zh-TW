---
title: 追蹤 Unity 中的遺失
description: 追蹤 Unity 應用程式內遺失的處理。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，追蹤遺失、 追蹤遺失映像
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595714"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="a3791-104">追蹤 Unity 中的遺失</span><span class="sxs-lookup"><span data-stu-id="a3791-104">Tracking loss in Unity</span></span>

<span data-ttu-id="a3791-105">當裝置找不到本身的世界中時，應用程式就會發生 「 追蹤遺失 」。</span><span class="sxs-lookup"><span data-stu-id="a3791-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="a3791-106">根據預設，Unity 會暫停更新迴圈，並向使用者顯示開頭顯示畫面影像。</span><span class="sxs-lookup"><span data-stu-id="a3791-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="a3791-107">當追蹤重新取得時，開頭顯示畫面影像就會消失，並更新迴圈會繼續。</span><span class="sxs-lookup"><span data-stu-id="a3791-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="a3791-108">或者，使用者可以手動處理這項轉換藉由選擇不設定。</span><span class="sxs-lookup"><span data-stu-id="a3791-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="a3791-109">所有的內容看起來將成為期間追蹤遺失，如果執行任何動作來處理它，鎖定的主體。</span><span class="sxs-lookup"><span data-stu-id="a3791-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="a3791-110">預設的處理</span><span class="sxs-lookup"><span data-stu-id="a3791-110">Default Handling</span></span>

<span data-ttu-id="a3791-111">根據預設，應用程式，以及所有訊息和事件的更新迴圈將停止期間追蹤遺失。</span><span class="sxs-lookup"><span data-stu-id="a3791-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="a3791-112">在該相同的時間，會向使用者顯示一個影像。</span><span class="sxs-lookup"><span data-stu-id="a3791-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="a3791-113">您可以自訂此映像，方法是移至 編輯-> 設定-> 播放程式中，按一下 啟動顯示映像，並設定全像攝影版的追蹤遺失映像。</span><span class="sxs-lookup"><span data-stu-id="a3791-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="a3791-114">手動處理</span><span class="sxs-lookup"><span data-stu-id="a3791-114">Manual Handling</span></span>

<span data-ttu-id="a3791-115">若要以手動方式處理追蹤遺失，您需要前往**編輯** > **專案設定** > **Player**  >  **通用 Windows 平台設定 索引標籤** > **開頭顯示畫面影像** > **Windows 全像攝影版**並取消核取 「 上追蹤遺失暫停並顯示映像".</span><span class="sxs-lookup"><span data-stu-id="a3791-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="a3791-116">在那之後，您需要使用下面指定的 Api 來處理追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="a3791-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="a3791-117">**命名空間：** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="a3791-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="a3791-118">**類型：** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="a3791-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="a3791-119">世界管理員會公開事件，以偵測追蹤遺失/獲得 (*WorldManager.OnPositionalLocatorStateChanged*) 查詢的目前狀態的屬性和 (*WorldManager.state*)</span><span class="sxs-lookup"><span data-stu-id="a3791-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="a3791-120">不使用中追蹤狀態時，相機不會出現轉譯於虛擬世界中，即使在使用者將轉譯中。</span><span class="sxs-lookup"><span data-stu-id="a3791-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="a3791-121">這表示物件將不會再對應到實體的任何位置，而且所有會出現鎖定的主體。</span><span class="sxs-lookup"><span data-stu-id="a3791-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="a3791-122">處理您自己的追蹤變更時必須輪詢狀態屬性，每個框架或控制代碼*OnPositionalLocatorStateChanged*事件。</span><span class="sxs-lookup"><span data-stu-id="a3791-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="a3791-123">輪詢</span><span class="sxs-lookup"><span data-stu-id="a3791-123">Polling</span></span>

<span data-ttu-id="a3791-124">最重要的狀態是*PositionalLocatorState.Active*表示追蹤會正常運作。</span><span class="sxs-lookup"><span data-stu-id="a3791-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="a3791-125">任何其他狀態將會導致主攝影機旋轉的差異。</span><span class="sxs-lookup"><span data-stu-id="a3791-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="a3791-126">例如: </span><span class="sxs-lookup"><span data-stu-id="a3791-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="a3791-127">處理 OnPositionalLocatorStateChanged 事件</span><span class="sxs-lookup"><span data-stu-id="a3791-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="a3791-128">或者，更方便，您也可以訂閱*OnPositionalLocatorStateChanged*處理轉換：</span><span class="sxs-lookup"><span data-stu-id="a3791-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="a3791-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3791-129">See also</span></span>
* [<span data-ttu-id="a3791-130">DirectX 中的處理追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="a3791-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
