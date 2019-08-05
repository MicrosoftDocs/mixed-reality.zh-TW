---
title: 適用于 HoloLens 2 的 Galaxy Explorer
description: 歡迎使用我們更新 HoloLens 2 的 Galaxy Explorer 的旅程。 就像原始的「Galaxy Explorer」一樣, 我們的小組也會在 GitHub 上開啟專案, 以確保該社區具有完整的存取權。
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy explorer, 案例研究, 專案, 範例
ms.openlocfilehash: 1e04b27ff0382d87f8e6a15ae2b7b2284fa020e6
ms.sourcegitcommit: be3631932ea1c88ac3ad8b2390c98c5a6e8b93ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2019
ms.locfileid: "68776542"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>適用于 HoloLens 2 的 Galaxy Explorer

歡迎使用我們更新 HoloLens 2 的 Galaxy Explorer 的旅程。 [Galaxy Explorer](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy Explorer")最初是以適用于 HoloLens (第1代) 的開放原始碼應用程式開發, 並透過分享您的創意計畫, 而且是許多人的第一個混合現實經驗。 現在我們要更新它, 以取得[HoloLens 2 的全新且令人興奮的功能](https://www.microsoft.com/hololens/hardware)。

身為[Microsoft Mixed Reality 工作室](galaxy-explorer-update.md#mixed-reality-studios)的其中一個, 我們通常會開發商業級解決方案, 並在整個創意和開發過程中, 開發 & 在目標平臺上進行測試。 我們現在有一種獨特的情況, 也就是還沒有 HoloLens 2 裝置的存取權, 但很高興能夠開始更新至 Galaxy Explorer。 我們會登機在這個專案上使用架構和工具 (例如[MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)), 因為它們可以提供給我們和「社區」, 而我們想要帶您一起進行。

就像原始的「Galaxy Explorer」一樣,[我們的小組](galaxy-explorer-update.md#meet-the-team)也會在[GitHub 上開啟專案](https://github.com/Microsoft/GalaxyExplorer), 以確保該社區具有完整的存取權。 我們也將在這裡記錄我們的旅程, 以完整的透明度說明我們 undertook 從 MRTK v1 移植到 MRTK v2 的方式、如何根據 HoloLens 2 中提供的新功能來增強體驗, 以及如何確保 Galaxy Explorer 保持不變多平臺體驗。 因此無論您是在 HoloLens (第1代)、HoloLens 2、Windows Mixed Reality 耳機或 Windows 10 desktop 上觀看 Galaxy Explorer, 我們都想要確保您擁有豐富的體驗, 並盡可能享用旅程。

此頁面將會隨著我們在專案中的進度擴展, 而我們將會連結至更詳細的文章、程式碼、設計構件、其他 MRTK v2 檔等專案。

## <a name="unveiling-the-new-logo"></a>揭露新標誌

我們很興奮地開始使用新的 Galaxy Explorer 標誌的預覽! 藉由以銀河的方式來以示敬意原始標誌, 我們設計了逼真的視覺效果並更新印刷樣式, 以提供更精緻且現代化的風格。 標誌中包含的是搶先查看其中一個新圖示。

![新的 [Galaxy Explorer] 標誌](images/ge-update-app-icon.png)

標誌的設計和印刷樣式會在整個體驗中, 設定 UI 元素整體外觀與風格的色調。 

## <a name="thinking-about-interactions"></a>考慮互動

身為創意的 studio, 我們 ecstatic 了將 [Galaxy Explorer] 移植至 HoloLens 2 的許可權。 我們從一開始就知道, 我們希望體驗成為新裝置的慶祝, 並示範混合現實的能力僅限於想像。

HoloLens 2 可讓使用者以自然的方式來觸控、抓住和移動全息影像, 它們會回應很多類似實際的物件。 全清楚表達的手模型很驚人, 因為它可讓使用者執行自然的外觀。 例如, 每個人都以不同的方式來挑選杯, 而不是強制執行它, 而是透過 HoloLens 2 來執行。

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

這是第一代 HoloLens 裝置上的以空中操作介面為基礎的重大變更。 使用者現在可以取得「關閉」和「個人」, 而不是與從遠處的全息影像互動。 將現有的經驗移植到 HoloLens 2 或規劃新的體驗時, 請務必熟悉全像投影的直接操作。

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>直接操作與空間中的巨大距離

這是一種神奇的體驗, 可讓您取得地球並將它放在您手中。 這種方法的挑戰是日光系統的大小–非常龐大! 使用者必須四處討論他們的房間, 才能與每個地球進行互動。

為了讓使用者能夠與距離較遠的物件互動, MRTK 提供了從使用者 palm 的中心開始的手片, 做為手的延伸。 環圈形游標會附加到光線的尾端, 以指示光線與目標物件相交的位置。 然後，游標所在的物件就能從手部接收手勢命令。 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

在原始版本的 [Galaxy Explorer] 中, 使用者會以看看游標的全球為目標, 然後再按 [按較近的電話]。 將體驗移植到 HoloLens 2 最簡單的方式, 就是採取此行為, 並使用手片來選取行星。 雖然這是正常運作的功能, 但我們仍想要更多。

### <a name="back-to-the-drawing-board"></a>回到繪圖面板

我們合在一起, ideate 可以在現有互動之上建立的內容。 思考是:雖然 HoloLens 2 可讓使用者以自然、實際的方式與全息影像互動, 但全息的全像是不真正的定義。 因此, 只要使用者合理情況互動, 就不會影響到實際的物件是否能夠進行互動–我們可以做到這一點。

我們探索的一個概念是以 telekinesis 為基礎–這是一項想法來操控物件的能力。 通常會出現在超級主圖電影中, 一位人會想到他們的想法, 並將物件呼叫到他們的手中。 我們有更多的想法, 並提出概念的快速草圖。

![強制抓取互動的概念](images/ge-update-interactions-concept-force-grab.png)

使用者會將手中的光線指向地球, 這會提供目標意見反應。 當使用者接著擴充其開放式手時, 系統會將地球向使用者提取神奇強制, 直到夠近才能抓取。 因此, 我們會進行互動的名稱: force 抓取。 因為使用者會以其手上推播地球, 所以會再次回到其軌道。

### <a name="force-grab-prototyping"></a>強制抓取原型

接著, 我們建立了多個原型來測試概念:互動的整體外觀為何？ 被呼叫的物件是否會在使用者之前停止, 或停留在下的手中？ 呼叫的物件是否應該在呼叫時變更大小或小數值？

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>在應用程式中執行強制抓取

當我們嘗試在行星上進行強制抓取時, 我們發現我們必須變更日光系統的規模。 我們發現日光系統的精確、中型標記法很難以讓使用者瞭解和流覽-它們不知道要查看的位置。 不過, 精確、小型大小的標記法使得某些行星太小, 無法輕易地選取。 因此, 行星的大小和陽曆物件之間的間距, 是設計成在中等大小的房間內感到舒適, 同時維持相對的準確度。

在開發短期衝刺的後續階段中, 我們已經很幸運地有其他的 MSFT 混合現實專家, 所以我們可以將其輸入做為專家測試人員, 並在強制抓取互動上進行快速反復執行。

![Jenny Kam 測試 [Galaxy Explorer] 的預覽組建](images/ge-update-user-testing.png)

在圖片中:Jenny Kam, 資深設計組長, 測試 Galaxy Explorer 的工作進行中。

### <a name="adding-affordances-for-targeting"></a>新增目標的 affordances

當我們在 HoloLens 2 上實驗時, 我們發現即使新的互動是自然且直覺的, 但全息的全像沒有權數或觸覺 sensations。 由於全息影像不會提供自然的意見反應, 讓人類用來接收與物件互動時的情況, 我們需要建立它們。

我們考慮到使用者會針對其互動的各個階段提供的視覺和音訊意見反應, 而且由於強制抓取機制是與 Galaxy Explorer 互動的核心, 我們進行了許多反復專案。 其目標是要為互動的每個階段尋找適當的音訊和視覺效果意見反應: 將焦點放在預期的物件上, 並將其呼叫給使用者, 然後放開它。 我們學到的是, 要比我們用於 HoloLens (第一代) 的互動, 需要更多的音訊和視覺效果回饋。

![行星上的視覺 affordances](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>新增 affordances 以強制抓取
 
一旦有了具有音訊和視覺效果 affordances 的基本強制抓取機制, 我們探討了如何讓使用者更容易選擇使用行星。 有兩個主要的事項要解決:因為日光系統是3D 移動介面, 所以使用者會更複雜地瞭解如何以一致的方式為物件設定目標。 這是因為在選取物件時, 右手光線非常快速, 讓行星更快速地移至使用者。

我們使用三個架構的解決方案來達到這個效益。 第一種是相當直覺的: 使選取程式變慢, 讓行星以更自然的步調來處理使用者。 調整速度之後, 我們必須重新流覽音訊和視覺效果 affordances, 新增其他音訊意見反應, 做為向使用者追蹤的地球。

解決方案的第二個部分是讓整個強制抓取互動的視覺效果非常有形。 我們視覺化了一條粗線, 它會在手邊與目標物件連接之後移動, 然後將該物件帶回給使用者的套索。 

![適用于 force 抓取的視覺效果「套索」 affordances](images/ge-update-lasso-affordances.png)

最後, 我們優化了日光系統的規模, 讓行星的大小夠大, 讓使用者的注視和手上的光線達到目標。 

這三項改良功能可以讓使用者做出精確的選擇, 以直覺的方式對他們呼叫行星。 整體來說, 最終強制抓取的效果是在日光系統中提供更多的沉浸式互動體驗。

## <a name="spotlight-on-jupiter"></a>木星上的焦點

建立銀河方式的日光, 是一項 humbling 的經驗。 特別是, 木星的獨特特性讓它成為耶的可見方式。 這是天然氣巨人的最大和最多色彩, 其包含的品質比所有其他的行星還要大。 其晃動和 cloud dynamics 的龐大大小和 mesmerizing 區 prefect, 可讓您特別注意。

### <a name="geometry-and-meshes"></a>Geometry 和網格

隨著天然氣的外部 shell, 這是由 gaseous 層所組成。 其快速旋轉速度、內部熱度交換和 Coriolis 強制的結合, 可讓您建立色彩豐富的圖層和串流, 以形成 swirling cloud 皮帶和 vortices。 在建立我們的日光系統時, 捕捉這個複雜的美式就是關鍵。

這會立即清楚地說, 使用視覺化的技術 (例如流暢的模擬) 和具有預先計算串流的動畫紋理不會有任何問題。 同時模擬這項功能所需的運算能力, 可能會對效能造成明顯的不利影響。 

![木星物件的總覽](images/ge-update-jupiter-shells-complete.jpg)

下一個方法是「冒煙和鏡像」解決方案, 由覆迭透明材質圖層所組成, 其中每一個都是在旋轉網格的組合上所編譯的面向移動的特定層面。

在下圖中, 您可以看到左側的內部 shell。 此 matt 圖層提供組合的背景, 以預防組成雲端的多層之間的任何小間隙。 由於圖層的緩慢旋轉, 它也會在較快速的移動群組之間做為視覺化緩衝區, 以協助在整個層中建立視覺 unity。

將此錨點設定為模型之後, 移動的雲端層會接著投射在下面所見的中間和右側網格中。

![使用分隔的 shell 的木星物件總覽](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>繪製

現有材質已分成三個部分的材質, 如下所示:第三部裝載 motionless 的雲端層, 其中有間距可提供視差效果, 中間區段包含快速移動的外部資料流, 而第三個則包含緩慢旋轉的內部基底層。

特性良好的紅色點也會分成不同的移動部分, 然後插入材質的另一個不可見區域。 在下圖的中間區段中, 可以將這些元件視為紅色 toned speckles。

因為每個寬線都有特定的方向和速度, 所以紋理會個別套用至每個網格。 然後, 這些網格會有共同的中心和軸點, 以便 concentrically 整個表面的動畫。

![木星材質總覽](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>旋轉和材質行為

現在已設定了木星的視覺效果組合, 因此我們需要確保已適當地計算並套用旋轉和軌道速度。 針對木星完成完整輪替需要大約9小時的時間。 這是因為差異輪替而定義的。 因此, 赤道幾內亞資料流程已設定為「主要資料流程」, 以3600框架進行完整輪替。 其他每一層都必須以旋轉速度做為3600的因素, 才能符合其初始位置, 例如600、900、1200、1800等等。

![木星 shell 紋理](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>絕佳的紅色點

個別旋轉的資料流程提供了良好的視覺效果, 但在接近範圍觀察到的情況下, 會有更詳細的資訊。

最引人注目的部分是木星的絕佳紅色點, 因此我們建立了一組專門用來展示它的網格和紋理。
 
我們使用的機制類似于木星的波段: 一組旋轉的元件會在彼此之上組成, 同時也會在其「主要圖層」下分組, 以確保不論 rest 移動的速度為何, 它們都會保持在位置。

當網格已設定並備妥時, 會套用不同的 stormy vortex 層, 然後每個光碟會個別進行動畫, 而中間的片段則移動速度最快, 而其餘部分則會在移動時逐漸變慢。

![木星絕佳的 Red 點網格](images/ge-update-great-red-spot-mesh.jpg)

組合也具有與每個其他網格相同的樞紐分析表, 同時也會從其原始 y 軸 (!) 中保持其傾斜效果, 以讓您自由地製作旋轉的動畫。 3600框架是基本速率, 每個圖層都有這一段旋轉的因素。

![木星絕佳的紅色點材質](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>直接在 Unity 中取得

在 Unity 中執行此動作時, 有幾個重要的事項要謹記在心。

在處理大型透明層組時, Unity 很容易混淆。 解決的方法是複製每個網格的材質材質, 並將遞增的轉譯佇列值從內部逐漸套用到外部, 每個資料。

結果是內部命令介面的轉譯佇列值為 3000 (預設值), 而靜態 red toned outer 之後的值為 3005, 則快速的白色外部雲端會有3010。 很棒的紅色點 (從內部到外部層的進度) 已在此模型中完成, 值為3025。

![木星最終物件](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>最後的潤色

一開始會先設定多紋理的木星層級, 這證明會不足以進行執行。

原始的全球標準著色器 (及其所有變化) 會透過腳本 (SunLightReceiver) (MRTK 標準著色器不支援) 接收其光源資訊。

單純地交換著色器並不是一種解決方案, 因為地球標準著色器不支援具有透明度的材質對應。 我們已編輯此著色器, 讓 Jupiter 組建能夠如預期執行。

最後, 您必須將來源 Blend 設定為 10, 並將目的地 Blend 設為 5, 以設定 Alpha 混合。

![木星 Unity 屬性](images/ge-update-jupiter-unity-render-queue.jpg)

您可以在 [Galaxy Explorer] 中查看木星的最終呈現!

## <a name="meet-the-team"></a>認識團隊 

我們的 Mixed Reality studio 小組由設計人員、3D 演出者、UX 專家、開發人員、程式經理和 studio head 組成。 我們會從世界各地 hail:比利時、加拿大、德國、以色列、日本、英國和美國。 我們是來自不同背景的豐富團隊: 遊戲-傳統和獨立製作、數位行銷、醫療保健和科學。

我們很興奮地建立了 HoloLens 2 的 Galaxy Explorer, 並更新 HoloLens (第1代)、VR 和桌上出版本。 

![Galaxy Explorer 小組](images/ge-update-team-image.png)

從左上到右:Artemis Tsouflidou (開發人員)、Angie Teickner (視覺化設計工具)、David Janer (UX 設計工具)、劉娜 Garrett (傳遞 & 生產潛在客戶)、Yasushi Zonno (創意潛在客戶)、Eline Ledent (Developer) 和 Ben Turner (Sr-iov)。
左下到右:Amit Rojtblat (技術演出者)、聖馬丁 Wettig (3D 演出者) 和 Dirk Songuer (Studio Head)。
未精選:Tim Gerken (技術組長) 和 Oscar Salandin (視覺化設計工具)。

## <a name="additional-information"></a>其他資訊

### <a name="mixed-reality-studios"></a>混合現實工作室

Microsoft Mixed Reality Studio 團隊 (位於美國、歐洲和亞太地區) 是使用者經驗設計、全像電腦運算、AR/VR 技術和3D 開發的專家;包括3D 資產建立、DirectX、Unity 和 Unreal。 我們會協助想像所需的未來、設計、建立及交付解決方案, 同時讓客戶在其組織中建立可測量的影響。 工作室與超過22000的 Microsoft 服務專業人員密切合作, 以進行企業應用程式整合、採用、作業和支援。
