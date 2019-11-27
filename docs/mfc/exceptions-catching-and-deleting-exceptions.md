---
title: 异常：捕捉和删除异常
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 0142ffddfb391ae8da878d9e5fe34629cf16cb52
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246694"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>异常：捕捉和删除异常

下列说明和示例演示如何捕获和删除异常。 有关**try**、 **catch**和**throw**关键字的详细信息，请参阅[异常和C++错误处理的新式最佳实践](../cpp/errors-and-exception-handling-modern-cpp.md)。

你的异常处理程序必须删除其处理的异常对象，因为如果未删除异常将导致在代码捕获异常时出现内存泄漏。

在以下情况时， **catch**块必须删除异常：

- **Catch**块引发一个新的异常。

   当然，如果您再次引发同一异常，则不得删除此异常：

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- 执行从**catch**块中返回。

> [!NOTE]
>  删除 `CException`时，请使用 `Delete` 成员函数删除该异常。 不要使用**delete**关键字，因为如果异常不在堆上，则它可能会失败。

#### <a name="to-catch-and-delete-exceptions"></a>捕获和删除异常

1. 使用**try**关键字设置**try**块。 执行可能会在**try**块中引发异常的任何程序语句。

   使用**catch**关键字设置**catch**块。 在**catch**块中放置异常处理代码。 仅当**try**块中的代码引发**catch**语句中指定的类型的异常时，才会执行**catch**块中的代码。

   以下框架显示了**try**和**catch**块的正常排列方式：

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   当引发异常时，控制将传递到其异常声明与异常类型匹配的第一个**catch**块。 可以有选择地处理顺序**catch**块不同类型的异常，如下所示：

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

有关详细信息，请参阅[异常：从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)。

## <a name="see-also"></a>另请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
