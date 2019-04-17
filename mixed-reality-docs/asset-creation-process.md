---
title: 資產建立程序
description: 建立資產，而混合的實境體驗的指引。
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: 資產、 建立、 處理程序、 預算、 多邊形、 材質、 著色器、 效能
ms.openlocfilehash: cec689ab4d44591d2d3e84679c3fe51dba161bc5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596970"
---
# <a name="asset-creation-process"></a>資產建立程序

Windows Mixed Reality 是根據數十年來，Microsoft 投入到 DirectX 的投資。 這表示所有經驗和技術的開發人員有建置 3D 圖形會繼續與 HoloLens 具價值。

您建立專案的資產有許多的圖形和表單。 它們可以包含一系列的紋理/影像、 音訊、 視訊、 3D 模型和動畫。 我們無法開始涵蓋所有可用的專案中建立不同類型的資產使用的工具。 在本文中，我們將著重在 3D 資產建立方法。

![流程概念、 建立、 整合和反覆項目](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*流程概念、 建立、 整合和反覆項目*

## <a name="things-to-consider"></a>要考慮的事項

當查看您想要建立的體驗將它視為**預算**，您可以花嘗試提供最佳體驗。 數目沒有一定的固定限制**多邊形**或是**材質類型**用於您的資產，但更預算的組的權衡取捨。

以下是範例預算，針對您的體驗。 效能不通常是單點失敗，但由一千個剪下每個-se 死亡。
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>資產</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> 記憶體</th>
</tr><tr>
<td> 多邊形</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> 紋理</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> 著色器</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> 物理</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> 即時光源</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> 媒體 （音訊/視訊）</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> 指令碼/邏輯</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> 一般的額外負荷</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>總計</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**資產總數**
* 多少資產裡所有作用中的場景？

**資產的複雜度**
* 多少三角形 / 多邊形嗎？
* 複雜程度是著色器？

開發人員和演出者必須考量的裝置和圖形引擎功能。 Microsoft HoloLens 擁有所有的運算和圖形內建的裝置。 共用的開發人員認為在行動裝置平台的功能。

資產的建立程序是不論是否您設為目標的體驗相同[全像攝影版的裝置或沈浸式裝置](mixed-reality.md#the-mixed-reality-spectrum)。 要注意的主要項目是如先前所述小數位數以及因為您可以在您將想要維護正確的標尺經驗為基礎的混合實境中看到實際的裝置功能。 

## <a name="authoring-assets"></a>撰寫資產

我們將開始取得您的專案中的資產的方式：
1. 建立資產 （撰寫工具和擷取的物件）
2. 購買資產 （線上的名義購買資產）
3. 移植資產 （包含現有的資產）
4. 外包資產 （從第 3 個合作對象的匯入資產）

### <a name="creating-assets"></a>建立資產

**撰寫工具**<br>
第一次，您可以在幾個不同的方式建立您自己的資產。 3D 的演出者會使用許多應用程式和工具來建立模型組成**網狀結構**，**紋理**，並**材料**。 這會接著儲存在可以匯入或使用應用程式，例如圖形引擎所使用的檔案格式 **。FBX**或 **。OBJ**。 任何工具，產生您所選擇的圖形引擎支援的模型將努力**HoloLens**。 在 3D 的演出者之間有許多選擇使用[的 Autodesk Maya 而其本身是能夠使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)轉換方法會建立資產。 如果您想要快速得到您也可以使用[3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)所附 Windows 匯出。在您的應用程式中使用的 OBJ。

**物件擷取**<br>
另外還有擷取中 3D 物件的選項。 擷取以 3D 在意物件及編輯數位內容創作的軟體是越來越受歡迎的 3D 列印興起。 使用**Kinect 2**感應器並[3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)您可以使用 「 擷取 」 功能，從真實世界物件建立資產。 這也是[的工具套件](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software)來執行相同的作業**photogrammetry**藉由處理要編結在一起和網格和紋理的影像數目。

### <a name="purchasing-assets"></a>購買的資產

另一個絕佳的選項是購買資產以供您的體驗。 有許多的資產可透過服務這類[Unity Asset Store](https://www.assetstore.unity3d.com/)或是[TurboSquid](http://www.turbosquid.com/)等等。

當您從第 3 方購買資產時一定要檢查下列項目：
* **什麼是多邊計數？**
  * 它符合您的預算？
* **有模型的詳細資料 (LODs) 層級嗎？**
  * 模型的詳細層級可讓您調整模型的效能詳細資料。
* **是可用的來源檔案？**
  * 通常未隨附[Unity Asset Store](https://www.assetstore.unity3d.com/)一律包含與這類服務，但[TurboSquid](http://www.turbosquid.com/)。
  * 如果沒有來源檔案，您將無法修改資產。
  * 請確定提供的來源檔案可以匯入 3D 的工具。
* **了解您的重點**
  * 所提供的動畫
  * 請務必檢查您要購買的資產的 [內容] 清單。

### <a name="porting-assets"></a>移植的資產

在某些情況下，您會收到原先在建置以及其他裝置和不同的應用程式的現有資產。 在大部分情況下這些資產可以轉換為其應用程式正在使用的圖形引擎與相容的格式。

移植到 HoloLens 應用程式中使用的資產時您會想要提出下列問題：
* **您可以直接匯或需要轉換成另一種格式？** 請檢查您所匯入與您使用的圖形引擎的格式。
* **如果將轉換成相容的格式是任何項目遺失嗎？** 有時可能會遺失，詳細資料，或匯入可能會導致需要清除的 3D 撰寫工具中的成品。
* **什麼是三角形/多邊形計算資產？** 根據您應用程式可以使用預算[Simplygon](https://www.simplygon.com/)或類似的工具，削弱 （可循序或以手動方式減少多邊計數） 以符合您的應用程式的預算內原始的資產。

### <a name="outsourcing-assets"></a>外包資產

針對需要比您小組的多個資產的大型專案的另一個選項是建立配備是外包資產建立。 外包的程序牽涉到在外包資產中尋找正確的 studio 或特製化的機構。 這可以是最昂貴的選項，但是也是最具彈性中得到什麼結果。
* **清楚地定義您要要求**
  * 盡可能提供盡可能詳細的資料
  * 前端、 側邊和回復的概念影像
  * 在內容中的參考圖案顯示資產
  * 小數位數 （通常是以公分為單位指定） 的物件
* **提供在預算**
  * 多邊計數範圍
  * 紋理數目
  * 類型的著色器 （如 Unity 和 HoloLens 您一律應該預設第一次為行動裝置的著色器）
* **了解的成本**
  * 變更要求的外包原則為何？

外包可以運作得非常好根據您的專案時間軸，但需要更多的監督以確保您取得正確的資產，則必須在第一次。
