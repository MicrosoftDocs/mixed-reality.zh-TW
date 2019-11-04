---
title: 匯出和建立 Unity Visual Studio 解決方案
description: 本文概述如何從 Unity 匯出混合的現實專案，讓您可以在 Visual Studio 中建立和部署。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity，visual studio，匯出，組建，部署
ms.openlocfilehash: 752a9dd002d27d24d9b80a1a97cb07a44237b9e0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435571"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>匯出和建立 Unity Visual Studio 解決方案

如果您不想要在應用程式中使用系統鍵盤，我們的建議是使用*D3D* ，因為您的應用程式會使用稍微少一點的記憶體，且啟動時間較快。 如果您在專案中使用 TouchScreenKeyboard API 來使用系統鍵盤，則需要將匯出為*XAML*。

## <a name="how-to-export-from-unity"></a>如何從 Unity 匯出

![Unity 組建設定](images/unitybuildsettings-300px.png)<br>
*Unity 組建設定*

1. 當您準備好要從 Unity 匯出專案時，請開啟 **[檔案**] 功能表，然後選取 [**組建設定**]。
2. 按一下 [新增] [**開啟場景**]，將場景新增至組建。
3. 在 [**組建設定**] 對話方塊中，選擇下列選項來匯出 HoloLens：
   * **平臺：** *通用 Windows 平臺*並務必選取 [**切換平臺**]，讓您的選擇生效。
   * **SDK：** *通用 10*。
   * **UWP 組建類型：** *D3D*。
4. **選擇性**： **Unity C#專案：** 已核取。

>[!NOTE]
>核取此方塊可讓您：
>* 在 Visual Studio 遠端偵錯程式中，對您的應用程式進行偵測。
>* 在 Unity C#專案中編輯腳本，同時使用 WinRT Api 的 IntelliSense。

5. 從 [**組建設定 ...** ] 視窗中，開啟 [**播放者設定**]。
6. 選取 [**通用 Windows 平臺**] 索引標籤的設定。
7. 展開 [ **XR 設定**] 群組。
8. 在 [ **XR 設定**] 區段中，核取 [**支援虛擬實境**] 核取方塊以新增**虛擬實境裝置**清單，並確認 **[Windows Mixed Reality]** 已列為支援的裝置。
9. 返回 [**組建設定**] 對話方塊。
10. 選取 [**組建**]。
11. 在出現的 [Windows Explorer] 對話方塊中，建立新的資料夾來保存 Unity 的組建輸出。 一般來說，我們會將資料夾命名為「應用程式」。
12. 選取新建立的資料夾，然後按一下 [**選取資料夾**]。
13. Unity 完成建立之後，Windows Explorer 視窗會開啟至專案根目錄。 流覽至新建立的資料夾。
14. 開啟位於此資料夾內的產生 Visual Studio 方案檔。

## <a name="when-to-re-export-from-unity"></a>從 Unity 重新匯出的時機

從 Unity 匯出C#應用程式時，核取 [專案] 核取方塊會建立包含所有 Unity 腳本檔案的 Visual Studio 方案。 這可讓您反復執行腳本，而不需要從 Unity 重新匯出。 不過，如果您想要變更不只是變更腳本內容的專案，就必須從 Unity 重新匯出。 您需要從 Unity 重新匯出的一些時間範例如下：
* 您可以在 [專案] 索引標籤中新增或移除資產。
* 您可以變更 [偵測器] 索引標籤中的任何值。
* 您可以從 [階層] 索引標籤新增或移除物件。
* 您變更任何 Unity 專案設定

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>建立和部署 Unity Visual Studio 解決方案

建立和部署應用程式的其餘部分會在[Visual Studio](using-visual-studio.md)中發生。 您將需要指定 Unity 組建設定。 Unity 的命名慣例可能會與您通常在 Visual Studio 中使用的不同：

|  設定  |  說明 | 
|----------|----------|
|  偵錯  |  關閉所有優化並啟用 profiler。 用來調試腳本。 | 
|  主檔  |  所有優化都已開啟，而且分析工具已停用。 用來將應用程式提交至存放區。 | 
|  發行  |  所有優化都已開啟，而且已啟用 profiler。 用來評估應用程式效能。 | 

請注意，上述清單是常見觸發程式的子集，會導致需要產生 Visual Studio 專案。 一般而言，從 Visual Studio 中編輯 .cs 檔案不需要從 Unity 中重新產生專案。

## <a name="troubleshooting"></a>[疑難排解]

如果您發現您的 Visual Studio 專案無法辨識您的 .cs 檔案編輯，請確定當您從 Unity 的 [ C#組建] 功能表產生 VS 專案時，會核取 [Unity 專案]。
