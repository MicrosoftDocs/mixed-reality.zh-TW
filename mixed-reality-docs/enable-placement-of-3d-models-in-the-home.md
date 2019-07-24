---
title: 在首頁中啟用3D 模型的放置
description: 如何從您的網站或應用程式, 將3D 模型放在 Windows Mixed Reality 首頁
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, 模型, 放置於家裡, 地點, 世界, 模型, 混合現實首頁, web, 應用程式
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829729"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="46580-104">在混合現實首頁中啟用3D 模型的放置</span><span class="sxs-lookup"><span data-stu-id="46580-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="46580-105">這項功能已新增為[Windows 10 2018 年4月更新](release-notes-april-2018.md)的一部分。</span><span class="sxs-lookup"><span data-stu-id="46580-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="46580-106">較舊版本的 Windows 與此功能不相容。</span><span class="sxs-lookup"><span data-stu-id="46580-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="46580-107">[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。</span><span class="sxs-lookup"><span data-stu-id="46580-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="46580-108">在某些案例中, 2D 應用程式 (例如「全息影像」應用程式) 可將3D 模型直接放置在混合現實首頁中作為裝飾, 或以完整3D 進行進一步檢查。</span><span class="sxs-lookup"><span data-stu-id="46580-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="46580-109">「*新增模型」通訊協定*可讓您將3d 模型從您的網站或應用程式直接傳送至 Windows Mixed Reality 首頁, 其將會保存, 例如[3d 應用程式啟動器](3d-app-launcher-design-guidance.md)、2d 應用程式和全息影像。</span><span class="sxs-lookup"><span data-stu-id="46580-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="46580-110">例如, 如果您正在開發的應用程式會呈現3D 傢俱的目錄以設計空間, 您可以使用*新增模型通訊協定*, 讓使用者從類別目錄中放置這些3d 傢俱模型。</span><span class="sxs-lookup"><span data-stu-id="46580-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="46580-111">一旦放在世界中, 使用者就可以移動、調整大小和移除這些3D 模型, 就像在家中的其他全息影像一樣。</span><span class="sxs-lookup"><span data-stu-id="46580-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="46580-112">本文概述如何實行「*新增模型」通訊協定*, 讓您可以開始讓使用者從您的應用程式或 Web 使用3d 物件裝飾其世界。</span><span class="sxs-lookup"><span data-stu-id="46580-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="46580-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="46580-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="46580-114"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="46580-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="46580-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="46580-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="46580-116"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="46580-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="46580-117">新增模型通訊協定</span><span class="sxs-lookup"><span data-stu-id="46580-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="46580-118">✔️</span><span class="sxs-lookup"><span data-stu-id="46580-118">✔️</span></span></td>
        <td><span data-ttu-id="46580-119">✔️</span><span class="sxs-lookup"><span data-stu-id="46580-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="46580-120">總覽</span><span class="sxs-lookup"><span data-stu-id="46580-120">Overview</span></span>

<span data-ttu-id="46580-121">在 Windows Mixed Reality 首頁中啟用3D 模型的位置有2個步驟:</span><span class="sxs-lookup"><span data-stu-id="46580-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="46580-122">[確定您的3d 模型與 Windows Mixed Reality 首頁相容](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。</span><span class="sxs-lookup"><span data-stu-id="46580-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="46580-123">在您的應用程式或網頁中執行「*新增模型」通訊協定*(本文)。</span><span class="sxs-lookup"><span data-stu-id="46580-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="46580-124">執行*新增模型通訊協定*</span><span class="sxs-lookup"><span data-stu-id="46580-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="46580-125">當您擁有[相容的3d 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)之後, 您可以從任何網頁或應用程式啟用下列 URI, 以實作為「*新增模型」通訊協定*:</span><span class="sxs-lookup"><span data-stu-id="46580-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="46580-126">如果 URI 指向遠端資源, 則會自動下載並放在首頁。</span><span class="sxs-lookup"><span data-stu-id="46580-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="46580-127">本機資源會先複製到混合現實首頁的 [應用程式資料] 資料夾, 才會放入首頁。</span><span class="sxs-lookup"><span data-stu-id="46580-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="46580-128">我們建議您針對使用者可能執行舊版 Windows 而不支援這項功能的情況, 在可能的情況下, 將您的經驗設計成考慮。</span><span class="sxs-lookup"><span data-stu-id="46580-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="46580-129">從通用 Windows 平臺應用程式叫用*新增模型通訊協定*:</span><span class="sxs-lookup"><span data-stu-id="46580-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="46580-130">從網頁叫用*新增模型通訊協定*:</span><span class="sxs-lookup"><span data-stu-id="46580-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="46580-131">沉浸式 (VR) 耳機的考慮</span><span class="sxs-lookup"><span data-stu-id="46580-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="46580-132">若為沉浸式 (VR) 耳機, 則在叫用「*新增模型」通訊協定*之前, 混合現實入口網站不需要執行。</span><span class="sxs-lookup"><span data-stu-id="46580-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="46580-133">在此情況下, 「*新增模型」通訊協定*將會啟動混合現實入口網站, 並直接將物件放在您抵達混合現實首頁後的頭戴式裝置上。</span><span class="sxs-lookup"><span data-stu-id="46580-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="46580-134">從已執行混合現實入口網站的桌面叫用 [*新增模型] 通訊協定*時, 請確定耳機處於「喚醒」狀態。</span><span class="sxs-lookup"><span data-stu-id="46580-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="46580-135">如果不是, 則放置將會失敗。</span><span class="sxs-lookup"><span data-stu-id="46580-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="46580-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46580-136">See also</span></span>

* [<span data-ttu-id="46580-137">建立3D 模型以用於 Windows Mixed Reality 首頁</span><span class="sxs-lookup"><span data-stu-id="46580-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="46580-138">瀏覽 Windows Mixed Reality 住家</span><span class="sxs-lookup"><span data-stu-id="46580-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
