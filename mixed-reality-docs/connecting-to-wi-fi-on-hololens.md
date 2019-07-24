---
title: 連接到 HoloLens 上的 Wi-fi
description: 如何使用 HoloLens 連線至無線網際網路的指示, 以及如何識別裝置的 IP 位址。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, 無線, 網際網路, ip, ip 位址
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670120"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>連接到 HoloLens 上的 Wi-fi

HoloLens 包含具備802.11 電源功能、2x2 的 Wi-fi 無線電。 將 HoloLens 連接到 Wi-fi 網路, 類似于將 Windows 10 桌上型電腦或行動裝置連線到 Wi-fi 網路。

![HoloLens Wi-fi 設定](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>在 HoloLens 上連接到 Wi-fi 網路

1. [Bloom](gestures.md#bloom)至 [**開始**] 功能表。
2. 從 [開始] 功能表右邊的 [**所有應用程式**] 清單中, 選取 [**設定**] 應用程式。
3. [**設定**] 應用程式會自動放在您的前方。
4. 選取 [**網路 & 網際網路**]。
5. 確定已開啟 Wi-Fi。
6. 從清單中選取 Wi-fi 網路。
7. 輸入 Wi-fi 網路密碼 (如有需要)。

## <a name="disabling-wi-fi-on-hololens"></a>停用 HoloLens 上的 Wi-fi

### <a name="using-the-settings-app-on-hololens"></a>在 HoloLens 上使用設定應用程式

1. [Bloom](gestures.md#bloom)至 [**開始**] 功能表。
2. 從 [開始] 功能表右邊的 [**所有應用程式**] 清單中, 選取 [**設定**] 應用程式。
3. [**設定**] 應用程式會自動放在您的前方。
4. 選取 [**網路 & 網際網路**]。
5. 選取 [Wi-fi 滑杆] 開關, 將其移至 [關閉] 位置。 這會關閉 Wi-fi 無線電的 RF 元件, 並停用 HoloLens 上的所有 Wi-fi 功能。 

    >[!WARNING]
    >當停用 Wi-fi 無線電時, HoloLens 將無法自動載入您的[空間](environment-considerations-for-hololens.md#WiFi fingerprint considerations)。
    
6. 將滑杆切換至 [開啟] 位置, 以開啟 Wi-fi 無線電並在 Microsoft HoloLens 上還原 Wi-fi 功能。 選取的 Wi-fi 無線電狀態 (「開啟」) 將會在重新開機時保存。

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>如何確認您已連線到 Wi-fi 網路

1. [Bloom](gestures.md#bloom)以顯示 [**開始**] 功能表。
2. 查看 [開始] 功能表左上方的 [Wi-fi 狀態]。 隨即會顯示 Wi-fi 的狀態和連線網路的 SSID。

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>識別您的 HoloLens 在 Wi-fi 網路上的 IP 位址

### <a name="using-the-settings-app"></a>使用設定應用程式

1. [Bloom](gestures.md#bloom)至 [**開始**] 功能表。
2. 從 [開始] 功能表右邊的 [**所有應用程式**] 清單中, 選取 [**設定**] 應用程式。
3. [**設定**] 應用程式會自動放在您的前方。
4. 選取 [**網路 & 網際網路**]。
5. 在 [可用的 Wi-fi 網路] 清單下方向下流覽, 然後選取 [**硬體**內容]。

    ![Wi-fi 設定中的硬體屬性](images/wifi-hololens-hwdetails.jpg)

IP 位址會顯示在 [ **IPv4 位址**] 旁。

### <a name="using-cortana"></a>使用 Cortana

說「*嗨, Cortana, 我的 IP 位址是什麼？* 」 而 Cortana 會顯示並讀取您的 IP 位址。

### <a name="using-windows-device-portal"></a>使用 Windows 裝置入口網站

1. 在您電腦上的網頁瀏覽器中開啟[裝置入口網站](using-the-windows-device-portal.md#networking)。
2. 流覽至 [**網路**] 區段。

您的 IP 位址和其他網路資訊將會顯示在該處。 這個方法可讓您輕鬆地在開發電腦上複製和貼上 IP 位址。
