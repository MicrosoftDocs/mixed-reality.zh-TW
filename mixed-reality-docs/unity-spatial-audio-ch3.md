---
title: 空間音訊教學課程-3。 從影片 Spatializing 音訊
description: 將影片資產匯入到您的 Unity 專案，並從影片 spatialize 音訊。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教學課程，hololens2，空間音訊
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182745"
---
# <a name="spatializing-audio-from-a-video"></a>從影片 Spatializing 音訊
在 HoloLens 2 Unity 教學課程的空間音訊模組的第3章中，您將會：
* 匯入影片並新增影片播放
* 在 quadrangle 上播放影片
* 將音訊從影片路由傳送至 quadrangle，並 spatialize 音訊

## <a name="import-a-video-and-add-a-video-player"></a>匯入影片並新增影片播放

將影片檔案拖曳至 Unity 專案的 [**專案**] 窗格中。 您可以使用空間音訊範例專案中的[這段影片](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true)。

![具有影片的資產資料夾](images/spatial-audio/assets-folder-with-video.png)

調整影片剪輯上的品質設定可確保在 HoloLens 2 上順暢播放。 按一下 [**專案**] 窗格中的影片檔案。 然後在影片檔案的 [偵測**器**] 窗格中，覆寫 Windows Store 應用程式的設定，以及：
* 啟用**轉碼**
* 將**編解碼器**設定為 H264
* 將**位元速率模式**設定為低
* 將**空間品質**設定為中等空間品質

這些調整之後，影片檔案的 [偵測**器**] 窗格看起來會像這樣：

![影片屬性窗格](images/spatial-audio/video-property-pane.png)

接下來，以滑鼠右鍵**按一下 [階層**] 窗格，然後選擇 [**影片-> 影片播放程式** **]，** 將**影片播放機**物件新增至階層：

![階層中的影片播放](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a>播放影片至 quadrangle
**影片播放機**物件需要一個紋理的遊戲物件來呈現影片。 首先，以滑鼠右鍵按一下 [**階層] 窗格**，然後選擇 [ **3d 物件-> 四**：]，將 [**四**] 新增**至您的**階層。

![將四個新增至階層](images/spatial-audio/add-quad-to-hierarchy.png)

為確保當應用程式啟動時，**四**個會出現在使用者前方，請將**四**個的 [**位置**] 屬性設為（0，0，2），並將 [**小**數位數] 屬性設定為（1.28、0.72、1）。 這些變更之後，**四**個 [偵測**器**] 窗格上的 [**轉換**] 元件將會如下所示：

![四轉換](images/spatial-audio/quad-transform.png)

若要使用影片將**四**種材質紋理，請建立新的**呈現材質**。 在 [**專案**] 窗格中，以滑鼠右鍵按一下並選擇 [**建立-> 呈現材質**]：

![建立呈現材質](images/spatial-audio/create-render-texture.png)

在轉譯**材質**的 [偵測**器**] 窗格中，設定 [**大小**] 屬性，以符合影片的1280x720 原生解析度。 然後，若要確保在 HoloLens 2 上呈現良好的效能，請將**深度緩衝區**屬性設定為**至少16位深度**。 在這些設定之後，轉譯**材質**的 [偵測**器**] 窗格看起來會像這樣：

![轉譯材質屬性](images/spatial-audio/render-texture-properties.png)

接下來，使用新的轉譯**材質**做為**四**種的紋理：
1. 將轉譯**材質**從 [**專案**] 窗格拖曳至階層**中的 [** **四**個]
2. 若要確保 HoloLens 2 的效能良好，請在**四**個 [偵測**器**] 窗格中，選取 [**混合現實工具組標準著色器**]。

使用這些設定，**四**個 [偵測**器**] 窗格上的 [**材質**] 元件會如下所示：

![四紋理屬性](images/spatial-audio/quad-texture-properties.png)

若要設定新的**影片播放**程式並**呈現材質**來播放您的影片剪輯，請開啟**影片播放**程式的 [偵測**器**] 窗格，並：
* 將**影片剪輯**屬性設定為您的影片檔案
* 勾選 [**迴圈**] 核取方塊
* 將**目標材質**設定為新的呈現材質

**影片播放**程式的 [偵測**器**] 窗格現在看起來會像這樣：

![影片播放者屬性](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a>Spatialize 影片中的音訊
在**四**個的 [偵測**器**] 窗格中，建立**音訊來源**，以從影片路由傳送音訊：
* 按一下窗格底部的 [**新增元件**]
* 新增**音訊來源**

然後，在**音訊來源**上：
* 將**輸出**設定為混音器
* 勾選 [ **Spatialize** ] 方塊
* 將**空間 Blend**滑杆移至1（3d）

這些變更之後，**四**個 [偵測**器**] 窗格上的 [**音訊來源**] 元件看起來會像這樣：

![四音訊來源偵測器](images/spatial-audio/quad-audio-source-inspector.png)

若要設定**影片播放**程式將其音訊傳送至**四**個**音訊來源**，請開啟**影片播放機**的 [偵測**器**] 窗格，然後：
* 將**音訊輸出模式**設定為「音訊來源」
* 將 [**音訊來源**] 屬性設定為您的四個

這些變更之後，**影片播放**程式的 [偵測**器**] 窗格看起來會像這樣：

![影片播放組設定音訊來源](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a>後續步驟
在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。 您會看到並聆聽影片，而影片中的音訊將會 hrtf。

繼續進行[第4章](unity-spatial-audio-ch4.md)，以在執行時間使用按鈕來啟用和停用 spatialization。

