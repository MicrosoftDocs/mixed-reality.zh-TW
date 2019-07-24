---
title: 運動控制器
description: 混合現實運動控制器的詳細資料。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 控制器, 動作控制器
ms.openlocfilehash: fc6b0dcf7f338224af9ea9bc59e07187c33adda2
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024549"
---
# <a name="motion-controllers"></a>運動控制器

運動控制器是[硬體配件](hardware-accessories.md), 可讓使用者在混合現實中採取行動。 透過[手勢](gestures.md)的動作控制器的優點是控制器在空間上具有精確的位置, 可讓您更精細地與數位物件互動。 對於 Windows Mixed Reality 沉浸式耳機, 動作控制器是使用者在其世界中採取行動的主要方式。

![Windows Mixed Reality 運動控制器](images/winmr-ck-1080x1080-350px.jpg)


## <a name="device-support"></a>裝置支援

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>功能</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
</tr>
<tr>
     <td>運動控制器</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>硬體詳細資料

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

Windows Mixed Reality 運動控制器使用沉浸式頭戴式裝置中的感應器, 在您的觀點中提供精確且快速的移動追蹤, 這表示不需要在空間中的牆上安裝硬體。 這些動作控制器會提供與 Windows Mixed Reality 沉浸式耳機一樣容易的設定和可攜性。 我們的裝置合作夥伴計畫在此假期的零售貨架上市場並銷售這些控制器。

![瞭解您的控制器](images/controllerimage-750px.png)<br>
*瞭解您的控制器*

**功能**
* 光學追蹤
* 觸發程序
* 抓取按鈕
* 上下
* 觸控板

## <a name="setup"></a>安裝程式

### <a name="before-you-begin"></a>開始之前

**您將需要:**
* 一組兩個動作控制器。
* 四顆 AA 電池。
* 能夠使用 Bluetooth 4.0 的電腦。

**檢查 Windows、Unity 和驅動程式更新**
* 請造訪安裝適用于 Windows、Unity 等慣用版本的[工具](install-the-tools.md), 以進行混合的事實開發。
* 請確定您擁有最新的[耳機和動作控制器驅動程式](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)。

### <a name="pairing-controllers"></a>配對控制器

您可以使用像是任何其他 Bluetooth 裝置的 Windows 設定, 將動作控制器與主機電腦進行相互綁定。

1. 將 2 AA 電池插入控制器的背面。 立即讓電池蓋掉。
2. 如果您使用的是外部 USB 藍牙介面卡, 而不是內建的藍牙無線電, 請先參閱[藍牙最佳作法](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices), 再繼續進行。 針對具有內建收音機的桌面設定, 請確定天線已連線。
3. 開啟 [ **Windows 設定** -> ] [**裝置** -> ] [**新增藍牙] 或 [其他裝置** -> ] [**藍牙**], 並移除任何先前的 [動作控制器–右側] 和 [移動控制器–左方] 的實例。 另請核取清單底部的 [其他裝置] 類別。
4. 選取 [**新增藍牙或其他裝置**], 並查看其開始探索藍牙裝置。
5. 按住控制器的 [Windows] 按鈕, 在 buzzes 後開啟控制器。
6. 按住 [配對] 按鈕 (電池區間中的索引標籤), 直到 Led 開始閃爍。
7. 等候 [動作控制器-Left] 或 [運動控制器-Right] 顯示在清單的底部。 選取以配對。 連線時, 控制器會震動一次。

   ![選取要配對的動作控制器, 如果多個實例從清單底部選取一個](images/450px-bluetooth-add-a-device-300px.png)<br>
   *選取「動作控制器」以配對;如果有多個實例, 請從清單底部選取一個。*
   
