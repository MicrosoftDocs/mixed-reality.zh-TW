---
title: MR 學習 ASA 模組上 HoloLens 2 Azure 空間的錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326672"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>Getting Started with Azure HoloLens 2 上的空間錨點

歡迎來到 HoloLens 2 教學課程的第二個模組 ！ 開始之前，務必讓所有的[必要條件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)完成。 如果您尚未完成第一個[基底模組](mrlearning-base.md)，我們強烈建議您先完成該第一個。 如果您從新的 unity 專案，請依照下列中的新專案建立步驟[基底模組](mrlearning-base.md)。 

## <a name="objectives"></a>目標

* 了解使用 Azure 空間的錨點標記 HoloLens 2 開發基礎

* 建立、 上傳，並下載空間的錨點

  

## <a name="instructions"></a>指示

### <a name="downloading-and-importing-assets"></a>下載和匯入資產
在開始之前，您必須下載並匯入下列資產：

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[MR 基底模組資產套件](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[ASA 模組資產套件](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[混合實境工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> 注意： 請參閱步驟 5 中的特定指示匯入 Azure 空間的錨點，步驟 6 的特定指示需 MR 基底模組資產套件和步驟 3 到 4 的特殊指示混合實境工具組。

1. 在專案中建立新的場景。 以滑鼠右鍵按一下您的場景資料夾，按一下 [建立]，然後場景。 命名新的場景"ASALearningmodule。 」

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. 按兩下 「 ASALearningmodule"以查看一些預先定義的項目出現以及新的場景。 
3. 設定適用於混合的實境開發場景。 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 注意:您會看到快顯視窗，指出: 「 您必須選擇檔案的混合實境工具組 」。 按一下 [確定] 會帶您前往步驟 4。

4. 當選擇混合實境工具組的檔案，選取，"DefaultMixedRealityToolkitConfigurationProfile。 」

   > 注意:如果您有自己的組態設定檔自由，改為使用。

![module2chapter1step4im](images/module2chapter1step4im.PNG)

混合實境現在設定場景。 請確定您將場景 （使用其中一個控制項執行此作業 / 命令 + S 鍵，或按一下檔案，然後按一下 儲存）。 

5. 匯入[Azure 空間的錨點](https://github.com/azure/azure-spatial-anchors-samples/releases)。 若要使用空間的錨點，您必須匯入此資產。 因此，按一下上方的連結，並以滑鼠右鍵按一下 「 AzureSpatialAnchors.unitypackage。 」 按一下 另存目標為"，並將它儲存到您的電腦。 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   然後，儲存之後，移至 unity，按一下 「 資產 」 移至 [匯入封裝]，然後按一下 [自訂的套件...]會開啟您電腦的檔案。 一次在執行，尋找您儲存 Azure 空間的錨點的套件並加以選取。 然後按一下 [開啟]。

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   現在會快顯功能表提供的工具和設定，要求您要匯入的項目清單。 選取 ***所有***可用的選項，然後按一下 「 匯入。 」

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > 注意： 需要幾分鐘的時間匯入 」，因此請耐心等候。 

   6. 匯入[MR 基底模組資產套件](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)下一步。 如同步驟 5 中，按一下上方的連結，然後以滑鼠右鍵按一下 「 BasemoduleAssetsV1 1.unitypackage 」 並按一下 另存目標為"，並將它儲存到您的電腦。

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > 秘訣：儲存所有這些資產的相同資料夾中，使其更輕鬆地尋找及存取。 美觀且妥善管理，則會保留所有項目 ！

   步驟 5，請移至 unity，在按一下時，如同 「 資產 」，停留在 [匯入封裝]，然後按一下 [自訂的套件...]您電腦的檔案應該會再次出現，因此請移至您儲存此基本模組資產套件並加以選取。 然後按一下 [開啟]。

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > 注意： 可能會稍後在此模組所需的多個資產。 請遵循下列步驟來匯入從這裡開始所述的任何資產。 

7. 匯入 ASA 模組組件使用相同的方法為匯入前的套件。

### <a name="configuring-your-scene"></a>設定場景

在本節中，我們將新增 prefabs 和指令碼到場景方向，以建立一系列的示範基本概念的本機的錨點和 Azure 空間的錨點的行為方式的應用程式中的按鈕。

7. 在 專案 索引標籤底下的 「 資產 」 資料夾中，按一下 「 ASAmoduleAssets。 」 一次選取的是您會看到 2 prefabs"ButtonParent"和"ParentAnchor。 」

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. 將這兩個 prefabs 拖曳到場景。 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. 按兩下父錨點，以選取它。 您可能需要調整您的檢視，若要查看整個場景，因此視需要調整您的場景。

    熟悉 ParentAnchor prefab。 目前，名為"ParentAnchor 」 遊戲物件是彩色的 cube 中，供示範之用。 最後，我們將會隱藏的 cube，並將我們的內容放 ParentAnchor 的子系。 此 prefab 包含 AzureSpatialAnchorsDemoWrapper.cs 隨附的指令碼 （ASA SDK） 和 ParentAnchor 物件 ASAmoduleScript.cs 指令碼 （包含此模組的一部分）。 

10. 設定按鈕。 下 ParentAnchor prefab 中，您會發現許多加上標籤的按鈕。 這些按鈕會從 MRTK PressableButton prefabs 建立。 深入了解如何建立從 Pressable 按鈕[基底模組](mrlearning-base-ch2.md)。 針對每個按鈕，新增當使用者按下或選取下列清單根據按鈕就會觸發的事件。 

- 名為"StartAzureSession 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 StartAzureSession() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- 名為"StopAzureSession 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 StopAzureSession() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

- 名為"CreateAnchor 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 CreateAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

- 名為"開始尋找的錨點 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 FindAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

- 名為"DeleteAzureAnchor 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 DeleteAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

- 名為 「 刪除本機錨點 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 RemoveLocalAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

### <a name="build-and-demonstrate-base-application"></a>建置，並示範基底的應用程式

現在，場景設定來示範 Azure 空間的錨點的基本概念，我們會建置及示範 Azure 空間的錨點的基本行為。 

1. 如果您已關閉前面幾節中的 [建置設定] 視窗，請移至 [檔案] > [建置設定] 來重新開啟 [建置設定] 視窗。
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. 藉由按一下 [加入開啟場景] 按鈕，來確定您想要嘗試的場景有在 [建置中的場景] 清單中。

3. 按下 [建置] 按鈕，開始建置程序。
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. 為您的應用程式建立並命名新資料夾。 在下圖中，已建立名為 “App” 的資料夾來包含應用程式。 按一下 [選取資料夾]，即可開始對新建立的資料夾進行建置。 建置完成之後，您可以關閉 Unity 中的 [建置設定] 視窗。 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。 如果您看到錯誤，例如「錯誤：CS0246 = 找不到"XX"的輸入或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？) 」，則您可能需要安裝[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. 在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。 按兩下 “MixedRealityBase.sln” 解決方案 (或是相對應名稱，如果您為專案使用替代名稱的話)，以在 Visual Studio 中開啟解決方案檔案。

  > 注意:請務必開啟新建立的資料夾 (如果您遵循先前步驟中的命名慣例，此資料夾為 "App" 資料夾)，因為該資料夾外會有名稱類似的 .sln 檔案，不應與建置資料夾中的 .sln 檔案混淆。 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > 注意:如果 visual studio 會要求安裝新的元件，請花一些時間來確保所有必要的元件會安裝在為特定[[安裝工具] 頁面](install-the-tools.md) 

6. 使用 USB 纜線，將 HoloLens 2 插入您的電腦。 雖然這些課程指示假設您要部署測試與 HoloLens 2 裝置，您也可以選擇將部署到[HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[側載應用程式套件](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 對您的裝置進行建置之前，請確定裝置處於開發人員模式。 如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。 若要啟用開發人員模式，或與 Visual Studio 配對，請遵循[這些指示](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)。

8. 若要設定 Visual Studio 來對 HoloLens 2 進行建置，請選取 [發行] 組態和 [ARM] 架構。
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
    
9. 最後一個步驟是建置到您的裝置，選取 偵錯 > 啟動但不偵錯。 選取 [啟動但不偵錯] 會讓裝置上的應用程式在建置成功時立即啟動，但 Visual Studio 中不會出現偵錯資訊。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。 您也可以選取 [建置] > [部署解決方案]，在不自動啟動應用程式的情況下，對您的裝置進行部署。
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. 當您的裝置上執行應用程式時，請遵循螢幕上的指示。 請按下列步驟對應的場景按鈕。
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. 啟動 Azure 空間的錨點的工作階段。
    
    2. 移到不同位置的 cube。
    
    3. 儲存 Azure 空間的錨點，在 cube 的位置。
    
    4. 停止 Azure 空間的錨點的工作階段。
    
    5. 移除本機 cube，就可以讓使用者移動 cube 上的錨點。
    6. 移動其他地方的 cube。
    
    7. 啟動 Azure 空間的錨點的工作階段。
    
    8. 尋找 Azure 空間的錨點。
    （cube 應該返回到原始位置，現在您將它放在建立錨點時）。
    9. 刪除 Azure 空間的錨點。
    
    10. 停止 Azure 工作階段。

### <a name="anchoring-an-experience"></a>錨定的體驗

在先前章節中，您已了解 Azure 空間的錨點的基本概念。 我們使用 cube 來表示，並且將視覺化父代遊戲物件，具有附加的錨點。 在本節中，您 wiill 了解如何將其放 ParentAnchor 物件的子系的錨點整個的體驗。 此範例中，我們將使用農曆模組組件示範應用程式期間所建立[第 6 課的基本模組](mrlearning-base-ch6.md)。

1. 搜尋農曆模組組件完整 prefab，並將它拖曳到您的階層做為子系的 AnchorParent gameobject，如下圖所示。

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 定位的方式，仍會公開 cube，模組組件的體驗，如下圖所示。 在應用程式，使用者可能會重新定位整個體驗，藉由移動 cube。 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > 注意:有各種不同的重新定位體驗，包括使用按鈕來切換週框方塊括住的經驗，使用 （例如，在此步驟中所用的 cube)，重新調整物件的位置和旋轉的 gizmo 使用的使用者體驗流程等等。

## <a name="congratulations"></a>恭喜！
在這一課，您已了解 Azure 空間的錨點的基本概念。 本課程中提供了幾個按鈕，可讓您探索各種不同的步驟，才能啟動和停止 Azure 工作階段，並建立、 上傳及下載 azure 的錨點，單一裝置上。 在下一課中，我們將學習如何將 Azure 的錨點識別碼儲存至擷取，您 HoloLens 2，即使重新啟動應用程式。 在系列中，您將也了解如何達成空間的對齊方式、 多個裝置之間傳輸錨點識別碼和最終了解多使用者共用工作階段 （即將推出的共用模組一部分）。

[下一課：ASA Lesson 2](mrlearning-asa-ch2.md)

