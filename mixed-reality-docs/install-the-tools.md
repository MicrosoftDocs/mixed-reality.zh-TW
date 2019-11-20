---
title: 安裝工具
description: 從此開始準備混合實境開發。 本文應該一律反映 Unity、Visual Studio 以及建議用於 HoloLens 和 Windows Mixed Reality 沉浸式頭戴裝置開發的其他工具的最新版本。
author: thetuvix
ms.author: alexturn
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 工具, 開始使用, 基本概念, unity, visual studio, 工具組
ms.openlocfilehash: f63cf094c5dffd29d2cb54cb56df588858785ae9
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064252"
---
# <a name="install-the-tools"></a>安裝工具

取得為 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 頭戴裝置建置應用程式所需的工具。 沒有個別的 SDK 可用於 Windows Mixed Reality 開發，您將使用 Visual Studio 搭配 Windows 10 SDK。

沒有混合實境裝置嗎？ 您可以安裝 [HoloLens 模擬器](using-the-hololens-emulator.md)，以在沒有 HoloLens 的情況下測試混合實境應用程式的一些功能。 您也可以使用 [Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)，針對沉浸式頭戴裝置測試您的混合實境應用程式。

我們建議您安裝 Unity 遊戲引擎，因為這是開始建立混合實境應用程式的最簡單方式。 不過，如果您想要使用自訂引擎，也可以針對 DirectX 進行建置。

>[!TIP]
>將這個頁面加入書籤並定期檢查，以在建議用於混合實境開發的每個工具最新版本上保持最新狀態。

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>安裝檢查清單


