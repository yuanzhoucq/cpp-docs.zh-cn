---
title: 异常：3.0 版本中对异常宏的修改
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 82320b0c7ccd6766e016f0437633339f8f8f61d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365496"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>异常：3.0 版本中对异常宏的修改

这是一个高级主题。

在 MFC 版本 3.0 及更高版本中，异常处理宏已更改为使用C++异常。 本文介绍这些更改如何影响使用宏的现有代码的行为。

本文涵盖以下主题：

- [异常类型和 CATCH 宏](#_core_exception_types_and_the_catch_macro)

- [重新引发异常](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>异常类型和 CATCH 宏

在早期版本的 MFC 中 **，CATCH**宏使用 MFC 运行时类型信息来确定异常的类型;异常的类型在捕获站点确定，换句话说。 但是，对于C++异常，异常的类型始终由引发的异常对象的类型在引发站点中确定。 在极少数情况下，指向引发对象的指针类型与引发对象的类型不同，这将导致不兼容。

下面的示例说明了 MFC 版本 3.0 和早期版本之间的这种差异的后果：

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

此代码在版本 3.0 中的行为不同，因为控件始终通过匹配的异常声明传递到第一个**catch**块。 引发表达式的结果

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

被抛出为`CException*`，即使它构造为 。 `CCustomException` MFC 版本 2.5 和更早版本的`CObject::IsKindOf`**CATCH**宏用于在运行时测试类型。 因为表达式

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

为 true，第一个 catch 块捕获异常。 在版本 3.0 中，使用C++个异常来实现许多异常处理宏，第二个 catch 块与引发`CException`的操作匹配 。

像这样的代码并不常见。 当异常对象传递给接受泛型`CException*`的另一个函数，执行"预引发"处理，最后引发异常时，通常会出现异常。

要解决此问题，请将 throw 表达式从函数移动到调用代码，并引发编译器在生成异常时已知的实际类型的异常。

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>重新引发异常

catch 块无法引发捕获的异常指针。

例如，此代码在以前的版本中有效，但在版本 3.0 中会有意外的结果：

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

在 catch 块中使用**THROW** `e`会导致删除指针，以便外部捕获站点将接收无效的指针。 使用**THROW_LAST**重新引发`e`。

有关详细信息，请参阅[异常：捕获和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
