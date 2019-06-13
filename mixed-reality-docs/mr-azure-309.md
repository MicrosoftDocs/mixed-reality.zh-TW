---
title: MR 和 Azure 309-Application insights
description: 完成此課程來了解如何收集有關使用者行為，在混合的實境應用程式中，使用 Azure Application Insights 服務的分析。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 application insights、 hololens、 沉浸式 vr
ms.openlocfilehash: 838dbe38724d29f4c5987e2f6ac7a07231015c82
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596994"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR 和 Azure 309:Application insights

![最終產品-開始](images/AzureLabs-Lab309-00.png)

在此課程中，您將了解如何將 Application Insights 功能新增至混合的實境應用程式，來收集有關使用者行為分析中使用 Azure Application Insights API。

Application Insights 是 Microsoft 服務，讓開發人員從其應用程式收集分析，並從方便使用入口網站進行管理。 分析可以是任何您想要收集的自訂資訊的效能。 如需詳細資訊，請瀏覽[Application Insights 頁面](https://azure.microsoft.com/services/application-insights/)。

完成本課程之後，您必須能夠執行下列作業的混合的實境耳機沈浸式應用程式：

1.  允許使用者視線和場景中四處移動。
2.  觸發程序的分析，以傳送*Application Insights 服務*、 透過視線和場景中物件的鄰近性使用。
3.  應用程式也會在服務中，擷取關於哪個物件已經過已由使用者最接近過去 24 小時內的資訊時呼叫。 該物件會將其色彩會變成綠色。

本課程將教導您如何從 Application Insights 服務中，取得結果，到 Unity 為基礎的範例應用程式。 它會決定要將這些概念套用到您可能建置自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 309:Application insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。 當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。 當使用 HoloLens，您可能會發現某些回應語音擷取期間。

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程專為具有基礎經驗的 Unity 開發人員和C#。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。 中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。

我們建議下列的硬體和軟體這堂課程：

- 開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發
- [Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式
- 一組的耳機與內建的麥克風 （如果耳機並沒有內建的麥克風和喇叭）
- 針對 Azure 設定和 Application Insights 資料擷取的網際網路存取

## <a name="before-you-start"></a>開始之前

若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。

> [!WARNING] 
> 請注意，資料流向*Application Insights*需要時間，因此請耐心等候。 如果您想要檢查如果此服務已收到您的資料，請參閱[第 14 章](#chapter-14---the-application-insights-service-portal)，這會告訴您如何瀏覽至入口網站。

## <a name="chapter-1---the-azure-portal"></a>第 1 章-Azure 入口網站

若要使用*Application Insights*，您必須建立及設定*Application Insights 服務*在 Azure 入口網站中。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**新增**在左上角，，然後搜尋*Application Insights*，然後按一下**Enter**。

    > [!NOTE]
    > 單字**的新**可能已取代為**建立資源**，較新的入口網站中。

    ![Azure 入口網站](images/AzureLabs-Lab309-01.png)

3.  向新的頁面將提供的描述*Azure Application Insights*服務。 在左下方的這個頁面上，選取**建立**按鈕，以建立與這個關聯服務。

    ![Azure 入口網站](images/AzureLabs-Lab309-02.png)

4.  一旦您按下**建立**:

    1.  插入您想要**名稱**此服務執行個體。

    2.  作為**應用程式類型**，選取**一般**。

    3.  選取適當**訂用帳戶**。

    4.  選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5.  選取 **位置**。

    6.  您也必須確認您已了解這些條款和條件套用到此服務。

    7.  選取 [建立]  。

        ![Azure 入口網站](images/AzureLabs-Lab309-03.png)

5.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

6.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![Azure 入口網站](images/AzureLabs-Lab309-04.png)

7.  按一下通知，以探索新的服務執行個體。

    ![Azure 入口網站](images/AzureLabs-Lab309-05.png)

8.  按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 您將會被重新導向至新*Application Insights 服務*執行個體。

    ![Azure 入口網站](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  保持開啟這個 web 網頁，並很容易地存取，您會返回此處通常若要查看所收集的資料。

    > [!IMPORTANT]
    > 若要實作 Application Insights，您必須使用三 （3） 特定值：**檢測金鑰**，**應用程式識別碼**，以及**API 金鑰**。 以下您將了解如何從您的服務中擷取這些值。 請務必記下這些值在空白*記事本*頁面上，因為您即將使用這些程式碼中。

9.  若要尋找**檢測金鑰**，您必須向下捲動服務功能的清單，然後按一下 **屬性**，顯示  索引標籤會顯示**服務金鑰**。

    ![Azure 入口網站](images/AzureLabs-Lab309-07.png)

10. 以下有點**屬性**，您會發現**API 存取**，您需要按一下。 右側面板會提供**應用程式識別碼**應用程式。

    ![Azure 入口網站](images/AzureLabs-Lab309-08.png)

11. 具有**應用程式識別碼**面板仍開啟時，按一下**建立 API 金鑰**，這會開啟*建立的 API 金鑰*面板。

    ![Azure 入口網站](images/AzureLabs-Lab309-09.png)

12. 現在開放內*建立的 API 金鑰* 面板中，輸入描述，以及**勾選三個方塊**。

13. 按一下 **產生金鑰**。 您**API 金鑰**會建立並顯示。 

    ![Azure 入口網站](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > 這是唯一的時候您**服務金鑰**隨即出現，因此請確定您現在建立一份。

## <a name="chapter-2---set-up-the-unity-project"></a>第 2 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟*Unity*然後按一下**新增**。

    ![設定 Unity 專案](images/AzureLabs-Lab309-11.png)

2.  您現在需要提供 Unity 專案名稱、 插入**MR\_Azure\_應用程式\_Insights**。 請確定*樣板*設為**3D**。 設定*位置*適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![設定 Unity 專案](images/AzureLabs-Lab309-12.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯\>喜好設定**，然後在新視窗中，瀏覽**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![設定 Unity 專案](images/AzureLabs-Lab309-13.png)

4.  接下來，移至**檔案\>組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。

    ![設定 Unity 專案](images/AzureLabs-Lab309-14.png)

5.  移至**檔案\>組建設定**並確定：

    1.  **裝置為目標**設為**任何裝置**

        > 對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。

    2.  **建置型別**設為**D3D**

    3.  **SDK**設為**最新安裝**

    4.  **建置並執行**設為**本機電腦**

    5.  儲存場景，並將它新增至組建。

        1.  做法是選取**加入開啟的場景**。 儲存視窗會出現。

            ![設定 Unity 專案](images/AzureLabs-Lab309-15.png)

        2. 為此範例和任何未來的場景，請建立新的資料夾，然後按一下 **新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![設定 Unity 專案](images/AzureLabs-Lab309-16.png)

        3. 開啟您剛建立**場景**資料夾，然後在*檔案名稱：* 文字欄位中輸入**ApplicationInsightsScene**，然後按一下 **儲存**.

            ![設定 Unity 專案](images/AzureLabs-Lab309-17.png)

6.  剩餘的設定，**組建設定**，應保持為預設值，現在。

7.  中**組建設定**視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。

    ![設定 Unity 專案](images/AzureLabs-Lab309-18.png)

8. 在此窗格中，少數設定需要驗證：

    1.  在 [**其他設定**] 索引標籤：

        1.  **指令碼** **執行階段版本**應該 **（.NET 4.6 對等） 的實驗性**，這會觸發程序需要重新啟動編輯器。

        2.  **指令碼後端**應該是 **.NET**

        3.  **API 相容性層級**應該是 **.NET 4.6**

        ![設定 Unity 專案](images/AzureLabs-Lab309-19.png)

    2.  內**發佈設定**索引標籤之下**功能**，檢查：

        - **InternetClient**     

            ![設定 Unity 專案](images/AzureLabs-Lab309-20.png)

    3.  在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed RealitySDK**加入。

        ![設定 Unity 專案](images/AzureLabs-Lab309-21.png)

9.  回到**Build Settings**， **Unity C\#專案**不再呈現灰色，這旁邊的核取方塊。

10.  關閉 [建立設定] 視窗。

11.  儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。


## <a name="chapter-3---import-the-unity-package"></a>第 3 章-匯入 Unity 封裝

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件，這些課程，並繼續直接進入程式碼，請自由下載此[Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)，它匯入到您的專案做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)。 這也會包含從下一章中的 Dll。 匯入之後，從繼續[**第 6 章**](#chapter-6---create-the-applicationinsightstracker-class)。

> [!IMPORTANT]
> 若要使用 Application Insights 在 Unity 內，您要匯入 DLL，以及 Newtonsoft DLL。 這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。 這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。

若要匯入到您自己專案的 Application Insights，請確定您已[下載 '.unitypackage'，其中包含外掛程式](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)。 然後，執行下列作業：

1.  新增 **.unitypackage**若要使用的 Unity**資產\>匯入封裝\>自訂封裝**功能表選項。

2.  在 **匯入 Unity 封裝**方塊會顯示。 請確認所有項目底下 （而且包括）**外掛程式**已選取。

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-22.png)

3.  按一下 **匯入**按鈕，將項目新增至您的專案。

4.  移至**Insights**下方的資料夾**外掛程式**專案中檢視，然後選取下列外掛程式*只*:

    -   Microsoft.ApplicationInsights

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-23.png)

5.  與這個*外掛程式*選取，請確認**任何平台**是**unchecked**，然後確定**WSAPlayer**也**unchecked**，然後按一下**套用**。 執行此動作只是要確認已正確設定檔案。

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > 將標示這類的外掛程式，會設定它們僅適用於在 Unity 編輯器中。 有一組不同的專案會匯出從 Unity 後要使用 WSA 資料夾中的 Dll。

6.  接下來，您必須開啟**WSA**資料夾內**Insights**資料夾。 您會看到您剛才設定的相同檔案的複本。 選取此檔案，並在偵測器中，確定該**任何平台**是**unchecked**，然後確定**只** **WSAPlayer**是**檢查**。 按一下 **[套用]** 。

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-25.png)

7. 您現在必須遵循**步驟 4-6**，但*Newtonsoft*外掛程式改。 請參閱以下螢幕擷取畫面的結果應該如下所示。

    ![匯入 Unity 封裝](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>第 4 章-設定攝影機和使用者控制項

在這一章將設定觀景窗和控制項，以允許使用者查看，並在場景中移動。

1.  以滑鼠右鍵按一下空白區域，在階層窗格中，然後**建立 > 空白**。

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-26.png)

2.  重新命名以新的空 GameObject**相機父**。

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-27.png)

3.  以滑鼠右鍵按一下空白區域，在階層窗格中，然後**3D 物件**，然後在**球體**。

4.  重新命名球體**右手邊**。

5.  設定**轉換擴展**到右下的**0.1、 0.1、 0.1**

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-28.png)

6.  移除**球體 Collider**元件從按一下右手邊**齒輪**中*球體 Collider*元件，然後**移除元件**.

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-29.png)

