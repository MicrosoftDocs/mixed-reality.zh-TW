---
title: MR 和 Azure 310-物體偵測
description: 完成此課程來了解如何定型機器學習服務模型，然後使用定型的模型來識別相似的物件，並在混合的實境應用程式中從真實世界中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 中，自訂的視覺物件偵測、 混合實境、 academy、 unity、 教學課程、 api、 hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591148"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

# <a name="mr-and-azure-310-object-detection"></a>Mr 和 Azure 310:物件偵測

在此課程中，您將了解如何識別自訂的視覺內容，並提供的映像中，其空間位置使用 Azure Custom Vision 混合的實境應用程式中的 「 物件偵測 」 功能。

這項服務可讓您定型機器學習模型，使用物件的映像。 然後將定型的模型識別相似的物件，然後大約在真實世界中，其位置所提供的 Microsoft HoloLens 相機擷取或相機連接到電腦的沈浸式 (VR) 耳機。

![課程結果](images/AzureLabs-Lab310-00.png)

**Azure Custom Vision、 物體偵測**是一項 Microsoft 服務可讓開發人員建置自訂映像分類器。 這些分類器可以再搭配新的映像來偵測該新的映像 」 中的物件，藉由提供** 方塊界限**的映像本身。 服務提供簡單、 容易使用的線上的入口網站，來簡化此程序。 如需詳細資訊，請瀏覽下列連結：

