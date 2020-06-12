---
title: Unreal 中的空間對應
description: 在 Unreal 中使用空間對應的指南
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 空間對應
ms.openlocfilehash: 2bbfc3972acdb9dc7d5ebd23c85ab0ef5532cfb9
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428785"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal 中的空間對應

## <a name="overview"></a>概觀
空間對應可讓您將物件放在實體世界的表面上，方法是在 HoloLens 周圍顯示世界，這使得全像投影對使用者來說看起來更真實。 空間對應也會利用真實世界的深度提示，來錨定使用者世界中的物件。這有助於說服使用者這些全像投影實際在其空間內；在空間中浮動或隨著使用者移動的全像投影，將不會覺得真實。 您想要盡可能地將項目放在舒適的位置。

若要深入了解空間對應品質、放置、遮蔽、轉譯等等，請參閱[空間對應](spatial-mapping.md)文件。

## <a name="enabling-spatial-mapping"></a>啟用空間對應

若要在 HoloLens 上啟用空間對應：
- 開啟 [編輯] > [專案設定]，然後向下捲動至 [平台] 區段。    
    + 選取 **HoloLens** 並勾選 [空間感知]。

若要在 HoloLens 遊戲中加入空間對應，並偵錯 **MRMesh**：
1. 開啟 **ARSessionConfig**，並展開 [ARSettings] > [世界對應] 區段。 

2. 勾選 [從追蹤的幾何圖形產生網格資料]，這會指示 HoloLens 外掛程式啟動，以非同步方式取得空間對應資料，並透過 **MRMesh**將其呈現給 Unreal。 
3. 勾選 [以線框呈現網格資料]，以在 **MRMesh** 中顯示每個三角形的白色線框。 

![空間錨點存放區就緒](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>執行階段的空間對應
您可以修改下列參數，以更新空間對應執行階段行為：

- 開啟 [編輯] > [專案設定]、向下捲動至 [平台] 區段，然後選取 [HoloLens] > [空間對應]： 

![空間錨點專案設定](images/unreal-spatialmapping-projectsettings.PNG)

- **每立方米的三角形數量上限計量**會更新空間對應網格中三角形的密度。  
- **空間網格體積大小**是玩家周圍用來呈現和更新空間對應資料的立方體大小。  
    + 如果預期的應用程式執行階段環境預期會很大，此值可能需要很大，才能符合真實世界的空間。  另一方面，如果應用程式只需要在使用者附近的表面上放置全像投影，則此值可能會比較小。 當使用者在世界中行走時，空間對應體積會隨著他們移動。 

## <a name="working-with-mrmesh"></a>使用 MongoDB
若要可在執行階段存取 **MRMesh**：
1. 將 **ARTrackableNotify** 元件新增至藍圖動作項目。 

![空間錨點的 AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. 選取 **ARTrackableNotify** 元件，然後展開 [詳細資料] 面板中的 [事件] 區段。 
    - 對您要監視的事件按一下 **+** 按鈕。 

![空間錨點事件](images/unreal-spatialmapping-events.PNG)

在此情況下，會監視 **On Add Tracked Geometry** 事件，這會尋找與空間對應資料相符的有效世界網格。 您可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 元件 API 中找到完整的事件清單。 

您可以在藍圖事件圖形或 C++ 中變更網格的材質。 下方螢幕擷取畫面會顯示藍圖路由： 

![空間錨點範例](images/unreal-spatialmapping-example.PNG)

在 C++ 中，您可以訂閱 `OnTrackableAdded` 委派，以在 `ARTrackedGeometry` 可用時立即取得，如下列程式碼所示。 

> [!IMPORTANT]
> 專案的 build.cs 檔案**必須**具有 **PublicDependencyModuleNames** 清單中的 **AugmentedReality**。
> - 這包括 **ARBlueprintLibrary** 和 MRMeshComponent，可讓您檢查 **UARTrackedGeometry** 的 **MRMesh** 元件。 

![空間錨點範例程式 C++ 代碼](images/unreal-spatialmapping-examplecode.PNG)

空間對應不是透過 **ARTrackedGeometries** 呈現的唯一資料類型。 您可以檢查 `EARObjectClassification` 是否為 `World`，其表示這是空間對應幾何。 

已更新和移除的事件也有類似的委派： 
- `AddOnTrackableUpdatedDelegate_Handle` 
- `AddOnTrackableRemovedDelegate_Handle`。 

您可以在 [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API 中找到完整的事件清單。

## <a name="see-also"></a>另請參閱
* [空間對應](spatial-mapping.md)
