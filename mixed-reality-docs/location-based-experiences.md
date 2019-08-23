---
title: 以位置為基礎的娛樂與 Windows Mixed Reality
description: 取得 Unity 中基礎全像原生物件的存取權。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: mixed reality、vr、lbe、location
ms.openlocfilehash: e23d17ff2b07c636c98a9f19a5dd20f4dc558bf7
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69983396"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>以位置為基礎的娛樂與 Windows Mixed Reality

過去幾年來, 我們在以位置為基礎的娛樂類別中目睹了大量的成長和創新。 傳統地點 (例如主題公園和 theatres) 已開始為現有的乘車和安裝提供可免費體驗的沉浸式多玩家體驗。 新的操作員和地點為 masses 帶來了獨特的多 sensorial、多玩家體驗。 所有這些體驗都會推播信封, 以瞭解混合現實的可能性。

本檔是在以位置為基礎的娛樂類別中開始使用 Windows Mixed Reality 的指南。 下列指導方針可能會另外適用于以位置為基礎的體驗 (例如訓練、產品設計或其他使用案例)。

## <a name="engineering-faq"></a>工程常見問題

### <a name="hardware"></a>硬體

**問題解答Microsoft 及其合作夥伴可以使用哪些硬體來進行設定？**

答：Microsoft 及其 OEM 合作夥伴提供了一套吸引人的裝置組合, 視您的需求而定。  

如果您提供給客戶的體驗需要虛擬實境耳機, 則來自 HP、Samsung 和 Acer 的下列市場頭戴式耳機非常適合。 每個耳機都有自己的差異屬性。 下列各項的詳細資訊。

