---
title: 讓應用程式做好使用 HoloLens 2 的準備
description: 適用對象為擁有可在 HoloLens (第 1 代) 及/或較舊 MRTK 上運作的現有應用程式，並想要移植到 MRTK 第 2 版和 HoloLens 2 的開發人員。
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 測試, MRTK, MRTK 第 2 版, HoloLens 2
ms.openlocfilehash: 02dabd21b7a6add2ce53fe291a447e49057184d0
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270389"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>讓現有應用程式做好使用 HoloLens 2 的準備

本指南專門打造來協助開發人員，讓其將適用於 HoloLens (第 1 代) 的現有 Unity 應用程式，移植給新的 HoloLens 2 裝置使用。 將 HoloLens (第 1 代) Unity 應用程式移植到 HoloLens 2 的作業有四個重要步驟。 下列各節會詳細說明每個階段的資訊。 

| 步驟 1 | 步驟 2 | 步驟 3 | 步驟 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio 標誌](images/visualstudio_logo.png) | ![Unity 標誌](images/unity_logo.png)| ![Unity 圖示](images/hololens2_icon.jpg) | ![MRTK 標誌](images/MRTKIcon.jpg) |
| 下載最新工具 | 更新 Unity 專案 | 針對 ARM 進行編譯 | 遷移至 MRTK v2

**強烈建議**開發人員在開始移植程序之前，先利用原始檔控制來儲存其應用程式原始狀態的快照。 此外，也建議開發人員在移植程序進行期間於各個時間點「儲存」  檢查點狀態。 為原始應用程式準備另一個 Unity 執行個體以便能在移植程序進行期間兩相比較，也會非常有幫助。 

> [!NOTE]
> 在移植之前，請確定您已安裝可用於開發 Windows Mixed Reality 的最新工具。 對大部分現有的 HoloLens 開發人員來說，這主要涉及更新至最新的 Visual Studio 2017，以及安裝適當的 Windows SDK。 以下內容將進一步說明不同的 Unity 版本和混合實境工具組第 2 版。
>
> 如需詳細資訊，請參閱[安裝工具](install-the-tools.md)。

## <a name="migrate-project-to-latest-version-of-unity"></a>將專案遷移至最新版的 Unity

如果使用 MRTK v2，則 Unity 2018 LTS 會是最佳的長期支援途徑，因為 Unity 或 MRTK 沒有重大變更。  根據上面的「安裝工具」，建議的 Unity 組建是 Unity 2018.3，這會成為 Unity 2018 的 LTS 版本。  此外，MRTK v2 一律保證會支援 Unity 2018 LTS，但不一定保證支援 Unity 2019.x 的每個新版本。 

為了協助釐清 Unity 2018.3.x 或 Unity 2019.1.x 之間的其他差異，下面會概述這兩個版本之間的利弊得失，其中的主要差異是能夠在 Unity 2019 中針對 ARM64 進行編譯。 

