---
title: CWinThread 类
ms.date: 11/04/2016
f1_keywords:
- CWinThread
- AFXWIN/CWinThread
- AFXWIN/CWinThread::CWinThread
- AFXWIN/CWinThread::CreateThread
- AFXWIN/CWinThread::ExitInstance
- AFXWIN/CWinThread::GetMainWnd
- AFXWIN/CWinThread::GetThreadPriority
- AFXWIN/CWinThread::InitInstance
- AFXWIN/CWinThread::IsIdleMessage
- AFXWIN/CWinThread::OnIdle
- AFXWIN/CWinThread::PostThreadMessage
- AFXWIN/CWinThread::PreTranslateMessage
- AFXWIN/CWinThread::ProcessMessageFilter
- AFXWIN/CWinThread::ProcessWndProcException
- AFXWIN/CWinThread::PumpMessage
- AFXWIN/CWinThread::ResumeThread
- AFXWIN/CWinThread::Run
- AFXWIN/CWinThread::SetThreadPriority
- AFXWIN/CWinThread::SuspendThread
- AFXWIN/CWinThread::m_bAutoDelete
- AFXWIN/CWinThread::m_hThread
- AFXWIN/CWinThread::m_nThreadID
- AFXWIN/CWinThread::m_pActiveWnd
- AFXWIN/CWinThread::m_pMainWnd
helpviewer_keywords:
- CWinThread [MFC], CWinThread
- CWinThread [MFC], CreateThread
- CWinThread [MFC], ExitInstance
- CWinThread [MFC], GetMainWnd
- CWinThread [MFC], GetThreadPriority
- CWinThread [MFC], InitInstance
- CWinThread [MFC], IsIdleMessage
- CWinThread [MFC], OnIdle
- CWinThread [MFC], PostThreadMessage
- CWinThread [MFC], PreTranslateMessage
- CWinThread [MFC], ProcessMessageFilter
- CWinThread [MFC], ProcessWndProcException
- CWinThread [MFC], PumpMessage
- CWinThread [MFC], ResumeThread
- CWinThread [MFC], Run
- CWinThread [MFC], SetThreadPriority
- CWinThread [MFC], SuspendThread
- CWinThread [MFC], m_bAutoDelete
- CWinThread [MFC], m_hThread
- CWinThread [MFC], m_nThreadID
- CWinThread [MFC], m_pActiveWnd
- CWinThread [MFC], m_pMainWnd
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
ms.openlocfilehash: f2e95dd3ba8be31633590e37d95dedc8749ebdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367423"
---
# <a name="cwinthread-class"></a>CWinThread 类

表示应用程序中的执行线程。

