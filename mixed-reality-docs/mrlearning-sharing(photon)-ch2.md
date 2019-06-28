**準備 Unity 進行開發** 

在這一課中，我們將了解如何準備及設定 Unity 以應用程式開發，包括匯入混合實境工具組、 設定組建設定，並準備我們的場景。

目標：

- 設定 Unity 以應用程式開發

- 匯入混合實境工具組

- 準備您的專案場景

### <a name="instructions"></a>指示

1. 下載並儲存混合實境 Toolkit unity 套件，依序按一下[這裡。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. 在 Unity 中，按一下 資產 功能表並選取 匯入封裝，然後按一下 「 自訂套件。 」

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 選取您從步驟 1 中所提供的連結下載 Unity 套件。 一旦匯入快顯視窗會出現在 Unity 中，按一下 匯入 按鈕，以開始匯入。 匯入 MRTK 可能需要幾分鐘的時間。

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 注意:下載的封裝會在您的本機資料夾儲存檔案的位置。 上圖未顯示您將在其中找到封裝。

4. 建立新的場景 （做法是按一下 [檔案] 並選取 「 新場景 」）。 將場景儲存為"HLSharedProjectMain。 」

> 注意： 您可能會收到看起來類似下面的影像的快顯視窗。 現在，只要按一下 [否]。
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. 在 「 混合實境工具組 」 中，按一下 "新增至場景，並設定 」。

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完成後完成時，新的組態檔會出現，讓您選擇以自訂設定檔。 按一下 複製和自訂 」。

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. 向下捲動，並取消核取 [啟用診斷系統] 是否您想要隱藏 [diagnostics] 視窗。 我們建議您保持 [diagnostics] 視窗來監視效能，應用程式開發期間啟用和停用在生產環境或應用程式的示範期間。 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. 開啟 組建設定，請按 control + shift + B 或前往 檔案 > 建置設定。 請注意，此程式目前設定下的 「 個人電腦、 Mac 和 Linux 的獨立 」 平台。 HoloLens 2 程式開發中，將 平台為 「 通用 Windows 平台。 」 選取它，然後按一下 「 交換器平台。 」![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 完成後，按一下 加入 開啟的場景。 方塊 現在請移至 [偵測器] 面板，並確定核取方塊右邊的 「 支援的虛擬實境"（如下圖所示） 會檢查。 也確定也勾選 「 場景/HLSharedProjectMain 」 旁的核取方塊，如下圖所示。![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. 在 [發行設定] 下一節中偵測器窗格中向下捲動到 「 功能 」，並確定下列核取方塊會標示：![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. 匯入自訂的封裝稱為 「 SharingAssetCollection"可下載[以下。](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. 現在，在 [專案] 面板中，移至 「 prefabs"資料夾，因為在接下來的步驟中您會實作少數 prefabs 場景。 在 「 prefabs"資料夾中，按一下並拖曳 prefab，"DebugWindow 」 到階層。 完成之後，儲存專案 （按一下檔案，然後儲存，或按 control + S）

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 注意:您可能會注意到快顯視窗會顯示當您按一下 prefab，詢問您關於 TMP Essentials。 將需要，請按一下 [匯入 TMP Essentials]。 如果這個快顯視窗出現時，您可能需要刪除您的階層 prefab 並重新將它拖曳到您的階層，以避免可能的文字相關錯誤。
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>恭喜！

您的 Unity 專案已準備好進行 Photon ！ 在接下來的課程中，我們將建置此場景和我們針對完整的共用經驗的 Unity 專案。

[下一課：第 3 課 Sharing(Photon)](mrlearning-sharing(photon)-ch3.md)

