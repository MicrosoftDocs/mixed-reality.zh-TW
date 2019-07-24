---
title: MR 和 Azure 304-臉部辨識
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合現實, 學術, unity, 教學課程, api, 臉部辨識, hololens, 沉浸, vr
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63554705"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。  因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊, 以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時, 使用這些教學課程的連結進行更新。

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR 和 Azure 304:臉部辨識

![完成此課程的結果](images/AzureLabs-Lab4-00.png)

在此課程中, 您將瞭解如何使用 Azure 認知服務, 搭配 Microsoft 臉部 API, 將臉部辨識功能新增至混合現實應用程式。

*Azure 臉部 API*是一項 Microsoft 服務, 可為開發人員提供最先進的臉部演算法, 全都在雲端中。 *臉部 API*有兩個主要功能: 使用屬性進行臉部偵測, 以及臉部辨識。 這可讓開發人員直接為臉部設定一組群組, 然後在稍後將查詢影像傳送到服務, 以判斷臉部所屬的人。 如需詳細資訊, 請造訪[Azure 臉部辨識頁面](https://azure.microsoft.com/services/cognitive-services/face/)。

完成此課程之後, 您將擁有一個混合現實 HoloLens 應用程式, 其將能夠執行下列作業:

1. 使用「點按**手勢**」來起始使用板載 HoloLens 攝影機的影像捕捉。 
2. 將已捕獲的映射傳送至*Azure 臉部 API*服務。
3. 接收*臉部 API*演算法的結果。
4. 使用簡單的使用者介面, 以顯示相符人員的名稱。

這將告訴您如何將臉部 API 服務的結果放入 Unity 型混合現實應用程式中。

在您的應用程式中, 您可以決定如何將結果與您的設計整合。 本課程的設計目的是要告訴您如何將 Azure 服務與您的 Unity 專案整合。 您的工作是使用您從這個課程取得的知識, 來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 304:臉部辨識</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然此課程主要著重于 HoloLens, 但您也可以將在本課程中學習到的內容套用至 Windows Mixed Reality 沉浸式 (VR) 耳機。 因為沉浸式 (VR) 耳機沒有可存取的相機, 所以您需要連接到電腦的外部相機。 隨著課程的遵循, 您將會看到支援沉浸式 (VR) 耳機時, 您可能需要採取的任何變更的附注。

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程是專為具備 Unity 和C#基本經驗的開發人員所設計。 也請注意, 本檔中的必要條件和書面指示, 代表在撰寫本文時已測試和驗證的內容 (5 月 2018)。 您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體, 但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容, 而不是如下所示。

在此課程中, 我們建議您採用下列硬體和軟體:

- [與 Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的開發電腦, 可用於沉浸式 (VR) 耳機開發
- [已啟用開發人員模式的 Windows 10 秋季建立者更新 (或更新版本)](install-the-tools.md)
- [最新的 Windows 10 SDK](install-the-tools.md)
- [Unity 2017。4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- 已啟用開發人員模式的[Windows Mixed Reality 沉浸 (VR) 耳機](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 連接到您電腦的相機 (適用于沉浸式耳機開發)
- 適用于 Azure 設定和臉部 API 抓取的網際網路存取

## <a name="before-you-start"></a>開始之前

1.  為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。
2.  設定並測試您的 HoloLens。 如果您需要支援設定 HoloLens,[請務必造訪 hololens 安裝程式一文](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  開始開發新的 HoloLens 應用程式時, 最好先執行校正和感應器微調 (有時候它有助於為每個使用者執行這些工作)。 

如需校正的說明, 請遵循此[HoloLens 校正文章的連結](calibration.md#hololens)。

如需感應器微調的說明, 請遵循此[HoloLens 感應器微調文章連結](sensor-tuning.md)。

## <a name="chapter-1---the-azure-portal"></a>第1章-Azure 入口網站

若要在 Azure 中使用*臉部 API*服務, 您將需要設定服務的實例, 讓應用程式可以使用。

1.  首先, 登入[Azure 入口網站](https://portal.azure.com)。 

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶, 您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。

2.  登入之後, 按一下左上角的 [**新增**], 然後搜尋 [*臉部 API*], 再按**enter**鍵。

    ![搜尋臉部 api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。

3.  新頁面將會提供*臉部 API*服務的描述。 在此提示的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。

    ![臉部 api 資訊](images/AzureLabs-Lab4-02.png)

4.  一旦您按下 **建立** :

    1. 為此服務實例插入您想要的名稱。

    2. 選取訂用帳戶。

    3. 選取適合您的定價層, 如果這是您第一次建立*臉部 API 服務*, 您應該可以使用免費層 (名為 F0)。

    4. 選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。 

        > 如果您想要深入瞭解 Azure 資源群組, 請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 您稍後使用的 UWP 應用程式 (**人員製作者**) 需要使用「美國西部」作為位置。

    6. 您也必須確認您已瞭解適用于此服務的條款及條件。

    7. 選取 **建立*。**

        ![建立臉部 api 服務](images/AzureLabs-Lab4-03.png)

5.  一旦您按下 **建立** 您必須建立服務，這可能需要一分鐘。

6.  建立服務實例之後, 入口網站中會出現通知。

    ![服務建立通知](images/AzureLabs-Lab4-04.png)

7.  按一下 [通知] 以探索新的服務實例。

    ![前往資源通知](images/AzureLabs-Lab4-05.png)

8.  當您準備好時, 請按一下通知中的 [**移至資源**] 按鈕, 以探索新的服務實例。

    ![存取臉部 api 金鑰](images/AzureLabs-Lab4-06.png)

9.  在本教學課程中, 您的應用程式必須呼叫您的服務, 這會透過使用您服務的訂用帳戶「金鑰」來完成。 從您的*臉部 API*服務的 [*快速入門*] 頁面, 第一個點是數位 1, 以*抓取您的金鑰。*

10. 在 [*服務*] 頁面上, 選取 [藍色**按鍵**] 超連結 (如果位於 [快速入門] 頁面), 或 [服務] 導覽功能表中的 [**金鑰**] 連結 (在左側, 以 [金鑰] 圖示表示), 以顯示您的金鑰。

    > [!NOTE] 
    > 請記下其中一個金鑰並加以保護, 因為您稍後將會用到它。

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>第2章-使用「人員製作者」 UWP 應用程式

請務必下載名為[Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)的預建 UWP 應用程式。 此應用程式不是本課程的最終產品, 只是可協助您建立 Azure 專案的工具, 之後的專案將會依賴此專案。

**Person Maker**可讓您建立與人員和人員群組相關聯的 Azure 專案。 應用程式會將所有需要的資訊, 以稍後可供 FaceAPI 使用的格式, 以辨識您已新增的人臉。 

> 重大**人員製作者**會使用一些基本的節流, 以協助確保您不會超過**免費訂**用帳戶層的每分鐘服務呼叫數。 當節流發生時, 頂端的綠色文字會變更為紅色, 並更新為「作用中」;如果是這種情況, 只需等待應用程式 (它會等到可以繼續存取臉部服務, 然後在您可以再次使用時更新為「主動」)。

此應用程式會使用*對 microsoft.projectoxford.face*的程式庫, 可讓您充分利用臉部 API。 此程式庫免費提供 NuGet 套件。 如需這項和類似的 Api 的詳細資訊, 請[務必造訪 api 參考文章](https://docs.microsoft.com/azure/cognitive-services/face/apireference)。

> [!NOTE] 
> 這些只是必要的步驟, 而如何執行這些動作的指示則是在檔的正下方。 **人員製作者**應用程式可讓您:
>
> - 建立*人員群組*, 這是由數個想要與之相關聯的人員所組成的群組。 使用您的 Azure 帳戶, 您可以裝載多個人員群組。
>
> - 建立*person*, 這是 person 群組的成員。 每個人都有一些相關聯的*臉部*影像。
>
> -  將*臉部影像*指派給*個人*, 以允許您的 Azure 臉部 API 服務依對應的*臉部*辨識*人員*。
>
> -  *訓練*您的*Azure 臉部 API 服務*。

請注意, 若要將此應用程式定型以辨識人員, 您將需要每個人的十 (10) 張左右相片, 以加入您的人員群組。 Windows 10 Cam 應用程式可協助您進行這些工作。 您必須確保每張相片都清楚明瞭 (避免模糊、遮蔽或太遠, 從主旨), 將相片設定為 jpg 或 png 檔案格式, 且影像檔案大小不會大於**4 MB**, 且不小於**1 KB**。

> [!NOTE]
> 如果您遵循本教學課程, 請勿使用您自己的臉部進行訓練, 如同當您將 HoloLens 放在時, 您無法自行查看。 使用同事或學生的臉部。

正在執行**人員製作者**:

1.  開啟 [ **PersonMaker** ] 資料夾, 然後按兩下 [ *PersonMaker] 方案*, 以*Visual Studio*開啟它。

2.  *PersonMaker 解決方案*開啟之後, 請確定:

    1. *解決方案*設定會設為**Debug**。

    2. *解決方案平臺*設定為**x86**

    3. *目標平臺*為 [**本機電腦**]。

    4.  您也可能需要*還原 Nuget 套件*(以滑鼠右鍵按一下*解決方案*, 然後選取 [**還原 nuget 套件**])。

3.  按一下 [*本機電腦*], 應用程式就會啟動。 請注意, 在較小的螢幕上, 可能不會顯示所有內容, 但您可以進一步向下滾動以進行觀看。

    ![人員製作者使用者介面](images/AzureLabs-Lab4-07.png)

4.  從 Azure 內的*臉部 API*服務, 插入您應該擁有的**azure 驗證金鑰**。

5.  插入

    1. 您想要指派給*Person 群組*的*識別碼*。 識別碼必須是小寫, 不含空格。 請記下此識別碼, 因為您稍後會在 Unity 專案中需要它。
    2. 您想要指派給*Person 群組*的*名稱*(可以有空格)。


6.  按 [**建立人員群組**] 按鈕。 確認訊息應該會出現在按鈕下方。

> [!NOTE]
> 如果您有「拒絕存取」錯誤, 請檢查您為 Azure 服務設定的位置。 如上所述, 此應用程式是專為「美國西部」所設計。

> [!IMPORTANT]
> 您會注意到, 您也可以按一下 [**提取已知群組**] 按鈕: 這適用于您已建立人員群組, 並想要使用它, 而不是建立新的群組。 請注意, 如果您按一下 [建立具有已知群組的*人員群組*], 這也會提取群組。

7.  插入您想要建立之*人員*的*名稱*。

    1. 按一下 [**建立人員**] 按鈕。

    2. 確認訊息應該會出現在按鈕下方。

    3. 如果您想要刪除先前建立的人員, 可以將名稱寫入文字方塊中, 然後按**Delete person**

8.  請確定您知道要新增至群組之人員的十 (10) 張相片的位置。

9.  按 [**建立] 和 [開啟資料夾**], 將 Windows Explorer 開啟至與該人員相關聯的資料夾。 在資料夾中新增十 (10) 個影像。 這些必須是*JPG*或*PNG*檔案格式。

10. 按一下 [**提交至 Azure**]。 計數器會顯示提交的狀態, 後面接著訊息完成時的訊息。

11. 當計數器完成並顯示確認訊息時, 按一下 [**定型**] 來訓練您的服務。

完成此程式之後, 您就可以開始移至 Unity。

## <a name="chapter-3---set-up-the-unity-project"></a>第3章-設定 Unity 專案

以下是使用混合現實進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本。

1.  開啟*Unity* , 然後按一下 [**新增**]。 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab4-08.png)

2.  現在您將需要提供 Unity 專案名稱。 插入**MR_FaceRecognition**。 請確定 [專案類型] 設定為 [ **3d**]。 將位置設定為適合您的**位置**(請記住, 接近根目錄較佳)。 然後, 按一下 [**建立專案**]。

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab4-09.png)

3.  在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 **編輯 > 喜好**設定, 然後在新視窗中, 流覽至 **外部工具**。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab4-10.png)

4.  接著, 移至 [檔案] **> [組建設定**], 然後按一下 [**切換平臺**] 按鈕, 將平臺切換至**通用 Windows 平臺**。

    ![[組建設定] 視窗, 將平臺切換至 UWP。](images/AzureLabs-Lab4-11.png)

5.  移至 [檔案] **> [組建設定**], 並確認:

    1. **目標裝置**設定為**HoloLens**

        > 針對沉浸式耳機, 將 [**目標裝置**] 設定為 [*任何裝置*]。

    2. **組建類型**設定為**D3D**
    3. **SDK**已設定為**最新安裝**
    4. **Visual Studio 版本**設定為 [**最新安裝**]
    5. **組建和執行**設定為**本機電腦**
    6. 儲存場景, 並將它加入至組建。 

        1. 選取 [新增] [**開啟場景**] 來執行此動作。 [儲存] 視窗隨即出現。

            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab4-12.png)

        2. 選取 [**新增資料夾**] 按鈕, 若要建立新的資料夾, 請將其命名為**場景**。

            ![建立新的腳本資料夾](images/AzureLabs-Lab4-13.png)

        3. 開啟新建立的 [**幕後**] 資料夾, 然後在 [**檔案名**: 文字] 欄位中輸入**FaceRecScene**, 然後按 [**儲存**]。

            ![為新場景指定名稱。](images/AzureLabs-Lab4-14.png)

    7. [*組建設定*] 中的其餘設定, 現在應該保留為預設值。

6. 在 [*組建設定*] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測*器*所在的空間中開啟相關的面板。 

    ![開啟 [播放] [設定]。](images/AzureLabs-Lab4-15.png)

7. 在此面板中, 需要驗證幾項設定:

    1. 在 [**其他設定**] 索引標籤中:

        1. **指令碼** **執行階段版本**應該**實驗性**（.NET 4.6 對等）。 變更此程式將會觸發需要重新開機編輯器的程式。
        2. **腳本後端**應該是 **.net**
        3. **API 相容性層級**應該是 **.net 4.6**

            ![更新其他設定。](images/AzureLabs-Lab4-16.png)
      
    2. 在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:

        - **InternetClient**
        - **網路**

            ![正在更新發行設定。](images/AzureLabs-Lab4-17.png)

    3. 在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]。

        ![更新 X R 設定。](images/AzureLabs-Lab4-18.png)

8.  回到 [*組建設定*] **, C# Unity 專案**不再呈現灰色;勾選 [] 旁的核取方塊。 
9.  關閉 [組建設定] 視窗。
10. 儲存場景和專案 (**file > 儲存場景/檔案 > 儲存專案**)。

## <a name="chapter-4---main-camera-setup"></a>第4章-主要相機設定

> [!IMPORTANT]
> 如果您想要略過此課程的*Unity 設定*元件, 並直接繼續執行程式碼, 您可以[下載 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), 並將它匯入到您的專案中做為[自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)。 請注意, 此套件也包含匯入*NEWTONSOFT DLL*, 其涵蓋于[第5章](#chapter-5--import-the-newtonsoft.json-library)。 匯入此匯入之後, 您可以從[第6章](#chapter-6-create-the-faceanalysis-class)繼續進行。

1.  在 [ 階層] 面板中, 選取**主要相機**。

2.  選取之後, 您就可以在 [偵測*器] 面板*中看到**主要攝影機**的所有元件。

    1. **相機物件**必須命名為「**主攝影機**」 (請注意拼寫的!)

    2. 主要相機**標記**必須設定為**MainCamera** (請注意拼寫!)

    3. 請確定**轉換位置**設定為**0, 0, 0**

    4. 將**清除旗標**設定為**純色**

    5. 將相機元件的**背景**色彩設定為**黑色, Alpha 0 (十六進位碼: #00000000)**

        ![設定相機元件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>第5章–匯入 Newtonsoft Json 程式庫

> [!IMPORTANT]
> 如果您已匯入[上一章](#chapter-4--main-camera-setup)中的 '. unitypackage ', 您可以略過這一章。

若要協助您還原序列化並將已接收和傳送至 Bot 服務的物件序列化, 您需要下載*Newtonsoft*程式庫。 您會在此[unity 封裝](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)檔案中找到已使用正確 unity 資料夾結構組織的相容版本。 

若要匯入程式庫:

1.  下載 Unity 套件。
2.  按一下 [**資產**]、[匯**入封裝**]、[**自訂套件**]。

    ![匯入 Newtonsoft Json 程式庫](images/AzureLabs-Lab4-20.png)

3.  尋找您已下載的 Unity 套件, 然後按一下 [開啟]。
4.  請確定套件的所有元件都已核取, 然後按一下 [匯**入**]。

    ![匯入 Newtonsoft Json 程式庫](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>第6章-建立 FaceAnalysis 類別

FaceAnalysis 類別的用途是裝載與您的 Azure 臉部辨識服務通訊所需的方法。 

- 當服務傳送了一個 capture 映射之後, 它就會分析它並識別中的臉部, 並判斷是否有任何人屬於已知的人員。 
- 如果找到已知的人員, 此類別就會將其名稱顯示為場景中的 UI 文字。

若要建立*FaceAnalysis*類別:

 1. 以滑鼠右鍵按一下位於 [專案] 面板中的 [*資產] 資料夾*, 然後按一下 [**建立** > **資料夾**]。 呼叫資料夾**腳本**。 

    ![建立 FaceAnalysis 類別。](images/AzureLabs-Lab4-22.png)

2.  按兩下剛才建立的資料夾, 將它開啟。 
3.  在資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立** >   **C#腳本**]。 呼叫腳本*FaceAnalysis*。 
4.  按兩下新的*FaceAnalysis*腳本, 以 Visual Studio 2017 開啟它。
5.  在*FaceAnalysis*類別上方輸入下列命名空間:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  您現在需要新增用於 deserialising 的所有物件。 這些物件必須加入*FaceAnalysis*腳本**之外**(下方大括弧底下)。 

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
7. 不會使用*Start ()* 和*Update ()* 方法, 因此請立即將其刪除。 

8.  在*FaceAnalysis*類別中, 新增下列變數:

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
    > 將**金鑰**和**personGroupId**取代為您的服務金鑰, 以及您先前建立之群組的識別碼。

9.  新增 initialises 類別的*喚醒 ()* 方法, 將*ImageCapture*類別新增至主要相機, 並呼叫標籤建立方法:

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

10. 加入*CreateLabel ()* 方法, 它會建立*標籤*物件以顯示分析結果:

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

11. 新增*DetectFacesFromImage ()* 和*GetImageAsByteArray ()* 方法。 前者會要求臉部辨識服務來偵測所提交影像中任何可能的臉部, 而後者則需要將已捕獲的影像轉換成位元組陣列:

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

12. 新增*IdentifyFaces ()* 方法, 它會要求*臉部辨識服務*, 以識別先前在提交的影像中偵測到的任何已知臉部。 要求會傳回識別之人員的識別碼, 但不會傳回名稱:

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

13. 新增*GetPerson ()* 方法。 藉由提供人員識別碼, 此方法接著會要求*臉部辨識服務*傳回已識別人員的名稱:

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

14.  請記得先**儲存**變更, 再回到 Unity 編輯器。
15.  在 Unity 編輯器中, 從 [專案] 面板的 [腳本] 資料夾中, 將 FaceAnalysis 腳本拖曳至 [階層]*面板*中的主要相機物件。 新的腳本元件將會新增至主要攝影機。 

![將 FaceAnalysis 放到主要相機上](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>第7章-建立 ImageCapture 類別

*ImageCapture*類別的目的是裝載與您的*Azure 臉部辨識服務*通訊所需的方法, 以分析您將捕捉的影像、識別其中的臉部, 以及判斷其是否屬於已知的人員。 如果找到已知的人員, 此類別就會將其名稱顯示為場景中的 UI 文字。

若要建立*ImageCapture*類別:
 
1.  以滑鼠右鍵按一下您先前建立的 [**腳本**] 資料夾, 然後按一下 [**建立**]、  **C# [腳本**]。 呼叫腳本*ImageCapture*。 
2.  按兩下新的*ImageCapture*腳本, 以 Visual Studio 2017 開啟它。
3.  在 ImageCapture 類別上方輸入下列命名空間:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  在*ImageCapture*類別中, 新增下列變數:

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

5.  新增初始化類別所需的*喚醒 ()* 和*Start ()* 方法, 並允許 HoloLens 捕獲使用者的手勢:

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

6.  新增*TapHandler ()* , 以在使用者執行點按手勢時呼叫:

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

7.  新增*ExecuteImageCaptureAndAnalysis ()* 方法, 這將會開始進行映射捕獲的進程:

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

8.  新增在完成相片 capture 程式時所呼叫的處理常式:

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

9. 請記得先**儲存**變更, 再回到 Unity 編輯器。

## <a name="chapter-8---building-the-solution"></a>第8章-建立解決方案

若要執行應用程式的徹底測試, 您必須將它側載到 HoloLens。

在您執行之前, 請確定:

-   第3章所述的所有設定都已正確設定。 
-   腳本*FaceAnalysis*會附加到主要相機物件。 
-   *FaceAnalysis*腳本內已設定**驗證金鑰**和**群組識別碼**。

答: 此時您已準備好建立解決方案。 建立解決方案之後, 您就可以開始部署您的應用程式。

若要開始建立程式:

1.  按一下 [檔案]、[儲存] 來儲存目前的場景。
2.  移至 [檔案]、[組建設定], 然後按一下 [新增開啟的場景]。
3.  請務必勾選 Unity C#專案。

    ![從 Visual Studio 部署解決方案。](images/AzureLabs-Lab4-24.png)

4.  按 [組建]。 這麼做之後, Unity 將會啟動 [檔案瀏覽器] 視窗, 您必須在其中建立並選取要建立應用程式的資料夾。 立即在 Unity 專案中建立該資料夾, 並呼叫它應用程式。 然後選取 [應用程式] 資料夾, 按 [選取資料夾]。 
5.  Unity 會開始建立您的專案, 並移至應用程式資料夾。 
6.  Unity 完成建立 (可能需要一些時間) 之後, 它會在組建的位置開啟 [檔案瀏覽器] 視窗。

    ![從 Visual Studio 部署解決方案。](images/AzureLabs-Lab4-25.png)

7.  開啟您的應用程式資料夾, 然後開啟 [新增專案] 方案 (如上所示, 也就是 MR_FaceRecognition)。


## <a name="chapter-9---deploying-your-application"></a>第9章-部署您的應用程式

若要在 HoloLens 上部署:

1.  您將需要 HoloLens 的 IP 位址 (用於遠端部署), 並確保 HoloLens 處於**開發人員模式**。 請這樣做：

    1. 在戴 HoloLens 的同時, 請開啟**設定**。
    2. 前往**Network & Internet > wi-fi > Advanced Options**
    3. 記下**IPv4**位址。
    4. 接下來, 流覽回到 [**設定**], 然後為**開發人員更新 & 的安全性 >** 
    5. 將開發人員模式設定為 On。

2.  流覽至新的 Unity 組建 (*應用程式*資料夾), 然後使用*Visual Studio*開啟方案檔。
3.  在 [解決方案設定] 中, 選取 [ **Debug**]。
4.  在解決方案平臺中, 選取 [ **x86**]、[**遠端電腦**]。 

    ![從 Visual Studio 部署解決方案。](images/AzureLabs-Lab4-26.png)
 
5.  移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的 HoloLens。
6.  您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中, 準備好啟動!

> [!NOTE]
> 若要部署到沉浸式耳機, 請將**解決方案平臺**設定為 [*本機電腦*], 然後將 [設定] 設為 [  *Debug*], 並將*x86*作為**平臺**。 然後, 使用 [**建立] 功能表**, 選取 [*部署解決方案*], 部署至本機電腦。 


## <a name="chapter-10---using-the-application"></a>第10章-使用應用程式

1.  戴上 HoloLens, 啟動應用程式。
2.  查看已向*臉部 API*註冊的人員。 請確認︰

    -  該人的臉部不太遠且清楚可見
    -  環境光源不會太暗

3.  使用 [點按手勢] 來捕捉人員的圖片。
4.  等待應用程式傳送分析要求並接收回應。
5.  如果已成功辨識該人員, 該人員的名稱將會顯示為 UI 文字。
6.  您可以每隔幾秒鐘, 使用點按手勢來重複捕捉程式。

## <a name="your-finished-azure-face-api-application"></a>您已完成的 Azure 臉部 API 應用程式

恭喜, 您建立了一個混合現實應用程式, 利用 Azure 臉部辨識服務來偵測影像中的臉部, 並識別任何已知的臉部。

![完成此課程的結果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

**Azure 臉部 API**的功能強大, 足以偵測單一影像中最多64人臉。 擴充應用程式, 讓它可以辨識兩個或三個臉部, 而不是在其他許多人之間。

### <a name="exercise-2"></a>練習2

**Azure 臉部 API**也能夠提供所有種類的屬性資訊。 將此整合到應用程式中。 相較于[表情 API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/), 這可能更為有趣。
