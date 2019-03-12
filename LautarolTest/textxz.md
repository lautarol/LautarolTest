---
title: Use markdown to format Microsoft Flow approvals | Microsoft Docs
description: Learn to use markdown to format Microsoft Flow approval requests.
services: ''
suite: flow
documentationcenter: na
author: gcorvera
manager: kfile
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 4/23/2018
ms.author: gcorvera
search.app:
  - Flow
search.audienceType:
  - flowmaker
  - enduser
---

# <a name="use-markdown-in-microsoft-flow-approval-requests"></a><span data-ttu-id="1834a-103">Use Markdown in Microsoft Flow approval requests</span><span class="sxs-lookup"><span data-stu-id="1834a-103">Use Markdown in Microsoft Flow approval requests</span></span>

<span data-ttu-id="1834a-104">This article teaches you how to use [Markdown](https://en.wikipedia.org/wiki/Markdown) syntax to add rich formatting and tables to your approval requests.</span><span class="sxs-lookup"><span data-stu-id="1834a-104">This article teaches you how to use [Markdown](https://en.wikipedia.org/wiki/Markdown) syntax to add rich formatting and tables to your approval requests.</span></span>

## <a name="headers"></a><span data-ttu-id="1834a-105">Headers</span><span class="sxs-lookup"><span data-stu-id="1834a-105">Headers</span></span>

<span data-ttu-id="1834a-106">Structure your comments using headers.</span><span class="sxs-lookup"><span data-stu-id="1834a-106">Structure your comments using headers.</span></span> <span data-ttu-id="1834a-107">Headers segment longer comments, making them easier to read.</span><span class="sxs-lookup"><span data-stu-id="1834a-107">Headers segment longer comments, making them easier to read.</span></span>

<span data-ttu-id="1834a-108">Start a line with a hash character `#` to set a heading.</span><span class="sxs-lookup"><span data-stu-id="1834a-108">Start a line with a hash character `#` to set a heading.</span></span> <span data-ttu-id="1834a-109">Organize your remarks with subheadings by starting a line with additional hash characters, for example `####`.</span><span class="sxs-lookup"><span data-stu-id="1834a-109">Organize your remarks with subheadings by starting a line with additional hash characters, for example `####`.</span></span> <span data-ttu-id="1834a-110">Up to six levels of headings are supported.</span><span class="sxs-lookup"><span data-stu-id="1834a-110">Up to six levels of headings are supported.</span></span>

<span data-ttu-id="1834a-111">**Example:**</span><span class="sxs-lookup"><span data-stu-id="1834a-111">**Example:**</span></span>

```Markdown
# This is a H1 header
## This is a H2 header
### This is a H3 header
#### This is a H4 header
##### This is a H5 header
```

<span data-ttu-id="1834a-112">**Result:**</span><span class="sxs-lookup"><span data-stu-id="1834a-112">**Result:**</span></span>

![Export flow](./media/approvals-markdown-support/mrkdown-headers.png)

## <a name="paragraphs-and-line-breaks"></a><span data-ttu-id="1834a-114">Paragraphs and line breaks</span><span class="sxs-lookup"><span data-stu-id="1834a-114">Paragraphs and line breaks</span></span>

<span data-ttu-id="1834a-115">Make your text easier to read by breaking it up with paragraphs or line breaks.</span><span class="sxs-lookup"><span data-stu-id="1834a-115">Make your text easier to read by breaking it up with paragraphs or line breaks.</span></span> <span data-ttu-id="1834a-116">Enter two spaces prior to the line break to begin a new paragraph, or enter two line breaks consecutively to begin a new paragraph.</span><span class="sxs-lookup"><span data-stu-id="1834a-116">Enter two spaces prior to the line break to begin a new paragraph, or enter two line breaks consecutively to begin a new paragraph.</span></span>   
   
<span data-ttu-id="1834a-117">**Example**</span><span class="sxs-lookup"><span data-stu-id="1834a-117">**Example**</span></span>

<pre>
Add lines between your text with the Enter key.
This spaces your text better and makes it easier to read.
</pre>

<span data-ttu-id="1834a-118">**Result:** </span><span class="sxs-lookup"><span data-stu-id="1834a-118">**Result:** </span></span>  
<span data-ttu-id="1834a-119">Add lines between your text with the Enter key.</span><span class="sxs-lookup"><span data-stu-id="1834a-119">Add lines between your text with the Enter key.</span></span>      
<span data-ttu-id="1834a-120">This spaces your text better and makes it easier to read.</span><span class="sxs-lookup"><span data-stu-id="1834a-120">This spaces your text better and makes it easier to read.</span></span>


<span data-ttu-id="1834a-121">**Example 2**</span><span class="sxs-lookup"><span data-stu-id="1834a-121">**Example 2**</span></span>

<pre>
Add two spaces prior to the end of the line.(space, space)     
This adds space in between paragraphs.
</pre>

<span data-ttu-id="1834a-122">**Result:**</span><span class="sxs-lookup"><span data-stu-id="1834a-122">**Result:**</span></span>  
<span data-ttu-id="1834a-123">Add two spaces prior to the end of the line.</span><span class="sxs-lookup"><span data-stu-id="1834a-123">Add two spaces prior to the end of the line.</span></span>   

<span data-ttu-id="1834a-124">This adds space in between paragraphs.</span><span class="sxs-lookup"><span data-stu-id="1834a-124">This adds space in between paragraphs.</span></span>
  

## <a name="lists"></a><span data-ttu-id="1834a-125">Lists</span><span class="sxs-lookup"><span data-stu-id="1834a-125">Lists</span></span>

<span data-ttu-id="1834a-126">Organize related items with lists.</span><span class="sxs-lookup"><span data-stu-id="1834a-126">Organize related items with lists.</span></span> <span data-ttu-id="1834a-127">You can add ordered lists with numbers, or unordered lists with just bullets.</span><span class="sxs-lookup"><span data-stu-id="1834a-127">You can add ordered lists with numbers, or unordered lists with just bullets.</span></span>

<span data-ttu-id="1834a-128">Ordered lists start with a number followed by a period for each list item.</span><span class="sxs-lookup"><span data-stu-id="1834a-128">Ordered lists start with a number followed by a period for each list item.</span></span> <span data-ttu-id="1834a-129">Unordered lists start with a `*`.</span><span class="sxs-lookup"><span data-stu-id="1834a-129">Unordered lists start with a `*`.</span></span> <span data-ttu-id="1834a-130">Begin each list item on a new line.</span><span class="sxs-lookup"><span data-stu-id="1834a-130">Begin each list item on a new line.</span></span> <span data-ttu-id="1834a-131">In a Markdown file or widget, enter two spaces prior to the line break to begin a new paragraph, or enter two line breaks consecutively to begin a new paragraph.</span><span class="sxs-lookup"><span data-stu-id="1834a-131">In a Markdown file or widget, enter two spaces prior to the line break to begin a new paragraph, or enter two line breaks consecutively to begin a new paragraph.</span></span>   

### <a name="ordered-or-numbered-lists"></a><span data-ttu-id="1834a-132">Ordered or numbered lists</span><span class="sxs-lookup"><span data-stu-id="1834a-132">Ordered or numbered lists</span></span>

<span data-ttu-id="1834a-133">**Example:**</span><span class="sxs-lookup"><span data-stu-id="1834a-133">**Example:**</span></span>

```Markdown
0. First item.
0. Second item.
0. Third item.
```

<span data-ttu-id="1834a-134">**Result:**</span><span class="sxs-lookup"><span data-stu-id="1834a-134">**Result:**</span></span>

1. <span data-ttu-id="1834a-135">First item.</span><span class="sxs-lookup"><span data-stu-id="1834a-135">First item.</span></span>
2. <span data-ttu-id="1834a-136">Second item.</span><span class="sxs-lookup"><span data-stu-id="1834a-136">Second item.</span></span>
3. <span data-ttu-id="1834a-137">Third item.</span><span class="sxs-lookup"><span data-stu-id="1834a-137">Third item.</span></span>

### <a name="bullet-lists"></a><span data-ttu-id="1834a-138">Bullet lists</span><span class="sxs-lookup"><span data-stu-id="1834a-138">Bullet lists</span></span>

<span data-ttu-id="1834a-139">**Example:**</span><span class="sxs-lookup"><span data-stu-id="1834a-139">**Example:**</span></span>

<pre>

- Item 1
- Item 2
- Item 3

</pre>

<span data-ttu-id="1834a-140">**Result:**</span><span class="sxs-lookup"><span data-stu-id="1834a-140">**Result:**</span></span>

- <span data-ttu-id="1834a-141">Item 1</span><span class="sxs-lookup"><span data-stu-id="1834a-141">Item 1</span></span>
- <span data-ttu-id="1834a-142">Item 2</span><span class="sxs-lookup"><span data-stu-id="1834a-142">Item 2</span></span>
- <span data-ttu-id="1834a-143">Item 3</span><span class="sxs-lookup"><span data-stu-id="1834a-143">Item 3</span></span>

### <a name="nested-lists"></a><span data-ttu-id="1834a-144">Nested lists</span><span class="sxs-lookup"><span data-stu-id="1834a-144">Nested lists</span></span>

<span data-ttu-id="1834a-145">**Example:**</span><span class="sxs-lookup"><span data-stu-id="1834a-145">**Example:**</span></span>
<pre>

1. First item.
   - Item 1
   - Item 2
   - Item 3
1. Second item.
   - Nested item 1
   - Nested item 2
   - Nested item 3

</pre>

<span data-ttu-id="1834a-146">**Result:**</span><span class="sxs-lookup"><span data-stu-id="1834a-146">**Result:**</span></span>  

1. <span data-ttu-id="1834a-147">First item.</span><span class="sxs-lookup"><span data-stu-id="1834a-147">First item.</span></span>

    - <span data-ttu-id="1834a-148">Item 1</span><span class="sxs-lookup"><span data-stu-id="1834a-148">Item 1</span></span>
    - <span data-ttu-id="1834a-149">Item 2</span><span class="sxs-lookup"><span data-stu-id="1834a-149">Item 2</span></span>
    - <span data-ttu-id="1834a-150">Item 3</span><span class="sxs-lookup"><span data-stu-id="1834a-150">Item 3</span></span>
2. <span data-ttu-id="1834a-151">Second item.</span><span class="sxs-lookup"><span data-stu-id="1834a-151">Second item.</span></span>
    - <span data-ttu-id="1834a-152">Nested item 1</span><span class="sxs-lookup"><span data-stu-id="1834a-152">Nested item 1</span></span>
    - <span data-ttu-id="1834a-153">Nested item 2</span><span class="sxs-lookup"><span data-stu-id="1834a-153">Nested item 2</span></span>
    - <span data-ttu-id="1834a-154">Nested item 3</span><span class="sxs-lookup"><span data-stu-id="1834a-154">Nested item 3</span></span>


## <a name="links"></a><span data-ttu-id="1834a-155">Links</span><span class="sxs-lookup"><span data-stu-id="1834a-155">Links</span></span>

<span data-ttu-id="1834a-156">HTTP and HTTPS URLs are automatically formatted as links.</span><span class="sxs-lookup"><span data-stu-id="1834a-156">HTTP and HTTPS URLs are automatically formatted as links.</span></span> 

<span data-ttu-id="1834a-157">You can set text hyperlinks for your URL using the standard markdown link syntax:</span><span class="sxs-lookup"><span data-stu-id="1834a-157">You can set text hyperlinks for your URL using the standard markdown link syntax:</span></span>

```Markdown
[Link Text](Link URL)
```

<span data-ttu-id="1834a-158">**Example:**</span><span class="sxs-lookup"><span data-stu-id="1834a-158">**Example:**</span></span>
<pre>
&#91;Microsoft Flow](https://flow.microsoft.com)
</pre>

<span data-ttu-id="1834a-159">**Result:**</span><span class="sxs-lookup"><span data-stu-id="1834a-159">**Result:**</span></span>

    [Microsoft Flow](https://flow.microsoft.com)

### <a name="anchor-links"></a><span data-ttu-id="1834a-160">Anchor links</span><span class="sxs-lookup"><span data-stu-id="1834a-160">Anchor links</span></span>

<span data-ttu-id="1834a-161">Anchor IDs are assigned to all headings when rendered as HTML.</span><span class="sxs-lookup"><span data-stu-id="1834a-161">Anchor IDs are assigned to all headings when rendered as HTML.</span></span> <span data-ttu-id="1834a-162">The ID is the heading text, with the spaces replaced by dashes (-) and all lower case.</span><span class="sxs-lookup"><span data-stu-id="1834a-162">The ID is the heading text, with the spaces replaced by dashes (-) and all lower case.</span></span>

<span data-ttu-id="1834a-163">**Example:**</span><span class="sxs-lookup"><span data-stu-id="1834a-163">**Example:**</span></span>

<pre>
###Link to a heading in the page
</pre>

<br/>

<span data-ttu-id="1834a-164">**Result:**</span><span class="sxs-lookup"><span data-stu-id="1834a-164">**Result:**</span></span>

    The syntax for an anchor link to a section...

<pre>
[Link to a heading in the page](#link-to-a-heading-in-the-page)
</pre> 
<br/>
<span data-ttu-id="1834a-165">The ID is all lower case, and the link is case sensitive, so be sure to use lower case, even though the heading itself uses upper case.</span><span class="sxs-lookup"><span data-stu-id="1834a-165">The ID is all lower case, and the link is case sensitive, so be sure to use lower case, even though the heading itself uses upper case.</span></span>


## <a name="tables"></a><span data-ttu-id="1834a-166">Tables</span><span class="sxs-lookup"><span data-stu-id="1834a-166">Tables</span></span>

<span data-ttu-id="1834a-167">Organize structured data with tables.</span><span class="sxs-lookup"><span data-stu-id="1834a-167">Organize structured data with tables.</span></span> 

- <span data-ttu-id="1834a-168">Place each table row on its own line</span><span class="sxs-lookup"><span data-stu-id="1834a-168">Place each table row on its own line</span></span> 
- <span data-ttu-id="1834a-169">Separate table cells using the pipe character `|`</span><span class="sxs-lookup"><span data-stu-id="1834a-169">Separate table cells using the pipe character `|`</span></span> 
- <span data-ttu-id="1834a-170">The first two lines of a table set the column headers and the alignment of elements in the table</span><span class="sxs-lookup"><span data-stu-id="1834a-170">The first two lines of a table set the column headers and the alignment of elements in the table</span></span>
- <span data-ttu-id="1834a-171">Use colons (`:`) when dividing the header and body of tables to specify column alignment (left, center, right)</span><span class="sxs-lookup"><span data-stu-id="1834a-171">Use colons (`:`) when dividing the header and body of tables to specify column alignment (left, center, right)</span></span> 
- <span data-ttu-id="1834a-172">To start a new line, use the HTML break tag (`<br/>`) (Works within a Wiki but not elsewhere)</span><span class="sxs-lookup"><span data-stu-id="1834a-172">To start a new line, use the HTML break tag (`<br/>`) (Works within a Wiki but not elsewhere)</span></span>  
- <span data-ttu-id="1834a-173">Make sure to end each row with a CR or LF.</span><span class="sxs-lookup"><span data-stu-id="1834a-173">Make sure to end each row with a CR or LF.</span></span> 

<span data-ttu-id="1834a-174">**Example:**</span><span class="sxs-lookup"><span data-stu-id="1834a-174">**Example:**</span></span>

```
| Heading 1 | Heading 2 | Heading 3 |  
|-----------|:-----------:|-----------:|  
| Cell A1 | Cell A2 | Cell A3 |  
| Cell B1 | Cell B2 | Cell B3<br/>second line of text |  
```




<span data-ttu-id="1834a-175">**Result:**</span><span class="sxs-lookup"><span data-stu-id="1834a-175">**Result:**</span></span>  

    | <span data-ttu-id="1834a-176">Heading 1</span><span class="sxs-lookup"><span data-stu-id="1834a-176">Heading 1</span></span> | <span data-ttu-id="1834a-177">Heading 2</span><span class="sxs-lookup"><span data-stu-id="1834a-177">Heading 2</span></span> | <span data-ttu-id="1834a-178">Heading 3</span><span class="sxs-lookup"><span data-stu-id="1834a-178">Heading 3</span></span> |  
    |-----------|:---------:|-----------:|  
    | <span data-ttu-id="1834a-179">Cell A1</span><span class="sxs-lookup"><span data-stu-id="1834a-179">Cell A1</span></span> | <span data-ttu-id="1834a-180">Cell A2</span><span class="sxs-lookup"><span data-stu-id="1834a-180">Cell A2</span></span> | <span data-ttu-id="1834a-181">Cell A3</span><span class="sxs-lookup"><span data-stu-id="1834a-181">Cell A3</span></span> |  
    | <span data-ttu-id="1834a-182">Cell B1</span><span class="sxs-lookup"><span data-stu-id="1834a-182">Cell B1</span></span> | <span data-ttu-id="1834a-183">Cell B2</span><span class="sxs-lookup"><span data-stu-id="1834a-183">Cell B2</span></span> | <span data-ttu-id="1834a-184">Cell B3</span><span class="sxs-lookup"><span data-stu-id="1834a-184">Cell B3</span></span><br/><span data-ttu-id="1834a-185">second line of text</span><span class="sxs-lookup"><span data-stu-id="1834a-185">second line of text</span></span> |  

 
## <a name="emphasis-bold-italics-strikethrough"></a><span data-ttu-id="1834a-186">Emphasis (bold, italics, strikethrough)</span><span class="sxs-lookup"><span data-stu-id="1834a-186">Emphasis (bold, italics, strikethrough)</span></span>  

<span data-ttu-id="1834a-187">You can emphasize text by applying bold, italics, or strikethrough to characters:</span><span class="sxs-lookup"><span data-stu-id="1834a-187">You can emphasize text by applying bold, italics, or strikethrough to characters:</span></span> 
- <span data-ttu-id="1834a-188">To apply italics: surround the text with an asterisk `*` or underscore `_`</span><span class="sxs-lookup"><span data-stu-id="1834a-188">To apply italics: surround the text with an asterisk `*` or underscore `_`</span></span>   
- <span data-ttu-id="1834a-189">To apply bold: surround the text with double asterisks `**`.</span><span class="sxs-lookup"><span data-stu-id="1834a-189">To apply bold: surround the text with double asterisks `**`.</span></span>    
- <span data-ttu-id="1834a-190">To apply strikethrough: surround the text with double tilde characters `~~`.</span><span class="sxs-lookup"><span data-stu-id="1834a-190">To apply strikethrough: surround the text with double tilde characters `~~`.</span></span>   

<span data-ttu-id="1834a-191">Combine these elements to apply multiple emphasis to text.</span><span class="sxs-lookup"><span data-stu-id="1834a-191">Combine these elements to apply multiple emphasis to text.</span></span>    

<span data-ttu-id="1834a-192">**Example:**</span><span class="sxs-lookup"><span data-stu-id="1834a-192">**Example:**</span></span>

<pre>
Use _emphasis_ in comments to express **strong** opinions and point out ~~corrections~~ 
**_Bold, italicized text_**  
**~~Bold, strike-through text~~**
</pre>

<br/>

<span data-ttu-id="1834a-193">**Result:**</span><span class="sxs-lookup"><span data-stu-id="1834a-193">**Result:**</span></span>

    Use _emphasis_ in comments to express **strong** opinions and point out <s>corrections</s>   
    **_Bold, italicized text_**   
    **~~Bold, strike-through text~~**  


## <a name="special-characters"></a><span data-ttu-id="1834a-194">Special characters</span><span class="sxs-lookup"><span data-stu-id="1834a-194">Special characters</span></span>

<table width="650px">
<tbody valign="top">
<tr>
<th width="300px"><span data-ttu-id="1834a-195">Syntax</span><span class="sxs-lookup"><span data-stu-id="1834a-195">Syntax</span></span></th>
<th width="350px"><span data-ttu-id="1834a-196">Example/notes</span><span class="sxs-lookup"><span data-stu-id="1834a-196">Example/notes</span></span></th>
</tr>



<tr>
<td>
<p><span data-ttu-id="1834a-197">To insert one of the following characters, prefix with a backslash:</span><span class="sxs-lookup"><span data-stu-id="1834a-197">To insert one of the following characters, prefix with a backslash:</span></span></p>

<p style="margin-bottom:2px;">```\   backslash ``` </p>
<p style="margin-bottom:2px;"><span data-ttu-id="1834a-198"><code>\`</code>   `backtick`</span><span class="sxs-lookup"><span data-stu-id="1834a-198"><code>\`</code>   `backtick`</span></span></p>
<p style="margin-bottom:2px;">```_   underscore  ```</p>
<p style="margin-bottom:2px;">```{}  curly braces  ``` </p>
<p style="margin-bottom:2px;">```[]  square brackets ```</p>
<p style="margin-bottom:2px;">```()  parentheses  ```</p>
<p style="margin-bottom:2px;">```#   hash mark  ``` </p>
<p style="margin-bottom:2px;">```+   plus sign  ```</p>
<p style="margin-bottom:2px;">```-   minus sign (hyphen) ```</p>
<p style="margin-bottom:2px;">```.   dot  ``` </p>
<p style="margin-bottom:2px;">```!   exclamation mark ```</p>


</td>
<td><span data-ttu-id="1834a-199">Some examples on inserting special characters</span><span class="sxs-lookup"><span data-stu-id="1834a-199">Some examples on inserting special characters</span></span>
<p><span data-ttu-id="1834a-200">Enter ```\\``` to get \\</span><span class="sxs-lookup"><span data-stu-id="1834a-200">Enter ```\\``` to get \\</span></span> </p>
<p><span data-ttu-id="1834a-201">Enter ```\_``` to get _</span><span class="sxs-lookup"><span data-stu-id="1834a-201">Enter ```\_``` to get _</span></span> </p>
<p><span data-ttu-id="1834a-202">Enter ```\#``` to get \#</span><span class="sxs-lookup"><span data-stu-id="1834a-202">Enter ```\#``` to get \#</span></span> </p>
<p><span data-ttu-id="1834a-203">Enter ```\(``` to get \(</span><span class="sxs-lookup"><span data-stu-id="1834a-203">Enter ```\(``` to get \(</span></span> </p>
<p><span data-ttu-id="1834a-204">Enter ```\.``` to get \.</span><span class="sxs-lookup"><span data-stu-id="1834a-204">Enter ```\.``` to get \.</span></span> </p>
<p><span data-ttu-id="1834a-205">Enter ```\!``` to get \!</span><span class="sxs-lookup"><span data-stu-id="1834a-205">Enter ```\!``` to get \!</span></span> </p>
</td>
</tr>

</tbody>
</table>
