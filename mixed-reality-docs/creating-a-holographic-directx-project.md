---
title: 建立全像攝影版的 DirectX 專案
description: 說明如何建立新的全像攝影版應用程式，以根據 Windows Mixed Reality 應用程式範本。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全像攝影版的應用程式、 新的應用程式、 UWP 應用程式、 範本應用程式、 全像投影、 新的專案、 逐步解說、 下載、 範例程式碼
ms.openlocfilehash: 7d1ea0246cf823f74e68b4e67fbcfc275d081688
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597123"
---
# <a name="creating-a-holographic-directx-project"></a>建立全像攝影版的 DirectX 專案

全像攝影版的應用程式建立都是 HoloLens<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平台 (UWP) 應用程式</a>。  如果目標桌面 Windows Mixed Reality 耳機，您可以建立 UWP 應用程式或 Win32 應用程式。

DirectX 11 全像攝影版 UWP 應用程式範本十分類似的 DirectX 11 UWP 應用程式範本中;它包含程式迴圈 （或 「 遊戲迴圈 」）， **DeviceResources**類別來管理的 Direct3D 裝置和內容，以及簡化的內容轉譯器類別。 它也有<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>，就像任何其他的 UWP 應用程式。

混合的實境應用程式，不過，有一些額外功能，未出現在一般的 Direct3D 11 UWP 應用程式。 Windows 全像攝影版的應用程式範本是能夠：
* 處理全像攝影版的數位相機與相關聯的 Direct3D 裝置資源。
* 從系統擷取相機背景緩衝區。
* 處理[視線](gaze.md)輸入，並辨識簡單[筆勢](gestures.md)。
* 進入全螢幕是立體聲的轉譯模式。

## <a name="how-do-i-get-started"></a>如何開始？

第一個[安裝工具](install-the-tools.md)，下列有關下載 Visual Studio 2017 的指示和 Microsoft HoloLens 模擬器。 全像攝影版的應用程式範本會包含在相同的安裝程式，為 Microsoft HoloLens 模擬器。 也請確定安裝之前，已選取要安裝的範本選項。

您現在已準備好建立您的 DirectX 11 Windows Mixed Reality 應用程式 ！ 請注意，若要移除範例內容，標記為註解**DRAW_SAMPLE_CONTENT**中的前置處理器指示詞*pch.h*。

## <a name="creating-a-uwp-project"></a>建立 UWP 專案

安裝工具之後您可以建立全像攝影版的 DirectX UWP 專案。 若要建立新的專案：
1. 開始**Visual Studio**。
2. 從**檔案**功能表上，指向**新增**，然後選取**專案**從內容功能表。 **新的專案** 對話方塊隨即開啟。
3. 依序展開**已安裝**左側，展開**視覺化C++** 語言節點。
4. 瀏覽至**Windows 通用 > Holographic**節點，然後選取**全像攝影版的 DirectX 11 應用程式 (通用 Windows) (C++/WinRT)**。
   >[!IMPORTANT]
   >請務必將專案範本的名稱包含"(C++/WinRT) 」。  如果沒有，您有舊版安裝的全像攝影版的專案範本。  若要取得最新的專案範本中，[安裝最新的 HoloLens 模擬器](using-the-hololens-emulator.md)。
5. 填寫**名稱**並**位置**文字方塊中，然後按一下或點選**確定**。 會建立全像攝影版的應用程式專案。
6. 開發目標設定為只 HoloLens 2，請確定**目標版本**並**最低版本**設定為**Windows 10 版本 1903年**。  如果您的也目標 HoloLens （第 1 代） 或桌上型電腦的 Windows Mixed Reality 耳機，您可以設定**最低版本**要**Windows 10 版本 1809年**相反地，雖然這需要一些<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本 adapative 檢查</a>在您的程式碼時使用的 HoloLens 2 的新功能。

![全像攝影版的應用程式專案範本，在 Visual Studio 中的螢幕擷取畫面](images/holographic-directx-app-cpp-new-project.png)<br>
*在 Visual Studio 中的全像攝影版的應用程式專案範本*

