---
title: 多使用者功能教學課程 - 2。 準備 Unity 以進行開發
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031234"
---
# <a name="2-getting-unity-ready-for-development"></a>2.準備 Unity 以進行開發

在本教學課程中，您將了解如何準備和設定 Unity 來開發應用程式，包括匯入混合實境工具組、設定組建設定，以及準備您的場景。

## <a name="objectives"></a>目標

* 設定 Unity 以用於應用程式開發
* 匯入混合實境工具組
* 準備您的專案場景

## <a name="instructions"></a>指示

1. 按一下[這裡](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)，下載並儲存混合實境工具組的基礎 Unity 套件。

2. 在 Unity 中，按一下 [資產] 功能表並選取 [匯入套件]，然後按一下 [自訂套件]。

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 從步驟 1 所提供的連結中，選取您剛才下載的 Unity 套件。 當 Unity 中出現匯入快顯視窗時，按一下 [匯入] 按鈕以開始匯入 MRTK。 這可能需要幾分鐘的時間。

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >下載的套件會位在您的本機資料夾中，也就是您儲存該檔案的地方。 上圖不會說明您套件的所在位置。

    匯入套件之後，應該會出現 [MRTK 專案設定程式] 視窗。 如果沒有，請在 Unity 功能表中選取 [混合現實工具組] > [公用程式] > [設定 Unity 專案] 加以開啟。

    在 [MRTK 專案設定程式] 視窗中，展開 [修改設定] 區段，取消勾選 [啟用適用於 Unity 的 MSBuild] 核取方塊，確定已勾選所有其他選項，然後按一下 [套用] 按鈕來套用設定。

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > 適用於 Unity 的 MSBuild 可能不支援您將使用的所有 SDK，且在啟用之後，可能會很難停用。 因此，強烈建議您不要啟用適用於 Unity 的 MSBuild。
    
4. 建立新場景。 這可以藉由按一下 [檔案] 並選取 [新增場景] 來完成。 將其儲存為 HLSharedProjectMain。

5. 在 [混合時竟工具組] 底下，按一下 [新增至場景並設定]。

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完成後，請從階層中選取 [混合現實工具組 (MRTK)]。 在 [偵測器] 面板中，將 MRTK 組態設定檔變更為 DefaultHoloLens2ConfigurationProfile。

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. 從階層中選取 [混合實境工具組 (MRTK)]。 在偵測器面板中尋找 [混合實境工具組指令碼]，然後按 [複製與自訂] 按鈕，如下圖所示。  此時會出現一個快顯示窗，在快顯功能表中選取 [複製] 選項。

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. 如果您想要隱藏診斷視窗，請向下捲動並取消核取 [啟用診斷系統]。 建議您在應用程式開發期間讓診斷視窗保持啟用狀態，以監視效能，然後在生產環境或應用程式示範期間將其停用。 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. 按 ctrl + shift + B，或移至 [檔案] -> [組建設定]，以開啟組建設定。 請注意，程式目前可在 PC、Mac 和 Linux 獨立平台下設定。 若是進行 HoloLens 2 開發，請將平台設定為通用 Windows 平台。 選取該項目，然後按一下 [切換平台]。

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. 完成後，按一下名為 [新增開啟場景] 的方塊。 現在，移至偵測器面板，並確定已核取 [支援的虛擬實境] 右邊的核取方塊 (如下圖所示)。 此外，也請確定 [場景/HLSharedProjectMain] 旁的核取方塊也已核取，如下圖所示。

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. 在 [偵測器] 面板的 [發佈設定] 區段下，向下捲動至 [功能]，並確定已核取下列核取方塊：

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. 匯入列出的自訂套件：

    * [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (2.1.1 版)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >如需有關如何為 Azure Spatial Anchors 設定 Unity 專案的提示，您可以參閱[開始使用 Azure Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) 教學課程，這是 [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) 教學課程系列的一部分。


13. 在 [專案] 面板中，移至 [Prefabs] 資料夾。 在下列步驟中，您將會在場景中實作幾個 Prefab。 在 [Prefabs] 資料夾中，按一下 [Debug Window] Prefab 並將其拖曳至階層中。 完成後，依序按一下 [檔案] 和 [儲存] 或按 Ctrl + S 來儲存專案。

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    您可能會注意到當您按一下 Prefab 時，會出現快顯視窗來詢問您有關 TMP Essentials 的資訊。 請視需要按一下 [匯入 TMP Essentials]。 如果出現此快顯視窗，表示您可能需要從階層中刪除 Prefab，然後將其重新拖曳到您的階層中，以避免潛在的文字相關錯誤。

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>恭喜！

您的 Unity 專案現在已準備好用於 Photon。 在接下來的教學課程中，我們將以這個場景和 Unity 專案為基礎來建立完整的共用體驗。

[下一個教學課程：3.連線多個使用者](mrlearning-sharing(photon)-ch3.md)
