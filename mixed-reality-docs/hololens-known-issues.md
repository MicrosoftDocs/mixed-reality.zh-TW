---
title: HoloLens 的已知問題
description: 這是可能會影響 HoloLens 開發人員的已知問題清單。
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: 疑難排解, 已知問題, 協助
ms.openlocfilehash: 80bd7499c0075399e516648dd92b7515fdba753a
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122135"
---
# <a name="hololens-known-issues"></a><span data-ttu-id="63180-104">HoloLens 的已知問題</span><span class="sxs-lookup"><span data-stu-id="63180-104">HoloLens known issues</span></span>

<span data-ttu-id="63180-105">這是 HoloLens 影響開發人員的目前已知問題清單。</span><span class="sxs-lookup"><span data-stu-id="63180-105">This is the current list of known issues for HoloLens affecting developers.</span></span> <span data-ttu-id="63180-106">如果您看到奇怪的行為, 請先查看這裡。</span><span class="sxs-lookup"><span data-stu-id="63180-106">Check here first if you are seeing an odd behavior.</span></span> <span data-ttu-id="63180-107">當發現或回報新問題, 或在未來的 HoloLens 軟體更新中解決問題時, 這份清單將會保持更新。</span><span class="sxs-lookup"><span data-stu-id="63180-107">This list will be kept updated as new issues are discovered or reported, or as issues are addressed in future HoloLens software updates.</span></span>

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a><span data-ttu-id="63180-108">無法透過 Visual Studio 連線並部署至 HoloLens</span><span class="sxs-lookup"><span data-stu-id="63180-108">Unable to connect and deploy to HoloLens through Visual Studio</span></span>

>[!NOTE]
><span data-ttu-id="63180-109">上次更新日期:8/8 @ 5: Visual Studio 晚上11點已發行 VS 2019 16.2 版, 其中包含此問題的修正。</span><span class="sxs-lookup"><span data-stu-id="63180-109">Last Update: 8/8 @ 5:11PM - Visual Studio has released VS 2019 Version 16.2 which includes a fix to this issue.</span></span> <span data-ttu-id="63180-110">我們建議您更新到這個最新版本, 以避免發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="63180-110">We recommend updating to this newest version to avoid experiencing this error.</span></span>

<span data-ttu-id="63180-111">Visual Studio 已發行 VS 2019 16.2 版, 其中包含此問題的修正。</span><span class="sxs-lookup"><span data-stu-id="63180-111">Visual Studio has released VS 2019 Version 16.2 which includes a fix to this issue.</span></span> <span data-ttu-id="63180-112">我們建議您更新到這個最新版本, 以避免發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="63180-112">We recommend updating to this newest version to avoid experiencing this error.</span></span>

<span data-ttu-id="63180-113">問題根本原因:使用 Visual Studio 2015 或舊版 Visual Studio 2017 的使用者在其 HoloLens 上部署和偵測應用程式, 然後再使用相同 HoloLens 的最新版本 Visual Studio 2017 或 Visual Studio 2019 將會受到影響。</span><span class="sxs-lookup"><span data-stu-id="63180-113">Issue root-cause: Users who used Visual Studio 2015 or early releases of Visual Studio 2017 to deploy and debug applications on their HoloLens and then subsequently used the latest versions of Visual Studio 2017 or Visual Studio 2019 with the same HoloLens will be affected.</span></span> <span data-ttu-id="63180-114">較新版本的 Visual Studio 會部署新版的元件, 但較舊版本的檔案會保留在裝置上, 導致較新的版本失敗。</span><span class="sxs-lookup"><span data-stu-id="63180-114">The newer releases of Visual Studio deploy a new version of a component, but files from the older version are left over on the device, causing the newer version to fail.</span></span>  <span data-ttu-id="63180-115">這會導致下列錯誤訊息:DEP0100:請確定目標裝置已啟用開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="63180-115">This causes the following error message: DEP0100: Please ensure that target device has developer mode enabled.</span></span> <span data-ttu-id="63180-116"><ip>因錯誤80004005而無法取得開發人員授權。</span><span class="sxs-lookup"><span data-stu-id="63180-116">Could not obtain a developer license on <ip> due to error 80004005.</span></span>
 
