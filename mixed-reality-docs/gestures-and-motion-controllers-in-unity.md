---
title: Unity 中的手勢和運動控制器
description: 有兩種主要方式可對您在 Unity、右手手勢和動作控制器的注視採取動作。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手勢，動作控制器，unity，注視，輸入
ms.openlocfilehash: a7ca5a895015ba0458f0f64f1422612e797f5067
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435222"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Unity 中的手勢和運動控制器

有兩個主要的方式可[對您的](gaze-in-unity.md)目光採取行動，包括 HoloLens 和沉浸式 HMD 中的[右手手勢](gaze-and-commit.md#composite-gestures)和[運動控制器](motion-controllers.md)。 您可以透過 Unity 中的相同 Api，存取這兩個空間輸入來源的資料。

Unity 提供兩種主要方式來存取適用于 Windows Mixed Reality 的空間輸入資料、共同的*GetButton/GetAxis* api，可跨多個 Unity XR sdk 執行，以及特定的*InteractionManager/GestureRecognizer* apiWindows Mixed Reality，會公開可用的完整空間輸入資料集。

## <a name="unity-buttonaxis-mapping-table"></a>Unity 按鈕/軸對應表

在 Windows Mixed Reality 運動控制器的 Unity 輸入管理員中，透過*GetButton/GetAxis* api 支援下表中的按鈕和軸識別碼，而「windows MR-特定」資料行則是指可從下列位置取得的屬性：*InteractionSourceState*類型。 下列各節將詳細說明每個 Api。

Windows Mixed Reality 的按鈕/軸識別碼對應通常符合 Oculus go 按鈕/軸識別碼。

Windows Mixed Reality 的按鈕/軸識別碼對應與 OpenVR 的對應有兩種不同之處：
1. 對應會使用與操縱杆不同的觸控板識別碼，以支援具有 thumbsticks 和 touchpads 的控制器。
2. 對應可避免將功能表按鈕的 A 和 X 按鈕識別碼多載，讓實體的 ABXY 按鈕可以使用。

<table>
<tr>
<th rowspan="2">Input </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">通用 Unity Api</a><br />（輸入. GetButton/GetAxis） </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 特有的輸入 API</a><br />XR.WSA.源</th>
</tr><tr>
<th> 左手 </th><th> 右手</th>
</tr><tr>
<td> 已按下選取觸發程式 </td><td> 軸 9 = 1。0 </td><td> 軸 10 = 1。0 </td><td> selectPressed</td>
</tr><tr>
<td> 選取觸發程式類比值 </td><td> 軸9 </td><td> 軸10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 選取 [觸發部分已按下] </td><td> 按鈕 14 <i>（遊戲台相容性）</i> </td><td> 按鈕 15 <i>（遊戲台相容性）</i> </td><td> selectPressedAmount &gt; 0。0</td>
</tr><tr>
<td> 已按下功能表按鈕 </td><td> 按鈕 6 * </td><td> 按鈕 7 * </td><td> menuPressed</td>
</tr><tr>
<td> 已按下手柄按鈕 </td><td> 軸 11 = 1.0 （沒有類比值）<br />按鈕 4 <i>（遊戲台相容性）</i> </td><td> 軸 12 = 1.0 （沒有類比值）<br />按鈕 5 <i>（遊戲台相容性）</i> </td><td> grasped</td>
</tr><tr>
<td> 操縱杆 X <i>（左：-1.0，右：1.0）</i> </td><td> 軸1 </td><td> 軸4 </td><td> thumbstickPosition. x</td>
</tr><tr>
<td> 操縱杆 Y <i>（上：-1.0，下：1.0）</i> </td><td> 軸2 </td><td> 軸5 </td><td> thumbstickPosition. y</td>
</tr><tr>
<td> 已按下操縱杆 </td><td> 按鈕8 </td><td> 按鈕9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> 觸達 X <i>（左：-1.0，右：1.0）</i> </td><td> 軸 17 * </td><td> 軸 19 * </td><td> touchpadPosition. x</td>
</tr><tr>
<td> 觸控板 Y <i>（上方：-1.0、下：1.0）</i> </td><td> 軸 18 * </td><td> 軸 20 * </td><td> touchpadPosition. y</td>
</tr><tr>
<td> 觸及觸控板 </td><td> 按鈕 18 * </td><td> 按鈕 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> 已按下觸控板 </td><td> 按鈕 16 * </td><td> 按鈕 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 底框姿勢或指標姿勢 </td><td colspan="2"> 僅限<i>握</i>姿勢： <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> 傳遞<i>手柄</i>或<i>指標</i>做為引數： SourceState. sourcePose. TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 追蹤狀態 </td><td colspan="2"> <i>位置精確度和來源遺失風險僅可透過 MR 特定 API</i>取得 </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. properties. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>這些按鈕/軸識別碼與 Unity 用於 OpenVR 的識別碼不同，因為遊戲台、Oculus go Touch 和 OpenVR 所使用的對應發生衝突。

## <a name="grip-pose-vs-pointing-pose"></a>抓握姿勢與指標姿勢

Windows Mixed Reality 支援各種外型規格中的動作控制器，而每個控制器的設計都不同于使用者的手位置與自然「正向」方向之間的關聯性，應用程式應該在呈現時使用指標控制器.

為了更清楚地表示這些控制站，您可以針對每個互動來源來調查兩種類型的姿勢，**抓住姿勢**和**指標姿勢**。 「手柄姿勢」和「指標姿勢」座標都會以全域 Unity 全局座標中的所有 Unity Api 表示。

### <a name="grip-pose"></a>抓握姿勢

「**抓握姿勢**」代表 HoloLens 偵測到的掌上的位置，或用來存放運動控制器的 palm。

在沉浸式耳機上，抓握姿勢最適合用來**轉譯使用者手**或**使用者手中所持有的物件**，例如寶劍或機槍。 當視覺化動作控制器時，也會使用「底框姿勢」，因為適用于動作控制器的 Windows 所提供的**呈現模型**會使用「手柄姿勢」作為其原點和旋轉中心。

抓握姿勢的定義方式如下：
* **抓握位置**：以自然的來保存控制器時的 palm 距心，向左或右調整以置中的位置。 在 Windows Mixed Reality 動作控制器上，此位置通常會與 [抓住] 按鈕對齊。
* **抓握方向的右軸**：當您完全開啟手來形成一般的5方姿勢時，您的掌上的光線（從左 palm 向前、向右的 palm）
* **抓握方向的正向軸**：當您局部關閉手（如同按住控制器）時，會透過非拇指手指所形成的電子管「轉寄」光線。
* **抓握方向的向上軸**：右邊和後向定義所隱含的向上軸。

您可以透過 Unity 的跨廠商輸入 API （XR）來存取底框姿勢 *[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/輪替*），或透過 WINDOWS MR 特定 API （*SourceState. SourcePose. TryGetPosition/輪替*，要求「底框 **」節點的**姿勢資料）。

### <a name="pointer-pose"></a>指標姿勢

**指標姿勢**代表指向轉寄的控制器秘訣。

當您**呈現控制器模型本身**時，系統提供的指標姿勢最適合用來 raycast。 如果您要呈現某個其他虛擬物件來取代控制器（例如虛擬機器槍），您應該指向該虛擬物件最自然的光線，例如沿著應用程式定義的機槍模型的桶移動的光線。 由於使用者可以看到虛擬物件，而不是實體控制器，因此使用您的應用程式時，指向虛擬物件的方式可能會更自然。

目前，指標姿勢僅適用于 Unity 中的 Windows MR 特定 API *sourcePose. TryGetPosition/輪替*，傳入*InteractionSourceNode*做為引數。

## <a name="controller-tracking-state"></a>控制器追蹤狀態

就像耳機一樣，Windows Mixed Reality 運動控制器不需要設定外部追蹤感應器。 而是由耳機本身的感應器來追蹤控制器。

如果使用者將控制器移出頭戴式裝置的視野，在大部分情況下，Windows 會繼續推斷控制器位置並提供給應用程式。 當控制器已夠長的視覺效果追蹤時，控制器的位置將會降到近似的精確度位置。

此時，系統會將控制器鎖定給使用者，並在移動時追蹤使用者的位置，同時仍然使用其內部方向感應器來公開控制器的真正方向。 許多使用控制器來指向並啟動 UI 元素的應用程式，都可以正常運作，但不會察覺到使用者的精確度。

瞭解這一點的最佳方式，就是親自試試看。 請參閱這段影片，其中包含可在各種追蹤狀態下搭配運動控制器使用的沉浸式內容範例：

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>明確追蹤狀態的推理

如果應用程式想要根據追蹤狀態以不同的方式來處理位置，可能會進一步進行，並檢查控制器狀態的屬性，例如*SourceLossRisk*和*PositionAccuracy*：

<table>
<tr>
<th> 追蹤狀態 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高準確度</b> </td><td style="background-color: green; color: white"> &lt; 1。0 </td><td style="background-color: green; color: white"> [高] </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精確度（有遺失的風險）</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: green; color: white"> [高] </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>估計精確度</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>沒有位置</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: orange"> false</td>
</tr>
</table>

這些動作控制器的追蹤狀態定義如下：
* **高精確度：** 雖然動作控制器是在耳機的視野中，但它通常會根據視覺效果追蹤來提供高精確度的位置。 請注意，移動控制器會暫時離開此欄位，或從耳機感應器暫時遮蔽（例如，使用者的另一方面），會根據控制站的慣性追蹤，以較短的時間繼續傳回高準確度的姿勢直接.
* **高精確度（有遺失的風險）：** 當使用者將動作控制器移到耳機的視野邊緣上方時，耳機很快就無法以視覺方式追蹤控制器的位置。 應用程式會透過看到**SourceLossRisk**觸達1.0，得知控制器已達到此 FOV 界限。 此時，應用程式可能會選擇暫停需要穩定串流高品質姿勢的控制器手勢。
* **估計精確度：** 當控制器已夠長的視覺效果追蹤時，控制器的位置將會降到近似的精確度位置。 此時，系統會將控制器鎖定給使用者，並在移動時追蹤使用者的位置，同時仍然使用其內部方向感應器來公開控制器的真正方向。 許多使用控制器來指向並啟動 UI 元素的應用程式，都可以正常運作，而不會察覺到使用者注意到的精確度。 具有較**高**輸入需求的應用程式可能會選擇透過檢查**PositionAccuracy**屬性（例如，讓使用者在螢幕上的目標上有更大的 Hitbox），從高度準確度中瞭解這項下降**的準確度。** 在這段期間內。
* **沒有位置：** 雖然控制器可以在大概的精確度內正常運作，但有時系統會知道即使是主體鎖定的位置也不會有意義。 例如，剛開啟的控制器可能從未以視覺化方式觀察到，或使用者可能會關閉某個控制器，然後由其他人挑選。 在這些時間，系統不會提供任何位置給應用程式，而且*TryGetPosition*會傳回 false。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>通用 Unity Api （輸入. GetButton/GetAxis）

**命名空間：** *UnityEngine*、 *UnityEngine. XR*<br>
**類型**： *Input*、 *XR。InputTracking*

Unity 目前使用其一般*輸入 GetButton/GetAxis* api 來公開[Oculus go SDK](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)和 Windows Mixed Reality 的輸入，包括手和運動控制器。 如果您的應用程式使用這些 Api 來進行輸入，它可以輕鬆地支援跨多個 XR Sdk 的運動控制器，包括 Windows Mixed Reality。

### <a name="getting-a-logical-buttons-pressed-state"></a>取得邏輯按鈕的已按下狀態

若要使用一般 Unity 輸入 Api，您通常會先將按鈕和軸連接到[Unity 輸入管理員](https://docs.unity3d.com/Manual/ConventionalGameInput.html)中的邏輯名稱，並將按鈕或軸識別碼系結至每個名稱。 接著，您可以撰寫參考該邏輯按鈕/軸名稱的程式碼。

例如，若要將左側動作控制器的 [觸發程式] 按鈕對應至 [提交] 動作，請移至 [**編輯] > [專案設定] >** Unity 內的輸入，然後展開 [軸] 底下 [提交] 區段的屬性。 將 [**正整數] 按鈕**或**Alt 正按鈕**屬性變更為閱讀**搖桿按鈕 14**，如下所示：

![Unity 的 InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

接著，您的腳本可以使用*GetButton*檢查提交動作：

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
您可以藉由變更 [**軸**] 底下的 [**大小**] 屬性來新增更多邏輯按鈕。

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>直接取得實體按鈕的已按下狀態

您也可以使用*GetKey*，以其完整名稱來手動存取按鈕：

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>取得手或運動控制器的姿勢

您可以使用 XR 來存取控制器的位置和旋轉 *。InputTracking*：

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

請注意，這代表控制器的底框姿勢（使用者保有控制器的位置），這適用于在使用者手中呈現寶劍或機槍，或控制器本身的模型。

請注意，此底框和指標（控制器的秘訣指向的位置）之間的關聯性可能會在不同的控制器之間有所不同。 目前，只有透過 MR 特定的輸入 API （如下列各節所述），才可以存取控制器的指標姿勢。

## <a name="windows-specific-apis-xrwsainput"></a>Windows 特定的 Api （XR。WSA.源

**命名空間：** *UnityEngine. XR. WSA. 輸入*<br>
**類型**： *InteractionManager*、 *InteractionSourceState*、 *InteractionSource*、 *InteractionSourceProperties*、 *InteractionSourceKind*、 *InteractionSourceLocation*

若要取得有關 Windows Mixed Reality 手寫輸入（適用于 HoloLens）和動作控制器的更詳細資訊，您可以選擇使用*UnityEngine. XR*命名空間下的 windows 特定空間輸入 api。 這可讓您存取其他資訊，例如位置精確度或來源種類，讓您可以讓手和控制器分開。

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>輪詢實習和運動控制器的狀態

您可以使用*GetCurrentReading*方法，針對每個互動來源（手或動作控制器）輪詢此畫面格的狀態。

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

您取回的每個*InteractionSourceState*都代表目前當時的互動來源。 *InteractionSourceState*會公開如下的資訊：
* 發生的[按下類型](motion-controllers.md)（選取/功能表/抓住/觸控板/操縱杆）

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* 動作控制器特定的其他資料，例如觸控板和/或操縱杆的 XY 座標和觸及狀態

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* 要知道來源是手或動作控制器的 InteractionSourceKind

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>輪詢正向預測呈現的姿勢

* 當您輪詢來自手和控制器的互動來源資料時，您所得到的會是向前預測，這是在此框架的光子到達使用者眼的時間點。  這些向前預測的姿勢最適合**用來轉譯**控制器或每個框架的保留物件。  如果您以具有控制器的特定按或發行為目標，如果您使用下面所述的歷程記錄事件 Api，這會是最精確的方式。

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* 您也可以取得這個目前框架的正向預測 head 姿勢。  就像來源姿勢一樣，這對於轉譯資料指標很有用，但如果您使用下面所述的歷程記錄事件 Api，**則以指定**的長按或版本為目標會最為精確。

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>處理互動來源事件

若要在輸入事件發生時處理其正確的歷程記錄姿勢資料，您可以處理互動來源事件，而不是輪詢。

若要處理互動來源事件：
* 註冊*InteractionManager*輸入事件。 針對您感興趣的每一種互動事件，您必須訂閱它。

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* 處理事件。 當您訂閱互動事件之後，您將會在適當時取得回呼。 在*SourcePressed*範例中，這會在偵測到來源之後，以及釋放或遺失之前。

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>如何停止處理事件

當您不再對事件感興趣，或正在終結已訂閱事件的物件時，您必須停止處理事件。 若要停止處理事件，請取消訂閱事件。

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>互動來源事件的清單

可用的互動來源事件如下：
* *InteractionSourceDetected* （來源變成作用中狀態）
* *InteractionSourceLost* （變成非作用中）
* *InteractionSourcePressed* （點一下、按下按鈕或 "Select" 從未提到）
* *InteractionSourceReleased* （點一下、放開的按鈕，或 "Select" 從未提到的結尾）
* *InteractionSourceUpdated* （移動或以其他方式變更某個狀態）

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>歷程記錄目標的事件，最精確地符合「按下」或「發行」

稍早所述的輪詢 Api 會提供您的應用程式向前預測的姿勢。  雖然這些預測的姿勢最適合用來呈現控制器或虛擬掌上型物件，但基於兩個主要原因，未來的姿勢並不是最佳目標：
* 當使用者按下控制器上的按鈕時，可能會有大約20毫秒的無線延遲，然後系統才會收到按下。
* 然後，如果您要使用正向預測的姿勢，則會有另一個 10 20 毫秒的正向預測，目標是目前框架的光子會到達使用者眼睛的時間。

這表示輪詢會提供來源姿勢或 head 姿勢，這是從使用者的前端和手中，在發生按下或發行時實際回到的40毫秒。  針對 HoloLens 手寫輸入，雖然沒有無線傳輸延遲，但有類似的處理延遲可偵測按下。

若要根據使用者的原始意圖或控制器按下正確目標，您應該使用來自該*InteractionSourcePressed*或*InteractionSourceReleased*輸入事件的歷程記錄來源姿勢或 head 姿勢。

您可以使用來自使用者前端或其控制器的歷程記錄姿勢資料，以按下或發行為目標：
* 當手勢或控制器按下時的 head 姿勢，可以用來決定要[撥雲見日](gaze-and-commit.md)使用者的**目標**：

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* 當發生動作控制器按下時的來源姿勢，可以用來做為**目標**，以判斷使用者指向控制器的位置。  這會是經歷按下的控制器狀態。  如果您要轉譯控制器本身，您可以要求指標姿勢，而不是抓握姿勢，以從使用者會考慮該呈現控制器之自然提示的目標光線：

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>事件處理常式範例

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高階複合手勢 Api （GestureRecognizer）

**命名空間：** *UnityEngine. XR. WSA. 輸入*<br>
**類型**： *GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*

您的應用程式也可以辨識空間輸入來源、點按、按住、操作和導覽手勢的更高層級複合手勢。 您可以使用 GestureRecognizer，在[手](gaze-and-commit.md#composite-gestures)和[運動控制器](motion-controllers.md)上辨識這些複合手勢。

GestureRecognizer 上的每個手勢事件都會提供輸入的 SourceKind，以及事件當時的目標 head 光線。 某些事件會提供其他內容特定資訊。

使用手勢辨識器來捕獲手勢時，只需要幾個步驟：
1. 建立新的手勢辨識器
2. 指定要監看的手勢
3. 訂閱這些手勢的事件
4. 開始捕獲手勢

### <a name="create-a-new-gesture-recognizer"></a>建立新的手勢辨識器

若要使用*GestureRecognizer*，您必須已建立*GestureRecognizer*：

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>指定要監看的手勢

透過*SetRecognizableGestures （）* 指定您感興趣的手勢：

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>訂閱這些手勢的事件

針對您感興趣的手勢訂閱事件。

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>導覽和動作筆勢在*GestureRecognizer*的實例上是互斥的。

### <a name="start-capturing-gestures"></a>開始捕獲手勢

根據預設，在呼叫*StartCapturingGestures （）* 之前， *GestureRecognizer*不會監視輸入。 如果在處理*StopCapturingGestures （）* 的框架之前執行了輸入，則在呼叫*StopCapturingGestures （）* 之後，可能會產生手勢事件。 *GestureRecognizer*會記住，在實際發生手勢的 previou 畫面中，它是開啟還是關閉的，因此，根據這個畫面格的注視目標來啟動和停止手勢監視是很可靠的。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>停止捕獲手勢

若要停止手勢識別：

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>移除手勢辨識器

請記得先取消訂閱已訂閱的事件，再終結*GestureRecognizer*物件。

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>在 Unity 中呈現動作控制器模型

![動作控制器模型和 teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*運動控制器模型和 teleportation*

若要在您的應用程式中轉譯符合您的使用者所持有之實體控制器的運動控制器，並在按下各種按鈕時進行轉譯，您可以使用[Mixed Reality 工具](https://github.com/Microsoft/MixedRealityToolkit-Unity/)組中的**MotionController prefab** 。  這個 prefab 會從系統已安裝的動作控制器驅動程式，在執行時間動態載入正確的 glTF 模型。  請務必以動態方式載入這些模型，而不是在編輯器中手動加以匯入，如此一來，您的應用程式就會針對您的使用者可能會有的任何目前和未來的控制器，顯示實際精確的3D 模型。

1. 遵循[消費者入門](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)的指示下載混合的現實工具組，並將其新增至您的 Unity 專案。
2. 如果您在消費者入門步驟中將相機取代為*MixedRealityCameraParent* prefab，您就可以開始使用！  該 prefab 包含動作控制器呈現。  否則，請從 [專案] 窗格將 [*資產]/[HoloToolkit]/[輸入/Prefabs]/[MotionControllers* ] 新增至您的場景。  當使用者在場景中 teleports 時，您會想要將該 prefab 新增為任何父物件的子系，以用來移動相機，讓控制器與使用者一起使用。  如果您的應用程式不牽涉到 teleporting，只需在您場景的根目錄新增 prefab。

## <a name="throwing-objects"></a>擲回物件

在虛擬實境中擲回物件是較困難的問題，因此可能一開始就會出現。 如同大部分的實際互動，當遊戲中擲回時，它會立即明顯地中斷深度。 我們花了一些時間來思考如何代表實際的正確擲回行為，並提供一些指導方針，並透過我們的平臺更新而啟用，我們想要與您分享。

您可以在[這裡](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到建議如何執行的範例。 這個範例會遵循下列四個指導方針：
* **使用控制器的*速度*而不是位置**。 在 Windows 的11月更新中，我們在[' ' 近似 ' ' 位置追蹤狀態](motion-controllers.md#controller-tracking-state)中引進了行為變更。 處於此狀態時，將會繼續回報關於控制器的速度資訊，只要我們認為它是高精確度，通常比位置保持高的精確度長。
* **納入控制器的*角度速度*** 。 這個邏輯全部包含在 `GetThrownObjectVelAngVel` 靜態方法的 `throwing.cs` 檔案中，在上述連結的封裝內：
   1. 隨著角度的速度 conserved，所擲回的物件必須維持與擲回時相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. 因為擲回物件的範圍可能不是在抓握姿勢的原點，所以它可能會有不同的速度，而在使用者參考的框架中，控制器的速度也不一樣。 以這種方式貢獻的物件速度部分，是在控制器原點周圍，所擲回物件的即時相切速度。 此相切速度是控制器角度速度的交叉乘積，其向量代表控制器原點與所擲回物件之大量的中心之間的距離。
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. 所擲回物件的總速度就是控制器的速度和此相切速度的總和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* 請**密切注意我們套用速度的*時間*** 。 按下按鈕時，最多可能需要20毫秒該事件，才能透過藍牙向上到作業系統。 這表示，如果您輪詢控制器狀態變更，使其無法按下，或反之亦然，控制器會使用您所取得的資訊，實際上會在這項變更的狀態之前。 此外，我們的輪詢 API 所呈現的控制器會向前預測，以反映在畫面顯示時可能會有的姿勢，未來可能會有更多的20毫秒。 這適合用來*呈現*持有的物件，但是會在使用者釋放其擲回的時間點時，將我們的目標問題放在我們的*目標*物件上。 幸運的是，在11月更新中，當*InteractionSourcePressed*或*InteractionSourceReleased*等 Unity 事件傳送時，狀態會在按鈕實際按下或放開時，包含背景的歷程記錄資料。  若要在擲回時取得最精確的控制器轉譯和控制器目標，您必須適當地使用輪詢和事件：
   * 對於**呈現**每個畫面格的控制器，您的應用程式應該將控制器的*GameObject*置於目前框架 photon 時間的正向預測控制器上。  您會從 Unity 輪詢 Api （例如 XR）取得此資料 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。WSA.輸入. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* 。
   * 針對以按下或發行為**目標的控制器**，您的應用程式應該根據該按下或釋放事件的歷程控制器姿勢來 raycast 和計算軌跡。  您會從 Unity 事件 Api 取得此資料，例如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 。
* **使用抓握姿勢**。 角度的速度和速度會相對於抓握姿勢（而不是指標姿勢）來報告。

擲回會繼續改善未來的 Windows 更新，您可以在這裡找到更多相關資訊。

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>MRTK v2 中的手勢和運動控制器

您可以從輸入管理員存取手勢和動作控制器。 
* [MRTK v2 中的手勢](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [MRTK v2 中的運動控制器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>遵循教學課程

混合現實學術提供逐步教學課程，其中包含更詳細的自訂範例：

- [MR 輸入211：手勢](holograms-211.md)
- [MR 輸入213：動作控制器](mixed-reality-213.md)

[![MR 輸入 213-運動控制器](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR 輸入 213-運動控制器*

## <a name="see-also"></a>請參閱

* [頭部目光和行動](gaze-and-commit.md)
* [運動控制器](motion-controllers.md)


