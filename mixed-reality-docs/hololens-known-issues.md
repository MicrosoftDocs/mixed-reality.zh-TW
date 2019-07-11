---
title: HoloLens 的已知問題
description: 這是已知的問題可能會影響 HoloLens 的開發人員的清單。
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: 針對進行疑難排解，已知問題，協助
ms.openlocfilehash: 1ef9e9f411e16d2f604930f3146ede1d03d7c0f6
ms.sourcegitcommit: c36b8c8573f51afa79504c4a17084e4f55d2f664
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67789484"
---
# <a name="hololens-known-issues"></a><span data-ttu-id="e8ab8-104">HoloLens 的已知問題</span><span class="sxs-lookup"><span data-stu-id="e8ab8-104">HoloLens known issues</span></span>

<span data-ttu-id="e8ab8-105">這是目前的 HoloLens 影響開發人員的已知問題清單。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-105">This is the current list of known issues for HoloLens affecting developers.</span></span> <span data-ttu-id="e8ab8-106">在此請先檢查您會看到一個奇怪的行為。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-106">Check here first if you are seeing an odd behavior.</span></span> <span data-ttu-id="e8ab8-107">這份清單會保持更新發現新問題或收到回報，或未來的 HoloLens 軟體更新問題的解答。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-107">This list will be kept updated as new issues are discovered or reported, or as issues are addressed in future HoloLens software updates.</span></span>

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a><span data-ttu-id="e8ab8-108">無法連接，然後部署至透過 Visual Studio 的 HoloLens</span><span class="sxs-lookup"><span data-stu-id="e8ab8-108">Unable to connect and deploy to HoloLens through Visual Studio</span></span>

>[!NOTE]
><span data-ttu-id="e8ab8-109">上次更新日期：7/8 下午 7:25-@ 小組已識別的根本原因和目前正努力修正。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-109">Last Update: 7/8 @ 7:25PM - The team has identified the root cause and is currently working on fix.</span></span> <span data-ttu-id="e8ab8-110">因應措施如下所示。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-110">Workaround available below.</span></span> 

<span data-ttu-id="e8ab8-111">我們可以找出此問題的根本原因。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-111">We were able to identify the root cause of this issue.</span></span> <span data-ttu-id="e8ab8-112">然後使用相同的 HoloLens 後續使用最新版的 Visual Studio 2017 或 Visual Studio 2019 和 Visual Studio 2015 或 Visual Studio 2017 的早期版本來部署和偵錯其 HoloLens 上的應用程式的使用者會受到影響。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-112">Users who used Visual Studio 2015 or early releases of Visual Studio 2017 to deploy and debug applications on their HoloLens and then subsequently used the latest versions of Visual Studio 2017 or Visual Studio 2019 with the same HoloLens will be affected.</span></span> 

<span data-ttu-id="e8ab8-113">由較新版本的 Visual Studio 部署新版的元件，但造成失敗的較新版本的裝置上剩餘檔案從舊的版本。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-113">The newer releases of Visual Studio deploy a new version of a component, but files from the older version are left over on the device, causing the newer version to fail.</span></span>  <span data-ttu-id="e8ab8-114">這會導致下列錯誤訊息：DEP0100:請確定目標裝置已啟用開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-114">This causes the following error message: DEP0100: Please ensure that target device has developer mode enabled.</span></span> <span data-ttu-id="e8ab8-115">無法取得開發人員授權上<ip>因為錯誤 80004005。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-115">Could not obtain a developer license on <ip> due to error 80004005.</span></span>
 
<span data-ttu-id="e8ab8-116">**因應措施**：</span><span class="sxs-lookup"><span data-stu-id="e8ab8-116">**Workaround**:</span></span> 

