---
title: 异常：使用 MFC 宏和 C++ 异常
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: 9e97eb545dedd3ac38dd93471f82aecc382717ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223169"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>异常：使用 MFC 宏和 C++ 异常

本文讨论编写使用 MFC 异常处理宏和 c + + 异常处理关键字的代码的注意事项。

本文涵盖以下主题：

- [混合异常关键字和宏](#_core_mixing_exception_keywords_and_macros)

- [Catch 块内的 Try 块](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>混合异常关键字和宏

可以在同一程序中混合使用 MFC 异常宏和 c + + 异常关键字。 但不能在同一个块中将 MFC 宏与 c + + 异常关键字混合使用，因为当宏超出范围时，它们会自动删除异常对象，而使用异常处理关键字的代码则不能。 有关详细信息，请参阅文章[异常：捕获和删除异常](exceptions-catching-and-deleting-exceptions.md)。

宏和关键字之间的主要区别在于，当异常超出范围时，宏会 "自动" 删除捕获的异常。 使用关键字的代码不会;必须显式删除 catch 块中捕获的异常。 不删除异常对象时，混合宏和 c + + 异常关键字可能会导致内存泄漏，或在异常被删除两次时导致堆损坏。

例如，以下代码使异常指针失效：

[!code-cpp[NVC_MFCExceptions#10](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

之所以出现此问题， `e` 是因为在执行从 "内部" **CATCH**块中传递时删除。 使用**THROW_LAST**宏而不是**THROW**语句将导致 "外部" **CATCH**块接收有效指针：

[!code-cpp[NVC_MFCExceptions#11](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Catch 块内的 Try 块

不能从 **`try`** **CATCH**块内的块内重新引发当前异常。 下面的示例无效：

[!code-cpp[NVC_MFCExceptions#12](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

有关详细信息，请参阅异常[：检查异常内容](exceptions-examining-exception-contents.md)。

## <a name="see-also"></a>另请参阅

[异常处理](exception-handling-in-mfc.md)
