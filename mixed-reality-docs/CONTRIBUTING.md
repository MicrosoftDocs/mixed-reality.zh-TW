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
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="e221b-103">提供給 Windows Mixed Reality 開發人員文件</span><span class="sxs-lookup"><span data-stu-id="e221b-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="e221b-104">歡迎來到[如需 Windows Mixed Reality 開發人員文件的公用存放庫](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)！</span><span class="sxs-lookup"><span data-stu-id="e221b-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="e221b-105">您建立或編輯此存放庫中的任何發行項**會公開顯示。**</span><span class="sxs-lookup"><span data-stu-id="e221b-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="e221b-106">Windows Mixed Reality 台文件現在位於 docs.microsoft.com 平台，它會使用具備 GitHub 特色的 Markdown （包含 Markdig 功能）。</span><span class="sxs-lookup"><span data-stu-id="e221b-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="e221b-107">基本上，您在此存放庫中編輯的內容取得轉換成在顯示的格式化和樣式化頁面 https://docs.microsoft.com/windows/mixed-reality。</span><span class="sxs-lookup"><span data-stu-id="e221b-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="e221b-108">本頁涵蓋基本的步驟和指導方針的貢獻，以及連結至 Markdown 基本概念。</span><span class="sxs-lookup"><span data-stu-id="e221b-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="e221b-109">感謝您為您的貢獻的 ！</span><span class="sxs-lookup"><span data-stu-id="e221b-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="e221b-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="e221b-110">Before you start</span></span>

