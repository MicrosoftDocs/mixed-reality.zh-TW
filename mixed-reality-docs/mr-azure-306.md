---
title: MR 和 Azure 306-串流影片
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure 媒體服務。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學術，unity，教學課程，api，媒體服務，串流影片，360，沉浸，vr
ms.openlocfilehash: e0350d69eed9b922e174bc521107beac7d11b1bc
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926832"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時，使用這些教學課程的連結進行更新。

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR 和 Azure 306：串流影片

![最終產品-開始](images/AzureLabs-Lab6-00.png)
![最終產品-開始](images/AzureLabs-Lab6-01.png)

在此課程中，您將瞭解如何將您的 Azure 媒體服務連線到 Windows Mixed Reality VR 體驗，以允許在沉浸式耳機上串流360度的影片播放。 

**Azure 媒體服務**是一組服務，可為您提供廣播品質的影片串流服務，以在現今最熱門的行動裝置上觸及更大的觀眾。 如需詳細資訊，請造訪[Azure 媒體服務頁面](https://azure.microsoft.com/services/media-services)。

完成此課程之後，您將擁有一個混合現實的沉浸式耳機應用程式，其將能夠執行下列動作：

1. 透過**Azure 媒體服務**從**Azure 儲存體**取出360度的影片。

2. 顯示 Unity 場景內抓取的360度影片。

3. 使用兩個不同的影片，在兩個場景之間流覽。

在您的應用程式中，您可以決定如何將結果與您的設計整合。 本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。 您的工作是使用您從這個課程取得的知識，來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 306：串流影片</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。 也請注意，本檔中的必要條件和書面指示，代表在撰寫本文時已測試和驗證的內容（5月2018）。 您可以免費使用 [[安裝工具] 文章](install-the-tools.md)中所列的最新軟體，但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容，而不是如下所示。

在此課程中，我們建議您採用下列硬體和軟體：

- [與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦，可用於沉浸式（VR）耳機開發
- [已啟用開發人員模式的 Windows 10 秋季建立者更新（或更新版本）](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 沉浸式（VR）耳機](immersive-headset-hardware-details.md)
- 適用于 Azure 設定和資料抓取的網際網路存取
- 以檔案格式的 2 360-角度影片（您可以[在此下載頁面](https://www.mettle.com/360vr-master-series-free-360-downloads-page)找到一些免版稅的影片）

## <a name="before-you-start"></a>開始之前

1.  為避免在建立此專案時發生問題，強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案（長資料夾路徑可能會在組建階段造成問題）。
2.  設定和測試混合現實的沉浸式耳機。

    > [!NOTE]
    > 在此課程中，您將**不**需要有動作控制器。 如果您需要支援設定「沉浸式耳機」，請按一下[如何設定 Windows Mixed Reality 的連結](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>第1章-Azure 入口網站：建立 Azure 儲存體帳戶

若要使用**Azure 儲存體服務**，您將需要在 Azure 入口網站中建立並設定**儲存體帳戶**。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程，請洽詢您的講師或其中一個 proctors，以協助設定您的新帳戶。

2.  登入之後，請按一下左側功能表中的 [**儲存體帳戶**]。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-02.png)

3.  在 [**儲存體帳戶**] 索引標籤上，按一下 [**新增**]。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-03.png)

4.  在 [**建立儲存體帳戶**] 索引標籤中：

    1.  插入您帳戶的**名稱**，請注意此欄位只接受數位和小寫字母。

    2.  針對 [**部署模型]，** 選取 [ **Resource manager**]。

    3.  針對 [**帳戶類型**]，選取 [**儲存體（一般用途 v1）** ]。

    4.  針對 [**效能**]，請選取 [**標準] *。**

    5.  針對 **[** 複寫]，請選取 **[本機-多餘儲存體（LRS）** ]。

    6.  將 [**需要安全傳輸**] 保留為 [**停用**]。

    7.  選取**訂**用帳戶。

    8.  選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。

    9.  判斷資源群組的**位置**（如果您要建立新的資源群組）。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于特定區域。

5.  您必須確認已瞭解適用于此服務的條款及條件。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-04.png)

6.  按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。

7.  建立服務實例之後，入口網站中會出現通知。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-05.png)

