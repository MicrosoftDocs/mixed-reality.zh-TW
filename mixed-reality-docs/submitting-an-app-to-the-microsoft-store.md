---
title: 將應用程式提交至 Microsoft Store
description: 本文提供將混合現實應用程式提交至 Microsoft Store 的秘訣，包括如何封裝和測試您的應用程式，以及傳遞認證並協助您在存放區中探索應用程式的秘訣。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式，uwp，提交，提交，篩選，中繼資料，系統需求，關鍵字，wack，認證，套件，appx，商品
ms.openlocfilehash: f2eb4093a2bea51d8c39b94d23777e426810981e
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375805"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>將應用程式提交至 Microsoft Store

[HoloLens](hololens-hardware-details.md)和 WINDOWS 10 電腦都能讓您的[沉浸式耳機](immersive-headset-hardware-details.md)執行通用 Windows 平臺應用程式。 無論您是提交支援 HoloLens 或 PC （或兩者）的應用程式，您都可以透過[合作夥伴中心](https://partner.microsoft.com/dashboard)將您的應用程式提交到 Microsoft Store。

如果您還沒有合作夥伴中心的開發人員帳戶，您可以[立即註冊](https://developer.microsoft.com/store/register)。

## <a name="packaging-a-mixed-reality-app"></a>封裝混合現實應用程式

### <a name="prepare-image-assets-included-in-the-appx"></a>準備包含在 appx 中的映射資產

Appx 建立工具需要數個映射資產，以將您的應用程式建立至 appx 套件以提交至存放區。 您可以在 MSDN 上深入瞭解[磚和圖示資產的指導方針](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx)。

| 必要的資產 | 建議的調整 | 映像格式 | 這會顯示在哪裡？ | 
|----------|----------|----------|------------------|
| 方形71x71 正方形標誌 | 任何 |  PNG | N/A | 
| 方形150x150 正方形標誌 | 150x150 正方形（100% scale）或225x225 （150% scale） | PNG | 啟動 pin 和所有應用程式（如果未提供310x310 正方形）、儲存搜尋建議、商店清單頁面、儲存流覽、儲存搜尋 | 
|  寬310x150 寬標誌 |  任何  |  PNG  |  N/A | 
|  市集標誌 |  75x75 （150% scale）  |  PNG  |  合作夥伴中心，報表應用程式，撰寫評論，我的文件庫 | 
|  啟動顯示畫面 |  930x450 （150% scale）  |  PNG  |  2D 應用程式啟動器（平板電腦） | 

另外還有一些建議的資產，可供 HoloLens 利用。

| 建議的資產 | 建議的調整 | 這會顯示在哪裡？ | 
|----------|----------|----------|
|  方形310x310 正方形標誌 |  310x310 正方形（150% scale） |  啟動 pin 和所有應用程式 | 

### <a name="live-tile-requirements"></a>動態磚需求

HoloLens 上的 [開始] 功能表會使用最大的內含正方形磚影像。

您可能會看到 Microsoft 發佈的某些應用程式具有其應用程式的3D 啟動器。 開發人員可以使用[這些指示](implementing-3d-app-launchers.md)，為其應用程式新增3d 啟動器。

### <a name="specifying-target-and-minimum-version-of-windows"></a>指定 Windows 的目標和最低版本

如果您的混合現實應用程式包含特定 Windows 版本特有的功能，請務必指定通用 Windows 應用程式將支援的目標和最小平臺版本。

**這特別適用于以[Windows Mixed Reality 沉浸式耳機](immersive-headset-hardware-details.md)為目標的應用程式，這需要至少 Windows 10 秋季建立者更新（10.0;組建16299）以正常運作。**

當您在 Visual Studio 中建立新的通用 Windows 專案時，系統將會提示您設定目標和最低版本的 Windows。 您也可以在 [專案] 功能表中變更現有專案的這項設定，然後在下拉式功能表底部的 [< 您的應用程式名稱 > 屬性]。

![設定 Visual Studio 2019 中的最低和目標平臺版本](images/visual-studio-min-version-500px.png)<br>
在 Visual Studio 中設定最低和目標平臺版本

### <a name="specifying-target-device-families"></a>指定目標裝置系列

Windows Mixed Reality 應用程式（適用于[HoloLens](hololens-hardware-details.md)和[沉浸式耳機](immersive-headset-hardware-details.md)）是通用 Windows 平臺的一部分，因此任何[目標裝置系列](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)為 "Windows. 通用" 的應用程式套件，都能夠在 HoloLens 或 Windows 10 電腦上使用沉浸式耳機來執行。 話雖如此，如果您未在應用程式資訊清單中指定目標裝置系列，您可能會不小心開啟應用程式，而不是非預期的 Windows 10 裝置。 請遵循下列步驟來指定想要的 Windows 10 裝置系列，然後[再次確認您在合作夥伴中心上傳應用程式套件以提交至存放區時，已選取正確的裝置系列。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

若要在 Visual Studio 中設定此欄位，請以滑鼠右鍵按一下 package.appxmanifest.xml 並選取 [查看程式碼]，然後尋找 [y 名稱] 欄位。 根據預設，它看起來可能如下所示：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果您的應用程式是針對**HoloLens**所建立，則您可以藉由指定「Windows 全像攝影」的目標裝置系列，確保它只會安裝在 hololens 上。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果您的應用程式特別需要**HoloLens 2**的功能（例如，眼追蹤或手動追蹤），則您可以指定目標裝置系列的「windows 全息版」和 [MinVersion 10.0.18362.0]，確保其以 windows 18362 或更新版本為目標。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

如果您的應用程式是針對**Windows Mixed Reality 沉浸式耳機**所建立，則您可以指定目標裝置系列「windows 桌面」和「10.0.16299.0」的 MinVersion，確保它只會安裝在具有 Windows 10 秋季建立者更新的 Windows 10 電腦上（Windows Mixed Reality 的必要項）。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

最後，如果您的應用程式要在**HoloLens 和 Windows Mixed Reality 沉浸式耳機**上執行，您可以確保應用程式僅適用于這兩個裝置系列，並同時為每個目標裝置系列加上一條線，並包含其各自的 MinVersion，以確保每個目標都是正確的最低 Windows 版本。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

您可以閱讀[y UWP 檔](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)，深入瞭解目標裝置系列。

### <a name="associate-app-with-the-store"></a>將應用程式與存放區產生關聯

從 Visual Studio 解決方案的 [專案] 功能表中，選擇 [儲存 > 將應用程式與存放區建立關聯]。 若您執行此動作，您可以測試您應用程式中的購買與通知案例。 當您將應用程式與存放區建立關聯時，這些值會下載到本機電腦上目前專案的應用程式資訊清單檔中：
* 套件顯示名稱
* 套件名稱
* 發行者 ID
* 發行者顯示名稱
* 版本

如果您為資訊清單建立自訂 .xml 檔，以覆寫預設 package.appxmanifest 檔案，則無法將應用程式與「市集」建立關聯。 如果您嘗試將自訂資訊清單檔與市集建立關聯，您將會看到錯誤訊息。

### <a name="creating-an-upload-package"></a>建立上傳套件

遵循[封裝適用于 Windows 10 的通用 windows 應用程式中的](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)指導方針。

建立上傳套件的最後一個步驟是使用[Windows 應用程式認證套件](#windows-app-certification-kit)來驗證套件。

如果您要將特別針對 HoloLens 的套件新增至其他 Windows 10 裝置系列上提供的現有產品，您也會想要瞭解[版本號碼可能會如何影響哪些套件會傳遞給特定客戶](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)，以及[如何將封裝散發到不同的作業系統](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)。

一般指引是適用于裝置的最高版本號碼套件，會是存放區所散發的封裝。

如果有一個 Windows 通用封裝和一個 Windows 全像的套件，而 Windows 通用套件的版本號碼較高，則 HoloLens 使用者會下載較高版本的 Windows. 通用套件，而不是 Windows 的全息版包裹. 此問題有幾個解決方案：
1. 請確定您的平臺特定套件（例如 Windows）的版本號碼一律高於您的平臺中立套件（例如 Windows）。
2. 如果您也有平臺特定套件，請勿將應用程式封裝為 [通用]，而是針對您想要在其上使用的特定平臺封裝 Windows 通用套件。

>[!NOTE]
> 若要在 HoloLens （第1代）和 HoloLen 2 上支援您的應用程式，您將需要上傳兩個應用程式套件;一個包含 HoloLens （第1代）的 x86，另一個包含 HoloLens 2 的 ARM 或 ARM64。 
> 
> 如果您在套件中同時包含 ARM 和 ARM64，則 ARM64 版本將會用於 HoloLens 2。 

>[!NOTE]
> 您可以宣告單一封裝，以適用于多個目標裝置系列

3. 建立可跨所有平臺運作的單一 Windows 通用套件。 對這方面的支援並不大，因此建議使用上述解決方案。

## <a name="testing-your-app"></a>測試您的應用程式

### <a name="windows-app-certification-kit"></a>Windows 應用程式認證套件

當您透過 Visual Studio 建立要提交至合作夥伴中心的應用程式套件時，[建立應用程式套件] wizard 會提示您針對所建立的套件執行 Windows 應用程式認證套件。 若要對存放區進行順暢的提交程式，最好先確認[Windows 應用程式認證套件測試](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx)是否已在本機電腦上傳遞您的應用程式，再將其提交至存放區。 目前不支援在遠端 HoloLens 上執行 Windows 應用程式認證套件。

### <a name="run-on-all-targeted-device-families"></a>在所有目標裝置系列上執行

Windows 通用平臺可讓您建立在所有 Windows 10 裝置系列上執行的單一應用程式。 不過，它並不保證通用 Windows 應用程式只會在所有裝置系列上工作。 在您選擇讓您的應用程式可在 HoloLens 或其他任何 Windows 10 目標裝置系列上使用時，請務必在每個裝置系列上[測試應用程式](testing-your-app-on-hololens.md)，以確保有良好的體驗。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>將您的混合現實應用程式提交至存放區

如果您要提交以 Unity 專案為基礎的混合現實應用程式，請先參閱這段[影片](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app)。

一般來說，提交適用于 HoloLens 和/或沉浸式耳機的 Windows Mixed Reality 應用程式，就像是將任何 UWP 應用程式提交到 Microsoft Store。 一旦您藉[由保留其名稱來建立應用程式](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)之後，您應該遵循[UWP 提交檢查清單](https://docs.microsoft.com/windows/uwp/publish/app-submissions)。

您要做的第一件事，就是為您的混合現實體驗[選取類別和子類別](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table)。 **請務必為您的應用程式選擇最精確的類別**，讓我們可以將您的應用程式放在正確的商店類別中，並確保它會使用相關的搜尋查詢來顯示。 **將您的 VR 標題列為遊戲並不會讓您的應用程式得到更好的曝光，** 而且可能會使其無法顯示在更適合和較不擁擠的類別中。

不過，提交程式中有四個主要區域，您會想要進行混合的現實特定選擇：
1. 在 [[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)] 底下的 [ **[產品](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** 宣告] 區段中。
2. 在 [[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)] 底下的 [ **[系統需求](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** ] 區段中。
3. 在 [[套件](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)] 底下的 [ **[裝置系列可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** ] 區段中。
4. 在其中幾個 **[商店清單頁面](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 欄位。

### <a name="mixed-reality-product-declarations"></a>混合現實產品聲明

在應用程式提交流程的 [內容] 頁面上，您會在 [ **[產品](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** 宣告] 區段中找到數個與混合現實 **[相關的選項](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 。

![混合現實產品聲明](images/product-declarations-900px.png)<br>
混合現實產品聲明

首先，您會想要識別應用程式提供混合現實體驗的裝置類型。 這可確保您的應用程式會包含在存放區中的 Windows Mixed Reality 集合中，並在連接沉浸式耳機（或在 HoloLens 上流覽商店時）呈現給使用者流覽 Store。

在「此體驗是針對 Windows Mixed Reality 而設計的：」旁，
* 只有當您的應用程式在有沉浸式耳機連線到使用者的電腦時，才會提供 VR 體驗，才選取 [**電腦**] 方塊。 您應該核取此方塊，無論您的應用程式是專門設計用來在沉浸式頭戴式裝置上執行，或是在耳機連線時提供混合現真實模式及/或額外內容的標準電腦遊戲/應用程式。
* 只有當您的應用程式在 HoloLens 上執行時，才會提供全像攝影體驗，請檢查**hololens**方塊。
* 如果您的應用程式提供兩種裝置類型的混合現實體驗，例如組建2017中的[混合現實學術「專案島」應用程式](mixed-reality-250.md)，請檢查**這兩個**方塊。

如果您選取上方的 [PC]，您會想要設定 [混合現實設定] （活動層級）。 這僅適用于連接到沉浸式耳機的電腦上執行的混合現實體驗，因為 HoloLens 上的混合現實應用程式是全球規模，而且使用者不會在安裝期間定義界限。
* 如果您的應用程式設計的目的是讓使用者停留在同一個位置（例如，您在飛機的環境中坐在一場遊戲中），請選擇 [內部] **+ [待命**]。
* 如果您的應用程式設計的目的是讓使用者在安裝期間所定義的界限內進行操作，請選擇 [**所有體驗**] （例如，您可以在其中逐步執行並進入減到最淡攻擊的遊戲）。

### <a name="mixed-reality-system-requirements"></a>混合現實系統需求

在應用程式提交流程的 [內容] 頁面上，您會在 [ **[系統需求](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** ] 區段中找到數個與混合現實 **[相關的選項](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 。

![系統需求](images/system-reqs-800px.png)<br>
系統需求

在本節中，您將識別混合現實應用程式的最小（必要）硬體和建議（選擇性）硬體。

**輸入硬體：**

如果您的應用程式支援**麥克風**（適用于[語音輸入](voice-input.md)）、 **[Xbox 控制器或遊戲台](hardware-accessories.md#bluetooth-gamepads)** ，以及（或） **[Windows Mixed Reality 動作控制器](motion-controllers.md)** ，請使用核取方塊來告知潛在客戶。 這項資訊會顯示在您應用程式的產品詳細資料頁面上，並可協助您的應用程式包含在適當的應用程式/遊戲集合中（例如，支援動作控制器的所有遊戲可能會有一個集合）。

請仔細針對輸入類型選取 [最低硬體] 或 [建議的硬體] 核取方塊。 

例如， 
* 如果您的遊戲需要動作控制器，但接受透過麥克風的語音輸入，請選取 [Windows Mixed Reality 動作控制器] 旁的 [最小硬體] 核取方塊，但 [麥克風] 旁的 [建議的硬體] 核取方塊。 
* 如果您的遊戲可以透過 Xbox 控制器/遊戲台或動作控制器來播放，您可以選取 [Xbox controller 或遊戲台] 旁的 [最低硬體] 核取方塊，然後選取 [Windows Mixed Reality 動作控制器] 旁的 [建議的硬體] 核取方塊，因為運動控制器可能會提供遊戲台的經驗。

**Windows Mixed Reality 沉浸式耳機：**

指出是否需要沉浸式耳機才能使用您的應用程式，或者是選擇性的，對於客戶滿意度和教育而言，是不可或缺的。

如果您的應用程式*只能*透過沉浸式耳機使用，請選取 [Windows Mixed Reality 沉浸式耳機] 旁的 [最小硬體] 核取方塊。 這會顯示在 [購買] 按鈕上方的 [存放區] 中，作為警告，讓客戶不會認為購買的應用程式可在其電腦上運作，例如傳統的桌面應用程式。

如果您的應用程式在桌上型電腦上執行，例如傳統的 PC 應用程式，但在有沉浸式耳機連線時提供 VR 體驗（不論您的應用程式的完整內容是否可供使用，或是只有部分），請選取 [Windows Mixed Reality] 旁的 [建議的硬體] 核取方塊沉浸式耳機。」 如果您的應用程式以傳統桌面應用程式的形式運作，而未連接沉浸式耳機，則應用程式產品詳細資料頁面上的 [購買] 按鈕不會出現任何警告。

**電腦規格：**

如果您想要讓應用程式盡可能觸達許多 Windows Mixed Reality 的沉浸式耳機使用者，您會想要以整合式[圖形的 Windows Mixed Reality 電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的電腦規格為[目標](understanding-performance-for-mixed-reality.md)。

無論您的混合現實應用程式是以最小的 Windows Mixed Reality 電腦需求為目標，或是需要特定的電腦設定（例如[Windows Mixed Reality ULTRA 電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的專用 GPU，您都應該在「最低硬體」資料行中指出有相關的電腦規格。

如果您的混合現實應用程式設計成在特定電腦設定或圖形配接器上執行得更好，或提供更高解析度的圖形，您應該在 [建議的硬體] 資料行中指出有相關的電腦規格。

這僅適用于您的混合現實應用程式使用連接到電腦的沉浸式耳機時。 如果您的混合現實應用程式只在 HoloLens 上執行，您就不需要指出電腦規格，因為 HoloLens 只有一個硬體設定。

### <a name="device-family-availability"></a>裝置系列可用性

如果您已在 Visual Studio 中[正確封裝您的應用程式](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements)，請在應用程式提交流程的 [套件] 頁面上上傳它，應該會產生一個資料表來識別您的應用程式將可供使用的裝置系列。

![裝置系列可用性資料表](images/device-family-table-900px.png)<br>
裝置系列可用性表

如果您的混合現實應用程式適用于沉浸式耳機，則至少應在表格中選取「Windows 10 桌面」。 如果您的混合現實應用程式在 HoloLens 上運作，則至少應選取「Windows 10 全像攝影版」。 如果您的應用程式同時在 Windows Mixed Reality 耳機類型上執行，例如[混合現實學術「專案島」應用程式](mixed-reality-250.md)，則應選取「Windows 10 桌上出版」和「windows 10 全像攝影」。

>[!TIP]
>許多開發人員在上傳其應用程式套件時遇到錯誤，與套件資訊清單和合作夥伴中心內的應用程式/發行者帳戶資訊相關。 使用與您的 Windows 開發人員帳戶（您用來登入合作夥伴中心的帳戶）相關聯的相同帳戶登入 Visual Studio，通常可以避免這些錯誤。 如果您使用相同的帳戶，您將能夠在封裝應用程式之前，將其與 Microsoft Store 中的身分識別建立關聯。

![將您的應用程式與 Microsoft Store 建立關聯](images/associate-your-app-700px.png)<br>
將您的應用程式與中的 Microsoft Store 建立關聯 Visual Studio

### <a name="store-listing-page"></a>商店清單頁面

在應用程式提交流程的 [[商店清單](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings)] 頁面上，有幾個地方可以讓您新增混合現實應用程式的實用資訊。

>[!IMPORTANT]
>為確保您的應用程式已由商店正確分類，並可供 Windows Mixed Reality 客戶使用，您應該將「 **Windows Mixed Reality** 」新增為應用程式的其中一個「搜尋詞彙」（您可以藉由展開 [共用欄位] 區段來尋找搜尋詞彙）。

![新增 Windows Mixed Reality 來搜尋詞彙](images/search-terms-800px.png)<br>
將「Windows Mixed Reality」新增至搜尋詞彙

## <a name="offering-a-free-trial-for-your-game-or-app"></a>為您的遊戲或應用程式提供免費試用版

在購買 Windows Mixed Reality 沉浸式耳機之前，許多消費者都不會有虛擬實境的經驗。 他們可能不知道要從密集遊戲中預期的內容，而且在沉浸式體驗中可能不熟悉自己的緩和閾值。 許多客戶也可以在未徽章為[Windows Mixed Reality 電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的電腦上，嘗試使用 Windows mixed Reality 沉浸式耳機。 基於這些考慮，我們強烈建議您考慮為付費的混合現實應用程式或遊戲提供[免費試用版](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial)。

## <a name="see-also"></a>另請參閱
* [混合實境](mixed-reality.md)
* [開發概觀](development.md)
* [應用程式檢視](app-views.md)
* [瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)
* [Unity 的效能建議](performance-recommendations-for-unity.md)
* [測試 HoloLens 上的應用程式](testing-your-app-on-hololens.md)
* [Windows Mixed Reality 最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
