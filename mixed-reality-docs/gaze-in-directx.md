---
title: DirectX 中的前端和眼睛視線
description: 使用前端的視線和追蹤在原生的 DirectX 應用程式的開發人員指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 視線、 前端的視線、 標頭追蹤、 追蹤、 directx、 輸入、 全像投影
ms.openlocfilehash: ac72c5305527ed2d68945aeb32051cf2246a736e
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453738"
---
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="e9357-104">前端和眼睛視線 DirectX 中的輸入</span><span class="sxs-lookup"><span data-stu-id="e9357-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="e9357-105">在 Windows Mixed Reality、 眼睛和前端的視線輸入用來判斷使用者正在查看。</span><span class="sxs-lookup"><span data-stu-id="e9357-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="e9357-106">這可以用來驅動主要輸入的模型，例如[前端視線和認可](gaze-and-commit.md)，同時還可以提供內容的互動類型。</span><span class="sxs-lookup"><span data-stu-id="e9357-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="e9357-107">有兩種類型的視線向量可透過 API： 視線和眼睛視線前端。</span><span class="sxs-lookup"><span data-stu-id="e9357-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="e9357-108">同時，提供三個維度的光線，與來源和方向。</span><span class="sxs-lookup"><span data-stu-id="e9357-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="e9357-109">應用程式可以接著 raycast 到場景或真實世界中，並判斷使用者的目標。</span><span class="sxs-lookup"><span data-stu-id="e9357-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="e9357-110">**Head 視線**代表使用者的大腦中指向的方向。</span><span class="sxs-lookup"><span data-stu-id="e9357-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="e9357-111">將此視為位置和裝置本身的正向方向，代表在中心位置與點之間兩個顯示。</span><span class="sxs-lookup"><span data-stu-id="e9357-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="e9357-112">混合實境的所有裝置上使用 Head 視線。</span><span class="sxs-lookup"><span data-stu-id="e9357-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="e9357-113">**眼睛視線**代表使用者的眼睛想要的方向。</span><span class="sxs-lookup"><span data-stu-id="e9357-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="e9357-114">原點是位於使用者的眼睛之間。</span><span class="sxs-lookup"><span data-stu-id="e9357-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="e9357-115">包括追蹤系統監控的混合實境裝置上使用。</span><span class="sxs-lookup"><span data-stu-id="e9357-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="e9357-116">前端和眼睛視線光線都可透過存取[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API。</span><span class="sxs-lookup"><span data-stu-id="e9357-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="e9357-117">只要呼叫[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)接收新 SpatialPointerPose 物件在指定的時間戳記並[座標系統](coordinate-systems-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="e9357-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="e9357-118">此 SpatialPointerPose 包含前端的視線來源和方向。</span><span class="sxs-lookup"><span data-stu-id="e9357-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="e9357-119">它也包含眼睛視線原點與方向追蹤是否可用。</span><span class="sxs-lookup"><span data-stu-id="e9357-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="e9357-120">使用前端的視線</span><span class="sxs-lookup"><span data-stu-id="e9357-120">Using head gaze</span></span>

<span data-ttu-id="e9357-121">若要存取前端的視線，開始藉由呼叫[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)接收新的 SpatialPointerPose 物件。</span><span class="sxs-lookup"><span data-stu-id="e9357-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="e9357-122">您必須傳遞下列參數。</span><span class="sxs-lookup"><span data-stu-id="e9357-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="e9357-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)前端的視線表示所需的座標系統。</span><span class="sxs-lookup"><span data-stu-id="e9357-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="e9357-124">這由*coordinateSystem*變數中的下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9357-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="e9357-125">如需詳細資訊，請瀏覽我們[座標系統](coordinate-systems-in-directx.md)開發人員指南。</span><span class="sxs-lookup"><span data-stu-id="e9357-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="e9357-126">A[時間戳記](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)表示前端的姿勢要求的確切時間。</span><span class="sxs-lookup"><span data-stu-id="e9357-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="e9357-127">您通常會使用對應至目前的框架會顯示時的時間的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="e9357-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="e9357-128">您可以取得此預測的顯示時間戳記[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)物件，它是透過目前可存取[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。</span><span class="sxs-lookup"><span data-stu-id="e9357-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="e9357-129">這個 HolographicFramePrediction 物件由*預測*變數中的下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9357-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="e9357-130">有效 SpatialPointerPose，前端的位置和正向方向就可以存取為屬性。</span><span class="sxs-lookup"><span data-stu-id="e9357-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="e9357-131">下列程式碼示範如何存取它們。</span><span class="sxs-lookup"><span data-stu-id="e9357-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="e9357-132">使用眼睛視線</span><span class="sxs-lookup"><span data-stu-id="e9357-132">Using eye gaze</span></span>

<span data-ttu-id="e9357-133">非常類似於前端的視線眼睛視線 API。</span><span class="sxs-lookup"><span data-stu-id="e9357-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="e9357-134">它會使用相同[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API，可提供無限遠的光線，來源和方向，您可以針對您的場景 raycast。</span><span class="sxs-lookup"><span data-stu-id="e9357-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="e9357-135">唯一的差別是您要明確啟用才能使用它的眼睛追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="e9357-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="e9357-136">這麼做，您需要執行兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="e9357-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="e9357-137">要求使用者使用應用程式中追蹤權限。</span><span class="sxs-lookup"><span data-stu-id="e9357-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="e9357-138">可讓您封裝資訊清單中的 「 視線輸入 」 功能。</span><span class="sxs-lookup"><span data-stu-id="e9357-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="e9357-139">要求的存取權視線輸入</span><span class="sxs-lookup"><span data-stu-id="e9357-139">Requesting access to gaze input</span></span>
<span data-ttu-id="e9357-140">當您的應用程式啟動時，呼叫[EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)眼睛追蹤的要求存取。</span><span class="sxs-lookup"><span data-stu-id="e9357-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="e9357-141">系統會提示使用者如有需要並傳回[GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)一旦授與存取權。</span><span class="sxs-lookup"><span data-stu-id="e9357-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="e9357-142">這會是管理的非同步呼叫，因此它需要一些額外。</span><span class="sxs-lookup"><span data-stu-id="e9357-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="e9357-143">下列範例會啟動等候結果，其儲存至成員變數，呼叫的已卸離 std::thread *m_isEyeTrackingEnabled*。</span><span class="sxs-lookup"><span data-stu-id="e9357-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="e9357-144">正在啟動的已卸離的執行緒只是選項之一來處理非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="e9357-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="e9357-145">或者，您可以使用新[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)所支援的功能C++/WinRT。</span><span class="sxs-lookup"><span data-stu-id="e9357-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="e9357-146">以下是詢問使用者權限的另一個範例：</span><span class="sxs-lookup"><span data-stu-id="e9357-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="e9357-147">EyesPose::IsSupported() 允許應用程式只有眼睛追蹤器時，觸發程序權限對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e9357-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="e9357-148">GazeInputAccessStatus m_gazeInputAccessStatus;這是為了避免一再彈出權限提示。</span><span class="sxs-lookup"><span data-stu-id="e9357-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="e9357-149">宣告*視線輸入*功能</span><span class="sxs-lookup"><span data-stu-id="e9357-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="e9357-150">按兩下 [appxmanifest 中的檔案*方案總管] 中*。</span><span class="sxs-lookup"><span data-stu-id="e9357-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="e9357-151">然後瀏覽至*能力*區段，並檢查*視線輸入*功能。</span><span class="sxs-lookup"><span data-stu-id="e9357-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![視線輸入的功能](images/gaze-input-capability.png)

<span data-ttu-id="e9357-153">這樣會加入下列行以*封裝*appxmanifest 檔案中的區段：</span><span class="sxs-lookup"><span data-stu-id="e9357-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="e9357-154">取得眼睛視線光線</span><span class="sxs-lookup"><span data-stu-id="e9357-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="e9357-155">一旦您收到存取權等，您可以自由抓取眼睛視線光線的每個畫面。</span><span class="sxs-lookup"><span data-stu-id="e9357-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="e9357-156">如同前端的視線，取得[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose)藉由呼叫[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)所需的時間戳記和座標系統。</span><span class="sxs-lookup"><span data-stu-id="e9357-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="e9357-157">包含 SpatialPointerPose [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)物件傳遞[眼睛](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)屬性。</span><span class="sxs-lookup"><span data-stu-id="e9357-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="e9357-158">此為非 null 才會啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="e9357-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="e9357-159">從這裡您可以檢查裝置中的使用者是否藉由呼叫追蹤校正眼睛[EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)。</span><span class="sxs-lookup"><span data-stu-id="e9357-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="e9357-160">接下來，使用[視線](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)屬性來取得[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing 眼睛視線位置和方向。</span><span class="sxs-lookup"><span data-stu-id="e9357-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="e9357-161">視線屬性可以有時可以是 null，因此請務必檢查為這。</span><span class="sxs-lookup"><span data-stu-id="e9357-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="e9357-162">這可能會發生是如果校正的使用者暫時關閉其眼睛。</span><span class="sxs-lookup"><span data-stu-id="e9357-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="e9357-163">下列程式碼示範如何存取眼睛視線無限遠的光線。</span><span class="sxs-lookup"><span data-stu-id="e9357-163">The following code shows how to access the eye gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="e9357-164">相互關聯的視線，與其他輸入</span><span class="sxs-lookup"><span data-stu-id="e9357-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="e9357-165">有時候您可能會發現您需要[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)過去與事件對應。</span><span class="sxs-lookup"><span data-stu-id="e9357-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="e9357-166">比方說，如果使用者執行空中點選時，您的應用程式可能會想知道他們正在看著。</span><span class="sxs-lookup"><span data-stu-id="e9357-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="e9357-167">基於此目的，只使用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)與預測的畫面格時間將不夠準確因為系統的輸入的處理和顯示時間之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="e9357-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="e9357-168">此外，如果使用眼睛視線為目標，我們的眼睛通常完成認可動作前，甚至是移。</span><span class="sxs-lookup"><span data-stu-id="e9357-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="e9357-169">這是不是問題的簡單空中點選，但當長時間的語音命令結合快速眼睛移動變得十分重要。</span><span class="sxs-lookup"><span data-stu-id="e9357-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="e9357-170">若要解決這種情況的一個方法是讓額外的呼叫[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)，使用對應至輸入事件的歷程記錄時間戳記。</span><span class="sxs-lookup"><span data-stu-id="e9357-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="e9357-171">不過，對於透過 SpatialInteractionManager 路由的輸入，還有更容易的方法。</span><span class="sxs-lookup"><span data-stu-id="e9357-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="e9357-172">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)有其自己[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函式。</span><span class="sxs-lookup"><span data-stu-id="e9357-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="e9357-173">會提供完全相互關聯的電話[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)而不需要猜測。</span><span class="sxs-lookup"><span data-stu-id="e9357-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="e9357-174">如需有關使用 SpatialInteractionSourceStates 的詳細資訊，看看[雙手及 DirectX 中的動作控制站](hands-and-motion-controllers-in-directx.md)文件。</span><span class="sxs-lookup"><span data-stu-id="e9357-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9357-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9357-175">See also</span></span>
* [<span data-ttu-id="e9357-176">前端視線，並且認可輸入的模型</span><span class="sxs-lookup"><span data-stu-id="e9357-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e9357-177">HoloLens 2 上追蹤</span><span class="sxs-lookup"><span data-stu-id="e9357-177">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="e9357-178">DirectX 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="e9357-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="e9357-179">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="e9357-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="e9357-180">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="e9357-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
