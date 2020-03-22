---
title: Unity 中的空間音效
description: 從 Unity 場景內的特定3D 點播放空間音效。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間音效、HRTF、會議室大小
ms.openlocfilehash: af3f1486c3e931ad93d7b8960d822653ec740c12
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082036"
---
# <a name="spatial-sound-in-unity"></a>Unity 中的空間音效

此頁面會連結到 Unity 中的空間音效資源。

## <a name="spatializer-options"></a>空間定位器選項
混合現實應用程式的空間定位器選項包括：
* *MS HRTF 空間定位器*。 Unity 提供此做為*Windows Mixed Reality*選用套件的一部分。
  * 這會在較高成本的「單一來源」架構中，于 CPU 上執行。
  * 這是針對與原始 HoloLens 應用程式的回溯相容性而提供的。
* *Microsoft 空間定位器*。 這可從[Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)取得。
  * 這會使用較低成本的「多來源」架構。
  * 在 HoloLens 2 上，這會卸載至硬體加速器。

針對新的應用程式，我們建議*Microsoft 空間定位器*。

## <a name="enable-spatialization"></a>啟用 spatialization

使用[適用于 Unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)來安裝_SpatialAudio 空間定位器 unity_ ，並在專案的音訊設定中選擇 [ **microsoft 空間定位器**]。 然後：
* 將**音訊來源**連結至階層中的物件
* 核取 [**啟用 spatialization** ] 核取方塊
* 將**空間 Blend**滑杆移至 ' 1 '
* 請確定您的開發人員工作站上已啟用空間音訊。 以滑鼠右鍵按一下工作列中的磁片區圖示，並確定 [空間音效] 設定為 [關閉] 以外的專案，即可加以啟用。 若要取得您在 HoloLens 2 上聽到的最佳呈現方式，請選擇 [ **Windows Sonic For 耳機**]。

>[!NOTE]
>如果您在 Unity 中收到錯誤，指出無法載入外掛程式 SpatialAudio，因為遺漏了其中一個相依性，請檢查您的電腦上是否已安裝最新版的[Microsoft Visual C++ ](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)可轉散發套件。

如需詳細資訊，請參閱：
* [Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft 的空間定位器教學課程](unity-spatial-audio-ch1.md)
* [Unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Unity 的空間定位器檔](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>以距離為基礎的衰減
以 Unity 的預設距離為基礎的衰減，其最小距離為1個計量，而最大距離為500計量，而對數 rolloff 為。 這些設定可能適用于您的案例，或者您可能會發現來源的 attenuate 速度太快或太慢。 如需詳細資訊，請參閱：
* 針對建議的設定，[在混合現實中的音效設計](spatial-sound-design.md)。
* [Unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)，以取得有關設定這些曲線的指示。

## <a name="reverb"></a>殘響
根據預設， _Microsoft 空間定位器_會停用空間定位器後的效果。 若要啟用 hrtf 來源的回音和其他效果：
* 將**房間效果傳送層級**元件附加到每個來源
* 調整每個來源的傳送層級曲線，以控制送回給圖形以進行效果處理的音訊增益

如需詳細資訊，請參閱[空間定位器教學課程的第5章](unity-spatial-audio-ch5.md)。

## <a name="unity-spatial-sound-examples"></a>Unity 空間音效範例
如需 Unity 中的空間音效範例，請參閱：
* [MRTK 示範](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Microsoft 空間定位器範例專案](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-steps"></a>後續步驟
* [混合現實中的音效設計](spatial-sound-design.md)
* [Microsoft 的空間定位器教學課程](unity-spatial-audio-ch1.md)