7.  在 [階層] 面板拖曳**Main Camera**而**右手邊**物件上**相機父**物件。

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-30.png)

8.  設定**轉換的位置**兩個**Main Camera**並**右手邊**物件**0，0，0**。

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-31.png)

    ![設定觀景窗和使用者控制項](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>第 5 章-設定 Unity 場景中的物件

您現在將建立一些基本的圖形的場景，使用者可以與之互動。

1.  在中的空白區域按一下滑鼠右鍵*階層面板*，然後在**3D 物件**，然後選取**平面**。

2.  設定平面**轉換位置**要**0，-1，0**。

3.  設定平面**轉換擴展**要**5、 1、 5**。

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-33.png)

4.  建立基本材質以搭配您**平面**物件，使您更輕鬆地查看其他圖形。 瀏覽至您 *[專案] 面板*，按一下滑鼠右鍵，然後**建立**，後面接著**資料夾**，以建立新的資料夾。 命名**材料**。

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-34.png) ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-35.png)

5.  開啟**材料**資料夾，然後按一下滑鼠右鍵，按一下**建立**，然後**材料**，以建立新的資料。 命名**藍色**。

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-36.png) ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-37.png)

6.  與新**藍色**，查看在選取的資料*Inspector*，按一下 [矩形] 視窗一起**Albedo**。 選取藍色的色彩 (下一張圖片是**十六進位色彩：\#3592FFFF**)。 選擇之後，請按一下 [關閉] 按鈕。

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-38.png)

