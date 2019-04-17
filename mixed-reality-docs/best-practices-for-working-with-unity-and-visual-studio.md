---
title: 使用 Unity 和 Visual Studio 的最佳作法
description: 秘訣與技巧，來簡化使用 Unity 和 Visual Studio 中建立的混合的實境應用程式的工作流程。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: visual studio 中，HoloLens，沈浸式耳機，unity，部署
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596686"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="d7213-104">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="d7213-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="d7213-105">使用 Unity 建立混合的實境應用程式開發人員必須 Unity 和 Visual Studio 來建置應用程式套件部署到 HoloLens 和/或沈浸式耳機之間切換。</span><span class="sxs-lookup"><span data-stu-id="d7213-105">A developer creating a mixed reality application with Unity will need to switch between Unity and Visual Studio to build the application package that is deployed to HoloLens and/or an immersive headset.</span></span> <span data-ttu-id="d7213-106">根據預設的 Visual Studio 的兩個執行個體都需要 （一個修改 Unity 指令碼），另一個来部署到裝置和偵錯。</span><span class="sxs-lookup"><span data-stu-id="d7213-106">By default two instances of Visual Studio are required (one to modify Unity scripts and one to deploy to the device and debug).</span></span> <span data-ttu-id="d7213-107">下列程序允許使用單一的 Visual Studio 執行個體的開發、 減少匯出 Unity 專案的頻率和改善的偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="d7213-107">The following procedure allows development using single Visual Studio instance, reduces the frequency of exporting Unity projects, and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="d7213-108">改善的反覆項目時間</span><span class="sxs-lookup"><span data-stu-id="d7213-108">Improving iteration time</span></span>

<span data-ttu-id="d7213-109">常見的工作流程問題時使用 Unity 和 Visual Studio 有多個視窗開啟的 Visual Studio 和需要不斷切換來逐一查看的 Visual Studio 和 Unity。</span><span class="sxs-lookup"><span data-stu-id="d7213-109">A common workflow problem when working with Unity and Visual Studio is having multiple windows of Visual Studio open and the need to constantly switch between Visual Studio and Unity to iterate.</span></span>
1. <span data-ttu-id="d7213-110">**Unity** -修改場景和匯出的 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="d7213-110">**Unity** - for modifying the scene and exporting a Visual Studio solution</span></span>
2. <span data-ttu-id="d7213-111">**Visual Studio (1)** -適用於修改指令碼</span><span class="sxs-lookup"><span data-stu-id="d7213-111">**Visual Studio (1)** - for modifying scripts</span></span>
3. <span data-ttu-id="d7213-112">**Visual Studio (2)** -針對建置和部署 Unity 到裝置中匯出的 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="d7213-112">**Visual Studio (2)** - for building and deploying the Unity exported Visual Studio solution to the device</span></span>

<span data-ttu-id="d7213-113">幸運的是，還有以簡化的 Visual Studio 的單一執行個體，並減少經常匯出從 Unity 的方法。</span><span class="sxs-lookup"><span data-stu-id="d7213-113">Luckily, there's a way to streamline to a single instance of Visual Studio and cut down on frequent exports from Unity.</span></span>

<span data-ttu-id="d7213-114">當[匯出您的專案，從 Unity](exporting-and-building-a-unity-visual-studio-solution.md)，檢查**UnityC#專案**[檔案 > 建置設定] 功能表中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d7213-114">When [exporting your project from Unity](exporting-and-building-a-unity-visual-studio-solution.md), check the **Unity C# Projects** checkbox in the "File > Build Settings" menu.</span></span> <span data-ttu-id="d7213-115">現在，您匯出從 Unity 專案會包含您的專案的所有C#指令碼，並有幾項優點：</span><span class="sxs-lookup"><span data-stu-id="d7213-115">Now, the project you export from Unity includes all of your project's C# scripts and has several benefits:</span></span>
* <span data-ttu-id="d7213-116">使用 Visual Studio 的相同執行個體，用來撰寫指令碼和建置/部署您的專案</span><span class="sxs-lookup"><span data-stu-id="d7213-116">Use the same instance of Visual Studio for writing scripts and building/deploying your project</span></span>
* <span data-ttu-id="d7213-117">匯出從 Unity 場景變更在 Unity Editor; 時，才變更指令碼的內容可以在 Visual Studio 中完成而不重新匯出。</span><span class="sxs-lookup"><span data-stu-id="d7213-117">Export from Unity only when the scene is changed in the Unity Editor; changing the contents of scripts can be done in Visual Studio without re-exporting.</span></span>