<span data-ttu-id="63180-117">**因應措施**：</span><span class="sxs-lookup"><span data-stu-id="63180-117">**Workaround**:</span></span> 

<span data-ttu-id="63180-118">雖然 Visual Studio 2019 16.2 中已修正此問題, 但選擇停留在舊版 Visual Studio 的開發人員可以使用下列步驟來解決問題, 並協助解除封鎖部署和調試:</span><span class="sxs-lookup"><span data-stu-id="63180-118">While this issue is fixed in Visual Studio 2019 16.2, developers who choose to stay in previous versions of Visual Studio can use the following steps to work around the issue and help unblock deployment and debugging:</span></span>  
1. <span data-ttu-id="63180-119">開啟 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63180-119">Open Visual Studio</span></span>
2. <span data-ttu-id="63180-120">檔案 > 新 > 專案</span><span class="sxs-lookup"><span data-stu-id="63180-120">File -> New -> Project</span></span>
3. <span data-ttu-id="63180-121">Visual C# > Windows 桌面 > 主控台應用程式 (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="63180-121">Visual C# -> Windows Desktop -> Console App (.NET Framework)</span></span>
4. <span data-ttu-id="63180-122">提供專案的名稱 (例如 HoloLensDeploymentFix), 並確定架構設定為至少 .NET Framework 4.5, 然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="63180-122">Give the project a name (e.g. HoloLensDeploymentFix) and make sure the Framework is set to at least .NET Framework 4.5 then click OK.</span></span>
5. <span data-ttu-id="63180-123">以滑鼠右鍵按一下方案總管中的 [參考] 節點, 並新增下列參考 (按一下 [流覽] 區段, 然後按一下 [流覽 ...]按鈕):</span><span class="sxs-lookup"><span data-stu-id="63180-123">Right-click on the References node in Solution Explorer and add the following references (click to the 'Browse' section and click the 'Browse...' button):</span></span>
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    ><span data-ttu-id="63180-124">如果您尚未安裝 10.0.18362.0, 請使用您所擁有的最新版本。</span><span class="sxs-lookup"><span data-stu-id="63180-124">If you don't have 10.0.18362.0 installed, use the most recent version that you have.</span></span>
 
6. <span data-ttu-id="63180-125">以滑鼠右鍵按一下方案總管中的專案, 然後選擇 [加入 >] [現有專案]。</span><span class="sxs-lookup"><span data-stu-id="63180-125">Right-click on the project in Solution Explorer and choose Add -> Existing Item.</span></span>
 
7. <span data-ttu-id="63180-126">流覽至 C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86, 並將篩選準則變更為 "All\*Files\*(.)"</span><span class="sxs-lookup"><span data-stu-id="63180-126">Browse to C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86 and change the filter to "All Files (\*.\*)"</span></span>
 
8. <span data-ttu-id="63180-127">選取 [SirepClient] 和 [SshClient], 然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="63180-127">Select both SirepClient.dll and SshClient.dll and click "Add".</span></span>
 
9. <span data-ttu-id="63180-128">在方案總管中找出並選取這兩個檔案 (它們應該位於檔案清單的底部), 然後在屬性視窗中將 [複製到輸出目錄] 變更為 [永遠複製]</span><span class="sxs-lookup"><span data-stu-id="63180-128">Locate and select both files in Solution Explorer (they should be at the bottom of the list of files) and change "Copy to Output Directory" in the Properties window to "Copy always"</span></span>
 
10. <span data-ttu-id="63180-129">在檔案的頂端, 將下列內容新增至現有的 ' using ' 語句清單:</span><span class="sxs-lookup"><span data-stu-id="63180-129">At the top of the file, add the following to the existing list of 'using' statements:</span></span> 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. <span data-ttu-id="63180-130">在 "static void Main (...)" 內, 新增下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="63180-130">Inside of “static void Main(...)”, add the following code:</span></span>
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. <span data-ttu-id="63180-131">組建 > 組建解決方案</span><span class="sxs-lookup"><span data-stu-id="63180-131">Build -> Build Solution</span></span>
 
