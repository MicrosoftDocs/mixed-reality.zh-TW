---
title: 6. 封裝並部署至裝置或模擬器
description: 教學課程的第 6 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 35b18e4bb289438f94433827846e94d1014385db
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840377"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6.封裝並部署至裝置或模擬器

本節會逐步引導您完成準備應用程式以在 HoloLens 2 裝置或模擬器上執行的步驟。 如果您有裝置，您可以從電腦串流至裝置，或封裝應用程式以直接在裝置上執行。 如果您沒有裝置，您必須封裝應用程式，才能在模擬器上執行。 

## <a name="objectives"></a>目標

* [僅限裝置] 透過全像應用程式遠端處理，將您的應用程式串流至 HoloLens 2
* 封裝您的應用程式並將其部署至 HoloLens 2 裝置或模擬器

## <a name="device-only-stream"></a>[僅限裝置] 串流

1.  從您的 HoloLens 2 上的 Microsoft Store 安裝**全像攝影遠端播放程式**並執行應用程式

2.  移至 [編輯] > [專案設定]  。 在 [全像攝影遠端處理] 區段中，勾選核取方塊以啟用遠端處理，然後重新啟動編輯器。

3.  輸入您裝置的 IP 位址，然後按一下 [連線]。

4.  連線之後，請在 UE4 編輯器中按一下 [播放] 按鈕右邊的下拉箭號，然後選取 [VR 預覽]。

## <a name="package-and-deploy-your-app"></a>封裝和部署您的應用程式 

1.  移至 [編輯] > [專案設定]  。 在 [專案] > [描述] > [關於] > [專案名稱]  底下，為您的專案命名。 在 [專案] > [描述] > [發行者] > [公司辨別名稱]  底下，輸入 “CN={INSERT COMPANY NAME}”。 將其中一個欄位留空會導致錯誤。 

![專案設定 - 描述](images/unreal-uxt/6-cn.PNG)

2.  在 [平台] > [HoloLens]  底下，根據您的目標選擇模擬及/或裝置。

3.  在 [封裝]  區段的 [簽署憑證]  旁，按一下 [產生新的]  按鈕，以產生新的簽署憑證。 返回主視窗。

![專案設定 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  移至 [檔案] > [封裝專案]  ，然後選取 [HoloLens]  。 建立新資料夾來儲存您的封裝，然後按一下 [選取資料夾]  。 

5.  成功封裝應用程式之後，請開啟 **Windows 裝置入口網站**，移至 [檢視] > [應用程式]  ，並尋找**部署應用程式**一節。

6.  按一下 [瀏覽...]  ，瀏覽至您的 **ChessApp.appxbundle** 檔案。 按一下 [開啟]  。 

    * 如果這是您第一次在裝置上安裝應用程式，請勾選 [允許我選取架構套件]  旁的方塊。 在下一個對話方塊中，包含適當的 VCLibs appx 檔案 (針對裝置為 arm64、針對模擬器為 x64)。 

7.  按一下 [安裝] 

恭喜您完成本教學課程！  