---
title: Unreal 中的空間音訊
description: 概述 Unreal Engine 的空間音訊外掛程式。
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 串流, 遠端, 混合實境, 開發, 開始使用, 功能, 新專案, 模擬器, 文件, 指南, 功能, 全像投影, 遊戲開發
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446789"
---
# <a name="spatial-audio-in-unreal"></a>Unreal 中的空間音訊

## <a name="overview"></a>概觀

不同於視覺，人類可聽到來自周遭 360 度的聲音。 空間音效會模擬人類聽覺的運作方式，提供識別真實世界中的發聲位置所需的提示。 在混合實境應用程式中新增空間音效後，將可加強使用者體驗的沉浸程度。  

高品質的空間音效處理是很複雜的，因此，HoloLens 2 隨附了專用硬體來處理這些音效物件。  您必須先在 Unreal 專案中安裝 **MicrosoftSpatialSound** 外掛程式，才可存取此硬體處理支援。 本文將逐步引導您完成該外掛程式的安裝和設定，並為您深入介紹在 Unreal Engine 中使用空間音效所需的資源。 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a>安裝 Microsoft 空間音效外掛程式 

將空間音效新增至專案的第一個步驟，是安裝 Microsoft 空間音效外掛程式；您可以透過下列方式找到此外掛程式： 

1. 按一下 [編輯] > [外掛程式]，並在搜尋方塊中搜尋 **MicrosoftSpatialSound**。 
2. 選取 **MicrosoftSpatialSound** 外掛程式中的 [已啟用] 核取方塊。 
3. 在 [外掛程式] 頁面中選取 [立即重新啟動]，將 Unreal 編輯器重新啟動。 

> [!NOTE]
> 若您尚未依照 Unreal 教學課程系列的 **[初始化您的專案](unreal-uxt-ch2.md)** 一節中的指示，安裝 **Microsoft Windows Mixed Reality** 和 **HoloLens** 外掛程式，您必須加以安裝。

![Unreal 空間音訊外掛程式](images/unreal-spatial-audio-img-01.png)

編輯器重新啟動後，您的專案即設定完成。


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a>設定 HoloLens 2 平台的空間化外掛程式
空間化外掛程式的設定須就個別平台來執行。  您可以啟用適用於 HoloLens 2 的 Microsoft 空間音效外掛程式，方法是：
1. 選取 [編輯] > [專案設定] 並捲動至 [平台]，然後按一下 [HoloLens]。
2. 展開 [音訊] 屬性，並將 [空間化外掛程式] 欄位設定為 [Microsoft 空間音效]。

![適用於 HoloLens 平台的空間化外掛程式](images/unreal-spatial-audio-img-02.png)

如果您要在桌上型電腦的 Unreal 編輯器中預覽您的應用程式，您必須對 **Windows** 平台重複上述步驟：

![適用於 Windows 平台的空間化外掛程式](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a>在工作站上啟用空間音訊
Windows 桌面版依預設會停用空間音訊。 您可以透過下列方式加以啟用：
* 以滑鼠右鍵按一下工作列中的 [磁碟區] 圖示。 
    + 選擇 [空間音效] -> [Windows Sonic 耳機版]，以便在 HoloLens 2 上聽到最佳呈現的音效。

![空間化外掛程式](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
>只有您要在 Unreal 編輯器中測試您的專案時，才需要進行此設定。

## <a name="creating-attenuation-objects"></a>建立衰減物件
在您安裝並設定必要的外掛程式後：
1. 在 [放置動作項目] 視窗中搜尋 [環境音效] 動作項目，並將其拖曳至 [場景] 視窗中。

![新增環境音效動作項目](images/unreal-spatial-audio-img-07.png)

2. 讓 [環境音效] 動作項目成為場景中視覺元素的子系。 
    * 環境音效動作項目依預設不會有任何視覺呈現，因此您只會聽到其在場景中的所在位置傳來的聲音。 將其附加至視覺元素，您就可看到該動作項目，並像任何其他資產一樣加以移動。

3.  以滑鼠右鍵按一下 [內容瀏覽器]，然後選取 [建立進階資產] -> [音效] -> [音效衰減]：

![建立音效衰減資產](images/unreal-spatial-audio-img-06.png)

4. 以滑鼠右鍵按一下 [內容瀏覽器] 視窗中的 [音效衰減] 資產，然後選取 [編輯] 選項以顯示 [屬性] 視窗。
    * 將 [空間化方法] 切換為 [雙聲道]。

![設定空間化方法](images/unreal-spatial-audio-img-03.png)

5. 選取 [環境音效] 動作項目，並向下捲動至 [詳細資料] 面板中的 [衰減] 區段。 
    * 將 [衰減設定] 屬性設定為您所建立的 [音效衰減] 資產。

![設定衰減設定](images/unreal-spatial-audio-img-08.png)

6. 藉由更新環境音效動作項目的 [音效] 屬性以指定所要使用的 SoundAsset 檔案，藉以設定要附加至環境音效動作項目的 [音效資產]。

![設定音效資產](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> SoundAsset 檔案必須是單聲道，才能使用 Microsoft 空間音效外掛程式進行空間化。 您可以將滑鼠游標移至 [內容瀏覽器] 視窗中的資產上方，以尋找音效檔案屬性，如下列螢幕擷取畫面所示。

![新的音效衰減資產](images/unreal-spatial-audio-img-10.png)

一切都設定完成後，就可以使用 HoloLens 2 上的專用硬體卸載支援將環境音效空間化。

## <a name="configuring-objects-for-spatialization"></a>設定空間化的物件
使用空間音訊時，表示您將負責管理音效在虛擬環境中的運作方式。 您主要的工作重心，是要建立在使用者靠近時發出較大聲響、並在使用者遠離時較小聲的音效物件。 這就是所謂的音效衰減，聽起來會像是音效物件置於固定之處。

所有衰減物件都附有下列可修改的設定：
* 距離
* 空間化
* 空氣吸收
* 聽覺焦點
* 殘響傳送
* 遮蔽

[Unreal 中的音效衰減](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html)提供每個主題的詳細資料和實作細節。


## <a name="see-also"></a>另請參閱
* [空間音效](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [空間音效設計](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [MR Spatial 220：空間音效](https://docs.microsoft.com/windows/mixed-reality/holograms-220)