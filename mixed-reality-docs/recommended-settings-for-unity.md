---
title: Unity 的建議的設定
description: Unity 提供一些可透過 專案設定中切換的混合實境特有的行為。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: unity、 設定、 混合的實境
ms.openlocfilehash: c8b5598fa702954ca14b9b013e44ed38cf6075c2
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148665"
---
# <a name="recommended-settings-for-unity"></a>Unity 的建議的設定

Unity 提供一組通常是一般的情況下，所有平台的預設選項。 不過，Unity 會提供一些可透過 專案設定中切換的混合實境特有的行為。

## <a name="performant-environment-set-up"></a>高效能環境設定

### <a name="low-quality-settings"></a>低品質設定

請務必修改**Unity 品質設定**針對您的環境**非常低**。 這將有助於確保您的應用程式正在 performantly 以適當的畫面播放速率。 這是非常重要的 Hololens 的開發。 沈浸式耳機，根據電源 VR 體驗中，在桌面的規格上進行開發，其中仍可達到不含最低品質參數的畫面播放速率。 

在 Unity 2018 LTS + 中，專案的品質等級可以藉由設定：

底下**編輯** > **專案設定** > **品質**> 設定**預設**按一下若要向下的箭號**非常低**品質層級

### <a name="lighting-settings"></a>光源設定

與品質場景設定相似，務必設定您的混合實境應用程式的最佳光源設定。 在 Unity 中，通常會有最大的效能影響在場景的照明設定是**即時全域照明**。 這可以關閉移 **視窗** > **轉譯** > **光源設定** > **即時全域照明**。 

沒有其他光源的設定值，**內建全域照明**。 此設定可提供高效能及以視覺化方式顯著的結果上沈浸式耳機，但通常並不適用 HoloLens 的開發。 **內建全域 Illumniation**僅針對靜態 Gameobject 通常所沒有的未知且變動的環境由於 HoloLens 場景中的計算。

請閱讀[從 Unity 的通用照明](https://docs.unity3d.com/Manual/GIIntro.html)如需詳細資訊。 

>[!NOTE]
> **即時全域照明**nastavena**每個場景**和開發人員因此必須將每個 Unity 場景的這個屬性儲存在其專案。 

### <a name="single-pass-instancing-rendering-path"></a>單一行程的執行個體轉譯路徑

在混合實境應用程式中，場景會轉譯兩次，一次的每個使用者的眼睛。 相較於傳統的 3D 開發，此有效地加倍需要計算工作數量。 因此，務必選取最有效率的轉譯路徑儲存在 CPU 和 GPU 時間 Unity 中。 單一行程的執行個體的轉譯最佳化 Unity 轉譯管線的混合實境應用程式，因此建議您啟用此設定預設會針對每個專案。 

若要啟用這項功能在您的 Unity 專案
1)  開啟**Player XR 設定**(前往**編輯** > **專案設定** > **Player**  > **XR 設定**)
2) 選取 **執行個體的單一傳遞**從**立體轉譯方法**下拉式選單 (**虛擬實境支援**必須選取核取方塊)

如需詳細資訊，此轉譯方法，從 Unity 閱讀下列文章。
- [如何使用進階的立體聲呈現的 AR 及 VR 效能最大化](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [單一行程的執行個體](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 如果開發人員已經不是針對撰寫的現有自訂著色器，就會發生一個常見的問題，使用單一傳遞執行個體轉譯執行個體。 之後啟用此功能，開發人員可能會注意到某些 Gameobject 唯一呈現，一眼中。 這是因為相關聯的自訂著色器沒有適當的屬性執行個體。
>
> 請參閱[單一傳遞是立體聲呈現 HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)從 Unity 如何解決這個問題

### <a name="enable-depth-buffer-sharing"></a>啟用深度緩衝區共用

若要達到更佳的全像穩定性，從認知的使用者，建議啟用**深度緩衝區共用**Unity 中的屬性。 藉由開啟這個功能，Unity 會共用您的應用程式與 Windows Mixed Reality 平台所產生的深度對應。 平台可進一步最佳化全像穩定性，特別是針對任何指定的範圍內，您的應用程式所呈現的場景。

若要啟用這項功能在您的 Unity 專案
1) 開啟**Player XR 設定**(前往**編輯** > **專案設定** > **Player**  > **XR 設定**)
2) 選取的核取方塊**啟用深度緩衝區共用**下方**虛擬實境 Sdk** > **Windows Mixed Reality**擴充 (**虛擬但實際上支援**必須選取核取方塊)

