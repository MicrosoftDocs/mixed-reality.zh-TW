---
title: Azure 雲端教學課程 - 2. 整合 Azure 儲存體
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中執行 Azure 表格儲存體和 Azure Blob 儲存體。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, hololens 2, azure 儲存體
ms.localizationpriority: high
ms.openlocfilehash: a8d91bc55b3ce73d6e1fb46e5d696d853adcf871
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376470"
---
# <a name="2-integrating-azure-storage"></a>2.整合 Azure 儲存體

在本教學課程中，您將了解如何將實體資料儲存至 Azure 表格儲存體，並將縮圖影像儲存至 Azure Blob 儲存體。 這項功能可讓我們使用識別碼、名稱、縮圖影像等資料，在工作階段和裝置之間將「追蹤物件」儲存和擷取至雲端。

## <a name="objectives"></a>目標

* 了解 Azure 儲存體的基本概念
* 了解如何從表格儲存體儲存、修改和擷取資料
* 了解如何從 Blob 儲存體儲存和刪除影像

## <a name="understanding-azure-storage"></a>了解 Azure 儲存體

**Azure 儲存體** 是 Microsoft 的雲端儲存體解決方案，可涵蓋許多案例和需求。 開發人員可以進行大規模調整並輕鬆運用。 所有服務都可以在 **Azure 儲存體帳戶**之下使用。 在我們的使用案例中，將會使用「表格儲存體」和「Blob 儲存體」。

深入了解 [Azure 儲存體服務](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview)。

### <a name="azure-table-storage"></a>Azure 表格儲存體

這項服務可讓我們以 NoSQL 的方式儲存資料，在此專案中，我們將使用這種方式來儲存「追蹤物件」的相關資訊，例如：名稱、描述、空間錨點識別碼等等。

在示範應用程式的內容中，您需要兩個表格，其中一個用來儲存專案的相關資訊，其中包含有關已定型模型狀態 ([整合 Azure 自訂視覺](mr-learning-azure-03.md)) 教學課程的詳細資訊；第二個表格用來儲存「追蹤物件」的相關資訊。

