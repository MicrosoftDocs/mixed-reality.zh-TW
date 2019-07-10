---
title: MR 和 Azure 308-跨裝置通知
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 通知中樞、 Azure Functions 和 Azure 儲存體和資料表。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 通知、 函式、 資料表、 通知中樞、 hololens、 沉浸式 vr
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694610"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR 和 Azure 308:跨裝置通知

![最終產品-開始](images/AzureLabs-Lab8-00.png)

在此課程中，您將學習如何使用 Azure 通知中樞、 Azure 資料表和 Azure Functions 的混合的實境應用程式中加入通知中樞功能。

**Azure 通知中樞**是 Microsoft 的服務，這可讓開發人員作為目標，並個人化推播通知傳送到任何平台，所有電源雲端內。 這可以有效地讓開發人員與終端使用者進行通訊，或甚至溝通各種應用程式，視案例而定。 如需詳細資訊，請瀏覽**Azure 通知中樞**[頁面](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)。

**Azure Functions**是 Microsoft 服務，可讓開發人員執行程式碼片段，'函式'，在 Azure 中。 這可用來將工作委派給雲端，而不是您本機的應用程式，可以有許多優點。 **Azure Functions**支援數種開發語言，包括 C\#，F\#、 Node.js、 Java 和 PHP。 如需詳細資訊，請瀏覽**Azure Functions** [頁面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

