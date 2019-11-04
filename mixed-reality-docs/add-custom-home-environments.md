---
title: 設計您自己的沉浸式環境
description: 除了我們提供的 Windows Mixed Reality 家庭環境之外，您還可以試驗自己的建立和使用。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality，混合現實，虛擬實境，VR，MR，Home，自訂環境，地點，cliff 房屋，skyloft，使用者，建立
ms.openlocfilehash: e133e1438410540592a51f54ed136aecd04c6244
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437075"
---
# <a name="design-your-own-immersive-environments"></a>設計您自己的沉浸式環境

>[!NOTE]
>這是實驗性的功能。 試試看吧！，如果所有東西都不會如預期般運作，則不會驚訝。 我們正在評估這項功能的可用性，並對其使用感興趣，因此請在[開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)中告訴我們您的經驗（以及您發現的任何錯誤）。

從[windows 10 2018 年4月更新](release-notes-april-2018.md)開始，我們已啟用實驗性功能，可讓您將自訂環境新增至 [位置] 選擇器（在 [開始] 功能表上），以做為[Windows Mixed Reality 首頁](navigating-the-windows-mixed-reality-home.md)。 Windows Mixed Reality 有兩個預設環境： Cliff 房子和 Skyloft，您可以選擇做為首頁。 建立自訂環境可讓您使用自己的建立來擴充該清單。 我們會使這項功能在早期的狀態下提供，以評估建立者和開發人員的興趣、查看您所建立的各種類型，以及瞭解如何使用不同的撰寫工具。

使用自訂環境時，您會注意到 teleporting、與應用程式互動，以及放置全息影像的運作方式，就像在 Cliff 房子和 Skyloft 中一樣。 您可以在幻想的橫向流覽 web，或使用全像幻想式道具的城市填補，這可能是無限的！

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>特徵</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>自訂家庭環境</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>嘗試範例環境

我們建立了一個範例環境，其中顯示一些自訂家庭環境的創意可能性。 請遵循下列步驟來試用：
1. [下載我們的範例幻想島環境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe)（連結點到自我解壓縮的可執行檔）。

    ![的幻想島範例環境](images/FantasyLand.jpg)<br>
    *幻想島範例環境*<br>

2. 執行您剛才下載的**Fantasy_Island .exe**檔案。

    > [!NOTE]
    > 當您嘗試執行從 web 下載的 .exe 檔案時（例如此檔案），您可能會遇到「Windows 受保護的電腦」快顯視窗。 若要從此快顯視窗執行 Fantasy_Island .exe，請選取 [**更多資訊**]，然後 [**仍要執行**]。 此安全性設定的目的是為了保護您無法下載您不想要信任的檔案，因此請只在信任檔案來源時選擇此選項。

