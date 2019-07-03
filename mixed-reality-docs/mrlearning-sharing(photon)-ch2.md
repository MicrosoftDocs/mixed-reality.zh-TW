# <a name="getting-unity-ready-for-development"></a>準備 Unity 進行開發 

在本教學課程中，我們了解如何準備及設定 Unity 以應用程式開發，包括匯入混合實境工具組、 設定組建設定，並準備我們的場景。

目標：

- 設定 Unity 應用程式開發

- 匯入混合實境工具組

- 準備您的專案場景

### <a name="instructions"></a>指示

1. 下載並儲存混合實境 Toolkit unity 套件，依序按一下[這裡。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. 在 Unity 中，按一下 [資產] 功能表並選取匯入封裝，然後按一下自訂套件。

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 選取您從步驟 1 中所提供的連結下載 Unity 套件。 一旦匯入快顯視窗會出現在 Unity 中，按一下 匯入 按鈕，以開始匯入。 匯入 MRTK 可能需要幾分鐘的時間。

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 注意:下載的封裝是在您儲存檔案的位置的本機資料夾中。 上圖未顯示您將在其中找到封裝。

4. 建立新的場景。 T 可按一下檔案，然後選取新的場景 」）。 存 HLSharedProjectMain 場景。

> 注意： 您可能會收到看起來類似下面的影像的快顯視窗。 現在，請按一下 [否]。
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. 在混合實境工具箱項目，按一下 新增至場景，然後設定。

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完成後完成時，新的組態檔隨即出現，讓您選擇以自訂設定檔。 按一下 複製和自訂。

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. 向下捲動，並取消核取 啟用 Siagnostics 系統，如果您想要隱藏 diagnostics 視窗。 我們建議您保持 [diagnostics] 視窗來監視效能，應用程式開發期間啟用和停用在生產環境或應用程式的示範期間。 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. 開啟的組建設定，請按 control + shift + B，或前往 檔案-> 組建設定。 請注意，此程式目前設定在 PC、 Mac 和 Linux 的獨立平台。 HoloLens 2 開發，會設定為通用 Windows 平台的平台。 選取它，然後按一下 切換平台。![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 完成後，按一下 [新增開啟場景] 方塊。 現在請移至 [偵測器] 面板中，並確定已核取核取方塊右邊的虛擬實境支援 （如圖所示）。 也請確定在下圖所示，也檢查場景/HLSharedProjectMain 旁邊的核取方塊。![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. 在 [偵測器] 面板中的 [發佈設定] 區段中，向下捲動功能，並確保已標示下列核取方塊：![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. 匯入自訂的套件稱為 SharingAssetCollection 可下載[以下。](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. 在 [專案] 面板中，移至 Prefabs 資料夾。 在接下來的步驟中，您會實作少數 prefabs 場景。 在 Prefabs 資料夾中，按一下並拖曳 prefab，DebugWindow 到階層。 完成之後，儲存專案的 clckin 檔案，然後儲存或按 Control + S。

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 注意:您可能會注意到快顯視窗會顯示當您按一下 prefab，詢問您關於 TMP Essentials。 如有需要請按一下 匯入 TMP 基本功能。 如果這個快顯視窗出現時，您可能需要刪除您的階層 prefab 並重新將它拖曳到您的階層，以避免可能的文字相關錯誤。
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>恭喜！

您的 Unity 專案已準備好進行 Photon。 在接下來的教學課程中，我們將建置此場景和我們針對完整的共用經驗的 Unity 專案。

[下一個教學課程：連接多個使用者](mrlearning-sharing(photon)-ch3.md)

