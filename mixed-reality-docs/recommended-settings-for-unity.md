---
title: Unity 的建議設定
description: Unity 提供一些混合現實特有的行為，可以透過專案設定進行切換。
author: troy-ferrell
ms.author: trferrel
ms.date: 07/07/2020
ms.topic: article
keywords: unity，設定，混合現實
ms.openlocfilehash: d2cc79ba0818985795c49f8812d33eba77b92b74
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390115"
---
# <a name="recommended-settings-for-unity"></a>Unity 的建議設定

Unity 提供一組預設選項，通常是所有平臺的平均案例。 不過，Unity 提供一些混合現實特有的行為，可以透過專案設定進行切換。

## <a name="performant-environment-set-up"></a>高效能環境設定

### <a name="low-quality-settings"></a>低品質設定

請務必將您環境的**Unity 品質設定**修改為**極低**。 這將有助於確保您的應用程式以適當的幀速度執行 performantly。 這對於 HoloLens 開發而言非常重要。 為了在沉浸式耳機上進行開發，視桌上型電腦為 VR 經驗所提供的規格而定，您仍然可以在沒有最低品質參數的情況下達到畫面播放速率。

在 Unity 2019 LTS + 中，您可以藉由前往 [**編輯**專案設定品質] 來設定專案的品質等級  >  **Project Settings**  >  **Quality** ，並按一下向下箭號到**非常低**的品質等級來設定**預設值**。

### <a name="lighting-settings"></a>光源設定

類似于品質場景設定，請務必為您的混合現實應用程式設定最佳光源設定。 在 Unity 中，通常會對場景產生最佳效能影響的光源設定，是**即時的全域照明**。 這可以藉由在**視窗**轉譯  >  **Rendering**  >  **光源設定**  >  **即時全域照明**來關閉。

還有另一個光源設定，也就是**內建全域照明**。 此設定可在沉浸式耳機上提供高效能和視覺效果的結果，但通常不適用於 HoloLens 開發。 **內建 Global Illumniation**僅針對靜態 gameobject 計算，通常在 HoloLens 場景中找不到，因為有未知和變動環境的本質。

如需詳細資訊，請參閱[Unity 中的全域照明](https://docs.unity3d.com/Manual/GIIntro.html)。 

>[!NOTE]
> **即時全域照明**設定為**每個場景**，因此開發人員必須為其專案中的每個 Unity 場景儲存這個屬性。

### <a name="single-pass-instancing-rendering-path"></a>單一傳遞實例轉譯路徑

在混合式現實應用程式中，場景會轉譯兩次，每一眼就會對使用者呈現一次。 相較于傳統的3D 開發，這實際上會使需要計算的工作量加倍。 因此，請務必在 Unity 中選取最有效率的轉譯路徑，以節省 CPU 和 GPU 時間。 單一傳遞實例轉譯會將混合現實應用程式的 Unity 轉譯管線優化，因此建議您針對每個專案預設啟用這項設定。

若要在 Unity 專案中啟用這項功能

1)  開啟 [Player XR 設定] (移至 [編輯] > [專案設定] > [播放器] > [XR 設定])
2) 從 [立體聲轉譯方法] 下拉式功能表中，選取 [單通道執行個體化] (必須核取 [支援的虛擬實境] 核取方塊)

如需此轉譯方法的詳細資訊，請參閱 Unity 中的下列文章。

- [如何使用進階的立體聲轉譯將 AR 和 VR 效能最大化](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [單通道執行個體](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> 如果開發人員已經有非針對執行個體撰寫的現有自訂著色器，就會發生單通道執行個體化轉譯的一個常見問題。 啟用這項功能之後，開發人員可能會注意到，有些 GameObject 只會在單一眼球中轉譯。 這是因為相關聯的自訂著色器沒有適當的執行個體屬性。
>
> 如需解決此問題的方法，請參閱 Unity 中的[適用於 HoloLens 的單通道立體聲轉譯](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)

### <a name="enable-depth-buffer-sharing"></a>啟用深度緩衝區共用

若要從使用者的認知中達到更佳的全息影像穩定性，建議您啟用 Unity 中的**深度緩衝區共用**屬性。 藉由開啟此項，Unity 將會與您的應用程式所產生的深度對應，與 Windows Mixed Reality 平臺共用。 然後，平臺就能夠為您的應用程式所呈現的任何特定框架，更有效地為您的場景優化全息的全像投影穩定性。

若要在 Unity 專案中啟用這項功能

1) 開啟 [Player XR 設定] (移至 [編輯] > [專案設定] > [播放器] > [XR 設定])
2) 選取 [**虛擬實境 sdk**] 底下的 [**啟用深度緩衝區共用**] 核取方塊 [  >  **Windows Mixed Reality**擴充] （必須核取 [**虛擬實境支援**] 核取方塊）

