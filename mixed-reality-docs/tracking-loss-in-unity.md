---
title: Unity 中的追蹤遺失
description: 處理 Unity 應用程式內的追蹤遺失。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 追蹤遺失, 追蹤遺失影像
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548750"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="77ebe-104">Unity 中的追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="77ebe-104">Tracking loss in Unity</span></span>

<span data-ttu-id="77ebe-105">當裝置無法在世界中找到自己時, 應用程式就會遇到「追蹤遺失」的情況。</span><span class="sxs-lookup"><span data-stu-id="77ebe-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="77ebe-106">根據預設, Unity 會暫停更新迴圈, 並向使用者顯示開機映射。</span><span class="sxs-lookup"><span data-stu-id="77ebe-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="77ebe-107">重新執行追蹤時, 啟動顯示映射會消失, 且更新迴圈會繼續。</span><span class="sxs-lookup"><span data-stu-id="77ebe-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="77ebe-108">或者, 使用者可以退出宣告設定來手動處理這項轉換。</span><span class="sxs-lookup"><span data-stu-id="77ebe-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="77ebe-109">所有內容在追蹤遺失期間似乎會被鎖定, 如果沒有處理它,</span><span class="sxs-lookup"><span data-stu-id="77ebe-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="77ebe-110">預設處理</span><span class="sxs-lookup"><span data-stu-id="77ebe-110">Default Handling</span></span>

<span data-ttu-id="77ebe-111">根據預設, 應用程式的更新迴圈以及所有訊息和事件都會在追蹤遺失的期間停止。</span><span class="sxs-lookup"><span data-stu-id="77ebe-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="77ebe-112">此時, 系統會對使用者顯示影像。</span><span class="sxs-lookup"><span data-stu-id="77ebe-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="77ebe-113">若要自訂此映射, 請前往 編輯-> 設定-> 播放程式, 按一下 啟動顯示影像, 然後設定全像攝影追蹤遺失影像。</span><span class="sxs-lookup"><span data-stu-id="77ebe-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="77ebe-114">手動處理</span><span class="sxs-lookup"><span data-stu-id="77ebe-114">Manual Handling</span></span>

<span data-ttu-id="77ebe-115">若要手動處理追蹤遺失, 您必須移至 **編輯** > **專案設定** >  **播放** >  **, 通用 Windows 平臺設定**  > 索引標籤**啟動顯示影像** > **Windows**全像投影和取消核取 追蹤遺失暫停並顯示影像。</span><span class="sxs-lookup"><span data-stu-id="77ebe-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="77ebe-116">之後, 您必須使用下列指定的 Api 來處理追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="77ebe-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="77ebe-117">**命名空間：**  *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="77ebe-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="77ebe-118">**類型：** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="77ebe-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="77ebe-119">World Manager 會公開一個事件來偵測遺失/取得的追蹤 (*WorldManager. OnPositionalLocatorStateChanged*) 和屬性以查詢目前的狀態 (*WorldManager 狀態*)。</span><span class="sxs-lookup"><span data-stu-id="77ebe-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="77ebe-120">當追蹤狀態不是作用中時, 即使使用者翻譯, 相機也不會在虛擬世界中轉譯。</span><span class="sxs-lookup"><span data-stu-id="77ebe-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="77ebe-121">這表示物件不會再對應到任何實體位置, 而且全部都會顯示為 [已鎖定] 主體。</span><span class="sxs-lookup"><span data-stu-id="77ebe-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="77ebe-122">處理自己的追蹤變更時, 您必須輪詢每個框架的狀態屬性, 或處理*OnPositionalLocatorStateChanged*事件。</span><span class="sxs-lookup"><span data-stu-id="77ebe-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="77ebe-123">巡迴</span><span class="sxs-lookup"><span data-stu-id="77ebe-123">Polling</span></span>

<span data-ttu-id="77ebe-124">最重要的狀態為*PositionalLocatorState* , 表示追蹤功能完全正常。</span><span class="sxs-lookup"><span data-stu-id="77ebe-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="77ebe-125">任何其他狀態都只會導致主要攝影機的旋轉差異。</span><span class="sxs-lookup"><span data-stu-id="77ebe-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="77ebe-126">例如:</span><span class="sxs-lookup"><span data-stu-id="77ebe-126">For example:</span></span>

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="77ebe-127">處理 OnPositionalLocatorStateChanged 事件</span><span class="sxs-lookup"><span data-stu-id="77ebe-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="77ebe-128">或者, 您也可以更方便地訂閱*OnPositionalLocatorStateChanged*來處理轉換:</span><span class="sxs-lookup"><span data-stu-id="77ebe-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="77ebe-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77ebe-129">See also</span></span>
* [<span data-ttu-id="77ebe-130">處理 DirectX 中的追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="77ebe-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
