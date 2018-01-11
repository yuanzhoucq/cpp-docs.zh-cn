---
title: "多线程处理： 创建用户界面线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 105685e0db4689978ef1e6f8615bb5e5f8acdd43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-creating-user-interface-threads"></a>多线程处理：创建用户界面线程
用户界面线程通常用于处理用户输入并响应用户事件行为独立于线程执行其他部分的应用程序。 主应用程序线程 (中提供你`CWinApp`-派生类) 已经创建并启动。 本主题介绍创建其他用户界面线程所需的步骤。  
  
 创建用户界面线程时必须执行的第一件事是从派生类[CWinThread](../mfc/reference/cwinthread-class.md)。 必须声明并实现此类，使用[DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)和[IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate)宏。 此类必须重写某些函数，并且可重写其他人。 下表中显示这些函数以及应做些什么。  
  
### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>要创建用户界面线程时覆盖函数  
  
|函数|目标|  
|--------------|-------------|  

|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|当线程终止时，请执行清理操作。 通常中重写。 |  
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|执行线程实例初始化。 必须重写。 |  
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|执行特定于线程的空闲时间处理。 通常不重写。 |  
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|筛选消息之前被发送到**TranslateMessage**和**DispatchMessage**。 通常不重写。 |  
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|截获由线程的消息和命令处理程序引发的未经处理的异常。 通常不重写。 |  
|[运行](../mfc/reference/cwinthread-class.md#run)|控制线程的函数。 包含消息泵。 一般不重写。 |  

  
 MFC 通过参数重载提供两个版本的 `AfxBeginThread`：一个只能创建辅助线程，另一个既可创建用户界面线程也可创建辅助线程。 若要启动你的用户界面线程，调用的第二个重载[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，提供以下信息：  
  
-   [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)类派生自的`CWinThread`。  
  
-   （可选）所需的优先级。 默认值为普通优先级。 有关可用的优先级级别的详细信息，请参阅[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
-   （可选）线程所需的堆栈大小。 默认值为相同大小堆栈上为创建的线程。  
  
-   （可选）**CREATE_SUSPENDED**如果你想要在挂起状态中创建的线程。 默认值为 0，或正常启动线程。  
  
-   （可选）中的所需的安全特性。 默认值为与父线程一样进行访问。 此安全信息的格式的详细信息，请参阅[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
 `AfxBeginThread`为你进行的大部分工作。 它将创建您的类的新对象，使用你提供的信息并调用其进行初始化[CWinThread::CreateThread](../mfc/reference/cwinthread-class.md#createthread)开始执行线程。 在整个过程进行检查以确保所有对象都都释放正确应创建的任何部分出现故障。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [多线程处理：终止线程](../parallel/multithreading-terminating-threads.md)  
  
-   [多线程处理：创建辅助线程](../parallel/multithreading-creating-worker-threads.md)  
  
-   [进程和线程](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
## <a name="see-also"></a>请参阅  
 [使用 C++ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)