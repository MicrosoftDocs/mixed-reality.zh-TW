---
title: MR 和 Azure 313-IoT 中樞服務
description: 完成這個課程來了解如何實作在執行 Ubuntu 16.4 的虛擬機器上的 Azure IoT 中樞服務，並使用 Microsoft HoloLens 或沈浸式的 (VR) 耳機的訊息資料以視覺化方式檢視。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 edge、 iot edge、 教學課程、 api、 通知、 函數、 資料表、 沈浸式 hololens、 vr、 iot、 虛擬機器、 ubuntu、 python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591132"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

# <a name="mr-and-azure-313-iot-hub-service"></a>MR 和 Azure 313:IoT 中樞服務

![課程結果](images/AzureLabs-Lab313-00.png)

在此課程中，您將了解如何實作**Azure IoT 中樞服務**的虛擬機器上執行 Ubuntu 16.4 的作業系統。 **Azure 函數應用程式**然後將用來從您的 Ubuntu VM，接收訊息，並內將結果儲存**Azure 表格服務**。 您接著可以檢視此資料使用**Power BI** Microsoft HoloLens 或沈浸式 (VR) 耳機。

本課程的內容*適用於*到 IoT Edge 裝置，但為了本課程中，則會著重於在虛擬機器環境中，如此便不需要實體的 Edge 裝置的存取。

藉由完成本課程，您將學習：

- 部署**IoT Edge 模組**至虛擬機器 (Ubuntu 16 OS)，即代表您的 IoT 裝置。
- 新增**Azure 自訂視覺 Tensorflow 模型**到 Edge 模組，將會分析儲存在容器映像的程式碼。
- 設定模組，將分析結果訊息傳送至您**IoT 中樞服務**。
- 使用**Azure 函數應用程式**來儲存訊息內**Azure 資料表**。
- 設定好**Power BI**收集預存的訊息，並建立報表。
- 以視覺化方式檢視您的 IoT 訊息資料內**Power BI**。

您將使用的服務包括：

