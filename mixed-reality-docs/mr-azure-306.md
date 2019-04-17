---
title: MR 和 Azure 306-串流處理視訊
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 媒體服務。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境，academy、 unity、 教學課程、 api，媒體服務，串流處理視訊，360、 沉浸式 vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591607"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR 和 Azure 306:串流處理視訊

![最終產品-開始](images/AzureLabs-Lab6-00.png)
![最終成品-啟動](images/AzureLabs-Lab6-01.png)

在本課程中，您將學習如何連接到 Windows 混合實境的 VR 體驗，以使串流 360 度的視訊播放沈浸式耳機上的 您的 Azure 媒體服務。 

**Azure 媒體服務**是服務的集合，可讓您廣播品質的影片串流服務可接觸到現今最熱門的行動裝置的觀眾。 如需詳細資訊，請瀏覽[Azure 媒體服務頁面](https://azure.microsoft.com/services/media-services)。

完成本課程之後，您會有的混合的實境沈浸式耳機應用程式，可以執行下列作業：

1. 擷取來自的 360 度影片**Azure 儲存體**，透過**Azure 媒體服務**。

2. 顯示 Unity 場景中擷取的 360 度影片。

3. 使用兩個不同的影片的兩個場景之間巡覽。

在您的應用程式，則您對於如何將整合結果進行設計。 本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。 它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 306:串流處理視訊</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程專為具有基礎經驗的 Unity 開發人員和C#。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試並驗證時寫入 (2018 年)。 中所示，您可以自由使用最新的軟體[安裝工具文章](install-the-tools.md)，不過它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體與以下所列.

我們建議下列的硬體和軟體這堂課程：

- 開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發
- [Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)
- Azure 的安裝程式和資料擷取的網際網路存取
- 兩個 mp4 格式的 360 度影片 (您可以找到一些免費的影片[在此下載頁面](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>開始之前

1.  若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。
2.  設定並測試混合實境沈浸式耳機。

    > [!NOTE]
    > 您將會**不**本課程所需動作的控制器。 如果您需要支援沈浸式耳機的設定，請按一下[連結，有關如何設定 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>第 1-Azure 入口網站： 建立 Azure 儲存體帳戶

若要使用**Azure 儲存體服務**，您必須建立及設定**儲存體帳戶**在 Azure 入口網站中。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**儲存體帳戶**左側功能表中。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-02.png)

3.  在 **儲存體帳戶**索引標籤上，按一下**新增**。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-03.png)

4.  在 [**建立儲存體帳戶**] 索引標籤：

    1.  插入**名稱**您的帳戶，請留意這個欄位只接受數字和小寫字母。

    2.  針對**部署模型**選取**Resource manager**。

    3.  針對**帳戶種類**，選取**儲存體 (一般用途 v1)**。

    4.  針對**效能**，選取**標準 *。**

    5.  針對**複寫**選取**本地備援儲存體 (LRS)**。

    6.  離開**需要安全傳輸**作為**停用**。

    7.  選取 **訂用帳戶**。

    8.  選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。

    9.  判斷**位置**資源群組 （如果您要建立新的資源群組）。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。

5.  您必須確認您已了解這些條款和條件套用到此服務。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-04.png)

6.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

7.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-05.png)

8.  此時您就不必遵循資源，只需移至下一步 一章。

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>章節 2-在 Azure 入口網站： 建立媒體服務

若要使用 Azure 媒體服務，您必須設定可供使用 （其中帳戶持有者必須是系統管理員） 的應用程式服務的執行個體。

1.  在 Azure 入口網站中，按一下**建立資源**在左上角，，然後搜尋**媒體服務**按下**Enter**。 您想在目前的資源都有粉紅色的圖示;按一下此選項，以顯示新的頁面。

    ![Azure 入口網站](images/AzureLabs-Lab6-06.png)

2.  新的頁面將提供的描述**媒體服務**。 在此提示的左下方，按一下**建立**按鈕，以建立與此服務的關聯。

    ![Azure 入口網站](images/AzureLabs-Lab6-07.png)

