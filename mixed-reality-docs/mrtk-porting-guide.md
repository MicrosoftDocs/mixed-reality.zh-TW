---
title: HoloLens 2 準備您的應用程式
description: HoloLens 有現有的應用程式開發人員適用對象 （第 1 代） 及/或較舊 MRTK，並想要 MRTK 第 2 版 」 和 「 HoloLens 2 的連接埠。
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality，MRTK MRTK 第 2 版、 HoloLens 2 測試
ms.openlocfilehash: 98fde1a597bcc20b14037176748258d35ef99ab9
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730871"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>HoloLens 2 準備您現有的應用程式

本指南專為協助開發人員的 HoloLens 有現有的 Unity 應用程式 （第 1 代） 移植他們的應用程式，在新的 HoloLens 2 裝置。 有四個重要的步驟，移植 HoloLens （第 1 代） 為 HoloLens 2 的 Unity 應用程式。 下列各節將詳細說明每個階段的資訊。 

| 步驟 1 | 步驟 2 | 步驟 3 | 步驟 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio 標誌](images/visualstudio_logo.png) | ![Unity 標誌](images/unity_logo.png)| ![Unity 圖示](images/hololens2_icon.jpg) | ![MRTK 標誌](images/MRTKIcon.jpg) |
| 下載最新的工具 | 更新 Unity 專案 | 適用於 ARM 編譯 | 移轉至 MRTK v2

很**強烈建議**，再開始移轉程序，開發人員利用原始檔控制來儲存其應用程式的原始狀態的快照。 此外，建議您使用*儲存*程序期間的各個點上的檢查點狀態。 它也可以是非常有幫助另一個連接埠程序期間，以便並排顯示比較原始的應用程式的 Unity 執行個體。 

> [!NOTE]
> 移植前，請確定您已安裝適用於 Windows Mixed Reality 開發最新工具。 對於大部分現有的 HoloLens 開發人員，這主要是涉及更新至最新的 Visual Studio 2017，並安裝適當的 Windows SDK。 以下內容將深入了解進一步不同 Unity 版本及混合實境工具組第 2 版。
>
> 如需詳細資訊，請參閱[安裝工具](install-the-tools.md)。

## <a name="migrate-project-to-latest-version-of-unity"></a>將專案移轉至最新版本的 Unity

如果使用 MRTK v2，Unity 2018 LTS 會是最佳的長期支援路徑與 Unity 或 MRTK 中沒有重大變更。  建議的 Unity 組建中每個上述 「 安裝工具 」 是 Unity 2018.3，這會成為 Unity 2018 的 LTS 版本。  此外，MRTK v2 將一律保證 Unity 2018 LTS 支援，但不是一定保證支援 Unity 的每個反覆項目 2019.x。 

若要協助釐清其他差異 Unity 2018.3.x 或 Unity 2019.1.x，兩者的精確度所能夠編譯適用於 ARM64 Unity 2019 中的主要差異的外框取捨之間下列兩個版本，如下。 

