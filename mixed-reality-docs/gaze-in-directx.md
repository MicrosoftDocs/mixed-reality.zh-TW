---
title: DirectX 中的列印頭和眼睛
description: 在原生 DirectX 應用程式中使用 head 注視和眼追蹤的開發人員指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 眼睛眼, 列印頭, 頭追蹤, 眼睛追蹤, directx, 輸入, 全息影像
ms.openlocfilehash: 2197f0ba3ecb77188d532d77ba29595c380a039d
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122052"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="36979-104">DirectX 中的列印頭和眼睛輸入</span><span class="sxs-lookup"><span data-stu-id="36979-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="36979-105">在 Windows Mixed Reality 中, 眼睛和列印頭的輸入是用來判斷使用者正在查看的內容。</span><span class="sxs-lookup"><span data-stu-id="36979-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="36979-106">這可用來驅動主要輸入模型 (例如[head 和 commit](gaze-and-commit.md)), 也可以提供互動類型的內容。</span><span class="sxs-lookup"><span data-stu-id="36979-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="36979-107">有兩種類型的注視向量可透過 API 取得: 頭眼和眼睛。</span><span class="sxs-lookup"><span data-stu-id="36979-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="36979-108">這兩者都是以具有原點和方向的三維光線形式提供。</span><span class="sxs-lookup"><span data-stu-id="36979-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="36979-109">然後, 應用程式可以 raycast 至其幕後或真實世界, 並判斷使用者的目標。</span><span class="sxs-lookup"><span data-stu-id="36979-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="36979-110">**Head** , 代表使用者的標頭指向的方向。</span><span class="sxs-lookup"><span data-stu-id="36979-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="36979-111">請將此視為裝置本身的位置和正向方向, 其位置代表兩個顯示器之間的中心點。</span><span class="sxs-lookup"><span data-stu-id="36979-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="36979-112">所有混合現實裝置上都可使用 Head 注視。</span><span class="sxs-lookup"><span data-stu-id="36979-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="36979-113">**眼睛**指的是使用者眼所期待的方向。</span><span class="sxs-lookup"><span data-stu-id="36979-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="36979-114">原點位於使用者的眼睛之間。</span><span class="sxs-lookup"><span data-stu-id="36979-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="36979-115">其適用于包含眼睛追蹤系統的混合現實裝置。</span><span class="sxs-lookup"><span data-stu-id="36979-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="36979-116">Head 和眼睛光線都可透過[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API 來存取。</span><span class="sxs-lookup"><span data-stu-id="36979-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="36979-117">只要呼叫[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) , 即可在指定的時間戳記和[座標系統](coordinate-systems-in-directx.md)上接收新的 SpatialPointerPose 物件。</span><span class="sxs-lookup"><span data-stu-id="36979-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="36979-118">此 SpatialPointerPose 包含一個頭部的原點和方向。</span><span class="sxs-lookup"><span data-stu-id="36979-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="36979-119">它也包含眼睛的原點和方向 (如果有眼睛追蹤可用的話)。</span><span class="sxs-lookup"><span data-stu-id="36979-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="36979-120">使用頭部注視</span><span class="sxs-lookup"><span data-stu-id="36979-120">Using head-gaze</span></span>

<span data-ttu-id="36979-121">若要存取頭部, 請先呼叫[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)來接收新的 SpatialPointerPose 物件。</span><span class="sxs-lookup"><span data-stu-id="36979-121">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="36979-122">您必須傳遞下列參數。</span><span class="sxs-lookup"><span data-stu-id="36979-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="36979-123">[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , 代表 head 的所需座標系統。</span><span class="sxs-lookup"><span data-stu-id="36979-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="36979-124">這會由下列程式碼中的*coordinateSystem*變數表示。</span><span class="sxs-lookup"><span data-stu-id="36979-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="36979-125">如需詳細資訊, 請造訪我們的[座標系統](coordinate-systems-in-directx.md)開發人員指南。</span><span class="sxs-lookup"><span data-stu-id="36979-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="36979-126">[時間戳記](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp), 表示要求之 head 姿勢的確切時間。</span><span class="sxs-lookup"><span data-stu-id="36979-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="36979-127">通常您會使用時間戳, 其對應到目前畫面格的顯示時間。</span><span class="sxs-lookup"><span data-stu-id="36979-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="36979-128">您可以從[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)物件取得這個預測的顯示時間戳記, 這可透過目前的[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)來存取。</span><span class="sxs-lookup"><span data-stu-id="36979-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="36979-129">這個 HolographicFramePrediction 物件是由下列程式碼中的*預測*變數表示。</span><span class="sxs-lookup"><span data-stu-id="36979-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="36979-130">一旦您擁有有效的 SpatialPointerPose, 就可以存取標頭位置和正向方向作為屬性。</span><span class="sxs-lookup"><span data-stu-id="36979-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="36979-131">下列程式碼說明如何存取它們。</span><span class="sxs-lookup"><span data-stu-id="36979-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="36979-132">使用眼注視</span><span class="sxs-lookup"><span data-stu-id="36979-132">Using eye-gaze</span></span>

