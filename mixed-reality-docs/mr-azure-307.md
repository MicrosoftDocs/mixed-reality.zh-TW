---
title: MR 和 Azure 307-機器學習服務
description: 完成這個課程來了解如何實作 Azure Machine Learning Studio 內的混合的實境應用程式。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 機器學習服務，ml、 機器學習 studio、 hololens、 沈浸式、 vr
ms.openlocfilehash: 93263817df0fd809a09b32c1b34a636eab7026a1
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516044"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR 和 Azure 307:機器學習

![最終產品-開始](images/AzureLabs-Lab7-0.png)

在此課程中，您將學習如何將 Machine Learning (ML) 功能新增至混合的實境應用程式使用 Azure Machine Learning Studio。

*Azure Machine Learning Studio*是 Microsoft 服務，開發人員提供了大量的機器學習服務演算法，可協助進行資料輸入、 輸出、 準備及視覺效果。 從這些元件，就能夠開發預測性分析實驗，逐一查看，並使用它來定型模型。 下列訓練，您可以讓您的模型運作內 Azure 雲端中，以便它可以再評分新資料。 如需詳細資訊，請瀏覽[Azure Machine Learning Studio 頁面](https://azure.microsoft.com/en-au/services/machine-learning-studio/)。

完成本課程，您將的混合的實境沈浸式耳機應用程式，且將會學到如何執行下列作業：

1.  提供的銷售資料的資料表*Azure Machine Learning Studio*入口網站，並設計演算法來預測未來銷售的受歡迎的項目。
2.  建立**Unity 專案**，它可以接收和解譯 ML 服務的預測資料。
3.  中以視覺化方式顯示 predication 資料**Unity 專案**，透過提供的最受歡迎的銷售項目，放到書架上。

在您的應用程式，則您對於如何將整合結果進行設計。 本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。 它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。

本課程是獨立的教學課程，其中並不直接包含任何其他混合實境實驗室。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 307:機器學習</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。 當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。 當使用 HoloLens，您可能會發現某些回應語音擷取期間。

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程專為具有基礎經驗的 Unity 開發人員和C#。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。 中所示，您可以自由使用最新的軟體[安裝工具文章](install-the-tools.md)，不過它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體與以下所列.

我們建議下列的硬體和軟體這堂課程：

- 開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發
- [Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式
- 針對 Azure 設定和 ML 資料擷取的網際網路存取

## <a name="before-you-start"></a>開始之前

若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。 

## <a name="chapter-1---azure-storage-account-setup"></a>第 1 章-Azure 儲存體帳戶設定

若要使用 Azure 轉譯程式 API，您必須設定您的應用程式提供服務的執行個體。
1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**儲存體帳戶**左側功能表中。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > 單字**的新**可能已取代為**建立資源**，較新的入口網站中。

3.  在 **儲存體帳戶**索引標籤上，按一下**新增**。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-2.png)

4.  在 **建立儲存體帳戶**面板：

    1.  插入**名稱**您的帳戶，請留意這個欄位只接受數字和小寫字母。
    2.  針對**部署模型**選取**Resource manager**。
    3.  針對**帳戶種類**，選取**儲存體 (一般用途 v1)** 。
    4.  針對**效能**，選取**標準**。
    5.  針對**複寫**選取**讀取-存取-異地備援儲存體 (RA-GRS)** 。
    6.  離開**需要安全傳輸**作為**停用**。
    7.  選取 **訂用帳戶**。
    4. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。
    
    5.  判斷**位置**資源群組 （如果您要建立新的資源群組）。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。

5.  您也必須確認您已了解這些條款和條件套用到此服務。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-3.png)

6.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

7.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>第 2 章-Azure Machine Learning Studio

若要使用*Azure Machine Learning*，您必須設定機器學習服務可供您的應用程式的執行個體。

1.  在 Azure 入口網站中，按一下**新增**在左上角，，然後搜尋**Machine Learning Studio 工作區**、 按下**Enter**。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  新的頁面將提供的描述**Machine Learning Studio 工作區**服務。 在此提示的左下方，按一下**建立**按鈕，以建立與此服務的關聯。

