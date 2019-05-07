# <a name="setting-up"></a><span data-ttu-id="a14bc-101">設定</span><span class="sxs-lookup"><span data-stu-id="a14bc-101">Setting Up</span></span>

<span data-ttu-id="a14bc-102">開始使用 Azure Kinect DK API 嗎？</span><span class="sxs-lookup"><span data-stu-id="a14bc-102">Getting started with the Azure Kinect DK API?</span></span> <span data-ttu-id="a14bc-103">這裡就對了 ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-103">Look no further!</span></span> <span data-ttu-id="a14bc-104">這份文件可以讓您啟動並執行具有存取權進入裝置 ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-104">This document will get you up and running with access to the device!</span></span>

<span data-ttu-id="a14bc-105">首先，下載並安裝[Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK)從 Github。</span><span class="sxs-lookup"><span data-stu-id="a14bc-105">First, download and install the [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) from Github.</span></span>

<span data-ttu-id="a14bc-106">**內容**</span><span class="sxs-lookup"><span data-stu-id="a14bc-106">**Contents**</span></span>  
[<span data-ttu-id="a14bc-107">標頭</span><span class="sxs-lookup"><span data-stu-id="a14bc-107">Headers</span></span>](#Headers)  
[<span data-ttu-id="a14bc-108">尋找 Kinect 裝置</span><span class="sxs-lookup"><span data-stu-id="a14bc-108">Finding a Kinect Device</span></span>](#Finding-a-Kinect-Device)  
[<span data-ttu-id="a14bc-109">啟動相機</span><span class="sxs-lookup"><span data-stu-id="a14bc-109">Starting the Cameras</span></span>](#Starting-the-Cameras)  
[<span data-ttu-id="a14bc-110">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="a14bc-110">Error Handling</span></span>](#Error-Handling)  
[<span data-ttu-id="a14bc-111">完整的來源</span><span class="sxs-lookup"><span data-stu-id="a14bc-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="a14bc-112">**以下是我們將使用的函式：**</span><span class="sxs-lookup"><span data-stu-id="a14bc-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a><span data-ttu-id="a14bc-113">標頭</span><span class="sxs-lookup"><span data-stu-id="a14bc-113">Headers</span></span>
<span data-ttu-id="a14bc-114">沒有您所需要的只有一個標頭，這是 k4a.h ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-114">There's only one header that you'll need, and that's k4a.h!</span></span> <span data-ttu-id="a14bc-115">請確定您選擇的編譯器設定的 SDK 程式庫，並包含的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a14bc-115">Make sure your compiler of choice is set up with the SDK's lib and include folders.</span></span> <span data-ttu-id="a14bc-116">您也需要 k4a.lib 和 k4a.dll 檔案連結。</span><span class="sxs-lookup"><span data-stu-id="a14bc-116">You'll also need the k4a.lib and k4a.dll files linked up.</span></span>
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a><span data-ttu-id="a14bc-117">尋找 Kinect 裝置</span><span class="sxs-lookup"><span data-stu-id="a14bc-117">Finding a Kinect Device</span></span>

![](img/Serial.png)

<span data-ttu-id="a14bc-118">多個 Azure Kinect DK 裝置可以連線到您的電腦 ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-118">Multiple Azure Kinect DK devices can be connected to your computer!</span></span> <span data-ttu-id="a14bc-119">我們第一次一開始先尋找出多少，或任何連線完全使用[ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)函式。</span><span class="sxs-lookup"><span data-stu-id="a14bc-119">We'll first start by finding out how many, or if any are connected at all using the [`k4a_device_get_installed_count`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) function.</span></span> <span data-ttu-id="a14bc-120">此函式應該不必進行任何額外的設定，能用 ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-120">This function should work right away, without any additional setup!</span></span>

```C
uint32_t count = k4a_device_get_installed_count();
```

<span data-ttu-id="a14bc-121">一旦您那里判定實際的裝置連接到電腦，您可以開啟使用它[ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)。</span><span class="sxs-lookup"><span data-stu-id="a14bc-121">Once you've determined there is actually a device connected to the computer, you can open it using [`k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span></span> <span data-ttu-id="a14bc-122">您可以提供索引的裝置，您想要開啟此項目，或您可以使用[ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT)針對第一個。</span><span class="sxs-lookup"><span data-stu-id="a14bc-122">You can provide the index of the device you want to open, or you can just use [`K4A_DEVICE_DEFAULT`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) for the first one.</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
<span data-ttu-id="a14bc-123">為與大多在 k4a API 中，當您開啟什麼項目，您也應該關閉它與它完成時 ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-123">As with most things in the k4a API, when you open something, you should also close it when you're finished with it!</span></span> <span data-ttu-id="a14bc-124">您正在關閉時，務必呼叫[ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)。</span><span class="sxs-lookup"><span data-stu-id="a14bc-124">When you're shutting down, remember to make a call to [`k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span></span>

```C
k4a_device_close(device);
```

<span data-ttu-id="a14bc-125">裝置開啟後，我們可以非常簡單的測試，以確保就行了。</span><span class="sxs-lookup"><span data-stu-id="a14bc-125">Once the device is open, we can make a really simple test to ensure it's all good.</span></span> <span data-ttu-id="a14bc-126">現在讓我們來讀取裝置的序號 ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-126">So let's read the device's serial number!</span></span>

```C
// Get the size of the serial number
size_t serial_size = 0;
k4a_device_get_serialnum(device, NULL, &serial_size);

// Allocate memory for the serial, then acquire it
char *serial = static_cast<char*>(malloc(serial_size));
k4a_device_get_serialnum(device, serial, &serial_size);
printf("Opened device: %s\n", serial);
free(serial);
```

## <a name="starting-the-cameras"></a><span data-ttu-id="a14bc-127">啟動相機</span><span class="sxs-lookup"><span data-stu-id="a14bc-127">Starting the Cameras</span></span>

<span data-ttu-id="a14bc-128">一旦您開啟裝置，您將需要設定攝影機[ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t)物件 ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-128">Once you've opened the device, you'll need to configure the camera with a [`k4a_device_configuration_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) object!</span></span> <span data-ttu-id="a14bc-129">相機設定有許多不同的選項，您必須選擇最適合自己案例的設定。</span><span class="sxs-lookup"><span data-stu-id="a14bc-129">Camera configuration has a number of different options, and you'll need to choose the settings that best fit your own scenario.</span></span>

```C
// Configure a stream of 4096x3072 BRGA color data at 15 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_15;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

// Start the camera with the given configuration
k4a_device_start_cameras(device, &config)

// ...Camera capture and application specific code would go here...

// Shut down the camera when finished with application logic
k4a_device_stop_cameras(device);
```

<span data-ttu-id="a14bc-130">如需組態詳細資料__色彩__相機[查看這份文件]()！</span><span class="sxs-lookup"><span data-stu-id="a14bc-130">For configuration details about the __color__ camera, [check out this document]()!</span></span>  
<span data-ttu-id="a14bc-131">如需組態詳細資料__深度__相機[查看這份文件]()！</span><span class="sxs-lookup"><span data-stu-id="a14bc-131">For configuration details about the __depth__ camera, [check out this document]()!</span></span>

## <a name="error-handling"></a><span data-ttu-id="a14bc-132">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="a14bc-132">Error Handling</span></span>

<span data-ttu-id="a14bc-133">為了保持簡潔和避免困擾，我們不會顯示一些內嵌範例中的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="a14bc-133">For the sake of brevity and clarity, we don't show error handling in some inline examples.</span></span> <span data-ttu-id="a14bc-134">不過，錯誤處理很重要 ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-134">However, error handling is always important!</span></span> <span data-ttu-id="a14bc-135">許多函式會傳回一般的成功/失敗類型[ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t)，或具有更特定變數的詳細資訊這類[ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t)。</span><span class="sxs-lookup"><span data-stu-id="a14bc-135">Many functions will return a general success/failure type [`k4a_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), or a more specific variant with detailed information such as [`k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span></span> <span data-ttu-id="a14bc-136">請務必檢查 docs 或特定的函式的 intellisense 以查看哪些錯誤訊息，您可能會看到從它 ！</span><span class="sxs-lookup"><span data-stu-id="a14bc-136">Be sure to check the docs or intellisense of a specific function to see what error messages you might expect to see from it!</span></span>

<span data-ttu-id="a14bc-137">以及錯誤類型，另外還有[ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED)並[ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED)巨集，您可以使用它們。</span><span class="sxs-lookup"><span data-stu-id="a14bc-137">Along with the error types, there's also the [`K4A_SUCCEEDED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) and [`K4A_FAILED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros that you can use with them.</span></span> <span data-ttu-id="a14bc-138">因此而不是只開啟 k4a 裝置，我們可能會保護它像這樣：</span><span class="sxs-lookup"><span data-stu-id="a14bc-138">So instead of just opening a k4a device, we might guard it like this:</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a><span data-ttu-id="a14bc-139">完整的來源</span><span class="sxs-lookup"><span data-stu-id="a14bc-139">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

int main()
{
    uint32_t count = k4a_device_get_installed_count();
    if (count == 0)
    {
        printf("No k4a devices attached!\n");
        return 0;
    }

    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    if (K4A_FAILED(k4a_device_open(K4A_DEVICE_DEFAULT, &device)))
    {
        printf("Failed to open k4a device!\n");
        return 0;
    }

    // Get the size of the serial number
    size_t serial_size = 0;
    k4a_device_get_serialnum(device, NULL, &serial_size);

    // Allocate memory for the serial, then acquire it
    char* serial = static_cast<char*>(malloc(serial_size));
    k4a_device_get_serialnum(device, serial, &serial_size);
    printf("Opened device: %s\n", serial);
    free(serial);

    // Configure a stream of 4096x3072 BRGA color data at 15 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_15;
    config.color_format = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

    // Start the camera with the given configuration
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
    {
        printf("Failed to start cameras!\n");
        k4a_device_close(device);
        return 0;
    }

    // ...Camera capture and application specific code would go here...

    // Shut down the camera when finished with application logic
    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}
```

## <a name="next-lab---reading-depth-datareaddepthmd"></a><span data-ttu-id="a14bc-140">下一步 實驗室-[讀取深度資料](ReadDepth.md)</span><span class="sxs-lookup"><span data-stu-id="a14bc-140">Next Lab - [Reading Depth Data](ReadDepth.md)</span></span>
