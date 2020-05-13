---
title: 感知模擬
description: 使用認知模擬程式庫將沉浸式應用程式的模擬輸入自動化的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens、模擬、測試
ms.openlocfilehash: 701fd39490d87b70df9bd68cc99da6482d41b676
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228023"
---
# <a name="perception-simulation"></a>感知模擬

您要為您的應用程式建立自動化測試嗎？ 您是否想要讓測試超越元件層級的單元測試，並確實執行應用程式端對端？ 認知模擬是您要尋找的。 認知模擬程式庫會將人類和世界的輸入資料傳送至您的應用程式，讓您可以自動化測試。 例如，您可以模擬人類的輸入，尋找特定、可重複的位置，然後執行手勢或使用動作控制器。

認知模擬可以將這類模擬的輸入傳送至實體 HoloLens、HoloLens 模擬器（第一代）、HoloLens 2 模擬器，或已安裝混合 Reality 入口網站的電腦。 認知模擬會略過混合現實裝置上的即時感應器，並將模擬的輸入傳送至裝置上執行的應用程式。 應用程式會透過他們一律使用的相同 Api 來接收這些輸入事件，而且無法分辨實際感應器的執行與使用認知模擬的執行之間的差異。 認知模擬是 HoloLens 模擬器用來將模擬輸入傳送至 HoloLens 虛擬機器的相同技術。

若要開始在程式碼中使用模擬，請先建立 IPerceptionSimulationManager 物件。 您可以從該物件發出命令，以控制模擬「人」的屬性，包括頭部位置、手位置和手勢，而且您可以啟用和操作動作控制器。

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>設定認知模擬的 Visual Studio 專案
1. 在開發電腦上[安裝 HoloLens 模擬器](install-the-tools.md)。 模擬器包含您將用於認知模擬的程式庫。
2. 建立新的 Visual Studio c # 桌面專案（主控台專案非常適合用來開始使用）。
3. 將下列二進位檔新增至您的專案做為參考（專案 >的 [加入 >參考 ...]）。您可以在% ProgramFiles （x86）% \ Microsoft XDE \\ （版本）中找到它們，例如適用于 HoloLens 2 模擬器的 **% ProgramFiles （x86）% \ microsoft XDE \\ 10.0.18362.0** 。  （注意：雖然二進位檔是 HoloLens 2 模擬器的一部分，但它們也適用于桌上型電腦上的 Windows Mixed Reality）。為. PerceptionSimulationManager 感知模擬的 Managed c # 包裝函式。
    b. PerceptionSimulationRest：用於設定 HoloLens 或模擬器之 web 通訊端通道的程式庫。
    c. SimulationStream：模擬的共用類型。
4. 將 [執行二進位 PerceptionSimulationManager] 加入至您的專案 a。 首先，將它當做二進位檔新增至專案（專案 >[加入 >現有專案 ...]）。將它儲存為連結，讓它不會將它複製到您的專案源資料夾。 ![將 PerceptionSimulationManager 新增至專案，做為連結 ](images/saveaslink.png) b。 然後，確定它已複製到組建上的輸出檔案夾。 這是在二進位檔的屬性工作表中。 ![將 PerceptionSimulationManager 標記為要複製到輸出目錄](images/copyalways.png)
5. 將使用中的方案平臺設定為 x64。  （如果不存在，請使用 Configuration Manager 來建立 x64 的平臺專案）。

## <a name="creating-an-iperceptionsimulation-manager-object"></a>建立 IPerceptionSimulation Manager 物件

若要控制模擬，您會對從 IPerceptionSimulationManager 物件取得的物件發出更新。 第一個步驟是取得該物件，並將它連接到您的目標裝置或模擬器。 您可以按一下[工具列](using-the-hololens-emulator.md)中的 [裝置入口網站] 按鈕，以取得您的模擬器的 IP 位址

![開啟裝置入口網站圖示 ](images/emulator-deviceportal.png) **開啟裝置入口網站**：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。  對於 Windows Mixed Reality，可以在 [更新 & 安全性] 底下的 [設定] 應用程式中抓取，然後在 [啟用裝置入口網站] 底下的 [使用下列方式連線] 區段中，找到 [適用于開發人員]。  請務必記下 IP 位址和埠。

