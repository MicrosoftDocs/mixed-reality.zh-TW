---
title: MR 和 Azure 301-語言翻譯
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 翻譯工具文字 API。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合現實, 學術, unity, 教學課程, api, 翻譯工具文字, hololens, 沉浸, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63553980"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。  因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊, 以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。  此通知會在張貼時, 使用這些教學課程的連結進行更新。

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR 和 Azure 301:語言翻譯

在此課程中, 您將瞭解如何使用 Azure 認知服務搭配翻譯工具文字 API, 將翻譯功能新增至混合現實應用程式。

![最終產品](images/AzureLabs-Lab1-00.png)

翻譯工具文字 API 是一項轉譯服務, 以近乎即時的方式運作。 此服務是以雲端為基礎, 而使用 REST API 呼叫, 應用程式可以使用類神經機器翻譯技術, 將文字翻譯成另一種語言。 如需詳細資訊, 請造訪[Azure 翻譯工具文字 API 頁面](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。

完成本課程之後, 您將會有一個混合現實應用程式, 可以執行下列作業:

1.  使用者會說話連接到沉浸式 (VR) 耳機 (或 HoloLens 的內建麥克風) 的麥克風。
2.  應用程式將會捕捉聽寫, 並將其傳送至 Azure 翻譯工具文字 API。
3.  轉譯結果會顯示在 Unity 場景的簡單 UI 群組中。

本課程將告訴您如何將 Translator 服務的結果放入 Unity 型範例應用程式中。 您必須將這些概念套用到您可能正在建立的自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 301:語言翻譯</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- 一組具有內建麥克風的耳機 (如果耳機沒有內建的 mic 和喇叭)
- Azure 設定和翻譯抓取的網際網路存取

## <a name="before-you-start"></a>開始之前

- 為避免在建立此專案時發生問題, 強烈建議您在根或接近根資料夾中建立本教學課程中所述的專案 (長資料夾路徑可能會在組建階段造成問題)。
- 本教學課程中的程式碼可讓您從連接到電腦的預設麥克風裝置錄製。 請確定預設的麥克風裝置已設定為您打算用來捕捉語音的裝置。
- 若要允許您的電腦啟用聽寫, 請移至 [**設定] > [隱私權 > 語音]、** [筆跡] & 輸入, 然後選取 [**開啟語音服務] 和 [輸入建議**] 按鈕。
- 如果您使用連接到 (或內建于) 耳機的麥克風和耳機, 請確定已在 設定 中開啟 當我戴耳機、切換到耳機 mic 選項, **> Mixed reality > 音訊和語音**。

   ![Mixed reality 設定](images/AzureLabs-Lab1-00-5.png)

   ![麥克風設定](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> 請注意, 如果您是針對此實驗室的沉浸式耳機進行開發, 您可能會遇到音訊輸出裝置問題。 這是因為 Unity 的問題 (在較新版本的 Unity (Unity 2018.2) 中已修正)。 此問題會防止 Unity 在執行時間變更預設音訊輸出裝置。 因應措施是, 確定您已完成上述步驟, 然後關閉並重新開啟編輯器 (當此問題呈現其本身時)。

## <a name="chapter-1--the-azure-portal"></a>第1章– Azure 入口網站

若要使用 Azure Translator API, 您必須設定服務的實例, 讓應用程式可以使用。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶, 您將需要建立一個。 如果您是在課堂或實驗室的情況下進行本教學課程, 請洽詢您的講師或其中一個 proctors, 以協助設定您的新帳戶。

2.  登入之後, 按一下左上角的 [**新增**], 並搜尋「翻譯工具文字 API」。 選取**Enter 鍵**。

    ![新增資源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 在較新的入口網站中,**新**的「可能」已取代為「**建立資源**」。

3.  新的頁面會提供*翻譯工具文字 API*服務的描述。 在此頁面的左下方, 選取 [**建立**] 按鈕, 以建立與此服務的關聯。

    ![建立翻譯工具文字 API 服務](images/AzureLabs-Lab1-03.png)

4.  一旦您按下 **建立** :

    1. 為此服務實例插入您想要的**名稱**。
    2. 選取適當的**訂**用帳戶。
    3. 選取適合您的**定價層**, 如果這是您第一次建立*翻譯工具文字服務*, 則應該可以使用免費層 (名為 F0)。
    4. 選擇**資源群組**或建立一個新的。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您將與單一專案相關聯的所有 Azure 服務 (例如這些實驗室) 都保留在通用資源群組底下)。

        > 如果您想要深入瞭解 Azure 資源群組, 請[造訪資源群組一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 判斷資源群組的**位置**(如果您要建立新的資源群組)。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于特定區域。
    6. 您也必須確認您已瞭解適用于此服務的條款及條件。
    7. 選取 [建立]。

        ![選取 [建立] 按鈕。](images/AzureLabs-Lab1-04.png)

5.  按一下 [**建立**] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。
6.  建立服務實例之後, 入口網站中會出現通知。 

    ![Azure 服務建立通知](images/AzureLabs-Lab1-05.png)

7.  按一下通知以探索新的服務實例。 

    ![移至 [資源] 快顯視窗。](images/AzureLabs-Lab1-06.png)

8.  按一下通知中的 [**移至資源**] 按鈕, 探索新的服務實例。 您將會進入新的翻譯工具文字 API 服務實例。 

    ![翻譯工具文字 API 服務頁面](images/AzureLabs-Lab1-07.png)

9.  在本教學課程中, 您的應用程式將需要呼叫您的服務, 這會透過使用您服務的訂用帳戶金鑰來完成。 
10. 從*翻譯工具文字*服務的 [*快速入門*] 頁面中, 流覽至第一個步驟,*抓取您的金鑰*, 然後按一下 [**金鑰**] (您也可以按一下位於 [服務] 導覽功能表中的藍色超連結鍵來達成此目的,以按鍵圖示表示)。 這會顯示您的服務*金鑰*。
11. 複製其中一個顯示的金鑰, 因為您稍後會在專案中用到。 

## <a name="chapter-2--set-up-the-unity-project"></a>第2章–設定 Unity 專案

設定和測試混合現實的沉浸式耳機。

> [!NOTE]
> 在此課程中, 您將不需要有動作控制器。 如果您需要支援設定沉浸式耳機, 請[遵循下列步驟](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

以下是使用混合現實進行開發的一般設定, 因此, 這是適用于其他專案的絕佳範本:

1.  開啟*Unity* , 然後按一下 [**新增**]。 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab1-08.png)

2.  現在您將需要提供 Unity 專案名稱。 插入**MR_Translation**。 請確定 [專案類型] 設定為 [ **3d**]。 將位置設定為適合您的*位置*(請記住, 接近根目錄較佳)。 然後, 按一下 [**建立專案**]。

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab1-09.png)

3.  在 Unity 開啟的情況下, 值得檢查預設**腳本編輯器**是否設定為**Visual Studio**。 移至 **編輯 > 喜好**設定, 然後在新視窗中, 流覽至 **外部工具**。 將**外部腳本編輯器**變更為**Visual Studio 2017**。 關閉 [**喜好**設定] 視窗。

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab1-10.png)

4.  接著, 移至 [檔案] **> [組建設定**], 然後按一下 [**切換平臺**] 按鈕, 將平臺切換至**通用 Windows 平臺**。

    ![[組建設定] 視窗, 將平臺切換至 UWP。](images/AzureLabs-Lab1-11.png)

5.  移至 [檔案] **> [組建設定**], 並確認:

    1. [**目標裝置**] 已設定為 [**任何裝置**]。

        > 若為 Microsoft HoloLens, 請將**目標裝置**設定為*HoloLens*。

    2. **組建類型**設定為**D3D**
    3. **SDK**已設定為**最新安裝**
    4. **Visual Studio 版本**設定為 [**最新安裝**]
    5. **組建和執行**設定為**本機電腦**
    6. 儲存場景, 並將它加入至組建。

        1. 選取 [新增] [**開啟場景**] 來執行此動作。 [儲存] 視窗隨即出現。

            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab1-12.png)

        2. 為此建立新的資料夾, 並在任何未來的場景中選取 [**新增資料夾**] 按鈕, 以建立新的資料夾, 將其命名為**場景**。

            ![建立新的腳本資料夾](images/AzureLabs-Lab1-13.png)

        3. 開啟新建立的 [**幕後**] 資料夾, 然後在 [*檔案名*: 文字] 欄位中輸入**MR_TranslationScene**, 然後按 [**儲存**]。

            ![為新場景指定名稱。](images/AzureLabs-Lab1-14.png)

            > 請注意, 您必須將 Unity 場景儲存在 [*資產*] 資料夾中, 因為它們必須與 Unity 專案相關聯。 建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。

    7. [*組建設定*] 中的其餘設定, 現在應該保留為預設值。

