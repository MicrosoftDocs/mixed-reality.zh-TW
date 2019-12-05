---
title: 入門教學課程 - 2。 初始化您的專案和第一個應用程式
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: d4e58e2c9236ba35b4394fd80cde3843edaa6f57
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491208"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化您的專案和第一個應用程式

在此第一課中，您將了解[混合實境工具組 (MRTK)]()提供的一些功能，然後啟動第一個適用於 HoloLens 2 的應用程式，並將其部署到裝置。

## <a name="objectives"></a>目標

* 最佳化 Unity 以用於 HoloLens 開發。
* 匯入資產並設定場景。
* 空間對應網格、手部網格和畫面播放速率計數器的視覺效果。

## <a name="instructions"></a>指示

### <a name="create-new-unity-project"></a>建立新的 Unity 專案

1. 啟動 Unity。
2. 選取 [新增]  。
![第 1 課第 1 節第 2 步](images/mrlearning-base-ch1-1-step2.JPG)

3. 輸入專案名稱 (例如："MixedRealityBase")。
![第 1 課第 1 節第 3 步](images/mrlearning-base-ch1-1-step3.JPG)
4. 輸入要儲存專案的位置。
![第 1 課第 1 節第 4 步](images/mrlearning-base-ch1-1-step4.JPG)
5. 確定專案已設定為 **3D**。
![第 1 課第 1 節第 5 步](images/mrlearning-base-ch1-1-step5.JPG)
6. 按一下 [建立專案]  。
![第 1 課第 1 節第 6 步](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>設定適用於 Windows Mixed Reality 的 Unity 專案

1. 請移至 [檔案]   >  [建置設定]  來開啟 [建置設定]  視窗。
![第 1 課第 2 節第 1 步](images/mrlearning-base-ch1-2-step1.JPG)
2. 選取 [通用 Windows 平台]  ，然後按一下 [切換平台]  按鈕來切換平台。 HoloLens 2 上執行的應用程式必須與通用 Windows 平台 (UWP) 相容。
![第 1 課第 2 節第 2 步](images/mrlearning-base-ch1-2-step2.JPG)
3. 在 [建置] 視窗中按一下 [播放器設定]  按鈕來啟用虛擬實境，然後在偵測程式面板的 [XR 設定] 下啟用 [支援的虛擬實境]  核取方塊，如下圖所示。 請注意，您可能需要將 [建置設定]  視窗拖曳到其他位置，才能看到偵測程式面板。 [支援的虛擬實境]  核取方塊也適用混合實境和擴增實境頭戴式裝置，因為其與立體視覺 (為每個眼睛轉譯不同影像) 的啟用有關連。![第 1 課第 2 節第 3 步](images/mrlearning-base-ch1-2-step3.JPG)
4. 此外，在 [XR 設定] 下，將 [立體聲轉譯模式]  變更為 [單通道執行個體化]  。 此[轉譯管線樣式](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)通常是 HoloLens 2 的最高效能。 如果您對 Unity 環境的其他效能設定感興趣，請遵循[這些指示](recommended-settings-for-unity.md)。
![第 1 課第 2 節第 4 步](images/mrlearning-base-ch1-2-step4.jpg)
5. 從相同的偵測程式面板，確認 [發佈設定]  底下的功能區段中已啟用 [空間感知]  核取方塊。 空間感知可讓我們將混合實境裝置 (例如 HoloLens 2) 上的空間對應網格視覺化。 [發佈設定] 位在偵測程式面板中的 [XR 設定] 上方及 [其他設定] 下方。
![第 1 課第 2 節第 5 步](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > 雖然未在本節中使用，但您可以啟用一些其他常見功能，包括麥克風  (適用於語音命令) 和 InternetClient  (適用於連線到需要網路連線的服務)。

### <a name="import-the-mixed-reality-toolkit"></a>匯入混合實境工具組

1. 下載[混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [基礎套件 2.1.0 版](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)，並將其儲存在您電腦上的資料夾。

2. 匯入您在上一個步驟中下載的「混合實境工具組」  套件。 從按一下 [資產]   >  [匯入]   >  [自訂套件]  開始，選取 [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage]  ，然後將它開啟以便開始匯入程序。 請稍候幾分鐘讓匯入程序完成。
    ![第 1 課第 3 節第 2a 步](images/mrlearning-base-ch1-3-step2a.JPG) ![第 1 課第 3 節第 2b 步](images/mrlearning-base-ch1-3-step2b.JPG)

3. 在下一個快顯視窗中，按一下 [匯入]  ，開始將選取的套件匯入 Unity 專案。 請確定已核取所有項目，如圖所示。
    ![第 1 課第 3 節第 3 步](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > 如果您看到快顯對話方塊詢問是否套用混合實境工具組的預設設定，請按一下 [套用]  。 匯入以進行自動化安裝時，MRTK 會分析您的專案是否有任何遺漏的建議設定。 視您的設定而定，快顯看起來可能會與下圖不同。

    ![第 1 課第 3 節第 4 步備註 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>設定混合實境工具組

1. 藉由選取 [混合實境工具組]   >  [新增至場景和設定..]  ，將 [混合實境工具組]  新增至您目前的場景。 從功能表列。 如果您在匯入混合實境工具組之後沒有看到此功能表項目，請重新啟動 Unity。
    ![第 1 課第 4 節第 1 步](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > 您可能會看到一個快顯對話方塊，用來選取[混合實境工具組的設定檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。 按兩下名為 DefaultHoloLens2ConfigurationProfile  的設定檔。

2. 您的場景會有數個新項目和修改。 若要以不同名稱來儲存場景，請按一下 [檔案]   >  [另存新檔...]  ，然後為場景指定名稱，例如 BaseScene  。 為了讓場景井然有序，您可以將場景儲存到專案 [資產]  資料夾中的 [場景]  資料夾。
    ![第 1 課第 4 節第 2a 步](images/mrlearning-base-ch1-4-step2a.JPG) ![第 1 課第 4 節第 2b 步](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>對您的裝置建置應用程式

1. 如果您已關閉前面幾節中的 [建置設定]  視窗，請移至 [檔案]   >  [建置設定]  來重新開啟 [建置設定]  視窗。
    ![第 1 課第 5 節第 1 步](images/mrlearning-base-ch1-5-step1.JPG)

2. 在您的場景於 Unity 開啟時，藉由按一下 [加入開啟場景]  按鈕，來確定您剛剛建立的場景有在 [建置中的場景]  清單中。

3. 按下 [建置]  按鈕，開始建置程序。
    ![第 1 課第 5 節第 3 步](images/mrlearning-base-ch1-5-step3.JPG)

4. 為您的應用程式建立並命名新資料夾。 在下圖中，已建立名為 App 的資料夾來包含應用程式。 按一下 [選取資料夾]  ，即可開始對新建立的資料夾進行建置。 建置完成之後，您可以關閉 Unity 中的 [建置設定]  視窗。
    ![第 1 課第 5 節第 4 步](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > 如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。 如果您看到錯誤，例如「錯誤：CS0246 = 找不到名為 "XX" 的類型或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？)」。 若是如此，則您可能需要安裝 [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)

5. 在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。 按兩下 [MixedRealityBase.sln]  解決方案 (或是相對應名稱，如果您為專案使用替代名稱的話)，以在 Visual Studio 中開啟解決方案檔案。

    > [!NOTE]
    > 請務必開啟新建立的資料夾 (如果您遵循先前步驟中的命名慣例，此資料夾為 [App]  資料夾)，因為該資料夾外會有名稱類似的 .sln 檔案，不應與建置資料夾中的 .sln 檔案混淆。 資料夾結構看起來應該類似下圖。
    >
    > 如果 Visual Studio 要求您安裝新元件，請花一點時間確認是否已安裝所有必要元件，如同 [[安裝工具] 頁面](install-the-tools.md)中所指定

    ![第 1 課第 5 節第 5 步](images/mrlearning-base-ch1-5-step5.JPG)

6. 將 HoloLens 2 連線到您的電腦。 雖然這些指示假設您會部署到 HoloLens 2 裝置，但是您也可以選擇部署到 [HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[用於側載的應用程式套件](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

    > [!IMPORTANT]
    > 在建置您的裝置之前，裝置必須處於「開發人員模式」  ，並與您的開發電腦配對。 這兩個步驟都可以透過依照[這些指示](using-visual-studio.md)來完成

7. 若要設定 Visual Studio 來對 HoloLens 2 進行建置，請選取 [發行]  或 [主要]  組態、[ARM]  架構以及 [裝置]  作為目標。
    ![第 1 課第 5 節第 8 步](images/mrlearning-base-ch1-5-step7.JPG)

8. 最後一個步驟是藉由選取 [偵錯]   >  [啟動但不偵錯]  ，來對您的裝置進行建置和部署。 選取 [啟動但不偵錯]  會讓裝置上的應用程式在建置成功時立即啟動，但 Visual Studio 中不會有偵錯工具連接，也不會出現資訊。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。

    > [!NOTE]
    > 您也可以選取 [建置]   >  [部署解決方案]  ，在不自動啟動應用程式的情況下，對您的裝置進行部署。

    ![第 1 課第 5 節第 9 步](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>恭喜！

您現在已部署第一個 HoloLens 2 應用程式。 當您隨處走動時，您應該會看到空間對應網格涵蓋了所有 HoloLens 2 所感知到的介面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。 這些只是混合實境工具組的幾個現成基本項目。 在之後的課程中，您將開始在場景中加入更多內容和互動項目，讓您可以完整地探索 HoloLens 2 及混合實境工具組的功能。

> [!NOTE]
> 在應用程式中，您可能會注意到 Visual Profiler。 您也將在[第 5 課](mrlearning-base-ch5.md)中了解如何使用語音命令切換畫面播放速率計數器。 通常會建議您在開發期間保持 Visual Profiler 隨時可見，以了解程式碼變更可能會影響效能的時機。 HoloLens 2 應用程式應該[持續以 60 FPS 執行](understanding-performance-for-mixed-reality.md)。

[下一課：3.建立使用者介面並設定混合實境工具組](mrlearning-base-ch2.md)