首先，您會呼叫 RestSimulationStreamSink 來取得 RestSimulationStreamSink 物件。 這是您將透過 HTTP 連接控制的目標裝置或模擬器。 您的命令將會傳遞至裝置或模擬器上執行的[Windows 裝置入口網站](using-the-windows-device-portal.md)並加以處理。 建立物件所需的四個參數如下：
* Uri uri-目標裝置的 IP 位址（例如，" https://123.123.123.123 " 或 " https://123.123.123.123:50080 "）
* NetworkCredential 認證-使用者名稱/密碼，用於連接至目標裝置或模擬器上的[Windows 裝置入口網站](using-the-windows-device-portal.md)。 如果您是透過本機位址連接到模擬器（例如，*168 ...**）在同一部電腦上，將會接受任何認證。
* 一般優先權為 bool 標準-True，低優先順序為 false。 在測試案例中，您通常會想要將此設定為*true* ，讓您的測試能夠取得控制權。  模擬器和 Windows Mixed Reality 模擬會使用低優先順序的連接。  如果您的測試也使用低優先順序的連接，最近建立的連接將會受到控制。
* CancellationToken token-用來取消非同步作業的 Token。

第二，您將建立 IPerceptionSimulationManager。 這是您用來控制模擬的物件。 請注意，這也必須在非同步方法中完成。

## <a name="control-the-simulated-human"></a>控制模擬的人類

IPerceptionSimulationManager 具有可傳回 ISimulatedHuman 物件的人類屬性。 若要控制模擬的人力，請在此物件上執行作業。 例如：

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>基本 c # 主控台應用程式範例

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>擴充的範例 c # 主控台應用程式

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>6 DOF 控制器上的附注

在模擬的 6 DOF 控制器上呼叫方法的任何屬性之前，您必須啟動控制器。  不這樣做會導致例外狀況。  從 Windows 10 5 月2019更新開始，可以藉由將 ISimulatedSixDofController 物件上的 Status 屬性設為 SimulatedSixDofControllerStatus，來安裝和啟動模擬的 6 DOF 控制器。
在 Windows 10 2018 年10月更新和較舊版本中，您必須先呼叫位於 \Windows\System32 資料夾中的 PerceptionSimulationDevice 工具，分別安裝模擬的 6 DOF 控制器。  此工具的使用方式如下：


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

例如：

```
    PerceptionSimulationDevice.exe i 6dof 1
```

支援的動作包括：
* i = 安裝
* q = 查詢
* r = 移除

支援的實例包括：
* 1 = 左 6 DOF 控制器
* 2 = 右方的 6 DOF 控制器

進程的結束代碼會指出成功（零傳回值）或失敗（非零的傳回值）。  使用「q」動作來查詢是否已安裝控制器時，如果控制器尚未安裝，則傳回值會是零（0），如果已安裝控制器，則傳回一個（1）。

移除 Windows 10 2018 年10月更新或更早版本上的控制器時，請先透過 API 將其狀態設定為 Off，然後再呼叫 PerceptionSimulationDevice 工具。

請注意，此工具必須以系統管理員身分執行。




## <a name="api-reference"></a>API 參考

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>PerceptionSimulation. SimulatedDeviceType

描述模擬裝置類型

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**PerceptionSimulation. SimulatedDeviceType. Reference**

虛構的參考設備，這是 PerceptionSimulationManager 的預設值

### <a name="microsoftperceptionsimulationheadtrackermode"></a>PerceptionSimulation. HeadTrackerMode

描述 head 追蹤器模式

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**PerceptionSimulation. HeadTrackerMode. Default**

預設的標頭追蹤。 這表示系統可能會根據執行時間條件來選取最佳的標頭追蹤模式。

**PerceptionSimulation. HeadTrackerMode. 取向**

僅限方向的頭追蹤。 這表示追蹤的位置可能不可靠，而且某些相依于 head 位置的功能可能無法使用。

**PerceptionSimulation. HeadTrackerMode. Position**

位置標頭追蹤。 這表示追蹤的標頭位置和方向都是可靠的

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>PerceptionSimulation. SimulatedGesture

描述模擬的手勢

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**PerceptionSimulation. SimulatedGesture. None**

用來表示沒有手勢的 sentinel 值。

**PerceptionSimulation. SimulatedGesture. FingerPressed**

按手指的手勢。

**PerceptionSimulation. SimulatedGesture. FingerReleased**

手指已釋放手勢。

