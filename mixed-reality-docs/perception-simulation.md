---
title: Perception 模擬
description: 使用認知模擬程式庫來自動化模擬的輸入沉浸式應用程式的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens，模擬測試
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414535"
---
# <a name="perception-simulation"></a><span data-ttu-id="585ae-104">Perception 模擬</span><span class="sxs-lookup"><span data-stu-id="585ae-104">Perception simulation</span></span>

<span data-ttu-id="585ae-105">若要建置應用程式的自動化的測試嗎？</span><span class="sxs-lookup"><span data-stu-id="585ae-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="585ae-106">您想要超越元件層級的單元測試，並確實執行您應用程式端對端測試嗎？</span><span class="sxs-lookup"><span data-stu-id="585ae-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="585ae-107">Perception 模擬是您要尋找的內容。</span><span class="sxs-lookup"><span data-stu-id="585ae-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="585ae-108">Perception 模擬程式庫傳送人力和世界輸入您的應用程式的資料，因此您可以將自動化測試。</span><span class="sxs-lookup"><span data-stu-id="585ae-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="585ae-109">例如，您可以模擬人為想要的特定、 高再現性的位置，然後執行動作，或使用動作控制器的輸入。</span><span class="sxs-lookup"><span data-stu-id="585ae-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="585ae-110">Perception 模擬可以將這類的模擬的輸入傳送至實體的 HoloLens、 HoloLens 模擬器 （第 1 代）、 HoloLens 2 的模擬器或使用混合實境入口網站的電腦安裝。</span><span class="sxs-lookup"><span data-stu-id="585ae-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="585ae-111">模擬會略過混合實境裝置上的即時感應器並傳送認知模擬裝置上執行的應用程式的輸入。</span><span class="sxs-lookup"><span data-stu-id="585ae-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="585ae-112">應用程式收到這些輸入的事件，透過相同的 Api，它們一律使用和無法分辨執行搭配真實感應器與 Perception 模擬與執行之間的差異。</span><span class="sxs-lookup"><span data-stu-id="585ae-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="585ae-113">Perception 模擬是 HoloLens 模擬器用來傳送模擬的輸入到 HoloLens 虛擬機器中的相同技術。</span><span class="sxs-lookup"><span data-stu-id="585ae-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="585ae-114">若要開始在您的程式碼中使用模擬，首先建立 IPerceptionSimulationManager 物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="585ae-115">從該物件中，您可以發出命令來控制模擬 「 人 」，包括前端的位置、 游標位置和筆勢，屬性，您可以啟用和操作動作控制站。</span><span class="sxs-lookup"><span data-stu-id="585ae-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="585ae-116">Visual Studio 專案設定 Perception 模擬</span><span class="sxs-lookup"><span data-stu-id="585ae-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="585ae-117">[安裝 HoloLens 模擬器](install-the-tools.md)開發電腦上。</span><span class="sxs-lookup"><span data-stu-id="585ae-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="585ae-118">模擬器會包含您要用於 Perception 模擬程式庫。</span><span class="sxs-lookup"><span data-stu-id="585ae-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="585ae-119">建立新的 Visual StudioC#桌面 （主控台專案非常適合開始） 的專案。</span><span class="sxs-lookup"><span data-stu-id="585ae-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="585ae-120">做為參考，將下列二進位檔加入至專案 (專案]-> [新增...]-> [參考)。您可以找到它們在 %programfiles (x86) %\Microsoft XDE\\（版本），例如 **%programfiles (x86) %\Microsoft XDE\\10.0.18362.0** HoloLens 2 模擬器。</span><span class="sxs-lookup"><span data-stu-id="585ae-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="585ae-121">(注意： 雖然二進位檔是 HoloLens 2 模擬器的一部分，它們也適用於 Windows Mixed Reality 桌面上。)a。</span><span class="sxs-lookup"><span data-stu-id="585ae-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="585ae-122">PerceptionSimulationManager.Interop.dll-管理C#Perception 模擬的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="585ae-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="585ae-123">b.</span><span class="sxs-lookup"><span data-stu-id="585ae-123">b.</span></span> <span data-ttu-id="585ae-124">PerceptionSimulationRest.dll-設定 web 通訊端通訊通道的 HoloLens 或模擬器的程式庫。</span><span class="sxs-lookup"><span data-stu-id="585ae-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="585ae-125">c.</span><span class="sxs-lookup"><span data-stu-id="585ae-125">c.</span></span> <span data-ttu-id="585ae-126">SimulationStream.Interop.dll-模擬的共用類型。</span><span class="sxs-lookup"><span data-stu-id="585ae-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="585ae-127">將實作新增至您的專案二進位 PerceptionSimulationManager.dll。</span><span class="sxs-lookup"><span data-stu-id="585ae-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="585ae-128">第一次以二進位格式將它新增至專案 (專案]-> [新增...]-> [現有項目)。將它儲存為連結，使它不會將它複製到您專案的來源資料夾。</span><span class="sxs-lookup"><span data-stu-id="585ae-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="585ae-129">![加入專案做為連結的 PerceptionSimulationManager.dll](images/saveaslink.png) b。</span><span class="sxs-lookup"><span data-stu-id="585ae-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="585ae-130">請確定它取得的複製到組建輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="585ae-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="585ae-131">這是在二進位檔的屬性工作表中。</span><span class="sxs-lookup"><span data-stu-id="585ae-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="585ae-132">![若要複製到輸出目錄的 Mark PerceptionSimulationManager.dll](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="585ae-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="585ae-133">設定您的使用中的方案平台為 x64。</span><span class="sxs-lookup"><span data-stu-id="585ae-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="585ae-134">（使用 Configuration Manager 來建立適用於 x64 的平台項目，如果尚未存在）。</span><span class="sxs-lookup"><span data-stu-id="585ae-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="585ae-135">建立 IPerceptionSimulation Manager 物件</span><span class="sxs-lookup"><span data-stu-id="585ae-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="585ae-136">若要控制模擬，您將更新發給 IPerceptionSimulationManager 物件中擷取的物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="585ae-137">第一個步驟是取得該物件，並將它連接到您的目標裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="585ae-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="585ae-138">您可以在裝置入口網站中的按鈕，即可取得您的模擬器的 IP 位址[工具列](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="585ae-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="585ae-139">![開啟 [裝置入口網站] 圖示](images/emulator-deviceportal.png)**開啟裝置入口網站**:在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="585ae-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="585ae-140">Windows Mixed Reality，這可以擷取在 [更新與安全性] 之下，則 「 適用於開發人員 」，[設定] 應用程式中"使用連接:"一節 「 啟用裝置入口網站 」。</span><span class="sxs-lookup"><span data-stu-id="585ae-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="585ae-141">請務必記下 IP 位址和連接埠。</span><span class="sxs-lookup"><span data-stu-id="585ae-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="585ae-142">首先，您將呼叫 RestSimulationStreamSink.Create 取得 RestSimulationStreamSink 物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="585ae-143">這是目標裝置或模擬器，您會控制透過 http 連線。</span><span class="sxs-lookup"><span data-stu-id="585ae-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="585ae-144">您的命令將會傳遞至，而且由[Windows Device Portal](using-the-windows-device-portal.md)裝置或模擬器上執行。</span><span class="sxs-lookup"><span data-stu-id="585ae-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="585ae-145">您必須建立物件的四個參數如下：</span><span class="sxs-lookup"><span data-stu-id="585ae-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="585ae-146">Uri 的 uri-目標裝置的 IP 位址 (例如，「 http://123.123.123.123 「 或 」 http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="585ae-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="585ae-147">System.Net.NetworkCredential 認證-使用者名稱/密碼連接到[Windows Device Portal](using-the-windows-device-portal.md)目標裝置或模擬器上。</span><span class="sxs-lookup"><span data-stu-id="585ae-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="585ae-148">如果您要連接到其本機位址透過模擬器 (例如 168。 *。* 。 \*) 在相同電腦上，將會接受任何認證。</span><span class="sxs-lookup"><span data-stu-id="585ae-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="585ae-149">bool 正常-適用於一般的優先權，則為 false 的低優先順序服務。</span><span class="sxs-lookup"><span data-stu-id="585ae-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="585ae-150">您通常想要將此設為 *，則為 true*進行測試案例，可讓您的測試，來控制。</span><span class="sxs-lookup"><span data-stu-id="585ae-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="585ae-151">模擬器 和 Windows Mixed Reality 模擬使用低優先順序服務連線。</span><span class="sxs-lookup"><span data-stu-id="585ae-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="585ae-152">如果您的測試也會使用低優先順序服務連線，最最近建立的連接將會在控制項中。</span><span class="sxs-lookup"><span data-stu-id="585ae-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="585ae-153">System.Threading.CancellationToken 權杖-語彙基元來取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="585ae-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="585ae-154">其次，您將建立 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="585ae-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="585ae-155">這是您用來控制模擬的物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="585ae-156">請注意，這也必須在非同步方法。</span><span class="sxs-lookup"><span data-stu-id="585ae-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="585ae-157">控制模擬人類看得</span><span class="sxs-lookup"><span data-stu-id="585ae-157">Control the simulated Human</span></span>

