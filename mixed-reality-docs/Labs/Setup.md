# <a name="setting-up"></a>設定

開始使用 Azure Kinect DK API 嗎？ 這裡就對了 ！ 這份文件可以讓您啟動並執行具有存取權進入裝置 ！

首先，下載並安裝[Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK)從 Github。

**內容**  
[標頭](#Headers)  
[尋找 Kinect 裝置](#Finding-a-Kinect-Device)  
[啟動相機](#Starting-the-Cameras)  
[錯誤處理](#Error-Handling)  
[完整的來源](#Full-Source)  

**以下是我們將使用的函式：**  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a>標頭
沒有您所需要的只有一個標頭，這是 k4a.h ！ 請確定您選擇的編譯器設定的 SDK 程式庫，並包含的資料夾。 您也需要 k4a.lib 和 k4a.dll 檔案連結。
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a>尋找 Kinect 裝置

![](img/Serial.png)

多個 Azure Kinect DK 裝置可以連線到您的電腦 ！ 我們第一次一開始先尋找出多少，或任何連線完全使用[ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)函式。 此函式應該不必進行任何額外的設定，能用 ！

```C
uint32_t count = k4a_device_get_installed_count();
```

一旦您那里判定實際的裝置連接到電腦，您可以開啟使用它[ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)。 您可以提供索引的裝置，您想要開啟此項目，或您可以使用[ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT)針對第一個。

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
為與大多在 k4a API 中，當您開啟什麼項目，您也應該關閉它與它完成時 ！ 您正在關閉時，務必呼叫[ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)。

```C
k4a_device_close(device);
```

裝置開啟後，我們可以非常簡單的測試，以確保就行了。 現在讓我們來讀取裝置的序號 ！

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

## <a name="starting-the-cameras"></a>啟動相機

一旦您開啟裝置，您將需要設定攝影機[ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t)物件 ！ 相機設定有許多不同的選項，您必須選擇最適合自己案例的設定。

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

如需組態詳細資料__色彩__相機[查看這份文件]()！  
如需組態詳細資料__深度__相機[查看這份文件]()！

## <a name="error-handling"></a>錯誤處理

為了保持簡潔和避免困擾，我們不會顯示一些內嵌範例中的錯誤處理。 不過，錯誤處理很重要 ！ 許多函式會傳回一般的成功/失敗類型[ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t)，或具有更特定變數的詳細資訊這類[ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t)。 請務必檢查 docs 或特定的函式的 intellisense 以查看哪些錯誤訊息，您可能會看到從它 ！

以及錯誤類型，另外還有[ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED)並[ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED)巨集，您可以使用它們。 因此而不是只開啟 k4a 裝置，我們可能會保護它像這樣：

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a>完整的來源

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

## <a name="next-lab---reading-depth-datareaddepthmd"></a>下一步 實驗室-[讀取深度資料](ReadDepth.md)