7.  拖曳您新的內容，從**材料**拖曳至您新建立的資料夾**平面**，場景中 (或將其放在**平面**物件內*階層*)。

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-39.png)

8.  在中的空白區域按一下滑鼠右鍵*階層面板*，然後在**3D 物件、 Capsule**。

    -  具有**Capsule**選取，變更其**轉換***位置*至： **-10、 1、 0**。

9.  在中的空白區域按一下滑鼠右鍵*階層面板*，然後在**3D 物件、 Cube**。

    -  具有**Cube**選取，變更其**轉換***位置*來：**0, 0, 10**.

10. 在中的空白區域按一下滑鼠右鍵*階層面板*，然後在**3D 物件、 球體**。

    -  具有**球體**選取，變更其**轉換***位置*來：**10, 0, 0**.

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > 這些*位置*的值為*建議*。 您可以自由設定到任何您想要的物件的位置，如果物件的距離太遠從相機是應用程式的使用者更容易。

11. 當您的應用程式執行時，它必須能夠識別中的場景，為了達成此目的的物件，它們需要來加以標記。 選取其中一個物件，並在*Inspector* ] 面板中，按一下 [**新增標記...** ，這將會交換*Inspector*具有**標記 & 層**面板。

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. 按一下  **+ （加號）** 符號，然後輸入標記名稱為**ObjectInScene**。

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > 如果您使用不同的名稱，您的標記，您必須確保這項變更也為了*DataFromAnalytics*， *ObjectTrigger*，並*視線*，更新版本中，指令碼，讓您物件是找不到，而且偵測到，場景中。

13. 建立的標記，您現在需要將它套用到所有三個物件。 從*階層*，保留**Shift**鍵，然後按一下  **Capsule**， **Cube**，以及**球體**，物件，然後在*Inspector*，按一下下拉式功能表中的，一起**標記**，然後按一下*ObjectInScene*標記您所建立。

    ![設定 Unity 場景中的物件](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>章節 6-建立 ApplicationInsightsTracker 類別

您必須建立第一個指令碼**ApplicationInsightsTracker**，它會負責：

1.  建立根據使用者互動，以提交至 Azure Application Insights 的事件。

2. 建立適當的事件名稱，根據使用者互動。

3. 正在提交事件與 Application Insights 服務執行個體。

若要建立此類別：

1.  以滑鼠右鍵按一下*專案 面板*，然後**建立 > 資料夾**。 將資料夾命名**指令碼**。

    ![建立 ApplicationInsightsTracker 類別](images/AzureLabs-Lab309-46.png)  ![建立 ApplicationInsightsTracker 類別](images/AzureLabs-Lab309-47.png)

2.  具有**指令碼**建立資料夾，按兩下，以開啟。 然後，在該資料夾中，按一下滑鼠右鍵**建立 > C\#指令碼**。 指令碼命名**ApplicationInsightsTracker**。

3.  按兩下新**ApplicationInsightsTracker**指令碼，以開啟它**Visual Studio**。

4.  更新命名空間頂端的 指令碼，如下所示：

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  類別內插入下列變數：

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
    > 設定**instrumentationKey，applicationId 和 API_Key**值適當地使用*服務金鑰*從 Azure 入口網站中所述[第 1 章](#chapter-1---the-azure-portal)，步驟 9及更新版本。

6.  然後新增**start （)** 並**Awake()** 類別初始化時呼叫的方法：

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

7.  新增方法負責傳送的事件與註冊您的應用程式的計量：

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

8.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-7---create-the-gaze-script"></a>第 7-建立視線指令碼

下一步 以建立指令碼**視線**指令碼。 此指令碼會負責建立*Raycast* ，從將轉寄投影*Main Camera*，來偵測使用者查看的物件。 在此情況下， *Raycast*需要識別使用者查看的物件是否**ObjectInScene**標記，並計算多久使用者*gazes*在該物件。

1.  按兩下**指令碼**資料夾，將它開啟。

2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** > **C\#指令碼**。 指令碼命名**視線**。

3.  按兩下要使用 Visual Studio 中開啟它的指令碼。

4.  以下列取代現有的程式碼：

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

5.  程式碼**Awake()** 並**start （)** 方法現在需要加入。

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

6.  內部**視線**類別中，新增下列程式碼**update （)** 方法，以專案*Raycast*並偵測目標叫用：

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

