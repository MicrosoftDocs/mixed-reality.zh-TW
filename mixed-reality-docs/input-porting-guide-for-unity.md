---
title: 適用于 Unity 的輸入移植指南
description: 瞭解如何在 Unity 中處理 Windows Mixed Reality 的輸入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 輸入、unity、移植
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515492"
---
# <a name="input-porting-guide-for-unity"></a>適用于 Unity 的輸入移植指南

您可以使用下列兩種方法之一, 將您的輸入邏輯移植到 Windows Mixed Reality: Unity 的一般輸入。跨多個平臺的 GetButton/GetAxis Api, 或 Windows 特定的 XR。WSA.輸入 Api, 專門為運動控制器和 HoloLens 提供更豐富的資料。

## <a name="general-inputgetbuttongetaxis-apis"></a>一般輸入. GetButton/GetAxis Api

Unity 目前使用其一般輸入. GetButton/GetAxis Api 來公開[OCULUS GO SDK](https://docs.unity3d.com/Manual/OculusControllers.html)和[OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)的輸入。 如果您的應用程式已經使用這些 Api 來進行輸入, 這是在 Windows Mixed Reality 中支援動作控制器的最簡單路徑: 您應該只需要在輸入管理員中重新對應按鈕和軸。

如需詳細資訊, 請參閱[Unity 按鈕/軸對應表](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)和[通用 Unity api 的總覽](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。

## <a name="windows-specific-xrwsainput-apis"></a>Windows 特定的 XR。WSA.輸入 Api

如果您的應用程式已經為每個平臺建立自訂輸入邏輯, 您可以選擇使用**UnityEngine. XR**命名空間下的 Windows 特定空間輸入 api。 這可讓您存取其他資訊, 例如位置精確度或來源種類, 讓您可以在 HoloLens 上區分手和控制器。

如需詳細資訊, 請參閱[UnityEngine. XR 的總覽](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。

## <a name="grip-pose-vs-pointing-pose"></a>抓握姿勢與指標姿勢

Windows Mixed Reality 支援各種外型規格中的動作控制器, 而每個控制器的設計都不同于使用者的手位置與自然「正向」方向之間的關聯性, 應用程式應該在呈現時使用指標控制器.

為了更清楚地表示這些控制器, 您可以針對每個互動來源進行兩種類型的調查:

* **抓握姿勢**, 代表 HoloLens 偵測到的掌上的位置, 或用來存放運動控制器的 palm。
    * 在沉浸式耳機上, 這項姿勢最適合用來呈現使用者的**手**或**物件**(例如寶劍或機槍)。
    * **抓握位置**:自然地保留控制器時的 palm 距心, 會向左或右調整以置中的位置。
    * **抓握方向的右軸**:當您完全開啟手來形成一般的5方姿勢時, 您的 palm 的光線 (從左 palm 向前, 向右的 palm 往後)
    * **抓握方向的正向軸**:當您關閉手中的部分 (如同按住控制器) 時, 就會以非拇指手指所形成的電子管「轉送」光線。
    * **抓握方向的向上軸**:右邊和後向定義所隱含的向上軸。
    * 您可以透過 Unity 的跨廠商輸入 API (XR) 來存取底框姿勢 **[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/輪替**) 或透過 Windows 特定 API (**SourceState. SourcePose. TryGetPosition/旋轉**, 要求底框姿勢)。
* **指標姿勢**, 代表指向轉寄的控制器提示。
    * 當您在呈現控制器模型本身時, 當**指向 UI**時, 最好使用此姿勢來進行 raycast。
    * 目前, 指標姿勢只能透過 Windows 特定 API (**sourceState. sourcePose. TryGetPosition/旋轉**, 要求指標姿勢) 來使用。

這些姿勢座標全都以 Unity world 座標表示。

## <a name="see-also"></a>另請參閱
* [運動控制器](motion-controllers.md)
* [Unity 中的筆勢和運動控制器](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. 輸入](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植指南](porting-guides.md)