<span data-ttu-id="585ae-158">IPerceptionSimulationManager 有一個人為的屬性會傳回 ISimulatedHuman 物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="585ae-159">若要控制模擬人類看得，執行此物件上的作業。</span><span class="sxs-lookup"><span data-stu-id="585ae-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="585ae-160">例如:</span><span class="sxs-lookup"><span data-stu-id="585ae-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="585ae-161">基本範例C#主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="585ae-161">Basic Sample C# console application</span></span>

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
                        new Uri("http://169.254.227.115"),
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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="585ae-162">擴充範例C#主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="585ae-162">Extended Sample C# console application</span></span>

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
                        new Uri("http://169.254.227.115"),
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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="585ae-163">請注意，在 6 DOF 控制站上</span><span class="sxs-lookup"><span data-stu-id="585ae-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="585ae-164">在呼叫前的任何屬性上模擬的 6 DOF 控制站上的方法，您必須啟動控制器。</span><span class="sxs-lookup"><span data-stu-id="585ae-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="585ae-165">沒有這麼做的話，會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="585ae-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="585ae-166">從 Windows 10 開始可能 2019年更新，可以安裝並 SimulatedSixDofControllerStatus.Active ISimulatedSixDofController 物件上設定的 Status 屬性啟用模擬的 6 DOF 控制站。</span><span class="sxs-lookup"><span data-stu-id="585ae-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="585ae-167">在 Windows 10 年 10 月 2018年更新和更早版本，您必須另外安裝模擬的 6 DOF 控制器第一次呼叫 PerceptionSimulationDevice 工具 \Windows\System32 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="585ae-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="585ae-168">此工具的用法如下所示：</span><span class="sxs-lookup"><span data-stu-id="585ae-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="585ae-169">例如：</span><span class="sxs-lookup"><span data-stu-id="585ae-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="585ae-170">支援的動作如下：</span><span class="sxs-lookup"><span data-stu-id="585ae-170">Supported actions are:</span></span>
* <span data-ttu-id="585ae-171">我 = install</span><span class="sxs-lookup"><span data-stu-id="585ae-171">i = install</span></span>
* <span data-ttu-id="585ae-172">q = 查詢</span><span class="sxs-lookup"><span data-stu-id="585ae-172">q = query</span></span>
* <span data-ttu-id="585ae-173">r = 移除</span><span class="sxs-lookup"><span data-stu-id="585ae-173">r = remove</span></span>

