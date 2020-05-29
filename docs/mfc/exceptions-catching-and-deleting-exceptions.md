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
ms.openlocfilehash: 74022c8bc6af1d2cdf74fa452d4e0483637e542e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365520"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>异常：捕捉和删除异常

下列说明和示例演示如何捕获和删除异常。 有关**尝试**、**捕获**和**引发**关键字的详细信息，请参阅[现代C++异常和错误处理的最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)。

你的异常处理程序必须删除其处理的异常对象，因为如果未删除异常将导致在代码捕获异常时出现内存泄漏。

捕获**块**必须在以下情况删除异常：

- **catch**块将引发新的异常。

   当然，如果您再次引发同一异常，则不得删除此异常：

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- 执行从**catch**块内返回。

> [!NOTE]
> 删除 时`CException`，使用`Delete`成员函数删除异常。 不要使用**delete**关键字，因为如果异常不在堆中，则该关键字可能会失败。

#### <a name="to-catch-and-delete-exceptions"></a>捕获和删除异常

1. 使用**try**关键字设置**try**块。 执行任何可能在**try**块中引发异常的程序语句。

   使用**catch**关键字设置**catch**块。 将异常处理代码放在**catch**块中。 仅当**try**块中的代码引发**catch**语句中指定的类型的异常时，才会执行**catch**块中的代码。

   以下骨架显示了**尝试**和**捕捉**块通常如何排列：

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   引发异常时，控件将传递到其异常声明与异常类型匹配的第一**个 catch**块。 您可以有选择地处理不同类型的异常，顺序**CATCH**块如下所示：

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

有关详细信息，请参阅[异常：从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)。

## <a name="see-also"></a>另请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
