---
Description: 'Panning or scrolling lets users navigate within a single view, to display the content of the view that does not fit within the viewport. Examples of views include the folder structure of a computer, a library of documents, or a photo album.'
title: Panning
ms.assetid: b419f538-c7fb-4e7c-9547-5fb2494c0b71
label: Panning
template: detail.hbs
ms.date: 02/08/2017
ms.topic: article
keywords: 'windows 10, uwp'
ms.localizationpriority: medium
---
# <a name="guidelines-for-panning"></a><span data-ttu-id="3320e-105">Guidelines for panning</span><span class="sxs-lookup"><span data-stu-id="3320e-105">Guidelines for panning</span></span>


<span data-ttu-id="3320e-106">Panning or scrolling lets users navigate within a single view, to display the content of the view that does not fit within the viewport.</span><span class="sxs-lookup"><span data-stu-id="3320e-106">Panning or scrolling lets users navigate within a single view, to display the content of the view that does not fit within the viewport.</span></span> <span data-ttu-id="3320e-107">Examples of views include the folder structure of a computer, a library of documents, or a photo album.</span><span class="sxs-lookup"><span data-stu-id="3320e-107">Examples of views include the folder structure of a computer, a library of documents, or a photo album.</span></span>

> <span data-ttu-id="3320e-108">**Important APIs**: [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994)</span><span class="sxs-lookup"><span data-stu-id="3320e-108">**Important APIs**: [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994)</span></span>


## <a name="dos-and-donts"></a><span data-ttu-id="3320e-109">Dos and don'ts</span><span class="sxs-lookup"><span data-stu-id="3320e-109">Dos and don'ts</span></span>


<span data-ttu-id="3320e-110">**Panning indicators and scroll bars**</span><span class="sxs-lookup"><span data-stu-id="3320e-110">**Panning indicators and scroll bars**</span></span>

-   <span data-ttu-id="3320e-111">Ensure panning/scrolling is possible before loading content into your app.</span><span class="sxs-lookup"><span data-stu-id="3320e-111">Ensure panning/scrolling is possible before loading content into your app.</span></span>

-   <span data-ttu-id="3320e-112">Display panning indicators and scroll bars to provide location and size cues. Hide them if you provide a custom navigation feature.</span><span class="sxs-lookup"><span data-stu-id="3320e-112">Display panning indicators and scroll bars to provide location and size cues. Hide them if you provide a custom navigation feature.</span></span>

    <span data-ttu-id="3320e-113">**Note**  Unlike standard scroll bars, panning indicators are purely informative.</span><span class="sxs-lookup"><span data-stu-id="3320e-113">**Note**  Unlike standard scroll bars, panning indicators are purely informative.</span></span> <span data-ttu-id="3320e-114">They are not exposed to input devices and cannot be manipulated in any way.</span><span class="sxs-lookup"><span data-stu-id="3320e-114">They are not exposed to input devices and cannot be manipulated in any way.</span></span>

     

<span data-ttu-id="3320e-115">**Single-axis panning (one-dimensional overflow)**</span><span class="sxs-lookup"><span data-stu-id="3320e-115">**Single-axis panning (one-dimensional overflow)**</span></span>

-   <span data-ttu-id="3320e-116">Use one-axis panning for content regions that extend beyond one viewport boundary (vertical or horizontal).</span><span class="sxs-lookup"><span data-stu-id="3320e-116">Use one-axis panning for content regions that extend beyond one viewport boundary (vertical or horizontal).</span></span>

    -   <span data-ttu-id="3320e-117">Vertical panning for a one-dimensional list of items.</span><span class="sxs-lookup"><span data-stu-id="3320e-117">Vertical panning for a one-dimensional list of items.</span></span>
    -   <span data-ttu-id="3320e-118">Horizontal panning for a grid of items.</span><span class="sxs-lookup"><span data-stu-id="3320e-118">Horizontal panning for a grid of items.</span></span>