<span data-ttu-id="585ae-174">支援的執行個體是：</span><span class="sxs-lookup"><span data-stu-id="585ae-174">Supported instances are:</span></span>
* <span data-ttu-id="585ae-175">1 = 的左邊的 6 DOF 控制站</span><span class="sxs-lookup"><span data-stu-id="585ae-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="585ae-176">2 = 右邊的 6 DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="585ae-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="585ae-177">（零傳回值） 的成功或失敗 （非零傳回值），會指出程序的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="585ae-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="585ae-178">若要查詢安裝在控制站 'q' 動作時，傳回的值會零 (0) (如果尚未安裝在控制器或一 （1） 如果控制器已安裝。</span><span class="sxs-lookup"><span data-stu-id="585ae-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="585ae-179">移除在 Windows 上的控制站時 10 年 10 月 2018年更新或更早版本，將它關閉透過 API 第一次，然後呼叫 PerceptionSimulationDevice 工具的狀態。</span><span class="sxs-lookup"><span data-stu-id="585ae-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="585ae-180">請注意，此工具必須以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="585ae-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="585ae-181">API 參考資料</span><span class="sxs-lookup"><span data-stu-id="585ae-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="585ae-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="585ae-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="585ae-183">描述模擬的裝置類型</span><span class="sxs-lookup"><span data-stu-id="585ae-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="585ae-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="585ae-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="585ae-185">虛構的參考裝置 PerceptionSimulationManager 的預設值</span><span class="sxs-lookup"><span data-stu-id="585ae-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="585ae-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="585ae-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="585ae-187">說明前端的追蹤器模式</span><span class="sxs-lookup"><span data-stu-id="585ae-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="585ae-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="585ae-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="585ae-189">追蹤的預設標頭。</span><span class="sxs-lookup"><span data-stu-id="585ae-189">Default Head Tracking.</span></span> <span data-ttu-id="585ae-190">這表示系統可能會選取最佳的標頭追蹤執行階段條件所根據的模式。</span><span class="sxs-lookup"><span data-stu-id="585ae-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="585ae-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="585ae-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="585ae-192">方向追蹤了唯一的標頭。</span><span class="sxs-lookup"><span data-stu-id="585ae-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="585ae-193">這表示可能不可靠，追蹤的位置，而且可能無法使用某些功能依賴前端的位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="585ae-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="585ae-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="585ae-195">位置標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="585ae-195">Positional Head Tracking.</span></span> <span data-ttu-id="585ae-196">這表示，追蹤前端的位置和方向都可靠</span><span class="sxs-lookup"><span data-stu-id="585ae-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="585ae-197">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="585ae-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="585ae-198">描述模擬的筆勢</span><span class="sxs-lookup"><span data-stu-id="585ae-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="585ae-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="585ae-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="585ae-200">用來不表示任何筆勢之 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="585ae-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="585ae-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="585ae-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="585ae-202">手指，按下動作。</span><span class="sxs-lookup"><span data-stu-id="585ae-202">A finger pressed gesture.</span></span>

<span data-ttu-id="585ae-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="585ae-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="585ae-204">手指發行動作。</span><span class="sxs-lookup"><span data-stu-id="585ae-204">A finger released gesture.</span></span>

<span data-ttu-id="585ae-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="585ae-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="585ae-206">首頁/系統筆勢。</span><span class="sxs-lookup"><span data-stu-id="585ae-206">The home/system gesture.</span></span>

<span data-ttu-id="585ae-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="585ae-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="585ae-208">最大的有效筆勢。</span><span class="sxs-lookup"><span data-stu-id="585ae-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="585ae-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="585ae-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="585ae-210">模擬的 6 DOF 控制器可能的狀態。</span><span class="sxs-lookup"><span data-stu-id="585ae-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="585ae-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span><span class="sxs-lookup"><span data-stu-id="585ae-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="585ae-212">6-DOF 控制器已關閉。</span><span class="sxs-lookup"><span data-stu-id="585ae-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="585ae-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span><span class="sxs-lookup"><span data-stu-id="585ae-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="585ae-214">6-DOF 控制器已開啟，並追蹤。</span><span class="sxs-lookup"><span data-stu-id="585ae-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="585ae-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="585ae-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="585ae-216">6-DOF 控制器為開啟狀態，但無法追蹤。</span><span class="sxs-lookup"><span data-stu-id="585ae-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="585ae-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="585ae-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="585ae-218">在模擬的 6 DOF 控制站上支援的按鈕。</span><span class="sxs-lookup"><span data-stu-id="585ae-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="585ae-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span><span class="sxs-lookup"><span data-stu-id="585ae-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="585ae-220">用來表示 [否] 按鈕之 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="585ae-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="585ae-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span><span class="sxs-lookup"><span data-stu-id="585ae-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="585ae-222">[首頁] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="585ae-222">The Home button is pressed.</span></span>

<span data-ttu-id="585ae-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span><span class="sxs-lookup"><span data-stu-id="585ae-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="585ae-224">已按下功能表按鈕。</span><span class="sxs-lookup"><span data-stu-id="585ae-224">The Menu button is pressed.</span></span>

<span data-ttu-id="585ae-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span><span class="sxs-lookup"><span data-stu-id="585ae-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="585ae-226">已按下的底框的按鈕。</span><span class="sxs-lookup"><span data-stu-id="585ae-226">The Grip button is pressed.</span></span>

<span data-ttu-id="585ae-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="585ae-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="585ae-228">已按下觸控板。</span><span class="sxs-lookup"><span data-stu-id="585ae-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="585ae-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span><span class="sxs-lookup"><span data-stu-id="585ae-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="585ae-230">[選取] 按鈕已按下。</span><span class="sxs-lookup"><span data-stu-id="585ae-230">The Select button is pressed.</span></span>

<span data-ttu-id="585ae-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="585ae-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="585ae-232">觸控板都會被接觸到。</span><span class="sxs-lookup"><span data-stu-id="585ae-232">The TouchPad is touched.</span></span>

<span data-ttu-id="585ae-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="585ae-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="585ae-234">已按下搖桿。</span><span class="sxs-lookup"><span data-stu-id="585ae-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="585ae-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span><span class="sxs-lookup"><span data-stu-id="585ae-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="585ae-236">[最大的有效] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="585ae-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="585ae-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="585ae-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="585ae-238">模擬的眼睛的校正的狀態</span><span class="sxs-lookup"><span data-stu-id="585ae-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="585ae-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="585ae-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="585ae-240">無法使用眼睛校正。</span><span class="sxs-lookup"><span data-stu-id="585ae-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="585ae-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span><span class="sxs-lookup"><span data-stu-id="585ae-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="585ae-242">眼睛有校正。</span><span class="sxs-lookup"><span data-stu-id="585ae-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="585ae-243">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="585ae-243">This is the default value.</span></span>

