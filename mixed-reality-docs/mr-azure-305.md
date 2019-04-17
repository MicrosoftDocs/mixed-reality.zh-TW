---
title: MR 和 Azure 305-函式和儲存體
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 儲存體和函式。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 函式、 儲存體、 hololens、 vr 沈浸式，
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591278"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR 和 Azure 305:函式和儲存體

![最終產品-開始](images/AzureLabs-Lab5-00.png)

在此課程中，您將學習如何建立和使用 Azure Functions 及儲存與 Azure 儲存體資源，在混合的實境應用程式中的資料。

*Azure Functions*是 Microsoft 服務，可讓開發人員執行程式碼片段，'函式'，在 Azure 中。 這可用來將工作委派給雲端，而不是您本機的應用程式，可以有許多優點。 *Azure Functions*支援數種開發語言，包括 C\#，F\#、 Node.js、 Java 和 PHP。 如需詳細資訊，請瀏覽[Azure Functions 文件](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

*Azure 儲存體*是 Microsoft 雲端服務，可讓開發人員可以使用儲存資料，它會是高度可用、 安全、 持久、 可擴充和備援的保險。 這表示 Microsoft 會為您處理所有的維護，以及關鍵的問題。 如需詳細資訊，請瀏覽[Azure 儲存體文章](https://docs.microsoft.com/azure/storage/common/storage-introduction)。

完成本課程之後，您必須能夠執行下列作業的混合的實境耳機沈浸式應用程式：

1.  允許使用者視線周圍的場景。
2.  觸發程序繁衍 (sprawning) 物件時使用者 gazes 在 3D 'button'。
3.  繁衍 （spawn） 的物件將會選擇 Azure 函式。
4.  因為每個物件會繁衍，應用程式將會儲存中的物件型別*Azure 檔案*，位於*Azure 儲存體*。
5.  在第二次， *Azure 檔案*會擷取此項目，與用來重新執行先前的執行個體的應用程式的繁衍動作的資料。

在您的應用程式，則您對於如何將整合結果進行設計。 本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。 它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 和 Azure 305:函式和儲存體</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。 當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。

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
- 建立 Azure 資源的 Azure 帳戶的訂用帳戶
- Azure 的安裝程式和資料擷取的網際網路存取

## <a name="before-you-start"></a>開始之前

若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。

## <a name="chapter-1---the-azure-portal"></a>第 1 章-Azure 入口網站

若要使用**Azure 儲存體服務**，您必須建立及設定**儲存體帳戶**在 Azure 入口網站中。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**新增**在左上角，，然後搜尋*儲存體帳戶*，然後按一下**Enter**。

    ![azure 儲存體搜尋](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > 單字**的新**可能已取代為**建立資源**，較新的入口網站中。

3.  新的頁面將提供的描述*Azure 儲存體帳戶*服務。 在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。

    ![建立服務](images/AzureLabs-Lab5-02.png)

4.  一旦您按下**建立**:

    1.  插入*名稱*您的帳戶，請留意這個欄位只接受數字和小寫字母。

    2.  針對*部署模型*，選取**Resource manager**。

    3.  針對*帳戶種類*，選取**儲存體 (一般用途 v1)**。

    4.  判斷*位置*資源群組 （如果您要建立新的資源群組）。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。

    5.  針對*複寫*選取**讀取-存取-異地備援儲存體 (RA-GRS)**。

    6.  針對*效能*，選取**標準**。

    7.  離開*需要安全傳輸*作為**停用**。

    8.  選取 *訂用帳戶*。

    9. 選擇*資源群組*或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。 

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 您也必須確認您已了解這些條款和條件套用到此服務。

    11. 選取 [建立]。

        ![輸入的服務資訊](images/AzureLabs-Lab5-03.png)

5.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

6.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![在 azure 入口網站中的新通知](images/AzureLabs-Lab5-04.png)

7.  按一下通知，以探索新的服務執行個體。

    ![前往資源](images/AzureLabs-Lab5-05.png)

8.  按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 您將會被重新導向至新*儲存體帳戶*服務執行個體。

    ![存取金鑰](images/AzureLabs-Lab5-06.png)

9.  按一下 *存取金鑰*，以顯示此雲端服務的端點。 使用 *記事本*或類似檔案，以供稍後使用其中一個金鑰複本。 另請注意*連接字串*值，因為您將會用於*所需的 AzureServices*類別，您將在稍後建立。

    ![複製連接字串](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>第 2 章-設定 Azure 函式

現在您將撰寫**Azure** **函式**的 Azure 服務。

您可以使用**Azure Function**執行幾乎任何項目，也就與傳統的函式在程式碼中，差異在於，此函式可以存取任何應用程式具有存取您的 Azure 帳戶的認證。

若要建立 Azure 函式：

1.  從您*Azure 入口網站*，按一下**新增**在左上角，，並搜尋*函式應用程式*，然後按一下**Enter**。

    ![建立函數應用程式](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > 單字**的新**可能已取代為**建立資源**，較新的入口網站中。

2.  新的頁面將提供的描述*Azure 函數應用程式*服務。 在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。

    ![函式應用程式資訊](images/AzureLabs-Lab5-09.png)

3.  一旦您按下**建立**:

    1.  提供*應用程式名稱*。 字母和數字此處只能使用 （允許上限或下限的大小寫）。

    2.  選取您偏好*訂用帳戶*。

    3. 選擇*資源群組*或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。 

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  針對此練習中，選取*Windows*為所選**OS**。

    5.  選取 *耗用量計劃*for**主控方案**。

    6.  判斷*位置*資源群組 （如果您要建立新的資源群組）。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。 為了達到最佳效能，選取 儲存體帳戶相同的區域。

    7.  針對*儲存體*，選取**使用現有**，然後使用下拉式功能表中，尋找您先前建立的儲存體。

    8.  離開*Application Insights*關閉這項練習。

        ![輸入函式應用程式詳細資料](images/AzureLabs-Lab5-10.png)

4.  按一下 [建立] 按鈕。

5.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

6.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![新的 azure 入口網站通知](images/AzureLabs-Lab5-11.png)

7.  按一下通知，以探索新的服務執行個體。 

    ![移至資源函式應用程式](images/AzureLabs-Lab5-12.png)

8.  按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 您將會被重新導向至新*函式應用程式*服務執行個體。

9.  在上*函式應用程式*儀表板，將滑鼠移*函式*，在左側面板中找到，然後按一下 **+ （加號）** 符號。

    ![建立新的函式](images/AzureLabs-Lab5-13.png)

10. 在下一步 頁面上，確定**Webhook + API**已選取，至於*選擇的語言，* 選取**CSharp**，因為這是本教學課程中所使用的語言。 最後，按一下**建立此函式** 按鈕。

    ![選取 web hook csharp](images/AzureLabs-Lab5-14.png)

11. 您應該會進入程式碼頁面 (run.csx)，如果沒有，按一下左側面板中的 [函數] 清單中新建立的函式。

    ![開啟新的函式](images/AzureLabs-Lab5-15.png)

12. 將下列程式碼複製到您的函式中。 此函式只會傳回隨機整數，介於 0 和 2 時呼叫。 請勿擔心現有的程式碼，歡迎您貼上至頂端。

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. 選取 \[儲存\]。

14. 結果看起來應該像下列映像。

15. 按一下 **取得函式 URL**並記*端點*顯示。 您必須將它插入*所需的 AzureServices*稍後在本課程中，您將建立的類別。

    ![取得函式端點](images/AzureLabs-Lab5-16.png)

    ![取得函式端點](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>第 3 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

設定並測試您的混合的實境沈浸式耳機。

> [!NOTE]
> 您將會**不**本課程所需動作的控制器。 如果您需要支援沈浸式耳機的設定，請[瀏覽設定發行項的混合的實境](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  開啟 Unity，然後按一下**新增**。

    ![建立新的 unity 專案](images/AzureLabs-Lab5-17.png)

2.  您現在必須提供 Unity 專案名稱。 插入**MR_Azure_Functions**。 請確定專案類型設定為**3D**。 設定*位置*適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![指定新的 unity 專案的名稱](images/AzureLabs-Lab5-18.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯* > *喜好設定** 從新的視窗中，然後瀏覽至**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![設定 visual studio，為指令碼編輯器](images/AzureLabs-Lab5-19.png)

4.  接下來，移至**檔案 > 組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。

    ![切換至 uwp 的平台](images/AzureLabs-Lab5-20.png)

5.  移至**檔案 > 組建設定**並確定：

    1. **裝置為目標**設定為**任何裝置**。

        > 對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。

    2. **建置型別**設為**D3D**

    3. **SDK**設為**最新安裝**

    4. **Visual Studio 版本**設為**最新安裝**

    5. **建置並執行**設為**本機電腦**

    6. 儲存場景，並將它新增至組建。

        1.  做法是選取**加入開啟的場景**。 儲存視窗會出現。

            ![將開啟的場景新增](images/AzureLabs-Lab5-21.png)

        2.  建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![建立場景資料夾](images/AzureLabs-Lab5-22.png)

        3.  開啟您剛建立**場景**資料夾，然後在**檔案名稱：** 文字欄位中輸入**FunctionsScene**，然後按**儲存**。

            ![儲存函式場景](images/AzureLabs-Lab5-23.png)

6.  剩餘的設定，**組建設定**，應保持為預設值，現在。

    ![儲存函式場景](images/AzureLabs-Lab5-24.png)

7.  中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。

    ![偵測器中的播放程式設定](images/AzureLabs-Lab5-25.png)

8.  在此窗格中，少數設定需要驗證：

    1.  在 [**其他設定**] 索引標籤：

        1.  **指令碼執行階段版本**應該**實驗性**（.NET 4.6 對等），這會觸發程序需要重新啟動編輯器。
        2.  **指令碼後端**應該是 **.NET**
        3.  **API 相容性層級**應該是 **.NET 4.6**

    2.  內**發佈設定**索引標籤之下**功能**，檢查：
        
        -  **InternetClient**

            ![設定功能](images/AzureLabs-Lab5-26.png)

    3.  在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed RealitySDK**加入。

        ![設定 XR 設定](images/AzureLabs-Lab5-27.png)

9.  回到*Build Settings* *UnityC#專案*不再呈現灰色，這旁邊的核取方塊。

    ![刻度 c# 專案](images/AzureLabs-Lab5-28.png)

10.  關閉 [建立設定] 視窗。

11. 儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。

## <a name="chapter-4---setup-main-camera"></a>第 4 章-安裝主攝影機

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件的課程，並直接在程式碼中繼續進行，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)，然後匯入您的專案做為[自訂封裝](https://docs.unity3d.com/Manual/AssetPackages.html)。 這也會包含從下一章中的 Dll。 匯入之後，從繼續[第 7 章](#chapter-7---create-the-azureservices-class)。 

1.  在 *階層面板*，您會發現呼叫物件**Main Camera**，這個物件代表您的 「 主要 」 觀點來看，當您 「 內部 」 您的應用程式。

2.  您面前的 Unity 儀表板中，選取**主攝影機 GameObject**。 您將會發現*偵測器 面板*（通常是到右方時，儀表板中找到） 將會顯示各種元件的*GameObject*，使用*轉換*在頂端，後面接著*相機*，和一些其他元件。 您必須重設主攝影機的轉換，以便正確地定位。

3.  若要這樣做，請選取**齒輪**相機的旁邊的圖示*轉換*元件，然後選取**重設**。

    ![重設轉換](images/AzureLabs-Lab5-29.png)

4.  然後更新**轉換**元件如下：

    |         |    轉換-位置   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | 轉換的旋轉 |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | 轉換為小數位數 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![設定觀景窗轉換](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>第 5 章-設定 Unity 場景

1.  中的空白區域上按一下滑鼠右鍵*階層面板*下方**3D 物件**，加入**平面**。

    ![建立新的平面](images/AzureLabs-Lab5-31.png)

2.  具有**平面**物件選取、 變更中的下列參數*Inspector 面板*:

    |       | 轉換-位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | 轉換為小數位數 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![設定平面位置和比例](images/AzureLabs-Lab5-32.png)

    ![平面的場景檢視](images/AzureLabs-Lab5-33.png)

3.  中的空白區域上按一下滑鼠右鍵*階層面板*下方**3D 物件**，加入**Cube**。

    1.  重新命名 Cube **GazeButton** （與所選取的 Cube，請按 'F2'）。

    2.  變更中的下列參數*Inspector 面板*:

        |       | 轉換-位置 |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![設定視線按鈕轉換](images/AzureLabs-Lab5-34.png)

        ![視線按鈕場景檢視](images/AzureLabs-Lab5-35.png)

    3.  按一下 **標記**下拉式按鈕，然後按一下 **新增標記**以開啟*標記和圖層 窗格*。

        ![加入新的標記](images/AzureLabs-Lab5-36.png)

        ![選取加號](images/AzureLabs-Lab5-37.png)

    4.  選取 [ **+ （加號）** ] 按鈕，然後在*新的標記名稱*欄位中，輸入**GazeButton**，然後按**儲存**。

        ![名稱的新標記](images/AzureLabs-Lab5-38.png)

    5.  按一下 [ **GazeButton**物件中*階層面板*，然後在*偵測器] 面板*，指派新建立**GazeButton**標記。

        ![將新的標籤指定視線按鈕](images/AzureLabs-Lab5-39.png)

4.  以滑鼠右鍵按一下**GazeButton**物件，在*階層面板*，並新增**空 GameObject** (這將會新增為*子*物件）。

5.  選取新的物件，然後將它重新命名**ShapeSpawnPoint**。

    1.  變更中的下列參數*Inspector 面板*:

        |       | 轉換-位置 |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![更新圖案繁衍點轉換](images/AzureLabs-Lab5-40.png)

        ![圖形繁衍點場景檢視](images/AzureLabs-Lab5-41.png)

6.  接下來，您會建立**3D 文字**来提供意見反應對 Azure 服務之狀態物件。

    以滑鼠右鍵按一下**GazeButton**階層中面板 一次，並新增**3D 物件 > 3D 文字**物件做為*子*。

    ![建立新的 3D 文字物件](images/AzureLabs-Lab5-42.png)

7.  重新命名**3D 文字**物件**AzureStatusText**。

8.  變更**AzureStatusText**物件轉換，如下所示：

    |       | 轉換-位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | 轉換為小數位數 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > 請勿擔心，如果它似乎是關閉中心，因為這將會修正當下方文字 Mesh 更新元件。

9.  變更**文字 Mesh**來比對的元件如下：

    ![設定文字網狀結構元件](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > 選取的色彩是十六進位色彩：**000000FF**，但是請放心選擇自己，只要確定它是可讀取。

10. 您的階層面板結構現在看起來應該像這樣：

    ![mesh 場景檢視中的文字](images/AzureLabs-Lab5-43b.png)

10. 場景現在看起來應該像這樣：

    ![mesh 場景檢視中的文字](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>第 6 章-匯入 Unity 的 Azure 儲存體

您將針對 Unity 使用 Azure 儲存體 （而其本身會利用.Net SDK for Azure）。 您可以深入了解這在[Unity 文件的 Azure 儲存體](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。

這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。 這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。

若要 SDK 匯入您自己的專案，請確定您已下載最新[從 GitHub '.unitypackage](https://aka.ms/azstorage-unitysdk)。 然後，執行下列作業：

1.  新增 **.unitypackage** unity 所使用的檔案**資產 > 匯入封裝 > 自訂封裝**功能表選項。

2.  在 **匯入 Unity 封裝**方塊，顯示，您可以選取下方的所有內容 **外掛程式*> * 儲存 * *。 取消選取所有項目不需要這堂課程。

    ![匯入封裝](images/AzureLabs-Lab5-45.png)

3.  按一下 **匯入**按鈕以新增至您的專案項目。

4.  移至*儲存體*下方的資料夾*外掛程式*，接著在專案檢視 中，選取下列外掛程式*只*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![取消選取任何平台](images/AzureLabs-Lab5-46.png)

5.  具有*這些特定的外掛程式*選取，**取消核取***任何平台*並**取消核取** *WSAPlayer*然後按一下**套用**。

    ![適用於平台的 dll](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > 我們會將標示要僅適用於在 Unity 編輯器中的這些特定外掛程式。 這是因為有不同版本的專案會匯出從 Unity 後要使用 WSA 資料夾中的同一個外掛程式。

6.  在 *儲存體*外掛程式資料夾中，只選取：

    -   Microsoft.Data.Services.Client

        ![dll 不會處理集合](images/AzureLabs-Lab5-48.png)

7.  請檢查**不處理程序**下方*平台設定*，按一下 **套用**。

    ![適用於任何處理](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > 我們會將標示此外掛程式 」 不會處理 」 的 Unity 組件修補程式發生無法處理此外掛程式。 即使它不會處理此外掛程式仍然可以運作。

## <a name="chapter-7---create-the-azureservices-class"></a>第 7-建立所需的 AzureServices 類別

您即將建立的第一個類別是*所需的 AzureServices*類別。

*所需的 AzureServices*類別會負責：

-   儲存 Azure 帳戶認證。

-   呼叫您的 Azure 應用程式函式。

-   上傳和下載資料檔案，您的 Azure 雲端儲存體中。

若要建立此類別：

1.  以滑鼠右鍵按一下*Asset*資料夾，位於 [專案] 面板**建立 > 資料夾**。 將資料夾命名**指令碼**。

    ![建立新資料夾](images/AzureLabs-Lab5-50.png)

    ![呼叫資料夾-指令碼](images/AzureLabs-Lab5-51.png)

2.  按兩下剛才建立開啟的資料夾。

3.  在資料夾中，以滑鼠右鍵按一下**建立 >C#指令碼**。 呼叫指令碼*所需的 AzureServices*。

4.  按兩下新*所需的 AzureServices*類別，以開啟它*Visual Studio*。

5.  將下列命名空間加入至頂端*所需的 AzureServices*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  加入下列 Inspector 欄位內*所需的 AzureServices*類別：

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  然後新增下列成員變數內*所需的 AzureServices*類別：

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > 請確定您取代*端點*並*連接字串*在 Azure 入口網站中找到的值與您的 Azure 儲存體、 值

8.  程式碼*Awake()* 並*start （)* 方法現在需要加入。 在類別初始化時，就會呼叫這些方法：

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > 我們將會填入的程式碼*CallAzureFunctionForNextShape()* 中[未來一章](#chapter-10---completing-the-AzureServices-class)。

9.  刪除*update （)* 方法，因為這個類別不會使用它。

10. 在 Visual Studio 中，儲存您的變更，然後返回 Unity。

11. 按一下並拖曳*所需的 AzureServices*指令碼 資料夾中的 Main Camera 物件的類別*階層面板*。

12. 選取 Main Camera，接著要抓取**AzureStatusText**從下方的子物件**GazeButton**物件，並放在**AzureStatusText**參考目標欄位中，以*Inspector*，以提供參考*所需的 AzureServices*指令碼。

    ![指派 azure 狀態文字參考目標](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>第 8-建立 ShapeFactory 類別

若要建立下, 一步 的指令碼*ShapeFactory*類別。 此類別的角色是要求時，建立新的圖形，並保留歷程記錄中建立的圖案*圖形歷程記錄清單*。 每次建立圖形時，*圖形歷程記錄清單*中更新*AzureService*類別，並且會儲存您*Azure 儲存體*。 應用程式啟動時，如果儲存的檔案位於您*Azure 儲存體*，則*圖形的歷程記錄清單*擷取和重新執行，使用**3D 文字**物件，提供產生的圖形是否從儲存體，或新的。

若要建立此類別：

1.  移至**指令碼**您先前建立的資料夾。

2.  在資料夾中，以滑鼠右鍵按一下**建立 >C#指令碼**。 呼叫指令碼*ShapeFactory*。

3.  按兩下新*ShapeFactory*指令碼，以開啟它*Visual Studio*。

4.  請確定*ShapeFactory*類別包含下列命名空間：

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  新增至如下所示的變數*ShapeFactory*類別，並取代*start （)* 並*Awake()* 與下列函式：

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  *CreateShape()* 方法會產生基本的圖形，根據所提供*整數*參數。 布林值參數是用來指定目前建立的圖形是從儲存體，或是新。 將下列程式碼，在您*ShapeFactory*類別，先前的方法如下：

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  請務必在 Visual Studio 中儲存您的變更，然後再回到 Unity。

8.  傳回在 Unity 編輯器中，按一下並拖曳*ShapeFactory*從類別**指令碼**資料夾**Main Camera**物件*階層面板*.

9. 您會發現與選取的 Main Camera *ShapeFactory*遺漏指令碼元件*繁衍點*參考。 若要修正此問題，拖曳**ShapeSpawnPoint**物件*階層面板*來**繁衍點**參考目標。

    ![集合圖形 factory 參考目標](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>第 9-建立視線類別

您需要建立的最後一個指令碼*視線*類別。

這個類別會負責建立**Raycast** ，從主攝影機，來偵測使用者查看哪些物件會向前投影。 在此情況下，進而識別是否有使用者查看需要 Raycast **GazeButton**場景中物件，並會觸發的行為。

若要建立此類別：

1.  移至**指令碼**您先前建立的資料夾。

2.  在 [專案] 面板中，以滑鼠右鍵按一下**建立 >C#指令碼**。 呼叫指令碼*視線*。

3.  按兩下新*視線*指令碼，以開啟它*Visual Studio。*

4.  請確定下列命名空間包含在指令碼的頂端：

    ```csharp
        using UnityEngine;
    ```

5.  然後新增下列變數內*視線*類別：

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> 這些變數的一些能夠在中編輯*編輯器*。

6.  程式碼*Awake()* 並*start （)* 方法現在需要加入。

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  新增下列程式碼會建立一個資料指標物件開頭的情況下，連同*update （)* 方法，將會執行 Raycast 方法，以及切換 GazeEnabled 布林值的位置：

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. 接下來新增*UpdateRaycast()* 方法，它將專案 Raycast 並偵測叫用的目標。

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. 最後，新增*ResetFocusedObject()* 方法，它會切換 GazeButton 物件目前的色彩，表示它要建立新的形狀與否。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  在 Visual Studio 中儲存的變更，然後再回到 Unity。

11.  按一下並拖曳*視線*類別的指令碼資料夾**Main Camera**物件*階層面板*。

## <a name="chapter-10---completing-the-azureservices-class"></a>第 10 章-完成所需的 AzureServices 類別

與其他指令碼中的地方，它現在便能夠*完整**所需的 AzureServices*類別。 這會透過來達成：

1.  新增名為的新方法*CreateCloudIdentityAsync()*，若要設定驗證所需的變數來與 Azure 進行通訊。

    > 這個方法也會檢查先前儲存的檔案，包含 [圖形] 清單中存在。
    >
    > **如果找到的檔案**，它會停用使用者*視線*，和形狀建立圖形，根據觸發程序，因為儲存在**Azure 儲存體檔案**。 使用者可以確認這一點，作為**文字 Mesh**會提供顯示 'Storage' 或 'New'，根據圖形原點。
    >
    > **如果不找到任何檔案**，它會讓*視線*，讓使用者能夠查看時，建立圖形**GazeButton**場景中的物件。

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  下一步 的程式碼片段是從*start （)* 方法，其中的呼叫將會對*CreateCloudIdentityAsync()* 方法。 歡迎您目前透過複製*start （)* 方法，與下面：

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  方法的程式碼中填滿*CallAzureFunctionForNextShape()*。 您將使用先前建立*Azure 函數應用程式*要求形狀索引。 一旦收到新的形狀時，這個方法會將傳送圖形，以*ShapeFactory*場景中建立新的形狀的類別。 若要完成本文中使用下列程式碼*CallAzureFunctionForNextShape()*。

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  新增方法以建立字串，串連的整數儲存圖形的歷程記錄清單，並將它儲存在您*Azure 儲存體檔案*。

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  新增方法以擷取儲存在檔案位於您*Azure 儲存體檔案*並*還原序列化*到清單。

6.  完成此程序之後，此方法會重新啟用視線，讓使用者可以將多個圖形新增至場景。

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  在 Visual Studio 中儲存的變更，然後再回到 Unity。

## <a name="chapter-11---build-the-uwp-solution"></a>第 11 章-建置 UWP 方案

若要開始建置程序：

1.  移至**檔案 > 組建設定**。

    ![建置應用程式](images/AzureLabs-Lab5-54.png)

2.  按一下 [建置] 。 將會啟動 unity*檔案總管*視窗中，您要建立，然後選取 建置到應用程式的資料夾。 現在，建立該資料夾並將它命名*應用程式*。 然後使用*應用程式*資料夾選取，請按下**選取資料夾**。

3.  Unity 會開始建置您的專案*應用程式*資料夾。

4.  一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟*檔案總管*視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。

## <a name="chapter-12---deploying-your-application"></a>第 12 章-部署應用程式

若要部署您的應用程式：

1.  瀏覽至*應用程式*中所建立的資料夾[最後一章](#chapter-11---build-the-uwp-solution)。 您會看到您的應用程式名稱，與 '.sln' 擴充功能，您應該連按兩下檔案，因此以內開啟它*Visual Studio*。

2.  在 **的方案平台**，選取**x86，本機電腦**。

3.  在 **方案組態**選取**偵錯**。

    > 針對 Microsoft HoloLens，您可能會發現它更輕鬆地將此設為*遠端機器*，如此一來，您不行動網卡到您的電腦。 不過，您必須也執行下列作業：
    > - 了解**IP 位址**的您 HoloLens，位於*設定 > 網路和網際網路 > Wi-fi > 進階選項*; IPv4 是您應該使用的位址。 
    > - 請確定**開發人員模式**是**上**; 在找到*設定 > 更新與安全性 > 適用於開發人員*。

    ![部署解決方案](images/AzureLabs-Lab5-55.png)

4.  移至**建置**功能表，然後按一下 **部署方案**側載應用程式到您的電腦。

5.  您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動並測試 ！

## <a name="your-finished-azure-functions-and-storage-application"></a>您已完成 Azure Functions 和儲存體應用程式

恭喜，您所建立的混合的實境應用程式，運用 Azure Functions 和 Azure 儲存體服務。 您的應用程式將能夠依據儲存的資料，並提供該資料為基礎的動作。

![最終產品-結束](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

建立第二個繁衍，點和記錄點已建立物件，從繁衍 （spawn）。 當您載入資料檔案時，重新執行正在繁衍從原先建立的位置的圖形。

### <a name="exercise-2"></a>練習 2

建立應用程式，而不必重新開啟它每次重新啟動的方式。 **正在載入場景**是很好的位置，以啟動。 之後，若要清除的預存的清單中的方式來建立*Azure 儲存體*，如此一來，它可以輕鬆地重設您的應用程式。 
