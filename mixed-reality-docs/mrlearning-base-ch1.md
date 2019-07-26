---
title: MR 學習基本模組 - 專案初始化和第一個應用程式
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: e79c3ea719a71d6df8ffd9e2be009d14a846a16a
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485726"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化您的專案和第一個應用程式

在第一課, 您將瞭解混合現實工具組 (MRTK) 所提供的一些功能、啟動 HoloLens 2 的第一個應用程式, 然後將它部署到裝置。

## <a name="objectives"></a>目標

* 最佳化 Unity 以用於 HoloLens 開發。
* 匯入資產並設定場景。
* 空間網格、手網格和畫面播放速率計數器的視覺效果。

## <a name="instructions"></a>指示

### <a name="create-new-unity-project"></a>建立新的 Unity 專案

1. 啟動 Unity。
2. 選取 [新增]。
![Lesson1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)
3. 輸入專案名稱 (例如："MixedRealityBase")。
![Lesson1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)
4. 輸入要儲存專案的位置。
![Lesson1 Chapter1 Step4](images/Lesson1Chapter1Step4.JPG)
5. 確定專案已設定為 **3D**。
![Lesson1 Chapter1 Step5](images/Lesson1Chapter1Step5.JPG)
6. 按一下 [建立專案]。
![Lesson1 Chapter1 Step6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>設定適用於 Windows Mixed Reality 的 Unity 專案

1. 前往 [檔案] > [組建設定], 以開啟 [組建設定] 視窗。
![Lesson1 Chapter4 Step1](images/Lesson1Chapter4Step1.JPG)
2. 選取 [通用 Windows 平臺] 來切換至通用 Windows 平臺。 按一下 [切換平臺] 按鈕以切換平臺。 在 HoloLens 2 上執行的應用程式必須通用 Windows 平臺 (UWP) 相容。
![Lesson1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)
3. 在 [組建] 視窗中按一下 [播放程式設定], 並從 [檢查] 面板的 [XR 設定] 下啟用 [支援虛擬實境] 核取方塊, 以啟用虛擬實境, 如下圖所示。 請注意, 您可能需要將 [組建設定] 視窗移出, 才能看到 [偵測器] 面板。 [支援的虛擬實境] 核取方塊也適用于混合現實和增強式現實耳機, 因為它是指啟用 stereoscopic 視覺 (針對每個眼睛呈現不同的影像)。![Lesson1 Chapter4 Step3](images/Lesson1Chapter4Step3.JPG)
4. 從相同的 [偵測器] 面板中, 確定已在 [發佈設定] 下啟用 [功能] 區段中的 [空間感知] 核取方塊。 空間感知可讓我們將混合現實裝置上的空間對應網格視覺化, 例如 HoloLens 2。 在 [偵測器] 面板的 [XR 設定] 和 [其他設定] 底下, 可以找到發佈設定。
![Lesson1 Chapter4 Step4](images/Lesson1Chapter4Step4.JPG)

> 注意：雖然不在本節中使用, 但您可能會想要啟用的一些其他常見功能包括語音命令的麥克風, 以及連接到需要網路連線之服務的 InternetClient。

### <a name="import-the-mixed-reality-toolkit"></a>匯入混合實境工具組

1. 下載[Mixed Reality 工具](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage)組 Unity 套件, 並將它儲存到您電腦上的資料夾。

2. 若要匯入混合實境工具組套件，請按一下 [資產] > [匯入] > [自訂套件]。 尋找在步驟 1 下載的混合實境工具組套件，並將其開啟，以開始匯入程序。 請稍候幾分鐘來完成匯入程序。
    ![Lesson1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. 在下一個快顯視窗中, 按一下 [匯入] 開始匯入混合現實工具組。 確認所有專案都已核取, 如影像中所示。 如果您看到快顯對話方塊, 要求套用混合現實工具組預設設定, 請按一下 [套用]。
    ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG) ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>設定混合實境工具組

1. 從功能表列選取 [> 設定] 中的 [混合現實工具組], 以設定 MRTK。 如果您在匯入混合實境工具組之後沒有看到此功能表項目，請重新啟動 Unity。
  ![Lesson1 Chapter3 Step1](images/Lesson1Chapter3Step1.JPG)

  > 注意:您可能會看到快顯對話方塊, 要求您選取混合現實工具組的設定檔。 若是如此, 請選取 [確定], 然後選擇名為 "DefaultMixedRealityToolkitConfigurationProfile" 的設定檔。

2. 您的場景將會有數個新專案, 並從 MRTK 進行修改。 按一下 檔案 > 另存新檔, 將場景儲存在不同名稱下, 並為您的場景提供名稱, 例如 BaseScene。 將您的場景儲存到專案 [資產] 資料夾中的 [場景] 資料夾, 以保持其組織。
  ![Lesson1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
  ![Lesson1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>對您的裝置建置應用程式

1. 如果您關閉了先前章節的 [組建設定] 視窗, 請前往 [檔案] > [組建設定] 再次開啟 [組建設定] 視窗。
    ![Lesson1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)

2. 按一下 [新增開啟的場景] 按鈕, 確定您想要嘗試的場景是在 [組建中的場景] 清單中。

3. 按下 [建置] 按鈕，開始建置程序。
    ![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)

4. 為您的應用程式建立並命名新資料夾。 在下圖中, 已建立名為 App 的資料夾來包含應用程式。 按一下 [選取資料夾], 開始建立新建立的資料夾。 組建完成之後, 您可以關閉 Unity 中的 [組建設定] 視窗。 
    ![Lesson1 Chapter5 Step4](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。 如果您看到錯誤, 例如「錯誤:CS0246 = 找不到類型或命名空間名稱 "XX" (您是否遺漏 using 指示詞或元件參考？)。 若是如此, 您可能需要安裝[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. 在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。 如果您使用專案的替代名稱, 請按兩下 [MixedRealityBase] 方案或對應的名稱, 以在 Visual Studio 中開啟方案檔。

  > 注意:請務必開啟新建立的資料夾 (也就是應用程式資料夾, 如果遵循先前步驟中的命名慣例), 因為在該資料夾之外會有類似名稱的 .sln 檔案, 不會與組建資料夾內的 .sln 檔案混淆。 

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

  > 注意:如果 Visual Studio 要求您安裝新元件，請花一點時間確認是否已安裝所有必要元件，如同 [[安裝工具] 頁面](install-the-tools.md)中所指定

6. 將 HoloLens 2 連接到您的電腦。 雖然這些指示會假設您將使用 HoloLens 2 裝置部署測試, 但您也可以選擇部署至[hololens 2 模擬器](using-the-hololens-emulator.md), 或選擇建立用於側[載的應用程式套件](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 對您的裝置進行建置之前，請確定裝置處於開發人員模式。 如果這是您第一次部署至 HoloLens 2, Visual Studio 可能會要求您將 HoloLens 2 與 PIN 配對。 若要啟用開發人員模式，或與 Visual Studio 配對，請遵循[這些指示](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)。

8. 藉由選取發行設定和 ARM 架構, 設定用來建立 HoloLens 2 的 Visual Studio。
    ![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 最後一個步驟是選取 [Debug] > [啟動但不進行偵錯工具] 來建立裝置。 選取 [啟動但不進行偵錯工具], 會在組建成功時立即在您的裝置上啟動, 但不會出現在 Visual Studio 中的偵測資訊。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。 您也可以選取 [組建 > 部署解決方案], 以部署至您的裝置, 而不會自動啟動應用程式。
    ![Lesson1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>恭喜！

您現在已部署第一個 HoloLens 2 應用程式。 當您逐步解說時, 您應該會看到一個空間網格, 其中涵蓋 HoloLens 2 已察覺的所有表面。 此外, 您應該會看到手中的指標, 以及用來追蹤應用程式效能的畫面播放速率計數器。 這些只是混合實境工具組的幾個現成基本項目。 在接下來的課程中, 您會開始在場景中新增更多內容和互動性, 讓您可以完整地探索 HoloLens 2 和混合現實工具組的功能。

>注意:您也將在[第 5 課](mrlearning-base-ch5.md)中了解如何使用語音命令切換畫面播放速率計數器

[下一課：3.建立使用者介面和設定混合現實工具組](mrlearning-base-ch2.md)
