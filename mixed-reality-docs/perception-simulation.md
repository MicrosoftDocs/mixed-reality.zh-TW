---
title: Perception 模擬
description: 使用認知模擬程式庫來自動化模擬的輸入沉浸式應用程式的指南
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，模擬測試
ms.openlocfilehash: 693750eb753bd11cbe7d7cfb47e04f1a3506ca9a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595377"
---
# <a name="perception-simulation"></a><span data-ttu-id="7695d-104">Perception 模擬</span><span class="sxs-lookup"><span data-stu-id="7695d-104">Perception simulation</span></span>

<span data-ttu-id="7695d-105">若要建置應用程式的自動化的測試嗎？</span><span class="sxs-lookup"><span data-stu-id="7695d-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="7695d-106">您想要超越元件層級的單元測試，並確實執行您應用程式端對端測試嗎？</span><span class="sxs-lookup"><span data-stu-id="7695d-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="7695d-107">Perception 模擬是您要尋找的內容。</span><span class="sxs-lookup"><span data-stu-id="7695d-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="7695d-108">Perception 模擬程式庫傳送假的人們和世界的輸入的資料給您的應用程式讓您可以將自動化測試。</span><span class="sxs-lookup"><span data-stu-id="7695d-108">The Perception Simulation library sends fake human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="7695d-109">例如，您可以模擬人類尋找左右，然後執行動作的輸入。</span><span class="sxs-lookup"><span data-stu-id="7695d-109">For example, you can simulate the input of a human looking left and right and then performing a gesture.</span></span>

<span data-ttu-id="7695d-110">Perception 模擬可以傳送如下的模擬的輸入實體的 HoloLens、 HoloLens 的模擬器，或安裝的混合實境入口網站的電腦。</span><span class="sxs-lookup"><span data-stu-id="7695d-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="7695d-111">模擬會略過混合實境裝置上的即時感應器並傳送認知模擬裝置上執行的應用程式的輸入。</span><span class="sxs-lookup"><span data-stu-id="7695d-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="7695d-112">應用程式收到這些假的輸入的事件，透過相同的 Api，它們一律使用和無法分辨執行搭配真實感應器與 Perception 模擬與執行之間的差異。</span><span class="sxs-lookup"><span data-stu-id="7695d-112">Applications receive these fake input events through the same APIs they always use, and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="7695d-113">Perception 模擬是 HoloLens 模擬器用來傳送模擬的輸入到 HoloLens 虛擬機器中的相同技術。</span><span class="sxs-lookup"><span data-stu-id="7695d-113">Perception Simulation is the same technology used by the HoloLens emulator to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="7695d-114">模擬會藉由建立 IPerceptionSimulationManager 物件開始。</span><span class="sxs-lookup"><span data-stu-id="7695d-114">Simulation starts by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="7695d-115">從該物件中，您可以發出命令來控制模擬 「 人 」，包括前端的位置、 游標位置和筆勢的屬性。</span><span class="sxs-lookup"><span data-stu-id="7695d-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="7695d-116">Visual Studio 專案設定 Perception 模擬</span><span class="sxs-lookup"><span data-stu-id="7695d-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="7695d-117">[安裝 HoloLens 模擬器](install-the-tools.md)開發電腦上。</span><span class="sxs-lookup"><span data-stu-id="7695d-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="7695d-118">模擬器會包含您要用於 Perception 模擬程式庫。</span><span class="sxs-lookup"><span data-stu-id="7695d-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="7695d-119">建立新的 Visual StudioC#桌面 （主控台專案非常適合開始） 的專案。</span><span class="sxs-lookup"><span data-stu-id="7695d-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="7695d-120">做為參考，將下列二進位檔加入至專案 (專案]-> [新增...]-> [參考)。您可以找到它們 **%programfiles (x86) %\Microsoft XDE\10.0.11082.0** 。</span><span class="sxs-lookup"><span data-stu-id="7695d-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in **%ProgramFiles(x86)%\Microsoft XDE\10.0.11082.0** a.</span></span> <span data-ttu-id="7695d-121">PerceptionSimulationManager.Interop.dll-管理C#Perception 模擬的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="7695d-121">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="7695d-122">b.</span><span class="sxs-lookup"><span data-stu-id="7695d-122">b.</span></span> <span data-ttu-id="7695d-123">PerceptionSimulationRest.dll-設定 web 通訊端通訊通道的 HoloLens 或模擬器的程式庫。</span><span class="sxs-lookup"><span data-stu-id="7695d-123">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="7695d-124">c. </span><span class="sxs-lookup"><span data-stu-id="7695d-124">c.</span></span> <span data-ttu-id="7695d-125">SimulationStream.Interop.dll-模擬的共用類型。</span><span class="sxs-lookup"><span data-stu-id="7695d-125">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="7695d-126">將實作新增至您的專案二進位 PerceptionSimulationManager.dll。</span><span class="sxs-lookup"><span data-stu-id="7695d-126">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="7695d-127">第一次以二進位格式將它新增至專案 (專案]-> [新增...]-> [現有項目)。將它儲存為連結，使它不會將它複製到您專案的來源資料夾。</span><span class="sxs-lookup"><span data-stu-id="7695d-127">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="7695d-128">![加入專案做為連結的 PerceptionSimulationManager.dll](images/saveaslink.png) b。</span><span class="sxs-lookup"><span data-stu-id="7695d-128">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="7695d-129">請確定它取得的複製到組建輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="7695d-129">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="7695d-130">這是在二進位檔的屬性工作表中。</span><span class="sxs-lookup"><span data-stu-id="7695d-130">This is in the property sheet for the binary .</span></span> <span data-ttu-id="7695d-131">![若要複製到輸出目錄的 Mark PerceptionSimulationManager.dll](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="7695d-131">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="7695d-132">建立 IPerceptionSimulation Manager 物件</span><span class="sxs-lookup"><span data-stu-id="7695d-132">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="7695d-133">若要控制模擬，您將更新發給 IPerceptionSimulationManager 物件中擷取的物件。</span><span class="sxs-lookup"><span data-stu-id="7695d-133">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="7695d-134">第一個步驟是取得該物件，並將它連接到您的目標裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="7695d-134">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="7695d-135">您可以在裝置入口網站中的按鈕，即可取得您的模擬器的 IP 位址[工具列](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span><span class="sxs-lookup"><span data-stu-id="7695d-135">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span></span>

