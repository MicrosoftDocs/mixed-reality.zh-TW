---
title: DirectX 開發概觀
description: 建置以 DirectX 為基礎的混合的實境引擎直接使用 Windows Mixed Reality Api。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全像攝影版轉譯，原生、 原生應用程式，WinRT，WinRT 應用程式中，平台 Api、 自訂引擎中, 介軟體
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414378"
---
# <a name="directx-development-overview"></a>DirectX 開發概觀


使用 Windows Mixed Reality 應用程式[全像攝影版的轉譯](rendering.md)，[視線](gaze.md)，[筆勢](gestures.md)，[動作控制器](motion-controllers.md)， [語音](voice-input.md)，並[空間的對應](spatial-mapping.md)Api 建置[混合實境](mixed-reality.md)HoloLens 和耳機沉浸式體驗。 您可以建立混合的實境應用程式使用的 3D 的引擎，例如[Unity](unity-development-overview.md)，或您可以直接撰寫程式碼使用 DirectX 11 或 DirectX 12 Windows Mixed Reality api。 如果您直接利用平台，您將實質上建置您自己的中介軟體或架構。 Windows Api 支援在撰寫的應用程式C++和C#。 如果您選擇使用C#，您的應用程式可以利用[SharpDX](http://sharpdx.org/)開放原始碼軟體程式庫。


支援 Windows Mixed Reality[應用程式的兩種](app-views.md):
* **混合實境應用程式**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)呈現[沈浸式檢視](app-views.md)填滿耳機顯示的使用者。
* **2D 應用程式**(UWP)，使用 DirectX、 XAML 或其他架構來呈現[2D 檢視](app-views.md#2d-views)在家用的 Windows Mixed Reality 平板上。


適用於 DirectX 開發之間的差異[2D 檢視和沈浸式檢視](app-views.md)主要是以全像攝影版相關的轉譯和空間的輸入。 您的 UWP 應用程式[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 應用程式的 HWND 是必要的並會保留主要相同，為執行應用程式可用的 WinRT Api。 不過，您必須使用這些 Api 的不同子集，以善用全像攝影版的功能。 比方說，交換鏈結由全像攝影版 appslications 的系統管理。 您使用 HolographicSpace API，而不是 DXGI[呈現畫面格](rendering-in-directx.md)。

若要開始開發沉浸式應用程式：
* 針對**UWP 應用程式**，[建立新的 UWP 專案使用 Visual Studio 中的範本](creating-a-holographic-directx-project.md)。 根據您的語言**Visual C++** 或**視覺化C#** ，您可以找到下的 UWP 範本**Windows 通用** >  **全像攝影版**。
* 針對**Win32 應用程式**，[從開始*BasicHologram* Win32 範例](creating-a-holographic-directx-project.md#creating-a-win32-project)。

這是適合用來取得您需要將全像攝影版的呈現支援新增至現有的應用程式或引擎的程式碼。 程式碼和概念會在範本中的即時互動式軟體的任何開發人員熟悉的方式。


## <a name="getting-started"></a>使用者入門

下列主題將討論 Windows Mixed Reality 支援加入以 DirectX 為基礎的中介軟體的基本需求：

* [建立全像攝影版的 DirectX 專案](creating-a-holographic-directx-project.md):搭配文件的全像攝影版的應用程式範本會顯示您要用來與裝置，設計成函式時將滑鼠停在頭上導入的特殊需求之間的差異。
* [取得 HolographicSpace](getting-a-holographicspace.md):您必須先建立將提供您的應用程式的 HolographicFrame 代表物件，從中您將轉譯的每個前端位置順序 HolographicSpace。
* [在 DirectX 中呈現](rendering-in-directx.md):因為全像攝影版的交換鏈結都有兩個呈現目標，您必須對您的應用程式呈現的方式進行一些變更。
* [DirectX 中的座標系統](coordinate-systems-in-directx.md):Windows Mixed Reality 學習，並更新其了解世界隨著使用者周圍。 這會提供空間座標系統應用程式會使用有關使用者的周圍環境，包括空間的錨點的原因，以及使用者定義的空間的階段。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>新增混合的實境功能和輸入

若要啟用您的沈浸式 appslication 的使用者最佳體驗，您會想要支援下列的主要建置組塊：

* [DirectX 中的頭部和眼睛目光](gaze-in-directx.md)
* [DirectX 中的手部和運動控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的語音輸入](voice-input-in-directx.md)
* [DirectX 中的空間音效](spatial-sound-in-directx.md)
* [DirectX 中的空間對應](spatial-mapping-in-directx.md)


有其他重要功能，許多的沈浸式應用程式會想要使用的 DirectX 應用程式也會公開：

* [DirectX 中的共用空間錨點](shared-spatial-anchors-in-directx.md)
* [DirectX 中的定位相機](locatable-camera-in-directx.md)
* [DirectX 中的鍵盤、滑鼠及控制器輸入](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>另請參閱
* [應用程式模型](app-model.md)
* [應用程式檢視](app-views.md)