開發人員應該評估任何目前存在於其專案中的[外掛程式相依性](https://docs.unity3d.com/Manual/Plugins.html)，和是否可以針對 ARM64 建置這些 DLL。 如果無法針對 ARM64 建置硬式相依性外掛程式，則必須利用 Unity 2018 LTS。


| Unity 2018.3.x | Unity 2019.1+ |
|----------|-------------------|
| ARM32 組建支援 | ARM32 和 ARM64 組建支援 |
| 穩定的 LTS 組建發行 | Beta 穩定性 |
| [.NET 指令碼處理後端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *已過時* | [.NET 指令碼處理後端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *已移除* |
| UNET 網路 *已過時* | UNET 網路 *已移除* |

## <a name="update-sceneproject-settings-in-unity"></a>更新 Unity 中的場景/專案設定

在更新至 Unity 2018.3.x 或 Unity 2019+ 之後，建議您更新 Unity 中的特殊設定，以便在裝置上獲得最佳結果。 **[Unity 的建議設定](Recommended-settings-for-Unity.md)** 底下會詳述這些設定。

重申一遍，[.NET 指令碼處理後端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)在 Unity 2018 已過時，且在 Unity 2019 中「已移除」  ，因此開發人員應積極考慮將其專案切換至 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。 

> [!NOTE]
> IL2CPP 指令碼處理後端會讓從 Unity 到 Visual Studio 的建置時間變長，因此請開發人員設定其開發人員機器以便[最佳化 IL2CPP 建置時間](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)。
> 此外，設定[快取伺服器](https://docs.unity3d.com/Manual/CacheServer.html)可能會有幫助，對於有大量資產 (排除指令檔) 或不斷變更場景/資產的 Unity 專案來說，更是如此。 開啟專案時，Unity 會將符合資格的資產以內部快取格式儲存在開發機器上。 項目必須重新匯入，因此修改時必須加以重新處理。 此程序可以執行一次後就儲存在快取伺服器中，之後再與其他開發人員共用以節省時間，而不是每位開發人員都在本機處理新變更的重新匯入工作。

移至已更新的 Unity 版本之後若有解決任何重大變更，開發人員就應該在 HoloLens (第 1 代) 上建置並測試其目前的應用程式。 此外，這也是為原始檔控制建立並儲存認可的好時機。 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>針對 ARM 處理器編譯相依性/外掛程式

HoloLens (第 1 代) 會在 x86 處理器上執行應用程式，新的 HoloLens 2 裝置則會利用 ARM 處理器。 因此，現有應用程式必須移植過去才能支援 ARM。 如先前所述，Unity 2018 支援針對 ARM32 應用程式進行編譯，而 Unity 2019+ 則支援針對 ARM64 應用程式進行編譯。 一般會比較喜歡針對 ARM64 應用程式進行開發，因為效能差異極大。 但要這麼做，所有的[外掛程式相依性](https://docs.unity3d.com/Manual/Plugins.html)也必須針對 ARM64 來建置。 

請檢閱您應用程式中目前的所有 DLL 相依性。 如果不再需要某個相依性，建議您將其從專案中移除。 至於其餘的必要外掛程式，則請將個別的 ARM32 或 ARM64 二進位檔案嵌入至您的 Unity 專案中。 

嵌入相關的 DLL 之後，請從 Unity 建置 Visual Studio 解決方案，然後在 Visual Studio 中針對 ARM 來編譯 AppX，以測試是否可以針對 ARM 處理器來建置您的應用程式。 這是另一個建議您在原始檔控制解決方案中儲存認可的時間點。 

## <a name="update-to-mrtk-version-2"></a>更新至 MRTK 第 2 版

MRTK 第 2 版是新的工具組，作為其建置依據的 Unity 可同時支援 HoloLens (第 1 代) 和 HoloLens 2，且其中已新增所有新的 HoloLens 2 功能，例如手部互動和眼球追蹤。

### <a name="prepare-for-the-migration"></a>準備移轉

在嵌入新的 [*.unitypackage 檔案 (適用於 MRTK v2)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) 之前，建議您清查 **1) 與 MRTK v1 整合的任何自訂建置程式碼**和 **2) 用於輸入互動或 UX 元件的任何自訂建置程式碼**。 內嵌新 MRTK v2 的 Mixed Reality 開發人員會在輸入和互動方面產生最常見也最普遍的衝突。 因此，建議您開始閱讀和了解 [MRTK v2 輸入模型](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)。

終於，新的 MRTK v2 已從指令碼和場景中管理員物件的模型轉換為設定和服務提供者架構。 這會讓場景階層和架構模型更為簡潔，但需要花一段時間學習才能了解新的組態設定檔。 因此，請閱讀[混合實境工具組設定指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)來開始熟悉重要設定和設定檔，以調整為符合應用程式的需求。 

### <a name="perform-the-migration"></a>執行移轉

匯入 MRTK v2 之後，Unity 專案可能會有許多編譯器相關錯誤。 會有這些錯誤通常是因為使用了新的命名空間結構和新的元件名稱。 請繼續藉由將指令碼修改為新的命名空間和元件，來解決這些錯誤。 

如需 HTK/MRTK 和 MRTK 第 2 版之間特定 API 差異的詳細資訊，請參閱 [MRTK 第 2 版 Wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html) 上的移植指南。

### <a name="best-practices"></a>最佳作法

- 最好使用 MRTK 標準著色器
- 一次處理一個重大變更類型 (例如：IFocusable 至 IMixedRealityFocusHandler)
- 每次變更後進行測試，並利用原始檔控制
- 盡可能使用預設的 MRTK UX (按鈕、靜態圖像等)
- 試著避免直接修改 MRTK 檔案，改為圍繞 MRTK 元件來建立包裝函式
    - 這可避免日後需要內嵌和更新 MRTK
- 檢閱和探索 MRTK 中所提供的場景範例 (尤其是 HandInteractionExamples.scene  )
- 改為重建有四色、碰撞器和 TextMeshPro 文字的畫布式 UI

### <a name="testing-your-application"></a>測試應用程式

既然 MRTK 第 2 版 (自 [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1) 起) 中已經有提供 HoloLens 2 元件與功能，您可以直接在 Unity 中模擬手部互動，並針對新的 API 來開發手部互動和眼球追蹤。  需要有 HoloLens 2 裝置才能建立絕佳體驗，但您至少可以先在工具和文件中開始學習。 此外，MRTK v2 支援在 HoloLens (第 1 代) 上進行開發，因此傳統的輸入模型 (例如，透過空中點選來進行選取) 仍可在 HoloLens (第 1 代) 裝置上進行測試。 

## <a name="updating-interaction-model-for-hololens-2"></a>更新 HoloLens 2 的互動模型

移植應用程式並讓其做好使用 HoloLens 2 的準備之後，您就可以開始考慮更新互動模型和全像投影設計/位置。
您的應用程式來自 HoloLens (第 1 代)，因此可能有注視和認可互動模型，而讓全像投影遠遠無法融入視野。

下列步驟可更新您應用程式的設計而使其完美適合 HoloLens 2：
1.  MRTK 元件：根據事前工作，如果您已新增 MRTK v2，則其中會有各種已針對 HoloLens 2 來設計及最佳化的元件/指令碼可供運用。

2.  互動模型：請考慮更新互動模型。  大部分情況下，建議您從注視和認可切換至手部。  一般來說，全像投影會在比手臂可及範圍還遠的地方，因此切換為手部會讓互動指標光線和抓取手勢變遠。
注意：在某些情況下，必須要有不用手部操作的互動模型 (例如，手裡握著工具的任務工作人員)，因此會有這類情況的具體設計指導方針。 

3.  全像投影位置：切換到手部互動模型之後，請考慮使用近距離互動抓取手勢將某些全像投影移得近一些，以便讓手部直接與全像投影互動。  建議可移得近一些以便能直接抓取或互動的全像投影類型包括，可在抓取和檢查全像投影時融入到 HoloLens 2 視野內的小型目標功能表、控制項、按鈕和較小型的全像投影。
<br>
每個應用程式和情境各不相同，所以我們會持續地根據意見反應和不斷地學習來改善和發佈設計指導方針。


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>將應用程式從 x86 移至 ARM 所獲得的其他經驗

- 簡截了當的 Unity 應用程式很簡單，因為您可以建置 ARM AppX 套件組合或直接部署至裝置中，然後便可執行。
但如果 Unity 應用程式使用原生外掛程式，挑戰便會接踵而來。  所有原生外掛程式都必須升級至 VS2017 並針對 ARM 重新建置，若使用 Unity 2019，則必須針對 ARM64 重新建置。

- 若應用程式使用適用於 Unity 的 AudioKinetic Wwise 外掛程式，且使用的版本沒有 UWP ARM 外掛程式。 該應用程式就需要用上好幾天的時間來重新處理應用程式中的音效，才能在 ARM 上運作。

- 在其他情況下，應用程式所需的外掛程式可能沒有 UWP/ARM 外掛程式，因此無法移植到 HoloLens 2 並於上面執行。  您可能需要與外掛程式提供者接洽，才能解除障礙並支援 ARM。

- 著色器中的 minfloat (和 min16float、minint 等變化) 在 HoloLen 2 上和在 HoloLens (第 1 代) 上的行為可能會不一樣。 具體來說，這些數字會保證「至少會使用指定的位元數」。 Intel/Nvidia GPU 多半會將這些數字當做 32 位元來處理。 ARM 則會實際採用所指定的位元數。 這表示實際上這些數字在 HoloLens 2 上的精確度/範圍，可能會比在 HoloLens (第 1 代) 上來得少。

- _asm 指令似乎無法在 ARM 上運作，這表示任何使用 _asm 指令的程式碼將必須重寫。

- ARM 不支援 SIMD 指令集。 這表示在 ARM 上無法使用 xmmintrin.h、emmintrin.h、tmmintrin.h 和 immintrin.h 等各種標頭。

- ARM 上的著色器編譯器會在第一次繪製呼叫期間，於著色器已載入或著色器所相依的某個項目有所變更後執行，而不是在著色器載入時執行。 視需要編譯的著色器數目多寡而定，畫面播放速率所受到的影響可能會非常明顯。 對於在 HoloLens 2 和 HoloLens (第 1 代) 上應該如何以不同方式處理/封裝/更新著色器，這一點會產生不同的影響。

## <a name="see-also"></a>請參閱
* [開始使用 MRTK 第 2 版](mrtk-getting-started.md)
* [MRTK 第 2 版操作說明](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [安裝工具](install-the-tools.md)
* [Unity 的建議設定](recommended-settings-for-unity.md)
* [了解混合實境的效能](understanding-performance-for-mixed-reality.md)

