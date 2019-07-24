---
title: 定位相機
description: HoloLens 前方攝影機的一般資訊、其運作方式, 以及可供開發人員使用的設定檔和解決方案。
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: 相機, hololens, 彩色攝影機, 正面, hololens 2, cv, 電腦視覺, 基準, 標記, qr 代碼, qr, 相片, 影片
ms.openlocfilehash: b80e201723f8f499a6d35008b9d308f93b925b1c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694531"
---
# <a name="locatable-camera"></a>定位相機

HoloLens 包含在裝置前方掛接的全球化相機, 可讓應用程式查看使用者看到的內容。 開發人員可以存取和控制相機, 就像在 smartphone、筆記本電腦或桌上型電腦上的彩色攝影機一樣。 在行動裝置和桌上型電腦上工作的相同通用 windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)和 windows Media foundation api 可在 HoloLens 上工作。 Unity[也包裝了這些 windows](locatable-camera-in-unity.md)應用程式開發介面, 以便在 HoloLens 上抽象化相機的簡單用法, 例如拍攝一般相片和影片 (不論是否有全息影像), 以及找出相機在場景中的位置和觀點。

## <a name="device-camera-information"></a>裝置相機資訊

### <a name="hololens-first-generation"></a>HoloLens (第一代)

* 已修正具有自動白平衡、自動曝光和完整影像處理管線的焦點相片/video (PV) 攝影機。
* 當相機處於作用中狀態時, 將會照亮世界上的白色隱私權 LED
* 相機支援下列模式 (所有模式都是16:9 外觀比例), 其為30、24、20、15和 5 fps:

  |  視訊  |  預覽  |  但是  |  視圖的水準欄位 (H-FOV) |  建議的使用方式 | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (具有視頻穩定的預設模式) | 
  |  N/A |  N/A |  2048x1152 |  67deg |  最高解析度仍然影像 | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  影片穩定前的 Overscan (填補) 解析度 | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  具有 overscan 的大型 FOV 影片模式 | 
  |  896x504 |  896x504 |  896x504 |  48deg |  影像處理工作的低電源/低解析度模式 | 

### <a name="hololens-2"></a>HoloLens 2

* 自動聚焦相片/影片 (PV) 攝影機, 具備自動白平衡、自動曝光和完整影像處理管線。
* 當相機處於作用中狀態時, 世界上的白色隱私權 LED 將會亮起。
* HoloLens 2 支援不同的相機設定檔。 瞭解如何[探索並選取攝影機功能](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles)。
* 相機支援下列設定檔和解決方案 (所有的影片模式都是16:9 外觀比例):
  
  | 設定檔                                         | 視訊     | 預覽   | 但是     | 畫面播放速率 | 視圖的水準欄位 (H-FOV) | 建議的使用方式                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | 舊版, 0 BalancedVideoAndPhoto, 100             | 2272x1278 | 2272x1278 |           | 15、30       | 64.69                            | 高品質的影片錄製                |
  | 舊版, 0 BalancedVideoAndPhoto, 100             | 896x504   | 896x504   |           | 15、30       | 64.69                            | 適用于高品質相片捕獲的預覽串流 |
  | 舊版, 0 BalancedVideoAndPhoto, 100             |           |           | 3904x2196 |             | 64.69                            | 高品質的相片捕獲                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15、30       | 64.69                            | 長時間的案例                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15、30       | 64.69                            | 長時間的案例                     |
  | 視訊會議, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15、30、60    | 64.69                            | 視訊會議, 長時間案例 |
  | 視訊會議, 100                           | 1504x846  | 1504x846  |           | 5、15、30、60  | 64.69                            | 視訊會議, 長時間案例 |
  | 視訊會議, 100 BalancedVideoAndPhoto, 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15、30       | 64.69                            | 視訊會議, 長時間案例 |
  | 視訊會議, 100 BalancedVideoAndPhoto, 120 | 1280x720  | 1280x720  | 1280x720  | 15、30       | 64.69                            | 視訊會議, 長時間案例 |
  | 視訊會議, 100 BalancedVideoAndPhoto, 120 | 1128x636  |           |           | 15、30       | 64.69                            | 視訊會議, 長時間案例 |
  | 視訊會議, 100 BalancedVideoAndPhoto, 120 | 960x540   |           |           | 15、30       | 64.69                            | 視訊會議, 長時間案例 |
  | 視訊會議, 100 BalancedVideoAndPhoto, 120 | 760x428   |           |           | 15、30       | 64.69                            | 視訊會議, 長時間案例 |
  | 視訊會議, 100 BalancedVideoAndPhoto, 120 | 640x360   |           |           | 15、30       | 64.69                            | 視訊會議, 長時間案例 |
  | 視訊會議, 100 BalancedVideoAndPhoto, 120 | 500x282   |           |           | 15、30       | 64.69                            | 視訊會議, 長時間案例 |
  | 視訊會議, 100 BalancedVideoAndPhoto, 120 | 424x240   |           |           | 15、30       | 64.69                            | 視訊會議, 長時間案例 |

