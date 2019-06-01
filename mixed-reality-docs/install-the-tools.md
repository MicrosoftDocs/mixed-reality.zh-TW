---
title: 安裝工具
description: 從這裡開始，若要準備適用於混合的實境開發。 這篇文章應該永遠會反映 Unity 及 Visual Studio 中，建議在 HoloLens 與 Windows Mixed Reality 沈浸式耳機開發其他工具的最新的版本。
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態，工具，開始，基本概念、 unity、 visual studio 工具組
ms.openlocfilehash: 32dcda0eceb8d3717de7b2502d86f03cda975b8f
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453734"
---
# <a name="install-the-tools"></a>安裝工具

取得您要建置 Microsoft HoloLens 和沈浸式 (VR) 耳機 Windows Mixed Reality 應用程式的工具。 沒有任何個別的 SDK for Windows Mixed Reality 開發;Windows 10 sdk，您將使用 Visual Studio。

沒有混合的實境裝置嗎？ 您可以安裝[HoloLens 模擬器](using-the-hololens-emulator.md)測試沒有 HoloLens 的混合的實境應用程式的一些功能。 您也可以使用[Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)來測試您的混合的實境應用程式的沈浸式耳機。

我們建議您安裝 Unity 遊戲引擎，因為最簡單的方式，若要開始建立混合實境應用程式，不過，您也可以建置針對 DirectX 如果您想要使用自訂的引擎。

>[!TIP]
>這個頁面加入書籤，並檢查定期以保持在最新版本的每個建議在混合的實境開發的工具。

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>安裝檢查清單


