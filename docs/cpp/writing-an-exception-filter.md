---
title: "编写异常筛选器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "异常处理, 筛选器"
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 编写异常筛选器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以通过跳转到异常处理程序的级别或通过继续执行来处理异常。  除了使用异常处理程序代码处理异常和故障，您也可以使用 *filter* 来清理问题，然后通过返回“–1”来继续正常流而不清除堆栈。  
  
> [!NOTE]
>  有些异常无法继续。  对这样的异常来说，如果 *filter* 计算结果为 \-1，则系统将产生新的异常。  调用 [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) 时，将确定异常是否会继续。  
  
 例如，下面的代码使用函数调用 *filter* 表达式：此函数处理该问题并返回 –1 以继续正常控制流：  
  
```  
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
  
 每当 *filter* 需要执行任何复杂操作时，最好在 *filter* 表达式中使用函数调用。  计算表达式将导致函数的执行，在此示例中，`Eval_Exception`。  
  
 请注意使用 [GetExceptionCode](http://msdn.microsoft.com/library/windows/desktop/ms679356) 以确定异常。  您必须在筛选器内部调用此函数。  `Eval_Exception` 不能调用 **GetExceptionCode**，但是它必须具有传递给它的异常代码。  
  
 除非异常是整数或浮点溢出，否则此处理程序会将控制权传递给其他处理程序。  如果异常是整数或浮点溢出，则处理程序将调用一个函数（`ResetVars` 只是一个示例，不是 API 函数）以重置某些全局变量。  *Statement\-block\-2*（在此示例中为空）无法执行，因为 `Eval_Exception` 绝不返回 EXCEPTION\_EXECUTE\_HANDLER \(1\)。  
  
 使用函数调用是处理复杂筛选器表达式的一个很好的通用方法。  其他两个有用的 C 语言功能是：  
  
-   条件运算符  
  
-   逗号运算符  
  
 条件运算符会经常用到，因为它可用于检查特定返回代码，然后返回两个不同值中的一个。  例如，仅当异常为 `STATUS_INTEGER_OVERFLOW` 时，下面代码中的筛选器才能识别异常：  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {  
```  
  
 条件运算符在此示例中的用途主要是进行澄清，因为下面的代码将生成相同的结果：  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {  
```  
  
 条件运算符在您希望筛选器的计算结果为 –1、EXCEPTION\_CONTINUE\_EXECUTION 时更有用。  
  
 利用逗号运算符，您可以在单个表达式中执行多个独立的运算。  效果大致是执行多个语句并返回最后一个表达式的值。  例如，下面的代码将异常代码存储在一个变量中，然后测试它：  
  
```  
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )  
```  
  
## 请参阅  
 [编写异常处理程序](../cpp/writing-an-exception-handler.md)   
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)