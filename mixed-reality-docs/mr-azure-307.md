---
title: MR 和 Azure 307-機器學習服務
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure Machine Learning Studio。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合現實，學術，unity，教學課程，api，機器學習，ml，machine learning studio，hololens，沉浸，vr
ms.openlocfilehash: c86c592573dd39d926869d8cce6025fa264cc90f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437929"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時，使用這些教學課程的連結進行更新。

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR 和 Azure 307：機器學習服務

![最終產品-開始](images/AzureLabs-Lab7-0.png)

在此課程中，您將瞭解如何使用 Azure Machine Learning Studio，將 Machine Learning （ML）功能新增至混合現實應用程式。

*Azure Machine Learning Studio*是一項 Microsoft 服務，可為開發人員提供大量的機器學習服務演算法，這有助於資料輸入、輸出、準備和視覺效果。 在這些元件中，您可以開發預測性分析實驗、逐一查看，並使用它來定型您的模型。 依照訓練，您可以讓模型在 Azure 雲端中運作，讓它可以對新資料進行評分。 如需詳細資訊，請造訪[Azure Machine Learning Studio 頁面](https://azure.microsoft.com/services/machine-learning-studio/)。

完成此課程之後，您將擁有一個混合現實的沉浸式耳機應用程式，並將學習如何執行下列作業：

1.  將銷售資料的資料表提供給*Azure Machine Learning Studio*入口網站，並設計演算法來預測熱門專案的未來銷售。
2.  建立**Unity 專案**，它可以接收並解讀來自 ML 服務的預測資料。
3.  透過在貨位上提供最受歡迎的銷售專案，以視覺化方式在**Unity 專案**中顯示 predication 資料。

在您的應用程式中，您可以決定如何將結果與您的設計整合。 本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。 您的工作是使用您從這個課程取得的知識，來增強您的混合現實應用程式。

本課程是獨立的教學課程，不直接牽涉到其他任何混合現實實驗室。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 307：機器學習服務</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然此課程主要著重于 Windows Mixed Reality 沉浸式（VR）耳機，但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。 隨著課程的遵循，您會看到您可能需要用來支援 HoloLens 的任何變更的附注。 使用 HoloLens 時，您可能會在語音捕獲期間發現一些回應。

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。 也請注意，本檔中的必要條件和書面指示，代表在撰寫本文時已測試和驗證的內容（5月2018）。 您可以免費使用 [[安裝工具] 文章](install-the-tools.md)中所列的最新軟體，但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容，而不是如下所示。

在此課程中，我們建議您採用下列硬體和軟體：

- [與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦，可用於沉浸式（VR）耳機開發
- [已啟用開發人員模式的 Windows 10 秋季建立者更新（或更新版本）](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 已啟用開發人員模式的[Windows Mixed Reality 沉浸（VR）耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 適用于 Azure 設定和 ML 資料抓取的網際網路存取

## <a name="before-you-start"></a>開始之前

為避免在建立此專案時發生問題，強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案（長資料夾路徑可能會在組建階段造成問題）。 

## <a name="chapter-1---azure-storage-account-setup"></a>第1章-Azure 儲存體帳戶設定

若要使用 Azure Translator API，您必須設定服務的實例，讓應用程式可以使用。
1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程，請洽詢您的講師或其中一個 proctors，以協助設定您的新帳戶。

2.  登入之後，請按一下左側功能表中的 [**儲存體帳戶**]。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > 在較新的入口網站中，**新**的「可能」已取代為「**建立資源**」。

3.  在 [**儲存體帳戶**] 索引標籤上，按一下 [**新增**]。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-2.png)

4.  在 [**建立儲存體帳戶**] 面板中：

    1.  插入您帳戶的**名稱**，請注意此欄位只接受數位和小寫字母。
    2.  針對 [**部署模型]，** 選取 [ **Resource manager**]。
    3.  針對 [**帳戶類型**]，選取 [**儲存體（一般用途 v1）** ]。
    4.  針對 [**效能**]，選取 [**標準**]。
    5.  針對 **[** 複寫]，選取 **[讀取權限-異地-多餘儲存體（RA-GRS）** ]。
    6.  將 [**需要安全傳輸**] 保留為 [**停用**]。
    7.  選取**訂**用帳戶。
    4. 選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務（例如這些實驗室）都保留在通用資源群組底下）。

        > 如果您想要深入瞭解 Azure 資源群組，請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。
    
    5.  判斷資源群組的**位置**（如果您要建立新的資源群組）。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于特定區域。

5.  您也必須確認您已瞭解適用于此服務的條款及條件。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-3.png)

6.  按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。

7.  建立服務實例之後，入口網站中會出現通知。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>第2章-Azure Machine Learning Studio

若要使用*Azure Machine Learning*，您必須設定 Machine Learning 服務的實例，讓應用程式可以使用。

1.  在 Azure 入口網站中，按一下左上角的 [**新增**]，然後搜尋**Machine Learning Studio 工作區**，按**enter**鍵。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  [新增] 頁面將會提供**Machine Learning Studio 工作區**服務的描述。 在此提示的左下方，按一下 [**建立**] 按鈕，以建立與此服務的關聯。

3.  當您按一下 [**建立**] 之後，就會出現一個面板，您必須在其中提供有關新**Machine Learning Studio 服務**的一些詳細資料：

    1.  為此服務實例插入所需的**工作區名稱**。

    2.  選取**訂**用帳戶。

    3. 選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務（例如這些實驗室）都保留在通用資源群組底下）。 

        > 如果您想要深入瞭解 Azure 資源群組，請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  判斷資源群組的**位置**（如果您要建立新的資源群組）。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于特定區域。 您應該使用您在上一章中用來建立 Azure 儲存體的相同資源群組。

    5.  在 [**儲存體帳戶**] 區段中，按一下 [**使用現有**的]，然後按一下下拉式功能表，然後按一下您在上一章中建立的**儲存體帳戶**。

    6.  從下拉式功能表中，為您選取適當的**工作區定價層**。

    7.  在 [ **Web 服務方案**] 區段中 **，按一下 [新建]** **，** 然後在文字欄位中插入它的名稱。

    8.  從 [ **Web 服務方案定價層**] 區段中，選取您選擇的 [定價層]。 名為**DEVTEST Standard**的開發測試層應免費提供給您。

    9.  您也必須確認您已瞭解適用于此服務的條款及條件。

    10. 按一下 \[建立\]。

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。

5.  建立服務實例之後，入口網站中會出現通知。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  按一下通知以探索新的服務實例。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  按一下通知中的 [**移至資源**] 按鈕，探索新的服務實例。

8.  在顯示的頁面中，按一下 [**其他連結**] 區段下的 [**啟動 Machine Learning Studio**]，這會將您的瀏覽器導向**Machine Learning Studio**入口網站。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  使用位於右上方或中央的 [登**入**] 按鈕，登入您的 Machine Learning Studio。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>第3章-Machine Learning Studio：資料集設定

Machine Learning 演算法的工作方式之一是分析現有的資料，然後根據現有的資料集嘗試預測未來的結果。 這通常表示您擁有的資料愈多，演算法將在預測未來結果時愈好。

範例資料表會提供給您，在此課程中稱為[ProductsTableCSV，而且可以在這裡下載](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。

> [!IMPORTANT]
> 上述 .zip 檔案包含**ProductsTableCSV**和**unitypackage**，您將在[第6章](#chapter-6---importing-the-mlproducts-unity-package)中需要此檔案。 這一章也提供此套件，但與 csv 檔案分開。

此範例資料集包含每一年2017之每小時的最佳銷售物件記錄。
        
![Machine Learning Studio：資料集設定](images/AzureLabs-Lab7-11.png)

例如，在2017的第1天，下午（小時13），最佳銷售專案是 salt 和辣椒。

這個範例資料表包含9998專案。

1.  返回**Machine Learning Studio**入口網站，並將此資料表新增為 ML 的**資料集**。 若要這麼做，請按一下畫面左下角的 [ **+ 新增**] 按鈕。

    ![Machine Learning Studio：資料集設定](images/AzureLabs-Lab7-12.png)

2.  區段會從底部出現，並在左側有導覽面板。 **從 [本機**檔案]，按一下 [**資料集**]，然後從 [] 右邊。

    ![Machine Learning Studio：資料集設定](images/AzureLabs-Lab7-13.png)

3.  依照下列步驟來上傳新的**資料集**：

    1. [上傳] 視窗隨即出現，您可以在其中**流覽**硬碟以尋找新的資料集。

        ![Machine Learning Studio：資料集設定](images/AzureLabs-Lab7-14.png)

    2.  選取之後，返回 [上傳] 視窗，將核取方塊保留為 [未核取]。

    3.  在下面的文字欄位中，輸入**ProductsTableCSV**做為資料集的名稱（但應該自動加入）。

    4.  使用 [**類型**] 的下拉式功能表，選取**具有標頭（.Csv）的一般 CSV**檔案。

    5.  按下 [上傳] 視窗右下方的 [滴答]，將會上傳您的**資料集**。

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>第4章-Machine Learning Studio：實驗

建立機器學習系統之前，您必須先建立實驗，以驗證您對資料的理論。 有了結果，您就會知道您是否需要更多資料，或者資料與可能的結果之間沒有相互關聯。

若要開始建立實驗：

1.  再次按一下頁面左下方的 [ **+ 新增**] 按鈕，然後按一下 [**實驗** > **空白實驗**]。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-15.png)

2.  新的頁面會顯示空白實驗：

3.  從左側面板中，展開 [**已儲存的資料集**] > [**我的資料集**]，然後將**ProductsTableCSV**拖曳到**實驗畫布**上。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-16.png)

4.  在左側面板中，展開 [**資料轉換**] > **範例和 [分割**]。 然後將 [**分割資料**] 專案拖曳至**實驗畫布**。 分割資料項目會將資料集分割成兩個部分。 您將用來訓練機器學習服務演算法的其中一個部分。 第二個部分將用來評估產生之演算法的精確度。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-17.png)

5.  在右面板中（當選取畫布上的 [分割資料項目] 時），將**第一個輸出資料集中的資料列分數**編輯為**0.7**。 這會將資料分割成兩個部分，第一個部分將是70% 的資料，而第二個部分將是剩餘的30%。 若要確保資料會隨機分割，請確定 [**隨機分割**] 核取方塊保持核取狀態。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-18.png)

