---
title: 轉譯
description: 全像攝影轉譯可讓您的應用程式在世界各地的確切位置繪製全息圖形，無論是精確地放在實體世界中，或在您建立的虛擬領域中。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 轉譯、全息影像
ms.openlocfilehash: 544e43ced57309cfe2628cbea65d07e94563eb41
ms.sourcegitcommit: 317653cd8500563c514464f0337c1f230a6f3653
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/28/2019
ms.locfileid: "75503816"
---
# <a name="rendering"></a>轉譯

全像攝影轉譯可讓您的應用程式在世界各地的確切位置繪製全息圖形，無論是精確地放在實體世界中，或在您建立的虛擬領域中。 [全息影像](hologram.md)是由音效和光線所組成的物件。 呈現可讓您的應用程式新增光線。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>轉譯</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>全像攝影

「全像攝影」轉譯的關鍵在於知道您是否要轉譯成可讓使用者同時看到實體世界和您的全息影像，或不透明的顯示，像是 Windows Mixed Reality 沉浸式耳機，這會封鎖成為.

具有**查看顯示**的裝置（如[HoloLens](hololens-hardware-details.md)）會將光線新增至世界。 黑色圖元是完全透明的，而較亮的圖元則逐漸不透明。 因為顯示器的光線會從真實世界新增到光線中，所以白色圖元有點半透明。

雖然 stereoscopic 轉譯會針對您的全息影像提供一個深度提示，但新增[接地效果](interaction-fundamentals.md)可協助使用者更輕鬆地看到全息的表面。 其中一個接地的技巧是在附近的表面上新增一條發光，然後針對此光暈呈現陰影。 如此一來，您的陰影似乎會從環境中減去光線。 [空間音效](spatial-sound.md)是另一個非常重要的深度提示，可讓使用者瞭解全息影像的距離和相對位置。

具有不**透明顯示**的裝置（例如[Windows Mixed Reality 沉浸式耳機](immersive-headset-hardware-details.md)）會封鎖世界。 黑色圖元是實心的黑色，而任何其他色彩都會以該色彩顯示給使用者。 您的應用程式會負責轉譯使用者看到的所有內容。 這讓維護持續的重新整理頻率變得更重要，讓使用者有熟悉的體驗。

## <a name="predicted-rendering-parameters"></a>預測的呈現參數

混合現實耳機（HoloLens 和沉浸式耳機）會持續追蹤使用者的前端相對於其周圍的位置和方向。 當您的應用程式開始準備它的下一個畫面時，系統會預測使用者在畫面上出現在顯示器上的哪個位置的未來。 根據這個預測，系統會計算要用於該框架的視圖和投射轉換。 您的應用程式**必須使用這些轉換來產生正確的結果**;如果未使用系統提供的轉換，則產生的影像將不會與真實世界一致，因而導致使用者 discomfort。

請注意，若要精確預測新的框架何時會到達顯示器，系統會持續測量應用程式轉譯管線的有效端對端延遲。 當系統調整為您的轉譯管線長度時，您可以將該管線保持在最短的時間，藉此改善全息顯示的穩定性。

使用 advanced 技術來增強系統預測的應用程式，可以覆寫系統檢視和投射轉換。 這些應用程式仍然必須使用系統提供的轉換作為其自訂轉換的基礎，才能產生有意義的結果。

## <a name="other-rendering-parameters"></a>其他呈現參數

當轉譯框架時，系統會指定您的應用程式應在其中繪製的後置緩衝區視口。 這個區隔通常會小於框架緩衝區的完整大小。 不論視口大小為何，一旦應用程式轉譯框架，系統就會 upscales 影像以填滿整個顯示器。

對於發現本身無法以所需的重新整理速率呈現的應用程式，[可以設定系統轉譯參數](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)來降低記憶體壓力和轉譯成本，代價是增加圖元別名。 您也可以變更後端緩衝區格式，部分應用程式可協助改善記憶體頻寬和圖元輸送量。

要求應用程式轉譯的轉譯截距、解析度和畫面播放速率可能也會從框架變更為框架，而且在左右的外觀上可能會有所不同。 例如，當[混合現實 capture](mixed-reality-capture.md) （MRC）處於作用中狀態，而[相片/視頻相機視圖](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)設定未加入時，可能會以較大的 FOV 或解析度呈現一眼。

針對任何指定的框架，您的應用程式*必須*使用系統所提供的「視圖轉換」、「投射轉換」和「視口解析」來呈現。 此外，您的應用程式絕不能假設任何轉譯或 view 參數都維持不變，從框架到框架都是固定的。 Unity 等引擎會在自己的相機物件中為您處理所有的轉換，讓您的使用者實際移動和系統的狀態一律遵守。 如果您的應用程式允許使用者透過全球進行虛擬移動（例如在遊戲台上使用操縱杆），您可以在移動它的相機上方加入上層的 rig 物件。 這會導致相機反映使用者的虛擬和實體動作。 如果您的應用程式修改系統所提供的 [視圖轉換]、[投射轉換] 或 [視口] 維度，則必須呼叫適當的覆[寫 API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)來通知系統。

