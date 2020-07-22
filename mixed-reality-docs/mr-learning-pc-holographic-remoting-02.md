---
title: 電腦全像攝影遠端處理教學課程 - 2。 建立全像攝影遠端處理電腦應用程式
description: 完成此課程，以了解如何從電腦到 HoloLens 2 進行遠端混合實境體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 32fccbaf6bae8031572ff716f3c9fc26a43849e5
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304683"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2.建立全像攝影遠端處理電腦應用程式

在本教學課程中，您將了解如何建立電腦應用程式來進行全像攝影遠端處理，並在任何時間點連線 HoloLens 2，進而提供一種在混合實境中將 3D 內容視覺化的方式。

## <a name="objectives"></a>目標

* 設定適用於全像攝影遠端處理的 Unity
* 了解如何使用 Visual Studio 建立及部署應用程式
* 開發全像攝影遠端處理應用程式並連線到 HoloLens

## <a name="configuring-your-scene-for-holographic-remoting"></a>設定您的場景以進行全像攝影遠端處理

在本節中，您將設定專案，以透過 Wi-Fi 連線即時地將您的混合現實境驗串流至電腦上的 HoloLens 2 裝置。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.PCHolograhicRemoting] > [Prefabs] 資料夾，然後按一下 **HolographicRemoting** Prefab 並拖曳到您的場景中。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>在電腦中建置應用程式

您的全像攝影遠端處理應用程式現在已準備好在電腦上建置。 請遵循下列步驟來進行這些變更，以將此應用程式建立到您的電腦上。

### <a name="1-set-the-player-settings"></a>1.設定玩家設定

在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗。

在 [XR 設定] 區段中，選取 [支援的 WSA 全像攝影遠端處理] 核取方塊，並啟用全像攝影遠端處理。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2.建置 Unity 專案

在 Unity 功能表中，選取 [檔案] > [建置設定] 來開啟 [建置設定] 視窗。

在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至場景。 在 [建置] 清單中，按一下 [建置按鈕] 以開啟 [建置通用 Windows 平台] 視窗：

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

在 [建置通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的建置，例如 Documents\MixedRealityLearning。 建立新的資料夾，並為其指定適當的名稱，例如 PCHolographicRemoting。 然後按一下 [選取資料夾] 按鈕來啟動建置程序：

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

等候 Unity 完成建置程序。

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3.組建和部署應用程式

當組建程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。 瀏覽該資料夾，按兩下 .sln 檔案即可在 Visual Studio 中開啟該檔案：

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> 如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同＜安裝工具＞文件中所指定。

藉由選取 x64 架構的發行設定，以及選取本機電腦作為目標，來設定電腦的 Visual Studio：

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

按一下顯示 [本機電腦] 的按鈕。 其會開始建置應用程式，並將其部署到您的電腦。 應用程式會預設安裝在您的電腦上。

## <a name="testing-holographic-remoting-remote-application"></a>測試全像攝影遠端處理應用程式

若要將您的電腦應用程式連線到 HoloLens 2，請遵循下列程序：

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1.在 HoloLens 2 裝置上安裝遠端播放程式應用程式

* 在您的 HoloLens 2 上，瀏覽市集應用程式並搜尋「遠端播放程式」。
* 選取**遠端處理播放程式**應用程式。
* 請點選 [安裝] 來下載並安裝應用程式。

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2.將全像攝影遠端處理電腦應用程式連線到遠端播放程式

* 啟動 HoloLens 上的**遠端播放程式**。
* 記下 HoloLens 的 **IP 位址**。 **遠端播放程式**會在啟動時，將其顯示為全像投影。
* 在您的電腦上開啟全像攝影遠端處理電腦應用程式。
* 啟動應用程式之後，輸入 **IP 位址**，然後按一下 [連線] 按鈕以進行連線。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何建立全像攝影遠端處理應用程式，並在任何時間點連線 HoloLens 2，進而提供一種在混合實境中將 3D 內容視覺化的方式。 當 HoloLens 連線到全像攝影遠端處理電腦應用程式之後，您應該會看到混合實境體驗串流至您的 HoloLens 2 裝置。
