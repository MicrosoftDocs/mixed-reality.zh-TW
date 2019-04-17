---
title: Spectator 檢視
description: 將外部裝置從全像投影視覺化做為示範的外部顯示器上的混合的實境體驗或錄製視訊的混合的實境體驗。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator 檢視中，資料 iPhone、 iPad iOS OpenCV、 相機、 ARKit、 HoloLens、 混合實境、 MixedRealityToolkit，示範中，記錄
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595414"
---
# <a name="spectator-view-for-hololens"></a>HoloLens spectator 檢視

![Marker](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a>目前的重構

> [!NOTE]
>正在主動重構 HoloLens spectator 檢視。 這項工作要合併的預覽和 Pro 程式碼基底，並將支援延伸到 HoloLens 2。 

若要檢視目前 Spectator 檢視重構的狀態，請參閱 MixedRealityToolkit 和 MixedRealityToolkit Unity 的存放庫中的 '功能/spectatorView' 分支：

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

和

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a>總覽

當穿著 HoloLens，我們常常忘了，個人使用者不具有它是無法體驗，我們可以。 Spectator 檢視可讓其他人在 2D 螢幕上看到 HoloLens 使用者會看到他們的世界中。
Spectator 檢視 （預覽） 是快速且經濟實惠方式 HD 中錄製全像投影，而 Spectator 檢視 Pro 適用於專業品質的全像投影的記錄。

下表顯示的選項和其功能。 選擇最適合您的視訊錄製需求的選項：

|                                      | Spectator 檢視 （預覽） |              Spectator 檢視 Pro              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 品質                         |         Full HD         |        專業品質 filming （如同取決於 DSLR）      |
| 簡單的觀景窗移動                      |            ✔            |                                             |
| 第三位使用者檢視                    |            ✔            |                      ✔                      |
| 可以將串流處理至螢幕           |            ✔            |                      ✔                      |
| 可攜式                             |            ✔            |                                             |
| 無線                             |            ✔            |                                             |
| 其他必要的硬體         |     iPhone （或 iPad）    | HoloLens + Rig + 三腳架 + DSLR + PC + Unity |
| 硬體投資                  |           低           |                     高                    |
| 跨平台                       |           iOS           |                                             |
| 檢視器可以互動                  |            ✔            |                                             |
| 網路功能的所需 （UNET 指令碼） |            ✔            |                      ✔                      |
| 執行階段安裝程式的持續時間               |         即時         |                     慢速                    |

## <a name="spectator-view-preview"></a>Spectator 檢視 （預覽）

![Marker](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a>使用案例

- Filming HD 中的全像投影：您可以使用 Spectator 檢視 （預覽），來記錄使用 iPhone 的混合的實境體驗。 在 full HD 中記錄，並將消除鋸齒套用至全像投影和甚至陰影。 這是符合成本效益且快速的方式來擷取影片的全像投影。
- 即時示範：Stream 即時混合的實境體驗至 Apple TV 直接從 iPhone 或 iPad，延隔時間-免費 ！
- 來賓分享您的經驗：可讓非 HoloLens 使用者體驗全像投影直接從他們的手機或平板電腦。

### <a name="current-features"></a>目前的功能

- 網路自動搜索功能將電話新增至工作階段。
- 自動的工作階段處理，因此使用者會新增至正確的工作階段。
- 同步處理空間全像投影，因此所有人會看到全像投影中完全相同的位置。
- podpora iOS pro （ARKit 功能的裝置）。
- 多個 iOS 來賓。
- 錄製的視訊 + 全像投影 + 環境的聲音 + 全像音效。
- 共用工作表，因此您可以儲存影片、 電子郵件，或與其他支援的應用程式共用。


>[!NOTE] 
>Spectator 檢視 （預覽） 程式碼無法搭配 Spectator 檢視 Pro 版本程式碼。 我們建議在新的專案需要視訊錄製全像投影的情況中加以實作。

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a>授權

- [OpenCV-（3 子句 BSD 授權）](https://opencv.org/license.html)
- [Unity ARKit-（MIT 授權）](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a>如何設定 Spectator 檢視 （預覽）

### <a name="requirements"></a>需求

- [Spectator 檢視外掛程式和必要的 OpenCV 二進位檔](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)-如何建置 Spectator 檢視原生外掛程式的詳細資訊，請參閱下方。 從產生的二進位檔，您將需要︰

    - opencv_aruco343.dll
    - opencv_calib3d343.dll
    - opencv_core343.dll
    - opencv_features2d343.dll
    - opencv_flann343.dll
    - opencv_imgproc343.dll

    - zlib1.dll
    - SpectatorViewPlugin.dll
- Spectator 檢視會使用 Unity 網路功能 (UNET) 及其網路探索和空間的同步處理。 這表示應用程式時的所有互動性必須在裝置之間進行同步處理。
- Unity 2017.2.1p2 或更新版本
- 硬體
    - HoloLens
    - 執行 Windows 10 的 Windows PC
    - ARKit 相容的裝置 (iPhone 6s 及更新版本 / iPad Pro 2016 及更新版本 / iPad 2017 及更新版本)-執行 iOS 11 或更高版本
    - 與 xcode 9.2 和更新版本的 Mac
- Apple 開發人員帳戶，免費或[付費](https://developer.apple.com/)
- Microsoft Visual Studio 2017

### <a name="building-the-spectator-view-native-plugin"></a>建置 Spectator 檢視原生外掛程式

若要產生所需的檔案，請遵循下列步驟： https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md

### <a name="project-setup"></a>專案設定

1. 準備您的場景，請確保場景中的所有可見 gameobject 都包含在全球根 gameobject。

    ![全球根](images/SpecViewPhoneWorldRoot2.PNG)

2. 新增 SpectatorView prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) 您在場景。
3. 新增 SpectatorViewNetworking prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) 您在場景。
4. 選取 SpectatorViewNetworking gameobject 還有 SpectatorViewNetworkingManager 元件，您可以連結的幾件事。 如果左側不必要的指令碼，在執行階段會搜尋此元件。
    - 標記偵測 HoloLens]-> [SpectatorView/Hololens/MarkerDetection
    - 標記產生 3D]-> [SpectatorView/IPhone/SyncMarker/3DMarker

    ![SpectatorView 網路探索](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a>網路應用程式

- Spectator 檢視 UNET 用於其網路，並管理為您的所有主機用戶端連線。
- 任何應用程式特定資料，就必須同步，且您使用例如 SyncVars、 NetworkTransform、 NetworkBehavior 實作。
- 如需 Unity 網路功能的詳細資訊請造訪[多人遊戲和網路](https://docs.unity3d.com/Manual/UNet.html)。 (注意：UNet 已被取代;目前的重構 Spectator 檢視程式碼基底會解決此問題）

### <a name="building-for-each-platform-hololens-or-ios"></a>建立每個平台 （HoloLens 或 iOS）

- 針對 iOS 建置時，請確定您移除 MRTK GLTF 元件，因為這尚未與此平台相容。
- SpectatorView prefab 艟鷁沒有稱為 '平台切換器' 的元件。 選取您想要建置的平台。
    - 如果選取 'Hololens' 您應該會看到所有 gameobject 下方中變成非使用中 SpectatorView prefab iPhone gameobject 和下 'Hololens' 會變成作用中的所有 gameobject。
    - 這可能需要一些時間，視平台在您選擇 HoloToolkit 正在專案中加入或移除。

    ![平台切換器](images/SpecViewPhoneSwitcher.PNG)

- 請確定您建置的應用程式使用相同的 Unity 編輯器執行個體 （執行之間的不關閉 Unity 組建），因為發生未解決的問題，使用 Unity 的所有版本。

### <a name="running-your-app"></a>執行您的應用程式

一旦您建置並部署您應用程式的版本和 HoloLens iPhone 上，您應該能夠將它們連接。

1. 請確定這兩個裝置都位於相同的 Wi-fi 網路。
2. 在這兩個裝置，沒有特定順序上啟動應用程式。 在 iPhone 上啟動應用程式的程序應該會觸發 HoloLens 相機開啟，並開始拍攝相片。
3. IPhone 應用程式啟動時，因為它會尋找例如樓層或資料表的介面。 當找不到介面時，您應該會看到類似以下的標記。 HoloLens 顯示此標記。

    ![Marker](images/SpecViewPhoneMarker.PNG)

4. 一旦偵測到標記應該會消失的 HoloLens 和兩個裝置應該連接，並在空間上同步處理。

### <a name="recording-video"></a>錄製影片

1. 若要擷取並儲存從 iPhone 的影片，點選並按住畫面 1 秒。 這會開啟 [記錄] 功能表。
2. 點選 [紅色的記錄] 按鈕，這會啟動記錄畫面開始之前的倒數計時。
3. 若要完成錄製點選並按住畫面另一個 1 秒，然後點選 [停止] 按鈕。
4. 錄製的視訊載入之後，會出現 [預覽] 按鈕 （藍色按鈕），請點選要觀賞錄製的視訊。
5. 開啟共用工作表，選取 儲存至手機相簿。

### <a name="example-scene"></a>範例場景

可以在中找到範例場景[HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)

### <a name="troubleshooting"></a>疑難排解

**Unity 編輯器不會連線到 HoloLens 裝置所裝載的工作階段**

- 這可能是 Windows 防火牆。
- 請移至 [Windows 防火牆] 選項。
- 允許應用程式或功能通過 Windows 防火牆。
- 所有執行個體的 Unity Editor 中清單報價網域、 私人和公用。
- 然後移回至 Windows 防火牆 選項。
- 按一下 進階的設定。
- 按一下 [輸入的規則]。
- 在 Unity 編輯器的所有執行個體應該有綠色勾號。
- 在 Unity 編輯器的任何執行個體，沒有綠色勾號：
    - 按兩下它。
    - 在 動作 對話方塊中選取 允許該連線。
    - 按一下 [確定]。
    - 重新啟動 Unity 編輯器。

**在執行階段 [iPhone] 畫面會顯示 「 尋找 Floor...」但不會顯示 AR 標記。**

- IPhone 正在尋找的水平的介面，因此嘗試指 iPhone 觀景窗朝向最低限度值或資料表。 這有助於 ARKit 尋找在空間上與 HoloLens 的同步處理所需的介面。

**HoloLens 相機不會開啟自動當 iPhone 嘗試加入。**

- 請確定 HoloLens 與 iPhone 相同的 Wi-fi 網路上執行。

**執行其他 Spectator 檢視應用程式其他 hololens 時啟動 Spectator 檢視應用程式在行動裝置上的，開啟其攝影機**

- Goto NewDeviceDiscovery 元件和變更的廣播金鑰和廣播的連接埠至兩個唯一值。
- 移至 SpectatorViewDiscovery，並將廣播的索引鍵和廣播的連接埠變更為另一組唯一的數字。

**HoloLens 不會與 mac 的 Unity 編輯器連線。**

- 這是可以連結它們來 Unity 版本的已知的問題。 IPhone 的建置應該仍然運作，並連線正常。

**HoloLens 相機開啟，但無法掃描標記。**

- 請確定您建立使用相同的 Unity 編輯器執行個體 （執行之間的不關閉 Unity 建置） 的應用程式的所有版本。 這是因為未知的問題，使用 Unity。

## <a name="spectator-view-pro"></a>Spectator 檢視 Pro

![Spectator 檢視安裝程式](images/spectatorview-300px.png)

使用 Pro Spectator 檢視包含以下四個元件：
1. 特別是若要啟用 spectator 檢視，此作業取決於所建置的應用程式[混合實境中共用體驗](shared-experiences-in-mixed-reality.md)。
2. 穿著 HoloLens 使用應用程式的使用者。
3. 提供第三位使用者的觀點來看視訊 spectator 檢視相機 rig。
4. 桌上型電腦執行分享的經驗的應用程式及複合 （compositing） 全像投影 spectator 檢視影片。

![檢視 Pro spectator 的安裝程式](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a>使用案例

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


*Spectator 檢視可用於共用全像攝影版創作，不論它們是靜止影像、 視訊剪輯或即時示範。*


有三個適用於這項技術的重要案例：

**1.拍攝相片**<br>
您可以使用這項技術，來擷取您全像投影的高解析度影像。 這些映像可用於展示內容行銷事件、 將傳送給您潛在的用戶端，或甚至是應用程式提交至 Windows 市集。 您可以決定您想要用來擷取這些映像的相片相機，因此您可能會偏好品質 DSLR 相機。


![檢視 Pro 相片擷取範例 spectator](images/fall-350px.jpg)<br>
*相片擷取範例-讓它顯示下限是由熔岩。*


**2.影像擷取**<br>
影片是告訴機制來與許多人共用的全像攝影版的應用程式體驗其最佳意涵。 Spectator 檢視可讓您選擇相機、 功能濾鏡，以及框架最花色您要展示您的應用程式的方式。 它可讓您的視訊品質視訊硬體為基礎的控制項中您可以使用。

![檢視 Pro 視訊擷取範例 spectator](images/spectatorviewvideo.gif)<br>
*視訊擷取範例-錄製混合的實境共同作業體驗。*


**3.實況示範**<br>
Spectator 檢視是慣用的方法，如即時的示範，因為觀景窗位置會保持穩定或控制。 因為您可以使用高品質的視訊攝影機，您也可以產生高品質的影像，適用於大螢幕。 這也是適用於串流處理實況示範在螢幕上，可能到積極式參與者排隊等候其開啟。

### <a name="comparing-video-capture-techniques"></a>比較視訊擷取技術

[混合實境擷取](mixed-reality-capture.md)(MRC) 提供的 HoloLens 使用者會看到第一個人點的-檢視從視訊的複合。 Spectator 檢視產生的第三位使用者的觀點而言，可讓視訊的觀察者，以查看具有全像投影和穿著 HoloLens 裝置的使用者環境的影片。 因為您必須選擇一種數位相機，spectator 檢視也可以產生較高的解析度和更佳的品質影像，比 MRC 映像所使用的內建 HoloLens 相機。 基於這個理由，spectator 檢視比較適合大型應用程式映像，在 Windows 市集中，行銷的影片，或對象為投影的即時檢視。

![檢視 Pro spectator Microsoft 重點演說簡報中使用專業相機](images/spectator-view-professional-red-camera-300px.jpg)<br>
*檢視 Pro spectator Microsoft 重點演說簡報中使用專業相機*


Spectator 檢視已經過 Microsoft HoloLens 已呈現方式體驗的對象自一開始在 2015 年 1 月發表產品時的必要部分。 使用專業的安裝程式會有高需求和昂貴的價格標記，請為它。 比方說，相機會使用 genlock 訊號，以確保會追蹤系統 HoloLens 與協調的確切時間。 在此設定中，移動 spectator 檢視相機無法同時全像投影穩定符合所查看的內容直接在 HoloLens 經驗的人的體驗。

移動相機 rig，以大幅降低整體安裝程式的成本的功能時，需 spectator 檢視的開放原始碼版本。 此專案會使用嚴格掛接到 HoloLens 外部相機邴畫觶圖片和影片的全像攝影版的 Unity 專案。 **在即時的示範期間相機應維持固定位置。** 觀景窗移動可能會導致闀抖動或漂移。 這是因為視訊畫面格的時間和全像投影在電腦上的呈現可能不會精確地同步處理。 因此，讓觀景窗保持穩定或限制移動會產生接近穿著 HoloLens 的人員可以看到結果。

若要讓您的應用程式準備好 spectator 檢視，您必須建置[共用體驗](holograms-240.md)應用程式，並確保應用程式可以執行 HoloLens 以及在 Unity 編輯器中的桌面。 桌面版本的應用程式必須在該複合視訊摘要與呈現全像投影中建置的其他元件。

## <a name="how-to-set-up-spectator-view-pro"></a>如何設定 Pro Spectator 檢視 

### <a name="requirements"></a>需求

![Spectator 檢視 Pro Rig](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a>硬體購物清單

以下是建議的硬體清單，但您可以也試驗其他相容的單位。 

|硬體元件                                                                     |建議               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|適用於使用 HoloLens 模擬器的全像攝影版開發的電腦設定  |                              | 
|相機與 out HDMI 或拍攝相片 SDK                                             | 如需相片和視訊擷取，我們已測試過[還要 EOS 5d Mark III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III)相機。 針對即時的示範，我們已測試過[Blackmagic 設計生產相機 4k](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k)。<br><br>請注意，普通的相機具有 HDMI 出 (例如 GoPro) 應該會運作。 許多我們的影片使用[Canon EF 14 mm f/2.8 L II USM Ultra-wide 角度固定功能濾鏡](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q)，但您應該選擇相機功能濾鏡，符合您的需求。 | 
|擷取您的電腦，以取得從您的相機校正 rig 並預覽您的複合場景的色彩框架的卡片 |  我們已測試過[Blackmagic 設計濃度 4k 擷取 pro](https://www.amazon.com/dp/B00U3QNP7Q)。 | 
|纜線                                                                                 |  [以迷你 HDMI HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00)提供將相機連接至您擷取卡。 請確定您購買符合您的相機 HDMI 外型規格。 (GoPro，比方說，將輸出透過[Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1)。)<br><br>[HDMI 纜線](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1)檢視複合預覽監視器或電視上的摘要 | 
|台到您的 HoloLens 攝影機 aluminum 括號。 | [Aluminum 括號](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|3D 列印與數位相機 hotshoe HoloLens 掛接的配接器。| [3D 列印的配接器](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|若要掛接 hotshoe 配接器的 Hotshoe fastener                                       |  [Hotshoe Fastener](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|各種的資訊、 bolt 和工具                                                |  [1/4 到 20 」 資訊](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[1/4-20"x 3/4 」 Bolt](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[7/16 糖堅果驅動程式](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[T15 Torx](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[T7 Torx](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a>軟體元件

1. 從下載軟體[spectator 檢視的 GitHub 專案](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)。
2. [Blackmagic 擷取卡 SDK](https://www.blackmagicdesign.com/support)。 \
 桌面的視訊開發人員 SDK 中 「 最新的下載 」 搜尋。
3. [Blackmagic 桌面視訊的執行階段](https://www.blackmagicdesign.com/support)。 \
 在 最新版本下載 「 桌面的視訊軟體更新的搜尋。 \
 請確定版本編號相符的 SDK 版本。
4. [OpenCV 3.1](https://opencv.org/releases.html)校正或視訊擷取，而不需要 Blackmagic 擷取卡。
5. [Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) （選擇性）。 \
 如果您使用 Canon 相機，並享有 Canon SDK，您可以 tether 至您的電腦，才會更高解析度影像的相機。
6. Unity 的全像攝影版的應用程式開發。 \
 OSS 專案中，可以找到支援的版本。
7. 具有最新更新的 visual Studio 2015。

### <a name="building-your-own-spectator-view-pro-camera"></a>建置您自己 Spectator 檢視 Pro 相機

**請注意 &AMP; 免責聲明：** 在修改 HoloLens 硬體 （包括但不是限於，設定 「 spectator 檢視 」 您 HoloLens） 基本時，應該一律要觀察安全性預防措施。 進行任何修改之前，先閱讀所有指示與手冊。 您必須負責遵循所有的指示，並使用工具的指示。 您可能已購買或授權您 HoloLens 與有限瑕疵責任擔保 」 或 「 不提供任何擔保。 請先閱讀您適用[HoloLens 授權合約或使用規定及銷售](https://www.microsoft.com/hololens/support/warranty)若要了解您擔保的選項。

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a>Rig 組件

![HoloLens 和 DSLR 相機的組合的 Spectator 檢視 Pro rig。](images/assembly.gif)<br>
*組裝的 Spectator 檢視專業人員的 rig HoloLens 和 DSLR 相機*


* 若要移除的 HoloLens 髮帶使用 T7 螺絲起子。 鬆散的螺絲之後，請加上來自另一端迴紋針逛方式。
* 移除螺絲上限，在內部使用小型的一般標頭螺絲起子 HoloLens 上面的前端。
* 若要移除的 HoloLens 括號，若要移除您的小型 torx bolt 使用 T15 螺絲起子和攔截形狀的附件。
* 置於括號，上面的內側上使用方括號前面立體化公開孔對齊 HoloLens。 HoloLens' 手臂應該保留的方括號下方 pin。
* 將您重新附加和攔截形狀來保護以方括號 HoloLens 的附件。
* 將 hotshoe fastener 附加至您的相機的 hotshoe 中。
* 將裝載配接器連接至 hotshoe fastener 中。
* 旋轉相機功能濾鏡的平行與配接器讓朝窄的側邊。
* 使用 7/16 糖堅果驅動程式 1/4 」 糖堅果與安全位置中的配接器。
* 因此 HoloLens' 上面的前面是盡可能接近相機功能濾鏡的最上層的位置對配接器的括號。
* 4 1/4 」 具體細節使用 7/16 糖堅果驅動程式與附加括號。

#### <a name="pc-setup"></a>電腦安裝程式
* 從 [軟體元件] 區段中安裝軟體。
* 加入在主機板上開啟 PCIe 位置擷取卡。
* 從相機到外部 HDMI 位置 HDMI 纜線 （HDMI 單元） 擷取卡。
* 插入從中心 HDMI 插槽 （HDMI 外） 擷取卡選擇性預覽監視器 HDMI 纜線。

#### <a name="camera-setup"></a>照相機設定
* 因此它會輸出在完整解析度 1920 x 1080、jpeg 而不裁剪 3:4 相片的解析度，則您可以將視訊模式相機。
* 尋找您的相機 HDMI 設定並啟用**鏡像**或是**雙重監視器**。
* 設定輸出解析度 1080 p
* 關閉**即時檢視在螢幕上顯示**讓複合摘要中看不到任何螢幕覆疊。
* 開啟您的相機**即時檢視**。
* 如果使用**Canon SDK**而且想要使用 flash 單位，請停用**無訊息 LV 限定**。
* 從相機到外部 HDMI 位置 HDMI 纜線 （HDMI 單元） 擷取卡。

#### <a name="calibration"></a>校正

設定好您的觀眾檢視 rig 之後，您必須校正以取得您 HoloLens 相機的位置和旋轉位移。
* 開啟下 Calibration\Calibration.sln 校正 Visual Studio 方案。
* 在此解決方案中，您會發現檔案 dependencies.props 這會建立內含位置的第 3 個合作對象來源的巨集。
* 更新這個檔案的位置您安裝 OpenCV 3.1、 Blackmagic SDK 和 Canon SDK （如果適用）

![Visual Studio 中的相依性位置快照集](images/dependencies-600px.png)<br>
*Visual Studio 中的相依性位置快照集*


* 印出校正模式 Calibration\CalibrationPatterns\2_66_grid_FULL.png 一般、 固定介面上。
* 透過 USB 插入您的電腦程式 HoloLens。
* 更新的前置處理器定義**HOLOLENS_USER**並**HOLOLENS_PW**中**stdafx.h**有 HoloLens' 裝置入口網站的認證。
* HDMI 移轉時，將相機連接至擷取卡，並將它開啟。
* 執行校正解決方案。
* 移動棋盤式圖樣周圍的檢視，像這樣：

![校正 Spectator 檢視 Pro rig](images/calibration.gif)<br>
*校正 Spectator 檢視 Pro rig*


* 棋盤式檢視中時，會自動採取一張圖片。 移至下一步 的姿勢之前尋找 HoloLens' 上面白色燈。
* 完成時，按下**Enter**校正應用程式在建立焦點**CalibrationData.txt**檔案。
* 此檔案會儲存至**Documents\CalibrationFiles\CalibrationData.txt**
* 檢查這個檔案來查看您校正資料是否正確：
   * **DSLR RMS**應該接近 0。
   * **HoloLens RMS**應該接近 0。
   * **立體聲 RMS**可能是 20-50，這是可接受因為之間兩個相機的視野，可能會不同。
   * **轉譯**是 HoloLens' 相機中要附加的相機功能濾鏡的距離。 這是以公尺為單位。
   * **旋轉**應該接近身分識別。
   * **DSLR_fov** y 值應該接近垂直檢視欄位必須是從功能濾鏡的焦距和任何相機主體裁剪因素。
* 如果任何上述的值似乎沒有意義，校準。
* 這個檔案複製到**資產**目錄中您的 Unity 專案。

### <a name="compositor"></a>撰寫器

複合項是以在 Unity 編輯器視窗中執行的 Unity 延伸模組。 若要啟用此功能，複合項 Visual Studio 方案必須先建置。
* 開啟下 Compositor\Compositor.sln 複合項 Visual Studio 方案
* 更新 dependencies.props 校正解決方案上述的相同準則。 如果您遵循校正步驟時，此檔案會有已更新。
* 建置整個解決方案，做為版本和架構符合您的 Unity 版本的架構。 如果在有疑問，建置 x86 和 x64。
* 如果您建置適用於 x64 的解決方案，也建置 SpatialPerceptionHelper 專案為 x86，因為它會執行 HoloLens 上。
* 如果執行您的應用程式，請關閉 Unity。 Unity 必須 Dll 會在執行階段變更如果會重新啟動。
* 執行 Compositor\CopyDLL.cmd 複製到 Unity 專案從這個方案所建置的 Dll。 此指令碼會將 Dll 複製至包含的範例專案中。 設定您自己的專案之後，您可以執行 CopyDLL 以指向您的專案資產目錄，也那里複製的命令列引數。
* 啟動範例 Unity 應用程式。

### <a name="unity-app"></a>Unity 應用程式

複合項會執行在 Unity 編輯器的視窗。 包含的範例專案會有所有項目設定為使用 spectator 檢視一次複製 Dll 的複合。

Spectator 檢視需要應用程式做為執行[共用體驗](holograms-240.md)。 這表示 HoloLens 上發生的任何應用程式狀態變更需要更新過在 Unity 中執行的應用程式之間的網路。

如果新的 Unity 專案從開始，您必須先進行一些設定：
* 複製**資產/附加元件/HolographicCameraRig**範例專案到您的專案。
* 將最新的 MixedRealityToolkit 新增至您的專案，包括**Sharing**， **csc.rsp**， **gmcs.rsp**，以及**smcs.rsp**。
* 新增您**CalibrationData.txt**檔案至您的資產目錄。

![Unity 資產目錄快照集](images/files-400px.png)

* 新增**HolographicCameraRig\Prefabs\SpectatorViewManager** prefab 至場景並填寫各欄位：
   * **HolographicCameraManager**應該填入從 HolographicCameraRig prefab 目錄 HolographicCameraManager prefab。
   * **錨點**應該填入從 HolographicCameraRig prefab 目錄錨點 prefab。
   * **共用**應該填入從 MixedRealityToolkit 共用 prefab。
   * 注意：如果任何這些 prefabs 已存在於您的專案階層架構中，將使用現有 prefabs，而不是下列項目。
   * **Spectator 檢視 IP**應該附加至您的觀眾檢視 rig 您 HoloLens 的 IP。
   * **共用服務 IP**應該執行 MixedRealityToolkit SharingService 電腦的 IP。
   * 選擇性：如果您有多個檢視附加至多個電腦的 rig 的 spectator 的**本機電腦 IP**應該設有 spectator 檢視 rig 會與通訊的電腦。

![在 Unity 中的 spectator 檢視管理員屬性](images/spectatorviewmanager-500px.png)

* 啟動 MixedRealityToolkit**共用服務**
* 建置及部署應用程式，以 HoloLens D3D UWP 連接至 spectator 檢視 rig。
* 將應用程式部署到體驗中的任何其他 HoloLens 裝置。
* 請檢查**在背景中執行**下方的核取方塊**編輯/專案設定/播放程式**。

![在 Unity 中的背景設定中執行](images/run-in-bg-400px.png)
* 啟動 [複合] 視窗下的**Spectator 檢視複合項**

![在 Unity 中的 [spectator] 檢視的複合檢視](images/compositor-500px.png)

* 此視窗可讓您：
   * 開始錄製影片
   * 拍照
   * 變更全像圖不透明度
   * 變更框架位移 （以調整色彩時間戳記的擷取卡片的延遲）
   * 開啟要儲存擷取的目錄
   * 要求 spectator 檢視相機中的空間的對應資料 （如果 SpatialMappingManager 存在於您的專案）
   * 個別視覺化場景的複合檢視，以及色彩、 全像投影和 alpha 色頻。
   * 開啟您的相機。
   * 在 Unity 中按下播放。
   * 當移動觀景窗時，全像投影在 Unity 中的應該是他們在現實世界裡，相對於摘要您相機色彩。

## <a name="see-also"></a>另請參閱

* [混合的實境擷取](mixed-reality-capture.md) 
* [混合實境擷取適用於開發人員](mixed-reality-capture-for-developers.md)
* [在混合實境中共用體驗](shared-experiences-in-mixed-reality.md)
* [在 GitHub 上的 spectator 檢視 （預覽） 程式碼](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [Spectator 檢視 （預覽） 原生程式碼在 GitHub 上](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [在 GitHub 上 spectator 檢視專業人員的程式碼](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