<span data-ttu-id="e8ab8-117">我們的小組目前正努力修正程式。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-117">Our team is currently working on a fix.</span></span> <span data-ttu-id="e8ab8-118">在此同時，您可以使用下列步驟來解決此問題，並協助解除部署和偵錯：</span><span class="sxs-lookup"><span data-stu-id="e8ab8-118">In the meantime, you can use the following steps to work around the issue and help unblock deployment and debugging:</span></span>  
1. <span data-ttu-id="e8ab8-119">開啟 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e8ab8-119">Open Visual Studio</span></span>
2. <span data-ttu-id="e8ab8-120">檔案-> 新增-> 專案</span><span class="sxs-lookup"><span data-stu-id="e8ab8-120">File -> New -> Project</span></span>
3. <span data-ttu-id="e8ab8-121">視覺化C#]-> [Windows 桌面]-> [主控台應用程式 (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="e8ab8-121">Visual C# -> Windows Desktop -> Console App (.NET Framework)</span></span>
4. <span data-ttu-id="e8ab8-122">提供專案名稱 (例如 HoloLensDeploymentFix)，並確定至少架構設定為.NET Framework 4.5，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-122">Give the project a name (e.g. HoloLensDeploymentFix) and make sure the Framework is set to at least .NET Framework 4.5 then click OK.</span></span>
5. <span data-ttu-id="e8ab8-123">以滑鼠右鍵按一下方案總管 中的 參考 節點，並新增下列參考 （按一下 瀏覽 區段中，然後按一下 瀏覽...按鈕）：</span><span class="sxs-lookup"><span data-stu-id="e8ab8-123">Right-click on the References node in Solution Explorer and add the following references (click to the 'Browse' section and click the 'Browse...' button):</span></span>
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    ><span data-ttu-id="e8ab8-124">如果您沒有安裝 10.0.18362.0，使用您所擁有的最新版本。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-124">If you don't have 10.0.18362.0 installed, use the most recent version that you have.</span></span>
 
