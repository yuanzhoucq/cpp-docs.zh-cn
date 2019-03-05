---
title: 异常:使用 MFC 宏和 c + + 异常
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
ms.openlocfilehash: 00e88ddabf3a8e8b591bebae7ebc8ced0e1dc637
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297705"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>异常:使用 MFC 宏和 c + + 异常

本文讨论有关编写使用 MFC 异常处理宏和 c + + 异常处理关键字的代码的注意事项。

本文介绍了以下主题：

- [混合使用异常关键字和宏](#_core_mixing_exception_keywords_and_macros)

- [请尝试在 catch 块中的块](#_core_try_blocks_inside_catch_blocks)

##  <a name="_core_mixing_exception_keywords_and_macros"></a> 混合使用异常关键字和宏

可以混合使用 MFC 异常宏和 c + + 异常关键字在同一程序中。 但不能与同一个块中的 c + + 异常关键字混合 MFC 宏，因为宏异常对象时自动删除它们超出范围，而不使用异常处理关键字的代码。 有关详细信息，请参阅文章[异常：捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

宏和关键字之间的主要区别是当异常超出范围时，宏将"自动"删除捕获的异常。 使用关键字的代码却不;必须显式删除的 catch 块中捕获的异常。 混合使用宏和 c + + 异常关键字可以导致内存泄漏时未删除异常对象，或堆损坏时两次删除异常。

例如，将以下代码，使失效异常指针：

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

出现问题的原因`e`时执行将跳出"内部"，删除**捕获**块。 使用**THROW_LAST**而不是宏**引发**语句将导致"外部"**捕获**块接收的有效指针：

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

##  <a name="_core_try_blocks_inside_catch_blocks"></a> 请尝试在 Catch 块中的块

不能重新中引发当前异常**尝试**内的块**捕获**块。 下面的示例为无效名称：

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

有关详细信息，请参阅[异常：检查异常内容](../mfc/exceptions-examining-exception-contents.md)。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
