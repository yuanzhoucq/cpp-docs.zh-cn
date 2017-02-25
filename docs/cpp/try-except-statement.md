---
title: "try-except 语句 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_abnormal_termination_cpp"
  - "_exception_code_cpp"
  - "EXCEPTION_CONTINUE_SEARCH"
  - "_exception_info"
  - "__except"
  - "EXCEPTION_CONTINUE_EXECUTION"
  - "_exception_code"
  - "__except_cpp"
  - "_exception_info_cpp"
  - "EXCEPTION_EXECUTE_HANDLER"
  - "_abnormal_termination"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__try 关键字 [C++]"
  - "_abnormal_termination 关键字 [C++]"
  - "_exception_code 关键字 [C++]"
  - "_exception_info 关键字 [C++]"
  - "EXCEPTION_CONTINUE_EXECUTION 宏"
  - "EXCEPTION_CONTINUE_SEARCH 宏"
  - "EXCEPTION_EXECUTE_HANDLER 宏"
  - "GetExceptionCode 函数"
  - "try-catch 关键字 [C++], try-except 关键字 [C++]"
  - "try-except 关键字 [C++]"
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# try-except 语句
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 以下语法描述一个 try\-except 语句：  
  
## 语法  
  
```  
  
      __try   
{  
   // guarded code  
}  
__except ( expression )  
{  
   // exception handler code  
}  
```  
  
## 备注  
 **try\-except** 语句是 Microsoft 对 C 语言和 C\+\+ 语言的扩展，使目标应用程序能够在正常终止程序执行的事件发生时获取控制权。  此类事件称为异常，处理异常的机制称为结构化异常处理。  
  
 有关相关信息，请参阅 [try\-finally 语句](../cpp/try-finally-statement.md)。  
  
 异常可基于硬件，也可基于软件。  即使应用程序无法从硬件或软件异常中完全恢复，结构化异常处理也可以显示错误信息并捕获应用程序的内部状态，从而帮助诊断问题。  这对于无法轻松重现的间歇性问题特别有用。  
  
> [!NOTE]
>  结构化异常处理适用于 Win32 中的 C 和 C\+\+ 源文件。  但是，这不是专门为 C\+\+ 设计的。  您可通过使用 C\+\+ 异常处理来确保提高代码的可移植性。  此外，C\+\+ 异常处理更为灵活，因此它可以处理任何类型的异常。  对于 C\+\+ 程序，建议使用 C\+\+ 异常处理机制（[try、catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md) 语句）。  
  
 在 `__try` 子句后的复合语句是主体或受保护节。  在 `__except` 子句后的复合语句是异常处理程序。  处理程序指定在执行受保护节的主体时引发了异常的情况下要执行的一组操作。  执行过程如下所示：  
  
1.  执行受保护节。  
  
2.  如果在受保护节执行过程中未发生异常，则继续执行 `__except` 子句之后的语句。  
  
3.  如果在受保护节执行过程中或在受保护节调用的任何例程中发生异常，则将计算 `__except` *expression*（称为 *filter* 表达式），并且得出的值将确定异常的处理方式。  有三个值：  
  
     **EXCEPTION\_CONTINUE\_EXECUTION \(–1\)** 异常已消除。  从出现异常的点继续执行。  
  
     **EXCEPTION\_CONTINUE\_SEARCH \(0\)** 未识别异常。  继续向上搜索堆栈查找处理程序，首先是所在的 **try\-except** 语句，然后是具有下一个最高优先级的处理程序。  
  
     **EXCEPTION\_EXECUTE\_HANDLER \(1\)** 已识别异常。  通过执行 `__except` 复合语句将控制权传输到异常处理程序，然后在 `__except` 块之后继续执行。  
  
 由于 \_\_**except** 表达式将作为 C 表达式计算，因此它将限制为单一值、条件表达式运算符或逗号运算符。  如果需要更大量的处理，表达式可调用返回上面列出的三个值之一的例程。  
  
 每个应用程序都可以有各自的异常处理程序。  
  
 跳转到 `__try` 语句是无效的，但是，跳出这样一个语句是有效的。  如果进程在执行 **try\-except** 语句过程中终止，则将不会调用异常处理程序。  
  
 有关详细信息，请参阅知识库文章 Q315937：“如何：捕获 Visual C\+\+ 应用程序中的堆栈溢出”。  
  
