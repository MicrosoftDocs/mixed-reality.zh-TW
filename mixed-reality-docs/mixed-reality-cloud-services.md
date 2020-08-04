---
layout: LandingPage
title: 混合實境雲端服務
description: 混合實境雲端服務資源。
author: hferrone
ms.author: v-haferr
ms.date: 06/5/2020
ms.topic: overview
ms.localizationpriority: high
keywords: 混合實境, 開發, 開發, HoloLens, 雲端服務
ms.openlocfilehash: 26c5f91eab2b39fbd809010ab0ac738d81dff854
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390215"
---
# <a name="cloud-services"></a>雲端服務

## <a name="overview"></a>概觀

混合實境雲端服務 (例如 **Azure 遠端轉譯**和 **Azure 空間錨點)** 可協助開發人員在各種平台上建置引人注目的沉浸式體驗。 這些服務可讓您為 3D 訓練、預測設備維護和設計審查 (都是在使用者環境的內容中) 提出申請時，將空間感知整合到您的專案中。

此外，您還可以輕鬆地將其他 Azure 服務新增至現有的專案中，而不屬於混合實境的範圍。 如果您正在針對 Unity 進行開發，則會在此頁面底部列出各種[教學課程](#standalone-services)，協助您開始使用。

## <a name="mixed-reality-services"></a>混合實境服務

### <a name="azure-remote-rendering"></a>Azure 遠端轉譯
[Azure 遠端轉譯](https://docs.microsoft.com/azure/remote-rendering) (ARR) 是一項服務，可讓您即時呈現高度複雜的 3D 模型。 ARR 是目前公開預覽中的功能。 其可新增至以 HoloLens 2 或 Windows 桌上型電腦為目標的 Unity 或原生 C++ 專案。

![Unity 展示應用程式中的 Azure 遠端轉譯範例](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors
[Azure 空間錨點](https://docs.microsoft.com/azure/spatial-anchors) (ASA) 是一種跨平台服務，可讓您建置空間感知的混合實境應用程式。 您可以使用 Azure 空間錨點，在全球規模的多個裝置之間對應、保存及共用全像攝影內容。

![Azure Spatial Anchors 範例](images/persistence.gif)

可在許多環境中開發該服務，並將其部署到大量的裝置和平台上。 這可讓他們對自己的可用平台清單進行特殊分配：
* 適用於 HoloLens 的 Unity
* 適用於 iOS 的 Unity
* 適用於 Android 的 Unity
* 原生 iOS
* 原生 Android
* HoloLens 的 C++/WinRT 和 DirectX
* 適用於 iOS 的 Xamarin
* 適用於 Android 的 Xamarin

## <a name="standalone-services"></a>獨立服務
下面所列的獨立服務不適用於混合實境，但可在各種不同的開發內容中提供幫助。 如果您在 Unity 中進行開發，則這些服務中的每個服務都可以整合到新專案或現有的專案中。

### <a name="device-support"></a>裝置支援
<table>
    <tr>
        <td><strong>Azure 雲端服務</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td><a href="mr-azure-301.md">語言翻譯</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302.md">電腦視覺</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302b.md">自訂視覺</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-303.md">跨裝置通知</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-304.md">臉部辨識</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-305.md">功能與儲存空間</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-306.md">串流視訊</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-307.md">機器學習</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-308.md">功能與儲存空間</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-309.md">Application insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-310.md">物件偵測</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-312.md">Bot 整合</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>