13. <span data-ttu-id="63180-132">在包含已編譯 .exe 的資料夾中開啟命令提示字元 (例如 C:\MyProjects\HoloLensDeploymentFix\bin\Debug)</span><span class="sxs-lookup"><span data-stu-id="63180-132">Open a command prompt to the folder that contains the compiled .exe (e.g. C:\MyProjects\HoloLensDeploymentFix\bin\Debug)</span></span>
 
14. <span data-ttu-id="63180-133">執行可執行檔, 並提供裝置的 IP 位址做為命令列引數。</span><span class="sxs-lookup"><span data-stu-id="63180-133">Run the executable and provide the device's IP address as a command-line argument.</span></span>  <span data-ttu-id="63180-134">(如果透過 USB 連線, 您可以使用 127.0.0.1, 否則請使用裝置的 WiFi IP 位址)。例如, "HoloLensDeploymentFix 127.0.0.1"</span><span class="sxs-lookup"><span data-stu-id="63180-134">(If connected via USB, you can use 127.0.0.1, otherwise use the device’s WiFi IP address.)  For example, "HoloLensDeploymentFix 127.0.0.1"</span></span>
 
15. <span data-ttu-id="63180-135">一旦工具結束但沒有任何訊息 (這應該只需要幾秒鐘的時間), 您現在就可以從 Visual Studio 2017 或更新版本進行部署和偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="63180-135">Once the tool has exited without any messages (this should only take a few seconds), you will now be able to deploy and debug from Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="63180-136">不需要繼續使用此工具。</span><span class="sxs-lookup"><span data-stu-id="63180-136">Continued use of the tool is not necessary.</span></span>


## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a><span data-ttu-id="63180-137">在 HoloLens 上啟動 Microsoft Store 和應用程式的問題</span><span class="sxs-lookup"><span data-stu-id="63180-137">Issues launching the Microsoft Store and apps on HoloLens</span></span>

>[!NOTE]
><span data-ttu-id="63180-138">上次更新日期:4/2 @ 10 AM-已解決問題。</span><span class="sxs-lookup"><span data-stu-id="63180-138">Last Update: 4/2 @ 10 AM - Issue resolved.</span></span> 

<span data-ttu-id="63180-139">當您嘗試在 HoloLens 上啟動 Microsoft Store 和應用程式時, 可能會遇到問題。</span><span class="sxs-lookup"><span data-stu-id="63180-139">You may experience issues when trying to launch the Microsoft Store and apps on HoloLens.</span></span> <span data-ttu-id="63180-140">我們已判定當背景應用程式更新在特定序列中部署較新版本的 framework 套件, 而其中一或多個相依應用程式仍在執行時, 就會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="63180-140">We've determined that the issue occurs when background app updates deploy a newer version of framework packages in specific sequences while one or more of their dependent apps are still running.</span></span> <span data-ttu-id="63180-141">在此情況下, 自動應用程式更新已提供新版的 .NET Native Framework (10.0.25531 到 10.0.27413), 導致執行的應用程式無法針對所有使用舊版 Framework 的執行中應用程式進行正確更新。</span><span class="sxs-lookup"><span data-stu-id="63180-141">In this case,  an automatic app update delivered a new version of the .NET Native Framework (version 10.0.25531 to 10.0.27413) caused the apps that are running to not correctly update for all running apps consuming the prior version of the framework.</span></span>  <span data-ttu-id="63180-142">架構更新的流程如下所示:</span><span class="sxs-lookup"><span data-stu-id="63180-142">The flow for framework update is as follows: -</span></span>

1.  <span data-ttu-id="63180-143">新的架構套件會從存放區下載並安裝</span><span class="sxs-lookup"><span data-stu-id="63180-143">The new framework package is downloaded from the store and installed</span></span>
2.  <span data-ttu-id="63180-144">所有使用舊版架構的應用程式都會「更新」, 以使用較新的版本</span><span class="sxs-lookup"><span data-stu-id="63180-144">All apps using the older framework are ‘updated’ to use the newer version</span></span>

