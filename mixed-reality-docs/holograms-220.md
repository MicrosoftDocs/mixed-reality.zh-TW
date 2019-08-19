---
title: MR 空間 220-空間音效
description: 遵循此編碼逐步解說, 使用 Unity、Visual Studio 和 HoloLens 來瞭解空間音效概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 學院, 教學課程, 空間音效
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526974"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。  因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊, 以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時, 使用這些教學課程的連結進行更新。

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR 空間 220:空間音效

[空間音效](spatial-sound.md)breathes 的生活進入全息的狀態, 並提供給我們世界各地。 全像投影都是由光線和音效所組成, 如果您似乎失去了全息影像, 空間音效可以協助您找到它們。 空間音效與您在廣播上聽到的一般音效不一樣, 它是位於3D 空間中的音效。 有了空間音效, 您就可以讓像是像是您一樣的全像投影, 或甚至是您的頭部! 在此課程中, 您將會:

* 設定您的開發環境以使用 Microsoft 空間音效。
* 使用空間音效來增強互動。
* 將空間音效與空間對應搭配使用。
* 瞭解音效設計和混合最佳作法。
* 使用音效來增強特殊效果, 並將使用者帶入混合現實世界。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 空間 220:空間音效</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

* [已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。
* 一些基本C#的程式設計能力。
* 您應已完成[MR 基本概念 101](holograms-101.md)。
* [為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔案

* 下載專案所需的[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。 此版本可能不再是最新狀態。
  * 如果您仍然需要 Unity 5.5 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。 此版本可能不再是最新狀態。
  * 如果您仍然需要 Unity 5.4 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。 此版本可能不再是最新狀態。
* 將檔案取消封存至您的桌面或其他容易到達的位置。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼, 可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)取得。

### <a name="errata-and-notes"></a>勘誤和注意事項

* 必須在 Visual Studio 下的 [工具]-[> 選項]-[> 的偵錯工具] 中停用 (*取消*核取) [啟用 Just My Code], 才能在程式碼中叫用中斷點。

## <a name="chapter-1---unity-setup"></a>第1章-Unity 設定

### <a name="objectives"></a>目標

* 將 Unity 的音效設定變更為使用 Microsoft 空間音效。
* 將3D 音效新增至 Unity 中的物件。

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 [**開啟**]。
* 流覽至您的桌面, 並尋找您先前取消封存的資料夾。
* 按一下 [ **Starting\Decibel** ] 資料夾, 然後按 [**選取資料夾**] 按鈕。
* 等候專案載入 Unity。
* 在 [ **專案**] 面板中, 開啟**Scenes\Decibel.unity**。
* 在 [階層] 面板中, 展開 [ **HologramCollection** ], 然後選取 [ **P0LY**]。
* 在偵測器中, 展開 [ **spatialize** ], 並注意 [沒有**Spatialize** ] 核取方塊。

根據預設, Unity 不會載入空間定位器外掛程式。 下列步驟將會啟用專案中的空間音效。

* 在 Unity 的頂端功能表中, 移至 **編輯 > 專案設定 > 音訊**。
* 尋找 [**空間定位器外掛程式**] 下拉式清單, 然後選取 [ **MS HRTF 空間定位器**]。
* 在 [階層] 面板中, 選取 [ **HologramCollection > P0LY**]。
* 在 [偵測**器**] 面板中, 尋找 [**音訊來源**] 元件。
* 核取 [ **Spatialize** ] 核取方塊。
* 將**空間 Blend**滑杆拖曳到**3d**, 或在編輯方塊中輸入**1** 。

我們現在會在 Unity 中建立專案, 並在 Visual Studio 中設定方案。

1. 在 Unity 中, 選取 [檔案] **> [組建設定**]。
2. 按一下 [新增] [**開啟場景**] 以加入場景。
3. 在 [**平臺**] 清單中選取**通用 Windows 平臺**, 然後按一下 [**切換平臺**]。
4. 如果您是特別針對 HoloLens 進行開發, 請將**目標裝置**設定為**hololens**。 否則, 請將它保留在**任何裝置**上。
5. 確定 [**組建類型**] 設定為 [ **D3D** ], 並將 [ **sdk** ] 設定為 [**已安裝最新**版本] (應該是 SDK 16299 或更新版本)。
6. 按一下 [建置]。
7. 建立名為 "App" 的**新資料夾**。
8. 按一下 [**應用程式**] 資料夾。
9. 按 [**選取資料夾**]。

當 Unity 完成時, 將會出現 [檔案瀏覽器] 視窗。

1. 開啟**應用程式**資料夾。
2. 開啟 [**分貝] Visual Studio 解決方案**。

如果部署至 HoloLens:

1. 使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**x86**。
2. 按一下 [本機電腦] 按鈕旁的下拉式箭號, 然後選取 [**遠端電腦**]。
3. 輸入**您的 HoloLens 裝置 IP 位址**, 並將驗證模式設定為 **[通用 (未加密的通訊協定)** ]。 按一下 [選取]。 如果您不知道您的裝置 IP 位址, 請查看 [設定] [ **> Network & Internet] > [Advanced Options**]。
4. 在頂端功能表列中, 按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。 如果這是您第一次部署至您的裝置, 您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device---hololens-1st-gen)。

如果部署到沉浸式耳機:

1. 使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**x64**。
2. 請確定 [部署目標] 設定為 [**本機電腦**]。
3. 在頂端功能表列中, 按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。

## <a name="chapter-2---spatial-sound-and-interaction"></a>第2章-空間音效和互動

### <a name="objectives"></a>目標

* 使用音效增強全息影像的真實感。
* 使用音效引導使用者的注視。
* 使用音效提供手勢意見反應。

### <a name="part-1---enhancing-realism"></a>第1部分-增強真實性

#### <a name="key-concepts"></a>重要概念

* Spatialize 的全息影像音效。
* 音效來源應該放在全息影像上的適當位置。

音效的適當位置將取決於全息影像。 例如, 如果全像是人類的全息圖, 則音效來源應該位於嘴附近, 而不是腳。

#### <a name="instructions"></a>指示

下列指示會將 hrtf 音效附加至全息影像。

* 在 [階層] 面板中, 展開 [ **HologramCollection** ], 然後選取 [ **P0LY**]。
* 在 [偵測**器**] 面板的 [ **spatialize**] 中, 按一下 [ **AudioClip** ] 旁邊的圓形, 然後從快顯視窗中選取 [ **PolyHover** ]。
* 按一下 [**輸出**] 旁的圓形, 然後從快顯視窗中選取 [ **SoundEffects** ]。

Project 分貝會使用 Unity **AudioMixer**元件, 為音效群組啟用調整聲音層級。 藉由以這種方式將聲音分組, 可以調整整體磁片區, 同時維持每個音效的相對量。

* 在**spatialize**中, 展開 [ **3d 音效設定**]。
* 將 [ **Doppler 層級**] 設定為**0**。

將 Doppler 層級設定為零會停用移動 (全像是全息或使用者) 所造成的音調變更。 Doppler 的典型範例是快速移動的汽車。 隨著汽車接近固定的接聽程式, 引擎的音調也會上升。 當它通過接聽程式時, 音調就會減少與距離。

### <a name="part-2---directing-the-users-gaze"></a>第2部分-引導使用者的注視

#### <a name="key-concepts"></a>重要概念

* 使用音效來留意重要的全息影像。
* 此耳可協助引導眼睛的外觀。
* 大腦有一些學習的預期。

學習預期的一個範例是, 鳥瞰通常在人類的正上方。 如果使用者聽到鳥瞰聲, 其初始反應就是查閱。 將鳥瞰圖放在使用者下方, 會導致他們以正確的音效方向呈現, 但無法根據預期的查詢來尋找全息。

#### <a name="instructions"></a>指示

下列指示可讓 P0LY 隱藏在您的後方, 讓您可以使用音效來尋找全息的全像投影。

* 在 [階層] 面板中, 選取 [**管理員**]。
* 在 [偵測**器**] 面板中, 尋找 [**語音輸入處理常式**]。
* 在 [**語音輸入處理常式**] 中, 展開 [**移至隱藏**]。
* 將**No Function**變更為**PolyActions. GoHide**。

![關鍵字移至隱藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>第3部分-手勢意見反應

#### <a name="key-concepts"></a>重要概念

* 為使用者提供使用音效的正面手勢確認
* 不要讓使用者過於塞滿的音效
* 微妙音效的效果最佳-不要失色經驗

#### <a name="instructions"></a>指示

* 在 [階層] 面板中, 展開 [ **HologramCollection**]。
* 展開 [ **EnergyHub** ], 然後選取 [**基底**]。
* 在 [偵測**器**] 面板中, 按一下 [**加入元件**], 然後加入**手勢音效處理常式**。
* 在 [**手勢音效處理常式**] 中, 按一下 [**導覽已啟動的剪輯**] 和 [**導覽已更新剪輯**] 旁的圓形, 然後從這兩者的快顯視窗選取 [ **RotateClick** ]。
* 按兩下 [GestureSoundHandler] 以載入 Visual Studio。

手勢音效處理常式會執行下列工作:

* 建立和設定**spatialize**。
* 將**spatialize**放在適當**GameObject**的位置。
* 播放與手勢相關聯的**AudioClip** 。

#### <a name="build-and-deploy"></a>組建和部署

1. 在 Unity 中, 選取 [檔案] **> [組建設定**]。
2. 按一下 [建置]。
3. 按一下 [**應用程式**] 資料夾。
4. 按 [**選取資料夾**]。

檢查工具列是否顯示 [發行]、[x86] 或 [x64], 以及 [遠端裝置]。 如果不是, 這就是 Visual Studio 的程式碼實例。 您可能需要從應用程式資料夾重新開啟解決方案。

* 如果出現提示, 請重載專案檔案。
* 同樣地, 從 Visual Studio 部署。

部署應用程式之後:

* 觀察當您在 P0LY 四處移動時, 音效如何改變。
* 說「 *Go Hide* 」, 讓 P0LY 移到您背後的位置。 依音效尋找。
* 看著能源中樞的基礎。 請按住滑鼠左鍵並向左或向右拖曳以旋轉全像投影, 並注意按一下音效如何確認手勢。

注意:有一個文字面板會與您一起標記。 這會包含可供您在本課程中使用的語音命令。

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>第3章-空間音效和空間對應

### <a name="objectives"></a>目標

* 使用音效確認全息影像與真實世界之間的互動。
* 使用實體世界遮蔽音效。

### <a name="part-1---physical-world-interaction"></a>第1部分-實體世界互動

#### <a name="key-concepts"></a>重要概念

* 當遇到表面或另一個物件時, 實體物件通常會發出音效。
* 音效在體驗中應該是適當的內容。

例如, 在資料表上設定杯時, 應該會比在金屬片上卸載科羅拉多, 讓音效更為安靜。

#### <a name="instructions"></a>指示

* 在 [階層] 面板中, 展開 [ **HologramCollection**]。
* 展開 [ **EnergyHub**], 選取 [**基底**]。
* 在 [偵測**器**] 面板中, 按一下 [**新增元件**], 然後新增 **[使用音效和動作來放置**]。
* **使用音效和動作來放置**:
  * 勾選 **[將父系放在點上**]。
  * 將**放置音效**設定為 [**放置**]。
  * 將**Pickup 音效**設定為**取貨**。
  * **在 [取貨動作**] 和 [**放置] 動作上**, 按右下方的 [+]。 將 [EnergyHub] 從場景拖曳至 [**無] (物件)** 欄位。
    * 在 [**收取取貨動作**] 下, 按一下 [ **No Function**  ->  **EnergyHubBase**  ->  **ResetAnimation**]。
    * 在 [**放置動作**] 底下,  -> 按一下 [無函式**EnergyHubBase**  ->  **OnSelect**]。

![利用音效和動作來放置](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>第2部分-音效遮蔽

#### <a name="key-concepts"></a>重要概念

* 音效 (如 light) 可以 pixels occluded。

典型的範例是音樂會廳。 當接聽程式離開大廳外, 而門已關閉時, 音樂會 muffled。 一般來說, 磁片區也會減少。 當門開啟時, 會在實際音量聽到音效的完整範圍。 高頻率的音效通常會吸收超過低頻率。

#### <a name="instructions"></a>指示

* 在 [階層] 面板中, 展開 [ **HologramCollection** ], 然後選取 [ **P0LY**]。
* 在 [偵測**器**] 面板中, 按一下 [**新增元件**] 並新增**音訊發射器**。

音訊發射器類別提供下列功能:

* 還原**spatialize**磁片區的任何變更。
* 以附加**AudioEmitter**的**GameObject**方向, 從使用者的位置執行**RaycastNonAlloc** 。

RaycastNonAlloc 方法是用來做為效能優化, 以限制配置以及傳回的結果數目。

* 針對每個遇到的**IAudioInfluencer** , 會呼叫**ApplyEffect**方法。
* 對於不再遇到的每個先前**IAudioInfluencer** , 請呼叫**RemoveEffect**方法。

請注意, AudioEmitter 會更新人力時間規模, 而不是每個畫面格。 這樣做的原因是, 人們通常無法快速地進行更新, 而需要比每個季或半秒的頻率更高。 從一個位置快速傳送到另一個位置的全息影像, 可能會破壞夢想。

* 在 [階層] 面板中, 展開 [ **HologramCollection**]。
* 展開 [ **EnergyHub** ], 然後選取 [ **BlobOutside**]。
* 在 [偵測**器**] 面板中, 按一下 [**新增元件**] 並新增**音訊 Occluder**。
* 在 [**音訊 Occluder**] 中, 將 [**截止頻率**] 設定為**1500**。

此設定會將 Spatialize 頻率限制為 1500 Hz 和以下。

* 將**磁片區傳遞**至**0.9**。

此設定會將 Spatialize 的數量減少到其目前層級的 90%。

音訊 Occluder 會將 IAudioInfluencer 實作為:

* 使用附加至**spatialize**受控購買**AudioEmitter**的**AudioLowPassFilter**來套用遮蔽效果。
* 將磁片區衰減套用至 Spatialize。
* 藉由設定中性的截止頻率並停用篩選來停用效果。

用為中性的頻率是 22 kHz (22000 Hz)。 選擇此頻率的原因, 是因為它高於人耳可聽到的名義最大頻率, 所以不會對音效造成明顯影響。

* 在 [階層] 面板中, 選取 [ **SpatialMapping**]。
* 在 [偵測**器**] 面板中, 按一下 [**新增元件**] 並新增**音訊 Occluder**。
* 在 [**音訊 Occluder**] 中, 將 [**截止頻率**] 設定為**750**。

當使用者和**AudioEmitter**之間的路徑中有多個阻隔器時, 會將最低頻率套用至篩選準則。

* 將**磁片區傳遞**至**0.75**。

當使用者和**AudioEmitter**之間的路徑中有多個阻隔器時, 就會套用 additively 的磁片區。

* 在 [階層] 面板中, 選取 [**管理員**]。
* 在 [偵測**器**] 面板中, 展開 [**語音輸入處理常式**]。
* 在 [**語音輸入處理常式**] 中, 展開 [**繼續收費**]。
* 將**No Function**變更為**PolyActions. GoCharge**。

![關鍵字繼續收費](images/gocharge.png)

* 依序展開 [前往**這裡**]。
* 將**No Function**變更為**PolyActions. 撰寫復活**。

![關鍵字過來這裡](images/comehere.png)

#### <a name="build-and-deploy"></a>組建和部署

* 如先前一樣, 在 Unity 中建立專案, 並在 Visual Studio 中部署。

部署應用程式之後:

* 說「*繼續收費*」, 讓 P0LY 進入能源中樞。

請注意音效中的變更。 它應該聽起來 muffled, 而且有點安靜。 如果您可以在您和能源中樞之間定位自己的牆或其他物件, 您應該會注意到因為真實世界遮蔽, 而 muffling 的音效。

* 說「*在這裡*」, 讓 P0LY 離開能源中樞, 並將其本身放在您的前方。

請注意, P0LY 結束能源中樞後, 就會移除音效遮蔽。 如果您仍然聽到遮蔽, P0LY 可能會受到真實世界的 pixels occluded。 請嘗試移動以確保您有清楚的 P0LY。

### <a name="part-3---room-models"></a>第3部分-會議室模型

#### <a name="key-concepts"></a>重要概念

* 空間的大小會提供 subliminal 的佇列, 以做出音效當地語系化。
* 會議室模型是依**spatialize**設定。
* [MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供設定房間模型的程式碼。
* 針對混合現實體驗, 請選取最適合真實世界空間的房間模型。

如果您要建立虛擬實境案例, 請選取最適合虛擬環境的房間模型。

## <a name="chapter-4---sound-design"></a>第4章-音效設計

### <a name="objectives"></a>目標

* 瞭解有效音效設計的考慮。
* 瞭解混合技術和指導方針。

### <a name="part-1---sound-and-experience-design"></a>第1部分-音效和體驗設計

本節討論主要音效和體驗設計考慮和指導方針。

#### <a name="normalize-all-sounds"></a>標準化所有聲音

如此一來, 就不需要特殊的案常式序代碼來調整每個音效的音量層級, 這可能相當耗時, 而且會限制輕鬆更新音效檔的能力。

#### <a name="design-for-an-untethered-experience"></a>非網路共用體驗的設計

HoloLens 是完全獨立的非網路共用全像攝影電腦。 您的使用者可以和將會在移動時使用您的體驗。 請務必四處流覽來測試您的音訊混合。

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>從您的全息影像上的邏輯位置發出音效

在真實世界中, 狗不會從結尾處吠, 而且人類的語音也不會來自其腳。 避免在您的全息影像未預期的部分發出聲音。

對於小型的全息影像, 從幾何中心開始音效是合理的。

#### <a name="familiar-sounds-are-most-localizable"></a>熟悉的音效是最能當地語系化的

人類語音和音樂很容易當地語系化。 如果有人撥打您的名字, 您就能夠非常準確地判斷語音的方向和距離。 簡言之, 不熟悉的音效很難當地語系化。

#### <a name="be-cognizant-of-user-expectations"></a>使用者期望的 cognizant

生命體驗在我們識別音效位置的功能中扮演了部分。 這就是為什麼人類語音特別容易當地語系化的原因之一。 請務必留意您的使用者在放置音效時所學到的預期。

比方說, 當有人聽到一則一般會查詢的「鳥」歌曲時, 因為鳥傾向于觀察線上 (飛行或在樹狀結構中)。 使用者不常以正確的音效方向開啟, 而是在找不到任何一種垂直方向, 並在無法找到全息的情況下感到困惑或挫折。

#### <a name="avoid-hidden-emitters"></a>避免隱藏的發射器

在真實世界中, 如果聽到音效, 我們通常可以識別發出音效的物件。 這也應該在您的經驗中成立。 這可能非常令人不安, 讓使用者聽到音效, 知道聲音源自何處, 而無法看到物件。

此指導方針有一些例外狀況。 例如, 欄位中的環境音效 (例如 crickets) 不需要是可見的。 生活經驗讓我們熟悉這些音效的來源, 而不需要看到它。

### <a name="part-2---sound-mixing"></a>第2部分-音效混合

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>將您的混合目標設為 HoloLens 上的 70% 磁片區

混合現實體驗允許在真實世界中看到全息影像。 他們也應該能夠聽到真實世界的聲音。 70% 的磁片區目標可讓使用者在世界各地聆聽他們, 並附上您的體驗。

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>100% 磁片區上的 HoloLens 應下拉式清單外部聲音

磁片區層級 100% 類似于虛擬實境體驗。 使用者會以視覺化方式傳輸到不同的世界。 同樣的情況也應該保留 true 語音。

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>使用 Unity AudioMixer 來調整音效的類別

設計混合時, 建立音效類別並能夠以一個單位來增加或減少其音量, 通常會很有説明。 這會保留每個音效的相對層級, 同時讓整體混合的快速且輕鬆地進行變更。 常見的類別包括:聲音效果、環境、語音轉移和背景音樂。

#### <a name="mix-sounds-based-on-the-users-gaze"></a>根據使用者的注視來混合聲音

根據使用者的所在位置 (或不是) 來變更您的體驗, 通常會很有用。 這項技術的其中一個常見用途是減少全像攝影畫面外的全息影像音量, 讓使用者更容易專注于他們前面的資訊。 另一種用途是增加音效的音量, 將使用者的注意力吸引到重要的事件。

#### <a name="building-your-mix"></a>打造您的混合

建立混合時, 建議您從體驗的背景音訊開始, 並根據重要性新增圖層。 通常, 這會導致每個圖層都比先前的還要大。

將您的混合想像為反向漏斗圖, 其底部最重要的 (通常是 quietest 音效), 建議您將混合結構與下圖類似。

![音效混合結構](images/soundlevels.png)

語音轉移是一種有趣的案例。 根據您所建立的經驗, 您可能會想要有身歷聲 (非當地語系化) 音效或 spatialize 語音轉移。 兩個 Microsoft 發佈的體驗說明每個案例的絕佳範例。

[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)使用身歷聲聲音。 當朗讀程式描述要查看的位置時, 音效會一致, 而且不會因使用者的位置而有所不同。 這可讓 [朗讀程式] 描述場景, 而不需要離開環境的 hrtf 音效。

[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)會以偵探的形式利用 hrtf 的聲音。 此偵探的語音是用來協助讓使用者注意到重要的線索, 就好像實際的人在聊天室一樣。 這可讓您更瞭解深度解決神秘的經驗。

### <a name="part-3--performance"></a>第3部分-效能

#### <a name="cpu-usage"></a>CPU 使用量

使用空間音效時, 10-12 發射器會耗用大約 12% 的 CPU。

#### <a name="stream-long-audio-files"></a>串流長音訊檔案

音訊資料可能很大, 尤其是常見的取樣率 (44.1 和 48 kHz)。 一般的規則是, 應串流處理長度超過 5-10 秒的音訊檔案, 以減少應用程式記憶體使用量。

在 Unity 中, 您可以在檔案的匯入設定中, 標示要串流處理的音訊檔案。

![音訊匯入設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>第5章-特殊效果

### <a name="objectives"></a>目標

* 將深度新增至「魔術視窗」。
* 將使用者帶到虛擬世界。

### <a name="magic-windows"></a>魔術視窗

#### <a name="key-concepts"></a>重要概念

* 在隱藏的世界中建立視圖, 視覺上具吸引力。
* 當全息影像或使用者接近隱藏世界時, 新增音訊效果, 以增強真實性。

#### <a name="instructions"></a>指示

* 在 [階層] 面板中, 展開 [ **HologramCollection** ], 然後選取 [ **Underworld**]。
* 展開 [ **Underworld** ], 然後選取 [ **VoiceSource**]。
* 在 [偵測**器**] 面板中, 按一下 [**新增元件**] 並新增 [**使用者聲音效果**]。

**Spatialize**元件將會新增至**VoiceSource**。

* 在**spatialize**中, 將 [**輸出**] 設定為 **[UserVoice (混音器)** ]。
* 核取 [ **Spatialize** ] 核取方塊。
* 將**空間 Blend**滑杆拖曳到**3d**, 或在編輯方塊中輸入**1** 。
* 展開 [ **3D 音效設定**]。
* 將 [ **Doppler 層級**] 設定為**0**。
* 在 [**使用者聲音效果**] 中, 將**父物件**從場景設定為**Underworld** 。
* 將 [**最大距離**] 設定為**1**。

設定 [**最大距離**] 可讓使用者在啟用效果之前, 先關閉使用者必須前往父物件的**聲音效果**。

* 在 [**使用者語音效果**] 中, 展開 [**一首哀歌參數**]。
* 將**深度**設定為**0.1**。
* 設定**一下1個磁片**區, 再按2個**音量**, 然後將**3 個磁片**區帶到**0.8**。
* 將 [**原始音效磁片**區] 設定為**0.5**。

先前的設定會設定 Unity **AudioChorusFilter**的參數, 用來將豐富的語音新增至使用者的聲音。

* 在 [**使用者語音效果**] 中, 展開 [ **Echo 參數**]。
* 將**延遲**設定為**300**
* 將 [**衰減比例**] 設定為**0.2**。
* 將 [**原始音效音量**] 設定為**0**。

先前的設定會設定用來讓使用者的語音回應的 Unity **AudioEchoFilter**參數。

使用者聲音效果腳本會負責:

* 測量使用者與附加腳本的**GameObject**之間的距離。
* 判斷使用者是否面臨**GameObject**。

無論距離為何, 使用者都必須面對 GameObject, 才會啟用效果。

* 對**spatialize**套用和設定**AudioChorusFilter**和**AudioEchoFilter** 。
* 停用篩選來停用效果。

使用者語音效果使用 Mic 串流選取器元件 (來自[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)) 來選取高品質的語音串流, 並將其路由傳送到 Unity 的音訊系統。

* 在 [階層] 面板中, 選取 [**管理員**]。
* 在 [偵測**器**] 面板中, 展開 [**語音輸入處理常式**]。
* 在 [**語音輸入處理常式**] 中, 展開 [**顯示 Underworld**]。
* 將**No Function**變更為**UnderworldBase. OnEnable**。

![關鍵字顯示 Underworld](images/showunderworld.png)

* 展開 [**隱藏 Underworld**]。
* 將**No Function**變更為**UnderworldBase. OnDisable**。

![關鍵字隱藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>組建和部署

* 如先前一樣, 在 Unity 中建立專案, 並在 Visual Studio 中部署。

部署應用程式之後:

* 臉部表面 (牆、樓層、桌子), 並說出「 *Show Underworld*」。

將會顯示 underworld, 並隱藏所有其他的全息影像。 如果您看不到 underworld, 請確定您面臨的是真實世界的表面。

* 一種 underworld 的全像投影, 並開始談。

音訊效果現已套用至您的語音!

* 關閉 underworld, 並留意效果不再套用的方式。
* 說「*隱藏 Underworld* 」以隱藏 Underworld。

Underworld 將會隱藏, 而先前隱藏的全息影像將會重新出現。

## <a name="the-end"></a>結束

恭喜您！ 您現在已完成**MR 空間 220:空間音效**。

收聽世界, 讓您的經驗實現音效!
