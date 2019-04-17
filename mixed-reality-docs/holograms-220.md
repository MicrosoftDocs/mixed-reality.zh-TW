---
title: MR 空間 220-空間的音效
description: 請遵循此程式碼撰寫的逐步解說，若要了解空間音效概念的詳細資料，使用 Unity、 Visual Studio 和 HoloLens。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit、 mixedrealitytoolkit unity、 academy、 教學課程中，空間的音效
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591421"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR 空間 220:空間音效

[空間音效](spatial-sound.md)活著到全像投影的生命週期，並提供我們的世界中的目前狀態。 全像投影組成光線和音效，萬一您無法看見您全像投影，空間音效可協助您找出它們。 空間音效不類似的典型的音效，您會聽到電台上，並放置在 3D 空間中的音效。 使用空間的音效，您可以進行全像投影音效起來像是背後旁，或甚至在您 ！ 在本課程中，您將：

* 設定您的開發環境，以使用 Microsoft 空間音效。
* 使用空間的音效增強互動。
* 搭配空間對應中使用空間的音效。
* 了解完善的設計，以及混用最佳作法。
* 您可以使用音效來增強特殊效果，並將使用者引導至混合實境世界。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 空間 220:空間音效</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>先決條件

* Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。
* 基本C#程式設計的能力。
* 您應已完成[MR 基本概念 101](holograms-101.md)。
* HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>專案檔

* 下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)專案所需。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。 這一版可能不再是最新狀態。
  * 如果您仍然需要 Unity 5.5 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。 這一版可能不再是最新狀態。
  * 如果您仍然需要 Unity 5.4 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。 這一版可能不再是最新狀態。
* 取消封存您的桌面或其他您輕鬆地連線到位置的檔案。

>[!NOTE]
>如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)。

### <a name="errata-and-notes"></a>偵錯 errata 和附註

* 若要停用 啟用 Just My Code 的需求 (*未核取*) 在 Visual Studio 的 工具-> 選項-> 偵錯以程式碼中設定中斷點。

## <a name="chapter-1---unity-setup"></a>第 1 章-Unity 安裝

### <a name="objectives"></a>目標

* Unity 的音效將組態變更為使用 Microsoft 空間音效。
* 在 Unity 中的物件加入 3D 的聲音。

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 **開啟**。
* 瀏覽至您的桌面及尋找資料夾您先前未封存。
* 按一下 [ **Starting\Decibel**資料夾，然後按下**選取資料夾**] 按鈕。
* 等待在 Unity 中載入專案。
* 在 [ **專案**] 面板中，開啟**Scenes\Decibel.unity**。
* 在 [**階層**] 面板中，展開**HologramCollection** ，然後選取**P0LY**。
* 在偵測器中，依序展開**AudioSource** ，請注意，沒有任何**Spatialize**核取方塊。

根據預設，Unity 不會載入空間外掛程式。 下列步驟會在專案中啟用空間音效。

* 在 Unity 的上方功能表中，移至**編輯 > 專案設定 > 音訊**。
* 尋找**空間外掛程式**下拉式清單中，然後選取**MS HRTF 空間**。
* 在 **階層**面板中，選取**HologramCollection > P0LY**。
* 在 [ **Inspector** ] 面板中，尋找**音訊來源**元件。
* 請檢查**Spatialize**核取方塊。
* 拖曳**空間 Blend**滑桿，一直到**3D**，或輸入**1**編輯方塊中。

現在，我們將建置 unity 專案，並設定 Visual Studio 中的解決方案。

1. 在 Unity 中，選取**檔案 > 組建設定**。
2. 按一下 **加入開啟的場景**加入場景。
3. 選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。
4. 如果您要特別開發的 HoloLens，設定**目標裝置**要**HoloLens**。 否則，將它保留在**任何裝置**。
5. 確保**建置型別**設為**D3D**並**SDK**設定為**最新安裝**（這應該可以 16299 或更新版本的 SDK）。
6. 按一下 [建置] 。
7. 建立**新的資料夾**名為 「 應用程式 」。
8. 只要按一下**應用程式**資料夾。
9. 按下**選取資料夾**。

Unity 完成時，會出現檔案總管 視窗。

1. 開啟**應用程式**資料夾。
2. 開啟**Decibel Visual Studio 方案**。

