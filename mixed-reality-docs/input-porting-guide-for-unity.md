---
title: 移植指南 Unity 的輸入
description: 了解如何處理在 Unity 中的 Windows Mixed Reality 的輸入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 輸入、 unity 移植
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595726"
---
# <a name="input-porting-guide-for-unity"></a>移植指南 Unity 的輸入

您可以移植到 Windows 混和實境使用兩個方法之一，Unity 的一般 Input.GetButton/GetAxis Api，跨越多個平台或 Windows 特定 XR 您輸入的邏輯。WSA。輸入提供更豐富的資料，專為動作控制站和 HoloLens 實際操作的 Api。

## <a name="general-inputgetbuttongetaxis-apis"></a>一般 Input.GetButton/GetAxis Api

Unity 目前會使用其一般的 Input.GetButton/Input.GetAxis Api 公開的輸入[Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)並[OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)。 如果您的應用程式已經在使用這些 Api 的輸入，這是最簡單的路徑，在 Windows Mixed Reality 中支援動作控制站： 您應該只需要重新對應按鈕與軸在輸入管理員。

如需詳細資訊，請參閱[Unity 按鈕/軸對應表](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)並[常見的 Unity Api 概觀](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。

## <a name="windows-specific-xrwsainput-apis"></a>Windows-specific XR.WSA.Input APIs

如果您的應用程式已建置自訂的輸入的邏輯，每個平台，您可以選擇使用空間輸入的 Windows 特定的 Api 之下**UnityEngine.XR.WSA.Input**命名空間。 這可讓您存取其他資訊，例如位置精確度或的來源類型，可讓您告訴雙手及相隔的控制站上 HoloLens。

如需詳細資訊，請參閱 < [UnityEngine.XR.WSA.Input Api 概觀](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。

## <a name="grip-pose-vs-pointing-pose"></a>指標的姿勢與的底框姿勢

Windows Mixed Reality 支援各種不同的外型規格中的動作控制站，與每個控制站設計不同使用者的手狀位置和 「 轉送 」 方向該應用程式的自然之間關聯性的相對值應該使用指出呈現時控制站。

若要更能代表這些控制站，有兩種您可以進行互動的每個來源的調查會帶來：

* **底框姿勢**，表示偵測到的 HoloLens，一隻手的或翲保存動作控制器的位置。
    * 沈浸式耳機，在此姿勢最適合用來呈現**使用者的手**或是**物件保留在使用者的手**劍或槍等。
    * **抓住位置**:Palm 距心自然，保留控制器時調整左邊或右邊，置中的底框的位置。
    * **抓住方向的右座標軸**:當您完全開啟以形成平坦的 5 手指姿勢手時，光線，一般是您 palm （從左 palm、 從右 palm 回溯順向）
    * **抓住方向的順向軸**:當您關閉您的手部分 （如同保存在控制站）、"forward"tube 透過由非 thumb 手指點光線。
    * **抓住方向的總軸**:隱含的權限和轉送的定義總軸。
    * 您可以透過任一 Unity 的跨銷售商輸入的 API 來存取的底框姿勢 (**[XR。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation**) 或透過 Windows 特定 API (**sourceState.sourcePose.TryGetPosition/Rotation**，要求的底框姿勢)。
* **指標姿勢**，代表向前指的控制站的提示。
    * 此姿勢最適合用於 raycast 時**指向 UI**當您要在其中呈現控制器模型本身。
    * 指標姿勢目前僅透過 Windows 特定的 API (**sourceState.sourcePose.TryGetPosition/Rotation**，要求指標姿勢)。

這些座標會表示在 Unity 的全局座標的姿勢。

## <a name="see-also"></a>另請參閱
* [動作控制站](motion-controllers.md)
* [筆勢和 Unity 中的動作控制站](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植指南](porting-guides.md)
