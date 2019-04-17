---
title: 瀏覽家用的 Windows Mixed Reality
description: HoloLens 與 Windows Mixed Reality 耳機共用用於啟動、 放置，以及管理應用程式和您的環境中的 3D 模型 （無論實體或數位） 的範例。 了解如何瀏覽首頁這兩種裝置類型上的 Windows Mixed Reality。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 殼層、 作業系統、 平台、 cliff 房屋房子、 首頁、 環境、 啟動、 [開始] 功能表、 主功能表、 pin、 應用程式、 啟動的應用程式，將應用程式、 傳送、 移動、 瀏覽
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597043"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>瀏覽家用的 Windows Mixed Reality

就像 Windows PC 體驗啟動與桌面時，Windows Mixed Reality，開始於首頁。 家用的 Windows Mixed Reality 運用我們對中炫耀都能夠了解，並瀏覽 3D 的地方。 HoloLens，您的首頁是您的實體空間。 沈浸式耳機，與您的首頁會是虛擬的位置。

您的首頁也是，您將使用 [開始] 功能表開啟，並將應用程式和內容。 您可以混合的實境內容中填入您的首頁和 multitask 同時使用多個應用程式。 您放置在您家中的項目留在那裡，即使您重新啟動您的裝置。

## <a name="start-menu"></a>開始功能表

![在 Microsoft HoloLens 上的 [開始] 功能表](images/start-500px.png)

[開始] 功能表所組成：
* 系統資訊 （網路狀態、 電池百分比、 目前時間和磁碟區）
* Cortana （沈浸式耳機，啟動磚; 在 HoloLens，在頂端開始）
* 已釘選的應用程式
* 所有的應用程式按鈕 （加號）
* 相片與視訊按鈕[混合實境擷取](mixed-reality-capture.md)

已釘選的應用程式和檢視之間切換的所有應用程式藉由選取加號或減號按鈕。 若要開啟 HoloLens 上的 [開始] 功能表，請使用 bloom 筆勢。 在沉浸式耳機，按下控制器上的 [Windows] 按鈕。

## <a name="launching-apps"></a>啟動應用程式

若要啟動應用程式，請在啟動時選取它。 [開始] 功能表便會消失，以及應用程式將會開啟在放置模式下，為 2D 視窗或[3D 模型](implementing-3d-app-launchers.md)。

若要執行應用程式，您必須再將它放在您家中：
1. 使用您[視線](gaze.md)或控制站，以在您要應用程式的位置。 若要符合的放置位置的空間，就會自動調整 （在大小和位置）。
2. 將使用空中點選 (HoloLens) 或 [選取] 按鈕 （沈浸式耳機） 應用程式。 若要取消並帶回 開始 功能表，請使用 bloom 筆勢 或 Windows 按鈕。

[2D 應用程式](building-2d-apps.md)、 針對桌面、 行動裝置，建立或 Xbox 可以修改，以使用混合的實境沈浸式應用程式會以[HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)。 沈浸式應用程式會將使用者帶出首頁並進入沉浸式體驗。 使用者就可以傳回首頁與 bloom 筆勢 (HoloLens) 或其控制站 （沈浸式耳機） 上按 [Windows] 按鈕。

透過應用程式-應用程式 API，或透過 Cortana，也可以啟動應用程式。