**Azure 資料表**Microsoft 雲端服務，讓開發人員能夠在雲端中儲存結構化的非 SQL 資料，因此能夠輕鬆存取任何位置。 服務擁有許多無結構描述的設計，如有需要讓資料表的發展，因此非常大的彈性。 如需詳細資訊，請瀏覽**Azure 資料表**[頁面](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

完成本課程之後，您會有混合的實境沈浸式耳機應用程式和桌上型電腦應用程式，可以執行下列作業：

1. 桌面電腦應用程式可讓使用者將物件移 2D 空間 （X，Y） 中使用滑鼠。

2. 移動的 PC 應用程式內的物件將會傳送至雲端，使用 JSON，這將會以字串的格式，其中包含的物件識別碼、 類型，並轉換資訊 （X 和 Y 座標）。 

3. 混合的實境應用程式，具有相同的場景，傳統型應用程式，會收到來自 「 通知中樞 」 服務 （這只是已更新的桌上型電腦應用程式） 的相關物件移動的通知。 

4. 收到通知，其中將包含物件識別碼、 類型和轉換資訊，mixed 的 reality 應用程式會套用至它自己的場景的已接收的資訊。

在您的應用程式，則您對於如何將整合結果進行設計。 本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。 它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。 本課程是獨立的教學課程，其中並不直接包含任何其他混合實境實驗室。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 308:跨裝置通知</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然這堂課程主要著重於 Windows Mixed Reality 沈浸式 (VR) 耳機，您也可以套用到 Microsoft HoloLens 本課程中您學到什麼。 當您依照本課程中，您會看到便箋上的任何變更，您可能需要用來支援 HoloLens。 當使用 HoloLens，您可能會發現某些回應語音擷取期間。

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
- 網際網路存取 Azure 的安裝程式，並存取通知中樞

## <a name="before-you-start"></a>開始之前

- 若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。
- 您必須是您的 Microsoft 開發人員入口網站和您的應用程式註冊入口網站的擁有者，否則您不會存取中的應用程式的權限[第 2 章](#chapter-2---retrieve-your-new-apps-credentials)。

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>第 1-Microsoft 開發人員入口網站建立應用程式

若要使用**Azure 通知中樞**服務，您必須建立應用程式上 Microsoft 開發人員入口網站中，因為您的應用程式必須進行註冊，使其可以傳送和接收通知。

1.  登入[Microsoft 開發人員入口網站](https://developer.microsoft.com/dashboard)。

    > 您必須登入您的 Microsoft 帳戶。

2.  從儀表板中，按一下**建立新的應用程式**。

    ![建立應用程式](images/AzureLabs-Lab8-01.png)

3.  會出現快顯視窗，其中您要為新的應用程式保留名稱。 在文字方塊中，插入適當的名稱;如果選擇的名稱可用，刻度會出現右邊的文字方塊中。 插入可用名稱之後，按一下**保留產品名稱**快顯視窗的左下方的按鈕。

    ![反向名稱](images/AzureLabs-Lab8-02.png)

4.  現在建立應用程式時，您已準備好移至下一步 一章項目。

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>第 2-擷取新的應用程式認證

登入應用程式註冊入口網站中，新的應用程式會列出，而擷取的認證將用來安裝**通知中樞服務**內**Azure 入口網站**。

1.  瀏覽至[應用程式註冊入口網站](http://apps.dev.microsoft.com)。

    ![應用程式註冊入口網站](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > 您必須使用您的 Microsoft 帳戶登入。  
    > 這**必須**是用在舊版的 Microsoft 帳戶[章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)，使用 Windows 市集開發人員入口網站。

2.  您會發現您的應用程式**我的應用程式**一節。 一旦找到它，按一下它，然後您會前往新頁面，具有應用程式名稱加上**註冊**。

    ![您新註冊的應用程式](images/AzureLabs-Lab8-04.png)

3.  捲動註冊頁面，尋找您**應用程式祕密**一節並**封裝 SID**應用程式。 用於設定複製**Azure 通知中樞服務**下一步 一章中。

    ![應用程式祕密](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>章節 3-設定 Azure 入口網站： 建立通知中樞 」 服務

使用您的應用程式的認證擷取，您需要移至 Azure 入口網站中，您將在其中建立 Azure 通知中樞服務。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE] 
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**新增**在左上角，，然後搜尋**通知中樞**，然後按一下***Enter***。

    ![通知中樞的搜尋](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > 單字***的新***可能已取代為**建立資源**，較新的入口網站中。

3.  新的頁面將提供的描述*通知中樞*服務。 在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。

    ![建立通知中樞執行個體](images/AzureLabs-Lab8-07.png)

4.  一旦您按下 ***建立*** :

    1.  插入您想要的名稱，此服務執行個體。

    2.  提供**命名空間**您會將與此應用程式產生關聯。

    3.  選取**位置。**

    4.  選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。

        > 如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。 

    5.  選取適當**訂用帳戶**。

    6.  您也必須確認您已了解這些條款和條件套用到此服務。

    7. 選取 [建立]  。

        ![填寫 服務詳細資料](images/AzureLabs-Lab8-08.png)

5.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

6.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![通知](images/AzureLabs-Lab8-09.png)

7.  按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 您將會被重新導向至新**通知中樞**服務執行個體。

    ![前往資源](images/AzureLabs-Lab8-10.png)
    
8.  從 概觀 頁面的中途頁面上，按一下  **Windows (WNS)。** 在右側面板會顯示兩個文字欄位，需要變更您**封裝 SID**並**安全性金鑰**，從您先前設定的應用程式。

    ![新建立的中樞服務](images/AzureLabs-Lab8-11.png)

9. 一旦您正確的欄位複製的詳細資訊，請按一下**儲存**，而且已成功更新通知中樞時，您會收到通知。

    ![複製安全性詳細資料](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>章節 4-設定 Azure 入口網站： 建立表格服務

建立您的通知中樞 」 服務執行個體之後, 瀏覽回到您的 Azure 入口網站，您將在其中建立儲存體資源建立 Azure 資料表服務。

1.  如果您尚未登入，登入[Azure 入口網站](https://portal.azure.com)。

2.  登入之後，按一下**新增**在左上角，，然後搜尋**儲存體帳戶**，然後按一下**Enter**。

    > [!NOTE] 
    > 單字***的新***可能已取代為**建立資源**，較新的入口網站中。

3.  選取 **儲存體帳戶-blob、 檔案、 資料表、 佇列**從清單中。

    ![搜尋儲存體帳戶](images/AzureLabs-Lab8-13.png)

4.  新的頁面將提供的描述**儲存體帳戶**服務。 在此提示，選取的左下方**建立**按鈕，以建立此服務的執行個體。

    ![建立儲存體執行個體](images/AzureLabs-Lab8-14.png)

5.  一旦您按下**建立**，面板會顯示：

    1. 插入您想要**名稱**（必須是全部小寫） 此服務執行個體。

    2. 針對**部署模型**，按一下**Resource manager**。

    3.  針對**帳戶種類**，使用下拉式功能表，選取**儲存體 (一般用途 v1)** 。

    4. 選取適當**位置**。
    
    5.  針對**複寫**下拉式功能表中，選取**讀取-存取-異地備援儲存體 (RA-GRS)** 。

    6.  針對**效能**，按一下**標準**。

    7.  內**需要安全傳輸**區段中，選取**停用**。

    8.  從**訂用帳戶**下拉式功能表中，選取適當的訂用帳戶。

    9.  選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。

        > 如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 離開**虛擬網路**作為**停用**如果這是您的選項。

    11. 按一下 [建立]  。

        ![填入儲存體詳細資料](images/AzureLabs-Lab8-15.png)

6.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

7.  通知會出現在入口網站中，一旦建立服務執行個體。 按一下通知，以探索新的服務執行個體。

    ![新的儲存體通知](images/AzureLabs-Lab8-16.png)

8.  按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 您將會進入您新的儲存體服務執行個體概觀 頁面。

    ![前往資源](images/AzureLabs-Lab8-17.PNG)

9. 從 [概觀] 頁面的右手邊的側邊，按一下**資料表**。
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. 在右側面板會變更以顯示**表格服務**資訊，您要在其中加入新的資料表。 依序按一下 **+** **表格**左上角的按鈕。

    ![開啟資料表](images/AzureLabs-Lab8-19.png)

11. 新的頁面將會顯示，您要在其中輸入**資料表名稱**。 這是您用來在您的應用程式，在後續章節中的資料所參考的名稱。 插入適當的名稱，然後按**確定**。

    ![建立新的資料表](images/AzureLabs-Lab8-20.png)    

12. 一旦建立新的資料表，您將能夠看到它內**表格服務**頁面 （位於底部）。

    ![建立新資料表](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>第 5 章-完成 Visual Studio 中的 Azure 資料表

既然您**表格服務**儲存體帳戶是否已設定，就可以開始將資料加入至它，將會用來儲存和擷取資訊。 編輯您的資料表可透過**Visual Studio**。

1.  開啟**Visual Studio**。

2.  從功能表中，按一下**檢視** > **Cloud Explorer**。

    ![開啟 cloud explorer](images/AzureLabs-Lab8-22.png)

3.  **Cloud Explorer**會開啟為停駐項目 （耐心等候，因為載入可能會花費的時間）。

    > [!NOTE] 
    > 如果您用來建立訂用帳戶您*儲存體帳戶*不可見，請確定您已： 
    > - 與您在 Azure 入口網站使用相同的帳戶登入。
    > - 從 [帳戶] 管理頁面 （您可能需要從您的帳戶設定套用篩選），選取您的訂用帳戶：  
    >
    >   ![尋找訂用帳戶](images/AzureLabs-Lab8-22-5.png)

4.  Azure 雲端服務將會顯示。 尋找**儲存體帳戶**按一下箭號左側，展開您的帳戶。

    ![開啟儲存體帳戶](images/AzureLabs-Lab8-23.png)

5.  一旦展開時，您新建立**儲存體帳戶**應該可用。 按一下您的儲存體中，左邊的箭號之後，會展開，然後尋找**資料表**，按一下，以顯示旁的箭號**資料表**在最後一章中所建立。 按兩下您**資料表**。

    ![開啟場景物件的資料表](images/AzureLabs-Lab8-24.png)

6.  您的資料表將會開啟您的 Visual Studio 視窗中央。 按一下 [資料表] 圖示，以 **+** （加上） 在其上。

    ![加入新的資料表](images/AzureLabs-Lab8-25.png)

7.  接著會出現視窗提示要*新增實體*。 您將建立三個實體中每個都有數個屬性的總計。 您將會發現*PartitionKey*並*RowKey*已提供，這些資料表所用來尋找您的資料。 

    ![資料分割和資料列索引鍵](images/AzureLabs-Lab8-26.png)

8. 更新*值*的**PartitionKey**並**RowKey** ，如下所示 (請記住，若要這樣做為您新增時，每個資料列屬性但每次遞增 RowKey):

    ![加入正確的值](images/AzureLabs-Lab8-26-5.png)

9.  按一下 **將屬性加入**新增額外的資料列的資料。 讓您比對的第一個空白資料表下表。

10. 按一下 **確定**完畢時。

    ![完成時，請按一下 [確定]](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > 請確定您已變更**型別**的**X**， **Y**，以及**Z**，項目，以**Double**。 

11. 您會發現您的資料表現在有一個資料列。 按一下 [ **+** （加號）] 圖示以新增另一個實體。

    ![第一個資料列](images/AzureLabs-Lab8-27-5.png)

12. 建立一個額外的屬性，然後將 新實體，以符合那些如下所示的值。

    ![新增 cube](images/AzureLabs-Lab8-28.png)

13. 重複最後一個步驟，以新增另一個實體。 設定此實體的值，如下所示。

    ![加入圓柱圖](images/AzureLabs-Lab8-29.png)

14. 您的資料表現在看起來應該像下面這樣。

    ![完整的資料表](images/AzureLabs-Lab8-30.png)

15. 您已完成這一章。 請務必儲存。

## <a name="chapter-6---create-an-azure-function-app"></a>章節 6-建立 Azure 函式應用程式

建立 Azure 函數應用程式，若要更新的桌面應用程式會呼叫**表格**服務，並將傳送的通知**通知中樞**。

首先，您必須建立一個檔案，可讓您的 Azure 函式，將您所需的程式庫。

1.  開啟**記事本**（按 Windows 鍵和型別 [記事本]）。

    ![開啟 [記事本]](images/AzureLabs-Lab8-31.png)

2.  使用 「 記事本 」 開啟，在其中插入以下的 JSON 結構。 完成後，會將它儲存為您的桌面上**project.json**。 請務必確認名稱是否正確： 請確定它會**沒有.txt**副檔名。 如果您使用過它看起來會類似的 NuGet，此檔案會定義將使用您的函式，程式庫。

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  登入[Azure 入口網站](https://portal.azure.com)。

4.  一旦您登入，按一下**新增**在左上角，，然後搜尋**函式應用程式**、 按下**Enter**。

    ![搜尋函式應用程式](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > 單字**的新**可能已取代為**建立資源**，較新的入口網站中。

5.  新的頁面將提供的描述**函式應用程式**服務。 在此提示，選取的左下方**建立**按鈕，以建立與此服務的關聯。

    ![函式應用程式執行個體](images/AzureLabs-Lab8-33.png)

6.  一旦您按下**建立**，填入下列：

    1. 針對**應用程式名稱**，插入您想要的名稱，此服務執行個體。

    2. 選取 **訂用帳戶**。

    3. 選取定價層適合您，如果這是第一次建立**函式應用程式服務**，免費層應該是您可以使用。

    4. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將常見的資源群組下 （例如例如這些實驗室中） 的單一專案相關聯的所有 Azure 服務）。

        > 如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 針對**OS**，按一下 Windows，因為這是預期的平台。

    6. 選取 **主控方案**(使用本教學課程**取用方案**。

    7. 選取 **位置** **（上一個步驟中選擇您已建立的儲存體相同的位置）**

    8. 針對**儲存體**一節**您必須選取您在上一個步驟中建立的儲存體服務**。

    9. 您不需要*Application Insights*在此應用程式，因此您將它保留**關閉**。

    10. 按一下 [建立]  。

        ![建立新的執行個體](images/AzureLabs-Lab8-34.png)

7.  一旦您按下**建立**您必須建立服務，這可能需要一分鐘。

8.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![新的通知](images/AzureLabs-Lab8-35.png)

9.  按一下通知，以探索新的服務執行個體。

10. 按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 

    ![前往資源](images/AzureLabs-Lab8-36.png)

11. 按一下  **+** （加號） 旁的圖示*函式*至*新建*。

    ![新增新的函式](images/AzureLabs-Lab8-37.png)

12. 在中央窗格中，**函式**建立視窗會出現。 忽略的窗格中，上半部中的資訊，然後按一下**自訂函式**，位在靠近底部 （在藍色區域中，如下所示）。

    ![自訂函式](images/AzureLabs-Lab8-38.png)

13. 在視窗內新的頁面會顯示各種函式類型。 向下捲動以檢視紫色的類型，然後按一下**HTTP PUT**項目。

    ![http put 連結](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > 您可能要進一步向下捲動一頁 （和此映像可能不看起來完全相同，如果您尚未執行 Azure 入口網站更新），不過，您要尋找的項目呼叫*HTTP PUT*。

14. **HTTP PUT**視窗會出現，您要設定函式 （請參閱下方的映像）。

    1.  針對**語言**使用下拉式功能表中，選取 C\#。

    2.  針對**名稱，** 輸入適當的名稱。

    3.  在 **驗證層級**下拉式功能表中，選取**函式**。

    4.  針對**資料表名稱**區段中，您需要使用您用來建立的確切名稱您**資料表**服務先前 （包括相同的字母大小寫）。

    5.  內**儲存體帳戶連線**區段中，使用下拉式功能表，然後從該處選取儲存體帳戶。 如果那里，按一下**新增**與區段標題，以顯示另一個面板，應該會列出您的儲存體帳戶的超連結。

        ![新的儲存體](images/AzureLabs-Lab8-40.png)

15. 按一下 **建立**而且您會收到通知，您的設定已成功更新。

    ![建立函式](images/AzureLabs-Lab8-41.png)

16. 按一下後**建立**，您會被重新導向至函式編輯器。

    ![更新函式程式碼](images/AzureLabs-Lab8-42.png)

17. （取代函式中的程式碼） 的函式編輯器中插入下列程式碼：

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > 使用內含的程式庫，在函數收到的名稱和位置的物件已移動的 Unity 場景中 (做為C#物件，稱為**UnityGameObject**)。 這個物件接著會用來更新物件內的參數建立的資料表中。 在此之後，函式可讓您建立的通知中樞服務，就會通知所有訂閱的應用程式的呼叫。

18. 中位置的程式碼，請按一下**儲存**。

19. 接下來，按一下 **\<** （箭頭） 圖示，在頁面的右手邊。

    ![開啟上傳 面板](images/AzureLabs-Lab8-43.png)

20. 從右邊的窗格中將投影片。 在該面板中，按一下**上傳**，檔案瀏覽器將會出現。

21. 瀏覽至，然後按一下 []， **project.json**中建立的檔案**記事本**之前，然後按一下 [**開啟**] 按鈕。 此檔案會定義您的函式會使用的程式庫。

    ![上傳 json](images/AzureLabs-Lab8-44.png)

22. 檔案已上傳時，它會出現在右側面板。 按一下將內開啟它**函式**編輯器。 它必須看起來**完全**下一步 的映像 （下面步驟 23） 相同。

23. 然後，在左側面板下方**函式**，按一下**整合**連結。

    ![整合函式](images/AzureLabs-Lab8-45.png)

24. 在下一步 頁面上，在右上角，按一下**進階的編輯器**（如下）。

    ![開啟進階編輯器](images/AzureLabs-Lab8-46.png)

25. A **function.json**檔案將會開啟在中央窗格中，必須以下列程式碼片段取代。 這會定義您要建置的函式和參數傳遞至函式。

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. 您的編輯器現在看起來應該類似下面的影像：

    ![回到標準編輯器](images/AzureLabs-Lab8-47.png)

27. 您可能會注意到您剛插入的輸入的參數可能不符合您的資料表和儲存體詳細資料，因此將需要使用您的資訊來更新。 **請不要這樣這裡**，如接下來指涵蓋。 只要按一下**標準編輯器**連結，頁面上，若要返回右上角。

28. 回到**標準編輯器**，按一下**Azure 資料表儲存體 （資料表）** 下方**輸入**。 
    
    ![資料表輸入](images/AzureLabs-Lab8-47-5.png)

29. 請確定下列比對**您**的詳細資訊，因為它們可能會不同 （沒有下列步驟的映像）：

    1.  **資料表名稱**： 您在 Azure 儲存體，資料表服務內建立的資料表名稱。

    2.  **儲存體帳戶連接：** 按一下 **新**旁下拉式功能表中，會出現，面板會顯示視窗的右邊。

        ![新的儲存體](images/AzureLabs-Lab8-48.png)

        1.  選取您**儲存體帳戶**，您先前建立到主機**函式應用程式。**

        2. 您將會發現**儲存體帳戶**已建立連接值。

        3. 請務必按下**儲存**完成之後。

    3.  **輸入**頁面上現在應該符合下面顯示**您**資訊。

        ![完整的輸入](images/AzureLabs-Lab8-49.png)

30. 接下來，按一下 **（通知） 的 Azure 通知中樞**-底下**輸出**。 請確認下列與進行比對**您**的詳細資訊，因為它們可能會不同 （沒有下列步驟的映像）：

    1.  **通知中樞名稱**： 這是名稱您**通知中樞**服務執行個體，您在先前所建立。

    2.  **通知中樞命名空間連線**： 按一下 **新**，旁邊的下拉式清單中的功能表會出現。

        ![檢查輸出](images/AzureLabs-Lab8-50.png)

    3. **連接**快顯視窗會出現 （請參閱下圖），您要選取**命名空間**的**通知中樞**，其中您先前設定。

    4. 選取您**通知中樞**從中間的下拉式清單中的功能表名稱。

    5.  設定**原則**下拉式功能表， **DefaultFullSharedAccessSignature**。

    6. 按一下 [**選取**返回] 按鈕。

        ![更新輸出](images/AzureLabs-Lab8-51.png)

31.  **輸出**頁面上現在應該符合以下，但**您**資訊改為。 請務必按下**儲存**。

> [!WARNING]
> *請勿直接編輯的通知中樞名稱*(這所有應該使用**進階編輯器**，前提是您正確地遵循上述步驟。

![完整的輸出](images/AzureLabs-Lab8-50.png)

32. 此時，您應該測試函式，以確保其正常運作。 請這樣做： 

    1. 瀏覽至函式頁面一次：

        ![完整的輸出](images/AzureLabs-Lab8-50-1.png)

    2. 返回 [函式] 頁面中，按一下 [**測試**] 索引標籤上，請在頁面上，開啟最右端*測試*刀鋒視窗中：

        ![完整的輸出](images/AzureLabs-Lab8-50-2.png)

    3. 內**要求本文**文字方塊中的刀鋒視窗中，貼上下列程式碼：

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. 使用就地測試程式碼中，按一下**執行**右下方，以及測試 按鈕將會執行。 測試的輸出記錄檔會出現在 [主控台] 區域中，您的函式程式碼下方。

        ![完整的輸出](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > 如果上述的測試失敗，您必須再次檢查您已遵循上述步驟，特別是在設定**整合面板**。 

## <a name="chapter-7---set-up-desktop-unity-project"></a>第 7 章-設定桌面 Unity 專案

> [!IMPORTANT]
> 您現在正在建立的桌面應用程式**不會**在 Unity 編輯器中工作。 它必須執行外部編輯器中，遵循建置的應用程式中，然後再使用 Visual Studio （或已部署的應用程式）。 

下列使用 Unity 進行開發及混合的實境，由一組典型，此情況下，是良好的其他專案範本。

設定並測試您的混合的實境沈浸式耳機。

> [!NOTE] 
> 您將會**不**本課程所需動作的控制器。 如果您需要支援沈浸式耳機的設定，請遵循此[連結，有關如何設定 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  開啟**Unity**然後按一下**新增**。

    ![新的 unity 專案](images/AzureLabs-Lab8-52.png)

2.  您需要提供 Unity 專案名稱、 插入**UnityDesktopNotifHub**。 請確定專案類型設定為**3D**。 設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![建立專案](images/AzureLabs-Lab8-53.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯** > **喜好設定**並從新的視窗，然後瀏覽至**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![設定外部的 VS 工具](images/AzureLabs-Lab8-54.png)

4.  接下來，移至**檔案** > **組建設定**，然後選取**通用 Windows 平台**，然後按一下 **切換平台**按鈕以套用您的選擇。

    ![切換平台](images/AzureLabs-Lab8-55.png)

5.  當您依然在**檔案** > **組建設定**，請確定：

    1.  **裝置為目標**設為**任何裝置**

        > 此應用程式將會為您的桌面，因此必須**任何裝置**

    2.  **建置型別**設為**D3D**

    3.  **SDK**設為**最新安裝**

    4.  **Visual Studio 版本**設為**最新安裝**

    5.  **建置並執行**設為**本機電腦**

    6.  在這裡值得儲存場景，並將它新增至組建。

        1. 做法是選取**加入開啟的場景**。 儲存視窗會出現。

            ![將開啟的場景新增](images/AzureLabs-Lab8-56.png)

        2. 建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![新的場景資料夾](images/AzureLabs-Lab8-57.png)

        3. 開啟您剛建立**場景**資料夾，然後在**檔案名稱：** 文字欄位中輸入**NH\_Desktop\_場景**，然後按**儲存**。

            ![新的 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  剩餘的設定，**組建設定**，應保持為預設值，現在。

6.  在相同的視窗中按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。

7.  在此窗格中，少數設定需要驗證：

    1.  在 [**其他設定**] 索引標籤：

        1.  **指令碼執行階段版本**應該是**實驗性 （.NET 4.6 對等）**

        2. **指令碼後端**應該是 **.NET**

        3. **API 相容性層級**應該是 **.NET 4.6**

            ![4.6 的.net 版本](images/AzureLabs-Lab8-59.png)

    2.  內**發佈設定**索引標籤之下**功能**，檢查：

        - **InternetClient**

            ![刻度網際網路用戶端](images/AzureLabs-Lab8-60.png)

8.  回到**Build Settings** *Unity C\#專案*不再呈現灰色，這旁邊的核取方塊。

9.  關閉**組建設定**視窗。

10. 儲存您的場景和專案**檔案** > **儲存場景檔案** > **儲存專案**。

    > [!IMPORTANT]
    > 如果您想要跳過*Unity 設定*元件 （桌面應用程式），此專案並繼續直接進入程式碼，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)，它匯入到您的專案做為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。  您仍必須新增指令碼元件。

## <a name="chapter-8---importing-the-dlls-in-unity"></a>第 8 章-匯入 Unity 中的 Dll

您將針對 Unity 使用 Azure 儲存體 （而其本身會利用.Net SDK for Azure）。 如需詳細資訊請遵循這[解 Unity 的 Azure 儲存體的連結](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。

這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。 這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。

若要 SDK 匯入您自己的專案，請確定您已下載最新[ **.unitypackage** ](https://aka.ms/azstorage-unitysdk)從 GitHub。 然後，執行下列作業：

1.  新增 **.unitypackage**若要使用的 Unity**資產\>匯入封裝\>自訂封裝**功能表選項。

2.  在 **匯入 Unity 封裝**方塊，顯示，您可以選取下方的所有內容 * **外掛程式* \> * 儲存 * * *。  取消選取所有項目不需要這堂課程。

    ![匯入封裝](images/AzureLabs-Lab8-61.png)

3.  按一下 ***匯入***按鈕以新增至您的專案項目。

4.  移至**儲存體**下方的資料夾**外掛程式**專案中檢視，然後選取下列外掛程式*只*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![取消選取任何平台](images/AzureLabs-Lab8-62.png)

5.  具有*這些特定的外掛程式*選取，**取消核取** **任何平台**並**取消核取** **WSAPlayer**然後按一下**套用**。

    ![適用於平台的 dll](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > 我們會將標示要僅適用於在 Unity 編輯器中的這些特定外掛程式。 這是因為有不同版本的專案會匯出從 Unity 後要使用 WSA 資料夾中的同一個外掛程式。

6.  在 **儲存體**外掛程式資料夾中，只選取：

    -   Microsoft.Data.Services.Client

        ![dll 不會處理集合](images/AzureLabs-Lab8-64.png)

7.  請檢查**不處理程序**下方**平台設定**，按一下 ***套用***。

    ![適用於任何處理](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > 我們會標示此外掛程式不處理，因為 Unity 組件修補程式已處理此外掛程式的困難度。 即使它不會處理此外掛程式仍然可以運作。

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>第 9-桌面 Unity 專案中建立 TableToScene 類別

您現在要建立包含程式碼以執行此應用程式的指令碼。

您必須建立第一個指令碼**TableToScene**，它會負責：

-   讀取 Azure 資料表中的實體。
-   使用資料表資料，來判斷哪些物件來繁衍 （spawn），以及在哪些位置。

您必須建立第二個指令碼**CloudScene**，它會負責：

-   註冊以滑鼠左鍵按一下事件，以允許使用者拖曳物件周圍的場景。
-   序列化物件資料，從這個 Unity 場景，並將它傳送至 Azure 函式應用程式。

若要建立此類別：

1.  以滑鼠右鍵按一下**Asset**  資料夾位於 專案 面板**建立** > **資料夾**。 將資料夾命名**指令碼**。

    ![建立指令碼 資料夾](images/AzureLabs-Lab8-66.png)

    ![建立指令碼資料夾 2](images/AzureLabs-Lab8-67.png)

2.  按兩下剛才建立開啟的資料夾。

3.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。 指令碼命名**TableToScene**。

    ![新的 c# 指令碼](images/AzureLabs-Lab8-68.png)
    ![TableToScene 重新命名](images/AzureLabs-Lab8-69.png)

4.  按兩下要開啟 Visual Studio 2017 中的指令碼。

5.  加入下列命名空間：

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  在類別中，插入下列變數：

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > Substitute **accountName**值與您 Azure 儲存體服務的名稱並**accountKey**具有金鑰的值，在 Azure 入口網站 （請參閱下圖） 中的 Azure 儲存體服務中找到的值。 
    >
    > ![擷取帳戶金鑰](images/AzureLabs-Lab8-70.png)

7.  現在，加入**start （)** 並**Awake()** 來初始化類別的方法。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  內**TableToScene**類別中，新增會從 Azure 資料表中擷取值，以及使用它們來繁衍 （spawn） 在場景中適當的基本類型的方法。

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  Outside **TableToScene**類別，您需要應用程式用來序列化和還原序列化的類別定義**資料表實體**。

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. 請務必**儲存**之前返回至 Unity Editor。

11. 按一下 [ **Main Camera**從**階層**] 面板中，使其屬性會出現在**Inspector**。

12. 具有**指令碼**資料夾中開啟，選取的指令碼**TableToScene 檔案**然後拖曳到**Main Camera**。 結果應該如下：

    ![將指令碼新增至主攝影機](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>第 10-桌面 Unity 專案中建立 CloudScene 類別

您必須建立第二個指令碼**CloudScene**，它會負責：

-   註冊以滑鼠左鍵按一下事件，以允許使用者拖曳物件周圍的場景。

-   序列化物件資料，從這個 Unity 場景，並將它傳送至 Azure 函式應用程式。

若要建立第二個指令碼：

1.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立**， **C\#指令碼**。 指令碼命名**CloudScene**
    
    ![新的 c# 指令碼](images/AzureLabs-Lab8-72.png)
    ![重新命名 CloudScene](images/AzureLabs-Lab8-73.png)

2.  加入下列命名空間：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  插入下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Substitute **azureFunctionEndpoint**與下圖所示，在 Azure 函式應用程式服務中，在 Azure 入口網站中，找到您的 Azure 函式應用程式 URL 的值：

    ![取得函式 URL](images/AzureLabs-Lab8-74.png)

5.  現在，加入**start （)** 並**Awake()** 來初始化類別的方法。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  內**update （)** 方法，將會偵測滑鼠輸入，並拖曳，會依次移動 Gameobject 場景中的下列程式碼。 如果使用者拖曳並卸除物件，它會將名稱和物件的座標傳遞至方法**UpdateCloudScene()** ，這會呼叫 Azure 函式應用程式服務，這會更新 Azure 資料表和觸發程序通知。

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  現在，加入**UpdateCloudScene()** 方法，如下所示：

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  儲存程式碼，並返回到 Unity

9.  拖曳**CloudScene**拖曳至指令碼**Main Camera**。 

    1. 按一下 [ **Main Camera**從**階層**] 面板中，使其屬性會出現在**Inspector**。 

    2. 具有**指令碼**資料夾開啟，請選取**CloudScene**指令碼，並將它拖曳到**Main Camera**。 結果應該如下：

        > ![拖曳主攝影機中的雲端指令碼](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>第 11 章-建置 UWP 桌面專案

此專案的 Unity 區段所需的所有項目現在已完成。

1.  瀏覽至**組建設定**(**檔案** > **組建設定**)。

2.  從**Build Settings**  視窗中，按一下**建置**。

    ![建置專案](images/AzureLabs-Lab8-76.png)

3.  A**檔案總管** 將會快顯視窗，提示您輸入要組建的位置。 建立新的資料夾 (依序按一下**新的資料夾**左上角)，並將它命名**建置**。

    ![組建的新資料夾](images/AzureLabs-Lab8-77.png)

    1.  開啟新**組建**資料夾，並建立另一個資料夾 (使用**新資料夾**一次)，並將它命名**NH\_Desktop\_應用程式**。

        ![資料夾名稱 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  具有**NH\_桌面\_應用程式**選取。 按一下 **選取資料夾**。 專案需要約一分鐘來建置。

4.  下列組建**檔案總管**會出現顯示您的新專案的位置。 若要開啟它，不過，您也可以視需要建立其他 Unity 專案首先，在接下來幾個章節則不需要。


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>第 12 章-設定混合實境 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟**Unity**然後按一下**新增**。

    ![新的 unity 專案](images/AzureLabs-Lab8-79.png)

2.  您現在需要提供 Unity 專案名稱、 插入**UnityMRNotifHub**。 請確定專案類型設定為**3D**。 設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯** > **喜好設定**並從新的視窗，然後瀏覽至**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![設定 VS 外部編輯器](images/AzureLabs-Lab8-81.png)

4.  接下來，移至**檔案** > **組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台**  按鈕。

    ![切換至 UWP 的平台](images/AzureLabs-Lab8-82.png)

5.  移至**檔案** > **組建設定**並確定：

    1.  **裝置為目標**設為**任何裝置**

        > 對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。

    2.  **建置型別**設為**D3D**

    3.  **SDK**設為**最新安裝**

    4.  **Visual Studio 版本**設為**最新安裝**

    5.  **建置並執行**設為**本機電腦**

    6.  在這裡值得儲存場景，並將它新增至組建。

        1. 做法是選取**加入開啟的場景**。 儲存視窗會出現。

            ![將開啟的場景新增](images/AzureLabs-Lab8-83.png)

        2. 建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![新的場景資料夾](images/AzureLabs-Lab8-84.png)

        3. 開啟您剛建立**場景**資料夾，然後在**檔案名稱：** 文字欄位中輸入**NH\_MR\_場景**，然後按下**儲存**。

            ![新的場景-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  剩餘的設定，**組建設定**，應保持為預設值，現在。

6.  在相同的視窗中按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置**Inspector**所在。    

    ![開啟 播放程式設定](images/AzureLabs-Lab8-86.png)

7.  在此窗格中，少數設定需要驗證：

    1.  在 [**其他設定**] 索引標籤：

        1.  **指令碼執行階段版本**應該**實驗性**（.NET 4.6 對等）
        2.  **指令碼後端**應該是 ***.NET***
        3.  **API 相容性層級**應該是 **.NET 4.6**

            ![api 相容性](images/AzureLabs-Lab8-87.png)

    2.  在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入

        ![更新 xr 設定](images/AzureLabs-Lab8-88.png)        

    3.  內**發佈設定**索引標籤之下**功能**，h:

        - **InternetClient**           

            ![刻度網際網路用戶端](images/AzureLabs-Lab8-89.png)

8.  回到**Build Settings**， **UnityC#專案**不再呈現灰色： 這旁邊的核取方塊。

9.  完成這些變更，關閉 [建立設定] 視窗。

10. 儲存您的場景和專案**檔案** > **儲存場景檔案** > **儲存專案**。

    > [!IMPORTANT]
    > 如果您想要跳過*Unity 設定*元件為此專案中 （混合實境應用程式），並直接在程式碼中繼續進行，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)，它匯入到您的專案，作為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)。 您仍必須新增指令碼元件。

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>第 13 章-匯入的混合的實境 Unity 專案中的 Dll

您將使用 Azure 儲存體的 Unity 文件庫 （這適用於 Azure 中使用.Net SDK）。 請遵循此[如何使用 Unity 的 Azure 儲存體的連結](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。
這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。 這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。

若要 SDK 匯入您自己的專案，請確定您已下載最新[.unitypackage](https://aka.ms/azstorage-unitysdk)。 然後，執行下列作業：

1.  新增您從上述項目，下載到使用 Unity.unitypackage**資產** > **匯入封裝** > **自訂封裝**功能表選項.

2.  在 **匯入 Unity 封裝**方塊，顯示，您可以選取下方的所有內容**外掛程式** > **儲存體**。

    ![匯入封裝](images/AzureLabs-Lab8-90.png)

3.  按一下 **匯入**按鈕以新增至您的專案項目。

4.  移至**儲存體**下方的資料夾**外掛程式**專案中檢視，然後選取下列外掛程式*只*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![選取外掛程式](images/AzureLabs-Lab8-91.png)

5.  具有*這些特定的外掛程式*選取，**取消核取** **任何平台**並**取消核取** **WSAPlayer**然後按一下**套用**。

    ![適用於平台的變更](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > 您必須先將這些特定的外掛程式，以僅適用於在 Unity 編輯器中。 這是因為有不同版本的專案會匯出從 Unity 後要使用 WSA 資料夾中的同一個外掛程式。

6.  在 **儲存體**外掛程式資料夾中，只選取：

    -   Microsoft.Data.Services.Client

        ![選取 data services 用戶端](images/AzureLabs-Lab8-93.png)

7.  請檢查**不處理程序**下方**平台設定**，按一下 **套用**。

    ![不會處理](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > 您必須先將此外掛程式 」 不會處理 」 的 Unity 組件修補程式發生無法處理此外掛程式。 即使它不處理的外掛程式仍然可以運作。

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>第 14 章-混合的實境 Unity 專案中建立 TableToScene 類別

**TableToScene**中所述的一個類別等同[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。 在 Unity 專案遵循相同的程序所述的混合實境中建立相同的類別[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。

當您完成這一章，這兩個您**Unity 專案**會有在 Main Camera 上設定這個類別。

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>第 15 章-混合實境 Unity 專案中建立 NotificationReceiver 類別

您必須建立第二個指令碼**NotificationReceiver**，它會負責：

-   在初始化時的通知中樞註冊的應用程式。
-   接聽來自通知中樞的通知。
-   還原序列化物件資料，從接收的通知。
-   場景，根據已還原序列化資料中移動 Gameobject。

若要建立**NotificationReceiver**指令碼：

1.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立**， **C\#指令碼**。 指令碼命名**NotificationReceiver**。

    ![建立新的 c# 指令碼](images/AzureLabs-Lab8-95.png)
    ![命名 NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  按兩下要開啟的指令碼。

3.  加入下列命名空間：

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  插入下列變數：

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Substitute **hubName**值與您通知中樞服務的名稱，並**hubListenEndpoint**值與存取原則 索引標籤中，Azure 通知中樞服務中找到的端點值Azure 入口網站 （請參閱下圖）。

    ![插入通知中樞原則端點](images/AzureLabs-Lab8-97.png)

6.  現在，加入**start （)** 並**Awake()** 來初始化類別的方法。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  新增**WaitForNotification**方法，以允許應用程式以接收來自通知中樞程式庫的通知，而不發生衝突與主執行緒：

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  下列方法**InitNotificationAsync()** ，會向通知中樞服務在初始化應用程式。 程式碼標記為註解為 Unity 將無法建置專案。 當您匯入 Visual Studio 中的 Azure 傳訊的 Nuget 套件，您將會移除註解。

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  下列處理常式中，**通道\_PushNotificationReceived()** ，每次接收到通知時，就會觸發。 它將會還原序列化該通知上方，它會於桌面應用程式中，已移動之 Azure 資料表實體，然後將對應的 GameObject MR 場景中移至相同的位置。 
    
    > [!IMPORTANT]
    > 因為程式碼會參考 Azure 傳訊程式庫，您將會新增在建置使用 Nuget 套件管理員，在 Visual Studio 的 Unity 專案之後，會註解化程式碼。 因此，Unity 專案將無法建置，除非它標記為註解。請注意，您應該建置您的專案，然後想要傳回至 Unity，您必須**恢復註解**該程式碼。

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. 請務必先返回至 Unity 編輯器中儲存變更。

11. 按一下 [ **Main Camera**從**階層**] 面板中，使其屬性會出現在**Inspector**。

12. 具有**指令碼**資料夾開啟，請選取**NotificationReceiver**指令碼，並將它拖曳到**Main Camera**。 結果應該如下：

    ![拖曳至攝影機的通知接收者指令碼](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > 如果您正在開發這 Microsoft HoloLens，您必須更新**Main Camera**的*相機*元件，以便：
    > - 清除旗標：純色
    > - 背景：黑色

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>第 16 章-建置混合的實境專案至 UWP

這一章等同於建置前一個專案的程序。 此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。

1.  瀏覽至**組建設定**(**檔案** > **組建設定**)。

2.  從**Build Settings**  功能表中，確保**UnityC#專案*** 已核 （這可讓您在建置後編輯此專案中的指令碼）。

3.  這麼做之後，請按一下**建置**。

    ![建置專案](images/AzureLabs-Lab8-99.png)

4.  A**檔案總管** 將會快顯視窗，提示您輸入要組建的位置。 建立新的資料夾 (依序按一下**新的資料夾**左上角)，並將它命名**建置**。

    ![建立組建 資料夾](images/AzureLabs-Lab8-100.png)

    1.  開啟新**組建**資料夾，並建立另一個資料夾 (使用**新資料夾**一次)，並將它命名**NH\_MR\_應用程式**。

        ![建立 NH_MR_Apps 資料夾](images/AzureLabs-Lab8-101.png)

    2.  具有**NH\_MR\_應用程式**選取。 按一下 **選取資料夾**。 專案需要約一分鐘來建置。

5.  下列組建**檔案總管**視窗就會開啟新專案的位置。



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>第 17 章-加入 UnityMRNotifHub 方案的 NuGet 套件

> [!WARNING] 
> 請記住，一旦您將下列 NuGet 封裝 (並在下一個程式碼取消註解[章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class))，程式碼，在 Unity 專案中，重新開啟時將會顯示錯誤。 如果您想要返回並繼續編輯在 Unity 編輯器中，您將需要發表評論該 errosome 程式碼中，，然後取消註解一次更新的版本，一旦您已回到 Visual Studio。 

完成混合的實境組建之後，瀏覽至混合的實境專案中，您建立，並按兩下該資料夾，若要使用 Visual Studio 2017 中開啟您的方案中的方案 (.sln) 檔案。
您現在需要新增**WindowsAzure.Messaging.managed** NuGet 套件，這是用來接收來自通知中樞通知程式庫。

若要匯入的 NuGet 套件：

1.  在 [**方案總管] 中**，以滑鼠右鍵按一下您的解決方案

2.  按一下 **管理 NuGet 封裝**。

    ![開啟 nuget 管理員](images/AzureLabs-Lab8-102.png)

3.  選取 ***瀏覽***索引標籤，然後搜尋**WindowsAzure.Messaging.managed**。

    ![尋找 windows azure 傳訊套件](images/AzureLabs-Lab8-103.png)

4.  選取結果 （如下所示），然後在右側視窗中，選取核取方塊旁**專案**。 這將會置於刻度核取方塊旁**專案**，以及旁的核取方塊**組件 CSharp**並**UnityMRNotifHub**專案。

    ![勾選所有專案](images/AzureLabs-Lab8-104.png)

5.  一開始提供的版本**可能不**與此專案相容。 因此，按一下功能表上的下拉式清單旁**版本**，然後按一下**版本 0.1.7.9**，然後按一下**安裝**。

6.  您現在已完成安裝 NuGet 套件。 尋找您在中輸入註解的程式碼**NotificationReceiver**類別，並移除註解...



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>第 18 章-編輯 UnityMRNotifHub 應用程式、 NotificationReceiver 類別

下列加**NuGet 套件**，您必須*取消註解*部分中的程式碼**NotificationReceiver**類別。

這包括：

1. 在頂端命名空間：

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. 內的所有程式碼**InitNotificationsAsync()** 方法：

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> 上述程式碼中有註解： 請確定您已不會無意*取消註解*，註解 （如程式碼將不會編譯有 ！）。

3. 而且，最後**Channel_PushNotificationReceived**事件：

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

使用這些取消註解，請確定您儲存，，，然後繼續進行下一步 一章。

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>將第 19 章-產生關聯的混合的實境專案，為市集應用程式

您現在必須將關聯**混合實境**中建立實驗室的開頭為市集應用程式的專案。

1.  開啟的方案。

2.  在方案總管 窗格中，移至 UWP 應用程式專案上按一下滑鼠右鍵**存放區**，和**與市集建立關聯的應用程式...** .

    ![開啟市集關聯](images/AzureLabs-Lab8-105.png)

3.  會出現一個新的視窗呼叫**產生關聯您的應用程式與 Windows 市集**。 按一下 [下一步]  。

    ![請移至下一個畫面](images/AzureLabs-Lab8-106.png)

4.  它會載入與您已登入的帳戶相關聯的所有應用程式。 如果您未登入您的帳戶，您可以**登入**此頁面上。

5.  尋找**市集應用程式名稱**，您在本教學課程開頭所建立，並加以選取。 然後按一下 [下一步]  。

    ![尋找並選取您的存放區名稱](images/AzureLabs-Lab8-107.png)

6.  按一下 **產生關聯**。

    ![應用程式建立關聯](images/AzureLabs-Lab8-108.png)

7.  您的應用程式現在已**相關聯**市集應用程式。 這是必要的啟用通知。

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>第 20 章-部署 UnityMRNotifHub 和 UnityDesktopNotifHub 應用程式

這一章可能容易，因為兩名人員，結果會包含同時執行的應用程式，在 Desktop 中，您電腦上的一個執行，另一個沈浸式耳機內。

耳機沈浸式應用程式正在等候接收場景 （本機 Gameobject 的位置變更，） 的變更和傳統型應用程式會對其本機場景 （位置的變更） 會共用 MR 應用程式進行變更。 合理 MR 應用程式部署在第一次，後面傳統型應用程式，以便開始接聽的接收者。

若要部署**UnityMRNotifHub**本機電腦上的應用程式：

1.  開啟的方案檔您**UnityMRNotifHub**中的應用程式**Visual Studio 2017**。

2.  在 **的方案平台**，選取**x86，本機電腦**。

3.  在 **方案組態**選取**偵錯**。

    ![設定專案組態](images/AzureLabs-Lab8-109.png)

4.  移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。

5.  您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。

若要部署**UnityDesktopNotifHub**本機電腦上的應用程式：

1.  開啟的方案檔您**UnityDesktopNotifHub**中的應用程式**Visual Studio 2017**。

2.  在 **的方案平台**，選取**x86，本機電腦**。

3.  在 **方案組態**選取**偵錯**。

    ![設定專案組態](images/AzureLabs-Lab8-110.png)

4.  移至**建置 功能表**，然後按一下**部署方案**側載應用程式到您的電腦。

5.  您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。

6.  啟動混合的實境應用程式，後面接著的桌面應用程式。

這兩個執行的應用程式，請在桌面的場景 （使用左滑鼠按鈕） 中移動的物件。 這些位置的變更會在本機進行，序列化，且傳送至函式應用程式服務。 函式應用程式服務會更新與通知中樞的資料表。 接收更新，通知中樞將更新的資料直接傳送到所有已註冊應用程式 （在此案例的沈浸式耳機應用程式），接著還原序列化傳入的資料，並將新的位置資料套用至本機的物件，您可以移動它們在場景中。


## <a name="your-finished-your-azure-notification-hubs-application"></a>您已完成您的 Azure 通知中樞應用程式
 
恭喜，您所建立的混合的實境應用程式會利用 「 Azure 通知中樞 」 服務，並允許應用程式之間的通訊。
 
![最終產品-結束](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

您可以變更 Gameobject 的色彩，並將該通知傳送給其他應用程式檢視場景怎麼運作嗎？

### <a name="exercise-2"></a>練習 2

您可以對 MR 應用程式中新增的 Gameobject 移動並傳統型應用程式中看到更新的場景嗎？