<span data-ttu-id="63180-145">如果步驟2在完成前中斷, 則未註冊新架構的任何應用程式都將無法從 [開始] 功能表啟動。</span><span class="sxs-lookup"><span data-stu-id="63180-145">If step 2 is interrupted before completion then any apps for which the newer framework wasn’t registered will fail to launch from the start menu.</span></span>  <span data-ttu-id="63180-146">我們相信 HoloLens 上的任何應用程式可能會受到此問題的影響。</span><span class="sxs-lookup"><span data-stu-id="63180-146">We believe any app on HoloLens could be affected by this issue.</span></span>

<span data-ttu-id="63180-147">有些使用者已回報關閉無回應應用程式並啟動其他應用程式 (例如意見反應中樞、3D 檢視器或相片) 可解決問題; 不過, 這不會在 100% 的時間內生效。</span><span class="sxs-lookup"><span data-stu-id="63180-147">Some users have reported that closing hung apps and launching other apps such as Feedback Hub, 3D Viewer or Photos resolves the issue for them - however, this does not work 100% of the time.</span></span>

<span data-ttu-id="63180-148">根本原因是此問題不會造成更新本身, 但是作業系統中導致 .NET Native framework 更新的錯誤處理不正確。</span><span class="sxs-lookup"><span data-stu-id="63180-148">We have root caused that this issue was not caused the update itself, but a bug in the OS that resulted in the .NET Native framework update being handled incorrectly.</span></span> <span data-ttu-id="63180-149">我們很高興宣佈, 我們已識別出修正程式, 並已發行包含修正程式的更新 (OS 版本 17763.380)。</span><span class="sxs-lookup"><span data-stu-id="63180-149">We are pleased to announce that we have identified a fix and have released an update (OS version 17763.380) containing the fix.</span></span> 

<span data-ttu-id="63180-150">若要查看您的裝置是否可以進行更新, 請:</span><span class="sxs-lookup"><span data-stu-id="63180-150">To see if your device can take the update please:</span></span>

1.  <span data-ttu-id="63180-151">移至 [設定] 應用程式, 並開啟 [更新 & 安全性]</span><span class="sxs-lookup"><span data-stu-id="63180-151">Go to the “Settings” app and open “Update & Security”</span></span>
2.  <span data-ttu-id="63180-152">按一下 [檢查更新]</span><span class="sxs-lookup"><span data-stu-id="63180-152">Click “Check for Updates”</span></span>
3.  <span data-ttu-id="63180-153">如果有17763.380 的更新可用, 請更新為此組建, 以接收應用程式停止回應 bug 的修正</span><span class="sxs-lookup"><span data-stu-id="63180-153">If update to 17763.380 is available, please update to this build to receive the fix for the App Hang bug</span></span>
4.  <span data-ttu-id="63180-154">更新為此版本的 OS 時, 應用程式應該會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="63180-154">Upon updating to this version of the OS, the Apps should work as expected.</span></span>

<span data-ttu-id="63180-155">此外, 在每次 HoloLens 作業系統版本中, 我們已將 FFU 映射張貼到 Microsoft 下載中心, 網址 https://aka.ms/hololensdownload/10.0.17763.380 為。</span><span class="sxs-lookup"><span data-stu-id="63180-155">Additionally, as we do with every HoloLens OS release, we have posted the FFU image to the Microsoft Download Center at https://aka.ms/hololensdownload/10.0.17763.380.</span></span> 

<span data-ttu-id="63180-156">如果您不想要進行更新, 我們已發行新版本的 Microsoft Store UWP 應用程式, 3/29。</span><span class="sxs-lookup"><span data-stu-id="63180-156">If you would not like to take the update, we have released a new version of the Microsoft Store UWP app as of 3/29.</span></span> <span data-ttu-id="63180-157">當您擁有更新版本的存放區之後:</span><span class="sxs-lookup"><span data-stu-id="63180-157">Once you have the updated version of the Store:</span></span>