<span data-ttu-id="36979-133">眼睛的 API 非常類似于列印頭。</span><span class="sxs-lookup"><span data-stu-id="36979-133">The eye-gaze API is very similar to head-gaze.</span></span>  <span data-ttu-id="36979-134">它會使用相同的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, 它會提供您可以針對場景 raycast 的光線來源和方向。</span><span class="sxs-lookup"><span data-stu-id="36979-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="36979-135">唯一的差別在於, 您必須先明確啟用眼睛追蹤, 才能使用它。</span><span class="sxs-lookup"><span data-stu-id="36979-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="36979-136">為此, 您需要執行兩個步驟:</span><span class="sxs-lookup"><span data-stu-id="36979-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="36979-137">要求使用者在您的應用程式中使用目視追蹤的許可權。</span><span class="sxs-lookup"><span data-stu-id="36979-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="36979-138">在您的套件資訊清單中啟用「注視輸入」功能。</span><span class="sxs-lookup"><span data-stu-id="36979-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="36979-139">要求存取眼睛輸入</span><span class="sxs-lookup"><span data-stu-id="36979-139">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="36979-140">當您的應用程式啟動時, 呼叫[EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)以要求存取眼追蹤。</span><span class="sxs-lookup"><span data-stu-id="36979-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="36979-141">系統會視需要提示使用者, 並在授與存取權之後傳回[GazeInputAccessStatus:: 允許](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)。</span><span class="sxs-lookup"><span data-stu-id="36979-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="36979-142">這是非同步呼叫, 因此需要一些額外的管理。</span><span class="sxs-lookup"><span data-stu-id="36979-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="36979-143">下列範例會啟動中斷連結的 std:: thread 以等候結果, 並將其儲存至名為*m_isEyeTrackingEnabled*的成員變數。</span><span class="sxs-lookup"><span data-stu-id="36979-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="36979-144">啟動卸離的執行緒只是處理非同步呼叫的一個選項。</span><span class="sxs-lookup"><span data-stu-id="36979-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="36979-145">或者, 您可以使用C++/winrt 所支援的新[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)功能</span><span class="sxs-lookup"><span data-stu-id="36979-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="36979-146">以下是詢問使用者權限的另一個範例:</span><span class="sxs-lookup"><span data-stu-id="36979-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="36979-147">EyesPose:: IsSupported () 可讓應用程式只在有眼睛追蹤器時觸發許可權對話方塊。</span><span class="sxs-lookup"><span data-stu-id="36979-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="36979-148">GazeInputAccessStatus m_gazeInputAccessStatus;這是為了防止再次彈出許可權提示。</span><span class="sxs-lookup"><span data-stu-id="36979-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="36979-149">宣告*注視輸入*功能</span><span class="sxs-lookup"><span data-stu-id="36979-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="36979-150">按兩下*方案總管*中的 package.appxmanifest.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="36979-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="36979-151">然後流覽至 [*功能*] 區段, 並查看 [*注視] 輸入*功能。</span><span class="sxs-lookup"><span data-stu-id="36979-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![注視輸入功能](images/gaze-input-capability.png)