<span data-ttu-id="7695d-136">![開啟 [裝置入口網站] 圖示](images/emulator-deviceportal.png)**開啟裝置入口網站**:開啟 Windows Device Portal HoloLens os 在模擬器中。</span><span class="sxs-lookup"><span data-stu-id="7695d-136">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

<span data-ttu-id="7695d-137">首先，您將呼叫 RestSimulationStreamSink.Create 取得 RestSimulationStreamSink 物件。</span><span class="sxs-lookup"><span data-stu-id="7695d-137">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="7695d-138">這是目標裝置或模擬器，您會控制透過 http 連線。</span><span class="sxs-lookup"><span data-stu-id="7695d-138">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="7695d-139">您的命令將會傳遞至，而且由[Windows Device Portal](using-the-windows-device-portal.md)裝置或模擬器上執行。</span><span class="sxs-lookup"><span data-stu-id="7695d-139">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="7695d-140">您必須建立物件的四個參數如下：</span><span class="sxs-lookup"><span data-stu-id="7695d-140">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="7695d-141">Uri 的 uri-目標裝置的 IP 位址 (例如，"http://123.123.123.123")</span><span class="sxs-lookup"><span data-stu-id="7695d-141">Uri uri - IP address of the target device (e.g., "http://123.123.123.123")</span></span>
* <span data-ttu-id="7695d-142">System.Net.NetworkCredential 認證-使用者名稱/密碼連接到[Windows Device Portal](using-the-windows-device-portal.md)目標裝置或模擬器上。</span><span class="sxs-lookup"><span data-stu-id="7695d-142">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="7695d-143">如果您要連接到其本機 168 透過模擬器。*.*。 \* 位址將會在相同電腦上，接受任何認證。</span><span class="sxs-lookup"><span data-stu-id="7695d-143">If you are connecting to the emulator via its local 168.*.*.\* address on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="7695d-144">bool 正常-適用於一般的優先權，則為 false 的低優先順序服務。</span><span class="sxs-lookup"><span data-stu-id="7695d-144">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="7695d-145">您通常想要將此設為 *，則為 true*進行測試案例。</span><span class="sxs-lookup"><span data-stu-id="7695d-145">You generally want to set this to *true* for test scenarios.</span></span>
* <span data-ttu-id="7695d-146">System.Threading.CancellationToken 權杖-語彙基元來取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="7695d-146">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="7695d-147">其次，您將建立 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="7695d-147">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="7695d-148">這是您用來控制模擬的物件。</span><span class="sxs-lookup"><span data-stu-id="7695d-148">This is the object you use to control simulation.</span></span> <span data-ttu-id="7695d-149">請注意，這也必須在非同步方法。</span><span class="sxs-lookup"><span data-stu-id="7695d-149">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="7695d-150">控制模擬人類看得</span><span class="sxs-lookup"><span data-stu-id="7695d-150">Control the simulated Human</span></span>