## \_\_leave 关键字  
 `__leave` 关键字只在 `try-except` 语句的受保护节中有效，其效果是跳转到受保护节的结尾处。  将继续执行异常处理程序后的第一个语句。  
  
 `goto` 语句也可以跳出受保护节，如同使用 `try-finally` 语句一样，不会造成性能下降，因为不会出现堆栈回退。  但是，建议使用 `__leave` 关键字而不是 `goto` 语句，这样在受保护节很大或者很复杂的情况下出现编程错误的可能性小一些。  
  
### 结构化异常处理内部函数  
 结构化异常处理提供了两个可与 **try\-except** 语句一起使用的内部函数：**GetExceptionCode** 和 **GetExceptionInformation**。  
  
 **GetExceptionCode** 返回异常的代码（32 位整数）。  
  
 内部函数 **GetExceptionInformation** 返回指向包含异常相关附加信息的结构的指针。  通过此指针，您可以访问在出现硬件异常时存在的计算机状态。  该结构如下所示：  
  
```  
struct _EXCEPTION_POINTERS {  
      EXCEPTION_RECORD *ExceptionRecord,  
      CONTEXT *ContextRecord }  
```  
  
 在包含文件 EXCPT.H 中定义了指针类型 \_**EXCEPTION\_RECORD** 和 \_**CONTEXT**。  
  
 您可以在异常处理程序中使用 **GetExceptionCode**。  但是，您只能在异常筛选器表达式中使用 **GetExceptionInformation**。  它指向的信息通常位于堆栈上，并且这些信息在控制权转交给异常处理程序之后不再可用。  
  
 内部函数 **AbnormalTermination** 在终止处理程序内可用。  如果 `try-finally` 语句的主体按顺序终止，则将返回 0。  在所有其他情况下，它将返回 1。  
  
 EXCPT.H 为这些内部函数定义了一些替代名称：  
  
 **GetExceptionCode** 等效于 \_exception\_code  
  
 **GetExceptionInformation** 等效于 \_exception\_info  
  
 **AbnormalTermination** 等效于 \_abnormal\_termination  
  
## 示例  
 `// exceptions_try_except_Statement.cpp`  
  
 `// Example of try-except and try-finally statements`  
  
 `#include <stdio.h>`  
  
 `#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION`  
  
 `#include <excpt.h>`  
  
 `int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep) {`  
  
 `puts("in filter.");`  
  
 `if (code == EXCEPTION_ACCESS_VIOLATION) {`  
  
 `puts("caught AV as expected.");`  
  
 `return EXCEPTION_EXECUTE_HANDLER;`  
  
 `}`  
  
 `else {`  
  
 `puts("didn't catch AV, unexpected.");`  
  
 `return EXCEPTION_CONTINUE_SEARCH;`  
  
 `};`  
  
 `}`  
  
 `int main()`  
  
 `{`  
  
 `int* p = 0x00000000;   // pointer to NULL`  
  
 `puts("hello");`  
  
 `__try{`  
  
 `puts("in try");`  
  
 `__try{`  
  
 `puts("in try");`  
  
 `*p = 13;    // causes an access violation exception;`  
  
 `}__finally{`  
  
 `puts("in finally. termination: ");`  
  
 `puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");`  
  
 `}`  
  
 `}__except(filter(GetExceptionCode(), GetExceptionInformation())){`  
  
 `puts("in except");`  
  
 `}`  
  
 `puts("world");`  
  
 `}`  
  
## 输出  
  
```  
hello  
in try  
in try  
in filter.  
caught AV as expected.  
in finally. termination:  
        abnormal  
in except  
world  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [编写异常处理程序](../cpp/writing-an-exception-handler.md)   
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)