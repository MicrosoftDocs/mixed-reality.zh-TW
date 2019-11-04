---
title: 認知模擬
description: 使用認知模擬程式庫將沉浸式應用程式的模擬輸入自動化的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens、模擬、測試
ms.openlocfilehash: 503533bc5a2e9307b7c5217632d42670285aac0a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437543"
---
# <a name="perception-simulation"></a><span data-ttu-id="084d5-104">認知模擬</span><span class="sxs-lookup"><span data-stu-id="084d5-104">Perception simulation</span></span>

<span data-ttu-id="084d5-105">您要為您的應用程式建立自動化測試嗎？</span><span class="sxs-lookup"><span data-stu-id="084d5-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="084d5-106">您是否想要讓測試超越元件層級的單元測試，並確實執行應用程式端對端？</span><span class="sxs-lookup"><span data-stu-id="084d5-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="084d5-107">認知模擬是您要尋找的。</span><span class="sxs-lookup"><span data-stu-id="084d5-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="084d5-108">認知模擬程式庫會將人類和世界的輸入資料傳送至您的應用程式，讓您可以自動化測試。</span><span class="sxs-lookup"><span data-stu-id="084d5-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="084d5-109">例如，您可以模擬人類的輸入，尋找特定、可重複的位置，然後執行手勢或使用動作控制器。</span><span class="sxs-lookup"><span data-stu-id="084d5-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="084d5-110">認知模擬可以將這類模擬的輸入傳送至實體 HoloLens、HoloLens 模擬器（第一代）、HoloLens 2 模擬器，或已安裝混合 Reality 入口網站的電腦。</span><span class="sxs-lookup"><span data-stu-id="084d5-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="084d5-111">認知模擬會略過混合現實裝置上的即時感應器，並將模擬的輸入傳送至裝置上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="084d5-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="084d5-112">應用程式會透過他們一律使用的相同 Api 來接收這些輸入事件，而且無法分辨實際感應器的執行與使用認知模擬的執行之間的差異。</span><span class="sxs-lookup"><span data-stu-id="084d5-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="084d5-113">認知模擬是 HoloLens 模擬器用來將模擬輸入傳送至 HoloLens 虛擬機器的相同技術。</span><span class="sxs-lookup"><span data-stu-id="084d5-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="084d5-114">若要開始在程式碼中使用模擬，請先建立 IPerceptionSimulationManager 物件。</span><span class="sxs-lookup"><span data-stu-id="084d5-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="084d5-115">您可以從該物件發出命令，以控制模擬「人」的屬性，包括頭部位置、手位置和手勢，而且您可以啟用和操作動作控制器。</span><span class="sxs-lookup"><span data-stu-id="084d5-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="084d5-116">設定認知模擬的 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="084d5-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="084d5-117">在開發電腦上[安裝 HoloLens 模擬器](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="084d5-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="084d5-118">模擬器包含您將用於認知模擬的程式庫。</span><span class="sxs-lookup"><span data-stu-id="084d5-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="084d5-119">建立新的 Visual Studio C#桌面專案（主控台專案非常適合用來開始使用）。</span><span class="sxs-lookup"><span data-stu-id="084d5-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="084d5-120">將下列二進位檔新增至您的專案做為參考（專案 > 的 [加入 > 參考 ...]）。您可以在% ProgramFiles （x86）% \ Microsoft XDE\\（版本）中找到它們，例如適用于 HoloLens 2 模擬器的 **% ProgramFiles （x86）% \ MICROSOFT XDE\\10.0.18362.0** 。</span><span class="sxs-lookup"><span data-stu-id="084d5-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="084d5-121">（注意：雖然二進位檔是 HoloLens 2 模擬器的一部分，但它們也適用于桌上型電腦上的 Windows Mixed Reality）。為.</span><span class="sxs-lookup"><span data-stu-id="084d5-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="084d5-122">PerceptionSimulationManager 感知模擬的 Managed C#包裝函式。</span><span class="sxs-lookup"><span data-stu-id="084d5-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="084d5-123">b。</span><span class="sxs-lookup"><span data-stu-id="084d5-123">b.</span></span> <span data-ttu-id="084d5-124">PerceptionSimulationRest：用於設定 HoloLens 或模擬器之 web 通訊端通道的程式庫。</span><span class="sxs-lookup"><span data-stu-id="084d5-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="084d5-125">c.</span><span class="sxs-lookup"><span data-stu-id="084d5-125">c.</span></span> <span data-ttu-id="084d5-126">SimulationStream：模擬的共用類型。</span><span class="sxs-lookup"><span data-stu-id="084d5-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="084d5-127">將 [執行二進位 PerceptionSimulationManager] 加入至您的專案 a。</span><span class="sxs-lookup"><span data-stu-id="084d5-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="084d5-128">首先，將它當做二進位檔新增至專案（專案 > [加入 > 現有專案 ...]）。將它儲存為連結，讓它不會將它複製到您的專案源資料夾。</span><span class="sxs-lookup"><span data-stu-id="084d5-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="084d5-129">![將 PerceptionSimulationManager 新增至專案，做為連結](images/saveaslink.png) b。</span><span class="sxs-lookup"><span data-stu-id="084d5-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="084d5-130">然後，確定它已複製到組建上的輸出檔案夾。</span><span class="sxs-lookup"><span data-stu-id="084d5-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="084d5-131">這是在二進位檔的屬性工作表中。</span><span class="sxs-lookup"><span data-stu-id="084d5-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="084d5-132">![將 PerceptionSimulationManager 標記為複製到輸出目錄](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="084d5-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="084d5-133">將使用中的方案平臺設定為 x64。</span><span class="sxs-lookup"><span data-stu-id="084d5-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="084d5-134">（如果不存在，請使用 Configuration Manager 來建立 x64 的平臺專案）。</span><span class="sxs-lookup"><span data-stu-id="084d5-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="084d5-135">建立 IPerceptionSimulation Manager 物件</span><span class="sxs-lookup"><span data-stu-id="084d5-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="084d5-136">若要控制模擬，您會對從 IPerceptionSimulationManager 物件取得的物件發出更新。</span><span class="sxs-lookup"><span data-stu-id="084d5-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="084d5-137">第一個步驟是取得該物件，並將它連接到您的目標裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="084d5-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="084d5-138">您可以按一下[工具列](using-the-hololens-emulator.md)中的 [裝置入口網站] 按鈕，以取得您的模擬器的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="084d5-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="084d5-139">![開啟裝置入口網站 圖示](images/emulator-deviceportal.png)**開啟 [裝置入口網站**]：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="084d5-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="084d5-140">對於 Windows Mixed Reality，可以在 [更新 & 安全性] 底下的 [設定] 應用程式中抓取，然後在 [啟用裝置入口網站] 底下的 [使用下列方式連線] 區段中，找到 [適用于開發人員]。</span><span class="sxs-lookup"><span data-stu-id="084d5-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="084d5-141">請務必記下 IP 位址和埠。</span><span class="sxs-lookup"><span data-stu-id="084d5-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="084d5-142">首先，您會呼叫 RestSimulationStreamSink 來取得 RestSimulationStreamSink 物件。</span><span class="sxs-lookup"><span data-stu-id="084d5-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="084d5-143">這是您將透過 HTTP 連接控制的目標裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="084d5-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="084d5-144">您的命令將會傳遞至裝置或模擬器上執行的[Windows 裝置入口網站](using-the-windows-device-portal.md)並加以處理。</span><span class="sxs-lookup"><span data-stu-id="084d5-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="084d5-145">建立物件所需的四個參數如下：</span><span class="sxs-lookup"><span data-stu-id="084d5-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="084d5-146">Uri uri-目標裝置的 IP 位址（例如，"https://123.123.123.123" 或 "https://123.123.123.123:50080"）</span><span class="sxs-lookup"><span data-stu-id="084d5-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="084d5-147">NetworkCredential 認證-使用者名稱/密碼，用於連接至目標裝置或模擬器上的[Windows 裝置入口網站](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="084d5-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="084d5-148">如果您是透過本機位址連接到模擬器（例如，*168 ...* \*）在同一部電腦上，將會接受任何認證。</span><span class="sxs-lookup"><span data-stu-id="084d5-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="084d5-149">一般優先權為 bool 標準-True，低優先順序為 false。</span><span class="sxs-lookup"><span data-stu-id="084d5-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="084d5-150">在測試案例中，您通常會想要將此設定為*true* ，讓您的測試能夠取得控制權。</span><span class="sxs-lookup"><span data-stu-id="084d5-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="084d5-151">模擬器和 Windows Mixed Reality 模擬會使用低優先順序的連接。</span><span class="sxs-lookup"><span data-stu-id="084d5-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="084d5-152">如果您的測試也使用低優先順序的連接，最近建立的連接將會受到控制。</span><span class="sxs-lookup"><span data-stu-id="084d5-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="084d5-153">CancellationToken token-用來取消非同步作業的 Token。</span><span class="sxs-lookup"><span data-stu-id="084d5-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="084d5-154">第二，您將建立 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="084d5-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="084d5-155">這是您用來控制模擬的物件。</span><span class="sxs-lookup"><span data-stu-id="084d5-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="084d5-156">請注意，這也必須在非同步方法中完成。</span><span class="sxs-lookup"><span data-stu-id="084d5-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="084d5-157">控制模擬的人類</span><span class="sxs-lookup"><span data-stu-id="084d5-157">Control the simulated Human</span></span>

<span data-ttu-id="084d5-158">IPerceptionSimulationManager 具有可傳回 ISimulatedHuman 物件的人類屬性。</span><span class="sxs-lookup"><span data-stu-id="084d5-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="084d5-159">若要控制模擬的人力，請在此物件上執行作業。</span><span class="sxs-lookup"><span data-stu-id="084d5-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="084d5-160">例如：</span><span class="sxs-lookup"><span data-stu-id="084d5-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="084d5-161">基本範例C#主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="084d5-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="084d5-162">擴充的C#範例主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="084d5-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="084d5-163">6 DOF 控制器上的附注</span><span class="sxs-lookup"><span data-stu-id="084d5-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="084d5-164">在模擬的 6 DOF 控制器上呼叫方法的任何屬性之前，您必須啟動控制器。</span><span class="sxs-lookup"><span data-stu-id="084d5-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="084d5-165">不這樣做會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="084d5-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="084d5-166">從 Windows 10 5 月2019更新開始，可以藉由將 ISimulatedSixDofController 物件上的 Status 屬性設為 SimulatedSixDofControllerStatus，來安裝和啟動模擬的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="084d5-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="084d5-167">在 Windows 10 2018 年10月更新和較舊版本中，您必須先呼叫位於 \Windows\System32 資料夾中的 PerceptionSimulationDevice 工具，分別安裝模擬的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="084d5-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="084d5-168">此工具的使用方式如下：</span><span class="sxs-lookup"><span data-stu-id="084d5-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="084d5-169">例如</span><span class="sxs-lookup"><span data-stu-id="084d5-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="084d5-170">支援的動作包括：</span><span class="sxs-lookup"><span data-stu-id="084d5-170">Supported actions are:</span></span>
* <span data-ttu-id="084d5-171">i = 安裝</span><span class="sxs-lookup"><span data-stu-id="084d5-171">i = install</span></span>
* <span data-ttu-id="084d5-172">q = 查詢</span><span class="sxs-lookup"><span data-stu-id="084d5-172">q = query</span></span>
* <span data-ttu-id="084d5-173">r = 移除</span><span class="sxs-lookup"><span data-stu-id="084d5-173">r = remove</span></span>

<span data-ttu-id="084d5-174">支援的實例包括：</span><span class="sxs-lookup"><span data-stu-id="084d5-174">Supported instances are:</span></span>
* <span data-ttu-id="084d5-175">1 = 左 6 DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="084d5-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="084d5-176">2 = 右方的 6 DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="084d5-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="084d5-177">進程的結束代碼會指出成功（零傳回值）或失敗（非零的傳回值）。</span><span class="sxs-lookup"><span data-stu-id="084d5-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="084d5-178">使用「q」動作來查詢是否已安裝控制器時，如果控制器尚未安裝，則傳回值會是零（0），如果已安裝控制器，則傳回一個（1）。</span><span class="sxs-lookup"><span data-stu-id="084d5-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="084d5-179">移除 Windows 10 2018 年10月更新或更早版本上的控制器時，請先透過 API 將其狀態設定為 Off，然後再呼叫 PerceptionSimulationDevice 工具。</span><span class="sxs-lookup"><span data-stu-id="084d5-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="084d5-180">請注意，此工具必須以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="084d5-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="084d5-181">API 參考資料</span><span class="sxs-lookup"><span data-stu-id="084d5-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="084d5-182">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="084d5-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="084d5-183">描述模擬裝置類型</span><span class="sxs-lookup"><span data-stu-id="084d5-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="084d5-184">**PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="084d5-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="084d5-185">虛構的參考設備，這是 PerceptionSimulationManager 的預設值</span><span class="sxs-lookup"><span data-stu-id="084d5-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="084d5-186">PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="084d5-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="084d5-187">描述 head 追蹤器模式</span><span class="sxs-lookup"><span data-stu-id="084d5-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="084d5-188">**PerceptionSimulation. HeadTrackerMode. Default**</span><span class="sxs-lookup"><span data-stu-id="084d5-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="084d5-189">預設的標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="084d5-189">Default Head Tracking.</span></span> <span data-ttu-id="084d5-190">這表示系統可能會根據執行時間條件來選取最佳的標頭追蹤模式。</span><span class="sxs-lookup"><span data-stu-id="084d5-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="084d5-191">**PerceptionSimulation. HeadTrackerMode. 取向**</span><span class="sxs-lookup"><span data-stu-id="084d5-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="084d5-192">僅限方向的頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="084d5-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="084d5-193">這表示追蹤的位置可能不可靠，而且某些相依于 head 位置的功能可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="084d5-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="084d5-194">**PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="084d5-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="084d5-195">位置標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="084d5-195">Positional Head Tracking.</span></span> <span data-ttu-id="084d5-196">這表示追蹤的標頭位置和方向都是可靠的</span><span class="sxs-lookup"><span data-stu-id="084d5-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="084d5-197">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="084d5-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="084d5-198">描述模擬的手勢</span><span class="sxs-lookup"><span data-stu-id="084d5-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="084d5-199">**PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="084d5-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="084d5-200">用來表示沒有手勢的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="084d5-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="084d5-201">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="084d5-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="084d5-202">按手指的手勢。</span><span class="sxs-lookup"><span data-stu-id="084d5-202">A finger pressed gesture.</span></span>

<span data-ttu-id="084d5-203">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="084d5-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="084d5-204">手指已釋放手勢。</span><span class="sxs-lookup"><span data-stu-id="084d5-204">A finger released gesture.</span></span>

<span data-ttu-id="084d5-205">**PerceptionSimulation. SimulatedGesture 首頁**</span><span class="sxs-lookup"><span data-stu-id="084d5-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="084d5-206">Home/system 手勢。</span><span class="sxs-lookup"><span data-stu-id="084d5-206">The home/system gesture.</span></span>

<span data-ttu-id="084d5-207">**PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="084d5-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="084d5-208">有效手勢的最大值。</span><span class="sxs-lookup"><span data-stu-id="084d5-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="084d5-209">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="084d5-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="084d5-210">模擬的 6 DOF 控制器的可能狀態。</span><span class="sxs-lookup"><span data-stu-id="084d5-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="084d5-211">**PerceptionSimulation. SimulatedSixDofControllerStatus. Off**</span><span class="sxs-lookup"><span data-stu-id="084d5-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="084d5-212">6 DOF 控制器已關閉。</span><span class="sxs-lookup"><span data-stu-id="084d5-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="084d5-213">**PerceptionSimulation. SimulatedSixDofControllerStatus. Active**</span><span class="sxs-lookup"><span data-stu-id="084d5-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="084d5-214">已開啟並追蹤 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="084d5-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="084d5-215">**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="084d5-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="084d5-216">已開啟6個 DOF 控制器，但無法加以追蹤。</span><span class="sxs-lookup"><span data-stu-id="084d5-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="084d5-217">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="084d5-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="084d5-218">模擬的 6 DOF 控制器上支援的按鈕。</span><span class="sxs-lookup"><span data-stu-id="084d5-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="084d5-219">**PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="084d5-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="084d5-220">用來表示沒有按鈕的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="084d5-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="084d5-221">**PerceptionSimulation. SimulatedSixDofControllerButton 首頁**</span><span class="sxs-lookup"><span data-stu-id="084d5-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="084d5-222">[首頁] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="084d5-222">The Home button is pressed.</span></span>

<span data-ttu-id="084d5-223">**PerceptionSimulation. SimulatedSixDofControllerButton. 功能表**</span><span class="sxs-lookup"><span data-stu-id="084d5-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="084d5-224">[功能表] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="084d5-224">The Menu button is pressed.</span></span>

<span data-ttu-id="084d5-225">**PerceptionSimulation. SimulatedSixDofControllerButton. 抓握**</span><span class="sxs-lookup"><span data-stu-id="084d5-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="084d5-226">[抓握] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="084d5-226">The Grip button is pressed.</span></span>

<span data-ttu-id="084d5-227">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="084d5-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="084d5-228">觸控板已按下。</span><span class="sxs-lookup"><span data-stu-id="084d5-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="084d5-229">**PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="084d5-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="084d5-230">[選取] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="084d5-230">The Select button is pressed.</span></span>

<span data-ttu-id="084d5-231">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="084d5-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="084d5-232">觸控板觸及。</span><span class="sxs-lookup"><span data-stu-id="084d5-232">The TouchPad is touched.</span></span>

<span data-ttu-id="084d5-233">**PerceptionSimulation. SimulatedSixDofControllerButton. 操縱杆**</span><span class="sxs-lookup"><span data-stu-id="084d5-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="084d5-234">操縱杆已按下。</span><span class="sxs-lookup"><span data-stu-id="084d5-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="084d5-235">**PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="084d5-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="084d5-236">有效的最大按鈕。</span><span class="sxs-lookup"><span data-stu-id="084d5-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="084d5-237">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="084d5-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="084d5-238">模擬眼睛的校正狀態</span><span class="sxs-lookup"><span data-stu-id="084d5-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="084d5-239">**PerceptionSimulation. SimulatedEyesCalibrationState. 無法使用**</span><span class="sxs-lookup"><span data-stu-id="084d5-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="084d5-240">眼睛校正無法使用。</span><span class="sxs-lookup"><span data-stu-id="084d5-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="084d5-241">**PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="084d5-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="084d5-242">眼睛已校正。</span><span class="sxs-lookup"><span data-stu-id="084d5-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="084d5-243">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="084d5-243">This is the default value.</span></span>

<span data-ttu-id="084d5-244">**PerceptionSimulation. SimulatedEyesCalibrationState. 設定**</span><span class="sxs-lookup"><span data-stu-id="084d5-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="084d5-245">正在校正眼睛。</span><span class="sxs-lookup"><span data-stu-id="084d5-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="084d5-246">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="084d5-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="084d5-247">眼睛必須經過校正。</span><span class="sxs-lookup"><span data-stu-id="084d5-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="084d5-248">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="084d5-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="084d5-249">手的接點追蹤精確度。</span><span class="sxs-lookup"><span data-stu-id="084d5-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="084d5-250">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 無法使用**</span><span class="sxs-lookup"><span data-stu-id="084d5-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="084d5-251">不會追蹤聯合。</span><span class="sxs-lookup"><span data-stu-id="084d5-251">The joint is not tracked.</span></span>

<span data-ttu-id="084d5-252">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 近似值**</span><span class="sxs-lookup"><span data-stu-id="084d5-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="084d5-253">會推斷聯合位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-253">The joint position is inferred.</span></span>

<span data-ttu-id="084d5-254">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**</span><span class="sxs-lookup"><span data-stu-id="084d5-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="084d5-255">聯合會受到完整追蹤。</span><span class="sxs-lookup"><span data-stu-id="084d5-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="084d5-256">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="084d5-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="084d5-257">手的接點追蹤精確度。</span><span class="sxs-lookup"><span data-stu-id="084d5-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="084d5-258">**PerceptionSimulation. SimulatedHandPose. 已關閉**</span><span class="sxs-lookup"><span data-stu-id="084d5-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="084d5-259">手的手指接點設定為反映封閉式姿勢。</span><span class="sxs-lookup"><span data-stu-id="084d5-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="084d5-260">**PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="084d5-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="084d5-261">手中的手指接點設定為反映開放式姿勢。</span><span class="sxs-lookup"><span data-stu-id="084d5-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="084d5-262">**PerceptionSimulation. SimulatedHandPose Point**</span><span class="sxs-lookup"><span data-stu-id="084d5-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="084d5-263">手的手指接點設定為反映指標姿勢。</span><span class="sxs-lookup"><span data-stu-id="084d5-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="084d5-264">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="084d5-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="084d5-265">手中的手指接點設定為反映捏合姿勢。</span><span class="sxs-lookup"><span data-stu-id="084d5-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="084d5-266">**PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="084d5-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="084d5-267">SimulatedHandPose 的最大有效值。</span><span class="sxs-lookup"><span data-stu-id="084d5-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="084d5-268">PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="084d5-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="084d5-269">描述播放的狀態。</span><span class="sxs-lookup"><span data-stu-id="084d5-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="084d5-270">**PerceptionSimulation. PlaybackState. 已停止**</span><span class="sxs-lookup"><span data-stu-id="084d5-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="084d5-271">錄製目前已停止，並已準備好進行播放。</span><span class="sxs-lookup"><span data-stu-id="084d5-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="084d5-272">**PerceptionSimulation. PlaybackState. 播放**</span><span class="sxs-lookup"><span data-stu-id="084d5-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="084d5-273">目前現正播放錄製。</span><span class="sxs-lookup"><span data-stu-id="084d5-273">The recording is currently playing.</span></span>

<span data-ttu-id="084d5-274">**PerceptionSimulation. PlaybackState. 已暫停**</span><span class="sxs-lookup"><span data-stu-id="084d5-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="084d5-275">錄製目前已暫停。</span><span class="sxs-lookup"><span data-stu-id="084d5-275">The recording is currently paused.</span></span>

<span data-ttu-id="084d5-276">**PerceptionSimulation. PlaybackState. 結束**</span><span class="sxs-lookup"><span data-stu-id="084d5-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="084d5-277">錄音已到達結尾。</span><span class="sxs-lookup"><span data-stu-id="084d5-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="084d5-278">PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="084d5-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="084d5-279">描述3個元件向量，這可能會描述3D 空間中的點或向量。</span><span class="sxs-lookup"><span data-stu-id="084d5-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="084d5-280">**PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="084d5-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="084d5-281">向量的 X 元件。</span><span class="sxs-lookup"><span data-stu-id="084d5-281">The X component of the vector.</span></span>

<span data-ttu-id="084d5-282">**PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="084d5-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="084d5-283">向量的 Y 元件。</span><span class="sxs-lookup"><span data-stu-id="084d5-283">The Y component of the vector.</span></span>

<span data-ttu-id="084d5-284">**PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="084d5-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="084d5-285">向量的 Z 元件。</span><span class="sxs-lookup"><span data-stu-id="084d5-285">The Z component of the vector.</span></span>

<span data-ttu-id="084d5-286">**PerceptionSimulation. Vector3. #ctor （System.web，system.object，system.string）**</span><span class="sxs-lookup"><span data-stu-id="084d5-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="084d5-287">建立新的 Vector3。</span><span class="sxs-lookup"><span data-stu-id="084d5-287">Construct a new Vector3.</span></span>

<span data-ttu-id="084d5-288">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-288">Parameters</span></span>
* <span data-ttu-id="084d5-289">x-向量的 x 元件。</span><span class="sxs-lookup"><span data-stu-id="084d5-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="084d5-290">y-向量的 y 元件。</span><span class="sxs-lookup"><span data-stu-id="084d5-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="084d5-291">z-向量的 z 元件。</span><span class="sxs-lookup"><span data-stu-id="084d5-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="084d5-292">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="084d5-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="084d5-293">描述3個元件旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="084d5-294">**PerceptionSimulation. Rotation3. 音調**</span><span class="sxs-lookup"><span data-stu-id="084d5-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="084d5-295">旋轉的螺距元件，沿著 X 軸向下移動。</span><span class="sxs-lookup"><span data-stu-id="084d5-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="084d5-296">**PerceptionSimulation. Rotation3. 偏擺**</span><span class="sxs-lookup"><span data-stu-id="084d5-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="084d5-297">旋轉的偏擺元件，右側為 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="084d5-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="084d5-298">**PerceptionSimulation. Rotation3. 滾動**</span><span class="sxs-lookup"><span data-stu-id="084d5-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="084d5-299">旋轉的變換元件，以 Z 軸為左右。</span><span class="sxs-lookup"><span data-stu-id="084d5-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="084d5-300">**PerceptionSimulation. Rotation3. #ctor （System.web，system.object，system.string）**</span><span class="sxs-lookup"><span data-stu-id="084d5-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="084d5-301">建立新的 Rotation3。</span><span class="sxs-lookup"><span data-stu-id="084d5-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="084d5-302">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-302">Parameters</span></span>
* <span data-ttu-id="084d5-303">音調-旋轉的螺距元件。</span><span class="sxs-lookup"><span data-stu-id="084d5-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="084d5-304">偏擺-旋轉的偏擺元件。</span><span class="sxs-lookup"><span data-stu-id="084d5-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="084d5-305">變換：旋轉的滾動部分。</span><span class="sxs-lookup"><span data-stu-id="084d5-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="084d5-306">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="084d5-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="084d5-307">描述模擬手上的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="084d5-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="084d5-308">**PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="084d5-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="084d5-309">聯合的位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-309">The position of the joint.</span></span>

<span data-ttu-id="084d5-310">**PerceptionSimulation. SimulatedHandJointConfiguration. 旋轉**</span><span class="sxs-lookup"><span data-stu-id="084d5-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="084d5-311">聯合的旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-311">The rotation of the joint.</span></span>

<span data-ttu-id="084d5-312">**PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="084d5-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="084d5-313">聯合的追蹤精確度。</span><span class="sxs-lookup"><span data-stu-id="084d5-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="084d5-314">PerceptionSimulation。</span><span class="sxs-lookup"><span data-stu-id="084d5-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="084d5-315">描述相機通常使用的視圖截圖。</span><span class="sxs-lookup"><span data-stu-id="084d5-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="084d5-316">**PerceptionSimulation。 Near**</span><span class="sxs-lookup"><span data-stu-id="084d5-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="084d5-317">以截距包含的最小距離。</span><span class="sxs-lookup"><span data-stu-id="084d5-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="084d5-318">**PerceptionSimulation....。**</span><span class="sxs-lookup"><span data-stu-id="084d5-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="084d5-319">以截距包含的最大距離。</span><span class="sxs-lookup"><span data-stu-id="084d5-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="084d5-320">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="084d5-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="084d5-321">截量的水準欄位，以弧度為單位（小於 PI）。</span><span class="sxs-lookup"><span data-stu-id="084d5-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="084d5-322">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="084d5-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="084d5-323">水準欄位和視圖垂直欄位的比例。</span><span class="sxs-lookup"><span data-stu-id="084d5-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="084d5-324">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="084d5-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="084d5-325">用於產生用於控制裝置之封包的根目錄。</span><span class="sxs-lookup"><span data-stu-id="084d5-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="084d5-326">**PerceptionSimulation. IPerceptionSimulationManager. 裝置**</span><span class="sxs-lookup"><span data-stu-id="084d5-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="084d5-327">取出模擬的裝置物件，以解讀模擬的人和模擬世界。</span><span class="sxs-lookup"><span data-stu-id="084d5-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="084d5-328">**PerceptionSimulation. IPerceptionSimulationManager. 人類**</span><span class="sxs-lookup"><span data-stu-id="084d5-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="084d5-329">取得控制模擬人類的物件。</span><span class="sxs-lookup"><span data-stu-id="084d5-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="084d5-330">**PerceptionSimulation. IPerceptionSimulationManager. 重設**</span><span class="sxs-lookup"><span data-stu-id="084d5-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="084d5-331">將模擬重設為其預設狀態。</span><span class="sxs-lookup"><span data-stu-id="084d5-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="084d5-332">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="084d5-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="084d5-333">描述裝置的介面，其會解讀模擬世界和模擬的人類</span><span class="sxs-lookup"><span data-stu-id="084d5-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="084d5-334">**PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="084d5-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="084d5-335">從模擬裝置取出 Head 追蹤器。</span><span class="sxs-lookup"><span data-stu-id="084d5-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="084d5-336">**PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="084d5-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="084d5-337">從模擬的裝置抓取手追蹤器。</span><span class="sxs-lookup"><span data-stu-id="084d5-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="084d5-338">**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType （Microsoft PerceptionSimulation. SimulatedDeviceType）**</span><span class="sxs-lookup"><span data-stu-id="084d5-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="084d5-339">設定模擬裝置的屬性，以符合提供的裝置類型。</span><span class="sxs-lookup"><span data-stu-id="084d5-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="084d5-340">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-340">Parameters</span></span>
* <span data-ttu-id="084d5-341">類型-模擬裝置的新類型</span><span class="sxs-lookup"><span data-stu-id="084d5-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="084d5-342">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="084d5-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="084d5-343">描述模擬裝置之部分的介面，它會追蹤模擬人類的標頭。</span><span class="sxs-lookup"><span data-stu-id="084d5-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="084d5-344">**PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="084d5-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="084d5-345">抓取和設定目前的標頭追蹤器模式。</span><span class="sxs-lookup"><span data-stu-id="084d5-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="084d5-346">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="084d5-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="084d5-347">描述模擬裝置之部分的介面，可追蹤模擬人類的手</span><span class="sxs-lookup"><span data-stu-id="084d5-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="084d5-348">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="084d5-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="084d5-349">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="084d5-350">**PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="084d5-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="084d5-351">抓取和設定模擬的手勢追蹤器的位置（相對於 head 的中心）。</span><span class="sxs-lookup"><span data-stu-id="084d5-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="084d5-352">**PerceptionSimulation. ISimulatedHandTracker. 音調**</span><span class="sxs-lookup"><span data-stu-id="084d5-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="084d5-353">取出並設定模擬的手勢追蹤器的下音調。</span><span class="sxs-lookup"><span data-stu-id="084d5-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="084d5-354">**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="084d5-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="084d5-355">抓取和設定是否忽略模擬的手勢追蹤器的錐狀。</span><span class="sxs-lookup"><span data-stu-id="084d5-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="084d5-356">忽略時，一律會顯示這兩個手。</span><span class="sxs-lookup"><span data-stu-id="084d5-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="084d5-357">[未略過] （預設值）只會在手上的 [指標追蹤器] 中出現時才會顯示。</span><span class="sxs-lookup"><span data-stu-id="084d5-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="084d5-358">**PerceptionSimulation. ISimulatedHandTracker。**</span><span class="sxs-lookup"><span data-stu-id="084d5-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="084d5-359">抓取和設定用來判斷模擬的手追蹤器是否可以看見手的「截錐」屬性。</span><span class="sxs-lookup"><span data-stu-id="084d5-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="084d5-360">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="084d5-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="084d5-361">控制模擬人類的最上層介面。</span><span class="sxs-lookup"><span data-stu-id="084d5-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="084d5-362">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="084d5-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="084d5-363">抓取和設定與世界相關的節點位置（以量為單位）。</span><span class="sxs-lookup"><span data-stu-id="084d5-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="084d5-364">這個位置會對應到位於人類腳中心的點。</span><span class="sxs-lookup"><span data-stu-id="084d5-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="084d5-365">**PerceptionSimulation. ISimulatedHuman. 方向**</span><span class="sxs-lookup"><span data-stu-id="084d5-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="084d5-366">取得並設定世界中模擬的人臉方向。</span><span class="sxs-lookup"><span data-stu-id="084d5-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="084d5-367">0弧度會向下到負 Z 軸。</span><span class="sxs-lookup"><span data-stu-id="084d5-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="084d5-368">正弧度會順時針旋轉 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="084d5-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="084d5-369">**PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="084d5-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="084d5-370">抓取和設定模擬人的高度（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="084d5-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="084d5-371">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="084d5-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="084d5-372">取出模擬人類的左邊。</span><span class="sxs-lookup"><span data-stu-id="084d5-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="084d5-373">**PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="084d5-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="084d5-374">取得模擬人類的右手邊。</span><span class="sxs-lookup"><span data-stu-id="084d5-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="084d5-375">**PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="084d5-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="084d5-376">抓取模擬人類的標頭。</span><span class="sxs-lookup"><span data-stu-id="084d5-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="084d5-377">**PerceptionSimulation. ISimulatedHuman. Move （PerceptionSimulation. Vector3）**</span><span class="sxs-lookup"><span data-stu-id="084d5-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="084d5-378">將模擬人相對於其目前位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="084d5-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="084d5-379">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-379">Parameters</span></span>
* <span data-ttu-id="084d5-380">轉譯-要移動的轉譯，相對於目前的位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="084d5-381">**PerceptionSimulation. ISimulatedHuman. 旋轉（System.web）**</span><span class="sxs-lookup"><span data-stu-id="084d5-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="084d5-382">以順時針方向針對 Y 軸，將模擬的人類旋轉相對於其目前方向</span><span class="sxs-lookup"><span data-stu-id="084d5-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="084d5-383">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-383">Parameters</span></span>
* <span data-ttu-id="084d5-384">弧度-要繞著 Y 軸旋轉的數量。</span><span class="sxs-lookup"><span data-stu-id="084d5-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="084d5-385">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="084d5-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="084d5-386">藉由將 ISimulatedHuman 轉型為 ISimulatedHuman2，可以使用其他屬性。</span><span class="sxs-lookup"><span data-stu-id="084d5-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="084d5-387">**PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="084d5-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="084d5-388">取出左邊的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="084d5-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="084d5-389">**PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="084d5-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="084d5-390">取出右6個 DOF 的控制器。</span><span class="sxs-lookup"><span data-stu-id="084d5-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="084d5-391">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="084d5-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="084d5-392">描述模擬人類之手的介面</span><span class="sxs-lookup"><span data-stu-id="084d5-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="084d5-393">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="084d5-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="084d5-394">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="084d5-395">**PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="084d5-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="084d5-396">抓取和設定相對於人類（以量為單位）的模擬手勢位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="084d5-397">**PerceptionSimulation. ISimulatedHand. 已啟用**</span><span class="sxs-lookup"><span data-stu-id="084d5-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="084d5-398">抓取並設定是否目前已啟用手。</span><span class="sxs-lookup"><span data-stu-id="084d5-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="084d5-399">**PerceptionSimulation. ISimulatedHand. Visible**</span><span class="sxs-lookup"><span data-stu-id="084d5-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="084d5-400">抓取 SimulatedDevice 的目前是否可見（也就是它是否位於 HandTracker 所偵測到的位置）。</span><span class="sxs-lookup"><span data-stu-id="084d5-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="084d5-401">**PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="084d5-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="084d5-402">移動手，讓 SimulatedDevice 可以看到它。</span><span class="sxs-lookup"><span data-stu-id="084d5-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="084d5-403">**PerceptionSimulation. ISimulatedHand. Move （PerceptionSimulation. Vector3）**</span><span class="sxs-lookup"><span data-stu-id="084d5-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="084d5-404">移動模擬手相對於其目前位置的位置（以量為單位）。</span><span class="sxs-lookup"><span data-stu-id="084d5-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="084d5-405">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-405">Parameters</span></span>
* <span data-ttu-id="084d5-406">轉譯-要轉譯模擬手的數量。</span><span class="sxs-lookup"><span data-stu-id="084d5-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="084d5-407">**PerceptionSimulation. ISimulatedHand. PerformGesture （Microsoft PerceptionSimulation. SimulatedGesture）**</span><span class="sxs-lookup"><span data-stu-id="084d5-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="084d5-408">使用模擬的手執行手勢。</span><span class="sxs-lookup"><span data-stu-id="084d5-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="084d5-409">只有在已啟用手時，系統才會偵測到此檔案。</span><span class="sxs-lookup"><span data-stu-id="084d5-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="084d5-410">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-410">Parameters</span></span>
* <span data-ttu-id="084d5-411">手勢-要執行的手勢。</span><span class="sxs-lookup"><span data-stu-id="084d5-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="084d5-412">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="084d5-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="084d5-413">將 ISimulatedHand 轉換為 ISimulatedHand2 可使用其他屬性。</span><span class="sxs-lookup"><span data-stu-id="084d5-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="084d5-414">**PerceptionSimulation. ISimulatedHand2. 取向**</span><span class="sxs-lookup"><span data-stu-id="084d5-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="084d5-415">取出或設定模擬手的旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="084d5-416">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="084d5-417">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="084d5-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="084d5-418">將 ISimulatedHand 轉換為 ISimulatedHand3 可使用其他屬性</span><span class="sxs-lookup"><span data-stu-id="084d5-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="084d5-419">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="084d5-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="084d5-420">取得所指定聯合的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="084d5-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="084d5-421">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="084d5-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="084d5-422">設定所指定聯合的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="084d5-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="084d5-423">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="084d5-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="084d5-424">將手設定為已知的姿勢，並使用選擇性的旗標來製作動畫。</span><span class="sxs-lookup"><span data-stu-id="084d5-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="084d5-425">注意：動畫不會導致直接反映其最終的聯合設定。</span><span class="sxs-lookup"><span data-stu-id="084d5-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="084d5-426">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="084d5-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="084d5-427">描述模擬人的頭的介面。</span><span class="sxs-lookup"><span data-stu-id="084d5-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="084d5-428">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="084d5-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="084d5-429">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="084d5-430">**PerceptionSimulation. ISimulatedHead. 旋轉**</span><span class="sxs-lookup"><span data-stu-id="084d5-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="084d5-431">取出模擬標頭的旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="084d5-432">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="084d5-433">**PerceptionSimulation. ISimulatedHead. 直徑**</span><span class="sxs-lookup"><span data-stu-id="084d5-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="084d5-434">取出模擬的標頭直徑。</span><span class="sxs-lookup"><span data-stu-id="084d5-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="084d5-435">這個值是用來判斷 head 的中心（旋轉點）。</span><span class="sxs-lookup"><span data-stu-id="084d5-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="084d5-436">**PerceptionSimulation. ISimulatedHead. 旋轉（PerceptionSimulation. Rotation3）**</span><span class="sxs-lookup"><span data-stu-id="084d5-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="084d5-437">將模擬的標頭旋轉成相對於目前的旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="084d5-438">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="084d5-439">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-439">Parameters</span></span>
* <span data-ttu-id="084d5-440">旋轉-要旋轉的數量。</span><span class="sxs-lookup"><span data-stu-id="084d5-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="084d5-441">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="084d5-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="084d5-442">將 ISimulatedHead 轉換為 ISimulatedHead2 可使用其他屬性</span><span class="sxs-lookup"><span data-stu-id="084d5-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="084d5-443">**PerceptionSimulation. ISimulatedHead2 眼**</span><span class="sxs-lookup"><span data-stu-id="084d5-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="084d5-444">取出模擬人類的眼睛。</span><span class="sxs-lookup"><span data-stu-id="084d5-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="084d5-445">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="084d5-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="084d5-446">描述與模擬人類相關聯之 6 DOF 控制器的介面。</span><span class="sxs-lookup"><span data-stu-id="084d5-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="084d5-447">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="084d5-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="084d5-448">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="084d5-449">**PerceptionSimulation. ISimulatedSixDofController. 狀態**</span><span class="sxs-lookup"><span data-stu-id="084d5-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="084d5-450">取得或設定控制器的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="084d5-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="084d5-451">控制器狀態必須設定為 [關閉] 以外的值，才能進行移動、旋轉或按下按鈕的任何呼叫。</span><span class="sxs-lookup"><span data-stu-id="084d5-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="084d5-452">**PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="084d5-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="084d5-453">抓取或設定模擬控制器相對於人類的位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="084d5-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="084d5-454">**PerceptionSimulation. ISimulatedSixDofController. 取向**</span><span class="sxs-lookup"><span data-stu-id="084d5-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="084d5-455">取得或設定模擬控制器的方向。</span><span class="sxs-lookup"><span data-stu-id="084d5-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="084d5-456">**PerceptionSimulation. ISimulatedSixDofController. Move （PerceptionSimulation. Vector3）**</span><span class="sxs-lookup"><span data-stu-id="084d5-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="084d5-457">移動模擬控制器相對於其目前位置的位置（以計量為單位）。</span><span class="sxs-lookup"><span data-stu-id="084d5-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="084d5-458">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-458">Parameters</span></span>
* <span data-ttu-id="084d5-459">轉譯-要轉譯模擬控制器的數量。</span><span class="sxs-lookup"><span data-stu-id="084d5-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="084d5-460">**PerceptionSimulation. ISimulatedSixDofController. PressButton （SimulatedSixDofControllerButton）**</span><span class="sxs-lookup"><span data-stu-id="084d5-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="084d5-461">在模擬控制器上按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="084d5-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="084d5-462">只有在已啟用控制器的情況下，系統才會偵測到它。</span><span class="sxs-lookup"><span data-stu-id="084d5-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="084d5-463">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-463">Parameters</span></span>
* <span data-ttu-id="084d5-464">按鈕-要按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="084d5-464">button - The button to press.</span></span>

<span data-ttu-id="084d5-465">**PerceptionSimulation. ISimulatedSixDofController. ReleaseButton （SimulatedSixDofControllerButton）**</span><span class="sxs-lookup"><span data-stu-id="084d5-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="084d5-466">釋放模擬控制器上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="084d5-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="084d5-467">只有在已啟用控制器的情況下，系統才會偵測到它。</span><span class="sxs-lookup"><span data-stu-id="084d5-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="084d5-468">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-468">Parameters</span></span>
* <span data-ttu-id="084d5-469">按鈕-要發行的按鈕。</span><span class="sxs-lookup"><span data-stu-id="084d5-469">button - The button to release.</span></span>

<span data-ttu-id="084d5-470">**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition （out float，out float）**</span><span class="sxs-lookup"><span data-stu-id="084d5-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="084d5-471">取得模擬控制器的觸控板上的模擬手指位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="084d5-472">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-472">Parameters</span></span>
* <span data-ttu-id="084d5-473">x-手指的水準位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="084d5-474">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="084d5-475">**PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition （float，float）**</span><span class="sxs-lookup"><span data-stu-id="084d5-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="084d5-476">將模擬手指的位置設定在模擬控制器的觸控板上。</span><span class="sxs-lookup"><span data-stu-id="084d5-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="084d5-477">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-477">Parameters</span></span>
* <span data-ttu-id="084d5-478">x-手指的水準位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="084d5-479">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="084d5-480">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="084d5-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="084d5-481">將 ISimulatedSixDofController 轉換為 ISimulatedSixDofController2 可使用其他屬性和方法</span><span class="sxs-lookup"><span data-stu-id="084d5-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="084d5-482">**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition （out float，out float）**</span><span class="sxs-lookup"><span data-stu-id="084d5-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="084d5-483">取得模擬控制站上模擬的操縱杆位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="084d5-484">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-484">Parameters</span></span>
* <span data-ttu-id="084d5-485">x-操縱杆的水準位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="084d5-486">y-操縱杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="084d5-487">**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition （float，float）**</span><span class="sxs-lookup"><span data-stu-id="084d5-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="084d5-488">在模擬的控制器上設定模擬的操縱杆位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="084d5-489">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-489">Parameters</span></span>
* <span data-ttu-id="084d5-490">x-操縱杆的水準位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="084d5-491">y-操縱杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="084d5-492">**PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="084d5-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="084d5-493">取出或設定模擬控制器的電池計量。</span><span class="sxs-lookup"><span data-stu-id="084d5-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="084d5-494">此值必須大於0.0 且小於或等於100.0。</span><span class="sxs-lookup"><span data-stu-id="084d5-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="084d5-495">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="084d5-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="084d5-496">描述模擬人眼的介面。</span><span class="sxs-lookup"><span data-stu-id="084d5-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="084d5-497">**PerceptionSimulation. ISimulatedEyes. 旋轉**</span><span class="sxs-lookup"><span data-stu-id="084d5-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="084d5-498">取出模擬眼睛的旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="084d5-499">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="084d5-500">**PerceptionSimulation. ISimulatedEyes. 旋轉（PerceptionSimulation. Rotation3）**</span><span class="sxs-lookup"><span data-stu-id="084d5-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="084d5-501">旋轉模擬的眼睛，相對於其目前的旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="084d5-502">正弧度在沿著軸進行檢查時，順時針旋轉。</span><span class="sxs-lookup"><span data-stu-id="084d5-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="084d5-503">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-503">Parameters</span></span>
* <span data-ttu-id="084d5-504">旋轉-要旋轉的數量。</span><span class="sxs-lookup"><span data-stu-id="084d5-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="084d5-505">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="084d5-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="084d5-506">抓取或設定模擬眼睛的校正狀態。</span><span class="sxs-lookup"><span data-stu-id="084d5-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="084d5-507">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="084d5-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="084d5-508">以量表為單位，抓取節點與世界的相對位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="084d5-509">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="084d5-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="084d5-510">介面，用於與已載入播放的單一錄製進行互動。</span><span class="sxs-lookup"><span data-stu-id="084d5-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="084d5-511">**PerceptionSimulation. ISimulationRecording 資料類型**</span><span class="sxs-lookup"><span data-stu-id="084d5-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="084d5-512">抓取記錄中的資料類型清單。</span><span class="sxs-lookup"><span data-stu-id="084d5-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="084d5-513">**PerceptionSimulation. ISimulationRecording. 州/省**</span><span class="sxs-lookup"><span data-stu-id="084d5-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="084d5-514">抓取錄影的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="084d5-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="084d5-515">**PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="084d5-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="084d5-516">開始播放。</span><span class="sxs-lookup"><span data-stu-id="084d5-516">Start the playback.</span></span> <span data-ttu-id="084d5-517">如果記錄已暫停，播放將會從暫停的位置繼續執行;如果已停止，播放會從一開始開始。</span><span class="sxs-lookup"><span data-stu-id="084d5-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="084d5-518">如果已經在播放，則會忽略此呼叫。</span><span class="sxs-lookup"><span data-stu-id="084d5-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="084d5-519">**PerceptionSimulation. ISimulationRecording. Pause**</span><span class="sxs-lookup"><span data-stu-id="084d5-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="084d5-520">暫停播放目前的位置。</span><span class="sxs-lookup"><span data-stu-id="084d5-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="084d5-521">如果記錄已停止，則會忽略呼叫。</span><span class="sxs-lookup"><span data-stu-id="084d5-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="084d5-522">**PerceptionSimulation. ISimulationRecording. Seek （System.object）**</span><span class="sxs-lookup"><span data-stu-id="084d5-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="084d5-523">將記錄搜尋到指定的時間（從一開始的100毫微秒間隔），並在該位置暫停。</span><span class="sxs-lookup"><span data-stu-id="084d5-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="084d5-524">如果時間超過錄製的結尾，則會在最後一個畫面上暫停。</span><span class="sxs-lookup"><span data-stu-id="084d5-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="084d5-525">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-525">Parameters</span></span>
* <span data-ttu-id="084d5-526">刻度-要搜尋的時間。</span><span class="sxs-lookup"><span data-stu-id="084d5-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="084d5-527">**PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="084d5-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="084d5-528">停止播放，並將位置重設為開頭。</span><span class="sxs-lookup"><span data-stu-id="084d5-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="084d5-529">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="084d5-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="084d5-530">用於在播放期間接收狀態變更的介面。</span><span class="sxs-lookup"><span data-stu-id="084d5-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="084d5-531">**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged （Microsoft PerceptionSimulation. PlaybackState）**</span><span class="sxs-lookup"><span data-stu-id="084d5-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="084d5-532">當 ISimulationRecording 的播放狀態變更時呼叫。</span><span class="sxs-lookup"><span data-stu-id="084d5-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="084d5-533">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-533">Parameters</span></span>
* <span data-ttu-id="084d5-534">newState-記錄的新狀態。</span><span class="sxs-lookup"><span data-stu-id="084d5-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="084d5-535">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="084d5-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="084d5-536">用來建立認知模擬物件的根物件。</span><span class="sxs-lookup"><span data-stu-id="084d5-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="084d5-537">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager （Microsoft PerceptionSimulation. ISimulationStreamSink）**</span><span class="sxs-lookup"><span data-stu-id="084d5-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="084d5-538">在物件上建立以產生模擬封包，並將它們傳遞至提供的接收。</span><span class="sxs-lookup"><span data-stu-id="084d5-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="084d5-539">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-539">Parameters</span></span>
* <span data-ttu-id="084d5-540">sink-接收所有產生的封包的接收器。</span><span class="sxs-lookup"><span data-stu-id="084d5-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="084d5-541">傳回值</span><span class="sxs-lookup"><span data-stu-id="084d5-541">Return value</span></span>

<span data-ttu-id="084d5-542">建立的管理員。</span><span class="sxs-lookup"><span data-stu-id="084d5-542">The created Manager.</span></span>

<span data-ttu-id="084d5-543">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording （System.string）**</span><span class="sxs-lookup"><span data-stu-id="084d5-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="084d5-544">建立接收，將所有接收的封包儲存在檔案中的指定路徑。</span><span class="sxs-lookup"><span data-stu-id="084d5-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="084d5-545">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-545">Parameters</span></span>
* <span data-ttu-id="084d5-546">path-要建立之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="084d5-546">path - The path of the file to create.</span></span>

<span data-ttu-id="084d5-547">傳回值</span><span class="sxs-lookup"><span data-stu-id="084d5-547">Return value</span></span>

<span data-ttu-id="084d5-548">建立的接收。</span><span class="sxs-lookup"><span data-stu-id="084d5-548">The created sink.</span></span>

<span data-ttu-id="084d5-549">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording （System.string，Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory）**</span><span class="sxs-lookup"><span data-stu-id="084d5-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="084d5-550">從指定的檔案載入記錄。</span><span class="sxs-lookup"><span data-stu-id="084d5-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="084d5-551">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-551">Parameters</span></span>
* <span data-ttu-id="084d5-552">path-要載入的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="084d5-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="084d5-553">factory-記錄在需要時用來建立 ISimulationStreamSink 的 factory。</span><span class="sxs-lookup"><span data-stu-id="084d5-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="084d5-554">傳回值</span><span class="sxs-lookup"><span data-stu-id="084d5-554">Return value</span></span>

<span data-ttu-id="084d5-555">載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="084d5-555">The loaded recording.</span></span>

<span data-ttu-id="084d5-556">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording （System.string，Microsoft PerceptionSimulation. ISimulationStreamSinkFactory，PerceptionSimulation. ISimulationRecordingCallback）**</span><span class="sxs-lookup"><span data-stu-id="084d5-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="084d5-557">從指定的檔案載入記錄。</span><span class="sxs-lookup"><span data-stu-id="084d5-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="084d5-558">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-558">Parameters</span></span>
* <span data-ttu-id="084d5-559">path-要載入的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="084d5-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="084d5-560">factory-記錄在需要時用來建立 ISimulationStreamSink 的 factory。</span><span class="sxs-lookup"><span data-stu-id="084d5-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="084d5-561">回呼-接收更新的回呼會 regrading 記錄的狀態。</span><span class="sxs-lookup"><span data-stu-id="084d5-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="084d5-562">傳回值</span><span class="sxs-lookup"><span data-stu-id="084d5-562">Return value</span></span>

<span data-ttu-id="084d5-563">載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="084d5-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="084d5-564">PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="084d5-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="084d5-565">描述不同類型的資料流程資料。</span><span class="sxs-lookup"><span data-stu-id="084d5-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="084d5-566">**PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="084d5-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="084d5-567">用來表示沒有資料流程資料類型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="084d5-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="084d5-568">**PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="084d5-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="084d5-569">關於 head 位置和方向的資料流程。</span><span class="sxs-lookup"><span data-stu-id="084d5-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="084d5-570">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="084d5-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="084d5-571">關於手的位置和手勢的資料流程。</span><span class="sxs-lookup"><span data-stu-id="084d5-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="084d5-572">**PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="084d5-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="084d5-573">關於環境的空間對應的資料流程。</span><span class="sxs-lookup"><span data-stu-id="084d5-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="084d5-574">**PerceptionSimulation. StreamDataTypes. 校正**</span><span class="sxs-lookup"><span data-stu-id="084d5-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="084d5-575">關於裝置校正的資料流程。</span><span class="sxs-lookup"><span data-stu-id="084d5-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="084d5-576">只有在遠端模式中的系統才會接受校正封包。</span><span class="sxs-lookup"><span data-stu-id="084d5-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="084d5-577">**PerceptionSimulation. StreamDataTypes. 環境**</span><span class="sxs-lookup"><span data-stu-id="084d5-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="084d5-578">關於裝置環境的資料流程。</span><span class="sxs-lookup"><span data-stu-id="084d5-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="084d5-579">**PerceptionSimulation. StreamDataTypes. 全部**</span><span class="sxs-lookup"><span data-stu-id="084d5-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="084d5-580">用來表示所有記錄資料類型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="084d5-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="084d5-581">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="084d5-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="084d5-582">物件，接收來自模擬資料流程的資料封包。</span><span class="sxs-lookup"><span data-stu-id="084d5-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="084d5-583">**PerceptionSimulation. ISimulationStreamSink. OnPacketReceived （uint length，byte [] 封包）**</span><span class="sxs-lookup"><span data-stu-id="084d5-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="084d5-584">接收單一封包，其為內部輸入和版本設定。</span><span class="sxs-lookup"><span data-stu-id="084d5-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="084d5-585">Parameters</span><span class="sxs-lookup"><span data-stu-id="084d5-585">Parameters</span></span>
* <span data-ttu-id="084d5-586">length-封包的長度。</span><span class="sxs-lookup"><span data-stu-id="084d5-586">length - The length of the packet.</span></span>
* <span data-ttu-id="084d5-587">封包-封包的資料。</span><span class="sxs-lookup"><span data-stu-id="084d5-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="084d5-588">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="084d5-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="084d5-589">建立 ISimulationStreamSink 的物件。</span><span class="sxs-lookup"><span data-stu-id="084d5-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="084d5-590">**PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink （）**</span><span class="sxs-lookup"><span data-stu-id="084d5-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="084d5-591">建立 ISimulationStreamSink 的單一實例。</span><span class="sxs-lookup"><span data-stu-id="084d5-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="084d5-592">傳回值</span><span class="sxs-lookup"><span data-stu-id="084d5-592">Return value</span></span>

<span data-ttu-id="084d5-593">建立的接收。</span><span class="sxs-lookup"><span data-stu-id="084d5-593">The created sink.</span></span>
