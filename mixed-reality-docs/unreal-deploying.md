---
title: 在 Unreal 中部署至裝置
description: 在 Unreal 至 HoloLens 2 中部署至裝置的指南
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal，Unreal Engine 4，UE4，HoloLens，HoloLens 2，mixed reality，部署至裝置，電腦，檔
appliesto:
- HoloLens 2
ms.openlocfilehash: 2d0cd67db79c1970695334d826fbbaf0f2f92ec0
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408176"
---
# <a name="deploy-to-device-in-unreal"></a>在 Unreal 中部署至裝置

## <a name="overview"></a>概觀
有兩種方式可將 Unreal 應用程式部署至 HoloLens 2： 
* 直接從 Unreal 編輯器
* 作為透過裝置入口網站上傳的套件

這兩個選項都需要您設定 HoloLens，才能使用[裝置入口網站](using-the-windows-device-portal.md)進行開發。 

## <a name="deploying-to-device-from-the-unreal-editor"></a>從 Unreal 編輯器部署至裝置

1. 按一下 [**啟動**] 按鈕旁邊的下拉式箭號。 一開始，HoloLens 裝置選項會呈現灰色。

![啟動下拉式清單選項](images/unreal/launch-dropdown.png)

2. 開啟 [ **Device Manager**]。 請注意，您的 HoloLens 不會自動出現在裝置清單中。

3. 展開 [**新增未列出的裝置**] 區段。

4. 選取 [ **HoloLens** ] 做為您的**平臺**。

5. 輸入您裝置的 IP 位址和埠資訊，並以冒號分隔作為裝置識別碼。 例如，"127.0.0.1： 10080" （透過 USB 連接時）。 使用您的裝置入口網站使用者名稱和密碼認證。

6. 點擊 [**新增**]，然後關閉 [裝置管理員]。 
    * 如果發生錯誤（例如位址、使用者名稱或密碼錯誤），則會將訊息列印到輸出記錄檔。

![新增未列出的裝置](images/unreal/add-unlisted-device.png)

7. 再次按一下 [**啟動**] 按鈕旁的下拉式箭號，此時您應該會看到剛才新增的 HoloLens 裝置。 選取要建立並部署至 HoloLens 的 HoloLens 裝置。 

>[!NOTE]
>建立裝置可能需要重新編譯著色器（特別是在第一次執行時）-這可能需要一些時間。 請勿讓裝置進入睡眠狀態，直到應用程式執行（您可能必須磨損）。 否則，著色器編譯將會失敗！

## <a name="deploying-to-device-via-device-portal"></a>透過裝置入口網站部署至裝置

您可以在消費者入門 with Unreal 教學課程系列的最後一節中，找到有關[封裝和部署應用程式](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)的詳細指示。
