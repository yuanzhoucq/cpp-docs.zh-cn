---
title: try-finally 语句 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
dev_langs:
- C++
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c57676cace8451de266d30d4c146e3ae0c3cb1b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="try-finally-statement"></a>try-finally 语句
**Microsoft 专用**  
  
 以下语法描述 `try-finally` 语句：  
  
```  
__try {  
   // guarded code  
}  
__finally {  
   // termination code  
}  
```  
  
## <a name="grammar"></a>语法  
 try-finally-statement:  
 `__try`*复合语句*  
  
 `__finally`*复合语句*  
  
 `try-finally` 语句是 Microsoft C 和 C++ 语言扩展，它们使目标应用程序能够确保在代码块的执行被中断时执行清理。 清理包括多个任务，如释放内存、关闭文件和释放文件句柄。 `try-finally` 语句对此类例程特别有用：具有几个位置，在这些位置上执行了检查以找出可能导致例程提前返回内容的错误。  
  
 有关相关的信息和代码示例，请参阅[重-除非语句](../cpp/try-except-statement.md)。 一般情况下处理结构化异常的详细信息，请参阅[结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)。 在托管应用程序中处理异常的详细信息，请参阅[在 /clr 下的异常处理](../windows/exception-handling-cpp-component-extensions.md)。  
  
> [!NOTE]
>  结构化异常处理适用于 Win32 中的 C 和 C++ 源文件。 但是，这不是专门为 C++ 设计的。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理更为灵活，因此它可以处理任何类型的异常。 对于 c + + 程序，建议你使用 c + + 异常处理机制 ([try、 catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)语句)。  
  
 `__try` 子句后的复合语句是受保护节。 `__finally` 子句后的复合语句是终止处理程序。 处理程序指定了在退出受保护部分时执行的一组操作，无论受保护部分是因异常（不正常终止）还是因标准失效（正常终止）导致退出。  
  
 控制权通过简单的顺序执行（贯穿）传递到 `__try` 语句。 在控制进入 `__try` 时，其关联的处理程序将变为活动状态。 如果控制流到达 try 块的末尾，执行将继续，如下所示：  
  
1.  调用终止处理程序。  
  
2.  当终止处理程序完成时，执行在 `__finally` 语句后继续。 无论受保护部分如何结束（例如，通过受保护主体外部的 `goto` 或通过 `return` 语句），在控制流移出受保护部分 `before`，都会执行终止处理程序。  
  
     A **__finally**语句不会阻止搜索适当异常处理程序。  
  
 如果 `__try` 块中发生异常，则操作系统必须找到该异常的处理程序，否则程序将失败。 如果找到处理程序，则会执行所有 `__finally` 块，并且执行将在处理程序中恢复。  
  
 例如，假设一个函数调用系列将函数 A 链接到函数 D，如下图所示。 每个函数均有一个终止处理程序。 如果异常在函数 D 中引发并在函数 A 中得到处理，则当系统展开堆栈时，按以下顺序调用终止处理程序：D、C、B。  
  
 ![顺序终止 &#45; 处理程序执行](../cpp/media/vc38cx1.gif "vc38CX1")  
终止处理程序执行顺序  
  
> [!NOTE]
>  Try-finally 的行为是不同的支持使用其他语言的**最后**，如 C#。  单个 `__try` 可以拥有 `__finally` 和 `__except` 之一，但不能同时拥有二者。  如果同时使用二者，则外部 try-except 语句必须包含内部 try-finally 语句。  指定何时执行每个块的规则也有所不同。  
  
## <a name="the-leave-keyword"></a>__leave 关键字  
 `__leave` 关键字只在 `try-finally` 语句的受保护节中有效，其效果是跳转到受保护节的结尾处。 执行将在终止处理程序中的第一个语句处继续。  
  
 `goto` 语句还可以跳出受保护部分，但由于它调用了堆栈展开，因此会降低性能。 `__leave` 语句将更为有效，因为它不会导致堆栈展开。  
  
## <a name="abnormal-termination"></a>异常终止  
 退出`try-finally`语句使用[longjmp](../c-runtime-library/reference/longjmp.md)运行时函数被视为异常终止。 跳转到 `__try` 语句是非法的，但跳出该语句是合法的。 必须运行在起点（`__finally` 块的正常中止）和终点（处理异常的 `__try` 块）之间处于活动状态的所有 `__except` 语句。 这称为本地展开。  
  
 如果**重**块过早终止出于任何原因，包括跳出该块，则系统将执行关联**最后**过程的一部分，序言的展开堆栈的块。 在这种情况下， [AbnormalTermination](http://msdn.microsoft.com/library/windows/desktop/ms679265)函数将返回 TRUE，如果从内调用**最后**块; 否则，它将返回 FALSE。  
  
 如果在执行 `try-finally` 语句期间结束进程，则不会调用终止处理程序。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编写终止处理程序](../cpp/writing-a-termination-handler.md)   
 [结构化的异常处理 （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [终止处理程序语法](http://msdn.microsoft.com/library/windows/desktop/ms681393)