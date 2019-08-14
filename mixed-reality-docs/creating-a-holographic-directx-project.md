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
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="183aa-104">建立全像攝影 DirectX 專案</span><span class="sxs-lookup"><span data-stu-id="183aa-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="183aa-105">您為 HoloLens 建立的全像攝影應用程式將會是<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平臺 (UWP) 應用程式</a>。</span><span class="sxs-lookup"><span data-stu-id="183aa-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="183aa-106">如果以桌面 Windows Mixed Reality 耳機為目標, 您可以建立 UWP 應用程式或 Win32 應用程式。</span><span class="sxs-lookup"><span data-stu-id="183aa-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="183aa-107">DirectX 11 全像攝影版 UWP 應用程式範本與 DirectX 11 UWP 應用程式範本十分相似;其中包含一個程式迴圈 (或「遊戲迴圈」)、一個**DeviceResources**類別來管理 Direct3D 裝置和內容, 以及一個簡化的內容轉譯器類別。</span><span class="sxs-lookup"><span data-stu-id="183aa-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="183aa-108">它也有<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, 就像任何其他 UWP 應用程式一樣。</span><span class="sxs-lookup"><span data-stu-id="183aa-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="183aa-109">不過, mixed reality 應用程式具有一些不存在於一般 Direct3D 11 UWP 應用程式中的額外功能。</span><span class="sxs-lookup"><span data-stu-id="183aa-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="183aa-110">Windows 全像應用程式範本可以:</span><span class="sxs-lookup"><span data-stu-id="183aa-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="183aa-111">處理與全像攝影相機相關聯的 Direct3D 裝置資源。</span><span class="sxs-lookup"><span data-stu-id="183aa-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="183aa-112">從系統取出相機背面緩衝區。</span><span class="sxs-lookup"><span data-stu-id="183aa-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="183aa-113">處理[注視](gaze.md)的輸入, 並辨識簡單[手勢](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="183aa-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="183aa-114">進入全螢幕身歷聲轉譯模式。</span><span class="sxs-lookup"><span data-stu-id="183aa-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="183aa-115">如何? 開始使用了嗎？</span><span class="sxs-lookup"><span data-stu-id="183aa-115">How do I get started?</span></span>

