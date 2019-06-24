## <a name="lesson-2"></a><span data-ttu-id="07cec-101">第 2 課</span><span class="sxs-lookup"><span data-stu-id="07cec-101">Lesson 2</span></span>

<span data-ttu-id="07cec-102">在第 2 課中，我們會新增離線模式，讓我們時無法連線到 Azure 服務，我們將執行本機語音轉換文字翻譯*模擬*中斷連線的狀態。</span><span class="sxs-lookup"><span data-stu-id="07cec-102">In Lesson 2, we will add an Offline mode that will allow us to perform local speech-to-text translation when we are unable to connect to the Azure service and we will *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="07cec-103">選取階層中的"Lunarcom_Base 」 物件，並在 [偵測器] 面板中按一下 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="07cec-103">Select the "Lunarcom_Base" object in the hierarchy and click “Add Component” in the inspector panel.</span></span> <span data-ttu-id="07cec-104">搜尋並選取 「 Lunarcom 離線辨識。 」</span><span class="sxs-lookup"><span data-stu-id="07cec-104">Search for and select the "Lunarcom Offline Recognition."</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. <span data-ttu-id="07cec-106">按一下 「 LunarcomOfflineRecognizer"中的下拉式清單，然後選取 [已啟用]。</span><span class="sxs-lookup"><span data-stu-id="07cec-106">Click the dropdown in the “LunarcomOfflineRecognizer” and select “Enabled.”</span></span> <span data-ttu-id="07cec-107">這將程式專案，以採取行動，例如使用者不需要連接。</span><span class="sxs-lookup"><span data-stu-id="07cec-107">This will program the project to act like the user doesn't have connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="07cec-109">現在，按下播放在 Unity 編輯器中，並加以測試。</span><span class="sxs-lookup"><span data-stu-id="07cec-109">Now, press play on the Unity Editor and test it.</span></span> <span data-ttu-id="07cec-110">按下中在場景中左下角的麥克風，並開始說話。</span><span class="sxs-lookup"><span data-stu-id="07cec-110">Press the microphone in the bottom left hand corner in the scene and begin speaking.</span></span> 

> <span data-ttu-id="07cec-111">注意： 我們離線，因為已停用喚醒 Word 的功能。</span><span class="sxs-lookup"><span data-stu-id="07cec-111">note: because we’re offline, the Wake Word functionality has been disabled.</span></span> <span data-ttu-id="07cec-112">因此，您必須實際在每次您想要讓您的語音辨識按一下麥克風時離線。</span><span class="sxs-lookup"><span data-stu-id="07cec-112">So, you will have to physically click the microphone every time you wish to have your speech recognized while offline.</span></span> 

<span data-ttu-id="07cec-113">以下是範例中的場景可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="07cec-113">Below is an example of what your scene could look like:</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="07cec-115">恭喜！</span><span class="sxs-lookup"><span data-stu-id="07cec-115">Congratulations</span></span>

<span data-ttu-id="07cec-116">已啟用離線模式 ！</span><span class="sxs-lookup"><span data-stu-id="07cec-116">The offline mode has been enabled!</span></span> <span data-ttu-id="07cec-117">現在當您準備離開任何形式的網際網路，您仍可使用您的專案與 Speech SDK ！</span><span class="sxs-lookup"><span data-stu-id="07cec-117">Now when you're away from any form of internet, you can still work on your project with Speech-SDK!</span></span> 

[<span data-ttu-id="07cec-118">下一課：第 3 課 SpeechSDK</span><span class="sxs-lookup"><span data-stu-id="07cec-118">Next Lesson: SpeechSDK Lesson 3</span></span>](link placeholder)