<span data-ttu-id="d7213-118">具有**UnityC#專案**啟用，只有一個執行個體的每個程式需要開啟：</span><span class="sxs-lookup"><span data-stu-id="d7213-118">With **Unity C# Projects** enabled, only one instance of each program need be opened:</span></span>
1. <span data-ttu-id="d7213-119">**Unity** -修改場景和匯出的 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="d7213-119">**Unity** - for modifying the scene and exporting a Visual Studio solution</span></span>
2. <span data-ttu-id="d7213-120">**Visual Studio** -修改指令碼，然後建置和部署 Unity 到裝置中匯出的 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="d7213-120">**Visual Studio** - for modifying scripts then building and deploying the Unity exported Visual Studio solution to the device</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="d7213-121">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="d7213-121">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="d7213-122">下載[Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)</span><span class="sxs-lookup"><span data-stu-id="d7213-122">Download [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)</span></span>

<span data-ttu-id="d7213-123">**Visual Studio Tools for Unity 的優點**</span><span class="sxs-lookup"><span data-stu-id="d7213-123">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="d7213-124">偵錯 Unity 編輯器中的 play 模式，從 Visual Studio 中放置中斷點，評估變數和複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="d7213-124">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="d7213-125">找不到您的指令碼完全相同的階層，會顯示 Unity 使用 Unity Project Explorer。</span><span class="sxs-lookup"><span data-stu-id="d7213-125">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="d7213-126">取得直接在 Visual Studio 的 Unity 主控台。</span><span class="sxs-lookup"><span data-stu-id="d7213-126">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="d7213-127">使用精靈來快速建立，或瀏覽至 指令碼。</span><span class="sxs-lookup"><span data-stu-id="d7213-127">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="d7213-128">公開 （expose)C#類別用來微調簡單的變數</span><span class="sxs-lookup"><span data-stu-id="d7213-128">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="d7213-129">有兩種方式來公開類別變數。</span><span class="sxs-lookup"><span data-stu-id="d7213-129">There are two ways to expose class variables.</span></span> <span data-ttu-id="d7213-130">若要這樣做的建議的方式是將 [SerializeField] 屬性加入至您的私用變數。</span><span class="sxs-lookup"><span data-stu-id="d7213-130">The recommended way to do so is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="d7213-131">這可讓他們存取從編輯器，但未以程式設計方式公開。</span><span class="sxs-lookup"><span data-stu-id="d7213-131">This allows them to be accessed from the editor but not programatically exposed.</span></span>  <span data-ttu-id="d7213-132">另一個選項是對C#類別的變數公開 」 以在編輯器 UI 中公開它們。</span><span class="sxs-lookup"><span data-stu-id="d7213-132">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="d7213-133">這兩種方法可使您能夠輕鬆地調整同時播放編輯器中的變數。</span><span class="sxs-lookup"><span data-stu-id="d7213-133">Both approaches make it possible to easily tweak variables while playing in-editor.</span></span> <span data-ttu-id="d7213-134">這是用來微調互動 mechanic 屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="d7213-134">This is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="d7213-135">Windows SDK 或 Unity 在升級後，重新產生 UWP 的 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="d7213-135">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="d7213-136">簽入原始檔控制的 UWP 的 Visual Studio 解決方案可以取得升級至新的 Windows SDK 或 Unity 引擎之後過期。</span><span class="sxs-lookup"><span data-stu-id="d7213-136">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="d7213-137">您可以解決此問題在升級之後從 Unity 建置新的 UWP 方案，然後將差異合併到簽入的解決方案。</span><span class="sxs-lookup"><span data-stu-id="d7213-137">You can resolve this after the upgrade by building a new UWP solution from Unity, then merging any differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="d7213-138">使用文字格式的資產，以便比較的內容變更</span><span class="sxs-lookup"><span data-stu-id="d7213-138">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="d7213-139">以文字格式儲存的資產，讓您更輕鬆地檢閱在 Visual Studio 中的內容變更差異比對。</span><span class="sxs-lookup"><span data-stu-id="d7213-139">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="d7213-140">您可以啟用 [編輯 > 專案設定 > 編輯器] 中變更**資產序列化**模式**強制文字**。</span><span class="sxs-lookup"><span data-stu-id="d7213-140">You can enable this in "Edit > Project Settings > Editor" by changing **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="d7213-141">不過，合併變更文字的資產檔案很容易發生錯誤，而且不建議使用，因此請考慮啟用二進位的獨佔簽出原始檔控制系統中。</span><span class="sxs-lookup"><span data-stu-id="d7213-141">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control system.</span></span>
