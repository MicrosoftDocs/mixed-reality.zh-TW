---
title: 3. 設定您的專案以進行混合實境
description: 教學課程的第 3 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840617"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3.設定您的專案以進行混合實境

本節將逐步引導您完成設定應用程式以進行混合現實開發的程序。 

## <a name="objectives"></a>目標

* 了解如何使用 ARSessionConfig、Pawn 和 GameMode 來設定混合實境專案

## <a name="configure-the-session"></a>設定工作階段

1. 在內容瀏覽器中，往回瀏覽到 [內容]  資料夾。 按一下 [新增] > [其他] > [資料資產]  。 

2. 挑選 **ARSessionConfig** 作為類別，然後按一下 [選取]  。 將資產命名為 "ARSessionConfig"。

![建立資料資產](images/unreal-uxt/3-createasset.PNG)

3. 按兩下 [ARSessionConfig] 以將其開啟。 ARSessionConfig 資料資產包含一些實用的 AR 設定，包括空間對應和遮蔽。 如需有關 ARSessionConfig 的詳細資訊，請參閱有關 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 的 Unreal 引擎文件。 針對我們的國際象棋應用程式，我們不需要修改任何設定，只要按 [儲存]  並返回主視窗即可。 

![AR 工作階段設定](images/unreal-uxt/3-arsessionconfig.PNG)

4. 在檢視區上方的工具列上，按一下 [藍圖] > [開啟層級藍圖]  。 層級藍圖是特殊的藍圖，可作為整個層級的全域事件圖表。 我們即將在此啟動 AR 工作階段，讓 AR 工作階段設定在層級開始時就加以套用。  

5. 拖曳 **Event BeginPlay** 的執行節點並放開。 搜尋 [啟動 AR 工作階段]  節點。 按一下 [工作階段]  ，然後選取您新建立的 **ARSessionConfig** 資產。 點擊 [編譯]  和 [儲存]  。 返回主視窗。

![啟動 AR 工作階段](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a>建立 Pawn

1.  在 [內容] 資料夾中，建立繼承自 **DefaultPawn** 的新藍圖。 在 Unreal 中，Pawn 代表遊戲中的使用者，或在此案例中是 HoloLens 2 體驗。 將新的 Pawn 重新命名為 "MRPawn"，然後按兩下 MRPawn 來將其開啟。 

![建立繼承自 DefaultPawn 的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

2.  根據預設，Pawn 具有網格元件和衝突元件，因為在大部分的 Unreal 專案中，由使用者控制的 Pawn 是會與其他元件衝突的穩固物件。 在這種情況下，由於使用者是 Pawn，所以我們想要能夠通過全像投影，而不會產生衝突。 在 [元件] 面板中，選取 [CollisionComponent]  。 在 [詳細資料] 面板中，向下捲動至 [衝突] 區段，然後按一下 [衝突預設] 旁的下拉式清單。 將此設定從 Pawn 變更為 **NoCollision**。 針對 **MeshComponent** 執行相同的動作。 **編譯**並**儲存**藍圖。 返回主視窗。 

![調整 Pawn 的衝突預設值](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a>建立遊戲模式

1.  在內容瀏覽器的 [內容] 資料夾中，建立具有父系**遊戲模式基底**的新藍圖。 將其命名為 MRGameMode，然後按兩下來開啟。 在 Unreal 中，遊戲模式會決定遊戲或體驗的一些設定，包括要使用的預設 Pawn。 

![內容瀏覽器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  在 [詳細資料] 面板中，找出 [類別] 區段。 將預設的 Pawn 類別從 DefaultPawn 變更為您剛才建立的 **MRPawn**。 點擊 [編譯]  和 [儲存]  。 返回主視窗。 

![設定預設的 Pawn 類別](images/unreal-uxt/3-setpawn.PNG)

3.  設定專案的最後一個步驟是告訴 Unreal 預設為 MRGameMode。 移至 [編輯] > [專案設定] > [地圖與模式] (在專案中)  區段。 在 [預設模式] 區段中，按一下下拉式清單，然後選擇 [MRGameMode]  。 在下方的 [預設地圖] 區段中，將 [EditorStartupMap]  和 [GameDefaultMap]  變更為 [主要]  。 如此一來，當您關閉編輯器並重新開啟時，系統會預設為選取主要地圖。 同樣地，當您開始遊戲時，主要地圖會是啟動的層級。 

![專案設定 - 地圖與模式](images/unreal-uxt/3-mapsandmodes.PNG)

[下一節：4.使場景成為互動式場景](unreal-uxt-ch4.md)