3.  一旦您按下**Create**，面板會顯示您要提供一些關於您的新詳細資料**Machine Learning Studio 服務**:

    1.  插入您想要**工作區名稱**此服務執行個體。

    2.  選取 **訂用帳戶**。

    3. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。 

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  判斷**位置**資源群組 （如果您要建立新的資源群組）。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。 您應該使用相同的資源群組，您用來建立 Azure 儲存體上一章。

    5.  針對**儲存體帳戶**區段中，按一下**使用現有**，然後按一下下拉式功能表中，並從該處，按一下**儲存體帳戶**在最後一章中所建立。

    6.  選取適當**工作區定價層**為您從下拉式功能表中。

    7.  內**Web 服務方案**區段中，按一下**建立** **新**再插入的文字欄位中的名稱。

    8.  從**Web 服務方案定價層**區段中，選取您選擇的價格層。 開發，測試呼叫階層**研發/測試標準**應該是您可以免費使用。

    9.  您也必須確認您已了解這些條款和條件套用到此服務。

    10. 按一下 [建立]  。

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

5.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  按一下通知，以探索新的服務執行個體。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。

8.  在下方顯示的網頁**其他連結**區段中，按一下**啟動 Machine Learning Studio**，這會將導向您的瀏覽器**Machine Learning Studio**入口網站。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  使用**登入** 按鈕，在右上方，或是在中心，登入您的 Machine Learning Studio 中。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>第 3 章-Machine Learning Studio:資料集的安裝程式

其中一種機器學習服務演算法運作方式是藉由分析現有的資料，並嘗試預測未來結果根據現有的資料集。 這通常表示，多現有的資料有，較佳的演算法會在預測未來結果。

範例資料表會提供給您，這堂課程中，呼叫[ProductsTableCSV 而且可以在這裡下載](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。

> [!IMPORTANT]
> 上述的.zip 檔案同時包含**ProductsTableCSV**並 **.unitypackage**，您將需要在[第 6 章](#chapter-6---importing-the-mlproducts-unity-package)。 此套件也會提供內該章節，但不同的 csv 檔案。

此範例資料集包含每小時的每一天的 2017 年的銷售量最高的物件記錄。
        
![Machine Learning Studio:資料集的安裝程式](images/AzureLabs-Lab7-11.png)

例如，在 2017 年第 1 天，下午 1 點 （小時 13），最暢銷的項目已 salt 披頭四與。

此範例資料表包含 9998 的項目。

1.  返回**Machine Learning Studio**入口網站中，並新增為此資料表**Dataset**您 ml。 依序按一下 **+ 新增**在畫面的左下角的按鈕。

    ![Machine Learning Studio:資料集的安裝程式](images/AzureLabs-Lab7-12.png)

2.  區段會出現從底部，且內左側的瀏覽窗格中。 按一下 **資料集**，則，右邊**從本機檔案**。

    ![Machine Learning Studio:資料集的安裝程式](images/AzureLabs-Lab7-13.png)

3.  上傳新**資料集**依照下列步驟：

    1. 會出現 [上傳] 視窗中，您可以在其中**瀏覽**硬碟的新資料集。

        ![Machine Learning Studio:資料集的安裝程式](images/AzureLabs-Lab7-14.png)

    2.  一旦選取，並重新上傳 視窗中，保留未核取此核取方塊。

    3.  在下方的文字欄位中輸入**ProductsTableCSV.csv**做為資料集的名稱 （但應該會自動加入）。

    4.  使用下拉式功能表**型別**，選取**一般 CSV 檔案 (.csv) 的標頭**。

    5.  按下的刻度在右下方的 [上傳] 視窗中，而您**資料集**即將上傳。

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>第 4 章-Machine Learning Studio:實驗

您可以建立您的機器學習系統之前，您必須建置實驗，以驗證您的理論上，您的資料。 結果，您會知道您是否需要更多資料，或是否有可能出現的結果和資料之間沒有相互關聯。

若要啟動建立實驗：

1.  請再按一下 **+ 新增**左下角的頁面，按鈕，然後按一下**實驗** > **空白實驗**。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-15.png)

2.  空白實驗，將會顯示新的頁面：

3.  從左側面板中，展開 **儲存的資料集* > *我的資料集** 拖曳**ProductsTableCSV**入**實驗畫布**。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-16.png)

4.  在左側窗格中，依序展開**Data Transformation** > **取樣和分割**。 然後將拖曳**資料分割**項目中加入**實驗畫布**。 分割資料的項目會將資料集分成兩個部分。 您將用於定型機器學習演算法使用一個組件。 第二個部分會用於評估產生演算法的精確度。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-17.png)

