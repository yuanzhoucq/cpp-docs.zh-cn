---
title: 异常:对异常宏的修改版本 3.0 中的更改
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: fb51ad91e001f0ed153bf4fdb5aa598ab5ba5042
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291218"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>异常:对异常宏的修改版本 3.0 中的更改

这是一个高级的主题。

在 MFC 3.0 版及更高版本中，已更改的异常处理宏以使用 c + + 异常。 本文介绍这些更改如何影响使用宏的现有代码的行为。

本文介绍了以下主题：

- [异常类型和 CATCH 宏](#_core_exception_types_and_the_catch_macro)

- [重新引发异常](#_core_re.2d.throwing_exceptions)

##  <a name="_core_exception_types_and_the_catch_macro"></a> 异常类型和 CATCH 宏

在早期版本的 MFC 中，**捕获**宏使用 MFC 运行时类型信息以确定异常的类型; 异常的类型确定，换而言之，在 catch 站点。 使用 c + + 异常，但是，异常的类型是始终在确定的引发站点由引发的异常对象类型。 这将导致不兼容性的情况很少而引发的对象的指针的类型不同于引发的对象的类型。

下面的示例演示了 MFC 3.0 版及更早版本之间的这种差异的结果：

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

此代码在版本 3.0 上行为不同，因为始终将控制传递给第一个**捕获**具有匹配的异常声明块。 Throw 表达式的结果

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

作为引发`CException*`，即使它被构造为`CCustomException`。 **捕获**MFC 版本 2.5 和早期版本使用中的宏`CObject::IsKindOf`来测试在运行时类型。 因为表达式

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

为 true，第一个 catch 块捕获异常。 在版本 3.0 中，使用 c + + 异常来实现许多异常处理宏，第二个 catch 块匹配引发`CException`。

此类代码并不常见。 它通常会显示在异常对象传递给另一个函数接受泛型`CException*`、 执行"预 throw"处理，并最后引发异常。

若要解决此问题，将从该函数的引发表达式移动到调用代码，并引发异常时生成异常编译器已知的实际类型。

##  <a name="_core_re.2d.throwing_exceptions"></a> 重新引发异常

Catch 块不能引发它捕获到的异常相同的指针。

此代码，如在上一版本中，有效，但将具有版本 3.0 的意外的结果：

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

使用**引发**catch 块会导致该指针`e`要删除，以便在外部 catch 站点将接收了无效的指针。 使用**THROW_LAST**以重新引发`e`。

有关详细信息，请参阅[异常：捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
