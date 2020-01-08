---
title: Unity 中的定位相機
description: 在 Unity 中使用 HoloLens 的相機。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 相片、影片、hololens、攝影機、unity、定位
ms.openlocfilehash: b4a1a7e11a7606dab76b954c8d58a335d6bae0ab
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597611"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="52883-104">Unity 中的定位相機</span><span class="sxs-lookup"><span data-stu-id="52883-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="52883-105">啟用相片攝影機的功能</span><span class="sxs-lookup"><span data-stu-id="52883-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="52883-106">必須為應用程式宣告「網路攝影機」功能，才能使用[相機](locatable-camera.md)。</span><span class="sxs-lookup"><span data-stu-id="52883-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="52883-107">在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > 播放機] 頁面，移至 [播放程式] 設定</span><span class="sxs-lookup"><span data-stu-id="52883-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="52883-108">按一下 [Windows Store] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="52883-108">Click the "Windows Store" tab</span></span>
3. <span data-ttu-id="52883-109">在 [發佈設定 > 功能] 區段中，檢查**網路**攝影機和**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="52883-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="52883-110">相機一次只能發生單一作業。</span><span class="sxs-lookup"><span data-stu-id="52883-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="52883-111">若要判斷相機目前所在的模式（相片、影片或無），您可以檢查 UnityEngine XR。</span><span class="sxs-lookup"><span data-stu-id="52883-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="52883-112">相片捕獲</span><span class="sxs-lookup"><span data-stu-id="52883-112">Photo Capture</span></span>

<span data-ttu-id="52883-113">**命名空間：** *UnityEngine. XR. WSA. 網路*攝影機</span><span class="sxs-lookup"><span data-stu-id="52883-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="52883-114">**類型：** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="52883-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="52883-115">*PhotoCapture*類型可讓您以相片攝影機拍照。</span><span class="sxs-lookup"><span data-stu-id="52883-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="52883-116">使用*PhotoCapture*拍攝相片的一般模式如下：</span><span class="sxs-lookup"><span data-stu-id="52883-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="52883-117">建立*PhotoCapture*物件</span><span class="sxs-lookup"><span data-stu-id="52883-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="52883-118">使用您想要的設定來建立*CameraParameters*物件</span><span class="sxs-lookup"><span data-stu-id="52883-118">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="52883-119">透過*StartPhotoModeAsync*啟動相片模式</span><span class="sxs-lookup"><span data-stu-id="52883-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="52883-120">採用所需的相片</span><span class="sxs-lookup"><span data-stu-id="52883-120">Take the desired photo</span></span>
    * <span data-ttu-id="52883-121">選擇性與該圖片互動</span><span class="sxs-lookup"><span data-stu-id="52883-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="52883-122">停止相片模式並清除資源</span><span class="sxs-lookup"><span data-stu-id="52883-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="52883-123">適用于 PhotoCapture 的一般設定</span><span class="sxs-lookup"><span data-stu-id="52883-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="52883-124">對於這三種用法，請從上述的前3個步驟開始</span><span class="sxs-lookup"><span data-stu-id="52883-124">For all three uses, start with the same first 3 steps above</span></span>

<span data-ttu-id="52883-125">從建立*PhotoCapture*物件開始</span><span class="sxs-lookup"><span data-stu-id="52883-125">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="52883-126">接下來，儲存您的物件、設定參數和啟動相片模式</span><span class="sxs-lookup"><span data-stu-id="52883-126">Next, store your object, set your parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="52883-127">最後，您也會使用此處顯示的相同清除程式碼</span><span class="sxs-lookup"><span data-stu-id="52883-127">In the end, you will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="52883-128">在這些步驟之後，您可以選擇要捕獲的相片類型。</span><span class="sxs-lookup"><span data-stu-id="52883-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="52883-129">將相片捕獲至檔案</span><span class="sxs-lookup"><span data-stu-id="52883-129">Capture a Photo to a File</span></span>

<span data-ttu-id="52883-130">最簡單的作業是直接將相片捕獲到檔案。</span><span class="sxs-lookup"><span data-stu-id="52883-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="52883-131">相片可以儲存為 JPG 或 PNG。</span><span class="sxs-lookup"><span data-stu-id="52883-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="52883-132">如果您已成功啟動相片模式，請拍攝相片並將它儲存在磁片上</span><span class="sxs-lookup"><span data-stu-id="52883-132">If you successfully started photo mode, take a photo and store it on disk</span></span>

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

<span data-ttu-id="52883-133">將相片捕獲到磁片之後，結束相片模式，然後清除您的物件</span><span class="sxs-lookup"><span data-stu-id="52883-133">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="52883-134">將相片捕獲到 Texture2D</span><span class="sxs-lookup"><span data-stu-id="52883-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="52883-135">將資料捕獲到 Texture2D 時，此程式非常類似于捕獲至磁片。</span><span class="sxs-lookup"><span data-stu-id="52883-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="52883-136">遵循上述的設定程式。</span><span class="sxs-lookup"><span data-stu-id="52883-136">Follow the set up process above.</span></span>

