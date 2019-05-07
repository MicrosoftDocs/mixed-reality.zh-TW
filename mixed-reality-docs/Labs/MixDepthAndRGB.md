# <a name="mixing-color-and-depth-data"></a><span data-ttu-id="ea6b3-101">混合色彩和深度的資料</span><span class="sxs-lookup"><span data-stu-id="ea6b3-101">Mixing Color and Depth Data</span></span>

<span data-ttu-id="ea6b3-102">您從色彩相機和深度相機取得的資源會有不同的形狀和大小 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-102">The resources you get from the color camera and the depth camera have different shapes and sizes!</span></span> <span data-ttu-id="ea6b3-103">如果您想要結合兩個，則有許多種您可以如何彼此對齊。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-103">If you want to combine the two, there's a number of things you can do to align them to each other.</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="ea6b3-104">**內容：**</span><span class="sxs-lookup"><span data-stu-id="ea6b3-104">**Contents:**</span></span>  
[<span data-ttu-id="ea6b3-105">組態和設定</span><span class="sxs-lookup"><span data-stu-id="ea6b3-105">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="ea6b3-106">取得資料</span><span class="sxs-lookup"><span data-stu-id="ea6b3-106">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="ea6b3-107">轉換資料</span><span class="sxs-lookup"><span data-stu-id="ea6b3-107">Transforming Data</span></span>](#Transforming-Data)  
[<span data-ttu-id="ea6b3-108">從點雲端建立網格</span><span class="sxs-lookup"><span data-stu-id="ea6b3-108">Creating a Mesh From the Point Cloud</span></span>](#Creating-a-Mesh-From-the-Point-Cloud)  
[<span data-ttu-id="ea6b3-109">色彩深度與建立映像</span><span class="sxs-lookup"><span data-stu-id="ea6b3-109">Creating an Image From Depth and Color</span></span>](#Creating-an-Image-From-Depth-and-Color)  
[<span data-ttu-id="ea6b3-110">清除</span><span class="sxs-lookup"><span data-stu-id="ea6b3-110">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="ea6b3-111">完整的來源</span><span class="sxs-lookup"><span data-stu-id="ea6b3-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="ea6b3-112">**以下是我們將使用的函式：**</span><span class="sxs-lookup"><span data-stu-id="ea6b3-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_calibration()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-calibration)  
[`k4a_transformation_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-create)  
[`k4a_image_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-create)  
[`k4a_transformation_depth_image_to_color_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-color-camera)  
[`k4a_transformation_color_image_to_depth_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-color-image-to-depth-camera)  
[`k4a_transformation_depth_image_to_point_cloud()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-point-cloud)  

## <a name="configuration-and-setup"></a><span data-ttu-id="ea6b3-113">組態和設定</span><span class="sxs-lookup"><span data-stu-id="ea6b3-113">Configuration and Setup</span></span>

<span data-ttu-id="ea6b3-114">雖然我們可以在這裡使用幾乎任何我們想要的設定，我們會著重於較小的解析度因為我們將會是未壓縮的資料寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-114">While we could use just about any configuration we wanted here, we're sticking to smaller resolutions since we'll be writing uncompressed data to file.</span></span> <span data-ttu-id="ea6b3-115">檢查上讀取的文件[色彩相機]()並[深度相機]()如需設定的詳細資訊 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-115">Check the documents on reading from the [color camera]() and [depth camera]() for more information about configurations!</span></span>

<span data-ttu-id="ea6b3-116">一個其他的元素是`synchronized_images_only`選項 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-116">One additional element here is the `synchronized_images_only` option!</span></span> <span data-ttu-id="ea6b3-117">將它設定為`true`指定我們只想擷取具有這兩個色彩<i>和</i>填入的深度。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-117">Setting it to `true` specifies that we only want captures that have both color <i>and</i> depth populated.</span></span> <span data-ttu-id="ea6b3-118">如果我們不使用此功能，第一次的幾個會擷取從`k4a_device_get_capture`可能缺少任一個的深度，或是彩色影像。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-118">If we don't use this, the first few captures from `k4a_device_get_capture` may lack either depth, or color images.</span></span>

```C
// Configure the Kinect to open a stream of 512x512 wide field of view
// 16 bit depth data + 1280x720 BRGA color at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;
config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
config.synchronized_images_only = true;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="ea6b3-119">現在，我們有我們的組態資訊，我們要設定將傳遞到所有我們轉換函式的校正物件 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-119">Now that we have our configuration information, we need to set up a calibration object that will be passed into all of our transformation functions!</span></span> <span data-ttu-id="ea6b3-120">此物件包含所使用的轉換與色彩深度空間 visa 反之亦然相機空間座標的預先計算的資源。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-120">This object contains precalculated resources used for transforming coordinates to and from color camera space to depth space and visa versa.</span></span> <span data-ttu-id="ea6b3-121">讓其中一個是很簡單：</span><span class="sxs-lookup"><span data-stu-id="ea6b3-121">Making one is pretty simple:</span></span>

```C
k4a_calibration_t calibration;
k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration);
k4a_transformation_t transform = k4a_transformation_create(&calibration);
```

## <a name="getting-data"></a><span data-ttu-id="ea6b3-122">取得資料</span><span class="sxs-lookup"><span data-stu-id="ea6b3-122">Getting Data</span></span>

<span data-ttu-id="ea6b3-123">現在，我們需要取得色彩影像以及深度影像 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-123">Now we need to acquire both a color image, and a depth image!</span></span> <span data-ttu-id="ea6b3-124">這裡會擷取單一畫面格及它的相關資料。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-124">So here's grabbing a single frame and the relevant data from it.</span></span> <span data-ttu-id="ea6b3-125">如果您的映像的其中一個傳入回 null 項目，請確保您使用`synchronized_images_only`組態中 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-125">If one of your images is coming back null, ensure you used `synchronized_images_only` in your configuration!</span></span>

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Grab image data from the Kinect
k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
int32_t color_w = k4a_image_get_width_pixels (raw_colors);
int32_t color_h = k4a_image_get_height_pixels(raw_colors);
printf("Captured depth image, %dx%d\n", depth_w, depth_h);
printf("Captured rgb image, %dx%d\n", color_w, color_h);
```

## <a name="transforming-data"></a><span data-ttu-id="ea6b3-126">轉換資料</span><span class="sxs-lookup"><span data-stu-id="ea6b3-126">Transforming Data</span></span>

<span data-ttu-id="ea6b3-127">`k4a_transform_`函式會轉換到另一個您映像的資料從相機空間 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-127">The `k4a_transform_` functions will transform your image data from one camera space to another!</span></span> <span data-ttu-id="ea6b3-128">產生的映像會符合的扭曲程度和解析的目標相機空間，因此您可以相互關聯的色彩和深度資訊一起輕鬆。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-128">Resulting images will match the distortion and resolution of the target camera space, so you can correlate color and depth information together easily.</span></span>

<span data-ttu-id="ea6b3-129">比方說 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-129">For example!</span></span> <span data-ttu-id="ea6b3-130">通常，您可能想從相機上，將對應的深度，每個色彩像素的彩色影像 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-130">Quite often, you might want a color image from the camera, with a corresponding depth for each color pixel!</span></span> <span data-ttu-id="ea6b3-131">這麼做，您會將深度資料轉換成色彩相機的空間。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-131">For this, you would transform the depth data into color camera space.</span></span>

<span data-ttu-id="ea6b3-132">或者，您可以從深度數位相機建立 3D 點資料的雲端，並知道什麼是每個點的色彩。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-132">Alternatively, you might want to create a cloud of 3D point data from the depth camera, and know what color each point is.</span></span> <span data-ttu-id="ea6b3-133">為此，我們可以將深度資料轉換成點定域機組，並將彩色影像轉換深度相機空間 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-133">For this, we can transform the depth data into a point cloud, and transform the color image into depth camera space!</span></span> <span data-ttu-id="ea6b3-134">然後，您將有 XYZ 值的緩衝區和對應的緩衝區的色彩。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-134">Then you'll have a buffer of XYZ values, and a corresponding buffer of colors.</span></span>

### <a name="depth-data-in-color-space"></a><span data-ttu-id="ea6b3-135">色彩空間中的深度資料</span><span class="sxs-lookup"><span data-stu-id="ea6b3-135">Depth Data in Color Space</span></span>

<span data-ttu-id="ea6b3-136">這會將轉換深度的資料，以符合色彩相機的輸出 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-136">This transforms depth data to match the color camera's output!</span></span> <span data-ttu-id="ea6b3-137">產生的緩衝區都會在色彩映像的每個像素 16 位元深度值。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-137">The resulting buffer will have a 16 bit depth value for each pixel in the color image.</span></span>
 
```C
k4a_image_t depth_color_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_DEPTH16, 
    color_w, color_h, color_w * sizeof(uint16_t), 
    &depth_color_space))
k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

uint16_t *depth_data = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_color_space));
```

### <a name="creating-a-point-cloud"></a><span data-ttu-id="ea6b3-138">建立點的雲端</span><span class="sxs-lookup"><span data-stu-id="ea6b3-138">Creating a Point Cloud</span></span>

<span data-ttu-id="ea6b3-139">點的雲端，也會儲存在映像資源 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-139">Point clouds are also stored in image resources!</span></span> <span data-ttu-id="ea6b3-140">在這裡，我們會建立映像格式的`K4A_IMAGE_FORMAT_CUSTOM`，因為點雲端並不完全的映像。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-140">Here, we create an image of format `K4A_IMAGE_FORMAT_CUSTOM`, since a point cloud is not exactly an image.</span></span> <span data-ttu-id="ea6b3-141">每個 '中的像素' 映像會組成 3`int16_t`表示 x y z 座標的值，因此我們也會指定正確的大小。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-141">Each 'pixel' in the image will be composed of 3 `int16_t` values representing XYZ coordinates, so we also specify the correct size for that.</span></span>

```C
k4a_image_t point_cloud_xyz;
k4a_image_create(
    K4A_IMAGE_FORMAT_CUSTOM, 
    depth_w, depth_h, depth_w * 3 * sizeof(int16_t), 
    &point_cloud_xyz);
