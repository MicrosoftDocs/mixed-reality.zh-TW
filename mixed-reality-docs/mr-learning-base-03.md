---
title: 入門教學課程 - 3。 設定 MRTK 設定檔
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2c413964a435814275a1b908770ca977412f92be
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304810"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3.設定 MRTK 設定檔

## <a name="overview"></a>概觀

在本教學課程中，您將了解如何自訂和設定 MRTK 設定檔。

此特定範例將示範如何藉由變更空間網格觀察器的設定，來隱藏空間感知網格。 不過，您也可以遵循這些相同原則，自訂 MRTK 設定檔中的任何設定或值。

## <a name="objectives"></a>目標

* 了解如何自訂和設定 MRTK 設定檔
* 隱藏空間感知網格

## <a name="changing-the-spatial-awareness-display-option"></a>變更空間感知顯示選項

隱藏空間感知網格所需採取的主要步驟如下：

1. 複製預設的組態設定檔
2. 啟用空間感知系統
3. 複製預設的空間感知系統設定檔
4. 複製預設的空間感知網格觀察器設定檔
5. 變更空間感知網格的顯示

> [!NOTE]
> 根據預設，您無法編輯 MRTK 設定檔。 這些是預設的設定檔範本，您必須先加以複製，才能進行編輯。 其中有數個巢狀的設定檔層。 因此，在設定一個或多個設定時，通常會複製及編輯數個設定檔。

### <a name="1-clone-the-default-configuration-profile"></a>1.複製預設的組態設定檔

> [!NOTE]
> 組態設定檔是最上層的設定檔。 因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，將 **MixedRealityToolkit** 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**：

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂] 按鈕來開啟 [複製設定檔] 視窗：

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

在 [複製設定檔] 視窗中，輸入適當的**設定檔名稱**，例如 _GettingStarted_HoloLens2ConfigurationProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultHololens2ConfigurationProfile** 的可編輯複本：

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

新建立的組態設定檔現在已指派為您場景的組態設定檔：

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

在 Unity 功能表中，選取 [檔案] > [儲存]，即可儲存場景。

> [!TIP]
> 請記得在整個教學課程中儲存工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.啟用空間感知系統

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中選取 [空間感知] 索引標籤，然後勾選 [啟用空間感知系統] 核取方塊：

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.複製預設的空間感知系統設定檔

在 [空間感知] 索引標籤中，按一下 [複製] 按鈕以開啟 [複製設定檔] 視窗：

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

在 [複製設定檔] 視窗中，輸入適當的**設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessSystemProfile** 的可編輯複本：

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.複製預設的空間感知網格觀察器設定檔

在仍選取 [空間感知] 索引標籤的情況下，展開 [Windows Mixed Reality 空間網格觀察器] 區段，然後按一下 [複製] 按鈕來開啟 [複製設定檔] 視窗：

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

在 [複製設定檔] 視窗中，輸入適當的**設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.變更空間感知網格的顯示

在 [空間網格觀察器設定] 中，將 [顯示選項] 變更為 [遮蔽]，以隱藏仍在運作的空間對應網格：

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> 雖然空間對應網格看不到，但仍存在且正常運作。 例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。

您方才已了解如何修改 MRTK 設定檔中的設定。 如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。 由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。 若要深入了解 MRTK 設定檔及其架構，您可以參閱 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的 [MRTK 設定檔設定指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何複製、自訂和設定 MRTK 設定檔和設定。

[下一個教學課程：4.將物件置放在場景中](mr-learning-base-04.md)
