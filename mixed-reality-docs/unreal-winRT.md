---
title: Unreal 中的 WinRT
description: 概述 Unreal Engine 的空間音訊外掛程式。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 串流, 遠端, 混合實境, 開發, 開始使用, 功能, 新專案, 模擬器, 文件, 指南, 功能, 全像投影, 遊戲開發
ms.openlocfilehash: 7a64002a5fa48bb589ab113f0a8dc1bfcb92d535
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408216"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="55a77-104">Unreal 中的 WinRT</span><span class="sxs-lookup"><span data-stu-id="55a77-104">WinRT in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="55a77-105">概觀</span><span class="sxs-lookup"><span data-stu-id="55a77-105">Overview</span></span>

<span data-ttu-id="55a77-106">在您的 HoloLens 開發過程中，您可能需要使用 WinRT 來撰寫功能。</span><span class="sxs-lookup"><span data-stu-id="55a77-106">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="55a77-107">例如，在 HoloLens 應用程式中開啟檔案對話方塊需要 winrt/Windows. FileSavePicker 標頭檔中的檔案。</span><span class="sxs-lookup"><span data-stu-id="55a77-107">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span>  <span data-ttu-id="55a77-108">由於 Unreal 不會以原生方式編譯 WinRT 程式碼，因此您的工作就是建立個別的二進位檔，並可供 Unreal 的組建系統使用。</span><span class="sxs-lookup"><span data-stu-id="55a77-108">Since Unreal doesn't natively compile WinRT code, it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="55a77-109">本教學課程將逐步引導您完成這類案例。</span><span class="sxs-lookup"><span data-stu-id="55a77-109">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="55a77-110">目標</span><span class="sxs-lookup"><span data-stu-id="55a77-110">Objectives</span></span>
- <span data-ttu-id="55a77-111">建立可開啟 FileSaveDialogue 的通用 Windows DLL</span><span class="sxs-lookup"><span data-stu-id="55a77-111">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="55a77-112">將該 DLL 連結至 Unreal 遊戲專案</span><span class="sxs-lookup"><span data-stu-id="55a77-112">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="55a77-113">使用新的 DLL，從 Unreal 藍圖將檔案儲存在 HoloLens</span><span class="sxs-lookup"><span data-stu-id="55a77-113">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="55a77-114">開始使用</span><span class="sxs-lookup"><span data-stu-id="55a77-114">Getting started</span></span>
1. <span data-ttu-id="55a77-115">檢查您是否已安裝所有[必要的工具](unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="55a77-115">Check that you have all [required tools](unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="55a77-116">[建立新的 Unreal 專案](unreal-uxt-ch2.md#creating-a-new-unreal-project)，並將其命名為**Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="55a77-116">[Create a new Unreal project](unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="55a77-117">啟用適用于 HoloLens 開發的[必要外掛程式](unreal-uxt-ch2.md#enabling-required-plugins)</span><span class="sxs-lookup"><span data-stu-id="55a77-117">Enable the [required plugins](unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="55a77-118">部署至裝置或模擬器[的設定](unreal-uxt-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="55a77-118">[Setup for deployment](unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="55a77-119">建立 WinRT DLL</span><span class="sxs-lookup"><span data-stu-id="55a77-119">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="55a77-120">開啟新的 Visual Studio 專案，並在與 Unreal 遊戲的**uproject**檔案相同的目錄中建立**DLL （通用 Windows）** 專案。</span><span class="sxs-lookup"><span data-stu-id="55a77-120">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![建立 DLL](images/unreal-winrt-img-01.png)

2. <span data-ttu-id="55a77-122">將專案命名為**HoloLensWinrtDLL** ，並將位置設定為 Unreal 遊戲 uproject 檔案的**ThirdParty**子目錄。</span><span class="sxs-lookup"><span data-stu-id="55a77-122">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="55a77-123">選取 **[將方案和專案放在相同的目錄中**]，以簡化稍後尋找路徑的方式。</span><span class="sxs-lookup"><span data-stu-id="55a77-123">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![設定 DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="55a77-125">在新專案編譯之後，您想要特別注意空白的 cpp 和標頭檔，分別名為**HoloLensWinrtDLL**和**HoloLensWinrtDLL** 。</span><span class="sxs-lookup"><span data-stu-id="55a77-125">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="55a77-126">標頭是在 Unreal 中使用 DLL 的 include 檔案，而 cpp 則保存您所匯出之任何函式的主體，並包含 Unreal 無法編譯的任何 WinRT 程式碼。</span><span class="sxs-lookup"><span data-stu-id="55a77-126">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="55a77-127">在您新增任何程式碼之前，您必須先更新專案屬性，以確保您需要的 WinRT 程式碼可以編譯：</span><span class="sxs-lookup"><span data-stu-id="55a77-127">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="55a77-128">以滑鼠右鍵按一下 HoloLensWinrtDLL 專案，然後選取 [**屬性**]</span><span class="sxs-lookup"><span data-stu-id="55a77-128">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="55a77-129">將 [**設定] 下拉式**清單變更為 [所有設定 **] 和 [** **平臺**] 下拉式清單至**所有平臺**</span><span class="sxs-lookup"><span data-stu-id="55a77-129">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="55a77-130">在 [設定屬性] 底下 **> C/c + +> 所有選項**：</span><span class="sxs-lookup"><span data-stu-id="55a77-130">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="55a77-131">將**await**新增至**其他選項**，以確保我們可以等候非同步工作</span><span class="sxs-lookup"><span data-stu-id="55a77-131">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="55a77-132">將**c + + 語言標準**變更為**ISO c + + 17 標準（/std： c + + 17）** 以包含任何 WinRT 程式碼</span><span class="sxs-lookup"><span data-stu-id="55a77-132">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![設定 DLL](images/unreal-winrt-img-03.png)

<span data-ttu-id="55a77-134">您的專案已準備好使用 WinRT 程式碼更新 DLL 的來源，這會開啟檔案對話方塊並將檔案儲存至 HoloLens 磁片。</span><span class="sxs-lookup"><span data-stu-id="55a77-134">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="55a77-135">新增 DLL 程式碼</span><span class="sxs-lookup"><span data-stu-id="55a77-135">Adding the DLL code</span></span>
1. <span data-ttu-id="55a77-136">開啟**HoloLensWinrtDLL** ，並新增 dll 匯出函式以供 Unreal 使用：</span><span class="sxs-lookup"><span data-stu-id="55a77-136">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="55a77-137">開啟**HoloLensWinrtDLL** ，並新增類別將使用的所有標頭：</span><span class="sxs-lookup"><span data-stu-id="55a77-137">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> <span data-ttu-id="55a77-138">所有的 WinRT 程式碼都儲存在**HoloLensWinrtDLL**中，因此在參考標頭時，Unreal 不會嘗試包含任何 WinRT 程式碼。</span><span class="sxs-lookup"><span data-stu-id="55a77-138">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="55a77-139">仍然在**HoloLensWinrtDLL**中，新增 OpenFileDialogue （）和所有支援程式碼的函式主體：</span><span class="sxs-lookup"><span data-stu-id="55a77-139">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="55a77-140">將 SaveGameManager 類別新增至**HoloLensWinrtDLL** ，以處理檔案對話並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="55a77-140">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullprt);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. <span data-ttu-id="55a77-141">建立**Release > ARM64**的解決方案，從 dll 解決方案將 dll 建立到子目錄 ARM64/Release/HoloLensWinrtDLL。</span><span class="sxs-lookup"><span data-stu-id="55a77-141">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="55a77-142">將 WinRT 二進位檔新增至 Unreal</span><span class="sxs-lookup"><span data-stu-id="55a77-142">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="55a77-143">在 Unreal 中連結和使用 DLL 需要 c + + 專案。</span><span class="sxs-lookup"><span data-stu-id="55a77-143">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="55a77-144">如果您使用藍圖專案，可以藉由新增 c + + 類別，輕鬆地將它轉換成 c + + 專案：</span><span class="sxs-lookup"><span data-stu-id="55a77-144">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="55a77-145">在 [Unreal 編輯器] 中，開啟 [ **File] > New c + + Class** .。。</span><span class="sxs-lookup"><span data-stu-id="55a77-145">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="55a77-146">並**建立名為** **WinrtActor**的新動作專案，以執行 DLL 中的程式碼：</span><span class="sxs-lookup"><span data-stu-id="55a77-146">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![設定 DLL](images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="55a77-148">現在已在與 uproject 檔案相同的目錄中建立解決方案，以及名為 Source/ConsumeWinRT/ConsumerWinRT 的新組建腳本。</span><span class="sxs-lookup"><span data-stu-id="55a77-148">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumerWinRT.Build.cs.</span></span>

2. <span data-ttu-id="55a77-149">開啟解決方案，流覽**遊戲/ConsumeWinRT/來源/ConsumeWinRT**資料夾，然後開啟**ConsumeWinRT.build.cs**：</span><span class="sxs-lookup"><span data-stu-id="55a77-149">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![設定 DLL](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="55a77-151">連結 DLL</span><span class="sxs-lookup"><span data-stu-id="55a77-151">Linking the DLL</span></span>
1. <span data-ttu-id="55a77-152">在**ConsumeWinRT.build.cs**中，新增屬性以尋找 DLL （包含 HoloLensWinrtDLL 的目錄）的 include 路徑。</span><span class="sxs-lookup"><span data-stu-id="55a77-152">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="55a77-153">DLL 位於 include 路徑的子目錄中，因此此屬性將用來做為二進位根目錄：</span><span class="sxs-lookup"><span data-stu-id="55a77-153">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

```cs
public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirddParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. <span data-ttu-id="55a77-154">在類別的函式中，加入下列程式碼以更新 include 路徑、連結新的 lib 和延遲載入，並將 DLL 複製到已封裝的 appx 位置：</span><span class="sxs-lookup"><span data-stu-id="55a77-154">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. <span data-ttu-id="55a77-155">開啟**WinrtActor** ，並新增兩個函式定義，其中一個藍圖可以使用，另一個則使用 DLL 程式碼：</span><span class="sxs-lookup"><span data-stu-id="55a77-155">Open **WinrtActor.h** and add two function definitions, one that a blueprint can use and another that uses the DLL code:</span></span> 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. <span data-ttu-id="55a77-156">開啟**WinrtActor** ，並在 BeginPlay 中載入 DLL：</span><span class="sxs-lookup"><span data-stu-id="55a77-156">Open **WinrtActor.cpp** and load the DLL in BeginPlay:</span></span> 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="55a77-157">必須先載入 DLL，才能呼叫其任何函式。</span><span class="sxs-lookup"><span data-stu-id="55a77-157">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="55a77-158">打造遊戲</span><span class="sxs-lookup"><span data-stu-id="55a77-158">Building the game</span></span>
1. <span data-ttu-id="55a77-159">建立遊戲解決方案，啟動對遊戲專案開啟的 Unreal 編輯器：</span><span class="sxs-lookup"><span data-stu-id="55a77-159">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="55a77-160">在 [**放置**動作專案] 索引標籤中，搜尋新的**WinrtActor** ，並將它拖曳到場景中。</span><span class="sxs-lookup"><span data-stu-id="55a77-160">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="55a77-161">開啟層級藍圖以執行**WinrtActor**中的藍圖可呼叫函式</span><span class="sxs-lookup"><span data-stu-id="55a77-161">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![設定 DLL](images/unreal-winrt-img-06.png)

2. <span data-ttu-id="55a77-163">在**世界 Outliner**中，尋找先前已放入場景中的**WindrtActor** ，並將它拖曳至層級藍圖：</span><span class="sxs-lookup"><span data-stu-id="55a77-163">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![設定 DLL](images/unreal-winrt-img-07.png)

3. <span data-ttu-id="55a77-165">在層級藍圖中，從 [WinrtActor] 拖曳 [輸出] 節點，搜尋 [開啟檔案]**對話方塊**，然後從任何使用者輸入路由傳送節點。</span><span class="sxs-lookup"><span data-stu-id="55a77-165">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="55a77-166">在此情況下，會從語音事件呼叫 [開啟檔案] 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="55a77-166">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![設定 DLL](images/unreal-winrt-img-08.png)

4. <span data-ttu-id="55a77-168">[為 HoloLens 封裝此遊戲](unreal-uxt-ch6.md)、部署並執行。</span><span class="sxs-lookup"><span data-stu-id="55a77-168">[Package this game for HoloLens](unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="55a77-169">當 Unreal 呼叫 OpenFileDialogue 時，會在 HoloLens 上開啟 [檔案] 對話方塊，提示您輸入 .txt 檔案名。</span><span class="sxs-lookup"><span data-stu-id="55a77-169">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="55a77-170">儲存檔案之後，請移至裝置入口網站中的 [檔案**瀏覽器**] 索引標籤，以查看 "Hello WinRT" 內容。</span><span class="sxs-lookup"><span data-stu-id="55a77-170">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="55a77-171">摘要</span><span class="sxs-lookup"><span data-stu-id="55a77-171">Summary</span></span> 

<span data-ttu-id="55a77-172">我們鼓勵您使用本教學課程中的程式碼，做為在 Unreal 中取用 WinRT 程式碼的起點。</span><span class="sxs-lookup"><span data-stu-id="55a77-172">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="55a77-173">它可讓使用者使用與 Windows 相同的檔案對話，將檔案儲存到 HoloLens 磁片。</span><span class="sxs-lookup"><span data-stu-id="55a77-173">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="55a77-174">遵循相同的程式，從 HoloLensWinrtDLL 標頭匯出任何其他函式，並在 Unreal 中使用。</span><span class="sxs-lookup"><span data-stu-id="55a77-174">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="55a77-175">請注意在背景 MTA 執行緒中等候任何非同步 WinRT 程式碼的 DLL 程式碼，這可避免死結 Unreal 遊戲執行緒。</span><span class="sxs-lookup"><span data-stu-id="55a77-175">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

## <a name="see-also"></a><span data-ttu-id="55a77-176">請參閱</span><span class="sxs-lookup"><span data-stu-id="55a77-176">See also</span></span>
* [<span data-ttu-id="55a77-177">C + +/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="55a77-177">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="55a77-178">FileSavePicker 類別</span><span class="sxs-lookup"><span data-stu-id="55a77-178">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="55a77-179">Unreal 協力廠商程式庫</span><span class="sxs-lookup"><span data-stu-id="55a77-179">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
