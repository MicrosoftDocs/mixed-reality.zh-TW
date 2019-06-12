---
title: 匯出和建置 Unity Visual Studio 方案
description: 本文概述從 Unity 匯出您的混合的實境專案，因此您可以建置並部署在 Visual Studio 中。
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity，visual studio 中，匯出、 建置、 部署
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596380"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>匯出和建置 Unity Visual Studio 方案

如果您不想在您的應用程式中使用系統鍵盤，我們建議是使用*D3D*您的應用程式會使用稍微較少的記憶體，並具有稍微快的啟動時間。 如果您使用 TouchScreenKeyboard API 專案中使用系統鍵盤，您需要將匯出為*XAML*。

## <a name="how-to-export-from-unity"></a>如何從 Unity 匯出

![Unity 組建設定](images/unitybuildsettings-300px.png)<br>
*Unity 組建設定*

1. 當您準備好從 Unity 匯出您的專案時，開啟**檔案**功能表，然後選取**組建設定...**
2. 按一下 **加入開啟的場景**將場景新增至組建。
3. 在 [**組建設定**] 對話方塊中，選擇要匯出的 HoloLens 的下列選項：
   * **平台：** *通用 Windows 平台* ，並確定選取 **切換平台** 您所選項目的才會生效。
   * **SDK:**  *通用的 10*。
   * **UWP 建置型別：**  *D3D*。
4. **選擇性**:**UnityC#專案：** 檢查。

>[!NOTE]
>核取此方塊，可讓您：
>* 偵錯您的應用程式，Visual Studio 遠端偵錯工具中。
>* Unity 中編輯指令碼C#專案時使用 IntelliSense 的 WinRT Api。

5. 從**組建設定...** 視窗中，開啟**播放程式設定...**
6. 選取 [**通用 Windows 平台設定**] 索引標籤。
7. 依序展開**XR 設定**群組。
8. 在  **XR 設定**區段中，按一下**虛擬實境支援**核取方塊以加入新**虛擬實境裝置**清單，並確認 **「 Windows 混合式但實際上"** 列為支援的裝置。
9. 返回**組建設定**對話方塊。
10. 選取 **建置**。
11. 在出現 [Windows 檔案總管] 對話方塊中，建立新的資料夾，保留 Unity 的組建輸出。 一般而言，我們將資料夾命名為 「 應用程式 」。
12. 選取新建立的資料夾，然後按一下**選取資料夾**。
13. 建置完成之後 Unity，Windows 檔案總管 視窗會開啟專案根目錄。 瀏覽至新建立的資料夾。
14. 開啟產生的 Visual Studio 解決方案檔案位於此資料夾。

## <a name="when-to-re-export-from-unity"></a>重新匯出從 Unity 的時機

檢查 」C#專案 」 核取方塊，當從 Unity 匯出您的應用程式建立 Visual Studio 方案，包含所有您的 Unity 指令碼檔案。 這可讓您逐一查看您指令碼，而不重新匯出從 Unity。 不過，如果您想要對您不只變更的指令碼內容的專案中的變更，您必須從 Unity 重新匯出。 有時候您需要重新匯出從 Unity 的一些範例包括：
* 您可以新增或移除在 [專案] 索引標籤中的資產。
* 您變更偵測器索引標籤中的任何值。
* 您可以新增或移除 [階層] 索引標籤中的物件。
* 您變更任何 Unity 專案設定

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>建置和部署 Unity Visual Studio 方案

建置和部署應用程式的其餘部分會在[Visual Studio](using-visual-studio.md)。 您必須指定 Unity 建置組態。 Unity 的命名慣例，可能會有所不同是通常用來在 Visual Studio 中：

|  組態  |  說明 | 
|----------|----------|
|  偵錯  |  關閉所有的最佳化和分析工具已啟用。 用來偵錯指令碼。 | 
|  主檔  |  所有的最佳化已開啟，且已停用分析工具。 用來提交至市集的應用程式。 | 
|  發行  |  所有的最佳化已開啟，且已啟用分析工具。 用來評估應用程式效能。 | 

請注意，上述清單為一般的觸發程序，將會導致 Visual Studio 專案，需要產生的子集。 一般情況下，編輯 Visual Studio 中的.cs 檔案，將不需要專案，以從 Unity 內重新產生。

## <a name="troubleshooting"></a>疑難排解

如果您發現，編輯您的.cs 檔案無法辨識您的 Visual Studio 專案中，請確定 「 UnityC#專案 」 會檢查當您從 Unity 的 [建置] 功能表，會在產生的 VS 專案時。
