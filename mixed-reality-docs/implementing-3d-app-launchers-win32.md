---
title: 執行3D 應用程式啟動器 (Win32 應用程式)
description: 如何建立適用于 Win32 VR 應用程式和遊戲的3D 應用程式啟動器和標誌 (散佈于流外), 使其顯示在 Windows Mixed Reality 的 [開始] 功能表和 [主環境] 中。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, 標誌, 圖示, 模型, 啟動器, 3D 啟動器, 磚, 即時 cube, win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515600"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>執行3D 應用程式啟動器 (Win32 應用程式)

> [!NOTE]
> 這項功能僅適用于執行最新[Windows 測試人員](https://insider.windows.com)航班 (RS5)、組建17704和更新版本的電腦。

[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。 根據預設, 沉浸式 Win32 VR 應用程式和遊戲必須從耳機外啟動, 而且不會出現在 Windows Mixed Reality [開始] 功能表上的 [所有應用程式] 清單中。 不過, 遵循本文中的指示來執行3D 應用程式啟動器, 您可以從 Windows Mixed Reality 的 [開始] 功能表和主環境中啟動您的沉浸式 Win32 VR 體驗。

這僅適用于 distributied 在流外的沉浸式 Win32 VR 體驗。 以 VR 體驗[透過資料流散發](updating-your-steamvr-application-for-windows-mixed-reality.md)，我們已[SteamVR beta 版更新 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新的 Windows Insider RS5 航班以便 SteamVR 向上標題顯示在 Windows 中混合實境開始 功能表會自動使用預設啟動程式的 [所有應用程式] 清單中。 換句話說, 本文中所述的方法不是 SteamVR 標題的必要專案, 且將由 Windows Mixed Reality 針對 SteamVR Beta 功能所覆寫。

## <a name="3d-app-launcher-creation-process"></a>3D 應用程式啟動器建立進程

建立3D 應用程式啟動器有3個步驟:
1. [設計和 concepting](3d-app-launcher-design-guidance.md)
2. [模型化和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 將它整合到您的應用程式 (本文)

要做為應用程式之啟動器使用的3D 資產, 應使用[Windows Mixed Reality 撰寫指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)來確保相容性。 無法符合此撰寫規格的資產將不會在 Windows Mixed Reality 首頁中轉譯。

## <a name="configuring-the-3d-launcher"></a>設定3D 啟動程式

如果您為其建立3D 應用程式啟動器, Win32 應用程式將會出現在 Windows Mixed Reality [開始] 功能表上的 [所有應用程式] 清單中。 若要這麼做, 請遵循下列步驟, 建立參考3D 應用程式啟動器的[視覺元素資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)XML 檔案:

1. 建立**3D 應用程式啟動器資產 GLB**檔案 (請參閱[模型和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md))。
2. 建立 **[視覺化項目資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 應用程式。
    1. 您可以從下面的[範例](#sample-visual-elements-manifest)開始。  如需詳細資訊, 請參閱完整的[視覺元素資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)檔。
    2. 使用您應用程式的 PNG/JPG/GIF 來更新**Square150x150Logo**和**Square70x70Logo** 。
        * 這些將用於 Windows Mixed Reality [所有應用程式] 清單中的應用程式2D 標誌, 以及桌上型電腦上的 [開始] 功能表。
        * 檔案路徑相對於包含視覺元素資訊清單的資料夾。
        * 您仍然需要透過標準機制, 為您的應用程式提供 [桌面] [開始] 功能表圖示。 這可以直接在可執行檔中, 或在您建立的快捷方式中 (例如透過 IShellLink:: SetIconLocation)。
        * *選擇性*如果您想要透過 MRT.LOG 為不同的解析度調整和高對比主題提供多個資產大小, 則可以使用 resources pri 檔案。
    3. 更新**MixedRealityModel 路徑**, 以指向您3D 應用程式啟動器的 GLB
    4. 以與可執行檔相同的名稱儲存檔案, 副檔名為 "。VisualElementsManifest, 並將它儲存在相同的目錄中。 例如, 針對可執行檔 "contoso. .exe", 隨附的 XML 檔案會命名為 "visualelementsmanifest .xml"。
3. 將應用程式的**快捷方式新增**至桌面 Windows 的 [開始] 功能表。 請參閱[下列範例](#sample-app-launcher-shortcut-creation), 以取得C++範例的執行。 
    * 在%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) 或%APPDATA%\Microsoft\Windows\Start Menu\Programs (使用者) 中建立
    * 如果更新變更您的視覺專案資訊清單或它所參考的資產, 則更新程式或安裝程式應該會更新快捷方式, 以便重新剖析資訊清單, 並更新快取的資產。
4. *選擇性*如果您的桌面快捷方式不會直接指向應用程式的 EXE (例如, 如果它叫用自訂通訊協定處理常式, 例如 "myapp://"), [開始] 功能表將不會自動尋找應用程式的 VisualElementsManifest。 若要解決這個問題, 快捷方式應該使用 AppUserModel. VisualElementsManifestHintPath () 指定視覺元素資訊清單的檔案路徑。 您可以使用與 System.AppUserModel.ID 相同的技術, 在快捷方式中設定這項功能。 您不需要使用 System.AppUserModel.ID, 但如果您想要讓快捷方式符合應用程式的明確應用程式使用者模型識別碼 (如果使用的話), 則可能會這麼做。  如需C++範例, 請參閱下面的[範例應用程式啟動器快捷方式建立](#sample-app-launcher-shortcut-creation)一節。

### <a name="sample-visual-elements-manifest"></a>範例視覺元素資訊清單

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

### <a name="sample-app-launcher-shortcut-creation"></a>範例應用程式啟動器快捷方式建立

下面的範例程式碼顯示如何在中C++建立快捷方式, 包括覆寫視覺元素資訊清單 XML 檔案的路徑。 請注意, 只有當您的快捷方式不會直接指向與資訊清單相關聯的 EXE 時, 才需要覆寫 (例如, 您的快捷方式會使用自訂通訊協定處理常式, 例如 "myapp://")。

#### <a name="sample-lnk-shortcut-creation-c"></a>抽樣.建立 .LNK 快捷方式C++()

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

#### <a name="sample-url-launcher-shortcut"></a>抽樣.URL 啟動程式快捷方式 

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

## <a name="see-also"></a>另請參閱

* 包含3D 應用程式啟動器的[混合現實模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。
* [3D 應用程式啟動程式設計指引](3d-app-launcher-design-guidance.md)
* [建立3D 模型以用於 Windows Mixed Reality 首頁](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [執行3D 應用程式啟動器 (UWP 應用程式)](implementing-3d-app-launchers.md)
* [瀏覽 Windows Mixed Reality 住家](navigating-the-windows-mixed-reality-home.md)
