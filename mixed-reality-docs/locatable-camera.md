---
title: 之外的可尋獲相機
description: HoloLens 前方相機、 其運作方式，和設定檔的一般資訊和開發人員可使用的解決方式。
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: 相機、 hololens、 色彩相機前端向
ms.openlocfilehash: f661fc82fbeab9a870e8ccf7044c9bb375bed7e3
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326295"
---
# <a name="locatable-camera"></a>之外的可尋獲相機

HoloLens 包含可讓應用程式，以查看使用者會看到裝置的正面掛接世界相機。 開發人員可以存取及控制相機，就像智慧型手機、 portables 或桌上型電腦上的色彩相機。 相同的通用 windows[媒體擷取](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)和 HoloLens 上的 windows 媒體基礎作用於行動和桌面的 Api 運作。 Unity[也已包裝這些 windows Api](locatable-camera-in-unity.md)抽取 HoloLens 上的相機，進行工作，例如採用一般的相片和視訊 （不論有無全像投影），並尋找中的鏡頭位置和檢視方塊上的簡單使用方式場景。

## <a name="device-camera-information"></a>裝置相機資訊

### <a name="hololens-first-generation"></a>HoloLens （第一代）

* 已修正的焦點相片/影片 (PV) 相機，白色自動平衡、 自動曝光，與完整的映像處理管道
* 面向世界的白色隱私權 LED 將會位於相機作用中時
* 相機支援下列模式 （所有模式都是 16:9 外觀比例） 在 30、 24、 20、 15 及 5 的 fps:

  |  視訊  |  預覽  |  仍  |  水平視野 (H FOV) |  建議的用法 | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  （透過視訊穩定功能的預設模式） | 
  |  N/A |  N/A |  2048x1152 |  67deg |  最高的解析度靜止影像 | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  溢出掃描 （填補） 解析度視訊穩定功能之前 | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  使用溢出掃描大型 FOV 視訊模式 | 
  |  896x504 |  896x504 |  896x504 |  48deg |  低電源 / 映像的低解析度模式處理工作 | 

### <a name="hololens-2"></a>HoloLens 2

* 自動焦點相片/影片 (PV) 相機，白色自動平衡、 自動曝光，與完整的映像處理管道
* 面向世界的白色隱私權 LED 將會位於相機作用中時
* 相機支援 （所有的視訊模式是 16:9 外觀比例） 的模式如下：

  >[!NOTE]
  >這些模式會有所 HoloLens 2 正式運作之前的變更。

  |  視訊  |  預覽  |  仍  |  畫面播放速率  |  水平視野 (H FOV) |  建議的用法 | 
  |----------|----------|----------|----------|----------|----------|
  |  1920x1080 |  1920x1080 |  N/A |  30、 15 的 fps  |  54deg  |  （透過視訊穩定功能的預設模式） | 
  |  N/A |  N/A |  3904X2196 |  N/A  |  64deg |  最高的解析度靜止影像 | 
  |  2272x1278 |  2272x1278 |  N/A |  30、 15 的 fps  |  64deg |  溢出掃描 （填補） 解析度視訊穩定功能之前 | 
  |  1952x1100 |  1952x1100 |  1952x1100  |  30、 15 的 fps  |  64deg |  高品質的串流處理 | 
  |  1280x720 |  1280x720 |  N/A |  30、 15、 5 的 fps  |  64deg |  針對串流和映像處理工作的低電源/解決模式 | 

## <a name="locating-the-device-camera-in-the-world"></a>尋找裝置相機在全局

當 HoloLens 將相片和視訊時，擷取的畫面格會包含觀景窗位置世界裡，以及功能濾鏡模型觀景窗。 如此應用程式的原因需觀景窗的位置，在真實世界的增強型映像的案例。 開發人員更多時間可以復原自己的案例使用其慣用的映像處理或自訂電腦視覺文件庫。

「 虛擬遊戲觀景窗 」 （位在範圍的應用程式呈現給） 可能參考 「 攝影機 」 HoloLens 文件中的其他位置。 否則表示，除非此頁面上的"相機 」 指的是實際 RGB 色彩相機。

此頁面涵蓋使用的詳細資料[MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference)類別，不過也有 Api 提取相機內建函式和使用的位置[Media Foundation 屬性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)。 請參閱[全像攝影版的臉部追蹤範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)如需詳細資訊。

### <a name="images-with-coordinate-systems"></a>與座標系統的映像