6.  將畫布上 [ **ProductsTableCSV** ] 專案基底的連接拖曳至 [分割] 資料項目的頂端。 這會連接專案，並將**ProductsTableCSV**資料集輸出（資料）傳送至分割資料輸入。  

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-19.png)

7.  在左側的 **實驗** 面板中，展開  **Machine Learning**  > **訓練**。 將**訓練模型**專案向外拖曳至實驗畫布。 您的畫布看起來應該與下面相同。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-20.png)

8.  從 [**分割資料項目**] 的***左下方***，將 [連接] 拖曳至 [**定型模型**] 專案的**右上**角。 定型模型會使用從資料集分割的第一個70% 來定型演算法。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-21.png)

9.  選取畫布上的 [**定型模型**] 專案，然後在 [**屬性**] 面板（位於瀏覽器視窗右側）中，按一下 [**啟動資料行選取器**] 按鈕。

10. 在文字方塊中輸入**product** ，然後按**enter**鍵， *product*將會設定為數據行來定型預測。 在此之後，按一下右下角的**滴答**，關閉選取對話方塊。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-22.png)

11. 您將訓練**多元羅吉斯回歸**演算法，根據一天中的一小時和日期來預測最銷售的**產品**。 這不在本檔的討論範圍內，以說明 Azure Machine Learning studio 所提供之不同演算法的詳細資料，但您可以從[Machine Learning 演算法](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)功能提要中深入瞭解