>[!NOTE]
>客戶可以利用[混合現實 capture](mixed-reality-capture.md)來拍攝應用程式的影片或相片, 包括全息影像和影片穩定。
>
>身為開發人員, 如果您想要在客戶捕獲內容時盡可能地查看, 請考慮建立您的應用程式。 您也可以直接在應用程式內啟用 (和自訂) 混合現實 capture。 深入瞭解[適用于開發人員的混合現實 capture](mixed-reality-capture-for-developers.md)。

## <a name="locating-the-device-camera-in-the-world"></a>尋找世界中的裝置攝影機

當 HoloLens 拍攝相片和影片時, 捕捉的畫面會包含相機在世界中的位置, 以及相機的鏡頭模型。 這可讓應用程式在現實世界中, 針對增強型映射案例的位置提供相關的原因。 開發人員可以使用他們最愛的影像處理或自訂的電腦視覺程式庫, 以創造性的案例來進行。

HoloLens 檔中其他地方的「相機」可能是指「虛擬遊戲攝影機」 (應用程式轉譯成的截錐)。 除非另有指示, 否則此頁面上的「相機」是指真實世界的 RGB 色彩相機。

本頁的詳細資料涵蓋了如何使用[MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference)類別, 不過也有 api 可使用[媒體基礎屬性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)來提取相機內建函式和位置。 如需詳細資訊, 請參閱全像攝影的[臉部追蹤範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)。

### <a name="images-with-coordinate-systems"></a>具有座標系統的影像

