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
# <a name="winrt-in-unreal"></a>Unreal 中的 WinRT

## <a name="overview"></a>概觀

在您的 HoloLens 開發過程中，您可能需要使用 WinRT 來撰寫功能。 例如，在 HoloLens 應用程式中開啟檔案對話方塊需要 winrt/Windows. FileSavePicker 標頭檔中的檔案。  由於 Unreal 不會以原生方式編譯 WinRT 程式碼，因此您的工作就是建立個別的二進位檔，並可供 Unreal 的組建系統使用。 本教學課程將逐步引導您完成這類案例。

## <a name="objectives"></a>目標
- 建立可開啟 FileSaveDialogue 的通用 Windows DLL
- 將該 DLL 連結至 Unreal 遊戲專案
- 使用新的 DLL，從 Unreal 藍圖將檔案儲存在 HoloLens

## <a name="getting-started"></a>開始使用
1. 檢查您是否已安裝所有[必要的工具](unreal-uxt-ch1.md)
2. [建立新的 Unreal 專案](unreal-uxt-ch2.md#creating-a-new-unreal-project)，並將其命名為**Consumewinrt**
3. 啟用適用于 HoloLens 開發的[必要外掛程式](unreal-uxt-ch2.md#enabling-required-plugins)
4. 部署至裝置或模擬器[的設定](unreal-uxt-ch6.md)

## <a name="creating-a-winrt-dll"></a>建立 WinRT DLL 
1. 開啟新的 Visual Studio 專案，並在與 Unreal 遊戲的**uproject**檔案相同的目錄中建立**DLL （通用 Windows）** 專案。 

![建立 DLL](images/unreal-winrt-img-01.png)

2. 將專案命名為**HoloLensWinrtDLL** ，並將位置設定為 Unreal 遊戲 uproject 檔案的**ThirdParty**子目錄。 
    * 選取 **[將方案和專案放在相同的目錄中**]，以簡化稍後尋找路徑的方式。 

![設定 DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> 在新專案編譯之後，您想要特別注意空白的 cpp 和標頭檔，分別名為**HoloLensWinrtDLL**和**HoloLensWinrtDLL** 。 標頭是在 Unreal 中使用 DLL 的 include 檔案，而 cpp 則保存您所匯出之任何函式的主體，並包含 Unreal 無法編譯的任何 WinRT 程式碼。 

3. 在您新增任何程式碼之前，您必須先更新專案屬性，以確保您需要的 WinRT 程式碼可以編譯： 
    * 以滑鼠右鍵按一下 HoloLensWinrtDLL 專案，然後選取 [**屬性**]  
    * 將 [**設定] 下拉式**清單變更為 [所有設定 **] 和 [** **平臺**] 下拉式清單至**所有平臺**  
    * 在 [設定屬性] 底下 **> C/c + +> 所有選項**：
        * 將**await**新增至**其他選項**，以確保我們可以等候非同步工作  
        * 將**c + + 語言標準**變更為**ISO c + + 17 標準（/std： c + + 17）** 以包含任何 WinRT 程式碼

![設定 DLL](images/unreal-winrt-img-03.png)

您的專案已準備好使用 WinRT 程式碼更新 DLL 的來源，這會開啟檔案對話方塊並將檔案儲存至 HoloLens 磁片。  

## <a name="adding-the-dll-code"></a>新增 DLL 程式碼
1. 開啟**HoloLensWinrtDLL** ，並新增 dll 匯出函式以供 Unreal 使用： 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. 開啟**HoloLensWinrtDLL** ，並新增類別將使用的所有標頭：  

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
> 所有的 WinRT 程式碼都儲存在**HoloLensWinrtDLL**中，因此在參考標頭時，Unreal 不會嘗試包含任何 WinRT 程式碼。 

3. 仍然在**HoloLensWinrtDLL**中，新增 OpenFileDialogue （）和所有支援程式碼的函式主體： 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. 將 SaveGameManager 類別新增至**HoloLensWinrtDLL** ，以處理檔案對話並儲存檔案： 

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

5. 建立**Release > ARM64**的解決方案，從 dll 解決方案將 dll 建立到子目錄 ARM64/Release/HoloLensWinrtDLL。 

## <a name="adding-the-winrt-binary-to-unreal"></a>將 WinRT 二進位檔新增至 Unreal 
在 Unreal 中連結和使用 DLL 需要 c + + 專案。 如果您使用藍圖專案，可以藉由新增 c + + 類別，輕鬆地將它轉換成 c + + 專案：  

1. 在 [Unreal 編輯器] 中，開啟 [ **File] > New c + + Class** .。。 並**建立名為** **WinrtActor**的新動作專案，以執行 DLL 中的程式碼： 

![設定 DLL](images/unreal-winrt-img-04.png)

> [!NOTE]
> 現在已在與 uproject 檔案相同的目錄中建立解決方案，以及名為 Source/ConsumeWinRT/ConsumerWinRT 的新組建腳本。

2. 開啟解決方案，流覽**遊戲/ConsumeWinRT/來源/ConsumeWinRT**資料夾，然後開啟**ConsumeWinRT.build.cs**：

![設定 DLL](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>連結 DLL
1. 在**ConsumeWinRT.build.cs**中，新增屬性以尋找 DLL （包含 HoloLensWinrtDLL 的目錄）的 include 路徑。 DLL 位於 include 路徑的子目錄中，因此此屬性將用來做為二進位根目錄：

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

2. 在類別的函式中，加入下列程式碼以更新 include 路徑、連結新的 lib 和延遲載入，並將 DLL 複製到已封裝的 appx 位置：

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

3. 開啟**WinrtActor** ，並新增兩個函式定義，其中一個藍圖可以使用，另一個則使用 DLL 程式碼： 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. 開啟**WinrtActor** ，並在 BeginPlay 中載入 DLL： 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> 必須先載入 DLL，才能呼叫其任何函式。

### <a name="building-the-game"></a>打造遊戲
1. 建立遊戲解決方案，啟動對遊戲專案開啟的 Unreal 編輯器： 
    * 在 [**放置**動作專案] 索引標籤中，搜尋新的**WinrtActor** ，並將它拖曳到場景中。 
    * 開啟層級藍圖以執行**WinrtActor**中的藍圖可呼叫函式 

![設定 DLL](images/unreal-winrt-img-06.png)

2. 在**世界 Outliner**中，尋找先前已放入場景中的**WindrtActor** ，並將它拖曳至層級藍圖： 

![設定 DLL](images/unreal-winrt-img-07.png)

3. 在層級藍圖中，從 [WinrtActor] 拖曳 [輸出] 節點，搜尋 [開啟檔案]**對話方塊**，然後從任何使用者輸入路由傳送節點。  在此情況下，會從語音事件呼叫 [開啟檔案] 對話方塊： 

![設定 DLL](images/unreal-winrt-img-08.png)

4. [為 HoloLens 封裝此遊戲](unreal-uxt-ch6.md)、部署並執行。  

當 Unreal 呼叫 OpenFileDialogue 時，會在 HoloLens 上開啟 [檔案] 對話方塊，提示您輸入 .txt 檔案名。  儲存檔案之後，請移至裝置入口網站中的 [檔案**瀏覽器**] 索引標籤，以查看 "Hello WinRT" 內容。 

## <a name="summary"></a>摘要 

我們鼓勵您使用本教學課程中的程式碼，做為在 Unreal 中取用 WinRT 程式碼的起點。  它可讓使用者使用與 Windows 相同的檔案對話，將檔案儲存到 HoloLens 磁片。  遵循相同的程式，從 HoloLensWinrtDLL 標頭匯出任何其他函式，並在 Unreal 中使用。  請注意在背景 MTA 執行緒中等候任何非同步 WinRT 程式碼的 DLL 程式碼，這可避免死結 Unreal 遊戲執行緒。 

## <a name="see-also"></a>請參閱
* [C + +/WinRT Api](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [FileSavePicker 類別](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Unreal 協力廠商程式庫](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