此外，建議您選取**16 位元深度**下方**深度格式**設定在這個窗格中，特別是針對 Hololens 的開發。 因為移動/處理需要較少的資料，選取 16 位元相較於 24 位元會大幅會降低頻寬需求。

為了讓 Windows Mixed Reality 平台，以最佳化全像穩定性，它需倚賴是正確和比對任何螢幕上的呈現全像投影的深度緩衝區。 因此，使用共用上的深度緩衝區，很重要時呈現的色彩，也會呈現深度。 在 Unity 中，大部分的不透明或 TransparentCutout 材料會轉譯深度，根據預設，但透明而文字物件通常不會呈現深度雖然這是相依的著色器等等。 

如果使用混合的現實工具組標準的著色器，來呈現透明物件的深度：
1) 選取 使用標準 MRTK 著色器的透明資料並開啟 偵測器的 編輯器 視窗
2) 設定**轉譯模式**要**自訂**然後設定**模式**至**Transparent**最後設定和**深度撰寫**至**上**

>[!NOTE]
> 變更這些值加到相機接近/遠離平面設定時，開發人員應該要小心的 Z 打擊。 Z 對抗發生於兩個 gameobject 嘗試轉譯到相同的像素和由於的深度緩衝區 （也就是精確度的限制 z 深度），Unity 無法分辨哪一個物件是另。 開發人員會發現兩個遊戲的物件，因為它們之間的閃爍*對抗*相同的 z 深度值。 可以藉由切換至 24 位元深度格式，因為會有較大範圍的值來計算時，其 z 深度相機中的每個物件解決此問題。
>
> 不過，建議，特別 Hololens 的開發，若要修改相機附近的遠改為平面以較小的範圍和保留的 16 位元深度格式化。 Z 深度非以線性方式對應至沿著遠近觀景窗的值範圍的飛機。 這可以藉由選取修改*Main Camera*場景中，然後在**Inspector**，變更**不久 & 遠裁剪平面**該值，以減少其範圍 （亦即 從 1000 x 值至 100 m 或其他 m，等。）

### <a name="building-for-il2cpp"></a>針對 IL2CPP 進行建置

Unity 已取代為.net 後端，因此建議開發人員利用指令碼的支援**IL2CPP**其 UWP 的 visual studio 會建置。 雖然這會帶各種優點，請從 Unity 的建置 visual studio 方案**Il2CPP**可以 signficantly 低於舊的.NET 方法。 因此，強烈建議遵循最佳做法進行建置**IL2CPP**以節省開發反覆項目時間。

1) 利用累加建置，藉由建置專案，以相同的目錄每次重複那里使用預先建置的檔案
2) 停用反惡意程式碼軟體掃描，為您的專案 （& b) 資料夾
   - 開啟**病毒與威脅防護**下您的 Windows 10 設定應用程式
   - 選取 **管理設定**下方**病毒與威脅防護設定**
   - 選取 **新增或移除的排除項目**下方**排除項目**區段
   - 按一下 **加入排除**，並選取該資料夾包含 Unity 專案的程式碼，並建置輸出
3) 利用建置 SSD

請閱讀[最佳化建置時間 IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)如需詳細資訊。

> [!NOTE]
> 此外，設定[快取伺服器](https://docs.unity3d.com/Manual/CacheServer.html)可能會有幫助，對於有大量資產 (排除指令檔) 或不斷變更場景/資產的 Unity 專案來說，更是如此。 開啟專案時，Unity 會將符合資格的資產以內部快取格式儲存在開發機器上。 項目必須重新匯入，因此修改時必須加以重新處理。 此程序可以執行一次後就儲存在快取伺服器中，之後再與其他開發人員共用以節省時間，而不是每位開發人員都在本機處理新變更的重新匯入工作。

## <a name="publishing-properties"></a>發行屬性

### <a name="holographic-splash-screen"></a>全像攝影版的啟動顯示畫面

HoloLens 具有行動類別 CPU 和 GPU，這表示應用程式可能需要較長的時間載入。 正在載入應用程式，使用者只會看到黑色，而因此它們可能會想知道發生什麼情況。 若要 reassure 它們在載入期間，您可以新增全像攝影版的啟動顯示畫面。

若要切換全像攝影版的啟動顯示畫面：
1) 移至**編輯** > **專案設定** > **Player**頁面
2) 按一下  **Windows 市集**索引標籤，然後開啟**開頭顯示畫面影像**區段
3) 適用於在您想要的映像**Windows 全像攝影版 > 全像攝影版的開頭顯示畫面影像**屬性。
    - 切換**顯示 Unity 啟動顯示畫面**選項會啟用或停用 Unity 加上品牌的啟動顯示畫面。 如果您沒有 Unity Pro 授權，將一律顯示 Unity 品牌的啟動顯示畫面。
    - 如果**全像攝影版的開頭顯示畫面影像**是套用，它將一律顯示不論是否啟用或停用顯示 Unity 啟動顯示畫面 核取方塊。 指定自訂全像攝影版的開頭顯示畫面影像只會提供給開發人員使用 Unity Pro 授權。

