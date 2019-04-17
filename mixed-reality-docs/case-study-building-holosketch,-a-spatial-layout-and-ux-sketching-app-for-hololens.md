---
title: 案例研究-建置 HoloSketch、 空間配置和草擬的 HoloLens 的應用程式的 UX
description: 裝置上的空間配置和 UX 草擬工具可協助您建立全像攝影版的體驗的 HoloLens HoloSketch。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch、 HoloLens、 Windows Mixed Reality，草擬，應用程式
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591867"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>案例研究-建置 HoloSketch、 空間配置和草擬的 HoloLens 的應用程式的 UX

裝置上的空間配置和 UX 草擬工具可協助您建立全像攝影版的體驗的 HoloLens HoloSketch。 HoloSketch 搭配配對的藍芽鍵盤和滑鼠以及手勢及語音命令。 HoloSketch 的目的是提供一個簡單的 UX 版面配置工具快速的視覺效果和反覆項目。

![HoloSketch:空間配置和草擬的 HoloLens 的應用程式的 UX 中。](images/holosketch-image-01-640px.png)<br>
*HoloSketch： 空間配置和草擬的 HoloLens 的應用程式的 UX*

![簡單 UX 版面配置工具，快速的視覺效果和反覆項目。](images/holosketch-image-02.png)<br>
*簡單的 UX 版面配置工具的快速視覺效果和反覆項目*

## <a name="features"></a>功能

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>快速研究和小數位數原型設計的基本項目

![使用基本的圖形](images/holosketch-primitives-giphy.gif)

您可以使用 基本的圖形快速聚集研究和原型設計的小數位數。

### <a name="import-objects-through-onedrive"></a>透過 OneDrive 匯入物件

![匯入物件](images/holosketch-importobjects-giphy.gif)

匯入 PNG/JPG 影像或 3D FBX 物件 （需要封裝，Unity 中的） 至混合的實境空間透過 OneDrive。

### <a name="manipulate-objects"></a>管理物件

![處理物件](images/manipulate-objects-640px.jpg)