每個影像框架 (是否相片或視訊) 包含[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)根目錄使用可存取的擷取時在觀景窗[CoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)屬性您[MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)。 此外，每個畫面格會包含描述的相機功能濾鏡模型中找到這些[CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)屬性。 在一起，這些轉換定義每個像素無限遠的光線表示所產生的像素 photons 採取的路徑的 3D 空間中。 這些光線可以藉由從畫面格的座標系統中取得轉換至其他的座標系統相關的應用程式中的其他內容 (例如從[靜態參考座標系](coordinate-systems.md#stationary-frame-of-reference))。 總結來說，每個影像框架提供下列功能：
* 像素格式的資料 （RGB/NV12 JPEG/等等）
* A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)從擷取的位置
* A [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)包含觀景窗的功能濾鏡模式類別

### <a name="camera-to-application-specified-coordinate-system"></a>應用程式指定的座標系統的相機

若要從 'CameraIntrinsics' 和 'CameraCoordinateSystem' 前往您的應用程式/全局座標系統，您將需要下列項目：

[在 Unity 中的可以找到相機](locatable-camera-in-unity.md):CameraToWorldMatrix 自動 PhotoCaptureFrame 類別提供 （因此您不需要擔心 CameraCoordinateSystem 轉換）。

[DirectX 之外的可尋獲觀景窗](locatable-camera-in-directx.md):顯示相機的座標系統與您自己的應用程式 coordinate system(s) 之間轉換的查詢相當簡單的方式。

### <a name="distortion-error"></a>扭曲錯誤

上 HoloLens、 影片和仍然影像資料流是 undistorted 系統的映像處理管線中之前的畫面格都會提供給應用程式 （預覽資料流包含原始的扭曲的框架）。 因為只有 CameraIntrinsics 可供使用，應用程式必須假設影像框架代表完美 pinhole 相機，不過 undistortion 函式中的映像處理器可能仍保留最多 10 個像素為單位的錯誤 HoloLens 上 （第一代）當使用 CameraIntrinsics 框架中繼資料中。 在許多使用案例，此錯誤就不重要，但如果您對齊全像投影至真實世界海報/標記，比方說，而且您會注意到 < 10px 位移 (大致上位於遠 2 公尺全像投影 11 mm) 此扭曲錯誤可能是原因。 

## <a name="locatable-camera-usage-scenarios"></a>之外的可尋獲相機使用方式案例

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>顯示相片或視訊擷取世界

裝置相機框架隨附的"相機來 World 」 轉換，可用來顯示完全裝置的擷取映像時。 比方說您無法放置小型全像攝影版圖示，此位置 （CameraToWorld.MultiplyPoint(Vector3.zero)) 和甚至是繪製方向，相機當時正面臨 (CameraToWorld.MultiplyVector(Vector3.forward)) 小箭號。

### <a name="tag--pattern--poster--object-tracking"></a>標記 / 模式 / 海報 / 物件追蹤

許多混合的實境應用程式會使用可辨識的映像或視覺化模式在空間上建立可追蹤點。 這再用來呈現物件的相對點，或建立一個已知的位置。 HoloLens 的部分用法包括的尋找真實世界物件加上 fiducials （例如有 QR 代碼的電視監視器）、 透過 fiducials，放置全像投影和視覺上已安裝程式，以透過 HoloLens 與通訊的平板電腦等的非 HoloLens 裝置配對Wi-fi。

若要識別其視覺化的模式，並再將該物件放在應用程式世界空間，您將需要幾件事：
1. 映像模式辨識工具組，例如 QR 代碼、 AR 標記、 臉部 finder、 圓形追蹤器、 OCR 等等。
2. 收集的影像框架，在執行階段，並將其傳遞至辨識層
3. Unproject 回世界位置或可能的世界光線其映像位置。 請參閱
4. 將您的虛擬模型放在這些全球位置

一些重要的映像處理的連結：
* [OpenCV](http://opencv.org/)
* [QR 標記](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

保留的互動式應用程式畫面播放速率很重要，特別是在處理長時間執行影像辨識演算法。 因此我們通常會使用下列模式：
1. 主執行緒： 管理相機物件
2. 主執行緒： 要求新的框架 （非同步）
3. 主執行緒： 將新的畫面格傳遞給追蹤的執行緒
4. 追蹤執行緒： 處理序映像，以收集關鍵點
5. 主執行緒： 移動的虛擬模式，以符合找到的關鍵點
6. 重複步驟 2 中的主執行緒：

有些映像標記系統僅提供單一像素的位置 (其他人提供完整的轉換在此情況下這一節將不需要)，這等同於無限遠的光線可能的位置。 若要移至單一的 3d 位置我們可以利用多個光線並尋找其大約的交集的最終結果。 若要這樣做您將需要：
1. 取得迴圈會收集多個相機的映像
2. 尋找關聯的功能點和他們的世界光線
3. 當您有的功能，每個都有多個世界的光線，字典時您可以使用下列程式碼來解決這些光線交集：

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

您可以指定兩個或多個追蹤的標記位置，來定位 modelled 的場景依據使用者目前的案例。 如果您不能假設重力，您將需要三個標記位置。 在許多情況下，我們會使用簡單的色彩配置，其中的白色置放的球體表示即時追蹤標記的位置，藍色置放的球體代表模型化的標記的位置，這可讓使用者以視覺方式量測計的對齊方式的品質。 我們假設我們所有的應用程式中的下列設定：
* 兩個或多個模型化的標籤位置
* 其中一個 「 敃櫆空間 」，也在場景中就是父項的標記
* 相機功能識別項
* 移動對齊 （很謹慎地移動父空間，而不 modelled 標記本身，因為其他 connect 是相對於它們的位置） 的即時標記 modelled 的標記的校正空間的行為。

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

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>追蹤或識別標記的靜止或移動真實世界物件/字體使用 Led 或辨識器的其他程式庫

範例：
* 工業機器人，各有 Led （或緩慢移動的 QR 代碼的物件）
* 找出並辨識在聊天室中的物件
* 找出並辨識空間 （例如進行全像攝影版連絡人卡片透過臉部） 中的人員

## <a name="see-also"></a>另請參閱
* [DirectX 中的定位相機](locatable-camera-in-directx.md)
* [Unity 中的定位相機](locatable-camera-in-unity.md)
* [混合實境擷取](mixed-reality-capture.md)
* [適用於開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)
* [媒體擷取簡介](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [全像攝影版的臉部追蹤範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
