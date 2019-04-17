---
title: MR 和 Azure 302-電腦視覺
description: 完成這個課程來了解如何辨識提供的映像，在混合的實境應用程式中使用 Azure 的 Computer Vision 內的視覺化內容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 電腦視覺、 hololens、 沉浸式 vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591196"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR 和 Azure 302:電腦視覺

在此課程中，您將學習如何辨識提供的映像 」 中的視覺內容混合的實境應用程式中使用的 Azure 電腦視覺功能。

辨識結果將顯示為具描述性的標籤。 您可以使用而不需要這項服務，來定型機器學習模型。 如果您的實作需要訓練機器學習模型，請參閱[MR 和 Azure 302b](mr-azure-302b.md)。

![實驗室結果](images/AzureLabs-Lab2-000.png)

Microsoft Computer Vision 是一份所有從雲端中使用進階的演算法，用以與映像處理和分析 （附帶傳回的資訊），提供開發人員 Api。 開發人員上傳映像或映像的 URL，以及 Microsoft 電腦視覺 API 演算法會分析視覺化內容中，根據選擇的使用者，則可以傳回資訊，請輸入包括，識別的型別和品質的影像，偵測人臉 （傳回其座標），並加上標籤、 或分類映像。 如需詳細資訊，請瀏覽[Azure Computer Vision API 頁面](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。

完成本課程之後，您會有混合的實境 HoloLens 應用程式，可以執行下列作業：

1.  HoloLens 相機會使用點選手勢，來擷取映像。
2.  映像將會傳送至 Azure 的電腦視覺 API 服務中。 
3.  簡單的 UI 群組放置在 Unity 場景中會列出可辨識的物件。

在您的應用程式，則您對於如何將整合結果進行設計。 本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。 它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 302:電腦視覺</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然這堂課程主要著重於 HoloLens，您也可以套用您在此課程 Windows Mixed Reality 沈浸式 (VR) 耳機來了解。 因為沈浸式 (VR) 耳機並沒有可存取的相機，您必須連線到您的 PC 外部相機。 當您遵循本課程中，您會看到 備忘稿上用來支援沈浸式 (VR) 耳機時，您可能需要的任何變更。

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程專為具有基礎經驗的 Unity 開發人員和C#。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。 中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊會完全符合您會發現在較新的軟體與以下所列內容.

我們建議下列的硬體和軟體這堂課程：

- 開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發
- [Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式
- 相機連接到您的電腦 （開發沈浸式耳機）
- Azure 的安裝程式和電腦視覺 API 擷取的網際網路存取

## <a name="before-you-start"></a>開始之前

1.  若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。
2.  設定並測試您的 HoloLens。 如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。 

校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。

如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。

## <a name="chapter-1--the-azure-portal"></a>第 1 章-Azure 入口網站

若要使用*Computer Vision API*服務在 Azure 中，您必須設定您的應用程式提供服務的執行個體。

1.  首先，登入[Azure 入口網站](https://portal.azure.com)。 

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**新增**在左上角，，然後搜尋*Computer Vision API*，然後按一下**Enter**。

    ![在 Azure 中建立新的資源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 單字**的新**可能已取代為**建立資源**，較新的入口網站中。
 
3.  新的頁面將提供的描述*Computer Vision API*服務。 在左下方的這個頁面上，選取**建立**按鈕，以建立與此服務的關聯。

    ![關於電腦視覺 api 服務](images/AzureLabs-Lab2-01.png)
 
4.  一旦您按下**建立**:

    1. 插入您想要**名稱**此服務執行個體。
    2. 選取 **訂用帳戶**。
    3. 選取 **定價層**適合您，如果這是第一個時間來建立*Computer Vision API*服務，免費層 （名為 F0） 應該是您可以使用。
    4. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。 

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. （如果您要建立新的資源群組），請判斷您的資源群組的位置。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。

    6. 您也必須確認您已了解這些條款和條件套用到此服務。
    7. 按一下 [建立]。

        ![服務建立資訊](images/AzureLabs-Lab2-02.png)

5.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。
6.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![請參閱您的新服務的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  按一下通知，以探索新的服務執行個體。 

    ![選取 [移至資源] 按鈕。](images/AzureLabs-Lab2-04.png)
 
8. 按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 您會前往新的 Computer Vision API 服務執行個體。 

    ![新的 Computer Vision API 服務](images/AzureLabs-Lab2-05.png)
 
9.  在本教學課程中，您的應用程式將需要對您的服務，透過使用您的服務訂用帳戶金鑰進行呼叫。
10. 從*快速入門*頁面上的您*Computer Vision API*服務，請瀏覽至第一個步驟中，*取得您的金鑰*，然後按一下**金鑰**(您也可以達到這按一下藍色超連結索引鍵，位於服務導覽功能表中，以索引鍵的圖示表示）。 這將顯示您的服務*金鑰*。
11. 需要顯示的索引鍵，其中的複本，因為您將需要此更新版本中您的專案。 

12. 請返回*快速入門*頁面，然後從該處擷取您的端點。 您可能會不同，依據您的地區 (這如果是，您必須對您的程式碼進行變更時，也將更新版本)。 需要此端點，供後續使用的複本：

    ![新的 Computer Vision API 服務](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > 您可以檢查不同的端點為何[此處](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。 

## <a name="chapter-2--set-up-the-unity-project"></a>第 2 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟*Unity*然後按一下**新增**。 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab2-06.png)

2.  您現在必須提供 Unity 專案名稱。 插入**MR_ComputerVision**。 請確定專案類型設定為**3D**。 設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![提供新的 Unity 專案的詳細資料。](images/AzureLabs-Lab2-07.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯 > 偏好**，然後在新視窗中，瀏覽**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![更新指令碼編輯器喜好設定。](images/AzureLabs-Lab2-08.png)

4.  接下來，移至**檔案 > 組建設定**，然後選取**通用 Windows 平台**，然後按一下**切換平台**按鈕以套用您的選擇。

    ![建置設定 視窗中，切換至 UWP 的平台。](images/AzureLabs-Lab2-10.png)

5.  當您依然在**檔案 > 組建設定**並確定：

    1. **裝置為目標**設為**HoloLens**

        > 針對擬真耳機，設定**目標裝置**要*任何裝置*。

    2. **建置型別**設為**D3D**
    3. **SDK**設為**最新安裝**
    4. **Visual Studio 版本**設為**最新安裝**
    5. **建置並執行**設為**本機電腦**
    6. 儲存場景，並將它新增至組建。

        1. 做法是選取**加入開啟的場景**。 儲存視窗會出現。
        
            ![按一下 新增開啟場景按鈕](images/AzureLabs-Lab2-11.png)

        2. 建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![建立新的指令碼資料夾](images/AzureLabs-Lab2-12.png)

        3. 開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中輸入**MR_ComputerVisionScene**，然後按一下**儲存**.

            ![指定新的場景的名稱。](images/AzureLabs-Lab2-13.png)

            > 請注意，您必須先儲存您的 Unity 場景中*資產*資料夾，因為它們必須是與 Unity 專案相關聯。 建立場景資料夾 （和其他類似的資料夾） 是建構的 Unity 專案的典型方式。

    7. 剩餘的設定，*組建設定*，應保持為預設值，現在。

6. 中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。 

    ![開啟播放程式設定。](images/AzureLabs-Lab2-14.png)

7. 在此窗格中，少數設定需要驗證：

    1. 在 [**其他設定**] 索引標籤：

        1. **指令碼執行階段版本**應該**穩定**（.NET 3.5 對等）。
        2. **指令碼後端**應該是 **.NET**
        3. **API 相容性層級**應該是 **.NET 4.6**

            ![更新其他設定。](images/AzureLabs-Lab2-15.png)
      
    2. 內**發佈設定**索引標籤之下**功能**，檢查：

        1. **InternetClient**
        2. **Webcam**

            ![正在更新發行的設定。](images/AzureLabs-Lab2-16.png)

    3. 在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。

        ![更新 R 設定。](images/AzureLabs-Lab2-17.png)

8.  回到*Build Settings* _Unity C#_ 專案不再呈現灰色，這旁邊的核取方塊。 
9.  關閉 [建立設定] 視窗。
10. 儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。

## <a name="chapter-3--main-camera-setup"></a>第 3 章-Main Camera 安裝程式

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)，它匯入到您的專案做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 5 章](#chapter-5--create-the-resultslabel-class)。

1.  在 *階層面板*，選取**Main Camera**。 
2.  選取之後，您將能夠看到所有的元件**Main Camera**中*Inspector 面板*。

    1. **相機物件**必須命名為**Main Camera** （請注意拼字 ！）
    2. Main Camera**標記**必須設為**MainCamera** （請注意拼字 ！）
    3. 請確定**轉換的位置**設定為**0，0，0**
    4. 設定**清除旗標**要**單色**（略過此的沈浸式耳機）。
    5. 設定**背景**相機元件以色彩**黑色，0 的 Alpha (十六進位的程式碼: #00000000)** （略過此的沈浸式耳機）。

        ![更新相機元件。](images/AzureLabs-Lab2-18.png)
 
3.  接下來，您必須建立簡單的 「 游標 」 物件附加至**Main Camera**，這會協助您放置影像分析輸出應用程式執行時。 這個資料指標將會決定攝影機焦點的中心點。

若要建立資料指標：

1.  在 *階層面板*，以滑鼠右鍵按一下**Main Camera**。 底下**3D 物件**，按一下**球體**。

    ![選取游標物件。](images/AzureLabs-Lab2-19.png)
 
2.  重新命名**球體**要**游標**（按兩下 游標物件或按 'F2' 的 鍵盤 按鈕選取的物件），並確定它位於做為子系**Main Camera**.

3.  在 *階層面板*上, 按一下滑鼠左鍵**游標**。 選取游標，調整中的下列變數*Inspector 面板*:

    1. 設定*轉換位置*到**0，0，5**
    2. 設定*擴展*到**0.02、 0.02、 0.02**

        ![更新的轉換位置和小數位數。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>第 4 章-設定標籤系統

一旦您有與 HoloLens 的攝影機擷取映像，該映像將會傳送至您*Azure Computer Vision API*進行分析的服務執行個體。 

該分析的結果會是一份可辨識的物件稱為**標記**。 

您會使用標籤 （世界空間中 3D 文字） 格式來顯示這些標記拍攝相片的位置。

下列步驟將示範如何設定**標籤**物件。

1.  以滑鼠右鍵按一下階層面板的 （位置不會影響在此時） 下的任何地方**3D 物件**，新增**3D 文字**。 命名**LabelText**。

    ![建立 3D 文字物件。](images/AzureLabs-Lab2-21.png)
 
2.  在 *階層面板*，在上按一下滑鼠左鍵**LabelText**。 具有**LabelText**選取，調整中的下列變數*Inspector 面板*:

    1. 設定**位置**到**0,0,0**
    2. 設定**擴展**到**0.01、 0.01、 0.01**
    3. 在元件**文字 Mesh**:
    4. 取代內的所有文字**文字**，使用 [...]        
    5. 設定**錨點**到**Na Střed**
    6. 設定**對齊**到**Center**
    7. 設定**定位點大小**到**4**
    8. 設定**字型大小**到**50**
    9. 設定**色彩**到 **#FFFFFFFF**

    ![文字元件](images/AzureLabs-Lab2-21-5.png)

3.  拖曳**LabelText**從*階層面板*，到*Assets 資料夾*內中*專案面板*。 這會讓**LabelText** Prefab，因此它可以在程式碼中具現化。

    ![建立 prefab 的 LabelText 物件。](images/AzureLabs-Lab2-22.png)
 
4.  您應該刪除**LabelText**從*階層面板*，以便將不會顯示開啟場景中。 它現在成為 prefab，您將呼叫個別的執行個體從 [資產] 資料夾，但沒有需要保留在場景中。 
5.  中的最終物件結構*階層面板*應該類似下面的影像中所示：

    ![在 [階層] 面板的最終結構。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>第 5 章-建立 ResultsLabel 類別

您必須建立第一個指令碼*ResultsLabel*類別，它會負責下列： 

- 在適當的世界空間中，相對於觀景窗位置建立標籤。
- 顯示從映像擺脫標記。

若要建立此類別： 

1.  以滑鼠右鍵按一下*專案 面板*，然後**建立 > 資料夾**。 將資料夾命名**指令碼**。 

    ![建立指令碼 資料夾。](images/AzureLabs-Lab2-24.png)

2.  具有**指令碼**資料夾建立，連按兩下以開啟該項目。 然後在該資料夾，然後按一下滑鼠右鍵，並選取**建立 >** 再**C#指令碼**。 指令碼命名*ResultsLabel*。 

3.  按兩下新*ResultsLabel*指令碼，以開啟它**Visual Studio**。

4.  類別內插入下列程式碼*ResultsLabel*類別：

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。
7.  回到*Unity Editor*，按一下並拖曳*ResultsLabel*類別**指令碼**資料夾**Main Camera** 中的物件*階層面板*。
8.  按一下  **Main Camera**並查看*Inspector 面板*。

您會注意到，從指令碼，您剛拖曳到相機，有兩個欄位：**資料指標**並**加上標籤 Prefab**。

9.  拖曳所呼叫的物件**游標**從*階層面板*命名的插槽**游標**，如下圖所示。
10. 拖曳物件呼叫**LabelText**從*Assets 資料夾*中*專案面板*至名為位置**標籤 Prefab**，如下所示下圖。 

    ![在 Unity 內參考為目標集。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>第 6 章-建立 ImageCapture 類別

下一步要建立的類別是*ImageCapture*類別。 這個類別會負責：

-   擷取映像使用 HoloLens 相機，並將其儲存在應用程式資料夾中。
-   擷取使用者的點選手勢。

若要建立此類別： 

1.  移至**指令碼**您先前建立的資料夾。 
2.  在資料夾中，以滑鼠右鍵按一下**建立 >C#指令碼**。 呼叫指令碼*ImageCapture*。 
3.  按兩下新*ImageCapture*指令碼，以開啟它**Visual Studio**。
4.  檔案開頭處新增下列命名空間：

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  然後新增下列變數內*ImageCapture*類別，上述*start （)* 方法：

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount**變數會儲存擷取自使用者的點選手勢的數目。 這個數字是用來擷取的映像命名。

6.  程式碼*Awake()* 並*start （)* 方法現在需要加入。 在類別初始化時，這些將會呼叫：

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  實作會在點選手勢時呼叫的處理常式。 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
*TapHandler()* 方法遞增擷取使用者的分接器數目，並且使用目前的資料指標位置，決定在何處放置新的標籤。

這個方法會接著呼叫*ExecuteImageCaptureAndAnalysis()* 方法開始此應用程式的核心功能。

8.  一旦已擷取並儲存映像，就會呼叫下列處理常式。 如果處理程序成功時，結果會傳遞至*VisionManager* （即您尚未建立） 進行分析。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  然後新增應用程式用來啟動映像擷取程序，並儲存映像的方法。

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> 此時您會注意到錯誤不會出現在*Unity 編輯器主控台面板*。 這是因為程式碼參考*VisionManager*您會建立下一步 一章中的類別。

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>第 7 章 – 對 Azure 和影像分析

您需要建立的最後一個指令碼*VisionManager*類別。 

這個類別會負責：

-   正在載入最新的映像擷取成位元組陣列。
-   傳送的位元組陣列，要您*Azure Computer Vision API*進行分析的服務執行個體。
-   接收回應為 JSON 字串。
-   還原序列化回應，並傳遞將產生的標記*ResultsLabel*類別。
 
若要建立此類別：

1.  按兩下**指令碼**資料夾，將它開啟。 
2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。 指令碼命名*VisionManager*。 
3.  按兩下新的指令碼，以使用 Visual Studio 中開啟它。
4.  更新命名空間相同，如下所示，在頂端*VisionManager*類別：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  在您的指令碼頂端*內* *VisionManager*類別 (以上*start （)* 方法)，您現在必須建立兩個*類別*，將代表從 Azure 還原序列化的 JSON 回應：

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > *TagData*並*AnalysedObject*類別必須能夠 *[System.Serializable]* 能夠還原序列化，使用 Unity 宣告前面加上的屬性程式庫。

6.  在 VisionManager 類別中，您應該加入下列變數：

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > 請確定您插入您**驗證金鑰**成**authorizationKey**變數。 您將已記下您**驗證金鑰**在此課程中，開頭[第 1 章](#chapter-1--the-azure-portal)。

    > [!WARNING] 
    > **VisionAnalysisEndpoint**變數可能會在此範例中所指定的不同。 **西-我們**嚴格參考為美國西部區域建立的服務執行個體。 更新與您[端點 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); 以下是這方面的一些範例看起來會像：
    > - 西歐： `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 東南亞： `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 澳洲東部： `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Awake 現在需要新增的程式碼。 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  接下來，新增 協同程式 （使用靜態的資料流方法下方），它會取得所擷取的映像的分析結果*ImageCapture*類別。 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。
10. 傳回在 Unity 編輯器中，按一下並拖曳*VisionManager*並*ImageCapture*類別**指令碼**資料夾**Main Camera**物件中*階層面板*。 

## <a name="chapter-8--before-building"></a>第 8 章-建置前

若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 HoloLens。
這麼做之前，請確認：

-   中所述的所有設定[第 2 章](#chapter-2--set-up-the-unity-project)都已正確設定。 
-   所有指令碼會附加至**Main Camera**物件。 
-   中的所有欄位*Main 攝影機偵測器 面板*皆正確。
-   請確定您插入您**驗證金鑰**成**authorizationKey**變數。
-   請確定您也必須檢查您的端點您*VisionManager*指令碼，以及它與*您*區域 (此文件會使用*西-我們*預設)。

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>第 9 – 建置的 UWP 方案和側載應用程式
此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。

1.  瀏覽至*組建設定* - **檔案 > 組建設定...**
2.  從*Build Settings*  視窗中，按一下**建置**。

    ![從 Unity 建置應用程式](images/AzureLabs-Lab2-26.png)

3.  如果您尚未，勾選**UnityC#專案**。
4.  按一下 [建置] 。 將會啟動 unity*檔案總管*視窗中，您要建立，然後選取 建置到應用程式的資料夾。 現在，建立該資料夾並將它命名*應用程式*。 然後使用*應用程式*資料夾選取，請按下**選取資料夾**。 
5.  Unity 會開始建置您的專案*應用程式*資料夾。 
6.  一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟*檔案總管*視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。

## <a name="chapter-10--deploy-to-hololens"></a>第 10 – 將部署到 HoloLens

若要部署 HoloLens 上：

1.  您將需要您 HoloLens IP 位址 （適用於遠端部署），並以確保您 HoloLens 處於**開發人員模式**。 請這樣做：

    1. 儘管穿著您 HoloLens，開啟**設定**。
    2. 移至**網路和網際網路 > Wi-fi > 進階選項**
    3. 附註**IPv4**位址。
    4. 接下來，瀏覽回到**設定**，然後**更新與安全性 > 適用於開發人員** 
    5. 設定開發人員模式。

2.  瀏覽至新的 Unity 組建 (*應用程式*資料夾)，並開啟方案檔*Visual Studio*。
3.  在 方案組態選取**偵錯**。
4.  在 方案平台上，選取**x86**，**遠端機器**。 

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab2-27.png)
 
5.  移至**建置 功能表**，然後按一下**部署方案**，側載您 HoloLens 應用程式。
6.  您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！

> [!NOTE]
> 若要將部署到擬真耳機，設定**的方案平台**來*本機電腦*，並設定**組態**至*偵錯*，使用*x86*作為**平台**。 然後部署到本機電腦，使用**建置 功能表**，並選取*部署方案*。 

## <a name="your-finished-computer-vision-api-application"></a>您已完成的 Computer Vision API 應用程式

恭喜，您建置利用 Azure 的 Computer Vision API，來辨識真實世界物件，並顯示信心的功能，曾 mixed 的 reality 應用程式。

![實驗室結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

就如同您已使用*標記*參數 (內，證明*端點*用於*VisionManager*)，擴充應用程式，來偵測其他的資訊，看看您可以存取哪些其他參數[此處](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。

### <a name="exercise-2"></a>練習 2

顯示傳回 Azure 中的資料，以更白話且容易閱讀的方式，或許隱藏的數字。 如同 bot 可能說給使用者。
