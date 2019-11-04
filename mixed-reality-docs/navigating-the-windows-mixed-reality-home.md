---
title: 流覽 Windows Mixed Reality 首頁
description: HoloLens 和 Windows Mixed Reality 耳機共用在您的環境中啟動、放置和操作應用程式和3D 模型的範例（不論是實體或數位）。 瞭解如何在這兩種裝置類型上流覽 Windows Mixed Reality 首頁。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: shell，os，平臺，cliff 房屋，房屋，首頁，環境，開始，開始功能表，首頁功能表，pin，應用程式，啟動應用程式，放置應用程式，傳送，移動，流覽
ms.openlocfilehash: 9de4cb44505d6cf4d0d3e4bd0fd9c5ee681063a5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438156"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>流覽 Windows Mixed Reality 首頁

就像 Windows 電腦經驗從桌上型電腦開始，Windows Mixed Reality 從首頁開始。 Windows Mixed Reality home 會利用我們的固有功能來瞭解和流覽3D 位置。 使用 HoloLens 時，您的家庭就是您的實體空間。 使用沉浸式耳機時，您的家庭就是虛擬位置。

您的家裡也會使用 [開始] 功能表來開啟和放置應用程式和內容。 您可以同時使用多個應用程式，以混合現實內容和多重處理來填滿您的家庭。 即使您重新開機裝置，您在家裡所放置的東西還是會保留在該處。

## <a name="start-menu"></a>開始功能表

![Microsoft HoloLens 上的 [開始] 功能表](images/start-500px.png)

[開始] 功能表包含：
* 系統資訊（網路狀態、電池百分比、目前時間和音量）
* Cortana （在沉浸式耳機上，開始磚，在 HoloLens 上，在 [開始] 上方）
* 釘選的應用程式
* [所有應用程式] 按鈕（加號）
* [混合現實 capture](mixed-reality-capture.md)的相片和影片按鈕

藉由選取加號或減號按鈕，在 [釘選的應用程式] 和 [所有應用程式] 視圖之間切換。 若要開啟 HoloLens 上的 [開始] 功能表，請使用 bloom 手勢。 在沉浸式耳機上，按下控制器上的 [Windows] 按鈕。

## <a name="launching-apps"></a>啟動應用程式

若要啟動應用程式，請在 [啟動] 時加以選取。 [開始] 功能表將會消失，而應用程式會以放置模式開啟，做為2D 視窗或[3d 模型](implementing-3d-app-launchers.md)。

若要執行應用程式，您必須將它放在您的首頁：
1. 使用您的[注視](gaze-and-commit.md)或控制器將應用程式放在您想要的位置。 它會自動調整（大小和位置）以符合您放置它的空間。
2. 使用 [空中] （HoloLens）或 [選取] 按鈕（沉浸式耳機）來放置應用程式。 若要取消並帶回 [開始] 功能表，請使用 bloom 手勢或 [Windows] 按鈕。

針對桌面、行動裝置或 Xbox 建立的[2d 應用程式](building-2d-apps.md)，可以修改為使用[HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)以混合現實沉浸式應用程式的形式執行。 沉浸式應用程式會讓使用者離開家裡，並成為沉浸式體驗。 使用者可以使用 bloom 手勢（HoloLens）或按下控制器上的 Windows 按鈕（沉浸式耳機）來傳回 home。

應用程式也可以透過應用程式對應用程式 API 或 Cortana 來啟動。