8.  此時您不需要追蹤資源，只要移到下一章即可。

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>第2章-Azure 入口網站：建立媒體服務

若要使用 Azure 媒體服務，您必須將服務的實例設定為可供應用程式使用（帳戶持有者必須是系統管理員）。

1.  在 Azure 入口網站中，按一下左上角的 [**建立資源**]，然後搜尋 [**媒體服務]，** 按**enter**鍵。 您想要的資源目前有粉紅色圖示;按一下此以顯示新的頁面。

    ![Azure 入口網站](images/AzureLabs-Lab6-06.png)

2.  新頁面將會提供**媒體服務**的描述。 在此提示的左下方，按一下 [**建立**] 按鈕，以建立與此服務的關聯。

    ![Azure 入口網站](images/AzureLabs-Lab6-07.png)

3.  當您按一下 [**建立**] 之後，就會出現一個面板，您需要提供一些有關新媒體服務的詳細資料：

    1.  為此服務實例插入所需的**帳戶名稱**。

    2.  選取**訂**用帳戶。

    3. 選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務（例如這些實驗室）都保留在通用資源群組底下）。 
    
    > 如果您想要深入瞭解 Azure 資源群組，請遵循此[連結以瞭解如何管理 Azure 資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  判斷資源群組的**位置**（如果您要建立新的資源群組）。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于特定區域。

    5.  針對 [**儲存體帳戶**] 區段，按一下 [**請選取 ...** ] 區段，然後按一下您在上一章中建立的**儲存體帳戶**。

    6.  您也必須確認您已瞭解適用于此服務的條款及條件。

    7.  按一下 \[建立\]。

        ![Azure 入口網站](images/AzureLabs-Lab6-08.png)

4.  按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。

5.  建立服務實例之後，入口網站中會出現通知。

    ![Azure 入口網站](images/AzureLabs-Lab6-09.png)

6.  按一下通知以探索新的服務實例。

    ![Azure 入口網站](images/AzureLabs-Lab6-10.png)

7.  按一下通知中的 [**移至資源**] 按鈕，探索新的服務實例。

8.  在 [新增媒體服務] 頁面左側的面板中，按一下 [**資產**] 連結，這是大約一半的。

9.  在下一個頁面上，按一下頁面左上角的 [**上傳**]。

    ![Azure 入口網站](images/AzureLabs-Lab6-11.png)

10. 按一下**資料夾**圖示以流覽您的檔案，然後選取您想要串流處理的前360影片。 
    
    > 您可以遵循此[連結來下載範例影片](https://vimeo.com/214401712)。

    ![Azure 入口網站](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> 長檔名可能會導致編碼器發生問題：因此，若要確保影片沒有問題，請考慮縮短影片檔案名的長度。

11. 當影片完成上傳時，進度列會變成綠色。

    ![Azure 入口網站](images/AzureLabs-Lab6-13.png)

12. 按一下上方的文字（**yourservicename-資產**）以返回 [**資產**] 頁面。

13. 您會注意到已成功上傳您的影片。 按一下 [開啟]。

    ![Azure 入口網站](images/AzureLabs-Lab6-14.png)

14. 您要重新導向的頁面會顯示有關您影片的詳細資訊。 若要能夠使用您的影片，您必須按一下頁面左上角的 [**編碼**] 按鈕，將其編碼。

    ![Azure 入口網站](images/AzureLabs-Lab6-15.png)

15. 右側會出現新的面板，您可以在其中設定檔案的編碼選項。 設定下列屬性（有些會預設為已設定）：

    1.  **媒體編碼器名稱*媒體編碼器標準***

    2.  **編碼預設*內容自動調整多重位元速率*設定**

    3.  ***媒體編碼器標準處理 Video1 的*作業名稱**

    4.  **輸出媒體資產名稱*Video1--已編碼媒體編碼器標準***

        ![Azure 入口網站](images/AzureLabs-Lab6-16.png)

16. 按一下 [建立] 按鈕。

17. 您會發現**已加入編碼作業**的橫條，按一下該橫條，就會出現一個面板，其中顯示編碼進度。

    ![Azure 入口網站](images/AzureLabs-Lab6-17.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-18.png)

18. 等候作業完成。 完成後，您可以使用該面板右上方的 [X] 來關閉面板。

    ![Azure 入口網站](images/AzureLabs-Lab6-19.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > 所需時間取決於影片的檔案大小。 此程式可能需要相當長的時間。

19. 現在已建立影片的編碼版本，您可以將其發佈，使其可供存取。 若要這麼做，請按一下藍色連結**資產**以返回 [資產] 頁面。

    ![Azure 入口網站](images/AzureLabs-Lab6-21.png)

20. 您會看到您的影片以及另一個，這是「 **_多位元率_」資產類型**。

    ![Azure 入口網站](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > 您可能會注意到，新的資產與您的初始影片是*未知*的，而且有 ' 0 ' 個位元組的**大小**，只要重新整理您的視窗，即可更新。

21. 按一下 [此新資產]。

    ![Azure 入口網站](images/AzureLabs-Lab6-23.png)

22. 您會看到先前所用的面板相似，只有這是不同的資產。 按一下位於頁面頂端的 [**發行**] 按鈕。

    ![Azure 入口網站](images/AzureLabs-Lab6-24.png)

23. 系統會提示您在資產中將 [**定位器**] （即進入點）設定為 [檔案/s]。 針對您的案例，請設定下列屬性：

    1.   > **漸進**的**定位器類型**。

    2.  系統會將您的**日期**和**時間**從目前的日期設定為未來的時間（在此案例中為100年）。 保持原狀，或將它變更為 [符合]。

    > [!NOTE]
    > 如需定位器的詳細資訊，以及您可以選擇的內容，請造訪[Azure 媒體服務檔](https://docs.microsoft.com/azure/media-services/media-services-concepts)。

24. 在該面板的底部，按一下 [**新增**] 按鈕。

    ![Azure 入口網站](images/AzureLabs-Lab6-25.png)

25. 您的影片現在已發行，可以使用其端點進行串流處理。 頁面的正下方是檔案**區段。** 這是影片的不同編碼版本所在的位置。 選取最高可能的解決方式1（在下圖中是1920x960 檔案），右側的面板會出現。 您會在這裡找到**下載 URL**。 複製此**端點**，因為您稍後會在程式碼中使用它。

    ![Azure 入口網站](images/AzureLabs-Lab6-26.png)    

    ![Azure 入口網站](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > 您也可以按下 [**播放**] 按鈕來播放您的影片並加以測試。

26. 您現在需要上傳將在此實驗室中使用的第二個影片。 遵循上述步驟，針對第二個影片重複相同的程式。 請確定您也複製了第二個**端點**。 使用下列[連結下載第二個影片](https://vimeo.com/214402865)。

27. 一旦發佈這兩個影片之後，您就可以繼續進行下一章。

## <a name="chapter-3---setting-up-the-unity-project"></a>第3章-設定 Unity 專案

以下是使用混合現實進行開發的一般設定，因此是適用于其他專案的絕佳範本。

1.  開啟**Unity** ，然後按一下 [**新增**]。 

    ![Azure 入口網站](images/AzureLabs-Lab6-28.png)

2.  您現在必須提供 Unity 專案名稱，並插入**MR\_360VideoStreaming。** 請確定 [專案類型] 設定為 [ **3d**]。 將位置設定為適合您的位置（請記住，接近根目錄較佳）。 然後，按一下 [**建立專案**]。

    ![Azure 入口網站](images/AzureLabs-Lab6-29.png)

3.  在 Unity 開啟的情況下，值得檢查預設**腳本編輯器**是否設定為**Visual Studio。** 移至 [ ***編輯* *喜好*** 設定]，然後在新視窗中，流覽至 [**外部工具**]。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

    ![Azure 入口網站](images/AzureLabs-Lab6-30.png)

4.  接下來，移至 [檔案] [  ***組建設定*** ]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至**通用 Windows 平臺**。

5.  也請確定：

    1. [**目標裝置**] 已設定為 [**任何裝置]。**
    
    2.  [**組建類型**] 設定為 [ **D3D]。**

    3.  **SDK**設定為 [**最新安裝]。**

    4.  **Visual Studio 版本**設定為 [**最新安裝]。**

    5.  [**組建與執行**] 設定為 [**本機電腦]。**

    6.  現在請不要擔心設定**場景**，因為您稍後會進行設定。

    7.  其餘的設定現在應保留為預設值。

        ![設定 Unity 專案](images/AzureLabs-Lab6-31.png)

6.  在 [**組建設定**] 視窗中，按一下 [ **Player 設定**] 按鈕，這會在偵測**器**所在的空間中開啟相關的面板。 

7. 在此面板中，需要驗證幾項設定：

    1.  在 [**其他設定**] 索引標籤中：

        1.  **腳本** **執行階段版本**應為**穩定**（.net 3.5 對等）。

        2. **腳本後端**應該是 **.net。**

        3. **API 相容性層級**應該是 **.net 4.6。**

            ![設定 Unity 專案](images/AzureLabs-Lab6-32.png)

    2.  在面板中，于 [ **XR 設定**] （在 [**發佈設定**] 下方找到）中，支援 [勾選**虛擬實境**]，並確定已新增 [ **Windows Mixed Reality SDK** ]。

        ![設定 Unity 專案](images/AzureLabs-Lab6-33.png)

    3.  在 [**發行設定**] 索引標籤的 [**功能**] 底下，檢查：

        - **InternetClient**

            ![設定 Unity 專案](images/AzureLabs-Lab6-34.png)

8.  進行這些變更之後，請關閉 [**組建設定**] 視窗。

9.  儲存專案 * 檔案 * 儲存*專案 * ** 。



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>第4章-匯入 InsideOutSphere Unity 封裝

> [!IMPORTANT]
> 如果您想要略過此課程的*Unity 設定*元件，並繼續直接進入程式碼，您可以下載這個[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)，將它匯入到您的專案中做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行**第5章**。 您仍然需要建立 Unity 專案。

在此課程中，您將需要下載名為 InsideOutSphere 的 Unity 資產套件[ **。 unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)。

如何匯入**unitypackage**：

1.  在您前方的 Unity 儀表板中，按一下畫面頂端功能表中的 **資產**，然後按一下 匯**入套件 > 自訂套件**。

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-35.png)

2.  使用檔案選擇器選取**InsideOutSphere unitypackage**套件，然後按一下 [**開啟**]。 系統會顯示此資產的元件清單。 按一下 [匯**入**] 確認匯入。

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-36.png)

3.  完成匯入之後，您會注意到有三個新的資料夾、**材質**、**型號**和**Prefabs**已新增至您的 [**資產**] 資料夾。 這種資料夾結構通常適用于 Unity 專案。

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-37.png)

    1.  開啟 [**模型**] 資料夾，您會看到**InsideOutSphere**模型已匯入。

    2.  在 [**材質**] 資料夾中，您會發現 [ **InsideOutSpheres**材質] *lambert1*，以及稱為*ButtonMaterial*的材料，這是 GazeButton 所使用的資料，您很快就會看到。

    3.  **Prefabs**資料夾包含**InsideOutSphere** prefab，其中同時包含**InsideOutSphere** *模型*和*GazeButton*。

    4.  **未包含任何程式碼**，您將會遵循此課程來撰寫程式碼。


4.  **在階層中，選取** **主要相機**物件，並更新下列元件：

    1.  **轉換**

        1.  Position = **X**：0， **Y**：0， **Z**：0。

        2. 旋轉 = **X**：0， **Y**：0， **Z**：0。

        3. 尺規**X**：1， **Y**：1， **Z**：1。

    2.  **相機**

        1. **清除旗標**：純色。

        2.  **裁剪平面**：接近：0.1，目前為6。

            ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-38.png)

5.  流覽至 [ **Prefab** ] 資料夾，然後將 [ **InsideOutSphere** ] Prefab 拖曳至 [階層 **] 面板。**

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-39.png)

6.  按一下 [ **InsideOutSphere** ] 物件旁邊的小箭**號，以**展開階層中的物件。 您會在其下看到一個名為**GazeButton**的**子**物件。 這將用來變更場景和影片。

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-40.png)

7.  在 [偵測器] 視窗中，按一下**InsideOutSphere**的 [轉換] 元件，確定已設定下列屬性：

    |            |    轉換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    轉換-旋轉   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     轉換-調整規模     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-41.png)

8.  按一下 [ **GazeButton** ] 子物件，並設定其**轉換**，如下所示：

    |            |    轉換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3。6|          **Y** 1。3        |  **Z** 0  |

    |            |    轉換-旋轉   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     轉換-調整規模     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>第5章-建立 VideoController 類別

**VideoController**類別會裝載兩個將用來從 Azure 媒體服務串流內容的影片端點。

若要建立此類別：

1.  以滑鼠右鍵按一下 [**資產] 資料夾**（位於 [**專案**] 面板中），然後按一下 [**建立 > 資料夾**]。 將資料夾命名為**Scripts**。

    ![建立 VideoController 類別](images/AzureLabs-Lab6-43.png)

    ![建立 VideoController 類別](images/AzureLabs-Lab6-44.png)

2.  按兩下 [**腳本**] 資料夾以開啟它。

3.  在資料夾內部按一下滑鼠右鍵，然後按一下 [**建立 > C\# 腳本**]。 將腳本命名為**VideoController**。

    ![建立 VideoController 類別](images/AzureLabs-Lab6-45.png)

4.  按兩下新的**VideoController**腳本，以**Visual Studio 2017**開啟它。

    ![建立 VideoController 類別](images/AzureLabs-Lab6-46.png)

5.  更新程式碼檔案頂端的命名空間，如下所示：

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  在**VideoController**類別中輸入下列變數，以及使用**喚醒（）** 方法：

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  現在是從您的 Azure 媒體服務影片輸入端點的時機：

    1.  *Video1endpoint*變數中的第一個。
    
    2.  *Video2endpoint*變數中的第二個。

    > [!WARNING]
    > 在 Unity 中使用*HTTPs*時，有版本 2017.4.1 f1 的已知問題。 如果影片在播放時提供錯誤，請嘗試改為使用 ' HTTP '。

8.  接下來，需要編輯**Start （）** 方法。 每次使用者切換場景（因而切換影片）時，就會觸發這個方法，方式是查看 [注視] 按鈕。

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  在**Start （）** 方法後面，插入**連結 playvideo （）** *IEnumerator*方法，這將用來順暢地啟動影片（因此不會出現任何斷斷續續）。

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. 您在此類別中所需的最後一個方法是**ChangeScene （）** 方法，它會用來在場景之間交換。

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > **ChangeScene （）** 方法會使用一個方便的 C\# 功能，稱為「*條件運算子*」。 如此一來，就可以檢查條件，然後根據檢查結果傳回的值，全都在單一語句內。 [若要深入瞭解條件運算子](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)，請遵循此連結。

11. 請先儲存 Visual Studio 中的變更，再返回 Unity。

12. 回到 Unity 編輯器中，按一下 [從] {. 底線} [**腳本**] 資料夾中的 [ **VideoController** ] 類別，然後拖曳至 [階層 **] 面板中**的**主要相機**物件。

13. 按一下**主攝影機**並查看 [**檢查] 面板**。 您會發現，在新加入的腳本元件中，有一個欄位具有空的值。 這是參考欄位，其以程式碼內的公用變數為目標。

14. 將 [ **InsideOutSphere** ] 物件從 [階層]**面板**拖曳至 [**球體**] 位置，如下圖所示。

    ![建立 VideoController 類別](images/AzureLabs-Lab6-47.png)
    ![建立 VideoController 類別](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>第6章-建立注視課程

此類別負責建立將從**主要相機**向前投射的**Raycast** ，以偵測使用者正在查看的物件。 在此情況下， **Raycast**將需要識別使用者是否正在查看場景中的**GazeButton**物件，並觸發行為。

若要建立此類別：

1.  移至您先前建立的**腳本**資料夾。

2.  以滑鼠右鍵按一下 [**專案**] 面板中的 [*建立** C\# 腳本] * *。 將腳本命名為**注視**。

3.  按兩下新的***注視***腳本，使用**Visual Studio 2017**加以開啟。

4.  請確定下列命名空間位於腳本的最上方，並移除其他任何專案：

    ```csharp
    using UnityEngine;
    ```

5.  然後在**注視**類別內新增下列變數：

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  現在必須加入**喚醒（）** 和**Start （）** 方法的程式碼。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  在**Update （）** 方法中新增下列程式碼，以投影 Raycast 並偵測目標叫用：

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  請先儲存 Visual Studio 中的變更，再返回 Unity。

9.  按一下 [腳本] 資料夾中的 [**注視**] 類別，並將其拖曳至 [階層 **] 面板中**的主要相機物件。

## <a name="chapter-7---setup-the-two-unity-scenes"></a>第7章-設定兩個 Unity 場景

本章的目的是要設定兩個場景，分別裝載影片以進行串流。 您會複製已建立的場景，這樣就不需要再次設定它，但您會接著編輯新場景，讓*GazeButton*物件位於不同的位置，並具有不同的外觀。 這是為了示範如何在幕後進行變更。

1.  請前往 檔案 **> 另存場景**... 來執行此動作。儲存 視窗隨即出現。 按一下 [**新增資料夾**] 按鈕。

    ![第7章-設定兩個 Unity 場景](images/AzureLabs-Lab6-49.png)

2.  將資料夾命名為**場景**。

3.  [**儲存場景**] 視窗仍會開啟。 開啟新建立的 [**幕後**] 資料夾。

4.  在 [**檔案名：** 文字] 欄位中，輸入**VideoScene1**，然後按 [**儲存**]。

5.  回到 Unity，開啟您的**幕後**資料夾，然後以滑鼠左鍵按一下您的**VideoScene1**檔案。 使用您的鍵盤，然後按下**Ctrl + D** ，將會複製該場景

    > [!TIP]
    > 您也可以流覽至 [**編輯 > 重複**] 來執行**重複**的命令。

6.  Unity 會自動遞增場景名稱，但仍然檢查，以確保它符合先前插入的程式碼。

    >  您應該有**VideoScene1**和**VideoScene2**。

7.  使用您的兩個場景，移至 [檔案] **> [組建設定**]。 在 [**組建設定**] 視窗開啟的情況下，將您的場景拖曳至 [**組建中的場景**] 區段。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > 您可以透過按住**Ctrl**鍵，然後以滑鼠左鍵按一下每個場景，最後再拖曳兩者，從**幕後**資料夾中選取這兩個場景。

8.  關閉 [**組建設定**] 視窗，然後按兩下 [ **VideoScene2**]。

9.  當第二個場景開啟時，按一下**InsideOutSphere**的 [ **GazeButton** ] 子物件，並設定其轉換，如下所示：

    |            |    轉換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1。3         | **Z** 3。6 |

    |            |    轉換-旋轉   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     轉換-調整規模     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. 在仍選取**GazeButton**子系的情況下，查看 [**檢查**] 和 [**網格] 篩選準則**。 按一下 [**網格**參考] 欄位旁的小目標：

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-51.png)

11. [**選取網格**] 快顯視窗隨即出現。 按兩下**資產**清單中的 [ **Cube**網格]。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-52.png)

12. **網格篩選器**將會更新，現在是一個**Cube**。 現在，按一下 [**球體碰撞**件] 旁的**齒輪**圖示，然後按一下 [**移除元件**]，以刪除此物件中的碰撞。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-53.png)

13. 在仍選取**GazeButton**的情況下，按一下偵測**器**底部的 [**新增元件**] 按鈕。 在 [搜尋] 欄位中，輸入**box**和**box 碰撞**會是一個選項，按一下該方塊，將方塊**碰撞**程式新增至您的**GazeButton**物件。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-54.png)

