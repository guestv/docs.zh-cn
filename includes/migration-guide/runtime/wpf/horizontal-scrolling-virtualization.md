### <a name="horizontal-scrolling-and-virtualization"></a><span data-ttu-id="f6128-101">水平滚动和虚拟化</span><span class="sxs-lookup"><span data-stu-id="f6128-101">Horizontal scrolling and virtualization</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f6128-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f6128-102">Details</span></span>|<span data-ttu-id="f6128-103">此更改适用于按与主滚动方向正交的方向自行执行虚拟化的 <xref:System.Windows.Controls.ItemsControl?displayProperty=name>（主要示例是 EnableColumnVirtualization=&quot;True&quot; 的 <xref:System.Windows.Controls.DataGrid?displayProperty=name>）。</span><span class="sxs-lookup"><span data-stu-id="f6128-103">This change applies to an <xref:System.Windows.Controls.ItemsControl?displayProperty=name> that does its own virtualization in the direction orthogonal to the main scrolling direction (the chief example is <xref:System.Windows.Controls.DataGrid?displayProperty=name> with EnableColumnVirtualization=&quot;True&quot;).</span></span>  <span data-ttu-id="f6128-104">已将特定水平滚动操作更改为生成更直观且更类似于可类比垂直滚动操作的结果。</span><span class="sxs-lookup"><span data-stu-id="f6128-104">The outcome of certain horizontal scrolling operations has been changed to produce results that are more intuitive and more analogous to the results of comparable vertical operations.</span></span><p/><span data-ttu-id="f6128-105">操作包括&quot;滚动到此处&quot;和&quot;滚动到右边缘&quot;（使用右键单击水平滚动条所获得的菜单中的名称）。</span><span class="sxs-lookup"><span data-stu-id="f6128-105">The operations include &quot;Scroll Here&quot; and &quot;Right Edge&quot;, to use the names from the menu obtained by right-clicking a horizontal scrollbar.</span></span>  <span data-ttu-id="f6128-106">这两种方法都能计算候选偏移和调用 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>。</span><span class="sxs-lookup"><span data-stu-id="f6128-106">Both of these compute a candidate offset and call <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.</span></span><p/><span data-ttu-id="f6128-107">滚动到新偏移后，&quot;滚动到此处&quot;或&quot;滚动到右边缘&quot;的概念可能会发生变化，因为反虚拟化的新内容已更改 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 的值。</span><span class="sxs-lookup"><span data-stu-id="f6128-107">After scrolling to the new offset, the notion of &quot;here&quot; or &quot;right edge&quot; may have changed because newly de-virtualized content has changed the value of <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>.</span></span><p/><span data-ttu-id="f6128-108">在低于 .NET Framework 4.6.2 的版本中，滚动操作仅使用候选偏移，即使不再位于&quot;此处&quot;或&quot;右边缘&quot;，也不例外。</span><span class="sxs-lookup"><span data-stu-id="f6128-108">Prior to .NET Framework 4.6.2, the scroll operation simply uses the candidate offset, even though it may not be &quot;here&quot; or at the &quot;right edge&quot; any more.</span></span>  <span data-ttu-id="f6128-109">这会导致滚动翻阅出现“退回”等效果，最好是用举例来说明。</span><span class="sxs-lookup"><span data-stu-id="f6128-109">This results in effects like &quot;bouncing&quot; the scroll thumb, best illustrated by example.</span></span> <span data-ttu-id="f6128-110">假设 <xref:System.Windows.Controls.DataGrid?displayProperty=name> 有 ExtentWidth=1000 和 Width=200。</span><span class="sxs-lookup"><span data-stu-id="f6128-110">Suppose a <xref:System.Windows.Controls.DataGrid?displayProperty=name> has ExtentWidth=1000 and Width=200.</span></span>  <span data-ttu-id="f6128-111">“滚动到右边缘”使用候选偏移 1000 - 200 = 800。</span><span class="sxs-lookup"><span data-stu-id="f6128-111">A scroll to &quot;Right Edge&quot; uses candidate offset 1000 - 200 = 800.</span></span>  <span data-ttu-id="f6128-112">在滚动到此偏移时，新列会进行反虚拟化；假设这些列都非常宽，这样就可以将 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 更改为 2000。</span><span class="sxs-lookup"><span data-stu-id="f6128-112">While scrolling to that offset, new columns are de- virtualized; let's suppose they are very wide, so that the <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> changes to 2000.</span></span>  <span data-ttu-id="f6128-113">滚动偏移最终为 HorizontalOffset=800，而翻阅&quot;退回&quot;到滚动条中间位置附近，精确位置是 800/2000 = 40%。</span><span class="sxs-lookup"><span data-stu-id="f6128-113">The scroll ends with HorizontalOffset=800, and the thumb &quot;bounces&quot; back to near the middle of the scrollbar - precisely at 800/2000 = 40%.</span></span><p/><span data-ttu-id="f6128-114">此更改是为了在发生此情况时重新计算新的候选偏移，并进行重试。</span><span class="sxs-lookup"><span data-stu-id="f6128-114">The change is to recompute a new candidate offset when this situation occurs, and try again.</span></span> <span data-ttu-id="f6128-115">（垂直滚动已采用这样的做法。）</span><span class="sxs-lookup"><span data-stu-id="f6128-115">(This is how vertical scrolling works already.)</span></span> <p/><span data-ttu-id="f6128-116">此更改为最终用户提供了更易于预测的直观体验，但还可能会影响依赖水平滚动后的 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> 确切值的所有应用，不论水平滚动是由最终用户触发，还是由显式调用 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)> 所触发。</span><span class="sxs-lookup"><span data-stu-id="f6128-116">The change produces a more predictable and intuitive experience for the end user, but it could also affect any app that depends on the exact value of <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> after a horizontal scroll, whether invoked by the end user or by an explicit call to <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.</span></span>|
|<span data-ttu-id="f6128-117">建议</span><span class="sxs-lookup"><span data-stu-id="f6128-117">Suggestion</span></span>|<span data-ttu-id="f6128-118">应将使用 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> 预测值的应用更改为：在由于反虚拟化而可能更改 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 的任何水平滚动发生后提取实际值（和 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 值）。</span><span class="sxs-lookup"><span data-stu-id="f6128-118">An app that uses a predicted value for <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> should be changed to fetch the actual value (and the value of <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>) after any horizontal scroll that could change <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> due to de-virtualization.</span></span>|
|<span data-ttu-id="f6128-119">范围</span><span class="sxs-lookup"><span data-stu-id="f6128-119">Scope</span></span>|<span data-ttu-id="f6128-120">次要</span><span class="sxs-lookup"><span data-stu-id="f6128-120">Minor</span></span>|
|<span data-ttu-id="f6128-121">版本</span><span class="sxs-lookup"><span data-stu-id="f6128-121">Version</span></span>|<span data-ttu-id="f6128-122">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f6128-122">4.6.2</span></span>|
|<span data-ttu-id="f6128-123">类型</span><span class="sxs-lookup"><span data-stu-id="f6128-123">Type</span></span>|<span data-ttu-id="f6128-124">运行时</span><span class="sxs-lookup"><span data-stu-id="f6128-124">Runtime</span></span>|
|<span data-ttu-id="f6128-125">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f6128-125">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|