8. 您會在 [**滑鼠、鍵盤、& 畫筆] 類別**底下的 [藍牙設定] 中, 看到控制器顯示為 [**已連線**]。 此時, 您可能會取得固件更新–請參閱[下一節](motion-controllers.md#updating-controller-firmware)。
9. 重新附加電池蓋。
10. 針對第二個控制器重複步驟1-9。

成功配對這兩個控制器之後, 您的設定在 **[滑鼠、鍵盤、& 畫筆] 類別**之下看起來應該像這樣 

   ![已連線的運動控制器](images/450px-motion-controller-connected-300px.png)<br>
   *已連線的運動控制器*

如果控制器在配對後關閉, 其狀態會顯示為 [已配對]。 如果控制器維持在 [其他裝置] 之下, 則可能只有部分完成, 而且需要再次執行才能讓控制器正常運作。

### <a name="updating-controller-firmware"></a>正在更新控制器固件

* 如果沉浸式耳機已連接到您的電腦, 而且有新的控制器固件可供使用, 則在下一次開啟時, 將會自動將該固件推送至您的動作控制器。 控制器固件更新是以圓形的發光 LED 象限模式來表示, 而且需要1-2 分鐘的時間。
* 在固件更新完成後, 控制器將會重新開機並重新連線。 這兩個控制器都應該立即連線。 
    
    ![已連線的控制器](images/cyk-connected-300px.jpg)<br>
    *在藍牙設定中連接的控制器*

* 確認您的控制器正常運作:
    1. 啟動**Mixed Reality 入口網站**, 並輸入您的混合現實首頁。
    2. 移動您的控制器並確認追蹤、測試按鈕, 並確認[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)可以運作。 如果沒有, 則請查看[動作控制器的疑難排解](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)。

## <a name="gazing-and-pointing"></a>撥雲見日和指向

Windows Mixed Reality 支援兩種主要模型以進行互動、**注視和認可**, 以及**點對認可**:
* 在**注視和認可**的情況下, 使用者會以其[注視](gaze.md)的物件為目標, 然後選取具有手中的物件、遊戲台、clicker 或聲音。
* 有了**point 和 commit**, 使用者就可以將具有點功能的運動控制器放在目標物件上, 然後選取具有控制器觸發程式的物件。

支援指向動作控制器的應用程式也應該在可能的情況下啟用駕駛間互動, 讓使用者選擇他們所使用的輸入裝置。

### <a name="managing-recoil-when-pointing"></a>在指向時管理 recoil

當使用動作控制器來指向並認可時, 您的使用者會使用控制器來設定目標, 然後藉由提取其觸發程式來採取動作。 提取觸發程式 vigorously 的使用者, 最後可能會在其觸發程式提取結束時, 讓控制器的意圖高於預期。

若要管理使用者提取觸發程式時可能發生的任何這類 recoil, 當觸發程式的類比軸值高於0.0 時, 您的應用程式可以貼齊其目標光線。 然後, 只要在短時間內發生最後一個按下的情況, 您就可以在觸發程式值達到1.0 之後, 使用目標光線的某些框架來採取動作。 當使用較高層級的[複合點手勢](gestures.md#composite-gestures)時, Windows 將會為您管理此目標光線捕捉和超時時間。

## <a name="grip-pose-vs-pointing-pose"></a>抓握姿勢與指標姿勢

Windows Mixed Reality 支援各種外型規格中的動作控制器, 而每個控制器的設計都不同于使用者的手位置與自然「正向」方向之間的關聯性, 應用程式應該在呈現時使用指標控制器.

為了更清楚地表示這些控制站, 您可以針對每個互動來源來調查兩種類型的姿勢,**抓住姿勢**和**指標姿勢**。

### <a name="grip-pose"></a>抓握姿勢

「**抓握姿勢**」代表 HoloLens 偵測到的掌上的位置, 或用來存放運動控制器的 palm。

在沉浸式耳機上, 抓握姿勢最適合用來轉譯使用者手或**使用者手中所持有的物件**, 例如寶劍或機槍。 當視覺化動作控制器時, 也會使用「底框姿勢」, 因為適用于動作控制器的 Windows 所提供的**呈現模型**會使用「手柄姿勢」作為其原點和旋轉中心。

抓握姿勢的定義方式如下:
* **抓握位置**:自然地保留控制器時的 palm 距心, 會向左或右調整以置中的位置。 在 Windows Mixed Reality 動作控制器上, 此位置通常會與 [抓住] 按鈕對齊。
* **抓握方向的右軸**:當您完全開啟手來形成一般的5方姿勢時, 您的 palm 的光線 (從左 palm 向前, 向右的 palm 往後)
* **抓握方向的正向軸**:當您關閉手中的部分 (如同按住控制器) 時, 就會以非拇指手指所形成的電子管「轉送」光線。
* **抓握方向的向上軸**:右邊和後向定義所隱含的向上軸。

### <a name="pointer-pose"></a>指標姿勢

**指標姿勢**代表指向轉寄的控制器秘訣。

當您**呈現控制器模型本身**時, 系統提供的指標姿勢最適合用來 raycast。 如果您要呈現某個其他虛擬物件來取代控制器 (例如虛擬機器槍), 您應該指向該虛擬物件最自然的光線, 例如沿著應用程式定義的機槍模型的桶移動的光線。 由於使用者可以看到虛擬物件, 而不是實體控制器, 因此使用您的應用程式時, 指向虛擬物件的方式可能會更自然。

## <a name="controller-tracking-state"></a>控制器追蹤狀態

就像耳機一樣, Windows Mixed Reality 運動控制器不需要設定外部追蹤感應器。 而是由耳機本身的感應器來追蹤控制器。

如果使用者將控制器移出頭戴式裝置的視野, 在大部分情況下, Windows 會繼續推斷控制器位置並提供給應用程式。 當控制器已夠長的視覺效果追蹤時, 控制器的位置將會降到近似的精確度位置。

此時, 系統會將控制器鎖定給使用者, 並在移動時追蹤使用者的位置, 同時仍然使用其內部方向感應器來公開控制器的真正方向。 許多使用控制器來指向並啟動 UI 元素的應用程式, 都可以正常運作, 但不會察覺到使用者的精確度。

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>明確追蹤狀態的推理

如果應用程式想要根據追蹤狀態以不同的方式來處理位置, 可能會進一步進行, 並檢查控制器狀態的屬性, 例如 SourceLossRisk 和 PositionAccuracy:

<table>
<tr>
<th> 追蹤狀態 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高準確度</b> </td><td style="background-color: green; color: white"> &lt;1。0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精確度 (有遺失的風險)</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>估計精確度</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>沒有位置</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: orange"> false</td>
</tr>
</table>



這些動作控制器的追蹤狀態定義如下:
* **高精確度:** 雖然動作控制器是在耳機的視野中, 但它通常會根據視覺效果追蹤來提供高精確度的位置。 請注意, 移動控制器會暫時離開此欄位, 或從耳機感應器暫時遮蔽 (例如, 使用者的另一方面), 會根據控制站的慣性追蹤, 以較短的時間繼續傳回高準確度的姿勢直接.
* **高精確度 (有遺失的風險):** 當使用者將動作控制器移到耳機的視野邊緣上方時, 耳機很快就無法以視覺方式追蹤控制器的位置。 應用程式會透過看到**SourceLossRisk**觸達 1.0, 得知控制器已達到此 FOV 界限。 此時, 應用程式可能會選擇暫停需要穩定串流高品質姿勢的控制器手勢。
* **估計精確度:** 當控制器已夠長的視覺效果追蹤時, 控制器的位置將會降到近似的精確度位置。 此時, 系統會將控制器鎖定給使用者, 並在移動時追蹤使用者的位置, 同時仍然使用其內部方向感應器來公開控制器的真正方向。 許多使用控制器來指向並啟動 UI 元素的應用程式, 都可以正常運作, 而不會察覺到使用者注意到的精確度。 具有較高輸入需求的應用程式可能會選擇透過檢查**PositionAccuracy**屬性 (例如, 讓使用者在螢幕上的目標上有更大的 Hitbox), 從**高度**準確度中瞭解這項下降的準確度。在這段期間內。
* **沒有位置:** 雖然控制器可以在大概的精確度內正常運作, 但有時系統會知道即使是主體鎖定的位置也不會有意義。 例如, 剛開啟的控制器可能從未以視覺化方式觀察到, 或使用者可能會關閉某個控制器, 然後由其他人挑選。 在這些時間, 系統不會提供任何位置給應用程式, 而且**TryGetPosition**會傳回 false。

## <a name="interactions-low-level-spatial-input"></a>互動低層級的空間輸入

跨手和運動控制器的核心互動包括**選取**、**功能表**、**抓住**、**觸控板**、**操縱杆**和**首頁**。
* **選取**[是] 可啟動全息影像的主要互動, 其中包含按下 [發行] 的一個。 針對 [動作控制器], 您可以使用控制器的觸發程式來執行選取 [按下]。 執行選取的其他方式是說[語音命令](voice-input.md)「選取」。 您可以在任何應用程式中使用相同的選取互動。 請將 Select 視為滑鼠點擊的對等, 這是您一次學習的通用動作, 然後套用到所有應用程式。
* **功能表**是在物件上作用的次要互動, 用來提取內容功能表或採取其他次要動作。 與動作控制站，您可以採取功能表動作，使用控制器的 *功能表* 按鈕。 (也就是它上有漢堡「功能表」圖示的按鈕)
* 瞭解使用者可以如何直接對物件採取動作來操作。 有了「動作控制器」, 您可以透過緊密地擠壓第一個來進行一項理解動作。 動作控制器可能會偵測到具有抓取按鈕、palm 觸發程式或其他感應器的。
* **觸控板**可讓使用者在動作控制器的觸控板介面上調整兩個維度中的動作, 並按一下觸控板上的 [向下] 來認可動作。 Touchpads 提供按下的狀態, 觸及狀態和標準化的 XY 座標。 X 和 Y 的範圍是從-1 到1之間的圓形觸控板範圍, 中間有 (0, 0)。 對於 X,-1 是在左邊, 1 位在右邊。 針對 Y,-1 位於底部, 而1位在頂端。
* 「**操縱杆**」可讓使用者在其迴圈範圍內移動動作控制器的操縱杆, 以調整兩個維度中的動作, 然後按一下操縱杆上的 [向下] 來認可動作。 Thumbsticks 也會提供已按下的狀態和正規化的 XY 座標。 X 和 Y 的範圍是從-1 到1之間的圓形觸控板範圍, 中間有 (0, 0)。 對於 X,-1 是在左邊, 1 位在右邊。 針對 Y,-1 位於底部, 而1位在頂端。
* **Home**是特殊的系統動作, 可用來返回 [開始] 功能表。 這類似于在鍵盤上按下 Windows 鍵, 或在 Xbox 控制器上按 Xbox 按鈕。 您可以在動作控制器上按下 [Windows] 按鈕來前往首頁。 請注意, 您也可以說「嗨, Cortana, Go Home」來開始。 應用程式無法特別針對家庭動作做出反應, 因為這些是由系統處理。

## <a name="composite-gestures-high-level-spatial-input"></a>複合手勢:高階空間輸入

兩者 [交給筆勢](gestures.md) 和動作控制站可以追蹤經過一段時間，來偵測一組常用的高階 **[複合筆勢](gestures.md#composite-gestures)** 。 這可讓您的應用程式偵測到高階的點**按、按住**、**操作**和**導覽**手勢, 無論使用者是使用手或控制器。

## <a name="rendering-the-motion-controller-model"></a>呈現動作控制器模型

**3d 控制器模型**Windows 讓應用程式可以使用系統中目前作用中的每個動作控制器的呈現模型。 藉由讓您的應用程式在執行時間以動態方式載入並表達這些系統提供的控制器模型, 您可以確保您的應用程式與任何未來的控制器設計都具有向前相容性。

這些呈現模型都應該在控制器的把手**姿勢**上轉譯, 因為模型的原點會與實體世界中的這個點對齊。 如果您要轉譯控制器模型, 則您可能會想要從**指標姿勢**raycast 到您的場景, 這表示該控制器的實體設計, 這代表使用者自然預期會指向的光線。

如需如何在 Unity 中以動態方式載入控制器模型的詳細資訊, 請參閱在[unity 中呈現動作控制器模型](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity)一節。

**2d 控制器線條美工圖案**雖然我們建議您將應用程式內控制器的秘訣和命令附加至應用程式內的控制器模型本身, 但有些開發人員可能會想要在一般「教學課程」或「操作方法」 UI 中使用動作控制器的2D 素描標記法。 針對這些開發人員, 我們製作了 png 動作控制器的線狀圖檔案 (以滑鼠右鍵按一下以儲存)。

![動作控制器的預覽線條美工圖案](images/motioncontrollers-black-preview-300px.png)

 [' ' ' 白色 ' ' ' 中的完整解析度動作控制器線條美工圖案](images/motioncontrollers-white.png)
 
 [全解析度的動作控制器 ' ' ' 中的線條美工圖案黑色 ' ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>常見問題集

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>我可以將運動控制器配對到多部電腦嗎？

動作控制器支援與單一電腦配對。 依照[動作控制器設定](motion-controllers.md#setup)的指示來配對您的控制器。

### <a name="how-do-i-update-motion-controller-firmware"></a>如何? 更新動作控制器固件？

動作控制器固件是耳機驅動程式的一部分, 並會在必要時自動在連線時更新。 根據藍牙無線電和連結品質, 固件更新通常需要1-2 分鐘的時間。 在罕見的情況下, 控制器固件更新可能需要最多10分鐘的時間, 這可能表示藍牙連線能力或無線電干擾不佳。 請參閱[愛好者指南中的藍牙最佳作法](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices), 以針對連線問題進行疑難排解。 在固件更新之後, 控制器將會重新開機並重新連線至主機電腦 (您可能會注意到 Led 會使其變亮以進行追蹤)。 如果固件更新中斷 (例如, 控制器失去電源), 則會在下一次控制器開機時再次嘗試。

### <a name="how-i-can-check-battery-level"></a>如何檢查電池等級？

在[Windows Mixed Reality 首頁](navigating-the-windows-mixed-reality-home.md)中, 您可以將控制器開啟, 以查看其在虛擬模型反向的電池計量。 沒有實體電池層級指示器。

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>您是否可以在沒有頭戴式裝置的情況下使用這些控制器？ 只針對搖桿/觸發程式/etc 輸入嗎？

不適用於通用 Windows 應用程式。

## <a name="troubleshooting"></a>疑難排解

請參閱愛好者指南中的[動作控制器疑難排解](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)。

## <a name="filing-motion-controller-feedbackbugs"></a>歸檔動作控制器的意見反應/bug

使用「混合現實-> 輸入」類別, 提供意見反應中樞的[意見](give-us-feedback.md)反應。

## <a name="see-also"></a>另請參閱
* [Unity 中的筆勢和運動控制器](gestures-and-motion-controllers-in-unity.md)
* [DirectX 中的手部和運動控制器](hands-and-motion-controllers-in-directx.md)
* [筆勢](gestures.md)
* [MR Input 213：運動控制器](mixed-reality-213.md)
* [愛好者指南:您的 Windows Mixed Reality 首頁](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [愛好者指南:在 Windows Mixed Reality 中使用遊戲 & 應用程式](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [內建追蹤的運作方式](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