1) <span data-ttu-id="63180-158">開啟存放區, 並確認它已載入。</span><span class="sxs-lookup"><span data-stu-id="63180-158">Open the Store and confirm that it loads.</span></span>
2) <span data-ttu-id="63180-159">使用 Bloom 手勢來開啟功能表。</span><span class="sxs-lookup"><span data-stu-id="63180-159">Use the Bloom Gesture to open the menu.</span></span>
3) <span data-ttu-id="63180-160">嘗試開啟先前中斷的應用程式</span><span class="sxs-lookup"><span data-stu-id="63180-160">Attempt to open previously broken apps</span></span>
3) <span data-ttu-id="63180-161">如果仍然無法啟動, 請按住中斷應用程式的圖示, 然後選取 [卸載]。</span><span class="sxs-lookup"><span data-stu-id="63180-161">If it still cannot be launched, tap and hold the icon of the broken app and select uninstall.</span></span>
4) <span data-ttu-id="63180-162">從存放區 Resinstall 這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="63180-162">Resinstall these apps from the store.</span></span>

<span data-ttu-id="63180-163">如果您的裝置仍然無法載入應用程式, 您可以執行下列動作, 透過下載中心側載某個版本的 .NET Native Framework 和執行時間:</span><span class="sxs-lookup"><span data-stu-id="63180-163">If your device is still unable to load apps, you can sideload a version of the .NET Native Framework and Runtime through the download center by doing:</span></span>

1)  <span data-ttu-id="63180-164">請從 Microsoft 下載中心下載[此 zip](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)檔案。</span><span class="sxs-lookup"><span data-stu-id="63180-164">Please download [this zip file](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) from the Microsoft Download Center.</span></span>  <span data-ttu-id="63180-165">解壓縮會產生兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="63180-165">Unzipping will produce two files.</span></span>  <span data-ttu-id="63180-166">NET.TCP 和 net.tcp. .appx........。</span><span class="sxs-lookup"><span data-stu-id="63180-166">Microsoft.NET.Native.Runtime.1.7.appx and Microsoft.NET.Native.Framework.1.7.appx</span></span>
2)  <span data-ttu-id="63180-167">請確認您的裝置已針對開發人員解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="63180-167">Please verify that your device is dev unlocked.</span></span>  <span data-ttu-id="63180-168">如果您還沒有這麼做, 請在[這裡](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)進行操作。</span><span class="sxs-lookup"><span data-stu-id="63180-168">If you haven’t done that before the instructions to do that are [here](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).</span></span>
3)  <span data-ttu-id="63180-169">接著, 您會想要進入 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="63180-169">You then want to get into the Windows Device Portal.</span></span>  <span data-ttu-id="63180-170">我們的建議是透過 USB 來執行這項操作, 您可以在 http://127.0.0.1:10080 瀏覽器中輸入來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="63180-170">Our recommendation is to do this over USB and you would do that by typing http://127.0.0.1:10080 into your browser.</span></span>  
4)  <span data-ttu-id="63180-171">當您完成 Windows 裝置入口網站後, 我們需要您「側載入」您所下載的兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="63180-171">Once you have the Windows Device Portal up we need you to “side load” the two files that you downloaded.</span></span>  <span data-ttu-id="63180-172">若要這麼做, 您必須往下移至 [應用程式] 區段, 然後按一下 [應用程式]。</span><span class="sxs-lookup"><span data-stu-id="63180-172">To do that you need to go down the left side bar until you get to the “Apps” section and click on “Apps”.</span></span>
5)  <span data-ttu-id="63180-173">然後您會看到類似下面的畫面。</span><span class="sxs-lookup"><span data-stu-id="63180-173">You will then see a screen that is similar to the below.</span></span>  <span data-ttu-id="63180-174">您想要移至顯示「安裝應用程式」的區段, 然後流覽至您解壓縮這兩個 APPX 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="63180-174">You want to go to the section that says “Install App” and browse to where you unzipped those two APPX files.</span></span>  <span data-ttu-id="63180-175">您一次只能執行一個, 因此在您選取第一個, 然後按一下 [部署] 區段下的 [移至]。</span><span class="sxs-lookup"><span data-stu-id="63180-175">You can only do one at a time, so after you select the first one, then click on “Go” under the Deploy section.</span></span>  <span data-ttu-id="63180-176">然後為第二個 APPX 檔案執行此動作。</span><span class="sxs-lookup"><span data-stu-id="63180-176">Then do this for the second APPX file.</span></span> 
  <span data-ttu-id="63180-177">![安裝側載應用程式的 Windows 裝置入口網站](images/20190322-DevicePortal.png)</span><span class="sxs-lookup"><span data-stu-id="63180-177">![Windows Device Portal to Install Side-Loaded app](images/20190322-DevicePortal.png)</span></span><br>