**PerceptionSimulation. SimulatedGesture 首頁**

Home/system 手勢。

**PerceptionSimulation. SimulatedGesture. Max**

有效手勢的最大值。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>PerceptionSimulation. SimulatedSixDofControllerStatus

模擬的 6 DOF 控制器的可能狀態。

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**PerceptionSimulation. SimulatedSixDofControllerStatus. Off**

6 DOF 控制器已關閉。

**PerceptionSimulation. SimulatedSixDofControllerStatus. Active**

已開啟並追蹤 6 DOF 控制器。

**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**

已開啟6個 DOF 控制器，但無法加以追蹤。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>PerceptionSimulation. SimulatedSixDofControllerButton

模擬的 6 DOF 控制器上支援的按鈕。

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**PerceptionSimulation. SimulatedSixDofControllerButton. None**

用來表示沒有按鈕的 sentinel 值。

**PerceptionSimulation. SimulatedSixDofControllerButton 首頁**

[首頁] 按鈕已按下。

**PerceptionSimulation. SimulatedSixDofControllerButton. 功能表**

[功能表] 按鈕已按下。

**PerceptionSimulation. SimulatedSixDofControllerButton. 抓握**

[抓握] 按鈕已按下。

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**

觸控板已按下。

**PerceptionSimulation. SimulatedSixDofControllerButton. Select**

[選取] 按鈕已按下。

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**

觸控板觸及。

**PerceptionSimulation. SimulatedSixDofControllerButton. 操縱杆**

操縱杆已按下。

**PerceptionSimulation. SimulatedSixDofControllerButton. Max**

有效的最大按鈕。


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>PerceptionSimulation. SimulatedEyesCalibrationState

模擬眼睛的校正狀態

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**PerceptionSimulation. SimulatedEyesCalibrationState. 無法使用**

眼睛校正無法使用。

**PerceptionSimulation. SimulatedEyesCalibrationState. Ready**

眼睛已校正。  這是預設值。

**PerceptionSimulation. SimulatedEyesCalibrationState. 設定**

正在校正眼睛。

**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**

眼睛必須經過校正。

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>PerceptionSimulation. SimulatedHandJointTrackingAccuracy

手的接點追蹤精確度。

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 無法使用**

不會追蹤聯合。

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 近似值**

會推斷聯合位置。

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**

聯合會受到完整追蹤。

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>PerceptionSimulation. SimulatedHandPose

手的接點追蹤精確度。

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**PerceptionSimulation. SimulatedHandPose. 已關閉**

手的手指接點設定為反映封閉式姿勢。

**PerceptionSimulation. SimulatedHandPose. Open**

手中的手指接點設定為反映開放式姿勢。

**PerceptionSimulation. SimulatedHandPose Point**

手的手指接點設定為反映指標姿勢。

**PerceptionSimulation. SimulatedHandPose**

手中的手指接點設定為反映捏合姿勢。

**PerceptionSimulation. SimulatedHandPose. Max**

SimulatedHandPose 的最大有效值。


### <a name="microsoftperceptionsimulationplaybackstate"></a>PerceptionSimulation. PlaybackState

描述播放的狀態。

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**PerceptionSimulation. PlaybackState. 已停止**

錄製目前已停止，並已準備好進行播放。

**PerceptionSimulation. PlaybackState. 播放**

目前現正播放錄製。

**PerceptionSimulation. PlaybackState. 已暫停**

錄製目前已暫停。

**PerceptionSimulation. PlaybackState. 結束**

錄音已到達結尾。

### <a name="microsoftperceptionsimulationvector3"></a>PerceptionSimulation. Vector3

描述3個元件向量，這可能會描述3D 空間中的點或向量。

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**PerceptionSimulation. Vector3. X**

此向量的 X 元件。

**PerceptionSimulation. Vector3. Y**

此向量的 Y 元件。

**PerceptionSimulation. Vector3. Z**

此向量的 Z 元件。

**PerceptionSimulation. Vector3. #ctor （System.web，system.object，system.string）**

建立新的 Vector3。

參數
* x-向量的 x 元件。
* y-向量的 y 元件。
* z-向量的 z 元件。

### <a name="microsoftperceptionsimulationrotation3"></a>PerceptionSimulation. Rotation3

描述3個元件旋轉。

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**PerceptionSimulation. Rotation3. 音調**

