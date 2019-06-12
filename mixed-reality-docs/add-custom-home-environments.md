---
title: 新增自訂的家庭環境
description: 除了我們所提供的 Windows Mixed Reality 家用的環境，您可以實驗建立和使用您自己。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、 混合實境，虛擬實境、 VR、 MR、 首頁、 自訂環境、 位置、 cliff 房子、 skyloft、 使用者，建立
ms.openlocfilehash: 8f5a3a1bdf5728260b0b7717c74a50f3356ca04a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829645"
---
# <a name="add-custom-home-environments"></a>新增自訂的家庭環境

>[!NOTE]
>這是實驗性功能。 不妨試試樂趣，但請不要感到驚訝，如果所有項目未完全如預期運作。 我們計劃要評估的可行性，此功能與感興趣，因此使用它，請告訴我們您的經驗 （和任何您已發現的 bug） 中[開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)。

開頭[Windows 10 April 2018 update](#release-notes-april-2018.md)，啟用了實驗性功能，可讓您將加入 （在 [開始] 功能表中） 的位置選擇器的自訂環境，以做為[Windows Mixed Reality 家用](#navigating-the-windows-mixed-reality-home.md). Windows Mixed Reality 有兩個預設環境，Cliff 房屋和 Skyloft，您可以選擇為您的首頁。 建立自訂的環境，可讓您擴充該清單與您自己的創作。 我們會提供此處於早期評估從建立者和開發人員感興趣，請參閱何種世界您建立，，和了解如何使用不同的撰寫工具的狀態。

時使用的自訂環境，您會發現該 teleporting，互動的應用程式，並將放置全像投影的運作方式就像它會以 Skyloft 與 Cliff 房子。 您可以瀏覽網頁的幻想架構中或未來的縣 （市） 填入全像投影-有無限的可能性 ！

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
    </tr>
     <tr>
        <td>自訂的家庭環境</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>嘗試的範例環境

我們已建立範例環境中，將展示一些自訂的家庭環境的創意的可能性。 請遵循下列步驟來試試看：
1. [下載我們的範例幻想島環境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe)（自動解壓縮可執行檔的連結點為單位）。

    ![幻想島範例環境](images/FantasyLand.jpg)<br>
    *幻想島範例環境*<br>

2. 執行**Fantasy_Island.exe**剛才下載的檔案。

    > [!NOTE]
    > 嘗試執行.exe 檔案 （例如這個） 網站下載，您可能會遇到 「 Windows 受保護您的電腦 」 快顯視窗。 若要從這個快顯視窗中執行 Fantasy_Island.exe，請選取**進一歩**，然後**仍要執行**。 此安全性設定為了保護您免於下載的檔案，您不一定要信任，因此當您信任的來源檔案時請只選擇此選項。

3. 開啟**檔案總管**並瀏覽至 [環境] 資料夾，藉由在 [網址] 列中貼上下列： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`。
4. 將您下載的範例環境複製到這個資料夾中。
5. 重新啟動**混合實境入口網站**。 這會重新整理在位置選擇器中的環境清單。
6. 置於耳機。 一旦您在家中，開啟 **[開始] 功能表**使用 Windows 按鈕您的控制器。
7. 選取 **上的芳鄰**選擇家庭環境的已釘選應用程式清單上方的圖示。
8. 您會發現您在清單中的位置中下載的幻想島環境。 選取 **幻想島**輸入在新的自訂家庭環境 ！

## <a name="creating-your-own-custom-environment"></a>建立您自己的自訂環境

除了使用我們的範例環境，您可以匯出您自己自訂的環境，使用您最愛的 3D 編輯軟體。 

### <a name="modeling-guidelines"></a>模型化的指導方針

當模型化您的環境，請注意下列建議。 這有助於確保以正確的方向 believably 大小的世界中的使用者會產生：

1. 使用者會繁衍 0,0,0 因此中心所需的繁衍您的位置原點為中心。
2. 工作單位應該設定以公尺為單位，以便可以撰寫全球規模的資產。
3. 總軸應該設定為"Y"。
4. 資產應該面臨"forward"朝向正 Z 軸。
5. 所有的網格不需要合併，但建議如果您的目標資源受限的裝置。

### <a name="exporting-your-environment"></a>匯出您的環境

Windows Mixed Reality 依賴二進位 glTF (.glb) 做為資產的傳遞格式的環境。 glTF 是獲微軟授權使用 3D 資產傳遞 Khronos 群組所維護的免費開放標準。 隨著 glTF 發展為一種業界標準的可互通的 3D 內容，因此會 Microsoft 的支援格式會在 Windows 應用程式和體驗。

匯出資產，以用作自訂家庭環境的第一個步驟產生 glTF 2.0 模型。 GlTF 工作群組會維護[份支援匯出工具和轉換器](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)建立 glTF 2.0 模型。 若要開始，使用本頁列出的程式來建立和匯出 glTF 2.0 模型，或轉換現有的模型使用其中一個支援的轉換器。

此外，請參閱[很有幫助本文](https://www.khronos.org/blog/art-pipeline-for-gltf)這提供封面流程概觀匯出 glTF 模型從 「 blender 」 和 3DS Max 直接。 

### <a name="environment-limits"></a>環境的限制

所有的環境必須是 < 256 mb。 大於 256 mb 為單位的環境將無法載入，並改為使用空的世界就預設天空盒周圍的使用者使用。 建立您的模型時，請記住此檔案的大小限制。 此外，如果您打算使用 WindowsMRAssetConverter，如下所述進行環境最佳化，是 cognizant 紋理大小，將會增加，因為最佳化工具會建立紋理，具有較大的檔案大小，但更快載入。 

### <a name="optimizing-your-environment"></a>將您的環境最佳化

Windows Mixed Reality 支援許多選用的最佳化功能，可大幅縮短載入時間，您的環境。 這可能會對大部分的紋理，環境來說尤其重要，因為他們有時會在載入時的逾時時間。 一般情況下，我們建議此步驟中的所有資產，不過，較小的環境，以幾個或低解析度的紋理不一定需要它。 

為了簡化此程序，我們建立了[Windows 混合實境資產轉換子 （可在 GitHub 上）](https://github.com/Microsoft/glTF-Toolkit/releases)來執行您的最佳化。 此工具會執行其他紋理封裝、 壓縮和解決方式向下調整，最佳化任何標準 2.0 glTF 或.glb 使用一組 Microsoft glTF 工具組中可用的公用程式。 

這個轉換子目前支援數目來調整最佳化的確切行為的旗標。 我們建議您執行下列的旗標，為獲得最佳結果：

Flag|建議的值|描述
---|---|---
-max-texture-size|1024 或 2048| 調整此選項可改善紋理的品質，預設值是 512 x 512。 請注意，較大的值會大幅影響環境的檔案大小因此牢記在心 256 mb 的限制
-min-version|1803|舊版 windows 上才支援自訂的環境 > = 1803年。 這個旗標將會移除較舊版本的紋理，並減少檔案大小的最終的資產

例如:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>測試您的環境

您最終.glb 環境之後您即可耳機中測試它。 步驟 2 中開始[「 嘗試的範例環境 」](#trying-a-sample-environment)家用混合實境中作為您的自訂環境的一節。 

## <a name="feedback"></a>意見反應

雖然我們會評估此實驗性功能，我們想要了解您如何使用自訂環境、 任何您可能會遇到，有關的錯誤，且您要的功能的方式。 請分享建立和使用自訂的家庭環境中的所有意見反應[開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)。

## <a name="troubleshooting-and-tips"></a>疑難排解與秘訣

### <a name="how-do-i-change-the-name-of-the-environment"></a>如何變更環境的名稱？

[環境] 資料夾中的檔案名稱將用於在位置選擇器中。 若要變更您的環境名稱只是重新命名環境檔案名稱，並重新混合實境入口網站。

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>如何從我的位置選擇器中移除自訂環境？

若要移除的自訂環境，請開啟 在您的電腦上的 環境 資料夾 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 和刪除環境。 一旦您重新啟動混合實境入口網站，此環境不會再出現在位置選擇器中。 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>如何 default 我最愛的自訂環境？

您目前無法變更預設環境。 每次您重新啟動混合實境入口網站中，您會返回 Cliff 房屋環境。 

### <a name="i-spawn-into-a-blank-space"></a>我繁衍 （spawn) 至空白空間

Windows Mixed Reality[不支援超過 256 mb 的環境](#environment-limits)。 當環境超出此限制時，您將登陸在空白的天空方塊中，不具有模型。

### <a name="it-takes-a-long-time-to-load-my-environment"></a>花費很長的時間，以載入我的環境

您可以新增選用的最佳化您的環境，讓它更快載入。 請參閱[< 最佳化您的環境 >](#optimizing-your-environment)如需詳細資訊。

### <a name="the-scale-of-my-environment-is-incorrect"></a>我的環境的縮放比例不正確

載入環境時，Windows Mixed Reality 將轉譯 glTF 單位，以 1 公尺。 如果您的環境載入非預期的小數位數，再次檢查您的匯出工具，以確保您正在建立模型 1 公尺的縮放比例。 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>在 我的環境中繁衍位置不正確

預設繁衍位置位於 0,0,0 在環境中。 其目前無法自訂這個位置，因此您必須修改繁衍點位於所需的繁衍點的來源匯出您的環境。

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>聲音聽起來不正確的環境中

當您建立您的自訂環境時，它會使用不符合您所建立的實體空間樂器轉譯模擬。 音效可能來自錯誤的指示，並聽 muffled。 

## <a name="see-also"></a>另請參閱
* [瀏覽 Windows 混合實境首頁](#navigating-the-windows-mixed-reality-home.md)
* [混合實境資產轉換子 （於 GitHub) 的 Windows](https://github.com/Microsoft/glTF-Toolkit/releases)

