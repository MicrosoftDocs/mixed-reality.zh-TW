---
title: MRTK 套件
description: 這篇文章描述組成 Microsoft 混合實境 Toollkit 的封裝。
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality，MRTK 元件、 封裝
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596942"
---
# <a name="mrtk-packages"></a>MRTK 套件

混合實境工具組 (MRTK) 是一個提供及支援的混合實境硬體平台元件化的方式來啟用跨平台混合實境應用程式開發的封裝的集合。

有三種 MRTK 套件： 

* [Foundation](#foundation-packages)
* [延伸模組](#extension-packages)
* [Experimental](#experimental-packages)

## <a name="foundation-packages"></a>Foundation 套件

混合實境 Toolkit Foundation 是一組可讓您運用混合實境平台的通用功能的應用程式封裝。 這些封裝是發行和從來源中的程式碼，Microsoft 支援[mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) GitHub 上的分支。

![MRTK Foundation 套件](images/mrtk-foundation.jpg)

*混合的實境 Toolkit Foundation 套件*

MRTK Foundation 所組成：

* [核心封裝](#core-package)
* [平台提供者](#platform-providers)
* [系統服務](#system-services)
* [功能資產](#feature-assets)

下列各節說明每個類別目錄中的封裝類型。

### <a name="core-package"></a>核心封裝

是核心封裝_必要_元件和 je obsazen MRTK foundation 的所有套件作為相依性。

MRTK Core 套件包括：

* [常見的介面、 類別和資料類型](#common-interfaces-clases-and-data-types)
* [MixedRealityToolkit 場景元件](#mixedrealitytoolkit-scene-component)
* [MRTK 標準著色器](#mrtk-standard-shader)
* [Unity 輸入提供者](#unity-input-provider)
* [套件管理](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a>常見的介面、 類別和資料類型

混合實境 Toolkit 核心套件包含所有常見的介面，類別和所有其他元件所使用的資料類型的定義。 強烈建議應用程式，以獨佔方式透過定義的介面，以啟用跨平台的相容性的最高層級存取 MRTK 元件。

#### <a name="mixedrealitytoolkit-scene-component"></a>MixedRealityToolkit 場景元件

MixedRealityToolkit 場景元件是單一的集中式資源管理員的混合實境工具組。 此元件會載入和管理的平台和服務模組的存留時間，並提供存取其組態設定的系統資源。 

#### <a name="mrtk-standard-shader"></a>MRTK 標準著色器

MRTK 標準著色器提供的基礎，幾乎所有 MRTK 所提供的資料。 這個著色器是極富彈性且最佳化的各種 MRTK 支援的平台。 很_高度_建議您的應用程式資料使用 MRTK 標準著色器，以獲得最佳效能。

#### <a name="unity-input-provider"></a>Unity 輸入提供者

Unity 的輸入提供者提供常見遊戲控制器、 觸控式螢幕等 3D 空間滑鼠的輸入裝置的存取權。

#### <a name="package-management"></a>套件管理

_即將推出_

混合實境 Toolkit 核心封裝可讓您探索及管理的選擇性的 foundation、 延伸模組和實驗性 MRTK 封裝。

### <a name="platform-providers"></a>平台提供者

MRTK 平台提供者套件會啟用目標混合實境硬體混合實境工具及平台功能的元件。

支援的平台包括：

* [Windows Mixed Reality](#windows-mixed-reality)
* [OpenVR](#openvr)
* [Windows Voice](#windows-voice)

#### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Windows Mixed Reality 封裝提供適用於 Microsoft HoloLens 和 Windows Mixed Reality 沈浸式裝置的支援。 封裝包含完整的平台支援，包括：

* 為目標的視線
* 手勢
* Windows Mixed Reality 動作控制站
* 空間對應

#### <a name="openvr"></a>OpenVR

OpenVR 套件提供的硬體和平台支援使用 OpenVR 平台的裝置。

#### <a name="windows-voice"></a>Windows 語音

Windows 語音套件會提供 Microsoft Windows 10 裝置上的關鍵字辨識和語音輸入功能的支援。

### <a name="system-services"></a>系統服務

核心平台服務提供系統服務封裝中。 這些套件包含混合實境工具組的預設實作中定義的系統服務介面[core](#core-package)封裝。

MRTK foundation 包含下列的系統服務：

* [界限系統](#boundary-system)
* [診斷系統](#diagnostic-system)
* [輸入的系統](#input-system)
* [空間感知系統](#spatial-awareness-system)
* [空間傳送系統](#teleport-system)

#### <a name="boundary-system"></a>界限系統

MRTK 界限系統提供資料至虛擬實境 playspace。 在系統上的使用者已設定的界限，floor 平面、 矩形 playspace、 追蹤的區域中，和更多功能，可以提供系統。

#### <a name="diagnostic-system"></a>診斷系統

MRTK 診斷系統會提供可在您的應用程式體驗的即時效能資料。 在瀏覽，您可以檢視畫面播放速率、 處理器時間和其他關鍵效能計量，當您使用您的應用程式。

#### <a name="input-system"></a>輸入的系統

MRTK 輸入系統可讓應用程式存取跨平台的方式輸入指定使用者的動作，並將這些動作指派給最適當的按鈕和目標的控制站上的軸。

#### <a name="spatial-awareness-system"></a>空間感知系統

MRTK 空間感知系統可從裝置，例如 Microsoft HoloLens 讓真實世界的環境資料的存取。

#### <a name="teleport-system"></a>空間傳送系統

MRTK 空間傳送系統提供的虛擬實境 locomotion 支援。

### <a name="feature-assets"></a>功能資產

功能資產是以 Unity 資產和指令碼的形式提供的相關功能的集合。 這些功能包括：

* 使用者介面控制項
* 標準資產
* more

## <a name="extension-packages"></a>延伸模組套件

MRTK 延伸模組套件是一個 Microsoft 和社群所撰寫，擴充及增強功能的混合實境工具組封裝的集合。 延伸模組作者將任何必要的相依性的狀態、 標示為相容於混合實境工具組封裝和提供授權和支援陳述式。

延伸模組套件可能會提供新功能和新的平台支援。 經過一段時間，擴充功能，協助與核准的作者，被移轉至 MRTK Foundation，屆時它們會發行並由 Microsoft 支援。

![MRTK 延伸模組套件](images/mrtk-extensions.jpg)

*混合的實境 Toolkit 擴充功能封裝*

## <a name="experimental-packages"></a>實驗性的套件

實驗性的封裝提供航班原型功能、 發行前版本和令人興奮的新想法的能力。 最實驗性套件的目標是要嘗試新的項目，並量測計的客戶感興趣。 許多，原型設計和測試階段完成後，實驗性的套件雖然不是全部，會重新發行為擴充功能。

![MRTK 實驗性套件](images/mrtk-experimental.jpg)

*混合的實境工具組實驗性的套件*

## <a name="conclusion"></a>結論

混合實境工具組封裝和封裝管理系統的設計可讓您火到您的經驗建置功能，而不需要不必要的元件加入至專案的簡單方法。

經過一段時間，會新增並增強在混合實境 Toolkit 中套件管理支援。 如果您有意見反應，或想要參與，請瀏覽[混合實境 Toolkit 專案](https://github.com/Microsoft/MixedRealityToolkit-Unity)GitHub 上。 

## <a name="see-also"></a>另請參閱

* [MixedRealityToolkit-Unity (GitHub)](https://github.com/Microsoft/MixedRealityToolkit-Unity)

