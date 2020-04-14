---
title: 將 XAML 與全像的 DirectX 應用程式搭配使用
description: 說明在 2D XAML 視圖和 DirectX 應用程式中的沉浸式視圖之間切換的影響，以及如何有效率地使用 XAML 視圖和沉浸式視圖。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: windows mixed reality，UWP，應用程式視圖管理，xaml，鍵盤，逐步解說，DirectX
ms.openlocfilehash: 4136e674cfc1737dba9dcc1f70bd68edd4e95a41
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277956"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>將 XAML 與全像的 DirectX 應用程式搭配使用

本主題說明在 DirectX 應用程式中切換[2D XAML 視圖和沉浸式](app-views.md)流覽的影響，以及如何有效率地使用 XAML 視圖和沉浸式視圖。

## <a name="xaml-view-switching-overview"></a>XAML 視圖切換總覽

在 HoloLens 上，通常會顯示 2D XAML 視圖的一般沉浸式應用程式必須先初始化該 XAML 視圖，然後立即從該處切換到沉浸式視圖。 這表示在您的應用程式可以執行任何動作之前，會載入 XAML。 如此一來，啟動時間會變小，而且 XAML 會在應用程式進程位於背景時繼續佔用記憶體空間;啟動延遲和記憶體使用量的數量取決於您的應用程式在切換到原生視圖之前，會如何處理 XAML。 如果您沒有在 XAML 中執行任何動作，請先啟動程式碼，除非開始您的沉浸式視圖，否則影回應該很小。 此外，由於您的全像攝影轉譯是直接對沉浸式視圖進行，因此您可以避免任何有關該呈現的 XAML 相關限制。

請注意，記憶體使用量會計入 CPU 和 GPU。 Direct3D 11 可以交換虛擬圖形記憶體，但它可能無法交換部分或所有的 XAML GPU 資源，而且可能會有明顯的效能影響。 不論是哪一種方式，都不會載入您的應用程式所需的任何 XAML 功能，並提供更好的體驗。

## <a name="xaml-view-switching-workflow"></a>XAML 視圖切換工作流程

直接從 XAML 進入沉浸式模式之應用程式的工作流程，如下所示：
* 應用程式會在 2D XAML 視圖中啟動。
* 應用程式的 XAML 啟動順序會偵測目前的系統是否支援全像攝影轉譯：
* 若是如此，應用程式會建立沉浸式視圖，並立即將其帶到前景。 Windows Mixed Reality 裝置上不需要的任何專案都會略過 XAML 載入，包括 XAML 視圖中的任何轉譯類別和資產載入。 如果應用程式使用 XAML 來進行鍵盤輸入，則仍應建立該輸入頁面。
* 如果沒有，XAML 視圖可以照常繼續業務。

## <a name="tip-for-rendering-graphics-across-both-views"></a>跨兩個視圖呈現圖形的秘訣

如果您的應用程式需要在 DirectX 中為 Windows Mixed Reality 的 XAML 視圖實行某種程度的轉譯，最好的做法是建立一個可與這兩個視圖搭配使用的轉譯器。 轉譯器應該是一個可以從兩個視圖存取的實例，而且應該能夠在2D 和全像攝影轉譯之間切換。 如此一來，就只會載入一次 GPU 資產，這可減少載入時間、記憶體影響，以及切換視圖時要交換的資源量。