- **Azure IoT 中樞**是 Microsoft Azure 服務可讓開發人員連接、 監視及管理 IoT 資產。 如需詳細資訊，請瀏覽[ **Azure IoT 中樞服務**頁面](https://azure.microsoft.com/en-au/services/iot-hub/)。

- **Azure Container Registry**是讓開發人員能夠儲存各種類型的容器的容器映像，Microsoft Azure 服務。 如需詳細資訊，請瀏覽[ **Azure 容器登錄服務**頁面](https://azure.microsoft.com/en-au/services/container-registry/)。

- **Azure 函式應用程式**是為 Microsoft Azure 服務，可讓開發人員執行程式碼片段，'函式'，在 Azure 中。 這可用來將工作委派給雲端，而不是您本機的應用程式，可以有許多優點。 **Azure Functions**支援數種開發語言，包括 C\#，F\#、 Node.js、 Java 和 PHP。 如需詳細資訊，請瀏覽[ **Azure Functions**頁面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

- **Azure 儲存體：資料表**是 Microsoft Azure 服務，可讓開發人員儲存結構化，非 SQL、 在雲端中的資料進行更容易存取任何位置。 服務擁有許多的無結構描述設計中，如有需要讓資料表的進化的因此非常大的彈性。 如需詳細資訊，請瀏覽[ **Azure 資料表**頁面](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

本課程將教導您如何設定並使用 IoT 中樞服務，然後以視覺化方式檢視裝置所提供的回應。 它會決定要自訂的 IoT 中樞服務安裝程式，故您可能建置運用這些概念。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 313:IoT 中樞服務</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>必要條件

如與混合實境，包括 Microsoft HoloLens，開發最新的必要條件，請造訪[安裝工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)文章。

> [!NOTE]
> 本教學課程專為開發人員使用 Python 的基本經驗。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。 中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，與下面列出的。

下列的硬體和軟體是必要項目：

- Windows 10 Fall Creators Update （或更新版本），**啟用開發人員模式**

    > [!WARNING]
    > 您無法執行使用只有 Windows 10 Home Edition 上的 HYPER-V 虛擬機器。

- Windows 10 SDK （最新版）
- HoloLens，a**啟用開發人員模式**
- Visual Studio 2017.15.4 （僅用來存取 Azure 的雲端總管）
- Azure 和 IoT 中樞服務的網際網路存取。 如需詳細資訊，請遵循此[連結至 IoT 中樞服務頁面](https://azure.microsoft.com/en-au/services/iot-hub/)
- 機器學習模型。 如果您不需要您自己的已備妥，可使用模型時，[您可以使用本課程提供的模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)。
- **HYPER-V**啟用 Windows 10 的開發電腦上的軟體。
- 在您的開發電腦或者執行執行 Ubuntu （16.4 或 18.4） 的虛擬機器可以使用不同的電腦執行 Linux (Ubuntu 16.4 或 18.4)。 您可以找到更多有關如何在 Windows 上建立的 VM 使用中的 HYPER-V [」 開始之前 > 一章](#before-you-start)。 (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>開始之前

1. 設定並測試您的 HoloLens。 如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。
2. 它是個不錯的主意，執行**校正**並**感應器調整**開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時。

校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。

如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。

3. 設定您**Ubuntu 虛擬機器**使用**HYPER-V**。 下列資源將協助您進行程序。
    1.  首先，請遵循下列連結來[下載 Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/)。 選取  **64 位元電腦 (AMD64) 桌面映像**。
    2.  請確定**HYPER-V**啟用您的 Windows 10 電腦上。 您可以依照此連結以取得指導方針[安裝和啟用 Windows 10 上的 HYPER-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)。
    3.  啟動 HYPER-V 並建立新的 Ubuntu VM。 您可以遵循此連結[如何使用 HYPER-V 建立的 VM 上的逐步解說指南](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)。 若要要求時 **[從開機映像檔安裝作業系統]**，選取**Ubuntu ISO**您稍早有下載。

    > [!NOTE]
    > 使用**HYPER-V 快速建立**不建議進行。  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>第 1 章-擷取自訂視覺模型

本課程中，您將可以存取[預先建置的自訂視覺模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)，偵測到鍵盤及滑鼠從映像。 如果您使用此功能，請繼續進行[第 2 章](#chapter-2---the-container-registry-service)。

不過，您可以遵循下列步驟，如果您想要使用您自己的自訂視覺模型：

1. 在您**自訂視覺專案**前往**效能** 索引標籤。

    > [!WARNING]
    > 您的模型必須使用*compact*網域，將模型匯出。 您可以變更您模型的網域設定中，為您的專案。

    ![效能 索引標籤](images/AzureLabs-Lab313-01.png)

2. 選取 **反覆項目**您想要匯出，然後按一下**匯出**。 刀鋒視窗會出現。

    ![匯出刀鋒視窗](images/AzureLabs-Lab313-02.png)

3. 在刀鋒視窗中按一下**Docker 檔案**。

    ![選取 docker](images/AzureLabs-Lab313-03.png)

4. 按一下  **Linux**中的下拉式選單，然後按一下 **下載**。

    ![按一下 [下載]](images/AzureLabs-Lab313-04.png)

5. 將解壓縮的內容。 您可以將在本課程後面。

## <a name="chapter-2---the-container-registry-service"></a>第 2 章-容器登錄服務

**容器登錄服務**是用來裝載您的容器存放庫。

**IoT 中樞服務**您會用來建置，並使用在這個課程中，是指**容器登錄服務**取得要在您的 Edge 裝置中部署的容器。

1. 首先，請依照這[Azure 入口網站連結](https://portal.azure.com/)，並使用您的認證登入。

2. 移至**建立資源**並尋找**Container Registry**。

    ![容器登錄](images/AzureLabs-Lab313-05.png)

3. 按一下 **建立**。

    ![](images/AzureLabs-Lab313-06.png)

4. 設定服務安裝程式參數：

    1. 在此範例中插入的名稱，為您的專案，其名**IoTCRegistry**。

    2. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理的 Azure 資產的集合計費。 建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。

    3. 設定服務的位置。

    4. 設定**系統管理員使用者**要**啟用**。

    5. 設定**SKU**要**基本**。 

    ![](images/AzureLabs-Lab313-07.png)

5. 按一下 **建立**並等候建立的服務。 

6. 當出現告知您成功建立通知*Container Registry*，按一下**移至資源**重新導向至您的服務頁面。

    ![](images/AzureLabs-Lab313-08.png)

7. 在  *Container Registry*服務頁面上，按一下**存取金鑰**。

8. 記下 （您可以使用您在 [記事本]） 的下列參數：
    1. **Login Server**
    2. **使用者名稱**
    3. **密碼**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>第 3 章-IoT 中樞服務

現在您將開始建立及安裝您**IoT 中樞服務**。

1. 如果您尚未登入，登入[Azure 入口網站](https://portal.azure.com)。

2.  登入之後，按一下**建立資源**在左上角，，然後搜尋**IoT 中樞**，然後按一下**Enter**。

 ![搜尋儲存體帳戶](images/AzureLabs-Lab313-10.png)

3.  新的頁面將提供的描述**儲存體帳戶**服務。 在此提示的左下方，按一下**建立**按鈕，以建立這個執行個體服務。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-11.png)

4.  一旦您按下**建立**，面板會顯示：

    1. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。

        > 如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。


    2. 選取適當**位置**（您在本課程中建立的所有服務上使用相同的位置）。

    3. 插入您想要**名稱**此服務執行個體。    

5.  在頁面底部按一下**下一步:大小和縮放比例**。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-12.png)

6.  在此頁面上，選取您**定價與級別層**（如果這是您第一個 IoT 中樞服務執行個體，免費層應該是您可以使用）。  

7.  按一下 **檢閱 + 建立**。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-13.png)

8.  檢閱您的設定，然後按一下**建立**。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-14.png)

9. 當出現告知您成功建立通知*IoT 中樞*服務，按一下**移至資源**重新導向至您的服務頁面。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-15.png)

10. 捲動左側的側邊面板，直到您看到*自動的裝置管理*，按一下**IoT Edge**。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-16.png)

11. 在顯示於右側視窗中，按一下**加入 IoT Edge 裝置**。 刀鋒視窗會出現在右邊。

12. 在刀鋒視窗中，提供您新的裝置**裝置識別碼**（您所選擇的名稱）。 然後，按一下**儲存**。 *主要*並*次要金鑰*會自動產生，如果您有**自動產生**勾選。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-17.png)

13. 您會瀏覽回到*IoT Edge 裝置*區段中，其中會列出您的新裝置。 按一下 新裝置上 (在紅色外框的下列映像)。 

    ![建立儲存體執行個體](images/AzureLabs-Lab313-18.png)

14. 在 *裝置詳細資料*頁面隨即出現，需要一份**連接字串**（主索引鍵）。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-19.png)

15. 在左側面板請返回並按一下*共用存取原則*，以開啟它。 