7.  新增**ResetFocusedObject()** 方法，將資料傳送至**Application Insights**當使用者已檢閱過的物件。

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

8.  您現在已完成**視線**指令碼。 您將變更儲存在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-8---create-the-objecttrigger-class"></a>第 8-建立 ObjectTrigger 類別

您必須建立下一個指令碼是**ObjectTrigger**，它會負責：

- 新增到 Main Camera 的衝突所需的元件。
- 偵測相機是否標記為物件附近**ObjectInScene**。

若要建立指令碼：

1.  按兩下**指令碼**資料夾，將它開啟。

2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** **C\# > 指令碼**。 指令碼命名**ObjectTrigger**。

3.  按兩下要使用 Visual Studio 中開啟它的指令碼。 以下列取代現有的程式碼：

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

4.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-9---create-the-datafromanalytics-class"></a>第 9-建立 DataFromAnalytics 類別

您現在必須建立**DataFromAnalytics**指令碼，也就是負責：

- 正在擷取哪些物件已著手一同由相機最多的分析資料。
- 使用*服務金鑰*，可讓您的 Azure Application Insights 服務執行個體的通訊。
- 排序場景中的物件，根據具有最高的事件計數。
- 為變更材質的色彩，最 approached 物件的*綠色*。

若要建立指令碼：

