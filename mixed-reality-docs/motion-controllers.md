---
title: 動作控制站
description: 在混合實境動作控制站上的詳細資料。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 控制器、 動作控制站
ms.openlocfilehash: fc6b0dcf7f338224af9ea9bc59e07187c33adda2
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024549"
---
# <a name="motion-controllers"></a>動作控制站

動作控制器[硬體附屬應用程式](hardware-accessories.md)方便在混合實境中採取動作的使用者。 透過動作控制器的優點[筆勢](gestures.md)是控制器有精確空間中的位置，以便進行更細緻的互動，以數位物件。 針對 Windows Mixed Reality 沈浸式耳機，移動控制器會是使用者將會在他們的世界採取動作的主要方式。

![Windows Mixed Reality 動作控制站](images/winmr-ck-1080x1080-350px.jpg)


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
     <td>動作控制站</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>硬體詳細資料

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

Windows Mixed Reality 動作控制站提供精確且回應迅速的沈浸式耳機，這表示不需要安裝在您的空間牆上的硬體中使用的感應器，在欄位的檢視中移動的追蹤。 這些動作控制站會提供安裝和可攜性，為 Windows Mixed Reality 沈浸式耳機一樣容易。 裝置合作夥伴計劃行銷和銷售零售架子上的這些控制器此假日。

![了解您的控制器](images/controllerimage-750px.png)<br>
*了解您的控制器*

**功能：**
* 光學追蹤
* 觸發程序
* 擷取按鈕
* 搖桿
* 觸控板

## <a name="setup"></a>安裝程式

### <a name="before-you-begin"></a>開始之前

**您必須：**
* 兩個動作控制器的一組。
* 四個 AA 電池。
* 支援的藍芽 4.0 的電腦。

**檢查 Windows、 Unity 及驅動程式更新**
* 請瀏覽[安裝工具](install-the-tools.md)慣用版本的 Windows，Unity 等混合的實境開發。
* 請確定您有最新[耳機式和移動控制器驅動程式](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)。

### <a name="pairing-controllers"></a>配對的控制站

動作控制站可以聯結與主機電腦使用任何其他藍芽裝置的 Windows 設定。

1. 插入控制器背面的 2 個 AA 電池。 現在讓電池封面。
2. 如果您使用外部 USB 藍芽介面卡，而不內建的藍芽無線電，請檢閱[藍芽最佳作法](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)後再繼續。 對於擁有內建的桌面設定，請確定天線連接。
3. 開啟**Windows 設定** -> **裝置** -> **新增藍芽或其他裝置** -> **藍芽** ，並移除任何先前的執行個體，「 動作控制站 – 權限 」 和 「 動作控制站 – 左 」。 也請檢查其他清單底部的 [裝置] 類別。
4. 選取 **新增藍芽或其他裝置**見報開始探索藍芽裝置。
5. 按住不放，控制站的 Windows 按鈕，以開啟控制器，發行一次它 buzzes。
6. 按住不放配對按鈕 （電池區間中的索引標籤），直到 Led 開始閃爍。
7. 等候 「 動作控制站-左 」 或 「 動作控制器-權限 」 清單的底部顯示。 選取此選項，進行配對。 連線時，會一次震動控制器。

   ![如果多個執行個體從選取清單中出現的底部，選取動作控制站進行配對，](images/450px-bluetooth-add-a-device-300px.png)<br>
   *選取組; 的 「 動作控制站 」如果有多個執行個體，從選取清單底部*
   
8. 您會看到出現下方的藍芽設定中的控制站 **"滑鼠、 鍵盤、 （& p) 」 類別目錄**做為**Connected**。 此時，您可能會收到韌體更新 – 請參閱[下一節](motion-controllers.md#updating-controller-firmware)。
9. 重新附加電池封面。
10. 重複步驟 1-9，第二個控制站。

之後成功地配對這兩個控制器，您的設定看起來應該像下 **"滑鼠、 鍵盤、 （& p) 」 類別目錄** 

   ![動作控制站連線](images/450px-motion-controller-connected-300px.png)<br>
   *動作控制站連線*

如果控制器已關閉之後配對，其狀態會顯示為 Paired。 如果控制站永遠保持在 [其他裝置] 類別目錄配對可能只有部分完成時，需要再次執行，即可取得控制器的功能。

