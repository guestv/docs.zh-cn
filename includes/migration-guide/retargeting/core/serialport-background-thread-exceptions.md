### <a name="serialport-background-thread-exceptions"></a><span data-ttu-id="3754e-101">SerialPort 后台线程异常</span><span class="sxs-lookup"><span data-stu-id="3754e-101">SerialPort background thread exceptions</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3754e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="3754e-102">Details</span></span>|<span data-ttu-id="3754e-103">使用 <xref:System.IO.Ports.SerialPort> 流创建的后台线程不再在引发 OS 异常时终止进程。</span><span class="sxs-lookup"><span data-stu-id="3754e-103">Background threads created with <xref:System.IO.Ports.SerialPort> streams no longer terminate the process when OS exceptions are thrown.</span></span> <br/><span data-ttu-id="3754e-104">在面向 .NET Framework 4.7 及更早版本的应用程序中，使用 <xref:System.IO.Ports.SerialPort> 流创建的后台线程上引发操作系统异常时，会终止进程。</span><span class="sxs-lookup"><span data-stu-id="3754e-104">In applications that target the .NET Framework 4.7 and earlier versions, a process is terminated when an operating system exception is thrown on a background thread created with a <xref:System.IO.Ports.SerialPort> stream.</span></span> <br/><span data-ttu-id="3754e-105">在面向 .NET Framework 4.7.1 或更高版本的应用程序中，后台线程等待与活动串行端口相关的 OS 事件，在某些情况下（例如突然删除串行端口）也可能崩溃。</span><span class="sxs-lookup"><span data-stu-id="3754e-105">In applications that target the .NET Framework 4.7.1 or a later version, background threads wait for OS events related to the active serial port and could crash in some cases, such as sudden removal of the serial port.</span></span>|
|<span data-ttu-id="3754e-106">建议</span><span class="sxs-lookup"><span data-stu-id="3754e-106">Suggestion</span></span>|<span data-ttu-id="3754e-107">对于面向 .NET Framework 4.7.1 的应用，如果无需异常处理，可通过将以下内容添加到 <code>app.config</code> 文件的 <code>&lt;runtime&gt;</code> 部分，从而选择不用异常处理：</span><span class="sxs-lookup"><span data-stu-id="3754e-107">For apps that target the .NET Framework 4.7.1, you can opt out of the exception handling if it is not desirable by adding the following to the <code>&lt;runtime&gt;</code> section of your <code>app.config</code> file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><span data-ttu-id="3754e-108">对于面向旧版 .NET Framework，但在 .NET Framework 4.7.1 或更高版本上运行的应用，可通过将以下内容添加到 <code>app.config</code> 文件的 <code>&lt;runtime&gt;</code> 部分来选择使用异常处理：</span><span class="sxs-lookup"><span data-stu-id="3754e-108">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.1 or later, you can opt in to the exception handling by adding the following to the <code>&lt;runtime&gt;</code> section of your <code>app.config</code> file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="3754e-109">范围</span><span class="sxs-lookup"><span data-stu-id="3754e-109">Scope</span></span>|<span data-ttu-id="3754e-110">次要</span><span class="sxs-lookup"><span data-stu-id="3754e-110">Minor</span></span>|
|<span data-ttu-id="3754e-111">版本</span><span class="sxs-lookup"><span data-stu-id="3754e-111">Version</span></span>|<span data-ttu-id="3754e-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="3754e-112">4.7.1</span></span>|
|<span data-ttu-id="3754e-113">类型</span><span class="sxs-lookup"><span data-stu-id="3754e-113">Type</span></span>|<span data-ttu-id="3754e-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="3754e-114">Retargeting</span></span>|
|<span data-ttu-id="3754e-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3754e-115">Affected APIs</span></span>|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|
