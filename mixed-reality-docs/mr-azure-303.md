---
title: MR 和 Azure 303-自然語言理解 (LUIS)
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure Language Understanding Intelligence Service (LUIS)。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境，academy、 unity、 教學課程、 api、 language understanding intelligence service，luis，hololens 沉浸式 vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595912"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR 和 Azure 303:自然語言理解 (LUIS)

在此課程中，您將了解如何整合 Azure 認知服務，使用 Language Understanding API 的混合的實境應用程式中的 Language Understanding。

![實驗室結果](images/AzureLabs-Lab3-000.png)

*Language Understanding (LUIS)* 是 Microsoft Azure 服務，例如可從使用者輸入的意義，透過擷取功能的人員可能會想，客戶推薦的能力提供應用程式。 這是透過機器學習服務，可了解和學習輸入的資訊，並接著可以回覆詳細、 相關的資訊來達成。 如需詳細資訊，請瀏覽[Azure Language Understanding (LUIS) 頁面](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。

完成本課程之後，您必須能夠執行下列作業的混合的實境耳機沈浸式應用程式：

1.  擷取使用者輸入的語音，使用附加至沈浸式耳機式麥克風。 
2.  傳送擷取的聽寫*Azure Language Understanding Intelligent Service* (*LUIS*)。 
3.  具有 LUIS 擷取表示傳送資訊，就會分析，並嘗試判斷將進行使用者要求的目的。

開發將包含建立的應用程式，使用者將能夠使用語音和/或視線變更大小和場景中物件的色彩。 將未涵蓋的動作控制站使用。

在您的應用程式，則您對於如何將整合結果進行設計。 本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。 它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。

準備好訓練 LUIS 數次，其中涵蓋[第 12 章](#chapter-12--improving-your-luis-service)。 您會更好的結果已訓練 LUIS 的更多時間。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 和 Azure 303:自然語言理解 (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。 當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。 當使用 HoloLens，您可能會發現某些回應語音擷取期間。

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程專為具有基礎經驗的 Unity 開發人員和C#。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。 中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊會完全符合您會發現在較新的軟體與以下所列內容.

我們建議下列的硬體和軟體這堂課程：

- 開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發
- [Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式](install-the-tools.md)
- [最新的 Windows 10 SDK](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式
- 一組的耳機與內建的麥克風 （如果耳機沒有內建的麥克風和喇叭）
- Azure 設定和 LUIS 擷取的網際網路存取

## <a name="before-you-start"></a>開始之前

1.  若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。 
2.  若要允許您的機器以啟用語音輸入，請移至**Windows 設定 > 隱私權 > 語音、 筆跡 & 輸入** 按鈕上按下**語音服務開啟與輸入的建議**。
3.  本教學課程中的程式碼可讓您從錄製**預設麥克風裝置**在電腦上。 請確定預設麥克風裝置設定為您想要用來擷取您的聲音。
4.  如果耳機有內建的麥克風，，請務必選擇 *「 我穿上我耳機，切換到耳機式麥克風 」* 開啟*混合實境入口網站*設定。

    ![設定 沈浸式耳機](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>第 1 章-設定 Azure 入口網站

若要使用*Language Understanding*服務在 Azure 中，您必須設定您的應用程式提供服務的執行個體。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**新增**在左上角，，然後搜尋*Language Understanding*，然後按一下**Enter**。 

    ![建立 LUIS 資源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > 單字**的新**可能已取代為**建立資源**，較新的入口網站中。
 
3.  向新的頁面會提供 Language Understanding 服務的描述。 在左下方的這個頁面上，選取**建立**按鈕，以建立此服務的執行個體。

    ![LUIS 服務建立的法律注意事項](images/AzureLabs-Lab3-02.png)
 
4.  一旦您按一下 建立：

    1. 插入您想要**名稱**此服務執行個體。
    2. 選取 **訂用帳戶**。
    3. 選取 **定價層**適合您，如果這是第一個時間來建立*LUIS 服務*，免費層 （名為 F0） 應該是您可以使用。 可用的配置應該是多個足夠這堂課程。
    4. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些課程中） 的單一專案相關聯的所有 Azure 服務）。 

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 判斷**位置**資源群組 （如果您要建立新的資源群組）。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。
    6. 您也必須確認您已了解這些條款和條件套用到此服務。
    7. 選取 [建立]。

        ![建立 LUIS 服務-使用者輸入](images/AzureLabs-Lab3-03.png)
 
5.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。
6.  通知會出現在入口網站中，一旦建立服務執行個體。 
 
    ![新的 Azure 通知映像](images/AzureLabs-Lab3-04.png)

7.  按一下通知，以探索新的服務執行個體。

    ![成功的資源建立通知](images/AzureLabs-Lab3-05.png)
 
8.  按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 您會前往新的 LUIS 服務執行個體。 
 
    ![存取 LUIS 金鑰](images/AzureLabs-Lab3-06.png)

9.  在本教學課程中，您的應用程式將需要對您的服務，透過使用您的服務訂用帳戶金鑰進行呼叫。
10. 從*快速入門*頁面上的您*LUIS API*服務，請瀏覽至第一個步驟中，*取得您的金鑰*，然後按一下**金鑰**（您也可以達到此目的按一下藍色超連結索引鍵，位於服務導覽功能表中，以索引鍵的圖示表示）。 這將顯示您的服務*金鑰*。
11. 需要顯示的索引鍵，其中的複本，因為您將需要此更新版本中您的專案。 
12. 在 *服務*頁面上，按一下*Language Understanding 入口網站*重新導向至用來建立新的服務，LUIS 應用程式內的網頁。 

## <a name="chapter-2--the-language-understanding-portal"></a>第 2 章-Language Understanding 入口網站

這一節中，您將了解如何對 LUIS 入口網站中的 LUIS 應用程式。 

> [!IMPORTANT]
> 請特別注意，設定*實體*，*意圖*，並*談話*這一章中是第一個步驟中建置您的 LUIS 服務： 您也必須重新訓練服務，許多次，因此要更精確。 重新訓練您的服務說明[最後一章](#chapter-12--improving-your-luis-service)本課程中，因此請確定您已完成它。

1.  達到*Language Understanding 入口網站*，您可能需要登入，如果您還沒有，與您的 Azure 入口網站相同的認證。 

    ![LUIS 登入頁面](images/AzureLabs-Lab3-07.png)
 
2.  如果這是您第一次使用 LUIS，您必須捲動到底部的 歡迎 頁面來尋找並按一下**建立 LUIS 應用程式** 按鈕。

    ![建立 LUIS 應用程式頁面](images/AzureLabs-Lab3-08.png)
 
3.  登入之後，按一下**我的應用程式**（如果您目前不是在該區段中）。 您可以按一下**建立新的應用程式**。

    ![LUIS-我的應用程式映像](images/AzureLabs-Lab3-09.png)
 
4.  提供給您的應用程式*名稱*。
5.  如果您的應用程式應該了解不同於英語的語言，您應該變更*文化特性*到適當的語言。
6.  這裡您也可以加入*描述*新 LUIS 應用程式。

    ![LUIS-建立新的應用程式](images/AzureLabs-Lab3-10.png)

7.  一旦您按下**完成**，將會進入*建置*您新的頁面*LUIS*應用程式。
8.  有幾個重要的概念，若要了解以下：

    -   *意圖*，表示將使用者從下列查詢會呼叫的方法。 *意圖*可能會有一或多個*實體*。
    -   *實體*，是描述的相關資訊之查詢的元件*意圖*。
    -   *談話*，前提是由開發人員，該 LUIS 會使用定型本身是查詢的範例。

如果這些概念不完全清除，請不要擔心，如本課程將釐其進一步在這一章中。

您將會開始建立*實體*建置這堂課程所需。

9.  在頁面的左側，按一下*實體*，然後按一下**建立新的實體**。

    ![建立新的實體](images/AzureLabs-Lab3-11.png)

10. 呼叫新的實體*色彩*，將其類型設*簡單*，然後按**完成**。

    ![建立簡單的實體-色彩](images/AzureLabs-Lab3-12.png)
 
11. 重複此程序來建立三 （3） 多個簡單的實體名稱為：

    -   *upsize*
    -   *downsize*
    -   *target*

結果看起來應該類似下面的影像：

![建立實體的結果](images/AzureLabs-Lab3-13.png)
 
此時您可以在其中開始建立*意圖*。 

> [!WARNING]
> 請勿刪除**無**意圖。

12. 在頁面的左側，按一下**意圖**，然後按一下**建立新的用途**。

    ![建立新的對應方式](images/AzureLabs-Lab3-14.png)

13. 呼叫新*意圖* **ChangeObjectColor**。

    > [!IMPORTANT]
    > 這*意圖*名稱用在稍後在本課程中的程式碼，因此為了獲得最佳結果，使用此名稱完全依照所提供。

一旦您確認您將會導向至意圖頁面的名稱。

![LUIS-意圖頁面](images/AzureLabs-Lab3-15.png)

您會注意到沒有文字方塊，要求您為 5 或以上不同的型別*發音*。

> [!NOTE]
> LUIS 會將所有的表達方式轉換為小寫。

14. 插入下列*Utterance*頂端的文字方塊中 (目前使用的文字*輸入約 5 範例...* )，然後按**Enter**:

```
The color of the cylinder must be red
```

您會注意到，新*Utterance*會出現在下方的清單。

遵循相同的程序中，插入下列六 （6） 表達方式：

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

如您所建立每個 [utterance] 中,，您必須識別為實體 LUIS 應該使用哪一個字。 在此範例中，您需要加上標籤與所有色彩*色彩*實體，並做為目標的所有可能參考*目標*實體。

15. 若要這樣做，請嘗試按一下的單字*圓柱*中第一個 [utterance]，然後選取*目標*。

    ![識別 [utterance] 目標](images/AzureLabs-Lab3-16.png)
 
16. 現在按一下 word*紅色*中第一個 [utterance]，然後選取*色彩*。

    ![識別 [utterance] 實體](images/AzureLabs-Lab3-17.png)
 
17. 此外，標籤的下一行所在*cube*應該*目標*，和*黑色*應該*色彩*。 也請注意使用的單字 *'this'*， *'it'*，並 *'這個物件'*，我們提供，因此也有可用的非特定的目標型別。 

18. 重複上述程序，直到所有談話都有標示的實體。 請參閱下列映像，如果您需要協助。

    > [!TIP]
    > 當選取以實體形式將它們加上標籤的文字：
    > - 如需單一字只按一下它們。
    > - 如需兩個或多個字組，按一下的開頭和結尾的集合。

    > [!NOTE]
    > 您可以使用*語彙基元檢視*切換按鈕，即可切換**實體 / 權杖檢視**！

19. 結果應該會顯示下列影像中所示**實體 / 權杖檢視**:

    ![權杖及實體的檢視](images/AzureLabs-Lab3-18.png)
  
20. 此時按下**定型**在頁面的右上方按鈕，然後等候小圓形指標，它才會變成綠色。 這表示 LUIS 已辨識此意圖成功訓練。

    ![訓練 LUIS](images/AzureLabs-Lab3-19.png)
 
21. 為您在練習中，建立新的對應方式，稱為**ChangeObjectSize**，使用實體*目標*，*轉換*，以及*縮小*。
22. 遵循先前的用途，相同的程序插入下列 （8） 的發音如*大小*變更：

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

23. 結果應該類似下面的影像中：

    ![設定 ChangeObjectSize 語彙基元 / 實體](images/AzureLabs-Lab3-20.png) 

24. 一次這兩種對應方式**ChangeObjectColor**並**ChangeObjectSize**，已建立並定型，按一下**發行**網頁頂端的按鈕。

    ![LUIS 服務發行](images/AzureLabs-Lab3-21.png)

25. 在 *發佈*頁面上，您將完成發佈您的 LUIS 應用程式，使它可以存取您的程式碼。

    1. 設定卸除*發佈至*作為**生產**。
    2. 設定*時區*到您的時區。
    3. 核取方塊**包含所有預測意圖分數**。
    4. 按一下 **發行至生產位置**。

        ![發行設定](images/AzureLabs-Lab3-22.png)

26. 一節*資源和金鑰*:

    1.  選取您要為在 Azure 入口網站中的服務執行個體的區域。
    2.  您會發現**Starter_Key**項目，會忽略它。
    3.  按一下**Add Key** ，並插入*金鑰*您取得在 Azure 入口網站中，當您建立您的服務執行個體。 如果您的 Azure 和 LUIS 入口網站登入相同的使用者，您將會提供下拉式清單功能表*租用戶名稱*，*訂用帳戶名稱*，而*金鑰*您想要使用 （為您提供先前在 Azure 入口網站中，會有相同的名稱。

    > [!IMPORTANT] 
    > 下面*端點*，製作的複本對應到索引鍵之端點的已插入，您很快就會使用它在程式碼中。
 
## <a name="chapter-3--set-up-the-unity-project"></a>第 3 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟*Unity*然後按一下**新增**。 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab3-24.png)

2.  您現在需要提供 Unity 專案名稱、 插入**MR_LUIS**。 請確定專案類型設定為**3D**。 設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![提供新的 Unity 專案的詳細資料。](images/AzureLabs-Lab3-25.png)
 
3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至 編輯 > 喜好設定，然後在新視窗中，瀏覽**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![更新指令碼編輯器喜好設定。](images/AzureLabs-Lab3-26.png)
 
4.  接下來，移至**檔案 > 組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。

    ![建置設定 視窗中，切換至 UWP 的平台。](images/AzureLabs-Lab3-27.png)
 
5.  移至**檔案 > 組建設定**並確定：

    1. **裝置為目標**設為**任何裝置**

        > 對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。

    2. **建置型別**設為**D3D**
    3. **SDK**設為**最新安裝**
    4. **Visual Studio 版本**設為**最新安裝**
    5. **建置並執行**設為**本機電腦**
    6. 儲存場景，並將它新增至組建。

        1. 做法是選取**加入開啟的場景**。 儲存視窗會出現。
        
            ![按一下 新增開啟場景按鈕](images/AzureLabs-Lab3-28.png)

        2. 建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![建立新的指令碼資料夾](images/AzureLabs-Lab3-29.png)

        3. 開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中輸入**MR_LuisScene**，然後按**儲存**。

            ![指定新的場景的名稱。](images/AzureLabs-Lab3-30.png)

    7. 剩餘的設定，*組建設定*，應保持為預設值，現在。

6. 中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。 

    ![開啟播放程式設定。](images/AzureLabs-Lab3-31.png) 
 
7. 在此窗格中，少數設定需要驗證：

    1. 在 [**其他設定**] 索引標籤：

        1. **指令碼執行階段版本**應該**穩定**（.NET 3.5 對等）。
        2. **指令碼後端**應該是 **.NET**
        3. **API 相容性層級**應該是 **.NET 4.6**

            ![更新其他設定。](images/AzureLabs-Lab3-32.png)
      
    2. 內**發佈設定**索引標籤之下**功能**，檢查：

        1. **InternetClient**
        2. **Microphone**

            ![正在更新發行的設定。](images/AzureLabs-Lab3-33.png)

    3. 在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。

        ![更新 R 設定。](images/AzureLabs-Lab3-34.png)

8.  回到*Build Settings* _Unity C#_ 專案不再呈現灰色，這旁邊的核取方塊。 
9.  關閉 [建立設定] 視窗。
10. 儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。

## <a name="chapter-4--create-the-scene"></a>第 4 章-建立場景

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，它匯入到您的專案做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 5 章](#chapter-5--create-the-microphonemanager-class)。 

1.  中的空白區域上按一下滑鼠右鍵*階層面板*下方**3D 物件**，加入**平面**。

    ![建立平面。](images/AzureLabs-Lab3-35.png)

2.  請注意，當您以滑鼠右鍵按一下*階層*再次建立更多的物件，如果您仍然有選取的最後一個物件，選取的物件會您的新物件的父系。 在階層中的空白空間上按一下滑鼠左鍵，然後以滑鼠右鍵按一下，可以避免此選項。

3.  重複上述程序，將下列物件：

    1. *Sphere*
    2. *Cylinder*
    3. *Cube*
    4. *3D 文字*

4.  產生的場景*階層*應該類似下面的影像中：

    ![場景階層安裝程式。](images/AzureLabs-Lab3-36.png)
 
5.  上按一下滑鼠左鍵**Main Camera**來選取它，看看*Inspector 面板*您會看到所有相機物件及其元件。
6.  按一下 **新增元件** 按鈕位於最底部*偵測器 面板*。

    ![新增音訊來源](images/AzureLabs-Lab3-37.png)
 
7.  搜尋呼叫的元件*音效來源*，如上所示。
8.  此外，請確定*轉換*Main Camera 元件設定為 (0,0,0)，這可以藉由按下**齒輪**相機的旁邊的圖示*轉換*元件然後選取**重設**。 *轉換*元件再看起來應該像：

    1.  *位置*設定為**0，0，0**。
    2.  *旋轉*設定為**0，0，0**。

    > [!NOTE] 
    > 針對 Microsoft HoloLens，您必須也變更下列項目，兩者皆屬於**相機**元件，這是在您**Main Camera**:
    > - **清除旗標：** 不透明色彩。
    > - **背景**' Black、 Alpha 0'-十六進位色彩: #00000000。

9.  上按一下滑鼠左鍵**平面**來選取它。 在 [*偵測器] 面板*設定*轉換*元件使用下列值：

    |       | 轉換-*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. 上按一下滑鼠左鍵**球體**來選取它。 在 [*偵測器] 面板*設定*轉換*元件使用下列值：

    |       | 轉換-*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. 上按一下滑鼠左鍵**圓柱**來選取它。 在 [*偵測器] 面板*設定*轉換*元件使用下列值：

    |       | 轉換-*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | -2    | 1                      | 2     |

12. 上按一下滑鼠左鍵**Cube**來選取它。 在 [*偵測器] 面板*設定*轉換*元件使用下列值：

    |        | 轉換-*位置* |       |  \| |       | 轉換-*旋轉* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. 上按一下滑鼠左鍵**新的文字**物件加以選取。 在 [*偵測器] 面板*設定*轉換*元件使用下列值：

    |       | 轉換-*位置* |       |  \| |       | 轉換-*小數位數* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. 變更**字型大小**中**文字 Mesh**元件加入**50**。
15. 變更*名稱*的**文字 Mesh**物件**聽寫的文字**。

    ![建立 3D 文字物件](images/AzureLabs-Lab3-38.png)
 
16. 您的階層面板結構現在看起來應該像這樣：

    ![mesh 場景檢視中的文字](images/AzureLabs-Lab3-38b.png)


17. 最終的場景看起來應該類似下面的影像：

    ![場景檢視中。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>第 5 章-建立 MicrophoneManager 類別

您即將建立的第一個指令碼*MicrophoneManager*類別。 在此之後，您將建立*LuisManager*，則*行為*類別，最後*視線*類別 （可自由雖然將討論當您建立所有這些現在，達到每一章）。

*MicrophoneManager*類別負責：

-   偵測耳機或 （無論是的預設值） 的機器附加的錄音裝置。
-   擷取音訊 （語音），並將它儲存為字串使用聽寫。
-   一旦已暫停的語音，提交至聽寫*LuisManager*類別。 

若要建立此類別： 

1.  以滑鼠右鍵按一下*專案 面板*，**建立 > 資料夾**。 呼叫資料夾**指令碼**。 

    ![建立指令碼 資料夾。](images/AzureLabs-Lab3-40.png)
 
2.  具有**指令碼**建立資料夾，按兩下，以開啟該項目。 然後，在該資料夾中，按一下滑鼠右鍵**建立 >C#指令碼**。 指令碼命名*MicrophoneManager*。 

3.  按兩下*MicrophoneManager*來開啟它*Visual Studio*。
4.  檔案開頭處新增下列命名空間：

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  然後新增下列變數內*MicrophoneManager*類別：

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  程式碼*Awake()* 並*start （)* 方法現在需要加入。 在類別初始化時，這些將會呼叫：

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
 
7.  現在，您需要應用程式用來啟動和停止語音擷取，並將它傳遞至方法*LuisManager*您即將建置的類別。 

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

8.  新增*聽寫處理常式*，將會叫用語音暫停時。 這個方法會傳遞要聽寫的文字*LuisManager*類別。

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
    > 刪除*update （)* 方法，因為這個類別不會使用它。

9.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

    > [!NOTE]
    > 此時您會注意到錯誤不會出現在*Unity 編輯器主控台面板*。 這是因為程式碼參考*LuisManager*您會建立下一步 一章中的類別。

## <a name="chapter-6--create-the-luismanager-class"></a>第 6 章-建立 LUISManager 類別

它是您建立的時候*LuisManager*類別，可讓 Azure LUIS 服務的呼叫。 

這個類別的目的是要接收的語音輸入文字*MicrophoneManager*類別，並將它傳送給*Azure Language Understanding API*以便進行分析。

這個類別會還原序列化*JSON*回應，並呼叫適當的方法*行為*觸發動作的類別。

若要建立此類別： 

1.  按兩下**指令碼**資料夾，將它開啟。 
2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。 指令碼命名*LuisManager*。 
3.  按兩下要使用 Visual Studio 中開啟它的指令碼。
4.  檔案開頭處新增下列命名空間：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  您將會開始建立三個類別**內** *LuisManager*類別 (在相同的指令碼檔案中，上述*start （)* 方法)，將會代表已還原序列化從 Azure 的 JSON 回應。

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

6.  接下來，新增下列變數內*LuisManager*類別：
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  請務必現在將放在您的 LUIS 端點 （這就會從您的 LUIS 入口網站）。

8.  程式碼*Awake()* 方法現在需要加入。 在類別初始化時，將會呼叫這個方法：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  現在，您需要的方法，此應用程式用來傳送來自聽寫*MicrophoneManager*類別，即可*LUIS*，然後接收和還原序列化回應。 
10. 一旦決定的意圖和相關聯的實體的值，傳遞至執行個體*行為*類別觸發的動作。

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
 
11. 建立新的方法，稱為*AnalyseResponseElements()* ，將讀取產生*AnalysedQuery*並判斷實體。 這些實體會決定之後，會將它們傳遞到的執行個體*行為*動作中使用的類別。

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

            // Depending on the topmost recognised intent, read the entities name
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
    > 刪除*start （)* 並*update （)* 方法，因為這個類別不會使用它們。

12. 請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

> [!NOTE]
> 此時您會注意到數個錯誤，不會出現在*Unity 編輯器主控台面板*。 這是因為程式碼參考*行為*您會建立下一步 一章中的類別。

## <a name="chapter-7--create-the-behaviours-class"></a>第 7 章-建立行為類別

*行為*類別將會觸發使用所提供之實體的動作*LuisManager*類別。

若要建立此類別： 

1.  按兩下**指令碼**資料夾，將它開啟。 
2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。 指令碼命名*行為*。 
3.  按兩下要開啟它的指令碼*Visual Studio*。
4.  然後新增下列變數內*行為*類別：

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  新增*Awake()* 方法程式碼。 在類別初始化時，將會呼叫這個方法：

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  下列方法會呼叫*LuisManager*類別 （您先前建立） 來判斷哪一個物件為目標的查詢，然後再觸發適當的動作。

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
 
7.  新增*FindTarget()* 方法，以判斷哪些*Gameobject*做為目標的目前的意圖。 這個方法預設目標，以便*GameObject*正在"gazed 」 如果沒有明確的目標定義實體中。

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
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
    > 刪除*start （)* 並*update （)* 方法，因為這個類別不會使用它們。