範本會產生專案，使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>，C + + 17 語言推演，支援任何符合標準的 C + + 17 編譯器的 Windows 執行階段 api。  專案會示範如何建立世界鎖定 cube 已放入使用者的兩個計量。 使用者可以[空中點選](gestures.md#air-tap)或按下按鈕，將 cube 放在不同的位置所指定的使用者在控制器上[視線](gaze.md)。 您可以修改此專案來建立任何 mixed 的 reality 應用程式。

或者，您可以在其中建立新的專案使用**Visual C#** 全像攝影版的專案範本，此作業取決於 SharpDX。  如果您全像攝影版C#未啟動專案，這是從 Windows 全像攝影版的應用程式範本，您必須從 Windows Mixed Reality 的 ms.fxcompile.targets 檔案複製到C#範本專案，然後匯入在您的.csproj 檔案以編譯 HLSL您新增至您專案的檔案。

檢閱[使用 Visual Studio 部署和偵錯](using-visual-studio.md)如需如何建置和部署範例，您的 HoloLens、 電腦連接的沈浸式裝置或模擬器。

下列指示的其餘部分將假設您使用C++來建置您的應用程式。

### <a name="uwp-app-entry-point"></a>UWP 應用程式進入點

在全像攝影版的 UWP 應用程式啟動**wWinMain** AppView.cpp 中的函式。 **WWinMain**函式會建立應用程式的<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>並啟動<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a>使用它。

從**AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

從那時起，AppView 類別會處理與 Windows 基本輸入的事件、 corewindow，否則事件和傳訊和等等的互動。 它也會建立應用程式所使用的 HolographicSpace。

## <a name="creating-a-win32-project"></a>建立 Win32 專案

最簡單的方式開始建置全像攝影版的專案是採用 Win32 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 範例</a>。

這個 Win32 範例會使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>，C + + 17 語言推演，支援任何符合標準的 C + + 17 編譯器的 Windows 執行階段 api。  專案會示範如何建立世界鎖定 cube 已放入使用者的兩個計量。 使用者可以將 cube 放在不同的位置所指定的使用者在控制器上項目按下按鈕[視線](gaze.md)。 您可以修改此專案來建立任何 mixed 的 reality 應用程式。

### <a name="win32-app-entry-point"></a>Win32 應用程式進入點

在全像攝影版的 Win32 應用程式啟動**wWinMain** AppMain.cpp 中的函式。 **WWinMain**函式會建立應用程式的 HWND，並啟動其訊息迴圈。

從**AppMain.cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

從那時起，AppMain 類別會處理與基本的視窗訊息，並依此類推的互動。 它也會建立應用程式所使用的 HolographicSpace。

## <a name="render-holographic-content"></a>呈現全像攝影版的內容

專案的**內容**資料夾包含類別，可以轉譯在全像投影[全像攝影版的空間](getting-a-holographicspace.md)。 在範本中的預設全像圖是兩個使用者俖籇所下的旋轉立方體。 繪製這個 cube 中實作**SpinningCubeRenderer.cpp**，其中包含這些金鑰的方法：

|  方法  |  說明 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  載入著色器，並建立 cube 網狀結構。 | 
|  `PositionHologram` |  所指定的位置放置闀<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>。 | 
|  `Update` |  旋轉立方體，並設定模型的矩陣。 | 
|  `Render` |  呈現的畫面格使用的端點和像素著色器。 | 

**著色器**子資料夾包含四個預設的著色器實作：

|  著色器  |  說明 | 
|----------|----------|
|  `GeometryShader.hlsl` |  這種傳遞離開的未經修改的幾何。 | 
|  `PixelShader.hlsl` |  若要通過的色彩資料。 插補色彩資料，並指派給像素在點陣化步驟。 | 
|  `VertexShader.hlsl` |  若要執行 GPU 上的頂點處理簡單的著色器。 | 
|  `VPRTVertexShader.hlsl` |  若要執行，適用於 Windows Mixed Reality 是立體聲轉譯在 GPU 上的頂點處理簡單的著色器。 | 

`VertexShaderShared.hlsl` 包含常見的程式碼之間共用`VertexShader.hlsl`和`VPRTVertexShader.hlsl`。

著色器編譯時建置專案時，它們是在載入**SpinningCubeRenderer::CreateDeviceDependentResources**方法。

## <a name="interact-with-your-holograms"></a>與您全像投影互動

在處理使用者輸入**SpatialInputHandler**類別，會遭到<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>執行個體，並訂閱<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>事件。 這可讓偵測空中點選手勢和其他空間的輸入的事件。

## <a name="update-holographic-content"></a>更新全像攝影版的內容

您在遊戲迴圈中，其預設實作中的混合的實境應用程式更新**更新**方法中的`AppMain.cpp`。 **更新**方法會更新場景物件，例如旋轉立方體，並傳回<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>用來取得最新的檢視和投影矩陣，並呈現交換鏈結的物件。

**呈現**方法中的`AppMain.cpp`採用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>並呈現目前的畫面格，以每個全像攝影版的相機，根據目前的應用程式與空間位置的狀態。

## <a name="see-also"></a>另請參閱
* [取得 HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [在 DirectX 中轉譯](rendering-in-directx.md)
* [使用 Visual Studio 來部署和偵錯](using-visual-studio.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [使用全像攝影版的 DirectX 應用程式中的 XAML](using-xaml-with-holographic-directx-apps.md)