1.  按兩下**指令碼**資料夾，將它開啟。

2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** **C\# > 指令碼**。 指令碼命名**DataFromAnalytics**。

3.  按兩下要使用 Visual Studio 中開啟它的指令碼。

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

5.  在指令碼中，插入下列各項：

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

6.  內**DataFromAnalytics**類別中，以滑鼠右鍵後**start （)** 方法，新增下列方法呼叫**FetchAnalytics()** 。 這個方法會負責的機碼值組清單已填入*GameObject*和預留位置事件計數數目。 然後初始化**GetWebRequest()** 協同程式。 若要呼叫的查詢結構*Application Insights*可以找到這個方法內同時，如同*查詢 URL*端點。

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

7.  正下方**FetchAnalytics()** 方法，新增一個方法，叫做**GetWebRequest()** ，就會傳回*IEnumerator*。 這個方法會負責要求事件，且具有特定對應的次數*GameObject*，已呼叫內*Application Insights*。 傳回所有已傳送的查詢，當**DetermineWinner()** 呼叫方法。

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
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

8.  下一個方法是**DetermineWinner()** ，其排序的清單*GameObject*並*Int*組，根據最高的事件計數。 然後，會變更的材質的色彩*GameObject*要*綠色*（做為其具有最高計數的意見反應）。 這會顯示分析結果的訊息。

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

9.  新增將用於還原序列化 JSON 物件，從接收的類別結構*Application Insights*。 在最下面加入這些類別您**DataFromAnalytics**類別檔案**外部**類別定義。

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

10. 請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-10---create-the-movement-class"></a>第 10-建立移動類別

**移動**指令碼是您必須建立下一個指令碼。 它會負責：

- 移動觀景窗的方向根據 Main Camera 會正面朝向。
- 加入場景物件中的所有其他指令碼。

若要建立指令碼：

1.  按兩下**指令碼**資料夾，將它開啟。

2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** > **C\#指令碼**。 指令碼命名**移動**。

3.  按兩下要開啟它的指令碼*Visual Studio*。

4.  以下列取代現有的程式碼：

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

5.  內**移動**類別*以下*空白**update （)** 方法中，插入下列方法，可讓使用者使用手動控制站虛擬空間中移動：

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

6.  最後將加入在方法呼叫內**update （)** 方法。

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-11---setting-up-the-scripts-references"></a>第 11 章-設定指令碼參考

