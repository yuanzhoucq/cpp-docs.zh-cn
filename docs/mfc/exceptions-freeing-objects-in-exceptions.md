---
title: "异常： 释放异常中的对象 |Microsoft 文档"
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
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a422347e319fabbd91f20e0ebf7897865f1ca4c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>异常：释放异常中的对象
此文章介绍了需要和发生异常时释放的对象的方法。 包括以下主题：  
  
-   [在本地处理异常](#_core_handling_the_exception_locally)  
  
-   [销毁对象后引发异常](#_core_throwing_exceptions_after_destroying_objects)  
  
 由框架或你的应用程序中断正常程序流引发的异常。 因此，它是非常重要，以跟踪关闭的对象，以便在引发异常的情况下正确释放它们。  
  
 有两种主要方法来执行此操作。  
  
-   本地使用处理异常**重**和**捕获**关键字，然后销毁用一条语句的所有对象。  
  
-   销毁中的任何对象**捕获**之前引发的异常用于进一步处理块外部的块。  
  
 下面的示例有问题的解决方案作为下面说明了这两种方法：  
  
 [!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]  
  
 与，上面所写`myPerson`如果通过引发异常后，不会删除`SomeFunc`。 执行直接跳至下一个外部异常处理程序，绕过普通函数退出并删除该对象的代码。 对象的指针超出范围时使函数，并且将永远不会恢复对象占用的内存，只要在程序运行。 这是内存泄漏;它将通过使用内存诊断检测到。  
  
##  <a name="_core_handling_the_exception_locally"></a>在本地处理异常  
 **Try/catch**范例提供了用于避免出现内存泄漏，并确保你的对象将销毁发生异常时的防御性编程方法。 例如，在本文前面所示的示例可重写，如下所示：  
  
 [!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]  
  
 这个新示例设置了捕获异常和本地处理的异常处理程序。 然后，它将正常退出该函数，销毁对象。 此示例的重要方面是上下文来捕获该异常会建立与**try/catch**块。 没有本地帧，该函数将永远不会知道异常已引发了异常，并且不会有机会正常退出并销毁对象。  
  
##  <a name="_core_throwing_exceptions_after_destroying_objects"></a>销毁对象后引发异常  
 若要处理的异常的另一种方法是将它们传递到下一个外部异常处理上下文。 在你**捕获**块中，可以执行一些清理你本地分配的对象的操作，然后引发异常，以做进一步处理。  
  
 引发函数可能或可能不需要释放堆对象。 如果该函数始终释放堆对象在正常情况下，返回之前然后函数还应在引发异常之前释放堆对象。 另一方面，如果该函数不通常不解除分配对象在正常情况下返回之前，然后你必须决定通过情况是否应释放堆对象。  
  
 下面的示例演示如何本地分配的对象，可清除：  
  
 [!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]  
  
 异常机制自动释放帧对象;也称为框架对象的析构函数。  
  
 如果调用函数可能引发异常时，你可以使用**try/catch**块以确保你捕获的异常，并有机会破坏你创建的任何对象。 具体而言，请注意，很多 MFC 函数可能引发异常。  
  
 有关详细信息，请参阅[异常： 捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)

