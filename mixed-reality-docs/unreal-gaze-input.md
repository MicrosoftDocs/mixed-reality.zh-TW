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
# <a name="gaze-input"></a>注視輸入

## <a name="overview"></a>概觀

[Windows Mixed Reality 外掛程式](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)並未提供任何內建的監看式輸入功能，但 HoloLens 2 確實支援眼追蹤。 實際的追蹤功能是由 Unreal 的前端**裝載的顯示**和**眼睛追蹤**api 所提供，包括：

- 裝置資訊
- 追蹤感應器
- 方向和位置
- 裁剪窗格
- 注視資料和追蹤資訊

您可以在 Unreal 的前端[裝載的顯示](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html)和[眼睛追蹤](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html)檔中找到完整的功能清單。

除了 Unreal Api 之外，也請查看 HoloLens 2 的[眼睛互動](eye-gaze-interaction.md)相關檔，並閱讀[hololens 2 眼追蹤](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)的運作方式。

> [!IMPORTANT]
> 只有 HoloLens 2 才支援眼睛追蹤。

## <a name="enabling-eye-tracking"></a>啟用眼睛追蹤
您必須先在 HoloLens 專案設定中啟用注視輸入，才能使用任何 Unreal 的 Api。 當應用程式啟動時，您會看到如下列螢幕擷取畫面所示的同意提示。

- 選取 **[是]** 以設定許可權，並取得注視輸入的存取權。 如果您需要隨時變更此設定，可以在 [**設定**] 應用程式中找到。

![目視輸入許可權](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> Unreal 中的 HoloLens 眼追蹤只有兩個眼睛的單一注視光線，而不是 stereoscopic 追蹤所需的兩張光線，這是不支援的。

這就是您開始在 Unreal 中新增注視輸入至 HoloLens 2 應用程式所需的所有設定。 您可以在下列連結中找到關於注視輸入的詳細資訊，以及它如何影響混合現實中的使用者。 建立您的互動體驗時，請務必考慮這些資訊。

## <a name="see-also"></a>另請參閱
* [校正](calibration.md)
* [舒適度](comfort.md)
* [目光和行動](gaze-and-commit.md)
* [語音輸入](voice-design.md)