為了加強您的全像攝影轉譯，您的應用程式應該提供 Windows 每個畫面格用來呈現的深度緩衝區。 如果您的應用程式確實提供深度緩衝區，則應該具有一致的深度值，並以從相機中的計量表示的深度。 這可讓系統使用您的每個圖元深度資料，在使用者的前端與預測位置稍有些許位移時，能提供更好的穩定內容。 如果您無法提供深度緩衝區，可以提供焦點和一般，定義一個可剪下大部分內容的平面。 如果同時提供深度緩衝區和焦點平面，則系統可能會同時使用這兩者。 特別是，當您的應用程式顯示移動中的全息影像時，同時提供深度緩衝區和包含速度向量的焦點，會很有説明。

如需有關主題的低層級詳細資料，請參閱[在 DirectX 中](rendering-in-directx.md)轉譯一文。

## <a name="holographic-cameras"></a>全像攝影相機

Windows Mixed Reality 引進了全像**攝影攝影機**的概念。 全像攝影攝影機類似于3D 圖形文字中的傳統相機;它們會定義外部（位置和方向）和內建相機屬性。 （例如：，使用 view 欄位來觀看虛擬3D 場景）。不同于傳統3D 攝影機，應用程式不會控制相機的位置、方向和內建屬性。 而是由使用者的移動隱含控制全像攝影攝影機的位置和方向。 使用者的移動會透過「視圖」轉換，以框架逐一轉送至應用程式。 同樣地，相機的內建屬性是由裝置的校正光纖所定義，並透過投射轉換來逐畫面轉送。

一般來說，您的應用程式將會針對單一身歷聲攝影機呈現。 不過，健全的轉譯迴圈將支援多個相機，而且將同時支援 mono 和身歷聲攝影機。 例如，系統可能會要求您的應用程式在使用者啟動[混合現實 capture](mixed-reality-capture.md) （MRC）之類的功能時，從替代的觀點呈現，視問題耳機的形狀而定。 可以支援多個相機的應用程式會藉由[選擇支援](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)的相機[類型](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)來取得它們。

## <a name="volume-rendering"></a>磁片區轉譯

以3D 呈現醫學/Mri 或工程區時，通常會使用[大量](volume-rendering.md)轉譯技術。 這些技術在混合現實中特別有趣，而使用者可以從關鍵角度自然地查看這類磁片區，只要移動其標頭即可。

## <a name="supported-resolutions-on-hololens-1st-gen"></a>HoloLens 上支援的解決方法（第1代）

* 最大的視口大小是[HolographicDisplay](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay)的屬性。 HoloLens 預設會設定為最大的視口大小，也就是720p （1268x720）。
* 您可以藉由在 HolographicCamera 上設定 ViewportScaleFactor 來變更此區大小。 此縮放比例的範圍介於0到1之間。
* HoloLens （第1代）上支援的最小視口大小為50% 的720p，也就是360p （634x360）。 這是0.5 的 ViewportScaleFactor。
* 由於視覺效果降低，因此不建議使用低於540p 的任何專案，但可以用來識別圖元填滿率的瓶頸。

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 上支援的解決方式

* 目前和最大的支援轉譯目標大小是[view](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)設定的屬性。 HoloLens 2 會設定為最大轉譯目標大小，預設為1440x936。
* 應用程式可以藉由呼叫 RequestRenderTargetSize 方法來要求新的轉譯目標大小，藉以變更呈現目標緩衝區的大小。 將會選擇新的轉譯目標大小，以符合或超過要求的呈現目標大小。 此 API 會變更轉譯目標緩衝區的大小，這需要在 GPU 上重新配置記憶體。 這項工作的含意包括：轉譯目標大小可以縮小以減少 GPU 上的記憶體壓力，而且不應該以較高的頻率呼叫此方法。
* 應用程式仍可透過與 HoloLens 1 相同的方式來變更視口大小。 這不會造成 GPU 上的記憶體重新配置，因此可以在較高的頻率變更，但無法用來減少 GPU 上的記憶體壓力。
* HoloLens 2 上支援的最小視口大小是634x412。 這是在使用預設呈現目標大小時，大約0.44 的 ViewportScaleFactor。
* 如果提供的呈現目標大小小於支援的最小視口大小，則會忽略此區縮放比例。
* 由於視覺效果降低，因此不建議使用低於540p 的任何專案，但可以用來識別圖元填滿率的瓶頸。



## <a name="see-also"></a>請參閱
* [全像投影穩定性](hologram-stability.md)
* [DirectX 中的呈現](rendering-in-directx.md)
