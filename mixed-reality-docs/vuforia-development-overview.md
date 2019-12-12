---
title: 搭配使用 Vuforia 與 Unity
description: 利用 Vuforia 在 Unity 中建立 Windows Mixed Reality 應用程式。
author: thetuvix
ms.author: alexturn
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia、標記、座標、參考框架、追蹤
ms.openlocfilehash: bae5d0eb04ab9434dd3e72674686743779a8f70c
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003187"
---
# <a name="using-vuforia-engine-with-unity"></a>搭配使用 Vuforia 引擎與 Unity

Vuforia Engine 為 HoloLens 提供了一項重要的功能–將 AR 體驗連線到環境中特定映射和物件的能力。 您可以使用這項功能，在產業企業的機械上重迭引導式逐步指示，或為實體產品或遊戲新增數位功能和體驗。

為了在開發 AR 體驗時擁有更大的彈性，Vuforia 引擎提供各種功能和目標。 其中一個最新的功能是 Vuforia 模型目標，這是商業和產業用途的主要功能。 模型目標可讓應用程式辨識實體物件（例如機器、汽車或玩具），並根據 CAD 或數位3D 模型加以追蹤。 對於產業用途，這項功能可以在工廠或在現場推出時，為元件工作者和服務技術人員提供 AR 工作指示和程式指引。

針對手機和平板電腦建立的現有 Vuforia 引擎應用程式，可以輕鬆地在 Unity 中設定以在 HoloLens 上執行。 您甚至可以使用 Vuforia 引擎將新的 HoloLens 應用程式帶到 Windows 10 平板電腦上，例如 Surface Pro 和 Surface Book。


## <a name="get-the-tools"></a>取得工具

[安裝建議](install-the-tools.md)的 Visual Studio 和 unity 版本，然後將 unity 設定為使用 Visual Studio 和慣用的 IDE 和編譯器。 

安裝 Unity 時，請務必安裝「Windows Store IL2CPP 腳本後端」。

根據您的 Unity 版本而定，新增 Vuforia 引擎支援的運作方式會有所不同：
*   Unity 2018.4：從 Vuforia 開發人員入口網站下載適用于 Unity 2018.4 的 Vuforia Engine 安裝程式
*   Unity 2019.2：取得最新的[Vuforia 引擎封裝](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html) 

## <a name="getting-started-with-vuforia-engine"></a>開始使用 Vuforia Engine

學習使用 Vuforia Engine 搭配 HoloLens 的最佳起點是使用[Vuforia Engine HoloLens 範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)（可在 Unity 資產存放區中取得）。 此範例會提供完整的 HoloLens 專案，包括可部署至 HoloLens 的預先設定場景。

幕後會示範如何使用 Vuforia 的影像目標來辨識影像，並使用 HoloLens 體驗中的數位內容來增加它。 Vuforia Engine Hololens 範例也包含一個場景，其中顯示在 HoloLens 上使用模型目標和 VuMarks 的情況。 您可以輕鬆地在幕後替換自己的內容，以實驗如何建立使用 Vuforia 引擎的 HoloLens 應用程式。



## <a name="configuring-a-vuforia-app-for-hololens"></a>設定適用于 HoloLens 的 Vuforia 應用程式

開發適用于 HoloLens 的 Vuforia 引擎應用程式基本上與開發其他裝置的 Vuforia 引擎應用程式相同。 接著，您可以套用下列區段中所述的組建設定和設定。 這就是讓 Vuforia 引擎使用 HoloLens 空間對應和位置追蹤系統所需的一切。

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>建立並執行 HoloLens 的 Vuforia 引擎範例
1.  從 Unity 資產存放區下載[適用于 HoloLens 的 Vuforia 引擎範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)
2.  套用適用于[電源和效能的建議 Unity 引擎選項](performance-recommendations-for-unity.md)
3.  將範例場景新增至組建中的場景。
4.  在 [檔案 > 組建設定] 中，設定 "通用 Windows 平臺" 的平臺組建目標。
5.  選取下列平臺組建設定： 
   * 目標裝置 = HoloLens
   * 組建類型 = D3D
   * SDK = 已安裝最新版本
   * Visual Studio 版本 = 最新安裝
   * 組建並在 = 本機電腦上執行
