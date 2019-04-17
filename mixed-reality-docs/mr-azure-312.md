---
title: MR 和 Azure 312-Bot 整合
description: 完成此課程來了解如何建立及部署 bot，使用 Microsoft Bot Framework v4，並與其通訊的混合的實境應用程式中。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 unity、 教學課程、 api、 電腦視景、 hololens、 沉浸式 vr microsoft bot framework v4、 web 應用程式 bot、 bot framework、 microsoft bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597078"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

# <a name="mr-and-azure-312-bot-integration"></a>MR 和 Azure 312:Bot 整合

在此課程中，您將學習如何建立並部署使用 Microsoft Bot Framework V4 bot，並透過 Windows Mixed Reality 應用程式與其通訊。 

![](images/AzureLabs-Lab312-00.png)

**Microsoft Bot Framework V4**是一組 Api 可提供開發人員工具來建置可擴充且可調整的 bot 應用程式。 如需詳細資訊，請瀏覽[Microsoft Bot Framework 頁面](https://dev.botframework.com/)或[V4 Git 存放庫](https://github.com/Microsoft/botbuilder-dotnet/wiki)。

完成本課程之後，您就會建置的 Windows Mixed Reality 應用程式，可以執行下列作業：

1. 使用**點選手勢**開始接聽使用者語音 bot。
2. 當使用者說過的項目 bot 會嘗試提供回應。
3. Bot 回覆文字顯示，bot，Unity 場景中靠近定位。

在您的應用程式，則您對於如何將整合結果進行設計。 本課程旨在教導您如何將 Azure 服務整合與您的 Unity 專案。 它是您的作業，以使用您從這個課程，以增強您的混合的實境應用程式所獲得的知識。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> MR 和 Azure 312:Bot 整合</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然這堂課程主要著重於 HoloLens，您也可以套用您在此課程 Windows Mixed Reality 沈浸式 (VR) 耳機來了解。 因為沈浸式 (VR) 耳機並沒有可存取的相機，您必須連線到您的 PC 外部相機。 當您遵循本課程中，您會看到 備忘稿上用來支援沈浸式 (VR) 耳機時，您可能需要的任何變更。

## <a name="prerequisites"></a>先決條件

> [!NOTE]
> 本教學課程專為具有基礎經驗的 Unity 開發人員和C#。 請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。 中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，比所列下面。

我們建議下列的硬體和軟體這堂課程：

- 開發電腦，[相容於 Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沈浸式 (VR) 耳機開發
- [Windows 10 Fall Creators Update （或更新版本） 啟用的開發人員模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 沈浸式 (VR) 耳機](immersive-headset-hardware-details.md)或是[Microsoft HoloLens](hololens-hardware-details.md)啟用開發人員模式
- Azure 和 Azure Bot 擷取的網際網路存取。 如需詳細資訊，[請遵循此連結](https://dev.botframework.com/)。

### <a name="before-you-start"></a>開始之前

1.  若要避免發生建置此專案的問題，強烈建議您建立根或接近根資料夾中，本教學課程中所述的專案 （長的資料夾路徑可能會造成問題，在建置階段）。
2.  設定並測試您的 HoloLens。 如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是個不錯的主意，若要開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時執行校正和感應器調整。 

校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。

如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。

## <a name="chapter-1--create-the-bot-application"></a>第 1 章-建立機器人應用程式

第一個步驟是建立您的機器人，做為本機的 ASP.Net Core Web 應用程式。 一旦您完成並測試它，將會發行至 Azure 入口網站。

1.  開啟 Visual Studio。 建立新專案，選取**ASP NET Core Web 應用程式**做為專案類型 （您會發現它在.NET Core 的小節），並稱之為**MyBot**。 按一下 [確定] 。

2.  在視窗中會出現選取**空**。 也請確定目標設為**ASP NET Core 2.0**並驗證已設為**不需要驗證**。 按一下 [確定] 。  

    ![建立機器人應用程式](images/AzureLabs-Lab312-01.png)

3.  現在將會開啟解決方案。 以滑鼠右鍵按一下方案**Mybot**中**方案總管**，然後按一下**管理方案的 NuGet 套件**。 

    ![建立機器人應用程式](images/AzureLabs-Lab312-02.png)

4.  在 **瀏覽**索引標籤上，搜尋**Microsoft.Bot.Builder.Integration.AspNet.Core** (請確定您已**包含發行前版本**檢查)。 選取的套件版本**4.0.1**，和勾選的 [專案] 方塊。 然後按一下**安裝**。 現在您已安裝所需的程式庫**Bot Framework v4**。 關閉 [NuGet] 頁面。

    ![建立機器人應用程式](images/AzureLabs-Lab312-03.png)

5.  以滑鼠右鍵按一下您*專案*， **MyBot**，請在**方案總管 中**，然後按一下**新增** **|****類別**。

    ![建立機器人應用程式](images/AzureLabs-Lab312-04.png)

6.  將類別命名為**MyBot** ，然後按一下**新增**。

    ![建立機器人應用程式](images/AzureLabs-Lab312-05.png)

7.  重複前一個點，來建立名為另一個類別**ConversationContext**。 

8.  以滑鼠右鍵按一下**wwwroot**中**方案總管**，然後按一下**新增** **|** **新項目**. 選取  **HTML 網頁**（您會發現它在 Web 子區段下）。 將檔案命名**default.html**。 按一下 **\[新增\]**。

    ![建立機器人應用程式](images/AzureLabs-Lab312-06.png)

9.  類別的清單中的物件 /**方案總管 中**看起來應該像下列映像。

    ![建立機器人應用程式](images/AzureLabs-Lab312-07.png)

10. 按兩下**ConversationContext**類別。 這個類別是對話的負責保存用來維護內容機器人的變數。 因為，將會維護此類別的執行個體中的這些交談內容值的任何執行個體**MyBot**類別將會重新整理每個活動接收的時間。 將下列程式碼新增至類別：

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. 按兩下**MyBot**類別。 這個類別會裝載任何連入的活動所呼叫，從客戶的處理常式。 此類別中，您將加入的程式碼，用來建置 bot 和客戶之間的對話。 如先前所述，此類別的執行個體被初始化每一個接收活動的時間。 將下列程式碼新增至此類別：

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. 按兩下**啟動**類別。 這個類別會初始化 bot。 將下列程式碼新增至類別：

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. 開啟**程式**類別檔案，並確認它的程式碼如下所示相同：

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. 請務必儲存您的變更，若要這樣做，請移至**檔案** > **全部儲存**，從頂端的 Visual Studio 工具列。

## <a name="chapter-2---create-the-azure-bot-service"></a>第 2-建立 Azure Bot 服務

既然您已針對您的 bot 建立程式碼，您必須將它發行到的執行個體*Web 應用程式 Bot*服務，在 Azure 入口網站上的。 本章將說明如何建立並設定在 Azure 上的機器人服務，然後再將您的程式碼發佈到它。

1.  首先，登入 Azure 入口網站 (https://portal.azure.com)。 

    1. 如果您還沒有 Azure 帳戶，您必須建立一個。 如果您要遵循本教學課程中的教室或實驗室的情況下，要求您的講師或其中一個新帳戶的說明設定 proctors。

2.  一旦您登入，按一下**建立資源**在左上角，，然後搜尋*Web 應用程式 bot*，然後按一下**Enter**。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-08.png)
 
3.  新的頁面將提供的描述*Web 應用程式 Bot*服務。 在左下方的這個頁面上，選取**建立**按鈕，以建立與這個關聯服務。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-09.png)
 
4.  一旦您按下**建立**:

    1. 插入您想要**名稱**此服務執行個體。
    2. 選取 **訂用帳戶**。
    3. 選擇**資源群組**或建立新的帳戶。 資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。 建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。

        > 如果您想要深入了解 Azure 資源群組，[請遵循此連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. （如果您要建立新的資源群組），請判斷您的資源群組的位置。 位置，在理想情況下會在應用程式會執行所在的區域。 在特定區域中，才可以使用一些 Azure 的資產。
    5. 選取 **定價層**適合您，如果這是第一個時間來建立*Web 應用程式 Bot*服務，免費層 （名為 F0） 應該是您可以使用
    6. **應用程式名稱**可以只保留相同*Bot 名稱*。 
    7. 離開*Bot 範本*作為**基本 (C#)**。
    8. *App service 方案/位置*應該已自動填入您的帳戶。
    9. 設定**Azure 儲存體**您想要用來裝載您的機器人。 如果您還沒有，您可以在此建立。
    10. 您也必須確認您已了解這些條款和條件套用到此服務。
    11. 按一下 [建立]。
 
        ![建立 Azure Bot 服務](images/AzureLabs-Lab312-10.png)

5.  一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。

6.  通知會出現在入口網站中，一旦建立服務執行個體。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-11.png) 
 
7.  按一下通知，以探索新的服務執行個體。 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-12.png)
 
8. 按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。 您會前往新的 Azure 服務執行個體。 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-13.png)
 
9.  此時您需要設定稱為功能**直線**以允許用戶端應用程式與此 Bot 服務進行通訊。 按一下 **通道**，然後在**新增精選的頻道**區段中，按一下**設定直接線路通道**。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-14.png)

10. 在此頁面中，您會發現**祕密金鑰**，可讓您的用戶端應用程式與機器人進行驗證。 按一下 **顯示**按鈕並複製的其中一個顯示的金鑰，因為您將需要這稍後會在您的專案。 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>第 3-將 Bot 發行至 Azure Web 應用程式 Bot 服務

現在，您的服務已準備就緒，您需要將您的 Bot 程式碼，您建置之前，您新建立的 Web 應用程式 Bot 服務的發佈。

> [!NOTE] 
> 您必須將您的 Bot 發行至 Azure 服務，每次您變更 Bot 解決方案 / c o d。

1.  回到您先前建立的 Visual Studio 方案。 
2.  以滑鼠右鍵按一下您**MyBot**專案中，在**方案總管**，然後按一下**發行**。

    ![將 Bot 發行至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-16.png)

3.  在上*挑選發行目標*頁面上，按一下**App Service**，然後**選取現有**，最後按一下**建立設定檔**（您可能需要按一下旁邊的下拉式箭號*發佈*按鈕，如果這是不可見)。

    ![將 Bot 發行至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-17.png)

4. 如果您尚未登入到您的 Microsoft 帳戶，您必須在此處進行。
5. 在上**發佈**您會發現您需要設定相同的頁面**訂用帳戶**用於*Web 應用程式 Bot*建立服務。 然後設定**檢視**作為**資源群組**，然後在下拉式清單的資料夾結構中，選取**資源群組**您先前建立。 按一下 [確定] 。 

    ![將 Bot 發行至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-18.png)

6.  現在，按一下**發佈**按鈕，並等候 Bot 發行 （可能需要幾分鐘的時間）。

    ![將 Bot 發行至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>第 4 章-設定 Unity 專案

下列已啟動的一組典型混合實境，進行開發，且此情況下，是良好的其他專案範本。

1.  開啟*Unity*然後按一下**新增**。 

    ![設定 Unity 專案](images/AzureLabs-Lab312-20.png)

2.  您現在必須提供 Unity 專案名稱。 插入**Hololens Bot**。 請確定已設定的專案範本**3D**。 設定**位置**適用於您的某個位置 （請記住，使其更接近根目錄是較佳）。 然後，按一下**建立專案**。

    ![設定 Unity 專案](images/AzureLabs-Lab312-21.png)

3.  使用 Unity 開啟，就代表值得查看以預設值**指令碼編輯器**設為**Visual Studio**。 移至**編輯 > 偏好**，然後在新視窗中，瀏覽**外部工具**。 變更**外部指令碼編輯器**要**Visual Studio 2017**。 關閉**喜好設定**視窗。

    ![設定 Unity 專案](images/AzureLabs-Lab312-22.png)

4.  接下來，移至**檔案 > 組建設定**，然後選取**通用 Windows 平台**，然後按一下**切換平台**按鈕以套用您的選擇。

    ![設定 Unity 專案](images/AzureLabs-Lab312-23.png)

5.  當您依然在**檔案 > 組建設定**並確定：

    1.  **裝置為目標**設為**Hololens**

        > 針對擬真耳機，設定**目標裝置**要*任何裝置*。

    2.  **建置型別**設為**D3D**

    3.  **SDK**設為**最新安裝**

    4.  **Visual Studio 版本**設為**最新安裝**

    5.  **建置並執行**設為**本機電腦**

    6.  儲存場景，並將它新增至組建。 

        1. 做法是選取**加入開啟的場景**。 儲存視窗會出現。
        
            ![設定 Unity 專案](images/AzureLabs-Lab312-24.png)

        2. 建立新的資料夾，以及任何未來、 場景，然後選取**新的資料夾**按鈕，以建立新的資料夾，其命名**場景**。

             ![設定 Unity 專案](images/AzureLabs-Lab312-25.png)

        3. 開啟您剛建立**場景**資料夾，然後在*檔名*： 文字欄位中，輸入**BotScene**，然後按一下**儲存**。

            ![設定 Unity 專案](images/AzureLabs-Lab312-26.png)

    7. 剩餘的設定，**組建設定**，應保持為預設值，現在。

6. 中*組建設定*視窗中，按一下**播放程式設定** 按鈕，這會開啟 相關 面板中的空間位置*Inspector*所在。 

    ![設定 Unity 專案](images/AzureLabs-Lab312-27.png)

7. 在此窗格中，少數設定需要驗證：

    1. 在 [**其他設定**] 索引標籤：

        1. **指令碼執行階段版本**應該 **（.NET 4.6 對等） 的實驗性**; 變更這項需要重新啟動的編輯器。
        2. **指令碼後端**應該是 **.NET**
        3. **API 相容性層級**應該是 **.NET 4.6**

            ![設定 Unity 專案](images/AzureLabs-Lab312-28.png)
      
    2. 內**發佈設定**索引標籤之下**功能**，檢查：

        - **InternetClient**
        - **Microphone**

            ![設定 Unity 專案](images/AzureLabs-Lab312-29.png)

    3. 在下方窗格中， **XR 設定**(參閱下方**發佈設定**)，刻度**虛擬實境支援**，請確定**Windows Mixed Reality SDK**加入。

        ![設定 Unity 專案](images/AzureLabs-Lab312-30.png)

8.  回到*Build Settings* _Unity C#_ 專案不再呈現灰色，這旁邊的核取方塊。 
9.  關閉 [建立設定] 視窗。
10. 儲存您的場景和專案 (**檔案 > 儲存場景檔案 > 儲存專案**)。


## <a name="chapter-5--camera-setup"></a>第 5 章-觀景窗設定

> [!IMPORTANT]
> 如果您想要跳過*Unity 設定*元件的課程，並繼續直接進入程式碼，請自由下載此[Azure MR-312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)，它匯入到您的專案，作為[**自訂封裝**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續從[第 7 章](#chapter-7-–-create-the-botobjects-class)。

1.  在 *階層面板*，選取**Main Camera**。 
2.  選取之後，您將能夠看到所有的元件**Main Camera**中*Inspector 面板*。

    1. **相機物件**必須命名為**Main Camera** （請注意拼字檢查）
    2. Main Camera**標記**必須設為**MainCamera** （請注意拼字檢查）
    3. 請確定**轉換的位置**設定為**0，0，0**
    4. 設定**清除旗標**要**單色**。
    5. 設定**背景**相機元件以色彩**黑色，0 的 Alpha (十六進位的程式碼: #00000000)**

    ![照相機設定](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>第 6 章-匯入 Newtonsoft 程式庫

若要可協助您還原序列化和序列化物件接收和傳送到 Bot 服務，您需要下載**Newtonsoft**程式庫。 您會發現[相容的版本已經組織使用的正確 Unity 資料夾結構這裡](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)。 

若要 Newtonsoft 程式庫匯入專案中，使用 Unity 套件所附的這堂課程。

1.  新增 *.unitypackage*若要使用的 Unity**資產** > **匯入封裝** > **自訂封裝**功能表選項。

    ![匯入 Newtonsoft 程式庫](images/AzureLabs-Lab312-34.png)

2.  在 **匯入 Unity 封裝**方塊會顯示。 請確認所有項目底下 （而且包括）**外掛程式**已選取。

    ![匯入 Newtonsoft 程式庫](images/AzureLabs-Lab312-35.png)

3.  按一下 **匯入**按鈕以新增至您的專案項目。

4.  移至**Newtonsoft**下方的資料夾**外掛程式**專案檢視，然後選取 Newtonsoft 外掛程式中。

    ![](images/AzureLabs-Lab312-35b.png)

5.  使用選取 Newtonsoft 外掛程式，請確認**任何平台**是**取消核取**，然後確定**WSAPlayer**也是**未核取**，然後按一下**套用**。 這只是要確認已正確設定檔案。

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > 標示這些外掛程式會設定它們僅適用於在 Unity 編輯器中。 有一組不同的專案會匯出從 Unity 後要使用 WSA 資料夾中。

6.  接下來，您必須開啟**WSA**資料夾內**Newtonsoft**資料夾。 您會看到您剛才設定的相同檔案的複本。 選取檔案，並在偵測器中，確定該
    -   **任何平台**是**unchecked** 
    -   **只有** **WSAPlayer**是**檢查**
    -   **不會處理**是**檢查**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>第 7 – 建立 BotTag

1.  建立新**標記**呼叫的物件**BotTag**。 您可以選取 Main Camera 在場景中。 按一下標記下拉式功能表偵測器 面板中。 按一下 **新增標記**。

    ![照相機設定](images/AzureLabs-Lab312-32.png)
 
2.  按一下  **+** 符號。 指定新**標記**作為**BotTag**，*儲存*。

    ![照相機設定](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **不這麼做**套用**BotTag**到 Main Camera。 如果您不小心這麼做，請務必變更標記回到 Main Camera *MainCamera*。

## <a name="chapter-8--create-the-botobjects-class"></a>第 8 章-建立 BotObjects 類別

您必須建立第一個指令碼**BotObjects**類別，這是空的類別建立，因此一系列的其他類別的物件可儲存在相同的指令碼，並在場景中其他指令碼存取。

建立這個類別是純粹的架構的選擇，這些物件可以改為裝載於稍後在本課程中，您將建立 Bot 指令碼。

若要建立此類別： 

1.  以滑鼠右鍵按一下 *[專案] 面板*，然後**建立 > 資料夾**。 將資料夾命名**指令碼**。 

    ![建立指令碼 資料夾。](images/AzureLabs-Lab312-36.png)

2.  按兩下**指令碼**資料夾將它開啟。 然後在該資料夾，然後按一下滑鼠右鍵，並選取**建立 >C#指令碼**。 指令碼命名**BotObjects**。 

3.  按兩下新**BotObjects**指令碼，以開啟它**Visual Studio**。

4.  刪除指令碼的內容，並取代為下列程式碼：

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-9--create-the-gazeinput-class"></a>第 9 章 – 建立 GazeInput 類別

下一步要建立的類別是**GazeInput**類別。 這個類別會負責：

- 建立資料指標，代表*視線*播放程式。
- 偵測物件叫用的視線，播放程式，並保存至偵測到的物件的參考。

若要建立此類別： 

1.  移至**指令碼**您先前建立的資料夾。 
2.  在資料夾中，以滑鼠右鍵按一下**建立 >C#指令碼**。 呼叫指令碼**GazeInput**。 
3.  按兩下新**GazeInput**指令碼，以開啟它**Visual Studio**。
4.  插入下面這一行的類別名稱的頂端：

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  然後新增下列變數內**GazeInput**類別，上述**start （)** 方法：

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  程式碼**start （)** 應該加入方法。 在類別初始化時，這將會呼叫：

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  實作的方法，將會具現化，並設定視線資料指標： 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  實作的方法，將設定從 Main Camera Raycast 並追蹤的目前具有焦點的物件。

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-10--create-the-bot-class"></a>第 10 章 – 建立 Bot 類別

現在會呼叫您要建立指令碼**Bot**。 這是您的應用程式的核心類別，它會儲存： 

- 您的 Web 應用程式 Bot 認證
- 收集使用者語音命令方法
- 必要起始交談的 Web 應用程式 Bot 方法 
- 為了將訊息傳送至您的 Web 應用程式 Bot 方法 

若要將訊息傳送到 Bot 服務時， **SendMessageToBot()** 協同程式將會建置的活動，這是使用者所傳送的資料 Bot Framework 可辨識的物件。 
 
若要建立此類別： 

1. 按兩下**指令碼**資料夾，將它開啟。 
2. 以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。 指令碼命名**Bot**。 
3. 按兩下新的指令碼，以使用 Visual Studio 中開啟它。
4. 更新命名空間相同，如下所示，在頂端**Bot**類別：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. 內部**Bot**類別新增下列變數：

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > 請確定您插入您**Bot 祕密金鑰**成**botSecret**變數。 您將已記下您**Bot 祕密金鑰**在開始本課程中，在**[第 2 章](#chapter-2---create-the-azure-bot-service)，步驟 10**。

7. 程式碼**Awake()** 並**start （)** 現在需要加入。 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. 新增語音擷取開始及結束時，會呼叫由語音程式庫的兩個處理常式。 *DictationRecognizer*將會自動停止擷取使用者的心聲，當使用者停止讀出。

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. 下列處理常式會收集使用者的語音輸入的結果，並呼叫協同程式負責將訊息傳送至 Web 應用程式 Bot Service。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. 下列的協同程式會呼叫來開始交談與機器人。 您會注意到交談呼叫完成之後，它會呼叫**SendMessageToCoroutine()** 藉由傳遞一系列會設定傳送到 Bot Service 與空的訊息活動的參數。 這是為了提示 Bot 服務，才能起始對話。

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. 下列的協同程式會呼叫來建置要傳送到 Bot 服務的活動。 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. 下列的協同程式會呼叫來要求傳送到 Bot 服務的活動之後的回應。 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. 要加入至這個類別的最後一個方法，才能在場景中顯示訊息：

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > 您可能會看到在 Unity 編輯器] 主控台的 [關於遺漏錯誤**SceneOrganiser**類別。 當您將會稍後在本教學課程中建立這個類別，請忽略此訊息中。

14.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-11--create-the-interactions-class"></a>第 11 章 – 建立互動類別

您即將建立的類別現在稱為**互動**。 這個類別用來偵測使用者的 HoloLens 點選輸入。 

如果在使用者點選時查看*Bot* Bot 以及在場景中的物件已準備好接聽語音輸入、 Bot 物件會變更色彩**紅色**並開始接聽語音輸入。 

這個類別繼承自**GazeInput**類別，並因此可參考**start （)** 方法，並自該類別，表示所使用的變數**基底**。 
 
若要建立此類別：

1.  按兩下**指令碼**資料夾，將它開啟。 
2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。 指令碼命名**互動**。 
3.  按兩下新的指令碼，以使用 Visual Studio 中開啟它。
4.  更新命名空間和類別繼承，如下所示，頂端的相同**互動**類別：

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  內部**互動**類別新增下列變數：

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  然後新增**start （)** 方法：

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  加入處理常式，將會在使用者執行前面 HoloLens 相機點選手勢時觸發

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. 請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。

## <a name="chapter-12--create-the-sceneorganiser-class"></a>第 12 章-建立 SceneOrganiser 類別

在這個實驗室中所需的最後一個類別會呼叫**SceneOrganiser**。 這個類別會以程式設計方式設定場景，藉由將元件和指令碼新增至 Main Camera 中，並在場景中建立適當的物件。
 
若要建立此類別：

1.  按兩下**指令碼**資料夾，將它開啟。 
2.  以滑鼠右鍵按一下**指令碼**資料夾中，按一下**建立 >C#指令碼**。 指令碼命名**SceneOrganiser**。 
3.  按兩下新的指令碼，以使用 Visual Studio 中開啟它。
4.  內部**SceneOrganiser**類別新增下列變數：

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  然後新增**Awake()** 並**start （)** 方法：

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  新增下列方法，負責在場景中建立 Bot 物件，並設定參數和元件：

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  新增下列方法，負責建立場景，代表來自 Bot 的回應中的 UI 物件：

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  請務必儲存您的變更，在*Visual Studio* ，然後傳回給*Unity*。
9.  在 Unity 編輯器中，拖曳**SceneOrganiser**到 Main Camera 從指令碼 資料夾的指令碼。 場景召集人元件現在應該會出現在 Main Camera 物件，如下圖所示。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>第 13 章-建置前

若要執行您的應用程式執行完整的測試必須側面載入它拖曳至您的 HoloLens。
這麼做之前，請確認：

-   中所述的所有設定[**第 4 章**](#Chapter-4-–-Set-up-the-unity-project)都已正確設定。 
-   指令碼**SceneOrganiser**附加至**Main Camera**物件。 
-   在  **Bot**類別中，請確定您已插入您**Bot 祕密金鑰**成**botSecret**變數。

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>第 14 章-建置和側載到 HoloLens

此專案的 Unity 區段所需的所有項目現在已完成，所以該是時候建置從 Unity。

1.  瀏覽至**組建設定**，**檔案 > 組建設定...**.
2.  從**Build Settings**  視窗中，按一下**建置**。

    ![從 Unity 建置應用程式](images/AzureLabs-Lab312-38.png)

3.  如果您尚未，勾選**UnityC#專案**。
4.  按一下 [建置] 。 將會啟動 unity**檔案總管**視窗中，您要建立，然後選取 建置到應用程式的資料夾。 現在，建立該資料夾並將它命名**應用程式**。 然後使用**應用程式**按一下 選取資料夾**選取資料夾**。 
5.  Unity 會開始建置您的專案**應用程式**資料夾。 
6.  一次 Unity 已完成的建置 （它可能需要一些時間），它將會開啟**檔案總管**視窗在您的組建位置 （檢查您的工作列中，因為它可能不一定會出現您的視窗上方會通知您加入的新視窗）。

## <a name="chapter-15--deploy-to-hololens"></a>章 15 – 將部署到 HoloLens

若要部署 HoloLens 上：

1.  您將需要您 HoloLens IP 位址 （適用於遠端部署），並以確保您 HoloLens 處於**開發人員模式**。 請這樣做：

    1. 儘管穿著您 HoloLens，開啟**設定**。
    2. 移至**網路和網際網路 > Wi-fi > 進階選項**
    3. 附註**IPv4**位址。
    4. 接下來，瀏覽回到**設定**，然後**更新與安全性 > 適用於開發人員** 
    5. 設定開發人員模式。

2.  瀏覽至新的 Unity 組建 (**應用程式**資料夾)，並開啟方案檔**Visual Studio**。
3.  在 **方案組態**選取**偵錯**。
4.  在 **的方案平台**，選取**x86**，**遠端機器**。 

    ![將部署從 Visual Studio 方案。](images/AzureLabs-Lab312-39.png)
 
5.  移至**建置 功能表**，然後按一下**部署方案**，側載您 HoloLens 應用程式。
6.  您的應用程式現在應該會出現在清單中，準備好啟動您 HoloLens 上已安裝的應用程式 ！

    > [!NOTE]
    > 若要將部署到擬真耳機，設定**的方案平台**來*本機電腦*，並設定**組態**至*偵錯*，使用*x86*作為**平台**。 然後部署到本機電腦，使用**建置 功能表**，並選取*部署方案*。 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>第 16 章 – HoloLens 上使用應用程式

- 一旦您已啟動的應用程式，您會看到您面前的藍色球體 Bot。

- 使用**點選手勢**時您會在起始交談球體 gazing。 
 
- 等候啟動交談 （發生時，UI 會顯示一則訊息）。 一旦您入門的訊息接收的 Bot 時，點選一次 Bot 讓它將會變成紅色，並開始接聽您的聲音。 

- 當您停止交談時，您的應用程式會將您的訊息傳送到 Bot 和您會立即收到的回應，將會顯示在 UI 中。 

- 重複程序，將多個訊息傳送至您的 Bot （您必須點選每個您想要傳送訊息的時間）。

這項交談會示範如何 Bot 可以保留資訊 （您的名稱），同時也提供已知的資訊 （例如所配備的項目）。

#### <a name="some-questions-to-ask-the-bot"></a>要求 Bot 一些問題：

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>您已完成的 Web 應用程式 Bot (v4) 應用程式

恭喜，您建置會利用 Azure Web 應用程式 Bot、 Microsoft Bot Framework v4 mixed 的 reality 應用程式。

![最終產品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Bonus 練習

### <a name="exercise-1"></a>練習 1

在這個實驗室中的交談結構是非常基本。 您可以使用 Microsoft LUIS，自然語言了解功能賦予機器人。

### <a name="exercise-2"></a>練習 2

此範例不包含終止的交談，並重新啟動一個新。 若要讓的 Bot 功能完成，請嘗試實作交談的結束。