![Windows Mixed Reality 首頁中的應用程式](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>移動和調整應用程式

選取應用程式行上的 [**調整**]，以顯示移動、調整和旋轉混合現實內容的控制項。 當您完成時，請選取 [**完成**]。

![以調整模式（藍色框架）儲存的平板電腦。 請注意，應用程式行（上方）已變更為包含 [完成] 和 [移除] 按鈕。](images/adjust-500px.png)

不同的應用程式可能會在應用程式行上有其他選項。 例如，Microsoft Edge 有*滾動*條、*拖曳*和*縮放*選項。 

![在 HoloLens 上執行之2D 應用程式的應用程式行](images/holobar-500px.png)

[**上一步**] 按鈕會流覽回到先前在應用程式中看到的畫面。 當您到達應用程式中顯示的體驗開始時，將會停止，而且不會流覽至其他應用程式。

## <a name="getting-around-your-home"></a>取得您的家庭

透過**HoloLens**，您可以在實際空間間移動，以在家裡移動。

有了**沉浸式耳機**，您就可以像是在 playspace 中開始進行，以在虛擬世界中的類似區域內移動。 若要在較長的距離之間移動，您可以使用控制器上的操縱杆來進行幾乎「逐步執行」，也可以使用*teleportation*立即跳躍較長的距離。

![Windows Mixed Reality 首頁中的 Teleportation](images/teleportation-500px.png)

**若要傳送：**
1. 顯示 teleportation reticle。
   * 使用[動作控制器](motion-controllers.md)：向前按下操縱杆，並將它放在該位置。
   * 使用 Xbox controller：按向左的操縱杆，並將其放在該位置。
   * 使用滑鼠：按住滑鼠右鍵鍵（並使用滾輪來旋轉您在傳送時所要面對的方向）。
2. 將 reticle 放在您想要傳送的位置。
   * 使用 [[移動控制器](motion-controllers.md)]：將控制器傾斜（您要在其上保留操縱杆）來移動 reticle。
   * 使用 Xbox controller：使用您的[注視](gaze-and-commit.md)來移動 reticle。
   * 使用滑鼠：移動滑鼠來移動 reticle。
3. 放開按鈕以在放置 reticle 的位置進行傳送。

**至虛擬「逐步解說：」**
* 使用[動態控制器](motion-controllers.md)：按一下操縱杆上的 [向下] 並按住，然後以您想要「逐步執行」的方向移動操縱杆。
* 使用 Xbox 控制器：按一下左側的操縱杆並按住，然後以您想要「逐步執行」的方向移動操縱杆。

## <a name="immersive-headset-input-support"></a>沉浸式耳機輸入支援

[Windows Mixed reality 沉浸式耳機](immersive-headset-hardware-details.md)支援多種輸入類型來流覽 Windows mixed reality 首頁。 HoloLens 不支援用於導覽的附件輸入，因為您會實際四處流覽並查看您的環境。 不過，HoloLens 支援與應用程式互動的[輸入](hardware-accessories.md)。

### <a name="motion-controllers"></a>運動控制器

Windows mixed reality 的最佳體驗，就是使用您的耳機中的[感應器來支援](motion-controllers.md)6 度自由的追蹤，而不需要外部攝影機或標記！

即將推出的導覽命令。

### <a name="gamepad"></a>遊戲台
* **左方控制杆：**
  * 按住左側的操縱杆，以帶出[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle。
  * 將操縱杆向左、靠右或向後移動，以小增量向左、右或向後移動。
  * 按一下左側的操縱杆並按住，然後以您想要的方向，將操縱杆移至 [[逐步解說]。](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* 向左或向右按一下**右側的操縱杆**，以旋轉45度所面臨的方向。
* 按下**按鈕會**執行 select，並使用像是 [[空中](gaze-and-commit.md#composite-gestures)] 手勢。
* 按下 [**引導**] 按鈕會顯示 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)，其作用就像[bloom](system-gesture.md#bloom)手勢。
* 按**左右的觸發**程式，可讓您放大和縮小要在家裡互動的2d 桌面應用程式。

### <a name="keyboard-and-mouse"></a>鍵盤和滑鼠

**注意：** 使用**Windows 鍵 + Y**在控制電腦的桌面和 Windows Mixed Reality 首頁之間切換滑鼠。

在 Windows Mixed Reality 首頁中：
* 按下滑鼠**左鍵**會執行選取，且其作用就像是 [[空中](gaze-and-commit.md#composite-gestures)] 手勢。
* 按住滑鼠**右鍵**鍵會顯示[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle。
* 按下鍵盤上的**Windows**鍵會開啟 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)，其作用就像[bloom](system-gesture.md#bloom)手勢。
* 在2D 桌面應用程式中[撥雲見日](gaze-and-commit.md)時，您可以**按一下**滑鼠右鍵來選取、以**滑鼠右鍵按一下**以顯示操作功能表，然後使用**滾輪來進行滾動（** 就像在您的電腦桌面上一樣）。

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana)是您在 Windows Mixed Reality 中的個人助理，就像在 PC 和手機上一樣。 HoloLens 有內建的麥克風，但沉浸式耳機可能需要額外的硬體。 使用 Cortana 開啟應用程式、重新開機您的裝置、線上查看專案等等。 開發人員也可以選擇將[Cortana 整合](https://dev.windows.com/cortana)到他們的經驗中。

您也可以使用語音命令來取得家庭。 例如，指向按鈕（使用[注視](gaze-and-commit.md)或控制器，視裝置而定），然後說「選取」。 其他語音命令包括「回家」、「大」、「小」、「近」和「臉部我」。

## <a name="store-settings-and-system-apps"></a>儲存、設定和系統應用程式

Windows Mixed Reality 有數個內建應用程式，例如：
* 取得應用程式和遊戲的**Microsoft Store**
* 提交有關系統和系統應用程式意見反應的**意見反應中樞**
* **設定**系統設定的設定（[包括網路](connecting-to-wi-fi-on-hololens.md)功能和系統更新）
* 流覽網站的**Microsoft Edge**
* 觀看及分享相片和影片的**相片**
* **校正**（僅限 hololens），用於調整目前使用者的 HoloLens 體驗
* 學習**手勢**（HoloLens）或**瞭解混合現實**（沉浸式耳機）以瞭解如何使用您的裝置
* 使用混合現實內容裝飾您世界的**3D 檢視器**
* 用於設定和管理您的沉浸式耳機的**混合現實入口網站**（桌面），並在耳機中串流您觀看的即時預覽，供其他人查看。
* 觀看360影片和最新電影和電視節目的**電影和電視**節目
* 所有虛擬助理需求的**Cortana**
* **桌面**（沉浸式耳機），可在沉浸式耳機中觀賞桌面監視器
* 檔案**瀏覽器**存取位於您裝置上的檔案和資料夾

## <a name="see-also"></a>請參閱
* [應用程式檢視](app-views.md)
* [運動控制器](motion-controllers.md)
* [硬體配件](hardware-accessories.md)
* [HoloLens 的環境考量](environment-considerations-for-hololens.md)
* [執行3D 應用程式啟動器](implementing-3d-app-launchers.md)
* [建立3D 模型以用於 Windows Mixed Reality 首頁](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