-   <span data-ttu-id="3320e-119">Don’t use mandatory snap-points with single-axis panning if a user must be able to pan and stop between snap-points.</span><span class="sxs-lookup"><span data-stu-id="3320e-119">Don’t use mandatory snap-points with single-axis panning if a user must be able to pan and stop between snap-points.</span></span> <span data-ttu-id="3320e-120">Mandatory snap-points guarantee that the user will stop on a snap-point.</span><span class="sxs-lookup"><span data-stu-id="3320e-120">Mandatory snap-points guarantee that the user will stop on a snap-point.</span></span> <span data-ttu-id="3320e-121">Use proximity snap-points instead.</span><span class="sxs-lookup"><span data-stu-id="3320e-121">Use proximity snap-points instead.</span></span>

<span data-ttu-id="3320e-122">**Freeform panning (two-dimensional overflow)**</span><span class="sxs-lookup"><span data-stu-id="3320e-122">**Freeform panning (two-dimensional overflow)**</span></span>

-   <span data-ttu-id="3320e-123">Use two-axis panning for content regions that extend beyond both viewport boundaries (vertical and horizontal).</span><span class="sxs-lookup"><span data-stu-id="3320e-123">Use two-axis panning for content regions that extend beyond both viewport boundaries (vertical and horizontal).</span></span>

    -   <span data-ttu-id="3320e-124">Override the default rails behavior and use freeform panning for unstructured content where the user is likely to move in multiple directions.</span><span class="sxs-lookup"><span data-stu-id="3320e-124">Override the default rails behavior and use freeform panning for unstructured content where the user is likely to move in multiple directions.</span></span>
-   <span data-ttu-id="3320e-125">Freeform panning is typically suited to navigating within images or maps.</span><span class="sxs-lookup"><span data-stu-id="3320e-125">Freeform panning is typically suited to navigating within images or maps.</span></span>

<span data-ttu-id="3320e-126">**Paged view**</span><span class="sxs-lookup"><span data-stu-id="3320e-126">**Paged view**</span></span>

-   <span data-ttu-id="3320e-127">Use mandatory snap-points when the content is composed of discrete elements or you want to display an entire element.</span><span class="sxs-lookup"><span data-stu-id="3320e-127">Use mandatory snap-points when the content is composed of discrete elements or you want to display an entire element.</span></span> <span data-ttu-id="3320e-128">This can include pages of a book or magazine, a column of items, or individual images.</span><span class="sxs-lookup"><span data-stu-id="3320e-128">This can include pages of a book or magazine, a column of items, or individual images.</span></span>

    -   <span data-ttu-id="3320e-129">A snap-point should be placed at each logical boundary.</span><span class="sxs-lookup"><span data-stu-id="3320e-129">A snap-point should be placed at each logical boundary.</span></span>
    -   <span data-ttu-id="3320e-130">Each element should be sized or scaled to fit the view.</span><span class="sxs-lookup"><span data-stu-id="3320e-130">Each element should be sized or scaled to fit the view.</span></span>

<span data-ttu-id="3320e-131">**Logical and key points**</span><span class="sxs-lookup"><span data-stu-id="3320e-131">**Logical and key points**</span></span>

-   <span data-ttu-id="3320e-132">Use proximity snap-points if there are key points or logical places in the content that a user will likely stop.</span><span class="sxs-lookup"><span data-stu-id="3320e-132">Use proximity snap-points if there are key points or logical places in the content that a user will likely stop.</span></span> <span data-ttu-id="3320e-133">For example, a section header.</span><span class="sxs-lookup"><span data-stu-id="3320e-133">For example, a section header.</span></span>

-   <span data-ttu-id="3320e-134">If maximum and minimum size constraints or boundaries are defined, use visual feedback to demonstrate when the user reaches or exceeds those boundaries.</span><span class="sxs-lookup"><span data-stu-id="3320e-134">If maximum and minimum size constraints or boundaries are defined, use visual feedback to demonstrate when the user reaches or exceeds those boundaries.</span></span>

<span data-ttu-id="3320e-135">**Chaining embedded or nested content**</span><span class="sxs-lookup"><span data-stu-id="3320e-135">**Chaining embedded or nested content**</span></span>

