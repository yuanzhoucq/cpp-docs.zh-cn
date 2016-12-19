---
title: "异常：释放异常中的对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "销毁对象"
  - "异常处理, 销毁对象"
  - "释放对象"
  - "本地异常处理"
  - "内存泄漏, 由异常导致"
  - "引发异常, 销毁后"
  - "引发异常, 释放异常中的对象"
  - "try-catch 异常处理, 销毁对象"
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常：释放异常中的对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在异常发生后，本文说明需求和释放对象方法。  主题包括：  
  
-   [本地异常处理](#_core_handling_the_exception_locally)  
  
-   [在销毁对象后引发的异常。](#_core_throwing_exceptions_after_destroying_objects)  
  
 应用程序由框架引发的异常中断或正常程序流。  因此，对象将靠近的跟踪非常重要，引发异常时这样才能在适当处理它们，。  
  
 可通过两种基本方法实现此目的。  
  
-   使用关键字 **try** 和 **catch**，本地处理异常，然后销毁一语句中的所有对象。  
  
-   在引发在块外部的异常之前销毁在 **catch** 块的所有对象进行进一步处理。  
  
 这两个方法如下说明作为到下面有问题的示例解决方案：  
  
 [!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/CPP/exceptions-freeing-objects-in-exceptions_1.cpp)]  
  
 如果异常是由引发 `SomeFunc`，所编写上面，`myPerson` 不会被删除。  执行直接跳转到下外部异常处理程序，而绕过功能正常退出和删除对象的代码。  只要程序运行，对象的指针到超出范围异常，则退出函数时，并且对象占用的内存将无法恢复。  这是内存泄漏；使用内存诊断会检测它。  
  
##  <a name="_core_handling_the_exception_locally"></a> 本地异常处理  
 当异常确实发生时，**try\/catch** 示例为避免内存泄漏和确保提供一个防护层编程方法销毁对象。  例如，本文前面给出的示例可能重写为：  
  
 [!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/CPP/exceptions-freeing-objects-in-exceptions_2.cpp)]  
  
 此新范例的设置异常处理程序捕获该异常并将其处理本地。  通常然后退出函数并销毁对象。  此示例捕捉重要方面是异常的上下文建立用 **try\/catch** 块。  如果没有本地异常帧，函数不知道已引发异常而不会有机会通常退出和销毁对象。  
  
##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> 在销毁对象后引发的异常。  
 另一个方式处理异常将它们传递到下外部处理异常的上下文。  在 **catch** 块，可执行部分配对象的某些清理然后引发异常的进一步处理。  
  
 引发的函数也可能无需释放堆对象。  如果函数在返回之前始终释放堆对象的情况，则函数应在引发异常之前还释放堆对象。  另一方面，如果不在，函数返回之前释放对象的行为通常情况，您必须决定基于特定条件应释放堆对象。  
  
 下面的示例演示如何清除本地分配的对象中：  
  
 [!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/CPP/exceptions-freeing-objects-in-exceptions_3.cpp)]  
  
 异常机制自动释放帧对象；帧对象的析构函数被调用。  
  
 如果调用可能引发异常的函数，就可以使用 **try\/catch** 块，以捕捉异常并有可能您销毁创建的所有对象。  具体而言，请注意很多 MFC 函数可能会引发异常。  
  
 有关更多信息，请参见 [异常：捕获和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)