* [Azure 的自訂視覺頁面](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [限制和配額](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

完成本課程的詳細資訊，您必須能夠執行下列作業的混合的實境應用程式：

1. 使用者將能夠*視線*的物件，它們必須使用 Azure Custom Vision Service，物件偵測來進行定型。 
2. 使用者會使用*點選*擷取的東西在映像的筆勢。
3. 應用程式會將影像傳送到 Azure Custom Vision Service。
4. 將會有的服務也會以全局空間文字顯示結果的辨識的回覆。 這會透過使用 Microsoft HoloLens 的空間追蹤，了解世界空間位置的可辨識的物件，然後使用這種方式來完成*標記*與項目中偵測到映像，為相關聯提供的標籤文字。

本課程也將涵蓋手動上傳的映像，建立標記，並訓練辨識不同的服務物件 （在提供的範例中，一杯），藉由設定*邊界方塊*您提交映像中。 

> [!IMPORTANT]
> 下列建立和使用應用程式中，開發人員應瀏覽回 Azure Custom Vision Service，並識別服務時，所做的預測，並判斷是否它們是正確或不 (透過標記的任何項目服務遺漏，以及調整*週框方塊*)。 服務可以再進行重新定型，這會增加它辨識真實世界物件的可能性。

本課程將教導您如何從 Azure Custom Vision Service，物件偵測的結果取得到 Unity 為基礎的範例應用程式。 它會決定要將這些概念套用到您可能建置自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 310:物件偵測</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程專為具有基礎經驗的 Unity 開發人員和C#。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。 中所示，您可以自由使用最新的軟體[安裝工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。

我們建議下列的硬體和軟體這堂課程：

- 開發電腦
- [Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [最新的 Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)啟用開發人員模式
- Azure 設定及自訂視覺服務擷取的網際網路存取
-  一系列的最少 15 （15） 映像所需的） 每個物件，您想要自訂視覺辨識。 如果您想，您可以使用本課程中，已提供的映像[一連串的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

## <a name="before-you-start"></a>開始之前

1.  若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。
2.  設定並測試您的 HoloLens。 如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。 

校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。

如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。

## <a name="chapter-1---the-custom-vision-portal"></a>第 1 章-Custom Vision 入口網站

若要使用**Azure Custom Vision Service**，您必須設定它可讓您的應用程式使用的執行個體。

1.  瀏覽[要**Custom Vision Service**主頁](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  按一下 **開始使用**。

    ![](images/AzureLabs-Lab310-01.png)

3.  登入自訂視覺入口網站。

    ![](images/AzureLabs-Lab310-02.png)

4.  如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

5.  當您第一次登入時，您將會收到提示*服務條款*面板。 按一下核取方塊*同意條款*。 然後按一下**我同意**。

    ![](images/AzureLabs-Lab310-03.png)

6.  需要同意的條款，現在您已*我的專案*一節。 按一下 **新的專案**。

    ![](images/AzureLabs-Lab310-04.png)

7.  索引標籤會出現在右手邊的畫面會提示您指定的專案部分欄位。

    1.  插入您的專案名稱

    2.  插入您專案的描述 (**選擇性**)

    3.  選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些課程中） 的單一專案相關聯的所有 Azure 服務）。

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > 如果您想要[深入了解 Azure 資源群組中，瀏覽至相關聯的文件](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  設定**專案類型**作為**物體偵測 （預覽）**。

8.  一旦您完成時，按一下**建立專案**，您就會重新導向至 Custom Vision Service 專案頁面。


## <a name="chapter-2---training-your-custom-vision-project"></a>第 2 章-訓練您的自訂視覺專案

一次在自訂視覺入口網站中，您的主要目標是訓練您的專案，以辨識影像中的特定物件。

對於每個您想要您的應用程式，可辨識的物件，您就會需要至少 15 個映像。 您可以使用本課程提供的映像 ([一連串的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

若要訓練您的自訂視覺專案：

1.  按一下  **+** 按鈕旁**標記**。

    ![](images/AzureLabs-Lab310-06.png)

2.  新增**名稱**將用來將您的映像，以建立關聯的標記。 在此範例中我們用來辨識，因此已為此，命名標記映像的 cup **Cup**。 按一下 **儲存**一次完成。

    ![](images/AzureLabs-Lab310-07.png)

3.  您會注意到您**標記**已加入 （您可能需要重新載入您的頁面才會出現）。 

    ![](images/AzureLabs-Lab310-08.png)

4.  按一下 **將影像加入**中頁面的中心。

    ![](images/AzureLabs-Lab310-09.png)

5.  按一下 **瀏覽本機檔案**，並瀏覽至您想要一個物件，並將最小值是 15 (15) 上傳的映像。

    > [!TIP]
    >  您可以選取數個映像，一次，若要上傳。

    ![](images/AzureLabs-Lab310-10.png)

6.  按下**將檔案上傳**一旦您選取的所有映像您想要定型的專案。 檔案就會開始上傳。 上傳的確認之後，按一下**完成**。

    ![](images/AzureLabs-Lab310-11.png)

7.  此時您的映像上傳，但未標記。

    ![](images/AzureLabs-Lab310-12.png)

8.  若要標記您的映像，請使用滑鼠。 當您暫留在您的映像的選取項目反白顯示都能協助您藉由自動繪製您的物件周圍的選取範圍。 如果您不正確，您可以繪製您自己。 這被透過滑鼠不放，以滑鼠左鍵按一下和拖曳選取範圍區域，以包含您的物件。 

    ![](images/AzureLabs-Lab310-13.png) 

9. 下列映像中物件的選取項目，小型的提示字元會要求您提供*新增 Region 標記*。 選取您先前建立的標記 ('Cup'，在上述範例中)，或如果您要新增更多標籤，輸入，然後按一下 **+ （加號）**  按鈕。

    ![](images/AzureLabs-Lab310-14.png) 

10. 若要標記下一步 的映像，您可以按一下刀鋒視窗中，右邊的箭號，或關閉 標記 刀鋒視窗 (依序按一下**X**刀鋒視窗的右上角)，然後按一下 下一步 的影像。 下一步 的映像準備好之後，重複執行相同的程序。 您已上傳，直到被所有標記的所有映像執行這項操作。 

    > [!NOTE]
    >  您可以選取數個物件相同的映像，類似下面的影像中： 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. 一旦您已標記它們全部，按一下**標記**按鈕，在左邊的畫面中，以顯示已加上標記的映像。 

    ![](images/AzureLabs-Lab310-16.png)

12. 您現在已準備好定型您的服務。 按一下 **定型**按鈕，然後在第一個訓練反覆項目就會開始。

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. 一旦建立，您會看到兩個按鈕稱為**設成預設值**並**預測 URL**。 按一下 **設成預設值**第一次，然後按一下**預測 URL**。

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > 提供從這裡開始，將端點設為者為準*反覆項目*已標示為預設值。 因此，如果您稍後建立新*反覆項目*更新為預設值，您不需要變更程式碼。

14. 一旦您按下**預測 URL**，開啟*記事本*，然後複製並貼上**URL** (也稱為您**預測端點**)而**服務的預測金鑰**，如此一來，您可以稍後在程式碼中需要時擷取它。

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟**Unity**然後按一下**新增**。

    ![](images/AzureLabs-Lab310-21.png)

2.  您現在必須提供 Unity 專案名稱。 插入**CustomVisionObjDetection**。 請確定專案類型設定為**3D**，並將**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![](images/AzureLabs-Lab310-22.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯* > *喜好設定** 從新的視窗中，然後瀏覽至**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio**。 關閉**喜好設定**視窗。

    ![](images/AzureLabs-Lab310-23.png)

4.  接下來，移至**檔案 > 組建設定**，並切換**平台**來*通用 Windows 平台*，然後按一下**切換平台**  按鈕。

    ![](images/AzureLabs-Lab310-24.png)

5.  在同一個**組建設定** 視窗中，請確定下列設定：

    1.  **裝置為目標**設為**HoloLens**        
    2.  **建置型別**設為**D3D**
    3.  **SDK**設為**最新安裝**
    4.  **Visual Studio 版本**設為**最新安裝**
    5.  **建置並執行**設為**本機電腦**            
    6.  剩餘的設定，**組建設定**，應保持為預設值，現在。

        ![](images/AzureLabs-Lab310-25.png)

6.  在同一個**組建設定**視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。

7. 在此窗格中，少數設定需要驗證：

    1.  在 [**其他設定**] 索引標籤：

        1.  **指令碼執行階段版本**應該**實驗性**（.NET 4.6 對等），這會觸發程序需要重新啟動編輯器。

        2. **指令碼後端**應該 **.NET**。

        3. **API 相容性層級**應該 **.NET 4.6**。

            ![](images/AzureLabs-Lab310-26.png)

    2.  內**發佈設定**索引標籤之下**功能**，檢查：

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，然後確定**Windows 混合但實際上 SDK**加入。

        ![](images/AzureLabs-Lab310-29.png)

8.  回到**Build Settings**， *Unity C\#專案*不再呈現灰色： 這旁邊的核取方塊。

9.  關閉**組建設定**視窗。

10. 在 **編輯器**，按一下**編輯** > **專案設定** > **圖形**。

    ![](images/AzureLabs-Lab310-30.png)

11. 在 [**偵測器] 面板***圖形設定*將會開啟。 向下捲動，直到您看到稱為陣列**一律包含著色器**。 新增位置透過增加**大小**其中一個變數 (在此範例中，所以 8 我們 9)。 新的位置會顯示，在陣列中的最後一個位置，如下所示：

    ![](images/AzureLabs-Lab310-31.png)

12. 在位置中，按一下的位置，以開啟一份著色器旁邊的小目標圓形。 尋求**Diffuse/著色器/Transparent 舊版**著色器，然後按兩下它。 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>第 4 章-匯入 CustomVisionObjDetection Unity 封裝

本課程為您提供 Unity 資產套件，稱為**Azure-MR-310.unitypackage**。 

> [提示]支援的 Unity，包含整個場景，任何物件可以封裝到 **.unitypackage**檔案，並匯出 / 匯入在其他專案中。 這是將資產移之間不同最安全的且最有效率的方式**Unity 專案**。

您可以找到[您必須下載此處的 Azure-MR-310 封裝](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。

1.  您面前的 Unity 儀表板中，按一下**資產**在畫面頂端的功能表，然後按一下**匯入封裝 > 自訂封裝**。

    ![](images/AzureLabs-Lab310-33.png)

2.  使用檔案選擇器選取**Azure-MR-310.unitypackage**封裝，然後按一下**開啟**。 為此資產的元件的清單會顯示給您。 確認匯入，依序按一下**匯入** 按鈕。

    ![](images/AzureLabs-Lab310-34.png)

3.  完成匯入後，您會發現現在有已從封裝的資料夾新增至您**資產**資料夾。 這種資料夾結構是典型的 Unity 專案。

    ![](images/AzureLabs-Lab310-35.png)

    1.  **材料**資料夾包含所使用的材料**視線游標**。 

    2.  **外掛程式**資料夾包含用來還原序列化服務的 web 回應的程式碼 Newtonsoft DLL。 兩個 （2） 不同的版本中所包含的資料夾，以及子資料夾中，會允許要使用與 Unity Editor 和 UWP 建置所建置的程式庫所需。 

    3.  **Prefabs**資料夾包含在場景中包含 prefabs。 這些是：

        1.  **GazeCursor**，應用程式中使用的游標。 將 SpatialMapping prefab，若要能夠放在實體物件上場景中一起運作。
        2.  **標籤**，它是用來顯示物件標記中的場景時所需的 UI 物件。
        3.  **SpatialMapping**，這是讓應用程式使用的物件建立一個虛擬的對應，使用 Microsoft HoloLens 的空間追蹤。

    4.  **場景**所在的資料夾目前這堂課程預先建置的場景。

4.  開啟**場景**資料夾，請在 **[專案] 面板**，然後按兩下**ObjDetectionScene**、 載入場景，您將用於本課程。

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **不包含任何程式碼**，您將會依照本課程中撰寫程式碼。

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>第 5-建立 CustomVisionAnalyser 類別。

此時，您已準備好開始撰寫一些程式碼。 將開頭**CustomVisionAnalyser**類別。

> [!NOTE]
> 若要呼叫**Custom Vision Service**，如下所示的程式碼中，使用**自訂視覺 REST API**。 透過使用這種情況，您會看到如何實作及使用此 api （適用於了解如何自行實作類似）。 請注意，Microsoft 提供了**自訂視覺 SDK** ，也可用來對服務進行呼叫。 如需詳細資訊，請造訪[自訂視覺 SDK 文件](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。

這個類別會負責：

- 正在載入最新的映像擷取成位元組陣列。

- 將位元組陣列傳送至您的 Azure **Custom Vision Service**執行個體進行分析。

- 接收回應為 JSON 字串。

- 還原序列化回應，並傳遞產生**預測**要**SceneOrganiser**類別，它會負責顯示回應的方式。

若要建立此類別：

1.  以滑鼠右鍵按一下**Assets 資料夾**，位於 **[專案] 面板**，然後按一下**建立** > **資料夾**。 呼叫資料夾**指令碼**。

    ![](images/AzureLabs-Lab310-37.png)

2.  按兩下新建立的資料夾，將它開啟。

3.  在資料夾中，以滑鼠右鍵按一下，然後按一下  **Create** > **C\#指令碼**。 指令碼命名**CustomVisionAnalyser。**

4.  按兩下新**CustomVisionAnalyser**指令碼，以開啟它**Visual Studio。**

5.  請確定您有下列命名空間參考在檔案頂端：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  在  **CustomVisionAnalyser**類別中，新增下列變數：

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
    > 請確定您插入您**服務的預測金鑰**成**predictionKey**變數和您**預測端點**到**predictionEndpoint**變數。 您可以複製這些[記事本更早版本，在第 2 章步驟 14](#chapter-2---training-your-custom-vision-project)。

7.  程式碼**Awake()** 現在必須初始化執行個體變數新增：

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

8.  新增協同程式 (具有靜態**GetImageAsByteArray()** 下方的方法)，這將會取得映像，所擷取的分析結果**ImageCapture**類別。

    > [!NOTE]
    > 在  **AnalyseImageCapture**協同程式，來呼叫**SceneOrganiser**您即將建立的類別。 因此，**保留的線條標記為註解現在**。

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

9. 刪除**start （)** 並**update （)** 方法，因為它們不會使用。 

10.  請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。

> [!IMPORTANT]
> 如先前所述，不必擔心可能會顯示有錯誤，將會進一步提供類別，以修正這些程式碼。

## <a name="chapter-6---create-the-customvisionobjects-class"></a>章節 6-建立 CustomVisionObjects 類別

您將建立的類別現在是**CustomVisionObjects**類別。

此指令碼包含用來序列化和還原序列化 Custom Vision Service 進行的呼叫其他類別的物件數目。

若要建立此類別：

1.  以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。 呼叫指令碼**CustomVisionObjects。**

2.  按兩下新**CustomVisionObjects**指令碼，以開啟它**Visual Studio。**

3.  請確定您有下列命名空間參考在檔案頂端：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  刪除**start （)** 並**update （)** 內的方法**CustomVisionObjects**類別，這個類別現在應空白。

    > [!WARNING]
    > 請務必仔細遵循下一步 的指示。 如果您將新的類別宣告內**CustomVisionObjects**類別，會產生編譯錯誤，[章 10](#chapter-10---create-the-imagecapture-class)，， **AnalysisRootObject**和**BoundingBox**找不到。

5.  新增下列類別*外* **CustomVisionObjects**類別。 這些物件由**Newtonsoft**序列化和還原序列化回應資料的程式庫：

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

6.  請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。

## <a name="chapter-7---create-the-spatialmapping-class"></a>第 7-建立 SpatialMapping 類別

此類別會設定**空間的對應 Collider**因此若要能夠偵測到虛擬與實際的物件間的衝突，場景中。

若要建立此類別：

1.  以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。 呼叫指令碼**SpatialMapping。**

2.  按兩下新**SpatialMapping**指令碼，以開啟它**Visual Studio。**

3.  請確定您具有下列命名空間上面提及**SpatialMapping**類別：

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  然後，新增下列變數內**SpatialMapping**類別，上述**start （)** 方法：

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

5.  新增**Awake()** 並**start**:

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

6.  刪除**update （)** 方法。

7.  請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。


## <a name="chapter-8---create-the-gazecursor-class"></a>第 8-建立 GazeCursor 類別

這個類別會負責設定資料指標，在正確的位置，在實際的空間中，藉由使用**SpatialMappingCollider**、 上一章中建立。

若要建立此類別：

1.  以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。 呼叫指令碼**GazeCursor**

2.  按兩下新**GazeCursor**指令碼，以開啟它**Visual Studio。**

3.  請確定您具有下列命名空間，上面提及**GazeCursor**類別：

    ```csharp
    using UnityEngine;
    ```

4.  然後新增下列變數內**GazeCursor**類別，上述**start （)** 方法。 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  更新**start （)** 為下列程式碼的方法：

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

6.  更新**update （)** 為下列程式碼的方法：

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
    > 不必擔心的錯誤**SceneOrganiser**類別找不到，您將在下一步 一章。

7. 請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。

## <a name="chapter-9---create-the-sceneorganiser-class"></a>第 9-建立 SceneOrganiser 類別

這個類別將會：

-   設定好*Main Camera*將 cvcollectioncmd 附加至適當的元件。

-   偵測到物件時，它會負責計算其位置與真實世界中的位置**標記標籤**附近以適當**標記名稱**。    

若要建立此類別：

1.  以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。 指令碼命名**SceneOrganiser**。

2.  按兩下新**SceneOrganiser**指令碼，以開啟它**Visual Studio。**

3.  請確定您具有下列命名空間上面提及**SceneOrganiser**類別：

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  然後新增下列變數內**SceneOrganiser**類別，上述**start （)** 方法：

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

5.  刪除**start （)** 並**update （)** 方法。

6.  底下的變數中，加入**Awake()** 方法，它會初始化類別，並設定場景。

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

7.  新增**PlaceAnalysisLabel()** 方法，將*具現化*場景 （這現在是看不到使用者項目） 中的標籤。 它也會四組數字 （也不可見） 映像放，而與真實世界重疊。 這很重要，因為方塊座標會從服務擷取之後分析會回溯追蹤到這個四判斷真實世界中物件的概略位置。 

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

8.  新增**FinaliseLabel()** 方法。 它會負責：

    *   設定*標籤*文字*標記*具有最高信賴度預測。
    *   呼叫的計算*週框方塊*在四個物件，過去，定位和放置在場景中的標籤。
    *   使用針對 Raycast 調整標籤深度*週框方塊*，這應該會對真實世界中的物件發生衝突。
    * 正在重設以允許使用者擷取另一個映像擷取程序。

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

9.  新增**CalculateBoundingBoxPosition()** 方法，它會裝載數目進行轉譯所需的計算*週框方塊*座標從服務擷取和重新建立它們按比例上四組數字。

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

10. 請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。

    > [!IMPORTANT]
    > 在繼續之前，開啟**CustomVisionAnalyser**類別，會在**AnalyseLastImageCaptured()** 方法*取消註解*下列幾行：
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
> 不要擔心**ImageCapture**類別 '無法找到' 的訊息中，您將在下一步 一章。


## <a name="chapter-10---create-the-imagecapture-class"></a>第 10-建立 ImageCapture 類別

下一步要建立的類別是**ImageCapture**類別。

這個類別會負責：

*   擷取映像使用 HoloLens 相機，並將它儲存在*應用程式*資料夾。
*   處理*點選*使用者筆勢。

若要建立此類別：

1.  移至**指令碼**您先前建立的資料夾。

2.  在資料夾中，以滑鼠右鍵按一下，然後按一下  **Create** > **C\#指令碼**。 指令碼命名**ImageCapture**。

3.  按兩下新**ImageCapture**指令碼，以開啟它**Visual Studio。**

4.  以下列內容取代頂端的 檔案命名空間：

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然後新增下列變數內**ImageCapture**類別，上述**start （)** 方法：

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