-   <span data-ttu-id="3320e-136">Use single-axis panning (typically horizontal) and column layouts for text and grid-based content.</span><span class="sxs-lookup"><span data-stu-id="3320e-136">Use single-axis panning (typically horizontal) and column layouts for text and grid-based content.</span></span> <span data-ttu-id="3320e-137">In these cases, content typically wraps and flows naturally from column to column and keeps the user experience consistent and discoverable across UWP apps.</span><span class="sxs-lookup"><span data-stu-id="3320e-137">In these cases, content typically wraps and flows naturally from column to column and keeps the user experience consistent and discoverable across UWP apps.</span></span>

-   <span data-ttu-id="3320e-138">Don't use embedded pannable regions to display text or item lists.</span><span class="sxs-lookup"><span data-stu-id="3320e-138">Don't use embedded pannable regions to display text or item lists.</span></span> <span data-ttu-id="3320e-139">Because the panning indicators and scroll bars are displayed only when the input contact is detected within the region, it is not an intuitive or discoverable user experience.</span><span class="sxs-lookup"><span data-stu-id="3320e-139">Because the panning indicators and scroll bars are displayed only when the input contact is detected within the region, it is not an intuitive or discoverable user experience.</span></span>

-   <span data-ttu-id="3320e-140">Don't chain or place one pannable region within another pannable region if they both pan in the same direction, as shown here.</span><span class="sxs-lookup"><span data-stu-id="3320e-140">Don't chain or place one pannable region within another pannable region if they both pan in the same direction, as shown here.</span></span> <span data-ttu-id="3320e-141">This can result in the parent area being panned unintentionally when a boundary for the child area is reached.</span><span class="sxs-lookup"><span data-stu-id="3320e-141">This can result in the parent area being panned unintentionally when a boundary for the child area is reached.</span></span> <span data-ttu-id="3320e-142">Consider making the panning axis perpendicular.</span><span class="sxs-lookup"><span data-stu-id="3320e-142">Consider making the panning axis perpendicular.</span></span>

    ![image demonstrating an embedded pannable area that scrolls in the same direction as its container.](images/scrolling-embedded3.png)

## <a name="additional-usage-guidance"></a><span data-ttu-id="3320e-144">Additional usage guidance</span><span class="sxs-lookup"><span data-stu-id="3320e-144">Additional usage guidance</span></span>

<span data-ttu-id="3320e-145">Panning with touch, by using a swipe or slide gesture with one or more fingers, is like scrolling with the mouse.</span><span class="sxs-lookup"><span data-stu-id="3320e-145">Panning with touch, by using a swipe or slide gesture with one or more fingers, is like scrolling with the mouse.</span></span> <span data-ttu-id="3320e-146">The panning interaction is most similar to rotating the mouse wheel or sliding the scroll box, rather than clicking the scroll bar.</span><span class="sxs-lookup"><span data-stu-id="3320e-146">The panning interaction is most similar to rotating the mouse wheel or sliding the scroll box, rather than clicking the scroll bar.</span></span> <span data-ttu-id="3320e-147">Unless a distinction is made in an API or required by some device-specific Windows UI, we simply refer to both interactions as panning.</span><span class="sxs-lookup"><span data-stu-id="3320e-147">Unless a distinction is made in an API or required by some device-specific Windows UI, we simply refer to both interactions as panning.</span></span>

> <div id="main"><span data-ttu-id="3320e-148">
> <strong>Windows 10 Fall Creators Update - Behavior change</strong> By default, instead of text selection, an active pen now scrolls/pans in UWP apps (like touch, touchpad, and passive pen).</span><span class="sxs-lookup"><span data-stu-id="3320e-148">
> <strong>Windows 10 Fall Creators Update - Behavior change</strong> By default, instead of text selection, an active pen now scrolls/pans in UWP apps (like touch, touchpad, and passive pen).</span></span>  
> <span data-ttu-id="3320e-149">If your app depends on the previous behavior, you can override pen scrolling and revert to the previous behavior.</span><span class="sxs-lookup"><span data-stu-id="3320e-149">If your app depends on the previous behavior, you can override pen scrolling and revert to the previous behavior.</span></span> <span data-ttu-id="3320e-150">For details, see the API reference topic for the <a href="https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.scrollviewer">ScrollViewer Class</a>.</span><span class="sxs-lookup"><span data-stu-id="3320e-150">For details, see the API reference topic for the <a href="https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.scrollviewer">ScrollViewer Class</a>.</span></span>
> </div>

