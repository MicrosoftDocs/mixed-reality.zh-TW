---
title: 語音輸入
description: 說明如何使用語音輸入
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality，HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835303"
---
# <a name="voice-input"></a>語音輸入

若要在 HoloLens 上啟用語音辨識，開發人員必須在 [專案設定] 下的 [Unreal 編輯器] 中啟用 [麥克風]，> 平臺 > HoloLens > 功能。 裝置也必須在 [設定] 中啟用 [語音辨識]，> 隱私權 > 語音]，並使用英文語言。

![Windows 語音辨識設定](images/unreal/speech-recognition-settings.png)

建議您也啟用線上語音辨識，以取得最佳的服務品質。 您可以在[這裡](voice-input.md)找到 HoloLens 上的語音辨識的技術詳細資料

然後，使用者會看到一個對話方塊，說明如何在應用程式第一次啟動時啟用麥克風。 如果使用者選取 [是]，則應用程式會開始取得語音輸入。

語音輸入不需要特殊的 Windows Mixed Reality API，而是以現有的 Unreal Engine 4 輸入對應 API 為基礎。 如需如何使用輸入 API 的詳細資料，請參閱[這裡](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)

語音對應已新增至 [引擎–輸入]、[動作] 和 [軸對應] 下方的 [系結] 區段。 

![UE4 引擎輸入](images/unreal/engine-input.png)
 
以下是針對全球「跳躍」進行新增監視的範例。 可以使用任何英文單字或短句子。 

透過專案設定加入語音對應之後，開發人員就可以使用標準 Unreal 邏輯來處理輸入，如下列範例所示： 
 
![語音的簡單動作](images/unreal/input-action-bp.png)
