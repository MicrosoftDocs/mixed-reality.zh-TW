# <a name="accessing-the-imu"></a><span data-ttu-id="09fdc-101">存取 IMU</span><span class="sxs-lookup"><span data-stu-id="09fdc-101">Accessing the IMU</span></span>

<span data-ttu-id="09fdc-102">Azure 的 Kinect DK 包含慣性的度量單位 (IMU) ！</span><span class="sxs-lookup"><span data-stu-id="09fdc-102">Azure Kinect DK contains an Inertial Measurement Unit (IMU)!</span></span> <span data-ttu-id="09fdc-103">這可用來協助判斷動作和裝置的擷取期間的方向。</span><span class="sxs-lookup"><span data-stu-id="09fdc-103">This can be useful for helping to determine motion and orientation of the device during capture.</span></span> <span data-ttu-id="09fdc-104">特別是如果您的裝置不是靜態的 ！</span><span class="sxs-lookup"><span data-stu-id="09fdc-104">Especially if you device isn't stationary!</span></span>

<span data-ttu-id="09fdc-105">**內容：**</span><span class="sxs-lookup"><span data-stu-id="09fdc-105">**Contents:**</span></span>  
[<span data-ttu-id="09fdc-106">組態和設定</span><span class="sxs-lookup"><span data-stu-id="09fdc-106">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="09fdc-107">取得資料</span><span class="sxs-lookup"><span data-stu-id="09fdc-107">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="09fdc-108">清除</span><span class="sxs-lookup"><span data-stu-id="09fdc-108">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="09fdc-109">完整的來源</span><span class="sxs-lookup"><span data-stu-id="09fdc-109">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="09fdc-110">**以下是我們將使用的函式：**</span><span class="sxs-lookup"><span data-stu-id="09fdc-110">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-imu)  
[`k4a_device_stop_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-imu)  
[`k4a_device_get_imu_sample()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-imu-sample)  

## <a name="configuration-and-setup"></a><span data-ttu-id="09fdc-111">組態和設定</span><span class="sxs-lookup"><span data-stu-id="09fdc-111">Configuration and Setup</span></span>

<span data-ttu-id="09fdc-112">在此組態是很簡單 ！</span><span class="sxs-lookup"><span data-stu-id="09fdc-112">Configuration here is pretty simple!</span></span> <span data-ttu-id="09fdc-113">您必須指定沒有項目 IMU 的裝置組態中取樣可以運作，但您必須呼叫`k4a_device_start_cameras`應可成功之前 ！</span><span class="sxs-lookup"><span data-stu-id="09fdc-113">There are no items you need to specify the in the device configuration for IMU sampling to work, but you will need to call `k4a_device_start_cameras` before it'll work!</span></span> <span data-ttu-id="09fdc-114">相反地，您將會呼叫`k4a_device_start_imu`之後啟動相機。</span><span class="sxs-lookup"><span data-stu-id="09fdc-114">Instead, you'll make a call to `k4a_device_start_imu` after starting the cameras.</span></span>

```C
// Cameras need to be 'started' even if all we want is the IMU
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
k4a_device_start_cameras(device, &config);

// Start up the IMU sensors
k4a_device_start_imu(device);
```

## <a name="getting-data"></a><span data-ttu-id="09fdc-115">取得資料</span><span class="sxs-lookup"><span data-stu-id="09fdc-115">Getting Data</span></span>

<span data-ttu-id="09fdc-116">![IMU 範例應用程式映像](img/IMU.png "以下是我們將建置做為範例 ！")</span><span class="sxs-lookup"><span data-stu-id="09fdc-116">![IMU sample app image](img/IMU.png "Here's what we'll build as an example!")</span></span>

<span data-ttu-id="09fdc-117">IMU 提供 1.6 kHz 的速度的資料 ！</span><span class="sxs-lookup"><span data-stu-id="09fdc-117">The IMU provides data at a rate of 1.6kHz!</span></span> <span data-ttu-id="09fdc-118">大量資料，而且這表示，如果您只想要在每個色彩深度/框架有可用的時間，您可能會有相當的佇列，等候您 IMU 範例 ！</span><span class="sxs-lookup"><span data-stu-id="09fdc-118">That's a lot of data, and this means that if you're only looking at it each time a depth/color frame is available, you'll likely have quite a queue of IMU samples waiting for you!</span></span> <span data-ttu-id="09fdc-119">請注意，這項資料不是方向或位置，但相反地，強制目前套用至裝置的量值。</span><span class="sxs-lookup"><span data-stu-id="09fdc-119">Note that this data is not an orientation or position, but rather, a measure of the force currently applied to the device.</span></span>

