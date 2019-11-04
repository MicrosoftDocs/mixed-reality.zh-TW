---
title: 快速入門教學課程-2。 初始化您的專案和第一個應用程式
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 3a7b25a17ed1a80834dc7029e172bc7924992b07
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438432"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="b31be-105">2. 初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="b31be-105">2. Initializing your project and first application</span></span>

<span data-ttu-id="b31be-106">在第一課，您將瞭解[混合現實工具組（MRTK）]()所提供的一些功能、啟動 HoloLens 2 的第一個應用程式，然後將它部署到裝置。</span><span class="sxs-lookup"><span data-stu-id="b31be-106">In this first lesson, you'll learn about some of the capabilities the [Mixed Reality Toolkit (MRTK)]() has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="b31be-107">目標</span><span class="sxs-lookup"><span data-stu-id="b31be-107">Objectives</span></span>

* <span data-ttu-id="b31be-108">最佳化 Unity 以用於 HoloLens 開發。</span><span class="sxs-lookup"><span data-stu-id="b31be-108">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="b31be-109">匯入資產並設定場景。</span><span class="sxs-lookup"><span data-stu-id="b31be-109">Import assets and setup the scene.</span></span>
* <span data-ttu-id="b31be-110">空間對應網格、手寫網格和畫面播放速率計數器的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="b31be-110">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter.</span></span>

## <a name="instructions"></a><span data-ttu-id="b31be-111">指示</span><span class="sxs-lookup"><span data-stu-id="b31be-111">Instructions</span></span>

### <a name="create-new-unity-project"></a><span data-ttu-id="b31be-112">建立新的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="b31be-112">Create new Unity project</span></span>

