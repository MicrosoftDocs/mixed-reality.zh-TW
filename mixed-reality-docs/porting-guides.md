---
title: 移植指南
description: 逐步解說會逐步解說說明如何將現有的沈浸式應用程式到 Windows 混和實境移植。
author: ChimeraScorn
ms.author: cwhite
ms.date: 10/02/2018
ms.topic: article
keywords: 連接埠、 移轉、 unity、 中介軟體引擎，UWP
ms.openlocfilehash: a4a8c78f1c45fd8e3b85a767d139bae9f67540e0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595360"
---
# <a name="porting-guides"></a>移植指南

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。

Windows 10 直接包含如耳機沈浸式和全像攝影版的支援。 如果您已建立的另一部裝置，例如 Oculus Rift 或 HTC Vive 內容，這些會對相依性存在上述作業系統的平台 API 的程式庫。 到 Windows 混和實境帶現有內容涉及重定目標的 Windows api 的這些其他 Sdk 的使用方式。 [Windows 平台 Api 的混合實境](https://docs.microsoft.com/uwp/api/Windows.Perception)只能在通用 Windows 平台 (UWP) 應用程式模型中運作。 因此如果您的應用程式已建置適用於 UWP，移植到 UWP 會移轉體驗的一部分。

## <a name="porting-overview"></a>移轉概觀

概括來說，這些是移植現有內容所需的步驟：
1. **請確定您的電腦執行 Windows 10 Fall Creators Update (16299)。** 我們不再建議接收預覽，從繼續 Insider 略過更新響鈴，建置這些組建不會是最穩定的混合的實境開發。
2. **升級至最新版的圖形或遊戲引擎。** 遊戲引擎必須支援 Windows 10 SDK （2017 年 4 月發行） 的 10.0.15063.0 版或更高版本。
3. **升級任何中介軟體、 外掛程式或元件。** 如果您的應用程式包含的任何元件，它會是個不錯的主意，升級至最新版本。 較新版本的最常見的外掛程式有適用於 UWP 的支援。
4. **移除重複的 sdk 的相依性**。 根據您的內容的目標的裝置，您將需要移除，或有條件地編譯出該 SDK (例如 SteamVR) 讓您可以改為目標的 Windows Api。
5. **逐步建立問題。** 此時，移植練習旨在說明您的應用程式、 您的引擎和您擁有的元件相依性。

## <a name="common-porting-steps"></a>常見的移轉步驟

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>常見的步驟 1:請確定您有正確的開發硬體

[安裝工具](install-the-tools.md#for-immersive-vr-headset-development)頁面會列出建議的開發硬體。

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>常見的步驟 2:升級至 Windows 10 最新的航班

Windows Mixed Reality 平台仍在進行開發，而若要最有效，但建議您在 「 Windows 測試人員快速 「 班機。 若要存取 windows 航班，您必須[加入 Windows Insider 計劃](https://insider.windows.com/)。
1. 安裝[Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [加入](https://insider.windows.com/)Windows Insider 計劃。
3. 啟用[開發人員模式](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. 切換至[快速 Windows Insider 航班](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)透過設定--> 更新與安全性 > 一節

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>常見的步驟 3:升級至 Visual Studio 的最新的組建
* 請參閱[安裝工具](install-the-tools.md#installation-checklist)頁面的 Visual Studio 2017 下

### <a name="common-step-4-be-ready-for-the-store"></a>常見的步驟 4:準備好供存放區
* 使用[Windows 應用程式認證套件](https://developer.microsoft.com/windows/develop/app-certification-kit)(也稱為 WACK) 及早且經常 ！
* 使用[Portability Analyzer](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([下載](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>常見的步驟 5:選擇正確的配接器
* 使用兩個 Gpu，notebook 等系統中[為目標的正確介面卡](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。 這適用於 Unity 應用程式，除了原生的 DirectX 應用程式，其中 ID3D11Device 建立時，明確或隱含 （媒體基礎），其功能。

## <a name="unity-porting-guidance"></a>Unity 移植指引

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity 步驟 1:請遵循常見的移轉步驟

請遵循所有的一般步驟。 在 步驟 #3 中，選取**使用 Unity 進行遊戲開發**工作負載。 因為您將從下面的指示安裝 Unity 的較新版本，您可能會取消選取 Unity 編輯器的選擇性元件。

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity 步驟 2:升級至最新的公用組建的 Windows MR 支援 Unity
1. 下載最新[建議的 Unity 的公用組建](install-the-tools.md)混合實境支援。
2. 在開始之前，儲存一份您的專案
3. 檢閱[文件](https://docs.unity3d.com/Manual/UpgradeGuides.html)用於從 Unity 移植。
4. 請遵循[指示](https://docs.unity3d.com/Manual/APIUpdater.html)Unity 的網站使用其自動 API 更新程式
5. 檢查並查看是否有其他變更，您必須先取得您的專案執行，並透過任何剩餘的錯誤和警告。 注意：如果您依賴的中介軟體，您可能需要更新開始 （在下面的步驟 3 的詳細資料） 的中介軟體。

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity 步驟 3:升級至最新版本的中介軟體

使用任何 Unity 更新時，沒有您需要更新您的遊戲或應用程式相依於一或多個中介軟體封裝的機會。 此外，所有中介軟體的最新版本會增加您的移轉程序的其餘部分成功的可能性。 許多中介軟體封裝最近已新增支援適用於通用 Windows 平台 (UWP)，並升級至最新版本可讓您運用這項工作。

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity 步驟 4:目標執行通用 Windows 平台 (UWP) 應用程式

在之後安裝工具，您需要取得做為通用 Windows 應用程式執行的應用程式。
* 請遵循[詳細的逐步解說逐步解說](https://unity3d.com/partners/microsoft/porting-guides)Unity 所提供。 請注意，您應該持續在最新 LTS 版本 （任何 20xx.4 發行） 的 Windows MR 上。
* 如需更多的 UWP 開發資源，看看[Windows 10 遊戲開發指南](https://docs.microsoft.com/windows/uwp/gaming/e2e)。
* 請注意，Unity 會持續改善 IL2CPP 支援;IL2CPP 讓某些 UWP 連接埠大幅簡化。 如果您目前的目標.Net 後端的指令碼，您應該考慮將轉換成改為利用 IL2CPP 後端。

注意：如果您的應用程式會具有任何相依性的裝置特定的服務，例如相符項目從資料流，您必須停用它們在此步驟。 稍後，您可以連結到 Windows 提供的對等服務。

### <a name="unity-step-5-deprecated"></a>Unity 步驟 5:（已過時）

步驟 5 已不再需要的。 我們會保留這裡使編製索引的步驟維持不變。

### <a name="unity-step-6-get-your-windows-mixed-reality-hardware-set-up"></a>Unity 步驟 6:取得您的 Windows Mixed Reality 硬體設定
1. 檢閱中的步驟[沈浸式耳機安裝程式](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. 深入了解[使用 Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)和[瀏覽 Windows Mixed Reality 首頁](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity 步驟 7:目標執行 Windows Mixed reality 應用程式
1. 首先，您必須移除，或有條件地編譯特定 VR SDK 任何其他程式庫支援。 這些資產經常變更設定和您的專案，方式與其他 VR Sdk 中，例如 Windows Mixed Reality 不相容的屬性。
    * 例如，如果您的專案參考 SteamVR SDK，您必須更新專案，以匯出為 Windows 市集建置目標時，排除這些 prefabs 和指令碼 API 呼叫。
    * 即將推出，可以有條件地排除其他 VR Sdk 的特定步驟。
2. 在 Unity 專案中，[目標 Windows 10 SDK](holograms-100.md#target-windows-10-sdk)
3. 針對每個場景，[設定觀景窗](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity 步驟 8:若要將內容放在地上使用階段

您可以跨各種不同的建置混合實境體驗[體驗標尺](coordinate-systems.md)。

如果您要移植**安插擴展經驗**，您必須確定設定為 Unity **「 定態**追蹤空間類型：

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

這會設定 Unity 的全局座標系統來追蹤[靜態參考座標系](coordinate-systems.md#spatial-coordinate-systems)。 在 「 定態的追蹤模式中，內容會放在編輯器中只前方相機的預設位置 （正向是-Z） 應用程式啟動時，會出現在使用者之前。 以 recenter 使用者的插入擴充槽原點，您可以呼叫 Unity [XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法。

如果您要移植**常設擴展經驗**或**聊天室擴展經驗**，將要放置內容相對於最低限度值。 您會理解使用者的 floor 使用 **[空間階段](coordinate-systems.md#spatial-coordinate-systems)** 、 樓層來源和選擇性空間界限代表使用者的定義、 設定期間第一次執行。 對於這些體驗，您必須確定設定為 Unity **RoomScale**追蹤空間型別。 雖然 RoomScale 是預設值，您會想要加以明確設定，並確保您取得上一步，則為 true，以擷取其中使用者已離開聊天室它們校正移動其電腦的情況下：

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

一旦您的應用程式已成功設定追蹤的空間型別，內容放在 y 軸上 RoomScale = 的 0 平面會出現在最低限度值。 （0，0，0） 處的原點，將會在最低限度值的空間在安裝期間，使用者名人-z 表示它們已在安裝期間對向的正向方向其中的特定位置。

在指令碼，您可以呼叫您 TryGetGeometry 方法正在 UnityEngine.Experimental.XR.Boundary 型別，以取得界限的多邊形，然後指定 TrackedArea 界限類型。 如果使用者定義的界限 （得到頂點清單），您就會知道它是安全地傳遞**聊天室擴展經驗**給使用者，可以走的地方周圍場景您建立。

請注意，系統會自動轉譯界限使用者接近它時。 您的應用程式不需要使用此多邊形呈現本身的界限。

如需詳細資訊，請參閱 < [Unity 中的座標系統](coordinate-systems-in-unity.md)頁面。

有些應用程式可以使用矩形來限制其互動。 擷取最大的內切的矩形不直接支援 UWP API 或 Unity 中。 範例程式碼連結至以下顯示如何尋找已追蹤的範圍內的矩形。 它是基礎，因此可能不會找到最好的解決方案的啟發學習法，不過，結果通常與預期一致。 可以微調演算法中的參數，以尋找更精確的結果，但代價是處理時間。 此演算法會為使用 5.6 preview MRTP Unity 版本的混合實境工具組 (fork） 中。 這不是可公開取得。 您應該直接使用 Unity 2017.2 和更高版本中的程式碼。 程式碼會在不久的將來移植到目前 MRTK。

[GitHub 上的程式碼的 zip 檔案](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20)重要檔案：
* Assets/HoloToolkit/Stage/Scripts/StageManager.cs-使用方式的範例
* Assets/HoloToolkit/Stage/Scripts/LargestRectangle.cs-演算法的實作
* Assets/HoloToolkit-UnitTests/Editor/Stage/LargestRectangleTest.cs-演算法的一般測試

結果範例：

![結果範例](images/largestrectangle-400px.jpg)

由 Daniel Smilkov，演算法根據部落格：[多邊形中的最大矩形](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Unity 步驟 9:透過您輸入的模型運作

每個遊戲或應用程式為目標的現有 HMD 會有一組它所處理的輸入、 輸入所需的體驗，與特定 Api，它會呼叫以取得這些輸入的類型。 我們已投資在嘗試建立以簡單又直截了當越好，以善用 Windows Mixed Reality 中可用的輸入。
1. 閱讀 **[輸入移植指南 Unity](input-porting-guide-for-unity.md)** 如需詳細的 Windows Mixed Reality 公開 （expose） 的輸入，以及如何對應至您應用程式可能會立即執行。
2. 選擇您要利用 Unity 的跨-VR-SDK 輸入 API，或 MR 特定輸入的 API。 一般的 Input.GetButton/Input.GetAxis Api 所使用 Unity VR 應用程式，今天就[Oculus 輸入](https://docs.unity3d.com/Manual/OculusControllers.html)並[OpenVR 輸入](https://docs.unity3d.com/Manual/OpenVRControllers.html)。 如果您的應用程式已經在使用這些 Api 的動作控制站，這是最簡單的路徑，-您應該只需要重新對應按鈕與軸在輸入管理員。
    * 您可以存取在 Unity 中使用的一般跨-VR-SDK Input.GetButton/Input.GetAxis Api 或 MR 專屬 UnityEngine.XR.WSA.Input Api 移動控制站的資料。 （先前以在 Unity 5.6 UnityEngine.XR.WSA.Input 命名空間）
    * 請參閱[工具組中的範例](https://github.com/Microsoft/HoloToolkit-Unity/pull/572)，結合遊樂器 」 和 「 動作控制站。

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity 步驟 10:效能測試與微調

Windows Mixed Reality 將可在廣泛的類別的裝置上，範圍從高結束遊戲電腦時，向廣泛的市場主要電腦。 根據您的目標哪些市場，還有您的應用程式的可用運算和圖形預算顯著的差異。 在本移植的練習中，您可能會利用進階的電腦，及有大量運算和圖形預算提供您的應用程式。 如果您想要您的應用程式提供給更廣泛的對象，您應該測試並分析您的應用程式[代表您想要的硬體目標](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。

兩者[Unity](https://docs.unity3d.com/Manual/Profiler.html)並[Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index)包括效能分析工具，以及兩者[Microsoft](understanding-performance-for-mixed-reality.md)和[Intel](https://software.intel.com/articles/vr-content-developer-guide)上發行的指導方針效能分析和最佳化。 沒有效能的廣泛討論網址[了解效能 for Mixed Reality](understanding-performance-for-mixed-reality.md)。 此外，在 Unity 底下的特定詳細資料[Unity 的效能建議](performance-recommendations-for-unity.md)。

## <a name="see-also"></a>另請參閱
* [移植指南 Unity 的輸入](input-porting-guide-for-unity.md)
* [Windows Mixed Reality 最小電腦的硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [了解效能 for Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Unity 的效能建議](performance-recommendations-for-unity.md)
* [加入 Unity 中的 Xbox Live 的支援，適用於 UWP](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