6.  在 [**播放程式設定**] 中定義唯一的**產品名稱**，以在安裝于 HoloLens 時做為應用程式的名稱。
7.  查看**Vuforia**增強的現實和**播放 > XR 設定**中**支援的虛擬實境**
8.  此外，在 [ **XR 設定**] 下，確定 [Windows Mixed Reality] 已新增至**虛擬實境 sdk**清單
9.  檢查播放 [設定] 中的下列功能 > 發佈設定 
   * InternetClient
   * 網路
   * SpatialPerception-如果您想要使用 Surface Observer API
10. 選取 [組建] 以產生 Visual Studio 專案
11. 從 Visual Studio 建立可執行檔，並將它安裝在 HoloLens 上

注意：從版本7.2 開始，HoloLens 的 Vuforia 引擎範例包含範例場景，包括模型目標的範例用法

## <a name="the-vuforia-developer-portal"></a>Vuforia 開發人員入口網站

想要使用 Vuforia 引擎和 HoloLens 建立自己的 AR 經驗的開發人員，應該在 Vuforia 開發人員入口網站的[developer.vuforia.com](https://developer.vuforia.com/)註冊。 在入口網站中，開發人員可以存取[Vuforia Engine 論壇](https://developer.vuforia.com/forum)，他們可在其中加入社區討論、具有所有 Vuforia 引擎功能之深入檔的文檔[庫](https://library.vuforia.com/)，以及[Vuforia 目標管理員](https://developer.vuforia.com/target-manager)，讓使用者可以在其中建立自己的自訂目標。 開發人員也可以使用[Vuforia 授權管理員](https://developer.vuforia.com/license-manager)註冊免費的開發人員授權。

## <a name="extended-tracking-with-vuforia"></a>使用 Vuforia 擴充追蹤

即使目標已經不在查看中，[延伸追蹤](https://library.vuforia.com/articles/Training/Extended-Tracking)還是會維持追蹤。 當位置裝置追蹤器啟用時，會自動為所有目標啟用此功能。 若是 HoloLens 應用程式，位置裝置追蹤器會在 Unity 中自動啟動。

Vuforia 引擎會自動 e-fuses 相機追蹤和 HoloLens 的空間追蹤的姿勢，以提供穩定的目標，而不受相機是否看過目標。

因為程式會自動處理，所以開發人員不需要任何程式設計。


**以下是發生的情況 ...**
1. Vuforia 的目標追蹤器可識別目標
2. 接著會初始化目標追蹤
3. 系統會分析目標的位置和旋轉，為 HoloLens 提供健全的姿勢估計
4. Vuforia 引擎會將目標的姿勢轉換成 HoloLens 空間對應座標空間
5. 如果目標不再是 view，HoloLens 會接管追蹤。 當您再次查看目標時，Vuforia 將會繼續正確地追蹤影像和物件。

系統會將偵測到但不再處於 view 的目標，回報為 EXTENDED_TRACKED。 在這些情況下，用於所有目標的 DefaultTrackableEventHandler 腳本會繼續轉譯擴充內容。 開發人員可以藉由執行自訂的可追蹤事件處理常式腳本來控制此行為。


## <a name="performance-mode-with-vuforia-engine"></a>具有 Vuforia 引擎的效能模式 

您可以透過 Vuforia 引擎來管理 HoloLens 的效能，以達到 AR 的範圍，並降低 CPU 上的工作負載。 Vuforia 引擎提供三種可選取的模式：預設、用於優化速度，以及優化品質。 

*   MODE_OPTIMIZE_SPEED 可讓您將 HoloLens 裝置上的工作負載最小化，而且很適合用來擴充 AR 的體驗。 在應用程式正在追蹤靜態物件/目標的情況下，建議使用此選項。
*   MODE_DEFAULT 是正常模式，可用於大部分的案例中。
*   MODE_OPTIMIZE_QUALITY 更適合用來追蹤您預期會挑選的可移動目標或模型目標。

**設定模式**

若要變更 Unity 中的效能模式，請流覽至 [Vuforia 設定] （Ctrl + Shift + V/Cmd + Shift + V），其位於 ARCamera GameObject 中的元件。 
*   選取 [相機裝置模式] 的下拉式功能表，然後選取三個選項的其中一個。


## <a name="see-also"></a>請參閱
* [Instalación de las herramientas](install-the-tools.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Asignación espacial](spatial-mapping.md)
* [Cámara en Unity](camera-in-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 檔：在 Unity 中針對 Windows 10 進行開發](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia 檔：如何安裝 Vuforia Unity 延伸模組](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia 檔：使用 Unity 中的 HoloLens 範例](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia 檔： Vuforia 中的延伸追蹤](https://library.vuforia.com/articles/Training/Extended-Tracking)