14. **GazeButton**現在已部分更新，看起來會不同，不過，您現在會建立新的資料，讓它看起來完全**不同，而且**比第一個場景中的物件更容易辨識為不同的物件。

15. 在 [**專案] 面板**中，流覽至您的 [**材質**] 資料夾。 複製**ButtonMaterial**材質（在鍵盤上按**Ctrl** + **D** ，或以滑鼠右鍵按一下**材質**，然後從 [**編輯**檔案] 功能表選項選取 [**複製**]）。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-55.png)
    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-56.png)

16. 選取新的**ButtonMaterial**材質（名為**ButtonMaterial 1**），然後在偵測**器**中，按一下 [ **Albedo**色彩] 視窗。 隨即會出現一個快顯視窗，您可以在其中選取另一個色彩（選擇您喜歡的方式），然後關閉快顯視窗。 此材質會是它自己的實例，與原始的不同。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-57.png)

17. 將**新的資料拖曳**到**GazeButton**子系上，以立即完整更新其外觀，讓它可以輕鬆地從第一個場景按鈕來區分。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-58.png)

18. 此時，您可以在建立 UWP 專案之前，先在編輯器中測試專案。

    -  按下**編輯器**中的 [**播放**] 按鈕，然後戴頭戴式裝置。

        ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-59.png)