5.  在右窗格中 （同時在畫布上的項目已選取分割資料），請編輯**的第一個輸出資料集中的資料列比例**要**0.7**。 這會將資料分成兩個部分，第一個部分會 70%的資料，而第二個部分會剩餘的 30%。 若要確保資料會隨機分割，請確定**Randomized split**核取方塊保持核取狀態。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-18.png)

6.  拖曳連接自的基底**ProductsTableCSV**分割資料的項目頂端，在畫布上的項目。 這會連接的項目，並傳送**ProductsTableCSV**資料集輸出至輸入的資料分割 （資料）。  

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-19.png)

7.  在 **實驗**左側面板中，展開 **Machine Learning* > * 訓練 * *。 拖曳**定型模型**中的項目縮小到實驗畫布。 畫布看起來應該與相同如下。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-20.png)

8.  從***左下方***的**分割資料**項目拖曳至某個連線**右上方**的**定型模型**項目。 第一個 70%分割資料集將用於定型的模型定型演算法。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-21.png)

9.  選取 **定型模型**畫布，在和中的項目**屬性**面板 （在您的瀏覽器視窗的右手邊） 按一下 **啟動資料行選取器** 按鈕。

10. 在文字方塊中輸入**產品**，然後按**Enter**，*產品*將做為資料行來訓練預測。 在此之後，按一下**刻度**以關閉 [選取] 對話方塊右下角。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-22.png)

11. 您要定型**多級羅吉斯迴歸**演算法來預測銷售最**產品**根據日期和日期的小時。 超出本文件提供 Azure Machine Learning studio 中，不過，不同演算法的詳細說明的範圍是您可以深入了解從[機器學習服務演算法小祕技](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. 從 實驗 項目面板的 在左側，展開 * **Machine Learning* > *初始化模型*> * 分類 * * *，然後拖曳**多級羅吉斯迴歸**至實驗畫布的項目。

13. 輸出中，連接到從底部**多級羅吉斯迴歸**的左上方輸入**定型模型**項目。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-23.png)

14. 在清單中的實驗項目，在左側面板中，展開 **Machine Learning* > * 分數 * *，然後將拖曳**評分模型**至畫布的項目。

15. 輸出中，連接到從底部**定型模型**的左上方輸入**評分模型**。

16. 從右下方輸出連接到**資料分割**，到右上方的輸入 **評分模型*項目*。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-24.png)

17. 在這份**實驗**在左側面板中的項目會展開 * **Machine Learning* > * 評估 * * *，然後拖曳**評估模型**拖曳到畫布上的項目。

18. 從輸出連接到**評分模型**的左上方輸入**評估模型**。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-25.png)

19. 您已建立您的第一個機器學習服務實驗。 您現在可以儲存並執行實驗。 在頁面底部功能表中，按一下**儲存**按鈕以儲存您的實驗，然後按一下**執行**開始實驗。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-26.png)

20. 您所見**狀態**中右上方畫布的實驗。 等候一些時間才能完成實驗。

    > 如果您有大型 （實際） 資料集很可能實驗可能需要執行的小時。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-27.png)

21. 以滑鼠右鍵按一下**評估模型**項目畫布中，並從內容功能表動態顯示滑鼠透過**評估結果**，然後選取**視覺化**。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-28.png)

22. 將顯示預測的結果與實際的結果會顯示評估結果。 這會使用原始資料集已分割更早版本，來評估模型的 30%。 您可以看到結果不是太棒了，在理想情況下您會具有最高數量中每個資料列是資料行中的反白顯示的項目。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-29.png)

23. 關閉**結果**。

24. 若要使用您新定型的機器學習服務模型，您需要將它公開為**Web 服務**。 若要這樣做，請按一下**設定 Web 服務** 功能表項目在頁面底部的功能表，然後按一下**預測性 Web 服務**。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-30.png)

25. 將建立新的索引標籤，並合併以建立新的 web 服務的定型模型。 

26. 在頁面底部的功能表中按一下**儲存**，然後按一下**執行**。 您會看到更新的實驗畫布右上角的狀態。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-31.png)

27. 一旦執行，完成**部署 Web 服務**按鈕將會出現在頁面底部。 您已準備好部署 web 服務。 按一下 **部署 Web 服務**（傳統） 在頁面底部的功能表中。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-32.png)

    > 您的瀏覽器可能會提示以允許快顯視窗，您應該**允許**，不過您可能需要按下**部署 Web 服務**同樣地，如果未顯示 [部署] 頁面。 

