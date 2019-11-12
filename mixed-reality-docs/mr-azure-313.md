---
title: MR 和 Azure 313-IoT 中樞服務
description: 完成此課程以瞭解如何在執行 Ubuntu 16.4 的虛擬機器上實施 Azure IoT 中樞服務，然後使用 Microsoft HoloLens 或沉浸式（VR）耳機將訊息資料視覺化。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure，混合現實，學術，邊緣，iot edge，教學課程，api，通知，函數，資料表，hololens，沉浸，vr，iot，虛擬機器，ubuntu，python
ms.openlocfilehash: bfb1518869892ed4899019d7b9c504a960e7db3f
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926839"
---
>[!NOTE]
><span data-ttu-id="96383-104">混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="96383-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="96383-105">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="96383-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="96383-106">這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="96383-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="96383-107">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="96383-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="96383-108">未來將會有一系列新的教學課程，將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="96383-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="96383-109">此通知會在張貼時，使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="96383-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="96383-110">MR 和 Azure 313： IoT 中樞服務</span><span class="sxs-lookup"><span data-stu-id="96383-110">MR and Azure 313: IoT Hub Service</span></span>

![課程結果](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="96383-112">在此課程中，您將瞭解如何在執行 Ubuntu 16.4 作業系統的虛擬機器上執行**Azure IoT 中樞服務**。</span><span class="sxs-lookup"><span data-stu-id="96383-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="96383-113">接著，會使用**azure 函數應用程式**從您的 Ubuntu VM 接收訊息，並將結果儲存在**Azure 表格服務**中。</span><span class="sxs-lookup"><span data-stu-id="96383-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="96383-114">然後您就可以使用 Microsoft HoloLens 或沉浸式（VR）頭戴式裝置上的**Power BI**來查看此資料。</span><span class="sxs-lookup"><span data-stu-id="96383-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="96383-115">本課程的內容*適用*于 IoT Edge 裝置，不過基於本課程的目的，焦點會在虛擬機器環境中，因此不需要存取實體邊緣裝置。</span><span class="sxs-lookup"><span data-stu-id="96383-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="96383-116">完成此課程之後，您將瞭解如何：</span><span class="sxs-lookup"><span data-stu-id="96383-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="96383-117">將**IoT Edge 模組**部署至虛擬機器（UBUNTU 16 OS），這會代表您的 IoT 裝置。</span><span class="sxs-lookup"><span data-stu-id="96383-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="96383-118">將**Azure 自訂視覺 Tensorflow 模型**新增至 Edge 模組，並使用程式碼來分析儲存在容器中的影像。</span><span class="sxs-lookup"><span data-stu-id="96383-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="96383-119">設定模組，以將分析結果訊息傳回給您的**IoT 中樞服務**。</span><span class="sxs-lookup"><span data-stu-id="96383-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="96383-120">使用**azure 函數應用程式**將訊息儲存在**azure 資料表**中。</span><span class="sxs-lookup"><span data-stu-id="96383-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="96383-121">設定**Power BI**來收集儲存的訊息並建立報表。</span><span class="sxs-lookup"><span data-stu-id="96383-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="96383-122">將**Power BI**中的 IoT 訊息資料視覺化。</span><span class="sxs-lookup"><span data-stu-id="96383-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="96383-123">您將使用的服務包括：</span><span class="sxs-lookup"><span data-stu-id="96383-123">The Services you will use include:</span></span>

- <span data-ttu-id="96383-124">**Azure IoT 中樞**是一種 Microsoft Azure 服務，可讓開發人員連接、監視和管理 IoT 資產。</span><span class="sxs-lookup"><span data-stu-id="96383-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="96383-125">如需詳細資訊，請造訪[ **Azure IoT 中樞服務**頁面](https://azure.microsoft.com/services/iot-hub/)。</span><span class="sxs-lookup"><span data-stu-id="96383-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/services/iot-hub/).</span></span>

- <span data-ttu-id="96383-126">**Azure Container Registry**是一項 Microsoft Azure 服務，可讓開發人員針對各種類型的容器儲存容器映射。</span><span class="sxs-lookup"><span data-stu-id="96383-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="96383-127">如需詳細資訊，請造訪[ **Azure Container Registry 服務**頁面](https://azure.microsoft.com/services/container-registry/)。</span><span class="sxs-lookup"><span data-stu-id="96383-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/services/container-registry/).</span></span>

- <span data-ttu-id="96383-128">**Azure 函數應用程式**是一項 Microsoft Azure 服務，可讓開發人員在 Azure 中執行一小段程式碼，即「函式」。</span><span class="sxs-lookup"><span data-stu-id="96383-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="96383-129">這可讓您將工作委派給雲端，而不是您的本機應用程式，這可能有許多好處。</span><span class="sxs-lookup"><span data-stu-id="96383-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="96383-130">**Azure Functions**支援數種開發語言，包括 C\#、F\#、Node.js、JAVA 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="96383-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="96383-131">如需詳細資訊，請造訪[ **Azure Functions**頁面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="96383-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="96383-132">**Azure 儲存體：資料表**是一種 Microsoft Azure 的服務，可讓開發人員在雲端儲存結構化的非 SQL 資料，讓您可以輕鬆地在任何地方存取。</span><span class="sxs-lookup"><span data-stu-id="96383-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="96383-133">此服務具有無架構的設計，可讓您視需要進行資料表的演進，因此非常有彈性。</span><span class="sxs-lookup"><span data-stu-id="96383-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="96383-134">如需詳細資訊，請造訪[ **Azure 資料表**頁面](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="96383-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="96383-135">本課程將告訴您如何設定及使用 IoT 中樞服務，然後將裝置所提供的回應視覺化。</span><span class="sxs-lookup"><span data-stu-id="96383-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="96383-136">您可以將這些概念套用到您可能會建立的自訂 IoT 中樞服務安裝程式。</span><span class="sxs-lookup"><span data-stu-id="96383-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="96383-137">裝置支援</span><span class="sxs-lookup"><span data-stu-id="96383-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="96383-138">粗</span><span class="sxs-lookup"><span data-stu-id="96383-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="96383-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="96383-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="96383-140"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="96383-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="96383-141">MR 和 Azure 313： IoT 中樞服務</span><span class="sxs-lookup"><span data-stu-id="96383-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="96383-142">✔️</span><span class="sxs-lookup"><span data-stu-id="96383-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="96383-143">✔️</span><span class="sxs-lookup"><span data-stu-id="96383-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="96383-144">必要條件</span><span class="sxs-lookup"><span data-stu-id="96383-144">Prerequisites</span></span>

<span data-ttu-id="96383-145">如需使用混合現實進行開發的最新必要條件，包括 Microsoft HoloLens，請造訪[安裝工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)一文。</span><span class="sxs-lookup"><span data-stu-id="96383-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="96383-146">本教學課程是專為具有 Python 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="96383-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="96383-147">也請注意，本檔中的必要條件和書面指示，代表在撰寫本文時已測試和驗證的內容（2018年7月）。</span><span class="sxs-lookup"><span data-stu-id="96383-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="96383-148">您可以免費使用 [[安裝工具](install-the-tools.md)] 文章中所列的最新軟體，但不應假設本課程中的資訊完全符合您在較新軟體中找到的內容，而不是如下所示。</span><span class="sxs-lookup"><span data-stu-id="96383-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="96383-149">需要下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="96383-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="96383-150">Windows 10 秋季建立者更新（或更新版本），**已啟用開發人員模式**</span><span class="sxs-lookup"><span data-stu-id="96383-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="96383-151">您無法在 Windows 10 Home Edition 上使用 Hyper-v 來執行虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="96383-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="96383-152">Windows 10 SDK （最新版本）</span><span class="sxs-lookup"><span data-stu-id="96383-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="96383-153">**已啟用 HoloLens、開發人員模式**</span><span class="sxs-lookup"><span data-stu-id="96383-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="96383-154">Visual Studio 2017.15.4 （僅用於存取 Azure Cloud Explorer）</span><span class="sxs-lookup"><span data-stu-id="96383-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="96383-155">適用于 Azure 的網際網路存取，以及適用于 IoT 中樞服務的。</span><span class="sxs-lookup"><span data-stu-id="96383-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="96383-156">如需詳細資訊，請遵循此[連結以 IoT 中樞服務 頁面](https://azure.microsoft.com/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="96383-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/services/iot-hub/)</span></span>
- <span data-ttu-id="96383-157">機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="96383-157">A machine learning model.</span></span> <span data-ttu-id="96383-158">如果您還沒有準備好使用模型，[您可以使用本課程所提供的模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)。</span><span class="sxs-lookup"><span data-stu-id="96383-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="96383-159">已在您的 Windows 10 開發電腦上啟用**hyper-v**軟體。</span><span class="sxs-lookup"><span data-stu-id="96383-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="96383-160">執行 Ubuntu （16.4 或18.4）並在您的開發電腦上執行的虛擬機器，或者您也可以使用執行 Linux 的個別電腦（Ubuntu 16.4 或18.4）。</span><span class="sxs-lookup"><span data-stu-id="96383-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="96383-161">您可以在[「開始之前」章節](#before-you-start)中，找到如何使用 Hyper-v 在 Windows 上建立 VM 的詳細資訊。（ https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine) 。</span><span class="sxs-lookup"><span data-stu-id="96383-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="96383-162">開始之前</span><span class="sxs-lookup"><span data-stu-id="96383-162">Before you start</span></span>