旋轉的螺距元件，沿著 X 軸向下移動。

**PerceptionSimulation. Rotation3. 偏擺**

旋轉的偏擺元件，右側為 Y 軸。

**PerceptionSimulation. Rotation3. 滾動**

旋轉的變換元件，以 Z 軸為左右。

**PerceptionSimulation. Rotation3. #ctor （System.web，system.object，system.string）**

建立新的 Rotation3。

參數
* 音調-旋轉的螺距元件。
* 偏擺-旋轉的偏擺元件。
* 變換：旋轉的滾動部分。

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>PerceptionSimulation. SimulatedHandJointConfiguration

描述模擬手上的聯合設定。

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**PerceptionSimulation. SimulatedHandJointConfiguration. Position**

聯合的位置。

**PerceptionSimulation. SimulatedHandJointConfiguration. 旋轉**

聯合的旋轉。

**PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**

聯合的追蹤精確度。


### <a name="microsoftperceptionsimulationfrustum"></a>PerceptionSimulation。

描述相機通常使用的視圖截圖。

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**PerceptionSimulation。 Near**

以截距包含的最小距離。

**PerceptionSimulation....。**

以截距包含的最大距離。

**PerceptionSimulation. FieldOfView**

截量的水準欄位，以弧度為單位（小於 PI）。

**PerceptionSimulation. AspectRatio**

水準欄位和視圖垂直欄位的比例。

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a>PerceptionSimulation. SimulatedDisplayConfiguration

說明模擬耳機顯示的設定。

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**

從開頭到左邊的轉換，以供身歷聲轉譯之用。

**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**

針對身歷聲轉譯的目的而左邊的旋轉。

**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**

從前端到右眼的轉換，以供身歷聲轉譯之用。

**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**

針對身歷聲轉譯的角度所做的調整。

**PerceptionSimulation. SimulatedDisplayConfiguration Ipd**

系統報告的 Ipd 值，用於呈現身歷聲轉譯。

**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**

針對 left 和 right 眼轉換提供的值是否應視為有效，並套用至執行中的系統。

**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**

是否應將為 Ipd 提供的值視為有效，並套用至執行中的系統。


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>PerceptionSimulation. IPerceptionSimulationManager

用於產生用於控制裝置之封包的根目錄。

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**PerceptionSimulation. IPerceptionSimulationManager. 裝置**

取出模擬的裝置物件，以解讀模擬的人和模擬世界。

**PerceptionSimulation. IPerceptionSimulationManager. 人類**

取得控制模擬人類的物件。

**PerceptionSimulation. IPerceptionSimulationManager. 重設**

將模擬重設為其預設狀態。

### <a name="microsoftperceptionsimulationisimulateddevice"></a>PerceptionSimulation. ISimulatedDevice

描述裝置的介面，其會解讀模擬世界和模擬的人類

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**PerceptionSimulation. ISimulatedDevice. HeadTracker**

從模擬裝置取出 Head 追蹤器。

**PerceptionSimulation. ISimulatedDevice. HandTracker**

從模擬的裝置抓取手追蹤器。

**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType （Microsoft PerceptionSimulation. SimulatedDeviceType）**

設定模擬裝置的屬性，以符合提供的裝置類型。

參數
* 類型-模擬裝置的新類型

### <a name="microsoftperceptionsimulationisimulateddevice2"></a>PerceptionSimulation. ISimulatedDevice2

藉由將 ISimulatedDevice 轉型為 ISimulatedDevice2，可以使用其他屬性。

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**

抓取或設定模擬的人是否積極戴頭戴式裝置。

**PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**

取出或設定模擬顯示的屬性。

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>PerceptionSimulation. ISimulatedHeadTracker

描述模擬裝置之部分的介面，它會追蹤模擬人類的標頭。

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**

抓取和設定目前的標頭追蹤器模式。

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>PerceptionSimulation. ISimulatedHandTracker

描述模擬裝置之部分的介面，可追蹤模擬人類的手

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**

以量表為單位，抓取節點與世界的相對位置。

**PerceptionSimulation. ISimulatedHandTracker. Position**

抓取和設定模擬的手勢追蹤器的位置（相對於 head 的中心）。

**PerceptionSimulation. ISimulatedHandTracker. 音調**

取出並設定模擬的手勢追蹤器的下音調。

**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**

