---
title: 之外的可尋獲相機
description: HoloLens 前方相機、 其運作方式，和設定檔的一般資訊和開發人員可使用的解決方式。
author: wguyman
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: 相機、 hololens、 色彩相機、 面向、 hololens 2，cv，電腦視覺，fiducial 前端、 標記、 qr 代碼、 qr、 相片、 視訊
ms.openlocfilehash: cadcd0762b8adf1001896c614451d2e1c9776c65
ms.sourcegitcommit: 79398a6b5b7037babcb05d86a5bcc336fd089ea0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028609"
---
# <a name="locatable-camera"></a>之外的可尋獲相機

HoloLens 包含可讓應用程式，以查看使用者會看到裝置的正面掛接世界相機。 開發人員可以存取及控制相機，就像智慧型手機、 portables 或桌上型電腦上的色彩相機。 相同的通用 windows[媒體擷取](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)和 HoloLens 上的 windows 媒體基礎作用於行動和桌面的 Api 運作。 Unity[也已包裝這些 windows Api](locatable-camera-in-unity.md)抽取 HoloLens 上的相機，進行工作，例如採用一般的相片和視訊 （不論有無全像投影），並尋找中的鏡頭位置和檢視方塊上的簡單使用方式場景。

## <a name="device-camera-information"></a>裝置相機資訊

### <a name="hololens-first-generation"></a>HoloLens （第一代）

* 已修正的焦點相片/影片 (PV) 相機白色自動平衡、 自動曝光，與完整的映像處理管線。
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

* 自動焦點相片/影片 (PV) 相機白色自動平衡、 自動曝光，與完整的映像處理管線。
* 觀景窗作用中時，會位於面向世界的白色隱私權 LED。
* HoloLens 2 支援不同的相機設定檔。 了解如何[探索並選取相機功能](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles)。
* 相機支援下列設定檔和 （所有的視訊模式是 16:9 外觀比例） 的解決方法：
  
  | 設定檔                                         | 視訊     | 預覽   | 仍     | 畫面播放速率 | 水平視野 (H FOV) | 建議的用法                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy,0  BalancedVideoAndPhoto,100             | 2272x1278 | 2272x1278 |           | 15,30       | 64.69                            | 高品質的視訊錄製                |
  | Legacy,0  BalancedVideoAndPhoto,100             |           |           | 3904x2196 |             | 64.69                            | 高品質拍攝相片                  |
  | BalancedVideoAndPhoto,120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15,30       | 64.69                            | 持續時間較長的案例                     |
  | BalancedVideoAndPhoto,120                       | 1504x846  | 1504x846  |           | 15,30       | 64.69                            | 持續時間較長的案例                     |
  | 視訊會議 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | 視訊會議，持續時間較長的案例 |
  | 視訊會議 100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | 視訊會議，持續時間較長的案例 |
  | 視訊會議，100 BalancedVideoAndPhoto 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | 視訊會議，持續時間較長的案例 |
  | 視訊會議，100 BalancedVideoAndPhoto 120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | 視訊會議，持續時間較長的案例 |
  | 視訊會議，100 BalancedVideoAndPhoto 120 | 1128x635  |           |           | 15,30       | 64.69                            | 視訊會議，持續時間較長的案例 |
  | 視訊會議，100 BalancedVideoAndPhoto 120 | 960x540   |           |           | 15,30       | 64.69                            | 視訊會議，持續時間較長的案例 |
  | 視訊會議，100 BalancedVideoAndPhoto 120 | 760x428   |           |           | 15,30       | 64.69                            | 視訊會議，持續時間較長的案例 |
  | 視訊會議，100 BalancedVideoAndPhoto 120 | 640x360   |           |           | 15,30       | 64.69                            | 視訊會議，持續時間較長的案例 |
  | 視訊會議，100 BalancedVideoAndPhoto 120 | 500x282   |           |           | 15,30       | 64.69                            | 視訊會議，持續時間較長的案例 |
  | 視訊會議，100 BalancedVideoAndPhoto 120 | 424x240   |           |           | 15,30       | 64.69                            | 視訊會議，持續時間較長的案例 |

