---
title: try-except 语句 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c55ff2599fac14be0be9ac852727167dd34e02d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="try-except-statement-c"></a>try-except 语句 (C)
**Microsoft 专用**  
  
 **try-except** 语句是一项 Microsoft C++ 语言扩展，它使应用程序能够在正常终止执行的事件发生时获取对程序的控制权。 此类事件称为异常，处理异常的机制称为结构化异常处理。  
  
 异常可能基于硬件或软件。 即使应用程序无法从硬件或软件异常中完全恢复，结构化异常处理也可以显示错误信息并捕获应用程序的内部状态，从而帮助诊断问题。 这对于无法轻松重现的间歇性问题特别有用。  
  
## <a name="syntax"></a>语法  
 *try-except-statement*:  
 **__try**  *compound-statement*  
  
 **__except (**  *expression*  **)**  *compound-statement*  
  
 `__try` 子句后的复合语句是受保护节。 在 `__except` 子句后的复合语句是异常处理程序。 如果在控制节执行过程中引发了异常，处理程序将指定要采取的一系列措施。 执行过程如下所示：  
  
1.  执行受保护节。  
  
2.  如果在受保护节执行过程中未发生异常，则继续执行 `__except` 子句之后的语句。  
  
3.  如果在受保护节的执行过程中或受保护节调用的任何例程中发生异常，则会计算 `__except` 表达式，返回的值将确定该异常的处理方式。 有三个值：  
  
     `EXCEPTION_CONTINUE_SEARCH` 异常无法识别。 继续向上搜索堆栈查找处理程序，首先是所在的 **try-except** 语句，然后是具有下一个最高优先级的处理程序。  
  
     `EXCEPTION_CONTINUE_EXECUTION` 异常可识别，但被关闭。 从出现异常的点继续执行。  
  
     `EXCEPTION_EXECUTE_HANDLER` 异常可识别。 通过执行 `__except` 复合语句来转移对异常处理程序的控制，然后在异常发生处继续执行。  
  
 由于 `__except` 表达式将作为 C 表达式来计算，因此它被限制为单个值、条件表达式运算符或逗号运算符。 如果需要更大量的处理，表达式可调用返回上面列出的三个值之一的例程。  
  
> [!NOTE]
>  结构化异常处理适用于 C 和 C++ 源文件。 但是，这不是专门为 C++ 设计的。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理机制灵活得多，因为它可以处理任何类型的异常。  
  
> [!NOTE]
>  对于 C++ 程序，应使用 C++ 异常处理，而不是结构化异常处理。 有关详细信息，请参阅《C++ 语言参考》中的[异常处理](../cpp/exception-handling-in-visual-cpp.md)。  
  
 应用程序中的每个例程可以有自己的异常处理程序。 `__except` 表达式在 `__try` 体的范围内执行。 这意味着它可以访问在该处声明的任何局部变量。  
  
 `__leave` 关键字在 **try-except** 语句块中有效。 `__leave` 的效果是跳转到 **try-except** 块的末尾。 执行将在异常处理程序结束后恢复。 尽管可使用 `goto` 语句来达到相同的结果，但 `goto` 语句会导致堆栈展开。 由于 `__leave` 语句不涉及堆栈展开，因此更有效。  
  
 使用 `longjmp` 运行时函数退出 **try-except** 语句被视为异常终止。 跳转到 `__try` 语句是非法的，但跳出该语句是合法的。 如果有进程在执行 **try-except** 语句的过程中终止，则不会调用异常处理程序。  
  
## <a name="example"></a>示例  
 下面是异常处理程序和终止处理程序的示例。 有关终止处理程序的详细信息，请参阅 [try-finally 语句](../c-language/try-finally-statement-c.md)。  
  
```  
.  
.  
.  
puts("hello");  
__try{  
   puts("in try");  
   __try{  
      puts("in try");  
      RAISE_AN_EXCEPTION();  
   }__finally{  
      puts("in finally");  
   }  
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){  
   puts("in except");  
}  
puts("world");  
```  
  
 这是上面的示例的输出，右侧还添加了注释：  
  
```  
hello  
in try              /* fall into try                     */  
in try              /* fall into nested try                */  
in filter           /* execute filter; returns 1 so accept  */  
in finally          /* unwind nested finally                */  
in except           /* transfer control to selected handler */  
world               /* flow out of handler                  */  
```  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [try-except 语句](../cpp/try-except-statement.md)