6.  程式碼**Awake()** 並**start （)** 方法現在需要新增：

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

7.  實作會在點選手勢時呼叫的處理常式：

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
    > 當游標位於**綠色**，它表示相機可採取的映像。 當游標位於**紅色**，這表示相機正在忙碌中。

8.  新增應用程式用來啟動映像擷取程序，並儲存映像的方法：

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

9.  新增處理常式會被呼叫時已擷取相片並時準備好進行分析。 結果會傳遞至**CustomVisionAnalyser**進行分析。

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

10. 請務必儲存您的變更，在**Visual Studio**，然後再回到**Unity**。

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>第 11 章-設定在場景中的指令碼

既然您已撰寫所有必要為此專案的程式碼，就可以設定在場景，與在 prefabs，才能正確運作的指令碼。

1.  內**Unity Editor**，請在**階層面板**，選取**Main Camera**。
2.  在 [**偵測器] 面板**，與**Main Camera**選取，按一下**新增元件**，然後搜尋**SceneOrganiser**指令碼和連按兩下，以將它加入。

    ![](images/AzureLabs-Lab310-38.png)

3.  在 [**專案] 面板**，開啟**Prefabs 資料夾**，拖曳**標籤**prefab 到*標籤*空白參考目標中輸入區域中，**SceneOrganiser**您剛剛加到的指令碼*Main Camera*，如下圖所示：

    ![](images/AzureLabs-Lab310-39.png)

