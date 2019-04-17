---
title: 在應用程式內購買
description: 在應用程式內購買支援混合的實境應用程式，還有一些工作，來設定它們。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 在應用程式內購買 hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595780"
---
# <a name="in-app-purchases"></a>在應用程式內購買

HoloLens，支援應用程式內購買，但有一些工作，來設定它們。

若要使用中的應用程式購買功能，您必須：
* 建立 XAML [2D 檢視](app-views.md)顯示為靜態圖像
* 切換至該啟動離開沈浸式檢視的位置
* Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

此 API 會顯示內建 Windows OS 快顯視窗會顯示在應用程式內購買名稱、 描述和價格。 接著，使用者可以選擇購買選項。 完成此動作之後，應用程式都必須顯示 UI 讓使用者切換回其[沈浸式檢視](app-views.md)。

針對以桌面為基礎的 「 Windows Mixed Reality 沈浸式耳機為目標的應用程式，它不需要手動切換到 [XAML] 檢視，然後再呼叫 RequestProductPurchaseAsync API。