6)  <span data-ttu-id="63180-178">此時, 我們認為您的應用程式應該會再次開始運作, 而且您也可以取得存放區。</span><span class="sxs-lookup"><span data-stu-id="63180-178">At this point we believe your applications should start working again and that you can also get to the Store.</span></span>
7)  <span data-ttu-id="63180-179">在某些情況下, 必須先執行額外的步驟來啟動3D 檢視器應用程式, 受影響的應用程式才會啟動。</span><span class="sxs-lookup"><span data-stu-id="63180-179">In some cases, it is necessary run the additional step of launching the 3D Viewer app before affected apps will launch.</span></span> 

<span data-ttu-id="63180-180">我們非常感謝您的耐心等候, 因為我們已完成解決此問題的流程, 我們期待繼續與我們的社區合作, 以建立成功的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="63180-180">We appreciate your patience as we have gone through the process to get this issue resolved, and we look forward to continued working with our community to create successful Mixed Reality experiences.</span></span>

## <a name="connecting-to-wifi"></a><span data-ttu-id="63180-181">連接到 WiFi</span><span class="sxs-lookup"><span data-stu-id="63180-181">Connecting to WiFi</span></span>

<span data-ttu-id="63180-182">在 OOBE & 設定期間, 有2分鐘的認證超時。</span><span class="sxs-lookup"><span data-stu-id="63180-182">During OOBE & Settings, there is a credential timeout of 2 mins.</span></span> <span data-ttu-id="63180-183">使用者名稱/密碼必須在2分鐘內輸入, 否則 [使用者名稱] 欄位將會自動清除。</span><span class="sxs-lookup"><span data-stu-id="63180-183">The username/password needs to be entered within 2 mins otherwise the username field will be automatically cleared.</span></span>

<span data-ttu-id="63180-184">我們建議使用藍牙鍵盤來輸入長密碼。</span><span class="sxs-lookup"><span data-stu-id="63180-184">We recommend using a Bluetooth keyboard for entering long passwords.</span></span>