抓取和設定是否忽略模擬的手勢追蹤器的錐狀。 忽略時，一律會顯示這兩個手。 [未略過] （預設值）只會在手上的 [指標追蹤器] 中出現時才會顯示。

**PerceptionSimulation. ISimulatedHandTracker。**

抓取和設定用來判斷模擬的手追蹤器是否可以看見手的「截錐」屬性。

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>PerceptionSimulation. ISimulatedHuman

控制模擬人類的最上層介面。

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**PerceptionSimulation. ISimulatedHuman. WorldPosition**

抓取和設定與世界相關的節點位置（以量為單位）。 這個位置會對應到位於人類腳中心的點。

**PerceptionSimulation. ISimulatedHuman. 方向**

取得並設定世界中模擬的人臉方向。 0弧度會向下到負 Z 軸。 正弧度會順時針旋轉 Y 軸。

**PerceptionSimulation. ISimulatedHuman. Height**

抓取和設定模擬人的高度（以計量為單位）。

**PerceptionSimulation. ISimulatedHuman. LeftHand**

取出模擬人類的左邊。

**PerceptionSimulation. ISimulatedHuman. RightHand**

取得模擬人類的右手邊。

**PerceptionSimulation. ISimulatedHuman. Head**

抓取模擬人類的標頭。

**PerceptionSimulation. ISimulatedHuman. Move （PerceptionSimulation. Vector3）**

將模擬人相對於其目前位置（以計量為單位）。

參數
* 轉譯-要移動的轉譯，相對於目前的位置。

**PerceptionSimulation. ISimulatedHuman. 旋轉（System.web）**

以順時針方向針對 Y 軸，將模擬的人類旋轉相對於其目前方向

參數
* 弧度-要繞著 Y 軸旋轉的數量。

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>PerceptionSimulation. ISimulatedHuman2

藉由將 ISimulatedHuman 轉型為 ISimulatedHuman2，可以使用其他屬性。

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**PerceptionSimulation. ISimulatedHuman2. LeftController**

取出左邊的 6 DOF 控制器。

**PerceptionSimulation. ISimulatedHuman2. RightController**

取出右6個 DOF 的控制器。


### <a name="microsoftperceptionsimulationisimulatedhand"></a>PerceptionSimulation. ISimulatedHand

描述模擬人類之手的介面

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**PerceptionSimulation. ISimulatedHand. WorldPosition**

以量表為單位，抓取節點與世界的相對位置。

**PerceptionSimulation. ISimulatedHand. Position**

抓取和設定相對於人類（以量為單位）的模擬手勢位置。

**PerceptionSimulation. ISimulatedHand. 已啟用**

抓取並設定是否目前已啟用手。

**PerceptionSimulation. ISimulatedHand. Visible**

抓取 SimulatedDevice 的目前是否可見（也就是它是否位於 HandTracker 所偵測到的位置）。

**PerceptionSimulation. ISimulatedHand. EnsureVisible**

移動手，讓 SimulatedDevice 可以看到它。

**PerceptionSimulation. ISimulatedHand. Move （PerceptionSimulation. Vector3）**

移動模擬手相對於其目前位置的位置（以量為單位）。

參數
* 轉譯-要轉譯模擬手的數量。

**PerceptionSimulation. ISimulatedHand. PerformGesture （Microsoft PerceptionSimulation. SimulatedGesture）**

使用模擬的手執行手勢。  只有在已啟用手時，系統才會偵測到此檔案。

參數
* 手勢-要執行的手勢。

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>PerceptionSimulation. ISimulatedHand2

將 ISimulatedHand 轉換為 ISimulatedHand2 可使用其他屬性。
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**PerceptionSimulation. ISimulatedHand2. 取向**

取出或設定模擬手的旋轉。  正弧度在沿著軸進行檢查時，順時針旋轉。

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>PerceptionSimulation. ISimulatedHand3

將 ISimulatedHand 轉換為 ISimulatedHand3 可使用其他屬性
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**

取得所指定聯合的聯合設定。

**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**

設定所指定聯合的聯合設定。

**PerceptionSimulation. ISimulatedHand3. SetHandPose**

將手設定為已知的姿勢，並使用選擇性的旗標來製作動畫。  注意：動畫不會導致直接反映其最終的聯合設定。


### <a name="microsoftperceptionsimulationisimulatedhead"></a>PerceptionSimulation. ISimulatedHead

