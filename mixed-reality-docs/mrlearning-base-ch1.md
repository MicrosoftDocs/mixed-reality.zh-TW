---
title: MR 學習基本模組 - 專案初始化和第一個應用程式
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "65814015"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>MR 學習基本模組 - 專案初始化和第一個應用程式

在此第一課中，您將了解混合實境工具組提供的一些功能，然後啟動第一個適用於 HoloLens 2 的應用程式，並將其部署到裝置。

## <a name="objectives"></a>目標

* 最佳化 Unity 以用於 HoloLens 開發。
* 匯入資產並設定場景。
* 空間網格、手網格和畫面播放速率計數器的視覺效果。

## <a name="instructions"></a>指示

### <a name="create-new-unity-project"></a>建立新的 Unity 專案

1. 啟動 Unity。
2. 選取 [新增]  。
![Lesson1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)
3. 輸入專案名稱 (例如："MixedRealityBase")。
![Lesson1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)
4. 輸入要儲存專案的位置。
![Lesson1 Chapter1 Step4](images/Lesson1Chapter1Step4.JPG)
5. 確定專案已設定為 **3D**。
![Lesson1 Chapter1 Step5](images/Lesson1Chapter1Step5.JPG)
6. 按一下 [建立專案]  。
![Lesson1 Chapter1 Step6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>設定適用於 Windows Mixed Reality 的 Unity 專案

1. 請前往 [檔案] > [建置設定] 來開啟 [建置設定] 視窗。
![Lesson1 Chapter4 Step1](images/Lesson1Chapter4Step1.JPG)
2. 藉由選取 [通用 Windows 平台] 並按一下 [切換平台] 按鈕來切換到 [通用 Windows 平台]。 HoloLens 2 上執行的應用程式必須是通用 Windows 平台 (UWP)。
![Lesson1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)
3. 在 [建置] 視窗中按一下 [播放機設定] 來啟用虛擬實境，然後在偵測程式面板的 [XR 設定] 下啟用 [支援的虛擬實境] 核取方塊，如下圖所示。 請注意，您可能需要將 [建置設定] 視窗拖曳到其他位置，才能看到偵測程式面板。 「支援的虛擬實境」核取方塊也適用混合實境/AR 頭戴式裝置，因為其與立體視覺 (為每個眼睛轉譯不同影像) 的啟用有關連。![Lesson1 Chapter4 Step3](images/Lesson1Chapter4Step3.JPG)
4. 在相同的偵測程式面板中，確認 [發佈設定] 底下的功能區段中已啟用 [空間感知] 核取方塊。 空間感知可讓我們將混合實境裝置 (例如 HoloLens 2) 上的空間對應網格視覺化。 [發佈設定] 位在偵測程式面板中的 [XR 設定] 上方及 [其他設定] 下方。
![Lesson1 Chapter4 Step4](images/Lesson1Chapter4Step4.JPG)

> 注意：雖然未在本節中使用，但您可以啟用一些其他常見功能，包括麥克風 (適用於語音命令) 和 InternetClient (適用於連線到需要網路連線的服務)

### <a name="import-the-mixed-reality-toolkit"></a>匯入混合實境工具組

1. 下載[混合實境工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) 的 Unity 套件，並將其儲存在您電腦上的資料夾。

2. 若要匯入混合實境工具組套件，請按一下 [資產] > [匯入] > [自訂套件]。 尋找在步驟 1 下載的混合實境工具組套件，並將其開啟，以開始匯入程序。 請稍候幾分鐘來完成匯入程序。
    ![Lesson1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. 在下一個快顯視窗中，按一下 [匯入] 來開始匯入混合實境工具組。 請確定已核取所有項目，如圖所示。 如果您看到快顯對話方塊詢問是否套用混合實境工具組的預設設定，請按一下 [套用]。
    ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG) ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>設定混合實境工具組

1. 若要設定混合實境工具組，請從功能表列選取 [混合實境工具組] > [設定]。 如果您在匯入混合實境工具組之後沒有看到此功能表項目，請重新啟動 Unity。
![Lesson1 Chapter3 Step1](images/Lesson1Chapter3Step1.JPG)
2. 現在，場景會有數個來自混合實境工具組的新項目和修改項目。 若要以不同名稱來儲存場景，請按一下 [檔案] > [另存新檔]，然後為場景指定名稱，例如 BaseScene。 為了讓場景井然有序，您可以將場景儲存到專案「資產」資料夾中的「場景」資料夾。
![Lesson1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Lesson1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>對您的裝置建置應用程式

1. 如果您已關閉前面幾節中的 [建置設定] 視窗，請移至 [檔案] > [建置設定] 來重新開啟 [建置設定] 視窗。
    ![Lesson1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)

2. 藉由按一下 [加入開啟場景] 按鈕，來確定您想要嘗試的場景有在 [建置中的場景] 清單中。

3. 按下 [建置] 按鈕，開始建置程序。
    ![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)

4. 為您的應用程式建立並命名新資料夾。 在下圖中，已建立名為 “App” 的資料夾來包含應用程式。 按一下 [選取資料夾]，即可開始對新建立的資料夾進行建置。 建置完成之後，您可以關閉 Unity 中的 [建置設定] 視窗。 
    ![Lesson1 Chapter5 Step4](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。 如果您看到錯誤，例如「錯誤：CS0246 = 找不到名為 "XX" 的類型或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？)」，則您可能需要安裝 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. 在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。 按兩下 “MixedRealityBase.sln” 解決方案 (或是相對應名稱，如果您為專案使用替代名稱的話)，以在 Visual Studio 中開啟解決方案檔案。

  > 注意：請務必開啟新建立的資料夾 (如果您遵循先前步驟中的命名慣例，此資料夾為 "App" 資料夾)，因為該資料夾外會有名稱類似的 .sln 檔案，不應與建置資料夾中的 .sln 檔案混淆。 

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

  > 注意：如果 Visual Studio 要求您安裝新元件，請花一點時間確認是否已安裝所有必要元件，如同 [[安裝工具] 頁面](install-the-tools.md)中所指定

6. 使用 USB 纜線，將 HoloLens 2 插入您的電腦。 雖然這些課程指示假設您會以 HoloLens 2 裝置部署測試，但您也可以選擇部署到 [HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[用於側載的應用程式套件](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 對您的裝置進行建置之前，請確定裝置處於開發人員模式。 如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。 若要啟用開發人員模式，或與 Visual Studio 配對，請遵循[這些指示](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)。

8. 若要設定 Visual Studio 來對 HoloLens 2 進行建置，請選取 [發行] 組態和 [ARM] 架構。
    ![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 最後一個步驟是選取 [偵錯] > [啟動但不偵錯] 來對您的裝置進行建置。 選取 [啟動但不偵錯] 會讓裝置上的應用程式在建置成功時立即啟動，但 Visual Studio 中不會出現偵錯資訊。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。 您也可以選取 [建置] > [部署解決方案]，在不自動啟動應用程式的情況下，對您的裝置進行部署。
    ![Lesson1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>恭喜

您現在現在已部署第一個 HoloLens 2 應用程式。 當您隨處走動時，您應該會看到空間網格涵蓋了所有 HoloLens 2 所感知到的介面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。 這些只是混合實境工具組的幾個現成基本項目。 在之後的課程中，您將開始在場景中加入更多內容和互動項目，讓您可以完整地探索 HoloLens 2 及混合實境工具組的功能。

>注意：您也將在[第 5 課](mrlearning-base-ch5.md)中了解如何使用語音命令切換畫面播放速率計數器

[下一課：使用者介面、手部追蹤及混合實境工具組組態](mrlearning-base-ch2.md)