<span data-ttu-id="7695d-151">IPerceptionSimulationManager 有一個人為的屬性會傳回 ISimulatedHuman 物件。</span><span class="sxs-lookup"><span data-stu-id="7695d-151">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="7695d-152">若要控制模擬人類看得，執行此物件上的作業。</span><span class="sxs-lookup"><span data-stu-id="7695d-152">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="7695d-153">例如: </span><span class="sxs-lookup"><span data-stu-id="7695d-153">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="7695d-154">基本範例C#主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="7695d-154">Basic Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="7695d-155">擴充範例C#主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="7695d-155">Extended Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

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
        }
    }
}
```

## <a name="api-reference"></a><span data-ttu-id="7695d-156">API 參考資料</span><span class="sxs-lookup"><span data-stu-id="7695d-156">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="7695d-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="7695d-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="7695d-158">描述模擬的裝置類型</span><span class="sxs-lookup"><span data-stu-id="7695d-158">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="7695d-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="7695d-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="7695d-160">虛構的參考裝置 PerceptionSimulationManager 的預設值</span><span class="sxs-lookup"><span data-stu-id="7695d-160">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="7695d-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="7695d-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="7695d-162">說明前端的追蹤器模式</span><span class="sxs-lookup"><span data-stu-id="7695d-162">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="7695d-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="7695d-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="7695d-164">追蹤的預設標頭。</span><span class="sxs-lookup"><span data-stu-id="7695d-164">Default Head Tracking.</span></span> <span data-ttu-id="7695d-165">這表示系統可能會選取最佳的標頭追蹤執行階段條件所根據的模式。</span><span class="sxs-lookup"><span data-stu-id="7695d-165">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="7695d-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="7695d-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="7695d-167">方向追蹤了唯一的標頭。</span><span class="sxs-lookup"><span data-stu-id="7695d-167">Orientation Only Head Tracking.</span></span> <span data-ttu-id="7695d-168">這表示可能不可靠，追蹤的位置，而且可能無法使用某些功能依賴前端的位置。</span><span class="sxs-lookup"><span data-stu-id="7695d-168">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="7695d-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="7695d-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="7695d-170">位置標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="7695d-170">Positional Head Tracking.</span></span> <span data-ttu-id="7695d-171">這表示，追蹤前端的位置和方向都可靠</span><span class="sxs-lookup"><span data-stu-id="7695d-171">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="7695d-172">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="7695d-172">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="7695d-173">描述模擬的筆勢</span><span class="sxs-lookup"><span data-stu-id="7695d-173">Describes a simulated gesture</span></span>

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

<span data-ttu-id="7695d-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="7695d-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="7695d-175">用來不表示任何筆勢的 sentinel 值</span><span class="sxs-lookup"><span data-stu-id="7695d-175">A sentinel value used to indicate no gestures</span></span>

<span data-ttu-id="7695d-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="7695d-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="7695d-177">手指，按下動作</span><span class="sxs-lookup"><span data-stu-id="7695d-177">A finger pressed gesture</span></span>

<span data-ttu-id="7695d-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="7695d-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="7695d-179">發行的手指筆勢</span><span class="sxs-lookup"><span data-stu-id="7695d-179">A finger released gesture</span></span>

<span data-ttu-id="7695d-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="7695d-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="7695d-181">主要的筆勢</span><span class="sxs-lookup"><span data-stu-id="7695d-181">The home gesture</span></span>

<span data-ttu-id="7695d-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="7695d-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="7695d-183">最大的有效筆勢</span><span class="sxs-lookup"><span data-stu-id="7695d-183">The maximum valid gesture</span></span>

### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="7695d-184">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="7695d-184">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="7695d-185">描述播放狀態</span><span class="sxs-lookup"><span data-stu-id="7695d-185">Describes the state of a playback</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="7695d-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="7695d-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="7695d-187">錄製目前處於已停止，可以開始播放</span><span class="sxs-lookup"><span data-stu-id="7695d-187">The recording is currently stopped and ready for playback</span></span>

<span data-ttu-id="7695d-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="7695d-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="7695d-189">目前正在播放錄製</span><span class="sxs-lookup"><span data-stu-id="7695d-189">The recording is currently playing</span></span>

<span data-ttu-id="7695d-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="7695d-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="7695d-191">目前已暫停錄製</span><span class="sxs-lookup"><span data-stu-id="7695d-191">The recording is currently paused</span></span>

<span data-ttu-id="7695d-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="7695d-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="7695d-193">記錄已到達結尾</span><span class="sxs-lookup"><span data-stu-id="7695d-193">The recording has reached the end</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="7695d-194">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="7695d-194">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="7695d-195">說明 3 個元件的向量，可能會說明了點或在 3D 空間中的向量</span><span class="sxs-lookup"><span data-stu-id="7695d-195">Describes a 3 components vector, which might describe a point or a vector in 3D space</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="7695d-196">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="7695d-196">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="7695d-197">向量的 X 元件</span><span class="sxs-lookup"><span data-stu-id="7695d-197">The X component of the vector</span></span>

<span data-ttu-id="7695d-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="7695d-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="7695d-199">向量的 Y 元件</span><span class="sxs-lookup"><span data-stu-id="7695d-199">The Y component of the vector</span></span>

<span data-ttu-id="7695d-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="7695d-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="7695d-201">向量的 Z 元件</span><span class="sxs-lookup"><span data-stu-id="7695d-201">The Z component of the vector</span></span>

<span data-ttu-id="7695d-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="7695d-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="7695d-203">建構新的 Vector3</span><span class="sxs-lookup"><span data-stu-id="7695d-203">Construct a new Vector3</span></span>

<span data-ttu-id="7695d-204">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-204">Parameters</span></span>
* <span data-ttu-id="7695d-205">x 軸向量的 x 元件</span><span class="sxs-lookup"><span data-stu-id="7695d-205">x - The x component of the vector</span></span>
* <span data-ttu-id="7695d-206">向量的 y y 元件</span><span class="sxs-lookup"><span data-stu-id="7695d-206">y - The y component of the vector</span></span>
* <span data-ttu-id="7695d-207">向量的 z z 元件</span><span class="sxs-lookup"><span data-stu-id="7695d-207">z - The z component of the vector</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="7695d-208">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="7695d-208">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="7695d-209">描述的 3 個元件的旋轉</span><span class="sxs-lookup"><span data-stu-id="7695d-209">Describes a 3 components rotation</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="7695d-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="7695d-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="7695d-211">輪替的字幅元件向下繞著 X 軸</span><span class="sxs-lookup"><span data-stu-id="7695d-211">The Pitch component of the Rotation, down around the X axis</span></span>

<span data-ttu-id="7695d-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="7695d-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="7695d-213">向右繞著 Y 軸旋轉的繞的元件</span><span class="sxs-lookup"><span data-stu-id="7695d-213">The Yaw component of the Rotation, right around the Y axis</span></span>

<span data-ttu-id="7695d-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="7695d-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="7695d-215">向右繞著 Z 軸旋轉的向前復原的元件</span><span class="sxs-lookup"><span data-stu-id="7695d-215">The Roll component of the Rotation, right around the Z axis</span></span>

<span data-ttu-id="7695d-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="7695d-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="7695d-217">建構新的 Rotation3</span><span class="sxs-lookup"><span data-stu-id="7695d-217">Construct a new Rotation3</span></span>

<span data-ttu-id="7695d-218">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-218">Parameters</span></span>
* <span data-ttu-id="7695d-219">字距-旋轉的字幅元件</span><span class="sxs-lookup"><span data-stu-id="7695d-219">pitch - The pitch component of the Rotation</span></span>
* <span data-ttu-id="7695d-220">繞-旋轉的繞元件</span><span class="sxs-lookup"><span data-stu-id="7695d-220">yaw - The yaw component of the Rotation</span></span>
* <span data-ttu-id="7695d-221">向前復原-旋轉的彙總元件</span><span class="sxs-lookup"><span data-stu-id="7695d-221">roll - The roll component of the Rotation</span></span>

### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="7695d-222">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="7695d-222">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="7695d-223">描述檢視範圍，通常由相機</span><span class="sxs-lookup"><span data-stu-id="7695d-223">Describes a view frustum, as typically used by a camera</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="7695d-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="7695d-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="7695d-225">位在範圍中包含的最小距離</span><span class="sxs-lookup"><span data-stu-id="7695d-225">The minimum distance that is contained in the frustum</span></span>

<span data-ttu-id="7695d-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="7695d-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="7695d-227">包含位在範圍中最大距離</span><span class="sxs-lookup"><span data-stu-id="7695d-227">The maximum distance that is contained in the frustum</span></span>

<span data-ttu-id="7695d-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="7695d-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="7695d-229">水平視野的範圍，以弧度為單位 （大於或等於 PI）</span><span class="sxs-lookup"><span data-stu-id="7695d-229">The horizontal field of view of the frustum, in radians (less than PI)</span></span>

<span data-ttu-id="7695d-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="7695d-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="7695d-231">水平視野來檢視垂直欄位的比率</span><span class="sxs-lookup"><span data-stu-id="7695d-231">The ratio of horizontal field of view to vertical field of view</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="7695d-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="7695d-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="7695d-233">產生用來控制裝置的封包的根</span><span class="sxs-lookup"><span data-stu-id="7695d-233">Root for generating the packets used to control a device</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="7695d-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="7695d-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="7695d-235">擷取解譯模擬的人類和模擬的世界的模擬的裝置物件。</span><span class="sxs-lookup"><span data-stu-id="7695d-235">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="7695d-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="7695d-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="7695d-237">擷取控制模擬人類看得的物件。</span><span class="sxs-lookup"><span data-stu-id="7695d-237">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="7695d-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="7695d-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="7695d-239">模擬重設為其預設狀態。</span><span class="sxs-lookup"><span data-stu-id="7695d-239">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="7695d-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="7695d-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="7695d-241">描述可解譯模擬的世界和模擬裝置的介面</span><span class="sxs-lookup"><span data-stu-id="7695d-241">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="7695d-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="7695d-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="7695d-243">從模擬裝置中擷取的標頭追蹤器。</span><span class="sxs-lookup"><span data-stu-id="7695d-243">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="7695d-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="7695d-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="7695d-245">擷取從模擬裝置的手動追蹤程式。</span><span class="sxs-lookup"><span data-stu-id="7695d-245">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="7695d-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="7695d-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="7695d-247">設定模擬的裝置，以符合所提供的裝置類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="7695d-247">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="7695d-248">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-248">Parameters</span></span>
* <span data-ttu-id="7695d-249">類型-新的模擬裝置類型</span><span class="sxs-lookup"><span data-stu-id="7695d-249">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="7695d-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="7695d-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="7695d-251">描述追蹤模擬人類的標頭的模擬裝置的部分介面</span><span class="sxs-lookup"><span data-stu-id="7695d-251">Interface describing the portion of the simulated device that tracks the head of the simulated human</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="7695d-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="7695d-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="7695d-253">擷取並設定目前的前端的追蹤器模式。</span><span class="sxs-lookup"><span data-stu-id="7695d-253">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="7695d-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="7695d-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="7695d-255">描述追蹤的模擬人類的模擬裝置的部分介面</span><span class="sxs-lookup"><span data-stu-id="7695d-255">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="7695d-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7695d-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="7695d-257">擷取與世界相關節點的位置，以公尺為單位</span><span class="sxs-lookup"><span data-stu-id="7695d-257">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="7695d-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="7695d-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="7695d-259">擷取和設定模擬的手動追蹤器的位置相對於標頭的中心。</span><span class="sxs-lookup"><span data-stu-id="7695d-259">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="7695d-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="7695d-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="7695d-261">擷取和設定模擬的手動追蹤器的向下的字幅</span><span class="sxs-lookup"><span data-stu-id="7695d-261">Retrieve and set the downward pitch of the simulated hand tracker</span></span>

<span data-ttu-id="7695d-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="7695d-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="7695d-263">會擷取和設定是否會忽略模擬的手動追蹤器的範圍。</span><span class="sxs-lookup"><span data-stu-id="7695d-263">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="7695d-264">當被忽略，雙手永遠會顯示。</span><span class="sxs-lookup"><span data-stu-id="7695d-264">When ignored, both hands are always visible.</span></span> <span data-ttu-id="7695d-265">不忽略 （預設值） 時手才看得到它們時手動追蹤器的範圍內。</span><span class="sxs-lookup"><span data-stu-id="7695d-265">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="7695d-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="7695d-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="7695d-267">擷取並設定用來判斷是否模擬的手動追蹤器看到實際操作的範圍屬性。</span><span class="sxs-lookup"><span data-stu-id="7695d-267">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="7695d-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="7695d-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="7695d-269">上方的層級介面來控制模擬人類看得</span><span class="sxs-lookup"><span data-stu-id="7695d-269">Top level interface for controlling the simulated human</span></span>

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

<span data-ttu-id="7695d-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7695d-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="7695d-271">擷取和設定節點的位置與相關的世界裡，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="7695d-271">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="7695d-272">位置相對應的人力英呎的中心點。</span><span class="sxs-lookup"><span data-stu-id="7695d-272">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="7695d-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="7695d-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="7695d-274">擷取，並在世界中設定模擬的人臉的方向。</span><span class="sxs-lookup"><span data-stu-id="7695d-274">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="7695d-275">0 的弧度為單位，面臨下負 Z 軸。</span><span class="sxs-lookup"><span data-stu-id="7695d-275">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="7695d-276">正數的弧度順時針旋轉繞 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="7695d-276">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="7695d-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="7695d-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="7695d-278">擷取和設定的高度，模擬的人，以公尺為單位</span><span class="sxs-lookup"><span data-stu-id="7695d-278">Retrieve and set the height of the simulated human, in meters</span></span>

<span data-ttu-id="7695d-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="7695d-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="7695d-280">擷取模擬人類看得在左邊</span><span class="sxs-lookup"><span data-stu-id="7695d-280">Retrieve the left hand of the simulated human</span></span>

<span data-ttu-id="7695d-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="7695d-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="7695d-282">擷取的模擬人類看得右下</span><span class="sxs-lookup"><span data-stu-id="7695d-282">Retrieve the right hand of the simulated human</span></span>

<span data-ttu-id="7695d-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="7695d-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="7695d-284">擷取標頭的模擬人類看得</span><span class="sxs-lookup"><span data-stu-id="7695d-284">Retrieve the head of the simulated human</span></span>

<span data-ttu-id="7695d-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="7695d-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="7695d-286">移動模擬人類看得相對於其目前的位置，以公尺為單位</span><span class="sxs-lookup"><span data-stu-id="7695d-286">Move the simulated human relative to its current position, in meters</span></span>

<span data-ttu-id="7695d-287">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-287">Parameters</span></span>
* <span data-ttu-id="7695d-288">轉譯-若要移動，相對於目前的位置轉譯</span><span class="sxs-lookup"><span data-stu-id="7695d-288">translation - The translation to move, relative to current position</span></span>

<span data-ttu-id="7695d-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="7695d-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="7695d-290">旋轉模擬的人類相對於其目前的方向，順時針方向繞 Y 軸</span><span class="sxs-lookup"><span data-stu-id="7695d-290">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="7695d-291">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-291">Parameters</span></span>
* <span data-ttu-id="7695d-292">弧度為單位-要繞著 Y 軸旋轉的數量</span><span class="sxs-lookup"><span data-stu-id="7695d-292">radians - The amount to rotate around the Y axis</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="7695d-293">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="7695d-293">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="7695d-294">描述模擬人類看得交介面</span><span class="sxs-lookup"><span data-stu-id="7695d-294">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="7695d-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7695d-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="7695d-296">擷取與世界相關節點的位置，以公尺為單位</span><span class="sxs-lookup"><span data-stu-id="7695d-296">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="7695d-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="7695d-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="7695d-298">擷取和設定相對於人類，模擬的左手邊的位置以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="7695d-298">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="7695d-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="7695d-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="7695d-300">會擷取和設定是否手形目前已啟動。</span><span class="sxs-lookup"><span data-stu-id="7695d-300">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="7695d-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="7695d-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="7695d-302">擷取目前可看見 （亦即，它是 HandTracker 可以偵測到的位置） SimulatedDevice 手形是否。</span><span class="sxs-lookup"><span data-stu-id="7695d-302">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="7695d-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="7695d-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="7695d-304">它會顯示以 SimulatedDevice，請移動手形。</span><span class="sxs-lookup"><span data-stu-id="7695d-304">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="7695d-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="7695d-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="7695d-306">移動模擬的左手邊的位置，相對於其目前的位置，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="7695d-306">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="7695d-307">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-307">Parameters</span></span>
* <span data-ttu-id="7695d-308">轉譯-要轉移模擬的手的數量</span><span class="sxs-lookup"><span data-stu-id="7695d-308">translation - The amount to translate the simulated hand</span></span>

<span data-ttu-id="7695d-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="7695d-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="7695d-310">執行使用 （它只會偵測到系統如果啟用了 hand） 模擬的手動動作。</span><span class="sxs-lookup"><span data-stu-id="7695d-310">Perform a gesture using the simulated hand (it will only be detected by the system if the hand is enabled).</span></span>

<span data-ttu-id="7695d-311">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-311">Parameters</span></span>
* <span data-ttu-id="7695d-312">筆勢-要執行的筆勢</span><span class="sxs-lookup"><span data-stu-id="7695d-312">gesture - The gesture to perform</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="7695d-313">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="7695d-313">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="7695d-314">描述模擬人類的標頭的介面</span><span class="sxs-lookup"><span data-stu-id="7695d-314">Interface describing the head of the simulated human</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="7695d-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="7695d-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="7695d-316">擷取與世界相關節點的位置，以公尺為單位</span><span class="sxs-lookup"><span data-stu-id="7695d-316">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="7695d-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="7695d-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="7695d-318">擷取模擬的標頭的旋轉。</span><span class="sxs-lookup"><span data-stu-id="7695d-318">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="7695d-319">正數時尋找沿著軸順時針旋轉弧度為單位。</span><span class="sxs-lookup"><span data-stu-id="7695d-319">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="7695d-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="7695d-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="7695d-321">擷取模擬標頭的直徑。</span><span class="sxs-lookup"><span data-stu-id="7695d-321">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="7695d-322">此值用以判斷前端的中心 （旋轉的點）。</span><span class="sxs-lookup"><span data-stu-id="7695d-322">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="7695d-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="7695d-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="7695d-324">旋轉模擬的標頭，相對於其目前的旋轉角度。</span><span class="sxs-lookup"><span data-stu-id="7695d-324">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="7695d-325">正數時尋找沿著軸順時針旋轉弧度為單位。</span><span class="sxs-lookup"><span data-stu-id="7695d-325">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="7695d-326">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-326">Parameters</span></span>
* <span data-ttu-id="7695d-327">輪替-要旋轉的數量</span><span class="sxs-lookup"><span data-stu-id="7695d-327">rotation - The amount to rotate</span></span>

### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="7695d-328">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="7695d-328">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="7695d-329">播放，載入與單一的錄製內容互動的介面。</span><span class="sxs-lookup"><span data-stu-id="7695d-329">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="7695d-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="7695d-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="7695d-331">擷取錄製中的資料類型的清單。</span><span class="sxs-lookup"><span data-stu-id="7695d-331">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="7695d-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="7695d-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="7695d-333">擷取記錄的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="7695d-333">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="7695d-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="7695d-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="7695d-335">開始播放。</span><span class="sxs-lookup"><span data-stu-id="7695d-335">Start the playback.</span></span> <span data-ttu-id="7695d-336">如果記錄已暫停，播放會繼續從暫停的位置;如果停止，將會開頭開始播放。</span><span class="sxs-lookup"><span data-stu-id="7695d-336">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="7695d-337">如果已播放，則會忽略這個呼叫。</span><span class="sxs-lookup"><span data-stu-id="7695d-337">If already playing, this call is ignored.</span></span>

<span data-ttu-id="7695d-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="7695d-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="7695d-339">暫停播放其目前的位置。</span><span class="sxs-lookup"><span data-stu-id="7695d-339">Pauses the playback at its current location.</span></span> <span data-ttu-id="7695d-340">如果停止錄製時，會忽略呼叫。</span><span class="sxs-lookup"><span data-stu-id="7695d-340">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="7695d-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="7695d-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="7695d-342">（在從一開始的 100 奈秒間隔） 會設法在指定的時間錄製與暫停在該位置。</span><span class="sxs-lookup"><span data-stu-id="7695d-342">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="7695d-343">如果記錄結尾以外的位置時，它會暫停在最後一個畫面格。</span><span class="sxs-lookup"><span data-stu-id="7695d-343">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="7695d-344">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-344">Parameters</span></span>
* <span data-ttu-id="7695d-345">刻度-要搜尋的時間</span><span class="sxs-lookup"><span data-stu-id="7695d-345">ticks - The time to which to seek</span></span>

<span data-ttu-id="7695d-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="7695d-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="7695d-347">停止播放，並且重設到開頭的位置</span><span class="sxs-lookup"><span data-stu-id="7695d-347">Stops the playback and resets the position to the beginning</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="7695d-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="7695d-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="7695d-349">在播放期間接收的狀態變更的介面</span><span class="sxs-lookup"><span data-stu-id="7695d-349">Interface for receiving state changes during playback</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="7695d-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="7695d-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="7695d-351">當 ISimulationRecording 播放狀態變更時呼叫</span><span class="sxs-lookup"><span data-stu-id="7695d-351">Called when an ISimulationRecording's playback state has changed</span></span>

<span data-ttu-id="7695d-352">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-352">Parameters</span></span>
* <span data-ttu-id="7695d-353">newState-錄製的新狀態</span><span class="sxs-lookup"><span data-stu-id="7695d-353">newState - The new state of the recording</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="7695d-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="7695d-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="7695d-355">建立 Perception 模擬物件的根物件</span><span class="sxs-lookup"><span data-stu-id="7695d-355">Root object for creating Perception Simulation objects</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="7695d-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="7695d-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="7695d-357">產生模擬的封包，並將其傳遞至所提供的接收的物件上建立。</span><span class="sxs-lookup"><span data-stu-id="7695d-357">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="7695d-358">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-358">Parameters</span></span>
* <span data-ttu-id="7695d-359">接收-將會收到所有產生的封包的接收</span><span class="sxs-lookup"><span data-stu-id="7695d-359">sink - The sink that will receive all generated packets</span></span>

<span data-ttu-id="7695d-360">傳回值</span><span class="sxs-lookup"><span data-stu-id="7695d-360">Return value</span></span>

<span data-ttu-id="7695d-361">建立的管理員</span><span class="sxs-lookup"><span data-stu-id="7695d-361">The created Manager</span></span>

<span data-ttu-id="7695d-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="7695d-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="7695d-363">建立儲存在指定路徑的檔案中的所有接收的封包的接收。</span><span class="sxs-lookup"><span data-stu-id="7695d-363">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="7695d-364">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-364">Parameters</span></span>
* <span data-ttu-id="7695d-365">path-建立檔案的路徑</span><span class="sxs-lookup"><span data-stu-id="7695d-365">path - The path of the file to create</span></span>

<span data-ttu-id="7695d-366">傳回值</span><span class="sxs-lookup"><span data-stu-id="7695d-366">Return value</span></span>

<span data-ttu-id="7695d-367">建立的接收</span><span class="sxs-lookup"><span data-stu-id="7695d-367">The created sink</span></span>

<span data-ttu-id="7695d-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="7695d-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="7695d-369">從指定的檔案載入記錄</span><span class="sxs-lookup"><span data-stu-id="7695d-369">Load a recording from the specified file</span></span>

<span data-ttu-id="7695d-370">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-370">Parameters</span></span>
* <span data-ttu-id="7695d-371">路徑-要載入之檔案的路徑</span><span class="sxs-lookup"><span data-stu-id="7695d-371">path - The path of the file to load</span></span>
* <span data-ttu-id="7695d-372">處理站-錄製用於建立 ISimulationStreamSink 時所需的處理站</span><span class="sxs-lookup"><span data-stu-id="7695d-372">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>

<span data-ttu-id="7695d-373">傳回值</span><span class="sxs-lookup"><span data-stu-id="7695d-373">Return value</span></span>

<span data-ttu-id="7695d-374">載入的記錄</span><span class="sxs-lookup"><span data-stu-id="7695d-374">The loaded recording</span></span>

<span data-ttu-id="7695d-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory，Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="7695d-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="7695d-376">從指定的檔案載入記錄</span><span class="sxs-lookup"><span data-stu-id="7695d-376">Load a recording from the specified file</span></span>

<span data-ttu-id="7695d-377">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-377">Parameters</span></span>
* <span data-ttu-id="7695d-378">路徑-要載入之檔案的路徑</span><span class="sxs-lookup"><span data-stu-id="7695d-378">path - The path of the file to load</span></span>
* <span data-ttu-id="7695d-379">處理站-錄製用於建立 ISimulationStreamSink 時所需的處理站</span><span class="sxs-lookup"><span data-stu-id="7695d-379">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>
* <span data-ttu-id="7695d-380">回呼的回呼會接收更新 regrading 錄製的狀態</span><span class="sxs-lookup"><span data-stu-id="7695d-380">callback - A callback which receives updates regrading the recording's status</span></span>

<span data-ttu-id="7695d-381">傳回值</span><span class="sxs-lookup"><span data-stu-id="7695d-381">Return value</span></span>

<span data-ttu-id="7695d-382">載入的記錄</span><span class="sxs-lookup"><span data-stu-id="7695d-382">The loaded recording</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="7695d-383">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="7695d-383">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="7695d-384">說明不同類型的資料流資料</span><span class="sxs-lookup"><span data-stu-id="7695d-384">Describes the different types of stream data</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    All = None | Head | Hands | SpatialMapping | Calibration | Environment
}
```