8.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-8--create-the-gaze-class"></a>第 8 – 建立視線類別

您必須完成此應用程式的最後一個類別是*視線*類別。 這個類別會更新參考*GameObject*目前在使用者的視覺焦點。

若要建立此類別： 

1.  按兩下**指令碼**資料夾，將它開啟。 
2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。 指令碼命名*視線*。 
3.  按兩下要開啟它的指令碼*Visual Studio*。
4.  插入此類別的下列程式碼：

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
 
5.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-9--completing-the-scene-setup"></a>第 9 章 – 場景設定完成

1.  若要完成場景的安裝程式，將您從指令碼 資料夾，以建立每個指令碼**Main Camera**物件中*階層面板*。
2.  選取  **Main Camera**並查看*Inspector 面板*您應該能夠看到您附加，每個指令碼，您會注意到每個指令碼在即將設定的參數。

    ![設定觀景窗參考目標。](images/AzureLabs-Lab3-41.png)

3.  若要正確地設定這些參數，請遵循下列指示：

    1. *MicrophoneManager*:

        - 從*階層面板*，拖曳**聽寫的文字**物件插入**聽寫的文字**參數值 方塊中。

    2. *行為*，從*階層面板*:

        - 拖曳**球體**物件插入*球體*參考 [目標] 方塊。
        - 拖曳**圓柱**成*圓柱*參考 [目標] 方塊。
        - 拖曳**Cube**成*Cube*參考 [目標] 方塊。

    3. *視線*:

        - 設定*視線最大距離*要**300** （如果它尚未）。 

