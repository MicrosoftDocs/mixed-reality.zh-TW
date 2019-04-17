---
title: 啟用在家中的 3D 模型的位置
description: 如何將 3D 模型，從您的網站或應用程式放入家用的 Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D、 模型、 家中的位置、 位置、 全球、 模型、 混合的實境家用、 web、 應用程式
ms.openlocfilehash: 3a50353aae8e03c3ebb3ee9ec2f642f21836e925
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597094"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="573d0-104">啟用在首頁的混合實境中的 3D 模型的位置</span><span class="sxs-lookup"><span data-stu-id="573d0-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="573d0-105">這項功能已加入的一部分[Windows 10 April 2018 Update](release-notes-april-2018.md)。</span><span class="sxs-lookup"><span data-stu-id="573d0-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="573d0-106">舊版 Windows 不相容於這項功能。</span><span class="sxs-lookup"><span data-stu-id="573d0-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="573d0-107">[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)是使用者啟動應用程式之前的登陸位置的起點。</span><span class="sxs-lookup"><span data-stu-id="573d0-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="573d0-108">在某些情況下，2D 應用程式 （例如全像投影的應用程式） 作為裝飾或進一步調查完整的 3D 中啟用 3D 模型直接放置到混合的實境首頁。</span><span class="sxs-lookup"><span data-stu-id="573d0-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="573d0-109">*新增模型通訊協定*可讓您從網站或直接將家中的 Windows Mixed Reality 應用程式傳送的 3D 模型，它會保存像是[3D 應用程式啟動器](3d-app-launcher-design-guidance.md)，2D 應用程式和全像投影。</span><span class="sxs-lookup"><span data-stu-id="573d0-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="573d0-110">例如，如果您正在開發應用程式的 3D furniture 設計空間的類別目錄的該介面，您可以使用*新增模型通訊協定*可讓使用者放置這些家具 3D 模型，從類別目錄。</span><span class="sxs-lookup"><span data-stu-id="573d0-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="573d0-111">一旦將放在世界裡，使用者可以移動、 調整大小，和在家中移除這些就像其他全像投影的 3D 模型。</span><span class="sxs-lookup"><span data-stu-id="573d0-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="573d0-112">這篇文章提供實作的概觀*新增模型通訊協定*，以便您可以開始讓裝飾他們的世界，以從您的應用程式或網站的 3D 物件的使用者。</span><span class="sxs-lookup"><span data-stu-id="573d0-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="573d0-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="573d0-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="573d0-114">功能</span><span class="sxs-lookup"><span data-stu-id="573d0-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="573d0-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="573d0-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="573d0-116"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="573d0-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="573d0-117">新增模型通訊協定</span><span class="sxs-lookup"><span data-stu-id="573d0-117">Add model protocol</span></span></td><td style="text-align: center;"> <span data-ttu-id="573d0-118">✔️</span><span class="sxs-lookup"><span data-stu-id="573d0-118">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="573d0-119">✔️</span><span class="sxs-lookup"><span data-stu-id="573d0-119">✔️</span></span></td>
</tr>
</table>

## <a name="overview"></a><span data-ttu-id="573d0-120">總覽</span><span class="sxs-lookup"><span data-stu-id="573d0-120">Overview</span></span>

<span data-ttu-id="573d0-121">有 2 個步驟，以啟用在家用的 Windows Mixed Reality 的 3D 模型的位置：</span><span class="sxs-lookup"><span data-stu-id="573d0-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="573d0-122">[請確定您的 3D 模型適用於家用的 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。</span><span class="sxs-lookup"><span data-stu-id="573d0-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="573d0-123">實作*新增模型通訊協定*在您的應用程式或網頁 （本文）。</span><span class="sxs-lookup"><span data-stu-id="573d0-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="573d0-124">實作*新增模型通訊協定*</span><span class="sxs-lookup"><span data-stu-id="573d0-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="573d0-125">一旦[相容的 3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)，您可以實作*新增模型通訊協定*藉由啟用下列 URI，從任何網頁或應用程式：</span><span class="sxs-lookup"><span data-stu-id="573d0-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="573d0-126">如果 URI 指向遠端資源，然後它會自動下載並放置在首頁。</span><span class="sxs-lookup"><span data-stu-id="573d0-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="573d0-127">本機資源會複製到混合的實境家中的應用程式資料資料夾，再放在首頁。</span><span class="sxs-lookup"><span data-stu-id="573d0-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="573d0-128">我們建議您設計您的體驗情況下，使用者可能同時執行的較舊版本的 [隱藏] 按鈕，或停用它的話不支援這項功能的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="573d0-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="573d0-129">叫用*新增模型通訊協定*從通用 Windows 平台應用程式：</span><span class="sxs-lookup"><span data-stu-id="573d0-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="573d0-130">叫用*新增模型通訊協定*從網頁：</span><span class="sxs-lookup"><span data-stu-id="573d0-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="573d0-131">沈浸式 (VR) 耳機的考量</span><span class="sxs-lookup"><span data-stu-id="573d0-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="573d0-132">針對擬真 (VR) 耳機，混合實境入口網站不需要執行之前叫用*新增模型通訊協定*。</span><span class="sxs-lookup"><span data-stu-id="573d0-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="573d0-133">在此情況下，*新增模型通訊協定*會啟動混合實境入口網站，並讓直接其中耳機正在尋找當您將看見在首頁的混合實境中的物件。</span><span class="sxs-lookup"><span data-stu-id="573d0-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="573d0-134">當叫用*新增模型通訊協定*從桌面與已執行的混合實境入口網站中，確定 耳機是"甦醒狀態 」。</span><span class="sxs-lookup"><span data-stu-id="573d0-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="573d0-135">如果沒有，則放置將會失敗。</span><span class="sxs-lookup"><span data-stu-id="573d0-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="573d0-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="573d0-136">See also</span></span>

* [<span data-ttu-id="573d0-137">建立 3D 模型，使用 Windows Mixed Reality 在家中</span><span class="sxs-lookup"><span data-stu-id="573d0-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="573d0-138">瀏覽家用的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="573d0-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
