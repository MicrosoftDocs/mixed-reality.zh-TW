---
title: 建立全像攝影 DirectX 專案
description: 說明如何根據 Windows Mixed Reality 應用程式範本建立新的全像攝影應用程式。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 全像攝影應用程式, 新的應用程式, UWP 應用程式, 範本應用程式, 全息影像, 新專案, 逐步解說, 下載, 範例程式碼
ms.openlocfilehash: 24f217021cd448f19a744696de42f580f139f76f
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387620"
---
# <a name="creating-a-holographic-directx-project"></a>建立全像攝影 DirectX 專案

您為 HoloLens 建立的全像攝影應用程式將會是<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平臺 (UWP) 應用程式</a>。  如果以桌面 Windows Mixed Reality 耳機為目標, 您可以建立 UWP 應用程式或 Win32 應用程式。

DirectX 11 全像攝影版 UWP 應用程式範本與 DirectX 11 UWP 應用程式範本十分相似;其中包含一個程式迴圈 (或「遊戲迴圈」)、一個**DeviceResources**類別來管理 Direct3D 裝置和內容, 以及一個簡化的內容轉譯器類別。 它也有<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, 就像任何其他 UWP 應用程式一樣。

不過, mixed reality 應用程式具有一些不存在於一般 Direct3D 11 UWP 應用程式中的額外功能。 Windows 全像應用程式範本可以:
* 處理與全像攝影相機相關聯的 Direct3D 裝置資源。
* 從系統取出相機背面緩衝區。
* 處理[注視](gaze.md)的輸入, 並辨識簡單[手勢](gestures.md)。
* 進入全螢幕身歷聲轉譯模式。

## <a name="how-do-i-get-started"></a>如何? 開始使用了嗎？

請依照下載 Visual Studio 2019 和 Microsoft HoloLens 模擬器中的指示, 先[安裝這些工具](install-the-tools.md)。 全像攝影應用程式範本包含在與 Microsoft HoloLens 模擬器相同的安裝程式中。 此外, 請確定已選取 [安裝範本] 選項, 然後再安裝。

現在您已經準備好建立 DirectX 11 Windows Mixed Reality 應用程式! 請注意, 若要移除範例內容, 請將*pch*中的**DRAW_SAMPLE_CONTENT**預處理器指示詞標記為批註。

## <a name="creating-a-uwp-project"></a>建立 UWP 專案

[安裝工具](install-the-tools.md)之後, 您就可以建立全像的 DirectX UWP 專案。

若要建立新的專案:
1. 啟動**Visual Studio**。
2. 從 [檔案] 功能表, 指向 [**新增**], 然後從內容功能表中選取 [**專案**]。 [**新增專案**] 對話方塊隨即開啟。
3. 展開左側的 [**已安裝**], 然後展開 [**視覺效果C++** 語言] 節點。
4. 流覽至 [ **Windows 通用 >** 全像攝影] 節點, 然後選取 [全像**C++/WinRT] [DirectX 11 應用程式 (通用 Windows)** ]。
   ![Visual Studio 中的全像「 C++DirectX 11/WinRT UWP 應用程式」專案範本的螢幕擷取畫面](images/holographic-directx-app-cpp-new-project.png)<br>
   *Visual Studio 中的C++全息版 DirectX 11/WinRT UWP 應用程式專案範本*
   >[!IMPORTANT]
   >請確定專案範本的名稱包含 "(C++/WinRT)"。  如果沒有, 則會安裝較舊版本的全像攝影專案範本。  若要取得最新的專案範本, 請[安裝最新的 HoloLens 模擬器](using-the-hololens-emulator.md)。
5. 填寫 [**名稱**] 和 [**位置**] 文字方塊, 然後按一下或點擊 **[確定]** 。 會建立全像攝影應用程式專案。
6. 針對僅以 HoloLens 2 為目標的開發, 請確定 [**目標版本**] 和 [**最低版本**] 設定為 [ **Windows 10, 版本 1903**]。  如果您也以 HoloLens (第1代) 或桌面 Windows Mixed Reality 耳機為目標, 則可以改為將**最低版本**設定為**windows 10 版本 1809** , 但在使用 new 時, 您的程式碼中需要一些版本調適型<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">檢查</a>HoloLens 2 的功能。
   ![將 Windows 10 (版本 1903) 設為目標和最低版本的螢幕擷取畫面](images/new-uwp-project.png)<br>
   *將 **Windows 10 (版本 1903)** 設定為目標和最低版本*
   >[!IMPORTANT]
   >如果您沒有看到 [ **windows 10, 版本 1903** ] 選項, 則不會安裝最新的 WINDOWS 10 SDK。  若要讓此選項出現, 請<a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">安裝 Windows 10 SDK 的版本10.0.18362.0 或更新版本</a>。

