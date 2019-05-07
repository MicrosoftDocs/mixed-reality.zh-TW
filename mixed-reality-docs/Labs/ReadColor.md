# <a name="reading-rgb-data"></a>讀取 RGB 資料

**內容**  
[設定裝置](#Configuring-the-Device)  
[取得色彩的框架](#Getting-a-Color-Frame)  
[清除](#Cleaning-Up)  
[完整的來源](#Full-Source)  

**以下是我們將使用的函式：**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a>設定裝置

在後[開啟 k4a 裝置]()，我們需要將相機設定為擷取色彩資料 ！ 很多個選項，因此我們將逐一。 以下是快速範例看起來像是啟動很基本色彩相機。

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

`color_format`可讓我們假設我們要如何讓我們儲存在映像緩衝區中的色彩資訊 ！ `K4A_IMAGE_FORMAT_COLOR_BGRA32` 是 32 位元 / 像素，儲存為 8 位元用於藍色、 綠色、 紅色和 Alpha。 我們在範例中，因為其為了方便起見，使用此格式，但如果您想要的記憶體使用量的 concious，其他格式可能是絕佳的選擇 ！

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|色彩資料會在[影片 JPEG 格式](https://en.wikipedia.org/wiki/Motion_JPEG)|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|[YUV](https://en.wikipedia.org/wiki/YUV)色彩空間 4:2:0 的格式，NV12，僅適用於以 720p 解析度。|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|[YUV](https://en.wikipedia.org/wiki/YUV)色彩空間 4:2:2 的格式，YUY2，僅適用於以 720p 解析度。|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|原始色彩資料，每像素 32 位元順序為藍色、 綠色、 紅色、 Alpha|

寫入時 YUV 轉換可能是簡單、 快速、 健全的程式庫 YUV 轉換，請參閱[libyuv](https://chromium.googlesource.com/libyuv/libyuv/)。

`color_resolution`也有幾個選項 ！

|`color_resolution`|解決方式|長寬|視野| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | 1280 x 720  | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1080P` | 1920 x 1080 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1440P` | 2560 x 1440 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_2160P` | 3840 x 2160 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1536P` | 2048 x 1536 | 4:3  | 90x74.3 
|`K4A_COLOR_RESOLUTION_3072P` | 4096 x 3072 | 4:3  | 90x74.3 | 最大畫面播放速率 15。

當然，`camera_fps`以及。

|camera_fps||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a>取得色彩的框架

取得色彩的框架和深度的畫面格的資料是非常類似的程序 ！ 我們先從該裝置，取得擷取然後我們從其中擷取色彩映像，然後我們提取該映像從未經處理的資料。

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

資料現在儲存在`colorDataBRGA`取決於組態所示的格式。 因為我們要求`K4A_IMAGE_FORMAT_COLOR_BGRA32`，我們有完整 32 位元色彩值儲存在 BGRA 陣列方式 ！

在此情況下，.tga 檔案存放區的色彩 BGR 順序已 ！ 因為我們正在儲存函式，可以略過這些引數的 alpha 色板，我們可以只將映像資料 ！

## <a name="cleaning-up"></a>清除

並如往常，請記住當您完成時釋放您的資源 ！
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a>完整的來源

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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a>下一步 實驗室-[混合色彩和深度的資料](MixDepthAndRGB.md)