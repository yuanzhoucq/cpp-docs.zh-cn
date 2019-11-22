---
title: 编写异常筛选器
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: aaf0dc77207399d7c6be86127d7decf03895ced5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245989"
---
# <a name="writing-an-exception-filter"></a>编写异常筛选器

您可以通过跳转到异常处理程序的级别或通过继续执行来处理异常。 Instead of using the exception handler code to handle the exception and falling through, you can use *filter* to clean up the problem and then, by returning -1, resume normal flow without clearing the stack.

> [!NOTE]
>  有些异常无法继续。 If *filter* evaluates to -1 for such an exception, the system raises a new exception. When you call [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception), you determine whether the exception will continue.

For example, the following code uses a function call in the *filter* expression: this function handles the problem and then returns -1 to resume normal flow of control:

```cpp
// exceptions_Writing_an_Exception_Filter.cpp
#include <windows.h>
int main() {
   int Eval_Exception( int );

   __try {}

   __except ( Eval_Exception( GetExceptionCode( ))) {
      ;
   }

}
void ResetVars( int ) {}
int Eval_Exception ( int n_except ) {
   if ( n_except != STATUS_INTEGER_OVERFLOW &&
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions
   return EXCEPTION_CONTINUE_SEARCH;

   // Execute some code to clean up problem
   ResetVars( 0 );   // initializes data to 0
   return EXCEPTION_CONTINUE_EXECUTION;
}
```

It is a good idea to use a function call in the *filter* expression whenever *filter* needs to do anything complex. 计算表达式将导致函数的执行，在此示例中，`Eval_Exception`。

Note the use of [GetExceptionCode](/windows/win32/Debug/getexceptioncode) to determine the exception. 您必须在筛选器内部调用此函数。 `Eval_Exception` cannot call `GetExceptionCode`, but it must have the exception code passed to it.

除非异常是整数或浮点溢出，否则此处理程序会将控制权传递给其他处理程序。 如果异常是整数或浮点溢出，则处理程序将调用一个函数（`ResetVars` 只是一个示例，不是 API 函数）以重置某些全局变量。 *Statement-block-2*, which in this example is empty, can never be executed because `Eval_Exception` never returns EXCEPTION_EXECUTE_HANDLER (1).

使用函数调用是处理复杂筛选器表达式的一个很好的通用方法。 其他两个有用的 C 语言功能是：

- 条件运算符

- 逗号运算符

条件运算符会经常用到，因为它可用于检查特定返回代码，然后返回两个不同值中的一个。 For example, the filter in the following code recognizes the exception only if the exception is STATUS_INTEGER_OVERFLOW:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

条件运算符在此示例中的用途主要是进行澄清，因为下面的代码将生成相同的结果：

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

The conditional operator is more useful in situations where you might want the filter to evaluate to -1, EXCEPTION_CONTINUE_EXECUTION.

利用逗号运算符，您可以在单个表达式中执行多个独立的运算。 效果大致是执行多个语句并返回最后一个表达式的值。 例如，下面的代码将异常代码存储在一个变量中，然后测试它：

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>请参阅

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)