6. <span data-ttu-id="e8ab8-125">以滑鼠右鍵按一下方案總管] 中的專案，然後選擇 [新增]-> [現有項目。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-125">Right-click on the project in Solution Explorer and choose Add -> Existing Item.</span></span>
 
7. <span data-ttu-id="e8ab8-126">瀏覽至 C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86 並變更篩選，以"的所有檔案 (\*。\*) 」</span><span class="sxs-lookup"><span data-stu-id="e8ab8-126">Browse to C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86 and change the filter to "All Files (\*.\*)"</span></span>
 
8. <span data-ttu-id="e8ab8-127">選取 SirepClient.dll 和 SshClient.dll，然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-127">Select both SirepClient.dll and SshClient.dll and click "Add".</span></span>
 
9. <span data-ttu-id="e8ab8-128">找出並選取方案總管 （它們應該是檔案的清單底部） 中的這兩個檔案並將"複製到輸出目錄 中 屬性 視窗變更為 一律複製</span><span class="sxs-lookup"><span data-stu-id="e8ab8-128">Locate and select both files in Solution Explorer (they should be at the bottom of the list of files) and change "Copy to Output Directory" in the Properties window to "Copy always"</span></span>
 
10. <span data-ttu-id="e8ab8-129">在檔案頂端，加入現有的 'using' 陳述式清單中的下列：</span><span class="sxs-lookup"><span data-stu-id="e8ab8-129">At the top of the file, add the following to the existing list of 'using' statements:</span></span> 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. <span data-ttu-id="e8ab8-130">在 「 靜態 void Main(...)"，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e8ab8-130">Inside of “static void Main(...)”, add the following code:</span></span>
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. <span data-ttu-id="e8ab8-131">組建]-> [建置方案</span><span class="sxs-lookup"><span data-stu-id="e8ab8-131">Build -> Build Solution</span></span>
 
13. <span data-ttu-id="e8ab8-132">開啟命令提示字元包含已編譯的.exe (例如 C:\MyProjects\HoloLensDeploymentFix\bin\Debug) 的資料夾</span><span class="sxs-lookup"><span data-stu-id="e8ab8-132">Open a command prompt to the folder that contains the compiled .exe (e.g. C:\MyProjects\HoloLensDeploymentFix\bin\Debug)</span></span>
 
14. <span data-ttu-id="e8ab8-133">執行可執行檔，並提供裝置的 IP 位址，做為命令列引數。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-133">Run the executable and provide the device's IP address as a command-line argument.</span></span>  <span data-ttu-id="e8ab8-134">（如果透過 USB 連接，您可以使用 127.0.0.1，否則請使用裝置的 WiFi IP 位址。）例如，"HoloLensDeploymentFix 127.0.0.1"</span><span class="sxs-lookup"><span data-stu-id="e8ab8-134">(If connected via USB, you can use 127.0.0.1, otherwise use the device’s WiFi IP address.)  For example, "HoloLensDeploymentFix 127.0.0.1"</span></span>
 
15. <span data-ttu-id="e8ab8-135">一旦此工具已結束但沒有任何訊息 （這應該只需要幾秒鐘的時間），您現在將能夠部署和偵錯從 Visual Studio 2017 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-135">Once the tool has exited without any messages (this should only take a few seconds), you will now be able to deploy and debug from Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="e8ab8-136">不需要繼續的使用此工具。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-136">Continued use of the tool is not necessary.</span></span>

<span data-ttu-id="e8ab8-137">我們將進一步提供可用的更新。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-137">We will provide further updates as they become available.</span></span>

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a><span data-ttu-id="e8ab8-138">啟動 Microsoft Store 和 HoloLens 上的應用程式的問題</span><span class="sxs-lookup"><span data-stu-id="e8ab8-138">Issues launching the Microsoft Store and apps on HoloLens</span></span>

>[!NOTE]
><span data-ttu-id="e8ab8-139">上次更新日期：@ 10AM-解決問題的 4/2。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-139">Last Update: 4/2 @ 10 AM - Issue resolved.</span></span> 

<span data-ttu-id="e8ab8-140">嘗試啟動 Microsoft Store 和 HoloLens 上的應用程式時，可能會遇到問題。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-140">You may experience issues when trying to launch the Microsoft Store and apps on HoloLens.</span></span> <span data-ttu-id="e8ab8-141">我們已決定背景應用程式更新部署新版 framework 中的封裝特定的順序，一或多個相依的應用程式仍在執行時，會發生問題。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-141">We've determined that the issue occurs when background app updates deploy a newer version of framework packages in specific sequences while one or more of their dependent apps are still running.</span></span> <span data-ttu-id="e8ab8-142">在此情況下，自動更新傳遞新版本的.NET 原生架構 （版本到 10.0.27413 10.0.25531） 會造成未正確更新所有執行的應用程式使用舊版的架構來執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-142">In this case,  an automatic app update delivered a new version of the .NET Native Framework (version 10.0.25531 to 10.0.27413) caused the apps that are running to not correctly update for all running apps consuming the prior version of the framework.</span></span>  <span data-ttu-id="e8ab8-143">Framework update 流程如下所示:-</span><span class="sxs-lookup"><span data-stu-id="e8ab8-143">The flow for framework update is as follows: -</span></span>

1.  <span data-ttu-id="e8ab8-144">從存放區下載並安裝新的 framework 套件</span><span class="sxs-lookup"><span data-stu-id="e8ab8-144">The new framework package is downloaded from the store and installed</span></span>
2.  <span data-ttu-id="e8ab8-145">使用較舊的架構的所有應用程式會 「 更新 」 使用較新版本</span><span class="sxs-lookup"><span data-stu-id="e8ab8-145">All apps using the older framework are ‘updated’ to use the newer version</span></span>

<span data-ttu-id="e8ab8-146">如果步驟 2 完成之前中斷任何不已註冊與新版架構的應用程式將無法從 [開始] 功能表啟動。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-146">If step 2 is interrupted before completion then any apps for which the newer framework wasn’t registered will fail to launch from the start menu.</span></span>  <span data-ttu-id="e8ab8-147">我們相信 HoloLens 上的任何應用程式可能會受到此問題。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-147">We believe any app on HoloLens could be affected by this issue.</span></span>

<span data-ttu-id="e8ab8-148">某些使用者有回報，關閉無回應的應用程式，並啟動其他應用程式，例如意見反應中樞，3D 檢視器或相片解決此問題，-但，這無法 100%的時間。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-148">Some users have reported that closing hung apps and launching other apps such as Feedback Hub, 3D Viewer or Photos resolves the issue for them - however, this does not work 100% of the time.</span></span>

<span data-ttu-id="e8ab8-149">我們根造成此問題已不造成導致不正確地處理，原生.NET framework 更新 OS 更新本身，但錯誤。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-149">We have root caused that this issue was not caused the update itself, but a bug in the OS that resulted in the .NET Native framework update being handled incorrectly.</span></span> <span data-ttu-id="e8ab8-150">我們很高興宣布，我們已識別出修正程式，而且已發行的更新 (OS 版本 17763.380) 包含修正程式。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-150">We are pleased to announce that we have identified a fix and have released an update (OS version 17763.380) containing the fix.</span></span> 

<span data-ttu-id="e8ab8-151">若要查看是否您的裝置可能需要更新請：</span><span class="sxs-lookup"><span data-stu-id="e8ab8-151">To see if your device can take the update please:</span></span>

1.  <span data-ttu-id="e8ab8-152">移至 [設定] 應用程式，並開啟 [更新與安全性]</span><span class="sxs-lookup"><span data-stu-id="e8ab8-152">Go to the “Settings” app and open “Update & Security”</span></span>
2.  <span data-ttu-id="e8ab8-153">按一下 [檢查更新]</span><span class="sxs-lookup"><span data-stu-id="e8ab8-153">Click “Check for Updates”</span></span>
3.  <span data-ttu-id="e8ab8-154">如果有可用 17763.380 的更新，請更新至接收應用程式懸置狀況 bug 的修正此組建</span><span class="sxs-lookup"><span data-stu-id="e8ab8-154">If update to 17763.380 is available, please update to this build to receive the fix for the App Hang bug</span></span>
4.  <span data-ttu-id="e8ab8-155">在更新到此版本的作業系統，應用程式應該運作如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-155">Upon updating to this version of the OS, the Apps should work as expected.</span></span>

<span data-ttu-id="e8ab8-156">此外，如同我們使用所有 HoloLens OS 發行版本一樣，我們有張貼 FFU 映像至 Microsoft 下載中心 https://aka.ms/hololensdownload/10.0.17763.380 。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-156">Additionally, as we do with every HoloLens OS release, we have posted the FFU image to the Microsoft Download Center at https://aka.ms/hololensdownload/10.0.17763.380.</span></span> 

<span data-ttu-id="e8ab8-157">如果您不想要取得更新，我們發行了新版本的 Microsoft Store UWP 應用程式自 3/29。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-157">If you would not like to take the update, we have released a new version of the Microsoft Store UWP app as of 3/29.</span></span> <span data-ttu-id="e8ab8-158">一旦您有更新的版本存放區：</span><span class="sxs-lookup"><span data-stu-id="e8ab8-158">Once you have the updated version of the Store:</span></span>

1) <span data-ttu-id="e8ab8-159">開啟存放區，並確認它會載入。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-159">Open the Store and confirm that it loads.</span></span>
2) <span data-ttu-id="e8ab8-160">您可以使用 Bloom 筆勢來開啟的功能表。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-160">Use the Bloom Gesture to open the menu.</span></span>
3) <span data-ttu-id="e8ab8-161">嘗試開啟先前中斷的應用程式</span><span class="sxs-lookup"><span data-stu-id="e8ab8-161">Attempt to open previously broken apps</span></span>
3) <span data-ttu-id="e8ab8-162">如果仍然無法啟動，點選 按住中斷的應用程式的圖示並選取 解除安裝。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-162">If it still cannot be launched, tap and hold the icon of the broken app and select uninstall.</span></span>
4) <span data-ttu-id="e8ab8-163">Resinstall 這些來自市集的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-163">Resinstall these apps from the store.</span></span>