| 工具 | 描述 | 附註 |
|---------|---------|---------|
| ![Windows 標誌](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(手動安裝連結)</a> | 安裝最新版的 Windows 10，讓您電腦的作業系統符合您要建置混合實境應用程式的平台。 | **安裝 Windows 10** <br> <ul><li>您可以透過 [設定] 中的 Windows Update 或藉由建立安裝媒體 (使用左欄中的連結)，安裝最新版的 Windows 10。<li>請參閱[目前的版本資訊](release-notes-october-2018.md)，以取得每個 Windows 10 版本可用的最新混合實境功能。</ul> **在開發電腦上啟用開發人員模式** (在 [設定] > [更新與安全性] / [開發人員專用])。 <br><br> **企業和公司管理電腦的注意事項：** 如果您的電腦由組織的 IT 部門管理，您可能需要與其連絡以便更新。 <br><br> **Windows 的 'N' 版本：** Windows 的 'N' 版本不支援 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置。 |
| ![Visual Studio 標誌](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.1 或更新版本)**<br>(安裝連結)</a> | Windows 等的全功能整合式開發環境 (IDE)。 您將使用 Visual Studio 來撰寫程式碼、偵錯、測試及部署。 | **要安裝的工作負載：** <ul><li>使用 C++ 的傳統型開發</li><li>通用 Windows 平台 (UWP) 開發</li></ul>**Unity 的注意事項：** 除非您刻意嘗試針對特定用途安裝更新 (非 LTS) 版本的 Unity，否則我們建議「不要」  在 Visual Studio 安裝過程中安裝 Unity 工作負載，並改為安裝 Unity 的 2018.4 LTS 資料流，如下所述。<br> <br>**注意：** Visual Studio 2019 16.0 版中的混合實境應用程式偵錯有一些已知問題。  請務必將 Visual Studio 2019 更新為 16.1 或更新版本。 |
| ![Windows 標誌](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>(手動安裝連結)</a> | 提供用於在 HoloLens 2 上建置 Windows 10 應用程式的最新標頭、程式庫、中繼資料和工具。 | 若要建置 HoloLens 2 應用程式，您必須安裝 Windows SDK (組建 18362 或更新版本)。<br> <br> 如果只要針對傳統型 Windows Mixed Reality 頭戴式裝置或 HoloLens (第 1 代) 開發應用程式，您可以使用 Visual Studio 2017 所安裝的 Windows SDK。 |
| ![Visual Studio 標誌](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2110553" target="_blank">**HoloLens 2 模擬器 (2019 年 11 月更新)**<br>(安裝連結：10.0.18362.1039)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (第 1 代) 模擬器**<br>(安裝連結：10.0.17763.134)</a> | HoloLens 模擬器可讓您在沒有實體 HoloLens 的 HoloLens 虛擬機器映像上執行應用程式。<br> <br> | 如需開始使用模擬器的詳細資訊，請參閱[使用 HoloLens 模擬器](using-the-hololens-emulator.md)。<br> <br> **您的系統必須支援 Hyper-V**，模擬器安裝才能成功。 請參考下面的「系統需求」一節以取得詳細資料。 <br>|

## <a name="choose-your-engine"></a>選擇您的引擎

:::row:::
    :::column:::
       [![Unity](images/unity_logo.png)](https://unity3d.com/unity/qa/lts-releases?version=2018.4)<br>
        **[Unity](https://unity3d.com/unity/qa/lts-releases?version=2018.4)**<br>
        通常建議 Unity LTS (長期支援) 資料流作為用來啟動新專案的最佳版本，並更新為其最新修訂版本，以挑選最新穩定的修正程式。<br> <br>目前建議使用 **Unity 2018.4.x**，這是下方 MRTK v2 所需的 LTS 組建。<br> <br>有些開發人員可能想要針對特定理由使用不同的 Unity 版本。 針對這些情況，Unity 會支援不同版本的並排安裝。<br><br>[![MRTK](images/MRTKIcon.jpg)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)<br>**[混合實境工具組 (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)**<br>適用於 Unity 的混合實境工具組 (MRTK) v2 是混合實境應用程式的開放原始碼跨平台開發套件。<br><br> MRTK v2 主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。 此專案的目標是減少建立混合實境應用程式的進入障礙，並且隨著進展回饋社群。
    :::column-end:::
    :::column:::
        [![Unreal](images/Unreal_logo.png)](https://docs.unrealengine.com//GettingStarted/Installation/index.html)<br>
        **[Unreal](https://docs.unrealengine.com//GettingStarted/Installation/index.html)**<br>
        Unreal Engine 4 是功能強大的開放原始碼建立引擎，具備對 C++ 和 Blueprints 混合實境的完整支援。<br> <br>HoloLens 對 Unreal Engine 4.23 的支援目前為搶鮮版。
    :::column-end:::
    :::column:::
        [![DirectX 範本](images/DirectX_logo.png)](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)<br>
        **[DirectX 範本](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)**<br>
        使用 DirectX 開始撰寫混合實境應用程式所需的所有基本知識。 包括轉譯迴圈 (或「遊戲迴圈」)、DeviceResources 協助程式類別，用來管理 Direct3D 裝置和內容，以及簡單的範例轉譯器。
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>混合實境工具組 (MRTK)

混合實境工具組提供的元件和功能主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 頭戴裝置和 OpenVR 平台為目標的應用程式。 此專案的目標是減少建立混合實境應用程式的進入障礙，並且隨著進展回饋社群。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合實境工具組</a> - 指令碼和元件的集合，目的是加速開發混合實境應用程式。
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">混合實境工具組 - Unity</a> - 使用基底工具組中的程式碼，使其在 Unity 中更容易使用。
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>設定您的電腦以便進行混合實境開發

Windows 10 SDK 最適合用於 Windows 10 作業系統。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。 請注意，舊版作業系統不支援所有工具。 

### <a name="for-hololens-development"></a>對於 HoloLens 開發

設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。 如果您打算使用 HoloLens (第 1 代) 模擬器，您會想確定您的電腦也符合 [HoloLens 模擬器系統需求](using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](using-the-hololens-emulator.md)。

如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。

### <a name="for-immersive-vr-headset-development"></a>對於沈浸式 (VR) 頭戴裝置開發

>[!NOTE]
>下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」  目前的最低建議規格，而且會定期更新。

>[!WARNING]
>請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」  。

如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。

目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。

<table>
<tr>
<th></th><th> 最低需求</th><th> 推薦項目</th>
</tr><tr>
<td> 處理器</td><td> <b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</td><td> <b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</td>
</tr><tr>
<td> GPU</td><td> <b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</td><td><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</td>
</tr><tr>
<td> GPU 驅動程式 WDDM 版本</td><td colspan="2"> WDDM 2.2 驅動程式</td>
</tr><tr>
<td> 散熱設計功率</td><td colspan="2"> 15W 或更大</td>
</tr><tr>
<td> 圖形顯示連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</td>
</tr><tr>
<td> 顯示器解析度</td><td colspan="2"> 解決方式：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</td>
</tr><tr>
<td> 記憶體</td><td> 8&#160;GB RAM 或更大</td><td> 16 GB RAM 或更大</td>
</tr><tr>
<td> 儲存體</td><td colspan="2"> &gt;10 GB 額外可用空間</td>
</tr><tr>
<td> USB 連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></td>
</tr><tr>
<td> 藍牙</td><td colspan="2"> Bluetooth 4.0 (適用於周邊連線)</td>
</tr>
</table>

## <a name="see-also"></a>請參閱

* [開發概觀](development.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [使用 Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)
* [Unity 開發概觀](unity-development-overview.md)
* [Unreal 開發概觀](unreal-development-overview.md)
* [DirectX 開發概觀](directx-development-overview.md)
* [HoloLens 模擬器封存](hololens-emulator-archive.md)
