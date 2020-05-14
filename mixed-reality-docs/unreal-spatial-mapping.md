---
title: Unreal 中的空間對應
description: 在 Unreal 中使用空間對應的指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 空間對應
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840077"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal 中的空間對應

若要在 HoloLens 上啟用空間對應，請確定已在 [專案設定] > [平台] > [HoloLens] > [功能] 下的 Unreal 編輯器中勾選「空間感知」功能。  

若要在 HoloLens 遊戲中選擇使用空間對應，請在 ARSessionConfig 中啟用 [從追蹤的幾何圖形產生網格資料]。  然後 HoloLens 外掛程式會以非同步方式取得空間對應資料，並透過 MRMesh 將其呈現給 Unreal。 

![空間錨點存放區就緒](images/unreal-spatialmapping-arsettings.PNG)

若要查看空間對應網格的偵錯視覺化效果，請啟用 ARSessionConfig 中的 [以線框呈現網格資料] 核取方塊，以查看 MRMesh 中每個三角形的白色線框。 

在 [專案設定] > [平台] > [HoloLens] > [空間對應] 中，您可以修改下列參數來更新空間對應的執行階段行為： 

![空間錨點專案設定](images/unreal-spatialmapping-projectsettings.PNG)

「每立方米的三角形數量上限計量」會更新空間對應網格中三角形的密度。  「空間網格體積大小」表示玩家周圍用來呈現和更新空間對應資料的立方體大小。  如果預期的應用程式執行階段環境預期會很大，此欄位可能需要很大，才能符合真實世界的空間。  相反地，如果應用程式只需要在使用者附近的表面上放置全像投影，則此欄位可能會比較小。  當使用者在世界中行走時，空間對應體積會隨著他們移動。 

若要在執行階段取得 MRMesh 的存取權，請先將 AR Trackable Notify 元件新增至藍圖動作項目： 

![空間錨點的 AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

然後移至元件的詳細資料，並且按一下要監視事件的綠色 "+" 按鈕。 

![空間錨點事件](images/unreal-spatialmapping-events.PNG)

在此案例中，我們會監視 On Add Tracked Geometry 事件，尋找與空間對應資料相對應的有效世界網格，並變更網格的材質： 

![空間錨點範例](images/unreal-spatialmapping-example.PNG)

在 C++ 中，我們可以訂閱 OnTrackableAdded 委派，以便在 ARTrackedGeometry 可供使用時立即取得。  已更新和移除的事件也有類似的委派：AddOnTrackableUpdatedDelegate_Handle 和 AddOnTrackableRemovedDelegate_Handle。 

![空間錨點範例程式 C++ 代碼](images/unreal-spatialmapping-examplecode.PNG)

專案的 build.cs 必須在 PublicDependencyModuleNames 清單中有 "AugmentedReality"，才能包含 “ARBlueprintLibrary.h” 和 “MRMesh” 來檢查 UARTrackedGeometry 的 MRMesh 元件。 

空間對應不是透過 ARTrackedGeometry 呈現的唯一資料類型，因此我們會先檢查 EARObjectClassification 是不是「世界」，以表示這是空間對應幾何圖形。 

## <a name="see-also"></a>另請參閱
* [空間對應](spatial-mapping.md)
