---
title: MR 和 Azure 301-語言翻譯
description: 完成這個課程來了解如何實作 Azure Translator Text API，在混合的實境應用程式中。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 翻譯文字、 hololens、 沉浸式 vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596314"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR 和 Azure 301:語言翻譯

在此課程中，您將學習如何將翻譯功能新增至 Translator Text API 搭配使用 Azure 認知服務的混合的實境應用程式。

![最終產品](images/AzureLabs-Lab1-00.png)

Translator Text API 是近乎即時地適用於服務的翻譯。 服務是以雲端為基礎，並使用 REST API 呼叫，讓應用程式可以使用的類神經機器翻譯技術翻譯成其他語言的文字。 如需詳細資訊，請瀏覽[Azure Translator Text API 頁面](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。

完成本課程的詳細資訊，您必須能夠執行下列作業的混合的實境應用程式：

1.  使用者會說話連接沈浸式的 (VR) 耳機式麥克風 （或內建的麥克風的 HoloLens）。
2.  應用程式會擷取語音輸入，並將它傳送至 Azure 的 Translator Text API。
3.  轉譯結果會顯示 Unity 場景中的簡單 UI 群組中。

本課程將教導您如何從轉譯程式服務取得結果到 Unity 為基礎的範例應用程式。 它會決定要將這些概念套用到您可能建置自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 301:語言翻譯</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- 一組的耳機與內建的麥克風 （如果耳機沒有內建的麥克風和喇叭）
- Azure 的安裝程式] 及 [翻譯擷取的網際網路存取

## <a name="before-you-start"></a>開始之前

- 若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。
- 本教學課程中的程式碼可讓您從預設麥克風的裝置連線到您的電腦記錄。 請確定預設麥克風的裝置設定為您打算用來擷取您的語音裝置。
- 若要允許您的電腦啟用語音輸入，請移至**設定 > 隱私權 > 語音、 筆跡 & 鍵入**，然後選取按鈕**語音服務開啟與輸入的建議**。
- 如果您使用麥克風並連接到的耳機 （或內建） 耳機，請確定選擇 「 我穿上我耳機，切換到耳機式麥克風 」 開啟**設定 > 混合實境 > 音訊及語音**。

   ![混合的實境設定](images/AzureLabs-Lab1-00-5.png)

   ![設定麥克風](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> 請注意，如果您正在開發的沈浸式耳機本實驗室中，您可能會遇到的音訊輸出裝置問題。 這是 unity 的因為 unity (Unity 2018.2) 更新版本中已修正的問題。 此問題會防止 Unity 在執行階段變更預設音訊輸出裝置。 因應之道，請確定您已完成上述步驟，並關閉並重新開啟編輯器 中，當此問題會。

## <a name="chapter-1--the-azure-portal"></a>第 1 章-Azure 入口網站

若要使用 Azure 轉譯程式 API，您必須設定您的應用程式提供服務的執行個體。

1.  登入[Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**新增**右上角左角並搜尋"Translator Text API。 」 選取 **輸入**。

    ![新的資源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 單字**的新**可能已取代為**建立資源**，較新的入口網站中。

3.  新的頁面將提供的描述*Translator Text API*服務。 在左下方的這個頁面上，選取**建立**按鈕，以建立與這個關聯服務。

    ![建立 Translator Text API 服務](images/AzureLabs-Lab1-03.png)

4.  一旦您按下**建立**:

    1. 插入您想要**名稱**此服務執行個體。
    2. 選取適當**訂用帳戶**。
    3. 選取 **定價層**適合您，如果這是第一個時間來建立*轉譯程式文字服務*，免費層 （名為 F0） 應該是您可以使用。
    4. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些實驗室中） 的單一專案保留）。

        > 如果您想要深入了解 Azure 資源群組，請[瀏覽資源群組文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 判斷**位置**資源群組 （如果您要建立新的資源群組）。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。
    6. 您也必須確認您已了解這些條款和條件套用到此服務。
    7. 選取 [建立]  。

        ![選取 [建立] 按鈕。](images/AzureLabs-Lab1-04.png)

5.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。
6.  通知會出現在入口網站中，一旦建立服務執行個體。 

    ![Azure 服務建立通知](images/AzureLabs-Lab1-05.png)

7.  按一下通知，以探索新的服務執行個體。 

    ![請移至資源的快顯視窗。](images/AzureLabs-Lab1-06.png)

8.  按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 您會前往新的 Translator Text API 服務執行個體。 

    ![Translator Text API 服務頁面](images/AzureLabs-Lab1-07.png)

9.  在本教學課程中，您的應用程式將需要對您的服務，透過使用您的服務訂用帳戶金鑰進行呼叫。 
10. 從*快速入門*頁面您*Translator Text*服務，瀏覽至第一個步驟中，*取得您的金鑰*，然後按一下**金鑰**（或者您可以也達到此目的按一下藍色超連結索引鍵，位於服務導覽功能表中，以索引鍵的圖示表示）。 這將顯示您的服務*金鑰*。
11. 需要顯示的索引鍵，其中的複本，因為您將需要此更新版本中您的專案。 

## <a name="chapter-2--set-up-the-unity-project"></a>第 2 章-設定 Unity 專案

設定並測試您的混合的實境沈浸式耳機。

> [!NOTE]
> 您不會需要移動控制器這堂課程。 如果您需要支援的沈浸式耳機的設定，請[遵循下列步驟](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

下列已啟動的一組典型混合實境進行開發，此情況下，是良好的其他專案範本：

1.  開啟*Unity*然後按一下**新增**。 

    ![啟動新的 Unity 專案。](images/AzureLabs-Lab1-08.png)

2.  您現在必須提供 Unity 專案名稱。 插入**MR_Translation**。 請確定專案類型設定為**3D**。 設定*位置*適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![提供新的 Unity 專案的詳細資料。](images/AzureLabs-Lab1-09.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯 > 偏好**，然後在新視窗中，瀏覽**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![更新指令碼編輯器喜好設定。](images/AzureLabs-Lab1-10.png)

4.  接下來，移至**檔案 > 組建設定**，並切換至平台**通用 Windows 平台**，按一下**切換平台** 按鈕。

    ![建置設定 視窗中，切換至 UWP 的平台。](images/AzureLabs-Lab1-11.png)

5.  移至**檔案 > 組建設定**並確定：

    1. **裝置為目標**設定為**任何裝置**。

        > 對於 Microsoft HoloLens，設定**目標裝置**要*HoloLens*。

    2. **建置型別**設為**D3D**
    3. **SDK**設為**最新安裝**
    4. **Visual Studio 版本**設為**最新安裝**
    5. **建置並執行**設為**本機電腦**
    6. 儲存場景，並將它新增至組建。

        1. 做法是選取**加入開啟的場景**。 儲存視窗會出現。

            ![按一下 新增開啟場景按鈕](images/AzureLabs-Lab1-12.png)

        2. 建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![建立新的指令碼資料夾](images/AzureLabs-Lab1-13.png)

        3. 開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中輸入**MR_TranslationScene**，然後按**儲存**。

            ![指定新的場景的名稱。](images/AzureLabs-Lab1-14.png)

            > 請注意，您必須先儲存您的 Unity 場景中*資產*資料夾，因為它們必須是與 Unity 專案相關聯。 建立場景資料夾 （和其他類似的資料夾） 是建構的 Unity 專案的典型方式。

    7. 剩餘的設定，*組建設定*，應保持為預設值，現在。

6. 中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。 

    ![開啟播放程式設定。](images/AzureLabs-Lab1-15.png)

7. 在此窗格中，少數設定需要驗證：

    1. 在 [**其他設定**] 索引標籤：

        1. **指令碼執行階段版本**應該**穩定**（.NET 3.5 對等）。
        2. **指令碼後端**應該是 **.NET**
        3. **API 相容性層級**應該是 **.NET 4.6**

            ![更新其他設定。](images/AzureLabs-Lab1-16.png)
      
    2. 內**發佈設定**索引標籤之下**功能**，檢查：

        1. **InternetClient**
        2. **Microphone**

            ![正在更新發行的設定。](images/AzureLabs-Lab1-17.png)

    3. 在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。

        ![更新 R 設定。](images/AzureLabs-Lab1-18.png)

8.  回到**Build Settings**， *UnityC#專案*不再呈現灰色，這旁邊的核取方塊。 
9.  關閉 [建立設定] 視窗。
10. 儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。

## <a name="chapter-3--main-camera-setup"></a>第 3 章-Main Camera 安裝程式

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件的課程，並直接在程式碼中繼續進行，請放心[下載此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)，它匯入到您的專案做為[ *自訂封裝*](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 5 章](#chapter-5--create-the-results-class)。 您仍然必須建立 Unity 專案。

1.  在 *階層面板*，您會發現呼叫物件**Main Camera**，這個物件代表您的 「 主要 」 觀點來看，當您 「 內部 」 您的應用程式。
2.  您面前的 Unity 儀表板中，選取**主攝影機 GameObject**。 您將會發現*偵測器 面板*（通常是到右方時，儀表板中找到） 將會顯示各種元件的*GameObject*，使用*轉換*在頂端，後面接著*相機*，和一些其他元件。 您必須重設主攝影機的轉換，以便正確地定位。
3.  若要這樣做，請選取**齒輪**相機的旁邊的圖示*轉換*元件，然後選取**重設**。 

    ![重設 Main Camera 轉換。](images/AzureLabs-Lab1-19.png)
 
4.  *轉換*元件再看起來應該像：

    1. *位置*設定為**0，0，0**
    2. *旋轉*設為**0，0，0**
    3. 並*擴展*設定為**1，1，1**

        ![轉換觀景窗的資訊](images/AzureLabs-Lab1-20.png)

5.  接下來，使用**Main Camera**選取資訊，請參閱**新增元件** 按鈕位於最底部*Inspector 面板*。 
6.  選取該按鈕，然後搜尋 (輸入*音訊來源*到 [搜尋] 欄位，或瀏覽區段) 稱為元件**音訊來源**，如下所示並加以選取 （按下 enter 上面也可以運作）。
7.  *音效來源*元件會加入至**Main Camera**，如下所示。

    ![新增音訊來源元件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > 針對 Microsoft HoloLens，您必須也變更下列項目，兩者皆屬於**相機**元件在您**Main Camera**:
    > - **清除旗標：** 不透明色彩。
    > - **背景**' Black、 Alpha 0'-十六進位色彩: #00000000。

## <a name="chapter-4--setup-debug-canvas"></a>第 4 章-設定偵錯畫布

若要顯示的輸入和輸出的轉譯，必須建立基本的 UI。 這堂課程中，您將建立畫布 UI 物件，以顯示資料的數個 'Text' 物件。

1.  中的空白區域上按一下滑鼠右鍵*階層面板*下方**UI**，加入**畫布**。

    ![加入新的畫布 UI 物件。](images/AzureLabs-Lab1-22.png)

2.  與已選取的畫布物件*偵測器 面板*（在 '畫布 」 元件），變更**轉譯模式**來**世界空間**。 
3.  接下來，變更下列參數*Inspector 面板 Rect 轉換*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *Width* -    500
    3. *Height* -   300
    4. *縮放比例* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![更新畫布的 rect 轉換。](images/AzureLabs-Lab1-23.png)
 
4.  以滑鼠右鍵按一下**畫布**中*階層面板*下方**UI**，並新增**面板**。 這**面板**會提供您將會顯示在場景中的文字的背景。
5.  以滑鼠右鍵按一下**面板**中*階層面板*下方**UI**，並新增**文字物件**。 重複相同的程序，直到您完成建立四個 UI 文字物件總計 (提示： 如果您有選取的第一個 'Text' 物件，您可以直接按下 **'Ctrl' + 有 '** 、 複製它，除非您有四個總計)。 
6.  每個**文字物件**、 選取它，並使用下表設定的參數*Inspector 面板*。

    1. 針對*Rect 轉換*元件：

        | 名稱                   | 轉換-*位置*             | 寬度      | 高度    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. 針對**文字 （指令碼）** 元件：


        | 名稱                   | 文字               | 字型大小    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | 麥克風狀態： | 20           |
        | AzureResponseLabel     | Azure 的 Web 回應 | 20           |
        | DictationLabel         |   您剛才提到：   | 20           |
        | TranslationResultLabel |    轉譯：    | 20           |

        ![輸入的 UI 標籤的對應值。](images/AzureLabs-Lab1-24.png)

    3. 此外，請 字型樣式**粗體**。 這會讓文字更方便閱讀。

        ![粗體字型。](images/AzureLabs-Lab1-25.png)

7.  每個*UI 文字物件*中建立[第 5 章](#chapter-5--create-the-results-class)，建立新*子* **UI 文字物件**。 這些子系會顯示應用程式的輸出。 建立*子系*透過以滑鼠右鍵按一下您要的父系的物件 (例如*MicrophoneStatusLabel*)，然後選取**UI** ，然後選取**文字**.
8.  針對每個這些子系，請選取它，然後使用下列設定的參數偵測器 面板中的資料表。

    1. 針對**Rect 轉換**元件：

        | 名稱                  | 轉換-*位置* | 寬度      | 高度    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. 針對**文字 （指令碼）** 元件：

        | 名稱                  | 文字          | 字型大小    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 接下來，選取每個文字元件 'centre' 對齊選項：

    ![文字對齊。](images/AzureLabs-Lab1-26.png)

10. 若要確保**子系 UI 文字**物件都可以輕鬆地讀取、 變更其*色彩*。 依序按一下  列上 （目前 ' 黑色'） 下的一步*色彩*。 

    ![輸入對應 UI 文字輸出的值。](images/AzureLabs-Lab1-27.png)
 
11. 然後，在新的很小，*色彩*視窗中，變更*十六進位色彩*來：**0032EAFF**

    ![更新為藍色的色彩。](images/AzureLabs-Lab1-28.png)
 
12. 以下是如何**UI**應該看起來。
    1.  在 *階層面板*:

        ![在提供的結構中的階層。](images/AzureLabs-Lab1-29.png)

    2.  在 *場景*並*遊戲檢視*:

        ![在相同的結構中的場景和遊戲的檢視。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>第 5 章-建立結果類別

您必須建立第一個指令碼*結果*類別，這是負責提供方法，以查看轉譯的結果。 類別會儲存，並會顯示下列資訊： 

- 從 Azure 回應結果。
- 麥克風狀態。 
- 聽寫 （語音文字） 的結果。
- 轉譯結果。

若要建立此類別： 

1.  以滑鼠右鍵按一下*專案 面板*，然後**建立 > 資料夾**。 將資料夾命名**指令碼**。 
 
    ![建立指令碼 資料夾。](images/AzureLabs-Lab1-31.png)

    ![開啟 [指令碼] 資料夾。](images/AzureLabs-Lab1-32.png)
 
2.  具有**指令碼**資料夾建立，連按兩下以開啟該項目。 然後在該資料夾，然後按一下滑鼠右鍵，並選取**建立 >** 再**C#指令碼**。 指令碼命名*結果*。 

    ![建立第一個指令碼。](images/AzureLabs-Lab1-33.png)
 
3.  按兩下新*結果*指令碼，以開啟它**Visual Studio**。
4.  插入下列命名空間：

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  類別內插入下列變數：

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

6.  然後新增*Awake()* 類別初始化時所呼叫的方法。 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  最後，新增會負責輸出至 UI 的各種結果資訊的方法。 

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

8.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-6--create-the-microphonemanager-class"></a>第 6 章-建立*MicrophoneManager*類別

您要建立第二個類別是*MicrophoneManager*。

這個類別會負責：

- 偵測耳機或 （無論是預設值） 的機器附加的錄音裝置。
- 擷取音訊 （語音），並將它儲存為字串使用聽寫。
- 一旦已暫停的語音，提交聽寫，轉譯器類別。
- 裝載的方法，如有需要，可停止語音擷取。

若要建立此類別： 
1.  按兩下**指令碼**資料夾，將它開啟。 
2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。 指令碼命名*MicrophoneManager*。 
3.  按兩下新的指令碼，以使用 Visual Studio 中開啟它。
4.  更新命名空間相同，如下所示，在頂端*MicrophoneManager*類別：

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  然後，新增下列變數內*MicrophoneManager*類別：

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

6.  程式碼*Awake()* 並*start （)* 方法現在需要加入。 在類別初始化時，這些將會呼叫：

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

7.  您可以*刪除* *update （)* 方法，因為這個類別不會使用它。
8.  現在，您需要讓應用程式用來啟動和停止語音擷取，並將它傳遞至方法*Translator*您即將建置的類別。 下列程式碼複製並貼上下方*start （)* 方法。

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
    > 雖然此應用程式不會使用它， *StopCapturingAudio()* 方法也已提供在這裡，如果您想要實作的功能，以停止擷取您的應用程式中的音訊。

9.  您現在需要新增語音停止時將會叫用語音輸入處理常式。 這個方法會再將要聽寫的文字*Translator*類別。

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

10. 請務必在 Visual Studio 中儲存您的變更，然後再回到 Unity。

> [!WARNING]  
> 此時您會注意到錯誤不會出現在*Unity 編輯器 主控台*面板 ("name 'Translator' 不存在...」)。 這是因為程式碼參考*Translator*類別，您將在下一步 一章。

## <a name="chapter-7--call-to-azure-and-translator-service"></a>第 7 章 – 對 Azure 和轉譯程式的服務呼叫

您需要建立的最後一個指令碼*Translator*類別。 

這個類別會負責：

-   驗證應用程式與*Azure*，exchange for**驗證權杖**。
-   使用**驗證權杖**送出的文字 (收到*MicrophoneManager*類別) 來轉譯。
-   接收轉譯的結果，並將它傳遞給*結果*類別，以在 UI 中視覺化。

若要建立此類別： 
1.  移至**指令碼**您先前建立的資料夾。 
2.  以滑鼠右鍵按一下**專案 面板**，**建立 >C#指令碼**。 呼叫指令碼*Translator*。
3.  按兩下新*Translator*以開啟它的指令碼**使用 Visual Studio**。
4.  檔案開頭處新增下列命名空間：

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  然後新增下列變數內*Translator*類別：

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
    > - 插入至語言的語言**enum**只是範例。 依需要新增更多，如果您想要的選項;[API 支援 60 語言](https://docs.microsoft.com/azure/cognitive-services/translator/languages)（包括克林貢） ！
    > - 沒有[涵蓋可用的語言更具互動性的頁面](https://www.microsoft.com/translator/business/languages/)，不過留意頁面才會出現在時使用的站台語言設定為 ' en-' （和 Microsoft 網站將 可能的重新導向至您的原生語言）。 您可以變更站台的語言，在下方的頁面或改變的 URL。
    > - **AuthorizationKey**值，在上述程式碼片段中，必須**金鑰**您訂閱時，您會收到*Azure Translator Text API*。 這已涵蓋在[第 1 章](#chapter-1--the-azure-portal)。

6.  程式碼*Awake()* 並*start （)* 方法現在需要加入。 
7.  在此情況下，程式碼會呼叫*Azure*使用授權金鑰，取得*語彙基元*。

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
    > 權杖會在 10 分鐘後過期。 根據您的應用程式案例，您可能必須進行多次呼叫相同的協同程式。

8.  若要取得此語彙基元協同程式如下：

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
    > 如果您編輯 IEnumerator 方法的名稱**GetTokenCoroutine()** ，您需要更新*StartCoroutine*並*StopCoroutine*呼叫上述程式碼中的字串值。 [根據 Unity 文件](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)，以停止特定*協同程式*，您需要使用的字串值的方法。

9.  接下來，新增的協同程式 （使用 「 支援 」 資料流的方法正下方） 以取得所收到的文字翻譯*MicrophoneManager*類別。 此程式碼會建立將傳送至查詢字串*Azure Translator Text API*，然後使用內部的 Unity UnityWebRequest 類別的查詢字串的端點 'Get' 呼叫。 結果是再用來設定您的結果物件中的翻譯。 下列程式碼顯示實作：

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

10. 請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-8--configure-the-unity-scene"></a>第 8 – 設定 Unity 場景

1.  傳回在 Unity 編輯器中，按一下並拖曳 *結果* 類別 *從* **指令碼** 資料夾 **Main Camera** 中的物件 *階層面板*。
2.  按一下  **Main Camera**並查看*Inspector 面板*。 您會注意到內新增*指令碼*元件，有四個欄位為空值。 這些是在程式碼屬性的輸出參考。 
3.  拖曳適當**文字**物件從*階層面板*對這些四個位置，如下圖所示。

    ![使用指定的值更新目標參考。](images/AzureLabs-Lab1-34.png)
  
4.  接下來，按一下並拖曳*Translator*從類別**指令碼**資料夾**Main Camera**物件*階層面板*。 
5.  然後，按一下並拖曳*MicrophoneManager*從類別**指令碼**資料夾**Main Camera**物件*階層面板*。 
6.  最後，按一下**Main Camera**並查看*Inspector 面板*。 您會發現，在您拖放至指令碼，有兩個的下拉式清單方塊，可讓您設定的語言。
 
    ![請確定輸入的預定的翻譯語言。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>第 9 章 – 在混合實境中的測試

此時，您需要測試已正確地實作場景。

請確定：

- 中所述的所有設定[第 1 章](#chapter-1--the-azure-portal)都已正確設定。 
- *結果*， *Translator*，並*MicrophoneManager*，指令碼會附加至**Main Camera**物件。 
- 您已經放置您*Azure Translator Text API*服務**金鑰**內**authorizationKey**變數*Translator*指令碼。  
- 中的所有欄位*Main 攝影機偵測器 面板*皆正確。
- 執行您的場景時，是否正常運作您的麥克風 (如果沒有，請檢查您連接的麥克風*預設*裝置，而且您擁有[正確地設定 Windows 內](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10))。

您可以藉由按下測試沈浸式耳機**播放**按鈕*Unity Editor*。
應用程式應該可以正常運作，透過附加的沈浸式耳機。

> [!WARNING]  
> 如果您看到錯誤的相關變更預設音訊裝置，Unity 主控台中，場景可能無法如預期般運作。 這是因為內建麥克風耳機，讓它們會處理混合的實境入口網站的方式。 如果您看到此錯誤，只是停止場景並重新啟動它，而且項目應該都能當作預期。

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>第 10 – 建置 UWP 方案，然後在本機電腦上的側載

此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。

1.  瀏覽至**組建設定**:**檔案 > 組建設定...**
2.  從**Build Settings**  視窗中，按一下**建置**。

    ![建置 Unity 場景。](images/AzureLabs-Lab1-36.png)
  
3.  如果您尚未，勾選**UnityC#專案**。
4.  按一下 [建置]  。 將會啟動 unity*檔案總管*視窗中，您要建立，然後選取 建置到應用程式的資料夾。 現在，建立該資料夾並將它命名*應用程式*。 然後使用*應用程式*資料夾選取，請按下**選取資料夾**。 
5.  Unity 會開始建置您的專案*應用程式*資料夾。 
6.  一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟*檔案總管*視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。

## <a name="chapter-11--deploy-your-application"></a>第 11 章-部署您的應用程式

若要部署您的應用程式：

1.  瀏覽至新的 Unity 組建 (*應用程式*資料夾)，並開啟方案檔*Visual Studio*。
2.  在 方案組態選取**偵錯**。
3.  在 方案平台上，選取**x86**，**本機**。 

    > 針對 Microsoft HoloLens，您可能會發現它更輕鬆地將此設為*遠端機器*，如此一來，您不行動網卡到您的電腦。 不過，您必須也執行下列作業：
    > - 了解**IP 位址**的您 HoloLens，位於*設定 > 網路和網際網路 > Wi-fi > 進階選項*; IPv4 是您應該使用的位址。 
    > - 請確定*開發人員模式*是**上**; 在找到*設定 > 更新與安全性 > 適用於開發人員*。

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab1-37.png)
    
 
4.  移至**建置 功能表**，然後按一下**部署方案**側載應用程式以您的電腦。
5.  您的應用程式現在應該會出現在清單中的已安裝的應用程式，即可啟動。
6.  一旦啟動，應用程式會提示您授權存取麥克風。 請務必按一下 [**是**] 按鈕。
7.  您現在已準備好開始轉譯 ！

## <a name="your-finished-translation-text-api-application"></a>您已完成的翻譯文字 API 應用程式

恭喜，您所建立的混合的實境應用程式，運用 Azure 翻譯文字 API，將語音翻譯的文字。

![最終的產品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

可以您文字轉換語音將功能加入至應用程式，使傳回的文字說出？

### <a name="exercise-2"></a>練習 2

讓使用者變更應用程式本身，來源和輸出的語言 （'from' 和 'to'），因此應用程式就不需要重建每次您想要變更語言。
