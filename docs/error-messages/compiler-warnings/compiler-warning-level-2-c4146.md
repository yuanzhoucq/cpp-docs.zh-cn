---
title: "编译器警告（等级 2）C4146 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4146"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4146"
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 2）C4146
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一元负运算符应用于无符号类型，结果仍为无符号类型  
  
 无符号类型只能保存非负值，所以一元负（非）应用于无符号类型时通常无意义。  操作数和结果都是非负的。  
  
 实际上，当程序员尝试表达最小整数值 \-2147483648 时，会发生此问题。  该值不能写为 \-2147483648，因为表达式处理分两个步骤：  
  
1.  计算数字 2147483648。  因 2147483648 大于最大整数值 2147483647，所以其类型不是 [int](../../c-language/integer-types.md)，而是 `unsigned int`。  
  
2.  将一元负应用于该值，得到无符号结果，该结果碰巧是 2147483648。  
  
 无符号类型的结果可能导致意外行为。  如果在比较中使用该结果，则可使用无符号比较，例如另一个操作数是 `int` 时。  这解释了下面的示例程序只输出一行的原因。  
  
 预期的第二行 `1 is greater than the most negative int` 未输出，因为 `((unsigned int)1) > 2147483648`  为假。  
  
 可以通过使用 limits.h 中的 INT\_MIN 来避免出现 C4146 警告，该 INT\_MIN 具有 **signed int** 类型。  
  
## 示例  
 下面的示例生成 C4146：  
  
```  
// C4146.cpp  
// compile with: /W2  
#include <stdio.h>  
  
void check(int i)   
{  
    if (i > -2147483648)   // C4146  
        printf_s("%d is greater than the most negative int\n", i);  
}  
  
int main()   
{  
    check(-100);  
    check(1);  
}  
```