<span data-ttu-id="52883-137">在*OnPhotoModeStarted*中，將框架捕捉至記憶體。</span><span class="sxs-lookup"><span data-stu-id="52883-137">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

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

<span data-ttu-id="52883-138">接著，您會將結果套用至材質，並使用上述的一般清除程式碼。</span><span class="sxs-lookup"><span data-stu-id="52883-138">You will then apply your result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="52883-139">捕捉相片並與原始位元組互動</span><span class="sxs-lookup"><span data-stu-id="52883-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="52883-140">若要與記憶體內框架中的原始位元組互動，請遵循上述的設定步驟，並*OnPhotoModeStarted*為將相片捕獲到 Texture2D。</span><span class="sxs-lookup"><span data-stu-id="52883-140">To interact with the raw bytes of an in memory frame, follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="52883-141">其差異在於*OnCapturedPhotoToMemory*中，您可以在其中取得原始位元組並與其互動。</span><span class="sxs-lookup"><span data-stu-id="52883-141">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="52883-142">在此範例中，您將建立可透過*SetPixels （）* 進一步處理或套用至材質的*清單<Color>*</span><span class="sxs-lookup"><span data-stu-id="52883-142">In this example, you will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="52883-143">影片捕獲</span><span class="sxs-lookup"><span data-stu-id="52883-143">Video Capture</span></span>

<span data-ttu-id="52883-144">**命名空間：** *UnityEngine. XR. WSA. 網路*攝影機</span><span class="sxs-lookup"><span data-stu-id="52883-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="52883-145">**類型：** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="52883-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="52883-146">*VideoCapture*的功能非常類似*PhotoCapture*。</span><span class="sxs-lookup"><span data-stu-id="52883-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="52883-147">唯一的兩個差異在於，您必須指定每秒一個畫面（FPS）值，而且您只能將磁片直接儲存為一個檔案。</span><span class="sxs-lookup"><span data-stu-id="52883-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="52883-148">使用*VideoCapture*的步驟如下所示：</span><span class="sxs-lookup"><span data-stu-id="52883-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="52883-149">建立*VideoCapture*物件</span><span class="sxs-lookup"><span data-stu-id="52883-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="52883-150">使用您想要的設定來建立*CameraParameters*物件</span><span class="sxs-lookup"><span data-stu-id="52883-150">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="52883-151">透過*StartVideoModeAsync*啟動影片模式</span><span class="sxs-lookup"><span data-stu-id="52883-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="52883-152">開始錄製影片</span><span class="sxs-lookup"><span data-stu-id="52883-152">Start recording video</span></span>
5. <span data-ttu-id="52883-153">停止錄製影片</span><span class="sxs-lookup"><span data-stu-id="52883-153">Stop recording video</span></span>
6. <span data-ttu-id="52883-154">停止影片模式並清除資源</span><span class="sxs-lookup"><span data-stu-id="52883-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="52883-155">從建立我們的*VideoCapture*物件*VideoCapture 開始，m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="52883-155">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="52883-156">接下來，設定您要記錄和啟動的參數。</span><span class="sxs-lookup"><span data-stu-id="52883-156">Next, set up the parameters you will want for the recording and start.</span></span>

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

<span data-ttu-id="52883-157">啟動之後，開始錄製</span><span class="sxs-lookup"><span data-stu-id="52883-157">Once started, begin the recording</span></span>

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

<span data-ttu-id="52883-158">記錄開始之後，您可以更新您的 UI 或行為以啟用停止。</span><span class="sxs-lookup"><span data-stu-id="52883-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="52883-159">在這裡，您只需要記錄。</span><span class="sxs-lookup"><span data-stu-id="52883-159">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="52883-160">稍後，您會想要停止錄製。</span><span class="sxs-lookup"><span data-stu-id="52883-160">At a later point, you will want to stop the recording.</span></span> <span data-ttu-id="52883-161">例如，計時器或使用者輸入可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="52883-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="52883-162">記錄停止後，請停止影片模式並清除您的資源。</span><span class="sxs-lookup"><span data-stu-id="52883-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="52883-163">[疑難排解]</span><span class="sxs-lookup"><span data-stu-id="52883-163">Troubleshooting</span></span>
* <span data-ttu-id="52883-164">沒有任何可用的解決方案</span><span class="sxs-lookup"><span data-stu-id="52883-164">No resolutions are available</span></span>
    * <span data-ttu-id="52883-165">請確定您的專案中已指定**網路**攝影機功能。</span><span class="sxs-lookup"><span data-stu-id="52883-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="52883-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="52883-166">See Also</span></span>
* [<span data-ttu-id="52883-167">定位相機</span><span class="sxs-lookup"><span data-stu-id="52883-167">Locatable camera</span></span>](locatable-camera.md)
