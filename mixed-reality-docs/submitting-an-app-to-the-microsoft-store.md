---
title: 提交至 Microsoft Store 應用程式
description: 本文提供上提交您的 Microsoft Store，包括如何封裝和測試您的應用程式和秘訣，傳遞認證，並協助您的應用程式存放區中的探索能力的混合的實境應用程式的秘訣。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式，uwp，提交，請提交、 篩選、 中繼資料、 系統需求、 關鍵字、 wack、 憑證、 封裝、 appx、 推銷
ms.openlocfilehash: 4eb69fbaa22f4864305f09d5e1bf1c1860a0d31f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594573"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>提交至 Microsoft Store 應用程式

兩者[HoloLens](hololens-hardware-details.md)以及 Windows 10 電腦加強您[沈浸式耳機](immersive-headset-hardware-details.md)執行通用 Windows 平台應用程式。 是否您上傳的應用程式支援 HoloLens 或電腦 （或兩者），您將應用程式提交到透過 Microsoft Store[合作夥伴中心](https://partner.microsoft.com/dashboard)。

如果您還沒有合作夥伴中心開發人員帳戶，您可以[立即註冊](https://developer.microsoft.com/store/register)。

## <a name="packaging-a-mixed-reality-app"></a>封裝 mixed 的 reality 應用程式

### <a name="prepare-image-assets-included-in-the-appx"></a>準備應用程式中包含的影像資產

有數個應用程式建置工具，建置應用程式的 appx 封裝以提交至市集所需的影像資產。 您可以深入了解[圖格和圖示的資產的指導方針](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx)MSDN 上。

| 所需的資產 | 建議的小數位數 | 影像格式 | 而這會顯示？ | 
|----------|----------|----------|------------------|
| 正方形 71x71 標誌 | 任何值 |  PNG | N/A | 
| 正方形 150 x 150 標誌 | 150 x 150 （100%級別） 或 225 x 225 （150%小數位數） | PNG | （如果未提供 310x310） 啟動 pin 與所有應用程式中，瀏覽市集搜尋建議，存放區 [列出] 頁面中，存放區，存放區搜尋 | 
|  寬 310 x 150 標誌 |  任何值  |  PNG  |  N/A | 
|  市集標誌 |  75 x 75 （150%小數位數）  |  PNG  |  合作夥伴中心 」、 「 報表應用程式撰寫評論，我的程式庫 | 
|  啟動顯示畫面 |  930 x 450 （150%小數位數）  |  PNG  |  2D 應用程式啟動器 （平板電腦） | 

另外還有 HoloLens 運用的一些建議的資產。

| 建議的資產 | 建議的小數位數 | 而這會顯示？ | 
|----------|----------|----------|
|  正方形 310x310 標誌 |  310x310 （150%小數位數） |  啟動 pin 與所有應用程式 | 

### <a name="live-tile-requirements"></a>即時磚的需求

HoloLens 上的 [開始] 功能表將使用的最大包含方形磚的影像。

您可能會看到 Microsoft 所發行的某些應用程式有 3D 的 launcher，可用於其應用程式。 開發人員可以新增其應用程式使用的 3D 程式啟動器[這些指示](implementing-3d-app-launchers.md)。

### <a name="specifying-target-and-minimum-version-of-windows"></a>指定目標和最低 Windows 版本

如果您的混合的實境應用程式包含專屬於 Windows 版的功能，務必指定目標和通用 Windows 應用程式將支援的最低平台版本。

**這特別適用於目標的應用程式[Windows Mixed Reality 沈浸式耳機](immersive-headset-hardware-details.md)，至少需要 Windows 10 Fall Creators Update (10.0;組建 16299） 才能正確運作。**

系統會提示您設定目標和最低 Windows 版本，當您在 Visual Studio 中建立新的通用 Windows 專案。 您也可以變更這項設定的現有專案中的 [專案] 功能表，然後 [< 應用程式名稱的 > 屬性] 底部的下拉式選單。

![將最小值和目標平台版本，在 Visual Studio 2017](images/visual-studio-min-version-500px.png)<br>
設定最小值，以在 Visual Studio 中的平台版本為目標

### <a name="specifying-target-device-families"></a>指定目標裝置系列

Windows Mixed Reality 應用程式 (兩者[HoloLens](hololens-hardware-details.md)並[沈浸式耳機](immersive-headset-hardware-details.md)) 是通用的 Windows 平台，因此任何應用程式封裝的一部分[目標裝置系列](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)"Windows.Universal"是能夠使用沈浸式耳機 HoloLens 或 Windows 10 電腦上執行。 確切地說，如果您未指定目標裝置系列在您的應用程式資訊清單中，您可能會不慎開啟應用程式設為非預期的 Windows 10 裝置。 請遵循下列步驟來指定預定的 Windows 10 裝置系列，然後[請仔細檢查上傳您的應用程式套件，在合作夥伴中心，以提交至市集時，會選取正確的裝置系列。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

若要在 Visual Studio 中設定此欄位，以滑鼠右鍵按一下 Package.appxmanifest 並選取 檢視程式碼 」，然後尋找 TargetDeviceFamily 名稱 欄位。 根據預設，它看起來可能如下所示：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果您的應用程式會建立**HoloLens**，則您可以確認它只能安裝在 HoloLens 藉由指定的 「 Windows.Holographic"的目標裝置系列。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果您的應用程式會建立**Windows Mixed Reality 沈浸式耳機**，則您可以確認它只安裝 Windows 10 Fall Creators Update （視需要的 Windows Mixed Reality） 與 Windows 10 電腦上所指定目標裝置系列 」 Windows.Desktop"和"10.0.16299.0 」 的 MinVersion。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

最後，如果您的應用程式要在兩者上執行**HoloLens 與 Windows Mixed Reality 沈浸式耳機**，您可以確保應用程式僅可供這些兩個裝置系列，並同時確保每個目標的正確包含的每個目標裝置系列，其中包含其各自的 MinVersion 列的最低 Windows 版本。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

您可以深入了解以裝置系列為目標，請閱讀[TargetDeviceFamily UWP 文件](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)。

### <a name="associate-app-with-the-store"></a>應用程式與市集建立關聯

從 Visual Studio 方案中的 專案 功能表中選擇 」 存放區 > 建立關聯的應用程式與市集建立關聯。 如果您這麼做，您可以在應用程式中測試購買和通知情況。 當您將您的應用程式關聯的存放區時，這些值會下載至應用程式資訊清單檔案目前的專案在本機電腦上：
* 套件顯示名稱
* 封裝名稱
* 發行者識別碼
* 發行者顯示名稱
* 版本

如果您覆寫預設 package.appxmanifest 檔案建立自訂.xml 檔，資訊清單，無法將您的應用程式與市集建立關聯。 如果您嘗試與市集建立關聯的自訂資訊清單檔，您會看到一則錯誤訊息。

### <a name="creating-an-upload-package"></a>建立上傳封裝

請依照下列指導方針[封裝通用 Windows 應用程式，適用於 Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)。

建立上傳封裝的最後一個步驟就驗證套件使用[Windows 應用程式認證套件](#windows-app-certification-kit)。

如果您會將套件專為 HoloLens 至現有的產品所提供其他的 Windows 10 裝置系列上，您也會想要了解[版本號碼可能會如何影響的套件會傳遞給特定的客戶](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)，並[如何將套件發佈到不同的作業系統](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)。

一般的指導方針是，最高的版本號碼套件適用的裝置將會是一個分散式存放區。

HoloLens 使用者如果沒有 Windows.Universal 封裝和 Windows.Holographic 封裝，而且 Windows.Universal 封裝具有較高的版本號碼，會下載較高的版本號碼 Windows.Universal 套件，而非 Windows.Holographic封裝。 有數種方法解決這個問題：
1. 確保您的平台特定套件，例如 Windows.Holographic 一定的版本號碼高於您的平台無從驗證套件，例如 Windows.Universal
2. 不會封裝應用程式因為 Windows.Universal 如果您也會有平台特定套件-改為 package Windows.Universal 針對您要用於特定平台

>[!NOTE]
> 您可以宣告單一封裝可套用到多個目標裝置系列

3. 建立適用於所有平台的單一 Windows.Universal 封裝。 因此建議使用上述的解決方案，不立即絕佳這個的支援。

## <a name="testing-your-app"></a>測試您的應用程式

### <a name="windows-app-certification-kit"></a>Windows 應用程式認證套件

當您建立應用程式封裝以提交至合作夥伴中心，透過 Visual Studio 時，建立應用程式套件精靈 會提示您建立的封裝對執行 Windows 應用程式認證套件。 為了順利提交程序至存放區，所以最好先確認[Windows 應用程式認證套件測試](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx)對您的應用程式傳遞到本機電腦上再一併提交至存放區。 目前不支援遠端 HoloLens 上執行 Windows 應用程式認證套件。

### <a name="run-on-all-targeted-device-families"></a>在 所有目標的裝置系列上執行

Windows 通用平台可讓您建立單一的應用程式在所有 Windows 10 裝置系列上執行。 不過，它並不保證在通用 Windows 應用程式，只是將所有裝置系列上運作。 您選擇讓 HoloLens 或任何其他 Windows 10 目標裝置系列上提供您的應用程式之前，重要的是您[測試應用程式](testing-your-app-on-hololens.md)上每個這些裝置系列，以確保良好的體驗。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>提交您的混合的實境應用程式存放區

如果您提交 mixed 的 reality 應用程式為基礎的 Unity 專案，請參閱本[視訊](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app)第一次。

HoloLens 和/或沈浸式耳機的運作方式的應用程式就如同提交至 Microsoft Store 任何 UWP 應用程式的一般情況下，提交 Windows Mixed Reality。 之後，您就[建立您的應用程式，並保留其名稱](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)，您應該遵循[UWP 提交的檢查清單](https://docs.microsoft.com/windows/uwp/publish/app-submissions)。

您將會執行第一件事之一就是[選取 類別目錄和子類別](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table)針對您的混合的實境體驗。 請務必您**選擇您的應用程式最精確的分類**，我們可以推銷您的應用程式，在正確的存放區類別中，並確保它會顯示您可以使用相關的搜尋查詢。 **因為遊戲不會導致更好的曝光度，您的應用程式中，列出 VR 標題**和可能導致它無法顯示在多個調整類別，並降低擁擠。

不過，提交程序，您會想要混合的實境特有的選取項目中有四個主要領域：
1. 在  **[產品宣告](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** 區段底下[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)。
2. 在  **[系統需求](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** 區段底下[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)。
3. 在  **[裝置系列可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** 區段底下[封裝](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)。
4. 在數個**[存放區清單頁面](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 欄位。

### <a name="mixed-reality-product-declarations"></a>混合的實境產品宣告

在  **[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 頁面上的應用程式提交程序中，您會發現與混合實境中相關的數個選項**[產品宣告](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** 一節。

![混合的實境產品宣告](images/product-declarations-900px.png)<br>
混合的實境產品宣告

首先，您會想要識別您的應用程式，可提供混合的實境體驗的裝置類型。 這可確保在市集中的 Windows Mixed Reality 集合中包含您的應用程式，並顯示在使用者瀏覽市集，連接的沈浸式耳機之後 （或瀏覽 HoloLens 上的存放區時）。

接下來為 「 這項體驗根據而設計的 Windows Mixed Reality: 」
* 請檢查**PC**方塊才沈浸式耳機連線到使用者的電腦時，您的應用程式提供 VR 體驗。 您應該檢查是否要將您的應用程式設計專用來執行在沉浸式耳機，或者它是一個標準 PC 遊戲/應用程式，提供混合的實境模式和/或額外內容，當話筒連接此方塊。
* 請檢查**HoloLens**方塊才 HoloLens 上執行時，您的應用程式提供了全像攝影版的體驗。
* 請檢查**兩者**方塊，如果您的應用程式提供混合的實境體驗這兩種裝置類型，例如[混合的實境 Academy"專案 Island"的應用程式](mixed-reality-250.md)來自 Build 2017。

如果您選取"PC"上方時，您需要設定"mixed 的 reality setup"（活動層級）。 這只適用於在電腦連線到沈浸式的耳機，隨著上 HoloLens 的混合的實境應用程式的全球規模和使用者不在安裝期間定義的範圍執行的混合的實境體驗。
* 選擇**Seated + 常設**如果使用者停留在一個位置 （範例為遊戲其中您要插入擴充槽的飛機 cockpit） 的用意設計您的應用程式。
* 選擇**所有體驗**如果您的應用程式專為使用者周圍會教他或她在安裝期間所定義的界限內的意圖 (範例可能是遊戲 where 您端步驟和鴨子閃躲前方的攻擊)。

### <a name="mixed-reality-system-requirements"></a>混合的實境系統需求

在  **[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 頁面上的應用程式提交程序中，您會發現與混合實境中相關的數個選項**[系統需求](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** 一節。

![系統需求](images/system-reqs-800px.png)<br>
系統需求

在本節中，您將混合的實境應用程式識別 （必要） 的最低硬體和建議 （選擇性） 的硬體。

**輸入的硬體：**

使用核取方塊，告訴您的應用程式是否支援的潛在客戶**麥克風**(如[語音輸入](voice-input.md))，  **[Xbox 控制器或遊戲台](hardware-accessories.md#bluetooth-gamepads)**，和/或 **[Windows Mixed Reality 動作控制站](motion-controllers.md)**。 這項資訊會呈現在存放區中的應用程式的產品詳細資料頁面上，並可協助您取得適當的應用程式/遊戲集合中包含的應用程式 （例如，集合可能存在的支援動作控制站的所有遊戲）。

要仔細考量，需選取 「 最小硬體 」 或 「 建議的硬體 」 輸入類型的核取方塊。 

例如:  
* 如果您的遊戲需要動作控制站，但接受透過麥克風的語音輸入，選取 Windows Mixed 的 Reality 移動 「 控制項 」，旁邊的 「 最小硬體 」 核取方塊，但 「 建議的硬體 」 的核取方塊旁邊 「 麥克風 」。 
* 如果您的遊戲可玩 Xbox 控制器/遊戲台或移動控制器，您可能選取 「 Xbox 控制器或遊戲台 」 旁的 「 最小硬體 」 核取方塊，然後選取 「 Windows Mixed 的 Reality 移動旁邊的 「 建議的硬體 」 核取方塊控制站 」 做為動作控制站可能會提供遊戲台升級的經驗。

**Windows Mixed Reality 沈浸式耳機：**

指出沈浸式耳機，才可使用您的應用程式，還是是選擇性的是重要客戶滿意度和教育。

如果您的應用程式可以*只*透過沉浸式耳機，選取 「 Windows Mixed 的 Reality 沈浸式耳機 」 旁的 「 最小硬體 」 核取方塊 這會做為存放區中的應用程式的產品詳細資料頁面上的 [購買] 按鈕上方警告讓客戶認為他們添購他們像傳統桌面應用程式的電腦運作的應用程式。

如果您的應用程式等傳統的 PC 應用程式中，在桌面上執行，但連線的沈浸式耳機時，可提供 VR 體驗 （您的應用程式的完整內容是否可用，或只有部分），選取 「 Windows Mixed Reality 旁邊的 「 建議的硬體 」 核取方塊沈浸式耳機。 」 在您的應用程式產品詳細資料頁面上將任何警告不顯示 [購買] 按鈕上方，如果您的應用程式函式，為沈浸式耳機沒有傳統桌面應用程式連線。

**電腦規格：**

如果您想要盡可能達到許多 Windows Mixed Reality 沈浸式耳機使用者應用程式時，您會想要[目標](understanding-performance-for-mixed-reality.md)的電腦規格[Windows 整合式圖形的混合實境電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。

混合的實境應用程式為目標的最小的 Windows Mixed Reality 電腦需求，還是需要特定的電腦組態 (例如的專用的 GPU [Windows Mixed Reality Ultra PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)，您應該使用相關指示「 最小硬體 」 資料行中的電腦規格。

如果您的混合的實境應用程式設計為較佳，或提供更高解析度的圖形，在特定電腦的組態或圖形卡上應該具有相關電腦規格中的 「 建議的硬體 」 資料行，以表示您的選擇。

這僅適用於您的混合的實境應用程式會使用連線至 PC 的沈浸式耳機。 此外，您的混合的實境應用程式只會在 HoloLens 上執行，如果您不需要為 HoloLens 只能在一個硬體設定，表示電腦規格。

### <a name="device-family-availability"></a>裝置系列可用性

如果您已經[正確封裝您的應用程式](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements)在 Visual Studio 中，將它上傳應用程式提交程序的 [封裝] 頁面上應該會產生資料表，找出您的應用程式可使用的裝置系列。

![裝置系列上市情況 」 表格](images/device-family-table-900px.png)<br>
裝置系列上市情況 」 表格

如果您的混合的實境應用程式的運作方式在沉浸式耳機，則在最低 「 Windows 10 Desktop 」 就應該選取資料表中。 如果您的混合的實境應用程式的運作上 HoloLens，則在最低 「 Windows 10 全像攝影版 」 應該被選取。 如果您的應用程式在這兩種 Windows Mixed Reality 耳機類型上執行，例如[混合的實境 Academy"專案 Island"的應用程式](mixed-reality-250.md)，應該選取 「 Windows 10 Desktop 」 和 「 Windows 10 全像攝影版 」。

>[!TIP]
>許多開發人員會遇到錯誤上, 傳其應用程式封裝與封裝資訊清單與您的應用程式/發行者帳戶資訊，在合作夥伴中心之間的不符時。 使用 Windows 開發人員帳戶 （您用來登入合作夥伴中心的那一個） 相關聯的相同帳戶登入 Visual Studio 通常可以避免這些錯誤。 如果您使用相同的帳戶，您可以在 Microsoft Store 中其身分識別您的應用程式關聯，您在封裝之前。

![您的應用程式相關聯的 Microsoft Store](images/associate-your-app-700px.png)<br>
將您的應用程式與 Visual Studio 中的 Microsoft Store 產生關聯

### <a name="store-listing-page"></a>存放區清單頁面

在 [存放區清單](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings)頁面的 應用程式提交程序時，有幾個地方，您可以新增混合的實境應用程式相關的有用的資訊。

>[!IMPORTANT]
>若要確保正確分類的存放區和 Windows Mixed Reality 客戶變成可探索您的應用程式，您應該加入 **」 Windows Mixed Reality"** 做為其中一個 「 搜尋字詞 」 （您可以尋找搜尋字詞擴充的應用程式「 共用欄位 」 一節）。

![新增至搜尋詞彙的 Windows Mixed Reality](images/search-terms-800px.png)<br>
新增至搜尋詞彙的"Windows Mixed Reality"

## <a name="offering-a-free-trial-for-your-game-or-app"></a>遊戲或應用程式的免費試用版供應項目

許多的取用者會有限制為沒有經驗與虛擬實境購買 Windows Mixed Reality 沈浸式耳機之前。 它們可能不知道什麼期望密集遊戲，並可能不熟悉如何使用自己的緩和臨界值，以嶄新的體驗。 許多客戶也可以嘗試以不具有徽章的電腦上的 Windows Mixed Reality 沈浸式耳機[Windows Mixed Reality 電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。 基於這些考量，我們強烈建議您考慮供應項目[免費試用](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial)您付費的混合的實境應用程式或遊戲。

## <a name="see-also"></a>另請參閱
* [混合實境](mixed-reality.md)
* [開發概觀](development-overview.md)
* [應用程式檢視](app-views.md)
* [了解效能 for Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Unity 的效能建議](performance-recommendations-for-unity.md)
* [測試 HoloLens 上的應用程式](testing-your-app-on-hololens.md)
* [Windows Mixed Reality 最小電腦的硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