16. 在出現的頁面上，按一下**iothubowner**，和刀鋒視窗會出現在螢幕的右邊。 

17. 請記下 （在您的 [記事本])**連接字串**（主索引鍵），供稍後使用設定時*連接字串*到您的裝置。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>第 4 章-設定開發環境

若要建立及部署適用於模組*IoT 中樞 Edge*，您將需要在執行 Windows 10 的開發電腦上安裝下列元件：

1.  [適用於 Windows 的 docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)，它會要求您建立帳戶要能夠下載。 

    [![下載適用於 windows 的 docker](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > 需要 docker *Windows 10 PRO*， *Enterprise 14393*，或*Windows Server 2016 RTM*，以執行。 如果您正在執行其他版本的 Windows 10，您可以嘗試使用 Docker 安裝[Docker 工具箱](https://docs.docker.com/toolbox/toolbox_install_windows/)。

2.  [Python 3.6](https://www.python.org/downloads/)。

    [![下載 python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (也稱為 VS Code)](https://code.visualstudio.com/download)。

    [![下載 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

安裝上述軟體之後，您必須重新啟動您的電腦。

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>第 5 章-設定 Ubuntu 環境

現在您可以移至您的裝置設定**執行 Ubuntu OS**。 請遵循下列步驟來安裝必要的軟體，您將容器部署在您的面板：

> [!IMPORTANT]
> 您應該一律在完成將終端機命令**sudo**以系統管理員使用者身分執行。 也就是：
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  開啟**Ubuntu 終端機**，並使用下列命令來安裝**pip**:

    > [!提示] 您可以開啟*終端機*非常輕鬆地透過使用鍵盤快速鍵：**Ctrl + Alt + T**。

    ```bash
        sudo apt-get install python-pip
    ```

2.  在本章中，您可能會提示您，由*終端機*、 權限使用裝置儲存空間，以及供您輸入**y/n** （是或否），型別 **'y'**，然後按下**Enter**金鑰，才能接受。

3.  該命令完成之後，使用下列命令來安裝**curl**:

    ```bash
        sudo apt install curl
    ```

4.  一次**pip**並**curl**會安裝，請使用下列命令來安裝**IoT Edge 執行階段**，這是為了部署，並控制在面板上的模組：

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. 此時系統會提示您開啟*執行階段組態檔*，以插入**裝置連接字串**，記下 （您在記事本中），建立時**IoT 中樞服務** ([在步驟 14 中的第 3 章](#chapter-3---the-iot-hub-service))。 在終端機中開啟該檔案執行下面這一行：

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. **Config.yaml**檔案將會顯示以供您編輯：

    > [!WARNING]
    > 當此檔案開啟時，可能有些令人混淆。 您必須編輯此檔案，內的文字*終端機*本身。 

    1.  使用鍵盤上的方向鍵來捲動的清單 （您必須捲動一些方式），到行包含":

        「**\<將裝置連接字串 &GT;**"。

    2. 替換成一行，**包括括號**，使用**Device Connection String**您稍早所。

7. 您的連接字串中在鍵盤上的位置，然後按**CTRL-X**來儲存檔案的索引鍵。 它會要求您輸入確認**Y**。然後按**Enter**金鑰，來確認。 您會回到一般*終端機*。 

8. 一旦所有成功地執行這些命令，您將安裝**IoT Edge 執行階段**。 初始化之後，執行階段會在其本身每次開啟裝置電源，啟動，並可以坐在背景中，從部署的模組正在等候**IoT 中樞服務**。

9.  執行下列命令列來初始化*IoT Edge 執行階段*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > 如果您變更.yaml 檔案或上述的安裝程式時，您必須再次執行上述的重新啟動程式碼內*終端機*。

10. 請檢查*IoT Edge 執行階段*藉由執行下列命令列的狀態。 執行階段應該會出現狀態**作用中 （執行）** 綠色文字。

    ```bash
        sudo systemctl status iotedge
    ```

11. 按下**Ctrl + C**索引鍵，結束 [狀態] 頁面。 您可以確認*IoT Edge 執行階段*提取容器正確輸入下列命令：

    ```bash
        sudo docker ps
    ```

12. 具有兩 （2） 容器的清單應該會出現。 這些是會自動建立 （edgeAgent 和 edgeHub） 時，IoT 中樞服務的預設模組。 一旦您建立及部署您自己的模組時，它們會出現在此清單中，預設的下方。

## <a name="chapter-6---install-the-extensions"></a>章節 6-安裝擴充功能

> [!IMPORTANT]
> 接下來的幾章 (6-9) 會在您的 Windows 10 電腦上執行。

1. 開啟**VS Code**。

2. 按一下 [**延伸模組**（正方形）] 按鈕在左側列的 VS Code 中，以開啟**擴充功能面板**。

3. 搜尋並安裝，下列延伸模組 （如圖所示）：

    1. Azure IoT Edge
    2. Azure IoT 工具組
    3. Docker   

    ![建立您的容器](images/AzureLabs-Lab313-24.png)

4. 一旦安裝擴充功能之後，請關閉並重新開啟 VS Code。

5. VS Code 開啟一次，然後瀏覽至**檢視 > 整合式終端機**。

6. 您現在將會安裝**Cookiecutter**。 在終端機中執行下列 bash 命令：

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!提示] 如果您無法使用此命令： 
    >1. 重新啟動 VS Code 中，和/或您的電腦。
    >2. 可能需要切換**VS Code 終端機**至您已安裝 Python，也就是使用一個**Powershell** （尤其是如果您的電腦上已安裝的 Python 環境）。 終端機開啟之後，您會發現終端機右邊的下拉式功能表。
     ![建立您的容器](images/AzureLabs-Lab313-24b.png) 
    >3. 請確定**Python**安裝路徑新增為**環境變數**您的電腦上。 Cookiecutter 應該是相同的位置路徑的一部分。 請遵循此[環境變數的詳細資訊的連結](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)， 

7. 一次**Cookiecutter**已完成安裝，您應該重新啟動您的電腦，以便**Cookiecutter**可辨識的命令，您的系統環境中。

## <a name="chapter-7---create-your-container-solution"></a>第 7-建立您的容器解決方案

此時，您需要建立容器，要推入的模組，與*Container Registry*。 一旦您已推送您的容器，您將使用*IoT 中樞 Edge*將其部署到您的裝置，正在執行的服務*IoT Edge 執行階段*。

1. 從 VS Code 中，按一下**檢視 > 命令選擇區**。

2. 在 選擇區中，搜尋並執行**Azure IoT Edge:新的 Iot Edge 方案**。

3. 瀏覽至您想要用來建立您的方案的位置。 按下**Enter**金鑰，才能接受位置。

4. 為您的方案中的名稱。 按下**Enter**金鑰，來確認您提供的名稱。

5. 現在系統會提示您選擇您的解決方案範本架構。 按一下  **Python 模組**。 按下**Enter**金鑰，來確認這項選擇。

6. 為您的模組名稱。 按下**Enter**金鑰，來確認您的模組名稱。 請務必記下 （與您的 「 記事本 」） 的模組名稱，以便稍後使用。

7. 您會發現預先建置*Docker 映像儲存機制*調色盤上，即可顯示位址。 它看起來像：

    **localhost:5000 /-NAME 您模組-**。 

8. 刪除**localhost:5000**，並在其位置插入*Container Registry* **登入伺服器**位址，您已記下建立時**容器登錄服務**([在步驟 8，第 2 章](#chapter-2---the-container-registry-service))。 按下**Enter**金鑰，才能確認該位址。

9. 此時，會建立包含 Python 模組的範本的方案和其結構會顯示在**瀏覽 索引標籤**，VS Code 中，在畫面左側。 如果**瀏覽 索引標籤**是未開啟，您可以開啟它依序按一下左側列中的最上層的按鈕。

    ![建立您的容器](images/AzureLabs-Lab313-25.png)

10. 本章中，最後一個步驟是按一下並開啟 **.env 檔案**，從**瀏覽 索引標籤**，並新增您*Container Registry* **的使用者名稱**並**密碼**。 Git 會忽略此檔案，但於建置容器，將設定認證以存取**容器登錄服務**。

    ![建立您的容器](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>第 8 章-編輯您的容器解決方案

您現在將完成容器解決方案，藉由更新下列檔案：

- *主<span></span>.py* python 指令碼。
- *requirements.txt*。
- *deployment.template.json*。
- *Dockerfile.amd64*

您接著會建立*映像*資料夾中，python 指令碼來檢查要比對的映像您*自訂視覺模型*。 最後，您將在其中加入*labels.txt*檔案，以協助讀取您的模型，而*model.pb*檔案，這是您的模型。

1. 使用 VS Code 開啟、 瀏覽至您的模組資料夾，並尋找呼叫的指令碼**主要<span></span>.py**。 按兩下以開啟它。

2. 刪除之檔案的內容，並插入下列程式碼：

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  開啟檔案**requirements.txt**，並以其取代為下列內容：

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  開啟檔案**deployment.template.json**，並以取代其內容的下列指導方針如下：

    1. 因為您會有自己唯一的的 JSON 結構，您必須手動編輯 （而非複製範例）。 若要方便使用，請使用下列映像做為指南。
    2. 看起來與您，不同的區域，但您**不應該變更為 反白顯示的黃色**。
    3. **若要刪除，您需要的各節會反白顯示的紅色。**
    4. 請務必刪除正確的括號，並移除逗號。

        ![建立您的容器](images/AzureLabs-Lab313-27.png)

    5. 已完成的 JSON 看起來如下圖所示 (不過，使用唯一的差異：*名稱的使用者名稱/密碼/模組/模組參考*):

        ![建立您的容器](images/AzureLabs-Lab313-28.png)

5.  開啟檔案**Dockerfile.amd64**，並以其取代為下列內容：

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  以滑鼠右鍵按一下下方的資料夾**模組**(會有您在先前; 所提供的名稱在範例中進一步向下，它會呼叫*pythonmodule*)，然後按一下 **新資料夾**. 將資料夾命名**映像**。

7.  在資料夾中，新增一些映像包含滑鼠或鍵盤。 這些是將 Tensorflow 模型所分析的映像。

    > [!WARNING]
    > 如果您使用您自己的模型，您必須變更以反映您自己的模型資料。

8.  您現在需要擷取**labels.txt**並**model.pb**從 [模型] 資料夾，您先前下載的檔案 (或從您自己建立**Custom Vision Service**)，在[第 1 章](#chapter-1---retrieve-the-custom-vision-model)。 檔案之後，請將它們放在您的解決方案，以及其他檔案。 最後的結果看起來應該類似下面的影像：

    ![建立您的容器](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>第 9 章-封裝做為容器解決方案

1.  您現在已準備好將檔案 「 套件 」 做為容器並將資料推送至您**Azure Container Registry**。 在 VS Code 中，開啟*整合式終端機*(**檢視 > 整合式終端機 / CTRL + '**)，並使用下列這一行加入登入**Docker** (替代值命令的認證與您**Azure Container Registry (ACR)**):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. 檔案上按一下滑鼠右鍵**deployment.template.json**，然後按一下**建置 IoT Edge 方案**。 此建置程序需要一段時間 （取決於您的裝置），因此請準備好等候。 建置程序完成之後， **deployment.json**檔案將已建立新資料夾，稱為內**config**。

    ![建立部署](images/AzureLabs-Lab313-30.png)

3. 開啟**命令調色盤**再次強調，並搜尋**Azure:登入**。 遵循提示使用您的 Azure 帳戶認證;VS Code 會為您提供的選項*複製並開啟*，這將會複製您很快就會需要並開啟預設網頁瀏覽器的裝置程式碼。 當系統詢問，貼上的裝置程式碼，來驗證您的電腦。

    ![複製並開啟](images/AzureLabs-Lab313-31.png)

4. 一次簽署在您會注意到，在下方*瀏覽* 面板中，呼叫的新區段**Azure IoT 中樞裝置**。 按一下以展開此區段。

    ![邊緣裝置](images/AzureLabs-Lab313-32.png)

5. 如果您的裝置是不在這裡，您必須以滑鼠右鍵按一下*Azure IoT Hub Devices*，然後按一下**設定 IoT 中樞連接字串**。 然後您會看到所**命令調色盤**（在 VS Code 的頂端），將會提示您輸入您*連接字串*。 這是*連接字串*您記下的結尾[第 3 章](#chapter-3---the-iot-hub-service)。 按下**Enter**金鑰，當您複製中的字串。    

6. 您的裝置應該載入，而且會出現。 裝置名稱上按一下滑鼠右鍵，然後按一下 **的單一裝置的 建立部署**。

    ![建立部署](images/AzureLabs-Lab313-33b.png)

7. 您會收到*檔案總管*提示字元中，您可以瀏覽至**config**資料夾，然後再選取**deployment.json**檔案。 選取該檔案中，按一下**選取 [Edge 部署資訊清單**] 按鈕。

    ![建立部署](images/AzureLabs-Lab313-34.png)

8. 現在您已提供您**IoT 中樞服務**與資訊清單，才能部署為模組，您的容器，從您**Azure Container Registry**，以有效地將它部署至您的裝置。

9. 若要檢視從您的裝置傳送到 IoT 中樞的訊息，再按一下滑鼠右鍵在您的裝置名稱，在**Azure IoT 中樞裝置**區段中**總管**] 面板，然後按一下 [**開始監視D2C 訊息**。 從您的裝置所傳送的訊息應該會出現在 VS 終端機中。 請耐心等候，因為這可能需要一些時間。 請參閱下一章中的偵錯，以及檢查部署是否成功。

此模組中的映像之間會現在逐一查看**映像**資料夾和分析系統，與每個反覆項目。 這是明顯只是示範如何取得基本的機器學習服務模型在 IoT Edge 裝置環境中工作。 

若要擴充此範例的功能，您可以繼續透過數種方式。 一種方法可以包括一些程式碼在容器中，會擷取從網路攝影機，連線到裝置，並將影像儲存映像資料夾中的相片。 

另一種方式可能複製映像從 IoT 裝置加入至容器。 實用的方法是在 IoT 裝置 （如果您想要自動化程序，或許是小型的應用程式無法執行作業） 的終端機中執行下列命令。 您可以從您的檔案儲存所在的資料夾位置以手動方式執行來測試此命令：

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>第 10 章-偵錯 IoT Edge 執行階段

以下是命令列和秘訣，可協助您監視和偵錯的傳訊活動的清單*IoT Edge 執行階段*，從您**Ubuntu 裝置**。 

- 請檢查*IoT Edge 執行階段*藉由執行下列命令列的狀態：

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > 按下時，請記得**Ctrl + C**，以完成檢視狀態。

- 列出目前已部署的容器。 如果*IoT 中樞服務*有容器成功部署，則會顯示藉由執行下列命令列：

    ```bash
        sudo iotedge list
    ```

    或

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > 以上是檢查是否您的模組是否已成功部署，就會出現在清單中的好方法否則，您將**僅**請參閱*edgeHub*並*edgeAgent*。

- 若要顯示容器的程式碼記錄檔，請執行下列命令列：

    ```bash
        journalctl -u iotedge
    ```

**用來管理 IoT Edge 執行階段的有用命令：**

-  若要刪除主應用程式中的所有容器：

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  若要停止*IoT Edge 執行階段*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>第 11-建立表格服務 

瀏覽回到 Azure 入口網站，您將在其中建立儲存體資源建立 Azure 資料表服務。

1. 如果您尚未登入，登入[Azure 入口網站](https://portal.azure.com)。

2. 登入之後，按一下**建立資源**，在左上角，並搜尋**儲存體帳戶**，然後按**Enter**金鑰，才能開始搜尋。

3. 之後它會顯示，按一下 **儲存體帳戶-blob、 檔案、 資料表、 佇列**從清單中。

    ![搜尋儲存體帳戶](images/AzureLabs-Lab313-35.png)

4. 新的頁面將提供的描述**儲存體帳戶**服務。 在此提示的左下方，按一下**建立**按鈕，以建立這個執行個體服務。

    ![建立儲存體執行個體](images/AzureLabs-Lab313-36.png)

5. 一旦您按下**建立**，面板會顯示：

    1. 插入您想要**名稱**此服務執行個體 (*必須全部小寫*)。

    2. 針對**部署模型**，按一下**Resource manager**。

    3. 針對**帳戶種類**，使用下拉式功能表中，按一下**儲存體 (一般用途 v1)**。

    4. 按一下適當**位置**。
    
    5. 針對**複寫**下拉式功能表中，按一下**讀取-存取-異地備援儲存體 (RA-GRS)**。

    6. 針對**效能**，按一下**標準**。

    7. 內**需要安全傳輸**區段中，按一下**停用**。

    8. 從**訂用帳戶**下拉式功能表中，按一下適當的訂用帳戶。

    9. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理的 Azure 資產的集合計費。 建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。

        > 如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 離開**虛擬網路**作為**停用**，如果這是您的選項。

    11. 按一下 [建立] 。

        ![填入儲存體詳細資料](images/AzureLabs-Lab313-37.png)

6. 一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

7. 通知會出現在入口網站中，一旦建立服務執行個體。 按一下通知，以探索新的服務執行個體。

    ![新的儲存體通知](images/AzureLabs-Lab313-38.png)

8. 按一下 [**移至資源**按鈕，在該通知上方，而且您將會進入您新的儲存體服務執行個體概觀] 頁面。

    ![前往資源](images/AzureLabs-Lab313-39.png)

9. 從 [概觀] 頁面的右手邊的側邊，按一下**資料表**。
    
    ![資料表](images/AzureLabs-Lab313-40.png)

10. 在右側面板會變更以顯示**表格服務**資訊，您要在其中加入新的資料表。 依序按一下 **+ 資料表**左上角的按鈕。

    ![開啟資料表](images/AzureLabs-Lab313-41.png)

11. 新的頁面將會顯示，您要在其中輸入**資料表名稱**。 這是您用來在您的應用程式，在後續的章節 （建立函數應用程式和 Power BI） 中的資料所參考的名稱。 插入**IoTMessages**做為名稱 （您也可以選擇自己的圖片，只要記住它稍後在本文件中使用時），按一下 **確定**。 

12. 一旦建立新的資料表，您將能夠看到它內**表格服務**頁面 （位於底部）。

    ![建立新資料表](images/AzureLabs-Lab313-42.png)  

13. 現在，按一下**存取金鑰**並採取一份**儲存體帳戶名稱**並**金鑰**（使用您在 [記事本]），您將使用這些值稍後在本課程中，建立時**Azure 函數應用程式**。

    ![建立新資料表](images/AzureLabs-Lab313-43.png) 

14. 同樣地，使用左邊的面板捲動到 *表格服務*區段，然後按一下**資料表**(或**瀏覽資料表**，在較新的入口網站中)，並採取一份**資料表 URL** （使用您在 記事本）。 連結資料表時，您會稍後在本課程中，使用此值您**Power BI**應用程式。

    ![建立新資料表](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>第 12 章-完成 Azure 資料表

既然您**表格服務**儲存體帳戶是否已設定，就可以開始將資料加入至它，將會用來儲存和擷取資訊。 編輯您的資料表可透過**Visual Studio**。

1. 開啟**Visual Studio** (**不**Visual Studio Code)。

2. 從功能表中，按一下**檢視 > Cloud Explorer**。

    ![開啟 cloud explorer](images/AzureLabs-Lab313-45.png)

3. **Cloud Explorer**會開啟為停駐項目 （耐心等候，因為載入可能會花費的時間）。

    > [!WARNING] 
    > 如果您用來建立訂用帳戶您*儲存體帳戶*不可見，請確定您已： 
    > - 與您在 Azure 入口網站使用相同的帳戶登入。
    > - 從 （您可能需要從您的帳戶設定套用篩選） 的 [帳戶管理] 頁面中選取您的訂用帳戶：  
    >
    >   ![尋找訂用帳戶](images/AzureLabs-Lab313-46.png)

4. Azure 雲端服務將會顯示。 尋找**儲存體帳戶**按一下箭號左側，展開您的帳戶。

    ![開啟儲存體帳戶](images/AzureLabs-Lab313-47.png)

5. 一旦展開時，您新建立**儲存體帳戶**應該可用。 按一下您的儲存體中，左邊的箭號之後，會展開，然後尋找**資料表**，按一下，以顯示旁的箭號**資料表**在最後一章中所建立。 按兩下您**資料表**。

6. 您的資料表將會開啟您的 Visual Studio 視窗中央。 按一下 [資料表] 圖示，以 **+** （加上） 在其上。

    ![加入新的資料表](images/AzureLabs-Lab313-48.png)

7. 接著會出現視窗提示要*新增實體*。 雖然會有三個屬性，您將建立一個的實體。 您將會發現*PartitionKey*並*RowKey*已提供，這些資料表所用來尋找您的資料。 

    ![資料分割和資料列索引鍵](images/AzureLabs-Lab313-49.png)

8. 更新下列值：

    - 名稱：**PartitionKey**，值：**PK_IoTMessages** 

    - 名稱：**RowKey**，值：**RK_1_IoTMessages** 

9. 然後，按一下 **將屬性加入**(至左下方的*加入實體*視窗)，並新增下列屬性：

    - **MessageContent**，作為*字串*，將值保留為空白。

10. 您的資料表應符合下面的影像中的一個：

    ![加入正確的值](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > 實體包含資料列索引鍵中的數字 1 的原因的原因是因為您可能想要新增更多的訊息，您想要實驗應該使用本課程。

11. 按一下 **確定**完畢時。 現在準備好可供您的資料表。

## <a name="chapter-13---create-an-azure-function-app"></a>第 13-建立 Azure 函式應用程式 

就可以立即開始建立*Azure 函數應用程式*，則會藉由呼叫*IoT 中樞服務*儲存*IoT Edge*裝置中的訊息**資料表**服務，您在上一章中建立。

首先，您必須建立一個檔案，可讓您的 Azure 函式，將您所需的程式庫。

1.  開啟**記事本**(按下*Windows 鍵*，和型別*記事本*)。

    ![開啟 [記事本]](images/AzureLabs-Lab313-51.png)

2.  使用 「 記事本 」 開啟，在其中插入以下的 JSON 結構。 完成後，會將它儲存為您的桌面上**project.json**。 此檔案會定義您的函式會使用的程式庫。 如果您已使用 NuGet，它看起來會類似。
    
    > [!WARNING]
    > 請務必確認名稱正確;請確定它並未**沒有.txt**副檔名。 如需參考，請參閱以下內容：
    >
    > ![儲存的 JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  登入[Azure 入口網站](https://portal.azure.com)。

4.  一旦您登入，按一下**建立資源**在左上角，，然後搜尋**函式應用程式**，然後按**Enter**来搜尋的索引鍵。 按一下 *函式應用程式*從結果中，若要開啟新的面板。

    ![搜尋函式應用程式](images/AzureLabs-Lab313-53.png)

5.  新的面板會提供的描述**函式應用程式**服務。 在此面板的左下方，按一下**建立**按鈕，以建立與這個關聯服務。

    ![函式應用程式執行個體](images/AzureLabs-Lab313-54.png)

6.  一旦您按下**建立**，填入下列：

    1. 針對**應用程式名稱**，插入您想要的名稱，此服務執行個體。

    2. 選取 **訂用帳戶**。

    3. 選取定價層適合您，如果這是第一次建立**函式應用程式服務**，免費層應該是您可以使用。

    4. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理的 Azure 資產的集合計費。 建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。

        > 如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 針對**OS**，按一下 Windows，因為這是預期的平台。

    6. 選取 **主控方案**(使用本教學課程**取用方案**。

    7. 選取 **位置**（上一個步驟中選擇您已建立的儲存體相同的位置）

    8. 針對**儲存體**一節**您必須選取您在上一個步驟中建立的儲存體服務**。

    9. 您不需要*Application Insights*在此應用程式，因此您將它保留**關閉**。

    10. 按一下 [建立] 。

        ![建立新的執行個體](images/AzureLabs-Lab313-55.png)

7.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

8.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![新的通知](images/AzureLabs-Lab313-56.png)

9.  部署成功之後，按一下 通知 （完成）。

10. 按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 

    ![前往資源](images/AzureLabs-Lab313-57.png)

11. 在新的面板的左側，按一下 **+** （加號） 旁的圖示*函式*，以建立新的函式。

    ![新增新的函式](images/AzureLabs-Lab313-58.png)

12. 在中央窗格中，**函式**建立視窗會出現。 此外，向下捲動，然後按一下**自訂函式**。

    ![自訂函式](images/AzureLabs-Lab313-59.png)

13. 下一步 頁面上，直到您找到捲動**IoT 中樞 （事件中樞）**，然後按一下它。

    ![自訂函式](images/AzureLabs-Lab313-60.png)

14. 在  **IoT 中樞 （事件中樞）** 刀鋒視窗中，將**語言**來**C#** ，然後按一下**新**。

    ![自訂函式](images/AzureLabs-Lab313-61.png)

15. 在視窗中會出現，請確定**IoT 中樞**已選取和名稱*IoT 中樞*欄位對應的名稱取代您*IoT 中樞服務*您具有先前所建立 ([在步驟 8，第 3 章](#chapter-3---the-iot-hub-service))。 然後按一下**選取** 按鈕。

    ![自訂函式](images/AzureLabs-Lab313-62.png)

16. 回到**IoT 中樞 （事件中樞）** 刀鋒視窗中，按一下**建立**。

    ![自訂函式](images/AzureLabs-Lab313-63.png)

17. 您將會重新導向至函式編輯器。

    ![自訂函式](images/AzureLabs-Lab313-64.png)

18. 刪除所有程式碼，並將它取代為下列：

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. 變更下列變數，讓它們對應至適當的值 (**表格**並**儲存體**的值，從[步驟 11 日及 13 日分別第 11 章](#chapter-11---create-table-service))，您會在中找到您**儲存體帳戶**:

    - **tableName**，名稱與您**表格**位於您**儲存體帳戶**。
    - **tableURL**，使用的 URL 您**表格**位於您**儲存體帳戶**。
    - **storageAccountName**，對應的名稱值的名稱與您**儲存體帳戶**名稱。
    - **storageAccountKey**，您已取得您先前建立的儲存體服務中的金鑰。

    ![自訂函式](images/AzureLabs-Lab313-65.png)

20. 中位置的程式碼，請按一下**儲存**。

21. 接下來，按一下 **\<** （箭頭） 圖示，在頁面的右手邊。

    ![自訂函式](images/AzureLabs-Lab313-66.png)

22. 從右邊的窗格中將投影片。 在該面板中，按一下**上傳**，以及*檔案瀏覽器*會出現。

23. 瀏覽至，然後按一下 []， **project.json**中建立的檔案**記事本**之前，然後按一下 [**開啟**] 按鈕。 此檔案會定義您的函式會使用的程式庫。

    ![自訂函式](images/AzureLabs-Lab313-67.png)

24. 檔案已上傳時，它會出現在右側面板。 按一下將內開啟它**函式**編輯器。 它必須看起來**完全**與下圖相同。

    ![自訂函式](images/AzureLabs-Lab313-68.png)

25. 此時就很好測試您的函式的功能，將訊息儲存在您*資料表*。 在右上方的 [] 視窗中，按一下**測試**。

    ![自訂函式](images/AzureLabs-Lab313-69.png)

26. 將訊息插入上**要求本文**，如上顯示的影像上方，然後按一下**執行**。 

27. 此函式會執行，顯示的結果狀態 (您會注意到綠色**狀態 202 已接受**上面*輸出*視窗中，這表示它已成功的呼叫):

    ![輸出結果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>第 14 章-檢視作用中的訊息

如果您現在可以開啟 Visual Studio (**未**Visual Studio Code)，您可以將視覺化您測試訊息的結果，因為它會儲存在*MessageContent*區域的字串。

![自訂函式](images/AzureLabs-Lab313-71.png)

表格服務和函式應用程式就地，Ubuntu 裝置上的訊息會出現在您*IoTMessages*資料表。 如果尚未執行，同樣地，啟動您的裝置，您將能夠看到結果訊息，從您的裝置和您的資料表內的模組，使用 Visual Studio *Cloud Explorer*。

![將資料視覺化](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>第 15 章-Power BI 設定

若要從您的 IOT 裝置會設定將資料視覺化**Power BI** （桌面版），要從中收集資料*資料表*您剛才建立的服務。 *HoloLens*版本的 Power BI 會接著使用該資料以視覺化方式檢視結果。

1.  開啟 Windows 10 上的 Microsoft Store 並搜尋**Power BI Desktop**。

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  下載應用程式。 一旦下載完成，請開啟它。

3.  登入*Power BI*與您**Microsoft 365 帳戶**。 您可能會重新導向至瀏覽器中，登入。 一旦您已註冊，返回 Power BI 應用程式，並再次登入。

4.  按一下 **取得資料**，然後按一下**更多...**.

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  按一下  **Azure**， **Azure 資料表儲存體**，然後按一下**Connect**。

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  系統會提示您插入**adresa URL Tabulky**稍早收集到的 ([在步驟 13 小時，共 11 章](#chapter-11---create-table-service))，建立您的資料表服務時。 在插入 URL 之後, 刪除路徑參考到資料表"子資料夾 」 （這是 IoTMessages，本課程中） 的一部分。 最後的結果應該如下圖所示。 然後按一下**確定**。

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  系統會提示您插入**儲存體金鑰**您記下 ([的步驟 11 第 11 章](#chapter-11---create-table-service)) 先前在建立您的資料表儲存體。 然後按一下**Connect**。

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. A**導覽器 面板**將會顯示，勾選您表旁邊的方塊，然後按一下**負載**。

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. Power BI 中，現在已載入您的資料表，但需要的查詢，以在其中顯示的值。 若要這樣做，請以滑鼠右鍵按一下資料表名稱，其位於**欄位面板**螢幕的右上方。 然後按一下**編輯查詢**。

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. A **Power Query 編輯器**會開啟新視窗，顯示您的資料表。 按一下 上一字**記錄**內*內容*資料表資料行，以視覺化方式檢視您儲存的內容。

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. 按一下  **Into 資料表**，在視窗的左上方。 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. 按一下 **關閉並套用**。

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. 在載入此查詢中，完成後**欄位面板**，在畫面的右側，勾選 參數對應的方塊**名稱**並**值**至以視覺化方式檢視**MessageContent**資料行內容。

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. 按一下 **藍色的磁碟片圖示**在左上方的 儲存您所選擇的資料夾中的工作 視窗。

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. 您現在可以按一下 [發行] 按鈕上, 傳至您的工作區的資料表。 出現提示時，按一下**我的工作區**然後按一下*選取*。 等候它顯示在提交的成功的結果。

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> 下一個章節是特定的 HoloLens。 Power BI 目前不提供為沈浸式應用程式，不過您可以在 Windows 混合實境入口網站 （也稱為 Cliff 房屋） 來執行桌面版本透過桌面應用程式。

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>第 16 章-HoloLens 上顯示 Power BI 資料

1. 在您的 HoloLens 上登入**Microsoft Store**，依序點選應用程式清單中的圖示。

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. 搜尋，然後下載**Power BI**應用程式。

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. 開始**Power BI**從您的應用程式清單。 

4. **Power BI**可能會要求您登入您**Microsoft 365 帳戶**。

5. 一次，應用程式內的工作區應該預設會顯示在下圖所示。 如果，不會發生，只要按一下視窗左邊的工作區圖示。

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>您已完成您的 IoT 中樞應用程式

恭喜，您已成功建立 IoT 中樞服務，以模擬的虛擬機器的 Edge 裝置。 您的裝置可以進行通訊的機器學習模型到 Azure 資料表服務，透過 Azure 函式應用程式，這是讀取到 Power BI，並以視覺化方式檢視內 Microsoft HoloLens 的結果。
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

展開 儲存在資料表中的訊息結構，則會顯示為圖形。 您可能想要收集更多資料，並將它儲存在相同資料表中，稍後再顯示。

### <a name="exercise-2"></a>練習 2

建立其他 IoT 面板，以便它可以透過分析攝影機擷取映像部署至 「 相機擷取 」 模組。
