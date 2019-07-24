---
title: MR 和 Azure 308-跨裝置通知
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 通知中樞、Azure Functions 和 Azure 儲存體和資料表。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合現實, 學術, unity, 教學課程, api, 通知, 函數, 資料表, 通知中樞, hololens, 沉浸, vr
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694610"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。  因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊, 以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時, 使用這些教學課程的連結進行更新。

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR 和 Azure 308:跨裝置通知

![最終產品-開始](images/AzureLabs-Lab8-00.png)

在此課程中, 您將瞭解如何使用 Azure 通知中樞、Azure 資料表和 Azure Functions, 將通知中樞功能新增至混合現實應用程式。

**Azure 通知中樞**是一種 Microsoft 服務, 可讓開發人員將目標和個人化推播通知傳送至任何平臺, 並在雲端中提供所有功能。 這可有效地讓開發人員與使用者進行通訊, 或甚至在各種應用程式之間進行通訊, 視案例而定。 如需詳細資訊, 請造訪**Azure 通知中樞**[頁面](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)。

**Azure Functions**是一項 Microsoft 服務, 可讓開發人員在 Azure 中執行一小段程式碼, 即「函式」。 這可讓您將工作委派給雲端, 而不是您的本機應用程式, 這可能有許多好處。 **Azure Functions**支援數種開發語言, 包括\#C、\#F、node.js、JAVA 和 PHP。 如需詳細資訊, 請造訪**Azure Functions** [頁面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

