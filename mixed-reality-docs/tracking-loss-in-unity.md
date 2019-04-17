---
title: 追蹤 Unity 中的遺失
description: 追蹤 Unity 應用程式內遺失的處理。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，追蹤遺失、 追蹤遺失映像
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595714"
---
# <a name="tracking-loss-in-unity"></a>追蹤 Unity 中的遺失

當裝置找不到本身的世界中時，應用程式就會發生 「 追蹤遺失 」。 根據預設，Unity 會暫停更新迴圈，並向使用者顯示開頭顯示畫面影像。 當追蹤重新取得時，開頭顯示畫面影像就會消失，並更新迴圈會繼續。

或者，使用者可以手動處理這項轉換藉由選擇不設定。 所有的內容看起來將成為期間追蹤遺失，如果執行任何動作來處理它，鎖定的主體。

## <a name="default-handling"></a>預設的處理

根據預設，應用程式，以及所有訊息和事件的更新迴圈將停止期間追蹤遺失。 在該相同的時間，會向使用者顯示一個影像。 您可以自訂此映像，方法是移至 編輯-> 設定-> 播放程式中，按一下 啟動顯示映像，並設定全像攝影版的追蹤遺失映像。

## <a name="manual-handling"></a>手動處理

若要以手動方式處理追蹤遺失，您需要前往**編輯** > **專案設定** > **Player**  >  **通用 Windows 平台設定 索引標籤** > **開頭顯示畫面影像** > **Windows 全像攝影版**並取消核取 「 上追蹤遺失暫停並顯示映像". 在那之後，您需要使用下面指定的 Api 來處理追蹤變更。

**命名空間：***UnityEngine.XR.WSA*<br>
**類型：***WorldManager*

* 世界管理員會公開事件，以偵測追蹤遺失/獲得 (*WorldManager.OnPositionalLocatorStateChanged*) 查詢的目前狀態的屬性和 (*WorldManager.state*)
* 不使用中追蹤狀態時，相機不會出現轉譯於虛擬世界中，即使在使用者將轉譯中。 這表示物件將不會再對應到實體的任何位置，而且所有會出現鎖定的主體。

處理您自己的追蹤變更時必須輪詢狀態屬性，每個框架或控制代碼*OnPositionalLocatorStateChanged*事件。

### <a name="polling"></a>輪詢

最重要的狀態是*PositionalLocatorState.Active*表示追蹤會正常運作。 任何其他狀態將會導致主攝影機旋轉的差異。 例如: 

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

或者，更方便，您也可以訂閱*OnPositionalLocatorStateChanged*處理轉換：

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
* [DirectX 中的處理追蹤遺失](coordinate-systems-in-directx.md#handling-tracking-loss)
