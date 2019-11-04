---
title: Unity 中的焦點點
description: 藉由設定焦點點，手動調整 Unity 中的全息影像穩定性
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，焦點點，焦點平面，穩定平面，穩定點，reprojection，LSR，深度緩衝區
ms.openlocfilehash: d48f6f1878a68a17be263f10b809229dc2705c58
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435420"
---
# <a name="focus-point-in-unity"></a>Unity 中的焦點點

**命名空間：** *UnityEngine. XR. WSA*<br>
**類型**： *HolographicSettings*

您可以將[焦點](hologram-stability.md#reprojection)設定為提供 HoloLens 提示，告訴您如何在目前顯示的全息影像上，最佳執行穩定。

如果您想要在 Unity 中設定焦點，則必須使用*HolographicSettings. SetFocusPointForFrame （）* 來設定每個畫面格。 如果沒有為框架設定焦點，則會使用預設的穩定平面。

> [!NOTE]
> 根據預設，新的 Unity 專案會設定 [啟用深度緩衝區共用] 選項。  使用此選項時，在沉浸式桌面耳機上執行的 Unity 應用程式或執行 Windows 10 四月份2018更新（RS4）或更新版本的 HoloLens 會將您的深度緩衝區提交至 Windows，以自動將您的「影像」穩定性優化，而不需要您的應用程式指定焦點點：
> * 在沉浸式桌面耳機上，這會啟用以圖元為基礎的深度 reprojection。
> * 在執行 Windows 10 2018 年4月更新（含）以後版本的 HoloLens 上，這會分析深度緩衝區，以自動挑選最佳穩定平面。
>
> 這兩種方法都應該提供更好的影像品質，而不需要由您的應用程式進行明確的工作，就能選取每個畫面  請注意，如果您手動提供焦點，這會覆寫上述的自動行為，而且通常會減少全息影像的穩定性。  一般而言，當您的應用程式在尚未更新為 Windows 10 2018 年4月更新的 HoloLens 上執行時，您應該只指定手動焦點點。

### <a name="example"></a>範例

有許多方式可設定焦點，如*SetFocusPointForFrame*靜態函式上提供的多載所建議。 以下是簡單的範例，可將焦點平面設定為每個框架所提供的物件：

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

請注意，上述的簡單程式碼可能會在焦點物件最後出現在使用者後方時，減少全息影像的穩定性。  這就是為什麼您通常應該設定「啟用深度緩衝區共用」，而不是手動指定焦點。

### <a name="see-also"></a>請參閱
* [穩定平面](hologram-stability.md#reprojection)