描述模擬人的頭的介面。

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**PerceptionSimulation. ISimulatedHead. WorldPosition**

以量表為單位，抓取節點與世界的相對位置。

**PerceptionSimulation. ISimulatedHead. 旋轉**

取出模擬標頭的旋轉。 正弧度在沿著軸進行檢查時，順時針旋轉。

**PerceptionSimulation. ISimulatedHead. 直徑**

取出模擬的標頭直徑。 這個值是用來判斷 head 的中心（旋轉點）。

**PerceptionSimulation. ISimulatedHead. 旋轉（PerceptionSimulation. Rotation3）**

將模擬的標頭旋轉成相對於目前的旋轉。 正弧度在沿著軸進行檢查時，順時針旋轉。

參數
* 旋轉-要旋轉的數量。

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>PerceptionSimulation. ISimulatedHead2

將 ISimulatedHead 轉換為 ISimulatedHead2 可使用其他屬性

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**PerceptionSimulation. ISimulatedHead2 眼**

取出模擬人類的眼睛。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>PerceptionSimulation. ISimulatedSixDofController

描述與模擬人類相關聯之 6 DOF 控制器的介面。

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**

以量表為單位，抓取節點與世界的相對位置。

**PerceptionSimulation. ISimulatedSixDofController. 狀態**

取得或設定控制器的目前狀態。  控制器狀態必須設定為 [關閉] 以外的值，才能進行移動、旋轉或按下按鈕的任何呼叫。

**PerceptionSimulation. ISimulatedSixDofController. Position**

抓取或設定模擬控制器相對於人類的位置（以計量為單位）。

**PerceptionSimulation. ISimulatedSixDofController. 取向**

取得或設定模擬控制器的方向。

**PerceptionSimulation. ISimulatedSixDofController. Move （PerceptionSimulation. Vector3）**

移動模擬控制器相對於其目前位置的位置（以計量為單位）。

參數
* 轉譯-要轉譯模擬控制器的數量。

**PerceptionSimulation. ISimulatedSixDofController. PressButton （SimulatedSixDofControllerButton）**

在模擬控制器上按下按鈕。  只有在已啟用控制器的情況下，系統才會偵測到它。

參數
* 按鈕-要按的按鈕。

**PerceptionSimulation. ISimulatedSixDofController. ReleaseButton （SimulatedSixDofControllerButton）**

釋放模擬控制器上的按鈕。  只有在已啟用控制器的情況下，系統才會偵測到它。

參數
* 按鈕-要發行的按鈕。

**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition （out float，out float）**

取得模擬控制器的觸控板上的模擬手指位置。

參數
* x-手指的水準位置。
* y-手指的垂直位置。

**PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition （float，float）**

將模擬手指的位置設定在模擬控制器的觸控板上。

參數
* x-手指的水準位置。
* y-手指的垂直位置。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>PerceptionSimulation. ISimulatedSixDofController2

將 ISimulatedSixDofController 轉換為 ISimulatedSixDofController2 可使用其他屬性和方法

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition （out float，out float）**

取得模擬控制站上模擬的操縱杆位置。

參數
* x-操縱杆的水準位置。
* y-操縱杆的垂直位置。

**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition （float，float）**

在模擬的控制器上設定模擬的操縱杆位置。

參數
* x-操縱杆的水準位置。
* y-操縱杆的垂直位置。

**PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**

取出或設定模擬控制器的電池計量。  此值必須大於0.0 且小於或等於100.0。


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>PerceptionSimulation. ISimulatedEyes

描述模擬人眼的介面。

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**PerceptionSimulation. ISimulatedEyes. 旋轉**

取出模擬眼睛的旋轉。 正弧度在沿著軸進行檢查時，順時針旋轉。

**PerceptionSimulation. ISimulatedEyes. 旋轉（PerceptionSimulation. Rotation3）**

旋轉模擬的眼睛，相對於其目前的旋轉。 正弧度在沿著軸進行檢查時，順時針旋轉。

參數
* 旋轉-要旋轉的數量。

**PerceptionSimulation. ISimulatedEyes. CalibrationState**

抓取或設定模擬眼睛的校正狀態。

**PerceptionSimulation. ISimulatedEyes. WorldPosition**

以量表為單位，抓取節點與世界的相對位置。


### <a name="microsoftperceptionsimulationisimulationrecording"></a>PerceptionSimulation. ISimulationRecording