<span data-ttu-id="3320e-151">Depending on the input device, the user pans within a pannable region by using one of these:</span><span class="sxs-lookup"><span data-stu-id="3320e-151">Depending on the input device, the user pans within a pannable region by using one of these:</span></span>

-   <span data-ttu-id="3320e-152">A mouse, touchpad, or active pen/stylus to click the scroll arrows, drag the scroll box, or click within the scroll bar.</span><span class="sxs-lookup"><span data-stu-id="3320e-152">A mouse, touchpad, or active pen/stylus to click the scroll arrows, drag the scroll box, or click within the scroll bar.</span></span>
-   <span data-ttu-id="3320e-153">The wheel button of the mouse to emulate dragging the scroll box.</span><span class="sxs-lookup"><span data-stu-id="3320e-153">The wheel button of the mouse to emulate dragging the scroll box.</span></span>
-   <span data-ttu-id="3320e-154">The extended buttons (XBUTTON1 and XBUTTON2), if supported by the mouse.</span><span class="sxs-lookup"><span data-stu-id="3320e-154">The extended buttons (XBUTTON1 and XBUTTON2), if supported by the mouse.</span></span>
-   <span data-ttu-id="3320e-155">The keyboard arrow keys to emulate dragging the scroll box or the page keys to emulate clicking within the scroll bar.</span><span class="sxs-lookup"><span data-stu-id="3320e-155">The keyboard arrow keys to emulate dragging the scroll box or the page keys to emulate clicking within the scroll bar.</span></span>
-   <span data-ttu-id="3320e-156">Touch, touchpad, or passive pen/stylus to slide or swipe the fingers in the desired direction.</span><span class="sxs-lookup"><span data-stu-id="3320e-156">Touch, touchpad, or passive pen/stylus to slide or swipe the fingers in the desired direction.</span></span>

<span data-ttu-id="3320e-157">Sliding involves moving the fingers slowly in the panning direction.</span><span class="sxs-lookup"><span data-stu-id="3320e-157">Sliding involves moving the fingers slowly in the panning direction.</span></span> <span data-ttu-id="3320e-158">This results in a one-to-one relationship, where the content pans at the same speed and distance as the fingers.</span><span class="sxs-lookup"><span data-stu-id="3320e-158">This results in a one-to-one relationship, where the content pans at the same speed and distance as the fingers.</span></span> <span data-ttu-id="3320e-159">Swiping, which involves rapidly sliding and lifting the fingers, results in the following physics being applied to the panning animation:</span><span class="sxs-lookup"><span data-stu-id="3320e-159">Swiping, which involves rapidly sliding and lifting the fingers, results in the following physics being applied to the panning animation:</span></span>

-   <span data-ttu-id="3320e-160">Deceleration (inertia): Lifting the fingers causes panning to start decelerating.</span><span class="sxs-lookup"><span data-stu-id="3320e-160">Deceleration (inertia): Lifting the fingers causes panning to start decelerating.</span></span> <span data-ttu-id="3320e-161">This is similar to sliding to a stop on a slippery surface.</span><span class="sxs-lookup"><span data-stu-id="3320e-161">This is similar to sliding to a stop on a slippery surface.</span></span>
-   <span data-ttu-id="3320e-162">Absorption: Panning momentum during deceleration causes a slight bounce-back effect if either a snap point or a content area boundary is reached.</span><span class="sxs-lookup"><span data-stu-id="3320e-162">Absorption: Panning momentum during deceleration causes a slight bounce-back effect if either a snap point or a content area boundary is reached.</span></span>

<span data-ttu-id="3320e-163">**Types of panning**</span><span class="sxs-lookup"><span data-stu-id="3320e-163">**Types of panning**</span></span>

<span data-ttu-id="3320e-164">Windows 8 supports three types of panning:</span><span class="sxs-lookup"><span data-stu-id="3320e-164">Windows 8 supports three types of panning:</span></span>

