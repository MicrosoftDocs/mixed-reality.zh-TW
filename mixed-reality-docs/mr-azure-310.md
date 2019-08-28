---
title: MR 和 Azure 310-物件偵測
description: 完成此課程以瞭解如何將機器學習模型定型, 然後使用定型的模型, 從混合現實應用程式中辨識出類似物件及其在現實世界中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 自訂視覺, 物件偵測, 混合現實, 學術, unity, 教學課程, api, hololens
ms.openlocfilehash: 71370db84a9b90b017e8d5fac0799a862883d046
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047220"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。  因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊, 以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時, 使用這些教學課程的連結進行更新。

# <a name="mr-and-azure-310-object-detection"></a>Mr 和 Azure 310:物件偵測

在此課程中, 您將瞭解如何使用混合現實應用程式中的 Azure 自訂視覺「物件偵測」功能, 辨識所提供影像中的自訂視覺內容及其空間位置。

此服務可讓您使用物件影像來定型機器學習模型。 接著, 您將使用定型的模型來辨識類似物件, 並在現實世界中取得其位置, 如 Microsoft HoloLens 的相機捕捉或相機連線到電腦的沉浸式 (VR) 耳機所提供。

![課程結果](images/AzureLabs-Lab310-00.png)

**Azure 自訂視覺, 物件偵測**是一種 Microsoft 服務, 可讓開發人員建立自訂影像分類器。 這些分類器可以再搭配新的映像來偵測該新的映像 」 中的物件，藉由提供 **方塊界限** 的映像本身。 此服務提供簡單、便於使用的線上入口網站, 以簡化此程式。 如需詳細資訊, 請造訪下列連結:

* [Azure 自訂視覺頁面](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [限制和配額](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

完成本課程之後, 您將會有一個混合現實應用程式, 可以執行下列作業:

1. 使用者將能夠使用 Azure 自訂視覺服務、物件偵測來進行訓練的物件。 
2. 使用者將使用點按手勢來捕獲其所查看內容的影像。
3. 應用程式會將映射傳送至 Azure 自訂視覺服務。
4. 將會有服務的回復, 其會將辨識結果顯示為世界空間的文字。 這會透過使用 Microsoft HoloLens 的空間追蹤來完成, 以瞭解辨識物件的世界位置, 然後使用與影像中偵測到的內容相關聯的標籤來提供標籤文字。

本課程也會說明如何手動上傳影像、建立標記和訓練服務, 藉由在您提交的影像內設定*界限*方塊來辨識不同的物件 (在提供的範例中為杯)。 

> [!IMPORTANT]
> 建立和使用應用程式之後, 開發人員應該流覽回到 Azure 自訂視覺服務, 並找出服務所做的預測, 並判斷其是否正確 (透過標記服務遺漏的任何專案, 以及調整周*框方塊*)。 服務接著可以重新定型, 這樣會增加識別真實世界物件的可能性。

本課程將告訴您如何從 Azure 自訂視覺服務 (物件偵測) 取得結果, 使其成為以 Unity 為基礎的範例應用程式。 您必須將這些概念套用到您可能正在建立的自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 310:物件偵測</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。 也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (2018 年7月)。 您可以免費使用 [[安裝工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)] 文章中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。

在此課程中, 我們建議您採用下列硬體和軟體:

- 開發電腦
- [已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [最新的 Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- 已啟用開發人員模式的[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)
- Azure 設定和自訂視覺服務的網際網路存取
-  您想要自訂視覺辨識的每個物件都需要一系列至少 15 (15) 個影像)。 如有需要, 您可以使用本課程中已提供的影像,[一系列的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

## <a name="before-you-start"></a>開始之前

1.  為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。
2.  設定並測試您的 HoloLens。 如果您需要支援設定 HoloLens,[請務必造訪 hololens 安裝程式一文](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  開始開發新的 HoloLens 應用程式時, 最好先執行校正和感應器微調 (有時候它有助於為每個使用者執行這些工作)。 

如需校正的說明, 請遵循此[HoloLens 校正文章的連結](calibration.md#hololens-2)。

如需感應器微調的說明, 請遵循此[HoloLens 感應器微調文章連結](sensor-tuning.md)。

## <a name="chapter-1---the-custom-vision-portal"></a>第1章-自訂視覺入口網站

若要使用**Azure 自訂視覺服務**, 您必須將其實例設定為可供您的應用程式使用。

1.  流覽[至 [**自訂視覺服務**] 主頁面](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  按一下 [**消費者入門**]。

    ![](images/AzureLabs-Lab310-01.png)

3.  登入自訂視覺入口網站。

    ![](images/AzureLabs-Lab310-02.png)

4.  如果您還沒有 Azure 帳戶, 您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。

5.  當您第一次登入之後, 系統會提示您使用 [*服務條款*] 面板。 按一下核取方塊以*同意條款*。 然後按一下 [**我同意**]。

    ![](images/AzureLabs-Lab310-03.png)

6.  當您同意這些條款時, 您現在會在 [*我的專案*] 區段中。 按一下 [**新增專案**]。

    ![](images/AzureLabs-Lab310-04.png)

7.  右側會出現一個索引標籤, 它會提示您指定專案的某些欄位。

    1.  插入專案的名稱

    2.  插入專案的描述 (**選擇性**)

    3.  選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務 (例如這些課程) 都保留在通用資源群組下)。

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > 如果您想要[深入瞭解 Azure 資源群組, 請流覽至相關聯的](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)檔

    4.  將**專案類型**設定為 [**物件偵測 (預覽)** ]。

8.  完成後, 按一下 [**建立專案**], 系統會將您重新導向至 [自訂視覺服務專案] 頁面。


## <a name="chapter-2---training-your-custom-vision-project"></a>第2章-訓練您的自訂視覺專案

在自訂視覺入口網站中, 您的主要目標是要將您的專案定型, 以辨識影像中的特定物件。

針對您希望應用程式辨識的每個物件, 您至少需要15個 (15) 個影像。 您可以使用本課程所提供的影像 ([一系列的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

若要將您的自訂視覺專案定型:

1.  按一下 [ **+** **標記**] 旁的按鈕。

    ![](images/AzureLabs-Lab310-06.png)

2.  新增將用來建立影像關聯的標記**名稱**。 在此範例中, 我們會使用 cup 的影像來進行辨識, 因此, 請將標記命名為「**杯**」。 完成後, 按一下 [**儲存**]。

    ![](images/AzureLabs-Lab310-07.png)

3.  您會注意到您已新增標籤 (您可能需要重載頁面, 才會出現此**標記**)。 

    ![](images/AzureLabs-Lab310-08.png)

4.  按一下頁面中央的 [**新增影像**]。

    ![](images/AzureLabs-Lab310-09.png)

5.  按一下 **[流覽本機檔案]** , 然後流覽至您想要上傳給一個物件的影像, 其最小值為 15 (15)。

    > [!TIP]
    >  您可以一次選取數個影像, 以進行上傳。

    ![](images/AzureLabs-Lab310-10.png)

6.  選取您想要用來定型專案的所有影像之後, 請按 **[上傳**檔案]。 檔案將會開始上傳。 確認上傳之後, 請按一下 [**完成**]。

    ![](images/AzureLabs-Lab310-11.png)

7.  此時, 您的影像已上傳, 但未加上標籤。

    ![](images/AzureLabs-Lab310-12.png)

8.  若要標記影像, 請使用您的滑鼠。 當您將滑鼠停留在影像上時, 選取專案反白顯示會自動在物件周圍繪製選取專案。 如果不正確, 您可以自行繪製。 這是藉由按住滑鼠左鍵, 並將選取區域拖曳至包含物件的方式來完成。 

    ![](images/AzureLabs-Lab310-13.png) 

9. 在影像中選取您的物件之後, 就會出現一個小提示, 詢問您是否要*新增區域標記*。 選取您先前建立的標籤 (在上述範例中為「杯」), 或者, 如果您要新增更多標籤, 請在中輸入該標記, 然後按一下 [ **+] (加號)** 按鈕。

    ![](images/AzureLabs-Lab310-14.png) 

10. 若要標記下一個影像, 您可以按一下分頁右邊的箭號, 或關閉 [標記] 分頁 (按一下分頁右上角的**X** ), 然後按下一個影像。 當您準備好下一個映射之後, 請重複相同的程式。 針對您上傳的所有影像執行此動作, 直到全部標記完畢為止。 

    > [!NOTE]
    >  您可以選取相同影像中的數個物件, 如下圖所示: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. 標記全部之後, 請按一下畫面左側的已**標記**按鈕, 以顯示已標記的影像。 

    ![](images/AzureLabs-Lab310-16.png)

12. 您現在已準備好訓練您的服務。 按一下 [**定型**] 按鈕, 就會開始進行第一個定型反復專案。

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. 建立之後, 您就可以看到兩個名為 [設為**預設**] 和 [**預測 URL**] 的按鈕。 按一下 [**設為預設值**], 然後按一下 [**預測 URL**]。

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > 從這個提供的端點會設定為任何已標示為預設的*反復*專案。 因此, 如果您稍後進行新的*反復*專案, 並將其更新為預設值, 則不需要變更您的程式碼。

14. 當您按一下 [**預測 URL**] 之後, 請開啟 [*記事本*], 然後複製並貼上**URL** (也稱為您的**預測端點**) 和**服務預測金鑰**, 以便您稍後在程式碼中需要時加以取出。

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第3章-設定 Unity 專案

以下是使用混合現實進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本。

1.  開啟**Unity** , 然後按一下 [**新增**]。

    ![](images/AzureLabs-Lab310-21.png)

2.  現在您將需要提供 Unity 專案名稱。 插入**CustomVisionObjDetection**。 請確定 [專案類型] 設定為 [ **3d**], 並將 [位置] 設定為適合您的**位置**(請記住, 接近根目錄較佳)。 然後, 按一下 [**建立專案**]。

    ![](images/AzureLabs-Lab310-22.png)

3.  在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 **編輯* > *喜好設定** 從新的視窗中，然後瀏覽至 **外部工具** 。 將**外部腳本編輯器**變更為**Visual Studio**。 關閉 [**喜好**設定] 視窗。

    ![](images/AzureLabs-Lab310-23.png)

4.  接下來, 移至 [檔案] **> [組建設定**], 並將**平臺**切換至 [*通用 Windows 平臺*], 然後按一下 [**切換平臺**] 按鈕。

    ![](images/AzureLabs-Lab310-24.png)

5.  在相同的 [**組建設定**] 視窗中, 確定已設定下列各項:

    1.  **目標裝置**設定為**HoloLens**        
    2.  **組建類型**設定為**D3D**
    3.  **SDK**已設定為**最新安裝**
    4.  **Visual Studio 版本**設定為 [**最新安裝**]
    5.  **組建和執行**設定為**本機電腦**            
    6.  [**組建設定**] 中的其餘設定, 現在應該保留為預設值。

        ![](images/AzureLabs-Lab310-25.png)

6.  在相同的 [**組建設定**] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測**器**所在的空間中開啟相關的面板。

7. 在此面板中, 需要驗證幾項設定:

    1.  在 [**其他設定**] 索引標籤中:

        1.  **腳本執行階段版本**應該是**實驗**性 (.net 4.6 對等用法), 這將會觸發重新開機編輯器的需求。

        2. **腳本後端**應該是 **.net**。

        3. **API 相容性層級**應該是 **.net 4.6**。

            ![](images/AzureLabs-Lab310-26.png)

    2.  在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:

        1. **InternetClient**

        2.  **網路**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  在面板的正下方, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到)、[**支援的虛擬實境**], 然後確定已新增 [ **Windows Mixed Reality SDK** ]。

        ![](images/AzureLabs-Lab310-29.png)

8.  回到 [**組建設定**], *Unity\# C 專案*不再呈現灰色: 勾選 [this] 旁的核取方塊。

9.  關閉 [**組建設定**] 視窗。

10. 在**編輯器**中, 按一下 [**編輯** > **專案設定** > ] [**圖形**]。

    ![](images/AzureLabs-Lab310-30.png)

11. 在 [**偵測器] 面板** *圖形設定*將會開啟。 向下滾動直到看到名為 [**永遠包含著色**器] 的陣列。 藉由將**大小**變數增加一個來新增位置 (在此範例中, 它是 8, 所以我們將它設為 9)。 陣列的最後一個位置會出現新的位置, 如下所示:

    ![](images/AzureLabs-Lab310-31.png)

12. 在插槽中, 按一下插槽旁的小型目標圓形, 以開啟著色器清單。 尋找**舊版著色器/透明/擴散**著色器, 然後按兩下它。 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>第4章-匯入 CustomVisionObjDetection Unity 封裝

在此課程中, 您會提供名為**unitypackage**的 Unity 資產套件。 

> 首先Unity 支援的任何物件 (包括整個場景) 都可以封裝成**unitypackage**檔案, 並在其他專案中匯出/匯入。 這是在不同**Unity 專案**之間移動資產最安全且最有效率的方式。

您可以在[這裡找到您需要下載的 Azure-MR-310 套件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。

1.  在您前方的 Unity 儀表板中, 按一下畫面頂端功能表中的 **資產**, 然後按一下 匯**入套件 > 自訂套件**。

    ![](images/AzureLabs-Lab310-33.png)

2.  使用檔案選擇器選取**unitypackage**套件, 然後按一下 [**開啟**]。 系統會顯示此資產的元件清單。 按一下 [匯**入**] 按鈕以確認匯入。

    ![](images/AzureLabs-Lab310-34.png)

3.  完成匯入之後, 您會發現套件中的資料夾現在已新增至您的 [**資產**] 資料夾。 這種資料夾結構通常適用于 Unity 專案。

    ![](images/AzureLabs-Lab310-35.png)

    1.  [**材質**] 資料夾包含**注視游標**所使用的材質。 

    2.  [**外掛程式**] 資料夾包含程式碼用來還原序列化服務 web 回應的 Newtonsoft DLL。 資料夾和子資料夾中所包含的兩個 (2) 不同版本是必要的, 以便讓 Unity 編輯器和 UWP 組建都能使用並建立程式庫。 

    3.  **Prefabs**資料夾包含場景中包含的 Prefabs。 這些是:

        1.  **GazeCursor**, 這是應用程式中使用的資料指標。 會與 SpatialMapping prefab 搭配使用, 以放在實體物件頂端的場景中。
        2.  **標籤**, 這是在必要時, 用來在場景中顯示物件標記的 UI 物件。
        3.  **SpatialMapping**, 這是可讓應用程式使用 Microsoft HoloLens 的空間追蹤來建立虛擬對應的物件。

    4.  **幕後**資料夾, 其中目前包含此課程的預先建立場景。

4.  開啟 [**幕後**] 資料夾, 在 [**專案] 面板**中按兩下 [ **ObjDetectionScene**], 以載入您將用於本課程的場景。

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **未包含任何程式碼**, 您將會遵循此課程來撰寫程式碼。

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>第5章-建立 CustomVisionAnalyser 類別。

此時, 您已準備好撰寫一些程式碼。 您將會從**CustomVisionAnalyser**類別開始。

> [!NOTE]
> **自訂視覺服務**的呼叫是在如下所示的程式碼中, 使用**自訂視覺 REST API**來進行。 藉由使用此功能, 您將瞭解如何執行並利用此 API (適用于瞭解如何執行與您自己類似的專案)。 請注意, Microsoft 提供的**自訂視覺 SDK**也可以用來對服務進行呼叫。 如需詳細資訊, 請造訪[自訂視覺 SDK 文章](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。

此類別負責:

- 載入以位元組陣列形式捕獲的最新影像。

- 將位元組陣列傳送至您的 Azure**自訂視覺服務**實例以進行分析。

- 以 JSON 字串的形式接收回應。

- 還原序列化回應, 並將產生的**預測**傳遞至**SceneOrganiser**類別, 這會負責顯示回應的方式。

若要建立此類別:

1.  以滑鼠右鍵按一下 [**資產] 資料夾**(位於 [**專案] 面板**中), 然後按一下 [**建立** > **資料夾**]。 呼叫資料夾**腳本**。

    ![](images/AzureLabs-Lab310-37.png)

2.  按兩下新建立的資料夾, 將它開啟。

3.  在資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。 將腳本命名為**CustomVisionAnalyser。**

4.  按兩下新的**CustomVisionAnalyser**腳本, 以 Visual Studio 開啟它 **。**

5.  請確定您在檔案頂端參考了下列命名空間:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  在**CustomVisionAnalyser**類別中, 新增下列變數:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 請務必將您的**服務預測金鑰**插入至**predictionKey**變數, 並將**預測端點**插入**predictionEndpoint**變數中。 您稍[早在步驟14的第2章中](#chapter-2---training-your-custom-vision-project)將這些複製到「記事本」。

7.  現在必須加入**喚醒 ()** 的程式碼, 以初始化執行個體變數:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  新增協同程式 (使用其底下的靜態**GetImageAsByteArray ()** 方法), 它會取得由**ImageCapture**類別所捕獲的影像分析結果。

    > [!NOTE]
    > 在**AnalyseImageCapture**協同程式中, 會呼叫您尚未建立的**SceneOrganiser**類別。 因此, 請**將這些行暫時**加上批註。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. 刪除**Start ()** 和**Update ()** 方法, 因為它們將不會使用。 

10.  請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。

> [!IMPORTANT]
> 如先前所述, 請不要擔心可能出現錯誤的程式碼, 因為您很快就會提供進一步的類別, 這將會修正這些問題。

## <a name="chapter-6---create-the-customvisionobjects-class"></a>第6章-建立 CustomVisionObjects 類別

現在您將建立的類別是**CustomVisionObjects**類別。

此腳本包含許多物件, 可供其他類別用來序列化和還原序列化對自訂視覺服務所做的呼叫。

若要建立此類別:

1.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。 呼叫腳本**CustomVisionObjects。**

2.  按兩下新的**CustomVisionObjects**腳本, 以 Visual Studio 開啟它 **。**

3.  請確定您在檔案頂端參考了下列命名空間:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  刪除**CustomVisionObjects**類別內的**Start ()** 和**Update ()** 方法, 這個類別現在應該是空的。

    > [!WARNING]
    > 請務必仔細遵循下一個指示。 如果您將新的類別宣告放在**CustomVisionObjects**類別中, 您會在第[10 章](#chapter-10---create-the-imagecapture-class)取得編譯錯誤, 指出找不到**AnalysisRootObject**和**BoundingBox** 。

5.  將下列類別新增至**CustomVisionObjects**類別*之外*。 **Newtonsoft**程式庫會使用這些物件來序列化和還原序列化回應資料:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。

## <a name="chapter-7---create-the-spatialmapping-class"></a>第7章-建立 SpatialMapping 類別

這個類別會在場景中設定**空間對應碰撞**, 讓能夠偵測虛擬物件與實際物件之間的衝突。

若要建立此類別:

1.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。 呼叫腳本**SpatialMapping。**

2.  按兩下新的**SpatialMapping**腳本, 以 Visual Studio 開啟它 **。**

3.  請確定您已在**SpatialMapping**類別上方參考下列命名空間:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  然後, 在**SpatialMapping**類別內的**Start ()** 方法上方, 新增下列變數:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  新增**喚醒 ()** 和**Start ()** :

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  刪除**Update ()** 方法。

7.  請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。


## <a name="chapter-8---create-the-gazecursor-class"></a>第8章-建立 GazeCursor 類別

這個類別會負責使用上一章所建立的**SpatialMappingCollider**, 在實際空間中設定正確位置的資料指標。

若要建立此類別:

1.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。 呼叫腳本**GazeCursor**

2.  按兩下新的**GazeCursor**腳本, 以 Visual Studio 開啟它 **。**

3.  請確定您已在**GazeCursor**類別上方參考下列命名空間:

    ```csharp
    using UnityEngine;
    ```

4.  然後, 在**GazeCursor**類別內的**Start ()** 方法上方加入下列變數。 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  使用下列程式碼更新**Start ()** 方法:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  使用下列程式碼更新**update ()** 方法:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > 請不要擔心找不到**SceneOrganiser**類別的錯誤, 您將在下一章中建立它。

7. 請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。

## <a name="chapter-9---create-the-sceneorganiser-class"></a>第9章-建立 SceneOrganiser 類別

此類別將會:

-   藉由附加適當的元件來設定*主要攝影機*。

-   當偵測到物件時, 它會負責計算其在真實世界中的位置, 並將**標記標籤**放在其附近, 並加上適當的**標記名稱**。    

若要建立此類別:

1.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。 將腳本命名為**SceneOrganiser**。

2.  按兩下新的**SceneOrganiser**腳本, 以 Visual Studio 開啟它 **。**

3.  請確定您已在**SceneOrganiser**類別上方參考下列命名空間:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  然後, 在**SceneOrganiser**類別內的**Start ()** 方法上方新增下列變數:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  刪除**Start ()** 和**Update ()** 方法。

6.  在變數底下, 新增**喚醒 ()** 方法, 這會初始化類別並設定場景。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  新增**PlaceAnalysisLabel ()** 方法, 它會將場景中的標籤具現*化*(此時使用者不會看到此點)。 它也會放入影像所在的四個 (也不可見), 並與真實世界重迭。 這很重要, 因為在分析之後, 從服務中取出的方塊座標會重新追蹤到這個四個, 判斷物件在真實世界中的大約位置。 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  新增**FinaliseLabel ()** 方法。 它負責:

    *   使用具有最高信賴度的預測*標記*來設定*標籤*文字。
    *   在四個物件上呼叫周*框*方塊的計算, 其位於先前的位置, 並將標籤放置在場景中。
    *   針對周*框*方塊使用 Raycast 來調整標籤深度, 這應該會與真實世界中的物件發生衝突。
    * 重設 capture 進程, 讓使用者能夠捕獲另一個映射。

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  加入**CalculateBoundingBoxPosition ()** 方法, 它會裝載一些必要的計算, 以轉譯從服務中取出的周*框*方塊座標, 並在四個按比例重新建立它們。

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. 請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。

    > [!IMPORTANT]
    > 在繼續之前, 請開啟**CustomVisionAnalyser**類別, 然後在**AnalyseLastImageCaptured ()** 方法內,*取消*批註下列幾行:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> 不擔心**ImageCapture**類別「找不到」訊息, 您將在下一章中建立它。


## <a name="chapter-10---create-the-imagecapture-class"></a>第10章-建立 ImageCapture 類別

下一個您即將建立的類別是**ImageCapture**類別。

此類別負責:

*   使用 HoloLens 攝影機來捕獲影像, 並將其儲存在*應用程式*資料夾中。
*   處理使用者的*點擊*手勢。

若要建立此類別:

1.  移至您先前建立的**腳本**資料夾。

2.  在資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >  **C\#腳本**]。 將腳本命名為**ImageCapture**。

3.  按兩下新的**ImageCapture**腳本, 以 Visual Studio 開啟它 **。**

4.  將檔案頂端的命名空間取代為下列內容:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然後, 在**ImageCapture**類別內的**Start ()** 方法上方新增下列變數:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  現在必須加入**喚醒 ()** 和**Start ()** 方法的程式碼:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  執行會在點碰手勢發生時呼叫的處理常式:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > 當游標呈**綠色**時, 表示相機可以取得影像。 當游標為**紅色**時, 表示相機忙碌中。

8.  新增應用程式用來啟動映射捕獲進程並儲存映射的方法:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  新增將在拍攝相片時呼叫的處理常式, 以及準備進行分析的時間。 然後, 結果會傳遞至**CustomVisionAnalyser**進行分析。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 請務必先將您的變更儲存在**Visual Studio**中, 然後再返回**Unity**。

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>第11章-在場景中設定腳本

既然您已撰寫此專案所需的所有程式碼, 就可以開始設定場景中的腳本, 以及在 prefabs 上, 讓它們正常運作。

1.  在**Unity 編輯器**中的 [階層]**面板**中, 選取**主攝影機**。
2.  在 [偵測**器] 面板**中, 選取**主相機**後, 按一下 [**新增元件**], 然後搜尋 [ **SceneOrganiser**腳本], 再按兩下, 將其加入。

    ![](images/AzureLabs-Lab310-38.png)

3.  在 [**專案] 面板**中, 開啟 [ **Prefabs] 資料夾**, 將**標籤**prefab 拖曳至您剛才新增到*主要相機*的**SceneOrganiser**腳本中的*標籤*空白參照目標輸入區域, 如下所示:下圖:

    ![](images/AzureLabs-Lab310-39.png)

4.  在 [階層]**面板**中, 選取**主要攝影機**的 [ **GazeCursor** ] 子系。
5.  在 [偵測**器] 面板**中, 選取 [ **GazeCursor** ], 按一下 [**新增元件**], 然後搜尋 [ **GazeCursor**腳本], 再按兩下 [新增]。

    ![](images/AzureLabs-Lab310-40.png)

6.  同樣地, 在 [階層]**面板**中, 選取**主要攝影機**的**SpatialMapping**子系。
7.  在 [偵測**器] 面板**中, 選取 [ **SpatialMapping** ], 按一下 [**新增元件**], 然後搜尋 [ **SpatialMapping**腳本], 再按兩下 [新增]。

    ![](images/AzureLabs-Lab310-41.png)

您未設定的其餘腳本, 將會由**SceneOrganiser**腳本中的程式碼在執行時間中新增。

## <a name="chapter-12---before-building"></a>第12章-建立前

若要執行應用程式的徹底測試, 您必須將它側載到您的 Microsoft HoloLens。

在您執行之前, 請確定:

-  [第3章](#chapter-3---set-up-the-unity-project)所述的所有設定都已正確設定。
- 腳本**SceneOrganiser**會附加到**主要相機**物件。
- 腳本**GazeCursor**會附加至**GazeCursor**物件。
- 腳本**SpatialMapping**會附加至**SpatialMapping**物件。
- 在第[5 章](#chapter-5---create-the-customvisionanalyser-class), 步驟 6:

    - 請務必將您的**服務預測金鑰**插入**predictionKey**變數中。
    - 您已將**預測端點**插入至**predictionEndpoint**類別。

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>第13章-建立 UWP 解決方案並側載您的應用程式

您現在已準備好將應用程式建立為 UWP 解決方案, 讓您能夠將其部署至 Microsoft HoloLens。 若要開始建立程式:

1.  移至 [檔案] **> [組建設定**]。

2.  Tick **Unity C\#專案**。

3.  按一下 [**新增開啟的場景**]。 這會將目前開啟的場景新增至組建。

    ![](images/AzureLabs-Lab310-42.png)

4.  按一下 [建置]。 Unity 將會啟動 [檔案*瀏覽器*] 視窗, 您必須在其中建立並選取要建立應用程式的資料夾。 立即建立該資料夾, 並將它命名為**應用程式**。 然後選取 [**應用程式**] 資料夾, 按一下 [**選取資料夾**]。

5.  Unity 會開始將您的專案建立至**應用程式**資料夾。

6.  Unity 完成建立之後 (可能需要一些時間), 它會在組建的位置開啟 [檔案**瀏覽器**] 視窗 (請檢查您的工作列, 因為它不一定會出現在視窗的上方, 但會通知您加入新的視窗)。

7.  若要部署至 Microsoft HoloLens, 您將需要該裝置的 IP 位址 (用於遠端部署), 並確保它也已設定**開發人員模式**。 請這樣做：

    1.  在戴 HoloLens 的同時, 請開啟**設定**。

    2.  前往**Network & Internet**  >  **wi-fi**  >  **Advanced Options**

    3.  記下**IPv4**位址。

    4.  接下來, 流覽回到 [**設定**], 然後為**開發人員** **更新 & 安全性** > 

    5.  設定**開發人員模式** *上*。

8.  流覽至新的 Unity 組建 (**應用程式**資料夾), 然後使用**Visual Studio**開啟方案檔。

9.  在 [解決方案設定] 中, 選取 [ **Debug**]。

10. 在解決方案平臺中, 選取 [ **x86]、[遠端電腦**]。 系統會提示您插入遠端裝置的**IP 位址**(在此案例中, 這是您記下的 Microsoft HoloLens)。

    ![](images/AzureLabs-Lab310-43.png)

11. 移至 [**建立**] 功能表, 然後按一下 [**部署方案**], 將應用程式側載至您的 HoloLens。

12. 您的應用程式現在應該會出現在 Microsoft HoloLens 上已安裝的應用程式清單中, 好讓您可以啟動!

### <a name="to-use-the-application"></a>若要使用應用程式:

* 查看物件, 您已使用**Azure 自訂視覺服務、物件偵測**來進行定型, 並使用點按**手勢**。
* 如果成功偵測到物件, 就會出現具有標記名稱的世界空間*標籤文字*。

> [!IMPORTANT]
> 每次您捕捉相片並將它傳送至服務時, 您可以返回 [服務] 頁面, 並以新建立的映射重新定型服務。 一開始, 您可能也必須更正周*框方塊*, 使其更正確, 並重新定型服務。

> [!NOTE]
> 當 Microsoft HoloLens 感應器和/或 Unity 中的 SpatialTrackingComponent 無法放置適當的 colliders (相對於真實世界物件) 時, 放置的標籤文字可能不會出現在物件附近。 如果是這種情況, 請嘗試在不同的表面上使用應用程式。

## <a name="your-custom-vision-object-detection-application"></a>您的自訂視覺, 物件偵測應用程式

恭喜您, 您建立了一個混合現實應用程式, 利用 Azure 自訂視覺的物件偵測 API, 它可以辨識影像中的物件, 然後在3D 空間中提供該物件的近似位置。

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

將加入至文字標籤時, 請使用半透明的 cube, 將實際物件包裝在3D 周*框*方塊中。

### <a name="exercise-2"></a>練習2

訓練您的自訂視覺服務, 以辨識更多物件。

### <a name="exercise-3"></a>練習3

在辨識物件時播放音效。

### <a name="exercise-4"></a>練習4

使用 API, 以應用程式所分析的相同影像重新訓練您的服務, 以便讓服務更精確 (同時進行預測和定型)。
