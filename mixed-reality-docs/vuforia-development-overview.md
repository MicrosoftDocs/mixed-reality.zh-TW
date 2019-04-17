---
title: 使用 Unity 的 Vuforia
description: 利用 Vuforia 來建置 Unity 中的 Windows Mixed Reality 應用程式。
author: ChimeraScorn
ms.author: cwhite
ms.date: 03/21/2018
ms.topic: article
keywords: Vuforia，標記、 座標、 參考架構追蹤
ms.openlocfilehash: 43a74989b931fee898af0aeae9e240303b2eef01
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595989"
---
# <a name="using-vuforia-engine-with-unity"></a>使用 Unity 使用 Vuforia 引擎

Vuforia 引擎會將一項重要功能帶入 HoloLens – 連接 AR 電源發生特定的映像和環境中的物件。 您可以使用這項功能，以覆疊工業企業的機制之上的引導式逐步指示，或將數位功能和體驗加入至實體的產品或遊戲。 

較大的彈性時開發 AR 體驗 Vuforia 引擎會提供廣泛的功能和目標。 其中一項我們最新的功能，Vuforia 模型目標，是針對商業和產業使用的重要功能。 模型的目標可讓應用程式，以辨識實體物件，例如電腦、 汽車或 toys 及追蹤為基礎的 CAD 或數位的 3D 模型。 工業的用途，這項功能可以提供組件的背景工作角色和服務技術人員 AR 與處理指示和 factory 中的程序指引，或向外調整欄位中。 

HoloLens 上執行的 Unity 中，可以輕鬆地設定針對手機和平板電腦所建置的現有 Vuforia 引擎應用程式。 您甚至可以使用 Vuforia 引擎，例如 Surface Book 的 Surface Pro 4 的 Windows 10 平板電腦採取新 HoloLens 應用程式。

## <a name="get-the-tools"></a>取得工具

[安裝建議的版本](install-the-tools.md)的 Visual Studio 和 Unity，然後設定 Unity 以使用 Visual Studio、 慣用 IDE 和編譯器。 

當安裝 Unity，請務必安裝 「 Windows 市集.NET 指令碼後端 」 或 「 Windows 儲存 clr、mono、il2cpp 指令碼後端 」。 此外，請務必選取 [Vuforia 擴增實境支援] 來啟用 Vuforia 引擎在 Unity 內。


## <a name="getting-started-with-vuforia-engine"></a>開始使用 Vuforia 引擎

因為 Vuforia 引擎已整合至 Unity，開發人員不需要下載或安裝任何額外的工具。 Unity 的建議的版本是目前位於 2017.3，且包含 Vuforia 引擎 7.0.57 LTS 資料流。 最開始點就了解 Vuforia 引擎使用 HoloLens [Vuforia 引擎 HoloLens 範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)（Unity Asset Store 中提供）。 此範例提供完整的 HoloLens 專案，包括預先設定的場景，可以部署到 HoloLens。

在背景會示範如何使用 Vuforia 映像的目標來辨識映像，並增強 HoloLens 體驗中的數位內容。 使用 Unity 和 Vuforia 的較新版本的開發人員能夠存取更新的範例包括 HoloLens 上顯示模型目標的使用方式的場景。 您可以輕鬆地取代您自己實驗使用 Vuforia 引擎的 HoloLens 應用程式建立場景中的內容。


## <a name="configuring-a-vuforia-app-for-hololens"></a>設定為 HoloLens Vuforia 應用程式

HoloLens 的開發 Vuforia 引擎應用程式基本上是開發 Vuforia 引擎針對其他裝置的應用程式相同。 您接著可以套用的建置設定和下一節中所述的組態。 這是所有所需啟用 Vuforia 引擎處理 HoloLens 空間對應與位置追蹤系統。

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>建置並執行 HoloLens Vuforia 引擎範例
1.  下載[HoloLens 的 Vuforia 引擎範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)從 Unity Asset Store
2.  套用[建議能力和效能的 Unity 引擎選項](performance-recommendations-for-unity.md)
3.  範例將場景新增至組建中的場景。
4.  在檔案中設定您的平台建置目標的 「 通用 Windows 平台 」 > 建置設定。
5.  選擇下列平台組建組態設定： 
   * 目標裝置 = HoloLens
   * 組建類型 = D3D
   * SDK = 最新安裝
   * Visual Studio 版本 = 最新安裝
   * 建置並執行上 = 本機電腦
