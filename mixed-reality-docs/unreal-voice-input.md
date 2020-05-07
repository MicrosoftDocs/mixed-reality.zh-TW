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
# <a name="voice-input"></a><span data-ttu-id="19220-104">語音輸入</span><span class="sxs-lookup"><span data-stu-id="19220-104">Voice Input</span></span>

<span data-ttu-id="19220-105">若要在 HoloLens 上啟用語音辨識，開發人員必須在 [專案設定] 下的 [Unreal 編輯器] 中啟用 [麥克風]，> 平臺 > HoloLens > 功能。</span><span class="sxs-lookup"><span data-stu-id="19220-105">To enable speech recognition on HoloLens, the developer needs to enable “Microphone” in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> <span data-ttu-id="19220-106">裝置也必須在 [設定] 中啟用 [語音辨識]，> 隱私權 > 語音]，並使用英文語言。</span><span class="sxs-lookup"><span data-stu-id="19220-106">The device must also have Speech recognition enabled in Settings > Privacy > Speech and use the English language.</span></span>

![Windows 語音辨識設定](images/unreal/speech-recognition-settings.png)

<span data-ttu-id="19220-108">建議您也啟用線上語音辨識，以取得最佳的服務品質。</span><span class="sxs-lookup"><span data-stu-id="19220-108">It’s recommended to enable Online speech recognition too for the best possible quality of the service.</span></span> <span data-ttu-id="19220-109">您可以在[這裡](voice-input.md)找到 HoloLens 上的語音辨識的技術詳細資料</span><span class="sxs-lookup"><span data-stu-id="19220-109">Technical details for speech recognition on HoloLens can be found [here](voice-input.md)</span></span>

<span data-ttu-id="19220-110">然後，使用者會看到一個對話方塊，說明如何在應用程式第一次啟動時啟用麥克風。</span><span class="sxs-lookup"><span data-stu-id="19220-110">Then user will see a dialog about enabling the microphone when the application first starts.</span></span> <span data-ttu-id="19220-111">如果使用者選取 [是]，則應用程式會開始取得語音輸入。</span><span class="sxs-lookup"><span data-stu-id="19220-111">If a user selects Yes, the application will begin getting voice input.</span></span>

<span data-ttu-id="19220-112">語音輸入不需要特殊的 Windows Mixed Reality API，而是以現有的 Unreal Engine 4 輸入對應 API 為基礎。</span><span class="sxs-lookup"><span data-stu-id="19220-112">Speech input doesn’t require a special Windows Mixed Reality API and is instead built upon the existing Unreal Engine 4 Input mapping API.</span></span> <span data-ttu-id="19220-113">如需如何使用輸入 API 的詳細資料，請參閱[這裡](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span><span class="sxs-lookup"><span data-stu-id="19220-113">Details on how to use the Input API are [here](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span></span>

<span data-ttu-id="19220-114">語音對應已新增至 [引擎–輸入]、[動作] 和 [軸對應] 下方的 [系結] 區段。</span><span class="sxs-lookup"><span data-stu-id="19220-114">Speech Mappings have been added to the Bindings section of Engine – Input below Action and Axis Mappings.</span></span> 

![UE4 引擎輸入](images/unreal/engine-input.png)
 
<span data-ttu-id="19220-116">以下是針對全球「跳躍」進行新增監視的範例。</span><span class="sxs-lookup"><span data-stu-id="19220-116">Here is an example of added monitoring for the world “jump”.</span></span> <span data-ttu-id="19220-117">可以使用任何英文單字或短句子。</span><span class="sxs-lookup"><span data-stu-id="19220-117">Any English word(s) or short sentences can be used.</span></span> 

<span data-ttu-id="19220-118">透過專案設定加入語音對應之後，開發人員就可以使用標準 Unreal 邏輯來處理輸入，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="19220-118">After a Speech Mapping is added via Project Settings, a developer can then use standard Unreal logic to handle the input, as in the following example:</span></span> 
 
![語音的簡單動作](images/unreal/input-action-bp.png)