6. 在 [*組建設定*] 視窗中, 按一下 [ **Player 設定**] 按鈕, 這會在偵測*器*所在的空間中開啟相關的面板。 

    ![開啟 [播放] [設定]。](images/AzureLabs-Lab1-15.png)

7. 在此面板中, 需要驗證幾項設定:

    1. 在 [**其他設定**] 索引標籤中:

        1. **腳本執行階段版本**應為**穩定**(.net 3.5 對等)。
        2. **腳本後端**應該是 **.net**
        3. **API 相容性層級**應該是 **.net 4.6**

            ![更新其他設定。](images/AzureLabs-Lab1-16.png)
      
    2. 在 [**發行設定**] 索引標籤的 [**功能**] 底下, 檢查:

        1. **InternetClient**
        2. **十分**

            ![正在更新發行設定。](images/AzureLabs-Lab1-17.png)

    3. 在面板中, 于 [ **XR 設定**] (在 [**發佈設定**] 下方找到) 中, 支援 [勾選**虛擬實境**], 並確定已新增 [ **Windows Mixed Reality SDK** ]。

        ![更新 X R 設定。](images/AzureLabs-Lab1-18.png)

8.  回到 [**組建設定**] *, C# Unity 專案*不再呈現灰色;勾選 [] 旁的核取方塊。 
9.  關閉 [組建設定] 視窗。
10. 儲存場景和專案 (**file > 儲存場景/檔案 > 儲存專案**)。

