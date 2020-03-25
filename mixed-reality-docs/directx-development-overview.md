---
title: 原生開發總覽
description: 直接使用 Windows Mixed Reality Api，建立以 DirectX 為基礎的混合現實引擎。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全像攝影轉譯，原生，原生應用程式，WinRT，WinRT 應用程式，平臺 Api，自訂引擎，中介軟體
ms.openlocfilehash: 5c61739ea6c90b4547c5c9927cf2129304650926
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80159993"
---
# <a name="native-development-overview"></a>原生開發總覽

Windows Mixed Reality 應用程式使用下列 Api 來打造適用于 HoloLens 和其他沉浸式耳機的[混合現實](mixed-reality.md)體驗：

 - [全像攝影的呈現](rendering.md)
 - [目光](gaze-and-commit.md)
 - [#](gaze-and-commit.md#composite-gestures)
 - [動作控制器](motion-controllers.md)
 - [語音](voice-input.md)
 - [空間對應](spatial-mapping.md)

您可以使用3D 引擎（例如[Unity](unity-development-overview.md)）來建立混合現實應用程式。 或者，您可以使用 DirectX 11 或 DirectX 12，直接將程式碼撰寫到 Windows Mixed Reality Api。 如果您直接運用平臺，基本上就是建立自己的中介軟體或架構。 Windows Api 支援以C++和C#撰寫的應用程式。 如果您使用C#，您的應用程式可以運用[SharpDX](https://sharpdx.org/)開放原始碼軟體程式庫。

Windows Mixed Reality 支援[兩種類型的應用程式](app-views.md)：
* **混合現實應用程式**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)或[OpenXR api](openxr.md)將[沉浸式視圖](app-views.md)呈現給填滿耳機顯示的使用者
* 使用 DirectX、XAML 或其他架構的**2d 應用程式**（UWP），在 Windows Mixed Reality 首頁的平板上呈現[2d 視圖](app-views.md#2d-views)

[2d 視圖和沉浸式視圖](app-views.md)的 DirectX 開發之間的差異主要涉及全像攝影轉譯和空間輸入。 您的 UWP 應用程式的[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 應用程式的 HWND 是必要的，而且兩者的存留程度都相同。 適用于您應用程式的 WinRT Api 也是如此。 但您必須使用這些 Api 的不同子集，才能利用全像攝影功能。 例如，現有的 swapchain 和框架是由系統為全像攝影應用程式所管理，以便啟用姿勢預測的框架迴圈。

## <a name="get-started-with-openxr"></a>開始使用 OpenXR

您可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 沉浸式耳機桌面上進行開發。  如果您沒有頭戴式裝置的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

若要開始開發 HoloLens 2 或沉浸式 Windows Mixed Reality 耳機的 OpenXR 應用程式，請參閱[如何開始使用 OpenXR 開發](openxr-getting-started.md)。

## <a name="get-started-with-winrt"></a>開始使用 WinRT

若要開始開發沉浸式應用程式：
* 針對**UWP 應用程式**，請[使用 Visual Studio 中的範本來建立新的 uwp 專案](creating-a-holographic-directx-project.md)。 根據您的語言、視覺C++效果或C#視覺效果，尋找**Windows 通用** > 全像攝影**版中的**UWP 範本。
* 針對**win32 應用程式**，請[從*BasicHologram* Win32 範例開始](creating-a-holographic-directx-project.md#creating-a-win32-project)。

這個步驟很適合用來取得您所需的程式碼，以便將全像攝影轉譯支援新增至現有的應用程式或引擎。 程式碼和概念在範本中的呈現方式，對任何即時互動式軟體發展人員而言都很熟悉。

下列主題說明當您將 Windows Mixed Reality 支援新增至以 DirectX 為基礎的中介軟體時的基本需求。

* 建立全像的[DirectX 專案](creating-a-holographic-directx-project.md)：與檔結合的全像攝影應用程式範本會顯示與您習慣的差異。 它也會描述裝置的特殊需求，而此裝置的設計可在您的前端上運作。
* [取得 HolographicSpace](getting-a-holographicspace.md)：您必須先建立 HolographicSpace，為應用程式提供一系列 HolographicFrame 物件，代表您將呈現的每個標頭位置。
* [在 DirectX 中](rendering-in-directx.md)轉譯：因為全像攝影 swapchain 有兩個轉譯目標，所以您必須對應用程式轉譯的方式進行一些變更。
* [在 DirectX 中協調系統](coordinate-systems-in-directx.md)： Windows Mixed Reality 會在使用者逐步解說的同時，學習並更新其對世界的瞭解。 這會提供應用程式使用的空間座標系統，以因應使用者的周圍的原因，包括空間錨點和使用者定義的空間階段。

## <a name="add-mixed-reality-capabilities-and-inputs"></a>新增混合現實功能和輸入

若要為您的沉浸式應用程式使用者提供最佳的體驗，您應該支援下列重要的建立區塊：

* [DirectX 中的頭部和眼睛目光](gaze-in-directx.md)
* [DirectX 中的手部和運動控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的語音輸入](voice-input-in-directx.md)
* [空間音效](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [DirectX 中的空間對應](spatial-mapping-in-directx.md)

這些是許多沉浸式應用程式所使用的其他重要功能，也會公開給 DirectX 應用程式：

* [DirectX 中的共用空間錨點](shared-spatial-anchors-in-directx.md)
* [DirectX 中的鍵盤、滑鼠及控制器輸入](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a>另請參閱
* [應用程式模型](app-model.md)
* [應用程式檢視](app-views.md)
