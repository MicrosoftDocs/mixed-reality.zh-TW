---
title: MR 和 Azure 311-Microsoft Graph
description: 完成這個課程來了解如何使用 Microsoft Graph，並連接驅動生產力，在混合的實境應用程式中的資料。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 microsoft graph、 hololens、 沉浸式 vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694530"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

# <a name="mr-and-azure-311---microsoft-graph"></a>MR 和 Azure 311-Microsoft Graph

在此課程中，您將了解如何使用*Microsoft Graph*登入您使用安全的驗證，在混合的實境應用程式中的 Microsoft 帳戶。 您接著擷取並顯示應用程式介面中的已排程的會議。

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph*是一組設計來啟用對許多 Microsoft 服務存取的 Api。 Microsoft 說明 Microsoft Graph 為連線的關聯性，資源的矩陣，這表示它可讓應用程式存取各式各樣的已連線的使用者資料。 如需詳細資訊，請瀏覽[Microsoft Graph 頁面](https://developer.microsoft.com/graph)。

開發將包含建立使用者以注視，然後點選 球體，將會提示使用者安全地登入 Microsoft 帳戶的指示，應用程式。 一旦登入其帳戶，使用者將能夠看到一份排程一天的會議。

完成本課程之後，您會有混合的實境 HoloLens 應用程式，可以執行下列作業：

1.  點選 使用點選手勢，將會提示使用者登入 Microsoft 帳戶 （移出登入，然後再移回至應用程式的應用程式） 的物件。
2.  檢視排程一天的會議的清單。 

在您的應用程式，則您對於如何將整合結果進行設計。 本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。 它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 311:Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程專為具有基礎經驗的 Unity 開發人員和C#。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。 中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。

我們建議下列的硬體和軟體這堂課程：

- 開發電腦
- [Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式
- Azure 的安裝程式和 Microsoft Graph 資料擷取的網際網路存取
- 有效**的 Microsoft 帳戶**（個人或公司/學校）
- 一些會議排定為目前日期，使用相同的 Microsoft 帳戶

### <a name="before-you-start"></a>開始之前

1.  若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。
2.  設定並測試您的 HoloLens。 如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。 

校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。

如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>第 1 層應用程式註冊入口網站中建立您的應用程式

一開始，您必須建立並註冊您的應用程式**應用程式註冊入口網站**。

您也會在這一章中找到服務金鑰，可讓您對進行呼叫*Microsoft Graph*來存取您帳戶的內容。

1.  瀏覽至[Microsoft 應用程式註冊入口網站](https://apps.dev.microsoft.com)並使用您的 Microsoft 帳戶登入。 一旦您已登入，您將會重新導向至**應用程式註冊入口網站**。

2.  在 **我的應用程式**區段中，按一下按鈕**新增應用程式**。

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > **應用程式註冊入口網站**可以看起來不同，取決於是否您先前用過*Microsoft Graph*。 以下螢幕擷取畫面顯示這些不同的版本。

3.  針對您的應用程式，然後按一下 新增名稱**建立**。

    ![](images/AzureLabs-Lab311-03.png)

4.  一旦建立應用程式，您將重新導向到的應用程式的主頁面。 複製**應用程式識別碼**請務必記下此值為安全的地方，您將使用它很快就在您的程式碼。

    ![](images/AzureLabs-Lab311-04.png)

5.  在 **平台**區段中，請確定**原生應用程式**隨即出現。 如果*未*上按一下**新增平台**，然後選取**原生應用程式**。

    ![](images/AzureLabs-Lab311-05.png)

6.  在相同的頁面和稱為區段，向下捲動**Microsoft Graph 權限**您必須新增應用程式的其他權限。 按一下 **新增**旁**委派的權限**。

    ![](images/AzureLabs-Lab311-06.png)

7.  由於您希望您的應用程式存取使用者的行事曆，核取方塊稱為**Calendars.Read**然後按一下**確定**。

    ![](images/AzureLabs-Lab311-07.png)

8.  捲動到底部，按一下**儲存** 按鈕。

    ![](images/AzureLabs-Lab311-08.png)

9.  會確認您的儲存，以及您可以登出**應用程式註冊入口網站**。

## <a name="chapter-2---set-up-the-unity-project"></a>第 2 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟*Unity*然後按一下**新增**。

    ![](images/AzureLabs-Lab311-09.png)

2.  您需要提供 Unity 專案名稱。 插入**MSGraphMR**。 請確定已設定的專案範本**3D**。 設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![](images/AzureLabs-Lab311-10.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯** > **喜好設定**並從新的視窗，然後瀏覽至**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![](images/AzureLabs-Lab311-11.png)

4.  移至**檔案** > **組建設定**，然後選取**通用 Windows 平台**，然後按一下**切換平台**按鈕，以套用您的選擇。

    ![](images/AzureLabs-Lab311-12.png)

5.  當您依然在**檔案** > **組建設定**，請確定：

    1. **裝置為目標**設為**HoloLens**
    2. **建置型別**設為**D3D**
    3. **SDK**設為**最新安裝**
    4. **Visual Studio 版本**設為**最新安裝**
    5. **建置並執行**設為**本機電腦**
    6. 儲存場景，並將它新增至組建。

        1. 做法是選取**加入開啟的場景**。 儲存視窗會出現。

            ![](images/AzureLabs-Lab311-13.png)

        2. 這與任何未來、 場景中建立新的資料夾。 選取 **新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

            ![](images/AzureLabs-Lab311-14.png)

        3. 開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中輸入**MR_ComputerVisionScene**，然後按一下**儲存**.

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > 請注意，您必須先儲存您的 Unity 場景中*資產*資料夾，因為它們必須是與 Unity 專案相關聯。 建立場景資料夾 （和其他類似的資料夾） 是建構的 Unity 專案的典型方式。

    7.  剩餘的設定，*組建設定*，應保持為預設值，現在。

6.  中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。 

    ![](images/AzureLabs-Lab311-16.png)

7. 在此窗格中，少數設定需要驗證：

    1. 在 [**其他設定**] 索引標籤：

        1.  **指令碼** **執行階段版本**應該**實驗性**（.NET 4.6 對等），這會觸發程序需要重新啟動編輯器。

        2. **指令碼後端**應該是 **.NET**

        3. **API 相容性層級**應該是 **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  內**發佈設定**索引標籤之下**功能**，檢查：

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，檢查**虛擬實境支援**，請確定**Windows Mixed RealitySDK**加入。

        ![](images/AzureLabs-Lab311-19.png)

8.  回到*Build Settings*， *UnityC#專案*不再呈現灰色，要檢查這旁邊的核取方塊。

9.  關閉*組建設定*視窗。

10.  儲存您的場景和專案 (**檔案** > **儲存場景檔案** > **儲存專案**)。

## <a name="chapter-3---import-libraries-in-unity"></a>第 3 章-在 Unity 中的匯入程式庫

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)，它匯入到您的專案做為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 5 章](#chapter-5---create-meetingsui-class)。

若要使用*Microsoft Graph*您需要進行的 Unity 中使用的**Microsoft.Identity.Client** DLL。 您可使用 Microsoft Graph SDK，不過，它就需要加入的 NuGet 套件之後建置 Unity 專案 （亦即編輯專案建置後）。 會被視為直接將 Unity 匯入必要的 Dll 的工作變得更容易。

> [!NOTE]
> 這需要匯入之後重新設定外掛程式的 Unity 中目前沒有已知的問題。 這些步驟 (4-在這一節中的 7) 將不再需要解決的 bug 之後。

若要匯入*Microsoft Graph*到您自己的專案[MSGraph_LabPlugins.zip 檔案下載](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)。 此套件已建立版本測試過的程式庫使用。

如果您想要深入了解如何將自訂 Dll 新增至您的 Unity 專案[請依循下列連結](https://docs.unity3d.com/Manual/UsingDLL.html)。

若要匯入套件：

1.  使用將 Unity 套件新增至 Unity**資產** > **匯入封裝** > **自訂封裝**功能表選項。 選取您剛才下載的封裝。

2.  在 **匯入 Unity 封裝**方塊會顯示。 請確認所有項目底下 （而且包括）**外掛程式**已選取。

    ![](images/AzureLabs-Lab311-20.png)

3.  按一下 **匯入**按鈕以新增至您的專案項目。

4.  移至**MSGraph**下的資料夾**外掛程式**中*專案] 面板*，然後選取 [外掛程式呼叫**Microsoft.Identity.Client**。

    ![](images/AzureLabs-Lab311-21.png)

5.  具有*外掛程式*選取，請確認**任何平台**未核取，則確定**WSAPlayer**也是未選取，然後按一下 **套用**. 這只是要確認已正確設定檔案。

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > 標示這些外掛程式會設定它們僅適用於在 Unity 編輯器中。 有一組不同的專案會匯出從 Unity 做為通用 Windows 應用程式後要使用 WSA 資料夾中的 Dll。

6.  接下來，您必須開啟**WSA**資料夾內**MSGraph**資料夾。 您會看到您剛才設定的相同檔案的複本。 選取檔案，然後在偵測器：

    -   請確認**任何平台**是**取消核取**，且**只** **WSAPlayer**是**檢查**。

    -   請確定**SDK**設為**UWP**，並**指令碼的後端**設為**Dot Net**

    -   請確認**不會處理**是**檢查**。

        ![](images/AzureLabs-Lab311-23.png)

7.  按一下 **[套用]** 。

## <a name="chapter-4---camera-setup"></a>第 4 章-觀景窗設定

在這一章期間您將設定場景的 Main Camera:

1.  在 *階層面板*，選取**Main Camera**。

2.  選取之後，您將能夠看到所有的元件**Main Camera**中*Inspector*面板。

    1.  **相機物件**必須命名為**Main Camera** （請注意拼字 ！）

    2.  Main Camera**標記**必須設為**MainCamera** （請注意拼字 ！）

    3.  請確定**轉換的位置**設定為**0，0，0**

    4.  設定**清除旗標**到**純色**

    5.  設定**背景色彩**要相機元件**黑色，0 的 Alpha** **(十六進位的程式碼: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  中的最終物件結構*階層面板*應該類似下面的影像中所示：

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>第 5 章-建立 MeetingsUI 類別

您必須建立第一個指令碼**MeetingsUI**，它會負責裝載，並填入 （歡迎訊息、 指示和會議詳細資料） 的應用程式的 UI。

若要建立此類別：

1.  以滑鼠右鍵按一下**資產**中的資料夾 *[專案] 面板*，然後選取**建立** > **資料夾**。 將資料夾命名**指令碼**。

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  開啟**指令碼**資料夾，在該資料夾中，按一下滑鼠右鍵，**建立** >   **C#指令碼**。 指令碼命名**MeetingsUI。**

    ![](images/AzureLabs-Lab311-28.png)

3.  按兩下新**MeetingsUI**指令碼，以開啟它*Visual Studio*。

4.  插入下列命名空間：

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  類別內插入下列變數：

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  然後取代**start （)** 方法，並新增**Awake()** 方法。 在類別初始化時，這些將會呼叫：

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  加入負責建立方法*會議 UI*並填入目前的會議時要求：

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **刪除** **update （)** 方法，以及**儲存您的變更**傳回給 Unity 之前的 Visual Studio 中。 

## <a name="chapter-6---create-the-graph-class"></a>章節 6-建立圖形類別

下一步 以建立指令碼**Graph**指令碼。 此指令碼是負責驗證使用者，並擷取目前的日期，從使用者的行事曆排定的會議的呼叫。

若要建立此類別：

1.  按兩下**指令碼**資料夾，將它開啟。

2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。 指令碼命名**Graph**。

3.  按兩下要使用 Visual Studio 中開啟它的指令碼。

4.  插入下列命名空間：

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > 您會注意到此指令碼中的程式碼的部分包裝著[先行編譯指示詞](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)，這是為了避免與程式庫的問題，當建置 Visual Studio 方案。

5.  刪除**start （)** 並**update （)** 方法，因為它們不會使用。

6.  Outside **Graph**類別中，插入所需的還原序列化 JSON 物件，表示每日排定的會議的下列物件：

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  內部**Graph**類別中，新增下列變數：

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > 變更 **appId** 值，成為 **應用程式識別碼** 您記下在 **[第 1 章](#chapter-1---create-your-app-in-the-application-registration-portal)，步驟 4** 。 這個值應該是顯示在相同**應用程式註冊入口網站，** 在您的應用程式註冊頁面中。

8.  內**Graph**類別中，將方法加入**SignInAsync()** 並**AquireTokenAsync()** ，，會提示使用者插入的登入認證。

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  新增下列兩種方法：

    1.  **BuildTodayCalendarEndpoint()** ，哪些組建會指定日期和時間範圍內，已排程的會議中擷取的 URI。

    2.  **ListMeetingsAsync()** ，會要求從已排程的會議*Microsoft Graph*。

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. 您現在已完成**Graph**指令碼。 **儲存您的變更**傳回給 Unity 之前的 Visual Studio 中。

## <a name="chapter-7---create-the-gazeinput-script"></a>第 7-建立 GazeInput 指令碼

您現在會建立**GazeInput**。 這個類別會處理並追蹤使用者的視線，使用**Raycast**來自**Main Camera**，向前投影。

若要建立指令碼：

1.  按兩下**指令碼**資料夾，將它開啟。

2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。 指令碼命名**GazeInput**。

3.  按兩下要使用 Visual Studio 中開啟它的指令碼。

4.  變更命名空間程式碼，以符合下面其中一個，以及新增 ' **\[System.Serializable\]** ' 上述標記您**GazeInput**類別，以便它可以序列化：

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  內部**GazeInput**類別中，新增下列變數：

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  新增**CreateCursor()** 方法來建立場景中的 HoloLens 資料指標，並呼叫方法，從**start （)** 方法：

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  下列方法啟用視線 Raycast 和追蹤的焦點的物件。

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **儲存您的變更**傳回給 Unity 之前的 Visual Studio 中。

## <a name="chapter-8---create-the-interactions-class"></a>第 8-建立互動類別

您現在必須建立**互動**指令碼，也就是負責：

-   處理**點選**互動並**相機視線**，這可讓使用者互動的記錄檔中在場景中的 「 按鈕 」。

-   建立記錄檔中的使用者互動，場景中的 「 按鈕 」 物件。

若要建立指令碼：

1.  按兩下**指令碼**資料夾，將它開啟。

2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立** >   **C#指令碼**。 指令碼命名**互動**。

3.  按兩下要使用 Visual Studio 中開啟它的指令碼。

4.  插入下列命名空間：

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  變更的繼承**互動**從類別*MonoBehaviour*來**GazeInput**。

    ~~公用類別互動：MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  內部**互動**類別插入下列變數：

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  取代**啟動**方法; 請注意，它會覆寫方法，它會呼叫的 'base' 視線類別方法。 **Start （)** 類別初始化時，輸入辨識向註冊，並建立登入將會呼叫 *按鈕* 場景中：

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  新增 **CreateSignInButton()** 方法，它會具現化的登入 *按鈕* 場景中並設定其屬性：

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  新增**GestureRecognizer_Tapped()** 方法，這是回應*點選*使用者事件。

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **刪除** **update （)** 方法，然後**儲存您的變更**傳回給 Unity 之前的 Visual Studio 中。