如果將部署到 HoloLens:

1. 使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x86**。
2. 按一下下拉式清單 [本機電腦] 按鈕旁邊的箭號，然後選取**遠端機器**。
3. 請輸入**HoloLens 裝置的 IP 位址**並將驗證模式設定為**通用 （未加密的通訊協定）**。 按一下 **選取**。 如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**。
4. 在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。 如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device---hololens-1st-gen)。

如果將部署到擬真耳機：

1. 使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x64**。
2. 請確定部署目標設定為**本機電腦**。
3. 在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。

## <a name="chapter-2---spatial-sound-and-interaction"></a>第 2 章-空間音效和互動

### <a name="objectives"></a>目標

* 加強使用音效的全像真實性。
* 將使用者的視線使用音效。
* 提供使用音效的筆勢意見反應。

### <a name="part-1---enhancing-realism"></a>第 1 部分-增強的真實性

#### <a name="key-concepts"></a>重要概念

* Spatialize 全像音效。
* 音效來源應該放在全像圖上的適當位置中。

音效的適當位置會取決於全像圖。 比方說，如果全像人類，音效來源應該靠近嘴巴無法英呎。

#### <a name="instructions"></a>指示

下列指示會附加至全像圖的 spatialized 的音效。

* 在 [**階層**] 面板中，展開**HologramCollection** ，然後選取**P0LY**。
* 在 [ **Inspector** ] 面板的**AudioSource**旁, 按一下圓形**AudioClip** ，然後選取**PolyHover**從快顯視窗中。
* 按一下旁邊的圓形**輸出**，然後選取**SoundEffects**從快顯視窗中。

專案 Decibel 使用 Unity **AudioMixer**啟用調整音效的音量的群組層級的元件。 受到群組音效如此一來，整體的磁碟區可以進行調整，同時維持每個音效的相對音量。

* 在  **AudioSource**，展開**3D 音效設定**。
* 設定**Doppler 層級**要**0**。

Doppler 層級設定為零會停用中的變更 （無論是全像 」 或 「 使用者） 的動作所造成的字幅。 Doppler 的典型範例是瞬息萬變的汽車。 車輛接近 「 定態的接聽程式時，引擎的字幅上升。 當它通過接聽程式時，字幅降低距離。

### <a name="part-2---directing-the-users-gaze"></a>第 2 部分-導向使用者的視線

#### <a name="key-concepts"></a>重要概念

* 您可以使用音效來醒目提示重要全像投影。
* 어 有助於引導外觀的眼睛。
* 大腦有某些所學習到的期望。

所學習到預期的其中一個範例是鳥通常會讓人判讀的讀寫頭上方。 如果使用者聽到 bird 音效，其反應是查閱。 放置 bird 以下使用者可能會導致它們對向的聲音，但其無法找到根據期望的需要來查閱全像正確的方向。

#### <a name="instructions"></a>指示

下列指示啟用 P0LY 背後，隱藏，以便您可以使用音效來找出全像圖。

* 在 **階層**面板中，選取**管理員**。
* 在 [ **Inspector** ] 面板中，尋找**語音輸入處理常式**。
* 在 **語音輸入處理常式**，展開**移隱藏**。
* 變更**沒有任何函式**要**PolyActions.GoHide**。