此外，建議您在此面板中選取 [**深度格式**] 設定下的 [ **16 位深度**]，特別是針對 HoloLens 開發。 相較于24位，選取 [16 位] 會大幅降低頻寬需求，因為需要移動/處理的資料才會變少。

為了讓 Windows Mixed Reality 平臺優化全息全像的穩定性，它依賴深度緩衝區來精確，並符合螢幕上任何轉譯的全息影像。 因此，在上進行深度緩衝區共用時，在轉譯色彩時，也必須呈現深度。 在 Unity 中，大部分不透明或 TransparentCutout 的材質預設都會呈現深度，但透明和文字物件通常不會呈現深度，雖然這是著色器相依的等等。

如果使用[混合現實工具組標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)來呈現透明物件的深度：

1) 選取使用 MRTK 標準著色器的透明材質，然後開啟 [偵測器編輯器] 視窗
2) 選取深度緩衝區共用警告中的 [**立即修正**] 按鈕。 這也可以透過將轉譯**模式**設定為**自訂**來手動執行;然後將**模式**設定為 [**透明**]，最後將 [**深度寫入**] 設定為 [**開啟**]

> [!IMPORTANT]
> 開發人員應該注意，在變更這些值時，以及相機的近/上平面設定時，會有 Z 對抗。 當兩個 gameobject 嘗試轉譯為相同的圖元，且由於深度緩衝區的精確度限制（也就是 z 深度），Unity 無法分辨哪個物件位於另一個物件前面。 開發人員會注意到兩個遊戲物件之間的閃爍，因為它們會*對抗*相同的 z 深度值。 這可以藉由切換為24位深度格式來解決，因為每個物件會有更大範圍的值來計算其在相機中的 z 深度。
>
> 不過，建議使用，特別是針對 HoloLens 開發，將相機的近距離和最遠平面修改為較小的範圍，而保留16位深度格式。 Z 深度會以非線性方式對應到距離相機平面附近的值範圍。 這可以藉由選取場景中的*主要攝影機*，然後在 [偵測**器**] 底下，變更**接近 & 的裁剪平面**值，以減少其範圍（亦即， 從1000m 到100m 或其他 x 值等等）

>[!IMPORTANT]
> 使用16位深度格式時， [Unity 不會建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)。 因此，除非選取了會建立[8 位樣板緩衝區](https://docs.unity3d.com/Manual/SL-Stencil.html)的24位深度格式，否則某些 Unity UI 效果和其他樣板所需的效果將無法使用。

### <a name="building-for-il2cpp"></a>建立 IL2CPP

Unity 已淘汰 .NET 腳本後端的支援，因此建議開發人員針對其 UWP visual studio 組建使用**IL2CPP** 。 雖然這帶來了各種優點，但從 Unity for **IL2CPP**建立 visual studio 解決方案的速度會明顯低於舊的 .net 方法。 因此，強烈建議您遵循建立**IL2CPP**的最佳作法，以節省開發反復專案的時間。

1) 每次在相同的目錄中重複使用預先建立的檔案，以利用增量建築物
2) 針對您的專案 & 組建資料夾停用反惡意程式碼軟體掃描
   - 在您的 Windows 10 設定應用程式下開啟**病毒 & 威脅防護**
   - 在 [**病毒 & 威脅防護設定**] 底下選取 [**管理設定**]
   - 選取 [**排除**] 區段底下的 [**新增或移除排除**專案]
   - 按一下 [**新增排除**]，然後選取包含 Unity 專案程式碼和組建輸出的資料夾。
3) 利用 SSD 來建立

請閱讀[優化 IL2CPP 的組建時間](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)以取得詳細資訊。

> [!NOTE]
> 此外，設定[快取伺服器](https://docs.unity3d.com/Manual/CacheServer.html)可能會有幫助，對於有大量資產 (排除指令檔) 或不斷變更場景/資產的 Unity 專案來說，更是如此。 開啟專案時，Unity 會將符合資格的資產以內部快取格式儲存在開發機器上。 項目必須重新匯入，因此修改時必須加以重新處理。 此程序可以執行一次後就儲存在快取伺服器中，之後再與其他開發人員共用以節省時間，而不是每位開發人員都在本機處理新變更的重新匯入工作。

## <a name="publishing-properties"></a>發行屬性

### <a name="holographic-splash-screen"></a>全像攝影畫面

HoloLens 具有行動類別的 CPU 和 GPU，這表示應用程式可能需要較長的時間才能載入。 當應用程式載入時，使用者只會看到黑色，因此他們可能會想知道發生了什麼事。 若要在載入期間 reassure 它們，您可以新增全像的啟動顯示畫面。

若要切換全像攝影的啟動顯示畫面：

1) 前往**編輯**  >  **專案設定**  >  **播放機**頁面
2) 按一下 [ **Windows Store** ] 索引標籤，然後開啟 [**啟動顯示映射**] 區段
3) 將所需的影像套用到 **> Windows**全像攝影版的「全像攝影」影像屬性下。
    - 切換 [**顯示 Unity 啟動顯示**畫面] 選項將會啟用或停用 Unity 品牌啟動顯示畫面。 如果您沒有 Unity Pro 授權，將一律會顯示 Unity 品牌啟動顯示畫面。
    - 如果套用全像攝影**啟動顯示畫面**，不論是否啟用或停用 [顯示 Unity 啟動顯示畫面] 核取方塊，一律會顯示該影像。 只有具備 Unity Pro 授權的開發人員才能夠指定自訂的全像攝影啟動顯示畫面。

