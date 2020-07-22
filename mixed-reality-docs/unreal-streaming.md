---
title: Unreal 中的串流
description: Unreal 至 HoloLens 2 的串流指南
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 串流, 電腦, 全像攝影應用程式遠端處理, 全像攝影遠端播放程式, 文件
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: d25efbcf83e45749cc4eb8b99581b71105c59c9d
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303529"
---
# <a name="streaming-in-unreal"></a>Unreal 中的串流

## <a name="overview"></a>概觀
從電腦串流至 HoloLens 可提供兩大優點： 
* 可讓您的混合實境應用程式利用電腦的計算能力。 
* 有助於加快開發反覆運算的時間。 

若要開始使用，您必須將[全像攝影遠端播放程式](holographic-remoting-player.md)下載到您的 HoloLens 裝置。 這可讓您的應用程式從下列來源直接串流至 HoloLens 上的遠端播放程式：

* Unreal Engine 編輯器
* 已封裝的 Windows 可執行檔 

進行串流時，您可以存取您在裝置上執行應用程式時可用的絕大多數 HoloLens 功能。 其中包括[手部關節追蹤](unreal-hand-tracking.md) (如果您是在 HoloLens 2 上)、[空間對應](unreal-spatial-mapping.md)和[空間錨點](unreal-spatial-anchors.md)，但不包括此[限制清單](holographic-remoting-troubleshooting.md)上的功能。 

> [!NOTE]
> * 串流品質高度取決於您的 wifi 網路強度。
> * 全像攝影遠端處理播放程式會自動啟用所有功能。 如果您發現某個功能需要使用者權限 (例如：眼睛追蹤)，才能透過串流方式來使用，但在裝置上執行時則不用，請檢查並確定您已在專案設定下啟用適當的功能。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>來源</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>沉浸式頭戴裝置</strong></td>
    </tr>
     <tr>
        <td>Unreal 編輯器</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Windows 套件</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>從 Unreal 編輯器進行串流

身為開發人員，您會發現從 Unreal 編輯器串流至 HoloLens 裝置可在測試時提供很大的好處，也就是您不再需要等到應用程式完成建置和部署，才能試用您的更新。

您可以在「開始使用 Unreal」教學課程系列的最後一節中，找到[從 Unreal 編輯器進行串流](unreal-uxt-ch6.md#device-only-streaming)的詳細指示。

## <a name="streaming-from-a-packaged-windows-executable"></a>從已封裝的 Windows 可執行檔進行串流

從 Unreal 4.25.1 開始，您可以依照下列步驟，從已封裝的 Windows 可執行檔將應用程式串流至 HoloLens 2 裝置： 

1. 在 [編輯器] 功能表中，移至 [檔案] > [封裝專案] > [Windows]。 
    * 選擇要儲存套件的位置，然後按一下 [選取資料夾]。

2. 套件完成建置後，請在 HoloLens 2 上開啟 [全像攝影遠端播放程式]，並記下 IP 位址。 
3. 將 [全像攝影遠端播放程式] 保持開啟，並使用命令列提示字元執行下列動作： 
    * 切換至套件儲存所在的本機目錄中。
    * 輸入下列命令：```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```

> [!NOTE]
> 系統應該會自動使用您專案設定中的應用程式名稱來建立 Windows 套件。 如果這些設定因某些原因而有所不同，請在命令提示字元中使用 Windows 可執行檔名稱。

按 Enter 鍵，您的應用程式即會開始串流！

## <a name="see-also"></a>另請參閱
* [全像攝影遠端處理版本歷程記錄](holographic-remoting-version-history.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [建立全像攝影遠端處理的連線安全](holographic-remoting-secure-connection.md)
