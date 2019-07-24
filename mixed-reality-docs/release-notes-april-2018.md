---
title: 版本資訊-2018 年4月
description: 適用于 Windows 10 2018 年4月更新的 HoloLens 和 Windows Mixed Reality 版本資訊 (也稱為 RS4)。
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: 版本資訊, 版本, windows 10, 組建, rs4, os
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524170"
---
# <a name="release-notes---april-2018"></a>版本資訊-2018 年4月

**[Windows 10 2018 年4月更新](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (也稱為 RS4) 包含與電腦連線的 HoloLens 和 Windows Mixed Reality 沉浸式耳機的新功能。 

若要更新為任一裝置類型的最新版本, 請開啟 [**設定**] 應用程式, 移至 [**更新 & 安全性**], 然後選取 [**檢查更新**] 按鈕。 在 Windows 10 電腦上, 您也可以使用[windows media 建立工具](https://www.microsoft.com/software-download/windows10), 以手動方式安裝 windows 10 2018 年4月的更新。

**Desktop 的最新版本:** Windows 10 2018 年4月更新 (**10.0.17134.1**)<br>
**HoloLens 的最新版本:** Windows 10 2018 年4月更新 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Alex Kipman 中的訊息, 以及 Windows 10 2018 年4月更新中新的混合現實功能的總覽*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沉浸式耳機的新功能

Windows 10 2018 年4月更新包含許多在桌上型電腦上使用 Windows Mixed Reality 沉浸 (VR) 耳機的改良功能, 例如: 

* **混合現實首頁的新環境**-您現在可以在 [開始] 功能表上選取 [**位置**], 在 Cliff 房屋和新的 Skyloft 環境之間做選擇。 我們也新增[了實驗性功能](add-custom-home-environments.md), 可讓您使用您所建立的自訂環境。
* **快速存取混合現實 capture** -您現在可以使用「動作控制器」來製作混合現實相片。 按住 Windows 按鈕, 然後按一下觸發程式。 這適用于環境和應用程式, 但不會捕捉以 DRM 保護的內容。
* 啟動**和調整內容大小的新選項**-應用程式現在會在您從 [開始] 功能表啟動它們時, 自動放在您的前方。 您現在也可以藉由拖曳視窗的邊緣和角落來調整2D 應用程式的大小。
* **使用「傳送」語音命令輕鬆地跳到內容**-您現在可以撥雲見日內容並說「傳送」, 快速地前往 Windows Mixed Reality 首頁內容的前方。
* **適用于混合現實首頁的[動畫3d 應用程式啟動器](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines)和[裝飾3d 物件](enable-placement-of-3d-models-in-the-home.md)** -您現在可以將動畫新增至3d 應用程式啟動器, 並允許使用者將裝飾的3d 模型從網頁或2D 應用程式放入 Windows mixed reality 首頁。
* **[適用于 SteamVR 的 Windows Mixed Reality 改善](updating-your-steamvr-application-for-windows-mixed-reality.md)** -SteamVR 的 Windows mixed reality 在全新的升級時不會「搶先存取」, 包括: 在使用動作控制器時 haptic 意見反應、改善效能和可靠性, 以及改善SteamVR 中的運動控制器外觀。
* **其他**改良功能-自動效能設定已更新, 可提供更好的體驗 (您可以[手動覆寫](#visual-quality)此設定)。 安裝程式現在提供 USB 3.0 控制器和圖形配接器常見相容性問題的詳細資訊。

## <a name="new-features-for-hololens"></a>HoloLens 的新功能

Windows 10 2018 年4月更新已抵達所有 HoloLens 客戶! 這項更新封裝了自[2016 年8月](release-notes-august-2016.md)前一次主要發行的 HoloLens 軟體以來所引進的改良功能。

### <a name="for-everyone"></a>適用于每個人

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>啟動時自動放置2D 和3D 內容</td><td>在啟動時, 2D 應用程式啟動器或 2D UWP 應用程式會以最佳的大小和距離自動放置在世界各地, 而不需要使用者將其放置。 如果<a href="app-views.md">沉浸式應用程式</a>使用2d 應用程式啟動器, 而不是<a href="3d-app-launcher-design-guidance.md">3d 應用程式啟動器</a>, 則沉浸式應用程式會從2d 應用程式啟動器自動啟動, 與 RS1 中的相同。<br><br>從 [開始] 功能表的3D 應用程式啟動器也會自動放在世界各地。 使用者可以按一下啟動器啟動沉浸式應用程式, 而不是自動啟動應用程式。 從全息影像應用程式和邊緣開啟的3D 內容也會自動放在世界各地。</td><td>從 [開始] 功能表開啟應用程式時, 不會再要求您將它放在世界中。<br><br>如果2D 應用程式/<a href="3d-app-launcher-design-guidance.md">3d 應用程式啟動器</a>放置不是最佳的, 您可以使用以下所述的新流暢應用程式操作, 輕鬆地移動它們。 您也可以藉由「移動此」來重新放置2D 應用程式啟動器/3D 內容, 然後使用 [注視] 來重新放置內容。</td>
  </tr>
  <tr>
    <td>流暢的應用程式操作</td><td>移動、調整大小和旋轉2D 和3D 內容, 而不需要輸入「調整」模式。</td><td>若要移動 2D UWP 應用程式或2D 應用程式啟動器, 只需要注視其應用程式行, 然後使用 [點按 + 按住 + 拖曳] 手勢。 您可以藉由撥雲見日物件上的任何位置來移動3D 內容, 然後使用 [點按 + 按住 + 拖曳]。<br><br>若要調整2D 內容的大小, 請注視其角落。 注視游標會變成調整大小游標, 然後您可以按住 ctrl + 拖曳以調整大小。 您也可以藉由查看邊緣和拖曳, 使2D 內容變得更高或更寬。<br><br>若要調整3D 內容的大小, 請將您的手拿到手勢框架, 然後在準備好的位置上手指。 您會看到游標變成具有2個小手的狀態。 使用您的手中, 同時按住手勢。 將您的手上移到更近或更遠的距離, 將會變更物件的大小。 將您的手向前和向後移動, 會旋轉物件。 您也可以透過這種方式來調整大小/旋轉2D 內容。</td>
  </tr>
  <tr>
    <td>使用重排的2D 應用程式水準調整大小</td><td>使 2D UWP 應用程式的外觀比例更寬, 以查看更多應用程式內容。 例如, 讓郵件應用程式夠寬以顯示預覽窗格。</td><td>只要看一下 2D UWP 應用程式的左邊或右邊緣, 即可看到調整大小游標, 然後使用點按 + 按住 + 拖曳手勢來調整大小。</td>
  </tr>
  <tr>
    <td>擴充語音命令支援</td><td>您可以使用自己的語音來執行更多動作。</td><td>嘗試下列語音命令:<ul><li>「移至開始」-帶出 [開始] 功能表或離開<a href="app-views.md">沉浸式應用程式</a>。</li><li>[移動此]-可讓您移動物件。</li></ul></td>
  </tr>
  <tr>
    <td>更新的全息影像和相片應用程式</td><td>已使用新的全息版更新了全息影像應用程式。 更新的相片應用程式。</td><td>您會注意到已更新的全息影像和相片應用程式的外觀。 「全息影像」應用程式包含數個新的全息和標籤製造者, 可讓您輕鬆地建立文字。</td>
  </tr>
  <tr>
    <td>改良的混合現實 capture</td><td>硬體快捷方式啟動和結束 MRC 影片。</td><td>將音量向上 + 向下移動3秒, 以開始錄製 MRC 影片。 再次點擊, 或使用 bloom 手勢結束。</td>
  </tr>
  <tr>
    <td>合併空格</td><td>簡化將全息合併至單一空間的空間管理。</td><td>HoloLens 會自動尋找您的空間, 不再需要您管理或選取空間。 如果您有與您的全息影像相關的問題, 您可以移至 [<b>設定] > [系統 > 全息影像] > 移除鄰近的全息影像</b>。 如有需要, 您也可以選取 [<b>移除所有全息影像</b>]。</td>
  </tr>
  <tr>
    <td>改良的音訊深度</td><td>您現在可以在嘈雜的環境中聽到 HoloLens 的效果, 並從應用程式體驗更逼真的音效, 因為它們的音效會被裝置偵測到的真實牆遮蔽。</td><td>您不需要採取任何動作, 就能享受改良的空間音效。</td>
  </tr>
  <tr>
    <td>檔案總管</td><td>在 HoloLens 中移動和刪除檔案。</td><td>您可以使用檔案<b>瀏覽器</b>應用程式, 在 HoloLens 中移動和刪除檔案。<br><br><b>變更複寫用快取資料夾路徑</b>如果您看不到任何檔案, [最近] 篩選可能會處於作用中狀態 (左窗格中的時鐘圖示會反白顯示)。 若要修正, 請在左窗格中選取 [<b>此裝置</b>檔] 圖示 (在 [時鐘] 圖示下方), 或開啟功能表並選取 [<b>此裝置</b>]。
</td>
  </tr>
  <tr>
    <td>MTP (媒體傳輸通訊協定) 支援</td><td>讓您的桌上型電腦存取 HoloLens 上的程式庫 (相片、影片、檔) 以方便傳輸。</td><td>與其他行動裝置類似, 請將 HoloLens 連線到電腦, 以帶出檔案<b>瀏覽器</b>來存取 HoloLens 程式庫 (相片、影片、檔) 以方便傳輸。<br><br><b>各種</b><ul><li>如果您沒有看到任何檔案, 請確定您登入 HoloLens 以啟用資料的存取權。</li><li>從您電腦上的檔案<b>瀏覽器</b>中, 您可以選取 [<b>裝置屬性</b>], 以查看 Windows 全像 OS 版本號碼 (固件版本) 和裝置序號。</li></ul><b>已知問題:</b>未啟用透過電腦上的檔案<b>瀏覽器</b>來重新命名 HoloLens。</td>
  </tr>
  <tr>
    <td>在安裝期間驗證入口網站網路支援</td><td>您現在可以在旅館、會議中心、零售商店或使用「網頁驗證入口」的企業中, 于來賓網路上設定 HoloLens。</td><td>在安裝期間, 選取 [網路], 視需要勾選 [自動連線], 然後在出現提示時輸入網路資訊。</td>
  </tr>
  <tr>
    <td>透過 OneDrive 應用程式的相片和影片同步處理</td><td>來自 HoloLens 的相片和影片現在會從 Microsoft Store 透過 OneDrive 應用程式進行同步處理, 而不是直接透過相片應用程式。</td><td>若要進行此設定, 請從存放區下載並啟動 OneDrive 應用程式。 第一次執行時, 系統應該會提示您自動將相片上傳到 OneDrive, 或您可以在應用程式設定中找到此選項。</td>
  </tr>
</table>

### <a name="for-developers"></a>適用於開發人員

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>空間對應改良功能</td><td>品質、簡化和效能改進。</td><td>空間對應網格會顯示為清除-需要較少的三角形來表示相同的詳細資料層級。 您可能會注意到場景中的三角形密度有變更。</td>
  </tr>
  <tr>
    <td>自動選取以深度緩衝區為基礎的焦點點</td><td>將深度緩衝區提交至 Windows, 可讓 HoloLens 自動選取焦點, 以優化全息全像的穩定性。</td><td>在 Unity 中, 移至 <b>編輯 > 專案設定 > Player > 通用 Windows 平臺 索引標籤 > XR 設定</b>, 展開  <b>WINDOWS Mixed Reality SDK</b>  專案, 並確定已核取 <b>啟用深度緩衝區共用</b>。 這會自動檢查是否有新的專案。<br><br>針對 DirectX 應用程式, 請務必在<b>HolographicRenderingParameters</b>每個畫面格上呼叫<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a>方法, 以提供深度緩衝區給 Windows。
</td>
  </tr>
  <tr>
    <td>全像 reprojection 模式</td><td>您現在可以停用 HoloLens 上的位置 reprojection, 以改善嚴格的主體鎖定內容的全息影像穩定性, 例如360度的影片。</td><td>在 Unity 中, 當 view 中的所有內容都是嚴格的主體鎖定時, 請將<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings</a>設定為<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode OrientationOnly</a> 。<br><br>針對 DirectX 應用程式, 當 view 中的所有內容都是嚴格的主體鎖定時, 請將<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">HolographicCameraRenderingParameters</a>設定為<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode OrientationOnly</a> 。</td>
  </tr>
  <tr>
    <td>應用程式量身打造 Api</td><td>Windows Api 深入瞭解您的應用程式執行位置, 例如裝置的顯示為透明 (HoloLens) 或不透明 (沉浸式耳機), 以及 UWP 應用程式的2D 視圖是否顯示在全像的 shell 中。</td><td>Unity 先前已手動公開<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings</a> , 即使在此組建之前也能正常運作。<br><br>針對 DirectX 應用程式, 您現在可以存取現有的 Api, 例如<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay. GetDefault ()。IsOpaque</a>和<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview。</a>也會在 HoloLens 上 IsCurrentViewPresentedOnHolographicDisplay。
</td>
  </tr>
  <tr>
      <td>研究模式</td><td>可讓開發人員在建立學術和產業應用程式時, 存取重要的 HoloLens 感應器, 以在電腦視覺和機器人的欄位中測試新的想法, 包括:<ul><li>四個環境追蹤攝影機</li><li>兩個版本的深度對應相機資料</li><li>兩個版本的 IR 反射率資料流程</li></ul></td><td><a href="research-mode.md">研究模式檔</a><br><a href="https://github.com/Microsoft/HoloLensForCV">研究模式範例應用程式</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>適用于商業客戶

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>在單一裝置上使用多個 Azure Active Directory 的使用者帳戶</td><td>與多個 Azure AD 使用者共用 HoloLens, 每個使用者都有自己的使用者設定和裝置上的使用者資料。</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT 專業人員中心:與多人共用 HoloLens</a></td>
  </tr>
  <tr>
    <td>變更登入時的 Wi-fi 網路</td><td>在登入之前變更 Wi-fi 網路, 讓另一位使用者第一次登入其 Azure AD 使用者帳戶, 讓使用者能夠在不同的位置和工作網站上共用裝置。</td><td>在 [登入] 畫面上, 您可以使用 [密碼] 欄位下方的網狀圖標來連線到網路。 當這是您第一次登入裝置時, 這會很有説明。</td>
  </tr>
  <tr>
    <td>整合註冊</td><td>您現在可以輕鬆地使用個人 Microsoft 帳戶設定裝置的 HoloLens 使用者新增工作帳戶 (Azure AD), 並將裝置加入其 MDM 伺服器。</td><td>只要使用 Azure AD 帳戶登入, 就會自動進行註冊。</td>
  </tr>
  <tr>
    <td>不進行 MDM 註冊的郵件同步處理</td><td>支援 Exchange Active Sync (EAS) 郵件同步處理, 而不需要 MDM 註冊。</td><td>您現在可以同步處理電子郵件, 而不需在 MDM 中註冊。 您可以使用 Microsoft 帳戶來設定裝置、下載並安裝郵件應用程式, 並直接新增工作電子郵件帳戶。</td>
  </tr>
</table>

### <a name="for-it-pros"></a>適用於 IT 專業人員

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>新的「Windows 全像企業版」作業系統名稱</td><td>清除版本命名, 以減少在 HoloLens 上啟用商業套件功能時對版本升級授權應用程式的混淆。</td><td>您可以在 [設定] [ <b>> 系統 > 關於</b>] 中查看哪個版本的 Windows 全像裝置。 如果已套用版本更新以啟用商業套件功能, 則會顯示「Windows 全像企業版」。 瞭解如何將<a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">Windows 全像商務功能解除鎖定</a>。</td>
  </tr>
  <tr>
  <td>Windows 設定設計工具 (WCD)</td><td>建立和編輯布建套件, 以透過更新的 WCD 應用程式來設定 HoloLens。 適用于版本更新、可設定的 OOBE、區域/時區、大量 Azure AD 權杖、網路和開發人員 CSP 的簡單 HoloLens wizard。 已篩選至 HoloLens 支援選項的 Advanced editor, 包括指派的存取權和帳戶管理 Csp。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT 專業人員中心:使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
    <td>可設定的安裝程式 (OOBE)</td><td>在安裝期間隱藏校正、手勢/注視訓練和 Wi-fi 設定畫面。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT 專業人員中心:使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
    <td>大量 Azure AD 權杖支援</td><td>預先註冊裝置以 Azure AD directory 租使用者, 以取得更快速的使用者設定流程。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT 專業人員中心:使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup CSP</td><td>部署設定檔以在開發人員模式中設定 HoloLens。 適用于開發和示範裝置。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT 專業人員中心:使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
  <td>AccountManagement CSP</td><td>共用 HoloLens 裝置, 並在登出或非使用中/儲存閾值後移除使用者資料, 以暫時使用。 支援 Azure AD 帳戶。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT 專業人員中心:使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
  <td>指派的存取權</td><td>Windows 指派給第一行背景工作或示範的存取權。 單一或多個應用程式鎖定。 不需要開發人員解除鎖定。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT 專業人員中心:在 kiosk 模式中設定 HoloLens</a></td>
  </tr>
  <tr>
  <td>Kiosk 裝置的來賓存取權</td><td>Windows 指派的存取權, 具備不受密碼的來賓帳戶以進行示範。 單一或多個應用程式鎖定。 不需要開發人員解除鎖定。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT 專業人員中心:在 kiosk 模式中設定 HoloLens</a></td>
  </tr>
  <tr>
    <td>設定 (OOBE) 診斷</td><td>從 HoloLens 取得診斷記錄, 讓您可以針對 Azure AD 登入失敗進行疑難排解 (將意見反應中樞提供給登入失敗的使用者之前)。</td><td>當安裝或登入失敗時, 請選擇 [新增<b>收集資訊</b>] 選項以取得診斷記錄以進行疑難排解。</td>
  </tr>
  <tr>
    <td>本機帳戶不限密碼到期</td><td>當本機帳戶密碼過期時, 移除裝置重設的中斷。</td><td>布建本機帳戶時, 您不再需要在<b>設定</b>中每42天變更密碼, 因為帳戶密碼已不再過期。</td>
  </tr>
  <tr>
    <td>MDM 同步狀態與詳細資料</td><td>從 HoloLens 中瞭解 MDM 同步狀態和詳細資料的標準 Windows 功能。</td><td>您可以在 設定 > 帳戶 中檢查裝置的 MDM 同步狀態, <b>> 存取公司或學校 > 資訊</b>。 在 [ <b>裝置同步狀態<b> ] 區段中, 您可以啟動同步處理、查看受 MDM 管理的區域, 以及建立和匯出先進的診斷報告。</td>
  </tr>
</table>

## <a name="known-issues"></a>已知問題

我們致力於提供絕佳的 Windows Mixed Reality 經驗, 但我們仍在追蹤一些已知問題。 如果您發現其他人, 請[提供意見反應給我們](give-us-feedback.md)。

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>更新之後

從 RS1 更新至 HoloLens 上的 RS4 後, 您可能會注意到下列問題:
* **Pin 重設**-釘選到 [開始] 功能表的3x3 應用程式將會在更新之後重設為預設值。 
* **應用程式和放置的全息影像重設**-您的世界中的應用程式將會在更新後移除, 而且必須在整個空間中重新放置。 
* **意見反應中樞可能不會立即啟動**-更新之後, 將需要幾分鐘的時間, 您才能啟動某些收件匣應用程式, 例如意見反應中樞, 而他們會自行更新。 
* **公司 wi-fi 憑證需要重新同步**處理-我們正在調查需要將 HoloLens 連線到不同網路的問題, 才能讓公司憑證重新同步處理至裝置, 然後才能夠重新連線至公司使用憑證的網路。 
* **H. 265 HEVC 影片播放不適用**-嘗試播放 H 的應用程式。265影片將會收到錯誤訊息。 因應措施是[存取 Windows 裝置入口網站](using-the-windows-device-portal.md), 選取左側導覽列上的 [**應用**程式], 然後**移除**HEVC 應用程式。 然後, 從 Microsoft Store 安裝最新的[HEVC 影片延伸](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7)模組。 我們正在調查此問題。 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>適用于開發人員: 更新執行 Windows 10 2018 年4月更新之裝置的 HoloLens 應用程式

除了一份絕佳的[新功能](#new-features-for-hololens)清單之外, Windows 10 2018 年4月更新 (RS4) (適用于 HoloLens) 會強制執行先前版本未進行的一些程式程式碼為:
* **使用敏感性資源 (相機、麥克風等) 的許可權要求**-HoloLens 上的 RS4 將會強制執行應用程式的許可權要求, 以存取機密資源, 例如相機或麥克風。 RS1 on HoloLens 並不會強制執行這些提示, 因此, 如果您的應用程式會直接存取這些資源, 它可能會在 RS4 中損毀 (即使使用者將許可權授與所要求的資源)。 如需詳細資訊, 請參閱相關的[UWP 應用程式功能](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations)宣告一文。
* 對 HoloLens**以外的應用程式呼叫**RS4, 將會強制適當地使用[ *Windows. 啟動器*類別](https://docs.microsoft.com/uwp/api/Windows.System.Launcher), 以從您自己的應用程式啟動另一個應用程式。 例如, 我們看到從非 ASTA (UI) 執行緒呼叫*LaunchUriForResultsAsync*的應用程式有問題。 這在 HoloLens 上會成功 RS1, 但是 RS4 需要在 UI 執行緒上執行呼叫。

### <a name="windows-mixed-reality-on-desktop"></a>桌上型電腦上的 Windows Mixed Reality

#### <a name="visual-quality"></a>視覺品質

* 如果您注意到 Windows 10 4 月2018之後, 圖形比以前更模糊, 或是視圖的欄位在耳機上看起來很小, 則自動效能設定可能已變更, 以便在較不強大的情況下維持足夠的畫面播放速率圖形配接器 (例如 Nvidia 1050)。 您可以手動覆寫此值 (如果您選擇), 方法是流覽至 [設定] > [混合] [ **> 耳機], > 體驗選項 > 變更**並將 [自動] 變更為 [90 Hz]。 您也可以嘗試將**視覺品質**(在相同的 [設定] 頁面上) 變更為 [高]。

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality 設定

* 當設定具有耳機連線的 Windows 時, 您的電腦監視器可能會空白。 拔下頭戴式裝置以啟用電腦監視器的輸出, 以完成 Windows 安裝程式。
* 如果您沒有連接耳機, 當您第一次造訪 Windows Mixed Reality 首頁時, 可能會錯過其他秘訣。
* 其他 Bluetooth 裝置可能會造成與動作控制器的干擾。 如果動作控制器有連線/配對/追蹤問題, 請確定藍牙無線電 (如果外部品牌) 已插入無障礙的位置, 而不是緊接在另一個藍牙品牌旁。 也請嘗試在 Windows Mixed Reality 會話期間關閉其他 Bluetooth 週邊設備, 以查看是否有説明。

#### <a name="games-and-apps-from-the-microsoft-store"></a>Microsoft Store 的遊戲和應用程式

* 有些以圖形化的遊戲 (如 Forza Motorsport 7) 可能會在 Windows Mixed Reality 內播放時, 導致電腦的效能問題降低。

#### <a name="audio"></a>音訊

* 如果您在使用 Windows Mixed Reality 耳機之前, 已在主機電腦上啟用 Cortana, 您可能會遺失套用至您在 Windows Mixed Reality 首頁所放置之應用程式的空間音效模擬。 
   * 解決的辦法是在連接到您電腦的所有音訊裝置上啟用「Windows Sonic for 耳機」, 甚至是您的耳機連線音訊裝置:
      1. 以滑鼠左鍵按一下桌面工作列上的 [喇叭] 圖示, 然後選取 [從音訊裝置清單]。
      2. 以滑鼠右鍵按一下桌面工作列上的 [喇叭] 圖示, 然後在 [說話者設定] 功能表中選取 [Windows Sonic for 耳機]。
      3. 針對所有音訊裝置 (端點) 重複上述步驟。
   * 另一個選項是在啟動 Windows Mixed Reality 之前, 關閉桌面上**設定** >  **cortana**中的 [讓 cortana 回應您的 cortana]。
* 當另一個多媒體 USB 裝置 (例如網路凸輪) 與 Windows Mixed Reality 耳機共用相同的 USB 集線器 (外部或在您的電腦內) 時, 在罕見的情況下, 耳機的音訊插座/耳機可能會有一聲聲或完全沒有音訊。 您可以將您的耳機修正為 USB 埠, 而該埠不會與其他裝置共用相同的中樞, 或中斷連線/停用其他 USB 多媒體裝置。
* 在極罕見的情況下, 主機電腦的 USB 集線器無法提供足夠的電源給 Windows Mixed Reality 頭戴式裝置, 而您可能會注意到連接到耳機的耳機突然激增。

#### <a name="holograms"></a>全息

* 如果您在 Windows Mixed Reality 首頁中放置了大量的全息影像, 有些可能會在您進行流覽時消失並重新出現。 若要避免這種情況, 請在 Windows Mixed Reality 首頁的該區域中移除部分全息影像。

#### <a name="motion-controllers"></a>運動控制器

* 如果未將輸入路由傳送至耳機, 則在會議室界限旁邊時, 移動控制器將會短暫消失。 按 Win + Y 以確保桌上型電腦監視器上有藍色橫幅可解決此問題。 
* 有時候, 當您按一下 Microsoft Edge 中的網頁時, 內容將會縮放, 而不是按一下。

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 首頁中的桌面應用程式

* 剪取工具無法在桌面應用程式中運作。
* 桌面應用程式不會在重新開機時保存設定。
* 如果您在桌面上使用混合現實入口網站預覽, 在 Windows Mixed Reality 首頁中開啟桌面應用程式時, 可能會注意到無限的鏡像效果。 
* 執行桌面應用程式可能會造成非 Ultra Windows Mixed Reality 電腦上的效能問題;不建議使用此選項。  
* 桌面應用程式可能會自動啟動, 因為桌面上的不可見視窗有焦點。 
* 桌面使用者帳戶控制提示會使耳機顯示黑色, 直到提示完成為止。

#### <a name="windows-mixed-reality-for-steamvr"></a>適用于 SteamVR 的 Windows Mixed Reality

* 您可能需要在更新之後啟動混合現實入口網站, 以確保在啟動 SteamVR 之前, 已完成 Windows 10 2018 年4月更新的必要軟體更新。 
* 您必須使用最新版本的 Windows Mixed Reality for SteamVR, 才能與 Windows 10 2018 年4月更新保持相容。 請確定已針對 SteamVR 的 Windows Mixed Reality 開啟自動更新, 此功能位於您媒體櫃的「軟體」區段中。  

#### <a name="other-issues"></a>其他問題

>[!IMPORTANT]
>推送至內部人員 (版本 17134.5) 的 Windows 10 2018 年4月更新版本, 缺少執行 Windows Mixed Reality 所需的一段軟體。 如果使用 Windows Mixed Reality, 建議您避免此版本。 

在此更新的初始版本 (10.0.17134.1) 上使用 Surface Book 2 時, 我們已識別出效能衰退, 我們正致力於在即將推出的更新修補程式中進行修正。 建議您在手動更新或等待更新正常推出之前, 先等待這項修正。

## <a name="provide-feedback-and-report-issues"></a>提供意見反應和報告問題

請[在 HoloLens 或 Windows 10 電腦上使用意見反應中樞應用程式](give-us-feedback.md), 以提供意見反應並回報問題。 使用意見反應中樞可確保包含所有必要的診斷資訊, 以協助我們的工程師快速地進行分析並解決問題。

>[!NOTE]
>請務必接受提示, 詢問您是否希望意見反應中樞存取您的 [檔] 資料夾 (出現提示時選取 **[是]** )。

## <a name="prior-release-notes"></a>先前的版本資訊

* [版本資訊 - 2017 年 10 月](release-notes-october-2017.md)
* [版本資訊 - 2016 年 8 月](release-notes-august-2016.md)
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [沉浸式耳機支援 (外部連結)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 支援 (外部連結)](https://support.microsoft.com/products/hololens)
* [安裝工具](install-the-tools.md)
* [提供意見反應給我們](give-us-feedback.md)

