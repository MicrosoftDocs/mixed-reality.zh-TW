---
title: MR 和 Azure 302b-自訂視覺
description: 完成此課程來了解如何定型機器學習服務模型，然後使用定型的模型可辨識的混合的實境應用程式中的相似物件。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 自訂視覺、 hololens、 沉浸式 vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591812"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR 和 Azure 302b:自訂辨識

在此課程中，您將學習如何辨識提供的映像 」 中的自訂視覺內容混合的實境應用程式中使用 Azure 自訂視覺功能。

這項服務可讓您定型機器學習模型，使用物件的映像。 然後您會辨識相似的物件，使用定型的模型，由攝影機擷取的 Microsoft HoloLens 或連線到您電腦上的沈浸式 (VR) 耳機相機所提供。

![課程結果](images/AzureLabs-Lab302b-00.png)

Azure Custom Vision 是 Microsoft 的認知服務，可讓開發人員建置自訂映像分類器。 這些分類器可以再搭配新的映像辨識，或分類，該新的映像中的物件。 服務提供簡單、 容易使用的線上入口網站簡化程序。 如需詳細資訊，請瀏覽[Azure Custom Vision Service 頁面](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。

完成本課程的詳細資訊，您必須將能夠在兩個模式下運作的混合的實境應用程式：

-   **分析模式**: Custom Vision Service 手動設定上傳映像、 建立標記，並訓練服務辨識不同的物件 （在此案例的滑鼠和鍵盤）。 您接著會建立一個 HoloLens 的應用程式，將擷取映像使用相機，並嘗試辨識這些真實世界中的物件。

-   **定型模式**： 您會實作可讓您的應用程式在 「 定型模式 」 的程式碼。 定型模式可讓您擷取映像使用 HoloLens' 相機、 將擷取的映像上傳至服務，以及自訂視覺模型定型。

本課程將教導您如何從 Custom Vision Service 取得結果，到 Unity 為基礎的範例應用程式。 它會決定要將這些概念套用到您可能建置自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 302b:自訂辨識</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然這堂課程主要著重於 HoloLens，您也可以套用您在此課程 Windows Mixed Reality 沈浸式 (VR) 耳機來了解。 因為沈浸式 (VR) 耳機並沒有可存取的相機，您必須連線到您的 PC 外部相機。 當您遵循本課程中，您會看到 備忘稿上用來支援沈浸式 (VR) 耳機時，您可能需要的任何變更。

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程專為具有基礎經驗的 Unity 開發人員和C#。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。 中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。

我們建議下列的硬體和軟體這堂課程：

- 開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發
- [Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式
- 相機連接到您的電腦 （開發沈浸式耳機）
- Azure 設定及自訂視覺 API 擷取的網際網路存取
- 至少五 （5） 映像 （十 （10） 建議選項） 的一系列的每個您想要自訂視覺服務，可辨識的物件。 如果您想，您可以使用[這個課程 （電腦滑鼠和鍵盤） 已提供的映像](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。

## <a name="before-you-start"></a>開始之前

1.  若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。
2.  設定並測試您的 HoloLens。 如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。 

校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。

如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。

## <a name="chapter-1---the-custom-vision-service-portal"></a>第 1 章-Custom Vision Service 入口網站

若要使用*Custom Vision Service*在 Azure 中，您必須設定您的應用程式提供服務的執行個體。

1.  首先，[瀏覽至*Custom Vision Service*主頁](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  按一下 [**開始**] 按鈕。

    ![](images/AzureLabs-Lab302b-01.png)

3.  登入*Custom Vision Service*入口網站。

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

4.  當您第一次登入時，您將會收到提示*服務條款*面板。 按一下核取方塊以同意條款。 然後按一下**我同意**。

    ![](images/AzureLabs-Lab302b-03.png)

5.  需要同意的條款，您將瀏覽至*專案*入口網站區段。 按一下 **新的專案**。

    ![](images/AzureLabs-Lab302b-04.png)

6.  索引標籤會出現在右手邊的畫面會提示您指定的專案部分欄位。

    1.  插入*名稱*為您的專案。

    2.  插入*描述*為您的專案 (*選擇性*)。

    3.  選擇*資源群組*或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。

    4. 設定*專案類型*到**分類**
    
    5. 設定*網域*作為**一般**。

        ![](images/AzureLabs-Lab302b-05.png)

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

7.  一旦您完成時，按一下**建立專案**，您將會重新導向至 Custom Vision Service，專案頁面。

## <a name="chapter-2---training-your-custom-vision-project"></a>第 2 章-訓練您的自訂視覺專案

一次在自訂視覺入口網站中，您的主要目標是訓練您的專案，以辨識影像中的特定物件。 您需要至少五 （5） 映像，但十 （10），最好使用，針對每個您想要您的應用程式，可辨識的物件。 [您可以使用本課程 （電腦滑鼠和鍵盤） 提供的映像](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。 

若要訓練您的自訂視覺服務專案：

1.  按一下  **+** 按鈕旁**標記。**

    ![](images/AzureLabs-Lab302b-06.png)

2.  新增**名稱**您想要辨識的物件。 按一下 **儲存**。

    ![](images/AzureLabs-Lab302b-07.png)

3.  您會注意到您**標記**已加入 （您可能需要重新載入您的頁面才會出現）。 如果未選取，請按一下與您的新標籤，核取方塊。

    ![](images/AzureLabs-Lab302b-08.png)

4.  按一下 **新增映像**中頁面的中心。

    ![](images/AzureLabs-Lab302b-09.png)

5.  按一下 **瀏覽本機檔案**，並搜尋，然後選取時，您想要使用最小的所上傳的映像五 （5)。 請記住所有這些映像應該包含您要訓練的物件。

    > [!NOTE]
    >  您可以選取數個映像，一次，若要上傳。

6.  一旦您所見的映像 索引標籤中，選取中適當的標籤**My 標記** 方塊中。

    ![](images/AzureLabs-Lab302b-10.png)

7.  按一下 **將檔案上傳**。 檔案就會開始上傳。 上傳的確認之後，按一下**完成**。

    ![](images/AzureLabs-Lab302b-11.png)

8.  重複相同的程序來建立新**標記**名為**鍵盤**及上傳適當的相片。 請務必**取消核取***滑鼠*當您建立新的標記，因此以顯示*新增映像*視窗。

9.  設定兩個標記之後，按一下**定型**，並且在第一個訓練反覆項目會開始建置。

    ![](images/AzureLabs-Lab302b-12.png)

10. 一旦建立，您會看到兩個按鈕稱為**設成預設值**並**預測 URL**。 按一下 **設成預設值**第一次，然後按一下**預測 URL**。

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > 從這裡開始，提供的端點 URL 設為者為準*反覆項目*已標示為預設值。 因此，如果您稍後建立新*反覆項目*更新為預設值，您不需要變更程式碼。

11. 一旦您按下*預測 URL*，開啟*記事本*，然後複製並貼上**URL**和**預測金鑰**，如此一來，您可以當您需要稍後在程式碼時，請擷取它。

    ![](images/AzureLabs-Lab302b-14.png)

12. 按一下 **齒輪**頂端螢幕的權限。

    ![](images/AzureLabs-Lab302b-15.png)

13. 複製**訓練的索引鍵**將它貼到*記事本*，以供稍後使用。

    ![](images/AzureLabs-Lab302b-16.png)

14. 同時複製您**專案識別碼**，也將它貼至您*記事本*檔案，以供稍後使用。

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟*Unity*然後按一下**新增**。

    ![](images/AzureLabs-Lab302b-17.png)

2.  您現在必須提供 Unity 專案名稱。 插入**AzureCustomVision。** 請確定已設定的專案範本**3D**。 設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![](images/AzureLabs-Lab302b-18.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至 **編輯* > *喜好設定** 從新的視窗中，然後瀏覽至 **外部工具** 。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![](images/AzureLabs-Lab302b-19.png)

4.  接下來，移至**檔案 > 組建設定**，然後選取**通用 Windows 平台**，然後按一下**切換平台**按鈕以套用您的選擇。

    ![](images/AzureLabs-Lab302b-20.png)

5.  當您依然在**檔案 > 組建設定**並確定：

    1.  **裝置為目標**設為**Hololens**

        > 針對擬真耳機，設定**目標裝置**要*任何裝置*。
        
    2.  **建置型別**設為**D3D**
    3.  **SDK**設為**最新安裝**
    4.  **Visual Studio 版本**設為**最新安裝**
    5.  **建置並執行**設為**本機電腦**
    6.  儲存場景，並將它新增至組建。 

        1. 做法是選取**加入開啟的場景**。 儲存視窗會出現。

            ![](images/AzureLabs-Lab302b-21.png)

        2. 建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![](images/AzureLabs-Lab302b-22.png)

        3. 開啟您剛建立**場景**資料夾，然後在*檔案名稱：* 文字欄位中輸入**CustomVisionScene**，然後按一下**儲存**。

            ![](images/AzureLabs-Lab302b-23.png)

            > 請注意，您必須先儲存您的 Unity 場景中*資產*資料夾，因為它們必須是與 Unity 專案相關聯。 建立場景資料夾 （和其他類似的資料夾） 是建構的 Unity 專案的典型方式。
            
    7.  剩餘的設定，*組建設定*，應保持為預設值，現在。

        ![](images/AzureLabs-Lab302b-24.png)

6.  中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。

7. 在此窗格中，少數設定需要驗證：

    1.  在 [**其他設定**] 索引標籤：

        1.  **指令碼執行階段版本**應該 **（.NET 4.6 對等） 的實驗性**，這會觸發程序需要重新啟動編輯器。

        2. **指令碼後端**應該是 **.NET**

        3. **API 相容性層級**應該是 **.NET 4.6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  內**發佈設定**索引標籤之下**功能**，檢查：

        1. **InternetClient**

        2.  **Webcam**

        3. **Microphone**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。

    ![](images/AzureLabs-Lab302b-27.png)

8.  回到*Build Settings* *Unity C\#專案*不再呈現灰色，這旁邊的核取方塊。

9.  關閉 [建立設定] 視窗。

10.  儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>第 4 章-匯入 unity Newtonsoft DLL

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)，它匯入到您的專案做為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 6 章](#chapter-6---create-the-customvisionanalyser-class)。

本課程需要使用**Newtonsoft**程式庫，您可以將做為 DLL，加入您的資產。 封裝包含[可以從此連結下載此文件庫](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)。
若要 Newtonsoft 程式庫匯入專案中，使用 Unity 套件所附的這堂課程。

1.  新增 *.unitypackage* 若要使用的 Unity **資產* > *匯入* *封裝* > *自訂* *封裝** 功能表選項。

2.  在 **匯入 Unity 封裝**方塊會顯示。 請確認所有項目底下 （而且包括）**外掛程式**已選取。

    ![](images/AzureLabs-Lab302b-28.png)

3.  按一下 **匯入**按鈕以新增至您的專案項目。

4.  移至**Newtonsoft**下方的資料夾**外掛程式**中的專案檢視，然後選取*Newtonsoft.Json 外掛程式*。

    ![](images/AzureLabs-Lab302b-29.png)

5.  與*Newtonsoft.Json 外掛程式*選取，請確認**任何平台**是**unchecked**，然後確定**WSAPlayer**也**未核取**，然後按一下**套用**。 這只是要確認已正確設定檔案。

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > 標示這些外掛程式會設定它們僅適用於在 Unity 編輯器中。 有一組不同的專案會匯出從 Unity 後要使用 WSA 資料夾中。

6.  接下來，您必須開啟**WSA**資料夾內**Newtonsoft**資料夾。 您會看到您剛才設定的相同檔案的複本。 選取檔案，並在偵測器中，確定該
    -   **任何平台**是**unchecked** 
    -   **只有** **WSAPlayer**是**檢查**
    -   **不會處理**是**檢查**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>第 5 章-觀景窗設定

1.  在階層窗格中，選取*Main Camera*。

2.  選取之後，您將能夠看到所有的元件*Main Camera*中*Inspector 面板*。

    1.  *相機*必須命名為物件**Main Camera** （請注意拼字 ！）

    2.  Main Camera**標記**必須設為**MainCamera** （請注意拼字 ！）

    3.  請確定**轉換的位置**設定為**0，0，0**

    4.  設定**清除旗標**要**單色**（略過此的沈浸式耳機）。

    5.  設定**背景**觀景窗的色彩元件至**黑色，0 的 Alpha (十六進位的程式碼: #00000000)** （略過此的沈浸式耳機）。

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>章節 6-建立 CustomVisionAnalyser 類別。

此時，您已準備好開始撰寫一些程式碼。

將開頭*CustomVisionAnalyser*類別。

> [!NOTE]
> 呼叫**Custom Vision Service**中顯示的程式碼進行以下都會使用**自訂視覺 REST API**。 透過使用這種情況，您會看到如何實作及使用此 api （適用於了解如何自行實作類似）。 請注意，Microsoft 提供了**Custom Vision Service SDK** ，也可用來對服務進行呼叫。 如需詳細資訊，請造訪[Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)文章。

這個類別會負責：

-   正在載入最新的映像擷取成位元組陣列。

-   將位元組陣列傳送至您的 Azure *Custom Vision Service*執行個體進行分析。

-   接收回應為 JSON 字串。

-   還原序列化回應，並傳遞產生*預測*要*SceneOrganiser*類別，它會負責顯示回應的方式。

若要建立此類別：

1.  以滑鼠右鍵按一下*Assets 資料夾*位於 *[專案] 面板*，然後按一下**建立 > 資料夾**。 呼叫資料夾**指令碼**。

    ![](images/AzureLabs-Lab302b-33.png)

2.  按兩下剛才建立開啟的資料夾。

3.  在資料夾中，以滑鼠右鍵按一下，然後按一下  **Create** > **C\#指令碼**。 指令碼命名*CustomVisionAnalyser*。

4.  按兩下新*CustomVisionAnalyser*指令碼，以開啟它**Visual Studio**。

5.  更新頂端的 您的檔案，以符合下列命名空間：

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  在  *CustomVisionAnalyser*類別中，新增下列變數：

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 請確定您插入您**預測金鑰**成**predictionKey**變數和您**預測端點**到**predictionEndpoint**變數。 您可以複製這些*記事本*稍早在本課程。

7.  程式碼**Awake()** 現在必須初始化執行個體變數新增：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  刪除方法**start （)** 並**update （)**。

9.  接下來，新增 協同程式 (具有靜態**GetImageAsByteArray()** 下方的方法)，這將會取得所擷取的映像的分析結果*ImageCapture*類別。

    > [!NOTE]
    > 在  **AnalyseImageCapture**協同程式，來呼叫*SceneOrganiser*您即將建立的類別。 因此，**保留的線條標記為註解現在**。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。

## <a name="chapter-7---create-the-customvisionobjects-class"></a>第 7-建立 CustomVisionObjects 類別

您將建立的類別現在是*CustomVisionObjects*類別。

此指令碼包含用來序列化和還原序列化的呼叫對其他類別的物件數目*Custom Vision Service*。

> [!WARNING]
> 很重要，您需要注意 Custom Vision Service 所提供的是，做為端點的下列 JSON 結構已設定來處理[*自訂辨識預測 v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)。 如果您有不同的版本，您可能需要更新下列結構。

若要建立此類別：

1.  以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。 呼叫指令碼*CustomVisionObjects*。

2.  按兩下新**CustomVisionObjects**指令碼，以開啟它**Visual Studio**。

3.  檔案開頭處新增下列命名空間：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  刪除**start （)** 並**update （)** 內的方法*CustomVisionObjects*類別; 此類別現在應為空白。

5.  新增下列類別**外** *CustomVisionObjects*類別。 這些物件由*Newtonsoft*序列化和還原序列化回應資料的程式庫：

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>第 8-建立 VoiceRecognizer 類別

這個類別會辨識來自使用者的語音輸入。

若要建立此類別：

1.  以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。 呼叫指令碼*VoiceRecognizer*。

2.  按兩下新**VoiceRecognizer**指令碼，以開啟它**Visual Studio**。

3.  新增下列命名空間的上述*VoiceRecognizer*類別：

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  然後新增下列變數內*VoiceRecognizer*類別，上述*start （)* 方法：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  新增**Awake()** 並**start （)** 方法，後者會設定使用者*關鍵字*建立關聯之影像標記時才能辨識：

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  刪除**update （)** 方法。

