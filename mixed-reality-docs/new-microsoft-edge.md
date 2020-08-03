---
title: Windows Mixed Reality 和新的 Microsoft Edge
description: 準備開始進行 Windows Mixed Reality 中新的 Microsoft Edge。 包含預期的變更、要查看的更新，以及已知問題。
author: mattzmsft
ms.author: mazeller
ms.date: 07/31/2020
ms.topic: article
keywords: edge、new、沉浸式 web、microsoft edge、browser、vr
ms.openlocfilehash: 107b825496cc318042da0e0cd9acdbe482994a69
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476980"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a><span data-ttu-id="db753-105">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="db753-105">Windows Mixed Reality and the new Microsoft Edge</span></span>

<span data-ttu-id="db753-106">[新的 Microsoft Edge 現在已可供下載](https://blogs.windows.com/windowsexperience/?p=173496)，但客戶也可以在未來數個月內以測量的推出方法，[等待它安裝到 Windows 10 的後續更新中](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)。</span><span class="sxs-lookup"><span data-stu-id="db753-106">The [new Microsoft Edge is now available for download](https://blogs.windows.com/windowsexperience/?p=173496), but customers can also [wait for it to be installed in a future update to Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), following a measured roll-out approach over the next several months.</span></span> 

<span data-ttu-id="db753-107">透過這段新聞，**我們想要讓 Windows Mixed REALITY VR 耳機客戶知道新的 Microsoft Edge 有哪些內容，並通知您一些可改善 Windows Mixed Reality web 流覽體驗的擱置更新**。</span><span class="sxs-lookup"><span data-stu-id="db753-107">With this news, **we wanted to let Windows Mixed Reality VR headset customers know what to expect from the new Microsoft Edge and inform you of some pending updates that will improve your web browsing experience in Windows Mixed Reality**.</span></span>

## <a name="introducing-the-new-microsoft-edge"></a><span data-ttu-id="db753-108">新的 Microsoft Edge 簡介</span><span class="sxs-lookup"><span data-stu-id="db753-108">Introducing the new Microsoft Edge</span></span>

<span data-ttu-id="db753-109">新的 Microsoft Edge 採用桌上型電腦上[的 Chromium 開放原始碼專案](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)，為客戶建立更佳的 web 相容性，並減少所有 網頁程式開發人員的 web 片段。</span><span class="sxs-lookup"><span data-stu-id="db753-109">The new Microsoft Edge [adopts the Chromium open source project](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) on the desktop to create better web compatibility for customers and less fragmentation of the web for all web developers.</span></span> <span data-ttu-id="db753-110">它也會在啟動時支援 WebXR，這是建立 VR 耳機的沉浸式 web 體驗的新標準，用來取代 WebVR。</span><span class="sxs-lookup"><span data-stu-id="db753-110">It will also support WebXR at launch, the new standard for creating immersive web experiences for VR headsets, in place of WebVR.</span></span>

>[!IMPORTANT]
><span data-ttu-id="db753-111">當您在最新的 Windows 10 裝置上安裝 Microsoft Edge 時，將會取代您電腦上先前的（舊版）版本。</span><span class="sxs-lookup"><span data-stu-id="db753-111">When you install Microsoft Edge on an up-to-date Windows 10 device, it will replace the previous (legacy) version on your PC.</span></span>

## <a name="getting-ready-for-the-new-microsoft-edge"></a><span data-ttu-id="db753-112">準備開始新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="db753-112">Getting ready for the new Microsoft Edge</span></span>

<span data-ttu-id="db753-113">Windows Mixed Reality VR 耳機客戶若想要在混合現實首頁中使用新的 Microsoft Edge，應**升級至 Windows 10 1903 版或更新版本，以在混合現實首頁中提供 Win32 應用程式的原生支援（例如新的 Microsoft Edge）** 。</span><span class="sxs-lookup"><span data-stu-id="db753-113">Windows Mixed Reality VR headset customers who want to use the new Microsoft Edge in the mixed reality home should **upgrade to Windows 10 Version 1903 or later for native support of Win32 applications (like the new Microsoft Edge)** in the mixed reality home.</span></span> <span data-ttu-id="db753-114">檢查 Windows Update 或[手動安裝最新版的 Windows 10](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="db753-114">Check Windows Update or [manually install the latest version of Windows 10](https://www.microsoft.com/en-us/software-download/windows10).</span></span>

<span data-ttu-id="db753-115">針對混合現實首頁中最佳可能的 Microsoft Edge 體驗，我們也建議您等待**windows 10 第 1 1903 版（或更新版本）的2020-01 累積更新抵達新 Microsoft edge 的一些重要 Windows Mixed reality 優化**，這應該會在一月月底的 Windows Update 中提供。</span><span class="sxs-lookup"><span data-stu-id="db753-115">For the best possible Microsoft Edge experience in the mixed reality home, we also recommend waiting for **some key Windows Mixed Reality optimizations for the new Microsoft Edge arriving with the 2020-01 Cumulative update for Windows 10 Version 1903 (or later)**, which should be available in Windows Update by the end of January.</span></span>

>[!IMPORTANT]
><span data-ttu-id="db753-116">如果您選擇在進行這些更新之前下載新的 Microsoft Edge，在 Windows Mixed Reality 中會有一些已知的問題（您可以在下方閱讀）。</span><span class="sxs-lookup"><span data-stu-id="db753-116">If you opt to download the new Microsoft Edge before taking these updates, there will be some known issues with its behavior in Windows Mixed Reality (which you can read about below).</span></span>

## <a name="known-issues"></a><span data-ttu-id="db753-117">已知問題</span><span class="sxs-lookup"><span data-stu-id="db753-117">Known issues</span></span>

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a><span data-ttu-id="db753-118">Windows 10 1903 版（或更新版本）的2020-01 累積更新所解決的已知問題</span><span class="sxs-lookup"><span data-stu-id="db753-118">Known issues resolved by the 2020-01 Cumulative update for Windows 10 Version 1903 (or later)</span></span>

- <span data-ttu-id="db753-119">啟動任何 Win32 應用程式（包括新的 Microsoft Edge）都會讓頭戴式裝置顯示短暫凍結。</span><span class="sxs-lookup"><span data-stu-id="db753-119">Launching any Win32 app, including the new Microsoft Edge, causes the headset display to briefly freeze.</span></span>
- <span data-ttu-id="db753-120">Microsoft Edge 磚會從 Windows Mixed Reality 的 [開始] 功能表中消失（您可以在 [傳統應用程式] 資料夾中找到它）。</span><span class="sxs-lookup"><span data-stu-id="db753-120">The Microsoft Edge tile disappears from the Windows Mixed Reality Start menu (you can find it in the “Classic apps” folder).</span></span>
- <span data-ttu-id="db753-121">來自先前 Microsoft Edge 的 Windows 仍然會放在混合現實首頁，但無法使用。</span><span class="sxs-lookup"><span data-stu-id="db753-121">Windows from the previous Microsoft Edge are still placed around the mixed reality home, but cannot be used.</span></span> <span data-ttu-id="db753-122">嘗試啟用這些 windows 會啟動桌面應用程式內的邊緣。</span><span class="sxs-lookup"><span data-stu-id="db753-122">Attempting to activate those windows launches Edge inside of the Desktop app.</span></span>
- <span data-ttu-id="db753-123">選取混合現實首頁中的超連結，就會在桌面上啟動網頁瀏覽器，而不是使用混合現實首頁。</span><span class="sxs-lookup"><span data-stu-id="db753-123">Selecting a hyperlink in the mixed reality home launches a web browser on the desktop instead of the mixed reality home.</span></span>
- <span data-ttu-id="db753-124">雖然 WebVR 不受支援，但 WebVR 展示應用程式存在於混合現實首頁中。</span><span class="sxs-lookup"><span data-stu-id="db753-124">The WebVR Showcase app is present in the mixed reality home, despite WebVR no longer being supported.</span></span>
- <span data-ttu-id="db753-125">鍵盤啟動和視覺效果的一般改良功能。</span><span class="sxs-lookup"><span data-stu-id="db753-125">General improvements to keyboard launch and visuals.</span></span>

### <a name="monitor-and-input-handling-issues"></a><span data-ttu-id="db753-126">監視和輸入處理問題</span><span class="sxs-lookup"><span data-stu-id="db753-126">Monitor and input handling issues</span></span>

<span data-ttu-id="db753-127">取得 Windows 10 版本1903（或更新版本）的2020-01 累積更新之後，虛擬監視器會在 [設定] 中顯示為一般實體監視器， **> 系統 >** 在 Windows Mixed Reality 會話期間顯示。</span><span class="sxs-lookup"><span data-stu-id="db753-127">After taking the 2020-01 Cumulative update for Windows 10 Version 1903 (or later), virtual monitors will appear as generic physical monitors in **Settings > System > Display** during Windows Mixed Reality sessions.</span></span> <span data-ttu-id="db753-128">某些客戶（特別是具有多個實體監視器的客戶）可能會注意到桌上出版面配置和輸入處理的問題。</span><span class="sxs-lookup"><span data-stu-id="db753-128">Some customers, especially those with more than one physical monitor, may notice issues with desktop layout and input handling as a result.</span></span>

<span data-ttu-id="db753-129">**發生這種情況的原因**</span><span class="sxs-lookup"><span data-stu-id="db753-129">**Why this happens**</span></span>

<span data-ttu-id="db753-130">Windows Mixed Reality 中的傳統 Win32 應用程式支援是在[windows 10 5 月2019更新](#release-notes-may-2019.md)中引進。</span><span class="sxs-lookup"><span data-stu-id="db753-130">Support for classic Win32 applications in Windows Mixed Reality was introduced with the [Windows 10 May 2019 Update](#release-notes-may-2019.md).</span></span> <span data-ttu-id="db753-131">若要啟用這種支援，必須建立虛擬監視器來裝載 Win32 應用程式。</span><span class="sxs-lookup"><span data-stu-id="db753-131">To enable this support, a virtual monitor must be created to host the Win32 application.</span></span> <span data-ttu-id="db753-132">每次啟動新的 Win32 應用程式時，都必須建立另一個虛擬監視器。</span><span class="sxs-lookup"><span data-stu-id="db753-132">Each time a new Win32 application is launched, another virtual monitor has to be created.</span></span> <span data-ttu-id="db753-133">可惜的是，建立虛擬監視器是一項密集的工作，可能會導致頭戴式裝置顯示短暫凍結。</span><span class="sxs-lookup"><span data-stu-id="db753-133">Unfortunately, creating a virtual monitor is an intensive task that can cause the headset display to briefly freeze.</span></span> <span data-ttu-id="db753-134">客戶提供意見反應，表示這是不舒服且干擾性的體驗。</span><span class="sxs-lookup"><span data-stu-id="db753-134">Customers offered feedback that this was an uncomfortable and disruptive experience.</span></span> <span data-ttu-id="db753-135">基於該意見反應，隨著 Win32 應用程式的使用增加，我們決定在啟動 Windows Mixed Reality 期間預先配置三個虛擬監視器，以避免這種中斷情形，並讓客戶啟動最多三個並行的 Win32 應用程式，而不會出現耳機顯示凍結。</span><span class="sxs-lookup"><span data-stu-id="db753-135">Because of that feedback, alongside increased usage of Win32 applications, we made the decision to pre-allocate three virtual monitors during startup of Windows Mixed Reality to prevent this disruption and enable customers to launch up to three concurrent Win32 applications without experiencing the headset display freeze.</span></span>

<span data-ttu-id="db753-136">**因應措施**</span><span class="sxs-lookup"><span data-stu-id="db753-136">**Workaround**</span></span>

<span data-ttu-id="db753-137">我們已收到一些客戶的意見反應，特別是有多個實體監視器的客戶，會想要停用此虛擬監視器預先配置。</span><span class="sxs-lookup"><span data-stu-id="db753-137">We've since received feedback that some customers, especially those with multiple physical monitors, would prefer to disable this virtual monitor pre-allocation.</span></span> <span data-ttu-id="db753-138">為了提供客戶控制和選擇，我們啟用了一個因應變更登錄機碼值的因應措施（適用于 Windows 10 版本2004的2020-07 累積更新）。</span><span class="sxs-lookup"><span data-stu-id="db753-138">To give customers control and choice, we've enabled a workaround that involves changing a registry key value (available with the 2020-07 Cumulative Update for Windows 10 Version 2004).</span></span>

>[!NOTE]
><span data-ttu-id="db753-139">修改登錄機碼值適用于 advanced users。</span><span class="sxs-lookup"><span data-stu-id="db753-139">Modifying registry key values is intended for advanced users.</span></span>

>[!WARNING]
><span data-ttu-id="db753-140">停用虛擬監視器預先配置可能會導致您的耳機顯示在 Windows Mixed Reality 中啟動 Win32 應用程式（例如，串流、新的 Microsoft Edge 或 Google Chrome）時短暫凍結。</span><span class="sxs-lookup"><span data-stu-id="db753-140">Disabling virtual monitor pre-allocation may result in your headset display briefly freezing when you launch a Win32 application (such as Steam, the new Microsoft Edge, or Google Chrome) in Windows Mixed Reality.</span></span>

<span data-ttu-id="db753-141">若要停用虛擬監視器預先配置：</span><span class="sxs-lookup"><span data-stu-id="db753-141">To disable virtual monitor pre-allocation:</span></span>
1. <span data-ttu-id="db753-142">檢查適用于 Windows 10 版本 2004 2020-07 累積更新的**Windows Update** ，並在可用時安裝更新。</span><span class="sxs-lookup"><span data-stu-id="db753-142">Check **Windows Update** for the 2020-07 Cumulative Update for Windows 10 Version 2004 and install the update when available.</span></span>
2. <span data-ttu-id="db753-143">啟動 [**登錄編輯程式**]。</span><span class="sxs-lookup"><span data-stu-id="db753-143">Launch **Registry Editor**.</span></span>
3. <span data-ttu-id="db753-144">流覽至 HKEY_CURRENT_USER \SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\PreallocateVirtualMonitors</span><span class="sxs-lookup"><span data-stu-id="db753-144">Navigate to HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\PreallocateVirtualMonitors</span></span>
4. <span data-ttu-id="db753-145">將 DWORD 值從1（其預設值）變更為0（零）</span><span class="sxs-lookup"><span data-stu-id="db753-145">Change the DWORD value from 1 (its default value) to 0 (zero)</span></span>
    * <span data-ttu-id="db753-146">TRUE-1</span><span class="sxs-lookup"><span data-stu-id="db753-146">TRUE - 1</span></span>
    * <span data-ttu-id="db753-147">FALSE-0</span><span class="sxs-lookup"><span data-stu-id="db753-147">FALSE - 0</span></span>

<span data-ttu-id="db753-148">當您嘗試在 Windows Mixed Reality 中啟動 Win32 應用程式，而不是預先配置時，虛擬監視器現在會進行配置。</span><span class="sxs-lookup"><span data-stu-id="db753-148">Virtual monitors will now allocate when you attempt to launch a Win32 application in Windows Mixed Reality instead of pre-allocating.</span></span> <span data-ttu-id="db753-149">若要重設此元件，並重新啟用虛擬監視器預先配置，請將 DWORD 值傳回1。</span><span class="sxs-lookup"><span data-stu-id="db753-149">To reset this and re-enable virtual monitor pre-allocation, return the DWORD value to 1.</span></span>

### <a name="additional-known-issues"></a><span data-ttu-id="db753-150">其他已知問題</span><span class="sxs-lookup"><span data-stu-id="db753-150">Additional known issues</span></span>

-   <span data-ttu-id="db753-151">在混合現實入口網站關閉的情況下，在 Windows Mixed Reality 中開啟的網站將會遺失，但 Microsoft Edge Windows 仍會保留在混合現實首頁中的位置。</span><span class="sxs-lookup"><span data-stu-id="db753-151">Websites open in Windows Mixed Reality will be lost when Mixed Reality Portal closes, though the Microsoft Edge windows will remain where they were placed in the mixed reality home.</span></span>
- <span data-ttu-id="db753-152">包含360檢視器擴充功能的 WebXR 體驗，可能無法在具有混合式 GPU 設定的電腦上正確啟動。</span><span class="sxs-lookup"><span data-stu-id="db753-152">WebXR experiences, including the 360 Viewer extension, may not launch correctly on PCs with a Hybrid GPU setup.</span></span> <span data-ttu-id="db753-153">您可以藉由選取專用 GPU 作為圖形卡軟體中的預設 GPU，來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="db753-153">You may be able to work around this issue by selecting your dedicated GPU as the default GPU in your graphics card software.</span></span>
-   <span data-ttu-id="db753-154">未 hrtf 來自 Microsoft Edge windows 的音訊。</span><span class="sxs-lookup"><span data-stu-id="db753-154">Audio from Microsoft Edge windows is not spatialized.</span></span>
-   <span data-ttu-id="db753-155">**修正360檢視器延伸模組版本 2.3.8**：在 Windows Mixed Reality 中從 YouTube 開啟360影片可能會導致影片在耳機中失真。</span><span class="sxs-lookup"><span data-stu-id="db753-155">**Fixed in 360 Viewer extension version 2.3.8**: Opening a 360 video from YouTube in Windows Mixed Reality may result in the video being distorted in the headset.</span></span> <span data-ttu-id="db753-156">重新開機邊緣應以不可見的程式更新360檢視器延伸模組，以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="db753-156">Restarting Edge should invisibly update the 360 Viewer extension to resolve this issue.</span></span> <span data-ttu-id="db753-157">您可以 `edge://system/` 在網址列中輸入，然後選取 [擴充功能] 旁的**展開**按鈕，以確認您擁有的延伸模組版本。</span><span class="sxs-lookup"><span data-stu-id="db753-157">You can confirm which version of the extension you have by entering `edge://system/` in the address bar and selecting the **Expand** button next to "extensions."</span></span>




