---
title: Managed 偵錯與 Unity IL2CPP
description: 這篇文章說明如何對 Unity IL2CPP UWP 專案中執行 managed 偵錯工具。
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: unity，visual studio 中，偵錯，il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148853"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="eea10-104">Managed 偵錯與 Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="eea10-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="eea10-105">請遵循下列步驟來將受管理的偵錯工具附加至 Unity IL2CPP UWP 組建。</span><span class="sxs-lookup"><span data-stu-id="eea10-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="eea10-106">原本是本指南所開發的 HoloLens 和 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="eea10-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="eea10-107">請確認**InternetClientServer**並**PrivateNetworkClientServer**簽入 Unity 在 UWP 的發行設定功能。</span><span class="sxs-lookup"><span data-stu-id="eea10-107">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![UWP 發佈設定功能](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="eea10-109">設定 Unity UWP 建置設定：</span><span class="sxs-lookup"><span data-stu-id="eea10-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="eea10-110">開發組建</span><span class="sxs-lookup"><span data-stu-id="eea10-110">Development Build</span></span>
    - <span data-ttu-id="eea10-111">指令碼偵錯</span><span class="sxs-lookup"><span data-stu-id="eea10-111">Script Debugging</span></span>
    - <span data-ttu-id="eea10-112">等候 （選擇性） Managed 偵錯工具</span><span class="sxs-lookup"><span data-stu-id="eea10-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP 建置設定](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="eea10-114">在 Unity 中建置。</span><span class="sxs-lookup"><span data-stu-id="eea10-114">Build in Unity.</span></span>
1. <span data-ttu-id="eea10-115">建置並從 Visual Studio 方案部署到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="eea10-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="eea10-116">您應該使用建置**偵錯**或是**發行**組態。</span><span class="sxs-lookup"><span data-stu-id="eea10-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="eea10-117">**主要**組態停用 Unity 分析工具，並可防止最佳的偵錯。</span><span class="sxs-lookup"><span data-stu-id="eea10-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="eea10-118">（選擇性） 請確認**網際網路 （用戶端和伺服器）** 並**私人網路 （用戶端和伺服器）** 方案中的 在 Package.appxmanifest 中的功能清單中。</span><span class="sxs-lookup"><span data-stu-id="eea10-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="eea10-119">在您的裝置上啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="eea10-119">Start the app on your device.</span></span> <span data-ttu-id="eea10-120">請確定您的裝置連線到您的電腦相同的網路。</span><span class="sxs-lookup"><span data-stu-id="eea10-120">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="eea10-121">請確定裝置**不是**連線到您的電腦透過 USB。</span><span class="sxs-lookup"><span data-stu-id="eea10-121">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="eea10-122">移至 Visual Studio 方案，當您按兩下在 Unity 中，您可以在其中檢視和編輯指令碼會建立您C#指令碼。</span><span class="sxs-lookup"><span data-stu-id="eea10-122">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="eea10-123">偵錯]-> [附加 Unity 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="eea10-123">Debug -> Attach Unity Debugger.</span></span>

    ![附加 Unity 偵錯工具](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="eea10-125">在清單中選取您的裝置，然後按一下 [確定] 以附加。</span><span class="sxs-lookup"><span data-stu-id="eea10-125">Select your device in the list and click "OK" to attach.</span></span>

    ![裝置清單](images/il2cpp-debugging-machines.png)