>[!NOTE]
>客戶可以利用[混合實境擷取](mixed-reality-capture.md)拍攝影片或應用程式，包括全像投影和視訊穩定的相片。
>
>身為開發人員，有一些您應該考慮建立您的應用程式，如果您想要客戶擷取內容時的外觀可能不如時的考量。 您可以也啟用 （和自訂） 直接在您的應用程式內的混合的實境擷取。 深入了解[開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)。

## <a name="locating-the-device-camera-in-the-world"></a>尋找裝置相機在全局

當 HoloLens 將相片和視訊時，擷取的畫面格會包含世界裡，以及將觀景窗的遠近景深投射觀景窗的位置。 如此應用程式的原因需觀景窗的位置，在真實世界的增強型映像的案例。 開發人員更多時間可以復原自己的案例使用其慣用的映像處理或自訂電腦視覺文件庫。

「 虛擬遊戲觀景窗 」 （位在範圍的應用程式呈現給） 可能參考 「 攝影機 」 HoloLens 文件中的其他位置。 否則表示，除非此頁面上的"相機 」 指的是實際 RGB 色彩相機。

在此頁面的外殼的詳細資料[Media Foundation 屬性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)，不過也有提取相機內建函式使用的 Api [WinRT Api](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics)。  

### <a name="images-with-coordinate-systems"></a>與座標系統的映像

每個影像框架 (是否相片或視訊) 包含座標系統，以及兩個重要的轉換。 「 檢視 」 轉換從數位相機，以提供的座標系統的對應和相機中的 「 投射 」 對應至映像中的像素。 在一起，這些轉換定義每個像素無限遠的光線表示所產生的像素 photons 採取的路徑的 3D 空間中。 這些光線可以藉由從畫面格的座標系統中取得轉換至其他的座標系統相關的應用程式中的其他內容 (例如從[靜態參考座標系](coordinate-systems.md#stationary-frame-of-reference))。 總結來說，每個影像框架提供下列功能：
* 像素格式的資料 （RGB/NV12 JPEG/等等）
* 中繼資料的 3 個片段 (儲存為[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx))，讓每個畫面格 」 之外的可尋獲 」:

|  屬性名稱  |  類型  |  GUID  |  描述 | 
|----------|----------|----------|----------|
|  MFSampleExtension_Spatial_CameraCoordinateSystem  |  IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))  |  {9D13C82F-2199-4E67-91CD-D1A4181F2534}  |  存放區[座標系統](coordinate-systems-in-directx.md)的擷取的畫面格 | 
|  MFSampleExtension_Spatial_CameraViewTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {4E251FA4-830F-4770-859A-4B8D99AA809B}  |  將相機的外建轉換存放在座標系統 | 
|  MFSampleExtension_Spatial_CameraProjectionTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {47F9FCB5-2A02-4F26-A477-792FDF95886A}  |  將相機的投影轉換 | 

投影轉換表示對應到從-1 延伸至 + 1 X 和 Y 軸中的映像平面 功能濾鏡的內建屬性 （焦距，投射的中心扭曲）。

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

不同的應用程式會有不同的座標系統。 以下是流程的要找出相機像素的單一應用程式概觀：