<span data-ttu-id="e8ab8-164">如果您的裝置仍然無法載入應用程式，您可以側載的版本的.NET 原生架構和執行階段透過 「 下載中心 」 這麼做：</span><span class="sxs-lookup"><span data-stu-id="e8ab8-164">If your device is still unable to load apps, you can sideload a version of the .NET Native Framework and Runtime through the download center by doing:</span></span>

1)  <span data-ttu-id="e8ab8-165">請下載[此 zip 檔案](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)從 Microsoft 下載中心取得。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-165">Please download [this zip file](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) from the Microsoft Download Center.</span></span>  <span data-ttu-id="e8ab8-166">解壓縮，將會產生兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-166">Unzipping will produce two files.</span></span>  <span data-ttu-id="e8ab8-167">Microsoft.NET.Native.Runtime.1.7.appx 和 Microsoft.NET.Native.Framework.1.7.appx</span><span class="sxs-lookup"><span data-stu-id="e8ab8-167">Microsoft.NET.Native.Runtime.1.7.appx and Microsoft.NET.Native.Framework.1.7.appx</span></span>
2)  <span data-ttu-id="e8ab8-168">請確認您的裝置是開發人員解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-168">Please verify that your device is dev unlocked.</span></span>  <span data-ttu-id="e8ab8-169">如果您尚未這麼做的指示之前完成[此處](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-169">If you haven’t done that before the instructions to do that are [here](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).</span></span>
3)  <span data-ttu-id="e8ab8-170">接著您要進入 Windows Device Portal。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-170">You then want to get into the Windows Device Portal.</span></span>  <span data-ttu-id="e8ab8-171">我們的建議是，若要這樣做透過 USB 和您一樣的輸入 http://127.0.0.1:10080 貼入瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-171">Our recommendation is to do this over USB and you would do that by typing http://127.0.0.1:10080 into your browser.</span></span>  
4)  <span data-ttu-id="e8ab8-172">一旦您有 Windows Device Portal 向上我們需要您 「 側載 」 的兩個檔案，下載。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-172">Once you have the Windows Device Portal up we need you to “side load” the two files that you downloaded.</span></span>  <span data-ttu-id="e8ab8-173">若要這麼做，您需要往左的提要欄位，直到您取得的 「 應用程式 」 一節，然後按一下 [應用程式]。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-173">To do that you need to go down the left side bar until you get to the “Apps” section and click on “Apps”.</span></span>
5)  <span data-ttu-id="e8ab8-174">然後，您會看到一個畫面，類似於下方。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-174">You will then see a screen that is similar to the below.</span></span>  <span data-ttu-id="e8ab8-175">您想要前往指出 「 安裝應用程式 」 一節，並瀏覽至您解壓縮這兩個的 APPX 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-175">You want to go to the section that says “Install App” and browse to where you unzipped those two APPX files.</span></span>  <span data-ttu-id="e8ab8-176">您可以只執行一次，因此您選取第一個之後然後按一下 [執行] 在 [部署] 區段。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-176">You can only do one at a time, so after you select the first one, then click on “Go” under the Deploy section.</span></span>  <span data-ttu-id="e8ab8-177">然後執行這項操作的第二個的 APPX 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-177">Then do this for the second APPX file.</span></span> 
  <span data-ttu-id="e8ab8-178">![若要安裝側載應用程式的 Windows Device Portal](images/20190322-DevicePortal.png)</span><span class="sxs-lookup"><span data-stu-id="e8ab8-178">![Windows Device Portal to Install Side-Loaded app](images/20190322-DevicePortal.png)</span></span><br>