<span data-ttu-id="585ae-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="585ae-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="585ae-245">正在制定的眼睛。</span><span class="sxs-lookup"><span data-stu-id="585ae-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="585ae-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="585ae-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="585ae-247">眼睛需要校正。</span><span class="sxs-lookup"><span data-stu-id="585ae-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="585ae-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="585ae-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="585ae-249">追蹤精確度的指針的聯結。</span><span class="sxs-lookup"><span data-stu-id="585ae-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="585ae-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="585ae-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="585ae-251">接合不會追蹤。</span><span class="sxs-lookup"><span data-stu-id="585ae-251">The joint is not tracked.</span></span>

<span data-ttu-id="585ae-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span><span class="sxs-lookup"><span data-stu-id="585ae-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="585ae-253">推斷的聯合的位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-253">The joint position is inferred.</span></span>

<span data-ttu-id="585ae-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span><span class="sxs-lookup"><span data-stu-id="585ae-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="585ae-255">完整追蹤聯結。</span><span class="sxs-lookup"><span data-stu-id="585ae-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="585ae-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="585ae-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="585ae-257">追蹤精確度的指針的聯結。</span><span class="sxs-lookup"><span data-stu-id="585ae-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="585ae-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span><span class="sxs-lookup"><span data-stu-id="585ae-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="585ae-259">手動指關節被設定為反映已關閉的姿勢。</span><span class="sxs-lookup"><span data-stu-id="585ae-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="585ae-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span><span class="sxs-lookup"><span data-stu-id="585ae-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="585ae-261">手動指關節被設定為反映開啟的姿勢。</span><span class="sxs-lookup"><span data-stu-id="585ae-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="585ae-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span><span class="sxs-lookup"><span data-stu-id="585ae-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="585ae-263">手動指關節被設定為反映指標的姿勢。</span><span class="sxs-lookup"><span data-stu-id="585ae-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="585ae-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span><span class="sxs-lookup"><span data-stu-id="585ae-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="585ae-265">手動指關節被設定為反映 pinching 姿勢。</span><span class="sxs-lookup"><span data-stu-id="585ae-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="585ae-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span><span class="sxs-lookup"><span data-stu-id="585ae-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="585ae-267">SimulatedHandPose 的最大有效的值。</span><span class="sxs-lookup"><span data-stu-id="585ae-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="585ae-268">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="585ae-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="585ae-269">描述播放的狀態。</span><span class="sxs-lookup"><span data-stu-id="585ae-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="585ae-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="585ae-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="585ae-271">記錄目前已停止，且準備好進行播放。</span><span class="sxs-lookup"><span data-stu-id="585ae-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="585ae-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="585ae-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="585ae-273">目前正在播放錄製。</span><span class="sxs-lookup"><span data-stu-id="585ae-273">The recording is currently playing.</span></span>

<span data-ttu-id="585ae-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="585ae-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="585ae-275">目前已暫停錄製。</span><span class="sxs-lookup"><span data-stu-id="585ae-275">The recording is currently paused.</span></span>

<span data-ttu-id="585ae-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="585ae-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="585ae-277">記錄已到達結尾。</span><span class="sxs-lookup"><span data-stu-id="585ae-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="585ae-278">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="585ae-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="585ae-279">說明 3 個元件的向量，可能會說明了點或在 3D 空間中的向量。</span><span class="sxs-lookup"><span data-stu-id="585ae-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="585ae-280">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="585ae-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="585ae-281">向量的 X 元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-281">The X component of the vector.</span></span>

<span data-ttu-id="585ae-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="585ae-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="585ae-283">向量的 Y 元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-283">The Y component of the vector.</span></span>

<span data-ttu-id="585ae-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="585ae-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="585ae-285">向量的 Z 元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-285">The Z component of the vector.</span></span>

<span data-ttu-id="585ae-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="585ae-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="585ae-287">建構新的 Vector3。</span><span class="sxs-lookup"><span data-stu-id="585ae-287">Construct a new Vector3.</span></span>

<span data-ttu-id="585ae-288">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-288">Parameters</span></span>
* <span data-ttu-id="585ae-289">x 軸向量的 x 元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="585ae-290">向量的 y y 元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="585ae-291">向量的 z z 元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="585ae-292">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="585ae-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="585ae-293">描述的 3 個元件的旋轉。</span><span class="sxs-lookup"><span data-stu-id="585ae-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="585ae-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="585ae-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="585ae-295">輪替的字幅元件向下繞著 X 軸。</span><span class="sxs-lookup"><span data-stu-id="585ae-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="585ae-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="585ae-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="585ae-297">繞右繞著 Y 軸旋轉的元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="585ae-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="585ae-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="585ae-299">向右繞著 Z 軸旋轉的向前復原元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="585ae-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="585ae-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="585ae-301">建構新的 Rotation3。</span><span class="sxs-lookup"><span data-stu-id="585ae-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="585ae-302">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-302">Parameters</span></span>
* <span data-ttu-id="585ae-303">字距-旋轉的字幅元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="585ae-304">繞-旋轉的繞元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="585ae-305">復原-旋轉的向前復原元件。</span><span class="sxs-lookup"><span data-stu-id="585ae-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="585ae-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="585ae-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="585ae-307">描述模擬手動聯結的組態。</span><span class="sxs-lookup"><span data-stu-id="585ae-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="585ae-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span><span class="sxs-lookup"><span data-stu-id="585ae-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="585ae-309">聯合的位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-309">The position of the joint.</span></span>

<span data-ttu-id="585ae-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span><span class="sxs-lookup"><span data-stu-id="585ae-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="585ae-311">聯合的旋轉角度。</span><span class="sxs-lookup"><span data-stu-id="585ae-311">The rotation of the joint.</span></span>