4.  結果看起來應該類似下面的影像：

    ![顯示相機參考目標，現在設定。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>第 10 章-測試在 Unity 編輯器中

場景安裝程式會正確地實作測試。

請確定：

-   所有指令碼會附加至**Main Camera**物件。 
-   中的所有欄位*Main 攝影機偵測器 面板*皆正確。

1.  按下**播放**按鈕*Unity Editor*。 應用程式應該附加的沈浸式耳機內執行。

2.  試用少數的表達方式，例如：

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > 如果您看到錯誤的相關變更預設音訊裝置，Unity 主控台中，場景可能無法如預期般運作。 這是因為內建麥克風耳機，讓它們會處理混合的實境入口網站的方式。 如果您看到此錯誤，只是停止場景並重新啟動它，而且項目應該都能當作預期。

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>第 11 章-建置和側載 UWP 方案

一旦確定應用程式正在 Unity 編輯器中，您就準備好要建置和部署。

若要建置：

1.  按一下儲存目前的場景**檔案 > 儲存**。
2.  移至**檔案 > 組建設定**。
3.  勾選方塊稱為**UnityC#專案**（適用於查看和 UWP 專案建立之後，偵錯您的程式碼。
4.  按一下 **加入開啟的場景**，然後按一下**建置**。

    ![建置設定 視窗](images/AzureLabs-Lab3-43.png)

4.  系統會提示您選取您要建置方案的資料夾。 

5.  建立*建置*資料夾和該資料夾中建立適當的名稱，您選擇的另一個資料夾。 
6.  按一下 **選取資料夾**開始在該位置的組建。
 
    ![建立組建資料夾](images/AzureLabs-Lab3-44.png)
    ![選取組建資料夾](images/AzureLabs-Lab3-45.png)
 
7.  一次 Unity 已完成的建置 （它可能需要一些時間），它應該會開啟**檔案總管**視窗在您的組建位置。

若要部署在本機電腦上：

1.  在  *Visual Studio*，開啟方案檔中已建立[前一章](#chapter-10--test-in-the-unity-editor)。
2.  在 **的方案平台**，選取**x86**，**本機**。
3.  在 **方案組態**選取**偵錯**。

    > 針對 Microsoft HoloLens，您可能會發現它更輕鬆地將此設為*遠端機器*，如此一來，您不行動網卡到您的電腦。 不過，您必須也執行下列作業：
    > - 了解**IP 位址**的您 HoloLens，位於*設定 > 網路和網際網路 > Wi-fi > 進階選項*; IPv4 是您應該使用的位址。 
    > - 請確定**開發人員模式**是**上**; 在找到*設定 > 更新與安全性 > 適用於開發人員*。

    ![部署應用程式](images/AzureLabs-Lab3-46.png)
 
4.  移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。
5.  您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動 ！
6.  一旦啟動，應用程式會提示您授權的存取權_麥克風_。 使用*移動控制器*，或*語音輸入*，或有*鍵盤*按**是** 按鈕。 

## <a name="chapter-12--improving-your-luis-service"></a>第 12 章-改善您的 LUIS 服務

>[!IMPORTANT] 
> 本章是非常重要的是，並可能需要 interated 時數次，因為它可協助改善您的 LUIS 服務的精確度： 確保您已完成這。

若要改善 LUIS 所提供的了解程度，您需要擷取新的談話，並使用它們來重新訓練您的 LUIS 應用程式。

例如，您可能已受過訓練 LUIS，若要了解"Increase"以及 「 轉換 」，但您不希望您的應用程式，也了解 「 放大 」 之類的字？

一旦您已使用您的應用程式數次，你說的所有項目會收集 LUIS 和 LUIS 入口網站中使用。

1.  移至入口網站應用程式遵循此[連結](https://www.luis.ai/home)，和登入。
2.  一旦您登入您的 MS 認證，按一下您*應用程式名稱*。
3.  按一下 **檢閱端點的發音**頁面左邊的按鈕。

    ![檢閱表達方式](images/AzureLabs-Lab3-47.png)
 
4.  您會看到一份已由您的混合實境應用程式傳送至 LUIS 的發音。

    ![清單中的表達方式](images/AzureLabs-Lab3-48.png)
 
您會發現一些反白顯示*實體*。 

停留在反白顯示的每個字，您可以檢閱每個 [utterance]，並判斷哪些實體有尚未正確辨識，實體是錯誤以及哪些實體就會遺失。

在上述範例中，它找不到，「 魚叉式 」 這個字有已反白顯示做為目標，所以必須更正錯誤，由這個字，以滑鼠暫留，然後按一下**移除標籤**。

![檢查談話](images/AzureLabs-Lab3-49.png)
![移除標籤影像](images/AzureLabs-Lab3-50.png)
 
5.  如果您發現完全無誤的談話，您可以刪除它們使用**刪除**螢幕右側的按鈕。

    ![刪除錯誤的表達方式](images/AzureLabs-Lab3-51.png)

6.  或如果您認為 LUIS 已正確解譯 utterance，您可以使用來驗證其了解**新增對齊意圖** 按鈕。

    ![加入 對齊的意圖](images/AzureLabs-Lab3-52.png)

7.  一旦您在排序所有顯示的談話，請嘗試並重新載入頁面，以查看更多是否可用。
8.  它是重複的次數以改善您的應用程式了解此程序非常重要。 

**愉快 ！**

## <a name="your-finished-luis-integrated-application"></a>您已完成的整合式 LUIS 應用程式

恭喜，您所建立的混合的實境應用程式，運用 Azure Language Understanding Intelligence Service，以了解使用者所講的是和處理該資訊。

![實驗室結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

使用此應用程式時可能會注意到，是否您注視 Floor 物件，並要求以變更其色彩，它就會如此。 您可以算出如何停止應用程式時變更 Floor 色彩嗎？

### <a name="exercise-2"></a>練習 2

請嘗試擴充 LUIS 和應用程式的功能，加入場景; 中的物件的其他功能做為範例，請在視線叫用的時間點，根據使用者所說，並且可使用現有的命令旁目前的場景物件，這些物件建立新的物件。 
