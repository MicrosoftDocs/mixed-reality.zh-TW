---
title: 參與指示
description: 如何參與 Windows Mixed Reality 文件。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596946"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>提供給 Windows Mixed Reality 開發人員文件

歡迎來到[如需 Windows Mixed Reality 開發人員文件的公用存放庫](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)！ 您建立或編輯此存放庫中的任何發行項**會公開顯示。** 

Windows Mixed Reality 台文件現在位於 docs.microsoft.com 平台，它會使用具備 GitHub 特色的 Markdown （包含 Markdig 功能）。 基本上，您在此存放庫中編輯的內容取得轉換成在顯示的格式化和樣式化頁面 https://docs.microsoft.com/windows/mixed-reality。 

本頁涵蓋基本的步驟和指導方針的貢獻，以及連結至 Markdown 基本概念。 感謝您為您的貢獻的 ！

## <a name="before-you-start"></a>開始之前

如果您還沒有做，您必須[建立 GitHub 帳戶](https://github.com/join)。

>[!NOTE]
>如果您是 Microsoft 員工，連結您的 GitHub 帳戶，以您的 Microsoft 別名[Microsoft 開放原始碼入口網站](https://repos.opensource.microsoft.com/)。 聯結 **「 Microsoft 」** 並 **"MicrosoftDocs"** 組織)。

當設定您的 GitHub 帳戶，我們也建議這些安全性預防措施：
- 建立[您的 Github 帳戶的強式密碼](https://github.com/settings/admin)。
- 啟用[雙因素驗證](https://github.com/settings/two_factor_authentication/configure)。
- 儲存您[復原碼](https://github.com/settings/auth/recovery-codes)在安全的地方。
- 更新您[公用設定檔設定](https://github.com/settings/profile)。
   - 設定您的名稱，並請考慮將您*公用電子郵件*要*不會顯示我的電子郵件地址*。
   - 我們建議您上傳個人檔案圖片，因為您參與 docs 頁面上會顯示縮圖。
- 如果您打算使用的命令列工作流程，請考慮設定[Windows 的 Git 認證管理員](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)，讓您不必每次輸入您的密碼進行貢獻。

執行這些步驟，是很重要，因為發行系統連至 GitHub，而且您將會列為作者或參與者使用 GitHub 別名每一個發行項。

## <a name="editing-an-existing-article"></a>編輯現有的發行項

使用下列工作流程進行更新才能*現有的發行項*透過網頁瀏覽器的 GitHub:

1. 瀏覽至您想要編輯的 「 混合實境-文件 」 資料夾中的文件。
2. 選取右上角的 [編輯] 按鈕 （鉛筆圖示）。 這會自動將分支，則以 「 主要 」 分支可處置分支。

   ![編輯文章。](images/editpage.png)
3. 編輯文章的內容 (請參閱[< Markdown 基本概念 >](#markdown-basics)以下指導方針)。
4. 更新為上方的每個發行項相關的中繼資料：
   * 標題：這是要檢視發行項時，會出現在瀏覽器索引標籤頁面標題。 這是用於 SEO 和編製索引，您就不應該變更標題，除非必要 （但文件會公開之前，這是較不重要）。
   * 描述：撰寫文章的內容的簡短描述。 這可協助 SEO 和探索。
   * 作者：如果您是主要的擁有者的頁面，新增您的 GitHub 別名。
   * ms.author:如果您是主要的擁有者的頁面，新增您的 Microsoft 別名這裡 (您不需要@microsoft.com，只要的別名)。
   * ms.date:如果您是將主要的內容新增到頁面上，而不是進一步釐清，格式文法，例如修正或拼字檢查，請更新的日期。
   * 關鍵字：關鍵字可協助 SEO （搜尋引擎最佳化）。 加入關鍵字，就以逗號和空格分隔專屬於您的文章 （但清單中最後一個關鍵字後面的任何標點符號）;您不需要加入全域套用至所有的發行項的關鍵字，因為這些在其他地方管理。 
5. 當您完成您的文件編輯時，向下捲動並按一下**建議檔案變更** 按鈕。
6. 在下一步 頁面上，按一下**建立提取要求**至您自動建立的分支合併至 'master'。
7. 下一步 您想要編輯的發行項重複上述步驟。

## <a name="creating-a-new-article"></a>建立新文章

使用下列工作流程*建立新的文章*透過 GitHub 的網頁瀏覽器中的文件存放庫中：

1. 建立分支的 MicrosoftDocs/混合實境 'master' 分支 (使用**分岔**右上角的按鈕)。

   ![分叉的主要分支。](images/forkbranch.png)
2. 在 「 混合實境-文件 」 資料夾中，按一下**建立新檔案**右上角的按鈕。
3. 建立發行項的頁面名稱 （而不是空白使用連字號和不會使用標點符號或單引號），並將附加".md"

   ![命名您的新頁面。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >請確定您建立新的發行項的 「 混合實境-文件 」 資料夾內。 您可以藉由檢查來確認此 「 混合實境 docs /"的新檔案名稱行中。

4. 在您的新頁面頂端，加入下列的中繼資料區塊：

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. 相關的中繼資料欄位，每個中的指示中填滿[節](#editing-an-existing-article)。
6. 寫入本文內容中使用[Markdown 基本概念](#markdown-basics)。
7. 新增`## See also`區段底部的其他相關文章連結的文章。
8. 完成後，按一下**認可新的檔案**。
9. 按一下 **新的提取要求**和您的分叉 'master' 分支合併至 MicrosoftDocs/混合實境 'master' （請確定箭頭所指向的正確方式）。

   ![從您的分支建立提取要求，至 MicrosoftDocs/混合實境](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Markdown 基本概念

下列資源將協助您了解如何編輯使用之 Markdown 語言的文件：

- [Markdown 基本概念](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown 在-快速參考海報](images/MarkdownPoster.pdf)
- [適用於撰寫 docs.microsoft.com 的 Markdown 其他資源](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>加入資料表

方式 docs.microsoft.com 樣式資料表，因為他們不需要框線或自訂的樣式，即使您嘗試內嵌 CSS。 它會顯示適用於一段時間，但最後的平台會去除移出資料表樣式。 因此請事先規劃，並簡化您的資料表。 [以下是站台，以簡化 Markdown 表格](http://www.tablesgenerator.com/markdown_tables)。

[適用於 Visual Studio Code 的 Docs Markdown 延伸模組](https://docs.microsoft.com/teamblog/docs-extension)也會使資料表產生簡單，如果您使用[Visual Studio Code （如下所示）](#using-visual-studio-code)編輯文件。

### <a name="adding-images"></a>加入影像

您必須上傳您的映像到 「 混合實境-docs/映像 」 資料夾中存放庫，然後文件中適當地參考它們。 映像會自動顯示在觀看完整大小，這表示如果您的映像很大，這樣就能填入文件的整個寬度。 因此，我們建議您預先調整大小之前將其上傳的映像。 建議的寬度是介於 600 到 700 的像素，但您應該調整大小增加或相應減少如果分別是密集的螢幕擷取畫面或螢幕擷取畫面中，一小部分。

>[!IMPORTANT]
>您可以只上傳映像至您分支存放庫在合併之前。 因此，如果您打算將映像新增至發行項，您必須[使用 Visual Studio Code](#using-visual-studio-code)第一次將映像加入至您分叉的 「 映像 」 資料夾或請確定您已完成的網頁瀏覽器中的下列：
>
>1. 分叉 MicrosoftDocs/混合實境存放庫。
>2. 編輯您的分叉中的發行項。
>3. 上傳您分叉中參考的 「 混合實境-docs/映像 」 資料夾在文章中的映像。
>4. 建立**提取要求**至 MicrosoftDocs/混合實境 'master' 分支合併您的分叉。
>
>若要了解如何設定您自己的分支存放庫，請遵循指示[建立新的發行項](#creating-a-new-article)。

## <a name="previewing-your-work"></a>預覽您的工作

在 GitHub 中編輯，透過網頁瀏覽器，您可以按一下**預覽** 索引標籤上方的頁面，即可預覽您的工作，然後再認可。 

>[!NOTE]
>預覽 review.docs.microsoft.com 變更只會提供給 Microsoft 的員工

Microsoft 員工： 一旦您的參與已合併至 「 主要 」 分支，您可以看到之前它會在公用文件的外觀 https://review.docs.microsoft.com/windows/mixed-reality?branch=master（找到您的文章左側資料行中使用的目錄）。

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>在與編輯桌面用戶端瀏覽器中編輯

在瀏覽器中編輯是最簡單的方式進行快速變更，不過，有幾個缺點：

- 您無法取得拼字檢查。
- 您無法取得任何智慧連結 （您必須以手動方式輸入文章的檔名） 的其他文章。
- 它可以上傳，並參考映像很麻煩。

如果您想而不處理這些問題，您可能想要使用桌上型電腦的用戶端，像是[Visual Studio Code](https://code.visualstudio.com/)幾[實用的擴充功能](#useful-extensions)來參與編輯文件。

## <a name="using-visual-studio-code"></a>使用 Visual Studio Code

原因列出[上述](#editing-in-the-browser-vs-editing-with-a-desktop-client)，您可能偏好使用編輯文件，而不是網頁瀏覽器的桌面用戶端。 我們建議您使用[Visual Studio Code](https://code.visualstudio.com/)。

### <a name="setup"></a>安裝程式

請遵循下列步驟來設定 Visual Studio Code，來處理此存放庫：

1. 在 web 瀏覽器：
    1. 安裝[針對您的電腦的 Git](https://git-scm.com/downloads)。
    2. 安裝[Visual Studio Code](https://code.visualstudio.com/)。
    3. [派生 MicrosoftDocs/混合實境](#creating-a-new-article)如果您還沒有這麼做。
    4. 在您的分叉中，按一下**複製或下載**並複製 URL。
2. 在 Visual Studio Code 建立分叉的本機複製品：
    1. 從**檢視**功能表上，選取**命令選擇區**。
    2. 類型"Git:Clone。 」
    3. 貼上您剛才複製的 URL。
    4. 選擇您的電腦上儲存複製的位置。
    5. 按一下 **開啟的存放庫**快顯視窗中。

### <a name="editing-documentation"></a>編輯文件

使用下列工作流程來進行使用 Visual Studio Code 文件中的變更：

>[!NOTE]
>所有的指導方針[編輯](#editing-an-existing-article)並[建立](#creating-a-new-article)文章，和[的編輯 Markdown 基本概念](#markdown-basics)，上述適用於當也使用 Visual Studio Code。

1. 請確定您複製的 「 分叉 」 是最新的官方存放庫。
   1. 在 web 瀏覽器中建立提取要求，以同步處理來自其他參與者 MicrosoftDocs/混合實境 'master' 中最近的變更至您的分叉 （請確定箭頭所指向正確的方式）。
      
      ![同步處理從 MicrosoftDocs/混合實境中的變更至您的分叉](images/sync_repos.PNG)
   2. 在 Visual Studio Code 中，按一下 [同步處理您剛更新的分叉的本機複本的同步處理] 按鈕。
      
      ![按一下 [同步] 按鈕](images/sync_clone.png)
2. 建立或編輯您使用 Visual Studio Code 的複製存放庫中的文章。
   1. 編輯 （如有必要，映像新增到 「 映像 」 資料夾） 中的一或多個發行項。
   2. **儲存**中變更**總管**。
      
      ![在 [總管] 中選擇 [全部儲存]](images/explorer_save.png)
   3. **全部認可**中變更**原始檔控制**（寫入認可訊息出現提示時）。
      
      ![選擇 「 全部認可 」 在原始檔控制](images/source_control_commit.png)
   4. 按一下 [**同步**變更回原始 （您在 GitHub 上的分支） 的同步處理] 按鈕。
      
      ![按一下 [同步] 按鈕](images/sync_back.png)
3. 在 web 瀏覽器中，建立 提取要求，以同步處理回到 MicrosoftDocs/混合實境 'master' 分支中的新變更 （請確定箭頭所指向的正確方式）。

   ![從您的分支建立提取要求，至 MicrosoftDocs/混合實境](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>實用的擴充功能

編輯文件時，下列 Visual Studio Code 擴充功能就非常有用：

- [適用於 Visual Studio Code 的 docs Markdown 延伸模組](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)-使用**Alt + M**來顯示功能表的 docs 編寫選項，例如：
   - 您已上傳的影像搜尋和參考。
   - 加入格式化的清單、 資料表、 docs 特定圖說喜歡也`>[!NOTE]`。
   - 搜尋和參考內部連結和書籤 （在頁面內的特定區段的連結）。
   - 格式錯誤會反白顯示 （停留在要了解更多的錯誤）。
- [拼字檢查工具的程式碼](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-拼錯的單字會加上底線，以滑鼠右鍵按一下拼錯的字，將它變更，或將它儲存至字典。
