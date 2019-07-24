---
title: 資產建立流程
description: 建立混合現實體驗資產的指導方針。
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: 資產, 建立, 進程, 預算, 多邊形, 紋理, 著色器, 效能
ms.openlocfilehash: 513a9856ac35e4229cfb7bc8bcb92d9d6a152980
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692296"
---
# <a name="asset-creation-process"></a>資產建立流程

Windows Mixed Reality 建基於 Microsoft 在 DirectX 中所做的數十年投資。 這表示開發人員建立3D 圖形所擁有的所有經驗和技能, 在 HoloLens 方面仍然相當重要。

您為專案建立的資產會有許多圖形和表單。 它們可以由一系列材質/影像、音訊、影片、3D 模型和動畫所組成。 我們無法開始涵蓋可用來建立專案中所使用之不同類型資產的所有工具。 在本文中, 我們將著重于3D 資產建立方法。

![概念、建立、整合和反復專案流程](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*概念、建立、整合和反復專案流程*

## <a name="things-to-consider"></a>要考慮的事項

在查看您的經驗時, 您嘗試將它視為**預算**, 您可以用它來嘗試建立最佳體驗。 您的資產中所使用的**多邊形**或**材質類型**數目不一定會有固定限制, 但會有一組預算的取捨。

以下是您體驗的範例預算。 效能通常不是單一失敗點, 但每個 se 會有一千個剪下的死亡。
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>固定資產</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> 記憶體</th>
</tr><tr>
<td> 多邊形</td><td> 0</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> 紋理</td><td> 5%</td><td> 次</td><td>25%</td>
</tr><tr>
<td> 著色器</td><td> 次</td><td> 35%</td><td> 0</td>
</tr><tr>
<td> <b>特性</b></td><td></td><td></td><td></td>
</tr><tr>
<td> 物理</td><td> 5%</td><td> 次</td><td> 0</td>
</tr><tr>
<td> 即時光源</td><td> 10%</td><td> 0</td><td> 0</td>
</tr><tr>
<td> 媒體 (音訊/影片)</td><td> -</td><td> 次</td><td> 25%</td>
</tr><tr>
<td> 腳本/邏輯</td><td> 25%</td><td> 0</td><td> 5%</td>
</tr><tr>
<td> 一般負擔</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>總數</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**資產總數**
* 場景中有多少個作用中的資產？

**資產的複雜性**
* 有多少三角形/多邊形？
* 著色器有多複雜？

開發人員和演出者都必須考慮裝置和圖形引擎的功能。 Microsoft HoloLens 具有內建于裝置的所有計算和圖形。 它會分享開發人員可在行動平臺上找到的功能。

無論您是以全像攝影[裝置或沉浸式裝置](mixed-reality.md#the-mixed-reality-spectrum)的體驗為目標, 資產的建立程式都是一樣的。 要注意的主要事項是如上所述的裝置功能以及規模, 因為您可以在混合現實中看到真實世界, 您會想要根據經驗來維持正確的規模。 

## <a name="authoring-assets"></a>撰寫資產

我們將從為您的專案取得資產的方法開始:
1. 建立資產 (撰寫工具和物件捕捉)
2. 購買資產 (線上購買資產)
3. 移植資產 (取得現有資產)
4. 外包資產 (匯入協力廠商的資產)

### <a name="creating-assets"></a>建立資產

**撰寫工具**<br>
首先, 您可以使用數種不同的方式來建立自己的資產。 3D 演出者會使用一些應用程式和工具來建立包含**網格**、**材質**和**材質**的模型。 然後, 這會以檔案格式儲存, 以供應用程式使用的圖形引擎 (例如) 匯入或使用 **。FBX**或 **。OBJ**。 任何會產生所選圖形引擎支援之模型的工具, 都可以在**HoloLens**上使用。 在3D 演出者之間, 許多選擇使用[Autodesk 的 Maya, 其本身能夠使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)來轉換資產的建立方式。 如果您想要取得快速的內容, 也可以使用隨附于 Windows 的[3d](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)產生器來進行匯出。要在您的應用程式中使用的 OBJ。

**物件捕獲**<br>
另外還有在3D 中捕捉物件的選項。 透過3D 列印的增加, 在3D 中捕捉無生命物件, 並使用數位內容建立軟體進行編輯。 使用**Kinect 2**感應器和[3d Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) , 您可以使用 [捕捉] 功能, 從真實世界的物件建立資產。 這也是一[套工具](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software), 可透過處理多個要裝訂在一起的影像, 以及網格和紋理來執行相同的**攝影測量**。

### <a name="purchasing-assets"></a>購買資產

另一個絕佳的選項是購買資產以獲得您的體驗。 服務中有大量的資產可供使用, 例如[Unity 資產存放區](https://www.assetstore.unity3d.com/)或[TurboSquid](http://www.turbosquid.com/)其他。

當您從協力廠商購買資產時, 您一定會想要檢查下列事項:
* **Poly 計數為何？**
  * 它是否符合您的預算？
* **模型有何層級的詳細資料 (LODs)？**
  * 模型的詳細資料層級可讓您針對效能調整模型的詳細資料。
* **來源檔案是否可用？**
  * 通常不會包含在[Unity 資產存放區](https://www.assetstore.unity3d.com/)中, 但一律會包含在服務 (例如[TurboSquid](http://www.turbosquid.com/)) 中。
  * 若沒有原始檔, 您將無法修改資產。
  * 請確定您的3D 工具可以匯入所提供的來源檔案。
* **瞭解您所取得的內容**
  * 是否提供動畫？
  * 請務必檢查您所購買資產的 [內容] 清單。

### <a name="porting-assets"></a>移植資產

在某些情況下, 您會將原本針對其他裝置和不同應用程式建立的現有資產遞交給您。 在大部分情況下, 這些資產可以轉換成與應用程式所使用之圖形引擎相容的格式。

當您在 HoloLens 應用程式中移植資產以使用時, 您會想要詢問下列事項:
* **您可以直接匯入, 還是需要轉換成另一種格式？** 請使用您所使用的圖形引擎來檢查您要匯入的格式。
* **如果轉換成相容的格式會遺失任何專案嗎？** 有時候詳細資料可能會遺失或匯入可能會導致需要在 3D authoring tool 中清除的成品。
* **資產的三角形/多邊形計數為何？** 根據您應用程式的預算, 您可以使用[Simplygon](https://www.simplygon.com/)或類似工具來刪減 (cti 或手動減少 poly 計數) 原始資產, 以符合您的應用程式預算。

### <a name="outsourcing-assets"></a>外包資產

對於需要比您的小組建立的更多資產的大型專案, 另一個選項是將資產建立外包。 外包的程式牽涉到尋找專門從事外包資產的適當 studio 或機構。 這可能是成本最高的選項, 但也是您取得的最具彈性。
* **清楚地定義您所要求的內容**
  * 盡可能提供最多詳細資料
  * Front、側視圖和 back 概念影像
  * 顯示內容中資產的參考圖片
  * 物件的小數值 (通常以釐米指定)
* **提供預算**
  * Poly 計數範圍
  * 紋理數目
  * 著色器的類型 (適用于 Unity 和 HoloLens, 請一律先預設為行動著色器)
* **瞭解成本**
  * 變更要求的外包原則是什麼？

外包可以根據您的專案時間軸來執行得非常順利, 但需要更多監督, 以確保您第一次取得所需的適當資產。