19. 查看兩個**GazeButton**物件，以在第一和第二部影片之間切換。

## <a name="chapter-8---build-the-uwp-solution"></a>第8章-建立 UWP 解決方案

一旦確定編輯器沒有任何錯誤，您就可以開始建立。

若要建立：

1.  按一下 檔案 **> 儲存** 來儲存目前的場景。

2.  勾選名為**Unity C\# 專案**的方塊（這很重要，因為它可讓您在組建完成後編輯類別）。

3.  移至 [檔案] **> [組建設定**]，按一下 [**組建**]。

4.  系統會提示您選取要在其中建立解決方案的資料夾。

5.  建立**組建**資料夾，並在該資料夾內建立另一個資料夾，並使用您選擇的適當名稱。

6.  按一下您的新資料夾，然後按一下 [**選取資料夾**]，選擇該資料夾，在該位置開始組建。

    ![第8章--建立 UWP 解決方案](images/AzureLabs-Lab6-60.png)
    ![第8章--建立 UWP 解決方案](images/AzureLabs-Lab6-61.png)

7.  Unity 完成建立（可能需要一些時間）之後，它會在組建的位置開啟 [檔案**瀏覽器**] 視窗。

## <a name="chapter-9---deploy-on-local-machine"></a>第9章-在本機電腦上部署

