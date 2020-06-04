---
title: 語音輸入
description: 在 HoloLens 2 和 Unreal 引擎中設定和使用語音輸入的教學課程
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality，Unreal，Unreal Engine 4，UE4，HoloLens 2，語音，語音輸入，語音辨識，混合現實，開發，功能，檔，指南，全息記錄，遊戲開發
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330630"
---
# <a name="voice-input-in-unreal"></a>Unreal 中的語音輸入

## <a name="overview"></a>概觀
語音輸入可讓您與全息影像互動，而不需要使用右手手勢，而且在 HoloLens （第1代）和 HoloLens 2 上支援。 它是由在所有其他通用 Windows 應用程式中支援語音的相同引擎所提供，而且可以在混合現實中的互動方式中新增自然感覺。 

支援的語音功能包括：
- [Select 命令](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)
- [您好，Cortana](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- 「見它」，用於按鈕和標籤互動
- 聽寫

如需詳細資訊，請參閱主要的[語音輸入](voice-input.md)檔。

## <a name="enabling-speech-recognition"></a>啟用語音辨識

若要在 HoloLens 上啟用語音辨識：
1. 選取 [**專案設定] > [平臺 > HoloLens > 功能**]，並啟用 [**麥克風**]。 
2. 在 [設定] 中啟用語音 recogniztion **> 隱私權 > 語音**]，然後選取 [**英文**]。

> [!NOTE]
> 語音辨識一律會在 [**設定**] 應用程式中設定的 Windows 顯示語言中運作。 建議您也啟用**線上語音辨識**，以獲得最佳的服務品質。

![Windows 語音辨識設定](images/unreal/speech-recognition-settings.png)

3. 當應用程式第一次開始詢問您是否要啟用麥克風時，會顯示對話方塊。 選取 [**是]** 會啟動應用程式中的語音輸入。

語音輸入不需要任何特殊的 Windows Mixed Reality Api;它是以現有的 Unreal Engine 4[輸入](https://docs.unrealengine.com/Gameplay/Input/index.html)對應 API 為基礎。 

## <a name="adding-speech-mappings"></a>新增語音對應
使用語音輸入時，將語音連線到動作是很重要的步驟。 這些對應會監視使用者可能說出的語音關鍵字應用程式，然後引發連結的動作。 您可以透過下列方式尋找語音對應：
1. 選取 [**編輯] > 專案設定**，並將它滾動至 [**引擎**] 區段，然後按一下 [**輸入**]。

若要為跳躍命令新增語音對應：
1. 按一下 [ **+** **陣列元素**] 旁的圖示，並填寫下列值：
    * **動作名稱**的**jumpWord**
    * **跳**過**語音關鍵字**

> [!NOTE]
> 任何英文單字或短句子都可以當做關鍵字使用。 

![UE4 引擎輸入](images/unreal/engine-input.png)

語音對應可以做為輸入元件（例如動作或軸對應），或當做事件圖形中的藍圖節點使用。 例如，您可以連結跳躍命令，根據說出單字的時間，列印出兩個不同的記錄檔：

1. 按兩下藍圖以在**事件圖形**中開啟。
2. 以**滑鼠右鍵按一下**並搜尋語音對應的**動作名稱**（在此案例中為**JumpWord**），然後按**Enter**。 這會將 [**輸入動作**] 節點加入至圖形。
3. 拖放**按下**的釘選來**列印字串**節點，如下圖所示。 您可以將**釋放**的 pin 保留空白，它不會執行任何語音對應的作業。
 
![語音的簡單動作](images/unreal/voice-input-img-03.png)

4. 播放應用程式，說出一個**字，** 然後監看主控台列印出記錄！

這就是您在 Unreal 中開始將語音輸入新增至 HoloLens 應用程式所需的所有設定。 如需有關語音和互動的詳細資訊，請參閱下列連結，並請務必考慮您為使用者建立的體驗。

## <a name="see-also"></a>另請參閱
* [目光和行動](gaze-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [MR Input 212：語音](holograms-212.md)