28. 建立實驗之後您將會重新導向至**儀表板**頁面，您必須將您**API 金鑰**顯示。 將它複製到 [記事本] 中，目前為止，您將很快在程式碼中需要它。 一旦您已記下您的 API 金鑰，按一下**要求/回應**按鈕**預設端點**區段下方的索引鍵。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > 如果您在此頁面中按一下測試，您可以輸入的輸入的資料，並檢視輸出。 請輸入**天**並**小時**。 離開**產品**空白的項目。 然後按一下**確認** 按鈕。 在頁面底部的輸出會顯示 JSON 表示正在選擇每項產品的可能性。

29. 新的 web 網頁將會開啟，顯示的指示和 Machine Learning Studio 所需的要求結構相關的一些範例。 複製**要求 URI**顯示在此頁面中，到您的 [記事本]。

    ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-34.png)

現在您已建置機器學習系統，可提供銷售產品最有可能根據購買歷程記錄資料，就是相互關聯的日期和年份的日期時間。

若要呼叫 web 服務，您需要 URL 的服務端點和服務的 API 金鑰。 按一下 **取用**索引標籤上，從上方的功能表。

**耗用量**資訊頁面會顯示您必須從您的程式碼中呼叫 web 服務的資訊。 需要一份**主索引鍵**並**要求-回應**URL。 您必須在下一步 一章中。

## <a name="chapter-5---setting-up-the-unity-project"></a>第 5 章-設定 Unity 專案

設定並測試混合實境沈浸式耳機。

> [!NOTE]
>  您將會**不**本課程所需動作的控制器。 如果您需要支援沈浸式耳機的設定，請按一下[此處](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  開啟**Unity**並建立新的 Unity 專案，稱為**MR\_。** 請確定專案類型設定為**3D**。

2.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至 ***編輯* > *喜好設定*** 從新的視窗中，然後瀏覽至 **外部工具** 。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

3.  接下來，移至 ***檔案* > *組建設定*** 切換平台**通用 Windows 平台**，按一下***切換平台*** 按鈕。

4.  此外，請確定：

    1.  **裝置為目標**設定為**任何裝置**。

        > 對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。

    2.  **建置型別**設定為**D3D**。

    3.  **SDK**設定為**最新安裝**。

    4.  **Visual Studio 版本**設定為**最新安裝**。

    5.  **建置並執行**設定為**本機電腦**。

    6.  不要擔心設定**場景**立即，因為這些會在稍後提供。

    7.  其餘的設定應該保持為預設值，現在。

        ![設定 Unity 專案](images/AzureLabs-Lab7-35.png)

5.  中**組建設定**視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。 

6. 在此窗格中，少數設定需要驗證：

    1.  在 [**其他設定**] 索引標籤：

        1.  **指令碼** **執行階段版本**應該**實驗性**（.NET 4.6 對等）

        2. **指令碼後端**應該是 ***.NET***

        3. **API 相容性層級**應該是 **.NET 4.6**

            ![設定 Unity 專案](images/AzureLabs-Lab7-36.png)

    2.  內**發佈設定**索引標籤之下**功能**，檢查：

        - **InternetClient**

            ![設定 Unity 專案](images/AzureLabs-Lab7-37.png)

    3.  在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入

        ![設定 Unity 專案](images/AzureLabs-Lab7-38.png)

    

6.  回到**Build Settings** *Unity C#* 專案不再呈現灰色，這旁邊的核取方塊。 

7.  關閉 [建立設定] 視窗。

8.  儲存您的專案 (**檔案 > 儲存專案**)。

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>第 6 章-匯入 MLProducts Unity 封裝

這堂課程中，您必須下載 Unity 資產套件，稱為[ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)。 此套件都有完整的場景，請使用中的所有物件也預先建置，因此您可以專注於取得它所有的工作。 **ShelfKeeper**提供指令碼，不過只會保留用於場景的安裝程式結構的公用變數。 您必須執行所有其他區段。 

若要匯入此套件：

1.  您面前的 Unity 儀表板中，按一下**資產**在畫面頂端的功能表，然後按一下**匯入封裝]、 [自訂封裝**。

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-39.png)

2.  使用檔案選擇器選取**Azure-MR-307.unitypackage**封裝，然後按一下**開啟**。

3.  為此資產的元件的清單會顯示給您。 確認匯入，依序按一下**匯入**。

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-40.png)