|  顯示 Unity 啟動顯示畫面  |  全像攝影啟動顯示畫面  |  行為 |
|----------|----------|----------|
|  開啟  |  無  |  在5秒內顯示預設的 Unity 啟動顯示畫面，或在載入應用程式之前，以較長的時間為准。 |
|  開啟  |  自訂  |  在5秒內顯示自訂啟動顯示畫面，或在載入應用程式之前，以較長的時間為准。 |
|  關閉  |  無  |  在載入應用程式之前，顯示透明的黑色（無）。 |
|  關閉  |  自訂  |  在5秒內顯示自訂啟動顯示畫面，或在載入應用程式之前，以較長的時間為准。 |

如需詳細資訊，請閱讀[Unity 的啟動顯示畫面檔](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html)。

### <a name="tracking-loss"></a>追蹤遺失

混合現實耳機取決於其周圍的環境，以建立[世界鎖定的座標系統](coordinate-systems-in-unity.md)，讓全息影像保持在位置。 當耳機在世界各地找不到自己時，即表示耳機已*遺失追蹤*。 在這些情況下，相依于全球鎖定座標系統的功能（例如空間階段、空間錨點和空間對應）無法運作。

如果發生追蹤遺失，Unity 的預設行為是停止轉譯全息影像、暫停[遊戲迴圈](https://docs.unity3d.com/Manual/ExecutionOrder.html)，以及顯示可輕鬆遵循使用者的追蹤遺失通知。 您也可以使用追蹤遺失影像的形式來提供自訂通知。 對於相依于追蹤整體體驗的應用程式而言，讓 Unity 完全可以處理這種情況，直到重新取得追蹤為止。 開發人員可以提供在追蹤遺失期間顯示的自訂影像。

若要自訂追蹤遺失的影像：

1) 前往**編輯**  >  **專案設定**  >  **播放機**頁面
2) 按一下 [ **Windows Store** ] 索引標籤，然後開啟 [**啟動顯示映射**] 區段
3) 將所需的影像套用到 Windows 全像 **> 追蹤遺失影像**] 屬性下。

#### <a name="opt-out-of-automatic-pause"></a>退出自動暫停

某些應用程式可能不需要追蹤（例如，[僅限方向的應用程式](coordinate-systems-in-unity.md)，例如360度的影片檢視器），或可能需要在追蹤遺失時繼續處理。 在這些情況下，應用程式可以選擇不執行追蹤行為的預設遺失。 選擇這種方式的開發人員會負責隱藏/停用不會在追蹤遺失案例中正確呈現的任何物件。 在大部分情況下，建議在該情況下轉譯的內容，是以主要相機為中心的主體鎖定內容。

若要退出自動暫停行為：

1) 移至 [**編輯**  >  **專案設定**]  >  **播放機**頁面
2) 按一下 [ **Windows Store** ] 索引標籤，然後開啟 [**啟動顯示映射**] 區段
3) 修改 [**追蹤遺失時暫停] 和 [顯示影像**] 核取方塊的 Windows 全像 >。

#### <a name="tracking-loss-events"></a>追蹤遺失事件

若要在追蹤遺失時定義自訂行為，請處理全域[追蹤遺失事件](tracking-loss-in-unity.md)。

### <a name="capabilities"></a>功能

若要讓應用程式利用特定功能，它必須在其資訊清單中宣告適當的功能。 資訊清單宣告可在 Unity 中進行，使其包含在每個後續的專案匯出中。

您可以藉由下列方式，為混合現實應用程式啟用功能：

1) 前往**編輯**  >  **專案設定**  >  **播放機**頁面
2) 按一下 [ **Windows Store** ] 索引標籤，開啟 [**發行設定**] 區段，然後尋找 [**功能**] 清單

適用于為全像攝影應用程式啟用常用 Api 的功能如下：
<br>

|  功能  |  需要功能的 Api |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  網路  |  PhotoCapture 和 VideoCapture |
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture，分別是（儲存已捕獲的內容時） |
|  麥克風  |  VideoCapture （在捕獲音訊時）、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer |
|  InternetClient  |  DictationRecognizer （並使用 Unity Profiler） |

## <a name="see-also"></a>另請參閱

* [Unity 開發概觀](unity-development-overview.md)
* [了解混合實境的效能](understanding-performance-for-mixed-reality.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