|  顯示 Unity 啟動顯示畫面  |  全像攝影版的開頭顯示畫面影像  |  行為 |
|----------|----------|----------|
|  開啟  |  None  |  會顯示預設 Unity 啟動顯示畫面的 5 秒，或直到載入應用程式時，較長者為準。 | 
|  開啟  |  自訂  |  自訂啟動顯示畫面會顯示 5 秒，或直到載入應用程式時，較長者為準。 | 
|  關閉  |  None  |  要等到載入應用程式顯示透明的黑色 (nothing)。 | 
|  關閉  |  自訂  |  自訂啟動顯示畫面會顯示 5 秒，或直到載入應用程式時，較長者為準。 | 

請閱讀[Unity 的啟動顯示畫面的文件](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html)如需詳細資訊。

### <a name="tracking-loss"></a>追蹤遺失

取決於看到其建構周圍環境的混合的實境耳機[世界鎖定座標系統](coordinate-systems-in-unity.md)，可讓全像投影保留在位置中。 耳機找不到本身世界耳機時，即所謂具有*遺失追蹤*。 在這些情況下，取決於全球鎖定座標系統，例如空間階段、 空間的錨點和空間的對應功能無法運作。

如果發生遺失的追蹤，Unity 的預設行為是要停止轉譯全像投影，請暫停[遊戲迴圈](http://docs.unity3d.com/Manual/ExecutionOrder.html)，並顯示該增至遺失通知追蹤遵循使用者視線。 也可以追蹤的形式提供自訂通知遺失映像。 針對相依於追蹤其完整的體驗的應用程式，即已足夠讓 Unity 控點，這完全重新取得追蹤項目。 開發人員可以提供要顯示在追蹤遺失的自訂映像。 

若要自訂追蹤遺失映像：
1) 移至**編輯** > **專案設定** > **Player**頁面
2) 按一下  **Windows 市集**索引標籤，然後開啟**開頭顯示畫面影像**區段
3) 適用於在您想要的映像**Windows 全像攝影版 > 追蹤遺失映像**屬性。

#### <a name="opt-out-of-automatic-pause"></a>選擇不自動暫停

某些應用程式可能不需要追蹤 (例如[方向專用的應用程式](coordinate-systems-in-unity.md)例如 360 度的視訊檢視器) 或可能需要繼續處理不受干擾，在追蹤時將會遺失。 在這些情況下，應用程式可以退出預設遺失追蹤行為。 選擇此開發人員負責隱藏/停用任何不會在追蹤遺失的案例中正確轉譯的物件。 在大部分情況下，建議您，案例是本文鎖定的內容，會呈現的唯一內容會環繞主攝影機。

若要退出自動暫停行為：
1) 移至**編輯** > **專案設定** > **Player**頁面
2) 按一下  **Windows 市集**索引標籤，然後開啟**開頭顯示畫面影像**區段
3) 修改**Windows 全像攝影版 > 上追蹤遺失暫停和顯示的影像**核取方塊。

#### <a name="tracking-loss-events"></a>追蹤遺失事件

若要定義自訂行為，追蹤遺失時，處理全域[追蹤遺失事件](tracking-loss-in-unity.md)。

### <a name="capabilities"></a>功能

若要利用特定功能的應用程式，它必須宣告適當的功能資訊清單中。 可以在 Unity 中進行資訊清單宣告，因此它們會包含在每個後續的專案匯入。 

混合實境應用程式，就可以啟用功能：
1) 移至**編輯** > **專案設定** > **Player**頁面
2) 按一下  **Windows 市集**索引標籤，然後開啟**發佈設定**區段，然後尋找**功能**清單

啟用全像攝影版的應用程式常用的 Api 適用的功能如下：
<br>

|  功能  |  需要功能的 Api |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver | 
|  WebCam  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture 或 VideoCapture，分別 （儲存時所擷取的內容） | 
|  麥克風  |  VideoCapture （當擷取音訊）、 DictationRecognizer、 GrammarRecognizer 和 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer （以及使用 Unity Profiler） | 

## <a name="see-also"></a>另請參閱
* [Unity 開發概觀](unity-development-overview.md)
* [For Mixed Reality Understaing 效能](understanding-performance-for-mixed-reality.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
