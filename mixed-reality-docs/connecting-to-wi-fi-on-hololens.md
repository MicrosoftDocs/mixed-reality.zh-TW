---
title: 連線至 Wi-fi HoloLens 上
description: 如何使用 HoloLens 無線網際網路連線以及如何找出裝置的 IP 位址的指示。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens、 wifi、 無線網路、 網際網路、 ip、 ip 位址
ms.openlocfilehash: 0440c3dad48d73db51e7d730e79d6eb1e74a5694
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596691"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>連線至 Wi-fi HoloLens 上

HoloLens 包含 802.11ac-2 的 Wi-fi 電台的能力，2x。 連線到 Wi-fi 網路的 HoloLens 是類似於 Windows 10 Desktop 或行動裝置版裝置連接到 Wi-fi 網路。

![HoloLens Wi-fi 設定](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>連線到 Wi-fi 網路上 HoloLens

1. [Bloom](gestures.md#bloom)要**啟動**功能表。
2. 選取 **設定**應用程式從開始，或從**所有應用程式**右邊的 開始 功能表上的清單。
3. **設定**應用程式將會自動放置您面前。
4. 選取 **網路和網際網路**。
5. 確定已開啟 Wi-Fi。
6. 從清單中選取 Wi-fi 網路。
7. （如有需要），請輸入中的 Wi-fi 網路密碼。

## <a name="disabling-wi-fi-on-hololens"></a>停用 HoloLens 上的 Wi-fi

### <a name="using-the-settings-app-on-hololens"></a>使用 HoloLens 上的 設定 應用程式

1. [Bloom](gestures.md#bloom)要**啟動**功能表。
2. 選取 **設定**應用程式從開始，或從**所有應用程式**右邊的 開始 功能表上的清單。
3. **設定**應用程式將會自動放置您面前。
4. 選取 **網路和網際網路**。
5. 選取 [Wi-fi] 滑桿切換，將它移到 「 關閉 」 位置。 這會關閉 Wi-fi 無線通訊的 RF 元件，並停用 HoloLens 上的所有 Wi-fi 功能。 

    >[!WARNING]
    >HoloLens 將無法自動載入您[空格](environment-considerations-for-hololens.md#spaces)Wi-fi 選項已停用。
    
6. 移動滑桿切換到開啟的 Wi-fi 選項和還原 Microsoft HoloLens 上的 Wi-fi 功能的 「 開啟 」 位置。 選取的 Wi-fi 選項狀態 (「 On 」 的 「 關閉 」) 會在重新啟動期間保存。

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>如何確認您連接到 Wi-fi 網路

1. [Bloom](gestures.md#bloom)即可啟動**啟動**功能表。
2. 看看右上方的 Wi-fi 狀態的 開始 功能表。 會顯示狀態的 Wi-fi 和連線的網路 SSID。

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>識別您 HoloLens Wi-fi 網路上 IP 位址

### <a name="using-the-settings-app"></a>使用 [設定] 應用程式

1. [Bloom](gestures.md#bloom)要**啟動**功能表。
2. 選取 **設定**應用程式從開始，或從**所有應用程式**右邊的 開始 功能表上的清單。
3. **設定**應用程式將會自動放置您面前。
4. 選取 **網路和網際網路**。
5. 向下捲動至下方清單中可用的 Wi-fi 網路，然後選取**硬體屬性**。

    ![在 Wi-fi 設定的硬體屬性](images/wifi-hololens-hwdetails.jpg)

將旁邊顯示的 IP 位址**IPv4 位址**。

### <a name="using-cortana"></a>使用 Cortana

說出 「*嘿 Cortana，我的 IP 位址是什麼？*" 和 Cortana 將會顯示和讀取您的 IP 位址。

### <a name="using-windows-device-portal"></a>使用 Windows Device Portal

1. 開啟[裝置入口網站](using-the-windows-device-portal.md#networking)網頁瀏覽器，在您的電腦上。
2. 瀏覽至**網路**一節。

您的 IP 位址和其他網路資訊會在該處顯示。 這個方法允許為簡單的複製和貼上的開發電腦上的 IP 位址。
