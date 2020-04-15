---
title: 编写异常筛选器
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: 05d3aa79d1293001e80a77b3171b7a4607cd81c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369487"
---
# <a name="writing-an-exception-filter"></a>编写异常筛选器

您可以通过跳转到异常处理程序的级别或通过继续执行来处理异常。 您可以使用*筛选器*来清理问题，然后返回 -1，在不清除堆栈的情况下恢复正常流，而不是使用异常处理程序代码来处理异常并中断。

> [!NOTE]
> 有些异常无法继续。 如果*筛选器*对于此类异常计算为 -1，则系统将引发新的异常。 当您调用["提升异常](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception)"时，您可以确定异常是否将继续。

例如，以下代码在*筛选器*表达式中使用函数调用：此函数处理问题，然后返回 -1 以恢复正常的控制流：

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

最好在*筛选器*表达式中使用函数调用，每当*筛选器*需要执行任何复杂操作时。 计算表达式将导致函数的执行，在此示例中，`Eval_Exception`。

请注意使用[GetExceptionCode](/windows/win32/Debug/getexceptioncode)来确定异常。 您必须在筛选器内部调用此函数。 `Eval_Exception`无法调用`GetExceptionCode`，但它必须将异常代码传递给它。

除非异常是整数或浮点溢出，否则此处理程序会将控制权传递给其他处理程序。 如果异常是整数或浮点溢出，则处理程序将调用一个函数（`ResetVars` 只是一个示例，不是 API 函数）以重置某些全局变量。 *语句-块-2*（在此示例中为空）永远无法执行，因为`Eval_Exception`永远不会返回EXCEPTION_EXECUTE_HANDLER （1）。

使用函数调用是处理复杂筛选器表达式的一个很好的通用方法。 其他两个有用的 C 语言功能是：

- 条件运算符

- 逗号运算符

条件运算符会经常用到，因为它可用于检查特定返回代码，然后返回两个不同值中的一个。 例如，只有在异常STATUS_INTEGER_OVERFLOW时，以下代码中的筛选器才会识别异常：

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

条件运算符在此示例中的用途主要是进行澄清，因为下面的代码将生成相同的结果：

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

条件运算符在您可能希望筛选器计算到 -1、EXCEPTION_CONTINUE_EXECUTION的情况下更有用。

利用逗号运算符，您可以在单个表达式中执行多个独立的运算。 效果大致是执行多个语句并返回最后一个表达式的值。 例如，下面的代码将异常代码存储在一个变量中，然后测试它：

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>另请参阅

[编写异常处理程序](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