4.  完成匯入後，您會注意到一些新的資料夾會出現在您的 Unity **[專案] 面板**。 這些都是場景的 3D 模型和屬於預先製作，您要處理的個別資料。 在本課程中，您將撰寫大部分的程式碼。

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-41.png)

5.  內**專案 面板**資料夾中，按一下**場景**資料夾，按兩下 在場景 (稱為**MR_MachineLearningScene**)。 場景會開啟 （請參閱下圖）。 如果紅色菱形遺漏，只要按一下**Gizmo**頂端的按鈕，方**遊戲面板**。

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>第 7 章-檢查 Unity 中的 Dll

若要利用 JSON 文件庫 （用於序列化和還原序列化） 使用，已與您所引進的封裝實作 Newtonsoft DLL。 程式庫應該有正確的設定，雖然很值得一查 （特別是當使用無效的程式碼有問題）。 

方法如下：

-  以滑鼠左鍵按一下 Plugins 資料夾內 Newtonsoft 歸檔，並查看**Inspector 面板**。 請確定**任何平台**已勾選。 移至**UWP 索引標籤**也可確保**不會處理**已勾選。

    ![匯入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>第 8-建立 ShelfKeeper 類別

**ShelfKeeper**類別裝載控制項的 UI 和產品在場景中繁衍的方法。

匯入套件的一部分，您將會提供這個類別，但已完成。 現在正是時候以完成該類別：

1.  按兩下**ShelfKeeper**指令碼，在**指令碼**資料夾，將它以開啟**Visual Studio 2017**。

2.  取代現有的指令碼使用下列程式碼，可設定的時間和日期，並已顯示產品的方法中的所有程式碼。

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  請務必儲存您的變更，在**Visual Studio** ，然後傳回給**Unity**。

4.  傳回在 Unity 編輯器中，確認**ShelfKeeper**類別看起來像下面：

    ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > 如果您的指令碼並沒有參考目標 (亦即 *(Mesh 的文字) 的日期*)，只需將拖曳對應的物件，從**階層面板**，目標欄位。 請參閱以下的說明，如有需要：
    > 
    > 1.  開啟**繁衍點**陣列內**ShelfKeeper**元件指令碼中的用滑鼠左鍵按一下它。 子區段會出現稱為**大小**，表示陣列的大小。 型別**3**旁邊的文字方塊**大小**然後按**Enter**，和下方，將會建立三個位置。
    > 2. 內**階層**展開**時間顯示**（藉由它旁邊的箭號上按一下滑鼠左鍵） 的物件。 接下來，按一下***Main Camera***內在**階層**，以便**Inspector**顯示其資訊。
    > 3. 選取 **主攝影機**中**階層面板**。 拖曳**日期**並**時間**物件**階層面板**來**日期的文字**和**階段文字**位置內**Inspector**的**Main Camera**中**ShelfKeeper**元件。
    > 4. 拖曳**繁衍點**從**階層面板**(下方*貨架*物件) 至**3** **元素**參考下的目標**繁衍點**陣列，如圖所示。
    > 
    >     ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>第 9-建立 ProductPrediction 類別

下一步要建立的類別是**ProductPrediction**類別。

這個類別會負責：

-   查詢**Machine Learning 服務**執行個體，提供目前的日期和時間。

-   可用的資料還原序列化 JSON 回應。

-   解譯的資料，擷取 3 個建議的產品。

-   呼叫**ShelfKeeper**類別方法來顯示場景中的資料。

若要建立此類別：

1.  移至**指令碼**資料夾，請在 **[專案] 面板**。

2.  在資料夾中，以滑鼠右鍵按一下**Create** > **C\#指令碼**。 呼叫指令碼**ProductPrediction**。

3.  按兩下新**ProductPrediction**指令碼，以開啟它**Visual Studio 2017**。

4.  如果**偵測到檔案修改**對話方塊顯示，按一下 ***重新載入解決方案**。

5.  ProductPrediction 類別頂端新增下列命名空間：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  內部**ProductPrediction**類別插入下列兩個物件是由數個巢狀類別所組成。 這些類別用來序列化和還原序列化的 Machine Learning 服務的 JSON。

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  （如此 JSON 的相關程式碼的指令碼，以下的所有其他程式碼，來移底部），然後加入先前的程式碼上方的下列變數：

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > 請確定插入**主索引鍵**並**要求-回應端點**，從 Machine Learning 入口網站，為的變數。 以下影像顯示其中您所花的金鑰和端點。 
    >  
    > ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio:實驗](images/AzureLabs-Lab7-53-2.png)