## <a name="chapter-9---set-up-the-script-references"></a>第 9 章-設定指令碼參考

您必須將放在本章**互動**拖曳至指令碼**Main Camera**。 該指令碼會接著處理放置其他指令碼能所需的位置。

-  從**指令碼**資料夾中的 *[專案] 面板*，將指令碼**互動**至**Main Camera**物件，請參閱下圖。

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>第 10 章-設定標記

處理視線的程式碼，將使用的標記**SignInButton**若要識別哪些物件使用者將互動登入*Microsoft Graph*。

若要建立的標記：

1.  在 Unity 編輯器中按一下**Main Camera**中*階層面板*。

2.  在 [*偵測器] 面板*上按一下**MainCamera** *標記*開啟下拉式清單。 按一下**新增標記...**

    ![](images/AzureLabs-Lab311-30.png)

3.  按一下 [ **+** ] 按鈕。

    ![](images/AzureLabs-Lab311-31.png)

4.  寫入的標記名稱，作為**SignInButton**並按一下 [儲存]。

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>第 11 章-建置 Unity 專案至 UWP

此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。

1.  瀏覽至 *組建設定* (**檔案* > *建置設定**)。

    ![](images/AzureLabs-Lab311-33.png)

2.  如果您尚未，勾選**Unity C\#專案**。