開發人員應該評估任何[外掛程式相依性](https://docs.unity3d.com/Manual/Plugins.html)目前存在於其專案和這些 Dll 是否可以建置適用於 ARM64。 如果無法建立硬式相依性外掛程式適用於 ARM64，則一個必須利用 Unity 2018 LTS。


| Unity 2018.3.x | Unity 2019.1 + |
|----------|-------------------|
| ARM32 組建支援 | ARM32 及 ARM64 建置支援 |
| 穩定的 LTS 建立發行 | Beta 穩定性 |
| [編寫.NET 指令碼的後端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)*已被取代* | [編寫.NET 指令碼的後端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)*移除* |
| UNET 網路*已被取代* | UNET 網路*移除* |

## <a name="update-sceneproject-settings-in-unity"></a>更新 Unity 中的場景/專案設定

更新至 Unity 之後 2018.3.x 或 Unity 2019 +，建議您更新在 Unity 中為裝置上獲得最佳結果的特定設定。 這些設定所述在詳細資料 **[for Unity 建議設定](Recommended-settings-for-Unity.md)**。

它應該是重新反覆執行的[.NET 指令碼的後端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)遭到非難 Unity 2018 和*移除*中 Unity 2019，因此開發人員應該慎重考慮其專案切換至[IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。 

> [!NOTE]
> IL2CPP 指令碼的後端可能會造成更長的建置時間從 Unity Visual studio，因此開發人員應該會設定為其開發人員電腦[最佳化 IL2CPP 建置時間](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)。

移至已更新的 Unity 版本之後解決任何重大變更之後，開發人員應該建置並測試 HoloLens 上其目前的應用程式 （第 1 代）。 此外，這是建立並儲存原始檔控制認可的好時機。 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>編譯為 ARM 處理器的相依性/外掛程式

HoloLens （第 1 代） x86 上執行應用程式時為新的 HoloLens 2 裝置利用 ARM 處理器的處理器。 因此，現有的應用程式需要支援 ARM 直接移植。 如先前所述，Unity 2018 支援 Unity 2019 + 支援 ARM64 應用程式編譯時，針對 ARM32 應用程式進行編譯。 ARM64 應用程式開發是通常慣用，因為效能的材質差異。 不過，這需要所有[外掛程式相依性](https://docs.unity3d.com/Manual/Plugins.html)也要建置適用於 ARM64。 

目前，請檢閱您的應用程式中的所有 DLL 相依性。 如果不再需要的相依性，則建議您從專案中移除。 其餘所需的外掛程式，嵌入您的 Unity 專案中的個別 ARM32 或 ARM64 二進位碼檔案。 

之後擷取相關的 Dll，從 Unity 建置 Visual Studio 方案，並再編譯來測試可以針對 ARM 處理器建置您的應用程式的 Visual Studio 中的 ARM 的 AppX。 它會建議儲存在您的原始檔控制解決方案中的認可此另一個點。 

## <a name="update-to-mrtk-version-2"></a>更新至 MRTK 第 2 版

MRTK 第 2 版是新的工具組，在 Unity 支援這兩個 HoloLens 之上 （第 1 代） 和 HoloLens 2 和其中的所有新的 HoloLens 2 功能已新增，這類交給互動和追蹤。

### <a name="prepare-for-the-migration"></a>為移轉做準備

之前擷取的新[*.unitypackage 檔案 MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)，建議您使用清查**MRTK v1 與整合，1） 任何自訂程式碼**和**2） 任何自訂程式碼輸入的互動或 UX 元件**。 最常見也太普遍了衝突的內嵌新 MRTK v2 Mixed Reality 開發人員會需要輸入和互動。 因此，建議您開始閱讀和理解[MRTK v2 輸入的模型](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)。

最後，新的 MRTK v2 已從模型的指令碼和管理員場景中物件轉換為組態和服務提供者架構。 這會導致更簡潔的場景階層和架構模型，但了解新的組態設定檔需要依照學習曲線。 因此，請閱讀[混合實境工具組組態指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)開始著手了解的重要設定和設定檔，以您的應用程式的需求進行調整。 

### <a name="perform-the-migration"></a>執行移轉

匯入之後 MRTK v2，您的 Unity 專案可能會有許多編譯器相關的錯誤。 這些通常是因為新的命名空間的結構與新的元件名稱。 請繼續進行修改您的指令碼至新的命名空間和元件來解決這些錯誤。 

如需有關特定 HTK/MRTK 之間 MRTK 第 2 版的 API 差異的詳細資訊，請參閱 < 移植指南上[MRTK 第 2 版 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)。

### <a name="best-practices"></a>最佳作法

- 偏好使用 MRTK 標準的著色器
- 上一個重大的工作一次變更型別 (例如：若要 IMixedRealityFocusHandler IFocusable)
- 測試每次變更之後，並利用原始檔控制
- 使用預設值 （按鈕、 靜態圖像等等） 的 MRTK UX 盡可能
- 若要避免直接修改 MRTK 檔案嘗試，請改為建立 MRTK 元件包裝函式
    - 這會防止未來 MRTK ingestions 和更新
- 檢閱和探索 MRTK 中提供的範例場景 (特別*HandInteractionExamples.scene*)
- 相反地重建四邊形、 colliders 與 TextMeshPro 文字畫布為基礎的 UI

### <a name="testing-your-application"></a>測試您的應用程式

既然 HoloLens 2 元件與功能有 MRTK 第 2 版的[RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1)，您可以模擬手動互動，直接在 Unity 中，並根據手動互動和追蹤的新 Api 進行開發。  HoloLens 2 裝置，才能建立絕佳的體驗，但至少一個無法開始學習的工具和文件。 此外，MRTK v2 支援在 HoloLens 上的開發 （第 1 代） 和傳統的輸入因此，模型例如透過空中點選選取的類型仍 HoloLens 上測試工作流程 （第 1 代） 裝置。 

## <a name="updating-interaction-model-for-hololens-2"></a>HoloLens 2 更新互動模型

您的應用程式移植，並備妥可供 HoloLens 2 之後，您已準備好，請考慮更新您的互動模型和全像設計/放置。
來自 HoloLens （第 1 代），您的應用程式可能有視線和認可互動模型，以全像投影相對很遠的地方而無法放入檢視欄位。

若要更新您的應用程式的設計最適合 HoloLens 2 的步驟：
1.  MRTK 元件：每個前的工作，如果您已新增 MRTK v2 中，有各種元件/的指令碼運用設計及最佳化 HoloLens 2。

2.  互動模型：請考慮更新您的互動模型。  大部分的情況下，我們建議從視線切換，並認可至實際操作。  使用全像通常要從手臂觸達您投影，切換到實際操作將導致遠互動指標光線並抓取筆勢。
注意： 在無互動模型是必要項目，例如任務型工作者保存工具，並沒有特定設計指導方針，這種情況下。 

3.  全像位置：之後切換到實際操作互動模型，請考慮直接互動與您的手裡，互動抓取筆勢附近使用全像投影更接近移動某些全像投影。  建議您移近一點來直接擷取或互動全像投影的類型是小型的目標功能表、 控制項、 按鈕和較小全像保留可容納在 HoloLens 2 檢視欄位時擷取並檢查全像投影。
<br>
每個應用程式和案例不同，而我們將持續改善，並張貼設計指引根據意見反應，並繼續所獲得的經驗。


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>其他學習，無法從 x86 的應用程式移至 ARM

- 直線的 Unity 應用程式很簡單，因為您可以建立的 ARM appx 套件組合，或直接部署至裝置，並執行。
所面臨的挑戰來自 Unity 應用程式中使用原生的外掛程式。  所有的原生的外掛程式必須升級至 VS2017 及重新建置針對 ARM，並使用 Unity 2019，ARM64。

- 一個應用程式，使用 Unity AudioKinetic Wwise 外掛程式，並使用的版本沒有 UWP ARM 外掛程式。 花費數天的重新處理要在 ARM 上運作的應用程式中的音效。

- 在其他情況下，UWP/ARM 外掛程式可能不存在的應用程式所需的外掛程式，封鎖連接埠和 HoloLens 2 上執行的能力。  Engagement 使用外掛程式提供者可能需要解除封鎖，並支援 ARM。

- Minfloat （和變數，例如 min16float、 minint、 等），在著色器的行為可能會比在 HoloLens 的 HoloLen 2 （第 1 代）。 具體來說，這些保證 「 至少指定將使用的位元數 」。 在 Intel/Nvidia Gpu 上這些多半只被被當做 32 位元。 在 ARM，實際上會遵守所指定的位元數。 這表示，在實務上，這些數字可能會有較少有效位數/範圍 HoloLens 2 比起原先 HoloLens （第 1 代）。

- _Asm 指示不會出現在 ARM 中，這表示任何使用 _asm 指示程式碼將會需要重寫上運作。

- 在 ARM 上不支援 SIMD 指令集。 這表示各種的標頭，例如 xmmintrin.h、 emmintrin.h、 tmmintrin.h 和 immintrin.h> 並不適用於 ARM。

- 在 ARM 執行期間第一次的繪製呼叫之後已載入著色器，或項目著色器依賴著色器編譯器已變更，不是在著色器載入時間。 對畫面播放速率的影響可以是非常值得注意，視需要進行編譯多少的著色器而定。 這有各種不同的含意的著色器應如何處理/封裝/更新以不同的方式在 HoloLens 2 vs HoloLens 上 （第 1 代）。

## <a name="see-also"></a>另請參閱
* [開始使用 MRTK 第 2 版](mrtk-getting-started.md)
* [MRTK 第 2 版如何](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [安裝工具](install-the-tools.md)
* [Unity 的建議設定](recommended-settings-for-unity.md)
* [了解效能 for Mixed Reality](understanding-performance-for-mixed-reality.md)