<span data-ttu-id="36979-153">這會將下列幾行新增至 package.appxmanifest.xml 檔案中的*Package*區段:</span><span class="sxs-lookup"><span data-stu-id="36979-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="36979-154">取得眼睛光線</span><span class="sxs-lookup"><span data-stu-id="36979-154">Getting the eye-gaze ray</span></span>
<span data-ttu-id="36979-155">一旦您收到 ET 的存取權, 就可以自由地抓取每個畫面格的眼睛光線。</span><span class="sxs-lookup"><span data-stu-id="36979-155">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="36979-156">就像使用 head, 使用所需的時間戳記和座標系統呼叫[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)來取得[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 。</span><span class="sxs-lookup"><span data-stu-id="36979-156">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="36979-157">SpatialPointerPose 會透過[眼睛](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)屬性包含[EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)物件。</span><span class="sxs-lookup"><span data-stu-id="36979-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="36979-158">只有在已啟用眼睛追蹤時, 此值才會是 null。</span><span class="sxs-lookup"><span data-stu-id="36979-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="36979-159">從該處, 您可以藉由呼叫[EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)來檢查裝置中的使用者是否具有眼睛追蹤校準。</span><span class="sxs-lookup"><span data-stu-id="36979-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="36979-160">接下來, 使用 [[注視](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)] 屬性來取得[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray)寫入眼的位置和方向。</span><span class="sxs-lookup"><span data-stu-id="36979-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye-gaze position and direction.</span></span> <span data-ttu-id="36979-161">注視屬性有時可以是 null, 因此請務必檢查是否有此情況。</span><span class="sxs-lookup"><span data-stu-id="36979-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="36979-162">如果已校正的使用者暫時關閉其眼睛, 就可能發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="36979-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="36979-163">下列程式碼顯示如何存取眼睛光線。</span><span class="sxs-lookup"><span data-stu-id="36979-163">The following code shows how to access the eye-gaze ray.</span></span>

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
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="36979-164">將注視與其他輸入相互關聯</span><span class="sxs-lookup"><span data-stu-id="36979-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="36979-165">有時候, 您可能會發現需要與過去事件對應的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 。</span><span class="sxs-lookup"><span data-stu-id="36979-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="36979-166">例如, 如果使用者執行空中碰, 您的應用程式可能會想要知道他們所看到的內容。</span><span class="sxs-lookup"><span data-stu-id="36979-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="36979-167">基於此目的, 只要將[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)與預測的框架時間搭配使用, 就會因為系統輸入處理和顯示時間之間的延遲而不正確。</span><span class="sxs-lookup"><span data-stu-id="36979-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="36979-168">此外, 如果針對目標使用眼睛眼, 我們的眼睛通常會在完成認可動作之前繼續進行。</span><span class="sxs-lookup"><span data-stu-id="36979-168">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="36979-169">這不是簡單的點按問題, 但在結合長語音命令與快速的移動時, 會變得更重要。</span><span class="sxs-lookup"><span data-stu-id="36979-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="36979-170">處理這種情況的其中一種方式, 是使用對應于輸入事件的歷程記錄時間戳記, 對[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)進行額外的呼叫。</span><span class="sxs-lookup"><span data-stu-id="36979-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="36979-171">不過, 針對透過 SpatialInteractionManager 進行路由的輸入, 有一個比較簡單的方法。</span><span class="sxs-lookup"><span data-stu-id="36979-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="36979-172">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)有它自己的[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函數。</span><span class="sxs-lookup"><span data-stu-id="36979-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="36979-173">呼叫可提供完美的相互關聯[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) , 而不需要猜測。</span><span class="sxs-lookup"><span data-stu-id="36979-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="36979-174">如需有關使用 SpatialInteractionSourceStates 的詳細資訊, 請參閱 DirectX 檔[中的實習和運動控制器](hands-and-motion-controllers-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="36979-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="36979-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36979-175">See also</span></span>
* [<span data-ttu-id="36979-176">頭部注視和認可輸入模型</span><span class="sxs-lookup"><span data-stu-id="36979-176">Head-gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="36979-177">HoloLens 2 上的眼睛</span><span class="sxs-lookup"><span data-stu-id="36979-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="36979-178">校正</span><span class="sxs-lookup"><span data-stu-id="36979-178">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="36979-179">DirectX 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="36979-179">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="36979-180">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="36979-180">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="36979-181">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="36979-181">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