## <a name="syntax"></a>语法

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWinThread：CWinThread](#cwinthread)|构造 `CWinThread` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWinThread：：创建线程](#createthread)|开始执行`CWinThread`对象。|
|[CWinThread：退出实例](#exitinstance)|重写以在线程终止时清理。|
|[CWinThread：获取主菜](#getmainwnd)|检索指向线程的主窗口的指针。|
|[CWinThread：获取线程优先级](#getthreadpriority)|获取当前线程的优先级。|
|[CWinThread：inininininininininininininininininininininin](#initinstance)|重写以执行线程实例初始化。|
|[CWinThread：：空闲消息](#isidlemessage)|检查特殊消息。|
|[CWinThread：onidle](#onidle)|覆盖以执行特定于线程的空闲时间处理。|
|[CWinThread：:P奥斯特线程消息](#postthreadmessage)|将消息发布到其他`CWinThread`对象。|
|[CWinThread：:P重新翻译消息](#pretranslatemessage)|在邮件发送到 Windows 函数["翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)"和["调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)"之前对其进行筛选。|
|[CWinThread：:Process消息过滤器](#processmessagefilter)|在某些消息到达应用程序之前拦截它们。|
|[CWinThread：:P罗塞斯·温德普罗奇例外](#processwndprocexception)|拦截线程的消息和命令处理程序引发的所有未处理异常。|
|[CWinThread：:Pump消息](#pumpmessage)|包含线程的消息循环。|
|[CWinThread：恢复线程](#resumethread)|取消线程的挂起计数。|
|[CWinThread：运行](#run)|使用消息泵控制螺纹的功能。 重写以自定义默认消息循环。|
|[CWinThread：：设置线程优先级](#setthreadpriority)|设置当前线程的优先级。|
|[CWinThread：暂停线程](#suspendthread)|增加线程的挂起计数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CWinThread：：操作员 HANDLE](#operator_handle)|检索`CWinThread`对象的句柄。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CWinThread：m_bAutoDelete](#m_bautodelete)|指定是否在线程终止时销毁对象。|
|[CWinThread：m_hThread](#m_hthread)|处理当前线程。|
|[CWinThread：m_nThreadID](#m_nthreadid)|当前线程的 ID。|
|[CWinThread：m_pActiveWnd](#m_pactivewnd)|当 OLE 服务器就地处于活动状态时，指向容器应用程序的主窗口。|
|[CWinThread：m_pMainWnd](#m_pmainwnd)|保存指向应用程序主窗口的指针。|

## <a name="remarks"></a>备注

执行的主线程通常由派生自`CWinApp`的对象提供。`CWinApp`派生自`CWinThread`。 其他`CWinThread`对象允许在给定应用程序中有多个线程。

`CWinThread`支持两种常规类型的线程：工作线程和用户界面线程。 工作线程没有消息泵：例如，在电子表格应用程序中执行后台计算的线程。 用户界面线程具有消息泵和处理从系统接收的消息。 [CWinApp](../../mfc/reference/cwinapp-class.md)和派生自它的类是用户界面线程的示例。 其他用户界面线程也可以直接从`CWinThread`派生。

类`CWinThread`的对象通常存在于线程的持续时间内。 如果要修改此行为，请[将m_bAutoDelete](#m_bautodelete)设置为 FALSE。

要使`CWinThread`代码和 MFC 完全线程安全，必须使用该类。 框架用于维护线程特定信息的线程本地数据由`CWinThread`对象管理。 由于依赖`CWinThread`来处理线程本地数据，因此使用 MFC 的任何线程必须由 MFC 创建。 例如，运行时函数_beginthread创建的线程[，_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)无法使用任何 MFC API。

要创建线程，请致电[AfxBeginThread](application-information-and-management.md#afxbeginthread)。 有两种形式，具体取决于是需要辅助角色线程还是用户界面线程。 如果需要用户界面线程，请传递到`AfxBeginThread`指向`CRuntimeClass``CWinThread`派生类的指针。 如果要创建辅助线程，请传递到`AfxBeginThread`指向控制函数的指针以及指向控制函数的参数。 对于工作线程和用户界面线程，可以指定修改优先级、堆栈大小、创建标志和安全属性的可选参数。 `AfxBeginThread`将返回指向新`CWinThread`对象的指针。

可以构造`AfxBeginThread``CWinThread`派生对象，然后调用`CreateThread`，而不是调用 。 如果要在连续创建和线程执行终止之间重用该对象，`CWinThread`则此两阶段构造方法非常有用。

有关 的详细信息`CWinThread`，请参阅[文章"使用 C++和 MFC 进行多线程"，](../../parallel/multithreading-with-cpp-and-mfc.md)[多线程：创建用户界面线程](../../parallel/multithreading-creating-user-interface-threads.md)、[多线程：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)和[多线程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread：：创建线程

创建要在调用进程的地址空间内执行的线程。

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>参数

*dwCreateFlags*<br/>
指定控制创建线程的其他标志。 此标志可以包含两个值之一：

- CREATE_SUSPENDED 以 1 的挂起计数启动线程。 如果要在线程开始运行之前初始化`CWinThread`对象的任何成员数据（如[m_bAutoDelete](#m_bautodelete)或派生类的任何成员，请使用CREATE_SUSPENDED。 初始化完成后，使用[CWinThread：resumeThread](#resumethread)开始线程运行。 在调用线程之前`CWinThread::ResumeThread`，线程不会执行。

- **0**创建后立即启动线程。

*nStackSize*<br/>
指定新线程堆栈的大小（以字节为单位）。 如果**为 0，** 则堆栈大小默认与进程主线程的大小相同。

*lpSecurityAttrs*<br/>
指向指定线程的安全属性[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构。

### <a name="return-value"></a>返回值

如果线程成功创建，则非零;否则 0。

### <a name="remarks"></a>备注

用于`AfxBeginThread`创建线程对象并在一个步骤中执行它。 如果要`CreateThread`在连续创建和终止线程执行之间重用线程对象，请使用。

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread：CWinThread

构造 `CWinThread` 对象。

```
CWinThread();
```

### <a name="remarks"></a>备注

要开始线程的执行，请调用[CreateThread](#createthread)成员函数。 您通常通过调用[AfxBeginThread](application-information-and-management.md#afxbeginthread)来创建线程，这将调用此构造函数`CreateThread`和 。

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread：退出实例

由框架从很少重写[的 Run](#run)成员函数中调用以退出线程的此实例，或者如果对[InitInstance](#initinstance)的调用失败。

```
virtual int ExitInstance();
```

### <a name="return-value"></a>返回值

线程的退出代码;0 表示没有错误，大于 0 的值表示错误。 可以通过调用[GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)来检索此值。

### <a name="remarks"></a>备注

不要从任何位置调用此成员函数，`Run`但不得在成员函数内调用。 此成员函数仅在用户界面线程中使用。

如果`CWinThread`[m_bAutoDelete](#m_bautodelete)为 TRUE，则此函数的默认实现将删除该对象。 如果要在线程终止时执行其他清理，请重写此函数。 执行代码后`ExitInstance`，应调用 基类的版本。

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread：获取主菜

如果应用程序是 OLE 服务器，请调用此函数以检索指向应用程序活动主窗口的指针，而不是直接引用应用程序对象`m_pMainWnd`的成员。

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>返回值

此函数返回指向两种类型的窗口之一的指针。 如果线程是 OLE 服务器的一部分，并且对象在活动容器内处于活动状态，则此函数将返回`CWinThread`对象的[CWinApp：：m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd)数据成员。

如果容器内没有就地处于活动状态的对象，或者您的应用程序不是 OLE 服务器，则此函数将返回线程对象的[m_pMainWnd](#m_pmainwnd)数据成员。

### <a name="remarks"></a>备注

对于用户界面线程，这相当于直接引用应用程序对象`m_pActiveWnd`的成员。

如果您的应用程序不是 OLE 服务器，调用此函数相当于直接引用应用程序对象的 `m_pMainWnd` 成员。

重写此函数以修改默认行为。

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread：获取线程优先级

获取此线程的当前线程优先级级别。

```
int GetThreadPriority();
```

### <a name="return-value"></a>返回值

其优先级类中的当前线程优先级级别。 返回的值将是以下值之一，从最高优先级列至最低优先级：

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

有关这些优先级的详细信息，请参阅 Windows SDK 中的[SetThreadPriority。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread：inininininininininininininininininininininin

`InitInstance`必须重写才能初始化用户界面线程的每个新实例。

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>返回值

初始化成功时非零;否则 0。

### <a name="remarks"></a>备注

通常，您可以重写`InitInstance`以执行在首次创建线程时必须完成的任务。

此成员函数仅在用户界面线程中使用。 在传递给[AfxBeginThread](application-information-and-management.md#afxbeginthread)的控制函数中执行辅助线程的初始化。

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread：：空闲消息

重写此函数以防止`OnIdle`在生成特定消息后被调用。

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>参数

*pMsg*<br/>
指向正在处理的当前消息。

### <a name="return-value"></a>返回值

处理消息后`OnIdle`应调用非零;如果处理消息后应调用非零。否则 0。

### <a name="remarks"></a>备注

默认实现不会在冗余鼠标`OnIdle`消息和闪烁的 cares 生成的消息之后调用。

如果应用程序已创建短计时器，`OnIdle`将频繁调用，从而导致性能问题。 为了提高此类应用程序的性能，请在应用程序的`IsIdleMessage``CWinApp`派生类中重写以检查WM_TIMER消息，如下所示：

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

以这种方式处理WM_TIMER将提高使用短计时器的应用程序的性能。

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a>CWinThread：m_bAutoDelete

指定 `CWinThread` 对象是否应在线程终止时自动删除。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>备注

数据`m_bAutoDelete`成员是 BOOL 类型的公共变量。

的值`m_bAutoDelete`不会影响基础线程句柄的关闭方式，但它确实会影响关闭句柄的时间。 在销毁 `CWinThread` 对象时，始终关闭线程句柄。

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a>CWinThread：m_hThread

处理附加到此`CWinThread`的线程。

```
HANDLE m_hThread;
```

### <a name="remarks"></a>备注

数据`m_hThread`成员是 HANDLE 类型的公共变量。 仅当基础内核线程对象当前存在且句柄尚未关闭时，它才有效。

CWinThread 析构函数调用 上的`m_hThread`CloseHandle。 如果[当](#m_bautodelete)线程终止时m_bAutoDelete为 TRUE，则 CWinThread 对象将被销毁，从而使指向 CWinThread 对象及其成员变量的任何指针无效。 您可能需要成员`m_hThread`检查线程退出值，或等待信号。 要在线程执行期间和终止后保留`m_hThread`CWinThread 对象及其成员，请设置为`m_bAutoDelete`FALSE，然后再允许线程执行继续。 否则，线程可能会终止、销毁 CWinThread 对象，并在尝试使用它之前关闭句柄。 如果使用此技术，则负责删除 CWinThread 对象。

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a>CWinThread：m_nThreadID

附加到此`CWinThread`的线程的 ID。

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>备注

数据`m_nThreadID`成员是 DWORD 类型的公共变量。 仅当基础内核线程对象当前存在时，它才有效。
另请参阅有关[m_hThread](#m_hthread)生存期的评论。

### <a name="example"></a>示例

  请参阅[AfxGetThread](application-information-and-management.md#afxgetthread)的示例。

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinThread：m_pActiveWnd

使用此数据成员可以存储指向线程活动窗口对象的指针。

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>备注

当引用`m_pActiveWnd`的窗口关闭时，Microsoft 基础类库将自动终止线程。 如果此线程是应用程序的主线程，则应用程序也将终止。 如果此数据成员为 NULL，则将继承应用程序`CWinApp`对象的活动窗口。 `m_pActiveWnd`是类型的`CWnd*`公共变量。

通常，在重写`InitInstance`时设置此成员变量。 在辅助线程中，此数据成员的值从其父线程继承。

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a>CWinThread：m_pMainWnd

使用此数据成员可以存储指向线程主窗口对象的指针。

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>备注

当引用`m_pMainWnd`的窗口关闭时，Microsoft 基础类库将自动终止线程。 如果此线程是应用程序的主线程，则应用程序也将终止。 如果此数据成员为 NULL，则应用程序`CWinApp`对象的主窗口将用于确定何时终止线程。 `m_pMainWnd`是类型的`CWnd*`公共变量。

通常，在重写`InitInstance`时设置此成员变量。 在辅助线程中，此数据成员的值从其父线程继承。

## <a name="cwinthreadonidle"></a><a name="onidle"></a>CWinThread：onidle

重写此成员函数以执行空闲时间处理。

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>参数

*lCount*<br/>
当线程的消息队列为空`OnIdle`时，每次调用一个计数器。 每次处理新消息时，此计数都会重置为 0。 可以使用*lCount*参数来确定线程空闲的相对时间长度，而无需处理消息。

### <a name="return-value"></a>返回值

非零接收更多的空闲处理时间;如果不需要更多的空闲处理时间，则为 0。

### <a name="remarks"></a>备注

`OnIdle`当线程的消息队列为空时，在默认消息循环中调用。 使用重写调用您自己的后台空闲处理程序任务。

`OnIdle`应返回 0 以指示不需要额外的空闲处理时间。 每次`OnIdle`在消息队列为空时调用*lCount*参数都会增加，并且每次处理新消息时都重置为 0。 您可以基于此计数调用不同的空闲例程。

此成员函数的默认实现将临时对象和未使用的动态链接库从内存中释放。

此成员函数仅在用户界面线程中使用。

由于应用程序无法处理消息，直到`OnIdle`返回，因此不要在此函数中执行冗长的任务。

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread：：操作员 HANDLE

检索`CWinThread`对象的句柄。

```
operator HANDLE() const;
```

### <a name="return-value"></a>返回值

如果成功，线程对象的句柄;否则，NULL。

### <a name="remarks"></a>备注

使用该句柄直接调用 Windows API。

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread：:P奥斯特线程消息

调用以将用户定义的消息发布到其他`CWinThread`对象。

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*消息*<br/>
用户定义消息的 ID。

*wParam*<br/>
第一个消息参数。

*lParam*<br/>
第二个消息参数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

消息映射宏ON_THREAD_MESSAGE将发布的消息映射到正确的消息处理程序。

> [!NOTE]
> 当您调用[PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)时，消息将放置在线程的消息队列中。 但是，由于以这种方式发布的消息不与窗口关联，MFC 不会将它们调度到消息或命令处理程序。 为了处理这些消息，请重写`PreTranslateMessage()`CWinApp 派生类的功能，并手动处理消息。

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread：:P重新翻译消息

重写此函数以筛选窗口消息，然后再将其发送到 Windows 函数[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>参数

*pMsg*<br/>
指向包含要处理的消息的[MSG 结构](/windows/win32/api/winuser/ns-winuser-msg)。

### <a name="return-value"></a>返回值

如果消息已完全处理，`PreTranslateMessage`则非零，不应进一步处理。 如果消息应以正常方式处理，则为零。

### <a name="remarks"></a>备注

此成员函数仅在用户界面线程中使用。

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread：:Process消息过滤器

框架的 hook 函数调用此成员函数来筛选和响应某些 Windows 消息。

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>参数

*代码*<br/>
指定挂钩代码。 此成员函数使用代码来确定如何处理*lpMsg。*

*lpMsg*<br/>
指向 Windows [MSG 结构](/windows/win32/api/winuser/ns-winuser-msg)的指针。

### <a name="return-value"></a>返回值

处理消息时非零;否则 0。

### <a name="remarks"></a>备注

hook 函数在事件发送到应用程序的正常消息处理之前处理事件。

如果重写此高级功能，请确保调用基类版本以维护框架的挂钩处理。

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread：:P罗塞斯·温德普罗奇例外

每当处理程序不捕获线程的消息或命令处理程序中引发异常时，框架将调用此成员函数。

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>参数

*e*<br/>
指向未处理的异常。

*pMsg*<br/>
指向包含导致框架引发异常的窗口消息的信息的[MSG 结构](/windows/win32/api/winuser/ns-winuser-msg)。

### <a name="return-value"></a>返回值

-1 如果生成WM_CREATE异常;如果生成异常，则为 -1;否则 0。

### <a name="remarks"></a>备注

不要直接调用此成员函数。

此成员函数的默认实现仅处理以下消息生成的异常：

|Command|操作|
|-------------|------------|
|WM_CREATE|Fail。|
|WM_PAINT|验证受影响的窗口，从而阻止生成另一WM_PAINT消息。|

重写此成员函数，以提供异常的全局处理。 仅当希望显示默认行为时，才调用基本功能。

此成员函数仅在具有消息泵的线程中使用。

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread：:Pump消息

包含线程的消息循环。

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>备注

`PumpMessage`包含线程的消息循环。 `PumpMessage`调用 以`CWinThread`泵送线程的消息。 您可以直接调用`PumpMessage`以强制处理邮件，也可以重写`PumpMessage`以更改其默认行为。

建议`PumpMessage`仅对高级用户直接调用并重写其默认行为。

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread：恢复线程

调用 以恢复执行由[挂起Thread](#suspendthread)成员函数挂起的线程，或使用 CREATE_SUSPENDED 标志创建的线程。

```
DWORD ResumeThread();
```

### <a name="return-value"></a>返回值

线程以前的挂起计数（如果成功）;`0xFFFFFFFF`否则。 如果返回值为零，则当前线程未挂起。 如果返回值为 1，则线程已挂起，但现在重新启动。 任何大于 1 的返回值都意味着线程将保持挂起状态。

### <a name="remarks"></a>备注

当前线程的挂起计数减少 1。 如果挂起计数减少到零，线程将恢复执行;如果挂起计数减少到零，则线程将恢复执行。否则，线程将保持挂起状态。

## <a name="cwinthreadrun"></a><a name="run"></a>CWinThread：运行

为用户界面线程提供默认消息循环。

```
virtual int Run();
```

### <a name="return-value"></a>返回值

线程返回的**int**值。 可以通过调用[GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)来检索此值。

### <a name="remarks"></a>备注

`Run`获取和调度 Windows 消息，直到应用程序收到[WM_QUIT](/windows/win32/winmsg/wm-quit)消息。 如果线程的消息队列当前不包含任何消息，则`Run`调用`OnIdle`以执行空闲时间处理。 传入消息转到[PreTranslateMessage](#pretranslatemessage)成员函数进行特殊处理，然后转到 Windows 函数[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)进行标准键盘翻译。 最后，调用[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口函数。

`Run`很少重写，但您可以重写它以实现特殊行为。

此成员函数仅在用户界面线程中使用。

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread：：设置线程优先级

此函数在其优先级类中设置当前线程的优先级。

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>参数

*n优先*<br/>
在其优先级类中指定新的线程优先级级别。 此参数必须是以下值之一，从最高优先级列至最低优先级：

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

有关这些优先级的详细信息，请参阅 Windows SDK 中的[SetThreadPriority。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

### <a name="return-value"></a>返回值

如果函数成功，则非零;否则 0。

### <a name="remarks"></a>备注

只能在[CreateThread](#createthread)成功返回后调用它。

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread：暂停线程

增加当前线程的挂起计数。

```
DWORD SuspendThread();
```

### <a name="return-value"></a>返回值

线程以前的挂起计数（如果成功）;`0xFFFFFFFF`否则。

### <a name="remarks"></a>备注

如果任何线程的挂起计数高于零，则该线程不会执行。 可以通过调用[ResumeThread](#resumethread)成员函数来恢复线程。

## <a name="see-also"></a>另请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWinApp 类](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
