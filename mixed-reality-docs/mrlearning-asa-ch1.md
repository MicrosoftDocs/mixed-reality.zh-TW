---
title: MR 學習 ASA 模組上 HoloLens 2 Azure 空間的錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: c120d22f955d366042bbcb9ac73eaa4f13dc20e9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415275"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>開始使用 Azure HoloLens 2 上的空間錨點

歡迎來到 HoloLens 2 教學課程的第二個模組。 開始之前，務必讓所有的[必要條件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)完成。 如果您尚未完成第一個[基底模組](mrlearning-base.md)，建議您先完成該模組。 如果您從新的 Unity 專案，請依照下列中的新專案建立步驟[基底模組](mrlearning-base.md)。 

## <a name="objectives"></a>目標

* 了解使用 Azure 空間的錨點標記 HoloLens 2 開發基礎

* 建立、 上傳，並下載空間的錨點

  

## <a name="instructions"></a>指示

### <a name="downloading-and-importing-assets"></a>下載和匯入資產
在開始之前，請下載並匯入下列資產：

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[MR 基底模組資產套件](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[ASA 模組資產套件](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[混合實境工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> 注意:如需有關如何匯入 Azure 空間的錨點，如需 MR 基底模組資產套件特定指示的步驟 6 和步驟 3 到 4 的特殊指示上混合實境工具組 (MRKT) 中的特定指示，請參閱步驟 5。

1. 在專案中建立新的場景。 以滑鼠右鍵按一下您的場景資料夾，按一下 [建立]，然後場景。 命名新的場景 ASALearningmodule。

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. 按兩下 ASALearningmodule 查看一些預先定義的項目，以及新的場景會出現。 
3. 設定適用於混合的實境開發場景。 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 注意:您會看到快顯視窗，指出: 「 您必須選擇檔案的混合實境工具組 」。 按一下 [確定] 將帶您前往步驟 4。

4. 當選擇 MRTK 檔案，選取，DefaultMixedRealityToolkitConfigurationProfile。

   > 注意:如果您有自己的組態設定檔，請放心，改為使用。

![module2chapter1step4im](images/module2chapter1step4im.PNG)

混合實境現在設定場景。 請確定您將場景 (使用其中一個控制項執行此作業 / 命令 + S 或按一下檔案，然後按一下 於儲存)。 

5. 匯入[Azure 空間的錨點](https://github.com/azure/azure-spatial-anchors-samples/releases)。 若要使用空間的錨點，您必須匯入此資產。 按一下上方的連結，然後 AzureSpatialAnchors.unitypackage 上按一下滑鼠右鍵。 按一下 另存目標為，並將它儲存到您的電腦。 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   儲存之後，請移回 Unity，按一下 資產，往下移到匯入封裝。 然後按一下 自訂封裝...會開啟您電腦的檔案。 當它們執行，尋找您儲存 Azure 空間的錨點的封裝，並加以選取。 然後按一下 [開啟]。

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   快顯視窗出現時，providingg 的工具和設定，以及詢問您要匯入的項目清單。 選取 ***所有***可用的選項，然後按一下 匯入。

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > 注意:請耐心等候，需要幾分鐘的時間匯入。 

   6. 匯入[MR 基底模組資產套件](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)下一步。 很多類似步驟 5 中，按一下上方的連結。 然後以滑鼠右鍵按一下 BasemoduleAssetsV1 1.unitypackag，按一下 另存目標，並將它儲存到您的電腦。

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > 秘訣：儲存所有這些資產的相同資料夾中，使其更輕鬆地尋找及存取。 它會保留所有項目好用且妥善管理。

   如同步驟 5 中，請回到 Unity、 按一下 資產，並停留在匯入封裝。 按一下 自訂封裝...您電腦的檔案將會再次出現。 請移至您儲存此基本模組資產套件。 然後選取它。 按一下 [開啟]。

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > 注意:可能有多個稍後在此模組所需的資產。 請遵循下列步驟來匯入從這裡開始所述的任何資產。 
                                                                                                                                                                                                                    
7. 匯入 ASA 模組通知使用相同的方法為匯入前的套件。

### <a name="configuring-your-scene"></a>設定場景

在本節中，我們會將 prefabs 和指令碼新增到場景方向，以建立一系列的示範基本概念的本機的錨點和 Azure 空間的錨點的行為方式的應用程式中的按鈕。

7. 在 [專案] 索引標籤的 [Assets] 資料夾底下按一下 ASAmoduleAssets。 選取之後，您會看到兩個 prefabs:ButtonParent 和 ParentAnchor。

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. 將這兩個 prefabs 拖曳到場景中。 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. 按兩下父錨點，以選取它。 您可能需要調整您的檢視，以查看整個場景。 視需要調整您的場景。

    熟悉 ParentAnchor prefab。 目前的遊戲物件名稱，ParentAnchor，是供示範之用的彩色的 cube。 最後，我們 '，將隱藏的 cube，並將我們的內容放 ParentAnchor 的子系。 此 prefab 包括 AzureSpatialAnchorsDemoWrapper.cs 隨附的指令碼 （ASA SDK），以及 ASAmoduleScript.cs 指令碼，包含這個模組 ParentAnchor 物件的一部分。 

10. 設定按鈕。 下 ParentAnchor prefab 中，請注意幾個按鈕，加上標籤。 這些按鈕會從 MRTK PressableButton prefabs 建立。 深入了解如何建立從 Pressable 按鈕[基底模組](mrlearning-base-ch2.md)。 針對每個按鈕，新增當使用者按下或選取下列清單根據按鈕就會觸發的事件。 

- 名為 StartAzureSession，按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 StartAzureSession() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- 按鈕名稱，StopAzureSession，建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 StopAzureSession() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

- 名為 CreateAnchor，按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 CreateAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

- 名為開始尋找的錨點，按鈕建立新的事件，在按鈕按下 」 事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 FindAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

- 名為 DeleteAzureAnchor，按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 DeleteAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

- 命名為，刪除本機錨點按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 RemoveLocalAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

### <a name="build-and-demonstrate-base-application"></a>建置，並示範基底應用程式

現在，場景設定來示範 Azure 空間的錨點的基本概念，我們會建置及示範 Azure 空間的錨點的基本行為。 

1. 如果您已關閉前面幾節中的 [建置設定] 視窗，請移至 [檔案] > [建置設定] 來重新開啟 [建置設定] 視窗。
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. 請確定您想要嘗試在的場景中組建清單中的場景是藉由按一下加入開啟的場景按鈕。

3. 按下 [建置] 按鈕，開始建置程序。
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. 為您的應用程式建立並命名新資料夾。 下圖中的應用程式命名的資料夾已建立包含應用程式。 按一下 選取的資料夾，以開始建置新建立的資料夾。 在 Unity 中建置完成之後，您也可以關閉 建立設定 」 視窗。 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。 如果您看到錯誤，例如「錯誤：CS0246 = 找不到"XX"的輸入或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？)。 您可能需要安裝[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. 在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。 按兩下 the"MixedRealityBase.sln 方案或對應的名稱。 如果您使用的替代名稱，為您的專案在 Visual Studio 中開啟方案檔。

  > 注意:請務必開啟新建立的資料夾 （亦即，應用程式資料夾，如果先前的步驟中遵循的命名慣例，因為會有該並不會混淆組建資料夾內的.sln 檔案的資料夾以外的名稱類似的.sln 檔案。 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > 注意:如果 Visual Studio 會要求安裝新的元件，請花一些時間來確保所有必要的元件會安裝在為特定[[安裝工具] 頁面](install-the-tools.md) 

6. 使用 USB 纜線，將 HoloLens 2 插入您的電腦。 雖然這些課程指示假設您要部署測試與 HoloLens 2 裝置，您也可以選擇將部署到[HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[側載應用程式套件](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 對您的裝置進行建置之前，請確定裝置處於開發人員模式。 如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。 請遵循[這些指示](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)若要啟用開發人員模式，或與 Visual Studio 配對。

8. 選取發行組態，而且"RM"架構，用於建置以 HoloLens 2 設定 Visual Studio。
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. 最後一個步驟是建置到您的裝置，選取 偵錯 > 啟動但不偵錯。 選取 啟動但不偵錯會立即開始在您的裝置時不會出現在 Visual Studio 成功組建 ithout 偵錯資訊的應用程式。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。 您也可以選取組建 > 部署的方案，而不需要自動啟動應用程式部署到您的裝置。
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10.遵循的指示。 當您的裝置上執行應用程式時，請遵循螢幕上的指示。 按 場景按鈕對應至下列步驟。
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. 啟動空間的錨點的工作階段。
    
    2. 移到不同位置的 cube。
    
    3. 儲存 Azure 空間的錨點，在 cube 的位置。
    
    4. 停止 Azure 空間的錨點的工作階段。
    
    5. 移除本機 cube，就可以讓使用者移動 cube 上的錨點。
    6. 移動其他地方的 cube。
    
    7. 啟動 Azure 空間的錨點的工作階段。
    
    8. 尋找 Azure 空間的 aachors。 
    
    您應該移回至原始位置您的電子將它放在建立錨點時）。
    9. 刪除 Azure 空間的錨點。
    
    10. 停止 Azure 工作階段。

### <a name="anchoring-an-experience"></a>錨定的體驗

在先前章節中，您已了解 Azure 空間的錨點的基本概念。 我們使用 cube 來表示，並且將視覺化父代遊戲物件，具有附加的錨點。 在本節中，您會學習如何將其放 ParentAnchor 物件的子系的錨點整個的體驗。 此範例中，我們使用農曆模組時所建立的組件示範應用程式[第 6 課的基本模組](mrlearning-base-ch6.md)。

1. 搜尋完成農曆模組組件的 prefab，並將它拖曳到您的階層做為子系的 AnchorParent gameobject 如下圖所示。

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 位置模組組件體驗，讓 cube 仍會暴露在下圖所示。 在應用程式，使用者可能會重新定位整個體驗，藉由移動 cube。 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > 注意:有各種不同的重新定位體驗，包括使用按鈕來切換週框方塊括住的經驗，使用 （例如，在此步驟中所用的 cube)，重新調整物件的位置和旋轉的 gizmo 使用的使用者體驗流程等等。

## <a name="congratulations"></a>恭喜！
在這一課，您已了解 Azure 空間的錨點的基本概念。 此 esson 提供您幾個按鈕，可讓您瀏覽啟動及停止 Azure 工作階段，以及建立、 上傳，以及下載 azure 的錨點，單一裝置上所需的各種步驟。 在下一課中，我們將學習如何將 Azure 的錨點識別碼儲存至擷取，您 HoloLens 2，即使重新啟動應用程式。 在系列中，您也將學習如何達成空間的對齊方式，並了解多使用者共用工作階段 （即將推出的共用模組一部分）。 多個裝置之間傳輸錨點識別碼

[下一課：ASA Lesson 2](mrlearning-asa-ch2.md)