<span data-ttu-id="09fdc-120">我們可以抓取的範例，並從佇列移除藉由呼叫`k4a_device_get_imu_sample`逾時值為 0 毫秒。</span><span class="sxs-lookup"><span data-stu-id="09fdc-120">We can grab a sample and remove it from the queue by calling `k4a_device_get_imu_sample` with a timeout of 0 milliseconds.</span></span> <span data-ttu-id="09fdc-121">它會傳回`K4A_WAIT_RESULT_SUCCEEDED`，只要它有可用的範例 ！</span><span class="sxs-lookup"><span data-stu-id="09fdc-121">It'll return `K4A_WAIT_RESULT_SUCCEEDED` as long as it has a sample available!</span></span>

<span data-ttu-id="09fdc-122">以下是加總目前在佇列中，所有範例和列印平均的範例。</span><span class="sxs-lookup"><span data-stu-id="09fdc-122">Here's an example of summing all the samples currently in the queue, and printing the average.</span></span> 

```C
k4a_float3_t gyro_sum  = {0};
k4a_float3_t acc_sum   = {0};
int32_t      sum_count = 0;

// Sum the current queue of IMU samples
k4a_imu_sample_t sample;
while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
{
    gyro_sum.xyz = { 
        gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
        gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
        gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
    acc_sum.xyz = { 
        acc_sum.xyz.x + sample.acc_sample.xyz.x,  
        acc_sum.xyz.y + sample.acc_sample.xyz.y,  
        acc_sum.xyz.z + sample.acc_sample.xyz.z };
    sum_count += 1;
    samples   += 1;
}

// If we got any samples, print out their average!
if (sum_count > 0)
{
    k4a_float3_t gyro_avg = {
        gyro_sum.xyz.x / sum_count,
        gyro_sum.xyz.y / sum_count,
        gyro_sum.xyz.z / sum_count };
    k4a_float3_t acc_avg = {
        acc_sum.xyz.x / sum_count,
        acc_sum.xyz.y / sum_count,
        acc_sum.xyz.z / sum_count };

    printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
    printf("<%6.2f, %6.2f, %6.2f>", acc_avg.xyz.x, acc_avg.xyz.y, acc_avg.xyz.z);

    // Write backspaces so we'll overwrite this line next time
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
}
```

## <a name="cleaning-up"></a><span data-ttu-id="09fdc-123">清除</span><span class="sxs-lookup"><span data-stu-id="09fdc-123">Cleaning Up</span></span>

<span data-ttu-id="09fdc-124">並如往常，發行的所有項目完成時:)</span><span class="sxs-lookup"><span data-stu-id="09fdc-124">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_device_stop_imu(device);
k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="09fdc-125">完整的來源</span><span class="sxs-lookup"><span data-stu-id="09fdc-125">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Cameras need to be 'started' even if all we want is the IMU
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    k4a_device_start_cameras(device, &config);

    // Start up the IMU sensors
    k4a_device_start_imu(device);

    // Display 10,000 samples as fast as they arrive
    printf("Sampling 10,000 times.\n");
    printf("Gyroscope radians/s:       Accelerometer meters/s^2:\n");
    int32_t samples = 0;
    while (samples < 10000)
    {
        k4a_float3_t gyro_sum  = {0};
        k4a_float3_t accel_sum = {0};
        int32_t      sum_count = 0;

        // Sum the current queue of IMU samples
        k4a_imu_sample_t sample;
        while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
        {
            gyro_sum.xyz = { 
                gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
                gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
                gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
            accel_sum.xyz = { 
                accel_sum.xyz.x + sample.acc_sample.xyz.x,  
                accel_sum.xyz.y + sample.acc_sample.xyz.y,  
                accel_sum.xyz.z + sample.acc_sample.xyz.z };
            sum_count += 1;
            samples   += 1;
        }

        // If we got any samples this loop, print out their average!
        if (sum_count > 0)
        {
            k4a_float3_t gyro_avg = {
                gyro_sum.xyz.x / sum_count,
                gyro_sum.xyz.y / sum_count,
                gyro_sum.xyz.z / sum_count };
            k4a_float3_t accel_avg = {
                accel_sum.xyz.x / sum_count,
                accel_sum.xyz.y / sum_count,
                accel_sum.xyz.z / sum_count };

            printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
            printf("<%6.2f, %6.2f, %6.2f>", accel_avg.xyz.x, accel_avg.xyz.y, accel_avg.xyz.z);

            // Write backspaces so we'll overwrite this line next time
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
        }
    }
    printf("\nShutting down.\n");

    // Release all allocated resources, and shut down the Kinect
    k4a_device_stop_imu(device);
    k4a_device_stop_cameras(device);
    k4a_device_close(device);
}
```