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
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="2596a-104">建立全像攝影版的 DirectX 專案</span><span class="sxs-lookup"><span data-stu-id="2596a-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="2596a-105">全像攝影版的應用程式建立都是 HoloLens<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平台 (UWP) 應用程式</a>。</span><span class="sxs-lookup"><span data-stu-id="2596a-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="2596a-106">如果目標桌面 Windows Mixed Reality 耳機，您可以建立 UWP 應用程式或 Win32 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2596a-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="2596a-107">DirectX 11 全像攝影版 UWP 應用程式範本十分類似的 DirectX 11 UWP 應用程式範本中;它包含程式迴圈 （或 「 遊戲迴圈 」）， **DeviceResources**類別來管理的 Direct3D 裝置和內容，以及簡化的內容轉譯器類別。</span><span class="sxs-lookup"><span data-stu-id="2596a-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="2596a-108">它也有<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>，就像任何其他的 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2596a-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="2596a-109">混合的實境應用程式，不過，有一些額外功能，未出現在一般的 Direct3D 11 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2596a-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="2596a-110">Windows 全像攝影版的應用程式範本是能夠：</span><span class="sxs-lookup"><span data-stu-id="2596a-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="2596a-111">處理全像攝影版的數位相機與相關聯的 Direct3D 裝置資源。</span><span class="sxs-lookup"><span data-stu-id="2596a-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="2596a-112">從系統擷取相機背景緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2596a-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="2596a-113">處理[視線](gaze.md)輸入，並辨識簡單[筆勢](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="2596a-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="2596a-114">進入全螢幕是立體聲的轉譯模式。</span><span class="sxs-lookup"><span data-stu-id="2596a-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="2596a-115">如何開始？</span><span class="sxs-lookup"><span data-stu-id="2596a-115">How do I get started?</span></span>

<span data-ttu-id="2596a-116">第一個[安裝工具](install-the-tools.md)，下列有關下載 Visual Studio 2017 的指示和 Microsoft HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="2596a-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2017 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="2596a-117">全像攝影版的應用程式範本會包含在相同的安裝程式，為 Microsoft HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="2596a-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="2596a-118">也請確定安裝之前，已選取要安裝的範本選項。</span><span class="sxs-lookup"><span data-stu-id="2596a-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="2596a-119">您現在已準備好建立您的 DirectX 11 Windows Mixed Reality 應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="2596a-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="2596a-120">請注意，若要移除範例內容，標記為註解**DRAW_SAMPLE_CONTENT**中的前置處理器指示詞*pch.h*。</span><span class="sxs-lookup"><span data-stu-id="2596a-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="2596a-121">建立 UWP 專案</span><span class="sxs-lookup"><span data-stu-id="2596a-121">Creating a UWP project</span></span>

<span data-ttu-id="2596a-122">安裝工具之後您可以建立全像攝影版的 DirectX UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="2596a-122">Once the tools are installed you can then create a holographic DirectX UWP project.</span></span> <span data-ttu-id="2596a-123">若要建立新的專案：</span><span class="sxs-lookup"><span data-stu-id="2596a-123">To create a new project:</span></span>
1. <span data-ttu-id="2596a-124">開始**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="2596a-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="2596a-125">從**檔案**功能表上，指向**新增**，然後選取**專案**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="2596a-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="2596a-126">**新的專案** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2596a-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="2596a-127">依序展開**已安裝**左側，展開**視覺化C++** 語言節點。</span><span class="sxs-lookup"><span data-stu-id="2596a-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="2596a-128">瀏覽至**Windows 通用 > Holographic**節點，然後選取**全像攝影版的 DirectX 11 應用程式 (通用 Windows) (C++/WinRT)**。</span><span class="sxs-lookup"><span data-stu-id="2596a-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="2596a-129">請務必將專案範本的名稱包含"(C++/WinRT) 」。</span><span class="sxs-lookup"><span data-stu-id="2596a-129">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="2596a-130">如果沒有，您有舊版安裝的全像攝影版的專案範本。</span><span class="sxs-lookup"><span data-stu-id="2596a-130">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="2596a-131">若要取得最新的專案範本中，[安裝最新的 HoloLens 模擬器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="2596a-131">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="2596a-132">填寫**名稱**並**位置**文字方塊中，然後按一下或點選**確定**。</span><span class="sxs-lookup"><span data-stu-id="2596a-132">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="2596a-133">會建立全像攝影版的應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="2596a-133">The holographic app project is created.</span></span>
6. <span data-ttu-id="2596a-134">開發目標設定為只 HoloLens 2，請確定**目標版本**並**最低版本**設定為**Windows 10 版本 1903年**。</span><span class="sxs-lookup"><span data-stu-id="2596a-134">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="2596a-135">如果您的也目標 HoloLens （第 1 代） 或桌上型電腦的 Windows Mixed Reality 耳機，您可以設定**最低版本**要**Windows 10 版本 1809年**相反地，雖然這需要一些<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本 adapative 檢查</a>在您的程式碼時使用的 HoloLens 2 的新功能。</span><span class="sxs-lookup"><span data-stu-id="2596a-135">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adapative checks</a> in your code when using new features of HoloLens 2.</span></span>

