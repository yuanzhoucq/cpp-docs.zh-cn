---
title: 异常：3.0 版本中对异常宏的修改
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 72b343641b0b43d408c5820ca2a2af1de94ce327
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225054"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>异常：3.0 版本中对异常宏的修改

这是一个高级主题。

在 MFC 版本3.0 及更高版本中，异常处理宏已更改为使用 c + + 异常。 本文说明这些更改如何影响使用宏的现有代码的行为。

本文涵盖以下主题：

- [异常类型和 CATCH 宏](#_core_exception_types_and_the_catch_macro)

- [重新引发异常](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>异常类型和 CATCH 宏

在 MFC 的早期版本中， **CATCH**宏使用 mfc 运行时类型信息来确定异常的类型;在 catch 站点上确定异常的类型。 但是，对于 c + + 异常，异常的类型始终在引发站点上由引发的异常对象的类型确定。 这会导致在极少数情况下发生不兼容问题，在这种情况下，指向引发的对象的指针类型不同于引发的对象的类型。

下面的示例演示 MFC 版本3.0 和早期版本之间的这种差异的结果：

[!code-cpp[NVC_MFCExceptions#1](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

此代码在版本3.0 中的行为不同，因为控件始终传递到 **`catch`** 具有匹配的异常声明的第一个块。 Throw 表达式的结果

[!code-cpp[NVC_MFCExceptions#19](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

作为引发 `CException*` ，即使它被构造为 `CCustomException` 。 MFC 版本2.5 和更早版本中的**CATCH**宏用于 `CObject::IsKindOf` 在运行时测试类型。 因为表达式

[!code-cpp[NVC_MFCExceptions#20](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

为 true，则第一个 catch 块捕获异常。 在版本3.0 中，使用 c + + 异常来实现许多异常处理宏，第二个 catch 块匹配引发的 `CException` 。

此类代码不常见。 当异常对象传递到接受泛型的另一个函数时，通常会出现此异常 `CException*` ，执行 "预引发" 处理，最后引发异常。

若要解决此问题，请将引发表达式从函数移到调用代码，并在生成异常时引发编译器已知的实际类型的异常。

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>重新引发异常

Catch 块无法引发它所捕获的同一异常指针。

例如，在以前的版本中，此代码是有效的，但在版本3.0 中将出现意外结果：

[!code-cpp[NVC_MFCExceptions#2](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

在 catch 块中使用**THROW**会导致指针被 `e` 删除，以便外部 catch 站点将接收无效指针。 使用**THROW_LAST**重新引发 `e` 。

有关详细信息，请参阅[异常：捕获和删除异常](exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另请参阅

[异常处理](exception-handling-in-mfc.md)