### <a name="updating-controller-firmware"></a>更新控制器韌體版本

* 如果沈浸式耳機已連線到您的電腦，而且新的控制器韌體版本可用，韌體會推送至您影片的控制站自動開啟下一次。 控制器韌體更新會以循環的運動，清楚 LED 象限的模式，並需要 1-2 分鐘的時間。
* 韌體更新完成之後，控制器會重新啟動，並重新連線。 現在應該連接兩個控制器。 
    
    ![連接的控制站](images/cyk-connected-300px.jpg)<br>
    *在藍牙設定連接的控制站*

* 適當地確認您的控制器工作：
    1. 啟動**混合實境入口網站**並輸入您的混合實境首頁。
    2. 移動您的控制器和確認追蹤測試按鈕，並確認[屏障](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)的運作方式。 如果它們不這麼做，請參閱[動作控制站疑難排解](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)。

## <a name="gazing-and-pointing"></a>Gazing 和指標

Windows Mixed Reality 支援兩種主要模型互動，如**視線並認可**並**點，並認可**:
* 具有**視線並認可**，使用者為目標的物件及其[視線](gaze.md)，然後選取 使用手動空中點選、 遊戲台、 clicker 或語音的物件。
* 具有**點，並認可**，使用者可以在目標物件是指功能的動作控制站的目標是與然後選取 使用控制器的觸發程序的物件。

應用程式可指向與動作控制器的支援也應該讓視線驅動的互動，盡可能，在功能中的選擇，讓使用者輸入他們使用的裝置。

### <a name="managing-recoil-when-pointing"></a>當管理 recoil

當使用動作控制站點，並認可，您的使用者會使用控制器為目標，並採取動作來提取其觸發程序。 Vigorously 提取觸發程序的使用者可能會得到比他們想要提供為目標的控制站更高版本，其觸發程序的結尾。