| 工具 | 描述 | 附註 |
|---------|---------|---------|
| ![Windows 標誌](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>（手動安裝連結）</a> | 使您的電腦的作業系統比對，您要建置混合的實境應用程式的平台，請安裝最新版的 Windows 10。 | **安裝 Windows 10** <br> <ul><li>在 設定，或藉由建立安裝媒體 （使用左側的資料行中的連結），您可以安裝最新版的 Windows 10 透過 Windows Update。<li>請參閱[目前的版本資訊](release-notes-october-2018.md)如需最新混合實境功能可以使用每個版本的 Windows 10。</ul> **啟用您的電腦上的開發人員模式**設定 > 更新與安全性 > 適用於開發人員。 <br><br> **請注意，適用於企業和公司管理的電腦：** 如果您的電腦由管理您組織的 IT 部門，您可能需要與其連絡以更新。 <br><br> **'N' 個版本的 Windows:** 'N' 個 Windows 版本不支援 Windows Mixed Reality 沈浸式 (VR) 耳機。 |
| ![Visual Studio 標誌](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>（安裝連結）</a> | 功能完整的整合式的開發環境 (IDE) 的 Windows 和更多功能。 您將使用 Visual Studio 來撰寫程式碼、 偵錯、 測試及部署。 | **若要安裝的工作負載：** <ul><li>使用的桌面開發C++</li><li>通用 Windows 平台開發</li></ul>**Unity 的注意事項：** 除非您有意嘗試安裝較新的 (非 LTS) 版本的 Unity 針對特定用途，我們建議*不*的 Visual Studio 安裝過程中安裝的 Unity 工作負載，並改為安裝 2018.4 LTSUnity，註記下的資料流。<br> <br>**注意：** 有一些已知的問題，目前在 Visual Studio 2019 的混合的實境開發。  現在，我們建議您繼續使用 Visual Studio 2017。 |
| ![Windows 標誌](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>（手動安裝連結）</a> | 提供最新的標頭、 程式庫、 中繼資料，以及工具建置 HoloLens 2 上的 Windows 10 應用程式。 | 若要建置 HoloLens 2 應用程式，您必須安裝 Windows SDK，建置 18362 或更新版本。<br> <br> 如果您只開發桌面 Windows Mixed Reality 耳機或 HoloLens 的應用程式 （第 1 代），您可以使用 Visual Studio 2017 所安裝的 Windows SDK。 |
| ![Visual Studio 標誌](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2087187" target="_blank">**HoloLens 2 模擬器**<br>(安裝連結：10.0.18362.1005)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens （第 1 代） 模擬器**<br>(安裝連結：10.0.17763.253)</a> | 模擬器可讓您在沒有實體的 HoloLens HoloLens 虛擬機器映像上執行應用程式。<br> <br> 此套件也包含 Visual Studio 全像攝影版的 DirectX 專案範本。 | 請參閱[使用 HoloLens 模擬器](using-the-hololens-emulator.md)如需開始使用模擬器的詳細資訊。<br> <br> **您的系統必須支援 HYPER-V**模擬器安裝成功。 請參閱下方詳細資料的系統需求一節。 如有需要，您可以選取要安裝的範本不需模擬器。<br>|
| ![Unity 標誌](images/unity_logo.png)<br><br><a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">**Unity 2018.4**<br>（安裝連結）</a> | Unity 遊戲引擎是最簡單的方式，來建立混合的實境體驗，Windows Mixed Reality 功能的內建支援。 | 通常建議 Unity LTS （長字詞支援） 資料流做為用來啟動新的專案，最佳的版本更新至其最新的修訂，挑選最新穩定的修正程式。<br> <br>目前的建議是使用**Unity 2018.4.x**，這是所需的下列 MRTK v2 LTS 組建。<br> <br>有些開發人員可能想要針對特定的理由要使用不同版本的 Unity。 針對這些情況下，Unity 會支援不同版本的並排顯示的安裝。 |
| ![MRTK 標誌](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**適用於 Unity 的混合的實境工具組 (MRTK v2)** </a> | Unity 的 MRTK v2 是開放原始碼跨平台開發套件的混合的實境應用程式。<br><br> MRTK v2 被要加速開發以 Microsoft HoloLens，Windows Mixed Reality 沈浸式 (VR) 耳機和 OpenVR 平台為目標的應用程式。 專案目標是減少障礙，以建立混合的實境應用程式的項目，並參與社群，我們都成長。 | 深入了解 MRTK v2 造訪專案組<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">GitHub wiki</a>。 |


## <a name="mixed-reality-toolkit"></a>混合的實境工具組

混合實境 Toolkit 提供元件和功能，為了加速開發以 Microsoft HoloLens，Windows Mixed Reality 耳機和 OpenVR 平台為目標的應用程式。 專案被針對至項目，以建立混合的實境應用程式以及貢獻回饋給社群隨著我們越來越減少屏障。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit Unity</a> -使用程式碼基底工具組，並可讓您更輕鬆地在 Unity 中使用。
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> -程式碼項目和直接在 HoloLens 或沈浸式 (VR) 耳機，可能無法執行的元件，但改為使用它們來建置的組體驗為目標的 Windows Mixed Reality。

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>設定您電腦上的混合的實境開發

Windows 10 SDK 最適合在 Windows 10 的作業系統。 此 SDK 也支援 Windows 8.1，Windows 8、 Windows 7、 Windows Server 2012，Windows Server 2008 R2 上。 請注意，並非所有工具都支援在舊版作業系統上。 

### <a name="for-hololens-development"></a>HoloLens 的開發

當設定開發電腦 HoloLens 的開發，請確定它符合系統需求<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a>並<a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>。 如果您打算使用 HoloLens （第 1 代） 的模擬器，您會想要確定您的電腦符合[HoloLens 模擬器系統需求](using-the-hololens-emulator.md#hololens-emulator-system-requirements)以及。

若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](using-the-hololens-emulator.md)。

如果您打算開發 HoloLens 與 Windows Mixed Reality 沈浸式的 (VR) 耳機時，請使用系統建議和需求下一節。

### <a name="for-immersive-vr-headset-development"></a>沈浸式 (VR) 耳機開發

>[!NOTE]
>下列指導方針是目前的最低和建議規格的沈浸式 (VR) 耳機*開發電腦*，而且可能會定期更新。

>[!WARNING]
>請勿混淆這[最小的 PC 硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)，其中概述了*取用者電腦規格*您應該目標沈浸式 (VR) 耳機應用程式或遊戲。

如果沈浸式耳機開發電腦並沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您將需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)連接耳機。

目前沒有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)加上一些硬體設定，特別是使用具有混合式圖形的 notebook。

<table>
<tr>
<th></th><th> 最小值</th><th> 建議</th>
</tr><tr>
<td> 處理器</td><td> <b>Notebook:</b>Intel 行動 Core i5 中第 7 層代 CPU，雙核心與超執行緒<b>桌面：</b>Intel 桌面 i5 中第 6 個層代 CPU，雙核心與超執行緒<b>或</b>AMD FX4350 4.2 Ghz 四核心對等項目</td><td> <b>桌面：</b>第 6 個層代 （6 核心） 的 Intel 桌面 i7<b>或</b>AMD Ryzen 5 1600 （6 核心，12 的執行緒）</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b>NVIDIA GTX 965 M、 AMD RX 460 M (2GB) 相等或更高 DX12 GPU<b>桌面：</b>NVIDIA GTX 960/1050、 AMD Radeon RX 460 (2GB) 相等或更高 DX12 GPU</td><td><b>桌面：</b>NVIDIA GTX 980/1060，AMD Radeon RX 480 (2GB) 相等或更高 DX12 GPU</td>
</tr><tr>
<td> GPU 驅動程式 WDDM 版本</td><td colspan="2"> WDDM 2.2 驅動程式</td>
</tr><tr>
<td> 熱設計電源</td><td colspan="2"> 15W 或更新版本</td>
</tr><tr>
<td> 圖形顯示通訊埠</td><td colspan="2"> 1 倍的可用的圖形顯示的連接埠&#160;耳機 （HDMI 1.4 或 60 赫茲耳機 HDMI 2.0 或 90 Hz 耳機 DisplayPort 1.2 DisplayPort 1.2）</td>
</tr><tr>
<td> 顯示器解析度</td><td colspan="2"> 解決方式：SVGA (800 x 600) 或更高的位元深度：每像素 32 位元的色彩</td>
</tr><tr>
<td> 記憶體</td><td> 8&#160;GB 或以上的 RAM</td><td> 16 GB 或以上的 RAM</td>
</tr><tr>
<td> 儲存體</td><td colspan="2"> &gt;10 GB 的額外可用空間</td>
</tr><tr>
<td> USB 連接埠</td><td colspan="2"> 1 倍的可用的 USB 連接埠 (USB 3.0 Type-A) 耳機<b>附註：USB 必須提供至少 900mA</b></td>
</tr><tr>
<td> 藍牙</td><td colspan="2"> 藍芽 4.0 （適用於配件的連線）</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱

* [開發概觀](development-overview.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [使用 Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)
* [Unity 開發概觀](unity-development-overview.md)
* [DirectX 開發概觀](directx-development-overview.md)
* [HoloLens 模擬器封存](hololens-emulator-archive.md)
