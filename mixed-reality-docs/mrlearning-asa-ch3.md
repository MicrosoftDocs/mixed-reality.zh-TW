---
title: Azure Spatial Anchor 教學課程 - 3。 顯示 Azure Spatial Anchor 意見反應
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 11342bada65e963db6393d35c99e2c2fbffe8ff1
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031258"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="380c0-105">3.顯示 Azure Spatial Anchor 意見反應</span><span class="sxs-lookup"><span data-stu-id="380c0-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="380c0-106">在本教學課程中，您將了解如何在使用 Azure Spatial Anchors (ASA) 時，為使用者提供有關錨點探索、事件和狀態的相關回饋。</span><span class="sxs-lookup"><span data-stu-id="380c0-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="380c0-107">目標</span><span class="sxs-lookup"><span data-stu-id="380c0-107">Objectives</span></span>

* <span data-ttu-id="380c0-108">了解如何設定 UI 面板，以顯示目前 ASA 工作階段的相關重要資訊</span><span class="sxs-lookup"><span data-stu-id="380c0-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="380c0-109">了解並探索 ASA SDK 可供使用者使用的回饋元素</span><span class="sxs-lookup"><span data-stu-id="380c0-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="380c0-110">設定 ASA 回饋 UI 面板</span><span class="sxs-lookup"><span data-stu-id="380c0-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="380c0-111">在 [階層] 視窗中，以滑鼠右鍵按一下 [指示]   > [TextContent]  物件，然後選取 [3D 物件]   > [文字 - TextMeshPro]  ，將 TextMeshPro 文字物件建立為 [指示] > [TextContent 物件] 的子系，並為其提供適當的名稱，例如 **Feedback**：</span><span class="sxs-lookup"><span data-stu-id="380c0-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="380c0-113">若要更簡便地使用場景，請按一下物件左邊的眼睛圖示，將 ParentAnchor 物件的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>設為關閉。</span><span class="sxs-lookup"><span data-stu-id="380c0-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="380c0-114">這會在場景視窗中隱藏物件，而不會變更其遊戲內的可見度。</span><span class="sxs-lookup"><span data-stu-id="380c0-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="380c0-115">在仍選取 **Feedback** 物件的情況下，在 [偵測器] 視窗中變更其位置和大小，使其整齊地放在指示文字底下，例如：</span><span class="sxs-lookup"><span data-stu-id="380c0-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="380c0-116">將矩形變形的 **Y 位置**變更為 -0.24</span><span class="sxs-lookup"><span data-stu-id="380c0-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="380c0-117">將矩形變形的**寬度**變更為 0.555</span><span class="sxs-lookup"><span data-stu-id="380c0-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="380c0-118">將矩形變形的**高度**變更為 0.1</span><span class="sxs-lookup"><span data-stu-id="380c0-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="380c0-119">然後選擇字型屬性，讓文字適當地放在文字區域中，例如：</span><span class="sxs-lookup"><span data-stu-id="380c0-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="380c0-120">將 Text Mesh Pro (指令碼) 的**字型樣式**變更為粗體</span><span class="sxs-lookup"><span data-stu-id="380c0-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="380c0-121">將 Text Mesh Pro (指令碼) 的**字型大小**變更為 0.17</span><span class="sxs-lookup"><span data-stu-id="380c0-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="380c0-122">將 Text Mesh Pro (指令碼) 的**對齊**變更為置中和中間</span><span class="sxs-lookup"><span data-stu-id="380c0-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="380c0-124">在仍選取 **Feedback** 物件的情況下，在 [偵測器] 視窗中，使用 [新增元件]  按鈕，將 **Anchor Feedback Script (指令碼)** 元件新增至 Feedback 物件：</span><span class="sxs-lookup"><span data-stu-id="380c0-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="380c0-126">將 **Feedback** 物件本身指派給 **Anchor Feedback Script (指令碼)** 元件的 [回饋文字]  欄位：</span><span class="sxs-lookup"><span data-stu-id="380c0-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="380c0-128">恭喜！</span><span class="sxs-lookup"><span data-stu-id="380c0-128">Congratulations</span></span>

<span data-ttu-id="380c0-129">在本教學課程中，您已了解如何建立 UI 面板，以顯示 Azure Spatial Anchor 驗的目前狀態，進而提供使用者即時回饋。</span><span class="sxs-lookup"><span data-stu-id="380c0-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
