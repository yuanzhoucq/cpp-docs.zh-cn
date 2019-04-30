---
title: 异常:释放异常中的对象
ms.date: 11/04/2016
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
ms.openlocfilehash: 23fe85018d1bc2c41371afec2ad6931755e4e682
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406062"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>异常:释放异常中的对象

本文介绍需要和发生异常时释放的对象的方法。 包括以下主题：

- [在本地处理异常](#_core_handling_the_exception_locally)

- [销毁对象后引发异常](#_core_throwing_exceptions_after_destroying_objects)

由框架或由你的应用程序中断正常程序流引发的异常。 因此，它是非常重要，以便可以正确处理了它们，将引发异常的情况下保持密切跟踪对象。

有两种主要方法来执行此操作。

- 处理异常使用本地**尝试**并**捕获**关键字，然后用一条语句的对象全部破坏。

- 中的任何对象销毁**捕获**块之前引发的异常用于进一步处理块外。

这两种方法如下所示为下面的示例有问题的解决方案：

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

编写更高版本，如`myPerson`如果通过引发异常后，不会删除`SomeFunc`。 执行直接跳至下一个外部异常处理程序，跳过正常函数退出和删除对象的代码。 对象的指针超出范围，使该函数，并将永远不会恢复对象占用的内存，只要在程序运行时。 这是内存泄漏;它会使用内存诊断检测到。

##  <a name="_core_handling_the_exception_locally"></a> 在本地处理异常

**Try/catch**模式提供的防御性编程方法来避免内存泄漏，同时确保发生异常时销毁对象。 例如，在本文前面所示的示例重写，如下所示：

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

此新的示例设置了一个异常处理程序以捕获异常和本地处理。 然后正常退出该函数，并销毁该对象。 此示例中的重要方面是用于捕获该异常的上下文会建立与**try/catch**块。 本地异常框架的情况下该函数将永远无法了解异常已引发了异常，并且不会正常退出，销毁该对象的机会。

##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> 销毁对象后引发异常

若要处理的异常的另一种方法是将它们传递到下一步的外部异常处理上下文。 在你**捕获**块中，可以执行一些清理在本地分配的对象，然后进行进一步的处理引发异常。

引发函数可能会或可能不需要解除分配的堆对象。 如果函数始终在正常情况下返回之前释放堆对象，然后该函数应还解除分配的堆对象引发异常之前。 另一方面，如果函数不正常情况下释放该对象在正常情况下返回之前，然后您必须决定通过情况是否应释放堆对象。

下面的示例演示如何在本地分配的对象，可清除：

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

异常机制自动释放帧对象;也称为帧对象的析构函数。

如果调用可能会引发异常的函数时，可以使用**try/catch**块以确保捕获的异常，并有机会破坏你创建的任何对象。 具体而言，请注意，许多 MFC 函数可以引发异常。

有关详细信息，请参阅[异常：捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