1. <span data-ttu-id="b31be-113">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="b31be-113">Start Unity.</span></span>
2. <span data-ttu-id="b31be-114">選取 **\[New\] (新增)** 。</span><span class="sxs-lookup"><span data-stu-id="b31be-114">Select **New**.</span></span>
<span data-ttu-id="b31be-115">![Lesson1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-115">![Lesson1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)</span></span>
3. <span data-ttu-id="b31be-116">輸入 [專案名稱] （例如 "MixedRealityBase"）。</span><span class="sxs-lookup"><span data-stu-id="b31be-116">Enter a project name (e.g. "MixedRealityBase").</span></span>
<span data-ttu-id="b31be-117">![Lesson1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-117">![Lesson1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)</span></span>
4. <span data-ttu-id="b31be-118">輸入要儲存專案的位置。</span><span class="sxs-lookup"><span data-stu-id="b31be-118">Enter a location to save your project.</span></span>
<span data-ttu-id="b31be-119">![Lesson1 Chapter1 Step4](images/Lesson1Chapter1Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-119">![Lesson1 Chapter1 Step4](images/Lesson1Chapter1Step4.JPG)</span></span>
5. <span data-ttu-id="b31be-120">確定專案已設定為 **3D**。</span><span class="sxs-lookup"><span data-stu-id="b31be-120">Make sure the project is set to **3D**.</span></span>
<span data-ttu-id="b31be-121">![Lesson1 Chapter1 Step5](images/Lesson1Chapter1Step5.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-121">![Lesson1 Chapter1 Step5](images/Lesson1Chapter1Step5.JPG)</span></span>
6. <span data-ttu-id="b31be-122">按一下 [建立專案]。</span><span class="sxs-lookup"><span data-stu-id="b31be-122">Click **Create Project**.</span></span>
<span data-ttu-id="b31be-123">![Lesson1 Chapter1 Step6](images/Lesson1Chapter1Step6.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-123">![Lesson1 Chapter1 Step6](images/Lesson1Chapter1Step6.JPG)</span></span>

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="b31be-124">設定適用於 Windows Mixed Reality 的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="b31be-124">Configure the Unity project for Windows Mixed Reality</span></span>

1. <span data-ttu-id="b31be-125">前往 [檔案] > [**組建設定** **]，以**開啟 [*組建設定*] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b31be-125">Open the *Build Settings* window by going to **File** > **Build Settings**.</span></span>
<span data-ttu-id="b31be-126">![Lesson1 Chapter4 Step1](images/Lesson1Chapter4Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-126">![Lesson1 Chapter4 Step1](images/Lesson1Chapter4Step1.JPG)</span></span>
2. <span data-ttu-id="b31be-127">選取*通用 Windows 平臺*，然後按一下 [**切換平臺**] 按鈕以切換平臺。</span><span class="sxs-lookup"><span data-stu-id="b31be-127">Select the *Universal Windows Platform* and click the **Switch Platform** button to switch platforms.</span></span> <span data-ttu-id="b31be-128">在 HoloLens 2 上執行的應用程式必須通用 Windows 平臺（UWP）相容。</span><span class="sxs-lookup"><span data-stu-id="b31be-128">Applications running on HoloLens 2 are required to be Universal Windows Platform (UWP) compatible.</span></span>
<span data-ttu-id="b31be-129">![Lesson1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-129">![Lesson1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)</span></span>
3. <span data-ttu-id="b31be-130">按一下 [組建] 視窗中的 [**播放程式設定**] 按鈕，並在 [檢查] 面板的 [XR 設定] 下啟用 [*虛擬實境支援*] 核取方塊，即可啟用虛擬實境，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b31be-130">Enable virtual reality by clicking on **Player Settings** button in the Build Window, and enable the *Virtual Reality Supported* checkbox under XR Settings from the inspector panel, as shown in the image below.</span></span> <span data-ttu-id="b31be-131">請注意，您可能需要將 [*組建設定*] 視窗移出，才能看到 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="b31be-131">Note that you might need to drag the *Build Settings* window out of the way in order to see the inspector panel.</span></span> <span data-ttu-id="b31be-132">[*支援的虛擬實境*] 核取方塊也適用于混合現實和增強式現實耳機，因為它是指啟用 stereoscopic 視覺（針對每個眼睛呈現不同的影像）。 ![Tut1-lesson1-step3 Chapter4 步驟 3](images/Lesson1Chapter4Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-132">The *Virtual Reality Supported* checkbox also applies to Mixed Reality and Augmented Reality headsets because it refers to the enabling of stereoscopic vision (rendering different images for each eye.) ![Lesson1 Chapter4 Step3](images/Lesson1Chapter4Step3.JPG)</span></span>
4. <span data-ttu-id="b31be-133">此外，在 [XR 設定] 下，將 [*身歷聲轉譯模式]* 變更為 [*單一傳遞實例*]。</span><span class="sxs-lookup"><span data-stu-id="b31be-133">Also under XR Settings, change the *Stereo Rendering Mode* to *Single Pass Instanced*.</span></span> <span data-ttu-id="b31be-134">這種轉譯[管線的樣式](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)對於 Hololens 2 而言通常是最高效能。</span><span class="sxs-lookup"><span data-stu-id="b31be-134">This [rendering pipeline style](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) is generally most performant for Hololens 2.</span></span> <span data-ttu-id="b31be-135">如果您對 Unity 環境的其他高效能設定感興趣，請遵循[這些指示](recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="b31be-135">If interested in other performant configurations for your Unity environment, follow [these instructions](recommended-settings-for-unity.md).</span></span>
<span data-ttu-id="b31be-136">![Tut1-lesson1-step3 Chapter4 Step3b](images/Lesson1Chapter4Step3b.jpg)</span><span class="sxs-lookup"><span data-stu-id="b31be-136">![Lesson1 Chapter4 Step3b](images/Lesson1Chapter4Step3b.jpg)</span></span>
5. <span data-ttu-id="b31be-137">從相同的 [偵測器] 面板中，確定已在 [*發佈設定*] 下啟用 [功能] 區段中的 [*空間感知*] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b31be-137">From the same inspector panel, ensure that the *Spatial Perception* checkbox in the capabilities section is enabled under *Publishing Settings*.</span></span> <span data-ttu-id="b31be-138">空間感知可讓我們將混合現實裝置上的空間對應網格視覺化，例如 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="b31be-138">Spatial Perception allows us to visualize the spatial mapping mesh on a mixed reality device, such as HoloLens 2.</span></span> <span data-ttu-id="b31be-139">在 [偵測器] 面板的 [XR 設定] 和 [其他設定] 底下，可以找到發佈設定。</span><span class="sxs-lookup"><span data-stu-id="b31be-139">Publishing Settings are found in the inspector panel, above XR Settings and under Other Settings.</span></span>
<span data-ttu-id="b31be-140">![Lesson1 Chapter4 Step4](images/Lesson1Chapter4Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-140">![Lesson1 Chapter4 Step4](images/Lesson1Chapter4Step4.JPG)</span></span>

> [!NOTE]
> <span data-ttu-id="b31be-141">雖然不在本節中使用，但您可能會想要啟用的一些其他常見功能包括語音命令的*麥克風*，以及連接到需要網路連線之服務的*InternetClient* 。</span><span class="sxs-lookup"><span data-stu-id="b31be-141">While not used in this section, some other common capabilities you might want to enable include the *Microphone* for voice commands, and *InternetClient* for connecting to services requiring a network connection.</span></span>

### <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="b31be-142">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="b31be-142">Import the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="b31be-143">下載最新的[混合現實工具](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)組 Unity 封裝，並將其儲存至您電腦上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b31be-143">Download the latest [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity packages, and save them to a folder on your PC.</span></span>

2. <span data-ttu-id="b31be-144">匯入每個*混合現實工具*組套件。</span><span class="sxs-lookup"><span data-stu-id="b31be-144">Import each of the *Mixed Reality Toolkit* packages.</span></span> <span data-ttu-id="b31be-145">首先按一下 **資產**， > 匯**入** > **自訂套件**。</span><span class="sxs-lookup"><span data-stu-id="b31be-145">Start by clicking on **Assets** > **Import** > **Custom Package**.</span></span> <span data-ttu-id="b31be-146">選取在步驟1中下載的其中一個*混合現實工具*組套件，然後將其開啟以開始匯入程式。</span><span class="sxs-lookup"><span data-stu-id="b31be-146">Select one of the *Mixed Reality Toolkit* packages downloaded in Step 1 and open it to begin the importing process.</span></span> <span data-ttu-id="b31be-147">請稍候幾分鐘來完成匯入程序。</span><span class="sxs-lookup"><span data-stu-id="b31be-147">Please allow a few minutes for the importing process.</span></span>
    <span data-ttu-id="b31be-148">![Lesson1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-148">![Lesson1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)</span></span>

3. <span data-ttu-id="b31be-149">在下一個快顯視窗中，按一下 [匯**入**] 開始將選取的封裝匯入 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="b31be-149">In the next pop-up window, click **Import** to begin importing the selected package into the Unity project.</span></span> <span data-ttu-id="b31be-150">確認所有專案都已核取，如影像中所示。</span><span class="sxs-lookup"><span data-stu-id="b31be-150">Ensure all items are checked as shown in the image.</span></span>
    <span data-ttu-id="b31be-151">![Tut1-lesson1-step3 Chapter2 步驟 3](images/Lesson1Chapter2Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-151">![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG)</span></span>
4. <span data-ttu-id="b31be-152">針對每個已下載的套件*混合現實工具*組套件，重複上述的步驟2和3。</span><span class="sxs-lookup"><span data-stu-id="b31be-152">Repeat steps 2 and 3 above for each package *Mixed Reality Toolkit* package downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="b31be-153">如果您看到快顯對話方塊，要求套用混合現實工具組預設設定，**請按一下 [** 套用]。</span><span class="sxs-lookup"><span data-stu-id="b31be-153">If you see a pop-up dialog box asking to apply the Mixed Reality Toolkit default settings, click **Apply**.</span></span> <span data-ttu-id="b31be-154">匯入以進行自動化安裝時，MRTK 會分析您的專案是否有任何遺漏的建議設定。</span><span class="sxs-lookup"><span data-stu-id="b31be-154">MRTK analyzes your project for any missing recommended settings when imported for automated setup.</span></span>

![Tut1-lesson1-step3 Chapter2 步驟3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="b31be-156">設定混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="b31be-156">Configure the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="b31be-157">藉由選取 [混合] [**現實工具**組] > [**加入場景] 並設定**，將*混合現實工具*組新增至您目前的場景。</span><span class="sxs-lookup"><span data-stu-id="b31be-157">Add the *Mixed Reality Toolkit* to your current scene by selecting **Mixed Reality Toolkit** > **Add to Scene and Configure..**</span></span> <span data-ttu-id="b31be-158">從功能表列。</span><span class="sxs-lookup"><span data-stu-id="b31be-158">from the menu bar.</span></span> <span data-ttu-id="b31be-159">如果您在匯入混合實境工具組之後沒有看到此功能表項目，請重新啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="b31be-159">If you don't see this menu item after importing the mixed reality toolkit, please restart Unity.</span></span>
  <span data-ttu-id="b31be-160">![Lesson1 Chapter3 Step1](images/Lesson1Chapter3Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-160">![Lesson1 Chapter3 Step1](images/Lesson1Chapter3Step1.JPG)</span></span>

> [!NOTE]
> <span data-ttu-id="b31be-161">您可能會看到快顯對話方塊，要求您選取[混合現實工具組的設定檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。</span><span class="sxs-lookup"><span data-stu-id="b31be-161">You may see a pop-up dialog box asking to select a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="b31be-162">若是如此，請選取 **[確定]** ，然後選擇名為 *"DefaultMixedRealityToolkitConfigurationProfile"* 的設定檔。</span><span class="sxs-lookup"><span data-stu-id="b31be-162">If so, select **Ok**, and choose the profile named *"DefaultMixedRealityToolkitConfigurationProfile"*.</span></span>

2. <span data-ttu-id="b31be-163">您的場景會有數個新專案和修改。</span><span class="sxs-lookup"><span data-stu-id="b31be-163">Your scene will have several new items and modifications.</span></span> <span data-ttu-id="b31be-164">**按一下** 檔案 > **另存**新檔，將場景儲存在不同名稱下，並為您的場景提供名稱，例如*BaseScene*。</span><span class="sxs-lookup"><span data-stu-id="b31be-164">Save your scene under a different name by clicking **File** > **Save As**, and give your scene a name, such as *BaseScene*.</span></span> <span data-ttu-id="b31be-165">將您的場景儲存到專案 [*資產*] 資料夾中的 [*場景*] 資料夾，以保持其組織。</span><span class="sxs-lookup"><span data-stu-id="b31be-165">Keep your scene organized by saving it to the *Scenes* folder in your project’s *Assets* folder.</span></span>
  <span data-ttu-id="b31be-166">![Lesson1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
  ![Lesson1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-166">![Lesson1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Lesson1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)</span></span>

### <a name="build-your-application-to-your-device"></a><span data-ttu-id="b31be-167">對您的裝置建置應用程式</span><span class="sxs-lookup"><span data-stu-id="b31be-167">Build your application to your device</span></span>

1. <span data-ttu-id="b31be-168">如果您關閉了先前章節的 [*組建設定*] 視窗，請前往 [檔案 **] > [** **組建設定**] 再次開啟 [*組建設定*] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b31be-168">If you closed the *Build Settings* window from the previous sections, open the *Build Settings* window again by going to **File** > **Build Settings**.</span></span>
    <span data-ttu-id="b31be-169">![Lesson1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-169">![Lesson1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="b31be-170">當您的場景在 Unity 中開啟時，請按一下 [**新增開啟的場景**] 按鈕，以確定您剛建立的場景位於組建清單的*場景*中。</span><span class="sxs-lookup"><span data-stu-id="b31be-170">Ensure the scene you just created is in the *Scenes in Build* list by clicking on the **Add Open Scenes** button while your scene is open in Unity.</span></span>

3. <span data-ttu-id="b31be-171">按下 [**組建**] 按鈕以開始建立程式。</span><span class="sxs-lookup"><span data-stu-id="b31be-171">Press the **Build** button to begin the build process.</span></span>
    <span data-ttu-id="b31be-172">![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-172">![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="b31be-173">為您的應用程式建立並命名新資料夾。</span><span class="sxs-lookup"><span data-stu-id="b31be-173">Create and name a new folder for your application.</span></span> <span data-ttu-id="b31be-174">在下圖中，已建立名為 App 的資料夾來包含應用程式。</span><span class="sxs-lookup"><span data-stu-id="b31be-174">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="b31be-175">按一下 [**選取資料夾**]，開始建立新建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b31be-175">Click **Select Folder** to begin building to the newly created folder.</span></span> <span data-ttu-id="b31be-176">組建完成之後，您可以關閉 Unity 中的 [*組建設定*] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b31be-176">After the build has completed, you can close the *Build Settings* window in Unity.</span></span>
    <span data-ttu-id="b31be-177">![Lesson1 Chapter5 Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-177">![Lesson1 Chapter5 Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b31be-178">如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。</span><span class="sxs-lookup"><span data-stu-id="b31be-178">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="b31be-179">如果您看到錯誤，例如「錯誤： CS0246 = 類型或命名空間名稱 "XX" 找不到（您是否遺漏 using 指示詞或元件參考？）。</span><span class="sxs-lookup"><span data-stu-id="b31be-179">If you see an error, such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="b31be-180">若是如此，您可能需要安裝[Windows 10 SDK （10.0.18362.0）](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span><span class="sxs-lookup"><span data-stu-id="b31be-180">If so, then you might need to install [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span></span>

5. <span data-ttu-id="b31be-181">在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="b31be-181">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="b31be-182">如果您使用專案的替代名稱，請按兩下 [ *MixedRealityBase* ] 方案或對應的名稱，以在 Visual Studio 中開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="b31be-182">Double click on the *MixedRealityBase.sln* solution, or the corresponding name, if you used an alternative name for your project, to open the solution file in Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="b31be-183">請務必開啟新建立的資料夾（也就是*應用程式*資料夾，如果遵循先前步驟中的命名慣例），因為該資料夾外部會有類似的名稱 .sln 檔案，不會與組建資料夾內的 .sln 檔案混淆。</span><span class="sxs-lookup"><span data-stu-id="b31be-183">Be sure to open the newly created folder (i.e. the *App* folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> <span data-ttu-id="b31be-184">資料夾結構看起來應該類似下圖。</span><span class="sxs-lookup"><span data-stu-id="b31be-184">The folder structure should look similar to the image below.</span></span>
>
> <span data-ttu-id="b31be-185">如果 Visual Studio 要求您安裝新元件，請花一點時間確認是否已安裝所有必要元件，如同 [[安裝工具] 頁面](install-the-tools.md)中所指定</span><span class="sxs-lookup"><span data-stu-id="b31be-185">If Visual Studio asks you to install new components, please take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

6. <span data-ttu-id="b31be-187">將 HoloLens 2 連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="b31be-187">Connect your HoloLens 2 into your PC.</span></span> <span data-ttu-id="b31be-188">雖然這些指示會假設您要部署至 HoloLens 2 裝置，但您也可以選擇部署至[hololens 2 模擬器](using-the-hololens-emulator.md)，或選擇建立用於側[載的應用程式套件](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="b31be-188">While these instructions assume you will be deploying to a HoloLens 2 device, you might also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b31be-189">在建立您的裝置之前，裝置必須處於*開發人員模式*，並與您的開發電腦配對。</span><span class="sxs-lookup"><span data-stu-id="b31be-189">Before building to your device, the device must be in *Developer Mode* and paired with your development machine.</span></span> <span data-ttu-id="b31be-190">您可以遵循[這些指示](using-visual-studio.md)來完成這兩個步驟</span><span class="sxs-lookup"><span data-stu-id="b31be-190">Both of these steps can be completed by following [these instructions](using-visual-studio.md)</span></span>

8. <span data-ttu-id="b31be-191">藉由選取*版本*或*主要*設定和*ARM*架構，設定用來建立 HoloLens 2 的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b31be-191">Configure Visual Studio for building to your HoloLens 2 by selecting the *Release* or *Master* configuration and the *ARM* architecture.</span></span>
    <span data-ttu-id="b31be-192">![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="b31be-192">![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)</span></span>

9. <span data-ttu-id="b31be-193">最後一個步驟是選取 [ **Debug** > **啟動但不進行調試**程式]，以建立並部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="b31be-193">The final step is to build and deploy to your device by selecting **Debug** > **Start without debugging**.</span></span> <span data-ttu-id="b31be-194">選取 [*啟動但不進行調試*程式]，會在組建成功時立即在您的裝置上啟動，但不會附加偵錯工具，而且資訊會出現在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="b31be-194">Selecting *Start without Debugging* causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="b31be-195">這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。</span><span class="sxs-lookup"><span data-stu-id="b31be-195">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

> [!NOTE]
> <span data-ttu-id="b31be-196">您也可以選取 [**組建** > **部署解決方案**]，以部署至您的裝置，而不會自動啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="b31be-196">You might also select **Build** > **Deploy Solution** to deploy to your device without having the application automatically start.</span></span>

![Tut1-lesson1-step3 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a><span data-ttu-id="b31be-198">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b31be-198">Congratulations</span></span>

<span data-ttu-id="b31be-199">您現在已部署第一個 HoloLens 2 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b31be-199">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="b31be-200">當您逐步解說時，您應該會看到一個空間對應網格，其中涵蓋 HoloLens 2 已察覺到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="b31be-200">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="b31be-201">此外，您應該會看到手中的指標，以及用來追蹤應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="b31be-201">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="b31be-202">這些只是混合實境工具組的幾個現成基本項目。</span><span class="sxs-lookup"><span data-stu-id="b31be-202">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="b31be-203">在接下來的課程中，您將開始在場景中新增更多內容和互動性，讓您可以完整地探索 HoloLens 2 和混合現實工具組的功能。</span><span class="sxs-lookup"><span data-stu-id="b31be-203">In the lessons to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="b31be-204">在[第5課](mrlearning-base-ch5.md)中，您將會討論如何使用語音命令來切換畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="b31be-204">You will cover how to toggle the frame rate counter using a voice command in [Lesson 5](mrlearning-base-ch5.md).</span></span> <span data-ttu-id="b31be-205">通常建議您在開發期間隨時保持可見的視覺化分析工具，以瞭解程式碼變更可能會影響效能的時機。</span><span class="sxs-lookup"><span data-stu-id="b31be-205">It is generally recommended to keep the visual profiler visible at all times during development to understand when code changes may have impacted perf.</span></span> <span data-ttu-id="b31be-206">Hololens 2 應用程式應[持續以 60 FPS 執行](understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="b31be-206">Hololens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="b31be-207">下一課： 3. 建立使用者介面和設定混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="b31be-207">Next Lesson: 3. Creating user interface and configure Mixed Reality Toolkit </span></span>](mrlearning-base-ch2.md)