3.  一旦您按下**建立**面板會顯示您要提供您新的媒體服務相關的一些詳細資料：

    1.  插入您想要**帳戶名稱**此服務執行個體。

    2.  選取 **訂用帳戶**。

    3. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。 
    
    > 如果您想要深入了解 Azure 資源群組，請遵循此[如何管理 Azure 資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  判斷**位置**資源群組 （如果您要建立新的資源群組）。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。

    5.  針對**儲存體帳戶**區段中，按一下**請選取...** 區段，然後按一下**儲存體帳戶**在最後一章中所建立。

    6.  您也必須確認您已了解這些條款和條件套用到此服務。

    7.  按一下 [建立] 。

        ![Azure 入口網站](images/AzureLabs-Lab6-08.png)

4.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

5.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![Azure 入口網站](images/AzureLabs-Lab6-09.png)

6.  按一下通知，以探索新的服務執行個體。

    ![Azure 入口網站](images/AzureLabs-Lab6-10.png)

7.  按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。

8.  在 [新媒體服務] 頁面的左側面板中按一下**資產**連結，也就是關於偶數的清單。

9.  在下一步 頁面上，左上角的頁面上，按一下**上傳**。

    ![Azure 入口網站](images/AzureLabs-Lab6-11.png)

10. 按一下 **資料夾**圖示以瀏覽檔案，並選取您想要串流處理的第一次 360 視訊。 
    
    > 您可以遵循此[連結以下載範例視訊](https://vimeo.com/214401712)。

    ![Azure 入口網站](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> 長檔名可能會使用編碼器的時發生問題： 因此若要確保影片並沒有問題，請考慮縮短您的視訊檔案名稱的長度。

11. 完成上傳影片時，進度列會變成綠色。

    ![Azure 入口網站](images/AzureLabs-Lab6-13.png)

12. 按一下上方的文字 (**yourservicename-資產**) 以返回**資產**頁面。

13. 您會發現，您的影片已成功上傳。 按一下它。

    ![Azure 入口網站](images/AzureLabs-Lab6-14.png)

14. 將您重新導向頁面會顯示您的影片的相關詳細資訊。 若要能夠使用您需要進行編碼，因此，依序按一下您的影片**編碼** 按鈕，在頁面的左上方。

    ![Azure 入口網站](images/AzureLabs-Lab6-15.png)

15. 新的面板會出現在右側，其中您可以在此處設定編碼選項，為您的檔案。 設定下列屬性 （部分已經將預設）：

    1.  **媒體編碼器名稱*媒體編碼器標準***

    2.  **編碼預設*內容自動調整的多個位元速率 MP4***

    3.  **作業名稱*Video1.mp4 媒體編碼器標準處理***

    4.  **輸出媒體資產名稱*Video1.mp4-Media Encoder Standard 編碼***

        ![Azure 入口網站](images/AzureLabs-Lab6-16.png)

16. 按一下 [建立] 按鈕。

17. 您會注意到具有的列**新增的編碼工作**按一下該列，面板會顯示與顯示的編碼方式進行。

    ![Azure 入口網站](images/AzureLabs-Lab6-17.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-18.png)

18. 等候作業完成。 完成之後，放心地關閉具有 'X' 右上方的面板的面板。

    ![Azure 入口網站](images/AzureLabs-Lab6-19.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > 這會帶，時間取決於您的影片檔案大小。 此程序可能需要一段時間。

19. 既然已建立的視訊編碼的版本，您可以發行它，使其可供存取。 若要這樣做，請按一下藍色的連結**資產**返回至 [資產] 頁面。

    ![Azure 入口網站](images/AzureLabs-Lab6-21.png)

20. 您會看到您的影片，以及另一個，這是 * * 資產類型 * 多位元速率 MP4 * * *。

    ![Azure 入口網站](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > 您可能會注意到新的資產，以及您初始的影片*未知*，而且它是具有 '0' 位元組**大小**，只重新整理您的視窗來進行更新。

21. 按一下這個新的資產。

    ![Azure 入口網站](images/AzureLabs-Lab6-23.png)

22. 您會看到類似的面板，您所使用之前，您也可以只是這是不同的資產。 按一下 **發佈**按鈕位於頁面頂端中央。

    ![Azure 入口網站](images/AzureLabs-Lab6-24.png)

23. 若要設定將會提示您**定位器**，這是進入點，為您的資產中的檔案/秒。 您的案例中，設定下列屬性：

    1.  **定位器類型** > **漸進式**。

    2.  **日期**並**時間**會從您目前的日期，為您設定，以在未來的時間 （在此情況下的 100 年）。 將保留為是或將它變更為符合。

    > [!NOTE]
    > 如需有關定位器，以及您可以選擇的詳細資訊，請瀏覽[Azure 媒體服務文件](https://docs.microsoft.com/azure/media-services/media-services-concepts)。

24. 在該面板下方，按一下**新增** 按鈕。

    ![Azure 入口網站](images/AzureLabs-Lab6-25.png)

25. 您的影片，現在已發行，並可以串流，方法是使用其端點。 進一步向下的頁面**檔案**一節。 這是影片的要編碼的不同版本，您。 選取其中一個最高可能解決方式 （在下圖中很 1920 x 960 檔案），則會出現在右邊面板和。 您會在這裡找到**下載 URL**。 複製這**端點**因為您將在稍後的程式碼中使用它。

    ![Azure 入口網站](images/AzureLabs-Lab6-26.png)    

    ![Azure 入口網站](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > 您也可以按下**播放**按鈕來播放影片，並加以測試。

26. 您現在需要在這個實驗室中，您將使用第二個影片上傳。 請遵循上述步驟，重複執行相同的程序，第二個影片。 請確定您複製第二個**端點**也。 使用下列[連結以下載第二個視訊](https://vimeo.com/214402865)。

27. 一旦已發佈這兩個影片，您就準備好移至下一步 一章。

## <a name="chapter-3---setting-up-the-unity-project"></a>第 3 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟**Unity**然後按一下**新增**。 

    ![Azure 入口網站](images/AzureLabs-Lab6-28.png)

2.  您現在需要提供 Unity 專案名稱、 插入**MR\_360VideoStreaming**。 請確定專案類型設定為**3D**。 適用於您的某處設定的位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![Azure 入口網站](images/AzureLabs-Lab6-29.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設定為**Visual Studio。** 移至***編輯**喜好設定*** ，然後在新視窗中，瀏覽**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![Azure 入口網站](images/AzureLabs-Lab6-30.png)

4.  接下來，移至***檔案**組建設定*** ，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。

5.  此外，請確定：

    1. **裝置為目標**設為**任何裝置。**
    
    2.  **建置型別**設為**D3D。**

    3.  **SDK**設為**最新安裝。**

    4.  **Visual Studio 版本**設為**最新安裝。**

    5.  **建置並執行**設為**本機電腦。**

    6.  不要擔心設定**場景**現在，當您將會設定這些更新版本。

    7.  其餘的設定應該保持為預設值，現在。

        ![設定 Unity 專案](images/AzureLabs-Lab6-31.png)

6.  中**組建設定**視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。 

7. 在此窗格中，少數設定需要驗證：

    1.  在 [**其他設定**] 索引標籤：

        1.  **指令碼****執行階段版本**應該**穩定**（.NET 3.5 對等）。

        2. **指令碼後端**應該是 **.NET。**

        3. **API 相容性層級**應該是 **.NET 4.6。**

            ![設定 Unity 專案](images/AzureLabs-Lab6-32.png)

    2.  在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。

        ![設定 Unity 專案](images/AzureLabs-Lab6-33.png)

    3.  內**發佈設定**索引標籤之下**功能**，檢查：

        - **InternetClient**

            ![設定 Unity 專案](images/AzureLabs-Lab6-34.png)

8.  一旦您進行這些變更，關閉**組建設定**視窗。

9.  儲存您的專案 **檔案** 儲存專案。



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>第 4 章-匯入 InsideOutSphere Unity 封裝

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)，它匯入到您的專案做為[ **自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從**第 5 章**。 您仍然必須建立 Unity 專案。

本課程，您必須下載 Unity 資產套件，稱為[ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)。

如何匯入**unitypackage**:

1.  您面前的 Unity 儀表板中，按一下**資產**在畫面頂端的功能表，然後按一下**匯入封裝 > 自訂封裝**。

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-35.png)

2.  使用檔案選擇器選取**InsideOutSphere.unitypackage**封裝，然後按一下**開啟**。 為此資產的元件的清單會顯示給您。 確認匯入，依序按一下**匯入**。

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-36.png)

3.  完成匯入後，您會發現三個新的資料夾**材料**，**模型**，和**Prefabs**，已新增至您**資產**資料夾。 這種資料夾結構是典型的 Unity 專案。

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-37.png)

    1.  開啟**模型**資料夾，而您會看到**InsideOutSphere**已匯入模型。

    2.  內**材料**資料夾，您會找到**InsideOutSpheres**材料*lambert1*，以及呼叫材質*ButtonMaterial*，這由 GazeButton，您就會立即看到。

    3.  **Prefabs**資料夾包含**InsideOutSphere** prefab 其中同時包含**InsideOutSphere** *模型*並*GazeButton*。

    4.  **不包含任何程式碼**，您將會依照本課程中撰寫程式碼。


4.  內**階層**，選取**Main Camera**物件，並更新下列元件：

    1.  **轉換**

        1.  位置 = **X**:0， **Y**:0， **Z**:0.

        2. 旋轉 = **X**:0， **Y**:0， **Z**:0.

        3. 縮放比例**X**:1， **Y**:1， **Z**:1.

    2.  **相機**

        1. **清除旗標**:不透明色彩。

        2.  **裁剪平面**:附近：0.1，到目前為止：6.

            ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-38.png)

5.  瀏覽至**Prefab**資料夾，然後再拖曳**InsideOutSphere**至 prefab**階層**面板。

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-39.png)

6.  依序展開**InsideOutSphere**物件內**階層**按一下它旁邊的小箭號。 您會看到**子系**下方，叫做物件**GazeButton**。 這會用來變更場景，因此影片。

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-40.png)

7.  在偵測器視窗中按一下**InsideOutSphere**的轉換元件，請確定已設定下列屬性：

    |            |    轉換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    轉換的旋轉   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     轉換為小數位數     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-41.png)

8.  按一下  **GazeButton**子物件，並設定其**轉換**，如下所示：

    |            |    轉換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    轉換的旋轉   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     轉換為小數位數     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![匯入 InsideOutSphere Unity 封裝](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>第 5-建立 VideoController 類別

**VideoController**類別裝載兩個視訊的端點，將用來串流處理從 Azure 媒體服務內容。

若要建立此類別：

1.  以滑鼠右鍵按一下**Assets 資料夾**，位於**專案**] 面板中，然後按一下 [**建立 > 資料夾**。 將資料夾命名**指令碼**。

    ![建立 VideoController 類別](images/AzureLabs-Lab6-43.png)

    ![建立 VideoController 類別](images/AzureLabs-Lab6-44.png)

2.  按兩下**指令碼**資料夾將它開啟。

3.  在資料夾中，以滑鼠右鍵按一下，然後按一下 **建立 > C\#指令碼**。 指令碼命名**VideoController**。

    ![建立 VideoController 類別](images/AzureLabs-Lab6-45.png)

4.  按兩下新**VideoController**指令碼，以開啟它**Visual Studio 2017。**

    ![建立 VideoController 類別](images/AzureLabs-Lab6-46.png)

5.  更新的程式碼檔案頂端的命名空間如下所示：

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  輸入中的下列變數**VideoController**類別，以及使用**Awake()** 方法：

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

7.  現在是從您的 Azure 媒體服務影片輸入端點的時間：

    1.  到第一個*video1endpoint*變數。
    
    2.  到第二個*video2endpoint*變數。

    > [!WARNING]
    > 沒有使用的已知的問題*https* Unity 中，使用版本 2017.4.1f1 內。 如果影片提供 play 上的錯誤，請嘗試改為使用 'http'。

8.  下一步 **start （)** 方法需要進行編輯。 每次使用者切換場景 （因此切換視訊），藉由查看視線 按鈕，就會觸發這個方法。

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  遵循**start （)** 方法，插入**PlayVideo()** *IEnumerator*方法，將用來啟動影片，順暢地 （因此會看到不間斷）。

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

10. 您需要為這個類別的最後一個方法**ChangeScene()** 方法，將場景之間交換使用。

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > **ChangeScene()** 方法會使用便利 C\#功能，稱為*條件運算子*。 這是用來進行檢查的條件，然後值根據傳回的檢查，全部都在單一陳述式內的結果。 請遵循這[連結以深入了解條件式運算子](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)。

11. 在 Visual Studio 中儲存的變更，然後再回到 Unity。

12. 傳回在 Unity 編輯器中，按一下並拖曳**VideoController**類別 [from] {.underline}**指令碼**資料夾**Main Camera**物件**階層**面板。

13. 按一下  **Main Camera**並查看**Inspector 面板**。 您會注意到，在新加入的指令碼元件，具有空值的欄位。 這是參考欄位，其以您的程式碼內的公用變數為目標。

14. 拖曳**InsideOutSphere**物件**階層面板**來**球體**位置，如下圖所示。

    ![建立 VideoController 類別](images/AzureLabs-Lab6-47.png)
    ![建立 VideoController 類別](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>章節 6-建立視線類別

這個類別會負責建立**Raycast** ，將 beprojected 從轉寄**Main Camera**，來偵測使用者查看的物件。 在此情況下， **Raycast**就必須找出，如果使用者查看**GazeButton**場景中物件，並會觸發的行為。

若要建立此類別：

1.  移至**指令碼**您先前建立的資料夾。

2.  以滑鼠右鍵按一下**專案** 面板中，**建立** C\#指令碼 * *。 指令碼命名**視線**。

3.  按兩下新***視線***指令碼，以開啟它**Visual Studio 2017。**

4.  請確認下列命名空間頂端的 指令碼，然後移除任何其他：

    ```csharp
    using UnityEngine;
    ```

5.  然後新增下列變數內**視線**類別：

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

6.  程式碼**Awake()** 並**start （)** 方法現在需要加入。

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

7.  新增下列程式碼**update （)** 投射 Raycast 和偵測目標叫用的方法：

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

