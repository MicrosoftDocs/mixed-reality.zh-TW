---
title: 眼部目光和停駐
description: 眼部目光和停駐輸入模型的概觀
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: 眼球追蹤, Mixed Reality, 輸入, 眼部注視, 眼部定向, HoloLens 2, 眼動式選取, 停駐
ms.openlocfilehash: ba793f6b1a95fe4b95aa9a043d36823487886b5e
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604899"
---
# <a name="eye-gaze-and-dwell"></a>眼部目光和停駐

「眼部目光和停駐」  互動模型是[眼部目光和行動](gaze-and-commit.md)互動模型的一個特殊案例：
1. 只需觀看目標，而 
2. 若要確認您選取此目標的意圖，請執行次要明確輸入：只要持續看著您要選取的目標。 

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a>眼部目光和停駐互動模型的優點 
當您的手上已有工作或持有工具時，可能沒辦法使用雙手來與全像投影互動。
選取全像投影的無手互動方式是「眼部目光和停駐」，也就是「觀看並注視」  。 這種方法的優點是，即使是可能無法完全轉動頭部或身體的嚴重受限使用者，也可以與全像投影互動 (例如，在高度限制的工作環境中)。
使用者只要持續看著想要選取的目標，螢幕上就會顯示不同的停駐回饋來指示進度。


## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a>眼部目光和停駐互動模型的挑戰
一般來說，我們建議您只在無法使用語音輸入或手部輸入的情況下，才使用停駐型互動來做為最後的遞補。 原因是停駐時間的選擇可能會很棘手。 新手使用者可以接受較長時間的停駐，而熟練的使用者則想要較快速有效率的瀏覽體驗。 這會導致如何將停駐時間調整為使用者特定需求的挑戰。
如果停駐時間太短：使用者可能會因為全像投影隨時都在反應其眼部目光而應接不暇。 如果停駐時間太長：體驗可能會變得太慢和斷續，因為使用者必須一直長時間看著目標。

## <a name="design-recommendations"></a>設計建議
我們建議您對停駐回饋採取兩個狀態的做法：
1. 啟動延遲  ：當使用者開始注視目標時，不要立即發生任何事，因為這可能會導致使用者應接不暇的不愉快體驗。 改成啟動計時器來偵測使用者是刻意在注視目標或只是瞥了一眼。
我們建議給定約 150-250 毫秒的啟動時間 (表示使用者關注與尋找大型目標)。  
2. 啟動停駐回饋  ：確定使用者刻意注視目標後，則會開始顯示停駐回饋，來通知使用者停駐啟動已經開始。 
3. 連續回饋  ：當使用者持續看著目標時，顯示持續的進度指示器，讓使用者知道他們必須繼續看著目標。 特別是針對眼部目光輸入，我們建議先從較大的圓圈或球體開始，再逐漸縮小圓圈或球體，以抓住使用者的視覺注意  。 顯示最終狀態的指示器 (小圓圈)，協助與使用者溝通何時將完成停駐完成。 下方有範例圖。 
4. 完成  ：如果使用者繼續關注目標 (再 650-850 毫秒)，便完成停駐啟動並選取注視的目標。

![停駐狀態](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a>另請參閱
* [眼球追蹤](eye-tracking.md)
* [眼部目光和行動](gaze-and-commit-eyes.md)
* [目光和行動](gaze-and-commit.md)
* [目光和停駐](gaze-and-dwell.md)
* [語音輸入](voice-design.md)