HP 回音:[詳細資料](https://hp.com/go/Reverbpro)

Samsung 電影對白 +:[詳細資料](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer[詳細資料](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

如果您的位置專門從事需要使用「觀看」耳機的混合或擴充現實體驗, 您可以購買 Microsoft HoloLens 2 (現已開放訂購單)。  

HoloLens 2:[預先訂購的利息](https://www.microsoft.com/en-us/hololens/buy)

如果您要試驗需要先進的電腦視覺、語音和本文追蹤的經驗, 您可能會發現 Azure Kinect DK 符合您的需求。  

Azure Kinect:[詳細資料](https://azure.microsoft.com/en-us/services/kinect-dk/)

**問題解答我可以使用哪些死忠電腦群組合來執行電腦行動網卡的 VR 體驗？**

針對電腦行動網卡的 VR 體驗, 我們的 Oem 提供了絕佳的死忠電腦選擇, 專為該需求而打造。

HP 剛剛啟動了其 HP VR 死忠 G2, 這是世界上最強大的穿戴式電腦–已針對免費漫遊體驗優化, 現在提供了 30% 以上的 RTX 2080 GPU 功能。 [詳細資料](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>安裝程式

**問題解答如何更輕鬆地設定設定和自訂 LBE 的混合現實入口網站？**

>[!NOTE]
>這項功能需要 version 2000.19061.1011.0 或更高版本。  

您可能會發現您需要更多的混合現實入口網站自訂, 而不是通常透過應用程式來將應用程式部署到 kiosk 或自訂體驗。 混合現實入口網站的最新7月更新支援數個可透過設定檔執行下列動作的先進設定:  

允許失敗的系統檢查–安裝程式通常會先檢查電腦是否與 Windows Mixed Reality 相容, 再完成安裝程式。 若略過這種情況, 可能會在嘗試執行 Windows Mixed Reality 時發生問題 (如果有相容性問題)。  

略過裝置附屬應用程式– DCA 提供由製造商提供的耳機特定設定步驟, 並可讓您更新耳機的固件。  

略過房間設定–不會收到提示以建立房間界限, 您可以直接進入位於站上/待命模式的頭戴式裝置。  

略過從存放區安裝應用程式-一般安裝程式會安裝數個存放區應用程式, 包括3D 檢視器和 Edge 360 檢視器附加元件。 這會略過這些應用程式的安裝, 但您可能會遺失裝置功能。  

以全螢幕顯示預覽–混合式現實入口網站會預設為在使用耳機時, 于桌上型電腦上以全螢幕顯示耳機預覽。  

隱藏新的您的面板-這會防止新的 [在您啟動混合現實入口網站時] 面板擴充。  

#### <a name="how-to-configure"></a>如何設定:  

若要設定其中任何一項設定, 您必須在此目錄下建立名為_UserConfig_的檔案: _$env:\\ LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState_

對於大部分使用者來說, 這看起來像是 _\<C:\Users\\ username > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState_

JSON 檔案應該有下列內容, 並針對您想要啟用的上述任何設定設定「true」:  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**問題解答有關于設定 playspace 的指引嗎？**

答：設定 playspace 應如同使用取用者安裝經驗一樣。 房間設定程式也可讓您定義房間界限。 您可以在[這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)閱讀更多有關設定房間界限的詳細資訊。

如上述檔中所述, 最大合理單一座標 playspace 是大約5mx5m。 如果您想要有更大的區域, 您可以利用 Windows 全像 API 堆疊中的空間錨點功能。 使用此 API 將需要在您所產生的體驗中進行自訂工程。  

如需如何針對不同空間大小優化內容的詳細資訊, 請參閱[這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems)。
 

**問題解答我的空間太大, 當我嘗試設定界限的經驗時, 就會發生錯誤。若要設定我的大型免費漫遊體驗, 我該怎麼做？**

答：若要設定比 ~ 18x18ft 更大的空間, 您將無法使用系統所提供的界限體驗。  界限系統依賴單一固定座標「錨點」, 而當使用者太遠離開中央階段錨點時, 可能會變得不穩定。 

相反地, 您可以設定「固定」模式, 這不會顯示界限或設定階段界限或 playspace。  然後, 您必須在應用程式內設定多個空間錨點, 以參考實體界限區域。 

應用程式開發人員負責顯示必要的保護措施, 讓使用者不會與實體的周圍環境衝突。  這些可能是經驗或自訂遊戲界限視覺效果中的數位牆。 

您可以在[這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)找到使用 WMR 設定房間界限的指引。

**問題解答Playspace 的來源在哪裡？**

答：Playspace 的來源是由房間設定經驗決定, 特別是在安裝期間按下中間按鈕時的 HMD 位置。 

### <a name="multi-player-setup"></a>多玩家設定

**問題解答我要在我的場所部署多玩家體驗。Windows Mixed Reality 是否支援這種情況？**

答：Mixed Reality 空間資料封裝工具是一種搶鮮版 (Beta) 功能, 可讓您將空間資料從一部電腦移植到另一部電腦, 以在相同的空間中將多個玩家當地語系化。 您可以在[這裡](mixedrealityspatialdatapackager.md)存取工具並深入瞭解。

### <a name="tracking"></a>修訂

Q:Windows Mixed Reality 耳機中的追蹤技術如何運作？  

Mixed Reality 與 HoloLens 共用相同的追蹤技術。 若要深入瞭解內部追蹤系統, 請參閱[這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system)的檔。

如需更高層級空間對應系統運作方式的說明, 請參閱[這裡](spatial-mapping-design.md)的說明。

**問題解答取得可靠的追蹤磁片區是否有任何最佳作法？**

若要最佳設定追蹤成功的環境, 您可以閱讀這[篇文章](environment-considerations-for-hololens.md)中的最佳作法。

**問題解答在倉儲級別的空間或優化中追蹤是否有任何特定的細節需要考慮？**

答：下列作法可協助取得更可靠的追蹤磁片區:  

在房間中提供多個位置重迭的各種功能, 可協助追蹤系統取得穩固的鎖定。 請考慮隨機繪製 splatters 和影線, 而不是使用實線輪廓樣式線條。 

盡可能減少您區域中的動態光源範圍。 混合現實 Hmd 上的追蹤攝影機不是 HDR, 而且具有 AGC (自動取得) 和 AEC (自動曝光) 來處理不同光源。 視表面光線、模式和對比的分佈而定, AGC 或 AEC 可能會結束您的所有白或黑室, 而這可能會使您的功能相對「色彩」而沖蝕。 如果您嘗試將內部圖片放在具有亮日光背後的外部視窗前方, 並調整曝光, 讓您可以查看外的詳細資料, 則內部的所有內容都是 underexposed 和黑色。 或者, 如果設定為 [內部], 則外部的所有專案現在都會 overexposed, 而且全部都是白色。  

如果追蹤攝影機有時可能會原因的房間 (甚至是額外負荷) 中的聚光燈, 這可能會使追蹤攝影機的 AEC/AGC 混淆。 平面/散射光源有助於。  

### <a name="mixed-reality-cloud-services-and-azure"></a>混合現實雲端服務和 AZURE 

**問題解答Microsoft Azure 可以如何協助我的企業規模？**

答：以 Azure 為基礎的現場和遠端系統管理可協助您的企業成為資料驅動、降低營運成本, 並在現有和新的位置調整部署規模。 Azure 雲端服務 (例如 Azure 儲存體、Azure Functions、App Service、Azure 網路和 IOT 中樞) 可協助下列使用案例:  

遠端裝置部署 & 管理 

即時現場分析 

智慧型的適應性 LBE 遊戲 

LBE 內容串流和部署 

LBE Player 喜好設定熱度圖 

LBE 保留與預約系統 

**問題解答我正在開發空間 MMOG, 以部署大量的空間。協助我管理內容和物件持續性的任何服務？**

答：Azure 空間錨點是全新的混合現實服務, 可在 HoloLens、iOS 和 Android 裝置上啟用多使用者、空間感知的混合現實體驗。 您可以在[這裡](https://azure.microsoft.com/en-us/services/spatial-anchors/)深入瞭解 Azure 空間錨點。

**問題解答.我們的場地專門從事多玩家體驗, 而我想要專注于內容和前端開發的開發時間。是否有可協助我啟動或卸載後端開發的供應專案？**

答：Azure PlayFab 是適用于即時遊戲的完整後端平臺。 您可以在[這裡](https://playfab.com/)深入瞭解。

### <a name="misc"></a>其他

**問題解答我使用 SteamVR 來部署我的經驗。Windows Mixed Reality 與 SteamVR 搭配使用嗎？**

答：適用于 SteamVR 的 windows Mixed Reality 可讓使用者在 Windows Mixed Reality 沉浸式耳機上執行 SteamVR 體驗。 [在這裡](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)深入瞭解 STEAMVR with WMR。

### <a name="support-and-community"></a>支援和社區  

以下是一些實用的資源, 可與我們小組的主題專家互動、取得疑難排解支援, 以及貢獻更廣泛的混合現實開發人員。  

如果您遇到任何公開發行的功能問題, 請使用意見反應中樞提出錯誤。如需相關指引, 請參閱此[頁面](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback)。

如需 WMR 的其他疑難排解協助, 請[提出支援要求](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782)以與我們的客戶支援小組聯繫。

加入我們的 HoloDevelopers 時差頻道, 與開發人員共同作業, 與小組的主題專家合作: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter遵循我們的混合現實開發人員關係小組, 取得新聞、活動和更新@MxdRealityDev 

如果您的工作時間是在三藩市或前後, 則 Microsoft Reactor 一律會發生一些問題。 您可以在[這裡](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco)看到我們的事件行事曆。