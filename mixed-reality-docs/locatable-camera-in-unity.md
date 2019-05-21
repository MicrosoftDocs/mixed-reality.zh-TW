---
title: Unity 之外的可尋獲觀景窗
description: 在 Unity HoloLens 之外的可尋獲相機使用方式。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 相片、 視訊、 hololens、 相機、 unity，可以找到
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595114"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="dfbbe-104">Unity 之外的可尋獲觀景窗</span><span class="sxs-lookup"><span data-stu-id="dfbbe-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="dfbbe-105">啟用此功能的相片攝影機</span><span class="sxs-lookup"><span data-stu-id="dfbbe-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="dfbbe-106">「 網路攝影機 」 功能必須宣告要使用的應用程式[相機](locatable-camera.md)。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="dfbbe-107">瀏覽至"編輯 > 專案設定 > Player"頁面在 Unity 編輯器中，請移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="dfbbe-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="dfbbe-108">按一下 [Windows Store] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="dfbbe-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="dfbbe-109">在 「 發行的設定 > 功能 」 區段中，檢查**網路攝影機**並**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="dfbbe-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="dfbbe-110">只有一項作業一次發生的相機。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="dfbbe-111">若要判斷哪一種模式 （相片、 視訊或 none） 在攝影機處於目前，您可以檢查 UnityEngine.XR.WSA.WebCam.Mode。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="dfbbe-112">拍攝相片</span><span class="sxs-lookup"><span data-stu-id="dfbbe-112">Photo Capture</span></span>

<span data-ttu-id="dfbbe-113">**命名空間：** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="dfbbe-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="dfbbe-114">**類型：** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="dfbbe-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="dfbbe-115">*PhotoCapture*類型可讓您充分仍與相片視訊攝影機中的相片。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="dfbbe-116">使用最一般的模式，就*PhotoCapture*來拍攝相片如下所示：</span><span class="sxs-lookup"><span data-stu-id="dfbbe-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="dfbbe-117">建立*PhotoCapture*物件</span><span class="sxs-lookup"><span data-stu-id="dfbbe-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="dfbbe-118">建立*CameraParameters*我們想要的設定物件</span><span class="sxs-lookup"><span data-stu-id="dfbbe-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="dfbbe-119">Start Photo Mode via *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="dfbbe-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="dfbbe-120">取得所需的相片</span><span class="sxs-lookup"><span data-stu-id="dfbbe-120">Take the desired photo</span></span>
    * <span data-ttu-id="dfbbe-121">（選擇性）該圖片的互動</span><span class="sxs-lookup"><span data-stu-id="dfbbe-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="dfbbe-122">停止相片模式，並清除資源</span><span class="sxs-lookup"><span data-stu-id="dfbbe-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="dfbbe-123">一般設定適用於 PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="dfbbe-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="dfbbe-124">所有的三個用途，我們開始相同上述的前 3 個步驟</span><span class="sxs-lookup"><span data-stu-id="dfbbe-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="dfbbe-125">我們先建立*PhotoCapture*物件</span><span class="sxs-lookup"><span data-stu-id="dfbbe-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="dfbbe-126">接下來我們可以在這裡儲存我們的物件、 設定我們的參數，以及啟動相片模式</span><span class="sxs-lookup"><span data-stu-id="dfbbe-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

<span data-ttu-id="dfbbe-127">最後，我們也會使用相同清除此處所提供的程式碼</span><span class="sxs-lookup"><span data-stu-id="dfbbe-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="dfbbe-128">完成這些步驟中之後, 您可以選擇擷取相片的類型。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="dfbbe-129">擷取至檔案相片</span><span class="sxs-lookup"><span data-stu-id="dfbbe-129">Capture a Photo to a File</span></span>

<span data-ttu-id="dfbbe-130">擷取相片直接以檔案為最簡單的操作。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="dfbbe-131">相片可以儲存為 JPG 或 PNG。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="dfbbe-132">如果我們已成功啟動相片模式，我們現在會拍攝相片，並將它儲存在磁碟上</span><span class="sxs-lookup"><span data-stu-id="dfbbe-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="dfbbe-133">在擷取後到磁碟的相片，我們將會結束相片模式，並再清除物件</span><span class="sxs-lookup"><span data-stu-id="dfbbe-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="dfbbe-134">擷取相片以 Texture2D</span><span class="sxs-lookup"><span data-stu-id="dfbbe-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="dfbbe-135">擷取資料到 Texture2D，程序時，非常類似於擷取到磁碟。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="dfbbe-136">我們會遵循上述程序設定。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-136">We will follow the set up process above.</span></span>

