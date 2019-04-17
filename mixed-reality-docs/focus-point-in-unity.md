---
title: 在 Unity 中的焦點
description: 以手動方式設定焦點調整在 Unity 的全像穩定性
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 焦點、 焦點平面、 穩定平面、 穩定點、 reprojection、 LSR、 深度緩衝區
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597038"
---
# <a name="focus-point-in-unity"></a>在 Unity 中的焦點

**命名空間：***UnityEngine.XR.WSA*<br>
**類型**：*HolographicSettings*

[專注點](hologram-stability.md#stabilization-plane)可以設為提供 HoloLens 有關如何以最適合目前在全像投影執行穩定的提示所顯示。

如果您想要將焦點設定在 Unity 中，它必須設定使用每框架*HolographicSettings.SetFocusPointForFrame()*。 如果未設定焦點的框架，將會使用預設穩定平面。

> [!NOTE]
> 根據預設，新的 Unity 專案已設定的 [啟用深度緩衝區共用] 選項。  使用此選項，在沉浸式桌面耳機或執行 Windows 的 HoloLens 上執行的 Unity 應用程式 10 April 2018 Update (RS4) 或更新版本會送出您的深度緩衝區，以自動將最佳化全像穩定性，而您的應用程式指定的 Windows焦點：
> * 在沉浸式桌面耳機，這可讓每一像素深度型 reprojection。
> * HoloLens 上執行 Windows 10 April 2018 Update 或更新版本中，這將會分析自動挑選最佳的穩定平面深度緩衝區。
>
> 兩種方法應該提供更好的影像品質，而不需要明確的工作由您的應用程式，以選取婧鎏鶗懘每個畫面格。  請注意，如果您以手動方式提供婧鎏鶗懘，將會覆寫自動上面所述的行為，通常會減少闀穩定性。  一般而言，您才應該指定手動鶗懘尚未更新至 Windows HoloLens 上執行您的應用程式時 10 April 2018 Update。

### <a name="example"></a>範例

有許多方法可設定焦點，所提供的多載建議*SetFocusPointForFrame*靜態函式。 下列是將焦點平面設定所提供的物件為每個畫面的簡單範例：

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

請注意，上述的簡單程式碼可能會得到減少闀穩定性，如果具有焦點的物件最後背後的使用者。  這就是為什麼一般來說，您應該設定 「 啟用深度緩衝區共用 」 而不是以手動方式指定婧鎏鶗懘。

### <a name="see-also"></a>另請參閱
* [穩定平面](hologram-stability.md#stabilization-plane)
