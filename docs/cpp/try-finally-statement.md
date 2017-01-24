---
title: "try-finally 语句 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__try"
  - "__leave_cpp"
  - "__leave"
  - "__finally_cpp"
  - "__try_cpp"
  - "__finally"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__finally 关键字 [C++]"
  - "__finally 关键字 [C++], try-finally 语句语法"
  - "__leave 关键字 [C++]"
  - "__leave 关键字 [C++], try-finally 语句"
  - "__try 关键字 [C++]"
  - "结构化异常处理, try-finally"
  - "try-catch 关键字 [C++], try-finally 关键字"
  - "try-finally 关键字 [C++]"
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# try-finally 语句
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 以下语法描述 `try-finally` 语句：  
  
```  
__try {  
   // guarded code  
}  
__finally {  
   // termination code  
}  
```  
  
## 语法  
 *try\-finally\-statement*：  
 `__try` *compound\-statement*  
  
 `__finally` *compound\-statement*  
  
 `try-finally` 语句是 Microsoft C 和 C\+\+ 语言扩展，它们使目标应用程序能够确保在代码块的执行被中断时执行清理。  清理包括多个任务，如释放内存、关闭文件和释放文件句柄。  `try-finally` 语句对此类例程特别有用：具有几个位置，在这些位置上执行了检查以找出可能导致例程提前返回内容的错误。  
  
 有关相关的信息和代码示例，请参阅 [try\-except 语句](../cpp/try-except-statement.md)。  有关常规的结构化异常处理的详细信息，请参阅[结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)。  有关托管应用程序中的异常处理的详细信息，请参阅 [\/clr 下的异常处理](../windows/exception-handling-cpp-component-extensions.md)。  
  
> [!NOTE]
>  结构化异常处理适用于 Win32 中的 C 和 C\+\+ 源文件。  但是，这不是专门为 C\+\+ 设计的。  您可通过使用 C\+\+ 异常处理来确保提高代码的可移植性。  此外，C\+\+ 异常处理更为灵活，因此它可以处理任何类型的异常。  对于 C\+\+ 程序，建议使用 C\+\+ 异常处理机制（[try、catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md) 语句）。  
  
 `__try` 子句后的复合语句是受保护节。  `__finally` 子句后的复合语句是终止处理程序。  处理程序指定了在退出受保护部分时执行的一组操作，无论受保护部分是因异常（不正常终止）还是因标准失效（正常终止）导致退出。  
  
 控制权通过简单的顺序执行（贯穿）传递到 `__try` 语句。  在控制进入 `__try` 时，其关联的处理程序将变为活动状态。  如果控制流到达 try 块的末尾，执行将继续，如下所示：  
  
1.  调用终止处理程序。  
  
2.  当终止处理程序完成时，执行在 `__finally` 语句后继续。  无论受保护部分如何结束（例如，通过受保护主体外部的 `goto` 或通过 `return` 语句），在控制流移出受保护部分 `before`，都会执行终止处理程序。  
  
     **\_\_finally** 语句不会阻碍搜索相应的异常处理程序。  
  
 如果 `__try` 块中发生异常，则操作系统必须找到该异常的处理程序，否则程序将失败。  如果找到处理程序，则会执行所有 `__finally` 块，并且执行将在处理程序中恢复。  
  
 例如，假设一个函数调用系列将函数 A 链接到函数 D，如下图所示。  每个函数均有一个终止处理程序。  如果异常在函数 D 中引发并在函数 A 中得到处理，则当系统展开堆栈时，按以下顺序调用终止处理程序：D、C、B。  
  
 ![终止处理程序执行顺序](../cpp/media/vc38cx1.png "vc38CX1")  
终止处理程序执行顺序  
  
> [!NOTE]
>  try\-finally 的行为与支持使用 **finally** 的其他语言（如 C\#）的行为不同。单个 `__try` 可以拥有 `__finally` 和 `__except` 之一，但不能同时拥有二者。如果同时使用二者，则外部 try\-except 语句必须包含内部 try\-finally 语句。指定何时执行每个块的规则也有所不同。  
  
## \_\_leave 关键字  
 `__leave` 关键字只在 `try-finally` 语句的受保护节中有效，其效果是跳转到受保护节的结尾处。  执行将在终止处理程序中的第一个语句处继续。  
  
 `goto` 语句还可以跳出受保护部分，但由于它调用了堆栈展开，因此会降低性能。  `__leave` 语句将更为有效，因为它不会导致堆栈展开。  
  
## 异常终止  
 使用 [longjmp](../c-runtime-library/reference/longjmp.md) 运行时函数退出 `try-finally` 语句被视为异常终止。  跳转到 `__try` 语句是非法的，但跳出该语句是合法的。  必须运行在起点（`__try` 块的正常中止）和终点（处理异常的 `__except` 块）之间处于活动状态的所有 `__finally` 语句。  这称为本地展开。  
  
 如果 **try** 块因某个原因提前终止（包括跳出该块），则系统将执行关联的 **finally** 块作为展开堆栈这一过程的一部分。  在此类情况下，如果从 **finally** 块内调用 [AbnormalTermination](http://msdn.microsoft.com/library/windows/desktop/ms679265) 函数，则该函数将返回 TRUE；否则，将返回 FALSE。  
  
 如果在执行 `try-finally` 语句期间结束进程，则不会调用终止处理程序。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [编写终止处理程序](../cpp/writing-a-termination-handler.md)   
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [Termination\-Handler Syntax](http://msdn.microsoft.com/library/windows/desktop/ms681393)