---
title: 正在更新 HoloLens
description: 如何更新 HoloLens 並加入預覽版組建的 Windows 測試人員程式。
author: mattzmsft
ms.author: mazeller
ms.date: 10/23/2018
ms.topic: article
keywords: 操作說明, insider, 預覽, 更新, 功能, 新版本
ms.openlocfilehash: 39df7f204af2edcfc83f6be245509e5d12c3bbc0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548718"
---
# <a name="updating-hololens"></a><span data-ttu-id="00c03-104">正在更新 HoloLens</span><span class="sxs-lookup"><span data-stu-id="00c03-104">Updating HoloLens</span></span>

<span data-ttu-id="00c03-105">您的 HoloLens 會在插入並聯機至 Wi-fi 時, 自動下載並安裝系統更新, 即使它處於待命狀態也一樣。</span><span class="sxs-lookup"><span data-stu-id="00c03-105">Your HoloLens will automatically download and install system updates whenever it is plugged-in and connected to Wi-Fi, even when it is in standby.</span></span> <span data-ttu-id="00c03-106">不過, 如果有的話, 您也可以手動觸發系統更新。</span><span class="sxs-lookup"><span data-stu-id="00c03-106">However, you can also trigger a system update manually if there is one available.</span></span>

## <a name="manual-update"></a><span data-ttu-id="00c03-107">手動更新</span><span class="sxs-lookup"><span data-stu-id="00c03-107">Manual update</span></span>

<span data-ttu-id="00c03-108">若要執行手動更新:</span><span class="sxs-lookup"><span data-stu-id="00c03-108">To perform a manual update:</span></span>
* <span data-ttu-id="00c03-109">開啟 [**設定**] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="00c03-109">Open the **Settings** app.</span></span>
* <span data-ttu-id="00c03-110">流覽至**Update & 安全性** >  **Windows Update**。</span><span class="sxs-lookup"><span data-stu-id="00c03-110">Navigate to **Update & Security** > **Windows Update**.</span></span>
* <span data-ttu-id="00c03-111">選取 [**檢查更新**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="00c03-111">Select the **Check for updates** button.</span></span>

<span data-ttu-id="00c03-112">如果有可用的更新, 它會開始下載新的版本。</span><span class="sxs-lookup"><span data-stu-id="00c03-112">If an update is available, it will start downloading the new version.</span></span> <span data-ttu-id="00c03-113">下載完成後, 請選取 [**立即重新開機**] 按鈕以觸發安裝。</span><span class="sxs-lookup"><span data-stu-id="00c03-113">Once the download is complete, select the **Restart Now** button to trigger the installation.</span></span> <span data-ttu-id="00c03-114">如果您的裝置低於 40% 且未插入, 重新開機將不會開始安裝更新。</span><span class="sxs-lookup"><span data-stu-id="00c03-114">If your device is below 40% and not plugged in, restarting will not start installing the update.</span></span>

<span data-ttu-id="00c03-115">當您的 HoloLens 安裝更新時, 它會顯示旋轉的齒輪和進度指示器。</span><span class="sxs-lookup"><span data-stu-id="00c03-115">While your HoloLens is installing the update, it will display spinning gears and a progress indicator.</span></span> <span data-ttu-id="00c03-116">請勿在這段期間關閉 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="00c03-116">Do not turn off your HoloLens during this time.</span></span> <span data-ttu-id="00c03-117">它會在完成安裝後自動重新開機。</span><span class="sxs-lookup"><span data-stu-id="00c03-117">It will reboot automatically once it has completed the installation.</span></span>

<span data-ttu-id="00c03-118">您可以開啟 [**設定**] 應用程式, 然後依序選取 [**系統**] 和 [**關於**], 來驗證系統版本號碼。</span><span class="sxs-lookup"><span data-stu-id="00c03-118">You can verify the system version number by opening the **Settings** app and selecting **System** and then **About**.</span></span> <span data-ttu-id="00c03-119">HoloLens 目前僅支援一次套用一個更新, 因此如果您的 HoloLens 超過最新版本, 您可能需要多次執行更新程式, 才能讓它完全保持在最新狀態。</span><span class="sxs-lookup"><span data-stu-id="00c03-119">HoloLens currently supports applying only one update at a time, so if your HoloLens is more than one version behind the latest you may need to run through the update process multiple times to get it fully up to date.</span></span>

## <a name="windows-insider-program-on-hololens"></a><span data-ttu-id="00c03-120">HoloLens 上的 Windows 測試人員程式</span><span class="sxs-lookup"><span data-stu-id="00c03-120">Windows Insider Program on HoloLens</span></span>

<span data-ttu-id="00c03-121">藉由從 HoloLens 加入 Windows 測試人員程式, 您將可在正式運作之前, 取得 HoloLens 軟體更新的預覽組建。</span><span class="sxs-lookup"><span data-stu-id="00c03-121">By joining the Windows Insider Program from your HoloLens, you'll get access to preview builds of HoloLens software updates before they're available to the general public.</span></span>

<span data-ttu-id="00c03-122">如需如何在 HoloLens 上參與 Windows 測試人員計畫的相關資訊, 請參閱我們的 IT 專業人員檔中的[Microsoft HoloLens Insider preview](https://docs.microsoft.com/hololens/hololens-insider)文章。</span><span class="sxs-lookup"><span data-stu-id="00c03-122">For information on how to participate in the Windows Insider Program on HoloLens, please refer to the [Insider preview for Microsoft HoloLens](https://docs.microsoft.com/hololens/hololens-insider) article in our IT Pro docs.</span></span>
