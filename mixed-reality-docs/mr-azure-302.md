---
title: MR 和 Azure 302-電腦視覺
description: 完成本課程, 以瞭解如何在混合現實應用程式中使用 Azure 電腦視覺, 以在所提供的影像中辨識視覺內容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合現實, 學術, unity, 教學課程, api, 電腦視覺, hololens, 沉浸, vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63552031"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。  因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊, 以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時, 使用這些教學課程的連結進行更新。

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR 和 Azure 302:電腦視覺

在此課程中, 您將瞭解如何使用混合現實應用程式中的 Azure 電腦視覺功能, 辨識所提供影像中的視覺內容。

辨識結果會顯示為描述性標記。 您可以使用此服務, 而不需要訓練機器學習服務模型。 如果您的執行需要訓練機器學習模型, 請參閱[MR 和 Azure 302b](mr-azure-302b.md)。

![實驗室結果](images/AzureLabs-Lab2-000.png)

Microsoft 電腦視覺是一組 Api, 其設計目的是要為開發人員提供影像處理和分析 (包含傳回信息), 並使用所有雲端的先進演算法。 開發人員上傳影像或影像 URL, 而 Microsoft 電腦視覺 API 演算法會根據選擇使用者的輸入來分析視覺內容, 然後傳回信息, 包括識別影像的類型和品質、偵測人臉 (傳回其座標)、標記或分類影像。 如需詳細資訊, 請造訪[Azure 電腦視覺 API 頁面](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。

完成此課程之後, 您將擁有一個混合現實 HoloLens 應用程式, 其將能夠執行下列作業:

1.  使用點一下手勢, HoloLens 的攝影機將會捕捉影像。
2.  映射將會傳送至 Azure 電腦視覺 API 服務。 
3.  辨識的物件將會列在位於 Unity 場景的簡單 UI 群組中。

在您的應用程式中, 您可以決定如何將結果與您的設計整合。 本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。 您的工作是使用您從這個課程取得的知識, 來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 302:電腦視覺</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然此課程主要著重于 HoloLens, 但您也可以將在本課程中學習到的內容套用至 Windows Mixed Reality 沉浸式 (VR) 耳機。 因為沉浸式 (VR) 耳機沒有可存取的相機, 所以您需要連接到電腦的外部相機。 隨著課程的遵循, 您將會看到支援沉浸式 (VR) 耳機時, 您可能需要採取的任何變更的附注。

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。 也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (5 月 2018)。 您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。

在此課程中, 我們建議您採用下列硬體和軟體:

- [與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦, 可用於沉浸式 (VR) 耳機開發
- [已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 已啟用開發人員模式的[Windows Mixed Reality 沉浸 (VR) 耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 連接到您電腦的相機 (適用于沉浸式耳機開發)
- 適用于 Azure 設定和電腦視覺 API 抓取的網際網路存取

## <a name="before-you-start"></a>開始之前

1.  為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。
2.  設定並測試您的 HoloLens。 如果您需要支援設定 HoloLens,[請務必造訪 hololens 安裝程式一文](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  開始開發新的 HoloLens 應用程式時, 最好先執行校正和感應器微調 (有時候它有助於為每個使用者執行這些工作)。 

如需校正的說明, 請遵循此[HoloLens 校正文章的連結](calibration.md#hololens)。

如需感應器微調的說明, 請遵循此[HoloLens 感應器微調文章連結](sensor-tuning.md)。

## <a name="chapter-1--the-azure-portal"></a>第1章– Azure 入口網站

若要在 Azure 中使用*電腦視覺 API*服務, 您將需要設定服務的實例, 讓應用程式可以使用。

1.  首先, 登入[Azure 入口網站](https://portal.azure.com)。 

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶, 您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。

2.  登入之後, 按一下左上角的 [**新增**], 並搜尋*電腦視覺 API*, 然後按一下**Enter**。

    ![在 Azure 中建立新的資源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。
 
3.  新的頁面會提供*電腦視覺 API*服務的描述。 在此頁面的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。

    ![關於電腦視覺 api 服務](images/AzureLabs-Lab2-01.png)
 
4.  一旦您按下 **建立** :

    1. 為此服務實例插入您想要的**名稱**。
    2. 選取**訂**用帳戶。
    3. 選取適合您的**定價層**, 如果這是您第一次建立*電腦視覺 API*服務, 則應該可供您使用的免費層 (名為 F0)。
    4. 選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。 

        > 如果您想要深入瞭解 Azure 資源群組, 請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 判斷資源群組的位置 (如果您要建立新的資源群組)。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于特定區域。

    6. 您也必須確認您已瞭解適用于此服務的條款及條件。
    7. 按一下 [建立]。

        ![服務建立資訊](images/AzureLabs-Lab2-02.png)

5.  按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。
6.  建立服務實例之後, 入口網站中會出現通知。

    ![查看新服務的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  按一下通知以探索新的服務實例。 

    ![選取 [移至資源] 按鈕。](images/AzureLabs-Lab2-04.png)
 
8. 按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。 您將會進入新的電腦視覺 API 服務實例。 

    ![您的新電腦視覺 API 服務](images/AzureLabs-Lab2-05.png)
 
9.  在本教學課程中, 您的應用程式將需要呼叫您的服務, 這會透過使用您服務的訂用帳戶金鑰來完成。
10. 從您*電腦視覺 API*服務的 [*快速入門*] 頁面, 流覽至第一個步驟,*抓取您的金鑰*, 然後按一下 [**金鑰**] (您也可以按一下位於 [服務] 導覽功能表中的藍色超連結金鑰來達成此目的,以按鍵圖示表示)。 這會顯示您的服務*金鑰*。
11. 複製其中一個顯示的金鑰, 因為您稍後會在專案中用到。 

12. 回到 [*快速入門*] 頁面, 然後從該處提取您的端點。 請注意, 您的區域可能會不同, 視您的地區而定 (如果是的話, 您稍後將需要變更程式碼)。 取得此端點的複本以供稍後使用:

    ![您的新電腦視覺 API 服務](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > 您可以在[這裡](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)檢查各種端點。 

## <a name="chapter-2--set-up-the-unity-project"></a>第2章–設定 Unity 專案

以下是使用混合現實進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本。

1.  開啟*Unity* , 然後按一下 [**新增**]。 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab2-06.png)

2.  現在您將需要提供 Unity 專案名稱。 插入**MR_ComputerVision**。 請確定 [專案類型] 設定為 [ **3d**]。 將位置設定為適合您的**位置**(請記住, 接近根目錄較佳)。 然後, 按一下 [**建立專案**]。

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab2-07.png)

3.  在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 **編輯 > 喜好**設定, 然後在新視窗中, 流覽至 **外部工具**。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab2-08.png)

4.  接下來, 移至 [檔案] **> [組建設定**], 並選取 [**通用 Windows 平臺**], 然後按一下 [**切換平臺**] 按鈕以套用您的選取專案。

    ![[組建設定] 視窗, 將平臺切換至 UWP。](images/AzureLabs-Lab2-10.png)

5.  仍在 檔案 **> 組建設定**, 並確認:

    1. **目標裝置**設定為**HoloLens**

        > 針對沉浸式耳機, 將 [**目標裝置**] 設定為 [*任何裝置*]。

    2. **組建類型**設定為**D3D**
    3. **SDK**已設定為**最新安裝**
    4. **Visual Studio 版本**設定為 [**最新安裝**]
    5. **組建和執行**設定為**本機電腦**
    6. 儲存場景, 並將它加入至組建。

        1. 選取 [新增] [**開啟場景**] 來執行此動作。 [儲存] 視窗隨即出現。
        
            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab2-11.png)

        2. 為此建立新的資料夾, 並在任何未來的場景中選取 [**新增資料夾**] 按鈕, 以建立新的資料夾, 將其命名為**場景**。

            ![建立新的腳本資料夾](images/AzureLabs-Lab2-12.png)

        3. 開啟新建立的 [**幕後**] 資料夾, 然後在 [*檔案名*: 文字] 欄位中, 輸入**MR_ComputerVisionScene**, 然後按一下 [**儲存**]。

            ![為新場景指定名稱。](images/AzureLabs-Lab2-13.png)

            > 請注意, 您必須將 Unity 場景儲存在 [*資產*] 資料夾中, 因為它們必須與 Unity 專案相關聯。 建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。

    7. [*組建設定*] 中的其餘設定, 現在應該保留為預設值。

6. 在 [*組建設定*] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測*器*所在的空間中開啟相關的面板。 

    ![開啟 [播放] [設定]。](images/AzureLabs-Lab2-14.png)

7. 在此面板中, 需要驗證幾項設定:

    1. 在 [**其他設定**] 索引標籤中:

        1. **腳本執行階段版本**應為**穩定**(.net 3.5 對等)。
        2. **腳本後端**應該是 **.net**
        3. **API 相容性層級**應該是 **.net 4.6**

            ![更新其他設定。](images/AzureLabs-Lab2-15.png)
      
    2. 在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:

        1. **InternetClient**
        2. **網路**

            ![正在更新發行設定。](images/AzureLabs-Lab2-16.png)

    3. 在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]。

        ![更新 X R 設定。](images/AzureLabs-Lab2-17.png)

8.  回到*組建設定* _Unity C#_ 專案已不再呈現灰色;勾選 [] 旁的核取方塊。 
9.  關閉 [組建設定] 視窗。
10. 儲存場景和專案 (**file > 儲存場景/檔案 > 儲存專案**)。

## <a name="chapter-3--main-camera-setup"></a>第3章–主要攝影機設定

> [!IMPORTANT]
> 如果您想要略過此課程的*Unity 設定*元件, 並繼續直接進入程式碼, 您可以下載這個[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), 將它匯入到您的專案中做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html), 然後繼續進行[第5章](#chapter-5--create-the-resultslabel-class)。

1.  在 [階層]*面板*中, 選取**主要相機**。 
2.  選取之後, 您就可以在 [偵測*器] 面板*中看到**主要攝影機**的所有元件。

    1. **相機物件**必須命名為「**主攝影機**」 (請注意拼寫的!)
    2. 主要相機**標記**必須設定為**MainCamera** (請注意拼寫!)
    3. 請確定**轉換位置**設定為**0, 0, 0**
    4. 將 [**清除旗標**] 設定為**純色**(針對沉浸式耳機忽略此標記)。
    5. 將相機元件的**背景**色彩設定為**黑色、Alpha 0 (十六進位碼: #00000000)** (針對沉浸式耳機則忽略此項)。

        ![更新攝影機元件。](images/AzureLabs-Lab2-18.png)
 
3.  接下來, 您必須建立連接到**主要攝影機**的簡單「游標」物件, 這可協助您在應用程式執行時放置影像分析輸出。 此游標會決定相機焦點的中心點。

若要建立資料指標:

1.  在 [階層]*面板*中, 以滑鼠右鍵按一下**主要相機**。 在 [ **3D 物件**] 底下, 按一下 [**球體**]。

    ![選取游標物件。](images/AzureLabs-Lab2-19.png)
 
2.  將**球體**重新命名為**Cursor** (按兩下游標物件, 或按下 [F2] 鍵盤按鈕, 並選取物件), 並確定它是位於**主攝影機**的子系。

3.  在 [階層]*面板*中, 以滑鼠左鍵按一下**游標**。 選取游標之後, 請在 [偵測*器] 面板*中調整下列變數:

    1. 將*轉換位置*設定為**0, 0, 5**
    2. 將*縮放比例*設定為**0.02、0.02、0.02**

        ![更新轉換位置和縮放比例。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>第4章–設定標籤系統

一旦您使用 HoloLens 的相機來捕捉映射, 該映射就會傳送至您的*Azure 電腦視覺 API*服務實例進行分析。 

該分析的結果會是可識別的物件清單, 稱為**標記**。 

您將使用標籤 (在世界空間中為3D 文字), 在拍攝相片的位置顯示這些標記。

下列步驟將示範如何設定**標籤**物件。

1.  以滑鼠右鍵按一下 [階層] 面板中的任何位置 (此處的位置並不重要), 然後在 [ **3D 物件**] 下加入**3d 文字**。 將它命名為**LabelText**。

    ![建立3D 文字物件。](images/AzureLabs-Lab2-21.png)
 
2.  在 [階層]*面板*中, 以滑鼠左鍵按一下 [ **LabelText**]。 選取**LabelText**之後, 請在 [偵測*器] 面板*中調整下列變數:

    1. 將**位置**設定為**0, 0, 0**
    2. 將**縮放比例**設定為**0.01、0.01、0.01**
    3. 在元件**文本網格**中:
    4. 將**文字**中的所有文字取代為 "..."        
    5. 將**錨點**設定為**中間置**
    6. 將**對齊**設定為 [**置**中]
    7. 將定位**鍵的大小**設定為**4**
    8. 將**字型大小**設定為**50**
    9. 將**色彩**設定為 **#FFFFFFFF**

    ![文字元件](images/AzureLabs-Lab2-21-5.png)

3.  將**LabelText**從 [階層]*面板*拖曳至 [*專案] 面板*中的 [資產]*資料夾*。 這會讓**LabelText**成為 Prefab, 讓它可以在程式碼中具現化。

    ![建立 LabelText 物件的 prefab。](images/AzureLabs-Lab2-22.png)
 
4.  您應該從 [階層]*面板*中刪除**LabelText** , 使其不會顯示在開啟的場景中。 現在它是一個 prefab, 您會針對資產資料夾中的個別實例呼叫它, 而不需要將它保留在場景中。 
5.  [階層]*面板*中的最終物件結構應如下圖所示:

    ![階層面板的最終結構。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>第5章–建立 ResultsLabel 類別

您需要建立的第一個腳本是*ResultsLabel*類別, 其負責下列各項: 

- 在適當的世界空間中建立標籤 (相對於相機的位置)。
- 顯示影像擺脫中的標記。

若要建立此類別: 

1.  在 *專案 面板*中按一下滑鼠右鍵, 然後**建立 > 資料夾**。 將資料夾命名為**Scripts**。 

    ![建立腳本資料夾。](images/AzureLabs-Lab2-24.png)

2.  在 [**腳本**] 資料夾建立後, 按兩下以開啟。 然後在該資料夾中, 以滑鼠右鍵按一下, 然後選取 [**建立] >** [  **C#腳本**]。 將腳本命名為*ResultsLabel*。 

3.  按兩下新的*ResultsLabel*腳本, 以**Visual Studio**開啟它。

4.  在類別內, 于*ResultsLabel*類別中插入下列程式碼:

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

6.  請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。
7.  回到*Unity 編輯器*中, 按一下 [**腳本**] 資料夾中的 [ *ResultsLabel* ] 類別, 並將其拖曳至 [階層]*面板*中的**主要相機**物件。
8.  按一下**主攝影機**並查看 [*檢查] 面板*。

您會發現, 從剛拖曳至相機的腳本中, 有兩個欄位:資料**指標**和**標籤 Prefab**。

9.  將名為**cursor**的物件從 [階層]*面板*拖曳到名為**cursor**的位置, 如下圖所示。
10. 從 [*專案] 面板*中的 [*資產] 資料夾*, 將名為**LabelText**的物件拖曳至名為**Label Prefab**的位置, 如下圖所示。 

    ![在 Unity 中設定參考目標。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>第6章–建立 ImageCapture 類別

下一個您即將建立的類別是*ImageCapture*類別。 此類別負責:

-   使用 HoloLens 攝影機來捕獲影像, 並將其儲存在應用程式資料夾中。
-   捕捉使用者的點擊手勢。

若要建立此類別: 

1.  移至您先前建立的**腳本**資料夾。 
2.  以滑鼠右鍵按一下資料夾內的 [**建立C# > 腳本**]。 呼叫腳本*ImageCapture*。 
3.  按兩下新的*ImageCapture*腳本, 以**Visual Studio**開啟它。
4.  將下列命名空間新增至檔案頂端:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  然後, 在*ImageCapture*類別內的*Start ()* 方法上方新增下列變數:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount**變數會儲存從使用者所捕獲的點擊點手勢數目。 這個數位會用於所捕獲的映射命名。

6.  現在必須加入*喚醒 ()* 和*Start ()* 方法的程式碼。 當類別初始化時, 將會呼叫這些:

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

7.  執行會在點碰手勢發生時呼叫的處理常式。 

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
 
*TapHandler ()* 方法會遞增從使用者中捕捉到的分次次數, 並使用目前的游標位置來決定要在何處放置新的標籤。

然後, 這個方法會呼叫*ExecuteImageCaptureAndAnalysis ()* 方法來開始此應用程式的核心功能。

8.  一旦捕獲並儲存映射之後, 就會呼叫下列處理常式。 如果程式成功, 結果會傳遞至*VisionManager* (您尚未建立) 進行分析。

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
 
9.  然後, 新增應用程式用來啟動映射捕獲進程並儲存映射的方法。

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
> 此時, 您會注意到 [ *Unity 編輯器] 主控台面板*中出現錯誤。 這是因為程式碼會參考您將在下一章中建立的*VisionManager*類別。

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>第7章–呼叫 Azure 和影像分析

您需要建立的最後一個腳本是*VisionManager*類別。 

此類別負責:

-   載入以位元組陣列形式捕獲的最新影像。
-   將位元組陣列傳送至您的*Azure 電腦視覺 API*服務實例以進行分析。
-   以 JSON 字串的形式接收回應。
-   還原序列化回應, 並將產生的標記傳遞至*ResultsLabel*類別。
 
若要建立此類別:

1.  按兩下 [**腳本**] 資料夾以開啟它。 
2.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立 > C#腳本**]。 將腳本命名為*VisionManager*。 
3.  按兩下新的腳本, 以 Visual Studio 開啟它。
4.  在*VisionManager*類別的頂端, 更新命名空間, 以與下列內容相同:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  在腳本頂端的*VisionManager*類別 (在*Start ()* 方法上方) 中, 您現在需要建立兩個*類別*, 以代表來自 Azure 的已還原序列化 JSON 回應:

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
    > *TagData*和*AnalysedObject*類別必須在宣告之前加入 *[system.object]* 屬性, 才能使用 Unity 程式庫進行還原序列化。

6.  在 VisionManager 類別中, 您應該加入下列變數:

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
    > 請務必將您的**驗證金鑰**插入**authorizationKey**變數中。 您會在本課程[第1章](#chapter-1--the-azure-portal)的一開始就記下**驗證金鑰**。

    > [!WARNING] 
    > **VisionAnalysisEndpoint**變數可能與此範例中指定的變數不同。 **美國西部**會嚴格地指的是針對美國西部區域所建立的服務實例。 請使用您的[端點 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)來更新此值;以下是一些可能如下的範例:
    > - 西歐:`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 東南亞:`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 澳大利亞東部:`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  現在必須加入喚醒的程式碼。 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  接下來, 新增協同程式 (使用其底下的靜態資料流程方法), 這會取得*ImageCapture*類別所捕獲影像的分析結果。 

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

9.  請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。
10. 回到 Unity 編輯器中, 按一下 [**腳本**] 資料夾中的 [ *VisionManager* ] 和 [ *ImageCapture* ] 類別, 並將其拖曳至 [階層]*面板*中的**主要相機**物件。 

## <a name="chapter-8--before-building"></a>第8章–大樓

若要執行應用程式的徹底測試, 您必須將它側載到 HoloLens。
在您執行之前, 請確定:

-   [第2章](#chapter-2--set-up-the-unity-project)所述的所有設定都已正確設定。 
-   所有腳本都會附加到**主要相機**物件。 
-   *主要相機偵測器面板*中的所有欄位都已正確指派。
-   請務必將您的**驗證金鑰**插入**authorizationKey**變數中。
-   請確定您已在*VisionManager*腳本中檢查端點, 並將其對應至*您*的區域 (本檔預設使用「*美國西部*」)。

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>第9章–建立 UWP 解決方案並側載應用程式
此專案的 Unity 區段所需的全部內容現在已經完成, 所以可以從 Unity 建立它。

1.  流覽至*組建配置* - **檔案 > 組建設定**。
2.  從 [*組建設定*] 視窗中, 按一下 [**建立**]。

    ![從 Unity 建立應用程式](images/AzureLabs-Lab2-26.png)

3.  如果尚未這麼做, 請先勾選**Unity C#專案**。
4.  按一下 [建置]。 Unity 將會啟動 [檔案*瀏覽器*] 視窗, 您必須在其中建立並選取要建立應用程式的資料夾。 立即建立該資料夾, 並將它命名為*應用程式*。 然後選取 [*應用程式*] 資料夾, 按 [**選取資料夾**]。 
5.  Unity 會開始將您的專案建立至*應用程式*資料夾。 
6.  Unity 完成建立之後 (可能需要一些時間), 它會在組建的位置開啟 [檔案*瀏覽器*] 視窗 (請檢查您的工作列, 因為它不一定會出現在視窗的上方, 但會通知您加入新的視窗)。

## <a name="chapter-10--deploy-to-hololens"></a>第10章-部署至 HoloLens

若要在 HoloLens 上部署:

1.  您將需要 HoloLens 的 IP 位址 (用於遠端部署), 並確保 HoloLens 處於**開發人員模式**。 請這樣做：

    1. 在戴 HoloLens 的同時, 請開啟**設定**。
    2. 前往**Network & Internet > wi-fi > Advanced Options**
    3. 記下**IPv4**位址。
    4. 接下來, 流覽回到 [**設定**], 然後為**開發人員更新 & 的安全性 >** 
    5. 將開發人員模式設定為 On。

2.  流覽至新的 Unity 組建 (*應用程式*資料夾), 然後使用*Visual Studio*開啟方案檔。
3.  在 [解決方案設定] 中, 選取 [ **Debug**]。
4.  在解決方案平臺中, 選取 [ **x86**]、[**遠端電腦**]。 

    ![從 Visual Studio 部署解決方案。](images/AzureLabs-Lab2-27.png)
 
5.  移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的 HoloLens。
6.  您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中, 準備好啟動!

> [!NOTE]
> 若要部署到沉浸式耳機, 請將**解決方案平臺**設定為 [*本機電腦*], 然後將 [設定] 設為 [ *Debug*], 並將*x86*作為**平臺**。 然後, 使用 [**建立] 功能表**, 選取 [*部署解決方案*], 部署至本機電腦。 

## <a name="your-finished-computer-vision-api-application"></a>您完成的電腦視覺 API 應用程式

恭喜您, 您建立了一個混合現實應用程式, 利用 Azure 電腦視覺 API 來辨識現實世界的物件, 並顯示已看到之內容的信心。

![實驗室結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

就如同您在*VisionManager*中使用的*端點*內所使用的*標記*參數一樣, 請擴充應用程式以偵測其他資訊;請[在此](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)查看您可以存取的其他參數。

### <a name="exercise-2"></a>練習2

以更具交談和可讀取的方式顯示傳回的 Azure 資料, 可能會隱藏數位。 如同 bot 可能對使用者說話。
