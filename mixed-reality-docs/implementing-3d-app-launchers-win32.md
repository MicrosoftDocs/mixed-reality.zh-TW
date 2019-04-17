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
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594651"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>實作 3D 應用程式啟動器 （Win32 應用程式）

> [!NOTE]
> 這項功能只會提供給執行最新的電腦[Windows Insider](https://insider.windows.com)航班 (RS5)、 17704 及更新版本的組建。

[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)是使用者啟動應用程式之前的登陸位置的起點。 根據預設，沈浸式 Win32 VR 應用程式和遊戲必須耳機之外，從啟動，而且不會出現在混合實境 [開始] 功能表上的 [所有應用程式] 清單。 不過，藉由遵循這篇文章中的指示，來實作 3D 應用程式啟動器，沈浸式的 Win32 VR 經驗可以從啟動 Windows Mixed Reality 開始 功能表和家庭環境內。

這只適用於外部資料流的沈浸式 Win32 VR 體驗 distributied。 以 VR 體驗[透過資料流散發](updating-your-steamvr-application-for-windows-mixed-reality.md)，我們已[SteamVR beta 版更新 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新的 Windows Insider RS5 航班以便 SteamVR 向上標題顯示在 Windows 中混合實境開始] 功能表會自動使用預設啟動程式的 [所有應用程式] 清單中。 換句話說，這篇文章中所述的方法不需要為 SteamVR 標題，並會覆寫 Windows Mixed Reality SteamVR Beta 功能。

## <a name="3d-app-launcher-creation-process"></a>3D 應用程式啟動器建立程序

有 3 個步驟以建立 3D 應用程式啟動程式：
1. [設計和 concepting](3d-app-launcher-design-guidance.md)
2. [模型化和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 將它整合到您的應用程式 （本文）

應該使用撰寫您的應用程式的啟動程式要使用 3D 資產[撰寫指導方針的 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)以確保相容性。 在家用的 Windows Mixed Reality 時，將無法呈現無法符合此規格中撰寫的資產。

## <a name="configuring-the-3d-launcher"></a>設定 「 3D 」 啟動程式

Win32 應用程式會出現在混合實境 [開始] 功能表上的 [所有應用程式] 清單中，如果您為其建立 3D 應用程式啟動程式。 若要這樣做，請建立[視覺項目資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)XML 檔案參考 3D 應用程式啟動器，依照下列步驟：

1. 建立**3D 應用程式啟動器資產 GLB 檔案**(請參閱[模型，以及匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md))。
2. 建立**[視覺化項目資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 應用程式。
    1. 您可以開始[下列範例](#sample-visual-elements-manifest)。  請參閱完整[視覺項目資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)文件，如需詳細資訊。
    2. 更新**Square150x150Logo**並**Square70x70Logo**與 PNG/JPG/GIF 應用程式。
        * 這些將用於 Windows Mixed Reality 所有應用程式清單中的應用程式的 2D 標誌和桌面上的 [開始] 功能表。
        * 檔案路徑會相對於包含視覺化的項目資訊清單的資料夾。
        * 您仍然需要提供應用程式的 [開始] 功能表圖示的桌面，可透過標準機制。 這可以是直接在可執行檔，或在您建立 （例如，透過 IShellLink::SetIconLocation) 的捷徑。
        * *選擇性：* 如果您想要針對 MRT 提供多個資產的大小不同的解析度標尺和高對比佈景主題，您可以使用 resources.pri 檔案。
    3. 更新**MixedRealityModel 路徑**指向 GLB 3D 的應用程式啟動器
    4. 將檔案儲存為可執行檔，副檔名為同名"。VisualElementsManifest.xml"並將它儲存在相同的目錄。 例如，"contoso.exe"的可執行檔，隨附的 XML 檔案是命名為"contoso.visualelementsmanifest.xml 」。
3. **將捷徑新增**桌面 Windows 開始 功能表中您應用程式。 請參閱[下列範例](#sample-app-launcher-shortcut-creation)例如C++實作。 
    * 建立在 %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs （電腦） 或 %APPDATA%\Microsoft\Windows\Start Menu\Programs （使用者）
    * 如果更新會變更您的視覺元素資訊清單或所參考的資產，更新程式或安裝程式應該更新快顯，使資訊清單會重新分析，並且會更新快取的資產。
4. *選擇性：* 如果您的桌面捷徑不直接指向您的應用程式 EXE (例如，如果它會叫用的自訂通訊協定處理常式，例如"myapp: / /")，[開始] 功能表將不會自動尋找應用程式的 VisualElementsManifest.xml 檔案。 若要解決此問題，捷徑應該指定使用 System.AppUserModel.VisualElementsManifestHintPath （） 視覺化項目資訊清單的檔案路徑。 這可以使用相同的技術為 System.AppUserModel.ID 捷徑設定。 您不需要使用 System.AppUserModel.ID 但您可能會這樣如果您想要以符合應用程式明確的應用程式使用者模型識別碼，如果使用捷徑。  請參閱[範例應用程式啟動器建立捷徑](#sample-app-launcher-shortcut-creation)節的C++範例。

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

### <a name="sample-app-launcher-shortcut-creation"></a>建立範例應用程式啟動程式捷徑

下列範例程式碼示範如何建立捷徑，以在C++，包括覆寫 Visual 項目資訊清單 XML 檔案的路徑。 請注意在您的快顯不直接以與資訊清單 （例如相關聯的 EXE 點的情況下才需要覆寫。 您的快顯會使用自訂通訊協定處理常式，例如"myapp: / /")。

#### <a name="sample-lnk-shortcut-creation-c"></a>此範例。LNK 建立捷徑 (C++)

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

#### <a name="sample-url-launcher-shortcut"></a>此範例。URL 啟動程式捷徑 

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

* [混合的實境模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)包含 3D 應用程式啟動程式。
* [3D 應用程式啟動程式的設計指引](3d-app-launcher-design-guidance.md)
* [建立 3D 模型，使用 Windows Mixed Reality 在家中](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [實作 3D 應用程式啟動器 (UWP app)](implementing-3d-app-launchers.md)
* [瀏覽家用的 Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