3.  按一下 [建置]  。 將會啟動 unity**檔案總管**視窗中，您要建立，然後選取 建置到應用程式的資料夾。 現在，建立該資料夾並將它命名**應用程式**。 然後使用**應用程式**按一下 選取資料夾**選取資料夾**。

4.  Unity 會開始建置您的專案**應用程式**資料夾。

5.  一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。

## <a name="chapter-12---deploy-to-hololens"></a>第 12-部署到 HoloLens

若要部署 HoloLens 上：

1.  您將需要您 HoloLens IP 位址 （適用於遠端部署），並以確保您 HoloLens 處於**開發人員模式。** 請這樣做：

    1.  儘管穿著您 HoloLens，開啟**設定**。

    2.  移至**網路和網際網路** > **Wi-fi** > **進階選項**

    3.  附註**IPv4**位址。

    4.  接下來，瀏覽回到**設定**，然後**更新與安全性** > **適用於開發人員**

    5.  設定**上的開發人員模式**。

2.  瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。

3.  在 **方案組態**選取**偵錯**。

4.  在 **的方案平台**，選取**x86，遠端機器**。 系統會提示您插入**IP 位址**的遠端裝置 (HoloLens，在此情況下，記下)。

    ![](images/AzureLabs-Lab311-34.png)

5.  移至**建置**功能表，然後按一下 **部署方案**側載您 HoloLens 應用程式。

6.  您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！

## <a name="your-microsoft-graph-hololens-application"></a>您的 Microsoft Graph HoloLens 應用程式

恭喜，您所建立的混合的實境應用程式，利用 Microsoft Graph，來讀取和顯示使用者的行事曆資料。

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

使用 Microsoft Graph，以顯示使用者的其他資訊

-   使用者電子郵件 / 電話號碼] / [設定檔圖片

### <a name="exercise-1"></a>練習 1

實作語音控制瀏覽 Microsoft 的圖形使用者介面。
