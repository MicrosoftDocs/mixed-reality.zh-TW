# <a name="reading-rgb-data"></a><span data-ttu-id="f2a35-101">讀取 RGB 資料</span><span class="sxs-lookup"><span data-stu-id="f2a35-101">Reading RGB Data</span></span>

<span data-ttu-id="f2a35-102">**內容**</span><span class="sxs-lookup"><span data-stu-id="f2a35-102">**Contents**</span></span>  
[<span data-ttu-id="f2a35-103">設定裝置</span><span class="sxs-lookup"><span data-stu-id="f2a35-103">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="f2a35-104">取得色彩的框架</span><span class="sxs-lookup"><span data-stu-id="f2a35-104">Getting a Color Frame</span></span>](#Getting-a-Color-Frame)  
[<span data-ttu-id="f2a35-105">清除</span><span class="sxs-lookup"><span data-stu-id="f2a35-105">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="f2a35-106">完整的來源</span><span class="sxs-lookup"><span data-stu-id="f2a35-106">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="f2a35-107">**以下是我們將使用的函式：**</span><span class="sxs-lookup"><span data-stu-id="f2a35-107">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a><span data-ttu-id="f2a35-108">設定裝置</span><span class="sxs-lookup"><span data-stu-id="f2a35-108">Configuring the Device</span></span>

<span data-ttu-id="f2a35-109">在後[開啟 k4a 裝置]()，我們需要將相機設定為擷取色彩資料 ！</span><span class="sxs-lookup"><span data-stu-id="f2a35-109">After [opening a k4a device](), we'll need to set up the cameras to grab color data!</span></span> <span data-ttu-id="f2a35-110">很多個選項，因此我們將逐一。</span><span class="sxs-lookup"><span data-stu-id="f2a35-110">There's a lot of options here as well, so we'll go through them.</span></span> <span data-ttu-id="f2a35-111">以下是快速範例看起來像是啟動很基本色彩相機。</span><span class="sxs-lookup"><span data-stu-id="f2a35-111">Here's a quick example of what it looks like to start up a really basic color camera.</span></span>

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="f2a35-112">`color_format`可讓我們假設我們要如何讓我們儲存在映像緩衝區中的色彩資訊 ！</span><span class="sxs-lookup"><span data-stu-id="f2a35-112">The `color_format` allows us to say how we want our color information stored in the image buffer!</span></span> <span data-ttu-id="f2a35-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` 是 32 位元 / 像素，儲存為 8 位元用於藍色、 綠色、 紅色和 Alpha。</span><span class="sxs-lookup"><span data-stu-id="f2a35-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` would be 32 bits per pixel, stored as 8 bits each for Blue, Green, Red, and Alpha.</span></span> <span data-ttu-id="f2a35-114">我們在範例中，因為其為了方便起見，使用此格式，但如果您想要的記憶體使用量的 concious，其他格式可能是絕佳的選擇 ！</span><span class="sxs-lookup"><span data-stu-id="f2a35-114">We use this format in the examples due to its convenience, but if you want to be concious of memory usage, other formats may be superior choices!</span></span>

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|<span data-ttu-id="f2a35-115">色彩資料會在[影片 JPEG 格式](https://en.wikipedia.org/wiki/Motion_JPEG)</span><span class="sxs-lookup"><span data-stu-id="f2a35-115">Color data will be in [Motion JPEG format](https://en.wikipedia.org/wiki/Motion_JPEG)</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|<span data-ttu-id="f2a35-116">[YUV](https://en.wikipedia.org/wiki/YUV)色彩空間 4:2:0 的格式，NV12，僅適用於以 720p 解析度。</span><span class="sxs-lookup"><span data-stu-id="f2a35-116">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:0 format, NV12, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|<span data-ttu-id="f2a35-117">[YUV](https://en.wikipedia.org/wiki/YUV)色彩空間 4:2:2 的格式，YUY2，僅適用於以 720p 解析度。</span><span class="sxs-lookup"><span data-stu-id="f2a35-117">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:2 format, YUY2, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|<span data-ttu-id="f2a35-118">原始色彩資料，每像素 32 位元順序為藍色、 綠色、 紅色、 Alpha</span><span class="sxs-lookup"><span data-stu-id="f2a35-118">Raw color data, 32 bits per pixel, ordered as Blue, Green, Red, Alpha</span></span>|

<span data-ttu-id="f2a35-119">寫入時 YUV 轉換可能是簡單、 快速、 健全的程式庫 YUV 轉換，請參閱[libyuv](https://chromium.googlesource.com/libyuv/libyuv/)。</span><span class="sxs-lookup"><span data-stu-id="f2a35-119">While writing your own YUV conversion may be easy enough, a fast, robust library for YUV conversion can be found at [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span></span>

<span data-ttu-id="f2a35-120">`color_resolution`也有幾個選項 ！</span><span class="sxs-lookup"><span data-stu-id="f2a35-120">The `color_resolution` also has a couple of options!</span></span>

|`color_resolution`|<span data-ttu-id="f2a35-121">解決方式</span><span class="sxs-lookup"><span data-stu-id="f2a35-121">resolution</span></span>|<span data-ttu-id="f2a35-122">長寬</span><span class="sxs-lookup"><span data-stu-id="f2a35-122">aspect</span></span>|<span data-ttu-id="f2a35-123">視野</span><span class="sxs-lookup"><span data-stu-id="f2a35-123">field of view</span></span>| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | <span data-ttu-id="f2a35-124">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="f2a35-124">1280 x 720</span></span>  | <span data-ttu-id="f2a35-125">16:9</span><span class="sxs-lookup"><span data-stu-id="f2a35-125">16:9</span></span> | <span data-ttu-id="f2a35-126">90x59</span><span class="sxs-lookup"><span data-stu-id="f2a35-126">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1080P` | <span data-ttu-id="f2a35-127">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="f2a35-127">1920 x 1080</span></span> | <span data-ttu-id="f2a35-128">16:9</span><span class="sxs-lookup"><span data-stu-id="f2a35-128">16:9</span></span> | <span data-ttu-id="f2a35-129">90x59</span><span class="sxs-lookup"><span data-stu-id="f2a35-129">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1440P` | <span data-ttu-id="f2a35-130">2560 x 1440</span><span class="sxs-lookup"><span data-stu-id="f2a35-130">2560 x 1440</span></span> | <span data-ttu-id="f2a35-131">16:9</span><span class="sxs-lookup"><span data-stu-id="f2a35-131">16:9</span></span> | <span data-ttu-id="f2a35-132">90x59</span><span class="sxs-lookup"><span data-stu-id="f2a35-132">90x59</span></span>
|`K4A_COLOR_RESOLUTION_2160P` | <span data-ttu-id="f2a35-133">3840 x 2160</span><span class="sxs-lookup"><span data-stu-id="f2a35-133">3840 x 2160</span></span> | <span data-ttu-id="f2a35-134">16:9</span><span class="sxs-lookup"><span data-stu-id="f2a35-134">16:9</span></span> | <span data-ttu-id="f2a35-135">90x59</span><span class="sxs-lookup"><span data-stu-id="f2a35-135">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1536P` | <span data-ttu-id="f2a35-136">2048 x 1536</span><span class="sxs-lookup"><span data-stu-id="f2a35-136">2048 x 1536</span></span> | <span data-ttu-id="f2a35-137">4:3</span><span class="sxs-lookup"><span data-stu-id="f2a35-137">4:3</span></span>  | <span data-ttu-id="f2a35-138">90x74.3</span><span class="sxs-lookup"><span data-stu-id="f2a35-138">90x74.3</span></span> 
|`K4A_COLOR_RESOLUTION_3072P` | <span data-ttu-id="f2a35-139">4096 x 3072</span><span class="sxs-lookup"><span data-stu-id="f2a35-139">4096 x 3072</span></span> | <span data-ttu-id="f2a35-140">4:3</span><span class="sxs-lookup"><span data-stu-id="f2a35-140">4:3</span></span>  | <span data-ttu-id="f2a35-141">90x74.3</span><span class="sxs-lookup"><span data-stu-id="f2a35-141">90x74.3</span></span> | <span data-ttu-id="f2a35-142">最大畫面播放速率 15。</span><span class="sxs-lookup"><span data-stu-id="f2a35-142">Max framerate 15.</span></span>

<span data-ttu-id="f2a35-143">當然，`camera_fps`以及。</span><span class="sxs-lookup"><span data-stu-id="f2a35-143">And of course, the `camera_fps` as well.</span></span>

|<span data-ttu-id="f2a35-144">camera_fps</span><span class="sxs-lookup"><span data-stu-id="f2a35-144">camera_fps</span></span>||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a><span data-ttu-id="f2a35-145">取得色彩的框架</span><span class="sxs-lookup"><span data-stu-id="f2a35-145">Getting a Color Frame</span></span>

<span data-ttu-id="f2a35-146">取得色彩的框架和深度的畫面格的資料是非常類似的程序 ！</span><span class="sxs-lookup"><span data-stu-id="f2a35-146">Getting data for a color frame and a depth frame is a very similar process!</span></span> <span data-ttu-id="f2a35-147">我們先從該裝置，取得擷取然後我們從其中擷取色彩映像，然後我們提取該映像從未經處理的資料。</span><span class="sxs-lookup"><span data-stu-id="f2a35-147">First we get a capture from the device, then we extract the color image from it, and then we pull the raw data out of that image.</span></span>

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the color data and information from the current capture
k4a_image_t colors      = k4a_capture_get_color_image(capture);
uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
int width  = k4a_image_get_width_pixels (colors);
int height = k4a_image_get_height_pixels(colors);

// Write this capture to file
tga_write("out.tga", width, height, colorDataBGRA, 4, 3);
```

<span data-ttu-id="f2a35-148">資料現在儲存在`colorDataBRGA`取決於組態所示的格式。</span><span class="sxs-lookup"><span data-stu-id="f2a35-148">The data now stored in `colorDataBRGA` is dependant on the format we indicated in configuration.</span></span> <span data-ttu-id="f2a35-149">因為我們要求`K4A_IMAGE_FORMAT_COLOR_BGRA32`，我們有完整 32 位元色彩值儲存在 BGRA 陣列方式 ！</span><span class="sxs-lookup"><span data-stu-id="f2a35-149">Since we asked for `K4A_IMAGE_FORMAT_COLOR_BGRA32`, we have an array full of 32 bit color values stored in BGRA order!</span></span>

<span data-ttu-id="f2a35-150">在此情況下，.tga 檔案存放區的色彩 BGR 順序已 ！</span><span class="sxs-lookup"><span data-stu-id="f2a35-150">In this case, .tga files store colors in BGR order already!</span></span> <span data-ttu-id="f2a35-151">因為我們正在儲存函式，可以略過這些引數的 alpha 色板，我們可以只將映像資料 ！</span><span class="sxs-lookup"><span data-stu-id="f2a35-151">And since our saving function can skip the alpha channel with these arguments, we can just pass the image data as is!</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="f2a35-152">清除</span><span class="sxs-lookup"><span data-stu-id="f2a35-152">Cleaning Up</span></span>

<span data-ttu-id="f2a35-153">並如往常，請記住當您完成時釋放您的資源 ！</span><span class="sxs-lookup"><span data-stu-id="f2a35-153">And as always, remember to release your resources when you're done with them!</span></span>
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a><span data-ttu-id="f2a35-154">完整的來源</span><span class="sxs-lookup"><span data-stu-id="f2a35-154">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main() {
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure a stream of 1280x720 BRGA data at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the color data and information from the current capture
    k4a_image_t colors      = k4a_capture_get_color_image(capture);
    uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
    int width  = k4a_image_get_width_pixels (colors);
    int height = k4a_image_get_height_pixels(colors);
    printf("Captured RGB image, %dx%d\n", width, height);

    // Write this capture to file
    tga_write("out.tga", width, height, colors_bgra, 4, 3);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(colors);
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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a><span data-ttu-id="f2a35-155">下一步 實驗室-[混合色彩和深度的資料](MixDepthAndRGB.md)</span><span class="sxs-lookup"><span data-stu-id="f2a35-155">Next Lab - [Mixing Color and Depth Data](MixDepthAndRGB.md)</span></span>