**Azure 資料表**是一項 Microsoft 雲端服務, 可讓開發人員在雲端中儲存結構化的非 SQL 資料, 讓您可以輕鬆地在任何地方存取。 此服務具有無架構設計, 可讓您視需要進行資料表演進, 因此非常有彈性。 如需詳細資訊, 請造訪**Azure 資料表**[頁面](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

完成此課程之後, 您將擁有一個混合現實的沉浸式耳機應用程式, 以及一個桌上型電腦應用程式, 其將能夠執行下列動作:

1. 桌上型電腦應用程式可讓使用者使用滑鼠來移動2D 空間 (X 和 Y) 中的物件。

2. 電腦應用程式中的物件移動會使用 JSON 傳送至雲端, 其格式為字串, 其中包含物件識別碼、類型和轉換資訊 (X 和 Y 座標)。 

3. 混合現實應用程式 (其具有與桌面應用程式相同的場景) 將會從通知中樞服務 (剛由桌上型電腦應用程式更新) 接收有關物件移動的通知。 

4. 收到包含物件識別碼、類型和轉換資訊的通知時, mixed reality 應用程式會將接收的資訊套用到自己的場景。

在您的應用程式中, 您可以決定如何將結果與您的設計整合。 本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。 您的工作是使用您從這個課程取得的知識, 來增強您的混合現實應用程式。 本課程是獨立的教學課程, 不直接牽涉到其他任何混合現實實驗室。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 308:跨裝置通知</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然此課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機, 但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。 隨著課程的遵循, 您會看到您可能需要用來支援 HoloLens 的任何變更的附注。 使用 HoloLens 時, 您可能會在語音捕獲期間發現一些回應。

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。 也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (5 月 2018)。 您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。

在此課程中, 我們建議您採用下列硬體和軟體:

- [與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦, 可用於沉浸式 (VR) 耳機開發
- [已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 已啟用開發人員模式的[Windows Mixed Reality 沉浸 (VR) 耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 適用于 Azure 設定和存取通知中樞的網際網路存取

## <a name="before-you-start"></a>開始之前

- 為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。
- 您必須是 Microsoft 開發人員入口網站和應用程式註冊入口網站的擁有者, 否則您將不會擁有存取[第2章](#chapter-2---retrieve-your-new-apps-credentials)中應用程式的許可權。

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>第1章-在 Microsoft 開發人員入口網站上建立應用程式

若要使用**Azure 通知中樞**服務, 您將需要在 Microsoft 開發人員入口網站上建立應用程式, 因為您的應用程式需要註冊, 才能傳送和接收通知。

1.  登入[Microsoft 開發人員入口網站](https://developer.microsoft.com/dashboard)。

    > 您必須登入您的 Microsoft 帳戶。

2.  在儀表板中, 按一下 [**建立新的應用程式**]。

    ![建立應用程式](images/AzureLabs-Lab8-01.png)

3.  隨即會出現一個快顯視窗, 您需要為新的應用程式保留名稱。 在文字方塊中, 插入適當的名稱;如果選擇的名稱可用, 則會在文字方塊的右邊顯示刻度。 插入可用名稱之後, 請按一下快顯視窗左下方的 [**保留產品名稱**] 按鈕。

    ![反向名稱](images/AzureLabs-Lab8-02.png)

4.  現在已建立應用程式, 您已準備好移至下一章。

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>第2章-取得新的應用程式認證

登入應用程式註冊入口網站, 其中會列出您的新應用程式, 並抓取將用來在**Azure 入口網站**中設定**通知中樞服務**的認證。

1.  流覽至[應用程式註冊入口網站](http://apps.dev.microsoft.com)。

    ![應用程式註冊入口網站](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > 您必須使用您的 Microsoft 帳戶登入。  
    > 這**必須**是您在上一[章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)中使用的 Microsoft 帳戶, 以及 Windows Store 開發人員入口網站。

2.  您會在 [**我的應用程式**] 區段下找到您的應用程式。 找到之後, 請按一下它, 您將會進入新的頁面, 其中包含應用程式名稱加上**註冊**。

    ![您剛註冊的應用程式](images/AzureLabs-Lab8-04.png)

3.  向下流覽註冊頁面, 以尋找**應用程式**的 [秘密] 區段和 [**套件 SID** ]。 在下一章中, 複製兩者以用於設定**Azure 通知中樞服務**。

    ![應用程式秘密](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>第3章-設定 Azure 入口網站: 建立通知中樞服務

取得您的應用程式認證之後, 您必須移至 Azure 入口網站, 您將在其中建立 Azure 通知中樞服務。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE] 
    > 如果您還沒有 Azure 帳戶, 您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。

2.  登入之後, 按一下左上角的 [**新增**], 並搜尋 [**通知中樞**], 然後按一下***Enter 鍵***。

    ![搜尋通知中樞](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > 在較新的入口網站中,***新***的「可能」已取代為「**建立資源**」。

3.  [新增] 頁面將會提供*通知中樞*服務的描述。 在此提示的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。

    ![建立通知中樞實例](images/AzureLabs-Lab8-07.png)

4.  一旦您按下 ***建立*** :

    1.  為此服務實例插入您想要的名稱。

    2.  提供可讓您與此應用程式建立關聯的**命名空間**。

    3.  選取 [**位置]。**

    4.  選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。

        > 如果您想要深入瞭解 Azure 資源群組, 請遵循此[連結以瞭解如何管理資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。 

    5.  選取適當的**訂**用帳戶。

    6.  您也必須確認您已瞭解適用于此服務的條款及條件。

    7. 選取 [建立]。

        ![填寫服務詳細資料](images/AzureLabs-Lab8-08.png)

5.  按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。

6.  建立服務實例之後, 入口網站中會出現通知。

    ![通知](images/AzureLabs-Lab8-09.png)

7.  按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。 您將會進入新的**通知中樞**服務實例。

    ![前往資源](images/AzureLabs-Lab8-10.png)
    
8.  從 [總覽] 頁面中, 按一下頁面的正下方, 然後按一下 [ **Windows (WNS)]。** 右邊的面板將會變更, 以顯示兩個文字欄位, 其中需要您先前設定的應用程式中的**套件 SID**和**安全性金鑰**。

    ![新建立的中樞服務](images/AzureLabs-Lab8-11.png)

9. 將詳細資料複製到正確的欄位之後, 按一下 [**儲存**], 您就會在通知中樞已成功更新時收到通知。

    ![複製安全性詳細資料](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>第4章-設定 Azure 入口網站: 建立資料表服務

建立通知中樞服務實例之後, 流覽回到您的 Azure 入口網站, 您將藉由建立儲存體資源來建立 Azure 資料表服務。

1.  如果尚未登入, 請登入[Azure 入口網站](https://portal.azure.com)。

2.  登入之後, 按一下左上角的 [**新增**], 並搜尋 [**儲存體帳戶**], 然後按一下**Enter 鍵**。

    > [!NOTE] 
    > 在較新的入口網站中,***新***的「可能」已取代為「**建立資源**」。

3.  從清單中選取 [**儲存體帳戶-blob、檔案、資料表、佇列**]。

    ![搜尋儲存體帳戶](images/AzureLabs-Lab8-13.png)

4.  新的頁面會提供**儲存體帳戶**服務的描述。 在此提示的左下方, 選取 [**建立**] 按鈕, 以建立此服務的實例。

    ![建立儲存體實例](images/AzureLabs-Lab8-14.png)

5.  當您按一下 [**建立**] 之後, 就會出現一個面板:

    1. 為此服務實例插入您想要的**名稱**(必須全部小寫)。

    2. 針對 [**部署模型**], 按一下 [ **Resource manager**]。

    3.  針對 [**帳戶種類**], 使用下拉式功能表, 選取 [**儲存體 (一般用途 v1)** ]。

    4. 選取適當的**位置**。
    
    5.  針對 [ 複寫] 下拉式功能表, 選取 [**讀取權限-異地-多餘儲存體 (RA-GRS)** ]。

    6.  針對 [**效能**], 請按一下 [**標準**]。

    7.  在 [**需要安全傳輸**] 區段中, 選取 [**停用**]。

    8.  從 [**訂**用帳戶] 下拉式功能表中, 選取適當的訂用帳戶。

    9.  選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。

        > 如果您想要深入瞭解 Azure 資源群組, 請遵循此[連結以瞭解如何管理資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 如果這是您的選項, 請將 [**虛擬網路**] 保留為 [**停用**]。

    11. 按一下 [建立] 。

        ![填入儲存體詳細資料](images/AzureLabs-Lab8-15.png)

6.  按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。

7.  建立服務實例之後, 入口網站中會出現通知。 按一下 [通知] 以探索新的服務實例。

    ![新的儲存體通知](images/AzureLabs-Lab8-16.png)

8.  按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。 您將會進入新的儲存體服務實例的 [總覽] 頁面。

    ![前往資源](images/AzureLabs-Lab8-17.PNG)

9. 從 [總覽] 頁面, 按一下右側的 [**資料表]** 。
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. 右側面板會變更, 以顯示**表格服務**資訊, 您需要在其中新增新的資料表。 若要這麼做, **+** 請按一下左上角的 [**資料表**] 按鈕。

    ![開啟資料表](images/AzureLabs-Lab8-19.png)

11. 將會顯示新的頁面, 您必須在其中輸入**資料表名稱**。 這是您在後續章節中用來參考應用程式中資料的名稱。 插入適當的名稱, 然後按一下 **[確定]** 。

    ![建立新資料表](images/AzureLabs-Lab8-20.png)    

12. 建立新的資料表之後, 您就可以在 [**表格服務**] 頁面 (底部) 中看到它。

    ![已建立新資料表](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>第5章-在 Visual Studio 中完成 Azure 資料表

既然已設定您的**表格服務**儲存體帳戶, 就可以在其中加入資料, 這將用來儲存和抓取資訊。 您可以透過**Visual Studio**來編輯您的資料表。

1.  開啟**Visual Studio**。

2.  從功能表中, 按一下 [ **View**  >  **Cloud Explorer**]。

    ![開啟 cloud explorer](images/AzureLabs-Lab8-22.png)

3.  **Cloud Explorer**將會開啟為停駐的專案 (請耐心等候, 因為載入可能需要一些時間)。

    > [!NOTE] 
    > 如果看不到您用來建立*儲存體帳戶*的訂用帳戶, 請確定您有: 
    > - 登入與您用於 Azure 入口網站的帳戶相同。
    > - 從 [帳戶管理] 頁面選取您的訂用帳戶 (您可能需要從您的帳戶設定套用篩選):  
    >
    >   ![尋找訂用帳戶](images/AzureLabs-Lab8-22-5.png)

4.  將會顯示您的 Azure 雲端服務。 尋找 [**儲存體帳戶**], 然後按一下該左側的箭號以展開您的帳戶。

    ![開啟儲存體帳戶](images/AzureLabs-Lab8-23.png)

5.  擴充之後, 應該就可以使用新建立的**儲存體帳戶**。 按一下儲存體左邊的箭號, 然後展開 [尋找**資料表**], 再按一下該按鈕旁邊的箭號, 以顯示您在上一章中建立的**資料表**。 按兩下您的**資料表**。

    ![開啟場景物件資料表](images/AzureLabs-Lab8-24.png)

6.  您的資料表將會在 Visual Studio 視窗的中央開啟。 按一下 [資料表] 圖示，以 **+** （加上） 在其上。

    ![加入新的資料表](images/AzureLabs-Lab8-25.png)

7.  隨即會出現一個視窗, 提示您*加入實體*。 您將會建立總共三個實體, 每個都有數個屬性。 您會發現*PartitionKey*和*RowKey*已提供, 因為資料表會使用這些來尋找您的資料。 

    ![資料分割和資料列索引鍵](images/AzureLabs-Lab8-26.png)

8. 更新**PartitionKey**和**RowKey**的*值*, 如下所示 (請務必針對您新增的每個資料列屬性執行此動作, 但每次都要增加 RowKey):

    ![新增正確的值](images/AzureLabs-Lab8-26-5.png)

9.  按一下 [**新增屬性**], 以新增額外的資料列。 讓您的第一個空白資料表符合下表。

10. 完成後, 請按一下 **[確定]** 。

    ![完成時按一下 [確定]](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > 請確定您已將**X**、 **Y**和**Z**等專案的**類型**變更為**Double**。 

11. 您會注意到您的資料表現在有一個資料列。 再次按一下 **+** (加號) 圖示, 以新增另一個實體。

    ![第一個資料列](images/AzureLabs-Lab8-27-5.png)

12. 建立其他屬性, 然後設定新實體的值以符合如下所示的值。

    ![新增 cube](images/AzureLabs-Lab8-28.png)

13. 重複最後一個步驟, 以加入另一個實體。 將此實體的值設定如下所示。

    ![新增圓柱](images/AzureLabs-Lab8-29.png)

14. 您的資料表現在看起來應該如下所示。

    ![資料表完成](images/AzureLabs-Lab8-30.png)

15. 您已完成這一章。 請務必儲存。

## <a name="chapter-6---create-an-azure-function-app"></a>第6章-建立 Azure 函數應用程式

建立 Azure 函數應用程式, 桌面應用程式將會呼叫它來更新**表格**服務, 並透過**通知中樞**傳送通知。

首先, 您必須建立可讓您的 Azure 函式載入所需程式庫的檔案。

1.  開啟 [**記事本**] (按 Windows 鍵, 然後輸入 [記事本])。

    ![開啟 [記事本]](images/AzureLabs-Lab8-31.png)

2.  在 [記事本] 開啟的情況下, 將下面的 JSON 結構插入其中。 完成之後, 請將它儲存在您的桌上型電腦上做為**專案 json**。 請務必正確地命名: 請確定它的副檔名**不是 .txt** 。 此檔案會定義您的函式將使用的程式庫, 如果您已經使用 NuGet, 它看起來會很熟悉。

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

4.  登入之後, 按一下左上角的 [**新增**], 然後搜尋**函數應用程式**, 按**enter**鍵。

    ![搜尋函數應用程式](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > 在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。

5.  [新增] 頁面將會提供**函數應用程式**服務的描述。 在此提示的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。

    ![函數應用程式實例](images/AzureLabs-Lab8-33.png)

6.  當您按一下 [**建立**] 之後, 請填寫下列內容:

    1. 針對 [**應用程式名稱**], 插入您想要的此服務實例名稱。

    2. 選取**訂**用帳戶。

    3. 選取適合您的定價層, 如果這是您第一次建立**函數應用程式服務**, 免費層應可供您使用。

    4. 選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。

        > 如果您想要深入瞭解 Azure 資源群組, 請遵循此[連結以瞭解如何管理資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 針對 [**作業系統**], 按一下 [Windows], 因為這是所需的平臺。

    6. 選取**主控方案**(本教學課程使用的是取用**方案**)。

    7. 選取**位置** **(選擇與您在上一個步驟中建立的儲存體相同的位置)**

    8. 針對 [**儲存體**] 區段,**您必須選取您在上一個步驟中建立的儲存體服務**。

    9. 您不需要在此應用程式中*Application Insights* , 因此請隨意保留。

    10. 按一下 [建立] 。

        ![建立新的實例](images/AzureLabs-Lab8-34.png)

7.  按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。

8.  建立服務實例之後, 入口網站中會出現通知。

    ![新通知](images/AzureLabs-Lab8-35.png)

9.  按一下 [通知] 以探索新的服務實例。

10. 按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。 

    ![前往資源](images/AzureLabs-Lab8-36.png)

11. 按一下 [ **+** 函式] 旁邊的 ( 加號) 圖示, 以*建立新*的。

    ![加入新函數](images/AzureLabs-Lab8-37.png)

12. 在中央面板中, 將會出現 [**函數**建立] 視窗。 忽略面板上半部的資訊, 然後按一下位於底部附近的 [**自訂**函式] (在藍色區域中, 如下所示)。

    ![自訂函數](images/AzureLabs-Lab8-38.png)

13. 視窗內的新頁面將會顯示各種功能類型。 向下滾動以查看紫色類型, 然後按一下 [ **HTTP PUT**元素]。

    ![HTTP put 連結](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > 您可能必須進一步向下滾動頁面 (如果已進行 Azure 入口網站更新, 此影像可能看起來不完全相同), 不過, 您正在尋找名為*HTTP PUT*的元素。

14. [ **HTTP PUT** ] 視窗隨即出現, 您必須在其中設定函式 (請參閱下方的影像)。

    1.  針對 [**語言],** 使用下拉式功能表, 選取 [\#C]。

    2.  針對 [**名稱],** 輸入適當的名稱。

    3.  在 [**驗證層級**] 下拉式功能表中, 選取 [函式]。

    4.  在 [**資料表名稱**] 區段中, 您必須使用先前用來建立**資料表**服務的確切名稱 (包括相同的字母大小寫)。

    5.  在 [**儲存體帳戶連接**] 區段中, 使用下拉式功能表, 然後從該處選取您的儲存體帳戶。 如果沒有出現, 請按一下 [**新增**] 超連結和區段標題, 以顯示另一個面板, 其中列出您的儲存體帳戶。

        ![新增存放裝置](images/AzureLabs-Lab8-40.png)

15. 按一下 [**建立**], 您就會收到通知, 指出您的設定已成功更新。

    ![create 函式](images/AzureLabs-Lab8-41.png)

16. 按一下 [**建立**] 之後, 系統會將您重新導向至 [函數編輯器]。

    ![更新函式程式碼](images/AzureLabs-Lab8-42.png)

17. 將下列程式碼插入函數編輯器中 (取代函式中的程式碼):

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
    > 函式會使用包含的程式庫, 接收在 Unity 場景中移動之物件的名稱和位置 (稱為**UnityGameObject**的C#物件)。 然後, 這個物件會用來更新所建立之資料表內的物件參數。 在此之後, 函式會呼叫已建立的通知中樞服務, 這會通知所有已訂閱的應用程式。

18. 備妥程式碼後, 按一下 [**儲存**]。

19. 接下來，按一下 **\<** （箭頭） 圖示，在頁面的右手邊。

    ![開啟上傳面板](images/AzureLabs-Lab8-43.png)

20. 面板會從右邊滑入。 在該面板中, 按一下 **[上傳**], 檔案瀏覽器隨即出現。

21. 流覽至, 然後按一下 [您先前在**記事本**中建立的**專案. json**檔案], 再按一下 [**開啟**] 按鈕。 此檔案會定義您的函式將使用的程式庫。

    ![上傳 json](images/AzureLabs-Lab8-44.png)

22. 檔案上傳之後, 它就會出現在右邊的面板中。 按一下它會在**函數**編輯器中開啟它。 它的外觀必須和下一個影像**完全**相同 (在步驟23底下)。

23. 然後, 在左側面板中, 按一下 [函式] 底下的 [**整合**] 連結。

    ![整合函式](images/AzureLabs-Lab8-45.png)

24. 在下一個頁面上, 按一下右上角的 [ **Advanced editor** ] (如下所示)。

    ![開啟進階編輯器](images/AzureLabs-Lab8-46.png)

25. 將會在中央面板中開啟函式**json**檔案, 此檔案必須以下列程式碼片段取代。 這會定義您要建立的函式, 以及傳遞至函式的參數。

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

26. 您的編輯器現在看起來應該如下圖所示:

    ![回到標準編輯器](images/AzureLabs-Lab8-47.png)

27. 您可能會注意到剛才插入的輸入參數可能不符合您的資料表和儲存體詳細資料, 因此需要以您的資訊進行更新。 請不要在**這裡執行此**動作, 如下所述。 只要按一下頁面右上角的 [**標準編輯器**] 連結, 即可返回。

28. 回到**標準編輯器**中, 按一下 [**輸入**] 底下的 **[Azure 表格儲存體 (資料表)** ]。 
    
    ![資料表輸入](images/AzureLabs-Lab8-47-5.png)

29. 請確定**您**的資訊符合下列各項, 因為它們可能不同 (以下步驟中有映射):

    1.  **資料表名稱**: 您在 Azure 儲存體資料表服務內建立的資料表名稱。

    2.  **儲存體帳戶連線:** 按一下 [**新增**], 這會出現在下拉式功能表旁邊, 而面板會出現在視窗的右側。

        ![新增存放裝置](images/AzureLabs-Lab8-48.png)

        1.  選取您先前建立用來裝載**函數應用程式**的**儲存體帳戶**。

        2. 您會發現已建立**儲存體帳戶**連接值。

        3. 完成後, 請務必按 [**儲存**]。

    3.  [**輸入**] 頁面現在應符合下列內容, 其中顯示**您**的資訊。

        ![輸入完成](images/AzureLabs-Lab8-49.png)

30. 接下來, 在 [**輸出**] 下按一下 [ **Azure 通知中樞 (通知)** ]。 請確定下列各項已符合**您**的資訊, 因為它們可能不同 (以下步驟中有一個影像):

    1.  **通知中樞名稱**: 這是您先前建立的**通知中樞**服務實例的名稱。

    2.  **通知中樞命名空間**連線: 按一下 [**新增**], 這會出現在下拉式功能表旁。

        ![檢查輸出](images/AzureLabs-Lab8-50.png)

    3. [ 連線] 快顯視窗隨即出現 (請參閱下圖), 您必須在此選取您先前設定的**通知中樞** **命名空間**。

    4. 從中間下拉式功能表中選取您的**通知中樞**名稱。

    5.  將**原則**下拉式功能表設定為**DefaultFullSharedAccessSignature**。

    6. 按一下 [**選取**] 按鈕以返回。

        ![輸出更新](images/AzureLabs-Lab8-51.png)

31.  [**輸出**] 頁面現在應符合下列內容, 但會改為使用**您**的資訊。 請務必按 [**儲存**]。

> [!WARNING]
> *請勿直接編輯通知中樞名稱*(這一切都應該使用**進階編輯器**完成, 前提是您已正確地遵循先前的步驟。

![輸出完成](images/AzureLabs-Lab8-50.png)

32. 此時, 您應該測試函式, 以確保其運作正常。 請這樣做： 

    1. 再次流覽至 [函式] 頁面:

        ![輸出完成](images/AzureLabs-Lab8-50-1.png)

    2. 回到 [函數] 頁面, 按一下頁面最右邊的 [**測試**] 索引標籤, 以開啟 [*測試*] 分頁:

        ![輸出完成](images/AzureLabs-Lab8-50-2.png)

    3. 在分頁的 [**要求**本文] 文字方塊中, 貼上下列程式碼:

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

    4. 測試程式碼準備就緒後, 按一下右下方的 [**執行**] 按鈕, 測試將會執行。 測試的輸出記錄將會出現在您的函式程式碼下方的主控台區域中。

        ![輸出完成](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > 如果上述測試失敗, 您必須再次檢查您已遵循上述步驟, 特別是 [**整合] 面板**中的設定。 

## <a name="chapter-7---set-up-desktop-unity-project"></a>第7章-設定桌面 Unity 專案

> [!IMPORTANT]
> 您現在建立的桌面應用程式**將無法**在 Unity 編輯器中使用。 您必須使用 Visual Studio (或已部署的應用程式), 在應用程式建立後, 于編輯器之外執行。 

以下是使用 Unity 和 mixed reality 進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本。

設定和測試混合現實的沉浸式耳機。

> [!NOTE] 
> 在此課程中, 您將**不**需要有動作控制器。 如果您需要支援設定沉浸式耳機, 請遵循此[連結以瞭解如何設定 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  開啟**Unity** , 然後按一下 [**新增**]。

    ![新增 unity 專案](images/AzureLabs-Lab8-52.png)

2.  您需要提供 Unity 專案名稱, 並插入**UnityDesktopNotifHub**。 請確定 [專案類型] 設定為 [ **3d**]。 將位置設定為適合您的**位置**(請記住, 接近根目錄較佳)。 然後, 按一下 [**建立專案**]。

    ![建立專案](images/AzureLabs-Lab8-53.png)

3.  在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 [**編輯** > **喜好**設定], 然後在新視窗中, 流覽至 [**外部工具**]。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

    ![設定外部 VS 工具](images/AzureLabs-Lab8-54.png)

4.  接下來, 移  > 至 [檔案] [**組建設定**] 並選取 [**通用 Windows 平臺**], 然後按一下 [**切換平臺**] 按鈕以套用您的選取專案。

    ![交換器平臺](images/AzureLabs-Lab8-55.png)

5.  仍在 [   > 檔案**組建] 設定**中, 請確定:

    1.  **目標裝置**已設定為**任何裝置**

        > 此應用程式將適用于您的桌面, 因此必須是**任何裝置**

    2.  **組建類型**設定為**D3D**

    3.  **SDK**已設定為**最新安裝**

    4.  **Visual Studio 版本**設定為 [**最新安裝**]

    5.  **組建和執行**設定為**本機電腦**

    6.  在這裡, 很值得儲存場景, 並將它加入組建。

        1. 選取 [新增] [**開啟場景**] 來執行此動作。 [儲存] 視窗隨即出現。

            ![新增開啟的場景](images/AzureLabs-Lab8-56.png)

        2. 為此建立新的資料夾, 並在任何未來的場景中選取 [**新增資料夾**] 按鈕, 以建立新的資料夾, 將其命名為**場景**。

            ![新增背景資料夾](images/AzureLabs-Lab8-57.png)

        3. 開啟新建立的 [**幕後**] 資料夾, 然後在 [**檔案名:** 文字] 欄位中, 輸入**NH\_Desktop\_場景**, 然後按 [**儲存**]。

            ![新增 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  [**組建設定**] 中的其餘設定, 現在應該保留為預設值。

6.  在相同的視窗中, 按一下 [**玩家設定**] 按鈕, 這會在偵測**器**所在的空間中開啟相關的面板。

7.  在此面板中, 需要驗證幾項設定:

    1.  在 [**其他設定**] 索引標籤中:

        1.  **腳本執行階段版本**應該是**實驗性 (.Net 4.6 對等用法)**

        2. **腳本後端**應該是 **.net**

        3. **API 相容性層級**應該是 **.net 4.6**

            ![4.6 net 版本](images/AzureLabs-Lab8-59.png)

    2.  在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:

        - **InternetClient**

            ![勾選網際網路用戶端](images/AzureLabs-Lab8-60.png)

8.  回到**組建設定**: *Unity C\#專案*不再呈現灰色; 勾選此旁的核取方塊。

9.  關閉 [**組建設定**] 視窗。

10. 儲存場景和專案**檔** > **儲存場景/**  > 檔案**儲存專案**。

    > [!IMPORTANT]
    > 如果您想要略過此專案的*Unity 設定*元件 (傳統型應用程式), 並直接繼續執行程式碼, 您可以[下載這個 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), 將它匯入您的專案中做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html), 然後從[一章繼續9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。  您仍然需要新增腳本元件。

## <a name="chapter-8---importing-the-dlls-in-unity"></a>第8章-匯入 Unity 中的 Dll

您將使用適用于 Unity 的 Azure 儲存體 (其本身會利用 .Net SDK for Azure)。 如需詳細資訊, 請遵循此[關於 Unity Azure 儲存體的連結](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。

Unity 中目前有一個已知問題, 需要在匯入後重新設定外掛程式。 解決錯誤之後, 將不再需要這些步驟 (本節中的 4-7)。

若要將 SDK 匯入您自己的專案, 請確定您已從 GitHub 下載最新的[**unitypackage。** ](https://aka.ms/azstorage-unitysdk) 然後, 執行下列動作:

1.  使用 [ 資產 **\> ] [匯入套件\> ] [自訂套件**] 功能表選項, 將 unitypackage 新增至 Unity。

2.  在彈出的 [匯**入 Unity 封裝**] 方塊中, 您可以選取 * **外掛程式* \> * 儲存體 * * * 底下的所有專案。  取消核取其他所有專案, 因為這個課程並不需要。

    ![匯入至封裝](images/AzureLabs-Lab8-61.png)

3.  按一下 [匯***入***] 按鈕, 將專案新增至您的專案。

4.  移至 [專案] 視圖中 [**外掛程式**] 底下的 [**儲存體**] 資料夾, 然後選取 [*僅*下列外掛程式]:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Windowsazure.storage 儲存體
    -   Newtonsoft.Json
    -   System.Spatial

![取消核取任何平臺](images/AzureLabs-Lab8-62.png)

5.  選取*這些特定外掛程式*後,**取消**核取**任何平臺**並**取消**核取 [ **WSAPlayer** ], 然後按一下 [套用]。

    ![套用平臺 dll](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > 我們會將這些特定外掛程式標示為僅在 Unity 編輯器中使用。 這是因為在從 Unity 匯出專案之後, 將會使用 [WSA] 資料夾中相同外掛程式的不同版本。

6.  在 [**儲存體**外掛程式] 資料夾中, 只選取:

    -   Microsoft. Data. 用戶端

        ![dll 的 set 不處理](images/AzureLabs-Lab8-64.png)

7.  勾選 [**平臺設定**] 底下的 [**不處理**] 方塊, 然後按一下 [套用]。 

    ![不套用任何處理](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > 因為 Unity assembly patcher 在處理此外掛程式時遇到困難, 所以我們將此外掛程式標示為「不處理」。 外掛程式仍然可以正常執行, 即使尚未處理也一樣。

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>第9章-在 Desktop Unity 專案中建立 TableToScene 類別

您現在需要建立包含程式碼的腳本, 以執行此應用程式。

您需要建立的第一個腳本是**TableToScene**, 它會負責:

-   讀取 Azure 資料表中的實體。
-   使用資料表資料, 判斷要產生的物件, 以及在哪個位置。

您需要建立的第二個腳本是**CloudScene**, 它會負責:

-   註冊滑鼠左鍵的事件, 讓使用者可以在場景周圍拖曳物件。
-   從這個 Unity 場景序列化物件資料, 並將其傳送至 Azure 函數應用程式。

若要建立此類別:

1.  以滑鼠右鍵按一下位於 [專案] 面板中的 [**資產**] 資料夾、[**建立** > **資料夾**]。 將資料夾命名為**Scripts**。

    ![建立腳本資料夾](images/AzureLabs-Lab8-66.png)

    ![建立腳本資料夾2](images/AzureLabs-Lab8-67.png)

2.  按兩下剛才建立的資料夾, 將它開啟。

3.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。 將腳本命名為**TableToScene**。

    ![新的 c](images/AzureLabs-Lab8-68.png)
    # 腳本![TableToScene 重新命名](images/AzureLabs-Lab8-69.png)

4.  按兩下腳本以在 Visual Studio 2017 中加以開啟。

5.  新增下列命名空間:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  在類別內, 插入下列變數:

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
    > 在 Azure 入口網站中, 將**accountName**值替換為您的 Azure 儲存體服務名稱, 並將**accountKey**值取代為 Azure 儲存體服務中找到的金鑰值 (請參閱下圖)。 
    >
    > ![提取帳戶金鑰](images/AzureLabs-Lab8-70.png)

7.  現在新增**Start ()** 和**喚醒 ()** 方法, 以初始化類別。

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

8.  在**TableToScene**類別中, 新增將從 Azure 資料表中抓取值的方法, 並使用它們在場景中產生適當的基本專案。

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

9.  在**TableToScene**類別之外, 您必須定義應用程式用來序列化和還原序列化**資料表實體**的類別。

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

10. 在回到 Unity 編輯器之前, 請務必先**儲存**。

11. 按一下 [階層] 面板中的**主要攝影機**, 使其屬性顯示在偵測**器**中。

12. 在 [**腳本**] 資料夾開啟的情況下, 選取腳本**TableToScene**檔案, 並將它拖曳到**主要相機**上。 結果應如下所示:

    ![將腳本新增至主要相機](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>第10章-在 Desktop Unity 專案中建立 CloudScene 類別

您需要建立的第二個腳本是**CloudScene**, 它會負責:

-   註冊滑鼠左鍵的事件, 讓使用者可以在場景周圍拖曳物件。

-   從這個 Unity 場景序列化物件資料, 並將其傳送至 Azure 函數應用程式。

若要建立第二個腳本:

1.  以滑鼠右鍵按一下 [**腳本**] 資料夾內部, 然後按一下 [**建立**]、[ **C\#腳本**]。 將腳本命名為**CloudScene**
    
    ![新的 c](images/AzureLabs-Lab8-72.png)
    # 腳本![重新命名 CloudScene](images/AzureLabs-Lab8-73.png)

2.  新增下列命名空間:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  插入下列變數:

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

4.  在 azure 入口網站中, 以 Azure 函數應用程式服務中找到的 Azure 函數應用程式 URL 取代**azureFunctionEndpoint**值, 如下圖所示:

    ![取得函式 URL](images/AzureLabs-Lab8-74.png)

5.  現在新增**Start ()** 和**喚醒 ()** 方法, 以初始化類別。

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

6.  在**Update ()** 方法中, 加入下列程式碼以偵測滑鼠輸入並拖曳, 這將會在場景中輪流移動 gameobject。 如果使用者已拖放物件, 它會將物件的名稱和座標傳遞給**UpdateCloudScene ()** 方法, 這會呼叫 azure 函數應用程式服務, 這會更新 azure 資料表並觸發通知。

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

7.  現在, 新增**UpdateCloudScene ()** 方法, 如下所示:

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

8.  儲存程式碼並返回 Unity

9.  將**CloudScene**腳本拖曳到**主要相機**上。 

    1. 按一下 [階層] 面板中的**主要攝影機**, 使其屬性顯示在偵測**器**中。 

    2. 在 [**腳本**] 資料夾開啟的情況下, 選取**CloudScene**腳本, 並將它拖曳到**主要相機**上。 結果應如下所示:

        > ![將雲端腳本拖曳到主要相機上](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>第11章-建立 UWP 的桌面專案

此專案的 Unity 區段所需的全部內容, 現在已完成。

1.  流覽至 [**組建設定**] ([  > 檔案**組建設定**])。

2.  從 [**組建設定**] 視窗中, 按一下 [**建立**]。

    ![組建專案](images/AzureLabs-Lab8-76.png)

3.  [檔案**瀏覽器**] 視窗隨即彈出, 提示您輸入要建立的位置。 建立新的資料夾 (按一下左上角的 [**新增資料夾**]), 並將其命名為**build**。

    ![組建的新資料夾](images/AzureLabs-Lab8-77.png)

    1.  開啟 [新增**組建**] 資料夾, 然後建立另一個資料夾 (使用 [**新增資料夾**] 一次), 並將它命名為 **\_NH Desktop\_App**。

        ![資料夾名稱 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  已選取**NH\_Desktop\_應用程式**。 按一下 [**選取資料夾**]。 專案需要幾分鐘的時間才能建立。

4.  在下列組建中, 會出現 [檔案**瀏覽器**], 顯示新專案的位置。 不過, 如果您需要先建立其他 Unity 專案, 請在接下來的幾個章節中, 不需要開啟它。


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>第12章-設定混合現實 Unity 專案

以下是使用混合現實進行開發的一般設定, 因此是適用于其他專案的絕佳範本。

1.  開啟**Unity** , 然後按一下 [**新增**]。

    ![新增 unity 專案](images/AzureLabs-Lab8-79.png)

2.  您現在必須提供 Unity 專案名稱, 並插入**UnityMRNotifHub**。 請確定 [專案類型] 設定為 [ **3d**]。 將位置設定為適合您的**位置**(請記住, 接近根目錄較佳)。 然後, 按一下 [**建立專案**]。

    ![名稱 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 [**編輯** > **喜好**設定], 然後在新視窗中, 流覽至 [**外部工具**]。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

    ![將外部編輯器設為 VS](images/AzureLabs-Lab8-81.png)

4.  接下來, 移  > 至 [檔案] [**組建設定**], 然後按一下 [**切換平臺**] 按鈕, 將平臺切換至**通用 Windows 平臺**。

    ![將平臺切換至 UWP](images/AzureLabs-Lab8-82.png)

5.  移至  > [檔案] [**組建設定**], 並確認:

    1.  **目標裝置**已設定為**任何裝置**

        > 若為 Microsoft HoloLens, 請將**目標裝置**設定為*HoloLens*。

    2.  **組建類型**設定為**D3D**

    3.  **SDK**已設定為**最新安裝**

    4.  **Visual Studio 版本**設定為 [**最新安裝**]

    5.  **組建和執行**設定為**本機電腦**

    6.  在這裡, 很值得儲存場景, 並將它加入組建。

        1. 選取 [新增] [**開啟場景**] 來執行此動作。 [儲存] 視窗隨即出現。

            ![新增開啟的場景](images/AzureLabs-Lab8-83.png)

        2. 為此建立新的資料夾, 並在任何未來的場景中選取 [**新增資料夾**] 按鈕, 以建立新的資料夾, 將其命名為**場景**。

            ![新增背景資料夾](images/AzureLabs-Lab8-84.png)

        3. 開啟新建立的 [**幕後**] 資料夾, 然後在 [**檔案名:** 文字] 欄位中, 輸入**NH\_MR\_場景**, 然後按 [**儲存**]。

            ![新場景-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  [**組建設定**] 中的其餘設定, 現在應該保留為預設值。

6.  在相同的視窗中, 按一下 [**玩家設定**] 按鈕, 這會在偵測**器**所在的空間中開啟相關的面板。    

    ![開啟播放 [設定]](images/AzureLabs-Lab8-86.png)

7.  在此面板中, 需要驗證幾項設定:

    1.  在 [**其他設定**] 索引標籤中:

        1.  **腳本執行階段版本**應該是**實驗**性 (.net 4.6 對等用法)
        2.  **腳本後端**應該是 ***.net***
        3.  **API 相容性層級**應該是 **.net 4.6**

            ![api 相容性](images/AzureLabs-Lab8-87.png)

    2.  在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]

        ![更新 xr 設定](images/AzureLabs-Lab8-88.png)        

    3.  在 [**發行設定**] 索引標籤的 [**功能**] 底下, 會執行:

        - **InternetClient**           

            ![勾選網際網路用戶端](images/AzureLabs-Lab8-89.png)

8.  回到 [**組建設定**] **, C# Unity 專案**已不再呈現灰色: 勾選 [this] 旁的核取方塊。

9.  完成這些變更後, 請關閉 [組建設定] 視窗。

10. 儲存場景和專案**檔** > **儲存場景/**  > 檔案**儲存專案**。

    > [!IMPORTANT]
    > 如果您想要略過*Unity 設定*此專案的元件 (混合現實應用程式), 並直接繼續程式碼, 您可以[下載這個 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), 將它匯入您的專案中做為[**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html), 然後繼續進行[第14章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)。 您仍然需要新增腳本元件。

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>第13章-匯入 Mixed Reality Unity 專案中的 Dll

您將使用適用于 Unity 程式庫的 Azure 儲存體 (使用適用于 Azure 的 .Net SDK)。 請遵循此[連結, 以瞭解如何搭配使用 Azure 儲存體與 Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。
Unity 中目前有一個已知問題, 需要在匯入後重新設定外掛程式。 解決錯誤之後, 將不再需要這些步驟 (本節中的 4-7)。

若要將 SDK 匯入您自己的專案, 請確定您已下載最新的[unitypackage](https://aka.ms/azstorage-unitysdk)。 然後, 執行下列動作:

1.  使用 [**資產** > ] [匯**入套件** > ] [**自訂套件**] 功能表選項, 將您從上述下載的 unitypackage 新增至 Unity。

2.  在彈出的 [匯**入 Unity 封裝**] 方塊中, 您可以選取 [**外掛程式** > ] [**儲存體**] 底下的所有專案。

    ![匯入套件](images/AzureLabs-Lab8-90.png)

3.  按一下 [匯**入**] 按鈕, 將專案新增至您的專案。

4.  移至 [專案] 視圖中 [**外掛程式**] 底下的 [**儲存體**] 資料夾, 然後選取 [*僅*下列外掛程式]:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Windowsazure.storage 儲存體
    -   Newtonsoft.Json
    -   System.Spatial

    ![選取外掛程式](images/AzureLabs-Lab8-91.png)

5.  選取*這些特定外掛程式*後,**取消**核取**任何平臺**並**取消**核取 [ **WSAPlayer** ], 然後按一下 [套用]。

    ![套用平臺變更](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > 您要將這些特定外掛程式標示為僅在 Unity 編輯器中使用。 這是因為在從 Unity 匯出專案之後, 將會使用 [WSA] 資料夾中相同外掛程式的不同版本。

6.  在 [**儲存體**外掛程式] 資料夾中, 只選取:

    -   Microsoft. Data. 用戶端

        ![選取資料服務用戶端](images/AzureLabs-Lab8-93.png)

7.  勾選 [**平臺設定**] 底下的 [**不處理**] 方塊, 然後按一下 [套用]。

    ![不要處理](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > 您正在將此外掛程式標示為「不要處理」, 因為 Unity assembly patcher 在處理此外掛程式時發生困難。 外掛程式仍然可以正常執行, 即使尚未處理也一樣。

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>第14章-在 mixed reality Unity 專案中建立 TableToScene 類別

**TableToScene**類別與第[9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)所述的相同。 遵循第[9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)所述的相同程式, 在 Mixed Reality Unity 專案中建立相同的類別。

當您完成這一章之後, 這兩個**Unity 專案**都會在主攝影機上設定此類別。

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>第15章-在 Mixed Reality Unity 專案中建立 NotificationReceiver 類別

您需要建立的第二個腳本是**NotificationReceiver**, 它會負責:

-   在初始化時向通知中樞註冊應用程式。
-   正在接聽來自通知中樞的通知。
-   從收到的通知還原序列化物件資料。
-   根據還原序列化的資料, 移動場景中的 Gameobject。

若要建立**NotificationReceiver**腳本:

1.  以滑鼠右鍵按一下 [**腳本**] 資料夾內部, 然後按一下 [**建立**]、[ **C\#腳本**]。 將腳本命名為**NotificationReceiver**。

    ![建立新的 c](images/AzureLabs-Lab8-95.png)
    # 腳本![名稱 NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  按兩下腳本加以開啟。

3.  新增下列命名空間:

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

4.  插入下列變數:

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

5.  將**hubName**值替換為您的通知中樞服務名稱, 並以 Azure 入口網站中 [存取原則] 索引標籤中的 [Azure 通知中樞服務] 中找到的端點值來取代**hubListenEndpoint**值 (請參閱下圖)。

    ![插入通知中樞原則端點](images/AzureLabs-Lab8-97.png)

6.  現在新增**Start ()** 和**喚醒 ()** 方法, 以初始化類別。

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

7.  新增**WaitForNotification**方法, 以允許應用程式接收來自通知中樞程式庫的通知, 而不衝突與主執行緒:

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

8.  下列方法 ( **InitNotificationAsync ())** 會在初始化時向通知中樞服務註冊應用程式。 程式碼已標記為批註, 因為 Unity 將無法建立專案。 當您在 Visual Studio 中匯入 Azure 訊息 Nuget 套件時, 將會移除批註。

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

9.  每次收到通知時, 將會觸發下列處理常式**Channel\_PushNotificationReceived ()** 。 它會將通知還原序列化, 這會是已移至桌面應用程式的 Azure 資料表實體, 然後將 MR 場景中對應的 GameObject 移到相同的位置。 
    
    > [!IMPORTANT]
    > 程式碼會標記為批註, 因為程式碼會參考 Azure 訊息程式庫, 而您將在 Visual Studio 中使用 Nuget 套件管理員建立 Unity 專案之後, 將會加入此程式庫。 因此, 除非已標記為批註, 否則 Unity 專案將無法建立。請注意, 如果您要建立專案, 然後想要回到 Unity, 就必須**重新批註**該程式碼。

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

10. 請記得儲存您的變更, 然後再回到 Unity 編輯器。

11. 按一下 [階層] 面板中的**主要攝影機**, 使其屬性顯示在偵測**器**中。

12. 在 [**腳本**] 資料夾開啟的情況下, 選取**NotificationReceiver**腳本, 並將它拖曳到**主要相機**上。 結果應如下所示:

    ![將通知接收器腳本拖曳至相機](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > 如果您是針對 Microsoft HoloLens 進行開發, 就必須更新**主要相機**的*相機*元件, 這樣才能:
    > - 清除旗標:單色
    > - 背景：黑色

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>第16章-建立 UWP 的混合現實專案

這一章與前一個專案的組建程式相同。 此專案的 Unity 區段所需的全部內容現在已經完成, 所以可以從 Unity 建立它。

1.  流覽至 [**組建設定**] ([   > 檔案**組建設定**])。

2.  從 [**組建設定**] 功能表中, 確定 [ **Unity C#專案**] 已核取 (這可讓您在組建之後編輯此專案中的腳本)。

3.  完成後, 按一下 [**建立**]。

    ![組建專案](images/AzureLabs-Lab8-99.png)

4.  [檔案**瀏覽器**] 視窗隨即彈出, 提示您輸入要建立的位置。 建立新的資料夾 (按一下左上角的 [**新增資料夾**]), 並將其命名為**build**。

    ![建立組建資料夾](images/AzureLabs-Lab8-100.png)

    1.  開啟 [新增**組建**] 資料夾, 然後建立另一個資料夾 (使用 [**新增資料夾**] 一次), 並將它命名為 **\_NH MR\_應用程式**。

        ![建立 NH_MR_Apps 資料夾](images/AzureLabs-Lab8-101.png)

    2.  已選取**NH\_MR\_應用程式**。 按一下 [**選取資料夾**]。 專案需要幾分鐘的時間才能建立。

5.  在組建之後, 會在新專案的位置開啟 [檔案**瀏覽器**] 視窗。



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>第17章-將 NuGet 套件新增至 UnityMRNotifHub 解決方案

> [!WARNING] 
> 請記住, 當您新增下列 NuGet 套件 (並取消下一[章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)中的程式碼) 後, 程式碼在 Unity 專案中重新開啟時, 將會出現錯誤。 如果您想要返回並繼續在 Unity 編輯器中編輯, 您將需要批註該 errosome 程式碼, 稍後當您回到 Visual Studio 之後, 就會再次取消批註。 

完成混合現實組建之後, 流覽至您所建立的混合現實專案, 然後按兩下該資料夾中的方案 (.sln) 檔案, 以使用 Visual Studio 2017 來開啟您的方案。
您現在將需要新增**windowsazure.storage 管理**的 NuGet 套件;這是用來接收來自通知中樞之通知的程式庫。

若要匯入 NuGet 套件:

1.  在 **方案總管**中, 以滑鼠右鍵按一下您的方案

2.  按一下 [**管理 NuGet 套件**]。

    ![開啟 nuget 管理員](images/AzureLabs-Lab8-102.png)

3.  選取 [***流覽***] 索引標籤, 並搜尋**windowsazure.storage**。

    ![尋找 windows azure 訊息封裝](images/AzureLabs-Lab8-103.png)

4.  選取結果 (如下所示), 然後在右邊的視窗中, 選取 [**專案**] 旁邊的核取方塊。 這會在 [**專案**] 旁的核取方塊中加上勾號, 以及 [**元件-CSharp**和**UnityMRNotifHub** ] 專案旁邊的核取方塊。

    ![勾選所有專案](images/AzureLabs-Lab8-104.png)

5.  一開始提供的版本可能與此專案**不**相容。 因此, 請按一下 [**版本**] 旁的下拉式功能表, 然後按一下 [**版本 0.1.7.9**], 再按一下 [**安裝**]。

6.  您現在已完成安裝 NuGet 套件。 尋找您在**NotificationReceiver**類別中所輸入的批註程式碼, 並移除留言。



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>第18章-編輯 UnityMRNotifHub 應用程式, NotificationReceiver 類別

新增**NuGet 套件**之後, 您必須將**NotificationReceiver**類別內的部分程式碼*取消*批註。

這包括：

1. 位於頂端的命名空間:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. **InitNotificationsAsync ()** 方法內的所有程式碼:

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
> 上述程式碼在其中有批註: 請確定您不會意外地*取消批註*該批註 (如果您有!, 程式碼不會進行編譯)。

3. 最後, **Channel_PushNotificationReceived**事件如下:

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

使用這些取消批註, 請確定您儲存, 然後繼續進行下一章。

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>第19章-將 mixed reality 專案與 Store 應用程式建立關聯

您現在需要將**mixed reality**專案與您在實驗室開始時所建立的 Store 應用程式建立關聯。

1.  開啟方案。

2.  在 [方案總管] 面板中, 以滑鼠右鍵按一下 UWP 應用程式專案、[移至] [**儲存**], 然後**將 [應用程式與存放區建立關聯**...]。

    ![開啟存放區關聯](images/AzureLabs-Lab8-105.png)

3.  隨即會出現一個新視窗 **, 稱為將您的應用程式與 Windows Store 建立關聯**。 按一下 [下一步] 。

    ![移至下一個畫面](images/AzureLabs-Lab8-106.png)

4.  它會載入與您已登入之帳戶相關聯的所有應用程式。 如果您未登入您的帳戶, 您可以在此頁面上**登入**。

5.  尋找您在本教學課程開始時所建立的**商店應用程式名稱**, 並加以選取。 然後按一下 [下一步] 。

    ![尋找並選取您的商店名稱](images/AzureLabs-Lab8-107.png)

6.  按一下 [**關聯**]。

    ![關聯應用程式](images/AzureLabs-Lab8-108.png)

7.  您的應用程式現在已與 Store 應用程式**相關聯**。 這是啟用通知的必要動作。

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>第20章-部署 UnityMRNotifHub 和 UnityDesktopNotifHub 應用程式

這一章可能會讓兩個人變得更容易, 因為這會包含兩個執行中的應用程式、一個在電腦桌面上執行, 另一個在您的沉浸式頭戴式裝置上執行。

沉浸式耳機應用程式正在等候接收場景的變更 (本機 Gameobject 的位置變更), 而桌面應用程式將會對其本機場景 (位置變更) 進行變更, 這將會與 MR 應用程式共用。 先部署 MR 應用程式, 接著使用桌面應用程式, 讓接收者可以開始接聽, 是合理的做法。

若要在本機電腦上部署**UnityMRNotifHub**應用程式:

1.  在**Visual Studio 2017**中開啟**UnityMRNotifHub**應用程式的方案檔。

2.  在**解決方案平臺**中, 選取 [ **x86]、[本機電腦**]。

3.  在 [**解決方案**設定] 中, 選取 [ **Debug**]。

    ![設定專案設定](images/AzureLabs-Lab8-109.png)

4.  移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的電腦。

5.  您的應用程式現在應該會出現在已安裝的應用程式清單中, 並準備好啟動。

若要在本機電腦上部署**UnityDesktopNotifHub**應用程式:

1.  在**Visual Studio 2017**中開啟**UnityDesktopNotifHub**應用程式的方案檔。

2.  在**解決方案平臺**中, 選取 [ **x86]、[本機電腦**]。

3.  在 [**解決方案**設定] 中, 選取 [ **Debug**]。

    ![設定專案設定](images/AzureLabs-Lab8-110.png)

4.  移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的電腦。

5.  您的應用程式現在應該會出現在已安裝的應用程式清單中, 並準備好啟動。

6.  啟動混合現實應用程式, 後面接著桌面應用程式。

在兩個應用程式執行的情況下, 在桌面場景中移動物件 (使用滑鼠左鍵)。 這些位置變更將會在本機進行序列化, 並傳送至函數應用程式服務。 函數應用程式服務接著會更新資料表以及通知中樞。 收到更新之後, 通知中樞會將更新的資料直接傳送給所有已註冊的應用程式 (在此案例中為沉浸式耳機應用程式), 然後將傳入的資料還原序列化, 並將新的位置資料套用至本機物件。在場景中移動它們。


## <a name="your-finished-your-azure-notification-hubs-application"></a>您已完成 Azure 通知中樞應用程式
 
恭喜, 您建立了一個混合現實應用程式來利用 Azure 通知中樞服務, 並允許應用程式之間的通訊。
 
![最終產品結束](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

您是否可以處理如何變更 Gameobject 的色彩, 並將該通知傳送給其他應用程式, 以查看場景？

### <a name="exercise-2"></a>練習2

您可以新增 Gameobject 至 MR 應用程式的移動, 並查看桌面應用程式中更新的場景嗎？
