---
title: "编译器警告（等级 4）C4754 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4754"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4754"
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 4）C4754
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在比较中的算术运算的转换规则意味着无法执行一个分支。  
  
 该 C4754 警告问题，因为该比较的结果总是相同的。  这可能表示一个条件的分支绝对不会执行，因为关联的整数表达式不正确。  此代码缺陷在 64 位体系结构不正确的整数溢出选定经常发生。  
  
 整数转换规则是复杂的，因此有许多细微的 bug。  作为一种替代方法，以适应每个C4754警告，您可以更新代码以使用 [SafeInt Library](../../windows/safeint-library.md)。  
  
## 示例  
 此示例生成 C4754：  
  
```cpp  
// C4754a.cpp  
// Compile with: /W4 /c  
#include "errno.h"  
  
int sum_overflow(unsigned long a, unsigned long b)   
{  
   unsigned long long x = a + b; // C4754  
  
   if (x > 0xFFFFFFFF)   
   {  
      // never executes!  
      return EOVERFLOW;  
   }  
   return 0;  
}  
```  
  
 加法`a + b` 可能导致算术溢出之前的结果是向上转型为一个64位的值，并分配给64位变量`x`。  这意味着，在`x`的检查是多余的，永远不会上溢出。  在这种情况下，编译器发出此警告：  
  
  **警告的 C4754:算术运算的转换规则在 C4754a.cpp \(7\) 表示的比较一个分支无法执行。  将'\(a \+ ...\)'强制转换为'ULONG64'\(或字节的相似类型\)。**  若要消除此警告，您可以更改赋值语句转换操作的为 8 字节值：  
  
```cpp  
// Casting one operand is sufficient to force all the operands in   
// the addition be upcast according to C/C++ conversion rules, but  
// casting both is clearer.  
unsigned long long x =   
   (unsigned long long)a + (unsigned long long)b;  
```  
  
## 示例  
 下面的示例也会生成 C4754。  
  
```cpp  
// C4754b.cpp  
// Compile with: /W4 /c  
#include "errno.h"  
  
int wrap_overflow(unsigned long a)   
{  
   if (a + sizeof(unsigned long) < a) // C4754  
   {   
      // never executes!  
      return EOVERFLOW;  
   }  
   return 0;  
}  
```  
  
 该`sizeof()`操作符返回一个`size_t`，其大小是与体系结构相关。  该示例代码适用于32位体系结构，其中一个`size_t`是一个32位的类型。  然而，在64位体系结构，其中一个`size_t`是一个64位的类型。  对于整数转换规则意味着`a`是向上转型中的表达`a + b < a`一个64位的值，正如它被写为`(size_t)a + (size_t)b < (size_t)a` 当`a`和`b`为32位整数，64位的加法运算可以永远不会溢出，并约束从不保存。  因此，代码会检测到 64 位体系结构的整数溢出条件。  此示例导致编译器发出此警告：  
  
  **警告的 C4754:算术运算的转换规则在 C4754b.cpp \(7\) 表示的比较一个分支无法执行。  转换“4 "到“ULONG”\(或 4 个字节的相似类型\)。**  请注意，警告讯息明确地列出了恒定值，而不是原始的源字符串的预警分析遇到的问题的代码，`sizeof(unsigned long)`已被转换为一个常数。  因此，在源代码的表达式与警告消息的常量值的可能必须能够找到。  代码解析为C4754警告消息常量中最常见的来源是如`sizeof(TYPE)` 和 `strlen(szConstantString)`。  
  
 在这种情况下，内置的代码将类似于以下内容：  
  
```cpp  
// Casting the result of sizeof() to unsigned long ensures  
// that all the addition operands are 32-bit, so any overflow   
// is detected by the check.  
if (a + (unsigned long)sizeof(unsigned long) < a)  
  
```  
  
 **Note**的编译器警告中提到的行号是一个语句的最后一行。  有关是扩展多个行的复杂条件语句的警告消息，具有的行代码缺陷可能是若干行中报告的行之前。  例如：  
  
```cpp  
unsigned long a;  
  
if (a + sizeof(unsigned long) < a || // incorrect check  
    condition1() ||   
    a == 0) {    // C4754 warning reported on this line  
         // never executes!  
         return INVALID_PARAMETER;  
}  
  
```