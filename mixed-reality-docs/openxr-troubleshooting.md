---
title: 對 OpenXR 進行疑難排解
description: 針對 OpenXR 應用程式中的問題進行疑難排解。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體、疑難排解
ms.openlocfilehash: 269982596ed6162d9c2f1ec999a446bcecd6ba2a
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228003"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="04f40-104">對 OpenXR 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="04f40-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="04f40-105">以下是使用 Windows Mixed Reality OpenXR 執行時間開發 OpenXR 應用程式時的一些疑難排解秘訣。</span><span class="sxs-lookup"><span data-stu-id="04f40-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="04f40-106">如果您有任何關於<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>的其他問題，請造訪<a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 論壇</a>或<a href="https://khr.io/slack" target="_blank">#openxr 頻道的時差</a>。</span><span class="sxs-lookup"><span data-stu-id="04f40-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="04f40-107">在目前的 Windows Mixed Reality OpenXR 執行時間中，有 x86 應用程式的已知問題。</span><span class="sxs-lookup"><span data-stu-id="04f40-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="04f40-108">您目前應該建立適用于 x64 的桌面 OpenXR 應用程式。</span><span class="sxs-lookup"><span data-stu-id="04f40-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="04f40-109">OpenXR 應用程式未啟動 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="04f40-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="04f40-110">如果您的 OpenXR 應用程式在執行時未啟動 Windows Mixed Reality，則 Windows Mixed Reality OpenXR 執行時間可能不會設定為作用中的執行時間。</span><span class="sxs-lookup"><span data-stu-id="04f40-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="04f40-111">請務必遵循上述指示，以[開始使用適用于 Windows Mixed Reality 耳機的 OpenXR](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) ，讓執行時間變成作用中。</span><span class="sxs-lookup"><span data-stu-id="04f40-111">Be sure to follow the instructions above for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="04f40-112">您也可以執行[Windows Mixed Reality OpenXR 開發人員工具](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)，以取得有關系統上的 Windows Mixed Reality OpenXR 執行時間狀態的其他疑難排解協助。</span><span class="sxs-lookup"><span data-stu-id="04f40-112">You can also run the [Windows Mixed Reality OpenXR Developer Tools](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a><span data-ttu-id="04f40-113">混合現實入口網站未顯示 [設定 OpenXR] 功能表項目</span><span class="sxs-lookup"><span data-stu-id="04f40-113">Mixed Reality Portal not showing "Set up OpenXR" menu item</span></span>

<span data-ttu-id="04f40-114">請確定您至少執行 Windows 10 2018 年10月更新（1809）。</span><span class="sxs-lookup"><span data-stu-id="04f40-114">Be sure you are running at least the Windows 10 October 2018 Update (1809).</span></span>  <span data-ttu-id="04f40-115">如果您是在舊版的 Windows 10 上，您可以使用[Windows 10 更新](https://www.microsoft.com//software-download/windows10)小幫手升級至5月2019更新（1903）。</span><span class="sxs-lookup"><span data-stu-id="04f40-115">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update (1903) using the [Windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10).</span></span>

<span data-ttu-id="04f40-116">如果您有較舊版本的混合現實入口網站應用程式，則可能無法使用 [設定 OpenXR] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="04f40-116">The "Set up OpenXR" menu item may not be available if you have an older version of the Mixed Reality Portal app.</span></span>  <span data-ttu-id="04f40-117">檢查是否有[混合現實入口網站應用程式更新](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)，以確保您擁有最新版本。</span><span class="sxs-lookup"><span data-stu-id="04f40-117">Check for a [Mixed Reality Portal app update](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) to ensure you have the latest version.</span></span>

<span data-ttu-id="04f40-118">請注意，如果 Windows Mixed Reality OpenXR 執行時間已安裝且作用中，就不會顯示 [設定 OpenXR] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="04f40-118">Note that the "Set up OpenXR" menu item will not show up if the Windows Mixed Reality OpenXR Runtime is already installed and active.</span></span>  <span data-ttu-id="04f40-119">您可以安裝[Windows Mixed Reality OpenXR 開發人員工具](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)，以判斷系統上 OpenXR 執行時間的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="04f40-119">You can install the [Windows Mixed Reality OpenXR Developer Tools](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) to determine the current status of the OpenXR runtime on your system.</span></span>