-   <span data-ttu-id="3320e-165">Single axis - panning is supported in one direction only (horizontal or vertical).</span><span class="sxs-lookup"><span data-stu-id="3320e-165">Single axis - panning is supported in one direction only (horizontal or vertical).</span></span>
-   <span data-ttu-id="3320e-166">Rails - panning is supported in all directions.</span><span class="sxs-lookup"><span data-stu-id="3320e-166">Rails - panning is supported in all directions.</span></span> <span data-ttu-id="3320e-167">However, once the user crosses a distance threshold in a specific direction, then panning is restricted to that axis.</span><span class="sxs-lookup"><span data-stu-id="3320e-167">However, once the user crosses a distance threshold in a specific direction, then panning is restricted to that axis.</span></span>
-   <span data-ttu-id="3320e-168">Freeform - panning is supported in all directions.</span><span class="sxs-lookup"><span data-stu-id="3320e-168">Freeform - panning is supported in all directions.</span></span>

<span data-ttu-id="3320e-169">**Panning UI**</span><span class="sxs-lookup"><span data-stu-id="3320e-169">**Panning UI**</span></span>

<span data-ttu-id="3320e-170">The interaction experience for panning is unique to the input device while still providing similar functionality.</span><span class="sxs-lookup"><span data-stu-id="3320e-170">The interaction experience for panning is unique to the input device while still providing similar functionality.</span></span>

<span data-ttu-id="3320e-171">**Pannable regions** Pannable region behaviors are exposed to UWP app using JavaScript developers at design time through Cascading Style Sheets (CSS).</span><span class="sxs-lookup"><span data-stu-id="3320e-171">**Pannable regions** Pannable region behaviors are exposed to UWP app using JavaScript developers at design time through Cascading Style Sheets (CSS).</span></span>

<span data-ttu-id="3320e-172">There are two panning display modes based on the input device detected:</span><span class="sxs-lookup"><span data-stu-id="3320e-172">There are two panning display modes based on the input device detected:</span></span>

-   <span data-ttu-id="3320e-173">Panning indicators for touch.</span><span class="sxs-lookup"><span data-stu-id="3320e-173">Panning indicators for touch.</span></span>
-   <span data-ttu-id="3320e-174">Scroll bars for other input devices, including mouse, touchpad, keyboard, and stylus.</span><span class="sxs-lookup"><span data-stu-id="3320e-174">Scroll bars for other input devices, including mouse, touchpad, keyboard, and stylus.</span></span>

<span data-ttu-id="3320e-175">**Note**  Panning indicators are only visible when the touch contact is within the pannable region.</span><span class="sxs-lookup"><span data-stu-id="3320e-175">**Note**  Panning indicators are only visible when the touch contact is within the pannable region.</span></span> <span data-ttu-id="3320e-176">Similarly, the scroll bar is only visible when the mouse cursor, pen/stylus cursor, or keyboard focus is within the scrollable region.</span><span class="sxs-lookup"><span data-stu-id="3320e-176">Similarly, the scroll bar is only visible when the mouse cursor, pen/stylus cursor, or keyboard focus is within the scrollable region.</span></span>

 

<span data-ttu-id="3320e-177">**Panning indicators** Panning indicators are similar to the scroll box in a scroll bar.</span><span class="sxs-lookup"><span data-stu-id="3320e-177">**Panning indicators** Panning indicators are similar to the scroll box in a scroll bar.</span></span> <span data-ttu-id="3320e-178">They indicate the proportion of displayed content to total pannable area and the relative position of the displayed content in the pannable area.</span><span class="sxs-lookup"><span data-stu-id="3320e-178">They indicate the proportion of displayed content to total pannable area and the relative position of the displayed content in the pannable area.</span></span>

<span data-ttu-id="3320e-179">The following diagram shows two pannable areas of different lengths and their panning indicators.</span><span class="sxs-lookup"><span data-stu-id="3320e-179">The following diagram shows two pannable areas of different lengths and their panning indicators.</span></span>

![image showing two pannable areas of different lengths and their panning indicators.](images/scrolling-indicators.png)

