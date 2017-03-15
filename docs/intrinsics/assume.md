---
title: "__assume | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__assume"
  - "__assume_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__assume keyword [C++]"
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# __assume
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 传递优化程序提示。  
  
## 语法  
  
```  
__assume(    expression )  
```  
  
#### 参数  
 `expression`  
 假设评估为 true 的任何表达式。  
  
## 备注  
 优化程序假设在关键词出现的地方由 `expression` 表示的条件为 true 并且直到修改 `expression`（例如，指定变量）前一直为 true。  选择性使用通过 `__assume` 传递给优化程序的提示可以完善优化。  
  
 如果将 `__assume` 语句写成矛盾（始终评估为 false 的表达式），则其始终会被视为 `__assume(0)`。  如果代码表现得不如预期，确保你定义的 `expression` 为有效和 true，如前所述。  有关更多预期 `__assume(0)` 行为的信息，请参阅后面的备注。  
  
> [!WARNING]
>  程序的可达路径不得包含无效的 `__assume` 语句。  如果编译器可以到达无效的 `__assume` 语句，程序可能会导致不可预测的潜在危险行为。  
  
 `__assume` 不是真正的内部函数。  不必将其宣传为函数，并且不能用于 `#pragma intrinsic` 指令。  尽管没有生成任何代码，但还是会对由优化程序生成的代码产生影响。  
  
 仅当此断言不可恢复时才能使用 [ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 中的 `__assume`。  请勿在其中有后续错误恢复代码的断言中使用 `__assume`，因为编译器可能优化掉错误处理的代码。  
  
 `__assume(0)` 语句是一个特例。  使用 `__assume(0)` 来表示无法到达的代码路径。  下例显示了如何使用 `__assume(0)` 来表示无法获得 switch 语句的默认大小写。  此例显示了 `__assume(0)` 最典型的用法。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`__assume`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
## 示例  
  
```  
// compiler_intrinsics__assume.cpp  
#ifdef DEBUG  
# define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__) )  
#else  
# define ASSERT(e)    ( __assume(e) )  
#endif  
  
void func1(int i)  
{  
}  
  
int main(int p)  
{  
   switch(p){  
      case 1:  
         func1(1);  
         break;  
      case 2:  
         func1(-1);  
         break;  
      default:  
         __assume(0);  
            // This tells the optimizer that the default  
            // cannot be reached. As so, it does not have to generate  
            // the extra code to check that 'p' has a value   
            // not represented by a case arm. This makes the switch   
            // run faster.  
   }  
}  
```  
  
 使用 `__assume(0)` 表示告诉优化程序，无法获得默认大小写。  此例证明，程序员了解 `p` 唯一可能的输入值是 1 或 2。  如果传入 `p` 其他值，程序将变为无效并导致不可预测的行为。  
  
 `__assume(0)` 语句的结果，编译器不会生成代码来测试 `p` 是否具有不会在 case 语句中显示的值。  要使此生效，`__assume(0)` 语句在默认大小写中的正文必须是第一个语句。  
  
 因为如果在运行时 `__assume` 语句中的表达式为 false，则编译器生成的基于 `__assume` 的代码可能无法正常运行。  如果不确定表达式在运行时始终为 true，你可以使用 `assert` 函数保护该代码。  
  
```  
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )  
```  
  
 遗憾的是，使用此 `assert` 函数将会阻止编译器执行默认大小写优化，此点已在本文前面说过。  或者，你还可以使用单独的宏，如下所示。  
  
```  
#ifdef DEBUG  
# define NODEFAULT   ASSERT(0)  
#else  
# define NODEFAULT   __assume(0)  
#endif  
  
   default:  
      NODEFAULT;  
```  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)