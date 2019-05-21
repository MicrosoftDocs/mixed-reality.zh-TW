---
title: 匯出和建置 Unity Visual Studio 方案
description: 本文概述從 Unity 匯出您的混合的實境專案，因此您可以建置並部署在 Visual Studio 中。
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity，visual studio 中，匯出、 建置、 部署
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596380"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a><span data-ttu-id="05c57-104">匯出和建置 Unity Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="05c57-104">Exporting and building a Unity Visual Studio solution</span></span>

<span data-ttu-id="05c57-105">如果您不想在您的應用程式中使用系統鍵盤，我們建議是使用*D3D*您的應用程式會使用稍微較少的記憶體，並具有稍微快的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="05c57-105">If you don't intend on using the system keyboard in your application, our recommendation is to use *D3D* as your application will use slightly less memory and have a slightly faster launch time.</span></span> <span data-ttu-id="05c57-106">如果您使用 TouchScreenKeyboard API 專案中使用系統鍵盤，您需要將匯出為*XAML*。</span><span class="sxs-lookup"><span data-stu-id="05c57-106">If you are using the TouchScreenKeyboard API in your project to use the system keyboard, you need to export as *XAML*.</span></span>

## <a name="how-to-export-from-unity"></a><span data-ttu-id="05c57-107">如何從 Unity 匯出</span><span class="sxs-lookup"><span data-stu-id="05c57-107">How to export from Unity</span></span>

<span data-ttu-id="05c57-108">![Unity 組建設定](images/unitybuildsettings-300px.png)</span><span class="sxs-lookup"><span data-stu-id="05c57-108">![Unity build settings](images/unitybuildsettings-300px.png)</span></span><br>
<span data-ttu-id="05c57-109">*Unity 組建設定*</span><span class="sxs-lookup"><span data-stu-id="05c57-109">*Unity build settings*</span></span>

1. <span data-ttu-id="05c57-110">當您準備好從 Unity 匯出您的專案時，開啟**檔案**功能表，然後選取**組建設定...**</span><span class="sxs-lookup"><span data-stu-id="05c57-110">When you are ready to export your project from Unity, open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="05c57-111">按一下 **加入開啟的場景**將場景新增至組建。</span><span class="sxs-lookup"><span data-stu-id="05c57-111">Click **Add Open Scenes** to add your scene to the build.</span></span>
3. <span data-ttu-id="05c57-112">在 [**組建設定**] 對話方塊中，選擇要匯出的 HoloLens 的下列選項：</span><span class="sxs-lookup"><span data-stu-id="05c57-112">In the **Build Settings** dialog, choose the following options to export for HoloLens:</span></span>
   * <span data-ttu-id="05c57-113">**平台：\*\**通用 Windows 平台*，並確定選取**切換平台\*\*您所選項目的才會生效。</span><span class="sxs-lookup"><span data-stu-id="05c57-113">**Platform:** *Universal Windows Platform* and be sure to select **Switch Platform** for your selection to take effect.</span></span>
   * <span data-ttu-id="05c57-114">**SDK:**  *通用的 10*。</span><span class="sxs-lookup"><span data-stu-id="05c57-114">**SDK:** *Universal 10*.</span></span>
   * <span data-ttu-id="05c57-115">**UWP 建置型別：**  *D3D*。</span><span class="sxs-lookup"><span data-stu-id="05c57-115">**UWP Build Type:** *D3D*.</span></span>
4. <span data-ttu-id="05c57-116">**選擇性**:**UnityC#專案：** 檢查。</span><span class="sxs-lookup"><span data-stu-id="05c57-116">**Optional**: **Unity C# Projects:** Checked.</span></span>

>[!NOTE]
><span data-ttu-id="05c57-117">核取此方塊，可讓您：</span><span class="sxs-lookup"><span data-stu-id="05c57-117">Checking this box allows you to:</span></span>
>* <span data-ttu-id="05c57-118">偵錯您的應用程式，Visual Studio 遠端偵錯工具中。</span><span class="sxs-lookup"><span data-stu-id="05c57-118">Debug your app in the Visual Studio remote debugger.</span></span>
>* <span data-ttu-id="05c57-119">Unity 中編輯指令碼C#專案時使用 IntelliSense 的 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="05c57-119">Edit scripts in the Unity C# project while using IntelliSense for WinRT APIs.</span></span>

