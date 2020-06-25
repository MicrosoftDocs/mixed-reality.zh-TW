---
title: 手動教練
description: 當系統偵測不到使用者的手協助時，所觸發的3D 手。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、手勢、沉浸式耳機、MRTK、手中的協助
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345660"
---
# <a name="hand-coach"></a>手動教練
![範例：手型教練](images/HandCoach/MRTK_handCoach.jpg)<br>

「手動操作」是一種3D 模型化的手，會在系統未偵測到使用者手時觸發。 這會實作為「教學」元件，可在未教授手勢時協助引導使用者。 如果使用者尚未針對某個時間執行指定的手勢，則手會以延遲方式迴圈。 右手教練可用來代表按下按鈕或挑選全像投影。  

## <a name="hand-coach-provided"></a>提供的手形指導

目前的互動模型代表各種手勢控制項，例如 [滾動]、[遠選] 和 [近碰點]。 以下是<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets">MRTK</a>中所提供之現有右手手勢的完整清單：

:::row:::
    :::column:::
       ![近乎選取的範例](images/HandCoach/NearSelect.gif)<br>
       **接近選取使用方式的範例示範如何選取按鈕或關閉可互動物件**<br>
    :::column-end:::
    :::column:::
       ![點擊點的範例](images/HandCoach/AirTap.gif)<br>
        **點一下的範例-用來示範如何選取距離最遠的物件**<br>
    :::column-end:::
    :::column:::
       ![移動的範例](images/HandCoach/Move.gif)<br>
       **在空間中移動物件的範例-用來示範如何在空間中移動全息影像**<br>
    :::column-end:::
    :::column:::
       ![旋轉的範例](images/HandCoach/Rotate.gif)<br>
       **旋轉範例-用來示範如何旋轉全息影像或物件**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![調整的範例](images/HandCoach/Scale.gif)<br>
       **縮放的範例，用來顯示如何操作全像更大的全息影像**<br>
    :::column-end:::
    :::column:::
       ![Palm 的範例](images/HandCoach/PalmUp.gif)<br>
        **掌上-建議使用的範例，以顯示功能表**<br>
    :::column-end:::
    :::column:::
       ![HandFlip 的範例](images/HandCoach/HandFlip.gif)<br>
       **右手手勢範例–另一種顯示功能表的方式**<br>
    :::column-end:::
    :::column:::
       ![Scroll 的範例](images/HandCoach/Scoll.gif)<br>
       **Scroll 範例-用於滾動清單或長檔**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>設計概念

針對 Hololens2，我們設計了根據本能和自然手勢的手動互動。 我們相信大部分使用者都可以直覺化，因此不會建立專用的手勢學習。 相反地，我們建立了手勢來協助可能停滯或不熟悉與全息影像互動的使用者瞭解這些手勢。 如果沒有學習時間，我們覺得顯示使用者如何藉由示範來執行動作，是最佳選項。 在我們的研究中，我們發現使用者能夠找出手勢，但需要一些指引。 如果我們偵測到使用者沒有與某個期間的物件互動，就會觸發右手的指示來示範正確的手和手指位置。 

### <a name="intuitive"></a>基本

以動畫顯示時，應該很明顯，而且 shoudn't 會造成混淆。 手的動畫表示您嘗試呼叫給使用者的手勢，以瞭解其用途。 

例如，如果您希望使用者按下按鈕，就會觸發按下按鈕的手。

![範例：靠近點一下的手勢](images/HandCoach/NearSelect_unity.gif)<br>
*示範近乎點擊 Gem 的手勢*  

### <a name="hand-scale"></a>右手小

我們使用 UI 功能表測試了各種不同的大小，並覺得如果手中真的要調整大小，就會有 menacing 的感受，但如果太小，則很難查看並瞭解手勢。 

**聲音和手**

不預期使用者可以透過 voice 接聽一組指示，並透過手動指示觀看不同的指示。 排序您的指示，協助使用者專注于競爭，以減少感應式多載。


## <a name="can-i-create-my-own"></a>我可以建立自己的嗎？

可以！ 我們鼓勵您為遊戲建立自己獨特的手勢，並向您貢獻給此社區！
我們提供了 Rigged 手的 Maya 檔案，可用於您的應用程式，您可以從這裡下載：<a href="files/HandCoach_MRTK.zip">下載 HandCoach_MRTK.zip</a>

![Maya 中的動畫實習範例](images/HandCoach/MayaSelect_Gif.gif)<br>
*Maya 中的動畫手勢刺探的範例*


**建議的 authoring tool**

在3D 演出者之間，許多選擇使用[Autodesk 的 Maya，其本身能夠使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)來轉換資產的建立方式。 提供的實習檔案是 Maya 二進位檔案，因此建議使用 Maya 來建立動畫並匯出手。 如果您想要使用另一個3D 程式，以下是<b>。FBX</b>：<a href="files/HandCoachMRTK_FBX.zip">下載 HandCoachMRTK_FBX.zip</a>以建立您自己的控制器設定。 