![在家用的 Windows Mixed Reality 應用程式](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>移動和調整應用程式

選取 **調整**應用程式上顯示的列控制移轉，小數位數和旋轉的混合實境內容。 當您完成時，選取**完成**。

![調整模式 （藍色框架） 中存放區的候選影片。 請注意應用程式列 （上方） 已變更為包括 [完成] 和 [移除] 按鈕。](images/adjust-500px.png)

不同的應用程式可能會有應用程式列上的其他選項。 例如，具有 Microsoft Edge*捲軸*，*拖曳*，和*縮放*選項。 

![2D HoloLens 上執行的應用程式的應用程式列](images/holobar-500px.png)

**回**按鈕導覽回到先前檢視的應用程式中的畫面。 當您到達 已顯示在應用程式，並不會瀏覽至其他應用程式體驗的開頭，它會停止。

## <a name="getting-around-your-home"></a>瀏覽您的首頁

具有**HoloLens**，您瀏覽實體空間，您的家中移動。

具有**沈浸式耳機**，您可以同樣地啟動並在您以類似於虛擬世界的區域內移動 playspace 四處巡察。 在距離之間的移動，您可以使用搖桿控制器上從頭到尾參與幾乎"，"，或者您可以使用*屏障*立即跳較長的距離。

![在家用的 Windows Mixed Reality 屏障](images/teleportation-500px.png)

**若要傳送：**
1. 顯示屏障 reticle。
   * 使用[動作控制器](motion-controllers.md): 搖桿向前按住不放在該位置。
   * 使用 Xbox 控制器： 左搖桿向前按住不放在該位置。
   * 使用滑鼠： 按住滑鼠右鍵按一下滑鼠按鈕 (使用滾輪旋轉您想要面臨時的方向和您傳送)。
2. 將 reticle 放在您想要用來傳送。
   * 使用[動作控制器](motion-controllers.md)： 移動 reticle 傾斜擁有的控制站 （在其上您在搖桿轉寄）。
   * 使用 Xbox 控制器： 使用您[視線](gaze.md)移動 reticle。
   * 使用滑鼠： 移動滑鼠移動 reticle。
3. 放開按鈕，即可傳送 reticle 放置的位置。

**若要幾乎 」 逐步: 」**
* 使用[動作控制器](motion-controllers.md)： 按一下向下搖桿，然後按住不放，然後將搖桿移動的方向，您想要 「 前進 」。
* 使用 Xbox 控制器： 按一下向下左搖桿，然後按住不放，然後將搖桿移動的方向，您想要 「 前進 」。

## <a name="immersive-headset-input-support"></a>沈浸式耳機輸入的支援

[Windows Mixed Reality 沈浸式耳機](immersive-headset-hardware-details.md)巡覽家用的 Windows Mixed Reality 支援多個輸入的類型。 HoloLens 不支援配件的輸入進行巡覽，因為您實際上四處巡察，請參閱您的環境。 不過，會 HoloLens[支援輸入](hardware-accessories.md)與應用程式互動。

### <a name="motion-controllers"></a>動作控制站

最佳的 Windows Mixed Reality 體驗將會使用 Windows Mixed Reality[動作控制器](motion-controllers.md)耳機-沒有外部的相機或需要的標記中使用的感應器，支援的自由 6 度-追蹤 ！

即將推出的巡覽命令。

### <a name="gamepad"></a>遊戲台
* **左搖桿：**
  * 按住不放以顯示的正向左搖桿[屏障](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)reticle。
  * 點選 left、 right 搖桿或後要向左移動、 權限，或在小型增量備份。
  * 按一下向下左搖桿，然後按住不放，則您想要的方向移動搖桿[幾乎上 「 前進。 」](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* 點選**右搖桿**左或向右旋轉 45 度，您所面臨的方向。
* 按下**A**  按鈕會執行 select 和其作用就像[空中點選](gestures.md#air-tap)筆勢。
* 按下**快速入門**按鈕會開啟[開始 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)和其作用就像[bloom](gestures.md#bloom)筆勢。
* 按下**左邊和右邊的觸發程序**可讓您縮放 2D 傳統型應用程式與在家中互動。

### <a name="keyboard-and-mouse"></a>鍵盤和滑鼠

**注意：** 使用**Windows 鍵 + Y**切換之間控制您的電腦桌面和家用的 Windows Mixed Reality 滑鼠。

在 Windows Mixed Reality 首頁：
* 按下**按滑鼠左鍵**滑鼠按鈕執行 select 和其作用就像[空中點選](gestures.md#air-tap)筆勢。
* 持有**上按一下滑鼠右鍵**滑鼠按鈕會開啟[屏障](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)reticle。
* 按下**Windows**鍵盤上的按鍵會顯示[開始 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)和其作用就像[bloom](gestures.md#bloom)筆勢。
* 時[gazing](gaze.md) 2D 的桌面應用程式，您可以**按滑鼠左鍵**若要選取，**以滑鼠右鍵按一下**開啟操作功能表，並使用**滾輪**捲動 （就如同您的電腦的桌面上）。

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana)一樣是在 PC 和手機上的 Windows Mixed Reality，在您個人助理。 HoloLens 有內建的麥克風，但沈浸式耳機可能需要額外的硬體。 若要開啟應用程式、 重新啟動您的裝置，線上查閱項目使用 Cortana 和更多功能。 開發人員也可以選擇[整合 Cortana](https://dev.windows.com/cortana)至其經驗。

您也可以使用語音命令來解決您的首頁。 比方說，指向按鈕 (使用[視線](gaze.md)或控制站，視裝置而定)，並說 「 Select 」。 其他的語音命令包括 「 移至首頁 」，「 大 」，「 比較小，"「 關閉 」 和 「 面臨我 」。

## <a name="store-settings-and-system-apps"></a>存放區、 設定和系統的應用程式

Windows Mixed Reality 有許多內建的應用程式，例如：
* **Microsoft Store**取得應用程式和遊戲
* **意見反應中樞**提交意見反應的系統和系統應用程式
* **設定**設定系統設定 ([包括網路](connecting-to-wi-fi-on-hololens.md)和系統更新)
* **Microsoft Edge**瀏覽網站
* **相片**來檢視和分享相片和視訊
* **校正**(只有 HoloLens) 調整到目前使用者的 HoloLens 體驗
* **了解筆勢**(HoloLens) 或**了解混合實境**（沈浸式耳機） 若要了解如何使用您的裝置
* **3D 檢視器**來裝飾您面對混合的實境內容
* **混合實境入口網站**（桌面） 設定和管理您的沈浸式耳機和串流您的檢視中供其他人查看耳機的即時預覽。
* **電影和電視節目**360 影片的最新的電影和電視節目的檢視會顯示
* **Cortana**讓所有虛擬助理必須
* **桌面**（沈浸式耳機） 來檢視您在沉浸式耳機的桌上型監視器
* **檔案總管**存取檔案和資料夾位於您的裝置

## <a name="see-also"></a>另請參閱
* [應用程式檢視](app-views.md)
* [動作控制站](motion-controllers.md)
* [硬體附屬應用程式](hardware-accessories.md)
* [HoloLens 的環境考量](environment-considerations-for-hololens.md)
* [實作的 3D 應用程式啟動器](implementing-3d-app-launchers.md)
* [建立 3D 模型，使用 Windows Mixed Reality 在家中](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
