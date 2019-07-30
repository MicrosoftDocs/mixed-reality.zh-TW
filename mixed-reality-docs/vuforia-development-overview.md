---
title: 搭配使用 Vuforia 與 Unity
description: 利用 Vuforia 在 Unity 中建立 Windows Mixed Reality 應用程式。
author: ailyadis
ms.author: ''
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia、標記、座標、參考框架、追蹤
ms.openlocfilehash: c0d2f6d0707e1ddd3ee00d3eb80af9fb459f252b
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750347"
---
# <a name="using-vuforia-engine-with-unity"></a>搭配使用 Vuforia 引擎與 Unity

Vuforia Engine 為 HoloLens 提供了一項重要的功能–將 AR 體驗連線到環境中特定映射和物件的能力。 您可以使用這項功能, 在產業企業的機械上重迭引導式逐步指示, 或為實體產品或遊戲新增數位功能和體驗。 

為了在開發 AR 體驗時擁有更大的彈性, Vuforia 引擎提供各種功能和目標。 其中一個最新的功能是 Vuforia 模型目標, 這是商業和產業用途的主要功能。 模型目標可讓應用程式辨識實體物件 (例如機器、汽車或玩具), 並根據 CAD 或數位3D 模型加以追蹤。 對於產業用途, 這項功能可以在工廠或在現場推出時, 為元件工作者和服務技術人員提供 AR 工作指示和程式指引。 

針對手機和平板電腦建立的現有 Vuforia 引擎應用程式, 可以輕鬆地在 Unity 中設定以在 HoloLens 上執行。 您甚至可以使用 Vuforia 引擎將新的 HoloLens 應用程式帶到 Windows 10 平板電腦上, 例如 Surface Pro 4 和 Surface Book。

## <a name="get-the-tools"></a>取得工具

[安裝建議](install-the-tools.md)的 Visual Studio 和 unity 版本, 然後將 unity 設定為使用 Visual Studio 和慣用的 IDE 和編譯器。 

安裝 Unity 時, 請務必安裝「Windows Store .NET 腳本後端」或「Windows Store IL2CPP 腳本後端」。 此外, 請務必選取 [Vuforia 增強的現實支援], 以啟用 Unity 中的 Vuforia 引擎。


## <a name="getting-started-with-vuforia-engine"></a>開始使用 Vuforia Engine

由於 Vuforia 引擎已整合至 Unity, 因此開發人員不需要下載或安裝任何額外的工具。 建議的 Unity 版本是目前位於2017.3 的 LTS 資料流程, 並包含 Vuforia Engine 7.0.57。 學習使用 Vuforia Engine 搭配 HoloLens 的最佳起點是使用[Vuforia Engine HoloLens 範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)(可在 Unity 資產存放區中取得)。 此範例會提供完整的 HoloLens 專案, 包括可部署至 HoloLens 的預先設定場景。

幕後會示範如何使用 Vuforia 的影像目標來辨識影像, 並使用 HoloLens 體驗中的數位內容來增加它。 使用較新版本 Unity 和 Vuforia 的開發人員可以存取已更新的範例, 其中包括顯示 HoloLens 上模型目標使用方式的場景。 您可以輕鬆地在幕後替換自己的內容, 以實驗如何建立使用 Vuforia 引擎的 HoloLens 應用程式。


## <a name="configuring-a-vuforia-app-for-hololens"></a>設定適用于 HoloLens 的 Vuforia 應用程式

開發適用于 HoloLens 的 Vuforia 引擎應用程式基本上與開發其他裝置的 Vuforia 引擎應用程式相同。 接著, 您可以套用下列區段中所述的組建設定和設定。 這就是讓 Vuforia 引擎使用 HoloLens 空間對應和位置追蹤系統所需的一切。

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>建立並執行 HoloLens 的 Vuforia 引擎範例
1.  從 Unity 資產存放區下載[適用于 HoloLens 的 Vuforia 引擎範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)
2.  套用適用于[電源和效能的建議 Unity 引擎選項](performance-recommendations-for-unity.md)
3.  將範例場景新增至組建中的場景。
4.  在 [檔案 > 組建設定] 中, 設定 "通用 Windows 平臺" 的平臺組建目標。
5.  選取下列平臺組建設定: 
   * 目標裝置 = HoloLens
   * 組建類型 = D3D
   * SDK = 已安裝最新版本
   * Visual Studio 版本 = 最新安裝
   * 組建並在 = 本機電腦上執行
