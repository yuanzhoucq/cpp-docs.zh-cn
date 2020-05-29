---
title: 异常：释放异常中的对象
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
ms.openlocfilehash: 49c7c6b0481f90baa23609c1bb1596deda49f7bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371990"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>异常：释放异常中的对象

本文介绍了发生异常时释放对象的需要和方法。 主题包括：

- [在本地处理异常](#_core_handling_the_exception_locally)

- [销毁对象后引发异常](#_core_throwing_exceptions_after_destroying_objects)

框架或应用程序引发的异常会中断正常程序流。 因此，密切跟踪对象非常重要，这样在引发异常时可以正确释放它们。

有两种主要方法可以执行此操作。

- 使用**try**和**catch**关键字在本地处理异常，然后使用一个语句销毁所有对象。

- 在将异常扔到块外部以便进一步处理之前，销毁**catch**块中的任何对象。

下面将这两种方法作为以下问题示例的解决方案进行说明：

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

如上所述，如果由`myPerson``SomeFunc`引发异常，将不会删除。 执行直接跳转到下一个外部异常处理程序，绕过正常的函数退出和删除对象的代码。 当异常离开函数时，指向对象的指针将超出范围，只要程序正在运行，对象占用的内存就永远不会恢复。 这是内存泄漏;将使用内存诊断检测到它。

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>本地处理异常

**try/catch**范例提供了一种防御性编程方法，用于避免内存泄漏，并确保对象在发生异常时被销毁。 例如，本文前面显示的示例可以重写如下：

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

此新示例设置一个异常处理程序来捕获异常并在本地处理它。 然后，它正常退出函数并销毁对象。 此示例的重要方面是，使用**try/catch**块建立了捕获异常的上下文。 如果没有本地异常帧，函数永远不会知道已引发异常，并且没有机会正常退出并销毁对象。

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>销毁对象后引发异常

处理异常的另一种方法是将它们传递到下一个外部异常处理上下文。 在**catch**块中，可以对本地分配的对象进行一些清理，然后引发异常以进行进一步处理。

引发函数可能需要或不需要取消分配堆对象。 如果函数总是在在正常情况下返回之前解分配堆对象，则函数还应在引发异常之前取消分配堆对象。 另一方面，如果函数在正常情况下返回之前通常不重新分配对象，则必须根据情况决定是否应处理堆对象。

下面的示例演示如何清理本地分配的对象：

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

异常机制自动取消分配帧对象;帧对象的析构函数也称为。

如果调用可以引发异常的函数，则可以使用**try/catch**块来确保捕获异常并有机会销毁已创建的任何对象。 特别是，请注意，许多 MFC 函数可能会引发异常。

有关详细信息，请参阅[异常：捕获和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