介面，用於與已載入播放的單一錄製進行互動。

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**PerceptionSimulation. ISimulationRecording 資料類型**

抓取記錄中的資料類型清單。

**PerceptionSimulation. ISimulationRecording. 州/省**

抓取錄影的目前狀態。

**PerceptionSimulation. ISimulationRecording. Play**

開始播放。 如果記錄已暫停，播放將會從暫停的位置繼續執行;如果已停止，播放會從一開始開始。 如果已經在播放，則會忽略此呼叫。

**PerceptionSimulation. ISimulationRecording. Pause**

暫停播放目前的位置。 如果記錄已停止，則會忽略呼叫。

**PerceptionSimulation. ISimulationRecording. Seek （System.object）**

將記錄搜尋到指定的時間（從一開始的100毫微秒間隔），並在該位置暫停。 如果時間超過錄製的結尾，則會在最後一個畫面上暫停。

參數
* 刻度-要搜尋的時間。

**PerceptionSimulation. ISimulationRecording. Stop**

停止播放，並將位置重設為開頭。

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>PerceptionSimulation. ISimulationRecordingCallback

用於在播放期間接收狀態變更的介面。

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged （Microsoft PerceptionSimulation. PlaybackState）**

當 ISimulationRecording 的播放狀態變更時呼叫。

參數
* newState-記錄的新狀態。

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>PerceptionSimulation. PerceptionSimulationManager

用來建立認知模擬物件的根物件。

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager （Microsoft PerceptionSimulation. ISimulationStreamSink）**

在物件上建立以產生模擬封包，並將它們傳遞至提供的接收。

參數
* sink-接收所有產生的封包的接收器。

傳回值

建立的管理員。

**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording （System.string）**

建立接收，將所有接收的封包儲存在檔案中的指定路徑。

參數
* path-要建立之檔案的路徑。

傳回值

建立的接收。

**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording （System.string，Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory）**

從指定的檔案載入記錄。

參數
* path-要載入的檔案路徑。
* factory-記錄在需要時用來建立 ISimulationStreamSink 的 factory。

傳回值

載入的記錄。

**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording （System.string，microsoft. PerceptionSimulation. ISimulationStreamSinkFactory，PerceptionSimulation）**

從指定的檔案載入記錄。

參數
* path-要載入的檔案路徑。
* factory-記錄在需要時用來建立 ISimulationStreamSink 的 factory。
* 回呼-接收更新的回呼會 regrading 記錄的狀態。

傳回值

載入的記錄。

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>PerceptionSimulation. StreamDataTypes

描述不同類型的資料流程資料。

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

**PerceptionSimulation. StreamDataTypes. None**

用來表示沒有資料流程資料類型的 sentinel 值。

**PerceptionSimulation. StreamDataTypes. Head**

關於 head 位置和方向的資料流程。

**PerceptionSimulation. StreamDataTypes**

關於手的位置和手勢的資料流程。

**PerceptionSimulation. StreamDataTypes. SpatialMapping**

關於環境的空間對應的資料流程。

**PerceptionSimulation. StreamDataTypes. 校正**

關於裝置校正的資料流程。 只有在遠端模式中的系統才會接受校正封包。

**PerceptionSimulation. StreamDataTypes. 環境**

關於裝置環境的資料流程。

**PerceptionSimulation. StreamDataTypes. SixDofControllers**

有關動作控制器的資料流程。

**PerceptionSimulation. StreamDataTypes 眼**

關於模擬人類眼的資料流程。

**PerceptionSimulation. StreamDataTypes. DisplayConfiguration**

關於裝置顯示設定的資料流程。

**PerceptionSimulation. StreamDataTypes. 全部**

用來表示所有記錄資料類型的 sentinel 值。

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>PerceptionSimulation. ISimulationStreamSink

物件，接收來自模擬資料流程的資料封包。

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**PerceptionSimulation. ISimulationStreamSink. OnPacketReceived （uint length，byte [] 封包）**

接收單一封包，其為內部輸入和版本設定。

參數
* length-封包的長度。
* 封包-封包的資料。

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>PerceptionSimulation. ISimulationStreamSinkFactory

建立 ISimulationStreamSink 的物件。

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink （）**

建立 ISimulationStreamSink 的單一實例。

傳回值

建立的接收。
