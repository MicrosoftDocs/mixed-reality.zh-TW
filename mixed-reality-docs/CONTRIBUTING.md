---
title: 參與指示
description: 如何參與 Windows Mixed Reality 檔。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516173"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="36317-103">參與 Windows Mixed Reality 開發人員檔</span><span class="sxs-lookup"><span data-stu-id="36317-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="36317-104">歡迎使用[Windows Mixed Reality 開發人員檔的公用](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)存放庫!</span><span class="sxs-lookup"><span data-stu-id="36317-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="36317-105">您在此存放庫中建立或編輯的任何文章,**都將可供公眾看見。**</span><span class="sxs-lookup"><span data-stu-id="36317-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="36317-106">Windows Mixed Reality 檔現在位於 docs.microsoft.com 平臺上, 其使用 GitHub flavored Markdown (含 Markdig 功能)。</span><span class="sxs-lookup"><span data-stu-id="36317-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="36317-107">基本上, 您在此存放庫中編輯的內容, 會轉換成顯示在上 https://docs.microsoft.com/windows/mixed-reality 的格式化和樣式頁面。</span><span class="sxs-lookup"><span data-stu-id="36317-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="36317-108">本頁涵蓋參與的基本步驟和指導方針, 以及 Markdown 基本概念的連結。</span><span class="sxs-lookup"><span data-stu-id="36317-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="36317-109">感謝您的貢獻!</span><span class="sxs-lookup"><span data-stu-id="36317-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="36317-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="36317-110">Before you start</span></span>