12. 從左側的 [實驗專案] 面板中，展開 [ **Machine Learning** ] > [**初始化模型** > **分類**]，然後將 [**多元羅吉斯回歸**] 專案拖曳至實驗畫布。

13. 將輸出從**多元羅吉斯回歸**的底部，連接到**訓練模型**專案的左上角輸入。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-23.png)

14. 在左側面板中的實驗專案清單中，展開 [ **Machine Learning** ] > [**分數**]，然後將 [**評分模型**] 專案拖曳到畫布上。

15. 將輸出從**訓練模型**的底部，連接到**評分模型**的左上角輸入。

16. 將 [**分割資料**] 的右下方輸出連接到 [**評分模型**] 專案的右上方輸入。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-24.png)

17. 在左側面板中的**實驗**專案清單中，展開  **Machine Learning**  > **評估**，然後將 **評估模型** 專案拖曳到畫布上。

18. 將**評分模型**的輸出連接到**評估模型**的左上角輸入。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-25.png)

19. 您已經建立您的第一個 Machine Learning 實驗。 您現在可以儲存並執行實驗。 在頁面底部的功能表中，按一下 [**儲存**] 按鈕以儲存您的實驗，然後按一下 [**執行**] 以啟動實驗。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-26.png)

20. 您可以在畫布右上角查看實驗的**狀態**。 請稍候片刻，讓實驗完成。

    > 如果您有大型（實際）的資料集，可能是實驗需要數小時才會執行。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-27.png)