8.  插入此程式碼內**start （)** 方法。 **Start （)** 類別初始化時，會呼叫方法：

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  以下是從 Windows 收集的日期和時間，並將它轉換成機器學習服務實驗可用來比較儲存在資料表中的資料格式的方法。

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. 您可以**刪除** **update （)** 方法，因為這個類別不會使用它。

11. 新增下列方法將目前的日期和時間的機器學習服務端點進行通訊，並接收 JSON 格式的回應。

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. 新增下列方法，也就是負責還原序列化 JSON 回應，以及通訊的還原序列化結果**ShelfKeeper**類別。 此結果會在目前的日期和時間大部分的銷售預測三個項目的名稱。 插入下列程式碼**ProductPrediction**類別前, 一個方法如下。

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. 儲存**Visual Studio**返回並**Unity**。

14. 拖曳**ProductPrediction**類別的指令碼從**指令碼**資料夾中，拖曳至**Main Camera**物件。

15. 儲存您的場景和專案**檔案** >  ***儲存場景* / *檔案***  >  **儲存專案**。

## <a name="chapter-10---build-the-uwp-solution"></a>第 10 章-建置 UWP 方案

現在正是時候建置您的專案做為 UWP 方案，讓它可以當做獨立應用程式執行。

若要建置：

1.  按一下儲存目前的場景**檔案** **儲存場景**。

2.  移至**檔案** **組建設定**

3.  核取方塊稱為**Unity C\#專案**（這是重要因為這樣可讓您完成建置後編輯類別）。

4.  按一下 **將開啟的場景新增**，

5.  按一下 [建置]  。

    ![建置 UWP 方案](images/AzureLabs-Lab7-54.png)

6.  系統會提示您選取您要建置方案的資料夾。

7.  建立**建置**資料夾和該資料夾中建立適當的名稱，您選擇的另一個資料夾。

8.  按一下您的新資料夾，然後按一下**選取資料夾**，若要開始在該位置的組建。

    ![建置 UWP 方案](images/AzureLabs-Lab7-55.png)

    ![建置 UWP 方案](images/AzureLabs-Lab7-56.png)

9.  一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。

## <a name="chapter-11---deploy-your-application"></a>第 11-部署應用程式

若要部署您的應用程式：

1.  瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。

2.  使用 Visual Studio 中開啟，您需要還原 NuGet 套件，您可以透過 MachineLearningLab_Build 方案時，從 方案總管中 （右邊的 Visual Studio 找到），以滑鼠右鍵按一下，然後按一下 還原 NuGet 套件：

    ![新增 NuGet 封裝](images/AzureLabs-Lab7-57.png)

3.  在 方案組態選取**偵錯**。

4.  在 方案平台上，選取**x86**，**本機**。 

    > 針對 Microsoft HoloLens，您可能會發現它更輕鬆地將此設為*遠端機器*，如此一來，您不行動網卡到您的電腦。 不過，您必須也執行下列作業：
    > - 了解**IP 位址**的您 HoloLens，位於*設定 > 網路和網際網路 > Wi-fi > 進階選項*; IPv4 是您應該使用的位址。 
    > - 請確定**開發人員模式**是**上**; 在找到*設定 > 更新與安全性 > 適用於開發人員*。

    ![新增 NuGet 封裝](images/AzureLabs-Lab7-58.png)

5.  移至**建置 功能表**，然後按一下**部署方案**側載應用程式以您的電腦。

6.  您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。

當您執行的混合實境應用程式時，您會看到已設定您的 Unity 場景，請在工作台，而且將從初始化時，擷取您在 Azure 中設定的資料。 資料會在應用程式內進行還原序列化，並將視覺化工作台上的三種模型提供的最上層的三個結果，您目前的日期和時間。


## <a name="your-finished-machine-learning-application"></a>您已完成的機器學習服務應用程式
 
恭喜，您建置利用 Azure Machine Learning 來進行資料預測，並顯示在場景的混合的實境應用程式。

![新增 NuGet 封裝](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>練習

**練習 1**

體驗您的應用程式的排序次序，並具有這項資料可能會有用也出現在上架，下方的三個預測。

**練習 2**

使用**Azure 資料表**填入新資料表天氣資訊，並建立新的實驗使用的資料。
