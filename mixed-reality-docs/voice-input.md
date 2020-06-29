---
title: 語音輸入
description: 語音輸入是 HoloLens 和 Windows Mixed Reality 沉浸式耳機的核心輸入。 語音可以用於命令、聽寫、Cortana 等等。
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv、語音、cortana、語音、輸入
ms.openlocfilehash: 37364e90aa1d8a7b607a99f4c9b830972f7f80b3
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441825"
---
# <a name="voice-input"></a><span data-ttu-id="cdf60-105">語音輸入</span><span class="sxs-lookup"><span data-stu-id="cdf60-105">Voice input</span></span>

![語音輸入](images/UX/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="cdf60-107">語音是 HoloLens 輸入的其中一種主要形式。</span><span class="sxs-lookup"><span data-stu-id="cdf60-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="cdf60-108">它可讓您直接命令全息影像，而不需要使用[右手手勢](gaze-and-commit.md#composite-gestures)。</span><span class="sxs-lookup"><span data-stu-id="cdf60-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="cdf60-109">語音輸入是溝通意圖的一種自然方式。</span><span class="sxs-lookup"><span data-stu-id="cdf60-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="cdf60-110">語音在遍歷複雜介面時特別有用，因為它可讓使用者使用一個命令來剪下嵌套的功能表。</span><span class="sxs-lookup"><span data-stu-id="cdf60-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="cdf60-111">語音輸入是由在所有其他_通用 Windows 應用程式_中支援語音的[相同引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)提供技術支援。</span><span class="sxs-lookup"><span data-stu-id="cdf60-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="cdf60-112">在 HoloLens 上，語音辨識一律會以 [設定] 中設定的 Windows 顯示語言運作。</span><span class="sxs-lookup"><span data-stu-id="cdf60-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="cdf60-113">語音和注視</span><span class="sxs-lookup"><span data-stu-id="cdf60-113">Voice and gaze</span></span>

<span data-ttu-id="cdf60-114">使用語音命令時，（head 或眼睛）注視通常用來做為目的機制，不論使用游標（"select"），或將命令隱含地通道至您要查看的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cdf60-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="cdf60-115">在此情況下，可能甚至不需要顯示任何看過的游標 _（「見它，說它」）_。</span><span class="sxs-lookup"><span data-stu-id="cdf60-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="cdf60-116">當然，有些語音命令根本不需要目標，例如「移至開始」或「嗨，Cortana」。</span><span class="sxs-lookup"><span data-stu-id="cdf60-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="cdf60-117">裝置支援</span><span class="sxs-lookup"><span data-stu-id="cdf60-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="cdf60-118"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="cdf60-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="cdf60-119"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="cdf60-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="cdf60-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="cdf60-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="cdf60-121"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="cdf60-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="cdf60-122">語音輸入</span><span class="sxs-lookup"><span data-stu-id="cdf60-122">Voice input</span></span></td>
        <td><span data-ttu-id="cdf60-123">✔️</span><span class="sxs-lookup"><span data-stu-id="cdf60-123">✔️</span></span></td>
        <td><span data-ttu-id="cdf60-124">✔️</span><span class="sxs-lookup"><span data-stu-id="cdf60-124">✔️</span></span></td>
        <td><span data-ttu-id="cdf60-125">✔️（使用麥克風）</span><span class="sxs-lookup"><span data-stu-id="cdf60-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="cdf60-126">"Select" 命令</span><span class="sxs-lookup"><span data-stu-id="cdf60-126">The "select" command</span></span>

<span data-ttu-id="cdf60-127">**HoloLens (第 1 代)**</span><span class="sxs-lookup"><span data-stu-id="cdf60-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="cdf60-128">即使不特別將語音支援新增至您的應用程式，您的使用者只要說出系統語音命令「選取」，就可以啟動全息影像。</span><span class="sxs-lookup"><span data-stu-id="cdf60-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="cdf60-129">其行為與 HoloLens 上的[空中](gaze-and-commit.md#composite-gestures)按鍵、按下[hololens clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上的 [選取] 按鈕，或在[Windows Mixed Reality 動作控制器](motion-controllers.md)上按下觸發程式一樣。</span><span class="sxs-lookup"><span data-stu-id="cdf60-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](https://docs.microsoft.com/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="cdf60-130">您會聽到音效，並看到包含 [選取] 的工具提示會顯示為 [確認]。</span><span class="sxs-lookup"><span data-stu-id="cdf60-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="cdf60-131">「選取」是由低乘冪關鍵字偵測演算法所啟用，因此隨時都可讓您以最少的電池壽命影響來表示，即使您的手中也一樣。</span><span class="sxs-lookup"><span data-stu-id="cdf60-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="cdf60-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="cdf60-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="cdf60-133">若要使用 HoloLens 2 中的「選取」語音命令，您必須先啟動注視游標以作為指標。</span><span class="sxs-lookup"><span data-stu-id="cdf60-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="cdf60-134">用來啟動它的命令很容易記住，只要說「select」就可以了。</span><span class="sxs-lookup"><span data-stu-id="cdf60-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="cdf60-135">若要結束模式，只要使用滑鼠按鍵、接近手指的按鈕，或使用系統手勢，就可以再次使用您的手。</span><span class="sxs-lookup"><span data-stu-id="cdf60-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="cdf60-136">*影像：說「選取」以使用語音命令進行選取*</span><span class="sxs-lookup"><span data-stu-id="cdf60-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![使用者可以說「選取」，使用語音命令進行選取。](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="cdf60-138">嗨 Cortana</span><span class="sxs-lookup"><span data-stu-id="cdf60-138">Hey Cortana</span></span>

<span data-ttu-id="cdf60-139">您也可以說「嘿 Cortana」，隨時帶出 Cortana。</span><span class="sxs-lookup"><span data-stu-id="cdf60-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="cdf60-140">您不需要等待她繼續詢問您的問題或提供指示，例如，試著說「嘿，我的天氣是什麼？」</span><span class="sxs-lookup"><span data-stu-id="cdf60-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="cdf60-141">當做單一句子。</span><span class="sxs-lookup"><span data-stu-id="cdf60-141">as a single sentence.</span></span> <span data-ttu-id="cdf60-142">如需 Cortana 和您可以執行之動作的詳細資訊，請直接詢問她！</span><span class="sxs-lookup"><span data-stu-id="cdf60-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="cdf60-143">說「嘿，我可以說什麼？」</span><span class="sxs-lookup"><span data-stu-id="cdf60-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="cdf60-144">她會提取一個工作和建議的命令清單。</span><span class="sxs-lookup"><span data-stu-id="cdf60-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="cdf60-145">如果您已經在 Cortana 應用程式中，也可以按一下 [ **？** ]</span><span class="sxs-lookup"><span data-stu-id="cdf60-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="cdf60-146">在提要欄位上拉出此相同功能表的圖示。</span><span class="sxs-lookup"><span data-stu-id="cdf60-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="cdf60-147">**HoloLens 特有的命令**</span><span class="sxs-lookup"><span data-stu-id="cdf60-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="cdf60-148">「我可以說什麼？」</span><span class="sxs-lookup"><span data-stu-id="cdf60-148">"What can I say?"</span></span>
* <span data-ttu-id="cdf60-149">[移至開始]-而不是 [ [bloom](system-gesture.md#bloom) ] 以進入 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="cdf60-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="cdf60-150">「啟動 <app> 」</span><span class="sxs-lookup"><span data-stu-id="cdf60-150">"Launch <app>"</span></span>
* <span data-ttu-id="cdf60-151">「移至 <app> 這裡」</span><span class="sxs-lookup"><span data-stu-id="cdf60-151">"Move <app> here"</span></span>
* <span data-ttu-id="cdf60-152">「拍照」</span><span class="sxs-lookup"><span data-stu-id="cdf60-152">"Take a picture"</span></span>
* <span data-ttu-id="cdf60-153">「開始錄製」</span><span class="sxs-lookup"><span data-stu-id="cdf60-153">"Start recording"</span></span>
* <span data-ttu-id="cdf60-154">「停止錄製」</span><span class="sxs-lookup"><span data-stu-id="cdf60-154">"Stop recording"</span></span>
* <span data-ttu-id="cdf60-155">「顯示手光線」</span><span class="sxs-lookup"><span data-stu-id="cdf60-155">"Show hand ray"</span></span>
* <span data-ttu-id="cdf60-156">「隱藏手光線」</span><span class="sxs-lookup"><span data-stu-id="cdf60-156">"Hide hand ray"</span></span>
* <span data-ttu-id="cdf60-157">「增加亮度」</span><span class="sxs-lookup"><span data-stu-id="cdf60-157">"Increase the brightness"</span></span>
* <span data-ttu-id="cdf60-158">「降低亮度」</span><span class="sxs-lookup"><span data-stu-id="cdf60-158">"Decrease the brightness"</span></span>
* <span data-ttu-id="cdf60-159">「增加音量」</span><span class="sxs-lookup"><span data-stu-id="cdf60-159">"Increase the volume"</span></span>
* <span data-ttu-id="cdf60-160">「減少音量」</span><span class="sxs-lookup"><span data-stu-id="cdf60-160">"Decrease the volume"</span></span>
* <span data-ttu-id="cdf60-161">「靜音」或「取消靜音」</span><span class="sxs-lookup"><span data-stu-id="cdf60-161">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="cdf60-162">「關閉裝置」</span><span class="sxs-lookup"><span data-stu-id="cdf60-162">"Shut down the device"</span></span>
* <span data-ttu-id="cdf60-163">「重新開機裝置」</span><span class="sxs-lookup"><span data-stu-id="cdf60-163">"Restart the device"</span></span>
* <span data-ttu-id="cdf60-164">「進入睡眠狀態」</span><span class="sxs-lookup"><span data-stu-id="cdf60-164">"Go to sleep"</span></span>
* <span data-ttu-id="cdf60-165">「有什麼時間？」</span><span class="sxs-lookup"><span data-stu-id="cdf60-165">"What time is it?"</span></span>
* <span data-ttu-id="cdf60-166">「我剩多少電池？」</span><span class="sxs-lookup"><span data-stu-id="cdf60-166">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="cdf60-167">「見它」</span><span class="sxs-lookup"><span data-stu-id="cdf60-167">"See It, Say It"</span></span><br>
        <span data-ttu-id="cdf60-168">HoloLens 有「看它，假設是語音輸入的模型」，其中標籤的按鈕會告訴使用者他們也可以說的語音命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-168">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="cdf60-169">例如，當您在 HoloLens （第1代）中查看應用程式視窗時，使用者可以在應用程式行中說出他們看到的「調整」命令，以調整應用程式在世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="cdf60-169">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="cdf60-170">*影像：使用者可以在應用程式行中顯示 [調整] 命令，以調整應用程式的位置*</span><span class="sxs-lookup"><span data-stu-id="cdf60-170">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="cdf60-171">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="cdf60-171">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="cdf60-172">![查看應用程式視窗或全息影像時，使用者可以說出他們在應用程式行中看到的「調整」命令，以調整應用程式在世界中的位置。](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="cdf60-172">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="cdf60-173">當應用程式遵循此規則時，使用者可以輕鬆地瞭解如何控制系統。</span><span class="sxs-lookup"><span data-stu-id="cdf60-173">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="cdf60-174">為了強調此情況，當您在 HoloLens （第1代）中的按鈕上撥雲見日時，如果按鈕已啟用語音，並顯示要對其進行「按下」的命令，您就會看到一個「聲音停留」工具提示。</span><span class="sxs-lookup"><span data-stu-id="cdf60-174">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="cdf60-175">若要在 HoloLens 2 中顯示語音工具提示，請以「選取」或「我可以說」來顯示語音游標（請參閱影像）。</span><span class="sxs-lookup"><span data-stu-id="cdf60-175">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="cdf60-176">*影像：「見它，說它」命令出現在按鈕下方*</span><span class="sxs-lookup"><span data-stu-id="cdf60-176">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![查看它，假設命令出現在按鈕下方](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="cdf60-178">快速全息影像操作的語音命令</span><span class="sxs-lookup"><span data-stu-id="cdf60-178">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="cdf60-179">在撥雲見日時，您可以說出一些語音命令，以快速執行操作工作。</span><span class="sxs-lookup"><span data-stu-id="cdf60-179">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="cdf60-180">這些語音命令適用于應用程式視窗，以及您在世界中所放置的3D 物件。</span><span class="sxs-lookup"><span data-stu-id="cdf60-180">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="cdf60-181">**全息影像操作命令**</span><span class="sxs-lookup"><span data-stu-id="cdf60-181">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="cdf60-182">臉部我</span><span class="sxs-lookup"><span data-stu-id="cdf60-182">Face me</span></span>
* <span data-ttu-id="cdf60-183">較大 |增加</span><span class="sxs-lookup"><span data-stu-id="cdf60-183">Bigger | Enhance</span></span>
* <span data-ttu-id="cdf60-184">較小</span><span class="sxs-lookup"><span data-stu-id="cdf60-184">Smaller</span></span>

<span data-ttu-id="cdf60-185">在 HoloLens 2 上，您也可以結合眼睛來建立更自然的互動，以隱含地提供有關您所指的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="cdf60-185">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="cdf60-186">例如，您可以直接查看全像投影，然後說「put_這個_」，然後查看要放置它的位置，然後說「到_這裡_」。</span><span class="sxs-lookup"><span data-stu-id="cdf60-186">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="cdf60-187">或者，您可以查看複雜電腦上的全像攝影元件，並說：「提供更多關於_此_的詳細資訊」。</span><span class="sxs-lookup"><span data-stu-id="cdf60-187">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="cdf60-188">探索語音命令</span><span class="sxs-lookup"><span data-stu-id="cdf60-188">Discovering voice commands</span></span>

<span data-ttu-id="cdf60-189">某些命令（例如上述快速操作的命令）可以隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="cdf60-189">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="cdf60-190">若要深入瞭解您可以使用的命令，請看一個物件，並說「我可以說什麼？」。</span><span class="sxs-lookup"><span data-stu-id="cdf60-190">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="cdf60-191">可能會彈出的命令清單。</span><span class="sxs-lookup"><span data-stu-id="cdf60-191">A list of possible commands pops up.</span></span> <span data-ttu-id="cdf60-192">您也可以使用 head 注視游標來尋找並顯示您前面的每個按鈕的語音工具提示。</span><span class="sxs-lookup"><span data-stu-id="cdf60-192">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="cdf60-193">如果您想要完整的清單，只要說「顯示所有命令」即可。</span><span class="sxs-lookup"><span data-stu-id="cdf60-193">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="cdf60-194">聽寫</span><span class="sxs-lookup"><span data-stu-id="cdf60-194">Dictation</span></span>

<span data-ttu-id="cdf60-195">語音聽寫可以更有效率地在應用程式中輸入文字，而不是鍵入[空中](gaze-and-commit.md#composite-gestures)。</span><span class="sxs-lookup"><span data-stu-id="cdf60-195">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="cdf60-196">這可以大幅加速輸入，讓使用者的工作更少。</span><span class="sxs-lookup"><span data-stu-id="cdf60-196">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="cdf60-197">![語音聽寫一開始會選取 [麥克風] 按鈕](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="cdf60-197">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="cdf60-198">*語音聽寫一開始會選取鍵盤上的 [麥克風] 按鈕*</span><span class="sxs-lookup"><span data-stu-id="cdf60-198">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="cdf60-199">當全像攝影鍵盤在使用中時，您可以切換到聽寫模式，而不是輸入。</span><span class="sxs-lookup"><span data-stu-id="cdf60-199">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="cdf60-200">選取文字輸入方塊旁邊的麥克風以開始使用。</span><span class="sxs-lookup"><span data-stu-id="cdf60-200">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="cdf60-201">將語音命令新增至您的應用程式</span><span class="sxs-lookup"><span data-stu-id="cdf60-201">Adding voice commands to your app</span></span>

<span data-ttu-id="cdf60-202">請考慮對您所建置的任何體驗新增語音命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-202">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="cdf60-203">語音是功能強大的方式，可方便您控制系統和應用程式。</span><span class="sxs-lookup"><span data-stu-id="cdf60-203">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="cdf60-204">因為使用者說話時的語調和口音各異，適當選擇語音關鍵字才能確保系統會分毫不差地解讀出使用者的命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-204">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="cdf60-205">最佳作法</span><span class="sxs-lookup"><span data-stu-id="cdf60-205">Best practices</span></span>

<span data-ttu-id="cdf60-206">以下是有助於順利辨識語音的一些做法。</span><span class="sxs-lookup"><span data-stu-id="cdf60-206">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="cdf60-207">**使用精簡的命令** - 盡可能選擇有兩個以上音節的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cdf60-207">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="cdf60-208">口音不同的人在說單音節的單字時往往會使用不同的元音。</span><span class="sxs-lookup"><span data-stu-id="cdf60-208">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="cdf60-209">範例：「播放影片」比「播放目前選取的影片」好</span><span class="sxs-lookup"><span data-stu-id="cdf60-209">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="cdf60-210">**使用簡單詞彙**-範例：「顯示便箋」比「顯示牌子」好</span><span class="sxs-lookup"><span data-stu-id="cdf60-210">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="cdf60-211">**確定命令不具破壞性** - 確定可透過語音命令來採取的動作不具破壞性，如果使用者附近有其他人不小心觸發命令，也可以輕鬆地加以復原。</span><span class="sxs-lookup"><span data-stu-id="cdf60-211">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="cdf60-212">**避免類似發音的命令** - 避免註冊多個聽起來非常類似的語音命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-212">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="cdf60-213">範例：「顯示更多」和「Show store」可能會有非常相似的發音。</span><span class="sxs-lookup"><span data-stu-id="cdf60-213">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="cdf60-214">**將未使用的應用程式取消註冊** - 當應用程式並非處在會讓特定語音命令生效的狀態時，請考慮將其取消註冊，以免該命令與其他命令混淆。</span><span class="sxs-lookup"><span data-stu-id="cdf60-214">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="cdf60-215">**使用不同口音進行測試** - 請使用不同口音的使用者測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="cdf60-215">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="cdf60-216">**讓語音命令保持一致** - 如果 "Go back" 會回到上一頁，請在應用程式中保持這個行為。</span><span class="sxs-lookup"><span data-stu-id="cdf60-216">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="cdf60-217">**避免使用系統命令** - 下列語音命令已保留給系統使用。</span><span class="sxs-lookup"><span data-stu-id="cdf60-217">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="cdf60-218">應用程式請勿使用這些命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-218">These should not be used by applications.</span></span>
   * <span data-ttu-id="cdf60-219">"Hey Cortana"</span><span class="sxs-lookup"><span data-stu-id="cdf60-219">"Hey Cortana"</span></span>
   * <span data-ttu-id="cdf60-220">"Select"</span><span class="sxs-lookup"><span data-stu-id="cdf60-220">"Select"</span></span>
   * <span data-ttu-id="cdf60-221">「移至開始」</span><span class="sxs-lookup"><span data-stu-id="cdf60-221">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="cdf60-222">語音輸入的優點</span><span class="sxs-lookup"><span data-stu-id="cdf60-222">Advantages of voice input</span></span>

<span data-ttu-id="cdf60-223">語音輸入是很自然的意圖溝通方式。</span><span class="sxs-lookup"><span data-stu-id="cdf60-223">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="cdf60-224">語音在介面**周遊**上特別有用，因為它可協助使用者剪下介面的多個步驟（使用者可能會在查看網頁時說「返回」，而不需要在應用程式中按 [上一步] 按鈕）。</span><span class="sxs-lookup"><span data-stu-id="cdf60-224">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="cdf60-225">這小段節省時間對於使用者對體驗的認知具有強大的**情緒效果**，並賦予他們少量的增強。</span><span class="sxs-lookup"><span data-stu-id="cdf60-225">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="cdf60-226">當我們無法騰出雙手或是在執行**多工**處理時，使用語音也是很方便的輸入方法。</span><span class="sxs-lookup"><span data-stu-id="cdf60-226">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="cdf60-227">在鍵盤上輸入的裝置很棘手，**語音聽寫**可以是輸入文字的有效替代方式。</span><span class="sxs-lookup"><span data-stu-id="cdf60-227">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="cdf60-228">最後，在某些情況下，當注視和手勢的**精確度範圍**受到限制時，voice 可以協助區分使用者的意圖。</span><span class="sxs-lookup"><span data-stu-id="cdf60-228">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="cdf60-229">**使用語音如何讓使用者受益**</span><span class="sxs-lookup"><span data-stu-id="cdf60-229">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="cdf60-230">減少時間 - 語音應該會讓最終目標更有效率。</span><span class="sxs-lookup"><span data-stu-id="cdf60-230">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="cdf60-231">最不費力 - 語音應該會讓工作變得更為流暢且更不費力。</span><span class="sxs-lookup"><span data-stu-id="cdf60-231">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="cdf60-232">降低認知負荷 - 語音既直覺、易於了解且容易記住。</span><span class="sxs-lookup"><span data-stu-id="cdf60-232">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="cdf60-233">符合社交規範 - 語音應該會符合社會行為規範。</span><span class="sxs-lookup"><span data-stu-id="cdf60-233">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="cdf60-234">語音很平常 - 語音隨時可以變成慣常行為。</span><span class="sxs-lookup"><span data-stu-id="cdf60-234">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="cdf60-235">語音輸入的挑戰</span><span class="sxs-lookup"><span data-stu-id="cdf60-235">Challenges for voice input</span></span>

<span data-ttu-id="cdf60-236">雖然語音輸入非常適用于許多不同的應用程式，但也面臨幾項挑戰。</span><span class="sxs-lookup"><span data-stu-id="cdf60-236">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="cdf60-237">瞭解語音輸入的優點和挑戰，可以讓應用程式開發人員針對使用語音輸入的方式和時機，以及為使用者建立絕佳體驗，提供更聰明的選擇。</span><span class="sxs-lookup"><span data-stu-id="cdf60-237">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="cdf60-238">**連續輸入控制項的語音輸入**精細的控制是其中一種。</span><span class="sxs-lookup"><span data-stu-id="cdf60-238">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="cdf60-239">例如，使用者可能會想要在其「音樂」應用程式中變更其磁片區。</span><span class="sxs-lookup"><span data-stu-id="cdf60-239">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="cdf60-240">她可以直接說「更高」，但並不清楚系統應該將磁片區設為多少。</span><span class="sxs-lookup"><span data-stu-id="cdf60-240">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="cdf60-241">使用者可能會說：「讓它變得更大」，但是「有點」難以量化。</span><span class="sxs-lookup"><span data-stu-id="cdf60-241">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="cdf60-242">使用語音移動或調整全息影像也很棘手。</span><span class="sxs-lookup"><span data-stu-id="cdf60-242">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="cdf60-243">**語音輸入偵測的可靠性**雖然語音輸入系統變得更好且更好，但有時可能會不正確地聽到並解讀語音命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-243">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="cdf60-244">重點是要在系統接聽時提供意見反應給使用者，以及系統瞭解如何在正確瞭解使用者的潛在問題上建立清楚，以解決應用程式中的這項挑戰。</span><span class="sxs-lookup"><span data-stu-id="cdf60-244">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="cdf60-245">**共用空間中的語音輸入**在您與其他人共用的空間中，語音可能無法社交接受。</span><span class="sxs-lookup"><span data-stu-id="cdf60-245">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="cdf60-246">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="cdf60-246">Here are a few examples:</span></span>
* <span data-ttu-id="cdf60-247">使用者可能不想干擾其他人（例如，在安靜程式庫或共用的辦公室）</span><span class="sxs-lookup"><span data-stu-id="cdf60-247">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="cdf60-248">使用者可能會覺得很難在公眾中看到自己的溝通，</span><span class="sxs-lookup"><span data-stu-id="cdf60-248">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="cdf60-249">當其他人正在接聽時，使用者可能會覺得不會聽寫個人或機密郵件（包括密碼）</span><span class="sxs-lookup"><span data-stu-id="cdf60-249">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="cdf60-250">**唯一或未知單字的語音輸入**語音輸入的困難也會在使用者聽寫可能對系統不明的字組（例如，昵稱、特定的俚語字組或縮寫）時出現。</span><span class="sxs-lookup"><span data-stu-id="cdf60-250">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="cdf60-251">**學習語音命令**雖然最終目標是要與您的系統自然配合，但應用程式通常還是會依賴特定預先定義的語音命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-251">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="cdf60-252">與一組大量語音命令相關的挑戰，就是如何在不多載使用者的情況下教他們，以及如何協助使用者加以保留。</span><span class="sxs-lookup"><span data-stu-id="cdf60-252">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="cdf60-253">語音反饋狀態</span><span class="sxs-lookup"><span data-stu-id="cdf60-253">Voice feedback states</span></span>

<span data-ttu-id="cdf60-254">當語音正確套用時，使用者會了解**他們能說什麼並獲得清楚的反饋**而知道系統**正確聽懂他們的語音**。</span><span class="sxs-lookup"><span data-stu-id="cdf60-254">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="cdf60-255">這兩個訊號會讓使用者有信心，確信他們可以使用語音作為主要輸入方式。</span><span class="sxs-lookup"><span data-stu-id="cdf60-255">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="cdf60-256">下圖顯示的是當系統辨識到語音輸入時會有什麼情形，以及系統會如何讓使用者知道這一點。</span><span class="sxs-lookup"><span data-stu-id="cdf60-256">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="cdf60-257">![1. 一般資料指標狀態](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="cdf60-257">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="cdf60-258">**1. 一般資料指標狀態**</span><span class="sxs-lookup"><span data-stu-id="cdf60-258">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cdf60-259">![2. 傳達語音意見反應，然後消失](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="cdf60-259">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="cdf60-260">**2. 傳達語音意見反應，然後消失**</span><span class="sxs-lookup"><span data-stu-id="cdf60-260">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cdf60-261">![第.</span><span class="sxs-lookup"><span data-stu-id="cdf60-261">![\*3.</span></span> <span data-ttu-id="cdf60-262">一般游標狀態](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="cdf60-262">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="cdf60-263">**3. 回到一般游標狀態**</span><span class="sxs-lookup"><span data-stu-id="cdf60-263">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="cdf60-264">針對混合實境中的「語音」，使用者最應該了解的事</span><span class="sxs-lookup"><span data-stu-id="cdf60-264">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="cdf60-265">在鎖定按鈕時說出 **"Select"** (您可以在任何地方使用這個命令來按一下按鈕)。</span><span class="sxs-lookup"><span data-stu-id="cdf60-265">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="cdf60-266">在某些應用程式中，您可以說出**應用程式列按鈕的標籤名稱**來採取動作。</span><span class="sxs-lookup"><span data-stu-id="cdf60-266">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="cdf60-267">例如，在查看應用程式的同時，使用者可以說出「Remove」命令來從該世界中移除應用程式 (這可省下必須用手按一下按鈕的時間)。</span><span class="sxs-lookup"><span data-stu-id="cdf60-267">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="cdf60-268">您可以說 **「嗨 Cortana」** 讓 Cortana 開始聽取命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-268">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="cdf60-269">您可以向她問問題 (「嗨 Cortana，艾菲爾鐵塔有多高」)、請她開啟應用程式 (「嗨 Cortana，開啟 Netflix」)，或請她顯示 [開始] 功能表 (「嗨 Cortana，回到首頁」) 等等。</span><span class="sxs-lookup"><span data-stu-id="cdf60-269">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="cdf60-270">使用者會有的語音相關常見問題和疑慮</span><span class="sxs-lookup"><span data-stu-id="cdf60-270">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="cdf60-271">我可以說什麼？</span><span class="sxs-lookup"><span data-stu-id="cdf60-271">What can I say?</span></span>
* <span data-ttu-id="cdf60-272">如何知道系統沒有聽錯？</span><span class="sxs-lookup"><span data-stu-id="cdf60-272">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="cdf60-273">系統一直聽錯我的語音命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-273">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="cdf60-274">我提供了語音命令，系統卻沒有反應。</span><span class="sxs-lookup"><span data-stu-id="cdf60-274">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="cdf60-275">我提供了語音命令，系統卻做出錯誤反應。</span><span class="sxs-lookup"><span data-stu-id="cdf60-275">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="cdf60-276">如何讓我的語音以特定應用程式或應用程式命令作為目標？</span><span class="sxs-lookup"><span data-stu-id="cdf60-276">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="cdf60-277">在 HoloLens 上的全像攝影畫面外，是否可以使用語音來命令物件？</span><span class="sxs-lookup"><span data-stu-id="cdf60-277">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="cdf60-278">通訊</span><span class="sxs-lookup"><span data-stu-id="cdf60-278">Communication</span></span>

<span data-ttu-id="cdf60-279">對於想要利用 HoloLens 所提供之自訂音訊輸入處理選項的應用程式，請務必瞭解您的應用程式可以使用的各種[音訊串流類別](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="cdf60-279">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="cdf60-280">Windows 10 支援數種不同的串流類別和 HoloLens，使用其中三種來啟用自訂處理，以優化專為語音、通訊及其他的麥克風音訊品質，可用於環境的音訊捕捉（也就是「攝影機」）案例。</span><span class="sxs-lookup"><span data-stu-id="cdf60-280">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="cdf60-281">[AudioCategory_Communications 串流] 類別是針對呼叫品質和旁白案例自訂，並為用戶端提供使用者語音的 Riff-16khz-16bit-mono-pcm 24bit mono 音訊串流</span><span class="sxs-lookup"><span data-stu-id="cdf60-281">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="cdf60-282">[AudioCategory_Speech 串流] 類別是針對 HoloLens （Windows）語音引擎自訂，並提供該使用者語音的 Riff-16khz-16bit-mono-pcm 24bit mono 串流。</span><span class="sxs-lookup"><span data-stu-id="cdf60-282">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="cdf60-283">如有需要，可由協力廠商語音引擎使用此類別。</span><span class="sxs-lookup"><span data-stu-id="cdf60-283">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="cdf60-284">[AudioCategory_Other 資料流程] 類別是針對環境環境音訊錄製而自訂，並提供 48kHz 24 位身歷聲音訊串流的用戶端。</span><span class="sxs-lookup"><span data-stu-id="cdf60-284">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="cdf60-285">所有此音訊處理都是硬體加速的，這表示在 HoloLens CPU 上進行相同的處理時，這些功能的耗電量會少很多。</span><span class="sxs-lookup"><span data-stu-id="cdf60-285">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="cdf60-286">避免在 CPU 上執行其他音訊輸入處理，以將系統電池壽命最大化，並利用內建的卸載音訊輸入處理。</span><span class="sxs-lookup"><span data-stu-id="cdf60-286">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="cdf60-287">語言</span><span class="sxs-lookup"><span data-stu-id="cdf60-287">Languages</span></span>

<span data-ttu-id="cdf60-288">HoloLens 2[支援多種語言](https://docs.microsoft.com/hololens/hololens2-language-support)。</span><span class="sxs-lookup"><span data-stu-id="cdf60-288">HoloLens 2 [supports multiple languages](https://docs.microsoft.com/hololens/hololens2-language-support).</span></span> <span data-ttu-id="cdf60-289">請記住，即使已安裝多個鍵盤，或是應用程式嘗試以不同的語言建立語音辨識器，語音命令也一律會以系統的顯示語言執行。</span><span class="sxs-lookup"><span data-stu-id="cdf60-289">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="cdf60-290">疑難排解</span><span class="sxs-lookup"><span data-stu-id="cdf60-290">Troubleshooting</span></span>

<span data-ttu-id="cdf60-291">如果您在使用「選取」和「嘿 Cortana」時遇到任何問題，請嘗試移到更好的空間、離開雜訊來源，或說出更大的聲音。</span><span class="sxs-lookup"><span data-stu-id="cdf60-291">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="cdf60-292">目前，所有的 HoloLens 語音辨識都是針對美國英文的原生喇叭進行微調與優化。</span><span class="sxs-lookup"><span data-stu-id="cdf60-292">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="cdf60-293">對於 Windows Mixed Reality Developer Edition 版本2017，在初始 HMD 連線之後，音訊端點管理邏輯會正常執行（永遠）到電腦桌面。</span><span class="sxs-lookup"><span data-stu-id="cdf60-293">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="cdf60-294">在經過 WMR OOBE 之後，第一次登出/進入事件之前，使用者可能會遇到各種音訊功能問題，範圍從沒有音訊到音訊切換，這取決於第一次連線 HMD 之前設定系統的方式。</span><span class="sxs-lookup"><span data-stu-id="cdf60-294">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="cdf60-295">適用于 Unity 的 MRTK （混合現實工具組）中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="cdf60-295">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="cdf60-296">有了**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**，您就可以輕鬆地在任何物件上指派語音命令。</span><span class="sxs-lookup"><span data-stu-id="cdf60-296">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="cdf60-297">使用 MRTK 的**語音輸入設定檔**來定義您的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cdf60-297">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="cdf60-298">藉由指派**SpeechInputHandler**腳本，您可以讓任何物件回應語音輸入設定檔中所定義的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cdf60-298">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="cdf60-299">SpeechInputHandler 也提供語音確認標籤，以改善使用者的信心。</span><span class="sxs-lookup"><span data-stu-id="cdf60-299">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="cdf60-300">MRTK-Voice 命令</span><span class="sxs-lookup"><span data-stu-id="cdf60-300">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="cdf60-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdf60-301">See also</span></span>
* [<span data-ttu-id="cdf60-302">目光和行動</span><span class="sxs-lookup"><span data-stu-id="cdf60-302">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="cdf60-303">本能互動</span><span class="sxs-lookup"><span data-stu-id="cdf60-303">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="cdf60-304">MR Input 212：語音</span><span class="sxs-lookup"><span data-stu-id="cdf60-304">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="cdf60-305">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="cdf60-305">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="cdf60-306">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="cdf60-306">Voice input in Unity</span></span>](voice-input-in-unity.md)
