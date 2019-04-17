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
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595114"
---
# <a name="locatable-camera-in-unity"></a>Unity 之外的可尋獲觀景窗

## <a name="enabling-the-capability-for-photo-video-camera"></a>啟用此功能的相片攝影機

「 網路攝影機 」 功能必須宣告要使用的應用程式[相機](locatable-camera.md)。
1. 瀏覽至"編輯 > 專案設定 > Player"頁面在 Unity 編輯器中，請移至播放程式設定
2. 按一下 [Windows Store] 索引標籤
3. 在 「 發行的設定 > 功能 」 區段中，檢查**網路攝影機**並**麥克風**功能

只有一項作業一次發生的相機。 若要判斷哪一種模式 （相片、 視訊或 none） 在攝影機處於目前，您可以檢查 UnityEngine.XR.WSA.WebCam.Mode。

## <a name="photo-capture"></a>拍攝相片

**命名空間：***UnityEngine.XR.WSA.WebCam*<br>
**類型：***PhotoCapture*

*PhotoCapture*類型可讓您充分仍與相片視訊攝影機中的相片。 使用最一般的模式，就*PhotoCapture*來拍攝相片如下所示：
1. 建立*PhotoCapture*物件
2. 建立*CameraParameters*我們想要的設定物件
3. Start Photo Mode via *StartPhotoModeAsync*
4. 取得所需的相片
    * （選擇性）該圖片的互動
5. 停止相片模式，並清除資源

### <a name="common-set-up-for-photocapture"></a>一般設定適用於 PhotoCapture

所有的三個用途，我們開始相同上述的前 3 個步驟

我們先建立*PhotoCapture*物件

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

接下來我們可以在這裡儲存我們的物件、 設定我們的參數，以及啟動相片模式

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

最後，我們也會使用相同清除此處所提供的程式碼

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

完成這些步驟中之後, 您可以選擇擷取相片的類型。

### <a name="capture-a-photo-to-a-file"></a>擷取至檔案相片

擷取相片直接以檔案為最簡單的操作。 相片可以儲存為 JPG 或 PNG。

如果我們已成功啟動相片模式，我們現在會拍攝相片，並將它儲存在磁碟上

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

在擷取後到磁碟的相片，我們將會結束相片模式，並再清除物件

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

### <a name="capture-a-photo-to-a-texture2d"></a>擷取相片以 Texture2D

擷取資料到 Texture2D，程序時，非常類似於擷取到磁碟。

我們會遵循上述程序設定。

在  *OnPhotoModeStarted*，我們會擷取記憶體的框架。

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

然後，我們將材質套用我們的結果，並使用的常見清除上述程式碼。

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>與未經處理位元組擷取相片和互動

在記憶體中的未經處理位元組與互動框架中，我們將遵循相同的設定上述的步驟並*OnPhotoModeStarted*如同擷取相片以 Texture2D。 不同之處在於*OnCapturedPhotoToMemory*我們可以在此取得未經處理位元組，並與其互動。

在此範例中，我們將建立*清單<Color>* 可能在進一步處理或套用到透過紋理*SetPixels()*

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

## <a name="video-capture"></a>影像擷取

**命名空間：***UnityEngine.XR.WSA.WebCam*<br>
**類型：***VideoCapture*

*VideoCapture*函式非常類似於*PhotoCapture*。 只有兩個差異是，您必須指定框架每個第二個 (FPS) 值，然後您可以只將直接儲存到磁碟儲存為.mp4 檔案。 若要使用的步驟*VideoCapture*如下所示：
1. 建立*VideoCapture*物件
2. 建立*CameraParameters*我們想要的設定物件
3. 開始透過視訊模式*StartVideoModeAsync*
4. 開始錄製影片
5. 停止錄製影片
6. 停止視訊模式，並清除資源

我們先建立我們*VideoCapture*物件*VideoCapture m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

接著會設定的參數，我們將需要進行錄製和開始。

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

一旦啟動，我們將開始錄製

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

啟動錄製後，您可以更新 UI 或行為，若要啟用停止。 這裡我們只是記錄

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

稍後，我們會想要停止錄製。 從計時器或使用者輸入，比方說，這可能會發生。

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

一旦停止錄製後，我們將會停止視訊的模式，並清除我們的資源。

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

## <a name="troubleshooting"></a>疑難排解
* 沒有解決方案可用
    * 請確定**網路攝影機**功能在您的專案中指定。

## <a name="see-also"></a>另請參閱
* [之外的可尋獲相機](locatable-camera.md)
