---
title: "CWinThread Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinThread 类"
  - "线程处理 [MFC], 创建线程"
  - "线程处理 [MFC], 安全"
  - "辅助线程"
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CWinThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示应用程序中的执行线程。  
  
## 语法  
  
```  
class CWinThread : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWinThread::CWinThread](../Topic/CWinThread::CWinThread.md)|构造 `CWinThread` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWinThread::CreateThread](../Topic/CWinThread::CreateThread.md)|开始 `CWinThread` 对象的执行。|  
|[CWinThread::ExitInstance](../Topic/CWinThread::ExitInstance.md)|清理的重写，当您的线程终止。|  
|[CWinThread::GetMainWnd](../Topic/CWinThread::GetMainWnd.md)|检索指向线程的主窗口。|  
|[CWinThread::GetThreadPriority](../Topic/CWinThread::GetThreadPriority.md)|获取当前线程的优先级。|  
|[CWinThread::InitInstance](../Topic/CWinThread::InitInstance.md)|执行线程实例初始化的重写。|  
|[CWinThread::IsIdleMessage](../Topic/CWinThread::IsIdleMessage.md)|具体信息的检查。|  
|[CWinThread::OnIdle](../Topic/CWinThread::OnIdle.md)|执行线程特定的空闲时间处理的重写。|  
|[CWinThread::PostThreadMessage](../Topic/CWinThread::PostThreadMessage.md)|将消息发送到另一 `CWinThread` 对象。|  
|[CWinThread::PreTranslateMessage](../Topic/CWinThread::PreTranslateMessage.md)|筛选器消息，并在调度到Windows之前函数 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。|  
|[CWinThread::ProcessMessageFilter](../Topic/CWinThread::ProcessMessageFilter.md)|截获某些消息，然后在到达应用程序。|  
|[CWinThread::ProcessWndProcException](../Topic/CWinThread::ProcessWndProcException.md)|截获线程的消息和命令处理程序引发的异常。|  
|[CWinThread::PumpMessage](../Topic/CWinThread::PumpMessage.md)|包含线程的消息循环。|  
|[CWinThread::ResumeThread](../Topic/CWinThread::ResumeThread.md)|递减线程的挂起计数。|  
|[CWinThread::Run](../Topic/CWinThread::Run.md)|控制线程的函数与消息泵。  自定义默认消息循环的重写。|  
|[CWinThread::SetThreadPriority](../Topic/CWinThread::SetThreadPriority.md)|设置当前线程的优先级。|  
|[CWinThread::SuspendThread](../Topic/CWinThread::SuspendThread.md)|增加线程的挂起计数。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CWinThread::operator HANDLE](../Topic/CWinThread::operator%20HANDLE.md)|检索 `CWinThread` 对象的句柄。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CWinThread::m\_bAutoDelete](../Topic/CWinThread::m_bAutoDelete.md)|指定是否销毁对象在线程终止。|  
|[CWinThread::m\_hThread](../Topic/CWinThread::m_hThread.md)|向当前线程的句柄。|  
|[CWinThread::m\_nThreadID](../Topic/CWinThread::m_nThreadID.md)|当前线程的ID。|  
|[CWinThread::m\_pActiveWnd](../Topic/CWinThread::m_pActiveWnd.md)|指向容器应用程序的主窗口，当OLE服务器处于就地活动状态。|  
|[CWinThread::m\_pMainWnd](../Topic/CWinThread::m_pMainWnd.md)|持有一个指针到应用程序的主窗口。|  
  
## 备注  
 从 `CWinApp`派生的对象通常提供主执行线程; `CWinApp` 从 `CWinThread`派生。  附加 `CWinThread` 对象允许在特定应用程序中的多个线程。  
  
 具有 `CWinThread` 支持线程的两种泛型类型:辅助线程和用户界面线程。  辅助线程没有消息泵:例如，在电子表格应用程序执行后台计算的线程。  用户界面线程具有一个消息泵和处理来自系统收到的消息。  从并选件类派生的[CWinApp](../../mfc/reference/cwinapp-class.md) 是用户界面线程的示例。  其他用户界面线程可以直接从 `CWinThread`还派生。  
  
 选件类 `CWinThread` Objects提供有关线程的持续时间通常存在。  如果希望修改此行为，请设置 [m\_bAutoDelete](../Topic/CWinThread::m_bAutoDelete.md) 到 **FALSE**。  
  
 `CWinThread` 选件类需要使您的线程完全安全代码和MFC。  框架使用的线程本地数据维护线程特定信息由 `CWinThread` 对象管理。  这样的所有线程必须由MFC创建与 `CWinThread` 的依赖项来处理线程本地数据，请使用MFC。  例如，运行时功能创建的线程 [\_beginthread，\_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) 不能使用任何MFC API。  
  
 若要创建线程，请调用 [AfxBeginThread](../Topic/AfxBeginThread.md)。  有两种形式，具体取决于您是否需要辅助或用户界面线程。  如果您希望用户界面线程，请传递给 `AfxBeginThread` 指向您的 `CWinThread``CRuntimeClass` 派生类。  如果要创建辅助线程，请传递给 `AfxBeginThread` 指针控件功能以及该参数为控件功能。  对于辅助线程和用户界面线程，可以指定修改优先级别、堆栈大小、创建标志和安全特性可选参数。  `AfxBeginThread` 将返回指向您的新 `CWinThread` 对象。  
  
 而不是调用 `AfxBeginThread`，可构造 `CWinThread`派生的对象并调用 `CreateThread`。  如果您要重用在线程上执行的连续创建和停止而不同，`CWinThread` 对象此两阶段构造方法很有用。  
  
 有关 `CWinThread`的更多信息，请参见位于 [用C\+\+和MFC的多线程](../../parallel/multithreading-with-cpp-and-mfc.md)、 [多线程处理:创建用户界面线程](../../parallel/multithreading-creating-user-interface-threads.md)、 [多线程处理:创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)和 [多线程处理:如何使用同步类选件](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)