在本章中，您必須將放**移動**拖曳至指令碼**相機父**並設定其參考的目標。 該指令碼會接著處理放置其他指令碼能所需的位置。

1.  從**指令碼**中的資料夾 *[專案] 面板*，拖曳**移動**指令碼來**相機父**中找到的物件*階層面板*。

    ![設定 Unity 場景中的指令碼參考](images/AzureLabs-Lab309-48.png)

2.  按一下 **相機父**。 在*階層面板*，拖曳**右手邊**物件*階層面板*至參考的目標，**控制器**中*Inspector 面板*。 設定**使用者速度**要**5**，如下圖所示。

    ![設定 Unity 場景中的指令碼參考](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>第 12 章-建置 Unity 專案

此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。

1.  瀏覽至**組建設定**， **(檔案 > 組建設定...)** .

2.  從**Build Settings**  視窗中，按一下**建置**。

    ![建置 Unity 專案至 UWP 方案](images/AzureLabs-Lab309-50.png)

3.  A**檔案總管**視窗將會快顯視窗，提示您輸入組建的位置。 建立新的資料夾 (依序按一下**新的資料夾**左上角)，並將它命名**建置**。

    ![建置 Unity 專案至 UWP 方案](images/AzureLabs-Lab309-51.png)

    1.  開啟新**組建**資料夾，並建立另一個資料夾 (使用**新資料夾**一次)，並將它命名**MR\_Azure\_應用程式\_Insights**。

        ![建置 Unity 專案至 UWP 方案](images/AzureLabs-Lab309-52.png)

    2.  具有**MR\_Azure\_應用程式\_Insights**按一下 選取資料夾**選取資料夾**。 專案需要約一分鐘來建置。

4.  遵循*建置*，**檔案總管**會出現顯示您的新專案的位置。

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>第 13 章-MR_Azure_Application_Insights 應用程式部署到您的電腦

若要部署**MR\_Azure\_應用程式\_Insights**本機電腦上的應用程式：

1.  開啟的方案檔您**MR\_Azure\_應用程式\_Insights**中的應用程式**Visual Studio**。

2.  在 **的方案平台**，選取**x86，本機電腦**。

3.  在 **方案組態**選取**偵錯**。

    ![建置 Unity 專案至 UWP 方案](images/AzureLabs-Lab309-53.png)

4.  移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。

5.  您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。

6. 啟動混合的實境應用程式。

7. 接近物件，並查看它們，場景中四處移動時*Azure Insight 服務*已收集足夠的事件資料，它將會設定已著手最多為綠色的物件。

> [!IMPORTANT] 
> 雖然的平均等候時間*事件和度量*收集由服務需要大約 15 分鐘，在某些情況下可能需要最多 1 小時。

## <a name="chapter-14---the-application-insights-service-portal"></a>第 14 章-Application Insights 服務入口網站

當您將會漫遊周圍場景，而且 gazed 數個物件在您所見中收集的資料*Application Insights 服務*入口網站。

1.  回到您的 Application Insights 服務入口網站。

2.  按一下 *計量瀏覽器*。

    ![查看所收集的資料](images/AzureLabs-Lab309-54.png)

3.  它會包含代表圖形 索引標籤中開啟*事件和度量*應用程式相關。 如上所述，可能需要一些時間 （最多 1 小時），資料才會顯示在圖形

    ![查看所收集的資料](images/AzureLabs-Lab309-55.png)

4.  按一下 *事件列*中*的事件總數*應用程式版本，若要查看的事件其名稱的詳細的細目。

    ![查看所收集的資料](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>您已完成您的 Application Insights 服務應用程式

恭喜，您所建立的混合的實境應用程式，利用 Application Insights 服務，來監視應用程式內的使用者的活動。

![課程結果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Bonus 練習

**練習 1**

嘗試產生，而不是以手動方式建立 ObjectInScene 物件，並在指令碼內的平面上設定其座標。 如此一來，您可以要求 Azure 的最受歡迎的哪些物件已 （無論是從視線或相近的結果） 和繁衍*額外*其中一個物件。

**練習 2**

讓您取得最相關的資料，並在您的應用程式中實作該時間敏感的資料，則您可以依照時間，您的 Application Insights 結果。