1. <span data-ttu-id="96383-163">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="96383-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="96383-164">如果您需要支援設定 HoloLens，[請務必造訪 hololens 安裝程式一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="96383-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="96383-165">開始開發新的 HoloLens 應用程式時，最好先執行**校正**和**感應器微調**（有時候它有助於為每個使用者執行這些工作）。</span><span class="sxs-lookup"><span data-stu-id="96383-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="96383-166">如需校正的說明，請遵循此[HoloLens 校正文章的連結](calibration.md#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="96383-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="96383-167">如需感應器微調的說明，請遵循此[HoloLens 感應器微調文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="96383-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="96383-168">使用**hyper-v**設定您的**Ubuntu 虛擬機器**。</span><span class="sxs-lookup"><span data-stu-id="96383-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="96383-169">下列資源將協助您處理此程式。</span><span class="sxs-lookup"><span data-stu-id="96383-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="96383-170">首先，請遵循此連結以[下載 Ubuntu 16.04.4 LTS （Xenial Xerus） ISO](https://au.releases.ubuntu.com/16.04/)。</span><span class="sxs-lookup"><span data-stu-id="96383-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](https://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="96383-171">選取**64 位電腦（AMD64）桌面映射**。</span><span class="sxs-lookup"><span data-stu-id="96383-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="96383-172">請確定您的 Windows 10 電腦上已啟用**hyper-v** 。</span><span class="sxs-lookup"><span data-stu-id="96383-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="96383-173">您可以遵循此連結，取得在[Windows 10 上安裝和啟用 hyper-v](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)的指引。</span><span class="sxs-lookup"><span data-stu-id="96383-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="96383-174">啟動 Hyper-v，並建立新的 Ubuntu VM。</span><span class="sxs-lookup"><span data-stu-id="96383-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="96383-175">您可以遵循此連結，取得[如何使用 hyper-v 建立 VM 的逐步指南](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)。</span><span class="sxs-lookup"><span data-stu-id="96383-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="96383-176">當要求「**從可開機的映射檔案安裝作業系統**」時，請選取您稍早下載的**Ubuntu ISO** 。</span><span class="sxs-lookup"><span data-stu-id="96383-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="96383-177">不建議使用**Hyper-v 快速建立**。</span><span class="sxs-lookup"><span data-stu-id="96383-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="96383-178">第1章-取出自訂視覺模型</span><span class="sxs-lookup"><span data-stu-id="96383-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="96383-179">在此課程中，您將可以存取[預先建立的自訂視覺模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)，以偵測影像中的鍵盤和滑鼠。</span><span class="sxs-lookup"><span data-stu-id="96383-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="96383-180">如果您使用此，請繼續進行[第2章](#chapter-2---the-container-registry-service)。</span><span class="sxs-lookup"><span data-stu-id="96383-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="96383-181">不過，如果您想要使用自己的自訂視覺模型，可以執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="96383-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="96383-182">在您的**自訂視覺專案**中，移至 [**效能**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="96383-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="96383-183">您的模型必須使用*精簡*的網域，才能匯出模型。</span><span class="sxs-lookup"><span data-stu-id="96383-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="96383-184">您可以在專案的 [設定] 中變更 [模型] 網域。</span><span class="sxs-lookup"><span data-stu-id="96383-184">You can change your models domain in the settings for your project.</span></span>

    ![[效能] 索引標籤](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="96383-186">選取您要匯出的**反復**專案，然後按一下 [**匯出**]。</span><span class="sxs-lookup"><span data-stu-id="96383-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="96383-187">分頁隨即出現。</span><span class="sxs-lookup"><span data-stu-id="96383-187">A blade will appear.</span></span>

    ![匯出分頁](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="96383-189">在分頁中，按一下 [ **Docker**檔案]。</span><span class="sxs-lookup"><span data-stu-id="96383-189">In the blade click **Docker File**.</span></span>

    ![選取 docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="96383-191">按一下下拉式功能表中的 [ **Linux** ]，然後按一下 [**下載**]。</span><span class="sxs-lookup"><span data-stu-id="96383-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![按一下 [下載]](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="96383-193">將內容解壓縮。</span><span class="sxs-lookup"><span data-stu-id="96383-193">Unzip the content.</span></span> <span data-ttu-id="96383-194">稍後在本課程中將會用到。</span><span class="sxs-lookup"><span data-stu-id="96383-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="96383-195">第2章-Container Registry 服務</span><span class="sxs-lookup"><span data-stu-id="96383-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="96383-196">**Container Registry 服務**是用來裝載容器的存放庫。</span><span class="sxs-lookup"><span data-stu-id="96383-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="96383-197">您將在本課程中建立和使用的**IoT 中樞服務**，是指**容器登錄服務**，以取得要在 Edge 裝置中部署的容器。</span><span class="sxs-lookup"><span data-stu-id="96383-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="96383-198">首先，遵循此[連結前往 Azure 入口網站](https://portal.azure.com/)，然後使用您的認證登入。</span><span class="sxs-lookup"><span data-stu-id="96383-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="96383-199">移至 [**建立資源**]，然後尋找 [ **Container Registry**]。</span><span class="sxs-lookup"><span data-stu-id="96383-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![container registry](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="96383-201">按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="96383-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="96383-202">設定服務安裝程式參數：</span><span class="sxs-lookup"><span data-stu-id="96383-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="96383-203">插入專案的名稱，在此範例中稱為**IoTCRegistry**。</span><span class="sxs-lookup"><span data-stu-id="96383-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="96383-204">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="96383-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="96383-205">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的費用。</span><span class="sxs-lookup"><span data-stu-id="96383-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="96383-206">建議您將與單一專案相關聯的所有 Azure 服務（例如這些課程）都保留在通用資源群組下）。</span><span class="sxs-lookup"><span data-stu-id="96383-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="96383-207">設定服務的位置。</span><span class="sxs-lookup"><span data-stu-id="96383-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="96383-208">將 [**管理使用者**] 設定為 [**啟用**]。</span><span class="sxs-lookup"><span data-stu-id="96383-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="96383-209">將**SKU**設定為 [**基本**]。</span><span class="sxs-lookup"><span data-stu-id="96383-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="96383-210">按一下 [**建立**]，並等候服務建立。</span><span class="sxs-lookup"><span data-stu-id="96383-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="96383-211">通知顯示成功建立*容器*登錄後，請按一下 [**移至資源**] 以重新導向至您的服務頁面。</span><span class="sxs-lookup"><span data-stu-id="96383-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="96383-212">在 [ *Container Registry*服務] 頁面上，按一下 [**存取金鑰**]。</span><span class="sxs-lookup"><span data-stu-id="96383-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="96383-213">請注意下列參數（您可以使用您的 [記事本]）：</span><span class="sxs-lookup"><span data-stu-id="96383-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="96383-214">**登入伺服器**</span><span class="sxs-lookup"><span data-stu-id="96383-214">**Login Server**</span></span>
    2. <span data-ttu-id="96383-215">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="96383-215">**Username**</span></span>
    3. <span data-ttu-id="96383-216">**密碼**</span><span class="sxs-lookup"><span data-stu-id="96383-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="96383-217">第3章-IoT 中樞服務</span><span class="sxs-lookup"><span data-stu-id="96383-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="96383-218">現在您將開始建立和設定您的**IoT 中樞服務**。</span><span class="sxs-lookup"><span data-stu-id="96383-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="96383-219">如果尚未登入，請登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="96383-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="96383-220">登入之後，按一下左上角的 [**建立資源**]，並搜尋**IoT 中樞**，然後按一下**Enter 鍵**。</span><span class="sxs-lookup"><span data-stu-id="96383-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![搜尋儲存體帳戶](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="96383-222">新的頁面會提供**儲存體帳戶**服務的描述。</span><span class="sxs-lookup"><span data-stu-id="96383-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="96383-223">在此提示的左下方，按一下 [**建立**] 按鈕，以建立此服務的實例。</span><span class="sxs-lookup"><span data-stu-id="96383-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="96383-225">當您按一下 [**建立**] 之後，就會出現一個面板：</span><span class="sxs-lookup"><span data-stu-id="96383-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="96383-226">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="96383-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="96383-227">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="96383-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="96383-228">建議您將與單一專案相關聯的所有 Azure 服務（例如這些課程）都保留在通用資源群組下）。</span><span class="sxs-lookup"><span data-stu-id="96383-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="96383-229">如果您想要深入瞭解 Azure 資源群組，請遵循此[連結以瞭解如何管理資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="96383-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="96383-230">選取適當的**位置**（在您于本課程中建立的所有服務上使用相同的位置）。</span><span class="sxs-lookup"><span data-stu-id="96383-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="96383-231">為此服務實例插入您想要的**名稱**。</span><span class="sxs-lookup"><span data-stu-id="96383-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="96383-232">在頁面底部，按一下 [**下一步：大小和小數值]** 。</span><span class="sxs-lookup"><span data-stu-id="96383-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="96383-234">在此頁面中，選取您的**定價和級別層**（如果這是您第一個 IoT 中樞服務實例，則免費層應供您使用）。</span><span class="sxs-lookup"><span data-stu-id="96383-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="96383-235">按一下 [**審核] [+ 建立**]。</span><span class="sxs-lookup"><span data-stu-id="96383-235">Click on **Review + Create**.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="96383-237">檢查您的設定，然後按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="96383-237">Review your settings and click on **Create**.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="96383-239">通知出現後，會通知您成功建立*IoT 中樞*服務，請按一下 [**前往資源**] 以重新導向至您的服務頁面。</span><span class="sxs-lookup"><span data-stu-id="96383-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="96383-241">將左邊的側邊面板向左移動，直到您看到 [*自動裝置管理*]，按一下 [ **IoT Edge**]。</span><span class="sxs-lookup"><span data-stu-id="96383-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="96383-243">在顯示于右側的視窗中，按一下 [**新增 IoT Edge 裝置**]。</span><span class="sxs-lookup"><span data-stu-id="96383-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="96383-244">分頁會出現在右側。</span><span class="sxs-lookup"><span data-stu-id="96383-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="96383-245">在分頁中，為您的新裝置提供**裝置識別碼**（您所選擇的名稱）。</span><span class="sxs-lookup"><span data-stu-id="96383-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="96383-246">然後按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="96383-246">Then, click **Save**.</span></span> <span data-ttu-id="96383-247">如果您有**自動產生**核取，*主要*和*次要金鑰*會自動產生。</span><span class="sxs-lookup"><span data-stu-id="96383-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="96383-249">您將會流覽回 [ *IoT Edge 裝置*] 區段，其中會列出您的新裝置。</span><span class="sxs-lookup"><span data-stu-id="96383-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="96383-250">按一下您的新裝置（下圖中以紅色概述）。</span><span class="sxs-lookup"><span data-stu-id="96383-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![建立儲存體實例](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="96383-252">在出現的 [*裝置詳細資料*] 頁面上，複製 [**連接字串**（主要金鑰）]。</span><span class="sxs-lookup"><span data-stu-id="96383-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="96383-254">返回左側的面板，按一下 [*共用存取原則*] 加以開啟。</span><span class="sxs-lookup"><span data-stu-id="96383-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="96383-255">在出現的頁面上，按一下 [ **iothubowner**]，畫面右側就會出現一個分頁。</span><span class="sxs-lookup"><span data-stu-id="96383-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="96383-256">請注意（在您的記事本）**連接字串**（主要金鑰），以供稍後在將*連接字串*設定至您的裝置時使用。</span><span class="sxs-lookup"><span data-stu-id="96383-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="96383-258">第4章-設定開發環境</span><span class="sxs-lookup"><span data-stu-id="96383-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="96383-259">若要建立和部署*IoT 中樞邊緣*的模組，您需要在執行 Windows 10 的開發電腦上安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="96383-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="96383-260">[適用於 Windows 的 Docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)，它會要求您建立能夠下載的帳戶。</span><span class="sxs-lookup"><span data-stu-id="96383-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="96383-261">[![下載適用于 windows 的 docker](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="96383-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="96383-262">Docker 需要*Windows 10 專業* *版、Enterprise 14393*或*windows Server 2016 RTM*才能執行。</span><span class="sxs-lookup"><span data-stu-id="96383-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="96383-263">如果您執行的是其他版本的 Windows 10，您可以嘗試使用[Docker 工具箱](https://docs.docker.com/toolbox/toolbox_install_windows/)來安裝 docker。</span><span class="sxs-lookup"><span data-stu-id="96383-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="96383-264">[Python 3.6](https://www.python.org/downloads/)。</span><span class="sxs-lookup"><span data-stu-id="96383-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="96383-265">[![下載 python 3。6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="96383-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="96383-266">[Visual Studio Code （也稱為 VS Code）](https://code.visualstudio.com/download)。</span><span class="sxs-lookup"><span data-stu-id="96383-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="96383-267">[![下載 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="96383-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="96383-268">安裝上述軟體之後，您將需要重新開機電腦。</span><span class="sxs-lookup"><span data-stu-id="96383-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="96383-269">第5章-設定 Ubuntu 環境</span><span class="sxs-lookup"><span data-stu-id="96383-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="96383-270">現在您可以繼續設定執行**UBUNTU OS**的裝置。</span><span class="sxs-lookup"><span data-stu-id="96383-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="96383-271">請遵循下列步驟來安裝必要的軟體，以在您的面板上部署您的容器：</span><span class="sxs-lookup"><span data-stu-id="96383-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96383-272">您應該一律在具有**sudo**的終端機命令前面加上 [以系統管理員身分執行] 使用者。</span><span class="sxs-lookup"><span data-stu-id="96383-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="96383-273">亦即</span><span class="sxs-lookup"><span data-stu-id="96383-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="96383-274">開啟**Ubuntu 終端**機，然後使用下列命令來安裝**pip**：</span><span class="sxs-lookup"><span data-stu-id="96383-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [!提示]<span data-ttu-id="96383-275"> 您可以使用鍵盤快速鍵，輕鬆地開啟*終端*機： **Ctrl + Alt + T**。</span><span class="sxs-lookup"><span data-stu-id="96383-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="96383-276">在本章中，系統會提示您在*終端*機上使用您的裝置儲存體的許可權，並讓您輸入**y/n** （yes 或 no）、輸入 **' y '** ，然後按**enter**鍵以接受。</span><span class="sxs-lookup"><span data-stu-id="96383-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="96383-277">該命令完成後，請使用下列命令來安裝**捲曲**的：</span><span class="sxs-lookup"><span data-stu-id="96383-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="96383-278">安裝**pip**和**捲曲**之後，請使用下列命令來安裝**IoT Edge 運行**時間，這是在您的面板上部署和控制模組的必要項：</span><span class="sxs-lookup"><span data-stu-id="96383-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="96383-279">此時，系統會提示您開啟*執行時間設定檔*，以插入您在建立**IoT 中樞服務**時（在 [記事本] 中）所記下的**裝置連接字串**（在第[3 章的步驟 14](#chapter-3---the-iot-hub-service)中）。</span><span class="sxs-lookup"><span data-stu-id="96383-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="96383-280">在終端機上執行下列程式程式碼以開啟該檔案：</span><span class="sxs-lookup"><span data-stu-id="96383-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="96383-281">將會顯示**yaml**檔案，並可供您編輯：</span><span class="sxs-lookup"><span data-stu-id="96383-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="96383-282">當此檔案開啟時，可能會有點混淆。</span><span class="sxs-lookup"><span data-stu-id="96383-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="96383-283">您將會在*終端*機本身內編輯此檔案的文字。</span><span class="sxs-lookup"><span data-stu-id="96383-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="96383-284">使用鍵盤上的方向鍵向下箭號（您必須以一點方式向下滾動），以到達包含 "：</span><span class="sxs-lookup"><span data-stu-id="96383-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="96383-285">「 **\<將裝置連接字串新增到這裡 >** 」。</span><span class="sxs-lookup"><span data-stu-id="96383-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="96383-286">以您先前記下的**裝置連接字串**取代行，**包括括弧**。</span><span class="sxs-lookup"><span data-stu-id="96383-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="96383-287">當您的連接字串備妥時，請在鍵盤上按下**Ctrl X**鍵來儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="96383-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="96383-288">它會要求您輸入**Y**來確認。然後，按**enter**鍵以確認。</span><span class="sxs-lookup"><span data-stu-id="96383-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="96383-289">您會回到一般*終端*機。</span><span class="sxs-lookup"><span data-stu-id="96383-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="96383-290">一旦這些命令全都順利執行，您就會安裝**IoT Edge 運行**時間。</span><span class="sxs-lookup"><span data-stu-id="96383-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="96383-291">一旦初始化之後，執行時間就會在每次裝置開機時自行啟動，並且會進入背景，等待模組從**IoT 中樞服務**部署。</span><span class="sxs-lookup"><span data-stu-id="96383-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="96383-292">執行下列命令列以初始化*IoT Edge 運行*時間：</span><span class="sxs-lookup"><span data-stu-id="96383-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="96383-293">如果您對 yaml 檔案或上述設定進行變更，就必須在*終端*機中再次執行上述重新開機行。</span><span class="sxs-lookup"><span data-stu-id="96383-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="96383-294">執行下列命令列來檢查*IoT Edge 運行*時間狀態。</span><span class="sxs-lookup"><span data-stu-id="96383-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="96383-295">執行時間應該會以綠色文字顯示為作用中（執行中 **）** 。</span><span class="sxs-lookup"><span data-stu-id="96383-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="96383-296">按下**Ctrl + C**鍵，以結束 [狀態] 頁面。</span><span class="sxs-lookup"><span data-stu-id="96383-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="96383-297">您可以輸入下列命令，確認*IoT Edge 運行*時間是否已正確提取容器：</span><span class="sxs-lookup"><span data-stu-id="96383-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="96383-298">包含兩個（2）容器的清單應會出現。</span><span class="sxs-lookup"><span data-stu-id="96383-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="96383-299">這些是 IoT 中樞服務自動建立的預設模組（edgeAgent 和 edgeHub）。</span><span class="sxs-lookup"><span data-stu-id="96383-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="96383-300">一旦您建立並部署自己的模組，它們就會出現在此清單中的預設值之下。</span><span class="sxs-lookup"><span data-stu-id="96383-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="96383-301">第6章-安裝延伸模組</span><span class="sxs-lookup"><span data-stu-id="96383-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96383-302">接下來的幾個章節（6-9）是在您的 Windows 10 電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="96383-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="96383-303">開啟**VS Code**。</span><span class="sxs-lookup"><span data-stu-id="96383-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="96383-304">按一下 VS Code 左邊列的 [**擴充**功能（方形）] 按鈕，以開啟 [擴充功能]**面板**。</span><span class="sxs-lookup"><span data-stu-id="96383-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="96383-305">搜尋並安裝下列延伸模組（如下圖所示）：</span><span class="sxs-lookup"><span data-stu-id="96383-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="96383-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="96383-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="96383-307">Azure IoT 工具組</span><span class="sxs-lookup"><span data-stu-id="96383-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="96383-308">Docker</span><span class="sxs-lookup"><span data-stu-id="96383-308">Docker</span></span>   

    ![建立您的容器](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="96383-310">安裝延伸模組之後，請關閉再重新開啟 VS Code。</span><span class="sxs-lookup"><span data-stu-id="96383-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="96383-311">VS Code 開啟之後，請**流覽至 > \*\* 整合式**終端\*\*機。</span><span class="sxs-lookup"><span data-stu-id="96383-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="96383-312">您現在將安裝**Cookiecutter**。</span><span class="sxs-lookup"><span data-stu-id="96383-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="96383-313">在終端機中，執行下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="96383-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!提示]<span data-ttu-id="96383-314"> 此命令的問題：</span><span class="sxs-lookup"><span data-stu-id="96383-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="96383-315">重新開機 VS Code 和/或您的電腦。</span><span class="sxs-lookup"><span data-stu-id="96383-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="96383-316">您可能必須將**VS Code 終端**機切換至您用來安裝 Python 的電腦（例如**Powershell** ）（特別是在您的機器上已安裝 python 環境的情況下）。</span><span class="sxs-lookup"><span data-stu-id="96383-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="96383-317">當終端機開啟時，您會在終端機右側找到下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="96383-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="96383-318">![建立您的容器](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="96383-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="96383-319">請確定已在您的電腦上將**Python**安裝路徑新增為**環境變數**。</span><span class="sxs-lookup"><span data-stu-id="96383-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="96383-320">Cookiecutter 應該是相同位置路徑的一部分。</span><span class="sxs-lookup"><span data-stu-id="96383-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="96383-321">[如需環境變數的詳細資訊](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)，請遵循此連結。</span><span class="sxs-lookup"><span data-stu-id="96383-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="96383-322">**Cookiecutter**完成安裝之後，您應該重新開機電腦，以便在系統的環境中將**Cookiecutter**辨識為命令。</span><span class="sxs-lookup"><span data-stu-id="96383-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="96383-323">第7章-建立您的容器解決方案</span><span class="sxs-lookup"><span data-stu-id="96383-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="96383-324">此時，您需要使用模組來建立容器，以推送至*容器*登錄。</span><span class="sxs-lookup"><span data-stu-id="96383-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="96383-325">推送容器之後，您將使用*IoT 中樞 Edge*服務將它部署到您的裝置，而您的裝置正在執行*IoT Edge 運行*時間。</span><span class="sxs-lookup"><span data-stu-id="96383-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="96383-326">從 VS Code 按一下 [ **View** > **命令**選擇區]。</span><span class="sxs-lookup"><span data-stu-id="96383-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="96383-327">在 色板 中，搜尋並執行**Azure IoT Edge：新增 IoT Edge 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="96383-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="96383-328">流覽至您要建立解決方案的位置。</span><span class="sxs-lookup"><span data-stu-id="96383-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="96383-329">按**enter**鍵以接受位置。</span><span class="sxs-lookup"><span data-stu-id="96383-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="96383-330">為您的解決方案提供名稱。</span><span class="sxs-lookup"><span data-stu-id="96383-330">Give a name to your solution.</span></span> <span data-ttu-id="96383-331">按**enter**鍵，確認您提供的名稱。</span><span class="sxs-lookup"><span data-stu-id="96383-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="96383-332">現在，系統會提示您選擇解決方案的範本架構。</span><span class="sxs-lookup"><span data-stu-id="96383-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="96383-333">按一下 [ **Python 模組**]。</span><span class="sxs-lookup"><span data-stu-id="96383-333">Click **Python Module**.</span></span> <span data-ttu-id="96383-334">按**enter**鍵以確認此選擇。</span><span class="sxs-lookup"><span data-stu-id="96383-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="96383-335">提供您的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="96383-335">Give a name to your module.</span></span> <span data-ttu-id="96383-336">按**enter**鍵，以確認您的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="96383-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="96383-337">請務必記下模組名稱的附注（含您的「記事本」），因為它會在稍後使用。</span><span class="sxs-lookup"><span data-stu-id="96383-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="96383-338">您會發現預先建立的*Docker 映射存放庫*位址會出現在色板上。</span><span class="sxs-lookup"><span data-stu-id="96383-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="96383-339">看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="96383-339">It will look like:</span></span>

    <span data-ttu-id="96383-340">**localhost： 5000/-模組的名稱-** 。</span><span class="sxs-lookup"><span data-stu-id="96383-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="96383-341">刪除**localhost： 5000**，並在其位置插入\*容器\***登錄登入伺服器**位址，這是您在建立**container registry 服務**（[在步驟8中，第2章](#chapter-2---the-container-registry-service)）時記下的。</span><span class="sxs-lookup"><span data-stu-id="96383-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="96383-342">按**enter**鍵以確認位址。</span><span class="sxs-lookup"><span data-stu-id="96383-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="96383-343">此時，將會建立包含 Python 模組範本的解決方案，而且其結構會顯示在畫面左側的 [**流覽]** 索引標籤中 VS Code。</span><span class="sxs-lookup"><span data-stu-id="96383-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="96383-344">如果 [**流覽]** 索引標籤未開啟，您可以按一下左側列中最上方的按鈕來開啟它。</span><span class="sxs-lookup"><span data-stu-id="96383-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![建立您的容器](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="96383-346">本章的最後一個步驟是按一下並開啟**env**檔案，從 [**探索]** 索引標籤中，然後新增您的*容器*登錄使用者**名稱**和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="96383-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="96383-347">Git 會忽略此檔案，但是在建立容器時，將會設定認證以存取**Container Registry 服務**。</span><span class="sxs-lookup"><span data-stu-id="96383-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![建立您的容器](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="96383-349">第8章-編輯您的容器解決方案</span><span class="sxs-lookup"><span data-stu-id="96383-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="96383-350">您現在會藉由更新下列檔案來完成容器解決方案：</span><span class="sxs-lookup"><span data-stu-id="96383-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="96383-351">.py python 腳本。 *<span></span>*</span><span class="sxs-lookup"><span data-stu-id="96383-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="96383-352">*需求 .txt*。</span><span class="sxs-lookup"><span data-stu-id="96383-352">*requirements.txt*.</span></span>
- <span data-ttu-id="96383-353">*deployment. template. json*。</span><span class="sxs-lookup"><span data-stu-id="96383-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="96383-354">*Dockerfile. amd64*</span><span class="sxs-lookup"><span data-stu-id="96383-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="96383-355">接著，您會建立 [ *images* ] 資料夾，供 python 腳本用來檢查要與您的*自訂視覺模型*相符的影像。</span><span class="sxs-lookup"><span data-stu-id="96383-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="96383-356">最後，您將新增*標籤 .txt*檔案，以協助讀取您的模型，以及*model. pb*檔案，也就是您的模型。</span><span class="sxs-lookup"><span data-stu-id="96383-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="96383-357">在 VS Code 開啟時，流覽至您的模組資料夾，然後尋找名 **<span></span>為 .py**的腳本。</span><span class="sxs-lookup"><span data-stu-id="96383-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="96383-358">按兩下以開啟它。</span><span class="sxs-lookup"><span data-stu-id="96383-358">Double-click to open it.</span></span>

2. <span data-ttu-id="96383-359">刪除檔案的內容，並插入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="96383-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="96383-360">開啟名為 [**需求 .txt**] 的檔案，並以下列內容取代其內容：</span><span class="sxs-lookup"><span data-stu-id="96383-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="96383-361">開啟名為**deployment**的檔案，並遵循下列指導方針來取代其內容：</span><span class="sxs-lookup"><span data-stu-id="96383-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="96383-362">因為您會有自己的唯一 JSON 結構，所以您必須手動編輯它（而不是複製範例）。</span><span class="sxs-lookup"><span data-stu-id="96383-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="96383-363">若要這麼做，請使用下列影像做為指南。</span><span class="sxs-lookup"><span data-stu-id="96383-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="96383-364">看起來會與您不同，但您**不應該變更的區域會以黃色反白顯示**。</span><span class="sxs-lookup"><span data-stu-id="96383-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="96383-365">**您需要刪除的區段會反白顯示為紅色。**</span><span class="sxs-lookup"><span data-stu-id="96383-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="96383-366">請小心刪除正確的方括弧，同時移除逗號。</span><span class="sxs-lookup"><span data-stu-id="96383-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![建立您的容器](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="96383-368">完成的 JSON 看起來應該如下圖所示（但唯一的差異如下：使用者*名稱/密碼/模組名稱/模組參考*）：</span><span class="sxs-lookup"><span data-stu-id="96383-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![建立您的容器](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="96383-370">開啟名為**Dockerfile**的檔案，並以下列內容取代其內容：</span><span class="sxs-lookup"><span data-stu-id="96383-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="96383-371">以滑鼠右鍵按一下 [**模組**] 底下的資料夾（它會有您先前提供的名稱; 在此範例中，它會被稱為 [ *pythonmodule*]），然後按一下 [**新增資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="96383-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="96383-372">將資料夾命名為**images**。</span><span class="sxs-lookup"><span data-stu-id="96383-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="96383-373">在資料夾內，新增一些包含滑鼠或鍵盤的影像。</span><span class="sxs-lookup"><span data-stu-id="96383-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="96383-374">這些會是 Tensorflow 模型將分析的影像。</span><span class="sxs-lookup"><span data-stu-id="96383-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="96383-375">如果您要使用自己的模型，則需要變更它以反映您自己的模型資料。</span><span class="sxs-lookup"><span data-stu-id="96383-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="96383-376">您現在必須從[第1章](#chapter-1---retrieve-the-custom-vision-model)的「模型」資料夾中，取出您先前下載（或從您自己的**自訂視覺服務**建立）的**標籤 .txt**和**model. pb**檔案。</span><span class="sxs-lookup"><span data-stu-id="96383-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="96383-377">當您擁有檔案之後，請將它們放在您的方案中，再加上其他檔案。</span><span class="sxs-lookup"><span data-stu-id="96383-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="96383-378">最後的結果看起來應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="96383-378">The final result should look like the image below:</span></span>

    ![建立您的容器](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="96383-380">第9章-將解決方案封裝為容器</span><span class="sxs-lookup"><span data-stu-id="96383-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="96383-381">您現在已準備好「封裝」您的檔案作為容器，並將其推送至您的**Azure Container Registry**。</span><span class="sxs-lookup"><span data-stu-id="96383-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="96383-382">在 VS Code 中，開啟*整合式終端*機（**View** > **整合式終端**機或**Ctrl**+ **\`** ），然後使用下列程式程式碼來登入**Docker** （將命令的值替換為**Azure Container Registry （ACR）** 的認證：</span><span class="sxs-lookup"><span data-stu-id="96383-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="96383-383">以滑鼠右鍵按一下 [檔案**部署**]，然後按一下 [**組建 IoT Edge 方案**]。</span><span class="sxs-lookup"><span data-stu-id="96383-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="96383-384">此組建程式需要相當長的時間（視您的裝置而定），因此請備妥等待。</span><span class="sxs-lookup"><span data-stu-id="96383-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="96383-385">在建立程式完成之後，會在稱為**config**的新資料夾內建立**部署 json**檔案。</span><span class="sxs-lookup"><span data-stu-id="96383-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![建立部署](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="96383-387">再次開啟**命令**選擇區，然後搜尋**Azure： Sign In**。</span><span class="sxs-lookup"><span data-stu-id="96383-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="96383-388">遵循使用您的 Azure 帳號憑證的提示;VS Code 將提供您*複製和開啟*的選項，它會複製您即將需要的裝置程式碼，並開啟您的預設網頁瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="96383-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="96383-389">當系統要求時，貼上裝置程式碼，以驗證您的電腦。</span><span class="sxs-lookup"><span data-stu-id="96383-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![複製並開啟](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="96383-391">登入之後，您會在 [*探索*] 面板的底部看到一個稱為 [ **Azure IoT 中樞裝置**] 的新區段。</span><span class="sxs-lookup"><span data-stu-id="96383-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="96383-392">按一下此區段以將它展開。</span><span class="sxs-lookup"><span data-stu-id="96383-392">Click this section to expand it.</span></span>

    ![edge 裝置](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="96383-394">如果您的裝置不在這裡，您將需要以滑鼠右鍵按一下 [ *Azure IoT 中樞裝置*]，然後按一下 [**設定 IoT 中樞連接字串**]。</span><span class="sxs-lookup"><span data-stu-id="96383-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="96383-395">您接著會看到 [**命令**選擇區] （位於 VS Code 頂端）會提示您輸入*連接字串*。</span><span class="sxs-lookup"><span data-stu-id="96383-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="96383-396">這是您在[第3章](#chapter-3---the-iot-hub-service)結尾處記下的*連接字串*。</span><span class="sxs-lookup"><span data-stu-id="96383-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="96383-397">當您複製中的字串之後，請按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="96383-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="96383-398">您的裝置應該會載入並顯示。</span><span class="sxs-lookup"><span data-stu-id="96383-398">Your device should load, and appear.</span></span> <span data-ttu-id="96383-399">以滑鼠右鍵按一下裝置名稱，然後按一下 [**建立單一裝置的部署**]。</span><span class="sxs-lookup"><span data-stu-id="96383-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![建立部署](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="96383-401">您會看到 [檔案*瀏覽器*] 提示字元，您可以在其中流覽至 [ **config** ] 資料夾，然後選取 [**部署 json** ] 檔案。</span><span class="sxs-lookup"><span data-stu-id="96383-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="96383-402">選取該檔案後，按一下 [**選取 Edge 部署資訊清單**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="96383-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![建立部署](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="96383-404">此時，您已為您的**IoT 中樞服務**提供資訊清單，以將您的容器（模組）部署到您的**Azure Container Registry**，並有效地將它部署到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="96383-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="96383-405">若要查看從您的裝置傳送到 IoT 中樞的訊息，請在 [ **Azure IoT 中樞裝置**] 區段的 [ **Explorer** ] 面板中，以滑鼠右鍵按一下您的裝置名稱，然後按一下 [**開始監視 D2C 訊息**]。</span><span class="sxs-lookup"><span data-stu-id="96383-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="96383-406">從您的裝置傳送的訊息應該會出現在 VS 終端機中。</span><span class="sxs-lookup"><span data-stu-id="96383-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="96383-407">請耐心等候，因為這可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="96383-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="96383-408">請參閱下一章的偵錯工具，並檢查部署是否成功。</span><span class="sxs-lookup"><span data-stu-id="96383-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="96383-409">此模組現在會逐一查看**images**資料夾中的影像，並使用每個反復專案加以分析。</span><span class="sxs-lookup"><span data-stu-id="96383-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="96383-410">這顯然只是示範如何讓基本機器學習模型在 IoT Edge 的裝置環境中工作。</span><span class="sxs-lookup"><span data-stu-id="96383-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="96383-411">若要擴充此範例的功能，您可以透過數種方式繼續進行。</span><span class="sxs-lookup"><span data-stu-id="96383-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="96383-412">其中一種方式可能包括容器中的一些程式碼，它會從連線到裝置的網路攝影機中捕捉相片，並將影像儲存在 images 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="96383-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="96383-413">另一種方式可能是將影像從 IoT 裝置複製到容器中。</span><span class="sxs-lookup"><span data-stu-id="96383-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="96383-414">做法是在 IoT 裝置終端機中執行下列命令（如果您想要將此程式自動化，可能是小型應用程式可以執行此作業）。</span><span class="sxs-lookup"><span data-stu-id="96383-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="96383-415">您可以從儲存檔案的資料夾位置手動執行，以測試此命令：</span><span class="sxs-lookup"><span data-stu-id="96383-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="96383-416">第10章-調試 IoT Edge 執行時間</span><span class="sxs-lookup"><span data-stu-id="96383-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="96383-417">以下是命令列和秘訣的清單，可協助您從**Ubuntu 裝置**監視和偵錯工具*IoT Edge 運行*時間的訊息活動。</span><span class="sxs-lookup"><span data-stu-id="96383-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="96383-418">執行下列命令列來檢查*IoT Edge 運行*時間狀態：</span><span class="sxs-lookup"><span data-stu-id="96383-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="96383-419">請記得按**Ctrl + C**來完成狀態的查看。</span><span class="sxs-lookup"><span data-stu-id="96383-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="96383-420">列出目前已部署的容器。</span><span class="sxs-lookup"><span data-stu-id="96383-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="96383-421">如果*IoT 中樞服務*已成功部署容器，則會藉由執行下列命令列來顯示它們：</span><span class="sxs-lookup"><span data-stu-id="96383-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="96383-422">或</span><span class="sxs-lookup"><span data-stu-id="96383-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="96383-423">上述是檢查模組是否已成功部署的好方法，因為它會出現在清單中;否則，您**只**會看到*edgeHub*和*edgeAgent*。</span><span class="sxs-lookup"><span data-stu-id="96383-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="96383-424">若要顯示容器的程式碼記錄，請執行下列命令列：</span><span class="sxs-lookup"><span data-stu-id="96383-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="96383-425">**管理 IoT Edge 執行時間的有用命令：**</span><span class="sxs-lookup"><span data-stu-id="96383-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="96383-426">若要刪除主機中的所有容器：</span><span class="sxs-lookup"><span data-stu-id="96383-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="96383-427">若要停止*IoT Edge 運行*時間：</span><span class="sxs-lookup"><span data-stu-id="96383-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="96383-428">第11章-建立資料表服務</span><span class="sxs-lookup"><span data-stu-id="96383-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="96383-429">流覽回到您的 Azure 入口網站，您將藉由建立儲存體資源來建立 Azure 資料表服務。</span><span class="sxs-lookup"><span data-stu-id="96383-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="96383-430">如果尚未登入，請登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="96383-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="96383-431">登入之後，按一下左上角的 [**建立資源**]，並搜尋 [**儲存體帳戶**]，然後按下**enter**鍵以開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="96383-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="96383-432">出現之後，按一下清單中的 [**儲存體帳戶-blob、檔案、資料表、佇列**]。</span><span class="sxs-lookup"><span data-stu-id="96383-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![搜尋儲存體帳戶](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="96383-434">新的頁面會提供**儲存體帳戶**服務的描述。</span><span class="sxs-lookup"><span data-stu-id="96383-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="96383-435">在此提示的左下方，按一下 [**建立**] 按鈕，以建立此服務的實例。</span><span class="sxs-lookup"><span data-stu-id="96383-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![建立儲存體實例](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="96383-437">當您按一下 [**建立**] 之後，就會出現一個面板：</span><span class="sxs-lookup"><span data-stu-id="96383-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="96383-438">為此服務實例插入您想要的**名稱**（*必須全部小寫*）。</span><span class="sxs-lookup"><span data-stu-id="96383-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="96383-439">針對 [**部署模型**]，按一下 [ **Resource manager**]。</span><span class="sxs-lookup"><span data-stu-id="96383-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="96383-440">針對 [**帳戶種類**]，使用下拉式功能表，按一下 [**儲存體（一般用途 v1）** ]。</span><span class="sxs-lookup"><span data-stu-id="96383-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="96383-441">按一下適當的**位置**。</span><span class="sxs-lookup"><span data-stu-id="96383-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="96383-442">針對 [**複寫**] 下拉式功能表，按一下 [**讀取權限-異地-多餘儲存體（RA-GRS）** ]。</span><span class="sxs-lookup"><span data-stu-id="96383-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="96383-443">針對 [**效能**]，請按一下 [**標準**]。</span><span class="sxs-lookup"><span data-stu-id="96383-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="96383-444">在 [**需要安全傳輸**] 區段中，按一下 [**停用**]。</span><span class="sxs-lookup"><span data-stu-id="96383-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="96383-445">從 [**訂**用帳戶] 下拉式功能表中，按一下適當的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="96383-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="96383-446">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="96383-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="96383-447">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的費用。</span><span class="sxs-lookup"><span data-stu-id="96383-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="96383-448">建議您將與單一專案相關聯的所有 Azure 服務（例如這些課程）都保留在通用資源群組下）。</span><span class="sxs-lookup"><span data-stu-id="96383-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="96383-449">如果您想要深入瞭解 Azure 資源群組，請遵循此[連結以瞭解如何管理資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="96383-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="96383-450">如果這是您的選項，請將 [**虛擬網路**] 保留為 [**停用**]。</span><span class="sxs-lookup"><span data-stu-id="96383-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="96383-451">按一下 \[建立\]。</span><span class="sxs-lookup"><span data-stu-id="96383-451">Click **Create**.</span></span>

        ![填入儲存體詳細資料](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="96383-453">按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="96383-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="96383-454">建立服務實例之後，入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="96383-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="96383-455">按一下 [通知] 以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="96383-455">Click on the notifications to explore your new Service instance.</span></span>

    ![新的儲存體通知](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="96383-457">按一下通知中的 [**移至資源**] 按鈕，您將會進入新的儲存體服務實例的 [總覽] 頁面。</span><span class="sxs-lookup"><span data-stu-id="96383-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![前往資源](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="96383-459">從 [總覽] 頁面，按一下右側的 [**資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="96383-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![多](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="96383-461">右側面板會變更以顯示**資料表服務**資訊，您必須在其中加入新的資料表。</span><span class="sxs-lookup"><span data-stu-id="96383-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="96383-462">若要這麼做，請按一下左上角的 [ **+ 資料表**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="96383-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![開啟資料表](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="96383-464">將會顯示新的頁面，您必須在其中輸入**資料表名稱**。</span><span class="sxs-lookup"><span data-stu-id="96383-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="96383-465">這是您稍後章節中用來參考應用程式中資料的名稱（建立函數應用程式，Power BI）。</span><span class="sxs-lookup"><span data-stu-id="96383-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="96383-466">將**IoTMessages**插入為名稱（您可以自行選擇，並在本檔稍後使用時記住），然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="96383-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="96383-467">建立新的資料表之後，您就可以在 [**資料表服務**] 頁面（底部）中看到它。</span><span class="sxs-lookup"><span data-stu-id="96383-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![已建立新資料表](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="96383-469">現在，按一下 [**存取金鑰**] 並取得**儲存體帳戶名稱**和**金鑰**的複本（使用您的 [記事本]），稍後在本課程中建立**Azure 函數應用程式**時，將會用到這些值。</span><span class="sxs-lookup"><span data-stu-id="96383-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![已建立新資料表](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="96383-471">再次使用左側的面板，流覽至 [*資料表服務*] 區段，然後按一下 [**資料表**] （或 **[流覽資料表]** ，在較新的入口網站中），並複製**資料表 URL** （使用您的 [記事本]）。</span><span class="sxs-lookup"><span data-stu-id="96383-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="96383-472">當您將資料表連結到**Power BI**應用程式時，將會在本課程稍後使用此值。</span><span class="sxs-lookup"><span data-stu-id="96383-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![已建立新資料表](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="96383-474">第12章-完成 Azure 資料表</span><span class="sxs-lookup"><span data-stu-id="96383-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="96383-475">既然您已設定**資料表服務**儲存體帳戶，就可以在其中加入資料，這將用來儲存和抓取資訊。</span><span class="sxs-lookup"><span data-stu-id="96383-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="96383-476">您可以透過**Visual Studio**來編輯您的資料表。</span><span class="sxs-lookup"><span data-stu-id="96383-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="96383-477">開啟**Visual Studio** （**不**Visual Studio Code）。</span><span class="sxs-lookup"><span data-stu-id="96383-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="96383-478">從功能表中，按一下 [ **View** > **Cloud Explorer**]。</span><span class="sxs-lookup"><span data-stu-id="96383-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![開啟 cloud explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="96383-480">**Cloud Explorer**將會開啟為停駐的專案（請耐心等候，因為載入可能需要一些時間）。</span><span class="sxs-lookup"><span data-stu-id="96383-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="96383-481">如果看不到您用來建立*儲存體帳戶*的訂用帳戶，請確定您有：</span><span class="sxs-lookup"><span data-stu-id="96383-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="96383-482">登入與您用於 Azure 入口網站的帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="96383-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="96383-483">從 [帳戶管理] 頁面選取您的訂用帳戶（您可能需要從您的帳戶設定套用篩選）：</span><span class="sxs-lookup"><span data-stu-id="96383-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![尋找訂用帳戶](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="96383-485">將會顯示您的 Azure 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="96383-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="96383-486">尋找 [**儲存體帳戶**]，然後按一下該左側的箭號以展開您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="96383-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![開啟儲存體帳戶](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="96383-488">擴充之後，應該就可以使用新建立的**儲存體帳戶**。</span><span class="sxs-lookup"><span data-stu-id="96383-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="96383-489">按一下儲存體左邊的箭號，然後展開 [尋找**資料表**]，再按一下該按鈕旁邊的箭號，以顯示您在上一章中建立的**資料表**。</span><span class="sxs-lookup"><span data-stu-id="96383-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="96383-490">按兩下您的**資料表**。</span><span class="sxs-lookup"><span data-stu-id="96383-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="96383-491">您的資料表將會在 Visual Studio 視窗的中央開啟。</span><span class="sxs-lookup"><span data-stu-id="96383-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="96383-492">按一下 [資料表] 圖示，並在其上加上 **+** （加號）。</span><span class="sxs-lookup"><span data-stu-id="96383-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![加入新的資料表](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="96383-494">隨即會出現一個視窗，提示您*加入實體*。</span><span class="sxs-lookup"><span data-stu-id="96383-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="96383-495">您只會建立一個實體，但它會有三個屬性。</span><span class="sxs-lookup"><span data-stu-id="96383-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="96383-496">您會發現*PartitionKey*和*RowKey*已提供，因為資料表會使用這些來尋找您的資料。</span><span class="sxs-lookup"><span data-stu-id="96383-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![資料分割和資料列索引鍵](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="96383-498">更新下列值：</span><span class="sxs-lookup"><span data-stu-id="96383-498">Update the following values:</span></span>

    - <span data-ttu-id="96383-499">名稱： **PartitionKey**，值： **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="96383-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="96383-500">名稱： **RowKey**，值： **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="96383-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="96383-501">然後，按一下 [**新增屬性**] （在 [*新增實體*] 視窗的左下方），然後加入下列屬性：</span><span class="sxs-lookup"><span data-stu-id="96383-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="96383-502">以*字串*的形式**MessageContent**，將此值保留空白。</span><span class="sxs-lookup"><span data-stu-id="96383-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="96383-503">您的資料表應符合下圖中的其中一個：</span><span class="sxs-lookup"><span data-stu-id="96383-503">Your table should match the one in the image below:</span></span>

    ![新增正確的值](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="96383-505">實體在資料列索引鍵中的數位為1的原因，是因為您可能想要加入更多的訊息，而您希望進一步試驗此課程。</span><span class="sxs-lookup"><span data-stu-id="96383-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="96383-506">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="96383-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="96383-507">您的資料表現在已準備好可供使用。</span><span class="sxs-lookup"><span data-stu-id="96383-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="96383-508">第13章-建立 Azure 函數應用程式</span><span class="sxs-lookup"><span data-stu-id="96383-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="96383-509">現在您可以建立*Azure 函數應用程式*， *IoT 中樞服務*會呼叫這項資訊，將*IoT Edge*的裝置訊息儲存在您在上一章中建立的**表格**服務。</span><span class="sxs-lookup"><span data-stu-id="96383-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="96383-510">首先，您必須建立可讓您的 Azure 函式載入所需程式庫的檔案。</span><span class="sxs-lookup"><span data-stu-id="96383-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="96383-511">開啟 [**記事本**] （按*Windows 鍵*，然後輸入 [*記事本*]）。</span><span class="sxs-lookup"><span data-stu-id="96383-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![開啟 [記事本]](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="96383-513">在 [記事本] 開啟的情況下，將下面的 JSON 結構插入其中。</span><span class="sxs-lookup"><span data-stu-id="96383-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="96383-514">完成之後，請將它儲存在您的桌上型電腦上做為**專案 json**。</span><span class="sxs-lookup"><span data-stu-id="96383-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="96383-515">此檔案會定義您的函式將使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="96383-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="96383-516">如果您已使用 NuGet，它看起來會很熟悉。</span><span class="sxs-lookup"><span data-stu-id="96383-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="96383-517">請務必正確地命名;請確定它**的副檔名不是 .txt** 。</span><span class="sxs-lookup"><span data-stu-id="96383-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="96383-518">請參閱下文以取得參考：</span><span class="sxs-lookup"><span data-stu-id="96383-518">See below for reference:</span></span>
    >
    > ![JSON 儲存](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="96383-520">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="96383-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="96383-521">登入之後，請按一下左上角的 [**建立資源**]，並搜尋**函數應用程式**，然後按**enter**鍵以進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="96383-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="96383-522">按一下結果中的 [*函數應用程式*] 以開啟新的面板。</span><span class="sxs-lookup"><span data-stu-id="96383-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![搜尋函數應用程式](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="96383-524">新的面板會提供**函數應用程式**服務的描述。</span><span class="sxs-lookup"><span data-stu-id="96383-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="96383-525">在此面板的左下方，按一下 [**建立**] 按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="96383-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![函數應用程式實例](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="96383-527">當您按一下 [**建立**] 之後，請填寫下列內容：</span><span class="sxs-lookup"><span data-stu-id="96383-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="96383-528">針對 [**應用程式名稱**]，插入您想要的此服務實例名稱。</span><span class="sxs-lookup"><span data-stu-id="96383-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="96383-529">選取**訂**用帳戶。</span><span class="sxs-lookup"><span data-stu-id="96383-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="96383-530">選取適合您的定價層，如果這是您第一次建立**函數應用程式服務**，免費層應可供您使用。</span><span class="sxs-lookup"><span data-stu-id="96383-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="96383-531">選擇**資源群組**或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="96383-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="96383-532">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的費用。</span><span class="sxs-lookup"><span data-stu-id="96383-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="96383-533">建議您將與單一專案相關聯的所有 Azure 服務（例如這些課程）都保留在通用資源群組下）。</span><span class="sxs-lookup"><span data-stu-id="96383-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="96383-534">如果您想要深入瞭解 Azure 資源群組，請遵循此[連結以瞭解如何管理資源群組](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="96383-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="96383-535">針對 [**作業系統**]，按一下 [Windows]，因為這是所需的平臺。</span><span class="sxs-lookup"><span data-stu-id="96383-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="96383-536">選取**主控方案**（本教學課程使用的是取用**方案**）。</span><span class="sxs-lookup"><span data-stu-id="96383-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="96383-537">選取**位置**（選擇與您在上一個步驟中建立的儲存體相同的位置）</span><span class="sxs-lookup"><span data-stu-id="96383-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="96383-538">針對 [**儲存體**] 區段，**您必須選取您在上一個步驟中建立的儲存體服務**。</span><span class="sxs-lookup"><span data-stu-id="96383-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="96383-539">您不需要在此應用程式中*Application Insights* ，因此請隨意**保留。**</span><span class="sxs-lookup"><span data-stu-id="96383-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="96383-540">按一下 \[建立\]。</span><span class="sxs-lookup"><span data-stu-id="96383-540">Click **Create**.</span></span>

        ![建立新的實例](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="96383-542">按一下 [**建立**] 之後，您必須等候服務建立，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="96383-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="96383-543">建立服務實例之後，入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="96383-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![新通知](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="96383-545">一旦部署成功（已完成），請按一下通知。</span><span class="sxs-lookup"><span data-stu-id="96383-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="96383-546">按一下通知中的 [**移至資源**] 按鈕，探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="96383-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![前往資源](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="96383-548">在新面板的左側，按一下 [函式] 旁邊的 **+** （加號）圖示 *，以*建立新的函數。</span><span class="sxs-lookup"><span data-stu-id="96383-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![加入新函數](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="96383-550">在中央面板中，將會出現 [**函數**建立] 視窗。</span><span class="sxs-lookup"><span data-stu-id="96383-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="96383-551">進一步向下流覽，然後按一下 [**自訂函數**]。</span><span class="sxs-lookup"><span data-stu-id="96383-551">Scroll down further, and click on **Custom function**.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="96383-553">在下一個頁面上向下流覽，直到您找到**IoT 中樞（事件中樞）** ，然後按一下它。</span><span class="sxs-lookup"><span data-stu-id="96383-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="96383-555">在 [ **IoT 中樞（事件中樞）** ] 分頁中，將語言**C#** 設定為，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="96383-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="96383-557">在隨即出現的視窗中，確定已選取 [ **IoT 中樞**]，而且 [ *IoT 中樞*] 欄位的名稱與您先前建立的*IoT 中樞服務*名稱（[在第3章的步驟8中](#chapter-3---the-iot-hub-service)）對應。</span><span class="sxs-lookup"><span data-stu-id="96383-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="96383-558">然後按一下 [**選取**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="96383-558">Then click the **Select** button.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="96383-560">回到 [ **IoT 中樞（事件中樞）** ] 分頁，按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="96383-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="96383-562">系統會將您重新導向至函數編輯器。</span><span class="sxs-lookup"><span data-stu-id="96383-562">You will be redirected to the function editor.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="96383-564">刪除其中的所有程式碼，並取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="96383-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="96383-565">變更下列變數，使其對應至您在**儲存體帳戶**中可找到的適當值（**資料表**和**儲存體**值，[分別是步驟11和13，第11章](#chapter-11---create-table-service)）：</span><span class="sxs-lookup"><span data-stu-id="96383-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="96383-566">**tableName**，並以您的**資料表**名稱放置在您的**儲存體帳戶**中。</span><span class="sxs-lookup"><span data-stu-id="96383-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="96383-567">**tableURL**，使用您的**儲存體帳戶**中的**資料表**URL。</span><span class="sxs-lookup"><span data-stu-id="96383-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="96383-568">**storageAccountName**，其值的名稱會對應至您的**儲存體帳戶**名稱名稱。</span><span class="sxs-lookup"><span data-stu-id="96383-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="96383-569">**storageAccountKey**，其中包含您先前建立的儲存體服務中取得的金鑰。</span><span class="sxs-lookup"><span data-stu-id="96383-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="96383-571">備妥程式碼後，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="96383-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="96383-572">接下來，按一下頁面右側的 [ **\<** ] （箭號）圖示。</span><span class="sxs-lookup"><span data-stu-id="96383-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="96383-574">面板會從右邊滑入。</span><span class="sxs-lookup"><span data-stu-id="96383-574">A panel will slide in from the right.</span></span> <span data-ttu-id="96383-575">在該面板中，按一下 **[上傳**]，檔案*瀏覽器*隨即出現。</span><span class="sxs-lookup"><span data-stu-id="96383-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="96383-576">流覽至，然後按一下 [您先前在**記事本**中建立的**專案. json**檔案]，再按一下 [**開啟**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="96383-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="96383-577">此檔案會定義您的函式將使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="96383-577">This file defines the libraries that your function will use.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="96383-579">檔案上傳之後，它就會出現在右邊的面板中。</span><span class="sxs-lookup"><span data-stu-id="96383-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="96383-580">按一下它會在**函數**編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="96383-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="96383-581">其外觀必須與下一個影像**完全**相同。</span><span class="sxs-lookup"><span data-stu-id="96383-581">It must look **exactly** the same as the next image.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="96383-583">此時，測試函式的功能以將訊息儲存在您的*資料表*上是很好的做法。</span><span class="sxs-lookup"><span data-stu-id="96383-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="96383-584">在視窗的右上方，按一下 [**測試**]。</span><span class="sxs-lookup"><span data-stu-id="96383-584">On the top right side of the window, click on **Test**.</span></span>

    ![自訂函數](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="96383-586">在**要求主體**上插入訊息，如上圖所示，然後按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="96383-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="96383-587">函式將會執行，並顯示結果狀態（您會在 [*輸出*] 視窗上方看到 [已**接受綠色狀態 202**]，這表示它是成功的呼叫）：</span><span class="sxs-lookup"><span data-stu-id="96383-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![輸出結果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="96383-589">第14章-查看活動訊息</span><span class="sxs-lookup"><span data-stu-id="96383-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="96383-590">如果您現在開啟 Visual Studio （**而不**是 Visual Studio Code），您可以將測試訊息結果視覺化，因為它會儲存在*MessageContent*字串區域中。</span><span class="sxs-lookup"><span data-stu-id="96383-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![自訂函數](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="96383-592">當資料表服務和函數應用程式就緒時，您的 Ubuntu 裝置訊息會出現在*IoTMessages*資料表中。</span><span class="sxs-lookup"><span data-stu-id="96383-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="96383-593">如果尚未執行，請重新開機您的裝置，您就可以使用 Visual Studio *Cloud Explorer*，在資料表中查看來自您裝置和模組的結果訊息。</span><span class="sxs-lookup"><span data-stu-id="96383-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![將資料視覺化](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="96383-595">第15章-Power BI 設定</span><span class="sxs-lookup"><span data-stu-id="96383-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="96383-596">若要將您的 IOT 裝置中的資料視覺化，您會設定**Power BI** （桌上出版本），以從您剛建立的*資料表*服務收集資料。</span><span class="sxs-lookup"><span data-stu-id="96383-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="96383-597">然後，Power BI 的*HoloLens*版本將會使用該資料將結果視覺化。</span><span class="sxs-lookup"><span data-stu-id="96383-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="96383-598">開啟 Windows 10 上的 Microsoft Store，然後搜尋**Power BI Desktop**。</span><span class="sxs-lookup"><span data-stu-id="96383-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="96383-600">下載應用程式。</span><span class="sxs-lookup"><span data-stu-id="96383-600">Download the application.</span></span> <span data-ttu-id="96383-601">完成下載之後，請將它開啟。</span><span class="sxs-lookup"><span data-stu-id="96383-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="96383-602">使用您的**Microsoft 365 帳戶**登入*Power BI* 。</span><span class="sxs-lookup"><span data-stu-id="96383-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="96383-603">您可能會被重新導向至瀏覽器以進行註冊。</span><span class="sxs-lookup"><span data-stu-id="96383-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="96383-604">註冊之後，請返回 Power BI 應用程式，然後再次登入。</span><span class="sxs-lookup"><span data-stu-id="96383-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="96383-605">按一下 [**取得資料**]，然後按一下 [**其他 ...** ]。</span><span class="sxs-lookup"><span data-stu-id="96383-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="96383-607">按一下 [ **Azure**]、[ **azure 表格儲存體**]，然後按一下 **[連線]** 。</span><span class="sxs-lookup"><span data-stu-id="96383-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="96383-609">建立表格服務時，系統會提示您插入稍早收集的**資料表 URL** （[在第11章的步驟13中](#chapter-11---create-table-service)）。</span><span class="sxs-lookup"><span data-stu-id="96383-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="96383-610">插入 URL 之後，請刪除參考「子資料夾」資料表的路徑部分（在此課程中為 IoTMessages）。</span><span class="sxs-lookup"><span data-stu-id="96383-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="96383-611">最後的結果應該如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="96383-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="96383-612">然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="96383-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="96383-614">建立表格儲存體時，系統會提示您插入先前記下的**儲存體金鑰**（[在第11章的步驟11中](#chapter-11---create-table-service)）。</span><span class="sxs-lookup"><span data-stu-id="96383-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="96383-615">然後按一下 **[連線]** 。</span><span class="sxs-lookup"><span data-stu-id="96383-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="96383-617">[導覽**器] 面板**隨即顯示，並勾選您資料表旁的方塊，然後按一下 [**載入**]。</span><span class="sxs-lookup"><span data-stu-id="96383-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="96383-619">您的資料表現在已載入 Power BI，但它需要查詢來顯示其中的值。</span><span class="sxs-lookup"><span data-stu-id="96383-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="96383-620">若要這麼做，請在畫面右側的 [**欄位] 面板**中，以滑鼠右鍵按一下資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="96383-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="96383-621">然後按一下 [**編輯查詢**]。</span><span class="sxs-lookup"><span data-stu-id="96383-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="96383-623">**Power Query 編輯器**會開啟為新視窗，並顯示您的資料表。</span><span class="sxs-lookup"><span data-stu-id="96383-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="96383-624">按一下資料表的 [*內容*] 資料行中的 [文字**記錄**]，將儲存的內容視覺化。</span><span class="sxs-lookup"><span data-stu-id="96383-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="96383-626">按一下視窗左上角的 [移**至資料表**]。</span><span class="sxs-lookup"><span data-stu-id="96383-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="96383-628">按一下 [**關閉 &** 套用]。</span><span class="sxs-lookup"><span data-stu-id="96383-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="96383-630">完成載入查詢後，在 [**欄位] 面板**的右側畫面中，勾選對應于參數**名稱**和**值**的方塊，以將**MessageContent**的資料行內容視覺化。</span><span class="sxs-lookup"><span data-stu-id="96383-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="96383-632">按一下視窗左上角的**藍色磁片圖示**，將您的工作儲存在您選擇的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="96383-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="96383-634">您現在可以按一下 [發佈] 按鈕，將您的資料表上傳至您的工作區。</span><span class="sxs-lookup"><span data-stu-id="96383-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="96383-635">出現提示時，按一下 [**我的工作區**] 並按一下 [*選取*]。</span><span class="sxs-lookup"><span data-stu-id="96383-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="96383-636">等候它顯示提交成功的結果。</span><span class="sxs-lookup"><span data-stu-id="96383-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="96383-639">下一章是 HoloLens 特有的。</span><span class="sxs-lookup"><span data-stu-id="96383-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="96383-640">Power BI 目前無法做為沉浸式應用程式使用，但是您可以透過桌面應用程式，在 Windows Mixed Reality 入口網站（也稱為 Cliff 房子）中執行桌上出版本。</span><span class="sxs-lookup"><span data-stu-id="96383-640">Power BI is not currently available as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="96383-641">第16章-在 HoloLens 上顯示 Power BI 資料</span><span class="sxs-lookup"><span data-stu-id="96383-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="96383-642">在您的 HoloLens 上，藉由在應用程式清單中的圖示上點擊，登入**Microsoft Store**。</span><span class="sxs-lookup"><span data-stu-id="96383-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="96383-644">搜尋，然後下載**Power BI**應用程式。</span><span class="sxs-lookup"><span data-stu-id="96383-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="96383-646">從您的應用程式清單啟動**Power BI** 。</span><span class="sxs-lookup"><span data-stu-id="96383-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="96383-647">**Power BI**可能會要求您登入您的**Microsoft 365 帳戶**。</span><span class="sxs-lookup"><span data-stu-id="96383-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="96383-648">在應用程式內，預設應該會顯示工作區，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="96383-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="96383-649">如果沒有發生這種情況，只要按一下視窗左側的工作區圖示即可。</span><span class="sxs-lookup"><span data-stu-id="96383-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="96383-651">您已完成 IoT 中樞應用程式</span><span class="sxs-lookup"><span data-stu-id="96383-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="96383-652">恭喜，您已成功建立具有模擬虛擬機器 Edge 裝置的 IoT 中樞服務。</span><span class="sxs-lookup"><span data-stu-id="96383-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="96383-653">您的裝置可以將機器學習模型的結果傳達給 Azure 資料表服務，這會被讀入 Power BI，並在 Microsoft HoloLens 中視覺化的 Azure 函數應用程式。</span><span class="sxs-lookup"><span data-stu-id="96383-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="96383-655">額外練習</span><span class="sxs-lookup"><span data-stu-id="96383-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="96383-656">練習1</span><span class="sxs-lookup"><span data-stu-id="96383-656">Exercise 1</span></span>

<span data-ttu-id="96383-657">展開儲存在資料表中的訊息結構，並將其顯示為圖表。</span><span class="sxs-lookup"><span data-stu-id="96383-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="96383-658">您可能想要收集更多資料，並將它儲存在相同的資料表中，以供稍後顯示。</span><span class="sxs-lookup"><span data-stu-id="96383-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="96383-659">練習2</span><span class="sxs-lookup"><span data-stu-id="96383-659">Exercise 2</span></span>

<span data-ttu-id="96383-660">建立要在 IoT 面板上部署的其他「相機捕捉」模組，使其可以透過相機進行分析來捕獲影像。</span><span class="sxs-lookup"><span data-stu-id="96383-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