8.  在 Visual Studio 中儲存的變更，然後再回到 Unity。

9.  按一下並拖曳**視線**指令碼 資料夾中的 Main Camera 物件的類別**階層**面板。

## <a name="chapter-7---setup-the-two-unity-scenes"></a>第 7 章-安裝這兩個 Unity 場景

本指南的用途是設定在兩個場景，每個裝載視訊資料流。 讓您不需要再次設定然後，您會編輯新的場景，不過，您將複製的場景，您已經建立，以便*GazeButton*物件是在不同的位置，而且有不同的外觀。 這是要說明如何變更場景之間。

1.  這樣做的方法是前往**檔案 > 儲存的場景為...**.儲存視窗會出現。 按一下 [**新的資料夾**] 按鈕。

    ![第 7 章-安裝這兩個 Unity 場景](images/AzureLabs-Lab6-49.png)

2.  將資料夾命名**場景**。

3.  **儲存場景**視窗仍會開啟。 開啟您新建**場景**資料夾。

4.  在 **檔案名稱：** 文字欄位中，輸入**VideoScene1**，然後按**儲存**。

5.  傳回在 Unity 中，開啟您**場景**資料夾，然後以滑鼠左鍵按一下您**VideoScene1**檔案。 使用鍵盤，按下**Ctrl + D**您將會複製該場景

    > [!TIP]
    > **重複**也可以瀏覽至執行命令**編輯 > 重複**。