k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

int16_t *xyz_data = reinterpret_cast<int16_t*>(k4a_image_get_buffer(point_cloud_xyz))
```

### <a name="color-data-in-depth-space"></a><span data-ttu-id="ea6b3-142">色彩深度空間中的資料</span><span class="sxs-lookup"><span data-stu-id="ea6b3-142">Color Data in Depth Space</span></span>

<span data-ttu-id="ea6b3-143">這會將轉換的色彩資料，以符合從深度攝影機輸出 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-143">This transforms color data to match the output from the depth camera!</span></span> <span data-ttu-id="ea6b3-144">每個色彩值從產生的緩衝區會對應至深度映像中的值。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-144">Each color value from the resulting buffer will correspond with a value from the depth image.</span></span>

```C
k4a_image_t color_depth_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_COLOR_BGRA32, 
    depth_w, depth_h, depth_w * sizeof(uint32_t), 
    &color_depth_space);
k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

uint8_t *color_data = static_cast<uint8_t*>(k4a_image_get_buffer(color_depth_space));
```

## <a name="creating-a-mesh-from-the-point-cloud"></a><span data-ttu-id="ea6b3-145">從點雲端建立網格</span><span class="sxs-lookup"><span data-stu-id="ea6b3-145">Creating a Mesh From the Point Cloud</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="ea6b3-146">我們一開始先將點的雲端資料轉換成更熟悉的格式。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-146">We'll start by converting the point cloud data into a format that's a little more familiar.</span></span> <span data-ttu-id="ea6b3-147">我們會將它從公釐為單位轉換計量，並將它移到浮點數。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-147">We'll convert it from millimeters to meters, and move it over to floats.</span></span>

```C
// Convert the point cloud from millimeters to meters
float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
for (int32_t i = 0; i < depth_w*depth_h; i++)
{
    vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
    vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
    vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
}
```

<span data-ttu-id="ea6b3-148">現在我們要編結向上這些頂點一些臉部資訊 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-148">Now we'll stitch up these vertices with some face information!</span></span> <span data-ttu-id="ea6b3-149">因為所有項目都會配置為格線，這是簡單的程序，設定每個儲存格角落的連結。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-149">Since everything is laid out as a grid, this is a straightforward process of linking up the corners of each cell.</span></span> <span data-ttu-id="ea6b3-150">我們在這裡做的唯一的額外項目會略過任何包含空白資料的臉部。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-150">The only additional thing we're doing here is skipping any face that contains empty data.</span></span> <span data-ttu-id="ea6b3-151">如果 Kinect 找不到點雲端中的點深度的資料，就會將它在 < 0,0,0 > ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-151">If the Kinect couldn't find depth data for a point in the point cloud, it places it at <0,0,0>!</span></span> <span data-ttu-id="ea6b3-152">它會變成相當 hedgehog，如果您將它們新增至索引清單。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-152">It turns into quite the hedgehog if you add those to the index list.</span></span>

```C
// Make mesh faces as quads across the image. Skip the 
// face if any part of its data is empty.
vector<uint32_t> indices;
for (int32_t y = 0; y < depth_h; y++)
{
    for (int32_t x = 0; x < depth_w; x++)
    {
        int32_t row1 = x +       y * depth_w;
        int32_t row2 = x + (y + 1) * depth_w;

        // If all corners of this quad have depth data
        if (xyz_data[ row1      * 3 + 1] != 0 && 
            xyz_data[(row1 + 1) * 3 + 1] != 0 && 
            xyz_data[ row2      * 3 + 1] != 0 && 
            xyz_data[(row2 + 1) * 3 + 1] != 0)
        {
            // ..then add indices for this quad
            indices.push_back(row2);
            indices.push_back(row2+1);
            indices.push_back(row1+1);
            indices.push_back(row1);
        }
    }
}
```

<span data-ttu-id="ea6b3-153">然後我們就可以寫入檔案這項資訊 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-153">Then we can just write this information to file!</span></span> <span data-ttu-id="ea6b3-154">我們不會移除未使用的色彩，或因為位置中建立索引，所以我們只要傳入我們到目前為止所建立的緩衝區新增複雜度。</span><span class="sxs-lookup"><span data-stu-id="ea6b3-154">We aren't removing unused colors or positions due to added complexity in creating indices, so we can just pass in the buffers we've created so far.</span></span>

```C
// Write geometry data to a .PLY, and clean up
ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, indices.size() / 4, &indices[0]);
free(vertex_positions);
```

## <a name="creating-an-image-from-depth-and-color"></a><span data-ttu-id="ea6b3-155">色彩深度與建立映像</span><span class="sxs-lookup"><span data-stu-id="ea6b3-155">Creating an Image From Depth and Color</span></span>

![](img/ColorandDepthSmall.png)

<span data-ttu-id="ea6b3-156">使用色彩，這是有多麼容易 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-156">With colors, this is much easier to do!</span></span> <span data-ttu-id="ea6b3-157">在這裡，我們將執行簡單的淡出，以黑色的距離，但您可以執行各式各樣有趣的事情，像是裁剪出特定深度的範圍，或儲存為遮罩是相片操作工具中使用的 alpha 色板的深度 ！</span><span class="sxs-lookup"><span data-stu-id="ea6b3-157">Here, we'll do a simple fade to black in the distance, but you could do all sorts of interesting things, like clipping out certain depth ranges, or storing depth in the alpha channel for use as a mask in a photo manipulation tool!</span></span>

```C
// Create an RGB image where we fade color values to black as they recede into the distance
uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
for (int32_t i = 0; i < color_w*color_h; i++)
{
    // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
    float depth = 1 - depth_data[i]/4000.0f;
    depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

    // Fade this pixel, and assign it to our new buffer
    mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
    mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
    mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
}
// Write the image to file
tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
free(mixed_colors);
```

## <a name="cleaning-up"></a><span data-ttu-id="ea6b3-158">清除</span><span class="sxs-lookup"><span data-stu-id="ea6b3-158">Cleaning Up</span></span>

<span data-ttu-id="ea6b3-159">並如往常，發行的所有項目完成時:)</span><span class="sxs-lookup"><span data-stu-id="ea6b3-159">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(point_cloud_xyz);
k4a_image_release(depth_color_space);
k4a_image_release(color_depth_space);
k4a_image_release(raw_colors);
k4a_image_release(raw_depth);
k4a_capture_release(capture);
k4a_transformation_destroy(transform);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="ea6b3-160">完整的來源</span><span class="sxs-lookup"><span data-stu-id="ea6b3-160">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

#include <vector>
using namespace std;

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices);
void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 512x512 wide field of view
    // 16 bit depth data + 1280x720 BRGA color at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;
    config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
    config.synchronized_images_only = true;
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
        printf("Failed to start cameras!\n");

    // Prep data for transforming depth information to color camera space
    k4a_calibration_t calibration;
    if (K4A_FAILED(k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration)))
        printf("Failed to get calibration!\n");
    k4a_transformation_t transform = k4a_transformation_create(&calibration);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    if (K4A_FAILED(k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE)))
        printf("Failed to capture image!\n");

    // Grab image data from the Kinect
    k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
    k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
    int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
    int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
    int32_t color_w = k4a_image_get_width_pixels (raw_colors);
    int32_t color_h = k4a_image_get_height_pixels(raw_colors);
    printf("Captured depth image, %dx%d\n", depth_w, depth_h);
    printf("Captured rgb image, %dx%d\n", color_w, color_h);

    // Transform the raw depth data into color camera space
    k4a_image_t depth_color_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_DEPTH16, color_w, color_h, color_w * sizeof(uint16_t), &depth_color_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

    // Get the point cloud
    k4a_image_t point_cloud_xyz;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_CUSTOM, depth_w, depth_h, depth_w * 3 * sizeof(int16_t), &point_cloud_xyz)))
        printf("Failed to create a point cloud image resource!\n");
    k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

    // Transform the raw color data into depth camera space
    k4a_image_t color_depth_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_COLOR_BGRA32, depth_w, depth_h, depth_w * sizeof(uint32_t), &color_depth_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

    // Get access to the raw color and point cloud data.
    uint8_t  *raw_color_data = static_cast     <uint8_t  *>(k4a_image_get_buffer(raw_colors));
    uint8_t  *color_data     = static_cast     <uint8_t  *>(k4a_image_get_buffer(color_depth_space));
    uint16_t *depth_data     = reinterpret_cast<uint16_t *>(k4a_image_get_buffer(depth_color_space));
    int16_t  *xyz_data       = reinterpret_cast<int16_t  *>(k4a_image_get_buffer(point_cloud_xyz));

    // Turn the point cloud into a mesh, and write it to file!

    // Convert the point cloud from millimeters to meters
    float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
    for (int32_t i = 0; i < depth_w*depth_h; i++)
    {
        vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
        vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
        vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
    }

    // Make mesh faces as quads across the image. Skip the
    // face if any part of its data is empty.
    vector<uint32_t> indices;
    for (int32_t y = 0; y < depth_h; y++)
    {
        for (int32_t x = 0; x < depth_w; x++)
        {
            int32_t row1 = x +       y * depth_w;
            int32_t row2 = x + (y + 1) * depth_w;

            // If all corners of this quad have depth data
            if (xyz_data[ row1      * 3 + 1] != 0 && 
                xyz_data[(row1 + 1) * 3 + 1] != 0 && 
                xyz_data[ row2      * 3 + 1] != 0 && 
                xyz_data[(row2 + 1) * 3 + 1] != 0)
            {
                // ..then add indices for this quad
                indices.push_back(row2);
                indices.push_back(row2+1);
                indices.push_back(row1+1);
                indices.push_back(row1);
            }
        }
    }

    // Write geometry data to a .PLY, and clean up
    ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, static_cast<uint32_t>(indices.size()) / 4, &indices[0]);
    free(vertex_positions);
    
    // Create an RGB image where we fade color values to black as they recede into the distance
    uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
    for (int32_t i = 0; i < color_w*color_h; i++)
    {
        // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
        float depth = 1 - depth_data[i]/4000.0f;
        depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

        // Fade this pixel, and assign it to our new buffer
        mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
        mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
        mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
    }
    // Write the image to file
    tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
    free(mixed_colors);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(point_cloud_xyz);
    k4a_image_release(depth_color_space);
    k4a_image_release(color_depth_space);
    k4a_image_release(raw_colors);
    k4a_image_release(raw_depth);
    k4a_capture_release(capture);
    k4a_transformation_destroy(transform);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices)
{
    FILE *fp = nullptr;
    fopen_s(&fp, filename, "w");

    // Write the .PLY header information
    fprintf(fp, "ply\nformat ascii 1.0\n");
    fprintf(fp, "element vertex %d\nproperty float x\nproperty float y\nproperty float z\nproperty uchar red\nproperty uchar green\nproperty uchar blue\n", vertex_count);
    fprintf(fp, "element face %d\nproperty list uchar int vertex_index\n", index_quad_count);
    fprintf(fp, "end_header\n");

    // Write each vertex with color information!
    for (uint32_t i = 0; i < vertex_count; i++)
    {
        fprintf(fp, "%g %g %g %d %d %d\n", 
            vertex_positions[i*3    ],
            vertex_positions[i*3 + 1],
            vertex_positions[i*3 + 2], 
            vertex_colors_bgra[i*4 + 2], 
            vertex_colors_bgra[i*4 + 1], 
            vertex_colors_bgra[i*4    ]);
    }

    // Write faces as quads.
    for (size_t i = 0; i < index_quad_count; i++)
    {
        fprintf(fp, "4 %d %d %d %d\n", quad_indices[i*4], quad_indices[i*4 + 1], quad_indices[i*4 + 2], quad_indices[i*4 + 3]);
    }
    fclose(fp);
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width%256, (uint8_t)(width/256), height%256, (uint8_t)(height/256), file_channels*8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---accessing-the-imuusingimumd"></a><span data-ttu-id="ea6b3-161">下一步 實驗室-[存取 IMU](UsingIMU.md)</span><span class="sxs-lookup"><span data-stu-id="ea6b3-161">Next Lab - [Accessing the IMU](UsingIMU.md)</span></span>