---
title: MR 和 Azure 305-函數和儲存體
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 儲存體和函式。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合現實, 學術, unity, 教學課程, api, 函式, 儲存體, hololens, 沉浸, vr
ms.openlocfilehash: 5f3d0c6990249bc32e4c0f55c72dd884c4c2214e
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694551"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。  因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊, 以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時, 使用這些教學課程的連結進行更新。

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR 和 Azure 305:函數和儲存體

![最終產品-開始](images/AzureLabs-Lab5-00.png)

在此課程中, 您將瞭解如何在混合的現實應用程式中, 建立和使用 Azure Functions, 並將資料儲存 Azure 儲存體資源。

*Azure Functions*是一項 Microsoft 服務, 可讓開發人員在 Azure 中執行一小段程式碼, 即「函式」。 這可讓您將工作委派給雲端, 而不是您的本機應用程式, 這可能有許多好處。 *Azure Functions*支援數種開發語言, 包括\#C、\#F、node.js、JAVA 和 PHP。 如需詳細資訊, 請造訪[Azure Functions 文章](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

*Azure 儲存體*是一種 Microsoft 雲端服務, 可讓開發人員儲存資料, 並將其視為高可用性、安全、耐用、可調整且重複。 這表示 Microsoft 會為您處理所有維護工作和嚴重問題。 如需詳細資訊, 請造訪[Azure 儲存體文章](https://docs.microsoft.com/azure/storage/common/storage-introduction)。

完成此課程之後, 您將擁有一個混合現實的沉浸式耳機應用程式, 其將能夠執行下列動作:

1.  允許使用者注視場景。
2.  當使用者在3D 「按鈕」上 gazes 時, 觸發物件的產生。
3.  衍生的物件將由 Azure 函數選擇。
4.  當產生每個物件時, 應用程式會將物件類型儲存在*Azure*檔案中, 該檔案位於*Azure 儲存體*。
5.  第二次載入時, 將會抓取*Azure*檔案資料, 並用來重新執行先前應用程式實例的產生動作。

在您的應用程式中, 您可以決定如何將結果與您的設計整合。 本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。 您的工作是使用您從這個課程取得的知識, 來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 和 Azure 305:函數和儲存體</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然此課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機, 但您也可以將您在本課程中學習到的內容套用至 Microsoft HoloLens。 隨著課程的遵循, 您會看到您可能需要用來支援 HoloLens 的任何變更的附注。

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
- 用來建立 Azure 資源的 Azure 帳戶訂閱
- 適用于 Azure 設定和資料抓取的網際網路存取

## <a name="before-you-start"></a>開始之前

為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。

## <a name="chapter-1---the-azure-portal"></a>第1章-Azure 入口網站

若要使用**Azure 儲存體服務**, 您將需要在 Azure 入口網站中建立並設定**儲存體帳戶**。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶, 您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。

2.  登入之後, 按一下左上角的 [**新增**], 並搜尋 [*儲存體帳戶*], 然後按一下**Enter 鍵**。

    ![azure 儲存體搜尋](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > 在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。

3.  [新增] 頁面將會提供*Azure 儲存體帳戶*服務的描述。 在此提示的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。

    ![建立服務](images/AzureLabs-Lab5-02.png)

4.  一旦您按下 **建立** :

    1.  插入您帳戶的*名稱*, 請注意此欄位只接受數位和小寫字母。

    2.  針對 [*部署模型*], 選取 [ **Resource manager**]。

    3.  針對 [*帳戶類型*], 選取 [**儲存體 (一般用途 v1)** ]。

    4.  判斷資源群組的*位置*(如果您要建立新的資源群組)。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于特定區域。

    5.  針對 [複寫], 選取 **[讀取權限-異地-多餘儲存體 (RA-GRS)** ]。

    6.  針對 [*效能*], 選取 [**標準**]。

    7.  將 [*需要安全傳輸*] 保留為 [**停用**]。

    8.  選取*訂*用帳戶。

    9. 選擇*資源群組*或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。 

        > 如果您想要深入瞭解 Azure 資源群組, 請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 您也必須確認您已瞭解適用于此服務的條款及條件。

    11. 選取 [建立]。

        ![輸入服務資訊](images/AzureLabs-Lab5-03.png)

5.  按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。

6.  建立服務實例之後, 入口網站中會出現通知。

    ![azure 入口網站中的新通知](images/AzureLabs-Lab5-04.png)

7.  按一下 [通知] 以探索新的服務實例。

    ![前往資源](images/AzureLabs-Lab5-05.png)

8.  按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。 您將會進入新的*儲存體帳戶*服務實例。

    ![存取金鑰](images/AzureLabs-Lab5-06.png)

9.  按一下 [*存取金鑰*], 以顯示此雲端服務的端點。 使用 [*記事本*] 或 [類似], 複製其中一個金鑰以供稍後使用。 此外, 請記下*連接字串*值, 因為它將用於*AzureServices*類別中, 稍後將會建立。

    ![複製連接字串](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>第2章-設定 Azure 函數

您現在將在 Azure 服務中撰寫**azure** 函式。

您可以使用**Azure**函式來執行您在程式碼中使用傳統函數所做的幾乎任何動作, 其差異在於具有認證可存取您 Azure 帳戶的任何應用程式都可以存取此函式。

若要建立 Azure 函數:

1.  從您的*Azure 入口網站*中, 按一下左上角的 [**新增**], 並搜尋*函數應用程式*, 然後按一下**Enter 鍵**。

    ![建立函數應用程式](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > 在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。

2.  新頁面將會提供*Azure 函數應用程式*服務的描述。 在此提示的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。

    ![函數應用程式資訊](images/AzureLabs-Lab5-09.png)

3.  一旦您按下 **建立** :

    1.  提供*應用程式名稱*。 這裡只能使用字母和數位 (大寫或小寫允許)。

    2.  選取您慣用的*訂*用帳戶。

    3. 選擇*資源群組*或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。 

        > 如果您想要深入瞭解 Azure 資源群組, 請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  針對此練習, 請選取 [ *Windows* ] 做為選擇的**作業系統**。

    5.  選取**主控方案**的 [取用*方案*]。

    6.  判斷資源群組的*位置*(如果您要建立新的資源群組)。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于特定區域。 為了達到最佳效能, 請選取與儲存體帳戶相同的區域。

    7.  針對 [*儲存體*], 選取 [**使用現有**的], 然後使用下拉式功能表尋找您先前建立的儲存體。

    8.  針對此練習, 請離開*Application Insights* 。

        ![輸入函數應用程式詳細資料](images/AzureLabs-Lab5-10.png)

4.  按一下 [建立] 按鈕。

5.  按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。

6.  建立服務實例之後, 入口網站中會出現通知。

    ![新的 azure 入口網站通知](images/AzureLabs-Lab5-11.png)

7.  按一下 [通知] 以探索新的服務實例。 

    ![前往資源函數應用程式](images/AzureLabs-Lab5-12.png)

8.  按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。 您將會進入新的*函數應用程式*服務實例。

9.  在 [*函數應用程式*] 儀表板上, 將滑鼠游標暫留在左側面板中的 [函式] 上方, 然後按一下 **+ (加號)** 符號。

    ![建立新函數](images/AzureLabs-Lab5-13.png)

10. 在下一個頁面上, 確定已選取 [ **Webhook + API** ], 並針對 *[選擇語言*] 選取 [ **CSharp**], 因為這會是本教學課程所使用的語言。 最後, 按一下 [**建立此函數**] 按鈕。

    ![選取 web 攔截 csharp](images/AzureLabs-Lab5-14.png)

11. 您應該會進入字碼頁 (.csx), 如果不是, 請在左側面板的 [函數] 清單中, 按一下新建立的函式。

    ![開啟新函數](images/AzureLabs-Lab5-15.png)

12. 將下列程式碼複製到您的函式。 呼叫時, 此函式只會傳回0到2之間的隨機整數。 不必擔心現有的程式碼, 您可以隨意貼到其頂端。

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

13. 選取 [儲存]。

14. 結果看起來應該如下圖所示。

15. 按一下 [**取得函數 URL** ], 並記下顯示的*端點*。 您必須將它插入您稍後將在本課程中建立的*AzureServices*類別。

    ![取得函式端點](images/AzureLabs-Lab5-16.png)

    ![取得函式端點](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>第3章-設定 Unity 專案

以下是使用混合現實進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本。

設定和測試混合現實的沉浸式耳機。

> [!NOTE]
> 在此課程中, 您將**不**需要有動作控制器。 如果您需要支援設定沉浸式耳機, 請[流覽混合現實設定一文](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  開啟 Unity, 然後按一下 [**新增**]。

    ![建立新的 unity 專案](images/AzureLabs-Lab5-17.png)

2.  現在您將需要提供 Unity 專案名稱。 插入**MR_Azure_Functions**。 請確定 [專案類型] 設定為 [ **3d**]。 將位置設定為適合您的*位置*(請記住, 接近根目錄較佳)。 然後, 按一下 [**建立專案**]。

    ![提供新的 unity 專案名稱](images/AzureLabs-Lab5-18.png)

3.  在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 [**編輯** > **喜好**設定], 然後在新視窗中, 流覽至 [**外部工具**]。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

    ![將 visual studio 設定為腳本編輯器](images/AzureLabs-Lab5-19.png)

4.  接下來, 移  > 至 [檔案] [**組建設定**], 然後按一下 [**切換平臺**] 按鈕, 將平臺切換至**通用 Windows 平臺**。

    ![將平臺切換至 uwp](images/AzureLabs-Lab5-20.png)

5.  移至  > [檔案] [**組建設定**], 並確認:

    1. [**目標裝置**] 已設定為 [**任何裝置**]。

        > 若為 Microsoft HoloLens, 請將**目標裝置**設定為*HoloLens*。

    2. **組建類型**設定為**D3D**

    3. **SDK**已設定為**最新安裝**

    4. **Visual Studio 版本**設定為 [**最新安裝**]

    5. **組建和執行**設定為**本機電腦**

    6. 儲存場景, 並將它加入至組建。

        1.  選取 [新增] [**開啟場景**] 來執行此動作。 [儲存] 視窗隨即出現。

            ![新增開啟的場景](images/AzureLabs-Lab5-21.png)

        2.  為此建立新的資料夾, 並在任何未來的場景中選取 [**新增資料夾**] 按鈕, 以建立新的資料夾, 將其命名為**場景**。

            ![建立場景資料夾](images/AzureLabs-Lab5-22.png)

        3.  開啟新建立的 [**幕後**] 資料夾, 然後在 [**檔案名:** 文字] 欄位中輸入**FunctionsScene**, 然後按 [**儲存**]。

            ![儲存函數場景](images/AzureLabs-Lab5-23.png)

6.  [**組建設定**] 中的其餘設定, 現在應該保留為預設值。

    ![儲存函數場景](images/AzureLabs-Lab5-24.png)

7.  在 [*組建設定*] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測*器*所在的空間中開啟相關的面板。

    ![inspector 中的 player 設定](images/AzureLabs-Lab5-25.png)

8.  在此面板中, 需要驗證幾項設定:

    1.  在 [**其他設定**] 索引標籤中:

        1.  **腳本執行階段版本**應該是**實驗**性 (.net 4.6 對等用法), 這將會觸發重新開機編輯器的需求。
        2.  **腳本後端**應該是 **.net**
        3.  **API 相容性層級**應該是 **.net 4.6**

    2.  在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:
        
        -  **InternetClient**

            ![設定功能](images/AzureLabs-Lab5-26.png)

    3.  在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]。

        ![設定 XR 設定](images/AzureLabs-Lab5-27.png)

9.  回到*組建設定* *Unity C#專案*已不再呈現灰色;勾選 [] 旁的核取方塊。

    ![計時 c # 專案](images/AzureLabs-Lab5-28.png)

10.  關閉 [組建設定] 視窗。

11. 儲存場景和專案 ([  > 檔案] [**儲存場景]/**  > [檔案] [**儲存專案**])。

## <a name="chapter-4---setup-main-camera"></a>第4章-設定主要攝影機

> [!IMPORTANT]
> 如果您想要略過*Unity 設定*本課程的元件, 並直接繼續執行程式碼, 您可以[下載 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), 並將它匯入到您的專案中做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)。 這也會包含下一章中的 Dll。 匯入之後, 請從[第7章](#chapter-7---create-the-azureservices-class)繼續進行。 

1.  在 [階層]*面板*中, 您會找到稱為「**主要攝影機**」的物件, 此物件代表您在應用程式內「內部」時的「前端」觀點。

2.  在您前方的 Unity 儀表板中, 選取**主要相機 GameObject**。 您會注意到, [*檢查面板*] (通常是在儀表板中找到) 會顯示該*GameObject*的各種元件, 並在頂端使用 [*轉換*], 然後按 [*相機*] 和一些其他元件。 您將需要重設主要攝影機的轉換, 使其正確定位。

3.  若要這麼做, 請選取相機的*轉換*元件旁的**齒輪**圖示, 然後選取 [**重設**]。

    ![重設轉換](images/AzureLabs-Lab5-29.png)

4.  然後更新 [**轉換**] 元件, 如下所示:

    |         |    轉換-位置   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | 轉換-旋轉 |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | 轉換-調整規模 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![設定相機轉換](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>第5章-設定 Unity 場景

1.  以滑鼠右鍵按一下 [階層]*面板*的空白區域, 然後在 [ **3d 物件**] 下加入**平面**。

    ![建立新平面](images/AzureLabs-Lab5-31.png)

2.  選取 [**平面**] 物件後, 變更 [*檢查] 面板*中的下列參數:

    |       | 轉換-位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | 轉換-調整規模 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![設定平面位置和尺規](images/AzureLabs-Lab5-32.png)

    ![平面的場景視圖](images/AzureLabs-Lab5-33.png)

3.  以滑鼠右鍵按一下 [階層]*面板*的空白區域, 然後在 [ **3d 物件**] 下加入**Cube**。

    1.  將 Cube 重新命名為**GazeButton** (已選取 cube, 請按 ' F2 ')。

    2.  變更 [偵測*器] 面板*中的下列參數:

        |       | 轉換-位置 |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![設定注視按鈕轉換](images/AzureLabs-Lab5-34.png)

        ![注視按鈕場景視圖](images/AzureLabs-Lab5-35.png)

    3.  按一下 [**標記**] 下拉按鈕, 然後按一下 [**新增標記**] 以開啟 [標籤 *& 圖層] 窗格*。

        ![加入新的標記](images/AzureLabs-Lab5-36.png)

        ![選取加號](images/AzureLabs-Lab5-37.png)

    4.  選取 [ **+ (加號)** ] 按鈕, 然後在 [*新增標記名稱*] 欄位中, 輸入**GazeButton**, 然後按 [**儲存**]。

        ![命名新標記](images/AzureLabs-Lab5-38.png)

    5.  按一下 [階層]*面板*中的 [ **GazeButton** ] 物件, 然後在 [偵測*器] 面板*中, 指派新建立的**GazeButton**標記。

        ![指派新標記的注視按鈕](images/AzureLabs-Lab5-39.png)

4.  以滑鼠右鍵按一下 [階層]*面板*中的 [ **GazeButton** ] 物件, 然後新增**空的 GameObject** (將新增為*子*物件)。

5.  選取新的物件, 並將它重新命名為**ShapeSpawnPoint**。

    1.  變更 [偵測*器] 面板*中的下列參數:

        |       | 轉換-位置 |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![更新圖形衍生點轉換](images/AzureLabs-Lab5-40.png)

        ![成形衍生點場景視圖](images/AzureLabs-Lab5-41.png)

6.  接下來, 您將建立**3D 文字**物件, 以提供 Azure 服務狀態的意見反應。

    再次以滑鼠右鍵按一下 [階層] 面板中的 [ **GazeButton** ], 並新增**3d 物件** >  **3d 文字**物件做為*子*系。

    ![建立新的3D 文字物件](images/AzureLabs-Lab5-42.png)

7.  將**3D 文字**物件重新命名為**AzureStatusText**。

8.  變更**AzureStatusText**物件轉換, 如下所示:

    |       | 轉換-位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0。6  |

    |       | 轉換-調整規模 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0。1   | 0。1               | 0。1   |


    > [!NOTE]
    > 如果它看起來不在中心, 請不要擔心, 因為當下列文本網格元件更新時, 將會修正此問題。

9.  變更**文本網格**元件以符合下列內容:

    ![設定文本網格元件](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > 此處選取的色彩是十六進位色彩:**000000FF**, 不過您可以自由選擇自己的程式, 只是要確保它可讀取。

10. 階層式面板的結構現在看起來應該像這樣:

    ![場景視圖中的文本網格](images/AzureLabs-Lab5-43b.png)

10. 您的場景現在看起來應該像這樣:

    ![場景視圖中的文本網格](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>第6章-匯入 Unity Azure 儲存體

您將使用適用于 Unity 的 Azure 儲存體 (其本身會利用 .Net SDK for Azure)。 您可以在[Unity 的 Azure 儲存體](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)中閱讀更多有關此專案的資訊。

Unity 中目前有一個已知問題, 需要在匯入後重新設定外掛程式。 解決錯誤之後, 將不再需要這些步驟 (本節中的 4-7)。

若要將 SDK 匯入您自己的專案, 請確定您已從 GitHub 下載最新的['. unitypackage '](https://aka.ms/azstorage-unitysdk)。 然後, 執行下列動作:

1.  使用 [**資產** > ] [匯**入套件** > ] [**自訂套件**] 功能表選項, 將**unitypackage**檔案新增至 Unity。

2.  在彈出的 [匯**入 Unity 封裝**] 方塊中, 您可以選取 [**外掛程式** > ] [**儲存體**] 底下的所有專案。 取消核取其他所有專案, 因為這個課程並不需要。

    ![匯入至封裝](images/AzureLabs-Lab5-45.png)

3.  按一下 [匯**入**] 按鈕, 將專案新增至您的專案。

4.  移至 [*外掛程式*] 底下的 [*儲存體*] 資料夾, 然後在 [專案] 視圖中選取下列外掛程式:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Windowsazure.storage 儲存體
    -   Newtonsoft.Json
    -   System.Spatial

        ![取消核取任何平臺](images/AzureLabs-Lab5-46.png)

5.  選取*這些特定外掛程式*後,**取消**核取*任何平臺*並**取消**核取 [ *WSAPlayer* ], 然後按一下 [套用]。

    ![套用平臺 dll](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > 我們會將這些特定外掛程式標示為僅在 Unity 編輯器中使用。 這是因為在從 Unity 匯出專案之後, 將會使用 [WSA] 資料夾中相同外掛程式的不同版本。

6.  在 [*儲存體*外掛程式] 資料夾中, 只選取:

    -   Microsoft. Data. 用戶端

        ![dll 的 set 不處理](images/AzureLabs-Lab5-48.png)

7.  勾選 [*平臺設定*] 底下的 [**不處理**] 方塊, 然後按一下 [套用]。

    ![不套用任何處理](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > 因為 Unity assembly patcher 在處理此外掛程式時發生困難, 所以我們將此外掛程式標示為「不處理」。 外掛程式仍然可以正常執行, 即使尚未處理也一樣。

## <a name="chapter-7---create-the-azureservices-class"></a>第7章-建立 AzureServices 類別

您即將建立的第一個類別是*AzureServices*類別。

*AzureServices*類別會負責:

-   儲存 Azure 帳號憑證。

-   呼叫您的 Azure App 函數。

-   上傳和下載 Azure 雲端儲存體中的資料檔案。

若要建立此類別:

1.  以滑鼠右鍵按一下 [*資產*] 資料夾, 位於 [專案] 面板中的 [**建立** > **資料夾**]。 將資料夾命名為**Scripts**。

    ![建立新資料夾](images/AzureLabs-Lab5-50.png)

    ![呼叫資料夾-腳本](images/AzureLabs-Lab5-51.png)

2.  按兩下剛才建立的資料夾, 將它開啟。

3.  以滑鼠右鍵按一下資料夾內的 [**建立** >   **C#腳本**]。 呼叫腳本*AzureServices*。

4.  按兩下新的*AzureServices*類別, 以*Visual Studio*開啟它。

5.  將下列命名空間新增至*AzureServices*的頂端:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  在*AzureServices*類別內新增下列 Inspector 欄位:

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

7.  然後, 在*AzureServices*類別內新增下列成員變數:

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
    > 請務必將*端點*和*連接字串*值取代為 azure 儲存體中的值 (可在 azure 入口網站中找到)

8.  現在必須加入*喚醒 ()* 和*Start ()* 方法的程式碼。 當類別初始化時, 將會呼叫這些方法:

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
    > 我們將在[未來的章節](#chapter-10---completing-the-azureservices-class)中填入*CallAzureFunctionForNextShape ()* 的程式碼。

9.  刪除*Update ()* 方法, 因為這個類別不會使用它。

10. 將您的變更儲存在 Visual Studio 中, 然後返回 Unity。

11. 按一下 [腳本] 資料夾中的 [ *AzureServices* ] 類別, 並將其拖曳至 [階層]*面板*中的主要相機物件。

12. 選取主要相機, 然後從**GazeButton**物件下方抓取**AzureStatusText**子物件, 並將它放在 [ **AzureStatusText**參考目標] 欄位的 [偵測*器*] 中, 以提供*對AzureServices*腳本。

    ![指派 azure 狀態文字參照目標](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>第8章-建立 ShapeFactory 類別

下一個要建立的腳本是*ShapeFactory*類別。 此類別的角色是在要求時建立新的圖形, 並保留在 [*圖形歷程記錄] 清單*中建立之圖形的歷程記錄。 每次建立圖形時, 會在*get-azureservice*類別中更新*圖形歷程記錄清單*, 然後儲存在您的*Azure 儲存體*中。 當應用程式啟動時, 如果在您的*Azure 儲存體*中找到已儲存的檔案, 則會抓取並重新執行*圖形歷程記錄清單*, 其中包含的**3d 文字**物件會提供所產生的圖形是來自儲存體, 或是新的。

若要建立此類別:

1.  移至您先前建立的**腳本**資料夾。

2.  以滑鼠右鍵按一下資料夾內的 [**建立** >   **C#腳本**]。 呼叫腳本*ShapeFactory*。

3.  按兩下新的*ShapeFactory*腳本, 以*Visual Studio*開啟它。

4.  請確定*ShapeFactory*類別包含下列命名空間:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  將下方顯示的變數新增至*ShapeFactory*類別, 並將*Start ()* 和*喚醒 ()* 函式取代為下列這些函式:

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

6.  *CreateShape ()* 方法會根據所提供的*整數*參數, 產生基本圖形。 布林值參數是用來指定目前建立的圖形是來自儲存體還是新的。 在您的*ShapeFactory*類別中, 將下列程式碼放在先前的方法下方:

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

7.  請務必先將您的變更儲存在 Visual Studio 中, 然後再返回 Unity。

8.  回到 Unity 編輯器中, 按一下 [**腳本**] 資料夾中的 [ *ShapeFactory* ] 類別, 並將其拖曳至 [階層]*面板*中的**主要相機**物件。

9. 選取主攝影機之後, 您會注意到*ShapeFactory*腳本元件缺少產生*點*參考。 若要修正此問題, 請將**ShapeSpawnPoint**物件從 [階層]*面板*拖曳至 [**衍生點**參考目標]。

    ![設定圖形 factory 參考目標](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>第9章-建立注視課程

您需要建立的最後一個腳本是*注視*類別。

此類別負責建立將從主要相機向前投射的**Raycast** , 以偵測使用者正在查看的物件。 在此情況下, Raycast 將需要識別使用者是否正在查看場景中的**GazeButton**物件, 並觸發行為。

若要建立此類別:

1.  移至您先前建立的**腳本**資料夾。

2.  以滑鼠右鍵按一下 [專案] 面板中的 [**建立** >   **C#腳本**]。 呼叫腳本*注視*。

3.  按兩下新的*注視*腳本, 以 Visual Studio 加以開啟 *。*

4.  請確定腳本頂端包含下列命名空間:

    ```csharp
        using UnityEngine;
    ```

5.  然後在*注視*類別內新增下列變數:

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
> 其中有些變數可以在*編輯器*中編輯。

6.  現在必須加入*喚醒 ()* 和*Start ()* 方法的程式碼。

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

7.  新增下列程式碼, 這會在 start 建立 cursor 物件, 以及使用*Update ()* 方法來執行 Raycast 方法, 並在其中切換 GazeEnabled 布林值:

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

8. 接下來, 新增*UpdateRaycast ()* 方法, 它會投影 Raycast 並偵測點擊的目標。

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

9. 最後, 加入*ResetFocusedObject ()* 方法, 這會切換 GazeButton 物件目前的色彩, 指出是否正在建立新的圖形。

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

10.  請先儲存 Visual Studio 中的變更, 再返回 Unity。

11.  按一下 [腳本] 資料夾中的 [*注視*] 類別, 並將其拖曳至 [階層]*面板*中的**主要相機**物件。

## <a name="chapter-10---completing-the-azureservices-class"></a>第10章-完成 AzureServices 類別

與其他指令碼中的地方，它現在便能夠*完整* *所需的 AzureServices*類別。 這將透過下列途徑達成:

1.  新增名為*CreateCloudIdentityAsync ()* 的新方法, 以設定與 Azure 通訊所需的驗證變數。

    > 這個方法也會檢查先前儲存的檔案是否存在, 其中包含圖形清單。
    >
    > **如果找到**檔案, 就會根據圖形的模式 (儲存在**Azure 儲存體**檔案中), 停用使用者*注視*並觸發圖形建立。 使用者可以看到這種情況, 因為**文字網格**會提供顯示「儲存」或「新」, 視圖形的來源而定。
    >
    > **如果找不到任何**檔案, 它會啟用*注視*, 讓使用者在查看場景中的**GazeButton**物件時建立圖形。

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

2.  下一個程式碼片段位於*Start ()* 方法內;其中會對*CreateCloudIdentityAsync ()* 方法進行呼叫。 請隨意複製您目前的*Start ()* 方法, 如下所示:

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

3.  填入*CallAzureFunctionForNextShape ()* 方法的程式碼。 您將使用先前建立的*Azure 函數應用程式*來要求圖形索引。 一旦收到新的圖形, 這個方法就會將圖形傳送至*ShapeFactory*類別, 以便在場景中建立新的圖形。 使用下列程式碼來完成 CallAzureFunctionForNextShape 的主體 *()* 。

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

4.  藉由串連儲存在 [圖形歷程記錄] 清單中的整數, 並將它儲存在您的*Azure 儲存體*檔案中, 來新增方法來建立字串。

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

5.  新增方法來抓取儲存在*Azure 儲存體*檔案中的檔案中的文字, 並將它還原序列化為清單。

6.  完成此程式之後, 方法會重新啟用注視, 讓使用者可以將更多圖形加入場景中。

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

7.  請先儲存 Visual Studio 中的變更, 再返回 Unity。

## <a name="chapter-11---build-the-uwp-solution"></a>第11章-建立 UWP 解決方案

若要開始建立程式:

1.  移至  > [檔案] [**組建設定**]。

    ![建立應用程式](images/AzureLabs-Lab5-54.png)

2.  按一下 [建置] 。 Unity 將會啟動 [檔案*瀏覽器*] 視窗, 您必須在其中建立並選取要建立應用程式的資料夾。 立即建立該資料夾, 並將它命名為*應用程式*。 然後選取 [*應用程式*] 資料夾, 按 [**選取資料夾**]。

3.  Unity 會開始將您的專案建立至*應用程式*資料夾。

4.  Unity 完成建立之後 (可能需要一些時間), 它會在組建的位置開啟 [檔案*瀏覽器*] 視窗 (請檢查您的工作列, 因為它不一定會出現在視窗的上方, 但會通知您加入新的視窗)。

## <a name="chapter-12---deploying-your-application"></a>第12章-部署您的應用程式

若要部署您的應用程式:

1.  流覽至在[上一章](#chapter-11---build-the-uwp-solution)中建立的*應用程式*資料夾。 您會看到一個檔案, 其中包含您的應用程式名稱, 副檔名為 ' .sln ', 您應該按兩下此檔案, 以便在*Visual Studio*中開啟它。

2.  在**解決方案平臺**中, 選取 [ **x86]、[本機電腦**]。

3.  在 [**解決方案**設定] 中, 選取 [ **Debug**]。

    > 針對 Microsoft HoloLens, 您可能會發現將此設定為 [*遠端電腦*] 比較容易, 因此您不會行動網卡到電腦。 不過, 您也必須執行下列動作:
    > - 知道您的 HoloLens 的**IP 位址**, 您可以在 [**設定** > ] [ **&**  > 網路] [**wi-fi**  > ] [**Advanced] 選項**中找到, IPv4 是您應該使用的位址。 
    > - 請確定**開發人員模式**已**開啟**;在 [**設定** > ] [更新] [**為開發人員** **& 安全性** > ] 中找到。

    ![部署解決方案](images/AzureLabs-Lab5-55.png)

4.  移至 [**建立**] 功能表, 然後按一下 [**部署方案**], 將應用程式側載至您的電腦。

5.  您的應用程式現在應該會出現在已安裝的應用程式清單中, 準備好啟動並測試!

## <a name="your-finished-azure-functions-and-storage-application"></a>您完成的 Azure Functions 和儲存體應用程式

恭喜, 您建立了一個混合現實應用程式, 利用 Azure Functions 和 Azure 儲存體服務。 您的應用程式可以在儲存的資料上繪製, 並根據該資料提供動作。

![最終產品結束](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

建立第二個產生點, 並記錄建立物件的衍生點。 當您載入資料檔案時, 會從原先建立的位置重新執行所產生的圖形。

### <a name="exercise-2"></a>練習2

建立重新開機應用程式的方法, 而不是每次都必須重新開啟它。 **載入場景**是很好的起點。 這麼做之後, 請建立一個方法來清除*Azure 儲存體*中的已儲存清單, 讓您可以輕鬆地從應用程式重設它。 
