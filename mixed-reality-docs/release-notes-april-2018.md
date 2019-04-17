---
title: 版本資訊-2018 年 4 月
description: HoloLens 與 Windows Mixed Reality 版本資訊適用於 Windows 10 April 2018 Update (也稱為 RS4)。
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: 版本資訊、 版本、 windows 10、 組建、 rs4、 os
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594597"
---
# <a name="release-notes---april-2018"></a>版本資訊-2018 年 4 月

**[Windows 10 April 2018 Update](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (也稱為 RS4) 包括 HoloLens 和沈浸式耳機連接到電腦的 Windows Mixed Reality 的新功能。 

若要更新為最新版本的其中一種裝置類型，請開啟**設定**應用程式，移至**更新與安全性**，然後選取**檢查更新** 按鈕。 在 Windows 10 電腦上，您也可以手動安裝 Windows 10 April 2018 Update 使用[Windows media 製作工具](https://www.microsoft.com/software-download/windows10)。

**適用於桌面的最新版本：** Windows 10 April 2018 Update (**10.0.17134.1**)<br>
**最新版次 HoloLens:** Windows 10 April 2018 Update (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*在 Windows 中的新混合的實境功能的概觀與 Alex Kipman 訊息 10 April 2018 Update*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沈浸式耳機的新功能

Windows 10 April 2018 Update 包含許多增強功能與桌上型 PC，使用 Windows Mixed Reality 沈浸式 (VR) 耳機，例如： 

* **新環境以供主混合實境**-您現在可以選擇 Cliff 房子和新的 Skyloft 環境之間選取**上的芳鄰**[開始] 功能表。 我們還新增了[實驗性功能](add-custom-home-environments.md)，可讓您使用您已建立的自訂環境。
* **快速存取混合的實境擷取**-您現在也可使用動作控制器的混合的實境相片。 保留 Windows 按鈕，然後點選 觸發程序。 這適用於環境和應用程式，但不是會擷取受 DRM 保護的內容。
* **新的選項來啟動或調整大小內容**-應用程式現在會自動位於您面前當您從 [開始] 功能表啟動。 您現在也可以藉由拖曳邊緣與角落的視窗調整 2D 應用程式。
* **使用 「 傳送 」 語音命令的內容讓您輕鬆跳**-您現在可以快速傳送要在家用的 Windows Mixed Reality 內容前面 gazing 在內容，並指出 「 傳送 」。
* **[以動畫顯示 3D 應用程式啟動器](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines)並[裝飾的 3D 物件](enable-placement-of-3d-models-in-the-home.md)家用混合實境的**-您現在可以將動畫加入至 3D 應用程式啟動器，並允許將裝飾的 3D 模型，從網頁或 2D 應用程式的使用者Windows Mixed Reality 首頁。
* **[對 Windows Mixed Reality for SteamVR 改進](updating-your-steamvr-application-for-windows-mixed-reality.md)** -SteamVR 的 Windows Mixed Reality 超出 「 搶先使用 」 新的升級，包括： haptic 意見反應時使用動作控制站、 更佳的效能和可靠性，並改進外觀 SteamVR 動作控制站。
* **其他改進**-自動效能設定已更新，以提供更完善的經驗 (您可以[手動覆寫](#visual-quality)這項設定)。 安裝程式現在會提供與 USB 3.0 控制站和圖形卡的更詳細常見的相容性問題的相關資訊。

## <a name="new-features-for-hololens"></a>HoloLens 的新功能

Windows 10 April 2018 Update 到達所有 HoloLens 客戶 ！ 此更新富含已自 HoloLens 軟體中的最後一個主要版本中引進的改良[2016 年 8 月](release-notes-august-2016.md)。

### <a name="for-everyone"></a>每個人

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>自動放置在啟動的 2D 和 3D 內容</td><td>2D 應用程式啟動器或 2D UWP 應用程式自動-數位世界的最佳大小和距離，而不需要將它放入使用者啟動時。 如果<a href="app-views.md">沉浸式應用程式</a>會使用 2D 應用程式啟動程式，而不是<a href="3d-app-launcher-design-guidance.md">3D 應用程式啟動器</a>，沈浸式應用程式會自動啟動從 2D 應用程式啟動器相同如 RS1 所示。<br><br>從 [開始] 功能表的 3D 應用程式啟動器也自動-數位世界。 而不是自動啟動應用程式，使用者可以按一下以啟動沈浸式應用程式啟動程式。 開啟從全像投影應用程式和 Edge 的 3D 內容也自動-數位世界。</td><td>當從 [開始] 功能表中開啟應用程式，不再會要求您將它放在世界各地。<br><br>如果 2D 應用程式 /<a href="3d-app-launcher-design-guidance.md">3D 應用程式啟動器</a>位置不是最佳選項，您可以輕鬆地移動它們使用新的流暢的應用程式操作，如下所述。 您也可以重新定位 2D 應用程式啟動器/3D 內容指出 「 移動這 」，然後使用 重新放置內容的 視線。</td>
  </tr>
  <tr>
    <td>流暢的應用程式操作</td><td>移動、 調整大小，和旋轉 2D 和 3D 內容，而不需要輸入 「 調整 」 模式。</td><td>若要移動的 2D 的 UWP 應用程式或 2D 應用程式啟動器，只要注視其應用程式列，然後使用 tap 保存 + 拖曳筆勢。 您可以移動 3D 內容 gazing 物件上的任何位置，然後使用點選 + 保存 + 拖曳。<br><br>若要調整大小 2D 內容，注視其邊角。 視線資料指標會變成調整大小資料指標，然後點選 + 保存 + 拖曳以調整大小。 您也可以查看其邊緣並拖曳讓 2D 內容高度或寬度。<br><br>若要調整 3D 內容，請提起筆勢框架中，指到這兩個您手裡準備好的位置。 您會看到資料指標轉換成 2 個小小的指針的狀態。 請勿點選並按住滑鼠筆勢與這兩個實際操作。 移近一點或遠您手裡會變更物件的大小。 移動向前及向後相對於其他您手裡會旋轉物件。 您也可以調整大小/旋轉 2D 內容這種方式。</td>
  </tr>
  <tr>
    <td>2D 應用程式使用自動重排的水平大小調整</td><td>若要查看更多的應用程式內容的外觀比例進行更廣的 2D UWP 應用程式。 比方說，讓郵件應用程式寬度不足以顯示 [預覽] 窗格。</td><td>只要視線向左或右邊緣的 2D UWP 應用程式的調整大小游標，則使用 tap 保存 + 拖曳調整大小的筆勢。</td>
  </tr>
  <tr>
    <td>展開的語音命令支援</td><td>您可以執行多個簡單地使用您的聲音。</td><td>請嘗試這些語音命令：<ul><li>移至 開始-會顯示 開始 功能表或離開<a href="app-views.md">沉浸式應用程式</a>。</li><li>「 移動這-」 可讓您移動物件。</li></ul></td>
  </tr>
  <tr>
    <td>更新的全像投影和相片應用程式</td><td>更新全像投影的應用程式新全像投影。 已更新的相片應用程式。</td><td>您會注意到全像投影和相片應用程式更新後的外觀。 全像投影應用程式包含數個新全像投影和標籤的標記文字更容易建立。</td>
  </tr>
  <tr>
    <td>改善混合的實境擷取</td><td>硬體快顯開始與結束 MRC 視訊。</td><td>保留 音量提高 + 3 秒，若要開始錄製 MRC 影片清單。 再次點選兩者，或使用 bloom 筆勢來結束。</td>
  </tr>
  <tr>
    <td>彙總的空間</td><td>簡化成單一空格全像投影空間管理。</td><td>HoloLens 自動尋找您的空間，並不再需要您管理，或選取空格。 如果您有全像投影解決您的問題，您可以移至<b>設定 > System > 全像投影 > 移除全像投影附近</b>。 如有需要您也可以選取<b>移除所有全像投影</b>。</td>
  </tr>
  <tr>
    <td>改善的音訊訓練活動</td><td>您現在可以在吵雜的環境中，進一步聽到 HoloLens，並體驗更 lifelike 音效應用程式，如其聲音會遮住真實裝置所偵測到的背景牆。</td><td>您不必執行任何動作即可享有改進空間的音效。</td>
  </tr>
  <tr>
    <td>檔案總管</td><td>移動和刪除 HoloLens 中的檔案。</td><td>您可以使用<b>檔案總管</b>來移動和刪除檔案內 HoloLens 的應用程式。<br><br><b>變更複寫用快取資料夾路徑</b>如果您沒有看到任何檔案，「 最近 」 篩選條件可能是作用中 （左窗格中，反白顯示時鐘圖示）。 若要修正問題，請選取<b>此裝置</b>文件圖示，左窗格中 （下方的時鐘圖示），或開啟功能表，然後選取<b>此裝置</b>。
</td>
  </tr>
  <tr>
    <td>MTP （媒體傳輸通訊協定） 支援</td><td>輕鬆傳輸 HoloLens 上啟用您的桌上型電腦存取您的程式庫 （相片、 影片、 文件）。</td><td>類似於其他行動裝置，連線到您的電腦，以顯示的您 HoloLens<b>檔案總管</b>輕鬆傳輸存取您 HoloLens 的程式庫 （相片、 影片、 文件）。<br><br><b>秘訣：</b><ul><li>如果您沒有看到任何檔案，請確定您登入您的 HoloLens 若要存取您的資料。</li><li>從<b>檔案總管</b>在您的電腦，您可以選取<b>裝置屬性</b>查看 Windows 全像攝影版的作業系統版本號碼 （韌體版本） 以及裝置序號。</li></ul><b>已知的問題：</b>重新命名透過 HoloLens<b>檔案總管</b>您的電腦未啟用。</td>
  </tr>
  <tr>
    <td>在安裝期間的網頁驗證入口網站的網路支援</td><td>您現在可以設定您的 HoloLens 訪客在網路上的旅館，會議中心、 零售商店或使用網頁驗證入口網站的企業。</td><td>在安裝期間，選取的網路、 核取自動連線，如有需要，然後輸入網路資訊的提示。</td>
  </tr>
  <tr>
    <td>相片和視訊的同步處理，透過 OneDrive 應用程式</td><td>相片和視訊從 HoloLens 現在會透過 OneDrive 應用程式，而不是 Microsoft Store 直接透過相片應用程式從同步處理。</td><td>若要設定此功能，下載並啟動 OneDrive 應用程式，從存放區。 第一次執行應該會提示您自動將相片上傳至 OneDrive 或您可以在應用程式設定中找到的選項。</td>
  </tr>
</table>

### <a name="for-developers"></a>適用於開發人員

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>空間對應的改進</td><td>品質、 簡化方式，與效能改進。</td><td>空間對應網格看起來更簡潔 – 較少的三角形，才能代表相同的層級的詳細資料。 您可能發現變更場景中的三角形密度。</td>
  </tr>
  <tr>
    <td>自動選擇的深度緩衝區所根據的焦點</td><td>提交至 Windows 的深度緩衝區讓選取自動以最佳化全像穩定性婧鎏鶗懘 HoloLens。</td><td>在 Unity 中，移至<b>編輯 > 專案設定 > Player > 通用 Windows 平台 索引標籤 > XR 設定</b>，展開<b>Windows Mixed Reality SDK</b>項目，並確保<b>啟用深度緩衝區共用</b>已核取。 這將會自動檢查新的專案。<br><br>DirectX 應用程式，請確定您呼叫<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a>方法<b>HolographicRenderingParameters</b>提供 Windows 的深度緩衝區的每個畫面格。
</td>
  </tr>
  <tr>
    <td>全像攝影版 reprojection 模式</td><td>您現在可以停用位置 reprojection 改善嚴格的主體鎖定的內容，例如 360 度影片的全像穩定性的 HoloLens 上。</td><td>在 Unity 中，設定<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a>要<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a>當所有的內容檢視中是嚴格的主體鎖定。<br><br>針對 DirectX 應用程式，設定<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">HolographicCameraRenderingParameters.ReprojectionMode</a>要<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a>當所有的內容檢視中是嚴格的主體鎖定。</td>
  </tr>
  <tr>
    <td>應用程式調適的 Api</td><td>Windows Api，深入了解有關您的應用程式正在執行，例如裝置的顯示是否透明 (HoloLens) 或不透明 （沈浸式耳機），以及是否在全像攝影版的殼層中出現的 UWP 應用程式的 2D 檢視。</td><td>先前已手動公開 unity <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings.IsDisplayOpaque</a>處理過之前此組建的方式。<br><br>針對 DirectX 應用程式，您現在可以存取現有的 Api，例如<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay.GetDefault()。IsOpaque</a>並<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a>也 HoloLens 上。
</td>
  </tr>
  <tr>
      <td>參考資料模式</td><td>可讓開發人員建置要在電腦視景和機器人的欄位中測試新構想的學術和產業應用程式時，存取金鑰的 HoloLens 感應器包括：<ul><li>四個追蹤相機的環境</li><li>兩個版本的深度對應相機資料</li><li>IR-反射率資料流的兩個版本</li></ul></td><td><a href="research-mode.md">參考資料模式的文件</a><br><a href="https://github.com/Microsoft/HoloLensForCV">參考資料模式的範例應用程式</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>商業客戶

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>在單一裝置上使用多個 Azure Active Directory 使用者帳戶</td><td>HoloLens 分享給多個 Azure AD 使用者，各有自己的使用者設定和裝置上的使用者資料。</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT 專業人員中心：與多人共用 HoloLens</a></td>
  </tr>
  <tr>
    <td>變更在登入的 Wi-fi 網路</td><td>變更之前登入若要啟用另一位使用者使用他 / 她的 Azure AD 使用者帳戶登入，第一次，讓使用者能夠共用裝置不同的位置，以及作業站台的 Wi-fi 網路。</td><td>在 登入 畫面中，您可以使用下列密碼 欄位中的網路圖示來連線到網路。 這是您的第一次登入裝置時，這是很有幫助。</td>
  </tr>
  <tr>
    <td>統一的註冊</td><td>現在很容易設定使用個人 Microsoft 帳戶新增工作帳戶 (Azure AD)，並將裝置及其 MDM 伺服器加入裝置的 HoloLens 使用者。</td><td>只要登入 Azure AD 帳戶，並註冊會自動發生。</td>
  </tr>
  <tr>
    <td>郵件同步處理，而不需要 MDM 註冊</td><td>適用於 Exchange Active Sync (EAS) 郵件同步處理，而不需要 MDM 註冊的支援。</td><td>您現在可以同步電子郵件，而不需要在 MDM 中註冊 您可以設定裝置與 Microsoft 帳戶、 下載和安裝的郵件應用程式，並直接加入工作電子郵件帳戶。</td>
  </tr>
</table>

### <a name="for-it-pros"></a>適用於 IT 專業人員

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>新的 「 Windows Holographic for Business"OS 名稱</td><td>清除版本命名減少時 HoloLens 上同時啟用 Commercial Suite，功能的版本升級授權應用程式造成混淆。</td><td>您可以看到哪個版本的 Windows 全像攝影版是在裝置上<b>設定 > System > 有關</b>。 「 Windows Holographic for Business"會顯示已套用至啟用 Commercial Suite，功能的版本更新。 了解如何<a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">功能解除鎖定 Windows Holographic for Business</a>。</td>
  </tr>
  <tr>
  <td>Windows Configuration Designer (WCD)</td><td>建立和編輯設定 HoloLens 透過更新 WCD 應用程式的佈建套件。 簡單的版本更新、 可設定的 OOBE、 區域/時區、 大量的 Azure AD 權杖、 網路和開發人員 CSP 的 HoloLens 精靈。 進階篩選為 HoloLens 的編輯器支援選項，包括指派的存取權和帳戶管理 Csp。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT 專業人員中心：設定使用佈建套件的 HoloLens</a></td>
  </tr>
  <tr>
    <td>可設定的安裝程式 (OOBE)</td><td>在安裝期間隱藏校正、 訓練、 手勢/視線和 Wi-fi 設定畫面。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT 專業人員中心：設定使用佈建套件的 HoloLens</a></td>
  </tr>
  <tr>
    <td>大量支援 Azure AD 權杖</td><td>預先註冊裝置 Azure AD 目錄租用戶的更快速的使用者安裝流程。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT 專業人員中心：設定使用佈建套件的 HoloLens</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup CSP</td><td>部署設定檔以設定 開發人員模式中的 HoloLens。 適用於開發和示範的裝置。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT 專業人員中心：設定使用佈建套件的 HoloLens</a></td>
  </tr>
  <tr>
  <td>AccountManagement CSP</td><td>共用的 HoloLens 裝置並移除使用者資料之後, 登出或非使用狀態/儲存體供暫時使用的臨界值。 支援的 Azure AD 帳戶。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT 專業人員中心：設定使用佈建套件的 HoloLens</a></td>
  </tr>
  <tr>
  <td>指派存取權</td><td>Windows 會指派存取權的第一列的背景工作角色或示範。 單一或多個應用程式鎖定。 開發人員不需要解除鎖定。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT 專業人員中心：Kiosk 模式設定 HoloLens</a></td>
  </tr>
  <tr>
  <td>Kiosk 裝置的來賓存取</td><td>示範與無密碼的來賓帳戶的存取權指派給 Windows。 單一或多個應用程式鎖定。 開發人員不需要解除鎖定。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT 專業人員中心：Kiosk 模式設定 HoloLens</a></td>
  </tr>
  <tr>
    <td>設定 (OOBE) 診斷</td><td>因此 （在之前的意見反應中樞是可供使用者在其登入失敗），您可以疑難排解 Azure AD 登入失敗，則您可以獲得 HoloLens 診斷記錄檔。</td><td>當安裝程式 」 或 「 登入失敗時，選擇新<b>收集資訊</b>選項，以取得診斷記錄進行疑難排解。</td>
  </tr>
  <tr>
    <td>本機帳戶無限制的密碼到期</td><td>移除裝置重設本機帳戶密碼到期時中斷。</td><td>當佈建的本機帳戶，您不再需要變更密碼中的每個 42 天數<b>設定</b>，因為帳戶密碼不會到期。</td>
  </tr>
  <tr>
    <td>MDM 同步處理狀態和詳細資料</td><td>若要了解 MDM 同步狀態，以及從 HoloLens 中的詳細資料的標準 Windows 功能。</td><td>您可以檢查中的裝置的 MDM 同步處理狀態<b>設定 > 帳戶 > 存取公司或學校 > 資訊</b>。 在 [<b>裝置同步處理狀態<b>] 區段中，您可以啟動同步處理、 查看由 MDM 管理的區域和建立及匯出的進階的診斷報告。</td>
  </tr>
</table>

## <a name="known-issues"></a>已知問題

我們已努力地提供絕佳的 Windows Mixed Reality 體驗，但我們仍正在追蹤一些已知的問題。 如果您發現其他人，請[提供意見反應](give-us-feedback.md)。

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>更新之後

從 RS1 更新至 RS4 您 HoloLens 上之後，您可能會發現下列問題：
* **Pin 重設**-3x3 的應用程式釘選到開始 功能表會更新之後重設預設值。 
* **應用程式和放置全像投影重設**-放在您的世界中的應用程式將會移除更新之後，必須重新放置到您的空間。 
* **意見反應中樞可能不會立即啟動**-立即更新之後，需要幾分鐘的時間才能啟動某些收件匣應用程式，例如意見反應中樞，雖然它們自行更新。 
* **需要重新同步處理公司的 Wi-fi 憑證**-我們正在調查需要連線到不同的網路，為了讓公司的憑證，才能夠重新連線至要重新同步處理到裝置 HoloLens 的問題使用憑證的公司網路。 
* **無法運作 H.265 HEVC 視訊播放**-嘗試播放 H.265 影片的應用程式會收到一則錯誤訊息。 因應措施是[存取 Windows Device Portal](using-the-windows-device-portal.md)，選取**應用程式**的左側的導覽列上，並**移除**HEVC 應用程式。 然後，安裝最新[HEVC 視訊延伸模組](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7)從 Microsoft Store。 我們正在調查此問題。 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>適用於開發人員： 更新 HoloLens 的應用程式的裝置執行 Windows 10 April 2018 Update

很棒的清單以及[新功能](#new-features-for-hololens)，Windows 10 年 4 月 HoloLens 的 2018 Update (RS4) 會強制執行舊版本不提供支援一些程式碼行為：
* **若要使用敏感性資源 （網路攝影機、 麥克風） 的權限要求** -RS4 HoloLens 上的將會強制執行的應用程式想要存取敏感資源，例如網路攝影機或麥克風的權限要求。 RS1 HoloLens 上的並未強制這些提示，因此，如果您的應用程式會假設立即存取這些資源，它可能會損毀 RS4 中 （即使使用者授與要求之資源的權限）。 請先閱讀相關[UWP 應用程式功能宣告文章](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations)如需詳細資訊。
* **呼叫外部您自己的應用程式**-RS4 HoloLens 上的將會強制執行的正確用法[ *Windows.System.Launcher*類別](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)啟動與您自己的另一個應用程式。 比方說，我們已了解問題與呼叫的應用程式*Windows.System.Launcher.LaunchUriForResultsAsync*從非 ASTA UI 執行緒。 RS1 HoloLens，在中，這會成功，但 RS4 需要 UI 執行緒上執行的呼叫。

### <a name="windows-mixed-reality-on-desktop"></a>Windows 桌面上的混合的實境

#### <a name="visual-quality"></a>視覺品質

* 如果您注意到的 Windows 10 April 2018 Update 圖形是比之前更模糊或欄位來看看起來較小上耳機之後，自動效能設定可能已變更維持足夠的畫面播放速率，在較不強大（例如 Nvidia 1050) 的圖形卡。 您可以手動覆寫此 （如果您選擇） 瀏覽至**設定 > 混合實境 > 耳機顯示 > 體驗選項 > 變更**並將 「 自動 」 變更為"90 Hz。 」 您也可以嘗試變更**的視覺品質**（在相同的 [設定] 頁面中） 來 「 高 」。

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality 安裝程式

* 設定 Windows 耳機，連接，當您的電腦監視器會變成空白。 拔下您耳機，若要啟用您的電腦監視器，來完成 Windows 安裝程式的輸出。
* 如果您沒有連接的耳機，可能會遺失其他祕訣，當您第一次造訪家用的 Windows Mixed Reality 時中。
* 其他藍芽裝置可能造成動作控制器的干擾。 如果動作控制站有連接/配對/追蹤問題，請確定藍芽無線電 （如果外部的硬體鎖） 已插入到遮擋位置並不會立即其他藍芽硬體鎖旁邊。 也請嘗試關閉其他藍牙周邊設備，看看是否最好的 Windows Mixed Reality 工作階段期間。

#### <a name="games-and-apps-from-the-microsoft-store"></a>遊戲和應用程式從 Microsoft Store

* Forza Motorsport 7 之類的某些圖形密集型遊戲可能造成效能問題，在播放內 Windows Mixed Reality 時效能較差的電腦上。

#### <a name="audio"></a>音訊

* 如果您有 Cortana 在您主機電腦上啟用，才能使用 Windows Mixed Reality 耳機時，您可能會喪失空間套用至您放置周圍家用的 Windows Mixed Reality 應用程式的聲音模擬。 
   * 因應措施是啟用 「 Windows Sonic 如耳機"附加至您的電腦，即使您耳機連接音訊裝置的所有音訊裝置上：
      1. 以滑鼠左鍵按一下桌面工作列上的 [演講者備忘] 圖示，然後選取清單中的音訊裝置。
      2. 以滑鼠右鍵按一下桌面工作列上的 [演講者備忘] 圖示並選取 [演講者備忘 setup] 功能表中的 「 Windows Sonic 如耳機"。
      3. 針對所有音訊裝置 （端點），請重複這些步驟。
   * 另一個選項，關閉 「 嘿 Cortana 讓 Cortana 回應 」**設定** > **Cortana**啟動 Windows Mixed Reality 之前您的桌面上。
* 時 （例如網路相機） 的另一個多媒體 USB 裝置與 Windows Mixed Reality 耳機共用相同的 USB 集線器 （外部或在您的電腦），在少數情況下耳機的音訊插孔/耳機可能是完全蒼蠅音效或不含音訊。 您可以修正這耳機，不會共用相同的中樞做為其他裝置，或中斷連線/停用其他 USB 多媒體裝置的 USB 連接埠。
* 在極少數的情況下，主機電腦的 USB 集線器無法提供足夠的電力以 Windows Mixed Reality 耳機，您可能會發現從連線到耳機耳機雜訊的暴增。

#### <a name="holograms"></a>全像投影

* 如果您已將大量的全像投影置於您家用的 Windows Mixed Reality，一些可能會消失，並再次出現，您看一下。 若要避免這個問題，移除全像投影的一些家用的 Windows Mixed Reality 該區域中。

#### <a name="motion-controllers"></a>動作控制站

* 如果輸入不會被路由至耳機中，動作控制器簡短會消失，持有旁邊聊天室界限時。 按 Win + Y，確保有藍色橫幅跨桌上型監視器將會解決此問題。 
* 有時候，當您按一下 Microsoft Edge 中的網頁上，內容會縮放而不是按一下。

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>在家用的 Windows Mixed Reality 傳統型應用程式

* 剪取工具在傳統型應用程式中無法運作。
* 傳統型應用程式不會保存在重新啟動的設定。
* 如果您使用的混合實境入口網站預覽您的桌面上，在家用的 Windows Mixed Reality 開啟桌面應用程式時，您可能會注意到無限鏡像效果。 
* 執行傳統型應用程式可能會造成效能問題非-強力 Windows 混合實境的 Pc 上;不建議。  
* 傳統型應用程式可能會自動啟動因為桌面上不可見視窗具有焦點。 
* 桌面的使用者帳戶控制提示字元中，將 顯示黑色，直到完成提示的耳機。

#### <a name="windows-mixed-reality-for-steamvr"></a>Windows Mixed 的 Reality SteamVR 的

* 若要啟動混合實境入口網站，您可能需要在更新之後，以確保必要的軟體更新適用於 Windows 10 April 2018 Update 之前會完成啟動 SteamVR。 
* 您必須是最新版的 Windows Mixed Reality SteamVR 維持與 Windows 相容的 10 April 2018 Update。 請確定自動更新已開啟的 Windows Mixed Reality SteamVR，位於 「 軟體 」 一節中的資料流的媒體櫃。  

#### <a name="other-issues"></a>其他問題

>[!IMPORTANT]
>舊版的 Windows 10 April 2018 Update 推送至測試人員 （版本 17134.5） 遺漏的軟體必須執行 Windows Mixed Reality。 建議您避免這一版，如果使用 Windows Mixed Reality。 

我們正努力在近期更新修補程式修正此更新 (10.0.17134.1) 的初始版本上使用 Surface Book 2 時，我們已找出效能變差。 我們建議您等待，直到這個問題已修正之前以手動方式更新，或等待通常推出更新。

## <a name="provide-feedback-and-report-issues"></a>提供意見反應及回報問題

請改用[HoloLens 或 Windows 10 電腦上的意見反應中樞應用程式](give-us-feedback.md)提供意見反應及回報的問題。 使用意見反應中樞，可確保所有必要的診斷資訊是以協助我們的工程師快速偵錯及解決問題。

>[!NOTE]
>請務必接受提示，詢問是否希望存取文件 資料夾的意見反應中樞 (選取**是**出現提示時)。

## <a name="prior-release-notes"></a>先前的版本資訊

* [版本資訊-2017 年 10 月](release-notes-october-2017.md)
* [版本資訊-2016 年 8 月](release-notes-august-2016.md)
* [版本資訊-2016 5 月](release-notes-may-2016.md)
* [版本資訊-2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [沈浸式耳機支援 （外部連結）](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 支援 （外部連結）](https://support.microsoft.com/products/hololens)
* [安裝工具](install-the-tools.md)
* [提供意見反應](give-us-feedback.md)