<span data-ttu-id="3320e-181">**Panning behaviors**
**Snap points** Panning with the swipe gesture introduces inertia behavior into the interaction when the touch contact is lifted.</span><span class="sxs-lookup"><span data-stu-id="3320e-181">**Panning behaviors**
**Snap points** Panning with the swipe gesture introduces inertia behavior into the interaction when the touch contact is lifted.</span></span> <span data-ttu-id="3320e-182">With inertia, the content continues to pan until some distance threshold is reached without direct input from the user.</span><span class="sxs-lookup"><span data-stu-id="3320e-182">With inertia, the content continues to pan until some distance threshold is reached without direct input from the user.</span></span> <span data-ttu-id="3320e-183">Use snap points to modify this inertia behavior.</span><span class="sxs-lookup"><span data-stu-id="3320e-183">Use snap points to modify this inertia behavior.</span></span>

<span data-ttu-id="3320e-184">Snap points specify logical stops in your app content.</span><span class="sxs-lookup"><span data-stu-id="3320e-184">Snap points specify logical stops in your app content.</span></span> <span data-ttu-id="3320e-185">Cognitively, snap points act as a paging mechanism for the user and minimize fatigue from excessive sliding or swiping in large pannable regions.</span><span class="sxs-lookup"><span data-stu-id="3320e-185">Cognitively, snap points act as a paging mechanism for the user and minimize fatigue from excessive sliding or swiping in large pannable regions.</span></span> <span data-ttu-id="3320e-186">With them, you can handle imprecise user input and ensure a specific subset of content or key information is displayed in the viewport.</span><span class="sxs-lookup"><span data-stu-id="3320e-186">With them, you can handle imprecise user input and ensure a specific subset of content or key information is displayed in the viewport.</span></span>

<span data-ttu-id="3320e-187">There are two types of snap-points:</span><span class="sxs-lookup"><span data-stu-id="3320e-187">There are two types of snap-points:</span></span>

-   <span data-ttu-id="3320e-188">Proximity - After the contact is lifted, a snap point is selected if inertia stops within a distance threshold of the snap point.</span><span class="sxs-lookup"><span data-stu-id="3320e-188">Proximity - After the contact is lifted, a snap point is selected if inertia stops within a distance threshold of the snap point.</span></span> <span data-ttu-id="3320e-189">Panning can still stop between proximity snap points.</span><span class="sxs-lookup"><span data-stu-id="3320e-189">Panning can still stop between proximity snap points.</span></span>
-   <span data-ttu-id="3320e-190">Mandatory - The snap point selected is the one that immediately precedes or succeeds the last snap point crossed before the contact was lifted (depending on the direction and velocity of the gesture).</span><span class="sxs-lookup"><span data-stu-id="3320e-190">Mandatory - The snap point selected is the one that immediately precedes or succeeds the last snap point crossed before the contact was lifted (depending on the direction and velocity of the gesture).</span></span> <span data-ttu-id="3320e-191">Panning must stop on a mandatory snap point.</span><span class="sxs-lookup"><span data-stu-id="3320e-191">Panning must stop on a mandatory snap point.</span></span>

<span data-ttu-id="3320e-192">Panning snap-points are useful for applications such as web browsers and photo albums that emulate paginated content or have logical groupings of items that can be dynamically regrouped to fit within a viewport or display.</span><span class="sxs-lookup"><span data-stu-id="3320e-192">Panning snap-points are useful for applications such as web browsers and photo albums that emulate paginated content or have logical groupings of items that can be dynamically regrouped to fit within a viewport or display.</span></span>

<span data-ttu-id="3320e-193">The following diagrams show how panning to a certain point and releasing causes the content to automatically pan to a logical location.</span><span class="sxs-lookup"><span data-stu-id="3320e-193">The following diagrams show how panning to a certain point and releasing causes the content to automatically pan to a logical location.</span></span>

|                                                                |                                                                                         |                                                                                                                 |
|----------------------------------------------------------------|-----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| ![image showing a pannable area.](images/ux-panning-snap1.png) | ![image showing a pannable area being panned to the left.](images/ux-panning-snap2.png) | ![image showing a pannable area that has stopped panning at a logical snap-point.](images/ux-panning-snap3.png) |
| <span data-ttu-id="3320e-197">Swipe to pan.</span><span class="sxs-lookup"><span data-stu-id="3320e-197">Swipe to pan.</span></span>                                                  | <span data-ttu-id="3320e-198">Lift touch contact.</span><span class="sxs-lookup"><span data-stu-id="3320e-198">Lift touch contact.</span></span>                                                                     | <span data-ttu-id="3320e-199">Pannable region stops at the snap point, not where the touch contact was lifted.</span><span class="sxs-lookup"><span data-stu-id="3320e-199">Pannable region stops at the snap point, not where the touch contact was lifted.</span></span>                                |

 

