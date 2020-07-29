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
ms.openlocfilehash: a02b71609ec19d6106153bf67e9d56b860cfdfff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217930"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>异常：释放异常中的对象

本文说明了在发生异常的情况下的需要和释放对象的方法。 主题包括：

- [在本地处理异常](#_core_handling_the_exception_locally)

- [销毁对象后引发异常](#_core_throwing_exceptions_after_destroying_objects)

框架引发的异常或应用程序中断正常程序流。 因此，始终跟踪对象非常重要，这样就可以在引发异常的情况下正确释放对象。

可以通过两种主要方法完成此操作。

- 使用和关键字在本地处理异常 **`try`** **`catch`** ，然后销毁包含一条语句的所有对象。

- 销毁块外的任何对象 **`catch`** ，然后在块外引发异常，以便进一步处理。

下面这两种方法的示例如下所示：

[!code-cpp[NVC_MFCExceptions#14](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

如上所述， `myPerson` 如果引发异常，则不会将其删除 `SomeFunc` 。 执行会直接跳转到下一个外部异常处理程序，绕过常规函数退出和删除该对象的代码。 当异常离开函数时，指向对象的指针将超出范围，并且只要程序正在运行，就永远不会恢复对象占用的内存。 这是内存泄漏;它将通过使用内存诊断来检测。

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>在本地处理异常

**Try/catch**模式提供了一种防御性编程方法，可避免内存泄漏，并确保对象在发生异常时被销毁。 例如，本文前面所示的示例可以重写，如下所示：

[!code-cpp[NVC_MFCExceptions#15](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

此新示例将设置一个异常处理程序来捕获异常并在本地处理它。 然后，它会正常退出函数并销毁对象。 此示例的一个重要方面是，使用**try/catch**块建立捕获异常的上下文。 如果没有本地异常框架，函数将永远不会知道已引发异常，并且不会有机会正常退出并销毁对象。

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>销毁对象后引发异常

处理异常的另一种方法是将其传递到下一个外部异常处理上下文。 在 **`catch`** 块中，你可以对本地分配的对象执行一些清理，然后在上引发异常以便进一步处理。

引发函数可能需要也可能不需要释放堆对象。 如果函数在正常情况下返回之前始终释放堆对象，则该函数还应在引发异常之前释放堆对象。 另一方面，如果在正常情况下，该函数通常不会解除分配对象，则必须根据具体情况决定是否应释放堆对象。

下面的示例演示如何清除本地分配的对象：

[!code-cpp[NVC_MFCExceptions#16](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

异常机制自动释放框架对象;还将调用 frame 对象的析构函数。

如果调用可能引发异常的函数，则可以使用**try/catch**块来确保捕获异常，并有可能销毁已创建的任何对象。 特别要注意的是，许多 MFC 函数可能会引发异常。

有关详细信息，请参阅[异常：捕获和删除异常](exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另请参阅

[异常处理](exception-handling-in-mfc.md)