7.  新增下列處理常式，每當辨識語音輸入，就會呼叫：

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。

> [!NOTE]
> 不要擔心可能會顯示有錯誤，當您將會提供進一步的類別，以修正這些程式碼。

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>第 9-建立 CustomVisionTrainer 類別

這個類別會鏈結一連串 web 呼叫來定型*Custom Vision Service*。 每個呼叫將會說明在上面的程式碼的詳細資料。

若要建立此類別：

1.  以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。 呼叫指令碼*CustomVisionTrainer*。

2.  按兩下新*CustomVisionTrainer*指令碼，以開啟它**Visual Studio**。

3.  新增下列命名空間的上述*CustomVisionTrainer*類別：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  然後新增下列變數內*CustomVisionTrainer*類別，上述**start （)** 方法。 

    > [!NOTE]
    > 此處所使用的訓練 URL 中提供*自訂辨識訓練 1.2*文件，並具有的結構： https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > 如需詳細資訊，請瀏覽[*自訂辨識訓練 API 的 v1.2 參考*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。

    > [!WARNING]
    > 很重要，您需要記下 Custom Vision Service 提供您的訓練模式，以使用 JSON 結構的端點 (內**CustomVisionObjects**類別) 來使用已設定[ *Custom Vision 訓練 v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。 如果您有不同的版本，您可能需要更新*物件*結構。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > 請務必將您**服務金鑰**（訓練） 索引鍵值並**專案識別碼**值，其中您記下先前; 這些都是值您[收集從先前的課程 （入口網站第 2 章步驟 10 及更新版本）](#chapter-2---training-your-custom-vision-oroject)。

5.  新增下列**start （)** 並**Awake()** 方法。 這些方法上初始化呼叫，並包含呼叫，以設定 UI:

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  刪除**update （)** 方法。 這個類別就不需要它。

7.  新增**RequestTagSelection()** 方法。 這個方法是已擷取並儲存在裝置影像時要呼叫的第一個，且現在已提交給*Custom Vision Service*、 將它定型。 這個方法會顯示，在 UI 中，一組使用者可以用來標記映像已擷取之關鍵字的訓練。 它也會提醒*VoiceRecognizer*類別，以開始接聽使用者的語音輸入。

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  新增**VerifyTag()** 方法。 這個方法會接收語音輸入辨識**VoiceRecognizer**類別並驗證其有效性，然後開始在定型程序。

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  新增**SubmitImageForTraining()** 方法。 此方法會開始 Custom Vision Service 定型程序。 第一個步驟是擷取**標記識別項**從使用者的已驗證的語音輸入相關聯的服務。 **標記識別項**會接著映像一起上傳。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. 新增**TrainCustomVisionProject()** 方法。 一旦已提交並標記映像，就會呼叫這個方法。 它會建立新的反覆項目將定型與提交給服務，再加上的映像的所有先前映像剛才上傳。 完成訓練之後，這個方法會呼叫方法來設定新建立**反覆項目**作為**預設**，如此一來，您要用於分析的端點是最新定型的反覆項目。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. 新增**SetDefaultIteration()** 方法。 這個方法會設定為先前建立及定型反覆項目*預設*。 完成時，這個方法就必須刪除現有的服務中的上一個反覆項目。 撰寫本課程的同時，沒有限制的最大十 （10） 反覆項目允許在服務中同時存在。

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. 新增**DeletePreviousIteration()** 方法。 這個方法會尋找並刪除先前的非預設反覆項目：

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. 要加入這個類別中的最後一個方法是**GetImageAsByteArray()** 方法，用於 web 呼叫，以轉換成位元組陣列所擷取的影像。

    ```csharp
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

14. 請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。

## <a name="chapter-10---create-the-sceneorganiser-class"></a>第 10-建立 SceneOrganiser 類別

這個類別將會：

-   建立**游標**来附加至 Main Camera 物件。

-   建立**標籤**服務能辨識的真實世界物件時，會出現的物件。

-   設定 Main Camera cvcollectioncmd 附加至適當的元件。

-   即使處於**分析模式**、 繁衍 （spawn） 在執行階段，相對於位置的 Main Camera 中，適當的世界空間中的標籤，並顯示 Custom Vision Service 從收到的資料。

-   即使處於**定型模式**，繁衍 （spawn) 將會顯示在定型程序的不同階段的 UI。

若要建立此類別：

1.  以滑鼠右鍵按一下**指令碼**資料夾，然後按一下**建立** > **C\#指令碼**。 指令碼命名*SceneOrganiser*。

2.  按兩下新*SceneOrganiser*指令碼，以開啟它**Visual Studio**。

3.  您只需要一個命名空間，移除上述的其他*SceneOrganiser*類別：

    ```csharp
    using UnityEngine;
    ```

4.  然後新增下列變數內*SceneOrganiser*類別，上述**start （)** 方法：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  刪除**start （)** 並**update （)** 方法。

6.  權限底下的變數中，加入**Awake()** 方法，它會初始化類別，並設定場景。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  現在加入**CreateCameraCursor()** 方法來建立，並將 Main Camera 資料指標，而**CreateLabel()** 方法會建立**分析標籤**物件.

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. 新增**SetCameraStatus()** 方法，它會處理要傳送給文字網狀結構提供觀景窗的狀態。

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. 新增**PlaceAnalysisLabel()** 並**SetTagsToLastLabel()** 方法，它會繁衍 （spawn），顯示場景的 Custom Vision Service 中的資料。

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. 最後，新增**CreateTrainingUI()** 方法，它會繁衍 （spawn） 的應用程式是在定型模式時，顯示定型程序的多個階段的 UI。 這個方法也將已經建立相機狀態物件。

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. 請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。

> [!IMPORTANT]
> 在繼續之前，開啟**CustomVisionAnalyser**類別，會在**AnalyseLastImageCaptured()** 方法*取消註解*下列幾行：
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>第 11-建立 ImageCapture 類別

下一步要建立的類別是*ImageCapture*類別。

這個類別會負責：

-   擷取映像使用 HoloLens 相機，並將它儲存在*應用程式*資料夾。

-   處理來自使用者的點選手勢。

-   維護*Enum*值，決定是否有應用程式會以*Analysis*模式或*訓練*模式。

若要建立此類別：

1.  移至**指令碼**您先前建立的資料夾。

2.  在資料夾中，以滑鼠右鍵按一下，然後按一下 **建立 > C\#指令碼**。 指令碼命名*ImageCapture*。

3.  按兩下新**ImageCapture**指令碼，以開啟它**Visual Studio**。

4.  以下列內容取代頂端的 檔案命名空間：

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然後新增下列變數內*ImageCapture*類別，上述**start （)** 方法：

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

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

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  實作會在點選手勢時呼叫的處理常式。

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > 在  *Analysis*模式中， **TapHandler**方法會作為交換器，來啟動或停止相片擷取迴圈。
    >
    > 在 *訓練*模式中，它將來自相機的映像的擷取。
    >
    > 當資料指標為綠色時，表示相機可採取的映像。
    >
    > 當資料指標為紅色時，表示相機正在忙碌中。

8.  新增應用程式用來啟動映像擷取程序，並儲存映像的方法。

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  新增處理常式會被呼叫時已擷取相片並時準備好進行分析。 結果會傳遞至*CustomVisionAnalyser*或*CustomVisionTrainer*根據哪一個模式上設定的程式碼。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。

11. 現在，所有指令碼完成時，請回到在 Unity 編輯器中，然後按一下並拖曳**SceneOrganiser**從類別**指令碼**資料夾**Main Camera**物件中*階層面板*。

## <a name="chapter-12---before-building"></a>第 12 章-建置前

若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 HoloLens。

這麼做之前，請確認：

- 中所述的所有設定[第 2 章](#chapter-2---training-your-custom-vision-project)都已正確設定。

- 中的所有欄位**Main Camera**，偵測器 面板中，適當地指派。

- 指令碼**SceneOrganiser**附加至**Main Camera**物件。

- 請確定您插入您**預測金鑰**成**predictionKey**變數。

- 您已插入您**預測端點**成**predictionEndpoint**變數。

- 您已插入您**訓練的索引鍵**成**trainingKey**的變數*CustomVisionTrainer*類別。

- 您已插入您**專案識別碼**成**projectId**的變數*CustomVisionTrainer*類別。

## <a name="chapter-13---build-and-sideload-your-application"></a>第 13 章-建置和側載您的應用程式

若要開始*建置*程序：

1.  移至**檔案 > 組建設定**。

2.  刻度**Unity C\#專案**。

3.  按一下 [建置] 。 將會啟動 unity**檔案總管**視窗中，您要建立，然後選取 建置到應用程式的資料夾。 現在，建立該資料夾並將它命名**應用程式**。 然後使用**應用程式**上按一下 選取資料夾**選取資料夾**。

4.  Unity 會開始建置您的專案**應用程式**資料夾。

5.  一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。

若要部署 HoloLens 上：

1.  您將需要您 HoloLens IP 位址 （適用於遠端部署），並以確保您 HoloLens 處於**開發人員模式**。 請這樣做：

    1.  儘管穿著您 HoloLens，開啟**設定**。

    2.  移至**網路和網際網路** > **Wi-fi** > **進階選項**

    3.  附註**IPv4**位址。

    4.  接下來，瀏覽回到**設定**，然後**更新與安全性** > **適用於開發人員**

    5.  設定**上的開發人員模式**。

2.  瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。

3.  在 *方案組態*選取**偵錯**。

4.  在 *的方案平台*，選取**x86，遠端機器**。 系統會提示您插入**IP 位址**的遠端裝置 (HoloLens，在此情況下，記下)。

    ![](images/AzureLabs-Lab302b-34.png)

5. 移至**建置**功能表，然後按一下 **部署方案**側載您 HoloLens 應用程式。

6. 您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！

> [!NOTE]
> 若要將部署到擬真耳機，設定**的方案平台**來*本機電腦*，並設定**組態**至*偵錯*，使用*x86*作為**平台**。 然後部署到本機電腦，使用**建置**功能表項目，選取*部署方案*。 

## <a name="to-use-the-application"></a>若要使用應用程式：

若要切換之間的應用程式功能*訓練*模式並*預測*模式，您需要更新**AppMode**變數，位於**Awake()** 方法將會位於*ImageCapture*類別。

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
或
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

在 *訓練*模式︰

- 看看**滑鼠**或是**鍵盤**並用**點選手勢**。

- 接下來，文字會出現要求您提供的標記。

- 顯示**滑鼠**或是**鍵盤**。


在 *預測*模式︰

- 查看物件，並使用**點選手勢**。

- 文字會出現提供具有最高的機率 （這標準化） 偵測到的物件。

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>第 14-評估，並改善您的自訂視覺模型

若要讓您的服務更精確，您必須繼續用於預測模型定型。 這透過使用新的應用程式同時使用達成*訓練*並*預測*模式，後者需要您造訪入口網站中，也就是在這一章中涵蓋的項目。 要準備多次重新瀏覽您的入口網站，以持續改善您的模型。

1. 同樣地，前往您的 Azure 自訂視覺入口網站，然後當您在專案中，選取*預測*（從頂端中央的頁面） 索引標籤：

    ![](images/AzureLabs-Lab302b-35.png)

2. 您會看到您的應用程式正在執行的同時傳送到您的服務的所有映像。 如果您停留映像時，它們會將您提供該映像所做的預測：

    ![](images/AzureLabs-Lab302b-36.png)

3. 選取您的映像，以開啟它的其中一個。 一旦開啟，您會看到右邊，該映像所做的預測。 如果您預測正確的而您想要將此映像新增至您的服務定型模型，請按一下*My 標記*輸入方塊，然後選取您想要建立關聯的標記。 當您完成時，請按一下*儲存並關閉*按鈕右下方，並繼續執行下一個映像。

    ![](images/AzureLabs-Lab302b-37.png)

4. 一旦您回到映像的方格中，您會注意到您已新增標記 （並儲存），映像將會移除。 如果您發現您認為不需要您標記的項目，其中任何映像，您可以刪除它們，按一下該映像 （可以執行這項操作的數個映像） 上的刻度，然後按一下*刪除*方格頁面右上角。 接下來，快顯功能表，您可以按一下其中一個*Yes，delete*或*No*，以確認刪除，或取消，分別。 

    ![](images/AzureLabs-Lab302b-38.png)

5. 當您準備好繼續進行，請按一下綠色*定型*右上角的按鈕。 這些映像您現在有提供 （這就變得更精確），都會加以定型您的服務模型。 訓練完成之後，請務必按一下 *設成預設值*同樣地，按鈕，讓您*預測 URL*會繼續使用服務的最新的反覆項目。

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>您已完成的自訂視覺 API 應用程式

恭喜，您建置利用 Azure 自訂視覺 API，以辨識真實世界物件、 訓練服務模型，並顯示信心的功能，曾 mixed 的 reality 應用程式。

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

訓練您**Custom Vision Service**辨識更多的物件。

### <a name="exercise-2"></a>練習 2

展開您已了解的方法，完成下列練習：

當辨識項物件時，請播放的音效。

### <a name="exercise-3"></a>練習 3

使用 API，來重新訓練您的服務，與正在分析您的應用程式相同的映像，因此若要讓服務更精確 （執行預測和同時訓練）。
