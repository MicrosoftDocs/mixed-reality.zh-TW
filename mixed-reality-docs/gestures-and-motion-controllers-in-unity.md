---
title: 筆勢和 Unity 中的動作控制站
description: 有兩種主要的方式，在您的視線 Unity、 手勢和動作控制站上採取動作。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 筆勢、 動作控制站、 unity、 視線，輸入
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591149"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>筆勢和 Unity 中的動作控制站

有兩種主要的方式採取行動您[視線中 Unity](gaze-in-unity.md)，[交給筆勢](gestures.md)並[動作控制器](motion-controllers.md)。 您透過相同的 Api，在 Unity 中存取這兩個來源的空間的輸入資料。

Unity 提供兩種主要的方式來存取空間的輸入的資料的 Windows Mixed Reality，常見*Input.GetButton/Input.GetAxis*可跨多個 Unity XR Sdk，Api 和*InteractionManager /GestureRecognizer*公開可用的空間輸入資料的一組完整的 Windows Mixed Reality 專屬的 API。

## <a name="unity-buttonaxis-mapping-table"></a>Unity 按鈕/軸對應表

下表中的按鈕和軸識別碼支援 Unity 的輸入管理員 中的 Windows Mixed Reality 動作控制站*Input.GetButton/GetAxis* Api，而 「 Windows MR 專屬"的資料行參考屬性都*InteractionSourceState*型別。 在下列各節中詳細說明每個這些 Api。

Windows Mixed Reality 的按鈕/軸識別碼對應通常會符合 Oculus 按鈕/軸識別碼。

Windows Mixed Reality 的按鈕/軸識別碼對應不同 OpenVR 的對應，有兩種：
1. 對應會使用觸控板 Id 不同於搖桿，來支援使用搖桿和跳動的控制站。
2. 對應可避免多載 A 和 X 按鈕的功能表按鈕時，若要讓這些可用的實體 ABXY 按鈕的識別碼。

<table>
<tr>
<th rowspan="2">Input </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">常見的 Unity Api</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR 特定輸入的 API</a><br />(XR.WSA.Input)</th>
</tr><tr>
<th> 左邊 </th><th> 右下</th>
</tr><tr>
<td> 按下選取的觸發程序 </td><td> 軸 9 = 1.0 </td><td> 軸 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> 選取觸發程序類比值 </td><td> 軸 9 </td><td> 軸 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 選取部分已按下的觸發程序 </td><td> 按鈕 14 <i>（遊戲台相容性）</i> </td><td> 按鈕 15 <i>（遊戲台相容性）</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> 已按下功能表按鈕 </td><td> 按鈕 6 * </td><td> 按鈕 7 * </td><td> menuPressed</td>
</tr><tr>
<td> 已按下的底框按鈕 </td><td> 11 = 1.0 （未類比的值） 軸<br />按鈕 4 <i>（遊戲台相容性）</i> </td><td> 12 = 1.0 （未類比的值） 軸<br />按鈕 5 <i>（遊戲台相容性）</i> </td><td> grasped</td>
</tr><tr>
<td> 搖桿 X <i>(左:-1.0，正確：1.0)</i> </td><td> 軸 1 </td><td> 軸 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> 搖桿 Y <i>(top:-1.0，底部：1.0)</i> </td><td> 軸 2 </td><td> 軸 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> 按下的搖桿 </td><td> 按鈕 8 </td><td> 按鈕 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> 觸控板 X <i>(左:-1.0，正確：1.0)</i> </td><td> 軸 17 * </td><td> 軸 19 * </td><td> touchpadPosition.x</td>
</tr><tr>
<td> 觸控板 Y <i>(top:-1.0，底部：1.0)</i> </td><td> 軸 18 * </td><td> 軸 20 * </td><td> touchpadPosition.y</td>
</tr><tr>
<td> 接觸到的觸控板 </td><td> 按鈕 18 * </td><td> 按鈕 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> 按下觸控板 </td><td> 按鈕 16 * </td><td> 按鈕 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 底框姿勢或指標姿勢 </td><td colspan="2"> <i>調整底框</i>只造成：<a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> 傳遞<i>底框</i>或是<i>指標</i>做為引數： sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 追蹤狀態 </td><td colspan="2"> <i>位置精確度和來源遺失風險只能透過 MR 特定 API</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>這些按鈕/軸識別碼不同於 Unity 使用 OpenVR 因為舵 Oculus 觸控和 OpenVR 所使用的對應發生衝突的識別碼。

