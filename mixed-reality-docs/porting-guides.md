---
title: 移植指南
description: 逐步解說說明如何將現有的沉浸式應用程式移植到 Windows Mixed Reality。
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: 埠、移植、unity、中介軟體、引擎、UWP、Win32
ms.openlocfilehash: a1e3cd47096d728091d62d6c038bf6b2eb6bab16
ms.sourcegitcommit: 0eb99fae933d4374af2c032af4e9ceda1807e532
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86156769"
---
# <a name="porting-guides"></a>移植指南

## <a name="overview"></a>概觀

Windows 10 包含沉浸式和全像攝影耳機的直接支援。 如果您已針對其他裝置（例如 Oculus go Rift 或 HTC Vive）建立內容，這些專案會相依于存在於作業系統平臺 API 的程式庫。 將現有內容帶入 Windows Mixed Reality 牽涉到將這些其他 Sdk 的使用重定至 Windows Api。 [適用于 mixed reality 的 Windows 平臺 api](https://docs.microsoft.com/uwp/api/Windows.Perception)可同時與 Win32 和通用 WINDOWS 平臺（UWP）應用程式模型搭配使用。 如果您的應用程式尚未針對 UWP 建立，則變更為 UWP 將會是移植體驗的一部分。

## <a name="porting-overview"></a>移植總覽

概括而言，移植現有的內容牽涉到下列步驟：
1. **確定您的電腦正在執行 Windows 10 秋季建立者更新（16299）。** 我們不再建議從內部跳躍略過的通道接收預覽組建，因為這些組建對混合現實開發而言並不是最穩定的。
2. **升級至圖形或遊戲引擎的最新版本。** 遊戲引擎必須支援 Windows 10 SDK 版本10.0.15063.0 （于2017年4月發行）或更高版本。
3. **升級任何中介軟體、外掛程式或元件。** 如果您的應用程式包含任何元件，最好先升級至最新版本。 較新版本的最常見外掛程式支援 UWP。
4. **移除重複 sdk 的**相依性。 根據您的內容設為目標的裝置，您必須移除或有條件地編譯該 SDK （例如，SteamVR），如此您才能改為以 Windows Api 為目標。
5. **解決組建問題。** 此時，移植練習僅適用于您的應用程式、您的引擎和您擁有的元件相依性。

## <a name="common-porting-steps"></a>一般移植步驟

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>一般步驟1：確定您有正確的開發硬體

[[安裝工具](install-the-tools.md#for-immersive-vr-headset-development)] 頁面會列出建議的開發硬體。

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>常見步驟2：升級至最新的 Windows 10 航班

Windows Mixed Reality 平臺仍在開發中。 我們建議您[加入 Windows 測試人員程式](https://insider.windows.com/)，以存取「Windows 測試人員快速」航班。
1. 安裝[Windows 10 建立者更新](https://www.microsoft.com/software-download/windows10)
2. [加入](https://insider.windows.com/)Windows 測試人員計畫。
3. 啟用[開發人員模式](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. 透過**設定 > 更新 & 安全性區段**，切換至[Windows 測試人員快速航班](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio-uwp-only"></a>一般步驟3：升級至最新的 Visual Studio 組建（僅限 UWP）
* 請參閱 Visual Studio 2019 底下[的 [安裝工具](install-the-tools.md#installation-checklist)] 頁面

### <a name="common-step-4-be-ready-for-the-store-uwp-only"></a>一般步驟4：準備好存放區（僅限 UWP）
* 儘早且經常使用[Windows 應用程式認證套件](https://developer.microsoft.com/windows/develop/app-certification-kit)（也稱為 WACK）！
* 使用可[移植性分析器](https://docs.microsoft.com/dotnet/standard/portability-analyzer)（[下載](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)）

### <a name="common-step-5-choose-the-correct-adapter"></a>一般步驟5：選擇正確的介面卡
* 在具有兩個 Gpu 的筆記本這類系統中，以[正確的介面卡為目標](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。 這適用于 Unity 和原生 DirectX 應用程式，其中會以明確或隱含的方式（媒體基礎）建立 ID3D11Device 以供其功能使用。

## <a name="unity-porting-guidance"></a>Unity 移植指引

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity 步驟1：遵循一般移植步驟

遵循所有的一般步驟。 在步驟 #3 中，選取 [**使用 Unity 進行遊戲開發**] 工作負載。 您可以取消選取 Unity Editor 選擇性元件，因為您將會從下列指示安裝較新版本的 Unity。

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity 步驟2：使用 Windows MR 支援升級至 Unity 的最新公開組建
1. 下載 Unity 的最新[建議公用組建](install-the-tools.md)與混合現實支援。
2. 在開始之前，請先儲存您的專案複本
3. 請參閱移植上的 Unity 所提供的[檔](https://docs.unity3d.com/Manual/UpgradeGuides.html)。
4. 遵循 Unity 網站上的[指示](https://docs.unity3d.com/Manual/APIUpdater.html)，使用其自動 API 更新程式
5. 檢查並查看是否有其他需要進行的變更，以便讓您的專案執行，並處理任何剩餘的錯誤和警告。 

> [!Note] 
> 如果您有相依的中介軟體，請檢查您使用的是最新版本（以下步驟3中的詳細資料）。

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity 步驟3：將您的中介軟體升級至最新版本

有了任何 Unity 更新，您很有可能需要更新您的遊戲或應用程式所依賴的一個或多個中介軟體套件。 此外，最新的中介軟體也會在移植程式的其餘部分中，增加成功的可能性。 許多中介軟體套件最近新增了對通用 Windows 平臺（UWP）的支援，而升級至最新版本可讓您運用該工作。

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity 步驟4：將您的應用程式目標設為在通用 Windows 平臺（UWP）上執行

如果您的目標是 Win32，可以略過此步驟並繼續執行步驟5。

安裝工具之後，您需要讓應用程式以通用 Windows 應用程式的身分執行。

* 依照 Unity 提供的[詳細逐步](https://unity3d.com/partners/microsoft/porting-guides)解說逐步解說。 您應該隨時掌握適用于 Windows MR 的最新 LTS 版本（任何 20xx. 4 版）。
* 如需更多 UWP 開發資源，請參閱《 [Windows 10 遊戲開發指南》](https://docs.microsoft.com/windows/uwp/gaming/e2e)。

> [!NOTE]
> Unity 繼續改善 IL2CPP 支援;IL2CPP 可讓某些 UWP 埠變得更容易。 如果您目前的目標是 .NET 腳本後端，您應該考慮轉換以改用 IL2CPP 後端。

* 您可以略過 "Unity step 5"，因為您是以 UWP 為目標，而不是 Win32。

> [!NOTE] 
> 如果您的應用程式與裝置特定的服務有任何相依性，例如從串流進行的比對，您必須在此步驟停用它們。 您可以連結到 Windows 稍後提供的對等服務。

### <a name="unity-step-5-target-your-application-to-run-on-win32"></a>Unity 步驟5：將您的應用程式設定為在 Win32 上執行

從您的 Unity 應用程式內：

* 流覽至檔案 > 組建設定
* 選取 [PC，Mac，Linux 獨立版]
* 將 [目標平臺] 設定為 [Windows]
* 將 [架構] 設定為 [x86] 選取 [切換平臺]


### <a name="unity-step-6-setup-your-windows-mixed-reality-hardware"></a>Unity 步驟6：設定您的 Windows Mixed Reality 硬體
1. 流覽[沉浸式耳機設定](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)中的步驟
2. 瞭解如何[使用 Windows Mixed reality](using-the-windows-mixed-reality-simulator.md)模擬器，以及如何[流覽 windows mixed reality 首頁](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity 步驟7：將您的應用程式設為目標以在 Windows Mixed Reality 上執行
1. 首先，您必須移除或有條件地編譯特定 VR SDK 特定的任何其他程式庫支援。 這些資產通常會以與其他 VR Sdk 不相容的方式來變更專案的設定和屬性，例如 Windows Mixed Reality。
    * 例如，如果您的專案參考 SteamVR SDK，則在匯出 Windows Store 組建目標時，您必須更新您的專案，以排除這些 prefabs 和腳本 API 呼叫。
    * 即將推出其他 VR Sdk 有條件地排除特定步驟。
2. 在您的 Unity 專案中，以[Windows 10 SDK 為目標](holograms-100.md#target-windows-10-sdk)
3. 針對每個場景，[設定相機](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity 步驟8：使用階段將內容放置在樓層上

您可以在各式各樣的[經驗調整](coordinate-systems.md)範圍內打造混合現實體驗。

如果您要移植**固定規模的經驗**，您必須確定 Unity 已設定為**固定**的追蹤空間類型：

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

上述程式碼會將 Unity 的全局座標系統設定為追蹤[固定的參考框架](coordinate-systems.md#spatial-coordinate-systems)。 在「固定」追蹤模式中，在應用程式啟動時，位於相機預設位置前方的內容（[轉寄] 為-Z）會出現在使用者的前方。 若要 recenter 使用者的固定來源，您可以呼叫 Unity 的[XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法。

如果您要移植的是**大規模體驗**或**會議室規模的體驗**，您將會放在與樓層相關的內容。 您的使用者使用**[空間階段](coordinate-systems.md#spatial-coordinate-systems)**（代表使用者定義的樓層層級原點和選擇性的房間界限），這是您在第一次執行期間設定的原因。 針對這些經驗，您必須確定 Unity 已設定為**RoomScale**追蹤空間類型。 雖然 RoomScale 是預設值，但您會想要明確設定並確保您得到 true，以攔截使用者已將其電腦從其校正的房間中移出的情況：

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

一旦您的應用程式成功設定 RoomScale 追蹤空間類型，放置在 y = 0 平面上的內容就會出現在樓層上。 位於（0，0，0）的原點會是在室內設定期間使用者勇敢面對考驗的特定位置，其中-Z 代表在安裝期間所面臨的正向方向。

在腳本程式碼中，您可以在上呼叫 TryGetGeometry 方法，以取得界限多邊形，並指定 TrackedArea 的界限類型。 如果使用者定義界限（您會取得頂點清單），則可安全地為使用者提供**會議室規模的體驗**，讓他們可以在其中四處流覽您建立的場景。

系統會在使用者進行方法時，自動呈現界限。 您的應用程式不需要使用此多邊形來呈現界限本身。

如需詳細資訊，請參閱在[Unity 中協調系統](coordinate-systems-in-unity.md)頁面。

有些應用程式會使用矩形來限制其互動。 UWP API 或 Unity 中不直接支援抓取最大的矩形。 以下連結的範例程式碼顯示如何在追蹤界限內尋找矩形。 它是以啟發學習法為基礎，因此可能找不到最佳的解決方案，不過結果會與預期一致。 演算法中的參數可以微調，以在處理時間的成本中尋找更精確的結果。 此演算法是使用 Unity 的 5.6 preview MRTP 版本之混合現實工具組的分叉。 這不是公開提供。 程式碼應該可以直接在2017.2 和更新版本的 Unity 中使用。 程式碼將會在不久的將來移植到目前的 MRTK。

[GitHub 上的程式碼 zip](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20)檔案重要檔案：
* 資產/HoloToolkit/階段/腳本/StageManager .cs-使用方式的範例
* 資產/HoloToolkit/階段/腳本/LargestRectangle .cs-演算法的執行
* 資產/HoloToolkit-Run-unittests/Editor/Stage/LargestRectangleTest-演算法的簡單測試

結果的範例：

![結果的範例](images/largestrectangle-400px.jpg)

演算法是以 Daniel Smilkov：[多邊形中的最大矩形](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)為基礎的 blog

### <a name="unity-step-9-work-through-your-input-model"></a>Unity 步驟9：逐步執行您的輸入模型

以現有 HMD 為目標的每個遊戲或應用程式將會有一組其處理的輸入、體驗所需的輸入類型，以及它所呼叫以取得這些輸入的特定 Api。 我們致力於嘗試讓它盡可能簡單明瞭，以利用 Windows Mixed Reality 提供的輸入。
1. 請仔細閱讀**[適用于 Unity 的輸入移植指南](input-porting-guide-for-unity.md)**，以取得有關 Windows Mixed Reality 如何公開輸入的詳細資訊，以及如何對應至您的應用程式目前所能執行的工作。
2. 選擇您要利用 Unity 的跨 VR-SDK 輸入 API，或 MR 特定的輸入 API。 Unity VR 應用程式現在會使用一般的 GetButton/GetAxis Api 來進行[oculus go 輸入](https://docs.unity3d.com/Manual/OculusControllers.html)和[OpenVR 輸入](https://docs.unity3d.com/Manual/OpenVRControllers.html)。 如果您的應用程式已經使用這些適用于動作控制器的 Api，這是最簡單的路徑，您應該只需要在輸入管理員中重新對應按鈕和軸。
    * 您可以使用一般的跨 VR-SDK 輸入來存取 Unity 中的動作控制器資料。 GetButton/GetAxis Api 或 MR 專屬的 UnityEngine. XR。輸入 Api。 （之前在 Unity 5.6 中的 UnityEngine. XR 命名空間）
    * 請參閱結合遊戲台和動作控制器的[工具組中的範例](https://github.com/Microsoft/HoloToolkit-Unity/pull/572)。

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity 步驟10：效能測試和微調

Windows Mixed Reality 會在廣泛的裝置上提供，範圍從高階遊戲電腦到廣泛的市場主流電腦。 根據您的目標市場，您的應用程式可用的計算和圖形預算會有顯著的差異。 在此移植練習中，您很可能會利用高階電腦，而且您的應用程式可以使用大量的計算和圖形預算。 如果您想要讓您的應用程式可供更多物件使用，您應該在[想要作為目標的代表性硬體](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)上測試和分析應用程式。

[Unity](https://docs.unity3d.com/Manual/Profiler.html)和[Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index)都包含效能分析工具，以及[Microsoft](understanding-performance-for-mixed-reality.md)和[Intel](https://software.intel.com/articles/vr-content-developer-guide)都發佈有關效能分析和優化的指導方針。 在[瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)方面，有廣泛的效能討論。 此外，unity 的[效能建議](performance-recommendations-for-unity.md)下還有 unity 的特定詳細資料。

## <a name="see-also"></a>另請參閱
* [Unity 的輸入移植指南](input-porting-guide-for-unity.md)
* [Windows Mixed Reality 最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)
* [Unity 的效能建議](performance-recommendations-for-unity.md)
* [將 Xbox Live 支援新增至適用于 UWP 的 Unity](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
