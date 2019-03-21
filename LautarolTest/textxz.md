---
title: Using GDI 8-Bit-Per-Pixel CMY Mask Modes
description: Using GDI 8-Bit-Per-Pixel CMY Mask Modes
ms.assetid: 0631f292-c1f1-4627-b116-0b54a34ea295
keywords:
  - 'GDI WDK Windows 2000 display , halftoning'
  - 'graphics drivers WDK Windows 2000 display , halftoning'
  - 'drawing WDK GDI , halftoning'
  - halftoning WDK GDI
  - 8-bit-per-pixel CMY mask modes WDK GDI
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# <a name="using-gdi-8-bit-per-pixel-cmy-mask-modes"></a><span data-ttu-id="e6072-108">Using GDI 8-Bit-Per-Pixel CMY Mask Modes</span><span class="sxs-lookup"><span data-stu-id="e6072-108">Using GDI 8-Bit-Per-Pixel CMY Mask Modes</span></span>


## <span id="ddk_using_gdi_8_bit_per_pixel_cmy_mask_modes_gg"></span><span id="DDK_USING_GDI_8_BIT_PER_PIXEL_CMY_MASK_MODES_GG"></span>


<span data-ttu-id="e6072-109">In Microsoft Windows 2000, the [**HT\_Get8BPPMaskPalette**](https://msdn.microsoft.com/library/windows/hardware/ff567320) function returned 8-bit-per-pixel monochrome or CMY palettes.</span><span class="sxs-lookup"><span data-stu-id="e6072-109">In Microsoft Windows 2000, the [**HT\_Get8BPPMaskPalette**](https://msdn.microsoft.com/library/windows/hardware/ff567320) function returned 8-bit-per-pixel monochrome or CMY palettes.</span></span> <span data-ttu-id="e6072-110">In Windows XP and later, this function has been modified so that it also returns inverted-index CMY palettes when the *Use8BPPMaskPal* parameter is set to **TRUE**.</span><span class="sxs-lookup"><span data-stu-id="e6072-110">In Windows XP and later, this function has been modified so that it also returns inverted-index CMY palettes when the *Use8BPPMaskPal* parameter is set to **TRUE**.</span></span> <span data-ttu-id="e6072-111">The type of palette returned depends on the value stored in *pPaletteEntry*\[0\] when **HT\_Get8BPPMaskPalette** is called.</span><span class="sxs-lookup"><span data-stu-id="e6072-111">The type of palette returned depends on the value stored in *pPaletteEntry*\[0\] when **HT\_Get8BPPMaskPalette** is called.</span></span> <span data-ttu-id="e6072-112">If *pPaletteEntry*\[0\] is set to 'RGB0', an inverted-index palette is returned.</span><span class="sxs-lookup"><span data-stu-id="e6072-112">If *pPaletteEntry*\[0\] is set to 'RGB0', an inverted-index palette is returned.</span></span> <span data-ttu-id="e6072-113">If *pPaletteEntry*\[0\] is set to 0, a normal CMY palette is returned.</span><span class="sxs-lookup"><span data-stu-id="e6072-113">If *pPaletteEntry*\[0\] is set to 0, a normal CMY palette is returned.</span></span>

<span data-ttu-id="e6072-114">The reason for this change in behavior of **HT\_Get8BPPMaskPalette** is that when Windows GDI uses ROPs, which are based on the indexes in a palette and not on the palette colors, it assumes that index 0 of the palette is always black and that the last index is always white.</span><span class="sxs-lookup"><span data-stu-id="e6072-114">The reason for this change in behavior of **HT\_Get8BPPMaskPalette** is that when Windows GDI uses ROPs, which are based on the indexes in a palette and not on the palette colors, it assumes that index 0 of the palette is always black and that the last index is always white.</span></span> <span data-ttu-id="e6072-115">GDI does not check the palette entries.</span><span class="sxs-lookup"><span data-stu-id="e6072-115">GDI does not check the palette entries.</span></span> <span data-ttu-id="e6072-116">This change in **HT\_Get8BPPMaskPalette** ensures correct ROP output, instead of a result that is inverted.</span><span class="sxs-lookup"><span data-stu-id="e6072-116">This change in **HT\_Get8BPPMaskPalette** ensures correct ROP output, instead of a result that is inverted.</span></span>

<span data-ttu-id="e6072-117">To correct the GDI ROP behavior, GDI in Windows XP and later supports a special CMY palette composition format in which the CMY mask palette entries start at index 255 (white) and work down to index 0 (black), instead of starting at index 0 (white) and working up to index 255 (black).</span><span class="sxs-lookup"><span data-stu-id="e6072-117">To correct the GDI ROP behavior, GDI in Windows XP and later supports a special CMY palette composition format in which the CMY mask palette entries start at index 255 (white) and work down to index 0 (black), instead of starting at index 0 (white) and working up to index 255 (black).</span></span> <span data-ttu-id="e6072-118">The CMY inverted modes also move all CMY mask color entries to the middle of a full 256-entry palette, with the beginning and end of the palette padded with equal numbers of black and white entries.</span><span class="sxs-lookup"><span data-stu-id="e6072-118">The CMY inverted modes also move all CMY mask color entries to the middle of a full 256-entry palette, with the beginning and end of the palette padded with equal numbers of black and white entries.</span></span>

<span data-ttu-id="e6072-119">**Note**   In the discussion that follows, the term *CMY mode* refers to a mode supported in the previous implementation of [**HT\_Get8BPPMaskPalette**](https://msdn.microsoft.com/library/windows/hardware/ff567320).</span><span class="sxs-lookup"><span data-stu-id="e6072-119">**Note**   In the discussion that follows, the term *CMY mode* refers to a mode supported in the previous implementation of [**HT\_Get8BPPMaskPalette**](https://msdn.microsoft.com/library/windows/hardware/ff567320).</span></span> <span data-ttu-id="e6072-120">The term *CMY\_INVERTED mode* refers to modes supported only on Windows XP and later GDI, in which this function inverts bitmask indexes when *pPaletteEntry*\[0\] is set to 'RGB0'.</span><span class="sxs-lookup"><span data-stu-id="e6072-120">The term *CMY\_INVERTED mode* refers to modes supported only on Windows XP and later GDI, in which this function inverts bitmask indexes when *pPaletteEntry*\[0\] is set to 'RGB0'.</span></span>

 

<span data-ttu-id="e6072-121">The following steps are required for all Windows XP and later drivers that use Windows GDI halftone 8-bit-per-pixel CMY mask modes.</span><span class="sxs-lookup"><span data-stu-id="e6072-121">The following steps are required for all Windows XP and later drivers that use Windows GDI halftone 8-bit-per-pixel CMY mask modes.</span></span> <span data-ttu-id="e6072-122">If you are developing a driver for Windows 2000, you should limit the driver's use to 8-bit-per-pixel monochrome palettes.</span><span class="sxs-lookup"><span data-stu-id="e6072-122">If you are developing a driver for Windows 2000, you should limit the driver's use to 8-bit-per-pixel monochrome palettes.</span></span>

1.  <span data-ttu-id="e6072-123">Set the **flHTFlags** member of the [**GDIINFO**](https://msdn.microsoft.com/library/windows/hardware/ff566484) structure to HT\_FLAG\_INVERT\_8BPP\_BITMASK\_IDX so that GDI will render images in one of the CMY\_INVERTED modes.</span><span class="sxs-lookup"><span data-stu-id="e6072-123">Set the **flHTFlags** member of the [**GDIINFO**](https://msdn.microsoft.com/library/windows/hardware/ff566484) structure to HT\_FLAG\_INVERT\_8BPP\_BITMASK\_IDX so that GDI will render images in one of the CMY\_INVERTED modes.</span></span>

2.  <span data-ttu-id="e6072-124">Set *pPaletteEntry*\[0\] as follows prior to a call to **HT\_Get8BPPMaskPalette**:</span><span class="sxs-lookup"><span data-stu-id="e6072-124">Set *pPaletteEntry*\[0\] as follows prior to a call to **HT\_Get8BPPMaskPalette**:</span></span>

    ```cpp
    pPaletteEntry[0].peRed   = 'R';
    pPaletteEntry[0].peGreen = 'G';
    pPaletteEntry[0].peBlue  = 'B';
    pPaletteEntry[0].peFlags = '0';
    ```

    <span data-ttu-id="e6072-125">To do this, a caller should use the **HT\_SET\_BITMASKPAL2RGB** macro (defined in *winddi.h*).</span><span class="sxs-lookup"><span data-stu-id="e6072-125">To do this, a caller should use the **HT\_SET\_BITMASKPAL2RGB** macro (defined in *winddi.h*).</span></span> <span data-ttu-id="e6072-126">Here is an example showing the use of this macro:</span><span class="sxs-lookup"><span data-stu-id="e6072-126">Here is an example showing the use of this macro:</span></span>

    ```cpp
    HT_SET_BITMASKPAL2RGB(pPaletteEntry)
    ```

    <span data-ttu-id="e6072-127">Here *pPaletteEntry* is the pointer to the PALETTEENTRY that was passed in the call to the **HT\_Get8BPPMaskPalette** function.</span><span class="sxs-lookup"><span data-stu-id="e6072-127">Here *pPaletteEntry* is the pointer to the PALETTEENTRY that was passed in the call to the **HT\_Get8BPPMaskPalette** function.</span></span> <span data-ttu-id="e6072-128">When this macro completes execution, *pPaletteEntry*\[0\] will contain the string 'RGB0'.</span><span class="sxs-lookup"><span data-stu-id="e6072-128">When this macro completes execution, *pPaletteEntry*\[0\] will contain the string 'RGB0'.</span></span>

3.  <span data-ttu-id="e6072-129">Check the *pPaletteEntry* parameter returned from the call to [**HT\_Get8BPPMaskPalette**](https://msdn.microsoft.com/library/windows/hardware/ff567320) using the **HT\_IS\_BITMASKPALRGB** macro, which is defined in *winddi.h*.</span><span class="sxs-lookup"><span data-stu-id="e6072-129">Check the *pPaletteEntry* parameter returned from the call to [**HT\_Get8BPPMaskPalette**](https://msdn.microsoft.com/library/windows/hardware/ff567320) using the **HT\_IS\_BITMASKPALRGB** macro, which is defined in *winddi.h*.</span></span> <span data-ttu-id="e6072-130">Here is an example showing the use of this macro.</span><span class="sxs-lookup"><span data-stu-id="e6072-130">Here is an example showing the use of this macro.</span></span>

    ```cpp
    InvCMYSupported = HT_IS_BITMASKPALRGB(pPaletteEntry)
    ```

    <span data-ttu-id="e6072-131">In this expression, *pPaletteEntry* is the pointer to the PALETTEENTRY that was passed to the **HT\_Get8BPPMaskPalette** function.</span><span class="sxs-lookup"><span data-stu-id="e6072-131">In this expression, *pPaletteEntry* is the pointer to the PALETTEENTRY that was passed to the **HT\_Get8BPPMaskPalette** function.</span></span> <span data-ttu-id="e6072-132">If this macro returns **TRUE**, then GDI *does* support the inverted CMY 8-bit-per-pixel bitmask modes.</span><span class="sxs-lookup"><span data-stu-id="e6072-132">If this macro returns **TRUE**, then GDI *does* support the inverted CMY 8-bit-per-pixel bitmask modes.</span></span> <span data-ttu-id="e6072-133">The caller must use a translation table to convert the palette indexes to ink levels.</span><span class="sxs-lookup"><span data-stu-id="e6072-133">The caller must use a translation table to convert the palette indexes to ink levels.</span></span> <span data-ttu-id="e6072-134">See [Translating 8-Bit-Per-Pixel Halftone Indexes to Ink Levels](translating-8-bit-per-pixel-halftone-indexes-to-ink-levels.md) for an example of a function that generates this translation table.</span><span class="sxs-lookup"><span data-stu-id="e6072-134">See [Translating 8-Bit-Per-Pixel Halftone Indexes to Ink Levels](translating-8-bit-per-pixel-halftone-indexes-to-ink-levels.md) for an example of a function that generates this translation table.</span></span>

    <span data-ttu-id="e6072-135">If this macro returns **FALSE**, then the current version of GDI *does not* support the inverted CMY 8-bit-per-pixel bitmask modes.</span><span class="sxs-lookup"><span data-stu-id="e6072-135">If this macro returns **FALSE**, then the current version of GDI *does not* support the inverted CMY 8-bit-per-pixel bitmask modes.</span></span> <span data-ttu-id="e6072-136">In that case, GDI supports only the older CMY noninverted modes.</span><span class="sxs-lookup"><span data-stu-id="e6072-136">In that case, GDI supports only the older CMY noninverted modes.</span></span>

<span data-ttu-id="e6072-137">For GDI versions that support the 8-bit-per-pixel CMY\_INVERTED modes, the meaning of the *CMYMask* parameter value passed to the [**HT\_Get8BPPMaskPalette**](https://msdn.microsoft.com/library/windows/hardware/ff567320) function has been changed.</span><span class="sxs-lookup"><span data-stu-id="e6072-137">For GDI versions that support the 8-bit-per-pixel CMY\_INVERTED modes, the meaning of the *CMYMask* parameter value passed to the [**HT\_Get8BPPMaskPalette**](https://msdn.microsoft.com/library/windows/hardware/ff567320) function has been changed.</span></span> <span data-ttu-id="e6072-138">The following table summarizes the changes:</span><span class="sxs-lookup"><span data-stu-id="e6072-138">The following table summarizes the changes:</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e6072-139">CMYMask</span><span class="sxs-lookup"><span data-stu-id="e6072-139">CMYMask</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-140">Value</span><span class="sxs-lookup"><span data-stu-id="e6072-140">Value</span></span></th>
<th align="left"><span data-ttu-id="e6072-141">CMY Mode Indexes</span><span class="sxs-lookup"><span data-stu-id="e6072-141">CMY Mode Indexes</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-142">(pPaletteEntry[0] != 'RGB0')</span><span class="sxs-lookup"><span data-stu-id="e6072-142">(pPaletteEntry[0] != 'RGB0')</span></span></th>
<th align="left"><span data-ttu-id="e6072-143">CMY_INVERTED Mode Indexes</span><span class="sxs-lookup"><span data-stu-id="e6072-143">CMY_INVERTED Mode Indexes</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-144">(pPaletteEntry[0] == 'RGB0')</span><span class="sxs-lookup"><span data-stu-id="e6072-144">(pPaletteEntry[0] == 'RGB0')</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="e6072-145">0</span><span class="sxs-lookup"><span data-stu-id="e6072-145">0</span></span></p></td>
<td align="left"><p><span data-ttu-id="e6072-146">0: White</span><span class="sxs-lookup"><span data-stu-id="e6072-146">0: White</span></span></p>
<div>
 
</div>
<span data-ttu-id="e6072-147">1 to 254: Light Gray --&gt; Dark Gray</span><span class="sxs-lookup"><span data-stu-id="e6072-147">1 to 254: Light Gray --&gt; Dark Gray</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-148">255: Black</span><span class="sxs-lookup"><span data-stu-id="e6072-148">255: Black</span></span></td>
<td align="left"><p><span data-ttu-id="e6072-149">0 - Black</span><span class="sxs-lookup"><span data-stu-id="e6072-149">0 - Black</span></span></p>
<div>
 
</div>
<span data-ttu-id="e6072-150">1 to 254: Dark Gray --&gt; Light Gray</span><span class="sxs-lookup"><span data-stu-id="e6072-150">1 to 254: Dark Gray --&gt; Light Gray</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-151">255: White</span><span class="sxs-lookup"><span data-stu-id="e6072-151">255: White</span></span></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="e6072-152">1</span><span class="sxs-lookup"><span data-stu-id="e6072-152">1</span></span></p></td>
<td align="left"><p><span data-ttu-id="e6072-153">0: White</span><span class="sxs-lookup"><span data-stu-id="e6072-153">0: White</span></span></p>
<div>
 
</div>
<span data-ttu-id="e6072-154">1 to 123: 123 5x5x5 colors</span><span class="sxs-lookup"><span data-stu-id="e6072-154">1 to 123: 123 5x5x5 colors</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-155">124 to 255: Black</span><span class="sxs-lookup"><span data-stu-id="e6072-155">124 to 255: Black</span></span></td>
<td align="left"><p><span data-ttu-id="e6072-156">0 to 65: Black</span><span class="sxs-lookup"><span data-stu-id="e6072-156">0 to 65: Black</span></span></p>
<div>
 
</div>
<span data-ttu-id="e6072-157">66 to 189: 123 5x5x5 colors plus one duplicate.</span><span class="sxs-lookup"><span data-stu-id="e6072-157">66 to 189: 123 5x5x5 colors plus one duplicate.</span></span> <span data-ttu-id="e6072-158">The entry at index 127 is copied to index 128.</span><span class="sxs-lookup"><span data-stu-id="e6072-158">The entry at index 127 is copied to index 128.</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-159">190 to 255: White</span><span class="sxs-lookup"><span data-stu-id="e6072-159">190 to 255: White</span></span>
<div>
 
</div>
<div>
 
</div>
<span data-ttu-id="e6072-160">The values at indexes 127 and 128 are duplicated to ensure that the XOR ROP works correctly.</span><span class="sxs-lookup"><span data-stu-id="e6072-160">The values at indexes 127 and 128 are duplicated to ensure that the XOR ROP works correctly.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="e6072-161">2</span><span class="sxs-lookup"><span data-stu-id="e6072-161">2</span></span></p></td>
<td align="left"><p><span data-ttu-id="e6072-162">0: White</span><span class="sxs-lookup"><span data-stu-id="e6072-162">0: White</span></span></p>
<div>
 
</div>
<span data-ttu-id="e6072-163">1 to 214: 214 6x6x6 colors</span><span class="sxs-lookup"><span data-stu-id="e6072-163">1 to 214: 214 6x6x6 colors</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-164">215 to 255: Black</span><span class="sxs-lookup"><span data-stu-id="e6072-164">215 to 255: Black</span></span></td>
<td align="left"><p><span data-ttu-id="e6072-165">0 to 20: Black</span><span class="sxs-lookup"><span data-stu-id="e6072-165">0 to 20: Black</span></span></p>
<div>
 
</div>
<span data-ttu-id="e6072-166">21 to 234: 214 6x6x6 colors</span><span class="sxs-lookup"><span data-stu-id="e6072-166">21 to 234: 214 6x6x6 colors</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-167">235 to 255: White</span><span class="sxs-lookup"><span data-stu-id="e6072-167">235 to 255: White</span></span></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="e6072-168">3 to 255</span><span class="sxs-lookup"><span data-stu-id="e6072-168">3 to 255</span></span></p></td>
<td align="left"><p><span data-ttu-id="e6072-169">0: White</span><span class="sxs-lookup"><span data-stu-id="e6072-169">0: White</span></span></p>
<div>
 
</div>
<span data-ttu-id="e6072-170">1 to 254: CxMxY color bitmask</span><span class="sxs-lookup"><span data-stu-id="e6072-170">1 to 254: CxMxY color bitmask</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-171">255: Black</span><span class="sxs-lookup"><span data-stu-id="e6072-171">255: Black</span></span>
<div>
 
</div>
<div>
 
</div>
<span data-ttu-id="e6072-172">In the product above, C, M, and Y represent the number of levels of cyan, magenta, and yellow, respectively.</span><span class="sxs-lookup"><span data-stu-id="e6072-172">In the product above, C, M, and Y represent the number of levels of cyan, magenta, and yellow, respectively.</span></span>
<div>
 
</div>
<div>
 
</div><span data-ttu-id="e6072-173">
<strong>Note</strong>: For these modes, a valid combination must not have any of the cyan, magenta, or yellow ink levels equal to zero.</span><span class="sxs-lookup"><span data-stu-id="e6072-173">
<strong>Note</strong>: For these modes, a valid combination must not have any of the cyan, magenta, or yellow ink levels equal to zero.</span></span> <span data-ttu-id="e6072-174">For such a combination, <a href="https://msdn.microsoft.com/library/windows/hardware/ff567320" data-raw-source="[&lt;strong&gt;HT_Get8BPPMaskPalette&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567320)"><strong>HT_Get8BPPMaskPalette</strong></a> indicates an error condition by returning a zero-count palette in its <em>pPaletteEntry</em> parameter.</span><span class="sxs-lookup"><span data-stu-id="e6072-174">For such a combination, <a href="https://msdn.microsoft.com/library/windows/hardware/ff567320" data-raw-source="[&lt;strong&gt;HT_Get8BPPMaskPalette&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567320)"><strong>HT_Get8BPPMaskPalette</strong></a> indicates an error condition by returning a zero-count palette in its <em>pPaletteEntry</em> parameter.</span></span></td>
<td align="left"><p><span data-ttu-id="e6072-175">0: Black</span><span class="sxs-lookup"><span data-stu-id="e6072-175">0: Black</span></span></p>
<div>
 
</div>
<span data-ttu-id="e6072-176">1 to 254: Centered CxMxY colors padded with black at the beginning and white at the end</span><span class="sxs-lookup"><span data-stu-id="e6072-176">1 to 254: Centered CxMxY colors padded with black at the beginning and white at the end</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-177">If CxMxY is an odd number, then the entry at index 128 is a duplicate of the one at index 127.</span><span class="sxs-lookup"><span data-stu-id="e6072-177">If CxMxY is an odd number, then the entry at index 128 is a duplicate of the one at index 127.</span></span>
<div>
 
</div>
<span data-ttu-id="e6072-178">255: White</span><span class="sxs-lookup"><span data-stu-id="e6072-178">255: White</span></span>
<div>
 
</div>
<div>
 
</div>
<span data-ttu-id="e6072-179">In the product above, C, M, and Y represent the number of levels of cyan, magenta, and yellow, respectively.</span><span class="sxs-lookup"><span data-stu-id="e6072-179">In the product above, C, M, and Y represent the number of levels of cyan, magenta, and yellow, respectively.</span></span>
<div>
 
</div>
<div>
 
</div><span data-ttu-id="e6072-180">
<strong>Note:</strong> The (C x M x Y) indexes are centered in the 256-entry palette.</span><span class="sxs-lookup"><span data-stu-id="e6072-180">
<strong>Note:</strong> The (C x M x Y) indexes are centered in the 256-entry palette.</span></span> <span data-ttu-id="e6072-181">That is, there are equal numbers of black entries padding the low end of the palette and white entries padding the high end.</span><span class="sxs-lookup"><span data-stu-id="e6072-181">That is, there are equal numbers of black entries padding the low end of the palette and white entries padding the high end.</span></span>
<div>
 
</div>
<div>
 
</div><span data-ttu-id="e6072-182">
<strong>Note</strong>: For these modes, a valid combination must not have any of the cyan, magenta, or yellow ink levels equal to zero.</span><span class="sxs-lookup"><span data-stu-id="e6072-182">
<strong>Note</strong>: For these modes, a valid combination must not have any of the cyan, magenta, or yellow ink levels equal to zero.</span></span> <span data-ttu-id="e6072-183">For such a combination, <a href="https://msdn.microsoft.com/library/windows/hardware/ff567320" data-raw-source="[&lt;strong&gt;HT_Get8BPPMaskPalette&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567320)"><strong>HT_Get8BPPMaskPalette</strong></a> indicates an error condition by returning a zero-count palette in its <em>pPaletteEntry</em> parameter.</span><span class="sxs-lookup"><span data-stu-id="e6072-183">For such a combination, <a href="https://msdn.microsoft.com/library/windows/hardware/ff567320" data-raw-source="[&lt;strong&gt;HT_Get8BPPMaskPalette&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff567320)"><strong>HT_Get8BPPMaskPalette</strong></a> indicates an error condition by returning a zero-count palette in its <em>pPaletteEntry</em> parameter.</span></span></td>
</tr>
</tbody>
</table>

 

-   <span data-ttu-id="e6072-184">For a value of *CMYMask* of 0 (Gray scale), the caller can process either the CMY mode or the CMY\_INVERTED mode.</span><span class="sxs-lookup"><span data-stu-id="e6072-184">For a value of *CMYMask* of 0 (Gray scale), the caller can process either the CMY mode or the CMY\_INVERTED mode.</span></span> <span data-ttu-id="e6072-185">Note, however, that GDI ROPs are correctly processed only in the CMY\_INVERTED mode.</span><span class="sxs-lookup"><span data-stu-id="e6072-185">Note, however, that GDI ROPs are correctly processed only in the CMY\_INVERTED mode.</span></span>

    <span data-ttu-id="e6072-186">CMY Mode: Indexes 0 to 255 represent a gray scale from white to black.</span><span class="sxs-lookup"><span data-stu-id="e6072-186">CMY Mode: Indexes 0 to 255 represent a gray scale from white to black.</span></span>

    <span data-ttu-id="e6072-187">CMY\_INVERTED Mode: Indexes 0 to 255 represent a gray scale ranging from black to white.</span><span class="sxs-lookup"><span data-stu-id="e6072-187">CMY\_INVERTED Mode: Indexes 0 to 255 represent a gray scale ranging from black to white.</span></span>

-   <span data-ttu-id="e6072-188">For any valid value of *CMYMask* from 1 to 255, the caller should use the example function shown in [Translating 8-Bit-Per-Pixel Halftone Indexes to Ink Levels](translating-8-bit-per-pixel-halftone-indexes-to-ink-levels.md) to translate indexes to ink levels.</span><span class="sxs-lookup"><span data-stu-id="e6072-188">For any valid value of *CMYMask* from 1 to 255, the caller should use the example function shown in [Translating 8-Bit-Per-Pixel Halftone Indexes to Ink Levels](translating-8-bit-per-pixel-halftone-indexes-to-ink-levels.md) to translate indexes to ink levels.</span></span>

-   <span data-ttu-id="e6072-189">For any valid value of *CMYMask* from 1 to 255, the CMY\_INVERTED modes pad the palettes with black entries at the beginning of the array, and an equal number of white entries at the end of the array.</span><span class="sxs-lookup"><span data-stu-id="e6072-189">For any valid value of *CMYMask* from 1 to 255, the CMY\_INVERTED modes pad the palettes with black entries at the beginning of the array, and an equal number of white entries at the end of the array.</span></span> <span data-ttu-id="e6072-190">The middle of the array is filled with the other colors.</span><span class="sxs-lookup"><span data-stu-id="e6072-190">The middle of the array is filled with the other colors.</span></span> <span data-ttu-id="e6072-191">This ensures that all 256 of the color palette entries are symmetrically distributed so that GDI ROPs, which are index-based, not color-based, work correctly.</span><span class="sxs-lookup"><span data-stu-id="e6072-191">This ensures that all 256 of the color palette entries are symmetrically distributed so that GDI ROPs, which are index-based, not color-based, work correctly.</span></span> <span data-ttu-id="e6072-192">The colors are symmetrically distributed when the color at index *N* is the inverse of the color at index (256 - *N*).</span><span class="sxs-lookup"><span data-stu-id="e6072-192">The colors are symmetrically distributed when the color at index *N* is the inverse of the color at index (256 - *N*).</span></span> <span data-ttu-id="e6072-193">When a color and its inverse are printed together, the result is black.</span><span class="sxs-lookup"><span data-stu-id="e6072-193">When a color and its inverse are printed together, the result is black.</span></span> <span data-ttu-id="e6072-194">In other words, for a given color and its inverse, the two cyan ink levels add to the maximum cyan ink level, as do the two magenta ink levels, and the two yellow ink levels.</span><span class="sxs-lookup"><span data-stu-id="e6072-194">In other words, for a given color and its inverse, the two cyan ink levels add to the maximum cyan ink level, as do the two magenta ink levels, and the two yellow ink levels.</span></span> <span data-ttu-id="e6072-195">The resulting ink levels correspond to black.</span><span class="sxs-lookup"><span data-stu-id="e6072-195">The resulting ink levels correspond to black.</span></span>

    <span data-ttu-id="e6072-196">For example; a CMY palette with three levels each of cyan, magenta, and yellow has a total of 27 (3 x 3 x 3) indexes for colors, including black and white.</span><span class="sxs-lookup"><span data-stu-id="e6072-196">For example; a CMY palette with three levels each of cyan, magenta, and yellow has a total of 27 (3 x 3 x 3) indexes for colors, including black and white.</span></span> <span data-ttu-id="e6072-197">Because 27 is an odd number, and because GDI requires that a CMY\_INVERTED mode palette be padded with equal numbers of black and white entries, GDI duplicates the entry at the middle index (index 13 of the 27 colors).</span><span class="sxs-lookup"><span data-stu-id="e6072-197">Because 27 is an odd number, and because GDI requires that a CMY\_INVERTED mode palette be padded with equal numbers of black and white entries, GDI duplicates the entry at the middle index (index 13 of the 27 colors).</span></span> <span data-ttu-id="e6072-198">With the entries at indexes 13 and 14 now the same, palette will now have 28 colors.</span><span class="sxs-lookup"><span data-stu-id="e6072-198">With the entries at indexes 13 and 14 now the same, palette will now have 28 colors.</span></span> <span data-ttu-id="e6072-199">To fill the palette, GDI places 114 black entries at the beginning of the palette (indexes 0 to 113), places the 28 colors at indexes 114 (black) through 141 (white), and fills the remaining 114 entries with white (indexes 142 through 255).</span><span class="sxs-lookup"><span data-stu-id="e6072-199">To fill the palette, GDI places 114 black entries at the beginning of the palette (indexes 0 to 113), places the 28 colors at indexes 114 (black) through 141 (white), and fills the remaining 114 entries with white (indexes 142 through 255).</span></span> <span data-ttu-id="e6072-200">This makes a total of 256 entries (114 + 28 + 114 = 256 entries).</span><span class="sxs-lookup"><span data-stu-id="e6072-200">This makes a total of 256 entries (114 + 28 + 114 = 256 entries).</span></span> <span data-ttu-id="e6072-201">This layout of the indexes ensures that all ROPs will be correctly rendered.</span><span class="sxs-lookup"><span data-stu-id="e6072-201">This layout of the indexes ensures that all ROPs will be correctly rendered.</span></span> <span data-ttu-id="e6072-202">The example function in [Translating 8-Bit-Per-Pixel Halftone Indexes to Ink Levels](translating-8-bit-per-pixel-halftone-indexes-to-ink-levels.md) shows how to generate the ink levels as well as a Windows 2000 CMY332 index translation table.</span><span class="sxs-lookup"><span data-stu-id="e6072-202">The example function in [Translating 8-Bit-Per-Pixel Halftone Indexes to Ink Levels](translating-8-bit-per-pixel-halftone-indexes-to-ink-levels.md) shows how to generate the ink levels as well as a Windows 2000 CMY332 index translation table.</span></span>

    <span data-ttu-id="e6072-203">The following table lists the cyan, magenta, and yellow levels for the 3 x 3 x 3 palette discussed in the previous paragraph.</span><span class="sxs-lookup"><span data-stu-id="e6072-203">The following table lists the cyan, magenta, and yellow levels for the 3 x 3 x 3 palette discussed in the previous paragraph.</span></span> <span data-ttu-id="e6072-204">The 28 colors (27 original palette colors plus one duplicate) are embedded in the middle of the 256-color palette, with equal amounts of black padding at the beginning and white padding at the end.</span><span class="sxs-lookup"><span data-stu-id="e6072-204">The 28 colors (27 original palette colors plus one duplicate) are embedded in the middle of the 256-color palette, with equal amounts of black padding at the beginning and white padding at the end.</span></span> <span data-ttu-id="e6072-205">The palette is symmetric, meaning that if the ink levels at index *N* are added to those at index (256 - *N*), the result will be black (cyan, magenta, and yellow levels = 2).</span><span class="sxs-lookup"><span data-stu-id="e6072-205">The palette is symmetric, meaning that if the ink levels at index *N* are added to those at index (256 - *N*), the result will be black (cyan, magenta, and yellow levels = 2).</span></span>

    <table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left"><span data-ttu-id="e6072-206">Palette Index(3x3x3 Index)</span><span class="sxs-lookup"><span data-stu-id="e6072-206">Palette Index(3x3x3 Index)</span></span></th>
    <th align="left"><span data-ttu-id="e6072-207">Cyan Level0 to 2</span><span class="sxs-lookup"><span data-stu-id="e6072-207">Cyan Level0 to 2</span></span></th>
    <th align="left"><span data-ttu-id="e6072-208">Magenta Level0 to 2</span><span class="sxs-lookup"><span data-stu-id="e6072-208">Magenta Level0 to 2</span></span></th>
    <th align="left"><span data-ttu-id="e6072-209">Yellow Level0 to 2</span><span class="sxs-lookup"><span data-stu-id="e6072-209">Yellow Level0 to 2</span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-210">0 to 113</span><span class="sxs-lookup"><span data-stu-id="e6072-210">0 to 113</span></span></p>
    <p><span data-ttu-id="e6072-211">Black</</span><span class="sxs-lookup"><span data-stu-id="e6072-211">Black</</span></span></td>
    <td align="left"><p><span data-ttu-id="e6072-212">2</span><span class="sxs-lookup"><span data-stu-id="e6072-212">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-213">2</span><span class="sxs-lookup"><span data-stu-id="e6072-213">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-214">2</span><span class="sxs-lookup"><span data-stu-id="e6072-214">2</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-215">114 (0)</span><span class="sxs-lookup"><span data-stu-id="e6072-215">114 (0)</span></span></p>
    <p><span data-ttu-id="e6072-216">Black</span><span class="sxs-lookup"><span data-stu-id="e6072-216">Black</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-217">2</span><span class="sxs-lookup"><span data-stu-id="e6072-217">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-218">2</span><span class="sxs-lookup"><span data-stu-id="e6072-218">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-219">2</span><span class="sxs-lookup"><span data-stu-id="e6072-219">2</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-220">115 (1)</span><span class="sxs-lookup"><span data-stu-id="e6072-220">115 (1)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-221">2</span><span class="sxs-lookup"><span data-stu-id="e6072-221">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-222">2</span><span class="sxs-lookup"><span data-stu-id="e6072-222">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-223">1</span><span class="sxs-lookup"><span data-stu-id="e6072-223">1</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-224">116 (2)</span><span class="sxs-lookup"><span data-stu-id="e6072-224">116 (2)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-225">2</span><span class="sxs-lookup"><span data-stu-id="e6072-225">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-226">2</span><span class="sxs-lookup"><span data-stu-id="e6072-226">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-227">0</span><span class="sxs-lookup"><span data-stu-id="e6072-227">0</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-228">117 (3)</span><span class="sxs-lookup"><span data-stu-id="e6072-228">117 (3)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-229">2</span><span class="sxs-lookup"><span data-stu-id="e6072-229">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-230">1</span><span class="sxs-lookup"><span data-stu-id="e6072-230">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-231">2</span><span class="sxs-lookup"><span data-stu-id="e6072-231">2</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-232">118 (4)</span><span class="sxs-lookup"><span data-stu-id="e6072-232">118 (4)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-233">2</span><span class="sxs-lookup"><span data-stu-id="e6072-233">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-234">1</span><span class="sxs-lookup"><span data-stu-id="e6072-234">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-235">1</span><span class="sxs-lookup"><span data-stu-id="e6072-235">1</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-236">119 (5)</span><span class="sxs-lookup"><span data-stu-id="e6072-236">119 (5)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-237">2</span><span class="sxs-lookup"><span data-stu-id="e6072-237">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-238">1</span><span class="sxs-lookup"><span data-stu-id="e6072-238">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-239">0</span><span class="sxs-lookup"><span data-stu-id="e6072-239">0</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-240">120 (6)</span><span class="sxs-lookup"><span data-stu-id="e6072-240">120 (6)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-241">2</span><span class="sxs-lookup"><span data-stu-id="e6072-241">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-242">0</span><span class="sxs-lookup"><span data-stu-id="e6072-242">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-243">2</span><span class="sxs-lookup"><span data-stu-id="e6072-243">2</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-244">121 (7)</span><span class="sxs-lookup"><span data-stu-id="e6072-244">121 (7)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-245">2</span><span class="sxs-lookup"><span data-stu-id="e6072-245">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-246">0</span><span class="sxs-lookup"><span data-stu-id="e6072-246">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-247">1</span><span class="sxs-lookup"><span data-stu-id="e6072-247">1</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-248">122 (8)</span><span class="sxs-lookup"><span data-stu-id="e6072-248">122 (8)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-249">2</span><span class="sxs-lookup"><span data-stu-id="e6072-249">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-250">0</span><span class="sxs-lookup"><span data-stu-id="e6072-250">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-251">0</span><span class="sxs-lookup"><span data-stu-id="e6072-251">0</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-252">123 (9)</span><span class="sxs-lookup"><span data-stu-id="e6072-252">123 (9)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-253">1</span><span class="sxs-lookup"><span data-stu-id="e6072-253">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-254">2</span><span class="sxs-lookup"><span data-stu-id="e6072-254">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-255">2</span><span class="sxs-lookup"><span data-stu-id="e6072-255">2</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-256">124 (10)</span><span class="sxs-lookup"><span data-stu-id="e6072-256">124 (10)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-257">1</span><span class="sxs-lookup"><span data-stu-id="e6072-257">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-258">2</span><span class="sxs-lookup"><span data-stu-id="e6072-258">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-259">1</span><span class="sxs-lookup"><span data-stu-id="e6072-259">1</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-260">125 (11)</span><span class="sxs-lookup"><span data-stu-id="e6072-260">125 (11)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-261">1</span><span class="sxs-lookup"><span data-stu-id="e6072-261">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-262">2</span><span class="sxs-lookup"><span data-stu-id="e6072-262">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-263">0</span><span class="sxs-lookup"><span data-stu-id="e6072-263">0</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-264">126 (12)</span><span class="sxs-lookup"><span data-stu-id="e6072-264">126 (12)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-265">1</span><span class="sxs-lookup"><span data-stu-id="e6072-265">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-266">1</span><span class="sxs-lookup"><span data-stu-id="e6072-266">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-267">2</span><span class="sxs-lookup"><span data-stu-id="e6072-267">2</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-268">127 (13)</span><span class="sxs-lookup"><span data-stu-id="e6072-268">127 (13)</span></span></p>
    <p><span data-ttu-id="e6072-269">Copied to index 128</span><span class="sxs-lookup"><span data-stu-id="e6072-269">Copied to index 128</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-270">1</span><span class="sxs-lookup"><span data-stu-id="e6072-270">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-271">1</span><span class="sxs-lookup"><span data-stu-id="e6072-271">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-272">1</span><span class="sxs-lookup"><span data-stu-id="e6072-272">1</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-273">128 (14)</span><span class="sxs-lookup"><span data-stu-id="e6072-273">128 (14)</span></span></p>
    <p><span data-ttu-id="e6072-274">Duplicate of entry at index 127</span><span class="sxs-lookup"><span data-stu-id="e6072-274">Duplicate of entry at index 127</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-275">1</span><span class="sxs-lookup"><span data-stu-id="e6072-275">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-276">1</span><span class="sxs-lookup"><span data-stu-id="e6072-276">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-277">1</span><span class="sxs-lookup"><span data-stu-id="e6072-277">1</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-278">129 (15)</span><span class="sxs-lookup"><span data-stu-id="e6072-278">129 (15)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-279">1</span><span class="sxs-lookup"><span data-stu-id="e6072-279">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-280">1</span><span class="sxs-lookup"><span data-stu-id="e6072-280">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-281">0</span><span class="sxs-lookup"><span data-stu-id="e6072-281">0</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-282">130 (16)</span><span class="sxs-lookup"><span data-stu-id="e6072-282">130 (16)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-283">1</span><span class="sxs-lookup"><span data-stu-id="e6072-283">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-284">0</span><span class="sxs-lookup"><span data-stu-id="e6072-284">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-285">2</span><span class="sxs-lookup"><span data-stu-id="e6072-285">2</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-286">131 (17)</span><span class="sxs-lookup"><span data-stu-id="e6072-286">131 (17)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-287">1</span><span class="sxs-lookup"><span data-stu-id="e6072-287">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-288">0</span><span class="sxs-lookup"><span data-stu-id="e6072-288">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-289">1</span><span class="sxs-lookup"><span data-stu-id="e6072-289">1</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-290">132 (18)</span><span class="sxs-lookup"><span data-stu-id="e6072-290">132 (18)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-291">1</span><span class="sxs-lookup"><span data-stu-id="e6072-291">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-292">0</span><span class="sxs-lookup"><span data-stu-id="e6072-292">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-293">0</span><span class="sxs-lookup"><span data-stu-id="e6072-293">0</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-294">133 (19)</span><span class="sxs-lookup"><span data-stu-id="e6072-294">133 (19)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-295">0</span><span class="sxs-lookup"><span data-stu-id="e6072-295">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-296">2</span><span class="sxs-lookup"><span data-stu-id="e6072-296">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-297">2</span><span class="sxs-lookup"><span data-stu-id="e6072-297">2</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-298">134 (20)</span><span class="sxs-lookup"><span data-stu-id="e6072-298">134 (20)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-299">0</span><span class="sxs-lookup"><span data-stu-id="e6072-299">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-300">2</span><span class="sxs-lookup"><span data-stu-id="e6072-300">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-301">1</span><span class="sxs-lookup"><span data-stu-id="e6072-301">1</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-302">135 (21)</span><span class="sxs-lookup"><span data-stu-id="e6072-302">135 (21)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-303">0</span><span class="sxs-lookup"><span data-stu-id="e6072-303">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-304">2</span><span class="sxs-lookup"><span data-stu-id="e6072-304">2</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-305">0</span><span class="sxs-lookup"><span data-stu-id="e6072-305">0</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-306">136 (22)</span><span class="sxs-lookup"><span data-stu-id="e6072-306">136 (22)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-307">0</span><span class="sxs-lookup"><span data-stu-id="e6072-307">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-308">1</span><span class="sxs-lookup"><span data-stu-id="e6072-308">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-309">2</span><span class="sxs-lookup"><span data-stu-id="e6072-309">2</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-310">137 (23)</span><span class="sxs-lookup"><span data-stu-id="e6072-310">137 (23)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-311">0</span><span class="sxs-lookup"><span data-stu-id="e6072-311">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-312">1</span><span class="sxs-lookup"><span data-stu-id="e6072-312">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-313">1</span><span class="sxs-lookup"><span data-stu-id="e6072-313">1</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-314">138 (24)</span><span class="sxs-lookup"><span data-stu-id="e6072-314">138 (24)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-315">0</span><span class="sxs-lookup"><span data-stu-id="e6072-315">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-316">1</span><span class="sxs-lookup"><span data-stu-id="e6072-316">1</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-317">0</span><span class="sxs-lookup"><span data-stu-id="e6072-317">0</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-318">139 (25)</span><span class="sxs-lookup"><span data-stu-id="e6072-318">139 (25)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-319">0</span><span class="sxs-lookup"><span data-stu-id="e6072-319">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-320">0</span><span class="sxs-lookup"><span data-stu-id="e6072-320">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-321">2</span><span class="sxs-lookup"><span data-stu-id="e6072-321">2</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-322">140 (26)</span><span class="sxs-lookup"><span data-stu-id="e6072-322">140 (26)</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-323">0</span><span class="sxs-lookup"><span data-stu-id="e6072-323">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-324">0</span><span class="sxs-lookup"><span data-stu-id="e6072-324">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-325">1</span><span class="sxs-lookup"><span data-stu-id="e6072-325">1</span></span></p></td>
    </tr>
    <tr class="odd">
    <td align="left"><p><span data-ttu-id="e6072-326">141 (27)</span><span class="sxs-lookup"><span data-stu-id="e6072-326">141 (27)</span></span></p>
    <p><span data-ttu-id="e6072-327">White</span><span class="sxs-lookup"><span data-stu-id="e6072-327">White</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-328">0</span><span class="sxs-lookup"><span data-stu-id="e6072-328">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-329">0</span><span class="sxs-lookup"><span data-stu-id="e6072-329">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-330">0</span><span class="sxs-lookup"><span data-stu-id="e6072-330">0</span></span></p></td>
    </tr>
    <tr class="even">
    <td align="left"><p><span data-ttu-id="e6072-331">142 to 255</span><span class="sxs-lookup"><span data-stu-id="e6072-331">142 to 255</span></span></p>
    <p><span data-ttu-id="e6072-332">White</span><span class="sxs-lookup"><span data-stu-id="e6072-332">White</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-333">0</span><span class="sxs-lookup"><span data-stu-id="e6072-333">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-334">0</span><span class="sxs-lookup"><span data-stu-id="e6072-334">0</span></span></p></td>
    <td align="left"><p><span data-ttu-id="e6072-335">0</span><span class="sxs-lookup"><span data-stu-id="e6072-335">0</span></span></p></td>
    </tr>
    </tbody>
    </table>

     

<!-- -->

-   <span data-ttu-id="e6072-336">If the requested palette is a CMY mode palette (not a CMY\_INVERTED mode palette), then for values of *CMYMask* from 3 to 255, the rendered 8-bit-per-pixel byte index bits have the following meaning.</span><span class="sxs-lookup"><span data-stu-id="e6072-336">If the requested palette is a CMY mode palette (not a CMY\_INVERTED mode palette), then for values of *CMYMask* from 3 to 255, the rendered 8-bit-per-pixel byte index bits have the following meaning.</span></span> <span data-ttu-id="e6072-337">In this case, the bit patterns represent ink levels that can be used directly without translation.</span><span class="sxs-lookup"><span data-stu-id="e6072-337">In this case, the bit patterns represent ink levels that can be used directly without translation.</span></span> <span data-ttu-id="e6072-338">This also applies when a CMY\_INVERTED mode byte index is mapped to CMY mode using a translation table's **CMY332Idx** member.</span><span class="sxs-lookup"><span data-stu-id="e6072-338">This also applies when a CMY\_INVERTED mode byte index is mapped to CMY mode using a translation table's **CMY332Idx** member.</span></span> <span data-ttu-id="e6072-339">See [Translating 8-Bit-Per-Pixel Halftone Indexes to Ink Levels](translating-8-bit-per-pixel-halftone-indexes-to-ink-levels.md) for more information.</span><span class="sxs-lookup"><span data-stu-id="e6072-339">See [Translating 8-Bit-Per-Pixel Halftone Indexes to Ink Levels](translating-8-bit-per-pixel-halftone-indexes-to-ink-levels.md) for more information.</span></span>

```cpp
  Bit     7 6 5 4 3 2 1 0
          |   | |   | | |
          +---+ +---+ +-+
            |     |    |
            |     |    +-- Yellow 0-3 (Max. 4 levels)
            |     |
            |     +-- Magenta 0-7 (Max. 8 levels)
            |
            +-- Cyan 0-7 (Max. 8 levels)
```

 

 