4.  在 **階層面板**，選取**GazeCursor**的子系**Main Camera**。
5.  在 [**偵測器] 面板**，與**GazeCursor**選取，按一下**新增元件**，然後搜尋**GazeCursor**指令碼和連按兩下，以將它加入。

    ![](images/AzureLabs-Lab310-40.png)

6.  同樣地，在**階層面板**，選取**SpatialMapping**的子系**Main Camera**。
7.  在 [**偵測器] 面板**，與**SpatialMapping**選取，按一下**新增元件**，然後搜尋**SpatialMapping**指令碼然後連按兩下，以將它加入。

    ![](images/AzureLabs-Lab310-41.png)

其餘的您的指令碼尚未設定將加入程式碼所**SceneOrganiser**指令碼，在執行階段。

## <a name="chapter-12---before-building"></a>第 12 章-建置前

若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 Microsoft HoloLens。

這麼做之前，請確認：

-  中所述的所有設定[第 3 章](#chapter-3---set-up-the-unity-project)都已正確設定。
- 指令碼**SceneOrganiser**附加至**Main Camera**物件。
- 指令碼**GazeCursor**附加至**GazeCursor**物件。
- 指令碼**SpatialMapping**附加至**SpatialMapping**物件。
- 在 [第 5 章](#chapter-5---create-the-customvisionanalyser-class)，步驟 6:

    - 請確定您插入您**預測的服務金鑰**成**predictionKey**變數。
    - 您已插入您**預測端點**成**predictionEndpoint**類別。

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>第 13-建置的 UWP 方案和側載您的應用程式

您現在就來建置您的應用程式做為您將能夠部署到 Microsoft HoloLens 的 UWP 方案。 若要開始建置程序：

1.  移至**檔案 > 組建設定**。

2.  刻度**Unity C\#專案**。

3.  按一下 **將開啟的場景新增**。 這會將目前開啟的場景新增至組建。

    ![](images/AzureLabs-Lab310-42.png)

4.  按一下 [建置] 。 將會啟動 unity*檔案總管*視窗中，您要建立，然後選取 建置到應用程式的資料夾。 現在，建立該資料夾並將它命名**應用程式**。 然後使用**應用程式**按一下 選取資料夾**選取資料夾**。

5.  Unity 會開始建置您的專案**應用程式**資料夾。

6.  一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。

7.  若要部署到 Microsoft HoloLens，您會需要該裝置的 IP 位址 （適用於遠端部署），並確認也已**開發人員模式**設定。 請這樣做：

    1.  儘管穿著您 HoloLens，開啟**設定**。

    2.  移至**網路和網際網路** > **Wi-fi** > **進階選項**

    3.  附註**IPv4**位址。

    4.  接下來，瀏覽回到**設定**，然後**更新與安全性** > **適用於開發人員**

    5.  設定**開發人員模式***上*。

8.  瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。

9.  在 方案組態選取**偵錯**。

10. 在 方案平台上，選取**x86，遠端機器**。 系統會提示您插入**IP 位址**的遠端裝置上 (Microsoft HoloLens，在此情況下，記下)。

    ![](images/AzureLabs-Lab310-43.png)

11. 移至**建置**功能表，然後按一下 **部署方案**側載您 HoloLens 應用程式。

12. 您的應用程式現在應該會出現在清單中，在您的 Microsoft HoloLens，即可啟動已安裝的應用程式 ！

### <a name="to-use-the-application"></a>若要使用應用程式：

* 查看的物件，您培訓與您**Azure Custom Vision Service、 物體偵測**，並使用**點選手勢**。
* 如果物件已成功偵測到，全局空間*標籤文字*標記名稱會出現。

> [!IMPORTANT]
> 每次您擷取相片，並將它傳送至服務，您可以返回 [服務] 頁面，並重新定型新擷取的映像的服務。 在開始時，可能會也必須更正*週框方塊*得更為準確地重新訓練的服務。

> [!NOTE]
> 當 Microsoft HoloLens 感應器和/或在 Unity SpatialTrackingComponent 無法放置適當的 colliders，相對於真實世界物件放置標籤文字可能不會顯示接近的物件。 嘗試使用不同的介面上的應用程式，如果這種情況。

## <a name="your-custom-vision-object-detection-application"></a>您自訂的願景，物件偵測應用程式

恭喜，您所建立的混合的實境應用程式，運用 Azure 自訂視覺物件偵測 API，而可以辨識的物件，從映像，然後提供該物件在 3D 空間中的約略位置。

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

加入文字標籤，來包裝的實際物件的 3D 中使用半透明效果 cube*週框方塊*。

### <a name="exercise-2"></a>練習 2

訓練您的自訂視覺服務辨識更多的物件。

### <a name="exercise-3"></a>練習 3

當辨識項物件時，請播放的音效。

### <a name="exercise-4"></a>練習 4

使用 API，來重新訓練您的服務，與正在分析您的應用程式相同的映像，因此若要讓服務更精確 （執行預測和同時訓練）。