6.  Unity 會自動遞增場景名稱數，但，檢查以確定它符合先前插入的程式碼。

    >  您應該**VideoScene1**並**VideoScene2**。

7.  使用您的兩個場景，請移至**檔案 > 組建設定**。 與**Build Settings**視窗中開啟，拖曳至您場景**組建中的場景**一節。

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > 您可以選取這兩個您場景，從您**場景**資料夾保存透過**Ctrl**按鈕，然後用滑鼠左鍵按一下每個場景，並最後進行拖曳，讓兩者之間。

8.  關閉**Build Settings**  視窗中，並按兩下**VideoScene2**。

9.  開啟第二個場景，請按一下 上**GazeButton**的子物件**InsideOutSphere**，並將其轉換，如下所示：

    |            |    轉換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    轉換的旋轉   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     轉換為小數位數     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. 與**GazeButton**仍已選取，尋找位於子**Inspector**並在**Mesh 的篩選器**。 接下來按一下小目標**Mesh**參考欄位：

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-51.png)

11. A**選取 Mesh**快顯視窗會出現。 按兩下**Cube**從清單中的網狀結構**資產**。

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-52.png)

12. **Mesh 的篩選條件**會更新，而且現在**Cube**。 現在，按一下 **齒輪**旁的圖示**球體 Collider**然後按一下**移除元件**，若要從這個物件刪除 collider。

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-53.png)