<span data-ttu-id="e221b-111">如果您還沒有做，您必須[建立 GitHub 帳戶](https://github.com/join)。</span><span class="sxs-lookup"><span data-stu-id="e221b-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="e221b-112">如果您是 Microsoft 員工，連結您的 GitHub 帳戶，以您的 Microsoft 別名[Microsoft 開放原始碼入口網站](https://repos.opensource.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="e221b-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="e221b-113">聯結 **「 Microsoft 」** 並 **"MicrosoftDocs"** 組織)。</span><span class="sxs-lookup"><span data-stu-id="e221b-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="e221b-114">當設定您的 GitHub 帳戶，我們也建議這些安全性預防措施：</span><span class="sxs-lookup"><span data-stu-id="e221b-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="e221b-115">建立[您的 Github 帳戶的強式密碼](https://github.com/settings/admin)。</span><span class="sxs-lookup"><span data-stu-id="e221b-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="e221b-116">啟用[雙因素驗證](https://github.com/settings/two_factor_authentication/configure)。</span><span class="sxs-lookup"><span data-stu-id="e221b-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="e221b-117">儲存您[復原碼](https://github.com/settings/auth/recovery-codes)在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="e221b-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="e221b-118">更新您[公用設定檔設定](https://github.com/settings/profile)。</span><span class="sxs-lookup"><span data-stu-id="e221b-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="e221b-119">設定您的名稱，並請考慮將您*公用電子郵件*要*不會顯示我的電子郵件地址*。</span><span class="sxs-lookup"><span data-stu-id="e221b-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="e221b-120">我們建議您上傳個人檔案圖片，因為您參與 docs 頁面上會顯示縮圖。</span><span class="sxs-lookup"><span data-stu-id="e221b-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="e221b-121">如果您打算使用的命令列工作流程，請考慮設定[Windows 的 Git 認證管理員](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)，讓您不必每次輸入您的密碼進行貢獻。</span><span class="sxs-lookup"><span data-stu-id="e221b-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="e221b-122">執行這些步驟，是很重要，因為發行系統連至 GitHub，而且您將會列為作者或參與者使用 GitHub 別名每一個發行項。</span><span class="sxs-lookup"><span data-stu-id="e221b-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="e221b-123">編輯現有的發行項</span><span class="sxs-lookup"><span data-stu-id="e221b-123">Editing an existing article</span></span>

<span data-ttu-id="e221b-124">使用下列工作流程進行更新才能*現有的發行項*透過網頁瀏覽器的 GitHub:</span><span class="sxs-lookup"><span data-stu-id="e221b-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="e221b-125">瀏覽至您想要編輯的 「 混合實境-文件 」 資料夾中的文件。</span><span class="sxs-lookup"><span data-stu-id="e221b-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="e221b-126">選取右上角的 [編輯] 按鈕 （鉛筆圖示）。</span><span class="sxs-lookup"><span data-stu-id="e221b-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="e221b-127">這會自動將分支，則以 「 主要 」 分支可處置分支。</span><span class="sxs-lookup"><span data-stu-id="e221b-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![編輯文章。](images/editpage.png)
3. <span data-ttu-id="e221b-129">編輯文章的內容 (請參閱[< Markdown 基本概念 >](#markdown-basics)以下指導方針)。</span><span class="sxs-lookup"><span data-stu-id="e221b-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="e221b-130">更新為上方的每個發行項相關的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="e221b-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="e221b-131">標題：這是要檢視發行項時，會出現在瀏覽器索引標籤頁面標題。</span><span class="sxs-lookup"><span data-stu-id="e221b-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="e221b-132">這是用於 SEO 和編製索引，您就不應該變更標題，除非必要 （但文件會公開之前，這是較不重要）。</span><span class="sxs-lookup"><span data-stu-id="e221b-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="e221b-133">描述：撰寫文章的內容的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="e221b-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="e221b-134">這可協助 SEO 和探索。</span><span class="sxs-lookup"><span data-stu-id="e221b-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="e221b-135">作者：如果您是主要的擁有者的頁面，新增您的 GitHub 別名。</span><span class="sxs-lookup"><span data-stu-id="e221b-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="e221b-136">ms.author:如果您是主要的擁有者的頁面，新增您的 Microsoft 別名這裡 (您不需要@microsoft.com，只要的別名)。</span><span class="sxs-lookup"><span data-stu-id="e221b-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="e221b-137">ms.date:如果您是將主要的內容新增到頁面上，而不是進一步釐清，格式文法，例如修正或拼字檢查，請更新的日期。</span><span class="sxs-lookup"><span data-stu-id="e221b-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="e221b-138">關鍵字：關鍵字可協助 SEO （搜尋引擎最佳化）。</span><span class="sxs-lookup"><span data-stu-id="e221b-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="e221b-139">加入關鍵字，就以逗號和空格分隔專屬於您的文章 （但清單中最後一個關鍵字後面的任何標點符號）;您不需要加入全域套用至所有的發行項的關鍵字，因為這些在其他地方管理。</span><span class="sxs-lookup"><span data-stu-id="e221b-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="e221b-140">當您完成您的文件編輯時，向下捲動並按一下**建議檔案變更** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e221b-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="e221b-141">在下一步 頁面上，按一下**建立提取要求**至您自動建立的分支合併至 'master'。</span><span class="sxs-lookup"><span data-stu-id="e221b-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="e221b-142">下一步 您想要編輯的發行項重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="e221b-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="e221b-143">建立新文章</span><span class="sxs-lookup"><span data-stu-id="e221b-143">Creating a new article</span></span>

<span data-ttu-id="e221b-144">使用下列工作流程*建立新的文章*透過 GitHub 的網頁瀏覽器中的文件存放庫中：</span><span class="sxs-lookup"><span data-stu-id="e221b-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="e221b-145">建立分支的 MicrosoftDocs/混合實境 'master' 分支 (使用**分岔**右上角的按鈕)。</span><span class="sxs-lookup"><span data-stu-id="e221b-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![分叉的主要分支。](images/forkbranch.png)
2. <span data-ttu-id="e221b-147">在 「 混合實境-文件 」 資料夾中，按一下**建立新檔案**右上角的按鈕。</span><span class="sxs-lookup"><span data-stu-id="e221b-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="e221b-148">建立發行項的頁面名稱 （而不是空白使用連字號和不會使用標點符號或單引號），並將附加".md"</span><span class="sxs-lookup"><span data-stu-id="e221b-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![命名您的新頁面。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="e221b-150">請確定您建立新的發行項的 「 混合實境-文件 」 資料夾內。</span><span class="sxs-lookup"><span data-stu-id="e221b-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="e221b-151">您可以藉由檢查來確認此 「 混合實境 docs /"的新檔案名稱行中。</span><span class="sxs-lookup"><span data-stu-id="e221b-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="e221b-152">在您的新頁面頂端，加入下列的中繼資料區塊：</span><span class="sxs-lookup"><span data-stu-id="e221b-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="e221b-153">相關的中繼資料欄位，每個中的指示中填滿[節](#editing-an-existing-article)。</span><span class="sxs-lookup"><span data-stu-id="e221b-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="e221b-154">寫入本文內容中使用[Markdown 基本概念](#markdown-basics)。</span><span class="sxs-lookup"><span data-stu-id="e221b-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="e221b-155">新增`## See also`區段底部的其他相關文章連結的文章。</span><span class="sxs-lookup"><span data-stu-id="e221b-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="e221b-156">完成後，按一下**認可新的檔案**。</span><span class="sxs-lookup"><span data-stu-id="e221b-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="e221b-157">按一下 **新的提取要求**和您的分叉 'master' 分支合併至 MicrosoftDocs/混合實境 'master' （請確定箭頭所指向的正確方式）。</span><span class="sxs-lookup"><span data-stu-id="e221b-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![從您的分支建立提取要求，至 MicrosoftDocs/混合實境](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="e221b-159">Markdown 基本概念</span><span class="sxs-lookup"><span data-stu-id="e221b-159">Markdown basics</span></span>

<span data-ttu-id="e221b-160">下列資源將協助您了解如何編輯使用之 Markdown 語言的文件：</span><span class="sxs-lookup"><span data-stu-id="e221b-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="e221b-161">Markdown 基本概念</span><span class="sxs-lookup"><span data-stu-id="e221b-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="e221b-162">Markdown 在-快速參考海報</span><span class="sxs-lookup"><span data-stu-id="e221b-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="e221b-163">適用於撰寫 docs.microsoft.com 的 Markdown 其他資源</span><span class="sxs-lookup"><span data-stu-id="e221b-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="e221b-164">加入資料表</span><span class="sxs-lookup"><span data-stu-id="e221b-164">Adding tables</span></span>

<span data-ttu-id="e221b-165">方式 docs.microsoft.com 樣式資料表，因為他們不需要框線或自訂的樣式，即使您嘗試內嵌 CSS。</span><span class="sxs-lookup"><span data-stu-id="e221b-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="e221b-166">它會顯示適用於一段時間，但最後的平台會去除移出資料表樣式。</span><span class="sxs-lookup"><span data-stu-id="e221b-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="e221b-167">因此請事先規劃，並簡化您的資料表。</span><span class="sxs-lookup"><span data-stu-id="e221b-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="e221b-168">[以下是站台，以簡化 Markdown 表格](http://www.tablesgenerator.com/markdown_tables)。</span><span class="sxs-lookup"><span data-stu-id="e221b-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="e221b-169">[適用於 Visual Studio Code 的 Docs Markdown 延伸模組](https://docs.microsoft.com/teamblog/docs-extension)也會使資料表產生簡單，如果您使用[Visual Studio Code （如下所示）](#using-visual-studio-code)編輯文件。</span><span class="sxs-lookup"><span data-stu-id="e221b-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="e221b-170">加入影像</span><span class="sxs-lookup"><span data-stu-id="e221b-170">Adding images</span></span>

<span data-ttu-id="e221b-171">您必須上傳您的映像到 「 混合實境-docs/映像 」 資料夾中存放庫，然後文件中適當地參考它們。</span><span class="sxs-lookup"><span data-stu-id="e221b-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="e221b-172">映像會自動顯示在觀看完整大小，這表示如果您的映像很大，這樣就能填入文件的整個寬度。</span><span class="sxs-lookup"><span data-stu-id="e221b-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="e221b-173">因此，我們建議您預先調整大小之前將其上傳的映像。</span><span class="sxs-lookup"><span data-stu-id="e221b-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="e221b-174">建議的寬度是介於 600 到 700 的像素，但您應該調整大小增加或相應減少如果分別是密集的螢幕擷取畫面或螢幕擷取畫面中，一小部分。</span><span class="sxs-lookup"><span data-stu-id="e221b-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e221b-175">您可以只上傳映像至您分支存放庫在合併之前。</span><span class="sxs-lookup"><span data-stu-id="e221b-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="e221b-176">因此，如果您打算將映像新增至發行項，您必須[使用 Visual Studio Code](#using-visual-studio-code)第一次將映像加入至您分叉的 「 映像 」 資料夾或請確定您已完成的網頁瀏覽器中的下列：</span><span class="sxs-lookup"><span data-stu-id="e221b-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="e221b-177">分叉 MicrosoftDocs/混合實境存放庫。</span><span class="sxs-lookup"><span data-stu-id="e221b-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="e221b-178">編輯您的分叉中的發行項。</span><span class="sxs-lookup"><span data-stu-id="e221b-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="e221b-179">上傳您分叉中參考的 「 混合實境-docs/映像 」 資料夾在文章中的映像。</span><span class="sxs-lookup"><span data-stu-id="e221b-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="e221b-180">建立**提取要求**至 MicrosoftDocs/混合實境 'master' 分支合併您的分叉。</span><span class="sxs-lookup"><span data-stu-id="e221b-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="e221b-181">若要了解如何設定您自己的分支存放庫，請遵循指示[建立新的發行項](#creating-a-new-article)。</span><span class="sxs-lookup"><span data-stu-id="e221b-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="e221b-182">預覽您的工作</span><span class="sxs-lookup"><span data-stu-id="e221b-182">Previewing your work</span></span>

<span data-ttu-id="e221b-183">在 GitHub 中編輯，透過網頁瀏覽器，您可以按一下**預覽** 索引標籤上方的頁面，即可預覽您的工作，然後再認可。</span><span class="sxs-lookup"><span data-stu-id="e221b-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="e221b-184">預覽 review.docs.microsoft.com 變更只會提供給 Microsoft 的員工</span><span class="sxs-lookup"><span data-stu-id="e221b-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="e221b-185">Microsoft 員工： 一旦您的參與已合併至 「 主要 」 分支，您可以看到之前它會在公用文件的外觀 https://review.docs.microsoft.com/windows/mixed-reality?branch=master（找到您的文章左側資料行中使用的目錄）。</span><span class="sxs-lookup"><span data-stu-id="e221b-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="e221b-186">在與編輯桌面用戶端瀏覽器中編輯</span><span class="sxs-lookup"><span data-stu-id="e221b-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="e221b-187">在瀏覽器中編輯是最簡單的方式進行快速變更，不過，有幾個缺點：</span><span class="sxs-lookup"><span data-stu-id="e221b-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="e221b-188">您無法取得拼字檢查。</span><span class="sxs-lookup"><span data-stu-id="e221b-188">You don't get spell-check.</span></span>
- <span data-ttu-id="e221b-189">您無法取得任何智慧連結 （您必須以手動方式輸入文章的檔名） 的其他文章。</span><span class="sxs-lookup"><span data-stu-id="e221b-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="e221b-190">它可以上傳，並參考映像很麻煩。</span><span class="sxs-lookup"><span data-stu-id="e221b-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="e221b-191">如果您想而不處理這些問題，您可能想要使用桌上型電腦的用戶端，像是[Visual Studio Code](https://code.visualstudio.com/)幾[實用的擴充功能](#useful-extensions)來參與編輯文件。</span><span class="sxs-lookup"><span data-stu-id="e221b-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="e221b-192">使用 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e221b-192">Using Visual Studio Code</span></span>

<span data-ttu-id="e221b-193">原因列出[上述](#editing-in-the-browser-vs-editing-with-a-desktop-client)，您可能偏好使用編輯文件，而不是網頁瀏覽器的桌面用戶端。</span><span class="sxs-lookup"><span data-stu-id="e221b-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="e221b-194">我們建議您使用[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="e221b-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="e221b-195">安裝程式</span><span class="sxs-lookup"><span data-stu-id="e221b-195">Setup</span></span>

<span data-ttu-id="e221b-196">請遵循下列步驟來設定 Visual Studio Code，來處理此存放庫：</span><span class="sxs-lookup"><span data-stu-id="e221b-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="e221b-197">在 web 瀏覽器：</span><span class="sxs-lookup"><span data-stu-id="e221b-197">In a web browser:</span></span>
    1. <span data-ttu-id="e221b-198">安裝[針對您的電腦的 Git](https://git-scm.com/downloads)。</span><span class="sxs-lookup"><span data-stu-id="e221b-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="e221b-199">安裝[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="e221b-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="e221b-200">[派生 MicrosoftDocs/混合實境](#creating-a-new-article)如果您還沒有這麼做。</span><span class="sxs-lookup"><span data-stu-id="e221b-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="e221b-201">在您的分叉中，按一下**複製或下載**並複製 URL。</span><span class="sxs-lookup"><span data-stu-id="e221b-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="e221b-202">在 Visual Studio Code 建立分叉的本機複製品：</span><span class="sxs-lookup"><span data-stu-id="e221b-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="e221b-203">從**檢視**功能表上，選取**命令選擇區**。</span><span class="sxs-lookup"><span data-stu-id="e221b-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="e221b-204">類型"Git:Clone。 」</span><span class="sxs-lookup"><span data-stu-id="e221b-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="e221b-205">貼上您剛才複製的 URL。</span><span class="sxs-lookup"><span data-stu-id="e221b-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="e221b-206">選擇您的電腦上儲存複製的位置。</span><span class="sxs-lookup"><span data-stu-id="e221b-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="e221b-207">按一下 **開啟的存放庫**快顯視窗中。</span><span class="sxs-lookup"><span data-stu-id="e221b-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="e221b-208">編輯文件</span><span class="sxs-lookup"><span data-stu-id="e221b-208">Editing documentation</span></span>

<span data-ttu-id="e221b-209">使用下列工作流程來進行使用 Visual Studio Code 文件中的變更：</span><span class="sxs-lookup"><span data-stu-id="e221b-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="e221b-210">所有的指導方針[編輯](#editing-an-existing-article)並[建立](#creating-a-new-article)文章，和[的編輯 Markdown 基本概念](#markdown-basics)，上述適用於當也使用 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="e221b-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="e221b-211">請確定您複製的 「 分叉 」 是最新的官方存放庫。</span><span class="sxs-lookup"><span data-stu-id="e221b-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="e221b-212">在 web 瀏覽器中建立提取要求，以同步處理來自其他參與者 MicrosoftDocs/混合實境 'master' 中最近的變更至您的分叉 （請確定箭頭所指向正確的方式）。</span><span class="sxs-lookup"><span data-stu-id="e221b-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![同步處理從 MicrosoftDocs/混合實境中的變更至您的分叉](images/sync_repos.PNG)
   2. <span data-ttu-id="e221b-214">在 Visual Studio Code 中，按一下 [同步處理您剛更新的分叉的本機複本的同步處理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e221b-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![按一下 [同步] 按鈕](images/sync_clone.png)
2. <span data-ttu-id="e221b-216">建立或編輯您使用 Visual Studio Code 的複製存放庫中的文章。</span><span class="sxs-lookup"><span data-stu-id="e221b-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="e221b-217">編輯 （如有必要，映像新增到 「 映像 」 資料夾） 中的一或多個發行項。</span><span class="sxs-lookup"><span data-stu-id="e221b-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="e221b-218">**儲存**中變更**總管**。</span><span class="sxs-lookup"><span data-stu-id="e221b-218">**Save** changes in **Explorer**.</span></span>
      
      ![在 [總管] 中選擇 [全部儲存]](images/explorer_save.png)
   3. <span data-ttu-id="e221b-220">**全部認可**中變更**原始檔控制**（寫入認可訊息出現提示時）。</span><span class="sxs-lookup"><span data-stu-id="e221b-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![選擇 「 全部認可 」 在原始檔控制](images/source_control_commit.png)
   4. <span data-ttu-id="e221b-222">按一下 [**同步**變更回原始 （您在 GitHub 上的分支） 的同步處理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e221b-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![按一下 [同步] 按鈕](images/sync_back.png)
3. <span data-ttu-id="e221b-224">在 web 瀏覽器中，建立 提取要求，以同步處理回到 MicrosoftDocs/混合實境 'master' 分支中的新變更 （請確定箭頭所指向的正確方式）。</span><span class="sxs-lookup"><span data-stu-id="e221b-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![從您的分支建立提取要求，至 MicrosoftDocs/混合實境](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="e221b-226">實用的擴充功能</span><span class="sxs-lookup"><span data-stu-id="e221b-226">Useful extensions</span></span>

<span data-ttu-id="e221b-227">編輯文件時，下列 Visual Studio Code 擴充功能就非常有用：</span><span class="sxs-lookup"><span data-stu-id="e221b-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="e221b-228">[適用於 Visual Studio Code 的 docs Markdown 延伸模組](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)-使用**Alt + M**來顯示功能表的 docs 編寫選項，例如：</span><span class="sxs-lookup"><span data-stu-id="e221b-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="e221b-229">您已上傳的影像搜尋和參考。</span><span class="sxs-lookup"><span data-stu-id="e221b-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="e221b-230">加入格式化的清單、 資料表、 docs 特定圖說喜歡也`>[!NOTE]`。</span><span class="sxs-lookup"><span data-stu-id="e221b-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="e221b-231">搜尋和參考內部連結和書籤 （在頁面內的特定區段的連結）。</span><span class="sxs-lookup"><span data-stu-id="e221b-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="e221b-232">格式錯誤會反白顯示 （停留在要了解更多的錯誤）。</span><span class="sxs-lookup"><span data-stu-id="e221b-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="e221b-233">[拼字檢查工具的程式碼](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-拼錯的單字會加上底線，以滑鼠右鍵按一下拼錯的字，將它變更，或將它儲存至字典。</span><span class="sxs-lookup"><span data-stu-id="e221b-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
