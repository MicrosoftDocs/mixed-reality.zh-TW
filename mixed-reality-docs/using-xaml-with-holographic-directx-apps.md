---
title: 使用全像攝影版的 DirectX 應用程式中的 XAML
description: 說明 2D XAML 檢視與您的 DirectX 應用程式，以及如何有效率地使用 [XAML] 檢視和沈浸式檢視中的沈浸式檢視之間切換的影響。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: windows mixed 的 reality，UWP 應用程式檢視管理、 xaml、 鍵盤、 逐步解說中，DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591355"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>使用全像攝影版的 DirectX 應用程式中的 XAML

本主題說明切換的影響[2D 的 XAML 檢視和沈浸式檢視](app-views.md)DirectX 應用程式，以及如何有效率地使用 [XAML] 檢視和沈浸式檢視。

## <a name="xaml-view-switching-overview"></a>XAML 檢視切換概觀

在 HoloLens，必須先初始化該 XAML 檢視更新的版本可能會顯示 2D 的 XAML 檢視通常沈浸式應用程式，並將其從該處立即切換的沈浸式檢視中。 這表示您的應用程式可以執行任何動作之前，會載入 XAML。 如此一來，會有少量增加您的啟動時間，以及 XAML 會繼續佔用您的應用程式處理序中的記憶體空間，而它位於背景;啟動延遲時間和使用方式取決於您的應用程式會使用 XAML 之前切換到原生檢視的記憶體數量。 如果您在程式碼一開始啟動您的沈浸式檢視，只不過您 XAML 開始執行任何動作，影響應該很小。 此外，因為您全像攝影版的轉譯直接為了沈浸式檢視，您可避免該轉譯任何 XAML 相關限制。

請注意，CPU 和 GPU 計算的記憶體使用量。 Direct3D 11 是能夠交換虛擬圖形記憶體，它可能無法空出部分或所有 XAML GPU 的資源，但可能會有明顯的效能衝擊。 無論如何，未載入任何 XAML 功能不需要將保留更多空間給您的應用程式，並提供更好的體驗。

## <a name="xaml-view-switching-workflow"></a>切換工作流程的 XAML 檢視

工作流程的應用程式當機時會直接從 XAML 至沈浸式模式，就像這樣：
* 應用程式會啟動在 2D 的 [XAML] 檢視中。
* 應用程式的 XAML 啟動順序偵測到目前的系統是否支援全像攝影版的轉譯：
* 若是如此，應用程式建立的沈浸式檢視，並立即將它帶到前景。 XAML 載入 Windows Mixed Reality 在裝置上，包括任何呈現類別和載入 XAML 檢視中的資產會略過不必要的項目。 如果應用程式使用 XAML 的鍵盤輸入，則應該仍會建立該輸入的頁面。
* 如果沒有，則 [XAML] 檢視可以像往常一樣繼續與企業。

## <a name="tip-for-rendering-graphics-across-both-views"></a>在這兩個檢視提示轉譯圖形

如果您的應用程式需要在 DirectX 中實作一定程度，XAML 檢視中 Windows Mixed Reality，最好是轉譯的建立一個可以使用這兩個檢視的轉譯器。 轉譯器應該是您可以從這兩個檢視中，存取的一個執行個體，它應該能夠轉譯 2D 和全像攝影版之間切換。 如此一來 GPU 資產只能載入一次-這會減少載入時間、 記憶體衝擊，以及切換檢視時要交換的資源數量。