6)  <span data-ttu-id="e8ab8-179">此時我們相信您的應用程式應該啟動重新運作，而且，您也可以取得存放區。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-179">At this point we believe your applications should start working again and that you can also get to the Store.</span></span>
7)  <span data-ttu-id="e8ab8-180">在某些情況下，就需要執行啟動之前將會啟動受影響的應用程式的 3D 檢視器應用程式的額外步驟。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-180">In some cases, it is necessary run the additional step of launching the 3D Viewer app before affected apps will launch.</span></span> 

<span data-ttu-id="e8ab8-181">我們已經看過的程序以解決此項目，這個問題，並期待繼續使用我們的社群建立成功的混合實境體驗，我們非常感謝您耐心等候。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-181">We appreciate your patience as we have gone through the process to get this issue resolved, and we look forward to continued working with our community to create successful Mixed Reality experiences.</span></span>

## <a name="connecting-to-wifi"></a><span data-ttu-id="e8ab8-182">連線到 WiFi</span><span class="sxs-lookup"><span data-stu-id="e8ab8-182">Connecting to WiFi</span></span>

<span data-ttu-id="e8ab8-183">OOBE 和設定，在沒有認證逾時為 2 分鐘。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-183">During OOBE & Settings, there is a credential timeout of 2 mins.</span></span> <span data-ttu-id="e8ab8-184">使用者名稱/密碼，就必須在 2 分鐘否則將會自動清除 [使用者名稱] 欄位內輸入。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-184">The username/password needs to be entered within 2 mins otherwise the username field will be automatically cleared.</span></span>