操作與熟悉的 3D 物件介面的物件 （移動/旋轉/縮放比例）。

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>藍芽、 滑鼠] / [鍵盤、 手勢和語音命令

![支援藍芽](images/supports-bluetooth-640px.jpg)

HoloSketch 支援藍芽滑鼠] / [鍵盤、 手勢和語音命令。

## <a name="background"></a>背景

### <a name="importance-of-experiencing-your-design-in-the-device"></a>發生在裝置中的設計的重要性

當您設計的項目為 HoloLens 時，務必體驗您的裝置中的設計。 在混合的實境應用程式設計中最大的挑戰之一是很難概略了解的延展性、 位置與深度，尤其是透過傳統的 2D 草圖。

### <a name="cost-of-2d-based-communication"></a>2D 的費用依通訊

若要有效地傳達 UX 流程和其他人的案例，設計工具可能會得到花很多時間來建立使用傳統的 2D 工具，例如 Illustrator、 Photoshop 和 PowerPoint 的資產。 這些 2D 設計通常需要額外的工作，將它們轉換到 3D。 一些構想是中遺失這項轉譯 2D 到 3D。

### <a name="complex-deployment-process"></a>複雜的部署程序

混合的實境是我們新的畫布，因為它牽涉到大量的設計反覆項目和試驗和錯誤本質上。 不熟悉使用 Unity 和 Visual Studio 等工具的設計工具，它並不容易在 HoloLens 一起放置一些項目。 通常您必須完成以下程序以查看您的 2D/3D 圖檔，在裝置中。 這是快速反覆運算的想法和案例的設計工具的大障礙。

![複雜的部署程序](images/holosketch-image-03-1000px.png)<br>
*部署程序*

### <a name="simplified-process-with-holosketch"></a>使用 HoloSketch 的簡化程序

使用 HoloSketch，我們想要簡化這個程序不需要涉及開發工具，並將其裝置入口網站配對。 使用 OneDrive，使用者可以輕鬆地將 2D/3D 資產置於 HoloLens。

![使用 HoloSketch 的簡化程序](images/holosketch-image-04-1000px.png)<br>
*使用 HoloSketch 的簡化程序*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>令人滿意的三維的設計考慮與解決方案

我們認為這項工具可讓設計工具有機會探索真正三維空間中的解決方案，並不會卡在 2D。 他們不必考慮由於背景是實際在 Hololens 的情況下，為其 UI 建立 3D 的背景。 HoloSketch 會開啟設計工具，可輕鬆地將 3D 設計探討 Hololens 的方式。

## <a name="get-started"></a>開始使用

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>如何將 HoloSketch 匯入的 2D 影像 (JPG/PNG)

* JPG/PNG 影像上傳至您的 OneDrive 資料夾 ' 文件/HoloSketch '。
* 從 OneDrive 中的功能表 HoloSketch，您可以選取，然後放置在環境中的映像。

![匯入的 2D 影像](images/import-2d-images-1000px.jpg)<br>
*匯入映像和透過 OneDrive 的 3D 物件*

### <a name="how-to-import-3d-objects-into-holosketch"></a>如何將 HoloSketch 匯入 3D 物件

再上傳至您的 OneDrive 資料夾時，請遵循下列步驟來封裝您的 3D 物件至 Unity 資產套件組合。 使用此程序您可以從 3D 的軟體，例如 Maya、 電影院 4d 和 Microsoft 小畫家 3D 匯 FBX/OBJ 檔案。

>[!IMPORTANT]
>目前，資產套件組合建立支援 Unity 版本 5.4.5f1。

1. 下載並開啟 Unity 專案['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)。 這個 Unity 專案包含的套件組合的資產產生指令碼。
2. 建立新的 GameObject。
3. 命名內容為基礎的 GameObject。
4. 在 偵測器 面板中，按一下 新增元件並加入 ' 方塊 Collider'。 

   ![在 [偵測器] 面板中，按一下 [加入元件]，然後新增 ' 方塊 Collider'](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在 偵測器 面板中，按一下 新增元件，並加入 ' 方塊 Collider' #2](images/holosketch-10b-assetbundles-1000px.png)

5. 匯入 3D FBX 檔拖曳到 [專案] 面板。
6. 將物件拖曳到 [階層] 面板**在新的 GameObject**。

   ![將物件拖曳到 新的 GameObject 下的 階層 面板](images/holosketch-12-assetbundles-1000px.png)

7. 如果不符合物件，請調整 collider 維度。 旋轉物件面臨**z 軸**。

   ![如果不符合物件，請調整 collider 維度。](images/holosketch-13-assetbundles-1000px.png)

8. 將物件從 [階層] 面板拖曳至 [專案] 面板來**使得 prefab**。
9. [偵測器] 面板底部，按一下下拉式清單中，建立並指派新的唯一名稱。 下列範例示範如何新增及指派 'brownchair' AssetBundle 名稱。 

   ![在 [偵測器] 面板底部，按一下下拉式清單中，指派新的唯一名稱。](images/holosketch-14-assetbundles-1000px.png)

10. 準備模型物件的縮圖影像。 
   ![將影像拖曳到 [專案] 面板，並指派物件的名稱。](images/holosketch-15-assetbundles-1000px.png)

11. Unity 專案的 '資產' 資料夾下建立名為 'Assetbundles' 的資料夾。

12. 從 [資產] 功能表中，選取 [產生檔案的 ' 建置 AssetBundles']。 
   ![從 [資產] 功能表中，選取 [產生檔案的 ' 建置 AssetBundles']。](images/holosketch-15a-assetbundles.png)


13. **將產生的檔案上傳到 OneDrive /Files/Documents/HoloSketch 資料夾。** 上傳僅 asset_unique_name 檔案。 您不需要上傳資訊清單檔案或 AssetBundles 檔案。 <br>
![將檔案新增至檔案/文件/HoloSketch/資料夾](images/holosketch-onedriveupload-1000px.png)
![您會看到已新增的 HoloSketch 的 OneDrive 功能表中的 3D 物件](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>如何管理物件

HoloSketch 支援廣泛使用的傳統介面中 3D 的軟體。 您可以使用移動、 旋轉、 縮放筆勢和滑鼠的物件。 您可以快速切換不同的模式，透過語音或鍵盤。

### <a name="object-manipulation-modes"></a>物件的操作模式

![如何管理物件](images/holosketch-image-06-1000px.png)<br>
*如何管理物件*

### <a name="contextual-and-tool-belt-menus"></a>內容 與 工具 功能表

**使用操作功能表**

若要開啟操作功能表的雙精度浮點空中點選。 

功能表項目：
* **配置的介面：** 這是 3D 方格系統，您可以配置多個物件，並以群組方式管理它們。 將物件新增至該版面配置介面上 double 空中點選。
* **基本項目：** 使用 cube、 陳列、 圓柱和圓錐體聚集研究。
* **OneDrive:** 開啟 [OneDrive] 功能表，以匯入物件。
* **說明：** 顯示說明畫面。

![操作功能表](images/holosketch-image-07.png)<br>
*操作功能表*

**使用工具帶狀功能表**

移動、 旋轉，小數位數、 儲存和載入場景都是從工具帶狀功能表。 

## <a name="using-keyboard-gestures-and-voice-commands"></a>使用鍵盤、 手勢及語音命令

![鍵盤、 手勢及語音命令](images/holosketch-image-08-1000px.png)<br>
*鍵盤、 筆勢和語音命令*

## <a name="download-the-app"></a>下載應用程式

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">下載並安裝免費 Microsoft Store HoloSketch 應用程式</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>已知問題
* 目前資產套件組合建立支援**Unity 版本 5.4.5f1。**
* 根據您的 OneDrive 中的資料數量的應用程式可能會出現如同它已停止載入 OneDrive 內容時
* 目前，儲存並載入功能僅支援基本的物件
* 操作功能表上的文字、 聲音、 視訊和相片的功能表會停用
* 在 [工具] 功能表上的 [播放] 按鈕會清除操作 gizmo

## <a name="sharing-your-sketches"></a>共用您的草圖

您可以使用視訊錄製中的功能 HoloLens 說明 ' 嘿 Cortana 開始/停止錄製 '。 按向上/向下一起為您的草圖的索引鍵的磁碟區。

## <a name="about-the-authors"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon Park</b><br>UX 設計工具 @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>開發人員 @Microsoft</td>
</tr>
</table> 
