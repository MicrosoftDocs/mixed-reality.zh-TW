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
# <a name="tracking-loss-in-unity"></a>Unity 中的追蹤遺失

當裝置無法在世界中找到自己時, 應用程式就會遇到「追蹤遺失」的情況。 根據預設, Unity 會暫停更新迴圈, 並向使用者顯示開機映射。 重新執行追蹤時, 啟動顯示映射會消失, 且更新迴圈會繼續。

或者, 使用者可以退出宣告設定來手動處理這項轉換。 所有內容在追蹤遺失期間似乎會被鎖定, 如果沒有處理它,

## <a name="default-handling"></a>預設處理

根據預設, 應用程式的更新迴圈以及所有訊息和事件都會在追蹤遺失的期間停止。 此時, 系統會對使用者顯示影像。 若要自訂此映射, 請前往 編輯-> 設定-> 播放程式, 按一下 啟動顯示影像, 然後設定全像攝影追蹤遺失影像。

## <a name="manual-handling"></a>手動處理

若要手動處理追蹤遺失, 您必須移至 **編輯** > **專案設定** >  **播放** >  **, 通用 Windows 平臺設定**  > 索引標籤**啟動顯示影像** > **Windows**全像投影和取消核取 追蹤遺失暫停並顯示影像。 之後, 您必須使用下列指定的 Api 來處理追蹤變更。

**命名空間：**  *UnityEngine.XR.WSA*<br>
**類型：** *WorldManager*

* World Manager 會公開一個事件來偵測遺失/取得的追蹤 (*WorldManager. OnPositionalLocatorStateChanged*) 和屬性以查詢目前的狀態 (*WorldManager 狀態*)。
* 當追蹤狀態不是作用中時, 即使使用者翻譯, 相機也不會在虛擬世界中轉譯。 這表示物件不會再對應到任何實體位置, 而且全部都會顯示為 [已鎖定] 主體。

處理自己的追蹤變更時, 您必須輪詢每個框架的狀態屬性, 或處理*OnPositionalLocatorStateChanged*事件。

### <a name="polling"></a>巡迴

最重要的狀態為*PositionalLocatorState* , 表示追蹤功能完全正常。 任何其他狀態都只會導致主要攝影機的旋轉差異。 例如:

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>處理 OnPositionalLocatorStateChanged 事件

或者, 您也可以更方便地訂閱*OnPositionalLocatorStateChanged*來處理轉換:

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

## <a name="see-also"></a>另請參閱
* [處理 DirectX 中的追蹤遺失](coordinate-systems-in-directx.md#handling-tracking-loss)