<span data-ttu-id="e8ab8-185">我們建議使用藍芽鍵盤輸入長密碼。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-185">We recommend using a Bluetooth keyboard for entering long passwords.</span></span>

## <a name="device-update"></a><span data-ttu-id="e8ab8-186">裝置更新</span><span class="sxs-lookup"><span data-stu-id="e8ab8-186">Device Update</span></span>
* <span data-ttu-id="e8ab8-187">在新的更新後, 的 30 秒殼層可能會消失一次。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-187">30 seconds after a new update, the shell may disappear one time.</span></span> <span data-ttu-id="e8ab8-188">請執行**bloom**繼續您的工作階段的筆勢。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-188">Please perform the **bloom** gesture to resume your session.</span></span>

## <a name="visual-studio"></a><span data-ttu-id="e8ab8-189">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e8ab8-189">Visual Studio</span></span>
* <span data-ttu-id="e8ab8-190">請參閱[安裝工具](install-the-tools.md)建議用於 HoloLens 的開發的 Visual Studio 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-190">See [Install the tools](install-the-tools.md) for the most up-to-date version of Visual Studio recommended for HoloLens development.</span></span>
* <span data-ttu-id="e8ab8-191">在部署您的 HoloLens 從 Visual Studio 應用程式時，您可能會看到錯誤：**要求的作業無法對具有對應的使用者 區段開啟的檔案。(發生例外狀況於 HRESULT:0x800704C8)** 。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-191">When deploying an app from Visual Studio to your HoloLens, you may see the error: **The requested operation cannot be performed on a file with a user-mapped section open. (Exception from HRESULT: 0x800704C8)**.</span></span> <span data-ttu-id="e8ab8-192">如果發生這種情況，再試一次您的部署通常會成功。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-192">If this happens, try again and your deployment will generally succeed.</span></span>

## <a name="emulator"></a><span data-ttu-id="e8ab8-193">模擬器</span><span class="sxs-lookup"><span data-stu-id="e8ab8-193">Emulator</span></span>
* <span data-ttu-id="e8ab8-194">在 Microsoft Store 中的並非所有應用程式都與模擬器相容的。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-194">Not all apps in the Microsoft Store are compatible with the emulator.</span></span> <span data-ttu-id="e8ab8-195">比方說，Young Conker 和片段不是在模擬器上播放。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-195">For example, Young Conker and Fragments are not playable on the emulator.</span></span>
* <span data-ttu-id="e8ab8-196">您無法在模擬器中使用電腦的網路攝影機。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-196">You cannot use the PC webcam in the Emulator.</span></span>
* <span data-ttu-id="e8ab8-197">Windows Device Portal 的即時預覽功能不適用於模擬器。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-197">The Live Preview feature of the Windows Device Portal does not work with the emulator.</span></span> <span data-ttu-id="e8ab8-198">此外，您還是可以擷取混合實境視訊和影像。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-198">You can still capture Mixed Reality videos and images.</span></span>