如果使用提供的可下載 maya 手檔案，建議您將 unity 中的手向下延展至0.6。

![範例： Maya 中的手動教練 rig](images/HandCoach/MayaExample.png)<br>
*Rigged 手*

### <a name="technical-specs"></a>技術規格

*   有兩個檔案是以 Maya Ascii 格式提供
*    右方和左側提供 Maya 二進位格式
*   將您的 Maya 檔案設定為 24 FPS
*   在檔案中，有左右的右手邊，可用於兩個右手式或單一右手手勢。 預設只會顯示右手邊。
*   建議在開頭和結尾保留大約10個畫面的緩衝區以淡化
*   如果以指定的目標建立物件的動畫，其最佳作法是以動畫顯示預設方塊或 Null。
*   如果手以動畫顯示實體物件（例如方塊），其最佳做法是不要在 Maya 中建立轉譯的動畫，而是在 Unity 或程式碼中等待以動畫顯示。
*   可見的動畫應為1.5 秒，才能傳達有意義的資訊
*   當您感到滿意動畫時：
    *   選取所有接點並製作主要畫面格
    *   刪除控制器，選取接點和網格並匯出為 FBX
    *  如果有多個動畫，您可以使用 Maya 的內建遊戲匯出工具：https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>從 Maya 匯出

在您滿意動畫之後
* 選取所有接點：選取 > 階層

     ![範例：功能表位置](images/HandCoach/Hierarchy.png)<br>
* 製作動畫：切換至動畫 > 鍵 > 製作動畫

     ![範例：功能表位置](images/HandCoach/BakeAnimation.png)<br>
* 刪除控制器 Rig： Outliner > MainR_Grp 或 MainL_Grp

     ![範例：功能表位置](images/HandCoach/ControllerRig.png)<br>

* 匯出為 FBX：選取 .JNT + 網格：檔案 > 匯出選取專案（選項框） > 匯出選取專案

     ![範例：功能表位置](images/HandCoach/OptionBox.png)<br>

     ![範例：功能表位置](images/HandCoach/SelectionExport.png)<br>

     ![範例：功能表位置](images/HandCoach/FBXSelection.png)<br>


 當匯出為 FBX 並帶入 Unity 時，請將其向下調整為0.6。 我們發現這是顯示手的完美平衡。 

![範例： Unity 設定](images/HandCoach/HandHintScale.png)<br>
*在 MRTK 中找到 HandCoach_R prefab 的 Unity 設定*


## <a name="implementing-hands-into-your-unity-project"></a>實作為 Unity 專案的實際執行

### <a name="best-practices"></a>最佳作法
*    建議您將 unity 中的手擴充至0。6
*   應播放兩次手，如果未完成，則會持續迴圈直到手勢完成為止。 應該將手迴圈兩次，以確保使用者有時間註冊並查看手勢。 手應該在迴圈之間淡入和移出。 
 *  如果 HL2 攝影機看得到使用者的手，但是使用者不會執行所需的互動，則手會在10秒後出現。
*   如果 HL2 攝影機看不到使用者的手，則手會在5秒後出現。  
*   如果動畫中間的 HL2 攝影機會以明顯的方式追蹤使用者的手，動畫將會完成並淡出。
*   如果您要包含 voice，建議您將它對應到手的手勢。
*   如果您至少已教授過一次，只會在偵測到使用者停滯時，才重複手勢。
*   如果特定手指/手位置非常重要，請確保使用者可以清楚地在動畫中看到這些細節。 試著 angling 手，讓最重要的部分清楚可見。 
* 如果您注意到手上的失真，您需要移至 Unity 的品質設定，以增加骨骼的數量。 
 前往 Unity 的編輯 > 專案設定 > 品質 > 其他 > Blend 權數。 請確定已選取 [4 個骨骼]，以查看平滑接點。 

   ![範例：功能表位置](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a>避免事項
* 調整太大的手
* 將手放在靠近使用者的附近
* 手上應該只教授一次。 透過教學可能會造成混淆和 messiness
*   將它帶入 Unity，請在這裡下載最新的 MRTK：https://github.com/microsoft/MixedRealityToolkit-Unity
    *   材質： Teaching_Hand2
    *   腳本：請參閱<a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">MRTK 手勢指導</a>的 MRTK 指導方針
    *   每個專案的設定
        *   場景設定為 UWP：指示可在適用于 Windows Mixed Reality 的[Configure Unity 專案](Configure-Unity-Project.md)中找到

## <a name="see-also"></a>另請參閱
* [互動-基本概念](interaction-fundamentals.md)
* [資產建立流程](asset-creation-process.md)
* [軌跡](gestures.md)
* [安裝工具](install-the-tools.md)
* [設定 Unity 專案](Configure-Unity-Project.md)
* [Unity 開發概觀](unity-development-overview.md)
* [MRTK 101](mrtk-101.md)