6.  在 [**播放程式設定**] 中定義唯一的**產品名稱**, 以在安裝于 HoloLens 時做為應用程式的名稱。
7.  查看**Vuforia**增強的現實和**播放 > XR 設定**中**支援的虛擬實境**
8.  此外, 在 [ **XR 設定**] 下, 確定 [Windows Mixed Reality] 已新增至**虛擬實境 sdk**清單
9.  檢查播放 [設定] 中的下列功能 > 發佈設定 
   * InternetClient
   * 網路
   * SpatialPerception-如果您想要使用 Surface Observer API
10. 選取 [組建] 以產生 Visual Studio 專案
11. 從 Visual Studio 建立可執行檔, 並將它安裝在 HoloLens 上

注意:從7.2 版開始, HoloLens 的 Vuforia 引擎範例包含範例場景, 包括模型目標的範例用法

## <a name="the-vuforia-developer-portal"></a>Vuforia 開發人員入口網站

想要使用 Vuforia 引擎和 HoloLens 建立自己的 AR 經驗的開發人員, 應該在 Vuforia 開發人員入口網站的[developer.vuforia.com](https://developer.vuforia.com/)註冊。 在入口網站中, 開發人員可以存取[Vuforia Engine 論壇](https://developer.vuforia.com/forum), 他們可在其中加入社區討論、具有所有 Vuforia 引擎功能之深入檔的文檔[庫](https://library.vuforia.com/), 以及使用者可以在其中進行的[Vuforia 目標管理員](https://developer.vuforia.com/target-manager)建立自己的自訂目標。 開發人員也可以使用[Vuforia 授權管理員](https://developer.vuforia.com/license-manager)註冊免費的開發人員授權。

## <a name="extended-tracking-with-vuforia"></a>使用 Vuforia 擴充追蹤

[延伸追蹤](https://library.vuforia.com/articles/Training/Extended-Tracking)會建立環境的對應, 以維持追蹤, 即使目標已不在查看中也一樣。 它是 HoloLens 所執行之空間對應的 Vuforia 引擎。 當您在目標上啟用延伸追蹤時, 您可以讓該目標的姿勢傳遞至空間對應系統。 如此一來, 目標就可以同時存在於 Vuforia 引擎和 HoloLens 空間座標系統中, 但不會同時存在。

![Unity 設定視窗](images/vuforia-extendedtracking.png)<br>
*Unity 設定視窗*

**在目標上啟用延伸追蹤**

Vuforia 引擎會自動將使用延伸追蹤的目標的姿勢轉換成 HoloLens 空間座標系統。 這可讓 HoloLens 接管追蹤, 並將任何內容增強功能整合到目標周圍的空間對應中。 此程式是在 Unity 中的 Vuforia 引擎和混合現實 Api 之間進行, 不需要由開發人員進行任何程式設計-它會自動處理。

**以下是發生的情況 ...**
1. Vuforia 的目標追蹤器可識別目標
2. 接著會初始化目標追蹤
3. 系統會分析目標的位置和旋轉, 為 HoloLens 提供健全的姿勢估計以供使用
4. Vuforia 會將目標的姿勢轉換成 HoloLens 空間對應座標空間
5. HoloLens 接管追蹤並停用 Vuforia 追蹤器

開發人員可以控制此程式, 藉由停用 TargetBehaviour 上的延伸追蹤, 將控制權交還給 Vuforia。

**注意：** 從 Vuforia 7.2 開始, 不會再以每個目標為基礎啟用延伸追蹤。 相反地, 開發人員可以開啟裝置追蹤, 在場景中的所有目標上啟用類似的功能。


## <a name="see-also"></a>另請參閱
* [安裝工具](install-the-tools.md)
* [座標系統](coordinate-systems.md)
* [空間對應](spatial-mapping.md)
* [Unity 中的相機](camera-in-unity.md)
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 檔:在 Unity 中針對 Windows 10 進行開發](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia 檔:如何安裝 Vuforia Unity 延伸模組](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia 檔:使用 Unity 中的 HoloLens 範例](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia 檔:Vuforia 中的延伸追蹤](https://library.vuforia.com/articles/Training/Extended-Tracking)
