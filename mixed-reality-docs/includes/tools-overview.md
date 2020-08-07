# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1.下載最新版本

建議 [Unity LTS (長期支援)](https://unity3d.com/unity/qa/lts-releases) 資料流作為用來啟動新專案的最佳版本，並更新為其最新修訂版本，以挑選最新穩定的修正程式。 
* 目前建議使用 **Unity 2019**，這是以下 MRTK v2 所需的 LTS 組建。
* 如果您基於特定理由而需要使用不同的 Unity 版本，Unity 支援不同版本的並存安裝。

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2.匯入混合實境工具組 (MRTK)
![MRTK](../images/UX/MRTK_UX_Hero.png)

[混合實境工具組](../mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。 MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。 該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)<br>**混合實境工具組-Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果您不想使用適用於 Unity 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。

#### <a name="other-tools-optional"></a>其他工具 [選用]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.設定您的電腦以便進行混合實境開發

Windows 10 SDK 最適合用於 Windows 10 作業系統。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。 請注意，舊版作業系統不支援所有工具。 

> [!NOTE]
> 您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。 視您的需求而定，請確定您符合下列需求。

#### <a name="for-hololens-development"></a>對於 HoloLens 開發

設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。 如果您打算使用 [HoloLens 模擬器](../using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](../using-the-hololens-emulator.md)。

如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。

#### <a name="immersive-vr-headset-requirements"></a>沈浸式 (VR) 頭戴式裝置需求

>[!NOTE]
>下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。

>[!WARNING]
>請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。

如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。

目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。

<table>
<tr>
<th></th><th> 最低需求</th><th> 建議</th>
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
<td> 顯示器解析度</td><td colspan="2"> 解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM 或更大</td><td> 16 GB RAM 或更大</td>
</tr><tr>
<td> 存放裝置</td><td colspan="2"> &gt;10 GB 額外可用空間</td>
</tr><tr>
<td> USB 連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (適用於周邊連線)</td>
</tr>
</table>

### <a name="whats-next"></a>接下來要做什麼？

> [!div class="nextstepaction"]
> [開始您的 Unity 旅程](../unity-development-overview.md)

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1.下載最新版本

建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2.匯入混合實境工具組 (MRTK)
![MRTK](../images/UX/MRTK_UX_Hero.png)

混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。 MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。 該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)<br>**混合實境工具組-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。

#### <a name="other-tools-optional"></a>其他工具 [選用]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.設定您的電腦以便進行混合實境開發

Windows 10 SDK 最適合用於 Windows 10 作業系統。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。 請注意，舊版作業系統不支援所有工具。 

> [!NOTE]
> 您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。 視您的需求而定，請確定您符合下列需求。

#### <a name="for-hololens-development"></a>對於 HoloLens 開發

設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。 如果您打算使用 [HoloLens 模擬器](../using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。

#### <a name="immersive-vr-headset-requirements"></a>沈浸式 (VR) 頭戴式裝置需求

>[!NOTE]
>下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。

>[!WARNING]
>請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。

如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。

目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。

<table>
<tr>
<th></th><th> 最低需求</th><th> 建議</th>
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
<td> 顯示器解析度</td><td colspan="2"> 解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM 或更大</td><td> 16 GB RAM 或更大</td>
</tr><tr>
<td> 存放裝置</td><td colspan="2"> &gt;10 GB 額外可用空間</td>
</tr><tr>
<td> USB 連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (適用於周邊連線)</td>
</tr>
</table>

### <a name="whats-next"></a>接下來要做什麼？

> [!div class="nextstepaction"]
> [開始您的 Unreal 旅程](../unreal-development-overview.md)

# <a name="native-openxr"></a>[原生 (OpenXR)](#tab/native)

 ![原生應用程式開發](../images/native_logo_banner.png)

原生 OpenXR 開發沒有可供您下載的引擎。 您可以在[開始使用 OpenXR](../openxr-getting-started.md) 文件中找到開始進行開發所需的一切資訊。

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1.設定您的電腦以便進行混合實境開發

Windows 10 SDK 最適合用於 Windows 10 作業系統。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。 請注意，舊版作業系統不支援所有工具。

#### <a name="for-hololens-development"></a>對於 HoloLens 開發

設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。 如果您打算使用 [HoloLens 模擬器](../using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。

> [!NOTE]
> 您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。 視您的需求而定，請確定您符合下列需求。

#### <a name="immersive-vr-headset-requirements"></a>沈浸式 (VR) 頭戴式裝置需求

>[!NOTE]
>下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。

>[!WARNING]
>請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。

如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。

目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。

<table>
<tr>
<th></th><th> 最低需求</th><th> 建議</th>
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
<td> 顯示器解析度</td><td colspan="2"> 解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM 或更大</td><td> 16 GB RAM 或更大</td>
</tr><tr>
<td> 存放裝置</td><td colspan="2"> &gt;10 GB 額外可用空間</td>
</tr><tr>
<td> USB 連接埠</td><td colspan="2"> 適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (適用於周邊連線)</td>
</tr>
</table>

### <a name="whats-next"></a>接下來要做什麼？

> [!div class="nextstepaction"]
> [開始您的原生旅程](../directx-development-overview.md)