>[!NOTE]
> <span data-ttu-id="63180-185">如果在 OOBE 期間選取了錯誤的網路, 裝置就必須完全重設。</span><span class="sxs-lookup"><span data-stu-id="63180-185">If the wrong network is selected during OOBE the device will need to be fully reset.</span></span> <span data-ttu-id="63180-186">您可以在這裡找到指示[。](https://docs.microsoft.com/en-us/windows/mixed-reality/reset-or-recover-your-hololens#perform-a-full-device-recovery)</span><span class="sxs-lookup"><span data-stu-id="63180-186">Instructions can be found [here.](https://docs.microsoft.com/en-us/windows/mixed-reality/reset-or-recover-your-hololens#perform-a-full-device-recovery)</span></span> 

## <a name="device-update"></a><span data-ttu-id="63180-187">裝置更新</span><span class="sxs-lookup"><span data-stu-id="63180-187">Device Update</span></span>
* <span data-ttu-id="63180-188">在新的更新之後30秒, shell 可能會消失一次。</span><span class="sxs-lookup"><span data-stu-id="63180-188">30 seconds after a new update, the shell may disappear one time.</span></span> <span data-ttu-id="63180-189">請執行**bloom**手勢來繼續您的會話。</span><span class="sxs-lookup"><span data-stu-id="63180-189">Please perform the **bloom** gesture to resume your session.</span></span>

## <a name="visual-studio"></a><span data-ttu-id="63180-190">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63180-190">Visual Studio</span></span>
* <span data-ttu-id="63180-191">如需適用于 HoloLens 開發的最新版本 Visual Studio, 請參閱[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="63180-191">See [Install the tools](install-the-tools.md) for the most up-to-date version of Visual Studio recommended for HoloLens development.</span></span>
* <span data-ttu-id="63180-192">將應用程式從 Visual Studio 部署至 HoloLens 時, 您可能會看到下列錯誤:**無法在開啟使用者對應區段的檔案上執行要求的作業。(發生例外狀況於 HRESULT:0x800704C8)** 。</span><span class="sxs-lookup"><span data-stu-id="63180-192">When deploying an app from Visual Studio to your HoloLens, you may see the error: **The requested operation cannot be performed on a file with a user-mapped section open. (Exception from HRESULT: 0x800704C8)**.</span></span> <span data-ttu-id="63180-193">如果發生這種情況, 請再試一次, 您的部署通常會成功。</span><span class="sxs-lookup"><span data-stu-id="63180-193">If this happens, try again and your deployment will generally succeed.</span></span>

## <a name="emulator"></a><span data-ttu-id="63180-194">模擬器</span><span class="sxs-lookup"><span data-stu-id="63180-194">Emulator</span></span>
* <span data-ttu-id="63180-195">並非 Microsoft Store 中的所有應用程式都與模擬器相容。</span><span class="sxs-lookup"><span data-stu-id="63180-195">Not all apps in the Microsoft Store are compatible with the emulator.</span></span> <span data-ttu-id="63180-196">例如, 在模擬器上無法播放年輕 Conker 和片段。</span><span class="sxs-lookup"><span data-stu-id="63180-196">For example, Young Conker and Fragments are not playable on the emulator.</span></span>
* <span data-ttu-id="63180-197">您無法在模擬器中使用電腦網路攝影機。</span><span class="sxs-lookup"><span data-stu-id="63180-197">You cannot use the PC webcam in the Emulator.</span></span>
* <span data-ttu-id="63180-198">Windows 裝置入口網站的 [即時預覽] 功能無法與模擬器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="63180-198">The Live Preview feature of the Windows Device Portal does not work with the emulator.</span></span> <span data-ttu-id="63180-199">您仍然可以捕捉混合現實影片和影像。</span><span class="sxs-lookup"><span data-stu-id="63180-199">You can still capture Mixed Reality videos and images.</span></span>

## <a name="unity"></a><span data-ttu-id="63180-200">Unity</span><span class="sxs-lookup"><span data-stu-id="63180-200">Unity</span></span>
* <span data-ttu-id="63180-201">如需 HoloLens 開發的最新版本建議, 請參閱[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="63180-201">See [Install the tools](install-the-tools.md) for the most up-to-date version of Unity recommended for HoloLens development.</span></span>
* <span data-ttu-id="63180-202">Unity HoloLens Technical Preview 的已知問題記載于[HoloLens Unity 論壇](http://forum.unity3d.com/threads/known-issues.394627/)。</span><span class="sxs-lookup"><span data-stu-id="63180-202">Known issues with the Unity HoloLens Technical Preview are documented in the [HoloLens Unity forums](http://forum.unity3d.com/threads/known-issues.394627/).</span></span>

## <a name="windows-device-portal"></a><span data-ttu-id="63180-203">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="63180-203">Windows Device Portal</span></span>
* <span data-ttu-id="63180-204">混合現實 capture 中的即時預覽功能可能會出現數秒的延遲。</span><span class="sxs-lookup"><span data-stu-id="63180-204">The Live Preview feature in Mixed Reality capture may exhibit several seconds of latency.</span></span>
* <span data-ttu-id="63180-205">在 [虛擬輸入] 頁面上, [虛擬手勢] 區段下的筆勢和 Scroll 控制項無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="63180-205">On the Virtual Input page, the Gesture and Scroll controls under the Virtual Gestures section are not functional.</span></span> <span data-ttu-id="63180-206">使用它們將不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="63180-206">Using them will have no effect.</span></span> <span data-ttu-id="63180-207">相同頁面上的虛擬鍵盤運作正常。</span><span class="sxs-lookup"><span data-stu-id="63180-207">The virtual keyboard on the same page works correctly.</span></span>
* <span data-ttu-id="63180-208">啟用 [設定] 中的 [開發人員模式] 之後, 可能需要幾秒鐘的時間, 才能開啟啟用裝置入口網站的交換器。</span><span class="sxs-lookup"><span data-stu-id="63180-208">After enabling Developer Mode in Settings, it may take a few seconds before the switch to turn on the Device Portal is enabled.</span></span>

## <a name="api"></a><span data-ttu-id="63180-209">API</span><span class="sxs-lookup"><span data-stu-id="63180-209">API</span></span>
* <span data-ttu-id="63180-210">如果應用程式將使用者背後的[焦點點](focus-point-in-unity.md)設定為, 或將其設為一般相機。轉寄, 則全像投影不會出現在混合現實的 Capture 相片或影片中。</span><span class="sxs-lookup"><span data-stu-id="63180-210">If the application sets the [focus point](focus-point-in-unity.md) behind the user or the normal to camera.forward, holograms will not appear in Mixed Reality Capture photos or videos.</span></span> <span data-ttu-id="63180-211">在 Windows 中修正此錯誤之前, 如果應用程式主動設定[焦點](focus-point-in-unity.md), 則應該確保平面的垂直方向是設定為與相機向前 (例如, normal =-攝影機)。</span><span class="sxs-lookup"><span data-stu-id="63180-211">Until this bug is fixed in Windows, if applications actively set the [focus point](focus-point-in-unity.md) they should ensure the plane normal is set opposite camera-forward (e.g. normal = -camera.forward).</span></span>

## <a name="xbox-wireless-controller"></a><span data-ttu-id="63180-212">Xbox 無線控制器</span><span class="sxs-lookup"><span data-stu-id="63180-212">Xbox Wireless Controller</span></span>
* <span data-ttu-id="63180-213">Xbox 無線控制器必須先更新, 才能與 HoloLens 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="63180-213">Xbox Wireless Controller S must be updated before it can be used with HoloLens.</span></span> <span data-ttu-id="63180-214">請確定您是[最](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)新的, 再嘗試將控制器與 HoloLens 配對。</span><span class="sxs-lookup"><span data-stu-id="63180-214">Ensure you are [up to date](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) before attempting to pair your controller with a HoloLens.</span></span>
* <span data-ttu-id="63180-215">如果您在 Xbox 無線控制器連線時重新開機 HoloLens, 控制器將不會自動重新連接至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="63180-215">If you reboot your HoloLens while the Xbox Wireless Controller is connected, the controller will not automatically reconnect to HoloLens.</span></span> <span data-ttu-id="63180-216">在3分鐘後控制器電源關閉後, 此指南按鈕 light 會慢慢閃爍。</span><span class="sxs-lookup"><span data-stu-id="63180-216">The Guide button light will flash slowly until the controller powers off after 3 minutes.</span></span> <span data-ttu-id="63180-217">若要立即重新連線您的控制器, 請按住 [節目表] 按鈕以關閉控制器電源, 直到燈關閉為止。</span><span class="sxs-lookup"><span data-stu-id="63180-217">To reconnect your controller immediately, power off the controller by holding the Guide button until the light turns off.</span></span> <span data-ttu-id="63180-218">當您再次開啟控制器電源時, 它會重新連線至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="63180-218">When you power your controller on again, it will reconnect to HoloLens.</span></span>
* <span data-ttu-id="63180-219">如果您的 HoloLens 在 Xbox 無線控制器連線時進入待命, 控制器上的任何輸入都會喚醒 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="63180-219">If your HoloLens enters standby while the Xbox Wireless Controller is connected, any input on the controller will wake the HoloLens.</span></span> <span data-ttu-id="63180-220">您可以在使用完控制器後關閉它, 藉此避免發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="63180-220">You can prevent this by powering off your controller when you are done using it.</span></span>
