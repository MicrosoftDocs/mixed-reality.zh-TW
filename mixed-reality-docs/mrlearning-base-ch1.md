---
title: 快速入門教學課程-2。 初始化您的專案和第一個應用程式
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 3bf218b42ea8abed45a80c0dd048e791cdd8372b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926891"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. 初始化您的專案和第一個應用程式

在第一課，您將瞭解[混合現實工具組（MRTK）]()所提供的一些功能、啟動 HoloLens 2 的第一個應用程式，然後將它部署到裝置。

## <a name="objectives"></a>目標

* 最佳化 Unity 以用於 HoloLens 開發。
* 匯入資產並設定場景。
* 空間對應網格、手寫網格和畫面播放速率計數器的視覺效果。

## <a name="instructions"></a>指示

### <a name="create-new-unity-project"></a>建立新的 Unity 專案

1. 啟動 Unity。
2. 選取 **\[New\] (新增)** 。
![Tut1-lesson1-step3 Section1 步驟 2](images/mrlearning-base-ch1-1-step2.JPG)

3. 輸入 [專案名稱] （例如 "MixedRealityBase"）。
![Tut1-lesson1-step3 Section1 步驟 3](images/mrlearning-base-ch1-1-step3.JPG)
4. 輸入要儲存專案的位置。
![Tut1-lesson1-step3 Section1 步驟 4](images/mrlearning-base-ch1-1-step4.JPG)
5. 確定專案已設定為 **3D**。
![Tut1-lesson1-step3 Section1 步驟 5](images/mrlearning-base-ch1-1-step5.JPG)
6. 按一下 [建立專案]。
![Tut1-lesson1-step3 Section1 步驟 6](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>設定適用於 Windows Mixed Reality 的 Unity 專案

1. 前往 [檔案] > [**組建設定** **]，以**開啟 [*組建設定*] 視窗。
![Tut1-lesson1-step3 Section2 步驟 1](images/mrlearning-base-ch1-2-step1.JPG)
2. 選取*通用 Windows 平臺*，然後按一下 [**切換平臺**] 按鈕以切換平臺。 在 HoloLens 2 上執行的應用程式必須通用 Windows 平臺（UWP）相容。
![Tut1-lesson1-step3 Section2 步驟 2](images/mrlearning-base-ch1-2-step2.JPG)
3. 按一下 [組建] 視窗中的 [**播放程式設定**] 按鈕，並在 [檢查] 面板的 [XR 設定] 下啟用 [*虛擬實境支援*] 核取方塊，即可啟用虛擬實境，如下圖所示。 請注意，您可能需要將 [*組建設定*] 視窗移出，才能看到 [偵測器] 面板。 [*支援的虛擬實境*] 核取方塊也適用于混合現實和增強式現實耳機，因為它是指啟用 stereoscopic 視覺（針對每個眼睛呈現不同的影像）。 ![Tut1-lesson1-step3 Section2 步驟 3](images/mrlearning-base-ch1-2-step3.JPG)
4. 此外，在 [XR 設定] 下，將 [*身歷聲轉譯模式]* 變更為 [*單一傳遞實例*]。 這種轉譯[管線的樣式](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)對於 HoloLens 2 而言通常是最高效能。 如果您對 Unity 環境的其他高效能設定感興趣，請遵循[這些指示](recommended-settings-for-unity.md)。
![Tut1-lesson1-step3 Section2 步驟 4](images/mrlearning-base-ch1-2-step4.jpg)
5. 從相同的 [偵測器] 面板中，確定已在 [*發佈設定*] 下啟用 [功能] 區段中的 [*空間感知*] 核取方塊。 空間感知可讓我們將混合現實裝置上的空間對應網格視覺化，例如 HoloLens 2。 在 [偵測器] 面板的 [XR 設定] 和 [其他設定] 底下，可以找到發佈設定。
![Tut1-lesson1-step3 Section2 步驟 5](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > 雖然不在本節中使用，但您可能會想要啟用的一些其他常見功能包括語音命令的*麥克風*，以及連接到需要網路連線之服務的*InternetClient* 。

### <a name="import-the-mixed-reality-toolkit"></a>匯入混合實境工具組

1. 下載[Mixed Reality 工具](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)組 Unity [foundation 封裝版本 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) ，並將它儲存到您電腦上的資料夾。

2. 匯入您在上一個步驟中下載的*Mixed Reality 工具*組套件。 首先按一下 **資產** > 匯**入** > **自訂套件**，然後選取*2.1.0 unitypackage*並加以開啟，以開始匯入程式。 請稍候幾分鐘，讓匯入處理完成。
    ![Tut1-lesson1-step3 Section3 Step2a](images/mrlearning-base-ch1-3-step2a.JPG) ![Tut1-lesson1-step3 Section3 Step2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. 在下一個快顯視窗中，按一下 [匯**入**] 開始將選取的封裝匯入 Unity 專案。 確認所有專案都已核取，如影像中所示。
    ![Tut1-lesson1-step3 Section3 步驟 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > 如果您看到快顯對話方塊，要求套用混合現實工具組預設設定，**請按一下 [** 套用]。 匯入以進行自動化安裝時，MRTK 會分析您的專案是否有任何遺漏的建議設定。 視您的設定而定，快顯可能看起來會不同，如下圖所示。

    ![Tut1-lesson1-step3 Section3 步驟 4 Note1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>設定混合實境工具組

1. 藉由選取 [混合] [**現實工具**組] > [**加入場景] 並設定**，將*混合現實工具*組新增至您目前的場景。 從功能表列。 如果您在匯入混合實境工具組之後沒有看到此功能表項目，請重新啟動 Unity。
    ![Tut1-lesson1-step3 Section4 步驟 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > 您可能會看到一個快顯對話方塊，可供您選取[混合現實工具組的設定檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。 按兩下名為*DefaultHoloLens2ConfigurationProfile*的設定檔。

2. 您的場景會有數個新專案和修改。 **按一下** 檔案 > 另存新檔 **...** ，將場景儲存在不同名稱下，並為您的場景提供名稱，例如*BaseScene*。 將您的場景儲存到專案 [*資產*] 資料夾中的 [*場景*] 資料夾，以保持其組織。
    ![Tut1-lesson1-step3 Section4 Step2a](images/mrlearning-base-ch1-4-step2a.JPG) ![Tut1-lesson1-step3 Section4 Step2b](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>對您的裝置建置應用程式

1. 如果您關閉了先前章節的 [*組建設定*] 視窗，請前往 [檔案 **] > [** **組建設定**] 再次開啟 [*組建設定*] 視窗。
    ![Tut1-lesson1-step3 Section5 步驟 1](images/mrlearning-base-ch1-5-step1.JPG)

2. 當您的場景在 Unity 中開啟時，請按一下 [**新增開啟的場景**] 按鈕，以確定您剛建立的場景位於組建清單的*場景*中。

3. 按下 [**組建**] 按鈕以開始建立程式。
    ![Tut1-lesson1-step3 Section5 步驟 3](images/mrlearning-base-ch1-5-step3.JPG)

4. 為您的應用程式建立並命名新資料夾。 在下圖中，已建立名為 App 的資料夾來包含應用程式。 按一下 [**選取資料夾**]，開始建立新建立的資料夾。 組建完成之後，您可以關閉 Unity 中的 [*組建設定*] 視窗。
    ![Tut1-lesson1-step3 Section5 步驟 4](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > 如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。 如果您看到錯誤，例如「錯誤： CS0246 = 類型或命名空間名稱 "XX" 找不到（您是否遺漏 using 指示詞或元件參考？）。 若是如此，您可能需要安裝[Windows 10 SDK （10.0.18362.0）](https://developer.microsoft.com//windows/downloads/windows-10-sdk)

5. 在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。 如果您使用專案的替代名稱，請按兩下 [ *MixedRealityBase* ] 方案或對應的名稱，以在 Visual Studio 中開啟方案檔。

    > [!NOTE]
    > 請務必開啟新建立的資料夾（也就是*應用程式*資料夾，如果遵循先前步驟中的命名慣例），因為該資料夾外部會有類似的名稱 .sln 檔案，不會與組建資料夾內的 .sln 檔案混淆。 資料夾結構看起來應該類似下圖。
    >
    > 如果 Visual Studio 要求您安裝新元件，請花一點時間確認是否已安裝所有必要元件，如同 [[安裝工具] 頁面](install-the-tools.md)中所指定

    ![Tut1-lesson1-step3 Section5 步驟5](images/mrlearning-base-ch1-5-step5.JPG)

6. 將 HoloLens 2 連接到您的電腦。 雖然這些指示會假設您要部署至 HoloLens 2 裝置，但您也可以選擇部署至[hololens 2 模擬器](using-the-hololens-emulator.md)，或選擇建立用於側[載的應用程式套件](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

    > [!IMPORTANT]
    > 在建立您的裝置之前，裝置必須處於*開發人員模式*，並與您的開發電腦配對。 您可以遵循[這些指示](using-visual-studio.md)來完成這兩個步驟

7. 選取 [*發行*] 或 [*主要*設定]、[ *ARM*架構] 和 [*裝置*] 做為 [目標]，以設定用於建立 HoloLens 2 的 Visual Studio。
    ![Tut1-lesson1-step3 Section5 Step8](images/mrlearning-base-ch1-5-step7.JPG)

8. 最後一個步驟是選取 [ **Debug** > **啟動但不進行調試**程式]，以建立並部署至您的裝置。 選取 [*啟動但不進行調試*程式]，會在組建成功時立即在您的裝置上啟動，但不會附加偵錯工具，而且資訊會出現在 Visual Studio 中。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。

    > [!NOTE]
    > 您也可以選取 [**組建** > **部署解決方案**]，以部署至您的裝置，而不會自動啟動應用程式。

    ![Tut1-lesson1-step3 Section5 Step9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>恭喜！

您現在已部署第一個 HoloLens 2 應用程式。 當您逐步解說時，您應該會看到一個空間對應網格，其中涵蓋 HoloLens 2 已察覺到的所有表面。 此外，您應該會看到手中的指標，以及用來追蹤應用程式效能的畫面播放速率計數器。 這些只是混合實境工具組的幾個現成基本項目。 在接下來的課程中，您將開始在場景中新增更多內容和互動性，讓您可以完整地探索 HoloLens 2 和混合現實工具組的功能。

> [!NOTE]
> 在應用程式中，您可能會注意到 visual profiler。 在[第5課](mrlearning-base-ch5.md)中，您將會討論如何使用語音命令來切換畫面播放速率計數器。 通常建議您在開發期間隨時保持可見的視覺化分析工具，以瞭解程式碼變更可能會影響效能的時機。 HoloLens 2 應用程式應[持續以 60 FPS 執行](understanding-performance-for-mixed-reality.md)。

[下一課： 3. 建立使用者介面和設定混合現實工具組](mrlearning-base-ch2.md)
