---
title: Windows Mixed Reality 和新的 Microsoft Edge
description: 準備開始進行 Windows Mixed Reality 中新的 Microsoft Edge。 包含預期的變更、要查看的更新，以及已知問題。
author: mattzmsft
ms.author: mazeller
ms.date: 01/15/2020
ms.topic: article
keywords: edge、new、沉浸式 web、microsoft edge、browser、vr
ms.openlocfilehash: d61780045e795850012536a36fde67b9934c76aa
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216229"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a><span data-ttu-id="13d78-105">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="13d78-105">Windows Mixed Reality and the new Microsoft Edge</span></span>

<span data-ttu-id="13d78-106">[新的 Microsoft Edge 現在已可供下載](https://blogs.windows.com/windowsexperience/?p=173496)，但客戶也可以在未來數個月內以測量的推出方法，[等待它安裝到 Windows 10 的後續更新中](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)。</span><span class="sxs-lookup"><span data-stu-id="13d78-106">The [new Microsoft Edge is now available for download](https://blogs.windows.com/windowsexperience/?p=173496), but customers can also [wait for it to be installed in a future update to Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), following a measured roll-out approach over the next several months.</span></span> 

<span data-ttu-id="13d78-107">透過這段新聞，**我們想要讓 Windows Mixed REALITY VR 耳機客戶知道新的 Microsoft Edge 有哪些內容，並通知您一些可改善 Windows Mixed Reality web 流覽體驗的擱置更新**。</span><span class="sxs-lookup"><span data-stu-id="13d78-107">With this news, **we wanted to let Windows Mixed Reality VR headset customers know what to expect from the new Microsoft Edge and inform you of some pending updates that will improve your web browsing experience in Windows Mixed Reality**.</span></span>

## <a name="introducing-the-new-microsoft-edge"></a><span data-ttu-id="13d78-108">新的 Microsoft Edge 簡介</span><span class="sxs-lookup"><span data-stu-id="13d78-108">Introducing the new Microsoft Edge</span></span>

<span data-ttu-id="13d78-109">新的 Microsoft Edge 採用桌上型電腦上[的 Chromium 開放原始碼專案](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)，為客戶建立更佳的 web 相容性，並減少所有 網頁程式開發人員的 web 片段。</span><span class="sxs-lookup"><span data-stu-id="13d78-109">The new Microsoft Edge [adopts the Chromium open source project](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) on the desktop to create better web compatibility for customers and less fragmentation of the web for all web developers.</span></span> <span data-ttu-id="13d78-110">它也會在啟動時支援 WebXR，這是建立 VR 耳機的沉浸式 web 體驗的新標準，用來取代 WebVR。</span><span class="sxs-lookup"><span data-stu-id="13d78-110">It will also support WebXR at launch, the new standard for creating immersive web experiences for VR headsets, in place of WebVR.</span></span>

>[!IMPORTANT]
><span data-ttu-id="13d78-111">當您在最新的 Windows 10 裝置上安裝 Microsoft Edge 時，將會取代您電腦上先前的（舊版）版本。</span><span class="sxs-lookup"><span data-stu-id="13d78-111">When you install Microsoft Edge on an up-to-date Windows 10 device, it will replace the previous (legacy) version on your PC.</span></span>

## <a name="getting-ready-for-the-new-microsoft-edge"></a><span data-ttu-id="13d78-112">準備開始新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="13d78-112">Getting ready for the new Microsoft Edge</span></span>

<span data-ttu-id="13d78-113">Windows Mixed Reality VR 耳機客戶若想要在混合現實首頁中使用新的 Microsoft Edge，應**升級至 Windows 10 1903 版或更新版本，以在混合現實首頁中提供 Win32 應用程式的原生支援（例如新的 Microsoft Edge）** 。</span><span class="sxs-lookup"><span data-stu-id="13d78-113">Windows Mixed Reality VR headset customers who want to use the new Microsoft Edge in the mixed reality home should **upgrade to Windows 10 Version 1903 or later for native support of Win32 applications (like the new Microsoft Edge)** in the mixed reality home.</span></span> <span data-ttu-id="13d78-114">檢查 Windows Update 或[手動安裝最新版的 Windows 10](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="13d78-114">Check Windows Update or [manually install the latest version of Windows 10](https://www.microsoft.com/en-us/software-download/windows10).</span></span>

<span data-ttu-id="13d78-115">針對混合現實首頁中最佳可能的 Microsoft Edge 體驗，我們也建議您等待**windows 10 第 1 1903 版（或更新版本）的2020-01 累積更新抵達新 Microsoft edge 的一些重要 Windows Mixed reality 優化**，這應該會在一月月底的 Windows Update 中提供。</span><span class="sxs-lookup"><span data-stu-id="13d78-115">For the best possible Microsoft Edge experience in the mixed reality home, we also recommend waiting for **some key Windows Mixed Reality optimizations for the new Microsoft Edge arriving with the 2020-01 Cumulative update for Windows 10 Version 1903 (or later)**, which should be available in Windows Update by the end of January.</span></span>

>[!IMPORTANT]
><span data-ttu-id="13d78-116">如果您選擇在進行這些更新之前下載新的 Microsoft Edge，在 Windows Mixed Reality 中會有一些已知的問題（您可以在下方閱讀）。</span><span class="sxs-lookup"><span data-stu-id="13d78-116">If you opt to download the new Microsoft Edge before taking these updates, there will be some known issues with its behavior in Windows Mixed Reality (which you can read about below).</span></span>

## <a name="known-issues"></a><span data-ttu-id="13d78-117">已知問題</span><span class="sxs-lookup"><span data-stu-id="13d78-117">Known issues</span></span>

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a><span data-ttu-id="13d78-118">Windows 10 1903 版（或更新版本）的2020-01 累積更新所解決的已知問題</span><span class="sxs-lookup"><span data-stu-id="13d78-118">Known issues resolved by the 2020-01 Cumulative update for Windows 10 Version 1903 (or later)</span></span>

- <span data-ttu-id="13d78-119">啟動任何 Win32 應用程式（包括新的 Microsoft Edge）都會讓頭戴式裝置顯示短暫凍結。</span><span class="sxs-lookup"><span data-stu-id="13d78-119">Launching any Win32 app, including the new Microsoft Edge, causes the headset display to briefly freeze.</span></span>
- <span data-ttu-id="13d78-120">Microsoft Edge 磚會從 Windows Mixed Reality 的 [開始] 功能表中消失（您可以在 [傳統應用程式] 資料夾中找到它）。</span><span class="sxs-lookup"><span data-stu-id="13d78-120">The Microsoft Edge tile disappears from the Windows Mixed Reality Start menu (you can find it in the “Classic apps” folder).</span></span>
- <span data-ttu-id="13d78-121">來自先前 Microsoft Edge 的 Windows 仍然會放在混合現實首頁，但無法使用。</span><span class="sxs-lookup"><span data-stu-id="13d78-121">Windows from the previous Microsoft Edge are still placed around the mixed reality home, but cannot be used.</span></span> <span data-ttu-id="13d78-122">嘗試啟用這些 windows 會啟動桌面應用程式內的邊緣。</span><span class="sxs-lookup"><span data-stu-id="13d78-122">Attempting to activate those windows launches Edge inside of the Desktop app.</span></span>
- <span data-ttu-id="13d78-123">選取混合現實首頁中的超連結，就會在桌面上啟動網頁瀏覽器，而不是使用混合現實首頁。</span><span class="sxs-lookup"><span data-stu-id="13d78-123">Selecting a hyperlink in the mixed reality home launches a web browser on the desktop instead of the mixed reality home.</span></span>
- <span data-ttu-id="13d78-124">雖然 WebVR 不受支援，但 WebVR 展示應用程式存在於混合現實首頁中。</span><span class="sxs-lookup"><span data-stu-id="13d78-124">The WebVR Showcase app is present in the mixed reality home, despite WebVR no longer being supported.</span></span>
- <span data-ttu-id="13d78-125">鍵盤啟動和視覺效果的一般改良功能。</span><span class="sxs-lookup"><span data-stu-id="13d78-125">General improvements to keyboard launch and visuals.</span></span>

### <a name="additional-known-issues"></a><span data-ttu-id="13d78-126">其他已知問題</span><span class="sxs-lookup"><span data-stu-id="13d78-126">Additional known issues</span></span>

-   <span data-ttu-id="13d78-127">在混合現實入口網站關閉的情況下，在 Windows Mixed Reality 中開啟的網站將會遺失，但 Microsoft Edge Windows 仍會保留在混合現實首頁中的位置。</span><span class="sxs-lookup"><span data-stu-id="13d78-127">Websites open in Windows Mixed Reality will be lost when Mixed Reality Portal closes, though the Microsoft Edge windows will remain where they were placed in the mixed reality home.</span></span>
- <span data-ttu-id="13d78-128">包含360檢視器擴充功能的 WebXR 體驗，可能無法在具有混合式 GPU 設定的電腦上正確啟動。</span><span class="sxs-lookup"><span data-stu-id="13d78-128">WebXR experiences, including the 360 Viewer extension, may not launch correctly on PCs with a Hybrid GPU setup.</span></span> <span data-ttu-id="13d78-129">您可以藉由選取專用 GPU 作為圖形卡軟體中的預設 GPU，來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="13d78-129">You may be able to work around this issue by selecting your dedicated GPU as the default GPU in your graphics card software.</span></span>
-   <span data-ttu-id="13d78-130">未 hrtf 來自 Microsoft Edge windows 的音訊。</span><span class="sxs-lookup"><span data-stu-id="13d78-130">Audio from Microsoft Edge windows is not spatialized.</span></span>
-   <span data-ttu-id="13d78-131">**修正360檢視器延伸模組版本 2.3.8**：在 Windows Mixed Reality 中從 YouTube 開啟360影片可能會導致影片在耳機中失真。</span><span class="sxs-lookup"><span data-stu-id="13d78-131">**Fixed in 360 Viewer extension version 2.3.8**: Opening a 360 video from YouTube in Windows Mixed Reality may result in the video being distorted in the headset.</span></span> <span data-ttu-id="13d78-132">重新開機邊緣應以不可見的程式更新360檢視器延伸模組，以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="13d78-132">Restarting Edge should invisibly update the 360 Viewer extension to resolve this issue.</span></span> <span data-ttu-id="13d78-133">您可以 `edge://system/` 在網址列中輸入，然後選取 [擴充功能] 旁的**展開**按鈕，以確認您擁有的延伸模組版本。</span><span class="sxs-lookup"><span data-stu-id="13d78-133">You can confirm which version of the extension you have by entering `edge://system/` in the address bar and selecting the **Expand** button next to "extensions."</span></span>
-   <span data-ttu-id="13d78-134">在 Windows Mixed Reality 會話期間，虛擬監視器會在 [設定] 中顯示為一般實體監視器 > 系統 > 顯示。</span><span class="sxs-lookup"><span data-stu-id="13d78-134">During Windows Mixed Reality sessions, virtual monitors will appear as generic physical monitors in Settings > System > Display.</span></span>



