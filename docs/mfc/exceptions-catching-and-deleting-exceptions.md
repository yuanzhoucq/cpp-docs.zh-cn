---
title: "异常：捕捉和删除异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AND_CATCH 宏"
  - "捕捉块, 捕捉和删除异常"
  - "异常处理, 捕捉和删除异常"
  - "异常, 删除"
  - "执行, 从捕获块内返回"
  - "try-catch 异常处理, 捕捉和删除异常"
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常：捕捉和删除异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下说明演示如何捕捉异常和删除的示例。  有关 **try**的更多信息， **catch**和 `throw` 关键字，请参见 [C\+\+ 异常处理](../cpp/cpp-exception-handling.md)。  
  
 它们处理的异常处理程序必须删除异常对象，因为异常，如果删除一导致内存泄漏，则只要该代码捕获异常。  
  
 **catch** 块必须删除时，通常引发异常：  
  
-   **catch** 块引发一个新异常。  
  
     当然，在中，如果您再次，引发同一异常无法删除的异常：  
  
     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/CPP/exceptions-catching-and-deleting-exceptions_1.cpp)]  
  
-   执行返回从 **catch** 块内部。  
  
> [!NOTE]
>  删除当 `CException`时，请使用 **删除** 成员函数删除异常。  不使用 **删除** 关键字，因为它可能失败，则异常不在堆。  
  
#### 捕获异常和删除  
  
1.  使用 **try** 关键字来设置 **try** 块。  练习可能引发在 **try** 块内的异常的程序语句。  
  
     使用 **catch** 关键字来设置 **catch** 块。  放置异常处理代码。**catch** 块。  在 **try** 块内的代码引发 **catch** 语句中，指定类型的异常。**catch** 块中的代码。  
  
     下面的主干显示通常如何具有 **try** 和 **catch** 块：  
  
     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/CPP/exceptions-catching-and-deleting-exceptions_2.cpp)]  
  
     引发异常时，控制将传递到异常匹配声明异常类型的第一 **catch** 块。  您可以选择性地处理异常的不同类型的运行 **catch** 块中。如下所示：  
  
     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/CPP/exceptions-catching-and-deleting-exceptions_3.cpp)]  
  
 有关更多信息，请参见 [异常：从 MFC 宏转换异常](../mfc/exceptions-converting-from-mfc-exception-macros.md)。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)