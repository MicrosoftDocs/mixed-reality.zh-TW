---
title: MR 和 Azure 303-自然語言理解（LUIS）
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure Language Understanding 智慧服務（LUIS）。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合現實，學術，unity，教學課程，api，語言理解智慧服務，luis，hololens，沉浸，vr
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926810"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時，使用這些教學課程的連結進行更新。

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR 和 Azure 303：自然語言理解（LUIS）

在此課程中，您將瞭解如何使用 Azure 認知服務搭配 Language Understanding API，將 Language Understanding 整合到混合的現實應用程式中。

![實驗室結果](images/AzureLabs-Lab3-000.png)

*Language Understanding （LUIS）* 是一項 Microsoft Azure 的服務，可讓應用程式從使用者輸入中實現意義，例如，藉由以自己的單字來解壓縮個人可能想要的內容。 這是透過機器學習來達成，這會瞭解並學習輸入資訊，然後可以使用詳細的相關資訊來回複。 如需詳細資訊，請造訪[Azure Language Understanding （LUIS）頁面](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。

完成此課程之後，您將擁有一個混合現實的沉浸式耳機應用程式，其將能夠執行下列動作：

1.  使用連接到沉浸式耳機的麥克風來捕捉使用者輸入語音。 
2.  將已捕獲的聽寫傳送至*Azure Language Understanding 智慧型服務*（*LUIS*）。 
3.  讓 LUIS 從傳送資訊中解壓縮意義，這將會進行分析，並嘗試判斷使用者的要求意圖。

開發會包含應用程式的建立，讓使用者能夠使用語音和/或注視來變更場景中物件的大小和色彩。 將不會涵蓋使用動作控制器。

在您的應用程式中，您可以決定如何將結果與您的設計整合。 本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。 您的工作是使用您從這個課程取得的知識，來增強您的混合現實應用程式。

準備好訓練 LUIS 數次，如第[12 章](#chapter-12--improving-your-luis-service)所述。 您會得到更好的結果，也就是 LUIS 已定型的次數。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 和 Azure 303：自然語言理解（LUIS）</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然此課程主要著重于 Windows Mixed Reality 沉浸式（VR）耳機，但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。 隨著課程的遵循，您會看到您可能需要用來支援 HoloLens 的任何變更的附注。 使用 HoloLens 時，您可能會在語音捕獲期間發現一些回應。

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。 也請注意，本檔中的必要條件和書面指示，代表在撰寫本文時已測試和驗證的內容（5月2018）。 您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體，但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容，而不是如下所示。

在此課程中，我們建議您採用下列硬體和軟體：

- [與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦，可用於沉浸式（VR）耳機開發
- [已啟用開發人員模式的 Windows 10 秋季建立者更新（或更新版本）](install-the-tools.md)
- [最新的 Windows 10 SDK](install-the-tools.md)
- [Unity 2017。4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- 已啟用開發人員模式的[Windows Mixed Reality 沉浸（VR）耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 一組具有內建麥克風的耳機（如果耳機沒有內建的 mic 和喇叭）
- 適用于 Azure 設定和 LUIS 抓取的網際網路存取

## <a name="before-you-start"></a>開始之前

1.  為避免在建立此專案時發生問題，強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案（長資料夾路徑可能會在組建階段造成問題）。 
2.  若要允許您的電腦啟用聽寫，請移至**Windows 設定 > 隱私權 > 語音，筆跡 & 輸入**，然後按下 [**開啟語音服務] 按鈕並輸入建議**。
3.  本教學課程中的程式碼可讓您從電腦上的**預設麥克風裝置**設定記錄。 請確定預設的麥克風裝置已設定為您要用來捕捉語音的裝置。
4.  如果您的耳機有內建的麥克風，請確定已在*Mixed Reality 入口網站*設定中開啟 [*當我戴耳機，切換到耳機 mic]* 選項。

    ![設定沉浸式頭戴式裝置](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>第1章–設定 Azure 入口網站

若要在 Azure 中使用*Language Understanding*服務，您將需要設定服務的實例，讓應用程式可以使用。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程，請洽詢您的講師或其中一個 proctors，以協助設定您的新帳戶。

2.  登入之後，按一下左上角的 [**新增**]，並搜尋*Language Understanding*，然後按一下**Enter 鍵**。 

    ![建立 LUIS 資源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > 在較新的入口網站中，**新**的「可能」已取代為「**建立資源**」。
 
3.  右側的新頁面將會提供 Language Understanding 服務的描述。 在此頁面的左下方，選取 [**建立**] 按鈕，以建立此服務的實例。

    ![LUIS 服務建立-法律注意事項](images/AzureLabs-Lab3-02.png)
 
4.  當您按一下 [建立] 之後：

    1. 為此服務實例插入您想要的**名稱**。
    2. 選取**訂**用帳戶。
    3. 選取適合您的**定價層**，如果這是您第一次建立*LUIS 服務*，您應該可以使用免費層（名為 F0）。 在此課程中，免費配置應該就夠多了。
    4. 選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務（例如這些課程）都保留在通用資源群組下）。 

        > 如果您想要深入瞭解 Azure 資源群組，請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 判斷資源群組的**位置**（如果您要建立新的資源群組）。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于特定區域。
    6. 您也必須確認您已瞭解適用于此服務的條款及條件。
    7. 選取 **\[建立\]** 。

        ![建立 LUIS 服務-使用者輸入](images/AzureLabs-Lab3-03.png)
 
5.  按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。
6.  建立服務實例之後，入口網站中會出現通知。 
 
    ![新增 Azure 通知映射](images/AzureLabs-Lab3-04.png)

7.  按一下通知以探索新的服務實例。

    ![成功建立資源通知](images/AzureLabs-Lab3-05.png)
 
8.  按一下通知中的 [**移至資源**] 按鈕，探索新的服務實例。 您將會進入新的 LUIS 服務實例。 
 
    ![存取 LUIS 金鑰](images/AzureLabs-Lab3-06.png)

9.  在本教學課程中，您的應用程式將需要呼叫您的服務，這會透過使用您服務的訂用帳戶金鑰來完成。
10. 從*LUIS API*服務的 [*快速入門*] 頁面，流覽至第一個步驟，*抓取您的金鑰*，然後按一下 [**金鑰**] （您也可以按一下位於 [服務] 導覽功能表中的藍色超連結鍵，以按鍵圖示表示）來達成此目的。 這會顯示您的服務*金鑰*。
11. 複製其中一個顯示的金鑰，因為您稍後會在專案中用到。 
12. 在 [*服務*] 頁面中，按一下 [ *Language Understanding 入口網站*]，將其重新導向至您將用來在 LUIS 應用程式中建立新服務的網頁。 

## <a name="chapter-2--the-language-understanding-portal"></a>第2章– Language Understanding 入口網站

在本節中，您將瞭解如何在 LUIS 入口網站上建立 LUIS 應用程式。 

> [!IMPORTANT]
> 請注意，在本章中設定*實體*、*意圖*和*語句*，只是建立 LUIS 服務的第一步：您也需要重新定型服務數次，讓它更準確。 本課程的[最後一章](#chapter-12--improving-your-luis-service)涵蓋重新定型您的服務，因此請確定您已完成。

1.  到達*Language Understanding 入口網站*時，您可能需要登入（如果您尚未這麼做），其認證與您的 Azure 入口網站相同。 

    ![LUIS 登入頁面](images/AzureLabs-Lab3-07.png)
 
2.  如果這是您第一次使用 LUIS，您將需要向下滾動到歡迎頁面底部，以尋找並按一下 [**建立 LUIS 應用程式**] 按鈕。

    ![建立 LUIS 應用程式頁面](images/AzureLabs-Lab3-08.png)
 
3.  登入之後，按一下 [**我的應用程式**] （如果您目前不在該區段中）。 然後，您可以按一下 [**建立新的應用程式**]。

    ![LUIS-我的應用程式影像](images/AzureLabs-Lab3-09.png)
 
4.  提供您的應用程式*名稱*。
5.  如果您的應用程式應該瞭解與英文不同的語言，您應該將*文化*特性變更為適當的語言。
6.  您也可以在這裡新增新 LUIS 應用程式的*描述*。

    ![LUIS-建立新的應用程式](images/AzureLabs-Lab3-10.png)

7.  當您按下 [**完成**] 之後，您將會進入新*LUIS*應用程式的 [*組建*] 頁面。
8.  這裡有幾個重要的概念需要瞭解：

    -   *意圖*：代表將在使用者的查詢之後呼叫的方法。 *意圖*可能會有一或多個*實體*。
    -   *實體*是查詢的元件，可描述與*意圖*相關的資訊。
    -   *語句*是開發人員所提供的查詢範例，LUIS 會用它來訓練自己。

如果這些概念並非完全清楚，請別擔心，因為本課程將在本章中進一步說明。

您將從建立此課程所需的*實體*開始。

9.  在頁面的左側，按一下 [*實體*]，然後按一下 [**建立新實體**]。

    ![建立新實體](images/AzureLabs-Lab3-11.png)

10. 呼叫新的實體*色彩*，將其類型設定為 [*簡單*]，然後按 [**完成**]。

    ![建立簡單的實體色彩](images/AzureLabs-Lab3-12.png)
 
11. 重複此程式以建立三個（3）個更簡單的實體，名為：

    -   *升遷*
    -   *縮減*
    -   *設定*

結果看起來應該如下圖所示：

![建立實體的結果](images/AzureLabs-Lab3-13.png)
 
此時您可以開始建立*意圖*。 

> [!WARNING]
> 請勿刪除 [**無**] 意圖。

12. 在頁面的左側，按一下 [**意圖**]，然後按一下 [**建立新的意圖**]。

    ![建立新意圖](images/AzureLabs-Lab3-14.png)

13. 呼叫新的*意圖* **ChangeObjectColor**。

    > [!IMPORTANT]
    > 此*意圖*名稱會在本課程稍後的程式碼中使用，因此若要獲得最佳結果，請依照所提供的方式使用此名稱。

一旦您確認名稱，系統就會將您導向至 [意圖] 頁面。

![LUIS-意圖頁面](images/AzureLabs-Lab3-15.png)

您會發現有一個文字方塊要求您輸入5個或更多不同的*語句*。

> [!NOTE]
> LUIS 會將所有語句轉換成小寫。

14. 在頂端的文字方塊中插入下列*語句*（目前有*大約5個範例*的文字類型 。 ），然後按**enter**鍵：

```
The color of the cylinder must be red
```

您會注意到新的*語句*會出現在下面的清單中。

遵循相同的程式，插入下列六個（6）語句：

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

針對您已建立的每個語句，您必須識別 LUIS 要使用哪些單字做為實體。 在此範例中，您必須將所有色彩標記為*色彩*實體，並將目標的所有可能參考標示為*目標*實體。

15. 若要這麼做，請嘗試在第一個語句中按一下 [*圓柱*]，然後選取 [*目標*]。

    ![識別語句目標](images/AzureLabs-Lab3-16.png)
 
16. 現在按一下第一個語句中的*紅色*文字，然後選取 [*色彩*]。

    ![識別語句的實體](images/AzureLabs-Lab3-17.png)
 
17. 為下一行加上標籤，其中*cube*應該是*目標*，而*黑色*則應該是*色彩*。 也請注意，我們所提供的「 *this*」、「 *it*」和「 *this object*」這幾個字，因此也有非特定的目標型別可供使用。 

18. 重複上述程式，直到所有語句都已標示實體為止。 如果您需要協助，請參閱下圖。

    > [!TIP]
    > 選取字詞以將其標示為實體時：
    > - 針對單一字組，只要按一下即可。
    > - 針對一組二或多個單字，按一下開頭，然後在集合結尾處。

    > [!NOTE]
    > 您可以使用 [*權杖] 視圖*切換按鈕，在**實體/標記視圖**之間切換！

19. 結果應如下圖所示，其中顯示 [**實體/權杖] 視圖**：

    ![& 實體視圖的權杖](images/AzureLabs-Lab3-18.png)
  
20. 此時，請按頁面右上方的 [**定型**] 按鈕，然後等候小型的圓角指標變成綠色。 這表示已成功訓練 LUIS 以辨識此意圖。

    ![訓練 LUIS](images/AzureLabs-Lab3-19.png)
 
21. 做為您的練習，使用實體*target*、*升遷*和*縮減*，建立名為**ChangeObjectSize**的新意圖。
22. 遵循與上一個意圖相同的程式，插入下列八個（8）語句以進行*大小*變更：

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. 結果應如下圖所示：

    ![設定 ChangeObjectSize token/實體](images/AzureLabs-Lab3-20.png) 

24. 當意圖、 **ChangeObjectColor**和**ChangeObjectSize**都已建立並定型之後，請按一下頁面頂端的 [**發佈**] 按鈕。

    ![發行 LUIS 服務](images/AzureLabs-Lab3-21.png)

25. 在 [*發佈*] 頁面上，您將會完成併發布您的 LUIS 應用程式，讓您的程式碼可以存取它。

    1. 將下拉式*發行*設定為 [**生產**]。
    2. 將*時區*設定為您的時區。
    3. 勾選 [**包含所有預測的意圖分數**] 方塊。
    4. 按一下 [**發佈至生產**位置]。

        ![發行設定](images/AzureLabs-Lab3-22.png)

26. 在 [*資源和金鑰*] 區段中：

    1.  選取您在 Azure 入口網站中為服務實例設定的區域。
    2.  您會注意到下列**Starter_Key**元素，請予以忽略。
    3.  按一下 [**新增金鑰**]，並插入當您建立服務實例時，在 Azure 入口網站中取得的*金鑰*。 如果您的 Azure 和 LUIS 入口網站已登入相同的使用者，您將會在*租使用者名稱*、訂用帳戶*名稱*和您想要使用的*金鑰*（將與您先前在 Azure 入口網站中提供的名稱相同）中提供下拉式功能表。

    > [!IMPORTANT] 
    > 在 [*端點*] 下方，建立對應至所插入金鑰的端點複本，您很快就會在程式碼中使用它。
 
## <a name="chapter-3--set-up-the-unity-project"></a>第3章–設定 Unity 專案

以下是使用混合現實進行開發的一般設定，因此是適用于其他專案的絕佳範本。

1.  開啟*Unity* ，然後按一下 [**新增**]。 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab3-24.png)

2.  現在您將需要提供 Unity 專案名稱、插入**MR_LUIS**。 請確定 [專案類型] 設定為 [ **3d**]。 將位置設定為適合您的**位置**（請記住，接近根目錄較佳）。 然後，按一下 [**建立專案**]。

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab3-25.png)
 
3.  在 Unity 開啟的情況下，值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 編輯 > 喜好設定，然後在新視窗中，流覽至 **外部工具**。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab3-26.png)
 
4.  接著，移至 [檔案] **> [組建設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至**通用 Windows 平臺**。

    ![[組建設定] 視窗，將平臺切換至 UWP。](images/AzureLabs-Lab3-27.png)
 
5.  移至 [檔案] **> [組建設定**]，並確認：

    1. **目標裝置**已設定為**任何裝置**

        > 若為 Microsoft HoloLens，請將**目標裝置**設定為*HoloLens*。

    2. **組建類型**設定為**D3D**
    3. **SDK**已設定為**最新安裝**
    4. **Visual Studio 版本**設定為 [**最新安裝**]
    5. **組建和執行**設定為**本機電腦**
    6. 儲存場景，並將它加入至組建。

        1. 選取 [新增] [**開啟場景**] 來執行此動作。 [儲存] 視窗隨即出現。
        
            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab3-28.png)

        2. 為此建立新的資料夾，並在任何未來的場景中選取 [**新增資料夾**] 按鈕，以建立新的資料夾，將其命名為**場景**。

            ![建立新的腳本資料夾](images/AzureLabs-Lab3-29.png)

        3. 開啟新建立的 [**幕後**] 資料夾，然後在 [*檔案名*：文字] 欄位中輸入**MR_LuisScene**，然後按 [**儲存**]。

            ![為新場景指定名稱。](images/AzureLabs-Lab3-30.png)

    7. [*組建設定*] 中的其餘設定，現在應該保留為預設值。

6. 在 [*組建設定*] 視窗中，按一下 [ **Player 設定**] 按鈕，這會在偵測*器*所在的空間中開啟相關的面板。 

    ![開啟 [播放] [設定]。](images/AzureLabs-Lab3-31.png) 
 
7. 在此面板中，需要驗證幾項設定：

    1. 在 [**其他設定**] 索引標籤中：

        1. **腳本執行階段版本**應為**穩定**（.net 3.5 對等）。
        2. **腳本後端**應該是 **.net**
        3. **API 相容性層級**應該是 **.net 4.6**

            ![更新其他設定。](images/AzureLabs-Lab3-32.png)
      
    2. 在 [**發行設定**] 索引標籤的 [**功能**] 底下，檢查：

        1. **InternetClient**
        2. **十分**

            ![正在更新發行設定。](images/AzureLabs-Lab3-33.png)

    3. 在面板中，于 [ **XR 設定**] （在 [**發佈設定**] 下方找到）中，支援 [勾選**虛擬實境**]，並確定已新增 [ **Windows Mixed Reality SDK** ]。

        ![更新 X R 設定。](images/AzureLabs-Lab3-34.png)

8.  回到*組建設定* _Unity C#_ 專案已不再呈現灰色;勾選 [] 旁的核取方塊。 
9.  關閉 [組建設定] 視窗。
10. 儲存場景和專案（**file > 儲存場景/檔案 > 儲存專案**）。

## <a name="chapter-4--create-the-scene"></a>第4章–建立場景

> [!IMPORTANT]
> 如果您想要略過此課程的*Unity 設定*元件，並繼續直接進入程式碼，您可以下載這個[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，將它匯入到您的專案中做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行[第5章](#chapter-5--create-the-microphonemanager-class)。 

1.  以滑鼠右鍵按一下 [階層]*面板*的空白區域，然後在 [ **3d 物件**] 下加入**平面**。

    ![建立平面。](images/AzureLabs-Lab3-35.png)

2.  請注意，當*您再次以*滑鼠右鍵按一下階層以建立更多物件時，如果您仍然選取最後一個物件，選取的物件將會是新物件的父系。 請避免這種情況，在階層內的空白處按一下滑鼠左鍵，然後按一下滑鼠右鍵。

3.  重複上述程式來新增下列物件：

    1. *Sphere*
    2. *柱*
    3. *Cube*
    4. *3D 文字*

4.  產生*的場景階層*應如下圖所示：

    ![場景階層設定。](images/AzureLabs-Lab3-36.png)
 
5.  以滑鼠左鍵按一下**主要相機**以選取它，查看 [*檢查] 面板*，您將會看到相機物件及其所有元件。
6.  按一下位於 [偵測*器] 面板*最下方的 [**新增元件**] 按鈕。

    ![新增音訊來源](images/AzureLabs-Lab3-37.png)
 
7.  搜尋稱為「*音訊來源*」的元件，如上所示。
8.  也請確定主要攝影機的 [*轉換*] 元件設定為（0，0，0），只要按下相機*轉換*元件旁的**齒輪**圖示，然後選取 [**重設**] 即可完成。 接著，*轉換*元件看起來應該像這樣：

    1.  *Position*設定為**0，0，0**。
    2.  *旋轉*設定為**0，0，0**。

    > [!NOTE] 
    > 針對 Microsoft HoloLens，您也必須變更下列各項，這是**相機**元件的一部分，位於您的**主要攝影機**上：
    > - **清除旗標：** 單色。
    > - **背景**' 黑色，Alpha 0 ' –十六進位色彩： #00000000。

9.  在**平面**上按一下滑鼠左鍵加以選取。 在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：

    |       | 轉換-*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. 在**球體**上按一下滑鼠左鍵加以選取。 在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：

    |       | 轉換-*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. 在**圓柱**上按一下滑鼠左鍵加以選取。 在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：

    |       | 轉換-*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | -2    | 1                      | 2     |

12. 在**Cube**上按一下滑鼠左鍵加以選取。 在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：

    |        | 轉換-*位置* |       |  \| |       | 轉換-*旋轉* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. 在**新的文字**物件上按一下滑鼠左鍵，加以選取。 在 [偵測*器] 面板*中，使用下列值設定*轉換*元件：

    |       | 轉換-*位置* |       |  \| |       | 轉換-*調整規模* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. 將 [**文字網格**] 元件中的**字型大小**變更為**50**。
15. 將**文本網格**物件的*名稱*變更為 [**聽寫文字**]。

    ![建立3D 文字物件](images/AzureLabs-Lab3-38.png)
 
16. 階層式面板的結構現在看起來應該像這樣：

    ![場景視圖中的文本網格](images/AzureLabs-Lab3-38b.png)


17. 最後的場景看起來應該如下圖所示：

    ![場景視圖。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>第5章–建立 MicrophoneManager 類別

您即將建立的第一個腳本是*MicrophoneManager*類別。 接下來，您將建立*LuisManager*、*行為*類別，最後是*注視*的課程（您可以隨意建立所有這些類別，不過這會在您每一章中討論）。

*MicrophoneManager*類別負責：

-   偵測連接到耳機或電腦的錄製裝置（以何者為預設值）。
-   捕捉音訊（語音）並使用聽寫將其儲存為字串。
-   聲音暫停之後，請將聽寫提交至*LuisManager*類別。 

若要建立此類別： 

1.  以滑鼠右鍵按一下 [*專案] 面板*中的 [**建立 > 資料夾**]。 呼叫資料夾**腳本**。 

    ![建立腳本資料夾。](images/AzureLabs-Lab3-40.png)
 
2.  建立**腳本**資料夾之後，按兩下它以開啟。 然後，在該資料夾中，以滑鼠右鍵按一下 [**建立 > C#腳本**]。 將腳本命名為*MicrophoneManager*。 

3.  按兩下 [ *MicrophoneManager* ]，以*Visual Studio*開啟它。
4.  將下列命名空間新增至檔案頂端：

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  然後，在*MicrophoneManager*類別內新增下列變數：

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  現在必須加入*喚醒（）* 和*Start （）* 方法的程式碼。 當類別初始化時，將會呼叫這些：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  現在您需要應用程式用來啟動和停止語音捕捉的方法，並將它傳遞給*LuisManager*類別，您很快就會建立。 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  新增語音暫停時將叫用的*聽寫處理常式*。 這個方法會將聽寫文字傳遞給*LuisManager*類別。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > 刪除*Update （）* 方法，因為這個類別不會使用它。

9.  請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。

    > [!NOTE]
    > 此時，您會注意到 [ *Unity 編輯器] 主控台面板*中出現錯誤。 這是因為程式碼會參考您將在下一章中建立的*LuisManager*類別。

## <a name="chapter-6--create-the-luismanager-class"></a>第6章–建立 LUISManager 類別

您現在可以建立*LuisManager*類別，這會呼叫 Azure LUIS 服務。 

此類別的目的是要從*MicrophoneManager*類別接收聽寫文字，並將其傳送至要分析的*Azure Language Understanding API* 。

這個類別會將*JSON*回應還原序列化，並呼叫*行為*類別的適當方法來觸發動作。

若要建立此類別： 

1.  按兩下 [**腳本**] 資料夾以開啟它。 
2.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立 > C#腳本**]。 將腳本命名為*LuisManager*。 
3.  按兩下腳本，以 Visual Studio 開啟它。
4.  將下列命名空間新增至檔案頂端：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  首先，您會在*LuisManager*類別**中建立三個類別（** 在相同的腳本檔案中，在*Start （）* 方法的上方），這會代表來自 Azure 的已還原序列化 JSON 回應。

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  接下來，在*LuisManager*類別內新增下列變數：
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  請務必將您的 LUIS 端點放在現在（您將會從 LUIS 入口網站）。

8.  現在必須加入*喚醒（）* 方法的程式碼。 當類別初始化時，會呼叫這個方法：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  現在您需要此應用程式使用的方法，將從*MicrophoneManager*類別收到的聽寫傳送至*LUIS*，然後接收和還原序列化回應。 
10. 一旦決定意圖的值和相關聯的實體之後，就會將其傳遞給*行為*類別的實例，以觸發預期的動作。

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. 建立名為*AnalyseResponseElements （）* 的新方法，它會讀取產生的*AnalysedQuery*並判斷實體。 一旦決定這些實體之後，它們就會傳遞給*行為*類別的實例，以便在動作中使用。

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > 刪除*Start （）* 和*Update （）* 方法，因為這個類別不會使用它們。

12. 請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。

> [!NOTE]
> 此時，您會注意到 [ *Unity 編輯器] 主控台面板*中出現數個錯誤。 這是因為程式碼會參考您將在下一章中建立的*行為*類別。

## <a name="chapter-7--create-the-behaviours-class"></a>第7章–建立行為類別

*行為*類別將會使用*LuisManager*類別所提供的實體來觸發動作。

若要建立此類別： 

1.  按兩下 [**腳本**] 資料夾以開啟它。 
2.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立 > C#腳本**]。 將腳本命名為*行為*。 
3.  按兩下腳本，以*Visual Studio*開啟它。
4.  然後，在*行為*類別內新增下列變數：

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  新增*喚醒（）* 方法程式碼。 當類別初始化時，會呼叫這個方法：

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  下列方法是由*LuisManager*類別（您先前建立的）所呼叫，用來判斷哪個物件是查詢的目標，然後觸發適當的動作。

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  加入*FindTarget （）* 方法，以判斷哪一個*Gameobject*是目前意圖的目標。 如果實體中未定義明確目標，則此方法會將目標預設為 "gazed" 的*GameObject* 。

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > 刪除*Start （）* 和*Update （）* 方法，因為這個類別不會使用它們。

8.  請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。

## <a name="chapter-8--create-the-gaze-class"></a>第8章–建立注視課程

完成此應用程式所需的最後一個類別是*注視*課程。 這個類別會更新目前在使用者視覺焦點中的*GameObject*參考。

若要建立此類別： 

1.  按兩下 [**腳本**] 資料夾以開啟它。 
2.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立 > C#腳本**]。 將腳本命名為*注視*。 
3.  按兩下腳本，以*Visual Studio*開啟它。
4.  為此類別插入下列程式碼：

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。

## <a name="chapter-9--completing-the-scene-setup"></a>第9章–完成場景設定

1.  若要完成場景的設定，請將您在 [腳本] 資料夾中建立的每個腳本，拖曳至 [階層]*面板*中的**主要相機**物件。
2.  選取**主攝影機**並查看 [*檢查器] 面板*，您應該可以看到已附加的每個腳本，而且您會注意到每個尚未設定的腳本都有參數。

    ![設定相機參照目標。](images/AzureLabs-Lab3-41.png)

3.  若要正確設定這些參數，請遵循下列指示：

    1. *MicrophoneManager*：

        - 從 [階層]*面板*中，將 [**聽寫文字**] 物件拖曳至 [**聽寫文字**參數值] 方塊中。

    2. *行為*，從 [階層]*面板*：

        - 將 [**球體**] 物件拖曳至 [*球體*參考目標] 方塊中。
        - 將**圓柱**拖曳至 [*圓柱*參考目標] 方塊中。
        - 將**cube**拖曳至 [ *cube*參考目標] 方塊中。

    3. *注視*：

        - 將 [*注視最大距離*] 設定為**300** （如果尚未這麼做）。 

4.  結果看起來應該如下圖所示：

    ![現在會顯示相機參考目標。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>第10章–在 Unity 編輯器中測試

測試場景設定是否已正確執行。

請確定：

-   所有腳本都會附加到**主要相機**物件。 
-   *主要相機偵測器面板*中的所有欄位都已正確指派。

1.  按下*Unity 編輯器*中的 [**播放**] 按鈕。 應用程式應在附加的沉浸式耳機內執行。

2.  嘗試幾個語句，例如：

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > 如果您在 Unity 主控台看到關於預設音訊裝置變更的錯誤，場景可能無法如預期般運作。 這是因為混合現實入口網站處理具有耳機之內建麥克風的方式。 如果您看到此錯誤，只要停止場景並重新啟動，就應該會如預期般運作。

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>第11章–組建和側載 UWP 解決方案

一旦確定應用程式是在 Unity 編輯器中運作，您就可以開始建立和部署。

若要建立：

1.  按一下 檔案 **> 儲存** 來儲存目前的場景。
2.  移至 [檔案] **> [組建設定**]。
3.  勾選名為 [ **Unity C#專案**] 的方塊（建立 UWP 專案之後，適用于查看和偵錯工具代碼）。
4.  按一下 [**新增] [開啟場景**]，然後按一下 [**建立**]。

    ![組建設定視窗](images/AzureLabs-Lab3-43.png)

4.  系統會提示您選取要在其中建立解決方案的資料夾。 

5.  建立*組建*資料夾，並在該資料夾內建立另一個資料夾，並使用您選擇的適當名稱。 
6.  按一下 [**選取資料夾**]，在該位置開始組建。
 
    ![建立組建資料夾](images/AzureLabs-Lab3-44.png)
    ![選取組建資料夾](images/AzureLabs-Lab3-45.png)
 
7.  Unity 完成建立（可能需要一些時間）之後，它應該會在組建的位置開啟 [檔案**瀏覽器**] 視窗。

若要在本機電腦上部署：

1.  在*Visual Studio*中，開啟在[上一章](#chapter-10--test-in-the-unity-editor)中建立的方案檔。
2.  在**解決方案平臺**中，選取 [ **x86**]、[**本機電腦**]。
3.  在 [**解決方案**設定] 中，選取 [ **Debug**]。

    > 針對 Microsoft HoloLens，您可能會發現將此設定為 [*遠端電腦*] 比較容易，因此您不會行動網卡到電腦。 不過，您也必須執行下列動作：
    > - 知道您的 HoloLens 的**IP 位址**，您可以在 *> Network & Internet > Wi-fi > Advanced 選項*的 [設定] 中找到它;IPv4 是您應該使用的位址。 
    > - 請確定**開發人員模式**已**開啟**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >* 。

    ![部署應用程式](images/AzureLabs-Lab3-46.png)
 
4.  移至 [**建立] 功能表**，然後按一下 [**部署方案**]，將應用程式側載至您的電腦。
5.  您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好啟動！
6.  啟動之後，應用程式會提示您授權存取_麥克風_。 使用 [*動作控制器*] 或 [*語音輸入*]，或*鍵盤*按 [**是]** 按鈕。 

## <a name="chapter-12--improving-your-luis-service"></a>第12章–改善您的 LUIS 服務

>[!IMPORTANT] 
> 這一章非常重要，而且可能需要反復執行幾次，因為這有助於改善 LUIS 服務的精確度：請務必完成這項工作。

若要改善 LUIS 所提供的瞭解層級，您需要捕捉新的語句，並使用它們來重新訓練您的 LUIS 應用程式。

例如，您可能已定型 LUIS 來瞭解「增加」和「升遷」，但您不想讓應用程式也瞭解「放大」之類的字詞嗎？

一旦使用您的應用程式數次，您所說的所有內容都將由 LUIS 收集，並可在 LUIS 入口網站中取得。

1.  遵循此[連結](https://www.luis.ai/home)移至入口網站應用程式，然後登入。
2.  當您使用 MS 認證登入之後，請按一下您的*應用程式名稱*。
3.  按一下頁面左側的 [**審查端點語句**] 按鈕。

    ![審查語句](images/AzureLabs-Lab3-47.png)
 
4.  您將會看到您的混合現實應用程式已傳送給 LUIS 的語句清單。

    ![語句清單](images/AzureLabs-Lab3-48.png)
 
您會發現一些反白顯示的*實體*。 

藉由將滑鼠停留在每個反白顯示的字組上，您可以檢查每個語句，並判斷哪些實體已正確辨識、哪些實體錯誤，以及哪些實體已遺失。

在上述範例中，發現 "魚叉式" 一字已反白顯示為目標，因此必須更正錯誤，這是藉由滑鼠游標停留在該字組上，然後按一下 [**移除標籤**] 來完成。

![檢查語句](images/AzureLabs-Lab3-49.png)
![移除標籤影像](images/AzureLabs-Lab3-50.png)
 
5.  如果您發現完全錯誤的語句，可以使用畫面右側的 [**刪除**] 按鈕將它們刪除。

    ![刪除錯誤的語句](images/AzureLabs-Lab3-51.png)

6.  或者，如果您覺得 LUIS 已正確地解讀語句，您可以使用 [**新增至對齊的意圖**] 按鈕來驗證其理解。

    ![新增至對齊的意圖](images/AzureLabs-Lab3-52.png)

7.  排序所有顯示的語句之後，請嘗試並重載頁面，以查看是否有更多可用的功能。
8.  請務必重複此程式，以改善應用程式的瞭解。 

**玩得愉快！**

## <a name="your-finished-luis-integrated-application"></a>您完成的 LUIS 整合式應用程式

恭喜，您建立了一個混合現實應用程式來運用 Azure Language Understanding 智慧服務，以瞭解使用者所說的內容，並對該資訊採取行動。

![實驗室結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

使用此應用程式時，您可能會注意到，如果您注視 Floor 物件，並要求變更其色彩，它就會這麼做。 您可以處理如何阻止應用程式變更樓層色彩？

### <a name="exercise-2"></a>練習2

嘗試擴充 LUIS 和應用程式功能，為場景中的物件新增額外的功能;例如，根據使用者所說的內容，在看眼點建立新的物件，然後能夠將這些物件與目前的場景物件搭配使用，以及現有的命令。 