<span data-ttu-id="183aa-116">請依照下載 Visual Studio 2019 和 Microsoft HoloLens 模擬器中的指示, 先[安裝這些工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="183aa-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2019 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="183aa-117">全像攝影應用程式範本包含在與 Microsoft HoloLens 模擬器相同的安裝程式中。</span><span class="sxs-lookup"><span data-stu-id="183aa-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="183aa-118">此外, 請確定已選取 [安裝範本] 選項, 然後再安裝。</span><span class="sxs-lookup"><span data-stu-id="183aa-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="183aa-119">現在您已經準備好建立 DirectX 11 Windows Mixed Reality 應用程式!</span><span class="sxs-lookup"><span data-stu-id="183aa-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="183aa-120">請注意, 若要移除範例內容, 請將*pch*中的**DRAW_SAMPLE_CONTENT**預處理器指示詞標記為批註。</span><span class="sxs-lookup"><span data-stu-id="183aa-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="183aa-121">建立 UWP 專案</span><span class="sxs-lookup"><span data-stu-id="183aa-121">Creating a UWP project</span></span>

<span data-ttu-id="183aa-122">[安裝工具](install-the-tools.md)之後, 您就可以建立全像的 DirectX UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="183aa-122">Once the [tools are installed](install-the-tools.md) you can then create a holographic DirectX UWP project.</span></span>

<span data-ttu-id="183aa-123">若要建立新的專案:</span><span class="sxs-lookup"><span data-stu-id="183aa-123">To create a new project:</span></span>
1. <span data-ttu-id="183aa-124">啟動**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="183aa-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="183aa-125">從 [檔案] 功能表, 指向 [**新增**], 然後從內容功能表中選取 [**專案**]。</span><span class="sxs-lookup"><span data-stu-id="183aa-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="183aa-126">[**新增專案**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="183aa-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="183aa-127">展開左側的 [**已安裝**], 然後展開 [**視覺效果C++** 語言] 節點。</span><span class="sxs-lookup"><span data-stu-id="183aa-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="183aa-128">流覽至 [ **Windows 通用 >** 全像攝影] 節點, 然後選取 [全像**C++/WinRT] [DirectX 11 應用程式 (通用 Windows)** ]。</span><span class="sxs-lookup"><span data-stu-id="183aa-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="183aa-129">![Visual Studio 中的全像「 C++DirectX 11/WinRT UWP 應用程式」專案範本的螢幕擷取畫面](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="183aa-129">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
   <span data-ttu-id="183aa-130">*Visual Studio 中的C++全息版 DirectX 11/WinRT UWP 應用程式專案範本*</span><span class="sxs-lookup"><span data-stu-id="183aa-130">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="183aa-131">請確定專案範本的名稱包含 "(C++/WinRT)"。</span><span class="sxs-lookup"><span data-stu-id="183aa-131">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="183aa-132">如果沒有, 則會安裝較舊版本的全像攝影專案範本。</span><span class="sxs-lookup"><span data-stu-id="183aa-132">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="183aa-133">若要取得最新的專案範本, 請[安裝最新的 HoloLens 模擬器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="183aa-133">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="183aa-134">填寫 [**名稱**] 和 [**位置**] 文字方塊, 然後按一下或點擊 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="183aa-134">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="183aa-135">會建立全像攝影應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="183aa-135">The holographic app project is created.</span></span>
6. <span data-ttu-id="183aa-136">針對僅以 HoloLens 2 為目標的開發, 請確定 [**目標版本**] 和 [**最低版本**] 設定為 [ **Windows 10, 版本 1903**]。</span><span class="sxs-lookup"><span data-stu-id="183aa-136">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="183aa-137">如果您也以 HoloLens (第1代) 或桌面 Windows Mixed Reality 耳機為目標, 則可以改為將**最低版本**設定為**windows 10 版本 1809** , 但在使用 new 時, 您的程式碼中需要一些版本調適型<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">檢查</a>HoloLens 2 的功能。</span><span class="sxs-lookup"><span data-stu-id="183aa-137">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="183aa-138">![將 Windows 10 (版本 1903) 設為目標和最低版本的螢幕擷取畫面](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="183aa-138">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="183aa-139">*將 **Windows 10 (版本 1903)** 設定為目標和最低版本*</span><span class="sxs-lookup"><span data-stu-id="183aa-139">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="183aa-140">如果您沒有看到 [ **windows 10, 版本 1903** ] 選項, 則不會安裝最新的 WINDOWS 10 SDK。</span><span class="sxs-lookup"><span data-stu-id="183aa-140">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="183aa-141">若要讓此選項出現, 請<a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">安裝 Windows 10 SDK 的版本10.0.18362.0 或更新版本</a>。</span><span class="sxs-lookup"><span data-stu-id="183aa-141">To get this option to appear, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="183aa-142">此範本會使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>產生專案, 這是支援任何符合標準之 c + + 17 編譯器的 Windows 執行階段 api 的 c + + 17 語言投影。</span><span class="sxs-lookup"><span data-stu-id="183aa-142">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="183aa-143">此專案會示範如何建立世界鎖定的 cube, 這是由使用者放置兩個計量。</span><span class="sxs-lookup"><span data-stu-id="183aa-143">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="183aa-144">使用者可以[按一下](gestures.md#air-tap)或按下控制器上的按鈕, 將 cube 放在使用者[注視](gaze.md)所指定的不同位置。</span><span class="sxs-lookup"><span data-stu-id="183aa-144">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="183aa-145">您可以修改此專案, 以建立任何混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="183aa-145">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="183aa-146">或者, 您可以使用以 SharpDX 為基礎的**Visual C#** 全像投影專案範本來建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="183aa-146">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="183aa-147">如果您的C#全像攝影專案未從 windows 全像攝影應用程式範本開始, 您必須從 Windows Mixed Reality C#範本專案複製 fxcompile 檔案, 並將它匯入 .csproj 檔案中, 才能編譯 HLSL您新增至專案的檔案。</span><span class="sxs-lookup"><span data-stu-id="183aa-147">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="183aa-148">請參閱[使用 Visual Studio 部署和調試](using-visual-studio.md)程式, 以瞭解如何建立範例, 並將其部署至您的 HoloLens、已連接沉浸式裝置的電腦或模擬器。</span><span class="sxs-lookup"><span data-stu-id="183aa-148">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="183aa-149">下面的其餘指示會假設您使用C++來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="183aa-149">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="183aa-150">UWP 應用程式進入點</span><span class="sxs-lookup"><span data-stu-id="183aa-150">UWP app entry point</span></span>

<span data-ttu-id="183aa-151">您的全像攝影 UWP 應用程式會在 AppView 中的**wWinMain**函式開始。</span><span class="sxs-lookup"><span data-stu-id="183aa-151">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="183aa-152">**WWinMain**函式會建立應用程式的<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> , 並使用它來啟動<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 。</span><span class="sxs-lookup"><span data-stu-id="183aa-152">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="183aa-153">從**AppView**:</span><span class="sxs-lookup"><span data-stu-id="183aa-153">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="183aa-154">從該時間點開始, AppView 類別會處理與 Windows 基本輸入事件、CoreWindow 事件和訊息等的互動。</span><span class="sxs-lookup"><span data-stu-id="183aa-154">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="183aa-155">它也會建立您的應用程式所使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="183aa-155">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="183aa-156">建立 Win32 專案</span><span class="sxs-lookup"><span data-stu-id="183aa-156">Creating a Win32 project</span></span>

<span data-ttu-id="183aa-157">開始建立 Win32 全像投影專案最簡單的方式, 就是調整<a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram*的 win32 範例</a>。</span><span class="sxs-lookup"><span data-stu-id="183aa-157">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="183aa-158">這個 Win32 範例會使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, 這是支援任何符合標準之 c + + 17 編譯器的 Windows 執行階段 api 的 c + + 17 語言投影。</span><span class="sxs-lookup"><span data-stu-id="183aa-158">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="183aa-159">此專案會示範如何建立世界鎖定的 cube, 這是由使用者放置兩個計量。</span><span class="sxs-lookup"><span data-stu-id="183aa-159">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="183aa-160">使用者可以按下控制器上的按鈕, 將 cube 放在使用者[注視](gaze.md)所指定的不同位置。</span><span class="sxs-lookup"><span data-stu-id="183aa-160">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="183aa-161">您可以修改此專案, 以建立任何混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="183aa-161">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="183aa-162">Win32 應用程式進入點</span><span class="sxs-lookup"><span data-stu-id="183aa-162">Win32 app entry point</span></span>

<span data-ttu-id="183aa-163">您的全像的 Win32 應用程式會從 AppMain 中的**wWinMain**函式開始。</span><span class="sxs-lookup"><span data-stu-id="183aa-163">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="183aa-164">**WWinMain**函數會建立應用程式的 HWND 並啟動其訊息迴圈。</span><span class="sxs-lookup"><span data-stu-id="183aa-164">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="183aa-165">從**AppMain**:</span><span class="sxs-lookup"><span data-stu-id="183aa-165">From **AppMain.cpp**:</span></span>

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

<span data-ttu-id="183aa-166">從該時間點開始, AppMain 類別會處理與基本視窗訊息的互動, 依此類推。</span><span class="sxs-lookup"><span data-stu-id="183aa-166">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="183aa-167">它也會建立您的應用程式所使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="183aa-167">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="183aa-168">呈現全像攝影內容</span><span class="sxs-lookup"><span data-stu-id="183aa-168">Render holographic content</span></span>

<span data-ttu-id="183aa-169">專案的**Content**資料夾包含可在全像攝影[空間](getting-a-holographicspace.md)中轉譯全息影像的類別。</span><span class="sxs-lookup"><span data-stu-id="183aa-169">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="183aa-170">範本中的預設全息影像是一個旋轉的 cube, 這會將兩個計量放在使用者之外。</span><span class="sxs-lookup"><span data-stu-id="183aa-170">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="183aa-171">繪製此 cube 會在**SpinningCubeRenderer**中實作為下列主要方法:</span><span class="sxs-lookup"><span data-stu-id="183aa-171">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="183aa-172">方法</span><span class="sxs-lookup"><span data-stu-id="183aa-172">Method</span></span>  |  <span data-ttu-id="183aa-173">說明</span><span class="sxs-lookup"><span data-stu-id="183aa-173">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="183aa-174">載入著色器並建立 cube 網格。</span><span class="sxs-lookup"><span data-stu-id="183aa-174">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="183aa-175">將全息影像放在提供的<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="183aa-175">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="183aa-176">旋轉 cube, 並設定模型矩陣。</span><span class="sxs-lookup"><span data-stu-id="183aa-176">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="183aa-177">使用頂點和圖元著色器來呈現框架。</span><span class="sxs-lookup"><span data-stu-id="183aa-177">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="183aa-178">**著色**子資料夾包含四個預設的著色器執行:</span><span class="sxs-lookup"><span data-stu-id="183aa-178">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="183aa-179">器</span><span class="sxs-lookup"><span data-stu-id="183aa-179">Shader</span></span>  |  <span data-ttu-id="183aa-180">說明</span><span class="sxs-lookup"><span data-stu-id="183aa-180">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="183aa-181">不修改 geometry 的傳遞。</span><span class="sxs-lookup"><span data-stu-id="183aa-181">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="183aa-182">傳遞色彩資料。</span><span class="sxs-lookup"><span data-stu-id="183aa-182">Passes through the color data.</span></span> <span data-ttu-id="183aa-183">色彩資料會插補並指派給點陣化步驟的圖元。</span><span class="sxs-lookup"><span data-stu-id="183aa-183">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="183aa-184">在 GPU 上執行頂點處理的簡單著色器。</span><span class="sxs-lookup"><span data-stu-id="183aa-184">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="183aa-185">在 GPU 上執行頂點處理的簡單著色器, 已針對 Windows Mixed Reality 身歷聲轉譯進行優化。</span><span class="sxs-lookup"><span data-stu-id="183aa-185">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="183aa-186">`VertexShaderShared.hlsl`包含和`VertexShader.hlsl` `VPRTVertexShader.hlsl`之間共用的通用程式碼。</span><span class="sxs-lookup"><span data-stu-id="183aa-186">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="183aa-187">建立專案時, 會編譯著色器, 而且會在**SpinningCubeRenderer:: CreateDeviceDependentResources**方法中載入。</span><span class="sxs-lookup"><span data-stu-id="183aa-187">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="183aa-188">與您的全息影像互動</span><span class="sxs-lookup"><span data-stu-id="183aa-188">Interact with your holograms</span></span>

<span data-ttu-id="183aa-189">使用者輸入會在**SpatialInputHandler**類別中處理, 這會取得<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>實例並訂閱<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>事件。</span><span class="sxs-lookup"><span data-stu-id="183aa-189">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="183aa-190">這可偵測空中手勢和其他空間輸入事件。</span><span class="sxs-lookup"><span data-stu-id="183aa-190">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="183aa-191">更新全像攝影內容</span><span class="sxs-lookup"><span data-stu-id="183aa-191">Update holographic content</span></span>

<span data-ttu-id="183aa-192">您的混合現實應用程式會在遊戲迴圈中更新, 預設會在的**Update**方法`AppMain.cpp`中執行。</span><span class="sxs-lookup"><span data-stu-id="183aa-192">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="183aa-193">**Update**方法會更新場景物件 (例如旋轉的 cube), 並傳回用來取得最新的視圖和投影矩陣並呈現交換鏈的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>物件。</span><span class="sxs-lookup"><span data-stu-id="183aa-193">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="183aa-194">中 `AppMain.cpp`的 Render 方法會採用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> , 並根據目前的應用程式和空間定位狀態, 將目前的框架轉譯為每個全像攝影攝影機。</span><span class="sxs-lookup"><span data-stu-id="183aa-194">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="183aa-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="183aa-195">See also</span></span>
* [<span data-ttu-id="183aa-196">取得 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="183aa-196">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="183aa-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="183aa-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="183aa-198">DirectX 中的呈現</span><span class="sxs-lookup"><span data-stu-id="183aa-198">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="183aa-199">使用 Visual Studio 來部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="183aa-199">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="183aa-200">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="183aa-200">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="183aa-201">使用全像攝影 DirectX 應用程式中的 XAML</span><span class="sxs-lookup"><span data-stu-id="183aa-201">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)
