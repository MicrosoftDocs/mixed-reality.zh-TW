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
# <a name="perception-simulation"></a><span data-ttu-id="97853-104">感知模擬</span><span class="sxs-lookup"><span data-stu-id="97853-104">Perception simulation</span></span>

<span data-ttu-id="97853-105">您要為您的應用程式建立自動化測試嗎？</span><span class="sxs-lookup"><span data-stu-id="97853-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="97853-106">您是否想要讓測試超越元件層級的單元測試，並確實執行應用程式端對端？</span><span class="sxs-lookup"><span data-stu-id="97853-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="97853-107">認知模擬是您要尋找的。</span><span class="sxs-lookup"><span data-stu-id="97853-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="97853-108">認知模擬程式庫會將人類和世界的輸入資料傳送至您的應用程式，讓您可以自動化測試。</span><span class="sxs-lookup"><span data-stu-id="97853-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="97853-109">例如，您可以模擬人類的輸入，尋找特定、可重複的位置，然後執行手勢或使用動作控制器。</span><span class="sxs-lookup"><span data-stu-id="97853-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="97853-110">認知模擬可以將這類模擬的輸入傳送至實體 HoloLens、HoloLens 模擬器（第一代）、HoloLens 2 模擬器，或已安裝混合 Reality 入口網站的電腦。</span><span class="sxs-lookup"><span data-stu-id="97853-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="97853-111">認知模擬會略過混合現實裝置上的即時感應器，並將模擬的輸入傳送至裝置上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="97853-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="97853-112">應用程式會透過他們一律使用的相同 Api 來接收這些輸入事件，而且無法分辨實際感應器的執行與使用認知模擬的執行之間的差異。</span><span class="sxs-lookup"><span data-stu-id="97853-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="97853-113">認知模擬是 HoloLens 模擬器用來將模擬輸入傳送至 HoloLens 虛擬機器的相同技術。</span><span class="sxs-lookup"><span data-stu-id="97853-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="97853-114">若要開始在程式碼中使用模擬，請先建立 IPerceptionSimulationManager 物件。</span><span class="sxs-lookup"><span data-stu-id="97853-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="97853-115">您可以從該物件發出命令，以控制模擬「人」的屬性，包括頭部位置、手位置和手勢，而且您可以啟用和操作動作控制器。</span><span class="sxs-lookup"><span data-stu-id="97853-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="97853-116">設定認知模擬的 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="97853-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="97853-117">在開發電腦上[安裝 HoloLens 模擬器](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="97853-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="97853-118">模擬器包含您將用於認知模擬的程式庫。</span><span class="sxs-lookup"><span data-stu-id="97853-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="97853-119">建立新的 Visual Studio c # 桌面專案（主控台專案非常適合用來開始使用）。</span><span class="sxs-lookup"><span data-stu-id="97853-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="97853-120">將下列二進位檔新增至您的專案做為參考（專案 >的 [加入 >參考 ...]）。您可以在% ProgramFiles （x86）% \ Microsoft XDE \\ （版本）中找到它們，例如適用于 HoloLens 2 模擬器的 **% ProgramFiles （x86）% \ microsoft XDE \\ 10.0.18362.0** 。</span><span class="sxs-lookup"><span data-stu-id="97853-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="97853-121">（注意：雖然二進位檔是 HoloLens 2 模擬器的一部分，但它們也適用于桌上型電腦上的 Windows Mixed Reality）。為.</span><span class="sxs-lookup"><span data-stu-id="97853-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="97853-122">PerceptionSimulationManager 感知模擬的 Managed c # 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="97853-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="97853-123">b.</span><span class="sxs-lookup"><span data-stu-id="97853-123">b.</span></span> <span data-ttu-id="97853-124">PerceptionSimulationRest：用於設定 HoloLens 或模擬器之 web 通訊端通道的程式庫。</span><span class="sxs-lookup"><span data-stu-id="97853-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="97853-125">c.</span><span class="sxs-lookup"><span data-stu-id="97853-125">c.</span></span> <span data-ttu-id="97853-126">SimulationStream：模擬的共用類型。</span><span class="sxs-lookup"><span data-stu-id="97853-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="97853-127">將 [執行二進位 PerceptionSimulationManager] 加入至您的專案 a。</span><span class="sxs-lookup"><span data-stu-id="97853-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="97853-128">首先，將它當做二進位檔新增至專案（專案 >[加入 >現有專案 ...]）。將它儲存為連結，讓它不會將它複製到您的專案源資料夾。</span><span class="sxs-lookup"><span data-stu-id="97853-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="97853-129">![將 PerceptionSimulationManager 新增至專案，做為連結 ](images/saveaslink.png) b。</span><span class="sxs-lookup"><span data-stu-id="97853-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="97853-130">然後，確定它已複製到組建上的輸出檔案夾。</span><span class="sxs-lookup"><span data-stu-id="97853-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="97853-131">這是在二進位檔的屬性工作表中。</span><span class="sxs-lookup"><span data-stu-id="97853-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="97853-132">![將 PerceptionSimulationManager 標記為要複製到輸出目錄](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="97853-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="97853-133">將使用中的方案平臺設定為 x64。</span><span class="sxs-lookup"><span data-stu-id="97853-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="97853-134">（如果不存在，請使用 Configuration Manager 來建立 x64 的平臺專案）。</span><span class="sxs-lookup"><span data-stu-id="97853-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="97853-135">建立 IPerceptionSimulation Manager 物件</span><span class="sxs-lookup"><span data-stu-id="97853-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="97853-136">若要控制模擬，您會對從 IPerceptionSimulationManager 物件取得的物件發出更新。</span><span class="sxs-lookup"><span data-stu-id="97853-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="97853-137">第一個步驟是取得該物件，並將它連接到您的目標裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="97853-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="97853-138">您可以按一下[工具列](using-the-hololens-emulator.md)中的 [裝置入口網站] 按鈕，以取得您的模擬器的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="97853-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="97853-139">![開啟裝置入口網站圖示 ](images/emulator-deviceportal.png) **開啟裝置入口網站**：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="97853-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="97853-140">對於 Windows Mixed Reality，可以在 [更新 & 安全性] 底下的 [設定] 應用程式中抓取，然後在 [啟用裝置入口網站] 底下的 [使用下列方式連線] 區段中，找到 [適用于開發人員]。</span><span class="sxs-lookup"><span data-stu-id="97853-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="97853-141">請務必記下 IP 位址和埠。</span><span class="sxs-lookup"><span data-stu-id="97853-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="97853-142">首先，您會呼叫 RestSimulationStreamSink 來取得 RestSimulationStreamSink 物件。</span><span class="sxs-lookup"><span data-stu-id="97853-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="97853-143">這是您將透過 HTTP 連接控制的目標裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="97853-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="97853-144">您的命令將會傳遞至裝置或模擬器上執行的[Windows 裝置入口網站](using-the-windows-device-portal.md)並加以處理。</span><span class="sxs-lookup"><span data-stu-id="97853-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="97853-145">建立物件所需的四個參數如下：</span><span class="sxs-lookup"><span data-stu-id="97853-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="97853-146">Uri uri-目標裝置的 IP 位址（例如，" https://123.123.123.123 " 或 " https://123.123.123.123:50080 "）</span><span class="sxs-lookup"><span data-stu-id="97853-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="97853-147">NetworkCredential 認證-使用者名稱/密碼，用於連接至目標裝置或模擬器上的[Windows 裝置入口網站](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="97853-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="97853-148">如果您是透過本機位址連接到模擬器（例如，\*168 ...\*\*）在同一部電腦上，將會接受任何認證。</span><span class="sxs-lookup"><span data-stu-id="97853-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="97853-149">一般優先權為 bool 標準-True，低優先順序為 false。</span><span class="sxs-lookup"><span data-stu-id="97853-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="97853-150">在測試案例中，您通常會想要將此設定為*true* ，讓您的測試能夠取得控制權。</span><span class="sxs-lookup"><span data-stu-id="97853-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="97853-151">模擬器和 Windows Mixed Reality 模擬會使用低優先順序的連接。</span><span class="sxs-lookup"><span data-stu-id="97853-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="97853-152">如果您的測試也使用低優先順序的連接，最近建立的連接將會受到控制。</span><span class="sxs-lookup"><span data-stu-id="97853-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="97853-153">CancellationToken token-用來取消非同步作業的 Token。</span><span class="sxs-lookup"><span data-stu-id="97853-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="97853-154">第二，您將建立 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="97853-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="97853-155">這是您用來控制模擬的物件。</span><span class="sxs-lookup"><span data-stu-id="97853-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="97853-156">請注意，這也必須在非同步方法中完成。</span><span class="sxs-lookup"><span data-stu-id="97853-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="97853-157">控制模擬的人類</span><span class="sxs-lookup"><span data-stu-id="97853-157">Control the simulated Human</span></span>

<span data-ttu-id="97853-158">IPerceptionSimulationManager 具有可傳回 ISimulatedHuman 物件的人類屬性。</span><span class="sxs-lookup"><span data-stu-id="97853-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="97853-159">若要控制模擬的人力，請在此物件上執行作業。</span><span class="sxs-lookup"><span data-stu-id="97853-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="97853-160">例如：</span><span class="sxs-lookup"><span data-stu-id="97853-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="97853-161">基本 c # 主控台應用程式範例</span><span class="sxs-lookup"><span data-stu-id="97853-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="97853-162">擴充的範例 c # 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="97853-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="97853-163">6 DOF 控制器上的附注</span><span class="sxs-lookup"><span data-stu-id="97853-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="97853-164">在模擬的 6 DOF 控制器上呼叫方法的任何屬性之前，您必須啟動控制器。</span><span class="sxs-lookup"><span data-stu-id="97853-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="97853-165">不這樣做會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="97853-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="97853-166">從 Windows 10 5 月2019更新開始，可以藉由將 ISimulatedSixDofController 物件上的 Status 屬性設為 SimulatedSixDofControllerStatus，來安裝和啟動模擬的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="97853-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="97853-167">在 Windows 10 2018 年10月更新和較舊版本中，您必須先呼叫位於 \Windows\System32 資料夾中的 PerceptionSimulationDevice 工具，分別安裝模擬的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="97853-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="97853-168">此工具的使用方式如下：</span><span class="sxs-lookup"><span data-stu-id="97853-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="97853-169">例如：</span><span class="sxs-lookup"><span data-stu-id="97853-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="97853-170">支援的動作包括：</span><span class="sxs-lookup"><span data-stu-id="97853-170">Supported actions are:</span></span>
* <span data-ttu-id="97853-171">i = 安裝</span><span class="sxs-lookup"><span data-stu-id="97853-171">i = install</span></span>
* <span data-ttu-id="97853-172">q = 查詢</span><span class="sxs-lookup"><span data-stu-id="97853-172">q = query</span></span>
* <span data-ttu-id="97853-173">r = 移除</span><span class="sxs-lookup"><span data-stu-id="97853-173">r = remove</span></span>

<span data-ttu-id="97853-174">支援的實例包括：</span><span class="sxs-lookup"><span data-stu-id="97853-174">Supported instances are:</span></span>
* <span data-ttu-id="97853-175">1 = 左 6 DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="97853-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="97853-176">2 = 右方的 6 DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="97853-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="97853-177">進程的結束代碼會指出成功（零傳回值）或失敗（非零的傳回值）。</span><span class="sxs-lookup"><span data-stu-id="97853-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="97853-178">使用「q」動作來查詢是否已安裝控制器時，如果控制器尚未安裝，則傳回值會是零（0），如果已安裝控制器，則傳回一個（1）。</span><span class="sxs-lookup"><span data-stu-id="97853-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="97853-179">移除 Windows 10 2018 年10月更新或更早版本上的控制器時，請先透過 API 將其狀態設定為 Off，然後再呼叫 PerceptionSimulationDevice 工具。</span><span class="sxs-lookup"><span data-stu-id="97853-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="97853-180">請注意，此工具必須以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="97853-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="97853-181">API 參考</span><span class="sxs-lookup"><span data-stu-id="97853-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="97853-182">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="97853-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="97853-183">描述模擬裝置類型</span><span class="sxs-lookup"><span data-stu-id="97853-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="97853-184">**PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="97853-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="97853-185">虛構的參考設備，這是 PerceptionSimulationManager 的預設值</span><span class="sxs-lookup"><span data-stu-id="97853-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="97853-186">PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="97853-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="97853-187">描述 head 追蹤器模式</span><span class="sxs-lookup"><span data-stu-id="97853-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="97853-188">**PerceptionSimulation. HeadTrackerMode. Default**</span><span class="sxs-lookup"><span data-stu-id="97853-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="97853-189">預設的標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="97853-189">Default Head Tracking.</span></span> <span data-ttu-id="97853-190">這表示系統可能會根據執行時間條件來選取最佳的標頭追蹤模式。</span><span class="sxs-lookup"><span data-stu-id="97853-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="97853-191">**PerceptionSimulation. HeadTrackerMode. 取向**</span><span class="sxs-lookup"><span data-stu-id="97853-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="97853-192">僅限方向的頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="97853-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="97853-193">這表示追蹤的位置可能不可靠，而且某些相依于 head 位置的功能可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="97853-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="97853-194">**PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="97853-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="97853-195">位置標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="97853-195">Positional Head Tracking.</span></span> <span data-ttu-id="97853-196">這表示追蹤的標頭位置和方向都是可靠的</span><span class="sxs-lookup"><span data-stu-id="97853-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="97853-197">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="97853-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="97853-198">描述模擬的手勢</span><span class="sxs-lookup"><span data-stu-id="97853-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="97853-199">**PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="97853-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="97853-200">用來表示沒有手勢的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="97853-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="97853-201">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="97853-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="97853-202">按手指的手勢。</span><span class="sxs-lookup"><span data-stu-id="97853-202">A finger pressed gesture.</span></span>

<span data-ttu-id="97853-203">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="97853-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="97853-204">手指已釋放手勢。</span><span class="sxs-lookup"><span data-stu-id="97853-204">A finger released gesture.</span></span>

<span data-ttu-id="97853-205">**PerceptionSimulation. SimulatedGesture 首頁**</span><span class="sxs-lookup"><span data-stu-id="97853-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="97853-206">Home/system 手勢。</span><span class="sxs-lookup"><span data-stu-id="97853-206">The home/system gesture.</span></span>

<span data-ttu-id="97853-207">**PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="97853-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="97853-208">有效手勢的最大值。</span><span class="sxs-lookup"><span data-stu-id="97853-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="97853-209">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="97853-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="97853-210">模擬的 6 DOF 控制器的可能狀態。</span><span class="sxs-lookup"><span data-stu-id="97853-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="97853-211">**PerceptionSimulation. SimulatedSixDofControllerStatus. Off**</span><span class="sxs-lookup"><span data-stu-id="97853-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="97853-212">6 DOF 控制器已關閉。</span><span class="sxs-lookup"><span data-stu-id="97853-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="97853-213">**PerceptionSimulation. SimulatedSixDofControllerStatus. Active**</span><span class="sxs-lookup"><span data-stu-id="97853-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="97853-214">已開啟並追蹤 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="97853-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="97853-215">**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="97853-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="97853-216">已開啟6個 DOF 控制器，但無法加以追蹤。</span><span class="sxs-lookup"><span data-stu-id="97853-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="97853-217">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="97853-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="97853-218">模擬的 6 DOF 控制器上支援的按鈕。</span><span class="sxs-lookup"><span data-stu-id="97853-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="97853-219">**PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="97853-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="97853-220">用來表示沒有按鈕的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="97853-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="97853-221">**PerceptionSimulation. SimulatedSixDofControllerButton 首頁**</span><span class="sxs-lookup"><span data-stu-id="97853-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="97853-222">[首頁] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="97853-222">The Home button is pressed.</span></span>

<span data-ttu-id="97853-223">**PerceptionSimulation. SimulatedSixDofControllerButton. 功能表**</span><span class="sxs-lookup"><span data-stu-id="97853-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="97853-224">[功能表] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="97853-224">The Menu button is pressed.</span></span>

<span data-ttu-id="97853-225">**PerceptionSimulation. SimulatedSixDofControllerButton. 抓握**</span><span class="sxs-lookup"><span data-stu-id="97853-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="97853-226">[抓握] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="97853-226">The Grip button is pressed.</span></span>

<span data-ttu-id="97853-227">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="97853-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="97853-228">觸控板已按下。</span><span class="sxs-lookup"><span data-stu-id="97853-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="97853-229">**PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="97853-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="97853-230">[選取] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="97853-230">The Select button is pressed.</span></span>

<span data-ttu-id="97853-231">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="97853-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="97853-232">觸控板觸及。</span><span class="sxs-lookup"><span data-stu-id="97853-232">The TouchPad is touched.</span></span>

<span data-ttu-id="97853-233">**PerceptionSimulation. SimulatedSixDofControllerButton. 操縱杆**</span><span class="sxs-lookup"><span data-stu-id="97853-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="97853-234">操縱杆已按下。</span><span class="sxs-lookup"><span data-stu-id="97853-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="97853-235">**PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="97853-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="97853-236">有效的最大按鈕。</span><span class="sxs-lookup"><span data-stu-id="97853-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="97853-237">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="97853-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="97853-238">模擬眼睛的校正狀態</span><span class="sxs-lookup"><span data-stu-id="97853-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="97853-239">**PerceptionSimulation. SimulatedEyesCalibrationState. 無法使用**</span><span class="sxs-lookup"><span data-stu-id="97853-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="97853-240">眼睛校正無法使用。</span><span class="sxs-lookup"><span data-stu-id="97853-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="97853-241">**PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="97853-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="97853-242">眼睛已校正。</span><span class="sxs-lookup"><span data-stu-id="97853-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="97853-243">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="97853-243">This is the default value.</span></span>

<span data-ttu-id="97853-244">**PerceptionSimulation. SimulatedEyesCalibrationState. 設定**</span><span class="sxs-lookup"><span data-stu-id="97853-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="97853-245">正在校正眼睛。</span><span class="sxs-lookup"><span data-stu-id="97853-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="97853-246">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="97853-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="97853-247">眼睛必須經過校正。</span><span class="sxs-lookup"><span data-stu-id="97853-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="97853-248">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="97853-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="97853-249">手的接點追蹤精確度。</span><span class="sxs-lookup"><span data-stu-id="97853-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="97853-250">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 無法使用**</span><span class="sxs-lookup"><span data-stu-id="97853-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="97853-251">不會追蹤聯合。</span><span class="sxs-lookup"><span data-stu-id="97853-251">The joint is not tracked.</span></span>

<span data-ttu-id="97853-252">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 近似值**</span><span class="sxs-lookup"><span data-stu-id="97853-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="97853-253">會推斷聯合位置。</span><span class="sxs-lookup"><span data-stu-id="97853-253">The joint position is inferred.</span></span>

<span data-ttu-id="97853-254">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**</span><span class="sxs-lookup"><span data-stu-id="97853-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="97853-255">聯合會受到完整追蹤。</span><span class="sxs-lookup"><span data-stu-id="97853-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="97853-256">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="97853-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="97853-257">手的接點追蹤精確度。</span><span class="sxs-lookup"><span data-stu-id="97853-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="97853-258">**PerceptionSimulation. SimulatedHandPose. 已關閉**</span><span class="sxs-lookup"><span data-stu-id="97853-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="97853-259">手的手指接點設定為反映封閉式姿勢。</span><span class="sxs-lookup"><span data-stu-id="97853-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="97853-260">**PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="97853-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="97853-261">手中的手指接點設定為反映開放式姿勢。</span><span class="sxs-lookup"><span data-stu-id="97853-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="97853-262">**PerceptionSimulation. SimulatedHandPose Point**</span><span class="sxs-lookup"><span data-stu-id="97853-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="97853-263">手的手指接點設定為反映指標姿勢。</span><span class="sxs-lookup"><span data-stu-id="97853-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="97853-264">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="97853-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="97853-265">手中的手指接點設定為反映捏合姿勢。</span><span class="sxs-lookup"><span data-stu-id="97853-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="97853-266">**PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="97853-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="97853-267">SimulatedHandPose 的最大有效值。</span><span class="sxs-lookup"><span data-stu-id="97853-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="97853-268">PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="97853-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="97853-269">描述播放的狀態。</span><span class="sxs-lookup"><span data-stu-id="97853-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="97853-270">**PerceptionSimulation. PlaybackState. 已停止**</span><span class="sxs-lookup"><span data-stu-id="97853-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="97853-271">錄製目前已停止，並已準備好進行播放。</span><span class="sxs-lookup"><span data-stu-id="97853-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="97853-272">**PerceptionSimulation. PlaybackState. 播放**</span><span class="sxs-lookup"><span data-stu-id="97853-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="97853-273">目前現正播放錄製。</span><span class="sxs-lookup"><span data-stu-id="97853-273">The recording is currently playing.</span></span>

<span data-ttu-id="97853-274">**PerceptionSimulation. PlaybackState. 已暫停**</span><span class="sxs-lookup"><span data-stu-id="97853-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="97853-275">錄製目前已暫停。</span><span class="sxs-lookup"><span data-stu-id="97853-275">The recording is currently paused.</span></span>

<span data-ttu-id="97853-276">**PerceptionSimulation. PlaybackState. 結束**</span><span class="sxs-lookup"><span data-stu-id="97853-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="97853-277">錄音已到達結尾。</span><span class="sxs-lookup"><span data-stu-id="97853-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="97853-278">PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="97853-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="97853-279">描述3個元件向量，這可能會描述3D 空間中的點或向量。</span><span class="sxs-lookup"><span data-stu-id="97853-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="97853-280">**PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="97853-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="97853-281">此向量的 X 元件。</span><span class="sxs-lookup"><span data-stu-id="97853-281">The X component of the vector.</span></span>

<span data-ttu-id="97853-282">**PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="97853-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="97853-283">此向量的 Y 元件。</span><span class="sxs-lookup"><span data-stu-id="97853-283">The Y component of the vector.</span></span>

<span data-ttu-id="97853-284">**PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="97853-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="97853-285">此向量的 Z 元件。</span><span class="sxs-lookup"><span data-stu-id="97853-285">The Z component of the vector.</span></span>

<span data-ttu-id="97853-286">**PerceptionSimulation. Vector3. #ctor （System.web，system.object，system.string）**</span><span class="sxs-lookup"><span data-stu-id="97853-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="97853-287">建立新的 Vector3。</span><span class="sxs-lookup"><span data-stu-id="97853-287">Construct a new Vector3.</span></span>

<span data-ttu-id="97853-288">參數</span><span class="sxs-lookup"><span data-stu-id="97853-288">Parameters</span></span>
* <span data-ttu-id="97853-289">x-向量的 x 元件。</span><span class="sxs-lookup"><span data-stu-id="97853-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="97853-290">y-向量的 y 元件。</span><span class="sxs-lookup"><span data-stu-id="97853-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="97853-291">z-向量的 z 元件。</span><span class="sxs-lookup"><span data-stu-id="97853-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="97853-292">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="97853-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="97853-293">描述3個元件旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="97853-294">**PerceptionSimulation. Rotation3. 音調**</span><span class="sxs-lookup"><span data-stu-id="97853-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="97853-295">旋轉的螺距元件，沿著 X 軸向下移動。</span><span class="sxs-lookup"><span data-stu-id="97853-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="97853-296">**PerceptionSimulation. Rotation3. 偏擺**</span><span class="sxs-lookup"><span data-stu-id="97853-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="97853-297">旋轉的偏擺元件，右側為 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="97853-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="97853-298">**PerceptionSimulation. Rotation3. 滾動**</span><span class="sxs-lookup"><span data-stu-id="97853-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="97853-299">旋轉的變換元件，以 Z 軸為左右。</span><span class="sxs-lookup"><span data-stu-id="97853-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="97853-300">**PerceptionSimulation. Rotation3. #ctor （System.web，system.object，system.string）**</span><span class="sxs-lookup"><span data-stu-id="97853-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="97853-301">建立新的 Rotation3。</span><span class="sxs-lookup"><span data-stu-id="97853-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="97853-302">參數</span><span class="sxs-lookup"><span data-stu-id="97853-302">Parameters</span></span>
* <span data-ttu-id="97853-303">音調-旋轉的螺距元件。</span><span class="sxs-lookup"><span data-stu-id="97853-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="97853-304">偏擺-旋轉的偏擺元件。</span><span class="sxs-lookup"><span data-stu-id="97853-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="97853-305">變換：旋轉的滾動部分。</span><span class="sxs-lookup"><span data-stu-id="97853-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="97853-306">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="97853-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="97853-307">描述模擬手上的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="97853-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="97853-308">**PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="97853-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="97853-309">聯合的位置。</span><span class="sxs-lookup"><span data-stu-id="97853-309">The position of the joint.</span></span>

<span data-ttu-id="97853-310">**PerceptionSimulation. SimulatedHandJointConfiguration. 旋轉**</span><span class="sxs-lookup"><span data-stu-id="97853-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="97853-311">聯合的旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-311">The rotation of the joint.</span></span>

<span data-ttu-id="97853-312">**PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="97853-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="97853-313">聯合的追蹤精確度。</span><span class="sxs-lookup"><span data-stu-id="97853-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="97853-314">PerceptionSimulation。</span><span class="sxs-lookup"><span data-stu-id="97853-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="97853-315">描述相機通常使用的視圖截圖。</span><span class="sxs-lookup"><span data-stu-id="97853-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="97853-316">**PerceptionSimulation。 Near**</span><span class="sxs-lookup"><span data-stu-id="97853-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="97853-317">以截距包含的最小距離。</span><span class="sxs-lookup"><span data-stu-id="97853-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="97853-318">**PerceptionSimulation....。**</span><span class="sxs-lookup"><span data-stu-id="97853-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="97853-319">以截距包含的最大距離。</span><span class="sxs-lookup"><span data-stu-id="97853-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="97853-320">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="97853-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="97853-321">截量的水準欄位，以弧度為單位（小於 PI）。</span><span class="sxs-lookup"><span data-stu-id="97853-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="97853-322">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="97853-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="97853-323">水準欄位和視圖垂直欄位的比例。</span><span class="sxs-lookup"><span data-stu-id="97853-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="97853-324">PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="97853-324">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="97853-325">說明模擬耳機顯示的設定。</span><span class="sxs-lookup"><span data-stu-id="97853-325">Describes the configuration of the simulated headset's display.</span></span>

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

<span data-ttu-id="97853-326">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="97853-326">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="97853-327">從開頭到左邊的轉換，以供身歷聲轉譯之用。</span><span class="sxs-lookup"><span data-stu-id="97853-327">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="97853-328">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="97853-328">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="97853-329">針對身歷聲轉譯的目的而左邊的旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-329">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="97853-330">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="97853-330">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="97853-331">從前端到右眼的轉換，以供身歷聲轉譯之用。</span><span class="sxs-lookup"><span data-stu-id="97853-331">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="97853-332">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="97853-332">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="97853-333">針對身歷聲轉譯的角度所做的調整。</span><span class="sxs-lookup"><span data-stu-id="97853-333">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="97853-334">**PerceptionSimulation. SimulatedDisplayConfiguration Ipd**</span><span class="sxs-lookup"><span data-stu-id="97853-334">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="97853-335">系統報告的 Ipd 值，用於呈現身歷聲轉譯。</span><span class="sxs-lookup"><span data-stu-id="97853-335">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="97853-336">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="97853-336">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="97853-337">針對 left 和 right 眼轉換提供的值是否應視為有效，並套用至執行中的系統。</span><span class="sxs-lookup"><span data-stu-id="97853-337">Whether or not the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="97853-338">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="97853-338">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="97853-339">是否應將為 Ipd 提供的值視為有效，並套用至執行中的系統。</span><span class="sxs-lookup"><span data-stu-id="97853-339">Whether or not the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="97853-340">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="97853-340">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="97853-341">用於產生用於控制裝置之封包的根目錄。</span><span class="sxs-lookup"><span data-stu-id="97853-341">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="97853-342">**PerceptionSimulation. IPerceptionSimulationManager. 裝置**</span><span class="sxs-lookup"><span data-stu-id="97853-342">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="97853-343">取出模擬的裝置物件，以解讀模擬的人和模擬世界。</span><span class="sxs-lookup"><span data-stu-id="97853-343">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="97853-344">**PerceptionSimulation. IPerceptionSimulationManager. 人類**</span><span class="sxs-lookup"><span data-stu-id="97853-344">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="97853-345">取得控制模擬人類的物件。</span><span class="sxs-lookup"><span data-stu-id="97853-345">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="97853-346">**PerceptionSimulation. IPerceptionSimulationManager. 重設**</span><span class="sxs-lookup"><span data-stu-id="97853-346">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="97853-347">將模擬重設為其預設狀態。</span><span class="sxs-lookup"><span data-stu-id="97853-347">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="97853-348">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="97853-348">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="97853-349">描述裝置的介面，其會解讀模擬世界和模擬的人類</span><span class="sxs-lookup"><span data-stu-id="97853-349">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="97853-350">**PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="97853-350">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="97853-351">從模擬裝置取出 Head 追蹤器。</span><span class="sxs-lookup"><span data-stu-id="97853-351">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="97853-352">**PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="97853-352">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="97853-353">從模擬的裝置抓取手追蹤器。</span><span class="sxs-lookup"><span data-stu-id="97853-353">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="97853-354">**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType （Microsoft PerceptionSimulation. SimulatedDeviceType）**</span><span class="sxs-lookup"><span data-stu-id="97853-354">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="97853-355">設定模擬裝置的屬性，以符合提供的裝置類型。</span><span class="sxs-lookup"><span data-stu-id="97853-355">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="97853-356">參數</span><span class="sxs-lookup"><span data-stu-id="97853-356">Parameters</span></span>
* <span data-ttu-id="97853-357">類型-模擬裝置的新類型</span><span class="sxs-lookup"><span data-stu-id="97853-357">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="97853-358">PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="97853-358">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="97853-359">藉由將 ISimulatedDevice 轉型為 ISimulatedDevice2，可以使用其他屬性。</span><span class="sxs-lookup"><span data-stu-id="97853-359">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="97853-360">**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="97853-360">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="97853-361">抓取或設定模擬的人是否積極戴頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="97853-361">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="97853-362">**PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="97853-362">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="97853-363">取出或設定模擬顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="97853-363">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="97853-364">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="97853-364">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="97853-365">描述模擬裝置之部分的介面，它會追蹤模擬人類的標頭。</span><span class="sxs-lookup"><span data-stu-id="97853-365">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="97853-366">**PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="97853-366">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="97853-367">抓取和設定目前的標頭追蹤器模式。</span><span class="sxs-lookup"><span data-stu-id="97853-367">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="97853-368">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="97853-368">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="97853-369">描述模擬裝置之部分的介面，可追蹤模擬人類的手</span><span class="sxs-lookup"><span data-stu-id="97853-369">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="97853-370">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="97853-370">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="97853-371">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="97853-371">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="97853-372">**PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="97853-372">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="97853-373">抓取和設定模擬的手勢追蹤器的位置（相對於 head 的中心）。</span><span class="sxs-lookup"><span data-stu-id="97853-373">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="97853-374">**PerceptionSimulation. ISimulatedHandTracker. 音調**</span><span class="sxs-lookup"><span data-stu-id="97853-374">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="97853-375">取出並設定模擬的手勢追蹤器的下音調。</span><span class="sxs-lookup"><span data-stu-id="97853-375">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="97853-376">**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="97853-376">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="97853-377">抓取和設定是否忽略模擬的手勢追蹤器的錐狀。</span><span class="sxs-lookup"><span data-stu-id="97853-377">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="97853-378">忽略時，一律會顯示這兩個手。</span><span class="sxs-lookup"><span data-stu-id="97853-378">When ignored, both hands are always visible.</span></span> <span data-ttu-id="97853-379">[未略過] （預設值）只會在手上的 [指標追蹤器] 中出現時才會顯示。</span><span class="sxs-lookup"><span data-stu-id="97853-379">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="97853-380">**PerceptionSimulation. ISimulatedHandTracker。**</span><span class="sxs-lookup"><span data-stu-id="97853-380">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="97853-381">抓取和設定用來判斷模擬的手追蹤器是否可以看見手的「截錐」屬性。</span><span class="sxs-lookup"><span data-stu-id="97853-381">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="97853-382">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="97853-382">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="97853-383">控制模擬人類的最上層介面。</span><span class="sxs-lookup"><span data-stu-id="97853-383">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="97853-384">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="97853-384">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="97853-385">抓取和設定與世界相關的節點位置（以量為單位）。</span><span class="sxs-lookup"><span data-stu-id="97853-385">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="97853-386">這個位置會對應到位於人類腳中心的點。</span><span class="sxs-lookup"><span data-stu-id="97853-386">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="97853-387">**PerceptionSimulation. ISimulatedHuman. 方向**</span><span class="sxs-lookup"><span data-stu-id="97853-387">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="97853-388">取得並設定世界中模擬的人臉方向。</span><span class="sxs-lookup"><span data-stu-id="97853-388">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="97853-389">0弧度會向下到負 Z 軸。</span><span class="sxs-lookup"><span data-stu-id="97853-389">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="97853-390">正弧度會順時針旋轉 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="97853-390">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="97853-391">**PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="97853-391">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="97853-392">抓取和設定模擬人的高度（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="97853-392">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="97853-393">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="97853-393">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="97853-394">取出模擬人類的左邊。</span><span class="sxs-lookup"><span data-stu-id="97853-394">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="97853-395">**PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="97853-395">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="97853-396">取得模擬人類的右手邊。</span><span class="sxs-lookup"><span data-stu-id="97853-396">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="97853-397">**PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="97853-397">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="97853-398">抓取模擬人類的標頭。</span><span class="sxs-lookup"><span data-stu-id="97853-398">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="97853-399">**PerceptionSimulation. ISimulatedHuman. Move （PerceptionSimulation. Vector3）**</span><span class="sxs-lookup"><span data-stu-id="97853-399">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="97853-400">將模擬人相對於其目前位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="97853-400">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="97853-401">參數</span><span class="sxs-lookup"><span data-stu-id="97853-401">Parameters</span></span>
* <span data-ttu-id="97853-402">轉譯-要移動的轉譯，相對於目前的位置。</span><span class="sxs-lookup"><span data-stu-id="97853-402">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="97853-403">**PerceptionSimulation. ISimulatedHuman. 旋轉（System.web）**</span><span class="sxs-lookup"><span data-stu-id="97853-403">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="97853-404">以順時針方向針對 Y 軸，將模擬的人類旋轉相對於其目前方向</span><span class="sxs-lookup"><span data-stu-id="97853-404">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="97853-405">參數</span><span class="sxs-lookup"><span data-stu-id="97853-405">Parameters</span></span>
* <span data-ttu-id="97853-406">弧度-要繞著 Y 軸旋轉的數量。</span><span class="sxs-lookup"><span data-stu-id="97853-406">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="97853-407">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="97853-407">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="97853-408">藉由將 ISimulatedHuman 轉型為 ISimulatedHuman2，可以使用其他屬性。</span><span class="sxs-lookup"><span data-stu-id="97853-408">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="97853-409">**PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="97853-409">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="97853-410">取出左邊的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="97853-410">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="97853-411">**PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="97853-411">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="97853-412">取出右6個 DOF 的控制器。</span><span class="sxs-lookup"><span data-stu-id="97853-412">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="97853-413">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="97853-413">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="97853-414">描述模擬人類之手的介面</span><span class="sxs-lookup"><span data-stu-id="97853-414">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="97853-415">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="97853-415">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="97853-416">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="97853-416">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="97853-417">**PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="97853-417">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="97853-418">抓取和設定相對於人類（以量為單位）的模擬手勢位置。</span><span class="sxs-lookup"><span data-stu-id="97853-418">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="97853-419">**PerceptionSimulation. ISimulatedHand. 已啟用**</span><span class="sxs-lookup"><span data-stu-id="97853-419">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="97853-420">抓取並設定是否目前已啟用手。</span><span class="sxs-lookup"><span data-stu-id="97853-420">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="97853-421">**PerceptionSimulation. ISimulatedHand. Visible**</span><span class="sxs-lookup"><span data-stu-id="97853-421">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="97853-422">抓取 SimulatedDevice 的目前是否可見（也就是它是否位於 HandTracker 所偵測到的位置）。</span><span class="sxs-lookup"><span data-stu-id="97853-422">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="97853-423">**PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="97853-423">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="97853-424">移動手，讓 SimulatedDevice 可以看到它。</span><span class="sxs-lookup"><span data-stu-id="97853-424">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="97853-425">**PerceptionSimulation. ISimulatedHand. Move （PerceptionSimulation. Vector3）**</span><span class="sxs-lookup"><span data-stu-id="97853-425">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="97853-426">移動模擬手相對於其目前位置的位置（以量為單位）。</span><span class="sxs-lookup"><span data-stu-id="97853-426">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="97853-427">參數</span><span class="sxs-lookup"><span data-stu-id="97853-427">Parameters</span></span>
* <span data-ttu-id="97853-428">轉譯-要轉譯模擬手的數量。</span><span class="sxs-lookup"><span data-stu-id="97853-428">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="97853-429">**PerceptionSimulation. ISimulatedHand. PerformGesture （Microsoft PerceptionSimulation. SimulatedGesture）**</span><span class="sxs-lookup"><span data-stu-id="97853-429">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="97853-430">使用模擬的手執行手勢。</span><span class="sxs-lookup"><span data-stu-id="97853-430">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="97853-431">只有在已啟用手時，系統才會偵測到此檔案。</span><span class="sxs-lookup"><span data-stu-id="97853-431">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="97853-432">參數</span><span class="sxs-lookup"><span data-stu-id="97853-432">Parameters</span></span>
* <span data-ttu-id="97853-433">手勢-要執行的手勢。</span><span class="sxs-lookup"><span data-stu-id="97853-433">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="97853-434">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="97853-434">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="97853-435">將 ISimulatedHand 轉換為 ISimulatedHand2 可使用其他屬性。</span><span class="sxs-lookup"><span data-stu-id="97853-435">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="97853-436">**PerceptionSimulation. ISimulatedHand2. 取向**</span><span class="sxs-lookup"><span data-stu-id="97853-436">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="97853-437">取出或設定模擬手的旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-437">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="97853-438">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-438">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="97853-439">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="97853-439">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="97853-440">將 ISimulatedHand 轉換為 ISimulatedHand3 可使用其他屬性</span><span class="sxs-lookup"><span data-stu-id="97853-440">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="97853-441">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="97853-441">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="97853-442">取得所指定聯合的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="97853-442">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="97853-443">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="97853-443">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="97853-444">設定所指定聯合的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="97853-444">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="97853-445">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="97853-445">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="97853-446">將手設定為已知的姿勢，並使用選擇性的旗標來製作動畫。</span><span class="sxs-lookup"><span data-stu-id="97853-446">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="97853-447">注意：動畫不會導致直接反映其最終的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="97853-447">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="97853-448">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="97853-448">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="97853-449">描述模擬人的頭的介面。</span><span class="sxs-lookup"><span data-stu-id="97853-449">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="97853-450">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="97853-450">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="97853-451">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="97853-451">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="97853-452">**PerceptionSimulation. ISimulatedHead. 旋轉**</span><span class="sxs-lookup"><span data-stu-id="97853-452">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="97853-453">取出模擬標頭的旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-453">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="97853-454">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-454">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="97853-455">**PerceptionSimulation. ISimulatedHead. 直徑**</span><span class="sxs-lookup"><span data-stu-id="97853-455">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="97853-456">取出模擬的標頭直徑。</span><span class="sxs-lookup"><span data-stu-id="97853-456">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="97853-457">這個值是用來判斷 head 的中心（旋轉點）。</span><span class="sxs-lookup"><span data-stu-id="97853-457">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="97853-458">**PerceptionSimulation. ISimulatedHead. 旋轉（PerceptionSimulation. Rotation3）**</span><span class="sxs-lookup"><span data-stu-id="97853-458">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="97853-459">將模擬的標頭旋轉成相對於目前的旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-459">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="97853-460">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-460">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="97853-461">參數</span><span class="sxs-lookup"><span data-stu-id="97853-461">Parameters</span></span>
* <span data-ttu-id="97853-462">旋轉-要旋轉的數量。</span><span class="sxs-lookup"><span data-stu-id="97853-462">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="97853-463">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="97853-463">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="97853-464">將 ISimulatedHead 轉換為 ISimulatedHead2 可使用其他屬性</span><span class="sxs-lookup"><span data-stu-id="97853-464">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="97853-465">**PerceptionSimulation. ISimulatedHead2 眼**</span><span class="sxs-lookup"><span data-stu-id="97853-465">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="97853-466">取出模擬人類的眼睛。</span><span class="sxs-lookup"><span data-stu-id="97853-466">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="97853-467">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="97853-467">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="97853-468">描述與模擬人類相關聯之 6 DOF 控制器的介面。</span><span class="sxs-lookup"><span data-stu-id="97853-468">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="97853-469">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="97853-469">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="97853-470">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="97853-470">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="97853-471">**PerceptionSimulation. ISimulatedSixDofController. 狀態**</span><span class="sxs-lookup"><span data-stu-id="97853-471">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="97853-472">取得或設定控制器的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="97853-472">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="97853-473">控制器狀態必須設定為 [關閉] 以外的值，才能進行移動、旋轉或按下按鈕的任何呼叫。</span><span class="sxs-lookup"><span data-stu-id="97853-473">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="97853-474">**PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="97853-474">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="97853-475">抓取或設定模擬控制器相對於人類的位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="97853-475">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="97853-476">**PerceptionSimulation. ISimulatedSixDofController. 取向**</span><span class="sxs-lookup"><span data-stu-id="97853-476">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="97853-477">取得或設定模擬控制器的方向。</span><span class="sxs-lookup"><span data-stu-id="97853-477">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="97853-478">**PerceptionSimulation. ISimulatedSixDofController. Move （PerceptionSimulation. Vector3）**</span><span class="sxs-lookup"><span data-stu-id="97853-478">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="97853-479">移動模擬控制器相對於其目前位置的位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="97853-479">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="97853-480">參數</span><span class="sxs-lookup"><span data-stu-id="97853-480">Parameters</span></span>
* <span data-ttu-id="97853-481">轉譯-要轉譯模擬控制器的數量。</span><span class="sxs-lookup"><span data-stu-id="97853-481">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="97853-482">**PerceptionSimulation. ISimulatedSixDofController. PressButton （SimulatedSixDofControllerButton）**</span><span class="sxs-lookup"><span data-stu-id="97853-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="97853-483">在模擬控制器上按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="97853-483">Press a button on the simulated controller.</span></span>  <span data-ttu-id="97853-484">只有在已啟用控制器的情況下，系統才會偵測到它。</span><span class="sxs-lookup"><span data-stu-id="97853-484">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="97853-485">參數</span><span class="sxs-lookup"><span data-stu-id="97853-485">Parameters</span></span>
* <span data-ttu-id="97853-486">按鈕-要按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="97853-486">button - The button to press.</span></span>

<span data-ttu-id="97853-487">**PerceptionSimulation. ISimulatedSixDofController. ReleaseButton （SimulatedSixDofControllerButton）**</span><span class="sxs-lookup"><span data-stu-id="97853-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="97853-488">釋放模擬控制器上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="97853-488">Release a button on the simulated controller.</span></span>  <span data-ttu-id="97853-489">只有在已啟用控制器的情況下，系統才會偵測到它。</span><span class="sxs-lookup"><span data-stu-id="97853-489">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="97853-490">參數</span><span class="sxs-lookup"><span data-stu-id="97853-490">Parameters</span></span>
* <span data-ttu-id="97853-491">按鈕-要發行的按鈕。</span><span class="sxs-lookup"><span data-stu-id="97853-491">button - The button to release.</span></span>

<span data-ttu-id="97853-492">**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition （out float，out float）**</span><span class="sxs-lookup"><span data-stu-id="97853-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="97853-493">取得模擬控制器的觸控板上的模擬手指位置。</span><span class="sxs-lookup"><span data-stu-id="97853-493">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="97853-494">參數</span><span class="sxs-lookup"><span data-stu-id="97853-494">Parameters</span></span>
* <span data-ttu-id="97853-495">x-手指的水準位置。</span><span class="sxs-lookup"><span data-stu-id="97853-495">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="97853-496">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="97853-496">y - The vertical position of the finger.</span></span>

<span data-ttu-id="97853-497">**PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition （float，float）**</span><span class="sxs-lookup"><span data-stu-id="97853-497">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="97853-498">將模擬手指的位置設定在模擬控制器的觸控板上。</span><span class="sxs-lookup"><span data-stu-id="97853-498">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="97853-499">參數</span><span class="sxs-lookup"><span data-stu-id="97853-499">Parameters</span></span>
* <span data-ttu-id="97853-500">x-手指的水準位置。</span><span class="sxs-lookup"><span data-stu-id="97853-500">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="97853-501">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="97853-501">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="97853-502">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="97853-502">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="97853-503">將 ISimulatedSixDofController 轉換為 ISimulatedSixDofController2 可使用其他屬性和方法</span><span class="sxs-lookup"><span data-stu-id="97853-503">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="97853-504">**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition （out float，out float）**</span><span class="sxs-lookup"><span data-stu-id="97853-504">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="97853-505">取得模擬控制站上模擬的操縱杆位置。</span><span class="sxs-lookup"><span data-stu-id="97853-505">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="97853-506">參數</span><span class="sxs-lookup"><span data-stu-id="97853-506">Parameters</span></span>
* <span data-ttu-id="97853-507">x-操縱杆的水準位置。</span><span class="sxs-lookup"><span data-stu-id="97853-507">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="97853-508">y-操縱杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="97853-508">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="97853-509">**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition （float，float）**</span><span class="sxs-lookup"><span data-stu-id="97853-509">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="97853-510">在模擬的控制器上設定模擬的操縱杆位置。</span><span class="sxs-lookup"><span data-stu-id="97853-510">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="97853-511">參數</span><span class="sxs-lookup"><span data-stu-id="97853-511">Parameters</span></span>
* <span data-ttu-id="97853-512">x-操縱杆的水準位置。</span><span class="sxs-lookup"><span data-stu-id="97853-512">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="97853-513">y-操縱杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="97853-513">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="97853-514">**PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="97853-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="97853-515">取出或設定模擬控制器的電池計量。</span><span class="sxs-lookup"><span data-stu-id="97853-515">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="97853-516">此值必須大於0.0 且小於或等於100.0。</span><span class="sxs-lookup"><span data-stu-id="97853-516">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="97853-517">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="97853-517">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="97853-518">描述模擬人眼的介面。</span><span class="sxs-lookup"><span data-stu-id="97853-518">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="97853-519">**PerceptionSimulation. ISimulatedEyes. 旋轉**</span><span class="sxs-lookup"><span data-stu-id="97853-519">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="97853-520">取出模擬眼睛的旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-520">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="97853-521">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-521">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="97853-522">**PerceptionSimulation. ISimulatedEyes. 旋轉（PerceptionSimulation. Rotation3）**</span><span class="sxs-lookup"><span data-stu-id="97853-522">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="97853-523">旋轉模擬的眼睛，相對於其目前的旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-523">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="97853-524">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="97853-524">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="97853-525">參數</span><span class="sxs-lookup"><span data-stu-id="97853-525">Parameters</span></span>
* <span data-ttu-id="97853-526">旋轉-要旋轉的數量。</span><span class="sxs-lookup"><span data-stu-id="97853-526">rotation - The amount to rotate.</span></span>

<span data-ttu-id="97853-527">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="97853-527">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="97853-528">抓取或設定模擬眼睛的校正狀態。</span><span class="sxs-lookup"><span data-stu-id="97853-528">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="97853-529">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="97853-529">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="97853-530">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="97853-530">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="97853-531">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="97853-531">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="97853-532">介面，用於與已載入播放的單一錄製進行互動。</span><span class="sxs-lookup"><span data-stu-id="97853-532">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="97853-533">**PerceptionSimulation. ISimulationRecording 資料類型**</span><span class="sxs-lookup"><span data-stu-id="97853-533">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="97853-534">抓取記錄中的資料類型清單。</span><span class="sxs-lookup"><span data-stu-id="97853-534">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="97853-535">**PerceptionSimulation. ISimulationRecording. 州/省**</span><span class="sxs-lookup"><span data-stu-id="97853-535">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="97853-536">抓取錄影的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="97853-536">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="97853-537">**PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="97853-537">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="97853-538">開始播放。</span><span class="sxs-lookup"><span data-stu-id="97853-538">Start the playback.</span></span> <span data-ttu-id="97853-539">如果記錄已暫停，播放將會從暫停的位置繼續執行;如果已停止，播放會從一開始開始。</span><span class="sxs-lookup"><span data-stu-id="97853-539">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="97853-540">如果已經在播放，則會忽略此呼叫。</span><span class="sxs-lookup"><span data-stu-id="97853-540">If already playing, this call is ignored.</span></span>

<span data-ttu-id="97853-541">**PerceptionSimulation. ISimulationRecording. Pause**</span><span class="sxs-lookup"><span data-stu-id="97853-541">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="97853-542">暫停播放目前的位置。</span><span class="sxs-lookup"><span data-stu-id="97853-542">Pauses the playback at its current location.</span></span> <span data-ttu-id="97853-543">如果記錄已停止，則會忽略呼叫。</span><span class="sxs-lookup"><span data-stu-id="97853-543">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="97853-544">**PerceptionSimulation. ISimulationRecording. Seek （System.object）**</span><span class="sxs-lookup"><span data-stu-id="97853-544">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="97853-545">將記錄搜尋到指定的時間（從一開始的100毫微秒間隔），並在該位置暫停。</span><span class="sxs-lookup"><span data-stu-id="97853-545">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="97853-546">如果時間超過錄製的結尾，則會在最後一個畫面上暫停。</span><span class="sxs-lookup"><span data-stu-id="97853-546">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="97853-547">參數</span><span class="sxs-lookup"><span data-stu-id="97853-547">Parameters</span></span>
* <span data-ttu-id="97853-548">刻度-要搜尋的時間。</span><span class="sxs-lookup"><span data-stu-id="97853-548">ticks - The time to which to seek.</span></span>

<span data-ttu-id="97853-549">**PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="97853-549">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="97853-550">停止播放，並將位置重設為開頭。</span><span class="sxs-lookup"><span data-stu-id="97853-550">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="97853-551">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="97853-551">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="97853-552">用於在播放期間接收狀態變更的介面。</span><span class="sxs-lookup"><span data-stu-id="97853-552">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="97853-553">**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged （Microsoft PerceptionSimulation. PlaybackState）**</span><span class="sxs-lookup"><span data-stu-id="97853-553">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="97853-554">當 ISimulationRecording 的播放狀態變更時呼叫。</span><span class="sxs-lookup"><span data-stu-id="97853-554">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="97853-555">參數</span><span class="sxs-lookup"><span data-stu-id="97853-555">Parameters</span></span>
* <span data-ttu-id="97853-556">newState-記錄的新狀態。</span><span class="sxs-lookup"><span data-stu-id="97853-556">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="97853-557">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="97853-557">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="97853-558">用來建立認知模擬物件的根物件。</span><span class="sxs-lookup"><span data-stu-id="97853-558">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="97853-559">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager （Microsoft PerceptionSimulation. ISimulationStreamSink）**</span><span class="sxs-lookup"><span data-stu-id="97853-559">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="97853-560">在物件上建立以產生模擬封包，並將它們傳遞至提供的接收。</span><span class="sxs-lookup"><span data-stu-id="97853-560">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="97853-561">參數</span><span class="sxs-lookup"><span data-stu-id="97853-561">Parameters</span></span>
* <span data-ttu-id="97853-562">sink-接收所有產生的封包的接收器。</span><span class="sxs-lookup"><span data-stu-id="97853-562">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="97853-563">傳回值</span><span class="sxs-lookup"><span data-stu-id="97853-563">Return value</span></span>

<span data-ttu-id="97853-564">建立的管理員。</span><span class="sxs-lookup"><span data-stu-id="97853-564">The created Manager.</span></span>

<span data-ttu-id="97853-565">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording （System.string）**</span><span class="sxs-lookup"><span data-stu-id="97853-565">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="97853-566">建立接收，將所有接收的封包儲存在檔案中的指定路徑。</span><span class="sxs-lookup"><span data-stu-id="97853-566">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="97853-567">參數</span><span class="sxs-lookup"><span data-stu-id="97853-567">Parameters</span></span>
* <span data-ttu-id="97853-568">path-要建立之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="97853-568">path - The path of the file to create.</span></span>

<span data-ttu-id="97853-569">傳回值</span><span class="sxs-lookup"><span data-stu-id="97853-569">Return value</span></span>

<span data-ttu-id="97853-570">建立的接收。</span><span class="sxs-lookup"><span data-stu-id="97853-570">The created sink.</span></span>

<span data-ttu-id="97853-571">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording （System.string，Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory）**</span><span class="sxs-lookup"><span data-stu-id="97853-571">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="97853-572">從指定的檔案載入記錄。</span><span class="sxs-lookup"><span data-stu-id="97853-572">Load a recording from the specified file.</span></span>

<span data-ttu-id="97853-573">參數</span><span class="sxs-lookup"><span data-stu-id="97853-573">Parameters</span></span>
* <span data-ttu-id="97853-574">path-要載入的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="97853-574">path - The path of the file to load.</span></span>
* <span data-ttu-id="97853-575">factory-記錄在需要時用來建立 ISimulationStreamSink 的 factory。</span><span class="sxs-lookup"><span data-stu-id="97853-575">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="97853-576">傳回值</span><span class="sxs-lookup"><span data-stu-id="97853-576">Return value</span></span>

<span data-ttu-id="97853-577">載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="97853-577">The loaded recording.</span></span>

<span data-ttu-id="97853-578">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording （System.string，microsoft. PerceptionSimulation. ISimulationStreamSinkFactory，PerceptionSimulation）**</span><span class="sxs-lookup"><span data-stu-id="97853-578">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="97853-579">從指定的檔案載入記錄。</span><span class="sxs-lookup"><span data-stu-id="97853-579">Load a recording from the specified file.</span></span>

<span data-ttu-id="97853-580">參數</span><span class="sxs-lookup"><span data-stu-id="97853-580">Parameters</span></span>
* <span data-ttu-id="97853-581">path-要載入的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="97853-581">path - The path of the file to load.</span></span>
* <span data-ttu-id="97853-582">factory-記錄在需要時用來建立 ISimulationStreamSink 的 factory。</span><span class="sxs-lookup"><span data-stu-id="97853-582">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="97853-583">回呼-接收更新的回呼會 regrading 記錄的狀態。</span><span class="sxs-lookup"><span data-stu-id="97853-583">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="97853-584">傳回值</span><span class="sxs-lookup"><span data-stu-id="97853-584">Return value</span></span>

<span data-ttu-id="97853-585">載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="97853-585">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="97853-586">PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="97853-586">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="97853-587">描述不同類型的資料流程資料。</span><span class="sxs-lookup"><span data-stu-id="97853-587">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="97853-588">**PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="97853-588">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="97853-589">用來表示沒有資料流程資料類型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="97853-589">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="97853-590">**PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="97853-590">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="97853-591">關於 head 位置和方向的資料流程。</span><span class="sxs-lookup"><span data-stu-id="97853-591">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="97853-592">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="97853-592">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="97853-593">關於手的位置和手勢的資料流程。</span><span class="sxs-lookup"><span data-stu-id="97853-593">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="97853-594">**PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="97853-594">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="97853-595">關於環境的空間對應的資料流程。</span><span class="sxs-lookup"><span data-stu-id="97853-595">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="97853-596">**PerceptionSimulation. StreamDataTypes. 校正**</span><span class="sxs-lookup"><span data-stu-id="97853-596">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="97853-597">關於裝置校正的資料流程。</span><span class="sxs-lookup"><span data-stu-id="97853-597">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="97853-598">只有在遠端模式中的系統才會接受校正封包。</span><span class="sxs-lookup"><span data-stu-id="97853-598">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="97853-599">**PerceptionSimulation. StreamDataTypes. 環境**</span><span class="sxs-lookup"><span data-stu-id="97853-599">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="97853-600">關於裝置環境的資料流程。</span><span class="sxs-lookup"><span data-stu-id="97853-600">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="97853-601">**PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="97853-601">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="97853-602">有關動作控制器的資料流程。</span><span class="sxs-lookup"><span data-stu-id="97853-602">Stream of data regarding motion controllers.</span></span>

<span data-ttu-id="97853-603">**PerceptionSimulation. StreamDataTypes 眼**</span><span class="sxs-lookup"><span data-stu-id="97853-603">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="97853-604">關於模擬人類眼的資料流程。</span><span class="sxs-lookup"><span data-stu-id="97853-604">Stream of data regarding the eyes of the simulated human.</span></span>

<span data-ttu-id="97853-605">**PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="97853-605">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="97853-606">關於裝置顯示設定的資料流程。</span><span class="sxs-lookup"><span data-stu-id="97853-606">Stream of data regarding the display configuration of the device.</span></span>

<span data-ttu-id="97853-607">**PerceptionSimulation. StreamDataTypes. 全部**</span><span class="sxs-lookup"><span data-stu-id="97853-607">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="97853-608">用來表示所有記錄資料類型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="97853-608">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="97853-609">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="97853-609">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="97853-610">物件，接收來自模擬資料流程的資料封包。</span><span class="sxs-lookup"><span data-stu-id="97853-610">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="97853-611">**PerceptionSimulation. ISimulationStreamSink. OnPacketReceived （uint length，byte [] 封包）**</span><span class="sxs-lookup"><span data-stu-id="97853-611">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="97853-612">接收單一封包，其為內部輸入和版本設定。</span><span class="sxs-lookup"><span data-stu-id="97853-612">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="97853-613">參數</span><span class="sxs-lookup"><span data-stu-id="97853-613">Parameters</span></span>
* <span data-ttu-id="97853-614">length-封包的長度。</span><span class="sxs-lookup"><span data-stu-id="97853-614">length - The length of the packet.</span></span>
* <span data-ttu-id="97853-615">封包-封包的資料。</span><span class="sxs-lookup"><span data-stu-id="97853-615">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="97853-616">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="97853-616">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="97853-617">建立 ISimulationStreamSink 的物件。</span><span class="sxs-lookup"><span data-stu-id="97853-617">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="97853-618">**PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink （）**</span><span class="sxs-lookup"><span data-stu-id="97853-618">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="97853-619">建立 ISimulationStreamSink 的單一實例。</span><span class="sxs-lookup"><span data-stu-id="97853-619">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="97853-620">傳回值</span><span class="sxs-lookup"><span data-stu-id="97853-620">Return value</span></span>

<span data-ttu-id="97853-621">建立的接收。</span><span class="sxs-lookup"><span data-stu-id="97853-621">The created sink.</span></span>