21. 以滑鼠右鍵按一下畫布中的 [**評估模型**] 專案，然後從內容功能表中，將滑鼠停留在 [**評估結果**] 上，然後選取 [**視覺化**]。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-28.png)

22. 將會顯示評估結果，顯示預測的結果與實際結果。 這會使用先前分割的原始資料集30% 來評估模型。 您可以看到結果並不大，在理想的情況下，每個資料列中的最大數目就是資料行中反白顯示的專案。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-29.png)

23. 關閉**結果**。

24. 若要使用您剛定型的 Machine Learning 模型，您必須將它公開為**Web 服務**。 若要這樣做，請在頁面底部的功能表中按一下 [**設定 Web 服務**] 功能表項目，然後按一下 [預測性**Web 服務**]。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-30.png)

25. 將建立新的索引標籤，併合並定型模型來建立新的 web 服務。 

26. 在頁面底部的功能表中，按一下 [**儲存**]，然後按一下 [**執行**]。 您會在實驗畫布右上角看到更新的狀態。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-31.png)

27. 完成執行後，[**部署 Web 服務**] 按鈕將會出現在頁面底部。 您已準備好部署 web 服務。 在頁面底部的功能表中，按一下 [**部署 Web 服務**（傳統）]。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-32.png)

    > 您的瀏覽器可能會提示您允許快顯視窗，這是您應該**允許**的，但如果 [部署] 頁面未顯示，您可能需要再次按下 [**部署 Web 服務**]。 

28. 建立實驗之後，您會被重新導向至**儀表板**頁面，其中會顯示您的**API 金鑰**。 將它複製到「記事本」，很快就會在您的程式碼中需要它。 記下 API 金鑰之後，請按一下金鑰底下 [**預設端點**] 區段中的 [**要求/回應**] 按鈕。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > 如果您按一下此頁面中的 [測試]，您將能夠輸入輸入資料並查看輸出。 輸入 [**日**] 和 [**小時**]。 將 [**產品**] 專案保留空白。 然後按一下 [**確認**] 按鈕。 頁面底部的輸出會顯示 JSON，代表每個產品的可能性。

29. 隨即會開啟新的網頁，並顯示有關 Machine Learning Studio 所需之要求結構的指示和一些範例。 將此頁面中顯示的**要求 URI**複製到您的 [記事本]。

    ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-34.png)

您現在已建立機器學習系統，以根據歷程記錄購買資料，提供最有可能的產品銷售，並與一年中的一天和一天的時間產生關聯。

若要呼叫 web 服務，您將需要服務端點的 URL 和服務的 API 金鑰。 按一下頂端功能表中的 [**取用] 索引**標籤。

[**耗用量**資訊] 頁面將會顯示您從程式碼呼叫 web 服務時所需的資訊。 請複製**主要金鑰**和**要求-回應**URL。 您將在下一章中需要這些功能。

## <a name="chapter-5---setting-up-the-unity-project"></a>第5章-設定 Unity 專案

設定和測試混合現實的沉浸式耳機。