每個影像框架 (不論是相片或影片) 都會在拍攝時包含根目錄在相機上的[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , 這可以使用[MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)的[CoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)屬性來存取。 此外, 每個畫面格都包含相機鏡頭模型的描述, 可以在[CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)屬性中找到。 這些轉換會一起定義3D 空間中的每個圖元光線, 其代表產生圖元的光子所採用的路徑。 這些光線可以與應用程式中的其他內容相關, 方法是從框架的座標系統取得轉換到其他的座標系統 (例如, 從[固定的參考框架](coordinate-systems.md#stationary-frame-of-reference))。 總而言之, 每個影像框架都會提供下列各項:
* 圖元資料 (RGB/NV12/JPEG/等格式)
* 從 capture 的位置[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)
* 包含相機鏡頭模式的[CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)類別

### <a name="camera-to-application-specified-coordinate-system"></a>攝影機至應用程式指定的座標系統

若要從「CameraIntrinsics」和「CameraCoordinateSystem」移至您的應用程式/全局座標系統, 您需要下列各項:

[Unity 中的定位相機](locatable-camera-in-unity.md):CameraToWorldMatrix 是由 PhotoCaptureFrame 類別自動提供 (因此您不需要擔心 CameraCoordinateSystem 轉換)。

[DirectX 中的攝影機相機](locatable-camera-in-directx.md):顯示在相機座標系統與您自己的應用程式座標系統之間查詢轉換時, 相當直接的方法。

### <a name="distortion-error"></a>失真錯誤

在 HoloLens 上, 影片和靜止影像串流會在系統的影像處理管線中 undistorted, 然後才能讓應用程式使用框架 (預覽串流包含原始的失真框架)。 由於只有 CameraIntrinsics 可供使用, 因此應用程式必須假設影像框架代表完美的 pinhole 攝影機, 不過影像處理器中的 undistortion 函式在 HoloLens (第一代) 上可能仍會保留最多10圖元的錯誤使用框架中繼資料中的 CameraIntrinsics 時。 在許多使用案例中, 此錯誤並不重要, 但如果您要將全息影像對齊真實世界的海報/標記, 而且您注意到 < 10px 位移 (大約是 11mm, 表示有2米的全息影像), 此失真錯誤可能是原因。 

## <a name="locatable-camera-usage-scenarios"></a>定位相機使用案例

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>在世界上顯示拍攝的相片或影片

裝置相機畫面格隨附「攝影機到世界」轉換, 可用來精確顯示裝置在拍攝影像時的位置。 例如, 您可以將小型的全像攝影圖示放在這個位置 (CameraToWorld. MultiplyPoint (Vector3)), 甚至在相機面向的方向繪製一個小箭號 (CameraToWorld. MultiplyVector (Vector3. forward))。

### <a name="tag--pattern--poster--object-tracking"></a>標記/模式/海報/物件追蹤

許多混合現實應用程式會使用可辨識的影像或視覺效果模式, 在空間中建立可追蹤的點。 這會接著用來呈現相對於該點的物件, 或建立已知的位置。 HoloLens 的部分用途包括尋找以 fiducials 標記的真實世界物件 (例如具有 QR 代碼的電視監視器)、將全息影像放在 fiducials 上, 以及與非 HoloLens 裝置 (如已設定為透過與 HoloLens 進行通訊的平板電腦) 進行視覺化配對Wi-fi。

若要辨識視覺效果模式, 然後將該物件放在應用程式的世界空間中, 您需要進行幾項動作:
1. 影像模式辨識工具組, 例如 QR 代碼、AR 標記、臉部搜尋工具、圓形追蹤器、OCR 等等。
2. 在執行時間收集影像框架, 並將其傳遞給辨識層
3. 將其影像位置 Unproject 回世界位置, 或可能的世界光線。 請參閱
4. 將您的虛擬模型放在這些世界位置

一些重要的影像處理連結:
* [OpenCV](http://opencv.org/)
* [QR 標記](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft 線上翻譯](https://www.microsoft.com/translator/business)

保持互動式應用程式框架速率非常重要, 特別是在處理長時間執行的影像辨識演算法時。 基於這個理由, 我們通常會使用下列模式:
1. 主要執行緒: 管理攝影機物件
2. 主要執行緒: 要求新的框架 (非同步)
3. 主要執行緒: 將新的框架傳遞至追蹤執行緒
4. 追蹤執行緒: 處理用來收集重點的影像
5. 主要執行緒: 移動虛擬模型以符合找到的關鍵點
6. 主要執行緒: 從步驟2重複

某些影像標記系統只提供單一圖元位置 (其他則會提供完整轉換, 在此情況下不需要此區段), 這等同于可能的位置光線。 若要取得單一3d 位置, 我們可以利用多個光線, 並根據其近似交集來尋找最終結果。 若要這樣做, 您必須:
1. 取得迴圈來收集多個相機影像
2. 尋找相關聯的功能點和其世界光線
3. 當您有一份功能字典, 每個都有多個世界光線時, 您可以使用下列程式碼來解決這些光線的交集:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

假設有兩個或多個追蹤標記位置, 您可以定位模型化場景, 以符合使用者目前的案例。 如果您無法假設重心, 則需要三個標記位置。 在許多情況下, 我們會使用簡單的色彩配置, 其中白色球體代表即時追蹤標記位置, 而藍色球體代表模型化標記位置, 這可讓使用者以視覺化方式測量對齊品質。 我們假設所有的應用程式都有下列設定:
* 兩個或多個模型化標記位置
* 場景中的一個「校正空間」是標記的父系
* 相機功能識別碼
* 會移動校正空間以將模型化標記與即時標記對齊的行為 (我們要小心移動父系空間, 而不是模型化標記本身, 因為其他連接是相對於它們的位置)。

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>使用 Led 或其他辨識器程式庫, 追蹤或識別已標記的固定或移動真實世界物件/臉部

範例：
* 具有 Led 的工業機器人 (或用於較慢移動物件的 QR 代碼)
* 識別和辨識房間中的物件
* 識別和辨識房間中的人員 (例如, 將全像攝影的連絡人卡片放在臉部)

## <a name="see-also"></a>另請參閱
* [DirectX 中的定位相機](locatable-camera-in-directx.md)
* [Unity 中的定位相機](locatable-camera-in-unity.md)
* [混合實境擷取](mixed-reality-capture.md)
* [適用於開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)
* [媒體捕捉簡介](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [全像臉部追蹤範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