若要管理使用者提取觸發程序時可能發生的任何這類 recoil，您的應用程式即可貼齊其目標的光跡，當觸發程序的類比的座標軸值高於 0.0。 然後，您可能需要使用該目標的光跡幾個畫面格稍後一旦觸發值達到 1.0 時，只要在短時間範圍內，最後按下就會發生的動作。 使用較高層級時[複合的點選手勢](gestures.md#composite-gestures)，Windows 將管理此目標光線擷取和逾時。

## <a name="grip-pose-vs-pointing-pose"></a>指標的姿勢與的底框姿勢

Windows Mixed Reality 支援各種不同的外型規格中的動作控制站，與每個控制站設計不同使用者的手狀位置和 「 轉送 」 方向該應用程式的自然之間關聯性的相對值應該使用指出呈現時控制站。

為了更能代表這些控制站，有兩種您可以調查每個互動來源，會帶來**底框姿勢**並**指標姿勢**。

### <a name="grip-pose"></a>調整底框姿勢

**底框姿勢**表示偵測到的 HoloLens，一隻手的或翲保存動作控制器的位置。

沈浸式耳機，在底框姿勢最適合用來呈現**使用者的手**或是**物件保留在使用者的手**劍或槍等。 將顯示為動作控制站時，也會使用的底框姿勢**可呈現模型**提供所移動的 Windows 控制站，請使用做為其原始並旋轉的中心點的底框姿勢。

調整底框姿勢定義具體來說，如下所示：
* **抓住位置**:Palm 距心自然，保留控制器時調整左邊或右邊，置中的底框的位置。 在 Windows Mixed Reality 動作控制站，這個位置通常配合掌握 按鈕。
* **抓住方向的右座標軸**:當您完全開啟以形成平坦的 5 手指姿勢手時，光線，一般是您 palm （從左 palm、 從右 palm 回溯順向）
* **抓住方向的順向軸**:當您關閉您的手部分 （如同保存在控制站）、"forward"tube 透過由非 thumb 手指點光線。
* **抓住方向的總軸**:隱含的權限和轉送的定義總軸。

### <a name="pointer-pose"></a>指標姿勢

**指標姿勢**表示向前指的控制站的提示。

系統提供的指標姿勢最適合用於 raycast 完**轉譯控制器模型本身**。 如果您要呈現其他某些虛擬物件，來控制站，例如虛擬的砲，取代您應該點是最方便的該虛擬物件，例如傳輸的應用程式定義槍模型鸃庢餂沿著光線的光線。 因為使用者可以看到虛擬物件並不是實體的控制器，指向與虛擬物件可能會對於使用您的應用程式更自然。

## <a name="controller-tracking-state"></a>控制器追蹤狀態

耳機，像是 Windows Mixed Reality 動作控制站不需要任何設定的外部追蹤感應器。 相反地，控制器會追蹤耳機本身中的感應器。

如果使用者移出耳機的視野，控制站，在大部分情況下 Windows 會推斷控制站的位置，並將其提供給應用程式繼續。 當控制器失去 visual 追蹤身體力行，控制站的位置將會卸除到近似精確度的位置。

此時，系統會主體鎖定給使用者時，追蹤使用者的位置，同時仍公開使用其內部的方向感應器的控制站，則為 true 的方向移動，控制站。 許多應用程式會使用控制器，以指向，並啟用 UI 項目可以正常運作近似值的精確度在使用者的演算法而不會。

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>明確地追蹤狀態的來龍去脈

想要將位置根據追蹤狀態的應用程式可能可以更進一步，並檢查控制器的狀態，例如 SourceLossRisk 和 PositionAccuracy 上的屬性：

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
* **不到位置：** 控制器可長時間操作近似值的精確度，而有時系統知道，甚至主體鎖定的位置目前不具意義。 例如，只是開啟的控制站可能永遠不會觀察到在視覺上，或使用者可能會讓下一個控制站，然後挑選其他人。 在這些時間，系統將不會提供任何位置，應用程式，並**TryGetPosition**會傳回 false。

## <a name="interactions-low-level-spatial-input"></a>互動：低層級的空間輸入

指針 」 和 「 動作控制站之間的核心互動都有**選取** ，**功能表**，**抓住**，**觸控板**， **搖桿**，並**首頁**。
* **選取**是啟用的全像，其中包含後面接著發行按下的主要互動。 動作控制站，您可以執行選取的按使用控制器的觸發程序。 其他執行 Select 的方式是透過說話[語音命令](voice-input.md)"Select"。 同一個 select 的互動可用於任何應用程式。 將選取視為相當於滑鼠按一下，一種通用的動作，您了解一次，，然後套用到您的所有應用程式。
* **功能表**是次要的互動，可處理的物件，用來提取的內容功能表，或採取其他一些次要的動作。 與動作控制站，您可以採取功能表動作，使用控制器的 *功能表* 按鈕。 （也就是漢堡 [功能表] 圖示，在其上的按鈕）
* **掌握**是如何使用者可以直接採取動作來操作這些瞭若指掌於物件。 與動作控制站，您可以掌握動作藉由緊密扭曲您的第一個。 動作控制器可能會偵測到掌握，以擷取按鈕、 palm 觸發程序或其他感應器。
* **觸控板**可讓使用者能夠調整動作控制器的觸控介面沿著兩個維度中的動作上的 向下觸控板認可動作。 跳動提供已按下的狀態、 觸及的狀態和標準化的 XY 座標。 X 和 Y 範圍從-1 到 1 的循環的觸控板，在中心與各種 （0，0）。 X，左邊是-1，1 為右邊。 Y，-1 會在底部，並在頂端的 [1] 是。
* **搖桿**可讓使用者藉由移動其循環的範圍內的動作控制器的搖桿調整兩個維度中的動作上的 向下搖桿認可動作。 搖桿也會提供已按下的狀態，並正規化 XY 座標。 X 和 Y 範圍從-1 到 1 的循環的觸控板，在中心與各種 （0，0）。 X，左邊是-1，1 為右邊。 Y，-1 會在底部，並在頂端的 [1] 是。
* **首頁**是用來返回至 [開始] 功能表的特殊系統動作。 這就像是在鍵盤或 Xbox 控制器上的 Xbox 按鈕上按下 Windows 鍵。 您可以回家動作控制站上，按 [Windows] 按鈕。 請注意，您可以也一律回到開始說 「 嘿 Cortana，移至首頁 」。 應用程式無法特別首頁的動作做出回應，因為這些會由系統處理。

## <a name="composite-gestures-high-level-spatial-input"></a>複合筆勢：高層級的空間輸入

兩者 [交給筆勢](gestures.md) 和動作控制站可以追蹤經過一段時間，來偵測一組常用的高階 **[複合筆勢](gestures.md#composite-gestures)** 。 這可讓您的應用程式偵測到高層級**點選**，**保存**，**操作**並**導覽**是否使用者最後使用筆勢指針或控制站。

## <a name="rendering-the-motion-controller-model"></a>轉譯動作控制器模型

**3D 控制器模型**Windows 提供給應用程式可呈現的模型，每個動作控制器的系統中目前作用中。 讓您以動態方式載入，並清楚表達這些系統提供的控制器模型，在執行階段的應用程式，您可以確保您的應用程式是以任何未來的向前相容控制器的設計。

這些可呈現模型的所有呈現在**底框姿勢**的控制器，做為模型的原點配合在真實世界的這一點。 如果您要轉譯控制器模型，您可能然後要 raycast 從您在場景**指標姿勢**，用來表示的光線沿著其使用者自然地預期能點時，提供該控制器的實體設計。

如需如何載入以動態方式在 Unity 中的控制器模型的詳細資訊，請參閱[轉譯動作控制器模型，在 Unity](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity)一節。

**2D 控制器藝術線條**雖然我們建議您將應用程式內控制站的秘訣和命令連結至應用程式內控制器模型本身，有些開發人員可能想要使用一般的 「 教學課程 」 或 「 作法 」 中的 2D 列美工圖案表示動作的控制器UI。 對於這些開發人員，我們已進行.png 動作控制器列美工檔案提供下列兩個黑與白 （按一下滑鼠右鍵儲存）。

![動作控制器藝術線條的預覽](images/motioncontrollers-black-preview-300px.png)

 [高解析度影片控制器線條中 '' 白色 ' '](images/motioncontrollers-white.png)
 
 [高解析度影片控制器線條中 '' 黑色 ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>常見問題集

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>我對可以動作控制站到多部電腦？

動作控制站都支援與一部電腦配對。 遵循指示[動作控制器設定](motion-controllers.md#setup)配對您的控制器。

### <a name="how-do-i-update-motion-controller-firmware"></a>如何更新動作控制器韌體版本？

動作控制器韌體版本是耳機驅動程式的一部分，而且會自動更新連接上如有必要。 韌體更新通常需要 1-2 分鐘，視藍芽無線電和連結的品質而定。 在罕見的情況下，控制器韌體更新可能需要最多 10 分鐘，表示不佳的藍芽連線或收音機干擾。 請參閱[藍芽人十分熱心指南中的最佳作法](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)連線問題進行疑難排解。 韌體更新之後，控制器會重新開機和重新連線到主機電腦 （您可能會注意到移往追蹤的 Led）。 如果中斷韌體更新 （例如，控制器失去電源），它將會嘗試在下次控制器電源。

### <a name="how-i-can-check-battery-level"></a>我如何檢查剩餘電力？

在  [Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)，您可以開啟您的控制器，以查看其電池電量虛擬模型的反向一端。 沒有任何實體的電池的層級指標。

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>您可以使用這些控制站，而不需要耳機嗎？ 只為搖桿/觸發程序等的輸入嗎？

不適用於通用 Windows 應用程式。

## <a name="troubleshooting"></a>疑難排解

請參閱[動作控制站疑難排解](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)愛好者指南中。

## <a name="filing-motion-controller-feedbackbugs"></a>提交動作控制器的意見反應/錯誤

[提供意見反應](give-us-feedback.md)意見反應中樞中使用的 「 混合的實境-> 輸入 「 類別目錄。

## <a name="see-also"></a>另請參閱
* [Unity 中的筆勢和運動控制器](gestures-and-motion-controllers-in-unity.md)
* [DirectX 中的手部和運動控制器](hands-and-motion-controllers-in-directx.md)
* [筆勢](gestures.md)
* [MR Input 213：運動控制器](mixed-reality-213.md)
* [人十分熱心的指南：您主要的 Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [人十分熱心的指南：使用 Windows Mixed Reality 中的遊戲和應用程式](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [追蹤內到外的運作方式](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
