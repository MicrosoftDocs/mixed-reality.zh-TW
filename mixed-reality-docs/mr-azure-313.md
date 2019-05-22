---
title: MR 和 Azure 313-IoT 中樞服務
description: 完成這個課程來了解如何實作在執行 Ubuntu 16.4 的虛擬機器上的 Azure IoT 中樞服務，並使用 Microsoft HoloLens 或沈浸式的 (VR) 耳機的訊息資料以視覺化方式檢視。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure、 混合實境、 academy、 edge、 iot edge、 教學課程、 api、 通知、 函數、 資料表、 沈浸式 hololens、 vr、 iot、 虛擬機器、 ubuntu、 python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591132"
---
>[!NOTE]
><span data-ttu-id="386eb-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="386eb-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="386eb-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="386eb-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="386eb-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="386eb-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="386eb-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="386eb-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="386eb-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="386eb-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="386eb-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="386eb-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="386eb-110">MR 和 Azure 313:IoT 中樞服務</span><span class="sxs-lookup"><span data-stu-id="386eb-110">MR and Azure 313: IoT Hub Service</span></span>

![課程結果](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="386eb-112">在此課程中，您將了解如何實作**Azure IoT 中樞服務**的虛擬機器上執行 Ubuntu 16.4 的作業系統。</span><span class="sxs-lookup"><span data-stu-id="386eb-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="386eb-113">**Azure 函數應用程式**然後將用來從您的 Ubuntu VM，接收訊息，並內將結果儲存**Azure 表格服務**。</span><span class="sxs-lookup"><span data-stu-id="386eb-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="386eb-114">您接著可以檢視此資料使用**Power BI** Microsoft HoloLens 或沈浸式 (VR) 耳機。</span><span class="sxs-lookup"><span data-stu-id="386eb-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="386eb-115">本課程的內容*適用於*到 IoT Edge 裝置，但為了本課程中，則會著重於在虛擬機器環境中，如此便不需要實體的 Edge 裝置的存取。</span><span class="sxs-lookup"><span data-stu-id="386eb-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="386eb-116">藉由完成本課程，您將學習：</span><span class="sxs-lookup"><span data-stu-id="386eb-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="386eb-117">部署**IoT Edge 模組**至虛擬機器 (Ubuntu 16 OS)，即代表您的 IoT 裝置。</span><span class="sxs-lookup"><span data-stu-id="386eb-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="386eb-118">新增**Azure 自訂視覺 Tensorflow 模型**到 Edge 模組，將會分析儲存在容器映像的程式碼。</span><span class="sxs-lookup"><span data-stu-id="386eb-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="386eb-119">設定模組，將分析結果訊息傳送至您**IoT 中樞服務**。</span><span class="sxs-lookup"><span data-stu-id="386eb-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="386eb-120">使用**Azure 函數應用程式**來儲存訊息內**Azure 資料表**。</span><span class="sxs-lookup"><span data-stu-id="386eb-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="386eb-121">設定好**Power BI**收集預存的訊息，並建立報表。</span><span class="sxs-lookup"><span data-stu-id="386eb-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="386eb-122">以視覺化方式檢視您的 IoT 訊息資料內**Power BI**。</span><span class="sxs-lookup"><span data-stu-id="386eb-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="386eb-123">您將使用的服務包括：</span><span class="sxs-lookup"><span data-stu-id="386eb-123">The Services you will use include:</span></span>

- <span data-ttu-id="386eb-124">**Azure IoT 中樞**是 Microsoft Azure 服務可讓開發人員連接、 監視及管理 IoT 資產。</span><span class="sxs-lookup"><span data-stu-id="386eb-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="386eb-125">如需詳細資訊，請瀏覽[ **Azure IoT 中樞服務**頁面](https://azure.microsoft.com/en-au/services/iot-hub/)。</span><span class="sxs-lookup"><span data-stu-id="386eb-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="386eb-126">**Azure Container Registry**是讓開發人員能夠儲存各種類型的容器的容器映像，Microsoft Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="386eb-127">如需詳細資訊，請瀏覽[ **Azure 容器登錄服務**頁面](https://azure.microsoft.com/en-au/services/container-registry/)。</span><span class="sxs-lookup"><span data-stu-id="386eb-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="386eb-128">**Azure 函式應用程式**是為 Microsoft Azure 服務，可讓開發人員執行程式碼片段，'函式'，在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="386eb-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="386eb-129">這可用來將工作委派給雲端，而不是您本機的應用程式，可以有許多優點。</span><span class="sxs-lookup"><span data-stu-id="386eb-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="386eb-130">**Azure Functions**支援數種開發語言，包括 C\#，F\#、 Node.js、 Java 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="386eb-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="386eb-131">如需詳細資訊，請瀏覽[ **Azure Functions**頁面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="386eb-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="386eb-132">**Azure 儲存體：資料表**是 Microsoft Azure 服務，可讓開發人員儲存結構化，非 SQL、 在雲端中的資料進行更容易存取任何位置。</span><span class="sxs-lookup"><span data-stu-id="386eb-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="386eb-133">服務擁有許多的無結構描述設計中，如有需要讓資料表的進化的因此非常大的彈性。</span><span class="sxs-lookup"><span data-stu-id="386eb-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="386eb-134">如需詳細資訊，請瀏覽[ **Azure 資料表**頁面](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="386eb-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="386eb-135">本課程將教導您如何設定並使用 IoT 中樞服務，然後以視覺化方式檢視裝置所提供的回應。</span><span class="sxs-lookup"><span data-stu-id="386eb-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="386eb-136">它會決定要自訂的 IoT 中樞服務安裝程式，故您可能建置運用這些概念。</span><span class="sxs-lookup"><span data-stu-id="386eb-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="386eb-137">裝置支援</span><span class="sxs-lookup"><span data-stu-id="386eb-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="386eb-138">課程</span><span class="sxs-lookup"><span data-stu-id="386eb-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="386eb-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="386eb-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="386eb-140"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="386eb-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="386eb-141">MR 和 Azure 313:IoT 中樞服務</span><span class="sxs-lookup"><span data-stu-id="386eb-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="386eb-142">✔️</span><span class="sxs-lookup"><span data-stu-id="386eb-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="386eb-143">✔️</span><span class="sxs-lookup"><span data-stu-id="386eb-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="386eb-144">必要條件</span><span class="sxs-lookup"><span data-stu-id="386eb-144">Prerequisites</span></span>

<span data-ttu-id="386eb-145">如與混合實境，包括 Microsoft HoloLens，開發最新的必要條件，請造訪[安裝工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)文章。</span><span class="sxs-lookup"><span data-stu-id="386eb-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="386eb-146">本教學課程專為開發人員使用 Python 的基本經驗。</span><span class="sxs-lookup"><span data-stu-id="386eb-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="386eb-147">請同時了解必要條件和書面的指示此文件中代表什麼已經過測試，並在寫入 (第 2018 年 7 月) 的時間驗證。</span><span class="sxs-lookup"><span data-stu-id="386eb-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="386eb-148">中所示，您可以自由使用最新的軟體[安裝工具](install-the-tools.md)發行項，但它不應該假設，本課程中的資訊將會完全符合您會發現在較新的軟體，與下面列出的。</span><span class="sxs-lookup"><span data-stu-id="386eb-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="386eb-149">下列的硬體和軟體是必要項目：</span><span class="sxs-lookup"><span data-stu-id="386eb-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="386eb-150">Windows 10 Fall Creators Update （或更新版本），**啟用開發人員模式**</span><span class="sxs-lookup"><span data-stu-id="386eb-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="386eb-151">您無法執行使用只有 Windows 10 Home Edition 上的 HYPER-V 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="386eb-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="386eb-152">Windows 10 SDK （最新版）</span><span class="sxs-lookup"><span data-stu-id="386eb-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="386eb-153">HoloLens，a**啟用開發人員模式**</span><span class="sxs-lookup"><span data-stu-id="386eb-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="386eb-154">Visual Studio 2017.15.4 （僅用來存取 Azure 的雲端總管）</span><span class="sxs-lookup"><span data-stu-id="386eb-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="386eb-155">Azure 和 IoT 中樞服務的網際網路存取。</span><span class="sxs-lookup"><span data-stu-id="386eb-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="386eb-156">如需詳細資訊，請遵循此[連結至 IoT 中樞服務頁面](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="386eb-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="386eb-157">機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="386eb-157">A machine learning model.</span></span> <span data-ttu-id="386eb-158">如果您不需要您自己的已備妥，可使用模型時，[您可以使用本課程提供的模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)。</span><span class="sxs-lookup"><span data-stu-id="386eb-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="386eb-159">**HYPER-V**啟用 Windows 10 的開發電腦上的軟體。</span><span class="sxs-lookup"><span data-stu-id="386eb-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="386eb-160">在您的開發電腦或者執行執行 Ubuntu （16.4 或 18.4） 的虛擬機器可以使用不同的電腦執行 Linux (Ubuntu 16.4 或 18.4)。</span><span class="sxs-lookup"><span data-stu-id="386eb-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="386eb-161">您可以找到更多有關如何在 Windows 上建立的 VM 使用中的 HYPER-V [」 開始之前 > 一章](#before-you-start)。 (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="386eb-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="386eb-162">開始之前</span><span class="sxs-lookup"><span data-stu-id="386eb-162">Before you start</span></span>

1. <span data-ttu-id="386eb-163">設定並測試您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="386eb-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="386eb-164">如果您需要支援設定您的 HoloLens[請務必瀏覽 HoloLens 安裝文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="386eb-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="386eb-165">它是個不錯的主意，執行**校正**並**感應器調整**開始開發新的 HoloLens 應用程式 （有時候它可以幫助每位使用者執行這些工作） 時。</span><span class="sxs-lookup"><span data-stu-id="386eb-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="386eb-166">校正的說明，請遵循此[HoloLens 校正文章連結](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="386eb-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="386eb-167">如需微調感應器的說明，請遵循此[HoloLens 感應器調整的文章連結](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="386eb-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="386eb-168">設定您**Ubuntu 虛擬機器**使用**HYPER-V**。</span><span class="sxs-lookup"><span data-stu-id="386eb-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="386eb-169">下列資源將協助您進行程序。</span><span class="sxs-lookup"><span data-stu-id="386eb-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="386eb-170">首先，請遵循下列連結來[下載 Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/)。</span><span class="sxs-lookup"><span data-stu-id="386eb-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="386eb-171">選取  **64 位元電腦 (AMD64) 桌面映像**。</span><span class="sxs-lookup"><span data-stu-id="386eb-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="386eb-172">請確定**HYPER-V**啟用您的 Windows 10 電腦上。</span><span class="sxs-lookup"><span data-stu-id="386eb-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="386eb-173">您可以依照此連結以取得指導方針[安裝和啟用 Windows 10 上的 HYPER-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)。</span><span class="sxs-lookup"><span data-stu-id="386eb-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="386eb-174">啟動 HYPER-V 並建立新的 Ubuntu VM。</span><span class="sxs-lookup"><span data-stu-id="386eb-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="386eb-175">您可以遵循此連結[如何使用 HYPER-V 建立的 VM 上的逐步解說指南](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)。</span><span class="sxs-lookup"><span data-stu-id="386eb-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="386eb-176">若要要求時 **[從開機映像檔安裝作業系統]**，選取**Ubuntu ISO**您稍早有下載。</span><span class="sxs-lookup"><span data-stu-id="386eb-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="386eb-177">使用**HYPER-V 快速建立**不建議進行。</span><span class="sxs-lookup"><span data-stu-id="386eb-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="386eb-178">第 1 章-擷取自訂視覺模型</span><span class="sxs-lookup"><span data-stu-id="386eb-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="386eb-179">本課程中，您將可以存取[預先建置的自訂視覺模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)，偵測到鍵盤及滑鼠從映像。</span><span class="sxs-lookup"><span data-stu-id="386eb-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="386eb-180">如果您使用此功能，請繼續進行[第 2 章](#chapter-2---the-container-registry-service)。</span><span class="sxs-lookup"><span data-stu-id="386eb-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="386eb-181">不過，您可以遵循下列步驟，如果您想要使用您自己的自訂視覺模型：</span><span class="sxs-lookup"><span data-stu-id="386eb-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="386eb-182">在您**自訂視覺專案**前往**效能** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="386eb-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="386eb-183">您的模型必須使用*compact*網域，將模型匯出。</span><span class="sxs-lookup"><span data-stu-id="386eb-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="386eb-184">您可以變更您模型的網域設定中，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="386eb-184">You can change your models domain in the settings for your project.</span></span>

    ![效能 索引標籤](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="386eb-186">選取 **反覆項目**您想要匯出，然後按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="386eb-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="386eb-187">刀鋒視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="386eb-187">A blade will appear.</span></span>

    ![匯出刀鋒視窗](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="386eb-189">在刀鋒視窗中按一下**Docker 檔案**。</span><span class="sxs-lookup"><span data-stu-id="386eb-189">In the blade click **Docker File**.</span></span>

    ![選取 docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="386eb-191">按一下  **Linux**中的下拉式選單，然後按一下 **下載**。</span><span class="sxs-lookup"><span data-stu-id="386eb-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![按一下 [下載]](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="386eb-193">將解壓縮的內容。</span><span class="sxs-lookup"><span data-stu-id="386eb-193">Unzip the content.</span></span> <span data-ttu-id="386eb-194">您可以將在本課程後面。</span><span class="sxs-lookup"><span data-stu-id="386eb-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="386eb-195">第 2 章-容器登錄服務</span><span class="sxs-lookup"><span data-stu-id="386eb-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="386eb-196">**容器登錄服務**是用來裝載您的容器存放庫。</span><span class="sxs-lookup"><span data-stu-id="386eb-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="386eb-197">**IoT 中樞服務**您會用來建置，並使用在這個課程中，是指**容器登錄服務**取得要在您的 Edge 裝置中部署的容器。</span><span class="sxs-lookup"><span data-stu-id="386eb-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="386eb-198">首先，請依照這[Azure 入口網站連結](https://portal.azure.com/)，並使用您的認證登入。</span><span class="sxs-lookup"><span data-stu-id="386eb-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="386eb-199">移至**建立資源**並尋找**Container Registry**。</span><span class="sxs-lookup"><span data-stu-id="386eb-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![容器登錄](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="386eb-201">按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="386eb-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="386eb-202">設定服務安裝程式參數：</span><span class="sxs-lookup"><span data-stu-id="386eb-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="386eb-203">在此範例中插入的名稱，為您的專案，其名**IoTCRegistry**。</span><span class="sxs-lookup"><span data-stu-id="386eb-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="386eb-204">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="386eb-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="386eb-205">資源群組可用來監視、 控制存取權，佈建及管理的 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="386eb-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="386eb-206">建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。</span><span class="sxs-lookup"><span data-stu-id="386eb-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="386eb-207">設定服務的位置。</span><span class="sxs-lookup"><span data-stu-id="386eb-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="386eb-208">設定**系統管理員使用者**要**啟用**。</span><span class="sxs-lookup"><span data-stu-id="386eb-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="386eb-209">設定**SKU**要**基本**。</span><span class="sxs-lookup"><span data-stu-id="386eb-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="386eb-210">按一下 **建立**並等候建立的服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="386eb-211">當出現告知您成功建立通知*Container Registry*，按一下**移至資源**重新導向至您的服務頁面。</span><span class="sxs-lookup"><span data-stu-id="386eb-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="386eb-212">在  *Container Registry*服務頁面上，按一下**存取金鑰**。</span><span class="sxs-lookup"><span data-stu-id="386eb-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="386eb-213">記下 （您可以使用您在 [記事本]） 的下列參數：</span><span class="sxs-lookup"><span data-stu-id="386eb-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="386eb-214">**Login Server**</span><span class="sxs-lookup"><span data-stu-id="386eb-214">**Login Server**</span></span>
    2. <span data-ttu-id="386eb-215">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="386eb-215">**Username**</span></span>
    3. <span data-ttu-id="386eb-216">**密碼**</span><span class="sxs-lookup"><span data-stu-id="386eb-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="386eb-217">第 3 章-IoT 中樞服務</span><span class="sxs-lookup"><span data-stu-id="386eb-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="386eb-218">現在您將開始建立及安裝您**IoT 中樞服務**。</span><span class="sxs-lookup"><span data-stu-id="386eb-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="386eb-219">如果您尚未登入，登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="386eb-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="386eb-220">登入之後，按一下**建立資源**在左上角，，然後搜尋**IoT 中樞**，然後按一下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="386eb-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![搜尋儲存體帳戶](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="386eb-222">新的頁面將提供的描述**儲存體帳戶**服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="386eb-223">在此提示的左下方，按一下**建立**按鈕，以建立這個執行個體服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="386eb-225">一旦您按下**建立**，面板會顯示：</span><span class="sxs-lookup"><span data-stu-id="386eb-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="386eb-226">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="386eb-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="386eb-227">資源群組可用來監視、 控制存取權，佈建及管理 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="386eb-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="386eb-228">建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。</span><span class="sxs-lookup"><span data-stu-id="386eb-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="386eb-229">如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="386eb-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="386eb-230">選取適當**位置**（您在本課程中建立的所有服務上使用相同的位置）。</span><span class="sxs-lookup"><span data-stu-id="386eb-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="386eb-231">插入您想要**名稱**此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="386eb-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="386eb-232">在頁面底部按一下**下一步:大小和縮放比例**。</span><span class="sxs-lookup"><span data-stu-id="386eb-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="386eb-234">在此頁面上，選取您**定價與級別層**（如果這是您第一個 IoT 中樞服務執行個體，免費層應該是您可以使用）。</span><span class="sxs-lookup"><span data-stu-id="386eb-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="386eb-235">按一下 **檢閱 + 建立**。</span><span class="sxs-lookup"><span data-stu-id="386eb-235">Click on **Review + Create**.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="386eb-237">檢閱您的設定，然後按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="386eb-237">Review your settings and click on **Create**.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="386eb-239">當出現告知您成功建立通知*IoT 中樞*服務，按一下**移至資源**重新導向至您的服務頁面。</span><span class="sxs-lookup"><span data-stu-id="386eb-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="386eb-241">捲動左側的側邊面板，直到您看到*自動的裝置管理*，按一下**IoT Edge**。</span><span class="sxs-lookup"><span data-stu-id="386eb-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="386eb-243">在顯示於右側視窗中，按一下**加入 IoT Edge 裝置**。</span><span class="sxs-lookup"><span data-stu-id="386eb-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="386eb-244">刀鋒視窗會出現在右邊。</span><span class="sxs-lookup"><span data-stu-id="386eb-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="386eb-245">在刀鋒視窗中，提供您新的裝置**裝置識別碼**（您所選擇的名稱）。</span><span class="sxs-lookup"><span data-stu-id="386eb-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="386eb-246">然後，按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="386eb-246">Then, click **Save**.</span></span> <span data-ttu-id="386eb-247">*主要*並*次要金鑰*會自動產生，如果您有**自動產生**勾選。</span><span class="sxs-lookup"><span data-stu-id="386eb-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="386eb-249">您會瀏覽回到*IoT Edge 裝置*區段中，其中會列出您的新裝置。</span><span class="sxs-lookup"><span data-stu-id="386eb-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="386eb-250">按一下 新裝置上 (在紅色外框的下列映像)。</span><span class="sxs-lookup"><span data-stu-id="386eb-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![建立儲存體執行個體](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="386eb-252">在 *裝置詳細資料*頁面隨即出現，需要一份**連接字串**（主索引鍵）。</span><span class="sxs-lookup"><span data-stu-id="386eb-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="386eb-254">在左側面板請返回並按一下*共用存取原則*，以開啟它。</span><span class="sxs-lookup"><span data-stu-id="386eb-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="386eb-255">在出現的頁面上，按一下**iothubowner**，和刀鋒視窗會出現在螢幕的右邊。</span><span class="sxs-lookup"><span data-stu-id="386eb-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="386eb-256">請記下 （在您的 [記事本])**連接字串**（主索引鍵），供稍後使用設定時*連接字串*到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="386eb-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="386eb-258">第 4 章-設定開發環境</span><span class="sxs-lookup"><span data-stu-id="386eb-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="386eb-259">若要建立及部署適用於模組*IoT 中樞 Edge*，您將需要在執行 Windows 10 的開發電腦上安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="386eb-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="386eb-260">[適用於 Windows 的 docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)，它會要求您建立帳戶要能夠下載。</span><span class="sxs-lookup"><span data-stu-id="386eb-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="386eb-261">[![下載適用於 windows 的 docker](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="386eb-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="386eb-262">需要 docker *Windows 10 PRO*， *Enterprise 14393*，或*Windows Server 2016 RTM*，以執行。</span><span class="sxs-lookup"><span data-stu-id="386eb-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="386eb-263">如果您正在執行其他版本的 Windows 10，您可以嘗試使用 Docker 安裝[Docker 工具箱](https://docs.docker.com/toolbox/toolbox_install_windows/)。</span><span class="sxs-lookup"><span data-stu-id="386eb-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="386eb-264">[Python 3.6](https://www.python.org/downloads/)。</span><span class="sxs-lookup"><span data-stu-id="386eb-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="386eb-265">[![下載 python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="386eb-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="386eb-266">[Visual Studio Code (也稱為 VS Code)](https://code.visualstudio.com/download)。</span><span class="sxs-lookup"><span data-stu-id="386eb-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="386eb-267">[![下載 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="386eb-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="386eb-268">安裝上述軟體之後，您必須重新啟動您的電腦。</span><span class="sxs-lookup"><span data-stu-id="386eb-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="386eb-269">第 5 章-設定 Ubuntu 環境</span><span class="sxs-lookup"><span data-stu-id="386eb-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="386eb-270">現在您可以移至您的裝置設定**執行 Ubuntu OS**。</span><span class="sxs-lookup"><span data-stu-id="386eb-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="386eb-271">請遵循下列步驟來安裝必要的軟體，您將容器部署在您的面板：</span><span class="sxs-lookup"><span data-stu-id="386eb-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="386eb-272">您應該一律在完成將終端機命令**sudo**以系統管理員使用者身分執行。</span><span class="sxs-lookup"><span data-stu-id="386eb-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="386eb-273">也就是：</span><span class="sxs-lookup"><span data-stu-id="386eb-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="386eb-274">開啟**Ubuntu 終端機**，並使用下列命令來安裝**pip**:</span><span class="sxs-lookup"><span data-stu-id="386eb-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [!提示]<span data-ttu-id="386eb-275"> 您可以開啟\*終端機\*非常輕鬆地透過使用鍵盤快速鍵：*\*Ctrl + Alt + T*\*。</span><span class="sxs-lookup"><span data-stu-id="386eb-275"> You can open \*Terminal* very easily through using the keyboard shortcut: *\*Ctrl + Alt + T*\*.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="386eb-276">在本章中，您可能會提示您，由*終端機*、 權限使用裝置儲存空間，以及供您輸入**y/n** （是或否），型別 **'y'**，然後按下**Enter**金鑰，才能接受。</span><span class="sxs-lookup"><span data-stu-id="386eb-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="386eb-277">該命令完成之後，使用下列命令來安裝**curl**:</span><span class="sxs-lookup"><span data-stu-id="386eb-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="386eb-278">一次**pip**並**curl**會安裝，請使用下列命令來安裝**IoT Edge 執行階段**，這是為了部署，並控制在面板上的模組：</span><span class="sxs-lookup"><span data-stu-id="386eb-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

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

5. <span data-ttu-id="386eb-279">此時系統會提示您開啟*執行階段組態檔*，以插入**裝置連接字串**，記下 （您在記事本中），建立時**IoT 中樞服務** ([在步驟 14 中的第 3 章](#chapter-3---the-iot-hub-service))。</span><span class="sxs-lookup"><span data-stu-id="386eb-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="386eb-280">在終端機中開啟該檔案執行下面這一行：</span><span class="sxs-lookup"><span data-stu-id="386eb-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="386eb-281">**Config.yaml**檔案將會顯示以供您編輯：</span><span class="sxs-lookup"><span data-stu-id="386eb-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="386eb-282">當此檔案開啟時，可能有些令人混淆。</span><span class="sxs-lookup"><span data-stu-id="386eb-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="386eb-283">您必須編輯此檔案，內的文字*終端機*本身。</span><span class="sxs-lookup"><span data-stu-id="386eb-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="386eb-284">使用鍵盤上的方向鍵來捲動的清單 （您必須捲動一些方式），到行包含":</span><span class="sxs-lookup"><span data-stu-id="386eb-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="386eb-285">「**\<將裝置連接字串 &GT;**"。</span><span class="sxs-lookup"><span data-stu-id="386eb-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="386eb-286">替換成一行，**包括括號**，使用**Device Connection String**您稍早所。</span><span class="sxs-lookup"><span data-stu-id="386eb-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="386eb-287">您的連接字串中在鍵盤上的位置，然後按**CTRL-X**來儲存檔案的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="386eb-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="386eb-288">它會要求您輸入確認**Y**。然後按**Enter**金鑰，來確認。</span><span class="sxs-lookup"><span data-stu-id="386eb-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="386eb-289">您會回到一般*終端機*。</span><span class="sxs-lookup"><span data-stu-id="386eb-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="386eb-290">一旦所有成功地執行這些命令，您將安裝**IoT Edge 執行階段**。</span><span class="sxs-lookup"><span data-stu-id="386eb-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="386eb-291">初始化之後，執行階段會在其本身每次開啟裝置電源，啟動，並可以坐在背景中，從部署的模組正在等候**IoT 中樞服務**。</span><span class="sxs-lookup"><span data-stu-id="386eb-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="386eb-292">執行下列命令列來初始化*IoT Edge 執行階段*:</span><span class="sxs-lookup"><span data-stu-id="386eb-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="386eb-293">如果您變更.yaml 檔案或上述的安裝程式時，您必須再次執行上述的重新啟動程式碼內*終端機*。</span><span class="sxs-lookup"><span data-stu-id="386eb-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="386eb-294">請檢查*IoT Edge 執行階段*藉由執行下列命令列的狀態。</span><span class="sxs-lookup"><span data-stu-id="386eb-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="386eb-295">執行階段應該會出現狀態**作用中 （執行）** 綠色文字。</span><span class="sxs-lookup"><span data-stu-id="386eb-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="386eb-296">按下**Ctrl + C**索引鍵，結束 [狀態] 頁面。</span><span class="sxs-lookup"><span data-stu-id="386eb-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="386eb-297">您可以確認*IoT Edge 執行階段*提取容器正確輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="386eb-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="386eb-298">具有兩 （2） 容器的清單應該會出現。</span><span class="sxs-lookup"><span data-stu-id="386eb-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="386eb-299">這些是會自動建立 （edgeAgent 和 edgeHub） 時，IoT 中樞服務的預設模組。</span><span class="sxs-lookup"><span data-stu-id="386eb-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="386eb-300">一旦您建立及部署您自己的模組時，它們會出現在此清單中，預設的下方。</span><span class="sxs-lookup"><span data-stu-id="386eb-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="386eb-301">章節 6-安裝擴充功能</span><span class="sxs-lookup"><span data-stu-id="386eb-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="386eb-302">接下來的幾章 (6-9) 會在您的 Windows 10 電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="386eb-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="386eb-303">開啟**VS Code**。</span><span class="sxs-lookup"><span data-stu-id="386eb-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="386eb-304">按一下 [**延伸模組**（正方形）] 按鈕在左側列的 VS Code 中，以開啟**擴充功能面板**。</span><span class="sxs-lookup"><span data-stu-id="386eb-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="386eb-305">搜尋並安裝，下列延伸模組 （如圖所示）：</span><span class="sxs-lookup"><span data-stu-id="386eb-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="386eb-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="386eb-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="386eb-307">Azure IoT 工具組</span><span class="sxs-lookup"><span data-stu-id="386eb-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="386eb-308">Docker</span><span class="sxs-lookup"><span data-stu-id="386eb-308">Docker</span></span>   

    ![建立您的容器](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="386eb-310">一旦安裝擴充功能之後，請關閉並重新開啟 VS Code。</span><span class="sxs-lookup"><span data-stu-id="386eb-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="386eb-311">VS Code 開啟一次，然後瀏覽至**檢視 > 整合式終端機**。</span><span class="sxs-lookup"><span data-stu-id="386eb-311">With VS Code open once more, navigate to **View > Integrated terminal**.</span></span>

6. <span data-ttu-id="386eb-312">您現在將會安裝**Cookiecutter**。</span><span class="sxs-lookup"><span data-stu-id="386eb-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="386eb-313">在終端機中執行下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="386eb-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!提示]<span data-ttu-id="386eb-314"> 如果您無法使用此命令：</span><span class="sxs-lookup"><span data-stu-id="386eb-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="386eb-315">重新啟動 VS Code 中，和/或您的電腦。</span><span class="sxs-lookup"><span data-stu-id="386eb-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="386eb-316">可能需要切換**VS Code 終端機**至您已安裝 Python，也就是使用一個**Powershell** （尤其是如果您的電腦上已安裝的 Python 環境）。</span><span class="sxs-lookup"><span data-stu-id="386eb-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="386eb-317">終端機開啟之後，您會發現終端機右邊的下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="386eb-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="386eb-318">![建立您的容器](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="386eb-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="386eb-319">請確定**Python**安裝路徑新增為**環境變數**您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="386eb-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="386eb-320">Cookiecutter 應該是相同的位置路徑的一部分。</span><span class="sxs-lookup"><span data-stu-id="386eb-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="386eb-321">請遵循此[環境變數的詳細資訊的連結](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)，</span><span class="sxs-lookup"><span data-stu-id="386eb-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="386eb-322">一次**Cookiecutter**已完成安裝，您應該重新啟動您的電腦，以便**Cookiecutter**可辨識的命令，您的系統環境中。</span><span class="sxs-lookup"><span data-stu-id="386eb-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="386eb-323">第 7-建立您的容器解決方案</span><span class="sxs-lookup"><span data-stu-id="386eb-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="386eb-324">此時，您需要建立容器，要推入的模組，與*Container Registry*。</span><span class="sxs-lookup"><span data-stu-id="386eb-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="386eb-325">一旦您已推送您的容器，您將使用*IoT 中樞 Edge*將其部署到您的裝置，正在執行的服務*IoT Edge 執行階段*。</span><span class="sxs-lookup"><span data-stu-id="386eb-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="386eb-326">從 VS Code 中，按一下**檢視 > 命令選擇區**。</span><span class="sxs-lookup"><span data-stu-id="386eb-326">From VS Code, click **View > Command palette**.</span></span>

2. <span data-ttu-id="386eb-327">在 選擇區中，搜尋並執行**Azure IoT Edge:新的 Iot Edge 方案**。</span><span class="sxs-lookup"><span data-stu-id="386eb-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="386eb-328">瀏覽至您想要用來建立您的方案的位置。</span><span class="sxs-lookup"><span data-stu-id="386eb-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="386eb-329">按下**Enter**金鑰，才能接受位置。</span><span class="sxs-lookup"><span data-stu-id="386eb-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="386eb-330">為您的方案中的名稱。</span><span class="sxs-lookup"><span data-stu-id="386eb-330">Give a name to your solution.</span></span> <span data-ttu-id="386eb-331">按下**Enter**金鑰，來確認您提供的名稱。</span><span class="sxs-lookup"><span data-stu-id="386eb-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="386eb-332">現在系統會提示您選擇您的解決方案範本架構。</span><span class="sxs-lookup"><span data-stu-id="386eb-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="386eb-333">按一下  **Python 模組**。</span><span class="sxs-lookup"><span data-stu-id="386eb-333">Click **Python Module**.</span></span> <span data-ttu-id="386eb-334">按下**Enter**金鑰，來確認這項選擇。</span><span class="sxs-lookup"><span data-stu-id="386eb-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="386eb-335">為您的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="386eb-335">Give a name to your module.</span></span> <span data-ttu-id="386eb-336">按下**Enter**金鑰，來確認您的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="386eb-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="386eb-337">請務必記下 （與您的 「 記事本 」） 的模組名稱，以便稍後使用。</span><span class="sxs-lookup"><span data-stu-id="386eb-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="386eb-338">您會發現預先建置*Docker 映像儲存機制*調色盤上，即可顯示位址。</span><span class="sxs-lookup"><span data-stu-id="386eb-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="386eb-339">它看起來像：</span><span class="sxs-lookup"><span data-stu-id="386eb-339">It will look like:</span></span>

    <span data-ttu-id="386eb-340">**localhost:5000 /-NAME 您模組-**。</span><span class="sxs-lookup"><span data-stu-id="386eb-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="386eb-341">刪除**localhost:5000**，並在其位置插入*Container Registry* **登入伺服器**位址，您已記下建立時**容器登錄服務**([在步驟 8，第 2 章](#chapter-2---the-container-registry-service))。</span><span class="sxs-lookup"><span data-stu-id="386eb-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="386eb-342">按下**Enter**金鑰，才能確認該位址。</span><span class="sxs-lookup"><span data-stu-id="386eb-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="386eb-343">此時，會建立包含 Python 模組的範本的方案和其結構會顯示在**瀏覽 索引標籤**，VS Code 中，在畫面左側。</span><span class="sxs-lookup"><span data-stu-id="386eb-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="386eb-344">如果**瀏覽 索引標籤**是未開啟，您可以開啟它依序按一下左側列中的最上層的按鈕。</span><span class="sxs-lookup"><span data-stu-id="386eb-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![建立您的容器](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="386eb-346">本章中，最後一個步驟是按一下並開啟 **.env 檔案**，從**瀏覽 索引標籤**，並新增您*Container Registry* **的使用者名稱**並**密碼**。</span><span class="sxs-lookup"><span data-stu-id="386eb-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="386eb-347">Git 會忽略此檔案，但於建置容器，將設定認證以存取**容器登錄服務**。</span><span class="sxs-lookup"><span data-stu-id="386eb-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![建立您的容器](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="386eb-349">第 8 章-編輯您的容器解決方案</span><span class="sxs-lookup"><span data-stu-id="386eb-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="386eb-350">您現在將完成容器解決方案，藉由更新下列檔案：</span><span class="sxs-lookup"><span data-stu-id="386eb-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="386eb-351">*主<span></span>.py* python 指令碼。</span><span class="sxs-lookup"><span data-stu-id="386eb-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="386eb-352">*requirements.txt*。</span><span class="sxs-lookup"><span data-stu-id="386eb-352">*requirements.txt*.</span></span>
- <span data-ttu-id="386eb-353">*deployment.template.json*。</span><span class="sxs-lookup"><span data-stu-id="386eb-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="386eb-354">*Dockerfile.amd64*</span><span class="sxs-lookup"><span data-stu-id="386eb-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="386eb-355">您接著會建立*映像*資料夾中，python 指令碼來檢查要比對的映像您*自訂視覺模型*。</span><span class="sxs-lookup"><span data-stu-id="386eb-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="386eb-356">最後，您將在其中加入*labels.txt*檔案，以協助讀取您的模型，而*model.pb*檔案，這是您的模型。</span><span class="sxs-lookup"><span data-stu-id="386eb-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="386eb-357">使用 VS Code 開啟、 瀏覽至您的模組資料夾，並尋找呼叫的指令碼**主要<span></span>.py**。</span><span class="sxs-lookup"><span data-stu-id="386eb-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="386eb-358">按兩下以開啟它。</span><span class="sxs-lookup"><span data-stu-id="386eb-358">Double-click to open it.</span></span>

2. <span data-ttu-id="386eb-359">刪除之檔案的內容，並插入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="386eb-359">Delete the content of the file and insert the following code:</span></span>

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

3.  <span data-ttu-id="386eb-360">開啟檔案**requirements.txt**，並以其取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="386eb-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="386eb-361">開啟檔案**deployment.template.json**，並以取代其內容的下列指導方針如下：</span><span class="sxs-lookup"><span data-stu-id="386eb-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="386eb-362">因為您會有自己唯一的的 JSON 結構，您必須手動編輯 （而非複製範例）。</span><span class="sxs-lookup"><span data-stu-id="386eb-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="386eb-363">若要方便使用，請使用下列映像做為指南。</span><span class="sxs-lookup"><span data-stu-id="386eb-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="386eb-364">看起來與您，不同的區域，但您**不應該變更為 反白顯示的黃色**。</span><span class="sxs-lookup"><span data-stu-id="386eb-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="386eb-365">**若要刪除，您需要的各節會反白顯示的紅色。**</span><span class="sxs-lookup"><span data-stu-id="386eb-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="386eb-366">請務必刪除正確的括號，並移除逗號。</span><span class="sxs-lookup"><span data-stu-id="386eb-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![建立您的容器](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="386eb-368">已完成的 JSON 看起來如下圖所示 (不過，使用唯一的差異：*名稱的使用者名稱/密碼/模組/模組參考*):</span><span class="sxs-lookup"><span data-stu-id="386eb-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![建立您的容器](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="386eb-370">開啟檔案**Dockerfile.amd64**，並以其取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="386eb-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

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

6.  <span data-ttu-id="386eb-371">以滑鼠右鍵按一下下方的資料夾**模組**(會有您在先前; 所提供的名稱在範例中進一步向下，它會呼叫*pythonmodule*)，然後按一下 **新資料夾**.</span><span class="sxs-lookup"><span data-stu-id="386eb-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="386eb-372">將資料夾命名**映像**。</span><span class="sxs-lookup"><span data-stu-id="386eb-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="386eb-373">在資料夾中，新增一些映像包含滑鼠或鍵盤。</span><span class="sxs-lookup"><span data-stu-id="386eb-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="386eb-374">這些是將 Tensorflow 模型所分析的映像。</span><span class="sxs-lookup"><span data-stu-id="386eb-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="386eb-375">如果您使用您自己的模型，您必須變更以反映您自己的模型資料。</span><span class="sxs-lookup"><span data-stu-id="386eb-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="386eb-376">您現在需要擷取**labels.txt**並**model.pb**從 [模型] 資料夾，您先前下載的檔案 (或從您自己建立**Custom Vision Service**)，在[第 1 章](#chapter-1---retrieve-the-custom-vision-model)。</span><span class="sxs-lookup"><span data-stu-id="386eb-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="386eb-377">檔案之後，請將它們放在您的解決方案，以及其他檔案。</span><span class="sxs-lookup"><span data-stu-id="386eb-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="386eb-378">最後的結果看起來應該類似下面的影像：</span><span class="sxs-lookup"><span data-stu-id="386eb-378">The final result should look like the image below:</span></span>

    ![建立您的容器](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="386eb-380">第 9 章-封裝做為容器解決方案</span><span class="sxs-lookup"><span data-stu-id="386eb-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="386eb-381">您現在已準備好將檔案 「 套件 」 做為容器並將資料推送至您**Azure Container Registry**。</span><span class="sxs-lookup"><span data-stu-id="386eb-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="386eb-382">在 VS Code 中，開啟*整合式終端機*(**檢視 > 整合式終端機 / CTRL + '**)，並使用下列這一行加入登入**Docker** (替代值命令的認證與您**Azure Container Registry (ACR)**):</span><span class="sxs-lookup"><span data-stu-id="386eb-382">Within VS Code, open the *Integrated Terminal* (**View > Integrated Terminal / CTRL + \`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="386eb-383">檔案上按一下滑鼠右鍵**deployment.template.json**，然後按一下**建置 IoT Edge 方案**。</span><span class="sxs-lookup"><span data-stu-id="386eb-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="386eb-384">此建置程序需要一段時間 （取決於您的裝置），因此請準備好等候。</span><span class="sxs-lookup"><span data-stu-id="386eb-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="386eb-385">建置程序完成之後， **deployment.json**檔案將已建立新資料夾，稱為內**config**。</span><span class="sxs-lookup"><span data-stu-id="386eb-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![建立部署](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="386eb-387">開啟**命令調色盤**再次強調，並搜尋**Azure:登入**。</span><span class="sxs-lookup"><span data-stu-id="386eb-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="386eb-388">遵循提示使用您的 Azure 帳戶認證;VS Code 會為您提供的選項*複製並開啟*，這將會複製您很快就會需要並開啟預設網頁瀏覽器的裝置程式碼。</span><span class="sxs-lookup"><span data-stu-id="386eb-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="386eb-389">當系統詢問，貼上的裝置程式碼，來驗證您的電腦。</span><span class="sxs-lookup"><span data-stu-id="386eb-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![複製並開啟](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="386eb-391">一次簽署在您會注意到，在下方*瀏覽* 面板中，呼叫的新區段**Azure IoT 中樞裝置**。</span><span class="sxs-lookup"><span data-stu-id="386eb-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="386eb-392">按一下以展開此區段。</span><span class="sxs-lookup"><span data-stu-id="386eb-392">Click this section to expand it.</span></span>

    ![邊緣裝置](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="386eb-394">如果您的裝置是不在這裡，您必須以滑鼠右鍵按一下*Azure IoT Hub Devices*，然後按一下**設定 IoT 中樞連接字串**。</span><span class="sxs-lookup"><span data-stu-id="386eb-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="386eb-395">然後您會看到所**命令調色盤**（在 VS Code 的頂端），將會提示您輸入您*連接字串*。</span><span class="sxs-lookup"><span data-stu-id="386eb-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="386eb-396">這是*連接字串*您記下的結尾[第 3 章](#chapter-3---the-iot-hub-service)。</span><span class="sxs-lookup"><span data-stu-id="386eb-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="386eb-397">按下**Enter**金鑰，當您複製中的字串。</span><span class="sxs-lookup"><span data-stu-id="386eb-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="386eb-398">您的裝置應該載入，而且會出現。</span><span class="sxs-lookup"><span data-stu-id="386eb-398">Your device should load, and appear.</span></span> <span data-ttu-id="386eb-399">裝置名稱上按一下滑鼠右鍵，然後按一下 **的單一裝置的 建立部署**。</span><span class="sxs-lookup"><span data-stu-id="386eb-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![建立部署](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="386eb-401">您會收到*檔案總管*提示字元中，您可以瀏覽至**config**資料夾，然後再選取**deployment.json**檔案。</span><span class="sxs-lookup"><span data-stu-id="386eb-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="386eb-402">選取該檔案中，按一下**選取 [Edge 部署資訊清單**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="386eb-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![建立部署](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="386eb-404">現在您已提供您**IoT 中樞服務**與資訊清單，才能部署為模組，您的容器，從您**Azure Container Registry**，以有效地將它部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="386eb-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="386eb-405">若要檢視從您的裝置傳送到 IoT 中樞的訊息，再按一下滑鼠右鍵在您的裝置名稱，在**Azure IoT 中樞裝置**區段中**總管**] 面板，然後按一下 [**開始監視D2C 訊息**。</span><span class="sxs-lookup"><span data-stu-id="386eb-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="386eb-406">從您的裝置所傳送的訊息應該會出現在 VS 終端機中。</span><span class="sxs-lookup"><span data-stu-id="386eb-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="386eb-407">請耐心等候，因為這可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="386eb-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="386eb-408">請參閱下一章中的偵錯，以及檢查部署是否成功。</span><span class="sxs-lookup"><span data-stu-id="386eb-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="386eb-409">此模組中的映像之間會現在逐一查看**映像**資料夾和分析系統，與每個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="386eb-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="386eb-410">這是明顯只是示範如何取得基本的機器學習服務模型在 IoT Edge 裝置環境中工作。</span><span class="sxs-lookup"><span data-stu-id="386eb-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="386eb-411">若要擴充此範例的功能，您可以繼續透過數種方式。</span><span class="sxs-lookup"><span data-stu-id="386eb-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="386eb-412">一種方法可以包括一些程式碼在容器中，會擷取從網路攝影機，連線到裝置，並將影像儲存映像資料夾中的相片。</span><span class="sxs-lookup"><span data-stu-id="386eb-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="386eb-413">另一種方式可能複製映像從 IoT 裝置加入至容器。</span><span class="sxs-lookup"><span data-stu-id="386eb-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="386eb-414">實用的方法是在 IoT 裝置 （如果您想要自動化程序，或許是小型的應用程式無法執行作業） 的終端機中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="386eb-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="386eb-415">您可以從您的檔案儲存所在的資料夾位置以手動方式執行來測試此命令：</span><span class="sxs-lookup"><span data-stu-id="386eb-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="386eb-416">第 10 章-偵錯 IoT Edge 執行階段</span><span class="sxs-lookup"><span data-stu-id="386eb-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="386eb-417">以下是命令列和秘訣，可協助您監視和偵錯的傳訊活動的清單*IoT Edge 執行階段*，從您**Ubuntu 裝置**。</span><span class="sxs-lookup"><span data-stu-id="386eb-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="386eb-418">請檢查*IoT Edge 執行階段*藉由執行下列命令列的狀態：</span><span class="sxs-lookup"><span data-stu-id="386eb-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="386eb-419">按下時，請記得**Ctrl + C**，以完成檢視狀態。</span><span class="sxs-lookup"><span data-stu-id="386eb-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="386eb-420">列出目前已部署的容器。</span><span class="sxs-lookup"><span data-stu-id="386eb-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="386eb-421">如果*IoT 中樞服務*有容器成功部署，則會顯示藉由執行下列命令列：</span><span class="sxs-lookup"><span data-stu-id="386eb-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="386eb-422">或</span><span class="sxs-lookup"><span data-stu-id="386eb-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="386eb-423">以上是檢查是否您的模組是否已成功部署，就會出現在清單中的好方法否則，您將**僅**請參閱*edgeHub*並*edgeAgent*。</span><span class="sxs-lookup"><span data-stu-id="386eb-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="386eb-424">若要顯示容器的程式碼記錄檔，請執行下列命令列：</span><span class="sxs-lookup"><span data-stu-id="386eb-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="386eb-425">**用來管理 IoT Edge 執行階段的有用命令：**</span><span class="sxs-lookup"><span data-stu-id="386eb-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="386eb-426">若要刪除主應用程式中的所有容器：</span><span class="sxs-lookup"><span data-stu-id="386eb-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="386eb-427">若要停止*IoT Edge 執行階段*:</span><span class="sxs-lookup"><span data-stu-id="386eb-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="386eb-428">第 11-建立表格服務</span><span class="sxs-lookup"><span data-stu-id="386eb-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="386eb-429">瀏覽回到 Azure 入口網站，您將在其中建立儲存體資源建立 Azure 資料表服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="386eb-430">如果您尚未登入，登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="386eb-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="386eb-431">登入之後，按一下**建立資源**，在左上角，並搜尋**儲存體帳戶**，然後按**Enter**金鑰，才能開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="386eb-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="386eb-432">之後它會顯示，按一下 **儲存體帳戶-blob、 檔案、 資料表、 佇列**從清單中。</span><span class="sxs-lookup"><span data-stu-id="386eb-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![搜尋儲存體帳戶](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="386eb-434">新的頁面將提供的描述**儲存體帳戶**服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="386eb-435">在此提示的左下方，按一下**建立**按鈕，以建立這個執行個體服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![建立儲存體執行個體](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="386eb-437">一旦您按下**建立**，面板會顯示：</span><span class="sxs-lookup"><span data-stu-id="386eb-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="386eb-438">插入您想要**名稱**此服務執行個體 (*必須全部小寫*)。</span><span class="sxs-lookup"><span data-stu-id="386eb-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="386eb-439">針對**部署模型**，按一下**Resource manager**。</span><span class="sxs-lookup"><span data-stu-id="386eb-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="386eb-440">針對**帳戶種類**，使用下拉式功能表中，按一下**儲存體 (一般用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="386eb-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="386eb-441">按一下適當**位置**。</span><span class="sxs-lookup"><span data-stu-id="386eb-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="386eb-442">針對**複寫**下拉式功能表中，按一下**讀取-存取-異地備援儲存體 (RA-GRS)**。</span><span class="sxs-lookup"><span data-stu-id="386eb-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="386eb-443">針對**效能**，按一下**標準**。</span><span class="sxs-lookup"><span data-stu-id="386eb-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="386eb-444">內**需要安全傳輸**區段中，按一下**停用**。</span><span class="sxs-lookup"><span data-stu-id="386eb-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="386eb-445">從**訂用帳戶**下拉式功能表中，按一下適當的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="386eb-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="386eb-446">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="386eb-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="386eb-447">資源群組可用來監視、 控制存取權，佈建及管理的 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="386eb-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="386eb-448">建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。</span><span class="sxs-lookup"><span data-stu-id="386eb-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="386eb-449">如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="386eb-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="386eb-450">離開**虛擬網路**作為**停用**，如果這是您的選項。</span><span class="sxs-lookup"><span data-stu-id="386eb-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="386eb-451">按一下 [建立] 。</span><span class="sxs-lookup"><span data-stu-id="386eb-451">Click **Create**.</span></span>

        ![填入儲存體詳細資料](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="386eb-453">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="386eb-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="386eb-454">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="386eb-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="386eb-455">按一下通知，以探索新的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="386eb-455">Click on the notifications to explore your new Service instance.</span></span>

    ![新的儲存體通知](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="386eb-457">按一下 [**移至資源**按鈕，在該通知上方，而且您將會進入您新的儲存體服務執行個體概觀] 頁面。</span><span class="sxs-lookup"><span data-stu-id="386eb-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![前往資源](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="386eb-459">從 [概觀] 頁面的右手邊的側邊，按一下**資料表**。</span><span class="sxs-lookup"><span data-stu-id="386eb-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![資料表](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="386eb-461">在右側面板會變更以顯示**表格服務**資訊，您要在其中加入新的資料表。</span><span class="sxs-lookup"><span data-stu-id="386eb-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="386eb-462">依序按一下 **+ 資料表**左上角的按鈕。</span><span class="sxs-lookup"><span data-stu-id="386eb-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![開啟資料表](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="386eb-464">新的頁面將會顯示，您要在其中輸入**資料表名稱**。</span><span class="sxs-lookup"><span data-stu-id="386eb-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="386eb-465">這是您用來在您的應用程式，在後續的章節 （建立函數應用程式和 Power BI） 中的資料所參考的名稱。</span><span class="sxs-lookup"><span data-stu-id="386eb-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="386eb-466">插入**IoTMessages**做為名稱 （您也可以選擇自己的圖片，只要記住它稍後在本文件中使用時），按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="386eb-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="386eb-467">一旦建立新的資料表，您將能夠看到它內**表格服務**頁面 （位於底部）。</span><span class="sxs-lookup"><span data-stu-id="386eb-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![建立新資料表](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="386eb-469">現在，按一下**存取金鑰**並採取一份**儲存體帳戶名稱**並**金鑰**（使用您在 [記事本]），您將使用這些值稍後在本課程中，建立時**Azure 函數應用程式**。</span><span class="sxs-lookup"><span data-stu-id="386eb-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![建立新資料表](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="386eb-471">同樣地，使用左邊的面板捲動到 *表格服務*區段，然後按一下**資料表**(或**瀏覽資料表**，在較新的入口網站中)，並採取一份**資料表 URL** （使用您在 記事本）。</span><span class="sxs-lookup"><span data-stu-id="386eb-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="386eb-472">連結資料表時，您會稍後在本課程中，使用此值您**Power BI**應用程式。</span><span class="sxs-lookup"><span data-stu-id="386eb-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![建立新資料表](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="386eb-474">第 12 章-完成 Azure 資料表</span><span class="sxs-lookup"><span data-stu-id="386eb-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="386eb-475">既然您**表格服務**儲存體帳戶是否已設定，就可以開始將資料加入至它，將會用來儲存和擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="386eb-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="386eb-476">編輯您的資料表可透過**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="386eb-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="386eb-477">開啟**Visual Studio** (**不**Visual Studio Code)。</span><span class="sxs-lookup"><span data-stu-id="386eb-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="386eb-478">從功能表中，按一下**檢視 > Cloud Explorer**。</span><span class="sxs-lookup"><span data-stu-id="386eb-478">From the menu, click **View > Cloud Explorer**.</span></span>

    ![開啟 cloud explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="386eb-480">**Cloud Explorer**會開啟為停駐項目 （耐心等候，因為載入可能會花費的時間）。</span><span class="sxs-lookup"><span data-stu-id="386eb-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="386eb-481">如果您用來建立訂用帳戶您*儲存體帳戶*不可見，請確定您已：</span><span class="sxs-lookup"><span data-stu-id="386eb-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="386eb-482">與您在 Azure 入口網站使用相同的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="386eb-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="386eb-483">從 （您可能需要從您的帳戶設定套用篩選） 的 [帳戶管理] 頁面中選取您的訂用帳戶：</span><span class="sxs-lookup"><span data-stu-id="386eb-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![尋找訂用帳戶](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="386eb-485">Azure 雲端服務將會顯示。</span><span class="sxs-lookup"><span data-stu-id="386eb-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="386eb-486">尋找**儲存體帳戶**按一下箭號左側，展開您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="386eb-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![開啟儲存體帳戶](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="386eb-488">一旦展開時，您新建立**儲存體帳戶**應該可用。</span><span class="sxs-lookup"><span data-stu-id="386eb-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="386eb-489">按一下您的儲存體中，左邊的箭號之後，會展開，然後尋找**資料表**，按一下，以顯示旁的箭號**資料表**在最後一章中所建立。</span><span class="sxs-lookup"><span data-stu-id="386eb-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="386eb-490">按兩下您**資料表**。</span><span class="sxs-lookup"><span data-stu-id="386eb-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="386eb-491">您的資料表將會開啟您的 Visual Studio 視窗中央。</span><span class="sxs-lookup"><span data-stu-id="386eb-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="386eb-492">按一下 [資料表] 圖示，以 **+** （加上） 在其上。</span><span class="sxs-lookup"><span data-stu-id="386eb-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![加入新的資料表](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="386eb-494">接著會出現視窗提示要*新增實體*。</span><span class="sxs-lookup"><span data-stu-id="386eb-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="386eb-495">雖然會有三個屬性，您將建立一個的實體。</span><span class="sxs-lookup"><span data-stu-id="386eb-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="386eb-496">您將會發現*PartitionKey*並*RowKey*已提供，這些資料表所用來尋找您的資料。</span><span class="sxs-lookup"><span data-stu-id="386eb-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![資料分割和資料列索引鍵](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="386eb-498">更新下列值：</span><span class="sxs-lookup"><span data-stu-id="386eb-498">Update the following values:</span></span>

    - <span data-ttu-id="386eb-499">名稱：**PartitionKey**，值：**PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="386eb-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="386eb-500">名稱：**RowKey**，值：**RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="386eb-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="386eb-501">然後，按一下 **將屬性加入**(至左下方的*加入實體*視窗)，並新增下列屬性：</span><span class="sxs-lookup"><span data-stu-id="386eb-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="386eb-502">**MessageContent**，作為*字串*，將值保留為空白。</span><span class="sxs-lookup"><span data-stu-id="386eb-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="386eb-503">您的資料表應符合下面的影像中的一個：</span><span class="sxs-lookup"><span data-stu-id="386eb-503">Your table should match the one in the image below:</span></span>

    ![加入正確的值](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="386eb-505">實體包含資料列索引鍵中的數字 1 的原因的原因是因為您可能想要新增更多的訊息，您想要實驗應該使用本課程。</span><span class="sxs-lookup"><span data-stu-id="386eb-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="386eb-506">按一下 **確定**完畢時。</span><span class="sxs-lookup"><span data-stu-id="386eb-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="386eb-507">現在準備好可供您的資料表。</span><span class="sxs-lookup"><span data-stu-id="386eb-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="386eb-508">第 13-建立 Azure 函式應用程式</span><span class="sxs-lookup"><span data-stu-id="386eb-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="386eb-509">就可以立即開始建立*Azure 函數應用程式*，則會藉由呼叫*IoT 中樞服務*儲存*IoT Edge*裝置中的訊息**資料表**服務，您在上一章中建立。</span><span class="sxs-lookup"><span data-stu-id="386eb-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="386eb-510">首先，您必須建立一個檔案，可讓您的 Azure 函式，將您所需的程式庫。</span><span class="sxs-lookup"><span data-stu-id="386eb-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="386eb-511">開啟**記事本**(按下*Windows 鍵*，和型別*記事本*)。</span><span class="sxs-lookup"><span data-stu-id="386eb-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![開啟 [記事本]](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="386eb-513">使用 「 記事本 」 開啟，在其中插入以下的 JSON 結構。</span><span class="sxs-lookup"><span data-stu-id="386eb-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="386eb-514">完成後，會將它儲存為您的桌面上**project.json**。</span><span class="sxs-lookup"><span data-stu-id="386eb-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="386eb-515">此檔案會定義您的函式會使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="386eb-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="386eb-516">如果您已使用 NuGet，它看起來會類似。</span><span class="sxs-lookup"><span data-stu-id="386eb-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="386eb-517">請務必確認名稱正確;請確定它並未**沒有.txt**副檔名。</span><span class="sxs-lookup"><span data-stu-id="386eb-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="386eb-518">如需參考，請參閱以下內容：</span><span class="sxs-lookup"><span data-stu-id="386eb-518">See below for reference:</span></span>
    >
    > ![儲存的 JSON](images/AzureLabs-Lab313-52.png)

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

3.  <span data-ttu-id="386eb-520">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="386eb-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="386eb-521">一旦您登入，按一下**建立資源**在左上角，，然後搜尋**函式應用程式**，然後按**Enter**来搜尋的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="386eb-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="386eb-522">按一下 *函式應用程式*從結果中，若要開啟新的面板。</span><span class="sxs-lookup"><span data-stu-id="386eb-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![搜尋函式應用程式](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="386eb-524">新的面板會提供的描述**函式應用程式**服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="386eb-525">在此面板的左下方，按一下**建立**按鈕，以建立與這個關聯服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![函式應用程式執行個體](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="386eb-527">一旦您按下**建立**，填入下列：</span><span class="sxs-lookup"><span data-stu-id="386eb-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="386eb-528">針對**應用程式名稱**，插入您想要的名稱，此服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="386eb-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="386eb-529">選取 **訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="386eb-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="386eb-530">選取定價層適合您，如果這是第一次建立**函式應用程式服務**，免費層應該是您可以使用。</span><span class="sxs-lookup"><span data-stu-id="386eb-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="386eb-531">選擇**資源群組**或建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="386eb-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="386eb-532">資源群組可用來監視、 控制存取權，佈建及管理的 Azure 資產的集合計費。</span><span class="sxs-lookup"><span data-stu-id="386eb-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="386eb-533">建議將所有 Azure 服務在一般的資源群組相關聯 （例如例如這些課程中） 的單一專案保留）。</span><span class="sxs-lookup"><span data-stu-id="386eb-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="386eb-534">如果您想要深入了解 Azure 資源群組，請遵循此[如何管理資源群組的連結](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="386eb-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="386eb-535">針對**OS**，按一下 Windows，因為這是預期的平台。</span><span class="sxs-lookup"><span data-stu-id="386eb-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="386eb-536">選取 **主控方案**(使用本教學課程**取用方案**。</span><span class="sxs-lookup"><span data-stu-id="386eb-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="386eb-537">選取 **位置**（上一個步驟中選擇您已建立的儲存體相同的位置）</span><span class="sxs-lookup"><span data-stu-id="386eb-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="386eb-538">針對**儲存體**一節**您必須選取您在上一個步驟中建立的儲存體服務**。</span><span class="sxs-lookup"><span data-stu-id="386eb-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="386eb-539">您不需要*Application Insights*在此應用程式，因此您將它保留**關閉**。</span><span class="sxs-lookup"><span data-stu-id="386eb-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="386eb-540">按一下 [建立] 。</span><span class="sxs-lookup"><span data-stu-id="386eb-540">Click **Create**.</span></span>

        ![建立新的執行個體](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="386eb-542">一旦您按下**建立**，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="386eb-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="386eb-543">通知會出現在入口網站中，一旦建立服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="386eb-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![新的通知](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="386eb-545">部署成功之後，按一下 通知 （完成）。</span><span class="sxs-lookup"><span data-stu-id="386eb-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="386eb-546">按一下 **移至資源**通知，以探索新的服務執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="386eb-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![前往資源](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="386eb-548">在新的面板的左側，按一下 **+** （加號） 旁的圖示*函式*，以建立新的函式。</span><span class="sxs-lookup"><span data-stu-id="386eb-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![新增新的函式](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="386eb-550">在中央窗格中，**函式**建立視窗會出現。</span><span class="sxs-lookup"><span data-stu-id="386eb-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="386eb-551">此外，向下捲動，然後按一下**自訂函式**。</span><span class="sxs-lookup"><span data-stu-id="386eb-551">Scroll down further, and click on **Custom function**.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="386eb-553">下一步 頁面上，直到您找到捲動**IoT 中樞 （事件中樞）**，然後按一下它。</span><span class="sxs-lookup"><span data-stu-id="386eb-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="386eb-555">在  **IoT 中樞 （事件中樞）** 刀鋒視窗中，將**語言**來**C#** ，然後按一下**新**。</span><span class="sxs-lookup"><span data-stu-id="386eb-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="386eb-557">在視窗中會出現，請確定**IoT 中樞**已選取和名稱*IoT 中樞*欄位對應的名稱取代您*IoT 中樞服務*您具有先前所建立 ([在步驟 8，第 3 章](#chapter-3---the-iot-hub-service))。</span><span class="sxs-lookup"><span data-stu-id="386eb-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="386eb-558">然後按一下**選取** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="386eb-558">Then click the **Select** button.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="386eb-560">回到**IoT 中樞 （事件中樞）** 刀鋒視窗中，按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="386eb-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="386eb-562">您將會重新導向至函式編輯器。</span><span class="sxs-lookup"><span data-stu-id="386eb-562">You will be redirected to the function editor.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="386eb-564">刪除所有程式碼，並將它取代為下列：</span><span class="sxs-lookup"><span data-stu-id="386eb-564">Delete all the code in it and replace it with the following:</span></span>

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

19. <span data-ttu-id="386eb-565">變更下列變數，讓它們對應至適當的值 (**表格**並**儲存體**的值，從[步驟 11 日及 13 日分別第 11 章](#chapter-11---create-table-service))，您會在中找到您**儲存體帳戶**:</span><span class="sxs-lookup"><span data-stu-id="386eb-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="386eb-566">**tableName**，名稱與您**表格**位於您**儲存體帳戶**。</span><span class="sxs-lookup"><span data-stu-id="386eb-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="386eb-567">**tableURL**，使用的 URL 您**表格**位於您**儲存體帳戶**。</span><span class="sxs-lookup"><span data-stu-id="386eb-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="386eb-568">**storageAccountName**，對應的名稱值的名稱與您**儲存體帳戶**名稱。</span><span class="sxs-lookup"><span data-stu-id="386eb-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="386eb-569">**storageAccountKey**，您已取得您先前建立的儲存體服務中的金鑰。</span><span class="sxs-lookup"><span data-stu-id="386eb-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="386eb-571">中位置的程式碼，請按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="386eb-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="386eb-572">接下來，按一下 **\<** （箭頭） 圖示，在頁面的右手邊。</span><span class="sxs-lookup"><span data-stu-id="386eb-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="386eb-574">從右邊的窗格中將投影片。</span><span class="sxs-lookup"><span data-stu-id="386eb-574">A panel will slide in from the right.</span></span> <span data-ttu-id="386eb-575">在該面板中，按一下**上傳**，以及*檔案瀏覽器*會出現。</span><span class="sxs-lookup"><span data-stu-id="386eb-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="386eb-576">瀏覽至，然後按一下 []， **project.json**中建立的檔案**記事本**之前，然後按一下 [**開啟**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="386eb-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="386eb-577">此檔案會定義您的函式會使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="386eb-577">This file defines the libraries that your function will use.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="386eb-579">檔案已上傳時，它會出現在右側面板。</span><span class="sxs-lookup"><span data-stu-id="386eb-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="386eb-580">按一下將內開啟它**函式**編輯器。</span><span class="sxs-lookup"><span data-stu-id="386eb-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="386eb-581">它必須看起來**完全**與下圖相同。</span><span class="sxs-lookup"><span data-stu-id="386eb-581">It must look **exactly** the same as the next image.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="386eb-583">此時就很好測試您的函式的功能，將訊息儲存在您*資料表*。</span><span class="sxs-lookup"><span data-stu-id="386eb-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="386eb-584">在右上方的 [] 視窗中，按一下**測試**。</span><span class="sxs-lookup"><span data-stu-id="386eb-584">On the top right side of the window, click on **Test**.</span></span>

    ![自訂函式](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="386eb-586">將訊息插入上**要求本文**，如上顯示的影像上方，然後按一下**執行**。</span><span class="sxs-lookup"><span data-stu-id="386eb-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="386eb-587">此函式會執行，顯示的結果狀態 (您會注意到綠色**狀態 202 已接受**上面*輸出*視窗中，這表示它已成功的呼叫):</span><span class="sxs-lookup"><span data-stu-id="386eb-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![輸出結果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="386eb-589">第 14 章-檢視作用中的訊息</span><span class="sxs-lookup"><span data-stu-id="386eb-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="386eb-590">如果您現在可以開啟 Visual Studio (**未**Visual Studio Code)，您可以將視覺化您測試訊息的結果，因為它會儲存在*MessageContent*區域的字串。</span><span class="sxs-lookup"><span data-stu-id="386eb-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![自訂函式](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="386eb-592">表格服務和函式應用程式就地，Ubuntu 裝置上的訊息會出現在您*IoTMessages*資料表。</span><span class="sxs-lookup"><span data-stu-id="386eb-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="386eb-593">如果尚未執行，同樣地，啟動您的裝置，您將能夠看到結果訊息，從您的裝置和您的資料表內的模組，使用 Visual Studio *Cloud Explorer*。</span><span class="sxs-lookup"><span data-stu-id="386eb-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![將資料視覺化](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="386eb-595">第 15 章-Power BI 設定</span><span class="sxs-lookup"><span data-stu-id="386eb-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="386eb-596">若要從您的 IOT 裝置會設定將資料視覺化**Power BI** （桌面版），要從中收集資料*資料表*您剛才建立的服務。</span><span class="sxs-lookup"><span data-stu-id="386eb-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="386eb-597">*HoloLens*版本的 Power BI 會接著使用該資料以視覺化方式檢視結果。</span><span class="sxs-lookup"><span data-stu-id="386eb-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="386eb-598">開啟 Windows 10 上的 Microsoft Store 並搜尋**Power BI Desktop**。</span><span class="sxs-lookup"><span data-stu-id="386eb-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="386eb-600">下載應用程式。</span><span class="sxs-lookup"><span data-stu-id="386eb-600">Download the application.</span></span> <span data-ttu-id="386eb-601">一旦下載完成，請開啟它。</span><span class="sxs-lookup"><span data-stu-id="386eb-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="386eb-602">登入*Power BI*與您**Microsoft 365 帳戶**。</span><span class="sxs-lookup"><span data-stu-id="386eb-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="386eb-603">您可能會重新導向至瀏覽器中，登入。</span><span class="sxs-lookup"><span data-stu-id="386eb-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="386eb-604">一旦您已註冊，返回 Power BI 應用程式，並再次登入。</span><span class="sxs-lookup"><span data-stu-id="386eb-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="386eb-605">按一下 **取得資料**，然後按一下**更多...**.</span><span class="sxs-lookup"><span data-stu-id="386eb-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="386eb-607">按一下  **Azure**， **Azure 資料表儲存體**，然後按一下**Connect**。</span><span class="sxs-lookup"><span data-stu-id="386eb-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="386eb-609">系統會提示您插入**adresa URL Tabulky**稍早收集到的 ([在步驟 13 小時，共 11 章](#chapter-11---create-table-service))，建立您的資料表服務時。</span><span class="sxs-lookup"><span data-stu-id="386eb-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="386eb-610">在插入 URL 之後, 刪除路徑參考到資料表"子資料夾 」 （這是 IoTMessages，本課程中） 的一部分。</span><span class="sxs-lookup"><span data-stu-id="386eb-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="386eb-611">最後的結果應該如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="386eb-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="386eb-612">然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="386eb-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="386eb-614">系統會提示您插入**儲存體金鑰**您記下 ([的步驟 11 第 11 章](#chapter-11---create-table-service)) 先前在建立您的資料表儲存體。</span><span class="sxs-lookup"><span data-stu-id="386eb-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="386eb-615">然後按一下**Connect**。</span><span class="sxs-lookup"><span data-stu-id="386eb-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="386eb-617">A**導覽器 面板**將會顯示，勾選您表旁邊的方塊，然後按一下**負載**。</span><span class="sxs-lookup"><span data-stu-id="386eb-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="386eb-619">Power BI 中，現在已載入您的資料表，但需要的查詢，以在其中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="386eb-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="386eb-620">若要這樣做，請以滑鼠右鍵按一下資料表名稱，其位於**欄位面板**螢幕的右上方。</span><span class="sxs-lookup"><span data-stu-id="386eb-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="386eb-621">然後按一下**編輯查詢**。</span><span class="sxs-lookup"><span data-stu-id="386eb-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="386eb-623">A **Power Query 編輯器**會開啟新視窗，顯示您的資料表。</span><span class="sxs-lookup"><span data-stu-id="386eb-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="386eb-624">按一下 上一字**記錄**內*內容*資料表資料行，以視覺化方式檢視您儲存的內容。</span><span class="sxs-lookup"><span data-stu-id="386eb-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="386eb-626">按一下  **Into 資料表**，在視窗的左上方。</span><span class="sxs-lookup"><span data-stu-id="386eb-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="386eb-628">按一下 **關閉並套用**。</span><span class="sxs-lookup"><span data-stu-id="386eb-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="386eb-630">在載入此查詢中，完成後**欄位面板**，在畫面的右側，勾選 參數對應的方塊**名稱**並**值**至以視覺化方式檢視**MessageContent**資料行內容。</span><span class="sxs-lookup"><span data-stu-id="386eb-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="386eb-632">按一下 **藍色的磁碟片圖示**在左上方的 儲存您所選擇的資料夾中的工作 視窗。</span><span class="sxs-lookup"><span data-stu-id="386eb-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="386eb-634">您現在可以按一下 [發行] 按鈕上, 傳至您的工作區的資料表。</span><span class="sxs-lookup"><span data-stu-id="386eb-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="386eb-635">出現提示時，按一下**我的工作區**然後按一下*選取*。</span><span class="sxs-lookup"><span data-stu-id="386eb-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="386eb-636">等候它顯示在提交的成功的結果。</span><span class="sxs-lookup"><span data-stu-id="386eb-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="386eb-639">下一個章節是特定的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="386eb-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="386eb-640">Power BI 目前不提供為沈浸式應用程式，不過您可以在 Windows 混合實境入口網站 （也稱為 Cliff 房屋） 來執行桌面版本透過桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="386eb-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="386eb-641">第 16 章-HoloLens 上顯示 Power BI 資料</span><span class="sxs-lookup"><span data-stu-id="386eb-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="386eb-642">在您的 HoloLens 上登入**Microsoft Store**，依序點選應用程式清單中的圖示。</span><span class="sxs-lookup"><span data-stu-id="386eb-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="386eb-644">搜尋，然後下載**Power BI**應用程式。</span><span class="sxs-lookup"><span data-stu-id="386eb-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="386eb-646">開始**Power BI**從您的應用程式清單。</span><span class="sxs-lookup"><span data-stu-id="386eb-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="386eb-647">**Power BI**可能會要求您登入您**Microsoft 365 帳戶**。</span><span class="sxs-lookup"><span data-stu-id="386eb-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="386eb-648">一次，應用程式內的工作區應該預設會顯示在下圖所示。</span><span class="sxs-lookup"><span data-stu-id="386eb-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="386eb-649">如果，不會發生，只要按一下視窗左邊的工作區圖示。</span><span class="sxs-lookup"><span data-stu-id="386eb-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="386eb-651">您已完成您的 IoT 中樞應用程式</span><span class="sxs-lookup"><span data-stu-id="386eb-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="386eb-652">恭喜，您已成功建立 IoT 中樞服務，以模擬的虛擬機器的 Edge 裝置。</span><span class="sxs-lookup"><span data-stu-id="386eb-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="386eb-653">您的裝置可以進行通訊的機器學習模型到 Azure 資料表服務，透過 Azure 函式應用程式，這是讀取到 Power BI，並以視覺化方式檢視內 Microsoft HoloLens 的結果。</span><span class="sxs-lookup"><span data-stu-id="386eb-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="386eb-655">Bonus 練習</span><span class="sxs-lookup"><span data-stu-id="386eb-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="386eb-656">練習 1</span><span class="sxs-lookup"><span data-stu-id="386eb-656">Exercise 1</span></span>

<span data-ttu-id="386eb-657">展開 儲存在資料表中的訊息結構，則會顯示為圖形。</span><span class="sxs-lookup"><span data-stu-id="386eb-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="386eb-658">您可能想要收集更多資料，並將它儲存在相同資料表中，稍後再顯示。</span><span class="sxs-lookup"><span data-stu-id="386eb-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="386eb-659">練習 2</span><span class="sxs-lookup"><span data-stu-id="386eb-659">Exercise 2</span></span>

<span data-ttu-id="386eb-660">建立其他 IoT 面板，以便它可以透過分析攝影機擷取映像部署至 「 相機擷取 」 模組。</span><span class="sxs-lookup"><span data-stu-id="386eb-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