## <a name="grip-pose-vs-pointing-pose"></a>指標的姿勢與的底框姿勢

Windows Mixed Reality 支援各種不同的外型規格中的動作控制站，與每個控制站設計不同使用者的手狀位置和 「 轉送 」 方向該應用程式的自然之間關聯性的相對值應該使用指出呈現時控制站。

為了更能代表這些控制站，有兩種您可以調查每個互動來源，會帶來**底框姿勢**並**指標姿勢**。 全域 Unity 的全局座標中的所有 Unity Api 來表示這兩個的底框姿勢和指標姿勢座標。

### <a name="grip-pose"></a>調整底框姿勢

**底框姿勢**表示偵測到的 HoloLens，一隻手的或翲保存動作控制器的位置。

沈浸式耳機，在底框姿勢最適合用來呈現**使用者的手**或是**物件保留在使用者的手**劍或槍等。 將顯示為動作控制站時，也會使用的底框姿勢**可呈現模型**提供所移動的 Windows 控制站，請使用做為其原始並旋轉的中心點的底框姿勢。

調整底框姿勢定義具體來說，如下所示：
* **抓住位置**:Palm 距心自然，保留控制器時調整左邊或右邊，置中的底框的位置。 在 Windows Mixed Reality 動作控制站，這個位置通常配合掌握 按鈕。
* **抓住方向的右座標軸**:當您完全開啟以形成平坦的 5 手指姿勢手時，光線，一般是您 palm （從左 palm、 從右 palm 回溯順向）
* **抓住方向的順向軸**:當您關閉您的手部分 （如同保存在控制站）、"forward"tube 透過由非 thumb 手指點光線。
* **抓住方向的總軸**:隱含的權限和轉送的定義總軸。