組建完成之後，[檔案**瀏覽器**] 視窗就會出現在組建的位置。 開啟您已命名並建立的資料夾，然後按兩下該資料夾中的解決方案（.sln）檔案，以 Visual Studio 2017 開啟您的解決方案。

剩下的工作就是將您的應用程式部署到您的電腦（或*本機電腦*）。

若要部署到本機電腦：

1.  在**Visual Studio 2017**中，開啟剛建立的方案檔。

2.  在**解決方案平臺**中，選取 [ **x86]、[本機電腦**]。

3.  在 [**解決方案**設定] 中，選取 [ **Debug**]。

    ![第9章--在本機電腦上部署](images/AzureLabs-Lab6-62.png)

4.  您現在必須將任何套件還原至您的解決方案。 以滑鼠右鍵按一下您的**方案**，然後按一下 [**還原解決方案的 NuGet 套件**...]

    > [!NOTE] 
    > 這是因為 Unity 所建立的套件必須設為目標，才能與您的本機電腦參考搭配使用。

5.  移至 [**建立] 功能表**，然後按一下 [**部署方案**]，將應用程式側載至您的電腦。 Visual Studio 會先建立並部署您的應用程式。

6.  您的應用程式現在應該會出現在已安裝的應用程式清單中，並準備好啟動。

    ![第9章--在本機電腦上部署](images/AzureLabs-Lab6-63.png)

當您執行 Mixed Reality 應用程式時，您會在應用程式內使用的**InsideOutSphere**模型中。 這個球體將是影片的串流目標位置，提供內送影片的360度觀點（這種觀點的 filmed）。 如果影片需要幾秒鐘的時間才能載入，您的應用程式會受限於可用的網際網路速度，因為必須提取並下載影片，才能串流至您的應用程式。
當您準備好時，請撥雲見日紅色球體來變更場景並開啟第二個影片！ 然後您可以隨意使用第二個場景中的藍色 cube！

## <a name="your-finished-azure-media-service-application"></a>您完成的 Azure 媒體服務應用程式
 
恭喜，您建立了一個混合現實應用程式，利用 Azure 媒體服務串流處理360影片。

![實驗室結果](images/AzureLabs-Lab6-00.png)

![實驗室結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>額外練習

**練習1**

在本教學課程中，您可以完全只使用單一場景來變更影片。 試驗您的應用程式，並使其進入單一場景！ 甚至可能將另一部影片新增至混合。

**練習2**

使用 Azure 和 Unity 進行實驗，並嘗試執行此功能，讓應用程式根據網際網路連線的強度，自動選取不同檔案大小的影片。