<span data-ttu-id="3320e-200">**Rails** Content can be wider and taller than the dimensions and resolution of a display device.</span><span class="sxs-lookup"><span data-stu-id="3320e-200">**Rails** Content can be wider and taller than the dimensions and resolution of a display device.</span></span> <span data-ttu-id="3320e-201">For this reason, two-dimensional panning (horizontal and vertical) is often necessary.</span><span class="sxs-lookup"><span data-stu-id="3320e-201">For this reason, two-dimensional panning (horizontal and vertical) is often necessary.</span></span> <span data-ttu-id="3320e-202">Rails improve the user experience in these cases by emphasizing panning along the axis of motion (vertical or horizontal).</span><span class="sxs-lookup"><span data-stu-id="3320e-202">Rails improve the user experience in these cases by emphasizing panning along the axis of motion (vertical or horizontal).</span></span>

<span data-ttu-id="3320e-203">The following diagram demonstrates the concept of rails.</span><span class="sxs-lookup"><span data-stu-id="3320e-203">The following diagram demonstrates the concept of rails.</span></span>

![diagram of a screen with rails that constrain panning](images/ux-panning-rails.png)

<span data-ttu-id="3320e-205">**Chaining embedded or nested content**</span><span class="sxs-lookup"><span data-stu-id="3320e-205">**Chaining embedded or nested content**</span></span>

<span data-ttu-id="3320e-206">After a user hits a zoom or scroll limit on an element that has been nested within another zoomable or scrollable element, you can specify whether that parent element should continue the zooming or scrolling operation begun in its child element.</span><span class="sxs-lookup"><span data-stu-id="3320e-206">After a user hits a zoom or scroll limit on an element that has been nested within another zoomable or scrollable element, you can specify whether that parent element should continue the zooming or scrolling operation begun in its child element.</span></span> <span data-ttu-id="3320e-207">This is called zoom or scroll chaining.</span><span class="sxs-lookup"><span data-stu-id="3320e-207">This is called zoom or scroll chaining.</span></span>

<span data-ttu-id="3320e-208">Chaining is used for panning within a single-axis content area that contains one or more single-axis or freeform panning regions (when the touch contact is within one of these child regions).</span><span class="sxs-lookup"><span data-stu-id="3320e-208">Chaining is used for panning within a single-axis content area that contains one or more single-axis or freeform panning regions (when the touch contact is within one of these child regions).</span></span> <span data-ttu-id="3320e-209">When the panning boundary of the child region is reached in a specific direction, panning is then activated on the parent region in the same direction.</span><span class="sxs-lookup"><span data-stu-id="3320e-209">When the panning boundary of the child region is reached in a specific direction, panning is then activated on the parent region in the same direction.</span></span>

<span data-ttu-id="3320e-210">When a pannable region is nested inside another pannable region it's important to specify enough space between the container and the embedded content.</span><span class="sxs-lookup"><span data-stu-id="3320e-210">When a pannable region is nested inside another pannable region it's important to specify enough space between the container and the embedded content.</span></span> <span data-ttu-id="3320e-211">In the following diagrams, one pannable region is placed inside another pannable region, each going in perpendicular directions.</span><span class="sxs-lookup"><span data-stu-id="3320e-211">In the following diagrams, one pannable region is placed inside another pannable region, each going in perpendicular directions.</span></span> <span data-ttu-id="3320e-212">There is plenty of space for users to pan in each region.</span><span class="sxs-lookup"><span data-stu-id="3320e-212">There is plenty of space for users to pan in each region.</span></span>

![image demonstrating an embedded pannable area.](images/scrolling-embedded.png)

<span data-ttu-id="3320e-214">Without enough space, as shown in the following diagram, the embedded pannable region can interfere with panning in the container and result in unintentional panning in one or more of the pannable regions.</span><span class="sxs-lookup"><span data-stu-id="3320e-214">Without enough space, as shown in the following diagram, the embedded pannable region can interfere with panning in the container and result in unintentional panning in one or more of the pannable regions.</span></span>