13. 與**GazeButton**保持選取，按一下**新增元件**底部的按鈕**Inspector**。 在 [搜尋] 欄位中，輸入**方塊**，和**方塊 Collider**會是一個選項，按一下該選項，以新增**方塊 Collider**至您**GazeButton**物件.

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-54.png)

14. **GazeButton**是部分更新，現在看起來不同，不過，您現在將建立新**材料**，好讓它看起來完全不同，而且容易比視為不同的物件，第一個場景中的物件。

15. 瀏覽至您**材料**資料夾內 **[專案] 面板**。 重複**ButtonMaterial**材料 (按下**Ctrl** + **D**鍵盤上按滑鼠左鍵**材料**，然後從**編輯**檔案 功能表選項中，選取**重複**)。

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-55.png)
    ![章 7--設定兩個的 Unity 場景](images/AzureLabs-Lab6-56.png)

16. 選取新**ButtonMaterial**材料 (這裡稱為**ButtonMaterial 1**)，內**Inspector**，按一下  **Albedo**色彩視窗。 會出現快顯視窗，您可以在其中選取另一種色彩 （選擇您喜歡的色彩），然後關閉快顯視窗。 資料將會有自己的執行個體，和不同原始。

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-57.png)

17. 拖曳新**材料**拖曳至**GazeButton**子系，現在它的外觀，完全更新，使其容易分辨從第一個場景按鈕。

    ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-58.png)

