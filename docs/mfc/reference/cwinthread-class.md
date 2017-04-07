---
title: "CWinThread 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- worker threads
- threading [MFC], safety
- CWinThread class
- threading [MFC], creating threads
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 866e847f9c1d73d6f9882e50b1274fbad9e21a39
ms.lasthandoff: 02/24/2017

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
|[CWinThread::CWinThread](#cwinthread)|构造 `CWinThread` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CWinThread::CreateThread](#createthread)|开始执行`CWinThread`对象。|  
|[CWinThread::ExitInstance](#exitinstance)|重写您的线程终止时进行清理。|  
|[CWinThread::GetMainWnd](#getmainwnd)|检索指向线程在主窗口的指针。|  
|[CWinThread::GetThreadPriority](#getthreadpriority)|获取当前线程的优先级。|  
|[CWinThread::InitInstance](#initinstance)|重写以执行线程实例初始化。|  
|[CWinThread::IsIdleMessage](#isidlemessage)|特殊的消息的检查。|  
|[CWinThread::OnIdle](#onidle)|重写以执行特定于线程的空闲时间处理。|  
|[CWinThread::PostThreadMessage](#postthreadmessage)|将消息发送到另一个`CWinThread`对象。|  
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|在它们调度到 Windows 函数之前筛选消息[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。|  
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|截获某些消息到达应用程序之前。|  
|[CWinThread::ProcessWndProcException](#processwndprocexception)|截获由线程的消息和命令处理程序引发的所有未处理的异常。|  
|[CWinThread::PumpMessage](#pumpmessage)|包含线程的消息循环。|  
|[CWinThread::ResumeThread](#resumethread)|递减一线程的挂起计数。|  
|[Cwinthread:: Run](#run)|具有消息泵的线程控制函数。 重写以自定义默认消息循环。|  
|[CWinThread::SetThreadPriority](#setthreadpriority)|设置当前线程的优先级。|  
|[CWinThread::SuspendThread](#suspendthread)|增量的线程的挂起计数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CWinThread::operator 句柄](#operator_handle)|检索的句柄`CWinThread`对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CWinThread::m_bAutoDelete](#m_bautodelete)|指定是否要销毁的对象在线程终止。|  
|[CWinThread::m_hThread](#m_hthread)|当前线程的句柄。|  
|[CWinThread::m_nThreadID](#m_nthreadid)|当前线程的 ID。|  
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|向容器应用程序是 OLE 服务器处于就地活动状态时的主窗口的指针。|  
|[CWinThread::m_pMainWnd](#m_pmainwnd)|包含指向应用程序的主窗口。|  
  
## <a name="remarks"></a>备注  
 主执行线程通常由一个对象派生自`CWinApp`;`CWinApp`派生自`CWinThread`。 其他`CWinThread`对象允许将多个线程在给定应用程序。  
  
 有两种常规类型的线程，`CWinThread`支持︰ 辅助线程和用户界面线程。 工作线程都没有消息泵︰ 例如，在电子表格应用程序中执行后台计算一个线程。 用户界面线程有一个消息泵并处理从系统收到的消息。 [CWinApp](../../mfc/reference/cwinapp-class.md)和从它派生的类都是用户界面线程的示例。 其他用户界面线程也可以直接从派生`CWinThread`。  
  
 类的对象`CWinThread`通常存在于线程的持续时间。 如果你想要修改此行为，设置[m_bAutoDelete](#m_bautodelete)到**FALSE**。  
  
 `CWinThread`类有必要使您的代码和 MFC 完全线程安全。 由框架用于维护线程特定的信息的线程本地数据`CWinThread`对象。 由于在这种依赖性`CWinThread`来处理线程本地数据，使用 MFC 的任何线程必须由 MFC 创建。 例如，运行时函数创建的线程[_beginthread、 _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)不能使用任何 MFC Api。  
  
 若要创建线程时，调用[AfxBeginThread](application-information-and-management.md#afxbeginthread)。 有两种形式，具体取决于您是否希望工作人员或用户界面线程。 如果您希望用户界面线程，将传递给`AfxBeginThread`指向的指针`CRuntimeClass`的您`CWinThread`的派生类。 如果你想要创建工作线程，将传递到`AfxBeginThread`对控制功能和控制函数的参数的指针。 对于工作线程和用户界面线程中，可以指定可选参数来修改优先级、 堆栈大小、 创建标志和安全属性。 `AfxBeginThread`会将一个指针返回到您的新`CWinThread`对象。  
  
 而不是调用`AfxBeginThread`，您可以构造`CWinThread`-派生的对象，然后调用`CreateThread`。 如果您想要重用此两阶段构建方法很有用`CWinThread`连续创建和终止线程执行之间的对象。  
  
 有关详细信息`CWinThread`，请参阅文章[使用 c + + 和 MFC 进行多线程处理](../../parallel/multithreading-with-cpp-and-mfc.md)，[多线程处理︰ 创建用户界面线程](../../parallel/multithreading-creating-user-interface-threads.md)，[多线程处理︰ 创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)，和[多线程处理︰ 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="createthread"></a>CWinThread::CreateThread  
 创建一个线程来执行调用进程的地址空间内。  
  
```  
BOOL CreateThread(
    DWORD dwCreateFlags = 0,  
    UINT nStackSize = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```  
  
### <a name="parameters"></a>参数  
 `dwCreateFlags`  
 指定控制该线程创建一个额外的标记。 此标志可以包含两个值之一︰  
  
- **CREATE_SUSPENDED**开头的挂起计数为其中一个线程。 使用**CREATE_SUSPENDED**如果您想要初始化的任何成员数据`CWinThread`对象，如[m_bAutoDelete](#m_bautodelete)或派生类中，在该线程开始运行前的任何成员。 您初始化完成后，使用[CWinThread::ResumeThread](#resumethread)开始运行的线程。 该线程不会执行直到`CWinThread::ResumeThread`调用。  
  
- **0**在创建后立即启动该线程。  
  
 `nStackSize`  
 以字节为单位的新线程的堆栈中指定的大小。 如果**0**，堆栈大小默认为与该进程的主线程的大小相同。  
  
 `lpSecurityAttrs`  
 指向[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)结构，它指定线程的安全属性。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建线程，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`AfxBeginThread`创建线程对象并执行一个步骤中。 使用`CreateThread`如果您想要重用之间连续创建和终止线程执行的线程对象。  
  
##  <a name="cwinthread"></a>CWinThread::CWinThread  
 构造 `CWinThread` 对象。  
  
```  
CWinThread();
```  
  
### <a name="remarks"></a>备注  
 若要开始线程的执行，请调用[CreateThread](#createthread)成员函数。 通常将通过调用创建线程[AfxBeginThread](http://msdn.microsoft.com/library/e9e8684d-24f7-4599-8fdf-1f4f560a753b)，它将调用此构造函数和`CreateThread`。  
  
##  <a name="exitinstance"></a>CWinThread::ExitInstance  
 由框架调用从中很少会重写[运行](#run)成员函数以退出此实例的线程，或如果调用[InitInstance](#initinstance)失败。  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>返回值  
 该线程退出代码;0 表示没有错误，而值大于 0 表示出现错误。 此值可以通过调用来检索[GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)。  
  
### <a name="remarks"></a>备注  
 不调用该成员函数从任意位置之内**运行**成员函数。 仅在用户界面线程中使用此成员函数。  
  
 此函数的默认实现中删除`CWinThread`对象，如果[m_bAutoDelete](#m_bautodelete)是**TRUE**。 如果您想要执行其他清理您的线程终止时，重写此函数。 实现`ExitInstance`执行您的代码后，应调用基类的版本。  
  
##  <a name="getmainwnd"></a>CWinThread::GetMainWnd  
 如果您的应用程序是 OLE 服务器，调用此函数可检索一个指向而不是直接引用应用程序的活动主窗口`m_pMainWnd`应用程序对象的成员。  
  
```  
virtual CWnd* GetMainWnd();
```  
  
### <a name="return-value"></a>返回值  
 此函数返回一个指向 windows 的两种类型之一。 如果您的线程是 OLE 服务器的一部分，并且具有一个对象，它在活动容器内的处于就地活动状态，此函数可返回[CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd)数据成员的`CWinThread`对象。  
  
 如果没有为容器内的处于就地活动状态的对象，或者您的应用程序不是 OLE 服务器，此函数将返回[m_pMainWnd](#m_pmainwnd)线程对象的数据成员。  
  
### <a name="remarks"></a>备注  
 对于用户界面线程，这相当于直接引用`m_pActiveWnd`应用程序对象的成员。  
  
 如果您的应用程序不是 OLE 服务器，调用此函数相当于直接引用应用程序对象的 `m_pMainWnd` 成员。  
  
 重写此函数可修改默认行为。  
  
##  <a name="getthreadpriority"></a>CWinThread::GetThreadPriority  
 获取此线程的当前线程优先级别。  
  
```  
int GetThreadPriority();
```  
  
### <a name="return-value"></a>返回值  
 在其优先级类中当前线程优先级别。 返回的值将是以下之一，从最高优先级到最低的顺序列出︰  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 有关这些优先级的详细信息，请参阅[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="initinstance"></a>CWinThread::InitInstance  
 `InitInstance`必须重写以初始化用户界面线程的每个新实例。  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 通常情况下，重写`InitInstance`执行首次创建一个线程时必须完成的任务。  
  
 仅在用户界面线程中使用此成员函数。 在控制传递到函数中执行的工作线程初始化[AfxBeginThread](application-information-and-management.md#afxbeginthread)。  
  
##  <a name="isidlemessage"></a>CWinThread::IsIdleMessage  
 重写此函数以保留**OnIdle**生成特定消息后被调用。  
  
```  
virtual BOOL IsIdleMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 `pMsg`  
 指向当前正在处理的消息。  
  
### <a name="return-value"></a>返回值  
 如果非零`OnIdle`应在处理后调用消息; 否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现不会调用**OnIdle**冗余鼠标消息和生成的插入符号闪烁消息之后。  
  
 如果应用程序已创建了一个简短的计时器， **OnIdle**将调用通常情况下，导致性能问题。 若要改善此类应用程序的性能，重写`IsIdleMessage`中应用程序的`CWinApp`的派生类来检查`WM_TIMER`消息，如下所示︰  
  
 [!code-cpp[NVC_MFCDocView #&189;](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]  
  
 处理`WM_TIMER`这种方式将提高性能的应用程序使用简短的计时器。  
  
##  <a name="m_bautodelete"></a>CWinThread::m_bAutoDelete  
 指定 `CWinThread` 对象是否应在线程终止时自动删除。  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>备注  
 `m_bAutoDelete`数据成员是类型的公共变量**BOOL**。  
  
 `m_bAutoDelete` 的值不影响关闭基础线程句柄的方式。 在销毁 `CWinThread` 对象时，始终关闭线程句柄。  
  
##  <a name="m_hthread"></a>CWinThread::m_hThread  
 附加到此该线程的句柄`CWinThread`。  
  
```  
HANDLE m_hThread;  
```  
  
### <a name="remarks"></a>备注  
 `m_hThread`数据成员是类型的公共变量`HANDLE`。 如果当前基础线程存在，才有效。  
  
##  <a name="m_nthreadid"></a>CWinThread::m_nThreadID  
 线程的 ID 附加到此`CWinThread`。  
  
```  
DWORD m_nThreadID;  
```  
  
### <a name="remarks"></a>备注  
 **M_nThreadID**数据成员是类型的公共变量`DWORD`。 如果当前基础线程存在，才有效。  
  
### <a name="example"></a>示例  
  请参阅示例[AfxGetThread](application-information-and-management.md#afxgetthread)。  
  
##  <a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd  
 使用此数据成员来存储指向线程的活动窗口对象的指针。  
  
```  
CWnd* m_pActiveWnd;  
```  
  
### <a name="remarks"></a>备注  
 Microsoft 基础类库将自动终止您的线程窗口中被引用时通过`m_pActiveWnd`已关闭。 如果此线程为应用程序的主线程，也将终止该应用程序。 如果此数据成员是**NULL**，为应用程序的活动窗口`CWinApp`对象将被继承。 `m_pActiveWnd`是类型的公共变量**CWnd\***。  
  
 通常情况下，设置此成员变量，当您重写`InitInstance`。 在辅助线程中，此数据成员的值继承自其父线程。  
  
##  <a name="m_pmainwnd"></a>CWinThread::m_pMainWnd  
 使用此数据成员来存储指向线程的主窗口对象的指针。  
  
```  
CWnd* m_pMainWnd;  
```  
  
### <a name="remarks"></a>备注  
 Microsoft 基础类库将自动终止您的线程窗口中被引用时通过`m_pMainWnd`已关闭。 如果此线程为应用程序的主线程，也将终止该应用程序。 如果此数据成员是**NULL**，为应用程序的主窗口`CWinApp`对象将用于确定何时终止该线程。 `m_pMainWnd`是类型的公共变量**CWnd\***。  
  
 通常情况下，设置此成员变量，当您重写`InitInstance`。 在辅助线程中，此数据成员的值继承自其父线程。  
  
##  <a name="onidle"></a>CWinThread::OnIdle  
 重写该成员函数以执行空闲处理。  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>参数  
 `lCount`  
 每次递增一个计数器`OnIdle`线程的消息队列为空时调用。 每次处理新消息时，此计数是置为 0。 您可以使用`lCount`参数，以确定相对的线程而不会处理一条消息处于空闲状态的时间长度。  
  
### <a name="return-value"></a>返回值  
 非零值，接收更多空闲处理时间;如果需要没有更多空闲处理时间为 0。  
  
### <a name="remarks"></a>备注  
 `OnIdle`默认消息循环中线程的消息队列为空时调用。 使用重写中调用您自己的背景空闲处理程序的任务。  
  
 `OnIdle`应返回 0 以指示需要任何额外的空闲处理时间。 `lCount`参数会在每次递增`OnIdle`时消息队列为空，并且将重置为 0 每次处理新消息时调用。 您可以调用不同空闲例程根据此计数。  
  
 此成员函数的默认实现将释放临时对象和从内存的未使用的动态链接库。  
  
 仅在用户界面线程中使用此成员函数。  
  
 因为应用程序无法处理消息之前`OnIdle`返回时，在此函数不执行耗时较长的任务。  
  
##  <a name="operator_handle"></a>CWinThread::operator 句柄  
 检索的句柄`CWinThread`对象。  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，使线程对象; 的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 使用该句柄直接调用 Windows Api。  
  
##  <a name="postthreadmessage"></a>CWinThread::PostThreadMessage  
 调用以将用户定义消息发布到另一个`CWinThread`对象。  
  
```  
BOOL PostThreadMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `message`  
 用户定义消息的 ID。  
  
 `wParam`  
 第一个消息参数。  
  
 `lParam`  
 第二个消息参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 已发布的消息映射到正确的消息处理程序的消息映射宏`ON_THREAD_MESSAGE`。  
  
> [!NOTE]
>  当调用 Windows [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946) MFC 应用程序内，MFC 消息处理程序，不会调用的函数。 有关详细信息，请参阅知识库文章"PRB:: MFC 消息处理程序不调用与 PostThreadMessage()"(Q142415)。  
  
##  <a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage  
 重写此函数可对筛选器窗口消息被发送到 Windows 函数之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 `pMsg`  
 指向[MSG 结构](../../mfc/reference/msg-structure1.md)包含要处理的消息。  
  
### <a name="return-value"></a>返回值  
 如果在完全处理了消息，则为非`PreTranslateMessage`，并且不应进一步处理。 如果应以正常方式处理该消息，则为零。  
  
### <a name="remarks"></a>备注  
 仅在用户界面线程中使用此成员函数。  
  
##  <a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter  
 框架的挂钩函数调用该成员函数以筛选和响应特定 Windows 消息。  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>参数  
 `code`  
 指定挂钩代码。 此成员函数将使用代码确定如何处理`lpMsg.`  
  
 `lpMsg`  
 一个指向 Windows [MSG 结构](../../mfc/reference/msg-structure1.md)。  
  
### <a name="return-value"></a>返回值  
 如果处理了消息; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 挂钩函数将处理事件之前它们被发送到应用程序的正常消息处理。  
  
 如果重写此高级的功能时，一定要调用基类版本以维护框架的挂钩处理。  
  
##  <a name="processwndprocexception"></a>CWinThread::ProcessWndProcException  
 框架调用此成员函数，只要该处理程序不捕获中的一个线程的消息或命令处理程序引发的异常。  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 *e*  
 指向以未处理的异常。  
  
 `pMsg`  
 指向[MSG 结构](../../mfc/reference/msg-structure1.md)包含导致引发异常的框架的 windows 消息有关的信息。  
  
### <a name="return-value"></a>返回值  
 – 1 如果`WM_CREATE`则会生成异常; 否则为 0。  
  
### <a name="remarks"></a>备注  
 不要直接调用此成员函数。  
  
 此成员函数的默认实现处理仅从以下邮件生成的异常︰  
  
|命令|操作|  
|-------------|------------|  
|`WM_CREATE`|失败。|  
|`WM_PAINT`|验证受影响的窗口中，从而阻止出现另一个`WM_PAINT`来自正在生成消息。|  
  
 重写该成员函数以提供全局处理的异常。 仅当您想要显示的默认行为，请调用的基本功能。  
  
 仅在有一个消息泵的线程中使用此成员函数。  
  
##  <a name="pumpmessage"></a>CWinThread::PumpMessage  
 包含线程的消息循环。  
  
```  
virtual BOOL PumpMessage();
```  
  
### <a name="remarks"></a>备注  
 `PumpMessage`包含线程的消息循环。 **PumpMessage**由调用`CWinThread`来发送线程的消息。 您可以调用`PumpMessage`直接强制消息进行处理，也可以重写`PumpMessage`若要更改其默认行为。  
  
 调用`PumpMessage`直接，重写其默认行为适用于高级用户。  
  
##  <a name="resumethread"></a>CWinThread::ResumeThread  
 若要继续执行挂起的线程的调用[SuspendThread](#suspendthread)成员函数或使用创建的线程**CREATE_SUSPENDED**标志。  
  
```  
DWORD ResumeThread();
```  
  
### <a name="return-value"></a>返回值  
 该线程的上一个挂起计数，如果成功，则`0xFFFFFFFF`否则为。 如果返回值为零，是不会挂起当前线程。 如果返回值为&1;，该线程已挂起，但现在重新启动。 任何返回的值大于&1; 意味着该线程将保持挂起。  
  
### <a name="remarks"></a>备注  
 当前线程的挂起计数被减少一个。 如果减小的挂起计数为零，该线程将继续执行。否则该线程将一直挂起。  
  
##  <a name="run"></a>Cwinthread:: Run  
 为用户界面线程提供一个默认的消息循环。  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>返回值  
 `int`由线程返回的值。 此值可以通过调用来检索[GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)。  
  
### <a name="remarks"></a>备注  
 **运行**获取，并将 Windows 消息调度直到应用程序收到[WM_QUIT](http://msdn.microsoft.com/library/windows/desktop/ms632641)消息。 如果当前线程的消息队列不包含任何消息中，**运行**调用`OnIdle`来执行空闲处理。 传入消息将转到[PreTranslateMessage](#pretranslatemessage)成员函数以进行特殊处理，然后执行到 Windows 函数[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)标准键盘翻译。 最后， [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)调用 Windows 函数。  
  
 **运行**很少会重写，但您可以覆盖以使其实现的特殊行为。  
  
 仅在用户界面线程中使用此成员函数。  
  
##  <a name="setthreadpriority"></a>CWinThread::SetThreadPriority  
 此函数将设置其优先级类中的当前线程的优先级。  
  
```  
BOOL SetThreadPriority(int nPriority);
```  
  
### <a name="parameters"></a>参数  
 `nPriority`  
 指定在其优先级类中的新线程优先级别。 此参数必须是从最高优先级到最低的顺序列出的以下值之一︰  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 有关这些优先级的详细信息，请参阅[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 仅之后调用[CreateThread](#createthread)成功返回。  
  
##  <a name="suspendthread"></a>CWinThread::SuspendThread  
 递增当前线程的挂起计数。  
  
```  
DWORD SuspendThread();
```  
  
### <a name="return-value"></a>返回值  
 该线程的上一个挂起计数，如果成功，则`0xFFFFFFFF`否则为。  
  
### <a name="remarks"></a>备注  
 如果任何线程的挂起计数高于零，则不执行该线程。 线程可以继续通过调用[ResumeThread](#resumethread)成员函数。  
  
## <a name="see-also"></a>另请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWinApp 类](../../mfc/reference/cwinapp-class.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)

