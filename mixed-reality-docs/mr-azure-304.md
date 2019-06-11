---
title: MR 和 Azure 304-臉部辨識
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境，academy、 unity、 教學課程中，api，臉部辨識、 hololens、 沉浸式 vr
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596464"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR 和 Azure 304:臉部辨識

![完成本課程的結果](images/AzureLabs-Lab4-00.png)

在本課程中您會了解如何將臉部辨識功能加入至混合的實境應用程式中，使用 Azure 認知服務，Microsoft 臉部 api。

*Azure 的人臉識別 API*是 Microsoft 服務，開發人員提供最先進的臉部演算法，全都在雲端。 *人臉識別 API*有兩個主要功能： 臉部屬性，以偵測和臉部辨識。 這可讓開發人員只要設定一組群組的表面，並接著，將傳送查詢映像服務更新版本中，以判斷其表面的所屬。 如需詳細資訊，請瀏覽[Azure 臉部辨識頁面](https://azure.microsoft.com/services/cognitive-services/face/)。

完成本課程之後，您會有混合的實境 HoloLens 應用程式，可以執行下列作業：

1. 使用**點選手勢**起始擷取的映像使用內建的 HoloLens 相機。 
2. 傳送至擷取的映像*Azure 人臉識別 API*服務。
3. 接收的結果*人臉識別 API*演算法。
4. 使用簡單的使用者介面，以顯示相符的人員名稱。

這將教導您如何將結果從臉部 API 服務進入您的 Unity 為基礎的混合的實境應用程式。

在您的應用程式，則您對於如何將整合結果進行設計。 本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。 它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 304:臉部辨識</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然這堂課程主要著重於 HoloLens，您也可以套用您在此課程 Windows Mixed Reality 沈浸式 (VR) 耳機來了解。 因為沈浸式 (VR) 耳機並沒有可存取的相機，您必須連線到您的 PC 外部相機。 當您遵循本課程中，您會看到 備忘稿上用來支援沈浸式 (VR) 耳機時，您可能需要的任何變更。

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
- 相機連接到您的電腦 （開發沈浸式耳機）
- Azure 設定和人臉識別 API 擷取的網際網路存取

## <a name="before-you-start"></a>開始之前

1.  若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。
2.  設定並測試您的 HoloLens。 如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。 

校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。

如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。

## <a name="chapter-1---the-azure-portal"></a>第 1 章-Azure 入口網站

若要使用*人臉識別 API*服務在 Azure 中，您必須設定您的應用程式提供服務的執行個體。

1.  首先，登入[Azure 入口網站](https://portal.azure.com)。 

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**新增**在左上角，，然後搜尋*人臉識別 API*、 按下**Enter**。

    ![搜尋臉部 api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 單字**的新**可能已取代為**建立資源**，較新的入口網站中。

3.  新的頁面將提供的描述*人臉識別 API*服務。 在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。

    ![臉部 api 資訊](images/AzureLabs-Lab4-02.png)

4.  一旦您按下 **建立** :

    1. 插入您想要的名稱，此服務執行個體。

    2. 選取訂用帳戶。

    3. 選取定價層適合您，如果這是第一次建立*臉部 API 服務*，免費層 （名為 F0） 應該是您可以使用。

    4. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。 

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. UWP 應用程式**人員 Maker**，供您更新版本中，需要使用 「 美國西部 」 位置。

    6. 您也必須確認您已了解這些條款和條件套用到此服務。

    7. 選取 **建立*。**

        ![建立臉部 api 服務](images/AzureLabs-Lab4-03.png)

5.  一旦您按下 **建立** 您必須建立服務，這可能需要一分鐘。

6.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![服務建立通知](images/AzureLabs-Lab4-04.png)

7.  按一下通知，以探索新的服務執行個體。

    ![請移至資源通知](images/AzureLabs-Lab4-05.png)

8.  當您準備好時，按一下**移至資源**通知，以探索新的服務執行個體中的按鈕。

    ![存取臉部 api 金鑰](images/AzureLabs-Lab4-06.png)

9.  在本教學課程中，您的應用程式必須對您的服務，透過使用您的服務訂用帳戶 'key' 進行呼叫。 從*快速入門*頁面上的您*人臉識別 API*服務，第一個點是數字 1，為*取得您的金鑰。*

10. 在上*服務*頁面上，選取任一個藍色**金鑰**超連結 （如果在快速入門 頁面上），或**金鑰**服務瀏覽功能表中的連結 (左邊，以表示 '索引鍵 ' 圖示)，以顯示您的金鑰。

    > [!NOTE] 
    > 請記下的其中一個索引鍵，並保護它，因為您稍後需要它。

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>第 2 章-使用 ' 人員 Maker' UWP 應用程式

請務必下載預先建置的 UWP 應用程式呼叫[人員 Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)。 此應用程式不是最終產品，如本課程中，只可協助您建立 Azure 項目，其更新版本的專案將會依賴工具。

**人員 Maker**可讓您建立 Azure 的項目，也就是與人員和群組的人員相關聯。 應用程式會將所需的資訊，然後稍後可由 FaceAPI，辨別您新增的人們的臉部格式。 

> [重要]**人員 Maker**會使用一些基本節流，協助確保不會超過每分鐘的服務呼叫數目**免費訂用帳戶層**。 在頂端的綠色文字會變更為紅色，並進行節流; 時，更新為 「 作用中 」如果發生這種情況，只需等待應用程式 （它會等到它接下來可以繼續存取臉部服務，一次使用時，更新為 「 中-作用中 」）。

此應用程式會使用*Microsoft.ProjectOxford.Face*程式庫，可讓您能夠完整使用人臉識別 API。 此程式庫是以 NuGet 套件的形式免費提供。 如需詳細資訊，以及類似，Api[請務必瀏覽 API 參考文章](https://docs.microsoft.com/azure/cognitive-services/face/apireference)。

> [!NOTE] 
> 這些是所需的步驟，說明如何達成上述目標，是進一步文件。 **人員 Maker**應用程式可讓您：
>
> - 建立*人員群組*、 有哪些群組包含的數個您想要與它相關聯的人員。 使用您的 Azure 帳戶中，您可以裝載多個人員群組。
>
> - 建立*人員*，這是使用者群組的成員。 每個人都有一些*臉部*與其相關聯的映像。
>
> -  指派*面臨映像*來*人員*，以允許您的 Azure 臉部 API 服務，以辨識*人員*由相對應*臉部*。
>
> -  *定型*您*Azure 臉部 API 服務*。

留意，因此若要定型此應用程式可以辨識的人員，您必須十 （10） 特寫相片的每個人，您想要新增到您的人員群組。 Windows 10 Cam 應用程式可協助您將這些。 您必須確定每張相片已清除 （避免模糊、 遮蔽，或正在牽扯太廣，從主體），在 jpg 或 png 檔案格式中的相片，正在不大的映像檔案大小**4MB**，並不小於**1KB**.

> [!NOTE]
> 如果您要遵循本教學課程，請勿用於您自己的臉部訓練，當您將 HoloLens 時，您無法看您自己。 使用表面的同事或人員的學生。

執行**人員 Maker**:

1.  開啟**PersonMaker**資料夾，然後按兩下*PersonMaker 解決方案*以開啟它*Visual Studio*。

2.  一次*PersonMaker 解決方案*開啟，請確定：

    1. *方案組態*設為**偵錯**。

    2. *的方案平台*設定為**x86**

    3. *目標平台*是**本機**。

    4.  您也可能需要*還原 NuGet 套件*(以滑鼠右鍵按一下*解決方案*，然後選取**還原 NuGet 套件**)。

3.  按一下 *本機電腦*和應用程式會啟動。 請注意，在較小的螢幕上，所有內容可能都無法看見，但您可以進一步向下捲動一進行檢視。

    ![人員 maker 使用者介面](images/AzureLabs-Lab4-07.png)

4.  插入您**Azure 驗證金鑰**，您應該有的從您*人臉識別 API*服務在 Azure 中。

5.  插入：

    1. *識別碼*您想要指派給*人員群組*。 識別碼必須是小寫、 不含空格。 為 Unity 專案中，稍後將需要它，請記下此識別碼。
    2. *名稱*您想要指派給*人員群組*（可以有空格）。


6.  按下**建立的人員群組** 按鈕。 確認訊息應該會出現下方的按鈕。

> [!NOTE]
> 如果您有 「 拒絕存取 」 錯誤，請檢查您要為您的 Azure 服務的位置。 如上所述，此應用程式被針對 「 美國西部 」。

> [!IMPORTANT]
> 您會注意到，您也可以按一下**提取已知群組**按鈕： 這是為了使用，而不是建立一個新的群組，且想如果您已經建立的人員。 請注意，如果您按一下*建立使用者群組*與已知的群組，這也會擷取群組。

7.  插入*名稱*的*人員*您想要建立。

    1. 按一下 [**建立人員**] 按鈕。

    2. 確認訊息應該會出現下方的按鈕。

    3. 如果您想要刪除個人您先前已經建立，您可以寫入文字方塊並按名稱**刪除的人員**

8.  請確定您知道您想要新增到群組之人員的相片十 （10） 的位置。

9.  按下**建立及開啟資料夾**的人員相關聯的資料夾中開啟 Windows 檔案總管。 新增十 （10） 映像的資料夾中。 它們必須有*JPG*或是*PNG*檔案格式。

10. 按一下 **提交至 Azure**。 計數器會顯示提交，後面的訊息，完成時的狀態。

11. 計數器已完成，並在顯示確認訊息後按一下 **定型**來定型您的服務。

程序完成後，您已準備好移至 Unity。

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟*Unity*然後按一下**新增**。 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab4-08.png)

2.  您現在必須提供 Unity 專案名稱。 插入**MR_FaceRecognition**。 請確定專案類型設定為**3D**。 設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![提供新的 Unity 專案的詳細資料。](images/AzureLabs-Lab4-09.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯 > 偏好**，然後在新視窗中，瀏覽**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![更新指令碼編輯器喜好設定。](images/AzureLabs-Lab4-10.png)

4.  接下來，移至**檔案 > 組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。

    ![建置設定 視窗中，切換至 UWP 的平台。](images/AzureLabs-Lab4-11.png)

5.  移至**檔案 > 組建設定**並確定：

    1. **裝置為目標**設為**HoloLens**

        > 針對擬真耳機，設定**目標裝置**要*任何裝置*。

    2. **建置型別**設為**D3D**
    3. **SDK**設為**最新安裝**
    4. **Visual Studio 版本**設為**最新安裝**
    5. **建置並執行**設為**本機電腦**
    6. 儲存場景，並將它新增至組建。 

        1. 做法是選取**加入開啟的場景**。 儲存視窗會出現。

            ![按一下 新增開啟場景按鈕](images/AzureLabs-Lab4-12.png)

        2. 選取 **新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![建立新的指令碼資料夾](images/AzureLabs-Lab4-13.png)

        3. 開啟您剛建立**場景**資料夾，然後在**檔名**： 文字欄位中輸入**FaceRecScene**，然後按**儲存**。

            ![指定新的場景的名稱。](images/AzureLabs-Lab4-14.png)

    7. 剩餘的設定，*組建設定*，應保持為預設值，現在。

6. 中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。 

    ![開啟播放程式設定。](images/AzureLabs-Lab4-15.png)

7. 在此窗格中，少數設定需要驗證：

    1. 在 [**其他設定**] 索引標籤：

        1. **指令碼** **執行階段版本**應該**實驗性**（.NET 4.6 對等）。 變更這將會觸發需要重新啟動編輯器。
        2. **指令碼後端**應該是 **.NET**
        3. **API 相容性層級**應該是 **.NET 4.6**

            ![更新其他設定。](images/AzureLabs-Lab4-16.png)
      
    2. 內**發佈設定**索引標籤之下**功能**，檢查：

        - **InternetClient**
        - **Webcam**

            ![正在更新發行的設定。](images/AzureLabs-Lab4-17.png)

    3. 在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。

        ![更新 R 設定。](images/AzureLabs-Lab4-18.png)

8.  回到*Build Settings*， **UnityC#專案**不再呈現灰色，這旁邊的核取方塊。 
9.  關閉 [建立設定] 視窗。
10. 儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。

## <a name="chapter-4---main-camera-setup"></a>第 4 章-Main Camera 安裝程式

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件的課程，並直接在程式碼中繼續進行，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)，然後匯入您的專案做為[自訂封裝](https://docs.unity3d.com/Manual/AssetPackages.html)。 請注意，此套件也包含匯入*Newtonsoft DLL*、 在涵蓋[第 5 章](#chapter-5--import-the-newtonsoft.json-library)。 與這個匯入，您可以繼續從[第 6 章](#chapter-6-create-the-faceanalysis-class)。

1.  在 [*階層*] 面板中，選取**Main Camera**。

2.  選取之後，您將能夠看到所有的元件**Main Camera**中*Inspector 面板*。

    1. **相機物件**必須命名為**Main Camera** （請注意拼字 ！）

    2. Main Camera**標記**必須設為**MainCamera** （請注意拼字 ！）

    3. 請確定**轉換的位置**設定為**0，0，0**

    4. 設定**清除旗標**到**純色**

    5. 設定**背景**相機元件以色彩**黑色，0 的 Alpha (十六進位的程式碼: #00000000)**

        ![設定觀景窗元件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>第 5 章-匯入 Newtonsoft.Json 程式庫

> [!IMPORTANT]
> 如果您匯入 '.unitypackage'[最後一章](#chapter-4--main-camera-setup)，您可以略過這一章。

若要可協助您還原序列化和序列化物件接收和傳送到 Bot 服務，您需要下載*Newtonsoft.Json*程式庫。 您會找到相容的版本已經使用正確的 Unity 資料夾結構，在此組織[Unity 封裝檔案](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)。 

若要匯入程式庫：

1.  下載 Unity 套件。
2.  按一下 **資產**，**匯入套件**，**自訂套件**。

    ![匯入 Newtonsoft.Json 程式庫](images/AzureLabs-Lab4-20.png)

3.  尋找您已下載，Unity 套件，並按一下 [開啟]。
4.  請確定已勾選的封裝的所有元件，然後按一下**匯入**。

    ![匯入 Newtonsoft.Json 程式庫](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>章節 6-建立 FaceAnalysis 類別

FaceAnalysis 類別的目的是要裝載與您的 Azure 臉部辨識服務進行通訊所需的方法。 

- 在傳送服務擷取映像之後, 它會分析它和識別人臉內，並判斷是否任何屬於已知的個人。 
- 如果找到已知的人員，則這個類別會顯示其名稱，作為在場景中的 UI 文字。

若要建立*FaceAnalysis*類別：

 1. 以滑鼠右鍵按一下*Assets 資料夾*位於 [專案] 面板，然後按一下**建立** > **資料夾**。 呼叫資料夾**指令碼**。 

    ![建立 FaceAnalysis 類別。](images/AzureLabs-Lab4-22.png)

2.  按兩下剛才建立開啟的資料夾。 
3.  在資料夾中，以滑鼠右鍵按一下，然後按一下**Create**  >   **C#指令碼**。 呼叫指令碼*FaceAnalysis*。 
4.  按兩下新*FaceAnalysis*指令碼，以使用 Visual Studio 2017 中開啟它。
5.  輸入下列的命名空間上述*FaceAnalysis*類別：

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  您現在需要新增所有用於 deserialising 的物件。 這些物件必須加入**外**的*FaceAnalysis* （下方下大括號中） 的指令碼。 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. *Start （)* 並*update （)* 方法不會使用，因此現在刪除它們。 

8.  內部*FaceAnalysis*類別中，新增下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > 取代**金鑰**並**personGroupId**您的服務金鑰與您先前建立的群組識別碼。

9.  新增*Awake()* 方法，initialises 類別，新增*ImageCapture* Main Camera 類別並呼叫標籤建立方法：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. 新增*CreateLabel()* 方法會建立*標籤*物件，以顯示分析結果：

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. 新增*DetectFacesFromImage()* 並*GetImageAsByteArray()* 方法。 前者會要求已送出的映像，在偵測任何可能的臉部，而後者是為了將擷取的映像轉換成位元組陣列臉部辨識服務︰

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. 新增*IdentifyFaces()* 方法，會要求*臉部辨識服務*來識別任何已知的臉部偵測到先前已送出的映像中。 要求會傳回識別碼所識別的人員，但不是名稱為：

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. 新增*GetPerson()* 方法。 藉由提供者識別碼，此方法，然後要求*臉部辨識服務*来傳回的已識別的人員名稱：

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  請記得**儲存**之前返回至 Unity 編輯器中的變更。
15.  在 Unity 編輯器中，從 專案 面板中的指令碼 資料夾拖曳 FaceAnalysis 指令碼中的 Main Camera 物件*階層面板*。 新的指令碼元件會因此新增到 Main Camera。 

![將放置到主攝影機 FaceAnalysis](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>第 7-建立 ImageCapture 類別

目的*ImageCapture*類別來裝載與通訊所需的方法是您*Azure 臉部辨識服務*分析的映像，您將會擷取時，用來識別在其中的臉部和判斷它是否屬於所知的人士。 如果找到已知的人員，則這個類別會顯示其名稱，作為在場景中的 UI 文字。

若要建立*ImageCapture*類別：
 
1.  以滑鼠右鍵按一下**指令碼**資料夾，您先前已建立，然後按一下**建立**，  **C#指令碼**。 呼叫指令碼*ImageCapture*。 
2.  按兩下新*ImageCapture*指令碼，以使用 Visual Studio 2017 中開啟它。
3.  輸入上面 ImageCapture 類別的下列命名空間：

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  內部*ImageCapture*類別中，新增下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  新增*Awake()* 並*start （)* 初始化類別，並允許以擷取使用者的筆勢 HoloLens 所需的方法：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  新增*TapHandler()* 使用者執行時呼叫*點選*筆勢：

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  新增*ExecuteImageCaptureAndAnalysis()* 方法，就會開始的映像擷取程序：

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  新增相片擷取程序完成時，會呼叫處理常式：

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. 請記得**儲存**之前返回至 Unity 編輯器中的變更。

## <a name="chapter-8---building-the-solution"></a>第 8 章-建置方案

若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 HoloLens。

這麼做之前，請確認：

-   第 3 章中所述的所有設定都正確都設定。 
-   指令碼*FaceAnalysis*會附加至 Main Camera 物件。 
-   這兩個**驗證金鑰**並**群組識別碼**都已設定內*FaceAnalysis*指令碼。

這提供您準備好要建置方案。 一旦已建置方案，您就可以部署您的應用程式。

若要開始建置程序：

1.  按一下檔案，儲存，以儲存目前場景。
2.  移至檔案，建置設定]，按一下 [加入開啟的場景。
3.  請務必建立刻度 UnityC#專案。

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab4-24.png)

4.  按下建置。 在這種方式，Unity 會啟動 檔案總管 視窗中，您要建立，然後選取 建置到應用程式的資料夾。 現在，在 Unity 專案中，建立該資料夾，並呼叫應用程式。 選取的應用程式資料夾，然後按選取資料夾。 
5.  Unity 會開始建置您的專案中，應用程式資料夾。 
6.  一次 Unity 已完成 （可能需要一些時間） 的建置，它將會開啟檔案總管 視窗中，您的組建位置。

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab4-25.png)

7.  開啟您的應用程式的資料夾，然後再開啟新的專案方案 （如上所示，MR_FaceRecognition.sln）。


## <a name="chapter-9---deploying-your-application"></a>第 9 章-部署應用程式

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

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab4-26.png)
 
5.  移至**建置 功能表**，然後按一下**部署方案**，側載您 HoloLens 應用程式。
6.  您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！

> [!NOTE]
> 若要將部署到擬真耳機，設定**的方案平台**來*本機電腦*，並設定**組態**至*偵錯*，使用*x86*作為**平台**。 然後部署到本機電腦，使用**建置 功能表**，並選取*部署方案*。 


## <a name="chapter-10---using-the-application"></a>第 10 章-使用應用程式

1.  頭戴 HoloLens，啟動應用程式。
2.  查看您已註冊的人員*人臉識別 API*。 請確認︰

    -  此人臉部不太遙遠，清楚地顯示
    -  環境光源不太深

3.  您可以使用點選手勢來擷取連絡人的圖片。
4.  等候傳送分析要求和接收回應應用程式。
5.  如果已成功辨識的人員，該人員的名稱會顯示為 UI 文字中。
6.  您可以重複使用點選手勢每隔幾秒鐘的擷取程序。

## <a name="your-finished-azure-face-api-application"></a>完成的 Azure 臉部 API 應用程式

恭喜，您可以建置利用 Azure 臉部辨識服務來偵測映像 」 中的臉部，並識別任何已知的人臉 mixed 的 reality 應用程式。

![完成本課程的結果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

**Azure 人臉識別 API**強大，足以偵測單一映像中的最多 64 的臉孔。 擴充應用程式，使它無法辨識兩個或三個的表面，在很多人之間。

### <a name="exercise-2"></a>練習 2

**Azure 人臉識別 API**時，也可以提供回的所有類型的屬性資訊。 將這整合到應用程式。 這可能是更有趣的是，結合[表情 API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)。