![轉換套用到數位相機座標系統](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a>應用程式指定的座標系統的相機

若要從 'CameraView' 和 'CameraCoordinateSystem' 前往您的應用程式/全局座標系統，您將需要下列項目：

[在 Unity 中的可以找到相機](locatable-camera-in-unity.md):CameraToWorldMatrix 自動 PhotoCaptureFrame 類別提供 （因此您不需要擔心 CameraCoordinateSystem 轉換）。

[DirectX 之外的可尋獲觀景窗](locatable-camera-in-directx.md):顯示相機的座標系統與您自己的應用程式 coordinate system(s) 之間轉換的查詢相當簡單的方式。

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a>應用程式指定座標系統，以像素座標

例如，假設您想要尋找] 或 [繪製在指定的 3d 位置上的相機映像：

檢視和投影轉換，這兩個的 4x4 矩陣時需要使用方式稍有不同。 也就是之後執行投影，其中會 「 正規化的 w 」，這個額外的步驟，在投射中模擬如何將多個不同的 3d 位置的最後可能會做為相同的 2d 位置 （也就是沿著某些光線的任何項目會顯示在相同的像素） 在螢幕上。 因此重點 （在著色器程式碼）：

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a>應用程式指定的座標系統的像素

要全局座標從像素就比較困難：

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

我們在其中定義為 UnProject:

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

若要尋找某個點的實際世界位置，您將需要： 兩個世界光線並尋找其交集，或是已知的點的大小。

### <a name="distortion-error"></a>扭曲錯誤

上 HoloLens、 影片和仍然影像資料流是 undistorted 系統的映像處理管線中之前的畫面格都會提供給應用程式 （預覽資料流包含原始的扭曲的框架）。 投影矩陣可供使用，因為應用程式必須假設影像框架代表完美 pinhole 相機，不過 undistortion 函式中的映像處理器可能仍保留最多 10 個像素為單位的錯誤時使用投影矩陣中框架的中繼資料。 在許多使用案例，此錯誤就不重要，但如果您對齊全像投影至真實世界海報/標記，比方說，而且您會注意到 < 10px 位移 (大致上位於遠 2 公尺全像投影 11 mm) 此扭曲錯誤可能是原因。

## <a name="locatable-camera-usage-scenarios"></a>之外的可尋獲相機使用方式案例

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>顯示相片或視訊擷取世界

裝置相機框架隨附的"相機來 World 」 轉換，可用來顯示完全裝置的擷取映像時。 比方說您無法放置小型全像攝影版圖示，此位置 （CameraToWorld.MultiplyPoint(Vector3.zero)) 和甚至是繪製方向，相機當時正面臨 (CameraToWorld.MultiplyVector(Vector3.forward)) 小箭號。

### <a name="painting-the-world-using-a-camera-shader"></a>繪製世界使用相機著色器

這一節我們將建立材料 '著色器' 世界為基礎，它顯示在裝置相機的檢視中的色彩。 我們要有效地為每個頂點會找出其與數位相機，相對的位置，然後每個像素會利用投影矩陣圖放大哪一個映像相關聯的材質。 最後，並選擇性地，我們會淡出的映像，讓它顯示更多類似的夢想的記憶體：

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

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
2. 尋找[相關聯的功能點](#pixel-to-application-specified-coordinate-system)，和他們的世界光線
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

### <a name="render-holograms-from-the-cameras-position"></a>呈現全像投影從相機的位置

注意:如果您嘗試建立您自己[混合實境擷取 (MRC)](mixed-reality-capture.md)，其中混合使用相機的資料流全像投影，您可以使用[MRC 效果](mixed-reality-capture-for-developers.md)] 或 [啟用中的 showHolograms 屬性[在 Unity 中的可以找到相機](locatable-camera-in-unity.md)。

如果您想要直接在 RGB 相機串流上的特殊轉譯，就可以呈現全像投影觀景窗的位置從空間中的視訊摘要與同步，以提供自訂的全像錄製/即時預覽。

Skype，目的是要顯示遠端用戶端 HoloLens 使用者所查看的內容，並允許它們與相同全像投影互動。 在傳送之前透過 Skype 服務每個視訊的範圍內，我們抓取每個畫面格的相對應的相機資料。 我們接著，封裝使用視訊畫面格相機的外建和內建函式中繼資料，然後透過 Skype 服務。

在接收端，使用 Unity，我們已同步處理所有全像投影中使用相同的座標系統的 HoloLens 使用者的空間。 這可讓我們使用相機的外建中繼資料來將 Unity 數位相機放在 HoloLens 使用者已釐時擷取視訊框架，（相對於全像投影的其餘部分） 世界中的確切位置，並使用相機內建函式的資訊來請確定檢視相同。

一旦擁有已正確地設定網路攝影機，我們會結合觀景窗會看到我們收到來自 Skype，建立的混合的實境檢視 HoloLens 使用者會看到使用 Graphics.Blit 框架到何種全像投影。

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
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