> [!NOTE]
>  在此課程中，您將**不**需要有動作控制器。 如果您需要支援設定沉浸式頭戴式裝置，請按一下[這裡](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  開啟**Unity** ，並建立名為**MR\_MachineLearning**的新 unity 專案。 請確定 [專案類型] 設定為 [ **3d**]。

2.  在 Unity 開啟的情況下，值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 **編輯** > **喜好**設定，然後在新視窗中，流覽至 **外部工具**。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

3.  接著，移至 [檔案] > [**組建設定**]，然後按一下 [***切換平臺***] 按鈕 **，將平臺**切換至**通用 Windows 平臺**。

4.  也請確定：

    1.  [**目標裝置**] 已設定為 [**任何裝置**]。

        > 若為 Microsoft HoloLens，請將**目標裝置**設定為*HoloLens*。

    2.  [**組建類型**] 設定為 [ **D3D**]。

    3.  **SDK**設定為 [**最新安裝**]。

    4.  **Visual Studio 版本**設定為 [**最新安裝**]。

    5.  [**組建與執行**] 設定為 [**本機電腦**]。

    6.  請不要擔心立即設定**場景**，因為稍後會提供這些資訊。

    7.  其餘的設定現在應保留為預設值。

        ![設定 Unity 專案](images/AzureLabs-Lab7-35.png)

5.  在 [**組建設定**] 視窗中，按一下 [ **Player 設定**] 按鈕，這會在偵測**器**所在的空間中開啟相關的面板。 

6. 在此面板中，需要驗證幾項設定：

    1.  在 [**其他設定**] 索引標籤中：

        1.  **腳本** **執行階段版本**應該是**實驗**性（.net 4.6 對等用法）

        2. **腳本後端**應該是 ***.net***

        3. **API 相容性層級**應該是 **.net 4.6**

            ![設定 Unity 專案](images/AzureLabs-Lab7-36.png)

    2.  在 [**發行設定**] 索引標籤的 [**功能**] 底下，檢查：

        - **InternetClient**

            ![設定 Unity 專案](images/AzureLabs-Lab7-37.png)

    3.  在面板中，于 [ **XR 設定**] （在 [**發佈設定**] 下方找到）中，支援 [勾選**虛擬實境**]，並確定已新增 [ **Windows Mixed Reality SDK** ]

        ![設定 Unity 專案](images/AzureLabs-Lab7-38.png)

    

6.  回到**組建設定** *Unity C#* 專案已不再呈現灰色;勾選 [] 旁的核取方塊。 

7.  關閉 [組建設定] 視窗。

8.  儲存您的專案（檔案 **> 儲存專案**）。

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>第6章-匯入 MLProducts Unity 封裝

在此課程中，您將需要下載名為[**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)的 Unity 資產套件。 此套件隨附于場景，所有物件都在該預先建立中，因此您可以專注于讓它運作。 由於場景安裝結構的目的，我們會提供**ShelfKeeper**腳本，但只會保存公用變數。 您將需要執行所有其他區段。 

若要匯入此封裝：

1.  在您前方的 Unity 儀表板中，按一下畫面頂端功能表中的 [**資產**]，然後按一下 [匯**入套件]、[自訂套件**]。

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-39.png)

2.  使用檔案選擇器選取**unitypackage**套件，然後按一下 [**開啟**]。

3.  系統會顯示此資產的元件清單。 按一下 [匯**入**] 確認匯入。

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-40.png)

4.  完成匯入之後，您會發現 Unity**專案面板**中出現一些新的資料夾。 這些是3D 模型，也是您將使用之預先製作場景中的個別材質。 在此課程中，您將會撰寫大部分的程式碼。

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-41.png)

