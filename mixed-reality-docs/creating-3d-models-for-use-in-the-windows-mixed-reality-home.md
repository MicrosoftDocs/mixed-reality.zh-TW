---
title: 在家中建立使用 3D 模型
description: 資產的需求，並撰寫要用於 HoloLens 和沈浸式 (VR) 耳機家用的 Windows Mixed Reality 的 3D 模型的指引。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D，模型，模型化的指引，資產需求，編寫指導方針、 啟動器、 3D 的啟動器、 紋理、 材料、 複雜度、 三角形、 網狀結構、 多邊形、 polycount，限制
ms.openlocfilehash: 209a92a8e7070ca23bcb9402d8716f3f91747a96
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591393"
---
# <a name="create-3d-models-for-use-in-the-home"></a>在家中建立使用 3D 模型

[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)是使用者啟動應用程式之前的登陸位置的起點。 您可以設計您的應用程式的 Windows Mixed Reality 耳機運用[3D 模型，為應用程式啟動器](implementing-3d-app-launchers.md)，並允許[3D 的深層連結，放入家用的 Windows Mixed Reality](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)從應用程式內。 本文概述的指導方針建立家用的 Windows Mixed Reality 與相容的 3D 模型。

## <a name="asset-requirements-overview"></a>資產需求概觀
建立 3D 模型的 Windows Mixed Reality 時有一些需求，必須符合所有的資產： 
1. [匯出](#exporting-models)-.glb 檔案格式 (二進位 glTF) 必須傳遞資產
2. [模型化](#modeling-guidelines)-資產必須是小於 10 k 三角形，有最多 64 個節點和每個 LOD 32 submeshes
3. [材料](#material-guidelines)-紋理不能大於 4096x4096 和最小的 mip 對應應該是大於任一維度的 4
4. [動畫](#animation-guidelines)-動畫不能超過 20 分鐘 30 FPS （36,000 主要畫面格），而且必須包含 < = 8192 的 morph 目標頂點
5. [最佳化](#optimizations)-資產應該使用最佳化[WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)。 這是**需要在 Windows 作業系統版本 < = 1709年**，建議在 Windows 作業系統版本 > = 1803年

本文的其餘部分包含這些需求，以及額外的指導方針以確保您的模型適用於家用的 Windows Mixed Reality 的詳細的概觀。 

## <a name="detailed-guidance"></a>詳細的指導方針

## <a name="exporting-models"></a>匯出模型

家用的 Windows Mixed Reality 預期 3D 資產傳遞.glb 檔案格式使用內嵌的影像和二進位資料。 Glb 是 glTF 格式，也就是獲微軟授權使用的二進位版本 Khronos 群組所維護的 3D 資產傳遞的免費開放標準。 隨著 glTF 發展為一種業界標準的可互通的 3D 內容也會格式的 Microsoft 的支援在 Windows 應用程式和體驗。 如果您尚未建立 glTF 資產之前，您可以找到[份支援匯出工具和轉換器](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)glTF 工作群組的 github 頁面上。  

## <a name="modeling-guidelines"></a>模型化的指導方針

Windows 必須使用下列的模型化指導方針，以確保相容性與混合實境的居家體驗產生的資產。 在您選擇的程式中建立模型時請記住下列建議事項：
1. 總軸應該設定為"Y"。
2. 資產應該面臨"forward"朝向正 Z 軸。
3. 所有的資產應該建置地面平面在場景的原點 (0,0,0)
4. 工作單位應該設定為計量和資產，以便可以撰寫全球規模的資產
5. 不需要合併所有網路，但仍建議如果您的目標資源受限的裝置
6. 所有的網格應該共用 1 的資料，使用 1 個設定用於整個資產的材質
7. Uv 必須在 0-1 以方形排列配置空間。 雖然它們允許，請避免並排紋理。
8. 不支援多重 Uv
9. 不支援雙單面的材料

### <a name="triangle-counts-and-levels-of-detail-lods"></a>三角形計數和層級的詳細資料 (LODs)

家用的 Windows Mixed Reality 不支援具有超過 10,000 個三角形的模型。 建議您在匯出以確保它們不能超過這個計數之前分成三角形您的網格。 Windows MR 也支援選擇性的幾何以確保高效能且高品質經驗的詳細資料 (LODs) 層級。 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)將協助您將模型的 3 個版本結合成單一.glb 模型。 Windows 會決定顯示 LOD 基礎的模型會佔據的螢幕面積量。 只有 3 個 LOD 層級支援下列建議三角形計數：
<br>

|  LOD 層級  |  建議的三角形計數  |  最大三角形計數 | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>節點計數和子網狀的限制
家用的 Windows Mixed Reality 不支援具有超過 64 個節點或每 LOD 32 submeshes 模型。 節點是中的概念[glTF 規格](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)，場景中定義的物件。 陣列中的定義 submeshes[基本型別](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)物件中 mesh 上。 

|  功能 |  描述  |  最大支援 | 文件 |
|------|------|------|------|
|  節點 |  GlTF 場景中的物件 |  每個 LOD 64 | [這裡](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  基本項目上所有的網格的總和 |  每個 LOD 32 | [這裡](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>材質的指導方針

應該使用 PBR 裸機粗糙度工作流程準備紋理。 開始建立一組完整的包括 Albedo、 Normal、 阻擋、 金屬外觀和粗糙度的紋理。 但其建議的 4096x4096 該您作者的 512 x 512 達 Windows Mixed Reality 支援材質與解決方法。 此外紋理應該撰寫解析度 4 的倍數，這是套用至下面所述的匯出步驟中紋理的壓縮格式的需求。 最後，當 gerating mip 對應，或紋理最低 mip 必須最多 4 x 4 個。
<br>

|  建議的紋理大小  |  最大紋理大小 | 最小的 Mip
|----|----|----|
|  512x512  |  4096x4096 | 最大值 4 x 4|

### <a name="albedo-base-color-map"></a>Albedo （基底的色彩） 對應

不含光源資訊未經處理的色彩。 此對應也包含 reflectance 和金屬 （白色金屬對應中） 和 （黑色金屬對應中） 的 insulator 表面的擴散資訊分別。

### <a name="normal"></a>一般

正切空間一般對應

### <a name="roughness-map"></a>粗糙度對應

描述物件的 microsurface。 白色 1.0 是概略黑色 0.0 是平滑。 此對應可提供最大字元它真正說明了在介面，例如而已的資產、 指紋、 smudges、 grime 等。

### <a name="ambient-occlusion-map"></a>環境阻擋對應

描述區域，它會封鎖反射 occluded 燈光的值擴展對應

### <a name="metallic-map"></a>金屬對應

告知項目是否 metal 著色器。 未經處理的 Metal = 1.0 的白色非 metal = 0.0 黑色。 可以是過渡期的灰色值，指出項目涵蓋灰塵，例如未經處理的裸機，但一般而言此對應應該是僅黑白。

## <a name="optimizations"></a>最佳化

Windows Mixed Reality 首頁會提供一系列的最佳化，在使用自訂延伸模組定義核心 glTF 規格之上。 Windows 版本都需要這些最佳化 < = 1709年，並建議在較新版本的 Windows 上使用。 您可以輕鬆地最佳化任何 glTF 2.0 模型使用[Windows 混合實境資產轉換子可以在 GitHub 上](https://github.com/Microsoft/glTF-Toolkit/releases)。 此工具會執行封裝的正確材質和依下列指定的最佳化。 一般用途建議使用 WindowsMRAssetConverter，但如果您需要更充分掌控體驗，並想要建置最佳化管線然後您可以參考以下的詳細規格。  

### <a name="materials"></a>資料

若要改善載入時間，在混合實境環境中 Windows MR 的資產支援呈現封裝此區段中定義的配置的材質根據封裝的壓縮的 DDS 紋理。 使用參考 DDS 紋理[MSFT_texture_dds 擴充](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)。 強烈建議壓縮紋理。 

#### <a name="hololens"></a>HoloLens

HoloLens 為基礎的混合的實境體驗預期紋理以封裝使用 2 材質的安裝程式，使用下列封裝規格：
<br>

|  glTF 屬性  |  材質  |  封裝配置 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  紅 (R)、 綠 (G) 藍色 (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  一般 (RG)，(B)，粗糙度金屬外觀 (A) | 


壓縮 DDS 紋理時預期會產生下列壓縮每一個 map 上︰
<br>

|  材質  |  預期的壓縮 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>沈浸式 (VR) 耳機

以 PC 為基礎的擬真 (VR) 耳機的 Windows Mixed Reality 體驗預期紋理以封裝使用 3 材質的安裝程式，使用下列封裝規格：

##### <a name="windows-os--1803"></a>Windows OS >= 1803

<br>

|  glTF 屬性  |  材質  |  封裝配置 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  紅 (R)、 綠 (G) 藍色 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusion (R) 粗糙度 (G) 金屬外觀 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  一般 (RG) | 

壓縮 DDS 紋理時預期會產生下列壓縮每一個 map 上︰
<br>

|  材質  |  預期的壓縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS <= 1709
<br>

|  glTF 屬性  |  材質  |  封裝配置 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  紅 (R)、 綠 (G) 藍色 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Roughness (R)，金屬外觀 (G)，(B) 會受阻擋 | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  一般 (RG) | 

壓縮 DDS 紋理時預期會產生下列壓縮每一個 map 上︰
<br>

|  材質  |  預期的壓縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>將網格 LODs

Windows MR 使用 geometry 節點 LODs 呈現不同的層級的詳細資料，根據畫面涵蓋範圍中的 3D 模型。 雖然這項功能就技術上而言不是必要，強烈建議為所有資產。 目前 Windows 支援 3 個層級的詳細資料。 LOD 的預設值為 0，表示最高的品質。 其他 LODs 是循序編號，例如 1、 2 和 get 以漸進方式較低的品質。 [Windows Mixed Reality 資產轉換器](https://github.com/Microsoft/glTF-Toolkit/releases)支援產生接受多個 glTF 模型，並將它們合併成單一資產有效 LOD 層級符合此 LOD 規格的資產。 下表列出預期的 LOD 排序和三角形目標：
<br>

|  LOD 層級  |  建議的三角形計數  |  最大三角形計數 | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

當使用 LODs 一律指定 3 個 LOD 層級。 遺漏 LODs 會導致不呈現為 LOD 系統切換到遺漏的 LOD 層級的非預期的模型。 glTF 2.0 目前不支援 LODs 核心規格的一部分。LODs 應該因此使用來定義[MSFT_LOD 擴充](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)。

### <a name="screen-coverage"></a>螢幕的涵蓋範圍

LODs 會顯示在系統，由每個 LOD 上設定的螢幕涵蓋範圍值為基礎的 Windows Mixed Reality。 目前使用的螢幕空間的更多部分的物件會顯示在較高的 LOD 層級。 螢幕的涵蓋範圍不是核心 glTF 2.0 規格的一部分，而且必須使用 MSFT_ScreenCoverage 「 額外項目 」 一節中指定[MSFT_lod 擴充](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)。
<br>

|  LOD 層級  |  建議的範圍  |  預設範圍 | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  .5 | 
|  LOD 1 |  在 50%-20%  |  .2 | 
|  LOD 2 |  下 20%1%  |  .01 | 
|  LOD 4  |  下 1%  |  - | 

## <a name="animation-guidelines"></a>動畫的指導方針

> [!NOTE]
> 這項功能已加入的一部分[Windows 10 April 2018 Update](release-notes-april-2018.md)。 在舊版的 Windows，這些動畫不播放，不過，它們仍然會載入撰寫根據這篇文章中的指導方針。  

混合的實境首頁 HoloLens 和沈浸式 (VR) 耳機支援動畫的 glTF 物件。 如果您想要觸發您的模型上的動畫，您必須使用動畫對應延伸模組的 glTF 格式。 此延伸模組可讓您觸發 glTF 模型根據使用者出現在世界中的動畫，例如在使用者接近物件，或當他們查看它時觸發動畫。 如果 glTF 物件具有動畫，但不會定義觸發程序就不會回播放動畫。 下一節描述這些觸發程序加入任何動畫的 glTF 物件的一個工作流程。

### <a name="tools"></a>工具
首先，下載下列工具，如果您還沒有它們。 這些工具會讓您輕鬆開啟任何 glTF 模型、 預覽、 變更及另存回 glTF 或.glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [glTF Tools for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>開啟和預覽模型
首先將.glTF 檔案拖曳到編輯器視窗 glTF 模型在 VSCode 中開啟。 請注意，是否您有.glb 而非.glTF 檔案可以匯入使用您所下載 glTF 工具增益集的 VSCode。 請移至 「 檢視]-> [命令選擇區 」 然後開始輸入 「 glTF 「 命令選擇區中，並選取 「 glTF:匯入從 glb 」 這就會出現供您匯入與.glb 檔案選擇器。 

一旦您開啟 glTF 模型應該會看到 [編輯器] 視窗中的 JSON。 請注意，您也可以預覽在即時的 3D 檢視器中使用模型的檔案名稱上按一下滑鼠右鍵，然後選取 「 glTF:預覽 3D 模型 」 以滑鼠右鍵按一下功能表命令快顯。 

### <a name="adding-the-triggers"></a>新增觸發程序
動畫觸發程序加入至 glTF 模型使用動畫對應延伸模組的 JSON。 動畫對應延伸模組有公開記載[這裡的 GitHub 上](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)(注意：這是草稿延伸模組）。 若要將擴充功能新增至您的模型只是捲動至 glTF 檔案在編輯器中的結尾，並將"extensionsUsed 」 和 「 延伸模組 」 區塊新增至您的檔案，如果它們尚不存在。 在 「 extensionsUsed 」 一節中，您將新增 「 EXT_animation_map 」 延伸模組的參考，「 延伸模組 」 區塊中會將您的對應新增到模型中的動畫。

如所述[規格中](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)您定義何者觸發動畫是動畫索引的陣列清單中的 「 動畫 「 使用 」 語意"的字串。 在下列範例中，我們已指定時使用者會在物件 gazing 播放動畫：

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
支援下列動畫觸發程序語意的家用的 Windows Mixed Reality。  
* 「 永遠 」:不斷循環播放動畫
* 「 保留 」:迴圈的整個持續期間將會抓取一個物件。
* 「 視線 」:而查看物件已形成迴路
* 「 鄰近 」:物件附近的檢視器時已形成迴路
* 「 指向 」:當使用者指向的物件已形成迴路

### <a name="saving-and-exporting"></a>儲存和匯出
一次，您可以將它儲存為 glTF 直接 glTF 模型進行變更，或您可以以滑鼠右鍵按一下編輯器，然後選取中的檔案名稱"glTF:匯出至 GLB （二進位檔） 」 改為匯出.glb。 

### <a name="restrictions"></a>限制
動畫不能超過 20 分鐘的時間，而且不能包含多個 36,000 主要畫面格 （在 30 FPS 的 20 分鐘）。 此外當使用 morph 目標式動畫不會超過 8192 morph 目標頂點或更少。 超出這些計數會而且不會支援 Windows Mixed Reality 在家中動畫的資產。 

|功能|最大值|
|-----|-----|
|持續時間|20 分鐘|
|主要畫面格|36,000| 
|Morph 目標頂點|8192|

## <a name="gltf-implementation-notes"></a>glTF 實作注意事項
Windows MR 不支援使用負的標尺的翻轉幾何。 使用負的標尺可能會導致視覺成品的幾何。

GlTF 資產必須指向使用 Windows MR 所呈現的場景屬性的預設場景。 此外之前 Windows MR glTF 載入器[Windows 10 April 2018 update](release-notes-april-2018.md) **需要**存取子：
* 必須具有最小和最大值。
* 純量類型必須是 componentType UNSIGNED_SHORT (5123) 或 UNSIGNED_INT (5125)。
* 型別 VEC2 和 VEC3 必須 componentType FLOAT (5126)。

下列的 material 屬性是使用從核心 glTF 2.0 規格，但不是需要：
* baseColorFactor metallicFactor roughnessFactor
* baseColorTexture:必須指向儲存在 dds 材質。
* emissiveTexture:必須指向儲存在 dds 材質。
* emissiveFactor
* alphaMode

下列的材質屬性，會忽略從核心規格：
* 所有的多個 Uv
* metalRoughnessTexture:必須改為使用下面定義的 Microsoft 最佳化紋理封裝
* normalTexture:必須改為使用下面定義的 Microsoft 最佳化紋理封裝
* normalScale
* occlusionTexture:必須改為使用下面定義的 Microsoft 最佳化紋理封裝
* occlusionStrength

不支援 Windows MR，基本模式線條和點。 

支援只有單一 UV 頂點屬性。

## <a name="additional-resources"></a>其他資源
* [glTF 匯出工具和轉換程式](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 規格](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD 擴充規格](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [混合實境紋理封裝擴充功能規格的電腦](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens 的混合實境紋理封裝擴充功能規格](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS 紋理 glTF 延伸模組規格](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>另請參閱

* [實作 3D 應用程式啟動器 (UWP app)](implementing-3d-app-launchers.md)
* [實作 3D 應用程式啟動器 （Win32 應用程式）](implementing-3d-app-launchers-win32.md)
* [瀏覽家用的 Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
