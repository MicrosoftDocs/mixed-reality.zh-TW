---
title: MR 學習基底模組-專案初始化 」 和 「 第一個應用程式
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65814015"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>MR 學習基底模組-專案初始化 」 和 「 第一個應用程式

在此第一課，您將學習一些混合實境 Toolkit 有提供，請啟動 HoloLens 2 中，第一個應用程式並將它部署到裝置的功能。

## <a name="objectives"></a>目標

* 最佳化 HoloLens 開發 Unity。
* 匯入資產，並設定場景。
* 空間網狀結構、 手網格和畫面播放速率計數器的視覺效果。

## <a name="instructions"></a>指示

### <a name="create-new-unity-project"></a>建立新的 Unity 專案

1. 啟動 Unity。
2. 選取 **\[New\] (新增)**。
![Lesson1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)
3. 輸入專案名稱 （例如：「 MixedRealityBase")。
![Lesson1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)
4. 輸入要儲存專案的位置。
![Lesson1 Chapter1 Step4](images/Lesson1Chapter1Step4.JPG)
5. 請確定專案已設定為**3D**。
![Lesson1 Chapter1 Step5](images/Lesson1Chapter1Step5.JPG)
6. 按一下 **建立專案**。
![Lesson1 Chapter1 Step6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>設定 Windows Mixed Reality Unity 專案

1. 開啟 組建設定 視窗，方法是前往 檔案 > 建置設定。
![第 1 課 Chapter4 步驟 1](images/Lesson1Chapter4Step1.JPG)
2. 選取 「 通用 Windows 平台 」 切換到 「 通用 Windows 平台 」，然後按一下 切換平台的 「 切換平台 」 按鈕。 HoloLens 2 上執行的應用程式必須是通用 Windows 平台 (UWP)。
![第 1 課 Chapter4 步驟 2](images/Lesson1Chapter4Step2.JPG)
3. 啟用虛擬實境，依序按一下 [建置] 視窗中的播放程式設定，然後在偵測器窗格中啟用 XR 設定下的，「 虛擬實境支援 」 核取方塊在下圖所示。 請注意，您可能需要以查看 [偵測器] 面板拖曳 [建置設定] 視窗的方式。 「 虛擬實境支援 」 的核取方塊也會套用至混合實境 / AR 耳機因為它參考到啟用 stereoscopic 願景 （轉譯不同映像的眼睛。）![第 1 課 Chapter4 步驟 3](images/Lesson1Chapter4Step3.JPG)
4. 在相同的偵測器窗格中，確認 [功能] 區段中的 「 空間感知 」 核取方塊已啟用，[發佈設定] 下。 空間感知可讓我們以視覺化方式檢視空間的對應網狀結構，例如 HoloLens 2 混合的實境裝置上。 在偵測器窗格中，上述 [XR 設定] 和 [其他設定。] 下找到的發行設定
![第 1 課 Chapter4 步驟 4](images/Lesson1Chapter4Step4.JPG)

> 注意：雖然未使用本節中，您可能想要啟用一些其他常見功能包括麥克風 （適用於語音命令） 和 InternetClient （適用於連接至需要網路連線的服務）

### <a name="import-the-mixed-reality-toolkit"></a>匯入的混合的實境工具組

1. 下載[混合實境 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) unity 套件，並將它儲存在您的電腦上的資料夾。

2. 資產上的 匯入混合實境工具組封裝 > 匯入 > 自訂封裝。 尋找在步驟 1 中下載的混合實境工具組封裝，並開啟它，以開始匯入程序。 請稍候幾分鐘的時間匯入程序。
    ![第 1 課 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![第 1 課 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. 在下一步] 快顯視窗中，按一下 [開始匯入混合實境工具組的 「 匯入 」。 請確定選取所有項目，如圖所示。 如果您看到快顯的對話方塊，詢問要套用混合實境工具組的預設設定，按一下 [套用]。
    ![第 1 課 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG) ![第 1 課 Chapter2 步驟 3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>設定混合的實境 Toolkit

1. 藉由選取功能表列混合實境工具組中設定混合的工具組 > 設定。 如果您沒有看到此功能表項目匯入的混合的實境工具組之後，請重新啟動 Unity。
![第 1 課 Chapter3 步驟 1](images/Lesson1Chapter3Step1.JPG)
2. 場景現在會有數個新項目和修改在其混合實境 toolkit。 儲存在不同的名稱下場景檔案上按一下 > 將儲存為和指定名稱，例如 BaseScene 的場景。 讓您依將它儲存到專案的 Assets 資料夾中的 「 場景 」 資料夾的場景。
![第 1 課 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![第 1 課 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>建置您的應用程式到您的裝置

1. 如果您關閉上一節中的 建置設定 視窗，開啟 組建設定 視窗一次移至 檔案 > 建置設定。
    ![第 1 課 Chapter5 步驟 1](images/Lesson1Chapter5Step1.JPG)

2. 請確定您想要嘗試在的場景位於藉由按一下 「 加入開啟花絮 」 按鈕 」 組建中的場景 」 清單。

3. 按下 [建立] 按鈕，開始建置程序。
    ![第 1 課 Chapter5 步驟 3](images/Lesson1Chapter5Step3.JPG)

4. 建立並命名您的應用程式的新資料夾。 在下圖中，同名的資料夾已建立 「 應用程式 」，以包含應用程式。 按一下 [選取資料夾]，開始建置新建立的資料夾。 建置完成之後，您可以關閉 [建立設定] 視窗中，在 Unity 中。 
    ![第 1 課 Chapter5 步驟 4](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果建置失敗，再試一次建置或重新啟動 Unity 並再次建置。 如果您看到錯誤，例如 「 錯誤：CS0246 = 找不到"XX"的類型或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？) 」，則您可能需要安裝[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. 在建置完成之後，開啟新建立的資料夾包含您新建置的應用程式的檔案。 按兩下 「 MixedRealityBase.sln 」 解決方案 （或對應的名稱，如果您使用您的專案的替代名稱） 以在 Visual Studio 中開啟方案檔。

  > 注意：請務必開啟新建立的資料夾 （亦即，「 應用程式 」 資料夾，如果先前的步驟中遵循的命名慣例），因為會有該並不會混淆組建資料夾內的.sln 檔案的資料夾以外的名稱類似的.sln 檔案。 

![第 1 課 Chapter5 步驟 5](images/Lesson1Chapter5Step5.JPG)

  > 注意：如果 Visual Studio 會要求您安裝新的元件，請花一點時間確認做為安裝的所有必要的元件中的指定[[安裝工具] 頁面](install-the-tools.md)

6. HoloLens 2 插入您的電腦，使用 USB 纜線。 雖然這些課程指示假設您要部署測試與 HoloLens 2 裝置，您也可以選擇將部署到[HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[側載應用程式套件](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 之前建置到您的裝置，請確定裝置處於開發人員模式。 如果這是您第一次，將部署到 HoloLens 2 時，Visual Studio 可能會要求您配對您的 HoloLens 2 使用 pin。 請遵循[這些指示](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)若要啟用開發人員模式，或與 Visual Studio 配對。

8. 設定用於建置以 HoloLens 2 的 Visual Studio，選取 [發行] 組態和"ARM"架構。
    ![第 1 課 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 最後一個步驟是建置到您的裝置，選取 偵錯 > 啟動但不偵錯。 選取 [啟動但不偵錯]，會導致您在建置成功，但如果沒有出現在 Visual Studio 中的偵錯資訊的裝置上立即啟動應用程式。 這也表示，HoloLens 2 上執行您的應用程式而不需停止應用程式時，您即可拔掉 USB 纜線。 您也可以選取組建 > 部署的方案，而不需要自動啟動應用程式部署到您的裝置。
    ![第 1 課 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>恭喜您

您現在現在已部署您第一次的 HoloLens 2 應用程式。 逐步周圍，您應該會看到空間網狀結構涵蓋有已發現的 HoloLens 2 的所有介面。 此外，您應該看到指標雙手及用於追蹤的手裡，並留意應用程式效能的畫面格速率計數器。 這些是幾個基本項目，包含現成的混合實境工具組。 在未來課程中，您將啟動更多的內容和互動功能加入至場景，，因此您可以完整地探索 HoloLens 2 及混合實境 toolkit 的推出的功能。

>注意：您也將討論如何切換使用中的語音命令的畫面格速率計數器[第 5 課](mrlearning-base-ch5.md)

[下一課：使用者介面，手動追蹤及混合實境工具組組態](mrlearning-base-ch2.md)