5.  在 [**專案面板**] 資料夾中，按一下 [**場景**] 資料夾，然後按兩下內的場景（稱為**MR_MachineLearningScene**）。 場景隨即開啟（請參閱下圖）。 如果缺少紅色菱形，只要按一下**遊戲面板**右上方的 [ **Gizmos** ] 按鈕即可。

    ![匯入 MLProducts Unity 封裝](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>第7章-檢查 Unity 中的 Dll

若要利用 JSON 程式庫（用於序列化和還原序列化），已使用您帶入的封裝來執行 Newtonsoft DLL。 程式庫應具有正確的設定，但值得檢查（尤其是如果您有程式碼無法運作的問題）。 

若要這樣做：

-  以滑鼠左鍵按一下 [外掛程式] 資料夾內的 Newtonsoft 檔案，然後查看 [**檢查] 面板**。 請確定已核取**任何平臺**。 移至 [ **UWP]** 索引標籤，並確定 [**不核取處理**]。

    ![匯入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>第8章-建立 ShelfKeeper 類別

**ShelfKeeper**類別裝載的方法，可控制在場景中衍生的 UI 和產品。

在匯入的套件中，您將會獲得這個類別，但它不完整。 現在是完成該類別的時機：

1.  按兩下 [**腳本**] 資料夾中的**ShelfKeeper**腳本，以**Visual Studio 2017**開啟它。

2.  將腳本中現有的所有程式碼取代為下列程式碼，這會設定時間和日期，並具有可顯示產品的方法。

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

3.  請務必先將您的變更儲存在**Visual Studio**中，然後再返回**Unity**。

4.  回到 Unity 編輯器，檢查**ShelfKeeper**類別看起來如下所示：

    ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > 如果您的腳本沒有參考目標（也就是*日期（文本網格）* ），只需從 [階層]**面板**將對應的物件拖曳至目標欄位。 如需說明，請參閱以下內容：
    > 
    > 1.  在**ShelfKeeper**元件腳本中，以滑鼠左鍵按一下產生**點**陣列，以開啟它。 子區段會顯示稱為「**大小**」，表示陣列的大小。 在 [**大小**] 旁的文字方塊中輸入**3** ，然後按**enter**鍵，下方會建立三個位置。
    > 2. **在階層中展開**[**時間顯示**] 物件（以滑鼠左鍵按一下其旁邊的箭號）。 接著，按一下階層內的***主要攝影機*** **，讓**偵測**器**顯示其資訊。
    > 3. 在 [階層]**面板**中選取**主要相機**。 從 [階層]**面板**中，將 [**日期**] 和 [**時間**] 物件拖曳至**ShelfKeeper**元件中**主要攝影機**的偵測**器**內的**日期文字**和**時間文字**位置。
    > 4. 將 [階層]**面板**中的 [產生**點**] （在 [*貨位*] 物件下方）拖曳至 [**衍生點**] 陣列底下的**3**個**專案參考目標**，如影像中所示。
    > 
    >     ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>第9章-建立 ProductPrediction 類別

下一個您即將建立的類別是**ProductPrediction**類別。

此類別負責：

-   查詢**Machine Learning 的服務**實例，並提供目前的日期和時間。

-   將 JSON 回應還原序列化為可用的資料。

-   解讀資料，並抓取3個建議的產品。

-   呼叫**ShelfKeeper**類別方法，以顯示場景中的資料。

若要建立此類別：

1.  移至 [**專案] 面板**中的 [**腳本**] 資料夾。

2.  以滑鼠右鍵按一下資料夾內的 [**建立** >  **C#腳本**]。 呼叫腳本**ProductPrediction**。

3.  按兩下新的**ProductPrediction**腳本，以**Visual Studio 2017**開啟它。

4.  如果出現 [偵測**到檔案修改**] 對話方塊，請按一下 [**重載解決方案**]。

5.  將下列命名空間新增至 ProductPrediction 類別的頂端：

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

6.  在**ProductPrediction**類別中，插入下列兩個由多個嵌套類別所組成的物件。 這些類別是用來序列化和還原序列化 Machine Learning 服務的 JSON。

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

7.  然後，在先前的程式碼上方加入下列變數（如此一來，JSON 相關程式碼就會在腳本的底部、所有其他程式碼之下，以及從外）：

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
    > 請務必將 [**主要金鑰**] 和 [**要求-回應] 端點**從 Machine Learning 入口網站插入此處的變數。 下列影像顯示您從何處取得金鑰和端點。 
    >  
    > ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio：實驗](images/AzureLabs-Lab7-53-2.png)

8.  將此程式碼插入**Start （）** 方法中。 當類別初始化時，會呼叫**Start （）** 方法：

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

9.  以下是從 Windows 收集日期和時間的方法，並將它轉換成 Machine Learning 實驗可用來與資料表中所儲存資料進行比較的格式。

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

10. 您可以**刪除** **Update （）** 方法，因為這個類別不會使用它。

11. 新增下列方法，這會將目前的日期和時間傳達給 Machine Learning 端點，並以 JSON 格式接收回應。

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

12. 新增下列方法，這會負責將 JSON 回應還原序列化，以及將還原序列化的結果與**ShelfKeeper**類別通訊。 此結果會是預測為目前日期和時間銷售最大的三個專案的名稱。 將下列程式碼插入**ProductPrediction**類別的先前方法底下。

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

13. 儲存**Visual Studio**並返回**Unity**。

14. 將 [ **ProductPrediction**類別] 腳本從 [**腳本**] 資料夾拖曳到**主要相機**物件上。

15. 儲存場景和專案**檔** > **儲存場景/** 檔案 > **儲存專案**。

## <a name="chapter-10---build-the-uwp-solution"></a>第10章-建立 UWP 解決方案

現在可以將您的專案建立成 UWP 解決方案，使其可以獨立應用程式的形式執行。

若要建立：

1.  按一下 [檔案 **] > ** **儲存**場景，以儲存目前的場景。

2.  移至**檔案** > **組建設定**

3.  選取名為 [ **Unity C#專案**] 的方塊（這很重要，因為它可讓您在組建完成後編輯類別）。

4.  按一下 [**新增開啟的場景**]，

5.  按一下 [建置]。

    ![建立 UWP 解決方案](images/AzureLabs-Lab7-54.png)

6.  系統會提示您選取要在其中建立解決方案的資料夾。

7.  建立**組建**資料夾，並在該資料夾內建立另一個資料夾，並使用您選擇的適當名稱。

8.  按一下您的新資料夾，然後按一下 [**選取資料夾**]，在該位置開始組建。

    ![建立 UWP 解決方案](images/AzureLabs-Lab7-55.png)

    ![建立 UWP 解決方案](images/AzureLabs-Lab7-56.png)

9.  Unity 完成建立之後（可能需要一些時間），它會在組建的位置開啟 [檔案**瀏覽器**] 視窗（請檢查您的工作列，因為它不一定會出現在視窗的上方，但會通知您加入新的視窗）。

## <a name="chapter-11---deploy-your-application"></a>第11章-部署您的應用程式

若要部署您的應用程式：

1.  流覽至新的 Unity 組建（**應用程式**資料夾），然後使用**Visual Studio**開啟方案檔。

2.  在 Visual Studio 開啟的情況下，您需要還原 NuGet 套件，您可以在 MachineLearningLab_Build 解決方案上按一下滑鼠右鍵，從 [方案總管] （在 [Visual Studio] 右邊），然後按一下 [還原 NuGet 套件] 來完成：

    ![新增 NuGet 套件](images/AzureLabs-Lab7-57.png)

3.  在 [解決方案設定] 中，選取 [ **Debug**]。

4.  在解決方案平臺中，選取 [ **x86**]、[**本機電腦**]。 

    > 針對 Microsoft HoloLens，您可能會發現將此設定為 [*遠端電腦*] 比較容易，因此您不會行動網卡到電腦。 不過，您也必須執行下列動作：
    > - 知道您的 HoloLens 的**IP 位址**，您可以在 *> Network & Internet > Wi-fi > Advanced 選項*的 [設定] 中找到它;IPv4 是您應該使用的位址。 
    > - 請確定**開發人員模式**已**開啟**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >* 。

    ![新增 NuGet 套件](images/AzureLabs-Lab7-58.png)

5.  移至 [**建立] 功能表**，然後按一下 [**部署方案**]，將應用程式側載至您的電腦。

6.  您的應用程式現在應該會出現在已安裝的應用程式清單中，並準備好啟動。

當您執行 Mixed Reality 應用程式時，您會看到在 Unity 場景中設定的工作臺，而從初始化開始，將會提取您在 Azure 中設定的資料。 資料將會在您的應用程式中還原序列化，而目前日期和時間的三個最上層結果將以視覺化方式提供，做為工作臺上的三個模型。


## <a name="your-finished-machine-learning-application"></a>您完成的 Machine Learning 應用程式
 
恭喜，您建立了一個混合現實應用程式，利用 Azure Machine Learning 來進行資料預測，並將它顯示在您的場景上。

![新增 NuGet 套件](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>練習

**練習1**

請試驗您應用程式的排序次序，並將三個底部的預測顯示在貨架上，因為這項資料可能也會很有用。

**練習2**

使用**Azure 資料表**會在新資料表中填入氣象資訊，並使用該資料建立新的實驗。