## <a name="chapter-3--main-camera-setup"></a>第3章–主要攝影機設定

> [!IMPORTANT]
> 如果您想要略過此課程的*Unity 設定*元件, 並繼續直接進入程式碼, 您可以[下載這個 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), 將它匯入到您的專案中做為[*自訂套件*](https://docs.unity3d.com/Manual/AssetPackages.html), 然後繼續進行[第5章](#chapter-5--create-the-results-class)。 您仍然需要建立 Unity 專案。

1.  在 [階層]*面板*中, 您會找到稱為「**主要攝影機**」的物件, 此物件代表您在應用程式內「內部」時的「前端」觀點。
2.  在您前方的 Unity 儀表板中, 選取**主要相機 GameObject**。 您會注意到, [*檢查面板*] (通常是在儀表板中找到) 會顯示該*GameObject*的各種元件, 並在頂端使用 [*轉換*], 然後按 [*相機*] 和一些其他元件。 您將需要重設主要攝影機的轉換, 使其正確定位。
3.  若要這樣做, 請選取相機*轉換*元件旁的**齒輪**圖示, 然後選取 [**重設**]。 

    ![重設主要相機轉換。](images/AzureLabs-Lab1-19.png)
 
4.  接著,*轉換*元件看起來應該像這樣:

    1. *位置*設定為**0, 0, 0**
    2. *旋轉*設定為**0, 0, 0**
    3. 和*Scale*設定為**1, 1, 1**

        ![相機的轉換資訊](images/AzureLabs-Lab1-20.png)

5.  接下來, 選取**主要相機**物件, 請參閱位於 [偵測*器] 面板*最下方的 [**新增元件**] 按鈕。 
6.  選取該按鈕, 並搜尋 (在搜尋欄位中輸入*音訊來源*或流覽區段), 以取得名為 [**音訊來源**] 的元件 (如下所示), 然後選取它 (在其上按 enter 鍵也適用)。
7.  *音訊來源*元件將會新增至**主要攝影機**, 如下所示。

    ![新增音訊來源元件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > 針對 Microsoft HoloLens, 您也必須變更下列各項, 這是您**主要攝影機**上**相機**元件的一部分:
    > - **清除旗標:** 單色。
    > - **背景**' 黑色, Alpha 0 ' –十六進位色彩: #00000000。

## <a name="chapter-4--setup-debug-canvas"></a>第4章–設定偵錯工具畫布

若要顯示翻譯的輸入和輸出, 必須建立基本 UI。 在此課程中, 您將建立畫布 UI 物件, 其中包含數個「文字」物件來顯示資料。

1.  以滑鼠右鍵按一下 [階層]*面板*的空白區域, 然後在 [ **UI**] 下加入**畫布**。

    ![加入新的畫布 UI 物件。](images/AzureLabs-Lab1-22.png)

2.  選取畫布物件後, 在 [偵測*器] 面板*中 (在 [畫布] 元件中), 將 [轉譯**模式]** 變更為 [**世界空間**]。 
3.  接下來, 變更偵測*器面板矩形轉換*中的下列參數:

    1. *POS*    X 0 Y 0 Z 40 -  
    2. *寬度*-500
    3. *高度*-300
    4. *尺規*    X 0.13 Y 0.13 Z 0.13 - 

        ![更新畫布的矩形轉換。](images/AzureLabs-Lab1-23.png)
 
4.  以滑鼠右鍵按一下 [階層]*面板*中的**畫布**, 在 [ **UI**] 底下, 然後加入**面板**。 此**面板**會提供您將在場景中顯示之文字的背景。
5.  以滑鼠右鍵按一下 [階層]*面板*中的**面板**, 在 [ **UI**] 底下, 然後新增 [**文字] 物件**。 重複相同的程式, 直到您建立了四個 UI 文字物件總計 (提示: 如果您選取了第一個 ' Text ' 物件, 只要按 **' Ctrl ' + d '** , 即可複製它, 直到總共有四個)。 
6.  針對每個**文字物件**, 請選取它, 並使用下表來設定 [偵測*器] 面板*中的參數。

    1. 針對*矩形轉換*元件:

        | 名稱                   | 轉換-*位置*             | 寬度      | 高寬比    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. 針對**文字 (腳本)** 元件:


        | 名稱                   | Text               | 字型大小    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | 麥克風狀態: | 20           |
        | AzureResponseLabel     | Azure Web 回應 | 20           |
        | DictationLabel         |   您剛剛說過:   | 20           |
        | TranslationResultLabel |    機器翻譯    | 20           |

        ![輸入 UI 標籤的對應值。](images/AzureLabs-Lab1-24.png)

    3. 此外, 請將字型樣式設為**粗體**。 這會讓文字更容易閱讀。

        ![粗體字型。](images/AzureLabs-Lab1-25.png)

7.  針對[第5章](#chapter-5--create-the-results-class)所建立的每個*UI 文字物件*, 建立新的*子* **ui 文字物件**。 這些子系會顯示應用程式的輸出。 以滑鼠右鍵按一下您想要的父系來建立*子*物件 (例如*MicrophoneStatusLabel*), 然後選取 [ **UI** ], 再選取 [**文字**]。
8.  針對上述每個子系, 請選取它, 並使用下表來設定 [偵測器] 面板中的參數。

    1. 針對**矩形轉換**元件:

        | 名稱                  | 轉換-*位置* | 寬度      | 高寬比    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y-30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y-30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y-30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y-30 Z 0          | 300        | 30        |

    2. 針對**文字 (腳本)** 元件:

        | 名稱                  | Text          | 字型大小    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 接下來, 為每個文字元件選取 [中心] 對齊選項:

    ![對齊文字。](images/AzureLabs-Lab1-26.png)

10. 若要確保**子 UI 文字**物件可輕鬆讀取, 請變更其*色彩*。 若要這麼做, 請按一下 [*色彩*] 旁邊的橫條 (目前為「黑色」)。 

    ![輸入 UI 文字輸出的對應值。](images/AzureLabs-Lab1-27.png)
 
11. 然後, 在 [新增]、[小]、[*色彩*] 視窗中, 將*十六進位色彩*變更為:**0032EAFF**

    ![將色彩更新為藍色。](images/AzureLabs-Lab1-28.png)
 
12. 以下是**UI**的外觀。
    1.  在 [階層]*面板*中:

        ![在提供的結構中具有階層。](images/AzureLabs-Lab1-29.png)

    2.  在*場景*和*遊戲視圖*中:

        ![將場景和遊戲視圖放在相同的結構中。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>第5章–建立結果類別

您需要建立的第一個腳本是*結果*類別, 其負責提供查看轉譯結果的方式。 類別會儲存並顯示下列內容: 

- 來自 Azure 的回應結果。
- 麥克風狀態。 
- 聽寫的結果 (語音到文字)。
- 轉譯的結果。

若要建立此類別: 

1.  在 *專案 面板*中按一下滑鼠右鍵, 然後**建立 > 資料夾**。 將資料夾命名為**Scripts**。 
 
    ![建立腳本資料夾。](images/AzureLabs-Lab1-31.png)

    ![開啟 [腳本] 資料夾。](images/AzureLabs-Lab1-32.png)
 
2.  在 [**腳本**] 資料夾建立後, 按兩下以開啟。 然後在該資料夾中, 以滑鼠右鍵按一下, 然後選取 [**建立] >** [  **C#腳本**]。 將腳本命名為*結果*。 

    ![建立第一個腳本。](images/AzureLabs-Lab1-33.png)
 
3.  按兩下新的*結果*腳本, 以**Visual Studio**開啟它。
4.  插入下列命名空間:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  在類別內插入下列變數:

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  然後, 新增*喚醒 ()* 方法, 這會在類別初始化時被呼叫。 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  最後, 新增負責將各種結果資訊輸出到 UI 的方法。 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。

## <a name="chapter-6--create-the-microphonemanager-class"></a>第6章–建立*MicrophoneManager*類別

您即將建立的第二個類別是*MicrophoneManager*。

此類別負責:

- 偵測連接到耳機或電腦的錄製裝置 (以何者為預設值)。
- 捕捉音訊 (語音) 並使用聽寫將其儲存為字串。
- 聲音暫停之後, 請將聽寫提交至 Translator 類別。
- 裝載可以在需要時停止語音捕捉的方法。

若要建立此類別: 
1.  按兩下 [**腳本**] 資料夾以開啟它。 
2.  在 [**腳本**] 資料夾內部按一下滑鼠右鍵, 然後按一下 [**建立 > C#腳本**]。 將腳本命名為*MicrophoneManager*。 
3.  按兩下新的腳本, 以 Visual Studio 開啟它。
4.  在*MicrophoneManager*類別的頂端, 更新命名空間, 以與下列內容相同:

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  然後, 在*MicrophoneManager*類別內新增下列變數:

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  現在必須加入*喚醒 ()* 和*Start ()* 方法的程式碼。 當類別初始化時, 將會呼叫這些:

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  您可以*刪除* *Update ()* 方法, 因為這個類別不會使用它。
8.  現在您需要應用程式用來啟動和停止語音捕獲的方法, 並將它傳遞給*Translator*類別, 您很快就會建立。 複製下列程式碼, 並將它貼入*Start ()* 方法底下。

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > 雖然此應用程式不會使用它, 但在這裡也會提供*StopCapturingAudio ()* 方法, 您應該要在應用程式中執行停止捕獲音訊的功能。

9.  您現在需要新增聽寫處理常式, 當聲音停止時, 就會叫用它。 然後, 這個方法會將聽寫的文字傳遞給*Translator*類別。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. 請務必先將您的變更儲存在 Visual Studio 中, 然後再返回 Unity。

> [!WARNING]  
> 此時, 您會注意到 [ *Unity 編輯器] 主控台*面板中出現錯誤 (「名稱 ' Translator ' 不存在 ...」)。 這是因為程式碼會參考*Translator*類別, 您將在下一章中建立。

## <a name="chapter-7--call-to-azure-and-translator-service"></a>第7章–呼叫 Azure 和 translator 服務

您需要建立的最後一個腳本是*Translator*類別。 

此類別負責:

-   在 exchange 中使用*Azure*驗證應用程式, 以取得**驗證權杖**。
-   使用**驗證權杖**來提交要轉譯的文字 (從*MicrophoneManager*類別收到)。
-   接收轉譯的結果, 並將它傳遞給要在 UI 中視覺化的*結果*類別。

若要建立此類別: 
1.  移至您先前建立的**腳本**資料夾。 
2.  以滑鼠右鍵按一下 [**專案] 面板**中的 [**建立 > C#腳本**]。 呼叫腳本*Translator*。
3.  按兩下新的*翻譯工具*腳本, 以**Visual Studio**開啟它。
4.  將下列命名空間新增至檔案頂端:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  然後在*Translator*類別內新增下列變數:

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - 插入至 [語言]**列舉**的語言只是範例。 如有需要, 您可以隨意加入更多;[API 支援超過60的語言](https://docs.microsoft.com/azure/cognitive-services/translator/languages)(包括克林貢)!
    > - 有[更多互動式頁面涵蓋可用的語言](https://www.microsoft.com/translator/business/languages/), 不過請注意, 只有當網站語言設定為 ' en-us ' (而 Microsoft 網站可能會重新導向至您的原生語言) 時, 頁面才會運作。 您可以變更頁面底部的網站語言, 或變更 URL。
    > - 上述程式碼片段中的**authorizationKey**值必須是您訂閱*Azure 翻譯工具文字 API*時所收到的**金鑰**。 [第1章](#chapter-1--the-azure-portal)已涵蓋這項功能。

6.  現在必須加入*喚醒 ()* 和*Start ()* 方法的程式碼。 
7.  在此情況下, 程式碼會使用授權金鑰來呼叫*Azure* , 以取得*權杖*。

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > 權杖將在10分鐘後到期。 視您應用程式的案例而定, 您可能必須多次進行相同的協同程式呼叫。

8.  取得權杖的協同程式如下所示:

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > 如果您編輯 IEnumerator 方法**GetTokenCoroutine ()** 的名稱, 則必須更新上述程式碼中的*StartCoroutine*和*StopCoroutine*呼叫字串值。 [根據 Unity 檔](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), 若要停止特定的*協同程式*, 您必須使用字串值方法。

9.  接下來, 新增協同程式 (其底下有「支援」資料流程方法), 以取得*MicrophoneManager*類別所收到文字的轉譯。 此程式碼會建立要傳送至*Azure 翻譯工具文字 API*的查詢字串, 然後使用內部 Unity UnityWebRequest 類別, 對具有查詢字串的端點進行「Get」呼叫。 然後, 結果會用來設定結果物件中的轉譯。 下列程式碼顯示執行的方式:

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. 請務必先將您的變更儲存在*Visual Studio*中, 然後再返回*Unity*。

## <a name="chapter-8--configure-the-unity-scene"></a>第8章–設定 Unity 場景

1.  傳回在 Unity 編輯器中，按一下並拖曳 *結果* 類別 *從* **指令碼** 資料夾 **Main Camera** 中的物件 *階層面板*。
2.  按一下**主攝影機**並查看 [*檢查] 面板*。 您會發現, 在新加入的*腳本*元件中, 有四個欄位具有空白值。 這些是程式碼中屬性的輸出參考。 
3.  將適當的**文字**物件從 [階層]*面板*拖曳到這四個位置, 如下圖所示。

    ![以指定的值更新目標參考。](images/AzureLabs-Lab1-34.png)
  
4.  接著, 按一下 [**腳本**] 資料夾中的*Translator*類別, 並將其拖曳至 [階層]*面板*中的**主要相機**物件。 
5.  然後, 按一下 [**腳本**] 資料夾中的 [ *MicrophoneManager* ] 類別, 並將其拖曳至 [階層]*面板*中的**主要相機**物件。 
6.  最後, 按一下**主攝影機**並查看 [*檢查器] 面板*。 您會注意到在您拖曳的腳本中有兩個下拉式方塊, 可讓您設定語言。
 
    ![請確定預定的翻譯語言為輸入。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>第9章–混合現實中的測試

此時, 您必須測試場景是否已正確執行。

請確定：

- [第1章](#chapter-1--the-azure-portal)所提及的所有設定都已正確設定。 
- *結果*、 *Translator*和*MicrophoneManager*, 腳本會附加至**主要相機**物件。 
- 您已將*Azure 翻譯工具文字 API*服務**金鑰**放在*Translator*腳本內的**authorizationKey**變數中。  
- *主要相機偵測器面板*中的所有欄位都已正確指派。
- 當您執行場景時, 您的麥克風會運作 (如果不是, 請檢查您連接的麥克風是否為*預設*裝置, 而且您已在[Windows 中正確設定](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10))。

您可以按下*Unity 編輯器*中的 [**播放**] 按鈕, 測試沉浸式耳機。
應用程式應透過附加的沉浸式耳機運作。

> [!WARNING]  
> 如果您在 Unity 主控台看到關於預設音訊裝置變更的錯誤, 場景可能無法如預期般運作。 這是因為混合現實入口網站處理具有耳機之內建麥克風的方式。 如果您看到此錯誤, 只要停止場景並重新啟動, 就應該會如預期般運作。

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>第10章–在本機電腦上建立 UWP 解決方案和側載

此專案的 Unity 區段所需的全部內容現在已經完成, 所以可以從 Unity 建立它。

1.  流覽至 [**組建設定**]:**檔案 > 組建設定 ...**
2.  從 [**組建設定**] 視窗中, 按一下 [**建立**]。

    ![建立 Unity 場景。](images/AzureLabs-Lab1-36.png)
  
3.  如果尚未這麼做, 請先勾選**Unity C#專案**。
4.  按一下 [建置] 。 Unity 將會啟動 [檔案*瀏覽器*] 視窗, 您必須在其中建立並選取要建立應用程式的資料夾。 立即建立該資料夾, 並將它命名為*應用程式*。 然後選取 [*應用程式*] 資料夾, 按 [**選取資料夾**]。 
5.  Unity 會開始將您的專案建立至*應用程式*資料夾。 
6.  Unity 完成建立之後 (可能需要一些時間), 它會在組建的位置開啟 [檔案*瀏覽器*] 視窗 (請檢查您的工作列, 因為它不一定會出現在視窗的上方, 但會通知您加入新的視窗)。

## <a name="chapter-11--deploy-your-application"></a>第11章–部署您的應用程式

若要部署您的應用程式:

1.  流覽至新的 Unity 組建 (*應用程式*資料夾), 然後使用*Visual Studio*開啟方案檔。
2.  在 [解決方案設定] 中, 選取 [ **Debug**]。
3.  在解決方案平臺中, 選取 [ **x86**]、[**本機電腦**]。 

    > 針對 Microsoft HoloLens, 您可能會發現將此設定為 [*遠端電腦*] 比較容易, 因此您不會行動網卡到電腦。 不過, 您也必須執行下列動作:
    > - 知道您的 HoloLens 的**IP 位址**, 您可以在 *> Network & Internet > Wi-fi > Advanced 選項*的 [設定] 中找到它;IPv4 是您應該使用的位址。 
    > - 請確定*開發人員模式*已**開啟**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >* 。

    ![從 Visual Studio 部署解決方案。](images/AzureLabs-Lab1-37.png)
    
 
4.  移至 [**建立] 功能表**, 然後按一下 [**部署方案**], 將應用程式側載至您的電腦。
5.  您的應用程式現在應該會出現在已安裝的應用程式清單中, 並準備好啟動。
6.  啟動之後, 應用程式會提示您授權存取麥克風。 請務必按一下 [**是]** 按鈕。
7.  您現在已經準備好開始翻譯了!

## <a name="your-finished-translation-text-api-application"></a>您完成的翻譯文字 API 應用程式

恭喜, 您建立了一個混合現實應用程式, 利用 Azure 翻譯文字 API 將語音轉換成翻譯的文字。

![最終產品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

您是否可以將文字轉換語音功能新增至應用程式, 以說出傳回的文字？

### <a name="exercise-2"></a>練習2

讓使用者可以在應用程式本身內變更來源和輸出語言 (「從」和「到」), 因此每次您想要變更語言時, 都不需要重建應用程式。