![image demonstrating insufficient padding for an embedded pannable area.](images/ux-panning-embedded-wrong.png)

<span data-ttu-id="3320e-216">This guidance is also useful for apps such as photo albums or mapping apps that support unconstrained panning within an individual image or map while also supporting single-axis panning within the album (to the previous or next images) or details area.</span><span class="sxs-lookup"><span data-stu-id="3320e-216">This guidance is also useful for apps such as photo albums or mapping apps that support unconstrained panning within an individual image or map while also supporting single-axis panning within the album (to the previous or next images) or details area.</span></span> <span data-ttu-id="3320e-217">In apps that provide a detail or options area corresponding to a freeform panning image or map, we recommend that the page layout start with the details and options area as the unconstrained panning area of the image or map might interfere with panning to the details area.</span><span class="sxs-lookup"><span data-stu-id="3320e-217">In apps that provide a detail or options area corresponding to a freeform panning image or map, we recommend that the page layout start with the details and options area as the unconstrained panning area of the image or map might interfere with panning to the details area.</span></span>

## <a name="related-articles"></a><span data-ttu-id="3320e-218">Related articles</span><span class="sxs-lookup"><span data-stu-id="3320e-218">Related articles</span></span>


* [<span data-ttu-id="3320e-219">Custom user interactions</span><span class="sxs-lookup"><span data-stu-id="3320e-219">Custom user interactions</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185599)
* [<span data-ttu-id="3320e-220">Optimize ListView and GridView</span><span class="sxs-lookup"><span data-stu-id="3320e-220">Optimize ListView and GridView</span></span>](https://msdn.microsoft.com/library/windows/apps/mt204776)
* [<span data-ttu-id="3320e-221">Keyboard accessibility</span><span class="sxs-lookup"><span data-stu-id="3320e-221">Keyboard accessibility</span></span>](https://msdn.microsoft.com/library/windows/apps/mt244347)

<span data-ttu-id="3320e-222">**Samples**</span><span class="sxs-lookup"><span data-stu-id="3320e-222">**Samples**</span></span>
* [<span data-ttu-id="3320e-223">Basic input sample</span><span class="sxs-lookup"><span data-stu-id="3320e-223">Basic input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="3320e-224">Low latency input sample</span><span class="sxs-lookup"><span data-stu-id="3320e-224">Low latency input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="3320e-225">User interaction mode sample</span><span class="sxs-lookup"><span data-stu-id="3320e-225">User interaction mode sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="3320e-226">Focus visuals sample</span><span class="sxs-lookup"><span data-stu-id="3320e-226">Focus visuals sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619895)

<span data-ttu-id="3320e-227">**Archive samples**</span><span class="sxs-lookup"><span data-stu-id="3320e-227">**Archive samples**</span></span>
* [<span data-ttu-id="3320e-228">Input: XAML user input events sample</span><span class="sxs-lookup"><span data-stu-id="3320e-228">Input: XAML user input events sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="3320e-229">Input: Device capabilities sample</span><span class="sxs-lookup"><span data-stu-id="3320e-229">Input: Device capabilities sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="3320e-230">Input: Touch hit testing sample</span><span class="sxs-lookup"><span data-stu-id="3320e-230">Input: Touch hit testing sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="3320e-231">XAML scrolling, panning, and zooming sample</span><span class="sxs-lookup"><span data-stu-id="3320e-231">XAML scrolling, panning, and zooming sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="3320e-232">Input: Simplified ink sample</span><span class="sxs-lookup"><span data-stu-id="3320e-232">Input: Simplified ink sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=246570)
* [<span data-ttu-id="3320e-233">Input: Windows 8 gestures sample</span><span class="sxs-lookup"><span data-stu-id="3320e-233">Input: Windows 8 gestures sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=264995)
* [<span data-ttu-id="3320e-234">Input: Manipulations and gestures (C++) sample</span><span class="sxs-lookup"><span data-stu-id="3320e-234">Input: Manipulations and gestures (C++) sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="3320e-235">DirectX touch input sample</span><span class="sxs-lookup"><span data-stu-id="3320e-235">DirectX touch input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=231627)
 

 