深入了解 [Azure 表格儲存體](https://docs.microsoft.com/azure/storage/tables/table-storage-overview)。

### <a name="azure-blob-storage"></a>Azure Blob 儲存體

此服務可讓您儲存大型二進位檔案，您將使用此檔案將針對「追蹤物件」所拍攝的相片儲存為縮圖。
針對示範應用程式，您需要一個 Blob 容器來儲存影像。

深入了解 [Azure Blob 儲存體](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction)。

## <a name="preparing-azure-storage"></a>準備 Azure 儲存體

若要取用 Azure 儲存體服務，您需要 Azure 儲存體帳戶。 若要建立儲存體帳戶，請參閱[如何建立儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal)。 若要深入瞭解儲存體帳戶，請參閱 [Azure 儲存體帳戶概觀](https://docs.microsoft.com/azure/storage/common/storage-account-overview)。

準備好儲存體帳戶後，您就可以從 **Azure 入口網站**擷取連接字串，您會在本課程的下一節中用到此一資訊。

### <a name="optional-azure-storage-explorer"></a>選用的 Azure 儲存體總管

雖然您可以從應用程式內的 UI 查看及確認所有資料變更，但我們建議您安裝 [Azure 儲存體總管](https://azure.microsoft.com/features/storage-explorer/)。 此工具可讓您以視覺化方式查看 Azure 儲存體中的資料，並在偵錯和學習時提供絕佳的協助。

> [!TIP]
> 若要從 Unity 編輯器內部進行測試，您可以使用本機模擬器：

> * 在 Windows 10 上，您可以使用 [Azure 儲存體模擬器](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)
> * 在 MacOS/Linux 上，您可以使用適用於 Docker 的 [Azurite Docker 影像](https://hub.docker.com/_/microsoft-azure-storage-azurite)

## <a name="preparing-the-scene"></a>準備場景

在階層視窗中，找出 **DataManager** 物件並加以選取。

![mr-learning-azure](images/mr-learning-azure/tutorial2-section4-step1-1.png)

在偵測器視窗中，您會看到 **DataManager (指令碼)** 元件是保留所有 **Azure 儲存體** 相關設定的位置。 所有相關的設定都已設定完成，您只需要將「連接字串」欄位取代為您可以從 Azure 入口網站取得的值。 如果您使用本機 Azure 儲存體模擬器解決方案，則可以保留已提供的「連接字串」。

**DataManager (指令碼)** 負責與**表格儲存體**和 **Blob 儲存體**溝通，這兩者是由 UI 元件上的其他控制器指令碼使用。

## <a name="writing-and-reading-data-from-azure-table-storage"></a>從 Azure 表格儲存體寫入和讀取資料

一切準備就緒後，就可以建立「追蹤物件」。

開啟 HoloLens 上的應用程式，按一下 [設定物件]，您就會看到 EnterObjectName 物件在階層中變成使用中狀態。 在此功能表中，按一下 [搜尋列]，然後輸入想要提供「追蹤物件」的名稱。 提供名稱之後，請按一下 [設定物件] 按鈕。 這會在 Azure 表格儲存體上建立「追蹤物件」，而您現在會看到**物件卡**。

此**物件卡**是「追蹤物件」 的 UI 標記法，在本教學課程系列中多次扮演重要的角色。

現在，按一下描述 [文字方塊] 並輸入 "Car"，然後按一下 [儲存] 按鈕以儲存變更。 停止應用程式並重新執行。

現在按一下 [搜尋物件]，然後在「搜尋列」中輸入您在建立「追蹤物件」時所使用的名稱。 您會看到**物件卡**，其中包含所有從 **Azure 表格儲存體**中擷取的資料。

依需求關閉**物件卡**並建立新的「追蹤物件」｜然後編輯其資料。

> [!TIP]
> 如果您已安裝 [Azure 儲存體總管](https://azure.microsoft.com/features/storage-explorer/)，請查看「物件」資料表，您會看到已建立的「追蹤物件」。

## <a name="uploading-and-download-image-from-azure-blob-storage"></a>從 Azure Blob 儲存體上傳和下載影像

在本節中，您將使用 Azure Blob 儲存體上傳和下載會用作「追蹤物件」縮圖的影像。

> [!NOTE]
> 在本教學課程中，應用程式會拍照以將影像上傳至 Blob 儲存體。 如果您是從 Unity 編輯器本機執行此程式，請確定已將網路攝影機與電腦連線。

在 HoloLens 上開啟應用程式，按一下 [設定物件]，然後在「搜尋列」中輸入名稱 "Car"。 現在您應該會看到**物件卡**，請按一下 [相機] 按鈕，系統會指示您使用 AirTap 拍照。 拍攝相片後，您會看到一則訊息，通知您正在上傳資料；一段時間後，影像應該會出現在之前保留的預留位置。

現在重新執行應用程式，並搜尋「追蹤物件」，先前上傳的影像應該會顯示為縮圖。

## <a name="deleting-image-from-azure-blob-storage"></a>從 Azure Blob 儲存體刪除影像

在上一節中，您已將新的影像上傳至 Azure Blob 儲存體；在本節中，您將會刪除「追蹤物件」的影像縮圖。

在 HoloLens 上開啟應用程式，按一下 [設定物件]，然後在「搜尋列」中輸入名稱 "Car"。 現在您應該會看到**物件卡**與縮圖影像，請按一下 [刪除] 按鈕。 您會發現縮圖影像已由預留位置影像所取代。

現在重新執行應用程式，並搜尋先前已刪除其縮圖的「追蹤物件」，您應該只會看到預留位置影像。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何使用 Azure 儲存體服務來保存非結構化資料；在我們的案例中為**追蹤物件**，而雲端上的 **HoloLens 2** 示範應用程式的二進位檔則是以縮圖影像的形式出現。

在下一個教學課程中，您將了解如何使用 Azure 自訂視覺來偵測與「追蹤物件」相關聯的影像。

[下一個教學課程：3.整合 Azure 自訂視覺](mr-learning-azure-03.md)