5. <span data-ttu-id="05c57-120">從**組建設定...** 視窗中，開啟**播放程式設定...**</span><span class="sxs-lookup"><span data-stu-id="05c57-120">From the **Build Settings...** window, open **Player Settings...**</span></span>
6. <span data-ttu-id="05c57-121">選取 [**通用 Windows 平台設定**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="05c57-121">Select the **Settings for Universal Windows Platform** tab.</span></span>
7. <span data-ttu-id="05c57-122">依序展開**XR 設定**群組。</span><span class="sxs-lookup"><span data-stu-id="05c57-122">Expand the **XR Settings** group.</span></span>
8. <span data-ttu-id="05c57-123">在  **XR 設定**區段中，按一下**虛擬實境支援**核取方塊以加入新**虛擬實境裝置**清單，並確認 **「 Windows 混合式但實際上"** 列為支援的裝置。</span><span class="sxs-lookup"><span data-stu-id="05c57-123">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list and confirm **"Windows Mixed Reality"** is listed as a supported device.</span></span>
9. <span data-ttu-id="05c57-124">返回**組建設定**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="05c57-124">Return to the **Build Settings** dialog.</span></span>
10. <span data-ttu-id="05c57-125">選取 **建置**。</span><span class="sxs-lookup"><span data-stu-id="05c57-125">Select **Build**.</span></span>
11. <span data-ttu-id="05c57-126">在出現 [Windows 檔案總管] 對話方塊中，建立新的資料夾，保留 Unity 的組建輸出。</span><span class="sxs-lookup"><span data-stu-id="05c57-126">In the Windows Explorer dialog that appears, create a new folder to hold Unity's build output.</span></span> <span data-ttu-id="05c57-127">一般而言，我們將資料夾命名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="05c57-127">Generally, we name the folder "App".</span></span>
12. <span data-ttu-id="05c57-128">選取新建立的資料夾，然後按一下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="05c57-128">Select the newly created folder and click **Select Folder**.</span></span>
13. <span data-ttu-id="05c57-129">建置完成之後 Unity，Windows 檔案總管 視窗會開啟專案根目錄。</span><span class="sxs-lookup"><span data-stu-id="05c57-129">Once Unity has finished building, a Windows Explorer window will open to the project root directory.</span></span> <span data-ttu-id="05c57-130">瀏覽至新建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="05c57-130">Navigate into the newly created folder.</span></span>
14. <span data-ttu-id="05c57-131">開啟產生的 Visual Studio 解決方案檔案位於此資料夾。</span><span class="sxs-lookup"><span data-stu-id="05c57-131">Open the generated Visual Studio solution file located inside this folder.</span></span>

## <a name="when-to-re-export-from-unity"></a><span data-ttu-id="05c57-132">重新匯出從 Unity 的時機</span><span class="sxs-lookup"><span data-stu-id="05c57-132">When to re-export from Unity</span></span>

<span data-ttu-id="05c57-133">檢查 」C#專案 」 核取方塊，當從 Unity 匯出您的應用程式建立 Visual Studio 方案，包含所有您的 Unity 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="05c57-133">Checking the "C# Projects" checkbox when exporting your app from Unity creates a Visual Studio solution that includes all your Unity script files.</span></span> <span data-ttu-id="05c57-134">這可讓您逐一查看您指令碼，而不重新匯出從 Unity。</span><span class="sxs-lookup"><span data-stu-id="05c57-134">This allows you to iterate on your scripts without re-exporting from Unity.</span></span> <span data-ttu-id="05c57-135">不過，如果您想要對您不只變更的指令碼內容的專案中的變更，您必須從 Unity 重新匯出。</span><span class="sxs-lookup"><span data-stu-id="05c57-135">However, if you want to make changes to your project that aren't just changing the contents of scripts, you will need to re-export from Unity.</span></span> <span data-ttu-id="05c57-136">有時候您需要重新匯出從 Unity 的一些範例包括：</span><span class="sxs-lookup"><span data-stu-id="05c57-136">Some examples of times you need to re-export from Unity are:</span></span>
* <span data-ttu-id="05c57-137">您可以新增或移除在 [專案] 索引標籤中的資產。</span><span class="sxs-lookup"><span data-stu-id="05c57-137">You add or remove assets in the Project tab.</span></span>
* <span data-ttu-id="05c57-138">您變更偵測器索引標籤中的任何值。</span><span class="sxs-lookup"><span data-stu-id="05c57-138">You change any value in the Inspector tab.</span></span>
* <span data-ttu-id="05c57-139">您可以新增或移除 [階層] 索引標籤中的物件。</span><span class="sxs-lookup"><span data-stu-id="05c57-139">You add or remove objects from the Hierarchy tab.</span></span>
* <span data-ttu-id="05c57-140">您變更任何 Unity 專案設定</span><span class="sxs-lookup"><span data-stu-id="05c57-140">You change any Unity project settings</span></span>

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a><span data-ttu-id="05c57-141">建置和部署 Unity Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="05c57-141">Building and deploying a Unity Visual Studio solution</span></span>

<span data-ttu-id="05c57-142">建置和部署應用程式的其餘部分會在[Visual Studio](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="05c57-142">The remainder of building and deploying apps happens in [Visual Studio](using-visual-studio.md).</span></span> <span data-ttu-id="05c57-143">您必須指定 Unity 建置組態。</span><span class="sxs-lookup"><span data-stu-id="05c57-143">You will need to specify a Unity build configuration.</span></span> <span data-ttu-id="05c57-144">Unity 的命名慣例，可能會有所不同是通常用來在 Visual Studio 中：</span><span class="sxs-lookup"><span data-stu-id="05c57-144">Unity's naming conventions may differ from what you're usually used to in Visual Studio:</span></span>

|  <span data-ttu-id="05c57-145">組態</span><span class="sxs-lookup"><span data-stu-id="05c57-145">Configuration</span></span>  |  <span data-ttu-id="05c57-146">說明</span><span class="sxs-lookup"><span data-stu-id="05c57-146">Explanation</span></span> | 
|----------|----------|
|  <span data-ttu-id="05c57-147">偵錯</span><span class="sxs-lookup"><span data-stu-id="05c57-147">Debug</span></span>  |  <span data-ttu-id="05c57-148">關閉所有的最佳化和分析工具已啟用。</span><span class="sxs-lookup"><span data-stu-id="05c57-148">All optimizations off and the profiler is enabled.</span></span> <span data-ttu-id="05c57-149">用來偵錯指令碼。</span><span class="sxs-lookup"><span data-stu-id="05c57-149">Used to debug scripts.</span></span> | 
|  <span data-ttu-id="05c57-150">主檔</span><span class="sxs-lookup"><span data-stu-id="05c57-150">Master</span></span>  |  <span data-ttu-id="05c57-151">所有的最佳化已開啟，且已停用分析工具。</span><span class="sxs-lookup"><span data-stu-id="05c57-151">All optimizations are turned on and the profiler is disabled.</span></span> <span data-ttu-id="05c57-152">用來提交至市集的應用程式。</span><span class="sxs-lookup"><span data-stu-id="05c57-152">Used to submit apps to the Store.</span></span> | 
|  <span data-ttu-id="05c57-153">發行</span><span class="sxs-lookup"><span data-stu-id="05c57-153">Release</span></span>  |  <span data-ttu-id="05c57-154">所有的最佳化已開啟，且已啟用分析工具。</span><span class="sxs-lookup"><span data-stu-id="05c57-154">All optimizations are turned on and the profiler is enabled.</span></span> <span data-ttu-id="05c57-155">用來評估應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="05c57-155">Used to evaluate app performance.</span></span> | 

<span data-ttu-id="05c57-156">請注意，上述清單為一般的觸發程序，將會導致 Visual Studio 專案，需要產生的子集。</span><span class="sxs-lookup"><span data-stu-id="05c57-156">Note, the above list is a subset of the common triggers that will cause the Visual Studio project to need to be generated.</span></span> <span data-ttu-id="05c57-157">一般情況下，編輯 Visual Studio 中的.cs 檔案，將不需要專案，以從 Unity 內重新產生。</span><span class="sxs-lookup"><span data-stu-id="05c57-157">In general, editing .cs files from within Visual Studio will not require the project to be regenerated from within Unity.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="05c57-158">疑難排解</span><span class="sxs-lookup"><span data-stu-id="05c57-158">Troubleshooting</span></span>

<span data-ttu-id="05c57-159">如果您發現，編輯您的.cs 檔案無法辨識您的 Visual Studio 專案中，請確定 「 UnityC#專案 」 會檢查當您從 Unity 的 [建置] 功能表，會在產生的 VS 專案時。</span><span class="sxs-lookup"><span data-stu-id="05c57-159">If you find that edits to your .cs files are not being recognized in your Visual Studio project, ensure that "Unity C# Projects" is checked when you generate the VS project from Unity's Build menu.</span></span>