<span data-ttu-id="585ae-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="585ae-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="585ae-313">聯合追蹤精確度。</span><span class="sxs-lookup"><span data-stu-id="585ae-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="585ae-314">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="585ae-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="585ae-315">描述檢視範圍，通常使用相機。</span><span class="sxs-lookup"><span data-stu-id="585ae-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="585ae-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="585ae-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="585ae-317">位在範圍中包含的最小距離。</span><span class="sxs-lookup"><span data-stu-id="585ae-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="585ae-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="585ae-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="585ae-319">包含位在範圍中最大距離。</span><span class="sxs-lookup"><span data-stu-id="585ae-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="585ae-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="585ae-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="585ae-321">水平視野的範圍，以弧度為單位 （大於或等於 PI）。</span><span class="sxs-lookup"><span data-stu-id="585ae-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="585ae-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="585ae-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="585ae-323">水平視野來檢視垂直欄位數的比率。</span><span class="sxs-lookup"><span data-stu-id="585ae-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="585ae-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="585ae-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="585ae-325">產生用來控制裝置的封包的根目錄。</span><span class="sxs-lookup"><span data-stu-id="585ae-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="585ae-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="585ae-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="585ae-327">擷取解譯模擬的人類和模擬的世界的模擬的裝置物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="585ae-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="585ae-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="585ae-329">擷取控制模擬人類看得的物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="585ae-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="585ae-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="585ae-331">模擬重設為其預設狀態。</span><span class="sxs-lookup"><span data-stu-id="585ae-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="585ae-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="585ae-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="585ae-333">描述可解譯模擬的世界和模擬裝置的介面</span><span class="sxs-lookup"><span data-stu-id="585ae-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="585ae-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="585ae-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="585ae-335">從模擬裝置中擷取的標頭追蹤器。</span><span class="sxs-lookup"><span data-stu-id="585ae-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="585ae-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="585ae-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="585ae-337">擷取從模擬裝置的手動追蹤程式。</span><span class="sxs-lookup"><span data-stu-id="585ae-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="585ae-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="585ae-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="585ae-339">設定模擬的裝置，以符合所提供的裝置類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="585ae-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="585ae-340">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-340">Parameters</span></span>
* <span data-ttu-id="585ae-341">類型-新的模擬裝置類型</span><span class="sxs-lookup"><span data-stu-id="585ae-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="585ae-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="585ae-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="585ae-343">描述模擬的裝置，追蹤的模擬人類看得標頭部分的介面。</span><span class="sxs-lookup"><span data-stu-id="585ae-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="585ae-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="585ae-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="585ae-345">擷取並設定目前的前端的追蹤器模式。</span><span class="sxs-lookup"><span data-stu-id="585ae-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="585ae-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="585ae-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="585ae-347">描述追蹤的模擬人類的模擬裝置的部分介面</span><span class="sxs-lookup"><span data-stu-id="585ae-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="585ae-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="585ae-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="585ae-349">擷取與世界相關節點的位置，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="585ae-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="585ae-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="585ae-351">擷取和設定模擬的手動追蹤器的位置相對於標頭的中心。</span><span class="sxs-lookup"><span data-stu-id="585ae-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="585ae-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="585ae-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="585ae-353">擷取並設定模擬的手動追蹤器的向下的字幅。</span><span class="sxs-lookup"><span data-stu-id="585ae-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="585ae-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="585ae-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="585ae-355">會擷取和設定是否會忽略模擬的手動追蹤器的範圍。</span><span class="sxs-lookup"><span data-stu-id="585ae-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="585ae-356">當被忽略，雙手永遠會顯示。</span><span class="sxs-lookup"><span data-stu-id="585ae-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="585ae-357">不忽略 （預設值） 時手才看得到它們時手動追蹤器的範圍內。</span><span class="sxs-lookup"><span data-stu-id="585ae-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="585ae-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="585ae-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="585ae-359">擷取並設定用來判斷是否模擬的手動追蹤器看到實際操作的範圍屬性。</span><span class="sxs-lookup"><span data-stu-id="585ae-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="585ae-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="585ae-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="585ae-361">用來控制模擬人類看得上方層級的介面。</span><span class="sxs-lookup"><span data-stu-id="585ae-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="585ae-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="585ae-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="585ae-363">擷取和設定節點的位置與相關的世界裡，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="585ae-364">位置相對應的人力英呎的中心點。</span><span class="sxs-lookup"><span data-stu-id="585ae-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="585ae-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="585ae-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="585ae-366">擷取，並在世界中設定模擬的人臉的方向。</span><span class="sxs-lookup"><span data-stu-id="585ae-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="585ae-367">0 的弧度為單位，面臨下負 Z 軸。</span><span class="sxs-lookup"><span data-stu-id="585ae-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="585ae-368">正數的弧度順時針旋轉繞 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="585ae-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="585ae-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="585ae-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="585ae-370">擷取和設定的高度，模擬的人，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="585ae-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="585ae-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="585ae-372">擷取模擬人類看得在左邊。</span><span class="sxs-lookup"><span data-stu-id="585ae-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="585ae-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="585ae-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="585ae-374">擷取的模擬人類的右側。</span><span class="sxs-lookup"><span data-stu-id="585ae-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="585ae-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="585ae-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="585ae-376">擷取模擬人類看得標的頭。</span><span class="sxs-lookup"><span data-stu-id="585ae-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="585ae-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="585ae-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="585ae-378">將模擬人類看得移動相對於其目前的位置，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="585ae-379">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-379">Parameters</span></span>
* <span data-ttu-id="585ae-380">轉譯-若要移動，相對於目前的位置轉譯。</span><span class="sxs-lookup"><span data-stu-id="585ae-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="585ae-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="585ae-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="585ae-382">旋轉模擬的人類相對於其目前的方向，順時針方向繞 Y 軸</span><span class="sxs-lookup"><span data-stu-id="585ae-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="585ae-383">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-383">Parameters</span></span>
* <span data-ttu-id="585ae-384">弧度為單位-要繞著 Y 軸旋轉的量。</span><span class="sxs-lookup"><span data-stu-id="585ae-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="585ae-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="585ae-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="585ae-386">轉換至 ISimulatedHuman2 ISimulatedHuman 會提供額外的屬性</span><span class="sxs-lookup"><span data-stu-id="585ae-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="585ae-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span><span class="sxs-lookup"><span data-stu-id="585ae-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="585ae-388">擷取左的 6 DOF 控制站。</span><span class="sxs-lookup"><span data-stu-id="585ae-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="585ae-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span><span class="sxs-lookup"><span data-stu-id="585ae-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="585ae-390">擷取正確的 6 DOF 控制站。</span><span class="sxs-lookup"><span data-stu-id="585ae-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="585ae-391">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="585ae-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="585ae-392">描述模擬人類看得交介面</span><span class="sxs-lookup"><span data-stu-id="585ae-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="585ae-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="585ae-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="585ae-394">擷取與世界相關節點的位置，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="585ae-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="585ae-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="585ae-396">擷取和設定相對於人類，模擬的左手邊的位置以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="585ae-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="585ae-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="585ae-398">會擷取和設定是否手形目前已啟動。</span><span class="sxs-lookup"><span data-stu-id="585ae-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="585ae-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="585ae-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="585ae-400">擷取目前可看見 （亦即，它是 HandTracker 可以偵測到的位置） SimulatedDevice 手形是否。</span><span class="sxs-lookup"><span data-stu-id="585ae-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="585ae-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="585ae-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="585ae-402">它會顯示以 SimulatedDevice，請移動手形。</span><span class="sxs-lookup"><span data-stu-id="585ae-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="585ae-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="585ae-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="585ae-404">移動模擬的左手邊的位置，相對於其目前的位置，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="585ae-405">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-405">Parameters</span></span>
* <span data-ttu-id="585ae-406">轉譯-要轉移模擬的手的數量。</span><span class="sxs-lookup"><span data-stu-id="585ae-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="585ae-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="585ae-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="585ae-408">執行使用模擬的手動動作。</span><span class="sxs-lookup"><span data-stu-id="585ae-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="585ae-409">如果啟用了 hand，它只會由系統偵測。</span><span class="sxs-lookup"><span data-stu-id="585ae-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="585ae-410">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-410">Parameters</span></span>
* <span data-ttu-id="585ae-411">筆勢-要執行的筆勢。</span><span class="sxs-lookup"><span data-stu-id="585ae-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="585ae-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="585ae-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="585ae-413">轉換至 ISimulatedHand2 ISimulatedHand，會提供額外的屬性。</span><span class="sxs-lookup"><span data-stu-id="585ae-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="585ae-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span><span class="sxs-lookup"><span data-stu-id="585ae-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="585ae-415">擷取或設定模擬的左手邊的旋轉。</span><span class="sxs-lookup"><span data-stu-id="585ae-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="585ae-416">正數時尋找沿著軸順時針旋轉弧度為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="585ae-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="585ae-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="585ae-418">轉換至 ISimulatedHand3 ISimulatedHand 會提供額外的屬性</span><span class="sxs-lookup"><span data-stu-id="585ae-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="585ae-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="585ae-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="585ae-420">取得指定的聯合的聯合組態。</span><span class="sxs-lookup"><span data-stu-id="585ae-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="585ae-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="585ae-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="585ae-422">設定指定的聯合的聯合組態。</span><span class="sxs-lookup"><span data-stu-id="585ae-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="585ae-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="585ae-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="585ae-424">設定已知的姿勢與選擇性旗標來以動畫顯示手形。</span><span class="sxs-lookup"><span data-stu-id="585ae-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="585ae-425">注意： 建立動畫不會導致立即反映其最終的聯合組態的接點。</span><span class="sxs-lookup"><span data-stu-id="585ae-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="585ae-426">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="585ae-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="585ae-427">描述模擬人類的前端介面。</span><span class="sxs-lookup"><span data-stu-id="585ae-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="585ae-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="585ae-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="585ae-429">擷取與世界相關節點的位置，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="585ae-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="585ae-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="585ae-431">擷取模擬的標頭的旋轉。</span><span class="sxs-lookup"><span data-stu-id="585ae-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="585ae-432">正數時尋找沿著軸順時針旋轉弧度為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="585ae-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="585ae-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="585ae-434">擷取模擬標頭的直徑。</span><span class="sxs-lookup"><span data-stu-id="585ae-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="585ae-435">此值用以判斷前端的中心 （旋轉的點）。</span><span class="sxs-lookup"><span data-stu-id="585ae-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="585ae-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="585ae-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="585ae-437">旋轉模擬的標頭，相對於其目前的旋轉角度。</span><span class="sxs-lookup"><span data-stu-id="585ae-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="585ae-438">正數時尋找沿著軸順時針旋轉弧度為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="585ae-439">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-439">Parameters</span></span>
* <span data-ttu-id="585ae-440">旋轉-要旋轉的量。</span><span class="sxs-lookup"><span data-stu-id="585ae-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="585ae-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="585ae-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="585ae-442">轉換至 ISimulatedHead2 ISimulatedHead 會提供額外的屬性</span><span class="sxs-lookup"><span data-stu-id="585ae-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="585ae-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span><span class="sxs-lookup"><span data-stu-id="585ae-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="585ae-444">擷取模擬人類看得的角度來看。</span><span class="sxs-lookup"><span data-stu-id="585ae-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="585ae-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="585ae-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="585ae-446">描述 6 DOF 控制器，以模擬人類與相關聯的介面。</span><span class="sxs-lookup"><span data-stu-id="585ae-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="585ae-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="585ae-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="585ae-448">擷取與世界相關節點的位置，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="585ae-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span><span class="sxs-lookup"><span data-stu-id="585ae-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="585ae-450">擷取或設定控制器的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="585ae-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="585ae-451">控制器狀態必須設定為值，除了關閉之前呼叫任何移動、 旋轉或按下按鈕將會成功。</span><span class="sxs-lookup"><span data-stu-id="585ae-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="585ae-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span><span class="sxs-lookup"><span data-stu-id="585ae-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="585ae-453">擷取或設定相對於人類，模擬的控制站的位置以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="585ae-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span><span class="sxs-lookup"><span data-stu-id="585ae-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="585ae-455">擷取或設定模擬的控制站的方向。</span><span class="sxs-lookup"><span data-stu-id="585ae-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="585ae-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="585ae-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="585ae-457">移動模擬的控制站的位置，相對於其目前的位置，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="585ae-458">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-458">Parameters</span></span>
* <span data-ttu-id="585ae-459">轉譯-要轉移的模擬的控制站的數量。</span><span class="sxs-lookup"><span data-stu-id="585ae-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="585ae-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="585ae-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="585ae-461">模擬的控制站上，按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="585ae-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="585ae-462">如果控制器已啟用，它只會由系統偵測。</span><span class="sxs-lookup"><span data-stu-id="585ae-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="585ae-463">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-463">Parameters</span></span>
* <span data-ttu-id="585ae-464">按鈕-按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="585ae-464">button - The button to press.</span></span>