<span data-ttu-id="2596a-136">![全像攝影版的應用程式專案範本，在 Visual Studio 中的螢幕擷取畫面](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="2596a-136">![Screenshot of the holographic app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
<span data-ttu-id="2596a-137">*在 Visual Studio 中的全像攝影版的應用程式專案範本*</span><span class="sxs-lookup"><span data-stu-id="2596a-137">*Holographic app project template in Visual Studio*</span></span>

<span data-ttu-id="2596a-138">範本會產生專案，使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>，C + + 17 語言推演，支援任何符合標準的 C + + 17 編譯器的 Windows 執行階段 api。</span><span class="sxs-lookup"><span data-stu-id="2596a-138">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="2596a-139">專案會示範如何建立世界鎖定 cube 已放入使用者的兩個計量。</span><span class="sxs-lookup"><span data-stu-id="2596a-139">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="2596a-140">使用者可以[空中點選](gestures.md#air-tap)或按下按鈕，將 cube 放在不同的位置所指定的使用者在控制器上[視線](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="2596a-140">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="2596a-141">您可以修改此專案來建立任何 mixed 的 reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2596a-141">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="2596a-142">或者，您可以在其中建立新的專案使用**Visual C#** 全像攝影版的專案範本，此作業取決於 SharpDX。</span><span class="sxs-lookup"><span data-stu-id="2596a-142">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="2596a-143">如果您全像攝影版C#未啟動專案，這是從 Windows 全像攝影版的應用程式範本，您必須從 Windows Mixed Reality 的 ms.fxcompile.targets 檔案複製到C#範本專案，然後匯入在您的.csproj 檔案以編譯 HLSL您新增至您專案的檔案。</span><span class="sxs-lookup"><span data-stu-id="2596a-143">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="2596a-144">檢閱[使用 Visual Studio 部署和偵錯](using-visual-studio.md)如需如何建置和部署範例，您的 HoloLens、 電腦連接的沈浸式裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="2596a-144">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="2596a-145">下列指示的其餘部分將假設您使用C++來建置您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2596a-145">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="2596a-146">UWP 應用程式進入點</span><span class="sxs-lookup"><span data-stu-id="2596a-146">UWP app entry point</span></span>

<span data-ttu-id="2596a-147">在全像攝影版的 UWP 應用程式啟動**wWinMain** AppView.cpp 中的函式。</span><span class="sxs-lookup"><span data-stu-id="2596a-147">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="2596a-148">**WWinMain**函式會建立應用程式的<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>並啟動<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a>使用它。</span><span class="sxs-lookup"><span data-stu-id="2596a-148">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="2596a-149">從**AppView.cpp**:</span><span class="sxs-lookup"><span data-stu-id="2596a-149">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="2596a-150">從那時起，AppView 類別會處理與 Windows 基本輸入的事件、 corewindow，否則事件和傳訊和等等的互動。</span><span class="sxs-lookup"><span data-stu-id="2596a-150">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="2596a-151">它也會建立應用程式所使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="2596a-151">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="2596a-152">建立 Win32 專案</span><span class="sxs-lookup"><span data-stu-id="2596a-152">Creating a Win32 project</span></span>

<span data-ttu-id="2596a-153">最簡單的方式開始建置全像攝影版的專案是採用 Win32 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 範例</a>。</span><span class="sxs-lookup"><span data-stu-id="2596a-153">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="2596a-154">這個 Win32 範例會使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>，C + + 17 語言推演，支援任何符合標準的 C + + 17 編譯器的 Windows 執行階段 api。</span><span class="sxs-lookup"><span data-stu-id="2596a-154">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="2596a-155">專案會示範如何建立世界鎖定 cube 已放入使用者的兩個計量。</span><span class="sxs-lookup"><span data-stu-id="2596a-155">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="2596a-156">使用者可以將 cube 放在不同的位置所指定的使用者在控制器上項目按下按鈕[視線](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="2596a-156">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="2596a-157">您可以修改此專案來建立任何 mixed 的 reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2596a-157">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="2596a-158">Win32 應用程式進入點</span><span class="sxs-lookup"><span data-stu-id="2596a-158">Win32 app entry point</span></span>

<span data-ttu-id="2596a-159">在全像攝影版的 Win32 應用程式啟動**wWinMain** AppMain.cpp 中的函式。</span><span class="sxs-lookup"><span data-stu-id="2596a-159">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="2596a-160">**WWinMain**函式會建立應用程式的 HWND，並啟動其訊息迴圈。</span><span class="sxs-lookup"><span data-stu-id="2596a-160">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="2596a-161">從**AppMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="2596a-161">From **AppMain.cpp**:</span></span>

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

<span data-ttu-id="2596a-162">從那時起，AppMain 類別會處理與基本的視窗訊息，並依此類推的互動。</span><span class="sxs-lookup"><span data-stu-id="2596a-162">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="2596a-163">它也會建立應用程式所使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="2596a-163">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="2596a-164">呈現全像攝影版的內容</span><span class="sxs-lookup"><span data-stu-id="2596a-164">Render holographic content</span></span>

<span data-ttu-id="2596a-165">專案的**內容**資料夾包含類別，可以轉譯在全像投影[全像攝影版的空間](getting-a-holographicspace.md)。</span><span class="sxs-lookup"><span data-stu-id="2596a-165">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="2596a-166">在範本中的預設全像圖是兩個使用者俖籇所下的旋轉立方體。</span><span class="sxs-lookup"><span data-stu-id="2596a-166">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="2596a-167">繪製這個 cube 中實作**SpinningCubeRenderer.cpp**，其中包含這些金鑰的方法：</span><span class="sxs-lookup"><span data-stu-id="2596a-167">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="2596a-168">方法</span><span class="sxs-lookup"><span data-stu-id="2596a-168">Method</span></span>  |  <span data-ttu-id="2596a-169">說明</span><span class="sxs-lookup"><span data-stu-id="2596a-169">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="2596a-170">載入著色器，並建立 cube 網狀結構。</span><span class="sxs-lookup"><span data-stu-id="2596a-170">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="2596a-171">所指定的位置放置闀<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>。</span><span class="sxs-lookup"><span data-stu-id="2596a-171">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="2596a-172">旋轉立方體，並設定模型的矩陣。</span><span class="sxs-lookup"><span data-stu-id="2596a-172">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="2596a-173">呈現的畫面格使用的端點和像素著色器。</span><span class="sxs-lookup"><span data-stu-id="2596a-173">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="2596a-174">**著色器**子資料夾包含四個預設的著色器實作：</span><span class="sxs-lookup"><span data-stu-id="2596a-174">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="2596a-175">著色器</span><span class="sxs-lookup"><span data-stu-id="2596a-175">Shader</span></span>  |  <span data-ttu-id="2596a-176">說明</span><span class="sxs-lookup"><span data-stu-id="2596a-176">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="2596a-177">這種傳遞離開的未經修改的幾何。</span><span class="sxs-lookup"><span data-stu-id="2596a-177">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="2596a-178">若要通過的色彩資料。</span><span class="sxs-lookup"><span data-stu-id="2596a-178">Passes through the color data.</span></span> <span data-ttu-id="2596a-179">插補色彩資料，並指派給像素在點陣化步驟。</span><span class="sxs-lookup"><span data-stu-id="2596a-179">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="2596a-180">若要執行 GPU 上的頂點處理簡單的著色器。</span><span class="sxs-lookup"><span data-stu-id="2596a-180">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="2596a-181">若要執行，適用於 Windows Mixed Reality 是立體聲轉譯在 GPU 上的頂點處理簡單的著色器。</span><span class="sxs-lookup"><span data-stu-id="2596a-181">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="2596a-182">`VertexShaderShared.hlsl` 包含常見的程式碼之間共用`VertexShader.hlsl`和`VPRTVertexShader.hlsl`。</span><span class="sxs-lookup"><span data-stu-id="2596a-182">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="2596a-183">著色器編譯時建置專案時，它們是在載入**SpinningCubeRenderer::CreateDeviceDependentResources**方法。</span><span class="sxs-lookup"><span data-stu-id="2596a-183">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="2596a-184">與您全像投影互動</span><span class="sxs-lookup"><span data-stu-id="2596a-184">Interact with your holograms</span></span>

<span data-ttu-id="2596a-185">在處理使用者輸入**SpatialInputHandler**類別，會遭到<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>執行個體，並訂閱<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>事件。</span><span class="sxs-lookup"><span data-stu-id="2596a-185">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="2596a-186">這可讓偵測空中點選手勢和其他空間的輸入的事件。</span><span class="sxs-lookup"><span data-stu-id="2596a-186">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="2596a-187">更新全像攝影版的內容</span><span class="sxs-lookup"><span data-stu-id="2596a-187">Update holographic content</span></span>

<span data-ttu-id="2596a-188">您在遊戲迴圈中，其預設實作中的混合的實境應用程式更新**更新**方法中的`AppMain.cpp`。</span><span class="sxs-lookup"><span data-stu-id="2596a-188">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="2596a-189">**更新**方法會更新場景物件，例如旋轉立方體，並傳回<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>用來取得最新的檢視和投影矩陣，並呈現交換鏈結的物件。</span><span class="sxs-lookup"><span data-stu-id="2596a-189">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="2596a-190">**呈現**方法中的`AppMain.cpp`採用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>並呈現目前的畫面格，以每個全像攝影版的相機，根據目前的應用程式與空間位置的狀態。</span><span class="sxs-lookup"><span data-stu-id="2596a-190">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="2596a-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2596a-191">See also</span></span>
* [<span data-ttu-id="2596a-192">取得 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="2596a-192">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="2596a-193"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="2596a-193"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="2596a-194">在 DirectX 中轉譯</span><span class="sxs-lookup"><span data-stu-id="2596a-194">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="2596a-195">使用 Visual Studio 來部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="2596a-195">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="2596a-196">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="2596a-196">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="2596a-197">使用全像攝影版的 DirectX 應用程式中的 XAML</span><span class="sxs-lookup"><span data-stu-id="2596a-197">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)
