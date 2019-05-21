---
title: 實作 3D 應用程式啟動器 （Win32 應用程式）
description: 如何建立 3D 應用程式啟動器和標誌 Win32 VR 應用程式和遊戲 （以外的資料流） 讓它們顯示在混合實境按下 [開始] 功能表和從家裡環境。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D，標誌、 圖示、 模型、 啟動器、 3D 的啟動器、 圖格、 即時的 cube win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594651"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="b5033-104">實作 3D 應用程式啟動器 （Win32 應用程式）</span><span class="sxs-lookup"><span data-stu-id="b5033-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="b5033-105">這項功能只會提供給執行最新的電腦[Windows Insider](https://insider.windows.com)航班 (RS5)、 17704 及更新版本的組建。</span><span class="sxs-lookup"><span data-stu-id="b5033-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="b5033-106">[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)是使用者啟動應用程式之前的登陸位置的起點。</span><span class="sxs-lookup"><span data-stu-id="b5033-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="b5033-107">根據預設，沈浸式 Win32 VR 應用程式和遊戲必須耳機之外，從啟動，而且不會出現在混合實境 [開始] 功能表上的 [所有應用程式] 清單。</span><span class="sxs-lookup"><span data-stu-id="b5033-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="b5033-108">不過，藉由遵循這篇文章中的指示，來實作 3D 應用程式啟動器，沈浸式的 Win32 VR 經驗可以從啟動 Windows Mixed Reality 開始 功能表和家庭環境內。</span><span class="sxs-lookup"><span data-stu-id="b5033-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="b5033-109">這只適用於外部資料流的沈浸式 Win32 VR 體驗 distributied。</span><span class="sxs-lookup"><span data-stu-id="b5033-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="b5033-110">以 VR 體驗[透過資料流散發](updating-your-steamvr-application-for-windows-mixed-reality.md)，我們已[SteamVR beta 版更新 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新的 Windows Insider RS5 航班以便 SteamVR 向上標題顯示在 Windows 中混合實境開始 功能表會自動使用預設啟動程式的 [所有應用程式] 清單中。</span><span class="sxs-lookup"><span data-stu-id="b5033-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="b5033-111">換句話說，這篇文章中所述的方法不需要為 SteamVR 標題，並會覆寫 Windows Mixed Reality SteamVR Beta 功能。</span><span class="sxs-lookup"><span data-stu-id="b5033-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="b5033-112">3D 應用程式啟動器建立程序</span><span class="sxs-lookup"><span data-stu-id="b5033-112">3D app launcher creation process</span></span>

<span data-ttu-id="b5033-113">有 3 個步驟以建立 3D 應用程式啟動程式：</span><span class="sxs-lookup"><span data-stu-id="b5033-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="b5033-114">設計和 concepting</span><span class="sxs-lookup"><span data-stu-id="b5033-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="b5033-115">模型化和匯出</span><span class="sxs-lookup"><span data-stu-id="b5033-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="b5033-116">將它整合到您的應用程式 （本文）</span><span class="sxs-lookup"><span data-stu-id="b5033-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="b5033-117">應該使用撰寫您的應用程式的啟動程式要使用 3D 資產[撰寫指導方針的 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)以確保相容性。</span><span class="sxs-lookup"><span data-stu-id="b5033-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="b5033-118">在家用的 Windows Mixed Reality 時，將無法呈現無法符合此規格中撰寫的資產。</span><span class="sxs-lookup"><span data-stu-id="b5033-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="b5033-119">設定 「 3D 」 啟動程式</span><span class="sxs-lookup"><span data-stu-id="b5033-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="b5033-120">Win32 應用程式會出現在混合實境 [開始] 功能表上的 [所有應用程式] 清單中，如果您為其建立 3D 應用程式啟動程式。</span><span class="sxs-lookup"><span data-stu-id="b5033-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="b5033-121">若要這樣做，請建立[視覺項目資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)XML 檔案參考 3D 應用程式啟動器，依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b5033-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="b5033-122">建立**3D 應用程式啟動器資產 GLB 檔案**(請參閱[模型，以及匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md))。</span><span class="sxs-lookup"><span data-stu-id="b5033-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="b5033-123">建立 **[視覺化項目資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b5033-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="b5033-124">您可以開始[下列範例](#sample-visual-elements-manifest)。</span><span class="sxs-lookup"><span data-stu-id="b5033-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="b5033-125">請參閱完整[視覺項目資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)文件，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b5033-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="b5033-126">更新**Square150x150Logo**並**Square70x70Logo**與 PNG/JPG/GIF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b5033-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="b5033-127">這些將用於 Windows Mixed Reality 所有應用程式清單中的應用程式的 2D 標誌和桌面上的 [開始] 功能表。</span><span class="sxs-lookup"><span data-stu-id="b5033-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="b5033-128">檔案路徑會相對於包含視覺化的項目資訊清單的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b5033-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="b5033-129">您仍然需要提供應用程式的 [開始] 功能表圖示的桌面，可透過標準機制。</span><span class="sxs-lookup"><span data-stu-id="b5033-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="b5033-130">這可以是直接在可執行檔，或在您建立 （例如，透過 IShellLink::SetIconLocation) 的捷徑。</span><span class="sxs-lookup"><span data-stu-id="b5033-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="b5033-131">*選擇性：* 如果您想要針對 MRT 提供多個資產的大小不同的解析度標尺和高對比佈景主題，您可以使用 resources.pri 檔案。</span><span class="sxs-lookup"><span data-stu-id="b5033-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="b5033-132">更新**MixedRealityModel 路徑**指向 GLB 3D 的應用程式啟動器</span><span class="sxs-lookup"><span data-stu-id="b5033-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="b5033-133">將檔案儲存為可執行檔，副檔名為同名"。VisualElementsManifest.xml"並將它儲存在相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="b5033-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="b5033-134">例如，"contoso.exe"的可執行檔，隨附的 XML 檔案是命名為"contoso.visualelementsmanifest.xml 」。</span><span class="sxs-lookup"><span data-stu-id="b5033-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="b5033-135">**將捷徑新增**桌面 Windows 開始 功能表中您應用程式。</span><span class="sxs-lookup"><span data-stu-id="b5033-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="b5033-136">請參閱[下列範例](#sample-app-launcher-shortcut-creation)例如C++實作。</span><span class="sxs-lookup"><span data-stu-id="b5033-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="b5033-137">建立在 %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs （電腦） 或 %APPDATA%\Microsoft\Windows\Start Menu\Programs （使用者）</span><span class="sxs-lookup"><span data-stu-id="b5033-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="b5033-138">如果更新會變更您的視覺元素資訊清單或所參考的資產，更新程式或安裝程式應該更新快顯，使資訊清單會重新分析，並且會更新快取的資產。</span><span class="sxs-lookup"><span data-stu-id="b5033-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="b5033-139">*選擇性：* 如果您的桌面捷徑不直接指向您的應用程式 EXE (例如，如果它會叫用的自訂通訊協定處理常式，例如"myapp: / /")，[開始] 功能表將不會自動尋找應用程式的 VisualElementsManifest.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="b5033-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="b5033-140">若要解決此問題，捷徑應該指定使用 System.AppUserModel.VisualElementsManifestHintPath （） 視覺化項目資訊清單的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b5033-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="b5033-141">這可以使用相同的技術為 System.AppUserModel.ID 捷徑設定。</span><span class="sxs-lookup"><span data-stu-id="b5033-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="b5033-142">您不需要使用 System.AppUserModel.ID 但您可能會這樣如果您想要以符合應用程式明確的應用程式使用者模型識別碼，如果使用捷徑。</span><span class="sxs-lookup"><span data-stu-id="b5033-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="b5033-143">請參閱[範例應用程式啟動器建立捷徑](#sample-app-launcher-shortcut-creation)節的C++範例。</span><span class="sxs-lookup"><span data-stu-id="b5033-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="b5033-144">範例視覺元素資訊清單</span><span class="sxs-lookup"><span data-stu-id="b5033-144">Sample Visual Elements Manifest</span></span>

