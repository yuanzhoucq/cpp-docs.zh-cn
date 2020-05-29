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
ms.openlocfilehash: afad5335bedf001329ecb401a8a16c663afb5571
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371593"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>异常：使用 MFC 宏和 C++ 异常

本文讨论了编写同时使用 MFC 异常处理宏和C++异常处理关键字的代码的注意事项。

本文涵盖以下主题：

- [混合异常关键字和宏](#_core_mixing_exception_keywords_and_macros)

- [尝试 catch 块内的块](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>混合异常关键字和宏

您可以在同一程序中混合 MFC 异常宏和C++异常关键字。 但是，您不能将 MFC 宏与同一块中的C++异常关键字混合在一起，因为宏在异常对象超出范围时会自动删除它们，而使用异常处理关键字的代码则不删除它们。 有关详细信息，请参阅文章["例外：捕获和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)"。

宏和关键字之间的主要区别是，宏"自动"删除捕获的异常，当异常超出范围时。 使用关键字的代码不;必须显式删除捕获块中捕获的异常。 混合宏和C++异常关键字可能会导致未删除异常对象时内存泄漏，或者在异常删除两次时导致堆损坏。

例如，以下代码使异常指针无效：

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

出现此问题的原因是`e`在执行从"内部 **"CATCH**块中传递时被删除。 使用**THROW_LAST**宏而不是**THROW**语句将导致"外部 **"CATCH**块接收有效的指针：

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>尝试 Catch 块内的块

不能从**CATCH**块内**的尝试**块中重新引发当前异常。 以下示例无效：

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

有关详细信息，请参阅[异常：检查异常内容](../mfc/exceptions-examining-exception-contents.md)。

## <a name="see-also"></a>另请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