![關鍵字：移隱藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>第 3 部分-筆勢的意見反應

#### <a name="key-concepts"></a>重要概念

* 對使用者提供正面的筆勢確認使用音效
* 不會拖垮使用者-太大聲音效 get 的方式
* 細微的音效適合-不會 overshadow 體驗

#### <a name="instructions"></a>指示

* 在 [**階層**] 面板中，展開**HologramCollection**。
* 依序展開**EnergyHub** ，然後選取**基底**。
* 在**Inspector**  面板中，按一下**新增元件**，並新增**軌跡音效處理常式**。
* 中**軌跡音效處理常式**旁, 按一下圓形**瀏覽啟動剪輯**並**導覽更新剪輯**，然後選取**RotateClick**從快顯視窗中兩個。
* 按兩下 「 GestureSoundHandler"在 Visual Studio 中載入。

筆勢音效處理常式會執行下列工作：

* 建立和設定**AudioSource**。
* 地方**AudioSource**的適當位置**GameObject**。
* 在扮演**AudioClip**與筆勢相關聯。

#### <a name="build-and-deploy"></a>建置和部署

1. 在 Unity 中，選取**檔案 > 組建設定**。
2. 按一下 [建置] 。
3. 只要按一下**應用程式**資料夾。
4. 按下**選取資料夾**。

請檢查工具列顯示"Release"、"x86"或"x64"，以及 「 遠端裝置 」。 如果沒有，這是 Visual Studio 的程式碼的執行個體。 您可能需要重新開啟方案，從應用程式資料夾。

* 如果出現提示，請重新載入專案檔。
* 同樣地，從 Visual Studio 部署。

應用程式部署後：

* 觀察當您移動 P0LY 音效要如何變更。
* 假設 *「 移隱藏 」* 讓 P0LY 移到您背後的位置。 發現的音效。
* 注視的能源中樞基底。 點選並拖曳左或向右旋轉全像圖，並請注意如何滑鼠的聲音確認筆勢。

注意：沒有文字面板，可將與您的 tag-along。 這會包含在本課程中，您可以使用可用的語音命令。

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>第 3 章-空間音效和空間的對應

### <a name="objectives"></a>目標

* 確認全像投影與真實世界使用音效之間的互動。
* Occlude 使用真實世界的音效。

### <a name="part-1---physical-world-interaction"></a>第 1 部分-真實世界互動

#### <a name="key-concepts"></a>重要概念

* 實體物件通常發出聲音時遇到一個介面，或另一個物件。
* 聽起來應該是適當的體驗中的內容。

比方說，在資料表上設定一杯要比卸除在一段 metal boulder 安靜音效。

#### <a name="instructions"></a>指示

* 在 [**階層**] 面板中，展開**HologramCollection**。
* 依序展開**EnergyHub**，選取**基底**。
* 在**Inspector**  面板中，按一下**新增元件**，並新增**點選來進行與聲音和動作**。
* 在 **點選以使用音效和動作的地方**:
  * 請檢查**父置於點選**。
  * 設定**放置音效**要**地方**。
  * 設定**Pickup 音效**要**Pickup**。
  * 按下 + 兩者都在底部**Pickup 動作上**並**上放置動作**。 從到場景拖曳 EnergyHub**無 （物件）** 欄位。
    * 底下**Pickup 動作上**，按一下**No 函式** -> **EnergyHubBase** -> **ResetAnimation**。
    * 底下**上放置動作**，按一下**No 函式** -> **EnergyHubBase** -> **OnSelect**。

![點選以使用音效和動作的位置](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>第 2 部分-音效的阻擋物

#### <a name="key-concepts"></a>重要概念

* 如同光線，可以阻擋。

典型的例子是 concert hall。 當接聽程式釐 hall 和門以外的單位已關閉，muffled 音樂音效。 另外還有通常縮小磁碟區。 機門開啟時，完整廣泛的聲音會聽到在實際的磁碟區。 高頻率音效通常是多個低頻率吸收。

#### <a name="instructions"></a>指示

* 在 [**階層**] 面板中，展開**HologramCollection** ，然後選取**P0LY**。
* 在  **Inspector**  面板中，按一下 **新增元件**並新增**音訊 fixit 發出器**。

音訊 fixit 發出器類別會提供下列功能：

* 將任何變更還原的磁碟區**AudioSource**。
* 會執行**Physics.RaycastNonAlloc**從使用者的位置中的方向**GameObject**要**AudioEmitter**附加。

RaycastNonAlloc 方法當做效能最佳化來配置，以及傳回的結果數目限制。

* 每個**IAudioInfluencer**遇到，呼叫**ApplyEffect**方法。
* 每個先前**IAudioInfluencer**也就是不會再發生，呼叫**RemoveEffect**方法。

請注意，AudioEmitter 上更新人性化的時間間隔，而不是以每個畫面格為基礎。 這是因為人們通常不會移動速度夠快的要需要更新頻率高於每季或半秒的效果。 全像投影快速從一個位置，傳送到另一個可能會中斷的假象。

* 在 [**階層**] 面板中，展開**HologramCollection**。
* 依序展開**EnergyHub** ，然後選取**BlobOutside**。
* 在  **Inspector**  面板中，按一下 **新增元件**並新增**音訊 Occluder**。
* 在 **音訊 Occluder**，將**截止頻率**來**1500年**。

此設定會限制 AudioSource 頻率 1500 Hz 和以下版本。

* 設定**磁碟區通過**要**0.9**。

此設定可減少的 AudioSource 為它的目前層級 90%。

音訊 Occluder 實作 IAudioInfluencer 來：

* 阻擋效果使用套用**AudioLowPassFilter**這會附加到**AudioSource**受管理的購買**AudioEmitter**。
* 適用於 AudioSource 磁碟區衰減。
* 藉由設定中性的截止頻率，並停用篩選器，停用生效。

做為中性的頻率是 22 kHz (22000 Hz)。 因為它正在上面可以聽到的人耳，這對不會明顯影響聲音的名義上的最大頻率會選擇此頻率。

* 在 **階層**面板中，選取**SpatialMapping**。
* 在  **Inspector**  面板中，按一下 **新增元件**並新增**音訊 Occluder**。
* 在 **音訊 Occluder**，將**截止頻率**來**750**。

當多個 occluders 位於使用者之間的路徑，而**AudioEmitter**，最低的頻率會套用至篩選條件。

* 設定**磁碟區通過**要**0.75**。

當多個 occluders 位於使用者之間的路徑， **AudioEmitter**，磁碟區通過火套用。

* 在 **階層**面板中，選取**管理員**。
* 在 [ **Inspector** ] 面板中，展開**語音輸入處理常式**。
* 在 **語音輸入處理常式**，展開**移費用**。
* 變更**沒有任何函式**要**PolyActions.GoCharge**。

![關鍵字：移費用](images/gocharge.png)

* 依序展開**這裡**。
* 變更**沒有任何函式**要**PolyActions.ComeBack**。

![關鍵字：到這裡](images/comehere.png)

#### <a name="build-and-deploy"></a>建置和部署

* 同樣地，建置 Unity 專案，並在 Visual Studio 中部署。

應用程式部署後：

* 假設 *「 移費用"* 有 P0LY 輸入能源中樞。

請注意音效中的變更。 它應該音效 muffled 和有點較小聲。 如果您能夠自行位置與塗鴉牆或您與能源中樞之間的其他物件時，您應該注意到因為真實世界會受阻擋音效進一步 muffling。

* 假設 *「 此處出現 」* 有 P0LY 保留能源中樞，並將本身放置您面前。

請注意，一旦 P0LY 結束能源中樞也會移除音效的阻擋物。 如果您仍然是期待阻擋，就可能會阻擋 P0LY 真實世界。 請嘗試以確定您有清楚的視野 P0LY 移動。

### <a name="part-3---room-models"></a>第 3 部分-聊天室模型

#### <a name="key-concepts"></a>重要概念

* 空間的大小提供張神奇參與音效當地語系化的佇列。
* 聊天室模型設定每位**AudioSource**。
* [Unity 的 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供程式碼，將空間模式設定。
* 混合實境體驗，針對選取的空間模型最適合的真實世界空間。

如果您要建立的虛擬實境案例，請選取 聊天室模型最適合虛擬環境。

## <a name="chapter-4---sound-design"></a>第 4 章-完善的設計

### <a name="objectives"></a>目標

* 了解有效完善的設計考量。
* 了解混用技術和指導方針。

### <a name="part-1---sound-and-experience-design"></a>第 1 部分-音效和體驗設計

本章節將討論主要的聲音和經驗的設計考量和指導方針。

#### <a name="normalize-all-sounds"></a>標準化所有的音效

這可避免需要特殊案例的程式碼來調整每個可能會很費時的音效的音量，並限制能夠輕鬆地更新音效檔。

#### <a name="design-for-an-untethered-experience"></a>設計 untethered 體驗

HoloLens 是完全自主、 untethered 全像攝影版的電腦。 您的使用者可以與將會使用您在移動時的體驗。 請務必測試您的聲音混合四處跑。

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>發出音效，從您全像投影上的邏輯位置

在真實世界中，dog 不會不會從其尾端吠，人類的語音不是來自他/她英呎。 避免您的聲音發出從您全像投影中未預期的部份。

針對小型全像投影，很合理的幾何中心所發出的聲音。

#### <a name="familiar-sounds-are-most-localizable"></a>熟悉的聲音都是最可當地語系化

人類聲音和音樂是很容易就能當地語系化。 只要有人撥打您的名稱，就能夠精確地判斷哪些來源之語音的方向和如何很遠的地方。 簡短、 不熟悉聽起來較難以當地語系化。

#### <a name="be-cognizant-of-user-expectations"></a>網站的使用者的期望

生命週期體驗扮演一個角色在我們能夠識別音效的位置。 這是其中一個原因，人類聲音為何特別容易當地語系化。 請務必留意您的使用者所學習到的期望放置您的聲音時。

比方說，當有人聽到 bird 歌曲他們通常查閱，因為鳥通常超過視野 （飛行或樹狀目錄中）。 是不常見的使用者開啟中，正確的方向，但看了錯誤的垂直方向，並成為混淆或挫折時找不到全像的位置。

#### <a name="avoid-hidden-emitters"></a>避免隱藏的 fixit 發出器

在真實世界中，如果我們聽到聲音，我們可以通常識別發出聲音的物件。 這也應該保留在您的經驗，則為 true。 它可以是非常令人不安聽到聲音，就是從來源位置的聲音的使用者，並無法看到物件。

有一些例外狀況，這個指導方針。 例如，環境的音效，例如 crickets 欄位中不需要會顯示。 生命週期體驗讓我們熟悉這些聲音，而不需要看到它的來源。

### <a name="part-2---sound-mixing"></a>第 2 部分-聲音混合

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>以您的混合 HoloLens 上 70%的磁碟區為目標

混合的實境體驗可讓全像投影至真實世界中看到。 它們也可讓要聽到的真實世界音效。 70%的磁碟區目標可讓使用者聽周遭世界，以及您的使用經驗的聲音。

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>在 100%的磁碟區的 HoloLens 應該掉外部清單

100%的磁碟區層級就像虛擬實境體驗。 以視覺化的方式，使用者會傳輸到不同的世界。 相同應該成立用語音。

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>使用 Unity AudioMixer 調整音效的類別

在設計您的混合時，通常很有幫助建立音效的類別，並有增加或減少其做為一個單位的磁碟區的能力。 這同時啟用快速且輕鬆地對整體混合保留相對的層級的每一種音效。 通用類別目錄包括：音效、 環境、 旁白和背景音樂。

#### <a name="mix-sounds-based-on-the-users-gaze"></a>根據使用者的視線混合音效

它通常可用來變更的聲音混合在您的位置為基礎的體驗或使用者的 （不） 尋找。 這項技術的常見用法之一是要減少全像投影全像攝影版的畫面格，以簡化使用者將焦點放在前面的資訊以外的磁碟區層級。 另一個用法是音效的，增加來強調使用者的一個重要事件的音量。

#### <a name="building-your-mix"></a>建置您混合

當建置您混合時，建議您開始使用您的體驗背景音訊，並新增根據重要性層級。 通常，這會導致正在比先前的每個圖層。

想像您混用做為反向的漏斗圖，以最不重要 （及一般 quietest 聲音） 在底部，建議以結構化您的混合類似下圖。

![聲音混合結構](images/soundlevels.png)

旁白是有趣的案例。 根據您所建立的經驗，您可能想讓立體聲的 （未當地語系化） 音效，或是 spatialize 您旁白。 兩個 Microsoft 發行體驗說明每個案例的絕佳範例。

[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)透過使用立體聲的語音。 當 [朗讀程式] 會描述正在檢視的位置時，音效是一致，而不會隨著使用者的位置。 這可讓朗讀程式，來描述而不離開環境 spatialized 音效製作場景。

[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)偵探的形式，透過利用 spatialized 的語音。 神探語音用來協助您將使用者的重要線索注意，如同實際的人類看得在聊天室中。 這可讓至體驗的訓練活動，解決神秘的更有意義。

### <a name="part-3--performance"></a>部分 3-效能

#### <a name="cpu-usage"></a>CPU 使用量

當使用空間音效，10-12 fixit 發出器會耗用大約 12%的 CPU。

#### <a name="stream-long-audio-files"></a>Stream 長音訊檔案

音訊資料可以是很大，尤其是在常見的取樣率 (44.1 和 48 kHz)。 一般規則是超過 5-10 秒的音訊檔案應該將它串流至降低應用程式的記憶體使用量。

在 Unity 中，您可以將標記中的檔案匯入設定資料流的音訊檔案。

![音訊的匯入設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>第 5 章-特殊效果

### <a name="objectives"></a>目標

* 加入 「 魔術 Windows 」 中的深度。
* 帶入虛擬世界中的使用者。

### <a name="magic-windows"></a>Magic Windows

#### <a name="key-concepts"></a>重要概念

* 到隱藏的世界中建立檢視，是以視覺方式吸引人。
* 加入音訊效果，接近隱藏世界雷射或使用者時，以加強真實性。

#### <a name="instructions"></a>指示

* 在 [**階層**] 面板中，展開**HologramCollection** ，然後選取**底世界**。
* 依序展開**底世界**，然後選取**VoiceSource**。
* 在**Inspector**  面板中，按一下**新增元件**，並新增**使用者語音效果**。

**AudioSource**元件會加入至**VoiceSource**。

* 在  **AudioSource**，將**輸出**來**UserVoice (Mixer)**。
* 請檢查**Spatialize**核取方塊。
* 拖曳**空間 Blend**滑桿，一直到**3D**，或輸入**1**編輯方塊中。
* 依序展開**3D 音效設定**。
* 設定**Doppler 層級**要**0**。
* 在**使用者語音生效**，將**父物件**來**底世界**從場景。
* 設定**最大距離**要**1**。

設定**最大距離**告訴**使用者語音效果**接近的使用者必須是父物件之前已啟用的效果。

* 在 **使用者語音生效**，展開**陣營參數**。
* 設定**深度**要**0.1**。
* 設定**點選 1 個磁碟區**，**點選 2 的磁碟區**並**點選 3 個磁碟區**至**0.8**。
* 設定**原始音效的音量**要**0.5**。

先前的設定中設定之參數的 Unity **AudioChorusFilter**用來將功能新增至使用者的語音。

* 在 **使用者語音生效**，展開**Echo 參數**。
* 設定**延遲**到**300**
* 設定**Decay 比例**要**0.2**。
* 設定**原始音效的音量**要**0**。

先前的設定中設定之參數的 Unity **AudioEchoFilter**用來造成使用者的語音來回應。

使用者語音效果指令碼會負責：

* 測量使用者之間的距離而**GameObject**附加指令碼。
* 判斷使用者是否正面向**GameObject**。

使用者必須面對 GameObject，不論距離，要啟用的效果。

* 套用並設定**AudioChorusFilter**並**AudioEchoFilter**來**AudioSource**。
* 停用篩選器停用生效。

使用者語音效果會使用 Mic Stream 選取器元件，從[Unity 的 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)，以選取高品質的聲音資料流，並將它路由傳送至 Unity 的音響系統。

* 在 **階層**面板中，選取**管理員**。
* 在 [ **Inspector** ] 面板中，展開**語音輸入處理常式**。
* 在 **語音輸入處理常式**，展開**顯示底世界**。
* 變更**沒有任何函式**要**UnderworldBase.OnEnable**。

![關鍵字：顯示底世界](images/showunderworld.png)

* 依序展開**隱藏底世界**。
* 變更**沒有任何函式**要**UnderworldBase.OnDisable**。

![關鍵字：隱藏底世界](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>建置和部署

* 同樣地，建置 Unity 專案，並在 Visual Studio 中部署。

應用程式部署後：

* 面臨 （牆上、 floor、 資料表） 的介面和 say *」 顯示底世界 」*。

將顯示底世界，並將隱藏所有其他全像投影。 如果看不到底世界，請確定您所面對的現實世界的介面。

* 底世界全像之 1 公尺內的方法，並開始交談。

現在有音訊效果套用至您的心聲 ！

* 背離底世界，並注意效果不會再套用的方式。
* 假設 *「 隱藏底世界 」* 隱藏底世界。

將隱藏底世界，先前隱藏全像投影會重新出現。

## <a name="the-end"></a>結束

恭喜您！ 您現在已完成**MR 空間 220:空間音效**。

聆聽世界和音效實現您的經驗 ！
