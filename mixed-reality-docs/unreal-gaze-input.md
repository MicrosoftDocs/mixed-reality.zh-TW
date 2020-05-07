---
title: Unreal 中的注視輸入
description: 說明如何在 Unreal 中使用注視輸入
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality、全息影像、HoloLens、眼睛追蹤
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835619"
---
# <a name="gaze-input"></a>注視輸入

Windows Mixed Reality 外掛程式不會針對注視輸入提供任何特殊功能。 所有專案都可透過標準 Unreal API 運作。

[Head 注視 API](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a>眼球追蹤

若要使用眼睛追蹤 API，開發人員應該在其 HoloLens 專案設定中啟用「注視輸入」功能。 當應用程式啟動時，使用者會看到下列同意提示

![目視輸入許可權](images/unreal/eye-input-permissions.png)
 
如果使用者提供其許可權，應用程式將會看到眼睛的輸入。 

Unreal 的眼睛追蹤 API 記載在[這裡](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)

眼睛追蹤的技術詳細資料在[這裡](eye-tracking.md)

請注意，特別是針對 Unreal，HoloLens 眼追蹤對於這兩種眼睛都有單一的注視光線。 HoloLens 並不提供 stereoscopic 眼追蹤。