18. 此時您可以在編輯器中測試專案之前建置的 UWP 專案。

    -  按下**播放**按鈕**編輯器**和戴上耳機。

        ![第 7 章-設定兩個的 Unity 場景](images/AzureLabs-Lab6-59.png)

19. 看看這兩個**GazeButton**切換的第一個和第二個視訊的物件。

## <a name="chapter-8---build-the-uwp-solution"></a>第 8 章-建置 UWP 方案

一旦確定編輯器沒有任何錯誤，您就準備好要建置的。

若要建置：

1.  按一下儲存目前的場景**檔案 > 儲存**。

2.  核取方塊稱為**Unity C\#專案**（這是重要因為這樣可讓您完成建置後編輯類別）。

3.  移至**檔案 > Build Settings**，按一下**建置**。

4.  系統會提示您選取要 buildthe 方案的資料夾。

5.  建立**建置**資料夾和該資料夾中建立適當的名稱，您選擇的另一個資料夾。

6.  按一下您的新資料夾，然後按一下**選取資料夾**，因此，若要選擇該資料夾中，若要開始在該位置的組建。

    ![第 8 章-建置的 UWP 方案](images/AzureLabs-Lab6-60.png)
    ![章 8-建置的 UWP 方案](images/AzureLabs-Lab6-61.png)

7.  一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置。

## <a name="chapter-9---deploy-on-local-machine"></a>第 9-將本機電腦上部署

完成組建後，**檔案總管**視窗將會出現在您的組建的位置。 開啟的資料夾命名，並建置，然後按兩下該資料夾，若要使用 Visual Studio 2017 中開啟您的方案中的方案 (.sln) 檔案。

只剩下来為應用程式部署至您的電腦 (或*本機電腦*)。

若要部署到本機電腦：

1.  在  **Visual Studio 2017**，開啟剛建立的方案檔。

2.  在 **的方案平台**，選取**x86，本機電腦**。

3.  在 **方案組態**選取**偵錯**。

    ![第 9 章-部署在本機電腦上](images/AzureLabs-Lab6-62.png)

4.  您現在必須將任何套件還原到您的解決方案。 以滑鼠右鍵按一下您**解決方案**，然後按一下**還原方案的 NuGet 套件...**

    > [!NOTE] 
    > 這是因為 Unity 建置的套件需要為目標來使用您本機電腦的參考。

5.  移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。 Visual Studio 會先建置，然後再部署您的應用程式。

6.  您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。

    ![第 9 章-部署在本機電腦上](images/AzureLabs-Lab6-63.png)

當您執行的混合實境應用程式時，您將會位於內**InsideOutSphere**用您的應用程式內的模型。 此球形會將串流處理視訊，提供 360 度檢視，連入的視訊 （這圖書館這種觀點來看）。 不會感到驚訝的影片需要幾秒鐘的時間載入的如果您的應用程式受限於可用的網際網路速度，因為視訊必須擷取並下載，因此以串流處理至您的應用程式。
當您準備好時，變更場景，並開啟第二段影片中，在紅色球體 gazing ！ 然後可以自由回到上一頁，使用第二個場景中的藍色的立方體 ！

## <a name="your-finished-azure-media-service-application"></a>您已完成的 Azure 媒體服務應用程式
 
恭喜，您所建立的混合的實境應用程式，利用 Azure 媒體服務來將 360 的視訊串流處理。

![實驗室結果](images/AzureLabs-Lab6-00.png)

![實驗室結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Bonus 練習

**練習 1**

完全可以只使用單一的場景變更這個教學課程中的影片。 試驗您的應用程式，並使它成為單一場景 ！ 或許甚至是另一個將影片新增至混合。

**練習 2**

體驗 Azure 和 Unity，並嘗試實作應用程式，以自動選取 使用不同的檔案大小，取決於網際網路連線的強度影片的能力。


