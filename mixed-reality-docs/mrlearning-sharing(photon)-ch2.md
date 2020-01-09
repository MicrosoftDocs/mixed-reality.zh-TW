---
title: 多使用者功能教學課程-2。 讓 Unity 準備好進行開發
description: 完成此課程，以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 6840bcc583fe3e42dcaa6f42e71098f4dbe76f4c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334311"
---
# <a name="2-getting-unity-ready-for-development"></a>2. 讓 Unity 準備好進行開發

在本教學課程中，您將瞭解如何為應用程式開發準備和設定 Unity，包括匯入混合現實工具組、設定組建設定，以及準備您的場景。

## <a name="objectives"></a>目標

* 設定 Unity 以進行應用程式開發
* 匯入混合實境工具組
* 準備您的專案場景

## <a name="instructions"></a>指示

1. 按一下這裡，下載並儲存 Mixed Reality 工具組 Foundation unity 封裝[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)

2. 在 Unity 中，按一下 [資產] 功能表並選取 [匯入套件]，然後按一下 [自訂套件]。

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 從步驟1所提供的連結中，選取您剛才下載的 Unity 套件。 在 Unity 中出現 [匯入] 快顯視窗後，按一下 [匯入] 按鈕以開始匯入 MRTK。 這可能需要數分鐘的時間。

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >下載的套件位於您的本機資料夾中，您已在其中儲存檔案。 上圖不會說明您會在何處找到封裝。

4. 建立新場景。 這可以藉由按一下 [檔案] 並選取 [新增場景] 來完成。 將它儲存為 HLSharedProjectMain。

    您可能會收到類似下圖的快顯視窗。 現在，請按一下 [否]。
    ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. 在 [混合式現實工具組] 底下，按一下 [新增至場景] 並設定。

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完成之後，就會出現新的設定檔案，讓您選擇自訂設定檔。

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. 從階層中選取 [混合現實工具組（MRTK）]。 在 [偵測器] 面板中，尋找 Mixed Reality 工具組腳本，然後按下圖所示的 [複製 & 自訂] 按鈕。  這會出現一個 pop，然後在快顯功能表中選取 [複製] 選項。

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. 如果您想要隱藏 [診斷] 視窗，請向下選取並取消核取 [啟用診斷系統]。 建議您在應用程式開發期間讓診斷視窗保持啟用狀態，以監視效能，然後在生產或應用程式示範期間將它停用。 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. 按 ctrl + shift + B，或移至 [檔案-> 組建設定]，以開啟組建設定。 請注意，程式目前是在電腦、Mac 和 Linux 獨立平臺下設定。 若是 HoloLens 2 開發，請將平臺設定為通用 Windows 平臺。 選取該檔案，然後按一下 [切換平臺]。

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. 完成後，按一下名為 [新增] [開啟場景] 的方塊。 現在，移至 [偵測器] 面板，並確定已核取 [支援的虛擬實境] 右邊的核取方塊（如下圖所示）。 此外，也請確定 [場景/HLSharedProjectMain] 旁的核取方塊也已核取，如下圖所示。

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. 在 [偵測器] 面板的 [發行設定] 區段下，向下流覽至 [功能]，並確定已將下列核取方塊標記為：

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. 匯入列出的自訂套件：

    a. [HoloLens2. GettingStarted 教學課程. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    b。 [HoloLens2. MultiUserCapabilities 教學課程. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    >如果您已完成開始使用[教學](mrlearning-base-ch1.md)課程，您的電腦上可能仍會有名為 GettingStarted 的 unity 套件。 _2.1.0.0. unitypackage_ 。 若是如此，您可以略過下載上述步驟中所列的資產。

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. 在 [專案] 面板中，移至 [Prefabs] 資料夾。 在下列步驟中，您將會在場景中執行幾個 prefabs。 在 [Prefabs] 資料夾中，按一下 [prefab]、[Debug] 視窗並拖曳至階層中。 完成後，依序按一下 [檔案] 和 [儲存] 或按 Ctrl + S 來儲存專案。

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    您可能會注意到當您按一下 prefab 時，快顯視窗會詢問您有關 TMP Essentials 的資訊。 視需要按一下 [匯入 TMP Essentials]。 如果出現這個快顯視窗，您可能需要從階層中刪除 prefab，然後將它重新拖曳到您的階層中，以避免潛在的文字相關錯誤。

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>恭喜您

您的 Unity 專案現在已準備好進行 Photon。 在接下來的教學課程中，我們將以這個場景和 Unity 專案為完整的共用體驗來建立。

[下一個教學課程： 3. 連接多個使用者](mrlearning-sharing(photon)-ch3.md)
