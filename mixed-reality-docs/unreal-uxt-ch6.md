---
title: 6. 封裝並部署至裝置或模擬器
description: 教學課程系列的第 6 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 99c431920c72cf85fed5a0eec6fc72ddf9fb112c
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330229"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6.封裝並部署至裝置或模擬器

## <a name="overview"></a>概觀

在上一個教學課程中，您已新增一個簡單按鈕，將棋子重設為其原始位置。 在此最後一節中，您將會準備好要在 HoloLens 2 或模擬器上執行的應用程式。 若有 HoloLens 2，您可以從電腦串流或封裝應用程式，以直接在裝置上執行。 如果沒有裝置，您會封裝應用程式以在模擬器上執行。 本節結束時，您將會有一個可以播放的已部署混合實境應用程式，這是透過互動和 UI 完成的。

## <a name="objectives"></a>目標

* [僅限裝置] 利用全像應用程式遠端處理串流至 HoloLens 2
* 封裝應用程式並將其部署至 HoloLens 2 裝置或模擬器

## <a name="device-only-streaming"></a>[僅限裝置] 串流
在此情況下，[全像遠端處理](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting)表示將電腦或獨立 UWP 裝置中的資料串流至 HoloLens 2，而不是切換管道。 其運作方式是遠端主機應用程式會從 HoloLens 接收輸入資料流程、在虛擬沉浸式檢視中呈現內容，以及透過 Wi-fi 將內容框架串流回 HoloLens。 串流可讓您將遠端沉浸式檢視新增至現有的桌上型電腦軟體，並可存取更多系統資源。 

如果您是使用國際象棋應用程式前往此路由，將需要進行一些事項：

1.  從您的 HoloLens 2 上的 Microsoft Store 安裝**全像攝影遠端播放程式**並執行應用程式。

2.  移至 [編輯] > [專案設定]，然後勾選 [全像攝影遠端處理] 區段中的 [啟用遠端處理]。

3.  重新啟動編輯器、[尋找您裝置的 IP 位址](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi) 並將其輸入，然後按一下 [連線]。

連線之後，請按一下 [播放] 按鈕右邊的下拉箭號，然後選取 [VR 預覽]。 這會在 [VR 預覽] 視窗中執行應用程式，進而串流至 HoloLens 頭戴式裝置。 

## <a name="packaging-and-deploying-the-app"></a>封裝和部署應用程式 

>[!NOTE]
>如果這是您第一次為適用於 HoloLens 的 Unreal 應用程式進行封裝，則需從 Epic Launcher 下載支援的檔案。 
>- 移至 Epic Games Launcher 中的 [程式庫] 索引標籤、選取 [啟動] 旁邊的下拉箭號，然後按一下 [選項]。 
>- 在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。 
>![專案設定 - 描述](images/unreal-uxt/6-installationoptions.PNG)

1.  移至 [編輯] > [專案設定]。 
    * 在 [專案] > [描述] > [關於] > [專案名稱] 底下，新增專案名稱。 
    * 在 [專案] > [描述] > [發行者] > [公司辨別名稱] 底下，新增 **CN={INSERT COMPANY NAME}** 。

> [!IMPORTANT]
> 將其中一個欄位留空會導致錯誤。 

![專案設定 - 描述](images/unreal-uxt/6-cn.PNG)

2.  在 [平台] > [HoloLens] 底下，啟用 [針對 HoloLens 模擬進行建置] 和/或 [針對 HoloLens 裝置進行建置]。

3.  按一下 [封裝] (在 [簽署憑證] 旁邊) 區段中的 [產生新項目]，然後返回主視窗。

![專案設定 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  移至 [檔案] > [封裝專案]，然後選取 [HoloLens]。 
    * 建立新資料夾來儲存您的封裝，然後按一下 [選取資料夾]。 

5.  一旦封裝了應用程式後，請開啟 [Windows 裝置入口網站](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)移至 [檢視] > [應用程式]，然後尋找 [部署應用程式] 區段。

6.  按一下 [瀏覽 ...]、移至您的 **ChessApp.appxbundle** 檔案，然後按一下 [開啟]。 

    * 如果這是您第一次在裝置上安裝應用程式，請勾選 [允許我選取架構套件] 旁的方塊。 
    * 在下一個對話方塊中，包含適當的 **VCLibs** 和 **appx** 檔案 (若為裝置則為 arm64，若為模擬器則為 x64)。 您可以在儲存套件的資料夾內 **HoloLens** 底下找到這些檔案。

7.  按一下 [安裝]
    * 您現在可以移至 [所有應用程式]，然後點選新安裝的應用程式來執行，也可以直接從 **Windows 裝置入口網站**啟動應用程式。 

恭喜！ 您已完成是 HoloLens 混合實境應用程式，並可以開始進行。 不過，這不是盡頭。 MRTK 有許多獨立功能，您可以將其新增至專案，包括空間對應、注視和語音輸入，甚至是 QR 代碼。 如需這些功能的詳細資訊，請參閱 [Unreal 開發概觀](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)。