## <a name="unity"></a><span data-ttu-id="e8ab8-199">Unity</span><span class="sxs-lookup"><span data-stu-id="e8ab8-199">Unity</span></span>
* <span data-ttu-id="e8ab8-200">請參閱[安裝工具](install-the-tools.md)Unity 建議用於 HoloLens 的開發的最新版本。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-200">See [Install the tools](install-the-tools.md) for the most up-to-date version of Unity recommended for HoloLens development.</span></span>
* <span data-ttu-id="e8ab8-201">使用 Unity HoloLens Technical Preview 的已知的問題所述[HoloLens Unity 論壇](http://forum.unity3d.com/threads/known-issues.394627/)。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-201">Known issues with the Unity HoloLens Technical Preview are documented in the [HoloLens Unity forums](http://forum.unity3d.com/threads/known-issues.394627/).</span></span>

## <a name="windows-device-portal"></a><span data-ttu-id="e8ab8-202">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="e8ab8-202">Windows Device Portal</span></span>
* <span data-ttu-id="e8ab8-203">混合實境擷取的即時預覽功能可能會出現幾秒鐘的延遲。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-203">The Live Preview feature in Mixed Reality capture may exhibit several seconds of latency.</span></span>
* <span data-ttu-id="e8ab8-204">在虛擬輸入 頁面上，虛擬的筆勢 區段下的手勢和捲軸控制項沒有正常運作。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-204">On the Virtual Input page, the Gesture and Scroll controls under the Virtual Gestures section are not functional.</span></span> <span data-ttu-id="e8ab8-205">使用它們，會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-205">Using them will have no effect.</span></span> <span data-ttu-id="e8ab8-206">虛擬鍵盤，在相同頁面上的正常運作。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-206">The virtual keyboard on the same page works correctly.</span></span>
* <span data-ttu-id="e8ab8-207">啟用開發人員模式，在設定後，可能需要幾秒鐘的時間才能啟用切換到開啟裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-207">After enabling Developer Mode in Settings, it may take a few seconds before the switch to turn on the Device Portal is enabled.</span></span>

## <a name="api"></a><span data-ttu-id="e8ab8-208">API</span><span class="sxs-lookup"><span data-stu-id="e8ab8-208">API</span></span>
* <span data-ttu-id="e8ab8-209">如果應用程式設定[專注點](focus-point-in-unity.md)背後使用者或以 camera.forward 一般，全像投影不會出現在混合實境擷取相片或視訊。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-209">If the application sets the [focus point](focus-point-in-unity.md) behind the user or the normal to camera.forward, holograms will not appear in Mixed Reality Capture photos or videos.</span></span> <span data-ttu-id="e8ab8-210">直到修正這個錯誤是 Windows，如果應用程式正在設定[專注點](focus-point-in-unity.md)應該確保平面一般設定相反的相機順向 (例如一般 =-camera.forward)。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-210">Until this bug is fixed in Windows, if applications actively set the [focus point](focus-point-in-unity.md) they should ensure the plane normal is set opposite camera-forward (e.g. normal = -camera.forward).</span></span>

## <a name="xbox-wireless-controller"></a><span data-ttu-id="e8ab8-211">Xbox 無線控制器</span><span class="sxs-lookup"><span data-stu-id="e8ab8-211">Xbox Wireless Controller</span></span>
* <span data-ttu-id="e8ab8-212">Xbox 無線控制器 S 必須更新，才能搭配 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-212">Xbox Wireless Controller S must be updated before it can be used with HoloLens.</span></span> <span data-ttu-id="e8ab8-213">確保您[最新狀態](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)之前嘗試配對您的控制器與 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-213">Ensure you are [up to date](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) before attempting to pair your controller with a HoloLens.</span></span>
* <span data-ttu-id="e8ab8-214">如果您重新啟動您的 HoloLens Xbox 無線控制器連線時，控制器會不會自動重新連線到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-214">If you reboot your HoloLens while the Xbox Wireless Controller is connected, the controller will not automatically reconnect to HoloLens.</span></span> <span data-ttu-id="e8ab8-215">指南按鈕燈光會顯示閃爍緩時變直到控制器電源關閉之後 3 分鐘。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-215">The Guide button light will flash slowly until the controller powers off after 3 minutes.</span></span> <span data-ttu-id="e8ab8-216">若要重新連線您的控制器，立即透過保留 [節目表] 按鈕，直到燈號會關閉控制站關閉電源。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-216">To reconnect your controller immediately, power off the controller by holding the Guide button until the light turns off.</span></span> <span data-ttu-id="e8ab8-217">當再次開啟電源您的控制器時，它會重新連線到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-217">When you power your controller on again, it will reconnect to HoloLens.</span></span>
* <span data-ttu-id="e8ab8-218">如果您的 HoloLens 進入待命，Xbox 無線控制器連線時，控制站上的任何輸入會喚醒 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-218">If your HoloLens enters standby while the Xbox Wireless Controller is connected, any input on the controller will wake the HoloLens.</span></span> <span data-ttu-id="e8ab8-219">您可以關閉您的控制站，當您完成來防止使用它。</span><span class="sxs-lookup"><span data-stu-id="e8ab8-219">You can prevent this by powering off your controller when you are done using it.</span></span>
