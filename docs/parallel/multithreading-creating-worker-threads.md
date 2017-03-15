---
title: "多线程处理：创建辅助线程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "背景任务 [C++]"
  - "多线程处理 [C++], 辅助线程"
  - "线程处理 [C++], 创建线程"
  - "线程处理 [C++], 无需用户输入"
  - "线程处理 [C++], 辅助线程"
  - "线程处理 [MFC], 辅助线程"
  - "辅助线程 [C++]"
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 多线程处理：创建辅助线程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

辅助线程通常用于处理后台任务，用户不必等待即可继续使用应用程序。  重新计算和后台打印等任务是很好的辅助线程示例。  本主题详细介绍创建辅助线程所需的步骤。  主题包括：  
  
-   [启动线程](#_core_starting_the_thread)  
  
-   [实现控制函数](#_core_implementing_the_controlling_function)  
  
-   [示例](#_core_controlling_function_example)  
  
 创建辅助线程是一个相对较为简单的任务。  只需两步即可以使线程运行：实现控制函数和启动线程。  不必从 [CWinThread](../mfc/reference/cwinthread-class.md) 派生类。  如果需要特殊版本的 `CWinThread`，可以从该类派生，但大多数简单辅助线程都不需要这样做。  无需修改即可使用 `CWinThread`。  
  
##  <a name="_core_starting_the_thread"></a> 启动线程  
 `AfxBeginThread` 有两个重载版本：一个只能创建辅助线程，另一个既可创建用户界面线程也可创建辅助线程。  若要使用第一个重载开始执行辅助线程，请调用 [AfxBeginThread](../Topic/AfxBeginThread.md)，并提供下列信息：  
  
-   控制函数的地址。  
  
-   要传递到控制函数的参数。  
  
-   （可选）所需的线程优先级。  默认值为正常优先级。  有关可用的优先级级别的更多信息，请参见 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的 [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)。  
  
-   （可选）所需的线程堆栈大小。  默认值与创建线程的堆栈大小相同。  
  
-   （可选）**CREATE\_SUSPENDED**，如果希望在挂起状态中创建线程。  默认值为 0，即正常启动线程。  
  
-   （可选）所需的安全特性。  默认值与父线程具有相同的访问权。  有关此安全信息格式的更多信息，请参见 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的 [SECURITY\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)。  
  
 `AfxBeginThread` 为您创建和初始化 `CWinThread` 对象、启动该对象并返回其地址，以便以后引用。  在整个过程中进行检查，确保假如创建过程的任何部分出现故障，所有对象都能被正确地解除分配。  
  
##  <a name="_core_implementing_the_controlling_function"></a> 实现控制函数  
 控制函数定义线程。  输入此函数后线程开始，此函数退出时线程终止。  此函数的原型应为：  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
 该参数为单个值。  函数在此参数中接收的值是在创建线程对象时传递到构造函数的值。  控制函数可以用其选择的任何方式解释此值。  它可以视为标量值，或指向包含多个参数的结构的指针，也可以忽略。  如果参数引用结构，则既可以使用该结构将数据从调用方传递到线程，也可以用该结构将数据从线程传递回调用方。  如果使用此类结构将数据传递回调用方，结果准备就绪时，线程需要通知调用方。  有关从辅助线程到调用方进行通信的信息，请参见[多线程处理：编程提示](../parallel/multithreading-programming-tips.md)。  
  
 函数终止后，应该返回指示终止原因的 **UINT** 值。  一般情况下，此退出代码为 0 指示成功；若为其他值，则指示不同类型的错误。  这只依赖于实现。  某些线程可以维护对象的使用计数，并返回该对象的当前使用数。  有关应用程序如何检索此值的信息，请参见[多线程处理：终止线程](../parallel/multithreading-terminating-threads.md)。  
  
 在用 MFC 库编写的多线程程序中有一些操作限制。  有关这些限制的说明以及使用线程的其他提示，请参见[多线程处理：编程提示](../parallel/multithreading-programming-tips.md)。  
  
##  <a name="_core_controlling_function_example"></a> 控制函数示例  
 下面的示例演示如何定义控制函数，以及如何从程序的其他部分使用此函数。  
  
```  
UINT MyThreadProc( LPVOID pParam )  
{  
    CMyObject* pObject = (CMyObject*)pParam;  
  
    if (pObject == NULL ||  
        !pObject->IsKindOf(RUNTIME_CLASS(CMyObject)))  
    return 1;   // if pObject is not valid  
  
    // do something with 'pObject'  
  
    return 0;   // thread completed successfully  
}  
  
// inside a different function in the program  
.  
.  
.  
pNewObject = new CMyObject;  
AfxBeginThread(MyThreadProc, pNewObject);  
.  
.  
.  
```  
  
## 您想进一步了解什么？  
  
-   [多线程处理：创建用户界面线程](../parallel/multithreading-creating-user-interface-threads.md)  
  
## 请参阅  
 [使用 C\+\+ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)