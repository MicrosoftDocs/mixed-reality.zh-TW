---
title: 使用 Unity IL2CPP 的 Managed 調試
description: 本文涵蓋如何在 Unity IL2CPP UWP 專案上執行 managed 偵錯工具。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity，visual studio，調試，il2cpp
ms.openlocfilehash: 970d3000df995e7c6e331a41d10e25dc5aa370a8
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502659"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="ef1ef-104">使用 Unity IL2CPP 的 Managed 調試</span><span class="sxs-lookup"><span data-stu-id="ef1ef-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="ef1ef-105">請遵循下列步驟，將 managed 偵錯工具附加至您的 Unity IL2CPP UWP 組建。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="ef1ef-106">本指南最初是針對 HoloLens 和 HoloLens 2 而開發。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="ef1ef-107">您必須位於支援[多播](https://en.wikipedia.org/wiki/Multicast)的網路上。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="ef1ef-108">請確定**InternetClientServer**和**PrivateNetworkClientServer**在 UWP 發行設定功能下已簽入 Unity。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![UWP 發行設定功能](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="ef1ef-110">設定 Unity UWP 組建設定：</span><span class="sxs-lookup"><span data-stu-id="ef1ef-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="ef1ef-111">開發組建</span><span class="sxs-lookup"><span data-stu-id="ef1ef-111">Development Build</span></span>
    - <span data-ttu-id="ef1ef-112">指令碼偵錯</span><span class="sxs-lookup"><span data-stu-id="ef1ef-112">Script Debugging</span></span>
    - <span data-ttu-id="ef1ef-113">等候受管理的偵錯工具（選擇性）</span><span class="sxs-lookup"><span data-stu-id="ef1ef-113">Wait for Managed Debugger (optional)</span></span>

    ![UWP 組建設定](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="ef1ef-115">Unity 中的組建。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-115">Build in Unity.</span></span>
1. <span data-ttu-id="ef1ef-116">建立 Visual Studio 解決方案，並將其部署到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="ef1ef-117">您應該使用**Debug**或**Release**設定來建立。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="ef1ef-118">**主要**設定會停用 Unity profiler，並防止優化的調試。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="ef1ef-119">（選擇性）在解決方案的 package.appxmanifest.xml 中，確認 [功能] 清單中的 [**網際網路（用戶端 & 伺服器）** ] 和 [**私人網路（用戶端 & 伺服器）** ]。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="ef1ef-120">在您的裝置上啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-120">Start the app on your device.</span></span> <span data-ttu-id="ef1ef-121">請確定您的裝置已連線到與您電腦相同的網路。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="ef1ef-122">請確定裝置**未**透過 USB 連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="ef1ef-123">當您按兩下 Unity 中的腳本時所建立的 Visual Studio 方案，您可以在其中查看及編輯C#腳本。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-123">Go to the Visual Studio solution that's created when you double-click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="ef1ef-124">Debug-> 附加 Unity 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-124">Debug -> Attach Unity Debugger.</span></span>

    ![附加 Unity 偵錯工具](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="ef1ef-126">在清單中選取您的裝置，然後按一下 [確定] 以連接。</span><span class="sxs-lookup"><span data-stu-id="ef1ef-126">Select your device in the list and click "OK" to attach.</span></span>

    ![裝置清單](images/il2cpp-debugging-machines.png)