<span data-ttu-id="585ae-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="585ae-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="585ae-466">放開按鈕，以在模擬的控制站上。</span><span class="sxs-lookup"><span data-stu-id="585ae-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="585ae-467">如果控制器已啟用，它只會由系統偵測。</span><span class="sxs-lookup"><span data-stu-id="585ae-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="585ae-468">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-468">Parameters</span></span>
* <span data-ttu-id="585ae-469">按鈕-[發行] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="585ae-469">button - The button to release.</span></span>

<span data-ttu-id="585ae-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="585ae-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="585ae-471">取得上模擬的控制器的觸控模擬手指的位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="585ae-472">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-472">Parameters</span></span>
* <span data-ttu-id="585ae-473">x-手指水平位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="585ae-474">y 手指-垂直位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="585ae-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="585ae-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="585ae-476">設定模擬的控制器的觸控模擬手指的位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="585ae-477">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-477">Parameters</span></span>
* <span data-ttu-id="585ae-478">x-手指水平位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="585ae-479">y 手指-垂直位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="585ae-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="585ae-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="585ae-481">其他屬性和方法都可以透過轉型至 ISimulatedSixDofController2 ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="585ae-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="585ae-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="585ae-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="585ae-483">取得模擬的搖桿，在模擬的控制站上的位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="585ae-484">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-484">Parameters</span></span>
* <span data-ttu-id="585ae-485">x-搖桿水平位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="585ae-486">y 搖桿-垂直位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="585ae-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="585ae-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="585ae-488">模擬的控制站上設定模擬搖桿的位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="585ae-489">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-489">Parameters</span></span>
* <span data-ttu-id="585ae-490">x-搖桿水平位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="585ae-491">y 搖桿-垂直位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="585ae-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="585ae-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="585ae-493">擷取或設定的模擬的控制站的剩餘電量。</span><span class="sxs-lookup"><span data-stu-id="585ae-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="585ae-494">值必須大於 0.0 且小於或等於 100.0。</span><span class="sxs-lookup"><span data-stu-id="585ae-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="585ae-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="585ae-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="585ae-496">描述模擬人類看得的角度來看的介面。</span><span class="sxs-lookup"><span data-stu-id="585ae-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="585ae-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span><span class="sxs-lookup"><span data-stu-id="585ae-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="585ae-498">擷取模擬的眼睛的旋轉角度。</span><span class="sxs-lookup"><span data-stu-id="585ae-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="585ae-499">正數時尋找沿著軸順時針旋轉弧度為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="585ae-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="585ae-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="585ae-501">旋轉模擬的眼睛，相對於其目前的旋轉角度。</span><span class="sxs-lookup"><span data-stu-id="585ae-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="585ae-502">正數時尋找沿著軸順時針旋轉弧度為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="585ae-503">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-503">Parameters</span></span>
* <span data-ttu-id="585ae-504">旋轉-要旋轉的量。</span><span class="sxs-lookup"><span data-stu-id="585ae-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="585ae-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="585ae-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="585ae-506">擷取或設定模擬眼睛的校正狀態。</span><span class="sxs-lookup"><span data-stu-id="585ae-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="585ae-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="585ae-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="585ae-508">擷取與世界相關節點的位置，以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="585ae-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="585ae-509">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="585ae-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="585ae-510">播放，載入與單一的錄製內容互動的介面。</span><span class="sxs-lookup"><span data-stu-id="585ae-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="585ae-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="585ae-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="585ae-512">擷取錄製中的資料類型的清單。</span><span class="sxs-lookup"><span data-stu-id="585ae-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="585ae-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="585ae-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="585ae-514">擷取記錄的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="585ae-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="585ae-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="585ae-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="585ae-516">開始播放。</span><span class="sxs-lookup"><span data-stu-id="585ae-516">Start the playback.</span></span> <span data-ttu-id="585ae-517">如果記錄已暫停，播放會繼續從暫停的位置;如果停止，將會開頭開始播放。</span><span class="sxs-lookup"><span data-stu-id="585ae-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="585ae-518">如果已播放，則會忽略這個呼叫。</span><span class="sxs-lookup"><span data-stu-id="585ae-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="585ae-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="585ae-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="585ae-520">暫停播放其目前的位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="585ae-521">如果停止錄製時，會忽略呼叫。</span><span class="sxs-lookup"><span data-stu-id="585ae-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="585ae-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="585ae-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="585ae-523">（在從一開始的 100 奈秒間隔） 會設法在指定的時間錄製與暫停在該位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="585ae-524">如果記錄結尾以外的位置時，它會暫停在最後一個畫面格。</span><span class="sxs-lookup"><span data-stu-id="585ae-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="585ae-525">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-525">Parameters</span></span>
* <span data-ttu-id="585ae-526">刻度-要搜尋的時間。</span><span class="sxs-lookup"><span data-stu-id="585ae-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="585ae-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="585ae-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="585ae-528">停止播放和重設到開頭的位置。</span><span class="sxs-lookup"><span data-stu-id="585ae-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="585ae-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="585ae-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="585ae-530">在播放期間接收的狀態變更的介面。</span><span class="sxs-lookup"><span data-stu-id="585ae-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="585ae-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="585ae-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="585ae-532">當 ISimulationRecording 播放狀態變更時呼叫。</span><span class="sxs-lookup"><span data-stu-id="585ae-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="585ae-533">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-533">Parameters</span></span>
* <span data-ttu-id="585ae-534">newState-錄製的新狀態。</span><span class="sxs-lookup"><span data-stu-id="585ae-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="585ae-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="585ae-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="585ae-536">建立 Perception 模擬物件的根物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="585ae-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="585ae-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="585ae-538">產生模擬的封包，並將其傳遞至所提供的接收的物件上建立。</span><span class="sxs-lookup"><span data-stu-id="585ae-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="585ae-539">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-539">Parameters</span></span>
* <span data-ttu-id="585ae-540">接收-將會收到所有產生的封包的接收。</span><span class="sxs-lookup"><span data-stu-id="585ae-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="585ae-541">傳回值</span><span class="sxs-lookup"><span data-stu-id="585ae-541">Return value</span></span>