```xml
<Application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="b5033-145">建立範例應用程式啟動程式捷徑</span><span class="sxs-lookup"><span data-stu-id="b5033-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="b5033-146">下列範例程式碼示範如何建立捷徑，以在C++，包括覆寫 Visual 項目資訊清單 XML 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="b5033-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="b5033-147">請注意在您的快顯不直接以與資訊清單 （例如相關聯的 EXE 點的情況下才需要覆寫。</span><span class="sxs-lookup"><span data-stu-id="b5033-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="b5033-148">您的快顯會使用自訂通訊協定處理常式，例如"myapp: / /")。</span><span class="sxs-lookup"><span data-stu-id="b5033-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="b5033-149">此範例。LNK 建立捷徑 (C++)</span><span class="sxs-lookup"><span data-stu-id="b5033-149">Sample .LNK shortcut creation (C++)</span></span>

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="b5033-150">此範例。URL 啟動程式捷徑</span><span class="sxs-lookup"><span data-stu-id="b5033-150">Sample .URL launcher shortcut</span></span> 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a><span data-ttu-id="b5033-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5033-151">See also</span></span>

* <span data-ttu-id="b5033-152">[混合的實境模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)包含 3D 應用程式啟動程式。</span><span class="sxs-lookup"><span data-stu-id="b5033-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="b5033-153">3D 應用程式啟動程式的設計指引</span><span class="sxs-lookup"><span data-stu-id="b5033-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="b5033-154">建立 3D 模型，使用 Windows Mixed Reality 在家中</span><span class="sxs-lookup"><span data-stu-id="b5033-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="b5033-155">實作 3D 應用程式啟動器 (UWP app)</span><span class="sxs-lookup"><span data-stu-id="b5033-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="b5033-156">瀏覽家用的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b5033-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
