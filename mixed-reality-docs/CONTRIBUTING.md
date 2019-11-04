---
title: 參與指示
description: 如何參與 Windows Mixed Reality 檔。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: 934171f26571b3219bbe390aff44349fb6908f74
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437122"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>參與 Windows Mixed Reality 開發人員檔

歡迎使用[Windows Mixed Reality 開發人員檔的公用](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)存放庫！ 您在此存放庫中建立或編輯的任何文章，**都將可供公眾看見。** 

Windows Mixed Reality 檔現在位於 docs.microsoft.com 平臺上，其使用 GitHub flavored Markdown （含 Markdig 功能）。 基本上，您在此存放庫中編輯的內容會轉換成在 https://docs.microsoft.com/windows/mixed-reality 顯示的格式化和樣式頁面。 

本頁涵蓋參與的基本步驟和指導方針，以及 Markdown 基本概念的連結。 感謝您的貢獻！

## <a name="before-you-start"></a>開始之前

如果您還沒有帳戶，您必須[建立一個 GitHub 帳戶](https://github.com/join)。

>[!NOTE]
>如果您是 Microsoft 員工，請將您的 GitHub 帳戶連結到[Microsoft 開放原始碼入口網站](https://repos.opensource.microsoft.com/)上的 microsoft 別名。 加入 **"Microsoft"** 和 **"MicrosoftDocs"** 組織）。

在設定您的 GitHub 帳戶時，我們也建議這些安全性預防措施：
- [為您的 Github 帳戶建立強式密碼](https://github.com/settings/admin)。
- 啟用[雙因素驗證](https://github.com/settings/two_factor_authentication/configure)。
- 將您的復原程式[代碼](https://github.com/settings/auth/recovery-codes)儲存在安全的地方。
- 更新您的[公用設定檔設定](https://github.com/settings/profile)。
   - 設定您的名稱，並考慮將您的*公用電子郵件*設定為*不顯示我的電子郵件地址*。
   - 我們建議您上傳個人資料圖片，因為縮圖會顯示在您所參與的檔頁面上。
- 如果您打算使用命令列工作流程，請考慮設定[適用于 Windows 的 Git 認證管理員](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)，如此一來，您就不需要在每次進行貢獻時都輸入密碼。

採取這些步驟很重要，因為發佈系統會系結至 GitHub，而您會使用 GitHub 別名，將您列為每篇文章的作者或參與者。

## <a name="editing-an-existing-article"></a>編輯現有的文章

使用下列工作流程，透過 web 瀏覽器中的 GitHub 對*現有文章*進行更新：

1. 流覽至您想要在「混合式-檔」資料夾中編輯的文章。
2. 選取右上方的 [編輯] 按鈕（鉛筆圖示）。 這會自動將可處置分支從「主要」分支中派生出來。

   ![編輯文章。](images/editpage.png)
3. 編輯文章的內容（請參閱下方的「 [Markdown 基本概念](#markdown-basics)」，以取得指導方針）。
4. 在每篇文章的頂端更新相關中繼資料：
   * 標題：這是在查看發行項時，出現在 [瀏覽器] 索引標籤中的頁面標題。 因為這是用於 SEO 和編制索引，除非必要，否則不應變更標題（雖然這在檔公開之前較不重要）。
   * 描述：撰寫文章內容的簡短描述。 這有助於 SEO 和探索。
   * 作者：如果您是網頁的主要擁有者，請在這裡新增您的 GitHub 別名。
   * （作者）：如果您是網頁的主要擁有者，請在這裡新增您的 Microsoft 別名（您不需要 @microsoft.com，只有別名）。
   * [ms]：如果您要在頁面中新增主要內容，而不是針對說明、格式、文法或拼寫等修正程式，請更新日期。
   * 關鍵字： [SEO] 中的關鍵字輔助（搜尋引擎優化）。 以逗號和空格分隔特定于您文章的關鍵字（但清單中的最後一個關鍵字後面沒有標點符號）;您不需要新增適用于所有發行項的全域關鍵字，因為這些專案是在其他地方管理。 
5. 當您完成文章編輯後，請向下卷，然後按一下 [**提議檔案變更**] 按鈕。
6. 在下一個頁面上，按一下 [**建立提取要求**]，將自動建立的分支合併至 [master]。
7. 針對您想要編輯的下一篇文章，重複上述步驟。

## <a name="renaming-or-deleting-an-existing-article"></a>重新命名或刪除現有的文章

如果您的變更將會重新命名或刪除現有的文章，請務必新增重新導向。 如此一來，具有現有文章連結的任何人，仍然會在正確的位置結束。 重新導向是由存放庫根目錄中的 openpublishing 所管理。

若要新增重新導向至 openpublishing，請將專案新增至 `redirections` 陣列：

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- `source_path` 是您要移除之舊發行項的相對存放庫路徑。 請確定路徑開頭為 `mixed-reality-docs`，並以 `.md`結尾。
- `redirect_url` 是從舊發行項到新文章的相對公用 URL。 請確定此 URL**不**包含 `mixed-reality-docs` 或 `.md`，因為它是指公用 URL，而不是存放庫路徑。 允許使用 `#section` 連結到新文章內的區段。 如有必要，您也可以在此處使用其他網站的絕對路徑。
- `redirect_document_id` 指出您是否要保留前一個檔案的檔識別碼。 預設值為 `false`。 如果您想要保留重新導向之發行項的 `ms.documentid` 屬性值，請使用 `true`。 如果您保留檔識別碼，資料（例如頁面流覽和排名）將會傳送至目標發行項。 如果重新導向主要是重新命名，而不是指向僅涵蓋部分相同內容的不同發行項的指標，請執行此動作。

如果您新增重新導向，也請務必刪除舊的檔案。

## <a name="creating-a-new-article"></a>建立新的文章

使用下列工作流程，透過 web 瀏覽器中的 GitHub 在檔存放庫中*建立新的文章*：

1. 使用右上方的 [**分叉**] 按鈕，從 MicrosoftDocs/混合現實的「主要」分支建立分叉。

   ![將 master 分支派生。](images/forkbranch.png)
2. 在 [混合式-檔] 資料夾中，按一下右上方的 [**建立新**檔案] 按鈕。
3. 建立發行項的頁面名稱（使用連字號，而不是空格，不要使用標點符號或單引號）並附加 "md"

   ![為新頁面命名。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >請確定您是從「混合現實檔」資料夾內建立新的文章。 您可以在新的檔案名行中檢查 "/mixed-reality-docs/" 來確認這一點。

4. 在新頁面的頂端，新增下列中繼資料區塊：

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

5. 根據[上一節](#editing-an-existing-article)中的指示填入相關的元資料欄位。
6. 使用[Markdown 基本概念](#markdown-basics)撰寫文章內容。
7. 在本文底部新增 `## See also` 區段，並提供其他相關文章的連結。
8. 完成後，按一下 [**認可新**檔案]。
9. 按一下 [**新增提取要求**]，並將分叉的「主要」分支合併到 MicrosoftDocs/mixed-reality ' master ' （請確定箭號是以正確的方式指向）。

   ![從您的分支建立提取要求至 MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Markdown 基本概念

下列資源將協助您瞭解如何使用 Markdown 語言來編輯檔：

- [Markdown 基本概念](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown 概覽的參考海報](images/MarkdownPoster.pdf)
- [為 docs.microsoft.com 撰寫 Markdown 的其他資源](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>加入資料表

由於 docs.microsoft.com 樣式表的方式，它們不會有框線或自訂樣式，即使您嘗試內嵌 CSS 也一樣。 它會在短時間內出現，但最終平臺會從資料表中去除樣式。 所以請先行規劃，讓資料表保持簡單。 [以下是讓 Markdown 資料表變得簡單的網站](https://www.tablesgenerator.com/markdown_tables)。

如果您使用[Visual Studio Code （請參閱下文）](#using-visual-studio-code)來編輯檔，則 Visual Studio Code 的檔[Markdown 擴充](https://docs.microsoft.com/teamblog/docs-extension)功能也可讓您輕鬆產生資料表。

### <a name="adding-images"></a>新增影像

您必須將映射上傳至存放庫中的「混合式-檔/影像」資料夾，然後在文章中適當地加以參考。 影像會自動以完整大小顯示，這表示如果您的影像很大，則會填滿整篇文章的寬度。 因此，建議您在上傳映射之前預先調整其大小。 建議的寬度介於600和700圖元之間，不過，如果它是密集螢幕擷取畫面或螢幕擷取畫面的一部分，則您應該將大小調整為相應增加或相應減少。

>[!IMPORTANT]
>在合併之前，您只能將影像上傳至分支存放庫。 因此，如果您打算將影像新增至文章，則必須先[使用 Visual Studio Code](#using-visual-studio-code)將影像新增至您分叉的「影像」資料夾，或確認您已在網頁瀏覽器中完成下列動作：
>
>1. 分支 MicrosoftDocs/mixed reality 存放庫。
>2. 已在您的分叉中編輯文章。
>3. 已將您在文章中參考的影像上傳至您分叉中的「混合現實檔/影像」資料夾。
>4. 建立**提取要求**，以將您的分叉合併到 MicrosoftDocs/mixed reality ' master ' 分支中。
>
>若要瞭解如何設定您自己的分支存放庫，請遵循[建立新文章](#creating-a-new-article)的指示。

## <a name="previewing-your-work"></a>預覽您的工作

當您透過網頁瀏覽器在 GitHub 中編輯時，您可以按一下頁面頂端附近的 [**預覽**] 索引標籤，以預覽您的工作，然後再進行認可。 

>[!NOTE]
>在 review.docs.microsoft.com 上預覽您的變更僅適用于 Microsoft 員工

Microsoft 員工：一旦您的投稿合併到「主要」分支之後，您就可以在 https://review.docs.microsoft.com/windows/mixed-reality?branch=master 公開檔之後，看到該檔的樣子（使用左欄中的目錄尋找您的文章）。

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>在瀏覽器中編輯與使用桌面用戶端編輯

在瀏覽器中編輯是進行快速變更的最簡單方式，不過，有幾個缺點：

- 您不會看到拼寫檢查。
- 您不會取得任何與其他文章的智慧型連結（您必須手動輸入文章的檔案名）。
- 上傳和參考影像可能會很麻煩。

如果您不處理這些問題，您可能會想要使用桌面用戶端（例如[Visual Studio Code](https://code.visualstudio.com/) ），並提供一些[實用的擴充](#useful-extensions)功能來貢獻檔。

## <a name="using-visual-studio-code"></a>使用 Visual Studio Code

基於[上述](#editing-in-the-browser-vs-editing-with-a-desktop-client)原因，您可能會偏好使用桌面用戶端來編輯檔，而不是網頁瀏覽器。 我們建議使用[Visual Studio Code](https://code.visualstudio.com/)。

### <a name="setup"></a>[設定]

請遵循下列步驟來設定 Visual Studio Code 以使用此存放庫：

1. 在網頁瀏覽器中：
    1. [為您的電腦安裝 Git](https://git-scm.com/downloads)。
    2. 安裝[Visual Studio Code](https://code.visualstudio.com/)。
    3. [分叉 MicrosoftDocs/mixed-事實（](#creating-a-new-article)如果您尚未這麼做）。
    4. 在您的分支中，按一下 [**複製] 或 [下載**] 並複製 URL。
2. 在 Visual Studio Code 中建立分支的本機複製：
    1. 從 [ **View** ] 功能表中，選取 [**命令**選擇區]。
    2. 輸入「Git： Clone」。
    3. 貼上您剛才複製的 URL。
    4. 選擇要將複製儲存在電腦上的位置。
    5. 在快顯視窗中，按一下 [**開啟**存放庫]。

### <a name="editing-documentation"></a>編輯檔

使用下列工作流程，利用 Visual Studio Code 來變更檔集：

>[!NOTE]
>當您使用 Visual Studio Code 時，所有[編輯](#editing-an-existing-article)和[建立](#creating-a-new-article)文章的指引，以及[編輯 Markdown 的基本概念](#markdown-basics)也適用。

1. 請確定您的已複製分支已與官方存放庫保持在最新狀態。
   1. 在網頁瀏覽器中，建立提取要求，將最近的變更從 MicrosoftDocs/mixed-現實 ' master ' 中的其他參與者同步處理至您的分支（請確定箭號是正確的方式）。
      
      ![將 MicrosoftDocs/mixed-reality 的變更同步處理至您的分支](images/sync_repos.PNG)
   2. 在 Visual Studio Code 中，按一下 [同步處理] 按鈕，將您剛剛更新的分支同步處理到本機複本。
      
      ![按一下 [同步處理] 按鈕](images/sync_clone.png)
2. 使用 Visual Studio Code，在複製的存放庫中建立或編輯文章。
   1. 編輯一或多篇文章（如有需要，將影像新增至 [映射] 資料夾）。
   2. **儲存** **Explorer**中的變更。
      
      ![在 Explorer 中選擇 [全部儲存]](images/explorer_save.png)
   3. **認可** **原始檔控制**中的所有變更（出現提示時寫入認可訊息）。
      
      ![選擇原始檔控制中的 [全部認可]](images/source_control_commit.png)
   4. 按一下 [**同步**] 按鈕，將您的變更同步處理回原始（GitHub 上的分支）。
      
      ![按一下 [同步處理] 按鈕](images/sync_back.png)
3. 在網頁瀏覽器中，建立提取要求，將您分支中的新變更同步處理回到 MicrosoftDocs/mixed-現實 ' master ' （請確定箭號指向正確的方式）。

   ![從您的分支建立提取要求至 MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>有用的擴充功能

編輯檔時，下列 Visual Studio Code 擴充功能非常有用：

- [適用于 Visual Studio Code 的檔 Markdown 延伸](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)模組-使用**Alt + M**來顯示檔撰寫選項的功能表，如下所示：
   - 搜尋並參考您已上傳的影像。
   - 加入格式如清單、資料表和檔特定的呼叫，例如 `>[!NOTE]`。
   - 搜尋和參考內部連結和書簽（頁面內特定區段的連結）。
   - 格式化錯誤會反白顯示（將滑鼠停留在錯誤上方以深入瞭解）。
- 程式[代碼拼寫檢查](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-拼錯的單字會加上底線;以滑鼠右鍵按一下拼錯的字組來加以變更，或將它儲存至字典。