<span data-ttu-id="585ae-542">建立的管理員。</span><span class="sxs-lookup"><span data-stu-id="585ae-542">The created Manager.</span></span>

<span data-ttu-id="585ae-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="585ae-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="585ae-544">建立儲存在指定路徑的檔案中的所有接收的封包的接收。</span><span class="sxs-lookup"><span data-stu-id="585ae-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="585ae-545">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-545">Parameters</span></span>
* <span data-ttu-id="585ae-546">path-建立檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="585ae-546">path - The path of the file to create.</span></span>

<span data-ttu-id="585ae-547">傳回值</span><span class="sxs-lookup"><span data-stu-id="585ae-547">Return value</span></span>

<span data-ttu-id="585ae-548">建立的接收器。</span><span class="sxs-lookup"><span data-stu-id="585ae-548">The created sink.</span></span>

<span data-ttu-id="585ae-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="585ae-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="585ae-550">從指定的檔案載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="585ae-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="585ae-551">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-551">Parameters</span></span>
* <span data-ttu-id="585ae-552">路徑： 要載入之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="585ae-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="585ae-553">處理站-錄製用於建立 ISimulationStreamSink 時所需的處理站。</span><span class="sxs-lookup"><span data-stu-id="585ae-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="585ae-554">傳回值</span><span class="sxs-lookup"><span data-stu-id="585ae-554">Return value</span></span>