<span data-ttu-id="7695d-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="7695d-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="7695d-386">用來表示任何資料流的資料類型之 sentinel 值</span><span class="sxs-lookup"><span data-stu-id="7695d-386">A sentinel value used to indicate no stream data types</span></span>

<span data-ttu-id="7695d-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="7695d-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="7695d-388">Stream 的位置和方向的標頭的相關資料</span><span class="sxs-lookup"><span data-stu-id="7695d-388">Stream of data regarding the position and orientation of the head</span></span>

<span data-ttu-id="7695d-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="7695d-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="7695d-390">Stream 的位置和指針的筆勢的相關資料</span><span class="sxs-lookup"><span data-stu-id="7695d-390">Stream of data regarding the position and gestures of hands</span></span>

<span data-ttu-id="7695d-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="7695d-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="7695d-392">Stream 的空間的對應環境的相關資料</span><span class="sxs-lookup"><span data-stu-id="7695d-392">Stream of data regarding spatial mapping of the environment</span></span>

<span data-ttu-id="7695d-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="7695d-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="7695d-394">Stream 的校正裝置的相關資料。</span><span class="sxs-lookup"><span data-stu-id="7695d-394">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="7695d-395">在遠端模式系統只接受校正封包。</span><span class="sxs-lookup"><span data-stu-id="7695d-395">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="7695d-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="7695d-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="7695d-397">Stream 的 關於裝置的環境資料</span><span class="sxs-lookup"><span data-stu-id="7695d-397">Stream of data regarding the environment of the device</span></span>