此範本會使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>產生專案, 這是支援任何符合標準之 c + + 17 編譯器的 Windows 執行階段 api 的 c + + 17 語言投影。  此專案會示範如何建立世界鎖定的 cube, 這是由使用者放置兩個計量。 使用者可以[按一下](gestures.md#air-tap)或按下控制器上的按鈕, 將 cube 放在使用者[注視](gaze.md)所指定的不同位置。 您可以修改此專案, 以建立任何混合現實應用程式。

或者, 您可以使用以 SharpDX 為基礎的**Visual C#** 全像投影專案範本來建立新的專案。  如果您的C#全像攝影專案未從 windows 全像攝影應用程式範本開始, 您必須從 Windows Mixed Reality C#範本專案複製 fxcompile 檔案, 並將它匯入 .csproj 檔案中, 才能編譯 HLSL您新增至專案的檔案。

請參閱[使用 Visual Studio 部署和調試](using-visual-studio.md)程式, 以瞭解如何建立範例, 並將其部署至您的 HoloLens、已連接沉浸式裝置的電腦或模擬器。

下面的其餘指示會假設您使用C++來建立應用程式。

### <a name="uwp-app-entry-point"></a>UWP 應用程式進入點

您的全像攝影 UWP 應用程式會在 AppView 中的**wWinMain**函式開始。 **WWinMain**函式會建立應用程式的<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> , 並使用它來啟動<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 。

從**AppView**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

從該時間點開始, AppView 類別會處理與 Windows 基本輸入事件、CoreWindow 事件和訊息等的互動。 它也會建立您的應用程式所使用的 HolographicSpace。

## <a name="creating-a-win32-project"></a>建立 Win32 專案

開始建立 Win32 全像投影專案最簡單的方式, 就是調整<a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram*的 win32 範例</a>。

這個 Win32 範例會使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, 這是支援任何符合標準之 c + + 17 編譯器的 Windows 執行階段 api 的 c + + 17 語言投影。  此專案會示範如何建立世界鎖定的 cube, 這是由使用者放置兩個計量。 使用者可以按下控制器上的按鈕, 將 cube 放在使用者[注視](gaze.md)所指定的不同位置。 您可以修改此專案, 以建立任何混合現實應用程式。

### <a name="win32-app-entry-point"></a>Win32 應用程式進入點

您的全像的 Win32 應用程式會從 AppMain 中的**wWinMain**函式開始。 **WWinMain**函數會建立應用程式的 HWND 並啟動其訊息迴圈。

從**AppMain**:

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

從該時間點開始, AppMain 類別會處理與基本視窗訊息的互動, 依此類推。 它也會建立您的應用程式所使用的 HolographicSpace。

## <a name="render-holographic-content"></a>呈現全像攝影內容

專案的**Content**資料夾包含可在全像攝影[空間](getting-a-holographicspace.md)中轉譯全息影像的類別。 範本中的預設全息影像是一個旋轉的 cube, 這會將兩個計量放在使用者之外。 繪製此 cube 會在**SpinningCubeRenderer**中實作為下列主要方法:

|  方法  |  說明 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  載入著色器並建立 cube 網格。 | 
|  `PositionHologram` |  將全息影像放在提供的<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>所指定的位置。 | 
|  `Update` |  旋轉 cube, 並設定模型矩陣。 | 
|  `Render` |  使用頂點和圖元著色器來呈現框架。 | 

**著色**子資料夾包含四個預設的著色器執行:

|  器  |  說明 | 
|----------|----------|
|  `GeometryShader.hlsl` |  不修改 geometry 的傳遞。 | 
|  `PixelShader.hlsl` |  傳遞色彩資料。 色彩資料會插補並指派給點陣化步驟的圖元。 | 
|  `VertexShader.hlsl` |  在 GPU 上執行頂點處理的簡單著色器。 | 
|  `VPRTVertexShader.hlsl` |  在 GPU 上執行頂點處理的簡單著色器, 已針對 Windows Mixed Reality 身歷聲轉譯進行優化。 | 

`VertexShaderShared.hlsl`包含和`VertexShader.hlsl` `VPRTVertexShader.hlsl`之間共用的通用程式碼。

建立專案時, 會編譯著色器, 而且會在**SpinningCubeRenderer:: CreateDeviceDependentResources**方法中載入。

## <a name="interact-with-your-holograms"></a>與您的全息影像互動

使用者輸入會在**SpatialInputHandler**類別中處理, 這會取得<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>實例並訂閱<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>事件。 這可偵測空中手勢和其他空間輸入事件。

## <a name="update-holographic-content"></a>更新全像攝影內容

您的混合現實應用程式會在遊戲迴圈中更新, 預設會在的**Update**方法`AppMain.cpp`中執行。 **Update**方法會更新場景物件 (例如旋轉的 cube), 並傳回用來取得最新的視圖和投影矩陣並呈現交換鏈的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>物件。

中 `AppMain.cpp`的 Render 方法會採用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> , 並根據目前的應用程式和空間定位狀態, 將目前的框架轉譯為每個全像攝影攝影機。

## <a name="see-also"></a>另請參閱
* [取得 HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [DirectX 中的呈現](rendering-in-directx.md)
* [使用 Visual Studio 來部署和偵錯](using-visual-studio.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [使用全像攝影 DirectX 應用程式中的 XAML](using-xaml-with-holographic-directx-apps.md)
