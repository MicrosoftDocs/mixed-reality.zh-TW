---
title: 建立要在首頁中使用的3D 模型
description: 適用于在 HoloLens 和沉浸式 (VR) 耳機的 Windows Mixed Reality 首頁中使用的3D 模型的資產需求和撰寫指導方針。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, 模型化, 指南, 資產需求, 撰寫方針, 啟動器, 3D 啟動器, 材質, 材質, 複雜度, 三角形, 網格, 多邊形, polycount, 限制
ms.openlocfilehash: 73af40cf2915742cab612625c8243a36ee74d748
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692291"
---
# <a name="create-3d-models-for-use-in-the-home"></a>建立要在首頁中使用的3D 模型

[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。 您可以為 Windows Mixed Reality 耳機設計應用程式, 以將[3d 模型作為應用程式啟動器](implementing-3d-app-launchers.md), 並允許將[3d 深層連結放入應用程式內的 Windows Mixed Reality 首頁](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)。 本文概述建立與 Windows Mixed Reality 首頁相容之3D 模型的指導方針。

## <a name="asset-requirements-overview"></a>資產需求總覽
建立適用于 Windows Mixed Reality 的3D 模型時, 所有資產都必須符合下列需求: 
1. [匯出](#exporting-models)-資產必須以 glb 檔案格式傳遞 (二進位 glTF)
2. [模型](#modeling-guidelines)-資產必須小於10k 三角形、每個 LOD 不超過64個節點和 32 submeshes
3. [材質](#material-guidelines) - 材質不能大於 4096 x 4096, 且最小 mip 對應在任一維度上都不能大於4
4. [動畫](#animation-guidelines)-動畫的長度不能超過20分鐘 30 FPS (36000 主要畫面), 而且必須包含 < = 8192 的變形目標頂點
5. [優化](#optimizations)-資產應該使用[WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)來優化。 這**在 WINDOWS 作業系統版本上是必要的 < = 1709** , 建議在 windows 作業系統版本 > = 1803

本文的其餘部分包含這些需求的詳細總覽, 以及額外的指導方針, 以確保您的模型適用于 Windows Mixed Reality 首頁。 

## <a name="detailed-guidance"></a>詳細指引

### <a name="exporting-models"></a>匯出模型

Windows Mixed Reality home 需要使用 glb 檔案格式搭配內嵌影像和二進位資料來傳遞3D 資產。 Glb 是 glTF 格式的二進位版本, 這是由 Khronos 群組維護之3D 資產傳遞的免費專利標準。 隨著 glTF 發展為可互通3D 內容的業界標準, Microsoft 也會支援跨 Windows 應用程式和體驗的格式。 如果您尚未建立 glTF 資產, 您就可以在 glTF 工作群組 github 頁面上找到[支援的匯出工具和轉換器清單](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)。  

### <a name="modeling-guidelines"></a>模型化方針

Windows 預期會使用下列模型化指導方針來產生資產, 以確保與混合現實家庭體驗的相容性。 當您選擇的程式模型化時, 請記住下列建議和限制:
1. 向上軸應該設定為 "Y"。
2. 資產應該朝正 Z 軸「順向」。
3. 所有資產都應建置於場景原點的地面 (0, 0, 0)
4. 工作單位應設定為計量和資產, 讓資產能夠以全球規模撰寫
5. 所有的網格都不需要合併, 但如果您的目標是資源受限裝置, 則建議使用此選項。
6. 所有的網格都應該共用1個材質, 其中只有1個材質集用於整個資產
7. UVs 必須以0-1 空間中的正方形排列來配置。 避免並排材質, 但允許使用。
8. 不支援多 UVs
9. 不支援雙面材質

### <a name="triangle-counts-and-levels-of-detail-lods"></a>三角形計數和詳細資料層級 (LODs)

Windows Mixed Reality home 不支援具有超過10000三角形的型號。 建議您先分成三角形您的網格再進行匯出, 以確保它們不會超過此計數。 Windows MR 也支援選擇性幾何層級的詳細資料 (LODs), 以確保效能和高品質的體驗。 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)將協助您將模型的3個版本結合成單一的 glb 模型。 Windows 會根據模型所佔用的畫面實際資產量, 決定要顯示的 LOD。 僅支援3個 LOD 層級, 並具有下列建議的三角形計數:
<br>

|  LOD 層級  |  建議的三角形計數  |  最大三角形計數 | 
|------|------|------|
|  LOD 0 |  10000 |  10000 | 
|  LOD 1 |  5000  |  10000 | 
|  LOD 2 |  2500  |  10000 | 

### <a name="node-counts-and-submesh-limits"></a>節點計數和 submesh 限制
Windows Mixed Reality home 不支援每個 LOD 具有超過64個節點或 32 submeshes 的模型。 節點是[glTF 規格](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)中的概念, 可定義場景中的物件。 Submeshes 是在物件的網格的[基本](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)陣列中定義。 

|  功能 |  描述  |  支援的最大值 | 文件 |
|------|------|------|------|
|  節點 |  GlTF 場景中的物件 |  每 LOD 64 | [如下](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  所有網格的基本類型總和 |  每 LOD 32 | [如下](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>材料指導方針

材質應使用 .PBR 金屬粗糙度工作流程來準備。 一開始先建立一組完整的紋理, 包括 Albedo、Normal、遮蔽、金屬和粗糙度。 Windows Mixed Reality 支援最多4096x4096 的材質, 但建議您在512x512 撰寫。 此外, 材質應以4的倍數撰寫, 因為這是在匯出步驟中套用至紋理的壓縮格式需求, 如下所述。 最後, 當 gerating mip 對應或材質時, 最低 mip 必須最大為4x4。
<br>

|  建議的材質大小  |  最大材質大小 | 最低 Mip
|----|----|----|
|  512x512  |  4096x4096 | 最大4x4|

### <a name="albedo-base-color-map"></a>Albedo (基底色彩) 地圖

沒有光源資訊的原始色彩。 此地圖也包含金屬的 reflectance 和擴散資訊 (金屬地圖中的白色) 和 insulator (金屬地圖中的黑色) 介面。

### <a name="normal"></a>一般

正切空格法線對應

### <a name="roughness-map"></a>粗糙度地圖

描述物件的 microsurface。 白色1.0 是粗略的黑色0.0。 此地圖會為資產提供最大的字元, 因為它真正描述了表面, 例如劃痕、指紋、塗抹、grime 等等。

### <a name="ambient-occlusion-map"></a>環境遮蔽地圖

描述會封鎖反射之 pixels occluded light 區域的值縮放地圖

### <a name="metallic-map"></a>金屬圖

如果某個專案為金屬, 則告訴著色器。 原始金屬 = 1.0 白色非金屬 = 0.0 黑色。 可能會有一些過渡的灰色值, 表示涵蓋原始金屬的東西 (例如灰塵), 但一般而言, 此地圖應該只有黑色和白色。

## <a name="optimizations"></a>優化

Windows Mixed Reality home 在使用自訂延伸模組定義的核心 glTF 規格之上, 提供一系列的優化。 Windows 版本需要這些優化 < = 1709, 而且建議在較新版本的 Windows 上使用。 您可以使用[GitHub 上提供的 Windows Mixed Reality 資產轉換器](https://github.com/Microsoft/glTF-Toolkit/releases), 輕鬆地將任何 glTF 2.0 模型優化。 此工具會執行正確的紋理封裝和優化, 如下所示。 針對一般用途, 我們建議使用 WindowsMRAssetConverter, 但如果您需要更充分掌控經驗, 而且想要建立您自己的優化管線, 您可以參閱下面的詳細規格。  

### <a name="materials"></a>涉及

為了改善混合現實環境中的資產載入時間, Windows MR 支援根據本節中定義的材質封裝配置來轉譯壓縮的 DDS 材質。 DDS 材質會使用[MSFT_texture_dds 延伸](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)模組來參考。 強烈建議您壓縮紋理。 

#### <a name="hololens"></a>HoloLens

HoloLens 型混合現實體驗使用下列封裝規格, 透過2個材質設定來封裝紋理:
<br>

|  glTF 屬性  |  層  |  封裝配置 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  紅色 (R)、綠色 (G)、藍色 (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  標準 (RG)、粗糙度 (B)、金屬 (A) | 


壓縮 DDS 材質時, 每個對應上預期會有下列壓縮:
<br>

|  層  |  預期的壓縮 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>沉浸式 (VR) 耳機

以電腦為基礎的沉浸式 Windows Mixed Reality 使用經驗 (VR) 耳機會使用下列封裝規格, 透過3個材質設定來封裝紋理:

##### <a name="windows-os--1803"></a>Windows 作業系統 > = 1803

<br>

|  glTF 屬性  |  層  |  封裝配置 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  紅色 (R)、綠色 (G)、藍色 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  遮蔽 (R)、粗糙度 (G)、金屬 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  一般 (RG) | 

壓縮 DDS 材質時, 每個對應上預期會有下列壓縮:
<br>

|  層  |  預期的壓縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows 作業系統 < = 1709
<br>

|  glTF 屬性  |  層  |  封裝配置 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  紅色 (R)、綠色 (G)、藍色 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  粗糙度 (R)、金屬 (G)、遮蔽 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  一般 (RG) | 

壓縮 DDS 材質時, 每個對應上預期會有下列壓縮:
<br>

|  層  |  預期的壓縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>新增網格 LODs

Windows MR 使用幾何節點 LODs, 根據螢幕涵蓋範圍, 在不同的詳細資料層級中轉譯3D 模型。 雖然在技術上並不需要這項功能, 但強烈建議所有資產。 目前 Windows 支援三種層級的詳細資料。 預設 LOD 為 0, 代表最高品質。 其他 LODs 會依序編號, 例如 1, 2, 且品質逐漸降低。 [Windows Mixed Reality 資產轉換器](https://github.com/Microsoft/glTF-Toolkit/releases)支援藉由接受多個 glTF 模型並將其合併至具有有效 LOD 層級的單一資產, 來產生符合此 LOD 規格的資產。 下表概述預期的 LOD 順序和三角形目標:
<br>

|  LOD 層級  |  建議的三角形計數  |  最大三角形計數 | 
|-------|-------|-------|
|  LOD 0 |  10000 |  10000 | 
|  LOD 1 |  5000  |  10000 | 
|  LOD 2 |  2500  |  10000 | 

使用 LODs 時, 請一律指定3個 LOD 層級。 遺漏 LODs 會導致模型不會意外轉譯, 因為 LOD 系統切換到遺失的 LOD 層級。 glTF 2.0 目前不支援 LODs 作為核心規格的一部分。因此, 應該使用[MSFT_LOD 延伸](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)模組來定義 LODs。

### <a name="screen-coverage"></a>畫面涵蓋範圍

LODs 會根據每個 LOD 上設定的螢幕涵蓋範圍值所驅動的系統, 以 Windows Mixed Reality 的形式顯示。 目前耗用較大部分螢幕空間的物件會顯示在較高的 LOD 層級上。 螢幕涵蓋範圍不是核心 glTF 2.0 規格的一部分, 而且必須使用[MSFT_lod 擴充](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)功能的「額外專案」區段中的 MSFT_ScreenCoverage 來指定。
<br>

|  LOD 層級  |  建議範圍  |  預設範圍 | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  .5 | 
|  LOD 1 |  低於 50%-20%  |  .2 | 
|  LOD 2 |  低於 20%-1%  |  乘 | 
|  LOD 4  |  低於 1%  |  - | 

## <a name="animation-guidelines"></a>動畫指導方針

> [!NOTE]
> 這項功能已新增為[Windows 10 2018 年4月更新](release-notes-april-2018.md)的一部分。 在舊版的 Windows 上, 這些動畫將不會播放, 不過, 如果是根據本文中的指導方針來撰寫, 它們仍然會載入。  

混合現實首頁支援 HoloLens 和沉浸式 (VR) 耳機上的動畫 glTF 物件。 如果您想要在模型上觸發動畫, 您必須使用 glTF 格式的動畫對應延伸模組。 此延伸模組可讓您根據世界各地的使用者, 在 glTF 模型中觸發動畫, 例如, 在使用者接近物件或正在查看時觸發動畫。 如果您 glTF 物件具有動畫, 但未定義觸發程式, 則不會播放動畫。 下一節說明將這些觸發程式新增至任何動畫 glTF 物件的工作流程。

### <a name="tools"></a>工具
首先, 下載下列工具 (如果您還沒有的話)。 這些工具可讓您輕鬆地開啟任何 glTF 模型、加以預覽、進行變更, 然後再存回 glTF 或 glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [適用于 Visual Studio Code 的 glTF 工具](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>開啟和預覽模型
首先, 將 glTF 檔案拖曳至編輯器視窗中, 以開啟 VSCode 中的 glTF 模型。 請注意, 如果您有 glb 而不是 glTF 檔案, 則可以使用您下載的 glTF 工具增益集將它匯入 VSCode。 移至 View-> 命令選擇區, 然後開始在命令選擇區中輸入 "glTF", 然後選取 glTF:從 glb 匯入, 這會顯示檔案選擇器, 讓您匯入含有的 glb。 

開啟 glTF 模型之後, 您應該會在編輯器視窗中看到 JSON。 請注意, 您也可以使用以滑鼠右鍵按一下檔案名, 然後選取 glTF:, 在即時3D 檢視器中預覽模型。預覽3D 模型 命令快捷方式, 從右鍵功能表中按一下。 

### <a name="adding-the-triggers"></a>新增觸發程式
動畫觸發程式會使用動畫對應延伸模組新增至 glTF 模型 JSON。 在[GitHub 上](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md), 動畫對應延伸模組是公開記載的 (注意:這是草稿延伸模組)。 若要將擴充功能加入至模型, 只要在編輯器中滾動到 glTF 檔案的結尾, 並將 "extensionsUsed" 和 "extension" 區塊新增至您的檔案 (如果它們還不存在的話)。 在 "extensionsUsed" 區段中, 您會新增 "EXT_animation_map" 擴充功能的參考, 並在 "extensions" 區塊中新增對應至模型中的動畫。

如[規格](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)所述, 您定義了在「動畫」清單上使用「語義」字串來觸發動畫的內容, 這是一種動畫索引陣列。 在下面的範例中, 我們指定在物件上撥雲見日使用者時要播放的動畫:

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
Windows Mixed Reality home 支援下列動畫觸發程式的語法。  
* 「一律」:不斷迴圈動畫
* 「保留」:在物件所抓取的整個持續期間內迴圈。
* 「注視」:正在查看物件時進行迴圈
* 「鄰近性」:在檢視器接近物件時進行迴圈
* 「指向」:當使用者指向物件時進行迴圈

### <a name="saving-and-exporting"></a>儲存和匯出
對 glTF 模型進行變更之後, 您可以直接將其儲存為 glTF, 或以滑鼠右鍵按一下編輯器中的檔案名, 然後選取 glTF:匯出至 GLB (二進位檔) 以改為匯出 GLB。 

### <a name="restrictions"></a>限制
動畫的長度不能超過20分鐘, 且不能包含超過36000個主要畫面格 (20 分鐘, 30 FPS)。 此外, 使用以平滑目標為基礎的動畫時, 不會超過8192的平滑目標頂點或更少。 超過這些計數會執行在 Windows Mixed Reality 首頁中不支援的動畫資產。 

|功能|最大值|
|-----|-----|
|Duration|20 分鐘|
|幀|36,000| 
|變形目標頂點|8192|

## <a name="gltf-implementation-notes"></a>glTF 執行注意事項
Windows MR 不支援使用負值縮放來翻轉幾何。 具有負值尺規的幾何可能會導致視覺成品。

GlTF 資產必須使用由 Windows MR 轉譯的場景屬性, 指向預設場景。 此外, windows [10 2018 年4月更新](release-notes-april-2018.md)之前的 Windows MR glTF 載入器**需要**存取子:
* 必須有 min 和 max 值。
* 類型純量必須是 componentType UNSIGNED_SHORT (5123) 或 UNSIGNED_INT (5125)。
* 類型 VEC2 和 VEC3 必須是 componentType FLOAT (5126)。

下列材質屬性是從 core glTF 2.0 規格使用, 但不是必要的:
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture:必須指向儲存在 dds 中的材質。
* emissiveTexture:必須指向儲存在 dds 中的材質。
* emissiveFactor
* AlphaMode

下列材質屬性會從核心規格中忽略:
* 所有多 UVs
* metalRoughnessTexture:必須改為使用下面定義的 Microsoft 優化材質封裝
* normalTexture:必須改為使用下面定義的 Microsoft 優化材質封裝
* normalScale
* occlusionTexture:必須改為使用下面定義的 Microsoft 優化材質封裝
* occlusionStrength

Windows MR 不支援基本模式線和點。 

僅支援單一 UV 頂點屬性。

## <a name="additional-resources"></a>其他資源
* [glTF 匯出工具和轉換器](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF 工具組](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 規格](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD 擴充功能規格](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [電腦混合現實材質封裝延伸模組規格](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens Mixed Reality 材質封裝延伸模組規格](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS 材質 glTF 擴充功能規格](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>另請參閱

* [實作 3D 應用程式啟動器 (UWP 應用程式)](implementing-3d-app-launchers.md)
* [實作 3D 應用程式啟動器 (Win32 應用程式)](implementing-3d-app-launchers-win32.md)
* [瀏覽 Windows Mixed Reality 住家](navigating-the-windows-mixed-reality-home.md)