<span data-ttu-id="36317-111">如果您還沒有帳戶, 您必須[建立一個 GitHub 帳戶](https://github.com/join)。</span><span class="sxs-lookup"><span data-stu-id="36317-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="36317-112">如果您是 Microsoft 員工, 請將您的 GitHub 帳戶連結到[Microsoft 開放原始碼入口網站](https://repos.opensource.microsoft.com/)上的 microsoft 別名。</span><span class="sxs-lookup"><span data-stu-id="36317-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="36317-113">加入 **"Microsoft"** 和 **"MicrosoftDocs"** 組織)。</span><span class="sxs-lookup"><span data-stu-id="36317-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="36317-114">在設定您的 GitHub 帳戶時, 我們也建議這些安全性預防措施:</span><span class="sxs-lookup"><span data-stu-id="36317-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="36317-115">[為您的 Github 帳戶建立強式密碼](https://github.com/settings/admin)。</span><span class="sxs-lookup"><span data-stu-id="36317-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="36317-116">啟用[雙因素驗證](https://github.com/settings/two_factor_authentication/configure)。</span><span class="sxs-lookup"><span data-stu-id="36317-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="36317-117">將您的復原程式[代碼](https://github.com/settings/auth/recovery-codes)儲存在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="36317-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="36317-118">更新您的[公用設定檔設定](https://github.com/settings/profile)。</span><span class="sxs-lookup"><span data-stu-id="36317-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="36317-119">設定您的名稱, 並考慮將您的*公用電子郵件*設定為*不顯示我的電子郵件地址*。</span><span class="sxs-lookup"><span data-stu-id="36317-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="36317-120">我們建議您上傳個人資料圖片, 因為縮圖會顯示在您所參與的檔頁面上。</span><span class="sxs-lookup"><span data-stu-id="36317-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="36317-121">如果您打算使用命令列工作流程, 請考慮設定[適用于 Windows 的 Git 認證管理員](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest), 如此一來, 您就不需要在每次進行貢獻時都輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="36317-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="36317-122">採取這些步驟很重要, 因為發佈系統會系結至 GitHub, 而您會使用 GitHub 別名, 將您列為每篇文章的作者或參與者。</span><span class="sxs-lookup"><span data-stu-id="36317-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="36317-123">編輯現有的文章</span><span class="sxs-lookup"><span data-stu-id="36317-123">Editing an existing article</span></span>

<span data-ttu-id="36317-124">使用下列工作流程, 透過 web 瀏覽器中的 GitHub 對*現有文章*進行更新:</span><span class="sxs-lookup"><span data-stu-id="36317-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="36317-125">流覽至您想要在「混合式-檔」資料夾中編輯的文章。</span><span class="sxs-lookup"><span data-stu-id="36317-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="36317-126">選取右上方的 [編輯] 按鈕 (鉛筆圖示)。</span><span class="sxs-lookup"><span data-stu-id="36317-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="36317-127">這會自動將可處置分支從「主要」分支中派生出來。</span><span class="sxs-lookup"><span data-stu-id="36317-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![編輯文章。](images/editpage.png)
3. <span data-ttu-id="36317-129">編輯文章的內容 (請參閱下方的「 [Markdown 基本概念](#markdown-basics)」, 以取得指導方針)。</span><span class="sxs-lookup"><span data-stu-id="36317-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="36317-130">在每篇文章的頂端更新相關中繼資料:</span><span class="sxs-lookup"><span data-stu-id="36317-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="36317-131">主題這是在查看發行項時, 出現在 [瀏覽器] 索引標籤中的頁面標題。</span><span class="sxs-lookup"><span data-stu-id="36317-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="36317-132">因為這是用於 SEO 和編制索引, 除非必要, 否則不應變更標題 (雖然這在檔公開之前較不重要)。</span><span class="sxs-lookup"><span data-stu-id="36317-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="36317-133">描述撰寫文章內容的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="36317-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="36317-134">這有助於 SEO 和探索。</span><span class="sxs-lookup"><span data-stu-id="36317-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="36317-135">授權如果您是網頁的主要擁有者, 請在這裡新增您的 GitHub 別名。</span><span class="sxs-lookup"><span data-stu-id="36317-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="36317-136">ms. author:如果您是網頁的主要擁有者, 請在這裡新增您的 Microsoft 別名 (不@microsoft.com需要, 只是別名)。</span><span class="sxs-lookup"><span data-stu-id="36317-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="36317-137">ms. date:如果您要在頁面中新增主要內容, 而不是針對說明、格式、文法或拼寫等修正程式, 請更新日期。</span><span class="sxs-lookup"><span data-stu-id="36317-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="36317-138">字關鍵字有助於 SEO (搜尋引擎優化)。</span><span class="sxs-lookup"><span data-stu-id="36317-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="36317-139">以逗號和空格分隔特定于您文章的關鍵字 (但清單中的最後一個關鍵字後面沒有標點符號);您不需要新增適用于所有發行項的全域關鍵字, 因為這些專案是在其他地方管理。</span><span class="sxs-lookup"><span data-stu-id="36317-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="36317-140">當您完成文章編輯後, 請向下卷, 然後按一下 [**提議檔案變更**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="36317-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="36317-141">在下一個頁面上, 按一下 [**建立提取要求**], 將自動建立的分支合併至 [master]。</span><span class="sxs-lookup"><span data-stu-id="36317-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="36317-142">針對您想要編輯的下一篇文章, 重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="36317-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="36317-143">建立新的文章</span><span class="sxs-lookup"><span data-stu-id="36317-143">Creating a new article</span></span>

<span data-ttu-id="36317-144">使用下列工作流程, 透過 web 瀏覽器中的 GitHub 在檔存放庫中*建立新的文章*:</span><span class="sxs-lookup"><span data-stu-id="36317-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="36317-145">使用右上方的 [**分叉**] 按鈕, 從 MicrosoftDocs/混合現實的「主要」分支建立分叉。</span><span class="sxs-lookup"><span data-stu-id="36317-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![將 master 分支派生。](images/forkbranch.png)
2. <span data-ttu-id="36317-147">在 [混合式-檔] 資料夾中, 按一下右上方的 [**建立新**檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="36317-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="36317-148">建立發行項的頁面名稱 (使用連字號, 而不是空格, 不要使用標點符號或單引號) 並附加 "md"</span><span class="sxs-lookup"><span data-stu-id="36317-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![為新頁面命名。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="36317-150">請確定您是從「混合現實檔」資料夾內建立新的文章。</span><span class="sxs-lookup"><span data-stu-id="36317-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="36317-151">您可以在新的檔案名行中檢查 "/mixed-reality-docs/" 來確認這一點。</span><span class="sxs-lookup"><span data-stu-id="36317-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="36317-152">在新頁面的頂端, 新增下列中繼資料區塊:</span><span class="sxs-lookup"><span data-stu-id="36317-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="36317-153">根據[上一節](#editing-an-existing-article)中的指示填入相關的元資料欄位。</span><span class="sxs-lookup"><span data-stu-id="36317-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="36317-154">使用[Markdown 基本概念](#markdown-basics)撰寫文章內容。</span><span class="sxs-lookup"><span data-stu-id="36317-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="36317-155">在本文`## See also`底部新增一個區段, 並提供其他相關文章的連結。</span><span class="sxs-lookup"><span data-stu-id="36317-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="36317-156">完成後, 按一下 [**認可新**檔案]。</span><span class="sxs-lookup"><span data-stu-id="36317-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="36317-157">按一下 [**新增提取要求**], 並將分叉的「主要」分支合併到 MicrosoftDocs/mixed-reality ' master ' (請確定箭號是以正確的方式指向)。</span><span class="sxs-lookup"><span data-stu-id="36317-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![從您的分支建立提取要求至 MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="36317-159">Markdown 基本概念</span><span class="sxs-lookup"><span data-stu-id="36317-159">Markdown basics</span></span>

<span data-ttu-id="36317-160">下列資源將協助您瞭解如何使用 Markdown 語言來編輯檔:</span><span class="sxs-lookup"><span data-stu-id="36317-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="36317-161">Markdown 基本概念</span><span class="sxs-lookup"><span data-stu-id="36317-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="36317-162">Markdown 概覽的參考海報</span><span class="sxs-lookup"><span data-stu-id="36317-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="36317-163">為 docs.microsoft.com 撰寫 Markdown 的其他資源</span><span class="sxs-lookup"><span data-stu-id="36317-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="36317-164">加入資料表</span><span class="sxs-lookup"><span data-stu-id="36317-164">Adding tables</span></span>

<span data-ttu-id="36317-165">由於 docs.microsoft.com 樣式表的方式, 它們不會有框線或自訂樣式, 即使您嘗試內嵌 CSS 也一樣。</span><span class="sxs-lookup"><span data-stu-id="36317-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="36317-166">它會在短時間內出現, 但最終平臺會從資料表中去除樣式。</span><span class="sxs-lookup"><span data-stu-id="36317-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="36317-167">所以請先行規劃, 讓資料表保持簡單。</span><span class="sxs-lookup"><span data-stu-id="36317-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="36317-168">[以下是讓 Markdown 資料表變得簡單的網站](http://www.tablesgenerator.com/markdown_tables)。</span><span class="sxs-lookup"><span data-stu-id="36317-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="36317-169">如果您使用[Visual Studio Code (請參閱下文)](#using-visual-studio-code)來編輯檔, 則 Visual Studio Code 的檔[Markdown 擴充](https://docs.microsoft.com/teamblog/docs-extension)功能也可讓您輕鬆產生資料表。</span><span class="sxs-lookup"><span data-stu-id="36317-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="36317-170">新增影像</span><span class="sxs-lookup"><span data-stu-id="36317-170">Adding images</span></span>

<span data-ttu-id="36317-171">您必須將映射上傳至存放庫中的「混合式-檔/影像」資料夾, 然後在文章中適當地加以參考。</span><span class="sxs-lookup"><span data-stu-id="36317-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="36317-172">影像會自動以完整大小顯示, 這表示如果您的影像很大, 則會填滿整篇文章的寬度。</span><span class="sxs-lookup"><span data-stu-id="36317-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="36317-173">因此, 建議您在上傳映射之前預先調整其大小。</span><span class="sxs-lookup"><span data-stu-id="36317-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="36317-174">建議的寬度介於600和700圖元之間, 不過, 如果它是密集螢幕擷取畫面或螢幕擷取畫面的一部分, 則您應該將大小調整為相應增加或相應減少。</span><span class="sxs-lookup"><span data-stu-id="36317-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="36317-175">在合併之前, 您只能將影像上傳至分支存放庫。</span><span class="sxs-lookup"><span data-stu-id="36317-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="36317-176">因此, 如果您打算將影像新增至文章, 則必須先[使用 Visual Studio Code](#using-visual-studio-code)將影像新增至您分叉的「影像」資料夾, 或確認您已在網頁瀏覽器中完成下列動作:</span><span class="sxs-lookup"><span data-stu-id="36317-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="36317-177">分支 MicrosoftDocs/mixed reality 存放庫。</span><span class="sxs-lookup"><span data-stu-id="36317-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="36317-178">已在您的分叉中編輯文章。</span><span class="sxs-lookup"><span data-stu-id="36317-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="36317-179">已將您在文章中參考的影像上傳至您分叉中的「混合現實檔/影像」資料夾。</span><span class="sxs-lookup"><span data-stu-id="36317-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="36317-180">建立**提取要求**, 以將您的分叉合併到 MicrosoftDocs/mixed reality ' master ' 分支中。</span><span class="sxs-lookup"><span data-stu-id="36317-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="36317-181">若要瞭解如何設定您自己的分支存放庫, 請遵循[建立新文章](#creating-a-new-article)的指示。</span><span class="sxs-lookup"><span data-stu-id="36317-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="36317-182">預覽您的工作</span><span class="sxs-lookup"><span data-stu-id="36317-182">Previewing your work</span></span>

<span data-ttu-id="36317-183">當您透過網頁瀏覽器在 GitHub 中編輯時, 您可以按一下頁面頂端附近的 [**預覽**] 索引標籤, 以預覽您的工作, 然後再進行認可。</span><span class="sxs-lookup"><span data-stu-id="36317-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="36317-184">在 review.docs.microsoft.com 上預覽您的變更僅適用于 Microsoft 員工</span><span class="sxs-lookup"><span data-stu-id="36317-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="36317-185">Microsoft 員工: 當您的貢獻合併到「主要」分支之後, 您就可以在公開 https://review.docs.microsoft.com/windows/mixed-reality?branch=master 之前查看檔的樣子 (使用左欄中的目錄尋找您的文章)。</span><span class="sxs-lookup"><span data-stu-id="36317-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="36317-186">在瀏覽器中編輯與使用桌面用戶端編輯</span><span class="sxs-lookup"><span data-stu-id="36317-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="36317-187">在瀏覽器中編輯是進行快速變更的最簡單方式, 不過, 有幾個缺點:</span><span class="sxs-lookup"><span data-stu-id="36317-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="36317-188">您不會看到拼寫檢查。</span><span class="sxs-lookup"><span data-stu-id="36317-188">You don't get spell-check.</span></span>
- <span data-ttu-id="36317-189">您不會取得任何與其他文章的智慧型連結 (您必須手動輸入文章的檔案名)。</span><span class="sxs-lookup"><span data-stu-id="36317-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="36317-190">上傳和參考影像可能會很麻煩。</span><span class="sxs-lookup"><span data-stu-id="36317-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="36317-191">如果您不處理這些問題, 您可能會想要使用桌面用戶端 (例如[Visual Studio Code](https://code.visualstudio.com/) ), 並提供一些[實用的擴充](#useful-extensions)功能來貢獻檔。</span><span class="sxs-lookup"><span data-stu-id="36317-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="36317-192">使用 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="36317-192">Using Visual Studio Code</span></span>

<span data-ttu-id="36317-193">基於[上述](#editing-in-the-browser-vs-editing-with-a-desktop-client)原因, 您可能會偏好使用桌面用戶端來編輯檔, 而不是網頁瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="36317-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="36317-194">我們建議使用[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="36317-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="36317-195">安裝程式</span><span class="sxs-lookup"><span data-stu-id="36317-195">Setup</span></span>

<span data-ttu-id="36317-196">請遵循下列步驟來設定 Visual Studio Code 以使用此存放庫:</span><span class="sxs-lookup"><span data-stu-id="36317-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="36317-197">在網頁瀏覽器中:</span><span class="sxs-lookup"><span data-stu-id="36317-197">In a web browser:</span></span>
    1. <span data-ttu-id="36317-198">[為您的電腦安裝 Git](https://git-scm.com/downloads)。</span><span class="sxs-lookup"><span data-stu-id="36317-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="36317-199">安裝[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="36317-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="36317-200">[分叉 MicrosoftDocs/mixed-事實 (](#creating-a-new-article)如果您尚未這麼做)。</span><span class="sxs-lookup"><span data-stu-id="36317-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="36317-201">在您的分支中, 按一下 [**複製] 或 [下載**] 並複製 URL。</span><span class="sxs-lookup"><span data-stu-id="36317-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="36317-202">在 Visual Studio Code 中建立分支的本機複製:</span><span class="sxs-lookup"><span data-stu-id="36317-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="36317-203">從 [ **View** ] 功能表中, 選取 [**命令**選擇區]。</span><span class="sxs-lookup"><span data-stu-id="36317-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="36317-204">輸入「Git: Clone」。</span><span class="sxs-lookup"><span data-stu-id="36317-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="36317-205">貼上您剛才複製的 URL。</span><span class="sxs-lookup"><span data-stu-id="36317-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="36317-206">選擇要將複製儲存在電腦上的位置。</span><span class="sxs-lookup"><span data-stu-id="36317-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="36317-207">在快顯視窗中, 按一下 [**開啟**存放庫]。</span><span class="sxs-lookup"><span data-stu-id="36317-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="36317-208">編輯檔</span><span class="sxs-lookup"><span data-stu-id="36317-208">Editing documentation</span></span>

<span data-ttu-id="36317-209">使用下列工作流程, 利用 Visual Studio Code 來變更檔集:</span><span class="sxs-lookup"><span data-stu-id="36317-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="36317-210">當您使用 Visual Studio Code 時, 所有[編輯](#editing-an-existing-article)和[建立](#creating-a-new-article)文章的指引, 以及[編輯 Markdown 的基本概念](#markdown-basics)也適用。</span><span class="sxs-lookup"><span data-stu-id="36317-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="36317-211">請確定您的已複製分支已與官方存放庫保持在最新狀態。</span><span class="sxs-lookup"><span data-stu-id="36317-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="36317-212">在網頁瀏覽器中, 建立提取要求, 將最近的變更從 MicrosoftDocs/mixed-現實 ' master ' 中的其他參與者同步處理至您的分支 (請確定箭號是正確的方式)。</span><span class="sxs-lookup"><span data-stu-id="36317-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![將 MicrosoftDocs/mixed-reality 的變更同步處理至您的分支](images/sync_repos.PNG)
   2. <span data-ttu-id="36317-214">在 Visual Studio Code 中, 按一下 [同步處理] 按鈕, 將您剛剛更新的分支同步處理到本機複本。</span><span class="sxs-lookup"><span data-stu-id="36317-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![按一下 [同步處理] 按鈕](images/sync_clone.png)
2. <span data-ttu-id="36317-216">使用 Visual Studio Code, 在複製的存放庫中建立或編輯文章。</span><span class="sxs-lookup"><span data-stu-id="36317-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="36317-217">編輯一或多篇文章 (如有需要, 將影像新增至 [映射] 資料夾)。</span><span class="sxs-lookup"><span data-stu-id="36317-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="36317-218">**儲存** **Explorer**中的變更。</span><span class="sxs-lookup"><span data-stu-id="36317-218">**Save** changes in **Explorer**.</span></span>
      
      ![在 Explorer 中選擇 [全部儲存]](images/explorer_save.png)
   3. <span data-ttu-id="36317-220">**認可** **原始檔控制**中的所有變更 (出現提示時寫入認可訊息)。</span><span class="sxs-lookup"><span data-stu-id="36317-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![選擇原始檔控制中的 [全部認可]](images/source_control_commit.png)
   4. <span data-ttu-id="36317-222">按一下 [**同步**] 按鈕, 將您的變更同步處理回原始 (GitHub 上的分支)。</span><span class="sxs-lookup"><span data-stu-id="36317-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![按一下 [同步處理] 按鈕](images/sync_back.png)
3. <span data-ttu-id="36317-224">在網頁瀏覽器中, 建立提取要求, 將您分支中的新變更同步處理回到 MicrosoftDocs/mixed-現實 ' master ' (請確定箭號指向正確的方式)。</span><span class="sxs-lookup"><span data-stu-id="36317-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![從您的分支建立提取要求至 MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="36317-226">有用的擴充功能</span><span class="sxs-lookup"><span data-stu-id="36317-226">Useful extensions</span></span>

<span data-ttu-id="36317-227">編輯檔時, 下列 Visual Studio Code 擴充功能非常有用:</span><span class="sxs-lookup"><span data-stu-id="36317-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="36317-228">[適用于 Visual Studio Code 的檔 Markdown 延伸](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)模組-使用**Alt + M**來顯示檔撰寫選項的功能表, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="36317-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="36317-229">搜尋並參考您已上傳的影像。</span><span class="sxs-lookup"><span data-stu-id="36317-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="36317-230">加入格式如清單、資料表和檔特定的呼叫, 例如`>[!NOTE]`。</span><span class="sxs-lookup"><span data-stu-id="36317-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="36317-231">搜尋和參考內部連結和書簽 (頁面內特定區段的連結)。</span><span class="sxs-lookup"><span data-stu-id="36317-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="36317-232">格式化錯誤會反白顯示 (將滑鼠停留在錯誤上方以深入瞭解)。</span><span class="sxs-lookup"><span data-stu-id="36317-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="36317-233">程式[代碼拼寫檢查](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-拼錯的單字會加上底線;以滑鼠右鍵按一下拼錯的字組來加以變更, 或將它儲存至字典。</span><span class="sxs-lookup"><span data-stu-id="36317-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
