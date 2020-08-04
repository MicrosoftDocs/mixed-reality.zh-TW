---
title: Azure 雲端教學課程 - 3。 整合 Azure 自訂視覺
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中執行 Azure 自訂視覺。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, hololens 2, azure 自訂視覺, azure 認知服務
ms.localizationpriority: high
ms.openlocfilehash: 0fc3793315dd05f91a6193b68343205f53a3092a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376460"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="e2a95-105">3.整合 Azure 自訂視覺</span><span class="sxs-lookup"><span data-stu-id="e2a95-105">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="e2a95-106">您將在本教學課程中了解如何使用 **Azure 自訂視覺**。您將上傳一組相片，將其與「追蹤物件」產生關聯，然後上傳至**自訂視覺**服務並開始訓練程序。</span><span class="sxs-lookup"><span data-stu-id="e2a95-106">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="e2a95-107">接著，您將使用該服務從網路攝影機摘要中捕捉相片，以偵測「追蹤物件」。</span><span class="sxs-lookup"><span data-stu-id="e2a95-107">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="e2a95-108">目標</span><span class="sxs-lookup"><span data-stu-id="e2a95-108">Objectives</span></span>

* <span data-ttu-id="e2a95-109">了解 Azure 自訂視覺的基本概念</span><span class="sxs-lookup"><span data-stu-id="e2a95-109">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="e2a95-110">了解如何設定場景，以在此專案中使用自訂視覺</span><span class="sxs-lookup"><span data-stu-id="e2a95-110">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="e2a95-111">了解如何整合上傳、訓練和偵測影像</span><span class="sxs-lookup"><span data-stu-id="e2a95-111">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="e2a95-112">了解 Azure 自訂視覺</span><span class="sxs-lookup"><span data-stu-id="e2a95-112">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="e2a95-113">**Azure 自訂視覺**是**認知服務**系列中的一部分，可用來訓練影像分類器。</span><span class="sxs-lookup"><span data-stu-id="e2a95-113">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="e2a95-114">影像分類器是一種 AI 服務，會使用訓練的模型來套用相符的標記。</span><span class="sxs-lookup"><span data-stu-id="e2a95-114">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="e2a95-115">我們的應用程式會使用此分類功能來偵測「追蹤物件」。</span><span class="sxs-lookup"><span data-stu-id="e2a95-115">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="e2a95-116">深入了解 [Azure 自訂視覺](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。</span><span class="sxs-lookup"><span data-stu-id="e2a95-116">Learn more about [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="e2a95-117">準備 Azure 自訂視覺</span><span class="sxs-lookup"><span data-stu-id="e2a95-117">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="e2a95-118">開始之前，您必須建立自訂視覺專案，而最快的方式是使用入口網站。</span><span class="sxs-lookup"><span data-stu-id="e2a95-118">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="e2a95-119">在＜上傳和標記影像＞區段之前，請遵循此[快速入門教學課程](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images)來設定帳戶和專案。</span><span class="sxs-lookup"><span data-stu-id="e2a95-119">Follow this [quickstart tutorial](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="e2a95-120">若要訓練模型，您必須至少有 2 個標記，且每個標記應有 5 個影像。</span><span class="sxs-lookup"><span data-stu-id="e2a95-120">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="e2a95-121">若要使用此應用程式，您應至少建立一個包含 5 個影像的標記，如此之後的訓練程序才不會失敗。</span><span class="sxs-lookup"><span data-stu-id="e2a95-121">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="e2a95-122">準備場景</span><span class="sxs-lookup"><span data-stu-id="e2a95-122">Preparing the scene</span></span>

<span data-ttu-id="e2a95-123">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureCloudServices] > [Prefabs] > [Manager] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e2a95-123">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="e2a95-125">從該處，將 Prefab **ObjectDetectionManager** 拖曳到場景階層中。</span><span class="sxs-lookup"><span data-stu-id="e2a95-125">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="e2a95-127">在 [階層] 視窗中，找出 **ObjectDetectionManager** 物件並加以選取。</span><span class="sxs-lookup"><span data-stu-id="e2a95-127">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="e2a95-128">**ObjectDetectionManager** Prefab 包含 **ObjectDetectionManager (指令碼)** 元件，而且您可以從 [偵測器] 視窗看到其相依於數個設定。</span><span class="sxs-lookup"><span data-stu-id="e2a95-128">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on several settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="e2a95-129">擷取 Azure API 資源認證</span><span class="sxs-lookup"><span data-stu-id="e2a95-129">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="e2a95-130">您可以從 Azure 入口網站和自訂視覺入口網站取得 **ObjectDetectionManager (指令碼)** 設定的必要認證。</span><span class="sxs-lookup"><span data-stu-id="e2a95-130">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="azure-portal"></a><span data-ttu-id="e2a95-131">Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="e2a95-131">Azure Portal</span></span>

<span data-ttu-id="e2a95-132">尋找並找出您在本教學課程＜準備場景＞一節中建立且類型為**認知服務**的自訂視覺資源。</span><span class="sxs-lookup"><span data-stu-id="e2a95-132">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial.</span></span> <span data-ttu-id="e2a95-133">按一下 [金鑰和端點] 以擷取必要的認證。</span><span class="sxs-lookup"><span data-stu-id="e2a95-133">There click on *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="custom-vision-dashboard"></a><span data-ttu-id="e2a95-134">自訂視覺儀表板</span><span class="sxs-lookup"><span data-stu-id="e2a95-134">Custom Vision Dashboard</span></span>

<span data-ttu-id="e2a95-135">在[自訂視覺](https://www.customvision.ai/projects)儀表板中，開啟您在本教學課程中建立的專案，然後按一下頁面右上角的齒輪圖示，以開啟設定頁面。</span><span class="sxs-lookup"><span data-stu-id="e2a95-135">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="e2a95-136">您會在右側的＜資源＞區段中找到所需的認證。</span><span class="sxs-lookup"><span data-stu-id="e2a95-136">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="e2a95-137">現在，正確設定 **ObjectDetectionManager (指令碼)** 之後，請在場景階層中尋找 **的 SceneController** 物件，然後加以選取。</span><span class="sxs-lookup"><span data-stu-id="e2a95-137">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="e2a95-139">您會在 **SceneController** 元件中看到 [物件偵測管理員] 欄位是空的，請將 **ObjectDetectionManager** 從階層拖曳至該欄位並儲存場景。</span><span class="sxs-lookup"><span data-stu-id="e2a95-139">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="e2a95-141">拍攝影像並上傳</span><span class="sxs-lookup"><span data-stu-id="e2a95-141">Take and upload images</span></span>

<span data-ttu-id="e2a95-142">執行場景並按一下 [設定物件]，然後輸入您在[上一課](mr-learning-azure-02.md)中建立的其中一個**追蹤物件名稱**。</span><span class="sxs-lookup"><span data-stu-id="e2a95-142">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="e2a95-143">現在，按一下**物件卡片**底部的 [電腦視覺] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e2a95-143">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="e2a95-144">新的視窗會隨即開啟，而您必須在其中拍攝六張相片來訓練模型，以進行影像辨識。</span><span class="sxs-lookup"><span data-stu-id="e2a95-144">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="e2a95-145">當您看到想要追蹤的物件時，請按一下 [相機] 按鈕並執行 AirTap，請執行此動作六次。</span><span class="sxs-lookup"><span data-stu-id="e2a95-145">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="e2a95-146">若要改善模型訓練，請嘗試拍攝角度和光源條件各不相同的影像。</span><span class="sxs-lookup"><span data-stu-id="e2a95-146">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="e2a95-147">當您有足夠的影像之後，請按一下 [訓練] 按鈕，在雲端中啟動模型訓練程序。</span><span class="sxs-lookup"><span data-stu-id="e2a95-147">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="e2a95-148">啟動訓練將會上傳所有影像並開始訓練，這可能需要一分鐘或更長的時間。</span><span class="sxs-lookup"><span data-stu-id="e2a95-148">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="e2a95-149">功能表內的訊息會指出目前進度，當其指示已完成時，您就可以停止應用程式</span><span class="sxs-lookup"><span data-stu-id="e2a95-149">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="e2a95-150">**ObjectDetectionManager (指令碼)** 會直接將拍攝的影像上傳至自訂視覺服務。</span><span class="sxs-lookup"><span data-stu-id="e2a95-150">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="e2a95-151">另一種方式是使用自訂視覺 API 接受影像的 URL，作為練習，您可以修改 **ObjectDetectionManager (指令碼)** ，改為將影像上傳至 Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="e2a95-151">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="e2a95-152">偵測物件</span><span class="sxs-lookup"><span data-stu-id="e2a95-152">Detect objects</span></span>

<span data-ttu-id="e2a95-153">您現在可以將訓練的模型放到測試中、執行應用程式，然後從 [主功能表] 中按一下 [搜尋物件]，接著輸入有問題的**追蹤物件**名稱。</span><span class="sxs-lookup"><span data-stu-id="e2a95-153">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="e2a95-154">**物件卡片**會隨即出現，然後請按一下 [自訂視覺] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e2a95-154">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="e2a95-155">在這裡，**ObjectDetectionManager** 會開始在背景中取得相機中的拍攝影像，並在功能表上顯示進度。</span><span class="sxs-lookup"><span data-stu-id="e2a95-155">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="e2a95-156">將相機指向您用來訓練模型的物件，您將在不久後看到其已偵測到該物件。</span><span class="sxs-lookup"><span data-stu-id="e2a95-156">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e2a95-157">恭喜！</span><span class="sxs-lookup"><span data-stu-id="e2a95-157">Congratulations</span></span>

<span data-ttu-id="e2a95-158">在本教學課程中，您已了解如何使用 Azure 自訂視覺來訓練影像，並使用分類服務來偵測符合相關**追蹤物件**的影像。</span><span class="sxs-lookup"><span data-stu-id="e2a95-158">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="e2a95-159">在下一個教學課程中，您將了解如何使用 Azure Spatial Anchors，將「追蹤物件」與實體世界中的位置連結，以及如何顯示箭號來引導使用者回到追蹤物件的連結位置。</span><span class="sxs-lookup"><span data-stu-id="e2a95-159">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

[<span data-ttu-id="e2a95-160">下一個教學課程：4.整合 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e2a95-160">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)