6.  定義唯一**Product Name**，請在**播放程式設定**，以做為 HoloLens 上安裝時，應用程式名稱。
7.  請檢查**Vuforia 擴增實境**並**支援的虛擬實境**在**播放程式設定 > XR 設定**
8.  之下，而且**XR 設定**，請確定 「 Windows Mixed Reality"會新增到**虛擬實境 Sdk**清單
9.  檢查播放程式設定中的下列功能 > 發行設定 
   * InternetClient
   * WebCam
   * SpatialPerception-如果您想要使用介面觀察者 API
10. 選取組建，以產生 Visual Studio 專案
11. 從 Visual Studio 中建置可執行檔，並將它安裝在您的 HoloLens 上

注意：從開始版本 7.2、 HoloLens Vuforia 引擎範例包含範例場景，包括模型目標的使用方式範例

## <a name="the-vuforia-developer-portal"></a>Vuforia 開發人員入口網站

開發人員想要建立自己的 AR 發生 Vuforia 引擎，而且我們 Vuforia 開發人員入口網站，在應該註冊 HoloLens [developer.vuforia.com](https://developer.vuforia.com/)。 在入口網站中，開發人員可以存取[Vuforia 引擎論壇](https://developer.vuforia.com/forum)它們可以加入社群的討論，其中[程式庫](https://library.vuforia.com/)與深入的文件上的所有的 Vuforia 引擎功能，以及[Vuforia 目標管理員](https://developer.vuforia.com/target-manager)使用者可以在其中建立自己的自訂目標。 開發人員也可以註冊免費的開發人員授權使用[Vuforia License Manager](https://developer.vuforia.com/license-manager)。

## <a name="extended-tracking-with-vuforia"></a>使用 Vuforia 擴充的追蹤

[擴充追蹤](https://library.vuforia.com/articles/Training/Extended-Tracking)建立環境，以維護追蹤即使目標已經不在檢視中的對應。 它是由 HoloLens 空間對應 Vuforia 引擎的對應項目。 當您啟用延伸的追蹤的目標上時，您會啟用要傳遞之空間的對應系統為目標的姿勢。 如此一來，目標可以存在於 Vuforia 引擎和 HoloLens 空間的座標系統，但不同時。

![Unity 設定視窗](images/vuforia-extendedtracking.png)<br>
*Unity 設定視窗*

**啟用延伸的追蹤目標**

Vuforia 引擎會將自動轉換會使用延伸的追蹤，到 HoloLens 空間座標系統為目標的姿勢。 這可讓 HoloLens 將接管追蹤，以及整合擴充到空間的對應目標的周圍環境的任何內容。 此程序 Vuforia 引擎與混合的實境中 Unity Api 之間發生，而且不需要任何開發人員的程式設計-它會自動處理。

**以下是可能發生的狀況...**
1. Vuforia 的 target Tracker 會辨識目標
2. 然後初始化目標追蹤
3. 位置和旋轉目標，系統會分析提供要使用的 HoloLens 的強固的姿勢預估
4. Vuforia HoloLens 空間的對應座標空間中轉換目標的姿勢
5. HoloLens 高於追蹤並停用 Vuforia 追蹤器

開發人員可以控制這個程序，將控制權交還給 Vuforia，，藉由停用上 TargetBehaviour 延伸的追蹤。

**注意：** 從 Vuforia 7.2 開始，擴充追蹤已不再啟用每個目標為基礎。 相反地，開發人員可以開啟追蹤來啟用類似的功能，在場景中的所有目標上的裝置。


## <a name="see-also"></a>另請參閱
* [安裝工具](install-the-tools.md)
* [座標系統](coordinate-systems.md)
* [空間對應](spatial-mapping.md)
* [在 Unity 中的相機](camera-in-unity.md)
* [匯出和建置 Unity Visual Studio 方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 文件：為 Unity 中的 Windows 10 開發](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia 文件：如何安裝 Vuforia Unity 延伸模組](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia 文件：使用 Unity 的 HoloLens 範例](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia 文件：在 Vuforia 擴充的追蹤](https://library.vuforia.com/articles/Training/Extended-Tracking)