您可以透過任一 Unity 的跨銷售商輸入的 API 來存取的底框姿勢 (*[XR。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation*) 或透過 Windows MR 特定 API (*sourceState.sourcePose.TryGetPosition/Rotation*，要求會造成資料**底框**節點)。

### <a name="pointer-pose"></a>指標姿勢

**指標姿勢**表示向前指的控制站的提示。

系統提供的指標姿勢最適合用於 raycast 完**轉譯控制器模型本身**。 如果您要呈現其他某些虛擬物件，來控制站，例如虛擬的砲，取代您應該點是最方便的該虛擬物件，例如傳輸的應用程式定義槍模型鸃庢餂沿著光線的光線。 因為使用者可以看到虛擬物件並不是實體的控制器，指向與虛擬物件可能會對於使用您的應用程式更自然。

指標姿勢目前可在 Unity 中只透過 Windows MR 特定 API *sourceState.sourcePose.TryGetPosition/Rotation*，並傳入*InteractionSourceNode.Pointer*為引數。

## <a name="controller-tracking-state"></a>控制器追蹤狀態

耳機，像是 Windows Mixed Reality 動作控制站不需要任何設定的外部追蹤感應器。 相反地，控制器會追蹤耳機本身中的感應器。

如果使用者移出耳機的視野，控制站，在大部分情況下 Windows 會推斷控制站的位置，並將其提供給應用程式繼續。 當控制器失去 visual 追蹤身體力行，控制站的位置將會卸除到近似精確度的位置。

此時，系統會主體鎖定給使用者時，追蹤使用者的位置，同時仍公開使用其內部的方向感應器的控制站，則為 true 的方向移動，控制站。 許多應用程式會使用控制器，以指向，並啟用 UI 項目可以正常運作近似值的精確度在使用者的演算法而不會。

若要瞭解這個，最好是親自試試看。 請參閱這段影片中使用控制器動作適用於各種追蹤狀態的沈浸式內容的範例：

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>明確地追蹤狀態的來龍去脈

想要將位置根據追蹤狀態的應用程式可能可以更進一步，並檢查控制器的狀態的屬性，例如*SourceLossRisk*並*PositionAccuracy*:

<table>
<tr>
<th> 追蹤狀態 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高精確度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>（有遺失資料的風險） 的高精確度</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>近似值的精確度</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>沒有位置</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: orange"> false</td>
</tr>
</table>

這些動作的控制器追蹤狀態定義，如下所示：
* **高精確度：** 耳機的視野內移動控制站時，它通常會提供高精確度的位置，以視覺化的追蹤。 請注意，移動的控制站，會暫時離開檢視欄位或暫時遮蔽耳機感應器 (例如，藉由使用者的相反) 會繼續傳回高精確度會帶來一小段時間，以控制站的慣性追蹤它本身。
* **（有遺失資料的風險） 的高精確度：** 當使用者移動超過的耳機的視野邊緣的移動控制站時，耳機將推出無法以視覺方式追蹤控制站的位置。 應用程式可讓您知道當控制器時，已藉由查看達到此 FOV 界限**SourceLossRisk**觸達 1.0。 此時，應用程式可以選擇暫停需要非常高品質會帶來的穩定資料流的控制站筆勢。
* **近似值的精確度：** 當控制器失去 visual 追蹤身體力行，控制站的位置將會卸除到近似精確度的位置。 此時，系統會主體鎖定給使用者時，追蹤使用者的位置，同時仍公開使用其內部的方向感應器的控制站，則為 true 的方向移動，控制站。 許多應用程式會使用控制器，以指向，並啟用 UI 項目可以做為一般的時間近似值的精確度在使用者的演算法而不會。 較輸入需求的應用程式可能會選擇感測從這個下拉式**高**精確度**近似**藉由檢查精確度**PositionAccuracy**屬性，如讓使用者更多的 hitbox 幕外的目標在這段時間的範例。
* **不到位置：** 控制器可長時間操作近似值的精確度，而有時系統知道，甚至主體鎖定的位置目前不具意義。 例如，只是開啟的控制站可能永遠不會觀察到在視覺上，或使用者可能會讓下一個控制站，然後挑選其他人。 在這些時間，系統將不會提供任何位置，應用程式，並*TryGetPosition*會傳回 false。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>常見的 Unity Api (Input.GetButton/GetAxis)

**命名空間：***UnityEngine*， *UnityEngine.XR*<br>
**型別**:*輸入*， *XR。InputTracking*

Unity 目前使用其一般*Input.GetButton/Input.GetAxis* Api 來公開 （expose） 輸入[Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)， [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)和 Windows Mixed Reality，包括雙手及動作控制站。 如果您的應用程式會使用這些 Api 的輸入，它可以輕鬆地跨多個 XR Sdk，包括 Windows Mixed Reality 中支援動作控制站。

### <a name="getting-a-logical-buttons-pressed-state"></a>取得邏輯按鈕已按下的狀態

若要使用一般的 Unity 輸入 Api，您將一開始通常會連接按鈕和中的邏輯名稱的座標軸[Unity 輸入管理員](https://docs.unity3d.com/Manual/ConventionalGameInput.html)，繫結至每個名稱的軸識別碼或按鈕。 然後，您可以撰寫程式碼，是指該邏輯的按鈕軸名稱。

例如，若要對應左的動作控制器的觸發程序] 按鈕送出動作，請前往**編輯 > 專案設定 > 輸入**Unity 內展開的送出區段的 [軸屬性。 變更**正值按鈕**或**Alt 正按鈕**屬性，以讀取**搖桿按鈕 14**，如下所示：

![Unity 的 InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

提交動作使用，可以接著選取您的指令碼*Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
您可以加入多個邏輯的按鈕，變更**大小**下方的屬性**軸**。

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>直接取得的實體按鈕已按下的狀態

您也可以存取按鈕以手動方式由其完整名稱，並使用*Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>取得手形或動作控制器的姿勢

您可以存取的位置和旋轉的控制器，使用*XR。InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

請注意，這代表控制器的底框姿勢 （使用者按住控制器），這很適合用於轉譯的拉鋸或槍中使用者的手的形狀或控制站本身的模型。

請注意，此調整底框姿勢 （其中指控制站的提示） 的指標姿勢之間的關聯性可能不同於各控制站。 目前，存取控制器的指標姿勢才可以透過 MR 特有的輸入下列各節中所述的 API。

## <a name="windows-specific-apis-xrwsainput"></a>Windows 特定的 Api (XR。WSA。輸入）

**命名空間：***UnityEngine.XR.WSA.Input*<br>
**型別**:*InteractionManager*， *InteractionSourceState*， *InteractionSource*， *InteractionSourceProperties*， *InteractionSourceKind*， *InteractionSourceLocation*

若要取得在 Windows Mixed Reality 手動輸入 （HoloLens) 和動作控制器的詳細資訊，，您可以在其中選擇 Windows 專屬空間輸入的 Api 之下*UnityEngine.XR.WSA.Input*命名空間。 這可讓您存取其他資訊，例如位置精確度或的來源類型，可讓您告訴雙手及控制站的位置。

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>輪詢雙手及動作控制器的狀態

您可以針對每個互動來源 （手動或動作的控制器） 使用此畫面格的狀態來輪詢*GetCurrentReading*方法。

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

每個*InteractionSourceState*您取得上一步 表示的互動來源在目前時間的時間。 *InteractionSourceState*公開資訊，例如：
* 這[種類的按下](motion-controllers.md)發生 （選取/功能表/掌握/觸控板/搖）

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* 其他資料特定動作控制站，這類觸控板和/或搖桿的 XY 座標和接觸的狀態

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* 若要知道來源是否為手形或移動控制站 InteractionSourceKind

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>正向預測的轉譯會帶來輪詢

* 輪詢互動來源資料是來自雙手及控制站，您取得帶來時轉寄預測帶來的此框架 photons 當觸達使用者的眼睛的時間。  這些順向預測會帶來最適合用於**轉譯**控制器或保留物件的每個畫面格。  如果您要為目標指定按下或釋放與控制站，這會是最精確，如果您使用歷程記錄的事件如下所述的 Api。

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* 您也可以取得順向預測前端姿勢這個目前的框架。  因為與來源姿勢中，這是適用於**轉譯**的資料指標，雖然會最精確，如果您使用歷程記錄的事件如下所述的 Api 以指定按下或版本為目標。

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

若要處理輸入的事件，與其正確的歷程記錄姿勢資料發生時，您可以處理互動來源事件，而非輪詢。

若要處理互動來源事件：
* 報名*InteractionManager*輸入的事件。 每一種您感興趣的互動事件中，您需要訂閱。

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* 處理事件。 一旦您已訂閱互動事件，您會在適當的回呼。 在  *SourcePressed*範例中，這將會偵測到來源後之前它會釋出或遺失。

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

您需要停止處理的事件，當您不再感興趣的事件，或已終結訂閱事件的物件。 若要停止處理事件，您取消訂閱事件。

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>互動來源事件清單

可用的互動來源事件如下：
* *InteractionSourceDetected* （來源成為使用中）
* *InteractionSourceLost* （變成非使用中）
* *InteractionSourcePressed* （點選、 按下按鈕，或"Select"玩具店）
* *InteractionSourceReleased* （結尾點選、 按鈕釋放或 「 Select 」 您知道的結尾）
* *InteractionSourceUpdated* （移動或變更某些狀態）

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>歷程記錄的目標會帶來最能精確符合在按下或發行的事件

稍早所述的輪詢 Api 可讓您的應用程式正向預測會帶來。  這些預測會帶來最適合呈現的控制器或虛擬的掌上型物件時，未來會帶來並非最適合用於搜尋的目標，兩個索引鍵的原因：
* 當使用者按下按鈕，控制站上時，可能會有約 20 毫秒的延遲無線透過藍牙之前，系統即會按。
* 接著，如果您使用順向預測的姿勢，那里會向前預測的另一個 10-20 毫秒套用至目標目前的框架 photons 當觸達使用者的眼睛的時間。

這表示輪詢可讓您的來源姿勢，或標頭會造成也就是從使用者的前端和指針實際所在回發生在按下或發行的 30 40 毫秒正向。  HoloLens 手動輸入，雖然沒有任何無線傳輸的延遲，沒有類似的處理延遲，以偵測按。

至正確的目標根據使用者的原意，手動或控制站的按下，您應該使用歷程記錄的來源姿勢或從該前端姿勢*InteractionSourcePressed*或*InteractionSourceReleased*輸入的事件。

您可以按下的目標或發行來自使用者的大腦或其控制站的歷程記錄的姿勢資料：
* 發生在動作或控制器按時間前端的姿勢，它可以用於**目標**來判斷使用者的已[gazing](gaze.md)在：

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

* 發生在當按下動作控制站時間來源姿勢，它可以用於**目標**來判斷哪些使用者指位於的控制站。  這會發生按下控制器的狀態。  如果您要轉譯控制器本身，您可以要求指標姿勢，而不是調整底框姿勢，以傳送目標的光跡從哪些使用者會考慮呈現控制器的自然提示：

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高階複合筆勢 Api (GestureRecognizer)

**命名空間：***UnityEngine.XR.WSA.Input*<br>
**型別**:*GestureRecognizer*， *GestureSettings*， *InteractionSourceKind*

您的應用程式，也可以識別較高層級的空間輸入的來源，點選，按住不放、 操作和瀏覽筆勢的複合筆勢。 您可以將這些複合的筆勢辨識在兩者之間[手](gestures.md)並[動作控制器](motion-controllers.md)使用 GestureRecognizer。

GestureRecognizer 上的每個動作事件會提供輸入為目標的前端光線 SourceKind，當時的事件。 某些事件提供額外內容的特定資訊。

有只擷取筆勢使用筆勢辨識器所需的幾個步驟：
1. 建立新的筆勢辨識器
2. 指定要監看的筆勢
3. 訂閱事件，這些筆勢
4. 開始擷取筆勢

### <a name="create-a-new-gesture-recognizer"></a>建立新的筆勢辨識器

若要使用*GestureRecognizer*，您必須建立*GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>指定要監看的筆勢

指定您感興趣透過的筆勢*SetRecognizableGestures()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>訂閱事件，這些筆勢

訂閱手勢您感興趣的事件。

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
>瀏覽和操作筆勢是互斥的執行個體上*GestureRecognizer*。

### <a name="start-capturing-gestures"></a>開始擷取筆勢

根據預設， *GestureRecognizer*不會監視輸入直到*StartCapturingGestures()* 呼叫。 很可能筆勢事件可能會產生後*StopCapturingGestures()* 若輸入執行之前框架則會呼叫所在*StopCapturingGestures()* 已處理。 *GestureRecognizer*是否筆勢實際發生的在 previou 畫面格期間是開啟或關閉因此很可靠地啟動及停止筆勢監視根據目標設為此框架的視線會記住。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>停止擷取筆勢

若要停止建置手勢辨識：

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>移除的筆勢辨識器

請務必從訂閱的事件取消訂閱，然後再終結*GestureRecognizer*物件。

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>轉譯在 Unity 中的移動控制器模型

![動作控制器模型和屏障](images/motioncontrollertest-teleport-1000px.png)<br>
*動作控制器模型和屏障*

若要轉譯符合實體的控制站，您的使用者會保存，並且清楚表達如不同按鈕按下您的應用程式中的動作控制站，您可以使用**MotionController prefab**在[混合實境工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  此 prefab 會從系統的安裝的動作控制器的驅動程式，以動態方式載入正確 glTF 模型，在執行階段。  請務必以動態方式載入這些模型，而不是手動匯入它們在編輯器中，這樣您的應用程式會顯示實際的精確的 3D 模型，任何目前和未來的控制站，您的使用者可能會有。

1. 請遵循[開始使用](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)指示下載混合實境工具組，並將它新增至您的 Unity 專案。
2. 如果您更換使用相機*MixedRealityCameraParent* prefab 的快速入門步驟的一部分，您已就緒 ！  該 prefab 包含移動控制站的轉譯。  否則，請新增*Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab*您從 [專案] 窗格在場景。  您會想要新增為任何父物件的子系 prefab 您用來移動相機繞著時使用者 teleports 內場景，以便控制站附隨的使用者。  如果您的應用程式並不包含 teleporting，只要新增 prefab 場景的根目錄。

## <a name="throwing-objects"></a>擲回物件

在虛擬實境中擲回物件是困難的問題，則一開始看起來似乎。 如同最實際根據互動，以預期的方式在遊戲會擲回時，它會立即一目暸然，並且中斷訓練活動。 我們花了一些時間來思考深如何代表實體上正確的擲回行為，並提供一些指導方針，啟用透過我們的平台，我們想要與您共用的更新。

您可以找到舉例來說，我們建議您如何實作擲回[此處](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)。 此範例會遵循下列四個的指導方針：
* **使用控制器*速度*而不是位置**。 在 Windows 的 11 月更新，我們引進了行為的變更在['近似' 位置追蹤狀態](motion-controllers.md#controller-tracking-state)。 處於此狀態時，速度控制器的相關的資訊會繼續報告，只要我們相信它是高精確度，這通常是超過會保持高精確度的位置。
* **併入*角速度*控制站的**。 此邏輯都包含在`throwing.cs`檔案中`GetThrownObjectVelAngVel`上述連結的套件內的靜態方法：
   1. 因為角速度是節約，擲回的物件必須維持相同的 angular 速度，因為它會擲回目前有： `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. 因為可能不在底框姿勢原點，可能有不同的速度的話，則的控制站在使用者的參照時，會擲回物件的中心的大量。 以這種方式提供的物件的部分是大量的速度的擲回物件控制器原點為中心的中心的即時略微相關速度。 此略微相關的速度是物件的角速度控制站，與代表控制器原點及中央的大型的擲回之間的距離的向量的交叉乘積。
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. 擲回總數速度，因此是物件的控制站的速度和此略微相關的速度的總和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **密切注意*時間*我們可以在其中套用速度**。 按下按鈕時，可能需要針對該事件，以反昇，以透過藍芽作業系統最多 20 毫秒。 這表示，如果未按下按下的輪詢從控制器狀態變更或控制站的姿勢資訊您開始之前的狀態這項變更將相反的情況，會。 此外，以反映在框架將會顯示在未來可能在多個然後 20 毫秒的時間可能姿勢向前預測我們輪詢 API 所提供的控制器姿勢。 這適用於*轉譯*持有的物件，但複合的時間問題*目標*物件，我們目前為止計算軌跡使用者發行其擲回。 幸運的是，使用年 11 月更新時，Unity 事件何時*InteractionSourcePressed*或*InteractionSourceReleased*傳送，狀態包括歷程記錄的姿勢資料從備份時的按鈕已實際已按下或發行。  若要取得最精確的控制站呈現和期間擲回的控制站為目標，您正確地必須適當地使用輪詢和事件處理:
   * 針對**控制器轉譯**每個畫面中，您的應用程式應該放置控制器的*GameObject*轉寄預測控制站會造成目前的框架 photon 時間。  您可以取得這項資料從輪詢的 Api，例如的 Unity *[XR。InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或是 *[XR。WSA。Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。
   * 針對**控制器目標**在按下或版本中，您的應用程式應該 raycast 並計算滴下根據歷程記錄的控制器姿勢，按下] 或 [發行事件。  您收到這項資料從 Unity 事件處理 Api，例如 *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。
* **使用調整底框姿勢**。 角速度和速度會報告相對於底框姿勢，而不是指標姿勢。

擲回將繼續改善未來的 Windows 更新，並取得更多有關它以下時，您可以預期。

## <a name="accelerate-development-with-mixed-reality-toolkit"></a>利用混合實境 Toolkit 加速開發

有關於 InputManager 和 MotionController Unity 中的兩個範例場景。 透過這些場景中，您可以了解如何使用 MRTK 的 InputManager 和從動作控制器按鈕存取的資料處理事件。

- [HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [讀我檔案的技術詳細資料](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

![輸入的範例 MRTK 場景](images/MRTK_ExampleScene_Input.png)<br>
*輸入的範例 MRTK 場景*

### <a name="automatic-scene-setup"></a>自動的場景設定

當您匯入[MRTK 發行 Unity 套件](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或從專案複製[GitHub 存放庫](https://github.com/Microsoft/MixedRealityToolkit-Unity)，您要在 Unity 中尋找新的功能表 ' 混合實境 Toolkit'。 在 [設定] 功能表上，您會看到功能表 [適用於混合實境場景設定]。 當您按一下它時，它會移除預設相機，並新增基本元件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，並[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。

![MRTK 場景設定功能表](images/MRTK_Input_Menu.png)<br>
*MRTK 場景設定功能表*

![自動的場景中 MRTK 的安裝程式](images/MRTK_HowTo_Input1.png)<br>
*自動的場景中 MRTK 的安裝程式*

### <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefab

您可以手動新增這些從 [專案] 面板。 您可以找到 prefabs 這些元件。 當您搜尋**MixedRealityCamera**，您將能夠看到兩個不同的數位相機 prefabs。 差別在於**MixedRealityCamera**才相機 prefab 而**MixedRealityCameraParent**包含沈浸式耳機，例如屏障，動作的其他元件控制器和，界限。

![在 MRTK 相機 prefabs](images/MRTK_HowTo_Input2.png)<br>
*在 MRTK 相機 prefabs*

**MixedRealtyCamera**支援 HoloLens 和沈浸式耳機。 它會偵測到的裝置類型，並最佳化清除旗標和天空盒等屬性。 以下您可以找到一些有用的屬性，您可以自訂游標，移動控制器模型，例如自訂和樓層。

![屬性的動作控制站中，資料指標和樓層](images/MRTK_HowTo_Input3.png)<br>
*屬性的動作控制站中，資料指標和樓層*

## <a name="follow-along-with-tutorials"></a>依照本教學課程

逐步教學課程中，使用更詳細的自訂範例，可在混合實境 Academy:

- [MR 輸入 211:筆勢](holograms-211.md)
- [MR 輸入 213:動作控制站](mixed-reality-213.md)

[![MR 輸入 213-動作控制站](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR 輸入 213-動作控制站*

## <a name="see-also"></a>另請參閱

* [筆勢](gestures.md)
* [動作控制站](motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [InteractionInputSource.cs MixedRealityToolkit Unity 中](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
