# <a name="reading-depth-data"></a><span data-ttu-id="26b72-101">讀取深度資料</span><span class="sxs-lookup"><span data-stu-id="26b72-101">Reading Depth Data</span></span>

<span data-ttu-id="26b72-102">需要從裝置讀取深度資料嗎？</span><span class="sxs-lookup"><span data-stu-id="26b72-102">Need to read depth data from the device?</span></span> <span data-ttu-id="26b72-103">很容易 ！</span><span class="sxs-lookup"><span data-stu-id="26b72-103">It's easy!</span></span>

<span data-ttu-id="26b72-104">**內容**</span><span class="sxs-lookup"><span data-stu-id="26b72-104">**Contents**</span></span>  
[<span data-ttu-id="26b72-105">設定裝置</span><span class="sxs-lookup"><span data-stu-id="26b72-105">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="26b72-106">深度來存取資料</span><span class="sxs-lookup"><span data-stu-id="26b72-106">Acessing Depth Data</span></span>](#Acessing-Depth-Data)  
[<span data-ttu-id="26b72-107">清除</span><span class="sxs-lookup"><span data-stu-id="26b72-107">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="26b72-108">完整的來源</span><span class="sxs-lookup"><span data-stu-id="26b72-108">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="26b72-109">**以下是我們將使用的函式：**</span><span class="sxs-lookup"><span data-stu-id="26b72-109">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a><span data-ttu-id="26b72-110">設定裝置</span><span class="sxs-lookup"><span data-stu-id="26b72-110">Configuring the Device</span></span>

<span data-ttu-id="26b72-111">在後[開啟介面]()Azure Kinect DK 裝置，您必須設定網路攝影機擷取深度的資料。</span><span class="sxs-lookup"><span data-stu-id="26b72-111">After [opening an interface]() to the Azure Kinect DK device, you'll need to configure the camera for capturing depth data.</span></span> <span data-ttu-id="26b72-112">您真的需要知道有關設定深度，只有一個項目也`depth_mode`！</span><span class="sxs-lookup"><span data-stu-id="26b72-112">There's only one item you really need to know about when configuring depth, and that's the `depth_mode`!</span></span>

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="26b72-113">這裡`depth_mode`有幾個選擇 ！</span><span class="sxs-lookup"><span data-stu-id="26b72-113">Here the `depth_mode` has a couple choices!</span></span> <span data-ttu-id="26b72-114">根據我們的應用程式的內容，我們可以要求我們深度的資料格式不同。</span><span class="sxs-lookup"><span data-stu-id="26b72-114">Depending on the context of our application, we can request our depth data in different formats.</span></span>

<span data-ttu-id="26b72-115">是否使用深度資料來執行時間限制演算法？</span><span class="sxs-lookup"><span data-stu-id="26b72-115">Are you running time constrained algorithms on the depth data?</span></span> <span data-ttu-id="26b72-116">或許 pick 2X2BINNED 模式，因此沒有較少的資料上運作 ！</span><span class="sxs-lookup"><span data-stu-id="26b72-116">Maybe pick a 2X2BINNED mode so there's less data to operate on!</span></span> <span data-ttu-id="26b72-117">您在意更多的功能遠直接出前，而不是什麼是關閉對視覺周圍中？</span><span class="sxs-lookup"><span data-stu-id="26b72-117">Do you care more about what's far out directly ahead, rather than what's close and in the periphery?</span></span> <span data-ttu-id="26b72-118">使用窄的視野與 NFOV 模式 ！</span><span class="sxs-lookup"><span data-stu-id="26b72-118">Use a narrow field of view with the NFOV modes!</span></span>
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | <span data-ttu-id="26b72-119">description</span><span class="sxs-lookup"><span data-stu-id="26b72-119">description</span></span> |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|<span data-ttu-id="26b72-120">寬的角度檢視 (120 x 120)，淺層深度 (0.25-2.21 m)、 高資料解析 (1024 x 1024)。</span><span class="sxs-lookup"><span data-stu-id="26b72-120">Wide angle view (120x120), shallow depth (0.25-2.21m), high data resolution (1024x1024).</span></span> <span data-ttu-id="26b72-121">有 15 個最大畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="26b72-121">Has a maximum framerate of 15.</span></span>|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|<span data-ttu-id="26b72-122">寬的角度檢視 (120 x 120)，淺層深度 (0.25-2.88 b m)，資料的低解析度 (512 x 512)。</span><span class="sxs-lookup"><span data-stu-id="26b72-122">Wide angle view (120x120), shallow depth (0.25-2.88m), low data resolution (512x512).</span></span>|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|<span data-ttu-id="26b72-123">半形的角度檢視 (75 x 65)，遠的深度 (0.5-3.86 m)，資料的高解析度 (640 x 576)。</span><span class="sxs-lookup"><span data-stu-id="26b72-123">Narrow angle view (75x65), far depth (0.5-3.86m), high data resolution (640x576).</span></span>|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|<span data-ttu-id="26b72-124">半形的角度檢視 (75 x 65)，遠的深度 (0.5-5.46 m)，資料的低解析度 (320 x 288)。</span><span class="sxs-lookup"><span data-stu-id="26b72-124">Narrow angle view (75x65), far depth (0.5-5.46m), low data resolution (320x288).</span></span>|
|`K4A_DEPTH_MODE_PASSIVE_IR`|<span data-ttu-id="26b72-125">原始 IR 相機 (1024 x 1024) 中的摘要</span><span class="sxs-lookup"><span data-stu-id="26b72-125">Raw feed from the IR camera (1024x1024)</span></span>|
||<span data-ttu-id="26b72-126">深度會提供物件反射率根據指定的範圍之外。</span><span class="sxs-lookup"><span data-stu-id="26b72-126">Depth will be provided outside of indicated range depending on object reflectivity.</span></span>|

## <a name="acessing-depth-data"></a><span data-ttu-id="26b72-127">深度來存取資料</span><span class="sxs-lookup"><span data-stu-id="26b72-127">Acessing Depth Data</span></span>

![](img/Depth.png)

<span data-ttu-id="26b72-128">當我們擷取來自裝置的畫面格時，我們可以使用`k4a_capture_get_depth_image`和`k4a_image_get_buffer`取得未經處理的深度資料 ！</span><span class="sxs-lookup"><span data-stu-id="26b72-128">When we capture a frame from the device, we can use `k4a_capture_get_depth_image` and `k4a_image_get_buffer` to get the raw depth data!</span></span>

```C
// Capture a frame
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the depth data and information from the current capture
k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
int32_t width  = k4a_image_get_width_pixels (depth_image);
int32_t height = k4a_image_get_height_pixels(depth_image);
```

<span data-ttu-id="26b72-129">不帶正負號的 16 位元整數陣列，代表來自相機的公釐為單位提供深入資訊。</span><span class="sxs-lookup"><span data-stu-id="26b72-129">Depth information is provided as an array of unsigned 16 bit integers, representing millimeters from the camera.</span></span> <span data-ttu-id="26b72-130">陣列會保留一個零，如果特定的像素的深度值沒有。</span><span class="sxs-lookup"><span data-stu-id="26b72-130">The array will hold a zero if the depth value isn't present for a particular pixel.</span></span>

<span data-ttu-id="26b72-131">在此範例中，我們將只是深度的資料轉換成灰階映像，並將它儲存到檔案 ！</span><span class="sxs-lookup"><span data-stu-id="26b72-131">In this example, we'll just convert the depth data into a grayscale image, and save it to file!</span></span>

```C
// Write this depth capture to an image file

// Allocate memory for an 8-bit grayscale image
uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

// Convert each depth value to a shade of gray!
for (int32_t i = 0; i < width*height; i++)
{
    // Make a gray from the depth, white up close, black at 3 meters in the distance
    float depth_gray = 1-(depth_buffer[i] / 3000.0f);
    // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
    depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

    file_color[i] = static_cast<uint8_t>(depth_gray * 255);
}
tga_write("outDepth.tga", width, height, file_color, 1, 3);
free(file_color);
```

## <a name="cleaning-up"></a><span data-ttu-id="26b72-132">清除</span><span class="sxs-lookup"><span data-stu-id="26b72-132">Cleaning Up</span></span>

<span data-ttu-id="26b72-133">請務必關閉並釋放已配置或抓取的所有內容 ！</span><span class="sxs-lookup"><span data-stu-id="26b72-133">Remember to shut down and release everything you've allocated or grabbed!</span></span> <span data-ttu-id="26b72-134">請記住完成並之前抓出另一個畫面格之後，應該釋放畫面格擷取。</span><span class="sxs-lookup"><span data-stu-id="26b72-134">Remember that frame captures should be freed after you're finished with them and before grabbing another frame.</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="26b72-135">完整的來源</span><span class="sxs-lookup"><span data-stu-id="26b72-135">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 1024x1024 wide FOV at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_5;
    config.depth_mode = K4A_DEPTH_MODE_WFOV_UNBINNED;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the depth data and information from the current capture
    k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
    uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
    int32_t width  = k4a_image_get_width_pixels (depth_image);
    int32_t height = k4a_image_get_height_pixels(depth_image);
    printf("Captured depth image, %dx%d\n", width, height);

    // Write this depth capture to an image file

    // Allocate memory for an 8-bit grayscale image
    uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

    // Convert each depth value to a shade of gray!
    for (int32_t i = 0; i < width*height; i++)
    {
        // Make a gray from the depth, white up close, black at 3 meters in the distance
        float depth_gray = 1-(depth_buffer[i] / 3000.0f);
        // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
        depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

        file_color[i] = static_cast<uint8_t>(depth_gray * 255);
    }
    tga_write("outDepth.tga", width, height, file_color, 1, 3);
    free(file_color);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(depth_image);
    k4a_capture_release(capture);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width % 256, (uint8_t)(width / 256), height % 256, (uint8_t)(height / 256), file_channels * 8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---reading-rgb-datareadcolormd"></a><span data-ttu-id="26b72-136">下一步 實驗室-[讀取 RGB 資料](ReadColor.md)</span><span class="sxs-lookup"><span data-stu-id="26b72-136">Next Lab - [Reading RGB Data](ReadColor.md)</span></span>