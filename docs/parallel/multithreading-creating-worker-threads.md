---
title: "多线程处理： 创建辅助线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94a047de82bebb03f681e1bfdf6f68d56554fe8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-creating-worker-threads"></a>多线程处理：创建辅助线程
工作线程通常用于处理用户不必等待就可以继续使用你的应用程序的后台任务。 任务 （如重新计算和后台打印) 的工作线程很好的示例。 本主题详细介绍创建工作线程所需的步骤。 包括以下主题：  
  
-   [启动线程](#_core_starting_the_thread)  
  
-   [控制函数的实现](#_core_implementing_the_controlling_function)  
  
-   [示例](#_core_controlling_function_example)  
  
 创建工作线程是相对简单的任务。 是否需要仅有两个步骤来获取你运行的线程： 控制函数的实现和启动线程。 不需要从派生类[CWinThread](../mfc/reference/cwinthread-class.md)。 如果你需要的特殊版本，则可以派生一个类`CWinThread`，但不需要对于大多数简单的工作线程。 你可以使用`CWinThread`而不进行修改。  
  
##  <a name="_core_starting_the_thread"></a>启动线程  
 有两个重载的版本`AfxBeginThread`： 一个只能创建工作线程，可以创建用户界面线程和辅助线程的另一个。 若要开始使用第一个重载在辅助线程的执行，调用[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，提供以下信息：  
  
-   控制函数的地址。  
  
-   要传递到控制函数的参数。  
  
-   （可选）所需的线程的优先级。 默认值为普通优先级。 有关可用的优先级级别的详细信息，请参阅[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
-   （可选）线程所需的堆栈大小。 默认值为相同大小堆栈上为创建的线程。  
  
-   （可选）**CREATE_SUSPENDED**如果你想要在挂起状态中创建的线程。 默认值为 0，或正常启动线程。  
  
-   （可选）中的所需的安全特性。 默认值为与父线程一样进行访问。 此安全信息的格式的详细信息，请参阅[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
 `AfxBeginThread`创建并初始化`CWinThread`为你的对象启动外接程序，并返回其地址，因此您可以参考其更高版本。 在整个过程进行检查以确保所有对象都都释放正确应创建的任何部分出现故障。  
  
##  <a name="_core_implementing_the_controlling_function"></a>控制函数的实现  
 控制函数定义线程。 输入此函数后，线程启动，并且当它退出时，线程终止。 此函数应具有以下原型：  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
 参数是单个值。 函数会收到此参数中的值是传递给构造函数创建线程对象时的值。 控制函数可以解释为它选择的任何方式中的此值。 可以被视为标量值或包含多个参数的结构的指针或可以忽略它。 如果该参数引用一个结构，不只将数据从调用方传递给线程，而且还可以将数据从线程传递到调用方可以使用结构。 如果这种结构用于将数据传递回调用方，线程将需要结果已准备就绪时通知调用方。 有关从工作线程到调用方进行通信的信息，请参阅[多线程处理： 编程提示](../parallel/multithreading-programming-tips.md)。  
  
 当函数将终止时，它应返回**UINT**值，该值指示终止的原因。 通常情况下，此退出代码为 0 以使用其他值，该值指示不同类型的错误指示成功。 这是只依赖于实现。 某些线程可能维护的对象的使用计数，并返回该对象使用的当前数目。 若要查看如何应用程序可以检索此值，请参阅[多线程处理： 终止线程](../parallel/multithreading-terminating-threads.md)。  
  
 有一些限制可以编写与 MFC 库的多线程程序中执行的操作。 有关这些限制和使用线程的其他提示的说明，请参阅[多线程处理： 编程提示](../parallel/multithreading-programming-tips.md)。  
  
##  <a name="_core_controlling_function_example"></a>控制函数的示例  
 下面的示例演示如何定义控制函数并使用它从程序的其他部分。  
  
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
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [多线程处理：创建用户界面线程](../parallel/multithreading-creating-user-interface-threads.md)  
  
## <a name="see-also"></a>请参阅  
 [使用 C++ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)