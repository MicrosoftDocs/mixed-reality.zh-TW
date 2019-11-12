---
title: MR 和 Azure 309-Application insights
description: 完成此課程，以瞭解如何使用 Azure 應用程式 Insights 服務，收集有關混合現實應用程式中使用者行為的分析。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合現實，學術，unity，教學課程，api，application insights，hololens，沉浸，vr
ms.openlocfilehash: 481fe3fc16ada06085a64c86867a1a892c76f2ad
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926893"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時，使用這些教學課程的連結進行更新。

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR 和 Azure 309： Application insights

![最終產品-開始](images/AzureLabs-Lab309-00.png)

在此課程中，您將瞭解如何使用 Azure 應用程式 Insights API 來收集有關使用者行為的分析，將 Application Insights 功能新增到混合的現實應用程式中。

Application Insights 是一種 Microsoft 服務，可讓開發人員從其應用程式收集分析，並從便於使用的入口網站進行管理。 分析可以從效能到您想要收集的自訂資訊。 如需詳細資訊，請造訪[Application Insights 頁面](https://azure.microsoft.com/services/application-insights/)。

完成此課程之後，您將擁有一個混合現實的沉浸式耳機應用程式，其將能夠執行下列動作：

1.  允許使用者在場景周圍進行注視和移動。
2.  藉由使用場景中的物件，觸發將分析傳送至*Application Insights 服務*的程式。
3.  應用程式也會在服務上呼叫，並在過去24小時內，提取使用者最常完成哪些物件的相關資訊。 該物件會將其色彩變更為綠色。

本課程將告訴您如何將來自 Application Insights 服務的結果，帶入以 Unity 為基礎的範例應用程式。 您必須將這些概念套用到您可能正在建立的自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 309： Application insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然此課程主要著重于 Windows Mixed Reality 沉浸式（VR）耳機，但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。 隨著課程的遵循，您會看到您可能需要用來支援 HoloLens 的任何變更的附注。 使用 HoloLens 時，您可能會在語音捕獲期間發現一些回應。

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。 也請注意，本檔中的必要條件和書面指示，代表在撰寫本文時已測試和驗證的內容（2018年7月）。 您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體，但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容，而不是如下所示。

在此課程中，我們建議您採用下列硬體和軟體：

- [與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦，可用於沉浸式（VR）耳機開發
- [已啟用開發人員模式的 Windows 10 秋季建立者更新（或更新版本）](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 已啟用開發人員模式的[Windows Mixed Reality 沉浸（VR）耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 一組具有內建麥克風的耳機（如果耳機沒有內建的 mic 和喇叭）
- 適用于 Azure 設定和 Application Insights 資料抓取的網際網路存取

## <a name="before-you-start"></a>開始之前

為避免在建立此專案時發生問題，強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案（長資料夾路徑可能會在組建階段造成問題）。

> [!WARNING] 
> 請注意，進入*Application Insights*的資料需要一些時間，因此請耐心等候。 如果您想要檢查服務是否已收到您的資料，請查看第[14 章](#chapter-14---the-application-insights-service-portal)，這會示範如何流覽入口網站。

## <a name="chapter-1---the-azure-portal"></a>第1章-Azure 入口網站

若要使用*Application Insights*，您將需要在 Azure 入口網站中建立和設定*Application Insights 服務*。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程，請洽詢您的講師或其中一個 proctors，以協助設定您的新帳戶。

2.  登入之後，按一下左上角的 [**新增**]，並搜尋*Application Insights*，然後按一下**Enter 鍵**。

    > [!NOTE]
    > 在較新的入口網站中，**新**的「可能」已取代為「**建立資源**」。

    ![Azure 入口網站](images/AzureLabs-Lab309-01.png)

3.  右側的新頁面將會提供*Azure 應用程式 Insights*服務的描述。 在此頁面的左下方，選取 [**建立**] 按鈕，以建立與此服務的關聯。

    ![Azure 入口網站](images/AzureLabs-Lab309-02.png)

4.  當您按一下 [**建立**] 之後：

    1.  為此服務實例插入您想要的**名稱**。

    2.  選取 **[一般**] 作為 [**應用程式類型**]。

    3.  選取適當的**訂**用帳戶。

    4.  選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務（例如這些課程）都保留在通用資源群組下）。

        > 如果您想要深入瞭解 Azure 資源群組，請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5.  選取 [**位置**]。

    6.  您也必須確認您已瞭解適用于此服務的條款及條件。

    7.  選取 **\[建立\]** 。

        ![Azure 入口網站](images/AzureLabs-Lab309-03.png)

5.  按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。

6.  建立服務實例之後，入口網站中會出現通知。

    ![Azure 入口網站](images/AzureLabs-Lab309-04.png)

7.  按一下 [通知] 以探索新的服務實例。

    ![Azure 入口網站](images/AzureLabs-Lab309-05.png)

8.  按一下通知中的 [**移至資源**] 按鈕，探索新的服務實例。 您將會進入新的*Application Insights 服務*實例。

    ![Azure 入口網站](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  讓此網頁保持開啟且易於存取，您通常會回到這裡查看所收集的資料。

    > [!IMPORTANT]
    > 若要執行 Application Insights，您必須使用三個（3）個特定值：**檢測金鑰**、**應用程式識別碼**和**API 金鑰**。 您會在下面看到如何從您的服務取得這些值。 請務必在空白的 [*記事本*] 頁面上記下這些值，因為您很快就會在程式碼中使用它們。

9.  若要尋找**檢測金鑰**，您必須向下滾動服務函式清單，然後按一下 [**屬性**]，顯示的索引標籤會顯示**服務金鑰**。

    ![Azure 入口網站](images/AzureLabs-Lab309-07.png)

10. 以下是一些**屬性**，您會發現需要按一下的**API 存取權**。 右邊的面板會提供您應用程式的**應用程式識別碼**。

    ![Azure 入口網站](images/AzureLabs-Lab309-08.png)

11. 在 [**應用程式識別碼**] 面板仍然開啟的情況下，按一下 [**建立 api 金鑰**]，這會開啟 [*建立 api 金鑰*] 面板。

    ![Azure 入口網站](images/AzureLabs-Lab309-09.png)

12. 在現在開啟 [*建立 API 金鑰*] 面板中，輸入描述，然後**勾選三個方塊**。

13. 按一下 [**產生金鑰**]。 將會建立並顯示您的**API 金鑰**。 

    ![Azure 入口網站](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > 這是您的**服務金鑰**只會顯示的時間，因此請務必立即建立複本。

## <a name="chapter-2---set-up-the-unity-project"></a>第2章-設定 Unity 專案

以下是使用混合現實進行開發的一般設定，因此是適用于其他專案的絕佳範本。

1.  開啟*Unity* ，然後按一下 [**新增**]。

    ![設定 Unity 專案](images/AzureLabs-Lab309-11.png)

2.  您現在必須提供 Unity 專案名稱、將**MR\_Azure\_應用程式\_深入**解析。 請確定*範本*已設定為 [ **3d**]。 將位置設定為適合您的*位置*（請記住，接近根目錄較佳）。 然後，按一下 [**建立專案**]。

    ![設定 Unity 專案](images/AzureLabs-Lab309-12.png)

3.  在 Unity 開啟的情況下，值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 **編輯 \> 喜好**設定，然後在新視窗中，流覽至 **外部工具**。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

    ![設定 Unity 專案](images/AzureLabs-Lab309-13.png)

4.  接著，移至 [檔案] **\> [組建設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至**通用 Windows 平臺**。

    ![設定 Unity 專案](images/AzureLabs-Lab309-14.png)

5.  移至 [檔案] **\> [組建設定**]，並確認：

    1.  **目標裝置**已設定為**任何裝置**

        > 若為 Microsoft HoloLens，請將**目標裝置**設定為*HoloLens*。

    2.  **組建類型**設定為**D3D**

    3.  **SDK**已設定為**最新安裝**

    4.  **組建和執行**設定為**本機電腦**

    5.  儲存場景，並將它加入至組建。

        1.  選取 [新增] [**開啟場景**] 來執行此動作。 [儲存] 視窗隨即出現。

            ![設定 Unity 專案](images/AzureLabs-Lab309-15.png)

        2. 建立這個的新資料夾，以及任何未來的場景，然後按一下 [**新增資料夾**] 按鈕，建立新的資料夾，將它命名為**場景**。

            ![設定 Unity 專案](images/AzureLabs-Lab309-16.png)

        3. 開啟新建立的 [**幕後**] 資料夾，然後在 [*檔案名：* 文字] 欄位中，輸入**ApplicationInsightsScene**，然後按一下 [**儲存**]。

            ![設定 Unity 專案](images/AzureLabs-Lab309-17.png)

6.  [**組建設定**] 中的其餘設定，現在應該保留為預設值。

7.  在 [**組建設定**] 視窗中，按一下 [ **Player 設定**] 按鈕，這會在偵測**器**所在的空間中開啟相關的面板。

    ![設定 Unity 專案](images/AzureLabs-Lab309-18.png)

8. 在此面板中，需要驗證幾項設定：

    1.  在 [**其他設定**] 索引標籤中：

        1.  **腳本** **執行階段版本**應該是**實驗性（.net 4.6 對等用法）** ，這將會觸發重新開機編輯器的需求。

        2.  **腳本後端**應該是 **.net**

        3.  **API 相容性層級**應該是 **.net 4.6**

        ![設定 Unity 專案](images/AzureLabs-Lab309-19.png)

    2.  在 [**發行設定**] 索引標籤的 [**功能**] 底下，檢查：

        - **InternetClient**     

            ![設定 Unity 專案](images/AzureLabs-Lab309-20.png)

    3.  在面板中，于 [ **XR 設定**] （在 [**發佈設定**] 下找到）中，支援 [勾選**虛擬實境**]，並確定已新增 [ **Windows Mixed Reality SDK** ]。

        ![設定 Unity 專案](images/AzureLabs-Lab309-21.png)

9.  回到 [**組建設定**] **， C# Unity 專案**不再呈現灰色;勾選 [] 旁的核取方塊。

10.  關閉 [組建設定] 視窗。

11.  儲存場景和專案（**file** > **儲存場景/** 檔案 > **儲存專案**）。


## <a name="chapter-3---import-the-unity-package"></a>第3章-匯入 Unity 封裝

> [!IMPORTANT]
> 如果您想要略過*Unity 設定*本課程的元件，並繼續直接進入程式碼，您可以免費下載此[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)，將它匯入您的專案中做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)。 這也會包含下一章中的 Dll。 匯入之後，請從[**第6章**](#chapter-6---create-the-applicationinsightstracker-class)繼續進行。

> [!IMPORTANT]
> 若要在 Unity 中使用 Application Insights，您需要匯入它的 DLL，以及 Newtonsoft DLL。 Unity 中目前有一個已知問題，需要在匯入後重新設定外掛程式。 解決錯誤之後，將不再需要這些步驟（本節中的 4-7）。

若要將 Application Insights 匯入至您自己的專案，請確定您已[下載包含外掛程式的 ' unitypackage '](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)。 然後，執行下列動作：

1.  使用 資產 \> 匯**入封裝 \> 自訂封裝** 功能表選項，將**Unitypackage**新增至 Unity。

2.  在快顯的 [匯**入 Unity 封裝**] 方塊中，確定已選取（和包含）**外掛程式**底下的所有專案。

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-22.png)

3.  按一下 [匯**入**] 按鈕，將專案新增至您的專案。

4.  移至 [專案] 視圖中 [**外掛程式**] 底下的 [ **Insights** ] 資料夾，然後選取 [*僅*下列外掛程式]：

    -   ApplicationInsights

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-23.png)

5.  選取此*外掛程式*之後，請確認已**取消**核取**任何平臺**，然後確定**WSAPlayer**也**未**核取，**然後按一下 [** 套用]。 這麼做只是為了確認檔案已正確設定。

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > 標記這類外掛程式時，會將它們設定為僅在 Unity 編輯器中使用。 在 [WSA] 資料夾中有一組不同的 Dll，將在從 Unity 匯出專案之後使用。

6.  接下來，您必須在 [ **Insights** ] 資料夾內開啟 [ **WSA** ] 資料夾。 您會看到您剛才設定的相同檔案的複本。 選取此檔案，然後在偵測器中，確定已**取消**選取**任何平臺**，然後確定**只**會**核**取 [ **WSAPlayer** ]。 按一下 **\[Apply\]** (套用)。

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-25.png)

7. 您現在必須遵循**步驟 4-6**，而不是*Newtonsoft*外掛程式。 請參閱下列螢幕擷取畫面，以瞭解結果看起來的樣子。

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>第4章-設定相機和使用者控制項

在本章中，您將設定相機和控制項，以允許使用者在場景中查看及移動。

1.  以滑鼠右鍵按一下 [階層] 面板中的空白區域，然後在 [**建立** > **空白**]。

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-26.png)

2.  將新的空白 GameObject 重新命名為**攝影機父系**。

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-27.png)

3.  以滑鼠右鍵按一下 [階層] 面板中的空白區域，然後在 [ **3D 物件**] 和 [**球體**] 上。

4.  將球體重新命名為**右手**邊。

5.  將右手邊的**轉換縮放比例**設定為**0.1、0.1、0.1**

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-28.png)

6.  按一下 [*球體碰撞*器] 元件中的**齒輪**，然後**移除 [元件**]，以移除右側的**球體碰撞**器元件。

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-29.png)

7.  在 [階層] 面板中，將**主相機**和**右手**邊物件拖曳至**相機父**物件。

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-30.png)

8.  將**主要相機**和**右手**邊物件的**轉換位置**設定為**0，0，0**。

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-31.png)

    ![設定相機和使用者控制項](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>第5章-在 Unity 場景中設定物件

您現在會為場景建立一些基本圖案，讓使用者可以進行互動。

1.  以滑鼠右鍵按一下 [階層]*面板*中的空白區域，然後在 [ **3d 物件**] 上，選取 [**平面**]。

2.  將平面**轉換位置**設定為**0，-1，0**。

3.  將平面**轉換比例**設定為**5、1、5**。

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-33.png)

4.  建立要與您的**平面**物件搭配使用的基本材質，讓其他圖形更容易看到。 流覽至您的 [*專案] 面板*，以滑鼠右鍵按一下 [**建立**]，接著按 [**資料夾**]，以建立新的資料夾。 為 it**教材**命名。

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-34.png) ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-35.png)

5.  開啟 [**材質**] 資料夾，然後以滑鼠右鍵按一下 [**建立**]，然後按一下 [**材質**] 來建立新的資料。 將它命名為**藍色**。

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-36.png) ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-37.png)

6.  選取新的**藍色**材質後，查看 [*檢查*]，然後按一下 [ **Albedo**] 矩形視窗。 選取藍色色彩（下一張圖片是**十六進位色彩： \#3592FFFF**）。 選擇之後，請按一下 [關閉] 按鈕。

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-38.png)

7.  將您的新材質從 [**材質**] 資料夾拖曳到您在新建立的**平面**上，放在您的場景內（或將它放置在階層內的**平面**物件*上）。*

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-39.png)

8.  以滑鼠右鍵按一下 [階層]*面板*中的空白區域，然後在 [ **3d 物件]、[膠囊**] 上。

    -  選取 [**膠囊**] 時，將其**轉換***位置*變更為： **-10，1，0**。

9.  以滑鼠右鍵按一下 [階層]*面板*中的空白區域，然後在 [ **3d 物件]、[Cube**] 上。

    -  選取**Cube**後，將其**轉換***位置*變更為： **0，0，10**。

10. 以滑鼠右鍵按一下 [階層]*面板*中的空白區域，然後在 [ **3d 物件]、[球體**] 上。

    -  選取**球體**後，將其**轉換***位置*變更為： **10，0，0**。

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > 這些*位置*值是*建議*。 您可以自由地將物件的位置設定為任何您想要的，不過，如果物件距離與相機不太遠，應用程式的使用者就會更容易。

11. 當您的應用程式正在執行時，它必須能夠識別場景內的物件，以達到此目的，必須加上標籤。 選取其中一個物件，然後在 偵測*器* 面板中按一下 **新增標記 ...** ，這會將偵測*器*與 標籤 **& 圖層** 面板交換。

    ![在 Unity 場景](images/AzureLabs-Lab309-41.png) 中設定物件 ![](images/AzureLabs-Lab309-42.png)

12. 按一下 [ **+] （加號）** 符號，然後將標記名稱輸入為**ObjectInScene**。

    ![在 Unity 場景中設定物件](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > 如果您的標籤使用不同的名稱，您必須確保這種變更也會變成*DataFromAnalytics*、 *ObjectTrigger*和*注視*、腳本之後，以便在場景中找到並偵測您的物件。

13. 建立標記之後，您現在必須將它套用到您的所有三個物件。 *在階層中，按住* **Shift**鍵，然後依序按一下 [**膠囊**]、[ **Cube**] 和 [**球體**]、[物件]，然後在 [偵測*器*] 中，按一下下拉式功能表加上**標記**，然後按一下您建立的*ObjectInScene*標記。

    ![在 Unity 場景](images/AzureLabs-Lab309-44.png) 中設定物件 ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>第6章-建立 ApplicationInsightsTracker 類別

您需要建立的第一個腳本是**ApplicationInsightsTracker**，它會負責：

1.  根據使用者互動建立事件以提交給 Azure 應用程式 Insights。

2. 根據使用者互動，建立適當的事件名稱。

3. 將事件提交至 Application Insights 服務實例。

若要建立此類別：

1.  在 *專案 面板*中按一下滑鼠右鍵，然後**建立** > **資料夾**。 將資料夾命名為**Scripts**。

    ![建立 ApplicationInsightsTracker 類別](images/AzureLabs-Lab309-46.png)  ![建立 ApplicationInsightsTracker 類別](images/AzureLabs-Lab309-47.png)

2.  在建立**script 資料夾之後**，按兩下以開啟。 然後，在該資料夾中，以滑鼠右鍵按一下 [**建立** >  **C#腳本**]。 將腳本命名為**ApplicationInsightsTracker**。

3.  按兩下新的**ApplicationInsightsTracker**腳本，以**Visual Studio**開啟它。

4.  更新腳本頂端的命名空間，如下所示：

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  在類別內插入下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > 使用 Azure 入口網站中的*服務金鑰*（如步驟9的「開始」一[章](#chapter-1---the-azure-portal)所述），適當地設定**instrumentationKey、applicationId 和 API_Key**值。

6.  然後，新增**開始（）** 和**喚醒（）** 方法，這會在類別初始化時呼叫：

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  新增負責傳送應用程式所註冊的事件和計量的方法：

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。

## <a name="chapter-7---create-the-gaze-script"></a>第7章-建立注視腳本

下一個要建立的腳本是**注視**腳本。 此腳本會負責建立將從*主要相機*向前投射的*Raycast* ，以偵測使用者正在查看的物件。 在此情況下， *Raycast*將需要識別使用者是否查看具有**ObjectInScene**標記的物件，然後計算使用者在該物件上*gazes*的時間長度。

1.  按兩下 [**腳本**] 資料夾以開啟它。

2.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立** >  **C#腳本**]。 將腳本命名為**注視**。

3.  按兩下腳本，以 Visual Studio 開啟它。

4.  將現有的程式碼取代為下列內容：

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  現在必須加入**喚醒（）** 和**Start （）** 方法的程式碼。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  在**注視**類別內部，于**Update （）** 方法中新增下列程式碼，以投影*Raycast*並偵測目標叫用：

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  加入**ResetFocusedObject （）** 方法，以在使用者查看物件時，將資料傳送至**Application Insights** 。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  您現在已完成**注視**腳本。 請先儲存*Visual Studio*中的變更，再返回*Unity*。

## <a name="chapter-8---create-the-objecttrigger-class"></a>第8章-建立 ObjectTrigger 類別

您需要建立的下一個腳本是**ObjectTrigger**，它會負責：

- 將衝突所需的元件新增至主要攝影機。
- 偵測相機是否接近標記為**ObjectInScene**的物件。

若要建立腳本：

1.  按兩下 [**腳本**] 資料夾以開啟它。

2.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立** >  **C#腳本**]。 將腳本命名為**ObjectTrigger**。

3.  按兩下腳本，以 Visual Studio 開啟它。 將現有的程式碼取代為下列內容：

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。

## <a name="chapter-9---create-the-datafromanalytics-class"></a>第9章-建立 DataFromAnalytics 類別

現在您將需要建立**DataFromAnalytics**腳本，其負責：

- 正在提取有關相機已接近哪個物件的分析資料。
- 使用*服務金鑰*，以允許與您的 Azure 應用程式 Insights 服務實例進行通訊。
- 根據具有最高事件計數的場景排序物件。
- 將最接近物件的材質色彩變更為*綠色*。

若要建立腳本：

1.  按兩下 [**腳本**] 資料夾以開啟它。

2.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立** >  **C#腳本**]。 將腳本命名為**DataFromAnalytics**。

3.  按兩下腳本，以 Visual Studio 開啟它。

4.  插入下列命名空間：

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  在腳本中，插入下列內容：

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  在**DataFromAnalytics**類別內的**Start （）** 方法後面，新增下列名為**FetchAnalytics （）** 的方法。 這個方法會負責填入機碼值組的清單，以及一個*GameObject*和一個預留位置事件計數編號。 然後，它會初始化**GetWebRequest （）** 協同程式。 您也可以在這個方法中找到*Application Insights*呼叫的查詢結構，做為*查詢 URL*端點。

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  在**FetchAnalytics （）** 方法的右下方，新增名為**GetWebRequest （）** 的方法，它會傳回*IEnumerator*。 這個方法會負責要求在*Application Insights*內呼叫事件（對應于特定*GameObject*）的次數。 當所有傳送的查詢都傳回時，會呼叫**DetermineWinner （）** 方法。

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  下一個方法是**DetermineWinner （）** ，它會根據最高的事件計數來排序*GameObject*和*Int*配對的清單。 然後，它會將該*GameObject*的材質色彩變更為*綠色*（以最高計數的意見反應表示）。 這會顯示含有分析結果的訊息。

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  新增類別結構，其將用來還原序列化從*Application Insights*接收的 JSON 物件。 在**DataFromAnalytics**類別檔案的最下方，于類別定義**之外**新增這些類別。

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. 請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。

## <a name="chapter-10---create-the-movement-class"></a>第10章-建立移動類別

**移動**腳本是您將需要建立的下一個腳本。 它負責：

- 根據相機正在尋找的方向移動主要攝影機。
- 將所有其他腳本新增至場景物件。

若要建立腳本：

1.  按兩下 [**腳本**] 資料夾以開啟它。

2.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵，然後按一下 [**建立** >  **C#腳本**]。 為腳本的**移動**命名。

3.  按兩下腳本，以*Visual Studio*開啟它。

4.  將現有的程式碼取代為下列內容：

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  在 move**類別內的空白** **Update （）** 方法*底下*，插入下列方法，讓使用者可以使用手形控制器來移動虛擬空間：

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  最後，在**Update （）** 方法內新增方法呼叫。

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  請務必先將您的變更儲存在*Visual Studio*中，然後再返回*Unity*。

## <a name="chapter-11---setting-up-the-scripts-references"></a>第11章-設定腳本參考

在本章中，您必須將**移動**腳本放在**相機父系**上，並設定其參考目標。 接著，該腳本會處理將其他腳本放在需要的位置。

1.  從 [*專案] 面板*的 [**腳本**] 資料夾中，將 [**移動**] 腳本拖曳至 [階層]*面板*中的 [**相機] 父**物件。

    ![在 Unity 場景中設定腳本參考](images/AzureLabs-Lab309-48.png)

2.  按一下 [**相機] 父系**。 在 [階層]*面板*中，**將右手**物件從 [階層]*面板*拖曳至 [偵測*器] 面板*中的參考目標**控制器**。 將 [**使用者速度**] 設定為 [ **5**]，如下圖所示。

    ![在 Unity 場景中設定腳本參考](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>第12章-建立 Unity 專案

此專案的 Unity 區段所需的全部內容現在已經完成，所以可以從 Unity 建立它。

1.  流覽**至 [** **組建設定**] （[檔案 > **組建設定**]）。

2.  從 [**組建設定**] 視窗中，按一下 [**建立**]。

    ![將 Unity 專案建立至 UWP 解決方案](images/AzureLabs-Lab309-50.png)

3.  [檔案**瀏覽器**] 視窗隨即出現，提示您輸入組建的位置。 建立新的資料夾（按一下左上角的 [**新增資料夾**]），並將其命名為**build**。

    ![將 Unity 專案建立至 UWP 解決方案](images/AzureLabs-Lab309-51.png)

    1.  開啟 [新增**組建**] 資料夾，然後建立另一個資料夾（使用**新資料夾**一次），並將其命名為**MR\_Azure\_應用程式\_深入**解析。

        ![將 Unity 專案建立至 UWP 解決方案](images/AzureLabs-Lab309-52.png)

    2.  在已選取 [ **MR\_Azure\_application\_Insights** ] 資料夾中，按一下 [**選取資料夾**]。 專案需要幾分鐘的時間才能建立。

4.  在下列*組建*中，會出現 [檔案**瀏覽器**]，顯示新專案的位置。

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a>第13章-將 MR_Azure_Application_Insights 應用程式部署到您的電腦

若要在您的本機電腦上部署**MR\_Azure\_application\_Insights**應用程式：

1.  在**Visual Studio**中，開啟**MR\_Azure\_application\_Insights**應用程式的解決方案檔案。

2.  在**解決方案平臺**中，選取 [ **x86]、[本機電腦**]。

3.  在 [**解決方案**設定] 中，選取 [ **Debug**]。

    ![將 Unity 專案建立至 UWP 解決方案](images/AzureLabs-Lab309-53.png)

4.  移至 [**建立] 功能表**，然後按一下 [**部署方案**]，將應用程式側載至您的電腦。

5.  您的應用程式現在應該會出現在已安裝的應用程式清單中，並準備好啟動。

6. 啟動混合現實應用程式。

7. 當*Azure 深入解析服務*收集到足夠的事件資料時，在場景前後移動，它會將已接近綠色的物件設為最多。

> [!IMPORTANT] 
> 雖然服務收集*事件和計量*的平均等候時間大約需要15分鐘，但在某些情況下，可能需要多達1小時。

## <a name="chapter-14---the-application-insights-service-portal"></a>第14章-Application Insights 服務入口網站

在您漫遊場景並 gazed 數個物件之後，您就可以看到*Application Insights 服務*入口網站中收集的資料。

1.  回到您的 Application Insights 服務入口網站。

2.  按一下 [*計量瀏覽器*]。

    ![查看收集的資料](images/AzureLabs-Lab309-54.png)

3.  它會在包含圖形的索引標籤中開啟，代表與您的應用程式相關的*事件和計量*。 如上所述，資料可能需要一段時間（最多1小時）才會顯示在圖形中

    ![查看收集的資料](images/AzureLabs-Lab309-55.png)

4.  按一下 [依應用程式版本的*事件總數*] 中的 [*事件*] 列，以查看事件的詳細細目及其名稱。

    ![查看收集的資料](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>您已完成 Application Insights 服務應用程式

恭喜，您建立了一個混合現實應用程式，利用 Application Insights 服務來監視應用程式中的使用者活動。

![課程結果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>額外練習

**練習1**

嘗試產生，而不是手動建立 ObjectInScene 物件，並在腳本內的平面上設定其座標。 如此一來，您可以向 Azure 詢問最受歡迎的物件是什麼（從注視或相近的結果），並產生一個*額外*的物件。

**練習2**

依時間排序您的 Application Insights 結果，讓您取得最相關的資料，並在您的應用程式中執行該時間的敏感性資料。