<span data-ttu-id="dfbbe-137">在  *OnPhotoModeStarted*，我們會擷取記憶體的框架。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="dfbbe-138">然後，我們將材質套用我們的結果，並使用的常見清除上述程式碼。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="dfbbe-139">與未經處理位元組擷取相片和互動</span><span class="sxs-lookup"><span data-stu-id="dfbbe-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="dfbbe-140">在記憶體中的未經處理位元組與互動框架中，我們將遵循相同的設定上述的步驟並*OnPhotoModeStarted*如同擷取相片以 Texture2D。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="dfbbe-141">不同之處在於*OnCapturedPhotoToMemory*我們可以在此取得未經處理位元組，並與其互動。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="dfbbe-142">在此範例中，我們將建立*清單<Color>* 可能在進一步處理或套用到透過紋理*SetPixels()*</span><span class="sxs-lookup"><span data-stu-id="dfbbe-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a><span data-ttu-id="dfbbe-143">影像擷取</span><span class="sxs-lookup"><span data-stu-id="dfbbe-143">Video Capture</span></span>

<span data-ttu-id="dfbbe-144">**命名空間：** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="dfbbe-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="dfbbe-145">**類型：** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="dfbbe-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="dfbbe-146">*VideoCapture*函式非常類似於*PhotoCapture*。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="dfbbe-147">只有兩個差異是，您必須指定框架每個第二個 (FPS) 值，然後您可以只將直接儲存到磁碟儲存為.mp4 檔案。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="dfbbe-148">若要使用的步驟*VideoCapture*如下所示：</span><span class="sxs-lookup"><span data-stu-id="dfbbe-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="dfbbe-149">建立*VideoCapture*物件</span><span class="sxs-lookup"><span data-stu-id="dfbbe-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="dfbbe-150">建立*CameraParameters*我們想要的設定物件</span><span class="sxs-lookup"><span data-stu-id="dfbbe-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="dfbbe-151">開始透過視訊模式*StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="dfbbe-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="dfbbe-152">開始錄製影片</span><span class="sxs-lookup"><span data-stu-id="dfbbe-152">Start recording video</span></span>
5. <span data-ttu-id="dfbbe-153">停止錄製影片</span><span class="sxs-lookup"><span data-stu-id="dfbbe-153">Stop recording video</span></span>
6. <span data-ttu-id="dfbbe-154">停止視訊模式，並清除資源</span><span class="sxs-lookup"><span data-stu-id="dfbbe-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="dfbbe-155">我們先建立我們*VideoCapture*物件*VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="dfbbe-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="dfbbe-156">接著會設定的參數，我們將需要進行錄製和開始。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-156">We then will set up the parameters we will want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

<span data-ttu-id="dfbbe-157">一旦啟動，我們將開始錄製</span><span class="sxs-lookup"><span data-stu-id="dfbbe-157">Once started, we will begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

<span data-ttu-id="dfbbe-158">啟動錄製後，您可以更新 UI 或行為，若要啟用停止。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="dfbbe-159">這裡我們只是記錄</span><span class="sxs-lookup"><span data-stu-id="dfbbe-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="dfbbe-160">稍後，我們會想要停止錄製。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="dfbbe-161">從計時器或使用者輸入，比方說，這可能會發生。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="dfbbe-162">一旦停止錄製後，我們將會停止視訊的模式，並清除我們的資源。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a><span data-ttu-id="dfbbe-163">疑難排解</span><span class="sxs-lookup"><span data-stu-id="dfbbe-163">Troubleshooting</span></span>
* <span data-ttu-id="dfbbe-164">沒有解決方案可用</span><span class="sxs-lookup"><span data-stu-id="dfbbe-164">No resolutions are available</span></span>
    * <span data-ttu-id="dfbbe-165">請確定**網路攝影機**功能在您的專案中指定。</span><span class="sxs-lookup"><span data-stu-id="dfbbe-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfbbe-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfbbe-166">See Also</span></span>
* [<span data-ttu-id="dfbbe-167">之外的可尋獲相機</span><span class="sxs-lookup"><span data-stu-id="dfbbe-167">Locatable camera</span></span>](locatable-camera.md)