<span data-ttu-id="585ae-555">載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="585ae-555">The loaded recording.</span></span>

<span data-ttu-id="585ae-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory，Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="585ae-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="585ae-557">從指定的檔案載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="585ae-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="585ae-558">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-558">Parameters</span></span>
* <span data-ttu-id="585ae-559">路徑： 要載入之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="585ae-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="585ae-560">處理站-錄製用於建立 ISimulationStreamSink 時所需的處理站。</span><span class="sxs-lookup"><span data-stu-id="585ae-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="585ae-561">回呼-regrading 錄製的狀態更新接收的回呼。</span><span class="sxs-lookup"><span data-stu-id="585ae-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="585ae-562">傳回值</span><span class="sxs-lookup"><span data-stu-id="585ae-562">Return value</span></span>

<span data-ttu-id="585ae-563">載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="585ae-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="585ae-564">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="585ae-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="585ae-565">說明不同類型的資料流資料。</span><span class="sxs-lookup"><span data-stu-id="585ae-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="585ae-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="585ae-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="585ae-567">用來表示任何資料流的資料類型之 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="585ae-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="585ae-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="585ae-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="585ae-569">Stream 的位置和方向的標頭的相關資料。</span><span class="sxs-lookup"><span data-stu-id="585ae-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="585ae-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="585ae-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="585ae-571">Stream 的位置和指針的筆勢的相關資料。</span><span class="sxs-lookup"><span data-stu-id="585ae-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="585ae-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="585ae-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="585ae-573">Stream 的空間的對應環境的相關資料。</span><span class="sxs-lookup"><span data-stu-id="585ae-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="585ae-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="585ae-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="585ae-575">Stream 的校正裝置的相關資料。</span><span class="sxs-lookup"><span data-stu-id="585ae-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="585ae-576">在遠端模式系統只接受校正封包。</span><span class="sxs-lookup"><span data-stu-id="585ae-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="585ae-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="585ae-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="585ae-578">關於裝置的環境資料的 Stream。</span><span class="sxs-lookup"><span data-stu-id="585ae-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="585ae-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="585ae-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="585ae-580">用來表示所有記錄的資料類型之 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="585ae-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="585ae-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="585ae-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="585ae-582">接收資料封包從模擬的資料流物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="585ae-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="585ae-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="585ae-584">接收單一封包，也就是在內部具類型和版本設定。</span><span class="sxs-lookup"><span data-stu-id="585ae-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="585ae-585">參數</span><span class="sxs-lookup"><span data-stu-id="585ae-585">Parameters</span></span>
* <span data-ttu-id="585ae-586">length-將封包的長度。</span><span class="sxs-lookup"><span data-stu-id="585ae-586">length - The length of the packet.</span></span>
* <span data-ttu-id="585ae-587">封包-封包的資料。</span><span class="sxs-lookup"><span data-stu-id="585ae-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="585ae-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="585ae-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="585ae-589">建立 ISimulationStreamSink 物件。</span><span class="sxs-lookup"><span data-stu-id="585ae-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="585ae-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="585ae-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="585ae-591">建立 ISimulationStreamSink 的單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="585ae-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="585ae-592">傳回值</span><span class="sxs-lookup"><span data-stu-id="585ae-592">Return value</span></span>

<span data-ttu-id="585ae-593">建立的接收器。</span><span class="sxs-lookup"><span data-stu-id="585ae-593">The created sink.</span></span>
