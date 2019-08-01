---
title: Azure 空間錨點教學課程-1。 開始使用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 110c8ae1a529d4a3b4796a5d2b6ee44c150741cb
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702065"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1.開始使用 Azure 空間錨點

歡迎使用 HoloLens 2 教學課程的第二個模組。 開始使用之前, 請確定所有[必要條件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)都已完成。 如果您尚未完成第一個[基本模組](mrlearning-base.md), 建議您先完成該課程模組。 如果您從新的 Unity 專案開始, 請遵循[基底模組](mrlearning-base.md)中的新專案建立步驟。 

## <a name="objectives"></a>目標

* 瞭解使用 HoloLens 2 搭配 Azure 空間錨點進行開發的基本概念

* 建立、上傳及下載空間錨點

## <a name="instructions"></a>指示

### <a name="downloading-and-importing-assets"></a>下載和匯入資產
開始之前, 請先下載並匯入下列資產:

[Azure 空間錨點 v 1.1。0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[MR 基底模組資產套件1.2 版](https://github.com/microsoft/MixedRealityLearning/releases/download/1.2/BaseModuleAssets-1.2.unitypackage)

[ASA 模組資產套件 v1。0](https://github.com/microsoft/MixedRealityLearning/releases/download/ASA_1.1/ASAModuleAssetsBeta.unitypackage)

[混合現實工具組 2.0.0 RC1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)

> 注意:如需有關如何匯入 Azure 空間錨點的特定指示, 請參閱步驟 5: 在 MR 基底模組資產套件上進行特定指示的步驟 6, 以及步驟3到 4, 以瞭解混合現實工具組 (MRKT) 上的特定指示。

1. 在您的專案中建立新的場景。 以滑鼠右鍵按一下場景資料夾, 然後依序按一下 [建立]、[場景]。 將新場景命名為 ASALearningmodule。

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. 按兩下 [ASALearningmodule], 以查看一些預先定義的專案會與新場景一併顯示。 
3. 設定混合現實開發的場景。 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 注意:您會看到一個快顯視窗, 指出您必須為混合現實工具組選擇一個檔案。 按一下 [確定] 會帶您前往步驟4。

4. 為 MRTK 選擇檔案時, 請選取 [DefaultMixedRealityToolkitConfigurationProfile]。

> 注意:如果您有自己的設定設定檔, 則可以隨意使用。

![module2chapter1step4im](images/module2chapter1step4im.PNG)

現在場景已設定為混合現實。 請確定您儲存場景 (以 control/command + S 執行此動作, 或按一下 [檔案], 然後按一下 [儲存])。 

5. 匯入[Azure 空間錨點](https://github.com/azure/azure-spatial-anchors-samples/releases)。 若要使用空間錨點, 您必須匯入此資產。 按一下上方的連結, 並以滑鼠右鍵按一下 [AzureSpatialAnchors unitypackage]。 按一下 [另存目標], 並將它儲存到您的電腦。 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

儲存之後, 請回到 Unity, 按一下 [資產], 再按 [匯入套件]。 然後按一下 [自訂套件 ...]您的電腦檔案將會開啟。 當他們這麼做時, 請尋找您儲存 Azure 空間錨點套件的位置, 並加以選取。 然後按一下 [開啟]。

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

快顯視窗隨即出現, providingg 工具和設定的清單, 並詢問您要匯入的內容。 選取***所有***可用的選項, 然後按一下 [匯入]。

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> 注意:請耐心等候, 需要幾分鐘的時間才能匯入。 

6. 匯入 [MR 基底模組資產 https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) 套件] 下一步。 如步驟5所示, 按一下上方的連結。 然後以滑鼠右鍵按一下 [BasemoduleAssetsV1 unitypackag], 再按一下 [另存目標], 然後將它儲存到您的電腦。

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> 秘訣：將所有這些資產都儲存在相同的資料夾中, 以便更容易尋找並擁有存取權。 它可讓所有專案保持良好和組織。

就像步驟5一樣, 請回到 Unity, 按一下 [資產], 然後將滑鼠停留在 [匯入套件] 上方。 按一下 [自訂套件 ...]您的電腦檔案將會再次出現。 移至您儲存基本模組資產套件的位置。 然後選取它。 按一下 [開啟]。

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> 注意:本課程模組稍後可能需要更多資產。 請遵循下列步驟來匯入此處所提及的任何資產。 

7. 使用與匯入先前封裝相同的方法匯入[ASA 模組套件](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1)。

### <a name="configuring-your-scene"></a>設定場景

在本節中, 我們將在場景中新增 prefabs 和腳本, 以建立一系列的按鈕, 以示範本機錨點和 Azure 空間錨點在應用程式中的行為。

8. 在 [專案] 索引標籤的 [資產] 資料夾底下, 按一下 [ASAmoduleAssets]。 選取之後, 您將會看到兩個 prefabs:ButtonParent 和 ParentAnchor。

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. 將這兩個 prefabs 拖曳到場景中。 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

10. 按兩下父錨點加以選取。 您可能需要調整您的視圖, 才能看到整個場景。 視需要調整您的場景。

熟悉 ParentAnchor prefab。 目前, 名為 ParentAnchor 的遊戲物件是彩色 cube, 供示範之用。 最後, 我們會隱藏 cube, 並將內容放在 ParentAnchor 的子系中。 此 prefab 包含 AzureSpatialAnchorsDemoWrapper.cs 腳本 (隨附于 ASA SDK) 和 ASAmoduleScript.cs 腳本 (隨附于此模組中) 至 ParentAnchor 物件。 

11. 設定按鈕。 在 [ButtonParent] prefab 下, 留意幾個加上標籤的按鈕。 這些按鈕是從 MRTK 的 PressableButton prefabs 所建立。 深入瞭解如何從[基底模組](mrlearning-base-ch2.md)建立 Pressable 按鈕。 針對每個按鈕, 新增在使用者按下或選取按鈕時所觸發的事件 (根據下列清單)。 

- 針對名為 StartAzureSession 的按鈕, 在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 StartAzureSession () 方法。

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- 針對按鈕名稱 StopAzureSession, 請在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 StopAzureSession () 方法。

- 針對名為 CreateAnchor 的按鈕, 在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 CreateAzureAnchor () 方法。

- 針對名為的按鈕, 開始尋找 [錨點], 在 [事件觸發程式] 和 [開啟] 事件觸發程式底下建立新事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 FindAzureAnchor () 方法。

- 針對名為 DeleteAzureAnchor 的按鈕, 在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 DeleteAzureAnchor () 方法。

- 針對名為的按鈕, 刪除本機錨點, 在按下按鈕的事件觸發程式和 On Click 事件觸發程式底下建立新事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 RemoveLocalAnchor () 方法。

### <a name="build-and-demonstrate-base-application"></a>建立並示範基本應用程式

既然您的場景已設定為示範 Azure 空間錨點的基本概念, 我們將會建立並示範 Azure 空間錨點的基本行為。 

1. 如果您已關閉前面幾節中的 [建置設定] 視窗，請移至 [檔案] > [建置設定] 來重新開啟 [建置設定] 視窗。
![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. 按一下 [新增開啟的場景] 按鈕, 確定您想要嘗試的場景是在 [組建中的場景] 清單中。

3. 按下 [建置] 按鈕，開始建置程序。
![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. 為您的應用程式建立並命名新資料夾。 在下圖中, 已建立名為 App 的資料夾來包含應用程式。 按一下 [選取資料夾], 開始建立新建立的資料夾。 組建完成之後, 您可以在 Unity 中關閉 [組建設定] 視窗。 
![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。 如果您看到錯誤，例如「錯誤：CS0246 = 找不到輸入或命名空間名稱 "XX" (您是否遺漏 using 指示詞或元件參考？)。 您可能需要安裝[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. 在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。 按兩下 [MixedRealityBase] 方案或對應的名稱。 如果您使用專案的替代名稱, 在 Visual Studio 中開啟方案檔。

  > 注意:如果遵循先前步驟中的命名慣例, 請務必開啟新建立的資料夾 (也就是應用程式資料夾), 因為該資料夾外部會有類似的名稱 .sln 檔案, 不會與組建資料夾內的 .sln 檔案混淆。 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> 注意:如果 Visual Studio 要求安裝新元件, 請花點時間確定所有必要條件元件都已安裝為[[安裝工具] 頁面](install-the-tools.md)中的特定 

6. 使用 USB 纜線，將 HoloLens 2 插入您的電腦。 雖然這些課程指示假設您將使用 HoloLens 2 裝置部署測試, 但您也可以選擇部署至[hololens 2 模擬器](using-the-hololens-emulator.md), 或選擇建立用於側[載的應用程式套件](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 對您的裝置進行建置之前，請確定裝置處於開發人員模式。 如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。 如果您需要啟用開發人員模式或與 Visual Studio 配對, 請遵循[這些指示](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)。

8. 藉由選取發行設定和 RM 架構, 設定用來建立 HoloLens 2 的 Visual Studio。
![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. 最後一個步驟是選取 [Debug] > [啟動但不進行偵錯工具] 來建立裝置。 選取 [啟動但不進行偵錯工具], 會在 Visual Studio 中出現成功的組建 ithout 偵測資訊時, 立即在您的裝置上啟動。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。 您也可以選取 [組建 > 部署解決方案], 以部署至您的裝置, 而不會自動啟動應用程式。
![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
   
10. 請依照指示進行。 當應用程式在您的裝置上執行時, 請遵循畫面上的指示。 按下與下列步驟對應的場景按鈕。

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. 啟動空間錨點會話。
    
    2. 將 cube 移至不同的位置。
    
    3. 將 Azure 空間錨點儲存在 cube 的位置。
    
    4. 停止 Azure 空間錨點會話。
    
    5. 移除 cube 上的本機錨點, 讓使用者可以移動 cube。
    
    6. 將 cube 移到其他地方。
    
    7. 啟動 Azure 空間錨點會話。
    
    8. 尋找 Azure 空間錨點。 
    當您建立錨點時, 應該回到原先放置的位置。
    
    9. 刪除 Azure 空間錨點。
    
    10. 停止 Azure 會話。

### <a name="anchoring-an-experience"></a>錨定體驗

在前面幾節中, 您已瞭解 Azure 空間錨點的基本概念。 我們已使用 cube 來呈現父遊戲物件, 並將其視覺化為連結的錨點。 在本節中, 您將瞭解如何藉由將它放在 ParentAnchor 物件的子系, 來錨定整個體驗。 在此範例中, 我們會使用在[基底模組第6課](mrlearning-base-ch6.md)期間所建立的陰曆模組元件示範應用程式。

1. 搜尋 [農曆模組元件完成] prefab, 並將它拖曳至您的階層中, 做為 AnchorParent gameobject 的子系, 如下圖所示。

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 定位模組元件體驗, 讓 cube 仍然公開, 如下圖所示。 在應用程式中, 使用者可以藉由移動 cube 來重新放置整個體驗。 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> 注意:有各種不同的使用者體驗流程可用於重新置放體驗, 包括使用按鈕來切換環繞體驗的周框方塊、使用重新置放的物件 (例如在此步驟中使用的 cube)、使用位置和旋轉 gizmos等等。

## <a name="congratulations"></a>恭喜！
在本教學課程中, 您已瞭解 Azure 空間錨點的基本概念。 此 esson 為您提供數個按鈕, 可讓您探索啟動和停止 Azure 會話所需的各種步驟, 以及在單一裝置上建立、上傳和下載 azure 錨點。 在下一課中, 我們將瞭解如何將 Azure 錨點識別碼儲存至 HoloLens 2 進行抓取, 即使在應用程式重新開機之後也一樣。 在此系列中, 您也將瞭解如何在多個裝置之間傳輸錨點識別碼, 以達成空間對齊, 並瞭解多使用者共用會話, 即將推出做為共用教學課程的一部分。

[下一課：2.儲存、擷取和共用 Azure Spatial Anchors](mrlearning-asa-ch2.md)