<span data-ttu-id="7695d-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="7695d-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="7695d-399">用來表示所有記錄的資料類型之 sentinel 值</span><span class="sxs-lookup"><span data-stu-id="7695d-399">A sentinel value used to indicate all recorded data types</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="7695d-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="7695d-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="7695d-401">接收資料封包從模擬的資料流物件</span><span class="sxs-lookup"><span data-stu-id="7695d-401">An object that receives data packets from a simulation stream</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="7695d-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="7695d-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="7695d-403">接收單一封包時，也就是在內部具類型和版本設定</span><span class="sxs-lookup"><span data-stu-id="7695d-403">Receives a single packet, which is internally typed and versioned</span></span>

<span data-ttu-id="7695d-404">參數</span><span class="sxs-lookup"><span data-stu-id="7695d-404">Parameters</span></span>
* <span data-ttu-id="7695d-405">length-將封包的長度</span><span class="sxs-lookup"><span data-stu-id="7695d-405">length - The length of the packet</span></span>
* <span data-ttu-id="7695d-406">封包-封包的資料</span><span class="sxs-lookup"><span data-stu-id="7695d-406">packet - The data of the packet</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="7695d-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="7695d-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="7695d-408">物件，可建立 ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="7695d-408">An object that creates ISimulationStreamSink</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="7695d-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="7695d-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="7695d-410">建立 ISimulationStreamSink 的單一執行個體</span><span class="sxs-lookup"><span data-stu-id="7695d-410">Creates a single instance of ISimulationStreamSink</span></span>

<span data-ttu-id="7695d-411">傳回值</span><span class="sxs-lookup"><span data-stu-id="7695d-411">Return value</span></span>

<span data-ttu-id="7695d-412">建立的接收</span><span class="sxs-lookup"><span data-stu-id="7695d-412">The created sink</span></span>
