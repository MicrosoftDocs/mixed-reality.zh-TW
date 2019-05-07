# <a name="reading-depth-data"></a>讀取深度資料

需要從裝置讀取深度資料嗎？ 很容易 ！

**內容**  
[設定裝置](#Configuring-the-Device)  
[深度來存取資料](#Acessing-Depth-Data)  
[清除](#Cleaning-Up)  
[完整的來源](#Full-Source)  

**以下是我們將使用的函式：**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a>設定裝置

在後[開啟介面]()Azure Kinect DK 裝置，您必須設定網路攝影機擷取深度的資料。 您真的需要知道有關設定深度，只有一個項目也`depth_mode`！

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

這裡`depth_mode`有幾個選擇 ！ 根據我們的應用程式的內容，我們可以要求我們深度的資料格式不同。

是否使用深度資料來執行時間限制演算法？ 或許 pick 2X2BINNED 模式，因此沒有較少的資料上運作 ！ 您在意更多的功能遠直接出前，而不是什麼是關閉對視覺周圍中？ 使用窄的視野與 NFOV 模式 ！
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | description |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|寬的角度檢視 (120 x 120)，淺層深度 (0.25-2.21 m)、 高資料解析 (1024 x 1024)。 有 15 個最大畫面播放速率。|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|寬的角度檢視 (120 x 120)，淺層深度 (0.25-2.88 b m)，資料的低解析度 (512 x 512)。|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|半形的角度檢視 (75 x 65)，遠的深度 (0.5-3.86 m)，資料的高解析度 (640 x 576)。|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|半形的角度檢視 (75 x 65)，遠的深度 (0.5-5.46 m)，資料的低解析度 (320 x 288)。|
|`K4A_DEPTH_MODE_PASSIVE_IR`|原始 IR 相機 (1024 x 1024) 中的摘要|
||深度會提供物件反射率根據指定的範圍之外。|

## <a name="acessing-depth-data"></a>深度來存取資料

![](img/Depth.png)

當我們擷取來自裝置的畫面格時，我們可以使用`k4a_capture_get_depth_image`和`k4a_image_get_buffer`取得未經處理的深度資料 ！

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

不帶正負號的 16 位元整數陣列，代表來自相機的公釐為單位提供深入資訊。 陣列會保留一個零，如果特定的像素的深度值沒有。

在此範例中，我們將只是深度的資料轉換成灰階映像，並將它儲存到檔案 ！

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

## <a name="cleaning-up"></a>清除

請務必關閉並釋放已配置或抓取的所有內容 ！ 請記住完成並之前抓出另一個畫面格之後，應該釋放畫面格擷取。

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a>完整的來源

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

## <a name="next-lab---reading-rgb-datareadcolormd"></a>下一步 實驗室-[讀取 RGB 資料](ReadColor.md)