3. 開啟 [檔案**瀏覽器**]，然後在網址列中貼上下列內容，以流覽至 [環境] 資料夾： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`。
4. 將您下載的範例環境複製到此資料夾中。
5. 重新開機**混合現實入口網站**。 這會重新整理位置選擇器中的環境清單。
6. 放在您的耳機上。 在首頁之後，使用 [Windows] 按鈕控制器開啟 [**開始] 功能表**。
7. 選取釘選的應用程式清單上方的 [**位置**] 圖示，以選擇家庭環境。
8. 您會在您的地點清單中找到您所下載的「幻想島」環境。 選取 [**幻想島**] 以輸入新的自訂家庭環境！

## <a name="creating-your-own-custom-environment"></a>建立您自己的自訂環境

除了使用我們的範例環境之外，您還可以使用您最愛的3D 編輯軟體，匯出自己的自訂環境。 

### <a name="modeling-guidelines"></a>模型化方針

在模型化您的環境時，請記住下列建議。 這可協助確保使用者在 believably 大小的世界中，以正確的方向產生：

1. 使用者將會產生0，0，0，將您所需的衍生位置置在原點周圍。
2. 工作單位應設定為計量，以便可在世界各地撰寫資產。
3. 向上軸應該設定為 "Y"。
4. 資產應該朝正 Z 軸「順向」。
5. 所有的網格都不需要合併，但如果您的目標是受資源限制的裝置，則建議使用此選項。

### <a name="exporting-your-environment"></a>匯出您的環境

Windows Mixed Reality 依賴二進位 glTF （. glb）作為環境的資產傳遞格式。 glTF 是由 Khronos 群組維護之3D 資產傳遞的免費開放標準。 隨著 glTF 發展成可互通3D 內容的業界標準，Microsoft 也會支援跨 Windows 應用程式和體驗的格式。

匯出資產以作為自訂家庭環境的第一個步驟是產生 glTF 2.0 模型。 GlTF 工作群組會維護一份[支援的匯出工具和轉換器清單](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)，以建立 glTF 2.0 模型。 若要開始，請使用此頁面上所列的其中一個程式來建立和匯出 glTF 2.0 模型，或使用其中一個支援的轉換器來轉換現有的模型。

此外，請參閱[這篇實用的文章](https://www.khronos.org/blog/art-pipeline-for-gltf)，其中提供了直接從 BLENDER 和 3DS Max 匯出 glTF 模型的藝術工作流程總覽。 

### <a name="environment-limits"></a>環境限制

所有環境都必須 < 256 mb。 大於 256 mb 的環境將無法載入並切換回空白的世界，只有使用者周圍的預設 skybox。 建立模型時，請記住此檔案大小限制。 此外，如果您打算使用 WindowsMRAssetConverter 來優化您的環境，如下所述，請 cognizant 紋理大小會隨著優化工具建立具有較大檔案大小的材質而增加，但載入速度更快。 

### <a name="optimizing-your-environment"></a>將您的環境優化

Windows Mixed Reality 支援數個選擇性的優化，可大幅減少您環境的載入時間。 對於具有許多材質的環境而言，這可能特別重要，因為它們有時會在載入時超時。 一般來說，我們建議所有資產使用此步驟，不過，只有少數或低解析度紋理的小型環境不一定會要求它。 

為了簡化此程式，我們已建立[Windows Mixed Reality 資產轉換器（可在 GitHub 上取得）](https://github.com/Microsoft/glTF-Toolkit/releases)來執行您的優化。 這項工具會使用 Microsoft glTF 工具組中提供的一組公用程式，藉由執行額外的材質封裝、壓縮和解析度向下延展來優化任何標準 2.0 glTF 或 glb。 

轉換器目前支援多個旗標，以調整優化的確切行為。 我們建議使用下列旗標來執行，以取得最佳結果：

Flag|建議的值|說明
---|---|---
-最大-材質-大小|1024或2048| 調整此項以改善材質的品質，預設值為512x512。 請注意，較大的值會大幅影響環境的檔案大小，因此請記住 256 mb 的限制
-最小-版本|1803|只有 windows > = 1803 版本才支援自訂環境。 此旗標會移除較舊版本的材質，並減少最終資產的檔案大小

例如：

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>測試您的環境

當您擁有最後的 glb 環境之後，就可以開始在耳機中進行測試。 從「[試用範例環境](#trying-a-sample-environment)」一節的步驟2開始，使用您的自訂環境作為混合現實首頁。 

## <a name="feedback"></a>意見反應

雖然我們正在評估這項實驗性功能，但我們想要瞭解您使用自訂環境的方式、您可能遇到的任何 bug，以及您喜歡這項功能的方式。 請在[開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)中分享建立和使用自訂家庭環境的任何意見反應。

## <a name="troubleshooting-and-tips"></a>疑難排解與秘訣

### <a name="how-do-i-change-the-name-of-the-environment"></a>如何? 變更環境的名稱嗎？

[環境] 資料夾中的檔案名將用於 [位置] 選擇器。 若要變更您的環境名稱，只需重新命名環境檔案名，然後重新開機混合現實入口網站。

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>如何? 從我的地點選擇器中移除自訂環境嗎？

若要移除自訂環境，請在您的電腦上開啟 [環境] 資料夾（`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`），然後刪除環境。 一旦您重新開機混合現實入口網站，這個環境就不會再出現在 [位置] 選擇器中。 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>如何? 預設為我最愛的自訂環境嗎？

您目前無法變更預設環境。 每次您重新開機混合現實入口網站時，將會回到 Cliff 房屋環境。 

### <a name="i-spawn-into-a-blank-space"></a>我會產生一個空格

Windows Mixed Reality[不支援超過 256 mb 的環境](#environment-limits)。 當環境超出此限制時，您會進入空的天空方塊，而不會有任何型號。

### <a name="it-takes-a-long-time-to-load-my-environment"></a>載入我的環境需要很長的時間

您可以在您的環境中新增選擇性的優化，使其更快載入。 如需詳細資訊，請參閱「[優化您的環境](#optimizing-your-environment)」。

### <a name="the-scale-of-my-environment-is-incorrect"></a>我的環境規模不正確

Windows Mixed Reality 會在載入環境時將 glTF 單位轉譯為1計量。 如果您的環境載入非預期的規模，請再次檢查您的匯出工具，以確定您是以1個計量規模進行模型化。 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>我的環境中的衍生位置不正確

預設的產生位置位於環境中的0，0，0。 目前無法自訂此位置，因此您必須藉由將您的環境匯出至所需的衍生點，以修改產生點。

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>在環境中音訊的音效不正確

當您建立自訂環境時，它會使用不符合您所建立之實體空間的聲場呈現模擬。 音效可能來自錯誤的方向，而且可能聽起來 muffled。 

## <a name="see-also"></a>請參閱
* [Windows Mixed Reality 資產轉換器（位於 GitHub）](https://github.com/Microsoft/glTF-Toolkit/releases)

