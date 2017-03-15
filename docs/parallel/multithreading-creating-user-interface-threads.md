---
title: "多线程处理：创建用户界面线程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CREATE_SUSPENDED"
  - "SECURITY_ATTRIBUTES"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "多线程处理 [C++], 用户界面线程"
  - "线程处理 [C++], 创建线程"
  - "线程处理 [C++], 用户界面线程"
  - "线程处理 [MFC], 用户界面线程"
  - "用户界面线程 [C++]"
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 多线程处理：创建用户界面线程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用户界面线程通常用于处理用户输入和响应用户事件，这些行为独立于执行该应用程序其他部分的线程。  已经创建并启动主应用程序线程（在 `CWinApp` 导出的类中提供）。  本文描述创建其他用户界面线程所需的步骤。  
  
 创建用户界面线程时，必须首先从 [CWinThread](../mfc/reference/cwinthread-class.md) 派生类。  必须使用 [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) 和 [IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md) 宏声明并实现此类。  此类必须重写某些函数，也可以重写其他函数。  下表列出了这些函数及其用途。  
  
### 创建用户界面线程时要重写的函数  
  
|功能|用途|  
|--------|--------|  
|[ExitInstance](../Topic/CWinThread::ExitInstance.md)|线程终止时执行清除。  通常重写。|  
|[InitInstance](../Topic/CWinThread::InitInstance.md)|执行线程实例初始化。  必须重写。|  
|[OnIdle](../Topic/CWinThread::OnIdle.md)|执行线程特定的闲置时间处理。  通常不重写。|  
|[PreTranslateMessage](../Topic/CWinThread::PreTranslateMessage.md)|将消息调度到 **TranslateMessage** 和 **DispatchMessage** 之前对其进行筛选。  通常不重写。|  
|[ProcessWndProcException](../Topic/CWinThread::ProcessWndProcException.md)|截获由线程的消息和命令处理程序引发的未经处理的异常。  通常不重写。|  
|[运行](../Topic/CWinThread::Run.md)|控制线程的函数。  包含消息泵。  一般不重写。|  
  
 MFC提供了`AfxBeginThread`两个参数重载版本：一个只能创建工作线程，另一个既可创建用户界面线程也可创建工作线程。  若要启动用户界面线程，请调用[AfxBeginThread](../Topic/AfxBeginThread.md)的第二个重载，提供下列信息：  
  
-   从 `CWinThread` 派生的类的 [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md)。  
  
-   （可选）所需的优先级级别。  默认值为正常优先级。  有关可用的优先级级别的更多信息，请参见 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的 [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)。  
  
-   （可选）所需的线程堆栈大小。  默认值与创建线程的堆栈大小相同。  
  
-   （可选）**CREATE\_SUSPENDED**，如果希望在挂起状态中创建线程。  默认值为 0，即正常启动线程。  
  
-   （可选）所需的安全特性。  默认值与父线程具有相同的访问权。  有关此安全信息格式的更多信息，请参见 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的 [SECURITY\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)。  
  
 `AfxBeginThread` 为您完成大部分工作。  它创建类的新对象、使用您提供的信息初始化该对象并调用 [CWinThread::CreateThread](../Topic/CWinThread::CreateThread.md) 开始执行线程。  在整个过程中进行检查，确保假如创建过程的任何部分出现故障，所有对象都能被正确地解除分配。  
  
## 您想进一步了解什么？  
  
-   [多线程处理：终止线程](../parallel/multithreading-terminating-threads.md)  
  
-   [多线程处理：创建辅助线程](../parallel/multithreading-creating-worker-threads.md)  
  
-   [\<caps:sentence id\="tgt49" sentenceid\="d446961ca833a037f83b141ec4859428" class\="tgtSentence"\>进程和线程\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
## 请参阅  
 [使用 C\+\+ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)