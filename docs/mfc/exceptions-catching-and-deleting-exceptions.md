---
title: "异常： 捕捉和删除异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8496b5228fe4002bb1ca80f8fbe793fd5e16ca81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>异常：捕捉和删除异常
下列说明和示例演示如何捕获和删除异常。 有关详细信息**重**，**捕获**，和`throw`关键字，请参阅[c + + 异常处理](../cpp/cpp-exception-handling.md)。  
  
 你的异常处理程序必须删除其处理的异常对象，因为如果未删除异常将导致在代码捕获异常时出现内存泄漏。  
  
 你**捕获**块必须删除异常时：  
  
-   **捕获**块中引发一个新异常。  
  
     当然，如果您再次引发同一异常，则不得删除此异常：  
  
     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]  
  
-   执行返回内**捕获**块。  
  
> [!NOTE]
>  删除时`CException`，使用**删除**成员函数删除异常。 不要使用**删除**关键字，因为如果异常不在堆上，它就可能会失败。  
  
#### <a name="to-catch-and-delete-exceptions"></a>捕获和删除异常  
  
1.  使用**重**关键字设置**重**块。 执行任何可能内引发异常的程序语句**重**块。  
  
     使用**捕获**关键字设置**捕获**块。 异常处理将代码放置在**捕获**块。 中的代码**捕获**仅当执行块中的代码内**重**块中引发的异常中指定的类型**捕获**语句。  
  
     以下框架演示如何**重**和**捕获**正常排列块：  
  
     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]  
  
     当引发异常时，控制权将交给第一个**捕获**其异常声明都与匹配的异常的类型的块。 你可以有选择地处理不同类型的异常的顺序**捕获**阻止如下所示：  
  
     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]  
  
 有关详细信息，请参阅[异常： 从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)。  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)

