---
title: 异常： 捕捉和删除异常 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bd59cc19c80e305a7e57fb711a49f59a024d528
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434760"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>异常：捕捉和删除异常

下列说明和示例演示如何捕获和删除异常。 有关详细信息**尝试**，**捕获**，并**引发**关键字，请参见[c + + 异常处理](../cpp/cpp-exception-handling.md)。

你的异常处理程序必须删除其处理的异常对象，因为如果未删除异常将导致在代码捕获异常时出现内存泄漏。

你**捕获**块必须删除异常时：

- **捕获**块引发新异常。

     当然，如果您再次引发同一异常，则不得删除此异常：

     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- 执行返回内**捕获**块。

> [!NOTE]
>  删除时`CException`，使用`Delete`成员函数删除异常。 不要使用**删除**关键字，因为它可能会失败，如果异常不在堆上。

#### <a name="to-catch-and-delete-exceptions"></a>捕获和删除异常

1. 使用**尝试**关键字设置**尝试**块。 执行可能引发异常中的任何程序语句**尝试**块。

     使用**捕获**关键字设置**捕获**块。 将异常处理代码中的放置**捕获**块。 中的代码**捕获**仅当执行块中的代码**尝试**该块引发一个异常中指定的类型**捕获**语句。

     以下框架演示如何**尝试**并**捕获**正常排列基块：

     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

     当引发异常时，控制权将传递给第一个**捕获**其异常声明匹配异常的类型的块。 您可以有选择地处理不同类型的异常和顺序**捕获**阻止如下所示：

     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

有关详细信息，请参阅[异常： 从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)

